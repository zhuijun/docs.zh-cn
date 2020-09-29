---
title: 业务流程模式 - 无服务器应用
description: Azure Durable 函数流程
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 6c5f6aaedbc13c47289e102bb59f7b066525b107
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171658"
---
# <a name="orchestration-patterns"></a><span data-ttu-id="9b727-103">业务流程模式</span><span class="sxs-lookup"><span data-stu-id="9b727-103">Orchestration patterns</span></span>

<span data-ttu-id="9b727-104">Durable Functions 使你可以更轻松地创建无服务器环境中由长时间运行的离散活动构成的状态工作流。</span><span class="sxs-lookup"><span data-stu-id="9b727-104">Durable Functions makes it easier to create stateful workflows that are composed of discrete, long running activities in a serverless environment.</span></span> <span data-ttu-id="9b727-105">由于 Durable Functions 可以跟踪工作流的进度并定期检查执行历史记录，因此它有助于实现一些有趣的模式。</span><span class="sxs-lookup"><span data-stu-id="9b727-105">Since Durable Functions can track the progress of your workflows and periodically checkpoints the execution history, it lends itself to implementing some interesting patterns.</span></span>

## <a name="function-chaining"></a><span data-ttu-id="9b727-106">函数链</span><span class="sxs-lookup"><span data-stu-id="9b727-106">Function chaining</span></span>

<span data-ttu-id="9b727-107">在典型的连续进程中，活动需要按特定顺序逐个执行。</span><span class="sxs-lookup"><span data-stu-id="9b727-107">In a typical sequential process, activities need to execute one after the other in a particular order.</span></span> <span data-ttu-id="9b727-108">或者，即将发生的活动可能需要前一个函数的一些输出。</span><span class="sxs-lookup"><span data-stu-id="9b727-108">Optionally, the upcoming activity may require some output from the previous function.</span></span> <span data-ttu-id="9b727-109">这种对活动顺序的依赖关系创建了执行的函数链。</span><span class="sxs-lookup"><span data-stu-id="9b727-109">This dependency on the ordering of activities creates a function chain of execution.</span></span>

<span data-ttu-id="9b727-110">使用 Durable Functions 实现此工作流模式的好处在于它可以执行检查点操作。</span><span class="sxs-lookup"><span data-stu-id="9b727-110">The benefit of using Durable Functions to implement this workflow pattern comes from its ability to do checkpointing.</span></span> <span data-ttu-id="9b727-111">如果服务器崩溃、网络超时或发生其他问题，则 Durable 函数可以从上一个已知状态恢复，并继续运行工作流，即使其位于另一台服务器上也是如此。</span><span class="sxs-lookup"><span data-stu-id="9b727-111">If the server crashes, the network times out or some other issue occurs, Durable functions can resume from the last known state and continue running your workflow even if it's on another server.</span></span>

```csharp
[FunctionName("PlaceOrder")]
public static async Task<string> PlaceOrder([OrchestrationTrigger] DurableOrchestrationContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    await context.CallActivityAsync<bool>("CheckAndReserveInventory", orderData);
    await context.CallActivityAsync<bool>("ProcessPayment", orderData);

    string trackingNumber = await context.CallActivityAsync<string>("ScheduleShipping", orderData);
    await context.CallActivityAsync<string>("EmailCustomer", trackingNumber);

    return trackingNumber;
}
```

<span data-ttu-id="9b727-112">在上面的代码示例中，`CallActivityAsync` 函数负责在数据中心中的虚拟机上运行给定的活动。</span><span class="sxs-lookup"><span data-stu-id="9b727-112">In the preceding code sample, the `CallActivityAsync` function is responsible for running a given activity on a virtual machine in the data center.</span></span> <span data-ttu-id="9b727-113">当 await 返回并且基础任务完成时，执行将被记录到历史记录表。</span><span class="sxs-lookup"><span data-stu-id="9b727-113">When the await returns and the underlying Task completes, the execution will be recorded to the history table.</span></span> <span data-ttu-id="9b727-114">业务流程协调程序函数中的代码可利用任何熟悉的任务并行库构造和 async/await 关键字。</span><span class="sxs-lookup"><span data-stu-id="9b727-114">The code in the orchestrator function can make use of any of the familiar constructs of the Task Parallel Library and the async/await keywords.</span></span>

<span data-ttu-id="9b727-115">下面的代码简单举例介绍了 `ProcessPayment` 方法：</span><span class="sxs-lookup"><span data-stu-id="9b727-115">The following code is a simplified example of what the `ProcessPayment` method may look like:</span></span>

```csharp
[FunctionName("ProcessPayment")]
public static bool ProcessPayment([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    ApplyCoupons(orderData);
    if(IssuePaymentRequest(orderData)) {
        return true;
    }

    return false;
}
```

## <a name="asynchronous-http-apis"></a><span data-ttu-id="9b727-116">异步 HTTP API</span><span class="sxs-lookup"><span data-stu-id="9b727-116">Asynchronous HTTP APIs</span></span>

<span data-ttu-id="9b727-117">在某些情况下，工作流可能包含需要较长时间才能完成的活动。</span><span class="sxs-lookup"><span data-stu-id="9b727-117">In some cases, workflows may contain activities that take a relatively long period of time to complete.</span></span> <span data-ttu-id="9b727-118">假设有一个进程，该进程开始将媒体文件备份到 blob 存储中。</span><span class="sxs-lookup"><span data-stu-id="9b727-118">Imagine a process that kicks off the backup of media files into blob storage.</span></span> <span data-ttu-id="9b727-119">根据媒体文件的大小和数量，此备份进程可能需要数小时才能完成。</span><span class="sxs-lookup"><span data-stu-id="9b727-119">Depending on the size and quantity of the media files, this backup process may take hours to complete.</span></span>

<span data-ttu-id="9b727-120">在此方案中，`DurableOrchestrationClient` 查看正在运行的工作流状态的功能非常有用。</span><span class="sxs-lookup"><span data-stu-id="9b727-120">In this scenario, the `DurableOrchestrationClient`'s ability to check the status of a running workflow becomes useful.</span></span> <span data-ttu-id="9b727-121">使用 `HttpTrigger` 启动工作流时，可以使用 `CreateCheckStatusResponse` 方法返回 `HttpResponseMessage` 的实例。</span><span class="sxs-lookup"><span data-stu-id="9b727-121">When using an `HttpTrigger` to start a workflow, the `CreateCheckStatusResponse` method can be used to return an instance of `HttpResponseMessage`.</span></span> <span data-ttu-id="9b727-122">此响应为客户端提供有效负载中的 URI，可用于检查正在运行的进程的状态。</span><span class="sxs-lookup"><span data-stu-id="9b727-122">This response provides the client with a URI in the payload that can be used to check the status of the running process.</span></span>

```csharp
[FunctionName("OrderWorkflow")]
public static async Task<HttpResponseMessage> Run(
    [HttpTrigger(AuthorizationLevel.Function, "POST")]HttpRequestMessage req,
    [OrchestrationClient ] DurableOrchestrationClient orchestrationClient)
{
    OrderRequestData data = await req.Content.ReadAsAsync<OrderRequestData>();

    string instanceId = await orchestrationClient.StartNewAsync("PlaceOrder", data);

    return orchestrationClient.CreateCheckStatusResponse(req, instanceId);
}
```

<span data-ttu-id="9b727-123">下面的示例结果显示了响应有效负载的结构。</span><span class="sxs-lookup"><span data-stu-id="9b727-123">The sample result below shows the structure of the response payload.</span></span>

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

<span data-ttu-id="9b727-124">使用你的首选 HTTP 客户端，可以对 statusQueryGetUri 中的 URI 发出 GET 请求，以检查正在运行的工作流的状态。</span><span class="sxs-lookup"><span data-stu-id="9b727-124">Using your preferred HTTP client, GET requests can be made to the URI in statusQueryGetUri to inspect the status of the running workflow.</span></span> <span data-ttu-id="9b727-125">返回的状态响应应类似于以下代码。</span><span class="sxs-lookup"><span data-stu-id="9b727-125">The returned status response should resemble the following code.</span></span>

```json
{
    "runtimeStatus": "Running",
    "input": {
        "$type": "DurableFunctionsDemos.OrderRequestData, DurableFunctionsDemos"
    },
    "output": null,
    "createdTime": "2018-01-01T00:22:05Z",
    "lastUpdatedTime": "2018-01-01T00:22:09Z"
}
```

<span data-ttu-id="9b727-126">在此过程继续时，状态响应将更改为“已失败”  或“已完成”  。</span><span class="sxs-lookup"><span data-stu-id="9b727-126">As the process continues, the status response will change to either **Failed** or **Completed**.</span></span> <span data-ttu-id="9b727-127">成功完成后，有效负载中的“输出”  属性将包含任何返回的数据。</span><span class="sxs-lookup"><span data-stu-id="9b727-127">On successful completion, the **output** property in the payload will contain any returned data.</span></span>

## <a name="monitoring"></a><span data-ttu-id="9b727-128">监视</span><span class="sxs-lookup"><span data-stu-id="9b727-128">Monitoring</span></span>

<span data-ttu-id="9b727-129">对于简单的定期任务，Azure Functions 提供可基于 CRON 表达式计划的 `TimerTrigger`。</span><span class="sxs-lookup"><span data-stu-id="9b727-129">For simple recurring tasks, Azure Functions provides the `TimerTrigger` that can be scheduled based on a CRON expression.</span></span> <span data-ttu-id="9b727-130">计时器适用于简单、生存期较短的任务，但可能存在需要更灵活的计划的情况。</span><span class="sxs-lookup"><span data-stu-id="9b727-130">The timer works well for simple, short-lived tasks, but there might be scenarios where more flexible scheduling is needed.</span></span> <span data-ttu-id="9b727-131">监视模式和 Durable Functions 可在此种情况下提供帮助。</span><span class="sxs-lookup"><span data-stu-id="9b727-131">This scenario is when the monitoring pattern and Durable Functions can help.</span></span>

<span data-ttu-id="9b727-132">Durable Functions 允许灵活计划间隔、生存期管理和从单个业务流程函数创建多个监视器进程。</span><span class="sxs-lookup"><span data-stu-id="9b727-132">Durable Functions allows for flexible scheduling intervals, lifetime management, and the creation of multiple monitor processes from a single orchestration function.</span></span> <span data-ttu-id="9b727-133">此功能的一个用例是为在满足特定阈值后完成的股票价格变化创建观察程序。</span><span class="sxs-lookup"><span data-stu-id="9b727-133">One use case for this functionality might be to create watchers for stock price changes that complete once a certain threshold is met.</span></span>

```csharp
[FunctionName("CheckStockPrice")]
public static async Task CheckStockPrice([OrchestrationTrigger] DurableOrchestrationContext context)
{
    StockWatcherInfo stockInfo = context.GetInput<StockWatcherInfo>();
    const int checkIntervalSeconds = 120;
    StockPrice initialStockPrice = null;

    DateTime fireAt;
    DateTime exitTime = context.CurrentUtcDateTime.Add(stockInfo.TimeLimit);

    while (context.CurrentUtcDateTime < exitTime)
    {
        StockPrice currentStockPrice = await context.CallActivityAsync<StockPrice>("GetStockPrice", stockInfo);

        if (initialStockPrice == null)
        {
            initialStockPrice = currentStockPrice;
            fireAt = context.CurrentUtcDateTime.AddSeconds(checkIntervalSeconds);
            await context.CreateTimer(fireAt, CancellationToken.None);
            continue;
        }

        decimal percentageChange = (initialStockPrice.Price - currentStockPrice.Price) /
                               ((initialStockPrice.Price + currentStockPrice.Price) / 2);

        if (Math.Abs(percentageChange) >= stockInfo.PercentageChange)
        {
            // Change threshold detected
            await context.CallActivityAsync("NotifyStockPercentageChange", currentStockPrice);
            break;
        }

        // Sleep til next polling interval
        fireAt = context.CurrentUtcDateTime.AddSeconds(checkIntervalSeconds);
        await context.CreateTimer(fireAt, CancellationToken.None);
    }
}
```

<span data-ttu-id="9b727-134">`DurableOrchestrationContext` 的 `CreateTimer` 方法设置了用于检查股票价格变化的下一次调用的计划。</span><span class="sxs-lookup"><span data-stu-id="9b727-134">`DurableOrchestrationContext`'s `CreateTimer` method sets up the schedule for the next invocation of the loop to check for stock price changes.</span></span> <span data-ttu-id="9b727-135">`DurableOrchestrationContext` 还具有 `CurrentUtcDateTime` 属性，用于获取 UTC 格式的当前日期时间值。</span><span class="sxs-lookup"><span data-stu-id="9b727-135">`DurableOrchestrationContext` also has a `CurrentUtcDateTime` property to get the current DateTime value in UTC.</span></span> <span data-ttu-id="9b727-136">最好使用此属性而不是 `DateTime.UtcNow`，因为它易于模拟进行测试。</span><span class="sxs-lookup"><span data-stu-id="9b727-136">It's better to use this property instead of `DateTime.UtcNow` because it's easily mocked for testing.</span></span>

## <a name="recommended-resources"></a><span data-ttu-id="9b727-137">推荐的资源</span><span class="sxs-lookup"><span data-stu-id="9b727-137">Recommended resources</span></span>

- [<span data-ttu-id="9b727-138">Azure Durable Functions</span><span class="sxs-lookup"><span data-stu-id="9b727-138">Azure Durable Functions</span></span>](/azure/azure-functions/durable-functions-overview)
- [<span data-ttu-id="9b727-139">.NET Core 和 .NET Standard 中的单元测试</span><span class="sxs-lookup"><span data-stu-id="9b727-139">Unit Testing in .NET Core and .NET Standard</span></span>](../../core/testing/index.md)

>[!div class="step-by-step"]
><span data-ttu-id="9b727-140">[上一页](durable-azure-functions.md)
>[下一页](serverless-business-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="9b727-140">[Previous](durable-azure-functions.md)
[Next](serverless-business-scenarios.md)</span></span>

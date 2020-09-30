---
title: 持久 Azure 函数 - 无服务器应用
description: 持久 Azure 函数将扩展 Azure Functions 运行时，以便在代码中启用有状态的工作流。
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 1498b5a19bc92b7db16f7422a35ac3afffb82b60
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171788"
---
# <a name="durable-azure-functions"></a><span data-ttu-id="f0452-103">持久 Azure 函数</span><span class="sxs-lookup"><span data-stu-id="f0452-103">Durable Azure functions</span></span>

<span data-ttu-id="f0452-104">使用 Azure Functions 创建无服务器应用程序时，操作通常会设计为以无状态方式运行。</span><span class="sxs-lookup"><span data-stu-id="f0452-104">When creating serverless applications with Azure Functions, your operations will typically be designed to run in a stateless manner.</span></span> <span data-ttu-id="f0452-105">选择此设计是因为，随着平台规模的不断增加，很难知道代码运行在哪些服务器上。</span><span class="sxs-lookup"><span data-stu-id="f0452-105">The reason for this design choice is because as the platform scales, it becomes difficult to know what servers the code is running on.</span></span> <span data-ttu-id="f0452-106">也很难知道任意给定点上有多少实例处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="f0452-106">It also becomes difficult to know how many instances are active at any given point.</span></span> <span data-ttu-id="f0452-107">但是，有些应用程序类需要知道进程的当前状态。</span><span class="sxs-lookup"><span data-stu-id="f0452-107">However, there are classes of applications that require the current state of a process to be known.</span></span> <span data-ttu-id="f0452-108">考虑向在线商店提交订单的过程。</span><span class="sxs-lookup"><span data-stu-id="f0452-108">Consider the process of submitting an order to an online store.</span></span> <span data-ttu-id="f0452-109">签出操作可能是由多个需要知道进程状态的操作组成的工作流。</span><span class="sxs-lookup"><span data-stu-id="f0452-109">The checkout operation might be a workflow that is composed of multiple operations that need to know the state of the process.</span></span> <span data-ttu-id="f0452-110">如果客户在其帐户上有任何信用额度，以及处理信用卡的结果，则此类信息可能包括产品清单。</span><span class="sxs-lookup"><span data-stu-id="f0452-110">Such information may include the product inventory, if the customer has any credits on their account, and also the results of processing the credit card.</span></span> <span data-ttu-id="f0452-111">这些操作可以很容易地成为它们自己的内部工作流，甚至是来自第三方系统的服务。</span><span class="sxs-lookup"><span data-stu-id="f0452-111">These operations could easily be their own internal workflows or even services from third-party systems.</span></span>

<span data-ttu-id="f0452-112">目前存在多种模式，这些模式可帮助协调内部和外部系统之间的应用程序状态。</span><span class="sxs-lookup"><span data-stu-id="f0452-112">Various patterns exist today that assist with the coordination of application state between internal and external systems.</span></span> <span data-ttu-id="f0452-113">这是一种很常见的解决方案，这些解决方案依赖于集中式队列系统、分布式键值存储或共享数据库来管理此状态。</span><span class="sxs-lookup"><span data-stu-id="f0452-113">It's common to come across solutions that rely on centralized queuing systems, distributed key-value stores, or shared databases to manage that state.</span></span> <span data-ttu-id="f0452-114">不过，这些是现在需要设置和管理的所有其他资源。</span><span class="sxs-lookup"><span data-stu-id="f0452-114">However, these are all additional resources that now need to be provisioned and managed.</span></span> <span data-ttu-id="f0452-115">在无服务器环境中，尝试手动协调这些资源可能会变得非常麻烦。</span><span class="sxs-lookup"><span data-stu-id="f0452-115">In a serverless environment, your code could become cumbersome trying to coordinate with these resources manually.</span></span> <span data-ttu-id="f0452-116">Azure Functions 提供了一种替代方法，用于创建名为 Durable Functions 的有状态函数。</span><span class="sxs-lookup"><span data-stu-id="f0452-116">Azure Functions offers an alternative for creating stateful functions called Durable Functions.</span></span>

<span data-ttu-id="f0452-117">Durable Functions 是 Azure Functions 运行时的扩展，可在代码中启用有状态工作流的定义。</span><span class="sxs-lookup"><span data-stu-id="f0452-117">Durable Functions is an extension to the Azure Functions runtime that enables the definition of stateful workflows in code.</span></span> <span data-ttu-id="f0452-118">通过将工作流分解为活动，Durable Functions 扩展可以管理状态、创建进度检查点，并处理跨服务器的函数调用分布。</span><span class="sxs-lookup"><span data-stu-id="f0452-118">By breaking down workflows into activities, the Durable Functions extension can manage state, create progress checkpoints, and handle the distribution of function calls across servers.</span></span> <span data-ttu-id="f0452-119">在后台，它利用 Azure 存储帐户来持久保存执行历史记录、计划活动函数和检索响应。</span><span class="sxs-lookup"><span data-stu-id="f0452-119">In the background, it makes use of an Azure Storage account to persist execution history, schedule activity functions and retrieve responses.</span></span> <span data-ttu-id="f0452-120">无服务器代码决不应与此存储帐户中的持久信息进行交互，通常也无需与开发人员进行交互。</span><span class="sxs-lookup"><span data-stu-id="f0452-120">Your serverless code should never interact with persisted information in that storage account, and is typically not something with which developers need to interact.</span></span>

## <a name="triggering-a-stateful-workflow"></a><span data-ttu-id="f0452-121">触发有状态工作流</span><span class="sxs-lookup"><span data-stu-id="f0452-121">Triggering a stateful workflow</span></span>

<span data-ttu-id="f0452-122">Durable Functions 中的有状态工作流可以分解为两个内部组件；业务流程和活动触发器。</span><span class="sxs-lookup"><span data-stu-id="f0452-122">Stateful workflows in Durable Functions can be broken down into two intrinsic components; orchestration and activity triggers.</span></span> <span data-ttu-id="f0452-123">触发器和绑定是 Azure Functions 用来让你的无服务器函数在启动、接收输入和返回结果时获得通知的核心组件。</span><span class="sxs-lookup"><span data-stu-id="f0452-123">Triggers and bindings are core components used by Azure Functions to enable your serverless functions to be notified when to start, receive input, and return results.</span></span>

### <a name="working-with-the-orchestration-client"></a><span data-ttu-id="f0452-124">使用业务流程客户端</span><span class="sxs-lookup"><span data-stu-id="f0452-124">Working with the Orchestration client</span></span>

<span data-ttu-id="f0452-125">与 Azure Functions 中的触发操作的其他样式相比，业务流程是唯一的。</span><span class="sxs-lookup"><span data-stu-id="f0452-125">Orchestrations are unique when compared to other styles of triggered operations in Azure Functions.</span></span> <span data-ttu-id="f0452-126">Durable Functions 允许执行可能需要数小时甚至数天才能完成的函数。</span><span class="sxs-lookup"><span data-stu-id="f0452-126">Durable Functions enables the execution of functions that may take hours or even days to complete.</span></span> <span data-ttu-id="f0452-127">这种类型的行为需要能够检查正在运行的业务流程的状态，提前终止或发送外部事件的通知。</span><span class="sxs-lookup"><span data-stu-id="f0452-127">That type of behavior comes with the need to able to check the status of a running orchestration, preemptively terminate, or send notifications of external events.</span></span>

<span data-ttu-id="f0452-128">对于这种情况，Durable Functions 扩展提供了 `DurableOrchestrationClient` 类，可用于与已协调的函数进行交互。</span><span class="sxs-lookup"><span data-stu-id="f0452-128">For such cases, the Durable Functions extension provides the `DurableOrchestrationClient` class that allows you to interact with orchestrated functions.</span></span> <span data-ttu-id="f0452-129">你可以使用 `OrchestrationClientAttribute` 绑定来访问业务流程客户端。</span><span class="sxs-lookup"><span data-stu-id="f0452-129">You get access to the orchestration client by using the `OrchestrationClientAttribute` binding.</span></span> <span data-ttu-id="f0452-130">通常，会将此属性与另一种触发器类型（如 `HttpTrigger` 或 `ServiceBusTrigger`）包括在内。</span><span class="sxs-lookup"><span data-stu-id="f0452-130">Generally, you would include this attribute with another trigger type, such as an `HttpTrigger` or `ServiceBusTrigger`.</span></span> <span data-ttu-id="f0452-131">一旦触发了源函数，就可以使用业务流程客户端启动业务流程函数。</span><span class="sxs-lookup"><span data-stu-id="f0452-131">Once the source function has been triggered, the orchestration client can be used to start an orchestrator function.</span></span>

```csharp
[FunctionName("KickOff")]
public static async Task<HttpResponseMessage> Run(
    [HttpTrigger(AuthorizationLevel.Function, "POST")]HttpRequestMessage req,
    [OrchestrationClient ] DurableOrchestrationClient<orchestrationClient>)
{
    OrderRequestData data = await req.Content.ReadAsAsync<OrderRequestData>();

    string instanceId = await orchestrationClient.StartNewAsync("PlaceOrder", data);

    return orchestrationClient.CreateCheckStatusResponse(req, instanceId);
}
```

### <a name="the-orchestrator-function"></a><span data-ttu-id="f0452-132">业务流程协调程序函数</span><span class="sxs-lookup"><span data-stu-id="f0452-132">The orchestrator function</span></span>

<span data-ttu-id="f0452-133">在 Azure Functions 中使用 OrchestrationTriggerAttribute 注释函数，将其用作业务流程协调程序函数。</span><span class="sxs-lookup"><span data-stu-id="f0452-133">Annotating a function with the OrchestrationTriggerAttribute in Azure Functions marks that function as an orchestrator function.</span></span> <span data-ttu-id="f0452-134">负责管理构成有状态工作流的各种活动。</span><span class="sxs-lookup"><span data-stu-id="f0452-134">It's responsible for managing the various activities that make up your stateful workflow.</span></span>

<span data-ttu-id="f0452-135">业务流程协调程序函数无法使用 OrchestrationTriggerAttribute 以外的绑定。</span><span class="sxs-lookup"><span data-stu-id="f0452-135">Orchestrator functions are unable to make use of bindings other than the OrchestrationTriggerAttribute.</span></span> <span data-ttu-id="f0452-136">此属性只能与 DurableOrchestrationContext 参数类型一起使用。</span><span class="sxs-lookup"><span data-stu-id="f0452-136">This attribute can only be used with a parameter type of DurableOrchestrationContext.</span></span> <span data-ttu-id="f0452-137">由于不支持反序列化函数签名中的输入，因此不能使用其他任何输入。</span><span class="sxs-lookup"><span data-stu-id="f0452-137">No other inputs can be used since deserialization of inputs in the function signature isn't supported.</span></span> <span data-ttu-id="f0452-138">若要获取业务流程客户端提供的输入，必须使用 GetInput\<T\> 方法。</span><span class="sxs-lookup"><span data-stu-id="f0452-138">To get inputs provided by the orchestration client, the GetInput\<T\> method must be used.</span></span>

<span data-ttu-id="f0452-139">此外，业务流程函数的返回类型必须是 void、Task 或 JSON 可序列化值。</span><span class="sxs-lookup"><span data-stu-id="f0452-139">Also, the return types of orchestration functions must be either void, Task, or a JSON serializable value.</span></span>

> <span data-ttu-id="f0452-140">*为简洁起见，已省略错误处理代码*</span><span class="sxs-lookup"><span data-stu-id="f0452-140">*Error handling code has been left out for brevity*</span></span>

```csharp
[FunctionName("PlaceOrder")]
public static async Task<string> PlaceOrder([OrchestrationTrigger] DurableOrchestrationContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    await context.CallActivityAsync<bool>("CheckAndReserveInventory", orderData);
    await context.CallActivityAsync<string>("ProcessPayment", orderData);

    string trackingNumber = await context.CallActivityAsync<string>("ScheduleShipping", orderData);
    await context.CallActivityAsync<string>("EmailCustomer", trackingNumber);

    return trackingNumber;
}
```

<span data-ttu-id="f0452-141">可以同时启动并运行多个业务流程实例。</span><span class="sxs-lookup"><span data-stu-id="f0452-141">Multiple instances of an orchestration can be started and running at the same time.</span></span> <span data-ttu-id="f0452-142">对 `DurableOrchestrationClient` 调用 `StartNewAsync` 方法将启动业务流程的新实例。</span><span class="sxs-lookup"><span data-stu-id="f0452-142">Calling the `StartNewAsync` method on the `DurableOrchestrationClient` launches a new instance of the orchestration.</span></span> <span data-ttu-id="f0452-143">方法返回在业务流程启动时完成的 `Task<string>`。</span><span class="sxs-lookup"><span data-stu-id="f0452-143">The method returns a `Task<string>` that completes when the orchestration has started.</span></span> <span data-ttu-id="f0452-144">如果业务流程未在 30 秒内启动，则会引发 `TimeoutException` 类型的异常。</span><span class="sxs-lookup"><span data-stu-id="f0452-144">An exception of type `TimeoutException` gets thrown if the orchestration hasn't started within 30 seconds.</span></span>

<span data-ttu-id="f0452-145">从 `StartNewAsync` 完成的 `Task<string>` 应包含业务流程实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="f0452-145">The completed `Task<string>` from `StartNewAsync` should contain the unique ID of the orchestration instance.</span></span> <span data-ttu-id="f0452-146">此实例 ID 可用于在该特定业务流程上的调用操作。</span><span class="sxs-lookup"><span data-stu-id="f0452-146">This instance ID can be used to invoke operations on that specific orchestration.</span></span> <span data-ttu-id="f0452-147">可以查询业务流程以获取状态或发送事件通知。</span><span class="sxs-lookup"><span data-stu-id="f0452-147">The orchestration can be queried for the status or sent event notifications.</span></span>

### <a name="the-activity-functions"></a><span data-ttu-id="f0452-148">活动函数</span><span class="sxs-lookup"><span data-stu-id="f0452-148">The activity functions</span></span>

<span data-ttu-id="f0452-149">活动函数是可在业务流程函数内组合在一起以创建工作流的离散操作。</span><span class="sxs-lookup"><span data-stu-id="f0452-149">Activity functions are the discrete operations that get composed together within an orchestration function to create the workflow.</span></span> <span data-ttu-id="f0452-150">大多数情况下，大多数实际工作都是在这里进行。</span><span class="sxs-lookup"><span data-stu-id="f0452-150">Here is where most of actual work would take place.</span></span> <span data-ttu-id="f0452-151">它们表示业务逻辑，长时间运行的进程，以及更大的解决方案中的难题。</span><span class="sxs-lookup"><span data-stu-id="f0452-151">They represent the business logic, long running processes, and the puzzle pieces to a larger solution.</span></span>

<span data-ttu-id="f0452-152">`ActivityTriggerAttribute` 可用于注释 `DurableActivityContext` 类型的函数参数。</span><span class="sxs-lookup"><span data-stu-id="f0452-152">The `ActivityTriggerAttribute` is used to annotate a function parameter of type `DurableActivityContext`.</span></span> <span data-ttu-id="f0452-153">使用注释通知运行时，此函数将计划用作活动函数。</span><span class="sxs-lookup"><span data-stu-id="f0452-153">Using the annotation informs the runtime that the function is intended to be used as an activity function.</span></span> <span data-ttu-id="f0452-154">使用 `DurableActivityContext` 参数的 `GetInput<T>` 方法检索活动函数的输入值。</span><span class="sxs-lookup"><span data-stu-id="f0452-154">Input values to activity functions are retrieved using the `GetInput<T>` method of the `DurableActivityContext` parameter.</span></span>

<span data-ttu-id="f0452-155">与业务流程函数类似，活动的返回类型必须是 void、Task 或 JSON 可序列化值。</span><span class="sxs-lookup"><span data-stu-id="f0452-155">Similar to orchestration functions, the return types of activity functions must be either void, Task, or a JSON serializable value.</span></span>

<span data-ttu-id="f0452-156">活动函数中引发的任何未经处理的异常都将发送到调用业务流程协调程序函数并显示为 `TaskFailedException`。</span><span class="sxs-lookup"><span data-stu-id="f0452-156">Any unhandled exceptions that get thrown within activity functions will get sent up to the calling orchestrator function and presented as a `TaskFailedException`.</span></span> <span data-ttu-id="f0452-157">此时，可以在业务流程协调程序中捕获并记录错误，并且可以重试此活动。</span><span class="sxs-lookup"><span data-stu-id="f0452-157">At this point, the error can be caught and logged in the orchestrator, and the activity can be retried.</span></span>

```csharp
[FunctionName("CheckAndReserveInventory")]
public static bool CheckAndReserveInventory([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    // Connect to inventory system and try to reserve items
    return true;
}
```

## <a name="recommended-resources"></a><span data-ttu-id="f0452-158">推荐的资源</span><span class="sxs-lookup"><span data-stu-id="f0452-158">Recommended resources</span></span>

- [<span data-ttu-id="f0452-159">Durable Functions</span><span class="sxs-lookup"><span data-stu-id="f0452-159">Durable Functions</span></span>](/azure/azure-functions/durable-functions-overview)
- [<span data-ttu-id="f0452-160">Durable Functions 的绑定</span><span class="sxs-lookup"><span data-stu-id="f0452-160">Bindings for Durable Functions</span></span>](/azure/azure-functions/durable-functions-bindings)
- [<span data-ttu-id="f0452-161">在 Durable Functions 中管理实例</span><span class="sxs-lookup"><span data-stu-id="f0452-161">Manage instances in Durable Functions</span></span>](/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
><span data-ttu-id="f0452-162">[上一页](event-grid.md)
>[下一页](orchestration-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="f0452-162">[Previous](event-grid.md)
[Next](orchestration-patterns.md)</span></span>

---
title: Application Insights - 无服务器应用
description: Application Insights 是一个无服务器诊断平台，使开发人员能够检测、会审和诊断 Web 应用、移动应用、桌面应用和微服务中的问题。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 42791b052ebb068c9b7109291e66b30b47e5821f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173316"
---
# <a name="telemetry-with-application-insights"></a><span data-ttu-id="414da-103">使用 Application Insights 遥测</span><span class="sxs-lookup"><span data-stu-id="414da-103">Telemetry with Application Insights</span></span>

<span data-ttu-id="414da-104">[Application Insights](/azure/application-insights) 是一个无服务器诊断平台，使开发人员能够检测、会审和诊断 Web 应用、移动应用、桌面应用和微服务中的问题。</span><span class="sxs-lookup"><span data-stu-id="414da-104">[Application Insights](/azure/application-insights) is a serverless diagnostics platform that enables developers to detect, triage, and diagnose issues in web apps, mobile apps, desktop apps, and microservices.</span></span> <span data-ttu-id="414da-105">只需在门户中翻转开关，即可打开 Application Insights 进入函数应用。</span><span class="sxs-lookup"><span data-stu-id="414da-105">You can turn on Application Insights for function apps simply by flipping a switch in the portal.</span></span> <span data-ttu-id="414da-106">Application Insights 提供所有这些功能，而无需配置服务器或设置自己的数据库。</span><span class="sxs-lookup"><span data-stu-id="414da-106">Application Insights provides all of these capabilities without you having to configure a server or set up your own database.</span></span> <span data-ttu-id="414da-107">所有 Application Insights 功能都作为可自动与你的应用集成的服务提供。</span><span class="sxs-lookup"><span data-stu-id="414da-107">All of Application Insights' capabilities are provided as a service that automatically integrates with your apps.</span></span>

![Application Insights 徽标](./media/application-insights-logo.png)

<span data-ttu-id="414da-109">将 Application Insights 添加到现有应用程序就像将检测密钥添加到应用程序设置一样容易。</span><span class="sxs-lookup"><span data-stu-id="414da-109">Adding Application Insights to existing apps is as easy as adding an instrumentation key to your application's settings.</span></span> <span data-ttu-id="414da-110">使用 Application Insights 可以：</span><span class="sxs-lookup"><span data-stu-id="414da-110">With Application Insights you can:</span></span>

- <span data-ttu-id="414da-111">根据指标创建自定义图表和警报，例如函数调用次数、运行函数所需时间以及异常</span><span class="sxs-lookup"><span data-stu-id="414da-111">Create custom charts and alerts based on metrics such as number of function invocations, the time it takes to run a function, and exceptions</span></span>
- <span data-ttu-id="414da-112">分析失败和服务器异常</span><span class="sxs-lookup"><span data-stu-id="414da-112">Analyze failures and server exceptions</span></span>
- <span data-ttu-id="414da-113">通过操作深入了解性能，并衡量调用第三方依赖项所花费的时间</span><span class="sxs-lookup"><span data-stu-id="414da-113">Drill into performance by operation and measure the time it takes to call third-party dependencies</span></span>
- <span data-ttu-id="414da-114">监视托管函数应用的所有服务器上的 CPU 使用情况、内存和速率</span><span class="sxs-lookup"><span data-stu-id="414da-114">Monitor CPU usage, memory, and rates across all servers that host your function apps</span></span>
- <span data-ttu-id="414da-115">查看实时指标流，包括函数应用的请求计数和延迟</span><span class="sxs-lookup"><span data-stu-id="414da-115">View a live stream of metrics including request count and latency for your function apps</span></span>
- <span data-ttu-id="414da-116">使用 [Analytics](/azure/application-insights/app-insights-analytics) 搜索、查询函数数据并据此创建自定义图表</span><span class="sxs-lookup"><span data-stu-id="414da-116">Use [Analytics](/azure/application-insights/app-insights-analytics) to search, query, and create custom charts over your function data</span></span>

![指标资源管理器](./media/metrics-explorer.png)

<span data-ttu-id="414da-118">除了内置遥测，还可以生成自定义遥测。</span><span class="sxs-lookup"><span data-stu-id="414da-118">In addition to built-in telemetry, it's also possible to generate custom telemetry.</span></span> <span data-ttu-id="414da-119">以下代码片段使用为函数应用设置的检测密钥来创建自定义遥测客户端：</span><span class="sxs-lookup"><span data-stu-id="414da-119">The following code snippet creates a custom telemetry client using the instrumentation key set for the function app:</span></span>

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

<span data-ttu-id="414da-120">下面的代码测量了在 [Azure 表存储](/azure/cosmos-db/table-storage-overview) 实例中插入新行所用的时间：</span><span class="sxs-lookup"><span data-stu-id="414da-120">The following code measures how long it takes to insert a new row into an [Azure Table Storage](/azure/cosmos-db/table-storage-overview) instance:</span></span>

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

<span data-ttu-id="414da-121">生成的性能图表如下所示：</span><span class="sxs-lookup"><span data-stu-id="414da-121">The resulting performance graph is shown:</span></span>

![自定义遥测](./media/custom-telemetry.png)

<span data-ttu-id="414da-123">自定义遥测显示了插入新行的平均时间为 32.6 毫秒。</span><span class="sxs-lookup"><span data-stu-id="414da-123">The custom telemetry reveals the average time to insert a new row is 32.6 milliseconds.</span></span>

<span data-ttu-id="414da-124">Application Insights 提供了一种强大而便捷的方式来记录有关无服务器应用程序的详细遥测。</span><span class="sxs-lookup"><span data-stu-id="414da-124">Application Insights provides a powerful, convenient way to log detailed telemetry about your serverless applications.</span></span> <span data-ttu-id="414da-125">你可以完全控制所提供的跟踪和日志记录级别。</span><span class="sxs-lookup"><span data-stu-id="414da-125">You have full control over the level of tracing and logging that is provided.</span></span> <span data-ttu-id="414da-126">可以跟踪自定义统计信息，如事件、依赖项和页面视图。</span><span class="sxs-lookup"><span data-stu-id="414da-126">You can track custom statistics such as events, dependencies, and page view.</span></span> <span data-ttu-id="414da-127">最后，利用强大的分析功能，可以编写查询来询问重要问题并生成图表和高级见解。</span><span class="sxs-lookup"><span data-stu-id="414da-127">Finally, the powerful analytics enable you to write queries that ask important questions and generate charts and advanced insights.</span></span>

<span data-ttu-id="414da-128">有关详细信息，请参阅[监视 Azure Functions](/azure/azure-functions/functions-monitoring)。</span><span class="sxs-lookup"><span data-stu-id="414da-128">For more information, see [Monitor Azure Functions](/azure/azure-functions/functions-monitoring).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="414da-129">[上一页](azure-functions.md)
>[下一页](logic-apps.md)</span><span class="sxs-lookup"><span data-stu-id="414da-129">[Previous](azure-functions.md)
[Next](logic-apps.md)</span></span>

---
title: 使用 .NET Core 中的 EventCounters 衡量性能
description: 本教程将介绍如何使用 EventCounters 衡量性能。
ms.date: 08/07/2020
ms.topic: tutorial
ms.openlocfilehash: db9a0889d46cc4db02baac60cbed6f6e0ba6856b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538561"
---
# <a name="tutorial-measure-performance-using-eventcounters-in-net-core"></a><span data-ttu-id="a7955-103">教程：使用 .NET Core 中的 EventCounters 衡量性能</span><span class="sxs-lookup"><span data-stu-id="a7955-103">Tutorial: Measure performance using EventCounters in .NET Core</span></span>

<span data-ttu-id="a7955-104">**本文适用于：** ✔️ .NET Core 3.0 SDK 及更高版本</span><span class="sxs-lookup"><span data-stu-id="a7955-104">**This article applies to: ✔️** .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="a7955-105">本教程将介绍如何使用 <xref:System.Diagnostics.Tracing.EventCounter> 衡量高频率事件的性能。</span><span class="sxs-lookup"><span data-stu-id="a7955-105">In this tutorial, you'll learn how an <xref:System.Diagnostics.Tracing.EventCounter> can be used to measure performance with a high frequency of events.</span></span> <span data-ttu-id="a7955-106">可以使用由各种官方 .NET Core 包或第三方提供者发布的[可用的计数器](event-counters.md#available-counters)，或创建自己的监视指标。</span><span class="sxs-lookup"><span data-stu-id="a7955-106">You can use the [available counters](event-counters.md#available-counters) published by various official .NET Core packages, third-party providers, or create your own metrics for monitoring.</span></span>

<span data-ttu-id="a7955-107">在本教程中，将：</span><span class="sxs-lookup"><span data-stu-id="a7955-107">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="a7955-108">实现 <xref:System.Diagnostics.Tracing.EventSource>。</span><span class="sxs-lookup"><span data-stu-id="a7955-108">Implement an <xref:System.Diagnostics.Tracing.EventSource>.</span></span>
> - <span data-ttu-id="a7955-109">利用 [dotnet-counters](dotnet-counters.md) 监视计数器。</span><span class="sxs-lookup"><span data-stu-id="a7955-109">Monitor counters with [dotnet-counters](dotnet-counters.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a7955-110">先决条件</span><span class="sxs-lookup"><span data-stu-id="a7955-110">Prerequisites</span></span>

<span data-ttu-id="a7955-111">本教程使用：</span><span class="sxs-lookup"><span data-stu-id="a7955-111">The tutorial uses:</span></span>

- <span data-ttu-id="a7955-112">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="a7955-112">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="a7955-113">[dotnet-counters](dotnet-counters.md) 监视事件计数器。</span><span class="sxs-lookup"><span data-stu-id="a7955-113">[dotnet-counters](dotnet-counters.md) to monitor event counters.</span></span>
- <span data-ttu-id="a7955-114">要诊断的[示例调试目标](/samples/dotnet/samples/diagnostic-scenarios)应用。</span><span class="sxs-lookup"><span data-stu-id="a7955-114">A [sample debug target](/samples/dotnet/samples/diagnostic-scenarios) app to diagnose.</span></span>

## <a name="get-the-source"></a><span data-ttu-id="a7955-115">获取源</span><span class="sxs-lookup"><span data-stu-id="a7955-115">Get the source</span></span>

<span data-ttu-id="a7955-116">示例应用程序将用作监视的基础。</span><span class="sxs-lookup"><span data-stu-id="a7955-116">The sample application will be used as a basis for monitoring.</span></span> <span data-ttu-id="a7955-117">示例浏览器中提供了[示例 ASP.NET Core 存储库](/samples/dotnet/samples/diagnostic-scenarios)。</span><span class="sxs-lookup"><span data-stu-id="a7955-117">The [sample ASP.NET Core repository](/samples/dotnet/samples/diagnostic-scenarios) is available from the samples browser.</span></span> <span data-ttu-id="a7955-118">下载 zip 文件，下载后提取它，并在你喜欢的 IDE 中打开它。</span><span class="sxs-lookup"><span data-stu-id="a7955-118">You download the zip file, extract it once downloaded, and open it in your favorite IDE.</span></span> <span data-ttu-id="a7955-119">生成并运行应用程序以确保它正常工作，然后停止应用程序。</span><span class="sxs-lookup"><span data-stu-id="a7955-119">Build and run the application to ensure that it works properly, then stop the application.</span></span>

## <a name="implement-an-eventsource"></a><span data-ttu-id="a7955-120">实现 EventSource</span><span class="sxs-lookup"><span data-stu-id="a7955-120">Implement an EventSource</span></span>

<span data-ttu-id="a7955-121">对于每隔几毫秒发生的事件，最好使每个事件的开销较低（小于一毫秒）。</span><span class="sxs-lookup"><span data-stu-id="a7955-121">For events that happen every few milliseconds, you'll want the overhead per event to be low (less than a millisecond).</span></span> <span data-ttu-id="a7955-122">否则，对性能的影响将很大。</span><span class="sxs-lookup"><span data-stu-id="a7955-122">Otherwise, the impact on performance will be significant.</span></span> <span data-ttu-id="a7955-123">记录事件意味着你将向磁盘写入内容。</span><span class="sxs-lookup"><span data-stu-id="a7955-123">Logging an event means you're going to write something to disk.</span></span> <span data-ttu-id="a7955-124">如果磁盘不够快，你将丢失事件。</span><span class="sxs-lookup"><span data-stu-id="a7955-124">If the disk is not fast enough, you will lose events.</span></span> <span data-ttu-id="a7955-125">你需要一个解决方案，而不是记录事件本身。</span><span class="sxs-lookup"><span data-stu-id="a7955-125">You need a solution other than logging the event itself.</span></span>

<span data-ttu-id="a7955-126">在处理大量事件时，了解每个事件的度量值也无济于事。</span><span class="sxs-lookup"><span data-stu-id="a7955-126">When dealing with a large number of events, knowing the measure per event is not useful either.</span></span> <span data-ttu-id="a7955-127">大多数时候，你只需要一些统计信息。</span><span class="sxs-lookup"><span data-stu-id="a7955-127">Most of the time all you need is just some statistics out of it.</span></span> <span data-ttu-id="a7955-128">因此，你可以在进程本身中获取统计信息，然后偶尔编写一个事件来报告统计信息，这是 <xref:System.Diagnostics.Tracing.EventCounter> 将执行的操作。</span><span class="sxs-lookup"><span data-stu-id="a7955-128">So you could get the statistics within the process itself and then write an event once in a while to report the statistics, that's what <xref:System.Diagnostics.Tracing.EventCounter> will do.</span></span>

<span data-ttu-id="a7955-129">下面是有关如何实现 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> 的示例。</span><span class="sxs-lookup"><span data-stu-id="a7955-129">Below is an example of how to implement an <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName>.</span></span> <span data-ttu-id="a7955-130">创建名为 MinimalEventCounterSource.cs 的新文件，并使用代码片段作为其源：</span><span class="sxs-lookup"><span data-stu-id="a7955-130">Create a new file named *MinimalEventCounterSource.cs* and use the code snippet as its source:</span></span>

:::code language="csharp" source="snippets/EventCounters/MinimalEventCounterSource.cs":::

<span data-ttu-id="a7955-131"><xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=nameWithType> 行是 <xref:System.Diagnostics.Tracing.EventSource> 部分，而不是 <xref:System.Diagnostics.Tracing.EventCounter> 的一部分，编写它是为了表明你可以一起记录消息和事件计数器。</span><span class="sxs-lookup"><span data-stu-id="a7955-131">The <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=nameWithType> line is the <xref:System.Diagnostics.Tracing.EventSource> part and is not part of <xref:System.Diagnostics.Tracing.EventCounter>, it was written to show that you can log a message together with the event counter.</span></span>

## <a name="add-an-action-filter"></a><span data-ttu-id="a7955-132">添加操作筛选器</span><span class="sxs-lookup"><span data-stu-id="a7955-132">Add an action filter</span></span>

<span data-ttu-id="a7955-133">示例源代码是 ASP.NET Core 项目。</span><span class="sxs-lookup"><span data-stu-id="a7955-133">The sample source code is an ASP.NET Core project.</span></span> <span data-ttu-id="a7955-134">可以全局添加将记录总请求时间的[操作筛选器](/aspnet/core/mvc/controllers/filters#action-filters)。</span><span class="sxs-lookup"><span data-stu-id="a7955-134">You can add an [action filter](/aspnet/core/mvc/controllers/filters#action-filters) globally that will log the total request time.</span></span> <span data-ttu-id="a7955-135">创建名为 LogRequestTimeFilterAttribute.cs 的新文件，并使用以下代码：</span><span class="sxs-lookup"><span data-stu-id="a7955-135">Create a new file named *LogRequestTimeFilterAttribute.cs*, and use the following code:</span></span>

```csharp
using System.Diagnostics;
using Microsoft.AspNetCore.Http.Extensions;
using Microsoft.AspNetCore.Mvc.Filters;

namespace DiagnosticScenarios
{
    public class LogRequestTimeFilterAttribute : ActionFilterAttribute
    {
        readonly Stopwatch _stopwatch = new Stopwatch();

        public override void OnActionExecuting(ActionExecutingContext context) => _stopwatch.Start();

        public override void OnActionExecuted(ActionExecutedContext context)
        {
            _stopwatch.Stop();

            MinimalEventCounterSource.Log.Request(
                context.HttpContext.Request.GetDisplayUrl(), _stopwatch.ElapsedMilliseconds);
        }
    }
}
```

<span data-ttu-id="a7955-136">操作筛选器在请求开始时启动 <xref:System.Diagnostics.Stopwatch>，并在其完成后停止，捕获运行时间。</span><span class="sxs-lookup"><span data-stu-id="a7955-136">The action filter starts a <xref:System.Diagnostics.Stopwatch> as the request begins, and stops after it has completed, capturing the elapsed time.</span></span> <span data-ttu-id="a7955-137">总毫秒数记录到 `MinimalEventCounterSource` 单一实例。</span><span class="sxs-lookup"><span data-stu-id="a7955-137">The total milliseconds is logged to the `MinimalEventCounterSource` singleton instance.</span></span> <span data-ttu-id="a7955-138">为了应用此筛选器，需要将其添加到筛选器集合。</span><span class="sxs-lookup"><span data-stu-id="a7955-138">In order for this filter to be applied, you need to add it to the filters collection.</span></span> <span data-ttu-id="a7955-139">在 Startup.cs 文件中，更新包含此筛选器的 `ConfigureServices` 方法。</span><span class="sxs-lookup"><span data-stu-id="a7955-139">In the *Startup.cs* file, update the `ConfigureServices` method in include this filter.</span></span>

```csharp
public void ConfigureServices(IServiceCollection services) =>
    services.AddControllers(options => options.Filters.Add<LogRequestTimeFilterAttribute>())
            .AddNewtonsoftJson();
```

## <a name="monitor-event-counter"></a><span data-ttu-id="a7955-140">监视事件计数器</span><span class="sxs-lookup"><span data-stu-id="a7955-140">Monitor event counter</span></span>

<span data-ttu-id="a7955-141">通过 <xref:System.Diagnostics.Tracing.EventSource> 上的实现和自定义操作筛选器，生成和启动应用程序。</span><span class="sxs-lookup"><span data-stu-id="a7955-141">With the implementation on an <xref:System.Diagnostics.Tracing.EventSource> and the custom action filter, build and launch the application.</span></span>
<span data-ttu-id="a7955-142">你已将指标记录到 <xref:System.Diagnostics.Tracing.EventCounter> 中，但除非你从其中访问统计信息，否则它将不起作用。</span><span class="sxs-lookup"><span data-stu-id="a7955-142">You logged the metric to the <xref:System.Diagnostics.Tracing.EventCounter>, but unless you access the statistics from of it, it is not useful.</span></span> <span data-ttu-id="a7955-143">要获取统计信息，需要通过创建以所需事件频率触发的计时器来启用 <xref:System.Diagnostics.Tracing.EventCounter>，并启用侦听器来捕获事件。</span><span class="sxs-lookup"><span data-stu-id="a7955-143">To get the statistics, you need to enable the <xref:System.Diagnostics.Tracing.EventCounter> by creating a timer that fires as frequently as you want the events, as well as a listener to capture the events.</span></span> <span data-ttu-id="a7955-144">为此，可以使用 [dotnet-counters](dotnet-counters.md)。</span><span class="sxs-lookup"><span data-stu-id="a7955-144">To do that, you can use [dotnet-counters](dotnet-counters.md).</span></span>

<span data-ttu-id="a7955-145">使用 [dotnet-counters ps](dotnet-counters.md#dotnet-counters-ps) 命令来显示可监视的 .NET 进程的列表。</span><span class="sxs-lookup"><span data-stu-id="a7955-145">Use the [dotnet-counters ps](dotnet-counters.md#dotnet-counters-ps) command to display a list of .NET processes that can be monitored.</span></span>

```console
dotnet-counters ps
```

<span data-ttu-id="a7955-146">通过使用 `dotnet-counters ps` 命令的输出中的进程标识符，你可以使用以下 `dotnet-counters monitor` 命令开始监视事件计数器：</span><span class="sxs-lookup"><span data-stu-id="a7955-146">Using the process identifier from the output of the `dotnet-counters ps` command, you can start monitoring the event counter with the following `dotnet-counters monitor` command:</span></span>

```console
dotnet-counters monitor --process-id 2196 Sample.EventCounter.Minimal Microsoft.AspNetCore.Hosting[total-requests,requests-per-second] System.Runtime[cpu-usage]
```

<span data-ttu-id="a7955-147">当 `dotnet-counters monitor` 命令正在运行时，请在浏览器上按住 <kbd>F5</kbd>，以开始向 `https://localhost:5001/api/values` 终结点发出连续请求。</span><span class="sxs-lookup"><span data-stu-id="a7955-147">While the `dotnet-counters monitor` command is running, hold <kbd>F5</kbd> on the browser to start issuing continuous requests to the `https://localhost:5001/api/values` endpoint.</span></span> <span data-ttu-id="a7955-148">几秒后按 <kbd>q</kbd> 以停止</span><span class="sxs-lookup"><span data-stu-id="a7955-148">After a few seconds stop by pressing <kbd>q</kbd></span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[Microsoft.AspNetCore.Hosting]
    Request Rate / 1 sec                               9
    Total Requests                                   134
[System.Runtime]
    CPU Usage (%)                                     13
[Sample.EventCounter.Minimal]
    Request Processing Time (ms)                      34.5
```

<span data-ttu-id="a7955-149">`dotnet-counters monitor` 命令非常适合主动监视。</span><span class="sxs-lookup"><span data-stu-id="a7955-149">The `dotnet-counters monitor` command is great for active monitoring.</span></span> <span data-ttu-id="a7955-150">不过，可以收集这些诊断指标以便进行后续处理和分析。</span><span class="sxs-lookup"><span data-stu-id="a7955-150">However, you may want to collect these diagnostic metrics for post processing and analysis.</span></span> <span data-ttu-id="a7955-151">为此，请使用 `dotnet-counters collect` 命令。</span><span class="sxs-lookup"><span data-stu-id="a7955-151">For that, use the `dotnet-counters collect` command.</span></span> <span data-ttu-id="a7955-152">`collect` 开关命令类似于 `monitor` 命令，但接受几个其他参数。</span><span class="sxs-lookup"><span data-stu-id="a7955-152">The `collect` switch command is similar to the `monitor` command, but accepts a few additional parameters.</span></span> <span data-ttu-id="a7955-153">你可以指定所需的输出文件名和格式。</span><span class="sxs-lookup"><span data-stu-id="a7955-153">You can specify the desired output file name and format.</span></span> <span data-ttu-id="a7955-154">对于名为 diagnostics.json 的 JSON 文件，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="a7955-154">For a JSON file named *diagnostics.json* use the following command:</span></span>

```console
dotnet-counters collect --process-id 2196 --format json -o diagnostics.json Sample.EventCounter.Minimal Microsoft.AspNetCore.Hosting[total-requests,requests-per-second] System.Runtime[cpu-usage]
```

<span data-ttu-id="a7955-155">再一次，当命令正在运行时，在浏览器上按住 <kbd>F5</kbd>，以开始向 `https://localhost:5001/api/values` 终结点发出连续请求。</span><span class="sxs-lookup"><span data-stu-id="a7955-155">Again, while the command is running, hold <kbd>F5</kbd> on the browser to start issuing continuous requests to the `https://localhost:5001/api/values` endpoint.</span></span> <span data-ttu-id="a7955-156">几秒后按 <kbd>q</kbd> 以停止。</span><span class="sxs-lookup"><span data-stu-id="a7955-156">After a few seconds stop by pressing <kbd>q</kbd>.</span></span> <span data-ttu-id="a7955-157">写入 diagnostics.json 文件。</span><span class="sxs-lookup"><span data-stu-id="a7955-157">The *diagnostics.json* file is written.</span></span> <span data-ttu-id="a7955-158">写入的 JSON 文件不会缩进；但为了提升可读性，在这里进行了缩进。</span><span class="sxs-lookup"><span data-stu-id="a7955-158">The JSON file that is written is not indented, however; for readability it is indented here.</span></span>

```json
{
  "TargetProcess": "DiagnosticScenarios",
  "StartTime": "8/5/2020 3:02:45 PM",
  "Events": [
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "System.Runtime",
      "name": "CPU Usage (%)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Request Rate / 1 sec",
      "counterType": "Rate",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Total Requests",
      "counterType": "Metric",
      "value": 134
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "Sample.EventCounter.Minimal",
      "name": "Request Processing Time (ms)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "System.Runtime",
      "name": "CPU Usage (%)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Request Rate / 1 sec",
      "counterType": "Rate",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Total Requests",
      "counterType": "Metric",
      "value": 134
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "Sample.EventCounter.Minimal",
      "name": "Request Processing Time (ms)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "System.Runtime",
      "name": "CPU Usage (%)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:50Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Request Rate / 1 sec",
      "counterType": "Rate",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:50Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Total Requests",
      "counterType": "Metric",
      "value": 134
    },
    {
      "timestamp": "2020-08-05 15:02:50Z",
      "provider": "Sample.EventCounter.Minimal",
      "name": "Request Processing Time (ms)",
      "counterType": "Metric",
      "value": 0
    }
  ]
}
```

## <a name="next-steps"></a><span data-ttu-id="a7955-159">后续步骤</span><span class="sxs-lookup"><span data-stu-id="a7955-159">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a7955-160">EventCounters</span><span class="sxs-lookup"><span data-stu-id="a7955-160">EventCounters</span></span>](event-counters.md)

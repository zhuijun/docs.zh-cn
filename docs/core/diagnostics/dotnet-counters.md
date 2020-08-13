---
title: dotnet-counters - .NET Core
description: 了解如何安装和使用 dotnet-counter 命令行工具。
ms.date: 02/26/2020
ms.openlocfilehash: 71e3c4f0a60960c4e672b95000bc0d67bd427514
ms.sourcegitcommit: 1e6439ec4d5889fc08cf3bfb4dac2b91931eb827
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2020
ms.locfileid: "88024623"
---
# <a name="dotnet-counters"></a><span data-ttu-id="b5766-103">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="b5766-103">dotnet-counters</span></span>

<span data-ttu-id="b5766-104"> 本文适用于： ✔️ .NET Core 3.0 SDK 及更高版本</span><span class="sxs-lookup"><span data-stu-id="b5766-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-counters"></a><span data-ttu-id="b5766-105">安装 dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="b5766-105">Install dotnet-counters</span></span>

<span data-ttu-id="b5766-106">若要安装最新版 `dotnet-counters` [NuGet 包](https://www.nuget.org/packages/dotnet-counters)，请使用 [dotnet tool install](../tools/dotnet-tool-install.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="b5766-106">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a><span data-ttu-id="b5766-107">摘要</span><span class="sxs-lookup"><span data-stu-id="b5766-107">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="b5766-108">描述</span><span class="sxs-lookup"><span data-stu-id="b5766-108">Description</span></span>

<span data-ttu-id="b5766-109">`dotnet-counters` 是一个性能监视工具，用于临时运行状况监视和初级性能调查。</span><span class="sxs-lookup"><span data-stu-id="b5766-109">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="b5766-110">它可以观察通过 <xref:System.Diagnostics.Tracing.EventCounter> API 发布的性能计数器值。</span><span class="sxs-lookup"><span data-stu-id="b5766-110">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="b5766-111">例如，可以快速监视 CPU 使用情况或 .NET Core 应用程序中引发的异常率，以了解在使用 `PerfView` 或 `dotnet-trace` 深入调查更严重的性能问题之前是否有任何可疑操作。</span><span class="sxs-lookup"><span data-stu-id="b5766-111">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="b5766-112">选项</span><span class="sxs-lookup"><span data-stu-id="b5766-112">Options</span></span>

- **`--version`**

  <span data-ttu-id="b5766-113">显示 dotnet-counters 实用工具的版本。</span><span class="sxs-lookup"><span data-stu-id="b5766-113">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="b5766-114">显示命令行帮助。</span><span class="sxs-lookup"><span data-stu-id="b5766-114">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="b5766-115">命令</span><span class="sxs-lookup"><span data-stu-id="b5766-115">Commands</span></span>

| <span data-ttu-id="b5766-116">命令</span><span class="sxs-lookup"><span data-stu-id="b5766-116">Command</span></span>                                             |
|-----------------------------------------------------|
| [<span data-ttu-id="b5766-117">dotnet-counters collect</span><span class="sxs-lookup"><span data-stu-id="b5766-117">dotnet-counters collect</span></span>](#dotnet-counters-collect) |
| [<span data-ttu-id="b5766-118">dotnet-counters list</span><span class="sxs-lookup"><span data-stu-id="b5766-118">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="b5766-119">dotnet-counters monitor</span><span class="sxs-lookup"><span data-stu-id="b5766-119">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |
| [<span data-ttu-id="b5766-120">dotnet-counters ps</span><span class="sxs-lookup"><span data-stu-id="b5766-120">dotnet-counters ps</span></span>](#dotnet-counters-ps)           |

## <a name="dotnet-counters-collect"></a><span data-ttu-id="b5766-121">dotnet-counters collect</span><span class="sxs-lookup"><span data-stu-id="b5766-121">dotnet-counters collect</span></span>

<span data-ttu-id="b5766-122">定期收集所选计数器的值，并将它们导出为指定的文件格式以进行后续处理。</span><span class="sxs-lookup"><span data-stu-id="b5766-122">Periodically collect selected counter values and export them into a specified file format for post-processing.</span></span>

### <a name="synopsis"></a><span data-ttu-id="b5766-123">摘要</span><span class="sxs-lookup"><span data-stu-id="b5766-123">Synopsis</span></span>

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list] [--format] [-o|--output]
```

### <a name="options"></a><span data-ttu-id="b5766-124">选项</span><span class="sxs-lookup"><span data-stu-id="b5766-124">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="b5766-125">要监视的进程的 ID。</span><span class="sxs-lookup"><span data-stu-id="b5766-125">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="b5766-126">更新显示的计数器之间延迟的秒数</span><span class="sxs-lookup"><span data-stu-id="b5766-126">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="b5766-127">计数器的空格分隔列表。</span><span class="sxs-lookup"><span data-stu-id="b5766-127">A space separated list of counters.</span></span> <span data-ttu-id="b5766-128">计数器可以指定为 `provider_name[:counter_name]`。</span><span class="sxs-lookup"><span data-stu-id="b5766-128">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="b5766-129">如果在没有符合条件的 `counter_name` 的情况下使用 `provider_name`，则会显示所有计数器。</span><span class="sxs-lookup"><span data-stu-id="b5766-129">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="b5766-130">若要发现提供程序和计数器名称，请使用 [dotnet-counters list](#dotnet-counters-list) 命令。</span><span class="sxs-lookup"><span data-stu-id="b5766-130">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

- **`--format <csv|json>`**

  <span data-ttu-id="b5766-131">要导出的格式。</span><span class="sxs-lookup"><span data-stu-id="b5766-131">TThe format to be exported.</span></span> <span data-ttu-id="b5766-132">当前可用的格式：csv 和 json。</span><span class="sxs-lookup"><span data-stu-id="b5766-132">Currently available: csv, json.</span></span>

- **`-o|--output <output>`**

  <span data-ttu-id="b5766-133">输出文件的名称。</span><span class="sxs-lookup"><span data-stu-id="b5766-133">The name of the output file.</span></span>

### <a name="examples"></a><span data-ttu-id="b5766-134">示例</span><span class="sxs-lookup"><span data-stu-id="b5766-134">Examples</span></span>

- <span data-ttu-id="b5766-135">以 3 秒的刷新间隔时间收集所有计数器的值，并生成 csv 输出文件：</span><span class="sxs-lookup"><span data-stu-id="b5766-135">Collect all counters at a refresh interval of 3 seconds and generate a csv as output:</span></span>

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

## <a name="dotnet-counters-list"></a><span data-ttu-id="b5766-136">dotnet-counters list</span><span class="sxs-lookup"><span data-stu-id="b5766-136">dotnet-counters list</span></span>

<span data-ttu-id="b5766-137">显示按提供程序分组的计数器名称和说明的列表。</span><span class="sxs-lookup"><span data-stu-id="b5766-137">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="b5766-138">摘要</span><span class="sxs-lookup"><span data-stu-id="b5766-138">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="b5766-139">示例</span><span class="sxs-lookup"><span data-stu-id="b5766-139">Example</span></span>

```console
> dotnet-counters list
Showing well-known counters only. Specific processes may support additional counters.

System.Runtime
    cpu-usage                                    Amount of time the process has utilized the CPU (ms)
    working-set                                  Amount of working set used by the process (MB)
    gc-heap-size                                 Total heap size reported by the GC (MB)
    gen-0-gc-count                               Number of Gen 0 GCs / min
    gen-1-gc-count                               Number of Gen 1 GCs / min
    gen-2-gc-count                               Number of Gen 2 GCs / min
    time-in-gc                                   % time in GC since the last GC
    gen-0-size                                   Gen 0 Heap Size
    gen-1-size                                   Gen 1 Heap Size
    gen-2-size                                   Gen 2 Heap Size
    loh-size                                     LOH Heap Size
    alloc-rate                                   Allocation Rate
    assembly-count                               Number of Assemblies Loaded
    exception-count                              Number of Exceptions / sec
    threadpool-thread-count                      Number of ThreadPool Threads
    monitor-lock-contention-count                Monitor Lock Contention Count
    threadpool-queue-length                      ThreadPool Work Items Queue Length
    threadpool-completed-items-count             ThreadPool Completed Work Items Count
    active-timer-count                           Active Timers Count

Microsoft.AspNetCore.Hosting
    requests-per-second                  Request rate
    total-requests                       Total number of requests
    current-requests                     Current number of requests
    failed-requests                      Failed number of requests
```

> [!NOTE]
> <span data-ttu-id="b5766-140">当有已标记的进程支持 `Microsoft.AspNetCore.Hosting` 计数器时（例如当 ASP.NET Core 应用程序在主机上运行时），将显示这些计数器。</span><span class="sxs-lookup"><span data-stu-id="b5766-140">The `Microsoft.AspNetCore.Hosting` counters are displayed when there are processes identified that support these counters, for example; when an ASP.NET Core application is running on the host machine.</span></span>

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="b5766-141">dotnet-counters monitor</span><span class="sxs-lookup"><span data-stu-id="b5766-141">dotnet-counters monitor</span></span>

<span data-ttu-id="b5766-142">显示所选计数器的定期刷新值。</span><span class="sxs-lookup"><span data-stu-id="b5766-142">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="b5766-143">摘要</span><span class="sxs-lookup"><span data-stu-id="b5766-143">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a><span data-ttu-id="b5766-144">选项</span><span class="sxs-lookup"><span data-stu-id="b5766-144">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="b5766-145">要监视的进程的 ID。</span><span class="sxs-lookup"><span data-stu-id="b5766-145">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="b5766-146">更新显示的计数器之间延迟的秒数</span><span class="sxs-lookup"><span data-stu-id="b5766-146">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="b5766-147">计数器的空格分隔列表。</span><span class="sxs-lookup"><span data-stu-id="b5766-147">A space separated list of counters.</span></span> <span data-ttu-id="b5766-148">计数器可以指定为 `provider_name[:counter_name]`。</span><span class="sxs-lookup"><span data-stu-id="b5766-148">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="b5766-149">如果在没有符合条件的 `counter_name` 的情况下使用 `provider_name`，则会显示所有计数器。</span><span class="sxs-lookup"><span data-stu-id="b5766-149">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="b5766-150">若要发现提供程序和计数器名称，请使用 [dotnet-counters list](#dotnet-counters-list) 命令。</span><span class="sxs-lookup"><span data-stu-id="b5766-150">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

### <a name="examples"></a><span data-ttu-id="b5766-151">示例</span><span class="sxs-lookup"><span data-stu-id="b5766-151">Examples</span></span>

- <span data-ttu-id="b5766-152">以 3 秒的刷新间隔监视 `System.Runtime` 中的所有计数器：</span><span class="sxs-lookup"><span data-stu-id="b5766-152">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902  --refresh-interval 3 System.Runtime

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      Working Set (MB)                            1982
      GC Heap Size (MB)                            811
      Gen 0 GC / second                             20
      Gen 1 GC / second                              4
      Gen 2 GC / second                              1
      Number of Exceptions / sec                     4
  ```

- <span data-ttu-id="b5766-153">仅监视 `System.Runtime` 中的 CPU 使用情况和 GC 堆大小：</span><span class="sxs-lookup"><span data-stu-id="b5766-153">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="b5766-154">监视用户定义的 `EventSource` 中的 `EventCounter` 值。</span><span class="sxs-lookup"><span data-stu-id="b5766-154">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="b5766-155">有关详细信息，请参阅[教程：使用 .NET Core 中的 EventCounters 衡量性能](event-counter-perf.md)。</span><span class="sxs-lookup"><span data-stu-id="b5766-155">For more information, see [Tutorial: Measure performance using EventCounters in .NET Core](event-counter-perf.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
  
## <a name="dotnet-counters-ps"></a><span data-ttu-id="b5766-156">dotnet-counters ps</span><span class="sxs-lookup"><span data-stu-id="b5766-156">dotnet-counters ps</span></span>

<span data-ttu-id="b5766-157">显示可监视的 dotnet 进程的列表。</span><span class="sxs-lookup"><span data-stu-id="b5766-157">Display a list of dotnet processes that can be monitored.</span></span>

### <a name="synopsis"></a><span data-ttu-id="b5766-158">摘要</span><span class="sxs-lookup"><span data-stu-id="b5766-158">Synopsis</span></span>

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a><span data-ttu-id="b5766-159">示例</span><span class="sxs-lookup"><span data-stu-id="b5766-159">Example</span></span>

```console
> dotnet-counters ps
  
  15683 WebApi     /home/suwhang/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```

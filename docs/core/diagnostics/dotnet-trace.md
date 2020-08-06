---
title: dotnet-trace 工具 - .NET Core
description: 安装和使用 dotnet-trace 命令行工具。
ms.date: 11/21/2019
ms.openlocfilehash: 25178a0e59ce9edb69d15ee761c1b9e56aa5eb3a
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517303"
---
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="85600-103">dotnet-trace 性能分析实用工具</span><span class="sxs-lookup"><span data-stu-id="85600-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="85600-104">本文适用于： ✔️ .NET Core 3.0 SDK 及更高版本</span><span class="sxs-lookup"><span data-stu-id="85600-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-trace"></a><span data-ttu-id="85600-105">安装 dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="85600-105">Install dotnet-trace</span></span>

<span data-ttu-id="85600-106">使用 [dotnet tool install](../tools/dotnet-tool-install.md) 命令安装 `dotnet-trace` [NuGet 包](https://www.nuget.org/packages/dotnet-trace)：</span><span class="sxs-lookup"><span data-stu-id="85600-106">Install `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace) with the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a><span data-ttu-id="85600-107">摘要</span><span class="sxs-lookup"><span data-stu-id="85600-107">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="85600-108">描述</span><span class="sxs-lookup"><span data-stu-id="85600-108">Description</span></span>

<span data-ttu-id="85600-109">`dotnet-trace` 工具：</span><span class="sxs-lookup"><span data-stu-id="85600-109">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="85600-110">是一个跨平台的 .NET Core 工具。</span><span class="sxs-lookup"><span data-stu-id="85600-110">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="85600-111">在不使用本机探查器的情况下启用正在运行的进程的 .NET Core 跟踪集合。</span><span class="sxs-lookup"><span data-stu-id="85600-111">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="85600-112">它是围绕 .NET Core 运行时的跨平台 `EventPipe` 技术而构建的。</span><span class="sxs-lookup"><span data-stu-id="85600-112">Is built around the cross-platform `EventPipe` technology of the .NET Core runtime.</span></span>
* <span data-ttu-id="85600-113">在 Windows、Linux 或 macOS 上提供相同体验。</span><span class="sxs-lookup"><span data-stu-id="85600-113">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="85600-114">选项</span><span class="sxs-lookup"><span data-stu-id="85600-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="85600-115">显示命令行帮助。</span><span class="sxs-lookup"><span data-stu-id="85600-115">Shows command-line help.</span></span>

- **`--version`**

  <span data-ttu-id="85600-116">显示 dotnet-dump 实用工具的版本。</span><span class="sxs-lookup"><span data-stu-id="85600-116">Displays the version of the dotnet-trace utility.</span></span>

## <a name="commands"></a><span data-ttu-id="85600-117">命令</span><span class="sxs-lookup"><span data-stu-id="85600-117">Commands</span></span>

| <span data-ttu-id="85600-118">命令</span><span class="sxs-lookup"><span data-stu-id="85600-118">Command</span></span>                                                   |
|-----------------------------------------------------------|
| [<span data-ttu-id="85600-119">dotnet-trace collect</span><span class="sxs-lookup"><span data-stu-id="85600-119">dotnet-trace collect</span></span>](#dotnet-trace-collect)             |
| [<span data-ttu-id="85600-120">dotnet-trace convert</span><span class="sxs-lookup"><span data-stu-id="85600-120">dotnet-trace convert</span></span>](#dotnet-trace-convert)             |
| [<span data-ttu-id="85600-121">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="85600-121">dotnet-trace ps</span></span>](#dotnet-trace-ps)                       |
| [<span data-ttu-id="85600-122">dotnet-trace list-profiles</span><span class="sxs-lookup"><span data-stu-id="85600-122">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles) |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="85600-123">dotnet-trace collect</span><span class="sxs-lookup"><span data-stu-id="85600-123">dotnet-trace collect</span></span>

<span data-ttu-id="85600-124">从正在运行的进程中收集诊断跟踪。</span><span class="sxs-lookup"><span data-stu-id="85600-124">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="85600-125">摘要</span><span class="sxs-lookup"><span data-stu-id="85600-125">Synopsis</span></span>

```console
dotnet-trace collect [--buffersize <size>] [--clreventlevel <clreventlevel>] [--clrevents <clrevents>]
    [--format <Chromium|NetTrace|Speedscope>] [-h|--help]
    [-n, --name <name>]  [-o|--output <trace-file-path>] [-p|--process-id <pid>]
    [--profile <profile-name>] [--providers <list-of-comma-separated-providers>]
```

### <a name="options"></a><span data-ttu-id="85600-126">选项</span><span class="sxs-lookup"><span data-stu-id="85600-126">Options</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="85600-127">设置内存中循环缓冲区的大小（以 MB 表示）。</span><span class="sxs-lookup"><span data-stu-id="85600-127">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="85600-128">默认值为 256 MB。</span><span class="sxs-lookup"><span data-stu-id="85600-128">Default 256 MB.</span></span>

- **`--clreventlevel <clreventlevel>`**

  <span data-ttu-id="85600-129">要发出的 CLR 事件的详细级别。</span><span class="sxs-lookup"><span data-stu-id="85600-129">Verbosity of CLR events to be emitted.</span></span>

- **`--clrevents <clrevents>`**

  <span data-ttu-id="85600-130">要发出的 CLR 运行时事件的列表。</span><span class="sxs-lookup"><span data-stu-id="85600-130">List of CLR runtime events to emit.</span></span>

- **`--format {Chromium|NetTrace|Speedscope}`**

  <span data-ttu-id="85600-131">设置跟踪文件转换的输出格式。</span><span class="sxs-lookup"><span data-stu-id="85600-131">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="85600-132">默认值为 `NetTrace`。</span><span class="sxs-lookup"><span data-stu-id="85600-132">The default is `NetTrace`.</span></span>

- **`-n, --name <name>`**

  <span data-ttu-id="85600-133">从中收集跟踪的进程的名称。</span><span class="sxs-lookup"><span data-stu-id="85600-133">The name of the process to collect the trace from.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="85600-134">收集的跟踪数据的输出路径。</span><span class="sxs-lookup"><span data-stu-id="85600-134">The output path for the collected trace data.</span></span> <span data-ttu-id="85600-135">如果未指定，则默认为 `trace.nettrace`。</span><span class="sxs-lookup"><span data-stu-id="85600-135">If not specified, it defaults to `trace.nettrace`.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="85600-136">从中收集跟踪的进程 ID。</span><span class="sxs-lookup"><span data-stu-id="85600-136">The process id to collect the trace from.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="85600-137">一组命名的预定义提供程序配置，允许简明地指定常见跟踪方案。</span><span class="sxs-lookup"><span data-stu-id="85600-137">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span>

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="85600-138">要启用的 `EventPipe` 提供程序的以逗号分隔的列表。</span><span class="sxs-lookup"><span data-stu-id="85600-138">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="85600-139">这些提供程序会补充 `--profile <profile-name>` 隐含的任何提供程序。</span><span class="sxs-lookup"><span data-stu-id="85600-139">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="85600-140">如果特定提供程序存在任何不一致的情况，此配置将优先于配置文件中的隐式配置。</span><span class="sxs-lookup"><span data-stu-id="85600-140">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="85600-141">此提供程序列表的格式为：</span><span class="sxs-lookup"><span data-stu-id="85600-141">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="85600-142">`Provider` 的格式为：`KnownProviderName[:Flags[:Level][:KeyValueArgs]]`。</span><span class="sxs-lookup"><span data-stu-id="85600-142">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="85600-143">`KeyValueArgs` 的格式为：`[key1=value1][;key2=value2]`。</span><span class="sxs-lookup"><span data-stu-id="85600-143">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="85600-144">dotnet-trace convert</span><span class="sxs-lookup"><span data-stu-id="85600-144">dotnet-trace convert</span></span>

<span data-ttu-id="85600-145">将 `nettrace` 跟踪转换为备用格式，以便用于备用跟踪分析工具。</span><span class="sxs-lookup"><span data-stu-id="85600-145">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="85600-146">摘要</span><span class="sxs-lookup"><span data-stu-id="85600-146">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [--format <Chromium|NetTrace|Speedscope>] [-h|--help] [-o|--output <output-filename>]
```

### <a name="arguments"></a><span data-ttu-id="85600-147">自变量</span><span class="sxs-lookup"><span data-stu-id="85600-147">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="85600-148">要转换的输入跟踪文件。</span><span class="sxs-lookup"><span data-stu-id="85600-148">Input trace file to be converted.</span></span> <span data-ttu-id="85600-149">默认为 trace.nettrace  。</span><span class="sxs-lookup"><span data-stu-id="85600-149">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="85600-150">选项</span><span class="sxs-lookup"><span data-stu-id="85600-150">Options</span></span>

- **`--format <Chromium|NetTrace|Speedscope>`**

  <span data-ttu-id="85600-151">设置跟踪文件转换的输出格式。</span><span class="sxs-lookup"><span data-stu-id="85600-151">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="85600-152">输出文件名。</span><span class="sxs-lookup"><span data-stu-id="85600-152">Output filename.</span></span> <span data-ttu-id="85600-153">将添加目标格式的扩展。</span><span class="sxs-lookup"><span data-stu-id="85600-153">Extension of target format will be added.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="85600-154">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="85600-154">dotnet-trace ps</span></span>

 <span data-ttu-id="85600-155">列出可从中收集跟踪的 dotnet 进程。</span><span class="sxs-lookup"><span data-stu-id="85600-155">Lists the dotnet processes that traces can be collected from.</span></span>

### <a name="synopsis"></a><span data-ttu-id="85600-156">摘要</span><span class="sxs-lookup"><span data-stu-id="85600-156">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="85600-157">dotnet-trace list-profiles</span><span class="sxs-lookup"><span data-stu-id="85600-157">dotnet-trace list-profiles</span></span>

<span data-ttu-id="85600-158">列出预生成的跟踪配置文件，并描述每个配置文件中包含的提供程序和筛选器。</span><span class="sxs-lookup"><span data-stu-id="85600-158">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="85600-159">摘要</span><span class="sxs-lookup"><span data-stu-id="85600-159">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="85600-160">使用 dotnet-trace 收集跟踪</span><span class="sxs-lookup"><span data-stu-id="85600-160">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="85600-161">若要使用 `dotnet-trace` 收集跟踪，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="85600-161">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="85600-162">需要首先查找要从中收集跟踪的 .NET Core 应用程序的进程标识符 (PID)。</span><span class="sxs-lookup"><span data-stu-id="85600-162">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="85600-163">例如，在 Windows 上，可以使用任务管理器或 `tasklist` 命令。</span><span class="sxs-lookup"><span data-stu-id="85600-163">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="85600-164">在 Linux 上，使用 `ps` 命令。</span><span class="sxs-lookup"><span data-stu-id="85600-164">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="85600-165">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="85600-165">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="85600-166">运行下面的命令：</span><span class="sxs-lookup"><span data-stu-id="85600-166">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="85600-167">前面的命令生成类似于以下内容的输出：</span><span class="sxs-lookup"><span data-stu-id="85600-167">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="85600-168">按 `<Enter>` 键停止收集。</span><span class="sxs-lookup"><span data-stu-id="85600-168">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="85600-169">`dotnet-trace` 会将完成将事件记录到 trace.nettrace 文件中  。</span><span class="sxs-lookup"><span data-stu-id="85600-169">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="85600-170">查看由 dotnet-trace 捕获的跟踪</span><span class="sxs-lookup"><span data-stu-id="85600-170">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="85600-171">在 Windows 上，可以使用 [PerfView](https://github.com/microsoft/perfview) 查看 .nettrace 文件以进行分析  ：对于其他平台上收集的跟踪，可以将跟踪文件移动到 Windows 计算机上，以在 PerfView 上进行查看。</span><span class="sxs-lookup"><span data-stu-id="85600-171">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="85600-172">在 Linux 上，可以通过将 `dotnet-trace` 的输出格式更改为 `speedscope` 来查看跟踪。</span><span class="sxs-lookup"><span data-stu-id="85600-172">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="85600-173">可以使用 `-f|--format` 选项更改输出文件格式 - `-f speedscope` 会使 `dotnet-trace` 生成 `speedscope` 文件。</span><span class="sxs-lookup"><span data-stu-id="85600-173">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="85600-174">可以在 `nettrace`（默认选项）和 `speedscope` 之间进行选择。</span><span class="sxs-lookup"><span data-stu-id="85600-174">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="85600-175">可以在 <https://www.speedscope.app> 打开 `Speedscope` 文件。</span><span class="sxs-lookup"><span data-stu-id="85600-175">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="85600-176">.NET Core 运行时以 `nettrace` 格式生成跟踪。</span><span class="sxs-lookup"><span data-stu-id="85600-176">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="85600-177">跟踪完成后，跟踪将转换为 speedscope（如果指定）。</span><span class="sxs-lookup"><span data-stu-id="85600-177">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="85600-178">由于某些转换可能会导致数据丢失，因此，原始 `nettrace` 文件将保留在转换后的文件旁边。</span><span class="sxs-lookup"><span data-stu-id="85600-178">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="85600-179">使用 dotnet-trace 收集随时间变化的计数器值</span><span class="sxs-lookup"><span data-stu-id="85600-179">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="85600-180">`dotnet-trace` 可以：</span><span class="sxs-lookup"><span data-stu-id="85600-180">`dotnet-trace` can:</span></span>

* <span data-ttu-id="85600-181">在性能敏感的环境中使用 `EventCounter` 进行基本运行状况监视。</span><span class="sxs-lookup"><span data-stu-id="85600-181">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="85600-182">例如，在生产环境中。</span><span class="sxs-lookup"><span data-stu-id="85600-182">For example, in production.</span></span>
* <span data-ttu-id="85600-183">收集跟踪，这样就不需要实时查看。</span><span class="sxs-lookup"><span data-stu-id="85600-183">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="85600-184">例如，若要收集运行时性能计数器值，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="85600-184">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="85600-185">上述命令通知运行时计数器每秒报告一次，以便进行轻量型运行状况监视。</span><span class="sxs-lookup"><span data-stu-id="85600-185">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="85600-186">通过使用较大的值（例如 60）替换 `EventCounterIntervalSec=1`，可以收集计数器数据中粒度较小的跟踪。</span><span class="sxs-lookup"><span data-stu-id="85600-186">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="85600-187">以下命令比以上命令产生更小的开销和跟踪大小：</span><span class="sxs-lookup"><span data-stu-id="85600-187">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="85600-188">以上命令会禁用运行时事件和托管堆栈探查器。</span><span class="sxs-lookup"><span data-stu-id="85600-188">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="net-providers"></a><span data-ttu-id="85600-189">.NET 提供程序</span><span class="sxs-lookup"><span data-stu-id="85600-189">.NET Providers</span></span>

<span data-ttu-id="85600-190">.NET Core 运行时支持以下 .NET 提供程序：</span><span class="sxs-lookup"><span data-stu-id="85600-190">The .NET Core runtime supports the following .NET providers.</span></span> <span data-ttu-id="85600-191">.NET Core 使用相同的关键字来启用 `Event Tracing for Windows (ETW)` 和 `EventPipe` 跟踪。</span><span class="sxs-lookup"><span data-stu-id="85600-191">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span></span>

| <span data-ttu-id="85600-192">提供程序名称</span><span class="sxs-lookup"><span data-stu-id="85600-192">Provider name</span></span>                            | <span data-ttu-id="85600-193">信息</span><span class="sxs-lookup"><span data-stu-id="85600-193">Information</span></span> |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [<span data-ttu-id="85600-194">运行时提供程序</span><span class="sxs-lookup"><span data-stu-id="85600-194">The Runtime Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[<span data-ttu-id="85600-195">CLR 运行时关键字</span><span class="sxs-lookup"><span data-stu-id="85600-195">CLR Runtime Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [<span data-ttu-id="85600-196">断开提供程序</span><span class="sxs-lookup"><span data-stu-id="85600-196">The Rundown Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[<span data-ttu-id="85600-197">CLR 断开关键字</span><span class="sxs-lookup"><span data-stu-id="85600-197">CLR Rundown Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | <span data-ttu-id="85600-198">启用示例探查器。</span><span class="sxs-lookup"><span data-stu-id="85600-198">Enables the sample profiler.</span></span> |

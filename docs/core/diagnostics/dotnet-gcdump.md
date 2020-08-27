---
title: dotnet-gcdump - .NET Core
description: 安装和使用 dotnet-gcdump 命令行工具。
ms.date: 07/26/2020
ms.openlocfilehash: a7b19f4d7487677b975621e7267a17894dae2e3a
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656646"
---
# <a name="heap-analysis-tool-dotnet-gcdump"></a><span data-ttu-id="55ccd-103">堆分析工具 (dotnet-gcdump)</span><span class="sxs-lookup"><span data-stu-id="55ccd-103">Heap analysis tool (dotnet-gcdump)</span></span>

<span data-ttu-id="55ccd-104">**本文适用于：** ✔️ .NET Core 3.1 SDK 及更高版本</span><span class="sxs-lookup"><span data-stu-id="55ccd-104">**This article applies to:** ✔️ .NET Core 3.1 SDK and later versions</span></span>

## <a name="install-dotnet-gcdump"></a><span data-ttu-id="55ccd-105">安装 dotnet-gcdump</span><span class="sxs-lookup"><span data-stu-id="55ccd-105">Install dotnet-gcdump</span></span>

<span data-ttu-id="55ccd-106">若要安装最新版 `dotnet-gcdump` [NuGet 包](https://www.nuget.org/packages/dotnet-gcdump)，请使用 [dotnet tool install](../tools/dotnet-tool-install.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="55ccd-106">To install the latest release version of the `dotnet-gcdump` [NuGet package](https://www.nuget.org/packages/dotnet-gcdump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install -g dotnet-gcdump
```

## <a name="synopsis"></a><span data-ttu-id="55ccd-107">摘要</span><span class="sxs-lookup"><span data-stu-id="55ccd-107">Synopsis</span></span>

```console
dotnet-gcdump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="55ccd-108">描述</span><span class="sxs-lookup"><span data-stu-id="55ccd-108">Description</span></span>

<span data-ttu-id="55ccd-109">`dotnet-gcdump` 全局工具可用于为活动 .NET 进程收集 GC（垃圾回收器）转储。</span><span class="sxs-lookup"><span data-stu-id="55ccd-109">The `dotnet-gcdump` global tool is a way to collect GC (Garbage Collector) dumps of live .NET processes.</span></span> <span data-ttu-id="55ccd-110">它使用 EventPipe 技术，这是 Windows 上 ETW 的一个跨平台替代方法。</span><span class="sxs-lookup"><span data-stu-id="55ccd-110">It uses the EventPipe technology, which is a cross-platform alternative to ETW on Windows.</span></span> <span data-ttu-id="55ccd-111">创建 GC 转储时需要在目标进程中触发 GC、开启特殊事件并从事件流中重新生成对象根图。</span><span class="sxs-lookup"><span data-stu-id="55ccd-111">GC dumps are created by triggering a GC in the target process, turning on special events, and regenerating the graph of object roots from the event stream.</span></span> <span data-ttu-id="55ccd-112">此过程允许在进程运行时以最小的开销收集 GC 转储。</span><span class="sxs-lookup"><span data-stu-id="55ccd-112">This process allows for GC dumps to be collected while the process is running and with minimal overhead.</span></span> <span data-ttu-id="55ccd-113">这些转储对于以下几种情况非常有用：</span><span class="sxs-lookup"><span data-stu-id="55ccd-113">These dumps are useful for several scenarios:</span></span>

- <span data-ttu-id="55ccd-114">比较多个时间点堆上的对象数。</span><span class="sxs-lookup"><span data-stu-id="55ccd-114">Comparing the number of objects on the heap at several points in time.</span></span>
- <span data-ttu-id="55ccd-115">分析对象的根（回答诸如“还有哪些引用此类型的内容？”等问题）。</span><span class="sxs-lookup"><span data-stu-id="55ccd-115">Analyzing roots of objects (answering questions like, "what still has a reference to this type?").</span></span>
- <span data-ttu-id="55ccd-116">收集有关堆上的对象计数的常规统计信息。</span><span class="sxs-lookup"><span data-stu-id="55ccd-116">Collecting general statistics about the counts of objects on the heap.</span></span>

### <a name="view-the-gc-dump-captured-from-dotnet-gcdump"></a><span data-ttu-id="55ccd-117">查看从 dotnet-gcdump 捕获的 GC 转储</span><span class="sxs-lookup"><span data-stu-id="55ccd-117">View the GC dump captured from dotnet-gcdump</span></span>

<span data-ttu-id="55ccd-118">在 Windows 上，可以在 [PerfView](https://github.com/microsoft/perfview) 中查看 `.gcdump` 文件，以便进行分析，也可在 Visual Studio 中查看该文件。</span><span class="sxs-lookup"><span data-stu-id="55ccd-118">On Windows, `.gcdump` files can be viewed in [PerfView](https://github.com/microsoft/perfview) for analysis or in Visual Studio.</span></span> <span data-ttu-id="55ccd-119">目前，无法在非 Windows 平台上打开 `.gcdump`。</span><span class="sxs-lookup"><span data-stu-id="55ccd-119">Currently, There is no way of opening a `.gcdump` on non-Windows platforms.</span></span>

<span data-ttu-id="55ccd-120">可以收集多个 `.gcdump`，并在 Visual Studio 中同时打开它们以获取比较体验。</span><span class="sxs-lookup"><span data-stu-id="55ccd-120">You can collect multiple `.gcdump`s and open them simultaneously in Visual Studio to get a comparison experience.</span></span>

## <a name="options"></a><span data-ttu-id="55ccd-121">选项</span><span class="sxs-lookup"><span data-stu-id="55ccd-121">Options</span></span>

- **`--version`**

  <span data-ttu-id="55ccd-122">显示 `dotnet-gcdump` 实用工具的版本。</span><span class="sxs-lookup"><span data-stu-id="55ccd-122">Displays the version of the `dotnet-gcdump` utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="55ccd-123">显示命令行帮助。</span><span class="sxs-lookup"><span data-stu-id="55ccd-123">Shows command-line help.</span></span>

## `dotnet-gcdump collect`

<span data-ttu-id="55ccd-124">从当前正在运行的进程中收集 GC 转储。</span><span class="sxs-lookup"><span data-stu-id="55ccd-124">Collects a GC dump from a currently running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="55ccd-125">摘要</span><span class="sxs-lookup"><span data-stu-id="55ccd-125">Synopsis</span></span>

```console
dotnet-gcdump collect [-h|--help] [-p|--process-id <pid>] [-o|--output <gcdump-file-path>] [-v|--verbose] [-t|--timeout <timeout>] [-n|--name <name>]
```

### <a name="options"></a><span data-ttu-id="55ccd-126">选项</span><span class="sxs-lookup"><span data-stu-id="55ccd-126">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="55ccd-127">显示命令行帮助。</span><span class="sxs-lookup"><span data-stu-id="55ccd-127">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="55ccd-128">可从中收集 GC 转储的进程 ID。</span><span class="sxs-lookup"><span data-stu-id="55ccd-128">The process ID to collect the GC dump from.</span></span>

- **`-o|--output <gcdump-file-path>`**

  <span data-ttu-id="55ccd-129">应写入收集 GC 转储的路径。</span><span class="sxs-lookup"><span data-stu-id="55ccd-129">The path where collected GC dumps should be written.</span></span> <span data-ttu-id="55ccd-130">默认为 .\\YYYYMMDD\_HHMMSS\_\<pid>.gcdump。</span><span class="sxs-lookup"><span data-stu-id="55ccd-130">Defaults to *.\\YYYYMMDD\_HHMMSS\_\<pid>.gcdump*.</span></span>

- **`-v|--verbose`**

  <span data-ttu-id="55ccd-131">收集 GC 转储时输出日志。</span><span class="sxs-lookup"><span data-stu-id="55ccd-131">Output the log while collecting the GC dump.</span></span>

- **`-t|--timeout <timeout>`**

  <span data-ttu-id="55ccd-132">如果收集 GC 转储的时间超过了此秒数，则放弃收集。</span><span class="sxs-lookup"><span data-stu-id="55ccd-132">Give up on collecting the GC dump if it takes longer than this many seconds.</span></span> <span data-ttu-id="55ccd-133">默认值为 30。</span><span class="sxs-lookup"><span data-stu-id="55ccd-133">The default value is 30.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="55ccd-134">可从中收集 GC 转储的进程的名称。</span><span class="sxs-lookup"><span data-stu-id="55ccd-134">The name of the process to collect the GC dump from.</span></span>

## `dotnet-gcdump ps`

<span data-ttu-id="55ccd-135">列出可为其收集 GC 转储的 dotnet 进程。</span><span class="sxs-lookup"><span data-stu-id="55ccd-135">Lists the dotnet processes that GC dumps can be collected for.</span></span>

### <a name="synopsis"></a><span data-ttu-id="55ccd-136">摘要</span><span class="sxs-lookup"><span data-stu-id="55ccd-136">Synopsis</span></span>

```console
dotnet-gcdump ps
```

## `dotnet-gcdump report <gcdump_filename>`

<span data-ttu-id="55ccd-137">从以前生成的 GC 转储或从正在运行的进程生成报表，并将其写入 `stdout`。</span><span class="sxs-lookup"><span data-stu-id="55ccd-137">Generate a report from a previously generated GC dump or from a running process, and write to `stdout`.</span></span>

### <a name="synopsis"></a><span data-ttu-id="55ccd-138">摘要</span><span class="sxs-lookup"><span data-stu-id="55ccd-138">Synopsis</span></span>

```console
dotnet-gcdump report [-h|--help] [-p|--process-id <pid>] [-t|--report-type <HeapStat>]
```

### <a name="options"></a><span data-ttu-id="55ccd-139">选项</span><span class="sxs-lookup"><span data-stu-id="55ccd-139">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="55ccd-140">显示命令行帮助。</span><span class="sxs-lookup"><span data-stu-id="55ccd-140">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="55ccd-141">可从中收集 GC 转储的进程 ID。</span><span class="sxs-lookup"><span data-stu-id="55ccd-141">The process ID to collect the GC dump from.</span></span>

- **`-t|--report-type <HeapStat>`**

  <span data-ttu-id="55ccd-142">可生成报表的类型。</span><span class="sxs-lookup"><span data-stu-id="55ccd-142">The type of report to generate.</span></span> <span data-ttu-id="55ccd-143">可用选项：heapstat（默认）。</span><span class="sxs-lookup"><span data-stu-id="55ccd-143">Available options: heapstat (default).</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="55ccd-144">疑难解答</span><span class="sxs-lookup"><span data-stu-id="55ccd-144">Troubleshoot</span></span>

- <span data-ttu-id="55ccd-145">gcdump 中没有类型信息。</span><span class="sxs-lookup"><span data-stu-id="55ccd-145">There is no type information in the gcdump.</span></span>

   <span data-ttu-id="55ccd-146">在 .NET Core 3.1 之前，存在一个问题，即使用 EventPipe 调用 gcdump 时，gcdump 之间的类型缓存没有清除。</span><span class="sxs-lookup"><span data-stu-id="55ccd-146">Prior to .NET Core 3.1, there was an issue where a type cache was not cleared between gcdumps when they were invoked with EventPipe.</span></span> <span data-ttu-id="55ccd-147">这导致确定类型信息所需的事件未发送给第二个和后续 gcdump。</span><span class="sxs-lookup"><span data-stu-id="55ccd-147">This resulted in the events needed for determining type information not being sent for the second and subsequent gcdumps.</span></span> <span data-ttu-id="55ccd-148">此问题已在 .NET Core 3.1-preview2 中得以修复。</span><span class="sxs-lookup"><span data-stu-id="55ccd-148">This was fixed in .NET Core 3.1-preview2.</span></span>

- <span data-ttu-id="55ccd-149">COM 和静态类型不在 GC 转储中。</span><span class="sxs-lookup"><span data-stu-id="55ccd-149">COM and static types aren't in the GC dump.</span></span>

   <span data-ttu-id="55ccd-150">在 .NET Core 3.1-preview2 之前，存在一个问题，即通过 EventPipe 调用 GC 转储时，不会发送静态和 COM 类型。</span><span class="sxs-lookup"><span data-stu-id="55ccd-150">Prior to .NET Core 3.1-preview2, there was an issue where static and COM types weren't sent when the GC dump was invoked via EventPipe.</span></span> <span data-ttu-id="55ccd-151">此问题已在 .NET Core 3.1-preview2 中得以修复。</span><span class="sxs-lookup"><span data-stu-id="55ccd-151">This has been fixed in .NET Core 3.1-preview2.</span></span>

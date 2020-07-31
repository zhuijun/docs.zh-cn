---
title: 调试内存泄漏教程
description: 了解如何调试 .NET Core 中的内存泄漏。
ms.topic: tutorial
ms.date: 04/20/2020
ms.openlocfilehash: ff684f9b9402cb8b7b648e792a1d37ddcc96b399
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924885"
---
# <a name="debug-a-memory-leak-in-net-core"></a><span data-ttu-id="8e07d-103">调试 .NET Core 中的内存泄漏</span><span class="sxs-lookup"><span data-stu-id="8e07d-103">Debug a memory leak in .NET Core</span></span>

<span data-ttu-id="8e07d-104">**本文适用于：** ✔️ .NET Core 3.1 SDK 及更高版本</span><span class="sxs-lookup"><span data-stu-id="8e07d-104">**This article applies to:** ✔️ .NET Core 3.1 SDK and later versions</span></span>

<span data-ttu-id="8e07d-105">本教程演示用于分析 .NET Core 内存泄漏的工具。</span><span class="sxs-lookup"><span data-stu-id="8e07d-105">This tutorial demonstrates the tools to analyze a .NET Core memory leak.</span></span>

<span data-ttu-id="8e07d-106">本教程使用一个示例应用程序，它设计为有意泄漏内存。</span><span class="sxs-lookup"><span data-stu-id="8e07d-106">This tutorial uses a sample app, which is designed to intentionally leak memory.</span></span> <span data-ttu-id="8e07d-107">本示例作为练习提供。</span><span class="sxs-lookup"><span data-stu-id="8e07d-107">The sample is provided as an exercise.</span></span> <span data-ttu-id="8e07d-108">还可以分析无意中泄漏内存的应用程序。</span><span class="sxs-lookup"><span data-stu-id="8e07d-108">You can analyze an app that is unintentionally leaking memory too.</span></span>

<span data-ttu-id="8e07d-109">在本教程中，你将：</span><span class="sxs-lookup"><span data-stu-id="8e07d-109">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="8e07d-110">使用 [dotnet-counters](dotnet-counters.md) 检查托管内存的使用情况。</span><span class="sxs-lookup"><span data-stu-id="8e07d-110">Examine managed memory usage with [dotnet-counters](dotnet-counters.md).</span></span>
> - <span data-ttu-id="8e07d-111">生成转储文件。</span><span class="sxs-lookup"><span data-stu-id="8e07d-111">Generate a dump file.</span></span>
> - <span data-ttu-id="8e07d-112">使用转储文件分析内存使用情况。</span><span class="sxs-lookup"><span data-stu-id="8e07d-112">Analyze the memory usage using the dump file.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8e07d-113">先决条件</span><span class="sxs-lookup"><span data-stu-id="8e07d-113">Prerequisites</span></span>

<span data-ttu-id="8e07d-114">本教程使用：</span><span class="sxs-lookup"><span data-stu-id="8e07d-114">The tutorial uses:</span></span>

- <span data-ttu-id="8e07d-115">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="8e07d-115">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="8e07d-116">[dotnet-trace](dotnet-trace.md) 列出进程。</span><span class="sxs-lookup"><span data-stu-id="8e07d-116">[dotnet-trace](dotnet-trace.md) to list processes.</span></span>
- <span data-ttu-id="8e07d-117">[dotnet-counters](dotnet-counters.md) 检查托管内存的使用情况。</span><span class="sxs-lookup"><span data-stu-id="8e07d-117">[dotnet-counters](dotnet-counters.md) to check managed memory usage.</span></span>
- <span data-ttu-id="8e07d-118">[dotnet-dump](dotnet-dump.md) 收集和分析转储文件。</span><span class="sxs-lookup"><span data-stu-id="8e07d-118">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file.</span></span>
- <span data-ttu-id="8e07d-119">要诊断的[示例调试目标](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/)应用。</span><span class="sxs-lookup"><span data-stu-id="8e07d-119">A [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) app to diagnose.</span></span>

<span data-ttu-id="8e07d-120">本教程假设已安装示例和工具并可供使用。</span><span class="sxs-lookup"><span data-stu-id="8e07d-120">The tutorial assumes the sample and tools are installed and ready to use.</span></span>

## <a name="examine-managed-memory-usage"></a><span data-ttu-id="8e07d-121">检查托管内存的使用情况</span><span class="sxs-lookup"><span data-stu-id="8e07d-121">Examine managed memory usage</span></span>

<span data-ttu-id="8e07d-122">在开始收集诊断数据以帮助分析本案例的根本原因时，需要确保实际看到的是内存泄漏（内存增加）。</span><span class="sxs-lookup"><span data-stu-id="8e07d-122">Before you start collecting diagnostics data to help us root cause this scenario, you need to make sure you're actually seeing a memory leak (memory growth).</span></span> <span data-ttu-id="8e07d-123">可以使用 [dotnet-counters](dotnet-counters.md) 工具进行确认。</span><span class="sxs-lookup"><span data-stu-id="8e07d-123">You can use the [dotnet-counters](dotnet-counters.md) tool to confirm that.</span></span>

<span data-ttu-id="8e07d-124">打开控制台窗口并导航到下载并解压缩[示例调试目标](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/)的目录。</span><span class="sxs-lookup"><span data-stu-id="8e07d-124">Open a console window and navigate to the directory where you downloaded and unzipped the [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/).</span></span> <span data-ttu-id="8e07d-125">运行目标：</span><span class="sxs-lookup"><span data-stu-id="8e07d-125">Run the target:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="8e07d-126">在单独的控制台中，使用 [dotnet-trace](dotnet-trace.md) 工具查找进程 ID：</span><span class="sxs-lookup"><span data-stu-id="8e07d-126">From a separate console, find the process ID using the [dotnet-trace](dotnet-trace.md) tool:</span></span>

```console
dotnet-trace ps
```

<span data-ttu-id="8e07d-127">输出应如下所示：</span><span class="sxs-lookup"><span data-stu-id="8e07d-127">The output should be similar to:</span></span>

```console
4807 DiagnosticScena /home/user/git/samples/core/diagnostics/DiagnosticScenarios/bin/Debug/netcoreapp3.0/DiagnosticScenarios
```

<span data-ttu-id="8e07d-128">现使用 [dotnet-counters](dotnet-counters.md) 工具检查托管内存的使用情况。</span><span class="sxs-lookup"><span data-stu-id="8e07d-128">Now, check managed memory usage with the [dotnet-counters](dotnet-counters.md) tool.</span></span> <span data-ttu-id="8e07d-129">`--refresh-interval` 指定两次刷新之间的秒数：</span><span class="sxs-lookup"><span data-stu-id="8e07d-129">The `--refresh-interval` specifies the number of seconds between refreshes:</span></span>

```console
dotnet-counters monitor --refresh-interval 1 -p 4807
```

<span data-ttu-id="8e07d-130">实时输出应如下所示：</span><span class="sxs-lookup"><span data-stu-id="8e07d-130">The live output should be similar to:</span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    # of Assemblies Loaded                           118
    % Time in GC (since last GC)                       0
    Allocation Rate (Bytes / sec)                 37,896
    CPU Usage (%)                                      0
    Exceptions / sec                                   0
    GC Heap Size (MB)                                  4
    Gen 0 GC / sec                                     0
    Gen 0 Size (B)                                     0
    Gen 1 GC / sec                                     0
    Gen 1 Size (B)                                     0
    Gen 2 GC / sec                                     0
    Gen 2 Size (B)                                     0
    LOH Size (B)                                       0
    Monitor Lock Contention Count / sec                0
    Number of Active Timers                            1
    ThreadPool Completed Work Items / sec             10
    ThreadPool Queue Length                            0
    ThreadPool Threads Count                           1
    Working Set (MB)                                  83
```

<span data-ttu-id="8e07d-131">重点介绍此行：</span><span class="sxs-lookup"><span data-stu-id="8e07d-131">Focusing on this line:</span></span>

```console
    GC Heap Size (MB)                                  4
```

<span data-ttu-id="8e07d-132">启动后，可以看到托管堆内存为 4 MB。</span><span class="sxs-lookup"><span data-stu-id="8e07d-132">You can see that the managed heap memory is 4 MB right after startup.</span></span>

<span data-ttu-id="8e07d-133">现在，点击 URL `https://localhost:5001/api/diagscenario/memleak/20000`。</span><span class="sxs-lookup"><span data-stu-id="8e07d-133">Now, hit the URL `https://localhost:5001/api/diagscenario/memleak/20000`.</span></span>

<span data-ttu-id="8e07d-134">请注意，内存使用量已增加到 30 MB。</span><span class="sxs-lookup"><span data-stu-id="8e07d-134">Observe that the memory usage has grown to 30 MB.</span></span>

```console
    GC Heap Size (MB)                                 30
```

<span data-ttu-id="8e07d-135">通过监视内存使用情况，可以确定内存正在增长或泄漏。</span><span class="sxs-lookup"><span data-stu-id="8e07d-135">By watching the memory usage, you can safely say that memory is growing or leaking.</span></span> <span data-ttu-id="8e07d-136">下一步是收集内存分析的适当数据。</span><span class="sxs-lookup"><span data-stu-id="8e07d-136">The next step is to collect the right data for memory analysis.</span></span>

### <a name="generate-memory-dump"></a><span data-ttu-id="8e07d-137">生成内存转储</span><span class="sxs-lookup"><span data-stu-id="8e07d-137">Generate memory dump</span></span>

<span data-ttu-id="8e07d-138">分析可能的内存泄漏时，需要访问应用的内存堆。</span><span class="sxs-lookup"><span data-stu-id="8e07d-138">When analyzing possible memory leaks, you need access to the app's memory heap.</span></span> <span data-ttu-id="8e07d-139">然后可以分析内存内容。</span><span class="sxs-lookup"><span data-stu-id="8e07d-139">Then you can analyze the memory contents.</span></span> <span data-ttu-id="8e07d-140">查看对象之间的关系，可以创建理论说明内存未释放的原因。</span><span class="sxs-lookup"><span data-stu-id="8e07d-140">Looking at relationships between objects, you create theories on why memory isn't being freed.</span></span> <span data-ttu-id="8e07d-141">常见的诊断数据源是 Windows 上的内存转储或 Linux 上的等效核心转储。</span><span class="sxs-lookup"><span data-stu-id="8e07d-141">A common diagnostics data source is a memory dump on Windows or the equivalent core dump on Linux.</span></span> <span data-ttu-id="8e07d-142">若要生成 .NET Core 应用程序转储，可以使用 [dotnet-dump)](dotnet-dump.md) 工具。</span><span class="sxs-lookup"><span data-stu-id="8e07d-142">To generate a dump of a .NET Core application, you can use the [dotnet-dump)](dotnet-dump.md) tool.</span></span>

<span data-ttu-id="8e07d-143">使用之前启动的[示例调试目标](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/)，运行以下命令以生成 Linux 核心转储：</span><span class="sxs-lookup"><span data-stu-id="8e07d-143">Using the [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) previously started, run the following command to generate a Linux core dump:</span></span>

```dotnetcli
dotnet-dump collect -p 4807
```

<span data-ttu-id="8e07d-144">结果是位于同一文件夹中的核心转储。</span><span class="sxs-lookup"><span data-stu-id="8e07d-144">The result is a core dump located in the same folder.</span></span>

```console
Writing minidump with heap to ./core_20190430_185145
Complete
```

### <a name="restart-the-failed-process"></a><span data-ttu-id="8e07d-145">重新启动失败的进程</span><span class="sxs-lookup"><span data-stu-id="8e07d-145">Restart the failed process</span></span>

<span data-ttu-id="8e07d-146">收集转储后，你应该有足够的信息来诊断失败的进程。</span><span class="sxs-lookup"><span data-stu-id="8e07d-146">Once the dump is collected, you should have sufficient information to diagnose the failed process.</span></span> <span data-ttu-id="8e07d-147">如果失败的进程在生产服务器上运行，现在是通过重新启动进程进行短期修正的理想时机。</span><span class="sxs-lookup"><span data-stu-id="8e07d-147">If the failed process is running on a production server, now it's the ideal time for short-term remediation by restarting the process.</span></span>

<span data-ttu-id="8e07d-148">在本教程中，你已经完成了[示例调试目标](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/)，现在可以将其关闭。</span><span class="sxs-lookup"><span data-stu-id="8e07d-148">In this tutorial, you're now done with the [Sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) and you can close it.</span></span> <span data-ttu-id="8e07d-149">导航到启动服务器的终端并按 <kbd>Ctrl+C</kbd>。</span><span class="sxs-lookup"><span data-stu-id="8e07d-149">Navigate to the terminal that started the server, and press <kbd>Ctrl+C</kbd>.</span></span>

### <a name="analyze-the-core-dump"></a><span data-ttu-id="8e07d-150">分析核心转储</span><span class="sxs-lookup"><span data-stu-id="8e07d-150">Analyze the core dump</span></span>

<span data-ttu-id="8e07d-151">生成核心转储后，请使用 [dotnet-dump](dotnet-dump.md) 工具分析转储：</span><span class="sxs-lookup"><span data-stu-id="8e07d-151">Now that you have a core dump generated, use the [dotnet-dump](dotnet-dump.md) tool to analyze the dump:</span></span>

```dotnetcli
dotnet-dump analyze core_20190430_185145
```

<span data-ttu-id="8e07d-152">其中 `core_20190430_185145` 是要分析的核心转储的名称。</span><span class="sxs-lookup"><span data-stu-id="8e07d-152">Where `core_20190430_185145` is the name of the core dump you want to analyze.</span></span>

> [!NOTE]
> <span data-ttu-id="8e07d-153">如果你看到报错“找不到 libdl.so  ”，则可能需要安装 libc6-dev  包。</span><span class="sxs-lookup"><span data-stu-id="8e07d-153">If you see an error complaining that *libdl.so* cannot be found, you may have to install the *libc6-dev* package.</span></span> <span data-ttu-id="8e07d-154">有关详细信息，请参阅 [Linux 上 .NET Core 的先决条件](../install/dependencies.md?pivots=os-linux)。</span><span class="sxs-lookup"><span data-stu-id="8e07d-154">For more information, see [Prerequisites for .NET Core on Linux](../install/dependencies.md?pivots=os-linux).</span></span>

<span data-ttu-id="8e07d-155">此时会显示一个提示，可在其中输入 SOS 命令。</span><span class="sxs-lookup"><span data-stu-id="8e07d-155">You'll be presented with a prompt where you can enter SOS commands.</span></span> <span data-ttu-id="8e07d-156">通常，首先要查看的是托管堆的整体状态：</span><span class="sxs-lookup"><span data-stu-id="8e07d-156">Commonly, the first thing you want to look at is the overall state of the managed heap:</span></span>

```console
> dumpheap -stat

Statistics:
              MT    Count    TotalSize Class Name
...
00007f6c1eeefba8      576        59904 System.Reflection.RuntimeMethodInfo
00007f6c1dc021c8     1749        95696 System.SByte[]
00000000008c9db0     3847       116080      Free
00007f6c1e784a18      175       128640 System.Char[]
00007f6c1dbf5510      217       133504 System.Object[]
00007f6c1dc014c0      467       416464 System.Byte[]
00007f6c21625038        6      4063376 testwebapi.Controllers.Customer[]
00007f6c20a67498   200000      4800000 testwebapi.Controllers.Customer
00007f6c1dc00f90   206770     19494060 System.String
Total 428516 objects
```

<span data-ttu-id="8e07d-157">可在此处看到大多数对象是 `String` 或 `Customer` 对象。</span><span class="sxs-lookup"><span data-stu-id="8e07d-157">Here you can see that most objects are either `String` or `Customer` objects.</span></span>

<span data-ttu-id="8e07d-158">可以使用方法表 (MT) 再次使用 `dumpheap` 命令来获取所有 `String` 实例的列表：</span><span class="sxs-lookup"><span data-stu-id="8e07d-158">You can use the `dumpheap` command again with the method table (MT) to get a list of all the `String` instances:</span></span>

```console
> dumpheap -mt 00007faddaa50f90

         Address               MT     Size
...
00007f6ad09421f8 00007faddaa50f90       94
...
00007f6ad0965b20 00007f6c1dc00f90       80
00007f6ad0965c10 00007f6c1dc00f90       80
00007f6ad0965d00 00007f6c1dc00f90       80
00007f6ad0965df0 00007f6c1dc00f90       80
00007f6ad0965ee0 00007f6c1dc00f90       80

Statistics:
              MT    Count    TotalSize Class Name
00007f6c1dc00f90   206770     19494060 System.String
Total 206770 objects
```

<span data-ttu-id="8e07d-159">现在可以对 `System.String` 实例使用 `gcroot` 命令，以查看对象的根方式和原因。</span><span class="sxs-lookup"><span data-stu-id="8e07d-159">You can now use the `gcroot` command on a `System.String` instance to see how and why the object is rooted.</span></span> <span data-ttu-id="8e07d-160">请耐心等待，因为对于 30 MB 的堆，此命令需要几分钟的时间：</span><span class="sxs-lookup"><span data-stu-id="8e07d-160">Be patient because this command takes several minutes with a 30-MB heap:</span></span>

```console
> gcroot -all 00007f6ad09421f8

Thread 3f68:
    00007F6795BB58A0 00007F6C1D7D0745 System.Diagnostics.Tracing.CounterGroup.PollForValues() [/_/src/System.Private.CoreLib/shared/System/Diagnostics/Tracing/CounterGroup.cs @ 260]
        rbx:  (interior)
            ->  00007F6BDFFFF038 System.Object[]
            ->  00007F69D0033570 testwebapi.Controllers.Processor
            ->  00007F69D0033588 testwebapi.Controllers.CustomerCache
            ->  00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
            ->  00007F6C000148A0 testwebapi.Controllers.Customer[]
            ->  00007F6AD0942258 testwebapi.Controllers.Customer
            ->  00007F6AD09421F8 System.String

HandleTable:
    00007F6C98BB15F8 (pinned handle)
    -> 00007F6BDFFFF038 System.Object[]
    -> 00007F69D0033570 testwebapi.Controllers.Processor
    -> 00007F69D0033588 testwebapi.Controllers.CustomerCache
    -> 00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
    -> 00007F6C000148A0 testwebapi.Controllers.Customer[]
    -> 00007F6AD0942258 testwebapi.Controllers.Customer
    -> 00007F6AD09421F8 System.String

Found 2 roots.
```

<span data-ttu-id="8e07d-161">可以看到 `String` 由 `Customer` 对象直接保存，并由 `CustomerCache` 对象间接保存。</span><span class="sxs-lookup"><span data-stu-id="8e07d-161">You can see that the `String` is directly held by the `Customer` object and indirectly held by a `CustomerCache` object.</span></span>

<span data-ttu-id="8e07d-162">可以继续转储对象，以查看大多数 `String` 对象是否遵循类似的模式。</span><span class="sxs-lookup"><span data-stu-id="8e07d-162">You can continue dumping out objects to see that most `String` objects follow a similar pattern.</span></span> <span data-ttu-id="8e07d-163">此时，调查会提供足够的信息来确定代码中的根本原因。</span><span class="sxs-lookup"><span data-stu-id="8e07d-163">At this point, the investigation provided sufficient information to identify the root cause in your code.</span></span>

<span data-ttu-id="8e07d-164">可通过此常规过程确定主要内存泄漏源。</span><span class="sxs-lookup"><span data-stu-id="8e07d-164">This general procedure allows you to identify the source of major memory leaks.</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="8e07d-165">清理资源</span><span class="sxs-lookup"><span data-stu-id="8e07d-165">Clean up resources</span></span>

<span data-ttu-id="8e07d-166">在本教程中，你已启动一个示例 Web 服务器。</span><span class="sxs-lookup"><span data-stu-id="8e07d-166">In this tutorial, you started a sample web server.</span></span> <span data-ttu-id="8e07d-167">此服务器应已关闭，如[重新启动失败的进程](#restart-the-failed-process)部分所述。</span><span class="sxs-lookup"><span data-stu-id="8e07d-167">This server should have been shut down as explained in the [Restart the failed process](#restart-the-failed-process) section.</span></span>

<span data-ttu-id="8e07d-168">还可以删除已创建的转储文件。</span><span class="sxs-lookup"><span data-stu-id="8e07d-168">You can also delete the dump file that was created.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e07d-169">请参阅</span><span class="sxs-lookup"><span data-stu-id="8e07d-169">See also</span></span>

- <span data-ttu-id="8e07d-170">用于列出进程的 [dotnet-trace](dotnet-trace.md)</span><span class="sxs-lookup"><span data-stu-id="8e07d-170">[dotnet-trace](dotnet-trace.md) to list processes</span></span>
- <span data-ttu-id="8e07d-171">用于检查托管内存使用情况的 [dotnet-counters](dotnet-counters.md)</span><span class="sxs-lookup"><span data-stu-id="8e07d-171">[dotnet-counters](dotnet-counters.md) to check managed memory usage</span></span>
- <span data-ttu-id="8e07d-172">用于收集和分析转储文件的 [dotnet-dump](dotnet-dump.md)</span><span class="sxs-lookup"><span data-stu-id="8e07d-172">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file</span></span>
- [<span data-ttu-id="8e07d-173">dotnet/diagnostics</span><span class="sxs-lookup"><span data-stu-id="8e07d-173">dotnet/diagnostics</span></span>](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

## <a name="next-steps"></a><span data-ttu-id="8e07d-174">后续步骤</span><span class="sxs-lookup"><span data-stu-id="8e07d-174">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8e07d-175">调试 .NET Core 中的高 CPU</span><span class="sxs-lookup"><span data-stu-id="8e07d-175">Debug high CPU in .NET Core</span></span>](debug-highcpu.md)

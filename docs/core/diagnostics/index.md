---
title: 诊断工具概述 - .NET Core
description: 概述用于 .NET Core 应用程序的工具和技术。
ms.date: 07/16/2020
ms.topic: overview
ms.openlocfilehash: d78b73e53637927ecb877dd69054f75a1f5ac91f
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/29/2020
ms.locfileid: "91437999"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="5a0f0-103">.NET Core 中提供哪些诊断工具？</span><span class="sxs-lookup"><span data-stu-id="5a0f0-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="5a0f0-104">软件并非始终按预计方式运行，但 .NET Core 具有可帮助用户快速有效地诊断这些问题的工具和 API。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="5a0f0-105">本文可帮助用户查找各种所需的工具。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggers"></a><span data-ttu-id="5a0f0-106">托管调试器</span><span class="sxs-lookup"><span data-stu-id="5a0f0-106">Managed debuggers</span></span>

<span data-ttu-id="5a0f0-107">借助[托管调试器](managed-debuggers.md)，用户可以与程序进行交互。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-107">[Managed debuggers](managed-debuggers.md) allow you to interact with your program.</span></span> <span data-ttu-id="5a0f0-108">暂停、增量执行、检查和恢复操作可让用户深入了解代码的行为。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="5a0f0-109">调试器是诊断易于重现的功能问题的首选。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracing"></a><span data-ttu-id="5a0f0-110">日志记录和跟踪</span><span class="sxs-lookup"><span data-stu-id="5a0f0-110">Logging and tracing</span></span>

<span data-ttu-id="5a0f0-111">[日志记录和跟踪](logging-tracing.md)是相关技术。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-111">[Logging and tracing](logging-tracing.md) are related techniques.</span></span> <span data-ttu-id="5a0f0-112">它们指的是用于创建日志文件的检测代码。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="5a0f0-113">这些文件记录了程序操作的详细信息。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-113">The files record the details of what a program does.</span></span> <span data-ttu-id="5a0f0-114">这些细节可用于诊断最复杂的问题。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="5a0f0-115">当与时间戳结合使用时，这些技术在性能调查中也非常有用。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="unit-testing"></a><span data-ttu-id="5a0f0-116">单元测试</span><span class="sxs-lookup"><span data-stu-id="5a0f0-116">Unit testing</span></span>

<span data-ttu-id="5a0f0-117">[单元测试](../testing/index.md)是持续集成和部署高质量软件的关键组件。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-117">[Unit testing](../testing/index.md) is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="5a0f0-118">单元测试的目的在于，在用户操作导致系统出现问题时提前向其发出警告。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-118">Unit tests are designed to give you an early warning when you break something.</span></span>

## <a name="collect-diagnostics-in-containers"></a><span data-ttu-id="5a0f0-119">收集容器中的诊断</span><span class="sxs-lookup"><span data-stu-id="5a0f0-119">Collect diagnostics in containers</span></span>

<span data-ttu-id="5a0f0-120">也可使用非容器化 Linux 环境中使用的相同诊断工具[收集容器中的诊断](diagnostics-in-containers.md)。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-120">The same diagnostics tools that are used in non-containerized Linux environments can also be used to [collect diagnostics in containers](diagnostics-in-containers.md).</span></span> <span data-ttu-id="5a0f0-121">只需进行几次使用更改就可使这些工具在 Docker 容器中运行。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-121">There are just a few usage changes needed to make sure the tools work in a Docker container.</span></span>

## <a name="debug-linux-dumps"></a><span data-ttu-id="5a0f0-122">调试 Linux 转储</span><span class="sxs-lookup"><span data-stu-id="5a0f0-122">Debug Linux dumps</span></span>

<span data-ttu-id="5a0f0-123">[调试 Linux 转储](debug-linux-dumps.md)说明了如何收集和分析 Linux 上的转储。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-123">[Debug Linux dumps](debug-linux-dumps.md) explains how to collect and analyze dumps on Linux.</span></span>

## <a name="net-core-diagnostic-global-tools"></a><span data-ttu-id="5a0f0-124">.NET Core 诊断全局工具</span><span class="sxs-lookup"><span data-stu-id="5a0f0-124">.NET Core diagnostic global tools</span></span>

### <a name="dotnet-counters"></a><span data-ttu-id="5a0f0-125">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="5a0f0-125">dotnet-counters</span></span>

<span data-ttu-id="5a0f0-126">[dotnet-counters](dotnet-counters.md) 是一个性能监视工具，用于初级运行状况监视和性能调查。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-126">[dotnet-counters](dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span> <span data-ttu-id="5a0f0-127">它通过 <xref:System.Diagnostics.Tracing.EventCounter> API 观察已发布的性能计数器值。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-127">It observes performance counter values published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="5a0f0-128">例如，可以快速监视 CPU 使用情况或 .NET Core 应用程序中的异常率等指标。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-128">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application.</span></span>

### <a name="dotnet-dump"></a><span data-ttu-id="5a0f0-129">dotnet-dump</span><span class="sxs-lookup"><span data-stu-id="5a0f0-129">dotnet-dump</span></span>

<span data-ttu-id="5a0f0-130">通过 [dotnet-dump](dotnet-dump.md) 工具，可在不使用本机调试器的情况下收集和分析 Windows 和 Linux 核心转储。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-130">The [dotnet-dump](dotnet-dump.md) tool is a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

### <a name="dotnet-gcdump"></a><span data-ttu-id="5a0f0-131">dotnet-gcdump</span><span class="sxs-lookup"><span data-stu-id="5a0f0-131">dotnet-gcdump</span></span>

<span data-ttu-id="5a0f0-132">[dotnet-gcdump](dotnet-gcdump.md) 工具可用于为活动 .NET 进程收集 GC（垃圾回收器）转储。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-132">The [dotnet-gcdump](dotnet-gcdump.md) tool is a way to collect GC (Garbage Collector) dumps of live .NET processes.</span></span>

### <a name="dotnet-trace"></a><span data-ttu-id="5a0f0-133">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="5a0f0-133">dotnet-trace</span></span>

<span data-ttu-id="5a0f0-134">分析数据通过 .NET Core 中的 `EventPipe` 公开。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-134">.NET Core includes what is called the `EventPipe` through which diagnostics data is exposed.</span></span> <span data-ttu-id="5a0f0-135">通过 [dotnet-trace](dotnet-trace.md) 工具，可以使用来自应用的有意思的分析数据，这些数据可帮助你分析应用运行缓慢的根本原因。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-135">The [dotnet-trace](dotnet-trace.md) tool allows you to consume interesting profiling data from your app that can help in scenarios where you need to root cause apps running slow.</span></span>

### <a name="dotnet-symbol"></a><span data-ttu-id="5a0f0-136">dotnet-symbol</span><span class="sxs-lookup"><span data-stu-id="5a0f0-136">dotnet-symbol</span></span>

<span data-ttu-id="5a0f0-137">[dotnet-symbol](dotnet-symbol.md) 用于下载打开核心转储或小型转储所需的文件（符号、DAC/DBI、主机文件等）。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-137">[dotnet-symbol](dotnet-symbol.md) downloads files (symbols, DAC/DBI, host files, etc.) needed to open a core dump or minidump.</span></span> <span data-ttu-id="5a0f0-138">如果需要使用符号和模块来调试在其他计算机上捕获的转储文件，请使用此工具。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-138">Use this tool if you need symbols and modules to debug a dump file captured on a different machine.</span></span>

### <a name="dotnet-sos"></a><span data-ttu-id="5a0f0-139">dotnet-sos</span><span class="sxs-lookup"><span data-stu-id="5a0f0-139">dotnet-sos</span></span>

<span data-ttu-id="5a0f0-140">[dotnet-sos](dotnet-sos.md) 用于在 Linux 或 MacOS 上安装 [SOS 调试扩展](../../framework/tools/sos-dll-sos-debugging-extension.md)（如果使用较旧的调试工具，则在 Windows 上进行安装）。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-140">[dotnet-sos](dotnet-sos.md) is used to install the [SOS debugging extension](../../framework/tools/sos-dll-sos-debugging-extension.md) on Linux or MacOS (or on Windows if using older debugging tools).</span></span>

## <a name="net-core-diagnostics-tutorials"></a><span data-ttu-id="5a0f0-141">.NET Core 诊断教程</span><span class="sxs-lookup"><span data-stu-id="5a0f0-141">.NET Core diagnostics tutorials</span></span>

### <a name="debug-a-memory-leak"></a><span data-ttu-id="5a0f0-142">调试内存泄露</span><span class="sxs-lookup"><span data-stu-id="5a0f0-142">Debug a memory leak</span></span>

<span data-ttu-id="5a0f0-143">[教程：调试内存泄漏](debug-memory-leak.md)演示了如何查找内存泄漏。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-143">[Tutorial: Debug a memory leak](debug-memory-leak.md) walks through finding a memory leak.</span></span> <span data-ttu-id="5a0f0-144">[dotnet-counters](dotnet-counters.md) 工具用于确认泄露，[dotnet-dump](dotnet-dump.md) 工具用于诊断泄露。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-144">The [dotnet-counters](dotnet-counters.md) tool is used to confirm the leak and the [dotnet-dump](dotnet-dump.md) tool is used to diagnose the leak.</span></span>

### <a name="debug-high-cpu-usage"></a><span data-ttu-id="5a0f0-145">调试高 CPU 使用率</span><span class="sxs-lookup"><span data-stu-id="5a0f0-145">Debug high CPU usage</span></span>

<span data-ttu-id="5a0f0-146">[教程：调试高 CPU 使用率](debug-highcpu.md)逐步介绍了如何调查高 CPU 使用率。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-146">[Tutorial: Debug high CPU usage](debug-highcpu.md) walks you through investigating high CPU usage.</span></span> <span data-ttu-id="5a0f0-147">它使用 [dotnet-counters](dotnet-counters.md) 工具来确认高 CPU 使用率。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-147">It uses the [dotnet-counters](dotnet-counters.md) tool to confirm the high CPU usage.</span></span> <span data-ttu-id="5a0f0-148">然后，它逐步介绍了如何使用[性能分析实用工具 (`dotnet-trace`) 跟踪](dotnet-trace.md)或 Linux `perf` 来收集和查看 CPU 使用率配置文件。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-148">It then walks you through using [Trace for performance analysis utility (`dotnet-trace`)](dotnet-trace.md) or Linux `perf` to collect and view CPU usage profile.</span></span>

### <a name="debug-deadlock"></a><span data-ttu-id="5a0f0-149">调试死锁</span><span class="sxs-lookup"><span data-stu-id="5a0f0-149">Debug deadlock</span></span>

<span data-ttu-id="5a0f0-150">[教程：调试死锁](debug-deadlock.md)介绍了如何使用 [dotnet-dump](dotnet-dump.md) 工具来调查线程和锁。</span><span class="sxs-lookup"><span data-stu-id="5a0f0-150">[Tutorial: Debug deadlock](debug-deadlock.md) shows you how to use the [dotnet-dump](dotnet-dump.md) tool to investigate threads and locks.</span></span>

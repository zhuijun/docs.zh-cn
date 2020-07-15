---
title: CLR ETW 提供程序
description: 查看有关 Windows （ETW）提供程序的两个公共语言运行时（CLR）事件跟踪的详细信息： runtimne 提供程序和断开提供程序。
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, CLR providers
- CLR ETW providers
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
ms.openlocfilehash: 9f86e8334482880c4f7cb23ec93a3c826c083389
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309646"
---
# <a name="clr-etw-providers"></a><span data-ttu-id="94fb4-103">CLR ETW 提供程序</span><span class="sxs-lookup"><span data-stu-id="94fb4-103">CLR ETW Providers</span></span>
<span data-ttu-id="94fb4-104">公共语言运行时 (CLR) 具有两个提供程序：运行时提供程序和断开提供程序。</span><span class="sxs-lookup"><span data-stu-id="94fb4-104">The common language runtime (CLR) has two providers: the runtime provider and the rundown provider.</span></span>  
  
 <span data-ttu-id="94fb4-105">运行时提供程序根据启用的关键字（事件的类别）引发事件。</span><span class="sxs-lookup"><span data-stu-id="94fb4-105">The runtime provider raises events, depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="94fb4-106">例如，可以通过启用 `LoaderKeyword` 关键字收集加载程序事件。</span><span class="sxs-lookup"><span data-stu-id="94fb4-106">For example, you can collect loader events by enabling the `LoaderKeyword` keyword.</span></span>  
  
 <span data-ttu-id="94fb4-107">Windows 事件跟踪（ETW）事件被记录到一个文件中，该文件的 .etl 扩展名为 .etl，以后可根据需要在逗号分隔值（.csv）文件中对其进行后期处理。</span><span class="sxs-lookup"><span data-stu-id="94fb4-107">Event Tracing for Windows (ETW) events are logged into a file that has an .etl extension, which can later be post-processed in comma-separated value (.csv) files as needed.</span></span> <span data-ttu-id="94fb4-108">有关如何将 .etl 文件转换为 .csv 文件的信息，请参阅[控制 .NET Framework 日志记录](controlling-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="94fb4-108">For information about how to convert the .etl file to a .csv file, see [Controlling .NET Framework Logging](controlling-logging.md).</span></span>  
  
## <a name="the-runtime-provider"></a><span data-ttu-id="94fb4-109">运行时提供程序</span><span class="sxs-lookup"><span data-stu-id="94fb4-109">The Runtime Provider</span></span>  
 <span data-ttu-id="94fb4-110">运行时提供程序是主 CLR ETW 提供程序。</span><span class="sxs-lookup"><span data-stu-id="94fb4-110">The runtime provider is the main CLR ETW provider.</span></span>  
  
 <span data-ttu-id="94fb4-111">CLR 运行时提供程序 GUID 是 e13c0d23-ccbc-4e12-931b-d9cc2eee27e4。</span><span class="sxs-lookup"><span data-stu-id="94fb4-111">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
 <span data-ttu-id="94fb4-112">有关如何使用常用工具记录并查看 CLR ETW 事件的示例，请参阅[控制 .NET Framework 日志记录](controlling-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="94fb4-112">For examples of how to log and view CLR ETW events by using commonly available tools, see [Controlling .NET Framework Logging](controlling-logging.md).</span></span>  
  
 <span data-ttu-id="94fb4-113">除了使用 `LoaderKeyword` 之类的关键字以外，可能还需要启用用于记录会被过于频繁地引发的事件的关键字。</span><span class="sxs-lookup"><span data-stu-id="94fb4-113">In addition to using keywords such as `LoaderKeyword`, you may have to enable keywords for logging events that may be raised too frequently.</span></span> <span data-ttu-id="94fb4-114">`StartEnumerationKeyword` 和 `EndEnumerationKeyword` 关键字启用这些事件，[CLR ETW 关键字和级别](clr-etw-keywords-and-levels.md)中对这些关键字进行了总结。</span><span class="sxs-lookup"><span data-stu-id="94fb4-114">The `StartEnumerationKeyword` and the `EndEnumerationKeyword` keywords enable these events and are summarized in [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>  
  
## <a name="the-rundown-provider"></a><span data-ttu-id="94fb4-115">断开提供程序</span><span class="sxs-lookup"><span data-stu-id="94fb4-115">The Rundown Provider</span></span>  
 <span data-ttu-id="94fb4-116">对于某些特殊用途必须启用断开提供程序。</span><span class="sxs-lookup"><span data-stu-id="94fb4-116">The rundown provider must be turned on for certain special-purpose uses.</span></span> <span data-ttu-id="94fb4-117">但对于大多数用户来说，运行时提供程序应该就足够了。</span><span class="sxs-lookup"><span data-stu-id="94fb4-117">However, for a majority of users, the runtime provider should suffice.</span></span>  
  
 <span data-ttu-id="94fb4-118">CLR 断开提供程序 GUID 是 A669021C-C450-4609-A035-5AF59AF4DF18。</span><span class="sxs-lookup"><span data-stu-id="94fb4-118">The CLR rundown provider GUID is A669021C-C450-4609-A035-5AF59AF4DF18.</span></span>  
  
 <span data-ttu-id="94fb4-119">通常情况下，ETW 日志记录在进程启动前启用，在进程退出后关闭。</span><span class="sxs-lookup"><span data-stu-id="94fb4-119">Normally, ETW logging is enabled before a process launches, and the logging is turned off after the process exits.</span></span> <span data-ttu-id="94fb4-120">但是，如果在执行进程的过程中打开 ETW 日志记录功能，则需要有关进程的其他信息。</span><span class="sxs-lookup"><span data-stu-id="94fb4-120">However, if ETW logging is turned on while the process is executing, additional information is needed about the process.</span></span> <span data-ttu-id="94fb4-121">例如，对于符号解析，必须记录在启用日志记录功能前已经加载的方法的方法事件。</span><span class="sxs-lookup"><span data-stu-id="94fb4-121">For example, for symbol resolution you have to log method events for methods that were already loaded before logging was turned on.</span></span>  
  
 <span data-ttu-id="94fb4-122">`DCStart` 和 `DCEnd` 事件捕获进程在数据收集开始和停止时的状态。</span><span class="sxs-lookup"><span data-stu-id="94fb4-122">The `DCStart` and `DCEnd` events capture the state of the process when data collection was started and stopped.</span></span> <span data-ttu-id="94fb4-123">（状态指的是高级别的信息，包括已实时（JIT）编译的方法和已加载的程序集。这两个事件可以提供有关进程中已发生的事件的信息;例如，JIT 编译了哪些方法，等等。</span><span class="sxs-lookup"><span data-stu-id="94fb4-123">(State refers to information at a high level, including the methods that were already just-in-time (JIT) compiled and assemblies that were loaded.) These two events can provide information about what has already happened in the process; for example, which methods were JIT- compiled, and so on.</span></span>  
  
 <span data-ttu-id="94fb4-124">在使用断开提供程序时只引发名称中包含 `DC`、`DCStart`、`DCEnd` 或 `DCInit` 的事件。</span><span class="sxs-lookup"><span data-stu-id="94fb4-124">Only the events with `DC`, `DCStart`, `DCEnd`, or `DCInit` in their names are raised under the rundown provider.</span></span> <span data-ttu-id="94fb4-125">此外，仅在使用断开提供程序时才引发这些事件。</span><span class="sxs-lookup"><span data-stu-id="94fb4-125">Additionally, these events are raised only under the rundown provider.</span></span>  
  
 <span data-ttu-id="94fb4-126">除事件关键字筛选器以外，断开提供程序还支持 `StartRundownKeyword` 和 `EndRundownKeyword` 关键字，以便提供定向筛选。</span><span class="sxs-lookup"><span data-stu-id="94fb4-126">In addition to the event keyword filters, the rundown provider also supports the `StartRundownKeyword` and `EndRundownKeyword` keywords to provide targeted filtering.</span></span>  
  
### <a name="start-rundown"></a><span data-ttu-id="94fb4-127">开始断开</span><span class="sxs-lookup"><span data-stu-id="94fb4-127">Start Rundown</span></span>  
 <span data-ttu-id="94fb4-128">使用 `StartRundownKeyword` 关键字启用断开提供程序的日志记录功能，会触发开始断开。</span><span class="sxs-lookup"><span data-stu-id="94fb4-128">A start rundown is triggered when logging under the rundown provider is enabled with the `StartRundownKeyword` keyword.</span></span> <span data-ttu-id="94fb4-129">这将导致引发 `DCStart` 事件并捕获系统的状态。</span><span class="sxs-lookup"><span data-stu-id="94fb4-129">This causes the `DCStart` event to be raised, and captures the state of the system.</span></span> <span data-ttu-id="94fb4-130">在枚举开始前引发 `DCStartInit`。</span><span class="sxs-lookup"><span data-stu-id="94fb4-130">Before the start of the enumeration, the `DCStartInit` event is raised.</span></span> <span data-ttu-id="94fb4-131">在枚举结束时引发 `DCStartComplete` 事件，通知控制器数据收集已正常终止。</span><span class="sxs-lookup"><span data-stu-id="94fb4-131">At the end of the enumeration, the `DCStartComplete` event is raised to notify the controller that data collection terminated normally.</span></span>  
  
### <a name="end-rundown"></a><span data-ttu-id="94fb4-132">结束断开</span><span class="sxs-lookup"><span data-stu-id="94fb4-132">End Rundown</span></span>  
 <span data-ttu-id="94fb4-133">使用 `EndRundownKeyword` 关键字启用断开提供程序的日志记录功能，会触发结束断开。</span><span class="sxs-lookup"><span data-stu-id="94fb4-133">An end rundown is triggered when logging under the rundown provider is enabled with the `EndRundownKeyword` keyword.</span></span> <span data-ttu-id="94fb4-134">结束断开将停止分析继续执行的进程。</span><span class="sxs-lookup"><span data-stu-id="94fb4-134">End rundown stops profiling on a process that continues to execute.</span></span> <span data-ttu-id="94fb4-135">`DCEnd` 事件捕获系统在分析停止时的状态。</span><span class="sxs-lookup"><span data-stu-id="94fb4-135">The `DCEnd` events capture the state of the system when profiling is stopped.</span></span>  
  
 <span data-ttu-id="94fb4-136">在枚举开始前引发 `DCEndInit`。</span><span class="sxs-lookup"><span data-stu-id="94fb4-136">Before the start of the enumeration, the `DCEndInit` event is raised.</span></span> <span data-ttu-id="94fb4-137">在枚举结束时引发 `DCEndComplete` 事件，通知使用者数据收集已正常终止。</span><span class="sxs-lookup"><span data-stu-id="94fb4-137">At the end of the enumeration, the `DCEndComplete` event is raised to notify the consumer that data collection terminated normally.</span></span> <span data-ttu-id="94fb4-138">开始断开和结束断开主要用于托管符号解析。</span><span class="sxs-lookup"><span data-stu-id="94fb4-138">Start rundown and end rundown are primarily used for managed symbol resolution.</span></span> <span data-ttu-id="94fb4-139">开始断开可以为分析会话开始前已实时编译的方法提供地址范围信息。</span><span class="sxs-lookup"><span data-stu-id="94fb4-139">Start rundown can provide address range information for methods that were already JIT-compiled before the profiling session was started.</span></span> <span data-ttu-id="94fb4-140">结束断开可以为分析将关闭时已实时编译的方法提供地址范围信息。</span><span class="sxs-lookup"><span data-stu-id="94fb4-140">End rundown can provide address range information for all methods that have been JIT-compiled when profiling is about to be turned off.</span></span>  
  
 <span data-ttu-id="94fb4-141">分析会话停止时，不会自动发生结束断开。</span><span class="sxs-lookup"><span data-stu-id="94fb4-141">End rundown does not happen automatically when a profiling session is stopped.</span></span> <span data-ttu-id="94fb4-142">相反，尝试执行托管符号解析的工具必须在即将停止分析之前，显式调用 CLR 断开提供程序会话，同时启用 `EndRundownKeyword` 关键字。</span><span class="sxs-lookup"><span data-stu-id="94fb4-142">Instead, a tool that is seeking to perform managed symbol resolution has to explicitly invoke a CLR rundown provider session with the `EndRundownKeyword` keyword enabled, just before profiling is stopped.</span></span>  
  
 <span data-ttu-id="94fb4-143">尽管开始断开或结束断开都能够提供有关托管符号解析的方法地址范围信息，但建议使用 `EndRundownKeyword` 关键字（提供 `DCEnd` 事件），而不使用 `StartRundownKeyword` 关键字（提供 `DCStart` 事件）。</span><span class="sxs-lookup"><span data-stu-id="94fb4-143">Although either start rundown or end rundown can provide method address range information for managed symbol resolution, we recommend that you use the `EndRundownKeyword` keyword (which supplies `DCEnd` events) instead of the `StartRundownKeyword` keyword (which supplies `DCStart` events).</span></span> <span data-ttu-id="94fb4-144">使用 `StartRundownKeyword` 会导致在分析会话期间发生断开，这可能会干扰所分析的方案。</span><span class="sxs-lookup"><span data-stu-id="94fb4-144">Using `StartRundownKeyword` causes the rundown to happen during the profiling session, which may disturb the profiled scenario.</span></span>  
  
## <a name="etw-data-collection-using-runtime-and-rundown-providers"></a><span data-ttu-id="94fb4-145">使用运行时提供程序和断开提供程序执行 ETW 数据收集</span><span class="sxs-lookup"><span data-stu-id="94fb4-145">ETW Data Collection Using Runtime and Rundown Providers</span></span>  
 <span data-ttu-id="94fb4-146">下面的示例演示如何以一种允许托管进程的符号解析并将影响减至最小的方式来使用 CLR 断开提供程序，而不考虑进程是在所分析的窗口内部还是外部开始或结束的。</span><span class="sxs-lookup"><span data-stu-id="94fb4-146">The following example demonstrates how to use the CLR rundown provider in a way that allows symbol resolution of managed processes with minimal impact, regardless of whether the processes start or end inside or outside the profiled window.</span></span>  
  
1. <span data-ttu-id="94fb4-147">使用 CLR 运行时提供程序启用 ETW 日志记录：</span><span class="sxs-lookup"><span data-stu-id="94fb4-147">Turn on ETW logging by using the CLR runtime provider:</span></span>  
  
    ```console
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl
    ```  
  
     <span data-ttu-id="94fb4-148">日志将保存到 clr1.etl 文件中。</span><span class="sxs-lookup"><span data-stu-id="94fb4-148">The log will be saved to the clr1.etl file.</span></span>  
  
2. <span data-ttu-id="94fb4-149">要在进程继续执行的过程中停止分析，请启动断开提供程序以捕获 `DCEnd` 事件：</span><span class="sxs-lookup"><span data-stu-id="94fb4-149">To stop profiling while the process continues to execute, start the rundown provider to capture the `DCEnd` events:</span></span>  
  
    ```console
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl
    ```  
  
     <span data-ttu-id="94fb4-150">这将使 `DCEnd` 事件的收集开始断开会话。</span><span class="sxs-lookup"><span data-stu-id="94fb4-150">This enables the collection of `DCEnd` events to start a rundown session.</span></span> <span data-ttu-id="94fb4-151">可能需要等待 30 至 60 秒钟，才能收集完所有事件。</span><span class="sxs-lookup"><span data-stu-id="94fb4-151">You may need to wait 30 to 60 seconds for all events to be collected.</span></span> <span data-ttu-id="94fb4-152">日志将保存到 clr1.et2 文件中。</span><span class="sxs-lookup"><span data-stu-id="94fb4-152">The log will be saved to the clr1.et2 file.</span></span>  
  
3. <span data-ttu-id="94fb4-153">关闭所有 ETW 分析：</span><span class="sxs-lookup"><span data-stu-id="94fb4-153">Turn off all ETW profiling:</span></span>  
  
    ```console
    xperf -stop clrRundown
    xperf -stop clr  
    ```  
  
4. <span data-ttu-id="94fb4-154">合并分析以便创建一个日志文件：</span><span class="sxs-lookup"><span data-stu-id="94fb4-154">Merge the profiles to create one log file:</span></span>  
  
    ```console
    xperf -merge clr1.etl clr2.etl merged.etl  
    ```  
  
     <span data-ttu-id="94fb4-155">merged.etl 文件将包含来自运行时提供程序会话和断开提供程序会话的事件。</span><span class="sxs-lookup"><span data-stu-id="94fb4-155">The merged.etl file will contain the events from the runtime and the rundown provider sessions.</span></span>  
  
 <span data-ttu-id="94fb4-156">使用工具可以执行步骤 2 和步骤 3（开始断开会话然后终止分析），而不是在用户请求停止分析后立即关闭分析。</span><span class="sxs-lookup"><span data-stu-id="94fb4-156">A tool can execute steps 2 and 3 (starting a rundown session and then terminating profiling) instead of immediately turning off profiling when a user requests profiling to be stopped.</span></span> <span data-ttu-id="94fb4-157">还可以执行步骤 4。</span><span class="sxs-lookup"><span data-stu-id="94fb4-157">A tool can also execute step 4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94fb4-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="94fb4-158">See also</span></span>

- [<span data-ttu-id="94fb4-159">公共语言运行时中的 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="94fb4-159">ETW Events in the Common Language Runtime</span></span>](etw-events-in-the-common-language-runtime.md)

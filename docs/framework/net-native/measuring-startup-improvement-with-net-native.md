---
title: 使用 .NET Native 衡量启动改善
ms.date: 03/30/2017
ms.assetid: c4d25b24-9c1a-4b3e-9705-97ba0d6c0289
ms.openlocfilehash: 5d20fa77ee299065ced406bf8cd531b8c54b6c33
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540883"
---
# <a name="measuring-startup-improvement-with-net-native"></a><span data-ttu-id="2f4b2-102">使用 .NET Native 衡量启动改善</span><span class="sxs-lookup"><span data-stu-id="2f4b2-102">Measuring Startup Improvement with .NET Native</span></span>
<span data-ttu-id="2f4b2-103">.NET Native 显著改善了应用的启动时间。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-103">.NET Native significantly improves the launch time of apps.</span></span> <span data-ttu-id="2f4b2-104">这一改善在便携式、低功耗设备上和在使用复杂应用时尤其明显。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-104">This improvement is particularly noticeable on portable, low-powered devices and with complex apps.</span></span> <span data-ttu-id="2f4b2-105">该主题将帮助你初步了解衡量这个启动提升所需的基本检测。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-105">This topic helps you get started with the basic instrumentation needed to measure this startup improvement.</span></span>  
  
 <span data-ttu-id="2f4b2-106">为方便性能调查，.NET Framework 和 Windows 使用一个名为 Windows 事件跟踪 (ETW) 的事件框架，它允许你的应用在事件发生时通知工具。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-106">To facilitate performance investigations, the .NET Framework and Windows use an event framework called Event Tracing for Windows (ETW) that allows your app to notify tooling when events happen.</span></span> <span data-ttu-id="2f4b2-107">然后你可以使用一个名为 PerfView 的工具查看和分析 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-107">You can then use a tool called PerfView to easily view and analyze of ETW events.</span></span> <span data-ttu-id="2f4b2-108">该主题解释了如何：</span><span class="sxs-lookup"><span data-stu-id="2f4b2-108">This topic explains how to:</span></span>  
  
- <span data-ttu-id="2f4b2-109">使用 <xref:System.Diagnostics.Tracing.EventSource> 类来发出事件。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-109">Use the <xref:System.Diagnostics.Tracing.EventSource> class to emit events.</span></span>  
  
- <span data-ttu-id="2f4b2-110">使用 PerfView 来收集这些事件。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-110">Use PerfView to gather those events.</span></span>  
  
- <span data-ttu-id="2f4b2-111">使用 PerfView 来显示这些事件。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-111">Use PerfView to display those events.</span></span>  
  
## <a name="using-eventsource-to-emit-events"></a><span data-ttu-id="2f4b2-112">使用 EventSource 来发出事件</span><span class="sxs-lookup"><span data-stu-id="2f4b2-112">Using EventSource to emit events</span></span>  
 <span data-ttu-id="2f4b2-113"><xref:System.Diagnostics.Tracing.EventSource> 提供了一个基类，从该基类可以创建自定义事件提供程序。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-113"><xref:System.Diagnostics.Tracing.EventSource> provides a base class from which to create a custom event provider.</span></span> <span data-ttu-id="2f4b2-114">通常，你可以创建 <xref:System.Diagnostics.Tracing.EventSource> 的一个子类并使用你自己的事件方法环绕 `Write*` 方法。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-114">Generally, you create a subclass of <xref:System.Diagnostics.Tracing.EventSource> and wrap the `Write*` methods with your own event methods.</span></span> <span data-ttu-id="2f4b2-115">一个单独模式通常用于每个 <xref:System.Diagnostics.Tracing.EventSource>。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-115">A singleton pattern is generally used for each <xref:System.Diagnostics.Tracing.EventSource>.</span></span>  
  
 <span data-ttu-id="2f4b2-116">例如，以下实例中的类可以用来衡量两个性能特征：</span><span class="sxs-lookup"><span data-stu-id="2f4b2-116">For example, the class in the following example can be used to measure two performance characteristics:</span></span>  
  
- <span data-ttu-id="2f4b2-117">`App` 类构造函数得到调用所花时间。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-117">The time until the `App` class constructor was called.</span></span>  
  
- <span data-ttu-id="2f4b2-118">`MainPage` 构造函数得到调用所花时间。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-118">The time until the `MainPage` constructor was called.</span></span>  
  
 [!code-csharp[ProjectN_ETW#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw1.cs#1)]  
  
 <span data-ttu-id="2f4b2-119">有几个需要记住的要点。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-119">There are a few things to notice here.</span></span> <span data-ttu-id="2f4b2-120">首先，在 `AppEventSource.Log` 中创建一个单独实例。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-120">First, a singleton is created in `AppEventSource.Log`.</span></span> <span data-ttu-id="2f4b2-121">该实例将用于所有记录。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-121">That instance will be used for all logging.</span></span> <span data-ttu-id="2f4b2-122">其次，每个事件方法都有一个 <xref:System.Diagnostics.Tracing.EventAttribute>。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-122">Second, each event method has an <xref:System.Diagnostics.Tracing.EventAttribute>.</span></span> <span data-ttu-id="2f4b2-123">这将帮助工具将 <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> 方法的索引与在 `AppEventSource` 上调用的方法关联起来。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-123">This helps tooling associate the index of the <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> method with the method that was called on `AppEventSource`.</span></span>  
  
 <span data-ttu-id="2f4b2-124">注意，这些事件纯粹是说明性的。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-124">Note that these events are purely illustrative.</span></span> <span data-ttu-id="2f4b2-125">大多数应用代码会在这些事件之后运行。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-125">Most app code will run after these events.</span></span> <span data-ttu-id="2f4b2-126">你应该了解代码中的哪些事件对应于用户交互，衡量它们并提高这些基准。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-126">You should understand which events in code correspond to user interactions, measure those, and improve those benchmarks.</span></span> <span data-ttu-id="2f4b2-127">并且，这些事件本身每次只记录一个实例。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-127">Also, the events themselves log only a single instance in time.</span></span> <span data-ttu-id="2f4b2-128">通常让成对的实例为每一步操作开始和停止事件是有用的。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-128">It’s often useful to have paired start and stop events for every operation.</span></span> <span data-ttu-id="2f4b2-129">检查应用启动时，开始事件通常是操作系统发出的“Process/Star”事件。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-129">When examining app startup, the start event is generally the "Process/Start" event that the operating system emits.</span></span>  
  
 <span data-ttu-id="2f4b2-130">例如，假设你正在创建一个 RSS 阅读器。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-130">For example, suppose you are creating an RSS reader.</span></span> <span data-ttu-id="2f4b2-131">一些记录事件的有趣的时间点是：</span><span class="sxs-lookup"><span data-stu-id="2f4b2-131">A few interesting locations to log an event are:</span></span>  
  
- <span data-ttu-id="2f4b2-132">当主页首次呈现时。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-132">When the main page is first rendered.</span></span>  
  
- <span data-ttu-id="2f4b2-133">当旧的 RSS 故事从本地存储中遭到反序列化时。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-133">When old RSS stories are deserialized from local storage.</span></span>  
  
- <span data-ttu-id="2f4b2-134">当你的应用开始同步新故事时。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-134">When your app begins syncing new stories.</span></span>  
  
- <span data-ttu-id="2f4b2-135">当你的应用已完成同步新故事时。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-135">When your app has finished syncing new stories.</span></span>  
  
 <span data-ttu-id="2f4b2-136">检测应用程序非常简单：只需在派生类上调用适当的方法。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-136">Instrumenting an app is straightforward: Just call the appropriate method on the derived class.</span></span> <span data-ttu-id="2f4b2-137">通过使用前面实例中的 `AppEventSource`，你可以按照如下所示检测一个应用：</span><span class="sxs-lookup"><span data-stu-id="2f4b2-137">Using `AppEventSource` from the previous example, you can instrument an app as follows:</span></span>  
  
 [!code-csharp[ProjectN_ETW#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw2.cs#2)]  
  
 <span data-ttu-id="2f4b2-138">当应用得到检测后，你就可以收集事件。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-138">When the app is instrumented, you’re ready to gather events.</span></span>  
  
## <a name="gathering-events-with-perfview"></a><span data-ttu-id="2f4b2-139">使用 PerfView 收集事件</span><span class="sxs-lookup"><span data-stu-id="2f4b2-139">Gathering events with PerfView</span></span>  
 <span data-ttu-id="2f4b2-140">PerfView 使用 ETW 事件帮助你在设备上进行各种性能研究。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-140">PerfView uses ETW events to help you do all sorts of performance investigations on your app.</span></span> <span data-ttu-id="2f4b2-141">它还包括一个配置 GUI，这允许你打开或关闭事件的不同类型的记录。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-141">It also includes a configuration GUI that lets you turn logging for different types of events on or off.</span></span> <span data-ttu-id="2f4b2-142">PerfView 是一个免费的工具，可从 [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=28567) 下载。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-142">PerfView is a free tool and can be downloaded from the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=28567).</span></span> <span data-ttu-id="2f4b2-143">有关详细信息，请观看 [PerfView 教程视频](https://channel9.msdn.com/Series/PerfView-Tutorial).</span><span class="sxs-lookup"><span data-stu-id="2f4b2-143">For more information, watch the [PerfView tutorial videos](https://channel9.msdn.com/Series/PerfView-Tutorial).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f4b2-144">PerfView 无法用于收集 ARM 系统上的事件。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-144">PerfView cannot be used to collect events on ARM systems.</span></span> <span data-ttu-id="2f4b2-145">有收集 ARM 系统上的事件，请使用 Windows 性能记录器 (WPR)。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-145">To collect events on ARM systems, use Windows Performance Recorder (WPR).</span></span> <span data-ttu-id="2f4b2-146">有关详细信息，请参阅 [Vance Morrison 的博客文章](/archive/blogs/vancem/collecting-etwperfview-data-on-an-windows-rt-winrt-arm-surface-device)。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-146">For more information, see [Vance Morrison's blog post](/archive/blogs/vancem/collecting-etwperfview-data-on-an-windows-rt-winrt-arm-surface-device).</span></span>  
  
 <span data-ttu-id="2f4b2-147">你也可以从命令行调用 PerfView。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-147">You can also invoke PerfView from the command line.</span></span> <span data-ttu-id="2f4b2-148">如仅要记录来自你的提供程序的事件，请打开“命令提示符”窗口并输入以下命令：</span><span class="sxs-lookup"><span data-stu-id="2f4b2-148">To log only the events from your provider, open the Command Prompt window and enter the command:</span></span>  
  
```console
perfview -KernelEvents:Process -OnlyProviders:*MyCompany-MyApp collect outputFile
```  
  
 <span data-ttu-id="2f4b2-149">其中：</span><span class="sxs-lookup"><span data-stu-id="2f4b2-149">where:</span></span>  
  
 `-KernelEvents:Process`  
 <span data-ttu-id="2f4b2-150">显示你想知道程序何时启动和停止。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-150">Indicates that you want to know when the process starts and stops.</span></span> <span data-ttu-id="2f4b2-151">你需要为你的应用设置“进程/开始”事件，才能使其从其他事件时间被扣除。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-151">You need the Process/Start event for your app so it can be subtracted from other event times.</span></span>  
  
 `-OnlyProviders:*MyCompany-MyApp`  
 <span data-ttu-id="2f4b2-152">关闭 PerfView 默认开启的其他提供程序，并开启 MyCompany-MyApp 提供程序。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-152">Turns off other providers that PerfView turns on by default, and turns on the MyCompany-MyApp provider.</span></span>  <span data-ttu-id="2f4b2-153">（此处的星号表示 <xref:System.Diagnostics.Tracing.EventSource>.）</span><span class="sxs-lookup"><span data-stu-id="2f4b2-153">(The asterisk indicates that it is an <xref:System.Diagnostics.Tracing.EventSource>.)</span></span>  
  
 `collect outputFile`  
 <span data-ttu-id="2f4b2-154">显示你想开始收集数据并将其保存到 outputFile.etl.zip。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-154">Indicates that you want to start collection and save the data to outputFile.etl.zip.</span></span>  
  
 <span data-ttu-id="2f4b2-155">在开启 PerfView 后运行你的应用。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-155">Run your app after starting PerfView.</span></span> <span data-ttu-id="2f4b2-156">运行你的程序时有几个需要谨记的要点：</span><span class="sxs-lookup"><span data-stu-id="2f4b2-156">There are a few things to remember when running your app:</span></span>  
  
- <span data-ttu-id="2f4b2-157">使用发布版本，而不是调试版本。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-157">Use a release build, not a debug build.</span></span> <span data-ttu-id="2f4b2-158">调试版本通常包含额外的错误检查和错误处理代码，会导致你的应用运行的速度比预期的要慢。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-158">Debug builds often contain extra error checking and error handling code that can cause your app to run slower than expected.</span></span>  
  
- <span data-ttu-id="2f4b2-159">运行附带调试程序的应用会影响应用性能。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-159">Running your app with a debugger attached affects the performance of your app.</span></span>  
  
- <span data-ttu-id="2f4b2-160">Windows 使用多种缓存策略来缩短应用启用时间。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-160">Windows uses multiple caching strategies to speed up app launch times.</span></span> <span data-ttu-id="2f4b2-161">如果你的应用目前缓存在内存中并且不需要从磁盘中加载，它的启动速度会更快。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-161">If your app is currently cached in memory and doesn't have to be loaded from disk, it will start faster.</span></span> <span data-ttu-id="2f4b2-162">要确保一致性，在衡量你的应用之前先将其启动和关闭数次。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-162">To ensure consistency, start and close your app a few times before measuring it.</span></span>  
  
 <span data-ttu-id="2f4b2-163">在已运行应用以便 PerfView 可以收集发出的事件时，选择“停止收集”按钮\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-163">When you’ve run your app so that PerfView can collect emitted events, choose the **Stop Collection** button.</span></span> <span data-ttu-id="2f4b2-164">通常，你应该在关闭应用之前停止收集，这样就不会收集到无关的事件。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-164">Generally, you should stop collection before closing your app so you don’t get extraneous events.</span></span> <span data-ttu-id="2f4b2-165">然而，如果你正在衡量关机或暂停性能，就应该继续收集。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-165">However, if you’re measuring shutdown or suspension performance, you’ll want to continue collection.</span></span>  
  
## <a name="displaying-the-events"></a><span data-ttu-id="2f4b2-166">正在显示事件</span><span class="sxs-lookup"><span data-stu-id="2f4b2-166">Displaying the events</span></span>  
 <span data-ttu-id="2f4b2-167">要查看已经收集到的事件，请使用 PerfView 打开所创建的 .etl 或 .etl.zip 文件并选择“事件”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-167">To view the events that have already been collected, use PerfView to open the .etl or .etl.zip file you created and choose **Events**.</span></span> <span data-ttu-id="2f4b2-168">ETW 将会收集有关大量事件的信息，包括来自其他进程的事件。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-168">ETW will have collected information about a large number of events, including events from other processes.</span></span> <span data-ttu-id="2f4b2-169">要专注于你的调查，完成以下事件视图中的文本框：</span><span class="sxs-lookup"><span data-stu-id="2f4b2-169">To focus your investigation, complete the following text boxes in the events view:</span></span>  
  
- <span data-ttu-id="2f4b2-170">在“进程筛选器”文本框中，指定应用名称（不要包含“.exe”）\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-170">In the **Process Filter** box, specify your app name (without ".exe").</span></span>  
  
- <span data-ttu-id="2f4b2-171">在“事件类型筛选器”框中，指定 `Process/Start | MyCompany-MyApp`\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-171">In the **Event Types Filter** box, specify `Process/Start | MyCompany-MyApp`.</span></span> <span data-ttu-id="2f4b2-172">这为来自 MyCompany-MyApp 的事件和“Windows 内核/进程/开始”事件设置了一个筛选器。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-172">This sets a filter for events from MyCompany-MyApp and the Windows Kernel/Process/Start event.</span></span>  
  
 <span data-ttu-id="2f4b2-173">选中左窗格中列出的所有事件 (Ctrl-A) 并选择“Enter”键\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-173">Select all the events listed in the left pane (Ctrl-A) and choose the **Enter** key.</span></span> <span data-ttu-id="2f4b2-174">现在你能够查看每个事件的时间戳了。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-174">Now, you should be able to see the timestamps from each event.</span></span> <span data-ttu-id="2f4b2-175">这些时间戳是从跟踪开始算起的，所以你必须用进程的开始时间减去每个事件的时间，才能确定启动花费的时间。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-175">These timestamps are relative to the start of the trace, so you have to subtract the time of each event from the start time of the process to identify the elapsed time since startup.</span></span> <span data-ttu-id="2f4b2-176">如果你使用“Ctrl+单击”选中了两个时间戳，你会在页面底部看到在状态栏中显示的他们之间的区别。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-176">If you use Ctrl+Click to select two timestamps, you'll see the difference between them displayed in the status bar at the bottom of the page.</span></span> <span data-ttu-id="2f4b2-177">这使得要在显示中查看任何两个事件之间的时间间隔变得简单（包括进程开始）。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-177">This makes it easy to see the elapsed time between any two events in the display (including process start).</span></span> <span data-ttu-id="2f4b2-178">你可以打开快捷菜单试图并在一些有用的选项中进行选择，比如导出到 CSV 文件或打开 Microsoft Excel 保存或处理这些数据。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-178">You can open the shortcut menu for the view and select from a number of useful options, like exporting to CSV files or opening Microsoft Excel to save or process the data.</span></span>  
  
 <span data-ttu-id="2f4b2-179">通过对原始应用和使用 .NET Native 工具链生成的版本重复此过程，可以比较性能差异。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-179">By repeating the procedure for both your original app and the version you built by using the .NET Native tool chain, you can compare the difference in performance.</span></span>   <span data-ttu-id="2f4b2-180">.NET Native 应用通常比 non-.NET 本机应用启动更快。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-180">.NET Native apps generally start faster than non-.NET Native apps.</span></span> <span data-ttu-id="2f4b2-181">如果你有兴趣更深入了解，PerfView 也可以识别你的应用代码中花费时间最多的部分。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-181">If you’re interested in digging deeper, PerfView can also identify the parts of your code that are taking the most time.</span></span> <span data-ttu-id="2f4b2-182">有关详细信息，请观看 [PerfView 教程](https://channel9.msdn.com/Series/PerfView-Tutorial)或读取 [Vance Morrison 的博客文章](/archive/blogs/vancem/publication-of-the-perfview-performance-analysis-tool)。</span><span class="sxs-lookup"><span data-stu-id="2f4b2-182">For more information, watch the [PerfView tutorials](https://channel9.msdn.com/Series/PerfView-Tutorial) or read [Vance Morrison’s blog entry](/archive/blogs/vancem/publication-of-the-perfview-performance-analysis-tool).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f4b2-183">请参阅</span><span class="sxs-lookup"><span data-stu-id="2f4b2-183">See also</span></span>

- <xref:System.Diagnostics.Tracing.EventSource>

---
title: 线程处理模型
description: 了解 Windows Presentation Foundation 应用程序中可能需要多个线程的情况。 首选单线程解决方案。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text on buttons [WPF], updating
- message processing [WPF], nested
- blocking operations [WPF]
- Common Language Runtime (CLR), locking mechanism
- locking mechanism of Common Language Runtime (CLR)
- threading model [WPF]
- Word [WPF], spelling checking
- button text [WPF], updating
- spelling checking in Word [WPF]
- asynchronous behavior [WPF], exposing
- nested message processing [WPF]
- reentrancy [WPF]
ms.assetid: 02d8fd00-8d7c-4604-874c-58e40786770b
ms.openlocfilehash: 9b67b6ea2896e9e6fec57dee8d1013d54fab03fc
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166375"
---
# <a name="threading-model"></a>线程处理模型
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 旨在帮助开发人员处理复杂的线程处理问题。 因此，大多数 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 开发人员无需编写使用多个线程的接口。 由于多线程程序既复杂又难以调试，因此当存在单线程解决方案时，应避免使用多线程程序。

 当然，无论架构的设计方式如何， [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 框架都无法为每种类型的问题提供单线程解决方案。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]接近，但在某些情况下，多个线程会提高 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 响应能力或应用程序性能。 基于上文所述的背景材料，本文对上述情况进行探讨，然后通过对一些低级别的细节进行讨论作出总结。

> [!NOTE]
> 本主题介绍了如何使用 <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> 异步调用方法进行线程处理。 还可以通过调用 <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> 方法（采用 <xref:System.Action> 或作为参数）进行异步调用 <xref:System.Func%601> 。  <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>方法返回 <xref:System.Windows.Threading.DispatcherOperation> 或 <xref:System.Windows.Threading.DispatcherOperation%601> ，它具有 <xref:System.Windows.Threading.DispatcherOperation.Task%2A> 属性。 可以将 `await` 关键字与或关联的结合使用 <xref:System.Windows.Threading.DispatcherOperation> <xref:System.Threading.Tasks.Task> 。 如果需要为 <xref:System.Threading.Tasks.Task> 或返回的返回同步 <xref:System.Windows.Threading.DispatcherOperation> <xref:System.Windows.Threading.DispatcherOperation%601> ，请调用 <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> 扩展方法。  调用 <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> 将导致死锁。 有关使用 <xref:System.Threading.Tasks.Task> 执行异步操作的详细信息，请参阅任务并行。  <xref:System.Windows.Threading.Dispatcher.Invoke%2A>方法还具有采用 <xref:System.Action> 或作为参数的重载 <xref:System.Func%601> 。  可以 <xref:System.Windows.Threading.Dispatcher.Invoke%2A> 通过传入委托或，使用方法进行同步调用 <xref:System.Action> <xref:System.Func%601> 。

<a name="threading_overview"></a>
## <a name="overview-and-the-dispatcher"></a>概述和调度程序
 通常， [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序从两个线程开始：一个用于处理渲染，另一个用于管理 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 。 当 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 线程接收输入、处理事件、绘制屏幕和运行应用程序代码时，呈现线程在后台有效地运行。 大多数应用程序使用单个 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 线程，尽管在某些情况下，最好使用多个线程。 我们将稍后通过示例对此进行讨论。

 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]线程在名为的对象内对工作项进行排队 <xref:System.Windows.Threading.Dispatcher> 。 <xref:System.Windows.Threading.Dispatcher> 基于优先级选择工作项，并运行每一个工作项直到完成。  每个 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 线程都必须至少有一个线程 <xref:System.Windows.Threading.Dispatcher> ，并且每个线程 <xref:System.Windows.Threading.Dispatcher> 只能在一个线程中执行工作项。

 构建响应能力强的用户应用程序的技巧是通过使工作项更小来最大限度地提高 <xref:System.Windows.Threading.Dispatcher> 吞吐量。 这样一来，在队列中等待处理的项永远不会过时 <xref:System.Windows.Threading.Dispatcher> 。 输入和响应间任何可察觉的延迟都会让用户不满。

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序应该如何处理大操作？ 如果代码涉及大型计算，或需要查询某些远程服务器上的数据库，应该怎么办？ 通常情况下，答案是在单独的线程中处理大操作，使线程可自由地用于 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 队列中的项 <xref:System.Windows.Threading.Dispatcher> 。 当大操作完成时，它可以将其结果报告回 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 线程以便显示。

 以前，Windows [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 只允许通过创建元素的线程访问元素。 这意味着，负责长时间运行任务的后台线程无法在任务完成时更新文本框。 Windows 这样做是为了确保组件的完整性 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 。 如果在绘制过程中后台线程更新了列表框的内容，则此列表框看起来可能会很奇怪。

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 具有内置互相排斥机制，此机制能强制执行这种协调。 中的大多数类都是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 从派生的 <xref:System.Windows.Threading.DispatcherObject> 。 构造时，将对 <xref:System.Windows.Threading.DispatcherObject> 链接的引用存储到 <xref:System.Windows.Threading.Dispatcher> 当前正在运行的线程。 实际上， <xref:System.Windows.Threading.DispatcherObject> 与创建它的线程关联。 在程序执行期间， <xref:System.Windows.Threading.DispatcherObject> 可以调用其公共 <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> 方法。 <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A>检查 <xref:System.Windows.Threading.Dispatcher> 与当前线程关联的，并将其与在 <xref:System.Windows.Threading.Dispatcher> 构造过程中存储的引用进行比较。 如果二者不匹配， <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> 将引发异常。 <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A>用于在属于的每个方法的开头调用 <xref:System.Windows.Threading.DispatcherObject> 。

 如果只有一个线程可以修改 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ，则后台线程如何与用户交互？ 后台线程可以要求 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 线程代表其执行操作。 它通过将工作项注册到线程的来实现此目的 <xref:System.Windows.Threading.Dispatcher> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 。 <xref:System.Windows.Threading.Dispatcher>类提供两种方法来注册工作项： <xref:System.Windows.Threading.Dispatcher.Invoke%2A> 和 <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> 。 这两种方法都计划一个用于执行的委托。 <xref:System.Windows.Threading.Dispatcher.Invoke%2A>是一个同步调用-即，它不会返回，直到 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 线程实际完成执行委托。 <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>是异步的，并且会立即返回。

 <xref:System.Windows.Threading.Dispatcher>按优先级对其队列中的元素进行排序。 向队列中添加元素时，可以指定10个级别 <xref:System.Windows.Threading.Dispatcher> 。 这些优先级在枚举中维护 <xref:System.Windows.Threading.DispatcherPriority> 。 <xref:System.Windows.Threading.DispatcherPriority>在 Windows SDK 文档中可以找到有关级别的详细信息。

<a name="samples"></a>
## <a name="threads-in-action-the-samples"></a>实际线程：示例

<a name="prime_number"></a>
### <a name="a-single-threaded-application-with-a-long-running-calculation"></a>具有长时间运行计算的单线程应用程序
 大多数图形用户界面（Gui）在等待为响应用户交互而生成的事件时，花费了大量时间空闲。 对此空闲时间进行仔细编程时，可以建设性地使用，而不会影响的响应能力 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]线程模型不允许输入中断线程中发生的操作 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 。 这意味着，你必须确保定期返回以 <xref:System.Windows.Threading.Dispatcher> 处理挂起输入事件，然后才能使其过时。

 请考虑以下示例：

 ![显示质数线程的屏幕截图。](./media/threading-model/threading-prime-numbers.png)

 这个简单的应用程序从 3 开始向上计数以搜索质数。 当用户单击 "**开始**" 按钮时，将开始搜索。 当程序查找到一个质数时，它将根据其发现内容更新用户界面。 用户可随时停止搜索。

 尽管十分简单，但对质数的搜索可以永远持续下去，这会带来一些问题。  如果在按钮的 click 事件处理程序中处理了整个搜索，则永远不会为线程分配 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 处理其他事件的机会。 将 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 无法响应输入或处理消息。 它将永远不会重绘，也永远不会响应按钮单击。

 可以在单独的线程中搜索质数，但这样的话，我们需要处理一些同步问题。 通过单线程方法，可以直接更新列出所找到的最大质数的标签。

 如果我们将计算任务分解为可管理的块，我们可以定期返回到 <xref:System.Windows.Threading.Dispatcher> 并处理事件。 我们可以给出重 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 绘和处理输入的机会。

 在计算与事件处理之间拆分处理时间的最佳方式是从管理计算 <xref:System.Windows.Threading.Dispatcher> 。 通过使用 <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> 方法，可以在从其绘制事件的同一队列中计划质数检查 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 。 在我们的示例中，一次仅计划一个质数检查。 完成质数检查后，立即计划下一个检查。 只有处理挂起事件之后，才会执行此检查 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 。

 ![显示调度程序队列的屏幕截图。](./media/threading-model/threading-dispatcher-queue.png)

 Microsoft Word 使用此机制完成拼写检查。 使用线程的空闲时间在后台完成拼写检查 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 。 我们来看一看代码。

 下列示例显示了创建用户界面的 XAML。

 [!code-xaml[ThreadingPrimeNumbers#ThreadingPrimeNumberXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml#threadingprimenumberxaml)]

 以下示例显示了代码隐藏。

 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumbercodebehind)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumbercodebehind)]

 下面的示例演示的事件处理程序 <xref:System.Windows.Controls.Button> 。

 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberstartorstop)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberstartorstop)]

 除了更新上的文本 <xref:System.Windows.Controls.Button> ，此处理程序负责通过将委托添加到队列来计划第一个质数检查 <xref:System.Windows.Threading.Dispatcher> 。 在此事件处理程序完成其工作后的某个时间， <xref:System.Windows.Threading.Dispatcher> 将选择此委托以便执行。

 如前文所述， <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> 是 <xref:System.Windows.Threading.Dispatcher> 用于计划委托执行的成员。 在此示例中，我们选择 <xref:System.Windows.Threading.DispatcherPriority.SystemIdle> 优先级。 <xref:System.Windows.Threading.Dispatcher>仅当没有要处理的重要事件时，才会执行此委托。 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 响应能力比数字检查更重要。 我们还传递了一个表示数字检查例程的新委托。

 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberchecknextnumber)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberchecknextnumber)]

 此方法检查下一个奇数是否是质数。 如果它是质数，则方法会直接更新 `bigPrime` <xref:System.Windows.Controls.TextBlock> 以反映它的发现。 可以如此操作的原因是，该计算发生在用于创建组件的相同线程中。 如果我们选择使用单独的线程进行计算，则必须使用更复杂的同步机制，并在线程中执行更新 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 。 我们将在下一步中演示这种情况。

 有关此示例的完整源代码，请参阅[具有长时间运行计算的单线程应用程序示例](https://github.com/Microsoft/WPF-Samples/tree/master/Threading/SingleThreadedApplication)

<a name="weather_sim"></a>
### <a name="handling-a-blocking-operation-with-a-background-thread"></a>使用后台线程处理阻塞操作
 在图形应用程序中处理阻塞操作可能很困难。 我们不希望从事件处理程序调用阻塞方法，因为应用程序可能看上去冻结。 我们可以使用单独的线程来处理这些操作，但完成此操作后，必须与线程同步， [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 因为我们无法从我们的工作线程直接修改 GUI。 我们可以使用 <xref:System.Windows.Threading.Dispatcher.Invoke%2A> 或 <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> 将委托插入到 <xref:System.Windows.Threading.Dispatcher> 线程的中 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 。 最终，将执行这些委托并带有修改元素的权限 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 。

 在本例中，我们模拟了一个检索天气预报的远程过程调用。 我们使用单独的工作线程执行此调用，并在完成时在线程的中计划更新方法 <xref:System.Windows.Threading.Dispatcher> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 。

 ![显示天气 UI 的屏幕截图。](./media/threading-model/threading-weather-ui.png)

 [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweathercodebehind)]
 [!code-vb[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweathercodebehind)]

 以下是一些需要注意的详细信息。

- 创建按钮处理程序

     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherbuttonhandler)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherbuttonhandler)]

 单击按钮时，会显示时钟绘图并开始对其进行动画处理。 禁用该按钮。 我们 `FetchWeatherFromServer` 在新线程中调用方法，然后返回，允许在 <xref:System.Windows.Threading.Dispatcher> 我们等待收集天气预报时处理事件。

- 获取天气

     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherfetchweather)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherfetchweather)]

 为简便起见，本例中没有任何网络代码。 通过使新线程进入休眠状态四秒钟，模拟网络访问的延迟。 此时，原始 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 线程仍在运行并响应事件。 为了对此进行演示，我们让动画保持运行状态，最小化和最大化按钮也继续工作。

 当延迟结束，并且我们随机选择了天气预报后，就可以向下报告回来了 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 。 为此，我们需要 `UpdateUserInterface` 使用线程的在线程中计划对的调用 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Threading.Dispatcher> 。 将描述天气的字符串传递给此计划方法调用。

- 更新[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]

     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherupdateui)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherupdateui)]

 当 <xref:System.Windows.Threading.Dispatcher> 线程中的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 具有时间时，它将执行对的计划调用 `UpdateUserInterface` 。 此方法停止时钟动画，并选择一张映像用于描述天气。 它将显示此映像，并还原“获取预报”按钮。

<a name="multi_browser"></a>
### <a name="multiple-windows-multiple-threads"></a>多窗口、多线程
 某些 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序需要多个顶级窗口。 一个线程/ <xref:System.Windows.Threading.Dispatcher> 组合可用于管理多个窗口是完全可接受的，但有时多个线程会执行更好的作业。 尤其当这些窗口中的某一个将有可能要独占线程时，更是如此。

 Windows 资源管理器以这种方式工作。 每个新资源管理器窗口都属于原始进程，但它是在独立线程的控件下创建的。

 使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Frame> 控件，可以显示网页。 我们可以轻松创建简单的 Internet Explorer 替换。 让我们从一个重要功能开始：打开新资源管理器窗口的能力。 当用户单击“新建窗口”按钮时，我们将在单独的线程中启动窗口的副本。 这样一来，在其中一个窗口中的长时间运行或阻塞操作将不会锁定其他窗口。

 在实际情况下，Web 浏览器模型自身拥有复杂的线程模型。 由于大多数读者都熟悉它，所以我们选择它。

 以下示例显示了代码。

 [!code-xaml[ThreadingMultipleBrowsers#ThreadingMultiBrowserXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml#threadingmultibrowserxaml)]

 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsercodebehind)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsercodebehind)]

 此代码中的以下线程段对我们来说是最有趣的：

 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsernewwindow)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsernewwindow)]

 当单击“新建窗口”按钮时，将调用该方法。 它创建了一个新线程，并以异步方式启动。

 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowserthreadstart)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowserthreadstart)]

 此方法是新线程的起点。 我们在此线程的控件下创建了一个新窗口。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]自动创建新的 <xref:System.Windows.Threading.Dispatcher> 以管理新线程。 为了使窗口正常运行，我们需要做的就是启动 <xref:System.Windows.Threading.Dispatcher> 。

<a name="stumbling_points"></a>
## <a name="technical-details-and-stumbling-points"></a>技术详细信息和疑难点

### <a name="writing-components-using-threading"></a>使用线程处理编写组件
 Microsoft .NET Framework 开发人员指南介绍了组件如何向其客户端公开异步行为的模式（请参阅[基于事件的异步模式概述](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)）。 例如，假设我们想要将方法打包 `FetchWeatherFromServer` 到可重用的非图形组件。 按照标准 Microsoft .NET 框架模式，这会如下所示。

 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent1)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent1)]

 `GetWeatherAsync` 将使用上述的技术之一（如创建后台线程）来以异步方式工作，而非阻止调用线程。

 此模式中最重要的部分之一是*MethodName* `Completed` 在调用方法*名称*方法的同一线程上调用方法1， `Async` 以开始。 你可以 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 通过存储来轻松地执行此操作， <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A> 但之后，非图形组件只能在应用程序中使用，而不能在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Windows 窗体或 ASP.NET 程序中使用。

 <xref:System.Windows.Threading.DispatcherSynchronizationContext>类可满足这一需要，将其视为 <xref:System.Windows.Threading.Dispatcher> 与其他框架一起工作的简化版本 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 。

 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent2)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent2)]

### <a name="nested-pumping"></a>嵌套泵
 有时完全锁定线程是不可行的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 。 让我们考虑一下 <xref:System.Windows.MessageBox.Show%2A> 类的方法 <xref:System.Windows.MessageBox> 。 <xref:System.Windows.MessageBox.Show%2A>用户单击 "确定" 按钮后，才会返回。 但是，它却会创建一个窗口，该窗口为了获得交互性而必须具有消息循环。 在等待用户单击“确定”时，原始应用程序窗口将不会响应用户的输入。 但是，它将继续处理绘制消息。 当被覆盖和被显示时，原始窗口将重绘其本身。

 ![显示带有 "确定" 按钮的消息的屏幕截图](./media/threading-model/threading-message-loop.png)

 一些线程必须负责消息框窗口。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可以为消息框窗口创建新线程，但此线程无法在原始窗口中绘制禁用的元素（请回忆之前所讨论的互相排斥）。 相反， [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用嵌套消息处理系统。 <xref:System.Windows.Threading.Dispatcher>类包含名为的特殊方法 <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> ，该方法存储应用程序的当前执行点，然后开始新的消息循环。 当嵌套消息循环完成时，执行将在原始调用后恢复 <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> 。

 在这种情况下， <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> 会在调用时维护程序上下文 <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> ，并启动一个新的消息循环，以重新绘制背景窗口，并处理消息框窗口中的输入。 当用户单击 "确定" 并清除弹出窗口时，嵌套循环将退出，并在调用后恢复控件 <xref:System.Windows.MessageBox.Show%2A> 。

### <a name="stale-routed-events"></a>过时的路由事件
 引发事件时，中的路由事件系统会 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 通知整个树。

 [!code-xaml[InputOvw#ThreadingArticleStaticRoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#threadingarticlestaticroutedevent)]

 当在椭圆上按下鼠标左键时， `handler2` 将执行。 `handler2`完成后，会将事件传递给 <xref:System.Windows.Controls.Canvas> 对象，后者使用 `handler1` 来处理该事件。 仅当 `handler2` 未将事件对象显式标记为已处理时，才会发生这种情况。

 可能 `handler2` 需要大量时间来处理此事件。 `handler2`可能使用 <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> 来开始一个嵌套消息循环，该循环在数小时内不会返回。 如果 `handler2` 在此消息循环完成时未将事件标记为已处理，则该事件将在树中向上传递，即使它非常旧。

### <a name="reentrancy-and-locking"></a>重新进入和锁定
 公共语言运行时（CLR）的锁定机制的行为与可能不完全相同;请求锁时，可能会希望线程完全停止操作。 实际上，该线程将继续接收和处理高优先级的消息。 这样有助于防止死锁，并使接口最低限度地响应，但这样做有可能引入细微 bug。  大多数情况下，您不需要了解有关此操作的任何信息，但在极少数情况下（通常涉及 Win32 窗口消息或 COM STA 组件），这一点很有价值。

 大多数接口都不是以线程安全为基础生成的，因为开发人员可以假定 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 永远不会由多个线程访问。 在这种情况下，单个线程可能会在意外的时间发生环境更改，从而导致这类错误的影响，从而导致 <xref:System.Windows.Threading.DispatcherObject> 互斥机制能够解决。 请看下面的伪代码：

 ![显示线程重入的关系图。](./media/threading-model/threading-reentrancy.png "ThreadingReentrancy")

 大多数情况下都是正确的，但有时 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 这种意外重入可能会导致问题。 因此，在某些关键情况下 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ， <xref:System.Windows.Threading.Dispatcher.DisableProcessing%2A> 会调用，这将更改该线程的锁定指令以使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 无提示锁定，而不是使用常用的 CLR 锁。

 那么为什么 CLR 团队选择此行为呢？ 它与 COM STA 对象和完成线程有关。 当对对象进行垃圾回收时，它的 `Finalize` 方法将在专用终结器线程上运行，而不是在线程上运行 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 。 其中存在问题，因为在线程上创建的 COM STA 对象 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 只能在线程上释放 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 。 CLR 执行的等效操作 <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> （在这种情况下，使用 win32 `SendMessage` ）。 但如果 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 线程繁忙，则终结器线程将停止，并且无法释放 COM STA 对象，这将导致严重的内存泄漏。 因此，CLR 团队做出了很难的调用，使锁按照它们的工作方式工作。

 的任务 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 是在不重新引入内存泄漏的情况下避免意外的重入，这就是我们不会在任何地方阻止重入的原因。

## <a name="see-also"></a>另请参阅

- [具有长时间运行计算的单线程应用程序示例](https://github.com/Microsoft/WPF-Samples/tree/master/Threading/SingleThreadedApplication)

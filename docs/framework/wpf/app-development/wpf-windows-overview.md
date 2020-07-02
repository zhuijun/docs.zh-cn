---
title: Windows 概述
description: 熟悉在 Windows Presentation Foundation （WPF）中创建和管理独立应用程序的 windows 的基本知识。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XAML [WPF], displaying content via
- XAML pages [WPF], displaying
- content [WPF], displaying via XAML
- window objects [WPF]
- hosting [WPF], applications
- managing windows [WPF]
- dialog boxes [WPF]
- Page object [WPF]
- NavigationWindow objects [WPF]
- applications [WPF], hosting
- content [WPF], displaying
- events [WPF]
- content [WPF], displaying via procedural code
- modal windows [WPF]
- procedural code [WPF], displaying content via
- displaying content via procedural code [WPF]
- window management [WPF]
- displaying content [WPF]
- window events [WPF]
- windows [WPF]
- modal dialog boxes [WPF]
- displaying XAML pages [WPF]
ms.assetid: 737d04ec-8861-46c3-8d44-fa11d3528d23
ms.openlocfilehash: e1ad3c118fbaea8f1e23d012721f0cf3c2c50015
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622882"
---
# <a name="wpf-windows-overview"></a>WPF Windows 概述
用户通过 Windows 与 Windows Presentation Foundation （WPF）独立应用程序交互。 窗口的主要用途是托管使数据可视化并使用户能够与数据交互的内容。 独立 WPF 应用程序使用类提供自己的窗口 <xref:System.Windows.Window> 。 本主题将介绍在 <xref:System.Windows.Window> 独立的应用程序中创建和管理 windows 的基本原理。  
  
> [!NOTE]
> 浏览器承载的 WPF 应用程序（包括 XAML 浏览器应用程序（Xbap）和松散 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 页面）不提供其自己的窗口。 而是托管在 Windows Internet Explorer 提供的 windows 中。 请参阅[WPF XAML 浏览器应用程序概述](wpf-xaml-browser-applications-overview.md)。  

<a name="TheWindowClass"></a>
## <a name="the-window-class"></a>窗口类  
 下图说明了窗口的组成部分：  
  
 ![显示窗口元素的屏幕截图。](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 窗口分为两个区域：非工作区和工作区。  
  
 窗口的*非工作区*是由 WPF 实现的，包括大多数窗口所共有的窗口部分，其中包括：  
  
- 边框。  
  
- 标题栏。  
  
- 图标。  
  
- “最小化”、“最大化”和“还原”按钮。  
  
- “关闭”按钮。  
  
- “系统”菜单，其中包含允许用户最小化、最大化、还原、移动和关闭窗口以及重设窗口大小的菜单项。  
  
 窗口的*工作区*是窗口非工作区内的区域，开发人员使用它来添加特定于应用程序的内容，例如菜单栏、工具栏和控件。  
  
 在 WPF 中，窗口由 <xref:System.Windows.Window> 用于执行以下操作的类进行封装：  
  
- 显示窗口。  
  
- 配置窗口的大小、位置和外观。  
  
- 托管特定于应用程序的内容。  
  
- 管理窗口的生存期。  
  
<a name="DefiningAWindow"></a>
## <a name="implementing-a-window"></a>实现窗口  
 典型窗口的实现同时包含外观和行为，其中*外观*定义了窗口对用户和*行为*的外观，定义了窗口与用户交互的方式。 在 WPF 中，可以使用代码或标记实现窗口的外观和行为 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 。  
  
 但一般情况下，窗口的外观是使用标记实现的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，其行为是使用代码隐藏实现的，如下面的示例中所示。  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 若要使 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 标记文件和代码隐藏文件协同工作，需要满足以下要求：  
  
- 在标记中， `Window` 元素必须包含 `x:Class` 属性。 生成应用程序后， `x:Class` 标记文件中存在会导致 Microsoft 生成引擎（MSBuild）创建一个 `partial` 派生自的类， <xref:System.Windows.Window> 并具有由特性指定的名称 `x:Class` 。 这要求为架构（）添加 XML 命名空间声明 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` 。 生成的 `partial` 类实现 `InitializeComponent` 方法，该方法用于注册事件并设置标记中实现的属性。  
  
- 在代码隐藏中，类必须是 `partial` 由标记中的特性指定的同名类 `x:Class` ，并且必须派生自 <xref:System.Windows.Window> 。 这允许在生成应用程序时将代码隐藏文件与为 `partial` 标记文件生成的类相关联（请参阅[生成 WPF 应用程序](building-a-wpf-application-wpf.md)）。  
  
- 在代码隐藏中， <xref:System.Windows.Window> 该类必须实现调用方法的构造函数 `InitializeComponent` 。 `InitializeComponent`由标记文件的生成类实现， `partial` 用于注册事件和设置在标记中定义的属性。  
  
> [!NOTE]
> <xref:System.Windows.Window>使用 Visual Studio 向项目添加新的时，将 <xref:System.Windows.Window> 使用标记和代码隐藏来实现，并包括必要的配置以创建标记和代码隐藏文件之间的关联，如此处所述。  
  
 通过此配置，你可以专注于定义标记中窗口的外观 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 并在代码隐藏中实现其行为。 下面的示例演示了一个窗口，其中包含一个按钮，在标记中实现 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 并在 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 代码隐藏中实现了该按钮事件的事件处理程序。  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>
## <a name="configuring-a-window-definition-for-msbuild"></a>为 MSBuild 配置窗口定义  
 如何实现窗口将决定如何为 MSBuild 配置它。 对于使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 标记和代码隐藏定义的窗口：  
  
- XAML 标记文件配置为 MSBuild `Page` 项。  
  
- 代码隐藏文件配置为 MSBuild `Compile` 项。  
  
 下面的 MSBuild 项目文件中显示了这种情况。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 有关生成 WPF 应用程序的信息，请参阅[生成 Wpf 应用程序](building-a-wpf-application-wpf.md)。  
  
<a name="WindowLifetime"></a>
## <a name="window-lifetime"></a>窗口生存期  
 与所有类一样，窗口也有生存期，开始于首次实例化窗口，在这之后将打开、激活、停用直至最终关闭窗口。  

<a name="Opening_a_Window"></a>
### <a name="opening-a-window"></a>打开窗口  
 若要打开窗口，首先要创建窗口实例，下面的示例演示此操作。  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 在此示例中，在 `MarkupAndCodeBehindWindow` 应用程序启动时实例化，这会在 <xref:System.Windows.Application.Startup> 引发事件时发生。  
  
 在实例化窗口时，对它的引用会自动添加到由该对象管理的窗口的列表中 <xref:System.Windows.Application> （请参见 <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType> ）。 此外，默认情况下，第一个要实例化的窗口是由设置 <xref:System.Windows.Application> 为主应用程序窗口（请参阅 <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType> ）。  
  
 最后，通过调用方法打开该窗口 <xref:System.Windows.Window.Show%2A> ; 结果如下图所示。  
  
 ![通过调用窗口打开的窗口。显示](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 通过调用打开的窗口 <xref:System.Windows.Window.Show%2A> 是一个无模式窗口，这意味着应用程序以允许用户在同一应用程序中激活其他窗口的模式操作。  
  
> [!NOTE]
> <xref:System.Windows.Window.ShowDialog%2A>调用以模式打开 windows，如对话框。 有关详细信息，请参阅[对话框概述](dialog-boxes-overview.md)。  
  
 <xref:System.Windows.Window.Show%2A>调用时，窗口将执行初始化工作，并显示该工作以建立允许它接收用户输入的基础结构。 初始化窗口时，将 <xref:System.Windows.Window.SourceInitialized> 引发事件，并显示窗口。  
  
 作为快捷方式， <xref:System.Windows.Application.StartupUri%2A> 可以将设置为指定应用程序启动时自动打开的第一个窗口。  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 当应用程序启动时，的值所指定的窗口 <xref:System.Windows.Application.StartupUri%2A> 将在 modelessly 中打开。通过调用其方法，打开窗口 <xref:System.Windows.Window.Show%2A> 。  
  
<a name="Ownership"></a>
#### <a name="window-ownership"></a>窗口所有权  
 使用方法打开的窗口 <xref:System.Windows.Window.Show%2A> 与创建它的窗口不具有隐式关系; 用户可以与任何一个窗口独立交互，这意味着，这两个窗口都可以执行以下操作：  
  
- 覆盖其他（除非其中一个 windows 的 <xref:System.Windows.Window.Topmost%2A> 属性设置为 `true` ）。  
  
- 在不影响另一个窗口的情况下最小化、最大化和还原。  
  
 某些窗口要求与打开它们的窗口保持某种关系。 例如，集成开发环境（IDE）应用程序可以打开属性窗口和工具窗口，其典型行为是涵盖创建它们的窗口。 此外，此类窗口应始终与创建它们的窗口一起关闭、最小化、最大化和还原。 这种关系可通过使*一个窗口成为*一个窗口而建立，通过设置 <xref:System.Windows.Window.Owner%2A> 拥有的*窗口*的属性和对*所有者窗口*的引用来实现。 这在下面的示例中显示。  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 建立所有权后：  
  
- 拥有的窗口可以通过检查其属性的值引用其所有者窗口 <xref:System.Windows.Window.Owner%2A> 。  
  
- 所有者窗口可以通过检查其属性的值来发现其拥有的所有窗口 <xref:System.Windows.Window.OwnedWindows%2A> 。  
  
<a name="Preventing"></a>
#### <a name="preventing-window-activation"></a>防止窗口激活  
 在某些情况下，windows 不应在显示时激活，如 Internet messenger 样式应用程序的对话窗口或电子邮件应用程序的通知窗口。  
  
 如果你的应用程序具有在显示时不应激活的窗口，则可在 <xref:System.Windows.Window.ShowActivated%2A> `false` <xref:System.Windows.Window.Show%2A> 第一次调用方法之前，将其属性设置为。 结果是：  
  
- 不会激活窗口。  
  
- <xref:System.Windows.Window.Activated>不引发窗口的事件。  
  
- 当前激活的窗口保持激活状态。  
  
 但是，只要用户通过单击工作区或非工作区激活了窗口，窗口就会变为激活状态。 在这种情况下：  
  
- 已激活窗口。  
  
- 引发窗口的 <xref:System.Windows.Window.Activated> 事件。  
  
- 停用之前激活的窗口。  
  
- <xref:System.Windows.Window.Deactivated> <xref:System.Windows.Window.Activated> 随后会按预期方式引发窗口和事件以响应用户操作。  
  
<a name="Window_Activation"></a>
### <a name="window-activation"></a>窗口激活  
 第一次打开窗口时，它将成为活动窗口（除非显示时显示 " <xref:System.Windows.Window.ShowActivated%2A> 设置为" `false` ）。 *活动窗口*是当前正在捕获用户输入的窗口，例如键击和鼠标单击。 当窗口处于活动状态时，它会引发 <xref:System.Windows.Window.Activated> 事件。  
  
> [!NOTE]
> 首次打开窗口时，仅在 <xref:System.Windows.FrameworkElement.Loaded> <xref:System.Windows.Window.ContentRendered> 引发事件后引发和事件 <xref:System.Windows.Window.Activated> 。 考虑到这一点，当引发时，可以有效地将窗口视为 <xref:System.Windows.Window.ContentRendered> 已打开。  
  
 某个窗口成为活动窗口后，用户可以在同一应用程序内激活其他窗口，或者激活其他应用程序。 发生这种情况时，将停用当前处于活动状态的窗口，并引发 <xref:System.Windows.Window.Deactivated> 事件。 同样，当用户选择当前已停用的窗口时，该窗口将再次变为活动状态并 <xref:System.Windows.Window.Activated> 引发。  
  
 处理和的一个常见 <xref:System.Windows.Window.Activated> 原因 <xref:System.Windows.Window.Deactivated> 是启用和禁用只能在窗口处于活动状态时运行的功能。 例如，一些窗口显示需要用户持续输入或关注的交互式内容，这些内容包括游戏和视频播放器。 下面的示例是一个简化的视频播放器，演示如何处理 <xref:System.Windows.Window.Activated> 和 <xref:System.Windows.Window.Deactivated> 实现此行为。  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 停用某个窗口后，其他类型的应用程序可能仍会在后台运行代码。 例如，在用户使用其他应用程序时，邮件客户端可能会继续轮询邮件服务器。 类似的应用程序在主窗口停用时，通常将提供不同或其他的行为。 对于邮件程序，这可能意味着将新邮件项添加到收件箱和将通知图标添加到系统任务栏。 仅当邮件窗口不处于活动状态时才显示通知图标，可以通过检查属性来确定 <xref:System.Windows.Window.IsActive%2A> 。  
  
 如果后台任务已完成，则窗口可能需要通过调用方法更紧急地通知用户 <xref:System.Windows.Window.Activate%2A> 。 如果用户与调用时激活的其他应用程序交互 <xref:System.Windows.Window.Activate%2A> ，则窗口的任务栏按钮会闪烁。 如果用户与当前应用程序交互，则调用 <xref:System.Windows.Window.Activate%2A> 会将窗口置于前台。  
  
> [!NOTE]
> 您可以使用和事件处理应用程序范围的激活 <xref:System.Windows.Application.Activated?displayProperty=nameWithType> <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> 。  
  
<a name="Closing_a_Window"></a>
### <a name="closing-a-window"></a>关闭窗口  
 窗口的生存期在用户关闭它时终止。 可以使用非工作区中的元素关闭窗口，这些元素包括：  
  
- **系统**菜单的**关闭**项。  
  
- 按 ALT+F4。  
  
- 按 "**关闭**" 按钮。  
  
 可以向工作区提供其他关闭窗口的机制，较为常见的机制包括：  
  
- "**文件**" 菜单中的 "**退出**" 项，通常用于主应用程序窗口。  
  
- "**文件**" 菜单中的 "**关闭**" 项，通常在辅助应用程序窗口中。  
  
- "**取消**" 按钮，通常位于模式对话框中。  
  
- "**关闭**" 按钮，通常位于无模式对话框中。  
  
 若要关闭窗口以响应其中一种自定义机制，需要调用 <xref:System.Windows.Window.Close%2A> 方法。 下面的示例通过选择 "**文件**" 菜单上的 "**退出**" 来实现关闭窗口的功能。  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 当窗口关闭时，它将引发两个事件： <xref:System.Windows.Window.Closing> 和 <xref:System.Windows.Window.Closed> 。  
  
 <xref:System.Windows.Window.Closing>在窗口关闭前引发，并提供一种机制，可通过该机制阻止窗口关闭。 阻止窗口关闭的一个常见原因是窗口内容包含修改的数据。 在这种情况下， <xref:System.Windows.Window.Closing> 可以处理事件以确定数据是否处于脏状态，如果是，则要求用户是否继续关闭窗口而不保存数据或取消关闭窗口。 下面的示例演示了处理的关键方面 <xref:System.Windows.Window.Closing> 。  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 <xref:System.Windows.Window.Closing>向事件处理程序传递，该事件处理程序 <xref:System.ComponentModel.CancelEventArgs> 实现了 `Boolean` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> 设置为的属性， `true` 以防止窗口关闭。  
  
 如果 <xref:System.Windows.Window.Closing> 未处理，或者处理但未取消，则窗口将关闭。 在窗口实际关闭之前， <xref:System.Windows.Window.Closed> 将引发。 此时，无法阻止窗口关闭。  
  
> [!NOTE]
> 在主应用程序窗口关闭（请参阅 <xref:System.Windows.Application.MainWindow%2A> ）或最后一个窗口关闭时，可以将应用程序配置为自动关闭。 有关详细信息，请参阅<xref:System.Windows.Application.ShutdownMode%2A>。  
  
 尽管可以通过非客户端和客户端区域中提供的机制显式关闭窗口，但也可以通过应用程序或窗口的其他部分中的行为来隐式关闭窗口，其中包括：  
  
- 用户注销或关闭 Windows。  
  
- 窗口的所有者将关闭（请参阅 <xref:System.Windows.Window.Owner%2A> ）。  
  
- 主应用程序窗口已关闭，并且 <xref:System.Windows.Application.ShutdownMode%2A> 为 <xref:System.Windows.ShutdownMode.OnMainWindowClose> 。  
  
- 调用 <xref:System.Windows.Application.Shutdown%2A>。  
  
> [!NOTE]
> 窗口在关闭后无法重新打开。  
  
<a name="Window_Lifetime_Events"></a>
### <a name="window-lifetime-events"></a>窗口生存期事件  
 下图显示了窗口生存期内的主体事件的顺序：  
  
 ![在窗口生存期内显示事件的关系图。](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 下图显示了在未激活的情况下显示的窗口生存期内的主体事件的顺序（在 <xref:System.Windows.Window.ShowActivated%2A> `false` 显示窗口之前设置为）：  
  
 ![在不激活的情况下显示窗口生存期内的事件的关系图。](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>
## <a name="window-location"></a>窗口位置  
 当窗口打开时，它在相对于桌面的 x 和 y 维度中有一个位置。 可以通过分别检查和属性来确定此位置 <xref:System.Windows.Window.Left%2A> <xref:System.Windows.Window.Top%2A> 。 设置这些属性可以更改窗口的位置。  
  
 你还可以 <xref:System.Windows.Window> 通过 <xref:System.Windows.Window.WindowStartupLocation%2A> 使用以下枚举值之一设置属性，来指定第一次出现的起始位置 <xref:System.Windows.WindowStartupLocation> ：  
  
- <xref:System.Windows.WindowStartupLocation.CenterOwner>（默认值）  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 如果将启动位置指定为 <xref:System.Windows.WindowStartupLocation.Manual> ，并且 <xref:System.Windows.Window.Left%2A> <xref:System.Windows.Window.Top%2A> 未设置和属性， <xref:System.Windows.Window> 将要求 Windows 提供要显示在中的位置。  
  
<a name="Topmost_Windows_and_Z_Order"></a>
### <a name="topmost-windows-and-z-order"></a>最顶层窗口和 Z 顺序  
 除了有 x 和 y 位置外，窗口还在 z 维度中有一个位置，该位置确定窗口相对于其他窗口的垂直位置。 它称为窗口的 z 顺序，并且有两种类型：正常 z 顺序和最顶层 z 顺序。 处于*正常 z 顺序*中的窗口的位置取决于它当前是否处于活动状态。 默认情况下，窗口位于正常 z 顺序中。 *最顶层 z 顺序*中的窗口位置也取决于它当前是否处于活动状态。 此外，最顶层 z 顺序中的窗口始终位于正常 z 顺序中的窗口之上。 窗口通过将其属性设置为，位于最顶层 z 顺序中 <xref:System.Windows.Window.Topmost%2A> `true` 。  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 在每个 z 顺序中，当前的活动窗口显示在同一 z 顺序中所有其他窗口之上。  
  
<a name="WindowSize"></a>
## <a name="window-size"></a>窗口大小  
 除了拥有桌面位置，窗口的大小由多个属性确定，其中包括各种宽度和高度属性以及 <xref:System.Windows.Window.SizeToContent%2A> 。  
  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>、 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.MaxWidth%2A> 用于管理窗口在其生存期内可以具有的宽度范围，并按以下示例所示进行配置。  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 窗口高度由 <xref:System.Windows.FrameworkElement.MinHeight%2A> 、 <xref:System.Windows.FrameworkElement.Height%2A> 、和进行管理， <xref:System.Windows.FrameworkElement.MaxHeight%2A> 如以下示例中所示。  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 由于各种宽度值和高度值各自指定了一个范围，所以大小可调整大小的窗口的宽度和高度可以是相应维度中指定范围内的任何值。 若要检测其当前的宽度和高度，请 <xref:System.Windows.FrameworkElement.ActualWidth%2A> 分别检查和 <xref:System.Windows.FrameworkElement.ActualHeight%2A> 。  
  
 如果希望窗口的宽度和高度与窗口内容的大小相符，则可以使用 <xref:System.Windows.Window.SizeToContent%2A> 属性，该属性具有以下各值：  
  
- <xref:System.Windows.SizeToContent.Manual>. 不起作用（默认值）。  
  
- <xref:System.Windows.SizeToContent.Width>. 适应内容宽度，其效果与将 <xref:System.Windows.FrameworkElement.MinWidth%2A> 和设置 <xref:System.Windows.FrameworkElement.MaxWidth%2A> 为内容的宽度相同。  
  
- <xref:System.Windows.SizeToContent.Height>. 适应内容高度，其效果与将 <xref:System.Windows.FrameworkElement.MinHeight%2A> 和设置 <xref:System.Windows.FrameworkElement.MaxHeight%2A> 为内容的高度相同。  
  
- <xref:System.Windows.SizeToContent.WidthAndHeight>. 适应内容宽度和高度，其效果与将 <xref:System.Windows.FrameworkElement.MinHeight%2A> 和设置 <xref:System.Windows.FrameworkElement.MaxHeight%2A> 为内容的高度相同，同时将 <xref:System.Windows.FrameworkElement.MinWidth%2A> 和设置 <xref:System.Windows.FrameworkElement.MaxWidth%2A> 为内容的宽度。  
  
 以下示例显示了一个窗口，它在第一次显示时即自动调整垂直方向和水平方向上的大小以适应内容。  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 下面的示例演示如何 <xref:System.Windows.Window.SizeToContent%2A> 在代码中设置属性，以指定如何调整窗口大小以适应其内容。
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>
## <a name="order-of-precedence-for-sizing-properties"></a>大小调整属性的优先级顺序  
 从根本上说，窗口的各种大小属性可以结合使用，以定义可调整大小的窗口的宽度和高度范围。 若要确保保持有效的范围，请 <xref:System.Windows.Window> 使用以下优先级顺序计算大小属性的值。  
  
 **对于高度属性：**  
  
1. <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 **对于宽度属性：**  
  
1. <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 优先级顺序还可以确定窗口最大化时的窗口大小，该大小是使用属性管理的 <xref:System.Windows.Window.WindowState%2A> 。  
  
<a name="WindowState"></a>
## <a name="window-state"></a>窗口状态  
 可调整大小的窗口在生存期中拥有三种状态：正常、最小化和最大化。 处于*正常*状态的窗口是窗口的默认状态。 这种状态下的窗口允许用户使用重设大小手柄或边框移动窗口和重设其大小（前提是大小可以重设）。  
  
 如果设置为，则具有*最小化*状态的窗口将折叠到其任务栏按钮 <xref:System.Windows.Window.ShowInTaskbar%2A> `true` ; 否则，它将折叠为可能的最小大小，并将自身重定位到桌面左下角。 虽然不在任务栏显示的最小化窗口可以在桌面上四处拖动，但这两种类型的最小化窗口都不可以使用边框或重设大小手柄重设窗口大小。  
  
 处于最*大化*状态的窗口将扩展为它的最大大小，这将只是其 <xref:System.Windows.FrameworkElement.MaxWidth%2A> 、 <xref:System.Windows.FrameworkElement.MaxHeight%2A> 和属性所规定的大小 <xref:System.Windows.Window.SizeToContent%2A> 。 与最小化窗口一样，最大化窗口无法使用重设大小手柄或通过拖动边框来重设大小。  
  
> [!NOTE]
> <xref:System.Windows.Window.Top%2A> <xref:System.Windows.Window.Left%2A> <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> 即使窗口当前已最大化或最小化，窗口的、、和属性的值也始终表示正常状态的值。  
  
 窗口的状态可以通过设置其属性来配置 <xref:System.Windows.Window.WindowState%2A> ，该属性可以具有以下 <xref:System.Windows.WindowState> 枚举值之一：  
  
- <xref:System.Windows.WindowState.Normal>（默认值）  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 以下示例显示如何创建在打开时最大化显示的窗口。  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 通常，应将设置 <xref:System.Windows.Window.WindowState%2A> 为配置窗口的初始状态。 显示可调整大小的窗口后，用户可以按窗口标题栏上的“最小化”、“最大化”和“还原”按钮来更改窗口状态。  
  
<a name="WindowAppearance"></a>
## <a name="window-appearance"></a>窗口外观  
 通过将特定于窗口的内容（例如按钮、标签和文本框）添加到窗口的工作区可以更改它的外观。 若要配置非工作区， <xref:System.Windows.Window> 提供了几个属性，其中包括 <xref:System.Windows.Window.Icon%2A> 设置窗口图标以及 <xref:System.Windows.Window.Title%2A> 设置其标题。  
  
 还可以通过配置窗口的重设大小模式、窗口样式，以及窗口是否显示为桌面任务栏中的按钮，更改非工作区边框的外观和行为。  

<a name="Resize_Mode"></a>
### <a name="resize-mode"></a>重设大小模式  
 根据 <xref:System.Windows.Window.WindowStyle%2A> 属性，您可以控制用户如何（以及用户）如何调整窗口的大小。 窗口样式的选择会影响用户是否可以通过使用鼠标拖动边框来调整窗口的大小，无论是否在非工作区显示 "**最小化**"、"**最大化**" 和 "**调整大小**" 按钮，以及它们是否已启用。  
  
 您可以通过设置窗口的属性来配置窗口调整大小的方式 <xref:System.Windows.Window.ResizeMode%2A> ，可以是下列 <xref:System.Windows.ResizeMode> 枚举值之一：  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <xref:System.Windows.ResizeMode.CanResize>（默认值）  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 与一样 <xref:System.Windows.Window.WindowStyle%2A> ，窗口的重设大小模式不太可能在其生存期内发生更改，这意味着你很可能会从标记中进行设置 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 。  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 请注意，可以通过检查属性来检测窗口是最大化、最小化还是已还原 <xref:System.Windows.Window.WindowState%2A> 。  
  
<a name="Window_Style"></a>
### <a name="window-style"></a>窗口样式  
 从窗口非工作区公开的边框适用于大多数应用程序。 但是，有时候会需要不同类型的边框，或者根本不需要边框，具体取决于窗口类型。  
  
 若要控制窗口的边框类型，请将其属性设置 <xref:System.Windows.Window.WindowStyle%2A> 为以下枚举值之一 <xref:System.Windows.WindowStyle> ：  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <xref:System.Windows.WindowStyle.SingleBorderWindow>（默认值）  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 下图演示了这些窗口样式的效果：  
  
 ![窗口边框样式的插图。](./media/wpf-windows-overview/window-border-styles.png)  
  
 您可以 <xref:System.Windows.Window.WindowStyle%2A> 使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 标记或代码进行设置; 因为在窗口生存期内不太可能更改，因此您最有可能使用标记对其进行配置 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 。  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a>非矩形窗口样式  
 在某些情况下， <xref:System.Windows.Window.WindowStyle%2A> 允许您使用的边框样式并不够。 例如，你可能想要创建一个具有非矩形边框的应用程序，如 Microsoft Windows Media Player 使用。  
  
 例如，请看下图中显示的语音气泡窗口：  
  
 ![显示 "拖动" 的语音气泡窗口。](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 可以通过将 <xref:System.Windows.Window.WindowStyle%2A> 属性设置为 <xref:System.Windows.WindowStyle.None> ，并使用具有透明度的特殊支持来创建此类型的窗口 <xref:System.Windows.Window> 。  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 多个值组合起来可以指示窗口呈现完全透明的效果。 在这种状态下，无法使用窗口的非工作区修饰（“关闭”菜单，“最小化”、“最大化”和“还原”按钮等）。 因此，需要提供自己的修饰。  
  
<a name="Task_Bar_Presence"></a>
### <a name="task-bar-presence"></a>任务栏显示  

窗口的默认外观包含一个任务栏按钮，如下图中所示：

 ![显示具有任务栏按钮的窗口的屏幕截图。](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 某些类型的 windows 没有任务栏按钮，如消息框和对话框（请参阅[对话框概述](dialog-boxes-overview.md)）。 您可以通过设置 <xref:System.Windows.Window.ShowInTaskbar%2A> 属性（ `true` 默认情况下）来控制是否显示窗口的任务栏按钮。  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>
## <a name="security-considerations"></a>安全注意事项  
 <xref:System.Windows.Window>需要 `UnmanagedCode` 实例化安全权限。 对于从本地计算机安装并启动的应用程序，此权限在授予应用程序的权限集中。  
  
 但是，这超出了向使用 ClickOnce 从 Internet 或本地 intranet 区域启动的应用程序授予的权限集。 因此，用户将收到 ClickOnce 安全警告，需要将应用程序的权限集提升到完全信任。  
  
 此外，默认情况下，Xbap 不能显示窗口或对话框。 有关独立应用程序安全注意事项的讨论，请参阅[WPF 安全策略-平台安全性](../wpf-security-strategy-platform-security.md)。  
  
<a name="Other_Types_of_Windows"></a>
## <a name="other-types-of-windows"></a>其他类型的窗口  
 <xref:System.Windows.Navigation.NavigationWindow>是旨在承载可导航内容的窗口。 有关详细信息，请参阅[导航概述](navigation-overview.md)。  
  
 对话框是通常用来收集用户信息以完成某项功能的窗口。 例如，当用户要打开文件时，应用程序通常会显示 "**打开文件**" 对话框以获取用户的文件名。 有关详细信息，请参阅[对话框概述](dialog-boxes-overview.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [对话框概述](dialog-boxes-overview.md)
- [生成 WPF 应用程序](building-a-wpf-application-wpf.md)

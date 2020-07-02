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
# <a name="wpf-windows-overview"></a><span data-ttu-id="d51cc-103">WPF Windows 概述</span><span class="sxs-lookup"><span data-stu-id="d51cc-103">WPF Windows Overview</span></span>
<span data-ttu-id="d51cc-104">用户通过 Windows 与 Windows Presentation Foundation （WPF）独立应用程序交互。</span><span class="sxs-lookup"><span data-stu-id="d51cc-104">Users interact with Windows Presentation Foundation (WPF) standalone applications through windows.</span></span> <span data-ttu-id="d51cc-105">窗口的主要用途是托管使数据可视化并使用户能够与数据交互的内容。</span><span class="sxs-lookup"><span data-stu-id="d51cc-105">The primary purpose of a window is to host content that visualizes data and enables users to interact with data.</span></span> <span data-ttu-id="d51cc-106">独立 WPF 应用程序使用类提供自己的窗口 <xref:System.Windows.Window> 。</span><span class="sxs-lookup"><span data-stu-id="d51cc-106">Standalone WPF applications provide their own windows by using the <xref:System.Windows.Window> class.</span></span> <span data-ttu-id="d51cc-107">本主题将介绍在 <xref:System.Windows.Window> 独立的应用程序中创建和管理 windows 的基本原理。</span><span class="sxs-lookup"><span data-stu-id="d51cc-107">This topic introduces <xref:System.Windows.Window> before covering the fundamentals of creating and managing windows in standalone applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d51cc-108">浏览器承载的 WPF 应用程序（包括 XAML 浏览器应用程序（Xbap）和松散 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 页面）不提供其自己的窗口。</span><span class="sxs-lookup"><span data-stu-id="d51cc-108">Browser-hosted WPF applications, including XAML browser applications (XBAPs) and loose [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pages, don't provide their own windows.</span></span> <span data-ttu-id="d51cc-109">而是托管在 Windows Internet Explorer 提供的 windows 中。</span><span class="sxs-lookup"><span data-stu-id="d51cc-109">Instead, they are hosted in windows provided by Windows Internet Explorer.</span></span> <span data-ttu-id="d51cc-110">请参阅[WPF XAML 浏览器应用程序概述](wpf-xaml-browser-applications-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d51cc-110">See [WPF XAML Browser Applications Overview](wpf-xaml-browser-applications-overview.md).</span></span>  

<a name="TheWindowClass"></a>
## <a name="the-window-class"></a><span data-ttu-id="d51cc-111">窗口类</span><span class="sxs-lookup"><span data-stu-id="d51cc-111">The Window Class</span></span>  
 <span data-ttu-id="d51cc-112">下图说明了窗口的组成部分：</span><span class="sxs-lookup"><span data-stu-id="d51cc-112">The following figure illustrates the constituent parts of a window:</span></span>  
  
 ![显示窗口元素的屏幕截图。](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 <span data-ttu-id="d51cc-114">窗口分为两个区域：非工作区和工作区。</span><span class="sxs-lookup"><span data-stu-id="d51cc-114">A window is divided into two areas: the non-client area and client area.</span></span>  
  
 <span data-ttu-id="d51cc-115">窗口的*非工作区*是由 WPF 实现的，包括大多数窗口所共有的窗口部分，其中包括：</span><span class="sxs-lookup"><span data-stu-id="d51cc-115">The *non-client area* of a window is implemented by WPF and includes the parts of a window that are common to most windows, including the following:</span></span>  
  
- <span data-ttu-id="d51cc-116">边框。</span><span class="sxs-lookup"><span data-stu-id="d51cc-116">A border.</span></span>  
  
- <span data-ttu-id="d51cc-117">标题栏。</span><span class="sxs-lookup"><span data-stu-id="d51cc-117">A title bar.</span></span>  
  
- <span data-ttu-id="d51cc-118">图标。</span><span class="sxs-lookup"><span data-stu-id="d51cc-118">An icon.</span></span>  
  
- <span data-ttu-id="d51cc-119">“最小化”、“最大化”和“还原”按钮。</span><span class="sxs-lookup"><span data-stu-id="d51cc-119">Minimize, Maximize, and Restore buttons.</span></span>  
  
- <span data-ttu-id="d51cc-120">“关闭”按钮。</span><span class="sxs-lookup"><span data-stu-id="d51cc-120">A Close button.</span></span>  
  
- <span data-ttu-id="d51cc-121">“系统”菜单，其中包含允许用户最小化、最大化、还原、移动和关闭窗口以及重设窗口大小的菜单项。</span><span class="sxs-lookup"><span data-stu-id="d51cc-121">A System menu with menu items that allow users to minimize, maximize, restore, move, resize, and close a window.</span></span>  
  
 <span data-ttu-id="d51cc-122">窗口的*工作区*是窗口非工作区内的区域，开发人员使用它来添加特定于应用程序的内容，例如菜单栏、工具栏和控件。</span><span class="sxs-lookup"><span data-stu-id="d51cc-122">The *client area* of a window is the area within a window's non-client area and is used by developers to add application-specific content, such as menu bars, tool bars, and controls.</span></span>  
  
 <span data-ttu-id="d51cc-123">在 WPF 中，窗口由 <xref:System.Windows.Window> 用于执行以下操作的类进行封装：</span><span class="sxs-lookup"><span data-stu-id="d51cc-123">In WPF, a window is encapsulated by the <xref:System.Windows.Window> class that you use to do the following:</span></span>  
  
- <span data-ttu-id="d51cc-124">显示窗口。</span><span class="sxs-lookup"><span data-stu-id="d51cc-124">Display a window.</span></span>  
  
- <span data-ttu-id="d51cc-125">配置窗口的大小、位置和外观。</span><span class="sxs-lookup"><span data-stu-id="d51cc-125">Configure the size, position, and appearance of a window.</span></span>  
  
- <span data-ttu-id="d51cc-126">托管特定于应用程序的内容。</span><span class="sxs-lookup"><span data-stu-id="d51cc-126">Host application-specific content.</span></span>  
  
- <span data-ttu-id="d51cc-127">管理窗口的生存期。</span><span class="sxs-lookup"><span data-stu-id="d51cc-127">Manage the lifetime of a window.</span></span>  
  
<a name="DefiningAWindow"></a>
## <a name="implementing-a-window"></a><span data-ttu-id="d51cc-128">实现窗口</span><span class="sxs-lookup"><span data-stu-id="d51cc-128">Implementing a Window</span></span>  
 <span data-ttu-id="d51cc-129">典型窗口的实现同时包含外观和行为，其中*外观*定义了窗口对用户和*行为*的外观，定义了窗口与用户交互的方式。</span><span class="sxs-lookup"><span data-stu-id="d51cc-129">The implementation of a typical window comprises both appearance and behavior, where *appearance* defines how a window looks to users and *behavior* defines the way a window functions as users interact with it.</span></span> <span data-ttu-id="d51cc-130">在 WPF 中，可以使用代码或标记实现窗口的外观和行为 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d51cc-130">In WPF, you can implement the appearance and behavior of a window using either code or [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 <span data-ttu-id="d51cc-131">但一般情况下，窗口的外观是使用标记实现的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，其行为是使用代码隐藏实现的，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="d51cc-131">In general, however, the appearance of a window is implemented using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and its behavior is implemented using code-behind, as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 <span data-ttu-id="d51cc-132">若要使 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 标记文件和代码隐藏文件协同工作，需要满足以下要求：</span><span class="sxs-lookup"><span data-stu-id="d51cc-132">To enable a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup file and code-behind file to work together, the following are required:</span></span>  
  
- <span data-ttu-id="d51cc-133">在标记中， `Window` 元素必须包含 `x:Class` 属性。</span><span class="sxs-lookup"><span data-stu-id="d51cc-133">In markup, the `Window` element must include the `x:Class` attribute.</span></span> <span data-ttu-id="d51cc-134">生成应用程序后， `x:Class` 标记文件中存在会导致 Microsoft 生成引擎（MSBuild）创建一个 `partial` 派生自的类， <xref:System.Windows.Window> 并具有由特性指定的名称 `x:Class` 。</span><span class="sxs-lookup"><span data-stu-id="d51cc-134">When the application is built, the existence of `x:Class` in the markup file causes Microsoft build engine (MSBuild) to create a `partial` class that derives from <xref:System.Windows.Window> and has the name that is specified by the `x:Class` attribute.</span></span> <span data-ttu-id="d51cc-135">这要求为架构（）添加 XML 命名空间声明 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` 。</span><span class="sxs-lookup"><span data-stu-id="d51cc-135">This requires the addition of an XML namespace declaration for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schema ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).</span></span> <span data-ttu-id="d51cc-136">生成的 `partial` 类实现 `InitializeComponent` 方法，该方法用于注册事件并设置标记中实现的属性。</span><span class="sxs-lookup"><span data-stu-id="d51cc-136">The generated `partial` class implements the `InitializeComponent` method, which is called to register the events and set the properties that are implemented in markup.</span></span>  
  
- <span data-ttu-id="d51cc-137">在代码隐藏中，类必须是 `partial` 由标记中的特性指定的同名类 `x:Class` ，并且必须派生自 <xref:System.Windows.Window> 。</span><span class="sxs-lookup"><span data-stu-id="d51cc-137">In code-behind, the class must be a `partial` class with the same name that is specified by the `x:Class` attribute in markup, and it must derive from <xref:System.Windows.Window>.</span></span> <span data-ttu-id="d51cc-138">这允许在生成应用程序时将代码隐藏文件与为 `partial` 标记文件生成的类相关联（请参阅[生成 WPF 应用程序](building-a-wpf-application-wpf.md)）。</span><span class="sxs-lookup"><span data-stu-id="d51cc-138">This allows the code-behind file to be associated with the `partial` class that is generated for the markup file when the application is built (see [Building a WPF Application](building-a-wpf-application-wpf.md)).</span></span>  
  
- <span data-ttu-id="d51cc-139">在代码隐藏中， <xref:System.Windows.Window> 该类必须实现调用方法的构造函数 `InitializeComponent` 。</span><span class="sxs-lookup"><span data-stu-id="d51cc-139">In code-behind, the <xref:System.Windows.Window> class must implement a constructor that calls the `InitializeComponent` method.</span></span> <span data-ttu-id="d51cc-140">`InitializeComponent`由标记文件的生成类实现， `partial` 用于注册事件和设置在标记中定义的属性。</span><span class="sxs-lookup"><span data-stu-id="d51cc-140">`InitializeComponent` is implemented by the markup file's generated `partial` class to register events and set properties that are defined in markup.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d51cc-141"><xref:System.Windows.Window>使用 Visual Studio 向项目添加新的时，将 <xref:System.Windows.Window> 使用标记和代码隐藏来实现，并包括必要的配置以创建标记和代码隐藏文件之间的关联，如此处所述。</span><span class="sxs-lookup"><span data-stu-id="d51cc-141">When you add a new <xref:System.Windows.Window> to your project by using Visual Studio, the <xref:System.Windows.Window> is implemented using both markup and code-behind, and includes the necessary configuration to create the association between the markup and code-behind files as described here.</span></span>  
  
 <span data-ttu-id="d51cc-142">通过此配置，你可以专注于定义标记中窗口的外观 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 并在代码隐藏中实现其行为。</span><span class="sxs-lookup"><span data-stu-id="d51cc-142">With this configuration in place, you can focus on defining the appearance of the window in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and implementing its behavior in code-behind.</span></span> <span data-ttu-id="d51cc-143">下面的示例演示了一个窗口，其中包含一个按钮，在标记中实现 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 并在 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 代码隐藏中实现了该按钮事件的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="d51cc-143">The following example shows a window with a button, implemented in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and an event handler for the button's <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, implemented in code-behind.</span></span>  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>
## <a name="configuring-a-window-definition-for-msbuild"></a><span data-ttu-id="d51cc-144">为 MSBuild 配置窗口定义</span><span class="sxs-lookup"><span data-stu-id="d51cc-144">Configuring a Window Definition for MSBuild</span></span>  
 <span data-ttu-id="d51cc-145">如何实现窗口将决定如何为 MSBuild 配置它。</span><span class="sxs-lookup"><span data-stu-id="d51cc-145">How you implement your window determines how it is configured for MSBuild.</span></span> <span data-ttu-id="d51cc-146">对于使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 标记和代码隐藏定义的窗口：</span><span class="sxs-lookup"><span data-stu-id="d51cc-146">For a window that is defined using both [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind:</span></span>  
  
- <span data-ttu-id="d51cc-147">XAML 标记文件配置为 MSBuild `Page` 项。</span><span class="sxs-lookup"><span data-stu-id="d51cc-147">XAML markup files are configured as MSBuild `Page` items.</span></span>  
  
- <span data-ttu-id="d51cc-148">代码隐藏文件配置为 MSBuild `Compile` 项。</span><span class="sxs-lookup"><span data-stu-id="d51cc-148">Code-behind files are configured as MSBuild `Compile` items.</span></span>  
  
 <span data-ttu-id="d51cc-149">下面的 MSBuild 项目文件中显示了这种情况。</span><span class="sxs-lookup"><span data-stu-id="d51cc-149">This is shown in the following MSBuild project file.</span></span>  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 <span data-ttu-id="d51cc-150">有关生成 WPF 应用程序的信息，请参阅[生成 Wpf 应用程序](building-a-wpf-application-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="d51cc-150">For information about building WPF applications, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>  
  
<a name="WindowLifetime"></a>
## <a name="window-lifetime"></a><span data-ttu-id="d51cc-151">窗口生存期</span><span class="sxs-lookup"><span data-stu-id="d51cc-151">Window Lifetime</span></span>  
 <span data-ttu-id="d51cc-152">与所有类一样，窗口也有生存期，开始于首次实例化窗口，在这之后将打开、激活、停用直至最终关闭窗口。</span><span class="sxs-lookup"><span data-stu-id="d51cc-152">As with any class, a window has a lifetime that begins when it is first instantiated, after which it is opened, activated and deactivated, and eventually closed.</span></span>  

<a name="Opening_a_Window"></a>
### <a name="opening-a-window"></a><span data-ttu-id="d51cc-153">打开窗口</span><span class="sxs-lookup"><span data-stu-id="d51cc-153">Opening a Window</span></span>  
 <span data-ttu-id="d51cc-154">若要打开窗口，首先要创建窗口实例，下面的示例演示此操作。</span><span class="sxs-lookup"><span data-stu-id="d51cc-154">To open a window, you first create an instance of it, which is demonstrated in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 <span data-ttu-id="d51cc-155">在此示例中，在 `MarkupAndCodeBehindWindow` 应用程序启动时实例化，这会在 <xref:System.Windows.Application.Startup> 引发事件时发生。</span><span class="sxs-lookup"><span data-stu-id="d51cc-155">In this example, the `MarkupAndCodeBehindWindow` is instantiated when the application starts, which occurs when the <xref:System.Windows.Application.Startup> event is raised.</span></span>  
  
 <span data-ttu-id="d51cc-156">在实例化窗口时，对它的引用会自动添加到由该对象管理的窗口的列表中 <xref:System.Windows.Application> （请参见 <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType> ）。</span><span class="sxs-lookup"><span data-stu-id="d51cc-156">When a window is instantiated, a reference to it is automatically added to a list of windows that is managed by the <xref:System.Windows.Application> object (see <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>).</span></span> <span data-ttu-id="d51cc-157">此外，默认情况下，第一个要实例化的窗口是由设置 <xref:System.Windows.Application> 为主应用程序窗口（请参阅 <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType> ）。</span><span class="sxs-lookup"><span data-stu-id="d51cc-157">Additionally, the first window to be instantiated is, by default, set by <xref:System.Windows.Application> as the main application window (see <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="d51cc-158">最后，通过调用方法打开该窗口 <xref:System.Windows.Window.Show%2A> ; 结果如下图所示。</span><span class="sxs-lookup"><span data-stu-id="d51cc-158">The window is finally opened by calling the <xref:System.Windows.Window.Show%2A> method; the result is shown in the following figure.</span></span>  
  
 ![通过调用窗口打开的窗口。显示](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 <span data-ttu-id="d51cc-160">通过调用打开的窗口 <xref:System.Windows.Window.Show%2A> 是一个无模式窗口，这意味着应用程序以允许用户在同一应用程序中激活其他窗口的模式操作。</span><span class="sxs-lookup"><span data-stu-id="d51cc-160">A window that is opened by calling <xref:System.Windows.Window.Show%2A> is a modeless window, which means that the application operates in a mode that allows users to activate other windows in the same application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d51cc-161"><xref:System.Windows.Window.ShowDialog%2A>调用以模式打开 windows，如对话框。</span><span class="sxs-lookup"><span data-stu-id="d51cc-161"><xref:System.Windows.Window.ShowDialog%2A> is called to open windows such as dialog boxes modally.</span></span> <span data-ttu-id="d51cc-162">有关详细信息，请参阅[对话框概述](dialog-boxes-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d51cc-162">See [Dialog Boxes Overview](dialog-boxes-overview.md) for more information.</span></span>  
  
 <span data-ttu-id="d51cc-163"><xref:System.Windows.Window.Show%2A>调用时，窗口将执行初始化工作，并显示该工作以建立允许它接收用户输入的基础结构。</span><span class="sxs-lookup"><span data-stu-id="d51cc-163">When <xref:System.Windows.Window.Show%2A> is called, a window performs initialization work before it is shown to establish infrastructure that allows it to receive user input.</span></span> <span data-ttu-id="d51cc-164">初始化窗口时，将 <xref:System.Windows.Window.SourceInitialized> 引发事件，并显示窗口。</span><span class="sxs-lookup"><span data-stu-id="d51cc-164">When the window is initialized, the <xref:System.Windows.Window.SourceInitialized> event is raised and the window is shown.</span></span>  
  
 <span data-ttu-id="d51cc-165">作为快捷方式， <xref:System.Windows.Application.StartupUri%2A> 可以将设置为指定应用程序启动时自动打开的第一个窗口。</span><span class="sxs-lookup"><span data-stu-id="d51cc-165">As a shortcut, <xref:System.Windows.Application.StartupUri%2A> can be set to specify the first window that is opened automatically when an application starts.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 <span data-ttu-id="d51cc-166">当应用程序启动时，的值所指定的窗口 <xref:System.Windows.Application.StartupUri%2A> 将在 modelessly 中打开。通过调用其方法，打开窗口 <xref:System.Windows.Window.Show%2A> 。</span><span class="sxs-lookup"><span data-stu-id="d51cc-166">When the application starts, the window specified by the value of <xref:System.Windows.Application.StartupUri%2A> is opened modelessly; internally, the window is opened by calling its <xref:System.Windows.Window.Show%2A> method.</span></span>  
  
<a name="Ownership"></a>
#### <a name="window-ownership"></a><span data-ttu-id="d51cc-167">窗口所有权</span><span class="sxs-lookup"><span data-stu-id="d51cc-167">Window Ownership</span></span>  
 <span data-ttu-id="d51cc-168">使用方法打开的窗口 <xref:System.Windows.Window.Show%2A> 与创建它的窗口不具有隐式关系; 用户可以与任何一个窗口独立交互，这意味着，这两个窗口都可以执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="d51cc-168">A window that is opened by using the <xref:System.Windows.Window.Show%2A> method does not have an implicit relationship with the window that created it; users can interact with either window independently of the other, which means that either window can do the following:</span></span>  
  
- <span data-ttu-id="d51cc-169">覆盖其他（除非其中一个 windows 的 <xref:System.Windows.Window.Topmost%2A> 属性设置为 `true` ）。</span><span class="sxs-lookup"><span data-stu-id="d51cc-169">Cover the other (unless one of the windows has its <xref:System.Windows.Window.Topmost%2A> property set to `true`).</span></span>  
  
- <span data-ttu-id="d51cc-170">在不影响另一个窗口的情况下最小化、最大化和还原。</span><span class="sxs-lookup"><span data-stu-id="d51cc-170">Be minimized, maximized, and restored without affecting the other.</span></span>  
  
 <span data-ttu-id="d51cc-171">某些窗口要求与打开它们的窗口保持某种关系。</span><span class="sxs-lookup"><span data-stu-id="d51cc-171">Some windows require a relationship with the window that opens them.</span></span> <span data-ttu-id="d51cc-172">例如，集成开发环境（IDE）应用程序可以打开属性窗口和工具窗口，其典型行为是涵盖创建它们的窗口。</span><span class="sxs-lookup"><span data-stu-id="d51cc-172">For example, an Integrated Development Environment (IDE) application may open property windows and tool windows whose typical behavior is to cover the window that creates them.</span></span> <span data-ttu-id="d51cc-173">此外，此类窗口应始终与创建它们的窗口一起关闭、最小化、最大化和还原。</span><span class="sxs-lookup"><span data-stu-id="d51cc-173">Furthermore, such windows should always close, minimize, maximize, and restore in concert with the window that created them.</span></span> <span data-ttu-id="d51cc-174">这种关系可通过使*一个窗口成为*一个窗口而建立，通过设置 <xref:System.Windows.Window.Owner%2A> 拥有的*窗口*的属性和对*所有者窗口*的引用来实现。</span><span class="sxs-lookup"><span data-stu-id="d51cc-174">Such a relationship can be established by making one window *own* another, and is achieved by setting the <xref:System.Windows.Window.Owner%2A> property of the *owned window* with a reference to the *owner window*.</span></span> <span data-ttu-id="d51cc-175">这在下面的示例中显示。</span><span class="sxs-lookup"><span data-stu-id="d51cc-175">This is shown in the following example.</span></span>  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 <span data-ttu-id="d51cc-176">建立所有权后：</span><span class="sxs-lookup"><span data-stu-id="d51cc-176">After ownership is established:</span></span>  
  
- <span data-ttu-id="d51cc-177">拥有的窗口可以通过检查其属性的值引用其所有者窗口 <xref:System.Windows.Window.Owner%2A> 。</span><span class="sxs-lookup"><span data-stu-id="d51cc-177">The owned window can reference its owner window by inspecting the value of its <xref:System.Windows.Window.Owner%2A> property.</span></span>  
  
- <span data-ttu-id="d51cc-178">所有者窗口可以通过检查其属性的值来发现其拥有的所有窗口 <xref:System.Windows.Window.OwnedWindows%2A> 。</span><span class="sxs-lookup"><span data-stu-id="d51cc-178">The owner window can discover all the windows it owns by inspecting the value of its <xref:System.Windows.Window.OwnedWindows%2A> property.</span></span>  
  
<a name="Preventing"></a>
#### <a name="preventing-window-activation"></a><span data-ttu-id="d51cc-179">防止窗口激活</span><span class="sxs-lookup"><span data-stu-id="d51cc-179">Preventing Window Activation</span></span>  
 <span data-ttu-id="d51cc-180">在某些情况下，windows 不应在显示时激活，如 Internet messenger 样式应用程序的对话窗口或电子邮件应用程序的通知窗口。</span><span class="sxs-lookup"><span data-stu-id="d51cc-180">There are scenarios where windows should not be activated when shown, such as conversation windows of an Internet messenger-style application or notification windows of an email application.</span></span>  
  
 <span data-ttu-id="d51cc-181">如果你的应用程序具有在显示时不应激活的窗口，则可在 <xref:System.Windows.Window.ShowActivated%2A> `false` <xref:System.Windows.Window.Show%2A> 第一次调用方法之前，将其属性设置为。</span><span class="sxs-lookup"><span data-stu-id="d51cc-181">If your application has a window that shouldn't be activated when shown, you can set its <xref:System.Windows.Window.ShowActivated%2A> property to `false` before calling the <xref:System.Windows.Window.Show%2A> method for the first time.</span></span> <span data-ttu-id="d51cc-182">结果是：</span><span class="sxs-lookup"><span data-stu-id="d51cc-182">As a consequence:</span></span>  
  
- <span data-ttu-id="d51cc-183">不会激活窗口。</span><span class="sxs-lookup"><span data-stu-id="d51cc-183">The window is not activated.</span></span>  
  
- <span data-ttu-id="d51cc-184"><xref:System.Windows.Window.Activated>不引发窗口的事件。</span><span class="sxs-lookup"><span data-stu-id="d51cc-184">The window's <xref:System.Windows.Window.Activated> event is not raised.</span></span>  
  
- <span data-ttu-id="d51cc-185">当前激活的窗口保持激活状态。</span><span class="sxs-lookup"><span data-stu-id="d51cc-185">The currently activated window remains activated.</span></span>  
  
 <span data-ttu-id="d51cc-186">但是，只要用户通过单击工作区或非工作区激活了窗口，窗口就会变为激活状态。</span><span class="sxs-lookup"><span data-stu-id="d51cc-186">The window will become activated, however, as soon as the user activates it by clicking either the client or non-client area.</span></span> <span data-ttu-id="d51cc-187">在这种情况下：</span><span class="sxs-lookup"><span data-stu-id="d51cc-187">In this case:</span></span>  
  
- <span data-ttu-id="d51cc-188">已激活窗口。</span><span class="sxs-lookup"><span data-stu-id="d51cc-188">The window is activated.</span></span>  
  
- <span data-ttu-id="d51cc-189">引发窗口的 <xref:System.Windows.Window.Activated> 事件。</span><span class="sxs-lookup"><span data-stu-id="d51cc-189">The window's <xref:System.Windows.Window.Activated> event is raised.</span></span>  
  
- <span data-ttu-id="d51cc-190">停用之前激活的窗口。</span><span class="sxs-lookup"><span data-stu-id="d51cc-190">The previously activated window is deactivated.</span></span>  
  
- <span data-ttu-id="d51cc-191"><xref:System.Windows.Window.Deactivated> <xref:System.Windows.Window.Activated> 随后会按预期方式引发窗口和事件以响应用户操作。</span><span class="sxs-lookup"><span data-stu-id="d51cc-191">The window's <xref:System.Windows.Window.Deactivated> and <xref:System.Windows.Window.Activated> events are subsequently raised as expected in response to user actions.</span></span>  
  
<a name="Window_Activation"></a>
### <a name="window-activation"></a><span data-ttu-id="d51cc-192">窗口激活</span><span class="sxs-lookup"><span data-stu-id="d51cc-192">Window Activation</span></span>  
 <span data-ttu-id="d51cc-193">第一次打开窗口时，它将成为活动窗口（除非显示时显示 " <xref:System.Windows.Window.ShowActivated%2A> 设置为" `false` ）。</span><span class="sxs-lookup"><span data-stu-id="d51cc-193">When a window is first opened, it becomes the active window (unless it is shown with <xref:System.Windows.Window.ShowActivated%2A> set to `false`).</span></span> <span data-ttu-id="d51cc-194">*活动窗口*是当前正在捕获用户输入的窗口，例如键击和鼠标单击。</span><span class="sxs-lookup"><span data-stu-id="d51cc-194">The *active window* is the window that is currently capturing user input, such as key strokes and mouse clicks.</span></span> <span data-ttu-id="d51cc-195">当窗口处于活动状态时，它会引发 <xref:System.Windows.Window.Activated> 事件。</span><span class="sxs-lookup"><span data-stu-id="d51cc-195">When a window becomes active, it raises the <xref:System.Windows.Window.Activated> event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d51cc-196">首次打开窗口时，仅在 <xref:System.Windows.FrameworkElement.Loaded> <xref:System.Windows.Window.ContentRendered> 引发事件后引发和事件 <xref:System.Windows.Window.Activated> 。</span><span class="sxs-lookup"><span data-stu-id="d51cc-196">When a window is first opened, the <xref:System.Windows.FrameworkElement.Loaded> and <xref:System.Windows.Window.ContentRendered> events are raised only after the <xref:System.Windows.Window.Activated> event is raised.</span></span> <span data-ttu-id="d51cc-197">考虑到这一点，当引发时，可以有效地将窗口视为 <xref:System.Windows.Window.ContentRendered> 已打开。</span><span class="sxs-lookup"><span data-stu-id="d51cc-197">With this in mind, a window can effectively be considered opened when <xref:System.Windows.Window.ContentRendered> is raised.</span></span>  
  
 <span data-ttu-id="d51cc-198">某个窗口成为活动窗口后，用户可以在同一应用程序内激活其他窗口，或者激活其他应用程序。</span><span class="sxs-lookup"><span data-stu-id="d51cc-198">After a window becomes active, a user can activate another window in the same application, or activate another application.</span></span> <span data-ttu-id="d51cc-199">发生这种情况时，将停用当前处于活动状态的窗口，并引发 <xref:System.Windows.Window.Deactivated> 事件。</span><span class="sxs-lookup"><span data-stu-id="d51cc-199">When that happens, the currently active window becomes deactivated and raises the <xref:System.Windows.Window.Deactivated> event.</span></span> <span data-ttu-id="d51cc-200">同样，当用户选择当前已停用的窗口时，该窗口将再次变为活动状态并 <xref:System.Windows.Window.Activated> 引发。</span><span class="sxs-lookup"><span data-stu-id="d51cc-200">Likewise, when the user selects a currently deactivated window, the window becomes active again and <xref:System.Windows.Window.Activated> is raised.</span></span>  
  
 <span data-ttu-id="d51cc-201">处理和的一个常见 <xref:System.Windows.Window.Activated> 原因 <xref:System.Windows.Window.Deactivated> 是启用和禁用只能在窗口处于活动状态时运行的功能。</span><span class="sxs-lookup"><span data-stu-id="d51cc-201">One common reason to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> is to enable and disable functionality that can only run when a window is active.</span></span> <span data-ttu-id="d51cc-202">例如，一些窗口显示需要用户持续输入或关注的交互式内容，这些内容包括游戏和视频播放器。</span><span class="sxs-lookup"><span data-stu-id="d51cc-202">For example, some windows display interactive content that requires constant user input or attention, including games and video players.</span></span> <span data-ttu-id="d51cc-203">下面的示例是一个简化的视频播放器，演示如何处理 <xref:System.Windows.Window.Activated> 和 <xref:System.Windows.Window.Deactivated> 实现此行为。</span><span class="sxs-lookup"><span data-stu-id="d51cc-203">The following example is a simplified video player that demonstrates how to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> to implement this behavior.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 <span data-ttu-id="d51cc-204">停用某个窗口后，其他类型的应用程序可能仍会在后台运行代码。</span><span class="sxs-lookup"><span data-stu-id="d51cc-204">Other types of applications may still run code in the background when a window is deactivated.</span></span> <span data-ttu-id="d51cc-205">例如，在用户使用其他应用程序时，邮件客户端可能会继续轮询邮件服务器。</span><span class="sxs-lookup"><span data-stu-id="d51cc-205">For example, a mail client may continue polling the mail server while the user is using other applications.</span></span> <span data-ttu-id="d51cc-206">类似的应用程序在主窗口停用时，通常将提供不同或其他的行为。</span><span class="sxs-lookup"><span data-stu-id="d51cc-206">Applications like these often provide different or additional behavior while the main window is deactivated.</span></span> <span data-ttu-id="d51cc-207">对于邮件程序，这可能意味着将新邮件项添加到收件箱和将通知图标添加到系统任务栏。</span><span class="sxs-lookup"><span data-stu-id="d51cc-207">With respect to the mail program, this may mean both adding the new mail item to the inbox and adding a notification icon to the system tray.</span></span> <span data-ttu-id="d51cc-208">仅当邮件窗口不处于活动状态时才显示通知图标，可以通过检查属性来确定 <xref:System.Windows.Window.IsActive%2A> 。</span><span class="sxs-lookup"><span data-stu-id="d51cc-208">A notification icon need only be displayed when the mail window isn't active, which can be determined by inspecting the <xref:System.Windows.Window.IsActive%2A> property.</span></span>  
  
 <span data-ttu-id="d51cc-209">如果后台任务已完成，则窗口可能需要通过调用方法更紧急地通知用户 <xref:System.Windows.Window.Activate%2A> 。</span><span class="sxs-lookup"><span data-stu-id="d51cc-209">If a background task completes, a window may want to notify the user more urgently by calling <xref:System.Windows.Window.Activate%2A> method.</span></span> <span data-ttu-id="d51cc-210">如果用户与调用时激活的其他应用程序交互 <xref:System.Windows.Window.Activate%2A> ，则窗口的任务栏按钮会闪烁。</span><span class="sxs-lookup"><span data-stu-id="d51cc-210">If the user is interacting with another application activated when <xref:System.Windows.Window.Activate%2A> is called, the window's taskbar button flashes.</span></span> <span data-ttu-id="d51cc-211">如果用户与当前应用程序交互，则调用 <xref:System.Windows.Window.Activate%2A> 会将窗口置于前台。</span><span class="sxs-lookup"><span data-stu-id="d51cc-211">If a user is interacting with the current application, calling <xref:System.Windows.Window.Activate%2A> will bring the window to the foreground.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d51cc-212">您可以使用和事件处理应用程序范围的激活 <xref:System.Windows.Application.Activated?displayProperty=nameWithType> <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="d51cc-212">You can handle application-scope activation using the <xref:System.Windows.Application.Activated?displayProperty=nameWithType> and <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> events.</span></span>  
  
<a name="Closing_a_Window"></a>
### <a name="closing-a-window"></a><span data-ttu-id="d51cc-213">关闭窗口</span><span class="sxs-lookup"><span data-stu-id="d51cc-213">Closing a Window</span></span>  
 <span data-ttu-id="d51cc-214">窗口的生存期在用户关闭它时终止。</span><span class="sxs-lookup"><span data-stu-id="d51cc-214">The life of a window starts coming to an end when a user closes it.</span></span> <span data-ttu-id="d51cc-215">可以使用非工作区中的元素关闭窗口，这些元素包括：</span><span class="sxs-lookup"><span data-stu-id="d51cc-215">A window can be closed by using elements in the non-client area, including the following:</span></span>  
  
- <span data-ttu-id="d51cc-216">**系统**菜单的**关闭**项。</span><span class="sxs-lookup"><span data-stu-id="d51cc-216">The **Close** item of the **System** menu.</span></span>  
  
- <span data-ttu-id="d51cc-217">按 ALT+F4。</span><span class="sxs-lookup"><span data-stu-id="d51cc-217">Pressing ALT+F4.</span></span>  
  
- <span data-ttu-id="d51cc-218">按 "**关闭**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="d51cc-218">Pressing the **Close** button.</span></span>  
  
 <span data-ttu-id="d51cc-219">可以向工作区提供其他关闭窗口的机制，较为常见的机制包括：</span><span class="sxs-lookup"><span data-stu-id="d51cc-219">You can provide additional mechanisms to the client area to close a window, the more common of which include the following:</span></span>  
  
- <span data-ttu-id="d51cc-220">"**文件**" 菜单中的 "**退出**" 项，通常用于主应用程序窗口。</span><span class="sxs-lookup"><span data-stu-id="d51cc-220">An **Exit** item in the **File** menu, typically for main application windows.</span></span>  
  
- <span data-ttu-id="d51cc-221">"**文件**" 菜单中的 "**关闭**" 项，通常在辅助应用程序窗口中。</span><span class="sxs-lookup"><span data-stu-id="d51cc-221">A **Close** item in the **File** menu, typically on a secondary application window.</span></span>  
  
- <span data-ttu-id="d51cc-222">"**取消**" 按钮，通常位于模式对话框中。</span><span class="sxs-lookup"><span data-stu-id="d51cc-222">A **Cancel** button, typically on a modal dialog box.</span></span>  
  
- <span data-ttu-id="d51cc-223">"**关闭**" 按钮，通常位于无模式对话框中。</span><span class="sxs-lookup"><span data-stu-id="d51cc-223">A **Close** button, typically on a modeless dialog box.</span></span>  
  
 <span data-ttu-id="d51cc-224">若要关闭窗口以响应其中一种自定义机制，需要调用 <xref:System.Windows.Window.Close%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="d51cc-224">To close a window in response to one of these custom mechanisms, you need to call the <xref:System.Windows.Window.Close%2A> method.</span></span> <span data-ttu-id="d51cc-225">下面的示例通过选择 "**文件**" 菜单上的 "**退出**" 来实现关闭窗口的功能。</span><span class="sxs-lookup"><span data-stu-id="d51cc-225">The following example implements the ability to close a window by choosing the **Exit** on the **File** menu.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 <span data-ttu-id="d51cc-226">当窗口关闭时，它将引发两个事件： <xref:System.Windows.Window.Closing> 和 <xref:System.Windows.Window.Closed> 。</span><span class="sxs-lookup"><span data-stu-id="d51cc-226">When a window closes, it raises two events: <xref:System.Windows.Window.Closing> and <xref:System.Windows.Window.Closed>.</span></span>  
  
 <span data-ttu-id="d51cc-227"><xref:System.Windows.Window.Closing>在窗口关闭前引发，并提供一种机制，可通过该机制阻止窗口关闭。</span><span class="sxs-lookup"><span data-stu-id="d51cc-227"><xref:System.Windows.Window.Closing> is raised before the window closes, and it provides a mechanism by which window closure can be prevented.</span></span> <span data-ttu-id="d51cc-228">阻止窗口关闭的一个常见原因是窗口内容包含修改的数据。</span><span class="sxs-lookup"><span data-stu-id="d51cc-228">One common reason to prevent window closure is if window content contains modified data.</span></span> <span data-ttu-id="d51cc-229">在这种情况下， <xref:System.Windows.Window.Closing> 可以处理事件以确定数据是否处于脏状态，如果是，则要求用户是否继续关闭窗口而不保存数据或取消关闭窗口。</span><span class="sxs-lookup"><span data-stu-id="d51cc-229">In this situation, the <xref:System.Windows.Window.Closing> event can be handled to determine whether data is dirty and, if so, to ask the user whether to either continue closing the window without saving the data or to cancel window closure.</span></span> <span data-ttu-id="d51cc-230">下面的示例演示了处理的关键方面 <xref:System.Windows.Window.Closing> 。</span><span class="sxs-lookup"><span data-stu-id="d51cc-230">The following example shows the key aspects of handling <xref:System.Windows.Window.Closing>.</span></span>  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 <span data-ttu-id="d51cc-231"><xref:System.Windows.Window.Closing>向事件处理程序传递，该事件处理程序 <xref:System.ComponentModel.CancelEventArgs> 实现了 `Boolean` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> 设置为的属性， `true` 以防止窗口关闭。</span><span class="sxs-lookup"><span data-stu-id="d51cc-231">The <xref:System.Windows.Window.Closing> event handler is passed a <xref:System.ComponentModel.CancelEventArgs>, which implements the `Boolean`<xref:System.ComponentModel.CancelEventArgs.Cancel%2A> property that you set to `true` to prevent a window from closing.</span></span>  
  
 <span data-ttu-id="d51cc-232">如果 <xref:System.Windows.Window.Closing> 未处理，或者处理但未取消，则窗口将关闭。</span><span class="sxs-lookup"><span data-stu-id="d51cc-232">If <xref:System.Windows.Window.Closing> is not handled, or it is handled but not canceled, the window will close.</span></span> <span data-ttu-id="d51cc-233">在窗口实际关闭之前， <xref:System.Windows.Window.Closed> 将引发。</span><span class="sxs-lookup"><span data-stu-id="d51cc-233">Just before a window actually closes, <xref:System.Windows.Window.Closed> is raised.</span></span> <span data-ttu-id="d51cc-234">此时，无法阻止窗口关闭。</span><span class="sxs-lookup"><span data-stu-id="d51cc-234">At this point, a window cannot be prevented from closing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d51cc-235">在主应用程序窗口关闭（请参阅 <xref:System.Windows.Application.MainWindow%2A> ）或最后一个窗口关闭时，可以将应用程序配置为自动关闭。</span><span class="sxs-lookup"><span data-stu-id="d51cc-235">An application can be configured to shut down automatically when either the main application window closes (see <xref:System.Windows.Application.MainWindow%2A>) or the last window closes.</span></span> <span data-ttu-id="d51cc-236">有关详细信息，请参阅<xref:System.Windows.Application.ShutdownMode%2A>。</span><span class="sxs-lookup"><span data-stu-id="d51cc-236">For details, see <xref:System.Windows.Application.ShutdownMode%2A>.</span></span>  
  
 <span data-ttu-id="d51cc-237">尽管可以通过非客户端和客户端区域中提供的机制显式关闭窗口，但也可以通过应用程序或窗口的其他部分中的行为来隐式关闭窗口，其中包括：</span><span class="sxs-lookup"><span data-stu-id="d51cc-237">While a window can be explicitly closed through mechanisms provided in the non-client and client areas, a window can also be implicitly closed as a result of behavior in other parts of the application or Windows, including the following:</span></span>  
  
- <span data-ttu-id="d51cc-238">用户注销或关闭 Windows。</span><span class="sxs-lookup"><span data-stu-id="d51cc-238">A user logs off or shuts down Windows.</span></span>  
  
- <span data-ttu-id="d51cc-239">窗口的所有者将关闭（请参阅 <xref:System.Windows.Window.Owner%2A> ）。</span><span class="sxs-lookup"><span data-stu-id="d51cc-239">A window's owner closes (see <xref:System.Windows.Window.Owner%2A>).</span></span>  
  
- <span data-ttu-id="d51cc-240">主应用程序窗口已关闭，并且 <xref:System.Windows.Application.ShutdownMode%2A> 为 <xref:System.Windows.ShutdownMode.OnMainWindowClose> 。</span><span class="sxs-lookup"><span data-stu-id="d51cc-240">The main application window is closed and <xref:System.Windows.Application.ShutdownMode%2A> is <xref:System.Windows.ShutdownMode.OnMainWindowClose>.</span></span>  
  
- <span data-ttu-id="d51cc-241">调用 <xref:System.Windows.Application.Shutdown%2A>。</span><span class="sxs-lookup"><span data-stu-id="d51cc-241"><xref:System.Windows.Application.Shutdown%2A> is called.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d51cc-242">窗口在关闭后无法重新打开。</span><span class="sxs-lookup"><span data-stu-id="d51cc-242">A window cannot be reopened after it is closed.</span></span>  
  
<a name="Window_Lifetime_Events"></a>
### <a name="window-lifetime-events"></a><span data-ttu-id="d51cc-243">窗口生存期事件</span><span class="sxs-lookup"><span data-stu-id="d51cc-243">Window Lifetime Events</span></span>  
 <span data-ttu-id="d51cc-244">下图显示了窗口生存期内的主体事件的顺序：</span><span class="sxs-lookup"><span data-stu-id="d51cc-244">The following illustration shows the sequence of the principal events in the lifetime of a window:</span></span>  
  
 ![在窗口生存期内显示事件的关系图。](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 <span data-ttu-id="d51cc-246">下图显示了在未激活的情况下显示的窗口生存期内的主体事件的顺序（在 <xref:System.Windows.Window.ShowActivated%2A> `false` 显示窗口之前设置为）：</span><span class="sxs-lookup"><span data-stu-id="d51cc-246">The following illustration shows the sequence of the principal events in the lifetime of a window that is shown without activation (<xref:System.Windows.Window.ShowActivated%2A> is set to `false` before the window is shown):</span></span>  
  
 ![在不激活的情况下显示窗口生存期内的事件的关系图。](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>
## <a name="window-location"></a><span data-ttu-id="d51cc-248">窗口位置</span><span class="sxs-lookup"><span data-stu-id="d51cc-248">Window Location</span></span>  
 <span data-ttu-id="d51cc-249">当窗口打开时，它在相对于桌面的 x 和 y 维度中有一个位置。</span><span class="sxs-lookup"><span data-stu-id="d51cc-249">While a window is open, it has a location in the x and y dimensions relative to the desktop.</span></span> <span data-ttu-id="d51cc-250">可以通过分别检查和属性来确定此位置 <xref:System.Windows.Window.Left%2A> <xref:System.Windows.Window.Top%2A> 。</span><span class="sxs-lookup"><span data-stu-id="d51cc-250">This location can be determined by inspecting the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties, respectively.</span></span> <span data-ttu-id="d51cc-251">设置这些属性可以更改窗口的位置。</span><span class="sxs-lookup"><span data-stu-id="d51cc-251">You can set these properties to change the location of the window.</span></span>  
  
 <span data-ttu-id="d51cc-252">你还可以 <xref:System.Windows.Window> 通过 <xref:System.Windows.Window.WindowStartupLocation%2A> 使用以下枚举值之一设置属性，来指定第一次出现的起始位置 <xref:System.Windows.WindowStartupLocation> ：</span><span class="sxs-lookup"><span data-stu-id="d51cc-252">You can also specify the initial location of a <xref:System.Windows.Window> when it first appears by setting the <xref:System.Windows.Window.WindowStartupLocation%2A> property with one of the following <xref:System.Windows.WindowStartupLocation> enumeration values:</span></span>  
  
- <span data-ttu-id="d51cc-253"><xref:System.Windows.WindowStartupLocation.CenterOwner>（默认值）</span><span class="sxs-lookup"><span data-stu-id="d51cc-253"><xref:System.Windows.WindowStartupLocation.CenterOwner> (default)</span></span>  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 <span data-ttu-id="d51cc-254">如果将启动位置指定为 <xref:System.Windows.WindowStartupLocation.Manual> ，并且 <xref:System.Windows.Window.Left%2A> <xref:System.Windows.Window.Top%2A> 未设置和属性， <xref:System.Windows.Window> 将要求 Windows 提供要显示在中的位置。</span><span class="sxs-lookup"><span data-stu-id="d51cc-254">If the startup location is specified as <xref:System.Windows.WindowStartupLocation.Manual>, and the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties have not been set, <xref:System.Windows.Window> will ask Windows for a location to appear in.</span></span>  
  
<a name="Topmost_Windows_and_Z_Order"></a>
### <a name="topmost-windows-and-z-order"></a><span data-ttu-id="d51cc-255">最顶层窗口和 Z 顺序</span><span class="sxs-lookup"><span data-stu-id="d51cc-255">Topmost Windows and Z-Order</span></span>  
 <span data-ttu-id="d51cc-256">除了有 x 和 y 位置外，窗口还在 z 维度中有一个位置，该位置确定窗口相对于其他窗口的垂直位置。</span><span class="sxs-lookup"><span data-stu-id="d51cc-256">Besides having an x and y location, a window also has a location in the z dimension, which determines its vertical position with respect to other windows.</span></span> <span data-ttu-id="d51cc-257">它称为窗口的 z 顺序，并且有两种类型：正常 z 顺序和最顶层 z 顺序。</span><span class="sxs-lookup"><span data-stu-id="d51cc-257">This is known as the window's z-order, and there are two types: normal z-order and topmost z-order.</span></span> <span data-ttu-id="d51cc-258">处于*正常 z 顺序*中的窗口的位置取决于它当前是否处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="d51cc-258">The location of a window in the *normal z-order* is determined by whether it is currently active or not.</span></span> <span data-ttu-id="d51cc-259">默认情况下，窗口位于正常 z 顺序中。</span><span class="sxs-lookup"><span data-stu-id="d51cc-259">By default, a window is located in the normal z-order.</span></span> <span data-ttu-id="d51cc-260">*最顶层 z 顺序*中的窗口位置也取决于它当前是否处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="d51cc-260">The location of a window in the *topmost z-order* is also determined by whether it is currently active or not.</span></span> <span data-ttu-id="d51cc-261">此外，最顶层 z 顺序中的窗口始终位于正常 z 顺序中的窗口之上。</span><span class="sxs-lookup"><span data-stu-id="d51cc-261">Furthermore, windows in the topmost z-order are always located above windows in the normal z-order.</span></span> <span data-ttu-id="d51cc-262">窗口通过将其属性设置为，位于最顶层 z 顺序中 <xref:System.Windows.Window.Topmost%2A> `true` 。</span><span class="sxs-lookup"><span data-stu-id="d51cc-262">A window is located in the topmost z-order by setting its <xref:System.Windows.Window.Topmost%2A> property to `true`.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 <span data-ttu-id="d51cc-263">在每个 z 顺序中，当前的活动窗口显示在同一 z 顺序中所有其他窗口之上。</span><span class="sxs-lookup"><span data-stu-id="d51cc-263">Within each z-order, the currently active window appears above all other windows in the same z-order.</span></span>  
  
<a name="WindowSize"></a>
## <a name="window-size"></a><span data-ttu-id="d51cc-264">窗口大小</span><span class="sxs-lookup"><span data-stu-id="d51cc-264">Window Size</span></span>  
 <span data-ttu-id="d51cc-265">除了拥有桌面位置，窗口的大小由多个属性确定，其中包括各种宽度和高度属性以及 <xref:System.Windows.Window.SizeToContent%2A> 。</span><span class="sxs-lookup"><span data-stu-id="d51cc-265">Besides having a desktop location, a window has a size that is determined by several properties, including the various width and height properties and <xref:System.Windows.Window.SizeToContent%2A>.</span></span>  
  
 <span data-ttu-id="d51cc-266"><xref:System.Windows.FrameworkElement.MinWidth%2A>、 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.MaxWidth%2A> 用于管理窗口在其生存期内可以具有的宽度范围，并按以下示例所示进行配置。</span><span class="sxs-lookup"><span data-stu-id="d51cc-266"><xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.MaxWidth%2A> are used to manage the range of widths that a window can have during its lifetime, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 <span data-ttu-id="d51cc-267">窗口高度由 <xref:System.Windows.FrameworkElement.MinHeight%2A> 、 <xref:System.Windows.FrameworkElement.Height%2A> 、和进行管理， <xref:System.Windows.FrameworkElement.MaxHeight%2A> 如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="d51cc-267">Window height is managed by <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, and <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 <span data-ttu-id="d51cc-268">由于各种宽度值和高度值各自指定了一个范围，所以大小可调整大小的窗口的宽度和高度可以是相应维度中指定范围内的任何值。</span><span class="sxs-lookup"><span data-stu-id="d51cc-268">Because the various width values and height values each specify a range, it is possible for the width and height of a resizable window to be anywhere within the specified range for the respective dimension.</span></span> <span data-ttu-id="d51cc-269">若要检测其当前的宽度和高度，请 <xref:System.Windows.FrameworkElement.ActualWidth%2A> 分别检查和 <xref:System.Windows.FrameworkElement.ActualHeight%2A> 。</span><span class="sxs-lookup"><span data-stu-id="d51cc-269">To detect its current width and height, inspect <xref:System.Windows.FrameworkElement.ActualWidth%2A> and <xref:System.Windows.FrameworkElement.ActualHeight%2A>, respectively.</span></span>  
  
 <span data-ttu-id="d51cc-270">如果希望窗口的宽度和高度与窗口内容的大小相符，则可以使用 <xref:System.Windows.Window.SizeToContent%2A> 属性，该属性具有以下各值：</span><span class="sxs-lookup"><span data-stu-id="d51cc-270">If you'd like the width and height of your window to have a size that fits to the size of the window's content, you can use the <xref:System.Windows.Window.SizeToContent%2A> property, which has the following values:</span></span>  
  
- <span data-ttu-id="d51cc-271"><xref:System.Windows.SizeToContent.Manual>.</span><span class="sxs-lookup"><span data-stu-id="d51cc-271"><xref:System.Windows.SizeToContent.Manual>.</span></span> <span data-ttu-id="d51cc-272">不起作用（默认值）。</span><span class="sxs-lookup"><span data-stu-id="d51cc-272">No effect (default).</span></span>  
  
- <span data-ttu-id="d51cc-273"><xref:System.Windows.SizeToContent.Width>.</span><span class="sxs-lookup"><span data-stu-id="d51cc-273"><xref:System.Windows.SizeToContent.Width>.</span></span> <span data-ttu-id="d51cc-274">适应内容宽度，其效果与将 <xref:System.Windows.FrameworkElement.MinWidth%2A> 和设置 <xref:System.Windows.FrameworkElement.MaxWidth%2A> 为内容的宽度相同。</span><span class="sxs-lookup"><span data-stu-id="d51cc-274">Fit to content width, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
- <span data-ttu-id="d51cc-275"><xref:System.Windows.SizeToContent.Height>.</span><span class="sxs-lookup"><span data-stu-id="d51cc-275"><xref:System.Windows.SizeToContent.Height>.</span></span> <span data-ttu-id="d51cc-276">适应内容高度，其效果与将 <xref:System.Windows.FrameworkElement.MinHeight%2A> 和设置 <xref:System.Windows.FrameworkElement.MaxHeight%2A> 为内容的高度相同。</span><span class="sxs-lookup"><span data-stu-id="d51cc-276">Fit to content height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content.</span></span>  
  
- <span data-ttu-id="d51cc-277"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span><span class="sxs-lookup"><span data-stu-id="d51cc-277"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span></span> <span data-ttu-id="d51cc-278">适应内容宽度和高度，其效果与将 <xref:System.Windows.FrameworkElement.MinHeight%2A> 和设置 <xref:System.Windows.FrameworkElement.MaxHeight%2A> 为内容的高度相同，同时将 <xref:System.Windows.FrameworkElement.MinWidth%2A> 和设置 <xref:System.Windows.FrameworkElement.MaxWidth%2A> 为内容的宽度。</span><span class="sxs-lookup"><span data-stu-id="d51cc-278">Fit to content width and height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content, and setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
 <span data-ttu-id="d51cc-279">以下示例显示了一个窗口，它在第一次显示时即自动调整垂直方向和水平方向上的大小以适应内容。</span><span class="sxs-lookup"><span data-stu-id="d51cc-279">The following example shows a window that automatically sizes to fit its content, both vertically and horizontally, when first shown.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 <span data-ttu-id="d51cc-280">下面的示例演示如何 <xref:System.Windows.Window.SizeToContent%2A> 在代码中设置属性，以指定如何调整窗口大小以适应其内容。</span><span class="sxs-lookup"><span data-stu-id="d51cc-280">The following example shows how to set the <xref:System.Windows.Window.SizeToContent%2A> property in code to specify how a window resizes to fit its content    .</span></span>
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>
## <a name="order-of-precedence-for-sizing-properties"></a><span data-ttu-id="d51cc-281">大小调整属性的优先级顺序</span><span class="sxs-lookup"><span data-stu-id="d51cc-281">Order of Precedence for Sizing Properties</span></span>  
 <span data-ttu-id="d51cc-282">从根本上说，窗口的各种大小属性可以结合使用，以定义可调整大小的窗口的宽度和高度范围。</span><span class="sxs-lookup"><span data-stu-id="d51cc-282">Essentially, the various sizes properties of a window combine to define the range of width and height for a resizable window.</span></span> <span data-ttu-id="d51cc-283">若要确保保持有效的范围，请 <xref:System.Windows.Window> 使用以下优先级顺序计算大小属性的值。</span><span class="sxs-lookup"><span data-stu-id="d51cc-283">To ensure a valid range is maintained, <xref:System.Windows.Window> evaluates the values of the size properties using the following orders of precedence.</span></span>  
  
 <span data-ttu-id="d51cc-284">**对于高度属性：**</span><span class="sxs-lookup"><span data-stu-id="d51cc-284">**For Height Properties:**</span></span>  
  
1. <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="d51cc-285">**对于宽度属性：**</span><span class="sxs-lookup"><span data-stu-id="d51cc-285">**For Width Properties:**</span></span>  
  
1. <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="d51cc-286">优先级顺序还可以确定窗口最大化时的窗口大小，该大小是使用属性管理的 <xref:System.Windows.Window.WindowState%2A> 。</span><span class="sxs-lookup"><span data-stu-id="d51cc-286">The order of precedence can also determine the size of a window when it is maximized, which is managed with the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="WindowState"></a>
## <a name="window-state"></a><span data-ttu-id="d51cc-287">窗口状态</span><span class="sxs-lookup"><span data-stu-id="d51cc-287">Window State</span></span>  
 <span data-ttu-id="d51cc-288">可调整大小的窗口在生存期中拥有三种状态：正常、最小化和最大化。</span><span class="sxs-lookup"><span data-stu-id="d51cc-288">During the lifetime of a resizable window, it can have three states: normal, minimized, and maximized.</span></span> <span data-ttu-id="d51cc-289">处于*正常*状态的窗口是窗口的默认状态。</span><span class="sxs-lookup"><span data-stu-id="d51cc-289">A window with a *normal* state is the default state of a window.</span></span> <span data-ttu-id="d51cc-290">这种状态下的窗口允许用户使用重设大小手柄或边框移动窗口和重设其大小（前提是大小可以重设）。</span><span class="sxs-lookup"><span data-stu-id="d51cc-290">A window with this state allows a user to move and resize it by using a resize grip or the border, if it is resizable.</span></span>  
  
 <span data-ttu-id="d51cc-291">如果设置为，则具有*最小化*状态的窗口将折叠到其任务栏按钮 <xref:System.Windows.Window.ShowInTaskbar%2A> `true` ; 否则，它将折叠为可能的最小大小，并将自身重定位到桌面左下角。</span><span class="sxs-lookup"><span data-stu-id="d51cc-291">A window with a *minimized* state collapses to its task bar button if <xref:System.Windows.Window.ShowInTaskbar%2A> is set to `true`; otherwise, it collapses to the smallest possible size it can be and relocates itself to the bottom-left corner of the desktop.</span></span> <span data-ttu-id="d51cc-292">虽然不在任务栏显示的最小化窗口可以在桌面上四处拖动，但这两种类型的最小化窗口都不可以使用边框或重设大小手柄重设窗口大小。</span><span class="sxs-lookup"><span data-stu-id="d51cc-292">Neither type of minimized window can be resized using a border or resize grip, although a minimized window that isn't shown in the task bar can be dragged around the desktop.</span></span>  
  
 <span data-ttu-id="d51cc-293">处于最*大化*状态的窗口将扩展为它的最大大小，这将只是其 <xref:System.Windows.FrameworkElement.MaxWidth%2A> 、 <xref:System.Windows.FrameworkElement.MaxHeight%2A> 和属性所规定的大小 <xref:System.Windows.Window.SizeToContent%2A> 。</span><span class="sxs-lookup"><span data-stu-id="d51cc-293">A window with a *maximized* state expands to the maximum size it can be, which will only be as large as its <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and <xref:System.Windows.Window.SizeToContent%2A> properties dictate.</span></span> <span data-ttu-id="d51cc-294">与最小化窗口一样，最大化窗口无法使用重设大小手柄或通过拖动边框来重设大小。</span><span class="sxs-lookup"><span data-stu-id="d51cc-294">Like a minimized window, a maximized window cannot be resized by using a resize grip or by dragging the border.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d51cc-295"><xref:System.Windows.Window.Top%2A> <xref:System.Windows.Window.Left%2A> <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> 即使窗口当前已最大化或最小化，窗口的、、和属性的值也始终表示正常状态的值。</span><span class="sxs-lookup"><span data-stu-id="d51cc-295">The values of the <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.Height%2A> properties of a window always represent the values for the normal state, even when the window is currently maximized or minimized.</span></span>  
  
 <span data-ttu-id="d51cc-296">窗口的状态可以通过设置其属性来配置 <xref:System.Windows.Window.WindowState%2A> ，该属性可以具有以下 <xref:System.Windows.WindowState> 枚举值之一：</span><span class="sxs-lookup"><span data-stu-id="d51cc-296">The state of a window can be configured by setting its <xref:System.Windows.Window.WindowState%2A> property, which can have one of the following <xref:System.Windows.WindowState> enumeration values:</span></span>  
  
- <span data-ttu-id="d51cc-297"><xref:System.Windows.WindowState.Normal>（默认值）</span><span class="sxs-lookup"><span data-stu-id="d51cc-297"><xref:System.Windows.WindowState.Normal> (default)</span></span>  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 <span data-ttu-id="d51cc-298">以下示例显示如何创建在打开时最大化显示的窗口。</span><span class="sxs-lookup"><span data-stu-id="d51cc-298">The following example shows how to create a window that is shown as maximized when it opens.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 <span data-ttu-id="d51cc-299">通常，应将设置 <xref:System.Windows.Window.WindowState%2A> 为配置窗口的初始状态。</span><span class="sxs-lookup"><span data-stu-id="d51cc-299">In general, you should set <xref:System.Windows.Window.WindowState%2A> to configure the initial state of a window.</span></span> <span data-ttu-id="d51cc-300">显示可调整大小的窗口后，用户可以按窗口标题栏上的“最小化”、“最大化”和“还原”按钮来更改窗口状态。</span><span class="sxs-lookup"><span data-stu-id="d51cc-300">Once a resizable window is shown, users can press the minimize, maximize, and restore buttons on the window's title bar to change the window state.</span></span>  
  
<a name="WindowAppearance"></a>
## <a name="window-appearance"></a><span data-ttu-id="d51cc-301">窗口外观</span><span class="sxs-lookup"><span data-stu-id="d51cc-301">Window Appearance</span></span>  
 <span data-ttu-id="d51cc-302">通过将特定于窗口的内容（例如按钮、标签和文本框）添加到窗口的工作区可以更改它的外观。</span><span class="sxs-lookup"><span data-stu-id="d51cc-302">You change the appearance of the client area of a window by adding window-specific content to it, such as buttons, labels, and text boxes.</span></span> <span data-ttu-id="d51cc-303">若要配置非工作区， <xref:System.Windows.Window> 提供了几个属性，其中包括 <xref:System.Windows.Window.Icon%2A> 设置窗口图标以及 <xref:System.Windows.Window.Title%2A> 设置其标题。</span><span class="sxs-lookup"><span data-stu-id="d51cc-303">To configure the non-client area, <xref:System.Windows.Window> provides several properties, which include <xref:System.Windows.Window.Icon%2A> to set a window's icon and <xref:System.Windows.Window.Title%2A> to set its title.</span></span>  
  
 <span data-ttu-id="d51cc-304">还可以通过配置窗口的重设大小模式、窗口样式，以及窗口是否显示为桌面任务栏中的按钮，更改非工作区边框的外观和行为。</span><span class="sxs-lookup"><span data-stu-id="d51cc-304">You can also change the appearance and behavior of non-client area border by configuring a window's resize mode, window style, and whether it appears as a button in the desktop task bar.</span></span>  

<a name="Resize_Mode"></a>
### <a name="resize-mode"></a><span data-ttu-id="d51cc-305">重设大小模式</span><span class="sxs-lookup"><span data-stu-id="d51cc-305">Resize Mode</span></span>  
 <span data-ttu-id="d51cc-306">根据 <xref:System.Windows.Window.WindowStyle%2A> 属性，您可以控制用户如何（以及用户）如何调整窗口的大小。</span><span class="sxs-lookup"><span data-stu-id="d51cc-306">Depending on the <xref:System.Windows.Window.WindowStyle%2A> property, you can control how (and if) users can resize the window.</span></span> <span data-ttu-id="d51cc-307">窗口样式的选择会影响用户是否可以通过使用鼠标拖动边框来调整窗口的大小，无论是否在非工作区显示 "**最小化**"、"**最大化**" 和 "**调整大小**" 按钮，以及它们是否已启用。</span><span class="sxs-lookup"><span data-stu-id="d51cc-307">The choice of window style affects whether a user can resize the window by dragging its border with the mouse, whether the **Minimize**, **Maximize**, and **Resize** buttons appear on the non-client area, and, if they do appear, whether they are enabled.</span></span>  
  
 <span data-ttu-id="d51cc-308">您可以通过设置窗口的属性来配置窗口调整大小的方式 <xref:System.Windows.Window.ResizeMode%2A> ，可以是下列 <xref:System.Windows.ResizeMode> 枚举值之一：</span><span class="sxs-lookup"><span data-stu-id="d51cc-308">You can configure how a window resizes by setting its <xref:System.Windows.Window.ResizeMode%2A> property, which can be one of the following <xref:System.Windows.ResizeMode> enumeration values:</span></span>  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <span data-ttu-id="d51cc-309"><xref:System.Windows.ResizeMode.CanResize>（默认值）</span><span class="sxs-lookup"><span data-stu-id="d51cc-309"><xref:System.Windows.ResizeMode.CanResize> (default)</span></span>  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 <span data-ttu-id="d51cc-310">与一样 <xref:System.Windows.Window.WindowStyle%2A> ，窗口的重设大小模式不太可能在其生存期内发生更改，这意味着你很可能会从标记中进行设置 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d51cc-310">As with <xref:System.Windows.Window.WindowStyle%2A>, the resize mode of a window is unlikely to change during its lifetime, which means that you'll most likely set it from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 <span data-ttu-id="d51cc-311">请注意，可以通过检查属性来检测窗口是最大化、最小化还是已还原 <xref:System.Windows.Window.WindowState%2A> 。</span><span class="sxs-lookup"><span data-stu-id="d51cc-311">Note that you can detect whether a window is maximized, minimized, or restored by inspecting the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="Window_Style"></a>
### <a name="window-style"></a><span data-ttu-id="d51cc-312">窗口样式</span><span class="sxs-lookup"><span data-stu-id="d51cc-312">Window Style</span></span>  
 <span data-ttu-id="d51cc-313">从窗口非工作区公开的边框适用于大多数应用程序。</span><span class="sxs-lookup"><span data-stu-id="d51cc-313">The border that is exposed from the non-client area of a window is suitable for most applications.</span></span> <span data-ttu-id="d51cc-314">但是，有时候会需要不同类型的边框，或者根本不需要边框，具体取决于窗口类型。</span><span class="sxs-lookup"><span data-stu-id="d51cc-314">However, there are circumstances where different types of borders are needed, or no borders are needed at all, depending on the type of window.</span></span>  
  
 <span data-ttu-id="d51cc-315">若要控制窗口的边框类型，请将其属性设置 <xref:System.Windows.Window.WindowStyle%2A> 为以下枚举值之一 <xref:System.Windows.WindowStyle> ：</span><span class="sxs-lookup"><span data-stu-id="d51cc-315">To control what type of border a window gets, you set its <xref:System.Windows.Window.WindowStyle%2A> property with one of the following values of the <xref:System.Windows.WindowStyle> enumeration:</span></span>  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <span data-ttu-id="d51cc-316"><xref:System.Windows.WindowStyle.SingleBorderWindow>（默认值）</span><span class="sxs-lookup"><span data-stu-id="d51cc-316"><xref:System.Windows.WindowStyle.SingleBorderWindow> (default)</span></span>  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 <span data-ttu-id="d51cc-317">下图演示了这些窗口样式的效果：</span><span class="sxs-lookup"><span data-stu-id="d51cc-317">The effect of these window styles are illustrated in the following figure:</span></span>  
  
 ![窗口边框样式的插图。](./media/wpf-windows-overview/window-border-styles.png)  
  
 <span data-ttu-id="d51cc-319">您可以 <xref:System.Windows.Window.WindowStyle%2A> 使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 标记或代码进行设置; 因为在窗口生存期内不太可能更改，因此您最有可能使用标记对其进行配置 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d51cc-319">You can set <xref:System.Windows.Window.WindowStyle%2A> using either [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup or code; because it is unlikely to change during the lifetime of a window, you will most likely configure it using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a><span data-ttu-id="d51cc-320">非矩形窗口样式</span><span class="sxs-lookup"><span data-stu-id="d51cc-320">Non-Rectangular Window Style</span></span>  
 <span data-ttu-id="d51cc-321">在某些情况下， <xref:System.Windows.Window.WindowStyle%2A> 允许您使用的边框样式并不够。</span><span class="sxs-lookup"><span data-stu-id="d51cc-321">There are also situations where the border styles that <xref:System.Windows.Window.WindowStyle%2A> allows you to have are not sufficient.</span></span> <span data-ttu-id="d51cc-322">例如，你可能想要创建一个具有非矩形边框的应用程序，如 Microsoft Windows Media Player 使用。</span><span class="sxs-lookup"><span data-stu-id="d51cc-322">For example, you may want to create an application with a non-rectangular border, like Microsoft Windows Media Player uses.</span></span>  
  
 <span data-ttu-id="d51cc-323">例如，请看下图中显示的语音气泡窗口：</span><span class="sxs-lookup"><span data-stu-id="d51cc-323">For example, consider the speech bubble window shown in the following figure:</span></span>  
  
 ![显示 "拖动" 的语音气泡窗口。](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 <span data-ttu-id="d51cc-325">可以通过将 <xref:System.Windows.Window.WindowStyle%2A> 属性设置为 <xref:System.Windows.WindowStyle.None> ，并使用具有透明度的特殊支持来创建此类型的窗口 <xref:System.Windows.Window> 。</span><span class="sxs-lookup"><span data-stu-id="d51cc-325">This type of window can be created by setting the <xref:System.Windows.Window.WindowStyle%2A> property to <xref:System.Windows.WindowStyle.None>, and by using special support that <xref:System.Windows.Window> has for transparency.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 <span data-ttu-id="d51cc-326">多个值组合起来可以指示窗口呈现完全透明的效果。</span><span class="sxs-lookup"><span data-stu-id="d51cc-326">This combination of values instructs the window to render completely transparent.</span></span> <span data-ttu-id="d51cc-327">在这种状态下，无法使用窗口的非工作区修饰（“关闭”菜单，“最小化”、“最大化”和“还原”按钮等）。</span><span class="sxs-lookup"><span data-stu-id="d51cc-327">In this state, the window's non-client area adornments (the Close menu, Minimize, Maximize, and Restore buttons, and so on) cannot be used.</span></span> <span data-ttu-id="d51cc-328">因此，需要提供自己的修饰。</span><span class="sxs-lookup"><span data-stu-id="d51cc-328">Consequently, you need to provide your own.</span></span>  
  
<a name="Task_Bar_Presence"></a>
### <a name="task-bar-presence"></a><span data-ttu-id="d51cc-329">任务栏显示</span><span class="sxs-lookup"><span data-stu-id="d51cc-329">Task Bar Presence</span></span>  

<span data-ttu-id="d51cc-330">窗口的默认外观包含一个任务栏按钮，如下图中所示：</span><span class="sxs-lookup"><span data-stu-id="d51cc-330">The default appearance of a window includes a taskbar button, like the one shown in the following figure:</span></span>

 ![显示具有任务栏按钮的窗口的屏幕截图。](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 <span data-ttu-id="d51cc-332">某些类型的 windows 没有任务栏按钮，如消息框和对话框（请参阅[对话框概述](dialog-boxes-overview.md)）。</span><span class="sxs-lookup"><span data-stu-id="d51cc-332">Some types of windows don't have a task bar button, such as message boxes and dialog boxes (see [Dialog Boxes Overview](dialog-boxes-overview.md)).</span></span> <span data-ttu-id="d51cc-333">您可以通过设置 <xref:System.Windows.Window.ShowInTaskbar%2A> 属性（ `true` 默认情况下）来控制是否显示窗口的任务栏按钮。</span><span class="sxs-lookup"><span data-stu-id="d51cc-333">You can control whether the task bar button for a window is shown by setting the <xref:System.Windows.Window.ShowInTaskbar%2A> property (`true` by default).</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>
## <a name="security-considerations"></a><span data-ttu-id="d51cc-334">安全注意事项</span><span class="sxs-lookup"><span data-stu-id="d51cc-334">Security Considerations</span></span>  
 <span data-ttu-id="d51cc-335"><xref:System.Windows.Window>需要 `UnmanagedCode` 实例化安全权限。</span><span class="sxs-lookup"><span data-stu-id="d51cc-335"><xref:System.Windows.Window> requires `UnmanagedCode` security permission to be instantiated.</span></span> <span data-ttu-id="d51cc-336">对于从本地计算机安装并启动的应用程序，此权限在授予应用程序的权限集中。</span><span class="sxs-lookup"><span data-stu-id="d51cc-336">For applications installed on and launched from the local machine, this falls within the set of permissions that are granted to the application.</span></span>  
  
 <span data-ttu-id="d51cc-337">但是，这超出了向使用 ClickOnce 从 Internet 或本地 intranet 区域启动的应用程序授予的权限集。</span><span class="sxs-lookup"><span data-stu-id="d51cc-337">However, this falls outside the set of permissions granted to applications that are launched from the Internet or Local intranet zone using ClickOnce.</span></span> <span data-ttu-id="d51cc-338">因此，用户将收到 ClickOnce 安全警告，需要将应用程序的权限集提升到完全信任。</span><span class="sxs-lookup"><span data-stu-id="d51cc-338">Consequently, users will receive a ClickOnce security warning and will need to elevate the permission set for the application to full trust.</span></span>  
  
 <span data-ttu-id="d51cc-339">此外，默认情况下，Xbap 不能显示窗口或对话框。</span><span class="sxs-lookup"><span data-stu-id="d51cc-339">Additionally, XBAPs cannot show windows or dialog boxes by default.</span></span> <span data-ttu-id="d51cc-340">有关独立应用程序安全注意事项的讨论，请参阅[WPF 安全策略-平台安全性](../wpf-security-strategy-platform-security.md)。</span><span class="sxs-lookup"><span data-stu-id="d51cc-340">For a discussion on standalone application security considerations, see [WPF Security Strategy - Platform Security](../wpf-security-strategy-platform-security.md).</span></span>  
  
<a name="Other_Types_of_Windows"></a>
## <a name="other-types-of-windows"></a><span data-ttu-id="d51cc-341">其他类型的窗口</span><span class="sxs-lookup"><span data-stu-id="d51cc-341">Other Types of Windows</span></span>  
 <span data-ttu-id="d51cc-342"><xref:System.Windows.Navigation.NavigationWindow>是旨在承载可导航内容的窗口。</span><span class="sxs-lookup"><span data-stu-id="d51cc-342"><xref:System.Windows.Navigation.NavigationWindow> is a window that is designed to host navigable content.</span></span> <span data-ttu-id="d51cc-343">有关详细信息，请参阅[导航概述](navigation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d51cc-343">For more information, see [Navigation Overview](navigation-overview.md)).</span></span>  
  
 <span data-ttu-id="d51cc-344">对话框是通常用来收集用户信息以完成某项功能的窗口。</span><span class="sxs-lookup"><span data-stu-id="d51cc-344">Dialog boxes are windows that are often used to gather information from a user to complete a function.</span></span> <span data-ttu-id="d51cc-345">例如，当用户要打开文件时，应用程序通常会显示 "**打开文件**" 对话框以获取用户的文件名。</span><span class="sxs-lookup"><span data-stu-id="d51cc-345">For example, when a user wants to open a file, the **Open File** dialog box is usually displayed by an application to get the file name from the user.</span></span> <span data-ttu-id="d51cc-346">有关详细信息，请参阅[对话框概述](dialog-boxes-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d51cc-346">For more information, see [Dialog Boxes Overview](dialog-boxes-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d51cc-347">请参阅</span><span class="sxs-lookup"><span data-stu-id="d51cc-347">See also</span></span>

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [<span data-ttu-id="d51cc-348">对话框概述</span><span class="sxs-lookup"><span data-stu-id="d51cc-348">Dialog Boxes Overview</span></span>](dialog-boxes-overview.md)
- [<span data-ttu-id="d51cc-349">生成 WPF 应用程序</span><span class="sxs-lookup"><span data-stu-id="d51cc-349">Building a WPF Application</span></span>](building-a-wpf-application-wpf.md)

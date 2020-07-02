---
title: 导航概述
description: 了解在 Windows Presentation Foundation （WPF）中的独立应用程序和 XAML 浏览器应用程序中使用的浏览器样式的导航支持。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- loose XAML files [WPF]
- windows [WPF]
- Start page [WPF]
- HTML files [WPF]
- structured navigation [WPF]
- fragment navigation [WPF]
- URIs (Uniform Resource Identifiers)
- custom objects [WPF]
- Uniform Resource Identifiers (URIs)
- pages [WPF]
- frames [WPF]
- navigation hosts [WPF]
- journals [WPF]
- lifetimes [WPF]
- retaining content state [WPF]
- content state [WPF]
- programmatic navigation [WPF]
- hyperlinks [WPF]
ms.assetid: 86ad2143-606a-4e34-bf7e-51a2594248b8
ms.openlocfilehash: 2aac1b3a38b6240bfba1b90983fd9cbd18b31b6f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621699"
---
# <a name="navigation-overview"></a><span data-ttu-id="1e267-103">导航概述</span><span class="sxs-lookup"><span data-stu-id="1e267-103">Navigation Overview</span></span>

<span data-ttu-id="1e267-104">Windows Presentation Foundation （WPF）支持可在两种类型的应用程序中使用的浏览器样式的导航：独立应用程序和 XAML 浏览器应用程序（Xbap）。</span><span class="sxs-lookup"><span data-stu-id="1e267-104">Windows Presentation Foundation (WPF) supports browser-style navigation that can be used in two types of applications: standalone applications and XAML browser applications (XBAPs).</span></span> <span data-ttu-id="1e267-105">为了打包导航内容，WPF 提供了 <xref:System.Windows.Controls.Page> 类。</span><span class="sxs-lookup"><span data-stu-id="1e267-105">To package content for navigation, WPF provides the <xref:System.Windows.Controls.Page> class.</span></span> <span data-ttu-id="1e267-106">您可以通过 <xref:System.Windows.Controls.Page> 使用或以编程方式使用从一个导航到另一个 <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Navigation.NavigationService> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-106">You can navigate from one <xref:System.Windows.Controls.Page> to another declaratively, by using a <xref:System.Windows.Documents.Hyperlink>, or programmatically, by using the <xref:System.Windows.Navigation.NavigationService>.</span></span> <span data-ttu-id="1e267-107">WPF 使用日记来记住已从导航的页面，并向后导航到它们。</span><span class="sxs-lookup"><span data-stu-id="1e267-107">WPF uses the journal to remember pages that have been navigated from and to navigate back to them.</span></span>

<span data-ttu-id="1e267-108"><xref:System.Windows.Controls.Page>、 <xref:System.Windows.Documents.Hyperlink> 、 <xref:System.Windows.Navigation.NavigationService> 和日志构成了由 WPF 提供的导航支持的核心。</span><span class="sxs-lookup"><span data-stu-id="1e267-108"><xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Navigation.NavigationService>, and the journal form the core of the navigation support offered by WPF.</span></span> <span data-ttu-id="1e267-109">本概述首先详细探讨这些功能，然后介绍高级导航支持，其中包括导航到松散 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 文件、HTML 文件和对象。</span><span class="sxs-lookup"><span data-stu-id="1e267-109">This overview explores these features in detail before covering advanced navigation support that includes navigation to loose [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] files, HTML files, and objects.</span></span>

> [!NOTE]
> <span data-ttu-id="1e267-110">在本主题中，术语 "浏览器" 只引用可以承载 WPF 应用程序的浏览器，当前包括 Microsoft Internet Explorer 和 Firefox。</span><span class="sxs-lookup"><span data-stu-id="1e267-110">In this topic, the term "browser" refers only to browsers that can host WPF applications, which currently includes Microsoft Internet Explorer and Firefox.</span></span> <span data-ttu-id="1e267-111">只有特定的浏览器支持特定 WPF 功能的情况下，浏览器版本被引用。</span><span class="sxs-lookup"><span data-stu-id="1e267-111">Where specific WPF features are supported only by a particular browser, the browser version is referred to.</span></span>

## <a name="navigation-in-wpf-applications"></a><span data-ttu-id="1e267-112">WPF 应用程序中的导航</span><span class="sxs-lookup"><span data-stu-id="1e267-112">Navigation in WPF Applications</span></span>

<span data-ttu-id="1e267-113">本主题提供有关 WPF 中的主要导航功能的概述。</span><span class="sxs-lookup"><span data-stu-id="1e267-113">This topic provides an overview of the key navigation capabilities in WPF.</span></span> <span data-ttu-id="1e267-114">这些功能适用于独立应用程序和 Xbap，不过，本主题在 XBAP 的上下文中提供了这些功能。</span><span class="sxs-lookup"><span data-stu-id="1e267-114">These capabilities are available to both standalone applications and XBAPs, although this topic presents them within the context of an XBAP.</span></span>

> [!NOTE]
> <span data-ttu-id="1e267-115">本主题不讨论如何生成和部署 Xbap。</span><span class="sxs-lookup"><span data-stu-id="1e267-115">This topic doesn't discuss how to build and deploy XBAPs.</span></span> <span data-ttu-id="1e267-116">有关 Xbap 的详细信息，请参阅[WPF XAML 浏览器应用程序概述](wpf-xaml-browser-applications-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="1e267-116">For more information on XBAPs, see [WPF XAML Browser Applications Overview](wpf-xaml-browser-applications-overview.md).</span></span>

<span data-ttu-id="1e267-117">本节解释并演示导航的以下方面：</span><span class="sxs-lookup"><span data-stu-id="1e267-117">This section explains and demonstrates the following aspects of navigation:</span></span>

- [<span data-ttu-id="1e267-118">实现页</span><span class="sxs-lookup"><span data-stu-id="1e267-118">Implementing a Page</span></span>](#CreatingAXAMLPage)

- [<span data-ttu-id="1e267-119">配置起始页</span><span class="sxs-lookup"><span data-stu-id="1e267-119">Configuring a Start Page</span></span>](#Configuring_a_Start_Page)

- [<span data-ttu-id="1e267-120">配置主机窗口的标题、宽度和高度</span><span class="sxs-lookup"><span data-stu-id="1e267-120">Configuring the Host Window's Title, Width, and Height</span></span>](#ConfiguringAXAMLPage)

- [<span data-ttu-id="1e267-121">超链接导航</span><span class="sxs-lookup"><span data-stu-id="1e267-121">Hyperlink Navigation</span></span>](#NavigatingBetweenXAMLPages)

- [<span data-ttu-id="1e267-122">片段导航</span><span class="sxs-lookup"><span data-stu-id="1e267-122">Fragment Navigation</span></span>](#FragmentNavigation)

- [<span data-ttu-id="1e267-123">导航服务</span><span class="sxs-lookup"><span data-stu-id="1e267-123">Navigation Service</span></span>](#NavigationService)

- [<span data-ttu-id="1e267-124">使用导航服务以编程方式导航</span><span class="sxs-lookup"><span data-stu-id="1e267-124">Programmatic Navigation with the Navigation Service</span></span>](#Programmatic_Navigation_with_the_Navigation_Service)

- [<span data-ttu-id="1e267-125">导航生存期</span><span class="sxs-lookup"><span data-stu-id="1e267-125">Navigation Lifetime</span></span>](#Navigation_Lifetime)

- [<span data-ttu-id="1e267-126">使用日志记住导航</span><span class="sxs-lookup"><span data-stu-id="1e267-126">Remembering Navigation with the Journal</span></span>](#NavigationHistory)

- [<span data-ttu-id="1e267-127">页生存期和日志</span><span class="sxs-lookup"><span data-stu-id="1e267-127">Page Lifetime and the Journal</span></span>](#PageLifetime)

- [<span data-ttu-id="1e267-128">保留导航历史记录的内容状态</span><span class="sxs-lookup"><span data-stu-id="1e267-128">Retaining Content State with Navigation History</span></span>](#RetainingContentStateWithNavigationHistory)

- [<span data-ttu-id="1e267-129">Cookie</span><span class="sxs-lookup"><span data-stu-id="1e267-129">Cookies</span></span>](#Cookies)

- [<span data-ttu-id="1e267-130">结构化导航</span><span class="sxs-lookup"><span data-stu-id="1e267-130">Structured Navigation</span></span>](#Structured_Navigation)

<a name="CreatingAXAMLPage"></a>

### <a name="implementing-a-page"></a><span data-ttu-id="1e267-131">实现页</span><span class="sxs-lookup"><span data-stu-id="1e267-131">Implementing a Page</span></span>

<span data-ttu-id="1e267-132">在 WPF 中，可以导航到多个内容类型，其中包括 .NET Framework 对象、自定义对象、枚举值、用户控件、 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 文件和 HTML 文件。</span><span class="sxs-lookup"><span data-stu-id="1e267-132">In WPF, you can navigate to several content types that include .NET Framework objects, custom objects, enumeration values, user controls, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files, and HTML files.</span></span> <span data-ttu-id="1e267-133">不过，你会发现打包内容最常见和最方便的方法是使用 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-133">However, you'll find that the most common and convenient way to package content is by using <xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="1e267-134">此外，还 <xref:System.Windows.Controls.Page> 实现了特定于导航的功能，以增强其外观并简化开发。</span><span class="sxs-lookup"><span data-stu-id="1e267-134">Furthermore, <xref:System.Windows.Controls.Page> implements navigation-specific features to enhance their appearance and simplify development.</span></span>

<span data-ttu-id="1e267-135">使用 <xref:System.Windows.Controls.Page> ，可以通过使用如下所示的标记以声明方式实现可导航的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 内容页。</span><span class="sxs-lookup"><span data-stu-id="1e267-135">Using <xref:System.Windows.Controls.Page>, you can declaratively implement a navigable page of [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content by using markup like the following.</span></span>

[!code-xaml[NavigationOverviewSnippets#Page1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page1.xaml#page1xaml)]

<span data-ttu-id="1e267-136"><xref:System.Windows.Controls.Page>在标记中实现的将 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] `Page` 作为其根元素，并且需要 WPF XML 命名空间声明。</span><span class="sxs-lookup"><span data-stu-id="1e267-136">A <xref:System.Windows.Controls.Page> that is implemented in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup has `Page` as its root element and requires the WPF XML namespace declaration.</span></span> <span data-ttu-id="1e267-137">`Page`元素包含要导航并显示的内容。</span><span class="sxs-lookup"><span data-stu-id="1e267-137">The `Page` element contains the content that you want to navigate to and display.</span></span> <span data-ttu-id="1e267-138">可以通过设置属性元素来添加内容 `Page.Content` ，如以下标记所示。</span><span class="sxs-lookup"><span data-stu-id="1e267-138">You add content by setting the `Page.Content` property element, as shown in the following markup.</span></span>

[!code-xaml[NavigationOverviewSnippets#Page2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page2.xaml#page2xaml)]

<span data-ttu-id="1e267-139">`Page.Content` 只能包含一个子元素，在前面的实例中，内容是一个单独的字符串“Hello, Page!”。</span><span class="sxs-lookup"><span data-stu-id="1e267-139">`Page.Content` can only contain one child element; in the preceding example, the content is a single string, "Hello, Page!"</span></span> <span data-ttu-id="1e267-140">在实践中，通常会使用布局控件作为子元素（请参阅[布局](../advanced/layout.md)）来包含内容并撰写内容。</span><span class="sxs-lookup"><span data-stu-id="1e267-140">In practice, you will usually use a layout control as the child element (see [Layout](../advanced/layout.md)) to contain and compose your content.</span></span>

<span data-ttu-id="1e267-141">元素的子元素被 `Page` 视为和的内容 <xref:System.Windows.Controls.Page> ，因此，不需要使用显式 `Page.Content` 声明。</span><span class="sxs-lookup"><span data-stu-id="1e267-141">The child elements of a `Page` element are considered to be the content of a <xref:System.Windows.Controls.Page> and, consequently, you don't need to use the explicit `Page.Content` declaration.</span></span> <span data-ttu-id="1e267-142">以下标记和前面的示例在声明上是等效的。</span><span class="sxs-lookup"><span data-stu-id="1e267-142">The following markup is the declarative equivalent to the preceding sample.</span></span>

[!code-xaml[NavigationOverviewSnippets#Page3XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page3.xaml#page3xaml)]

<span data-ttu-id="1e267-143">在这种情况下， `Page.Content` 将自动设置为元素的子元素 `Page` 。</span><span class="sxs-lookup"><span data-stu-id="1e267-143">In this case, `Page.Content` is automatically set with the child elements of the `Page` element.</span></span> <span data-ttu-id="1e267-144">有关详细信息，请参阅 [WPF 内容模型](../controls/wpf-content-model.md)。</span><span class="sxs-lookup"><span data-stu-id="1e267-144">For more information, see [WPF Content Model](../controls/wpf-content-model.md).</span></span>

<span data-ttu-id="1e267-145">仅标记 <xref:System.Windows.Controls.Page> 可用于显示内容。</span><span class="sxs-lookup"><span data-stu-id="1e267-145">A markup-only <xref:System.Windows.Controls.Page> is useful for displaying content.</span></span> <span data-ttu-id="1e267-146">但是， <xref:System.Windows.Controls.Page> 还可以显示允许用户与页面交互的控件，并且它可以通过处理事件和调用应用程序逻辑来响应用户交互。</span><span class="sxs-lookup"><span data-stu-id="1e267-146">However, a <xref:System.Windows.Controls.Page> can also display controls that allow users to interact with the page, and it can respond to user interaction by handling events and calling application logic.</span></span> <span data-ttu-id="1e267-147">交互式 <xref:System.Windows.Controls.Page> 是通过结合使用标记和代码隐藏来实现的，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="1e267-147">An interactive <xref:System.Windows.Controls.Page> is implemented by using a combination of markup and code-behind, as shown in the following example.</span></span>

[!code-xaml[XBAPAppDefSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml#homepagemarkup)]

[!code-csharp[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml.cs#homepagecodebehind)]
[!code-vb[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/HomePage.xaml.vb#homepagecodebehind)]

<span data-ttu-id="1e267-148">要允许标记文件和代码隐藏文件协同工作，需要进行以下配置：</span><span class="sxs-lookup"><span data-stu-id="1e267-148">To allow a markup file and code-behind file to work together, the following configuration is required:</span></span>

- <span data-ttu-id="1e267-149">在标记中， `Page` 元素必须包含 `x:Class` 属性。</span><span class="sxs-lookup"><span data-stu-id="1e267-149">In markup, the `Page` element must include the `x:Class` attribute.</span></span> <span data-ttu-id="1e267-150">生成应用程序后， `x:Class` 标记文件中存在会导致 Microsoft 生成引擎（MSBuild）创建一个 `partial` 派生自的类， <xref:System.Windows.Controls.Page> 并具有由特性指定的名称 `x:Class` 。</span><span class="sxs-lookup"><span data-stu-id="1e267-150">When the application is built, the existence of `x:Class` in the markup file causes Microsoft build engine (MSBuild) to create a `partial` class that derives from <xref:System.Windows.Controls.Page> and has the name that is specified by the `x:Class` attribute.</span></span> <span data-ttu-id="1e267-151">这要求为架构（）添加 XML 命名空间声明 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` 。</span><span class="sxs-lookup"><span data-stu-id="1e267-151">This requires the addition of an XML namespace declaration for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schema ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).</span></span> <span data-ttu-id="1e267-152">生成的 `partial` 类实现 `InitializeComponent` ，调用它来注册事件并设置标记中实现的属性。</span><span class="sxs-lookup"><span data-stu-id="1e267-152">The generated `partial` class implements `InitializeComponent`, which is called to register the events and set the properties that are implemented in markup.</span></span>

- <span data-ttu-id="1e267-153">在代码隐藏中，类必须是 `partial` 由标记中的特性指定的同名类 `x:Class` ，并且必须派生自 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-153">In code-behind, the class must be a `partial` class with the same name that is specified by the `x:Class` attribute in markup, and it must derive from <xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="1e267-154">这允许在生成应用程序时将代码隐藏文件与为 `partial` 标记文件生成的类相关联（请参阅[生成 WPF 应用程序](building-a-wpf-application-wpf.md)）。</span><span class="sxs-lookup"><span data-stu-id="1e267-154">This allows the code-behind file to be associated with the `partial` class that is generated for the markup file when the application is built (see [Building a WPF Application](building-a-wpf-application-wpf.md)).</span></span>

- <span data-ttu-id="1e267-155">在代码隐藏中， <xref:System.Windows.Controls.Page> 该类必须实现调用方法的构造函数 `InitializeComponent` 。</span><span class="sxs-lookup"><span data-stu-id="1e267-155">In code-behind, the <xref:System.Windows.Controls.Page> class must implement a constructor that calls the `InitializeComponent` method.</span></span> <span data-ttu-id="1e267-156">`InitializeComponent`由标记文件的生成类实现， `partial` 用于注册事件和设置在标记中定义的属性。</span><span class="sxs-lookup"><span data-stu-id="1e267-156">`InitializeComponent` is implemented by the markup file's generated `partial` class to register events and set properties that are defined in markup.</span></span>

> [!NOTE]
> <span data-ttu-id="1e267-157"><xref:System.Windows.Controls.Page>使用 Visual Studio 将新添加到项目时，将 <xref:System.Windows.Controls.Page> 使用标记和代码隐藏来实现，并且它包括必要的配置以创建标记和代码隐藏文件之间的关联，如此处所述。</span><span class="sxs-lookup"><span data-stu-id="1e267-157">When you add a new <xref:System.Windows.Controls.Page> to your project using Visual Studio, the <xref:System.Windows.Controls.Page> is implemented using both markup and code-behind, and it includes the necessary configuration to create the association between the markup and code-behind files as described here.</span></span>

<span data-ttu-id="1e267-158">获得之后 <xref:System.Windows.Controls.Page> ，可以导航到它。</span><span class="sxs-lookup"><span data-stu-id="1e267-158">Once you have a <xref:System.Windows.Controls.Page>, you can navigate to it.</span></span> <span data-ttu-id="1e267-159">若要指定 <xref:System.Windows.Controls.Page> 应用程序导航到的第一个，需要配置启动 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-159">To specify the first <xref:System.Windows.Controls.Page> that an application navigates to, you need to configure the start <xref:System.Windows.Controls.Page>.</span></span>

<a name="Configuring_a_Start_Page"></a>

### <a name="configuring-a-start-page"></a><span data-ttu-id="1e267-160">配置起始页</span><span class="sxs-lookup"><span data-stu-id="1e267-160">Configuring a Start Page</span></span>

<span data-ttu-id="1e267-161">Xbap 需要在浏览器中托管一定数量的应用程序基础结构。</span><span class="sxs-lookup"><span data-stu-id="1e267-161">XBAPs require a certain amount of application infrastructure to be hosted in a browser.</span></span> <span data-ttu-id="1e267-162">在 WPF 中， <xref:System.Windows.Application> 类是建立所需的应用程序基础结构的应用程序定义的一部分（请参阅[应用程序管理概述](application-management-overview.md)）。</span><span class="sxs-lookup"><span data-stu-id="1e267-162">In WPF, the <xref:System.Windows.Application> class is part of an application definition that establishes the required application infrastructure (see [Application Management Overview](application-management-overview.md)).</span></span>

<span data-ttu-id="1e267-163">通常使用标记和代码隐藏来实现应用程序定义，并将标记文件配置为 MSBuild `ApplicationDefinition` 项。</span><span class="sxs-lookup"><span data-stu-id="1e267-163">An application definition is usually implemented using both markup and code-behind, with the markup file configured as an MSBuild`ApplicationDefinition` item.</span></span> <span data-ttu-id="1e267-164">下面是 XBAP 的应用程序定义。</span><span class="sxs-lookup"><span data-stu-id="1e267-164">The following is an application definition for an XBAP.</span></span>

[!code-xaml[XBAPAppDefSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

[!code-csharp[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml.cs#xbapapplicationdefinitioncodebehind)]
[!code-vb[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/Application.xaml.vb#xbapapplicationdefinitioncodebehind)]

<span data-ttu-id="1e267-165">XBAP 可以使用其应用程序定义来指定 start <xref:System.Windows.Controls.Page> ，这是在 <xref:System.Windows.Controls.Page> 启动 XBAP 时自动加载的。</span><span class="sxs-lookup"><span data-stu-id="1e267-165">An XBAP can use its application definition to specify a start <xref:System.Windows.Controls.Page>, which is the <xref:System.Windows.Controls.Page> that is automatically loaded when the XBAP is launched.</span></span> <span data-ttu-id="1e267-166">为此，可将 <xref:System.Windows.Application.StartupUri%2A> 属性设置为所需的统一资源标识符（URI） <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-166">You do this by setting the <xref:System.Windows.Application.StartupUri%2A> property with the uniform resource identifier (URI) for the desired <xref:System.Windows.Controls.Page>.</span></span>

> [!NOTE]
> <span data-ttu-id="1e267-167">在大多数情况下，将 <xref:System.Windows.Controls.Page> 编译到应用程序中或与应用程序一起部署。</span><span class="sxs-lookup"><span data-stu-id="1e267-167">In most cases, the <xref:System.Windows.Controls.Page> is either compiled into or deployed with an application.</span></span> <span data-ttu-id="1e267-168">在这些情况下，标识的 URI <xref:System.Windows.Controls.Page> 是一个包 uri，它是符合*pack*方案的 uri。</span><span class="sxs-lookup"><span data-stu-id="1e267-168">In these cases, the URI that identifies a <xref:System.Windows.Controls.Page> is a pack URI, which is a URI that conforms to the *pack* scheme.</span></span> <span data-ttu-id="1e267-169">WPF 中的[Pack uri](pack-uris-in-wpf.md)进一步讨论了包 uri。</span><span class="sxs-lookup"><span data-stu-id="1e267-169">Pack URIs are discussed further in     [Pack URIs in WPF](pack-uris-in-wpf.md).</span></span> <span data-ttu-id="1e267-170">也可使用 http 方案导航到内容，这将在以下内容中讨论。</span><span class="sxs-lookup"><span data-stu-id="1e267-170">You can also navigate to content using the http scheme, which is discussed below.</span></span>

<span data-ttu-id="1e267-171">您可以 <xref:System.Windows.Application.StartupUri%2A> 在标记中以声明方式进行设置，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="1e267-171">You can set <xref:System.Windows.Application.StartupUri%2A> declaratively in markup, as shown in the following example.</span></span>

[!code-xaml[NavigationOverviewSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

<span data-ttu-id="1e267-172">在此示例中， `StartupUri` 使用标识主页的相对 PACK URI 设置特性。</span><span class="sxs-lookup"><span data-stu-id="1e267-172">In this example, the `StartupUri` attribute is set with a relative pack URI that identifies HomePage.xaml.</span></span> <span data-ttu-id="1e267-173">启动 XBAP 后，会自动导航到并显示 "主页"。</span><span class="sxs-lookup"><span data-stu-id="1e267-173">When the XBAP is launched, HomePage.xaml is automatically navigated to and displayed.</span></span> <span data-ttu-id="1e267-174">下图对此进行了演示，其中显示了从 Web 服务器启动的 XBAP。</span><span class="sxs-lookup"><span data-stu-id="1e267-174">This is demonstrated by the following figure, which shows an XBAP that was launched from a Web server.</span></span>

<span data-ttu-id="1e267-175">![XBAP 页](./media/navigation-overview/xbap-launched-from-a-web-server.png "这会显示从 Web 服务器启动的 XBAP。")</span><span class="sxs-lookup"><span data-stu-id="1e267-175">![XBAP page](./media/navigation-overview/xbap-launched-from-a-web-server.png "This shows an XBAP launched from a Web server.")</span></span>

> [!NOTE]
> <span data-ttu-id="1e267-176">有关开发和部署 Xbap 的详细信息，请参阅[WPF XAML 浏览器应用程序概述](wpf-xaml-browser-applications-overview.md)和[部署 WPF 应用程序](deploying-a-wpf-application-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="1e267-176">For more information regarding the development and deployment of XBAPs, see [WPF XAML Browser Applications Overview](wpf-xaml-browser-applications-overview.md) and     [Deploying a WPF Application](deploying-a-wpf-application-wpf.md).</span></span>

<a name="ConfiguringAXAMLPage"></a>

### <a name="configuring-the-host-windows-title-width-and-height"></a><span data-ttu-id="1e267-177">配置主机窗口的标题、宽度和高度</span><span class="sxs-lookup"><span data-stu-id="1e267-177">Configuring the Host Window's Title, Width, and Height</span></span>

<span data-ttu-id="1e267-178">您从上图中可以看到的一件事情是，浏览器和选项卡面板的标题都是 XBAP 的 URI。</span><span class="sxs-lookup"><span data-stu-id="1e267-178">One thing you may have noticed from the previous figure is that the title of both the browser and the tab panel is the URI for the XBAP.</span></span> <span data-ttu-id="1e267-179">除了长，标题既没什么吸引力也没什么帮助。</span><span class="sxs-lookup"><span data-stu-id="1e267-179">Besides being long, the title is neither attractive nor informative.</span></span> <span data-ttu-id="1e267-180">出于此原因，我们 <xref:System.Windows.Controls.Page> 提供了一种方法，用于通过设置属性来更改标题 <xref:System.Windows.Controls.Page.WindowTitle%2A> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-180">For this reason, <xref:System.Windows.Controls.Page> offers a way for you to change the title by setting the <xref:System.Windows.Controls.Page.WindowTitle%2A> property.</span></span> <span data-ttu-id="1e267-181">此外，您还可以通过分别设置和来配置浏览器窗口的宽度和高度 <xref:System.Windows.Controls.Page.WindowWidth%2A> <xref:System.Windows.Controls.Page.WindowHeight%2A> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-181">Furthermore, you can configure the width and height of the browser window by setting <xref:System.Windows.Controls.Page.WindowWidth%2A> and <xref:System.Windows.Controls.Page.WindowHeight%2A>, respectively.</span></span>

<span data-ttu-id="1e267-182"><xref:System.Windows.Controls.Page.WindowTitle%2A>、 <xref:System.Windows.Controls.Page.WindowWidth%2A> 和 <xref:System.Windows.Controls.Page.WindowHeight%2A> 可以在标记中以声明方式设置，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="1e267-182"><xref:System.Windows.Controls.Page.WindowTitle%2A>, <xref:System.Windows.Controls.Page.WindowWidth%2A>, and <xref:System.Windows.Controls.Page.WindowHeight%2A> can be set declaratively in markup, as shown in the following example.</span></span>

[!code-xaml[NavigationOverviewSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/HomePage.xaml#homepagemarkup)]

<span data-ttu-id="1e267-183">结果如下图所示。</span><span class="sxs-lookup"><span data-stu-id="1e267-183">The result is shown in the following figure.</span></span>

<span data-ttu-id="1e267-184">![Window 标题、高度、宽度](./media/navigation-overview/window-title-width-height.png "这会显示可以配置的窗口标题、高度和宽度。")</span><span class="sxs-lookup"><span data-stu-id="1e267-184">![Window title, height, width](./media/navigation-overview/window-title-width-height.png "This shows the window title, height, and width you can configure.")</span></span>

<a name="NavigatingBetweenXAMLPages"></a>

### <a name="hyperlink-navigation"></a><span data-ttu-id="1e267-185">超链接导航</span><span class="sxs-lookup"><span data-stu-id="1e267-185">Hyperlink Navigation</span></span>

<span data-ttu-id="1e267-186">典型的 XBAP 包含多个页面。</span><span class="sxs-lookup"><span data-stu-id="1e267-186">A typical XBAP comprises several pages.</span></span> <span data-ttu-id="1e267-187">若要从一页导航到另一页，最简单的方法是使用 <xref:System.Windows.Documents.Hyperlink> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-187">The simplest way to navigate from one page to another is to use a <xref:System.Windows.Documents.Hyperlink>.</span></span> <span data-ttu-id="1e267-188">您可以使用元素以声明方式向添加 <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Controls.Page> ，该 `Hyperlink` 元素显示在下面的标记中。</span><span class="sxs-lookup"><span data-stu-id="1e267-188">You can declaratively add a <xref:System.Windows.Documents.Hyperlink> to a <xref:System.Windows.Controls.Page> by using the `Hyperlink` element, which is shown in the following markup.</span></span>

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

<span data-ttu-id="1e267-189">`Hyperlink`元素需要以下各项：</span><span class="sxs-lookup"><span data-stu-id="1e267-189">A `Hyperlink` element requires the following:</span></span>

- <span data-ttu-id="1e267-190">要导航到的的包 URI <xref:System.Windows.Controls.Page> ，如特性所指定 `NavigateUri` 。</span><span class="sxs-lookup"><span data-stu-id="1e267-190">The pack URI of the <xref:System.Windows.Controls.Page> to navigate to, as specified by the `NavigateUri` attribute.</span></span>

- <span data-ttu-id="1e267-191">用户可以单击以启动导航的内容，如文本和图像（对于 `Hyperlink` 元素可包含的内容，请参阅 <xref:System.Windows.Documents.Hyperlink> ）。</span><span class="sxs-lookup"><span data-stu-id="1e267-191">Content that a user can click to initiate the navigation, such as text and images (for the content that the `Hyperlink` element can contain, see <xref:System.Windows.Documents.Hyperlink>).</span></span>

<span data-ttu-id="1e267-192">下图显示了一个具有的的 XBAP <xref:System.Windows.Controls.Page> <xref:System.Windows.Documents.Hyperlink> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-192">The following figure shows an XBAP with a <xref:System.Windows.Controls.Page> that has a <xref:System.Windows.Documents.Hyperlink>.</span></span>

<span data-ttu-id="1e267-193">![具有超链接的页面](./media/navigation-overview/xbap-with-a-page-with-a-hyperlink.png "这会显示一个包含超链接的页的 XBAP。")</span><span class="sxs-lookup"><span data-stu-id="1e267-193">![Page with Hyperlink](./media/navigation-overview/xbap-with-a-page-with-a-hyperlink.png "This shows an XBAP with a page with a hyperlink.")</span></span>

<span data-ttu-id="1e267-194">正如您所期望的那样，单击将 <xref:System.Windows.Documents.Hyperlink> 导致 XBAP 导航到 <xref:System.Windows.Controls.Page> 由属性标识的 `NavigateUri` 。</span><span class="sxs-lookup"><span data-stu-id="1e267-194">As you would expect, clicking the <xref:System.Windows.Documents.Hyperlink> causes the XBAP to navigate to the <xref:System.Windows.Controls.Page> that is identified by the `NavigateUri` attribute.</span></span> <span data-ttu-id="1e267-195">此外，XBAP 向 <xref:System.Windows.Controls.Page> Internet Explorer 中的 "最近使用的页" 列表添加了一个条目。</span><span class="sxs-lookup"><span data-stu-id="1e267-195">Additionally, the XBAP adds an entry for the previous <xref:System.Windows.Controls.Page> to the Recent Pages list in Internet Explorer.</span></span> <span data-ttu-id="1e267-196">如下图所示。</span><span class="sxs-lookup"><span data-stu-id="1e267-196">This is shown in the following figure.</span></span>

<span data-ttu-id="1e267-197">![后退和前进按钮](./media/navigation-overview/back-and-forward-navigation.png "用 "后退" 和 "前进" 按钮导航。")</span><span class="sxs-lookup"><span data-stu-id="1e267-197">![Back and Forward buttons](./media/navigation-overview/back-and-forward-navigation.png "Navigate with the back and forward buttons.")</span></span>

<span data-ttu-id="1e267-198">并且支持从一个导航 <xref:System.Windows.Controls.Page> 到另一个导航， <xref:System.Windows.Documents.Hyperlink> 还支持片段导航。</span><span class="sxs-lookup"><span data-stu-id="1e267-198">As well as supporting navigation from one <xref:System.Windows.Controls.Page> to another, <xref:System.Windows.Documents.Hyperlink> also supports fragment navigation.</span></span>

<a name="FragmentNavigation"></a>

### <a name="fragment-navigation"></a><span data-ttu-id="1e267-199">片段导航</span><span class="sxs-lookup"><span data-stu-id="1e267-199">Fragment Navigation</span></span>

<span data-ttu-id="1e267-200">*片段导航*是在当前或另一个中导航到内容片段的内容 <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-200">*Fragment navigation* is the navigation to a content fragment in either the current <xref:System.Windows.Controls.Page> or another <xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="1e267-201">在 WPF 中，内容片段是已命名元素包含的内容。</span><span class="sxs-lookup"><span data-stu-id="1e267-201">In WPF, a content fragment is the content that is contained by a named element.</span></span> <span data-ttu-id="1e267-202">命名元素是设置了其属性的元素 `Name` 。</span><span class="sxs-lookup"><span data-stu-id="1e267-202">A named element is an element that has its `Name` attribute set.</span></span> <span data-ttu-id="1e267-203">下面的标记显示了 `TextBlock` 包含内容片段的命名元素。</span><span class="sxs-lookup"><span data-stu-id="1e267-203">The following markup shows a named `TextBlock` element that contains a content fragment.</span></span>

[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup2)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup3)]

<span data-ttu-id="1e267-204"><xref:System.Windows.Documents.Hyperlink>若要导航到内容片段，该 `NavigateUri` 属性必须包括以下内容：</span><span class="sxs-lookup"><span data-stu-id="1e267-204">For a <xref:System.Windows.Documents.Hyperlink> to navigate to a content fragment, the `NavigateUri` attribute must include the following:</span></span>

- <span data-ttu-id="1e267-205"><xref:System.Windows.Controls.Page>具有要导航到的内容片段的的 URI。</span><span class="sxs-lookup"><span data-stu-id="1e267-205">The URI of the <xref:System.Windows.Controls.Page> with the content fragment to navigate to.</span></span>

- <span data-ttu-id="1e267-206">“#”字符。</span><span class="sxs-lookup"><span data-stu-id="1e267-206">A "#" character.</span></span>

- <span data-ttu-id="1e267-207">中包含内容片段的元素的名称 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-207">The name of the element on the <xref:System.Windows.Controls.Page> that contains the content fragment.</span></span>

<span data-ttu-id="1e267-208">片段 URI 的格式如下。</span><span class="sxs-lookup"><span data-stu-id="1e267-208">A fragment URI has the following format.</span></span>

<span data-ttu-id="1e267-209">*PageURI* `#` *ElementName*</span><span class="sxs-lookup"><span data-stu-id="1e267-209">*PageURI* `#` *ElementName*</span></span>

<span data-ttu-id="1e267-210">下面显示了一个 `Hyperlink` 配置为导航到内容片段的的示例。</span><span class="sxs-lookup"><span data-stu-id="1e267-210">The following shows an example of a `Hyperlink` that is configured to navigate to a content fragment.</span></span>

[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml1)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml2)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml3)]

> [!NOTE]
> <span data-ttu-id="1e267-211">本部分介绍 WPF 中的默认片段导航实现。</span><span class="sxs-lookup"><span data-stu-id="1e267-211">This section describes the default fragment navigation implementation in WPF.</span></span> <span data-ttu-id="1e267-212">WPF 还允许实现自己的片段导航方案，该方案在某种程度上需要处理 <xref:System.Windows.Navigation.NavigationService.FragmentNavigation?displayProperty=nameWithType> 事件。</span><span class="sxs-lookup"><span data-stu-id="1e267-212">WPF also allows you to implement your own fragment navigation scheme which, in part, requires handling the <xref:System.Windows.Navigation.NavigationService.FragmentNavigation?displayProperty=nameWithType> event.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1e267-213">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] `Page` 仅当可以通过 HTTP 浏览这些页面时，才能导航到松散页面（仅限标记的文件，并将其作为根元素）。</span><span class="sxs-lookup"><span data-stu-id="1e267-213">You can navigate to fragments in loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pages (markup-only [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files with `Page` as the root element) only if the pages can be browsed via HTTP.</span></span>
>
> <span data-ttu-id="1e267-214">但松散 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 页可以导航到其自己的片段。</span><span class="sxs-lookup"><span data-stu-id="1e267-214">However, a loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page can navigate to its own fragments.</span></span>

<a name="NavigationService"></a>

### <a name="navigation-service"></a><span data-ttu-id="1e267-215">导航服务</span><span class="sxs-lookup"><span data-stu-id="1e267-215">Navigation Service</span></span>

<span data-ttu-id="1e267-216">虽然 <xref:System.Windows.Documents.Hyperlink> 允许用户启动对特定的导航，但 <xref:System.Windows.Controls.Page> 查找和下载页面的工作由 <xref:System.Windows.Navigation.NavigationService> 类执行。</span><span class="sxs-lookup"><span data-stu-id="1e267-216">While <xref:System.Windows.Documents.Hyperlink> allows a user to initiate navigation to a particular <xref:System.Windows.Controls.Page>, the work of locating and downloading the page is performed by the <xref:System.Windows.Navigation.NavigationService> class.</span></span> <span data-ttu-id="1e267-217">实质 <xref:System.Windows.Navigation.NavigationService> 上，提供代表客户端代码处理导航请求的能力，例如 <xref:System.Windows.Documents.Hyperlink> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-217">Essentially, <xref:System.Windows.Navigation.NavigationService> provides the ability to process a navigation request on behalf of client code, such as the <xref:System.Windows.Documents.Hyperlink>.</span></span> <span data-ttu-id="1e267-218">此外，还 <xref:System.Windows.Navigation.NavigationService> 实现了对跟踪和影响导航请求的更高级别的支持。</span><span class="sxs-lookup"><span data-stu-id="1e267-218">Additionally, <xref:System.Windows.Navigation.NavigationService> implements higher-level support for tracking and influencing a navigation request.</span></span>

<span data-ttu-id="1e267-219">单击时 <xref:System.Windows.Documents.Hyperlink> ，WPF 将调用 <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> 以在指定的 <xref:System.Windows.Controls.Page> 包 URI 上查找并下载。</span><span class="sxs-lookup"><span data-stu-id="1e267-219">When a <xref:System.Windows.Documents.Hyperlink> is clicked, WPF calls <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> to locate and download the <xref:System.Windows.Controls.Page> at the specified pack URI.</span></span> <span data-ttu-id="1e267-220">下载的 <xref:System.Windows.Controls.Page> 会转换为对象树，这些对象的根对象是已下载的实例 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-220">The downloaded <xref:System.Windows.Controls.Page> is converted to a tree of objects whose root object is an instance of the downloaded <xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="1e267-221">对根对象的引用 <xref:System.Windows.Controls.Page> 存储在 <xref:System.Windows.Navigation.NavigationService.Content%2A?displayProperty=nameWithType> 属性中。</span><span class="sxs-lookup"><span data-stu-id="1e267-221">A reference to the root <xref:System.Windows.Controls.Page> object is stored in the <xref:System.Windows.Navigation.NavigationService.Content%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="1e267-222">所导航到的内容的 pack URI 存储在 <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> 属性中，而 <xref:System.Windows.Navigation.NavigationService.CurrentSource%2A?displayProperty=nameWithType> 存储所导航到的最后一页的包 uri。</span><span class="sxs-lookup"><span data-stu-id="1e267-222">The pack URI for the content that was navigated to is stored in the <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> property, while the <xref:System.Windows.Navigation.NavigationService.CurrentSource%2A?displayProperty=nameWithType> stores the pack URI for the last page that was navigated to.</span></span>

> [!NOTE]
> <span data-ttu-id="1e267-223">WPF 应用程序可以有多个当前处于活动状态 <xref:System.Windows.Navigation.NavigationService> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-223">It is possible for a WPF application to have more than one currently active <xref:System.Windows.Navigation.NavigationService>.</span></span> <span data-ttu-id="1e267-224">有关详细信息，请参阅本主题后面的[导航宿主](#Navigation_Hosts)。</span><span class="sxs-lookup"><span data-stu-id="1e267-224">For more information, see [Navigation Hosts](#Navigation_Hosts) later in this topic.</span></span>

<a name="Programmatic_Navigation_with_the_Navigation_Service"></a>

### <a name="programmatic-navigation-with-the-navigation-service"></a><span data-ttu-id="1e267-225">使用导航服务以编程方式导航</span><span class="sxs-lookup"><span data-stu-id="1e267-225">Programmatic Navigation with the Navigation Service</span></span>

<span data-ttu-id="1e267-226">您无需知道 <xref:System.Windows.Navigation.NavigationService> 是否使用在标记中以声明方式实现导航 <xref:System.Windows.Documents.Hyperlink> ，因为 <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Navigation.NavigationService> 代表您使用。</span><span class="sxs-lookup"><span data-stu-id="1e267-226">You don't need to know about <xref:System.Windows.Navigation.NavigationService> if navigation is implemented declaratively in markup using <xref:System.Windows.Documents.Hyperlink>, because <xref:System.Windows.Documents.Hyperlink> uses the <xref:System.Windows.Navigation.NavigationService> on your behalf.</span></span> <span data-ttu-id="1e267-227">这意味着，只要的直接或间接父级 <xref:System.Windows.Documents.Hyperlink> 是导航宿主（请参阅[导航](#Navigation_Hosts)宿主）， <xref:System.Windows.Documents.Hyperlink> 就能找到并使用导航宿主的导航服务来处理导航请求。</span><span class="sxs-lookup"><span data-stu-id="1e267-227">This means that, as long as either the direct or indirect parent of a <xref:System.Windows.Documents.Hyperlink> is a navigation host (see [Navigation Hosts](#Navigation_Hosts)), <xref:System.Windows.Documents.Hyperlink> will be able to find and use the navigation host's navigation service to process a navigation request.</span></span>

<span data-ttu-id="1e267-228">但是，在某些情况下，你需要 <xref:System.Windows.Navigation.NavigationService> 直接使用，其中包括：</span><span class="sxs-lookup"><span data-stu-id="1e267-228">However, there are situations when you need to use <xref:System.Windows.Navigation.NavigationService> directly, including the following:</span></span>

- <span data-ttu-id="1e267-229">需要 <xref:System.Windows.Controls.Page> 使用非参数构造函数实例化时。</span><span class="sxs-lookup"><span data-stu-id="1e267-229">When you need to instantiate a <xref:System.Windows.Controls.Page> using a non-parameterless constructor.</span></span>

- <span data-ttu-id="1e267-230">当你需要在上设置属性， <xref:System.Windows.Controls.Page> 然后再导航到它。</span><span class="sxs-lookup"><span data-stu-id="1e267-230">When you need to set properties on the <xref:System.Windows.Controls.Page> before you navigate to it.</span></span>

- <span data-ttu-id="1e267-231"><xref:System.Windows.Controls.Page>需要导航到的时，只能在运行时确定。</span><span class="sxs-lookup"><span data-stu-id="1e267-231">When the <xref:System.Windows.Controls.Page> that needs to be navigated to can only be determined at run time.</span></span>

<span data-ttu-id="1e267-232">在这些情况下，需要编写代码，以便通过调用对象的方法以编程方式启动导航 <xref:System.Windows.Navigation.NavigationService.Navigate%2A> <xref:System.Windows.Navigation.NavigationService> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-232">In these situations, you need to write code to programmatically initiate navigation by calling the <xref:System.Windows.Navigation.NavigationService.Navigate%2A> method of the <xref:System.Windows.Navigation.NavigationService> object.</span></span> <span data-ttu-id="1e267-233">这需要获取对的引用 <xref:System.Windows.Navigation.NavigationService> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-233">That requires getting a reference to a <xref:System.Windows.Navigation.NavigationService>.</span></span>

#### <a name="getting-a-reference-to-the-navigationservice"></a><span data-ttu-id="1e267-234">获取对 NavigationService 的引用</span><span class="sxs-lookup"><span data-stu-id="1e267-234">Getting a Reference to the NavigationService</span></span>

<span data-ttu-id="1e267-235">出于[导航宿主](#Navigation_Hosts)部分所述的原因，WPF 应用程序可以有多个 <xref:System.Windows.Navigation.NavigationService> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-235">For reasons that are covered in the [Navigation Hosts](#Navigation_Hosts) section, a WPF application can have more than one <xref:System.Windows.Navigation.NavigationService>.</span></span> <span data-ttu-id="1e267-236">这意味着，你的代码需要一种方法来查找 <xref:System.Windows.Navigation.NavigationService> ，这通常是 <xref:System.Windows.Navigation.NavigationService> 导航到当前的 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-236">This means that your code needs a way to find a <xref:System.Windows.Navigation.NavigationService>, which is usually the <xref:System.Windows.Navigation.NavigationService> that navigated to the current <xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="1e267-237">可以通过调用方法获取对的引用 <xref:System.Windows.Navigation.NavigationService> `static` <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-237">You can get a reference to a <xref:System.Windows.Navigation.NavigationService> by calling the `static`<xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="1e267-238">若要获取 <xref:System.Windows.Navigation.NavigationService> 导航到特定的 <xref:System.Windows.Controls.Page> ，请将对的引用 <xref:System.Windows.Controls.Page> 作为方法的参数传递 <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-238">To get the <xref:System.Windows.Navigation.NavigationService> that navigated to a particular <xref:System.Windows.Controls.Page>, you pass a reference to the <xref:System.Windows.Controls.Page> as the argument of the <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A> method.</span></span> <span data-ttu-id="1e267-239">下面的代码演示如何获取当前的 <xref:System.Windows.Navigation.NavigationService> <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-239">The following code shows how to get the <xref:System.Windows.Navigation.NavigationService> for the current <xref:System.Windows.Controls.Page>.</span></span>

[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPage.xaml.vb#getnscodebehind2)]

<span data-ttu-id="1e267-240">作为的查找的快捷方式 <xref:System.Windows.Navigation.NavigationService> <xref:System.Windows.Controls.Page> ，实现了 <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page.NavigationService%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="1e267-240">As a shortcut for finding the <xref:System.Windows.Navigation.NavigationService> for a <xref:System.Windows.Controls.Page>, <xref:System.Windows.Controls.Page> implements the <xref:System.Windows.Controls.Page.NavigationService%2A> property.</span></span> <span data-ttu-id="1e267-241">这在下面的示例中显示。</span><span class="sxs-lookup"><span data-stu-id="1e267-241">This is shown in the following example.</span></span>

[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPageShortCut.xaml.vb#getnsshortcutcodebehind2)]

> [!NOTE]
> <span data-ttu-id="1e267-242"><xref:System.Windows.Controls.Page> <xref:System.Windows.Navigation.NavigationService> 引发事件时，只能获取对其的引用 <xref:System.Windows.Controls.Page> <xref:System.Windows.FrameworkElement.Loaded> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-242">A <xref:System.Windows.Controls.Page> can only get a reference to its <xref:System.Windows.Navigation.NavigationService> when <xref:System.Windows.Controls.Page> raises the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

#### <a name="programmatic-navigation-to-a-page-object"></a><span data-ttu-id="1e267-243">以编程方式导航到页对象</span><span class="sxs-lookup"><span data-stu-id="1e267-243">Programmatic Navigation to a Page Object</span></span>

<span data-ttu-id="1e267-244">下面的示例演示如何使用 <xref:System.Windows.Navigation.NavigationService> 以编程方式导航到 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-244">The following example shows how to use the <xref:System.Windows.Navigation.NavigationService> to programmatically navigate to a <xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="1e267-245">需要编程式导航，因为 <xref:System.Windows.Controls.Page> 要导航到的只能使用单个无参数的构造函数实例化。</span><span class="sxs-lookup"><span data-stu-id="1e267-245">Programmatic navigation is required because the <xref:System.Windows.Controls.Page> that is being navigated to can only be instantiated using a single, non-parameterless constructor.</span></span> <span data-ttu-id="1e267-246"><xref:System.Windows.Controls.Page>以下标记和代码中显示了具有非参数构造函数的。</span><span class="sxs-lookup"><span data-stu-id="1e267-246">The <xref:System.Windows.Controls.Page> with the non-parameterless constructor is shown in the following markup and code.</span></span>

[!code-xaml[NavigationOverviewSnippets#PageWithNonDefaultConstructorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml#pagewithnondefaultconstructorxaml)]

[!code-csharp[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml.cs#pagewithnondefaultconstructorcodebehind)]
[!code-vb[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithNonDefaultConstructor.xaml.vb#pagewithnondefaultconstructorcodebehind)]

<span data-ttu-id="1e267-247"><xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page> 以下标记和代码中显示了导航到具有非参数构造函数的。</span><span class="sxs-lookup"><span data-stu-id="1e267-247">The <xref:System.Windows.Controls.Page> that navigates to the <xref:System.Windows.Controls.Page> with the non-parameterless constructor is shown in the following markup and code.</span></span>

[!code-xaml[NavigationOverviewSnippets#NSNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml#nsnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml.cs#nsnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSNavigationPage.xaml.vb#nsnavigationpagecodebehind)]

<span data-ttu-id="1e267-248">当 <xref:System.Windows.Documents.Hyperlink> 单击上的时 <xref:System.Windows.Controls.Page> ，将通过实例化导航到 <xref:System.Windows.Controls.Page> 使用非参数构造函数并调用方法来启动导航 <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-248">When the <xref:System.Windows.Documents.Hyperlink> on this <xref:System.Windows.Controls.Page> is clicked, navigation is initiated by instantiating the <xref:System.Windows.Controls.Page> to navigate to using the non-parameterless constructor and calling the <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="1e267-249"><xref:System.Windows.Navigation.NavigationService.Navigate%2A>接受对将导航到的对象的引用 <xref:System.Windows.Navigation.NavigationService> ，而不是包 URI。</span><span class="sxs-lookup"><span data-stu-id="1e267-249"><xref:System.Windows.Navigation.NavigationService.Navigate%2A> accepts a reference to the object that the <xref:System.Windows.Navigation.NavigationService> will navigate to, rather than a pack URI.</span></span>

#### <a name="programmatic-navigation-with-a-pack-uri"></a><span data-ttu-id="1e267-250">使用 Pack URI 以编程方式导航</span><span class="sxs-lookup"><span data-stu-id="1e267-250">Programmatic Navigation with a Pack URI</span></span>

<span data-ttu-id="1e267-251">如果需要以编程方式构造包 URI （例如，只能在运行时确定 pack URI，则可以使用 <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> 方法）。</span><span class="sxs-lookup"><span data-stu-id="1e267-251">If you need to construct a pack URI programmatically (when you can only determine the pack URI at run time, for example), you can use the <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="1e267-252">这在下面的示例中显示。</span><span class="sxs-lookup"><span data-stu-id="1e267-252">This is shown in the following example.</span></span>

[!code-xaml[NavigationOverviewSnippets#NSUriNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml#nsurinavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml.cs#nsurinavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSUriNavigationPage.xaml.vb#nsurinavigationpagecodebehind)]

#### <a name="refreshing-the-current-page"></a><span data-ttu-id="1e267-253">刷新当前页</span><span class="sxs-lookup"><span data-stu-id="1e267-253">Refreshing the Current Page</span></span>

<span data-ttu-id="1e267-254"><xref:System.Windows.Controls.Page>如果与存储在属性中的 PACK uri 的包 uri 相同，则不会下载。 <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1e267-254">A <xref:System.Windows.Controls.Page> is not downloaded if it has the same pack URI as the pack URI that is stored in the <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="1e267-255">若要强制 WPF 再次下载当前页，可以调用 <xref:System.Windows.Navigation.NavigationService.Refresh%2A?displayProperty=nameWithType> 方法，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="1e267-255">To force WPF to download the current page again, you can call the <xref:System.Windows.Navigation.NavigationService.Refresh%2A?displayProperty=nameWithType> method, as shown in the following example.</span></span>

[!code-xaml[NavigationOverviewSnippets#NSRefreshNavigationPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml#nsrefreshnavigationpagexaml1)]

[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind1)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind2)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind2)]

<a name="Navigation_Lifetime"></a>

### <a name="navigation-lifetime"></a><span data-ttu-id="1e267-256">导航生存期</span><span class="sxs-lookup"><span data-stu-id="1e267-256">Navigation Lifetime</span></span>

<span data-ttu-id="1e267-257">如你所见，有很多方法初始化导航。</span><span class="sxs-lookup"><span data-stu-id="1e267-257">There are many ways to initiate navigation, as you've seen.</span></span> <span data-ttu-id="1e267-258">当启动导航时，导航正在进行时，可以使用以下实现的事件来跟踪和影响导航 <xref:System.Windows.Navigation.NavigationService> ：</span><span class="sxs-lookup"><span data-stu-id="1e267-258">When navigation is initiated, and while navigation is in progress, you can track and influence the navigation using the following events that are implemented by <xref:System.Windows.Navigation.NavigationService>:</span></span>

- <span data-ttu-id="1e267-259"><xref:System.Windows.Navigation.NavigationService.Navigating>.</span><span class="sxs-lookup"><span data-stu-id="1e267-259"><xref:System.Windows.Navigation.NavigationService.Navigating>.</span></span> <span data-ttu-id="1e267-260">请求新导航时发生。</span><span class="sxs-lookup"><span data-stu-id="1e267-260">Occurs when a new navigation is requested.</span></span> <span data-ttu-id="1e267-261">可用于取消导航。</span><span class="sxs-lookup"><span data-stu-id="1e267-261">Can be used to cancel the navigation.</span></span>

- <span data-ttu-id="1e267-262"><xref:System.Windows.Navigation.NavigationService.NavigationProgress>.</span><span class="sxs-lookup"><span data-stu-id="1e267-262"><xref:System.Windows.Navigation.NavigationService.NavigationProgress>.</span></span> <span data-ttu-id="1e267-263">在下载过程中定期发生，用于提供定位进度信息。</span><span class="sxs-lookup"><span data-stu-id="1e267-263">Occurs periodically during a download to provide navigation progress information.</span></span>

- <span data-ttu-id="1e267-264"><xref:System.Windows.Navigation.NavigationService.Navigated>.</span><span class="sxs-lookup"><span data-stu-id="1e267-264"><xref:System.Windows.Navigation.NavigationService.Navigated>.</span></span> <span data-ttu-id="1e267-265">已定位并下载页时发生。</span><span class="sxs-lookup"><span data-stu-id="1e267-265">Occurs when the page has been located and downloaded.</span></span>

- <span data-ttu-id="1e267-266"><xref:System.Windows.Navigation.NavigationService.NavigationStopped>.</span><span class="sxs-lookup"><span data-stu-id="1e267-266"><xref:System.Windows.Navigation.NavigationService.NavigationStopped>.</span></span> <span data-ttu-id="1e267-267">在导航停止（通过调用 <xref:System.Windows.Navigation.NavigationService.StopLoading%2A> ）时发生，或在当前导航正在进行时请求新导航时发生。</span><span class="sxs-lookup"><span data-stu-id="1e267-267">Occurs when the navigation is stopped (by calling <xref:System.Windows.Navigation.NavigationService.StopLoading%2A>), or when a new navigation is requested while a current navigation is in progress.</span></span>

- <span data-ttu-id="1e267-268"><xref:System.Windows.Navigation.NavigationService.NavigationFailed>.</span><span class="sxs-lookup"><span data-stu-id="1e267-268"><xref:System.Windows.Navigation.NavigationService.NavigationFailed>.</span></span> <span data-ttu-id="1e267-269">在导航到所需内容的同时遇到错误时发生。</span><span class="sxs-lookup"><span data-stu-id="1e267-269">Occurs when an error is raised while navigating to the requested content.</span></span>

- <span data-ttu-id="1e267-270"><xref:System.Windows.Navigation.NavigationService.LoadCompleted>.</span><span class="sxs-lookup"><span data-stu-id="1e267-270"><xref:System.Windows.Navigation.NavigationService.LoadCompleted>.</span></span> <span data-ttu-id="1e267-271">导航到的内容已加载和分析，并开始呈现时发生。</span><span class="sxs-lookup"><span data-stu-id="1e267-271">Occurs when content that was navigated to is loaded and parsed, and has begun rendering.</span></span>

- <span data-ttu-id="1e267-272"><xref:System.Windows.Navigation.NavigationService.FragmentNavigation>.</span><span class="sxs-lookup"><span data-stu-id="1e267-272"><xref:System.Windows.Navigation.NavigationService.FragmentNavigation>.</span></span> <span data-ttu-id="1e267-273">导航到内容片段开始时发生，具体如何发生如下所述：</span><span class="sxs-lookup"><span data-stu-id="1e267-273">Occurs when navigation to a content fragment begins, which happens:</span></span>

  - <span data-ttu-id="1e267-274">立即，如果所需片段位于当前内容中。</span><span class="sxs-lookup"><span data-stu-id="1e267-274">Immediately, if the desired fragment is in the current content.</span></span>

  - <span data-ttu-id="1e267-275">源内容加载之后，如果所需片段在不同内容中。</span><span class="sxs-lookup"><span data-stu-id="1e267-275">After the source content has been loaded, if the desired fragment is in different content.</span></span>

<span data-ttu-id="1e267-276">引发导航事件的顺序如下图所示。</span><span class="sxs-lookup"><span data-stu-id="1e267-276">The navigation events are raised in the order that is illustrated by the following figure.</span></span>

<span data-ttu-id="1e267-277">![页面导航流程图](./media/navigation-overview/order-of-navigation-events.png "页面导航事件流程图")</span><span class="sxs-lookup"><span data-stu-id="1e267-277">![Page navigation flow chart](./media/navigation-overview/order-of-navigation-events.png "Page navigation event flow chart")</span></span>

<span data-ttu-id="1e267-278">一般情况下， <xref:System.Windows.Controls.Page> 并不关心这些事件。</span><span class="sxs-lookup"><span data-stu-id="1e267-278">In general, a <xref:System.Windows.Controls.Page> isn't concerned about these events.</span></span> <span data-ttu-id="1e267-279">更有可能应用程序与应用程序相关，因此，这些事件也由 <xref:System.Windows.Application> 类引发：</span><span class="sxs-lookup"><span data-stu-id="1e267-279">It is more likely that an application is concerned with them and, for that reason, these events are also raised by the <xref:System.Windows.Application> class:</span></span>

- <xref:System.Windows.Application.Navigating?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationProgress?displayProperty=nameWithType>

- <xref:System.Windows.Application.Navigated?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationFailed?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationStopped?displayProperty=nameWithType>

- <xref:System.Windows.Application.LoadCompleted?displayProperty=nameWithType>

- <xref:System.Windows.Application.FragmentNavigation?displayProperty=nameWithType>

<span data-ttu-id="1e267-280">每次 <xref:System.Windows.Navigation.NavigationService> 引发事件时， <xref:System.Windows.Application> 类将引发相应的事件。</span><span class="sxs-lookup"><span data-stu-id="1e267-280">Every time <xref:System.Windows.Navigation.NavigationService> raises an event, the <xref:System.Windows.Application> class raises the corresponding event.</span></span> <span data-ttu-id="1e267-281"><xref:System.Windows.Controls.Frame>和 <xref:System.Windows.Navigation.NavigationWindow> 提供相同的事件来检测其各自范围内的导航。</span><span class="sxs-lookup"><span data-stu-id="1e267-281"><xref:System.Windows.Controls.Frame> and <xref:System.Windows.Navigation.NavigationWindow> offer the same events to detect navigation within their respective scopes.</span></span>

<span data-ttu-id="1e267-282">在某些情况下， <xref:System.Windows.Controls.Page> 可能会对这些事件感兴趣。</span><span class="sxs-lookup"><span data-stu-id="1e267-282">In some cases, a <xref:System.Windows.Controls.Page> might be interested in these events.</span></span> <span data-ttu-id="1e267-283">例如， <xref:System.Windows.Controls.Page> 可以处理 <xref:System.Windows.Navigation.NavigationService.Navigating?displayProperty=nameWithType> 事件，以确定是否取消导航。</span><span class="sxs-lookup"><span data-stu-id="1e267-283">For example, a <xref:System.Windows.Controls.Page> might handle the <xref:System.Windows.Navigation.NavigationService.Navigating?displayProperty=nameWithType> event to determine whether or not to cancel navigation away from itself.</span></span> <span data-ttu-id="1e267-284">这在下面的示例中显示。</span><span class="sxs-lookup"><span data-stu-id="1e267-284">This is shown in the following example.</span></span>

[!code-xaml[NavigationOverviewSnippets#CancelNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml#cancelnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml.cs#cancelnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/CancelNavigationPage.xaml.vb#cancelnavigationpagecodebehind)]

<span data-ttu-id="1e267-285">如果你使用中的导航事件注册处理程序 <xref:System.Windows.Controls.Page> ，如前面的示例所示，你还必须取消注册事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="1e267-285">If you register a handler with a navigation event from a <xref:System.Windows.Controls.Page>, as the preceding example does, you must also unregister the event handler.</span></span> <span data-ttu-id="1e267-286">否则，对于 WPF 导航如何记住 <xref:System.Windows.Controls.Page> 使用日记的导航，可能会产生负面影响。</span><span class="sxs-lookup"><span data-stu-id="1e267-286">If you don't, there may be side effects with respect to how WPF navigation remembers <xref:System.Windows.Controls.Page> navigation using the journal.</span></span>

<a name="NavigationHistory"></a>

### <a name="remembering-navigation-with-the-journal"></a><span data-ttu-id="1e267-287">使用日志记住导航</span><span class="sxs-lookup"><span data-stu-id="1e267-287">Remembering Navigation with the Journal</span></span>

<span data-ttu-id="1e267-288">WPF 使用两个堆栈来记住您从其导航的页面：后退堆栈和前进堆栈。</span><span class="sxs-lookup"><span data-stu-id="1e267-288">WPF uses two stacks to remember the pages that you have navigated from: a back stack and a forward stack.</span></span> <span data-ttu-id="1e267-289">当你从当前导航 <xref:System.Windows.Controls.Page> 到新的 <xref:System.Windows.Controls.Page> 或转发到现有的时 <xref:System.Windows.Controls.Page> ，当前 <xref:System.Windows.Controls.Page> 将添加到*back 堆栈*中。</span><span class="sxs-lookup"><span data-stu-id="1e267-289">When you navigate from the current <xref:System.Windows.Controls.Page> to a new <xref:System.Windows.Controls.Page> or forward to an existing <xref:System.Windows.Controls.Page>, the current <xref:System.Windows.Controls.Page> is added to the *back stack*.</span></span> <span data-ttu-id="1e267-290">当您从当前导航 <xref:System.Windows.Controls.Page> 回之前 <xref:System.Windows.Controls.Page> ，当前 <xref:System.Windows.Controls.Page> 将添加到*前进堆栈*中。</span><span class="sxs-lookup"><span data-stu-id="1e267-290">When you navigate from the current <xref:System.Windows.Controls.Page> back to the previous <xref:System.Windows.Controls.Page>, the current <xref:System.Windows.Controls.Page> is added to the *forward stack*.</span></span> <span data-ttu-id="1e267-291">后退堆栈、前进堆栈和管理它们的功能统称为日志。</span><span class="sxs-lookup"><span data-stu-id="1e267-291">The back stack, the forward stack, and the functionality to manage them, are collectively referred to as the journal.</span></span> <span data-ttu-id="1e267-292">后退堆栈中的每一项和正向堆栈是类的实例 <xref:System.Windows.Navigation.JournalEntry> ，并且称为*日记条目*。</span><span class="sxs-lookup"><span data-stu-id="1e267-292">Each item in the back stack and the forward stack is an instance of the <xref:System.Windows.Navigation.JournalEntry> class, and is referred to as a *journal entry*.</span></span>

#### <a name="navigating-the-journal-from-internet-explorer"></a><span data-ttu-id="1e267-293">从 Internet Explorer 导航日志</span><span class="sxs-lookup"><span data-stu-id="1e267-293">Navigating the Journal from Internet Explorer</span></span>

<span data-ttu-id="1e267-294">从概念上讲，日记的工作方式与 Internet Explorer 中的 "**后退**" 和 "**前进**" 按钮的操作方式相同。</span><span class="sxs-lookup"><span data-stu-id="1e267-294">Conceptually, the journal operates the same way that the **Back** and **Forward** buttons in Internet Explorer do.</span></span> <span data-ttu-id="1e267-295">这些在下图中显示。</span><span class="sxs-lookup"><span data-stu-id="1e267-295">These are shown in the following figure.</span></span>

<span data-ttu-id="1e267-296">![后退和前进按钮](./media/navigation-overview/back-and-forward-navigation.png "用 "后退" 和 "前进" 按钮导航。")</span><span class="sxs-lookup"><span data-stu-id="1e267-296">![Back and Forward buttons](./media/navigation-overview/back-and-forward-navigation.png "Navigate with the back and forward buttons.")</span></span>

<span data-ttu-id="1e267-297">对于由 Internet Explorer 承载的 Xbap，WPF 将日记本集成到 Internet Explorer 的导航中 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1e267-297">For XBAPs that are hosted by Internet Explorer, WPF integrates the journal into the navigation [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] of Internet Explorer.</span></span> <span data-ttu-id="1e267-298">这允许用户使用 Internet Explorer 中的 "**后退**"、"**前进**" 和 "**最新页**" 按钮在 XBAP 中导航页面。</span><span class="sxs-lookup"><span data-stu-id="1e267-298">This allows users to navigate pages in an XBAP by using the **Back**, **Forward**, and **Recent Pages** buttons in Internet Explorer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1e267-299">在 Internet Explorer 中，当用户离开并返回到 XBAP 时，仅将未保持活动状态的页的日记条目保留在日志中。</span><span class="sxs-lookup"><span data-stu-id="1e267-299">In Internet Explorer, when a user navigates away from and back to an XBAP, only the journal entries for pages that were not kept alive are retained in the journal.</span></span> <span data-ttu-id="1e267-300">有关保持页处于活动状态的讨论，请参阅本主题后面的[页生存期和日志](#PageLifetime)。</span><span class="sxs-lookup"><span data-stu-id="1e267-300">For discussion on keeping pages alive, see [Page Lifetime and the Journal](#PageLifetime) later in this topic.</span></span>

<span data-ttu-id="1e267-301">默认情况下， <xref:System.Windows.Controls.Page> Internet Explorer 的 "**最新页**" 列表中显示的每个文本都是的 URI <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-301">By default, the text for each <xref:System.Windows.Controls.Page> that appears in the **Recent Pages** list of Internet Explorer is the URI for the <xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="1e267-302">很多情况下这对用户并没有什么特殊的意义。</span><span class="sxs-lookup"><span data-stu-id="1e267-302">In many cases, this is not particularly meaningful to the user.</span></span> <span data-ttu-id="1e267-303">幸运的是，可以使用以下选项更改文本：</span><span class="sxs-lookup"><span data-stu-id="1e267-303">Fortunately, you can change the text using one the following options:</span></span>

1. <span data-ttu-id="1e267-304">附加的 `JournalEntry.Name` 属性值。</span><span class="sxs-lookup"><span data-stu-id="1e267-304">The attached `JournalEntry.Name` attribute value.</span></span>

2. <span data-ttu-id="1e267-305">`Page.Title`特性值。</span><span class="sxs-lookup"><span data-stu-id="1e267-305">The `Page.Title` attribute value.</span></span>

3. <span data-ttu-id="1e267-306">`Page.WindowTitle`当前的特性值和 URI <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-306">The `Page.WindowTitle` attribute value and the URI for the current <xref:System.Windows.Controls.Page>.</span></span>

4. <span data-ttu-id="1e267-307">当前的 URI <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-307">The URI for the current <xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="1e267-308">（默认值）</span><span class="sxs-lookup"><span data-stu-id="1e267-308">(Default)</span></span>

<span data-ttu-id="1e267-309">选项列出的顺序和查找文本的优先级顺序一致。</span><span class="sxs-lookup"><span data-stu-id="1e267-309">The order in which the options are listed matches the order of precedence for finding the text.</span></span> <span data-ttu-id="1e267-310">例如，如果 `JournalEntry.Name` 设置了，则忽略其他值。</span><span class="sxs-lookup"><span data-stu-id="1e267-310">For example, if `JournalEntry.Name` is set, the other values are ignored.</span></span>

<span data-ttu-id="1e267-311">下面的示例使用 `Page.Title` 特性更改为日记条目显示的文本。</span><span class="sxs-lookup"><span data-stu-id="1e267-311">The following example uses the `Page.Title` attribute to change the text that appears for a journal entry.</span></span>

[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup2)]

[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind1)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind2)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind2)]

#### <a name="navigating-the-journal-using-wpf"></a><span data-ttu-id="1e267-312">使用 WPF 导航日志</span><span class="sxs-lookup"><span data-stu-id="1e267-312">Navigating the Journal Using WPF</span></span>

<span data-ttu-id="1e267-313">尽管用户可以使用 Internet Explorer 中的 "**后退**"、"**前进**" 和 "**最新" 页**导航日记，但也可以使用 WPF 提供的声明性和编程机制导航日志。</span><span class="sxs-lookup"><span data-stu-id="1e267-313">Although a user can navigate the journal by using the **Back**, **Forward**, and **Recent Pages** in Internet Explorer, you can also navigate the journal using both declarative and programmatic mechanisms provided by WPF.</span></span> <span data-ttu-id="1e267-314">这样做的一个原因是在页面中提供自定义导航 Ui。</span><span class="sxs-lookup"><span data-stu-id="1e267-314">One reason to do this is to provide custom navigation UIs in your pages.</span></span>

<span data-ttu-id="1e267-315">您可以使用公开的导航命令以声明方式添加日记本导航支持 <xref:System.Windows.Input.NavigationCommands> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-315">You can declaratively add journal navigation support by using the navigation commands exposed by <xref:System.Windows.Input.NavigationCommands>.</span></span> <span data-ttu-id="1e267-316">下面的示例演示如何使用 `BrowseBack` 导航命令。</span><span class="sxs-lookup"><span data-stu-id="1e267-316">The following example demonstrates how to use the `BrowseBack` navigation command.</span></span>

[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml1)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml2)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml3)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML4](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml4)]

<span data-ttu-id="1e267-317">可以使用类的以下成员之一以编程方式导航日记 <xref:System.Windows.Navigation.NavigationService> ：</span><span class="sxs-lookup"><span data-stu-id="1e267-317">You can programmatically navigate the journal by using one of the following members of the <xref:System.Windows.Navigation.NavigationService> class:</span></span>

- <xref:System.Windows.Navigation.NavigationService.GoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.GoForward%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoForward%2A>

<span data-ttu-id="1e267-318">此日志还可以通过编程方式进行操作，如本主题后面的将[内容状态保留为导航历史记录](#RetainingContentStateWithNavigationHistory)中所述。</span><span class="sxs-lookup"><span data-stu-id="1e267-318">The journal can also be manipulated programmatically, as discussed in [Retaining Content State with Navigation History](#RetainingContentStateWithNavigationHistory) later in this topic.</span></span>

<a name="PageLifetime"></a>

### <a name="page-lifetime-and-the-journal"></a><span data-ttu-id="1e267-319">页生存期和日志</span><span class="sxs-lookup"><span data-stu-id="1e267-319">Page Lifetime and the Journal</span></span>

<span data-ttu-id="1e267-320">请考虑 XBAP，其中包含多个包含丰富内容的页，包括图形、动画和媒体。</span><span class="sxs-lookup"><span data-stu-id="1e267-320">Consider an XBAP with several pages that contain rich content, including graphics, animations, and media.</span></span> <span data-ttu-id="1e267-321">这类页的内存占用量可能相当大，尤其是使用视频和音频媒体的时候。</span><span class="sxs-lookup"><span data-stu-id="1e267-321">The memory footprint for pages like these could be quite large, particularly if video and audio media are used.</span></span> <span data-ttu-id="1e267-322">假设该日记 "记住" 已导航到的页面，则此类 XBAP 会迅速消耗大量内存。</span><span class="sxs-lookup"><span data-stu-id="1e267-322">Given that the journal "remembers" pages that have been navigated to, such an XBAP could quickly consume a large and noticeable amount of memory.</span></span>

<span data-ttu-id="1e267-323">出于此原因，日记的默认行为是 <xref:System.Windows.Controls.Page> 在每个日记条目中存储元数据，而不是对对象的引用 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-323">For this reason, the default behavior of the journal is to store <xref:System.Windows.Controls.Page> metadata in each journal entry rather than a reference to a <xref:System.Windows.Controls.Page> object.</span></span> <span data-ttu-id="1e267-324">导航到日记条目时，其 <xref:System.Windows.Controls.Page> 元数据用于创建指定的的新实例 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-324">When a journal entry is navigated to, its <xref:System.Windows.Controls.Page> metadata is used to create a new instance of the specified <xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="1e267-325">因此，所导航的每个都 <xref:System.Windows.Controls.Page> 具有如下图所示的生存期。</span><span class="sxs-lookup"><span data-stu-id="1e267-325">As a consequence, each <xref:System.Windows.Controls.Page> that is navigated has the lifetime that is illustrated by the following figure.</span></span>

<span data-ttu-id="1e267-326">![页面生存期](./media/navigation-overview/navigated-page-lifetime.png "这会显示导航页面时的生存期。")</span><span class="sxs-lookup"><span data-stu-id="1e267-326">![Page lifetime](./media/navigation-overview/navigated-page-lifetime.png "This shows the lifetime when a page is navigated.")</span></span>

<span data-ttu-id="1e267-327">尽管使用默认日记行为可以节省内存消耗，但每页呈现性能可能会降低;呈现 <xref:System.Windows.Controls.Page> 可能会很耗时，尤其是在有大量内容时。</span><span class="sxs-lookup"><span data-stu-id="1e267-327">Although using the default journaling behavior can save on memory consumption, per-page rendering performance might be reduced; reinstantiating a <xref:System.Windows.Controls.Page> can be time-intensive, particularly if it has a lot of content.</span></span> <span data-ttu-id="1e267-328">如果需要将 <xref:System.Windows.Controls.Page> 实例保留在日记中，可以通过两种方法进行绘制。</span><span class="sxs-lookup"><span data-stu-id="1e267-328">If you need to retain a <xref:System.Windows.Controls.Page> instance in the journal, you can draw on two techniques for doing so.</span></span> <span data-ttu-id="1e267-329">首先，可以通过调用方法以编程方式导航到 <xref:System.Windows.Controls.Page> 对象 <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-329">First, you can programmatically navigate to a <xref:System.Windows.Controls.Page> object by calling the <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="1e267-330">其次，可以 <xref:System.Windows.Controls.Page> 通过将 <xref:System.Windows.Controls.Page.KeepAlive%2A> 属性设置为 `true` （默认值为）来指定 WPF 在日志中保留的实例 `false` 。</span><span class="sxs-lookup"><span data-stu-id="1e267-330">Second, you can specify that WPF retain an instance of a <xref:System.Windows.Controls.Page> in the journal by setting the <xref:System.Windows.Controls.Page.KeepAlive%2A> property to `true` (the default is `false`).</span></span> <span data-ttu-id="1e267-331">如以下示例中所示，可以 <xref:System.Windows.Controls.Page.KeepAlive%2A> 在标记中以声明方式设置。</span><span class="sxs-lookup"><span data-stu-id="1e267-331">As shown in the following example, you can set <xref:System.Windows.Controls.Page.KeepAlive%2A> declaratively in markup.</span></span>

[!code-xaml[NavigationOverviewSnippets#KeepAlivePageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/KeepAlivePage.xaml#keepalivepagexaml)]

<span data-ttu-id="1e267-332"><xref:System.Windows.Controls.Page>保持活动状态的生存期与不是相同。</span><span class="sxs-lookup"><span data-stu-id="1e267-332">The lifetime of a <xref:System.Windows.Controls.Page> that is kept alive is subtly different from one that is not.</span></span> <span data-ttu-id="1e267-333">第一次将处于 <xref:System.Windows.Controls.Page> 活动状态的状态导航到时，它的实例化就像 <xref:System.Windows.Controls.Page> 是未保持活动状态的。</span><span class="sxs-lookup"><span data-stu-id="1e267-333">The first time a <xref:System.Windows.Controls.Page> that is kept alive is navigated to, it is instantiated just like a <xref:System.Windows.Controls.Page> that is not kept alive.</span></span> <span data-ttu-id="1e267-334">但是，由于的实例 <xref:System.Windows.Controls.Page> 保留在日志中，因此只要它保留在日志中，就永远不会再对其进行实例化。</span><span class="sxs-lookup"><span data-stu-id="1e267-334">However, because an instance of the <xref:System.Windows.Controls.Page> is retained in the journal, it is never instantiated again for as long as it remains in the journal.</span></span> <span data-ttu-id="1e267-335">因此，如果 <xref:System.Windows.Controls.Page> 有在每次导航到时需要调用的初始化逻辑 <xref:System.Windows.Controls.Page> ，则应将其从构造函数移到事件的处理程序中 <xref:System.Windows.FrameworkElement.Loaded> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-335">Consequently, if a <xref:System.Windows.Controls.Page> has initialization logic that needs to be called every time the <xref:System.Windows.Controls.Page> is navigated to, you should move it from the constructor into a handler for the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span> <span data-ttu-id="1e267-336">如下图所示， <xref:System.Windows.FrameworkElement.Loaded> <xref:System.Windows.FrameworkElement.Unloaded> 每次导航到和时，都仍将引发和事件 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-336">As shown in the following figure, the <xref:System.Windows.FrameworkElement.Loaded> and <xref:System.Windows.FrameworkElement.Unloaded> events are still raised each time a <xref:System.Windows.Controls.Page> is navigated to and from, respectively.</span></span>

<span data-ttu-id="1e267-337">![当引发 Loaded 和 Unloaded 事件时](./media/navigation-overview/loaded-and-unloaded-events.png "当导航到和中的某个页面时，将引发已加载和已卸载的事件。")</span><span class="sxs-lookup"><span data-stu-id="1e267-337">![When the Loaded and Unloaded events are raised](./media/navigation-overview/loaded-and-unloaded-events.png "Loaded and unloaded events are raised when a page is navigated to and from.")</span></span>

<span data-ttu-id="1e267-338">如果 <xref:System.Windows.Controls.Page> 未保持活动状态，则不应执行以下任一操作：</span><span class="sxs-lookup"><span data-stu-id="1e267-338">When a <xref:System.Windows.Controls.Page> is not kept alive, you should not do either of the following:</span></span>

- <span data-ttu-id="1e267-339">存储对它或它的任何部分的引用。</span><span class="sxs-lookup"><span data-stu-id="1e267-339">Store a reference to it, or any part of it.</span></span>

- <span data-ttu-id="1e267-340">将事件处理程序注册到并非由其实现的事件。</span><span class="sxs-lookup"><span data-stu-id="1e267-340">Register event handlers with events that are not implemented by it.</span></span>

<span data-ttu-id="1e267-341">执行上述任一操作都将创建强制 <xref:System.Windows.Controls.Page> 保留在内存中的引用，即使已从日志中删除该引用。</span><span class="sxs-lookup"><span data-stu-id="1e267-341">Doing either of these will create references that force the <xref:System.Windows.Controls.Page> to be retained in memory, even after it has been removed from the journal.</span></span>

<span data-ttu-id="1e267-342">通常，您应该首选 <xref:System.Windows.Controls.Page> 不保持活动状态的默认行为 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-342">In general, you should prefer the default <xref:System.Windows.Controls.Page> behavior of not keeping a <xref:System.Windows.Controls.Page> alive.</span></span> <span data-ttu-id="1e267-343">但是，这会存在将在下一节中讨论的状态影响。</span><span class="sxs-lookup"><span data-stu-id="1e267-343">However, this has state implications that are discussed in the next section.</span></span>

<a name="RetainingContentStateWithNavigationHistory"></a>

### <a name="retaining-content-state-with-navigation-history"></a><span data-ttu-id="1e267-344">保留导航历史记录的内容状态</span><span class="sxs-lookup"><span data-stu-id="1e267-344">Retaining Content State with Navigation History</span></span>

<span data-ttu-id="1e267-345">如果 <xref:System.Windows.Controls.Page> 未保持活动状态，并且具有收集用户数据的控件，则当用户离开并返回到时，数据会发生什么情况 <xref:System.Windows.Controls.Page> ？</span><span class="sxs-lookup"><span data-stu-id="1e267-345">If a <xref:System.Windows.Controls.Page> is not kept alive, and it has controls that collect data from the user, what happens to the data if a user navigates away from and back to the <xref:System.Windows.Controls.Page>?</span></span> <span data-ttu-id="1e267-346">从用户体验角度，用户应该会希望看到他们以前输入的数据。</span><span class="sxs-lookup"><span data-stu-id="1e267-346">From a user experience perspective, the user should expect to see the data they entered previously.</span></span> <span data-ttu-id="1e267-347">遗憾的是，由于每个导航都创建了一个新实例 <xref:System.Windows.Controls.Page> ，因此收集数据的控件将重新实例化，数据会丢失。</span><span class="sxs-lookup"><span data-stu-id="1e267-347">Unfortunately, because a new instance of the <xref:System.Windows.Controls.Page> is created with each navigation, the controls that collected the data are reinstantiated and the data is lost.</span></span>

<span data-ttu-id="1e267-348">幸运的是，日记本提供对跨导航的数据 <xref:System.Windows.Controls.Page> （包括控制数据）的支持。</span><span class="sxs-lookup"><span data-stu-id="1e267-348">Fortunately, the journal provides support for remembering data across <xref:System.Windows.Controls.Page> navigations, including control data.</span></span> <span data-ttu-id="1e267-349">具体而言，每个的日记条目都 <xref:System.Windows.Controls.Page> 充当关联状态的临时容器 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-349">Specifically, the journal entry for each <xref:System.Windows.Controls.Page> acts as a temporary container for the associated <xref:System.Windows.Controls.Page> state.</span></span> <span data-ttu-id="1e267-350">以下步骤概述了从导航时使用此支持的方式 <xref:System.Windows.Controls.Page> ：</span><span class="sxs-lookup"><span data-stu-id="1e267-350">The following steps outline how this support is used when a <xref:System.Windows.Controls.Page> is navigated from:</span></span>

1. <span data-ttu-id="1e267-351">当前的条目 <xref:System.Windows.Controls.Page> 将添加到日志中。</span><span class="sxs-lookup"><span data-stu-id="1e267-351">An entry for the current <xref:System.Windows.Controls.Page> is added to the journal.</span></span>

2. <span data-ttu-id="1e267-352">的状态 <xref:System.Windows.Controls.Page> 与该页的日记条目一起存储，后者将添加到后面的堆栈中。</span><span class="sxs-lookup"><span data-stu-id="1e267-352">The state of the <xref:System.Windows.Controls.Page> is stored with the journal entry for that page, which is added to the back stack.</span></span>

3. <span data-ttu-id="1e267-353"><xref:System.Windows.Controls.Page>导航到新的。</span><span class="sxs-lookup"><span data-stu-id="1e267-353">The new <xref:System.Windows.Controls.Page> is navigated to.</span></span>

<span data-ttu-id="1e267-354">当 <xref:System.Windows.Controls.Page> 使用日记向后导航到页面时，将执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="1e267-354">When the page <xref:System.Windows.Controls.Page> is navigated back to, using the journal, the following steps take place:</span></span>

1. <span data-ttu-id="1e267-355"><xref:System.Windows.Controls.Page>实例化（back 堆栈顶部的日记条目）。</span><span class="sxs-lookup"><span data-stu-id="1e267-355">The <xref:System.Windows.Controls.Page> (the top journal entry on the back stack) is instantiated.</span></span>

2. <span data-ttu-id="1e267-356">将 <xref:System.Windows.Controls.Page> 用与的日记条目一起存储的状态进行刷新 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-356">The <xref:System.Windows.Controls.Page> is refreshed with the state that was stored with the journal entry for the <xref:System.Windows.Controls.Page>.</span></span>

3. <span data-ttu-id="1e267-357">向 <xref:System.Windows.Controls.Page> 后导航到。</span><span class="sxs-lookup"><span data-stu-id="1e267-357">The <xref:System.Windows.Controls.Page> is navigated back to.</span></span>

<span data-ttu-id="1e267-358">当在上使用以下控件时，WPF 将自动使用此支持 <xref:System.Windows.Controls.Page> ：</span><span class="sxs-lookup"><span data-stu-id="1e267-358">WPF automatically uses this support when the following controls are used on a <xref:System.Windows.Controls.Page>:</span></span>

- <xref:System.Windows.Controls.CheckBox>

- <xref:System.Windows.Controls.ComboBox>

- <xref:System.Windows.Controls.Expander>

- <xref:System.Windows.Controls.Frame>

- <xref:System.Windows.Controls.ListBox>

- <xref:System.Windows.Controls.ListBoxItem>

- <xref:System.Windows.Controls.MenuItem>

- <xref:System.Windows.Controls.ProgressBar>

- <xref:System.Windows.Controls.RadioButton>

- <xref:System.Windows.Controls.Slider>

- <xref:System.Windows.Controls.TabControl>

- <xref:System.Windows.Controls.TabItem>

- <xref:System.Windows.Controls.TextBox>

<span data-ttu-id="1e267-359">如果 <xref:System.Windows.Controls.Page> 使用这些控件，则会在导航中记住输入的数据， <xref:System.Windows.Controls.Page> 如下图所示**Favorite Color** <xref:System.Windows.Controls.ListBox> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-359">If a <xref:System.Windows.Controls.Page> uses these controls, data entered into them is remembered across <xref:System.Windows.Controls.Page> navigations, as demonstrated by the **Favorite Color**<xref:System.Windows.Controls.ListBox> in the following figure.</span></span>

<span data-ttu-id="1e267-360">![具有记忆状态的控件的页面](./media/navigation-overview/data-remembered-across-page-navigations.png "跨页面导航记住输入的数据。")</span><span class="sxs-lookup"><span data-stu-id="1e267-360">![Page with controls that remember state](./media/navigation-overview/data-remembered-across-page-navigations.png "Data entered is remembered across page navigations.")</span></span>

<span data-ttu-id="1e267-361">当除 <xref:System.Windows.Controls.Page> 前面的列表中的控件以外的其他控件时，或者当状态存储在自定义对象中时，需要编写代码以使日志记住跨导航状态的状态 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-361">When a <xref:System.Windows.Controls.Page> has controls other than those in the preceding list, or when state is stored in custom objects, you need to write code to cause the journal to remember state across <xref:System.Windows.Controls.Page> navigations.</span></span>

<span data-ttu-id="1e267-362">如果需要记住跨导航的小块状态 <xref:System.Windows.Controls.Page> ，可以使用 <xref:System.Windows.DependencyProperty> 配置了元数据标志的依赖属性（请参见） <xref:System.Windows.FrameworkPropertyMetadata.Journal%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-362">If you need to remember small pieces of state across <xref:System.Windows.Controls.Page> navigations, you can use dependency properties (see <xref:System.Windows.DependencyProperty>) that are configured with the <xref:System.Windows.FrameworkPropertyMetadata.Journal%2A?displayProperty=nameWithType> metadata flag.</span></span>

<span data-ttu-id="1e267-363">如果 <xref:System.Windows.Controls.Page> 需要记住的跨导航的状态包含多个数据段，则可能会发现，将状态封装到单个类并实现接口所需的代码要少得多 <xref:System.Windows.Navigation.IProvideCustomContentState> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-363">If the state that your <xref:System.Windows.Controls.Page> needs to remember across navigations comprises multiple pieces of data, you may find it less code intensive to encapsulate your state in a single class and implement the <xref:System.Windows.Navigation.IProvideCustomContentState> interface.</span></span>

<span data-ttu-id="1e267-364">如果需要在单个的各个状态之间导航 <xref:System.Windows.Controls.Page> ，而不是从自身导航 <xref:System.Windows.Controls.Page> ，则可以使用 <xref:System.Windows.Navigation.IProvideCustomContentState> 和 <xref:System.Windows.Navigation.NavigationService.AddBackEntry%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-364">If you need to navigate through various states of a single <xref:System.Windows.Controls.Page>, without navigating from the <xref:System.Windows.Controls.Page> itself, you can use <xref:System.Windows.Navigation.IProvideCustomContentState> and <xref:System.Windows.Navigation.NavigationService.AddBackEntry%2A?displayProperty=nameWithType>.</span></span>

<a name="Cookies"></a>

### <a name="cookies"></a><span data-ttu-id="1e267-365">Cookie</span><span class="sxs-lookup"><span data-stu-id="1e267-365">Cookies</span></span>

<span data-ttu-id="1e267-366">WPF 应用程序可以存储数据的另一种方法是使用和方法来创建、更新和删除 cookie <xref:System.Windows.Application.SetCookie%2A> <xref:System.Windows.Application.GetCookie%2A> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-366">Another way that WPF applications can store data is with cookies, which are created, updated, and deleted by using the <xref:System.Windows.Application.SetCookie%2A> and <xref:System.Windows.Application.GetCookie%2A> methods.</span></span> <span data-ttu-id="1e267-367">可以在 WPF 中创建的 cookie 与其他类型的 Web 应用程序使用的 cookie 相同;cookie 是由应用程序在客户端计算机上或跨应用程序会话存储的任意数据块。</span><span class="sxs-lookup"><span data-stu-id="1e267-367">The cookies that you can create in WPF are the same cookies that other types of Web applications use; cookies are arbitrary pieces of data that are stored by an application on a client machine either during or across application sessions.</span></span> <span data-ttu-id="1e267-368">Cookie 数据通常采用以下格式的名称/值对的形式。</span><span class="sxs-lookup"><span data-stu-id="1e267-368">Cookie data typically takes the form of a name/value pair in the following format.</span></span>

<span data-ttu-id="1e267-369">*名称* `=`*值*</span><span class="sxs-lookup"><span data-stu-id="1e267-369">*Name* `=` *Value*</span></span>

<span data-ttu-id="1e267-370">在将数据传递到时，如果将数据传递到 <xref:System.Windows.Application.SetCookie%2A> <xref:System.Uri> 应设置 cookie 的位置，则会在内存中创建一个 cookie，并且该 cookie 仅在当前应用程序会话的持续时间内可用。</span><span class="sxs-lookup"><span data-stu-id="1e267-370">When the data is passed to <xref:System.Windows.Application.SetCookie%2A>, along with the <xref:System.Uri> of the location for which the cookie should be set, a cookie is created in-memory, and it is only available for the duration of the current application session.</span></span> <span data-ttu-id="1e267-371">这种类型的 cookie 称为*会话 cookie*。</span><span class="sxs-lookup"><span data-stu-id="1e267-371">This type of cookie is referred to as a *session cookie*.</span></span>

<span data-ttu-id="1e267-372">要跨应用程序会话存储 cookie，必须使用以下格式将到期日期添加到 cookie。</span><span class="sxs-lookup"><span data-stu-id="1e267-372">To store a cookie across application sessions, an expiration date must be added to the cookie, using the following format.</span></span>

<span data-ttu-id="1e267-373">*NAME* `=` *VALUE* `; expires=DAY, DD-MMM-YYYY HH:MM:SS GMT`</span><span class="sxs-lookup"><span data-stu-id="1e267-373">*NAME* `=` *VALUE* `; expires=DAY, DD-MMM-YYYY HH:MM:SS GMT`</span></span>

<span data-ttu-id="1e267-374">在 cookie 过期之前，具有到期日期的 cookie 存储在当前的 Windows 安装程序的临时 Internet Files 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="1e267-374">A cookie with an expiration date is stored in the current Windows installation's Temporary Internet Files folder until the cookie expires.</span></span> <span data-ttu-id="1e267-375">此类 cookie 称为*永久性 cookie* ，因为它在应用程序会话之间保持不变。</span><span class="sxs-lookup"><span data-stu-id="1e267-375">Such a cookie is known as a *persistent cookie* because it persists across application sessions.</span></span>

<span data-ttu-id="1e267-376">可以通过调用方法来检索会话和持久 cookie <xref:System.Windows.Application.GetCookie%2A> ，同时传递 <xref:System.Uri> 使用方法设置 cookie 的位置的 <xref:System.Windows.Application.SetCookie%2A> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-376">You retrieve both session and persistent cookies by calling the <xref:System.Windows.Application.GetCookie%2A> method, passing the <xref:System.Uri> of the location where the cookie was set with the <xref:System.Windows.Application.SetCookie%2A> method.</span></span>

<span data-ttu-id="1e267-377">下面是在 WPF 中支持 cookie 的一些方法：</span><span class="sxs-lookup"><span data-stu-id="1e267-377">The following are some of the ways that cookies are supported in WPF:</span></span>

- <span data-ttu-id="1e267-378">WPF 独立应用程序和 Xbap 可以创建和管理 cookie。</span><span class="sxs-lookup"><span data-stu-id="1e267-378">WPF standalone applications and XBAPs can both create and manage cookies.</span></span>

- <span data-ttu-id="1e267-379">可以从浏览器访问 XBAP 创建的 cookie。</span><span class="sxs-lookup"><span data-stu-id="1e267-379">Cookies that are created by an XBAP can be accessed from the browser.</span></span>

- <span data-ttu-id="1e267-380">同一个域中的 Xbap 可以创建和共享 cookie。</span><span class="sxs-lookup"><span data-stu-id="1e267-380">XBAPs from the same domain can create and share cookies.</span></span>

- <span data-ttu-id="1e267-381">同一域中的 Xbap 和 HTML 页可以创建和共享 cookie。</span><span class="sxs-lookup"><span data-stu-id="1e267-381">XBAPs and HTML pages from the same domain can create and share cookies.</span></span>

- <span data-ttu-id="1e267-382">当 Xbap 和松散 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 页发出 Web 请求时，会调度 cookie。</span><span class="sxs-lookup"><span data-stu-id="1e267-382">Cookies are dispatched when XBAPs and loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pages make Web requests.</span></span>

- <span data-ttu-id="1e267-383">在 IFRAME 中承载的顶级 Xbap 和 Xbap 都可以访问 cookie。</span><span class="sxs-lookup"><span data-stu-id="1e267-383">Both top-level XBAPs and XBAPs hosted in IFRAMES can access cookies.</span></span>

- <span data-ttu-id="1e267-384">WPF 中的 Cookie 支持对于所有受支持的浏览器都是相同的。</span><span class="sxs-lookup"><span data-stu-id="1e267-384">Cookie support in WPF is the same for all supported browsers.</span></span>

- <span data-ttu-id="1e267-385">在 Internet Explorer 中，与 cookie 相关的 P3P 策略由 WPF 提供，特别是对于第一方和第三方 Xbap。</span><span class="sxs-lookup"><span data-stu-id="1e267-385">In Internet Explorer, P3P policy that pertains to cookies is honored by WPF, particularly with respect to first-party and third-party XBAPs.</span></span>

<a name="Structured_Navigation"></a>

### <a name="structured-navigation"></a><span data-ttu-id="1e267-386">结构化导航</span><span class="sxs-lookup"><span data-stu-id="1e267-386">Structured Navigation</span></span>

<span data-ttu-id="1e267-387">如果需要将数据从一个传递 <xref:System.Windows.Controls.Page> 到另一个，则可以将数据作为参数传递给的非参数构造函数 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-387">If you need to pass data from one <xref:System.Windows.Controls.Page> to another, you can pass the data as arguments to a non-parameterless constructor of the <xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="1e267-388">请注意，如果使用此方法，则必须保持 <xref:System.Windows.Controls.Page> 活动状态; 否则，下一次导航到时 <xref:System.Windows.Controls.Page> ，WPF 将 <xref:System.Windows.Controls.Page> 使用无参数构造函数重新实例化。</span><span class="sxs-lookup"><span data-stu-id="1e267-388">Note that if you use this technique, you must keep the <xref:System.Windows.Controls.Page> alive; if not, the next time you navigate to the <xref:System.Windows.Controls.Page>, WPF reinstantiates the <xref:System.Windows.Controls.Page> by using the parameterless constructor.</span></span>

<span data-ttu-id="1e267-389">或者，你 <xref:System.Windows.Controls.Page> 可以实现用需要传递的数据设置的属性。</span><span class="sxs-lookup"><span data-stu-id="1e267-389">Alternatively, your <xref:System.Windows.Controls.Page> can implement properties that are set with the data that needs to be passed.</span></span> <span data-ttu-id="1e267-390">不过，当 <xref:System.Windows.Controls.Page> 需要将数据传递回导航到该数据的时，这会变得困难 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-390">Things become tricky, however, when a <xref:System.Windows.Controls.Page> needs to pass data back to the <xref:System.Windows.Controls.Page> that navigated to it.</span></span> <span data-ttu-id="1e267-391">问题在于，导航不会以本机方式支持用于确保在 <xref:System.Windows.Controls.Page> 从其导航后将返回到的机制。</span><span class="sxs-lookup"><span data-stu-id="1e267-391">The problem is that navigation doesn't natively support mechanisms for guaranteeing that a <xref:System.Windows.Controls.Page> will be returned to after it is navigated from.</span></span> <span data-ttu-id="1e267-392">实质上，导航不支持调用/返回语义。</span><span class="sxs-lookup"><span data-stu-id="1e267-392">Essentially, navigation doesn't support call/return semantics.</span></span> <span data-ttu-id="1e267-393">为了解决此问题，WPF 提供了 <xref:System.Windows.Navigation.PageFunction%601> 类，可用于确保以 <xref:System.Windows.Controls.Page> 可预测的结构化方式返回到。</span><span class="sxs-lookup"><span data-stu-id="1e267-393">To solve this problem, WPF provides the <xref:System.Windows.Navigation.PageFunction%601> class that you can use to ensure that a <xref:System.Windows.Controls.Page> is returned to in a predictable and structured fashion.</span></span> <span data-ttu-id="1e267-394">有关详细信息，请参阅[结构化导航概述](structured-navigation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="1e267-394">For more information, see [Structured Navigation Overview](structured-navigation-overview.md).</span></span>

<a name="The_NavigationWindow_Class"></a>

## <a name="the-navigationwindow-class"></a><span data-ttu-id="1e267-395">NavigationWindow 类</span><span class="sxs-lookup"><span data-stu-id="1e267-395">The NavigationWindow Class</span></span>

<span data-ttu-id="1e267-396">到目前为止，你已全面了解最有可能用可导航内容生成应用程序的导航服务。</span><span class="sxs-lookup"><span data-stu-id="1e267-396">To this point, you've seen the gamut of navigation services that you are most likely to use to build applications with navigable content.</span></span> <span data-ttu-id="1e267-397">这些服务在 Xbap 的上下文中进行了讨论，不过它们并不局限于 Xbap。</span><span class="sxs-lookup"><span data-stu-id="1e267-397">These services were discussed in the context of XBAPs, although they are not limited to XBAPs.</span></span> <span data-ttu-id="1e267-398">现代操作系统和 Windows 应用程序利用了新式用户的浏览器体验，将浏览器样式的导航并入独立的应用程序。</span><span class="sxs-lookup"><span data-stu-id="1e267-398">Modern operating systems and Windows applications take advantage of the browser experience of modern users to incorporate browser-style navigation into standalone applications.</span></span> <span data-ttu-id="1e267-399">常见示例包括：</span><span class="sxs-lookup"><span data-stu-id="1e267-399">Common examples include:</span></span>

- <span data-ttu-id="1e267-400">**Word 同义词库**：导航字选择。</span><span class="sxs-lookup"><span data-stu-id="1e267-400">**Word Thesaurus**: Navigate word choices.</span></span>

- <span data-ttu-id="1e267-401">**文件资源管理器**：导航文件和文件夹。</span><span class="sxs-lookup"><span data-stu-id="1e267-401">**File Explorer**: Navigate files and folders.</span></span>

- <span data-ttu-id="1e267-402">**向导**：将复杂任务分为多页，可以在它们之间导航。</span><span class="sxs-lookup"><span data-stu-id="1e267-402">**Wizards**: Breaking down a complex task into multiple pages that can be navigated between.</span></span> <span data-ttu-id="1e267-403">例如，处理添加和删除 Windows 功能的 Windows 组件向导。</span><span class="sxs-lookup"><span data-stu-id="1e267-403">An example is the Windows Components Wizard that handles adding and removing Windows features.</span></span>

<span data-ttu-id="1e267-404">若要将浏览器样式的导航并入独立应用程序，可以使用 <xref:System.Windows.Navigation.NavigationWindow> 类。</span><span class="sxs-lookup"><span data-stu-id="1e267-404">To incorporate browser-style navigation into your standalone applications, you can use the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="1e267-405"><xref:System.Windows.Navigation.NavigationWindow>派生自 <xref:System.Windows.Window> ，并对 xbap 提供的导航支持相同的扩展。</span><span class="sxs-lookup"><span data-stu-id="1e267-405"><xref:System.Windows.Navigation.NavigationWindow> derives from <xref:System.Windows.Window> and extends it with the same support for navigation that XBAPs provide.</span></span> <span data-ttu-id="1e267-406">你可以将 <xref:System.Windows.Navigation.NavigationWindow> 作为独立应用程序的主窗口，也可以用作辅助窗口（如对话框）。</span><span class="sxs-lookup"><span data-stu-id="1e267-406">You can use <xref:System.Windows.Navigation.NavigationWindow> as either the main window of your standalone application or as a secondary window such as a dialog box.</span></span>

<span data-ttu-id="1e267-407">若要实现 <xref:System.Windows.Navigation.NavigationWindow> ，与 WPF 中的大多数顶级类（ <xref:System.Windows.Window> 、 <xref:System.Windows.Controls.Page> 等）结合使用，可以使用标记和代码隐藏。</span><span class="sxs-lookup"><span data-stu-id="1e267-407">To implement a <xref:System.Windows.Navigation.NavigationWindow>, as with most top-level classes in WPF (<xref:System.Windows.Window>, <xref:System.Windows.Controls.Page>, and so on), you use a combination of markup and code-behind.</span></span> <span data-ttu-id="1e267-408">这在下面的示例中显示。</span><span class="sxs-lookup"><span data-stu-id="1e267-408">This is shown in the following example.</span></span>

[!code-xaml[IntroToNavNavigationWindowSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml#navigationwindowmarkup)]

[!code-csharp[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml.cs#navigationwindowcodebehind)]
[!code-vb[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/MainWindow.xaml.vb#navigationwindowcodebehind)]

<span data-ttu-id="1e267-409">此代码将创建一个 <xref:System.Windows.Navigation.NavigationWindow> ，它在打开时会自动导航到 <xref:System.Windows.Controls.Page> （主页 .xaml） <xref:System.Windows.Navigation.NavigationWindow> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-409">This code creates a <xref:System.Windows.Navigation.NavigationWindow> that automatically navigates to a <xref:System.Windows.Controls.Page> (HomePage.xaml) when the <xref:System.Windows.Navigation.NavigationWindow> is opened.</span></span> <span data-ttu-id="1e267-410">如果 <xref:System.Windows.Navigation.NavigationWindow> 是主应用程序窗口，则可以使用 `StartupUri` 属性来启动它。</span><span class="sxs-lookup"><span data-stu-id="1e267-410">If the <xref:System.Windows.Navigation.NavigationWindow> is the main application window, you can use the `StartupUri` attribute to launch it.</span></span> <span data-ttu-id="1e267-411">这在以下标记中显示。</span><span class="sxs-lookup"><span data-stu-id="1e267-411">This is shown in the following markup.</span></span>

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchNavWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/App.xaml#applaunchnavwindow)]

<span data-ttu-id="1e267-412">下图显示的是 <xref:System.Windows.Navigation.NavigationWindow> 独立应用程序的主窗口。</span><span class="sxs-lookup"><span data-stu-id="1e267-412">The following figure shows the <xref:System.Windows.Navigation.NavigationWindow> as the main window of a standalone application.</span></span>

<span data-ttu-id="1e267-413">![主窗口](./media/navigation-overview/navigation-window-as-main-window.png "作为主窗口的导航窗口")</span><span class="sxs-lookup"><span data-stu-id="1e267-413">![A main window](./media/navigation-overview/navigation-window-as-main-window.png "Navigation window as the main window")</span></span>

<span data-ttu-id="1e267-414">从图中可以看到， <xref:System.Windows.Navigation.NavigationWindow> 具有标题，即使未在 <xref:System.Windows.Navigation.NavigationWindow> 前面示例的实现代码中进行设置也是如此。</span><span class="sxs-lookup"><span data-stu-id="1e267-414">From the figure, you can see that the <xref:System.Windows.Navigation.NavigationWindow> has a title, even though it wasn't set in the <xref:System.Windows.Navigation.NavigationWindow> implementation code from the preceding example.</span></span> <span data-ttu-id="1e267-415">而是使用属性设置标题 <xref:System.Windows.Controls.Page.WindowTitle%2A> ，如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="1e267-415">Instead, the title is set using the <xref:System.Windows.Controls.Page.WindowTitle%2A> property, which is shown in the following code.</span></span>

[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup1)]
[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup2)]

<span data-ttu-id="1e267-416">设置 <xref:System.Windows.Controls.Page.WindowWidth%2A> 和 <xref:System.Windows.Controls.Page.WindowHeight%2A> 属性还会影响 <xref:System.Windows.Navigation.NavigationWindow> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-416">Setting the <xref:System.Windows.Controls.Page.WindowWidth%2A> and <xref:System.Windows.Controls.Page.WindowHeight%2A> properties also affects the <xref:System.Windows.Navigation.NavigationWindow>.</span></span>

<span data-ttu-id="1e267-417">通常， <xref:System.Windows.Navigation.NavigationWindow> 当你需要自定义其行为或外观时，可以自行实现。</span><span class="sxs-lookup"><span data-stu-id="1e267-417">Usually, you implement your own <xref:System.Windows.Navigation.NavigationWindow> when you need to customize either its behavior or its appearance.</span></span> <span data-ttu-id="1e267-418">如果没有执行上述操作，则可以使用快捷方式。</span><span class="sxs-lookup"><span data-stu-id="1e267-418">If you do neither, you can use a shortcut.</span></span> <span data-ttu-id="1e267-419">如果在独立的应用程序中将的 pack URI 指定 <xref:System.Windows.Controls.Page> 为 <xref:System.Windows.Application.StartupUri%2A> ，则 <xref:System.Windows.Application> 会自动创建 <xref:System.Windows.Navigation.NavigationWindow> 来承载的 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-419">If you specify the pack URI of a <xref:System.Windows.Controls.Page> as the <xref:System.Windows.Application.StartupUri%2A> in a standalone application, <xref:System.Windows.Application> automatically creates a <xref:System.Windows.Navigation.NavigationWindow> to host the <xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="1e267-420">以下标记显示如何实现此功能。</span><span class="sxs-lookup"><span data-stu-id="1e267-420">The following markup shows how to enable this.</span></span>

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchPage](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/AnotherApp.xaml#applaunchpage)]

<span data-ttu-id="1e267-421">如果希望将辅助应用程序窗口（如对话框 <xref:System.Windows.Navigation.NavigationWindow> ）作为，可以使用以下示例中的代码将其打开。</span><span class="sxs-lookup"><span data-stu-id="1e267-421">If you want a secondary application window such as a dialog box to be a <xref:System.Windows.Navigation.NavigationWindow>, you can use the code in the following example to open it.</span></span>

[!code-csharp[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/DialogOwnerWindow.xaml.cs#createnwdialogbox)]
[!code-vb[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/DialogOwnerWindow.xaml.vb#createnwdialogbox)]

<span data-ttu-id="1e267-422">下图显示结果。</span><span class="sxs-lookup"><span data-stu-id="1e267-422">The following figure shows the result.</span></span>

<span data-ttu-id="1e267-423">![对话框](./media/navigation-overview/navigation-window-as-dialog-box.png "作为对话框的导航窗口")</span><span class="sxs-lookup"><span data-stu-id="1e267-423">![A dialog box](./media/navigation-overview/navigation-window-as-dialog-box.png "Navigation window as a dialog box")</span></span>

<span data-ttu-id="1e267-424">如您所见，会 <xref:System.Windows.Navigation.NavigationWindow> 显示允许用户导航日记的 Internet Explorer 样式的 "**后退**" 和 "**前进**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="1e267-424">As you can see, <xref:System.Windows.Navigation.NavigationWindow> displays Internet Explorer-style **Back** and **Forward** buttons that allow users to navigate the journal.</span></span> <span data-ttu-id="1e267-425">这些按钮提供相同的用户体验，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="1e267-425">These buttons provide the same user experience, as shown in the following figure.</span></span>

<span data-ttu-id="1e267-426">![NavigationWindow 中的“后退”和“前进”按钮](./media/navigation-overview/back-and-forward-buttons-in-navigation-window.png "导航窗口中的 "后退" 和 "前进" 按钮")</span><span class="sxs-lookup"><span data-stu-id="1e267-426">![Back and Forward buttons in a NavigationWindow](./media/navigation-overview/back-and-forward-buttons-in-navigation-window.png "Back and Forward buttons in a Navigation window")</span></span>

<span data-ttu-id="1e267-427">如果页面提供其自己的日记导航支持和 UI，则可以**Forward**通过将**Back** <xref:System.Windows.Navigation.NavigationWindow> 属性的值设置为来隐藏显示的 "后退" 和 "前进" 按钮 <xref:System.Windows.Navigation.NavigationWindow.ShowsNavigationUI%2A> `false` 。</span><span class="sxs-lookup"><span data-stu-id="1e267-427">If your pages provide their own journal navigation support and UI, you can hide the **Back** and **Forward** buttons displayed by <xref:System.Windows.Navigation.NavigationWindow> by setting the value of the <xref:System.Windows.Navigation.NavigationWindow.ShowsNavigationUI%2A> property to `false`.</span></span>

<span data-ttu-id="1e267-428">此外，还可以使用 WPF 中的自定义支持来替换 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Navigation.NavigationWindow> 自身的。</span><span class="sxs-lookup"><span data-stu-id="1e267-428">Alternatively, you can use customization support in WPF to replace the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] of the <xref:System.Windows.Navigation.NavigationWindow> itself.</span></span>

<a name="Frame_in_Standalone_Applications"></a>

## <a name="the-frame-class"></a><span data-ttu-id="1e267-429">框架类</span><span class="sxs-lookup"><span data-stu-id="1e267-429">The Frame Class</span></span>

<span data-ttu-id="1e267-430">浏览器和 <xref:System.Windows.Navigation.NavigationWindow> 都是托管可导航内容的窗口。</span><span class="sxs-lookup"><span data-stu-id="1e267-430">Both the browser and <xref:System.Windows.Navigation.NavigationWindow> are windows that host navigable content.</span></span> <span data-ttu-id="1e267-431">在某些情况下，应用程序具有无需整个窗口托管的内容。</span><span class="sxs-lookup"><span data-stu-id="1e267-431">In some cases, applications have content that does not need to be hosted by an entire window.</span></span> <span data-ttu-id="1e267-432">相反，此类内容在其他内容中托管。</span><span class="sxs-lookup"><span data-stu-id="1e267-432">Instead, such content be hosted inside other content.</span></span> <span data-ttu-id="1e267-433">可以使用类将导向性内容插入到其他内容中 <xref:System.Windows.Controls.Frame> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-433">You can insert navigable content into other content by using the <xref:System.Windows.Controls.Frame> class.</span></span> <span data-ttu-id="1e267-434"><xref:System.Windows.Controls.Frame>提供与和 Xbap 相同的支持 <xref:System.Windows.Navigation.NavigationWindow> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-434"><xref:System.Windows.Controls.Frame> provides the same support as <xref:System.Windows.Navigation.NavigationWindow> and XBAPs.</span></span>

<span data-ttu-id="1e267-435">下面的示例演示如何使用元素以声明方式将添加 <xref:System.Windows.Controls.Frame> 到 <xref:System.Windows.Controls.Page> `Frame` 。</span><span class="sxs-lookup"><span data-stu-id="1e267-435">The following example shows how to add a <xref:System.Windows.Controls.Frame> to a <xref:System.Windows.Controls.Page> declaratively by using the `Frame` element.</span></span>

[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml3)]

<span data-ttu-id="1e267-436">此标记设置 `Source` 元素的属性， `Frame` 其中包含 <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Frame> 最初应导航到的的包 URI。</span><span class="sxs-lookup"><span data-stu-id="1e267-436">This markup sets the `Source` attribute of the `Frame` element with a pack URI for the <xref:System.Windows.Controls.Page> that the <xref:System.Windows.Controls.Frame> should initially navigate to.</span></span> <span data-ttu-id="1e267-437">下图显示了一个具有已在 <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Frame> 多个页面之间导航的的 XBAP。</span><span class="sxs-lookup"><span data-stu-id="1e267-437">The following figure shows an XBAP with a <xref:System.Windows.Controls.Page> that has a <xref:System.Windows.Controls.Frame> that has navigated between several pages.</span></span>

<span data-ttu-id="1e267-438">![已在多页之间导航的框架](./media/navigation-overview/frame-navigation-between-multiple-pages.png "这会显示多个页面之间的帧导航。")</span><span class="sxs-lookup"><span data-stu-id="1e267-438">![A frame that has navigated between multiple pages](./media/navigation-overview/frame-navigation-between-multiple-pages.png "This shows a frame navigation between multiple pages.")</span></span>

<span data-ttu-id="1e267-439">你不必在的 <xref:System.Windows.Controls.Frame> 内容内使用 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-439">You don't only have to use <xref:System.Windows.Controls.Frame> inside the content of a <xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="1e267-440">在的 <xref:System.Windows.Controls.Frame> 内容中托管 <xref:System.Windows.Window> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-440">It is also common to host a <xref:System.Windows.Controls.Frame> inside the content of a <xref:System.Windows.Window>.</span></span>

<span data-ttu-id="1e267-441">默认情况下， <xref:System.Windows.Controls.Frame> 只有在没有其他日志时才使用自己的日记。</span><span class="sxs-lookup"><span data-stu-id="1e267-441">By default, <xref:System.Windows.Controls.Frame> only uses its own journal in the absence of another journal.</span></span> <span data-ttu-id="1e267-442">如果 <xref:System.Windows.Controls.Frame> 是在或 xbap 内承载的内容的一部分 <xref:System.Windows.Navigation.NavigationWindow> ，则 <xref:System.Windows.Controls.Frame> 使用属于 <xref:System.Windows.Navigation.NavigationWindow> 或 xbap 的日记。</span><span class="sxs-lookup"><span data-stu-id="1e267-442">If a <xref:System.Windows.Controls.Frame> is part of content that is hosted inside either a <xref:System.Windows.Navigation.NavigationWindow> or an XBAP, <xref:System.Windows.Controls.Frame> uses the journal that belongs to the <xref:System.Windows.Navigation.NavigationWindow> or XBAP.</span></span> <span data-ttu-id="1e267-443">但是，有时 <xref:System.Windows.Controls.Frame> 可能需要负责自己的日记。</span><span class="sxs-lookup"><span data-stu-id="1e267-443">Sometimes, though, a <xref:System.Windows.Controls.Frame> might need to be responsible for its own journal.</span></span> <span data-ttu-id="1e267-444">这样做的一个原因是允许在承载的页面内进行日志导航 <xref:System.Windows.Controls.Frame> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-444">One reason to do so is to allow journal navigation within the pages that are hosted by a <xref:System.Windows.Controls.Frame>.</span></span> <span data-ttu-id="1e267-445">这由下图说明。</span><span class="sxs-lookup"><span data-stu-id="1e267-445">This is illustrated by the following figure.</span></span>

<span data-ttu-id="1e267-446">![框架和页面示意图](./media/navigation-overview/journal-navigation-within-pages-hosted-by-a-frame.png "这会在框架托管的页中显示日志导航。")</span><span class="sxs-lookup"><span data-stu-id="1e267-446">![Frame and Page diagram](./media/navigation-overview/journal-navigation-within-pages-hosted-by-a-frame.png "This shows journal navigation within pages hosted by a frame.")</span></span>

<span data-ttu-id="1e267-447">在这种情况下，你可以 <xref:System.Windows.Controls.Frame> 通过将的属性设置为来将配置为使用自己的日记 <xref:System.Windows.Controls.Frame.JournalOwnership%2A> <xref:System.Windows.Controls.Frame> <xref:System.Windows.Navigation.JournalOwnership.OwnsJournal> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-447">In this case, you can configure the <xref:System.Windows.Controls.Frame> to use its own journal by setting the <xref:System.Windows.Controls.Frame.JournalOwnership%2A> property of the <xref:System.Windows.Controls.Frame> to <xref:System.Windows.Navigation.JournalOwnership.OwnsJournal>.</span></span> <span data-ttu-id="1e267-448">这在以下标记中显示。</span><span class="sxs-lookup"><span data-stu-id="1e267-448">This is shown in the following markup.</span></span>

[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml3)]

<span data-ttu-id="1e267-449">下图说明了在使用自己的日记的中导航的效果 <xref:System.Windows.Controls.Frame> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-449">The following figure illustrates the effect of navigating within a <xref:System.Windows.Controls.Frame> that uses its own journal.</span></span>

<span data-ttu-id="1e267-450">![使用自己的日记的框架](./media/navigation-overview/frame-uses-its-own-journal.png "这显示了在使用其自己的日记的帧中导航的效果。")</span><span class="sxs-lookup"><span data-stu-id="1e267-450">![A frame that uses its own journal](./media/navigation-overview/frame-uses-its-own-journal.png "This shows the effect of navigating within a frame that uses its own journal.")</span></span>

<span data-ttu-id="1e267-451">请注意 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ，在中的导航 <xref:System.Windows.Controls.Frame> （而不是 Internet Explorer）中显示日记条目。</span><span class="sxs-lookup"><span data-stu-id="1e267-451">Notice that the journal entries are shown by the navigation [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] in the <xref:System.Windows.Controls.Frame>, rather than by Internet Explorer.</span></span>

> [!NOTE]
> <span data-ttu-id="1e267-452">如果 <xref:System.Windows.Controls.Frame> 是在中承载的内容的一部分，则 <xref:System.Windows.Window> <xref:System.Windows.Controls.Frame> 使用其自己的日记，因此会显示自己的导航 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1e267-452">If a <xref:System.Windows.Controls.Frame> is part of content that is hosted in a <xref:System.Windows.Window>, <xref:System.Windows.Controls.Frame> uses its own journal and, consequently, displays its own navigation [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span></span>

<span data-ttu-id="1e267-453">如果你的用户体验需要 <xref:System.Windows.Controls.Frame> 提供自己的日记而不显示导航 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ，则可以 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 通过将设置为来隐藏导航 <xref:System.Windows.Controls.Frame.NavigationUIVisibility%2A> <xref:System.Windows.Visibility.Hidden> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-453">If your user experience requires a <xref:System.Windows.Controls.Frame> to provide its own journal without showing the navigation [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], you can hide the navigation [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] by setting the <xref:System.Windows.Controls.Frame.NavigationUIVisibility%2A> to <xref:System.Windows.Visibility.Hidden>.</span></span> <span data-ttu-id="1e267-454">这在以下标记中显示。</span><span class="sxs-lookup"><span data-stu-id="1e267-454">This is shown in the following markup.</span></span>

[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml3)]

<a name="Navigation_Hosts"></a>

## <a name="navigation-hosts"></a><span data-ttu-id="1e267-455">导航主机</span><span class="sxs-lookup"><span data-stu-id="1e267-455">Navigation Hosts</span></span>

<span data-ttu-id="1e267-456"><xref:System.Windows.Controls.Frame>和 <xref:System.Windows.Navigation.NavigationWindow> 是称为导航宿主的类。</span><span class="sxs-lookup"><span data-stu-id="1e267-456"><xref:System.Windows.Controls.Frame> and <xref:System.Windows.Navigation.NavigationWindow> are classes that are known as navigation hosts.</span></span> <span data-ttu-id="1e267-457">*导航宿主*是可导航到并显示内容的类。</span><span class="sxs-lookup"><span data-stu-id="1e267-457">A *navigation host* is a class that can navigate to and display content.</span></span> <span data-ttu-id="1e267-458">为实现此目的，每个导航宿主都使用其自己的 <xref:System.Windows.Navigation.NavigationService> 和日志。</span><span class="sxs-lookup"><span data-stu-id="1e267-458">To accomplish this, each navigation host uses its own <xref:System.Windows.Navigation.NavigationService> and journal.</span></span> <span data-ttu-id="1e267-459">导航主机的基本构造在下图中显示。</span><span class="sxs-lookup"><span data-stu-id="1e267-459">The basic construction of a navigation host is shown in the following figure.</span></span>

<span data-ttu-id="1e267-460">![导航器示意图](./media/navigation-overview/navigation-host-construction.png "导航宿主的基本构造")</span><span class="sxs-lookup"><span data-stu-id="1e267-460">![Navigator diagrams](./media/navigation-overview/navigation-host-construction.png "Basic construction of a navigation host")</span></span>

<span data-ttu-id="1e267-461">实质上，这允许 <xref:System.Windows.Navigation.NavigationWindow> 和 <xref:System.Windows.Controls.Frame> 提供 XBAP 在浏览器中承载时提供的相同导航支持。</span><span class="sxs-lookup"><span data-stu-id="1e267-461">Essentially, this allows <xref:System.Windows.Navigation.NavigationWindow> and <xref:System.Windows.Controls.Frame> to provide the same navigation support that an XBAP provides when hosted in the browser.</span></span>

<span data-ttu-id="1e267-462">除了使用 <xref:System.Windows.Navigation.NavigationService> 和日记，导航宿主还实现实现相同的成员 <xref:System.Windows.Navigation.NavigationService> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-462">Besides using <xref:System.Windows.Navigation.NavigationService> and a journal, navigation hosts implement the same members that <xref:System.Windows.Navigation.NavigationService> implements.</span></span> <span data-ttu-id="1e267-463">这由下图说明。</span><span class="sxs-lookup"><span data-stu-id="1e267-463">This is illustrated by the following figure.</span></span>

<span data-ttu-id="1e267-464">![Frame 和 NavigationWindow 中的日记](./media/navigation-overview/navigation-window-and-frame.png "导航窗口和框架")</span><span class="sxs-lookup"><span data-stu-id="1e267-464">![A journal in a Frame and in a NavigationWindow](./media/navigation-overview/navigation-window-and-frame.png "Navigation Window and Frame")</span></span>

<span data-ttu-id="1e267-465">这就允许直接对它们进行导航支持编程。</span><span class="sxs-lookup"><span data-stu-id="1e267-465">This allows you to program navigation support directly against them.</span></span> <span data-ttu-id="1e267-466">如果需要为中托管的提供自定义导航，则可以考虑此情况 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Controls.Frame> <xref:System.Windows.Window> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-466">You may consider this if you need to provide a custom navigation [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] for a <xref:System.Windows.Controls.Frame> that is hosted in a <xref:System.Windows.Window>.</span></span> <span data-ttu-id="1e267-467">此外，这两种类型都实现了与导航相关的附加成员，其中包括 `BackStack` （ <xref:System.Windows.Navigation.NavigationWindow.BackStack%2A?displayProperty=nameWithType> 、 <xref:System.Windows.Controls.Frame.BackStack%2A?displayProperty=nameWithType> ）和 `ForwardStack` （ <xref:System.Windows.Navigation.NavigationWindow.ForwardStack%2A?displayProperty=nameWithType> ， <xref:System.Windows.Controls.Frame.ForwardStack%2A?displayProperty=nameWithType> ），这使您可以分别枚举后退堆栈和前进堆栈中的日记条目。</span><span class="sxs-lookup"><span data-stu-id="1e267-467">Furthermore, both types implement additional, navigation-related members, including `BackStack` (<xref:System.Windows.Navigation.NavigationWindow.BackStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.BackStack%2A?displayProperty=nameWithType>) and `ForwardStack` (<xref:System.Windows.Navigation.NavigationWindow.ForwardStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.ForwardStack%2A?displayProperty=nameWithType>), which allow you to enumerate the journal entries in the back stack and forward stack, respectively.</span></span>

<span data-ttu-id="1e267-468">如之前提及，应用程序中可以存在不止一个日志。</span><span class="sxs-lookup"><span data-stu-id="1e267-468">As mentioned earlier, more than one journal can exist within an application.</span></span> <span data-ttu-id="1e267-469">下图提供何时可能发生这种情况的示例。</span><span class="sxs-lookup"><span data-stu-id="1e267-469">The following figure provides an example of when this can happen.</span></span>

<span data-ttu-id="1e267-470">![一个应用程序内的多个日记](./media/navigation-overview/multiple-journals-in-one-application.png "这是一个应用程序中多个日记的示例。")</span><span class="sxs-lookup"><span data-stu-id="1e267-470">![Multiple journals within one application](./media/navigation-overview/multiple-journals-in-one-application.png "This is an example of more than one journal in an application.")</span></span>

<a name="Navigating_to_Content_Other_than_Pages"></a>

## <a name="navigating-to-content-other-than-xaml-pages"></a><span data-ttu-id="1e267-471">导航到非 XAML 页内容</span><span class="sxs-lookup"><span data-stu-id="1e267-471">Navigating to Content Other than XAML Pages</span></span>

<span data-ttu-id="1e267-472">本主题中的 <xref:System.Windows.Controls.Page> 和 Pack xbap 已用于演示 WPF 的各种导航功能。</span><span class="sxs-lookup"><span data-stu-id="1e267-472">Throughout this topic, <xref:System.Windows.Controls.Page> and pack XBAPs have been used to demonstrate the various navigation capabilities of WPF.</span></span> <span data-ttu-id="1e267-473">但是， <xref:System.Windows.Controls.Page> 编译到应用程序中的内容并不是可以导航到的唯一内容类型，Pack xbap 不是标识内容的唯一方法。</span><span class="sxs-lookup"><span data-stu-id="1e267-473">However, a <xref:System.Windows.Controls.Page> that is compiled into an application is not the only type of content that can be navigated to, and pack XBAPs aren't the only way to identify content.</span></span>

<span data-ttu-id="1e267-474">如本部分所示，你还可以导航到松散 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 文件、HTML 文件和对象。</span><span class="sxs-lookup"><span data-stu-id="1e267-474">As this section demonstrates, you can also navigate to loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files, HTML files, and objects.</span></span>

<a name="Navigating_to_Loose_XAML_Files"></a>

### <a name="navigating-to-loose-xaml-files"></a><span data-ttu-id="1e267-475">导航到松散 XAML 文件</span><span class="sxs-lookup"><span data-stu-id="1e267-475">Navigating to Loose XAML Files</span></span>

<span data-ttu-id="1e267-476">松散 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 文件是具有以下特征的文件：</span><span class="sxs-lookup"><span data-stu-id="1e267-476">A loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is a file with the following characteristics:</span></span>

- <span data-ttu-id="1e267-477">仅包含 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] （即，不包含任何代码）。</span><span class="sxs-lookup"><span data-stu-id="1e267-477">Contains only [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (that is, no code).</span></span>

- <span data-ttu-id="1e267-478">具有适当的命名空间声明。</span><span class="sxs-lookup"><span data-stu-id="1e267-478">Has an appropriate namespace declaration.</span></span>

- <span data-ttu-id="1e267-479">具有 .xaml 文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="1e267-479">Has the .xaml file name extension.</span></span>

<span data-ttu-id="1e267-480">例如，请考虑以下存储为松散 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 文件 "Person" 的内容。</span><span class="sxs-lookup"><span data-stu-id="1e267-480">For example, consider the following content that is stored as a loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file, Person.xaml.</span></span>

[!code-xaml[NavigationOverviewSnippets#LooseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Person.xaml#loosexaml)]

<span data-ttu-id="1e267-481">双击该文件时，浏览器打开、导航到并显示内容。</span><span class="sxs-lookup"><span data-stu-id="1e267-481">When you double-click the file, the browser opens and navigates to and displays the content.</span></span> <span data-ttu-id="1e267-482">如下图所示。</span><span class="sxs-lookup"><span data-stu-id="1e267-482">This is shown in the following figure.</span></span>

<span data-ttu-id="1e267-483">![Person.XAML 文件中的内容的显示](./media/navigation-overview/contents-of-person-xaml-file.png "显示 Person 文件的内容。")</span><span class="sxs-lookup"><span data-stu-id="1e267-483">![Display of the content in the Person.XAML file](./media/navigation-overview/contents-of-person-xaml-file.png "Shows the contents of the Person.XAML file.")</span></span>

<span data-ttu-id="1e267-484">可显示 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 以下内容的松散文件：</span><span class="sxs-lookup"><span data-stu-id="1e267-484">You can display a loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file from the following:</span></span>

- <span data-ttu-id="1e267-485">本地计算机上的网站、Intranet 或 Internet。</span><span class="sxs-lookup"><span data-stu-id="1e267-485">A Web site on the local machine, the intranet, or the Internet.</span></span>

- <span data-ttu-id="1e267-486">通用命名约定（UNC）文件共享。</span><span class="sxs-lookup"><span data-stu-id="1e267-486">A Universal Naming Convention (UNC) file share.</span></span>

- <span data-ttu-id="1e267-487">本地磁盘。</span><span class="sxs-lookup"><span data-stu-id="1e267-487">The local disk.</span></span>

<span data-ttu-id="1e267-488">可以将松散 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 文件添加到浏览器的收藏夹，或浏览器的主页。</span><span class="sxs-lookup"><span data-stu-id="1e267-488">A loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file can be added to the browser's favorites, or be the browser's home page.</span></span>

> [!NOTE]
> <span data-ttu-id="1e267-489">有关发布和启动松散页面的详细信息 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，请参阅[部署 WPF 应用程序](deploying-a-wpf-application-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="1e267-489">For more information about publishing and launching loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pages, see [Deploying a WPF Application](deploying-a-wpf-application-wpf.md).</span></span>

<span data-ttu-id="1e267-490">松散的一项限制 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 是您只能承载安全地在部分信任环境中运行的内容。</span><span class="sxs-lookup"><span data-stu-id="1e267-490">One limitation with respect to loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] is that you can only host content that is safe to run in partial trust.</span></span> <span data-ttu-id="1e267-491">例如， `Window` 不能是松散文件的根元素 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1e267-491">For example, `Window` cannot be the root element of a loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="1e267-492">有关详细信息，请参阅 [WPF 部分信任安全性](../wpf-partial-trust-security.md)。</span><span class="sxs-lookup"><span data-stu-id="1e267-492">For more information, see [WPF Partial Trust Security](../wpf-partial-trust-security.md).</span></span>

<a name="Navigating_to_HTML_Files_Using_Frame"></a>

### <a name="navigating-to-html-files-by-using-frame"></a><span data-ttu-id="1e267-493">通过使用框架导航到 HTML 文件</span><span class="sxs-lookup"><span data-stu-id="1e267-493">Navigating to HTML Files by Using Frame</span></span>

<span data-ttu-id="1e267-494">正如您所料，还可以导航到 HTML。</span><span class="sxs-lookup"><span data-stu-id="1e267-494">As you might expect, you can also navigate to HTML.</span></span> <span data-ttu-id="1e267-495">只需提供使用 http 方案的 URI 即可。</span><span class="sxs-lookup"><span data-stu-id="1e267-495">You simply need to provide a URI that uses the http scheme.</span></span> <span data-ttu-id="1e267-496">例如，下面的示例 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 演示一个 <xref:System.Windows.Controls.Frame> 导航到 HTML 页的。</span><span class="sxs-lookup"><span data-stu-id="1e267-496">For example, the following [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] shows a <xref:System.Windows.Controls.Frame> that navigates to an HTML page.</span></span>

[!code-xaml[NavigationOverviewSnippets#FrameHtmlNavMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHTMLNavPage.xaml#framehtmlnavmarkup)]

<span data-ttu-id="1e267-497">导航到 HTML 需要特殊权限。</span><span class="sxs-lookup"><span data-stu-id="1e267-497">Navigating to HTML requires special permissions.</span></span> <span data-ttu-id="1e267-498">例如，你不能从在 Internet 区域部分信任安全沙箱中运行的 XBAP 导航。</span><span class="sxs-lookup"><span data-stu-id="1e267-498">For example, you can't navigate from an XBAP that is running in the Internet zone partial trust security sandbox.</span></span> <span data-ttu-id="1e267-499">有关详细信息，请参阅 [WPF 部分信任安全性](../wpf-partial-trust-security.md)。</span><span class="sxs-lookup"><span data-stu-id="1e267-499">For more information, see [WPF Partial Trust Security](../wpf-partial-trust-security.md).</span></span>

<a name="Navigating_to_HTML_Files_Using_WebBrowser"></a>

### <a name="navigating-to-html-files-by-using-the-webbrowser-control"></a><span data-ttu-id="1e267-500">通过使用 WebBrowser 控件导航到 HTML 文件</span><span class="sxs-lookup"><span data-stu-id="1e267-500">Navigating to HTML Files by Using the WebBrowser Control</span></span>

<span data-ttu-id="1e267-501"><xref:System.Windows.Controls.WebBrowser>控件支持 HTML 文档托管、导航和脚本/托管代码互操作性。</span><span class="sxs-lookup"><span data-stu-id="1e267-501">The <xref:System.Windows.Controls.WebBrowser> control supports HTML document hosting, navigation and script/managed code interoperability.</span></span> <span data-ttu-id="1e267-502">有关控件的详细信息 <xref:System.Windows.Controls.WebBrowser> ，请参阅 <xref:System.Windows.Controls.WebBrowser> 。</span><span class="sxs-lookup"><span data-stu-id="1e267-502">For detailed information regarding the <xref:System.Windows.Controls.WebBrowser> control, see <xref:System.Windows.Controls.WebBrowser>.</span></span>

<span data-ttu-id="1e267-503">类似 <xref:System.Windows.Controls.Frame> 地，使用导航到使用的 HTML <xref:System.Windows.Controls.WebBrowser> 需要特殊的权限。</span><span class="sxs-lookup"><span data-stu-id="1e267-503">Like <xref:System.Windows.Controls.Frame>, navigating to HTML using <xref:System.Windows.Controls.WebBrowser> requires special permissions.</span></span> <span data-ttu-id="1e267-504">例如，在部分信任的应用程序中，你只能导航到位于源站点的 HTML。</span><span class="sxs-lookup"><span data-stu-id="1e267-504">For example, from a partial-trust application, you can navigate only to HTML located at the site of origin.</span></span> <span data-ttu-id="1e267-505">有关详细信息，请参阅 [WPF 部分信任安全性](../wpf-partial-trust-security.md)。</span><span class="sxs-lookup"><span data-stu-id="1e267-505">For more information, see [WPF Partial Trust Security](../wpf-partial-trust-security.md).</span></span>

<a name="Navigating_to_Objects"></a>

### <a name="navigating-to-custom-objects"></a><span data-ttu-id="1e267-506">导航到自定义对象</span><span class="sxs-lookup"><span data-stu-id="1e267-506">Navigating to Custom Objects</span></span>

<span data-ttu-id="1e267-507">如果你有存储为自定义对象的数据，则显示该数据的一种方法是创建一个 <xref:System.Windows.Controls.Page> 具有绑定到这些对象的内容（请参阅[数据绑定概述](../../../desktop-wpf/data/data-binding-overview.md)）。</span><span class="sxs-lookup"><span data-stu-id="1e267-507">If you have data that is stored as custom objects, one way to display that data is to create a <xref:System.Windows.Controls.Page> with content that is bound to those objects (see [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md)).</span></span> <span data-ttu-id="1e267-508">如果无需创建整个页面而只要显示对象，则可以直接导航到它们。</span><span class="sxs-lookup"><span data-stu-id="1e267-508">If you don't need the overhead of creating an entire page just to display the objects, you can navigate directly to them instead.</span></span>

<span data-ttu-id="1e267-509">请考虑 `Person` 在以下代码中实现的类。</span><span class="sxs-lookup"><span data-stu-id="1e267-509">Consider the `Person` class that is implemented in the following code.</span></span>

[!code-csharp[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/Person.cs#personclasscode)]
[!code-vb[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/Person.vb#personclasscode)]

<span data-ttu-id="1e267-510">若要导航到该方法，请调用 <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A?displayProperty=nameWithType> 方法，如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="1e267-510">To navigate to it, you call the <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A?displayProperty=nameWithType> method, as demonstrated by the following code.</span></span>

[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject1)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject2)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject3)]

[!code-csharp[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml.cs#pagethatnavstoobjectcodebehind)]
[!code-vb[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/HomePage.xaml.vb#pagethatnavstoobjectcodebehind)]

<span data-ttu-id="1e267-511">下图显示结果。</span><span class="sxs-lookup"><span data-stu-id="1e267-511">The following figure shows the result.</span></span>

<span data-ttu-id="1e267-512">![导航到某个类的页面](./media/navigation-overview/page-navigates-to-an-object.png "这是一个导航到对象的页面的示例。")</span><span class="sxs-lookup"><span data-stu-id="1e267-512">![A page that navigates to a class](./media/navigation-overview/page-navigates-to-an-object.png "This is an example of a page that navigates to an object.")</span></span>

<span data-ttu-id="1e267-513">从此图可以看出，没有显示任何有用信息。</span><span class="sxs-lookup"><span data-stu-id="1e267-513">From this figure, you can see that nothing useful is displayed.</span></span> <span data-ttu-id="1e267-514">事实上，显示的值是 Person 对象的方法的返回值 `ToString` ; 默认情况下**Person** ，这是 WPF 可用于表示对象的唯一值。</span><span class="sxs-lookup"><span data-stu-id="1e267-514">In fact, the value that is displayed is the return value of the `ToString` method for the **Person** object; by default, this is the only value that WPF can use to represent your object.</span></span> <span data-ttu-id="1e267-515">您可以重写 `ToString` 方法以返回更有意义的信息，尽管它仍只是一个字符串值。</span><span class="sxs-lookup"><span data-stu-id="1e267-515">You could override the `ToString` method to return more meaningful information, although it will still only be a string value.</span></span> <span data-ttu-id="1e267-516">使用 WPF 的演示功能的一种方法是使用数据模板。</span><span class="sxs-lookup"><span data-stu-id="1e267-516">One technique you can use that takes advantage of the presentation capabilities of WPF is to use a data template.</span></span> <span data-ttu-id="1e267-517">可以实现 WPF 可以与特定类型的对象关联的数据模板。</span><span class="sxs-lookup"><span data-stu-id="1e267-517">You can implement a data template that WPF can associate with an object of a particular type.</span></span> <span data-ttu-id="1e267-518">下面的代码演示了对象的数据模板 `Person` 。</span><span class="sxs-lookup"><span data-stu-id="1e267-518">The following code shows a data template for the `Person` object.</span></span>

[!code-xaml[NavigateToObjectSnippets#DataTemplateMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/App.xaml#datatemplatemarkup)]

<span data-ttu-id="1e267-519">此处， `Person` 使用 `x:Type` 特性中的标记扩展将数据模板与类型相关联 `DataType` 。</span><span class="sxs-lookup"><span data-stu-id="1e267-519">Here, the data template is associated with the `Person` type by using the `x:Type` markup extension in the `DataType` attribute.</span></span> <span data-ttu-id="1e267-520">然后，数据模板会将 `TextBlock` 元素（请参见 <xref:System.Windows.Controls.TextBlock> ）绑定到类的属性 `Person` 。</span><span class="sxs-lookup"><span data-stu-id="1e267-520">The data template then binds `TextBlock` elements (see <xref:System.Windows.Controls.TextBlock>) to the properties of the `Person` class.</span></span> <span data-ttu-id="1e267-521">下图显示了对象的更新外观 `Person` 。</span><span class="sxs-lookup"><span data-stu-id="1e267-521">The following figure shows the updated appearance of the `Person` object.</span></span>

<span data-ttu-id="1e267-522">![导航到具有数据模板的类](./media/navigation-overview/navigating-to-a-class.png "导航到具有数据模板的类。")</span><span class="sxs-lookup"><span data-stu-id="1e267-522">![Navigating to a class that has a data template](./media/navigation-overview/navigating-to-a-class.png "Navigating to a class that has a data template.")</span></span>

<span data-ttu-id="1e267-523">此技术的优势之一在于能够通过重复使用数据模板以在应用程序任意位置一致地显示对象而获得一致性。</span><span class="sxs-lookup"><span data-stu-id="1e267-523">An advantage of this technique is the consistency you gain by being able to reuse the data template to display your objects consistently anywhere in your application.</span></span>

<span data-ttu-id="1e267-524">有关数据模板的详细信息，请参阅[数据模板化概述](../data/data-templating-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="1e267-524">For more information on data templates, see [Data Templating Overview](../data/data-templating-overview.md).</span></span>

<a name="Security"></a>

## <a name="security"></a><span data-ttu-id="1e267-525">安全性</span><span class="sxs-lookup"><span data-stu-id="1e267-525">Security</span></span>

<span data-ttu-id="1e267-526">WPF 导航支持允许跨 Internet 导航到 Xbap，并允许应用程序托管第三方内容。</span><span class="sxs-lookup"><span data-stu-id="1e267-526">WPF navigation support allows XBAPs to be navigated to across the Internet, and it allows applications to host third-party content.</span></span> <span data-ttu-id="1e267-527">为了保护应用程序和用户免受有害行为的影响，WPF 提供了在[安全](../security-wpf.md)和[WPF 部分信任安全性](../wpf-partial-trust-security.md)中讨论的各种安全功能。</span><span class="sxs-lookup"><span data-stu-id="1e267-527">To protect both applications and users from harmful behavior, WPF provides a variety of security features that are discussed in [Security](../security-wpf.md) and [WPF Partial Trust Security](../wpf-partial-trust-security.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1e267-528">请参阅</span><span class="sxs-lookup"><span data-stu-id="1e267-528">See also</span></span>

- <xref:System.Windows.Application.SetCookie%2A>
- <xref:System.Windows.Application.GetCookie%2A>
- [<span data-ttu-id="1e267-529">应用程序管理概述</span><span class="sxs-lookup"><span data-stu-id="1e267-529">Application Management Overview</span></span>](application-management-overview.md)
- [<span data-ttu-id="1e267-530">WPF 中的 Pack URI</span><span class="sxs-lookup"><span data-stu-id="1e267-530">Pack URIs in WPF</span></span>](pack-uris-in-wpf.md)
- [<span data-ttu-id="1e267-531">结构化导航概述</span><span class="sxs-lookup"><span data-stu-id="1e267-531">Structured Navigation Overview</span></span>](structured-navigation-overview.md)
- [<span data-ttu-id="1e267-532">导航拓扑概述</span><span class="sxs-lookup"><span data-stu-id="1e267-532">Navigation Topologies Overview</span></span>](navigation-topologies-overview.md)
- [<span data-ttu-id="1e267-533">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="1e267-533">How-to Topics</span></span>](navigation-how-to-topics.md)
- [<span data-ttu-id="1e267-534">部署 WPF 应用程序</span><span class="sxs-lookup"><span data-stu-id="1e267-534">Deploying a WPF Application</span></span>](deploying-a-wpf-application-wpf.md)

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
# <a name="navigation-overview"></a>导航概述

Windows Presentation Foundation （WPF）支持可在两种类型的应用程序中使用的浏览器样式的导航：独立应用程序和 XAML 浏览器应用程序（Xbap）。 为了打包导航内容，WPF 提供了 <xref:System.Windows.Controls.Page> 类。 您可以通过 <xref:System.Windows.Controls.Page> 使用或以编程方式使用从一个导航到另一个 <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Navigation.NavigationService> 。 WPF 使用日记来记住已从导航的页面，并向后导航到它们。

<xref:System.Windows.Controls.Page>、 <xref:System.Windows.Documents.Hyperlink> 、 <xref:System.Windows.Navigation.NavigationService> 和日志构成了由 WPF 提供的导航支持的核心。 本概述首先详细探讨这些功能，然后介绍高级导航支持，其中包括导航到松散 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 文件、HTML 文件和对象。

> [!NOTE]
> 在本主题中，术语 "浏览器" 只引用可以承载 WPF 应用程序的浏览器，当前包括 Microsoft Internet Explorer 和 Firefox。 只有特定的浏览器支持特定 WPF 功能的情况下，浏览器版本被引用。

## <a name="navigation-in-wpf-applications"></a>WPF 应用程序中的导航

本主题提供有关 WPF 中的主要导航功能的概述。 这些功能适用于独立应用程序和 Xbap，不过，本主题在 XBAP 的上下文中提供了这些功能。

> [!NOTE]
> 本主题不讨论如何生成和部署 Xbap。 有关 Xbap 的详细信息，请参阅[WPF XAML 浏览器应用程序概述](wpf-xaml-browser-applications-overview.md)。

本节解释并演示导航的以下方面：

- [实现页](#CreatingAXAMLPage)

- [配置起始页](#Configuring_a_Start_Page)

- [配置主机窗口的标题、宽度和高度](#ConfiguringAXAMLPage)

- [超链接导航](#NavigatingBetweenXAMLPages)

- [片段导航](#FragmentNavigation)

- [导航服务](#NavigationService)

- [使用导航服务以编程方式导航](#Programmatic_Navigation_with_the_Navigation_Service)

- [导航生存期](#Navigation_Lifetime)

- [使用日志记住导航](#NavigationHistory)

- [页生存期和日志](#PageLifetime)

- [保留导航历史记录的内容状态](#RetainingContentStateWithNavigationHistory)

- [Cookie](#Cookies)

- [结构化导航](#Structured_Navigation)

<a name="CreatingAXAMLPage"></a>

### <a name="implementing-a-page"></a>实现页

在 WPF 中，可以导航到多个内容类型，其中包括 .NET Framework 对象、自定义对象、枚举值、用户控件、 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 文件和 HTML 文件。 不过，你会发现打包内容最常见和最方便的方法是使用 <xref:System.Windows.Controls.Page> 。 此外，还 <xref:System.Windows.Controls.Page> 实现了特定于导航的功能，以增强其外观并简化开发。

使用 <xref:System.Windows.Controls.Page> ，可以通过使用如下所示的标记以声明方式实现可导航的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 内容页。

[!code-xaml[NavigationOverviewSnippets#Page1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page1.xaml#page1xaml)]

<xref:System.Windows.Controls.Page>在标记中实现的将 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] `Page` 作为其根元素，并且需要 WPF XML 命名空间声明。 `Page`元素包含要导航并显示的内容。 可以通过设置属性元素来添加内容 `Page.Content` ，如以下标记所示。

[!code-xaml[NavigationOverviewSnippets#Page2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page2.xaml#page2xaml)]

`Page.Content` 只能包含一个子元素，在前面的实例中，内容是一个单独的字符串“Hello, Page!”。 在实践中，通常会使用布局控件作为子元素（请参阅[布局](../advanced/layout.md)）来包含内容并撰写内容。

元素的子元素被 `Page` 视为和的内容 <xref:System.Windows.Controls.Page> ，因此，不需要使用显式 `Page.Content` 声明。 以下标记和前面的示例在声明上是等效的。

[!code-xaml[NavigationOverviewSnippets#Page3XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page3.xaml#page3xaml)]

在这种情况下， `Page.Content` 将自动设置为元素的子元素 `Page` 。 有关详细信息，请参阅 [WPF 内容模型](../controls/wpf-content-model.md)。

仅标记 <xref:System.Windows.Controls.Page> 可用于显示内容。 但是， <xref:System.Windows.Controls.Page> 还可以显示允许用户与页面交互的控件，并且它可以通过处理事件和调用应用程序逻辑来响应用户交互。 交互式 <xref:System.Windows.Controls.Page> 是通过结合使用标记和代码隐藏来实现的，如下面的示例中所示。

[!code-xaml[XBAPAppDefSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml#homepagemarkup)]

[!code-csharp[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml.cs#homepagecodebehind)]
[!code-vb[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/HomePage.xaml.vb#homepagecodebehind)]

要允许标记文件和代码隐藏文件协同工作，需要进行以下配置：

- 在标记中， `Page` 元素必须包含 `x:Class` 属性。 生成应用程序后， `x:Class` 标记文件中存在会导致 Microsoft 生成引擎（MSBuild）创建一个 `partial` 派生自的类， <xref:System.Windows.Controls.Page> 并具有由特性指定的名称 `x:Class` 。 这要求为架构（）添加 XML 命名空间声明 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` 。 生成的 `partial` 类实现 `InitializeComponent` ，调用它来注册事件并设置标记中实现的属性。

- 在代码隐藏中，类必须是 `partial` 由标记中的特性指定的同名类 `x:Class` ，并且必须派生自 <xref:System.Windows.Controls.Page> 。 这允许在生成应用程序时将代码隐藏文件与为 `partial` 标记文件生成的类相关联（请参阅[生成 WPF 应用程序](building-a-wpf-application-wpf.md)）。

- 在代码隐藏中， <xref:System.Windows.Controls.Page> 该类必须实现调用方法的构造函数 `InitializeComponent` 。 `InitializeComponent`由标记文件的生成类实现， `partial` 用于注册事件和设置在标记中定义的属性。

> [!NOTE]
> <xref:System.Windows.Controls.Page>使用 Visual Studio 将新添加到项目时，将 <xref:System.Windows.Controls.Page> 使用标记和代码隐藏来实现，并且它包括必要的配置以创建标记和代码隐藏文件之间的关联，如此处所述。

获得之后 <xref:System.Windows.Controls.Page> ，可以导航到它。 若要指定 <xref:System.Windows.Controls.Page> 应用程序导航到的第一个，需要配置启动 <xref:System.Windows.Controls.Page> 。

<a name="Configuring_a_Start_Page"></a>

### <a name="configuring-a-start-page"></a>配置起始页

Xbap 需要在浏览器中托管一定数量的应用程序基础结构。 在 WPF 中， <xref:System.Windows.Application> 类是建立所需的应用程序基础结构的应用程序定义的一部分（请参阅[应用程序管理概述](application-management-overview.md)）。

通常使用标记和代码隐藏来实现应用程序定义，并将标记文件配置为 MSBuild `ApplicationDefinition` 项。 下面是 XBAP 的应用程序定义。

[!code-xaml[XBAPAppDefSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

[!code-csharp[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml.cs#xbapapplicationdefinitioncodebehind)]
[!code-vb[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/Application.xaml.vb#xbapapplicationdefinitioncodebehind)]

XBAP 可以使用其应用程序定义来指定 start <xref:System.Windows.Controls.Page> ，这是在 <xref:System.Windows.Controls.Page> 启动 XBAP 时自动加载的。 为此，可将 <xref:System.Windows.Application.StartupUri%2A> 属性设置为所需的统一资源标识符（URI） <xref:System.Windows.Controls.Page> 。

> [!NOTE]
> 在大多数情况下，将 <xref:System.Windows.Controls.Page> 编译到应用程序中或与应用程序一起部署。 在这些情况下，标识的 URI <xref:System.Windows.Controls.Page> 是一个包 uri，它是符合*pack*方案的 uri。 WPF 中的[Pack uri](pack-uris-in-wpf.md)进一步讨论了包 uri。 也可使用 http 方案导航到内容，这将在以下内容中讨论。

您可以 <xref:System.Windows.Application.StartupUri%2A> 在标记中以声明方式进行设置，如下面的示例所示。

[!code-xaml[NavigationOverviewSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

在此示例中， `StartupUri` 使用标识主页的相对 PACK URI 设置特性。 启动 XBAP 后，会自动导航到并显示 "主页"。 下图对此进行了演示，其中显示了从 Web 服务器启动的 XBAP。

![XBAP 页](./media/navigation-overview/xbap-launched-from-a-web-server.png "这会显示从 Web 服务器启动的 XBAP。")

> [!NOTE]
> 有关开发和部署 Xbap 的详细信息，请参阅[WPF XAML 浏览器应用程序概述](wpf-xaml-browser-applications-overview.md)和[部署 WPF 应用程序](deploying-a-wpf-application-wpf.md)。

<a name="ConfiguringAXAMLPage"></a>

### <a name="configuring-the-host-windows-title-width-and-height"></a>配置主机窗口的标题、宽度和高度

您从上图中可以看到的一件事情是，浏览器和选项卡面板的标题都是 XBAP 的 URI。 除了长，标题既没什么吸引力也没什么帮助。 出于此原因，我们 <xref:System.Windows.Controls.Page> 提供了一种方法，用于通过设置属性来更改标题 <xref:System.Windows.Controls.Page.WindowTitle%2A> 。 此外，您还可以通过分别设置和来配置浏览器窗口的宽度和高度 <xref:System.Windows.Controls.Page.WindowWidth%2A> <xref:System.Windows.Controls.Page.WindowHeight%2A> 。

<xref:System.Windows.Controls.Page.WindowTitle%2A>、 <xref:System.Windows.Controls.Page.WindowWidth%2A> 和 <xref:System.Windows.Controls.Page.WindowHeight%2A> 可以在标记中以声明方式设置，如下面的示例中所示。

[!code-xaml[NavigationOverviewSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/HomePage.xaml#homepagemarkup)]

结果如下图所示。

![Window 标题、高度、宽度](./media/navigation-overview/window-title-width-height.png "这会显示可以配置的窗口标题、高度和宽度。")

<a name="NavigatingBetweenXAMLPages"></a>

### <a name="hyperlink-navigation"></a>超链接导航

典型的 XBAP 包含多个页面。 若要从一页导航到另一页，最简单的方法是使用 <xref:System.Windows.Documents.Hyperlink> 。 您可以使用元素以声明方式向添加 <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Controls.Page> ，该 `Hyperlink` 元素显示在下面的标记中。

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

`Hyperlink`元素需要以下各项：

- 要导航到的的包 URI <xref:System.Windows.Controls.Page> ，如特性所指定 `NavigateUri` 。

- 用户可以单击以启动导航的内容，如文本和图像（对于 `Hyperlink` 元素可包含的内容，请参阅 <xref:System.Windows.Documents.Hyperlink> ）。

下图显示了一个具有的的 XBAP <xref:System.Windows.Controls.Page> <xref:System.Windows.Documents.Hyperlink> 。

![具有超链接的页面](./media/navigation-overview/xbap-with-a-page-with-a-hyperlink.png "这会显示一个包含超链接的页的 XBAP。")

正如您所期望的那样，单击将 <xref:System.Windows.Documents.Hyperlink> 导致 XBAP 导航到 <xref:System.Windows.Controls.Page> 由属性标识的 `NavigateUri` 。 此外，XBAP 向 <xref:System.Windows.Controls.Page> Internet Explorer 中的 "最近使用的页" 列表添加了一个条目。 如下图所示。

![后退和前进按钮](./media/navigation-overview/back-and-forward-navigation.png "用 "后退" 和 "前进" 按钮导航。")

并且支持从一个导航 <xref:System.Windows.Controls.Page> 到另一个导航， <xref:System.Windows.Documents.Hyperlink> 还支持片段导航。

<a name="FragmentNavigation"></a>

### <a name="fragment-navigation"></a>片段导航

*片段导航*是在当前或另一个中导航到内容片段的内容 <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page> 。 在 WPF 中，内容片段是已命名元素包含的内容。 命名元素是设置了其属性的元素 `Name` 。 下面的标记显示了 `TextBlock` 包含内容片段的命名元素。

[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup2)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup3)]

<xref:System.Windows.Documents.Hyperlink>若要导航到内容片段，该 `NavigateUri` 属性必须包括以下内容：

- <xref:System.Windows.Controls.Page>具有要导航到的内容片段的的 URI。

- “#”字符。

- 中包含内容片段的元素的名称 <xref:System.Windows.Controls.Page> 。

片段 URI 的格式如下。

*PageURI* `#` *ElementName*

下面显示了一个 `Hyperlink` 配置为导航到内容片段的的示例。

[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml1)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml2)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml3)]

> [!NOTE]
> 本部分介绍 WPF 中的默认片段导航实现。 WPF 还允许实现自己的片段导航方案，该方案在某种程度上需要处理 <xref:System.Windows.Navigation.NavigationService.FragmentNavigation?displayProperty=nameWithType> 事件。

> [!IMPORTANT]
> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] `Page` 仅当可以通过 HTTP 浏览这些页面时，才能导航到松散页面（仅限标记的文件，并将其作为根元素）。
>
> 但松散 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 页可以导航到其自己的片段。

<a name="NavigationService"></a>

### <a name="navigation-service"></a>导航服务

虽然 <xref:System.Windows.Documents.Hyperlink> 允许用户启动对特定的导航，但 <xref:System.Windows.Controls.Page> 查找和下载页面的工作由 <xref:System.Windows.Navigation.NavigationService> 类执行。 实质 <xref:System.Windows.Navigation.NavigationService> 上，提供代表客户端代码处理导航请求的能力，例如 <xref:System.Windows.Documents.Hyperlink> 。 此外，还 <xref:System.Windows.Navigation.NavigationService> 实现了对跟踪和影响导航请求的更高级别的支持。

单击时 <xref:System.Windows.Documents.Hyperlink> ，WPF 将调用 <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> 以在指定的 <xref:System.Windows.Controls.Page> 包 URI 上查找并下载。 下载的 <xref:System.Windows.Controls.Page> 会转换为对象树，这些对象的根对象是已下载的实例 <xref:System.Windows.Controls.Page> 。 对根对象的引用 <xref:System.Windows.Controls.Page> 存储在 <xref:System.Windows.Navigation.NavigationService.Content%2A?displayProperty=nameWithType> 属性中。 所导航到的内容的 pack URI 存储在 <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> 属性中，而 <xref:System.Windows.Navigation.NavigationService.CurrentSource%2A?displayProperty=nameWithType> 存储所导航到的最后一页的包 uri。

> [!NOTE]
> WPF 应用程序可以有多个当前处于活动状态 <xref:System.Windows.Navigation.NavigationService> 。 有关详细信息，请参阅本主题后面的[导航宿主](#Navigation_Hosts)。

<a name="Programmatic_Navigation_with_the_Navigation_Service"></a>

### <a name="programmatic-navigation-with-the-navigation-service"></a>使用导航服务以编程方式导航

您无需知道 <xref:System.Windows.Navigation.NavigationService> 是否使用在标记中以声明方式实现导航 <xref:System.Windows.Documents.Hyperlink> ，因为 <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Navigation.NavigationService> 代表您使用。 这意味着，只要的直接或间接父级 <xref:System.Windows.Documents.Hyperlink> 是导航宿主（请参阅[导航](#Navigation_Hosts)宿主）， <xref:System.Windows.Documents.Hyperlink> 就能找到并使用导航宿主的导航服务来处理导航请求。

但是，在某些情况下，你需要 <xref:System.Windows.Navigation.NavigationService> 直接使用，其中包括：

- 需要 <xref:System.Windows.Controls.Page> 使用非参数构造函数实例化时。

- 当你需要在上设置属性， <xref:System.Windows.Controls.Page> 然后再导航到它。

- <xref:System.Windows.Controls.Page>需要导航到的时，只能在运行时确定。

在这些情况下，需要编写代码，以便通过调用对象的方法以编程方式启动导航 <xref:System.Windows.Navigation.NavigationService.Navigate%2A> <xref:System.Windows.Navigation.NavigationService> 。 这需要获取对的引用 <xref:System.Windows.Navigation.NavigationService> 。

#### <a name="getting-a-reference-to-the-navigationservice"></a>获取对 NavigationService 的引用

出于[导航宿主](#Navigation_Hosts)部分所述的原因，WPF 应用程序可以有多个 <xref:System.Windows.Navigation.NavigationService> 。 这意味着，你的代码需要一种方法来查找 <xref:System.Windows.Navigation.NavigationService> ，这通常是 <xref:System.Windows.Navigation.NavigationService> 导航到当前的 <xref:System.Windows.Controls.Page> 。 可以通过调用方法获取对的引用 <xref:System.Windows.Navigation.NavigationService> `static` <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A?displayProperty=nameWithType> 。 若要获取 <xref:System.Windows.Navigation.NavigationService> 导航到特定的 <xref:System.Windows.Controls.Page> ，请将对的引用 <xref:System.Windows.Controls.Page> 作为方法的参数传递 <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A> 。 下面的代码演示如何获取当前的 <xref:System.Windows.Navigation.NavigationService> <xref:System.Windows.Controls.Page> 。

[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPage.xaml.vb#getnscodebehind2)]

作为的查找的快捷方式 <xref:System.Windows.Navigation.NavigationService> <xref:System.Windows.Controls.Page> ，实现了 <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page.NavigationService%2A> 属性。 这在下面的示例中显示。

[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPageShortCut.xaml.vb#getnsshortcutcodebehind2)]

> [!NOTE]
> <xref:System.Windows.Controls.Page> <xref:System.Windows.Navigation.NavigationService> 引发事件时，只能获取对其的引用 <xref:System.Windows.Controls.Page> <xref:System.Windows.FrameworkElement.Loaded> 。

#### <a name="programmatic-navigation-to-a-page-object"></a>以编程方式导航到页对象

下面的示例演示如何使用 <xref:System.Windows.Navigation.NavigationService> 以编程方式导航到 <xref:System.Windows.Controls.Page> 。 需要编程式导航，因为 <xref:System.Windows.Controls.Page> 要导航到的只能使用单个无参数的构造函数实例化。 <xref:System.Windows.Controls.Page>以下标记和代码中显示了具有非参数构造函数的。

[!code-xaml[NavigationOverviewSnippets#PageWithNonDefaultConstructorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml#pagewithnondefaultconstructorxaml)]

[!code-csharp[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml.cs#pagewithnondefaultconstructorcodebehind)]
[!code-vb[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithNonDefaultConstructor.xaml.vb#pagewithnondefaultconstructorcodebehind)]

<xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page> 以下标记和代码中显示了导航到具有非参数构造函数的。

[!code-xaml[NavigationOverviewSnippets#NSNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml#nsnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml.cs#nsnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSNavigationPage.xaml.vb#nsnavigationpagecodebehind)]

当 <xref:System.Windows.Documents.Hyperlink> 单击上的时 <xref:System.Windows.Controls.Page> ，将通过实例化导航到 <xref:System.Windows.Controls.Page> 使用非参数构造函数并调用方法来启动导航 <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> 。 <xref:System.Windows.Navigation.NavigationService.Navigate%2A>接受对将导航到的对象的引用 <xref:System.Windows.Navigation.NavigationService> ，而不是包 URI。

#### <a name="programmatic-navigation-with-a-pack-uri"></a>使用 Pack URI 以编程方式导航

如果需要以编程方式构造包 URI （例如，只能在运行时确定 pack URI，则可以使用 <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> 方法）。 这在下面的示例中显示。

[!code-xaml[NavigationOverviewSnippets#NSUriNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml#nsurinavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml.cs#nsurinavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSUriNavigationPage.xaml.vb#nsurinavigationpagecodebehind)]

#### <a name="refreshing-the-current-page"></a>刷新当前页

<xref:System.Windows.Controls.Page>如果与存储在属性中的 PACK uri 的包 uri 相同，则不会下载。 <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> 若要强制 WPF 再次下载当前页，可以调用 <xref:System.Windows.Navigation.NavigationService.Refresh%2A?displayProperty=nameWithType> 方法，如以下示例中所示。

[!code-xaml[NavigationOverviewSnippets#NSRefreshNavigationPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml#nsrefreshnavigationpagexaml1)]

[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind1)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind2)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind2)]

<a name="Navigation_Lifetime"></a>

### <a name="navigation-lifetime"></a>导航生存期

如你所见，有很多方法初始化导航。 当启动导航时，导航正在进行时，可以使用以下实现的事件来跟踪和影响导航 <xref:System.Windows.Navigation.NavigationService> ：

- <xref:System.Windows.Navigation.NavigationService.Navigating>. 请求新导航时发生。 可用于取消导航。

- <xref:System.Windows.Navigation.NavigationService.NavigationProgress>. 在下载过程中定期发生，用于提供定位进度信息。

- <xref:System.Windows.Navigation.NavigationService.Navigated>. 已定位并下载页时发生。

- <xref:System.Windows.Navigation.NavigationService.NavigationStopped>. 在导航停止（通过调用 <xref:System.Windows.Navigation.NavigationService.StopLoading%2A> ）时发生，或在当前导航正在进行时请求新导航时发生。

- <xref:System.Windows.Navigation.NavigationService.NavigationFailed>. 在导航到所需内容的同时遇到错误时发生。

- <xref:System.Windows.Navigation.NavigationService.LoadCompleted>. 导航到的内容已加载和分析，并开始呈现时发生。

- <xref:System.Windows.Navigation.NavigationService.FragmentNavigation>. 导航到内容片段开始时发生，具体如何发生如下所述：

  - 立即，如果所需片段位于当前内容中。

  - 源内容加载之后，如果所需片段在不同内容中。

引发导航事件的顺序如下图所示。

![页面导航流程图](./media/navigation-overview/order-of-navigation-events.png "页面导航事件流程图")

一般情况下， <xref:System.Windows.Controls.Page> 并不关心这些事件。 更有可能应用程序与应用程序相关，因此，这些事件也由 <xref:System.Windows.Application> 类引发：

- <xref:System.Windows.Application.Navigating?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationProgress?displayProperty=nameWithType>

- <xref:System.Windows.Application.Navigated?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationFailed?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationStopped?displayProperty=nameWithType>

- <xref:System.Windows.Application.LoadCompleted?displayProperty=nameWithType>

- <xref:System.Windows.Application.FragmentNavigation?displayProperty=nameWithType>

每次 <xref:System.Windows.Navigation.NavigationService> 引发事件时， <xref:System.Windows.Application> 类将引发相应的事件。 <xref:System.Windows.Controls.Frame>和 <xref:System.Windows.Navigation.NavigationWindow> 提供相同的事件来检测其各自范围内的导航。

在某些情况下， <xref:System.Windows.Controls.Page> 可能会对这些事件感兴趣。 例如， <xref:System.Windows.Controls.Page> 可以处理 <xref:System.Windows.Navigation.NavigationService.Navigating?displayProperty=nameWithType> 事件，以确定是否取消导航。 这在下面的示例中显示。

[!code-xaml[NavigationOverviewSnippets#CancelNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml#cancelnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml.cs#cancelnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/CancelNavigationPage.xaml.vb#cancelnavigationpagecodebehind)]

如果你使用中的导航事件注册处理程序 <xref:System.Windows.Controls.Page> ，如前面的示例所示，你还必须取消注册事件处理程序。 否则，对于 WPF 导航如何记住 <xref:System.Windows.Controls.Page> 使用日记的导航，可能会产生负面影响。

<a name="NavigationHistory"></a>

### <a name="remembering-navigation-with-the-journal"></a>使用日志记住导航

WPF 使用两个堆栈来记住您从其导航的页面：后退堆栈和前进堆栈。 当你从当前导航 <xref:System.Windows.Controls.Page> 到新的 <xref:System.Windows.Controls.Page> 或转发到现有的时 <xref:System.Windows.Controls.Page> ，当前 <xref:System.Windows.Controls.Page> 将添加到*back 堆栈*中。 当您从当前导航 <xref:System.Windows.Controls.Page> 回之前 <xref:System.Windows.Controls.Page> ，当前 <xref:System.Windows.Controls.Page> 将添加到*前进堆栈*中。 后退堆栈、前进堆栈和管理它们的功能统称为日志。 后退堆栈中的每一项和正向堆栈是类的实例 <xref:System.Windows.Navigation.JournalEntry> ，并且称为*日记条目*。

#### <a name="navigating-the-journal-from-internet-explorer"></a>从 Internet Explorer 导航日志

从概念上讲，日记的工作方式与 Internet Explorer 中的 "**后退**" 和 "**前进**" 按钮的操作方式相同。 这些在下图中显示。

![后退和前进按钮](./media/navigation-overview/back-and-forward-navigation.png "用 "后退" 和 "前进" 按钮导航。")

对于由 Internet Explorer 承载的 Xbap，WPF 将日记本集成到 Internet Explorer 的导航中 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 。 这允许用户使用 Internet Explorer 中的 "**后退**"、"**前进**" 和 "**最新页**" 按钮在 XBAP 中导航页面。

> [!IMPORTANT]
> 在 Internet Explorer 中，当用户离开并返回到 XBAP 时，仅将未保持活动状态的页的日记条目保留在日志中。 有关保持页处于活动状态的讨论，请参阅本主题后面的[页生存期和日志](#PageLifetime)。

默认情况下， <xref:System.Windows.Controls.Page> Internet Explorer 的 "**最新页**" 列表中显示的每个文本都是的 URI <xref:System.Windows.Controls.Page> 。 很多情况下这对用户并没有什么特殊的意义。 幸运的是，可以使用以下选项更改文本：

1. 附加的 `JournalEntry.Name` 属性值。

2. `Page.Title`特性值。

3. `Page.WindowTitle`当前的特性值和 URI <xref:System.Windows.Controls.Page> 。

4. 当前的 URI <xref:System.Windows.Controls.Page> 。 （默认值）

选项列出的顺序和查找文本的优先级顺序一致。 例如，如果 `JournalEntry.Name` 设置了，则忽略其他值。

下面的示例使用 `Page.Title` 特性更改为日记条目显示的文本。

[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup2)]

[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind1)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind2)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind2)]

#### <a name="navigating-the-journal-using-wpf"></a>使用 WPF 导航日志

尽管用户可以使用 Internet Explorer 中的 "**后退**"、"**前进**" 和 "**最新" 页**导航日记，但也可以使用 WPF 提供的声明性和编程机制导航日志。 这样做的一个原因是在页面中提供自定义导航 Ui。

您可以使用公开的导航命令以声明方式添加日记本导航支持 <xref:System.Windows.Input.NavigationCommands> 。 下面的示例演示如何使用 `BrowseBack` 导航命令。

[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml1)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml2)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml3)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML4](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml4)]

可以使用类的以下成员之一以编程方式导航日记 <xref:System.Windows.Navigation.NavigationService> ：

- <xref:System.Windows.Navigation.NavigationService.GoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.GoForward%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoForward%2A>

此日志还可以通过编程方式进行操作，如本主题后面的将[内容状态保留为导航历史记录](#RetainingContentStateWithNavigationHistory)中所述。

<a name="PageLifetime"></a>

### <a name="page-lifetime-and-the-journal"></a>页生存期和日志

请考虑 XBAP，其中包含多个包含丰富内容的页，包括图形、动画和媒体。 这类页的内存占用量可能相当大，尤其是使用视频和音频媒体的时候。 假设该日记 "记住" 已导航到的页面，则此类 XBAP 会迅速消耗大量内存。

出于此原因，日记的默认行为是 <xref:System.Windows.Controls.Page> 在每个日记条目中存储元数据，而不是对对象的引用 <xref:System.Windows.Controls.Page> 。 导航到日记条目时，其 <xref:System.Windows.Controls.Page> 元数据用于创建指定的的新实例 <xref:System.Windows.Controls.Page> 。 因此，所导航的每个都 <xref:System.Windows.Controls.Page> 具有如下图所示的生存期。

![页面生存期](./media/navigation-overview/navigated-page-lifetime.png "这会显示导航页面时的生存期。")

尽管使用默认日记行为可以节省内存消耗，但每页呈现性能可能会降低;呈现 <xref:System.Windows.Controls.Page> 可能会很耗时，尤其是在有大量内容时。 如果需要将 <xref:System.Windows.Controls.Page> 实例保留在日记中，可以通过两种方法进行绘制。 首先，可以通过调用方法以编程方式导航到 <xref:System.Windows.Controls.Page> 对象 <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> 。

其次，可以 <xref:System.Windows.Controls.Page> 通过将 <xref:System.Windows.Controls.Page.KeepAlive%2A> 属性设置为 `true` （默认值为）来指定 WPF 在日志中保留的实例 `false` 。 如以下示例中所示，可以 <xref:System.Windows.Controls.Page.KeepAlive%2A> 在标记中以声明方式设置。

[!code-xaml[NavigationOverviewSnippets#KeepAlivePageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/KeepAlivePage.xaml#keepalivepagexaml)]

<xref:System.Windows.Controls.Page>保持活动状态的生存期与不是相同。 第一次将处于 <xref:System.Windows.Controls.Page> 活动状态的状态导航到时，它的实例化就像 <xref:System.Windows.Controls.Page> 是未保持活动状态的。 但是，由于的实例 <xref:System.Windows.Controls.Page> 保留在日志中，因此只要它保留在日志中，就永远不会再对其进行实例化。 因此，如果 <xref:System.Windows.Controls.Page> 有在每次导航到时需要调用的初始化逻辑 <xref:System.Windows.Controls.Page> ，则应将其从构造函数移到事件的处理程序中 <xref:System.Windows.FrameworkElement.Loaded> 。 如下图所示， <xref:System.Windows.FrameworkElement.Loaded> <xref:System.Windows.FrameworkElement.Unloaded> 每次导航到和时，都仍将引发和事件 <xref:System.Windows.Controls.Page> 。

![当引发 Loaded 和 Unloaded 事件时](./media/navigation-overview/loaded-and-unloaded-events.png "当导航到和中的某个页面时，将引发已加载和已卸载的事件。")

如果 <xref:System.Windows.Controls.Page> 未保持活动状态，则不应执行以下任一操作：

- 存储对它或它的任何部分的引用。

- 将事件处理程序注册到并非由其实现的事件。

执行上述任一操作都将创建强制 <xref:System.Windows.Controls.Page> 保留在内存中的引用，即使已从日志中删除该引用。

通常，您应该首选 <xref:System.Windows.Controls.Page> 不保持活动状态的默认行为 <xref:System.Windows.Controls.Page> 。 但是，这会存在将在下一节中讨论的状态影响。

<a name="RetainingContentStateWithNavigationHistory"></a>

### <a name="retaining-content-state-with-navigation-history"></a>保留导航历史记录的内容状态

如果 <xref:System.Windows.Controls.Page> 未保持活动状态，并且具有收集用户数据的控件，则当用户离开并返回到时，数据会发生什么情况 <xref:System.Windows.Controls.Page> ？ 从用户体验角度，用户应该会希望看到他们以前输入的数据。 遗憾的是，由于每个导航都创建了一个新实例 <xref:System.Windows.Controls.Page> ，因此收集数据的控件将重新实例化，数据会丢失。

幸运的是，日记本提供对跨导航的数据 <xref:System.Windows.Controls.Page> （包括控制数据）的支持。 具体而言，每个的日记条目都 <xref:System.Windows.Controls.Page> 充当关联状态的临时容器 <xref:System.Windows.Controls.Page> 。 以下步骤概述了从导航时使用此支持的方式 <xref:System.Windows.Controls.Page> ：

1. 当前的条目 <xref:System.Windows.Controls.Page> 将添加到日志中。

2. 的状态 <xref:System.Windows.Controls.Page> 与该页的日记条目一起存储，后者将添加到后面的堆栈中。

3. <xref:System.Windows.Controls.Page>导航到新的。

当 <xref:System.Windows.Controls.Page> 使用日记向后导航到页面时，将执行以下步骤：

1. <xref:System.Windows.Controls.Page>实例化（back 堆栈顶部的日记条目）。

2. 将 <xref:System.Windows.Controls.Page> 用与的日记条目一起存储的状态进行刷新 <xref:System.Windows.Controls.Page> 。

3. 向 <xref:System.Windows.Controls.Page> 后导航到。

当在上使用以下控件时，WPF 将自动使用此支持 <xref:System.Windows.Controls.Page> ：

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

如果 <xref:System.Windows.Controls.Page> 使用这些控件，则会在导航中记住输入的数据， <xref:System.Windows.Controls.Page> 如下图所示**Favorite Color** <xref:System.Windows.Controls.ListBox> 。

![具有记忆状态的控件的页面](./media/navigation-overview/data-remembered-across-page-navigations.png "跨页面导航记住输入的数据。")

当除 <xref:System.Windows.Controls.Page> 前面的列表中的控件以外的其他控件时，或者当状态存储在自定义对象中时，需要编写代码以使日志记住跨导航状态的状态 <xref:System.Windows.Controls.Page> 。

如果需要记住跨导航的小块状态 <xref:System.Windows.Controls.Page> ，可以使用 <xref:System.Windows.DependencyProperty> 配置了元数据标志的依赖属性（请参见） <xref:System.Windows.FrameworkPropertyMetadata.Journal%2A?displayProperty=nameWithType> 。

如果 <xref:System.Windows.Controls.Page> 需要记住的跨导航的状态包含多个数据段，则可能会发现，将状态封装到单个类并实现接口所需的代码要少得多 <xref:System.Windows.Navigation.IProvideCustomContentState> 。

如果需要在单个的各个状态之间导航 <xref:System.Windows.Controls.Page> ，而不是从自身导航 <xref:System.Windows.Controls.Page> ，则可以使用 <xref:System.Windows.Navigation.IProvideCustomContentState> 和 <xref:System.Windows.Navigation.NavigationService.AddBackEntry%2A?displayProperty=nameWithType> 。

<a name="Cookies"></a>

### <a name="cookies"></a>Cookie

WPF 应用程序可以存储数据的另一种方法是使用和方法来创建、更新和删除 cookie <xref:System.Windows.Application.SetCookie%2A> <xref:System.Windows.Application.GetCookie%2A> 。 可以在 WPF 中创建的 cookie 与其他类型的 Web 应用程序使用的 cookie 相同;cookie 是由应用程序在客户端计算机上或跨应用程序会话存储的任意数据块。 Cookie 数据通常采用以下格式的名称/值对的形式。

*名称* `=`*值*

在将数据传递到时，如果将数据传递到 <xref:System.Windows.Application.SetCookie%2A> <xref:System.Uri> 应设置 cookie 的位置，则会在内存中创建一个 cookie，并且该 cookie 仅在当前应用程序会话的持续时间内可用。 这种类型的 cookie 称为*会话 cookie*。

要跨应用程序会话存储 cookie，必须使用以下格式将到期日期添加到 cookie。

*NAME* `=` *VALUE* `; expires=DAY, DD-MMM-YYYY HH:MM:SS GMT`

在 cookie 过期之前，具有到期日期的 cookie 存储在当前的 Windows 安装程序的临时 Internet Files 文件夹中。 此类 cookie 称为*永久性 cookie* ，因为它在应用程序会话之间保持不变。

可以通过调用方法来检索会话和持久 cookie <xref:System.Windows.Application.GetCookie%2A> ，同时传递 <xref:System.Uri> 使用方法设置 cookie 的位置的 <xref:System.Windows.Application.SetCookie%2A> 。

下面是在 WPF 中支持 cookie 的一些方法：

- WPF 独立应用程序和 Xbap 可以创建和管理 cookie。

- 可以从浏览器访问 XBAP 创建的 cookie。

- 同一个域中的 Xbap 可以创建和共享 cookie。

- 同一域中的 Xbap 和 HTML 页可以创建和共享 cookie。

- 当 Xbap 和松散 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 页发出 Web 请求时，会调度 cookie。

- 在 IFRAME 中承载的顶级 Xbap 和 Xbap 都可以访问 cookie。

- WPF 中的 Cookie 支持对于所有受支持的浏览器都是相同的。

- 在 Internet Explorer 中，与 cookie 相关的 P3P 策略由 WPF 提供，特别是对于第一方和第三方 Xbap。

<a name="Structured_Navigation"></a>

### <a name="structured-navigation"></a>结构化导航

如果需要将数据从一个传递 <xref:System.Windows.Controls.Page> 到另一个，则可以将数据作为参数传递给的非参数构造函数 <xref:System.Windows.Controls.Page> 。 请注意，如果使用此方法，则必须保持 <xref:System.Windows.Controls.Page> 活动状态; 否则，下一次导航到时 <xref:System.Windows.Controls.Page> ，WPF 将 <xref:System.Windows.Controls.Page> 使用无参数构造函数重新实例化。

或者，你 <xref:System.Windows.Controls.Page> 可以实现用需要传递的数据设置的属性。 不过，当 <xref:System.Windows.Controls.Page> 需要将数据传递回导航到该数据的时，这会变得困难 <xref:System.Windows.Controls.Page> 。 问题在于，导航不会以本机方式支持用于确保在 <xref:System.Windows.Controls.Page> 从其导航后将返回到的机制。 实质上，导航不支持调用/返回语义。 为了解决此问题，WPF 提供了 <xref:System.Windows.Navigation.PageFunction%601> 类，可用于确保以 <xref:System.Windows.Controls.Page> 可预测的结构化方式返回到。 有关详细信息，请参阅[结构化导航概述](structured-navigation-overview.md)。

<a name="The_NavigationWindow_Class"></a>

## <a name="the-navigationwindow-class"></a>NavigationWindow 类

到目前为止，你已全面了解最有可能用可导航内容生成应用程序的导航服务。 这些服务在 Xbap 的上下文中进行了讨论，不过它们并不局限于 Xbap。 现代操作系统和 Windows 应用程序利用了新式用户的浏览器体验，将浏览器样式的导航并入独立的应用程序。 常见示例包括：

- **Word 同义词库**：导航字选择。

- **文件资源管理器**：导航文件和文件夹。

- **向导**：将复杂任务分为多页，可以在它们之间导航。 例如，处理添加和删除 Windows 功能的 Windows 组件向导。

若要将浏览器样式的导航并入独立应用程序，可以使用 <xref:System.Windows.Navigation.NavigationWindow> 类。 <xref:System.Windows.Navigation.NavigationWindow>派生自 <xref:System.Windows.Window> ，并对 xbap 提供的导航支持相同的扩展。 你可以将 <xref:System.Windows.Navigation.NavigationWindow> 作为独立应用程序的主窗口，也可以用作辅助窗口（如对话框）。

若要实现 <xref:System.Windows.Navigation.NavigationWindow> ，与 WPF 中的大多数顶级类（ <xref:System.Windows.Window> 、 <xref:System.Windows.Controls.Page> 等）结合使用，可以使用标记和代码隐藏。 这在下面的示例中显示。

[!code-xaml[IntroToNavNavigationWindowSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml#navigationwindowmarkup)]

[!code-csharp[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml.cs#navigationwindowcodebehind)]
[!code-vb[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/MainWindow.xaml.vb#navigationwindowcodebehind)]

此代码将创建一个 <xref:System.Windows.Navigation.NavigationWindow> ，它在打开时会自动导航到 <xref:System.Windows.Controls.Page> （主页 .xaml） <xref:System.Windows.Navigation.NavigationWindow> 。 如果 <xref:System.Windows.Navigation.NavigationWindow> 是主应用程序窗口，则可以使用 `StartupUri` 属性来启动它。 这在以下标记中显示。

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchNavWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/App.xaml#applaunchnavwindow)]

下图显示的是 <xref:System.Windows.Navigation.NavigationWindow> 独立应用程序的主窗口。

![主窗口](./media/navigation-overview/navigation-window-as-main-window.png "作为主窗口的导航窗口")

从图中可以看到， <xref:System.Windows.Navigation.NavigationWindow> 具有标题，即使未在 <xref:System.Windows.Navigation.NavigationWindow> 前面示例的实现代码中进行设置也是如此。 而是使用属性设置标题 <xref:System.Windows.Controls.Page.WindowTitle%2A> ，如以下代码所示。

[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup1)]
[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup2)]

设置 <xref:System.Windows.Controls.Page.WindowWidth%2A> 和 <xref:System.Windows.Controls.Page.WindowHeight%2A> 属性还会影响 <xref:System.Windows.Navigation.NavigationWindow> 。

通常， <xref:System.Windows.Navigation.NavigationWindow> 当你需要自定义其行为或外观时，可以自行实现。 如果没有执行上述操作，则可以使用快捷方式。 如果在独立的应用程序中将的 pack URI 指定 <xref:System.Windows.Controls.Page> 为 <xref:System.Windows.Application.StartupUri%2A> ，则 <xref:System.Windows.Application> 会自动创建 <xref:System.Windows.Navigation.NavigationWindow> 来承载的 <xref:System.Windows.Controls.Page> 。 以下标记显示如何实现此功能。

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchPage](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/AnotherApp.xaml#applaunchpage)]

如果希望将辅助应用程序窗口（如对话框 <xref:System.Windows.Navigation.NavigationWindow> ）作为，可以使用以下示例中的代码将其打开。

[!code-csharp[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/DialogOwnerWindow.xaml.cs#createnwdialogbox)]
[!code-vb[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/DialogOwnerWindow.xaml.vb#createnwdialogbox)]

下图显示结果。

![对话框](./media/navigation-overview/navigation-window-as-dialog-box.png "作为对话框的导航窗口")

如您所见，会 <xref:System.Windows.Navigation.NavigationWindow> 显示允许用户导航日记的 Internet Explorer 样式的 "**后退**" 和 "**前进**" 按钮。 这些按钮提供相同的用户体验，如下图所示。

![NavigationWindow 中的“后退”和“前进”按钮](./media/navigation-overview/back-and-forward-buttons-in-navigation-window.png "导航窗口中的 "后退" 和 "前进" 按钮")

如果页面提供其自己的日记导航支持和 UI，则可以**Forward**通过将**Back** <xref:System.Windows.Navigation.NavigationWindow> 属性的值设置为来隐藏显示的 "后退" 和 "前进" 按钮 <xref:System.Windows.Navigation.NavigationWindow.ShowsNavigationUI%2A> `false` 。

此外，还可以使用 WPF 中的自定义支持来替换 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Navigation.NavigationWindow> 自身的。

<a name="Frame_in_Standalone_Applications"></a>

## <a name="the-frame-class"></a>框架类

浏览器和 <xref:System.Windows.Navigation.NavigationWindow> 都是托管可导航内容的窗口。 在某些情况下，应用程序具有无需整个窗口托管的内容。 相反，此类内容在其他内容中托管。 可以使用类将导向性内容插入到其他内容中 <xref:System.Windows.Controls.Frame> 。 <xref:System.Windows.Controls.Frame>提供与和 Xbap 相同的支持 <xref:System.Windows.Navigation.NavigationWindow> 。

下面的示例演示如何使用元素以声明方式将添加 <xref:System.Windows.Controls.Frame> 到 <xref:System.Windows.Controls.Page> `Frame` 。

[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml3)]

此标记设置 `Source` 元素的属性， `Frame` 其中包含 <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Frame> 最初应导航到的的包 URI。 下图显示了一个具有已在 <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Frame> 多个页面之间导航的的 XBAP。

![已在多页之间导航的框架](./media/navigation-overview/frame-navigation-between-multiple-pages.png "这会显示多个页面之间的帧导航。")

你不必在的 <xref:System.Windows.Controls.Frame> 内容内使用 <xref:System.Windows.Controls.Page> 。 在的 <xref:System.Windows.Controls.Frame> 内容中托管 <xref:System.Windows.Window> 。

默认情况下， <xref:System.Windows.Controls.Frame> 只有在没有其他日志时才使用自己的日记。 如果 <xref:System.Windows.Controls.Frame> 是在或 xbap 内承载的内容的一部分 <xref:System.Windows.Navigation.NavigationWindow> ，则 <xref:System.Windows.Controls.Frame> 使用属于 <xref:System.Windows.Navigation.NavigationWindow> 或 xbap 的日记。 但是，有时 <xref:System.Windows.Controls.Frame> 可能需要负责自己的日记。 这样做的一个原因是允许在承载的页面内进行日志导航 <xref:System.Windows.Controls.Frame> 。 这由下图说明。

![框架和页面示意图](./media/navigation-overview/journal-navigation-within-pages-hosted-by-a-frame.png "这会在框架托管的页中显示日志导航。")

在这种情况下，你可以 <xref:System.Windows.Controls.Frame> 通过将的属性设置为来将配置为使用自己的日记 <xref:System.Windows.Controls.Frame.JournalOwnership%2A> <xref:System.Windows.Controls.Frame> <xref:System.Windows.Navigation.JournalOwnership.OwnsJournal> 。 这在以下标记中显示。

[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml3)]

下图说明了在使用自己的日记的中导航的效果 <xref:System.Windows.Controls.Frame> 。

![使用自己的日记的框架](./media/navigation-overview/frame-uses-its-own-journal.png "这显示了在使用其自己的日记的帧中导航的效果。")

请注意 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ，在中的导航 <xref:System.Windows.Controls.Frame> （而不是 Internet Explorer）中显示日记条目。

> [!NOTE]
> 如果 <xref:System.Windows.Controls.Frame> 是在中承载的内容的一部分，则 <xref:System.Windows.Window> <xref:System.Windows.Controls.Frame> 使用其自己的日记，因此会显示自己的导航 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 。

如果你的用户体验需要 <xref:System.Windows.Controls.Frame> 提供自己的日记而不显示导航 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ，则可以 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 通过将设置为来隐藏导航 <xref:System.Windows.Controls.Frame.NavigationUIVisibility%2A> <xref:System.Windows.Visibility.Hidden> 。 这在以下标记中显示。

[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml3)]

<a name="Navigation_Hosts"></a>

## <a name="navigation-hosts"></a>导航主机

<xref:System.Windows.Controls.Frame>和 <xref:System.Windows.Navigation.NavigationWindow> 是称为导航宿主的类。 *导航宿主*是可导航到并显示内容的类。 为实现此目的，每个导航宿主都使用其自己的 <xref:System.Windows.Navigation.NavigationService> 和日志。 导航主机的基本构造在下图中显示。

![导航器示意图](./media/navigation-overview/navigation-host-construction.png "导航宿主的基本构造")

实质上，这允许 <xref:System.Windows.Navigation.NavigationWindow> 和 <xref:System.Windows.Controls.Frame> 提供 XBAP 在浏览器中承载时提供的相同导航支持。

除了使用 <xref:System.Windows.Navigation.NavigationService> 和日记，导航宿主还实现实现相同的成员 <xref:System.Windows.Navigation.NavigationService> 。 这由下图说明。

![Frame 和 NavigationWindow 中的日记](./media/navigation-overview/navigation-window-and-frame.png "导航窗口和框架")

这就允许直接对它们进行导航支持编程。 如果需要为中托管的提供自定义导航，则可以考虑此情况 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Controls.Frame> <xref:System.Windows.Window> 。 此外，这两种类型都实现了与导航相关的附加成员，其中包括 `BackStack` （ <xref:System.Windows.Navigation.NavigationWindow.BackStack%2A?displayProperty=nameWithType> 、 <xref:System.Windows.Controls.Frame.BackStack%2A?displayProperty=nameWithType> ）和 `ForwardStack` （ <xref:System.Windows.Navigation.NavigationWindow.ForwardStack%2A?displayProperty=nameWithType> ， <xref:System.Windows.Controls.Frame.ForwardStack%2A?displayProperty=nameWithType> ），这使您可以分别枚举后退堆栈和前进堆栈中的日记条目。

如之前提及，应用程序中可以存在不止一个日志。 下图提供何时可能发生这种情况的示例。

![一个应用程序内的多个日记](./media/navigation-overview/multiple-journals-in-one-application.png "这是一个应用程序中多个日记的示例。")

<a name="Navigating_to_Content_Other_than_Pages"></a>

## <a name="navigating-to-content-other-than-xaml-pages"></a>导航到非 XAML 页内容

本主题中的 <xref:System.Windows.Controls.Page> 和 Pack xbap 已用于演示 WPF 的各种导航功能。 但是， <xref:System.Windows.Controls.Page> 编译到应用程序中的内容并不是可以导航到的唯一内容类型，Pack xbap 不是标识内容的唯一方法。

如本部分所示，你还可以导航到松散 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 文件、HTML 文件和对象。

<a name="Navigating_to_Loose_XAML_Files"></a>

### <a name="navigating-to-loose-xaml-files"></a>导航到松散 XAML 文件

松散 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 文件是具有以下特征的文件：

- 仅包含 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] （即，不包含任何代码）。

- 具有适当的命名空间声明。

- 具有 .xaml 文件扩展名。

例如，请考虑以下存储为松散 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 文件 "Person" 的内容。

[!code-xaml[NavigationOverviewSnippets#LooseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Person.xaml#loosexaml)]

双击该文件时，浏览器打开、导航到并显示内容。 如下图所示。

![Person.XAML 文件中的内容的显示](./media/navigation-overview/contents-of-person-xaml-file.png "显示 Person 文件的内容。")

可显示 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 以下内容的松散文件：

- 本地计算机上的网站、Intranet 或 Internet。

- 通用命名约定（UNC）文件共享。

- 本地磁盘。

可以将松散 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 文件添加到浏览器的收藏夹，或浏览器的主页。

> [!NOTE]
> 有关发布和启动松散页面的详细信息 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，请参阅[部署 WPF 应用程序](deploying-a-wpf-application-wpf.md)。

松散的一项限制 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 是您只能承载安全地在部分信任环境中运行的内容。 例如， `Window` 不能是松散文件的根元素 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 。 有关详细信息，请参阅 [WPF 部分信任安全性](../wpf-partial-trust-security.md)。

<a name="Navigating_to_HTML_Files_Using_Frame"></a>

### <a name="navigating-to-html-files-by-using-frame"></a>通过使用框架导航到 HTML 文件

正如您所料，还可以导航到 HTML。 只需提供使用 http 方案的 URI 即可。 例如，下面的示例 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 演示一个 <xref:System.Windows.Controls.Frame> 导航到 HTML 页的。

[!code-xaml[NavigationOverviewSnippets#FrameHtmlNavMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHTMLNavPage.xaml#framehtmlnavmarkup)]

导航到 HTML 需要特殊权限。 例如，你不能从在 Internet 区域部分信任安全沙箱中运行的 XBAP 导航。 有关详细信息，请参阅 [WPF 部分信任安全性](../wpf-partial-trust-security.md)。

<a name="Navigating_to_HTML_Files_Using_WebBrowser"></a>

### <a name="navigating-to-html-files-by-using-the-webbrowser-control"></a>通过使用 WebBrowser 控件导航到 HTML 文件

<xref:System.Windows.Controls.WebBrowser>控件支持 HTML 文档托管、导航和脚本/托管代码互操作性。 有关控件的详细信息 <xref:System.Windows.Controls.WebBrowser> ，请参阅 <xref:System.Windows.Controls.WebBrowser> 。

类似 <xref:System.Windows.Controls.Frame> 地，使用导航到使用的 HTML <xref:System.Windows.Controls.WebBrowser> 需要特殊的权限。 例如，在部分信任的应用程序中，你只能导航到位于源站点的 HTML。 有关详细信息，请参阅 [WPF 部分信任安全性](../wpf-partial-trust-security.md)。

<a name="Navigating_to_Objects"></a>

### <a name="navigating-to-custom-objects"></a>导航到自定义对象

如果你有存储为自定义对象的数据，则显示该数据的一种方法是创建一个 <xref:System.Windows.Controls.Page> 具有绑定到这些对象的内容（请参阅[数据绑定概述](../../../desktop-wpf/data/data-binding-overview.md)）。 如果无需创建整个页面而只要显示对象，则可以直接导航到它们。

请考虑 `Person` 在以下代码中实现的类。

[!code-csharp[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/Person.cs#personclasscode)]
[!code-vb[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/Person.vb#personclasscode)]

若要导航到该方法，请调用 <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A?displayProperty=nameWithType> 方法，如以下代码所示。

[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject1)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject2)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject3)]

[!code-csharp[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml.cs#pagethatnavstoobjectcodebehind)]
[!code-vb[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/HomePage.xaml.vb#pagethatnavstoobjectcodebehind)]

下图显示结果。

![导航到某个类的页面](./media/navigation-overview/page-navigates-to-an-object.png "这是一个导航到对象的页面的示例。")

从此图可以看出，没有显示任何有用信息。 事实上，显示的值是 Person 对象的方法的返回值 `ToString` ; 默认情况下**Person** ，这是 WPF 可用于表示对象的唯一值。 您可以重写 `ToString` 方法以返回更有意义的信息，尽管它仍只是一个字符串值。 使用 WPF 的演示功能的一种方法是使用数据模板。 可以实现 WPF 可以与特定类型的对象关联的数据模板。 下面的代码演示了对象的数据模板 `Person` 。

[!code-xaml[NavigateToObjectSnippets#DataTemplateMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/App.xaml#datatemplatemarkup)]

此处， `Person` 使用 `x:Type` 特性中的标记扩展将数据模板与类型相关联 `DataType` 。 然后，数据模板会将 `TextBlock` 元素（请参见 <xref:System.Windows.Controls.TextBlock> ）绑定到类的属性 `Person` 。 下图显示了对象的更新外观 `Person` 。

![导航到具有数据模板的类](./media/navigation-overview/navigating-to-a-class.png "导航到具有数据模板的类。")

此技术的优势之一在于能够通过重复使用数据模板以在应用程序任意位置一致地显示对象而获得一致性。

有关数据模板的详细信息，请参阅[数据模板化概述](../data/data-templating-overview.md)。

<a name="Security"></a>

## <a name="security"></a>安全性

WPF 导航支持允许跨 Internet 导航到 Xbap，并允许应用程序托管第三方内容。 为了保护应用程序和用户免受有害行为的影响，WPF 提供了在[安全](../security-wpf.md)和[WPF 部分信任安全性](../wpf-partial-trust-security.md)中讨论的各种安全功能。

## <a name="see-also"></a>请参阅

- <xref:System.Windows.Application.SetCookie%2A>
- <xref:System.Windows.Application.GetCookie%2A>
- [应用程序管理概述](application-management-overview.md)
- [WPF 中的 Pack URI](pack-uris-in-wpf.md)
- [结构化导航概述](structured-navigation-overview.md)
- [导航拓扑概述](navigation-topologies-overview.md)
- [操作指南主题](navigation-how-to-topics.md)
- [部署 WPF 应用程序](deploying-a-wpf-application-wpf.md)

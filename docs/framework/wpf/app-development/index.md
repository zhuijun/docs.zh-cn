---
title: 应用程序开发
description: 了解如何使用 Windows Presentation Foundation （WPF）框架构建各种应用程序。
ms.date: 01/26/2018
helpviewer_keywords:
- WPF [WPF], about application development
- application development [WPF], about
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
ms.openlocfilehash: ac4227785f2fc398217b3aa8984176844264bbaa
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85613730"
---
# <a name="application-development"></a>应用程序开发
<a name="introduction"></a>Windows Presentation Foundation （WPF）是一个演示框架，可用于开发以下类型的应用程序：  
  
- 独立应用程序（传统样式 Windows 应用程序，内置于安装到客户端计算机并从客户端计算机运行的可执行程序集。  
  
- XAML 浏览器应用程序（Xbap）（由导航页面构成的应用程序，这些应用程序被构建为可执行程序集并由 Web 浏览器（如 Microsoft Internet Explorer 或 Mozilla Firefox）承载。  
  
- 自定义控件库（包含可重用控件的非可执行程序集）。  
  
- 类库（包含可重用类的非可执行程序集）。  
  
> [!NOTE]
> 强烈建议不要在 Windows 服务中使用 WPF 类型。 如果尝试在 Windows 服务中使用这些功能，这些功能可能无法按预期工作。  
  
 为了构建这组应用程序，WPF 实现了服务主机。 本主题对这些服务以及在何处可以找到更多相关信息进行了概述。  

<a name="Application_Management"></a>
## <a name="application-management"></a>应用程序管理  
 可执行的 WPF 应用程序通常需要一组包括以下内容的核心功能：  
  
- 创建和管理常见的应用程序基础结构（包括创建入口点方法和 Windows 消息循环，以接收系统和输入消息）。  
  
- 对应用程序的生存期进行跟踪并与之进行交互。  
  
- 检索和处理命令行参数。  
  
- 共享应用程序范围的属性和 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 资源。  
  
- 检测和处理未经处理的异常。  
  
- 返回退出代码。  
  
- 管理独立应用程序中的窗口。  
  
- 在 XAML 浏览器应用程序（Xbap）中跟踪导航，并在导航窗口和框架中跟踪独立应用程序。  
  
 以上功能由通过*应用程序定义*添加到应用程序的 <xref:System.Windows.Application> 类来实现。  
  
 有关详细信息，请参阅[应用程序管理概述](application-management-overview.md)。  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>
## <a name="wpf-application-resource-content-and-data-files"></a>WPF 应用程序资源、内容和数据文件  
 WPF 为嵌入资源扩展了 Microsoft .NET 框架中的核心支持，并支持三种不可执行的数据文件：资源、内容和数据。 有关详细信息，请参阅 [WPF 应用程序资源、内容和数据文件](wpf-application-resource-content-and-data-files.md)。  
  
 WPF 不可执行数据文件支持的关键组件是能够使用唯一 URI 来识别和加载它们。 有关详细信息，请参阅[WPF 中的 Pack uri](pack-uris-in-wpf.md)。  
  
<a name="Windows_and_Dialog_Boxes"></a>
## <a name="windows-and-dialog-boxes"></a>窗口和对话框  
 用户通过 windows 与 WPF 独立应用程序交互。 窗口旨在托管应用程序内容并提供通常允许用户与内容交互的应用程序功能。 在 WPF 中，windows 由类封装 <xref:System.Windows.Window> ，该类支持：  
  
- 创建和显示窗口。  
  
- 建立所有者/所拥有窗口关系。  
  
- 配置窗口外观（例如，大小、位置、图标、标题栏文本、边框）。  
  
- 对窗口的生存期进行跟踪并与之进行交互。  
  
 有关详细信息，请参阅 [WPF 窗口概述](wpf-windows-overview.md)。  
  
 <xref:System.Windows.Window> 支持用于创建被称为对话框的特殊窗口类型的功能。 可以创建两种类型的对话框，即模式和无模式对话框。  
  
 为方便起见，并提供可重用性和跨应用程序的一致用户体验的优点，WPF 公开了三个常见的 Windows 对话框： <xref:Microsoft.Win32.OpenFileDialog> 、 <xref:Microsoft.Win32.SaveFileDialog> 和 <xref:System.Windows.Controls.PrintDialog> 。  
  
 消息框是一种特殊类型的对话框，用于向用户显示重要的文本信息并询问简单的“是/否/确定/取消”问题。 使用 <xref:System.Windows.MessageBox> 类创建并显示消息框。  
  
 有关详细信息，请参阅[对话框概述](dialog-boxes-overview.md)。  
  
<a name="Navigation"></a>
## <a name="navigation"></a>导航  
 WPF 使用页面（ <xref:System.Windows.Controls.Page> ）和超链接（）支持 Web 样式 <xref:System.Windows.Documents.Hyperlink> 的导航。 导航可以通过多种方式来实现，其中包括：  
  
- 在 Web 浏览器中承载的独立页面。  
  
- 编译到在 Web 浏览器中承载的 XBAP 的页面。  
  
- 被编译到独立应用程序中并由导航窗口 (<xref:System.Windows.Navigation.NavigationWindow>) 承载的页面。  
  
- 由框架（）承载的页面（ <xref:System.Windows.Controls.Frame> 可在独立页面上承载）或编译到 XBAP 或独立应用程序中的页面。  
  
 为了便于导航，WPF 实现了以下各项：  
  
- <xref:System.Windows.Navigation.NavigationService>用于处理导航请求的共享导航引擎 <xref:System.Windows.Controls.Frame> ，由、 <xref:System.Windows.Navigation.NavigationWindow> 和 xbap 用来支持应用程序内导航。  
  
- 用于启动导航的导航方法。  
  
- 各种导航事件，用于对导航的生存期进行跟踪并与之进行交互。  
  
- 记住通过日志实现的后向和前向导航，还可以检查和操控这些导航。  
  
 有关信息，请参阅[导航概述](navigation-overview.md)。  
  
 WPF 还支持一种特殊类型的导航，称为结构化导航。 结构化导航可用于调用一个或多个页面，这些页面能以结构化的可预测方式返回与调用函数一致的数据。 此功能将取决于 <xref:System.Windows.Navigation.PageFunction%601> 类；有关该类的进一步描述，请参阅[结构化导航概述](structured-navigation-overview.md)。 <xref:System.Windows.Navigation.PageFunction%601> 还可用于简化[导航拓扑概述](navigation-topologies-overview.md)中所述的复杂导航拓扑的创建。  
  
<a name="Hosting"></a>
## <a name="hosting"></a>Hosting  
 Xbap 可在 Microsoft Internet Explorer 或 Firefox 中承载。 每个承载模型都有各自的一些注意事项和约束，这些内容在[承载](hosting-wpf-applications.md)中均有涵盖。  
  
<a name="Build_and_Deploy"></a>
## <a name="build-and-deploy"></a>生成和部署  
 尽管可以使用命令行编译器从命令提示符生成简单的 WPF 应用程序，但 WPF 与 Visual Studio 集成，以提供简化开发和生成过程的附加支持。 有关详细信息，请参阅[生成 WPF 应用程序](building-a-wpf-application-wpf.md)。  
  
 根据所生成的应用程序类型，会有一个或多个部署选项可供选择。 有关详细信息，请参阅[部署 WPF 应用程序](deploying-a-wpf-application-wpf.md)。  
  
<a name="related_topics"></a>
## <a name="related-topics"></a>相关主题  
  
|Title|描述|  
|-----------|-----------------|  
|[应用程序管理概述](application-management-overview.md)|简要介绍 <xref:System.Windows.Application> 类，包括管理应用程序生存期、窗口、应用程序资源和导航。|  
|[WPF 中的窗口](windows-in-wpf-applications.md)|详细介绍如何在应用程序中管理窗口，包括如何使用 <xref:System.Windows.Window> 类和对话框。|  
|[导航概述](navigation-overview.md)|概述如何管理应用程序的各个页面间的导航。|  
|[承载](hosting-wpf-applications.md)|提供 XAML 浏览器应用程序（Xbap）的概述。|  
|[生成和部署](building-and-deploying-wpf-applications.md)|描述如何生成和部署 WPF 应用程序。|  
|[Visual Studio 中的 WPF 简介](../getting-started/introduction-to-wpf-in-vs.md)|介绍 WPF 的主要功能。|  
|[演练：我的第一个 WPF 桌面应用程序](../getting-started/walkthrough-my-first-wpf-desktop-application.md)|一项演练，用于演示如何使用页面导航、布局、控件、图像、样式和绑定来创建 WPF 应用程序。|

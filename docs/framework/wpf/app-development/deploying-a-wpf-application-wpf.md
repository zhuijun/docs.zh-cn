---
title: 部署应用
description: 探索 Windows 和 .NET Framework 用于 Windows Presentation Foundation （WPF）应用程序的部署技术。
ms.date: 03/30/2017
helpviewer_keywords:
- WPF applications [WPF], deployment
- deployment [WPF], applications
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
ms.openlocfilehash: 62904ccd47800c8340d68c223e50688902170063
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619294"
---
# <a name="deploy-a-wpf-application"></a>部署 WPF 应用程序

生成 Windows Presentation Foundation （WPF）应用程序后，需要部署这些应用程序。 Windows 和 .NET Framework 包括几种部署技术。 用于部署 WPF 应用程序的部署技术取决于应用程序类型。 本主题简要概述了每种部署技术，以及如何将它们与每个 WPF 应用程序类型的部署要求结合使用。

<a name="Deployment_Technologies"></a>
## <a name="deployment-technologies"></a>部署技术  
 Windows 和 .NET Framework 包括几种部署技术，其中包括：  
  
- XCopy 部署。  
  
- Windows Installer 部署。  
  
- ClickOnce 部署。  
  
<a name="XCopy_Deployment"></a>
### <a name="xcopy-deployment"></a>XCopy 部署  
 XCopy 部署是指使用 XCopy 命令行程序将文件从一个位置复制到另一个位置。 XCopy 部署适用于下列情况：  
  
- 应用程序是自包含的。 无需更新客户端，即可运行。  
  
- 应用程序文件必须从一个位置移到另一个位置，如从生成位置（本地磁盘、UNC 文件共享等）移动到发布位置（网站、UNC 文件共享等）。  
  
- 应用程序无需进行 Shell 集成（“开始”菜单快捷方式、桌面图标等）。  
  
 XCopy 适用于简单的部署方案；如果需要更为复杂的部署功能，则会限制使用 XCopy。 具体而言就是，使用 XCopy 往往会导致创建、执行并维护能以可靠方式管理部署的脚本，并进而产生相应的开销。 此外，XCopy 不支持版本控制、卸载或回滚。  
  
<a name="Windows_Installer"></a>
### <a name="windows-installer"></a>Windows Installer  
 Windows Installer 允许将应用程序打包为独立的可执行文件，这些可轻松分发到客户端并运行。 此外，Windows Installer 随 Windows 一起安装，可与桌面、"开始" 菜单和 "程序" 控制面板集成。  
  
 Windows Installer 简化了应用程序的安装和卸载，但它并不提供用于确保已安装的应用程序从版本控制的角度保持最新的功能。  
  
 有关 Windows Installer 的详细信息，请参阅[Windows Installer 部署](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop)。
  
<a name="ClickOnce_Deployment"></a>
### <a name="clickonce-deployment"></a>ClickOnce 部署  
 ClickOnce 为非 Web 应用程序启用 Web 样式应用程序部署。 应用程序会发布到 Web 或文件服务器，也会从 Web 或文件服务器进行部署。 尽管 ClickOnce 不支持 Windows Installer 安装应用程序所支持的所有客户端功能，但它确实支持包含以下内容的子集：  
  
- 与“开始”菜单及“程序”控制面板集成。  
  
- 版本控制、回滚和卸载。  
  
- 联机安装模式，该模式始终会从部署位置启动应用程序。  
  
- 当有新版本发布时自动更新。  
  
- 注册文件扩展名。  
  
 有关 ClickOnce 的详细信息，请参阅[Clickonce 安全和部署](/visualstudio/deployment/clickonce-security-and-deployment)。  
  
<a name="Deploying_WPF_Applications"></a>
## <a name="deploying-wpf-applications"></a>部署 WPF 应用程序  
 WPF 应用程序的部署选项取决于应用程序的类型。 从部署的角度来看，WPF 具有三种重要的应用程序类型：  
  
- 独立应用程序。  
  
- 仅标记 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 应用程序。  
  
- XAML 浏览器应用程序（Xbap）。  
  
<a name="Deploying_Standalone_Applications"></a>
### <a name="deploying-standalone-applications"></a>部署独立应用程序  
 使用 ClickOnce 或 Windows Installer 部署独立的应用程序。 无论使用哪一项，独立应用程序都要在完全信任的状态下才能运行。 将自动向使用 Windows Installer 部署的独立应用程序授予完全信任。 使用 ClickOnce 部署的独立应用程序不会自动被授予完全信任。 相反，ClickOnce 会显示一个安全警告对话框，用户必须先接受该对话框，然后才能安装独立的应用程序。 如果接受，独立应用程序就会安装并被授予完全信任状态。 如果不接受，则独立应用程序不会安装。  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>
### <a name="deploying-markup-only-xaml-applications"></a>部署仅标记 XAML 应用程序  
 仅标记 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 页面通常会发布到 Web 服务器（如 HTML 页面），可以使用 Internet Explorer 来查看。 仅标记 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 页面会按照 Internet 区域权限集定义的限制，在部分信任的安全沙箱内运行。 这为基于 HTML 的 Web 应用程序提供了等效的安全沙箱。  
  
 有关 WPF 应用程序安全性的详细信息，请参阅[安全性](../security-wpf.md)。  
  
 仅标记 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 页面可以使用 XCopy 或 Windows Installer 安装到本地文件系统。 可以使用 Internet Explorer 或 Windows 资源管理器查看这些页面。  
  
 有关 XAML 的详细信息，请参阅 [XAML 概述 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)。  
  
<a name="Deploying_XAML_Browser_Applications"></a>
### <a name="deploying-xaml-browser-applications"></a>部署 XAML 浏览器应用程序  
 Xbap 是已编译的应用程序，需要部署以下三个文件：  
  
- *应用程序名称*.exe：可执行的程序集应用程序文件。  
  
- *应用程序名称*.xbap：部署清单。  
  
- *应用程序名称*.exe.manifest：应用程序清单。  
  
> [!NOTE]
> 有关部署和应用程序清单的详细信息，请参阅[生成 WPF 应用程序](building-a-wpf-application-wpf.md)。  
  
 这些文件是在生成 XBAP 时生成的。 有关详细信息，请参阅[如何：创建新的 WPF 浏览器应用程序项目](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100))。 与仅标记 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 页面类似，xbap 通常会发布到 Web 服务器，并使用 Internet Explorer 进行查看。  
  
 可以使用任何一种部署技术将 Xbap 部署到客户端。 但建议使用 ClickOnce，因为它提供以下功能：  
  
1. 当有新版本发布时自动更新。  
  
2. 以完全信任级别运行的 XBAP 的提升权限。  
  
 默认情况下，ClickOnce 会使用.deploy 扩展名来发布应用程序文件。 这可能会引发问题，但可被禁用。 有关详细信息，请参阅 [ClickOnce 部署中的服务器和客户端配置问题](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments)。  
  
 有关部署 XAML 浏览器应用程序（Xbap）的详细信息，请参阅[WPF XAML 浏览器应用程序概述](wpf-xaml-browser-applications-overview.md)。  
  
<a name="Installing__NET_Framework_3_0"></a>
## <a name="installing-the-net-framework"></a>安装 .NET Framework  
 若要运行 WPF 应用程序，Microsoft .NET 框架必须安装在客户端上。 当查看 WPF 浏览器承载的应用程序时，Internet Explorer 会自动检测是否随 .NET Framework 一起安装了客户端。 如果未安装 .NET Framework，Internet Explorer 将提示用户安装。  
  
 为了检测 .NET Framework 是否已安装，Internet Explorer 包括一个引导程序应用程序，该应用程序已注册为具有以下扩展名的内容文件的后备多用途 Internet 邮件扩展（MIME）处理程序： .xaml、.xps、xbap 和应用程序。 如果你导航到这些文件类型，并且客户端上未安装 .NET Framework，则引导程序应用程序会请求安装它的权限。 如果未提供权限，则不会安装 .NET Framework 和应用程序。  
  
 如果授予了权限，Internet Explorer 将使用 Microsoft 后台智能传输服务（BITS）下载并安装 .NET Framework。 成功安装 .NET Framework 后，最初请求的文件将在新的浏览器窗口中打开。  
  
 有关详细信息，请参阅[部署 .NET Framework 和应用程序](../../deployment/index.md)。  
  
## <a name="see-also"></a>请参阅

- [生成 WPF 应用程序](building-a-wpf-application-wpf.md)
- [安全性](../security-wpf.md)

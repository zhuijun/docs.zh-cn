---
title: 配置应用程序
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: 04ddce4755ce30b7d46c3bd54024af08361d96ad
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90536076"
---
# <a name="configuring-your-application"></a><span data-ttu-id="43865-102">配置应用程序</span><span class="sxs-lookup"><span data-stu-id="43865-102">Configuring Your Application</span></span>
<span data-ttu-id="43865-103">Windows Communication Foundation (WCF) 使用 .NET 配置系统，并允许你在计算机和应用程序范围中配置服务。</span><span class="sxs-lookup"><span data-stu-id="43865-103">Windows Communication Foundation (WCF) uses the .NET configuration system and allows you to configure services at both the machine and application scope.</span></span>  
  
 <span data-ttu-id="43865-104">WCF 定义的配置设置位于 `<system.serviceModel>` 节组中。</span><span class="sxs-lookup"><span data-stu-id="43865-104">Configuration settings defined by WCF are located in the `<system.serviceModel>` section group.</span></span> <span data-ttu-id="43865-105">有关如何配置 WCF 服务的详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="43865-105">For more information about how to configure a WCF service, see the following topics:</span></span>  
  
- [<span data-ttu-id="43865-106">正在配置服务</span><span class="sxs-lookup"><span data-stu-id="43865-106">Configuring Services</span></span>](../configuring-services.md)  
  
- [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 <span data-ttu-id="43865-107">应用程序定义的配置设置是在 `<appSettings>` 节组中定义的。</span><span class="sxs-lookup"><span data-stu-id="43865-107">Application-defined configurations settings are defined in the `<appSettings>` section group.</span></span> <span data-ttu-id="43865-108">有关 .NET 配置文件中的应用程序设置的详细信息，请参阅 [\<appSettings>](/previous-versions/dotnet/netframework-4.0/ms228154(v=vs.100)) 。</span><span class="sxs-lookup"><span data-stu-id="43865-108">For more information about application settings in .NET configuration files, see [\<appSettings>](/previous-versions/dotnet/netframework-4.0/ms228154(v=vs.100)).</span></span>  
  
## <a name="using-the-configuration-editor"></a><span data-ttu-id="43865-109">使用配置编辑器</span><span class="sxs-lookup"><span data-stu-id="43865-109">Using the Configuration Editor</span></span>  
 <span data-ttu-id="43865-110">[ ( # A0) 的 Wcf 配置编辑器工具](../configuration-editor-tool-svcconfigeditor-exe.md)允许管理员和开发人员使用图形用户界面来创建和修改 WCF 服务的配置设置。</span><span class="sxs-lookup"><span data-stu-id="43865-110">The WCF [Configuration Editor Tool (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md) allows administrators and developers to create and modify configuration settings for WCF services using a graphical user interface.</span></span> <span data-ttu-id="43865-111">利用此工具，无需直接编辑 XML 配置文件，即可管理 WCF 绑定、行为、服务和诊断的设置。</span><span class="sxs-lookup"><span data-stu-id="43865-111">With this tool, you can manage settings for WCF bindings, behaviors, services, and diagnostics without directly editing XML configuration files.</span></span>  
  
## <a name="editing-configuration-files-in-visual-studio"></a><span data-ttu-id="43865-112">在 Visual Studio 中编辑配置文件</span><span class="sxs-lookup"><span data-stu-id="43865-112">Editing Configuration Files in Visual Studio</span></span>  
 <span data-ttu-id="43865-113">若要在 Visual Studio 中编辑 WCF 服务项目的配置文件，请在 **解决方案资源管理器** 中右键单击该项目，然后选择 " **编辑 WCF 配置** " 上下文菜单项。</span><span class="sxs-lookup"><span data-stu-id="43865-113">To edit the configuration file of a WCF service project in Visual Studio, right click it in **Solution Explorer** and choose the **Edit WCF Config** context menu item.</span></span> <span data-ttu-id="43865-114">这将启动 [ ( # A0) 的配置编辑器工具 ](../configuration-editor-tool-svcconfigeditor-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="43865-114">This launches the [Configuration Editor Tool (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="43865-115">如果你在 Visual Studio 中编辑 WCF Web Services 项目的配置文件，请在 **解决方案资源管理器**中右键单击该项目，请注意，" **编辑 wcf 配置** " 上下文菜单项缺失。</span><span class="sxs-lookup"><span data-stu-id="43865-115">If you edit the configuration file of a WCF Web Service project in Visual Studio by right-clicking it in **Solution Explorer**, notice that the **Edit WCF Config** context menu item is missing.</span></span> <span data-ttu-id="43865-116">若要解决此问题，请单击 " **工具** " 菜单，然后选择 " **WCF 服务配置编辑器**"。</span><span class="sxs-lookup"><span data-stu-id="43865-116">To workaround this issue, click the **Tools** menu, and choose **WCF Service Config Editor**.</span></span> <span data-ttu-id="43865-117">之后，您可以右键单击某个配置文件并使用 " **编辑 WCF 配置** " 上下文菜单项。</span><span class="sxs-lookup"><span data-stu-id="43865-117">After that, you can right-click a configuration file and use the **Edit WCF Config** context menu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43865-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="43865-118">See also</span></span>

- [<span data-ttu-id="43865-119">配置编辑器工具 (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="43865-119">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>](../configuration-editor-tool-svcconfigeditor-exe.md)
- [<span data-ttu-id="43865-120">正在配置服务</span><span class="sxs-lookup"><span data-stu-id="43865-120">Configuring Services</span></span>](../configuring-services.md)
- [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md)

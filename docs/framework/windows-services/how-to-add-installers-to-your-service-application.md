---
title: 如何：将安装程序添加到服务应用程序
description: 了解如何将安装程序添加到服务应用程序。 Visual Studio 提供可安装与服务应用关联资源的安装组件。
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, deploying
- installation components, adding to services
- installers, adding to services
- Windows Service applications, adding installers
- services, adding installers
- ServiceInstaller class, adding installers to services
- ServiceProcessInstaller class, adding installers to services
ms.assetid: 8b698e9a-b88e-4f44-ae45-e0c5ea0ae5a8
author: ghogen
ms.openlocfilehash: f82dd6635555ccb8fcbcdf63cba2495084194731
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925639"
---
# <a name="how-to-add-installers-to-your-service-application"></a><span data-ttu-id="a9f83-104">如何：将安装程序添加到服务应用程序</span><span class="sxs-lookup"><span data-stu-id="a9f83-104">How to: Add Installers to Your Service Application</span></span>
<span data-ttu-id="a9f83-105">Visual Studio 提供可安装与服务应用程序关联资源的安装组件。</span><span class="sxs-lookup"><span data-stu-id="a9f83-105">Visual Studio ships installation components that can install resources associated with your service applications.</span></span> <span data-ttu-id="a9f83-106">安装组件在安装它的系统上注册单个服务，并让服务控制管理器知道存在该服务。</span><span class="sxs-lookup"><span data-stu-id="a9f83-106">Installation components register an individual service on the system to which it is being installed and let the Services Control Manager know that the service exists.</span></span> <span data-ttu-id="a9f83-107">当使用服务应用程序时，你可以在“属性”窗口中选择一个链接，以将相应的安装程序自动添加到项目中。</span><span class="sxs-lookup"><span data-stu-id="a9f83-107">When you work with a service application, you can select a link in the Properties window to automatically add the appropriate installers to your project.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a9f83-108">将服务的属性值从服务类复制到安装程序类。</span><span class="sxs-lookup"><span data-stu-id="a9f83-108">Property values for your service are copied from the service class to the installer class.</span></span> <span data-ttu-id="a9f83-109">如果更新服务类的属性值，这些值不会在安装程序中自动更新。</span><span class="sxs-lookup"><span data-stu-id="a9f83-109">If you update the property values on the service class, they are not automatically updated in the installer.</span></span>  
  
 <span data-ttu-id="a9f83-110">将安装程序添加到项目时，会在项目中创建一个新类（默认情况下名为 `ProjectInstaller`），并在其中创建适当安装组件的实例。</span><span class="sxs-lookup"><span data-stu-id="a9f83-110">When you add an installer to your project, a new class (which, by default, is named `ProjectInstaller`) is created in the project, and instances of the appropriate installation components are created within it.</span></span> <span data-ttu-id="a9f83-111">该类用作项目所需的所有安装组件的中心点。</span><span class="sxs-lookup"><span data-stu-id="a9f83-111">This class acts as a central point for all of the installation components your project needs.</span></span> <span data-ttu-id="a9f83-112">例如，如果向应用程序添加第二项服务并单击“添加安装程序”链接，则不会创建第二个安装程序类；相反，会将第二项服务必需的附加安装组件添加到现有类中。</span><span class="sxs-lookup"><span data-stu-id="a9f83-112">For example, if you add a second service to your application and click the Add Installer link, a second installer class is not created; instead, the necessary additional installation component for the second service is added to the existing class.</span></span>  
  
 <span data-ttu-id="a9f83-113">无需在安装程序中执行任何特殊编码就可以正确安装服务。</span><span class="sxs-lookup"><span data-stu-id="a9f83-113">You do not need to do any special coding within the installers to make your services install correctly.</span></span> <span data-ttu-id="a9f83-114">但是，如果需要为安装进程添加特殊功能，则可能偶尔需要修改安装程序的内容。</span><span class="sxs-lookup"><span data-stu-id="a9f83-114">However, you may occasionally need to modify the contents of the installers if you need to add special functionality to the installation process.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a9f83-115">显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。</span><span class="sxs-lookup"><span data-stu-id="a9f83-115">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="a9f83-116">若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。</span><span class="sxs-lookup"><span data-stu-id="a9f83-116">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="a9f83-117">有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="a9f83-117">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-installers-to-your-service-application"></a><span data-ttu-id="a9f83-118">将安装程序添加到服务应用程序</span><span class="sxs-lookup"><span data-stu-id="a9f83-118">To add installers to your service application</span></span>  
  
1. <span data-ttu-id="a9f83-119">在“解决方案资源管理器”  中，访问要为其添加安装组件的服务的“设计”  视图。</span><span class="sxs-lookup"><span data-stu-id="a9f83-119">In **Solution Explorer**, access **Design** view for the service for which you want to add an installation component.</span></span>  
  
2. <span data-ttu-id="a9f83-120">单击设计器的背景以选择服务本身，而不是它的任何内容。</span><span class="sxs-lookup"><span data-stu-id="a9f83-120">Click the background of the designer to select the service itself, rather than any of its contents.</span></span>  
  
3. <span data-ttu-id="a9f83-121">设计器具有焦点时，右键单击，然后单击“添加安装程序”  。</span><span class="sxs-lookup"><span data-stu-id="a9f83-121">With the designer in focus, right-click, and then click **Add Installer**.</span></span>  
  
     <span data-ttu-id="a9f83-122">将新类 `ProjectInstaller` 和两个安装组件 <xref:System.ServiceProcess.ServiceProcessInstaller> 和 <xref:System.ServiceProcess.ServiceInstaller> 添加到项目中，并将该服务的属性值复制到组件。</span><span class="sxs-lookup"><span data-stu-id="a9f83-122">A new class, `ProjectInstaller`, and two installation components, <xref:System.ServiceProcess.ServiceProcessInstaller> and <xref:System.ServiceProcess.ServiceInstaller>, are added to your project, and property values for the service are copied to the components.</span></span>  
  
4. <span data-ttu-id="a9f83-123">单击 <xref:System.ServiceProcess.ServiceInstaller> 组件并验证 <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> 属性的值是否设置为与服务本身的 <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> 属性相同的值。</span><span class="sxs-lookup"><span data-stu-id="a9f83-123">Click the <xref:System.ServiceProcess.ServiceInstaller> component and verify that the value of the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property is set to the same value as the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property on the service itself.</span></span>  
  
5. <span data-ttu-id="a9f83-124">要确定服务的启动方式，请单击 <xref:System.ServiceProcess.ServiceInstaller> 组件并将 <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> 属性设置为适当的值。</span><span class="sxs-lookup"><span data-stu-id="a9f83-124">To determine how your service will be started, click the <xref:System.ServiceProcess.ServiceInstaller> component and set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to the appropriate value.</span></span>  
  
    |<span data-ttu-id="a9f83-125">“值”</span><span class="sxs-lookup"><span data-stu-id="a9f83-125">Value</span></span>|<span data-ttu-id="a9f83-126">结果</span><span class="sxs-lookup"><span data-stu-id="a9f83-126">Result</span></span>|  
    |-----------|------------|  
    |<xref:System.ServiceProcess.ServiceStartMode.Manual>|<span data-ttu-id="a9f83-127">该服务必须在安装后手动启动。</span><span class="sxs-lookup"><span data-stu-id="a9f83-127">The service must be manually started after installation.</span></span> <span data-ttu-id="a9f83-128">有关详细信息，请参阅[如何：启动服务](how-to-start-services.md)。</span><span class="sxs-lookup"><span data-stu-id="a9f83-128">For more information, see [How to: Start Services](how-to-start-services.md).</span></span>|  
    |<xref:System.ServiceProcess.ServiceStartMode.Automatic>|<span data-ttu-id="a9f83-129">只要重启计算机，服务就将自行启动。</span><span class="sxs-lookup"><span data-stu-id="a9f83-129">The service will start by itself whenever the computer reboots.</span></span>|  
    |<xref:System.ServiceProcess.ServiceStartMode.Disabled>|<span data-ttu-id="a9f83-130">服务无法启动。</span><span class="sxs-lookup"><span data-stu-id="a9f83-130">The service cannot be started.</span></span>|  
  
6. <span data-ttu-id="a9f83-131">要确定服务将在其中运行的安全性上下文，请单击 <xref:System.ServiceProcess.ServiceProcessInstaller> 组件并设置适当的属性值。</span><span class="sxs-lookup"><span data-stu-id="a9f83-131">To determine the security context in which your service will run, click the <xref:System.ServiceProcess.ServiceProcessInstaller> component and set the appropriate property values.</span></span> <span data-ttu-id="a9f83-132">有关详细信息，请参阅[如何：为服务指定安全上下文](how-to-specify-the-security-context-for-services.md)。</span><span class="sxs-lookup"><span data-stu-id="a9f83-132">For more information, see [How to: Specify the Security Context for Services](how-to-specify-the-security-context-for-services.md).</span></span>  
  
7. <span data-ttu-id="a9f83-133">替代需要为其执行自定义处理进程的任何方法。</span><span class="sxs-lookup"><span data-stu-id="a9f83-133">Override any methods for which you need to perform custom processing.</span></span>  
  
8. <span data-ttu-id="a9f83-134">对项目中的每项其他服务执行步骤 1 至 7。</span><span class="sxs-lookup"><span data-stu-id="a9f83-134">Perform steps 1 through 7 for each additional service in your project.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a9f83-135">对于项目中的每项其他服务，必须向项目的 `ProjectInstaller` 类添加一个附加 <xref:System.ServiceProcess.ServiceInstaller> 组件。</span><span class="sxs-lookup"><span data-stu-id="a9f83-135">For each additional service in your project, you must add an additional <xref:System.ServiceProcess.ServiceInstaller> component to the project's `ProjectInstaller` class.</span></span> <span data-ttu-id="a9f83-136">在步骤 3 中添加的 <xref:System.ServiceProcess.ServiceProcessInstaller> 组件可与项目中的所有单个服务安装程序一起使用。</span><span class="sxs-lookup"><span data-stu-id="a9f83-136">The <xref:System.ServiceProcess.ServiceProcessInstaller> component added in step three works with all of the individual service installers in the project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9f83-137">请参阅</span><span class="sxs-lookup"><span data-stu-id="a9f83-137">See also</span></span>

- [<span data-ttu-id="a9f83-138">Windows 服务应用程序介绍</span><span class="sxs-lookup"><span data-stu-id="a9f83-138">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="a9f83-139">如何：安装和卸载服务</span><span class="sxs-lookup"><span data-stu-id="a9f83-139">How to: Install and Uninstall Services</span></span>](how-to-install-and-uninstall-services.md)
- [<span data-ttu-id="a9f83-140">如何：启动服务</span><span class="sxs-lookup"><span data-stu-id="a9f83-140">How to: Start Services</span></span>](how-to-start-services.md)
- [<span data-ttu-id="a9f83-141">如何：为服务指定安全上下文</span><span class="sxs-lookup"><span data-stu-id="a9f83-141">How to: Specify the Security Context for Services</span></span>](how-to-specify-the-security-context-for-services.md)

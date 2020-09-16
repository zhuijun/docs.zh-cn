---
title: 如何：使用 Windows Server App Fabric 承载工作流服务
ms.date: 03/30/2017
ms.assetid: 83b62cce-5fc2-4c6d-b27c-5742ba3bac73
ms.openlocfilehash: 2cf77753a0540e75ae6778065f7fa006729f8d6a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555980"
---
# <a name="how-to-host-a-workflow-service-with-windows-server-app-fabric"></a><span data-ttu-id="e94a0-102">如何：使用 Windows Server App Fabric 承载工作流服务</span><span class="sxs-lookup"><span data-stu-id="e94a0-102">How to: Host a Workflow Service with Windows Server App Fabric</span></span>

<span data-ttu-id="e94a0-103">在 App Fabric 中承载工作流服务类似于在 IIS/WAS 下承载。</span><span class="sxs-lookup"><span data-stu-id="e94a0-103">Hosting workflow services in App Fabric is similar to hosting under IIS/WAS.</span></span> <span data-ttu-id="e94a0-104">唯一的区别在于 App Fabric 提供的用于部署、监控和管理工作流服务的工具。</span><span class="sxs-lookup"><span data-stu-id="e94a0-104">The only difference is the tools App Fabric provides for deploying, monitoring, and managing workflow services.</span></span> <span data-ttu-id="e94a0-105">本主题使用在 [创建长时间运行的工作流服务](creating-a-long-running-workflow-service.md)中创建的工作流服务。</span><span class="sxs-lookup"><span data-stu-id="e94a0-105">This topic uses the workflow service created in the [Creating a Long-running Workflow Service](creating-a-long-running-workflow-service.md).</span></span> <span data-ttu-id="e94a0-106">本主题将指导您创建工作流服务。</span><span class="sxs-lookup"><span data-stu-id="e94a0-106">That topic will walk you through creating a workflow service.</span></span> <span data-ttu-id="e94a0-107">本主题将介绍如何使用 App Fabric 承载工作流服务。</span><span class="sxs-lookup"><span data-stu-id="e94a0-107">This topic will explain how to host the workflow service using App Fabric.</span></span> <span data-ttu-id="e94a0-108">有关 Windows Server App Fabric 的详细信息，请参阅 [Windows Server App Fabric 文档](/previous-versions/appfabric/ff384253(v=azure.10))。</span><span class="sxs-lookup"><span data-stu-id="e94a0-108">For more information about Windows Server App Fabric, see [Windows Server App Fabric Documentation](/previous-versions/appfabric/ff384253(v=azure.10)).</span></span> <span data-ttu-id="e94a0-109">完成以下步骤之前，请确保已安装 Windows Server App Fabric。</span><span class="sxs-lookup"><span data-stu-id="e94a0-109">Before completing the steps below make sure you have Windows Server App Fabric installed.</span></span>  <span data-ttu-id="e94a0-110">为此，请打开 Internet Information Services ( # A0) ，在 " **连接** " 视图中单击您的服务器名称，单击 "站点"，然后单击 " **默认**网站"。</span><span class="sxs-lookup"><span data-stu-id="e94a0-110">To do this open up Internet Information Services (inetmgr.exe), click your server name in the **Connections** view, click Sites, and click **Default Web Site**.</span></span> <span data-ttu-id="e94a0-111">在屏幕右侧，应会看到一个名为 " **App Fabric**" 的部分。</span><span class="sxs-lookup"><span data-stu-id="e94a0-111">In the right-hand side of the screen you should see a section called **App Fabric**.</span></span> <span data-ttu-id="e94a0-112">如果您看不到这一部分（它位于右侧窗格的顶部），则表示您还未安装 App Fabric。</span><span class="sxs-lookup"><span data-stu-id="e94a0-112">If you don’t see this section (it will be on the top of the right-hand pane) you do not have App Fabric installed.</span></span> <span data-ttu-id="e94a0-113">有关安装 Windows Server App Fabric 的详细信息，请参阅 [安装 Windows Server App fabric](/previous-versions/appfabric/ee790960(v=azure.10))。</span><span class="sxs-lookup"><span data-stu-id="e94a0-113">For more information about installing Windows Server App Fabric see [Installing Windows Server App Fabric](/previous-versions/appfabric/ee790960(v=azure.10)).</span></span>  
  
### <a name="creating-a-simple-workflow-service"></a><span data-ttu-id="e94a0-114">创建简单工作流服务</span><span class="sxs-lookup"><span data-stu-id="e94a0-114">Creating a Simple Workflow Service</span></span>  
  
1. <span data-ttu-id="e94a0-115">打开 Visual Studio 2012 并加载在 [创建长时间运行的工作流服务](creating-a-long-running-workflow-service.md) 主题中创建的 OrderProcessing 解决方案。</span><span class="sxs-lookup"><span data-stu-id="e94a0-115">Open Visual Studio 2012 and load the OrderProcessing solution you created in the [Creating a Long-running Workflow Service](creating-a-long-running-workflow-service.md) topic.</span></span>  
  
2. <span data-ttu-id="e94a0-116">右键单击 " **OrderService** " 项目并选择 " **属性** "，然后选择 " **Web** " 选项卡。</span><span class="sxs-lookup"><span data-stu-id="e94a0-116">Right click the **OrderService** project and select **Properties** and select the **Web** tab.</span></span>  
  
3. <span data-ttu-id="e94a0-117">在 "属性" 页的 " **启动操作** " 部分中，选择 " **特定页面** "，然后在编辑框中键入 Service1。</span><span class="sxs-lookup"><span data-stu-id="e94a0-117">In the **Start Action** section of the property page select **Specific Page** and type Service1.xamlx in the edit box.</span></span>  
  
4. <span data-ttu-id="e94a0-118">在属性页的 " **服务器** " 部分中，选择 " **使用本地 IIS Web 服务器** "，并键入以下 URL： `http://localhost/OrderService` 。</span><span class="sxs-lookup"><span data-stu-id="e94a0-118">In the **Servers** section of the property page select **Use Local IIS Web Server** and type in the following URL: `http://localhost/OrderService`.</span></span>  
  
5. <span data-ttu-id="e94a0-119">单击 " **创建虚拟目录** " 按钮。</span><span class="sxs-lookup"><span data-stu-id="e94a0-119">Click the **Create Virtual Directory** button.</span></span> <span data-ttu-id="e94a0-120">这将新建一个虚拟目录，并将项目设置为在生成项目时将所需文件复制到此虚拟目录。</span><span class="sxs-lookup"><span data-stu-id="e94a0-120">This will create a new virtual directory and set up the project to copy the needed files to the virtual directory when the project is built.</span></span>  <span data-ttu-id="e94a0-121">或者，你也可以手动将 .xamlx、web.config 以及任何所需的 DLL 复制到此虚拟目录。</span><span class="sxs-lookup"><span data-stu-id="e94a0-121">Alternatively you could manually copy the .xamlx, the web.config, and any needed DLLs to the virtual directory.</span></span>  
  
### <a name="configuring-a-workflow-service-hosted-in-windows-server-app-fabric"></a><span data-ttu-id="e94a0-122">配置承载于 Windows Server App Fabric 中的工作流服务</span><span class="sxs-lookup"><span data-stu-id="e94a0-122">Configuring a Workflow Service Hosted in Windows Server App Fabric</span></span>  
  
1. <span data-ttu-id="e94a0-123">打开 Internet 信息服务管理器 (inetmgr.exe)。</span><span class="sxs-lookup"><span data-stu-id="e94a0-123">Open Internet Information Services Manager (inetmgr.exe).</span></span>  
  
2. <span data-ttu-id="e94a0-124">在 " **连接** " 窗格中导航到 OrderService 虚拟目录。</span><span class="sxs-lookup"><span data-stu-id="e94a0-124">Navigate to the OrderService virtual directory in the **Connections** pane.</span></span>  
  
3. <span data-ttu-id="e94a0-125">右键单击 OrderService，然后选择 " **管理 WCF 和 WF 服务**， **配置 ...**"。</span><span class="sxs-lookup"><span data-stu-id="e94a0-125">Right click OrderService and select **Manage WCF and WF Services**, **Configure…**.</span></span> <span data-ttu-id="e94a0-126">将显示 " **为应用程序配置 WCF 和 WF** " 对话框。</span><span class="sxs-lookup"><span data-stu-id="e94a0-126">The **Configure WCF and WF for Application** dialog box is displayed.</span></span>  
  
4. <span data-ttu-id="e94a0-127">选择 " **常规** " 选项卡以显示有关应用程序的一般信息，如以下屏幕截图所示。</span><span class="sxs-lookup"><span data-stu-id="e94a0-127">Select the **General** tab to display general information about the application as shown in the following screenshot.</span></span>  
  
     <span data-ttu-id="e94a0-128">![“App Fabric 配置”对话框的“常规”选项卡](media/appfabricconfiguration-general.gif "AppFabricConfiguration-常规")</span><span class="sxs-lookup"><span data-stu-id="e94a0-128">![General tab of the App Fabric Configuration dialog](media/appfabricconfiguration-general.gif "AppFabricConfiguration-General")</span></span>  
  
5. <span data-ttu-id="e94a0-129">选择 " **监视** " 选项卡。这会显示各种监视设置，如以下屏幕截图所示。</span><span class="sxs-lookup"><span data-stu-id="e94a0-129">Select the **Monitoring** tab. This shows various monitoring settings as shown in the following screenshot.</span></span>  
  
     <span data-ttu-id="e94a0-130">![“App Fabric 配置监视”选项卡](media/appfabricconfiguration-monitoring.gif "AppFabricConfiguration-监视")</span><span class="sxs-lookup"><span data-stu-id="e94a0-130">![App Fabric Configuration Monitoring tab](media/appfabricconfiguration-monitoring.gif "AppFabricConfiguration-Monitoring")</span></span>  
  
     <span data-ttu-id="e94a0-131">有关在应用结构中配置工作流服务监视的详细信息，请参阅 [配置应用构造监视](/previous-versions/appfabric/ee677384(v=azure.10))。</span><span class="sxs-lookup"><span data-stu-id="e94a0-131">For more information about configuring workflow service monitoring in App Fabric see [Configuring monitoring with App Fabric](/previous-versions/appfabric/ee677384(v=azure.10)).</span></span>  
  
6. <span data-ttu-id="e94a0-132">选择 " **工作流持久性** " 选项卡。这使你可以将应用程序配置为使用 App Fabric 的默认永久性提供程序，如以下屏幕截图所示。</span><span class="sxs-lookup"><span data-stu-id="e94a0-132">Select the **Workflow Persistence** tab. This allows you to configure your application to use App Fabric’s default persistence provider as shown in the following screenshot.</span></span>  
  
     <span data-ttu-id="e94a0-133">![应用程序结构配置 &#45; 持久性](media/appfabricconfiguration-persistence.gif "AppFabricConfiguration-持久性")</span><span class="sxs-lookup"><span data-stu-id="e94a0-133">![App Fabric Configuration &#45; Persistence](media/appfabricconfiguration-persistence.gif "AppFabricConfiguration-Persistence")</span></span>  
  
     <span data-ttu-id="e94a0-134">有关在 Windows Server App Fabric 中配置工作流持久性的详细信息，请参阅 [在应用结构中配置工作流持久性](/previous-versions/appfabric/ee677353(v=azure.10))。</span><span class="sxs-lookup"><span data-stu-id="e94a0-134">For more information about configuring workflow persistence in Windows Server App Fabric see [Configuring Workflow Persistence in App Fabric](/previous-versions/appfabric/ee677353(v=azure.10)).</span></span>  
  
7. <span data-ttu-id="e94a0-135">选择 " **工作流主机管理** " 选项卡。这样，你可以指定何时卸载和持久保存空闲工作流服务实例，如以下屏幕截图中所示。</span><span class="sxs-lookup"><span data-stu-id="e94a0-135">Select the **Workflow Host Management** tab. This allows you to specify when idle workflow service instances should be unloaded and persisted as shown in the following screenshot.</span></span>  
  
     <span data-ttu-id="e94a0-136">![应用结构配置工作流主机管理](media/appfabricconfiguration-management.gif "AppFabricConfiguration-管理")</span><span class="sxs-lookup"><span data-stu-id="e94a0-136">![App Fabric Configuration  Workflow Host Management](media/appfabricconfiguration-management.gif "AppFabricConfiguration-Management")</span></span>  
  
     <span data-ttu-id="e94a0-137">有关工作流主机管理配置的详细信息，请参阅 [在应用结构中配置工作流主机管理](/previous-versions/appfabric/ff383424(v=azure.10))。</span><span class="sxs-lookup"><span data-stu-id="e94a0-137">For more information about workflow host management configuration see [Configuring Workflow Host Management in App Fabric](/previous-versions/appfabric/ff383424(v=azure.10)).</span></span>  
  
8. <span data-ttu-id="e94a0-138">选择 " **自动启动** " 选项卡。这使你可以为应用程序中的工作流服务指定自动启动设置，如以下屏幕截图所示。</span><span class="sxs-lookup"><span data-stu-id="e94a0-138">Select the **Auto-Start** tab. This allows you to specify auto-start settings for the workflow services in the application as shown in the following screenshot.</span></span>  
  
     ![显示 App Fabric 自动&#45;启动配置的屏幕截图。](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/app-fabric-auto-start-configuration.gif)  
  
     <span data-ttu-id="e94a0-140">有关配置自动启动的详细信息，请参阅 [通过 App Fabric 配置自动启动](/previous-versions/appfabric/ee677261(v=azure.10))。</span><span class="sxs-lookup"><span data-stu-id="e94a0-140">For more information about configuring Auto-Start see [Configuring Auto-Start with App Fabric](/previous-versions/appfabric/ee677261(v=azure.10)).</span></span>  
  
9. <span data-ttu-id="e94a0-141">选择 " **限制** " 选项卡。这允许你为工作流服务配置阻止设置，如以下屏幕截图所示。</span><span class="sxs-lookup"><span data-stu-id="e94a0-141">Select the **Throttling** tab. This allows you to configure throttling settings for the workflow service as shown in the following screenshot.</span></span>  
  
     ![显示 App Fabric 限制配置的屏幕截图。](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/app-fabric-throttling-configuration.gif)  
  
     <span data-ttu-id="e94a0-143">有关配置限制的详细信息，请参阅 [配置应用程序结构的限制](/previous-versions/appfabric/ee677261(v=azure.10))。</span><span class="sxs-lookup"><span data-stu-id="e94a0-143">For more information about configuring throttling see [Configuring Throttling with App Fabric](/previous-versions/appfabric/ee677261(v=azure.10)).</span></span>  
  
10. <span data-ttu-id="e94a0-144">选择 " **安全** " 选项卡。这允许你为应用程序配置安全设置，如以下屏幕截图所示。</span><span class="sxs-lookup"><span data-stu-id="e94a0-144">Select the **Security** tab. This allows you to configure security settings for the application as shown in the following screenshot.</span></span>  
  
     <span data-ttu-id="e94a0-145">![App Fabric 安全配置](media/appfabricconfiguration-security.gif "AppFabricConfiguration-安全性")</span><span class="sxs-lookup"><span data-stu-id="e94a0-145">![App Fabric Security Configuration](media/appfabricconfiguration-security.gif "AppFabricConfiguration-Security")</span></span>  
  
     <span data-ttu-id="e94a0-146">有关配置 Windows Server App Fabric 安全性的详细信息，请参阅 [配置应用程序结构的安全性](/previous-versions/appfabric/ee677278(v=azure.10))。</span><span class="sxs-lookup"><span data-stu-id="e94a0-146">For more information about configuring security with Windows Server App Fabric see [Configuring Security with App Fabric](/previous-versions/appfabric/ee677278(v=azure.10)).</span></span>  
  
### <a name="using-windows-server-app-fabric"></a><span data-ttu-id="e94a0-147">使用 Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="e94a0-147">Using Windows Server App Fabric</span></span>  
  
1. <span data-ttu-id="e94a0-148">生成解决方案以便将所需的文件复制到虚拟目录。</span><span class="sxs-lookup"><span data-stu-id="e94a0-148">Build the solution to copy the necessary files to the virtual directory.</span></span>  
  
2. <span data-ttu-id="e94a0-149">右键单击 "OrderClient" 项目，然后选择 " **调试**" 和 " **启动新实例** " 以启动客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="e94a0-149">Right click the OrderClient project and select **Debug**, **Start New Instance** to launch the client application.</span></span>  
  
3. <span data-ttu-id="e94a0-150">客户端将运行，Visual Studio 将显示 " **附加安全警告** " 对话框，单击 " **不附加** " 按钮。</span><span class="sxs-lookup"><span data-stu-id="e94a0-150">The client will run and Visual Studio will display an **Attach Security Warning** dialog box, click the **Don’t Attach** button.</span></span> <span data-ttu-id="e94a0-151">这会告知 Visual Studio 不要附加到 IIS 进程进行调试。</span><span class="sxs-lookup"><span data-stu-id="e94a0-151">This tells Visual Studio to not attach to the IIS process for debugging.</span></span>  
  
4. <span data-ttu-id="e94a0-152">客户端应用程序将立即调用工作流服务，然后等待。</span><span class="sxs-lookup"><span data-stu-id="e94a0-152">The client application will immediately call the Workflow service and then wait.</span></span> <span data-ttu-id="e94a0-153">工作流服务将转为空闲暂留状态。</span><span class="sxs-lookup"><span data-stu-id="e94a0-153">The workflow service will go idle and be persisted.</span></span> <span data-ttu-id="e94a0-154">通过启动 Internet 信息服务 (inetmgr.exe)，在“连接”窗格中导航至 OrderService 并将其选中，可以对此进行验证。</span><span class="sxs-lookup"><span data-stu-id="e94a0-154">You can verify this by starting Internet Information Services (inetmgr.exe), navigating to the OrderService in the Connections pane and selecting it.</span></span> <span data-ttu-id="e94a0-155">接下来，单击右侧窗格中的“App Fabric 仪表板”图标。</span><span class="sxs-lookup"><span data-stu-id="e94a0-155">Next, click the App Fabric Dashboard icon in the right-hand pane.</span></span> <span data-ttu-id="e94a0-156">在持久化 WF 实例下，你会看到一个保留的工作流服务实例，如以下屏幕截图所示。</span><span class="sxs-lookup"><span data-stu-id="e94a0-156">Under Persisted WF Instances you will see there is one persisted workflow service instance as shown in the following screenshot.</span></span>  
  
     ![显示 App Fabric 仪表板的屏幕截图。](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/app-fabric-dashboard.gif)  
  
     <span data-ttu-id="e94a0-158">**WF 实例历史记录**列出了有关工作流服务的信息，例如工作流服务激活次数、工作流服务实例完成的数目，以及有故障的工作流实例数。</span><span class="sxs-lookup"><span data-stu-id="e94a0-158">The **WF Instance History** lists information about the workflow service such as the number of workflow service activations, the number of workflow service instance completions, and the number of workflow instances with failures.</span></span> <span data-ttu-id="e94a0-159">在 "活动" 或 "空闲实例" 下，将显示一个链接，单击该链接将显示有关空闲工作流实例的详细信息，如以下屏幕截图中所示。</span><span class="sxs-lookup"><span data-stu-id="e94a0-159">Under Active or Idle instances a link will be displayed, clicking on the link will display more information about the idle workflow instances as shown in the following screenshot.</span></span>  
  
     ![显示保存的工作流实例详细信息的屏幕截图。](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/persisted-workflow-instance-detail.gif)  
  
     <span data-ttu-id="e94a0-161">有关 Windows Server App Fabric 功能以及如何使用它们的详细信息，请参阅 [Windows Server App Fabric 托管功能](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="e94a0-161">For more information about Windows Server App Fabric features and how to use them see [Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e94a0-162">请参阅</span><span class="sxs-lookup"><span data-stu-id="e94a0-162">See also</span></span>

- [<span data-ttu-id="e94a0-163">创建长时间运行的工作流服务</span><span class="sxs-lookup"><span data-stu-id="e94a0-163">Creating a Long-running Workflow Service</span></span>](creating-a-long-running-workflow-service.md)
- <span data-ttu-id="e94a0-164">[Windows Server App Fabric 承载功能](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="e94a0-164">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
- <span data-ttu-id="e94a0-165">[安装 Windows Server App Fabric](/previous-versions/appfabric/ee790960(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="e94a0-165">[Installing Windows Server App Fabric](/previous-versions/appfabric/ee790960(v=azure.10))</span></span>
- <span data-ttu-id="e94a0-166">[Windows Server App Fabric 文档](/previous-versions/appfabric/ff384253(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="e94a0-166">[Windows Server App Fabric Documentation](/previous-versions/appfabric/ff384253(v=azure.10))</span></span>

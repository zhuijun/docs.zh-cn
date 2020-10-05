---
title: 如何：启动服务
description: 了解启动服务的多种方式。 安装服务后，必须启动它。 开始调用服务类上的 OnStart 方法。
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
ms.openlocfilehash: 1ca597379ab2a8fdae19fcfc5351c29d716753dc
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608408"
---
# <a name="how-to-start-services"></a><span data-ttu-id="357a9-105">如何：启动服务</span><span class="sxs-lookup"><span data-stu-id="357a9-105">How to: Start Services</span></span>

<span data-ttu-id="357a9-106">安装服务后，必须启动它。</span><span class="sxs-lookup"><span data-stu-id="357a9-106">After a service is installed, it must be started.</span></span> <span data-ttu-id="357a9-107">开始调用服务类上的 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="357a9-107">Starting calls the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method on the service class.</span></span> <span data-ttu-id="357a9-108"><xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法通常定义服务将执行的有用工作。</span><span class="sxs-lookup"><span data-stu-id="357a9-108">Usually, the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method defines the useful work the service will perform.</span></span> <span data-ttu-id="357a9-109">服务启动后，在手动暂停或停止它前，该服务将保持活动状态。</span><span class="sxs-lookup"><span data-stu-id="357a9-109">After a service starts, it remains active until it is manually paused or stopped.</span></span>

<span data-ttu-id="357a9-110">服务可以设置为自动或手动启动。</span><span class="sxs-lookup"><span data-stu-id="357a9-110">Services can be set up to start automatically or manually.</span></span> <span data-ttu-id="357a9-111">自动启动的服务将在安装它的计算机重启或首次打开时启动。</span><span class="sxs-lookup"><span data-stu-id="357a9-111">A service that starts automatically will be started when the computer on which it is installed is rebooted or first turned on.</span></span> <span data-ttu-id="357a9-112">用户必须启动手动启动的服务。</span><span class="sxs-lookup"><span data-stu-id="357a9-112">A user must start a service that starts manually.</span></span>

> [!NOTE]
> <span data-ttu-id="357a9-113">默认情况下，使用 Visual Studio 创建的服务设置为手动启动。</span><span class="sxs-lookup"><span data-stu-id="357a9-113">By default, services created with Visual Studio are set to start manually.</span></span>

<span data-ttu-id="357a9-114">可以通过多种方式手动启动服务 — 从“服务器资源管理器”  、“服务控制管理器”  ，或从使用名为 <xref:System.ServiceProcess.ServiceController> 的组件的代码均可启动。</span><span class="sxs-lookup"><span data-stu-id="357a9-114">There are several ways you can manually start a service — from **Server Explorer**, from the **Services Control Manager**, or from code using a component called the <xref:System.ServiceProcess.ServiceController>.</span></span>

<span data-ttu-id="357a9-115">可以在 <xref:System.ServiceProcess.ServiceInstaller> 类中设置 <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> 属性，以确定是应该手动还是自动启动服务。</span><span class="sxs-lookup"><span data-stu-id="357a9-115">You set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property on the <xref:System.ServiceProcess.ServiceInstaller> class to determine whether a service should be started manually or automatically.</span></span>

### <a name="to-specify-how-a-service-should-start"></a><span data-ttu-id="357a9-116">指定服务的启动方式</span><span class="sxs-lookup"><span data-stu-id="357a9-116">To specify how a service should start</span></span>

1. <span data-ttu-id="357a9-117">在创建服务后为其添加必要的安装程序。</span><span class="sxs-lookup"><span data-stu-id="357a9-117">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="357a9-118">有关详细信息，请参阅[如何：将安装程序添加到服务应用程序](how-to-add-installers-to-your-service-application.md)。</span><span class="sxs-lookup"><span data-stu-id="357a9-118">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>

2. <span data-ttu-id="357a9-119">在设计器中，单击正在使用的服务的服务安装程序。</span><span class="sxs-lookup"><span data-stu-id="357a9-119">In the designer, click the service installer for the service you are working with.</span></span>

3. <span data-ttu-id="357a9-120">在“属性”  窗口中，将 <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> 属性设置为以下之一：</span><span class="sxs-lookup"><span data-stu-id="357a9-120">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to one of the following:</span></span>

    |<span data-ttu-id="357a9-121">安装服务</span><span class="sxs-lookup"><span data-stu-id="357a9-121">To have your service install</span></span>|<span data-ttu-id="357a9-122">设置此值</span><span class="sxs-lookup"><span data-stu-id="357a9-122">Set this value</span></span>|
    |----------------------------------|--------------------|
    |<span data-ttu-id="357a9-123">计算机重启时</span><span class="sxs-lookup"><span data-stu-id="357a9-123">When the computer is restarted</span></span>|<span data-ttu-id="357a9-124">**自动**</span><span class="sxs-lookup"><span data-stu-id="357a9-124">**Automatic**</span></span>|
    |<span data-ttu-id="357a9-125">显式用户动作启动服务时</span><span class="sxs-lookup"><span data-stu-id="357a9-125">When an explicit user action starts the service</span></span>|<span data-ttu-id="357a9-126">手动</span><span class="sxs-lookup"><span data-stu-id="357a9-126">**Manual**</span></span>|

    > [!TIP]
    > <span data-ttu-id="357a9-127">为防止服务完全启动，可以将 <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> 属性设置为“禁用”  。</span><span class="sxs-lookup"><span data-stu-id="357a9-127">To prevent your service from being started at all, you can set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to **Disabled**.</span></span> <span data-ttu-id="357a9-128">如果要多次重启服务器并希望通过阻止在服务器启动时通常会启动的服务来节省时间，则可以执行此操作。</span><span class="sxs-lookup"><span data-stu-id="357a9-128">You might do this if you are going to reboot a server several times and want to save time by preventing the services that would normally start from starting up.</span></span>

    > [!NOTE]
    > <span data-ttu-id="357a9-129">安装服务后，可以更改这些属性和其他属性。</span><span class="sxs-lookup"><span data-stu-id="357a9-129">These and other properties can be changed after your service is installed.</span></span>

    <span data-ttu-id="357a9-130">可以通过多种方式启动将其 <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> 进程设置为“手动”  的服务 — 从“服务器资源管理器”、   “Windows 服务控制管理器”，或从代码均可启动。</span><span class="sxs-lookup"><span data-stu-id="357a9-130">There are several ways you can start a service that has its <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> process set to **Manual** — from **Server Explorer**, from the **Windows Services Control Manager**, or from code.</span></span> <span data-ttu-id="357a9-131">请务必注意，实际上，并非所有这些方法都在服务控制管理器  的上下文中启动服务；  服务器资源管理器和启动服务的编程方法实际上会操纵控制器。</span><span class="sxs-lookup"><span data-stu-id="357a9-131">It is important to note that not all of these methods actually start the service in the context of the **Services Control Manager**; **Server Explorer** and programmatic methods of starting the service actually manipulate the controller.</span></span>

### <a name="to-manually-start-a-service-from-server-explorer"></a><span data-ttu-id="357a9-132">从“服务器资源管理器”手动启动服务</span><span class="sxs-lookup"><span data-stu-id="357a9-132">To manually start a service from Server Explorer</span></span>

1. <span data-ttu-id="357a9-133">在“服务器资源管理器”  中，添加所需的服务器（如果尚未列出）。</span><span class="sxs-lookup"><span data-stu-id="357a9-133">In **Server Explorer**, add the server you want if it is not already listed.</span></span> <span data-ttu-id="357a9-134">有关详细信息，请参阅“操作说明：访问和初始化服务器资源管理器/数据库资源管理器。</span><span class="sxs-lookup"><span data-stu-id="357a9-134">For more information, see How to: Access and Initialize Server Explorer-Database Explorer.</span></span>

2. <span data-ttu-id="357a9-135">展开“服务”  节点，然后找到要启动的服务。</span><span class="sxs-lookup"><span data-stu-id="357a9-135">Expand the **Services** node, and then locate the service you want to start.</span></span>

3. <span data-ttu-id="357a9-136">右键单击该服务的名称，然后单击“启动”  。</span><span class="sxs-lookup"><span data-stu-id="357a9-136">Right-click the name of the service, and click **Start**.</span></span>

### <a name="to-manually-start-a-service-from-services-control-manager"></a><span data-ttu-id="357a9-137">从“服务控制管理器”手动启动服务</span><span class="sxs-lookup"><span data-stu-id="357a9-137">To manually start a service from Services Control Manager</span></span>

1. <span data-ttu-id="357a9-138">执行以下操作之一，打开“服务控制管理器”  ：</span><span class="sxs-lookup"><span data-stu-id="357a9-138">Open the **Services Control Manager** by doing one of the following:</span></span>

    - <span data-ttu-id="357a9-139">在 Windows XP 和 2000 Professional 中，右键单击桌面上的“我的电脑”  ，然后单击“管理”  。</span><span class="sxs-lookup"><span data-stu-id="357a9-139">In Windows XP and 2000 Professional, right-click **My Computer** on the desktop, and then click **Manage**.</span></span> <span data-ttu-id="357a9-140">在出现的对话框中，展开“服务和应用程序”  节点。</span><span class="sxs-lookup"><span data-stu-id="357a9-140">In the dialog box that appears, expand the **Services and Applications** node.</span></span>

      <span data-ttu-id="357a9-141">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="357a9-141">\- or -</span></span>

    - <span data-ttu-id="357a9-142">在 Windows Server 2003 和 Windows 2000 Server 中，单击“开始”  ，指向“程序”  ，单击“管理工具”  ，然后单击“服务”  。</span><span class="sxs-lookup"><span data-stu-id="357a9-142">In Windows Server 2003 and Windows 2000 Server, click **Start**, point to **Programs**, click **Administrative Tools**, and then click **Services**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="357a9-143">在 Windows NT 4.0 版中，可以从“控制面板”  打开此对话框。</span><span class="sxs-lookup"><span data-stu-id="357a9-143">In Windows NT version 4.0, you can open this dialog box from **Control Panel**.</span></span>

    <span data-ttu-id="357a9-144">现在应该可看到在窗口的“服务”  部分列出的服务。</span><span class="sxs-lookup"><span data-stu-id="357a9-144">You should now see your service listed in the **Services** section of the window.</span></span>

2. <span data-ttu-id="357a9-145">从列表中选择你的服务，右键单击该服务，然后单击“启动”  。</span><span class="sxs-lookup"><span data-stu-id="357a9-145">Select your service in the list, right-click it, and then click **Start**.</span></span>

### <a name="to-manually-start-a-service-from-code"></a><span data-ttu-id="357a9-146">从代码手动启动服务</span><span class="sxs-lookup"><span data-stu-id="357a9-146">To manually start a service from code</span></span>

1. <span data-ttu-id="357a9-147">创建 <xref:System.ServiceProcess.ServiceController> 类的实例，并将其配置为与要管理的服务进行交互。</span><span class="sxs-lookup"><span data-stu-id="357a9-147">Create an instance of the <xref:System.ServiceProcess.ServiceController> class, and configure it to interact with the service you want to administer.</span></span>

2. <span data-ttu-id="357a9-148">调用 <xref:System.ServiceProcess.ServiceController.Start%2A> 方法以启动该服务。</span><span class="sxs-lookup"><span data-stu-id="357a9-148">Call the <xref:System.ServiceProcess.ServiceController.Start%2A> method to start the service.</span></span>

## <a name="see-also"></a><span data-ttu-id="357a9-149">请参阅</span><span class="sxs-lookup"><span data-stu-id="357a9-149">See also</span></span>

- [<span data-ttu-id="357a9-150">Windows 服务应用程序介绍</span><span class="sxs-lookup"><span data-stu-id="357a9-150">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="357a9-151">如何：创建 Windows 服务</span><span class="sxs-lookup"><span data-stu-id="357a9-151">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)
- [<span data-ttu-id="357a9-152">如何：将安装程序添加到服务应用程序</span><span class="sxs-lookup"><span data-stu-id="357a9-152">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)

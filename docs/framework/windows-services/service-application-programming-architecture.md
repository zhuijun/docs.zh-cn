---
title: 服务应用程序编程体系结构
description: 了解服务应用程序编程体系结构。 Windows 服务应用程序基于从 System.ServiceProcess.ServiceBase 继承的类。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ServiceController components, programming architecture
- ServiceBase class, service states
- Windows Service applications, code model
- services, programming architecture
- ServiceController class
- services, states
- ServiceProcessInstaller class, service application code model
- Windows Service applications, states
ms.assetid: 83230026-d068-4174-97ff-e264c896eb2f
ms.openlocfilehash: 386311228abb08600acc249e80702c724c137900
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609260"
---
# <a name="service-application-programming-architecture"></a><span data-ttu-id="9047a-104">服务应用程序编程体系结构</span><span class="sxs-lookup"><span data-stu-id="9047a-104">Service Application Programming Architecture</span></span>
<span data-ttu-id="9047a-105">Windows 服务应用程序基于从 <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> 类继承的类。</span><span class="sxs-lookup"><span data-stu-id="9047a-105">Windows Service applications are based on a class that inherits from the <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="9047a-106">可以替代此类中的方法并为其定义功能，以确定服务的行为方式。</span><span class="sxs-lookup"><span data-stu-id="9047a-106">You override methods from this class and define functionality for them to determine how your service behaves.</span></span>  
  
 <span data-ttu-id="9047a-107">服务创建中涉及的主要类包括：</span><span class="sxs-lookup"><span data-stu-id="9047a-107">The main classes involved in service creation are:</span></span>  
  
- <span data-ttu-id="9047a-108"><xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> — 可以在创建服务时替代 <xref:System.ServiceProcess.ServiceBase> 类中的方法，并定义代码以确定服务在此继承类中的工作方式。</span><span class="sxs-lookup"><span data-stu-id="9047a-108"><xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> — You override methods from the <xref:System.ServiceProcess.ServiceBase> class when creating a service and define the code to determine how your service functions in this inherited class.</span></span>  
  
- <span data-ttu-id="9047a-109"><xref:System.ServiceProcess.ServiceProcessInstaller?displayProperty=nameWithType> 和 <xref:System.ServiceProcess.ServiceInstaller?displayProperty=nameWithType> — 使用这些类来安装和卸载服务。</span><span class="sxs-lookup"><span data-stu-id="9047a-109"><xref:System.ServiceProcess.ServiceProcessInstaller?displayProperty=nameWithType> and <xref:System.ServiceProcess.ServiceInstaller?displayProperty=nameWithType> —You use these classes to install and uninstall your service.</span></span>  
  
 <span data-ttu-id="9047a-110">另外，可以使用名为 <xref:System.ServiceProcess.ServiceController> 的类来操纵服务本身。</span><span class="sxs-lookup"><span data-stu-id="9047a-110">In addition, a class named <xref:System.ServiceProcess.ServiceController> can be used to manipulate the service itself.</span></span> <span data-ttu-id="9047a-111">该类不参与创建服务，但可用于启动和停止服务、将命令传递给它并返回一系列枚举。</span><span class="sxs-lookup"><span data-stu-id="9047a-111">This class is not involved in the creation of a service, but can be used to start and stop the service, pass commands to it, and return a series of enumerations.</span></span>  
  
## <a name="defining-your-services-behavior"></a><span data-ttu-id="9047a-112">定义服务的行为</span><span class="sxs-lookup"><span data-stu-id="9047a-112">Defining Your Service's Behavior</span></span>  
 <span data-ttu-id="9047a-113">在服务类中，替代基类函数，这些函数可确定服务状态在服务控制管理器中更改时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="9047a-113">In your service class, you override base class functions that determine what happens when the state of your service is changed in the Services Control Manager.</span></span> <span data-ttu-id="9047a-114"><xref:System.ServiceProcess.ServiceBase> 类公开以下方法，可替代这些方法以添加自定义行为。</span><span class="sxs-lookup"><span data-stu-id="9047a-114">The <xref:System.ServiceProcess.ServiceBase> class exposes the following methods, which you can override to add custom behavior.</span></span>  
  
|<span data-ttu-id="9047a-115">方法</span><span class="sxs-lookup"><span data-stu-id="9047a-115">Method</span></span>|<span data-ttu-id="9047a-116">替代为</span><span class="sxs-lookup"><span data-stu-id="9047a-116">Override to</span></span>|  
|------------|-----------------|  
|<xref:System.ServiceProcess.ServiceBase.OnStart%2A>|<span data-ttu-id="9047a-117">指示服务开始运行时应采取的操作。</span><span class="sxs-lookup"><span data-stu-id="9047a-117">Indicate what actions should be taken when your service starts running.</span></span> <span data-ttu-id="9047a-118">必须在此过程中为服务编写代码才能执行有用的操作。</span><span class="sxs-lookup"><span data-stu-id="9047a-118">You must write code in this procedure for your service to perform useful work.</span></span>|  
|<xref:System.ServiceProcess.ServiceBase.OnPause%2A>|<span data-ttu-id="9047a-119">指示在服务暂停时应发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="9047a-119">Indicate what should happen when your service is paused.</span></span>|  
|<xref:System.ServiceProcess.ServiceBase.OnStop%2A>|<span data-ttu-id="9047a-120">指示在服务停止运行时应发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="9047a-120">Indicate what should happen when your service stops running.</span></span>|  
|<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>|<span data-ttu-id="9047a-121">指示服务在暂停后恢复正常运行时应发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="9047a-121">Indicate what should happen when your service resumes normal functioning after being paused.</span></span>|  
|<xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>|<span data-ttu-id="9047a-122">指示在系统关闭之前应发生什么情况（如果此时服务正在运行）。</span><span class="sxs-lookup"><span data-stu-id="9047a-122">Indicate what should happen just prior to your system shutting down, if your service is running at that time.</span></span>|  
|<xref:System.ServiceProcess.ServiceBase.OnCustomCommand%2A>|<span data-ttu-id="9047a-123">指示服务在收到自定义命令时应发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="9047a-123">Indicate what should happen when your service receives a custom command.</span></span> <span data-ttu-id="9047a-124">有关自定义命令的详细信息，请参阅 MSDN Online。</span><span class="sxs-lookup"><span data-stu-id="9047a-124">For more information on custom commands, see MSDN online.</span></span>|  
|<xref:System.ServiceProcess.ServiceBase.OnPowerEvent%2A>|<span data-ttu-id="9047a-125">指示服务在收到电源管理事件时应如何响应，如电池电量不足或已挂起的操作。</span><span class="sxs-lookup"><span data-stu-id="9047a-125">Indicate how the service should respond when a power management event is received, such as a low battery or suspended operation.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="9047a-126">这些方法表示服务在其生存期中不断变化的状态；服务从一个状态转换到下一个状态。</span><span class="sxs-lookup"><span data-stu-id="9047a-126">These methods represent states that the service moves through in its lifetime; the service transitions from one state to the next.</span></span> <span data-ttu-id="9047a-127">例如，在调用 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 之前，将永远无法获得该服务来响应 <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> 命令。</span><span class="sxs-lookup"><span data-stu-id="9047a-127">For example, you will never get the service to respond to an <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> command before <xref:System.ServiceProcess.ServiceBase.OnStart%2A> has been called.</span></span>  
  
 <span data-ttu-id="9047a-128">还有其他几个令人感兴趣的属性和方法。</span><span class="sxs-lookup"><span data-stu-id="9047a-128">There are several other properties and methods that are of interest.</span></span> <span data-ttu-id="9047a-129">这些方法包括：</span><span class="sxs-lookup"><span data-stu-id="9047a-129">These include:</span></span>  
  
- <span data-ttu-id="9047a-130"><xref:System.ServiceProcess.ServiceBase> 类的 <xref:System.ServiceProcess.ServiceBase.Run%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="9047a-130">The <xref:System.ServiceProcess.ServiceBase.Run%2A> method on the <xref:System.ServiceProcess.ServiceBase> class.</span></span> <span data-ttu-id="9047a-131">这是服务的主入口点。</span><span class="sxs-lookup"><span data-stu-id="9047a-131">This is the main entry point for the service.</span></span> <span data-ttu-id="9047a-132">使用 Windows 服务模板创建服务时，将在应用程序的 `Main` 方法中插入代码以运行该服务。</span><span class="sxs-lookup"><span data-stu-id="9047a-132">When you create a service using the Windows Service template, code is inserted in your application's `Main` method to run the service.</span></span> <span data-ttu-id="9047a-133">此代码如下所示：</span><span class="sxs-lookup"><span data-stu-id="9047a-133">This code looks like this:</span></span>  
  
     [!code-csharp[VbRadconService#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#6)]
     [!code-vb[VbRadconService#6](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#6)]  
  
    > [!NOTE]
    > <span data-ttu-id="9047a-134">这些示例使用 <xref:System.ServiceProcess.ServiceBase> 类型的数组，可将应用程序包含的每项服务添加到其中，然后所有服务均可一同运行。</span><span class="sxs-lookup"><span data-stu-id="9047a-134">These examples use an array of type <xref:System.ServiceProcess.ServiceBase>, into which each service your application contains can be added, and then all of the services can be run together.</span></span> <span data-ttu-id="9047a-135">但是，如果仅创建单个服务，则可以选择不使用该数组，然后只声明从 <xref:System.ServiceProcess.ServiceBase> 继承的新对象，然后运行它。</span><span class="sxs-lookup"><span data-stu-id="9047a-135">If you are only creating a single service, however, you might choose not to use the array and simply declare a new object inheriting from <xref:System.ServiceProcess.ServiceBase> and then run it.</span></span> <span data-ttu-id="9047a-136">有关示例，请参见 [如何：以编程方式编写服务](how-to-write-services-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="9047a-136">For an example, see [How to: Write Services Programmatically](how-to-write-services-programmatically.md).</span></span>  
  
- <span data-ttu-id="9047a-137"><xref:System.ServiceProcess.ServiceBase> 类的一系列属性。</span><span class="sxs-lookup"><span data-stu-id="9047a-137">A series of properties on the <xref:System.ServiceProcess.ServiceBase> class.</span></span> <span data-ttu-id="9047a-138">这些属性确定可对服务调用的方法。</span><span class="sxs-lookup"><span data-stu-id="9047a-138">These determine what methods can be called on your service.</span></span> <span data-ttu-id="9047a-139">例如，当 <xref:System.ServiceProcess.ServiceBase.CanStop%2A> 属性设置为 `true` 时，可以调用服务上的 <xref:System.ServiceProcess.ServiceBase.OnStop%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="9047a-139">For example, when the <xref:System.ServiceProcess.ServiceBase.CanStop%2A> property is set to `true`, the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method on your service can be called.</span></span> <span data-ttu-id="9047a-140">当 <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> 属性设置为 `true` 时，可以调用 <xref:System.ServiceProcess.ServiceBase.OnPause%2A> 和 <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="9047a-140">When the <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> property is set to `true`, the <xref:System.ServiceProcess.ServiceBase.OnPause%2A> and <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> methods can be called.</span></span> <span data-ttu-id="9047a-141">在将其中一个属性设置为 `true` 时，应该替代并定义关联方法的处理进程。</span><span class="sxs-lookup"><span data-stu-id="9047a-141">When you set one of these properties to `true`, you should then override and define processing for the associated methods.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="9047a-142">服务必须至少替代 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 和 <xref:System.ServiceProcess.ServiceBase.OnStop%2A> 才有用。</span><span class="sxs-lookup"><span data-stu-id="9047a-142">Your service must override at least <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> to be useful.</span></span>  
  
 <span data-ttu-id="9047a-143">还可以使用名为 <xref:System.ServiceProcess.ServiceController> 的组件与现有服务进行通信并控制其行为。</span><span class="sxs-lookup"><span data-stu-id="9047a-143">You can also use a component called the <xref:System.ServiceProcess.ServiceController> to communicate with and control the behavior of an existing service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9047a-144">请参阅</span><span class="sxs-lookup"><span data-stu-id="9047a-144">See also</span></span>

- [<span data-ttu-id="9047a-145">Windows 服务应用程序介绍</span><span class="sxs-lookup"><span data-stu-id="9047a-145">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="9047a-146">如何：创建 Windows 服务</span><span class="sxs-lookup"><span data-stu-id="9047a-146">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)

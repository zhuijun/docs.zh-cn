---
title: 如何：以编程方式编写服务
description: 了解如何通过自行设置继承和其他基础结构元素以编程方式编写服务。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- services, creating
- Windows Service applications, creating
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
ms.openlocfilehash: cd749d325bec6636243dec1905f79abb5e42f04e
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608395"
---
# <a name="how-to-write-services-programmatically"></a><span data-ttu-id="7b77e-103">如何：以编程方式编写服务</span><span class="sxs-lookup"><span data-stu-id="7b77e-103">How to: Write Services Programmatically</span></span>
<span data-ttu-id="7b77e-104">如果选择不使用 Windows 服务项目模板，则可以通过自行设置继承和其他基础结构元素来编写自己的服务。</span><span class="sxs-lookup"><span data-stu-id="7b77e-104">If you choose not to use the Windows Service project template, you can write your own services by setting up the inheritance and other infrastructure elements yourself.</span></span> <span data-ttu-id="7b77e-105">当以编程方式创建服务时，必须执行以下几个步骤（否则，模板将为你处理）：</span><span class="sxs-lookup"><span data-stu-id="7b77e-105">When you create a service programmatically, you must perform several steps that the template would otherwise handle for you:</span></span>  
  
- <span data-ttu-id="7b77e-106">必须将服务类设置为从 <xref:System.ServiceProcess.ServiceBase> 类继承。</span><span class="sxs-lookup"><span data-stu-id="7b77e-106">You must set up your service class to inherit from the <xref:System.ServiceProcess.ServiceBase> class.</span></span>  
  
- <span data-ttu-id="7b77e-107">必须为服务项目创建 `Main` 方法，该方法定义要运行的服务并在其上调用 <xref:System.ServiceProcess.ServiceBase.Run%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="7b77e-107">You must create a `Main` method for your service project that defines the services to run and calls the <xref:System.ServiceProcess.ServiceBase.Run%2A> method on them.</span></span>  
  
- <span data-ttu-id="7b77e-108">必须替代 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 和 <xref:System.ServiceProcess.ServiceBase.OnStop%2A> 过程并填入你希望它们运行的任何代码。</span><span class="sxs-lookup"><span data-stu-id="7b77e-108">You must override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures and fill in any code you want them to run.</span></span>  
  
### <a name="to-write-a-service-programmatically"></a><span data-ttu-id="7b77e-109">以编程方式编写服务</span><span class="sxs-lookup"><span data-stu-id="7b77e-109">To write a service programmatically</span></span>  
  
1. <span data-ttu-id="7b77e-110">创建一个空项目并通过以下步骤创建对必要命名空间的引用：</span><span class="sxs-lookup"><span data-stu-id="7b77e-110">Create an empty project and create a reference to the necessary namespaces by following these steps:</span></span>  
  
    1. <span data-ttu-id="7b77e-111">在“解决方案资源管理器”  中，右键单击“引用”  节点，然后单击  “添加引用”。</span><span class="sxs-lookup"><span data-stu-id="7b77e-111">In **Solution Explorer**, right-click the **References** node and click **Add Reference**.</span></span>  
  
    2. <span data-ttu-id="7b77e-112">在“.NET Framework”  选项卡上，滚动到“System.dll”  ，然后单击“选择”  。</span><span class="sxs-lookup"><span data-stu-id="7b77e-112">On the **.NET Framework** tab, scroll to **System.dll** and click **Select**.</span></span>  
  
    3. <span data-ttu-id="7b77e-113">滚动到“System.ServiceProcess.dll”  ，然后单击“选择”  。</span><span class="sxs-lookup"><span data-stu-id="7b77e-113">Scroll to **System.ServiceProcess.dll** and click **Select**.</span></span>  
  
    4. <span data-ttu-id="7b77e-114">单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="7b77e-114">Click **OK**.</span></span>  
  
2. <span data-ttu-id="7b77e-115">添加一个类并将其配置为从 <xref:System.ServiceProcess.ServiceBase> 继承：</span><span class="sxs-lookup"><span data-stu-id="7b77e-115">Add a class and configure it to inherit from <xref:System.ServiceProcess.ServiceBase>:</span></span>  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3. <span data-ttu-id="7b77e-116">添加下面的代码来配置服务类：</span><span class="sxs-lookup"><span data-stu-id="7b77e-116">Add the following code to configure your service class:</span></span>  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4. <span data-ttu-id="7b77e-117">为类创建 `Main` 方法，并用它来定义类将包含的服务；`userService1` 是类的名称：</span><span class="sxs-lookup"><span data-stu-id="7b77e-117">Create a `Main` method for your class, and use it to define the service your class will contain; `userService1` is the name of the class:</span></span>  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5. <span data-ttu-id="7b77e-118">替代 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法，并定义服务启动时想要执行的任何处理进程。</span><span class="sxs-lookup"><span data-stu-id="7b77e-118">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and define any processing you want to occur when your service is started.</span></span>  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6. <span data-ttu-id="7b77e-119">替代要为其定义自定义处理进程的任何其他方法，并编写代码以确定服务在每种情况下应采取的操作。</span><span class="sxs-lookup"><span data-stu-id="7b77e-119">Override any other methods you want to define custom processing for, and write code to determine the actions the service should take in each case.</span></span>  
  
7. <span data-ttu-id="7b77e-120">添加服务应用程序所必需的安装程序。</span><span class="sxs-lookup"><span data-stu-id="7b77e-120">Add the necessary installers for your service application.</span></span> <span data-ttu-id="7b77e-121">有关详细信息，请参阅[如何：将安装程序添加到服务应用程序](how-to-add-installers-to-your-service-application.md)。</span><span class="sxs-lookup"><span data-stu-id="7b77e-121">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>  
  
8. <span data-ttu-id="7b77e-122">通过从“生成”  菜单选择“生成解决方案”  来生成项目。</span><span class="sxs-lookup"><span data-stu-id="7b77e-122">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7b77e-123">不要通过按 F5 来运行你的项目 — 你无法通过这种方式运行服务项目。</span><span class="sxs-lookup"><span data-stu-id="7b77e-123">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
9. <span data-ttu-id="7b77e-124">创建安装项目和自定义操作以安装服务。</span><span class="sxs-lookup"><span data-stu-id="7b77e-124">Create a setup project and the custom actions to install your service.</span></span> <span data-ttu-id="7b77e-125">有关示例，请参阅[演练：在组件设计器中创建 Windows 服务应用程序](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="7b77e-125">For an example, see [Walkthrough: Creating a Windows Service Application in the Component Designer](walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>  
  
10. <span data-ttu-id="7b77e-126">安装服务。</span><span class="sxs-lookup"><span data-stu-id="7b77e-126">Install the service.</span></span> <span data-ttu-id="7b77e-127">有关详细信息，请参阅[如何：安装和卸载服务](how-to-install-and-uninstall-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7b77e-127">For more information, see [How to: Install and Uninstall Services](how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b77e-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="7b77e-128">See also</span></span>

- [<span data-ttu-id="7b77e-129">Windows 服务应用程序介绍</span><span class="sxs-lookup"><span data-stu-id="7b77e-129">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="7b77e-130">如何：创建 Windows 服务</span><span class="sxs-lookup"><span data-stu-id="7b77e-130">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)
- [<span data-ttu-id="7b77e-131">如何：将安装程序添加到服务应用程序</span><span class="sxs-lookup"><span data-stu-id="7b77e-131">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="7b77e-132">如何：记录关于服务的信息</span><span class="sxs-lookup"><span data-stu-id="7b77e-132">How to: Log Information About Services</span></span>](how-to-log-information-about-services.md)
- [<span data-ttu-id="7b77e-133">演练：在组件设计器中创建 Windows 服务应用程序</span><span class="sxs-lookup"><span data-stu-id="7b77e-133">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

---
title: 教程：定义 Windows Communication Foundation 服务协定
description: 了解如何将服务约定定义为一系列文章中的一部分，这些文章可帮助你开始创建 WCF 应用程序。
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 5cb371da8c7180b8c4cbf5ac11468fbb8e0e13cc
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246306"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="65712-103">教程：定义 Windows Communication Foundation 服务协定</span><span class="sxs-lookup"><span data-stu-id="65712-103">Tutorial: Define a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="65712-104">本教程介绍创建基本 Windows Communication Foundation （WCF）应用程序所需的五个任务中的第一个。</span><span class="sxs-lookup"><span data-stu-id="65712-104">This tutorial describes the first of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="65712-105">有关教程的概述，请参阅[教程： Windows Communication Foundation 应用程序入门](getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="65712-105">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="65712-106">创建 WCF 服务时，第一个任务是定义服务协定。</span><span class="sxs-lookup"><span data-stu-id="65712-106">When you create a WCF service, your first task is to define a service contract.</span></span> <span data-ttu-id="65712-107">服务协定指定服务支持的操作。</span><span class="sxs-lookup"><span data-stu-id="65712-107">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="65712-108">可以将操作视为一个 Web 服务方法。</span><span class="sxs-lookup"><span data-stu-id="65712-108">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="65712-109">可以通过定义 c # 或 Visual Basic 界面来创建服务协定。</span><span class="sxs-lookup"><span data-stu-id="65712-109">You create service contracts by defining a C# or Visual Basic interface.</span></span> <span data-ttu-id="65712-110">接口具有以下特征：</span><span class="sxs-lookup"><span data-stu-id="65712-110">An interface has the following characteristics:</span></span>

- <span data-ttu-id="65712-111">接口中的每个方法都对应一个特定的服务操作。</span><span class="sxs-lookup"><span data-stu-id="65712-111">Each method in the interface corresponds to a specific service operation.</span></span>
- <span data-ttu-id="65712-112">对于每个接口，必须应用 <xref:System.ServiceModel.ServiceContractAttribute> 特性。</span><span class="sxs-lookup"><span data-stu-id="65712-112">For each interface, you must apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span>
- <span data-ttu-id="65712-113">对于每个操作/方法，必须应用 <xref:System.ServiceModel.OperationContractAttribute> 特性。</span><span class="sxs-lookup"><span data-stu-id="65712-113">For each operation/method, you must apply the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span>

<span data-ttu-id="65712-114">在本教程中，你将了解如何执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="65712-114">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="65712-115">创建一个**WCF 服务库**项目。</span><span class="sxs-lookup"><span data-stu-id="65712-115">Create a **WCF Service Library** project.</span></span>
> - <span data-ttu-id="65712-116">定义服务协定接口。</span><span class="sxs-lookup"><span data-stu-id="65712-116">Define a service contract interface.</span></span>

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a><span data-ttu-id="65712-117">创建 WCF 服务库项目并定义服务协定接口</span><span class="sxs-lookup"><span data-stu-id="65712-117">Create a WCF Service Library project and define a service contract interface</span></span>

1. <span data-ttu-id="65712-118">以管理员的身份打开 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="65712-118">Open Visual Studio as an administrator.</span></span> <span data-ttu-id="65712-119">为此，请在 "**开始**" 菜单中选择 "Visual Studio" 程序，然后从快捷菜单中选择 "**更多**  >  **运行方式管理员**"。</span><span class="sxs-lookup"><span data-stu-id="65712-119">To do so, select the Visual Studio program in the **Start** menu, and then select **More** > **Run as administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="65712-120">创建一个**WCF 服务库**项目。</span><span class="sxs-lookup"><span data-stu-id="65712-120">Create a **WCF Service Library** project.</span></span>

   1. <span data-ttu-id="65712-121">从“文件”菜单中选择“新建” > “项目”  。</span><span class="sxs-lookup"><span data-stu-id="65712-121">From the **File** menu, select **New** > **Project**.</span></span>

   2. <span data-ttu-id="65712-122">在 "**新建项目**" 对话框的左侧，展开 " **Visual c #** " 或 " **Visual Basic**"，然后选择 " **WCF** " 类别。</span><span class="sxs-lookup"><span data-stu-id="65712-122">In the **New Project** dialog, on the left-hand side, expand **Visual C#** or **Visual Basic**, and then select the **WCF** category.</span></span> <span data-ttu-id="65712-123">Visual Studio 会在窗口的中间部分显示项目模板的列表。</span><span class="sxs-lookup"><span data-stu-id="65712-123">Visual Studio displays a list of project templates in the center section of the window.</span></span> <span data-ttu-id="65712-124">选择 " **WCF 服务库**"。</span><span class="sxs-lookup"><span data-stu-id="65712-124">Select **WCF Service Library**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="65712-125">如果看不到 " **WCF**项目模板" 类别，可能需要安装 Visual Studio 的**Windows Communication Foundation**组件。</span><span class="sxs-lookup"><span data-stu-id="65712-125">If you don't see the **WCF** project template category, you may need to install the **Windows Communication Foundation** component of Visual Studio.</span></span> <span data-ttu-id="65712-126">在 "**新建项目**" 对话框中，选择左侧的 "**打开 Visual Studio 安装程序**" 链接。</span><span class="sxs-lookup"><span data-stu-id="65712-126">In the **New Project** dialog box, select the **Open Visual Studio Installer** link on the left side.</span></span> <span data-ttu-id="65712-127">选择 "**单个组件**" 选项卡，然后在 "**开发活动**" 类别下查找并选择**Windows Communication Foundation** 。</span><span class="sxs-lookup"><span data-stu-id="65712-127">Select the **Individual components** tab, and then find and select **Windows Communication Foundation** under the **Development activities** category.</span></span> <span data-ttu-id="65712-128">选择 "**修改**" 开始安装组件。</span><span class="sxs-lookup"><span data-stu-id="65712-128">Choose **Modify** to begin installing the component.</span></span>

   3. <span data-ttu-id="65712-129">在窗口的底部，为 "**名称**" 和 " *GettingStarted* " 输入 " *GettingStartedLib* " 作为 "**解决方案名称**"。</span><span class="sxs-lookup"><span data-stu-id="65712-129">In the bottom section of the window, enter *GettingStartedLib* for the **Name** and *GettingStarted* for the **Solution name**.</span></span>

   4. <span data-ttu-id="65712-130">选择“确定”。</span><span class="sxs-lookup"><span data-stu-id="65712-130">Select **OK**.</span></span>

      <span data-ttu-id="65712-131">Visual Studio 将创建一个项目，该项目具有三个文件： *IService1.cs* （或 Visual Basic 项目的*IService1* ）、 *Service1.cs* （或 Visual Basic 项目的*Service1* ）和*App.config*。Visual Studio 会按如下所示定义这些文件：</span><span class="sxs-lookup"><span data-stu-id="65712-131">Visual Studio creates the project, which has three files: *IService1.cs* (or *IService1.vb* for a Visual Basic project), *Service1.cs* (or *Service1.vb* for a Visual Basic project), and *App.config*. Visual Studio defines these files as follows:</span></span>
      - <span data-ttu-id="65712-132">*IService1*文件包含服务协定的默认定义。</span><span class="sxs-lookup"><span data-stu-id="65712-132">The *IService1* file contains the default definition of the service contract.</span></span>
      - <span data-ttu-id="65712-133">*Service1*文件包含服务协定的默认实现。</span><span class="sxs-lookup"><span data-stu-id="65712-133">The *Service1* file contains the default implementation of the service contract.</span></span>
      - <span data-ttu-id="65712-134">*App.config*文件包含用 VISUAL Studio WCF 服务主机工具加载默认服务所需的配置信息。</span><span class="sxs-lookup"><span data-stu-id="65712-134">The *App.config* file contains the configuration info needed to load the default service with the Visual Studio WCF Service Host tool.</span></span> <span data-ttu-id="65712-135">有关 WCF 服务主机工具的详细信息，请参阅[Wcf 服务主机（WcfSvcHost.exe）](wcf-service-host-wcfsvchost-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="65712-135">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span></span>

      > [!NOTE]
      > <span data-ttu-id="65712-136">如果安装了包含 Visual Basic 开发人员环境设置的 Visual Studio，则可能会隐藏解决方案。</span><span class="sxs-lookup"><span data-stu-id="65712-136">If you installed Visual Studio with Visual Basic developer environment settings, the solution might be hidden.</span></span> <span data-ttu-id="65712-137">如果是这种情况，请从 "**工具**" 菜单中选择 "**选项**"，然后在 "选项" 窗口中选择 "常规**项目和解决方案**  >  **General** "。 **Options**</span><span class="sxs-lookup"><span data-stu-id="65712-137">If this is the case, select **Options** from the **Tools** menu, then select **Projects and Solutions** > **General** in the **Options** window.</span></span> <span data-ttu-id="65712-138">选择 "**始终显示解决方案**"。</span><span class="sxs-lookup"><span data-stu-id="65712-138">Select **Always show solution**.</span></span> <span data-ttu-id="65712-139">同时，验证是否选择了 "**创建时保存新项目**"。</span><span class="sxs-lookup"><span data-stu-id="65712-139">Also, verify that **Save new projects when created** is selected.</span></span>

3. <span data-ttu-id="65712-140">在**解决方案资源管理器**中，打开**IService1.cs**或**IService1**文件，并将其代码替换为以下代码：</span><span class="sxs-lookup"><span data-stu-id="65712-140">From **Solution Explorer**, open the **IService1.cs** or **IService1.vb** file, and replace its code with the following code:</span></span>

    ```csharp
    using System;
    using System.ServiceModel;

    namespace GettingStartedLib
    {
            [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
            public interface ICalculator
            {
                [OperationContract]
                double Add(double n1, double n2);
                [OperationContract]
                double Subtract(double n1, double n2);
                [OperationContract]
                double Multiply(double n1, double n2);
                [OperationContract]
                double Divide(double n1, double n2);
            }
    }
    ```

    ```vb
    Imports System.ServiceModel

    Namespace GettingStartedLib

        <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
        Public Interface ICalculator

            <OperationContract()> _
            Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
        End Interface
    End Namespace
    ```

     <span data-ttu-id="65712-141">本协定定义了一个在线计算器。</span><span class="sxs-lookup"><span data-stu-id="65712-141">This contract defines an online calculator.</span></span> <span data-ttu-id="65712-142">请注意， `ICalculator` 接口用特性标记 <xref:System.ServiceModel.ServiceContractAttribute> （简化为 `ServiceContract` ）。</span><span class="sxs-lookup"><span data-stu-id="65712-142">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute (simplified as `ServiceContract`).</span></span> <span data-ttu-id="65712-143">此属性定义一个命名空间以消除协定名称的歧义。</span><span class="sxs-lookup"><span data-stu-id="65712-143">This attribute defines a namespace to disambiguate the contract name.</span></span> <span data-ttu-id="65712-144">此代码用属性标记每个计算器操作 <xref:System.ServiceModel.OperationContractAttribute> （简化为 `OperationContract` ）。</span><span class="sxs-lookup"><span data-stu-id="65712-144">The code marks each calculator operation with the <xref:System.ServiceModel.OperationContractAttribute> attribute (simplified as `OperationContract`).</span></span>

## <a name="next-steps"></a><span data-ttu-id="65712-145">后续步骤</span><span class="sxs-lookup"><span data-stu-id="65712-145">Next steps</span></span>

<span data-ttu-id="65712-146">在本教程中，你将了解：</span><span class="sxs-lookup"><span data-stu-id="65712-146">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="65712-147">创建一个 WCF 服务库项目。</span><span class="sxs-lookup"><span data-stu-id="65712-147">Create a WCF Service Library project.</span></span>
> - <span data-ttu-id="65712-148">定义服务协定接口。</span><span class="sxs-lookup"><span data-stu-id="65712-148">Define a service contract interface.</span></span>

<span data-ttu-id="65712-149">转到下一教程，了解如何实现 WCF 服务协定。</span><span class="sxs-lookup"><span data-stu-id="65712-149">Advance to the next tutorial to learn how to implement the WCF service contract.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="65712-150">教程：实现 WCF 服务协定</span><span class="sxs-lookup"><span data-stu-id="65712-150">Tutorial: Implement a WCF service contract</span></span>](how-to-implement-a-wcf-contract.md)

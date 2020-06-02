---
title: 教程：承载和运行基本 Windows Communication Foundation 服务
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 872844487578843492e05dd2abb87b50e0bec91c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291391"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="a78ec-102">教程：承载和运行基本 Windows Communication Foundation 服务</span><span class="sxs-lookup"><span data-stu-id="a78ec-102">Tutorial: Host and run a basic Windows Communication Foundation service</span></span>

<span data-ttu-id="a78ec-103">本教程介绍创建基本 Windows Communication Foundation （WCF）应用程序所需的五个任务中的第三个。</span><span class="sxs-lookup"><span data-stu-id="a78ec-103">This tutorial describes the third of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="a78ec-104">有关教程的概述，请参阅[教程： Windows Communication Foundation 应用程序入门](getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="a78ec-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="a78ec-105">用于创建 WCF 应用程序的下一个任务是在控制台应用程序中托管 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="a78ec-105">The next task for creating a WCF application is to host a WCF service in a console application.</span></span> <span data-ttu-id="a78ec-106">WCF 服务公开一个或多个*终结点*，每个终结点都公开一个或多个服务操作。</span><span class="sxs-lookup"><span data-stu-id="a78ec-106">A WCF service exposes one or more *endpoints*, each of which exposes one or more service operations.</span></span> <span data-ttu-id="a78ec-107">服务终结点指定下列信息：</span><span class="sxs-lookup"><span data-stu-id="a78ec-107">A service endpoint specifies the following information:</span></span>

- <span data-ttu-id="a78ec-108">可在其中找到服务的地址。</span><span class="sxs-lookup"><span data-stu-id="a78ec-108">An address where you can find the service.</span></span>
- <span data-ttu-id="a78ec-109">一个包含描述客户端如何与服务进行通信的信息的绑定。</span><span class="sxs-lookup"><span data-stu-id="a78ec-109">A binding that contains the information that describes how a client must communicate with the service.</span></span>
- <span data-ttu-id="a78ec-110">定义服务向其客户端提供的功能的协定。</span><span class="sxs-lookup"><span data-stu-id="a78ec-110">A contract that defines the functionality that the service provides to its clients.</span></span>

<span data-ttu-id="a78ec-111">在本教程中，了解如何：</span><span class="sxs-lookup"><span data-stu-id="a78ec-111">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="a78ec-112">创建和配置用于承载 WCF 服务的控制台应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="a78ec-112">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="a78ec-113">添加代码以承载 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="a78ec-113">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="a78ec-114">更新配置文件。</span><span class="sxs-lookup"><span data-stu-id="a78ec-114">Update the configuration file.</span></span>
> - <span data-ttu-id="a78ec-115">启动 WCF 服务并验证它是否正在运行。</span><span class="sxs-lookup"><span data-stu-id="a78ec-115">Start the WCF service and verify it's running.</span></span>

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a><span data-ttu-id="a78ec-116">创建和配置用于托管服务的控制台应用程序项目</span><span class="sxs-lookup"><span data-stu-id="a78ec-116">Create and configure a console app project for hosting the service</span></span>

1. <span data-ttu-id="a78ec-117">在 Visual Studio 中创建控制台应用项目：</span><span class="sxs-lookup"><span data-stu-id="a78ec-117">Create a console app project in Visual Studio:</span></span>

    1. <span data-ttu-id="a78ec-118">从 "**文件**" 菜单中，选择 "**打开**  >  **项目/解决方案**"，并浏览到前面创建的**GettingStarted**解决方案（*GettingStarted*）。</span><span class="sxs-lookup"><span data-stu-id="a78ec-118">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="a78ec-119">选择“打开”。</span><span class="sxs-lookup"><span data-stu-id="a78ec-119">Select **Open**.</span></span>

    2. <span data-ttu-id="a78ec-120">从 "**视图**" 菜单中选择 "**解决方案资源管理器**"。</span><span class="sxs-lookup"><span data-stu-id="a78ec-120">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="a78ec-121">在 "**解决方案资源管理器**" 窗口中，选择 " **GettingStarted** " 解决方案（顶级节点），然后从快捷菜单中选择 "**添加**  >  **新项目**"。</span><span class="sxs-lookup"><span data-stu-id="a78ec-121">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span>

    4. <span data-ttu-id="a78ec-122">在 "**添加新项目**" 窗口的左侧，选择 " **Visual c #** " 或 " **Visual Basic**下的" **Windows 桌面**"类别。</span><span class="sxs-lookup"><span data-stu-id="a78ec-122">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span>

    5. <span data-ttu-id="a78ec-123">选择 "**控制台应用（.NET Framework）** " 模板，然后输入 " *GettingStartedHost* " 作为 "**名称**"。</span><span class="sxs-lookup"><span data-stu-id="a78ec-123">Select the **Console App (.NET Framework)** template, and enter *GettingStartedHost* for the **Name**.</span></span> <span data-ttu-id="a78ec-124">选择“确定”。</span><span class="sxs-lookup"><span data-stu-id="a78ec-124">Select **OK**.</span></span>

2. <span data-ttu-id="a78ec-125">将**GettingStartedHost**项目中的引用添加到**GettingStartedLib**项目：</span><span class="sxs-lookup"><span data-stu-id="a78ec-125">Add a reference in the **GettingStartedHost** project to the **GettingStartedLib** project:</span></span>

    1. <span data-ttu-id="a78ec-126">在 "**解决方案资源管理器**" 窗口中，选择 " **GettingStartedHost** " 项目下的 "**引用**" 文件夹，然后从快捷菜单中选择 "**添加引用**"。</span><span class="sxs-lookup"><span data-stu-id="a78ec-126">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="a78ec-127">在 "**添加引用**" 对话框中窗口左侧的 "**项目**" 下，选择 "**解决方案**"。</span><span class="sxs-lookup"><span data-stu-id="a78ec-127">In the **Add Reference** dialog, under **Projects** on the left side of the window, select **Solution**.</span></span>

    3. <span data-ttu-id="a78ec-128">在窗口的中间部分中选择 " **GettingStartedLib** "，然后选择 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="a78ec-128">Select **GettingStartedLib** in the center section of the window, and then select **OK**.</span></span>

       <span data-ttu-id="a78ec-129">此操作可使**GettingStartedLib**项目中定义的类型可用于**GettingStartedHost**项目。</span><span class="sxs-lookup"><span data-stu-id="a78ec-129">This action makes the types defined in the **GettingStartedLib** project available to the **GettingStartedHost** project.</span></span>

3. <span data-ttu-id="a78ec-130">将**GettingStartedHost**项目中的引用添加到 <xref:System.ServiceModel> 程序集：</span><span class="sxs-lookup"><span data-stu-id="a78ec-130">Add a reference in the **GettingStartedHost** project to the <xref:System.ServiceModel> assembly:</span></span>

    1. <span data-ttu-id="a78ec-131">在 "**解决方案资源管理器**" 窗口中，选择 " **GettingStartedHost** " 项目下的 "**引用**" 文件夹，然后从快捷菜单中选择 "**添加引用**"。</span><span class="sxs-lookup"><span data-stu-id="a78ec-131">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="a78ec-132">在 "**添加引用**" 窗口中窗口左侧的 "**程序集**" 下，选择 "**框架**"。</span><span class="sxs-lookup"><span data-stu-id="a78ec-132">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>

    3. <span data-ttu-id="a78ec-133">选择 " **system.servicemodel**"，然后选择 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="a78ec-133">Select **System.ServiceModel**, and then select **OK**.</span></span>

    4. <span data-ttu-id="a78ec-134">通过选择 "**文件**" "  >  **全部保存**" 保存解决方案。</span><span class="sxs-lookup"><span data-stu-id="a78ec-134">Save the solution by selecting **File** > **Save All**.</span></span>

## <a name="add-code-to-host-the-service"></a><span data-ttu-id="a78ec-135">添加用于托管服务的代码</span><span class="sxs-lookup"><span data-stu-id="a78ec-135">Add code to host the service</span></span>

<span data-ttu-id="a78ec-136">若要承载服务，请添加代码以执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="a78ec-136">To host the service, you add code to do the following steps:</span></span>

1. <span data-ttu-id="a78ec-137">创建基址的 URI。</span><span class="sxs-lookup"><span data-stu-id="a78ec-137">Create a URI for the base address.</span></span>
2. <span data-ttu-id="a78ec-138">创建用于承载服务的类实例。</span><span class="sxs-lookup"><span data-stu-id="a78ec-138">Create a class instance for hosting the service.</span></span>
3. <span data-ttu-id="a78ec-139">创建服务终结点。</span><span class="sxs-lookup"><span data-stu-id="a78ec-139">Create a service endpoint.</span></span>
4. <span data-ttu-id="a78ec-140">启用元数据交换。</span><span class="sxs-lookup"><span data-stu-id="a78ec-140">Enable metadata exchange.</span></span>
5. <span data-ttu-id="a78ec-141">打开服务主机以侦听传入消息。</span><span class="sxs-lookup"><span data-stu-id="a78ec-141">Open the service host to listen for incoming messages.</span></span>
  
<span data-ttu-id="a78ec-142">对代码进行以下更改：</span><span class="sxs-lookup"><span data-stu-id="a78ec-142">Make the following changes to the code:</span></span>

1. <span data-ttu-id="a78ec-143">在**GettingStartedHost**项目中打开**Program.cs**或**Module1**文件，并将其代码替换为以下代码：</span><span class="sxs-lookup"><span data-stu-id="a78ec-143">Open the **Program.cs** or **Module1.vb** file in the **GettingStartedHost** project and replace its code with the following code:</span></span>

    ```csharp
    using System;
    using System.ServiceModel;
    using System.ServiceModel.Description;
    using GettingStartedLib;

    namespace GettingStartedHost
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Step 1: Create a URI to serve as the base address.
                Uri baseAddress = new Uri("http://localhost:8000/GettingStarted/");

                // Step 2: Create a ServiceHost instance.
                ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);

                try
                {
                    // Step 3: Add a service endpoint.
                    selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");

                    // Step 4: Enable metadata exchange.
                    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
                    smb.HttpGetEnabled = true;
                    selfHost.Description.Behaviors.Add(smb);

                    // Step 5: Start the service.
                    selfHost.Open();
                    Console.WriteLine("The service is ready.");

                    // Close the ServiceHost to stop the service.
                    Console.WriteLine("Press <Enter> to terminate the service.");
                    Console.WriteLine();
                    Console.ReadLine();
                    selfHost.Close();
                }
                catch (CommunicationException ce)
                {
                    Console.WriteLine("An exception occurred: {0}", ce.Message);
                    selfHost.Abort();
                }
            }
        }
    }
    ```

    ```vb
    Imports System.ServiceModel
    Imports System.ServiceModel.Description
    Imports GettingStartedLib.GettingStartedLib

    Module Service

        Class Program
            Shared Sub Main()
                ' Step 1: Create a URI to serve as the base address.
                Dim baseAddress As New Uri("http://localhost:8000/GettingStarted/")

                ' Step 2: Create a ServiceHost instance.
                Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)
               Try

                    ' Step 3: Add a service endpoint.
                    selfHost.AddServiceEndpoint( _
                        GetType(ICalculator), _
                        New WSHttpBinding(), _
                        "CalculatorService")

                    ' Step 4: Enable metadata exchange.
                    Dim smb As New ServiceMetadataBehavior()
                    smb.HttpGetEnabled = True
                    selfHost.Description.Behaviors.Add(smb)

                    ' Step 5: Start the service.
                    selfHost.Open()
                    Console.WriteLine("The service is ready.")

                    ' Close the ServiceHost to stop the service.
                    Console.WriteLine("Press <Enter> to terminate the service.")
                    Console.WriteLine()
                    Console.ReadLine()
                    selfHost.Close()

                Catch ce As CommunicationException
                    Console.WriteLine("An exception occurred: {0}", ce.Message)
                    selfHost.Abort()
                End Try
            End Sub
        End Class

    End Module
    ```

    <span data-ttu-id="a78ec-144">有关此代码的工作原理的信息，请参阅[服务托管程序步骤](#service-hosting-program-steps)。</span><span class="sxs-lookup"><span data-stu-id="a78ec-144">For information about how this code works, see [Service hosting program steps](#service-hosting-program-steps).</span></span>

2. <span data-ttu-id="a78ec-145">更新项目属性：</span><span class="sxs-lookup"><span data-stu-id="a78ec-145">Update the project properties:</span></span>

   1. <span data-ttu-id="a78ec-146">在 "**解决方案资源管理器**" 窗口中，选择 " **GettingStartedHost** " 文件夹，然后从快捷菜单中选择 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="a78ec-146">In the **Solution Explorer** window, select the **GettingStartedHost** folder, and then select **Properties** from the shortcut menu.</span></span>

   2. <span data-ttu-id="a78ec-147">在**GettingStartedHost**属性页上，选择 "**应用程序**" 选项卡：</span><span class="sxs-lookup"><span data-stu-id="a78ec-147">On the **GettingStartedHost** properties page, select the **Application** tab:</span></span>

      - <span data-ttu-id="a78ec-148">对于 c # 项目，请从 "**启动对象**" 列表中选择 " **GettingStartedHost** "。</span><span class="sxs-lookup"><span data-stu-id="a78ec-148">For C# projects, select **GettingStartedHost.Program** from the **Startup object** list.</span></span>

      - <span data-ttu-id="a78ec-149">对于 Visual Basic 项目，从 "**启动对象**" 列表中选择 "**服务**"。</span><span class="sxs-lookup"><span data-stu-id="a78ec-149">For Visual Basic projects, select **Service.Program** from the **Startup object** list.</span></span>

   3. <span data-ttu-id="a78ec-150">从 "**文件**" 菜单中，选择 "**全部保存**"。</span><span class="sxs-lookup"><span data-stu-id="a78ec-150">From the **File** menu, select **Save All**.</span></span>

## <a name="verify-the-service-is-working"></a><span data-ttu-id="a78ec-151">验证服务是否正常运行</span><span class="sxs-lookup"><span data-stu-id="a78ec-151">Verify the service is working</span></span>

1. <span data-ttu-id="a78ec-152">生成解决方案，然后从 Visual Studio 内部运行**GettingStartedHost**控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="a78ec-152">Build the solution, and then run the **GettingStartedHost** console application from inside Visual Studio.</span></span>

    <span data-ttu-id="a78ec-153">必须以管理员权限运行该服务。</span><span class="sxs-lookup"><span data-stu-id="a78ec-153">The service must be run with administrator privileges.</span></span> <span data-ttu-id="a78ec-154">由于你以管理员权限打开了 Visual Studio，因此，当你在 Visual Studio 中运行**GettingStartedHost**时，该应用程序也会以管理员权限运行。</span><span class="sxs-lookup"><span data-stu-id="a78ec-154">Because you opened Visual Studio with administrator privileges, when you run **GettingStartedHost** in Visual Studio, the application is run with administrator privileges as well.</span></span> <span data-ttu-id="a78ec-155">作为替代方法，您可以以管理员身份打开新的命令提示符（从快捷菜单中选择 "**更多**以  >  **管理员身份运行**"），并在其中运行**GettingStartedHost** 。</span><span class="sxs-lookup"><span data-stu-id="a78ec-155">As an alternative, you can open a new command prompt as an administrator (select **More** > **Run as administrator** from the shortcut menu) and run **GettingStartedHost.exe** within it.</span></span>

2. <span data-ttu-id="a78ec-156">打开 web 浏览器并浏览到中的服务页面 `http://localhost:8000/GettingStarted/CalculatorService` 。</span><span class="sxs-lookup"><span data-stu-id="a78ec-156">Open a web browser and browse to the service's page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

   > [!NOTE]
   > <span data-ttu-id="a78ec-157">此类服务需要适当的权限才能在计算机上注册 HTTP 地址以进行侦听。</span><span class="sxs-lookup"><span data-stu-id="a78ec-157">Services such as this one require the proper permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="a78ec-158">管理员帐户具有此权限，但对于非管理员帐户来说，必须授予对 HTTP 命名空间的权限。</span><span class="sxs-lookup"><span data-stu-id="a78ec-158">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> <span data-ttu-id="a78ec-159">有关如何配置命名空间预留的详细信息，请参阅[配置 HTTP 和 HTTPS](feature-details/configuring-http-and-https.md)。</span><span class="sxs-lookup"><span data-stu-id="a78ec-159">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](feature-details/configuring-http-and-https.md).</span></span>

## <a name="service-hosting-program-steps"></a><span data-ttu-id="a78ec-160">服务托管计划步骤</span><span class="sxs-lookup"><span data-stu-id="a78ec-160">Service hosting program steps</span></span>

<span data-ttu-id="a78ec-161">你添加用于承载服务的代码中的步骤如下所述：</span><span class="sxs-lookup"><span data-stu-id="a78ec-161">The steps in the code you added to host the service are described as follows:</span></span>

- <span data-ttu-id="a78ec-162">**步骤 1**：创建类的实例 `Uri` 以承载服务的基址。</span><span class="sxs-lookup"><span data-stu-id="a78ec-162">**Step 1**: Create an instance of the `Uri` class to hold the base address of the service.</span></span> <span data-ttu-id="a78ec-163">包含基址的 URL 具有标识服务的可选 URI。</span><span class="sxs-lookup"><span data-stu-id="a78ec-163">A URL that contains a base address has an optional URI that identifies a service.</span></span> <span data-ttu-id="a78ec-164">基址的格式如下所示： `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>` 。</span><span class="sxs-lookup"><span data-stu-id="a78ec-164">The base address is formatted as follows: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`.</span></span> <span data-ttu-id="a78ec-165">计算器服务的基址使用 HTTP 传输、localhost、端口8000和 URI 段 GettingStarted。</span><span class="sxs-lookup"><span data-stu-id="a78ec-165">The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment, GettingStarted.</span></span>

- <span data-ttu-id="a78ec-166">**步骤 2**：创建用于 <xref:System.ServiceModel.ServiceHost> 承载服务的类的实例。</span><span class="sxs-lookup"><span data-stu-id="a78ec-166">**Step 2**: Create an instance of the <xref:System.ServiceModel.ServiceHost> class, which you use to host the service.</span></span> <span data-ttu-id="a78ec-167">构造函数采用两个参数：实现服务协定的类的类型和服务的基址。</span><span class="sxs-lookup"><span data-stu-id="a78ec-167">The constructor takes two parameters: the type of the class that implements the service contract and the base address of the service.</span></span>

- <span data-ttu-id="a78ec-168">**步骤 3**：创建 <xref:System.ServiceModel.Description.ServiceEndpoint> 实例。</span><span class="sxs-lookup"><span data-stu-id="a78ec-168">**Step 3**: Create a <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span></span> <span data-ttu-id="a78ec-169">服务终结点由地址、绑定和服务协定组成。</span><span class="sxs-lookup"><span data-stu-id="a78ec-169">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="a78ec-170"><xref:System.ServiceModel.Description.ServiceEndpoint>构造函数由服务协定接口类型、绑定和地址组成。</span><span class="sxs-lookup"><span data-stu-id="a78ec-170">The <xref:System.ServiceModel.Description.ServiceEndpoint> constructor is composed of the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="a78ec-171">服务协定是在服务类型中定义和实现的 `ICalculator`。</span><span class="sxs-lookup"><span data-stu-id="a78ec-171">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="a78ec-172">此示例的绑定为 <xref:System.ServiceModel.WSHttpBinding> ，它是内置绑定并连接到符合 WS-\* 规范的终结点。</span><span class="sxs-lookup"><span data-stu-id="a78ec-172">The binding for this sample is <xref:System.ServiceModel.WSHttpBinding>, which is a built-in binding and connects to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="a78ec-173">有关 WCF 绑定的详细信息，请参阅[wcf 绑定概述](bindings-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="a78ec-173">For more information about WCF bindings, see [WCF bindings overview](bindings-overview.md).</span></span> <span data-ttu-id="a78ec-174">将地址追加到基址以标识终结点。</span><span class="sxs-lookup"><span data-stu-id="a78ec-174">You append the address to the base address to identify the endpoint.</span></span> <span data-ttu-id="a78ec-175">该代码将地址指定为 CalculatorService，将终结点的完全限定地址指定为 `http://localhost:8000/GettingStarted/CalculatorService` 。</span><span class="sxs-lookup"><span data-stu-id="a78ec-175">The code specifies the address as CalculatorService and the fully qualified address for the endpoint as `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="a78ec-176">对于 .NET Framework 版本4及更高版本，添加服务终结点是可选的。</span><span class="sxs-lookup"><span data-stu-id="a78ec-176">For .NET Framework Version 4 and later, adding a service endpoint is optional.</span></span> <span data-ttu-id="a78ec-177">对于这些版本，如果不添加代码或配置，WCF 将为服务实现的每个基址和协定组合添加一个默认终结点。</span><span class="sxs-lookup"><span data-stu-id="a78ec-177">For these versions, if you don't add your code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="a78ec-178">有关默认终结点的详细信息，请参阅[指定终结点地址](specifying-an-endpoint-address.md)。</span><span class="sxs-lookup"><span data-stu-id="a78ec-178">For more information about default endpoints, see [Specifying an endpoint address](specifying-an-endpoint-address.md).</span></span> <span data-ttu-id="a78ec-179">有关默认终结点、绑定和行为的详细信息，请参阅[WCF 服务的](samples/simplified-configuration-for-wcf-services.md)[简化配置](simplified-configuration.md)和简化配置。</span><span class="sxs-lookup"><span data-stu-id="a78ec-179">For more information about default endpoints, bindings, and behaviors, see [Simplified configuration](simplified-configuration.md) and [Simplified configuration for WCF services](samples/simplified-configuration-for-wcf-services.md).</span></span>

- <span data-ttu-id="a78ec-180">**步骤 4**：启用元数据交换。</span><span class="sxs-lookup"><span data-stu-id="a78ec-180">**Step 4**: Enable metadata exchange.</span></span> <span data-ttu-id="a78ec-181">客户端使用元数据交换生成代理来调用服务操作。</span><span class="sxs-lookup"><span data-stu-id="a78ec-181">Clients use metadata exchange to generate proxies for calling the service operations.</span></span> <span data-ttu-id="a78ec-182">若要启用元数据交换，请创建一个 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 实例，将其 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> 属性设置为 `true` ，然后将该 `ServiceMetadataBehavior` 对象添加到实例的集合中 <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> <xref:System.ServiceModel.ServiceHost> 。</span><span class="sxs-lookup"><span data-stu-id="a78ec-182">To enable metadata exchange, create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set its <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> property to `true`, and add the `ServiceMetadataBehavior` object to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>

- <span data-ttu-id="a78ec-183">**步骤 5**：打开 <xref:System.ServiceModel.ServiceHost> 以侦听传入的消息。</span><span class="sxs-lookup"><span data-stu-id="a78ec-183">**Step 5**: Open <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="a78ec-184">应用程序等待你按**enter**。</span><span class="sxs-lookup"><span data-stu-id="a78ec-184">The application waits for you to press **Enter**.</span></span> <span data-ttu-id="a78ec-185">在应用程序实例化后 <xref:System.ServiceModel.ServiceHost> ，它将执行 try/catch 块。</span><span class="sxs-lookup"><span data-stu-id="a78ec-185">After the application instantiates <xref:System.ServiceModel.ServiceHost>, it executes a try/catch block.</span></span> <span data-ttu-id="a78ec-186">有关安全捕获引发的异常的详细信息 <xref:System.ServiceModel.ServiceHost> ，请参阅[使用 Close 和 ABORT 释放 WCF 客户端资源](samples/use-close-abort-release-wcf-client-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="a78ec-186">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Use Close and Abort to release WCF client resources](samples/use-close-abort-release-wcf-client-resources.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a78ec-187">添加 WCF 服务库时，如果你通过启动服务主机进行调试，则 Visual Studio 会为你托管它。</span><span class="sxs-lookup"><span data-stu-id="a78ec-187">When you add a WCF service library, Visual Studio hosts it for you if you debug it by starting a service host.</span></span> <span data-ttu-id="a78ec-188">若要避免冲突，可以阻止 Visual Studio 承载 WCF 服务库。</span><span class="sxs-lookup"><span data-stu-id="a78ec-188">To avoid conflicts, you can prevent Visual Studio from hosting the WCF service library.</span></span>
>
> 1. <span data-ttu-id="a78ec-189">在**解决方案资源管理器**中选择 " **GettingStartedLib** " 项目，然后从快捷菜单中选择 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="a78ec-189">Select the **GettingStartedLib** project in **Solution Explorer** and choose **Properties** from the shortcut menu.</span></span>
> 2. <span data-ttu-id="a78ec-190">选择 " **Wcf 选项**" 并取消选中 **"在调试同一解决方案中的另一个项目时启动 WCF 服务主机"**。</span><span class="sxs-lookup"><span data-stu-id="a78ec-190">Select **WCF Options** and uncheck **Start WCF Service Host when debugging another project in the same solution**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a78ec-191">后续步骤</span><span class="sxs-lookup"><span data-stu-id="a78ec-191">Next steps</span></span>

<span data-ttu-id="a78ec-192">在本教程中，你了解了如何执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="a78ec-192">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="a78ec-193">创建和配置用于承载 WCF 服务的控制台应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="a78ec-193">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="a78ec-194">添加代码以承载 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="a78ec-194">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="a78ec-195">更新配置文件。</span><span class="sxs-lookup"><span data-stu-id="a78ec-195">Update the configuration file.</span></span>
> - <span data-ttu-id="a78ec-196">启动 WCF 服务并验证它是否正在运行。</span><span class="sxs-lookup"><span data-stu-id="a78ec-196">Start the WCF service and verify it's running.</span></span>

<span data-ttu-id="a78ec-197">转到下一教程，了解如何创建 WCF 客户端。</span><span class="sxs-lookup"><span data-stu-id="a78ec-197">Advance to the next tutorial to learn how to create a WCF client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a78ec-198">教程：创建 WCF 客户端</span><span class="sxs-lookup"><span data-stu-id="a78ec-198">Tutorial: Create a WCF client</span></span>](how-to-create-a-wcf-client.md)

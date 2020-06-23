---
title: 教程：创建 Windows Communication Foundation 客户端
description: 了解如何通过从 WCF 服务中检索元数据来创建客户端，这是一系列文章中的一部分，可帮助你开始创建 WCF 应用程序。
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: d5a2a2b5175c9e34eaf1dbaff20ac57f34117c4e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246319"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a><span data-ttu-id="e2175-103">教程：创建 Windows Communication Foundation 客户端</span><span class="sxs-lookup"><span data-stu-id="e2175-103">Tutorial: Create a Windows Communication Foundation client</span></span>

<span data-ttu-id="e2175-104">本教程介绍创建基本 Windows Communication Foundation （WCF）应用程序所需的五个任务中的第四个。</span><span class="sxs-lookup"><span data-stu-id="e2175-104">This tutorial describes the fourth of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="e2175-105">有关教程的概述，请参阅[教程： Windows Communication Foundation 应用程序入门](getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="e2175-105">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="e2175-106">用于创建 WCF 应用程序的下一个任务是通过从 WCF 服务中检索元数据来创建客户端。</span><span class="sxs-lookup"><span data-stu-id="e2175-106">The next task for creating a WCF application is to create a client by retrieving metadata from a WCF service.</span></span> <span data-ttu-id="e2175-107">使用 Visual Studio 添加服务引用，后者从服务的 MEX 终结点中获取元数据。</span><span class="sxs-lookup"><span data-stu-id="e2175-107">You use Visual Studio to add a service reference, which gets the metadata from the service’s MEX endpoint.</span></span> <span data-ttu-id="e2175-108">然后，Visual Studio 将使用你选择的语言生成客户端代理的托管源代码文件。</span><span class="sxs-lookup"><span data-stu-id="e2175-108">Visual Studio then generates a managed source code file for a client proxy in the language you've chosen.</span></span> <span data-ttu-id="e2175-109">它还会创建一个客户端配置文件（*App.config*）。</span><span class="sxs-lookup"><span data-stu-id="e2175-109">It also creates a client configuration file (*App.config*).</span></span> <span data-ttu-id="e2175-110">此文件使客户端应用程序能够连接到终结点上的服务。</span><span class="sxs-lookup"><span data-stu-id="e2175-110">This file enables the client application to connect to the service at an endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="e2175-111">如果从 Visual Studio 中的类库项目调用 WCF 服务，请使用**添加服务引用**功能自动生成代理和关联的配置文件。</span><span class="sxs-lookup"><span data-stu-id="e2175-111">If you call a WCF service from a class library project in Visual Studio, use the **Add Service Reference** feature to automatically generate a proxy and associated configuration file.</span></span> <span data-ttu-id="e2175-112">但是，由于类库项目不使用此配置文件，因此需要将生成的配置文件中的设置添加到调用类库的可执行文件的*App.config*文件中。</span><span class="sxs-lookup"><span data-stu-id="e2175-112">However, because class library projects don't use this configuration file, you need to add the settings in the generated configuration file to the *App.config* file for the executable that calls the class library.</span></span>

> [!NOTE]
> <span data-ttu-id="e2175-113">作为替代方法，请使用 "配置[元数据" 实用工具](#servicemodel-metadata-utility-tool)（而不是 Visual Studio）生成代理类和配置文件。</span><span class="sxs-lookup"><span data-stu-id="e2175-113">As an alternative, use the [ServiceModel Metadata Utility tool](#servicemodel-metadata-utility-tool) instead of Visual Studio to generate the proxy class and configuration file.</span></span>

<span data-ttu-id="e2175-114">客户端应用程序使用生成的代理类与服务通信。</span><span class="sxs-lookup"><span data-stu-id="e2175-114">The client application uses the generated proxy class to communicate with the service.</span></span> <span data-ttu-id="e2175-115">[教程：使用客户端](how-to-use-a-wcf-client.md)中介绍了此过程。</span><span class="sxs-lookup"><span data-stu-id="e2175-115">This procedure is described in [Tutorial: Use a client](how-to-use-a-wcf-client.md).</span></span>

<span data-ttu-id="e2175-116">在本教程中，你将了解如何执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="e2175-116">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="e2175-117">创建并配置 WCF 客户端的控制台应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="e2175-117">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="e2175-118">将服务引用添加到 WCF 服务，以生成代理类和配置文件。</span><span class="sxs-lookup"><span data-stu-id="e2175-118">Add a service reference to the WCF service to generate the proxy class and configuration files.</span></span>

## <a name="create-a-windows-communication-foundation-client"></a><span data-ttu-id="e2175-119">创建 Windows Communication Foundation 客户端</span><span class="sxs-lookup"><span data-stu-id="e2175-119">Create a Windows Communication Foundation client</span></span>

1. <span data-ttu-id="e2175-120">在 Visual Studio 中创建控制台应用项目：</span><span class="sxs-lookup"><span data-stu-id="e2175-120">Create a console app project in Visual Studio:</span></span>

    1. <span data-ttu-id="e2175-121">从 "**文件**" 菜单中，选择 "**打开**  >  **项目/解决方案**"，并浏览到前面创建的**GettingStarted**解决方案（*GettingStarted*）。</span><span class="sxs-lookup"><span data-stu-id="e2175-121">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="e2175-122">选择“打开”。</span><span class="sxs-lookup"><span data-stu-id="e2175-122">Select **Open**.</span></span>

    2. <span data-ttu-id="e2175-123">从 "**视图**" 菜单中选择 "**解决方案资源管理器**"。</span><span class="sxs-lookup"><span data-stu-id="e2175-123">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="e2175-124">在 "**解决方案资源管理器**" 窗口中，选择 " **GettingStarted** " 解决方案（顶级节点），然后从快捷菜单中选择 "**添加**  >  **新项目**"。</span><span class="sxs-lookup"><span data-stu-id="e2175-124">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span>

    4. <span data-ttu-id="e2175-125">在 "**添加新项目**" 窗口的左侧，选择 " **Visual c #** " 或 " **Visual Basic**下的" **Windows 桌面**"类别。</span><span class="sxs-lookup"><span data-stu-id="e2175-125">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span>

    5. <span data-ttu-id="e2175-126">选择 "**控制台应用（.NET Framework）** " 模板，然后输入 " *GettingStartedClient* " 作为 "**名称**"。</span><span class="sxs-lookup"><span data-stu-id="e2175-126">Select the **Console App (.NET Framework)** template, and enter *GettingStartedClient* for the **Name**.</span></span> <span data-ttu-id="e2175-127">选择“确定”。</span><span class="sxs-lookup"><span data-stu-id="e2175-127">Select **OK**.</span></span>

2. <span data-ttu-id="e2175-128">将**GettingStartedClient**项目中的引用添加到 <xref:System.ServiceModel> 程序集：</span><span class="sxs-lookup"><span data-stu-id="e2175-128">Add a reference in the **GettingStartedClient** project to the <xref:System.ServiceModel> assembly:</span></span>

    1. <span data-ttu-id="e2175-129">在 "**解决方案资源管理器**" 窗口中，选择 " **GettingStartedClient** " 项目下的 "**引用**" 文件夹，然后从快捷菜单中选择 "**添加引用**"。</span><span class="sxs-lookup"><span data-stu-id="e2175-129">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="e2175-130">在 "**添加引用**" 窗口中窗口左侧的 "**程序集**" 下，选择 "**框架**"。</span><span class="sxs-lookup"><span data-stu-id="e2175-130">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>

    3. <span data-ttu-id="e2175-131">找到并选择 " **system.servicemodel**"，然后选择 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="e2175-131">Find and select **System.ServiceModel**, and then choose **OK**.</span></span>

    4. <span data-ttu-id="e2175-132">通过选择 "**文件**" "  >  **全部保存**" 保存解决方案。</span><span class="sxs-lookup"><span data-stu-id="e2175-132">Save the solution by selecting **File** > **Save All**.</span></span>

3. <span data-ttu-id="e2175-133">将服务引用添加到计算器服务：</span><span class="sxs-lookup"><span data-stu-id="e2175-133">Add a service reference to the calculator service:</span></span>

   1. <span data-ttu-id="e2175-134">在 "**解决方案资源管理器**" 窗口中，选择 " **GettingStartedClient** " 项目下的 "**引用**" 文件夹，然后从快捷菜单中选择 "**添加服务引用**"。</span><span class="sxs-lookup"><span data-stu-id="e2175-134">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Service Reference** from the shortcut menu.</span></span>

   2. <span data-ttu-id="e2175-135">在 "**添加服务引用**" 窗口中，选择 "**发现**"。</span><span class="sxs-lookup"><span data-stu-id="e2175-135">In the **Add Service Reference** window, select **Discover**.</span></span>

      <span data-ttu-id="e2175-136">CalculatorService 服务启动，Visual Studio 会将其显示在 "**服务**" 框中。</span><span class="sxs-lookup"><span data-stu-id="e2175-136">The CalculatorService service starts and Visual Studio displays it in the **Services** box.</span></span>

   3. <span data-ttu-id="e2175-137">选择 " **CalculatorService** " 以将其展开并显示服务实现的服务协定。</span><span class="sxs-lookup"><span data-stu-id="e2175-137">Select **CalculatorService** to expand it and display the service contracts implemented by the service.</span></span> <span data-ttu-id="e2175-138">保留默认**命名空间**，然后选择 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="e2175-138">Leave the default **Namespace** and choose **OK**.</span></span>

      <span data-ttu-id="e2175-139">Visual Studio 将在**GettingStartedClient**项目中的**连接的服务**文件夹下添加一个新项。</span><span class="sxs-lookup"><span data-stu-id="e2175-139">Visual Studio adds a new item under the **Connected Services** folder in the **GettingStartedClient** project.</span></span>

### <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="e2175-140">System.servicemodel 元数据实用工具</span><span class="sxs-lookup"><span data-stu-id="e2175-140">ServiceModel Metadata Utility tool</span></span>

<span data-ttu-id="e2175-141">下面的示例演示如何选择性地使用带[元数据实用工具（Svcutil.exe）](servicemodel-metadata-utility-tool-svcutil-exe.md)生成代理类文件。</span><span class="sxs-lookup"><span data-stu-id="e2175-141">The following examples show how to optionally use the [ServiceModel Metadata Utility tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy class file.</span></span> <span data-ttu-id="e2175-142">此工具将生成代理类文件和*App.config*文件。</span><span class="sxs-lookup"><span data-stu-id="e2175-142">This tool generates the proxy class file and the *App.config* file.</span></span> <span data-ttu-id="e2175-143">下面的示例演示如何在 c # 中生成代理并分别 Visual Basic：</span><span class="sxs-lookup"><span data-stu-id="e2175-143">The following examples show how to generate the proxy in C# and Visual Basic, respectively:</span></span>

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a><span data-ttu-id="e2175-144">客户端配置文件</span><span class="sxs-lookup"><span data-stu-id="e2175-144">Client configuration file</span></span>

<span data-ttu-id="e2175-145">创建客户端后，Visual Studio 将在**GettingStartedClient**项目中创建**App.config**配置文件，该文件应类似于以下示例：</span><span class="sxs-lookup"><span data-stu-id="e2175-145">After you've created the client, Visual Studio creates the **App.config** configuration file in the **GettingStartedClient** project, which should be similar to the following example:</span></span>

```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup>
            <!-- specifies the version of WCF to use-->
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1" />
        </startup>
        <system.serviceModel>
            <bindings>
                <!-- Uses wsHttpBinding-->
                <wsHttpBinding>
                    <binding name="WSHttpBinding_ICalculator" />
                </wsHttpBinding>
            </bindings>
            <client>
                <!-- specifies the endpoint to use when calling the service -->
                <endpoint address="http://localhost:8000/GettingStarted/CalculatorService"
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">
                    <identity>
                        <dns value="localhost" />
                    </identity>
                </endpoint>
            </client>
        </system.serviceModel>
    </configuration>
```

<span data-ttu-id="e2175-146">在 [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) 部分下，请注意 [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="e2175-146">Under the [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) section, notice the [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="e2175-147">\*\* &lt; 终结点 &gt; \*\*元素定义客户端用于访问服务的终结点，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e2175-147">The **&lt;endpoint&gt;** element defines the endpoint that the client uses to access the service as follows:</span></span>

- <span data-ttu-id="e2175-148">地址： `http://localhost:8000/GettingStarted/CalculatorService` 。</span><span class="sxs-lookup"><span data-stu-id="e2175-148">Address: `http://localhost:8000/GettingStarted/CalculatorService`.</span></span> <span data-ttu-id="e2175-149">终结点的地址。</span><span class="sxs-lookup"><span data-stu-id="e2175-149">The address of the endpoint.</span></span>
- <span data-ttu-id="e2175-150">服务协定： `ServiceReference1.ICalculator` 。</span><span class="sxs-lookup"><span data-stu-id="e2175-150">Service contract: `ServiceReference1.ICalculator`.</span></span> <span data-ttu-id="e2175-151">服务协定处理 WCF 客户端和服务之间的通信。</span><span class="sxs-lookup"><span data-stu-id="e2175-151">The service contract handles communication between the WCF client and the service.</span></span> <span data-ttu-id="e2175-152">使用其**添加服务引用**函数时，Visual Studio 会生成此约定。</span><span class="sxs-lookup"><span data-stu-id="e2175-152">Visual Studio generated this contract when you used its **Add Service Reference** function.</span></span> <span data-ttu-id="e2175-153">它实质上是在 GettingStartedLib 项目中定义的协定副本。</span><span class="sxs-lookup"><span data-stu-id="e2175-153">It's essentially a copy of the contract that you defined in the GettingStartedLib project.</span></span>
- <span data-ttu-id="e2175-154">绑定： <xref:System.ServiceModel.WSHttpBinding> 。</span><span class="sxs-lookup"><span data-stu-id="e2175-154">Binding: <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="e2175-155">绑定将 HTTP 指定为传输、可互操作的安全性和其他配置详细信息。</span><span class="sxs-lookup"><span data-stu-id="e2175-155">The binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e2175-156">后续步骤</span><span class="sxs-lookup"><span data-stu-id="e2175-156">Next steps</span></span>

<span data-ttu-id="e2175-157">在本教程中，你将了解：</span><span class="sxs-lookup"><span data-stu-id="e2175-157">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="e2175-158">创建并配置 WCF 客户端的控制台应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="e2175-158">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="e2175-159">将服务引用添加到 WCF 服务，以生成客户端应用程序的代理类和配置文件。</span><span class="sxs-lookup"><span data-stu-id="e2175-159">Add a service reference to the WCF service to generate the proxy class and configuration files for the client application.</span></span>

<span data-ttu-id="e2175-160">转到下一教程，了解如何使用生成的客户端。</span><span class="sxs-lookup"><span data-stu-id="e2175-160">Advance to the next tutorial to learn how to use the generated client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e2175-161">教程：使用 WCF 客户端</span><span class="sxs-lookup"><span data-stu-id="e2175-161">Tutorial: Use a WCF client</span></span>](how-to-use-a-wcf-client.md)

---
title: 如何：在 IIS 中承载 WCF 服务
description: 了解如何创建在 Internet Information Services （IIS）中承载的 WCF 服务。 只可以将 IIS 宿主与 HTTP 传输协议一起使用。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: 2ba0ae7adedc3bf0e0ca0cb92b4205edc968a5d8
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052008"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a><span data-ttu-id="1d885-104">如何：在 IIS 中承载 WCF 服务</span><span class="sxs-lookup"><span data-stu-id="1d885-104">How to: Host a WCF Service in IIS</span></span>
<span data-ttu-id="1d885-105">本主题概述了创建在 Internet Information Services （IIS）中承载的 Windows Communication Foundation （WCF）服务所需的基本步骤。</span><span class="sxs-lookup"><span data-stu-id="1d885-105">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="1d885-106">本主题假设您熟悉 IIS 且了解如何使用 IIS 管理工具创建和管理 IIS 应用程序。</span><span class="sxs-lookup"><span data-stu-id="1d885-106">This topic assumes you are familiar with IIS and understand how to use the IIS management tool to create and manage IIS applications.</span></span> <span data-ttu-id="1d885-107">有关 IIS 的详细信息，请参阅[Internet Information Services](https://www.iis.net/)。</span><span class="sxs-lookup"><span data-stu-id="1d885-107">For more information about IIS see [Internet Information Services](https://www.iis.net/).</span></span> <span data-ttu-id="1d885-108">在 IIS 环境中运行的 WCF 服务充分利用 IIS 功能，如进程回收、空闲关闭、进程运行状况监视和基于消息的激活。</span><span class="sxs-lookup"><span data-stu-id="1d885-108">A WCF service that runs in the IIS environment takes full advantage of IIS features, such as process recycling, idle shutdown, process health monitoring, and message-based activation.</span></span> <span data-ttu-id="1d885-109">此宿主选项要求正确配置 IIS，但不需要编写任何承载代码作为应用程序的一部分。</span><span class="sxs-lookup"><span data-stu-id="1d885-109">This hosting option requires that IIS be properly configured, but it does not require that any hosting code be written as part of the application.</span></span> <span data-ttu-id="1d885-110">只可以将 IIS 宿主与 HTTP 传输协议一起使用。</span><span class="sxs-lookup"><span data-stu-id="1d885-110">You can use IIS hosting only with an HTTP transport.</span></span>  
  
 <span data-ttu-id="1d885-111">有关 WCF 和 ASP.NET 如何交互的详细信息，请参阅[Wcf 服务和 ASP.NET](wcf-services-and-aspnet.md)。</span><span class="sxs-lookup"><span data-stu-id="1d885-111">For more information about how WCF and ASP.NET interact, see [WCF Services and ASP.NET](wcf-services-and-aspnet.md).</span></span> <span data-ttu-id="1d885-112">有关配置安全的详细信息，请参阅[安全性](security.md)。</span><span class="sxs-lookup"><span data-stu-id="1d885-112">For more information about configuring security, see [Security](security.md).</span></span>  
  
 <span data-ttu-id="1d885-113">有关此示例的源副本，请参阅[使用内联代码的 IIS 承载](../samples/iis-hosting-using-inline-code.md)。</span><span class="sxs-lookup"><span data-stu-id="1d885-113">For the source copy of this example, see [IIS Hosting Using Inline Code](../samples/iis-hosting-using-inline-code.md).</span></span>  
  
### <a name="to-create-a-service-hosted-by-iis"></a><span data-ttu-id="1d885-114">创建由 IIS 承载的服务</span><span class="sxs-lookup"><span data-stu-id="1d885-114">To create a service hosted by IIS</span></span>  
  
1. <span data-ttu-id="1d885-115">确认 IIS 已经安装并在计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="1d885-115">Confirm that IIS is installed and running on your computer.</span></span> <span data-ttu-id="1d885-116">有关安装和配置 IIS 的详细信息，请参阅[安装和配置 iis 7.0](https://docs.microsoft.com/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista)</span><span class="sxs-lookup"><span data-stu-id="1d885-116">For more information about installing and configuring IIS see [Installing and Configuring IIS 7.0](https://docs.microsoft.com/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista)</span></span>  
  
2. <span data-ttu-id="1d885-117">为应用程序文件创建一个名为 "IISHostedCalcService" 的新文件夹，确保 ASP.NET 有权访问该文件夹的内容，并使用 IIS 管理工具创建一个物理上位于此应用程序目录中的新 IIS 应用程序。</span><span class="sxs-lookup"><span data-stu-id="1d885-117">Create a new folder for your application files called "IISHostedCalcService", ensure that ASP.NET has access to the contents of the folder, and use the IIS management tool to create a new IIS application that is physically located in this application directory.</span></span> <span data-ttu-id="1d885-118">当为应用程序目录创建别名时，请使用“IISHostedCalc”。</span><span class="sxs-lookup"><span data-stu-id="1d885-118">When creating an alias for the application directory use "IISHostedCalc".</span></span>  
  
3. <span data-ttu-id="1d885-119">在应用程序目录中创建一个名为“service.svc”的新文件。</span><span class="sxs-lookup"><span data-stu-id="1d885-119">Create a new file named "service.svc" in the application directory.</span></span> <span data-ttu-id="1d885-120">通过添加以下元素编辑此文件 @ServiceHost 。</span><span class="sxs-lookup"><span data-stu-id="1d885-120">Edit this file by adding the following @ServiceHost element.</span></span>  
  
   ```aspx-csharp
   <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>
   ```  
  
4. <span data-ttu-id="1d885-121">在应用程序目录中创建 App_Code 子目录。</span><span class="sxs-lookup"><span data-stu-id="1d885-121">Create an App_Code subdirectory within the application directory.</span></span>  
  
5. <span data-ttu-id="1d885-122">在 App_Code 子目录中创建名为 Service.cs 的代码文件。</span><span class="sxs-lookup"><span data-stu-id="1d885-122">Create a code file named Service.cs in the App_Code subdirectory.</span></span>  
  
6. <span data-ttu-id="1d885-123">将下面的 using 语句添加到 Service.cs 文件的最前面。</span><span class="sxs-lookup"><span data-stu-id="1d885-123">Add the following using statements to the top of the Service.cs file.</span></span>  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7. <span data-ttu-id="1d885-124">将下面的命名空间声明添加到 using 语句后面。</span><span class="sxs-lookup"><span data-stu-id="1d885-124">Add the following namespace declaration after the using statements.</span></span>  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8. <span data-ttu-id="1d885-125">定义命名空间声明中的服务协定，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="1d885-125">Define the service contract inside the namespace declaration as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. <span data-ttu-id="1d885-126">在服务协定定义后实现服务协定，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="1d885-126">Implement the service contract after the service contract definition as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. <span data-ttu-id="1d885-127">在应用程序目录中创建一个名为“Web.config”的文件，并将下面的配置代码添加到该文件中。</span><span class="sxs-lookup"><span data-stu-id="1d885-127">Create a file named "Web.config" in the application directory and add the following configuration code into the file.</span></span> <span data-ttu-id="1d885-128">在运行时，WCF 基础结构使用这些信息来构造客户端应用程序可与其通信的终结点。</span><span class="sxs-lookup"><span data-stu-id="1d885-128">At runtime, the WCF infrastructure uses the information to construct an endpoint that client applications can communicate with.</span></span>  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]
  
     <span data-ttu-id="1d885-129">此示例显式指定配置文件中的终结点。</span><span class="sxs-lookup"><span data-stu-id="1d885-129">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="1d885-130">如果您不希望向服务添加任何终结点，则运行时为您添加默认终结点。</span><span class="sxs-lookup"><span data-stu-id="1d885-130">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="1d885-131">有关默认终结点、绑定和行为的详细信息，请参阅适用[于 WCF 服务的](../samples/simplified-configuration-for-wcf-services.md)[简化配置](../simplified-configuration.md)和简化配置。</span><span class="sxs-lookup"><span data-stu-id="1d885-131">For more information about default endpoints, bindings, and behaviors see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
11. <span data-ttu-id="1d885-132">为了确保正确承载该服务，请打开 Internet Explorer 的实例，导航到该服务的 URL：`http://localhost/IISHostedCalc/Service.svc`</span><span class="sxs-lookup"><span data-stu-id="1d885-132">To make sure the service is hosted correctly, open an instance of Internet Explorer and browse to the service's URL: `http://localhost/IISHostedCalc/Service.svc`</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d885-133">示例</span><span class="sxs-lookup"><span data-stu-id="1d885-133">Example</span></span>  
 <span data-ttu-id="1d885-134">下面是 IIS 承载的计算器服务的代码的完整列表。</span><span class="sxs-lookup"><span data-stu-id="1d885-134">The following is a complete listing of the code for the IIS hosted calculator service.</span></span>  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)]
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)]
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a><span data-ttu-id="1d885-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1d885-135">See also</span></span>

- [<span data-ttu-id="1d885-136">在 Internet 信息服务中承载</span><span class="sxs-lookup"><span data-stu-id="1d885-136">Hosting in Internet Information Services</span></span>](hosting-in-internet-information-services.md)
- [<span data-ttu-id="1d885-137">承载服务</span><span class="sxs-lookup"><span data-stu-id="1d885-137">Hosting Services</span></span>](../hosting-services.md)
- [<span data-ttu-id="1d885-138">WCF 服务和 ASP.NET</span><span class="sxs-lookup"><span data-stu-id="1d885-138">WCF Services and ASP.NET</span></span>](wcf-services-and-aspnet.md)
- [<span data-ttu-id="1d885-139">安全性</span><span class="sxs-lookup"><span data-stu-id="1d885-139">Security</span></span>](security.md)
- <span data-ttu-id="1d885-140">[Windows Server App Fabric 承载功能](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="1d885-140">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>

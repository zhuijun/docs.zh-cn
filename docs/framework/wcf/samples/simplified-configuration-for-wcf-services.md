---
title: WCF 服务的简化配置
description: 了解如何使用 WCF 实现和配置典型的服务和客户端。 服务通过使用配置文件中指定的终结点进行通信。
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: 46a0c878b29de34219413a508799ddaddf507dd8
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246211"
---
# <a name="simplified-configuration-for-wcf-services"></a><span data-ttu-id="5c336-104">WCF 服务的简化配置</span><span class="sxs-lookup"><span data-stu-id="5c336-104">Simplified Configuration for WCF Services</span></span>
<span data-ttu-id="5c336-105">此示例演示如何使用 Windows Communication Foundation （WCF）实现和配置典型的服务和客户端。</span><span class="sxs-lookup"><span data-stu-id="5c336-105">This sample demonstrates how to implement and configure a typical service and client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="5c336-106">此示例是所有其他基本技术示例的基础。</span><span class="sxs-lookup"><span data-stu-id="5c336-106">This sample is the basis for all other basic technology samples.</span></span>  
  
 <span data-ttu-id="5c336-107">此服务公开用于与服务进行通信的终结点，并使用 .NET Framework 4 中的简化配置。</span><span class="sxs-lookup"><span data-stu-id="5c336-107">This service, which exposes an endpoint for communicating with the service, uses the simplified configuration in .NET Framework 4.</span></span> <span data-ttu-id="5c336-108">在 .NET Framework 4 之前，通常在配置文件（Web.config）中定义终结点，如下面的示例配置代码所示。</span><span class="sxs-lookup"><span data-stu-id="5c336-108">Prior to .NET Framework 4, the endpoint is typically defined in a configuration file (Web.config), as shown in the following example configuration code.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright ©) Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Samples.GettingStarted.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <endpoint address="" binding="basicHttpBinding" contract="ICalculator"/>  
        <endpoint address="mex" binding="mexHttpBinding" contract="IMetadataExchange"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="5c336-109">在 .NET Framework 4 中， `<service>` 元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="5c336-109">In .NET Framework 4, the `<service>` element is optional.</span></span> <span data-ttu-id="5c336-110">当一个服务未定义任何终结点时，会将已实现的每个基址和协定的终结点添加到该服务。</span><span class="sxs-lookup"><span data-stu-id="5c336-110">When a service does not define any endpoints, an endpoint for each base address and contract implemented are added to the service.</span></span> <span data-ttu-id="5c336-111">基址将追加到协定名称后面以确定终结点，该地址方案将确定绑定。</span><span class="sxs-lookup"><span data-stu-id="5c336-111">The base address is appended to the contract name to determine the endpoint and the binding is determined by the address scheme.</span></span> <span data-ttu-id="5c336-112">以下代码示例演示一个简化的配置文件。</span><span class="sxs-lookup"><span data-stu-id="5c336-112">The following code example demonstrates a simplified configuration file.</span></span> <span data-ttu-id="5c336-113">在配置后， `http://localhost/servicemodelsamples/service.svc` 同一台计算机上的客户端可以访问该服务。</span><span class="sxs-lookup"><span data-stu-id="5c336-113">As configured, the service can be accessed at `http://localhost/servicemodelsamples/service.svc` by a client on the same computer.</span></span> <span data-ttu-id="5c336-114">若要使远程计算机上的客户端能够访问该服务，必须指定完全限定域名，而不是本地主机。</span><span class="sxs-lookup"><span data-stu-id="5c336-114">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span> <span data-ttu-id="5c336-115">默认情况下，该服务不公开元数据。</span><span class="sxs-lookup"><span data-stu-id="5c336-115">The service does not expose metadata by default.</span></span> <span data-ttu-id="5c336-116">因此，该服务将打开 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 行为。</span><span class="sxs-lookup"><span data-stu-id="5c336-116">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> behavior.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright © Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="5c336-117">使用此示例</span><span class="sxs-lookup"><span data-stu-id="5c336-117">To use this sample</span></span>  
  
1. <span data-ttu-id="5c336-118">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="5c336-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5c336-119">若要生成解决方案，请按照[生成 Windows Communication Foundation 示例](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="5c336-119">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="5c336-120">按照以下步骤运行示例：</span><span class="sxs-lookup"><span data-stu-id="5c336-120">Run the sample by following these steps:</span></span>  
  
    1. <span data-ttu-id="5c336-121">右键单击**服务**项目，选择 "**设为启动项目**"，然后按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="5c336-121">Right click the **Service** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
    2. <span data-ttu-id="5c336-122">等待确认服务已准备好并且正在运行的控制台输出。</span><span class="sxs-lookup"><span data-stu-id="5c336-122">Wait for the console output confirming that the service is up and running.</span></span>  
  
    3. <span data-ttu-id="5c336-123">右键单击**客户端**项目，选择 "**设为启动项目**"，然后按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="5c336-123">Right click the **Client** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5c336-124">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="5c336-124">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5c336-125">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="5c336-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5c336-126">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="5c336-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5c336-127">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="5c336-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a><span data-ttu-id="5c336-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="5c336-128">See also</span></span>

- <span data-ttu-id="5c336-129">[AppFabric 管理示例](https://docs.microsoft.com/previous-versions/appfabric/ff383405(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="5c336-129">[AppFabric Management Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383405(v=azure.10))</span></span>
- [<span data-ttu-id="5c336-130">简化配置</span><span class="sxs-lookup"><span data-stu-id="5c336-130">Simplified Configuration</span></span>](../simplified-configuration.md)

---
title: 如何：在 WAS 中承载 WCF 服务
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: 1e338440b3a630840230df838e46579e3725bb60
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593108"
---
# <a name="how-to-host-a-wcf-service-in-was"></a><span data-ttu-id="e47b9-102">如何：在 WAS 中承载 WCF 服务</span><span class="sxs-lookup"><span data-stu-id="e47b9-102">How to: Host a WCF Service in WAS</span></span>
<span data-ttu-id="e47b9-103">本主题概述了创建 Windows 进程激活服务（也称为 WAS）托管 Windows Communication Foundation （WCF）服务所需的基本步骤。</span><span class="sxs-lookup"><span data-stu-id="e47b9-103">This topic outlines the basic steps required to create a Windows Process Activation Services (also known as WAS) hosted Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="e47b9-104">WAS 是新的进程激活服务，是对使用非 HTTP 传输协议的 Internet Information Services (IIS) 功能的泛化。</span><span class="sxs-lookup"><span data-stu-id="e47b9-104">WAS is the new process activation service that is a generalization of Internet Information Services (IIS) features that work with non-HTTP transport protocols.</span></span> <span data-ttu-id="e47b9-105">WCF 使用侦听器适配器接口传递通过 WCF 支持的非 HTTP 协议（如 TCP、命名管道和消息队列）接收的激活请求。</span><span class="sxs-lookup"><span data-stu-id="e47b9-105">WCF uses the listener adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by WCF, such as TCP, named pipes, and Message Queuing.</span></span>  
  
 <span data-ttu-id="e47b9-106">此主机选项要求正确安装和配置 WAS 激活组件，但不要求编写任何主机代码作为应用程序的一部分。</span><span class="sxs-lookup"><span data-stu-id="e47b9-106">This hosting option requires that WAS activation components are properly installed and configured, but it does not require any hosting code to be written as part of the application.</span></span> <span data-ttu-id="e47b9-107">有关安装和配置 WAS 的详细信息，请参阅[如何：安装和配置 WCF 激活组件](how-to-install-and-configure-wcf-activation-components.md)。</span><span class="sxs-lookup"><span data-stu-id="e47b9-107">For more information about installing and configuring WAS, see [How to: Install and Configure WCF Activation Components](how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="e47b9-108">如果将 Web 服务器的请求处理管道设置为经典模式，则将不支持 WAS 激活。</span><span class="sxs-lookup"><span data-stu-id="e47b9-108">WAS activation is not supported if the web server’s request processing pipeline is set to Classic mode.</span></span> <span data-ttu-id="e47b9-109">如果要使用 WAS 激活，则必须将 Web 服务器的请求处理管道设置为集成模式。</span><span class="sxs-lookup"><span data-stu-id="e47b9-109">The web server’s request processing pipeline must be set to Integrated mode if WAS activation is to be used.</span></span>  
  
 <span data-ttu-id="e47b9-110">当在 WAS 中承载 WCF 服务时，将按常规方式使用标准绑定。</span><span class="sxs-lookup"><span data-stu-id="e47b9-110">When a WCF service is hosted in WAS, the standard bindings are used in the usual way.</span></span> <span data-ttu-id="e47b9-111">但是，在使用 <xref:System.ServiceModel.NetTcpBinding> 和 <xref:System.ServiceModel.NetNamedPipeBinding> 配置 WAS 承载的服务时，必须满足一个约束条件。</span><span class="sxs-lookup"><span data-stu-id="e47b9-111">However, when using the <xref:System.ServiceModel.NetTcpBinding> and the <xref:System.ServiceModel.NetNamedPipeBinding> to configure a WAS-hosted service, a constraint must be satisfied.</span></span> <span data-ttu-id="e47b9-112">当不同的终结点使用相同的传输时，绑定设置必须在以下的七个属性上相匹配：</span><span class="sxs-lookup"><span data-stu-id="e47b9-112">When different endpoints use the same transport, the binding settings have to match on the following seven properties:</span></span>  
  
- <span data-ttu-id="e47b9-113">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="e47b9-113">ConnectionBufferSize</span></span>  
  
- <span data-ttu-id="e47b9-114">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="e47b9-114">ChannelInitializationTimeout</span></span>  
  
- <span data-ttu-id="e47b9-115">MaxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="e47b9-115">MaxPendingConnections</span></span>  
  
- <span data-ttu-id="e47b9-116">MaxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="e47b9-116">MaxOutputDelay</span></span>  
  
- <span data-ttu-id="e47b9-117">MaxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="e47b9-117">MaxPendingAccepts</span></span>  
  
- <span data-ttu-id="e47b9-118">ConnectionPoolSettings.IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="e47b9-118">ConnectionPoolSettings.IdleTimeout</span></span>  
  
- <span data-ttu-id="e47b9-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="e47b9-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span></span>  
  
 <span data-ttu-id="e47b9-120">否则，最先初始化的终结点总是确定这些属性的值，并且以后添加的终结点若与这些设置不匹配，则将引发 <xref:System.ServiceModel.ServiceActivationException>。</span><span class="sxs-lookup"><span data-stu-id="e47b9-120">Otherwise, the endpoint that is initialized first always determines the values of these properties, and endpoints added later throw a <xref:System.ServiceModel.ServiceActivationException> if they do not match those settings.</span></span>  
  
 <span data-ttu-id="e47b9-121">有关此示例的源副本，请参阅[TCP 激活](../samples/tcp-activation.md)。</span><span class="sxs-lookup"><span data-stu-id="e47b9-121">For the source copy of this example, see [TCP Activation](../samples/tcp-activation.md).</span></span>  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a><span data-ttu-id="e47b9-122">创建 WAS 承载的基本服务</span><span class="sxs-lookup"><span data-stu-id="e47b9-122">To create a basic service hosted by WAS</span></span>  
  
1. <span data-ttu-id="e47b9-123">为该类型的服务定义服务协定。</span><span class="sxs-lookup"><span data-stu-id="e47b9-123">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2. <span data-ttu-id="e47b9-124">在服务类中实现该服务协定。</span><span class="sxs-lookup"><span data-stu-id="e47b9-124">Implement the service contract in a service class.</span></span> <span data-ttu-id="e47b9-125">请注意，在服务的实现内部，未指定地址或绑定信息。</span><span class="sxs-lookup"><span data-stu-id="e47b9-125">Note that address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="e47b9-126">而且，不必编写代码也可从配置文件中检索该信息。</span><span class="sxs-lookup"><span data-stu-id="e47b9-126">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3. <span data-ttu-id="e47b9-127">创建 Web.config 文件，以定义要由 <xref:System.ServiceModel.NetTcpBinding> 终结点使用的 `CalculatorService` 绑定。</span><span class="sxs-lookup"><span data-stu-id="e47b9-127">Create a Web.config file to define the <xref:System.ServiceModel.NetTcpBinding> binding to be used by the `CalculatorService` endpoints.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <bindings>  
          <netTcpBinding>  
            <binding portSharingEnabled="true">  
              <security mode="None" />  
            </binding>  
          </netTcpBinding>  
        </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4. <span data-ttu-id="e47b9-128">创建包含以下代码的 Service.svc 文件。</span><span class="sxs-lookup"><span data-stu-id="e47b9-128">Create a Service.svc file that contains the following code.</span></span>  
  
   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```
  
5. <span data-ttu-id="e47b9-129">将 Service.svc 文件放到 IIS 虚拟目录中。</span><span class="sxs-lookup"><span data-stu-id="e47b9-129">Place the Service.svc file in your IIS virtual directory.</span></span>  
  
### <a name="to-create-a-client-to-use-the-service"></a><span data-ttu-id="e47b9-130">创建要使用服务的客户端</span><span class="sxs-lookup"><span data-stu-id="e47b9-130">To create a client to use the service</span></span>  
  
1. <span data-ttu-id="e47b9-131">从命令行使用[Svcutil.exe 元数据实用工具（）](../servicemodel-metadata-utility-tool-svcutil-exe.md)从服务元数据生成代码。</span><span class="sxs-lookup"><span data-stu-id="e47b9-131">Use [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>  
  
    ```console
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="e47b9-132">生成的客户端包含 `ICalculator` 接口，该接口定义了客户端实现必须满足的服务协定。</span><span class="sxs-lookup"><span data-stu-id="e47b9-132">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3. <span data-ttu-id="e47b9-133">生成的客户端应用程序还包含 `ClientCalculator` 的实现。</span><span class="sxs-lookup"><span data-stu-id="e47b9-133">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="e47b9-134">请注意，在服务的实现内部，未指定地址和绑定信息。</span><span class="sxs-lookup"><span data-stu-id="e47b9-134">Note that the address and binding information is not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="e47b9-135">而且，不必编写代码也可从配置文件中检索该信息。</span><span class="sxs-lookup"><span data-stu-id="e47b9-135">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4. <span data-ttu-id="e47b9-136">使用 <xref:System.ServiceModel.NetTcpBinding> 的客户端配置也通过 Svcutil.exe 生成。</span><span class="sxs-lookup"><span data-stu-id="e47b9-136">The configuration for the client that uses the <xref:System.ServiceModel.NetTcpBinding> is also generated by Svcutil.exe.</span></span> <span data-ttu-id="e47b9-137">在使用 Visual Studio 时，应在 App.config 文件中命名此文件。</span><span class="sxs-lookup"><span data-stu-id="e47b9-137">This file should be named in the App.config file when using Visual Studio.</span></span>  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]
  
5. <span data-ttu-id="e47b9-138">在应用程序中创建 `ClientCalculator` 的实例，然后调用服务操作。</span><span class="sxs-lookup"><span data-stu-id="e47b9-138">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6. <span data-ttu-id="e47b9-139">编译并运行客户端。</span><span class="sxs-lookup"><span data-stu-id="e47b9-139">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e47b9-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e47b9-140">See also</span></span>

- [<span data-ttu-id="e47b9-141">TCP 激活</span><span class="sxs-lookup"><span data-stu-id="e47b9-141">TCP Activation</span></span>](../samples/tcp-activation.md)
- <span data-ttu-id="e47b9-142">[Windows Server App Fabric 承载功能](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="e47b9-142">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>

---
title: WCF Discovery 概述
ms.date: 03/30/2017
ms.assetid: 84fad0e4-23b1-45b5-a2d4-c9cdf90bbb22
ms.openlocfilehash: 8b4dda410b9ca7d7d3ff76795753811a80a617ec
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554614"
---
# <a name="wcf-discovery-overview"></a><span data-ttu-id="1e043-102">WCF Discovery 概述</span><span class="sxs-lookup"><span data-stu-id="1e043-102">WCF Discovery Overview</span></span>
<span data-ttu-id="1e043-103">Discovery API 提供了统一的编程模型来使用 WS-Discovery 协议动态发布和发现 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="1e043-103">The Discovery APIs provide a unified programming model for the dynamic publication and discovery of Web services using the WS-Discovery protocol.</span></span> <span data-ttu-id="1e043-104">通过这些 API，服务可以发布自身，客户端可以查找已发布的服务。</span><span class="sxs-lookup"><span data-stu-id="1e043-104">These APIs allow services to publish themselves and clients to find published services.</span></span> <span data-ttu-id="1e043-105">服务一旦可供检测，即可发送公告消息，并侦听和响应发现请求。</span><span class="sxs-lookup"><span data-stu-id="1e043-105">Once a service is made discoverable, the service has the ability to send announcement messages as well as listen for and respond to discovery requests.</span></span> <span data-ttu-id="1e043-106">可检测到的服务可以发送 Hello 消息和 Bye 消息，前者用于公告服务将到达网络，后者用于公告服务将离开网络。</span><span class="sxs-lookup"><span data-stu-id="1e043-106">Discoverable services can send Hello messages to announce their arrival on a network and Bye messages to announce their departure from a network.</span></span> <span data-ttu-id="1e043-107">若要查找服务，客户端将在网络上发送包含特定条件（如服务协定类型、关键字和范围）的 `Probe` 请求。</span><span class="sxs-lookup"><span data-stu-id="1e043-107">To find a service, clients send a `Probe` request that contains specific criteria such as service contract type, keywords, and scope on the network.</span></span> <span data-ttu-id="1e043-108">服务接收到此 `Probe` 请求，并确定它们是否匹配该条件。</span><span class="sxs-lookup"><span data-stu-id="1e043-108">Services receive the `Probe` request and determine whether they match the criteria.</span></span> <span data-ttu-id="1e043-109">如果某一服务匹配该条件，该服务会做出响应，向客户端回发一条 `ProbeMatch` 消息，该消息包含与该服务联系所需的信息。</span><span class="sxs-lookup"><span data-stu-id="1e043-109">If a service matches, it responds by sending a `ProbeMatch` message back to the client with the information necessary to contact the service.</span></span> <span data-ttu-id="1e043-110">客户端还可以发送 `Resolve` 请求，以便查找可能已更改终结点地址的服务。</span><span class="sxs-lookup"><span data-stu-id="1e043-110">Clients can also send `Resolve` requests that allow them to find services that may have changed their endpoint address.</span></span> <span data-ttu-id="1e043-111">匹配的服务会向客户端回发一条 `Resolve` 消息，以此来响应 `ResolveMatch` 请求。</span><span class="sxs-lookup"><span data-stu-id="1e043-111">Matching services respond to `Resolve` requests by sending a `ResolveMatch` message back to the client.</span></span>  
  
## <a name="ad-hoc-and-managed-modes"></a><span data-ttu-id="1e043-112">临时模式和托管模式</span><span class="sxs-lookup"><span data-stu-id="1e043-112">Ad-Hoc and Managed Modes</span></span>  
 <span data-ttu-id="1e043-113">Discovery API 支持两种不同模式：托管模式和临时模式。</span><span class="sxs-lookup"><span data-stu-id="1e043-113">The Discovery API supports two different modes: Managed and Ad-Hoc.</span></span> <span data-ttu-id="1e043-114">托管模式中存在一台称为发现代理的中央服务器，用于维护有关可用服务的信息。</span><span class="sxs-lookup"><span data-stu-id="1e043-114">In Managed mode there is a centralized server called a discovery proxy that maintains information about available services.</span></span> <span data-ttu-id="1e043-115">可以采用多种方式使用服务相关信息填充发现代理。</span><span class="sxs-lookup"><span data-stu-id="1e043-115">The discovery proxy can be populated with information about services in a variety of ways.</span></span> <span data-ttu-id="1e043-116">例如，服务可以在启动时向发现代理发送公告消息，或者代理也可以从数据库或配置文件中读取数据以确定可用服务。</span><span class="sxs-lookup"><span data-stu-id="1e043-116">For example, services can send announcement messages during start up to the discovery proxy or the proxy may read data from a database or a configuration file to determine what services are available.</span></span> <span data-ttu-id="1e043-117">发现代理的填充方式完全由开发人员决定。</span><span class="sxs-lookup"><span data-stu-id="1e043-117">How the discovery proxy is populated is completely up to the developer.</span></span> <span data-ttu-id="1e043-118">客户端使用发现代理检索有关可用服务的信息。</span><span class="sxs-lookup"><span data-stu-id="1e043-118">Clients use the discovery proxy to retrieve information about available services.</span></span> <span data-ttu-id="1e043-119">当客户端搜索服务时，它会向发现代理发送一条 `Probe` 消息，然后由代理确定已知的任何服务是否与客户端搜索的服务匹配。</span><span class="sxs-lookup"><span data-stu-id="1e043-119">When a client searches for a service it sends a `Probe` message to the discovery proxy and the proxy determines whether any of the services it knows about match the service the client is searching for.</span></span> <span data-ttu-id="1e043-120">如果存在匹配服务，发现代理会向客户端回发 `ProbeMatch` 响应。</span><span class="sxs-lookup"><span data-stu-id="1e043-120">If there are matches the discovery proxy sends a `ProbeMatch` response back to the client.</span></span> <span data-ttu-id="1e043-121">然后，客户端可以使用代理返回的服务信息，直接与该服务联系。</span><span class="sxs-lookup"><span data-stu-id="1e043-121">The client can then contact the service directly using the service information returned from the proxy.</span></span> <span data-ttu-id="1e043-122">托管模式所依据的关键原理是：以单播方式向一个机构（即发现代理）发送发现请求。</span><span class="sxs-lookup"><span data-stu-id="1e043-122">The key principle behind Managed mode is that the discovery requests are sent in a unicast manner to one authority, the discovery proxy.</span></span> <span data-ttu-id="1e043-123">通过 .NET Framework 包含的关键组件，您可以生成自己的代理。</span><span class="sxs-lookup"><span data-stu-id="1e043-123">The .NET Framework contains key components that allow you to build your own proxy.</span></span> <span data-ttu-id="1e043-124">客户端和服务可以采用多种方法来定位代理：</span><span class="sxs-lookup"><span data-stu-id="1e043-124">Clients and services can locate the proxy by multiple methods:</span></span>  
  
- <span data-ttu-id="1e043-125">代理可以响应临时消息。</span><span class="sxs-lookup"><span data-stu-id="1e043-125">The proxy can respond to ad-hoc messages.</span></span>  
  
- <span data-ttu-id="1e043-126">代理可以在启动时发送公告消息。</span><span class="sxs-lookup"><span data-stu-id="1e043-126">The proxy can send an announcement message during start up.</span></span>  
  
- <span data-ttu-id="1e043-127">可以编写客户端和服务来查找特定的已知终结点。</span><span class="sxs-lookup"><span data-stu-id="1e043-127">Clients and services can be written to look for a specific well-known endpoint.</span></span>  
  
 <span data-ttu-id="1e043-128">临时模式中没有任何中央服务器。</span><span class="sxs-lookup"><span data-stu-id="1e043-128">In Ad-Hoc mode, there is no centralized server.</span></span> <span data-ttu-id="1e043-129">服务公告和客户端请求等所有发现消息都以多播方式发送。</span><span class="sxs-lookup"><span data-stu-id="1e043-129">All discovery messages such as service announcements and client requests are sent in a multicast fashion.</span></span> <span data-ttu-id="1e043-130">默认情况下，.NET Framework 包含对基于 UDP 协议的临时发现的支持。</span><span class="sxs-lookup"><span data-stu-id="1e043-130">By default the .NET Framework contains support for Ad-Hoc discovery over the UDP protocol.</span></span> <span data-ttu-id="1e043-131">例如，如果将服务配置为在启动时发出 Hello 公告，则该服务采用 UDP 协议通过已知多播地址来发出此公告。</span><span class="sxs-lookup"><span data-stu-id="1e043-131">For example, if a service is configured to send out a Hello announcement on start up, it sends it out over a well-known, multicast address using the UDP protocol.</span></span> <span data-ttu-id="1e043-132">客户端必须主动侦听这些公告，并对这些公告进行相应处理。</span><span class="sxs-lookup"><span data-stu-id="1e043-132">Clients have to actively listen for these announcements and process them accordingly.</span></span> <span data-ttu-id="1e043-133">当客户端针对某一服务发送 `Probe` 消息时，会通过采用多播协议的网络进行发送。</span><span class="sxs-lookup"><span data-stu-id="1e043-133">When a client sends a `Probe` message for a service it is sent over the network using a multicast protocol.</span></span> <span data-ttu-id="1e043-134">接收到请求的各服务确定自身是否与 `Probe` 消息中的条件匹配，如果服务与 `ProbeMatch` 消息中指定的条件匹配，服务将直接使用 `Probe` 消息响应客户端。</span><span class="sxs-lookup"><span data-stu-id="1e043-134">Each service that receives the request determines whether it matches the criteria in the `Probe` message and responds directly to the client with a `ProbeMatch` message if the service matches the criteria specified in the `Probe` message.</span></span>  
  
## <a name="benefits-of-using-wcf-discovery"></a><span data-ttu-id="1e043-135">使用 WCF Discovery 的好处</span><span class="sxs-lookup"><span data-stu-id="1e043-135">Benefits of Using WCF Discovery</span></span>  
 <span data-ttu-id="1e043-136">由于 WCF Discovery 是采用 WS-Discovery 协议实现的，因此它可以与其他客户端、服务以及实现 WS-Discovery 的代理进行互操作。</span><span class="sxs-lookup"><span data-stu-id="1e043-136">Because WCF Discovery is implemented using the WS-Discovery protocol it is interoperable with other clients, services, and proxies that implement WS-Discovery as well.</span></span> <span data-ttu-id="1e043-137">WCF Discovery 建立在现有 WCF API 的基础上，从而可以向现有服务和客户端方便地添加 Discovery 功能。</span><span class="sxs-lookup"><span data-stu-id="1e043-137">WCF Discovery is built upon the existing WCF APIs, which makes it easy to add Discovery functionality to your existing services and clients.</span></span> <span data-ttu-id="1e043-138">通过应用程序配置设置，可以轻松地添加服务发现功能。</span><span class="sxs-lookup"><span data-stu-id="1e043-138">Service discoverability can be easily added through the application configuration settings.</span></span> <span data-ttu-id="1e043-139">此外，WCF Discovery 还支持在其他传输（如对等网络、命名覆盖和 HTTP）中使用发现协议。</span><span class="sxs-lookup"><span data-stu-id="1e043-139">In addition, WCF Discovery also supports using the discovery protocol over other transports such as peer net, naming overlay, and HTTP.</span></span> <span data-ttu-id="1e043-140">WCF Discovery 支持采用发现代理的托管运行模式。</span><span class="sxs-lookup"><span data-stu-id="1e043-140">WCF Discovery provides support for a Managed mode of operation where a discovery proxy is used.</span></span> <span data-ttu-id="1e043-141">由于消息直接发送到发现代理，而不是将多播消息发送到整个网络，因此这样可以减少网络流量。</span><span class="sxs-lookup"><span data-stu-id="1e043-141">This can reduce network traffic as messages are sent directly to the discovery proxy instead of sending multicast messages to the entire network.</span></span> <span data-ttu-id="1e043-142">使用 Web 服务时，WCF Discovery 还可以提高灵活性。</span><span class="sxs-lookup"><span data-stu-id="1e043-142">WCF Discovery also allows for more flexibility when working with Web services.</span></span> <span data-ttu-id="1e043-143">例如，您可以更改服务地址，而不必重新配置客户端或服务。</span><span class="sxs-lookup"><span data-stu-id="1e043-143">For example, you can change the address of a service without having to reconfigure the client or the service.</span></span> <span data-ttu-id="1e043-144">当客户端必须访问该服务时，它通过 `Probe` 请求发出 `Find` 消息，并希望该服务使用其当前地址进行响应。</span><span class="sxs-lookup"><span data-stu-id="1e043-144">When a client must access the service it can issue a `Probe` message through a `Find` request and expect the service to respond with its current address.</span></span> <span data-ttu-id="1e043-145">WCF Discovery 允许客户端基于不同条件搜索服务，这些条件包括协定类型、绑定元素、命名空间、范围以及关键字或版本号。</span><span class="sxs-lookup"><span data-stu-id="1e043-145">WCF Discovery allows a client to search for a service based on different criteria including contract types, binding elements, namespace, scope, and keywords or version numbers.</span></span> <span data-ttu-id="1e043-146">WCF Discovery 支持运行时和设计时发现功能。</span><span class="sxs-lookup"><span data-stu-id="1e043-146">WCF Discovery enables runtime and design time discovery.</span></span> <span data-ttu-id="1e043-147">可以将发现功能添加到应用程序中，这一特点可用于启用其他方案，如容错和自动配置。</span><span class="sxs-lookup"><span data-stu-id="1e043-147">Adding discovery to your application can be used to enable other scenarios such as fault tolerance and auto configuration.</span></span>  
  
## <a name="service-publication"></a><span data-ttu-id="1e043-148">服务发布</span><span class="sxs-lookup"><span data-stu-id="1e043-148">Service Publication</span></span>  
 <span data-ttu-id="1e043-149">若要使服务可供检测，必须向服务主机添加 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>，并且必须添加发现终结点，以便指定侦听发现消息的位置。</span><span class="sxs-lookup"><span data-stu-id="1e043-149">To make a service discoverable, a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> must be added to the service host and a discovery endpoint must be added to specify where to listen for discovery messages.</span></span> <span data-ttu-id="1e043-150">下面的代码示例演示如何修改自承载服务，以使该服务可供检测。</span><span class="sxs-lookup"><span data-stu-id="1e043-150">The following code example shows how a self-hosted service can be modified to make it discoverable.</span></span>  
  
```csharp  
Uri baseAddress = new Uri($"http://{System.Net.Dns.GetHostName()}:8000/discovery/scenarios/calculatorservice/{Guid.NewGuid().ToString()}/");

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());

    // ** DISCOVERY ** //
    // Add the discovery endpoint that specifies where to publish the services
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());

    // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();

    // The service can now be accessed.
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
}
```  
  
 <span data-ttu-id="1e043-151">必须在服务说明中添加 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> 实例，以使服务可供检测。</span><span class="sxs-lookup"><span data-stu-id="1e043-151">A <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance must be added to a service description for the service to be discoverable.</span></span> <span data-ttu-id="1e043-152">必须向服务主机添加 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> 实例，以将发现请求的侦听位置告知服务。</span><span class="sxs-lookup"><span data-stu-id="1e043-152">A <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance must be added to the service host to tell the service where to listen for discovery requests.</span></span> <span data-ttu-id="1e043-153">在本示例中，添加了 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>（派生自 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>），用于指定服务应通过 UDP 多播传输侦听发现请求。</span><span class="sxs-lookup"><span data-stu-id="1e043-153">In this example, a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (which is derived from <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>) is added to specify that the service should listen for discovery requests over the UDP multicast transport.</span></span> <span data-ttu-id="1e043-154">由于所有消息均以多播方式发送，因此，<xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 用于临时发现。</span><span class="sxs-lookup"><span data-stu-id="1e043-154">The <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is used for Ad-Hoc discovery because all messages are sent in a multicast fashion.</span></span>  
  
## <a name="announcement"></a><span data-ttu-id="1e043-155">公告</span><span class="sxs-lookup"><span data-stu-id="1e043-155">Announcement</span></span>  
 <span data-ttu-id="1e043-156">默认情况下，发布服务时不会发出公告消息。</span><span class="sxs-lookup"><span data-stu-id="1e043-156">By default, service publication does not send out announcement messages.</span></span> <span data-ttu-id="1e043-157">必须对服务进行配置才能发出公告消息。</span><span class="sxs-lookup"><span data-stu-id="1e043-157">The service must be configured to send out announcement messages.</span></span> <span data-ttu-id="1e043-158">这就为服务编写器提供了额外的灵活性，因为它们可以分别通告服务和侦听发现消息。</span><span class="sxs-lookup"><span data-stu-id="1e043-158">This provides additional flexibility for service writers because they can announce the service separately from listening for discovery messages.</span></span> <span data-ttu-id="1e043-159">服务公告还可用作向发现代理或其他服务注册表注册服务的机制。</span><span class="sxs-lookup"><span data-stu-id="1e043-159">Service announcement can also be used as a mechanism for registering services with a discovery proxy or other service registries.</span></span> <span data-ttu-id="1e043-160">下面的代码演示如何将服务配置为通过 UDP 绑定发送公告消息。</span><span class="sxs-lookup"><span data-stu-id="1e043-160">The following code shows how to configure a service to send announcement messages over a UDP binding.</span></span>  
  
```csharp  
Uri baseAddress = new Uri($"http://{System.Net.Dns.GetHostName()}:8000/discovery/scenarios/calculatorservice/{Guid.NewGuid().ToString()}/");

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    ServiceDiscoveryBehavior discoveryBehavior = new ServiceDiscoveryBehavior();
    serviceHost.Description.Behaviors.Add(discoveryBehavior);

    // Send announcements on UDP multicast transport
    discoveryBehavior.AnnouncementEndpoints.Add(
      new UdpAnnouncementEndpoint());

    // ** DISCOVERY ** //
    // Add the discovery endpoint that specifies where to publish the services
    serviceHost.Description.Endpoints.Add(new UdpDiscoveryEndpoint());

    // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();

    // The service can now be accessed.
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
}
```  
  
## <a name="service-discovery"></a><span data-ttu-id="1e043-161">服务发现</span><span class="sxs-lookup"><span data-stu-id="1e043-161">Service Discovery</span></span>  
 <span data-ttu-id="1e043-162">客户端应用程序可以使用 <xref:System.ServiceModel.Discovery.DiscoveryClient> 类查找服务。</span><span class="sxs-lookup"><span data-stu-id="1e043-162">A client application can use the <xref:System.ServiceModel.Discovery.DiscoveryClient> class to find services.</span></span> <span data-ttu-id="1e043-163">开发人员可创建 <xref:System.ServiceModel.Discovery.DiscoveryClient> 类的实例，用于传入指定 `Probe` 或 `Resolve` 消息的发送位置的发现终结点。</span><span class="sxs-lookup"><span data-stu-id="1e043-163">The developer creates an instance of the <xref:System.ServiceModel.Discovery.DiscoveryClient> class that passes in a discovery endpoint that specifies where to send `Probe` or `Resolve` messages.</span></span> <span data-ttu-id="1e043-164">然后，客户端调用 <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>，用于指定 <xref:System.ServiceModel.Discovery.FindCriteria> 实例中的搜索条件。</span><span class="sxs-lookup"><span data-stu-id="1e043-164">The client then calls <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> that specifies search criteria within a <xref:System.ServiceModel.Discovery.FindCriteria> instance.</span></span> <span data-ttu-id="1e043-165">如果找到匹配的服务，则 <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> 返回 <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> 的集合。</span><span class="sxs-lookup"><span data-stu-id="1e043-165">If matching services are found, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> returns a collection of <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>.</span></span> <span data-ttu-id="1e043-166">下面的代码演示如何调用 `Find` 方法并连接到已发现的服务。</span><span class="sxs-lookup"><span data-stu-id="1e043-166">The following code shows how to call the `Find` method and then connect to a discovered service.</span></span>  
  
```csharp  
class Client
{
    static EndpointAddress serviceAddress;
  
    static void Main()
    {  
        if (FindService())
        {
            InvokeService();
        }
    }  
  
    // ** DISCOVERY ** //  
    static bool FindService()  
    {  
        Console.WriteLine("\nFinding Calculator Service ..");  
        DiscoveryClient discoveryClient =
            new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
        Collection<EndpointDiscoveryMetadata> calculatorServices =
            (Collection<EndpointDiscoveryMetadata>)discoveryClient.Find(new FindCriteria(typeof(ICalculator))).Endpoints;  
  
        discoveryClient.Close();  
  
        if (calculatorServices.Count == 0)  
        {  
            Console.WriteLine("\nNo services are found.");  
            return false;  
        }  
        else  
        {  
            serviceAddress = calculatorServices[0].Address;  
            return true;  
        }  
    }  
  
    static void InvokeService()  
    {  
        Console.WriteLine("\nInvoking Calculator Service at {0}\n", serviceAddress);  
  
        // Create a client  
        CalculatorClient client = new CalculatorClient();  
        client.Endpoint.Address = serviceAddress;  
        client.Add(10,3);  
    }
}  
```  
  
## <a name="discovery-and-message-level-security"></a><span data-ttu-id="1e043-167">发现和消息级别安全</span><span class="sxs-lookup"><span data-stu-id="1e043-167">Discovery and Message Level Security</span></span>  
 <span data-ttu-id="1e043-168">使用消息级别安全时，需要在服务发现终结点上指定 <xref:System.ServiceModel.EndpointIdentity>，并在客户端发现终结点上指定匹配的 <xref:System.ServiceModel.EndpointIdentity>。</span><span class="sxs-lookup"><span data-stu-id="1e043-168">When using message level security it is necessary to specify an <xref:System.ServiceModel.EndpointIdentity> on the service discovery endpoint and a matching <xref:System.ServiceModel.EndpointIdentity> on the client discovery endpoint.</span></span> <span data-ttu-id="1e043-169">有关消息级别安全性的详细信息，请参阅 [消息安全](message-security-in-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="1e043-169">For more information about message level security, see [Message Security](message-security-in-wcf.md).</span></span>  
  
## <a name="discovery-and-web-hosted-services"></a><span data-ttu-id="1e043-170">发现和 Web 承载的服务</span><span class="sxs-lookup"><span data-stu-id="1e043-170">Discovery and Web Hosted Services</span></span>  
 <span data-ttu-id="1e043-171">若要使 WCF 服务可发现，这些服务必须正在运行。</span><span class="sxs-lookup"><span data-stu-id="1e043-171">In order for WCF services to be discoverable they must be running.</span></span> <span data-ttu-id="1e043-172">在 IIS/WAS 接收到为服务绑定的消息之前，IIS 或 WAS 下承载的 WCF 服务不会运行，因此这些服务在默认情况下不可发现。</span><span class="sxs-lookup"><span data-stu-id="1e043-172">WCF services hosted under IIS or WAS do not run until IIS/WAS receives a message bound for the service, so they cannot be discoverable by default.</span></span>  <span data-ttu-id="1e043-173">使 Web 承载的服务可发现的两种方法：</span><span class="sxs-lookup"><span data-stu-id="1e043-173">There are two options for making Web-Hosted services discoverable:</span></span>  
  
1. <span data-ttu-id="1e043-174">使用 Windows Server AppFabric 自动启动功能</span><span class="sxs-lookup"><span data-stu-id="1e043-174">Use the Windows Server AppFabric Auto-Start feature</span></span>  
  
2. <span data-ttu-id="1e043-175">使用发现代理代表服务进行通信</span><span class="sxs-lookup"><span data-stu-id="1e043-175">Use a discovery proxy to communicate on behalf of the service</span></span>  
  
 <span data-ttu-id="1e043-176">Windows Server AppFabric 具有自动启动功能，该功能允许服务在接收到任何消息之前启动。</span><span class="sxs-lookup"><span data-stu-id="1e043-176">Windows Server AppFabric has an Auto-Start feature that will allow a service to be started before receiving any messages.</span></span> <span data-ttu-id="1e043-177">设置了此自动启动功能时，IIS/WAS 承载的服务可配置为可发现。</span><span class="sxs-lookup"><span data-stu-id="1e043-177">With this Auto-Start set, an IIS/WAS hosted service can be configured to be discoverable.</span></span> <span data-ttu-id="1e043-178">有关自动启动功能的详细信息，请参阅 [Windows Server AppFabric 自动启动功能](/previous-versions/appfabric/ee677260(v=azure.10))。</span><span class="sxs-lookup"><span data-stu-id="1e043-178">For more information about the Auto-Start feature see, [Windows Server AppFabric Auto-Start Feature](/previous-versions/appfabric/ee677260(v=azure.10)).</span></span> <span data-ttu-id="1e043-179">必须随打开自动启动功能一起，针对发现配置服务。</span><span class="sxs-lookup"><span data-stu-id="1e043-179">Along with turning on the Auto-Start feature, you must configure the service for discovery.</span></span> <span data-ttu-id="1e043-180">有关详细信息，请参阅 [如何：以编程方式向 WCF 服务添加可发现性和](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[在配置文件中配置发现](configuring-discovery-in-a-configuration-file.md)的客户端。</span><span class="sxs-lookup"><span data-stu-id="1e043-180">For more information, see [How to: Programmatically Add Discoverability to a WCF Service and Client](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[Configuring Discovery in a Configuration File](configuring-discovery-in-a-configuration-file.md).</span></span>  
  
 <span data-ttu-id="1e043-181">发现代理可以用于在服务未运行时，代表 WCF 服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="1e043-181">A discovery proxy can be used to communicate on behalf of the WCF service when the service is not running.</span></span> <span data-ttu-id="1e043-182">代理可以为进行探测而侦听，或解析消息及对客户端的响应。</span><span class="sxs-lookup"><span data-stu-id="1e043-182">The proxy can listen for probe or resolve messages and respond to the client.</span></span> <span data-ttu-id="1e043-183">客户端随后可以直接向服务发送消息。</span><span class="sxs-lookup"><span data-stu-id="1e043-183">The client can then send messages directly to the service.</span></span> <span data-ttu-id="1e043-184">当客户端向服务发送消息时，它将实例化以响应消息。</span><span class="sxs-lookup"><span data-stu-id="1e043-184">When the client sends a message to the service it will be instantiated to respond to the message.</span></span> <span data-ttu-id="1e043-185">有关实现发现代理的详细信息，请参阅 [实现发现代理](implementing-a-discovery-proxy.md)。</span><span class="sxs-lookup"><span data-stu-id="1e043-185">For more information about implementing a discovery proxy see, [Implementing a Discovery Proxy](implementing-a-discovery-proxy.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e043-186">为了使 WCF 发现正常工作，所有 Nic (网络接口控制器) 应只有1个 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="1e043-186">For WCF Discovery to work correctly, all NICs (Network Interface Controller) should only have 1 IP address.</span></span>

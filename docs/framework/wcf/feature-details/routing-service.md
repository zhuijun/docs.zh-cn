---
title: 路由服务
ms.date: 03/30/2017
ms.assetid: ca7c216a-5141-4132-8193-102c181d2eba
ms.openlocfilehash: 833c824e17d70a982a2f7bb13fe388b9b2b0dec1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590444"
---
# <a name="routing-service"></a><span data-ttu-id="acd58-102">路由服务</span><span class="sxs-lookup"><span data-stu-id="acd58-102">Routing Service</span></span>

<span data-ttu-id="acd58-103">路由服务是充当消息路由器的泛型 SOAP 中介。</span><span class="sxs-lookup"><span data-stu-id="acd58-103">The Routing Service is a generic SOAP intermediary that acts as a message router.</span></span> <span data-ttu-id="acd58-104">路由服务的核心功能是基于消息内容来路由消息，通过该功能，可基于消息本身（标头或消息正文）中的值将消息转发到客户端终结点。</span><span class="sxs-lookup"><span data-stu-id="acd58-104">The core functionality of the Routing Service is the ability to route messages based on message content, which allows a message to be forwarded to a client endpoint based on a value within the message itself, in either the header or the message body.</span></span>

<span data-ttu-id="acd58-105"><xref:System.ServiceModel.Routing.RoutingService>作为命名空间中的 Windows Communication Foundation （WCF）服务实现 <xref:System.ServiceModel.Routing> 。</span><span class="sxs-lookup"><span data-stu-id="acd58-105">The <xref:System.ServiceModel.Routing.RoutingService> is implemented as a Windows Communication Foundation (WCF) service in the <xref:System.ServiceModel.Routing> namespace.</span></span> <span data-ttu-id="acd58-106">路由服务公开一个或多个用于接收消息的服务终结点，然后基于消息内容将每个消息路由到一个或多个客户端终结点。</span><span class="sxs-lookup"><span data-stu-id="acd58-106">The Routing Service exposes one or more service endpoints that receive messages and then routes each message to one or more client endpoints based on the message content.</span></span> <span data-ttu-id="acd58-107">该服务提供了以下功能：</span><span class="sxs-lookup"><span data-stu-id="acd58-107">The service provides the following features:</span></span>

- <span data-ttu-id="acd58-108">基于内容的路由</span><span class="sxs-lookup"><span data-stu-id="acd58-108">Content-based routing</span></span>

  - <span data-ttu-id="acd58-109">服务聚合</span><span class="sxs-lookup"><span data-stu-id="acd58-109">Service aggregation</span></span>

  - <span data-ttu-id="acd58-110">服务版本控制</span><span class="sxs-lookup"><span data-stu-id="acd58-110">Service versioning</span></span>

  - <span data-ttu-id="acd58-111">优先级路由</span><span class="sxs-lookup"><span data-stu-id="acd58-111">Priority routing</span></span>

  - <span data-ttu-id="acd58-112">动态配置</span><span class="sxs-lookup"><span data-stu-id="acd58-112">Dynamic configuration</span></span>

- <span data-ttu-id="acd58-113">协议桥接</span><span class="sxs-lookup"><span data-stu-id="acd58-113">Protocol bridging</span></span>

- <span data-ttu-id="acd58-114">SOAP 处理</span><span class="sxs-lookup"><span data-stu-id="acd58-114">SOAP processing</span></span>

- <span data-ttu-id="acd58-115">高级错误处理</span><span class="sxs-lookup"><span data-stu-id="acd58-115">Advanced error handling</span></span>

- <span data-ttu-id="acd58-116">备份终结点</span><span class="sxs-lookup"><span data-stu-id="acd58-116">Backup endpoints</span></span>

<span data-ttu-id="acd58-117">尽管可以创建可实现上述一个或多个目标的中介服务，但是此实现通常与特定方案或解决方案相关，并且不能轻松应用于新应用程序。</span><span class="sxs-lookup"><span data-stu-id="acd58-117">While it is possible to create an intermediary service that accomplishes one or more of these goals, often such an implementation is tied to a specific scenario or solution and cannot be readily applied to new applications.</span></span>

<span data-ttu-id="acd58-118">路由服务提供一个可动态配置的泛型可插入 SOAP 中介，与 WCF 服务和通道模型兼容，并允许您对基于 SOAP 的消息执行基于内容的路由。</span><span class="sxs-lookup"><span data-stu-id="acd58-118">The Routing Service provides a generic, dynamically configurable, pluggable SOAP intermediary that is compatible with the WCF Service and Channel models and allows you to perform content-based routing of SOAP-based messages.</span></span>

> [!NOTE]
> <span data-ttu-id="acd58-119">路由服务当前不支持路由 WCF REST 服务。</span><span class="sxs-lookup"><span data-stu-id="acd58-119">The Routing Service does not currently support routing of WCF REST services.</span></span>  <span data-ttu-id="acd58-120">若要路由 REST 调用，请考虑使用 <xref:System.Web.Routing> 或[应用程序请求路由](https://go.microsoft.com/fwlink/?LinkId=164589)。</span><span class="sxs-lookup"><span data-stu-id="acd58-120">To route REST calls, consider using <xref:System.Web.Routing> or [Application Request Routing](https://go.microsoft.com/fwlink/?LinkId=164589).</span></span>

## <a name="content-based-routing"></a><span data-ttu-id="acd58-121">基于内容的路由</span><span class="sxs-lookup"><span data-stu-id="acd58-121">Content-Based Routing</span></span>

<span data-ttu-id="acd58-122">基于内容的路由是指根据消息中包含的一个或多个值路由消息的能力。</span><span class="sxs-lookup"><span data-stu-id="acd58-122">Content-based routing is the ability to route a message based on one or more values contained within the message.</span></span> <span data-ttu-id="acd58-123">路由服务检查每条消息，并根据消息内容和您创建的路由逻辑将其路由至目标终结点。</span><span class="sxs-lookup"><span data-stu-id="acd58-123">The Routing Service inspects each message and routes it to the destination endpoint based on the message contents and the routing logic you create.</span></span> <span data-ttu-id="acd58-124">基于内容的路由为服务聚合、服务版本控制和优先级路由提供了基础。</span><span class="sxs-lookup"><span data-stu-id="acd58-124">Content-based routing provides the basis for service aggregation, service versioning, and priority routing.</span></span>

<span data-ttu-id="acd58-125">路由服务依赖于 <xref:System.ServiceModel.Dispatcher.MessageFilter> 实现来完成基于内容的路由，此类实现用于匹配要路由的消息中的特定值。</span><span class="sxs-lookup"><span data-stu-id="acd58-125">To implement content-based routing, the Routing Service relies on <xref:System.ServiceModel.Dispatcher.MessageFilter> implementations that are used to match specific values within the messages to be routed.</span></span> <span data-ttu-id="acd58-126">如果**MessageFilter**与消息相匹配，则会将消息路由到与**MessageFilter**关联的目标终结点。</span><span class="sxs-lookup"><span data-stu-id="acd58-126">If a **MessageFilter** matches a message, the message is routed to the destination endpoint associated with the **MessageFilter**.</span></span>  <span data-ttu-id="acd58-127">将若干个消息筛选器一起组合成筛选器表 (<xref:System.ServiceModel.Routing.Configuration.FilterTableCollection>) 可以构造复杂的路由逻辑。</span><span class="sxs-lookup"><span data-stu-id="acd58-127">Message filters are grouped together into filter tables (<xref:System.ServiceModel.Routing.Configuration.FilterTableCollection>) to construct complex routing logic.</span></span> <span data-ttu-id="acd58-128">例如，一个筛选器表可能包含五个互相排斥的消息筛选器，这会导致只将消息路由到五个目标终结点中的一个。</span><span class="sxs-lookup"><span data-stu-id="acd58-128">For example, a filter table might contain five mutually exclusive message filters that cause messages to be routed to only one of the five destination endpoints.</span></span>

<span data-ttu-id="acd58-129">路由服务允许您配置执行基于内容的路由所采用的逻辑，并在运行时动态更新路由逻辑。</span><span class="sxs-lookup"><span data-stu-id="acd58-129">The Routing Service allows you to configure the logic that is used to perform content-based routing, as well as dynamically update the routing logic at run time.</span></span>

<span data-ttu-id="acd58-130">通过将消息筛选器组合到筛选器表，您可以构造路由逻辑来处理如下所示的多个路由方案：</span><span class="sxs-lookup"><span data-stu-id="acd58-130">Through the grouping of message filters into filter tables, routing logic can be constructed that allows you to handle multiple routing scenarios such as:</span></span>

- <span data-ttu-id="acd58-131">服务聚合</span><span class="sxs-lookup"><span data-stu-id="acd58-131">Service aggregation</span></span>

- <span data-ttu-id="acd58-132">服务版本控制</span><span class="sxs-lookup"><span data-stu-id="acd58-132">Service versioning</span></span>

- <span data-ttu-id="acd58-133">优先级路由</span><span class="sxs-lookup"><span data-stu-id="acd58-133">Priority routing</span></span>

- <span data-ttu-id="acd58-134">动态配置</span><span class="sxs-lookup"><span data-stu-id="acd58-134">Dynamic configuration</span></span>

<span data-ttu-id="acd58-135">有关消息筛选器和筛选器表的详细信息，请参阅[路由介绍](routing-introduction.md)和[消息筛选](message-filters.md)器。</span><span class="sxs-lookup"><span data-stu-id="acd58-135">For more information about message filters and filter tables, see [Routing Introduction](routing-introduction.md) and [Message Filters](message-filters.md).</span></span>

### <a name="service-aggregation"></a><span data-ttu-id="acd58-136">服务聚合</span><span class="sxs-lookup"><span data-stu-id="acd58-136">Service Aggregation</span></span>

<span data-ttu-id="acd58-137">使用基于内容的路由，您可以公开一个用于接收外部客户端应用程序发送的消息的终结点，然后基于消息中的值将每条消息路由到相应的内部终结点。</span><span class="sxs-lookup"><span data-stu-id="acd58-137">By using content-based routing, you can expose one endpoint that receives messages from external client applications and then routes each message to the appropriate internal endpoint based on a value within the message.</span></span> <span data-ttu-id="acd58-138">这有助于为各种后端应用程序提供一个特定终结点，同时也有助于在将应用程序分解为各种服务时向客户提供一个应用程序终结点。</span><span class="sxs-lookup"><span data-stu-id="acd58-138">This is useful to offer one specific endpoint for a variety of back-end applications, and also to present one application endpoint to customers while factoring your application into a variety of services.</span></span>

### <a name="service-versioning"></a><span data-ttu-id="acd58-139">服务版本控制</span><span class="sxs-lookup"><span data-stu-id="acd58-139">Service Versioning</span></span>

<span data-ttu-id="acd58-140">当迁移到新版解决方案时，您可能需要并行维护旧版本，以便向现有客户提供服务。</span><span class="sxs-lookup"><span data-stu-id="acd58-140">When migrating to a new version of your solution, you may have to maintain the old version in parallel to serve existing customers.</span></span> <span data-ttu-id="acd58-141">通常，这要求连接到较新版本的客户端在与解决方案通信时必须使用不同的地址。</span><span class="sxs-lookup"><span data-stu-id="acd58-141">Often this requires that clients connecting to the newer version must use a different address when communicating with the solution.</span></span> <span data-ttu-id="acd58-142">路由服务允许您根据消息中包含的版本特定信息将消息路由至相应解决方案，从而公开一个可为解决方案的两个版本提供服务的服务终结点。</span><span class="sxs-lookup"><span data-stu-id="acd58-142">The Routing Service allows you to expose one service endpoint that serves both versions of your solution by routing messages to the appropriate solution based on version-specific information contained in the message.</span></span> <span data-ttu-id="acd58-143">有关此类实现的示例，请参阅[如何：服务版本控制](how-to-service-versioning.md)。</span><span class="sxs-lookup"><span data-stu-id="acd58-143">For an example of such an implementation see [How To: Service Versioning](how-to-service-versioning.md).</span></span>

### <a name="priority-routing"></a><span data-ttu-id="acd58-144">优先级路由</span><span class="sxs-lookup"><span data-stu-id="acd58-144">Priority Routing</span></span>

<span data-ttu-id="acd58-145">向多个客户端提供服务时，您可以与某些合作伙伴达成服务级别协议 (SLA)，该协议要求对来自这些合作伙伴的所有数据与其他客户端数据单独处理。</span><span class="sxs-lookup"><span data-stu-id="acd58-145">When providing a service for multiple clients, you may have a service level agreement (SLA) with some partners that requires all data from these partners to be processed separately from that of other clients.</span></span> <span data-ttu-id="acd58-146">使用查找消息中包含的客户特定信息的筛选器，您可以轻松地将来自特定合作伙伴的消息路由至为满足其 SLA 需求而创建的终结点。</span><span class="sxs-lookup"><span data-stu-id="acd58-146">By using a filter that looks for customer-specific information contained in the message, you can easily route messages from specific partners to an endpoint that has been created to meet their SLA requirements.</span></span>

## <a name="dynamic-configuration"></a><span data-ttu-id="acd58-147">动态配置</span><span class="sxs-lookup"><span data-stu-id="acd58-147">Dynamic Configuration</span></span>

<span data-ttu-id="acd58-148">若要支持任务关键型系统（在其中处理消息时不得出现任何服务中断），能够在运行时修改系统中组件的配置非常重要。</span><span class="sxs-lookup"><span data-stu-id="acd58-148">To support mission-critical systems, where messages must be processed without any service interruptions, it is vital that you be able to modify the configuration of components within the system at run time.</span></span> <span data-ttu-id="acd58-149">为了支持此需求，路由服务提供了一种 <xref:System.ServiceModel.IExtension%601> 实现（即 <xref:System.ServiceModel.Routing.RoutingExtension>），该实现允许在运行时动态更新路由服务的配置。</span><span class="sxs-lookup"><span data-stu-id="acd58-149">To support this need, the Routing Service provides an <xref:System.ServiceModel.IExtension%601> implementation, the <xref:System.ServiceModel.Routing.RoutingExtension>, which allows dynamic updating of the Routing Service configuration at run time.</span></span>

<span data-ttu-id="acd58-150">有关路由服务的动态配置的详细信息，请参阅[路由简介](routing-introduction.md)。</span><span class="sxs-lookup"><span data-stu-id="acd58-150">For more information about dynamic configuration of the Routing Service, see [Routing Introduction](routing-introduction.md).</span></span>

## <a name="protocol-bridging"></a><span data-ttu-id="acd58-151">协议桥接</span><span class="sxs-lookup"><span data-stu-id="acd58-151">Protocol Bridging</span></span>

<span data-ttu-id="acd58-152">中介方案面临的挑战之一是：内部终结点与接收消息的终结点可能具有不同的传输或 SOAP 版本要求。</span><span class="sxs-lookup"><span data-stu-id="acd58-152">One of the challenges in intermediary scenarios is that the internal endpoints may have different transport or SOAP version requirements than the endpoint that messages are received on.</span></span> <span data-ttu-id="acd58-153">若要支持此方案，路由服务可以桥接协议，包括根据目标终结点需要的 <xref:System.ServiceModel.Channels.MessageVersion> 处理 SOAP 消息。</span><span class="sxs-lookup"><span data-stu-id="acd58-153">To support this scenario, the Routing Service can bridge protocols, including processing the SOAP message to the <xref:System.ServiceModel.Channels.MessageVersion> required by the destination endpoint(s).</span></span> <span data-ttu-id="acd58-154">这样，一个协议可用于内部通信，而其他协议可用于外部通信。</span><span class="sxs-lookup"><span data-stu-id="acd58-154">In this way, one protocol can be used for internal communication, while another can be used for external communication.</span></span>

<span data-ttu-id="acd58-155">为了支持在具有不同传输方式的终结点之间路由消息，路由服务使用系统提供的绑定，这些绑定使服务可以起到不同协议之间的桥梁的作用。</span><span class="sxs-lookup"><span data-stu-id="acd58-155">To support the routing of messages between endpoints with different transports, the Routing Service uses system-provided bindings that enable the service to bridge dissimilar protocols.</span></span> <span data-ttu-id="acd58-156">如果路由服务公开的服务终结点与消息路由到的客户端终结点使用的协议不同，这种情况将自动发生。</span><span class="sxs-lookup"><span data-stu-id="acd58-156">This occurs automatically when the service endpoint exposed by the Routing Service uses a different protocol than the client endpoints that messages are routed to.</span></span>

## <a name="soap-processing"></a><span data-ttu-id="acd58-157">SOAP 处理</span><span class="sxs-lookup"><span data-stu-id="acd58-157">SOAP Processing</span></span>

<span data-ttu-id="acd58-158">常见路由要求是在具有不同 SOAP 要求的终结点之间路由消息。</span><span class="sxs-lookup"><span data-stu-id="acd58-158">A common routing requirement is the ability to route messages between endpoints with differing SOAP requirements.</span></span> <span data-ttu-id="acd58-159">为了支持此要求，路由服务提供了一个 <xref:System.ServiceModel.Routing.SoapProcessingBehavior> ，它会在消息路由到目标终结点之前自动创建满足目标终结点的要求的新**MessageVersion** 。</span><span class="sxs-lookup"><span data-stu-id="acd58-159">To support this requirement, the Routing Service provides a <xref:System.ServiceModel.Routing.SoapProcessingBehavior> that automatically creates a new **MessageVersion** that meets the requirements of the destination endpoint before the message is routed to it.</span></span> <span data-ttu-id="acd58-160">此行为还会在将响应消息返回给发出请求的客户端应用程序之前为任何响应消息创建新的**MessageVersion** ，以确保响应的 MessageVersion 与原始请求的**MessageVersion**相匹配。</span><span class="sxs-lookup"><span data-stu-id="acd58-160">This behavior also creates a new **MessageVersion** for any response message before returning it to the requesting client application, to ensure that the **MessageVersion** of the response matches that of the original request.</span></span>

<span data-ttu-id="acd58-161">有关 SOAP 处理的详细信息，请参阅[路由简介](routing-introduction.md)。</span><span class="sxs-lookup"><span data-stu-id="acd58-161">For more information about SOAP processing, see [Routing Introduction](routing-introduction.md).</span></span>

## <a name="error-handling"></a><span data-ttu-id="acd58-162">错误处理</span><span class="sxs-lookup"><span data-stu-id="acd58-162">Error Handling</span></span>

<span data-ttu-id="acd58-163">在由依赖于网络通信的分布式服务组成的系统中，确保系统中的通信不受暂时网络故障的影响是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="acd58-163">In a system composed of distributed services that rely on network communications, it is important to ensure that communications within your system are resistant to transient network failures.</span></span>  <span data-ttu-id="acd58-164">路由服务会实现错误处理，这样您便可以处理多种通信故障情况。如果不处理这些故障，可能会导致服务中断。</span><span class="sxs-lookup"><span data-stu-id="acd58-164">The Routing Service implements error handling that allows you to handle many communication failure scenarios that might otherwise result in a service outage.</span></span>

<span data-ttu-id="acd58-165">如果路由服务在尝试发送消息时遇到 <xref:System.ServiceModel.CommunicationException>，将会进行错误处理。</span><span class="sxs-lookup"><span data-stu-id="acd58-165">If the Routing Service encounters a <xref:System.ServiceModel.CommunicationException> while attempting to send a message, error handling will take place.</span></span>  <span data-ttu-id="acd58-166">这些异常通常指示在尝试与定义的客户端终结点进行通信时遇到了问题，例如 <xref:System.ServiceModel.EndpointNotFoundException>、<xref:System.ServiceModel.ServerTooBusyException> 或 <xref:System.ServiceModel.CommunicationObjectFaultedException>。</span><span class="sxs-lookup"><span data-stu-id="acd58-166">These exceptions typically indicate that a problem was encountered while attempting to communicate with the defined client endpoint, such as an <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, or <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span></span>  <span data-ttu-id="acd58-167">发生**TimeoutException**时，错误处理代码还将捕获并尝试重试发送，这是不是派生自**CommunicationException**的另一个常见异常。</span><span class="sxs-lookup"><span data-stu-id="acd58-167">The error-handling code will also catch and attempt to retry sending when a **TimeoutException** occurs, which is another common exception that is not derived from **CommunicationException**.</span></span>

<span data-ttu-id="acd58-168">有关错误处理的详细信息，请参阅[路由简介](routing-introduction.md)。</span><span class="sxs-lookup"><span data-stu-id="acd58-168">For more information about error handling, see [Routing Introduction](routing-introduction.md).</span></span>

## <a name="backup-endpoints"></a><span data-ttu-id="acd58-169">备份终结点</span><span class="sxs-lookup"><span data-stu-id="acd58-169">Backup Endpoints</span></span>

<span data-ttu-id="acd58-170">除了与筛选器表中的每个筛选器定义关联的目标客户端终结点，您还可以创建在传输失败时将消息路由到的备份终结点的列表。</span><span class="sxs-lookup"><span data-stu-id="acd58-170">In addition to the destination client endpoints associated with each filter definition in the filter table, you can also create a list of backup endpoints that the message will be routed to in the event of a transmission failure.</span></span> <span data-ttu-id="acd58-171">如果为筛选器条目定义了备份列表，则一旦出现错误，路由服务会尝试将消息发送到列表中定义的第一个终结点。</span><span class="sxs-lookup"><span data-stu-id="acd58-171">If an error occurs and a backup list is defined for the filter entry, the Routing Service will attempt to send the message to the first endpoint defined in the list.</span></span> <span data-ttu-id="acd58-172">如果此传输尝试失败，路由服务将尝试发送到下一个终结点，并一直继续此过程，直到传输尝试成功、返回与传输无关的错误或者备份列表中的所有终结点都返回传输错误。</span><span class="sxs-lookup"><span data-stu-id="acd58-172">If this transmission attempt fails, the service will try the next endpoint, and continue this process until the transmission attempt succeeds, returns a non-transmission related error, or all endpoints in the backup list have returned a transmission error.</span></span>

<span data-ttu-id="acd58-173">有关备份终结点的详细信息，请参阅[路由简介](routing-introduction.md)和[消息筛选器](message-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="acd58-173">For more information about backup endpoints, see [Routing Introduction](routing-introduction.md) and [Message Filters](message-filters.md).</span></span>

## <a name="streaming"></a><span data-ttu-id="acd58-174">流式处理</span><span class="sxs-lookup"><span data-stu-id="acd58-174">Streaming</span></span>

<span data-ttu-id="acd58-175">如果你设置绑定以支持流式处理，则路由服务可以成功对消息进行流式处理。</span><span class="sxs-lookup"><span data-stu-id="acd58-175">The routing service can successfully stream messages if you set the binding to support streaming.</span></span>  <span data-ttu-id="acd58-176">但是，在某些情况下可能需要对消息进行缓冲：</span><span class="sxs-lookup"><span data-stu-id="acd58-176">However, there are some conditions under which messages may need to buffered:</span></span>

- <span data-ttu-id="acd58-177">多播（缓冲以创建更多消息副本）</span><span class="sxs-lookup"><span data-stu-id="acd58-177">Multicast (buffer to create additional message copies)</span></span>

- <span data-ttu-id="acd58-178">故障转移（缓冲以免消息需要发送到备份）</span><span class="sxs-lookup"><span data-stu-id="acd58-178">Failover (buffer in case the message needs to be sent to a backup)</span></span>

- <span data-ttu-id="acd58-179">System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly 为 false（缓冲以提供带有 MessageBuffer 的 MessageFilterTable，以便筛选器可以检查正文）</span><span class="sxs-lookup"><span data-stu-id="acd58-179">System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly is false (buffer to present the MessageFilterTable with a MessageBuffer so that filters can inspect the body)</span></span>

- <span data-ttu-id="acd58-180">动态配置</span><span class="sxs-lookup"><span data-stu-id="acd58-180">Dynamic configuration</span></span>

## <a name="see-also"></a><span data-ttu-id="acd58-181">另请参阅</span><span class="sxs-lookup"><span data-stu-id="acd58-181">See also</span></span>

- [<span data-ttu-id="acd58-182">路由简介</span><span class="sxs-lookup"><span data-stu-id="acd58-182">Routing Introduction</span></span>](routing-introduction.md)
- [<span data-ttu-id="acd58-183">路由协定</span><span class="sxs-lookup"><span data-stu-id="acd58-183">Routing Contracts</span></span>](routing-contracts.md)
- [<span data-ttu-id="acd58-184">消息筛选器</span><span class="sxs-lookup"><span data-stu-id="acd58-184">Message Filters</span></span>](message-filters.md)

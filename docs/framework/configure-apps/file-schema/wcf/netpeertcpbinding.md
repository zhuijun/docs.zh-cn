---
title: <netPeerTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: 5fe221c5ec6c51afb199b2c66eab9d72cdfd750b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556136"
---
# \<netPeerTcpBinding>
<span data-ttu-id="29235-101">为特定于对等通道的 TCP 消息定义绑定。</span><span class="sxs-lookup"><span data-stu-id="29235-101">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netPeerTcpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="29235-102">语法</span><span class="sxs-lookup"><span data-stu-id="29235-102">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding name="string"
           closeTimeout="TimeSpan"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           listenIPAddress="String"
           maxBufferPoolSize="integer"
           maxReceiveMessageSize="Integer"
           port="Integer">
    <security mode="None/Transport/Message/TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29235-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="29235-103">Attributes and Elements</span></span>  
 <span data-ttu-id="29235-104">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="29235-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29235-105">属性</span><span class="sxs-lookup"><span data-stu-id="29235-105">Attributes</span></span>  
  
|<span data-ttu-id="29235-106">属性</span><span class="sxs-lookup"><span data-stu-id="29235-106">Attribute</span></span>|<span data-ttu-id="29235-107">说明</span><span class="sxs-lookup"><span data-stu-id="29235-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="29235-108">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="29235-108">closeTimeout</span></span>|<span data-ttu-id="29235-109">一个 <xref:System.TimeSpan> 值，指定为完成关闭操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="29235-109">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="29235-110">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="29235-110">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="29235-111">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="29235-111">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="29235-112">listenIPAddress</span><span class="sxs-lookup"><span data-stu-id="29235-112">listenIPAddress</span></span>|<span data-ttu-id="29235-113">一个字符串，指定对等节点将在其上侦听 TCP 消息的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="29235-113">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="29235-114">默认值为 `null`。</span><span class="sxs-lookup"><span data-stu-id="29235-114">The default is `null`.</span></span>|  
|<span data-ttu-id="29235-115">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="29235-115">maxBufferPoolSize</span></span>|<span data-ttu-id="29235-116">一个整数，指定此绑定的最大缓冲池大小。</span><span class="sxs-lookup"><span data-stu-id="29235-116">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="29235-117">默认值为 524,288 字节 (512 \* 1024)。</span><span class="sxs-lookup"><span data-stu-id="29235-117">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="29235-118">Windows Communication Foundation (WCF) 的许多部件使用缓冲区。</span><span class="sxs-lookup"><span data-stu-id="29235-118">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="29235-119">每次使用缓冲区时，创建和销毁它们都将占用大量资源，而缓冲区的垃圾回收过程也是如此。</span><span class="sxs-lookup"><span data-stu-id="29235-119">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="29235-120">利用缓冲池，可以从缓冲池中获得缓冲区，使用缓冲区，然后在完成工作后将其返回给缓冲池。</span><span class="sxs-lookup"><span data-stu-id="29235-120">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="29235-121">这样就避免了创建和销毁缓冲区的系统开销。</span><span class="sxs-lookup"><span data-stu-id="29235-121">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="29235-122">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="29235-122">maxReceivedMessageSize</span></span>|<span data-ttu-id="29235-123">一个正整数，指定采用此绑定配置的通道上可以接收的最大消息大小（字节），包括消息头。</span><span class="sxs-lookup"><span data-stu-id="29235-123">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="29235-124">如果消息超出此限制，则发送方将收到 SOAP 错误。</span><span class="sxs-lookup"><span data-stu-id="29235-124">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="29235-125">接收方将删除该消息，并在跟踪日志中创建事件项。</span><span class="sxs-lookup"><span data-stu-id="29235-125">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="29235-126">默认值为 65536。</span><span class="sxs-lookup"><span data-stu-id="29235-126">The default is 65536.</span></span>|  
|<span data-ttu-id="29235-127">name</span><span class="sxs-lookup"><span data-stu-id="29235-127">name</span></span>|<span data-ttu-id="29235-128">一个包含绑定的配置名称的字符串。</span><span class="sxs-lookup"><span data-stu-id="29235-128">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="29235-129">因为此值用作绑定的标识，所以它应该是唯一的。</span><span class="sxs-lookup"><span data-stu-id="29235-129">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="29235-130">从 .NET Framework 4 开始，绑定和行为不需要具有名称。</span><span class="sxs-lookup"><span data-stu-id="29235-130">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="29235-131">有关默认配置和无值绑定和行为的详细信息，请参阅[WCF 服务的](../../../wcf/samples/simplified-configuration-for-wcf-services.md)[简化配置](../../../wcf/simplified-configuration.md)和简化配置。</span><span class="sxs-lookup"><span data-stu-id="29235-131">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="29235-132">openTimeout</span><span class="sxs-lookup"><span data-stu-id="29235-132">openTimeout</span></span>|<span data-ttu-id="29235-133">一个 <xref:System.TimeSpan> 值，指定为完成打开操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="29235-133">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="29235-134">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="29235-134">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="29235-135">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="29235-135">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="29235-136">port</span><span class="sxs-lookup"><span data-stu-id="29235-136">port</span></span>|<span data-ttu-id="29235-137">一个整数，指定此绑定将用于处理对等通道 TCP 消息的网络接口端口。</span><span class="sxs-lookup"><span data-stu-id="29235-137">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="29235-138">该值必须介于 <xref:System.Net.IPEndPoint.MinPort> 和 <xref:System.Net.IPEndPoint.MaxPort> 之间。</span><span class="sxs-lookup"><span data-stu-id="29235-138">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="29235-139">默认值为 0。</span><span class="sxs-lookup"><span data-stu-id="29235-139">The default is 0.</span></span>|  
|<span data-ttu-id="29235-140">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="29235-140">receiveTimeout</span></span>|<span data-ttu-id="29235-141">一个 <xref:System.TimeSpan> 值，指定为完成接收操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="29235-141">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="29235-142">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="29235-142">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="29235-143">默认值为 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="29235-143">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="29235-144">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="29235-144">sendTimeout</span></span>|<span data-ttu-id="29235-145">一个 <xref:System.TimeSpan> 值，指定为完成发送操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="29235-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="29235-146">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="29235-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="29235-147">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="29235-147">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29235-148">子元素</span><span class="sxs-lookup"><span data-stu-id="29235-148">Child Elements</span></span>  
  
|<span data-ttu-id="29235-149">元素</span><span class="sxs-lookup"><span data-stu-id="29235-149">Element</span></span>|<span data-ttu-id="29235-150">说明</span><span class="sxs-lookup"><span data-stu-id="29235-150">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="29235-151">定义可由采用此绑定配置的终结点进行处理的 SOAP 消息的复杂性约束。</span><span class="sxs-lookup"><span data-stu-id="29235-151">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="29235-152">此元素的类型为 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="29235-152">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<resolver>](resolver.md)|<span data-ttu-id="29235-153">指定一个对等解析程序，此绑定将使用该解析程序将对等网格 ID 解析为对等网格中节点的终结点 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="29235-153">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[\<security>](security-of-netpeerbinding.md)|<span data-ttu-id="29235-154">定义消息的安全设置。</span><span class="sxs-lookup"><span data-stu-id="29235-154">Defines the security settings for the message.</span></span> <span data-ttu-id="29235-155">此元素的类型为 <xref:System.ServiceModel.Configuration.PeerSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="29235-155">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="29235-156">父元素</span><span class="sxs-lookup"><span data-stu-id="29235-156">Parent Elements</span></span>  
  
|<span data-ttu-id="29235-157">元素</span><span class="sxs-lookup"><span data-stu-id="29235-157">Element</span></span>|<span data-ttu-id="29235-158">说明</span><span class="sxs-lookup"><span data-stu-id="29235-158">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="29235-159">此元素包含标准绑定和自定义绑定的集合。</span><span class="sxs-lookup"><span data-stu-id="29235-159">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29235-160">备注</span><span class="sxs-lookup"><span data-stu-id="29235-160">Remarks</span></span>  
 <span data-ttu-id="29235-161">此绑定为使用 TCP 上的对等传输创建对等应用程序或多方应用程序提供支持。</span><span class="sxs-lookup"><span data-stu-id="29235-161">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="29235-162">每个对等节点均可承载使用此绑定类型定义的多个对等通道。</span><span class="sxs-lookup"><span data-stu-id="29235-162">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29235-163">示例</span><span class="sxs-lookup"><span data-stu-id="29235-163">Example</span></span>  
 <span data-ttu-id="29235-164">下面的示例演示如何使用 NetPeerTcpBinding 绑定，该绑定使用对等通道提供多方通信。</span><span class="sxs-lookup"><span data-stu-id="29235-164">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="29235-165">有关使用此绑定的详细方案，请参阅 [Net 对等 TCP](/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="29235-165">For a detailed scenario of using this binding, see [Net Peer TCP](/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <netPeerBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 maxBufferSize="1001"
                 maxConnections="123"
                 maxReceiveMessageSize="1000">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="TransportWithMessageCredential">
            <message clientCredentialType="CardSpace" />
          </security>
        </binding>
      </netPeerBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="29235-166">请参阅</span><span class="sxs-lookup"><span data-stu-id="29235-166">See also</span></span>

- <xref:System.ServiceModel.NetPeerTcpBinding>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>
- [<span data-ttu-id="29235-167">绑定</span><span class="sxs-lookup"><span data-stu-id="29235-167">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="29235-168">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="29235-168">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="29235-169">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="29235-169">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- <span data-ttu-id="29235-170">[网络对等 TCP](/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="29235-170">[Net Peer TCP](/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span></span>
- [<span data-ttu-id="29235-171">对等网络</span><span class="sxs-lookup"><span data-stu-id="29235-171">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)

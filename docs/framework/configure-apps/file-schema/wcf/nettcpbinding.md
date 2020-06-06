---
title: <netTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netTcpBinding Element
ms.assetid: 5c5104a7-8754-4335-8233-46a45322503e
ms.openlocfilehash: c43c141093c8287adb6d5a841a43ac893deefccd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139340"
---
# \<netTcpBinding>

<span data-ttu-id="75fa6-101">指定一种适合于跨计算机通信的安全、可靠且进行了优化的绑定。</span><span class="sxs-lookup"><span data-stu-id="75fa6-101">Specifies a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="75fa6-102">默认情况下，它会生成一个运行时通信堆栈，该堆栈包含 Windows Security 以保证消息安全性和进行身份验证，包含 TCP 以便进行消息传递，并且包含二进制消息编码机制。</span><span class="sxs-lookup"><span data-stu-id="75fa6-102">By default, it generates a runtime communication stack with Windows Security for message security and authentication, TCP for message delivery, and binary message encoding.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netTcpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="75fa6-103">语法</span><span class="sxs-lookup"><span data-stu-id="75fa6-103">Syntax</span></span>  
  
```xml  
<netTcpBinding>
  <binding closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           listenBacklog="Integer"
           maxBufferPoolSize="integer"
           maxBufferSize="Integer"
           maxConnections="Integer"
           maxReceivedMessageSize="Integer"
           name="string"
           openTimeout="TimeSpan"
           portSharingEnabled="Boolean"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transactionFlow="Boolean"
           transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="None/Transport/Message/Both">
      <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />
      <transport clientCredentialType="None/Windows/Certificate"
                 protectionLevel="None/Sign/EncryptAndSign" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75fa6-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="75fa6-104">Attributes and elements</span></span>

<span data-ttu-id="75fa6-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="75fa6-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75fa6-106">特性</span><span class="sxs-lookup"><span data-stu-id="75fa6-106">Attributes</span></span>  
  
|<span data-ttu-id="75fa6-107">属性</span><span class="sxs-lookup"><span data-stu-id="75fa6-107">Attribute</span></span>|<span data-ttu-id="75fa6-108">说明</span><span class="sxs-lookup"><span data-stu-id="75fa6-108">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="75fa6-109">一个 <xref:System.TimeSpan> 值，指定为完成关闭操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="75fa6-109">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="75fa6-110">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="75fa6-110">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="75fa6-111">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="75fa6-111">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="75fa6-112">指定用于分析 URI 的 HTTP 主机名比较模式。</span><span class="sxs-lookup"><span data-stu-id="75fa6-112">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="75fa6-113">此属性的类型为 <xref:System.ServiceModel.HostNameComparisonMode>，指示在对 URI 进行匹配时，是否使用主机名来访问服务。</span><span class="sxs-lookup"><span data-stu-id="75fa6-113">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="75fa6-114">默认值为 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>，表示忽略匹配项中的主机名。</span><span class="sxs-lookup"><span data-stu-id="75fa6-114">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`listenBacklog`|<span data-ttu-id="75fa6-115">一个正整数，指定侦听器上等待接受的最大通道数。</span><span class="sxs-lookup"><span data-stu-id="75fa6-115">A positive integer that specifies the maximum number of channels waiting to be accepted on the listener.</span></span> <span data-ttu-id="75fa6-116">超出此限制的连接会被排队，直到连接数低于限制值。</span><span class="sxs-lookup"><span data-stu-id="75fa6-116">Connections in excess of this limit are queued until space below the limit becomes available.</span></span> <span data-ttu-id="75fa6-117">`connectionTimeout` 属性限制客户端在引发连接异常之前将等待连接的时间。</span><span class="sxs-lookup"><span data-stu-id="75fa6-117">The `connectionTimeout` attribute limits the time a client will wait to be connected before throwing a connection exception.</span></span> <span data-ttu-id="75fa6-118">默认值为 10。</span><span class="sxs-lookup"><span data-stu-id="75fa6-118">The default is 10.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="75fa6-119">一个整数，指定此绑定的最大缓冲池大小。</span><span class="sxs-lookup"><span data-stu-id="75fa6-119">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="75fa6-120">默认值为 512 \* 1024 字节。</span><span class="sxs-lookup"><span data-stu-id="75fa6-120">The default is 512 \* 1024 bytes.</span></span> <span data-ttu-id="75fa6-121">Windows Communication Foundation (WCF) 的许多部件使用缓冲区。</span><span class="sxs-lookup"><span data-stu-id="75fa6-121">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="75fa6-122">每次使用缓冲区时，创建和销毁它们都将占用大量资源，而缓冲区的垃圾回收过程也是如此。</span><span class="sxs-lookup"><span data-stu-id="75fa6-122">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="75fa6-123">利用缓冲池，可以从缓冲池中获得缓冲区，使用缓冲区，然后在完成工作后将其返回给缓冲池。</span><span class="sxs-lookup"><span data-stu-id="75fa6-123">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="75fa6-124">这样就避免了创建和销毁缓冲区的系统开销。</span><span class="sxs-lookup"><span data-stu-id="75fa6-124">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="75fa6-125">一个正整数，指定内存中用于存储消息的缓冲区的最大大小（字节）。</span><span class="sxs-lookup"><span data-stu-id="75fa6-125">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span><br /><br /> <span data-ttu-id="75fa6-126">如果 `transferMode` 属性等于 `Buffered`，则此属性应等于 `maxReceivedMessageSize` 属性值。</span><span class="sxs-lookup"><span data-stu-id="75fa6-126">If the `transferMode` attribute equals to `Buffered`, this attribute should be equal to the `maxReceivedMessageSize` attribute value.</span></span><br /><br /> <span data-ttu-id="75fa6-127">如果 `transferMode` 属性等于 `Streamed`，则此属性不能大于 `maxReceivedMessageSize` 属性值，应当至少为标头的大小。</span><span class="sxs-lookup"><span data-stu-id="75fa6-127">If the `transferMode` attribute equals to `Streamed`, this attribute cannot be more than the `maxReceivedMessageSize` attribute value, and should be at least the size of the headers.</span></span><br /><br /> <span data-ttu-id="75fa6-128">默认值为 65536。</span><span class="sxs-lookup"><span data-stu-id="75fa6-128">The default is 65536.</span></span> <span data-ttu-id="75fa6-129">有关详细信息，请参阅 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>。</span><span class="sxs-lookup"><span data-stu-id="75fa6-129">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|`maxConnections`|<span data-ttu-id="75fa6-130">一个整数，指定服务将创建/接受的最大出站和入站连接数。</span><span class="sxs-lookup"><span data-stu-id="75fa6-130">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="75fa6-131">传入和传出连接分别根据此属性指定的限制进行计数。</span><span class="sxs-lookup"><span data-stu-id="75fa6-131">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="75fa6-132">超出此限制的入站连接需要排队，直到连接数低于限制值。</span><span class="sxs-lookup"><span data-stu-id="75fa6-132">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="75fa6-133">超出此限制的出站连接需要排队，直到连接数低于限制值。</span><span class="sxs-lookup"><span data-stu-id="75fa6-133">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="75fa6-134">默认值为 10。</span><span class="sxs-lookup"><span data-stu-id="75fa6-134">The default is 10.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="75fa6-135">一个正整数，指定采用此绑定配置的通道上可以接收的最大消息大小（字节），包括消息头。</span><span class="sxs-lookup"><span data-stu-id="75fa6-135">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="75fa6-136">如果消息超出此限制，则发送方将收到 SOAP 错误。</span><span class="sxs-lookup"><span data-stu-id="75fa6-136">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="75fa6-137">接收方将删除该消息，并在跟踪日志中创建事件项。</span><span class="sxs-lookup"><span data-stu-id="75fa6-137">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="75fa6-138">默认值为 65536。</span><span class="sxs-lookup"><span data-stu-id="75fa6-138">The default is 65536.</span></span>|  
|`name`|<span data-ttu-id="75fa6-139">一个包含绑定的配置名称的字符串。</span><span class="sxs-lookup"><span data-stu-id="75fa6-139">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="75fa6-140">因为此值用作绑定的标识，所以它应该是唯一的。</span><span class="sxs-lookup"><span data-stu-id="75fa6-140">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="75fa6-141">从 .NET Framework 4 开始，绑定和行为不需要具有名称。</span><span class="sxs-lookup"><span data-stu-id="75fa6-141">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="75fa6-142">有关默认配置和无值绑定和行为的详细信息，请参阅[WCF 服务的](../../../wcf/samples/simplified-configuration-for-wcf-services.md)[简化配置](../../../wcf/simplified-configuration.md)和简化配置。</span><span class="sxs-lookup"><span data-stu-id="75fa6-142">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="75fa6-143">一个 <xref:System.TimeSpan> 值，指定为完成打开操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="75fa6-143">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="75fa6-144">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="75fa6-144">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="75fa6-145">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="75fa6-145">The default is 00:01:00.</span></span>|  
|`portSharingEnabled`|<span data-ttu-id="75fa6-146">一个布尔值，指定是否为此连接启用 TCP 端口共享。</span><span class="sxs-lookup"><span data-stu-id="75fa6-146">A Boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span> <span data-ttu-id="75fa6-147">如果此值为 `false`，则每个绑定都使用自己的独占端口。</span><span class="sxs-lookup"><span data-stu-id="75fa6-147">If this is `false`, each binding uses its own exclusive port.</span></span> <span data-ttu-id="75fa6-148">此设置只与服务相关，因为客户端不受影响。</span><span class="sxs-lookup"><span data-stu-id="75fa6-148">This setting is relevant only to services, because clients are not affected.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="75fa6-149">一个 <xref:System.TimeSpan> 值，指定为完成接收操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="75fa6-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="75fa6-150">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="75fa6-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="75fa6-151">默认值为 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="75fa6-151">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="75fa6-152">一个 <xref:System.TimeSpan> 值，指定为完成发送操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="75fa6-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="75fa6-153">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="75fa6-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="75fa6-154">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="75fa6-154">The default is 00:01:00.</span></span>|  
|`transactionFlow`|<span data-ttu-id="75fa6-155">一个布尔值，指定绑定是否支持流动 WS-Transactions。</span><span class="sxs-lookup"><span data-stu-id="75fa6-155">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="75fa6-156">默认为 `false`。</span><span class="sxs-lookup"><span data-stu-id="75fa6-156">The default is `false`.</span></span>|  
|`transactionProtocol`|<span data-ttu-id="75fa6-157">指定与此绑定一起使用的事务处理协议。</span><span class="sxs-lookup"><span data-stu-id="75fa6-157">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="75fa6-158">有效值为</span><span class="sxs-lookup"><span data-stu-id="75fa6-158">Valid values are</span></span><br /><br /> <span data-ttu-id="75fa6-159">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="75fa6-159">-   OleTransactions</span></span><br /><span data-ttu-id="75fa6-160">-WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="75fa6-160">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="75fa6-161">默认值为 OleTransactions。</span><span class="sxs-lookup"><span data-stu-id="75fa6-161">The default is OleTransactions.</span></span> <span data-ttu-id="75fa6-162">此属性的类型为 <xref:System.ServiceModel.TransactionProtocol>。</span><span class="sxs-lookup"><span data-stu-id="75fa6-162">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|`transferMode`|<span data-ttu-id="75fa6-163">一个 <xref:System.ServiceModel.TransferMode> 值，指定为请求或响应对消息进行缓冲处理还是流式处理。</span><span class="sxs-lookup"><span data-stu-id="75fa6-163">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="75fa6-164">子元素</span><span class="sxs-lookup"><span data-stu-id="75fa6-164">Child elements</span></span>  
  
|<span data-ttu-id="75fa6-165">元素</span><span class="sxs-lookup"><span data-stu-id="75fa6-165">Element</span></span>|<span data-ttu-id="75fa6-166">描述</span><span class="sxs-lookup"><span data-stu-id="75fa6-166">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nettcpbinding.md)|<span data-ttu-id="75fa6-167">定义绑定的安全设置。</span><span class="sxs-lookup"><span data-stu-id="75fa6-167">Defines the security settings for the binding.</span></span> <span data-ttu-id="75fa6-168">此元素的类型为 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="75fa6-168">This element is of type <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.</span></span>|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="75fa6-169">定义可由采用此绑定配置的终结点进行处理的 SOAP 消息的复杂性约束。</span><span class="sxs-lookup"><span data-stu-id="75fa6-169">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="75fa6-170">此元素的类型为 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="75fa6-170">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="75fa6-171">指定是否在通道终结点之间建立可靠会话。</span><span class="sxs-lookup"><span data-stu-id="75fa6-171">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="75fa6-172">父元素</span><span class="sxs-lookup"><span data-stu-id="75fa6-172">Parent elements</span></span>  
  
|<span data-ttu-id="75fa6-173">元素</span><span class="sxs-lookup"><span data-stu-id="75fa6-173">Element</span></span>|<span data-ttu-id="75fa6-174">描述</span><span class="sxs-lookup"><span data-stu-id="75fa6-174">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="75fa6-175">此元素包含标准绑定和自定义绑定的集合。</span><span class="sxs-lookup"><span data-stu-id="75fa6-175">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75fa6-176">注解</span><span class="sxs-lookup"><span data-stu-id="75fa6-176">Remarks</span></span>

<span data-ttu-id="75fa6-177">默认情况下，此绑定会生成一个运行时通信堆栈，该堆栈使用传输安全、用于消息传递的 TCP 和二进制消息编码机制。</span><span class="sxs-lookup"><span data-stu-id="75fa6-177">This binding generates a run-time communication stack by default, which uses transport security, TCP for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="75fa6-178">此绑定是适当的 Windows Communication Foundation （WCF）系统提供的选择，用于通过 Intranet 进行通信。</span><span class="sxs-lookup"><span data-stu-id="75fa6-178">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for communicating over an Intranet.</span></span>  
  
 <span data-ttu-id="75fa6-179">的默认配置 `netTcpBinding` 比提供的配置更快 `wsHttpBinding` ，但它仅适用于 WCF 通信。</span><span class="sxs-lookup"><span data-stu-id="75fa6-179">The default configuration for the `netTcpBinding` is faster than the configuration provided by the `wsHttpBinding`, but it is intended only for WCF communication.</span></span> <span data-ttu-id="75fa6-180">可以使用可选的 `securityMode` 属性配置安全行为。</span><span class="sxs-lookup"><span data-stu-id="75fa6-180">The security behavior is configurable using the optional `securityMode` attribute.</span></span> <span data-ttu-id="75fa6-181">使用可选的 `reliableSessionEnabled` 属性可以配置 WS-ReliableMessaging 的用法。</span><span class="sxs-lookup"><span data-stu-id="75fa6-181">The use of WS-ReliableMessaging is configurable using the optional `reliableSessionEnabled` attribute.</span></span> <span data-ttu-id="75fa6-182">但是在默认情况下可靠消息传递为关闭状态。</span><span class="sxs-lookup"><span data-stu-id="75fa6-182">But reliable messaging is off by default.</span></span> <span data-ttu-id="75fa6-183">一般来说，HTTP 系统提供的绑定（如 `wsHttpBinding` 和 `basicHttpBinding`）是默认配置为打开事项，而 `netTcpBinding` 绑定是默认配置为关闭事项，因此，你必须选择性加入所需事项才能获取支持，例如获取对一种 WS-\* 规范的支持。</span><span class="sxs-lookup"><span data-stu-id="75fa6-183">More generally, the HTTP system-provided bindings such as `wsHttpBinding` and `basicHttpBinding` are configured to turn things on by default, whereas the `netTcpBinding` binding turns things off by default so that you have to opt-in to get support, for example, for one of the WS-\* specifications.</span></span> <span data-ttu-id="75fa6-184">这意味着在终结点之间交换消息时，TCP 的默认配置比 HTTP 绑定的默认配置更快。</span><span class="sxs-lookup"><span data-stu-id="75fa6-184">This means that the default configuration for TCP is faster at exchanging messages between endpoints than those configured for the HTTP bindings by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75fa6-185">示例</span><span class="sxs-lookup"><span data-stu-id="75fa6-185">Example</span></span>

<span data-ttu-id="75fa6-186">绑定是在客户端和服务的配置文件中指定的。</span><span class="sxs-lookup"><span data-stu-id="75fa6-186">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="75fa6-187">绑定类型是在 `binding` 元素的 `<endpoint>` 属性中指定的。</span><span class="sxs-lookup"><span data-stu-id="75fa6-187">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="75fa6-188">如果要配置 netTcpBinding 绑定并更改它的一些设置，则必须定义绑定配置。</span><span class="sxs-lookup"><span data-stu-id="75fa6-188">If you want to configure the netTcpBinding binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="75fa6-189">终结点必须使用 `bindingConfiguration` 特性来引用绑定配置。</span><span class="sxs-lookup"><span data-stu-id="75fa6-189">The endpoint must reference the binding configuration with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="75fa6-190">在下面的示例中，定义了一个绑定配置。</span><span class="sxs-lookup"><span data-stu-id="75fa6-190">In the following example, a binding configuration is defined.</span></span>  
  
```xml  
<services>
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    ...
    <endpoint address=""
              binding="netTcpBinding"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />
    ...
  </service>
</services>
<bindings>
  <netTcpBinding>
    <binding closeTimeout="00:01:00"
             openTimeout="00:01:00"
             receiveTimeout="00:10:00"
             sendTimeout="00:01:00"
             transactionFlow="false"
             transferMode="Buffered"
             transactionProtocol="OleTransactions"
             hostNameComparisonMode="StrongWildcard"
             listenBacklog="10"
             maxBufferPoolSize="524288"
             maxBufferSize="65536"
             maxConnections="10"
             maxReceivedMessageSize="65536">
      <readerQuotas maxDepth="32"
                    maxStringContentLength="8192"
                    maxArrayLength="16384"
                    maxBytesPerRead="4096"
                    maxNameTableCharCount="16384" />
      <reliableSession ordered="true"
                       inactivityTimeout="00:10:00"
                       enabled="false" />
      <security mode="Transport">
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign" />
      </security>
    </binding>
  </netTcpBinding>
</bindings>
```  
  
## <a name="see-also"></a><span data-ttu-id="75fa6-191">另请参阅</span><span class="sxs-lookup"><span data-stu-id="75fa6-191">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement>
- [<span data-ttu-id="75fa6-192">绑定</span><span class="sxs-lookup"><span data-stu-id="75fa6-192">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="75fa6-193">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="75fa6-193">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="75fa6-194">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="75fa6-194">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

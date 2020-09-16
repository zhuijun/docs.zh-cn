---
title: <wsDualHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsDualHttpBinding Element
ms.assetid: fd8ac4e2-5641-473b-9115-73f14ab1c065
ms.openlocfilehash: 3e32539900893297d2bac232138f9940a8ab100b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557640"
---
# \<wsDualHttpBinding>
<span data-ttu-id="0f1aa-101">定义一个安全可靠且可互操作的绑定，该绑定适合于双工服务协定或通过 SOAP 中介进行的通信。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-101">Defines a secure, reliable and interoperable binding that is suitable for duplex service contracts or communication through SOAP intermediaries.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsDualHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="0f1aa-102">语法</span><span class="sxs-lookup"><span data-stu-id="0f1aa-102">Syntax</span></span>  
  
```xml  
<wsDualHttpBinding>
  <binding name="String"
          closeTimeout="TimeSpan"
          openTimeout="TimeSpan"
          receiveTimeout="TimeSpan"
          sendTimeout="TimeSpan"
          bypassProxyOnLocal="Boolean"
          clientBaseAddress="URI"
          transactionFlow="Boolean"
          hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
          maxBufferPoolSize="integer"
          maxReceivedMessageSize="Integer"
          messageEncoding="Text/Mtom"
          proxyAddress="URI"
          textEncoding="Unicode/BigEndianUnicode/UTF8"
          useDefaultWebProxy="Boolean">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan" />
    <security mode="None/Message">
      <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</wsDualHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0f1aa-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="0f1aa-103">Attributes and Elements</span></span>  
 <span data-ttu-id="0f1aa-104">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0f1aa-105">属性</span><span class="sxs-lookup"><span data-stu-id="0f1aa-105">Attributes</span></span>  
  
|<span data-ttu-id="0f1aa-106">属性</span><span class="sxs-lookup"><span data-stu-id="0f1aa-106">Attribute</span></span>|<span data-ttu-id="0f1aa-107">说明</span><span class="sxs-lookup"><span data-stu-id="0f1aa-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0f1aa-108">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="0f1aa-108">bypassProxyOnLocal</span></span>|<span data-ttu-id="0f1aa-109">一个布尔值，指示是否对本地地址不使用代理服务器。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-109">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="0f1aa-110">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-110">The default is `false`.</span></span>|  
|<span data-ttu-id="0f1aa-111">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="0f1aa-111">clientBaseAddress</span></span>|<span data-ttu-id="0f1aa-112">一个 URI，设置客户端为接收来自服务的响应消息而侦听的基址。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-112">A URI that sets the base address that the client listens to for response messages from the service.</span></span> <span data-ttu-id="0f1aa-113">如果指定了此地址，则此地址（以及每个通道的 GUID）将用于侦听。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-113">If specified, this address (plus a per-channelGUID) is used for listening.</span></span> <span data-ttu-id="0f1aa-114">如果未指定此值，则将以传输特定的方式生成客户端基址。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-114">If the value is not specified, the client base address is generated in a transport-specific manner.</span></span> <span data-ttu-id="0f1aa-115">默认值为 `null`。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-115">The default is `null`.</span></span>|  
|<span data-ttu-id="0f1aa-116">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="0f1aa-116">closeTimeout</span></span>|<span data-ttu-id="0f1aa-117">一个 <xref:System.TimeSpan> 值，指定为完成关闭操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-117">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="0f1aa-118">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-118">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0f1aa-119">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-119">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="0f1aa-120">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="0f1aa-120">hostnameComparisonMode</span></span>|<span data-ttu-id="0f1aa-121">指定用于分析 URI 的 HTTP 主机名比较模式。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-121">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="0f1aa-122">此属性的类型为 <xref:System.ServiceModel.HostNameComparisonMode>，指示在对 URI 进行匹配时，是否使用主机名来访问服务。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-122">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="0f1aa-123">默认值为 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>，表示忽略匹配项中的主机名。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-123">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="0f1aa-124">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="0f1aa-124">maxBufferPoolSize</span></span>|<span data-ttu-id="0f1aa-125">一个整数，指定此绑定的最大缓冲池大小。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-125">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="0f1aa-126">默认值为 524,288 字节 (512 \* 1024)。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-126">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="0f1aa-127">Windows Communication Foundation (WCF) 的许多部件使用缓冲区。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-127">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="0f1aa-128">每次使用缓冲区时，创建和销毁它们都将占用大量资源，而缓冲区的垃圾回收过程也是如此。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-128">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="0f1aa-129">利用缓冲池，可以从缓冲池中获得缓冲区，使用缓冲区，然后在完成工作后将其返回给缓冲池。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-129">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="0f1aa-130">这样就避免了创建和销毁缓冲区的系统开销。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-130">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="0f1aa-131">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="0f1aa-131">maxReceivedMessageSize</span></span>|<span data-ttu-id="0f1aa-132">一个正整数，指定采用此绑定配置的通道上可以接收的最大消息大小（字节），包括消息头。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-132">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="0f1aa-133">如果消息超出此限制，则发送方将收到 SOAP 错误。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-133">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="0f1aa-134">接收方将删除该消息，并在跟踪日志中创建事件项。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-134">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="0f1aa-135">默认值为 65536。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-135">The default is 65536.</span></span>|  
|<span data-ttu-id="0f1aa-136">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="0f1aa-136">messageEncoding</span></span>|<span data-ttu-id="0f1aa-137">定义用于对消息进行编码的编码器。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-137">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="0f1aa-138">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="0f1aa-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0f1aa-139">-Text：使用文本消息编码器。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-139">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="0f1aa-140">-Mtom：使用消息传输组织机制 1.0 (MTOM) 编码器。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-140">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="0f1aa-141">-默认值为 Text。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-141">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="0f1aa-142">此属性的类型为 <xref:System.ServiceModel.WSMessageEncoding>。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-142">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="0f1aa-143">name</span><span class="sxs-lookup"><span data-stu-id="0f1aa-143">name</span></span>|<span data-ttu-id="0f1aa-144">一个包含绑定的配置名称的字符串。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-144">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="0f1aa-145">因为此值用作绑定的标识，所以它应该是唯一的。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-145">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="0f1aa-146">从 .NET Framework 4 开始，绑定和行为不需要具有名称。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-146">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="0f1aa-147">有关默认配置和无值绑定和行为的详细信息，请参阅[WCF 服务的](../../../wcf/samples/simplified-configuration-for-wcf-services.md)[简化配置](../../../wcf/simplified-configuration.md)和简化配置。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-147">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="0f1aa-148">openTimeout</span><span class="sxs-lookup"><span data-stu-id="0f1aa-148">openTimeout</span></span>|<span data-ttu-id="0f1aa-149">一个 <xref:System.TimeSpan> 值，指定为完成打开操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="0f1aa-150">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0f1aa-151">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-151">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="0f1aa-152">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="0f1aa-152">proxyAddress</span></span>|<span data-ttu-id="0f1aa-153">一个指定 HTTP 代理的地址的 URI。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-153">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="0f1aa-154">如果 `useDefaultWebProxy` 为 `true`，则此设置必须为 `null`。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-154">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="0f1aa-155">默认值为 `null`。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-155">The default is `null`.</span></span>|  
|<span data-ttu-id="0f1aa-156">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="0f1aa-156">receiveTimeout</span></span>|<span data-ttu-id="0f1aa-157">一个 <xref:System.TimeSpan> 值，指定为完成接收操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-157">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="0f1aa-158">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-158">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0f1aa-159">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-159">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="0f1aa-160">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="0f1aa-160">sendTimeout</span></span>|<span data-ttu-id="0f1aa-161">一个 <xref:System.TimeSpan> 值，指定为完成发送操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-161">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="0f1aa-162">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-162">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0f1aa-163">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-163">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="0f1aa-164">textEncoding</span><span class="sxs-lookup"><span data-stu-id="0f1aa-164">textEncoding</span></span>|<span data-ttu-id="0f1aa-165">设置要用来在绑定上发出消息的字符集编码。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-165">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="0f1aa-166">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="0f1aa-166">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0f1aa-167">-BigEndianUnicode： Unicode BigEndian 编码。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-167">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="0f1aa-168">-Unicode：16位编码。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-168">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="0f1aa-169">-UTF8：8位编码</span><span class="sxs-lookup"><span data-stu-id="0f1aa-169">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="0f1aa-170">默认编码为 UTF8。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-170">The default is UTF8.</span></span> <span data-ttu-id="0f1aa-171">此属性的类型为 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-171">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="0f1aa-172">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="0f1aa-172">transactionFlow</span></span>|<span data-ttu-id="0f1aa-173">一个布尔值，指定绑定是否支持流动 WS-Transactions。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-173">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="0f1aa-174">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-174">The default is `false`.</span></span>|  
|<span data-ttu-id="0f1aa-175">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="0f1aa-175">useDefaultWebProxy</span></span>|<span data-ttu-id="0f1aa-176">一个布尔值，指示是否使用系统的自动配置 HTTP 代理。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-176">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="0f1aa-177">如果此属性为 `null`，则代理地址必须为 `true`（即，不设置代理地址）。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-177">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="0f1aa-178">默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-178">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0f1aa-179">子元素</span><span class="sxs-lookup"><span data-stu-id="0f1aa-179">Child Elements</span></span>  
  
|<span data-ttu-id="0f1aa-180">元素</span><span class="sxs-lookup"><span data-stu-id="0f1aa-180">Element</span></span>|<span data-ttu-id="0f1aa-181">说明</span><span class="sxs-lookup"><span data-stu-id="0f1aa-181">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wsdualhttpbinding.md)|<span data-ttu-id="0f1aa-182">定义绑定的安全设置。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-182">Defines the security settings for the binding.</span></span> <span data-ttu-id="0f1aa-183">此元素的类型为 <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-183">This element is of type <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement>.</span></span>|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="0f1aa-184">定义可由采用此绑定配置的终结点进行处理的 SOAP 消息的复杂性约束。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-184">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="0f1aa-185">此元素的类型为 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-185">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<reliableSession>](/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="0f1aa-186">指定是否在通道终结点之间建立可靠会话。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-186">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0f1aa-187">父元素</span><span class="sxs-lookup"><span data-stu-id="0f1aa-187">Parent Elements</span></span>  
  
|<span data-ttu-id="0f1aa-188">元素</span><span class="sxs-lookup"><span data-stu-id="0f1aa-188">Element</span></span>|<span data-ttu-id="0f1aa-189">说明</span><span class="sxs-lookup"><span data-stu-id="0f1aa-189">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="0f1aa-190">此元素包含标准绑定和自定义绑定的集合。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-190">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f1aa-191">备注</span><span class="sxs-lookup"><span data-stu-id="0f1aa-191">Remarks</span></span>  
 <span data-ttu-id="0f1aa-192">`WSDualHttpBinding` 提供与 `WSHttpBinding` 相同的 Web 服务协议支持，但用于双工协定。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-192">The `WSDualHttpBinding` provides the same support for Web Service protocols as the `WSHttpBinding`, but for use with duplex contracts.</span></span> <span data-ttu-id="0f1aa-193">`WSDualHttpBinding` 仅支持 SOAP 安全，且需要可靠的消息传递。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-193">`WSDualHttpBinding` only supports SOAP security and requires reliable messaging.</span></span> <span data-ttu-id="0f1aa-194">此绑定要求客户端具有可为服务提供回调终结点的公共 URI。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-194">This binding requires that the client has a public URI that provides a callback endpoint for the service.</span></span> <span data-ttu-id="0f1aa-195">此元素由 `clientBaseAddress` 属性提供。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-195">This is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="0f1aa-196">双向绑定向服务公开客户端的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-196">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="0f1aa-197">客户端应使用安全来确保仅连接到自己信任的服务。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-197">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
 <span data-ttu-id="0f1aa-198">此绑定可用于通过一个或多个 SOAP 媒介可靠地进行通信。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-198">This binding can be used to communicate reliably through one or more SOAP intermediaries.</span></span>  
  
 <span data-ttu-id="0f1aa-199">默认情况下，此绑定会生成一个运行时堆栈，该堆栈包含 WS-ReliableMessaging 以保证可靠性，包含 WS-Security 以保证消息安全性和进行身份验证，包含 HTTP 以便进行消息传递，并且包含 Text/XML 消息编码功能。</span><span class="sxs-lookup"><span data-stu-id="0f1aa-199">By default, this binding generates a runtime stack with WS-ReliableMessaging for reliability, WS-Security for message security and authentication, HTTP for message delivery, and a Text/XML message encoding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f1aa-200">示例</span><span class="sxs-lookup"><span data-stu-id="0f1aa-200">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <wsDualHttpBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 bypassProxyOnLocal="false"
                 clientBaseAddress="http://localhost:8001/client/"
                 transactionFlow="true"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://foo/bar"
                 textEncoding="utf-16"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00" />
          <security mode="None">
            <message clientCredentialType="None"
                     negotiateServiceCredential="false"
                     algorithmSuite="Aes128" />
          </security>
        </binding>
      </wsDualHttpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="0f1aa-201">请参阅</span><span class="sxs-lookup"><span data-stu-id="0f1aa-201">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>
- <xref:System.ServiceModel.Configuration.WSDualHttpBindingElement>
- [<span data-ttu-id="0f1aa-202">绑定</span><span class="sxs-lookup"><span data-stu-id="0f1aa-202">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0f1aa-203">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="0f1aa-203">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0f1aa-204">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="0f1aa-204">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

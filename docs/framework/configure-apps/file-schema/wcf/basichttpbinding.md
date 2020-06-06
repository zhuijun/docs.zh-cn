---
title: <basicHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- basicHttpBinding Element
ms.assetid: 85cf1a4f-26c2-48c7-bda6-6c960d5d3fb3
ms.openlocfilehash: ab8dca7f7065d7c174e38ad3a88ea15e39351bed
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "84202046"
---
# \<basicHttpBinding>
<span data-ttu-id="1d939-101">表示 Windows Communication Foundation (WCF)服务可用来配置和公开终结点的绑定，这些终结点将能够与基于 ASMX 的 Web 服务和客户端以及其他符合 WS-I Basic Profile 1.1 的服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="1d939-101">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate with ASMX-based Web services and clients and other services that conform to the WS-I Basic Profile 1.1.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<basicHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="1d939-102">语法</span><span class="sxs-lookup"><span data-stu-id="1d939-102">Syntax</span></span>  
  
```xml  
<basicHttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Text/Mtom"
           name="String"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"
           useDefaultWebProxy="Boolean">
    <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">
      <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"
                 proxyCredentialType="None/Basic/Digest/Ntlm/Windows"
                 realm="String" />
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="UserName/Certificate" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d939-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="1d939-103">Attributes and Elements</span></span>  
 <span data-ttu-id="1d939-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1d939-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d939-105">特性</span><span class="sxs-lookup"><span data-stu-id="1d939-105">Attributes</span></span>  
  
|<span data-ttu-id="1d939-106">属性</span><span class="sxs-lookup"><span data-stu-id="1d939-106">Attribute</span></span>|<span data-ttu-id="1d939-107">说明</span><span class="sxs-lookup"><span data-stu-id="1d939-107">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="1d939-108">一个布尔值，指示客户端是否接受 Cookie 并在今后的请求中传播这些 Cookie。</span><span class="sxs-lookup"><span data-stu-id="1d939-108">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="1d939-109">默认为 `false`。</span><span class="sxs-lookup"><span data-stu-id="1d939-109">The default is `false`.</span></span><br /><br /> <span data-ttu-id="1d939-110">在与使用 Cookie 的 ASMX Web 服务进行交互时，可以使用此属性。</span><span class="sxs-lookup"><span data-stu-id="1d939-110">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="1d939-111">通过这种方式，可以确保从服务器返回的 Cookie 自动复制到客户端今后对该服务的所有请求。</span><span class="sxs-lookup"><span data-stu-id="1d939-111">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="1d939-112">一个布尔值，指示是否对本地地址不使用代理服务器。</span><span class="sxs-lookup"><span data-stu-id="1d939-112">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="1d939-113">默认为 `false`。</span><span class="sxs-lookup"><span data-stu-id="1d939-113">The default is `false`.</span></span><br /><br /> <span data-ttu-id="1d939-114">如果 Internet 资源具有本地地址，则该资源是本地资源。</span><span class="sxs-lookup"><span data-stu-id="1d939-114">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="1d939-115">本地地址是指在同一台计算机上，本地 LAN 或 intranet 上的地址，在语法上，通过缺乏句点（.）来标识 `http://webserver/` `http://localhost/` 。</span><span class="sxs-lookup"><span data-stu-id="1d939-115">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs `http://webserver/` and `http://localhost/`.</span></span><br /><br /> <span data-ttu-id="1d939-116">通过设置此属性，可以确定在访问本地资源时，采用 BasicHttpBinding 配置的终结点是否使用代理服务器。</span><span class="sxs-lookup"><span data-stu-id="1d939-116">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="1d939-117">如果此属性为 `true`，则对本地 Internet 资源的请求不使用代理服务器。</span><span class="sxs-lookup"><span data-stu-id="1d939-117">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="1d939-118">当此属性设置为 `true` 时，如果希望客户端在与同一台计算机上的服务通话时使用代理，请使用主机名称（而非 localhost）。</span><span class="sxs-lookup"><span data-stu-id="1d939-118">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="1d939-119">当此属性为 `false` 时，所有 Internet 请求都通过代理服务器发出。</span><span class="sxs-lookup"><span data-stu-id="1d939-119">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="1d939-120">一个 <xref:System.TimeSpan> 值，指定为完成关闭操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="1d939-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="1d939-121">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="1d939-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1d939-122">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="1d939-122">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="1d939-123">指定用于分析 URI 的 HTTP 主机名比较模式。</span><span class="sxs-lookup"><span data-stu-id="1d939-123">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="1d939-124">此属性的类型为 <xref:System.ServiceModel.HostNameComparisonMode>，指示在对 URI 进行匹配时，是否使用主机名来访问服务。</span><span class="sxs-lookup"><span data-stu-id="1d939-124">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="1d939-125">默认值为 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>，表示忽略匹配项中的主机名。</span><span class="sxs-lookup"><span data-stu-id="1d939-125">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="1d939-126">一个整数值，指定为从通道接收消息的消息缓冲区管理器分配并供其使用的最大内存量。</span><span class="sxs-lookup"><span data-stu-id="1d939-126">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="1d939-127">默认值为 524288 (0x80000) 字节。</span><span class="sxs-lookup"><span data-stu-id="1d939-127">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="1d939-128">通过使用缓冲池，缓冲区管理器可将使用缓冲区的开销降到最低。</span><span class="sxs-lookup"><span data-stu-id="1d939-128">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="1d939-129">当消息离开通道时，服务需要使用缓冲区来处理这些消息。</span><span class="sxs-lookup"><span data-stu-id="1d939-129">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="1d939-130">如果缓冲池中的内存不够用来处理消息负载，则缓冲区管理器必须从 CLR 堆分配更多内存，而这会增加垃圾回收的系统开销。</span><span class="sxs-lookup"><span data-stu-id="1d939-130">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="1d939-131">从 CLR 垃圾堆进行大量分配表明缓冲池太小，可以通过提高此属性指定的限制来实现更大的内存分配，从而提高性能。</span><span class="sxs-lookup"><span data-stu-id="1d939-131">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="1d939-132">一个整数值，指定为采用此绑定配置的终结点处理消息时存储消息的缓冲区的最大大小（字节）。</span><span class="sxs-lookup"><span data-stu-id="1d939-132">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="1d939-133">默认值为 65,536 字节。</span><span class="sxs-lookup"><span data-stu-id="1d939-133">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="1d939-134">一个正整数，定义在采用此绑定配置的通道上可以接收的消息的最大消息大小（字节），包括消息头。</span><span class="sxs-lookup"><span data-stu-id="1d939-134">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="1d939-135">如果消息对于接收方而言太大，则发送方将收到 SOAP 错误。</span><span class="sxs-lookup"><span data-stu-id="1d939-135">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="1d939-136">接收方将删除该消息，并在跟踪日志中创建事件项。</span><span class="sxs-lookup"><span data-stu-id="1d939-136">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="1d939-137">默认值为 65,536 字节。</span><span class="sxs-lookup"><span data-stu-id="1d939-137">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="1d939-138">定义用于对 SOAP 消息进行编码的编码器。</span><span class="sxs-lookup"><span data-stu-id="1d939-138">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="1d939-139">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="1d939-139">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1d939-140">-Text：使用文本消息编码器。</span><span class="sxs-lookup"><span data-stu-id="1d939-140">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="1d939-141">-Mtom：使用消息传输组织机制1.0 （MTOM）编码器。</span><span class="sxs-lookup"><span data-stu-id="1d939-141">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="1d939-142">默认值为 Text。</span><span class="sxs-lookup"><span data-stu-id="1d939-142">The default is Text.</span></span> <span data-ttu-id="1d939-143">此属性的类型为 <xref:System.ServiceModel.WSMessageEncoding>。</span><span class="sxs-lookup"><span data-stu-id="1d939-143">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="1d939-144">一个包含绑定的配置名称的字符串。</span><span class="sxs-lookup"><span data-stu-id="1d939-144">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="1d939-145">此值在同一类型的绑定中应是唯一的。</span><span class="sxs-lookup"><span data-stu-id="1d939-145">This value should be unique among bindings of the same type.</span></span> <span data-ttu-id="1d939-146">从 .NET Framework 4 开始，绑定和行为不需要具有名称。</span><span class="sxs-lookup"><span data-stu-id="1d939-146">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="1d939-147">有关默认配置和无值绑定和行为的详细信息，请参阅[WCF 服务的](../../../wcf/samples/simplified-configuration-for-wcf-services.md)[简化配置](../../../wcf/simplified-configuration.md)和简化配置。</span><span class="sxs-lookup"><span data-stu-id="1d939-147">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="1d939-148">一个 <xref:System.TimeSpan> 值，指定为完成打开操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="1d939-148">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="1d939-149">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="1d939-149">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1d939-150">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="1d939-150">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="1d939-151">一个包含 HTTP 代理地址的 URI。</span><span class="sxs-lookup"><span data-stu-id="1d939-151">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="1d939-152">如果 `useSystemWebProxy` 设置为 `true`，则此设置必须为 `null`。</span><span class="sxs-lookup"><span data-stu-id="1d939-152">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="1d939-153">默认为 `null`。</span><span class="sxs-lookup"><span data-stu-id="1d939-153">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="1d939-154">一个 <xref:System.TimeSpan> 值，指定为完成接收操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="1d939-154">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="1d939-155">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="1d939-155">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1d939-156">默认值为 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="1d939-156">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="1d939-157">一个 <xref:System.TimeSpan> 值，指定为完成发送操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="1d939-157">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="1d939-158">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="1d939-158">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1d939-159">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="1d939-159">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="1d939-160">设置要用来在绑定上发出消息的字符集编码。</span><span class="sxs-lookup"><span data-stu-id="1d939-160">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="1d939-161">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="1d939-161">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1d939-162">-BigEndianUnicode： Unicode BigEndian 编码。</span><span class="sxs-lookup"><span data-stu-id="1d939-162">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="1d939-163">-Unicode：16位编码。</span><span class="sxs-lookup"><span data-stu-id="1d939-163">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="1d939-164">-UTF8：8位编码</span><span class="sxs-lookup"><span data-stu-id="1d939-164">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="1d939-165">默认编码为 UTF8。</span><span class="sxs-lookup"><span data-stu-id="1d939-165">The default is UTF8.</span></span> <span data-ttu-id="1d939-166">此属性的类型为 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="1d939-166">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="1d939-167">一个有效的 <xref:System.ServiceModel.TransferMode> 值，指定为请求或响应对消息进行缓冲处理还是流式处理。</span><span class="sxs-lookup"><span data-stu-id="1d939-167">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="1d939-168">一个布尔值，指定是否应在可用时使用系统的自动配置 HTTP 代理。</span><span class="sxs-lookup"><span data-stu-id="1d939-168">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="1d939-169">默认为 `true`。</span><span class="sxs-lookup"><span data-stu-id="1d939-169">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d939-170">子元素</span><span class="sxs-lookup"><span data-stu-id="1d939-170">Child Elements</span></span>  
  
|<span data-ttu-id="1d939-171">元素</span><span class="sxs-lookup"><span data-stu-id="1d939-171">Element</span></span>|<span data-ttu-id="1d939-172">描述</span><span class="sxs-lookup"><span data-stu-id="1d939-172">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|<span data-ttu-id="1d939-173">定义绑定的安全设置。</span><span class="sxs-lookup"><span data-stu-id="1d939-173">Defines the security settings for the binding.</span></span> <span data-ttu-id="1d939-174">此元素的类型为 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="1d939-174">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span></span>|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="1d939-175">定义可由采用此绑定配置的终结点进行处理的 SOAP 消息的复杂性约束。</span><span class="sxs-lookup"><span data-stu-id="1d939-175">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="1d939-176">此元素的类型为 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="1d939-176">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1d939-177">父元素</span><span class="sxs-lookup"><span data-stu-id="1d939-177">Parent Elements</span></span>  
  
|<span data-ttu-id="1d939-178">元素</span><span class="sxs-lookup"><span data-stu-id="1d939-178">Element</span></span>|<span data-ttu-id="1d939-179">描述</span><span class="sxs-lookup"><span data-stu-id="1d939-179">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="1d939-180">此元素包含标准绑定和自定义绑定的集合。</span><span class="sxs-lookup"><span data-stu-id="1d939-180">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d939-181">注解</span><span class="sxs-lookup"><span data-stu-id="1d939-181">Remarks</span></span>  
 <span data-ttu-id="1d939-182">BasicHttpBinding 使用 HTTP 作为传输协议来发送 SOAP 1.1 消息。</span><span class="sxs-lookup"><span data-stu-id="1d939-182">The BasicHttpBinding uses HTTP as the transport for sending SOAP 1.1 messages.</span></span> <span data-ttu-id="1d939-183">服务可以使用此绑定来公开符合 WS-I BP 1.1 标准的终结点，例如 ASMX 客户端使用的终结点。</span><span class="sxs-lookup"><span data-stu-id="1d939-183">A service can use this binding to expose endpoints that conform to WS-I BP 1.1, such as those that ASMX clients consume.</span></span> <span data-ttu-id="1d939-184">同样，客户端可以使用 BasicHttpBinding 与公开符合 WS-I BP 1.1 标准的终结点的服务（如 ASMX Web 服务或采用 BasicHttpBinding 配置的服务）进行通信。</span><span class="sxs-lookup"><span data-stu-id="1d939-184">Similarly, a client can use the BasicHttpBinding to communicate with services exposing endpoints that conform to WS-I BP 1.1, such as ASMX Web services or services configured with the BasicHttpBinding.</span></span>  
  
 <span data-ttu-id="1d939-185">默认情况下，安全设置处于关闭状态，但可以将子元素的模式属性设置 [\<security>](security-of-basichttpbinding.md) 为以外的值 `None` 。</span><span class="sxs-lookup"><span data-stu-id="1d939-185">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="1d939-186">默认情况下，它使用“Text”消息编码和 UTF-8 文本编码。</span><span class="sxs-lookup"><span data-stu-id="1d939-186">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d939-187">示例</span><span class="sxs-lookup"><span data-stu-id="1d939-187">Example</span></span>  
 <span data-ttu-id="1d939-188">下面的示例演示如何使用 <xref:System.ServiceModel.BasicHttpBinding> 提供 HTTP 通信以及与第一代和第二代 Web 服务的最大互操作性。</span><span class="sxs-lookup"><span data-stu-id="1d939-188">The following example demonstrates the use of <xref:System.ServiceModel.BasicHttpBinding> that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="1d939-189">绑定是在客户端和服务的配置文件中指定的。</span><span class="sxs-lookup"><span data-stu-id="1d939-189">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="1d939-190">绑定类型是使用 `binding` 元素的 `<endpoint>` 属性指定的。</span><span class="sxs-lookup"><span data-stu-id="1d939-190">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="1d939-191">如果要配置基本绑定并更改它的某些设置，则必须定义一个绑定配置。</span><span class="sxs-lookup"><span data-stu-id="1d939-191">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="1d939-192">终结点必须使用 `bindingConfiguration` 元素的 `<endpoint>` 属性按名称引用绑定配置，如以下服务配置代码所示。</span><span class="sxs-lookup"><span data-stu-id="1d939-192">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
      <binding name="Binding1"
               hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxReceivedMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Text"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="example"></a><span data-ttu-id="1d939-193">示例</span><span class="sxs-lookup"><span data-stu-id="1d939-193">Example</span></span>  
 <span data-ttu-id="1d939-194">从 .NET Framework 4 开始，绑定和行为不需要具有名称。</span><span class="sxs-lookup"><span data-stu-id="1d939-194">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="1d939-195">可以通过从终结点地址和绑定的名称中删除 bindingConfiguration 来完成上一示例中的功能。</span><span class="sxs-lookup"><span data-stu-id="1d939-195">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name from the binding.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
      <binding hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxReceivedMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Text"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
 <span data-ttu-id="1d939-196">有关默认配置和无值绑定和行为的详细信息，请参阅[WCF 服务的](../../../wcf/samples/simplified-configuration-for-wcf-services.md)[简化配置](../../../wcf/simplified-configuration.md)和简化配置。</span><span class="sxs-lookup"><span data-stu-id="1d939-196">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d939-197">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1d939-197">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="1d939-198">绑定</span><span class="sxs-lookup"><span data-stu-id="1d939-198">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1d939-199">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="1d939-199">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1d939-200">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="1d939-200">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

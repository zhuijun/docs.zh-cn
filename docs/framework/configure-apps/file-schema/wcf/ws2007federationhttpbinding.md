---
title: <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
ms.openlocfilehash: 20ba643fddbac8a488e5457f0195cc253d4d23f7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139311"
---
# \<ws2007FederationHttpBinding>

<span data-ttu-id="1eb67-101">一个安全且可互操作的绑定，它派生自 [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) 并支持联合安全性。</span><span class="sxs-lookup"><span data-stu-id="1eb67-101">A secure and interoperable binding that derives from [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) and supports federated security.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ws2007FederationHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="1eb67-102">语法</span><span class="sxs-lookup"><span data-stu-id="1eb67-102">Syntax</span></span>

```xml
<ws2007FederationHttpBinding>
  <binding bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxReceivedMessageSize="integer"
           messageEncoding="Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           privacyNoticeAt="Uri"
           privacyNoticeVersion="Integer"
           proxyAddress="Uri"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
      </message>
    </security>
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</ws2007FederationHttpBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1eb67-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="1eb67-103">Attributes and Elements</span></span>

<span data-ttu-id="1eb67-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1eb67-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="1eb67-105">特性</span><span class="sxs-lookup"><span data-stu-id="1eb67-105">Attributes</span></span>

|<span data-ttu-id="1eb67-106">属性</span><span class="sxs-lookup"><span data-stu-id="1eb67-106">Attribute</span></span>|<span data-ttu-id="1eb67-107">说明</span><span class="sxs-lookup"><span data-stu-id="1eb67-107">Description</span></span>|
|---------------|-----------------|
|`bypassProxyOnLocal`|<span data-ttu-id="1eb67-108">一个值，指示是否对本地地址不使用代理服务器。</span><span class="sxs-lookup"><span data-stu-id="1eb67-108">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="1eb67-109">默认为 `false`。</span><span class="sxs-lookup"><span data-stu-id="1eb67-109">The default is `false`.</span></span>|
|`closeTimeout`|<span data-ttu-id="1eb67-110">一个 <xref:System.TimeSpan> 值，指定为完成关闭操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="1eb67-110">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="1eb67-111">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="1eb67-111">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1eb67-112">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="1eb67-112">The default is 00:01:00.</span></span>|
|`hostNameComparisonMode`|<span data-ttu-id="1eb67-113">指定用于分析 URI 的 HTTP 主机名比较模式。</span><span class="sxs-lookup"><span data-stu-id="1eb67-113">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="1eb67-114">此属性的类型为 <xref:System.ServiceModel.HostNameComparisonMode>，指示在对 URI 进行匹配时，是否使用主机名来访问服务。</span><span class="sxs-lookup"><span data-stu-id="1eb67-114">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="1eb67-115">默认值为 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>，表示忽略匹配项中的主机名。</span><span class="sxs-lookup"><span data-stu-id="1eb67-115">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|`maxBufferPoolSize`|<span data-ttu-id="1eb67-116">此绑定的最大缓冲池大小。</span><span class="sxs-lookup"><span data-stu-id="1eb67-116">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="1eb67-117">默认值为 524,288 字节 (512 \* 1024)。</span><span class="sxs-lookup"><span data-stu-id="1eb67-117">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="1eb67-118">Windows Communication Foundation (WCF) 的许多部件使用缓冲区。</span><span class="sxs-lookup"><span data-stu-id="1eb67-118">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="1eb67-119">每次使用缓冲区时，创建和销毁它们都将占用大量资源，而缓冲区的垃圾回收过程也是如此。</span><span class="sxs-lookup"><span data-stu-id="1eb67-119">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="1eb67-120">利用缓冲池，可以从缓冲池中获得缓冲区，使用缓冲区，然后在完成工作后将其返回给缓冲池。</span><span class="sxs-lookup"><span data-stu-id="1eb67-120">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="1eb67-121">这样就避免了创建和销毁缓冲区的系统开销。</span><span class="sxs-lookup"><span data-stu-id="1eb67-121">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|`maxReceivedMessageSize`|<span data-ttu-id="1eb67-122">在采用此绑定配置的通道上可以接收的最大消息大小（包括标头），单位为字节。</span><span class="sxs-lookup"><span data-stu-id="1eb67-122">The maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="1eb67-123">如果消息超出此限制，则发送方将收到 SOAP 错误。</span><span class="sxs-lookup"><span data-stu-id="1eb67-123">The sender of a message that exceeds this limit receives a SOAP fault.</span></span> <span data-ttu-id="1eb67-124">接收方将删除该消息，并在跟踪日志中创建事件项。</span><span class="sxs-lookup"><span data-stu-id="1eb67-124">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="1eb67-125">默认值为 65536。</span><span class="sxs-lookup"><span data-stu-id="1eb67-125">The default is 65536.</span></span>|
|`messageEncoding`|<span data-ttu-id="1eb67-126">定义用于对消息进行编码的编码器。</span><span class="sxs-lookup"><span data-stu-id="1eb67-126">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="1eb67-127">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="1eb67-127">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1eb67-128">-Text：使用文本消息编码器。</span><span class="sxs-lookup"><span data-stu-id="1eb67-128">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="1eb67-129">-Mtom：使用消息传输组织机制1.0 （MTOM）编码器。</span><span class="sxs-lookup"><span data-stu-id="1eb67-129">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="1eb67-130">默认值为 Text。</span><span class="sxs-lookup"><span data-stu-id="1eb67-130">The default is Text.</span></span><br /><br /> <span data-ttu-id="1eb67-131">此属性的类型为 <xref:System.ServiceModel.WSMessageEncoding>。</span><span class="sxs-lookup"><span data-stu-id="1eb67-131">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|`name`|<span data-ttu-id="1eb67-132">绑定的配置名称。</span><span class="sxs-lookup"><span data-stu-id="1eb67-132">The configuration name of the binding.</span></span> <span data-ttu-id="1eb67-133">因为此值用作绑定的标识，所以它应该是唯一的。</span><span class="sxs-lookup"><span data-stu-id="1eb67-133">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="1eb67-134">从 .NET Framework 4 开始，绑定和行为不需要具有名称。</span><span class="sxs-lookup"><span data-stu-id="1eb67-134">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="1eb67-135">有关默认配置和无值绑定和行为的详细信息，请参阅[WCF 服务的](../../../wcf/samples/simplified-configuration-for-wcf-services.md)[简化配置](../../../wcf/simplified-configuration.md)和简化配置。</span><span class="sxs-lookup"><span data-stu-id="1eb67-135">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|`openTimeout`|<span data-ttu-id="1eb67-136">一个 <xref:System.TimeSpan> 值，指定为完成打开操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="1eb67-136">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="1eb67-137">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="1eb67-137">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1eb67-138">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="1eb67-138">The default is 00:01:00.</span></span>|
|`privacyNoticeAt`|<span data-ttu-id="1eb67-139">隐私声明所在的 URI。</span><span class="sxs-lookup"><span data-stu-id="1eb67-139">A URI at which the privacy notice is located.</span></span>|
|`privacyNoticeVersion`|<span data-ttu-id="1eb67-140">当前隐私声明的版本。</span><span class="sxs-lookup"><span data-stu-id="1eb67-140">The version of the current privacy notice.</span></span>|
|`proxyAddress`|<span data-ttu-id="1eb67-141">一个指定 HTTP 代理的地址的 URI。</span><span class="sxs-lookup"><span data-stu-id="1eb67-141">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="1eb67-142">如果 `useDefaultWebProxy` 为 `true`，则此设置必须为 `null`。</span><span class="sxs-lookup"><span data-stu-id="1eb67-142">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="1eb67-143">默认为 `null`。</span><span class="sxs-lookup"><span data-stu-id="1eb67-143">The default is `null`.</span></span>|
|`receiveTimeout`|<span data-ttu-id="1eb67-144">一个 <xref:System.TimeSpan> 值，指定为完成接收操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="1eb67-144">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="1eb67-145">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="1eb67-145">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1eb67-146">默认值为 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="1eb67-146">The default is 00:10:00.</span></span>|
|`sendTimeout`|<span data-ttu-id="1eb67-147">一个 <xref:System.TimeSpan> 值，指定为完成发送操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="1eb67-147">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="1eb67-148">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="1eb67-148">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1eb67-149">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="1eb67-149">The default is 00:01:00.</span></span>|
|`textEncoding`|<span data-ttu-id="1eb67-150">设置要用来在绑定上发出消息的字符集编码。</span><span class="sxs-lookup"><span data-stu-id="1eb67-150">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="1eb67-151">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="1eb67-151">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1eb67-152">-BigEndianUnicode： Unicode Big Endian 编码。</span><span class="sxs-lookup"><span data-stu-id="1eb67-152">-   BigEndianUnicode: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="1eb67-153">-Unicode：16位编码。</span><span class="sxs-lookup"><span data-stu-id="1eb67-153">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="1eb67-154">-UTF8：8位编码。</span><span class="sxs-lookup"><span data-stu-id="1eb67-154">-   UTF8: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="1eb67-155">默认编码为 UTF8。</span><span class="sxs-lookup"><span data-stu-id="1eb67-155">The default is UTF8.</span></span> <span data-ttu-id="1eb67-156">此属性的类型为 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="1eb67-156">This attribute is of type <xref:System.Text.Encoding>.</span></span>|
|`transactionFlow`|<span data-ttu-id="1eb67-157">一个值，指定绑定是否支持流动 WS-Transactions。</span><span class="sxs-lookup"><span data-stu-id="1eb67-157">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="1eb67-158">默认为 `false`。</span><span class="sxs-lookup"><span data-stu-id="1eb67-158">The default is `false`.</span></span>|
|`useDefaultWebProxy`|<span data-ttu-id="1eb67-159">一个值，指示是否使用系统的自动配置 HTTP 代理。</span><span class="sxs-lookup"><span data-stu-id="1eb67-159">A value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="1eb67-160">如果此属性为 `null`，则代理地址必须为 `true`（即，不设置代理地址）。</span><span class="sxs-lookup"><span data-stu-id="1eb67-160">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="1eb67-161">默认为 `true`。</span><span class="sxs-lookup"><span data-stu-id="1eb67-161">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="1eb67-162">子元素</span><span class="sxs-lookup"><span data-stu-id="1eb67-162">Child Elements</span></span>

|<span data-ttu-id="1eb67-163">元素</span><span class="sxs-lookup"><span data-stu-id="1eb67-163">Element</span></span>|<span data-ttu-id="1eb67-164">描述</span><span class="sxs-lookup"><span data-stu-id="1eb67-164">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="1eb67-165">定义消息的安全设置。</span><span class="sxs-lookup"><span data-stu-id="1eb67-165">Defines the security settings for the message.</span></span> <span data-ttu-id="1eb67-166">此元素的类型为 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="1eb67-166">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="1eb67-167">定义可由采用此绑定配置的终结点进行处理的 SOAP 消息的复杂性约束。</span><span class="sxs-lookup"><span data-stu-id="1eb67-167">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="1eb67-168">此元素的类型为 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="1eb67-168">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="1eb67-169">指定是否在通道终结点之间建立可靠会话。</span><span class="sxs-lookup"><span data-stu-id="1eb67-169">Specifies whether reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1eb67-170">父元素</span><span class="sxs-lookup"><span data-stu-id="1eb67-170">Parent Elements</span></span>

|<span data-ttu-id="1eb67-171">元素</span><span class="sxs-lookup"><span data-stu-id="1eb67-171">Element</span></span>|<span data-ttu-id="1eb67-172">描述</span><span class="sxs-lookup"><span data-stu-id="1eb67-172">Description</span></span>|
|-------------|-----------------|
|[\<bindings>](bindings.md)|<span data-ttu-id="1eb67-173">此元素包含标准绑定和自定义绑定的集合。</span><span class="sxs-lookup"><span data-stu-id="1eb67-173">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1eb67-174">注解</span><span class="sxs-lookup"><span data-stu-id="1eb67-174">Remarks</span></span>

<span data-ttu-id="1eb67-175">联合是一种可以在多个企业或信任域通过共享标识进行身份验证和授权的功能。</span><span class="sxs-lookup"><span data-stu-id="1eb67-175">Federation is the ability to share identities across multiple enterprises or trust domains for authentication and authorization.</span></span> <span data-ttu-id="1eb67-176">它使用 WS-Trust 协议将标识的表示形式从一个信任域映射到另一个信任域。</span><span class="sxs-lookup"><span data-stu-id="1eb67-176">It uses the WS-Trust protocol to map the identity representation from one trust domain to another.</span></span> <span data-ttu-id="1eb67-177">联合 HTTP 绑定支持 SOAP 安全以及混合模式安全，但不支持传输安全。</span><span class="sxs-lookup"><span data-stu-id="1eb67-177">Federated HTTP binding supports SOAP security as well as mixed-mode security, but it does not support transport security.</span></span> <span data-ttu-id="1eb67-178">配置了此绑定的服务必须使用 HTTP 传输。</span><span class="sxs-lookup"><span data-stu-id="1eb67-178">Services configured with this binding must use the HTTP transport.</span></span> <span data-ttu-id="1eb67-179">有关详细信息，请参阅 [\<wsFederationHttpBinding>](wsfederationhttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="1eb67-179">For more information, see [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="1eb67-180">示例</span><span class="sxs-lookup"><span data-stu-id="1eb67-180">Example</span></span>

```xml
<configuration>
  <system.ServiceModel>
    <bindings>
      <ws2007FederationHttpBinding>
        <binding bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://www.contoso.com"
                 textEncoding="Utf16TextEncoding"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="None">
            <message negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"
                     issuedKeyType="PublicKey">
              <issuer address="http://localhost/Sts" />
            </message>
          </security>
        </binding>
      </ws2007FederationBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="1eb67-181">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1eb67-181">See also</span></span>

- <xref:System.ServiceModel.WS2007FederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>
- [\<wsFederationHttpBinding>](wsfederationhttpbinding.md)
- [<span data-ttu-id="1eb67-182">绑定</span><span class="sxs-lookup"><span data-stu-id="1eb67-182">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1eb67-183">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="1eb67-183">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1eb67-184">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="1eb67-184">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

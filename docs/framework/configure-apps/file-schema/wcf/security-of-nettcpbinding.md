---
title: <security> 的 <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
ms.openlocfilehash: aa01e906ddd2f15007c72bfc2a45122cfb15ba2c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736369"
---
# <a name="security-of-nettcpbinding"></a><span data-ttu-id="b2dfa-102">\<security> 的 \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="b2dfa-102">\<security> of \<netTcpBinding></span></span>
<span data-ttu-id="b2dfa-103">定义绑定的安全设置。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-103">Defines the security settings for a binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="b2dfa-104">语法</span><span class="sxs-lookup"><span data-stu-id="b2dfa-104">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             protectionLevel="None/Sign/EncryptAndSign" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b2dfa-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="b2dfa-105">Attributes and Elements</span></span>  
 <span data-ttu-id="b2dfa-106">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2dfa-107">特性</span><span class="sxs-lookup"><span data-stu-id="b2dfa-107">Attributes</span></span>  
  
|<span data-ttu-id="b2dfa-108">属性</span><span class="sxs-lookup"><span data-stu-id="b2dfa-108">Attribute</span></span>|<span data-ttu-id="b2dfa-109">说明</span><span class="sxs-lookup"><span data-stu-id="b2dfa-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b2dfa-110">模式</span><span class="sxs-lookup"><span data-stu-id="b2dfa-110">mode</span></span>|<span data-ttu-id="b2dfa-111">可选。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-111">Optional.</span></span> <span data-ttu-id="b2dfa-112">指定所应用的安全类型。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="b2dfa-113">以下列出了有效值。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-113">Valid values are shown below.</span></span> <span data-ttu-id="b2dfa-114">默认值为 `Transport`。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-114">The default value is `Transport`.</span></span><br /><br /> <span data-ttu-id="b2dfa-115">此属性的类型为 <xref:System.ServiceModel.SecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-115">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="b2dfa-116">mode 属性</span><span class="sxs-lookup"><span data-stu-id="b2dfa-116">mode Attribute</span></span>  
  
|<span data-ttu-id="b2dfa-117">值</span><span class="sxs-lookup"><span data-stu-id="b2dfa-117">Value</span></span>|<span data-ttu-id="b2dfa-118">说明</span><span class="sxs-lookup"><span data-stu-id="b2dfa-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b2dfa-119">无</span><span class="sxs-lookup"><span data-stu-id="b2dfa-119">None</span></span>|<span data-ttu-id="b2dfa-120">禁用安全性。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-120">Security is disabled.</span></span>|  
|<span data-ttu-id="b2dfa-121">Transport</span><span class="sxs-lookup"><span data-stu-id="b2dfa-121">Transport</span></span>|<span data-ttu-id="b2dfa-122">使用 TLS over TCP 或 SPNego 提供传输安全性。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-122">Transport security is provided using TLS over TCP or SPNego.</span></span> <span data-ttu-id="b2dfa-123">此服务可能需要使用 SSL 证书进行配置。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-123">The service may need to be configured with SSL certificates.</span></span> <span data-ttu-id="b2dfa-124">可以使用此模式控制保护级别。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-124">It is possible to control the protection level with this mode.</span></span>|  
|<span data-ttu-id="b2dfa-125">消息</span><span class="sxs-lookup"><span data-stu-id="b2dfa-125">Message</span></span>|<span data-ttu-id="b2dfa-126">使用 SOAP 消息安全提供安全性。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-126">Security is provided using SOAP message security.</span></span> <span data-ttu-id="b2dfa-127">默认情况下，将对 SOAP 正文进行加密和签名。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-127">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="b2dfa-128">此模式提供了各种各样的功能，例如服务凭据在带外客户端是否可用、要使用的算法套件以及要应用于消息正文的保护级别。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-128">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body.</span></span> <span data-ttu-id="b2dfa-129">每个会话将执行一次客户端身份验证，身份验证的结果在会话过程中将被缓存。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-129">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="b2dfa-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="b2dfa-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="b2dfa-131">传输安全性与消息安全性结合使用。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-131">Transport security is coupled with message security.</span></span> <span data-ttu-id="b2dfa-132">使用 TLS over TCP 或 SPNego 提供传输安全性，传输安全性可确保完整性、保密性和服务器身份验证。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-132">Transport security is provided by TLS over TCP, or SPNego, and ensures integrity, confidentiality, and server authentication.</span></span> <span data-ttu-id="b2dfa-133">SOAP 消息安全性提供客户端身份验证。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-133">SOAP message security provides client authentication.</span></span> <span data-ttu-id="b2dfa-134">默认情况下，每个会话将执行一次客户端身份验证，身份验证的结果在会话过程中将被缓存。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-134">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b2dfa-135">子元素</span><span class="sxs-lookup"><span data-stu-id="b2dfa-135">Child Elements</span></span>  
  
|<span data-ttu-id="b2dfa-136">元素</span><span class="sxs-lookup"><span data-stu-id="b2dfa-136">Element</span></span>|<span data-ttu-id="b2dfa-137">描述</span><span class="sxs-lookup"><span data-stu-id="b2dfa-137">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-nettcpbinding.md)|<span data-ttu-id="b2dfa-138">定义传输的安全设置。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-138">Defines the security settings for the transport.</span></span> <span data-ttu-id="b2dfa-139">此元素的类型为 <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-139">This element is of type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span></span>|  
|[\<message>](message-element-of-nettcpbinding.md)|<span data-ttu-id="b2dfa-140">定义消息的安全设置。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-140">Defines the security settings for the message.</span></span> <span data-ttu-id="b2dfa-141">此元素的类型为 <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-141">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b2dfa-142">父元素</span><span class="sxs-lookup"><span data-stu-id="b2dfa-142">Parent Elements</span></span>  
  
|<span data-ttu-id="b2dfa-143">元素</span><span class="sxs-lookup"><span data-stu-id="b2dfa-143">Element</span></span>|<span data-ttu-id="b2dfa-144">描述</span><span class="sxs-lookup"><span data-stu-id="b2dfa-144">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b2dfa-145">binding</span><span class="sxs-lookup"><span data-stu-id="b2dfa-145">binding</span></span>|<span data-ttu-id="b2dfa-146">的绑定元素 [\<netTcpBinding>](nettcpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-146">The binding element of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2dfa-147">注解</span><span class="sxs-lookup"><span data-stu-id="b2dfa-147">Remarks</span></span>  
 <span data-ttu-id="b2dfa-148">每个标准绑定都提供用于控制传输安全性需求的参数。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-148">Each of the standard bindings provides parameters for controlling the transfer security requirements.</span></span> <span data-ttu-id="b2dfa-149">这些参数通常包括指定是使用消息级安全性还是使用传输级安全性的安全模式，还包括客户端凭据类型的选项。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-149">These parameters typically include the security mode that specified whether message-level or transport-level security is used and the choice of client credential type.</span></span> <span data-ttu-id="b2dfa-150">基于这些参数提供的可供选择的选项，构建一个具有适当安全性的信道堆栈。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-150">Based on the choice of options these parameters present, a channel stack is constructed with appropriate security.</span></span>  
  
 <span data-ttu-id="b2dfa-151">由 Windows Communication Foundation (WCF) 提供的系统提供的绑定是一组旨在满足一些最常见的方案要求的绑定。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-151">The system-provided bindings supplied by Windows Communication Foundation (WCF) are a set designed to meet some of the most common scenario requirements.</span></span> <span data-ttu-id="b2dfa-152">所有这些绑定都允许为某些特定的目标方案指定安全要求。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-152">Each of these bindings allows the specification of security requirements for some specific targeted scenarios.</span></span>  
  
 <span data-ttu-id="b2dfa-153">此配置元素提供用于 `netTcpBinding` 的安全规范。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-153">This configuration element provides the security specifications for `netTcpBinding`.</span></span> <span data-ttu-id="b2dfa-154">这是一种适合于跨计算机通信的安全、可靠且进行了优化的绑定。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-154">This is a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="b2dfa-155">默认情况下，它生成运行时通信堆栈，该堆栈支持用于消息传递的 TCP、消息安全性和身份验证的 Windows 安全、可靠的 WS-ReliableMessaging，以及二进制消息编码。</span><span class="sxs-lookup"><span data-stu-id="b2dfa-155">By default it generates a runtime communication stack supporting TCP for message delivery and Windows Security for message security and authentication, WS-ReliableMessaging for reliability, and binary message encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2dfa-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b2dfa-156">See also</span></span>

- <xref:System.ServiceModel.NetTcpSecurity>
- <xref:System.ServiceModel.NetTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="b2dfa-157">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="b2dfa-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b2dfa-158">绑定</span><span class="sxs-lookup"><span data-stu-id="b2dfa-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b2dfa-159">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="b2dfa-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b2dfa-160">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="b2dfa-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

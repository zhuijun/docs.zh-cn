---
title: <security> 的 <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
ms.openlocfilehash: d39e3e5e655817aa91c5301274a860a00a6ab7ef
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169981"
---
# <a name="security-of-nettcpbinding"></a><span data-ttu-id="1f834-102">\<security> 的 \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="1f834-102">\<security> of \<netTcpBinding></span></span>

<span data-ttu-id="1f834-103">定义绑定的安全设置。</span><span class="sxs-lookup"><span data-stu-id="1f834-103">Defines the security settings for a binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="1f834-104">语法</span><span class="sxs-lookup"><span data-stu-id="1f834-104">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             protectionLevel="None/Sign/EncryptAndSign" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f834-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="1f834-105">Attributes and Elements</span></span>  

 <span data-ttu-id="1f834-106">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1f834-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f834-107">特性</span><span class="sxs-lookup"><span data-stu-id="1f834-107">Attributes</span></span>  
  
|<span data-ttu-id="1f834-108">属性</span><span class="sxs-lookup"><span data-stu-id="1f834-108">Attribute</span></span>|<span data-ttu-id="1f834-109">描述</span><span class="sxs-lookup"><span data-stu-id="1f834-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1f834-110">mode</span><span class="sxs-lookup"><span data-stu-id="1f834-110">mode</span></span>|<span data-ttu-id="1f834-111">可选。</span><span class="sxs-lookup"><span data-stu-id="1f834-111">Optional.</span></span> <span data-ttu-id="1f834-112">指定所应用的安全类型。</span><span class="sxs-lookup"><span data-stu-id="1f834-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="1f834-113">以下列出了有效值。</span><span class="sxs-lookup"><span data-stu-id="1f834-113">Valid values are shown below.</span></span> <span data-ttu-id="1f834-114">默认值是 `Transport`。</span><span class="sxs-lookup"><span data-stu-id="1f834-114">The default value is `Transport`.</span></span><br /><br /> <span data-ttu-id="1f834-115">此属性的类型为 <xref:System.ServiceModel.SecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="1f834-115">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="1f834-116">mode 属性</span><span class="sxs-lookup"><span data-stu-id="1f834-116">mode Attribute</span></span>  
  
|<span data-ttu-id="1f834-117">值</span><span class="sxs-lookup"><span data-stu-id="1f834-117">Value</span></span>|<span data-ttu-id="1f834-118">描述</span><span class="sxs-lookup"><span data-stu-id="1f834-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1f834-119">无</span><span class="sxs-lookup"><span data-stu-id="1f834-119">None</span></span>|<span data-ttu-id="1f834-120">禁用安全性。</span><span class="sxs-lookup"><span data-stu-id="1f834-120">Security is disabled.</span></span>|  
|<span data-ttu-id="1f834-121">传输</span><span class="sxs-lookup"><span data-stu-id="1f834-121">Transport</span></span>|<span data-ttu-id="1f834-122">使用 TLS over TCP 或 SPNego 提供传输安全性。</span><span class="sxs-lookup"><span data-stu-id="1f834-122">Transport security is provided using TLS over TCP or SPNego.</span></span> <span data-ttu-id="1f834-123">此服务可能需要使用 SSL 证书进行配置。</span><span class="sxs-lookup"><span data-stu-id="1f834-123">The service may need to be configured with SSL certificates.</span></span> <span data-ttu-id="1f834-124">可以使用此模式控制保护级别。</span><span class="sxs-lookup"><span data-stu-id="1f834-124">It is possible to control the protection level with this mode.</span></span>|  
|<span data-ttu-id="1f834-125">消息</span><span class="sxs-lookup"><span data-stu-id="1f834-125">Message</span></span>|<span data-ttu-id="1f834-126">使用 SOAP 消息安全提供安全性。</span><span class="sxs-lookup"><span data-stu-id="1f834-126">Security is provided using SOAP message security.</span></span> <span data-ttu-id="1f834-127">默认情况下，将对 SOAP 正文进行加密和签名。</span><span class="sxs-lookup"><span data-stu-id="1f834-127">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="1f834-128">此模式提供了各种各样的功能，例如服务凭据在带外客户端是否可用、要使用的算法套件以及要应用于消息正文的保护级别。</span><span class="sxs-lookup"><span data-stu-id="1f834-128">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body.</span></span> <span data-ttu-id="1f834-129">每个会话将执行一次客户端身份验证，身份验证的结果在会话过程中将被缓存。</span><span class="sxs-lookup"><span data-stu-id="1f834-129">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="1f834-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="1f834-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="1f834-131">传输安全性与消息安全性结合使用。</span><span class="sxs-lookup"><span data-stu-id="1f834-131">Transport security is coupled with message security.</span></span> <span data-ttu-id="1f834-132">使用 TLS over TCP 或 SPNego 提供传输安全性，传输安全性可确保完整性、保密性和服务器身份验证。</span><span class="sxs-lookup"><span data-stu-id="1f834-132">Transport security is provided by TLS over TCP, or SPNego, and ensures integrity, confidentiality, and server authentication.</span></span> <span data-ttu-id="1f834-133">SOAP 消息安全性提供客户端身份验证。</span><span class="sxs-lookup"><span data-stu-id="1f834-133">SOAP message security provides client authentication.</span></span> <span data-ttu-id="1f834-134">默认情况下，每个会话将执行一次客户端身份验证，身份验证的结果在会话过程中将被缓存。</span><span class="sxs-lookup"><span data-stu-id="1f834-134">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1f834-135">子元素</span><span class="sxs-lookup"><span data-stu-id="1f834-135">Child Elements</span></span>  
  
|<span data-ttu-id="1f834-136">元素</span><span class="sxs-lookup"><span data-stu-id="1f834-136">Element</span></span>|<span data-ttu-id="1f834-137">描述</span><span class="sxs-lookup"><span data-stu-id="1f834-137">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-nettcpbinding.md)|<span data-ttu-id="1f834-138">定义传输的安全设置。</span><span class="sxs-lookup"><span data-stu-id="1f834-138">Defines the security settings for the transport.</span></span> <span data-ttu-id="1f834-139">此元素的类型为 <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="1f834-139">This element is of type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span></span>|  
|[\<message>](message-element-of-nettcpbinding.md)|<span data-ttu-id="1f834-140">定义消息的安全设置。</span><span class="sxs-lookup"><span data-stu-id="1f834-140">Defines the security settings for the message.</span></span> <span data-ttu-id="1f834-141">此元素的类型为 <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>。</span><span class="sxs-lookup"><span data-stu-id="1f834-141">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1f834-142">父元素</span><span class="sxs-lookup"><span data-stu-id="1f834-142">Parent Elements</span></span>  
  
|<span data-ttu-id="1f834-143">元素</span><span class="sxs-lookup"><span data-stu-id="1f834-143">Element</span></span>|<span data-ttu-id="1f834-144">描述</span><span class="sxs-lookup"><span data-stu-id="1f834-144">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1f834-145">binding</span><span class="sxs-lookup"><span data-stu-id="1f834-145">binding</span></span>|<span data-ttu-id="1f834-146">的绑定元素 [\<netTcpBinding>](nettcpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="1f834-146">The binding element of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f834-147">备注</span><span class="sxs-lookup"><span data-stu-id="1f834-147">Remarks</span></span>  

 <span data-ttu-id="1f834-148">每个标准绑定都提供用于控制传输安全性需求的参数。</span><span class="sxs-lookup"><span data-stu-id="1f834-148">Each of the standard bindings provides parameters for controlling the transfer security requirements.</span></span> <span data-ttu-id="1f834-149">这些参数通常包括指定是使用消息级安全性还是使用传输级安全性的安全模式，还包括客户端凭据类型的选项。</span><span class="sxs-lookup"><span data-stu-id="1f834-149">These parameters typically include the security mode that specified whether message-level or transport-level security is used and the choice of client credential type.</span></span> <span data-ttu-id="1f834-150">基于这些参数提供的可供选择的选项，构建一个具有适当安全性的信道堆栈。</span><span class="sxs-lookup"><span data-stu-id="1f834-150">Based on the choice of options these parameters present, a channel stack is constructed with appropriate security.</span></span>  
  
 <span data-ttu-id="1f834-151">由 Windows Communication Foundation (WCF) 提供的系统提供的绑定是一组旨在满足一些最常见的方案要求的绑定。</span><span class="sxs-lookup"><span data-stu-id="1f834-151">The system-provided bindings supplied by Windows Communication Foundation (WCF) are a set designed to meet some of the most common scenario requirements.</span></span> <span data-ttu-id="1f834-152">所有这些绑定都允许为某些特定的目标方案指定安全要求。</span><span class="sxs-lookup"><span data-stu-id="1f834-152">Each of these bindings allows the specification of security requirements for some specific targeted scenarios.</span></span>  
  
 <span data-ttu-id="1f834-153">此配置元素提供用于 `netTcpBinding` 的安全规范。</span><span class="sxs-lookup"><span data-stu-id="1f834-153">This configuration element provides the security specifications for `netTcpBinding`.</span></span> <span data-ttu-id="1f834-154">这是一种适合于跨计算机通信的安全、可靠且进行了优化的绑定。</span><span class="sxs-lookup"><span data-stu-id="1f834-154">This is a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="1f834-155">默认情况下，它生成运行时通信堆栈，该堆栈支持用于消息传递的 TCP、消息安全性和身份验证的 Windows 安全、可靠的 WS-ReliableMessaging，以及二进制消息编码。</span><span class="sxs-lookup"><span data-stu-id="1f834-155">By default it generates a runtime communication stack supporting TCP for message delivery and Windows Security for message security and authentication, WS-ReliableMessaging for reliability, and binary message encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f834-156">请参阅</span><span class="sxs-lookup"><span data-stu-id="1f834-156">See also</span></span>

- <xref:System.ServiceModel.NetTcpSecurity>
- <xref:System.ServiceModel.NetTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="1f834-157">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="1f834-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="1f834-158">绑定</span><span class="sxs-lookup"><span data-stu-id="1f834-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1f834-159">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="1f834-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1f834-160">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="1f834-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

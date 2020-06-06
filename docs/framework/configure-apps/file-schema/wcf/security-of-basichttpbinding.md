---
title: <security> 的 <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
ms.openlocfilehash: c8e4f2d000a155eecd2a6c7faaaf4af525b24ca3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738717"
---
# <a name="security-of-basichttpbinding"></a><span data-ttu-id="b377c-102">\<security> 的 \<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="b377c-102">\<security> of \<basicHttpBinding></span></span>
<span data-ttu-id="b377c-103">定义的安全功能 [\<basicHttpBinding>](basichttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="b377c-103">Defines the security capabilities of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="b377c-104">语法</span><span class="sxs-lookup"><span data-stu-id="b377c-104">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b377c-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="b377c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="b377c-106">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b377c-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b377c-107">特性</span><span class="sxs-lookup"><span data-stu-id="b377c-107">Attributes</span></span>  
  
|<span data-ttu-id="b377c-108">属性</span><span class="sxs-lookup"><span data-stu-id="b377c-108">Attribute</span></span>|<span data-ttu-id="b377c-109">说明</span><span class="sxs-lookup"><span data-stu-id="b377c-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b377c-110">模式</span><span class="sxs-lookup"><span data-stu-id="b377c-110">mode</span></span>|<span data-ttu-id="b377c-111">可选。</span><span class="sxs-lookup"><span data-stu-id="b377c-111">Optional.</span></span> <span data-ttu-id="b377c-112">指定所使用的安全类型。</span><span class="sxs-lookup"><span data-stu-id="b377c-112">Specifies the type of security that is used.</span></span> <span data-ttu-id="b377c-113">默认为 `None`。</span><span class="sxs-lookup"><span data-stu-id="b377c-113">The default is `None`.</span></span> <span data-ttu-id="b377c-114">此属性的类型为 <xref:System.ServiceModel.BasicHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="b377c-114">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="b377c-115">mode 属性</span><span class="sxs-lookup"><span data-stu-id="b377c-115">mode Attribute</span></span>  
  
|<span data-ttu-id="b377c-116">值</span><span class="sxs-lookup"><span data-stu-id="b377c-116">Value</span></span>|<span data-ttu-id="b377c-117">说明</span><span class="sxs-lookup"><span data-stu-id="b377c-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b377c-118">无</span><span class="sxs-lookup"><span data-stu-id="b377c-118">None</span></span>|<span data-ttu-id="b377c-119">-传输过程中消息不受保护。</span><span class="sxs-lookup"><span data-stu-id="b377c-119">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="b377c-120">Transport</span><span class="sxs-lookup"><span data-stu-id="b377c-120">Transport</span></span>|<span data-ttu-id="b377c-121">使用 HTTPS 传输提供安全性。</span><span class="sxs-lookup"><span data-stu-id="b377c-121">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="b377c-122">使用 HTTPS 对 SOAP 消息进行保护。</span><span class="sxs-lookup"><span data-stu-id="b377c-122">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="b377c-123">使用服务的 X.509 证书向客户端对服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="b377c-123">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="b377c-124">使用所提供的 ClientCredentialType 对客户端进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="b377c-124">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="b377c-125">请参阅 [\<transport>](transport-of-basichttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="b377c-125">See the [\<transport>](transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="b377c-126">消息</span><span class="sxs-lookup"><span data-stu-id="b377c-126">Message</span></span>|<span data-ttu-id="b377c-127">使用 SOAP 消息安全提供安全性。</span><span class="sxs-lookup"><span data-stu-id="b377c-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="b377c-128">默认情况下，将对正文进行加密和签名。</span><span class="sxs-lookup"><span data-stu-id="b377c-128">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="b377c-129">对于此绑定，系统要求向带外客户端提供服务器证书。</span><span class="sxs-lookup"><span data-stu-id="b377c-129">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="b377c-130">此绑定仅有的有效 `ClientCredentialType` 为 `Certificate`。</span><span class="sxs-lookup"><span data-stu-id="b377c-130">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="b377c-131">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="b377c-131">TransportWithMessageCredential</span></span>|<span data-ttu-id="b377c-132">完整性、保密性和服务器身份验证由传输安全来提供。</span><span class="sxs-lookup"><span data-stu-id="b377c-132">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="b377c-133">客户端身份验证采用 SOAP 消息安全方式提供。</span><span class="sxs-lookup"><span data-stu-id="b377c-133">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="b377c-134">如果要使用用户名/密码对用户进行身份验证，并且存在用于保护消息传输的现有 HTTP 部署，则适用此模式。</span><span class="sxs-lookup"><span data-stu-id="b377c-134">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="b377c-135">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="b377c-135">TransportCredentialOnly</span></span>|<span data-ttu-id="b377c-136">此模式并不提供消息的完整性和保密性，</span><span class="sxs-lookup"><span data-stu-id="b377c-136">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="b377c-137">而是提供基于 http 的客户端身份验证。</span><span class="sxs-lookup"><span data-stu-id="b377c-137">It provides http-based client authentication.</span></span> <span data-ttu-id="b377c-138">使用此模式时应当小心。</span><span class="sxs-lookup"><span data-stu-id="b377c-138">This mode should be used with caution.</span></span> <span data-ttu-id="b377c-139">在通过其他方式（如 IPSec）提供传输安全，并且 WCF 基础结构仅提供客户端身份验证的环境中，应使用此方法。</span><span class="sxs-lookup"><span data-stu-id="b377c-139">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b377c-140">子元素</span><span class="sxs-lookup"><span data-stu-id="b377c-140">Child Elements</span></span>  
  
|<span data-ttu-id="b377c-141">元素</span><span class="sxs-lookup"><span data-stu-id="b377c-141">Element</span></span>|<span data-ttu-id="b377c-142">描述</span><span class="sxs-lookup"><span data-stu-id="b377c-142">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-basichttpbinding.md)|<span data-ttu-id="b377c-143">定义基本 HTTP 服务的传输安全设置。</span><span class="sxs-lookup"><span data-stu-id="b377c-143">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="b377c-144">此元素与 <xref:System.ServiceModel.HttpTransportSecurity> 相对应。</span><span class="sxs-lookup"><span data-stu-id="b377c-144">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[\<message>](message-of-basichttpbinding.md)|<span data-ttu-id="b377c-145">定义基本 HTTP 服务的消息安全设置。</span><span class="sxs-lookup"><span data-stu-id="b377c-145">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="b377c-146">此元素与 <xref:System.ServiceModel.BasicHttpMessageSecurity> 相对应。</span><span class="sxs-lookup"><span data-stu-id="b377c-146">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b377c-147">父元素</span><span class="sxs-lookup"><span data-stu-id="b377c-147">Parent Elements</span></span>  
  
|<span data-ttu-id="b377c-148">元素</span><span class="sxs-lookup"><span data-stu-id="b377c-148">Element</span></span>|<span data-ttu-id="b377c-149">描述</span><span class="sxs-lookup"><span data-stu-id="b377c-149">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b377c-150">binding</span><span class="sxs-lookup"><span data-stu-id="b377c-150">binding</span></span>|<span data-ttu-id="b377c-151">的绑定元素 [\<basicHttpBinding>](basichttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="b377c-151">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b377c-152">注解</span><span class="sxs-lookup"><span data-stu-id="b377c-152">Remarks</span></span>  
 <span data-ttu-id="b377c-153">默认情况下，不会对 SOAP 消息进行保护，也不会对客户端进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="b377c-153">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="b377c-154">使用此元素，您可以配置 `basicHttpBinding` 元素的其他安全设置。</span><span class="sxs-lookup"><span data-stu-id="b377c-154">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b377c-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b377c-155">See also</span></span>

- <xref:System.ServiceModel.BasicHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="b377c-156">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="b377c-156">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b377c-157">选择凭据类型</span><span class="sxs-lookup"><span data-stu-id="b377c-157">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="b377c-158">绑定</span><span class="sxs-lookup"><span data-stu-id="b377c-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b377c-159">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="b377c-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b377c-160">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="b377c-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

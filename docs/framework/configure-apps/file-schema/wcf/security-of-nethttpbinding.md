---
title: <security> 的 <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: 97c52fa4f062ed0c65d5b1a8ca47a1439ab04cf5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736491"
---
# <a name="security-of-nethttpbinding"></a><span data-ttu-id="2dfab-102">\<security> 的 \<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="2dfab-102">\<security> of \<netHttpBinding></span></span>

<span data-ttu-id="2dfab-103">定义的安全功能 [\<netHttpBinding>](nethttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="2dfab-103">Defines the security capabilities of the [\<netHttpBinding>](nethttpbinding.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  

## <a name="syntax"></a><span data-ttu-id="2dfab-104">语法</span><span class="sxs-lookup"><span data-stu-id="2dfab-104">Syntax</span></span>

```xml
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2dfab-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="2dfab-105">Attributes and elements</span></span>

<span data-ttu-id="2dfab-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2dfab-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="2dfab-107">特性</span><span class="sxs-lookup"><span data-stu-id="2dfab-107">Attributes</span></span>

|<span data-ttu-id="2dfab-108">属性</span><span class="sxs-lookup"><span data-stu-id="2dfab-108">Attribute</span></span>|<span data-ttu-id="2dfab-109">说明</span><span class="sxs-lookup"><span data-stu-id="2dfab-109">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="2dfab-110">模式</span><span class="sxs-lookup"><span data-stu-id="2dfab-110">mode</span></span>|<span data-ttu-id="2dfab-111">可选。</span><span class="sxs-lookup"><span data-stu-id="2dfab-111">Optional.</span></span> <span data-ttu-id="2dfab-112">指定所使用的安全类型。</span><span class="sxs-lookup"><span data-stu-id="2dfab-112">Specifies the type of security that is used.</span></span> <span data-ttu-id="2dfab-113">默认为 `None`。</span><span class="sxs-lookup"><span data-stu-id="2dfab-113">The default is `None`.</span></span> <span data-ttu-id="2dfab-114">此属性的类型为 <xref:System.ServiceModel.BasicHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="2dfab-114">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|

## <a name="mode-attribute"></a><span data-ttu-id="2dfab-115">mode 特性</span><span class="sxs-lookup"><span data-stu-id="2dfab-115">mode attribute</span></span>

|<span data-ttu-id="2dfab-116">值</span><span class="sxs-lookup"><span data-stu-id="2dfab-116">Value</span></span>|<span data-ttu-id="2dfab-117">说明</span><span class="sxs-lookup"><span data-stu-id="2dfab-117">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="2dfab-118">无</span><span class="sxs-lookup"><span data-stu-id="2dfab-118">None</span></span>|<span data-ttu-id="2dfab-119">-传输过程中消息不受保护。</span><span class="sxs-lookup"><span data-stu-id="2dfab-119">-   Messages are not secured during transfer.</span></span>|
|<span data-ttu-id="2dfab-120">Transport</span><span class="sxs-lookup"><span data-stu-id="2dfab-120">Transport</span></span>|<span data-ttu-id="2dfab-121">使用 HTTPS 传输提供安全性。</span><span class="sxs-lookup"><span data-stu-id="2dfab-121">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="2dfab-122">使用 HTTPS 对 SOAP 消息进行保护。</span><span class="sxs-lookup"><span data-stu-id="2dfab-122">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="2dfab-123">使用服务的 X.509 证书向客户端对服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="2dfab-123">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="2dfab-124">使用所提供的 ClientCredentialType 对客户端进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="2dfab-124">The client is authenticated using the ClientCredentialType supplied.</span></span>|
|<span data-ttu-id="2dfab-125">消息</span><span class="sxs-lookup"><span data-stu-id="2dfab-125">Message</span></span>|<span data-ttu-id="2dfab-126">使用 SOAP 消息安全提供安全性。</span><span class="sxs-lookup"><span data-stu-id="2dfab-126">Security is provided using SOAP message security.</span></span> <span data-ttu-id="2dfab-127">默认情况下，将对正文进行加密和签名。</span><span class="sxs-lookup"><span data-stu-id="2dfab-127">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="2dfab-128">对于此绑定，系统要求向带外客户端提供服务器证书。</span><span class="sxs-lookup"><span data-stu-id="2dfab-128">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="2dfab-129">此绑定仅有的有效 `ClientCredentialType` 为 `Certificate`。</span><span class="sxs-lookup"><span data-stu-id="2dfab-129">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|
|<span data-ttu-id="2dfab-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="2dfab-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="2dfab-131">完整性、保密性和服务器身份验证由传输安全来提供。</span><span class="sxs-lookup"><span data-stu-id="2dfab-131">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="2dfab-132">客户端身份验证采用 SOAP 消息安全方式提供。</span><span class="sxs-lookup"><span data-stu-id="2dfab-132">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="2dfab-133">如果要使用用户名/密码对用户进行身份验证，并且存在用于保护消息传输的现有 HTTP 部署，则适用此模式。</span><span class="sxs-lookup"><span data-stu-id="2dfab-133">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|
|<span data-ttu-id="2dfab-134">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="2dfab-134">TransportCredentialOnly</span></span>|<span data-ttu-id="2dfab-135">此模式并不提供消息的完整性和保密性，</span><span class="sxs-lookup"><span data-stu-id="2dfab-135">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="2dfab-136">而是提供基于 http 的客户端身份验证。</span><span class="sxs-lookup"><span data-stu-id="2dfab-136">It provides http-based client authentication.</span></span> <span data-ttu-id="2dfab-137">使用此模式时应当小心。</span><span class="sxs-lookup"><span data-stu-id="2dfab-137">This mode should be used with caution.</span></span> <span data-ttu-id="2dfab-138">在通过其他方式（如 IPSec）提供传输安全，并且 WCF 基础结构仅提供客户端身份验证的环境中，应使用此方法。</span><span class="sxs-lookup"><span data-stu-id="2dfab-138">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="2dfab-139">子元素</span><span class="sxs-lookup"><span data-stu-id="2dfab-139">Child elements</span></span>

|<span data-ttu-id="2dfab-140">元素</span><span class="sxs-lookup"><span data-stu-id="2dfab-140">Element</span></span>|<span data-ttu-id="2dfab-141">描述</span><span class="sxs-lookup"><span data-stu-id="2dfab-141">Description</span></span>|
|-------------|-----------------|
|[\<transport>](transport-of-nethttpbinding.md)|<span data-ttu-id="2dfab-142">定义基本 HTTP 服务的传输安全设置。</span><span class="sxs-lookup"><span data-stu-id="2dfab-142">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="2dfab-143">此元素与 <xref:System.ServiceModel.HttpTransportSecurity> 相对应。</span><span class="sxs-lookup"><span data-stu-id="2dfab-143">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|
|[\<message>](message-of-nethttpbinding.md)|<span data-ttu-id="2dfab-144">定义基本 HTTP 服务的消息安全设置。</span><span class="sxs-lookup"><span data-stu-id="2dfab-144">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="2dfab-145">此元素与 <xref:System.ServiceModel.BasicHttpMessageSecurity> 相对应。</span><span class="sxs-lookup"><span data-stu-id="2dfab-145">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2dfab-146">父元素</span><span class="sxs-lookup"><span data-stu-id="2dfab-146">Parent elements</span></span>

|<span data-ttu-id="2dfab-147">元素</span><span class="sxs-lookup"><span data-stu-id="2dfab-147">Element</span></span>|<span data-ttu-id="2dfab-148">描述</span><span class="sxs-lookup"><span data-stu-id="2dfab-148">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="2dfab-149">binding</span><span class="sxs-lookup"><span data-stu-id="2dfab-149">binding</span></span>|<span data-ttu-id="2dfab-150">的绑定元素 [\<basicHttpBinding>](basichttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="2dfab-150">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|

## <a name="remarks"></a><span data-ttu-id="2dfab-151">注解</span><span class="sxs-lookup"><span data-stu-id="2dfab-151">Remarks</span></span>

 <span data-ttu-id="2dfab-152">默认情况下，不会对 SOAP 消息进行保护，也不会对客户端进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="2dfab-152">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="2dfab-153">使用此元素，您可以配置 `netHttpBinding` 元素的其他安全设置。</span><span class="sxs-lookup"><span data-stu-id="2dfab-153">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="2dfab-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2dfab-154">See also</span></span>

- <xref:System.ServiceModel.NetHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>  
- [<span data-ttu-id="2dfab-155">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="2dfab-155">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="2dfab-156">选择凭据类型</span><span class="sxs-lookup"><span data-stu-id="2dfab-156">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="2dfab-157">绑定</span><span class="sxs-lookup"><span data-stu-id="2dfab-157">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2dfab-158">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="2dfab-158">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="2dfab-159">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="2dfab-159">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

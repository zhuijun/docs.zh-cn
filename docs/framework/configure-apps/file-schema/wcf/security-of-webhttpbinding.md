---
title: <security> 的 <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: 77009dc950a608da9e0db3a7d09be67e1ed46137
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738638"
---
# <a name="security-of-webhttpbinding"></a><span data-ttu-id="f1aab-102">\<security> 的 \<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="f1aab-102">\<security> of \<webHttpBinding></span></span>
<span data-ttu-id="f1aab-103">指定用配置的终结点的安全要求 [\<webHttpBinding>](webhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="f1aab-103">Specifies the security requirements for an endpoint configured with a [\<webHttpBinding>](webhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="f1aab-104">语法</span><span class="sxs-lookup"><span data-stu-id="f1aab-104">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <bindings>
    <webHttpBinding>
      <binding name = "String">
        <security mode="None/Transport/TransportCredentialOnly">
          <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                     proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                     realm="String" />
        </security>
      </binding>
    </webHttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1aab-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="f1aab-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f1aab-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f1aab-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1aab-107">特性</span><span class="sxs-lookup"><span data-stu-id="f1aab-107">Attributes</span></span>  
  
|<span data-ttu-id="f1aab-108">属性</span><span class="sxs-lookup"><span data-stu-id="f1aab-108">Attribute</span></span>|<span data-ttu-id="f1aab-109">说明</span><span class="sxs-lookup"><span data-stu-id="f1aab-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f1aab-110">模式</span><span class="sxs-lookup"><span data-stu-id="f1aab-110">mode</span></span>|<span data-ttu-id="f1aab-111">指定终结点是使用传输级安全模式还是不使用安全模式。</span><span class="sxs-lookup"><span data-stu-id="f1aab-111">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="f1aab-112">默认为 `None`。</span><span class="sxs-lookup"><span data-stu-id="f1aab-112">The default is `None`.</span></span> <span data-ttu-id="f1aab-113">此属性的类型为 <xref:System.ServiceModel.WebHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="f1aab-113">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="f1aab-114">Mode 属性</span><span class="sxs-lookup"><span data-stu-id="f1aab-114">Mode Attribute</span></span>  
  
|<span data-ttu-id="f1aab-115">值</span><span class="sxs-lookup"><span data-stu-id="f1aab-115">Value</span></span>|<span data-ttu-id="f1aab-116">说明</span><span class="sxs-lookup"><span data-stu-id="f1aab-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f1aab-117">无</span><span class="sxs-lookup"><span data-stu-id="f1aab-117">None</span></span>|<span data-ttu-id="f1aab-118">禁用安全性。</span><span class="sxs-lookup"><span data-stu-id="f1aab-118">Security is disabled.</span></span>|  
|<span data-ttu-id="f1aab-119">Transport</span><span class="sxs-lookup"><span data-stu-id="f1aab-119">Transport</span></span>|<span data-ttu-id="f1aab-120">使用 HTTPS 提供安全性。</span><span class="sxs-lookup"><span data-stu-id="f1aab-120">Security is provided using HTTPS.</span></span> <span data-ttu-id="f1aab-121">此服务需要使用 SSL 证书进行配置。</span><span class="sxs-lookup"><span data-stu-id="f1aab-121">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="f1aab-122">消息使用 HTTPS 获得全面保护，而且客户端使用服务的 SSL 证书对服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="f1aab-122">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="f1aab-123">客户端身份验证通过 `ClientCredentialType` 的属性进行控制 [\<transport>](transport-of-webhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="f1aab-123">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="f1aab-124">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="f1aab-124">TransportCredentialOnly</span></span>|<span data-ttu-id="f1aab-125">此模式并不提供消息的完整性和保密性，</span><span class="sxs-lookup"><span data-stu-id="f1aab-125">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="f1aab-126">而是提供基于 HTTP 的客户端身份验证。</span><span class="sxs-lookup"><span data-stu-id="f1aab-126">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="f1aab-127">使用此模式时应当小心。</span><span class="sxs-lookup"><span data-stu-id="f1aab-127">This mode should be used with caution.</span></span> <span data-ttu-id="f1aab-128">在通过其他方式（如 IPSec）提供传输安全，并且 WCF 基础结构仅提供客户端身份验证的环境中，应使用此方法。</span><span class="sxs-lookup"><span data-stu-id="f1aab-128">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f1aab-129">子元素</span><span class="sxs-lookup"><span data-stu-id="f1aab-129">Child Elements</span></span>  
  
|<span data-ttu-id="f1aab-130">元素</span><span class="sxs-lookup"><span data-stu-id="f1aab-130">Element</span></span>|<span data-ttu-id="f1aab-131">描述</span><span class="sxs-lookup"><span data-stu-id="f1aab-131">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-webhttpbinding.md)|<span data-ttu-id="f1aab-132">定义传输安全设置。</span><span class="sxs-lookup"><span data-stu-id="f1aab-132">Defines the transport security settings.</span></span> <span data-ttu-id="f1aab-133">此元素与 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 类型相对应。</span><span class="sxs-lookup"><span data-stu-id="f1aab-133">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f1aab-134">父元素</span><span class="sxs-lookup"><span data-stu-id="f1aab-134">Parent Elements</span></span>  
  
|<span data-ttu-id="f1aab-135">元素</span><span class="sxs-lookup"><span data-stu-id="f1aab-135">Element</span></span>|<span data-ttu-id="f1aab-136">描述</span><span class="sxs-lookup"><span data-stu-id="f1aab-136">Description</span></span>|  
|-------------|-----------------|  
|[\<webHttpBinding>](webhttpbinding.md)|<span data-ttu-id="f1aab-137">一个绑定元素，用于为响应 HTTP 请求（而不是 SOAP 消息）的 Windows Communication Foundation （WCF） Web 服务配置终结点。</span><span class="sxs-lookup"><span data-stu-id="f1aab-137">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f1aab-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f1aab-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [<span data-ttu-id="f1aab-139">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="f1aab-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f1aab-140">选择凭据类型</span><span class="sxs-lookup"><span data-stu-id="f1aab-140">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="f1aab-141">绑定</span><span class="sxs-lookup"><span data-stu-id="f1aab-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f1aab-142">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="f1aab-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f1aab-143">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="f1aab-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="f1aab-144">WCF Web HTTP 编程模型</span><span class="sxs-lookup"><span data-stu-id="f1aab-144">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)

---
title: <add> 的 <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 4e7b7637-e0ea-4a91-988f-6b6ef28d9fc3
ms.openlocfilehash: bcbc9c7dbc5b57da2de2685fff8eee4aca64f7cc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181682"
---
# <a name="add-of-allowedaudienceuris"></a><span data-ttu-id="04d76-102">\<add> 的 \<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="04d76-102">\<add> of \<allowedAudienceUris></span></span>

<span data-ttu-id="04d76-103">添加 <xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全令牌的目标 URI，只有在使用该目标 URI 时，<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 实例才会将该令牌视为有效令牌。</span><span class="sxs-lookup"><span data-stu-id="04d76-103">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<allowedAudienceUris>**](allowedaudienceuris.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="04d76-104">语法</span><span class="sxs-lookup"><span data-stu-id="04d76-104">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04d76-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="04d76-105">Attributes and Elements</span></span>  

 <span data-ttu-id="04d76-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="04d76-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04d76-107">特性</span><span class="sxs-lookup"><span data-stu-id="04d76-107">Attributes</span></span>  
  
|<span data-ttu-id="04d76-108">属性</span><span class="sxs-lookup"><span data-stu-id="04d76-108">Attribute</span></span>|<span data-ttu-id="04d76-109">描述</span><span class="sxs-lookup"><span data-stu-id="04d76-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="04d76-110">allowedAudienceUri</span><span class="sxs-lookup"><span data-stu-id="04d76-110">allowedAudienceUri</span></span>|<span data-ttu-id="04d76-111">一个包含 <xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全令牌的目标 URI 的字符串，只有在使用该目标 URI 时，<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 实例才会将该令牌视为有效令牌。</span><span class="sxs-lookup"><span data-stu-id="04d76-111">A string that contains a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="04d76-112">子元素</span><span class="sxs-lookup"><span data-stu-id="04d76-112">Child Elements</span></span>  

 <span data-ttu-id="04d76-113">无。</span><span class="sxs-lookup"><span data-stu-id="04d76-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="04d76-114">父元素</span><span class="sxs-lookup"><span data-stu-id="04d76-114">Parent Elements</span></span>  
  
|<span data-ttu-id="04d76-115">元素</span><span class="sxs-lookup"><span data-stu-id="04d76-115">Element</span></span>|<span data-ttu-id="04d76-116">描述</span><span class="sxs-lookup"><span data-stu-id="04d76-116">Description</span></span>|  
|-------------|-----------------|  
|[\<allowedAudienceUris>](allowedaudienceuris.md)|<span data-ttu-id="04d76-117">表示 <xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全令牌的目标 URI 集合，只有在使用这些目标 URI 时，<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 实例才会将该令牌视为有效令牌。</span><span class="sxs-lookup"><span data-stu-id="04d76-117">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04d76-118">备注</span><span class="sxs-lookup"><span data-stu-id="04d76-118">Remarks</span></span>  

 <span data-ttu-id="04d76-119">在采用颁发 <xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全令牌的安全令牌服务 (STS) 的联合应用程序中，应使用此集合。</span><span class="sxs-lookup"><span data-stu-id="04d76-119">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="04d76-120">当 STS 颁发安全令牌时，它可以通过将 <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> 添加到安全令牌中，来指定安全令牌的目标 Web 服务的 URI。</span><span class="sxs-lookup"><span data-stu-id="04d76-120">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="04d76-121">这样，通过指定应采用以下方式执行此检查，接收方 Web 服务的 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 将能够验证颁发的安全令牌是否针对此 Web 服务：</span><span class="sxs-lookup"><span data-stu-id="04d76-121">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="04d76-122">将 `audienceUriMode` 的 `<issuedTokenAuthentication>` 属性设置为 <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> 或 <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>。</span><span class="sxs-lookup"><span data-stu-id="04d76-122">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="04d76-123">将有效 URI 添加到此集合，以指定有效 URI 集。</span><span class="sxs-lookup"><span data-stu-id="04d76-123">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="04d76-124">有关详细信息，请参阅 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>。</span><span class="sxs-lookup"><span data-stu-id="04d76-124">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="04d76-125">有关使用此配置元素的详细信息，请参阅 [如何：在联合身份验证服务上配置凭据](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)。</span><span class="sxs-lookup"><span data-stu-id="04d76-125">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04d76-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="04d76-126">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [\<allowedAudienceUris>](allowedaudienceuris.md)
- [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="04d76-127">安全行为</span><span class="sxs-lookup"><span data-stu-id="04d76-127">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="04d76-128">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="04d76-128">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="04d76-129">如何：在联合身份验证服务上配置凭据</span><span class="sxs-lookup"><span data-stu-id="04d76-129">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)

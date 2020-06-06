---
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 8432463ff62e4b5e54a491b574cc6a5285efe220
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397958"
---
# \<issuedTokenParameters>
<span data-ttu-id="64664-101">指定在联合安全方案中颁发的安全令牌的参数。</span><span class="sxs-lookup"><span data-stu-id="64664-101">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenParameters>**  
  
## <a name="syntax"></a><span data-ttu-id="64664-102">语法</span><span class="sxs-lookup"><span data-stu-id="64664-102">Syntax</span></span>  
  
```xml  
<issuedTokenParameters defaultMessageSecurityVersion="System.ServiceModel.MessageSecurityVersion"
                       inclusionMode="AlwaysToInitiator/AlwaysToRecipient/Never/Once"
                       keySize="Integer"
                       keyType="AsymmetricKey/BearerKey/SymmetricKey"
                       tokenType="String">
  <additionalRequestParameters />
  <claimTypeRequirements>
    <add claimType="URI"
         isOptional="Boolean" />
  </claimTypeRequirements>
  <issuer address="String"
          binding="" />
  <issuerMetadata address="String" />
</issuedTokenParameters>
```  
  
## <a name="type"></a><span data-ttu-id="64664-103">类型</span><span class="sxs-lookup"><span data-stu-id="64664-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64664-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="64664-104">Attributes and Elements</span></span>  
 <span data-ttu-id="64664-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="64664-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="64664-106">特性</span><span class="sxs-lookup"><span data-stu-id="64664-106">Attributes</span></span>  
  
|<span data-ttu-id="64664-107">属性</span><span class="sxs-lookup"><span data-stu-id="64664-107">Attribute</span></span>|<span data-ttu-id="64664-108">说明</span><span class="sxs-lookup"><span data-stu-id="64664-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="64664-109">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="64664-109">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="64664-110">指定安全规范（WS-Security、WS-Trust、WS-Secure Conversation 和 WS-Security Policy）的版本，绑定必须支持这些安全规范。</span><span class="sxs-lookup"><span data-stu-id="64664-110">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="64664-111">此值的类型为 <xref:System.ServiceModel.MessageSecurityVersion>。</span><span class="sxs-lookup"><span data-stu-id="64664-111">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="64664-112">inclusionMode</span><span class="sxs-lookup"><span data-stu-id="64664-112">inclusionMode</span></span>|<span data-ttu-id="64664-113">指定令牌包含要求。</span><span class="sxs-lookup"><span data-stu-id="64664-113">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="64664-114">此属性的类型为 <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>。</span><span class="sxs-lookup"><span data-stu-id="64664-114">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="64664-115">keySize</span><span class="sxs-lookup"><span data-stu-id="64664-115">keySize</span></span>|<span data-ttu-id="64664-116">一个指定令牌的密钥大小的整数。</span><span class="sxs-lookup"><span data-stu-id="64664-116">An integer that specifies the token key size.</span></span> <span data-ttu-id="64664-117">默认值为 256。</span><span class="sxs-lookup"><span data-stu-id="64664-117">The default value is 256.</span></span>|  
|<span data-ttu-id="64664-118">keyType</span><span class="sxs-lookup"><span data-stu-id="64664-118">keyType</span></span>|<span data-ttu-id="64664-119">一个指定密钥类型的 <xref:System.IdentityModel.Tokens.SecurityKeyType> 的有效值。</span><span class="sxs-lookup"><span data-stu-id="64664-119">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="64664-120">默认为 `SymmetricKey`。</span><span class="sxs-lookup"><span data-stu-id="64664-120">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="64664-121">tokenType</span><span class="sxs-lookup"><span data-stu-id="64664-121">tokenType</span></span>|<span data-ttu-id="64664-122">一个指定令牌类型的字符串。</span><span class="sxs-lookup"><span data-stu-id="64664-122">A string that specifies the token type.</span></span> <span data-ttu-id="64664-123">默认值为“http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML”。</span><span class="sxs-lookup"><span data-stu-id="64664-123">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="64664-124">子元素</span><span class="sxs-lookup"><span data-stu-id="64664-124">Child Elements</span></span>  
  
|<span data-ttu-id="64664-125">元素</span><span class="sxs-lookup"><span data-stu-id="64664-125">Element</span></span>|<span data-ttu-id="64664-126">描述</span><span class="sxs-lookup"><span data-stu-id="64664-126">Description</span></span>|  
|-------------|-----------------|  
|[\<additionalRequestParameters>](additionalrequestparameters-element.md)|<span data-ttu-id="64664-127">一个用于指定附加请求参数的配置元素的集合。</span><span class="sxs-lookup"><span data-stu-id="64664-127">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="64664-128">指定所需声明类型的集合。</span><span class="sxs-lookup"><span data-stu-id="64664-128">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="64664-129">在联合方案中，服务规定有关传入凭据的要求。</span><span class="sxs-lookup"><span data-stu-id="64664-129">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="64664-130">例如，传入凭据必须具有某组声明类型。</span><span class="sxs-lookup"><span data-stu-id="64664-130">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="64664-131">此集合中的每个元素都指定希望出现在联合凭据中的必选和可选的声明类型。</span><span class="sxs-lookup"><span data-stu-id="64664-131">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[\<issuer>](issuer-of-issuedtokenparameters.md)|<span data-ttu-id="64664-132">一个用于指定颁发当前令牌的终结点的配置元素。</span><span class="sxs-lookup"><span data-stu-id="64664-132">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[\<issuerMetadata>](issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="64664-133">一个用于指定令牌颁发者的元数据的终结点地址的配置元素。</span><span class="sxs-lookup"><span data-stu-id="64664-133">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="64664-134">父元素</span><span class="sxs-lookup"><span data-stu-id="64664-134">Parent Elements</span></span>  
  
|<span data-ttu-id="64664-135">元素</span><span class="sxs-lookup"><span data-stu-id="64664-135">Element</span></span>|<span data-ttu-id="64664-136">描述</span><span class="sxs-lookup"><span data-stu-id="64664-136">Description</span></span>|  
|-------------|-----------------|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|<span data-ttu-id="64664-137">指定用于启动安全对话服务的默认值。</span><span class="sxs-lookup"><span data-stu-id="64664-137">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[\<security>](security-of-custombinding.md)|<span data-ttu-id="64664-138">指定自定义绑定的安全选项。</span><span class="sxs-lookup"><span data-stu-id="64664-138">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="64664-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="64664-139">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="64664-140">绑定</span><span class="sxs-lookup"><span data-stu-id="64664-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="64664-141">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="64664-141">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="64664-142">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="64664-142">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="64664-143">如何：使用 SecurityBindingElement 创建自定义绑定</span><span class="sxs-lookup"><span data-stu-id="64664-143">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="64664-144">自定义绑定安全性</span><span class="sxs-lookup"><span data-stu-id="64664-144">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
- [<span data-ttu-id="64664-145">服务标识和身份验证</span><span class="sxs-lookup"><span data-stu-id="64664-145">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="64664-146">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="64664-146">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="64664-147">使用自定义绑定的安全功能</span><span class="sxs-lookup"><span data-stu-id="64664-147">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="64664-148">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="64664-148">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)

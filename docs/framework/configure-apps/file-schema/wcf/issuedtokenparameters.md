---
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: c90024a0629f39d160967ca00434e48f682d8933
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157312"
---
# \<issuedTokenParameters>

<span data-ttu-id="6a6d2-101">指定在联合安全方案中颁发的安全令牌的参数。</span><span class="sxs-lookup"><span data-stu-id="6a6d2-101">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenParameters>**  
  
## <a name="syntax"></a><span data-ttu-id="6a6d2-102">语法</span><span class="sxs-lookup"><span data-stu-id="6a6d2-102">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="6a6d2-103">类型</span><span class="sxs-lookup"><span data-stu-id="6a6d2-103">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a6d2-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="6a6d2-104">Attributes and Elements</span></span>  

 <span data-ttu-id="6a6d2-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6a6d2-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a6d2-106">特性</span><span class="sxs-lookup"><span data-stu-id="6a6d2-106">Attributes</span></span>  
  
|<span data-ttu-id="6a6d2-107">属性</span><span class="sxs-lookup"><span data-stu-id="6a6d2-107">Attribute</span></span>|<span data-ttu-id="6a6d2-108">描述</span><span class="sxs-lookup"><span data-stu-id="6a6d2-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6a6d2-109">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="6a6d2-109">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="6a6d2-110">指定安全规范（WS-Security、WS-Trust、WS-Secure Conversation 和 WS-Security Policy）的版本，绑定必须支持这些安全规范。</span><span class="sxs-lookup"><span data-stu-id="6a6d2-110">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="6a6d2-111">此值的类型为 <xref:System.ServiceModel.MessageSecurityVersion>。</span><span class="sxs-lookup"><span data-stu-id="6a6d2-111">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="6a6d2-112">inclusionMode</span><span class="sxs-lookup"><span data-stu-id="6a6d2-112">inclusionMode</span></span>|<span data-ttu-id="6a6d2-113">指定令牌包含要求。</span><span class="sxs-lookup"><span data-stu-id="6a6d2-113">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="6a6d2-114">此属性的类型为 <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>。</span><span class="sxs-lookup"><span data-stu-id="6a6d2-114">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="6a6d2-115">keySize</span><span class="sxs-lookup"><span data-stu-id="6a6d2-115">keySize</span></span>|<span data-ttu-id="6a6d2-116">一个指定令牌的密钥大小的整数。</span><span class="sxs-lookup"><span data-stu-id="6a6d2-116">An integer that specifies the token key size.</span></span> <span data-ttu-id="6a6d2-117">默认值为 256。</span><span class="sxs-lookup"><span data-stu-id="6a6d2-117">The default value is 256.</span></span>|  
|<span data-ttu-id="6a6d2-118">keyType</span><span class="sxs-lookup"><span data-stu-id="6a6d2-118">keyType</span></span>|<span data-ttu-id="6a6d2-119">一个指定密钥类型的 <xref:System.IdentityModel.Tokens.SecurityKeyType> 的有效值。</span><span class="sxs-lookup"><span data-stu-id="6a6d2-119">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="6a6d2-120">默认为 `SymmetricKey`。</span><span class="sxs-lookup"><span data-stu-id="6a6d2-120">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="6a6d2-121">tokenType</span><span class="sxs-lookup"><span data-stu-id="6a6d2-121">tokenType</span></span>|<span data-ttu-id="6a6d2-122">一个指定令牌类型的字符串。</span><span class="sxs-lookup"><span data-stu-id="6a6d2-122">A string that specifies the token type.</span></span> <span data-ttu-id="6a6d2-123">默认值为“http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML”。</span><span class="sxs-lookup"><span data-stu-id="6a6d2-123">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6a6d2-124">子元素</span><span class="sxs-lookup"><span data-stu-id="6a6d2-124">Child Elements</span></span>  
  
|<span data-ttu-id="6a6d2-125">元素</span><span class="sxs-lookup"><span data-stu-id="6a6d2-125">Element</span></span>|<span data-ttu-id="6a6d2-126">描述</span><span class="sxs-lookup"><span data-stu-id="6a6d2-126">Description</span></span>|  
|-------------|-----------------|  
|[\<additionalRequestParameters>](additionalrequestparameters-element.md)|<span data-ttu-id="6a6d2-127">一个用于指定附加请求参数的配置元素的集合。</span><span class="sxs-lookup"><span data-stu-id="6a6d2-127">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="6a6d2-128">指定所需声明类型的集合。</span><span class="sxs-lookup"><span data-stu-id="6a6d2-128">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="6a6d2-129">在联合方案中，服务规定有关传入凭据的要求。</span><span class="sxs-lookup"><span data-stu-id="6a6d2-129">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="6a6d2-130">例如，传入凭据必须具有某组声明类型。</span><span class="sxs-lookup"><span data-stu-id="6a6d2-130">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="6a6d2-131">此集合中的每个元素都指定希望出现在联合凭据中的必选和可选的声明类型。</span><span class="sxs-lookup"><span data-stu-id="6a6d2-131">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[\<issuer>](issuer-of-issuedtokenparameters.md)|<span data-ttu-id="6a6d2-132">一个用于指定颁发当前令牌的终结点的配置元素。</span><span class="sxs-lookup"><span data-stu-id="6a6d2-132">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[\<issuerMetadata>](issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="6a6d2-133">一个用于指定令牌颁发者的元数据的终结点地址的配置元素。</span><span class="sxs-lookup"><span data-stu-id="6a6d2-133">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6a6d2-134">父元素</span><span class="sxs-lookup"><span data-stu-id="6a6d2-134">Parent Elements</span></span>  
  
|<span data-ttu-id="6a6d2-135">元素</span><span class="sxs-lookup"><span data-stu-id="6a6d2-135">Element</span></span>|<span data-ttu-id="6a6d2-136">描述</span><span class="sxs-lookup"><span data-stu-id="6a6d2-136">Description</span></span>|  
|-------------|-----------------|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|<span data-ttu-id="6a6d2-137">指定用于启动安全对话服务的默认值。</span><span class="sxs-lookup"><span data-stu-id="6a6d2-137">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[\<security>](security-of-custombinding.md)|<span data-ttu-id="6a6d2-138">指定自定义绑定的安全选项。</span><span class="sxs-lookup"><span data-stu-id="6a6d2-138">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6a6d2-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="6a6d2-139">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="6a6d2-140">绑定</span><span class="sxs-lookup"><span data-stu-id="6a6d2-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6a6d2-141">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="6a6d2-141">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="6a6d2-142">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="6a6d2-142">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="6a6d2-143">如何：使用 SecurityBindingElement 创建自定义绑定</span><span class="sxs-lookup"><span data-stu-id="6a6d2-143">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="6a6d2-144">自定义绑定安全性</span><span class="sxs-lookup"><span data-stu-id="6a6d2-144">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
- [<span data-ttu-id="6a6d2-145">服务标识和身份验证</span><span class="sxs-lookup"><span data-stu-id="6a6d2-145">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="6a6d2-146">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="6a6d2-146">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="6a6d2-147">使用自定义绑定的安全功能</span><span class="sxs-lookup"><span data-stu-id="6a6d2-147">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="6a6d2-148">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="6a6d2-148">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)

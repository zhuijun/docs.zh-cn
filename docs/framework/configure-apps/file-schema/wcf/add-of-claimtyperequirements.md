---
title: <add> 的 <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 00699a6fa5d0de7ac554db6ef8d0bbe511a85c0a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149213"
---
# <a name="add-of-claimtyperequirements"></a><span data-ttu-id="247f0-102">\<add> 的 \<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="247f0-102">\<add> of \<claimTypeRequirements></span></span>

<span data-ttu-id="247f0-103">指定希望出现在联合凭据中的必选和可选的声明类型。</span><span class="sxs-lookup"><span data-stu-id="247f0-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="247f0-104">例如，服务规定有关传入凭据的要求，传入凭据必须具有某组声明类型。</span><span class="sxs-lookup"><span data-stu-id="247f0-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="247f0-105">语法</span><span class="sxs-lookup"><span data-stu-id="247f0-105">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="247f0-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="247f0-106">Attributes and Elements</span></span>  

 <span data-ttu-id="247f0-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="247f0-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="247f0-108">特性</span><span class="sxs-lookup"><span data-stu-id="247f0-108">Attributes</span></span>  
  
|<span data-ttu-id="247f0-109">属性</span><span class="sxs-lookup"><span data-stu-id="247f0-109">Attribute</span></span>|<span data-ttu-id="247f0-110">描述</span><span class="sxs-lookup"><span data-stu-id="247f0-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="247f0-111">claimType</span><span class="sxs-lookup"><span data-stu-id="247f0-111">claimType</span></span>|<span data-ttu-id="247f0-112">一个 URI，定义声明类型。</span><span class="sxs-lookup"><span data-stu-id="247f0-112">A URI that defines the type of a claim.</span></span> <span data-ttu-id="247f0-113">例如，若要从网站上购买产品，用户必须提供具有足够信用额度的有效信用卡。</span><span class="sxs-lookup"><span data-stu-id="247f0-113">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="247f0-114">声明类型将为信用卡 URI。</span><span class="sxs-lookup"><span data-stu-id="247f0-114">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="247f0-115">isOptional</span><span class="sxs-lookup"><span data-stu-id="247f0-115">isOptional</span></span>|<span data-ttu-id="247f0-116">一个布尔值，指定声明是否为可选的。</span><span class="sxs-lookup"><span data-stu-id="247f0-116">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="247f0-117">如果声明是必选的，则将此属性设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="247f0-117">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="247f0-118">当服务请求一些并非必要的信息时，可以使用此属性。</span><span class="sxs-lookup"><span data-stu-id="247f0-118">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="247f0-119">例如，如果要求用户输入其名字、姓氏和地址，但决定电话号码是可选的。</span><span class="sxs-lookup"><span data-stu-id="247f0-119">For example, if you require the user to enter their first name, last name, and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="247f0-120">子元素</span><span class="sxs-lookup"><span data-stu-id="247f0-120">Child Elements</span></span>  

 <span data-ttu-id="247f0-121">无。</span><span class="sxs-lookup"><span data-stu-id="247f0-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="247f0-122">父元素</span><span class="sxs-lookup"><span data-stu-id="247f0-122">Parent Elements</span></span>  
  
|<span data-ttu-id="247f0-123">元素</span><span class="sxs-lookup"><span data-stu-id="247f0-123">Element</span></span>|<span data-ttu-id="247f0-124">描述</span><span class="sxs-lookup"><span data-stu-id="247f0-124">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="247f0-125">指定所需声明类型的集合。</span><span class="sxs-lookup"><span data-stu-id="247f0-125">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="247f0-126">在联合方案中，服务规定有关传入凭据的要求。</span><span class="sxs-lookup"><span data-stu-id="247f0-126">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="247f0-127">例如，传入凭据必须具有某组声明类型。</span><span class="sxs-lookup"><span data-stu-id="247f0-127">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="247f0-128">此集合中的每个元素都指定希望出现在联合凭据中的必选和可选的声明类型。</span><span class="sxs-lookup"><span data-stu-id="247f0-128">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="247f0-129">备注</span><span class="sxs-lookup"><span data-stu-id="247f0-129">Remarks</span></span>  

 <span data-ttu-id="247f0-130">在联合方案中，服务规定有关传入凭据的要求。</span><span class="sxs-lookup"><span data-stu-id="247f0-130">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="247f0-131">例如，传入凭据必须具有某组声明类型。</span><span class="sxs-lookup"><span data-stu-id="247f0-131">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="247f0-132">此要求出现在安全策略中。</span><span class="sxs-lookup"><span data-stu-id="247f0-132">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="247f0-133">当客户端请求来自联合服务（例如 CardSpace）的凭据时，它会将需求放置在令牌请求 (RequestSecurityToken) 中，以便联合服务能够相应地颁发符合需求的凭据。</span><span class="sxs-lookup"><span data-stu-id="247f0-133">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="247f0-134">示例</span><span class="sxs-lookup"><span data-stu-id="247f0-134">Example</span></span>  

 <span data-ttu-id="247f0-135">下面的配置将两个声明类型需求添加到安全绑定。</span><span class="sxs-lookup"><span data-stu-id="247f0-135">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="myFederatedBinding">
      <security mode="Message">
        <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">
          <claimTypeRequirements>
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress" />
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"
                 optional="true" />
          </claimTypeRequirements>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>
```  
  
## <a name="see-also"></a><span data-ttu-id="247f0-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="247f0-136">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<claimTypeRequirements>](claimtyperequirements-element.md)
- [<span data-ttu-id="247f0-137">绑定</span><span class="sxs-lookup"><span data-stu-id="247f0-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="247f0-138">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="247f0-138">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="247f0-139">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="247f0-139">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="247f0-140">如何：使用 SecurityBindingElement 创建自定义绑定</span><span class="sxs-lookup"><span data-stu-id="247f0-140">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="247f0-141">自定义绑定安全性</span><span class="sxs-lookup"><span data-stu-id="247f0-141">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)

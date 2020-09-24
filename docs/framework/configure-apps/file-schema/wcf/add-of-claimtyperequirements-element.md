---
title: <add> of <claimTypeRequirements> 元素
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: 920d2b3fa4b51ee56e30863d521214ff66e7fcf2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149239"
---
# <a name="add-of-claimtyperequirements-element"></a><span data-ttu-id="172bd-102">\<add> of \<claimTypeRequirements> 元素</span><span class="sxs-lookup"><span data-stu-id="172bd-102">\<add> of \<claimTypeRequirements> element</span></span>

<span data-ttu-id="172bd-103">指定希望出现在联合凭据中的必选和可选的声明类型。</span><span class="sxs-lookup"><span data-stu-id="172bd-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="172bd-104">例如，服务规定有关传入凭据的要求，传入凭据必须具有某组声明类型。</span><span class="sxs-lookup"><span data-stu-id="172bd-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**
  
## <a name="syntax"></a><span data-ttu-id="172bd-105">语法</span><span class="sxs-lookup"><span data-stu-id="172bd-105">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="172bd-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="172bd-106">Attributes and Elements</span></span>  

 <span data-ttu-id="172bd-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="172bd-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="172bd-108">特性</span><span class="sxs-lookup"><span data-stu-id="172bd-108">Attributes</span></span>  
  
|<span data-ttu-id="172bd-109">属性</span><span class="sxs-lookup"><span data-stu-id="172bd-109">Attribute</span></span>|<span data-ttu-id="172bd-110">描述</span><span class="sxs-lookup"><span data-stu-id="172bd-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="172bd-111">claimType</span><span class="sxs-lookup"><span data-stu-id="172bd-111">claimType</span></span>|<span data-ttu-id="172bd-112">一个 URI，定义声明类型。</span><span class="sxs-lookup"><span data-stu-id="172bd-112">A URI that defines the type of a claim.</span></span> <span data-ttu-id="172bd-113">例如，若要从网站上购买产品，用户必须提供具有足够信用额度的有效信用卡。</span><span class="sxs-lookup"><span data-stu-id="172bd-113">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="172bd-114">声明类型将为信用卡 URI。</span><span class="sxs-lookup"><span data-stu-id="172bd-114">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="172bd-115">isOptional</span><span class="sxs-lookup"><span data-stu-id="172bd-115">isOptional</span></span>|<span data-ttu-id="172bd-116">一个布尔值，指定声明是否为可选的。</span><span class="sxs-lookup"><span data-stu-id="172bd-116">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="172bd-117">如果声明是必选的，则将此属性设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="172bd-117">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="172bd-118">当服务请求一些并非必要的信息时，可以使用此属性。</span><span class="sxs-lookup"><span data-stu-id="172bd-118">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="172bd-119">例如，如果要求用户输入其名字、姓氏和地址，但决定电话号码是可选的。</span><span class="sxs-lookup"><span data-stu-id="172bd-119">For example, if you require the user to enter their first name, last name, and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="172bd-120">子元素</span><span class="sxs-lookup"><span data-stu-id="172bd-120">Child Elements</span></span>  

 <span data-ttu-id="172bd-121">无。</span><span class="sxs-lookup"><span data-stu-id="172bd-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="172bd-122">父元素</span><span class="sxs-lookup"><span data-stu-id="172bd-122">Parent Elements</span></span>  
  
|<span data-ttu-id="172bd-123">元素</span><span class="sxs-lookup"><span data-stu-id="172bd-123">Element</span></span>|<span data-ttu-id="172bd-124">描述</span><span class="sxs-lookup"><span data-stu-id="172bd-124">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="172bd-125">指定所需声明类型的集合。</span><span class="sxs-lookup"><span data-stu-id="172bd-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="172bd-126">每个元素的类型都为 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="172bd-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="172bd-127">在联合方案中，服务规定有关传入凭据的要求。</span><span class="sxs-lookup"><span data-stu-id="172bd-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="172bd-128">例如，传入凭据必须具有某组声明类型。</span><span class="sxs-lookup"><span data-stu-id="172bd-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="172bd-129">此集合中的每个元素都指定希望出现在联合凭据中的必选和可选的声明类型。</span><span class="sxs-lookup"><span data-stu-id="172bd-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="172bd-130">备注</span><span class="sxs-lookup"><span data-stu-id="172bd-130">Remarks</span></span>  

 <span data-ttu-id="172bd-131">在联合方案中，服务规定有关传入凭据的要求。</span><span class="sxs-lookup"><span data-stu-id="172bd-131">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="172bd-132">例如，传入凭据必须具有某组声明类型。</span><span class="sxs-lookup"><span data-stu-id="172bd-132">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="172bd-133">此要求出现在安全策略中。</span><span class="sxs-lookup"><span data-stu-id="172bd-133">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="172bd-134">当客户端请求来自联合服务（例如 CardSpace）的凭据时，它会将需求放置在令牌请求 (RequestSecurityToken) 中，以便联合服务能够相应地颁发符合需求的凭据。</span><span class="sxs-lookup"><span data-stu-id="172bd-134">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="172bd-135">示例</span><span class="sxs-lookup"><span data-stu-id="172bd-135">Example</span></span>  

 <span data-ttu-id="172bd-136">下面的配置将两个声明类型需求添加到安全绑定。</span><span class="sxs-lookup"><span data-stu-id="172bd-136">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="172bd-137">请参阅</span><span class="sxs-lookup"><span data-stu-id="172bd-137">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>

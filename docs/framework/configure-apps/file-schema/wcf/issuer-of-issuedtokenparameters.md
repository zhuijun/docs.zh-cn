---
title: <issuer> 的 <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: bdd5ad45984fae7b39defe82c4af75845dfda1b6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397935"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="7edd1-102">\<issuer> 的 \<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="7edd1-102">\<issuer> of \<issuedTokenParameters></span></span>
<span data-ttu-id="7edd1-103">指定颁发安全令牌的安全令牌服务 (STS)。</span><span class="sxs-lookup"><span data-stu-id="7edd1-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**  
  
## <a name="syntax"></a><span data-ttu-id="7edd1-104">语法</span><span class="sxs-lookup"><span data-stu-id="7edd1-104">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7edd1-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="7edd1-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7edd1-106">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="7edd1-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7edd1-107">特性</span><span class="sxs-lookup"><span data-stu-id="7edd1-107">Attributes</span></span>  
  
|<span data-ttu-id="7edd1-108">属性</span><span class="sxs-lookup"><span data-stu-id="7edd1-108">Attribute</span></span>|<span data-ttu-id="7edd1-109">说明</span><span class="sxs-lookup"><span data-stu-id="7edd1-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7edd1-110">address</span><span class="sxs-lookup"><span data-stu-id="7edd1-110">address</span></span>|<span data-ttu-id="7edd1-111">必需的字符串。</span><span class="sxs-lookup"><span data-stu-id="7edd1-111">Required string.</span></span> <span data-ttu-id="7edd1-112">STS 的 URL。</span><span class="sxs-lookup"><span data-stu-id="7edd1-112">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7edd1-113">子元素</span><span class="sxs-lookup"><span data-stu-id="7edd1-113">Child Elements</span></span>  
  
|<span data-ttu-id="7edd1-114">元素</span><span class="sxs-lookup"><span data-stu-id="7edd1-114">Element</span></span>|<span data-ttu-id="7edd1-115">描述</span><span class="sxs-lookup"><span data-stu-id="7edd1-115">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="7edd1-116">生成器可以创建的终结点的地址标头的集合。</span><span class="sxs-lookup"><span data-stu-id="7edd1-116">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="7edd1-117">在使用颁发的令牌时，指定能够使客户端对服务器进行身份验证的设置。</span><span class="sxs-lookup"><span data-stu-id="7edd1-117">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7edd1-118">父元素</span><span class="sxs-lookup"><span data-stu-id="7edd1-118">Parent Elements</span></span>  
  
|<span data-ttu-id="7edd1-119">元素</span><span class="sxs-lookup"><span data-stu-id="7edd1-119">Element</span></span>|<span data-ttu-id="7edd1-120">描述</span><span class="sxs-lookup"><span data-stu-id="7edd1-120">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="7edd1-121">指定当前颁发的令牌。</span><span class="sxs-lookup"><span data-stu-id="7edd1-121">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7edd1-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7edd1-122">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="7edd1-123">服务标识和身份验证</span><span class="sxs-lookup"><span data-stu-id="7edd1-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="7edd1-124">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="7edd1-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="7edd1-125">使用自定义绑定的安全功能</span><span class="sxs-lookup"><span data-stu-id="7edd1-125">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="7edd1-126">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="7edd1-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="7edd1-127">绑定</span><span class="sxs-lookup"><span data-stu-id="7edd1-127">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7edd1-128">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="7edd1-128">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="7edd1-129">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="7edd1-129">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="7edd1-130">如何：使用 SecurityBindingElement 创建自定义绑定</span><span class="sxs-lookup"><span data-stu-id="7edd1-130">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="7edd1-131">自定义绑定安全性</span><span class="sxs-lookup"><span data-stu-id="7edd1-131">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)

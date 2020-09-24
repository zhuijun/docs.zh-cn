---
title: <issuer> 的 <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: bfe8163d2d6baba1d6e8053f7f6579673d8b4b21
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157273"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="7df2b-102">\<issuer> 的 \<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="7df2b-102">\<issuer> of \<issuedTokenParameters></span></span>

<span data-ttu-id="7df2b-103">指定颁发安全令牌的安全令牌服务 (STS)。</span><span class="sxs-lookup"><span data-stu-id="7df2b-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**  
  
## <a name="syntax"></a><span data-ttu-id="7df2b-104">语法</span><span class="sxs-lookup"><span data-stu-id="7df2b-104">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7df2b-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="7df2b-105">Attributes and Elements</span></span>  

 <span data-ttu-id="7df2b-106">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="7df2b-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7df2b-107">特性</span><span class="sxs-lookup"><span data-stu-id="7df2b-107">Attributes</span></span>  
  
|<span data-ttu-id="7df2b-108">属性</span><span class="sxs-lookup"><span data-stu-id="7df2b-108">Attribute</span></span>|<span data-ttu-id="7df2b-109">描述</span><span class="sxs-lookup"><span data-stu-id="7df2b-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7df2b-110">address</span><span class="sxs-lookup"><span data-stu-id="7df2b-110">address</span></span>|<span data-ttu-id="7df2b-111">必选字符串。</span><span class="sxs-lookup"><span data-stu-id="7df2b-111">Required string.</span></span> <span data-ttu-id="7df2b-112">STS 的 URL。</span><span class="sxs-lookup"><span data-stu-id="7df2b-112">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7df2b-113">子元素</span><span class="sxs-lookup"><span data-stu-id="7df2b-113">Child Elements</span></span>  
  
|<span data-ttu-id="7df2b-114">元素</span><span class="sxs-lookup"><span data-stu-id="7df2b-114">Element</span></span>|<span data-ttu-id="7df2b-115">描述</span><span class="sxs-lookup"><span data-stu-id="7df2b-115">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="7df2b-116">生成器可以创建的终结点的地址标头的集合。</span><span class="sxs-lookup"><span data-stu-id="7df2b-116">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="7df2b-117">在使用颁发的令牌时，指定能够使客户端对服务器进行身份验证的设置。</span><span class="sxs-lookup"><span data-stu-id="7df2b-117">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7df2b-118">父元素</span><span class="sxs-lookup"><span data-stu-id="7df2b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="7df2b-119">元素</span><span class="sxs-lookup"><span data-stu-id="7df2b-119">Element</span></span>|<span data-ttu-id="7df2b-120">描述</span><span class="sxs-lookup"><span data-stu-id="7df2b-120">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="7df2b-121">指定当前颁发的令牌。</span><span class="sxs-lookup"><span data-stu-id="7df2b-121">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7df2b-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="7df2b-122">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="7df2b-123">服务标识和身份验证</span><span class="sxs-lookup"><span data-stu-id="7df2b-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="7df2b-124">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="7df2b-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="7df2b-125">使用自定义绑定的安全功能</span><span class="sxs-lookup"><span data-stu-id="7df2b-125">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="7df2b-126">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="7df2b-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="7df2b-127">绑定</span><span class="sxs-lookup"><span data-stu-id="7df2b-127">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7df2b-128">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="7df2b-128">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="7df2b-129">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="7df2b-129">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="7df2b-130">如何：使用 SecurityBindingElement 创建自定义绑定</span><span class="sxs-lookup"><span data-stu-id="7df2b-130">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="7df2b-131">自定义绑定安全性</span><span class="sxs-lookup"><span data-stu-id="7df2b-131">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)

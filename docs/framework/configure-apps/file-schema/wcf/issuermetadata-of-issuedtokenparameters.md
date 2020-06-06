---
title: <issuerMetadata> 的 <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: fcdd66ecd162dff5be86a1d4ab1b196f50dbd445
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400346"
---
# <a name="issuermetadata-of-issuedtokenparameters"></a><span data-ttu-id="0b57f-102">\<issuerMetadata> 的 \<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="0b57f-102">\<issuerMetadata> of \<issuedTokenParameters></span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**  
  
## <a name="syntax"></a><span data-ttu-id="0b57f-103">语法</span><span class="sxs-lookup"><span data-stu-id="0b57f-103">Syntax</span></span>  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0b57f-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="0b57f-104">Attributes and Elements</span></span>  
 <span data-ttu-id="0b57f-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0b57f-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0b57f-106">特性</span><span class="sxs-lookup"><span data-stu-id="0b57f-106">Attributes</span></span>  
  
|<span data-ttu-id="0b57f-107">属性</span><span class="sxs-lookup"><span data-stu-id="0b57f-107">Attribute</span></span>|<span data-ttu-id="0b57f-108">说明</span><span class="sxs-lookup"><span data-stu-id="0b57f-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0b57f-109">address</span><span class="sxs-lookup"><span data-stu-id="0b57f-109">address</span></span>|<span data-ttu-id="0b57f-110">必需。</span><span class="sxs-lookup"><span data-stu-id="0b57f-110">Required.</span></span> <span data-ttu-id="0b57f-111">一个指定终结点地址的字符串。</span><span class="sxs-lookup"><span data-stu-id="0b57f-111">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="0b57f-112">该地址必须为绝对 URI。</span><span class="sxs-lookup"><span data-stu-id="0b57f-112">The address must be an absolute URI.</span></span> <span data-ttu-id="0b57f-113">默认值为空字符串。</span><span class="sxs-lookup"><span data-stu-id="0b57f-113">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0b57f-114">子元素</span><span class="sxs-lookup"><span data-stu-id="0b57f-114">Child Elements</span></span>  
  
|<span data-ttu-id="0b57f-115">元素</span><span class="sxs-lookup"><span data-stu-id="0b57f-115">Element</span></span>|<span data-ttu-id="0b57f-116">描述</span><span class="sxs-lookup"><span data-stu-id="0b57f-116">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="0b57f-117">一个地址标头集合。</span><span class="sxs-lookup"><span data-stu-id="0b57f-117">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="0b57f-118">一个标识，与某个终结点交换消息的其他终结点可以使用该标识对该终结点进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="0b57f-118">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0b57f-119">父元素</span><span class="sxs-lookup"><span data-stu-id="0b57f-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0b57f-120">元素</span><span class="sxs-lookup"><span data-stu-id="0b57f-120">Element</span></span>|<span data-ttu-id="0b57f-121">描述</span><span class="sxs-lookup"><span data-stu-id="0b57f-121">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="0b57f-122">指定在联合安全方案中颁发的安全令牌的参数。</span><span class="sxs-lookup"><span data-stu-id="0b57f-122">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0b57f-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0b57f-123">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="0b57f-124">服务标识和身份验证</span><span class="sxs-lookup"><span data-stu-id="0b57f-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="0b57f-125">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="0b57f-125">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="0b57f-126">使用自定义绑定的安全功能</span><span class="sxs-lookup"><span data-stu-id="0b57f-126">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="0b57f-127">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="0b57f-127">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="0b57f-128">绑定</span><span class="sxs-lookup"><span data-stu-id="0b57f-128">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0b57f-129">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="0b57f-129">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="0b57f-130">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="0b57f-130">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="0b57f-131">如何：使用 SecurityBindingElement 创建自定义绑定</span><span class="sxs-lookup"><span data-stu-id="0b57f-131">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="0b57f-132">自定义绑定安全性</span><span class="sxs-lookup"><span data-stu-id="0b57f-132">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)

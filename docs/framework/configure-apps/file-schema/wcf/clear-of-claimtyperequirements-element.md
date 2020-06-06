---
title: <clear>of <claimTypeRequirements> 元素
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: 01f101f7d0dd5da6a834a4ffb2c7e09df0e23cd8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400527"
---
# <a name="clear-of-claimtyperequirements-element"></a><span data-ttu-id="9a067-102">\<clear>of \<claimTypeRequirements> 元素</span><span class="sxs-lookup"><span data-stu-id="9a067-102">\<clear> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="9a067-103">指定所有声明类型都将从联合凭据中移除。</span><span class="sxs-lookup"><span data-stu-id="9a067-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="9a067-104">这样可以确保集合最初为空。</span><span class="sxs-lookup"><span data-stu-id="9a067-104">This ensures that the collection starts empty.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a><span data-ttu-id="9a067-105">语法</span><span class="sxs-lookup"><span data-stu-id="9a067-105">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9a067-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="9a067-106">Attributes and Elements</span></span>  
 <span data-ttu-id="9a067-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9a067-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9a067-108">特性</span><span class="sxs-lookup"><span data-stu-id="9a067-108">Attributes</span></span>  
 <span data-ttu-id="9a067-109">无。</span><span class="sxs-lookup"><span data-stu-id="9a067-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9a067-110">子元素</span><span class="sxs-lookup"><span data-stu-id="9a067-110">Child Elements</span></span>  
 <span data-ttu-id="9a067-111">无。</span><span class="sxs-lookup"><span data-stu-id="9a067-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9a067-112">父元素</span><span class="sxs-lookup"><span data-stu-id="9a067-112">Parent Elements</span></span>  
  
|<span data-ttu-id="9a067-113">元素</span><span class="sxs-lookup"><span data-stu-id="9a067-113">Element</span></span>|<span data-ttu-id="9a067-114">说明</span><span class="sxs-lookup"><span data-stu-id="9a067-114">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="9a067-115">指定所需声明类型的集合。</span><span class="sxs-lookup"><span data-stu-id="9a067-115">Specifies a collection of required claim types.</span></span> <span data-ttu-id="9a067-116">每个元素的类型都为 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="9a067-116">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="9a067-117">在联合方案中，服务规定有关传入凭据的要求。</span><span class="sxs-lookup"><span data-stu-id="9a067-117">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="9a067-118">例如，传入凭据必须具有某组声明类型。</span><span class="sxs-lookup"><span data-stu-id="9a067-118">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="9a067-119">此集合中的每个元素都指定希望出现在联合凭据中的必选和可选的声明类型。</span><span class="sxs-lookup"><span data-stu-id="9a067-119">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9a067-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9a067-120">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>

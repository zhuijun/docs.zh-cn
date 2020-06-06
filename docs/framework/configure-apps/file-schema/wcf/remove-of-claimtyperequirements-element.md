---
title: <remove>of <claimTypeRequirements> 元素
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 84f4208d3f4581cf7e8c4455bf3f5d78f7e13b9f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399989"
---
# <a name="remove-of-claimtyperequirements-element"></a><span data-ttu-id="4d34c-102">\<remove>of \<claimTypeRequirements> 元素</span><span class="sxs-lookup"><span data-stu-id="4d34c-102">\<remove> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="4d34c-103">指定要从联合凭据中移除的声明的类型。</span><span class="sxs-lookup"><span data-stu-id="4d34c-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="4d34c-104">语法</span><span class="sxs-lookup"><span data-stu-id="4d34c-104">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d34c-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="4d34c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="4d34c-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4d34c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d34c-107">特性</span><span class="sxs-lookup"><span data-stu-id="4d34c-107">Attributes</span></span>  
  
|<span data-ttu-id="4d34c-108">属性</span><span class="sxs-lookup"><span data-stu-id="4d34c-108">Attribute</span></span>|<span data-ttu-id="4d34c-109">说明</span><span class="sxs-lookup"><span data-stu-id="4d34c-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4d34c-110">claimType</span><span class="sxs-lookup"><span data-stu-id="4d34c-110">claimType</span></span>|<span data-ttu-id="4d34c-111">一个 URI，定义要移除的声明的类型。</span><span class="sxs-lookup"><span data-stu-id="4d34c-111">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4d34c-112">子元素</span><span class="sxs-lookup"><span data-stu-id="4d34c-112">Child Elements</span></span>  
 <span data-ttu-id="4d34c-113">无。</span><span class="sxs-lookup"><span data-stu-id="4d34c-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4d34c-114">父元素</span><span class="sxs-lookup"><span data-stu-id="4d34c-114">Parent Elements</span></span>  
  
|<span data-ttu-id="4d34c-115">元素</span><span class="sxs-lookup"><span data-stu-id="4d34c-115">Element</span></span>|<span data-ttu-id="4d34c-116">描述</span><span class="sxs-lookup"><span data-stu-id="4d34c-116">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="4d34c-117">指定所需声明类型的集合。</span><span class="sxs-lookup"><span data-stu-id="4d34c-117">Specifies a collection of required claim types.</span></span> <span data-ttu-id="4d34c-118">每个元素的类型都为 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="4d34c-118">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="4d34c-119">在联合方案中，服务规定有关传入凭据的要求。</span><span class="sxs-lookup"><span data-stu-id="4d34c-119">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="4d34c-120">例如，传入凭据必须具有某组声明类型。</span><span class="sxs-lookup"><span data-stu-id="4d34c-120">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="4d34c-121">此集合中的每个元素都指定希望出现在联合凭据中的必选和可选的声明类型。</span><span class="sxs-lookup"><span data-stu-id="4d34c-121">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4d34c-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4d34c-122">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>

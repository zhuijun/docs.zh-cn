---
title: <add> 的 <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: e2597bc51e788c919bfe3ce3422ae2911cc6b33b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400699"
---
# <a name="add-of-authorizationpolicies"></a><span data-ttu-id="9eea9-102">\<add> 的 \<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="9eea9-102">\<add> of \<authorizationPolicies></span></span>
<span data-ttu-id="9eea9-103">指定声明转换的授权策略。</span><span class="sxs-lookup"><span data-stu-id="9eea9-103">Specifies an authorization policy for claim transformation.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceAuthorization>**](serviceauthorization-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<authorizationPolicies>**](authorizationpolicies.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="9eea9-104">语法</span><span class="sxs-lookup"><span data-stu-id="9eea9-104">Syntax</span></span>  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a><span data-ttu-id="9eea9-105">类型</span><span class="sxs-lookup"><span data-stu-id="9eea9-105">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9eea9-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="9eea9-106">Attributes and Elements</span></span>  
 <span data-ttu-id="9eea9-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9eea9-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9eea9-108">特性</span><span class="sxs-lookup"><span data-stu-id="9eea9-108">Attributes</span></span>  
  
|<span data-ttu-id="9eea9-109">属性</span><span class="sxs-lookup"><span data-stu-id="9eea9-109">Attribute</span></span>|<span data-ttu-id="9eea9-110">说明</span><span class="sxs-lookup"><span data-stu-id="9eea9-110">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="9eea9-111">必需的字符串属性。</span><span class="sxs-lookup"><span data-stu-id="9eea9-111">A required String attribute.</span></span><br /><br /> <span data-ttu-id="9eea9-112">Windows Communication Foundation （WCF）访问控制模型支持将一组授权策略作为类型进行设置。</span><span class="sxs-lookup"><span data-stu-id="9eea9-112">The Windows Communication Foundation (WCF) access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="9eea9-113">此属性指定一个授权策略，使得可以将一组输入声明转换为另一组声明。</span><span class="sxs-lookup"><span data-stu-id="9eea9-113">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="9eea9-114">可以根据该授权策略来授予或拒绝访问控制。</span><span class="sxs-lookup"><span data-stu-id="9eea9-114">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9eea9-115">子元素</span><span class="sxs-lookup"><span data-stu-id="9eea9-115">Child Elements</span></span>  
 <span data-ttu-id="9eea9-116">无。</span><span class="sxs-lookup"><span data-stu-id="9eea9-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9eea9-117">父元素</span><span class="sxs-lookup"><span data-stu-id="9eea9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="9eea9-118">元素</span><span class="sxs-lookup"><span data-stu-id="9eea9-118">Element</span></span>|<span data-ttu-id="9eea9-119">描述</span><span class="sxs-lookup"><span data-stu-id="9eea9-119">Description</span></span>|  
|-------------|-----------------|  
|[\<authorizationPolicies>](authorizationpolicies.md)|<span data-ttu-id="9eea9-120">指定一个授权策略类型集合。</span><span class="sxs-lookup"><span data-stu-id="9eea9-120">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9eea9-121">注解</span><span class="sxs-lookup"><span data-stu-id="9eea9-121">Remarks</span></span>  
 <span data-ttu-id="9eea9-122">每个授权类型都包含一个所需的 `policyType` 属性，此属性是一个字符串。</span><span class="sxs-lookup"><span data-stu-id="9eea9-122">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="9eea9-123">该属性指定一个授权策略，可以将一组输入声明转换为另一组声明。</span><span class="sxs-lookup"><span data-stu-id="9eea9-123">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="9eea9-124">可以根据该授权策略来授予或拒绝访问控制。</span><span class="sxs-lookup"><span data-stu-id="9eea9-124">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="9eea9-125">有关授权策略工作方式的详细信息，请参阅 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> 和[授权策略](../../../wcf/samples/authorization-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="9eea9-125">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eea9-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9eea9-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="9eea9-127">授予对服务操作的访问权限</span><span class="sxs-lookup"><span data-stu-id="9eea9-127">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="9eea9-128">如何：为服务创建自定义授权管理器</span><span class="sxs-lookup"><span data-stu-id="9eea9-128">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [\<add>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="9eea9-129">授权策略</span><span class="sxs-lookup"><span data-stu-id="9eea9-129">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)

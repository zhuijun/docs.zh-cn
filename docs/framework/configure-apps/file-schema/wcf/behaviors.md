---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: 914fa04c9aff0c287913104cd9bedc570c473330
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201481"
---
# \<behaviors>

<span data-ttu-id="32d05-101">此元素定义名为 `endpointBehaviors` 和 `serviceBehaviors` 的两个子集合。</span><span class="sxs-lookup"><span data-stu-id="32d05-101">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="32d05-102">每个集合分别定义终结点和服务所使用的行为元素。</span><span class="sxs-lookup"><span data-stu-id="32d05-102">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="32d05-103">每个行为元素由其唯一的 `name` 属性标识。</span><span class="sxs-lookup"><span data-stu-id="32d05-103">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="32d05-104">从 .NET Framework 4 开始，绑定和行为不需要具有名称。</span><span class="sxs-lookup"><span data-stu-id="32d05-104">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="32d05-105">有关默认配置和无值绑定和行为的详细信息，请参阅[WCF 服务的](../../../wcf/samples/simplified-configuration-for-wcf-services.md)[简化配置](../../../wcf/simplified-configuration.md)和简化配置。</span><span class="sxs-lookup"><span data-stu-id="32d05-105">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**  
  
## <a name="syntax"></a><span data-ttu-id="32d05-106">语法</span><span class="sxs-lookup"><span data-stu-id="32d05-106">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32d05-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="32d05-107">Attributes and Elements</span></span>  

 <span data-ttu-id="32d05-108">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="32d05-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32d05-109">特性</span><span class="sxs-lookup"><span data-stu-id="32d05-109">Attributes</span></span>  

 <span data-ttu-id="32d05-110">无</span><span class="sxs-lookup"><span data-stu-id="32d05-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="32d05-111">子元素</span><span class="sxs-lookup"><span data-stu-id="32d05-111">Child Elements</span></span>  
  
|<span data-ttu-id="32d05-112">元素</span><span class="sxs-lookup"><span data-stu-id="32d05-112">Element</span></span>|<span data-ttu-id="32d05-113">描述</span><span class="sxs-lookup"><span data-stu-id="32d05-113">Description</span></span>|  
|-------------|-----------------|  
|[\<endpointBehaviors>](endpointbehaviors.md)|<span data-ttu-id="32d05-114">此配置节描述为特定终结点定义的所有行为。</span><span class="sxs-lookup"><span data-stu-id="32d05-114">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[\<serviceBehaviors>](servicebehaviors.md)|<span data-ttu-id="32d05-115">此配置节描述为特定服务定义的所有行为。</span><span class="sxs-lookup"><span data-stu-id="32d05-115">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="32d05-116">父元素</span><span class="sxs-lookup"><span data-stu-id="32d05-116">Parent Elements</span></span>  
  
|<span data-ttu-id="32d05-117">元素</span><span class="sxs-lookup"><span data-stu-id="32d05-117">Element</span></span>|<span data-ttu-id="32d05-118">描述</span><span class="sxs-lookup"><span data-stu-id="32d05-118">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="32d05-119">所有 Windows Communication Foundation (WCF) 配置元素的根元素。</span><span class="sxs-lookup"><span data-stu-id="32d05-119">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32d05-120">备注</span><span class="sxs-lookup"><span data-stu-id="32d05-120">Remarks</span></span>  

 <span data-ttu-id="32d05-121">使用 `<remove>` 元素可以从集合中移除特定行为。</span><span class="sxs-lookup"><span data-stu-id="32d05-121">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="32d05-122">为此，您只需在 `name` 元素的 `<remove>` 特性中提供要移除的行为的名称。</span><span class="sxs-lookup"><span data-stu-id="32d05-122">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="32d05-123">还可以使用 `<clear>` 元素清除集合中的所有内容，来确保行为集合最初为空。</span><span class="sxs-lookup"><span data-stu-id="32d05-123">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32d05-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="32d05-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="32d05-125">使用行为配置和扩展运行时</span><span class="sxs-lookup"><span data-stu-id="32d05-125">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [<span data-ttu-id="32d05-126">配置客户端行为</span><span class="sxs-lookup"><span data-stu-id="32d05-126">Configuring Client Behaviors</span></span>](../../../wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="32d05-127">指定客户端运行时行为</span><span class="sxs-lookup"><span data-stu-id="32d05-127">Specifying Client Run-Time Behavior</span></span>](../../../wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="32d05-128">指定服务运行时行为</span><span class="sxs-lookup"><span data-stu-id="32d05-128">Specifying Service Run-Time Behavior</span></span>](../../../wcf/specifying-service-run-time-behavior.md)
- [<span data-ttu-id="32d05-129">安全行为</span><span class="sxs-lookup"><span data-stu-id="32d05-129">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)

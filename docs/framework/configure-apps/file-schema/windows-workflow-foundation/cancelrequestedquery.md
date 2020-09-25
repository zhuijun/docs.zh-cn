---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: a50e9965a595fce64c383313091334e883dcfbfa
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189482"
---
# \<cancelRequestedQuery>

<span data-ttu-id="df259-101">表示一个查询，该查询用于跟踪父活动取消子活动的请求。</span><span class="sxs-lookup"><span data-stu-id="df259-101">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="df259-102">跟踪参与者需要用此查询来订阅取消请求记录对象。</span><span class="sxs-lookup"><span data-stu-id="df259-102">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="df259-103">有关跟踪配置文件查询的详细信息，请参阅 [跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="df259-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="df259-104">语法</span><span class="sxs-lookup"><span data-stu-id="df259-104">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <cancelRequestQueries>
        <cancelRequestQuery activityName="String"
                            childActivityName="String"/>
      </cancelRequestQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df259-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="df259-105">Attributes and Elements</span></span>  

 <span data-ttu-id="df259-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="df259-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df259-107">特性</span><span class="sxs-lookup"><span data-stu-id="df259-107">Attributes</span></span>  
  
|<span data-ttu-id="df259-108">属性</span><span class="sxs-lookup"><span data-stu-id="df259-108">Attribute</span></span>|<span data-ttu-id="df259-109">描述</span><span class="sxs-lookup"><span data-stu-id="df259-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="df259-110">activityName</span><span class="sxs-lookup"><span data-stu-id="df259-110">activityName</span></span>|<span data-ttu-id="df259-111">一个字符串，指定正在请求取消的活动的名称。</span><span class="sxs-lookup"><span data-stu-id="df259-111">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="df259-112">childActivityName</span><span class="sxs-lookup"><span data-stu-id="df259-112">childActivityName</span></span>|<span data-ttu-id="df259-113">一个字符串，指定已请求将其取消的子活动的名称。</span><span class="sxs-lookup"><span data-stu-id="df259-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="df259-114">子元素</span><span class="sxs-lookup"><span data-stu-id="df259-114">Child Elements</span></span>  

 <span data-ttu-id="df259-115">无。</span><span class="sxs-lookup"><span data-stu-id="df259-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="df259-116">父元素</span><span class="sxs-lookup"><span data-stu-id="df259-116">Parent Elements</span></span>  
  
|<span data-ttu-id="df259-117">元素</span><span class="sxs-lookup"><span data-stu-id="df259-117">Element</span></span>|<span data-ttu-id="df259-118">描述</span><span class="sxs-lookup"><span data-stu-id="df259-118">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery.md)|<span data-ttu-id="df259-119">表示一个配置元素列表，这些元素用于跟踪父活动取消子活动的请求。</span><span class="sxs-lookup"><span data-stu-id="df259-119">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="df259-120">跟踪参与者需要用此查询来订阅取消请求记录对象。</span><span class="sxs-lookup"><span data-stu-id="df259-120">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="df259-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="df259-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="df259-122">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="df259-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="df259-123">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="df259-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)

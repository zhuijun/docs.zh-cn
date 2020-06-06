---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: 3e6840ce647625c36356cccd4651f17de32777e2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152282"
---
# \<cancelRequestedQuery>
<span data-ttu-id="a1528-101">表示一个查询，该查询用于跟踪父活动取消子活动的请求。</span><span class="sxs-lookup"><span data-stu-id="a1528-101">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="a1528-102">跟踪参与者需要用此查询来订阅取消请求记录对象。</span><span class="sxs-lookup"><span data-stu-id="a1528-102">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="a1528-103">有关跟踪配置文件查询的详细信息，请参阅[跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="a1528-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="a1528-104">语法</span><span class="sxs-lookup"><span data-stu-id="a1528-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a1528-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="a1528-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a1528-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a1528-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a1528-107">特性</span><span class="sxs-lookup"><span data-stu-id="a1528-107">Attributes</span></span>  
  
|<span data-ttu-id="a1528-108">属性</span><span class="sxs-lookup"><span data-stu-id="a1528-108">Attribute</span></span>|<span data-ttu-id="a1528-109">说明</span><span class="sxs-lookup"><span data-stu-id="a1528-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a1528-110">activityName</span><span class="sxs-lookup"><span data-stu-id="a1528-110">activityName</span></span>|<span data-ttu-id="a1528-111">一个字符串，指定正在请求取消的活动的名称。</span><span class="sxs-lookup"><span data-stu-id="a1528-111">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="a1528-112">childActivityName</span><span class="sxs-lookup"><span data-stu-id="a1528-112">childActivityName</span></span>|<span data-ttu-id="a1528-113">一个字符串，指定已请求将其取消的子活动的名称。</span><span class="sxs-lookup"><span data-stu-id="a1528-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a1528-114">子元素</span><span class="sxs-lookup"><span data-stu-id="a1528-114">Child Elements</span></span>  
 <span data-ttu-id="a1528-115">无。</span><span class="sxs-lookup"><span data-stu-id="a1528-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a1528-116">父元素</span><span class="sxs-lookup"><span data-stu-id="a1528-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a1528-117">元素</span><span class="sxs-lookup"><span data-stu-id="a1528-117">Element</span></span>|<span data-ttu-id="a1528-118">描述</span><span class="sxs-lookup"><span data-stu-id="a1528-118">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery.md)|<span data-ttu-id="a1528-119">表示一个配置元素列表，这些元素用于跟踪父活动取消子活动的请求。</span><span class="sxs-lookup"><span data-stu-id="a1528-119">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="a1528-120">跟踪参与者需要用此查询来订阅取消请求记录对象。</span><span class="sxs-lookup"><span data-stu-id="a1528-120">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a1528-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a1528-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a1528-122">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="a1528-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a1528-123">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="a1528-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)

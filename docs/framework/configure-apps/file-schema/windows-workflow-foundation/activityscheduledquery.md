---
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: 09cbc43ae4db82dc80e6985131f8d6cc0c24b2ac
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152406"
---
# \<activityScheduledQuery>
<span data-ttu-id="67559-101">表示一个查询集合，这些查询用于跟踪安排给父活动来执行的活动。</span><span class="sxs-lookup"><span data-stu-id="67559-101">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="67559-102">跟踪参与者需要用此查询来订阅活动安排记录。</span><span class="sxs-lookup"><span data-stu-id="67559-102">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="67559-103">有关跟踪配置文件查询的详细信息，请参阅[跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="67559-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="67559-104">语法</span><span class="sxs-lookup"><span data-stu-id="67559-104">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String"
                                childActivityName="String"/>
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67559-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="67559-105">Attributes and Elements</span></span>  
 <span data-ttu-id="67559-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="67559-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67559-107">特性</span><span class="sxs-lookup"><span data-stu-id="67559-107">Attributes</span></span>  
  
|<span data-ttu-id="67559-108">属性</span><span class="sxs-lookup"><span data-stu-id="67559-108">Attribute</span></span>|<span data-ttu-id="67559-109">说明</span><span class="sxs-lookup"><span data-stu-id="67559-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="67559-110">activityName</span><span class="sxs-lookup"><span data-stu-id="67559-110">activityName</span></span>|<span data-ttu-id="67559-111">一个字符串，指定正在请求取消的活动的名称。</span><span class="sxs-lookup"><span data-stu-id="67559-111">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="67559-112">childActivityName</span><span class="sxs-lookup"><span data-stu-id="67559-112">childActivityName</span></span>|<span data-ttu-id="67559-113">一个字符串，指定已请求将其取消的子活动的名称。</span><span class="sxs-lookup"><span data-stu-id="67559-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="67559-114">子元素</span><span class="sxs-lookup"><span data-stu-id="67559-114">Child Elements</span></span>  
 <span data-ttu-id="67559-115">无。</span><span class="sxs-lookup"><span data-stu-id="67559-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="67559-116">父元素</span><span class="sxs-lookup"><span data-stu-id="67559-116">Parent Elements</span></span>  
  
|<span data-ttu-id="67559-117">元素</span><span class="sxs-lookup"><span data-stu-id="67559-117">Element</span></span>|<span data-ttu-id="67559-118">描述</span><span class="sxs-lookup"><span data-stu-id="67559-118">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery.md)|<span data-ttu-id="67559-119">一个查询，用于跟踪安排给父活动来执行的活动。</span><span class="sxs-lookup"><span data-stu-id="67559-119">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="67559-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="67559-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="67559-121">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="67559-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="67559-122">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="67559-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)

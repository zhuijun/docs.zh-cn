---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 936267f7d61dfd09af45ddb96b4406c92c30b3b2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148771"
---
# \<activityScheduledQueries>

<span data-ttu-id="cec49-101">表示一个查询集合，这些查询用于跟踪安排给父活动来执行的活动。</span><span class="sxs-lookup"><span data-stu-id="cec49-101">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="cec49-102">跟踪参与者需要用此查询来订阅活动安排记录。</span><span class="sxs-lookup"><span data-stu-id="cec49-102">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="cec49-103">有关跟踪配置文件查询的详细信息，请参阅 [跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="cec49-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="cec49-104">语法</span><span class="sxs-lookup"><span data-stu-id="cec49-104">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String"
                                childActivityName="String" />
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cec49-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="cec49-105">Attributes and Elements</span></span>  

 <span data-ttu-id="cec49-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cec49-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cec49-107">特性</span><span class="sxs-lookup"><span data-stu-id="cec49-107">Attributes</span></span>  

 <span data-ttu-id="cec49-108">无。</span><span class="sxs-lookup"><span data-stu-id="cec49-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cec49-109">子元素</span><span class="sxs-lookup"><span data-stu-id="cec49-109">Child Elements</span></span>  
  
|<span data-ttu-id="cec49-110">元素</span><span class="sxs-lookup"><span data-stu-id="cec49-110">Element</span></span>|<span data-ttu-id="cec49-111">描述</span><span class="sxs-lookup"><span data-stu-id="cec49-111">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery.md)|<span data-ttu-id="cec49-112">一个查询，用于跟踪安排给父活动来执行的活动。</span><span class="sxs-lookup"><span data-stu-id="cec49-112">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cec49-113">父元素</span><span class="sxs-lookup"><span data-stu-id="cec49-113">Parent Elements</span></span>  
  
|<span data-ttu-id="cec49-114">元素</span><span class="sxs-lookup"><span data-stu-id="cec49-114">Element</span></span>|<span data-ttu-id="cec49-115">描述</span><span class="sxs-lookup"><span data-stu-id="cec49-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="cec49-116">一个配置元素，该元素包含由 **activityDefinitionId** 属性标识的特定工作流的所有查询。</span><span class="sxs-lookup"><span data-stu-id="cec49-116">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cec49-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="cec49-117">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="cec49-118">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="cec49-118">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="cec49-119">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="cec49-119">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)

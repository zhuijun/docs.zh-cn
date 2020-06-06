---
title: <arguments>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 0f327196-f468-4be3-b6c4-68ba981a1bd6
ms.openlocfilehash: f06a2188ea3561437c1453d3a1cb23d42d767f53
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398914"
---
# \<arguments>
<span data-ttu-id="6fda7-101">表示与某一活动状态查询关联的参数的集合。</span><span class="sxs-lookup"><span data-stu-id="6fda7-101">Represents a collection of arguments associated with an activity state query.</span></span>  
  
 <span data-ttu-id="6fda7-102">有关跟踪配置文件查询的详细信息，请参阅[跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="6fda7-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<arguments>**  
  
## <a name="syntax"></a><span data-ttu-id="6fda7-103">语法</span><span class="sxs-lookup"><span data-stu-id="6fda7-103">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6fda7-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="6fda7-104">Attributes and Elements</span></span>  
 <span data-ttu-id="6fda7-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6fda7-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6fda7-106">特性</span><span class="sxs-lookup"><span data-stu-id="6fda7-106">Attributes</span></span>  
 <span data-ttu-id="6fda7-107">无。</span><span class="sxs-lookup"><span data-stu-id="6fda7-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6fda7-108">子元素</span><span class="sxs-lookup"><span data-stu-id="6fda7-108">Child Elements</span></span>  
  
|<span data-ttu-id="6fda7-109">元素</span><span class="sxs-lookup"><span data-stu-id="6fda7-109">Element</span></span>|<span data-ttu-id="6fda7-110">说明</span><span class="sxs-lookup"><span data-stu-id="6fda7-110">Description</span></span>|  
|-------------|-----------------|  
|[\<argument>](argument.md)|<span data-ttu-id="6fda7-111">与活动状态查询相关联的参数。</span><span class="sxs-lookup"><span data-stu-id="6fda7-111">An argument associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6fda7-112">父元素</span><span class="sxs-lookup"><span data-stu-id="6fda7-112">Parent Elements</span></span>  
  
|<span data-ttu-id="6fda7-113">元素</span><span class="sxs-lookup"><span data-stu-id="6fda7-113">Element</span></span>|<span data-ttu-id="6fda7-114">说明</span><span class="sxs-lookup"><span data-stu-id="6fda7-114">Description</span></span>|  
|-------------|-----------------|  
|[\<activityStateQuery>](activitystatequery.md)|<span data-ttu-id="6fda7-115">表示一个配置元素，该元素用于跟踪父活动取消子活动的请求。</span><span class="sxs-lookup"><span data-stu-id="6fda7-115">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="6fda7-116">跟踪参与者需要用此查询来订阅取消请求记录对象。</span><span class="sxs-lookup"><span data-stu-id="6fda7-116">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6fda7-117">注解</span><span class="sxs-lookup"><span data-stu-id="6fda7-117">Remarks</span></span>  
 <span data-ttu-id="6fda7-118">ActivityStateQuery 的一项独特功能是能够在跟踪工作流的执行时提取数据。</span><span class="sxs-lookup"><span data-stu-id="6fda7-118">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="6fda7-119">这在访问跟踪记录后续执行时可提供其他上下文。</span><span class="sxs-lookup"><span data-stu-id="6fda7-119">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="6fda7-120">您可以使用 [\<arguments>](arguments.md) 、 [\<states>](states.md) 和 [\<states>](states.md) 元素从工作流中的任何活动提取任何变量或参数。</span><span class="sxs-lookup"><span data-stu-id="6fda7-120">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="6fda7-121">下面的示例演示用于在发出活动的 `Closed` 跟踪记录时提取变量和自变量的活动状态查询。</span><span class="sxs-lookup"><span data-stu-id="6fda7-121">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="6fda7-122">变量和参数只能通过 ActivityStateRecord 提取，因此使用在跟踪配置文件内进行订阅 [\<activityStateQuery>](activitystatequery.md) 。</span><span class="sxs-lookup"><span data-stu-id="6fda7-122">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6fda7-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6fda7-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="6fda7-124">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="6fda7-124">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="6fda7-125">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="6fda7-125">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)

---
title: <states> 的 <activityStateQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7cc2018-2b79-44f1-825a-bb7ca08690a3
ms.openlocfilehash: e56df08813c091a9c9390db6fc19a7c39f2e8592
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169695"
---
# <a name="states-of-activitystatequery"></a><span data-ttu-id="4c148-102">\<states> 的 \<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="4c148-102">\<states> of \<activityStateQuery></span></span>

<span data-ttu-id="4c148-103">一个配置元素集合，这些元素包含应为其发出跟踪记录的已订阅活动的状态。</span><span class="sxs-lookup"><span data-stu-id="4c148-103">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="4c148-104">有关跟踪配置文件查询的详细信息，请参阅 [跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="4c148-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**  
  
## <a name="syntax"></a><span data-ttu-id="4c148-105">语法</span><span class="sxs-lookup"><span data-stu-id="4c148-105">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <states>
          <state name="String" />
        </states>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c148-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="4c148-106">Attributes and Elements</span></span>  

 <span data-ttu-id="4c148-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4c148-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c148-108">特性</span><span class="sxs-lookup"><span data-stu-id="4c148-108">Attributes</span></span>  

 <span data-ttu-id="4c148-109">无。</span><span class="sxs-lookup"><span data-stu-id="4c148-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4c148-110">子元素</span><span class="sxs-lookup"><span data-stu-id="4c148-110">Child Elements</span></span>  
  
|<span data-ttu-id="4c148-111">元素</span><span class="sxs-lookup"><span data-stu-id="4c148-111">Element</span></span>|<span data-ttu-id="4c148-112">描述</span><span class="sxs-lookup"><span data-stu-id="4c148-112">Description</span></span>|  
|-------------|-----------------|  
|[\<state>](state-of-states.md)|<span data-ttu-id="4c148-113">一个配置元素，该元素包含应为其发出跟踪记录的已订阅活动的状态。</span><span class="sxs-lookup"><span data-stu-id="4c148-113">A configuration element that contains the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4c148-114">父元素</span><span class="sxs-lookup"><span data-stu-id="4c148-114">Parent Elements</span></span>  
  
|<span data-ttu-id="4c148-115">元素</span><span class="sxs-lookup"><span data-stu-id="4c148-115">Element</span></span>|<span data-ttu-id="4c148-116">描述</span><span class="sxs-lookup"><span data-stu-id="4c148-116">Description</span></span>|  
|-------------|-----------------|  
|[\<activityStateQuery>](activitystatequery.md)|<span data-ttu-id="4c148-117">表示一个配置元素，该元素用于跟踪父活动取消子活动的请求。</span><span class="sxs-lookup"><span data-stu-id="4c148-117">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="4c148-118">跟踪参与者需要用此查询来订阅取消请求记录对象。</span><span class="sxs-lookup"><span data-stu-id="4c148-118">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c148-119">备注</span><span class="sxs-lookup"><span data-stu-id="4c148-119">Remarks</span></span>  

 <span data-ttu-id="4c148-120">ActivityStateQuery 的一项独特功能是能够在跟踪工作流的执行时提取数据。</span><span class="sxs-lookup"><span data-stu-id="4c148-120">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="4c148-121">这在访问跟踪记录后续执行时可提供其他上下文。</span><span class="sxs-lookup"><span data-stu-id="4c148-121">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="4c148-122">您可以使用 [\<arguments>](arguments.md) 、 [\<states>](states.md) 和 [\<states>](states.md) 元素从工作流中的任何活动提取任何变量或参数。</span><span class="sxs-lookup"><span data-stu-id="4c148-122">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="4c148-123">下面的示例演示用于在发出活动的 `Closed` 跟踪记录时提取变量和自变量的活动状态查询。</span><span class="sxs-lookup"><span data-stu-id="4c148-123">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="4c148-124">变量和参数只能通过 ActivityStateRecord 提取，因此使用在跟踪配置文件内进行订阅 [\<activityStateQuery>](activitystatequery.md) 。</span><span class="sxs-lookup"><span data-stu-id="4c148-124">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4c148-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="4c148-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4c148-126">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="4c148-126">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4c148-127">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="4c148-127">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)

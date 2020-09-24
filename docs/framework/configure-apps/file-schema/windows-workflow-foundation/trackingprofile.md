---
title: <trackingProfile>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 154830ff-ddd3-4397-a3b5-5b334907777f
ms.openlocfilehash: 8bf7798443e2022adef2738aad3e4e1b9846af53
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161992"
---
# \<trackingProfile>

<span data-ttu-id="dbe1d-101">表示一个配置节，用于创建对跟踪参与者中的工作流跟踪记录的订阅。</span><span class="sxs-lookup"><span data-stu-id="dbe1d-101">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="dbe1d-102">跟踪配置文件包含跟踪查询，这些查询允许跟踪参与者订阅当工作流实例的状态在运行时发生更改时发出的工作流事件。</span><span class="sxs-lookup"><span data-stu-id="dbe1d-102">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="dbe1d-103">跟踪配置文件节中定义的查询用于定义订阅返回的事件类型。</span><span class="sxs-lookup"><span data-stu-id="dbe1d-103">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="dbe1d-104">有关工作流跟踪及其配置的详细信息，请参阅 [工作流跟踪和跟踪](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) 和 [跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="dbe1d-104">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trackingProfile>**  
  
## <a name="syntax"></a><span data-ttu-id="dbe1d-105">语法</span><span class="sxs-lookup"><span data-stu-id="dbe1d-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <participants>
        <add name="String"
             profileName="String"
             type="String" />
      </participants>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String"
                                    childActivityName="String"/>
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String" />
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String"  />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQueries>
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestQueries>
            <cancelRequestQuery activityName="String"
                                childActivityName="String"/>
          </cancelRequestQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String"
                                 name="String"/>
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery activityName="String"
                                   faultHandlerActivityName="String" />
          </faultPropagationQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String" />
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dbe1d-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="dbe1d-106">Attributes and Elements</span></span>  

 <span data-ttu-id="dbe1d-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="dbe1d-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dbe1d-108">特性</span><span class="sxs-lookup"><span data-stu-id="dbe1d-108">Attributes</span></span>  
  
|<span data-ttu-id="dbe1d-109">属性</span><span class="sxs-lookup"><span data-stu-id="dbe1d-109">Attribute</span></span>|<span data-ttu-id="dbe1d-110">说明</span><span class="sxs-lookup"><span data-stu-id="dbe1d-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dbe1d-111">name</span><span class="sxs-lookup"><span data-stu-id="dbe1d-111">name</span></span>|<span data-ttu-id="dbe1d-112">一个字符串，指定跟踪配置文件的名称。</span><span class="sxs-lookup"><span data-stu-id="dbe1d-112">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dbe1d-113">子元素</span><span class="sxs-lookup"><span data-stu-id="dbe1d-113">Child Elements</span></span>  
  
|<span data-ttu-id="dbe1d-114">元素</span><span class="sxs-lookup"><span data-stu-id="dbe1d-114">Element</span></span>|<span data-ttu-id="dbe1d-115">描述</span><span class="sxs-lookup"><span data-stu-id="dbe1d-115">Description</span></span>|  
|-------------|-----------------|  
|[\<participants>](participants.md)|<span data-ttu-id="dbe1d-116">一个配置元素，包含 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> 属性所标识的特定工作流的所有查询。</span><span class="sxs-lookup"><span data-stu-id="dbe1d-116">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dbe1d-117">父元素</span><span class="sxs-lookup"><span data-stu-id="dbe1d-117">Parent Elements</span></span>  
  
|<span data-ttu-id="dbe1d-118">元素</span><span class="sxs-lookup"><span data-stu-id="dbe1d-118">Element</span></span>|<span data-ttu-id="dbe1d-119">描述</span><span class="sxs-lookup"><span data-stu-id="dbe1d-119">Description</span></span>|  
|-------------|-----------------|  
|[\<tracking>](tracking.md)|<span data-ttu-id="dbe1d-120">表示一个配置节，用于定义工作流服务的跟踪设置。</span><span class="sxs-lookup"><span data-stu-id="dbe1d-120">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbe1d-121">备注</span><span class="sxs-lookup"><span data-stu-id="dbe1d-121">Remarks</span></span>  

 <span data-ttu-id="dbe1d-122">跟踪配置文件包含跟踪查询，这些查询允许跟踪参与者订阅当工作流实例的状态在运行时发生更改时发出的工作流事件。</span><span class="sxs-lookup"><span data-stu-id="dbe1d-122">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="dbe1d-123">根据您的监视需求，可以编写一个非常粗陋的配置文件，用来订阅对工作流进行的一小组高级状态更改。</span><span class="sxs-lookup"><span data-stu-id="dbe1d-123">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="dbe1d-124">相反，也可以创建一个非常具体的配置文件，其生成的事件足够丰富，可在以后重新构造详细的执行流。</span><span class="sxs-lookup"><span data-stu-id="dbe1d-124">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="dbe1d-125">跟踪配置文件组织为跟踪记录的声明性订阅，利用这些订阅可以查询特定跟踪记录的工作流运行时。</span><span class="sxs-lookup"><span data-stu-id="dbe1d-125">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="dbe1d-126">有几种查询类型允许您订阅不同的 <xref:System.Activities.Tracking.TrackingRecord> 对象类。</span><span class="sxs-lookup"><span data-stu-id="dbe1d-126">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="dbe1d-127">有关查询的完整列表，请参阅 [\<participants>](participants.md) 和 [跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="dbe1d-127">For a complete list of queries, see [\<participants>](participants.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)..</span></span>  
  
 <span data-ttu-id="dbe1d-128">下面的示例演示配置文件中的跟踪配置文件，该配置文件允许跟踪参与者订阅 `Started` 和 `Completed` 工作流事件。</span><span class="sxs-lookup"><span data-stu-id="dbe1d-128">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
```xml  
<system.serviceModel>  
  <tracking>
    <trackingProfile name="Sample Tracking Profile">  
      <workflow activityDefinitionId="*">  
         <workflowInstanceQueries>  
            <workflowInstanceQuery>  
            <states>  
              <state name="Started"/>  
              <state name="Completed"/>  
            </states>  
          </workflowInstanceQuery>  
        </workflowInstanceQueries>  
      </workflow>  
    </trackingProfile>
   </profiles>  
  </tracking>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dbe1d-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="dbe1d-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="dbe1d-130">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="dbe1d-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="dbe1d-131">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="dbe1d-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)

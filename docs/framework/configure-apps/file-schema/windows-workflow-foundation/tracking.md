---
title: <tracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: fd9b50ed-98a1-4518-836d-e4e02c670822
ms.openlocfilehash: 0b00780dedc15fe90163145f23c57f62369c401f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198738"
---
# \<tracking>

<span data-ttu-id="50cf6-101">表示一个配置节，用于定义工作流服务的跟踪设置。</span><span class="sxs-lookup"><span data-stu-id="50cf6-101">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="50cf6-102">有关工作流跟踪及其配置的详细信息，请参阅工作流 [跟踪和跟踪](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) 和 [配置工作流跟踪](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="50cf6-102">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<tracking>**  
  
## <a name="syntax"></a><span data-ttu-id="50cf6-103">语法</span><span class="sxs-lookup"><span data-stu-id="50cf6-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50cf6-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="50cf6-104">Attributes and Elements</span></span>  

 <span data-ttu-id="50cf6-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="50cf6-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50cf6-106">特性</span><span class="sxs-lookup"><span data-stu-id="50cf6-106">Attributes</span></span>  

 <span data-ttu-id="50cf6-107">无。</span><span class="sxs-lookup"><span data-stu-id="50cf6-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="50cf6-108">子元素</span><span class="sxs-lookup"><span data-stu-id="50cf6-108">Child Elements</span></span>  
  
|<span data-ttu-id="50cf6-109">元素</span><span class="sxs-lookup"><span data-stu-id="50cf6-109">Element</span></span>|<span data-ttu-id="50cf6-110">描述</span><span class="sxs-lookup"><span data-stu-id="50cf6-110">Description</span></span>|  
|-------------|-----------------|  
|[\<participants>](participants.md)|<span data-ttu-id="50cf6-111">一个配置元素集合，这些元素定义了订阅跟踪记录的参与者。</span><span class="sxs-lookup"><span data-stu-id="50cf6-111">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="50cf6-112">跟踪参与者包含用于处理跟踪记录中负载的逻辑（例如，它们可以选择向某个文件中写入）。</span><span class="sxs-lookup"><span data-stu-id="50cf6-112">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[\<trackingProfile>](trackingprofile.md)|<span data-ttu-id="50cf6-113">一个跟踪配置文件，用于筛选从工作流实例发出的跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="50cf6-113">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="50cf6-114">父元素</span><span class="sxs-lookup"><span data-stu-id="50cf6-114">Parent Elements</span></span>  
  
|<span data-ttu-id="50cf6-115">元素</span><span class="sxs-lookup"><span data-stu-id="50cf6-115">Element</span></span>|<span data-ttu-id="50cf6-116">描述</span><span class="sxs-lookup"><span data-stu-id="50cf6-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="50cf6-117">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="50cf6-117">system.ServiceModel</span></span>|<span data-ttu-id="50cf6-118">所有工作流配置元素的根元素。</span><span class="sxs-lookup"><span data-stu-id="50cf6-118">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50cf6-119">备注</span><span class="sxs-lookup"><span data-stu-id="50cf6-119">Remarks</span></span>  

 <span data-ttu-id="50cf6-120">利用跟踪可以检查工作流的执行。</span><span class="sxs-lookup"><span data-stu-id="50cf6-120">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="50cf6-121">工作流跟踪基础结构检测工作流以发出反应执行期间关键事件的记录。</span><span class="sxs-lookup"><span data-stu-id="50cf6-121">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="50cf6-122">例如，工作流实例开始或完成时会发出跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="50cf6-122">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="50cf6-123">跟踪还可以提取与工作流变量关联的相关业务数据。</span><span class="sxs-lookup"><span data-stu-id="50cf6-123">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="50cf6-124">例如，如果工作流表示一个订单处理系统，则可以提取订单 ID 以及跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="50cf6-124">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="50cf6-125">一般来讲，启用 WF 跟踪便于对工作流的执行进行诊断或业务分析。</span><span class="sxs-lookup"><span data-stu-id="50cf6-125">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50cf6-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="50cf6-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="50cf6-127">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="50cf6-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)

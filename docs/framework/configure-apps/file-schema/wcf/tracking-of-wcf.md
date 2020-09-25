---
title: <tracking> WCF 的
ms.date: 03/30/2017
ms.assetid: 70cfaf24-a91c-4e56-ac47-d2ed87a963b3
ms.openlocfilehash: 223a30cd79d346d6ae36ca64fa887a683e6bfc8d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201429"
---
# <a name="tracking-of-wcf"></a><span data-ttu-id="06826-102">\<tracking> WCF 的</span><span class="sxs-lookup"><span data-stu-id="06826-102">\<tracking> of WCF</span></span>

<span data-ttu-id="06826-103">表示一个配置节，用于定义工作流服务的跟踪设置。</span><span class="sxs-lookup"><span data-stu-id="06826-103">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="06826-104">有关工作流跟踪及其配置的详细信息，请参阅工作流 [跟踪和跟踪](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) 和 [配置工作流跟踪](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="06826-104">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<tracking>**  
  
## <a name="syntax"></a><span data-ttu-id="06826-105">语法</span><span class="sxs-lookup"><span data-stu-id="06826-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <participants>
      <add name="String"
           profileName="String"
           type="String" />
    </participants>
    <profiles>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String"
                                    childActivityName="String"/>
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String" />
            <arguments>
              <argument name="String"/>
            </arguments>
            <states>
              <state name="String"/>
            </states>
            <variables>
              <variable name="String"/>
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
                                   faultHandlerActivityName="String"/>
          </faultPropagationQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String"/>
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06826-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="06826-106">Attributes and Elements</span></span>  

 <span data-ttu-id="06826-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="06826-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06826-108">特性</span><span class="sxs-lookup"><span data-stu-id="06826-108">Attributes</span></span>  

 <span data-ttu-id="06826-109">无。</span><span class="sxs-lookup"><span data-stu-id="06826-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="06826-110">子元素</span><span class="sxs-lookup"><span data-stu-id="06826-110">Child Elements</span></span>  
  
|<span data-ttu-id="06826-111">元素</span><span class="sxs-lookup"><span data-stu-id="06826-111">Element</span></span>|<span data-ttu-id="06826-112">描述</span><span class="sxs-lookup"><span data-stu-id="06826-112">Description</span></span>|  
|-------------|-----------------|  
|[\<participants>](../windows-workflow-foundation/participants.md)|<span data-ttu-id="06826-113">一个配置元素集合，这些元素定义了订阅跟踪记录的参与者。</span><span class="sxs-lookup"><span data-stu-id="06826-113">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="06826-114">跟踪参与者包含用于处理跟踪记录中负载的逻辑（例如，它们可以选择向某个文件中写入）。</span><span class="sxs-lookup"><span data-stu-id="06826-114">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[\<trackingProfile>](../windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="06826-115">一个跟踪配置文件，用于筛选从工作流实例发出的跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="06826-115">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="06826-116">父元素</span><span class="sxs-lookup"><span data-stu-id="06826-116">Parent Elements</span></span>  
  
|<span data-ttu-id="06826-117">元素</span><span class="sxs-lookup"><span data-stu-id="06826-117">Element</span></span>|<span data-ttu-id="06826-118">描述</span><span class="sxs-lookup"><span data-stu-id="06826-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="06826-119">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="06826-119">system.ServiceModel</span></span>|<span data-ttu-id="06826-120">所有工作流配置元素的根元素。</span><span class="sxs-lookup"><span data-stu-id="06826-120">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06826-121">备注</span><span class="sxs-lookup"><span data-stu-id="06826-121">Remarks</span></span>  

 <span data-ttu-id="06826-122">利用跟踪可以检查工作流的执行。</span><span class="sxs-lookup"><span data-stu-id="06826-122">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="06826-123">工作流跟踪基础结构检测工作流以发出反应执行期间关键事件的记录。</span><span class="sxs-lookup"><span data-stu-id="06826-123">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="06826-124">例如，工作流实例开始或完成时会发出跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="06826-124">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="06826-125">跟踪还可以提取与工作流变量关联的相关业务数据。</span><span class="sxs-lookup"><span data-stu-id="06826-125">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="06826-126">例如，如果工作流表示一个订单处理系统，则可以提取订单 ID 以及跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="06826-126">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="06826-127">一般来讲，启用 WF 跟踪便于对工作流的执行进行诊断或业务分析。</span><span class="sxs-lookup"><span data-stu-id="06826-127">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06826-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="06826-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="06826-129">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="06826-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)

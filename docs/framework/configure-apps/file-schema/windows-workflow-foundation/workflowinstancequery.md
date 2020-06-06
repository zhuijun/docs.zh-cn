---
title: <workflowInstanceQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
ms.openlocfilehash: 68e44584858e55c136bc3c3dc5f1fb333485fa17
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397513"
---
# \<workflowInstanceQuery>
<span data-ttu-id="714c6-101">表示一个查询，该查询跟踪工作流实例生命周期的更改，例如已开始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="714c6-101">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="714c6-102">有关跟踪配置文件查询的详细信息，请参阅[跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="714c6-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="714c6-103">语法</span><span class="sxs-lookup"><span data-stu-id="714c6-103">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="Name" />
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="714c6-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="714c6-104">Attributes and Elements</span></span>  
 <span data-ttu-id="714c6-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="714c6-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="714c6-106">特性</span><span class="sxs-lookup"><span data-stu-id="714c6-106">Attributes</span></span>  
 <span data-ttu-id="714c6-107">无。</span><span class="sxs-lookup"><span data-stu-id="714c6-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="714c6-108">子元素</span><span class="sxs-lookup"><span data-stu-id="714c6-108">Child Elements</span></span>  
  
|<span data-ttu-id="714c6-109">元素</span><span class="sxs-lookup"><span data-stu-id="714c6-109">Element</span></span>|<span data-ttu-id="714c6-110">说明</span><span class="sxs-lookup"><span data-stu-id="714c6-110">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states.md)|<span data-ttu-id="714c6-111">创建跟踪记录时已跟踪工作流实例中已订阅状态的集合。</span><span class="sxs-lookup"><span data-stu-id="714c6-111">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="714c6-112">父元素</span><span class="sxs-lookup"><span data-stu-id="714c6-112">Parent Elements</span></span>  
  
|<span data-ttu-id="714c6-113">元素</span><span class="sxs-lookup"><span data-stu-id="714c6-113">Element</span></span>|<span data-ttu-id="714c6-114">说明</span><span class="sxs-lookup"><span data-stu-id="714c6-114">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQueries>](workflowinstancequeries.md)|<span data-ttu-id="714c6-115">表示配置元素的集合，这些配置元素跟踪工作流实例生命周期的更改，例如已开始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="714c6-115">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="714c6-116">注解</span><span class="sxs-lookup"><span data-stu-id="714c6-116">Remarks</span></span>  
 <span data-ttu-id="714c6-117"><xref:System.Activities.Tracking.WorkflowInstanceQuery> 用于订阅以下 <xref:System.Activities.Tracking.TrackingRecord> 对象：</span><span class="sxs-lookup"><span data-stu-id="714c6-117">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="714c6-118">示例</span><span class="sxs-lookup"><span data-stu-id="714c6-118">Example</span></span>  
 <span data-ttu-id="714c6-119">下面的配置使用此查询订阅 `Started` 实例状态的工作流实例级跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="714c6-119">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="714c6-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="714c6-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="714c6-121">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="714c6-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="714c6-122">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="714c6-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)

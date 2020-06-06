---
title: <workflowInstanceQueries>WCF 的
ms.date: 03/30/2017
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
ms.openlocfilehash: 8a58767745efab67fb7550de8770fec2c6226117
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854772"
---
# <a name="workflowinstancequeries-of-wcf"></a><span data-ttu-id="3fdf9-102">\<workflowInstanceQueries>WCF 的</span><span class="sxs-lookup"><span data-stu-id="3fdf9-102">\<workflowInstanceQueries> of WCF</span></span>

<span data-ttu-id="3fdf9-103">表示配置元素的集合，这些配置元素跟踪工作流实例生命周期的更改，例如已开始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="3fdf9-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="3fdf9-104">有关跟踪配置文件查询的详细信息，请参阅[跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="3fdf9-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="3fdf9-105">语法</span><span class="sxs-lookup"><span data-stu-id="3fdf9-105">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
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
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3fdf9-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="3fdf9-106">Attributes and elements</span></span>

<span data-ttu-id="3fdf9-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3fdf9-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3fdf9-108">特性</span><span class="sxs-lookup"><span data-stu-id="3fdf9-108">Attributes</span></span>  

<span data-ttu-id="3fdf9-109">无。</span><span class="sxs-lookup"><span data-stu-id="3fdf9-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3fdf9-110">子元素</span><span class="sxs-lookup"><span data-stu-id="3fdf9-110">Child elements</span></span>  
  
|<span data-ttu-id="3fdf9-111">元素</span><span class="sxs-lookup"><span data-stu-id="3fdf9-111">Element</span></span>|<span data-ttu-id="3fdf9-112">说明</span><span class="sxs-lookup"><span data-stu-id="3fdf9-112">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](workflowinstancequery-of-wcf.md)|<span data-ttu-id="3fdf9-113">一个查询，用于跟踪工作流实例生命周期的更改。</span><span class="sxs-lookup"><span data-stu-id="3fdf9-113">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3fdf9-114">父元素</span><span class="sxs-lookup"><span data-stu-id="3fdf9-114">Parent elements</span></span>  
  
|<span data-ttu-id="3fdf9-115">元素</span><span class="sxs-lookup"><span data-stu-id="3fdf9-115">Element</span></span>|<span data-ttu-id="3fdf9-116">说明</span><span class="sxs-lookup"><span data-stu-id="3fdf9-116">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="3fdf9-117">一个配置元素，该元素包含由[activityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId)属性标识的特定工作流的所有查询。</span><span class="sxs-lookup"><span data-stu-id="3fdf9-117">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3fdf9-118">注解</span><span class="sxs-lookup"><span data-stu-id="3fdf9-118">Remarks</span></span>

<span data-ttu-id="3fdf9-119"><xref:System.Activities.Tracking.WorkflowInstanceQuery> 用于订阅以下 <xref:System.Activities.Tracking.TrackingRecord> 对象：</span><span class="sxs-lookup"><span data-stu-id="3fdf9-119">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="3fdf9-120">示例</span><span class="sxs-lookup"><span data-stu-id="3fdf9-120">Example</span></span>  

<span data-ttu-id="3fdf9-121">下面的配置使用此查询订阅 `Started` 实例状态的工作流实例级跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="3fdf9-121">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="3fdf9-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3fdf9-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="3fdf9-123">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="3fdf9-123">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3fdf9-124">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="3fdf9-124">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)

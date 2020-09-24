---
title: <workflowInstanceQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fe7ce85-cf9a-4dbf-a8f7-bc9b1fc2fe35
ms.openlocfilehash: 1b1315aa176f26c356726c5edf1c851bb4c63a47
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148603"
---
# \<workflowInstanceQueries>

<span data-ttu-id="1113d-101">表示配置元素的集合，这些配置元素跟踪工作流实例生命周期的更改，例如已开始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="1113d-101">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="1113d-102">有关跟踪配置文件查询的详细信息，请参阅 [跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="1113d-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="1113d-103">语法</span><span class="sxs-lookup"><span data-stu-id="1113d-103">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="Name"/>
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1113d-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="1113d-104">Attributes and Elements</span></span>  

<span data-ttu-id="1113d-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1113d-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1113d-106">特性</span><span class="sxs-lookup"><span data-stu-id="1113d-106">Attributes</span></span>  

<span data-ttu-id="1113d-107">无。</span><span class="sxs-lookup"><span data-stu-id="1113d-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1113d-108">子元素</span><span class="sxs-lookup"><span data-stu-id="1113d-108">Child Elements</span></span>  
  
|<span data-ttu-id="1113d-109">元素</span><span class="sxs-lookup"><span data-stu-id="1113d-109">Element</span></span>|<span data-ttu-id="1113d-110">描述</span><span class="sxs-lookup"><span data-stu-id="1113d-110">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](workflowinstancequery.md)|<span data-ttu-id="1113d-111">一个查询，用于跟踪工作流实例生命周期的更改。</span><span class="sxs-lookup"><span data-stu-id="1113d-111">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1113d-112">父元素</span><span class="sxs-lookup"><span data-stu-id="1113d-112">Parent Elements</span></span>  
  
|<span data-ttu-id="1113d-113">元素</span><span class="sxs-lookup"><span data-stu-id="1113d-113">Element</span></span>|<span data-ttu-id="1113d-114">描述</span><span class="sxs-lookup"><span data-stu-id="1113d-114">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="1113d-115">一个配置元素，该元素包含由 **activityDefinitionId** 属性标识的特定工作流的所有查询。</span><span class="sxs-lookup"><span data-stu-id="1113d-115">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1113d-116">备注</span><span class="sxs-lookup"><span data-stu-id="1113d-116">Remarks</span></span>  

<span data-ttu-id="1113d-117"><xref:System.Activities.Tracking.WorkflowInstanceQuery> 用于订阅以下 <xref:System.Activities.Tracking.TrackingRecord> 对象：</span><span class="sxs-lookup"><span data-stu-id="1113d-117">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="1113d-118">示例</span><span class="sxs-lookup"><span data-stu-id="1113d-118">Example</span></span>  

<span data-ttu-id="1113d-119">下面的配置使用此查询订阅 `Started` 实例状态的工作流实例级跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="1113d-119">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1113d-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="1113d-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="1113d-121">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="1113d-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1113d-122">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="1113d-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)

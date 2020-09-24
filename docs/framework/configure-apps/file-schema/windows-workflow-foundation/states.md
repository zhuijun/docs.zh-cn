---
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: e759f86e7746eaf3fdd72ed923612b24ef9b0c23
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150812"
---
# \<states>

<span data-ttu-id="f0abc-101">表示创建跟踪记录时已跟踪工作流实例中已订阅状态的集合。</span><span class="sxs-lookup"><span data-stu-id="f0abc-101">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="f0abc-102">有关跟踪配置文件查询的详细信息，请参阅 [跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f0abc-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**  
  
## <a name="syntax"></a><span data-ttu-id="f0abc-103">语法</span><span class="sxs-lookup"><span data-stu-id="f0abc-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0abc-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="f0abc-104">Attributes and Elements</span></span>  

 <span data-ttu-id="f0abc-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f0abc-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0abc-106">特性</span><span class="sxs-lookup"><span data-stu-id="f0abc-106">Attributes</span></span>  

 <span data-ttu-id="f0abc-107">无。</span><span class="sxs-lookup"><span data-stu-id="f0abc-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f0abc-108">子元素</span><span class="sxs-lookup"><span data-stu-id="f0abc-108">Child Elements</span></span>  
  
|<span data-ttu-id="f0abc-109">元素</span><span class="sxs-lookup"><span data-stu-id="f0abc-109">Element</span></span>|<span data-ttu-id="f0abc-110">描述</span><span class="sxs-lookup"><span data-stu-id="f0abc-110">Description</span></span>|  
|-------------|-----------------|  
|[\<state>](states.md)|<span data-ttu-id="f0abc-111">创建跟踪记录时已跟踪工作流实例中的一个已订阅状态。</span><span class="sxs-lookup"><span data-stu-id="f0abc-111">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f0abc-112">父元素</span><span class="sxs-lookup"><span data-stu-id="f0abc-112">Parent Elements</span></span>  
  
|<span data-ttu-id="f0abc-113">元素</span><span class="sxs-lookup"><span data-stu-id="f0abc-113">Element</span></span>|<span data-ttu-id="f0abc-114">描述</span><span class="sxs-lookup"><span data-stu-id="f0abc-114">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](workflowinstancequery.md)|<span data-ttu-id="f0abc-115">一个查询，该查询跟踪工作流实例生命周期的更改，例如已开始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="f0abc-115">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0abc-116">备注</span><span class="sxs-lookup"><span data-stu-id="f0abc-116">Remarks</span></span>  

 <span data-ttu-id="f0abc-117">返回的记录由此集合中的状态进行筛选。</span><span class="sxs-lookup"><span data-stu-id="f0abc-117">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="f0abc-118">下表中列出了可能的状态值。</span><span class="sxs-lookup"><span data-stu-id="f0abc-118">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="f0abc-119">状态</span><span class="sxs-lookup"><span data-stu-id="f0abc-119">State</span></span>|<span data-ttu-id="f0abc-120">说明</span><span class="sxs-lookup"><span data-stu-id="f0abc-120">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f0abc-121">Aborted</span><span class="sxs-lookup"><span data-stu-id="f0abc-121">Aborted</span></span>|<span data-ttu-id="f0abc-122">工作流实例已中止。</span><span class="sxs-lookup"><span data-stu-id="f0abc-122">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="f0abc-123">已完成</span><span class="sxs-lookup"><span data-stu-id="f0abc-123">Completed</span></span>|<span data-ttu-id="f0abc-124">工作流实例已完成。</span><span class="sxs-lookup"><span data-stu-id="f0abc-124">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="f0abc-125">Deleted</span><span class="sxs-lookup"><span data-stu-id="f0abc-125">Deleted</span></span>|<span data-ttu-id="f0abc-126">工作流实例已删除。</span><span class="sxs-lookup"><span data-stu-id="f0abc-126">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="f0abc-127">空闲</span><span class="sxs-lookup"><span data-stu-id="f0abc-127">Idle</span></span>|<span data-ttu-id="f0abc-128">工作流实例处于空闲状态。</span><span class="sxs-lookup"><span data-stu-id="f0abc-128">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="f0abc-129">持久化</span><span class="sxs-lookup"><span data-stu-id="f0abc-129">Persisted</span></span>|<span data-ttu-id="f0abc-130">工作流实例已保留。</span><span class="sxs-lookup"><span data-stu-id="f0abc-130">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="f0abc-131">Resumed</span><span class="sxs-lookup"><span data-stu-id="f0abc-131">Resumed</span></span>|<span data-ttu-id="f0abc-132">工作流实例已恢复。</span><span class="sxs-lookup"><span data-stu-id="f0abc-132">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="f0abc-133">Started</span><span class="sxs-lookup"><span data-stu-id="f0abc-133">Started</span></span>|<span data-ttu-id="f0abc-134">工作流实例已启动。</span><span class="sxs-lookup"><span data-stu-id="f0abc-134">The workflow instance is started.</span></span>|  
|<span data-ttu-id="f0abc-135">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="f0abc-135">UnhandledException</span></span>|<span data-ttu-id="f0abc-136">工作流实例遇到了未经处理的异常。</span><span class="sxs-lookup"><span data-stu-id="f0abc-136">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="f0abc-137">已卸载</span><span class="sxs-lookup"><span data-stu-id="f0abc-137">Unloaded</span></span>|<span data-ttu-id="f0abc-138">工作流实例已卸载。</span><span class="sxs-lookup"><span data-stu-id="f0abc-138">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="f0abc-139">已取消</span><span class="sxs-lookup"><span data-stu-id="f0abc-139">Canceled</span></span>|<span data-ttu-id="f0abc-140">工作流实例已取消。</span><span class="sxs-lookup"><span data-stu-id="f0abc-140">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="f0abc-141">已挂起</span><span class="sxs-lookup"><span data-stu-id="f0abc-141">Suspended</span></span>|<span data-ttu-id="f0abc-142">工作流实例处于挂起状态。</span><span class="sxs-lookup"><span data-stu-id="f0abc-142">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="f0abc-143">终止</span><span class="sxs-lookup"><span data-stu-id="f0abc-143">Terminated</span></span>|<span data-ttu-id="f0abc-144">工作流实例已终止。</span><span class="sxs-lookup"><span data-stu-id="f0abc-144">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="f0abc-145">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="f0abc-145">Unsuspended</span></span>|<span data-ttu-id="f0abc-146">工作流实例已取消挂起。</span><span class="sxs-lookup"><span data-stu-id="f0abc-146">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f0abc-147">示例</span><span class="sxs-lookup"><span data-stu-id="f0abc-147">Example</span></span>  

 <span data-ttu-id="f0abc-148">下面的配置使用此查询订阅 `Started` 实例状态的工作流实例级跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="f0abc-148">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f0abc-149">请参阅</span><span class="sxs-lookup"><span data-stu-id="f0abc-149">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f0abc-150">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="f0abc-150">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f0abc-151">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="f0abc-151">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)

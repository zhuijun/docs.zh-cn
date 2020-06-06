---
title: <states>WCF，<workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
ms.openlocfilehash: 5b779cf1074687dbd648b23d04f7cf3a354a2014
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855038"
---
# <a name="states-of-wcf-workflowinstancequery"></a><span data-ttu-id="a50ab-102">\<states>WCF，\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="a50ab-102">\<states> of WCF, \<workflowInstanceQuery></span></span>

<span data-ttu-id="a50ab-103">表示创建跟踪记录时已跟踪工作流实例中已订阅状态的集合。</span><span class="sxs-lookup"><span data-stu-id="a50ab-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
<span data-ttu-id="a50ab-104">有关跟踪配置文件查询的详细信息，请参阅[跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="a50ab-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**  
  
## <a name="syntax"></a><span data-ttu-id="a50ab-105">语法</span><span class="sxs-lookup"><span data-stu-id="a50ab-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a50ab-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="a50ab-106">Attributes and elements</span></span>

<span data-ttu-id="a50ab-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a50ab-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a50ab-108">特性</span><span class="sxs-lookup"><span data-stu-id="a50ab-108">Attributes</span></span>  

<span data-ttu-id="a50ab-109">无。</span><span class="sxs-lookup"><span data-stu-id="a50ab-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a50ab-110">子元素</span><span class="sxs-lookup"><span data-stu-id="a50ab-110">Child elements</span></span>
  
|<span data-ttu-id="a50ab-111">元素</span><span class="sxs-lookup"><span data-stu-id="a50ab-111">Element</span></span>|<span data-ttu-id="a50ab-112">说明</span><span class="sxs-lookup"><span data-stu-id="a50ab-112">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](state-of-wcf-workflowinstancequery.md)|<span data-ttu-id="a50ab-113">创建跟踪记录时已跟踪工作流实例中的一个已订阅状态。</span><span class="sxs-lookup"><span data-stu-id="a50ab-113">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a50ab-114">父元素</span><span class="sxs-lookup"><span data-stu-id="a50ab-114">Parent elements</span></span>  
  
|<span data-ttu-id="a50ab-115">元素</span><span class="sxs-lookup"><span data-stu-id="a50ab-115">Element</span></span>|<span data-ttu-id="a50ab-116">说明</span><span class="sxs-lookup"><span data-stu-id="a50ab-116">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](../windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="a50ab-117">一个查询，该查询跟踪工作流实例生命周期的更改，例如已开始或已完成的事件。</span><span class="sxs-lookup"><span data-stu-id="a50ab-117">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a50ab-118">注解</span><span class="sxs-lookup"><span data-stu-id="a50ab-118">Remarks</span></span>

<span data-ttu-id="a50ab-119">返回的记录由此集合中的状态进行筛选。</span><span class="sxs-lookup"><span data-stu-id="a50ab-119">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="a50ab-120">下表中列出了可能的状态值。</span><span class="sxs-lookup"><span data-stu-id="a50ab-120">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="a50ab-121">州省/自治区/直辖市</span><span class="sxs-lookup"><span data-stu-id="a50ab-121">State</span></span>|<span data-ttu-id="a50ab-122">说明</span><span class="sxs-lookup"><span data-stu-id="a50ab-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a50ab-123">Aborted</span><span class="sxs-lookup"><span data-stu-id="a50ab-123">Aborted</span></span>|<span data-ttu-id="a50ab-124">工作流实例已中止。</span><span class="sxs-lookup"><span data-stu-id="a50ab-124">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="a50ab-125">已完成</span><span class="sxs-lookup"><span data-stu-id="a50ab-125">Completed</span></span>|<span data-ttu-id="a50ab-126">工作流实例已完成。</span><span class="sxs-lookup"><span data-stu-id="a50ab-126">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="a50ab-127">已删除</span><span class="sxs-lookup"><span data-stu-id="a50ab-127">Deleted</span></span>|<span data-ttu-id="a50ab-128">工作流实例已删除。</span><span class="sxs-lookup"><span data-stu-id="a50ab-128">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="a50ab-129">空闲</span><span class="sxs-lookup"><span data-stu-id="a50ab-129">Idle</span></span>|<span data-ttu-id="a50ab-130">工作流实例处于空闲状态。</span><span class="sxs-lookup"><span data-stu-id="a50ab-130">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="a50ab-131">Persisted</span><span class="sxs-lookup"><span data-stu-id="a50ab-131">Persisted</span></span>|<span data-ttu-id="a50ab-132">工作流实例已保留。</span><span class="sxs-lookup"><span data-stu-id="a50ab-132">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="a50ab-133">Resumed</span><span class="sxs-lookup"><span data-stu-id="a50ab-133">Resumed</span></span>|<span data-ttu-id="a50ab-134">工作流实例已恢复。</span><span class="sxs-lookup"><span data-stu-id="a50ab-134">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="a50ab-135">已开始</span><span class="sxs-lookup"><span data-stu-id="a50ab-135">Started</span></span>|<span data-ttu-id="a50ab-136">工作流实例已启动。</span><span class="sxs-lookup"><span data-stu-id="a50ab-136">The workflow instance is started.</span></span>|  
|<span data-ttu-id="a50ab-137">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="a50ab-137">UnhandledException</span></span>|<span data-ttu-id="a50ab-138">工作流实例遇到了未经处理的异常。</span><span class="sxs-lookup"><span data-stu-id="a50ab-138">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="a50ab-139">已卸载</span><span class="sxs-lookup"><span data-stu-id="a50ab-139">Unloaded</span></span>|<span data-ttu-id="a50ab-140">工作流实例已卸载。</span><span class="sxs-lookup"><span data-stu-id="a50ab-140">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="a50ab-141">已取消</span><span class="sxs-lookup"><span data-stu-id="a50ab-141">Canceled</span></span>|<span data-ttu-id="a50ab-142">工作流实例已取消。</span><span class="sxs-lookup"><span data-stu-id="a50ab-142">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="a50ab-143">已挂起</span><span class="sxs-lookup"><span data-stu-id="a50ab-143">Suspended</span></span>|<span data-ttu-id="a50ab-144">工作流实例处于挂起状态。</span><span class="sxs-lookup"><span data-stu-id="a50ab-144">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="a50ab-145">Terminated</span><span class="sxs-lookup"><span data-stu-id="a50ab-145">Terminated</span></span>|<span data-ttu-id="a50ab-146">工作流实例已终止。</span><span class="sxs-lookup"><span data-stu-id="a50ab-146">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="a50ab-147">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="a50ab-147">Unsuspended</span></span>|<span data-ttu-id="a50ab-148">工作流实例已取消挂起。</span><span class="sxs-lookup"><span data-stu-id="a50ab-148">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a50ab-149">示例</span><span class="sxs-lookup"><span data-stu-id="a50ab-149">Example</span></span>

<span data-ttu-id="a50ab-150">下面的配置使用此查询订阅 `Started` 实例状态的工作流实例级跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="a50ab-150">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="a50ab-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a50ab-151">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a50ab-152">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="a50ab-152">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a50ab-153">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="a50ab-153">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)

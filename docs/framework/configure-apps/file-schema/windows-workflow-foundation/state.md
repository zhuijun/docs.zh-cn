---
title: <state>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 169fa900b5be9a9577818b68b540184afd4a6681
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169721"
---
# \<state>

<span data-ttu-id="af58b-101">表示创建跟踪记录时已跟踪工作流实例中已订阅状态的集合。</span><span class="sxs-lookup"><span data-stu-id="af58b-101">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="af58b-102">有关跟踪配置文件查询的详细信息，请参阅 [跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="af58b-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**  
  
## <a name="syntax"></a><span data-ttu-id="af58b-103">语法</span><span class="sxs-lookup"><span data-stu-id="af58b-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="af58b-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="af58b-104">Attributes and Elements</span></span>  

 <span data-ttu-id="af58b-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="af58b-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="af58b-106">特性</span><span class="sxs-lookup"><span data-stu-id="af58b-106">Attributes</span></span>  
  
|<span data-ttu-id="af58b-107">属性</span><span class="sxs-lookup"><span data-stu-id="af58b-107">Attribute</span></span>|<span data-ttu-id="af58b-108">说明</span><span class="sxs-lookup"><span data-stu-id="af58b-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="af58b-109">name</span><span class="sxs-lookup"><span data-stu-id="af58b-109">name</span></span>|<span data-ttu-id="af58b-110">一个字符串，指定创建跟踪记录时已跟踪工作流实例中的已订阅状态。</span><span class="sxs-lookup"><span data-stu-id="af58b-110">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="af58b-111">子元素</span><span class="sxs-lookup"><span data-stu-id="af58b-111">Child Elements</span></span>  

 <span data-ttu-id="af58b-112">无。</span><span class="sxs-lookup"><span data-stu-id="af58b-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="af58b-113">父元素</span><span class="sxs-lookup"><span data-stu-id="af58b-113">Parent Elements</span></span>  
  
|<span data-ttu-id="af58b-114">元素</span><span class="sxs-lookup"><span data-stu-id="af58b-114">Element</span></span>|<span data-ttu-id="af58b-115">描述</span><span class="sxs-lookup"><span data-stu-id="af58b-115">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states.md)|<span data-ttu-id="af58b-116">创建跟踪记录时已跟踪工作流实例中已订阅状态的集合。</span><span class="sxs-lookup"><span data-stu-id="af58b-116">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af58b-117">备注</span><span class="sxs-lookup"><span data-stu-id="af58b-117">Remarks</span></span>  

 <span data-ttu-id="af58b-118">返回的记录由此集合中的状态进行筛选。</span><span class="sxs-lookup"><span data-stu-id="af58b-118">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="af58b-119">下表中列出了可能的状态值。</span><span class="sxs-lookup"><span data-stu-id="af58b-119">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="af58b-120">状态</span><span class="sxs-lookup"><span data-stu-id="af58b-120">State</span></span>|<span data-ttu-id="af58b-121">说明</span><span class="sxs-lookup"><span data-stu-id="af58b-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="af58b-122">Aborted</span><span class="sxs-lookup"><span data-stu-id="af58b-122">Aborted</span></span>|<span data-ttu-id="af58b-123">工作流实例已中止。</span><span class="sxs-lookup"><span data-stu-id="af58b-123">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="af58b-124">已完成</span><span class="sxs-lookup"><span data-stu-id="af58b-124">Completed</span></span>|<span data-ttu-id="af58b-125">工作流实例已完成。</span><span class="sxs-lookup"><span data-stu-id="af58b-125">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="af58b-126">Deleted</span><span class="sxs-lookup"><span data-stu-id="af58b-126">Deleted</span></span>|<span data-ttu-id="af58b-127">工作流实例已删除。</span><span class="sxs-lookup"><span data-stu-id="af58b-127">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="af58b-128">空闲</span><span class="sxs-lookup"><span data-stu-id="af58b-128">Idle</span></span>|<span data-ttu-id="af58b-129">工作流实例处于空闲状态。</span><span class="sxs-lookup"><span data-stu-id="af58b-129">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="af58b-130">持久化</span><span class="sxs-lookup"><span data-stu-id="af58b-130">Persisted</span></span>|<span data-ttu-id="af58b-131">工作流实例已保留。</span><span class="sxs-lookup"><span data-stu-id="af58b-131">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="af58b-132">Resumed</span><span class="sxs-lookup"><span data-stu-id="af58b-132">Resumed</span></span>|<span data-ttu-id="af58b-133">工作流实例已恢复。</span><span class="sxs-lookup"><span data-stu-id="af58b-133">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="af58b-134">Started</span><span class="sxs-lookup"><span data-stu-id="af58b-134">Started</span></span>|<span data-ttu-id="af58b-135">工作流实例已启动。</span><span class="sxs-lookup"><span data-stu-id="af58b-135">The workflow instance is started.</span></span>|  
|<span data-ttu-id="af58b-136">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="af58b-136">UnhandledException</span></span>|<span data-ttu-id="af58b-137">工作流实例遇到了未经处理的异常。</span><span class="sxs-lookup"><span data-stu-id="af58b-137">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="af58b-138">已卸载</span><span class="sxs-lookup"><span data-stu-id="af58b-138">Unloaded</span></span>|<span data-ttu-id="af58b-139">工作流实例已卸载。</span><span class="sxs-lookup"><span data-stu-id="af58b-139">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="af58b-140">已取消</span><span class="sxs-lookup"><span data-stu-id="af58b-140">Canceled</span></span>|<span data-ttu-id="af58b-141">工作流实例已取消。</span><span class="sxs-lookup"><span data-stu-id="af58b-141">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="af58b-142">已挂起</span><span class="sxs-lookup"><span data-stu-id="af58b-142">Suspended</span></span>|<span data-ttu-id="af58b-143">工作流实例处于挂起状态。</span><span class="sxs-lookup"><span data-stu-id="af58b-143">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="af58b-144">终止</span><span class="sxs-lookup"><span data-stu-id="af58b-144">Terminated</span></span>|<span data-ttu-id="af58b-145">工作流实例已终止。</span><span class="sxs-lookup"><span data-stu-id="af58b-145">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="af58b-146">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="af58b-146">Unsuspended</span></span>|<span data-ttu-id="af58b-147">工作流实例已取消挂起。</span><span class="sxs-lookup"><span data-stu-id="af58b-147">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="af58b-148">示例</span><span class="sxs-lookup"><span data-stu-id="af58b-148">Example</span></span>  

 <span data-ttu-id="af58b-149">下面的配置使用此查询订阅 `Started` 实例状态的工作流实例级跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="af58b-149">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="af58b-150">请参阅</span><span class="sxs-lookup"><span data-stu-id="af58b-150">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="af58b-151">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="af58b-151">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="af58b-152">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="af58b-152">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)

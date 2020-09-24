---
title: <state> WCF， <workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
ms.openlocfilehash: c323f7dba265e7fbcb09482115694088e761af0e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148888"
---
# <a name="state-of-wcf-workflowinstancequery"></a><span data-ttu-id="14c3b-102">\<state> WCF， \<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="14c3b-102">\<state> of WCF, \<workflowInstanceQuery></span></span>

<span data-ttu-id="14c3b-103">表示创建跟踪记录时已跟踪工作流实例中已订阅状态的集合。</span><span class="sxs-lookup"><span data-stu-id="14c3b-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="14c3b-104">有关跟踪配置文件查询的详细信息，请参阅 [跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="14c3b-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states-of-wcf-workflowinstancequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**  
  
## <a name="syntax"></a><span data-ttu-id="14c3b-105">语法</span><span class="sxs-lookup"><span data-stu-id="14c3b-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14c3b-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="14c3b-106">Attributes and elements</span></span>

<span data-ttu-id="14c3b-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="14c3b-107">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="14c3b-108">特性</span><span class="sxs-lookup"><span data-stu-id="14c3b-108">Attributes</span></span>

|<span data-ttu-id="14c3b-109">属性</span><span class="sxs-lookup"><span data-stu-id="14c3b-109">Attribute</span></span>|<span data-ttu-id="14c3b-110">描述</span><span class="sxs-lookup"><span data-stu-id="14c3b-110">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="14c3b-111">一个字符串，指定创建跟踪记录时已跟踪工作流实例中的已订阅状态。</span><span class="sxs-lookup"><span data-stu-id="14c3b-111">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="14c3b-112">子元素</span><span class="sxs-lookup"><span data-stu-id="14c3b-112">Child elements</span></span>

<span data-ttu-id="14c3b-113">无。</span><span class="sxs-lookup"><span data-stu-id="14c3b-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="14c3b-114">父元素</span><span class="sxs-lookup"><span data-stu-id="14c3b-114">Parent elements</span></span>

|<span data-ttu-id="14c3b-115">元素</span><span class="sxs-lookup"><span data-stu-id="14c3b-115">Element</span></span>|<span data-ttu-id="14c3b-116">描述</span><span class="sxs-lookup"><span data-stu-id="14c3b-116">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="14c3b-117">创建跟踪记录时已跟踪工作流实例中已订阅状态的集合。</span><span class="sxs-lookup"><span data-stu-id="14c3b-117">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14c3b-118">备注</span><span class="sxs-lookup"><span data-stu-id="14c3b-118">Remarks</span></span>  

<span data-ttu-id="14c3b-119">返回的记录由此集合中的状态进行筛选。</span><span class="sxs-lookup"><span data-stu-id="14c3b-119">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="14c3b-120">下表描述了可能的状态值：</span><span class="sxs-lookup"><span data-stu-id="14c3b-120">Possible state values are described in the following table:</span></span>
  
|<span data-ttu-id="14c3b-121">状态</span><span class="sxs-lookup"><span data-stu-id="14c3b-121">State</span></span>|<span data-ttu-id="14c3b-122">说明</span><span class="sxs-lookup"><span data-stu-id="14c3b-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="14c3b-123">Aborted</span><span class="sxs-lookup"><span data-stu-id="14c3b-123">Aborted</span></span>|<span data-ttu-id="14c3b-124">工作流实例已中止。</span><span class="sxs-lookup"><span data-stu-id="14c3b-124">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="14c3b-125">已完成</span><span class="sxs-lookup"><span data-stu-id="14c3b-125">Completed</span></span>|<span data-ttu-id="14c3b-126">工作流实例已完成。</span><span class="sxs-lookup"><span data-stu-id="14c3b-126">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="14c3b-127">Deleted</span><span class="sxs-lookup"><span data-stu-id="14c3b-127">Deleted</span></span>|<span data-ttu-id="14c3b-128">工作流实例已删除。</span><span class="sxs-lookup"><span data-stu-id="14c3b-128">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="14c3b-129">空闲</span><span class="sxs-lookup"><span data-stu-id="14c3b-129">Idle</span></span>|<span data-ttu-id="14c3b-130">工作流实例处于空闲状态。</span><span class="sxs-lookup"><span data-stu-id="14c3b-130">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="14c3b-131">持久化</span><span class="sxs-lookup"><span data-stu-id="14c3b-131">Persisted</span></span>|<span data-ttu-id="14c3b-132">工作流实例已保留。</span><span class="sxs-lookup"><span data-stu-id="14c3b-132">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="14c3b-133">Resumed</span><span class="sxs-lookup"><span data-stu-id="14c3b-133">Resumed</span></span>|<span data-ttu-id="14c3b-134">工作流实例已恢复。</span><span class="sxs-lookup"><span data-stu-id="14c3b-134">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="14c3b-135">Started</span><span class="sxs-lookup"><span data-stu-id="14c3b-135">Started</span></span>|<span data-ttu-id="14c3b-136">工作流实例已启动。</span><span class="sxs-lookup"><span data-stu-id="14c3b-136">The workflow instance is started.</span></span>|  
|<span data-ttu-id="14c3b-137">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="14c3b-137">UnhandledException</span></span>|<span data-ttu-id="14c3b-138">工作流实例遇到了未经处理的异常。</span><span class="sxs-lookup"><span data-stu-id="14c3b-138">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="14c3b-139">已卸载</span><span class="sxs-lookup"><span data-stu-id="14c3b-139">Unloaded</span></span>|<span data-ttu-id="14c3b-140">工作流实例已卸载。</span><span class="sxs-lookup"><span data-stu-id="14c3b-140">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="14c3b-141">已取消</span><span class="sxs-lookup"><span data-stu-id="14c3b-141">Canceled</span></span>|<span data-ttu-id="14c3b-142">工作流实例已取消。</span><span class="sxs-lookup"><span data-stu-id="14c3b-142">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="14c3b-143">已挂起</span><span class="sxs-lookup"><span data-stu-id="14c3b-143">Suspended</span></span>|<span data-ttu-id="14c3b-144">工作流实例处于挂起状态。</span><span class="sxs-lookup"><span data-stu-id="14c3b-144">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="14c3b-145">终止</span><span class="sxs-lookup"><span data-stu-id="14c3b-145">Terminated</span></span>|<span data-ttu-id="14c3b-146">工作流实例已终止。</span><span class="sxs-lookup"><span data-stu-id="14c3b-146">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="14c3b-147">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="14c3b-147">Unsuspended</span></span>|<span data-ttu-id="14c3b-148">工作流实例已取消挂起。</span><span class="sxs-lookup"><span data-stu-id="14c3b-148">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="14c3b-149">示例</span><span class="sxs-lookup"><span data-stu-id="14c3b-149">Example</span></span>

<span data-ttu-id="14c3b-150">下面的配置使用此查询订阅 `Started` 实例状态的工作流实例级跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="14c3b-150">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="14c3b-151">请参阅</span><span class="sxs-lookup"><span data-stu-id="14c3b-151">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="14c3b-152">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="14c3b-152">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="14c3b-153">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="14c3b-153">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)

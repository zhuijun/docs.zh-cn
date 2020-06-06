---
title: <sqlWorkflowInstanceStore>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8a4e4214-fc51-4f4d-b968-0427c37a9520
ms.openlocfilehash: 56a44fdb62062903ca3ad00f8105a66ccab02cca
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79151957"
---
# \<sqlWorkflowInstanceStore>
<span data-ttu-id="dbf39-101">一种服务行为，它允许您配置 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 功能，该功能支持将工作流服务实例的状态信息保持到 SQL Server 2005 或 SQL Server 2008 数据库中。</span><span class="sxs-lookup"><span data-stu-id="dbf39-101">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span> <span data-ttu-id="dbf39-102">有关此功能的详细信息，请参阅[SQL 工作流实例存储](../../../windows-workflow-foundation/sql-workflow-instance-store.md)。</span><span class="sxs-lookup"><span data-stu-id="dbf39-102">For more information on this feature, see [SQL Workflow Instance Store](../../../windows-workflow-foundation/sql-workflow-instance-store.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sqlWorkflowInstanceStore>**  
  
## <a name="syntax"></a><span data-ttu-id="dbf39-103">语法</span><span class="sxs-lookup"><span data-stu-id="dbf39-103">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sqlWorkflowInstanceStore connectionStringName="String"
                                hostLockRenewalPeriod="TimeSpan"
                                instanceCompletionAction="DeleteNothing/DeleteAll"
                                instanceEncodingAction="None/GZip"
                                instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry"
                                runnableInstancesDetectionPeriod="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dbf39-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="dbf39-104">Attributes and Elements</span></span>  
 <span data-ttu-id="dbf39-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="dbf39-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dbf39-106">特性</span><span class="sxs-lookup"><span data-stu-id="dbf39-106">Attributes</span></span>  
  
|<span data-ttu-id="dbf39-107">属性</span><span class="sxs-lookup"><span data-stu-id="dbf39-107">Attribute</span></span>|<span data-ttu-id="dbf39-108">说明</span><span class="sxs-lookup"><span data-stu-id="dbf39-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dbf39-109">connectionString</span><span class="sxs-lookup"><span data-stu-id="dbf39-109">connectionString</span></span>|<span data-ttu-id="dbf39-110">一个字符串，包含用于连接到基础持久性数据库的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="dbf39-110">A string that contains a connection string used to connect to an underlying persistence database.</span></span>|  
|<span data-ttu-id="dbf39-111">connectionStringName</span><span class="sxs-lookup"><span data-stu-id="dbf39-111">connectionStringName</span></span>|<span data-ttu-id="dbf39-112">一个字符串，包含指向数据库服务器的已命名连接字符串。</span><span class="sxs-lookup"><span data-stu-id="dbf39-112">A string that contains a named connection string to the database server.</span></span> <span data-ttu-id="dbf39-113">命名连接字符串的示例为 "DefaultConnectionString"。</span><span class="sxs-lookup"><span data-stu-id="dbf39-113">An example of a named connection string is "DefaultConnectionString".</span></span>|  
|<span data-ttu-id="dbf39-114">hostLockRenewalPeriod</span><span class="sxs-lookup"><span data-stu-id="dbf39-114">hostLockRenewalPeriod</span></span>|<span data-ttu-id="dbf39-115">一个 Timespan 值，指定宿主必须在其间续订对某个实例的锁定的时间段。</span><span class="sxs-lookup"><span data-stu-id="dbf39-115">A Timespan value that specifies the time period in which the host must renew the lock on an instance.</span></span> <span data-ttu-id="dbf39-116">如果宿主没有在指定的时间段内续订锁定，则会解除锁定此实例，并且另一宿主可能会选取此实例。</span><span class="sxs-lookup"><span data-stu-id="dbf39-116">If the host does not renew the lock in the specified time period, the instance is unlocked and may be picked up by another host.</span></span><br /><br /> <span data-ttu-id="dbf39-117">卸载一个工作流意味着该工作流已持久保存。</span><span class="sxs-lookup"><span data-stu-id="dbf39-117">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="dbf39-118">如果此特性设置为零，则在工作流进入空闲状态后会立即持久保存并卸载该工作流实例。</span><span class="sxs-lookup"><span data-stu-id="dbf39-118">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="dbf39-119">将此特性设置为 TimeSpan.MaxValue 可以有效地禁用卸载操作。</span><span class="sxs-lookup"><span data-stu-id="dbf39-119">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="dbf39-120">处于空闲状态的工作流实例永远不会被卸载。</span><span class="sxs-lookup"><span data-stu-id="dbf39-120">Idle workflow instances are never unloaded.</span></span>|  
|<span data-ttu-id="dbf39-121">instanceCompletionAction</span><span class="sxs-lookup"><span data-stu-id="dbf39-121">instanceCompletionAction</span></span>|<span data-ttu-id="dbf39-122">一个值，指定在工作流实例完成之后，该工作流实例数据是保留在持久性存储区中还是被删除。</span><span class="sxs-lookup"><span data-stu-id="dbf39-122">A value that specifies whether workflow instance data is kept in the persistence store after the workflow instance completes or if it is deleted at that point.</span></span> <span data-ttu-id="dbf39-123">此值的类型为 <xref:System.Activities.DurableInstancing.InstanceCompletionAction>。</span><span class="sxs-lookup"><span data-stu-id="dbf39-123">This value is of type <xref:System.Activities.DurableInstancing.InstanceCompletionAction>.</span></span><br /><br /> <span data-ttu-id="dbf39-124">枚举的操作包括在实例完成其操作后删除持久性存储区中的实例数据或不删除持久性存储区中的实例数据。</span><span class="sxs-lookup"><span data-stu-id="dbf39-124">The enumerated actions consist of deleting the instance data from the persistence store or not deleting the instance data from the persistence store, when the instance has completed its operation.</span></span><br /><br /> <span data-ttu-id="dbf39-125">完成实例之后保留实例会导致持久性数据库快速增大，这会影响数据库的性能。</span><span class="sxs-lookup"><span data-stu-id="dbf39-125">Keeping instances after completion causes the persistence database to grow rapidly and this affects the performance of the database.</span></span> <span data-ttu-id="dbf39-126">您应当配置数据库清除策略来定期删除这些记录，以确保数据库的性能水平能够满足性能要求。</span><span class="sxs-lookup"><span data-stu-id="dbf39-126">You should configure a database purge policy to delete these records periodically to ensure that the performance of the database is at the level that satisfy your performance requirements.</span></span>|  
|<span data-ttu-id="dbf39-127">instanceEncodingOption</span><span class="sxs-lookup"><span data-stu-id="dbf39-127">instanceEncodingOption</span></span>|<span data-ttu-id="dbf39-128">一个可选值，指定在将实例状态信息保存到持久性存储区之前，是否使用 GZip 算法压缩此信息。</span><span class="sxs-lookup"><span data-stu-id="dbf39-128">An optional value that specifies  whether the instance state information is compressed using the GZip algorithm before the information is saved in the persistence store..</span></span> <span data-ttu-id="dbf39-129">此值的类型为 <xref:System.Activities.DurableInstancing.InstanceEncodingOption>。</span><span class="sxs-lookup"><span data-stu-id="dbf39-129">This value is of type <xref:System.Activities.DurableInstancing.InstanceEncodingOption>.</span></span> <span data-ttu-id="dbf39-130">此属性的可能值为 <xref:System.Activities.DurableInstancing.InstanceEncodingOption.None> ，指定无压缩，并指定对 <xref:System.Activities.DurableInstancing.InstanceEncodingOption.GZip> 实例数据进行压缩并使用 gzip 算法。</span><span class="sxs-lookup"><span data-stu-id="dbf39-130">Possible values for this property are <xref:System.Activities.DurableInstancing.InstanceEncodingOption.None>, which specifies no compression, and <xref:System.Activities.DurableInstancing.InstanceEncodingOption.GZip>, which specifies that instance data is compressed and uses the gzip algorithm.</span></span>|  
|<span data-ttu-id="dbf39-131">instanceLockedExceptionAction</span><span class="sxs-lookup"><span data-stu-id="dbf39-131">instanceLockedExceptionAction</span></span>|<span data-ttu-id="dbf39-132">一个值，指定为响应在宿主尝试锁定当前已由另一宿主锁定的实例时引发的异常而发生的操作。</span><span class="sxs-lookup"><span data-stu-id="dbf39-132">A value that specifies the action that occurs in response to an exception that is thrown when the host tries to lock an instance because the instance is currently locked by another host.</span></span> <span data-ttu-id="dbf39-133">此值的类型为 <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>。</span><span class="sxs-lookup"><span data-stu-id="dbf39-133">This value is of type <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>.</span></span><br /><br /> <span data-ttu-id="dbf39-134">此字段的可选选项有：“无”、“基本重试”和“积极重试”。</span><span class="sxs-lookup"><span data-stu-id="dbf39-134">The options allowed for this field are: None, Basic Retry, and Aggressive Retry.</span></span> <span data-ttu-id="dbf39-135">默认值为 None。</span><span class="sxs-lookup"><span data-stu-id="dbf39-135">The default value is None.</span></span> <span data-ttu-id="dbf39-136">下面逐一说明上述三个选项：</span><span class="sxs-lookup"><span data-stu-id="dbf39-136">The following list provides you with the descriptions for these three options:</span></span><br /><br /> <span data-ttu-id="dbf39-137">-   无。</span><span class="sxs-lookup"><span data-stu-id="dbf39-137">-   None.</span></span> <span data-ttu-id="dbf39-138">服务主机不会尝试锁定实例，并将 <xref:System.Runtime.DurableInstancing.InstanceLockedException> 传递给调用方。</span><span class="sxs-lookup"><span data-stu-id="dbf39-138">The service host does not attempt to lock the instance and passes the <xref:System.Runtime.DurableInstancing.InstanceLockedException> to the caller.</span></span><br /><span data-ttu-id="dbf39-139">-基本重试。</span><span class="sxs-lookup"><span data-stu-id="dbf39-139">-   Basic Retry.</span></span> <span data-ttu-id="dbf39-140">服务主机将使用线性重试间隔重新尝试锁定实例，并在序列结尾将异常传递给调用方。</span><span class="sxs-lookup"><span data-stu-id="dbf39-140">The service host reattempts to lock the instance with a linear retry interval and passes the exception to the caller at the end of the sequence.</span></span><br /><span data-ttu-id="dbf39-141">-积极重试。</span><span class="sxs-lookup"><span data-stu-id="dbf39-141">-   Aggressive Retry.</span></span> <span data-ttu-id="dbf39-142">服务主机将使用按指数增长的延迟时间重新尝试锁定实例，并在序列结尾将 <xref:System.Runtime.DurableInstancing.InstanceLockedException> 传递给调用方。</span><span class="sxs-lookup"><span data-stu-id="dbf39-142">The service host reattempts to lock the instance with an exponentially increasing delay and passes the <xref:System.Runtime.DurableInstancing.InstanceLockedException> to the caller at the end of the sequence.</span></span>|  
|<span data-ttu-id="dbf39-143">runnableInstancesDetectionPeriod</span><span class="sxs-lookup"><span data-stu-id="dbf39-143">runnableInstancesDetectionPeriod</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="dbf39-144">子元素</span><span class="sxs-lookup"><span data-stu-id="dbf39-144">Child Elements</span></span>  
 <span data-ttu-id="dbf39-145">无。</span><span class="sxs-lookup"><span data-stu-id="dbf39-145">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dbf39-146">父元素</span><span class="sxs-lookup"><span data-stu-id="dbf39-146">Parent Elements</span></span>  
  
|<span data-ttu-id="dbf39-147">元素</span><span class="sxs-lookup"><span data-stu-id="dbf39-147">Element</span></span>|<span data-ttu-id="dbf39-148">描述</span><span class="sxs-lookup"><span data-stu-id="dbf39-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dbf39-149">\<behavior>个\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="dbf39-149">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="dbf39-150">指定行为元素。</span><span class="sxs-lookup"><span data-stu-id="dbf39-150">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dbf39-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dbf39-151">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>
- <xref:System.ServiceModel.Activities.Configuration.SqlWorkflowInstanceStoreElement>
- <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>
- [<span data-ttu-id="dbf39-152">SQL 工作流实例存储</span><span class="sxs-lookup"><span data-stu-id="dbf39-152">SQL Workflow Instance Store</span></span>](../../../windows-workflow-foundation/sql-workflow-instance-store.md)

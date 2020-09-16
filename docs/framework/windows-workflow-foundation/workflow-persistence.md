---
title: 工作流持久性
description: .NET Framework 4.6.1 包含 SqlWorkflowInstanceStore 类，这允许将工作流数据和元数据保存到 SQL Server 数据库。
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], persistence
ms.assetid: 39e69d1f-b771-4c16-9e18-696fa43b65b2
ms.openlocfilehash: c609ec5e67ce3bb0605f543806085f893acba37c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557523"
---
# <a name="workflow-persistence"></a><span data-ttu-id="dfd69-103">工作流持久性</span><span class="sxs-lookup"><span data-stu-id="dfd69-103">Workflow Persistence</span></span>
<span data-ttu-id="dfd69-104">工作流持久性是指独立于进程或计算机信息持续捕获工作流实例的状态。</span><span class="sxs-lookup"><span data-stu-id="dfd69-104">Workflow persistence is the durable capture of a workflow instance's state, independent of process or computer information.</span></span> <span data-ttu-id="dfd69-105">其目的在于：在发生系统故障时为工作流实例提供一个已知恢复点，通过卸载当前未主动执行工作的工作流实例来节省内存，或者将工作流实例状态从服务器场中的一个节点移至另一个节点。</span><span class="sxs-lookup"><span data-stu-id="dfd69-105">This is done to provide a well-known point of recovery for the workflow instance in the event of system failure, or to preserve memory by unloading workflow instances that are not actively doing work, or to move the state of the workflow instance from one node to another node in a server farm.</span></span>  
  
 <span data-ttu-id="dfd69-106">持久性支持进程灵活性、可扩展性、故障恢复以及更有效地管理内存的功能。</span><span class="sxs-lookup"><span data-stu-id="dfd69-106">Persistence enables process agility, scalability, recovery in the face of failure, and the ability to manage memory more efficiently.</span></span> <span data-ttu-id="dfd69-107">持久性进程包括标识持久点、收集要保存的数据以及将数据实际存储最终委托给持久性提供程序。</span><span class="sxs-lookup"><span data-stu-id="dfd69-107">The persistence process includes the identification of a persistence point, the gathering of the data to be saved, and finally the delegation of the actual storage of the data to a persistence provider.</span></span>  
  
 <span data-ttu-id="dfd69-108">若要为工作流启用持久性，需要将实例存储与 **WorkflowApplication** 或 **WorkflowServiceHost** 相关联，如 [如何：为工作流和工作流服务启用持久性](how-to-enable-persistence-for-workflows-and-workflow-services.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="dfd69-108">To enable persistence for a workflow, you need to associate an instance store with the **WorkflowApplication** or **WorkflowServiceHost** as mentioned in [How to: Enable Persistence for Workflows and Workflow Services](how-to-enable-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="dfd69-109">**WorkflowApplication**和**WorkflowServiceHost**使用与之关联的实例存储区来启用将工作流实例保存到持久性存储区中，并基于存储在持久性存储区中的工作流实例数据将工作流实例加载到内存中。</span><span class="sxs-lookup"><span data-stu-id="dfd69-109">The **WorkflowApplication** and **WorkflowServiceHost** use the instance store associated with them to enable persisting workflow instances into a persistence store and loading workflow instances into memory based on the workflow instance data stored in the persistence store.</span></span>  
  
 <span data-ttu-id="dfd69-110">[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]附带了**SqlWorkflowInstanceStore**类，这允许将有关工作流实例的数据和元数据保存到 SQL Server 2005 或 SQL Server 2008 数据库。</span><span class="sxs-lookup"><span data-stu-id="dfd69-110">The [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] ships with the **SqlWorkflowInstanceStore** class, which allows persistence of data and metadata about workflow instances into a SQL Server 2005 or SQL Server 2008 database.</span></span> <span data-ttu-id="dfd69-111">有关更多详细信息，请参阅 [SQL 工作流实例存储](sql-workflow-instance-store.md) 。</span><span class="sxs-lookup"><span data-stu-id="dfd69-111">See [SQL Workflow Instance Store](sql-workflow-instance-store.md) for more details.</span></span>  
  
 <span data-ttu-id="dfd69-112">若要存储和加载应用程序特定数据以及与工作流实例相关的信息，您可以创建用于扩展 <xref:System.Activities.Persistence.PersistenceParticipant> 类的持久性参与者。</span><span class="sxs-lookup"><span data-stu-id="dfd69-112">To store and load your application-specific data along with the workflow instance-related information, you can create persistence participants that extend the <xref:System.Activities.Persistence.PersistenceParticipant> class.</span></span> <span data-ttu-id="dfd69-113">持久性参与者参与持久性进程的目的是：将可序列化的自定义数据保存到持久性存储中，将实例存储中的数据加载到内存中，以及在持久性事务下执行任何其他逻辑。</span><span class="sxs-lookup"><span data-stu-id="dfd69-113">A persistence participant participates in the persistence process to save custom serializable data into the persistence store, to load the data from the instance store into memory, and to perform any additional logic under a persistence transaction.</span></span> <span data-ttu-id="dfd69-114">有关详细信息，请参阅 [持久性参与者](persistence-participants.md)。</span><span class="sxs-lookup"><span data-stu-id="dfd69-114">For more information, see [Persistence Participants](persistence-participants.md).</span></span>  
  
 <span data-ttu-id="dfd69-115">Windows Server App Fabric 大大简化了配置持久性的过程。</span><span class="sxs-lookup"><span data-stu-id="dfd69-115">Windows Server App Fabric simplifies the process of configuring persistence.</span></span> <span data-ttu-id="dfd69-116">有关详细信息，请参阅 [Windows Server App Fabric 的持久性概念](/previous-versions/appfabric/ee677272(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="dfd69-116">For more information, see [Persistence Concepts with Windows Server App Fabric](/previous-versions/appfabric/ee677272(v=azure.10))</span></span>  
  
## <a name="implicit-persistence-points"></a><span data-ttu-id="dfd69-117">隐式持久点</span><span class="sxs-lookup"><span data-stu-id="dfd69-117">Implicit Persistence Points</span></span>  
 <span data-ttu-id="dfd69-118">以下列表包含当实例存储与工作流关联时持久化工作流所依据的条件的示例。</span><span class="sxs-lookup"><span data-stu-id="dfd69-118">The following list contains examples of the conditions upon which a workflow is persisted when an instance store is associated with a workflow.</span></span>  
  
- <span data-ttu-id="dfd69-119">当 **TransactionScope** 活动完成或 **TransactedReceiveScope** 活动完成时。</span><span class="sxs-lookup"><span data-stu-id="dfd69-119">When a **TransactionScope** activity completes or a **TransactedReceiveScope** activity completes.</span></span>  
  
- <span data-ttu-id="dfd69-120">当工作流实例处于空闲状态，并且在工作流主机上设置 **WorkflowIdleBehavior** 时。</span><span class="sxs-lookup"><span data-stu-id="dfd69-120">When a workflow instance becomes idle and the **WorkflowIdleBehavior** is set on workflow host.</span></span> <span data-ttu-id="dfd69-121">例如，在使用消息传递活动或 **延迟** 活动时，会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="dfd69-121">This occurs, for example, when you use messaging activities or a **Delay** activity.</span></span>  
  
- <span data-ttu-id="dfd69-122">WorkflowApplication 处于空闲状态，并且应用程序的 **PersistableIdle** 属性设置为 **PersistableIdleAction**。</span><span class="sxs-lookup"><span data-stu-id="dfd69-122">When a WorkflowApplication becomes idle and the **PersistableIdle** property of the application is set to **PersistableIdleAction.Persist**.</span></span>  
  
- <span data-ttu-id="dfd69-123">当指示主机应用程序保存或卸载工作流实例时。</span><span class="sxs-lookup"><span data-stu-id="dfd69-123">When a host application is instructed to persist or unload a workflow instance.</span></span>  
  
- <span data-ttu-id="dfd69-124">当中止工作流实例或工作流实例结束时。</span><span class="sxs-lookup"><span data-stu-id="dfd69-124">When a workflow instance is terminated or finishes.</span></span>  
  
- <span data-ttu-id="dfd69-125">当执行 **持久** 活动时。</span><span class="sxs-lookup"><span data-stu-id="dfd69-125">When a **Persist** activity executes.</span></span>  
  
- <span data-ttu-id="dfd69-126">当使用 Windows Workflow Foundation 的早期版本开发的工作流实例在可互操作执行过程中遇到持久点时。</span><span class="sxs-lookup"><span data-stu-id="dfd69-126">When an instance of a workflow developed using a previous version of Windows Workflow Foundation encounters a persistence point during interoperable execution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dfd69-127">本节内容</span><span class="sxs-lookup"><span data-stu-id="dfd69-127">In This Section</span></span>  
  
- [<span data-ttu-id="dfd69-128">SQL 工作流实例存储</span><span class="sxs-lookup"><span data-stu-id="dfd69-128">SQL Workflow Instance Store</span></span>](sql-workflow-instance-store.md)  
  
- [<span data-ttu-id="dfd69-129">实例存储区</span><span class="sxs-lookup"><span data-stu-id="dfd69-129">Instance Stores</span></span>](instance-stores.md)  
  
- [<span data-ttu-id="dfd69-130">持久性参与者</span><span class="sxs-lookup"><span data-stu-id="dfd69-130">Persistence Participants</span></span>](persistence-participants.md)  
  
- [<span data-ttu-id="dfd69-131">持久性最佳做法</span><span class="sxs-lookup"><span data-stu-id="dfd69-131">Persistence Best Practices</span></span>](persistence-best-practices.md)  
  
- [<span data-ttu-id="dfd69-132">非持久工作流实例</span><span class="sxs-lookup"><span data-stu-id="dfd69-132">Non-Persisted Workflow Instances</span></span>](non-persisted-workflow-instances.md)  
  
- [<span data-ttu-id="dfd69-133">暂停和继续工作流</span><span class="sxs-lookup"><span data-stu-id="dfd69-133">Pausing and Resuming a Workflow</span></span>](pausing-and-resuming-a-workflow.md)

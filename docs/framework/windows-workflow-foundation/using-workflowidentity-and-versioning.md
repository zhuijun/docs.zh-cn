---
title: 使用 WorkflowIdentity 和版本控制
ms.date: 03/30/2017
ms.assetid: b8451735-8046-478f-912b-40870a6c0c3a
ms.openlocfilehash: 1d31739c135dbb518f05c40ba802c782b6817bff
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855629"
---
# <a name="using-workflowidentity-and-versioning"></a><span data-ttu-id="04bad-102">使用 WorkflowIdentity 和版本控制</span><span class="sxs-lookup"><span data-stu-id="04bad-102">Using WorkflowIdentity and Versioning</span></span>

<span data-ttu-id="04bad-103"><xref:System.Activities.WorkflowIdentity> 为工作流应用程序开发人员提供了一种将名称和 <xref:System.Version> 与工作流定义关联的方法，这种方法还可用于将此信息与持久化工作流实例相关联。</span><span class="sxs-lookup"><span data-stu-id="04bad-103"><xref:System.Activities.WorkflowIdentity> provides a way for workflow application developers to associate a name and a <xref:System.Version> with a workflow definition, and for this information to be associated with a persisted workflow instance.</span></span> <span data-ttu-id="04bad-104">工作流应用程序开发人员可以使用这些标识信息，为一些情景（如并行执行一个工作流定义的多个版本）提供支持，并为其他功能（如动态更新）提供基础。</span><span class="sxs-lookup"><span data-stu-id="04bad-104">This identity information can be used by workflow application developers to enable scenarios such as side-by-side execution of multiple versions of a workflow definition, and provides the cornerstone for other functionality such as dynamic update.</span></span> <span data-ttu-id="04bad-105">此主题概述了如何将 <xref:System.Activities.WorkflowIdentity> 与 <xref:System.Activities.WorkflowApplication> 承载一起使用。</span><span class="sxs-lookup"><span data-stu-id="04bad-105">This topic provides as overview of using <xref:System.Activities.WorkflowIdentity> with <xref:System.Activities.WorkflowApplication> hosting.</span></span> <span data-ttu-id="04bad-106">有关工作流服务中工作流定义的并行执行的信息，请参阅[WorkflowServiceHost 中的并行版本控制](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md)。</span><span class="sxs-lookup"><span data-stu-id="04bad-106">For information on side-by-side execution of workflow definitions in a workflow service, see [Side by Side Versioning in WorkflowServiceHost](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).</span></span> <span data-ttu-id="04bad-107">有关动态更新的信息，请参阅[动态更新](dynamic-update.md)。</span><span class="sxs-lookup"><span data-stu-id="04bad-107">For information on dynamic update, see [Dynamic Update](dynamic-update.md).</span></span>

## <a name="in-this-topic"></a><span data-ttu-id="04bad-108">本主题内容</span><span class="sxs-lookup"><span data-stu-id="04bad-108">In this topic</span></span>

- [<span data-ttu-id="04bad-109">使用 WorkflowIdentity</span><span class="sxs-lookup"><span data-stu-id="04bad-109">Using WorkflowIdentity</span></span>](using-workflowidentity-and-versioning.md#UsingWorkflowIdentity)

  - [<span data-ttu-id="04bad-110">使用 WorkflowIdentity 并行执行</span><span class="sxs-lookup"><span data-stu-id="04bad-110">Side-by-side Execution using WorkflowIdentity</span></span>](using-workflowidentity-and-versioning.md#SxS)

- [<span data-ttu-id="04bad-111">升级 .NET Framework 4 持久性数据库以支持工作流版本控制</span><span class="sxs-lookup"><span data-stu-id="04bad-111">Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning</span></span>](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)

  - [<span data-ttu-id="04bad-112">升级数据库架构</span><span class="sxs-lookup"><span data-stu-id="04bad-112">To upgrade the database schema</span></span>](using-workflowidentity-and-versioning.md#ToUpgrade)

## <a name="using-workflowidentity"></a><a name="UsingWorkflowIdentity"></a><span data-ttu-id="04bad-113">使用 WorkflowIdentity</span><span class="sxs-lookup"><span data-stu-id="04bad-113">Using WorkflowIdentity</span></span>

<span data-ttu-id="04bad-114">若要使用 <xref:System.Activities.WorkflowIdentity>，请创建并配置一个实例，并将它与一个 <xref:System.Activities.WorkflowApplication> 实例关联。</span><span class="sxs-lookup"><span data-stu-id="04bad-114">To use <xref:System.Activities.WorkflowIdentity>, create an instance, configure it, and associate it with a <xref:System.Activities.WorkflowApplication> instance.</span></span> <span data-ttu-id="04bad-115">一个 <xref:System.Activities.WorkflowIdentity> 实例包含三条标识信息。</span><span class="sxs-lookup"><span data-stu-id="04bad-115">A <xref:System.Activities.WorkflowIdentity> instance contains three identifying pieces of information.</span></span> <span data-ttu-id="04bad-116"><xref:System.Activities.WorkflowIdentity.Name%2A> 和 <xref:System.Activities.WorkflowIdentity.Version%2A> 包含一个名称和一个 <xref:System.Version>，并且是必需的；而 <xref:System.Activities.WorkflowIdentity.Package%2A> 则是可选的，可用于指定包含如程序集名称或其他所需信息的附加字符串。</span><span class="sxs-lookup"><span data-stu-id="04bad-116"><xref:System.Activities.WorkflowIdentity.Name%2A> and <xref:System.Activities.WorkflowIdentity.Version%2A> contain a name and a <xref:System.Version> and are required, and <xref:System.Activities.WorkflowIdentity.Package%2A> is optional and can be used to specify an additional string containing information such as assembly name or other desired information.</span></span> <span data-ttu-id="04bad-117">如果 <xref:System.Activities.WorkflowIdentity> 的三个属性中有任一属性不同于其他 <xref:System.Activities.WorkflowIdentity>，则它是唯一的。</span><span class="sxs-lookup"><span data-stu-id="04bad-117">A <xref:System.Activities.WorkflowIdentity> is unique if any of its three properties are different from another <xref:System.Activities.WorkflowIdentity>.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="04bad-118"><xref:System.Activities.WorkflowIdentity> 不应包含任何个人身份信息 (PII)。</span><span class="sxs-lookup"><span data-stu-id="04bad-118">A <xref:System.Activities.WorkflowIdentity> should not contain any personally identifiable information (PII).</span></span> <span data-ttu-id="04bad-119">在几个不同活动生命周期点，运行时将向任何已配置的跟踪服务发出有关用于创建实例的 <xref:System.Activities.WorkflowIdentity> 的信息。</span><span class="sxs-lookup"><span data-stu-id="04bad-119">Information about the <xref:System.Activities.WorkflowIdentity> used to create an instance is emitted to any configured tracking services at several different points of the activity life-cycle by the runtime.</span></span> <span data-ttu-id="04bad-120">WF 跟踪没有任何隐藏 PII（敏感用户信息）的机制。</span><span class="sxs-lookup"><span data-stu-id="04bad-120">WF Tracking does not have any mechanism to hide PII (sensitive user data).</span></span> <span data-ttu-id="04bad-121">因此，<xref:System.Activities.WorkflowIdentity> 实例不应该包含任何 PII 数据，因为运行时将在跟踪记录中发出这些数据，任何有权查看跟踪记录的人都能够看到这些数据。</span><span class="sxs-lookup"><span data-stu-id="04bad-121">Therefore, a <xref:System.Activities.WorkflowIdentity> instance should not contain any PII data as it will be emitted by the runtime in tracking records and may be visible to anyone with access to view the tracking records.</span></span>

<span data-ttu-id="04bad-122">在以下示例中，创建了 <xref:System.Activities.WorkflowIdentity> 并将它与使用 `MortgageWorkflow` 工作流定义创建的工作流实例相关联。</span><span class="sxs-lookup"><span data-stu-id="04bad-122">In the following example, a <xref:System.Activities.WorkflowIdentity> is created and associated with an instance of a workflow created using a `MortgageWorkflow` workflow definition.</span></span>

```csharp
WorkflowIdentity identityV1 = new WorkflowIdentity
{
    Name = "MortgageWorkflow v1",
    Version = new Version(1, 0, 0, 0)
};

WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Run the workflow.
wfApp.Run();
```

<span data-ttu-id="04bad-123">重新加载和恢复工作流时，必须使用一个配置为与持久化工作流实例的 <xref:System.Activities.WorkflowIdentity> 匹配的 <xref:System.Activities.WorkflowIdentity>。</span><span class="sxs-lookup"><span data-stu-id="04bad-123">When reloading and resuming a workflow, a <xref:System.Activities.WorkflowIdentity> that is configured to match the <xref:System.Activities.WorkflowIdentity> of the persisted workflow instance must be used.</span></span>

```csharp
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Load the workflow.
wfApp.Load(instanceId);

// Resume the workflow...
```

<span data-ttu-id="04bad-124">如果重新加载工作流实例时使用的 <xref:System.Activities.WorkflowIdentity> 与持久化 <xref:System.Activities.WorkflowIdentity> 不匹配，则将引发 <xref:System.Activities.VersionMismatchException>。</span><span class="sxs-lookup"><span data-stu-id="04bad-124">If the <xref:System.Activities.WorkflowIdentity> used when reloading the workflow instance does not match the persisted <xref:System.Activities.WorkflowIdentity>, a <xref:System.Activities.VersionMismatchException> is thrown.</span></span> <span data-ttu-id="04bad-125">在以下示例中，尝试加载在前一个示例中持久化的 `MortgageWorkflow` 实例。</span><span class="sxs-lookup"><span data-stu-id="04bad-125">In the following example a load attempt is made on the `MortgageWorkflow` instance that was persisted in the previous example.</span></span> <span data-ttu-id="04bad-126">执行此加载尝试时，使用了一个为更新版本抵押工作流配置的 <xref:System.Activities.WorkflowIdentity>，该工作流与持久保存实例不匹配。</span><span class="sxs-lookup"><span data-stu-id="04bad-126">This load attempt is made using a <xref:System.Activities.WorkflowIdentity> configured for a newer version of the mortgage workflow that does not match the persisted instance.</span></span>

```csharp
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow_v2(), identityV2);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Attempt to load the workflow instance.
wfApp.Load(instanceId);

// Resume the workflow...
```

<span data-ttu-id="04bad-127">执行前一段代码时，引发了以下 <xref:System.Activities.VersionMismatchException>。</span><span class="sxs-lookup"><span data-stu-id="04bad-127">When the previous code is executed, the following <xref:System.Activities.VersionMismatchException> is thrown.</span></span>

```output
The WorkflowIdentity ('MortgageWorkflow v1; Version=1.0.0.0') of the loaded instance does not match the WorkflowIdentity ('MortgageWorkflow v2; Version=2.0.0.0') of the provided workflow definition. The instance can be loaded using a different definition, or updated using Dynamic Update.
```

### <a name="side-by-side-execution-using-workflowidentity"></a><a name="SxS"></a><span data-ttu-id="04bad-128">使用 WorkflowIdentity 的并行执行</span><span class="sxs-lookup"><span data-stu-id="04bad-128">Side-by-side Execution using WorkflowIdentity</span></span>

<span data-ttu-id="04bad-129">可使用 <xref:System.Activities.WorkflowIdentity> 帮助并行执行一个工作流的多个版本。</span><span class="sxs-lookup"><span data-stu-id="04bad-129"><xref:System.Activities.WorkflowIdentity> can be used to facilitate the execution of multiple versions of a workflow side-by-side.</span></span> <span data-ttu-id="04bad-130">一种常见的情形是更改长期运行的工作流的业务需求。</span><span class="sxs-lookup"><span data-stu-id="04bad-130">One common scenario is changing business requirements on a long-running workflow.</span></span> <span data-ttu-id="04bad-131">部署更新版本时，可能正在运行一个工作流的多个实例。</span><span class="sxs-lookup"><span data-stu-id="04bad-131">Many instances of a workflow could be running when an updated version is deployed.</span></span> <span data-ttu-id="04bad-132">可对主机应用程序进行配置，使之在启动新实例时使用更新过的工作流定义，并且该主机应用程序应负责在恢复实例时提供正确的工作流定义。</span><span class="sxs-lookup"><span data-stu-id="04bad-132">The host application can be configured to use the updated workflow definition when starting new instances, and it is the responsibility of the host application to provide the correct workflow definition when resuming instances.</span></span> <span data-ttu-id="04bad-133"><xref:System.Activities.WorkflowIdentity> 可用于在恢复工作流实例时确定和提供匹配的工作流定义。</span><span class="sxs-lookup"><span data-stu-id="04bad-133"><xref:System.Activities.WorkflowIdentity> can be used to identify and supply the matching workflow definition when resuming workflow instances.</span></span>

<span data-ttu-id="04bad-134">为检索持久化工作流实例的 <xref:System.Activities.WorkflowIdentity>，将使用 <xref:System.Activities.WorkflowApplication.GetInstance%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="04bad-134">To retrieve the <xref:System.Activities.WorkflowIdentity> of a persisted workflow instance, the <xref:System.Activities.WorkflowApplication.GetInstance%2A> method is used.</span></span> <span data-ttu-id="04bad-135"><xref:System.Activities.WorkflowApplication.GetInstance%2A> 方法使用持久化工作流实例的 <xref:System.Activities.WorkflowApplication.Id%2A> 和包含该持久化实例的 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>，并返回一个 <xref:System.Activities.WorkflowApplicationInstance>。</span><span class="sxs-lookup"><span data-stu-id="04bad-135">The <xref:System.Activities.WorkflowApplication.GetInstance%2A> method takes the <xref:System.Activities.WorkflowApplication.Id%2A> of the persisted workflow instance and the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> that contains the persisted instance and returns a <xref:System.Activities.WorkflowApplicationInstance>.</span></span> <span data-ttu-id="04bad-136"><xref:System.Activities.WorkflowApplicationInstance> 包含有关持久化工作流实例的信息，包括其关联的 <xref:System.Activities.WorkflowIdentity>。</span><span class="sxs-lookup"><span data-stu-id="04bad-136">A <xref:System.Activities.WorkflowApplicationInstance> contains information about a persisted workflow instance, including its associated <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="04bad-137">主机可使用此关联 <xref:System.Activities.WorkflowIdentity> 在加载和恢复工作流实例时提供正确的工作流定义。</span><span class="sxs-lookup"><span data-stu-id="04bad-137">This associated <xref:System.Activities.WorkflowIdentity> can be used by the host to supply the correct workflow definition when loading and resuming the workflow instance.</span></span>

> [!NOTE]
> <span data-ttu-id="04bad-138">空 <xref:System.Activities.WorkflowIdentity> 是有效的，主机可以用它将没有关联 <xref:System.Activities.WorkflowIdentity> 的持久化实例映射到正确的工作流定义。</span><span class="sxs-lookup"><span data-stu-id="04bad-138">A null <xref:System.Activities.WorkflowIdentity> is valid, and can be used by the host to map instances that were persisted with no associated <xref:System.Activities.WorkflowIdentity> to the proper workflow definition.</span></span> <span data-ttu-id="04bad-139">当最初未使用工作流版本写入工作流应用程序时，或者从 .NET Framework 4 升级应用程序时，可能会出现这种情况。</span><span class="sxs-lookup"><span data-stu-id="04bad-139">This scenario can occur when a workflow application was not initially written with workflow versioning, or when an application is upgraded from .NET Framework 4.</span></span> <span data-ttu-id="04bad-140">有关详细信息，请参阅[升级 .NET Framework 4 持久性数据库以支持工作流版本控制](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)。</span><span class="sxs-lookup"><span data-stu-id="04bad-140">For more information, see [Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).</span></span>

<span data-ttu-id="04bad-141">在下面的示例中 `Dictionary<WorkflowIdentity, Activity>` ，用于将 <xref:System.Activities.WorkflowIdentity> 实例与其匹配的工作流定义关联，并使用 `MortgageWorkflow` 与关联的工作流定义启动工作流 `identityV1` <xref:System.Activities.WorkflowIdentity> 。</span><span class="sxs-lookup"><span data-stu-id="04bad-141">In the following example a `Dictionary<WorkflowIdentity, Activity>` is used to associate <xref:System.Activities.WorkflowIdentity> instances with their matching workflow definitions, and a workflow is started using the `MortgageWorkflow` workflow definition, which is associated with the `identityV1` <xref:System.Activities.WorkflowIdentity>.</span></span>

```csharp
WorkflowIdentity identityV1 = new WorkflowIdentity
{
    Name = "MortgageWorkflow v1",
    Version = new Version(1, 0, 0, 0)
};

WorkflowIdentity identityV2 = new WorkflowIdentity
{
    Name = "MortgageWorkflow v2",
    Version = new Version(2, 0, 0, 0)
};

Dictionary<WorkflowIdentity, Activity> WorkflowVersionMap = new Dictionary<WorkflowIdentity, Activity>();
WorkflowVersionMap.Add(identityV1, new MortgageWorkflow());
WorkflowVersionMap.Add(identityV2, new MortgageWorkflow_v2());

WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Run the workflow.
wfApp.Run();
```

<span data-ttu-id="04bad-142">在以下示例中，通过调用 <xref:System.Activities.WorkflowApplication.GetInstance%2A> 来检索有关前一个示例中持久化工作流实例的信息，并使用了持久化 <xref:System.Activities.WorkflowIdentity> 信息来检索匹配的工作流定义。</span><span class="sxs-lookup"><span data-stu-id="04bad-142">In the following example, information about the persisted workflow instance from the previous example is retrieved by calling <xref:System.Activities.WorkflowApplication.GetInstance%2A>, and the persisted <xref:System.Activities.WorkflowIdentity> information is used to retrieve the matching workflow definition.</span></span> <span data-ttu-id="04bad-143">将使用这些信息来配置 <xref:System.Activities.WorkflowApplication>，然后将加载工作流。</span><span class="sxs-lookup"><span data-stu-id="04bad-143">This information is used to configure the <xref:System.Activities.WorkflowApplication>, and then the workflow is loaded.</span></span> <span data-ttu-id="04bad-144">请注意，因为使用了 <xref:System.Activities.WorkflowApplication.Load%2A> 重载（它使用 <xref:System.Activities.WorkflowApplicationInstance>），<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 将使用在 <xref:System.Activities.WorkflowApplicationInstance> 上配置的 <xref:System.Activities.WorkflowApplication>，因此无需配置其 <xref:System.Activities.WorkflowApplication.InstanceStore%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="04bad-144">Note that because the <xref:System.Activities.WorkflowApplication.Load%2A> overload that takes the <xref:System.Activities.WorkflowApplicationInstance> is used, the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> that was configured on the <xref:System.Activities.WorkflowApplicationInstance> is used by the <xref:System.Activities.WorkflowApplication> and therefore its <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property does not need to be configured.</span></span>

> [!NOTE]
> <span data-ttu-id="04bad-145">如果设置 <xref:System.Activities.WorkflowApplication.InstanceStore%2A> 属性，则必须用 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 所使用的那一个 <xref:System.Activities.WorkflowApplicationInstance> 实例来设置，否则将引发 <xref:System.ArgumentException> 异常，并显示以下消息：`The instance is configured with a different InstanceStore than this WorkflowApplication.`。</span><span class="sxs-lookup"><span data-stu-id="04bad-145">If the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property is set, it must be set with the same <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> instance used by the <xref:System.Activities.WorkflowApplicationInstance> or else an <xref:System.ArgumentException> will be thrown with the following message: `The instance is configured with a different InstanceStore than this WorkflowApplication.`.</span></span>

```csharp
// Get the WorkflowApplicationInstance of the desired workflow from the specified
// SqlWorkflowInstanceStore.
WorkflowApplicationInstance instance = WorkflowApplication.GetInstance(instanceId, store);

// Use the persisted WorkflowIdentity to retrieve the correct workflow
// definition from the dictionary.
Activity definition = WorkflowVersionMap[instance.DefinitionIdentity];

WorkflowApplication wfApp = new WorkflowApplication(definition, instance.DefinitionIdentity);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Load the persisted workflow instance.
wfApp.Load(instance);

// Resume the workflow...
```

## <a name="upgrading-net-framework-4-persistence-databases-to-support-workflow-versioning"></a><a name="UpdatingWF4PersistenceDatabases"></a><span data-ttu-id="04bad-146">升级 .NET Framework 4 持久性数据库以支持工作流版本控制</span><span class="sxs-lookup"><span data-stu-id="04bad-146">Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning</span></span>

<span data-ttu-id="04bad-147">提供 Sqlworkflowinstancestoreschemaupgrade.sql 数据库脚本来升级使用 .NET Framework 4 数据库脚本创建的持久性数据库。</span><span class="sxs-lookup"><span data-stu-id="04bad-147">A SqlWorkflowInstanceStoreSchemaUpgrade.sql database script is provided to upgrade persistence databases created using the .NET Framework 4 database scripts.</span></span> <span data-ttu-id="04bad-148">此脚本更新数据库以支持 .NET Framework 4.5 中引入的新版本控制功能。</span><span class="sxs-lookup"><span data-stu-id="04bad-148">This script updates the databases to support the new versioning capabilities introduced in .NET Framework 4.5.</span></span> <span data-ttu-id="04bad-149">数据库中任何持久化工作流实例都将获得默认的版本控制值，然后就可以参与并行执行和动态更新。</span><span class="sxs-lookup"><span data-stu-id="04bad-149">Any persisted workflow instances in the databases are given default versioning values, and can then participate in side-by-side execution and dynamic update.</span></span>

<span data-ttu-id="04bad-150">如果 .NET Framework 4.5 工作流应用程序尝试在未使用提供的脚本进行升级的暂留数据库上使用新版本控制功能的任何持久性操作， <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> 将引发并带有类似于以下消息的消息。</span><span class="sxs-lookup"><span data-stu-id="04bad-150">If a .NET Framework 4.5 workflow application attempts any persistence operations that use the new versioning features on a persistence database which has not been upgraded using the provided script, an <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> is thrown with a message similar to the following message.</span></span>

```output
The SqlWorkflowInstanceStore has a database version of '4.0.0.0'. InstancePersistenceCommand 'System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand' cannot be run against this database version.  Please upgrade the database to '4.5.0.0'.
```

### <a name="to-upgrade-the-database-schema"></a><a name="ToUpgrade"></a><span data-ttu-id="04bad-151">升级数据库架构</span><span class="sxs-lookup"><span data-stu-id="04bad-151">To upgrade the database schema</span></span>

1. <span data-ttu-id="04bad-152">打开 SQL Server Management Studio 并连接到持久性数据库服务器，例如 **.\SQLEXPRESS**。</span><span class="sxs-lookup"><span data-stu-id="04bad-152">Open SQL Server Management Studio and connect to the persistence database server, for example **.\SQLEXPRESS**.</span></span>

2. <span data-ttu-id="04bad-153">从 "**文件**" 菜单中**选择 "** **打开**"。</span><span class="sxs-lookup"><span data-stu-id="04bad-153">Choose **Open**, **File** from the **File** menu.</span></span> <span data-ttu-id="04bad-154">浏览到以下文件夹：`C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`</span><span class="sxs-lookup"><span data-stu-id="04bad-154">Browse to the following folder: `C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`</span></span>

3. <span data-ttu-id="04bad-155">选择**sqlworkflowinstancestoreschemaupgrade.sql**并单击 "**打开**"。</span><span class="sxs-lookup"><span data-stu-id="04bad-155">Select **SqlWorkflowInstanceStoreSchemaUpgrade.sql** and click **Open**.</span></span>

4. <span data-ttu-id="04bad-156">在 "**可用数据库**" 下拉中选择持久性数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="04bad-156">Select the name of the persistence database in the **Available Databases** drop-down.</span></span>

5. <span data-ttu-id="04bad-157">从 "**查询**" 菜单中选择 "**执行**"。</span><span class="sxs-lookup"><span data-stu-id="04bad-157">Choose **Execute** from the **Query** menu.</span></span>

<span data-ttu-id="04bad-158">查询完成时，数据库架构将升级，您可以根据需要查看分配给持久化工作流实例的默认工作流标识。</span><span class="sxs-lookup"><span data-stu-id="04bad-158">When the query completes, the database schema is upgraded, and if desired, you can view the default workflow identity that was assigned to the persisted workflow instances.</span></span> <span data-ttu-id="04bad-159">在**对象资源管理器**的 "**数据库**" 节点中展开持久性数据库，然后展开 "**视图**" 节点。</span><span class="sxs-lookup"><span data-stu-id="04bad-159">Expand your persistence database in the **Databases** node of the **Object Explorer**, and then expand the **Views** node.</span></span> <span data-ttu-id="04bad-160">右键单击 " **DurableInstancing** "，然后选择 "**选择前1000行**"。</span><span class="sxs-lookup"><span data-stu-id="04bad-160">Right-click **System.Activities.DurableInstancing.Instances** and choose **Select Top 1000 Rows**.</span></span> <span data-ttu-id="04bad-161">滚动到列的末尾，并注意向视图添加了六个附加列： **IdentityName**、 **IdentityPackage**、 **Build**、**主要**、**次要**和**修订**。</span><span class="sxs-lookup"><span data-stu-id="04bad-161">Scroll to end of the columns and note that there are six additional columns added to the view: **IdentityName**, **IdentityPackage**, **Build**, **Major**, **Minor**, and **Revision**.</span></span> <span data-ttu-id="04bad-162">对于这些字段，任何持久化工作流的值都将为**null** ，表示 NULL 工作流标识。</span><span class="sxs-lookup"><span data-stu-id="04bad-162">Any persisted workflows will have a value of **NULL** for these fields, representing a null workflow identity.</span></span>

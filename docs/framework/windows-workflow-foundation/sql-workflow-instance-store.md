---
title: SQL 工作流实例存储
ms.date: 03/30/2017
ms.assetid: 8cd2f8a5-4bf8-46ea-8909-c7fdb314fabc
ms.openlocfilehash: 38cf83ebb8417009c6aa205aa29cd633d1232f0a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540227"
---
# <a name="sql-workflow-instance-store"></a><span data-ttu-id="aacd0-102">SQL 工作流实例存储</span><span class="sxs-lookup"><span data-stu-id="aacd0-102">SQL Workflow Instance Store</span></span>
<span data-ttu-id="aacd0-103">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 附带的 SQL 工作流实例存储允许工作流在 SQL Server 2005 或 SQL Server 2008 数据库中持久保存有关工作流实例的状态信息。</span><span class="sxs-lookup"><span data-stu-id="aacd0-103">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] ships with the SQL Workflow Instance Store, which allows workflows to persist state information about workflow instances in a SQL Server 2005 or SQL Server 2008 database.</span></span> <span data-ttu-id="aacd0-104">此功能主要以 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 类的形式实现，该类是从持久性框架的抽象 <xref:System.Runtime.DurableInstancing.InstanceStore> 类派生的。</span><span class="sxs-lookup"><span data-stu-id="aacd0-104">This feature is primarily implemented in the form of the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> class, which derives from the abstract <xref:System.Runtime.DurableInstancing.InstanceStore> class of the persistence framework.</span></span> <span data-ttu-id="aacd0-105">SQL 工作流实例存储功能包含一个 SQL 持久性提供程序，该提供程序是持久性 API 的具体实现，宿主将使用此持久性 API 向存储发送持久性命令。</span><span class="sxs-lookup"><span data-stu-id="aacd0-105">The SQL Workflow Instance Store feature constitutes a SQL persistence provider, which is a concrete implementation of the persistence API that a host uses to send persistence commands to the store.</span></span>  
  
 <span data-ttu-id="aacd0-106">SQL 工作流实例存储支持自承载工作流或使用 <xref:System.Activities.WorkflowApplication> 或 <xref:System.ServiceModel.WorkflowServiceHost> 的工作流服务以及 WAS 中承载的使用 <xref:System.ServiceModel.WorkflowServiceHost> 的服务。</span><span class="sxs-lookup"><span data-stu-id="aacd0-106">The SQL Workflow Instance Store supports both self-hosted workflows or workflow services that use <xref:System.Activities.WorkflowApplication> or <xref:System.ServiceModel.WorkflowServiceHost> as well as services hosted in WAS using <xref:System.ServiceModel.WorkflowServiceHost>.</span></span> <span data-ttu-id="aacd0-107">可以使用 SQL 工作流实例存储功能公开的对象模型以编程方式为自承载服务配置该功能。</span><span class="sxs-lookup"><span data-stu-id="aacd0-107">You can configure the SQL Workflow Instance Store feature for self-hosted services programmatically by using the object model exposed by the feature.</span></span> <span data-ttu-id="aacd0-108">可以使用对象模型，也可以使用 XML 配置文件以编程方式为由 <xref:System.ServiceModel.WorkflowServiceHost> 承载的服务配置此功能。</span><span class="sxs-lookup"><span data-stu-id="aacd0-108">You can configure this feature for services hosted by <xref:System.ServiceModel.WorkflowServiceHost> both programmatically by using the object model and also by using an XML configuration file.</span></span>  
  
 <span data-ttu-id="aacd0-109">SQL 工作流实例存储区功能 (**SqlWorkflowInstanceStore** 类) 不实现 <xref:System.ServiceModel.Persistence.PersistenceProviderFactory> ，因此不为持久的非工作流 WCF 服务提供持久性支持。</span><span class="sxs-lookup"><span data-stu-id="aacd0-109">The SQL Workflow Instance Store feature (**SqlWorkflowInstanceStore** class) does not implement <xref:System.ServiceModel.Persistence.PersistenceProviderFactory> and hence does not offer persistence support for durable non-workflow WCF services.</span></span> <span data-ttu-id="aacd0-110">它也不实现 <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService>，因此不提供对 3.x 工作流的持久性支持。</span><span class="sxs-lookup"><span data-stu-id="aacd0-110">It also does not implement <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> and hence does not offer persistence support for 3.x workflows.</span></span> <span data-ttu-id="aacd0-111">该功能仅对 WF 4.0（和更高版本）工作流和工作流服务提供持久性支持。</span><span class="sxs-lookup"><span data-stu-id="aacd0-111">The feature supports persistence for only WF 4.0 (and later) workflows and workflow services.</span></span> <span data-ttu-id="aacd0-112">该功能也不支持除了 SQL Server 2005 和 SQL Server 2008 之外的任何数据库。</span><span class="sxs-lookup"><span data-stu-id="aacd0-112">The feature also does not support any databases other than SQL Server 2005 and SQL Server 2008.</span></span>  
  
 <span data-ttu-id="aacd0-113">本节中的主题介绍 SQL 工作流实例存储的属性和功能，并且提供有关配置该存储的详细信息。</span><span class="sxs-lookup"><span data-stu-id="aacd0-113">The topics in this section describe properties and features of the SQL Workflow Instance Store and provide you with details on configuring the store.</span></span>  
  
 <span data-ttu-id="aacd0-114">Windows Server App Fabric 提供自己的实例存储区和工具以便简化实例存储区的配置和使用。</span><span class="sxs-lookup"><span data-stu-id="aacd0-114">Windows Server App Fabric provides its own instance store and tooling to simplify the configuration and use of the instance store.</span></span> <span data-ttu-id="aacd0-115">有关详细信息，请参阅 [Windows Server App Fabric 实例存储](/previous-versions/appfabric/ff383417(v=azure.10))。</span><span class="sxs-lookup"><span data-stu-id="aacd0-115">For more information, see [Windows Server App Fabric Instance Store](/previous-versions/appfabric/ff383417(v=azure.10)).</span></span> <span data-ttu-id="aacd0-116">有关 App Fabric SQL Server 持久性数据库的详细信息，请参阅 [应用构造 SQL Server 持久性数据库](/previous-versions/appfabric/ee790819(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="aacd0-116">For more information about the App Fabric SQL Server Persistence Database see [App Fabric SQL Server Persistence Database](/previous-versions/appfabric/ee790819(v=azure.10))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aacd0-117">本节内容</span><span class="sxs-lookup"><span data-stu-id="aacd0-117">In This Section</span></span>  
  
- [<span data-ttu-id="aacd0-118">SQL 工作流实例存储的属性</span><span class="sxs-lookup"><span data-stu-id="aacd0-118">Properties of SQL Workflow Instance Store</span></span>](properties-of-sql-workflow-instance-store.md)  
  
- [<span data-ttu-id="aacd0-119">如何：对工作流和工作流服务启用 SQL 持久性</span><span class="sxs-lookup"><span data-stu-id="aacd0-119">How to: Enable SQL Persistence for Workflows and Workflow Services</span></span>](how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)  
  
- [<span data-ttu-id="aacd0-120">实例激活</span><span class="sxs-lookup"><span data-stu-id="aacd0-120">Instance Activation</span></span>](instance-activation.md)  
  
- [<span data-ttu-id="aacd0-121">查询支持</span><span class="sxs-lookup"><span data-stu-id="aacd0-121">Support for Queries</span></span>](support-for-queries.md)  
  
- [<span data-ttu-id="aacd0-122">存储扩展性</span><span class="sxs-lookup"><span data-stu-id="aacd0-122">Store Extensibility</span></span>](store-extensibility.md)  
  
- [<span data-ttu-id="aacd0-123">安全性</span><span class="sxs-lookup"><span data-stu-id="aacd0-123">Security</span></span>](security.md)  
  
- [<span data-ttu-id="aacd0-124">SQL Server 持久性数据库</span><span class="sxs-lookup"><span data-stu-id="aacd0-124">SQL Server Persistence Database</span></span>](sql-server-persistence-database.md)  
  
## <a name="see-also"></a><span data-ttu-id="aacd0-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="aacd0-125">See also</span></span>

- <span data-ttu-id="aacd0-126">[Persistence Samples（持久性示例）](/previous-versions/dotnet/netframework-4.0/dd699769(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="aacd0-126">[Persistence Samples](/previous-versions/dotnet/netframework-4.0/dd699769(v=vs.100))</span></span>

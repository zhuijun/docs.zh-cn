---
title: 使用 LINQ to SQL 的 N 层和远程应用程序
ms.date: 03/30/2017
ms.assetid: 854a1cdd-53cb-45f5-83ca-63962a9b3598
ms.openlocfilehash: 70f6a6ee91761196b62b34f6dde73d11dbe6b39d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200597"
---
# <a name="n-tier-and-remote-applications-with-linq-to-sql"></a><span data-ttu-id="1444c-102">使用 LINQ to SQL 的 N 层和远程应用程序</span><span class="sxs-lookup"><span data-stu-id="1444c-102">N-Tier and Remote Applications with LINQ to SQL</span></span>

<span data-ttu-id="1444c-103">可以创建使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的 n 层或多层应用程序。</span><span class="sxs-lookup"><span data-stu-id="1444c-103">You can create n-tier or multitier applications that use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="1444c-104">通常情况下， [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 数据上下文、实体类和查询构造逻辑位于中间层上，作为数据访问层 (DAL) 。</span><span class="sxs-lookup"><span data-stu-id="1444c-104">Typically, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] data context, entity classes, and query construction logic are located on the middle tier as the data access layer (DAL).</span></span> <span data-ttu-id="1444c-105">业务逻辑和任何非持久性数据都可以在实体的分部类和分部方法中以及数据上下文中完整实现，也可以在单独的类中实现。</span><span class="sxs-lookup"><span data-stu-id="1444c-105">Business logic and any non-persistent data can be implemented completely in partial classes and methods of entities and the data context, or it can be implemented in separate classes.</span></span>

 <span data-ttu-id="1444c-106">客户端或表示层调用中间层的远程接口上的方法，而该层上的 DAL 会执行映射到 <xref:System.Data.Linq.DataContext> 方法的查询或存储过程。</span><span class="sxs-lookup"><span data-stu-id="1444c-106">The client or presentation layer calls methods on the middle-tier's remote interface, and the DAL on that tier will execute queries or stored procedures that are mapped to <xref:System.Data.Linq.DataContext> methods.</span></span> <span data-ttu-id="1444c-107">中间层通常以实体或代理对象的 XML 表示形式向客户端返回数据。</span><span class="sxs-lookup"><span data-stu-id="1444c-107">The middle tier returns the data to clients typically as XML representations of entities or proxy objects.</span></span>

 <span data-ttu-id="1444c-108">在中间层上，实体由数据上下文创建，数据上下文会跟踪实体的状态，并管理从数据库延迟加载实体以及将更改提交给数据库的过程。</span><span class="sxs-lookup"><span data-stu-id="1444c-108">On the middle tier, entities are created by the data context, which tracks their state, and manages deferred loading from and submission of changes to the database.</span></span> <span data-ttu-id="1444c-109">这些实体被“附加”到 `DataContext`。</span><span class="sxs-lookup"><span data-stu-id="1444c-109">These entities are "attached" to the `DataContext`.</span></span> <span data-ttu-id="1444c-110">但是，在实体通过序列化发送到其他层后，这些实体会分离出来，这意味着 `DataContext` 不再跟踪它们的状态。</span><span class="sxs-lookup"><span data-stu-id="1444c-110">However, after the entities are sent to another tier through serialization, they become detached, which means the `DataContext` is no longer tracking their state.</span></span> <span data-ttu-id="1444c-111">必须在将客户端发送回来进行更新的实体重新附加到数据上下文之后，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 才能将更改提交给数据库。</span><span class="sxs-lookup"><span data-stu-id="1444c-111">Entities that the client sends back for updates must be reattached to the data context before [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can submit the changes to the database.</span></span> <span data-ttu-id="1444c-112">如果原始值和/或时间戳是开放式并发检查所必需的，则客户端负责将它们返回给中间层。</span><span class="sxs-lookup"><span data-stu-id="1444c-112">The client is responsible for providing original values and/or timestamps back to the middle tier if those are required for optimistic concurrency checks.</span></span>

 <span data-ttu-id="1444c-113">在 ASP.NET 应用程序中，<xref:System.Web.UI.WebControls.LinqDataSource> 管理这一复杂过程的大部分工作。</span><span class="sxs-lookup"><span data-stu-id="1444c-113">In ASP.NET applications, the <xref:System.Web.UI.WebControls.LinqDataSource> manages most of this complexity.</span></span> <span data-ttu-id="1444c-114">有关详细信息，请参阅 [LinqDataSource Web 服务器控件概述](/previous-versions/aspnet/bb547113(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="1444c-114">For more information, see [LinqDataSource Web Server Control Overview](/previous-versions/aspnet/bb547113(v=vs.100)).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="1444c-115">其他资源</span><span class="sxs-lookup"><span data-stu-id="1444c-115">Additional Resources</span></span>

 <span data-ttu-id="1444c-116">有关如何实现使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的 n 层应用程序的更多信息，请参见以下主题：</span><span class="sxs-lookup"><span data-stu-id="1444c-116">For more information about how to implement n-tier applications that use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], see the following topics:</span></span>

- [<span data-ttu-id="1444c-117">具有 ASP.NET 的 LINQ to SQL N 层</span><span class="sxs-lookup"><span data-stu-id="1444c-117">LINQ to SQL N-Tier with ASP.NET</span></span>](linq-to-sql-n-tier-with-aspnet.md)

- [<span data-ttu-id="1444c-118">具有 Web 服务的 LINQ to SQL N 层</span><span class="sxs-lookup"><span data-stu-id="1444c-118">LINQ to SQL N-Tier with Web Services</span></span>](linq-to-sql-n-tier-with-web-services.md)

- [<span data-ttu-id="1444c-119">实现 N 层业务逻辑</span><span class="sxs-lookup"><span data-stu-id="1444c-119">Implementing N-Tier Business Logic</span></span>](implementing-business-logic-linq-to-sql.md)

- [<span data-ttu-id="1444c-120">N 层应用程序中的数据检索和 CUD 操作 (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="1444c-120">Data Retrieval and CUD Operations in N-Tier Applications (LINQ to SQL)</span></span>](data-retrieval-and-cud-operations-in-n-tier-applications.md)

 <span data-ttu-id="1444c-121">有关使用 ADO.NET 数据集的 n 层应用程序的详细信息，请参阅 [在 n 层应用程序中使用数据集](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications)。</span><span class="sxs-lookup"><span data-stu-id="1444c-121">For more information about n-tier applications that use ADO.NET DataSets, see [Work with datasets in n-tier applications](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications).</span></span>

## <a name="see-also"></a><span data-ttu-id="1444c-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="1444c-122">See also</span></span>

- [<span data-ttu-id="1444c-123">背景信息</span><span class="sxs-lookup"><span data-stu-id="1444c-123">Background Information</span></span>](background-information.md)

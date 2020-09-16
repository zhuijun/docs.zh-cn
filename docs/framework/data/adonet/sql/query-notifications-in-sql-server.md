---
title: SQL Server 中的查询通知
description: 了解如何使用查询通知在 SQL Server 数据库中更改数据时通知应用程序，例如，刷新应用程序显示。
ms.date: 03/30/2017
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
ms.openlocfilehash: 43b496db74f7e6fc9bc9f17d946bf34398b32312
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543980"
---
# <a name="query-notifications-in-sql-server"></a><span data-ttu-id="c1f11-103">SQL Server 中的查询通知</span><span class="sxs-lookup"><span data-stu-id="c1f11-103">Query Notifications in SQL Server</span></span>
<span data-ttu-id="c1f11-104">查询通知建立在 Service Broker 基础结构之上，并允许在数据发生更改时向应用程序发送通知。</span><span class="sxs-lookup"><span data-stu-id="c1f11-104">Built upon the Service Broker infrastructure, query notifications allow applications to be notified when data has changed.</span></span> <span data-ttu-id="c1f11-105">对提供数据库信息的缓存且需要在源数据发生更改时收到通知的应用程序（如 Web 应用程序）而言，以上功能特别有用。</span><span class="sxs-lookup"><span data-stu-id="c1f11-105">This feature is particularly useful for applications that provide a cache of information from a database, such as a Web application, and need to be notified when the source data is changed.</span></span>  
  
 <span data-ttu-id="c1f11-106">使用 ADO.NET，可以通过三种方式实现查询通知：</span><span class="sxs-lookup"><span data-stu-id="c1f11-106">There are three ways you can implement query notifications using ADO.NET:</span></span>  
  
1. <span data-ttu-id="c1f11-107">公开服务器端功能的 `SqlNotificationRequest` 类提供低级别实现，使你能够利用通知请求执行命令。</span><span class="sxs-lookup"><span data-stu-id="c1f11-107">The low-level implementation is provided by the `SqlNotificationRequest` class that exposes server-side functionality, enabling you to execute a command with a notification request.</span></span>  
  
2. <span data-ttu-id="c1f11-108">高级别实现由 `SqlDependency` 类提供，该类可提供源应用程序与 SQL Server 之间的通知功能的高级抽象，使你能够使用依赖项来检测服务器中的更改。</span><span class="sxs-lookup"><span data-stu-id="c1f11-108">The high-level implementation is provided by the `SqlDependency` class, which is a class that provides a high-level abstraction of notification functionality between the source application and SQL Server, enabling you to use a dependency to detect changes in the server.</span></span> <span data-ttu-id="c1f11-109">大多数情况下，这是托管客户端应用程序通过适用于 SQL Server 的 .NET Framework 数据提供程序利用 SQL Server 通知功能的最简单、最有效的方法。</span><span class="sxs-lookup"><span data-stu-id="c1f11-109">In most cases, this is the simplest and most effective way to leverage SQL Server notifications capability by managed client applications using the .NET Framework Data Provider for SQL Server.</span></span>  
  
3. <span data-ttu-id="c1f11-110">此外，使用 ASP.NET 2.0 或更高版本构建的 Web 应用程序可以使用 `SqlCacheDependency` 帮助程序类。</span><span class="sxs-lookup"><span data-stu-id="c1f11-110">In addition, Web applications built using ASP.NET 2.0 or later can use the `SqlCacheDependency` helper classes.</span></span>  
  
 <span data-ttu-id="c1f11-111">如果应用程序需要通过刷新显示或缓存来响应基础数据中的更改，则查询通知非常有用。</span><span class="sxs-lookup"><span data-stu-id="c1f11-111">Query notifications are used for applications that need to refresh displays or caches in response to changes in underlying data.</span></span> <span data-ttu-id="c1f11-112">如果执行相同命令生成的结果集与最初检索到的结果集不同，则 Microsoft SQL Server 可允许 .NET Framework 应用程序向 SQL Server 发送命令和请求通知。</span><span class="sxs-lookup"><span data-stu-id="c1f11-112">Microsoft SQL Server allows .NET Framework applications to send a command to SQL Server and request notification if executing the same command would produce result sets different from those initially retrieved.</span></span> <span data-ttu-id="c1f11-113">服务器上生成的通知是通过这些队列发送的，以便在稍后进行处理。</span><span class="sxs-lookup"><span data-stu-id="c1f11-113">Notifications generated at the server are sent through queues to be processed later.</span></span>  
  
 <span data-ttu-id="c1f11-114">可以为 SELECT 和 EXECUTE 语句设置通知。</span><span class="sxs-lookup"><span data-stu-id="c1f11-114">You can set up notifications for SELECT and EXECUTE statements.</span></span> <span data-ttu-id="c1f11-115">使用 EXECUTE 语句时，SQL Server 将为执行的命令（而不是 EXECUTE 语句本身）注册一个通知。</span><span class="sxs-lookup"><span data-stu-id="c1f11-115">When using an EXECUTE statement, SQL Server registers a notification for the command executed rather than the EXECUTE statement itself.</span></span> <span data-ttu-id="c1f11-116">命令必须满足 SELECT 语句的要求和限制。</span><span class="sxs-lookup"><span data-stu-id="c1f11-116">The command must meet the requirements and limitations for a SELECT statement.</span></span> <span data-ttu-id="c1f11-117">当注册通知的命令包含多条语句时，数据库引擎将为批处理中的每条语句创建一个通知。</span><span class="sxs-lookup"><span data-stu-id="c1f11-117">When a command that registers a notification contains more than one statement, the Database Engine creates a notification for each statement in the batch.</span></span>  
  
 <span data-ttu-id="c1f11-118">如果正在开发的应用程序在数据更改时需要可靠的第二秒通知，请查看规划[通知](/previous-versions/sql/sql-server-2008-r2/ms187528(v=sql.105))一文中的 "**规划有效的查询通知策略**" 和 "**查询通知的替代方案**" 部分。</span><span class="sxs-lookup"><span data-stu-id="c1f11-118">If you are developing an application where you need reliable sub-second notifications when data changes, review the sections **Planning an Efficient Query Notifications Strategy** and **Alternatives to Query Notifications** in the [Planning for Notifications](/previous-versions/sql/sql-server-2008-r2/ms187528(v=sql.105)) article.</span></span> <span data-ttu-id="c1f11-119">有关查询通知和 SQL Server Service Broker 的详细信息，请参阅 SQL Server 文档中的以下文章链接。</span><span class="sxs-lookup"><span data-stu-id="c1f11-119">For more information about Query Notifications and SQL Server Service Broker, see the following links to articles in the SQL Server documentation.</span></span>  
  
 <span data-ttu-id="c1f11-120">**SQL Server 文档**</span><span class="sxs-lookup"><span data-stu-id="c1f11-120">**SQL Server documentation**</span></span>  
  
- <span data-ttu-id="c1f11-121">[使用查询通知](/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="c1f11-121">[Using Query Notifications](/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))</span></span>  
  
- <span data-ttu-id="c1f11-122">[为通知创建查询](/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="c1f11-122">[Creating a Query for Notification](/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span></span>  
  
- <span data-ttu-id="c1f11-123">[开发 (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="c1f11-123">[Development (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))</span></span>  
  
- <span data-ttu-id="c1f11-124">[Service Broker 开发人员信息中心](/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="c1f11-124">[Service Broker Developer InfoCenter](/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span></span>  
  
- <span data-ttu-id="c1f11-125">[开发人员指南 (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="c1f11-125">[Developer's Guide (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c1f11-126">本节内容</span><span class="sxs-lookup"><span data-stu-id="c1f11-126">In This Section</span></span>  
 [<span data-ttu-id="c1f11-127">启用查询通知</span><span class="sxs-lookup"><span data-stu-id="c1f11-127">Enabling Query Notifications</span></span>](enabling-query-notifications.md)  
 <span data-ttu-id="c1f11-128">介绍如何使用查询通知，其中包括启用和使用查询通知的要求。</span><span class="sxs-lookup"><span data-stu-id="c1f11-128">Discusses how to use query notifications, including the requirements for enabling and using them.</span></span>  
  
 [<span data-ttu-id="c1f11-129">ASP.NET 应用程序中的 SqlDependency</span><span class="sxs-lookup"><span data-stu-id="c1f11-129">SqlDependency in an ASP.NET Application</span></span>](sqldependency-in-an-aspnet-app.md)  
 <span data-ttu-id="c1f11-130">演示如何使用 ASP.NET 应用程序中的查询通知。</span><span class="sxs-lookup"><span data-stu-id="c1f11-130">Demonstrates how to use query notifications from an ASP.NET application.</span></span>  
  
 [<span data-ttu-id="c1f11-131">用 SqlDependency 检测更改</span><span class="sxs-lookup"><span data-stu-id="c1f11-131">Detecting Changes with SqlDependency</span></span>](detecting-changes-with-sqldependency.md)  
 <span data-ttu-id="c1f11-132">演示如何检测查询结果与最初接收的结果不同的情况。</span><span class="sxs-lookup"><span data-stu-id="c1f11-132">Demonstrates how to detect when query results will be different from those originally received.</span></span>  
  
 [<span data-ttu-id="c1f11-133">使用 SqlNotificationRequest 执行 SqlCommand</span><span class="sxs-lookup"><span data-stu-id="c1f11-133">SqlCommand Execution with a SqlNotificationRequest</span></span>](sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 <span data-ttu-id="c1f11-134">演示如何将 <xref:System.Data.SqlClient.SqlCommand> 对象配置为使用查询通知。</span><span class="sxs-lookup"><span data-stu-id="c1f11-134">Demonstrates configuring a <xref:System.Data.SqlClient.SqlCommand> object to work with a query notification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c1f11-135">参考</span><span class="sxs-lookup"><span data-stu-id="c1f11-135">Reference</span></span>  
 <xref:System.Data.Sql.SqlNotificationRequest>  
 <span data-ttu-id="c1f11-136">介绍 <xref:System.Data.Sql.SqlNotificationRequest> 类及其所有成员。</span><span class="sxs-lookup"><span data-stu-id="c1f11-136">Describes the <xref:System.Data.Sql.SqlNotificationRequest> class and all of its members.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 <span data-ttu-id="c1f11-137">介绍 <xref:System.Data.SqlClient.SqlDependency> 类及其所有成员。</span><span class="sxs-lookup"><span data-stu-id="c1f11-137">Describes the <xref:System.Data.SqlClient.SqlDependency> class and all of its members.</span></span>  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 <span data-ttu-id="c1f11-138">介绍 <xref:System.Web.Caching.SqlCacheDependency> 类及其所有成员。</span><span class="sxs-lookup"><span data-stu-id="c1f11-138">Describes the <xref:System.Web.Caching.SqlCacheDependency> class and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1f11-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="c1f11-139">See also</span></span>

- [<span data-ttu-id="c1f11-140">SQL Server 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c1f11-140">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="c1f11-141">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="c1f11-141">ADO.NET Overview</span></span>](../ado-net-overview.md)

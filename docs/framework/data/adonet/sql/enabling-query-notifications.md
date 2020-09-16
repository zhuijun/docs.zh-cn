---
title: 启用查询通知
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
ms.openlocfilehash: 693e67b4d369eb69b8e0a9dded6decb2d3928459
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554874"
---
# <a name="enabling-query-notifications"></a><span data-ttu-id="ff93b-102">启用查询通知</span><span class="sxs-lookup"><span data-stu-id="ff93b-102">Enabling Query Notifications</span></span>
<span data-ttu-id="ff93b-103">使用查询通知的应用程序具有一组通用的要求。</span><span class="sxs-lookup"><span data-stu-id="ff93b-103">Applications that consume query notifications have a common set of requirements.</span></span> <span data-ttu-id="ff93b-104">必须正确配置数据源才能支持 SQL 查询通知，并且用户必须具有正确的客户端和服务器端权限。</span><span class="sxs-lookup"><span data-stu-id="ff93b-104">Your data source must be correctly configured to support SQL query notifications, and the user must have the correct client-side and server-side permissions.</span></span>  
  
 <span data-ttu-id="ff93b-105">若要使用查询通知，必须：</span><span class="sxs-lookup"><span data-stu-id="ff93b-105">To use query notifications you must:</span></span>  
  
- <span data-ttu-id="ff93b-106">为数据库启用查询通知。</span><span class="sxs-lookup"><span data-stu-id="ff93b-106">Enable query notifications for your database.</span></span>  
  
- <span data-ttu-id="ff93b-107">确保用于连接数据库的用户 ID 具有所需的权限。</span><span class="sxs-lookup"><span data-stu-id="ff93b-107">Ensure that the user ID used to connect to the database has the necessary permissions.</span></span>  
  
- <span data-ttu-id="ff93b-108">使用 <xref:System.Data.SqlClient.SqlCommand> 对象与关联的通知对象（<xref:System.Data.SqlClient.SqlDependency> 或 <xref:System.Data.Sql.SqlNotificationRequest>）一起执行有效的 SELECT 语句。</span><span class="sxs-lookup"><span data-stu-id="ff93b-108">Use a <xref:System.Data.SqlClient.SqlCommand> object to execute a valid SELECT statement with an associated notification object—either <xref:System.Data.SqlClient.SqlDependency> or <xref:System.Data.Sql.SqlNotificationRequest>.</span></span>  
  
- <span data-ttu-id="ff93b-109">如果要监视的数据发生更改，请提供代码以处理通知。</span><span class="sxs-lookup"><span data-stu-id="ff93b-109">Provide code to process the notification if the data being monitored changes.</span></span>  
  
## <a name="query-notifications-requirements"></a><span data-ttu-id="ff93b-110">查询通知需求</span><span class="sxs-lookup"><span data-stu-id="ff93b-110">Query Notifications Requirements</span></span>  
 <span data-ttu-id="ff93b-111">只有满足下列特定要求的 SELECT 语句才支持查询通知。</span><span class="sxs-lookup"><span data-stu-id="ff93b-111">Query notifications are supported only for SELECT statements that meet a list of specific requirements.</span></span> <span data-ttu-id="ff93b-112">下表提供了指向 SQL Server 联机丛书中的 Service Broker 和查询通知文档的链接。</span><span class="sxs-lookup"><span data-stu-id="ff93b-112">The following table provides links to the Service Broker and Query Notifications documentation in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="ff93b-113">**SQL Server 文档**</span><span class="sxs-lookup"><span data-stu-id="ff93b-113">**SQL Server documentation**</span></span>  
  
- <span data-ttu-id="ff93b-114">[为通知创建查询](/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="ff93b-114">[Creating a Query for Notification](/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span></span>  
  
- <span data-ttu-id="ff93b-115">[Service Broker 的安全注意事项](/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="ff93b-115">[Security Considerations for Service Broker](/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))</span></span>  
  
- <span data-ttu-id="ff93b-116">[安全性和保护 (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="ff93b-116">[Security and Protection (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))</span></span>  
  
- <span data-ttu-id="ff93b-117">[Notification Services 的安全注意事项](/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="ff93b-117">[Security Considerations for Notifications Services](/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))</span></span>  
  
- <span data-ttu-id="ff93b-118">[查询通知权限](/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="ff93b-118">[Query Notification Permissions](/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))</span></span>  
  
- <span data-ttu-id="ff93b-119">[Service Broker 的国际化注意事项](/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="ff93b-119">[International Considerations for Service Broker](/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))</span></span>  
  
- <span data-ttu-id="ff93b-120">[解决方案设计注意事项 (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="ff93b-120">[Solution Design Considerations (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))</span></span>  
  
- <span data-ttu-id="ff93b-121">[Service Broker 开发人员信息中心](/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="ff93b-121">[Service Broker Developer InfoCenter](/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span></span>  
  
- <span data-ttu-id="ff93b-122">[开发人员指南 (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="ff93b-122">[Developer's Guide (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span></span>  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a><span data-ttu-id="ff93b-123">启用查询通知运行示例代码</span><span class="sxs-lookup"><span data-stu-id="ff93b-123">Enabling Query Notifications to Run Sample Code</span></span>  
 <span data-ttu-id="ff93b-124">若要通过使用 SQL Server Management Studio 在 AdventureWorks 数据库上启用 Service Broker，请执行下面的 Transact-SQL 语句\*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="ff93b-124">To enable Service Broker on the **AdventureWorks** database by using SQL Server Management Studio, execute the following Transact-SQL statement:</span></span>  
  
 `ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
 <span data-ttu-id="ff93b-125">为了使查询通知示例正确运行，必须在数据库服务器上执行以下 Transact-SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="ff93b-125">For the query notification samples to run correctly, the following Transact-SQL statements must be executed on the database server.</span></span>  
  
```sql
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a><span data-ttu-id="ff93b-126">查询通知权限</span><span class="sxs-lookup"><span data-stu-id="ff93b-126">Query Notifications Permissions</span></span>  
 <span data-ttu-id="ff93b-127">执行请求通知的命令的用户必须具有对服务器的 SUBSCRIBE QUERY NOTIFICATIONS 数据库权限。</span><span class="sxs-lookup"><span data-stu-id="ff93b-127">Users who execute commands requesting notification must have SUBSCRIBE QUERY NOTIFICATIONS database permission on the server.</span></span>  
  
 <span data-ttu-id="ff93b-128">在部分信任情况下运行的客户端代码需要 <xref:System.Data.SqlClient.SqlClientPermission>。</span><span class="sxs-lookup"><span data-stu-id="ff93b-128">Client-side code that runs in a partial trust situation requires the <xref:System.Data.SqlClient.SqlClientPermission>.</span></span>  
  
 <span data-ttu-id="ff93b-129">以下代码创建 <xref:System.Data.SqlClient.SqlClientPermission> 对象，并将 <xref:System.Security.Permissions.PermissionState> 设置为 <xref:System.Security.Permissions.PermissionState.Unrestricted>。</span><span class="sxs-lookup"><span data-stu-id="ff93b-129">The following code creates a <xref:System.Data.SqlClient.SqlClientPermission> object, setting the <xref:System.Security.Permissions.PermissionState> to <xref:System.Security.Permissions.PermissionState.Unrestricted>.</span></span> <span data-ttu-id="ff93b-130">如果未对调用堆栈中处于较高位置的所有调用方授予权限，<xref:System.Security.CodeAccessPermission.Demand%2A> 会在运行时强制执行 <xref:System.Security.SecurityException>。</span><span class="sxs-lookup"><span data-stu-id="ff93b-130">The <xref:System.Security.CodeAccessPermission.Demand%2A> will force a <xref:System.Security.SecurityException> at run time if all callers higher in the call stack have not been granted the permission.</span></span>  
  
 [!code-csharp[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/CS/source.cs#1)]
 [!code-vb[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/VB/source.vb#1)]  
  
## <a name="choosing-a-notification-object"></a><span data-ttu-id="ff93b-131">选择通知对象</span><span class="sxs-lookup"><span data-stu-id="ff93b-131">Choosing a Notification Object</span></span>  
 <span data-ttu-id="ff93b-132">查询通知 API 提供两个用于处理通知的对象：<xref:System.Data.SqlClient.SqlDependency> 和 <xref:System.Data.Sql.SqlNotificationRequest>。</span><span class="sxs-lookup"><span data-stu-id="ff93b-132">The query notifications API provides two objects to process notifications: <xref:System.Data.SqlClient.SqlDependency> and <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="ff93b-133">通常情况下，大多数非 ASP.NET 应用程序应使用 <xref:System.Data.SqlClient.SqlDependency> 对象。</span><span class="sxs-lookup"><span data-stu-id="ff93b-133">In general, most non-ASP.NET applications should use the <xref:System.Data.SqlClient.SqlDependency> object.</span></span> <span data-ttu-id="ff93b-134">ASP.NET 应用程序应使用更高级别的 <xref:System.Web.Caching.SqlCacheDependency>，以便包装 <xref:System.Data.SqlClient.SqlDependency> 并为管理通知和缓存对象提供框架。</span><span class="sxs-lookup"><span data-stu-id="ff93b-134">ASP.NET applications should use the higher-level <xref:System.Web.Caching.SqlCacheDependency>, which wraps <xref:System.Data.SqlClient.SqlDependency> and provides a framework for administering the notification and cache objects.</span></span>  
  
### <a name="using-sqldependency"></a><span data-ttu-id="ff93b-135">使用 SqlDependency</span><span class="sxs-lookup"><span data-stu-id="ff93b-135">Using SqlDependency</span></span>  
 <span data-ttu-id="ff93b-136">要使用 <xref:System.Data.SqlClient.SqlDependency>，必须对所使用的 SQL Server 数据库启用 Service Broker，并且用户必须具有接收通知的权限。</span><span class="sxs-lookup"><span data-stu-id="ff93b-136">To use <xref:System.Data.SqlClient.SqlDependency>, Service Broker must be enabled for the SQL Server database being used, and users must have permissions to receive notifications.</span></span> <span data-ttu-id="ff93b-137">Service Broker 对象（如通知队列）是预定义的。</span><span class="sxs-lookup"><span data-stu-id="ff93b-137">Service Broker objects, such as the notification queue, are predefined.</span></span>  
  
 <span data-ttu-id="ff93b-138">此外，<xref:System.Data.SqlClient.SqlDependency> 会自动启动一个工作线程以在通知发布到队列中时处理这些通知；它还会分析 Service Broker 消息，将此信息作为事件参数数据公开。</span><span class="sxs-lookup"><span data-stu-id="ff93b-138">In addition, <xref:System.Data.SqlClient.SqlDependency> automatically launches a worker thread to process notifications as they are posted to the queue; it also parses the Service Broker message, exposing the information as event argument data.</span></span> <span data-ttu-id="ff93b-139">必须通过调用 `Start` 方法建立对数据库的依赖关系，从而初始化 <xref:System.Data.SqlClient.SqlDependency>。</span><span class="sxs-lookup"><span data-stu-id="ff93b-139"><xref:System.Data.SqlClient.SqlDependency> must be initialized by calling the `Start` method to establish a dependency to the database.</span></span> <span data-ttu-id="ff93b-140">这是一个静态方法，对于每个所需的数据库连接，在应用程序初始化期间仅需调用一次。</span><span class="sxs-lookup"><span data-stu-id="ff93b-140">This is a static method that needs to be called only once during application initialization for each database connection required.</span></span> <span data-ttu-id="ff93b-141">必须在应用程序终止时为执行的每个相关连接调用 `Stop` 方法。</span><span class="sxs-lookup"><span data-stu-id="ff93b-141">The `Stop` method should be called at application termination for each dependency connection that was made.</span></span>  
  
### <a name="using-sqlnotificationrequest"></a><span data-ttu-id="ff93b-142">使用 SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="ff93b-142">Using SqlNotificationRequest</span></span>  
 <span data-ttu-id="ff93b-143">与此相反，<xref:System.Data.Sql.SqlNotificationRequest> 要求你自己实现整个侦听基础结构。</span><span class="sxs-lookup"><span data-stu-id="ff93b-143">In contrast, <xref:System.Data.Sql.SqlNotificationRequest> requires you to implement the entire listening infrastructure yourself.</span></span> <span data-ttu-id="ff93b-144">此外，必须定义队列所支持的所有支持 Service Broker 对象，例如队列、服务和消息类型。</span><span class="sxs-lookup"><span data-stu-id="ff93b-144">In addition, all the supporting Service Broker objects such as the queue, service, and message types supported by the queue must be defined.</span></span> <span data-ttu-id="ff93b-145">如果你的应用程序需要特殊通知消息或通知行为，或者你的应用程序是较大的 Service Broker 应用程序的一部分，则此手动方法非常有用。</span><span class="sxs-lookup"><span data-stu-id="ff93b-145">This manual approach is useful if your application requires special notification messages or notification behaviors, or if your application is part of a larger Service Broker application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff93b-146">请参阅</span><span class="sxs-lookup"><span data-stu-id="ff93b-146">See also</span></span>

- [<span data-ttu-id="ff93b-147">SQL Server 中的查询通知</span><span class="sxs-lookup"><span data-stu-id="ff93b-147">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)
- [<span data-ttu-id="ff93b-148">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="ff93b-148">ADO.NET Overview</span></span>](../ado-net-overview.md)

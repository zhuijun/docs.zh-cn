---
title: SQL Server 功能和 ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: 2839529b-a79b-4450-be5d-07a98dbc7a0f
ms.openlocfilehash: 121381114fadd8b20978d2e932bf3ec8bdcdb193
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177314"
---
# <a name="sql-server-features-and-adonet"></a><span data-ttu-id="56672-102">SQL Server 功能和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="56672-102">SQL Server Features and ADO.NET</span></span>

<span data-ttu-id="56672-103">本节中的主题讨论 SQL Server 中针对使用 ADO.NET 开发数据库应用程序的功能。</span><span class="sxs-lookup"><span data-stu-id="56672-103">The topics in this section discuss features in SQL Server that are targeted at developing database applications using ADO.NET.</span></span>  
  
 <span data-ttu-id="56672-104">有关更多信息，请参见与您所使用的 SQL Server 版本对应的 SQL Server 联机丛书，如下表中所示。</span><span class="sxs-lookup"><span data-stu-id="56672-104">For more information, see SQL Server Books Online for the version of SQL Server you are using, as listed in the following table.</span></span>  
  
 <span data-ttu-id="56672-105">**SQL Server 文档**</span><span class="sxs-lookup"><span data-stu-id="56672-105">**SQL Server documentation**</span></span>  
  
1. <span data-ttu-id="56672-106">[Development (Database Engine)（开发 [数据库引擎]）](/previous-versions/sql/sql-server-2008/bb500155(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="56672-106">[Development (Database Engine)](/previous-versions/sql/sql-server-2008/bb500155(v=sql.100))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="56672-107">本节内容</span><span class="sxs-lookup"><span data-stu-id="56672-107">In This Section</span></span>  

 [<span data-ttu-id="56672-108">枚举 SQL Server 的实例 (ADO.NET) </span><span class="sxs-lookup"><span data-stu-id="56672-108">Enumerating Instances of SQL Server (ADO.NET)</span></span>](enumerating-instances-of-sql-server.md)  
 <span data-ttu-id="56672-109">介绍如何枚举 SQL Server 的活动实例。</span><span class="sxs-lookup"><span data-stu-id="56672-109">Describes how to enumerate active instances of SQL Server.</span></span>  
  
 [<span data-ttu-id="56672-110">SQL Server 的提供程序统计信息</span><span class="sxs-lookup"><span data-stu-id="56672-110">Provider Statistics for SQL Server</span></span>](provider-statistics-for-sql-server.md)  
 <span data-ttu-id="56672-111">介绍对获取 SQL Server 运行时统计信息的支持。</span><span class="sxs-lookup"><span data-stu-id="56672-111">Describes support for obtaining SQL Server run-time statistics.</span></span>  
  
 [<span data-ttu-id="56672-112">SQL Server Express 用户实例</span><span class="sxs-lookup"><span data-stu-id="56672-112">SQL Server Express User Instances</span></span>](sql-server-express-user-instances.md)  
 <span data-ttu-id="56672-113">介绍对 SQL Server Express 用户实例的支持。</span><span class="sxs-lookup"><span data-stu-id="56672-113">Describes support for SQL Server Express user instances.</span></span>  
  
 [<span data-ttu-id="56672-114">SQL Server 中的数据库镜像</span><span class="sxs-lookup"><span data-stu-id="56672-114">Database Mirroring in SQL Server</span></span>](database-mirroring-in-sql-server.md)  
 <span data-ttu-id="56672-115">介绍了数据库镜像功能。</span><span class="sxs-lookup"><span data-stu-id="56672-115">Describes database mirroring functionality.</span></span>  
  
 [<span data-ttu-id="56672-116">SQL Server 公共语言运行时集成</span><span class="sxs-lookup"><span data-stu-id="56672-116">SQL Server Common Language Runtime Integration</span></span>](sql-server-common-language-runtime-integration.md)  
 <span data-ttu-id="56672-117">说明如何从 SQL Server 的公共语言运行库 (CLR) 数据库对象中访问数据。</span><span class="sxs-lookup"><span data-stu-id="56672-117">Describes how data can be accessed from within a common language runtime (CLR) database object in SQL Server.</span></span>  
  
 [<span data-ttu-id="56672-118">SQL Server 中的查询通知</span><span class="sxs-lookup"><span data-stu-id="56672-118">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)  
 <span data-ttu-id="56672-119">说明数据发生更改时，.NET Framework 应用程序如何从 SQL Server 请求通知。</span><span class="sxs-lookup"><span data-stu-id="56672-119">Describes how .NET Framework applications can request notification from SQL Server when data has changed.</span></span>  
  
 [<span data-ttu-id="56672-120">SQL Server 中的快照隔离</span><span class="sxs-lookup"><span data-stu-id="56672-120">Snapshot Isolation in SQL Server</span></span>](snapshot-isolation-in-sql-server.md)  
 <span data-ttu-id="56672-121">介绍对快照隔离的支持，这是一种旨在减少事务应用程序中的阻塞的行版本控制机制。</span><span class="sxs-lookup"><span data-stu-id="56672-121">Describes support for snapshot isolation, a row versioning mechanism designed to reduce blocking in transactional applications.</span></span>  
  
 [<span data-ttu-id="56672-122">SqlClient 对高可用性、灾难恢复的支持</span><span class="sxs-lookup"><span data-stu-id="56672-122">SqlClient Support for High Availability, Disaster Recovery</span></span>](sqlclient-support-for-high-availability-disaster-recovery.md)  
 <span data-ttu-id="56672-123">介绍对高可用性、灾难恢复 (AlwaysOn) 可用性组的 SqlClient 支持。</span><span class="sxs-lookup"><span data-stu-id="56672-123">Describes SqlClient support for high-availability, disaster recovery (AlwaysOn) availability groups.</span></span>  
  
 [<span data-ttu-id="56672-124">SqlClient 对 LocalDB 的支持</span><span class="sxs-lookup"><span data-stu-id="56672-124">SqlClient Support for LocalDB</span></span>](sqlclient-support-for-localdb.md)  
 <span data-ttu-id="56672-125">介绍对 LocalDB 数据库的 SqlClient 支持。</span><span class="sxs-lookup"><span data-stu-id="56672-125">Describes SqlClient support for LocalDB databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56672-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="56672-126">See also</span></span>

- [<span data-ttu-id="56672-127">ADO.NET 中的 SQL Server 数据操作</span><span class="sxs-lookup"><span data-stu-id="56672-127">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="56672-128">在 ADO.NET 中检索和修改数据</span><span class="sxs-lookup"><span data-stu-id="56672-128">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="56672-129">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="56672-129">LINQ to SQL</span></span>](./linq/index.md)
- [<span data-ttu-id="56672-130">SQL Server 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="56672-130">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="56672-131">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="56672-131">ADO.NET Overview</span></span>](../ado-net-overview.md)

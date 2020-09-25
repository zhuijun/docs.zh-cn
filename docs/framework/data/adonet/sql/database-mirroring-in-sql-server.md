---
title: SQL Server 中的数据库镜像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 89befaff-bb46-4290-8382-e67cdb0e3de9
ms.openlocfilehash: 7e2c1c8ea1cbc1bb22452b9ef9d1f250c96118ea
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173531"
---
# <a name="database-mirroring-in-sql-server"></a><span data-ttu-id="ccbfd-102">SQL Server 中的数据库镜像</span><span class="sxs-lookup"><span data-stu-id="ccbfd-102">Database Mirroring in SQL Server</span></span>

<span data-ttu-id="ccbfd-103">通过 SQL Server 中的数据库镜像，可以在备用服务器上保留 SQL Server 数据库的副本（即镜像）。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-103">Database mirroring in SQL Server allows you to keep a copy, or mirror, of a SQL Server database on a standby server.</span></span> <span data-ttu-id="ccbfd-104">镜像可确保始终存在数据的两个独立副本，从而提供高可用性和完整的数据冗余。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-104">Mirroring ensures that two separate copies of the data exist at all times, providing high availability and complete data redundancy.</span></span> <span data-ttu-id="ccbfd-105">用于 SQL Server 的 .NET 数据提供程序提供了数据库镜像的隐式支持，这样，在为 SQL Server 数据库配置了镜像之后，开发人员无需采取任何措施或编写任何代码。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-105">The .NET Data Provider for SQL Server provides implicit support for database mirroring, so that the developer does not need to take any action or write any code once it has been configured for a SQL Server database.</span></span> <span data-ttu-id="ccbfd-106">此外，<xref:System.Data.SqlClient.SqlConnection> 对象还支持显式连接模式，即允许在 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> 中提供故障转移伙伴服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-106">In addition, the <xref:System.Data.SqlClient.SqlConnection> object supports an explicit connection mode that allows supplying the name of a failover partner server in the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="ccbfd-107">下面是定目标到已配置镜像的数据库的 <xref:System.Data.SqlClient.SqlConnection> 对象的简化事件序列：</span><span class="sxs-lookup"><span data-stu-id="ccbfd-107">The following simplified sequence of events occurs for a <xref:System.Data.SqlClient.SqlConnection> object that targets a database configured for mirroring:</span></span>  
  
1. <span data-ttu-id="ccbfd-108">客户端应用程序成功连接到主体数据库，服务器发送回伙伴服务器的名称，然后将它缓存在客户端上。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-108">The client application successfully connects to the principal database, and the server sends back the name of the partner server, which is then cached on the client.</span></span>  
  
2. <span data-ttu-id="ccbfd-109">如果包含主体数据库的服务器发生故障或连接中断，连接和事务状态会丢失。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-109">If the server containing the principal database fails or connectivity is interrupted, connection and transaction state is lost.</span></span> <span data-ttu-id="ccbfd-110">客户端应用程序尝试重新与主体数据库建立连接，但失败了。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-110">The client application attempts to re-establish a connection to the principal database and fails.</span></span>  
  
3. <span data-ttu-id="ccbfd-111">然后，客户端应用程序以透明方式尝试与伙伴服务器上的镜像数据库建立连接。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-111">The client application then transparently attempts to establish a connection to the mirror database on the partner server.</span></span> <span data-ttu-id="ccbfd-112">如果成功，连接会重定向到镜像数据库，然后镜像数据库会成为新的主体数据库。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-112">If it succeeds, the connection is redirected to the mirror database, which then becomes the new principal database.</span></span>  
  
## <a name="specifying-the-failover-partner-in-the-connection-string"></a><span data-ttu-id="ccbfd-113">在连接字符串中指定故障转移合作伙伴</span><span class="sxs-lookup"><span data-stu-id="ccbfd-113">Specifying the Failover Partner in the Connection String</span></span>  

 <span data-ttu-id="ccbfd-114">如果你在连接字符串中提供故障转移伙伴服务器的名称，且主体数据库在客户端应用程序首次连接时不可用，那么客户端会以透明方式尝试与故障转移伙伴建立连接。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-114">If you supply the name of a failover partner server in the connection string, the client will transparently attempt a connection with the failover partner if the principal database is unavailable when the client application first connects.</span></span>  
  
```csharp
";Failover Partner=PartnerServerName"  
```  
  
 <span data-ttu-id="ccbfd-115">如果你省略故障转移伙伴服务器的名称，且主体数据库在客户端应用程序首次连接时不可用，那么 <xref:System.Data.SqlClient.SqlException> 会抛出。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-115">If you omit the name of the failover partner server and the principal database is unavailable when the client application first connects then a <xref:System.Data.SqlClient.SqlException> is raised.</span></span>  
  
 <span data-ttu-id="ccbfd-116">当 <xref:System.Data.SqlClient.SqlConnection> 成功打开时，服务器会返回故障转移伙伴名称，此名称取代连接字符串中提供的任何值。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-116">When a <xref:System.Data.SqlClient.SqlConnection> is successfully opened, the failover partner name is returned by the server and supersedes any values supplied in the connection string.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ccbfd-117">对于数据库镜像方案，必须在连接字符串中显式指定初始目录或数据库名称。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-117">You must explicitly specify the initial catalog or database name in the connection string for database mirroring scenarios.</span></span> <span data-ttu-id="ccbfd-118">如果客户端接收没有显式指定初始编录或数据库的连接的故障转移信息，故障转移信息不会缓存，应用程序也不会在主体服务器失败时尝试进行故障转移。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-118">If the client receives failover information on a connection that doesn't have an explicitly specified initial catalog or database, the failover information is not cached and the application does not attempt to fail over if the principal server fails.</span></span> <span data-ttu-id="ccbfd-119">如果连接字符串有故障转移伙伴的值，但没有初始目录或数据库的值，那么 `InvalidArgumentException` 会抛出。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-119">If a connection string has a value for the failover partner, but no value for the initial catalog or database, an `InvalidArgumentException` is raised.</span></span>  
  
## <a name="retrieving-the-current-server-name"></a><span data-ttu-id="ccbfd-120">检索当前服务器名称</span><span class="sxs-lookup"><span data-stu-id="ccbfd-120">Retrieving the Current Server Name</span></span>  

 <span data-ttu-id="ccbfd-121">在发生故障转移时，可以使用 <xref:System.Data.SqlClient.SqlConnection> 对象的 <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> 属性，检索当前连接实际连接到的服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-121">In the event of a failover, you can retrieve the name of the server to which the current connection is actually connected by using the <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> property of a <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="ccbfd-122">下面的代码片段检索活动服务器的名称（假设连接变量引用打开的 <xref:System.Data.SqlClient.SqlConnection>）。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-122">The following code fragment retrieves the name of the active server, assuming that the connection variable references an open <xref:System.Data.SqlClient.SqlConnection>.</span></span>  
  
 <span data-ttu-id="ccbfd-123">当故障转移事件发生且连接切换到镜像服务器时，DataSource  属性会更新，以反映镜像名称。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-123">When a failover event occurs and the connection is switched to the mirror server, the **DataSource** property is updated to reflect the mirror name.</span></span>  
  
```vb  
Dim activeServer As String = connection.DataSource  
```  
  
```csharp  
string activeServer = connection.DataSource;  
```  
  
## <a name="sqlclient-mirroring-behavior"></a><span data-ttu-id="ccbfd-124">SqlClient 镜像行为</span><span class="sxs-lookup"><span data-stu-id="ccbfd-124">SqlClient Mirroring Behavior</span></span>  

 <span data-ttu-id="ccbfd-125">客户端始终尝试连接到当前主体服务器。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-125">The client always tries to connect to the current principal server.</span></span> <span data-ttu-id="ccbfd-126">如果失败，它会尝试连接到故障转移伙伴。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-126">If it fails, it tries the failover partner.</span></span> <span data-ttu-id="ccbfd-127">如果镜像数据库已切换为伙伴服务器上的主体角色，连接会成功，且新的主体镜像映射会发送到客户端，并在调用 <xref:System.AppDomain> 的生存期内进行缓存。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-127">If the mirror database has already been switched to the principal role on the partner server, the connection succeeds and the new principal-mirror mapping is sent to the client and cached for the lifetime of the calling <xref:System.AppDomain>.</span></span> <span data-ttu-id="ccbfd-128">映射不会存储在永久存储空间中，也无法供其他 AppDomain 或进程中的后续连接使用  。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-128">It is not stored in persistent storage and is not available for subsequent connections in a different **AppDomain** or process.</span></span> <span data-ttu-id="ccbfd-129">但是，可以供相同 AppDomain 中的后续连接使用  。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-129">However, it is available for subsequent connections within the same **AppDomain**.</span></span> <span data-ttu-id="ccbfd-130">注意，在相同或不同的计算机上运行的其他 AppDomain 或进程总是拥有自己的连接池，这些连接不会重置  。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-130">Note that another **AppDomain** or process running on the same or a different computer always has its pool of connections, and those connections are not reset.</span></span> <span data-ttu-id="ccbfd-131">在这种情况下，如果主数据库关闭，每个进程或 AppDomain 将失败，池将被自动清除  。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-131">In that case, if the primary database goes down, each process or **AppDomain** fails once, and the pool is automatically cleared.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ccbfd-132">服务器上的镜像支持是逐个数据库进行配置的。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-132">Mirroring support on the server is configured on a per-database basis.</span></span> <span data-ttu-id="ccbfd-133">如果通过使用多部分名称或更改当前数据库对主体/镜像集中没有的其他数据库执行数据操作，对这些其他数据库所做的更改不会在发生故障时传播。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-133">If data manipulation operations are executed against other databases not included in the principal/mirror set, either by using multipart names or by changing the current database, the changes to these other databases do not propagate in the event of failure.</span></span> <span data-ttu-id="ccbfd-134">修改未镜像的数据库中的数据不会生成错误。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-134">No error is generated when data is modified in a database that is not mirrored.</span></span> <span data-ttu-id="ccbfd-135">开发人员必须评估此类操作可能会造成的影响。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-135">The developer must evaluate the possible impact of such operations.</span></span>  
  
## <a name="database-mirroring-resources"></a><span data-ttu-id="ccbfd-136">数据库镜像资源</span><span class="sxs-lookup"><span data-stu-id="ccbfd-136">Database Mirroring Resources</span></span>  

 <span data-ttu-id="ccbfd-137">有关配置、部署和管理镜像的概念性文档及信息，请参阅 SQL Server 文档中的下列资源。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-137">For conceptual documentation and information on configuring, deploying and administering mirroring, see the following resources in SQL Server documentation.</span></span>  
  
|<span data-ttu-id="ccbfd-138">资源</span><span class="sxs-lookup"><span data-stu-id="ccbfd-138">Resource</span></span>|<span data-ttu-id="ccbfd-139">说明</span><span class="sxs-lookup"><span data-stu-id="ccbfd-139">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="ccbfd-140">数据库镜像</span><span class="sxs-lookup"><span data-stu-id="ccbfd-140">Database Mirroring</span></span>](/sql/database-engine/database-mirroring/database-mirroring-sql-server)|<span data-ttu-id="ccbfd-141">介绍在 SQL Server 中设置和配置镜像的方法。</span><span class="sxs-lookup"><span data-stu-id="ccbfd-141">Describes how to set up and configure mirroring in SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ccbfd-142">请参阅</span><span class="sxs-lookup"><span data-stu-id="ccbfd-142">See also</span></span>

- [<span data-ttu-id="ccbfd-143">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="ccbfd-143">ADO.NET Overview</span></span>](../ado-net-overview.md)

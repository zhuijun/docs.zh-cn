---
title: SqlClient 对高可用性的支持，灾难恢复
description: 使用 AlwaysOn 可用性组了解 SQL Server 中的高可用性、灾难恢复的 SqlClient 应用程序支持。
ms.date: 03/30/2017
ms.assetid: 61e0b396-09d7-4e13-9711-7dcbcbd103a0
ms.openlocfilehash: eba243d37db8262970d161cfa786d3aee4462950
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286205"
---
# <a name="sqlclient-support-for-high-availability-disaster-recovery"></a><span data-ttu-id="d9f9c-103">SqlClient 对高可用性的支持，灾难恢复</span><span class="sxs-lookup"><span data-stu-id="d9f9c-103">SqlClient Support for High Availability, Disaster Recovery</span></span>
<span data-ttu-id="d9f9c-104">本主题讨论用于高可用性、灾难恢复 AlwaysOn 可用性组的 SqlClient 支持（在 .NET Framework 4.5 中添加）。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-104">This topic discusses SqlClient support (added in .NET Framework 4.5) for high-availability, disaster recovery -- AlwaysOn Availability Groups.</span></span>  <span data-ttu-id="d9f9c-105">AlwaysOn 可用性组功能已添加到 SQL Server 2012 中。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-105">AlwaysOn Availability Groups feature was added to SQL Server 2012.</span></span> <span data-ttu-id="d9f9c-106">有关 AlwaysOn 可用性组的详细信息，请参阅 SQL Server 联机丛书。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-106">For more information about AlwaysOn Availability Groups, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="d9f9c-107">现可在连接属性中指定（高可用性、灾难恢复功能）可用性组 (AG) 的可用性组侦听程序或 SQL Server 2012 故障转移群集实例。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-107">You can now specify the availability group listener of a (high-availability, disaster-recovery) availability group (AG) or SQL Server 2012 Failover Cluster Instance in the connection property.</span></span> <span data-ttu-id="d9f9c-108">如果将 SqlClient 应用程序连接到具有故障转移功能的 AlwaysOn 数据库，则在故障转移后，系统会断开原始连接，并且该应用程序必须建立一个新的连接才能继续运行。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-108">If a SqlClient application is connected to an AlwaysOn database that fails over, the original connection is broken and the application must open a new connection to continue work after the failover.</span></span>  
  
 <span data-ttu-id="d9f9c-109">如果没有连接到可用性组侦听程序或 SQL Server 2012 故障转移群集实例，并且如果多个 IP 地址关联一个主机名，SqlClient 将按顺序循环访问与 DNS 条目关联的所有 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-109">If you are not connecting to an availability group listener or SQL Server 2012 Failover Cluster Instance, and if multiple IP addresses are associated with a hostname, SqlClient will iterate sequentially through all IP addresses associated with DNS entry.</span></span> <span data-ttu-id="d9f9c-110">如果 DNS 服务器返回的第一个 IP 地址未绑定到任何网络接口卡 (NIC)，则上述遍历操作可能会用时较长。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-110">This can be time consuming if the first IP address returned by DNS server is not bound to any network interface card (NIC).</span></span> <span data-ttu-id="d9f9c-111">连接到一个可用性组侦听程序或 SQL Server 2012 故障转移群集实例时，SqlClient 尝试并行建立所有 IP 地址的连接，如果一个连接尝试成功，驱动程序将丢弃所有挂起的连接尝试。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-111">When connecting to an availability group listener or SQL Server 2012 Failover Cluster Instance, SqlClient attempts to establish connections to all IP addresses in parallel and if a connection attempt succeeds, the driver will discard any pending connection attempts.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9f9c-112">增大连接超时值和实现连接重试逻辑将增加应用程序连接到可用性组的概率。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-112">Increasing connection timeout and implementing connection retry logic will increase the probability that an application will connect to an availability group.</span></span> <span data-ttu-id="d9f9c-113">此外，由于故障转移可能会使连接失败，因此请实现连接重试逻辑；重试失败的连接直至重新连接。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-113">Also, because a connection can fail because of a failover, you should implement connection retry logic, retrying a failed connection until it reconnects.</span></span>  
  
 <span data-ttu-id="d9f9c-114">以下连接属性已添加到 .NET Framework 4.5 中的 SqlClient：</span><span class="sxs-lookup"><span data-stu-id="d9f9c-114">The following connection properties were added to SqlClient in .NET Framework 4.5:</span></span>  
  
- `ApplicationIntent`  
  
- `MultiSubnetFailover`  
  
 <span data-ttu-id="d9f9c-115">可以通过编程方式修改这些连接字符串关键字：</span><span class="sxs-lookup"><span data-stu-id="d9f9c-115">You can programmatically modify these connection string keywords with:</span></span>  
  
1. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ApplicationIntent%2A>  
  
2. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A>  

> [!NOTE]
> <span data-ttu-id="d9f9c-116">`MultiSubnetFailover` `true` .NET Framework 4.6.1 或更高版本不需要将设置为。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-116">Setting `MultiSubnetFailover` to `true` isn't required with .NET Framework 4.6.1 or later versions.</span></span>
  
## <a name="connecting-with-multisubnetfailover"></a><span data-ttu-id="d9f9c-117">使用 MultiSubnetFailover 进行连接</span><span class="sxs-lookup"><span data-stu-id="d9f9c-117">Connecting With MultiSubnetFailover</span></span>  
 <span data-ttu-id="d9f9c-118">在连接到 SQL Server 2012 可用性组侦听器或 SQL Server 2012 故障转移群集实例时，应始终指定 `MultiSubnetFailover=True`。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-118">Always specify `MultiSubnetFailover=True` when connecting to a SQL Server 2012 availability group listener or SQL Server 2012 Failover Cluster Instance.</span></span> <span data-ttu-id="d9f9c-119">`MultiSubnetFailover` 可加快 SQL Server 2012 中所有可用性组和故障转移群集实例的故障转移速度，并且将显著缩短单子网和多子网 AlwaysOn 拓扑的故障转移时间。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-119">`MultiSubnetFailover` enables faster failover for all Availability Groups and or Failover Cluster Instance in SQL Server 2012 and will significantly reduce failover time for single and multi-subnet AlwaysOn topologies.</span></span> <span data-ttu-id="d9f9c-120">在多子网故障转移过程中，客户端将尝试并行进行连接。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-120">During a multi-subnet failover, the client will attempt connections in parallel.</span></span> <span data-ttu-id="d9f9c-121">在子网故障转移过程中，将会主动重试 TCP 连接。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-121">During a subnet failover, will aggressively retry the TCP connection.</span></span>  
  
 <span data-ttu-id="d9f9c-122">`MultiSubnetFailover` 连接属性指示应用程序将部署到可用性组或 SQL Server 2012 故障转移群集实例，并且 SqlClient 将通过连接到所有的 IP 地址尝试连接到主 SQL Server 实例上的数据库。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-122">The `MultiSubnetFailover` connection property indicates that the application is being deployed in an availability group or SQL Server 2012 Failover Cluster Instance and that SqlClient will try to connect to the database on the primary SQL Server instance by trying to connect to all the IP addresses.</span></span> <span data-ttu-id="d9f9c-123">为连接指定 `MultiSubnetFailover=True` 后，客户端将在比操作系统的默认 TCP 重传间隔更短的时间内重试 TCP 连接尝试。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-123">When `MultiSubnetFailover=True` is specified for a connection, the client retries TCP connection attempts faster than the operating system’s default TCP retransmit intervals.</span></span> <span data-ttu-id="d9f9c-124">这样，就可以在对 AlwaysOn 可用性组或 AlwaysOn 故障转移群集实例执行故障转移之后更快地进行重新连接，这一点同时适用于单子网和多子网可用性组和故障转移群集实例。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-124">This enables faster reconnection after failover of either an AlwaysOn Availability Group or an AlwaysOn Failover Cluster Instance, and is applicable to both single- and multi-subnet Availability Groups and Failover Cluster Instances.</span></span>  
  
 <span data-ttu-id="d9f9c-125">有关 SqlClient 中的连接字符串关键字的详细信息，请参阅 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-125">For more information about connection string keywords in SqlClient, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="d9f9c-126">如果在连接到除可用性组侦听程序或 SQL Server 2012 故障转移群集实例之外的对象时指定 `MultiSubnetFailover=True`，可能导致性能下降，因此不支持这样做。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-126">Specifying `MultiSubnetFailover=True` when connecting to something other than a availability group listener or SQL Server 2012 Failover Cluster Instance may result in a negative performance impact, and is not supported.</span></span>  
  
 <span data-ttu-id="d9f9c-127">使用以下准则可以连接到可用性组或 SQL Server 2012 故障转移群集实例中的服务器：</span><span class="sxs-lookup"><span data-stu-id="d9f9c-127">Use the following guidelines to connect to a server in an availability group or SQL Server 2012 Failover Cluster Instance:</span></span>  
  
- <span data-ttu-id="d9f9c-128">在连接到单子网或多子网时使用 `MultiSubnetFailover` 连接属性；这将改进这两者的性能。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-128">Use the `MultiSubnetFailover` connection property when connecting to a single subnet or multi-subnet; it will improve performance for both.</span></span>  
  
- <span data-ttu-id="d9f9c-129">若要连接到某一可用性组，请在您的连接字符串中将该可用性组的可用性组侦听器指定为服务器。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-129">To connect to an availability group, specify the availability group listener of the availability group as the server in your connection string.</span></span>  
  
- <span data-ttu-id="d9f9c-130">连接到配置有超过 64 个 IP 地址的 SQL Server 实例将导致连接失败。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-130">Connecting to a SQL Server instance configured with more than 64 IP addresses will cause a connection failure.</span></span>  
  
- <span data-ttu-id="d9f9c-131">基于以下身份验证类型，使用 `MultiSubnetFailover` 连接属性的应用程序的行为将不会受到影响：SQL Server 身份验证、Kerberos 身份验证或 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-131">Behavior of an application that uses the `MultiSubnetFailover` connection property is not affected based on the type of authentication: SQL Server Authentication, Kerberos Authentication, or Windows Authentication.</span></span>  
  
- <span data-ttu-id="d9f9c-132">延长 `Connect Timeout` 的值可调整故障转移时间，减少应用程序连接重试次数。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-132">Increase the value of `Connect Timeout` to accommodate for failover time and reduce application connection retry attempts.</span></span>  
  
- <span data-ttu-id="d9f9c-133">不支持分布式事务。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-133">Distributed transactions are not supported.</span></span>  
  
 <span data-ttu-id="d9f9c-134">如果只读路由不起作用，则连接到次要副本位置在以下情况下将失败：</span><span class="sxs-lookup"><span data-stu-id="d9f9c-134">If read-only routing is not in effect, connecting to a secondary replica location will fail in the following situations:</span></span>  
  
1. <span data-ttu-id="d9f9c-135">如果未将辅助副本位置配置为接受连接。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-135">If the secondary replica location is not configured to accept connections.</span></span>  
  
2. <span data-ttu-id="d9f9c-136">如果应用程序使用 `ApplicationIntent=ReadWrite`（在下面论述）且将辅助副本位置配置为只读访问。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-136">If an application uses `ApplicationIntent=ReadWrite` (discussed below) and the secondary replica location is configured for read-only access.</span></span>  
  
 <span data-ttu-id="d9f9c-137">只读辅助副本不支持 <xref:System.Data.SqlClient.SqlDependency>。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-137"><xref:System.Data.SqlClient.SqlDependency> is not supported on read-only secondary replicas.</span></span>  
  
 <span data-ttu-id="d9f9c-138">如果将主副本配置为拒绝只读工作负荷且连接字符串包含 `ApplicationIntent=ReadOnly`，连接将失败。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-138">A connection will fail if a primary replica is configured to reject read-only workloads and the connection string contains `ApplicationIntent=ReadOnly`.</span></span>  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a><span data-ttu-id="d9f9c-139">升级以便使用来自数据库镜像的多子网群集</span><span class="sxs-lookup"><span data-stu-id="d9f9c-139">Upgrading to Use Multi-Subnet Clusters from Database Mirroring</span></span>  
 <span data-ttu-id="d9f9c-140">如果连接字符串中已存在 `MultiSubnetFailover` 和 `Failover Partner` 连接关键字，或者如果使用了 `MultiSubnetFailover=True` 和除 TCP 以外的其他协议，将出现连接错误 (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-140">A connection error (<xref:System.ArgumentException>) will occur if the `MultiSubnetFailover` and `Failover Partner` connection keywords are present in the connection string, or if `MultiSubnetFailover=True` and a protocol other than TCP is used.</span></span> <span data-ttu-id="d9f9c-141">如果使用 `MultiSubnetFailover` 且 SQL Server 返回一个故障转移伙伴响应指示它是数据库镜像对的一部分，也将出现错误 (<xref:System.Data.SqlClient.SqlException>)。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-141">An error (<xref:System.Data.SqlClient.SqlException>) will also occur if `MultiSubnetFailover` is used and the SQL Server returns a failover partner response indicating it is part of a database mirroring pair.</span></span>  
  
 <span data-ttu-id="d9f9c-142">如果你将当前使用数据库镜像的 SqlClient 应用程序升级到多子网方案，则应删除 `Failover Partner` 连接属性并使用设置为 `True` 的 `MultiSubnetFailover` 替换它，并且还应使用可用性组侦听程序替换连接字符串中的服务器名称。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-142">If you upgrade a SqlClient application that currently uses database mirroring to a multi-subnet scenario, you should remove the `Failover Partner` connection property and replace it with `MultiSubnetFailover` set to `True` and replace the server name in the connection string with an availability group listener.</span></span> <span data-ttu-id="d9f9c-143">如果连接字符串使用 `Failover Partner` 和 `MultiSubnetFailover=True`，则驱动程序将生成错误。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-143">If a connection string uses `Failover Partner` and `MultiSubnetFailover=True`, the driver will generate an error.</span></span> <span data-ttu-id="d9f9c-144">但是，如果连接字符串使用 `Failover Partner` 和 `MultiSubnetFailover=False`（或 `ApplicationIntent=ReadWrite`），则应用程序将使用数据库镜像。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-144">However, if a connection string uses `Failover Partner` and `MultiSubnetFailover=False` (or `ApplicationIntent=ReadWrite`), the application will use database mirroring.</span></span>  
  
 <span data-ttu-id="d9f9c-145">如果在 AG 的主数据库中使用数据库镜像，同时在连接到主数据库而不是可用性组侦听程序的连接字符串中使用 `MultiSubnetFailover=True`，则驱动程序将返回一条错误。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-145">The driver will return an error if database mirroring is used on the primary database in the AG, and if `MultiSubnetFailover=True` is used in the connection string that connects to a primary database instead of to an availability group listener.</span></span>  
  
## <a name="specifying-application-intent"></a><span data-ttu-id="d9f9c-146">指定应用程序意向</span><span class="sxs-lookup"><span data-stu-id="d9f9c-146">Specifying Application Intent</span></span>  
 <span data-ttu-id="d9f9c-147">如果 `ApplicationIntent=ReadOnly`，在连接到某一启用了 AlwaysOn 的数据库时，客户端将请求读取工作负荷。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-147">When `ApplicationIntent=ReadOnly`, the client requests a read workload when connecting to an AlwaysOn enabled database.</span></span> <span data-ttu-id="d9f9c-148">服务器在连接时和在执行 USE 数据库语句的过程中将强制该意向，但仅针对启用了 AlwaysOn 的数据库。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-148">The server will enforce the intent at connection time and during a USE database statement but only to an Always On enabled database.</span></span>  
  
 <span data-ttu-id="d9f9c-149">`ApplicationIntent` 关键字不适用于早期的只读数据库。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-149">The `ApplicationIntent` keyword does not work with legacy, read-only databases.</span></span>  
  
 <span data-ttu-id="d9f9c-150">数据库可允许或禁止目标 AlwaysOn 数据库上的读取工作负荷。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-150">A database can allow or disallow read workloads on the targeted AlwaysOn database.</span></span> <span data-ttu-id="d9f9c-151">（这是通过 `PRIMARY_ROLE` 和 `SECONDARY_ROLE`Transact-SQL 语句的 `ALLOW_CONNECTIONS` 子句实现的。）</span><span class="sxs-lookup"><span data-stu-id="d9f9c-151">(This is done with the `ALLOW_CONNECTIONS` clause of the `PRIMARY_ROLE` and `SECONDARY_ROLE`Transact-SQL statements.)</span></span>  
  
 <span data-ttu-id="d9f9c-152">`ApplicationIntent` 关键字用于启用只读路由。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-152">The `ApplicationIntent` keyword is used to enable read-only routing.</span></span>  
  
## <a name="read-only-routing"></a><span data-ttu-id="d9f9c-153">只读路由</span><span class="sxs-lookup"><span data-stu-id="d9f9c-153">Read-Only Routing</span></span>  
 <span data-ttu-id="d9f9c-154">只读路由是一项可确保数据库只读副本的可用性的功能。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-154">Read-only routing is a feature that can ensure the availability of a read only replica of a database.</span></span> <span data-ttu-id="d9f9c-155">启用只读路由：</span><span class="sxs-lookup"><span data-stu-id="d9f9c-155">To enable read-only routing:</span></span>  
  
1. <span data-ttu-id="d9f9c-156">您必须连接到某一 AlwaysOn 可用性组侦听器。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-156">You must connect to an Always On Availability Group availability group listener.</span></span>  
  
2. <span data-ttu-id="d9f9c-157">`ApplicationIntent` 连接字符串关键字必须设置为 `ReadOnly`。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-157">The `ApplicationIntent` connection string keyword must be set to `ReadOnly`.</span></span>  
  
3. <span data-ttu-id="d9f9c-158">数据库管理员必须配置该可用性组以便启用只读路由。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-158">The Availability Group must be configured by the database administrator to enable read-only routing.</span></span>  
  
 <span data-ttu-id="d9f9c-159">使用只读路由的多个连接可能不会全部连接到相同的只读副本。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-159">It is possible that multiple connections using read-only routing will not all connect to the same read-only replica.</span></span> <span data-ttu-id="d9f9c-160">对数据库同步进行更改或对服务器的路由配置进行更改可能导致客户端连接到不同的只读副本。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-160">Changes in database synchronization or changes in the server's routing configuration can result in client connections to different read-only replicas.</span></span> <span data-ttu-id="d9f9c-161">若要确保所有只读请求都连接到相同的只读副本，请勿将可用性组侦听器传递到 `Data Source` 连接字符串关键字。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-161">To ensure that all read-only requests connect to the same read-only replica, do not pass an availability group listener to the `Data Source` connection string keyword.</span></span> <span data-ttu-id="d9f9c-162">而是指定只读实例的名称。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-162">Instead, specify the name of the read-only instance.</span></span>  
  
 <span data-ttu-id="d9f9c-163">只读路由所用的时间可能会长于连接到主副本的时间，因为只读路由首先连接到主副本，然后查找可用的最佳可读取辅助副本。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-163">Read-only routing may take longer than connecting to the primary because read only routing first connects to the primary and then looks for the best available readable secondary.</span></span> <span data-ttu-id="d9f9c-164">为此，应增加您的登录超时。</span><span class="sxs-lookup"><span data-stu-id="d9f9c-164">Because of this, you should increase your login timeout.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9f9c-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d9f9c-165">See also</span></span>

- [<span data-ttu-id="d9f9c-166">SQL Server 功能和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d9f9c-166">SQL Server Features and ADO.NET</span></span>](sql-server-features-and-adonet.md)
- [<span data-ttu-id="d9f9c-167">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="d9f9c-167">ADO.NET Overview</span></span>](../ado-net-overview.md)

---
title: 启用多个活动结果集
description: 了解如何在连接字符串中启用/禁用 MARS，这与 SQL Server 一起使用，以便可以在 ADO.NET 中的单个连接上运行多个批处理。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 576079e4-debe-4ab5-9204-fcbe2ca7a5e2
ms.openlocfilehash: 0c5b4043b389c7dde39a477f90e82bbf654331f7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156246"
---
# <a name="enabling-multiple-active-result-sets"></a><span data-ttu-id="859ff-103">启用多个活动结果集</span><span class="sxs-lookup"><span data-stu-id="859ff-103">Enabling Multiple Active Result Sets</span></span>

<span data-ttu-id="859ff-104">多重活动结果集 (MARS) 是一项用于 SQL Server 的功能，可用来对单个连接执行多个批处理。</span><span class="sxs-lookup"><span data-stu-id="859ff-104">Multiple Active Result Sets (MARS) is a feature that works with SQL Server to allow the execution of multiple batches on a single connection.</span></span> <span data-ttu-id="859ff-105">如果对 SQL Server 启用了 MARS，使用的每个命令对象都将向该连接添加一个会话。</span><span class="sxs-lookup"><span data-stu-id="859ff-105">When MARS is enabled for use with SQL Server, each command object used adds a session to the connection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="859ff-106">单个 MARS 会话打开一个供 MARS 使用的逻辑连接，然后为每个活动命令打开一个逻辑连接。</span><span class="sxs-lookup"><span data-stu-id="859ff-106">A single MARS session opens one logical connection for MARS to use and then one logical connection for each active command.</span></span>  
  
## <a name="enabling-and-disabling-mars-in-the-connection-string"></a><span data-ttu-id="859ff-107">在连接字符串中启用和禁用 MARS</span><span class="sxs-lookup"><span data-stu-id="859ff-107">Enabling and Disabling MARS in the Connection String</span></span>  
  
> [!NOTE]
> <span data-ttu-id="859ff-108">下列连接字符串使用随 SQL Server 提供的 AdventureWorks 示例数据库\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="859ff-108">The following connection strings use the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="859ff-109">提供的连接字符串假定数据库安装在名为 MSSQL1 的服务器上。</span><span class="sxs-lookup"><span data-stu-id="859ff-109">The connection strings provided assume that the database is installed on a server named MSSQL1.</span></span> <span data-ttu-id="859ff-110">根据环境需要修改连接字符串。</span><span class="sxs-lookup"><span data-stu-id="859ff-110">Modify the connection string as necessary for your environment.</span></span>  
  
 <span data-ttu-id="859ff-111">默认情况下，MARS 功能处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="859ff-111">The MARS feature is disabled by default.</span></span> <span data-ttu-id="859ff-112">可以通过将“MultipleActiveResultSets=True”关键字对添加到连接字符串来启用它。</span><span class="sxs-lookup"><span data-stu-id="859ff-112">It can be enabled by adding the "MultipleActiveResultSets=True" keyword pair to your connection string.</span></span> <span data-ttu-id="859ff-113">“True”是启用 MARS 的唯一有效值。</span><span class="sxs-lookup"><span data-stu-id="859ff-113">"True" is the only valid value for enabling MARS.</span></span> <span data-ttu-id="859ff-114">下面的示例演示如何连接到 SQL Server 的实例以及如何指定是否应启用 MARS。</span><span class="sxs-lookup"><span data-stu-id="859ff-114">The following example demonstrates how to connect to an instance of SQL Server and how to specify that MARS should be enabled.</span></span>  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=True"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=True";  
```  
  
 <span data-ttu-id="859ff-115">可以通过将“MultipleActiveResultSets=False”关键字对添加到连接字符串来禁用 MARS。</span><span class="sxs-lookup"><span data-stu-id="859ff-115">You can disable MARS by adding the "MultipleActiveResultSets=False" keyword pair to your connection string.</span></span> <span data-ttu-id="859ff-116">“False”是禁用 MARS 的唯一有效值。</span><span class="sxs-lookup"><span data-stu-id="859ff-116">"False" is the only valid value for disabling MARS.</span></span> <span data-ttu-id="859ff-117">以下连接字符串演示了如何禁用 MARS。</span><span class="sxs-lookup"><span data-stu-id="859ff-117">The following connection string demonstrates how to disable MARS.</span></span>  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=False"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=False";  
```  
  
## <a name="special-considerations-when-using-mars"></a><span data-ttu-id="859ff-118">使用 MARS 时的特殊注意事项</span><span class="sxs-lookup"><span data-stu-id="859ff-118">Special Considerations When Using MARS</span></span>  

 <span data-ttu-id="859ff-119">通常，现有应用程序无需修改即可使用启用 MARS 的连接。</span><span class="sxs-lookup"><span data-stu-id="859ff-119">In general, existing applications should not need modification to use a MARS-enabled connection.</span></span> <span data-ttu-id="859ff-120">但是，如果希望在应用程序中使用 MARS 功能，则应了解以下特殊注意事项。</span><span class="sxs-lookup"><span data-stu-id="859ff-120">However, if you wish to use MARS features in your applications, you should understand the following special considerations.</span></span>  
  
### <a name="statement-interleaving"></a><span data-ttu-id="859ff-121">语句交替</span><span class="sxs-lookup"><span data-stu-id="859ff-121">Statement Interleaving</span></span>  

 <span data-ttu-id="859ff-122">MARS 操作在服务器上同步执行。</span><span class="sxs-lookup"><span data-stu-id="859ff-122">MARS operations execute synchronously on the server.</span></span> <span data-ttu-id="859ff-123">允许 SELECT 和 BULK INSERT 语句的语句交错。</span><span class="sxs-lookup"><span data-stu-id="859ff-123">Statement interleaving of SELECT and BULK INSERT statements is allowed.</span></span> <span data-ttu-id="859ff-124">但是，数据操作语言 (DML) 和数据定义语言 (DDL) 语句是以原子方式执行的。</span><span class="sxs-lookup"><span data-stu-id="859ff-124">However, data manipulation language (DML) and data definition language (DDL) statements execute atomically.</span></span> <span data-ttu-id="859ff-125">在执行原子批处理时，无法尝试执行任何语句。</span><span class="sxs-lookup"><span data-stu-id="859ff-125">Any statements attempting to execute while an atomic batch is executing are blocked.</span></span> <span data-ttu-id="859ff-126">服务器上的并发执行不是 MARS 功能。</span><span class="sxs-lookup"><span data-stu-id="859ff-126">Parallel execution at the server is not a MARS feature.</span></span>  
  
 <span data-ttu-id="859ff-127">如果在 MARS 连接下提交了两个批处理，其中一个包含 SELECT 语句，另一个包含 DML 语句，则可以在 SELECT 语句执行期间开始执行 DML。</span><span class="sxs-lookup"><span data-stu-id="859ff-127">If two batches are submitted under a MARS connection, one of them containing a SELECT statement, the other containing a DML statement, the DML can begin execution within execution of the SELECT statement.</span></span> <span data-ttu-id="859ff-128">但是，DML 语句必须先运行到完成，SELECT 语句才能取得进展。</span><span class="sxs-lookup"><span data-stu-id="859ff-128">However, the DML statement must run to completion before the SELECT statement can make progress.</span></span> <span data-ttu-id="859ff-129">如果两个语句都在同一事务下运行，那么在 SELECT 语句开始执行之后 DML 语句所做的任何更改对于读取操作都是不可见的。</span><span class="sxs-lookup"><span data-stu-id="859ff-129">If both statements are running under the same transaction, any changes made by a DML statement after the SELECT statement has started execution are not visible to the read operation.</span></span>  
  
 <span data-ttu-id="859ff-130">SELECT 语句中的 WAITFOR 语句在等待时（即直到生成第一行之前）不会产生事务。</span><span class="sxs-lookup"><span data-stu-id="859ff-130">A WAITFOR statement inside a SELECT statement does not yield the transaction while it is waiting, that is, until the first row is produced.</span></span> <span data-ttu-id="859ff-131">这意味着在等待 WAITFOR 语句时，其他批处理都无法在同一连接内执行。</span><span class="sxs-lookup"><span data-stu-id="859ff-131">This implies that no other batches can execute within the same connection while a WAITFOR statement is waiting.</span></span>  
  
### <a name="mars-session-cache"></a><span data-ttu-id="859ff-132">MARS 会话缓存</span><span class="sxs-lookup"><span data-stu-id="859ff-132">MARS Session Cache</span></span>  

 <span data-ttu-id="859ff-133">在启用 MARS 的情况下打开连接时，将创建逻辑会话，这会增加额外的开销。</span><span class="sxs-lookup"><span data-stu-id="859ff-133">When a connection is opened with MARS enabled, a logical session is created, which adds additional overhead.</span></span> <span data-ttu-id="859ff-134">为了将系统开销降至最低并提高性能，SqlClient 将 MARS 会话缓存在连接内\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="859ff-134">To minimize overhead and enhance performance, **SqlClient** caches the MARS session within a connection.</span></span> <span data-ttu-id="859ff-135">缓存最多包含 10 个 MARS 会话。</span><span class="sxs-lookup"><span data-stu-id="859ff-135">The cache contains at most 10 MARS sessions.</span></span> <span data-ttu-id="859ff-136">该值不是用户可调节的。</span><span class="sxs-lookup"><span data-stu-id="859ff-136">This value is not user adjustable.</span></span> <span data-ttu-id="859ff-137">如果达到会话限制，则会创建一个新会话，而不会生成错误。</span><span class="sxs-lookup"><span data-stu-id="859ff-137">If the session limit is reached, a new session is created—an error is not generated.</span></span> <span data-ttu-id="859ff-138">其中包含的缓存和会话是按连接进行的；它们不会在连接之间共享。</span><span class="sxs-lookup"><span data-stu-id="859ff-138">The cache and sessions contained in it are per-connection; they are not shared across connections.</span></span> <span data-ttu-id="859ff-139">发布会话时，会将其返回到池中，除非已达到池的上限。</span><span class="sxs-lookup"><span data-stu-id="859ff-139">When a session is released, it is returned to the pool unless the pool's upper limit has been reached.</span></span> <span data-ttu-id="859ff-140">如果缓存池已满，则会话将关闭。</span><span class="sxs-lookup"><span data-stu-id="859ff-140">If the cache pool is full, the session is closed.</span></span> <span data-ttu-id="859ff-141">MARS 会话不会过期。</span><span class="sxs-lookup"><span data-stu-id="859ff-141">MARS sessions do not expire.</span></span> <span data-ttu-id="859ff-142">仅在处置连接对象时，才清理这些会话。</span><span class="sxs-lookup"><span data-stu-id="859ff-142">They are only cleaned up when the connection object is disposed.</span></span> <span data-ttu-id="859ff-143">MARS 会话缓存未预加载。</span><span class="sxs-lookup"><span data-stu-id="859ff-143">The MARS session cache is not preloaded.</span></span> <span data-ttu-id="859ff-144">已加载它，因为应用程序需要更多会话。</span><span class="sxs-lookup"><span data-stu-id="859ff-144">It is loaded as the application requires more sessions.</span></span>  
  
### <a name="thread-safety"></a><span data-ttu-id="859ff-145">线程安全性</span><span class="sxs-lookup"><span data-stu-id="859ff-145">Thread Safety</span></span>  

 <span data-ttu-id="859ff-146">MARS 操作不是线程安全的。</span><span class="sxs-lookup"><span data-stu-id="859ff-146">MARS operations are not thread-safe.</span></span>  
  
### <a name="connection-pooling"></a><span data-ttu-id="859ff-147">连接池</span><span class="sxs-lookup"><span data-stu-id="859ff-147">Connection Pooling</span></span>  

 <span data-ttu-id="859ff-148">启用了 MARS 的连接像其他任何连接一样共用。</span><span class="sxs-lookup"><span data-stu-id="859ff-148">MARS-enabled connections are pooled like any other connection.</span></span> <span data-ttu-id="859ff-149">如果应用程序打开两个连接，一个启用了 MARS，一个禁用了 MARS，则两个连接位于不同的池中。</span><span class="sxs-lookup"><span data-stu-id="859ff-149">If an application opens two connections, one with MARS enabled and one with MARS disabled, the two connections are in separate pools.</span></span> <span data-ttu-id="859ff-150">有关详细信息，请参阅 [SQL Server 连接池 (ADO.NET)](../sql-server-connection-pooling.md)。</span><span class="sxs-lookup"><span data-stu-id="859ff-150">For more information, see [SQL Server Connection Pooling (ADO.NET)](../sql-server-connection-pooling.md).</span></span>  
  
### <a name="sql-server-batch-execution-environment"></a><span data-ttu-id="859ff-151">SQL Server 批处理执行环境</span><span class="sxs-lookup"><span data-stu-id="859ff-151">SQL Server Batch Execution Environment</span></span>  

 <span data-ttu-id="859ff-152">打开连接时，将定义默认环境。</span><span class="sxs-lookup"><span data-stu-id="859ff-152">When a connection is opened, a default environment is defined.</span></span> <span data-ttu-id="859ff-153">然后，将此环境复制到逻辑 MARS 会话中。</span><span class="sxs-lookup"><span data-stu-id="859ff-153">This environment is then copied into a logical MARS session.</span></span>  
  
 <span data-ttu-id="859ff-154">批处理执行环境包括以下组件：</span><span class="sxs-lookup"><span data-stu-id="859ff-154">The batch execution environment includes the following components:</span></span>  
  
- <span data-ttu-id="859ff-155">Set 选项（例如，ANSI_NULLS、DATE_FORMAT、LANGUAGE、TEXTSIZE）</span><span class="sxs-lookup"><span data-stu-id="859ff-155">Set options (for example, ANSI_NULLS, DATE_FORMAT, LANGUAGE, TEXTSIZE)</span></span>  
  
- <span data-ttu-id="859ff-156">安全性上下文（用户/应用程序角色）</span><span class="sxs-lookup"><span data-stu-id="859ff-156">Security context (user/application role)</span></span>  
  
- <span data-ttu-id="859ff-157">数据库上下文（当前数据库）</span><span class="sxs-lookup"><span data-stu-id="859ff-157">Database context (current database)</span></span>  
  
- <span data-ttu-id="859ff-158">执行状态变量（例如，@@ERROR、@@ROWCOUNT、@@FETCH_STATUS、@@IDENTITY）</span><span class="sxs-lookup"><span data-stu-id="859ff-158">Execution state variables (for example, @@ERROR, @@ROWCOUNT, @@FETCH_STATUS @@IDENTITY)</span></span>  
  
- <span data-ttu-id="859ff-159">顶级临时表</span><span class="sxs-lookup"><span data-stu-id="859ff-159">Top-level temporary tables</span></span>  
  
 <span data-ttu-id="859ff-160">借助 MARS，将默认执行环境与连接关联起来。</span><span class="sxs-lookup"><span data-stu-id="859ff-160">With MARS, a default execution environment is associated to a connection.</span></span> <span data-ttu-id="859ff-161">在特定连接下开始执行的每个新批处理都将接收默认环境的一个副本。</span><span class="sxs-lookup"><span data-stu-id="859ff-161">Every new batch that starts executing under a given connection receives a copy of the default environment.</span></span> <span data-ttu-id="859ff-162">每当在给定的批处理下执行代码时，对环境所做的所有更改都将限制在特定的批处理范围内。</span><span class="sxs-lookup"><span data-stu-id="859ff-162">Whenever code is executed under a given batch, all changes made to the environment are scoped to the specific batch.</span></span> <span data-ttu-id="859ff-163">执行完成后，执行设置将复制到默认环境中。</span><span class="sxs-lookup"><span data-stu-id="859ff-163">Once execution finishes, the execution settings are copied into the default environment.</span></span> <span data-ttu-id="859ff-164">如果一个批处理发出多个要在同一事务下按顺序执行的命令，语义将与早期客户端或服务器中涉及的连接所显示出来的语义相同。</span><span class="sxs-lookup"><span data-stu-id="859ff-164">In the case of a single batch issuing several commands to be executed sequentially under the same transaction, semantics are the same as those exposed by connections involving earlier clients or servers.</span></span>  
  
### <a name="parallel-execution"></a><span data-ttu-id="859ff-165">并行执行</span><span class="sxs-lookup"><span data-stu-id="859ff-165">Parallel Execution</span></span>  

 <span data-ttu-id="859ff-166">MARS 并非旨在删除对应用程序中多个连接的所有要求。</span><span class="sxs-lookup"><span data-stu-id="859ff-166">MARS is not designed to remove all requirements for multiple connections in an application.</span></span> <span data-ttu-id="859ff-167">如果应用程序需要对服务器执行真正的并发命令，则应使用多个连接。</span><span class="sxs-lookup"><span data-stu-id="859ff-167">If an application needs true parallel execution of commands against a server, multiple connections should be used.</span></span>  
  
 <span data-ttu-id="859ff-168">例如，考虑以下情况。</span><span class="sxs-lookup"><span data-stu-id="859ff-168">For example, consider the following scenario.</span></span> <span data-ttu-id="859ff-169">创建了两个命令对象，一个用于处理结果集，另一个用于更新数据；他们通过 MARS 共享公共连接。</span><span class="sxs-lookup"><span data-stu-id="859ff-169">Two command objects are created, one for processing a result set and another for updating data; they share a common connection via MARS.</span></span> <span data-ttu-id="859ff-170">在此方案中，`Transaction`.`Commit`</span><span class="sxs-lookup"><span data-stu-id="859ff-170">In this scenario, the `Transaction`.`Commit`</span></span> <span data-ttu-id="859ff-171">在更新时失败，直到在第一个命令对象上读取了所有结果，并生成以下异常：</span><span class="sxs-lookup"><span data-stu-id="859ff-171">fails on the update until all the results have been read on the first command object, yielding the following exception:</span></span>  
  
 <span data-ttu-id="859ff-172">消息：其他会话正在使用事务的上下文。</span><span class="sxs-lookup"><span data-stu-id="859ff-172">Message: Transaction context in use by another session.</span></span>  
  
 <span data-ttu-id="859ff-173">源： .NET SqlClient 数据提供程序</span><span class="sxs-lookup"><span data-stu-id="859ff-173">Source: .NET SqlClient Data Provider</span></span>  
  
 <span data-ttu-id="859ff-174">应为：(null)</span><span class="sxs-lookup"><span data-stu-id="859ff-174">Expected: (null)</span></span>  
  
 <span data-ttu-id="859ff-175">收到：System.Data.SqlClient.SqlException</span><span class="sxs-lookup"><span data-stu-id="859ff-175">Received: System.Data.SqlClient.SqlException</span></span>  
  
 <span data-ttu-id="859ff-176">有两种用于处理此方案的选项：</span><span class="sxs-lookup"><span data-stu-id="859ff-176">There are three options for handling this scenario:</span></span>  
  
1. <span data-ttu-id="859ff-177">创建读取器后，启动事务，以使其不属于事务。</span><span class="sxs-lookup"><span data-stu-id="859ff-177">Start the transaction after the reader is created, so that it is not part of the transaction.</span></span> <span data-ttu-id="859ff-178">然后，每次更新都将成为其自己的事务。</span><span class="sxs-lookup"><span data-stu-id="859ff-178">Every update then becomes its own transaction.</span></span>  
  
2. <span data-ttu-id="859ff-179">关闭读取器后，提交所有工作。</span><span class="sxs-lookup"><span data-stu-id="859ff-179">Commit all work after the reader is closed.</span></span> <span data-ttu-id="859ff-180">这可能会产生大量更新。</span><span class="sxs-lookup"><span data-stu-id="859ff-180">This has the potential for a substantial batch of updates.</span></span>  
  
3. <span data-ttu-id="859ff-181">不要使用 MARS；而是像在 MARS 之前那样为每个命令对象使用单独的连接。</span><span class="sxs-lookup"><span data-stu-id="859ff-181">Don't use MARS; instead use a separate connection for each command object as you would have before MARS.</span></span>  
  
### <a name="detecting-mars-support"></a><span data-ttu-id="859ff-182">检测 MARS 支持</span><span class="sxs-lookup"><span data-stu-id="859ff-182">Detecting MARS Support</span></span>  

 <span data-ttu-id="859ff-183">应用程序可以通过读取 `SqlConnection.ServerVersion` 值来检查 MARS 支持。</span><span class="sxs-lookup"><span data-stu-id="859ff-183">An application can check for MARS support by reading the `SqlConnection.ServerVersion` value.</span></span> <span data-ttu-id="859ff-184">SQL Server 2005 的主版本号为 9；SQL Server 2008 的主版本号为 10。</span><span class="sxs-lookup"><span data-stu-id="859ff-184">The major number should be 9 for SQL Server 2005 and 10 for SQL Server 2008.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="859ff-185">请参阅</span><span class="sxs-lookup"><span data-stu-id="859ff-185">See also</span></span>

- [<span data-ttu-id="859ff-186">多重活动结果集 (MARS)</span><span class="sxs-lookup"><span data-stu-id="859ff-186">Multiple Active Result Sets (MARS)</span></span>](multiple-active-result-sets-mars.md)
- [<span data-ttu-id="859ff-187">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="859ff-187">ADO.NET Overview</span></span>](../ado-net-overview.md)

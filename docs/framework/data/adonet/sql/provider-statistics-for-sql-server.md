---
title: 用于 SQL Server 的提供程序统计信息
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: 21bf7662094d5bc8948a1ce6378c454713cacc62
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183112"
---
# <a name="provider-statistics-for-sql-server"></a><span data-ttu-id="5a358-102">用于 SQL Server 的提供程序统计信息</span><span class="sxs-lookup"><span data-stu-id="5a358-102">Provider Statistics for SQL Server</span></span>

<span data-ttu-id="5a358-103">从 .NET Framework 2.0 版开始，适用于 SQL Server 的 .NET Framework 数据提供程序支持运行时统计信息。</span><span class="sxs-lookup"><span data-stu-id="5a358-103">Starting with the .NET Framework version 2.0, the .NET Framework Data Provider for SQL Server supports run-time statistics.</span></span> <span data-ttu-id="5a358-104">必须通过将 <xref:System.Data.SqlClient.SqlConnection> 对象的 <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> 属性设置为 `True` 来启用统计信息。</span><span class="sxs-lookup"><span data-stu-id="5a358-104">You must enable statistics by setting the <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object to `True` after you have a valid connection object created.</span></span> <span data-ttu-id="5a358-105">启用统计信息后，可以通过 <xref:System.Data.SqlClient.SqlConnection> 对象的 <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> 方法检索 <xref:System.Collections.IDictionary> 引用，以“即时快照”的方式查看统计信息。</span><span class="sxs-lookup"><span data-stu-id="5a358-105">After statistics are enabled, you can review them as a "snapshot in time" by retrieving an <xref:System.Collections.IDictionary> reference via the <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="5a358-106">可以将该列表枚举为一组名称/值对字典条目。</span><span class="sxs-lookup"><span data-stu-id="5a358-106">You enumerate through the list as a set of name/value pair dictionary entries.</span></span> <span data-ttu-id="5a358-107">这些名称/值对是无序的。</span><span class="sxs-lookup"><span data-stu-id="5a358-107">These name/value pairs are unordered.</span></span> <span data-ttu-id="5a358-108">随时都可以调用 <xref:System.Data.SqlClient.SqlConnection> 对象的 <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> 方法来重置计数器。</span><span class="sxs-lookup"><span data-stu-id="5a358-108">At any time, you can call the <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object to reset the counters.</span></span> <span data-ttu-id="5a358-109">如果尚未启用统计信息收集，则不会生成异常。</span><span class="sxs-lookup"><span data-stu-id="5a358-109">If statistic gathering has not been enabled, an exception is not generated.</span></span> <span data-ttu-id="5a358-110">此外，如果在未首先调用 <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> 的情况下调用 <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>，则检索的值是每个条目的初始值。</span><span class="sxs-lookup"><span data-stu-id="5a358-110">In addition, if <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> is called without <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> having been called first, the values retrieved are the initial values for each entry.</span></span> <span data-ttu-id="5a358-111">如果启用统计信息，请运行应用程序一段时间，然后禁用统计信息，检索到的值将反映收集的值，直到禁用统计信息为止。</span><span class="sxs-lookup"><span data-stu-id="5a358-111">If you enable statistics, run your application for a while, and then disable statistics, the values retrieved will reflect the values collected up to the point where statistics were disabled.</span></span> <span data-ttu-id="5a358-112">收集的所有统计值都基于每个连接。</span><span class="sxs-lookup"><span data-stu-id="5a358-112">All statistical values gathered are on a per-connection basis.</span></span>  
  
## <a name="statistical-values-available"></a><span data-ttu-id="5a358-113">可用的统计信息值</span><span class="sxs-lookup"><span data-stu-id="5a358-113">Statistical Values Available</span></span>  

 <span data-ttu-id="5a358-114">Microsoft SQL Server 提供程序中目前提供 18 个不同的项。</span><span class="sxs-lookup"><span data-stu-id="5a358-114">Currently there are 18 different items available from the Microsoft SQL Server provider.</span></span> <span data-ttu-id="5a358-115">可用的项数可以通过 <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> 返回的 <xref:System.Collections.IDictionary> 接口引用的 Count 属性进行访问\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5a358-115">The number of items available can be accessed via the **Count** property of the <xref:System.Collections.IDictionary> interface reference returned by <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>.</span></span> <span data-ttu-id="5a358-116">提供程序统计信息的所有计数器均使用公共语言运行时 <xref:System.Int64> 类型（C# 和 Visual Basic 中为 long），宽度为 64 位\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5a358-116">All of the counters for provider statistics use the common language runtime <xref:System.Int64> type (**long** in C# and Visual Basic), which is 64 bits wide.</span></span> <span data-ttu-id="5a358-117">int64 数据类型的最大值由 int64.MaxValue 字段定义，最大值为 ((2^63)-1))\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5a358-117">The maximum value of the **int64** data type, as defined by the **int64.MaxValue** field, is ((2^63)-1)).</span></span> <span data-ttu-id="5a358-118">当计数器的值达到此最大值时，它们将不再被认为是准确的。</span><span class="sxs-lookup"><span data-stu-id="5a358-118">When the values for the counters reach this maximum value, they should no longer be considered accurate.</span></span> <span data-ttu-id="5a358-119">这意味着 int64.MaxValue-1((2^63)-2) 实际上是任何统计信息的最大有效值\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5a358-119">This means that **int64.MaxValue**-1((2^63)-2) is effectively the greatest valid value for any statistic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5a358-120">字典用于返回提供程序统计信息，因为返回的统计信息的数量、名称和顺序可能会在将来发生变化。</span><span class="sxs-lookup"><span data-stu-id="5a358-120">A dictionary is used for returning provider statistics because the number, names and order of the returned statistics may change in the future.</span></span> <span data-ttu-id="5a358-121">应用程序不应依赖于在字典中找到的特定值，而应检查该值是否存在，并相应地设置分支。</span><span class="sxs-lookup"><span data-stu-id="5a358-121">Applications should not rely on a specific value being found in the dictionary, but should instead check whether the value is there and branch accordingly.</span></span>  
  
 <span data-ttu-id="5a358-122">下表显示了当前可用的统计值。</span><span class="sxs-lookup"><span data-stu-id="5a358-122">The following table describes the current statistical values available.</span></span> <span data-ttu-id="5a358-123">注意，在 Microsoft .NET Framework 的地区版本中，各个值的键名未本地化。</span><span class="sxs-lookup"><span data-stu-id="5a358-123">Note that the key names for the individual values are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="5a358-124">键名</span><span class="sxs-lookup"><span data-stu-id="5a358-124">Key Name</span></span>|<span data-ttu-id="5a358-125">描述</span><span class="sxs-lookup"><span data-stu-id="5a358-125">Description</span></span>|  
|--------------|-----------------|  
|`BuffersReceived`|<span data-ttu-id="5a358-126">返回应用程序开始使用提供程序并启用统计信息后，提供程序从 SQL Server 接收到的表格格式数据流 (TDS) 数据包的数量。</span><span class="sxs-lookup"><span data-stu-id="5a358-126">Returns the number of tabular data stream (TDS) packets received by the provider from SQL Server after the application has started using the provider and has enabled statistics.</span></span>|  
|`BuffersSent`|<span data-ttu-id="5a358-127">返回启用了统计信息之后，提供程序向 SQL Server 发送的 TDS 数据包的数量。</span><span class="sxs-lookup"><span data-stu-id="5a358-127">Returns the number of TDS packets sent to SQL Server by the provider after statistics have been enabled.</span></span> <span data-ttu-id="5a358-128">如果命令较大，可能需要多个缓冲区。</span><span class="sxs-lookup"><span data-stu-id="5a358-128">Large commands can require multiple buffers.</span></span> <span data-ttu-id="5a358-129">例如，如果将较大的命令发送到服务器，并且它需要六个数据包，则将 `ServerRoundtrips` 增加 1，将 `BuffersSent` 增加 6。</span><span class="sxs-lookup"><span data-stu-id="5a358-129">For example, if a large command is sent to the server and it requires six packets, `ServerRoundtrips` is incremented by one and `BuffersSent` is incremented by six.</span></span>|  
|`BytesReceived`|<span data-ttu-id="5a358-130">返回在应用程序使用提供程序启动并启用了统计信息之后，提供程序从 SQL Server 接收的 TDS 数据包中的数据字节数。</span><span class="sxs-lookup"><span data-stu-id="5a358-130">Returns the number of bytes of data in the TDS packets received by the provider from SQL Server once the application has started using the provider and has enabled statistics.</span></span>|  
|`BytesSent`|<span data-ttu-id="5a358-131">返回在应用程序使用提供程序启动并启用了统计信息之后，发送到 SQL Server 的 TDS 数据包中的数据字节数。</span><span class="sxs-lookup"><span data-stu-id="5a358-131">Returns the number of bytes of data sent to SQL Server in TDS packets after the application has started using the provider and has enabled statistics.</span></span>|  
|`ConnectionTime`|<span data-ttu-id="5a358-132">连接在统计信息启用之后已打开的时间（如果在打开连接之前就启用了统计信息，则为总连接时间），以毫秒为单位。</span><span class="sxs-lookup"><span data-stu-id="5a358-132">The amount of time (in milliseconds) that the connection has been opened after statistics have been enabled (total connection time if statistics were enabled before opening the connection).</span></span>|  
|`CursorOpens`|<span data-ttu-id="5a358-133">返回在应用程序使用提供程序启动并启用了统计信息之后，通过连接打开游标的次数。</span><span class="sxs-lookup"><span data-stu-id="5a358-133">Returns the number of times a cursor was open through the connection once the application has started using the provider and has enabled statistics.</span></span><br /><br /> <span data-ttu-id="5a358-134">请注意，SELECT 语句返回的只读/仅转发结果不被视为游标，因此不会影响此计数器。</span><span class="sxs-lookup"><span data-stu-id="5a358-134">Note that read-only/forward-only results returned by SELECT statements are not considered cursors and thus do not affect this counter.</span></span>|  
|`ExecutionTime`|<span data-ttu-id="5a358-135">返回在启用统计信息之后，提供程序用于处理方面的累计时间（以毫秒为单位），包括等待服务器回复所用的时间以及执行提供程序本身的代码所用的时间。</span><span class="sxs-lookup"><span data-stu-id="5a358-135">Returns the cumulative amount of time (in milliseconds) that the provider has spent processing once statistics have been enabled, including the time spent waiting for replies from the server as well as the time spent executing code in the provider itself.</span></span><br /><br /> <span data-ttu-id="5a358-136">包含计时代码的类如下：</span><span class="sxs-lookup"><span data-stu-id="5a358-136">The classes that include timing code are:</span></span><br /><br /> <span data-ttu-id="5a358-137">SqlConnection</span><span class="sxs-lookup"><span data-stu-id="5a358-137">SqlConnection</span></span><br /><br /> <span data-ttu-id="5a358-138">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="5a358-138">SqlCommand</span></span><br /><br /> <span data-ttu-id="5a358-139">SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="5a358-139">SqlDataReader</span></span><br /><br /> <span data-ttu-id="5a358-140">SqlDataAdapter</span><span class="sxs-lookup"><span data-stu-id="5a358-140">SqlDataAdapter</span></span><br /><br /> <span data-ttu-id="5a358-141">SqlTransaction</span><span class="sxs-lookup"><span data-stu-id="5a358-141">SqlTransaction</span></span><br /><br /> <span data-ttu-id="5a358-142">SqlCommandBuilder</span><span class="sxs-lookup"><span data-stu-id="5a358-142">SqlCommandBuilder</span></span><br /><br /> <span data-ttu-id="5a358-143">为了尽可能减少性能关键成员数，不会对以下成员计时：</span><span class="sxs-lookup"><span data-stu-id="5a358-143">To keep performance-critical members as small as possible, the following members are not timed:</span></span><br /><br /> <span data-ttu-id="5a358-144">SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="5a358-144">SqlDataReader</span></span><br /><br /> <span data-ttu-id="5a358-145">this[] 运算符（所有重载）</span><span class="sxs-lookup"><span data-stu-id="5a358-145">this[] operator (all overloads)</span></span><br /><br /> <span data-ttu-id="5a358-146">GetBoolean</span><span class="sxs-lookup"><span data-stu-id="5a358-146">GetBoolean</span></span><br /><br /> <span data-ttu-id="5a358-147">GetChar</span><span class="sxs-lookup"><span data-stu-id="5a358-147">GetChar</span></span><br /><br /> <span data-ttu-id="5a358-148">GetDateTime</span><span class="sxs-lookup"><span data-stu-id="5a358-148">GetDateTime</span></span><br /><br /> <span data-ttu-id="5a358-149">GetDecimal</span><span class="sxs-lookup"><span data-stu-id="5a358-149">GetDecimal</span></span><br /><br /> <span data-ttu-id="5a358-150">GetDouble</span><span class="sxs-lookup"><span data-stu-id="5a358-150">GetDouble</span></span><br /><br /> <span data-ttu-id="5a358-151">GetFloat</span><span class="sxs-lookup"><span data-stu-id="5a358-151">GetFloat</span></span><br /><br /> <span data-ttu-id="5a358-152">GetGuid</span><span class="sxs-lookup"><span data-stu-id="5a358-152">GetGuid</span></span><br /><br /> <span data-ttu-id="5a358-153">GetInt16</span><span class="sxs-lookup"><span data-stu-id="5a358-153">GetInt16</span></span><br /><br /> <span data-ttu-id="5a358-154">GetInt32</span><span class="sxs-lookup"><span data-stu-id="5a358-154">GetInt32</span></span><br /><br /> <span data-ttu-id="5a358-155">GetInt64</span><span class="sxs-lookup"><span data-stu-id="5a358-155">GetInt64</span></span><br /><br /> <span data-ttu-id="5a358-156">GetName</span><span class="sxs-lookup"><span data-stu-id="5a358-156">GetName</span></span><br /><br /> <span data-ttu-id="5a358-157">GetOrdinal</span><span class="sxs-lookup"><span data-stu-id="5a358-157">GetOrdinal</span></span><br /><br /> <span data-ttu-id="5a358-158">GetSqlBinary</span><span class="sxs-lookup"><span data-stu-id="5a358-158">GetSqlBinary</span></span><br /><br /> <span data-ttu-id="5a358-159">GetSqlBoolean</span><span class="sxs-lookup"><span data-stu-id="5a358-159">GetSqlBoolean</span></span><br /><br /> <span data-ttu-id="5a358-160">GetSqlByte</span><span class="sxs-lookup"><span data-stu-id="5a358-160">GetSqlByte</span></span><br /><br /> <span data-ttu-id="5a358-161">GetSqlDateTime</span><span class="sxs-lookup"><span data-stu-id="5a358-161">GetSqlDateTime</span></span><br /><br /> <span data-ttu-id="5a358-162">GetSqlDecimal</span><span class="sxs-lookup"><span data-stu-id="5a358-162">GetSqlDecimal</span></span><br /><br /> <span data-ttu-id="5a358-163">GetSqlDouble</span><span class="sxs-lookup"><span data-stu-id="5a358-163">GetSqlDouble</span></span><br /><br /> <span data-ttu-id="5a358-164">GetSqlGuid</span><span class="sxs-lookup"><span data-stu-id="5a358-164">GetSqlGuid</span></span><br /><br /> <span data-ttu-id="5a358-165">GetSqlInt16</span><span class="sxs-lookup"><span data-stu-id="5a358-165">GetSqlInt16</span></span><br /><br /> <span data-ttu-id="5a358-166">GetSqlInt32</span><span class="sxs-lookup"><span data-stu-id="5a358-166">GetSqlInt32</span></span><br /><br /> <span data-ttu-id="5a358-167">GetSqlInt64</span><span class="sxs-lookup"><span data-stu-id="5a358-167">GetSqlInt64</span></span><br /><br /> <span data-ttu-id="5a358-168">GetSqlMoney</span><span class="sxs-lookup"><span data-stu-id="5a358-168">GetSqlMoney</span></span><br /><br /> <span data-ttu-id="5a358-169">GetSqlSingle</span><span class="sxs-lookup"><span data-stu-id="5a358-169">GetSqlSingle</span></span><br /><br /> <span data-ttu-id="5a358-170">GetSqlString</span><span class="sxs-lookup"><span data-stu-id="5a358-170">GetSqlString</span></span><br /><br /> <span data-ttu-id="5a358-171">GetString</span><span class="sxs-lookup"><span data-stu-id="5a358-171">GetString</span></span><br /><br /> <span data-ttu-id="5a358-172">IsDBNull</span><span class="sxs-lookup"><span data-stu-id="5a358-172">IsDBNull</span></span>|  
|`IduCount`|<span data-ttu-id="5a358-173">返回在应用程序使用提供程序启动并启用了统计信息之后，通过连接执行的 INSERT、DELETE 和 UPDATE 语句的总数。</span><span class="sxs-lookup"><span data-stu-id="5a358-173">Returns the total number of INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`IduRows`|<span data-ttu-id="5a358-174">返回在应用程序使用提供程序启动并启用了统计信息之后，受通过连接执行的 INSERT、DELETE 和 UPDATE 语句影响的行的总数。</span><span class="sxs-lookup"><span data-stu-id="5a358-174">Returns the total number of rows affected by INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`NetworkServerTime`|<span data-ttu-id="5a358-175">返回在应用程序使用提供程序启动并启用了统计信息之后，提供程序等待服务器回复所用的累计时间（以毫秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="5a358-175">Returns the cumulative amount of time (in milliseconds) that the provider spent waiting for replies from the server once the application has started using the provider and has enabled statistics.</span></span>|  
|`PreparedExecs`|<span data-ttu-id="5a358-176">返回在应用程序使用提供程序启动并启用了统计信息之后，通过连接执行的已准备命令数。</span><span class="sxs-lookup"><span data-stu-id="5a358-176">Returns the number of prepared commands executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`Prepares`|<span data-ttu-id="5a358-177">返回在应用程序使用提供程序启动并启用了统计信息之后，通过连接准备的语句数。</span><span class="sxs-lookup"><span data-stu-id="5a358-177">Returns the number of statements prepared through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`SelectCount`|<span data-ttu-id="5a358-178">返回在应用程序使用提供程序启动并启用了统计信息之后，通过连接执行的 SELECT 语句数。</span><span class="sxs-lookup"><span data-stu-id="5a358-178">Returns the number of SELECT statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="5a358-179">这包括用于从游标检索行的 FETCH 语句，当到达 <xref:System.Data.SqlClient.SqlDataReader> 的末尾时，将更新 SELECT 语句的计数。</span><span class="sxs-lookup"><span data-stu-id="5a358-179">This includes FETCH statements to retrieve rows from cursors, and the count for SELECT statements is updated when the end of a <xref:System.Data.SqlClient.SqlDataReader> is reached.</span></span>|  
|`SelectRows`|<span data-ttu-id="5a358-180">返回在应用程序使用提供程序启动并启用了统计信息之后选定的行数。</span><span class="sxs-lookup"><span data-stu-id="5a358-180">Returns the number of rows selected once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="5a358-181">此技术反映了由 SQL 语句生成的所有行，即使调用方并未真正占用这些行也是如此。</span><span class="sxs-lookup"><span data-stu-id="5a358-181">This counter reflects all the rows generated by SQL statements, even those that were not actually consumed by the caller.</span></span> <span data-ttu-id="5a358-182">例如，在读取整个结果集之前关闭数据读取器不会影响计数。</span><span class="sxs-lookup"><span data-stu-id="5a358-182">For example, closing a data reader before reading the entire result set would not affect the count.</span></span> <span data-ttu-id="5a358-183">这包括通过 FETCH 语句从游标中检索的行。</span><span class="sxs-lookup"><span data-stu-id="5a358-183">This includes the rows retrieved from cursors through FETCH statements.</span></span>|  
|`ServerRoundtrips`|<span data-ttu-id="5a358-184">返回在应用程序使用提供程序启动并启用了统计信息之后，连接将命令发送到服务器并收到回复的次数。</span><span class="sxs-lookup"><span data-stu-id="5a358-184">Returns the number of times the connection sent commands to the server and got a reply back once the application has started using the provider and has enabled statistics.</span></span>|  
|`SumResultSets`|<span data-ttu-id="5a358-185">返回在应用程序使用提供程序启动并启用了统计信息之后已使用的结果集的数目。</span><span class="sxs-lookup"><span data-stu-id="5a358-185">Returns the number of result sets that have been used once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="5a358-186">例如，这将包括返回到客户端的任何结果集。</span><span class="sxs-lookup"><span data-stu-id="5a358-186">For example this would include any result set returned to the client.</span></span> <span data-ttu-id="5a358-187">对于游标，每个提取或块提取操作都被视为独立的结果集。</span><span class="sxs-lookup"><span data-stu-id="5a358-187">For cursors, each fetch or block-fetch operation is considered an independent result set.</span></span>|  
|`Transactions`|<span data-ttu-id="5a358-188">返回在应用程序使用提供程序启动并启用了统计信息（包括回滚）后启动的用户事务数。</span><span class="sxs-lookup"><span data-stu-id="5a358-188">Returns the number of user transactions started once the application has started using the provider and has enabled statistics, including rollbacks.</span></span> <span data-ttu-id="5a358-189">如果在自动提交启用的情况下运行连接，则每个命令均被视为事务。</span><span class="sxs-lookup"><span data-stu-id="5a358-189">If a connection is running with auto commit on, each command is considered a transaction.</span></span><br /><br /> <span data-ttu-id="5a358-190">一旦执行 BEGIN TRAN 语句，此计数器就会增加事务计数，而无需考虑稍后是提交还是回滚事务。</span><span class="sxs-lookup"><span data-stu-id="5a358-190">This counter increments the transaction count as soon as a BEGIN TRAN statement is executed, regardless of whether the transaction is committed or rolled back later.</span></span>|  
|`UnpreparedExecs`|<span data-ttu-id="5a358-191">返回在应用程序使用提供程序启动并启用了统计信息之后，通过连接执行的未准备语句数。</span><span class="sxs-lookup"><span data-stu-id="5a358-191">Returns the number of unprepared statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
  
### <a name="retrieving-a-value"></a><span data-ttu-id="5a358-192">检索值</span><span class="sxs-lookup"><span data-stu-id="5a358-192">Retrieving a Value</span></span>  

 <span data-ttu-id="5a358-193">下面的控制台应用程序显示了如何启用连接的统计信息，检索四个单独的统计值并将它们写出到控制台窗口。</span><span class="sxs-lookup"><span data-stu-id="5a358-193">The following console application shows how to enable statistics on a connection, retrieve four individual statistic values, and write them out to the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5a358-194">下面的示例使用随 SQL Server 提供的 AdventureWorks 示例数据库\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5a358-194">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="5a358-195">示例代码中提供的连接字符串假定数据库已安装并且在本地计算机上可用。</span><span class="sxs-lookup"><span data-stu-id="5a358-195">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="5a358-196">根据环境需要修改连接字符串。</span><span class="sxs-lookup"><span data-stu-id="5a358-196">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      ' Retrieve a few individual values  
      ' related to the previous command.  
      Dim bytesReceived As Long = _  
          CLng(currentStatistics.Item("BytesReceived"))  
      Dim bytesSent As Long = _  
          CLng(currentStatistics.Item("BytesSent"))  
      Dim selectCount As Long = _  
          CLng(currentStatistics.Item("SelectCount"))  
      Dim selectRows As Long = _  
          CLng(currentStatistics.Item("SelectRows"))  
  
      Console.WriteLine("BytesReceived: " & bytesReceived.ToString())  
      Console.WriteLine("BytesSent: " & bytesSent.ToString())  
      Console.WriteLine("SelectCount: " & selectCount.ToString())  
      Console.WriteLine("SelectRows: " & selectRows.ToString())  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetValue  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =
          new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
          awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
          currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        // Retrieve a few individual values  
        // related to the previous command.  
        long bytesReceived =  
            (long) currentStatistics["BytesReceived"];  
        long bytesSent =  
            (long) currentStatistics["BytesSent"];  
        long selectCount =  
            (long) currentStatistics["SelectCount"];  
        long selectRows =  
            (long) currentStatistics["SelectRows"];  
  
        Console.WriteLine("BytesReceived: " +  
            bytesReceived.ToString());  
        Console.WriteLine("BytesSent: " +  
            bytesSent.ToString());  
        Console.WriteLine("SelectCount: " +  
            selectCount.ToString());  
        Console.WriteLine("SelectRows: " +  
            selectRows.ToString());  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
### <a name="retrieving-all-values"></a><span data-ttu-id="5a358-197">检索所有值</span><span class="sxs-lookup"><span data-stu-id="5a358-197">Retrieving All Values</span></span>  

 <span data-ttu-id="5a358-198">下面的控制台应用程序显示了如何启用连接的统计信息，如何使用枚举器检索所有可用的统计信息值并将它们写入控制台窗口。</span><span class="sxs-lookup"><span data-stu-id="5a358-198">The following console application shows how to enable statistics on a connection, retrieve all available statistic values using the enumerator, and write them to the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5a358-199">下面的示例使用随 SQL Server 提供的 AdventureWorks 示例数据库\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5a358-199">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="5a358-200">示例代码中提供的连接字符串假定数据库已安装并且在本地计算机上可用。</span><span class="sxs-lookup"><span data-stu-id="5a358-200">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="5a358-201">根据环境需要修改连接字符串。</span><span class="sxs-lookup"><span data-stu-id="5a358-201">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      Console.WriteLine("Key Name and Value")  
  
      ' Note the entries are unsorted.  
      For Each entry As DictionaryEntry In currentStatistics  
        Console.WriteLine(entry.Key.ToString() & _  
            ": " & entry.Value.ToString())  
      Next  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetAll  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =  
            new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
            awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
            currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        Console.WriteLine("Key Name and Value");  
  
        // Note the entries are unsorted.  
        foreach (DictionaryEntry entry in currentStatistics)  
        {  
          Console.WriteLine(entry.Key.ToString() +  
              ": " + entry.Value.ToString());  
        }  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="5a358-202">请参阅</span><span class="sxs-lookup"><span data-stu-id="5a358-202">See also</span></span>

- [<span data-ttu-id="5a358-203">SQL Server 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5a358-203">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="5a358-204">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="5a358-204">ADO.NET Overview</span></span>](../ado-net-overview.md)

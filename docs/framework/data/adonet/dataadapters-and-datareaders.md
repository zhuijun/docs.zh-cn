---
title: DataAdapter 和 DataReader
description: 了解用于从数据库中检索数据的 ADO.NET DataReader 以及用于从数据源检索数据并填充数据集的 DataAdapter。
ms.date: 03/30/2017
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
ms.openlocfilehash: 17463d65266baa53521bed9603c8abd96923277b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286968"
---
# <a name="dataadapters-and-datareaders"></a><span data-ttu-id="6e18a-103">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="6e18a-103">DataAdapters and DataReaders</span></span>
<span data-ttu-id="6e18a-104">您可以使用 ADO.NET **DataReader**从数据库中检索只读、只进数据流。</span><span class="sxs-lookup"><span data-stu-id="6e18a-104">You can use the ADO.NET **DataReader** to retrieve a read-only, forward-only stream of data from a database.</span></span> <span data-ttu-id="6e18a-105">结果将在执行查询时返回，并存储在客户端的网络缓冲区中，直到您使用**DataReader**的**Read**方法请求它们。</span><span class="sxs-lookup"><span data-stu-id="6e18a-105">Results are returned as the query executes, and are stored in the network buffer on the client until you request them using the **Read** method of the **DataReader**.</span></span> <span data-ttu-id="6e18a-106">使用**DataReader**可以通过在数据可用时立即检索数据来提高应用程序的性能，并在默认情况下，每次仅在内存中存储一行，从而减少系统开销。</span><span class="sxs-lookup"><span data-stu-id="6e18a-106">Using the **DataReader** can increase application performance both by retrieving data as soon as it is available, and (by default) storing only one row at a time in memory, reducing system overhead.</span></span>  
  
 <span data-ttu-id="6e18a-107"><xref:System.Data.Common.DataAdapter> 用于从数据源检索数据并填充 <xref:System.Data.DataSet> 中的表。</span><span class="sxs-lookup"><span data-stu-id="6e18a-107">A <xref:System.Data.Common.DataAdapter> is used to retrieve data from a data source and populate tables within a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="6e18a-108">`DataAdapter` 还可将对 `DataSet` 所做的更改解析回数据源。</span><span class="sxs-lookup"><span data-stu-id="6e18a-108">The `DataAdapter` also resolves changes made to the `DataSet` back to the data source.</span></span> <span data-ttu-id="6e18a-109">`DataAdapter` 使用 .NET Framework 数据提供程序的 `Connection` 对象连接到数据源，并使用 `Command` 对象从数据源检索数据以及将更改解析回数据源。</span><span class="sxs-lookup"><span data-stu-id="6e18a-109">The `DataAdapter` uses the `Connection` object of the .NET Framework data provider to connect to a data source, and it uses `Command` objects to retrieve data from and resolve changes to the data source.</span></span>  
  
 <span data-ttu-id="6e18a-110">随 .NET Framework 提供的每个 .NET Framework 数据提供程序都具有一个 <xref:System.Data.Common.DbDataReader> 和一个 <xref:System.Data.Common.DbDataAdapter> 对象：用于 OLE DB 的 .NET Framework 数据提供程序包括一个 <xref:System.Data.OleDb.OleDbDataReader> 和一个 <xref:System.Data.OleDb.OleDbDataAdapter> 对象，用于 SQL Server 的 .NET Framework 数据提供程序包括一个 <xref:System.Data.SqlClient.SqlDataReader> 和一个 <xref:System.Data.SqlClient.SqlDataAdapter> 对象，用于 ODBC 的 .NET Framework 数据提供程序包括一个 <xref:System.Data.Odbc.OdbcDataReader> 和一个 <xref:System.Data.Odbc.OdbcDataAdapter> 对象，用于 Oracle 的 .NET Framework 数据提供程序包括一个 <xref:System.Data.OracleClient.OracleDataReader> 和一个 <xref:System.Data.OracleClient.OracleDataAdapter> 对象。</span><span class="sxs-lookup"><span data-stu-id="6e18a-110">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbDataReader> and a <xref:System.Data.Common.DbDataAdapter> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbDataReader> and an <xref:System.Data.OleDb.OleDbDataAdapter> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlDataReader> and a <xref:System.Data.SqlClient.SqlDataAdapter> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcDataReader> and an <xref:System.Data.Odbc.OdbcDataAdapter> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleDataReader> and an <xref:System.Data.OracleClient.OracleDataAdapter> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6e18a-111">本节内容</span><span class="sxs-lookup"><span data-stu-id="6e18a-111">In This Section</span></span>  
 [<span data-ttu-id="6e18a-112">使用 DataReader 检索 ADO 数据</span><span class="sxs-lookup"><span data-stu-id="6e18a-112">Retrieving Data Using a DataReader</span></span>](retrieving-data-using-a-datareader.md)  
 <span data-ttu-id="6e18a-113">介绍 ADO.NET **DataReader**对象，以及如何使用它从数据源返回结果流。</span><span class="sxs-lookup"><span data-stu-id="6e18a-113">Describes the ADO.NET **DataReader** object and how to use it to return a stream of results from a data source.</span></span>  
  
 [<span data-ttu-id="6e18a-114">从 DataAdapter 填充数据集</span><span class="sxs-lookup"><span data-stu-id="6e18a-114">Populating a DataSet from a DataAdapter</span></span>](populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="6e18a-115">说明如何通过 `DataSet` 使用表、列和行填充 `DataAdapter`。</span><span class="sxs-lookup"><span data-stu-id="6e18a-115">Describes how to fill a `DataSet` with tables, columns, and rows by using a `DataAdapter`.</span></span>  
  
 [<span data-ttu-id="6e18a-116">DataAdapter 参数</span><span class="sxs-lookup"><span data-stu-id="6e18a-116">DataAdapter Parameters</span></span>](dataadapter-parameters.md)  
 <span data-ttu-id="6e18a-117">说明如何与 `DataAdapter` 的命令属性一起使用参数，包括如何将 `DataSet` 的列内容映射到命令参数。</span><span class="sxs-lookup"><span data-stu-id="6e18a-117">Describes how to use parameters with the command properties of a `DataAdapter` including how to map the contents of a column in a `DataSet` to a command parameter.</span></span>  
  
 [<span data-ttu-id="6e18a-118">将现有约束添加到数据集</span><span class="sxs-lookup"><span data-stu-id="6e18a-118">Adding Existing Constraints to a DataSet</span></span>](adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="6e18a-119">说明如何将现有约束添加到 `DataSet`。</span><span class="sxs-lookup"><span data-stu-id="6e18a-119">Describes how to add existing constraints to a `DataSet`.</span></span>  
  
 [<span data-ttu-id="6e18a-120">DataAdapter 数据表和 DataColumn 映射</span><span class="sxs-lookup"><span data-stu-id="6e18a-120">DataAdapter DataTable and DataColumn Mappings</span></span>](dataadapter-datatable-and-datacolumn-mappings.md)  
 <span data-ttu-id="6e18a-121">说明如何为 `DataTableMappings` 设置 `ColumnMappings` 和 `DataAdapter`。</span><span class="sxs-lookup"><span data-stu-id="6e18a-121">Describes how to set up `DataTableMappings` and `ColumnMappings` for a `DataAdapter`.</span></span>  
  
 [<span data-ttu-id="6e18a-122">通过查询结果分页</span><span class="sxs-lookup"><span data-stu-id="6e18a-122">Paging Through a Query Result</span></span>](paging-through-a-query-result.md)  
 <span data-ttu-id="6e18a-123">提供一个以数据页形式查看查询结果的示例。</span><span class="sxs-lookup"><span data-stu-id="6e18a-123">Provides an example of viewing the results of a query as pages of data.</span></span>  
  
 [<span data-ttu-id="6e18a-124">使用 DataAdapter 更新数据源</span><span class="sxs-lookup"><span data-stu-id="6e18a-124">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="6e18a-125">说明如何使用 `DataAdapter` 将 `DataSet` 中的更改解析回数据库。</span><span class="sxs-lookup"><span data-stu-id="6e18a-125">Describes how to use a `DataAdapter` to resolve changes in a `DataSet` back to the database.</span></span>  
  
 [<span data-ttu-id="6e18a-126">处理 DataAdapter 事件</span><span class="sxs-lookup"><span data-stu-id="6e18a-126">Handling DataAdapter Events</span></span>](handling-dataadapter-events.md)  
 <span data-ttu-id="6e18a-127">说明 `DataAdapter` 事件以及如何使用这些事件。</span><span class="sxs-lookup"><span data-stu-id="6e18a-127">Describes `DataAdapter` events and how to use them.</span></span>  
  
 [<span data-ttu-id="6e18a-128">使用 DataAdapter 执行批处理操作</span><span class="sxs-lookup"><span data-stu-id="6e18a-128">Performing Batch Operations Using DataAdapters</span></span>](performing-batch-operations-using-dataadapters.md)  
 <span data-ttu-id="6e18a-129">说明在从 `DataSet` 应用更新时，如何通过减少与 SQL Server 之间的往返次数来提高应用程序的性能。</span><span class="sxs-lookup"><span data-stu-id="6e18a-129">Describes enhancing application performance by reducing the number of round trips to SQL Server when applying updates from the `DataSet`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e18a-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6e18a-130">See also</span></span>

- [<span data-ttu-id="6e18a-131">连接到数据源</span><span class="sxs-lookup"><span data-stu-id="6e18a-131">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="6e18a-132">命令和参数</span><span class="sxs-lookup"><span data-stu-id="6e18a-132">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="6e18a-133">事务和并发性</span><span class="sxs-lookup"><span data-stu-id="6e18a-133">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="6e18a-134">数据集、数据表和数据视图</span><span class="sxs-lookup"><span data-stu-id="6e18a-134">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)
- [<span data-ttu-id="6e18a-135">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="6e18a-135">ADO.NET Overview</span></span>](ado-net-overview.md)

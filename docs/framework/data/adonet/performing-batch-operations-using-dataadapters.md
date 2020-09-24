---
title: 使用 DataAdapter 执行批处理操作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e72ed5af-b24f-486c-8429-c8fd2208f844
ms.openlocfilehash: 9dd6abb91b3549e3bc8b4ae84cbb227171512ecb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177418"
---
# <a name="performing-batch-operations-using-dataadapters"></a><span data-ttu-id="82bd1-102">使用 DataAdapter 执行批处理操作</span><span class="sxs-lookup"><span data-stu-id="82bd1-102">Performing Batch Operations Using DataAdapters</span></span>

<span data-ttu-id="82bd1-103">通过 ADO.NET 中的批处理支持，<xref:System.Data.Common.DataAdapter> 可以将 <xref:System.Data.DataSet> 或 <xref:System.Data.DataTable> 中的 INSERT、UPDATE 和 DELETE 操作分组发向服务器，而不是每次发送一项操作。</span><span class="sxs-lookup"><span data-stu-id="82bd1-103">Batch support in ADO.NET allows a <xref:System.Data.Common.DataAdapter> to group INSERT, UPDATE, and DELETE operations from a <xref:System.Data.DataSet> or <xref:System.Data.DataTable> to the server, instead of sending one operation at a time.</span></span> <span data-ttu-id="82bd1-104">因为减少了与服务器的往返次数，通常可以大大提高性能。</span><span class="sxs-lookup"><span data-stu-id="82bd1-104">The reduction in the number of round trips to the server typically results in significant performance gains.</span></span> <span data-ttu-id="82bd1-105">SQL Server .NET 数据提供程序 (<xref:System.Data.SqlClient>) 和 Oracle .NET 数据提供程序 (<xref:System.Data.OracleClient>) 支持批量更新。</span><span class="sxs-lookup"><span data-stu-id="82bd1-105">Batch updates are supported for the .NET data providers for SQL Server (<xref:System.Data.SqlClient>) and Oracle (<xref:System.Data.OracleClient>).</span></span>  
  
 <span data-ttu-id="82bd1-106">在 ADO.NET 的以前版本中用 <xref:System.Data.DataSet> 中的更改更新数据库时，`Update` 的 `DataAdapter` 方法执行一次会向数据库中更新一行。</span><span class="sxs-lookup"><span data-stu-id="82bd1-106">When updating a database with changes from a <xref:System.Data.DataSet> in previous versions of ADO.NET, the `Update` method of a `DataAdapter` performed updates to the database one row at a time.</span></span> <span data-ttu-id="82bd1-107">当该方法循环访问指定 <xref:System.Data.DataTable> 中的各行时，它会检查每个 <xref:System.Data.DataRow> 以查看其是否已被修改。</span><span class="sxs-lookup"><span data-stu-id="82bd1-107">As it iterated through the rows in the specified <xref:System.Data.DataTable>, it examined each <xref:System.Data.DataRow> to see if it had been modified.</span></span> <span data-ttu-id="82bd1-108">如果行已被修改，它会调用相应的 `UpdateCommand`、`InsertCommand` 或 `DeleteCommand`，具体取决于该行的 <xref:System.Data.DataRow.RowState%2A> 属性值。</span><span class="sxs-lookup"><span data-stu-id="82bd1-108">If the row had been modified, it called the appropriate `UpdateCommand`, `InsertCommand`, or `DeleteCommand`, depending on the value of the <xref:System.Data.DataRow.RowState%2A> property for that row.</span></span> <span data-ttu-id="82bd1-109">每行更新都需要通过网络往返访问一次数据库。</span><span class="sxs-lookup"><span data-stu-id="82bd1-109">Every row update involved a network round-trip to the database.</span></span>  
  
 <span data-ttu-id="82bd1-110">从 ADO.NET 2.0 开始，<xref:System.Data.Common.DbDataAdapter> 公开一个 <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="82bd1-110">Starting with ADO.NET 2.0, the <xref:System.Data.Common.DbDataAdapter> exposes an <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> property.</span></span> <span data-ttu-id="82bd1-111">将 `UpdateBatchSize` 设置为正整数值可使对数据库的更新以指定大小的批处理形式发送。</span><span class="sxs-lookup"><span data-stu-id="82bd1-111">Setting the `UpdateBatchSize` to a positive integer value causes updates to the database to be sent as batches of the specified size.</span></span> <span data-ttu-id="82bd1-112">例如，将 `UpdateBatchSize` 设置为 10 可将 10 个单独的语句编成一组并作为单个批处理进行提交。</span><span class="sxs-lookup"><span data-stu-id="82bd1-112">For example, setting the `UpdateBatchSize` to 10 will group 10 separate statements and submit them as single batch.</span></span> <span data-ttu-id="82bd1-113">将 `UpdateBatchSize` 设置为 0 可使 <xref:System.Data.Common.DataAdapter> 使用服务器能够处理的最大批大小。</span><span class="sxs-lookup"><span data-stu-id="82bd1-113">Setting the `UpdateBatchSize` to 0 will cause the <xref:System.Data.Common.DataAdapter> to use the largest batch size that the server can handle.</span></span> <span data-ttu-id="82bd1-114">将其设置为 1 可禁用批处理更新，因为这时一次只发送一行。</span><span class="sxs-lookup"><span data-stu-id="82bd1-114">Setting it to 1 disables batch updates, as rows are sent one at a time.</span></span>  
  
 <span data-ttu-id="82bd1-115">执行极大的批处理会降低性能。</span><span class="sxs-lookup"><span data-stu-id="82bd1-115">Executing an extremely large batch could decrease performance.</span></span> <span data-ttu-id="82bd1-116">因此，在实现应用程序前应进行测试以得到最佳的批大小。</span><span class="sxs-lookup"><span data-stu-id="82bd1-116">Therefore, you should test for the optimum batch size setting before implementing your application.</span></span>  
  
## <a name="using-the-updatebatchsize-property"></a><span data-ttu-id="82bd1-117">使用 UpdateBatchSize 属性</span><span class="sxs-lookup"><span data-stu-id="82bd1-117">Using the UpdateBatchSize Property</span></span>  

 <span data-ttu-id="82bd1-118">启用批处理更新时，的 <xref:System.Data.IDbCommand.UpdatedRowSource%2A>、`UpdateCommand` 和 `InsertCommand` 的 `DeleteCommand` 属性值应设置为 <xref:System.Data.UpdateRowSource.None> 或 <xref:System.Data.UpdateRowSource.OutputParameters>。</span><span class="sxs-lookup"><span data-stu-id="82bd1-118">When batch updates are enabled, the <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of the DataAdapter's `UpdateCommand`, `InsertCommand`, and `DeleteCommand` should be set to <xref:System.Data.UpdateRowSource.None> or <xref:System.Data.UpdateRowSource.OutputParameters>.</span></span> <span data-ttu-id="82bd1-119">执行批处理更新时，命令的 <xref:System.Data.IDbCommand.UpdatedRowSource%2A> 或 <xref:System.Data.UpdateRowSource.FirstReturnedRecord> 的 <xref:System.Data.UpdateRowSource.Both> 属性值无效。</span><span class="sxs-lookup"><span data-stu-id="82bd1-119">When performing a batch update, the command's <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of <xref:System.Data.UpdateRowSource.FirstReturnedRecord> or <xref:System.Data.UpdateRowSource.Both> is invalid.</span></span>  
  
 <span data-ttu-id="82bd1-120">下面的过程演示 `UpdateBatchSize` 属性的用法。</span><span class="sxs-lookup"><span data-stu-id="82bd1-120">The following procedure demonstrates the use of the `UpdateBatchSize` property.</span></span> <span data-ttu-id="82bd1-121">此过程采用两个自变量：一个 <xref:System.Data.DataSet> 对象，该对象的列表示**ProductCategory**表中的**ProductCategoryID**和**Name**字段，一个整数表示批大小 (批处理) 中的行数。</span><span class="sxs-lookup"><span data-stu-id="82bd1-121">The procedure takes two arguments, a <xref:System.Data.DataSet> object that has columns representing the **ProductCategoryID** and **Name** fields in the **Production.ProductCategory** table, and an integer representing the batch size (the number of rows in the batch).</span></span> <span data-ttu-id="82bd1-122">代码创建一个新的 <xref:System.Data.SqlClient.SqlDataAdapter> 对象，并设置其 <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>、<xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> 和 <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="82bd1-122">The code creates a new <xref:System.Data.SqlClient.SqlDataAdapter> object, setting its <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties.</span></span> <span data-ttu-id="82bd1-123">代码假定 <xref:System.Data.DataSet> 对象具有经过修改的行。</span><span class="sxs-lookup"><span data-stu-id="82bd1-123">The code assumes that the <xref:System.Data.DataSet> object has modified rows.</span></span> <span data-ttu-id="82bd1-124">它设置 `UpdateBatchSize` 属性并执行更新。</span><span class="sxs-lookup"><span data-stu-id="82bd1-124">It sets the `UpdateBatchSize` property and executes the update.</span></span>  
  
```vb  
Public Sub BatchUpdate( _  
  ByVal dataTable As DataTable, ByVal batchSize As Int32)  
    ' Assumes GetConnectionString() returns a valid connection string.  
    Dim connectionString As String = GetConnectionString()  
  
    ' Connect to the AdventureWorks database.  
    Using connection As New SqlConnection(connectionString)  
        ' Create a SqlDataAdapter.  
        Dim adapter As New SqlDataAdapter()  
  
        'Set the UPDATE command and parameters.  
        adapter.UpdateCommand = New SqlCommand( _  
          "UPDATE Production.ProductCategory SET " _  
          & "Name=@Name WHERE ProductCategoryID=@ProdCatID;", _  
          connection)  
        adapter.UpdateCommand.Parameters.Add("@Name", _  
          SqlDbType.NVarChar, 50, "Name")  
        adapter.UpdateCommand.Parameters.Add("@ProdCatID",  _  
          SqlDbType.Int, 4, " ProductCategoryID ")  
        adapter.UpdateCommand.UpdatedRowSource = _  
          UpdateRowSource.None  
  
        'Set the INSERT command and parameter.  
        adapter.InsertCommand = New SqlCommand( _  
          "INSERT INTO Production.ProductCategory (Name) VALUES (@Name);", _  
  connection)  
        adapter.InsertCommand.Parameters.Add("@Name", _  
          SqlDbType.NVarChar, 50, "Name")  
        adapter.InsertCommand.UpdatedRowSource = _  
          UpdateRowSource.None  
  
        'Set the DELETE command and parameter.  
        adapter.DeleteCommand = New SqlCommand( _  
          "DELETE FROM Production.ProductCategory " _  
          & "WHERE ProductCategoryID=@ProdCatID;", connection)  
        adapter.DeleteCommand.Parameters.Add("@ProdCatID", _  
           SqlDbType.Int, 4, " ProductCategoryID ")  
        adapter.DeleteCommand.UpdatedRowSource = UpdateRowSource.None  
  
        ' Set the batch size.  
        adapter.UpdateBatchSize = batchSize  
  
        ' Execute the update.  
        adapter.Update(dataTable)  
    End Using  
End Sub  
```  
  
```csharp  
public static void BatchUpdate(DataTable dataTable,Int32 batchSize)  
{  
    // Assumes GetConnectionString() returns a valid connection string.  
    string connectionString = GetConnectionString();  
  
    // Connect to the AdventureWorks database.  
    using (SqlConnection connection = new
      SqlConnection(connectionString))  
    {  
  
        // Create a SqlDataAdapter.  
        SqlDataAdapter adapter = new SqlDataAdapter();  
  
        // Set the UPDATE command and parameters.  
        adapter.UpdateCommand = new SqlCommand(  
            "UPDATE Production.ProductCategory SET "  
            + "Name=@Name WHERE ProductCategoryID=@ProdCatID;",
            connection);  
        adapter.UpdateCommand.Parameters.Add("@Name",
           SqlDbType.NVarChar, 50, "Name");  
        adapter.UpdateCommand.Parameters.Add("@ProdCatID",
           SqlDbType.Int, 4, "ProductCategoryID");  
         adapter.UpdateCommand.UpdatedRowSource = UpdateRowSource.None;  
  
        // Set the INSERT command and parameter.  
        adapter.InsertCommand = new SqlCommand(  
            "INSERT INTO Production.ProductCategory (Name) VALUES (@Name);",
            connection);  
        adapter.InsertCommand.Parameters.Add("@Name",
          SqlDbType.NVarChar, 50, "Name");  
        adapter.InsertCommand.UpdatedRowSource = UpdateRowSource.None;  
  
        // Set the DELETE command and parameter.  
        adapter.DeleteCommand = new SqlCommand(  
            "DELETE FROM Production.ProductCategory "  
            + "WHERE ProductCategoryID=@ProdCatID;", connection);  
        adapter.DeleteCommand.Parameters.Add("@ProdCatID",
          SqlDbType.Int, 4, "ProductCategoryID");  
        adapter.DeleteCommand.UpdatedRowSource = UpdateRowSource.None;  
  
        // Set the batch size.  
        adapter.UpdateBatchSize = batchSize;  
  
        // Execute the update.  
        adapter.Update(dataTable);  
    }  
}  
```  
  
## <a name="handling-batch-update-related-events-and-errors"></a><span data-ttu-id="82bd1-125">处理与批处理更新相关的事件和错误</span><span class="sxs-lookup"><span data-stu-id="82bd1-125">Handling Batch Update-Related Events and Errors</span></span>  

 <span data-ttu-id="82bd1-126">**DataAdapter**有两个与更新相关的事件： **RowUpdating**和**RowUpdated**。</span><span class="sxs-lookup"><span data-stu-id="82bd1-126">The **DataAdapter** has two update-related events: **RowUpdating** and **RowUpdated**.</span></span> <span data-ttu-id="82bd1-127">在 ADO.NET 的以前版本中，如果禁用批处理，则每处理一行就会生成一次这些事件。</span><span class="sxs-lookup"><span data-stu-id="82bd1-127">In previous versions of ADO.NET, when batch processing is disabled, each of these events is generated once for each row processed.</span></span> <span data-ttu-id="82bd1-128">**RowUpdating** 是在更新执行之前生成的，在数据库更新完成后生成 **RowUpdated** 。</span><span class="sxs-lookup"><span data-stu-id="82bd1-128">**RowUpdating** is generated before the update occurs, and **RowUpdated** is generated after the database update has been completed.</span></span>  
  
### <a name="event-behavior-changes-with-batch-updates"></a><span data-ttu-id="82bd1-129">批处理更新的事件行为更改</span><span class="sxs-lookup"><span data-stu-id="82bd1-129">Event Behavior Changes with Batch Updates</span></span>  

 <span data-ttu-id="82bd1-130">启用批处理时，在单个数据库操作中可更新多行。</span><span class="sxs-lookup"><span data-stu-id="82bd1-130">When batch processing is enabled, multiple rows are updated in a single database operation.</span></span> <span data-ttu-id="82bd1-131">因此，每个批处理只发生一次 `RowUpdated` 事件，而对于处理每一行，`RowUpdating` 事件都会发生。</span><span class="sxs-lookup"><span data-stu-id="82bd1-131">Therefore, only one `RowUpdated` event occurs for each batch, whereas the `RowUpdating` event occurs for each row processed.</span></span> <span data-ttu-id="82bd1-132">禁用批处理时，这两个事件一对一交错触发，即一行触发一个 `RowUpdating` 事件和一个 `RowUpdated` 事件，下一行触发一个 `RowUpdating` 事件和一个 `RowUpdated` 事件，直到处理完所有行。</span><span class="sxs-lookup"><span data-stu-id="82bd1-132">When batch processing is disabled, the two events are fired with one-to-one interleaving, where one `RowUpdating` event and one `RowUpdated` event fire for a row, and then one `RowUpdating` and one `RowUpdated` event fire for the next row, until all of the rows are processed.</span></span>  
  
### <a name="accessing-updated-rows"></a><span data-ttu-id="82bd1-133">访问更新的行</span><span class="sxs-lookup"><span data-stu-id="82bd1-133">Accessing Updated Rows</span></span>  

 <span data-ttu-id="82bd1-134">禁用批处理时，可以使用 <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> 类的 <xref:System.Data.Common.RowUpdatedEventArgs> 属性访问要进行更新的行。</span><span class="sxs-lookup"><span data-stu-id="82bd1-134">When batch processing is disabled, the row being updated can be accessed using the <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> property of the <xref:System.Data.Common.RowUpdatedEventArgs> class.</span></span>  
  
 <span data-ttu-id="82bd1-135">启用批处理时，会为多行生成单个 `RowUpdated` 事件。</span><span class="sxs-lookup"><span data-stu-id="82bd1-135">When batch processing is enabled, a single `RowUpdated` event is generated for multiple rows.</span></span> <span data-ttu-id="82bd1-136">因此，每一行的 `Row` 属性值为空。</span><span class="sxs-lookup"><span data-stu-id="82bd1-136">Therefore, the value of the `Row` property for each row is null.</span></span> <span data-ttu-id="82bd1-137">但仍会为每一行生成 `RowUpdating` 事件。</span><span class="sxs-lookup"><span data-stu-id="82bd1-137">`RowUpdating` events are still generated for each row.</span></span> <span data-ttu-id="82bd1-138">使用 <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> 类的 <xref:System.Data.Common.RowUpdatedEventArgs> 方法可以通过将对行的引用复制到一个数组来访问已处理的行。</span><span class="sxs-lookup"><span data-stu-id="82bd1-138">The <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method of the <xref:System.Data.Common.RowUpdatedEventArgs> class allows you to access the processed rows by copying references to the rows into an array.</span></span> <span data-ttu-id="82bd1-139">如果没有要进行处理的行，`CopyToRows` 将引发一个 <xref:System.ArgumentNullException>。</span><span class="sxs-lookup"><span data-stu-id="82bd1-139">If no rows are being processed, `CopyToRows` throws an <xref:System.ArgumentNullException>.</span></span> <span data-ttu-id="82bd1-140">在调用 <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> 方法之前，使用 <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> 属性可返回已处理行的数目。</span><span class="sxs-lookup"><span data-stu-id="82bd1-140">Use the <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> property to return the number of rows processed before calling the <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method.</span></span>  
  
### <a name="handling-data-errors"></a><span data-ttu-id="82bd1-141">处理数据错误</span><span class="sxs-lookup"><span data-stu-id="82bd1-141">Handling Data Errors</span></span>  

 <span data-ttu-id="82bd1-142">执行批处理与执行每个单独的语句具有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="82bd1-142">Batch execution has the same effect as the execution of each individual statement.</span></span> <span data-ttu-id="82bd1-143">各语句按照其添加到批处理中的顺序执行。</span><span class="sxs-lookup"><span data-stu-id="82bd1-143">Statements are executed in the order that the statements were added to the batch.</span></span> <span data-ttu-id="82bd1-144">在批处理模式下处理错误的方式与禁用批处理模式时相同。</span><span class="sxs-lookup"><span data-stu-id="82bd1-144">Errors are handled the same way in batch mode as they are when batch mode is disabled.</span></span> <span data-ttu-id="82bd1-145">每一行均单独处理。</span><span class="sxs-lookup"><span data-stu-id="82bd1-145">Each row is processed separately.</span></span> <span data-ttu-id="82bd1-146">只有在数据库中经过成功处理的行才能在 <xref:System.Data.DataRow> 内的相应 <xref:System.Data.DataTable> 中更新。</span><span class="sxs-lookup"><span data-stu-id="82bd1-146">Only rows that have been successfully processed in the database will be updated in the corresponding <xref:System.Data.DataRow> within the <xref:System.Data.DataTable>.</span></span>  
  
 <span data-ttu-id="82bd1-147">数据提供程序和后端数据库服务器确定支持哪些 SQL 构造以执行批处理。</span><span class="sxs-lookup"><span data-stu-id="82bd1-147">The data provider and the back-end database server determine which SQL constructs are supported for batch execution.</span></span> <span data-ttu-id="82bd1-148">如果为执行提交了不支持的语句，则可能引发异常。</span><span class="sxs-lookup"><span data-stu-id="82bd1-148">An exception may be thrown if a non-supported statement is submitted for execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82bd1-149">请参阅</span><span class="sxs-lookup"><span data-stu-id="82bd1-149">See also</span></span>

- [<span data-ttu-id="82bd1-150">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="82bd1-150">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="82bd1-151">使用 DataAdapter 更新数据源</span><span class="sxs-lookup"><span data-stu-id="82bd1-151">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="82bd1-152">处理 DataAdapter 事件</span><span class="sxs-lookup"><span data-stu-id="82bd1-152">Handling DataAdapter Events</span></span>](handling-dataadapter-events.md)
- [<span data-ttu-id="82bd1-153">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="82bd1-153">ADO.NET Overview</span></span>](ado-net-overview.md)

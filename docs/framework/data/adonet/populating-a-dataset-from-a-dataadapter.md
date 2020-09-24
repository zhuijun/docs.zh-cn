---
title: 从 DataAdapter 填充数据集
description: 了解如何在 ADO.NET 中从 DataAdapter 填充数据集，这提供了独立于数据源的一致关系编程模型。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fa0ac7d-e266-4954-bfac-3fbe2f913153
ms.openlocfilehash: ac84af884238b166266d4206802878c1e21169fd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177405"
---
# <a name="populating-a-dataset-from-a-dataadapter"></a><span data-ttu-id="84af4-103">从 DataAdapter 填充数据集</span><span class="sxs-lookup"><span data-stu-id="84af4-103">Populating a DataSet from a DataAdapter</span></span>

<span data-ttu-id="84af4-104">ADO.NET <xref:System.Data.DataSet> 是数据的内存驻留表示形式，提供与数据源无关的一致关系编程模型。</span><span class="sxs-lookup"><span data-stu-id="84af4-104">The ADO.NET <xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model independent of the data source.</span></span> <span data-ttu-id="84af4-105">`DataSet` 表示整个数据集，其中包含表、约束和表之间的关系。</span><span class="sxs-lookup"><span data-stu-id="84af4-105">The `DataSet` represents a complete set of data that includes tables, constraints, and relationships among the tables.</span></span> <span data-ttu-id="84af4-106">由于 `DataSet` 独立于数据源，因此 `DataSet` 可以包含应用程序本地的数据，也可以包含来自多个数据源的数据。</span><span class="sxs-lookup"><span data-stu-id="84af4-106">Because the `DataSet` is independent of the data source, a `DataSet` can include data local to the application, and data from multiple data sources.</span></span> <span data-ttu-id="84af4-107">与现有数据源的交互通过 `DataAdapter`来控制。</span><span class="sxs-lookup"><span data-stu-id="84af4-107">Interaction with existing data sources is controlled through the `DataAdapter`.</span></span>  
  
 <span data-ttu-id="84af4-108">`SelectCommand` 的 `DataAdapter` 属性是一个 `Command` 对象，用于从数据源中检索数据。</span><span class="sxs-lookup"><span data-stu-id="84af4-108">The `SelectCommand` property of the `DataAdapter` is a `Command` object that retrieves data from the data source.</span></span> <span data-ttu-id="84af4-109">`InsertCommand`的 `UpdateCommand`、 `DeleteCommand` 和 `DataAdapter` 属性是 `Command` 对象，用于按照对 `DataSet`中数据的修改来管理对数据源中数据的更新。</span><span class="sxs-lookup"><span data-stu-id="84af4-109">The `InsertCommand`, `UpdateCommand`, and `DeleteCommand` properties of the `DataAdapter` are `Command` objects that manage updates to the data in the data source according to modifications made to the data in the `DataSet`.</span></span> <span data-ttu-id="84af4-110">[通过 Dataadapter 更新数据源](updating-data-sources-with-dataadapters.md)中更详细地介绍了这些属性。</span><span class="sxs-lookup"><span data-stu-id="84af4-110">These properties are covered in more detail in [Updating Data Sources with DataAdapters](updating-data-sources-with-dataadapters.md).</span></span>  
  
 <span data-ttu-id="84af4-111">`Fill` 的 `DataAdapter` 方法用于使用 `DataSet` 的 `SelectCommand` 结果填充 `DataAdapter`。</span><span class="sxs-lookup"><span data-stu-id="84af4-111">The `Fill` method of the `DataAdapter` is used to populate a `DataSet` with the results of the `SelectCommand` of the `DataAdapter`.</span></span> <span data-ttu-id="84af4-112">`Fill` 将要填充的 `DataSet` 、和 `DataTable` 对象（或要使用从 `DataTable` 中返回的行来填充的 `SelectCommand`的名称）作为它的参数。</span><span class="sxs-lookup"><span data-stu-id="84af4-112">`Fill` takes as its arguments a `DataSet` to be populated, and a `DataTable` object, or the name of the `DataTable` to be filled with the rows returned from the `SelectCommand`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="84af4-113">使用 `DataAdapter` 检索表的全部内容会花费些时间，尤其是在表中有很多行时。</span><span class="sxs-lookup"><span data-stu-id="84af4-113">Using the `DataAdapter` to retrieve all of a table takes time, especially if there are many rows in the table.</span></span> <span data-ttu-id="84af4-114">这是因为访问数据库，定位和处理数据，然后将数据传输到客户端是需要很长时间的。</span><span class="sxs-lookup"><span data-stu-id="84af4-114">This is because accessing the database, locating and processing the data, and then transferring the data to the client is time-consuming.</span></span> <span data-ttu-id="84af4-115">将表中全部内容提取到客户端还会在服务器上锁定所有行。</span><span class="sxs-lookup"><span data-stu-id="84af4-115">Pulling all of the table to the client also locks all of the rows on the server.</span></span> <span data-ttu-id="84af4-116">若要提高性能，您可以使用 `WHERE` 子句使返回客户端的行数大为减少。</span><span class="sxs-lookup"><span data-stu-id="84af4-116">To improve performance, you can use the `WHERE` clause to greatly reduce the number of rows returned to the client.</span></span> <span data-ttu-id="84af4-117">还可以通过只显式列出 `SELECT` 语句要求的列减少返回到客户端的数据量。</span><span class="sxs-lookup"><span data-stu-id="84af4-117">You can also reduce the amount of data returned to the client by only explicitly listing required columns in the `SELECT` statement.</span></span> <span data-ttu-id="84af4-118">另一种好的变通方法是以批次检索行（例如一次检索几百行），并且在客户端完成当前批次后只检索下一批次。</span><span class="sxs-lookup"><span data-stu-id="84af4-118">Another good workaround is to retrieve the rows in batches (such as several hundred rows at a time) and only retrieve the next batch when the client is finished with the current batch.</span></span>  
  
 <span data-ttu-id="84af4-119">`Fill` 方法使用 `DataReader` 对象来隐式地返回用于在 `DataSet`中创建表的列名称和类型，以及用于填充 `DataSet`中的表行的数据。</span><span class="sxs-lookup"><span data-stu-id="84af4-119">The `Fill` method uses the `DataReader` object implicitly to return the column names and types that are used to create the tables in the `DataSet`, and the data to populate the rows of the tables in the `DataSet`.</span></span> <span data-ttu-id="84af4-120">表和列仅在不存在时才创建；否则， `Fill` 将使用现有的 `DataSet` 架构。</span><span class="sxs-lookup"><span data-stu-id="84af4-120">Tables and columns are only created if they do not already exist; otherwise `Fill` uses the existing `DataSet` schema.</span></span> <span data-ttu-id="84af4-121">根据 [ADO.NET 中的数据类型映射](data-type-mappings-in-ado-net.md)中的表，列类型作为 .NET Framework 类型创建。</span><span class="sxs-lookup"><span data-stu-id="84af4-121">Column types are created as .NET Framework types according to the tables in [Data Type Mappings in ADO.NET](data-type-mappings-in-ado-net.md).</span></span> <span data-ttu-id="84af4-122">除非它们存在于数据源和中，否则不会创建主键 `DataAdapter` **。**`MissingSchemaAction`</span><span class="sxs-lookup"><span data-stu-id="84af4-122">Primary keys are not created unless they exist in the data source and `DataAdapter`**.**`MissingSchemaAction`</span></span> <span data-ttu-id="84af4-123">设置为 `MissingSchemaAction` **.** `AddWithKey` 。</span><span class="sxs-lookup"><span data-stu-id="84af4-123">is set to `MissingSchemaAction`**.**`AddWithKey`.</span></span> <span data-ttu-id="84af4-124">如果 `Fill` 发现某个表存在主键，对于主键列的值与从数据源返回的行的主键列的值匹配的行，将使用数据源中的数据重写 `DataSet` 中的数据。</span><span class="sxs-lookup"><span data-stu-id="84af4-124">If `Fill` finds that a primary key exists for a table, it will overwrite data in the `DataSet` with data from the data source for rows where the primary key column values match those of the row returned from the data source.</span></span> <span data-ttu-id="84af4-125">如果未找到任何主键，则将数据追加到 `DataSet`中的表。</span><span class="sxs-lookup"><span data-stu-id="84af4-125">If no primary key is found, the data is appended to the tables in the `DataSet`.</span></span> <span data-ttu-id="84af4-126">`Fill` 使用填充时可能存在的任何映射 `DataSet` (参阅 [DataAdapter DataTable And DataColumn 映射](dataadapter-datatable-and-datacolumn-mappings.md)) 。</span><span class="sxs-lookup"><span data-stu-id="84af4-126">`Fill` uses any mappings that may exist when you populate the `DataSet` (see [DataAdapter DataTable and DataColumn Mappings](dataadapter-datatable-and-datacolumn-mappings.md)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="84af4-127">如果 `SelectCommand` 返回 OUTER JOIN 的结果，则 `DataAdapter` 不会为生成的 `PrimaryKey` 设置 `DataTable`值。</span><span class="sxs-lookup"><span data-stu-id="84af4-127">If the `SelectCommand` returns the results of an OUTER JOIN, the `DataAdapter` does not set a `PrimaryKey` value for the resulting `DataTable`.</span></span> <span data-ttu-id="84af4-128">您必须自己定义 `PrimaryKey` 以确保正确解析重复行。</span><span class="sxs-lookup"><span data-stu-id="84af4-128">You must define the `PrimaryKey` yourself to make sure that duplicate rows are resolved correctly.</span></span> <span data-ttu-id="84af4-129">有关详细信息，请参阅 [定义主键](./dataset-datatable-dataview/defining-primary-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="84af4-129">For more information, see [Defining Primary Keys](./dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
 <span data-ttu-id="84af4-130">以下代码示例创建了一个 <xref:System.Data.SqlClient.SqlDataAdapter> 实例，使用 Microsoft SQL Server <xref:System.Data.SqlClient.SqlConnection> 数据库的 `Northwind` 并使用客户列表填充 <xref:System.Data.DataTable> 中的 `DataSet` 。</span><span class="sxs-lookup"><span data-stu-id="84af4-130">The following code example creates an instance of a <xref:System.Data.SqlClient.SqlDataAdapter> that uses a <xref:System.Data.SqlClient.SqlConnection> to the Microsoft SQL Server `Northwind` database and populates a <xref:System.Data.DataTable> in a `DataSet` with the list of customers.</span></span> <span data-ttu-id="84af4-131">向 <xref:System.Data.SqlClient.SqlConnection> 构造函数传递的 SQL 语句和 <xref:System.Data.SqlClient.SqlDataAdapter> 参数用于创建 <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> 的 <xref:System.Data.SqlClient.SqlDataAdapter>属性。</span><span class="sxs-lookup"><span data-stu-id="84af4-131">The SQL statement and <xref:System.Data.SqlClient.SqlConnection> arguments passed to the <xref:System.Data.SqlClient.SqlDataAdapter> constructor are used to create the <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> property of the <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84af4-132">示例</span><span class="sxs-lookup"><span data-stu-id="84af4-132">Example</span></span>  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim queryString As String = _  
  "SELECT CustomerID, CompanyName FROM dbo.Customers"  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  queryString, connection)  
  
Dim customers As DataSet = New DataSet  
adapter.Fill(customers, "Customers")  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
string queryString =
  "SELECT CustomerID, CompanyName FROM dbo.Customers";  
SqlDataAdapter adapter = new SqlDataAdapter(queryString, connection);  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
```  
  
> [!NOTE]
> <span data-ttu-id="84af4-133">此示例中所示的代码不显式打开和关闭 `Connection`。</span><span class="sxs-lookup"><span data-stu-id="84af4-133">The code shown in this example does not explicitly open and close the `Connection`.</span></span> <span data-ttu-id="84af4-134">如果 `Fill` 方法发现连接尚未打开，它将隐式地打开 `Connection` 正在使用的 `DataAdapter` 。</span><span class="sxs-lookup"><span data-stu-id="84af4-134">The `Fill` method implicitly opens the `Connection` that the `DataAdapter` is using if it finds that the connection is not already open.</span></span> <span data-ttu-id="84af4-135">如果 `Fill` 已打开连接，则它还将在 `Fill` 完成时关闭连接。</span><span class="sxs-lookup"><span data-stu-id="84af4-135">If `Fill` opened the connection, it also closes the connection when `Fill` is finished.</span></span> <span data-ttu-id="84af4-136">当处理单一操作（如 `Fill` 或 `Update`）时，这可以简化您的代码。</span><span class="sxs-lookup"><span data-stu-id="84af4-136">This can simplify your code when you deal with a single operation such as a `Fill` or an `Update`.</span></span> <span data-ttu-id="84af4-137">但是，如果您在执行多项需要打开连接的操作，则可以通过以下方式提高应用程序的性能：显式调用 `Open` 的 `Connection`方法，对数据源执行操作，然后调用 `Close` 的 `Connection`方法。</span><span class="sxs-lookup"><span data-stu-id="84af4-137">However, if you are performing multiple operations that require an open connection, you can improve the performance of your application by explicitly calling the `Open` method of the `Connection`, performing the operations against the data source, and then calling the `Close` method of the `Connection`.</span></span> <span data-ttu-id="84af4-138">应尝试使数据源的连接打开的时间尽可能短，以便释放资源供其他客户端应用程序使用。</span><span class="sxs-lookup"><span data-stu-id="84af4-138">You should try to keep connections to the data source open as briefly as possible to free resources for use by other client applications.</span></span>  
  
## <a name="multiple-result-sets"></a><span data-ttu-id="84af4-139">多个结果集</span><span class="sxs-lookup"><span data-stu-id="84af4-139">Multiple Result Sets</span></span>  

 <span data-ttu-id="84af4-140">如果 `DataAdapter` 遇到多个结果集，则将在 `DataSet`中创建多个表。</span><span class="sxs-lookup"><span data-stu-id="84af4-140">If the `DataAdapter` encounters multiple result sets, it creates multiple tables in the `DataSet`.</span></span> <span data-ttu-id="84af4-141">这些表的命名方式为默认名称 Table 加上*N*，N 从 0 开始递增，如以 Table0 为第一个表名，依次类推。</span><span class="sxs-lookup"><span data-stu-id="84af4-141">The tables are given an incremental default name of Table*N*, starting with "Table" for Table0.</span></span> <span data-ttu-id="84af4-142">如果以参数形式向 `Fill` 方法传递表名，则这些表的命名方式为默认名称 TableName 加上*N*，N 从 0 开始递增，如以 TableName0 为第一个表名，依次类推。</span><span class="sxs-lookup"><span data-stu-id="84af4-142">If a table name is passed as an argument to the `Fill` method, the tables are given an incremental default name of TableName*N*, starting with "TableName" for TableName0.</span></span>  
  
## <a name="populating-a-dataset-from-multiple-dataadapters"></a><span data-ttu-id="84af4-143">从多个 DataAdapter 填充 DataSet</span><span class="sxs-lookup"><span data-stu-id="84af4-143">Populating a DataSet from Multiple DataAdapters</span></span>  

 <span data-ttu-id="84af4-144">可以将任意数量的 `DataAdapter` 对象与一起使用 `DataSet` 。</span><span class="sxs-lookup"><span data-stu-id="84af4-144">Any number of `DataAdapter` objects can be used with a `DataSet`.</span></span> <span data-ttu-id="84af4-145">每个 `DataAdapter` 都可用于填充一个或多个 `DataTable` 对象并将更新解析回相关数据源。</span><span class="sxs-lookup"><span data-stu-id="84af4-145">Each `DataAdapter` can be used to fill one or more `DataTable` objects and resolve updates back to the relevant data source.</span></span> <span data-ttu-id="84af4-146">`DataRelation` 和 `Constraint` 对象可以在本地添加到 `DataSet` ，这样您就可以关联来自不同数据源的数据。</span><span class="sxs-lookup"><span data-stu-id="84af4-146">`DataRelation` and `Constraint` objects can be added to the `DataSet` locally, which enables you to relate data from dissimilar data sources.</span></span> <span data-ttu-id="84af4-147">例如， `DataSet` 可以包含来自 Microsoft SQL Server 数据库、通过 OLE DB 公开的 IBM DB2 数据库以及对 XML 进行流处理的数据源的数据。</span><span class="sxs-lookup"><span data-stu-id="84af4-147">For example, a `DataSet` can contain data from a Microsoft SQL Server database, an IBM DB2 database exposed through OLE DB, and a data source that streams XML.</span></span> <span data-ttu-id="84af4-148">一个或多个 `DataAdapter` 对象可以处理与每个数据源的通信。</span><span class="sxs-lookup"><span data-stu-id="84af4-148">One or more `DataAdapter` objects can handle communication to each data source.</span></span>  
  
### <a name="example"></a><span data-ttu-id="84af4-149">示例</span><span class="sxs-lookup"><span data-stu-id="84af4-149">Example</span></span>  

 <span data-ttu-id="84af4-150">以下代码示例从 Microsoft SQL Server 上的 `Northwind` 数据库填充客户列表，从存储在 Microsoft Access 2000 上的 `Northwind` 数据库填充订单列表。</span><span class="sxs-lookup"><span data-stu-id="84af4-150">The following code example populates a list of customers from the `Northwind` database on Microsoft SQL Server, and a list of orders from the `Northwind` database stored in Microsoft Access 2000.</span></span> <span data-ttu-id="84af4-151">已填充的表通过 `DataRelation`相关联，这样，客户列表将与相应客户的订单一起显示出来。</span><span class="sxs-lookup"><span data-stu-id="84af4-151">The filled tables are related with a `DataRelation`, and the list of customers is then displayed with the orders for that customer.</span></span> <span data-ttu-id="84af4-152">有关对象的详细信息 `DataRelation` ，请参阅 [添加 Datarelation](./dataset-datatable-dataview/adding-datarelations.md) 和 [导航 datarelation](./dataset-datatable-dataview/navigating-datarelations.md)。</span><span class="sxs-lookup"><span data-stu-id="84af4-152">For more information about `DataRelation` objects, see [Adding DataRelations](./dataset-datatable-dataview/adding-datarelations.md) and [Navigating DataRelations](./dataset-datatable-dataview/navigating-datarelations.md).</span></span>  
  
```vb  
' Assumes that customerConnection is a valid SqlConnection object.  
' Assumes that orderConnection is a valid OleDbConnection object.  
Dim custAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM dbo.Customers", customerConnection)  
  
Dim ordAdapter As OleDbDataAdapter = New OleDbDataAdapter( _  
  "SELECT * FROM Orders", orderConnection)  
  
Dim customerOrders As DataSet = New DataSet()  
custAdapter.Fill(customerOrders, "Customers")  
ordAdapter.Fill(customerOrders, "Orders")  
  
Dim relation As DataRelation = _  
  customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustomerID"), _
  customerOrders.Tables("Orders").Columns("CustomerID"))  
  
Dim pRow, cRow As DataRow  
For Each pRow In customerOrders.Tables("Customers").Rows  
  Console.WriteLine(pRow("CustomerID").ToString())  
  
  For Each cRow In pRow.GetChildRows(relation)  
    Console.WriteLine(vbTab & cRow("OrderID").ToString())  
  Next  
Next  
```  
  
```csharp  
// Assumes that customerConnection is a valid SqlConnection object.  
// Assumes that orderConnection is a valid OleDbConnection object.  
SqlDataAdapter custAdapter = new SqlDataAdapter(  
  "SELECT * FROM dbo.Customers", customerConnection);  
OleDbDataAdapter ordAdapter = new OleDbDataAdapter(  
  "SELECT * FROM Orders", orderConnection);  
  
DataSet customerOrders = new DataSet();  
  
custAdapter.Fill(customerOrders, "Customers");  
ordAdapter.Fill(customerOrders, "Orders");  
  
DataRelation relation = customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustomerID"],  
  customerOrders.Tables["Orders"].Columns["CustomerID"]);  
  
foreach (DataRow pRow in customerOrders.Tables["Customers"].Rows)  
{  
  Console.WriteLine(pRow["CustomerID"]);  
   foreach (DataRow cRow in pRow.GetChildRows(relation))  
    Console.WriteLine("\t" + cRow["OrderID"]);  
}  
```  
  
## <a name="sql-server-decimal-type"></a><span data-ttu-id="84af4-153">SQL Server Decimal 类型</span><span class="sxs-lookup"><span data-stu-id="84af4-153">SQL Server Decimal Type</span></span>  

 <span data-ttu-id="84af4-154">默认情况下， `DataSet` 使用 .NET Framework 数据类型存储数据。</span><span class="sxs-lookup"><span data-stu-id="84af4-154">By default, the `DataSet` stores data by using .NET Framework data types.</span></span> <span data-ttu-id="84af4-155">对于大多数应用程序，这些类型都提供了一种方便的数据源信息表示形式。</span><span class="sxs-lookup"><span data-stu-id="84af4-155">For most applications, these provide a convenient representation of data source information.</span></span> <span data-ttu-id="84af4-156">但是，当数据源中的数据类型是 SQL Server decimal 或 numeric 数据类型时，这种表示形式可能会导致问题。</span><span class="sxs-lookup"><span data-stu-id="84af4-156">However, this representation may cause a problem when the data type in the data source is a SQL Server decimal or numeric data type.</span></span> <span data-ttu-id="84af4-157">.NET Framework `decimal` 数据类型最多允许28个有效位，而 SQL Server `decimal` 数据类型允许38个有效位。</span><span class="sxs-lookup"><span data-stu-id="84af4-157">The .NET Framework `decimal` data type allows a maximum of 28 significant digits, whereas the SQL Server `decimal` data type allows 38 significant digits.</span></span> <span data-ttu-id="84af4-158">如果 `SqlDataAdapter` 在 `Fill` 操作过程中确定 SQL Server `decimal` 字段的精度大于 28 个字符，则不会将当前行添加到 `DataTable`。</span><span class="sxs-lookup"><span data-stu-id="84af4-158">If the `SqlDataAdapter` determines during a `Fill` operation that the precision of a SQL Server `decimal` field is larger than 28 characters, the current row is not added to the `DataTable`.</span></span> <span data-ttu-id="84af4-159">此时将发生 `FillError` 事件，使您能够确定是否将发生精度损失并作出适当的响应。</span><span class="sxs-lookup"><span data-stu-id="84af4-159">Instead the `FillError` event occurs, which enables you to determine whether a loss of precision will occur, and respond appropriately.</span></span> <span data-ttu-id="84af4-160">有关事件的详细信息 `FillError` ，请参阅 [处理 DataAdapter 事件](handling-dataadapter-events.md)。</span><span class="sxs-lookup"><span data-stu-id="84af4-160">For more information about the `FillError` event, see [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span> <span data-ttu-id="84af4-161">若要获取 SQL Server `decimal` 值，还可以使用 <xref:System.Data.SqlClient.SqlDataReader> 对象并调用 <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="84af4-161">To get the SQL Server `decimal` value, you can also use a <xref:System.Data.SqlClient.SqlDataReader> object and call the <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> method.</span></span>  
  
 <span data-ttu-id="84af4-162">ADO.NET 2.0 在中引入了的增强支持 <xref:System.Data.SqlTypes> `DataSet` 。</span><span class="sxs-lookup"><span data-stu-id="84af4-162">ADO.NET 2.0 introduced enhanced support for <xref:System.Data.SqlTypes> in the `DataSet`.</span></span> <span data-ttu-id="84af4-163">有关详细信息，请参阅 [SqlTypes and the DataSet](./sql/sqltypes-and-the-dataset.md)。</span><span class="sxs-lookup"><span data-stu-id="84af4-163">For more information, see [SqlTypes and the DataSet](./sql/sqltypes-and-the-dataset.md).</span></span>  
  
## <a name="ole-db-chapters"></a><span data-ttu-id="84af4-164">OLE DB 章节</span><span class="sxs-lookup"><span data-stu-id="84af4-164">OLE DB Chapters</span></span>  

 <span data-ttu-id="84af4-165">分层行集或章节（OLE DB 类型 `DBTYPE_HCHAPTER`、ADO 类型 `adChapter`）可用于填充 `DataSet`的内容。</span><span class="sxs-lookup"><span data-stu-id="84af4-165">Hierarchical rowsets, or chapters (OLE DB type `DBTYPE_HCHAPTER`, ADO type `adChapter`) can be used to fill the contents of a `DataSet`.</span></span> <span data-ttu-id="84af4-166">当 <xref:System.Data.OleDb.OleDbDataAdapter> 在 `Fill` 操作过程中遇到章节列时，将为章节列创建一个 `DataTable` ，并使用章节中的列和行填充该表。</span><span class="sxs-lookup"><span data-stu-id="84af4-166">When the <xref:System.Data.OleDb.OleDbDataAdapter> encounters a chaptered column during a `Fill` operation, a `DataTable` is created for the chaptered column, and that table is filled with the columns and rows from the chapter.</span></span> <span data-ttu-id="84af4-167">为章节列创建的表使用父表名称和章节列名称来命名，其形式为“*ParentTableNameChapteredColumnName*”。</span><span class="sxs-lookup"><span data-stu-id="84af4-167">The table created for the chaptered column is named by using both the parent table name and the chaptered column name in the form "*ParentTableNameChapteredColumnName*".</span></span> <span data-ttu-id="84af4-168">如果 `DataSet` 中已存在与章节列的名称相匹配的表，则将使用章节数据填充当前表。</span><span class="sxs-lookup"><span data-stu-id="84af4-168">If a table already exists in the `DataSet` that matches the name of the chaptered column, the current table is filled with the chapter data.</span></span> <span data-ttu-id="84af4-169">如果现有表中不存在与章节中的列相匹配的列，则将添加新列。</span><span class="sxs-lookup"><span data-stu-id="84af4-169">If there is no column in an existing table that matches a column found in the chapter, a new column is added.</span></span>  
  
 <span data-ttu-id="84af4-170">在使用章节列中的数据填充 `DataSet` 中的表之前，将创建分层行集的父表和子表之间的关系，方法是向父表和子表添加一个整数列，将父列设置为自动递增，然后使用两个表中所添加的列来创建 `DataRelation` 。</span><span class="sxs-lookup"><span data-stu-id="84af4-170">Before the tables in the `DataSet` are filled with the data in the chaptered columns, a relation is created between the parent and child tables of the hierarchical rowset by adding an integer column to both the parent and child table, setting the parent column to auto-increment, and creating a `DataRelation` using the added columns from both tables.</span></span> <span data-ttu-id="84af4-171">所添加的关系使用父表和章节列名称来命名，其形式为“*ParentTableNameChapterColumnName*”。</span><span class="sxs-lookup"><span data-stu-id="84af4-171">The added relation is named by using the parent table and chapter column names in the form "*ParentTableNameChapterColumnName*".</span></span>  
  
 <span data-ttu-id="84af4-172">请注意，相关列仅存在于 `DataSet`中。</span><span class="sxs-lookup"><span data-stu-id="84af4-172">Note that the related column only exists in the `DataSet`.</span></span> <span data-ttu-id="84af4-173">如果在随后从数据源进行填充，则将使新行被添加到表中，而不是使更改被并入现有行。</span><span class="sxs-lookup"><span data-stu-id="84af4-173">Subsequent fills from the data source can cause new rows to be added to the tables instead of changes being merged into existing rows.</span></span>  
  
 <span data-ttu-id="84af4-174">另请注意，如果使用采用 `DataAdapter.Fill` 的 `DataTable`重载，则将只填充该表。</span><span class="sxs-lookup"><span data-stu-id="84af4-174">Note also that, if you use the `DataAdapter.Fill` overload that takes a `DataTable`, only that table will be filled.</span></span> <span data-ttu-id="84af4-175">仍会将自动递增整数列添加到该表中，但不会创建或填充任何子表并且不会创建任何关系。</span><span class="sxs-lookup"><span data-stu-id="84af4-175">An auto-incrementing integer column will still be added to the table, but no child table will be created or filled, and no relation will be created.</span></span>  
  
 <span data-ttu-id="84af4-176">以下示例使用 MSDataShape 提供程序为客户列表中的每个客户生成订单的章节列。</span><span class="sxs-lookup"><span data-stu-id="84af4-176">The following example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span> <span data-ttu-id="84af4-177">然后使用相应数据来填充 `DataSet` 。</span><span class="sxs-lookup"><span data-stu-id="84af4-177">A `DataSet` is then filled with the data.</span></span>  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection( _  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" & _  
  "Data Source=(local);Integrated " & _  
  "Security=SSPI;Initial Catalog=northwind")  
  
Dim adapter As OleDbDataAdapter = New OleDbDataAdapter( _  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " & _  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS Orders " & _  
  "RELATE CustomerID TO CustomerID)", connection)  
  
Dim customers As DataSet = New DataSet()  
  
adapter.Fill(customers, "Customers")  
End Using  
```  
  
```csharp  
using (OleDbConnection connection = new OleDbConnection("Provider=MSDataShape;Data Provider=SQLOLEDB;" +  
  "Data Source=(local);Integrated Security=SSPI;Initial Catalog=northwind"))  
{  
OleDbDataAdapter adapter = new OleDbDataAdapter("SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS Orders " +  
  "RELATE CustomerID TO CustomerID)", connection);  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
}  
```  
  
 <span data-ttu-id="84af4-178">完成 `Fill` 操作后， `DataSet` 包含两个表： `Customers` 和 `CustomersOrders`，其中 `CustomersOrders` 表示章节列。</span><span class="sxs-lookup"><span data-stu-id="84af4-178">When the `Fill` operation is complete, the `DataSet` contains two tables: `Customers` and `CustomersOrders`, where `CustomersOrders` represents the chaptered column.</span></span> <span data-ttu-id="84af4-179">将名为 `Orders` 的附加列添加到 `Customers` 表中，将名为 `CustomersOrders` 的附加列添加到 `CustomersOrders` 表中。</span><span class="sxs-lookup"><span data-stu-id="84af4-179">An additional column named `Orders` is added to the `Customers` table, and an additional column named `CustomersOrders` is added to the `CustomersOrders` table.</span></span> <span data-ttu-id="84af4-180">将 `Orders` 表中的 `Customers` 列设置为自动递增。</span><span class="sxs-lookup"><span data-stu-id="84af4-180">The `Orders` column in the `Customers` table is set to auto-increment.</span></span> <span data-ttu-id="84af4-181">`DataRelation`这个 `CustomersOrders`是通过向上述两个表添加列创建的，其中以 `Customers` 表作为父表。</span><span class="sxs-lookup"><span data-stu-id="84af4-181">A `DataRelation`, `CustomersOrders`, is created by using the columns that were added to the tables with `Customers` as the parent table.</span></span> <span data-ttu-id="84af4-182">下表显示了一些示例结果。</span><span class="sxs-lookup"><span data-stu-id="84af4-182">The following tables show some sample results.</span></span>  
  
### <a name="tablename-customers"></a><span data-ttu-id="84af4-183">TableName：Customers</span><span class="sxs-lookup"><span data-stu-id="84af4-183">TableName: Customers</span></span>  
  
|<span data-ttu-id="84af4-184">CustomerID</span><span class="sxs-lookup"><span data-stu-id="84af4-184">CustomerID</span></span>|<span data-ttu-id="84af4-185">CompanyName</span><span class="sxs-lookup"><span data-stu-id="84af4-185">CompanyName</span></span>|<span data-ttu-id="84af4-186">Orders</span><span class="sxs-lookup"><span data-stu-id="84af4-186">Orders</span></span>|  
|----------------|-----------------|------------|  
|<span data-ttu-id="84af4-187">ALFKI</span><span class="sxs-lookup"><span data-stu-id="84af4-187">ALFKI</span></span>|<span data-ttu-id="84af4-188">Alfreds Futterkiste</span><span class="sxs-lookup"><span data-stu-id="84af4-188">Alfreds Futterkiste</span></span>|<span data-ttu-id="84af4-189">0</span><span class="sxs-lookup"><span data-stu-id="84af4-189">0</span></span>|  
|<span data-ttu-id="84af4-190">ANATR</span><span class="sxs-lookup"><span data-stu-id="84af4-190">ANATR</span></span>|<span data-ttu-id="84af4-191">Ana Trujillo Emparedados y helados</span><span class="sxs-lookup"><span data-stu-id="84af4-191">Ana Trujillo Emparedados y helados</span></span>|<span data-ttu-id="84af4-192">1</span><span class="sxs-lookup"><span data-stu-id="84af4-192">1</span></span>|  
  
### <a name="tablename-customersorders"></a><span data-ttu-id="84af4-193">TableName：CustomersOrders</span><span class="sxs-lookup"><span data-stu-id="84af4-193">TableName: CustomersOrders</span></span>  
  
|<span data-ttu-id="84af4-194">CustomerID</span><span class="sxs-lookup"><span data-stu-id="84af4-194">CustomerID</span></span>|<span data-ttu-id="84af4-195">OrderID</span><span class="sxs-lookup"><span data-stu-id="84af4-195">OrderID</span></span>|<span data-ttu-id="84af4-196">CustomersOrders</span><span class="sxs-lookup"><span data-stu-id="84af4-196">CustomersOrders</span></span>|  
|----------------|-------------|---------------------|  
|<span data-ttu-id="84af4-197">ALFKI</span><span class="sxs-lookup"><span data-stu-id="84af4-197">ALFKI</span></span>|<span data-ttu-id="84af4-198">10643</span><span class="sxs-lookup"><span data-stu-id="84af4-198">10643</span></span>|<span data-ttu-id="84af4-199">0</span><span class="sxs-lookup"><span data-stu-id="84af4-199">0</span></span>|  
|<span data-ttu-id="84af4-200">ALFKI</span><span class="sxs-lookup"><span data-stu-id="84af4-200">ALFKI</span></span>|<span data-ttu-id="84af4-201">10692</span><span class="sxs-lookup"><span data-stu-id="84af4-201">10692</span></span>|<span data-ttu-id="84af4-202">0</span><span class="sxs-lookup"><span data-stu-id="84af4-202">0</span></span>|  
|<span data-ttu-id="84af4-203">ANATR</span><span class="sxs-lookup"><span data-stu-id="84af4-203">ANATR</span></span>|<span data-ttu-id="84af4-204">10308</span><span class="sxs-lookup"><span data-stu-id="84af4-204">10308</span></span>|<span data-ttu-id="84af4-205">1</span><span class="sxs-lookup"><span data-stu-id="84af4-205">1</span></span>|  
|<span data-ttu-id="84af4-206">ANATR</span><span class="sxs-lookup"><span data-stu-id="84af4-206">ANATR</span></span>|<span data-ttu-id="84af4-207">10625</span><span class="sxs-lookup"><span data-stu-id="84af4-207">10625</span></span>|<span data-ttu-id="84af4-208">1</span><span class="sxs-lookup"><span data-stu-id="84af4-208">1</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="84af4-209">请参阅</span><span class="sxs-lookup"><span data-stu-id="84af4-209">See also</span></span>

- [<span data-ttu-id="84af4-210">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="84af4-210">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="84af4-211">ADO.NET 中的数据类型映射</span><span class="sxs-lookup"><span data-stu-id="84af4-211">Data Type Mappings in ADO.NET</span></span>](data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="84af4-212">使用 DbDataAdapter 修改数据</span><span class="sxs-lookup"><span data-stu-id="84af4-212">Modifying Data with a DbDataAdapter</span></span>](modifying-data-with-a-dbdataadapter.md)
- [<span data-ttu-id="84af4-213">多重活动结果集 (MARS)</span><span class="sxs-lookup"><span data-stu-id="84af4-213">Multiple Active Result Sets (MARS)</span></span>](./sql/multiple-active-result-sets-mars.md)
- [<span data-ttu-id="84af4-214">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="84af4-214">ADO.NET Overview</span></span>](ado-net-overview.md)

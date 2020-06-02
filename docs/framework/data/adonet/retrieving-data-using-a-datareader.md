---
title: 使用 DataReader 检索 ADO 数据
description: 了解如何使用此示例代码在 ADO.NET 中使用 DataReader 检索数据。 DataReader 提供未缓冲的数据流。
ms.date: 10/29/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 6e5161cc325bf0379bb9241b99c473c539ad1081
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286593"
---
# <a name="retrieve-data-using-a-datareader"></a><span data-ttu-id="afef8-104">使用 DataReader 检索数据</span><span class="sxs-lookup"><span data-stu-id="afef8-104">Retrieve data using a DataReader</span></span>
<span data-ttu-id="afef8-105">若要使用**DataReader**检索数据，请创建**命令**对象的实例，然后通过调用**ExecuteReader**来创建**DataReader** ，以从数据源中检索行。</span><span class="sxs-lookup"><span data-stu-id="afef8-105">To retrieve data using a **DataReader**, create an instance of the **Command** object, and then create a **DataReader** by calling **Command.ExecuteReader** to retrieve rows from a data source.</span></span> <span data-ttu-id="afef8-106">**DataReader**提供了一个未缓冲的数据流，该数据流允许过程逻辑有效地按顺序处理数据源中的结果。</span><span class="sxs-lookup"><span data-stu-id="afef8-106">The **DataReader** provides an unbuffered stream of data that allows procedural logic to efficiently process results from a data source sequentially.</span></span> <span data-ttu-id="afef8-107">当检索大量数据时， **DataReader**是一个不错的选择，因为数据不会缓存在内存中。</span><span class="sxs-lookup"><span data-stu-id="afef8-107">The **DataReader** is a good choice when you're retrieving large amounts of data because the data is not cached in memory.</span></span>

<span data-ttu-id="afef8-108">下面的示例阐释了如何使用**DataReader**，其中 `reader` 表示有效的 datareader 并 `command` 表示有效的命令对象。</span><span class="sxs-lookup"><span data-stu-id="afef8-108">The following example illustrates using a **DataReader**, where `reader` represents a valid DataReader and `command` represents a valid Command object.</span></span>  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

<span data-ttu-id="afef8-109">使用**DataReader**方法可从查询结果中获取行。</span><span class="sxs-lookup"><span data-stu-id="afef8-109">Use the **DataReader.Read** method to obtain a row from the query results.</span></span> <span data-ttu-id="afef8-110">通过向**DataReader**传递列的名称或序号，可以访问返回行的每一列。</span><span class="sxs-lookup"><span data-stu-id="afef8-110">You can access each column of the returned row by passing the name or ordinal number of the column to the **DataReader**.</span></span> <span data-ttu-id="afef8-111">但是，为获得最佳性能， **DataReader**提供一系列方法，使你可以访问其本机数据类型（**GetDateTime**、 **GetDouble**、 **GetGuid**、 **GetInt32**等）中的列值。</span><span class="sxs-lookup"><span data-stu-id="afef8-111">However, for best performance, the **DataReader** provides a series of methods that allow you to access column values in their native data types (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, and so on).</span></span> <span data-ttu-id="afef8-112">有关特定于数据访问接口的**datareader**的类型化访问器方法的列表，请参阅 <xref:System.Data.OleDb.OleDbDataReader> 和 <xref:System.Data.SqlClient.SqlDataReader> 。</span><span class="sxs-lookup"><span data-stu-id="afef8-112">For a list of typed accessor methods for data provider-specific **DataReaders**, see <xref:System.Data.OleDb.OleDbDataReader> and <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="afef8-113">当您知道基础数据类型时，使用类型化访问器方法可减少检索列值时所需的类型转换量。</span><span class="sxs-lookup"><span data-stu-id="afef8-113">Using the typed accessor methods when you know the underlying data type reduces the amount of type conversion required when retrieving the column value.</span></span>  
  
 <span data-ttu-id="afef8-114">下面的示例循环访问**DataReader**对象并返回每行中的两列。</span><span class="sxs-lookup"><span data-stu-id="afef8-114">The following example iterates through a **DataReader** object and returns two columns from each row.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a><span data-ttu-id="afef8-115">关闭 DataReader</span><span class="sxs-lookup"><span data-stu-id="afef8-115">Closing the DataReader</span></span>  
 <span data-ttu-id="afef8-116">当完成使用**DataReader**对象时，请始终调用**Close**方法。</span><span class="sxs-lookup"><span data-stu-id="afef8-116">Always call the **Close** method when you have finished using the **DataReader** object.</span></span>  
  
 <span data-ttu-id="afef8-117">如果你的**命令**包含输出参数或返回值，则在**DataReader**关闭之前，这些值将不可用。</span><span class="sxs-lookup"><span data-stu-id="afef8-117">If your **Command** contains output parameters or return values, those values are not available until the **DataReader** is closed.</span></span>  
  
 <span data-ttu-id="afef8-118">当**datareader**打开时，该**datareader**以独占方式使用**连接**。</span><span class="sxs-lookup"><span data-stu-id="afef8-118">While a **DataReader** is open, the **Connection** is in use exclusively by that **DataReader**.</span></span> <span data-ttu-id="afef8-119">不能对**连接**执行任何命令，包括创建另一个**datareader**，直到原始**DataReader**关闭为止。</span><span class="sxs-lookup"><span data-stu-id="afef8-119">You cannot execute any commands for the **Connection**, including creating another **DataReader**, until the original **DataReader** is closed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="afef8-120">不要对类的**Finalize**方法中的**连接**、 **DataReader**或任何其他托管对象调用**Close**或**Dispose**操作。</span><span class="sxs-lookup"><span data-stu-id="afef8-120">Do not call **Close** or **Dispose** on a **Connection**, a **DataReader**, or any other managed object in the **Finalize** method of your class.</span></span> <span data-ttu-id="afef8-121">在终结器中，仅释放类直接拥有的非托管资源。</span><span class="sxs-lookup"><span data-stu-id="afef8-121">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="afef8-122">如果类不拥有任何非托管资源，则不要在类定义中包括**Finalize**方法。</span><span class="sxs-lookup"><span data-stu-id="afef8-122">If your class does not own any unmanaged resources, do not include a **Finalize** method in your class definition.</span></span> <span data-ttu-id="afef8-123">有关详细信息，请参阅[垃圾回收](../../../standard/garbage-collection/index.md)。</span><span class="sxs-lookup"><span data-stu-id="afef8-123">For more information, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a><span data-ttu-id="afef8-124">使用 NextResult 检索多个结果集</span><span class="sxs-lookup"><span data-stu-id="afef8-124">Retrieving multiple result sets using NextResult</span></span>  
 <span data-ttu-id="afef8-125">如果**DataReader**返回多个结果集，请调用**NextResult**方法以按顺序循环访问结果集。</span><span class="sxs-lookup"><span data-stu-id="afef8-125">If the **DataReader** returns multiple result sets, call the **NextResult** method to iterate through the result sets sequentially.</span></span> <span data-ttu-id="afef8-126">以下示例显示 <xref:System.Data.SqlClient.SqlDataReader> 如何使用 <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> 方法处理两个 SELECT 语句的结果。</span><span class="sxs-lookup"><span data-stu-id="afef8-126">The following example shows the <xref:System.Data.SqlClient.SqlDataReader> processing the results of two SELECT statements using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a><span data-ttu-id="afef8-127">从 DataReader 获取架构信息</span><span class="sxs-lookup"><span data-stu-id="afef8-127">Getting schema information from the DataReader</span></span>  
 <span data-ttu-id="afef8-128">当**DataReader**打开时，可以使用**GetSchemaTable**方法检索有关当前结果集的架构信息。</span><span class="sxs-lookup"><span data-stu-id="afef8-128">While a **DataReader** is open, you can retrieve schema information about the current result set using the **GetSchemaTable** method.</span></span> <span data-ttu-id="afef8-129">**GetSchemaTable**返回一个 <xref:System.Data.DataTable> 用行和列填充的对象，其中包含当前结果集的架构信息。</span><span class="sxs-lookup"><span data-stu-id="afef8-129">**GetSchemaTable** returns a <xref:System.Data.DataTable> object populated with rows and columns that contain the schema information for the current result set.</span></span> <span data-ttu-id="afef8-130">对于结果集的每一列， **DataTable**都包含一行。</span><span class="sxs-lookup"><span data-stu-id="afef8-130">The **DataTable** contains one row for each column of the result set.</span></span> <span data-ttu-id="afef8-131">架构表中的每一列都映射到在结果集的行中返回的列的属性，其中**ColumnName**是属性的名称，列的值是属性的值。</span><span class="sxs-lookup"><span data-stu-id="afef8-131">Each column of the schema table maps to a property of the columns returned in the rows of the result set, where the **ColumnName** is the name of the property and the value of the column is the value of the property.</span></span> <span data-ttu-id="afef8-132">下面的示例写出**DataReader**的架构信息。</span><span class="sxs-lookup"><span data-stu-id="afef8-132">The following example writes out the schema information for **DataReader**.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a><span data-ttu-id="afef8-133">使用 OLE DB 章节</span><span class="sxs-lookup"><span data-stu-id="afef8-133">Working with OLE DB chapters</span></span>  
 <span data-ttu-id="afef8-134">可以使用检索分层行集或章节（OLE DB 类型**DBTYPE_HCHAPTER**，ADO 类型**adChapter**） <xref:System.Data.OleDb.OleDbDataReader> 。</span><span class="sxs-lookup"><span data-stu-id="afef8-134">Hierarchical rowsets, or chapters (OLE DB type **DBTYPE_HCHAPTER**, ADO type **adChapter**), can be retrieved using the <xref:System.Data.OleDb.OleDbDataReader>.</span></span> <span data-ttu-id="afef8-135">当包含某一章节的查询作为**datareader**返回时，该章节将作为该**datareader**中的列返回，并作为**datareader**对象公开。</span><span class="sxs-lookup"><span data-stu-id="afef8-135">When a query that includes a chapter is returned as a **DataReader**, the chapter is returned as a column in that **DataReader** and is exposed as a **DataReader** object.</span></span>  
  
 <span data-ttu-id="afef8-136">ADO.NET**数据集**还可用于通过使用表之间的父子关系来表示分层行集。</span><span class="sxs-lookup"><span data-stu-id="afef8-136">The ADO.NET **DataSet** can also be used to represent hierarchical rowsets by using parent-child relationships between tables.</span></span> <span data-ttu-id="afef8-137">有关详细信息，请参阅[数据集、数据表和 dataview](./dataset-datatable-dataview/index.md)。</span><span class="sxs-lookup"><span data-stu-id="afef8-137">For more information, see [DataSets, DataTables, and DataViews](./dataset-datatable-dataview/index.md).</span></span>  
  
 <span data-ttu-id="afef8-138">以下代码示例使用 MSDataShape 提供程序来为客户列表中的每个客户生成订单的章节列。</span><span class="sxs-lookup"><span data-stu-id="afef8-138">The following code example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span>  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection(
    "Provider=MSDataShape;Data Provider=SQLOLEDB;" &
    "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind")

    Using custCMD As OleDbCommand = New OleDbCommand(
        "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " &
        "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " &
        "RELATE CustomerID TO CustomerID)", connection)

        connection.Open()

        Using custReader As OleDbDataReader = custCMD.ExecuteReader()

            Do While custReader.Read()
                Console.WriteLine("Orders for " & custReader.GetString(1))
                ' custReader.GetString(1) = CompanyName  

                Using orderReader As OleDbDataReader = custReader.GetValue(2)
                    ' custReader.GetValue(2) = Orders chapter as DataReader  

                    Do While orderReader.Read()
                        Console.WriteLine(vbTab & orderReader.GetInt32(1))
                        ' orderReader.GetInt32(1) = OrderID  
                    Loop
                    orderReader.Close()
                End Using
            Loop
            ' Make sure to always close readers and connections.  
            custReader.Close()
        End Using
    End Using
End Using
```  
  
```csharp  
using (OleDbConnection connection = new OleDbConnection(
    "Provider=MSDataShape;Data Provider=SQLOLEDB;" +
    "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind"))
{
    using (OleDbCommand custCMD = new OleDbCommand(
        "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +
        "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " +
        "RELATE CustomerID TO CustomerID)", connection))
    {
        connection.Open();

        using (OleDbDataReader custReader = custCMD.ExecuteReader())
        {

            while (custReader.Read())
            {
                Console.WriteLine("Orders for " + custReader.GetString(1));
                // custReader.GetString(1) = CompanyName  

                using (OleDbDataReader orderReader = (OleDbDataReader)custReader.GetValue(2))
                {
                    // custReader.GetValue(2) = Orders chapter as DataReader  

                    while (orderReader.Read())
                        Console.WriteLine("\t" + orderReader.GetInt32(1));
                    // orderReader.GetInt32(1) = OrderID  
                    orderReader.Close();
                }
            }
            // Make sure to always close readers and connections.  
            custReader.Close();
        }
    }
}
```  
  
## <a name="returning-results-with-oracle-ref-cursors"></a><span data-ttu-id="afef8-139">用 Oracle REF cursor 返回结果</span><span class="sxs-lookup"><span data-stu-id="afef8-139">Returning results with Oracle REF CURSORs</span></span>  
 <span data-ttu-id="afef8-140">Oracle .NET Framework 数据提供程序支持使用 Oracle REF CURSOR 返回查询结果。</span><span class="sxs-lookup"><span data-stu-id="afef8-140">The .NET Framework Data Provider for Oracle supports the use of Oracle REF CURSORs to return a query result.</span></span> <span data-ttu-id="afef8-141">Oracle REF CURSOR 以 <xref:System.Data.OracleClient.OracleDataReader> 的形式返回。</span><span class="sxs-lookup"><span data-stu-id="afef8-141">An Oracle REF CURSOR is returned as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 <span data-ttu-id="afef8-142">您可以 <xref:System.Data.OracleClient.OracleDataReader> 使用方法检索表示 ORACLE REF CURSOR 的对象 <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> 。</span><span class="sxs-lookup"><span data-stu-id="afef8-142">You can retrieve an <xref:System.Data.OracleClient.OracleDataReader> object that represents an Oracle REF CURSOR by using the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> method.</span></span> <span data-ttu-id="afef8-143">还可以指定 <xref:System.Data.OracleClient.OracleCommand> 返回一个或多个 ORACLE REF cursor 的，作为用于填充的的**SelectCommand** <xref:System.Data.OracleClient.OracleDataAdapter> <xref:System.Data.DataSet> 。</span><span class="sxs-lookup"><span data-stu-id="afef8-143">You can also specify an <xref:System.Data.OracleClient.OracleCommand> that returns one or more Oracle REF CURSORs as the **SelectCommand** for an <xref:System.Data.OracleClient.OracleDataAdapter> used to fill a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="afef8-144">若要访问从 Oracle 数据源返回的 REF CURSOR，请 <xref:System.Data.OracleClient.OracleCommand> 为查询创建，并将引用该引用光标的 output 参数添加到的 <xref:System.Data.OracleClient.OracleCommand.Parameters> 集合中 <xref:System.Data.OracleClient.OracleCommand> 。</span><span class="sxs-lookup"><span data-stu-id="afef8-144">To access a REF CURSOR returned from an Oracle data source, create an <xref:System.Data.OracleClient.OracleCommand> for your query and add an output parameter that references the REF CURSOR to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection of your <xref:System.Data.OracleClient.OracleCommand>.</span></span> <span data-ttu-id="afef8-145">该参数的名称必须与查询中的 REF CURSOR 参数名称相匹配。</span><span class="sxs-lookup"><span data-stu-id="afef8-145">The name of the parameter must match the name of the REF CURSOR parameter in your query.</span></span> <span data-ttu-id="afef8-146">将参数的类型设置为 <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="afef8-146">Set the type of the parameter to <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>.</span></span> <span data-ttu-id="afef8-147">的 <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> 方法 <xref:System.Data.OracleClient.OracleCommand> <xref:System.Data.OracleClient.OracleDataReader> 为 REF CURSOR 返回一个。</span><span class="sxs-lookup"><span data-stu-id="afef8-147">The <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method of your <xref:System.Data.OracleClient.OracleCommand> returns an <xref:System.Data.OracleClient.OracleDataReader> for the REF CURSOR.</span></span>  
  
 <span data-ttu-id="afef8-148">如果 <xref:System.Data.OracleClient.OracleCommand> 返回多个 REF 游标，请添加多个输出参数。</span><span class="sxs-lookup"><span data-stu-id="afef8-148">If your <xref:System.Data.OracleClient.OracleCommand> returns multiple REF CURSORS, add multiple output parameters.</span></span> <span data-ttu-id="afef8-149">可以通过调用方法来访问不同的 REF cursor <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="afef8-149">You can access the different REF CURSORs by calling the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="afef8-150">对的调用将 <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> 返回 <xref:System.Data.OracleClient.OracleDataReader> 引用第一个引用游标的。</span><span class="sxs-lookup"><span data-stu-id="afef8-150">The call to <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> returns an <xref:System.Data.OracleClient.OracleDataReader> referencing the first REF CURSOR.</span></span> <span data-ttu-id="afef8-151">然后，可以调用 <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> 方法来访问后续的 REF cursor。</span><span class="sxs-lookup"><span data-stu-id="afef8-151">You can then call the <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> method to access subsequent REF CURSORs.</span></span> <span data-ttu-id="afef8-152">尽管集合中的参数 <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> 与 REF CURSOR 输出参数按名称匹配，但 <xref:System.Data.OracleClient.OracleDataReader> 会按照它们添加到集合中的顺序来访问这些参数 <xref:System.Data.OracleClient.OracleCommand.Parameters> 。</span><span class="sxs-lookup"><span data-stu-id="afef8-152">Although the parameters in your <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection match the REF CURSOR output parameters by name, the <xref:System.Data.OracleClient.OracleDataReader> accesses them in the order in which they were added to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection.</span></span>  
  
 <span data-ttu-id="afef8-153">例如，请看下面这个 Oracle 包和包正文。</span><span class="sxs-lookup"><span data-stu-id="afef8-153">For example, consider the following Oracle package and package body.</span></span>  
  
```sql
CREATE OR REPLACE PACKAGE CURSPKG AS
  TYPE T_CURSOR IS REF CURSOR;
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,
    DEPTCURSOR OUT T_CURSOR);
END CURSPKG;  
  
CREATE OR REPLACE PACKAGE BODY CURSPKG AS
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,
    DEPTCURSOR OUT T_CURSOR)
  IS
  BEGIN
    OPEN EMPCURSOR FOR SELECT * FROM DEMO.EMPLOYEE;
    OPEN DEPTCURSOR FOR SELECT * FROM DEMO.DEPARTMENT;
  END OPEN_TWO_CURSORS;
END CURSPKG;
```  
  
 <span data-ttu-id="afef8-154">下面的代码创建一个 <xref:System.Data.OracleClient.OracleCommand> ，它通过将类型的两个参数添加到集合中，从以前的 Oracle 包返回 REF cursor <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="afef8-154">The following code creates an <xref:System.Data.OracleClient.OracleCommand> that returns the REF CURSORs from the previous Oracle package by adding two parameters of type <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> to the <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection.</span></span>  
  
```vb  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
```  
  
```csharp  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
```  
  
 <span data-ttu-id="afef8-155">下面的代码使用的和方法返回前一个命令的 <xref:System.Data.OracleClient.OracleDataReader.Read> 结果 <xref:System.Data.OracleClient.OracleDataReader.NextResult> <xref:System.Data.OracleClient.OracleDataReader> 。</span><span class="sxs-lookup"><span data-stu-id="afef8-155">The following code returns the results of the previous command using the <xref:System.Data.OracleClient.OracleDataReader.Read> and <xref:System.Data.OracleClient.OracleDataReader.NextResult> methods of the <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="afef8-156">REF CURSOR 参数按顺序返回。</span><span class="sxs-lookup"><span data-stu-id="afef8-156">The REF CURSOR parameters are returned in order.</span></span>  
  
```vb  
oraConn.Open()  
  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.CommandType = CommandType.StoredProcedure  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
  
Dim reader As OracleDataReader = cursCmd.ExecuteReader()  
  
Console.WriteLine(vbCrLf & "Emp ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2))  
Loop  
  
reader.NextResult()  
  
Console.WriteLine(vbCrLf & "Dept ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}", reader.GetOracleNumber(0), reader.GetString(1))  
Loop  
' Make sure to always close readers and connections.  
reader.Close()  
oraConn.Close()  
```  
  
```csharp  
oraConn.Open();  
  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.CommandType = CommandType.StoredProcedure;  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
  
OracleDataReader reader = cursCmd.ExecuteReader();  
  
Console.WriteLine("\nEmp ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2));  
  
reader.NextResult();  
  
Console.WriteLine("\nDept ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}", reader.GetOracleNumber(0), reader.GetString(1));  
// Make sure to always close readers and connections.  
reader.Close();  
oraConn.Close();  
```  
  
 <span data-ttu-id="afef8-157">下面的示例使用上一个命令， <xref:System.Data.DataSet> 用 Oracle 包的结果填充。</span><span class="sxs-lookup"><span data-stu-id="afef8-157">The following example uses the previous command to populate a <xref:System.Data.DataSet> with the results of the Oracle package.</span></span>  
  
```vb  
Dim ds As DataSet = New DataSet()  
  
Dim adapter As OracleDataAdapter = New OracleDataAdapter(cursCmd)  
adapter.TableMappings.Add("Table", "Employees")  
adapter.TableMappings.Add("Table1", "Departments")  
  
adapter.Fill(ds)  
```  
  
```csharp  
DataSet ds = new DataSet();  
  
OracleDataAdapter adapter = new OracleDataAdapter(cursCmd);  
adapter.TableMappings.Add("Table", "Employees");  
adapter.TableMappings.Add("Table1", "Departments");  
  
adapter.Fill(ds);  
```

> [!NOTE]
> <span data-ttu-id="afef8-158">为了避免**OverflowException**，我们建议你还在将值存储在中之前，先处理从 Oracle NUMBER 类型到有效 .NET Framework 类型的任何转换 <xref:System.Data.DataRow> 。</span><span class="sxs-lookup"><span data-stu-id="afef8-158">To avoid an **OverflowException**, we recommend that you also handle any conversion from the Oracle NUMBER type to a valid .NET Framework type before storing the value in a <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="afef8-159">您可以使用 <xref:System.Data.Common.DataAdapter.FillError> 事件来确定是否发生了**OverflowException** 。</span><span class="sxs-lookup"><span data-stu-id="afef8-159">You can use the <xref:System.Data.Common.DataAdapter.FillError> event to determine if an **OverflowException** has occurred.</span></span> <span data-ttu-id="afef8-160">有关事件的详细信息 <xref:System.Data.Common.DataAdapter.FillError> ，请参阅[处理 DataAdapter 事件](handling-dataadapter-events.md)。</span><span class="sxs-lookup"><span data-stu-id="afef8-160">For more information on the <xref:System.Data.Common.DataAdapter.FillError> event, see [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afef8-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="afef8-161">See also</span></span>

- [<span data-ttu-id="afef8-162">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="afef8-162">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="afef8-163">命令和参数</span><span class="sxs-lookup"><span data-stu-id="afef8-163">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="afef8-164">检索数据库架构信息</span><span class="sxs-lookup"><span data-stu-id="afef8-164">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)
- [<span data-ttu-id="afef8-165">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="afef8-165">ADO.NET Overview</span></span>](ado-net-overview.md)

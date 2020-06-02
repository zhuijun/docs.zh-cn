---
title: 表值参数
description: 了解如何使用表值参数将多行数据从客户端应用程序封送到 SQL Server。
ms.date: 10/12/2018
dev_langs:
- csharp
- vb
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.openlocfilehash: 7b1f0a6c416f660f06cea099197ba136f84407f9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286192"
---
# <a name="table-valued-parameters"></a><span data-ttu-id="18e1d-103">表值参数</span><span class="sxs-lookup"><span data-stu-id="18e1d-103">Table-Valued Parameters</span></span>
<span data-ttu-id="18e1d-104">表值参数提供了一将多行数据从客户端应用程序封送到 SQL Server 的种简单方法，而无需进行多次往返或特殊的服务器端逻辑来处理数据。</span><span class="sxs-lookup"><span data-stu-id="18e1d-104">Table-valued parameters provide an easy way to marshal multiple rows of data from a client application to SQL Server without requiring multiple round trips or special server-side logic for processing the data.</span></span> <span data-ttu-id="18e1d-105">可使用表值参数来封装客户端应用程序中的数据行，并以单个参数化命令将数据发送到服务器。</span><span class="sxs-lookup"><span data-stu-id="18e1d-105">You can use table-valued parameters to encapsulate rows of data in a client application and send the data to the server in a single parameterized command.</span></span> <span data-ttu-id="18e1d-106">传入数据行存储在随后可使用 Transact-SQL 进行操作的表变量中。</span><span class="sxs-lookup"><span data-stu-id="18e1d-106">The incoming data rows are stored in a table variable that can then be operated on by using Transact-SQL.</span></span>  
  
 <span data-ttu-id="18e1d-107">可以使用标准的 Transact-SQL SELECT 语句来访问表值参数中的列值。</span><span class="sxs-lookup"><span data-stu-id="18e1d-107">Column values in table-valued parameters can be accessed using standard Transact-SQL SELECT statements.</span></span> <span data-ttu-id="18e1d-108">表值参数为强类型，其结构会自动进行验证。</span><span class="sxs-lookup"><span data-stu-id="18e1d-108">Table-valued parameters are strongly typed and their structure is automatically validated.</span></span> <span data-ttu-id="18e1d-109">表值参数的大小仅受服务器内存的限制。</span><span class="sxs-lookup"><span data-stu-id="18e1d-109">The size of table-valued parameters is limited only by server memory.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="18e1d-110">无法返回表值参数中的数据。</span><span class="sxs-lookup"><span data-stu-id="18e1d-110">You cannot return data in a table-valued parameter.</span></span> <span data-ttu-id="18e1d-111">表值参数仅限输入；不支持 OUTPUT 关键字。</span><span class="sxs-lookup"><span data-stu-id="18e1d-111">Table-valued parameters are input-only; the OUTPUT keyword is not supported.</span></span>  
  
 <span data-ttu-id="18e1d-112">若要详细了解表值参数，请参阅以下资源。</span><span class="sxs-lookup"><span data-stu-id="18e1d-112">For more information about table-valued parameters, see the following resources.</span></span>  
  
|<span data-ttu-id="18e1d-113">资源</span><span class="sxs-lookup"><span data-stu-id="18e1d-113">Resource</span></span>|<span data-ttu-id="18e1d-114">说明</span><span class="sxs-lookup"><span data-stu-id="18e1d-114">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="18e1d-115">使用表值参数（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="18e1d-115">Use Table-Valued Parameters (Database Engine)</span></span>](/sql/relational-databases/tables/use-table-valued-parameters-database-engine)|<span data-ttu-id="18e1d-116">介绍如何创建和使用表值参数。</span><span class="sxs-lookup"><span data-stu-id="18e1d-116">Describes how to create and use table-valued parameters.</span></span>|  
|<span data-ttu-id="18e1d-117">[User-Defined Table Types](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="18e1d-117">[User-Defined Table Types](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))</span></span>|<span data-ttu-id="18e1d-118">说明用于声明表值参数的用户定义的表类型。</span><span class="sxs-lookup"><span data-stu-id="18e1d-118">Describes user-defined table types that are used to declare table-valued parameters.</span></span>|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a><span data-ttu-id="18e1d-119">在 SQL Server 的早期版本中传递多行</span><span class="sxs-lookup"><span data-stu-id="18e1d-119">Passing Multiple Rows in Previous Versions of SQL Server</span></span>  
 <span data-ttu-id="18e1d-120">在 SQL Server 2008 中引入表值参数之前，用于将多行数据传递到存储过程或参数化 SQL 命令的选项受到限制。</span><span class="sxs-lookup"><span data-stu-id="18e1d-120">Before table-valued parameters were introduced to SQL Server 2008, the options for passing multiple rows of data to a stored procedure or a parameterized SQL command were limited.</span></span> <span data-ttu-id="18e1d-121">开发人员可以选择下面的一种方法，将多行传递到服务器：</span><span class="sxs-lookup"><span data-stu-id="18e1d-121">A developer could choose from the following options for passing multiple rows to the server:</span></span>  
  
- <span data-ttu-id="18e1d-122">使用一系列单独的参数来表示多列和多行数据中的值。</span><span class="sxs-lookup"><span data-stu-id="18e1d-122">Use a series of individual parameters to represent the values in multiple columns and rows of data.</span></span> <span data-ttu-id="18e1d-123">使用这种方法可以传递的数据量受到允许使用的参数数量限制。</span><span class="sxs-lookup"><span data-stu-id="18e1d-123">The amount of data that can be passed by using this method is limited by the number of parameters allowed.</span></span> <span data-ttu-id="18e1d-124">SQL Server 过程最多可以有 2100 个参数。</span><span class="sxs-lookup"><span data-stu-id="18e1d-124">SQL Server procedures can have, at most, 2100 parameters.</span></span> <span data-ttu-id="18e1d-125">必须使用服务器端逻辑，将这些单独的值汇编到表变量或临时表中以供处理。</span><span class="sxs-lookup"><span data-stu-id="18e1d-125">Server-side logic is required to assemble these individual values into a table variable or a temporary table for processing.</span></span>  
  
- <span data-ttu-id="18e1d-126">将多个数据值绑定到分隔字符串或 XML 文档，然后将这些文本值传递到过程或语句。</span><span class="sxs-lookup"><span data-stu-id="18e1d-126">Bundle multiple data values into delimited strings or XML documents and then pass those text values to a procedure or statement.</span></span> <span data-ttu-id="18e1d-127">这要求过程或语句包含验证数据结构和解除绑定值所需的逻辑。</span><span class="sxs-lookup"><span data-stu-id="18e1d-127">This requires the procedure or statement to include the logic necessary for validating the data structures and unbundling the values.</span></span>  
  
- <span data-ttu-id="18e1d-128">为影响多行的数据修改创建一系列单独的 SQL 语句，例如通过调用 `Update` 的 <xref:System.Data.SqlClient.SqlDataAdapter> 方法创建的语句。</span><span class="sxs-lookup"><span data-stu-id="18e1d-128">Create a series of individual SQL statements for data modifications that affect multiple rows, such as those created by calling the `Update` method of a <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="18e1d-129">更改可以单独提交给服务器，也可以批量提交给组。</span><span class="sxs-lookup"><span data-stu-id="18e1d-129">Changes can be submitted to the server individually or batched into groups.</span></span> <span data-ttu-id="18e1d-130">不过，即使是包含多个语句的批量提交，每个语句也是在服务器上单独执行。</span><span class="sxs-lookup"><span data-stu-id="18e1d-130">However, even when submitted in batches that contain multiple statements, each statement is executed separately on the server.</span></span>  
  
- <span data-ttu-id="18e1d-131">使用 `bcp` 实用工具或 <xref:System.Data.SqlClient.SqlBulkCopy> 对象将多行数据加载到表中。</span><span class="sxs-lookup"><span data-stu-id="18e1d-131">Use the `bcp` utility program or the <xref:System.Data.SqlClient.SqlBulkCopy> object to load many rows of data into a table.</span></span> <span data-ttu-id="18e1d-132">尽管这种技术非常高效，但它不支持服务器端处理，除非将数据加载到临时表或表变量中。</span><span class="sxs-lookup"><span data-stu-id="18e1d-132">Although this technique is very efficient, it does not support server-side processing unless the data is loaded into a temporary table or table variable.</span></span>  
  
## <a name="creating-table-valued-parameter-types"></a><span data-ttu-id="18e1d-133">创建表值参数类型</span><span class="sxs-lookup"><span data-stu-id="18e1d-133">Creating Table-Valued Parameter Types</span></span>  
 <span data-ttu-id="18e1d-134">表值参数基于使用 Transact-sql CREATE TYPE 语句定义的强类型表结构。</span><span class="sxs-lookup"><span data-stu-id="18e1d-134">Table-valued parameters are based on strongly typed table structures that are defined by using Transact-SQL CREATE TYPE statements.</span></span> <span data-ttu-id="18e1d-135">必须先在 SQL Server 中创建一个表类型并定义结构，才能在客户端应用程序中使用表值参数。</span><span class="sxs-lookup"><span data-stu-id="18e1d-135">You have to create a table type and define the structure in SQL Server before you can use table-valued parameters in your client applications.</span></span> <span data-ttu-id="18e1d-136">有关创建表类型的详细信息，请参阅[用户定义的表类型](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))。</span><span class="sxs-lookup"><span data-stu-id="18e1d-136">For more information about creating table types, see [User-Defined Table Types](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100)).</span></span>  
  
 <span data-ttu-id="18e1d-137">以下语句创建一个名为 CategoryTableType 的表类型，其中包含 CategoryID 列和 CategoryName 列：</span><span class="sxs-lookup"><span data-stu-id="18e1d-137">The following statement creates a table type named CategoryTableType that consists of CategoryID and CategoryName columns:</span></span>  
  
```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 <span data-ttu-id="18e1d-138">创建表类型后，可以基于该类型声明表值参数。</span><span class="sxs-lookup"><span data-stu-id="18e1d-138">After you create a table type, you can declare table-valued parameters based on that type.</span></span> <span data-ttu-id="18e1d-139">下面的 Transact-SQL 片段演示如何在存储过程定义中声明表值参数。</span><span class="sxs-lookup"><span data-stu-id="18e1d-139">The following Transact-SQL fragment demonstrates how to declare a table-valued parameter in a stored procedure definition.</span></span> <span data-ttu-id="18e1d-140">请注意，声明表值参数需要 READONLY 关键字。</span><span class="sxs-lookup"><span data-stu-id="18e1d-140">Note that the READONLY keyword is required for declaring a table-valued parameter.</span></span>  
  
```sql
CREATE PROCEDURE usp_UpdateCategories
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a><span data-ttu-id="18e1d-141">通过表值参数修改数据 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="18e1d-141">Modifying Data with Table-Valued Parameters (Transact-SQL)</span></span>  
 <span data-ttu-id="18e1d-142">表值参数可用于基于集的数据修改，这些修改通过执行一条语句影响多行。</span><span class="sxs-lookup"><span data-stu-id="18e1d-142">Table-valued parameters can be used in set-based data modifications that affect multiple rows by executing a single statement.</span></span> <span data-ttu-id="18e1d-143">例如，可以选择表值参数中的所有行并将它们插入数据库表，也可以通过将表值参数联接到要更新的表来创建更新语句。</span><span class="sxs-lookup"><span data-stu-id="18e1d-143">For example, you can select all the rows in a table-valued parameter and insert them into a database table, or you can create an update statement by joining a table-valued parameter to the table you want to update.</span></span>  
  
 <span data-ttu-id="18e1d-144">下面的 Transact-SQL UPDATE 语句演示如何通过将表值参数联接到 Categories 表来使用它。</span><span class="sxs-lookup"><span data-stu-id="18e1d-144">The following Transact-SQL UPDATE statement demonstrates how to use a table-valued parameter by joining it to the Categories table.</span></span> <span data-ttu-id="18e1d-145">在 FROM 子句中结合使用表值参数和 JOIN 时，还必须对表值参数使用别名。如下所示，表值参数的别名为“ec”：</span><span class="sxs-lookup"><span data-stu-id="18e1d-145">When you use a table-valued parameter with a JOIN in a FROM clause, you must also alias it, as shown here, where the table-valued parameter is aliased as "ec":</span></span>  
  
```sql
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 <span data-ttu-id="18e1d-146">此 Transact-SQL 示例演示如何从表值参数中选择行以在单个基于集的操作中执行 INSERT。</span><span class="sxs-lookup"><span data-stu-id="18e1d-146">This Transact-SQL example demonstrates how to select rows from a table-valued parameter to perform an INSERT in a single set-based operation.</span></span>  
  
```sql
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a><span data-ttu-id="18e1d-147">表值参数的限制</span><span class="sxs-lookup"><span data-stu-id="18e1d-147">Limitations of Table-Valued Parameters</span></span>  
 <span data-ttu-id="18e1d-148">表值参数有几个限制：</span><span class="sxs-lookup"><span data-stu-id="18e1d-148">There are several limitations to table-valued parameters:</span></span>  
  
- <span data-ttu-id="18e1d-149">无法将表值参数传递给 [CLR 用户定义的函数](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions)。</span><span class="sxs-lookup"><span data-stu-id="18e1d-149">You cannot pass table-valued parameters to [CLR user-defined functions](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions).</span></span>  
  
- <span data-ttu-id="18e1d-150">表值参数只能通过被编制索引来支持 UNIQUE 或 PRIMARY KEY 约束。</span><span class="sxs-lookup"><span data-stu-id="18e1d-150">Table-valued parameters can only be indexed to support UNIQUE or PRIMARY KEY constraints.</span></span> <span data-ttu-id="18e1d-151">SQL Server 不维护表值参数的统计信息。</span><span class="sxs-lookup"><span data-stu-id="18e1d-151">SQL Server does not maintain statistics on table-valued parameters.</span></span>  
  
- <span data-ttu-id="18e1d-152">在 Transact-SQL 代码中表值参数是只读的。</span><span class="sxs-lookup"><span data-stu-id="18e1d-152">Table-valued parameters are read-only in Transact-SQL code.</span></span> <span data-ttu-id="18e1d-153">既不能更新表值参数行中的列值，也不能插入或删除行。</span><span class="sxs-lookup"><span data-stu-id="18e1d-153">You cannot update the column values in the rows of a table-valued parameter and you cannot insert or delete rows.</span></span> <span data-ttu-id="18e1d-154">若要修改表值参数中传递到存储过程或参数化语句的数据，必须将数据插入临时表或表变量。</span><span class="sxs-lookup"><span data-stu-id="18e1d-154">To modify the data that is passed to a stored procedure or parameterized statement in table-valued parameter, you must insert the data into a temporary table or into a table variable.</span></span>  
  
- <span data-ttu-id="18e1d-155">不能使用 ALTER TABLE 语句来修改表值参数的设计。</span><span class="sxs-lookup"><span data-stu-id="18e1d-155">You cannot use ALTER TABLE statements to modify the design of table-valued parameters.</span></span>  
  
## <a name="configuring-a-sqlparameter-example"></a><span data-ttu-id="18e1d-156">配置 SqlParameter 示例</span><span class="sxs-lookup"><span data-stu-id="18e1d-156">Configuring a SqlParameter Example</span></span>  
 <span data-ttu-id="18e1d-157"><xref:System.Data.SqlClient> 支持从 <xref:System.Data.DataTable><xref:System.Data.Common.DbDataReader> 或 <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.SqlServer.Server.SqlDataRecord> 对象填充表值参数。</span><span class="sxs-lookup"><span data-stu-id="18e1d-157"><xref:System.Data.SqlClient> supports populating table-valued parameters from <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> or <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.SqlServer.Server.SqlDataRecord> objects.</span></span> <span data-ttu-id="18e1d-158">必须使用 <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> 的 <xref:System.Data.SqlClient.SqlParameter> 属性指定表值参数的类型名称。</span><span class="sxs-lookup"><span data-stu-id="18e1d-158">You must specify a type name for the table-valued parameter by using the <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="18e1d-159">`TypeName` 必须与先前在服务器上创建的兼容类型的名称相匹配。</span><span class="sxs-lookup"><span data-stu-id="18e1d-159">The `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="18e1d-160">下面的代码段演示如何配置 <xref:System.Data.SqlClient.SqlParameter> 以插入数据。</span><span class="sxs-lookup"><span data-stu-id="18e1d-160">The following code fragment demonstrates how to configure <xref:System.Data.SqlClient.SqlParameter> to insert data.</span></span>  

<span data-ttu-id="18e1d-161">在以下示例中，`addedCategories` 变量包含一个 <xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="18e1d-161">In the following example, the `addedCategories` variable contains a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="18e1d-162">若要查看如何填充变量，请参阅下一节中的示例，[将表值参数传递给存储过程](#passing)。</span><span class="sxs-lookup"><span data-stu-id="18e1d-162">To see how the variable is populated, see the examples in the next section, [Passing a Table-Valued Parameter to a Stored Procedure](#passing).</span></span>

```csharp  
// Configure the command and parameter.  
SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
tvpParam.SqlDbType = SqlDbType.Structured;  
tvpParam.TypeName = "dbo.CategoryTableType";  
```  
  
```vb  
' Configure the command and parameter.  
Dim insertCommand As New SqlCommand(sqlInsert, connection)  
Dim tvpParam As SqlParameter = _  
   insertCommand.Parameters.AddWithValue( _  
  "@tvpNewCategories", addedCategories)  
tvpParam.SqlDbType = SqlDbType.Structured  
tvpParam.TypeName = "dbo.CategoryTableType"  
```  
  
 <span data-ttu-id="18e1d-163">你也可以使用从 <xref:System.Data.Common.DbDataReader> 中派生的任何对象，将数据行流处理到表值参数，如本代码段所示：</span><span class="sxs-lookup"><span data-stu-id="18e1d-163">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter, as shown in this fragment:</span></span>  
  
```csharp  
// Configure the SqlCommand and table-valued parameter.  
SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
insertCommand.CommandType = CommandType.StoredProcedure;  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", dataReader);  
tvpParam.SqlDbType = SqlDbType.Structured;  
```  
  
```vb  
' Configure the SqlCommand and table-valued parameter.  
Dim insertCommand As New SqlCommand("usp_InsertCategories", connection)  
insertCommand.CommandType = CommandType.StoredProcedure  
Dim tvpParam As SqlParameter = _  
  insertCommand.Parameters.AddWithValue("@tvpNewCategories", _  
  dataReader)  
tvpParam.SqlDbType = SqlDbType.Structured  
```  
  
## <a name="passing-a-table-valued-parameter-to-a-stored-procedure"></a><a name="passing"></a><span data-ttu-id="18e1d-164">将表值参数传递给存储过程</span><span class="sxs-lookup"><span data-stu-id="18e1d-164">Passing a Table-Valued Parameter to a Stored Procedure</span></span>  
 <span data-ttu-id="18e1d-165">此示例演示如何将表值参数数据传递到存储过程。</span><span class="sxs-lookup"><span data-stu-id="18e1d-165">This example demonstrates how to pass table-valued parameter data to a stored procedure.</span></span> <span data-ttu-id="18e1d-166">代码使用 <xref:System.Data.DataTable> 方法将添加的行提取到新的 <xref:System.Data.DataTable.GetChanges%2A> 中。</span><span class="sxs-lookup"><span data-stu-id="18e1d-166">The code extracts added rows into a new <xref:System.Data.DataTable> by using the <xref:System.Data.DataTable.GetChanges%2A> method.</span></span> <span data-ttu-id="18e1d-167">然后，该代码定义一个 <xref:System.Data.SqlClient.SqlCommand>，并将 <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> 属性设置为 <xref:System.Data.CommandType.StoredProcedure>。</span><span class="sxs-lookup"><span data-stu-id="18e1d-167">The code then defines a <xref:System.Data.SqlClient.SqlCommand>, setting the <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> property to <xref:System.Data.CommandType.StoredProcedure>.</span></span> <span data-ttu-id="18e1d-168">使用 <xref:System.Data.SqlClient.SqlParameter> 方法填充 <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A>，并将 <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> 设置为 `Structured`。</span><span class="sxs-lookup"><span data-stu-id="18e1d-168">The <xref:System.Data.SqlClient.SqlParameter> is populated by using the <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> method and the <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> is set to `Structured`.</span></span> <span data-ttu-id="18e1d-169">然后，使用 <xref:System.Data.SqlClient.SqlCommand> 方法执行 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>。</span><span class="sxs-lookup"><span data-stu-id="18e1d-169">The <xref:System.Data.SqlClient.SqlCommand> is then executed by using the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method.</span></span>  
  
```csharp  
// Assumes connection is an open SqlConnection object.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Configure the SqlCommand and SqlParameter.  
  SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
  insertCommand.CommandType = CommandType.StoredProcedure;  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
```vb  
' Assumes connection is an open SqlConnection object.  
Using connection  
   '  Create a DataTable with the modified rows.  
   Dim addedCategories As DataTable = _  
     CategoriesDataTable.GetChanges(DataRowState.Added)  
  
  ' Configure the SqlCommand and SqlParameter.  
   Dim insertCommand As New SqlCommand( _  
     "usp_InsertCategories", connection)  
   insertCommand.CommandType = CommandType.StoredProcedure  
   Dim tvpParam As SqlParameter = _  
     insertCommand.Parameters.AddWithValue( _  
     "@tvpNewCategories", addedCategories)  
   tvpParam.SqlDbType = SqlDbType.Structured  
  
   '  Execute the command.  
   insertCommand.ExecuteNonQuery()  
End Using  
```  
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a><span data-ttu-id="18e1d-170">将表值参数传递给参数化 SQL 语句</span><span class="sxs-lookup"><span data-stu-id="18e1d-170">Passing a Table-Valued Parameter to a Parameterized SQL Statement</span></span>  
 <span data-ttu-id="18e1d-171">下面的示例演示如何使用包含将表值参数作为数据源的 SELECT 子查询的 INSERT 语句向 dbo.Categories 表插入数据。</span><span class="sxs-lookup"><span data-stu-id="18e1d-171">The following example demonstrates how to insert data into the dbo.Categories table by using an INSERT statement with a SELECT subquery that has a table-valued parameter as the data source.</span></span> <span data-ttu-id="18e1d-172">将表值参数传递给参数化 SQL 语句时，必须使用 <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> 的新 <xref:System.Data.SqlClient.SqlParameter> 属性指定表值参数的类型名称。</span><span class="sxs-lookup"><span data-stu-id="18e1d-172">When passing a table-valued parameter to a parameterized SQL statement, you must specify a type name for the table-valued parameter by using the new <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="18e1d-173">此 `TypeName` 必须与先前在服务器上创建的兼容类型的名称相匹配。</span><span class="sxs-lookup"><span data-stu-id="18e1d-173">This `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="18e1d-174">本示例中的代码使用 `TypeName` 属性来引用在 dbo.CategoryTableType 中定义的类型结构。</span><span class="sxs-lookup"><span data-stu-id="18e1d-174">The code in this example uses the `TypeName` property to reference the type structure defined in dbo.CategoryTableType.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="18e1d-175">如果为表值参数中的标识列提供值，则必须为会话发出 SET IDENTITY_INSERT 语句。</span><span class="sxs-lookup"><span data-stu-id="18e1d-175">If you supply a value for an identity column in a table-valued parameter, you must issue the SET IDENTITY_INSERT statement for the session.</span></span>  
  
```csharp  
// Assumes connection is an open SqlConnection.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Define the INSERT-SELECT statement.  
  string sqlInsert =
      "INSERT INTO dbo.Categories (CategoryID, CategoryName)"  
      + " SELECT nc.CategoryID, nc.CategoryName"  
      + " FROM @tvpNewCategories AS nc;"  

  // Configure the command and parameter.  
  SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  
  tvpParam.TypeName = "dbo.CategoryTableType";  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
```vb  
' Assumes connection is an open SqlConnection.  
Using connection  
  ' Create a DataTable with the modified rows.  
  Dim addedCategories As DataTable = _  
    CategoriesDataTable.GetChanges(DataRowState.Added)  
  
  ' Define the INSERT-SELECT statement.  
  Dim sqlInsert As String = _  
  "INSERT INTO dbo.Categories (CategoryID, CategoryName)" _  
  & " SELECT nc.CategoryID, nc.CategoryName" _  
  & " FROM @tvpNewCategories AS nc;"  
  
  ' Configure the command and parameter.  
  Dim insertCommand As New SqlCommand(sqlInsert, connection)  
  Dim tvpParam As SqlParameter = _  
     insertCommand.Parameters.AddWithValue( _  
    "@tvpNewCategories", addedCategories)  
  tvpParam.SqlDbType = SqlDbType.Structured  
  tvpParam.TypeName = "dbo.CategoryTableType"  
  
  ' Execute the query  
  insertCommand.ExecuteNonQuery()  
End Using  
```  
  
## <a name="streaming-rows-with-a-datareader"></a><span data-ttu-id="18e1d-176">使用 DataReader 对行进行流处理</span><span class="sxs-lookup"><span data-stu-id="18e1d-176">Streaming Rows with a DataReader</span></span>  
 <span data-ttu-id="18e1d-177">你也可以使用从 <xref:System.Data.Common.DbDataReader> 中派生的任何对象，将数据行流处理到表值参数。</span><span class="sxs-lookup"><span data-stu-id="18e1d-177">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter.</span></span> <span data-ttu-id="18e1d-178">下面的代码段演示如何使用 <xref:System.Data.OracleClient.OracleCommand> 和 <xref:System.Data.OracleClient.OracleDataReader> 从 Oracle 数据库中检索数据。</span><span class="sxs-lookup"><span data-stu-id="18e1d-178">The following code fragment demonstrates retrieving data from an Oracle database by using an <xref:System.Data.OracleClient.OracleCommand> and an <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="18e1d-179">然后，该代码将 <xref:System.Data.SqlClient.SqlCommand> 配置为使用单个输入参数调用存储过程。</span><span class="sxs-lookup"><span data-stu-id="18e1d-179">The code then configures a <xref:System.Data.SqlClient.SqlCommand> to invoke a stored procedure with a single input parameter.</span></span> <span data-ttu-id="18e1d-180"><xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> 的 <xref:System.Data.SqlClient.SqlParameter> 属性设置为 `Structured`。</span><span class="sxs-lookup"><span data-stu-id="18e1d-180">The <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> property of the <xref:System.Data.SqlClient.SqlParameter> is set to `Structured`.</span></span> <span data-ttu-id="18e1d-181"><xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> 将 `OracleDataReader` 结果集作为表值参数传递给存储过程。</span><span class="sxs-lookup"><span data-stu-id="18e1d-181">The <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> passes the `OracleDataReader` result set to the stored procedure as a table-valued parameter.</span></span>  
  
```csharp  
// Assumes connection is an open SqlConnection.  
// Retrieve data from Oracle.  
OracleCommand selectCommand = new OracleCommand(  
   "Select CategoryID, CategoryName FROM Categories;",  
   oracleConnection);  
OracleDataReader oracleReader = selectCommand.ExecuteReader(  
   CommandBehavior.CloseConnection);  
  
 // Configure the SqlCommand and table-valued parameter.  
 SqlCommand insertCommand = new SqlCommand(  
   "usp_InsertCategories", connection);  
 insertCommand.CommandType = CommandType.StoredProcedure;  
 SqlParameter tvpParam =  
    insertCommand.Parameters.AddWithValue(  
    "@tvpNewCategories", oracleReader);  
 tvpParam.SqlDbType = SqlDbType.Structured;  
  
 // Execute the command.  
 insertCommand.ExecuteNonQuery();  
```  
  
```vb  
' Assumes connection is an open SqlConnection.  
' Retrieve data from Oracle.  
Dim selectCommand As New OracleCommand( _  
  "Select CategoryID, CategoryName FROM Categories;", _  
  oracleConnection)  
Dim oracleReader As OracleDataReader = _  
  selectCommand.ExecuteReader(CommandBehavior.CloseConnection)  
  
' Configure SqlCommand and table-valued parameter.  
Dim insertCommand As New SqlCommand("usp_InsertCategories", connection)  
insertCommand.CommandType = CommandType.StoredProcedure  
Dim tvpParam As SqlParameter = _  
  insertCommand.Parameters.AddWithValue("@tvpNewCategories", _  
  oracleReader)  
tvpParam.SqlDbType = SqlDbType.Structured  
  
' Execute the command.  
insertCommand.ExecuteNonQuery()  
```  
  
## <a name="see-also"></a><span data-ttu-id="18e1d-182">另请参阅</span><span class="sxs-lookup"><span data-stu-id="18e1d-182">See also</span></span>

- [<span data-ttu-id="18e1d-183">配置参数和参数数据类型</span><span class="sxs-lookup"><span data-stu-id="18e1d-183">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="18e1d-184">命令和参数</span><span class="sxs-lookup"><span data-stu-id="18e1d-184">Commands and Parameters</span></span>](../commands-and-parameters.md)
- [<span data-ttu-id="18e1d-185">DataAdapter 参数</span><span class="sxs-lookup"><span data-stu-id="18e1d-185">DataAdapter Parameters</span></span>](../dataadapter-parameters.md)
- [<span data-ttu-id="18e1d-186">ADO.NET 中的 SQL Server 数据操作</span><span class="sxs-lookup"><span data-stu-id="18e1d-186">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="18e1d-187">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="18e1d-187">ADO.NET Overview</span></span>](../ado-net-overview.md)

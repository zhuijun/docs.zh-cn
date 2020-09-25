---
title: 修改大值 (max) 数据
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: 4748740379df689669ee87f66dce58a7015d1217
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172692"
---
# <a name="modifying-large-value-max-data-in-adonet"></a><span data-ttu-id="b316b-102">在 ADO.NET 中修改大值 (max) 数据</span><span class="sxs-lookup"><span data-stu-id="b316b-102">Modifying Large-Value (max) Data in ADO.NET</span></span>

<span data-ttu-id="b316b-103">大型对象 (LOB) 数据类型是指那些超过 8 KB 最大行大小的数据类型。</span><span class="sxs-lookup"><span data-stu-id="b316b-103">Large object (LOB) data types are those that exceed the maximum row size of 8 kilobytes (KB).</span></span> <span data-ttu-id="b316b-104">SQL Server 为 `varchar`、`nvarchar` 和 `varbinary` 数据类型引入了 `max` 说明符，以允许存储最长可达 2^32 个字节的值。</span><span class="sxs-lookup"><span data-stu-id="b316b-104">SQL Server provides a `max` specifier for `varchar`, `nvarchar`, and `varbinary` data types to allow storage of values as large as 2^32 bytes.</span></span> <span data-ttu-id="b316b-105">表列和 Transact-SQL 变量可以指定 `varchar(max)`、`nvarchar(max)` 或 `varbinary(max)` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="b316b-105">Table columns and Transact-SQL variables may specify `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` data types.</span></span> <span data-ttu-id="b316b-106">在 ADO.NET 中，`max` 数据类型可通过 `DataReader` 来提取，并可指定为输入和输出参数值而无需任何特殊处理。</span><span class="sxs-lookup"><span data-stu-id="b316b-106">In ADO.NET, the `max` data types can be fetched by a `DataReader`, and can also be specified as both input and output parameter values without any special handling.</span></span> <span data-ttu-id="b316b-107">对于大型 `varchar` 数据类型，可以增量地检索和更新数据。</span><span class="sxs-lookup"><span data-stu-id="b316b-107">For large `varchar` data types, data can be retrieved and updated incrementally.</span></span>  
  
 <span data-ttu-id="b316b-108">`max` 数据类型可用于进行比较（作为 Transact-SQL 变量）和串联。</span><span class="sxs-lookup"><span data-stu-id="b316b-108">The `max` data types can be used for comparisons, as Transact-SQL variables, and for concatenation.</span></span> <span data-ttu-id="b316b-109">它们还可以用于 SELECT 语句的 DISTINCT、ORDER BY、GROUP BY 子句，以及聚合、连接和子查询。</span><span class="sxs-lookup"><span data-stu-id="b316b-109">They can also be used in the DISTINCT, ORDER BY, GROUP BY clauses of a SELECT statement as well as in aggregates, joins, and subqueries.</span></span>  
  
 <span data-ttu-id="b316b-110">下表提供指向 SQL Server 联机丛书中的文档的链接。</span><span class="sxs-lookup"><span data-stu-id="b316b-110">The following table provides links to the documentation in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="b316b-111">**SQL Server 文档**</span><span class="sxs-lookup"><span data-stu-id="b316b-111">**SQL Server documentation**</span></span>  
  
1. <span data-ttu-id="b316b-112">[使用大值数据类型](/previous-versions/sql/sql-server-2008/ms178158(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="b316b-112">[Using Large-Value Data Types](/previous-versions/sql/sql-server-2008/ms178158(v=sql.100))</span></span>  
  
## <a name="large-value-type-restrictions"></a><span data-ttu-id="b316b-113">大值类型限制</span><span class="sxs-lookup"><span data-stu-id="b316b-113">Large-Value Type Restrictions</span></span>  

 <span data-ttu-id="b316b-114">以下限制适用于对于较小数据类型不存在的 `max` 数据类型：</span><span class="sxs-lookup"><span data-stu-id="b316b-114">The following restrictions apply to the `max` data types, which do not exist for smaller data types:</span></span>  
  
- <span data-ttu-id="b316b-115">`sql_variant` 不能包含大型 `varchar` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="b316b-115">A `sql_variant` cannot contain a large `varchar` data type.</span></span>  
  
- <span data-ttu-id="b316b-116">不能将大型 `varchar` 列指定为索引中的键列。</span><span class="sxs-lookup"><span data-stu-id="b316b-116">Large `varchar` columns cannot be specified as a key column in an index.</span></span> <span data-ttu-id="b316b-117">允许在非聚集索引的包含列中使用它们。</span><span class="sxs-lookup"><span data-stu-id="b316b-117">They are allowed in an included column in a non-clustered index.</span></span>  
  
- <span data-ttu-id="b316b-118">大型 `varchar` 列不能用作分区键列。</span><span class="sxs-lookup"><span data-stu-id="b316b-118">Large `varchar` columns cannot be used as partitioning key columns.</span></span>  
  
## <a name="working-with-large-value-types-in-transact-sql"></a><span data-ttu-id="b316b-119">在 Transact-SQL 中使用大值类型</span><span class="sxs-lookup"><span data-stu-id="b316b-119">Working with Large-Value Types in Transact-SQL</span></span>  

 <span data-ttu-id="b316b-120">Transact-SQL `OPENROWSET` 函数是连接和访问远程数据的一次性方法。</span><span class="sxs-lookup"><span data-stu-id="b316b-120">The Transact-SQL `OPENROWSET` function is a one-time method of connecting and accessing remote data.</span></span> <span data-ttu-id="b316b-121">它包含从 OLE DB 数据源访问远程数据所需的所有连接信息。</span><span class="sxs-lookup"><span data-stu-id="b316b-121">It includes all of the connection information necessary to access remote data from an OLE DB data source.</span></span> <span data-ttu-id="b316b-122">可在查询的 FROM 子句中像引用表名那样引用 `OPENROWSET`。</span><span class="sxs-lookup"><span data-stu-id="b316b-122">`OPENROWSET` can be referenced in the FROM clause of a query as though it were a table name.</span></span> <span data-ttu-id="b316b-123">根据 OLE DB 提供程序的功能，它还可作为 INSERT、UPDATE 或 DELETE 语句的目标表被引用。</span><span class="sxs-lookup"><span data-stu-id="b316b-123">It can also be referenced as the target table of an INSERT, UPDATE, or DELETE statement, subject to the capabilities of the OLE DB provider.</span></span>  
  
 <span data-ttu-id="b316b-124">`OPENROWSET` 函数包含 `BULK` 行集提供程序，它允许你直接从文件读取数据而不必将数据加载到目标表。</span><span class="sxs-lookup"><span data-stu-id="b316b-124">The `OPENROWSET` function includes the `BULK` rowset provider, which allows you to read data directly from a file without loading the data into a target table.</span></span> <span data-ttu-id="b316b-125">这样你可以在简单的 INSERT SELECT 语句中使用 `OPENROWSET`。</span><span class="sxs-lookup"><span data-stu-id="b316b-125">This enables you to use `OPENROWSET` in a simple INSERT SELECT statement.</span></span>  
  
 <span data-ttu-id="b316b-126">`OPENROWSET BULK` 选项参数可以有效地控制在何处开始和结束读取数据、如何处理错误以及如何解释数据。</span><span class="sxs-lookup"><span data-stu-id="b316b-126">The `OPENROWSET BULK` option arguments provide significant control over where to begin and end reading data, how to deal with errors, and how data is interpreted.</span></span> <span data-ttu-id="b316b-127">例如，可以指定以类型为 `varbinary`、`varchar` 或 `nvarchar` 的单行单列行集的形式读取数据文件。</span><span class="sxs-lookup"><span data-stu-id="b316b-127">For example, you can specify that the data file be read as a single-row, single-column rowset of type `varbinary`, `varchar`, or `nvarchar`.</span></span> <span data-ttu-id="b316b-128">有关完整的语法和选项，请参阅 SQL Server 联机丛书。</span><span class="sxs-lookup"><span data-stu-id="b316b-128">For the complete syntax and options, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="b316b-129">以下示例向 AdventureWorks 示例数据库的 ProductPhoto 表中插入照片。</span><span class="sxs-lookup"><span data-stu-id="b316b-129">The following example inserts a photo into the ProductPhoto table in the AdventureWorks sample database.</span></span> <span data-ttu-id="b316b-130">在使用 `BULK OPENROWSET` 提供程序时，即使不将值插入每个列中，也必须提供列的命名列表。</span><span class="sxs-lookup"><span data-stu-id="b316b-130">When using the `BULK OPENROWSET` provider, you must supply the named list of columns even if you aren't inserting values into every column.</span></span> <span data-ttu-id="b316b-131">在此示例中，主键定义为标识列，可以从列列表中省略。</span><span class="sxs-lookup"><span data-stu-id="b316b-131">The primary key in this case is defined as an identity column, and may be omitted from the column list.</span></span> <span data-ttu-id="b316b-132">请注意，还必须在 `OPENROWSET` 语句的末尾提供相关名称，在本例中为 ThumbnailPhoto。</span><span class="sxs-lookup"><span data-stu-id="b316b-132">Note that you must also supply a correlation name at the end of the `OPENROWSET` statement, which in this case is ThumbnailPhoto.</span></span> <span data-ttu-id="b316b-133">这与将文件加载到 `ProductPhoto` 表中的列相关联。</span><span class="sxs-lookup"><span data-stu-id="b316b-133">This correlates with the column in the `ProductPhoto` table into which the file is being loaded.</span></span>  
  
```sql  
INSERT Production.ProductPhoto (  
    ThumbnailPhoto,
    ThumbnailPhotoFilePath,
    LargePhoto,
    LargePhotoFilePath)  
SELECT ThumbnailPhoto.*, null, null, N'tricycle_pink.gif'  
FROM OPENROWSET
    (BULK 'c:\images\tricycle.jpg', SINGLE_BLOB) ThumbnailPhoto  
```  
  
## <a name="updating-data-using-update-write"></a><span data-ttu-id="b316b-134">使用 UPDATE .WRITE 更新数据</span><span class="sxs-lookup"><span data-stu-id="b316b-134">Updating Data Using UPDATE .WRITE</span></span>  

 <span data-ttu-id="b316b-135">Transact-SQL UPDATE 语句具有新的 WRITE 语法，用于修改 `varchar(max)`、`nvarchar(max)` 或 `varbinary(max)` 列的内容。</span><span class="sxs-lookup"><span data-stu-id="b316b-135">The Transact-SQL UPDATE statement has new WRITE syntax for modifying the contents of `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` columns.</span></span> <span data-ttu-id="b316b-136">这允许你对数据进行部分更新。</span><span class="sxs-lookup"><span data-stu-id="b316b-136">This allows you to perform partial updates of the data.</span></span> <span data-ttu-id="b316b-137">UPDATE .WRITE 语法在此以缩写形式显示：</span><span class="sxs-lookup"><span data-stu-id="b316b-137">The UPDATE .WRITE syntax is shown here in abbreviated form:</span></span>  
  
 <span data-ttu-id="b316b-138">UPDATE</span><span class="sxs-lookup"><span data-stu-id="b316b-138">UPDATE</span></span>  
  
 <span data-ttu-id="b316b-139">{ *\<object>* }</span><span class="sxs-lookup"><span data-stu-id="b316b-139">{ *\<object>* }</span></span>  
  
 <span data-ttu-id="b316b-140">SET</span><span class="sxs-lookup"><span data-stu-id="b316b-140">SET</span></span>  
  
 <span data-ttu-id="b316b-141">{ *column_name* = {。写入 ( *表达式* ， @Offset @Length ) }</span><span class="sxs-lookup"><span data-stu-id="b316b-141">{ *column_name* = { .WRITE ( *expression* , @Offset , @Length ) }</span></span>  
  
 <span data-ttu-id="b316b-142">WRITE 方法指定将修改 column_name 值的某个部分\*\*。</span><span class="sxs-lookup"><span data-stu-id="b316b-142">The WRITE method specifies that a section of the value of the *column_name* will be modified.</span></span> <span data-ttu-id="b316b-143">表达式是将复制到 column_name 的值，`@Offset` 是将写入表达式的开始点，`@Length` 自变量是列中该部分的长度\*\*。</span><span class="sxs-lookup"><span data-stu-id="b316b-143">The expression is the value that will be copied to the *column_name*, the `@Offset` is the beginning point at which the expression will be written, and the `@Length` argument is the length of the section in the column.</span></span>  
  
|<span data-ttu-id="b316b-144">如果</span><span class="sxs-lookup"><span data-stu-id="b316b-144">If</span></span>|<span data-ttu-id="b316b-145">Then</span><span class="sxs-lookup"><span data-stu-id="b316b-145">Then</span></span>|  
|--------|----------|  
|<span data-ttu-id="b316b-146">表达式设置为 NULL</span><span class="sxs-lookup"><span data-stu-id="b316b-146">The expression is set to NULL</span></span>|<span data-ttu-id="b316b-147">忽略 `@Length`，并在指定的 `@Offset` 处截断 column_name 中的值\*\*。</span><span class="sxs-lookup"><span data-stu-id="b316b-147">`@Length` is ignored and the value in *column_name* is truncated at the specified `@Offset`.</span></span>|  
|<span data-ttu-id="b316b-148">`@Offset` 为 NULL</span><span class="sxs-lookup"><span data-stu-id="b316b-148">`@Offset` is NULL</span></span>|<span data-ttu-id="b316b-149">更新操作将表达式追加到现有 column_name 值的末尾并忽略 `@Length`\*\*。</span><span class="sxs-lookup"><span data-stu-id="b316b-149">The update operation appends the expression at the end of the existing *column_name* value and `@Length` is ignored.</span></span>|  
|<span data-ttu-id="b316b-150">`@Offset` 大于 column_name 值的长度</span><span class="sxs-lookup"><span data-stu-id="b316b-150">`@Offset` is greater than the length of the column_name value</span></span>|<span data-ttu-id="b316b-151">SQL Server 将返回错误。</span><span class="sxs-lookup"><span data-stu-id="b316b-151">SQL Server returns an error.</span></span>|  
|<span data-ttu-id="b316b-152">`@Length` 为 NULL</span><span class="sxs-lookup"><span data-stu-id="b316b-152">`@Length` is NULL</span></span>|<span data-ttu-id="b316b-153">更新操作将删除从 `@Offset` 到 `column_name` 值的结尾的所有数据。</span><span class="sxs-lookup"><span data-stu-id="b316b-153">The update operation removes all data from `@Offset` to the end of the `column_name` value.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="b316b-154">`@Offset` 和 `@Length` 都不能为负数。</span><span class="sxs-lookup"><span data-stu-id="b316b-154">Neither `@Offset` nor `@Length` can be a negative number.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b316b-155">示例</span><span class="sxs-lookup"><span data-stu-id="b316b-155">Example</span></span>  

 <span data-ttu-id="b316b-156">此 Transact-SQL 示例更新 DocumentSummary 中的一个部分值，这是 AdventureWorks 数据库中 Document 表的 `nvarchar(max)` 列。</span><span class="sxs-lookup"><span data-stu-id="b316b-156">This Transact-SQL example updates a partial value in DocumentSummary, an `nvarchar(max)` column in the Document table in the AdventureWorks database.</span></span> <span data-ttu-id="b316b-157">通过指定替换单词、现有数据中要替换的单词的开始位置（偏移量）以及要替换的字符数（长度），将单词“components”替换为单词“features”。</span><span class="sxs-lookup"><span data-stu-id="b316b-157">The word 'components' is replaced by the word 'features' by specifying the replacement word, the beginning location (offset) of the word to be replaced in the existing data, and the number of characters to be replaced (length).</span></span> <span data-ttu-id="b316b-158">该示例在 UPDATE 语句之前和之后都包含 SELECT 语句来比较结果。</span><span class="sxs-lookup"><span data-stu-id="b316b-158">The example includes SELECT statements before and after the UPDATE statement to compare results.</span></span>  
  
```sql
USE AdventureWorks;  
GO  
--View the existing value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety components of your bicycle.  
  
--Modify a single word in the DocumentSummary column  
UPDATE Production.Document  
SET DocumentSummary .WRITE (N'features',28,10)  
WHERE DocumentID = 3 ;  
GO
--View the modified value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety features of your bicycle.  
```  
  
## <a name="working-with-large-value-types-in-adonet"></a><span data-ttu-id="b316b-159">在 ADO.NET 中使用大值类型</span><span class="sxs-lookup"><span data-stu-id="b316b-159">Working with Large-Value Types in ADO.NET</span></span>  

 <span data-ttu-id="b316b-160">通过将大值类型指定为 <xref:System.Data.SqlClient.SqlDataReader> 中的 <xref:System.Data.SqlClient.SqlParameter> 对象以返回结果集，或者通过 <xref:System.Data.SqlClient.SqlDataAdapter> 来填充 `DataSet`/`DataTable`，即可在 ADO.NET 中使用大值类型。</span><span class="sxs-lookup"><span data-stu-id="b316b-160">You can work with large value types in ADO.NET by specifying large value types as <xref:System.Data.SqlClient.SqlParameter> objects in a <xref:System.Data.SqlClient.SqlDataReader> to return a result set, or by using a <xref:System.Data.SqlClient.SqlDataAdapter> to fill a `DataSet`/`DataTable`.</span></span> <span data-ttu-id="b316b-161">处理大值类型与其相关的较小值数据类型的方式没有区别。</span><span class="sxs-lookup"><span data-stu-id="b316b-161">There is no difference between the way you work with a large value type and its related, smaller value data type.</span></span>  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a><span data-ttu-id="b316b-162">使用 GetSqlBytes 检索数据</span><span class="sxs-lookup"><span data-stu-id="b316b-162">Using GetSqlBytes to Retrieve Data</span></span>  

 <span data-ttu-id="b316b-163"><xref:System.Data.SqlClient.SqlDataReader> 的 `GetSqlBytes` 方法可用于检索 `varbinary(max)` 列的内容。</span><span class="sxs-lookup"><span data-stu-id="b316b-163">The `GetSqlBytes` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="b316b-164">下面的代码段假定一个名为 `cmd` 的 <xref:System.Data.SqlClient.SqlCommand> 对象，该对象从表中选择 `varbinary(max)` 数据，并假定一个名为 `reader` 的 <xref:System.Data.SqlClient.SqlDataReader> 对象以 <xref:System.Data.SqlTypes.SqlBytes> 的形式检索数据。</span><span class="sxs-lookup"><span data-stu-id="b316b-164">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as <xref:System.Data.SqlTypes.SqlBytes>.</span></span>  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim bytes As SqlBytes = reader.GetSqlBytes(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBytes bytes = reader.GetSqlBytes(0);  
    }  
```  
  
### <a name="using-getsqlchars-to-retrieve-data"></a><span data-ttu-id="b316b-165">使用 GetSqlChars 检索数据</span><span class="sxs-lookup"><span data-stu-id="b316b-165">Using GetSqlChars to Retrieve Data</span></span>  

 <span data-ttu-id="b316b-166"><xref:System.Data.SqlClient.SqlDataReader> 的 `GetSqlChars` 方法可用于检索 `varchar(max)` 或 `nvarchar(max)` 列的内容。</span><span class="sxs-lookup"><span data-stu-id="b316b-166">The `GetSqlChars` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varchar(max)` or `nvarchar(max)` column.</span></span> <span data-ttu-id="b316b-167">下面的代码段假定一个名为 `cmd` 的 <xref:System.Data.SqlClient.SqlCommand> 对象，该对象从表中选择 `nvarchar(max)` 数据，并假定一个名为 `reader` 的 <xref:System.Data.SqlClient.SqlDataReader> 对象来检索数据。</span><span class="sxs-lookup"><span data-stu-id="b316b-167">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `nvarchar(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim buffer As SqlChars = reader.GetSqlChars(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
{  
    SqlChars buffer = reader.GetSqlChars(0);  
}  
```  
  
### <a name="using-getsqlbinary-to-retrieve-data"></a><span data-ttu-id="b316b-168">使用 GetSqlBinary 检索数据</span><span class="sxs-lookup"><span data-stu-id="b316b-168">Using GetSqlBinary to Retrieve Data</span></span>  

 <span data-ttu-id="b316b-169"><xref:System.Data.SqlClient.SqlDataReader> 的 `GetSqlBinary` 方法可用于检索 `varbinary(max)` 列的内容。</span><span class="sxs-lookup"><span data-stu-id="b316b-169">The `GetSqlBinary` method of a <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="b316b-170">下面的代码段假定一个名为 `cmd` 的 <xref:System.Data.SqlClient.SqlCommand> 对象，该对象从表中选择 `varbinary(max)` 数据，并假定一个名为 `reader` 的 <xref:System.Data.SqlClient.SqlDataReader> 对象以 <xref:System.Data.SqlTypes.SqlBinary> 流的形式检索数据。</span><span class="sxs-lookup"><span data-stu-id="b316b-170">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as a <xref:System.Data.SqlTypes.SqlBinary> stream.</span></span>  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim binaryStream As SqlBinary = reader.GetSqlBinary(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBinary binaryStream = reader.GetSqlBinary(0);  
    }  
```  
  
### <a name="using-getbytes-to-retrieve-data"></a><span data-ttu-id="b316b-171">使用 GetBytes 检索数据</span><span class="sxs-lookup"><span data-stu-id="b316b-171">Using GetBytes to Retrieve Data</span></span>  

 <span data-ttu-id="b316b-172"><xref:System.Data.SqlClient.SqlDataReader> 的 `GetBytes` 方法从指定的列偏移量将字节流从指定数组偏移量开始读入字节数组。</span><span class="sxs-lookup"><span data-stu-id="b316b-172">The `GetBytes` method of a <xref:System.Data.SqlClient.SqlDataReader> reads a stream of bytes from the specified column offset into a byte array starting at the specified array offset.</span></span> <span data-ttu-id="b316b-173">下面的代码段假定一个名为 `reader` 的 <xref:System.Data.SqlClient.SqlDataReader> 对象，该对象将字节检索到字节数组中。</span><span class="sxs-lookup"><span data-stu-id="b316b-173">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves bytes into a byte array.</span></span> <span data-ttu-id="b316b-174">请注意，与 `GetSqlBytes` 不同，`GetBytes` 需要数组缓冲区的大小。</span><span class="sxs-lookup"><span data-stu-id="b316b-174">Note that, unlike `GetSqlBytes`, `GetBytes` requires a size for the array buffer.</span></span>  
  
```vb  
While reader.Read()  
    Dim buffer(4000) As Byte  
    Dim byteCount As Integer = _  
    CInt(reader.GetBytes(1, 0, buffer, 0, 4000))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    byte[] buffer = new byte[4000];  
    long byteCount = reader.GetBytes(1, 0, buffer, 0, 4000);  
}  
```  
  
### <a name="using-getvalue-to-retrieve-data"></a><span data-ttu-id="b316b-175">使用 GetValue 检索数据</span><span class="sxs-lookup"><span data-stu-id="b316b-175">Using GetValue to Retrieve Data</span></span>  

 <span data-ttu-id="b316b-176"><xref:System.Data.SqlClient.SqlDataReader> 的 `GetValue` 方法将值从指定的列偏移量读入数组。</span><span class="sxs-lookup"><span data-stu-id="b316b-176">The `GetValue` method of a <xref:System.Data.SqlClient.SqlDataReader> reads the value from the specified column offset into an array.</span></span> <span data-ttu-id="b316b-177">下面的代码段假定一个名为 `reader` 的 <xref:System.Data.SqlClient.SqlDataReader> 对象，该对象从第一个列偏移量检索二进制数据，然后从第二列偏移量检索字符串数据。</span><span class="sxs-lookup"><span data-stu-id="b316b-177">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves binary data from the first column offset, and then string data from the second column offset.</span></span>  
  
```vb  
While reader.Read()  
    ' Read the data from varbinary(max) column  
    Dim binaryData() As Byte = CByte(reader.GetValue(0))  
  
    ' Read the data from varchar(max) or nvarchar(max) column  
    Dim stringData() As String = Cstr((reader.GetValue(1))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    // Read the data from varbinary(max) column  
    byte[] binaryData = (byte[])reader.GetValue(0);  
  
    // Read the data from varchar(max) or nvarchar(max) column  
    String stringData = (String)reader.GetValue(1);  
}  
```  
  
## <a name="converting-from-large-value-types-to-clr-types"></a><span data-ttu-id="b316b-178">从大值类型转换为 CLR 类型</span><span class="sxs-lookup"><span data-stu-id="b316b-178">Converting from Large Value Types to CLR Types</span></span>  

 <span data-ttu-id="b316b-179">可以使用任何字符串转换方法（如 `ToString`）来转换 `varchar(max)` 或 `nvarchar(max)` 列的内容。</span><span class="sxs-lookup"><span data-stu-id="b316b-179">You can convert the contents of a `varchar(max)` or `nvarchar(max)` column using any of the string conversion methods, such as `ToString`.</span></span> <span data-ttu-id="b316b-180">下面的代码段假定一个名为 `reader` 的 <xref:System.Data.SqlClient.SqlDataReader> 对象，该对象检索数据。</span><span class="sxs-lookup"><span data-stu-id="b316b-180">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
```vb  
While reader.Read()  
    Dim str as String = reader(0).ToString()  
    Console.WriteLine(str)  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
     string str = reader[0].ToString();  
     Console.WriteLine(str);  
}  
```  
  
### <a name="example"></a><span data-ttu-id="b316b-181">示例</span><span class="sxs-lookup"><span data-stu-id="b316b-181">Example</span></span>  

 <span data-ttu-id="b316b-182">下面的代码从 `AdventureWorks` 数据库的 `ProductPhoto` 表中检索名称和 `LargePhoto` 对象，并将其保存到文件中。</span><span class="sxs-lookup"><span data-stu-id="b316b-182">The following code retrieves the name and the `LargePhoto` object from the `ProductPhoto` table in the `AdventureWorks` database and saves it to a file.</span></span> <span data-ttu-id="b316b-183">需要使用对 <xref:System.Drawing> 命名空间的引用来编译该程序集。</span><span class="sxs-lookup"><span data-stu-id="b316b-183">The assembly needs to be compiled with a reference to the <xref:System.Drawing> namespace.</span></span>  <span data-ttu-id="b316b-184"><xref:System.Data.SqlClient.SqlDataReader> 的 <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> 方法返回公开 `Stream` 属性的 <xref:System.Data.SqlTypes.SqlBytes> 对象。</span><span class="sxs-lookup"><span data-stu-id="b316b-184">The <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> method of the <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.SqlTypes.SqlBytes> object that exposes a `Stream` property.</span></span> <span data-ttu-id="b316b-185">代码使用此对象创建新的 `Bitmap` 对象，然后以 Gif `ImageFormat` 格式保存该对象。</span><span class="sxs-lookup"><span data-stu-id="b316b-185">The code uses this to create a new `Bitmap` object, and then saves it in the Gif `ImageFormat`.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a><span data-ttu-id="b316b-186">使用大值类型参数</span><span class="sxs-lookup"><span data-stu-id="b316b-186">Using Large Value Type Parameters</span></span>  

 <span data-ttu-id="b316b-187">在 <xref:System.Data.SqlClient.SqlParameter> 对象中使用的大值类型的方式与在 <xref:System.Data.SqlClient.SqlParameter> 对象中使用较小值类型的方式相同。</span><span class="sxs-lookup"><span data-stu-id="b316b-187">Large value types can be used in <xref:System.Data.SqlClient.SqlParameter> objects the same way you use smaller value types in <xref:System.Data.SqlClient.SqlParameter> objects.</span></span> <span data-ttu-id="b316b-188">可以将大值类型作为 <xref:System.Data.SqlClient.SqlParameter> 值进行检索，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="b316b-188">You can retrieve large value types as <xref:System.Data.SqlClient.SqlParameter> values, as shown in the following example.</span></span> <span data-ttu-id="b316b-189">此代码假定 AdventureWorks 示例数据库中存在以下 GetDocumentSummary 存储过程。</span><span class="sxs-lookup"><span data-stu-id="b316b-189">The code assumes that the following GetDocumentSummary stored procedure exists in the AdventureWorks sample database.</span></span> <span data-ttu-id="b316b-190">该存储过程采用名为 @DocumentID 的输入参数，并在 @DocumentSummary 输出参数中返回 DocumentSummary 列的内容。</span><span class="sxs-lookup"><span data-stu-id="b316b-190">The stored procedure takes an input parameter named @DocumentID and returns the contents of the DocumentSummary column in the @DocumentSummary output parameter.</span></span>  
  
```sql
CREATE PROCEDURE GetDocumentSummary
(  
    @DocumentID int,  
    @DocumentSummary nvarchar(MAX) OUTPUT  
)  
AS  
SET NOCOUNT ON  
SELECT  @DocumentSummary=Convert(nvarchar(MAX), DocumentSummary)  
FROM    Production.Document  
WHERE   DocumentID=@DocumentID  
```  
  
### <a name="example"></a><span data-ttu-id="b316b-191">示例</span><span class="sxs-lookup"><span data-stu-id="b316b-191">Example</span></span>  

 <span data-ttu-id="b316b-192">ADO.NET 代码将创建 <xref:System.Data.SqlClient.SqlConnection> 和 <xref:System.Data.SqlClient.SqlCommand> 对象以执行 GetDocumentSummary 存储过程，并检索文档摘要，该摘要存储为大值类型。</span><span class="sxs-lookup"><span data-stu-id="b316b-192">The ADO.NET code creates <xref:System.Data.SqlClient.SqlConnection> and <xref:System.Data.SqlClient.SqlCommand> objects to execute the GetDocumentSummary stored procedure and retrieve the document summary, which is stored as a large value type.</span></span> <span data-ttu-id="b316b-193">代码为 @DocumentID 输入参数传递一个值，并在控制台窗口显示 @DocumentSummary 输出参数中传回的结果。</span><span class="sxs-lookup"><span data-stu-id="b316b-193">The code passes a value for the @DocumentID input parameter, and displays the results passed back in the @DocumentSummary output parameter in the Console window.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b316b-194">请参阅</span><span class="sxs-lookup"><span data-stu-id="b316b-194">See also</span></span>

- [<span data-ttu-id="b316b-195">SQL Server 二进制和大值数据</span><span class="sxs-lookup"><span data-stu-id="b316b-195">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="b316b-196">SQL Server 数据类型映射</span><span class="sxs-lookup"><span data-stu-id="b316b-196">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="b316b-197">ADO.NET 中的 SQL Server 数据操作</span><span class="sxs-lookup"><span data-stu-id="b316b-197">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="b316b-198">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="b316b-198">ADO.NET Overview</span></span>](../ado-net-overview.md)

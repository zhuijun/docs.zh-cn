---
title: DataAdapter 参数
description: 了解 DbDataAdapter 的属性，这些属性从数据源返回数据并管理对数据源所做的更改。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
ms.openlocfilehash: 74b6787162b48f83a48127257dc8e23e31a859b7
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286981"
---
# <a name="dataadapter-parameters"></a><span data-ttu-id="e4346-103">DataAdapter 参数</span><span class="sxs-lookup"><span data-stu-id="e4346-103">DataAdapter Parameters</span></span>
<span data-ttu-id="e4346-104"><xref:System.Data.Common.DbDataAdapter> 具有四个用于从数据源检索数据和更新数据源中数据的属性：<xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> 属性返回数据源中的数据；<xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>、<xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> 和 <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> 属性用于管理数据源中的更改。</span><span class="sxs-lookup"><span data-stu-id="e4346-104">The <xref:System.Data.Common.DbDataAdapter> has four properties that are used to retrieve data from and update data to the data source: the <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> property returns data from the data source; and the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, and <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> properties are used to manage changes at the data source.</span></span> <span data-ttu-id="e4346-105">调用 `SelectCommand` 的 `Fill` 方法之前必须设置 `DataAdapter` 属性。</span><span class="sxs-lookup"><span data-stu-id="e4346-105">The `SelectCommand` property must be set before you call the `Fill` method of the `DataAdapter`.</span></span> <span data-ttu-id="e4346-106">在调用 `InsertCommand` 的 `UpdateCommand` 方法之前必须设置 `DeleteCommand`、`Update` 或 `DataAdapter` 属性，具体取决于对 <xref:System.Data.DataTable> 中的数据做了哪些更改。</span><span class="sxs-lookup"><span data-stu-id="e4346-106">The `InsertCommand`, `UpdateCommand`, or `DeleteCommand` properties must be set before the `Update` method of the `DataAdapter` is called, depending on what changes were made to the data in the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="e4346-107">例如，如果已添加行，在调用 `InsertCommand` 之前必须设置 `Update`。</span><span class="sxs-lookup"><span data-stu-id="e4346-107">For example, if rows have been added, the `InsertCommand` must be set before you call `Update`.</span></span> <span data-ttu-id="e4346-108">当 `Update` 正在处理已插入、已更新或已删除的行时，`DataAdapter` 将使用相应的 `Command` 属性来处理该操作。</span><span class="sxs-lookup"><span data-stu-id="e4346-108">When `Update` is processing an inserted, updated, or deleted row, the `DataAdapter` uses the respective `Command` property to process the action.</span></span> <span data-ttu-id="e4346-109">有关已修改行的当前信息将通过 `Command` 集合传递到 `Parameters` 对象。</span><span class="sxs-lookup"><span data-stu-id="e4346-109">Current information about the modified row is passed to the `Command` object through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="e4346-110">当您在数据源中更新行时，将调用 UPDATE 语句，该语句使用唯一标识符来标识要更新的表中的行。</span><span class="sxs-lookup"><span data-stu-id="e4346-110">When you update a row at the data source, you call the UPDATE statement, which uses a unique identifier to identify the row in the table to be updated.</span></span> <span data-ttu-id="e4346-111">该唯一标识符通常是主键字段的值。</span><span class="sxs-lookup"><span data-stu-id="e4346-111">The unique identifier is typically the value of a primary key field.</span></span> <span data-ttu-id="e4346-112">UPDATE 语句使用的参数既包含唯一标识符又包含要更新的列和值，如下面的 Transact-SQL 语句所示。</span><span class="sxs-lookup"><span data-stu-id="e4346-112">The UPDATE statement uses parameters that contain both the unique identifier and the columns and values to be updated, as shown in the following Transact-SQL statement.</span></span>  
  
```sql
UPDATE Customers SET CompanyName = @CompanyName
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
> <span data-ttu-id="e4346-113">参数占位符的语法取决于数据源。</span><span class="sxs-lookup"><span data-stu-id="e4346-113">The syntax for parameter placeholders depends on the data source.</span></span> <span data-ttu-id="e4346-114">此示例显示 SQL Server 数据源的占位符。</span><span class="sxs-lookup"><span data-stu-id="e4346-114">This example shows placeholders for a SQL Server data source.</span></span> <span data-ttu-id="e4346-115">使用问号 (?) 占位符代表 <xref:System.Data.OleDb> 和 <xref:System.Data.Odbc> 参数。</span><span class="sxs-lookup"><span data-stu-id="e4346-115">Use question mark (?) placeholders for <xref:System.Data.OleDb> and <xref:System.Data.Odbc> parameters.</span></span>  
  
 <span data-ttu-id="e4346-116">在此 Visual Basic 示例中，将 `CompanyName` 用 `@CompanyName` `CustomerID` 等于参数值的行的参数值更新字段 `@CustomerID` 。</span><span class="sxs-lookup"><span data-stu-id="e4346-116">In this Visual Basic example, the `CompanyName` field is updated with the value of the `@CompanyName` parameter for the row where `CustomerID` equals the value of the `@CustomerID` parameter.</span></span> <span data-ttu-id="e4346-117">参数使用对象的属性从修改的行中检索信息 <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> <xref:System.Data.SqlClient.SqlParameter> 。</span><span class="sxs-lookup"><span data-stu-id="e4346-117">The parameters retrieve information from the modified row using the <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> property of the <xref:System.Data.SqlClient.SqlParameter> object.</span></span> <span data-ttu-id="e4346-118">下面是上一示例 UPDATE 语句的参数。</span><span class="sxs-lookup"><span data-stu-id="e4346-118">The following are the parameters for the previous sample UPDATE statement.</span></span> <span data-ttu-id="e4346-119">代码假定变量 `adapter` 表示有效的 <xref:System.Data.SqlClient.SqlDataAdapter> 对象。</span><span class="sxs-lookup"><span data-stu-id="e4346-119">The code assumes that the variable `adapter` represents a valid <xref:System.Data.SqlClient.SqlDataAdapter> object.</span></span>  
  
```vb
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 <span data-ttu-id="e4346-120">`Add` 集合的 `Parameters` 方法接受参数的名称、数据类型、大小（如果适用于该类型）以及 <xref:System.Data.Common.DbParameter.SourceColumn%2A> 中的 `DataTable` 的名称。</span><span class="sxs-lookup"><span data-stu-id="e4346-120">The `Add` method of the `Parameters` collection takes the name of the parameter, the data type, the size (if applicable to the type), and the name of the <xref:System.Data.Common.DbParameter.SourceColumn%2A> from the `DataTable`.</span></span> <span data-ttu-id="e4346-121">请注意，<xref:System.Data.Common.DbParameter.SourceVersion%2A> 参数的 `@CustomerID` 设置为 `Original`。</span><span class="sxs-lookup"><span data-stu-id="e4346-121">Notice that the <xref:System.Data.Common.DbParameter.SourceVersion%2A> of the `@CustomerID` parameter is set to `Original`.</span></span> <span data-ttu-id="e4346-122">这样可以保证，如果标识列的值已经在修改后的 <xref:System.Data.DataRow> 中被更改，就一定会更新数据源中的现有行。</span><span class="sxs-lookup"><span data-stu-id="e4346-122">This guarantees that the existing row in the data source is updated if the value of the identifying column or columns has been changed in the modified <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="e4346-123">在这种情况下，`Original` 行值将匹配数据源中的当前值，而 `Current` 行值将包含更新的值。</span><span class="sxs-lookup"><span data-stu-id="e4346-123">In that case, the `Original` row value would match the current value at the data source, and the `Current` row value would contain the updated value.</span></span> <span data-ttu-id="e4346-124">没有设置 `SourceVersion` 参数的 `@CompanyName`，而将使用默认的 `Current` 行值。</span><span class="sxs-lookup"><span data-stu-id="e4346-124">The `SourceVersion` for the `@CompanyName` parameter is not set and uses the default, `Current` row value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4346-125">对于的 `Fill` 操作 `DataAdapter` 和的 `Get` 方法，将 `DataReader` 从 .NET Framework 数据提供程序返回的类型推断 .NET Framework 类型。</span><span class="sxs-lookup"><span data-stu-id="e4346-125">For both the `Fill` operations of the `DataAdapter` and the `Get` methods of the `DataReader`, the .NET Framework type is inferred from the type returned from the .NET Framework data provider.</span></span> <span data-ttu-id="e4346-126">ADO.NET 中的[数据类型映射](data-type-mappings-in-ado-net.md)中介绍了 Microsoft SQL Server、OLE DB 和 ODBC 数据类型的推断 .NET Framework 类型和访问器方法。</span><span class="sxs-lookup"><span data-stu-id="e4346-126">The inferred .NET Framework types and accessor methods for Microsoft SQL Server, OLE DB, and ODBC data types are described in [Data Type Mappings in ADO.NET](data-type-mappings-in-ado-net.md).</span></span>  
  
## <a name="parametersourcecolumn-parametersourceversion"></a><span data-ttu-id="e4346-127">Parameter.SourceColumn，Parameter.SourceVersion</span><span class="sxs-lookup"><span data-stu-id="e4346-127">Parameter.SourceColumn, Parameter.SourceVersion</span></span>  
 <span data-ttu-id="e4346-128">`SourceColumn` 和 `SourceVersion` 可以作为自变量传递给 `Parameter` 构造函数，也可以设置为现有 `Parameter` 的属性。</span><span class="sxs-lookup"><span data-stu-id="e4346-128">The `SourceColumn` and `SourceVersion` may be passed as arguments to the `Parameter` constructor, or set as properties of an existing `Parameter`.</span></span> <span data-ttu-id="e4346-129">`SourceColumn` 是将要从中检索 <xref:System.Data.DataColumn> 值的 <xref:System.Data.DataRow> 中的 `Parameter` 的名称。</span><span class="sxs-lookup"><span data-stu-id="e4346-129">The `SourceColumn` is the name of the <xref:System.Data.DataColumn> from the <xref:System.Data.DataRow> where the value of the `Parameter` will be retrieved.</span></span> <span data-ttu-id="e4346-130">`SourceVersion` 指定 `DataRow` 用于检索该值的 `DataAdapter` 版本。</span><span class="sxs-lookup"><span data-stu-id="e4346-130">The `SourceVersion` specifies the `DataRow` version that the `DataAdapter` uses to retrieve the value.</span></span>  
  
 <span data-ttu-id="e4346-131">下表显示可以与 <xref:System.Data.DataRowVersion> 一起使用的 `SourceVersion` 枚举值。</span><span class="sxs-lookup"><span data-stu-id="e4346-131">The following table shows the <xref:System.Data.DataRowVersion> enumeration values available for use with `SourceVersion`.</span></span>  
  
|<span data-ttu-id="e4346-132">DataRowVersion 枚举</span><span class="sxs-lookup"><span data-stu-id="e4346-132">DataRowVersion Enumeration</span></span>|<span data-ttu-id="e4346-133">说明</span><span class="sxs-lookup"><span data-stu-id="e4346-133">Description</span></span>|  
|--------------------------------|-----------------|  
|`Current`|<span data-ttu-id="e4346-134">该参数使用列的当前值。</span><span class="sxs-lookup"><span data-stu-id="e4346-134">The parameter uses the current value of the column.</span></span> <span data-ttu-id="e4346-135">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="e4346-135">This is the default.</span></span>|  
|`Default`|<span data-ttu-id="e4346-136">该参数使用列的 `DefaultValue`。</span><span class="sxs-lookup"><span data-stu-id="e4346-136">The parameter uses the `DefaultValue` of the column.</span></span>|  
|`Original`|<span data-ttu-id="e4346-137">该参数使用列的原始值。</span><span class="sxs-lookup"><span data-stu-id="e4346-137">The parameter uses the original value of the column.</span></span>|  
|`Proposed`|<span data-ttu-id="e4346-138">该参数使用建议值。</span><span class="sxs-lookup"><span data-stu-id="e4346-138">The parameter uses a proposed value.</span></span>|  
  
 <span data-ttu-id="e4346-139">下一节中的 `SqlClient` 代码示例为 <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> 定义了一个参数，在该示例中 `CustomerID` 列用作以下两个参数的 `SourceColumn`：`@CustomerID` (`SET CustomerID = @CustomerID`) 和 `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`)。</span><span class="sxs-lookup"><span data-stu-id="e4346-139">The `SqlClient` code example in the next section defines a parameter for an <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> in which the `CustomerID` column is used as a `SourceColumn` for two parameters: `@CustomerID` (`SET CustomerID = @CustomerID`), and `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`).</span></span> <span data-ttu-id="e4346-140">`@CustomerID`参数用于将**CustomerID**列更新为中的当前值 `DataRow` 。</span><span class="sxs-lookup"><span data-stu-id="e4346-140">The `@CustomerID` parameter is used to update the **CustomerID** column to the current value in the `DataRow`.</span></span> <span data-ttu-id="e4346-141">因此， `CustomerID` `SourceColumn` `SourceVersion` 使用带有的 `Current` 。</span><span class="sxs-lookup"><span data-stu-id="e4346-141">As a result, the `CustomerID` `SourceColumn` with a `SourceVersion` of `Current` is used.</span></span> <span data-ttu-id="e4346-142">`@OldCustomerID`参数用于标识数据源中的当前行。</span><span class="sxs-lookup"><span data-stu-id="e4346-142">The `@OldCustomerID` parameter is used to identify the current row in the data source.</span></span> <span data-ttu-id="e4346-143">由于在该行的 `Original` 版本中找到了匹配列值，所以将使用 `SourceColumn` 为 `CustomerID` 的相同 `SourceVersion` (`Original`)。</span><span class="sxs-lookup"><span data-stu-id="e4346-143">Because the matching column value is found in the `Original` version of the row, the same `SourceColumn` (`CustomerID`) with a `SourceVersion` of `Original` is used.</span></span>  
  
## <a name="working-with-sqlclient-parameters"></a><span data-ttu-id="e4346-144">使用 SqlClient 参数</span><span class="sxs-lookup"><span data-stu-id="e4346-144">Working with SqlClient Parameters</span></span>  
 <span data-ttu-id="e4346-145">下面的示例演示如何创建 <xref:System.Data.SqlClient.SqlDataAdapter> 并将 <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> 设置为 <xref:System.Data.MissingSchemaAction.AddWithKey>，以便从数据库中检索其他架构信息。</span><span class="sxs-lookup"><span data-stu-id="e4346-145">The following example demonstrates how to create a <xref:System.Data.SqlClient.SqlDataAdapter> and set the <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> to <xref:System.Data.MissingSchemaAction.AddWithKey> in order to retrieve additional schema information from the database.</span></span> <span data-ttu-id="e4346-146"><xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>、<xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>、<xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A> 和 <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> 属性集及其相应的 <xref:System.Data.SqlClient.SqlParameter> 对象已添加到 <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> 集合。</span><span class="sxs-lookup"><span data-stu-id="e4346-146">The <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties set and their corresponding <xref:System.Data.SqlClient.SqlParameter> objects added to the <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection.</span></span> <span data-ttu-id="e4346-147">该方法返回一个 `SqlDataAdapter` 对象。</span><span class="sxs-lookup"><span data-stu-id="e4346-147">The method returns a `SqlDataAdapter` object.</span></span>  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a><span data-ttu-id="e4346-148">OleDb 参数占位符</span><span class="sxs-lookup"><span data-stu-id="e4346-148">OleDb Parameter Placeholders</span></span>  
 <span data-ttu-id="e4346-149">对于 <xref:System.Data.OleDb.OleDbDataAdapter> 对象和 <xref:System.Data.Odbc.OdbcDataAdapter> 对象，必须使用问号 (?) 占位符来标识参数。</span><span class="sxs-lookup"><span data-stu-id="e4346-149">For the <xref:System.Data.OleDb.OleDbDataAdapter> and <xref:System.Data.Odbc.OdbcDataAdapter> objects, you must use question mark (?) placeholders to identify the parameters.</span></span>  
  
```vb  
Dim selectSQL As String = _  
  "SELECT CustomerID, CompanyName FROM Customers " & _  
  "WHERE CountryRegion = ? AND City = ?"  
Dim insertSQL AS String = _  
  "INSERT INTO Customers (CustomerID, CompanyName) VALUES (?, ?)"  
Dim updateSQL AS String = _  
  "UPDATE Customers SET CustomerID = ?, CompanyName = ? " & _  
  WHERE CustomerID = ?"  
Dim deleteSQL As String = "DELETE FROM Customers WHERE CustomerID = ?"  
```  
  
```csharp  
string selectSQL =
  "SELECT CustomerID, CompanyName FROM Customers " +  
  "WHERE CountryRegion = ? AND City = ?";  
string insertSQL =
  "INSERT INTO Customers (CustomerID, CompanyName) " +  
  "VALUES (?, ?)";  
string updateSQL =
  "UPDATE Customers SET CustomerID = ?, CompanyName = ? " +  
  "WHERE CustomerID = ? ";  
string deleteSQL = "DELETE FROM Customers WHERE CustomerID = ?";  
```  
  
 <span data-ttu-id="e4346-150">参数化查询语句定义必须创建的输入和输出参数。</span><span class="sxs-lookup"><span data-stu-id="e4346-150">The parameterized query statements define which input and output parameters must be created.</span></span> <span data-ttu-id="e4346-151">若要创建参数，请使用 `Parameters.Add` 方法或 `Parameter` 构造函数来指定列名称、数据类型和大小。</span><span class="sxs-lookup"><span data-stu-id="e4346-151">To create a parameter, use the `Parameters.Add` method or the `Parameter` constructor to specify the column name, data type, and size.</span></span> <span data-ttu-id="e4346-152">对于内部数据类型（如 `Integer`）无需包含大小，也可以指定默认大小。</span><span class="sxs-lookup"><span data-stu-id="e4346-152">For intrinsic data types, such as `Integer`, you do not have to include the size, or you can specify the default size.</span></span>  
  
 <span data-ttu-id="e4346-153">下面的代码示例创建 SQL 语句的参数，然后填充 `DataSet`。</span><span class="sxs-lookup"><span data-stu-id="e4346-153">The following code example creates the parameters for a SQL statement and then fills a `DataSet`.</span></span>  
  
## <a name="oledb-example"></a><span data-ttu-id="e4346-154">OleDb 示例</span><span class="sxs-lookup"><span data-stu-id="e4346-154">OleDb Example</span></span>  
  
```vb  
' Assumes that connection is a valid OleDbConnection object.  
Dim adapter As OleDbDataAdapter = New OleDbDataAdapter
  
Dim selectCMD AS OleDbCommand = New OleDbCommand(selectSQL, connection)  
adapter.SelectCommand = selectCMD  
  
' Add parameters and set values.  
selectCMD.Parameters.Add( _  
  "@CountryRegion", OleDbType.VarChar, 15).Value = "UK"  
selectCMD.Parameters.Add( _  
  "@City", OleDbType.VarChar, 15).Value = "London"  
  
Dim customers As DataSet = New DataSet  
adapter.Fill(customers, "Customers")  
```  
  
```csharp  
// Assumes that connection is a valid OleDbConnection object.  
OleDbDataAdapter adapter = new OleDbDataAdapter();  
  
OleDbCommand selectCMD = new OleDbCommand(selectSQL, connection);  
adapter.SelectCommand = selectCMD;  
  
// Add parameters and set values.  
selectCMD.Parameters.Add(  
  "@CountryRegion", OleDbType.VarChar, 15).Value = "UK";  
selectCMD.Parameters.Add(  
  "@City", OleDbType.VarChar, 15).Value = "London";  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
```  
  
## <a name="odbc-parameters"></a><span data-ttu-id="e4346-155">Odbc 参数</span><span class="sxs-lookup"><span data-stu-id="e4346-155">Odbc Parameters</span></span>  
  
```vb  
' Assumes that connection is a valid OdbcConnection object.  
Dim adapter As OdbcDataAdapter = New OdbcDataAdapter  
  
Dim selectCMD AS OdbcCommand = New OdbcCommand(selectSQL, connection)  
adapter.SelectCommand = selectCMD  
  
' Add Parameters and set values.  
selectCMD.Parameters.Add("@CountryRegion", OdbcType.VarChar, 15).Value = "UK"  
selectCMD.Parameters.Add("@City", OdbcType.VarChar, 15).Value = "London"  
  
Dim customers As DataSet = New DataSet  
adapter.Fill(customers, "Customers")  
```  
  
```csharp  
// Assumes that connection is a valid OdbcConnection object.  
OdbcDataAdapter adapter = new OdbcDataAdapter();  
  
OdbcCommand selectCMD = new OdbcCommand(selectSQL, connection);  
adapter.SelectCommand = selectCMD;  
  
//Add Parameters and set values.  
selectCMD.Parameters.Add("@CountryRegion", OdbcType.VarChar, 15).Value = "UK";  
selectCMD.Parameters.Add("@City", OdbcType.VarChar, 15).Value = "London";  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
```  
  
> [!NOTE]
> <span data-ttu-id="e4346-156">如果没有为参数提供参数名称，则会为该参数指定增量默认名称 parameter*N* *，* 以 "Parameter1" 开头。</span><span class="sxs-lookup"><span data-stu-id="e4346-156">If a parameter name is not supplied for a parameter, the parameter is given an incremental default name of Parameter*N* *,* starting with "Parameter1".</span></span> <span data-ttu-id="e4346-157">建议在提供参数名称时避免使用参数*N*命名约定，因为所提供的名称可能会与中现有的默认参数名称冲突 `ParameterCollection` 。</span><span class="sxs-lookup"><span data-stu-id="e4346-157">We recommend that you avoid the Parameter*N* naming convention when you supply a parameter name, because the name that you supply might conflict with an existing default parameter name in the `ParameterCollection`.</span></span> <span data-ttu-id="e4346-158">如果提供的名称已经存在，将引发异常。</span><span class="sxs-lookup"><span data-stu-id="e4346-158">If the supplied name already exists, an exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4346-159">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e4346-159">See also</span></span>

- [<span data-ttu-id="e4346-160">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="e4346-160">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="e4346-161">命令和参数</span><span class="sxs-lookup"><span data-stu-id="e4346-161">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="e4346-162">使用 DataAdapter 更新数据源</span><span class="sxs-lookup"><span data-stu-id="e4346-162">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="e4346-163">使用存储过程修改数据</span><span class="sxs-lookup"><span data-stu-id="e4346-163">Modifying Data with Stored Procedures</span></span>](modifying-data-with-stored-procedures.md)
- [<span data-ttu-id="e4346-164">ADO.NET 中的数据类型映射</span><span class="sxs-lookup"><span data-stu-id="e4346-164">Data Type Mappings in ADO.NET</span></span>](data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="e4346-165">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="e4346-165">ADO.NET Overview</span></span>](ado-net-overview.md)

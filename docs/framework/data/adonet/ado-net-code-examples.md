---
title: 代码示例
description: 这些示例演示 .NET Framework 程序员如何使用 ADO.NET 数据提供程序和 ADO.NET 实体框架从数据库中检索数据。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c119657a-9ce6-4940-91e4-ac1d5f0d9584
ms.openlocfilehash: 54df0e253716c970cf23446434d96b104b8e9b03
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287163"
---
# <a name="adonet-code-examples"></a><span data-ttu-id="ebf00-103">ADO.NET 代码示例</span><span class="sxs-lookup"><span data-stu-id="ebf00-103">ADO.NET code examples</span></span>

<span data-ttu-id="ebf00-104">本页上的代码列表演示如何使用以下 ADO.NET 技术从数据库中检索数据：</span><span class="sxs-lookup"><span data-stu-id="ebf00-104">The code listings on this page demonstrate how to retrieve data from a database by using the following ADO.NET technologies:</span></span>

- <span data-ttu-id="ebf00-105">ADO.NET 数据提供程序：</span><span class="sxs-lookup"><span data-stu-id="ebf00-105">ADO.NET data providers:</span></span>

  - <span data-ttu-id="ebf00-106">[SqlClient](#sqlclient) （ `System.Data.SqlClient` ）</span><span class="sxs-lookup"><span data-stu-id="ebf00-106">[SqlClient](#sqlclient) (`System.Data.SqlClient`)</span></span>

  - <span data-ttu-id="ebf00-107">[OleDb](#oledb) （ `System.Data.OleDb` ）</span><span class="sxs-lookup"><span data-stu-id="ebf00-107">[OleDb](#oledb) (`System.Data.OleDb`)</span></span>

  - <span data-ttu-id="ebf00-108">[Odbc](#odbc) （ `System.Data.Odbc` ）</span><span class="sxs-lookup"><span data-stu-id="ebf00-108">[Odbc](#odbc) (`System.Data.Odbc`)</span></span>

  - <span data-ttu-id="ebf00-109">[System.data.oracleclient](#oracleclient) （ `System.Data.OracleClient` ）</span><span class="sxs-lookup"><span data-stu-id="ebf00-109">[OracleClient](#oracleclient) (`System.Data.OracleClient`)</span></span>

- <span data-ttu-id="ebf00-110">ADO.NET 实体框架：</span><span class="sxs-lookup"><span data-stu-id="ebf00-110">ADO.NET Entity Framework:</span></span>

  - [<span data-ttu-id="ebf00-111">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="ebf00-111">LINQ to Entities</span></span>](#linq-to-entities)

  - [<span data-ttu-id="ebf00-112">类型化 ObjectQuery</span><span class="sxs-lookup"><span data-stu-id="ebf00-112">Typed ObjectQuery</span></span>](#typed-objectquery)

  - <span data-ttu-id="ebf00-113">[EntityClient](#entityclient) （ `System.Data.EntityClient` ）</span><span class="sxs-lookup"><span data-stu-id="ebf00-113">[EntityClient](#entityclient) (`System.Data.EntityClient`)</span></span>

- [<span data-ttu-id="ebf00-114">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ebf00-114">LINQ to SQL</span></span>](#linq-to-sql)

## <a name="adonet-data-provider-examples"></a><span data-ttu-id="ebf00-115">ADO.NET 数据提供程序示例</span><span class="sxs-lookup"><span data-stu-id="ebf00-115">ADO.NET data provider examples</span></span>
<span data-ttu-id="ebf00-116">以下代码列表演示如何使用 ADO.NET 数据提供程序从数据库中检索数据。</span><span class="sxs-lookup"><span data-stu-id="ebf00-116">The following code listings demonstrate how to retrieve data from a database using ADO.NET data providers.</span></span> <span data-ttu-id="ebf00-117">数据在一个 `DataReader` 中返回。</span><span class="sxs-lookup"><span data-stu-id="ebf00-117">The data is returned in a `DataReader`.</span></span> <span data-ttu-id="ebf00-118">有关详细信息，请参阅[使用 DataReader 检索数据](retrieving-data-using-a-datareader.md)。</span><span class="sxs-lookup"><span data-stu-id="ebf00-118">For more information, see [Retrieving Data Using a DataReader](retrieving-data-using-a-datareader.md).</span></span>

### <a name="sqlclient"></a><span data-ttu-id="ebf00-119">SqlClient</span><span class="sxs-lookup"><span data-stu-id="ebf00-119">SqlClient</span></span>
<span data-ttu-id="ebf00-120">本示例中的代码假定您可以连接到 `Northwind` Microsoft SQL Server 上的示例数据库。</span><span class="sxs-lookup"><span data-stu-id="ebf00-120">The code in this example assumes that you can connect to the `Northwind` sample database on Microsoft SQL Server.</span></span> <span data-ttu-id="ebf00-121">在此情形 5 中，示例代码创建一个 <xref:System.Data.SqlClient.SqlCommand> 以从 Products 表中选择行，并添加 <xref:System.Data.SqlClient.SqlParameter> 来将结果限制为其 UnitPrice 大于指定参数值的行。</span><span class="sxs-lookup"><span data-stu-id="ebf00-121">The code creates a <xref:System.Data.SqlClient.SqlCommand> to select rows from the Products table, adding a <xref:System.Data.SqlClient.SqlParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="ebf00-122">在 <xref:System.Data.SqlClient.SqlConnection> 块中打开 `using` ，这可确保在代码退出时关闭并释放资源。</span><span class="sxs-lookup"><span data-stu-id="ebf00-122">The <xref:System.Data.SqlClient.SqlConnection> is opened inside a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="ebf00-123">示例代码使用 <xref:System.Data.SqlClient.SqlDataReader> 执行命令，并在控制台窗口中显示结果。</span><span class="sxs-lookup"><span data-stu-id="ebf00-123">The code executes the command by using a <xref:System.Data.SqlClient.SqlDataReader>, and displays the results in the console window.</span></span>

 [!code-csharp[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/VB/source.vb#1)]

### <a name="oledb"></a><span data-ttu-id="ebf00-124">OleDb</span><span class="sxs-lookup"><span data-stu-id="ebf00-124">OleDb</span></span>
<span data-ttu-id="ebf00-125">此示例中的代码假定你可以连接到 Microsoft Access Northwind 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="ebf00-125">The code in this example assumes that you can connect to the Microsoft Access Northwind sample database.</span></span> <span data-ttu-id="ebf00-126">在此情形 5 中，示例代码创建一个 <xref:System.Data.OleDb.OleDbCommand> 以从 Products 表中选择行，并添加 <xref:System.Data.OleDb.OleDbParameter> 来将结果限制为其 UnitPrice 大于指定参数值的行。</span><span class="sxs-lookup"><span data-stu-id="ebf00-126">The code creates a <xref:System.Data.OleDb.OleDbCommand> to select rows from the Products table, adding a <xref:System.Data.OleDb.OleDbParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="ebf00-127"><xref:System.Data.OleDb.OleDbConnection> 在 `using` 块内打开，这将确保在代码退出时会关闭和释放资源。</span><span class="sxs-lookup"><span data-stu-id="ebf00-127">The <xref:System.Data.OleDb.OleDbConnection> is opened inside of a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="ebf00-128">示例代码使用 <xref:System.Data.OleDb.OleDbDataReader> 执行命令，并在控制台窗口中显示结果。</span><span class="sxs-lookup"><span data-stu-id="ebf00-128">The code executes the command by using a <xref:System.Data.OleDb.OleDbDataReader>, and displays the results in the console window.</span></span>

 [!code-csharp[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/VB/source.vb#1)]

### <a name="odbc"></a><span data-ttu-id="ebf00-129">Odbc</span><span class="sxs-lookup"><span data-stu-id="ebf00-129">Odbc</span></span>
<span data-ttu-id="ebf00-130">此示例中的代码假定你可以连接到 Microsoft Access Northwind 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="ebf00-130">The code in this example assumes that you can connect to the Microsoft Access Northwind sample database.</span></span> <span data-ttu-id="ebf00-131">在此情形 5 中，示例代码创建一个 <xref:System.Data.Odbc.OdbcCommand> 以从 Products 表中选择行，并添加 <xref:System.Data.Odbc.OdbcParameter> 来将结果限制为其 UnitPrice 大于指定参数值的行。</span><span class="sxs-lookup"><span data-stu-id="ebf00-131">The code creates a <xref:System.Data.Odbc.OdbcCommand> to select rows from the Products table, adding a <xref:System.Data.Odbc.OdbcParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="ebf00-132">在 <xref:System.Data.Odbc.OdbcConnection> 块中打开 `using` ，这可确保在代码退出时关闭并释放资源。</span><span class="sxs-lookup"><span data-stu-id="ebf00-132">The <xref:System.Data.Odbc.OdbcConnection> is opened inside a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="ebf00-133">示例代码使用 <xref:System.Data.Odbc.OdbcDataReader> 执行命令，并在控制台窗口中显示结果。</span><span class="sxs-lookup"><span data-stu-id="ebf00-133">The code executes the command by using a <xref:System.Data.Odbc.OdbcDataReader>, and displays the results in the console window.</span></span>

[!code-csharp[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/CS/source.cs#1)]
[!code-vb[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/VB/source.vb#1)]

### <a name="oracleclient"></a><span data-ttu-id="ebf00-134">OracleClient</span><span class="sxs-lookup"><span data-stu-id="ebf00-134">OracleClient</span></span>
<span data-ttu-id="ebf00-135">此示例中的代码假定已建立与 Oracle 服务器上的 DEMO.CUSTOMER 的连接。</span><span class="sxs-lookup"><span data-stu-id="ebf00-135">The code in this example assumes a connection to DEMO.CUSTOMER on an Oracle server.</span></span> <span data-ttu-id="ebf00-136">您还必须添加对 System.Data.OracleClient.dll 的引用。</span><span class="sxs-lookup"><span data-stu-id="ebf00-136">You must also add a reference to the System.Data.OracleClient.dll.</span></span> <span data-ttu-id="ebf00-137">示例代码在 <xref:System.Data.OracleClient.OracleDataReader> 中返回数据。</span><span class="sxs-lookup"><span data-stu-id="ebf00-137">The code returns the data in an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>

 [!code-csharp[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/VB/source.vb#1)]

## <a name="entity-framework-examples"></a><span data-ttu-id="ebf00-138">实体框架示例</span><span class="sxs-lookup"><span data-stu-id="ebf00-138">Entity Framework examples</span></span>
<span data-ttu-id="ebf00-139">以下代码列表演示如何通过查询实体数据模型 (EDM) 中的实体来从数据源检索数据。</span><span class="sxs-lookup"><span data-stu-id="ebf00-139">The following code listings demonstrate how to retrieve data from a data source by querying entities in an Entity Data Model (EDM).</span></span> <span data-ttu-id="ebf00-140">这些示例使用基于 Northwind 示例数据库的模型。</span><span class="sxs-lookup"><span data-stu-id="ebf00-140">These examples use a model based on the Northwind sample database.</span></span> <span data-ttu-id="ebf00-141">有关实体框架的详细信息，请参阅[实体框架概述](./ef/overview.md)。</span><span class="sxs-lookup"><span data-stu-id="ebf00-141">For more information about Entity Framework, see [Entity Framework Overview](./ef/overview.md).</span></span>

### <a name="linq-to-entities"></a><span data-ttu-id="ebf00-142">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="ebf00-142">LINQ to Entities</span></span>
<span data-ttu-id="ebf00-143">此示例中的代码使用 LINQ 查询以 Categories 对象的形式返回数据，这些对象将作为仅包含 CategoryID 和 CategoryName 属性的匿名类型提取。</span><span class="sxs-lookup"><span data-stu-id="ebf00-143">The code in this example uses a LINQ query to return data as Categories objects, which are projected as an anonymous type that contains only the CategoryID and CategoryName properties.</span></span> <span data-ttu-id="ebf00-144">有关详细信息，请参阅[LINQ to Entities 概述](./ef/language-reference/linq-to-entities.md)。</span><span class="sxs-lookup"><span data-stu-id="ebf00-144">For more information, see [LINQ to Entities Overview](./ef/language-reference/linq-to-entities.md).</span></span>

```csharp
using System;
using System.Linq;
using System.Data.Objects;
using NorthwindModel;

class LinqSample
{
    public static void ExecuteQuery()
    {
        using (NorthwindEntities context = new NorthwindEntities())
        {
            try
            {
                var query = from category in context.Categories
                            select new
                            {
                                categoryID = category.CategoryID,
                                categoryName = category.CategoryName
                            };

                foreach (var categoryInfo in query)
                {
                    Console.WriteLine("\t{0}\t{1}",
                        categoryInfo.categoryID, categoryInfo.categoryName);
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
        }
    }
}
```

```vb
Option Explicit On
Option Strict On

Imports System.Linq
Imports System.Data.Objects
Imports NorthwindModel

Class LinqSample
    Public Shared Sub ExecuteQuery()
        Using context As NorthwindEntities = New NorthwindEntities()
            Try
                Dim query = From category In context.Categories _
                            Select New With _
                            { _
                                .categoryID = category.CategoryID, _
                                .categoryName = category.CategoryName _
                            }

                For Each categoryInfo In query
                    Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                        categoryInfo.categoryID, categoryInfo.categoryName)
                Next
            Catch ex As Exception
                Console.WriteLine(ex.Message)
            End Try
        End Using
    End Sub
End Class
```

### <a name="typed-objectquery"></a><span data-ttu-id="ebf00-145">类型化 ObjectQuery</span><span class="sxs-lookup"><span data-stu-id="ebf00-145">Typed ObjectQuery</span></span>
<span data-ttu-id="ebf00-146">此示例中的代码使用 <xref:System.Data.Objects.ObjectQuery%601> 以 Categories 对象的形式返回数据。</span><span class="sxs-lookup"><span data-stu-id="ebf00-146">The code in this example uses an <xref:System.Data.Objects.ObjectQuery%601> to return data as Categories objects.</span></span> <span data-ttu-id="ebf00-147">有关详细信息，请参阅[对象查询](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="ebf00-147">For more information, see [Object Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100)).</span></span>

```csharp
using System;
using System.Data.Objects;
using NorthwindModel;

class ObjectQuerySample
{
    public static void ExecuteQuery()
    {
        using (NorthwindEntities context = new NorthwindEntities())
        {
            ObjectQuery<Categories> categoryQuery = context.Categories;

            foreach (Categories category in
                categoryQuery.Execute(MergeOption.AppendOnly))
            {
                Console.WriteLine("\t{0}\t{1}",
                    category.CategoryID, category.CategoryName);
            }
        }
    }
}
```

```vb
Option Explicit On
Option Strict On

Imports System.Data.Objects
Imports NorthwindModel

Class ObjectQuerySample
    Public Shared Sub ExecuteQuery()
        Using context As NorthwindEntities = New NorthwindEntities()
            Dim categoryQuery As ObjectQuery(Of Categories) = context.Categories

            For Each category As Categories In _
                categoryQuery.Execute(MergeOption.AppendOnly)
                Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                    category.CategoryID, category.CategoryName)
            Next
        End Using
    End Sub
End Class
```

### <a name="entityclient"></a><span data-ttu-id="ebf00-148">EntityClient</span><span class="sxs-lookup"><span data-stu-id="ebf00-148">EntityClient</span></span>
<span data-ttu-id="ebf00-149">此示例中的代码使用 <xref:System.Data.EntityClient.EntityCommand> 来执行实体 SQL 查询。</span><span class="sxs-lookup"><span data-stu-id="ebf00-149">The code in this example uses an <xref:System.Data.EntityClient.EntityCommand> to execute an Entity SQL query.</span></span> <span data-ttu-id="ebf00-150">此查询会返回表示 Categories 实体类型的实例的记录的列表。</span><span class="sxs-lookup"><span data-stu-id="ebf00-150">This query returns a list of records that represent instances of the Categories entity type.</span></span> <span data-ttu-id="ebf00-151"><xref:System.Data.EntityClient.EntityDataReader> 用于访问结果集中的数据记录。</span><span class="sxs-lookup"><span data-stu-id="ebf00-151">An <xref:System.Data.EntityClient.EntityDataReader> is used to access data records in the result set.</span></span> <span data-ttu-id="ebf00-152">有关详细信息，请参阅 [用于 Entity Framework 的 EntityClient 提供程序](./ef/entityclient-provider-for-the-entity-framework.md)。</span><span class="sxs-lookup"><span data-stu-id="ebf00-152">For more information, see [EntityClient Provider for the Entity Framework](./ef/entityclient-provider-for-the-entity-framework.md).</span></span>

```csharp
using System;
using System.Data;
using System.Data.Common;
using System.Data.EntityClient;
using NorthwindModel;

class EntityClientSample
{
    public static void ExecuteQuery()
    {
        string queryString =
            @"SELECT c.CategoryID, c.CategoryName
                FROM NorthwindEntities.Categories AS c";

        using (EntityConnection conn =
            new EntityConnection("name=NorthwindEntities"))
        {
            try
            {
                conn.Open();
                using (EntityCommand query = new EntityCommand(queryString, conn))
                {
                    using (DbDataReader rdr =
                        query.ExecuteReader(CommandBehavior.SequentialAccess))
                    {
                        while (rdr.Read())
                        {
                            Console.WriteLine("\t{0}\t{1}", rdr[0], rdr[1]);
                        }
                    }
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
        }
    }
}
```

```vb
Option Explicit On
Option Strict On

Imports System.Data
Imports System.Data.Common
Imports System.Data.EntityClient
Imports NorthwindModel

Class EntityClientSample
    Public Shared Sub ExecuteQuery()
        Dim queryString As String = _
            "SELECT c.CategoryID, c.CategoryName " & _
                "FROM NorthwindEntities.Categories AS c"

        Using conn As EntityConnection = _
            New EntityConnection("name=NorthwindEntities")

            Try
                conn.Open()
                Using query As EntityCommand = _
                New EntityCommand(queryString, conn)
                    Using rdr As DbDataReader = _
                        query.ExecuteReader(CommandBehavior.SequentialAccess)
                        While rdr.Read()
                            Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                                              rdr(0), rdr(1))
                        End While
                    End Using
                End Using
            Catch ex As Exception
                Console.WriteLine(ex.Message)
            End Try
        End Using
    End Sub
End Class
```

## <a name="linq-to-sql"></a><span data-ttu-id="ebf00-153">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ebf00-153">LINQ to SQL</span></span>
<span data-ttu-id="ebf00-154">此示例中的代码使用 LINQ 查询以 Categories 对象的形式返回数据，这些对象将作为仅包含 CategoryID 和 CategoryName 属性的匿名类型提取。</span><span class="sxs-lookup"><span data-stu-id="ebf00-154">The code in this example uses a LINQ query to return data as Categories objects, which are projected as an anonymous type that contains only the CategoryID and CategoryName properties.</span></span> <span data-ttu-id="ebf00-155">此示例基于 Northwind 数据上下文。</span><span class="sxs-lookup"><span data-stu-id="ebf00-155">This example is based on the Northwind data context.</span></span> <span data-ttu-id="ebf00-156">有关详细信息，请参阅[入门](./sql/linq/getting-started.md)。</span><span class="sxs-lookup"><span data-stu-id="ebf00-156">For more information, see [Getting Started](./sql/linq/getting-started.md).</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Northwind;

    class LinqSqlSample
    {
        public static void ExecuteQuery()
        {
            using (NorthwindDataContext db = new NorthwindDataContext())
            {
                try
                {
                    var query = from category in db.Categories
                                select new
                                {
                                    categoryID = category.CategoryID,
                                    categoryName = category.CategoryName
                                };

                    foreach (var categoryInfo in query)
                    {
                        Console.WriteLine("vbTab {0} vbTab {1}",
                            categoryInfo.categoryID, categoryInfo.categoryName);
                    }
                }
                catch (Exception ex)
                {
                    Console.WriteLine(ex.Message);
                }
            }
        }
    }
```

```vb
Option Explicit On
Option Strict On

Imports System.Collections.Generic
Imports System.Linq
Imports System.Text
Imports Northwind

Class LinqSqlSample
    Public Shared Sub ExecuteQuery()
        Using db As NorthwindDataContext = New NorthwindDataContext()
            Try
                Dim query = From category In db.Categories _
                                Select New With _
                                { _
                                    .categoryID = category.CategoryID, _
                                    .categoryName = category.CategoryName _
                                }

                For Each categoryInfo In query
                    Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                            categoryInfo.categoryID, categoryInfo.categoryName)
                Next
            Catch ex As Exception
                Console.WriteLine(ex.Message)
            End Try
            End Using
    End Sub
End Class
```

## <a name="see-also"></a><span data-ttu-id="ebf00-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ebf00-157">See also</span></span>

- [<span data-ttu-id="ebf00-158">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="ebf00-158">ADO.NET Overview</span></span>](ado-net-overview.md)
- [<span data-ttu-id="ebf00-159">在 ADO.NET 中检索和修改数据</span><span class="sxs-lookup"><span data-stu-id="ebf00-159">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- <span data-ttu-id="ebf00-160">[创建数据应用程序](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h0y4a0f6(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="ebf00-160">[Creating Data Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h0y4a0f6(v=vs.120))</span></span>
- <span data-ttu-id="ebf00-161">[查询实体数据模型（实体框架任务）](https://docs.microsoft.com/previous-versions/bb738455(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="ebf00-161">[Querying an Entity Data Model (Entity Framework Tasks)](https://docs.microsoft.com/previous-versions/bb738455(v=vs.90))</span></span>
- <span data-ttu-id="ebf00-162">[如何：执行返回匿名类型对象的查询](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ebf00-162">[How to: Execute a Query that Returns Anonymous Type Objects](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span></span>

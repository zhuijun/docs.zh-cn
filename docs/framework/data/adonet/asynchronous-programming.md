---
title: 异步编程
description: 了解适用于 SQL Server 的 .NET Framework 数据提供程序中的异步编程，包括 .NET Framework 4.5 中引入的增强功能。
ms.date: 10/18/2018
ms.assetid: 85da7447-7125-426e-aa5f-438a290d1f77
ms.openlocfilehash: b8f718e0def2ab0b6953ed121eb916f282562d32
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558467"
---
# <a name="asynchronous-programming"></a><span data-ttu-id="f2426-103">异步编程</span><span class="sxs-lookup"><span data-stu-id="f2426-103">Asynchronous Programming</span></span>

<span data-ttu-id="f2426-104">本主题讨论对 SQL Server (SqlClient 的 .NET Framework 数据提供程序中的异步编程的支持) 包括为支持 .NET Framework 4.5 中引入的异步编程功能所做的增强。</span><span class="sxs-lookup"><span data-stu-id="f2426-104">This topic discusses support for asynchronous programming in the .NET Framework Data Provider for SQL Server (SqlClient) including enhancements made to support asynchronous programming functionality that was introduced in .NET Framework 4.5.</span></span>

## <a name="legacy-asynchronous-programming"></a><span data-ttu-id="f2426-105">旧版异步编程</span><span class="sxs-lookup"><span data-stu-id="f2426-105">Legacy Asynchronous Programming</span></span>

<span data-ttu-id="f2426-106">在 .NET Framework 4.5 之前，通过以下方法和连接属性实现了 SqlClient 的异步编程 `Asynchronous Processing=true` ：</span><span class="sxs-lookup"><span data-stu-id="f2426-106">Prior to .NET Framework 4.5, asynchronous programming with SqlClient was done with the following methods and the `Asynchronous Processing=true` connection property:</span></span>

1. <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A?displayProperty=nameWithType>

2. <xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A?displayProperty=nameWithType>

3. <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A?displayProperty=nameWithType>

<span data-ttu-id="f2426-107">此功能保留在 .NET Framework 4.5 的 SqlClient 中。</span><span class="sxs-lookup"><span data-stu-id="f2426-107">This functionality remains in SqlClient in .NET Framework 4.5.</span></span>

> [!TIP]
> <span data-ttu-id="f2426-108">从 .NET Framework 4.5 开始，这些旧方法不再需要 `Asynchronous Processing=true` 在连接字符串中。</span><span class="sxs-lookup"><span data-stu-id="f2426-108">Beginning in the .NET Framework 4.5, these legacy methods no longer require `Asynchronous Processing=true` in the connection string.</span></span>

## <a name="asynchronous-programming-features-added-in-net-framework-45"></a><span data-ttu-id="f2426-109">.NET Framework 4.5 中添加的异步编程功能</span><span class="sxs-lookup"><span data-stu-id="f2426-109">Asynchronous Programming Features Added in .NET Framework 4.5</span></span>

<span data-ttu-id="f2426-110">该新的异步编程功能提供了一种用于使代码异步的简单技术。</span><span class="sxs-lookup"><span data-stu-id="f2426-110">The new asynchronous programming feature provides a simple technique to make code asynchronous.</span></span>

<span data-ttu-id="f2426-111">有关 .NET Framework 4.5 中引入的异步编程功能的详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="f2426-111">For more information about the asynchronous programming feature that was introduced in .NET Framework 4.5, see:</span></span>

- [<span data-ttu-id="f2426-112">C# 中的异步编程</span><span class="sxs-lookup"><span data-stu-id="f2426-112">Asynchronous programming in C#</span></span>](../../../csharp/async.md)

- [<span data-ttu-id="f2426-113">使用 Async 和 Await 的异步编程 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2426-113">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)

- [<span data-ttu-id="f2426-114">在 .NET 4.5 (第1部分中使用 SqlDataReader 的新异步方法) </span><span class="sxs-lookup"><span data-stu-id="f2426-114">Using SqlDataReader’s new async methods in .NET 4.5 (Part 1)</span></span>](/archive/blogs/adonet/using-sqldatareaders-new-async-methods-in-net-4-5)

- [<span data-ttu-id="f2426-115">在 .NET 4.5 (第2部分中使用 SqlDataReader 的新异步方法) </span><span class="sxs-lookup"><span data-stu-id="f2426-115">Using SqlDataReader’s new async methods in .NET 4.5 (Part 2)</span></span>](/archive/blogs/adonet/using-sqldatareaders-new-async-methods-in-net-4-5-part-2-examples)

<span data-ttu-id="f2426-116">当用户接口无响应或服务器无法扩展时，很可能需要使代码异步程度更高。</span><span class="sxs-lookup"><span data-stu-id="f2426-116">When your user interface is unresponsive or your server does not scale, it is likely that you need your code to be more asynchronous.</span></span> <span data-ttu-id="f2426-117">以前，编写异步代码涉及安装回调（也称为延续）来表示异步操作完成后发生的逻辑。</span><span class="sxs-lookup"><span data-stu-id="f2426-117">Writing asynchronous code has traditionally involved installing a callback (also called continuation) to express the logic that occurs after the asynchronous operation finishes.</span></span> <span data-ttu-id="f2426-118">这将增加异步代码结构的复杂性（与同步代码相比）。</span><span class="sxs-lookup"><span data-stu-id="f2426-118">This complicates the structure of asynchronous code as compared with synchronous code.</span></span>

<span data-ttu-id="f2426-119">现在，您可以调用异步方法而无需使用回调，也不需要跨多个方法或 lambda 表达式来拆分代码。</span><span class="sxs-lookup"><span data-stu-id="f2426-119">You can now call into asynchronous methods without using callbacks, and without splitting your code across multiple methods or lambda expressions.</span></span>

<span data-ttu-id="f2426-120">`async` 修饰符用于指定异步方法。</span><span class="sxs-lookup"><span data-stu-id="f2426-120">The `async` modifier specifies that a method is asynchronous.</span></span> <span data-ttu-id="f2426-121">调用 `async` 方法时，将返回一个任务。</span><span class="sxs-lookup"><span data-stu-id="f2426-121">When calling an `async` method, a task is returned.</span></span> <span data-ttu-id="f2426-122">将 `await` 运算符应用于任务后，当前方法会立即退出。</span><span class="sxs-lookup"><span data-stu-id="f2426-122">When the `await` operator is applied to a task, the current method exits immediately.</span></span> <span data-ttu-id="f2426-123">在该任务完成时，执行会在同一方法中恢复。</span><span class="sxs-lookup"><span data-stu-id="f2426-123">When the task finishes, execution resumes in the same method.</span></span>

> [!WARNING]
> <span data-ttu-id="f2426-124">如果应用程序还使用 `Context Connection` 连接字符串关键字，则不支持异步调用。</span><span class="sxs-lookup"><span data-stu-id="f2426-124">Asynchronous calls are not supported if an application also uses the `Context Connection` connection string keyword.</span></span>

<span data-ttu-id="f2426-125">调用 `async` 方法不会分配任何附加线程。</span><span class="sxs-lookup"><span data-stu-id="f2426-125">Calling an `async` method does not allocate any additional threads.</span></span> <span data-ttu-id="f2426-126">结束时，它可以简单地使用现有 I/O 完成线程。</span><span class="sxs-lookup"><span data-stu-id="f2426-126">It may use the existing I/O completion thread briefly at the end.</span></span>

<span data-ttu-id="f2426-127">在 .NET Framework 4.5 中添加了以下方法以支持异步编程：</span><span class="sxs-lookup"><span data-stu-id="f2426-127">The following methods were added in .NET Framework 4.5 to support asynchronous programming:</span></span>

- <xref:System.Data.Common.DbConnection.OpenAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.Common.DbCommand.ExecuteDbDataReaderAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.Common.DbCommand.ExecuteNonQueryAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.Common.DbCommand.ExecuteReaderAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.Common.DbCommand.ExecuteScalarAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.Common.DbDataReader.GetFieldValueAsync%2A>

- <xref:System.Data.Common.DbDataReader.IsDBNullAsync%2A>

- <xref:System.Data.Common.DbDataReader.NextResultAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.Common.DbDataReader.ReadAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.SqlClient.SqlConnection.OpenAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQueryAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.SqlClient.SqlCommand.ExecuteReaderAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.SqlClient.SqlCommand.ExecuteScalarAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.SqlClient.SqlCommand.ExecuteXmlReaderAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.SqlClient.SqlDataReader.NextResultAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.SqlClient.SqlDataReader.ReadAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.SqlClient.SqlBulkCopy.WriteToServerAsync%2A?displayProperty=nameWithType>

 <span data-ttu-id="f2426-128">添加了其他异步成员以支持 [SqlClient 流式处理支持](sqlclient-streaming-support.md)。</span><span class="sxs-lookup"><span data-stu-id="f2426-128">Other asynchronous members were added to support [SqlClient Streaming Support](sqlclient-streaming-support.md).</span></span>

> [!TIP]
> <span data-ttu-id="f2426-129">新的异步方法不会 `Asynchronous Processing=true` 在连接字符串中需要。</span><span class="sxs-lookup"><span data-stu-id="f2426-129">The new asynchronous methods don't require `Asynchronous Processing=true` in the connection string.</span></span>

### <a name="synchronous-to-asynchronous-connection-open"></a><span data-ttu-id="f2426-130">同步到异步连接打开</span><span class="sxs-lookup"><span data-stu-id="f2426-130">Synchronous to Asynchronous Connection Open</span></span>

<span data-ttu-id="f2426-131">您可以将现有应用程序升级以使用新的异步功能。</span><span class="sxs-lookup"><span data-stu-id="f2426-131">You can upgrade an existing application to use the new asynchronous feature.</span></span> <span data-ttu-id="f2426-132">例如，假设应用程序具有同步连接算法，并在每次 UI 线程连接到数据库时加以阻止，连接后，该应用程序将调用向刚登录的用户之外的其他用户发送信号的存储过程。</span><span class="sxs-lookup"><span data-stu-id="f2426-132">For example, assume an application has a synchronous connection algorithm and blocks the UI thread every time it connects to the database and, once connected, the application calls a stored procedure that signals other users of the one who just signed in.</span></span>

```csharp
using SqlConnection conn = new SqlConnection("…");
{
   conn.Open();
   using (SqlCommand cmd = new SqlCommand("StoredProcedure_Logon", conn))
   {
      cmd.ExecuteNonQuery();
   }
}
```

<span data-ttu-id="f2426-133">转换为使用新异步功能时，该程序看起来与下面类似：</span><span class="sxs-lookup"><span data-stu-id="f2426-133">When converted to use the new asynchronous functionality, the program would look like:</span></span>

```csharp
using System;
using System.Data.SqlClient;
using System.Threading.Tasks;

class A {

   static async Task<int> Method(SqlConnection conn, SqlCommand cmd) {
      await conn.OpenAsync();
      await cmd.ExecuteNonQueryAsync();
      return 1;
   }

   public static void Main() {
      using (SqlConnection conn = new SqlConnection("Data Source=(local); Initial Catalog=NorthWind; Integrated Security=SSPI")) {
         SqlCommand command = new SqlCommand("select top 2 * from orders", conn);

         int result = A.Method(conn, command).Result;

         SqlDataReader reader = command.ExecuteReader();
         while (reader.Read())
            Console.WriteLine(reader[0]);
      }
   }
}
```

### <a name="adding-the-new-asynchronous-feature-in-an-existing-application-mixing-old-and-new-patterns"></a><span data-ttu-id="f2426-134">在现有应用程序中添加新的异步功能（将旧模式与新模式混合）</span><span class="sxs-lookup"><span data-stu-id="f2426-134">Adding the New Asynchronous Feature in an Existing Application (Mixing Old and New Patterns)</span></span>

<span data-ttu-id="f2426-135">也可以在不更改现有异步逻辑的情况下添加新的异步功能 (SqlConnection::OpenAsync)。</span><span class="sxs-lookup"><span data-stu-id="f2426-135">It is also possible to add new asynchronous capability (SqlConnection::OpenAsync) without changing the existing asynchronous logic.</span></span> <span data-ttu-id="f2426-136">例如，如果应用程序当前使用：</span><span class="sxs-lookup"><span data-stu-id="f2426-136">For example, if an application currently uses:</span></span>

```csharp
AsyncCallback productList = new AsyncCallback(ProductList);
SqlConnection conn = new SqlConnection("…");
conn.Open();
SqlCommand cmd = new SqlCommand("SELECT * FROM [Current Product List]", conn);
IAsyncResult ia = cmd.BeginExecuteReader(productList, cmd);
```

<span data-ttu-id="f2426-137">您可以开始使用新异步模式而不会显著改变现有算法。</span><span class="sxs-lookup"><span data-stu-id="f2426-137">You can begin to use the new asynchronous pattern without substantially changing the existing algorithm.</span></span>

```csharp
using System;
using System.Data.SqlClient;
using System.Threading.Tasks;

class A {
   static void ProductList(IAsyncResult result) { }

   public static void Main() {
      // AsyncCallback productList = new AsyncCallback(ProductList);
      // SqlConnection conn = new SqlConnection("Data Source=(local); Initial Catalog=NorthWind; Integrated Security=SSPI");
      // conn.Open();
      // SqlCommand cmd = new SqlCommand("select top 2 * from orders", conn);
      // IAsyncResult ia = cmd.BeginExecuteReader(productList, cmd);

      AsyncCallback productList = new AsyncCallback(ProductList);
      SqlConnection conn = new SqlConnection("Data Source=(local); Initial Catalog=NorthWind; Integrated Security=SSPI");
      conn.OpenAsync().ContinueWith((task) => {
         SqlCommand cmd = new SqlCommand("select top 2 * from orders", conn);
         IAsyncResult ia = cmd.BeginExecuteReader(productList, cmd);
      }, TaskContinuationOptions.OnlyOnRanToCompletion);
   }
}
```

### <a name="using-the-base-provider-model-and-the-new-asynchronous-feature"></a><span data-ttu-id="f2426-138">使用基本提供程序模型和新的异步功能</span><span class="sxs-lookup"><span data-stu-id="f2426-138">Using the Base Provider Model and the New Asynchronous Feature</span></span>

<span data-ttu-id="f2426-139">您可能需要创建一个能够连接到不同数据库并执行查询的工具。</span><span class="sxs-lookup"><span data-stu-id="f2426-139">You may need to create a tool that is able to connect to different databases and execute queries.</span></span> <span data-ttu-id="f2426-140">您可以使用基本提供程序模型和新的异步功能。</span><span class="sxs-lookup"><span data-stu-id="f2426-140">You can use the base provider model and the new asynchronous feature.</span></span>

<span data-ttu-id="f2426-141">必须在服务器上启用 Microsoft 分布式事务处理控制器 (MSDTC) 以使用分布式事务。</span><span class="sxs-lookup"><span data-stu-id="f2426-141">The Microsoft Distributed Transaction Controller (MSDTC) must be enabled on the server to use distributed transactions.</span></span> <span data-ttu-id="f2426-142">有关如何启用 MSDTC 的信息，请参阅 [如何在 Web 服务器上启用 MSDTC](/previous-versions/commerce-server/dd327979(v=cs.90))。</span><span class="sxs-lookup"><span data-stu-id="f2426-142">For information on how to enable MSDTC, see [How to Enable MSDTC on a Web Server](/previous-versions/commerce-server/dd327979(v=cs.90)).</span></span>

```csharp
using System;
using System.Data.Common;
using System.Data.SqlClient;
using System.Threading.Tasks;

class A {
   static async Task PerformDBOperationsUsingProviderModel(string connectionString, string providerName) {
      DbProviderFactory factory = DbProviderFactories.GetFactory(providerName);
      using (DbConnection connection = factory.CreateConnection()) {
         connection.ConnectionString = connectionString;
         await connection.OpenAsync();

         DbCommand command = connection.CreateCommand();
         command.CommandText = "SELECT * FROM AUTHORS";

         using (DbDataReader reader = await command.ExecuteReaderAsync()) {
            while (await reader.ReadAsync()) {
               for (int i = 0; i < reader.FieldCount; i++) {
                  // Process each column as appropriate
                  object obj = await reader.GetFieldValueAsync<object>(i);
                  Console.WriteLine(obj);
               }
            }
         }
      }
   }

   public static void Main()
   {
       SqlConnectionStringBuilder builder = new SqlConnectionStringBuilder();
       // replace these with your own values
       builder.DataSource = "your_server";
       builder.InitialCatalog = "pubs";
       builder.IntegratedSecurity = true;
       string provider = "System.Data.SqlClient";

       Task task = PerformDBOperationsUsingProviderModel(builder.ConnectionString, provider);
       task.Wait();
   }
}
```

### <a name="using-sql-transactions-and-the-new-asynchronous-feature"></a><span data-ttu-id="f2426-143">使用 SQL 事务和新的异步功能</span><span class="sxs-lookup"><span data-stu-id="f2426-143">Using SQL Transactions and the New Asynchronous Feature</span></span>

```csharp
using System;
using System.Data.SqlClient;
using System.Threading.Tasks;

class Program {
   static void Main() {
      string connectionString =
          "Persist Security Info=False;Integrated Security=SSPI;database=Northwind;server=(local)";
      Task task = ExecuteSqlTransaction(connectionString);
      task.Wait();
   }

   static async Task ExecuteSqlTransaction(string connectionString) {
      using (SqlConnection connection = new SqlConnection(connectionString)) {
         await connection.OpenAsync();

         SqlCommand command = connection.CreateCommand();
         SqlTransaction transaction = null;

         // Start a local transaction.
         transaction = await Task.Run<SqlTransaction>(
             () => connection.BeginTransaction("SampleTransaction")
             );

         // Must assign both transaction object and connection
         // to Command object for a pending local transaction
         command.Connection = connection;
         command.Transaction = transaction;

         try {
            command.CommandText =
                "Insert into Region (RegionID, RegionDescription) VALUES (555, 'Description')";
            await command.ExecuteNonQueryAsync();

            command.CommandText =
                "Insert into Region (RegionID, RegionDescription) VALUES (556, 'Description')";
            await command.ExecuteNonQueryAsync();

            // Attempt to commit the transaction.
            await Task.Run(() => transaction.Commit());
            Console.WriteLine("Both records are written to database.");
         }
         catch (Exception ex) {
            Console.WriteLine("Commit Exception Type: {0}", ex.GetType());
            Console.WriteLine("  Message: {0}", ex.Message);

            // Attempt to roll back the transaction.
            try {
               transaction.Rollback();
            }
            catch (Exception ex2) {
               // This catch block will handle any errors that may have occurred
               // on the server that would cause the rollback to fail, such as
               // a closed connection.
               Console.WriteLine("Rollback Exception Type: {0}", ex2.GetType());
               Console.WriteLine("  Message: {0}", ex2.Message);
            }
         }
      }
   }
}
```

### <a name="using-sql-transactions-and-the-new-asynchronous-feature"></a><span data-ttu-id="f2426-144">使用 SQL 事务和新的异步功能</span><span class="sxs-lookup"><span data-stu-id="f2426-144">Using SQL Transactions and the New Asynchronous Feature</span></span>

<span data-ttu-id="f2426-145">在企业应用程序中，某些情况下，您可能需要添加分布式事务以启用多个数据库服务器之间的事务。</span><span class="sxs-lookup"><span data-stu-id="f2426-145">In an enterprise application, you may need to add distributed transactions in some scenarios, to enable transactions between multiple database servers.</span></span> <span data-ttu-id="f2426-146">你可以使用 System.Transactions 命名空间并登记分布式事务，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f2426-146">You can use the System.Transactions namespace and enlist a distributed transaction, as follows:</span></span>

```csharp
using System;
using System.Data.SqlClient;
using System.Threading.Tasks;
using System.Transactions;

class Program {
   public static void Main()
   {
       SqlConnectionStringBuilder builder = new SqlConnectionStringBuilder();
       // replace these with your own values
       builder.DataSource = "your_server";
       builder.InitialCatalog = "your_data_source";
       builder.IntegratedSecurity = true;

       Task task = ExecuteDistributedTransaction(builder.ConnectionString, builder.ConnectionString);
       task.Wait();
   }

   static async Task ExecuteDistributedTransaction(string connectionString1, string connectionString2) {
      using (SqlConnection connection1 = new SqlConnection(connectionString1))
      using (SqlConnection connection2 = new SqlConnection(connectionString2)) {
         using (CommittableTransaction transaction = new CommittableTransaction()) {
            await connection1.OpenAsync();
            connection1.EnlistTransaction(transaction);

            await connection2.OpenAsync();
            connection2.EnlistTransaction(transaction);

            try {
               SqlCommand command1 = connection1.CreateCommand();
               command1.CommandText = "Insert into RegionTable1 (RegionID, RegionDescription) VALUES (100, 'Description')";
               await command1.ExecuteNonQueryAsync();

               SqlCommand command2 = connection2.CreateCommand();
               command2.CommandText = "Insert into RegionTable2 (RegionID, RegionDescription) VALUES (100, 'Description')";
               await command2.ExecuteNonQueryAsync();

               transaction.Commit();
            }
            catch (Exception ex) {
               Console.WriteLine("Exception Type: {0}", ex.GetType());
               Console.WriteLine("  Message: {0}", ex.Message);

               try {
                  transaction.Rollback();
               }
               catch (Exception ex2) {
                  Console.WriteLine("Rollback Exception Type: {0}", ex2.GetType());
                  Console.WriteLine("  Message: {0}", ex2.Message);
               }
            }
         }
      }
   }
}
```

### <a name="cancelling-an-asynchronous-operation"></a><span data-ttu-id="f2426-147">取消异步操作</span><span class="sxs-lookup"><span data-stu-id="f2426-147">Cancelling an Asynchronous Operation</span></span>

<span data-ttu-id="f2426-148">可通过使用 <xref:System.Threading.CancellationToken> 来取消异步请求。</span><span class="sxs-lookup"><span data-stu-id="f2426-148">You can cancel an asynchronous request by using the <xref:System.Threading.CancellationToken>.</span></span>

```csharp
using System;
using System.Data.SqlClient;
using System.Threading;
using System.Threading.Tasks;

namespace Samples {
   class CancellationSample {
      public static void Main(string[] args) {
         CancellationTokenSource source = new CancellationTokenSource();
         source.CancelAfter(2000); // give up after 2 seconds
         try {
            Task result = CancellingAsynchronousOperations(source.Token);
            result.Wait();
         }
         catch (AggregateException exception) {
            if (exception.InnerException is SqlException) {
               Console.WriteLine("Operation canceled");
            }
            else {
               throw;
            }
         }
      }

      static async Task CancellingAsynchronousOperations(CancellationToken cancellationToken) {
         using (SqlConnection connection = new SqlConnection("Server=(local);Integrated Security=true")) {
            await connection.OpenAsync(cancellationToken);

            SqlCommand command = new SqlCommand("WAITFOR DELAY '00:10:00'", connection);
            await command.ExecuteNonQueryAsync(cancellationToken);
         }
      }
   }
}
```

### <a name="asynchronous-operations-with-sqlbulkcopy"></a><span data-ttu-id="f2426-149">使用 SqlBulkCopy 的异步操作</span><span class="sxs-lookup"><span data-stu-id="f2426-149">Asynchronous Operations with SqlBulkCopy</span></span>

<span data-ttu-id="f2426-150">异步功能也添加到了带有 <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType> 的 <xref:System.Data.SqlClient.SqlBulkCopy.WriteToServerAsync%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="f2426-150">Asynchronous capabilities were also added to <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType> with <xref:System.Data.SqlClient.SqlBulkCopy.WriteToServerAsync%2A?displayProperty=nameWithType>.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Data;
using System.Data.Odbc;
using System.Data.SqlClient;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;

namespace SqlBulkCopyAsyncCodeSample {
   class Program {
      static string selectStatement = "SELECT * FROM [pubs].[dbo].[titles]";
      static string createDestTableStatement =
          @"CREATE TABLE {0} (
            [title_id] [varchar](6) NOT NULL,
            [title] [varchar](80) NOT NULL,
            [type] [char](12) NOT NULL,
            [pub_id] [char](4) NULL,
            [price] [money] NULL,
            [advance] [money] NULL,
            [royalty] [int] NULL,
            [ytd_sales] [int] NULL,
            [notes] [varchar](200) NULL,
            [pubdate] [datetime] NOT NULL)";

      // Replace the connection string if needed, for instance to connect to SQL Express: @"Server=(local)\SQLEXPRESS;Database=Demo;Integrated Security=true"
      // static string connectionString = @"Server=(localdb)\V11.0;Database=Demo";
      static string connectionString = @"Server=(local);Database=Demo;Integrated Security=true";

      // static string odbcConnectionString = @"Driver={SQL Server};Server=(localdb)\V11.0;UID=oledb;Pwd=1Password!;Database=Demo";
      static string odbcConnectionString = @"Driver={SQL Server};Server=(local);Database=Demo;Integrated Security=true";

      // static string marsConnectionString = @"Server=(localdb)\V11.0;Database=Demo;MultipleActiveResultSets=true;";
      static string marsConnectionString = @"Server=(local);Database=Demo;MultipleActiveResultSets=true;Integrated Security=true";

      // Replace the Server name with your actual sql azure server name and User ID/Password
      static string azureConnectionString = @"Server=SqlAzure;User ID=myUserID;Password=myPassword;Database=Demo";

      static void Main(string[] args) {
         SynchronousSqlBulkCopy();
         AsyncSqlBulkCopy().Wait();
         MixSyncAsyncSqlBulkCopy().Wait();
         AsyncSqlBulkCopyNotifyAfter().Wait();
         AsyncSqlBulkCopyDataRows().Wait();
         // AsyncSqlBulkCopySqlServerToSqlAzure().Wait();
         // AsyncSqlBulkCopyCancel().Wait();
         AsyncSqlBulkCopyMARS().Wait();
      }

      // 3.1.1 Synchronous bulk copy in .NET 4.5
      private static void SynchronousSqlBulkCopy() {
         using (SqlConnection conn = new SqlConnection(connectionString)) {
            conn.Open();
            DataTable dt = new DataTable();
            using (SqlCommand cmd = new SqlCommand(selectStatement, conn)) {
               SqlDataAdapter adapter = new SqlDataAdapter(cmd);
               adapter.Fill(dt);

               string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";
               cmd.CommandText = string.Format(createDestTableStatement, temptable);
               cmd.ExecuteNonQuery();

               using (SqlBulkCopy bcp = new SqlBulkCopy(conn)) {
                  bcp.DestinationTableName = temptable;
                  bcp.WriteToServer(dt);
               }
            }
         }

      }

      // 3.1.2 Asynchronous bulk copy in .NET 4.5
      private static async Task AsyncSqlBulkCopy() {
         using (SqlConnection conn = new SqlConnection(connectionString)) {
            await conn.OpenAsync();
            DataTable dt = new DataTable();
            using (SqlCommand cmd = new SqlCommand(selectStatement, conn)) {
               SqlDataAdapter adapter = new SqlDataAdapter(cmd);
               adapter.Fill(dt);

               string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";
               cmd.CommandText = string.Format(createDestTableStatement, temptable);
               await cmd.ExecuteNonQueryAsync();

               using (SqlBulkCopy bcp = new SqlBulkCopy(conn)) {
                  bcp.DestinationTableName = temptable;
                  await bcp.WriteToServerAsync(dt);
               }
            }
         }
      }

      // 3.2 Add new Async.NET capabilities in an existing application (Mixing synchronous and asynchronous calls)
      private static async Task MixSyncAsyncSqlBulkCopy() {
         using (OdbcConnection odbcconn = new OdbcConnection(odbcConnectionString)) {
            odbcconn.Open();
            using (OdbcCommand odbccmd = new OdbcCommand(selectStatement, odbcconn)) {
               using (OdbcDataReader odbcreader = odbccmd.ExecuteReader()) {
                  using (SqlConnection conn = new SqlConnection(connectionString)) {
                     await conn.OpenAsync();
                     string temptable = "temptable";//"[#" + Guid.NewGuid().ToString("N") + "]";
                     SqlCommand createCmd = new SqlCommand(string.Format(createDestTableStatement, temptable), conn);
                     await createCmd.ExecuteNonQueryAsync();
                     using (SqlBulkCopy bcp = new SqlBulkCopy(conn)) {
                        bcp.DestinationTableName = temptable;
                        await bcp.WriteToServerAsync(odbcreader);
                     }
                  }
               }
            }
         }
      }

      // 3.3 Using the NotifyAfter property
      private static async Task AsyncSqlBulkCopyNotifyAfter() {
         using (SqlConnection conn = new SqlConnection(connectionString)) {
            await conn.OpenAsync();
            DataTable dt = new DataTable();
            using (SqlCommand cmd = new SqlCommand(selectStatement, conn)) {
               SqlDataAdapter adapter = new SqlDataAdapter(cmd);
               adapter.Fill(dt);

               string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";
               cmd.CommandText = string.Format(createDestTableStatement, temptable);
               await cmd.ExecuteNonQueryAsync();

               using (SqlBulkCopy bcp = new SqlBulkCopy(conn)) {
                  bcp.DestinationTableName = temptable;
                  bcp.NotifyAfter = 5;
                  bcp.SqlRowsCopied += new SqlRowsCopiedEventHandler(OnSqlRowsCopied);
                  await bcp.WriteToServerAsync(dt);
               }
            }
         }
      }

      private static void OnSqlRowsCopied(object sender, SqlRowsCopiedEventArgs e) {
         Console.WriteLine("Copied {0} so far...", e.RowsCopied);
      }

      // 3.4 Using the new SqlBulkCopy Async.NET capabilities with DataRow[]
      private static async Task AsyncSqlBulkCopyDataRows() {
         using (SqlConnection conn = new SqlConnection(connectionString)) {
            await conn.OpenAsync();
            DataTable dt = new DataTable();
            using (SqlCommand cmd = new SqlCommand(selectStatement, conn)) {
               SqlDataAdapter adapter = new SqlDataAdapter(cmd);
               adapter.Fill(dt);
               DataRow[] rows = dt.Select();

               string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";
               cmd.CommandText = string.Format(createDestTableStatement, temptable);
               await cmd.ExecuteNonQueryAsync();

               using (SqlBulkCopy bcp = new SqlBulkCopy(conn)) {
                  bcp.DestinationTableName = temptable;
                  await bcp.WriteToServerAsync(rows);
               }
            }
         }
      }

      // 3.5 Copying data from SQL Server to SQL Azure in .NET 4.5
      //private static async Task AsyncSqlBulkCopySqlServerToSqlAzure() {
      //   using (SqlConnection srcConn = new SqlConnection(connectionString))
      //   using (SqlConnection destConn = new SqlConnection(azureConnectionString)) {
      //      await srcConn.OpenAsync();
      //      await destConn.OpenAsync();
      //      using (SqlCommand srcCmd = new SqlCommand(selectStatement, srcConn)) {
      //         using (SqlDataReader reader = await srcCmd.ExecuteReaderAsync()) {
      //            string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";
      //            using (SqlCommand destCmd = new SqlCommand(string.Format(createDestTableStatement, temptable), destConn)) {
      //               await destCmd.ExecuteNonQueryAsync();
      //               using (SqlBulkCopy bcp = new SqlBulkCopy(destConn)) {
      //                  bcp.DestinationTableName = temptable;
      //                  await bcp.WriteToServerAsync(reader);
      //               }
      //            }
      //         }
      //      }
      //   }
      //}

      // 3.6 Cancelling an Asynchronous Operation to SQL Azure
      //private static async Task AsyncSqlBulkCopyCancel() {
      //   CancellationTokenSource cts = new CancellationTokenSource();
      //   using (SqlConnection srcConn = new SqlConnection(connectionString))
      //   using (SqlConnection destConn = new SqlConnection(azureConnectionString)) {
      //      await srcConn.OpenAsync(cts.Token);
      //      await destConn.OpenAsync(cts.Token);
      //      using (SqlCommand srcCmd = new SqlCommand(selectStatement, srcConn)) {
      //         using (SqlDataReader reader = await srcCmd.ExecuteReaderAsync(cts.Token)) {
      //            string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";
      //            using (SqlCommand destCmd = new SqlCommand(string.Format(createDestTableStatement, temptable), destConn)) {
      //               await destCmd.ExecuteNonQueryAsync(cts.Token);
      //               using (SqlBulkCopy bcp = new SqlBulkCopy(destConn)) {
      //                  bcp.DestinationTableName = temptable;
      //                  await bcp.WriteToServerAsync(reader, cts.Token);
      //                  //Cancel Async SqlBulCopy Operation after 200 ms
      //                  cts.CancelAfter(200);
      //               }
      //            }
      //         }
      //      }
      //   }
      //}

      // 3.7 Using Async.Net and MARS
      private static async Task AsyncSqlBulkCopyMARS() {
         using (SqlConnection marsConn = new SqlConnection(marsConnectionString)) {
            await marsConn.OpenAsync();

            SqlCommand titlesCmd = new SqlCommand("SELECT * FROM [pubs].[dbo].[titles]", marsConn);
            SqlCommand authorsCmd = new SqlCommand("SELECT * FROM [pubs].[dbo].[authors]", marsConn);
            //With MARS we can have multiple active results sets on the same connection
            using (SqlDataReader titlesReader = await titlesCmd.ExecuteReaderAsync())
            using (SqlDataReader authorsReader = await authorsCmd.ExecuteReaderAsync()) {
               await authorsReader.ReadAsync();

               string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";
               using (SqlConnection destConn = new SqlConnection(connectionString)) {
                  await destConn.OpenAsync();
                  using (SqlCommand destCmd = new SqlCommand(string.Format(createDestTableStatement, temptable), destConn)) {
                     await destCmd.ExecuteNonQueryAsync();
                     using (SqlBulkCopy bcp = new SqlBulkCopy(destConn)) {
                        bcp.DestinationTableName = temptable;
                        await bcp.WriteToServerAsync(titlesReader);
                     }
                  }
               }
            }
         }
      }
   }
}
```

## <a name="asynchronously-using-multiple-commands-with-mars"></a><span data-ttu-id="f2426-151">异步使用多个命令与 MARS</span><span class="sxs-lookup"><span data-stu-id="f2426-151">Asynchronously Using Multiple Commands with MARS</span></span>

<span data-ttu-id="f2426-152">该示例将打开与 AdventureWorks\*\*\*\* 数据库的单个连接。</span><span class="sxs-lookup"><span data-stu-id="f2426-152">The example opens a single connection to the **AdventureWorks** database.</span></span> <span data-ttu-id="f2426-153">使用 <xref:System.Data.SqlClient.SqlCommand> 对象时，将创建一个 <xref:System.Data.SqlClient.SqlDataReader>。</span><span class="sxs-lookup"><span data-stu-id="f2426-153">Using a <xref:System.Data.SqlClient.SqlCommand> object, a <xref:System.Data.SqlClient.SqlDataReader> is created.</span></span> <span data-ttu-id="f2426-154">使用阅读器时，打开第二个 <xref:System.Data.SqlClient.SqlDataReader>，使用第一个 <xref:System.Data.SqlClient.SqlDataReader> 的数据作为第二个阅读器的 WHERE 子句的输入。</span><span class="sxs-lookup"><span data-stu-id="f2426-154">As the reader is used, a second <xref:System.Data.SqlClient.SqlDataReader> is opened, using data from the first <xref:System.Data.SqlClient.SqlDataReader> as input to the WHERE clause for the second reader.</span></span>

> [!NOTE]
> <span data-ttu-id="f2426-155">下面的示例使用随 SQL Server 提供的 AdventureWorks 示例数据库\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2426-155">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="f2426-156">示例代码中提供的连接字符串假定数据库已安装并且在本地计算机上可用。</span><span class="sxs-lookup"><span data-stu-id="f2426-156">The connection string provided in the sample code assumes that the database is installed and available on the local computer.</span></span> <span data-ttu-id="f2426-157">根据环境需要修改连接字符串。</span><span class="sxs-lookup"><span data-stu-id="f2426-157">Modify the connection string as necessary for your environment.</span></span>

```csharp
using System;
using System.Data;
using System.Data.SqlClient;
using System.Threading.Tasks;

class Class1 {
   static void Main() {
      Task task = MultipleCommands();
      task.Wait();
   }

   static async Task MultipleCommands() {
      // By default, MARS is disabled when connecting to a MARS-enabled.
      // It must be enabled in the connection string.
      string connectionString = GetConnectionString();

      int vendorID;
      SqlDataReader productReader = null;
      string vendorSQL =
        "SELECT VendorId, Name FROM Purchasing.Vendor";
      string productSQL =
        "SELECT Production.Product.Name FROM Production.Product " +
        "INNER JOIN Purchasing.ProductVendor " +
        "ON Production.Product.ProductID = " +
        "Purchasing.ProductVendor.ProductID " +
        "WHERE Purchasing.ProductVendor.VendorID = @VendorId";

      using (SqlConnection awConnection =
        new SqlConnection(connectionString)) {
         SqlCommand vendorCmd = new SqlCommand(vendorSQL, awConnection);
         SqlCommand productCmd =
           new SqlCommand(productSQL, awConnection);

         productCmd.Parameters.Add("@VendorId", SqlDbType.Int);

         await awConnection.OpenAsync();
         using (SqlDataReader vendorReader = await vendorCmd.ExecuteReaderAsync()) {
            while (await vendorReader.ReadAsync()) {
               Console.WriteLine(vendorReader["Name"]);

               vendorID = (int)vendorReader["VendorId"];

               productCmd.Parameters["@VendorId"].Value = vendorID;
               // The following line of code requires a MARS-enabled connection.
               productReader = await productCmd.ExecuteReaderAsync();
               using (productReader) {
                  while (await productReader.ReadAsync()) {
                     Console.WriteLine("  " +
                       productReader["Name"].ToString());
                  }
               }
            }
         }
      }
   }

   private static string GetConnectionString() {
      // To avoid storing the connection string in your code, you can retrieve it from a configuration file.
      return "Data Source=(local);Integrated Security=SSPI;Initial Catalog=AdventureWorks;MultipleActiveResultSets=True";
   }
}
```

## <a name="asynchronously-reading-and-updating-data-with-mars"></a><span data-ttu-id="f2426-158">使用 MARS 异步读取和更新数据</span><span class="sxs-lookup"><span data-stu-id="f2426-158">Asynchronously Reading and Updating Data with MARS</span></span>

<span data-ttu-id="f2426-159">MARS 允许将连接用于读取操作和数据操作语言 (DML) 操作，其中有多个待处理操作。</span><span class="sxs-lookup"><span data-stu-id="f2426-159">MARS allows a connection to be used for both read operations and data manipulation language (DML) operations with more than one pending operation.</span></span> <span data-ttu-id="f2426-160">此功能使应用程序无需处理连接繁忙错误。</span><span class="sxs-lookup"><span data-stu-id="f2426-160">This feature eliminates the need for an application to deal with connection-busy errors.</span></span> <span data-ttu-id="f2426-161">此外，MARS 可以替换服务器端游标的用户，这通常会消耗更多资源。</span><span class="sxs-lookup"><span data-stu-id="f2426-161">In addition, MARS can replace the user of server-side cursors, which generally consume more resources.</span></span> <span data-ttu-id="f2426-162">最后，因为可以在单个连接上执行多个操作，所以，这些操作可以共享相同的事务上下文，不需要使用 sp_getbindtoken 和 sp_bindsession 系统存储过程\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2426-162">Finally, because multiple operations can operate on a single connection, they can share the same transaction context, eliminating the need to use **sp_getbindtoken** and **sp_bindsession** system stored procedures.</span></span>

<span data-ttu-id="f2426-163">下面的控制台应用程序演示如何使用两个包含三个 <xref:System.Data.SqlClient.SqlCommand> 对象的 <xref:System.Data.SqlClient.SqlDataReader> 对象和一个启用了 MARS 的 <xref:System.Data.SqlClient.SqlConnection> 对象。</span><span class="sxs-lookup"><span data-stu-id="f2426-163">The following Console application demonstrates how to use two <xref:System.Data.SqlClient.SqlDataReader> objects with three <xref:System.Data.SqlClient.SqlCommand> objects and a single <xref:System.Data.SqlClient.SqlConnection> object with MARS enabled.</span></span> <span data-ttu-id="f2426-164">第一个命令对象检索信用评级为 5 的供应商列表。</span><span class="sxs-lookup"><span data-stu-id="f2426-164">The first command object retrieves a list of vendors whose credit rating is 5.</span></span> <span data-ttu-id="f2426-165">第二个命令对象使用 <xref:System.Data.SqlClient.SqlDataReader> 提供的供应商 ID 为第二个 <xref:System.Data.SqlClient.SqlDataReader> 加载特定供应商的所有产品。</span><span class="sxs-lookup"><span data-stu-id="f2426-165">The second command object uses the vendor ID provided from a <xref:System.Data.SqlClient.SqlDataReader> to load the second <xref:System.Data.SqlClient.SqlDataReader> with all of the products for the particular vendor.</span></span> <span data-ttu-id="f2426-166">每个产品记录由第二个 <xref:System.Data.SqlClient.SqlDataReader> 访问。</span><span class="sxs-lookup"><span data-stu-id="f2426-166">Each product record is visited by the second <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="f2426-167">通过执行计算来确定新的 OnOrderQty\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2426-167">A calculation is performed to determine what the new **OnOrderQty** should be.</span></span> <span data-ttu-id="f2426-168">然后，通过第三个命令对象来使用新值更新 ProductVendor 表\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2426-168">The third command object is then used to update the **ProductVendor** table with the new value.</span></span> <span data-ttu-id="f2426-169">整个过程发生在单个事务中，该事务在结束时回滚。</span><span class="sxs-lookup"><span data-stu-id="f2426-169">This entire process takes place within a single transaction, which is rolled back at the end.</span></span>

> [!NOTE]
> <span data-ttu-id="f2426-170">下面的示例使用随 SQL Server 提供的 AdventureWorks 示例数据库\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2426-170">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="f2426-171">示例代码中提供的连接字符串假定数据库已安装并且在本地计算机上可用。</span><span class="sxs-lookup"><span data-stu-id="f2426-171">The connection string provided in the sample code assumes that the database is installed and available on the local computer.</span></span> <span data-ttu-id="f2426-172">根据环境需要修改连接字符串。</span><span class="sxs-lookup"><span data-stu-id="f2426-172">Modify the connection string as necessary for your environment.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Text;
using System.Data;
using System.Data.SqlClient;
using System.Threading.Tasks;

class Program {
   static void Main() {
      Task task = ReadingAndUpdatingData();
      task.Wait();
   }

   static async Task ReadingAndUpdatingData() {
      // By default, MARS is disabled when connecting to a MARS-enabled host.
      // It must be enabled in the connection string.
      string connectionString = GetConnectionString();

      SqlTransaction updateTx = null;
      SqlCommand vendorCmd = null;
      SqlCommand prodVendCmd = null;
      SqlCommand updateCmd = null;

      SqlDataReader prodVendReader = null;

      int vendorID = 0;
      int productID = 0;
      int minOrderQty = 0;
      int maxOrderQty = 0;
      int onOrderQty = 0;
      int recordsUpdated = 0;
      int totalRecordsUpdated = 0;

      string vendorSQL =
          "SELECT VendorID, Name FROM Purchasing.Vendor " +
          "WHERE CreditRating = 5";
      string prodVendSQL =
          "SELECT ProductID, MaxOrderQty, MinOrderQty, OnOrderQty " +
          "FROM Purchasing.ProductVendor " +
          "WHERE VendorID = @VendorID";
      string updateSQL =
          "UPDATE Purchasing.ProductVendor " +
          "SET OnOrderQty = @OrderQty " +
          "WHERE ProductID = @ProductID AND VendorID = @VendorID";

      using (SqlConnection awConnection =
        new SqlConnection(connectionString)) {
         await awConnection.OpenAsync();
         updateTx = await Task.Run(() => awConnection.BeginTransaction());

         vendorCmd = new SqlCommand(vendorSQL, awConnection);
         vendorCmd.Transaction = updateTx;

         prodVendCmd = new SqlCommand(prodVendSQL, awConnection);
         prodVendCmd.Transaction = updateTx;
         prodVendCmd.Parameters.Add("@VendorId", SqlDbType.Int);

         updateCmd = new SqlCommand(updateSQL, awConnection);
         updateCmd.Transaction = updateTx;
         updateCmd.Parameters.Add("@OrderQty", SqlDbType.Int);
         updateCmd.Parameters.Add("@ProductID", SqlDbType.Int);
         updateCmd.Parameters.Add("@VendorID", SqlDbType.Int);

         using (SqlDataReader vendorReader = await vendorCmd.ExecuteReaderAsync()) {
            while (await vendorReader.ReadAsync()) {
               Console.WriteLine(vendorReader["Name"]);

               vendorID = (int)vendorReader["VendorID"];
               prodVendCmd.Parameters["@VendorID"].Value = vendorID;
               prodVendReader = await prodVendCmd.ExecuteReaderAsync();

               using (prodVendReader) {
                  while (await prodVendReader.ReadAsync()) {
                     productID = (int)prodVendReader["ProductID"];

                     if (prodVendReader["OnOrderQty"] == DBNull.Value) {
                        minOrderQty = (int)prodVendReader["MinOrderQty"];
                        onOrderQty = minOrderQty;
                     }
                     else {
                        maxOrderQty = (int)prodVendReader["MaxOrderQty"];
                        onOrderQty = (int)(maxOrderQty / 2);
                     }

                     updateCmd.Parameters["@OrderQty"].Value = onOrderQty;
                     updateCmd.Parameters["@ProductID"].Value = productID;
                     updateCmd.Parameters["@VendorID"].Value = vendorID;

                     recordsUpdated = await updateCmd.ExecuteNonQueryAsync();
                     totalRecordsUpdated += recordsUpdated;
                  }
               }
            }
         }
         Console.WriteLine("Total Records Updated: ", totalRecordsUpdated.ToString());
         await Task.Run(() => updateTx.Rollback());
         Console.WriteLine("Transaction Rolled Back");
      }
   }

   private static string GetConnectionString() {
      // To avoid storing the connection string in your code, you can retrieve it from a configuration file.
      return "Data Source=(local);Integrated Security=SSPI;Initial Catalog=AdventureWorks;MultipleActiveResultSets=True";
   }
}
```

## <a name="see-also"></a><span data-ttu-id="f2426-173">请参阅</span><span class="sxs-lookup"><span data-stu-id="f2426-173">See also</span></span>

- [<span data-ttu-id="f2426-174">在 ADO.NET 中检索和修改数据</span><span class="sxs-lookup"><span data-stu-id="f2426-174">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)

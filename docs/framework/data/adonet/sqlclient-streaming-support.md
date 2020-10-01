---
title: SqlClient 流支持
ms.date: 03/30/2017
ms.assetid: c449365b-470b-4edb-9d61-8353149f5531
ms.openlocfilehash: a396e3e172c63b0b71b085d4694184c42cc42f3e
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609240"
---
# <a name="sqlclient-streaming-support"></a><span data-ttu-id="cb867-102">SqlClient 流支持</span><span class="sxs-lookup"><span data-stu-id="cb867-102">SqlClient Streaming Support</span></span>

<span data-ttu-id="cb867-103">.NET Framework 4.5) 中 SQL Server 和应用程序之间的流支持 (在服务器 (文档、图像和媒体文件) 支持非结构化数据。</span><span class="sxs-lookup"><span data-stu-id="cb867-103">Streaming support between SQL Server and an application (new in .NET Framework 4.5) supports unstructured data on the server (documents, images, and media files).</span></span> <span data-ttu-id="cb867-104">SQL Server 数据库可以将二进制大型对象存储 (Blob) ，但检索 BLOB 可能会占用大量内存。</span><span class="sxs-lookup"><span data-stu-id="cb867-104">A SQL Server database can store binary large objects (BLOBs), but retrieving BLOBS can use a lot of memory.</span></span>

<span data-ttu-id="cb867-105">与 SQL Server 的流支持简化了写入流式处理数据的应用程序，而无需将数据完全加载到内存中，从而减少了内存溢出异常。</span><span class="sxs-lookup"><span data-stu-id="cb867-105">Streaming support to and from SQL Server simplifies writing applications that stream data, without having to fully load the data into memory, resulting in fewer memory overflow exceptions.</span></span>

<span data-ttu-id="cb867-106">通过流支持，中间层应用程序还可以更好地扩展，尤其是在业务对象连接到 SQL Azure 以发送、检索和操作大型 BLOB 的方案中。</span><span class="sxs-lookup"><span data-stu-id="cb867-106">Streaming support will also enable middle-tier applications to scale better, especially in scenarios where business objects connect to SQL Azure in order to send, retrieve, and manipulate large BLOBs.</span></span>

> [!WARNING]
> <span data-ttu-id="cb867-107">如果应用程序还使用 `Context Connection` 连接字符串关键字，则不支持异步调用。</span><span class="sxs-lookup"><span data-stu-id="cb867-107">Asynchronous calls are not supported if an application also uses the `Context Connection` connection string keyword.</span></span>
>
> <span data-ttu-id="cb867-108">为支持流处理而添加的成员用于从查询中检索数据，并将参数传递给查询和存储过程。</span><span class="sxs-lookup"><span data-stu-id="cb867-108">The members added to support streaming are used to retrieve data from queries and to pass parameters to queries and stored procedures.</span></span> <span data-ttu-id="cb867-109">流式处理功能可解决基本的 OLTP 和数据迁移方案，适用于本地和非本地数据迁移环境。</span><span class="sxs-lookup"><span data-stu-id="cb867-109">The streaming feature addresses basic OLTP and data migration scenarios and is applicable to on-premises and off-premises data migrations environments.</span></span>

## <a name="streaming-support-from-sql-server"></a><span data-ttu-id="cb867-110">SQL Server 中的流式处理支持</span><span class="sxs-lookup"><span data-stu-id="cb867-110">Streaming Support from SQL Server</span></span>

<span data-ttu-id="cb867-111">SQL Server 中的流支持在和类中引入了新功能 <xref:System.Data.Common.DbDataReader> <xref:System.Data.SqlClient.SqlDataReader> ，以便获取 <xref:System.IO.Stream> 、 <xref:System.Xml.XmlReader> 、和 <xref:System.IO.TextReader> 对象并对其做出反应。</span><span class="sxs-lookup"><span data-stu-id="cb867-111">Streaming support from SQL Server introduces new functionality in the <xref:System.Data.Common.DbDataReader> and in the <xref:System.Data.SqlClient.SqlDataReader> classes in order to get <xref:System.IO.Stream>, <xref:System.Xml.XmlReader>, and <xref:System.IO.TextReader> objects and react to them.</span></span> <span data-ttu-id="cb867-112">这些类用于检索查询中的数据。</span><span class="sxs-lookup"><span data-stu-id="cb867-112">These classes are used to retrieve data from queries.</span></span> <span data-ttu-id="cb867-113">因此，SQL Server 中的流支持可解决 OLTP 方案，并适用于本地和非本地环境。</span><span class="sxs-lookup"><span data-stu-id="cb867-113">As a result, Streaming support from SQL Server addresses OLTP scenarios and applies to on-premises and off-premises environments.</span></span>

<span data-ttu-id="cb867-114">将以下成员添加到 <xref:System.Data.SqlClient.SqlDataReader> 以启用从 SQL Server 的流支持：</span><span class="sxs-lookup"><span data-stu-id="cb867-114">The following members were added to <xref:System.Data.SqlClient.SqlDataReader> to enable streaming support from SQL Server:</span></span>

1. <xref:System.Data.SqlClient.SqlDataReader.IsDBNullAsync%2A>

2. <xref:System.Data.SqlClient.SqlDataReader.GetFieldValue%2A?displayProperty=nameWithType>

3. <xref:System.Data.SqlClient.SqlDataReader.GetFieldValueAsync%2A>

4. <xref:System.Data.SqlClient.SqlDataReader.GetStream%2A>

5. <xref:System.Data.SqlClient.SqlDataReader.GetTextReader%2A>

6. <xref:System.Data.SqlClient.SqlDataReader.GetXmlReader%2A>

<span data-ttu-id="cb867-115">将以下成员添加到 <xref:System.Data.Common.DbDataReader> 以启用从 SQL Server 的流支持：</span><span class="sxs-lookup"><span data-stu-id="cb867-115">The following members were added to <xref:System.Data.Common.DbDataReader> to enable streaming support from SQL Server:</span></span>

1. <xref:System.Data.Common.DbDataReader.GetFieldValue%2A>

2. <xref:System.Data.Common.DbDataReader.GetStream%2A>

3. <xref:System.Data.Common.DbDataReader.GetTextReader%2A>

## <a name="streaming-support-to-sql-server"></a><span data-ttu-id="cb867-116">SQL Server 的流式处理支持</span><span class="sxs-lookup"><span data-stu-id="cb867-116">Streaming Support to SQL Server</span></span>

<span data-ttu-id="cb867-117">SQL Server 的流式处理支持会引入类中的新功能 <xref:System.Data.SqlClient.SqlParameter> ，使其可以接受和响应 <xref:System.Xml.XmlReader> 、 <xref:System.IO.Stream> 和 <xref:System.IO.TextReader> 对象。</span><span class="sxs-lookup"><span data-stu-id="cb867-117">Streaming support to SQL Server introduces new functionality in the <xref:System.Data.SqlClient.SqlParameter> class so it can accept and react to <xref:System.Xml.XmlReader>, <xref:System.IO.Stream>, and <xref:System.IO.TextReader> objects.</span></span> <span data-ttu-id="cb867-118"><xref:System.Data.SqlClient.SqlParameter> 用于将参数传递给查询和存储过程。</span><span class="sxs-lookup"><span data-stu-id="cb867-118"><xref:System.Data.SqlClient.SqlParameter> is used to pass parameters to queries and stored procedures.</span></span>

<span data-ttu-id="cb867-119">释放 <xref:System.Data.SqlClient.SqlCommand> 对象或调用 <xref:System.Data.SqlClient.SqlCommand.Cancel%2A> 必须取消任何流操作。</span><span class="sxs-lookup"><span data-stu-id="cb867-119">Disposing a <xref:System.Data.SqlClient.SqlCommand> object or calling <xref:System.Data.SqlClient.SqlCommand.Cancel%2A> must cancel any streaming operation.</span></span> <span data-ttu-id="cb867-120">如果应用程序发送 <xref:System.Threading.CancellationToken>，则不保证取消。</span><span class="sxs-lookup"><span data-stu-id="cb867-120">If an application sends <xref:System.Threading.CancellationToken>, cancellation is not guaranteed.</span></span>

<span data-ttu-id="cb867-121">以下 <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> 类型将接受 <xref:System.Data.SqlClient.SqlParameter.Value%2A> 的 <xref:System.IO.Stream>：</span><span class="sxs-lookup"><span data-stu-id="cb867-121">The following <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> types will accept a <xref:System.Data.SqlClient.SqlParameter.Value%2A> of <xref:System.IO.Stream>:</span></span>

- <span data-ttu-id="cb867-122">**二进制**</span><span class="sxs-lookup"><span data-stu-id="cb867-122">**Binary**</span></span>

- <span data-ttu-id="cb867-123">**VarBinary**</span><span class="sxs-lookup"><span data-stu-id="cb867-123">**VarBinary**</span></span>

<span data-ttu-id="cb867-124">以下 <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> 类型将接受 <xref:System.Data.SqlClient.SqlParameter.Value%2A> 的 <xref:System.IO.TextReader>：</span><span class="sxs-lookup"><span data-stu-id="cb867-124">The following <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> types will accept a <xref:System.Data.SqlClient.SqlParameter.Value%2A> of <xref:System.IO.TextReader>:</span></span>

- <span data-ttu-id="cb867-125">**Char**</span><span class="sxs-lookup"><span data-stu-id="cb867-125">**Char**</span></span>

- <span data-ttu-id="cb867-126">**NChar**</span><span class="sxs-lookup"><span data-stu-id="cb867-126">**NChar**</span></span>

- <span data-ttu-id="cb867-127">**NVarChar**</span><span class="sxs-lookup"><span data-stu-id="cb867-127">**NVarChar**</span></span>

- <span data-ttu-id="cb867-128">**Xml**</span><span class="sxs-lookup"><span data-stu-id="cb867-128">**Xml**</span></span>

<span data-ttu-id="cb867-129">**Xml** <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> 类型将接受 <xref:System.Data.SqlClient.SqlParameter.Value%2A> 的 <xref:System.Xml.XmlReader> 。</span><span class="sxs-lookup"><span data-stu-id="cb867-129">The **Xml**<xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> type will accept a <xref:System.Data.SqlClient.SqlParameter.Value%2A> of <xref:System.Xml.XmlReader>.</span></span>

<span data-ttu-id="cb867-130"><xref:System.Data.SqlClient.SqlParameter.SqlValue%2A> 可接受类型 <xref:System.Xml.XmlReader>、<xref:System.IO.TextReader> 和 <xref:System.IO.Stream> 的值。</span><span class="sxs-lookup"><span data-stu-id="cb867-130"><xref:System.Data.SqlClient.SqlParameter.SqlValue%2A> can accept values of type <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader>, and <xref:System.IO.Stream>.</span></span>

<span data-ttu-id="cb867-131"><xref:System.Xml.XmlReader>、<xref:System.IO.TextReader> 和 <xref:System.IO.Stream> 对象将转移到由 <xref:System.Data.SqlClient.SqlParameter.Size%2A> 定义的值。</span><span class="sxs-lookup"><span data-stu-id="cb867-131">The <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader>, and <xref:System.IO.Stream> object will be transferred up to the value defined by the <xref:System.Data.SqlClient.SqlParameter.Size%2A>.</span></span>

## <a name="sample----streaming-from-sql-server"></a><span data-ttu-id="cb867-132">示例-从 SQL Server 流式处理</span><span class="sxs-lookup"><span data-stu-id="cb867-132">Sample -- Streaming from SQL Server</span></span>

<span data-ttu-id="cb867-133">使用以下 Transact-sql 创建示例数据库：</span><span class="sxs-lookup"><span data-stu-id="cb867-133">Use the following Transact-SQL to create the sample database:</span></span>

```sql
CREATE DATABASE [Demo]
GO
USE [Demo]
GO
CREATE TABLE [Streams] (
[id] INT PRIMARY KEY IDENTITY(1, 1),
[textdata] NVARCHAR(MAX),
[bindata] VARBINARY(MAX),
[xmldata] XML)
GO
INSERT INTO [Streams] (textdata, bindata, xmldata) VALUES (N'This is a test', 0x48656C6C6F, N'<test>value</test>')
INSERT INTO [Streams] (textdata, bindata, xmldata) VALUES (N'Hello, World!', 0x54657374696E67, N'<test>value2</test>')
INSERT INTO [Streams] (textdata, bindata, xmldata) VALUES (N'Another row', 0x666F6F626172, N'<fff>bbb</fff><fff>bbc</fff>')
GO
```

<span data-ttu-id="cb867-134">该示例说明如何执行以下功能：</span><span class="sxs-lookup"><span data-stu-id="cb867-134">The sample shows how to do the following:</span></span>

- <span data-ttu-id="cb867-135">通过提供用于检索大型文件的异步方法来避免阻止用户接口线程。</span><span class="sxs-lookup"><span data-stu-id="cb867-135">Avoid blocking a user-interface thread by providing an asynchronous way to retrieve large files.</span></span>

- <span data-ttu-id="cb867-136">从 .NET Framework 4.5 中的 SQL Server 传输大型文本文件。</span><span class="sxs-lookup"><span data-stu-id="cb867-136">Transfer a large text file from SQL Server in .NET Framework 4.5.</span></span>

- <span data-ttu-id="cb867-137">从 .NET Framework 4.5 中的 SQL Server 传输大型 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="cb867-137">Transfer a large XML file from SQL Server in .NET Framework 4.5.</span></span>

- <span data-ttu-id="cb867-138">从 SQL Server 检索数据。</span><span class="sxs-lookup"><span data-stu-id="cb867-138">Retrieve data from SQL Server.</span></span>

- <span data-ttu-id="cb867-139">将大型文件 (Blob) 从一个 SQL Server 数据库传输到另一个数据库，而不会耗尽内存。</span><span class="sxs-lookup"><span data-stu-id="cb867-139">Transfer large files (BLOBs) from one SQL Server database to another without running out of memory.</span></span>

```csharp
using System;
using System.Data;
using System.Data.SqlClient;
using System.IO;
using System.Threading.Tasks;
using System.Xml;

namespace StreamingFromServer {
   class Program {
      // Replace the connection string if needed, for instance to connect to SQL Express: @"Server=(local)\SQLEXPRESS;Database=Demo;Integrated Security=true"
      private const string connectionString = @"Server=(localdb)\V11.0;Database=Demo";

      static void Main(string[] args) {
         CopyBinaryValueToFile().Wait();
         PrintTextValues().Wait();
         PrintXmlValues().Wait();
         PrintXmlValuesViaNVarChar().Wait();

         Console.WriteLine("Done");
      }

      // Application retrieving a large BLOB from SQL Server in .NET 4.5 using the new asynchronous capability
      private static async Task CopyBinaryValueToFile() {
         string filePath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), "binarydata.bin");

         using (SqlConnection connection = new SqlConnection(connectionString)) {
            await connection.OpenAsync();
            using (SqlCommand command = new SqlCommand("SELECT [bindata] FROM [Streams] WHERE [id]=@id", connection)) {
               command.Parameters.AddWithValue("id", 1);

               // The reader needs to be executed with the SequentialAccess behavior to enable network streaming
               // Otherwise ReadAsync will buffer the entire BLOB into memory which can cause scalability issues or even OutOfMemoryExceptions
               using (SqlDataReader reader = await command.ExecuteReaderAsync(CommandBehavior.SequentialAccess)) {
                  if (await reader.ReadAsync()) {
                     if (!(await reader.IsDBNullAsync(0))) {
                        using (FileStream file = new FileStream(filePath, FileMode.Create, FileAccess.Write)) {
                           using (Stream data = reader.GetStream(0)) {

                              // Asynchronously copy the stream from the server to the file we just created
                              await data.CopyToAsync(file);
                           }
                        }
                     }
                  }
               }
            }
         }
      }

      // Application transferring a large Text File from SQL Server in .NET 4.5
      private static async Task PrintTextValues() {
         using (SqlConnection connection = new SqlConnection(connectionString)) {
            await connection.OpenAsync();
            using (SqlCommand command = new SqlCommand("SELECT [id], [textdata] FROM [Streams]", connection)) {

               // The reader needs to be executed with the SequentialAccess behavior to enable network streaming
               // Otherwise ReadAsync will buffer the entire text document into memory which can cause scalability issues or even OutOfMemoryExceptions
               using (SqlDataReader reader = await command.ExecuteReaderAsync(CommandBehavior.SequentialAccess)) {
                  while (await reader.ReadAsync()) {
                     Console.Write("{0}: ", reader.GetInt32(0));

                     if (await reader.IsDBNullAsync(1)) {
                        Console.Write("(NULL)");
                     }
                     else {
                        char[] buffer = new char[4096];
                        int charsRead = 0;
                        using (TextReader data = reader.GetTextReader(1)) {
                           do {
                              // Grab each chunk of text and write it to the console
                              // If you are writing to a TextWriter you should use WriteAsync or WriteLineAsync
                              charsRead = await data.ReadAsync(buffer, 0, buffer.Length);
                              Console.Write(buffer, 0, charsRead);
                           } while (charsRead > 0);
                        }
                     }

                     Console.WriteLine();
                  }
               }
            }
         }
      }

      // Application transferring a large Xml Document from SQL Server in .NET 4.5
      private static async Task PrintXmlValues() {
         using (SqlConnection connection = new SqlConnection(connectionString)) {
            await connection.OpenAsync();
            using (SqlCommand command = new SqlCommand("SELECT [id], [xmldata] FROM [Streams]", connection)) {

               // The reader needs to be executed with the SequentialAccess behavior to enable network streaming
               // Otherwise ReadAsync will buffer the entire Xml Document into memory which can cause scalability issues or even OutOfMemoryExceptions
               using (SqlDataReader reader = await command.ExecuteReaderAsync(CommandBehavior.SequentialAccess)) {
                  while (await reader.ReadAsync()) {
                     Console.WriteLine("{0}: ", reader.GetInt32(0));

                     if (await reader.IsDBNullAsync(1)) {
                        Console.WriteLine("\t(NULL)");
                     }
                     else {
                        using (XmlReader xmlReader = reader.GetXmlReader(1)) {
                           int depth = 1;
                           // NOTE: The XmlReader returned by GetXmlReader does NOT support async operations
                           // See the example below (PrintXmlValuesViaNVarChar) for how to get an XmlReader with asynchronous capabilities
                           while (xmlReader.Read()) {
                              switch (xmlReader.NodeType) {
                                 case XmlNodeType.Element:
                                    Console.WriteLine("{0}<{1}>", new string('\t', depth), xmlReader.Name);
                                    depth++;
                                    break;
                                 case XmlNodeType.Text:
                                    Console.WriteLine("{0}{1}", new string('\t', depth), xmlReader.Value);
                                    break;
                                 case XmlNodeType.EndElement:
                                    depth--;
                                    Console.WriteLine("{0}</{1}>", new string('\t', depth), xmlReader.Name);
                                    break;
                              }
                           }
                        }
                     }
                  }
               }
            }
         }
      }

      // Application transferring a large Xml Document from SQL Server in .NET 4.5
      // This goes via NVarChar and TextReader to enable asynchronous reading
      private static async Task PrintXmlValuesViaNVarChar() {
         XmlReaderSettings xmlSettings = new XmlReaderSettings() {
            // Async must be explicitly enabled in the XmlReaderSettings otherwise the XmlReader will throw exceptions when async methods are called
            Async = true,
            // Since we will immediately wrap the TextReader we are creating in an XmlReader, we will permit the XmlReader to take care of closing\disposing it
            CloseInput = true,
            // If the Xml you are reading is not a valid document (as per <https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/6bts1x50(v=vs.100)>) you will need to set the conformance level to Fragment
            ConformanceLevel = ConformanceLevel.Fragment
         };

         using (SqlConnection connection = new SqlConnection(connectionString)) {
            await connection.OpenAsync();

            // Cast the XML into NVarChar to enable GetTextReader - trying to use GetTextReader on an XML type will throw an exception
            using (SqlCommand command = new SqlCommand("SELECT [id], CAST([xmldata] AS NVARCHAR(MAX)) FROM [Streams]", connection)) {

               // The reader needs to be executed with the SequentialAccess behavior to enable network streaming
               // Otherwise ReadAsync will buffer the entire Xml Document into memory which can cause scalability issues or even OutOfMemoryExceptions
               using (SqlDataReader reader = await command.ExecuteReaderAsync(CommandBehavior.SequentialAccess)) {
                  while (await reader.ReadAsync()) {
                     Console.WriteLine("{0}:", reader.GetInt32(0));

                     if (await reader.IsDBNullAsync(1)) {
                        Console.WriteLine("\t(NULL)");
                     }
                     else {
                        // Grab the row as a TextReader, then create an XmlReader on top of it
                        // We are not keeping a reference to the TextReader since the XmlReader is created with the "CloseInput" setting (so it will close the TextReader when needed)
                        using (XmlReader xmlReader = XmlReader.Create(reader.GetTextReader(1), xmlSettings)) {
                           int depth = 1;
                           // The XmlReader above now supports asynchronous operations, so we can use ReadAsync here
                           while (await xmlReader.ReadAsync()) {
                              switch (xmlReader.NodeType) {
                                 case XmlNodeType.Element:
                                    Console.WriteLine("{0}<{1}>", new string('\t', depth), xmlReader.Name);
                                    depth++;
                                    break;
                                 case XmlNodeType.Text:
                                    // Depending on what your data looks like, you should either use Value or GetValueAsync
                                    // Value has less overhead (since it doesn't create a Task), but it may also block if additional data is required
                                    Console.WriteLine("{0}{1}", new string('\t', depth), await xmlReader.GetValueAsync());
                                    break;
                                 case XmlNodeType.EndElement:
                                    depth--;
                                    Console.WriteLine("{0}</{1}>", new string('\t', depth), xmlReader.Name);
                                    break;
                              }
                           }
                        }
                     }
                  }
               }
            }
         }
      }
   }
}
```

## <a name="sample----streaming-to-sql-server"></a><span data-ttu-id="cb867-140">示例--流式传输到 SQL Server</span><span class="sxs-lookup"><span data-stu-id="cb867-140">Sample -- Streaming to SQL Server</span></span>

<span data-ttu-id="cb867-141">使用以下 Transact-sql 创建示例数据库：</span><span class="sxs-lookup"><span data-stu-id="cb867-141">Use the following Transact-SQL to create the sample database:</span></span>

```sql
CREATE DATABASE [Demo2]
GO
USE [Demo2]
GO
CREATE TABLE [BinaryStreams] (
[id] INT PRIMARY KEY IDENTITY(1, 1),
[bindata] VARBINARY(MAX))
GO
CREATE TABLE [TextStreams] (
[id] INT PRIMARY KEY IDENTITY(1, 1),
[textdata] NVARCHAR(MAX))
GO
CREATE TABLE [BinaryStreamsCopy] (
[id] INT PRIMARY KEY IDENTITY(1, 1),
[bindata] VARBINARY(MAX))
GO
```

<span data-ttu-id="cb867-142">该示例说明如何执行以下功能：</span><span class="sxs-lookup"><span data-stu-id="cb867-142">The sample shows how to do the following:</span></span>

- <span data-ttu-id="cb867-143">在 .NET Framework 4.5 中将大型 BLOB 传输到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="cb867-143">Transferring a large BLOB to SQL Server in .NET Framework 4.5.</span></span>

- <span data-ttu-id="cb867-144">在 .NET Framework 4.5 中将大文本文件传输到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="cb867-144">Transferring a large text file to SQL Server in .NET Framework 4.5.</span></span>

- <span data-ttu-id="cb867-145">使用新异步功能来传输大型 BLOB。</span><span class="sxs-lookup"><span data-stu-id="cb867-145">Using the new asynchronous feature to transfer a large BLOB.</span></span>

- <span data-ttu-id="cb867-146">使用新异步功能和 await 关键字来传输大型 BLOB。</span><span class="sxs-lookup"><span data-stu-id="cb867-146">Using the new asynchronous feature and the await keyword to transfer a large BLOB.</span></span>

- <span data-ttu-id="cb867-147">正在取消大型 BLOB 的传输。</span><span class="sxs-lookup"><span data-stu-id="cb867-147">Cancelling the transfer of a large BLOB.</span></span>

- <span data-ttu-id="cb867-148">使用新的异步功能从一个 SQL Server 传输到另一个。</span><span class="sxs-lookup"><span data-stu-id="cb867-148">Streaming from one SQL Server to another using the new asynchronous feature.</span></span>

```csharp
using System;
using System.Data;
using System.Data.SqlClient;
using System.IO;
using System.Threading;
using System.Threading.Tasks;

namespace StreamingToServer {
   class Program {
      // Replace the connection string if needed, for instance to connect to SQL Express: @"Server=(local)\SQLEXPRESS;Database=Demo2;Integrated Security=true"
      private const string connectionString = @"Server=(localdb)\V11.0;Database=Demo2";

      static void Main(string[] args) {
         CreateDemoFiles();

         StreamBLOBToServer().Wait();
         StreamTextToServer().Wait();

         // Create a CancellationTokenSource that will be cancelled after 100ms
         // Typically this token source will be cancelled by a user request (e.g. a Cancel button)
         CancellationTokenSource tokenSource = new CancellationTokenSource();
         tokenSource.CancelAfter(100);
         try {
            CancelBLOBStream(tokenSource.Token).Wait();
         }
         catch (AggregateException ex) {
            // Cancelling an async operation will throw an exception
            // Since we are using the Task's Wait method, this exception will be wrapped in an AggregateException
            // If you were using the 'await' keyword, the compiler would take care of unwrapping the AggregateException
            // Depending on when the cancellation occurs, you can either get an error from SQL Server or from .Net
            if ((ex.InnerException is SqlException) || (ex.InnerException is TaskCanceledException)) {
               // This is an expected exception
               Console.WriteLine("Got expected exception: {0}", ex.InnerException.Message);
            }
            else {
               // Did not expect this exception - re-throw it
               throw;
            }
         }

         Console.WriteLine("Done");
      }

      // This is used to generate the files which are used by the other sample methods
      private static void CreateDemoFiles() {
         Random rand = new Random();
         byte[] data = new byte[1024];
         rand.NextBytes(data);

         using (FileStream file = File.Open("binarydata.bin", FileMode.Create)) {
            file.Write(data, 0, data.Length);
         }

         using (StreamWriter writer = new StreamWriter(File.Open("textdata.txt", FileMode.Create))) {
            writer.Write(Convert.ToBase64String(data));
         }
      }

      // Application transferring a large BLOB to SQL Server in .NET 4.5
      private static async Task StreamBLOBToServer() {
         using (SqlConnection conn = new SqlConnection(connectionString)) {
            await conn.OpenAsync();
            using (SqlCommand cmd = new SqlCommand("INSERT INTO [BinaryStreams] (bindata) VALUES (@bindata)", conn)) {
               using (FileStream file = File.Open("binarydata.bin", FileMode.Open)) {

                  // Add a parameter which uses the FileStream we just opened
                  // Size is set to -1 to indicate "MAX"
                  cmd.Parameters.Add("@bindata", SqlDbType.Binary, -1).Value = file;

                  // Send the data to the server asynchronously
                  await cmd.ExecuteNonQueryAsync();
               }
            }
         }
      }

      // Application transferring a large Text File to SQL Server in .NET 4.5
      private static async Task StreamTextToServer() {
         using (SqlConnection conn = new SqlConnection(connectionString)) {
            await conn.OpenAsync();
            using (SqlCommand cmd = new SqlCommand("INSERT INTO [TextStreams] (textdata) VALUES (@textdata)", conn)) {
               using (StreamReader file = File.OpenText("textdata.txt")) {

                  // Add a parameter which uses the StreamReader we just opened
                  // Size is set to -1 to indicate "MAX"
                  cmd.Parameters.Add("@textdata", SqlDbType.NVarChar, -1).Value = file;

                  // Send the data to the server asynchronously
                  await cmd.ExecuteNonQueryAsync();
               }
            }
         }
      }

      // Cancelling the transfer of a large BLOB
      private static async Task CancelBLOBStream(CancellationToken cancellationToken) {
         using (SqlConnection conn = new SqlConnection(connectionString)) {
            // We can cancel not only sending the data to the server, but also opening the connection
            await conn.OpenAsync(cancellationToken);

            // Artificially delay the command by 100ms
            using (SqlCommand cmd = new SqlCommand("WAITFOR DELAY '00:00:00:100';INSERT INTO [BinaryStreams] (bindata) VALUES (@bindata)", conn)) {
               using (FileStream file = File.Open("binarydata.bin", FileMode.Open)) {

                  // Add a parameter which uses the FileStream we just opened
                  // Size is set to -1 to indicate "MAX"
                  cmd.Parameters.Add("@bindata", SqlDbType.Binary, -1).Value = file;

                  // Send the data to the server asynchronously
                  // Pass the cancellation token such that the command will be cancelled if needed
                  await cmd.ExecuteNonQueryAsync(cancellationToken);
               }
            }
         }
      }
   }
}
```

## <a name="sample----streaming-from-one-sql-server-to-another-sql-server"></a><span data-ttu-id="cb867-149">示例-从一个 SQL Server 到另一个 SQL Server 的流式处理</span><span class="sxs-lookup"><span data-stu-id="cb867-149">Sample -- Streaming From One SQL Server to Another SQL Server</span></span>

<span data-ttu-id="cb867-150">此示例演示如何将大型 BLOB 从一个 SQL Server 异步流式传输到另一个，并支持取消操作。</span><span class="sxs-lookup"><span data-stu-id="cb867-150">This sample demonstrates how to asynchronously stream a large BLOB from one SQL Server to another, with support for cancellation.</span></span>

```csharp
using System;
using System.Data;
using System.Data.SqlClient;
using System.IO;
using System.Threading;
using System.Threading.Tasks;

namespace StreamingFromServerToAnother {
   class Program {
      // Replace the connection string if needed, for instance to connect to SQL Express: @"Server=(local)\SQLEXPRESS;Database=Demo2;Integrated Security=true"
      private const string connectionString = @"Server=(localdb)\V11.0;Database=Demo2";

      static void Main(string[] args) {
         // For this example, we don't want to cancel
         // So we can pass in a "blank" cancellation token
         E2EStream(CancellationToken.None).Wait();

         Console.WriteLine("Done");
      }

      // Streaming from one SQL Server to Another One using the new Async.NET
      private static async Task E2EStream(CancellationToken cancellationToken) {
         using (SqlConnection readConn = new SqlConnection(connectionString)) {
            using (SqlConnection writeConn = new SqlConnection(connectionString)) {

               // Note that we are using the same cancellation token for calls to both connections\commands
               // Also we can start both the connection opening asynchronously, and then wait for both to complete
               Task openReadConn = readConn.OpenAsync(cancellationToken);
               Task openWriteConn = writeConn.OpenAsync(cancellationToken);
               await Task.WhenAll(openReadConn, openWriteConn);

               using (SqlCommand readCmd = new SqlCommand("SELECT [bindata] FROM [BinaryStreams]", readConn)) {
                  using (SqlCommand writeCmd = new SqlCommand("INSERT INTO [BinaryStreamsCopy] (bindata) VALUES (@bindata)", writeConn)) {

                     // Add an empty parameter to the write command which will be used for the streams we are copying
                     // Size is set to -1 to indicate "MAX"
                     SqlParameter streamParameter = writeCmd.Parameters.Add("@bindata", SqlDbType.Binary, -1);

                     // The reader needs to be executed with the SequentialAccess behavior to enable network streaming
                     // Otherwise ReadAsync will buffer the entire BLOB into memory which can cause scalability issues or even OutOfMemoryExceptions
                     using (SqlDataReader reader = await readCmd.ExecuteReaderAsync(CommandBehavior.SequentialAccess, cancellationToken)) {
                        while (await reader.ReadAsync(cancellationToken)) {
                           // Grab a stream to the binary data in the source database
                           using (Stream dataStream = reader.GetStream(0)) {

                              // Set the parameter value to the stream source that was opened
                              streamParameter.Value = dataStream;

                              // Asynchronously send data from one database to another
                              await writeCmd.ExecuteNonQueryAsync(cancellationToken);
                           }
                        }
                     }
                  }
               }
            }
         }
      }
   }
}
```

## <a name="see-also"></a><span data-ttu-id="cb867-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cb867-151">See also</span></span>

- [<span data-ttu-id="cb867-152">在 ADO.NET 中检索和修改数据</span><span class="sxs-lookup"><span data-stu-id="cb867-152">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)

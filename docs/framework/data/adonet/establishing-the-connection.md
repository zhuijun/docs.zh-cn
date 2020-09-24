---
title: 建立连接
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
ms.openlocfilehash: bf38475711a193bc69176993154f87d455aefe7d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156467"
---
# <a name="establishing-the-connection"></a><span data-ttu-id="e9c81-102">建立连接</span><span class="sxs-lookup"><span data-stu-id="e9c81-102">Establishing the Connection</span></span>

<span data-ttu-id="e9c81-103">要连接到 Microsoft SQL Server，请使用 SQL Server .NET Framework 数据提供程序的 <xref:System.Data.SqlClient.SqlConnection> 对象。</span><span class="sxs-lookup"><span data-stu-id="e9c81-103">To connect to Microsoft SQL Server, use the <xref:System.Data.SqlClient.SqlConnection> object of the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="e9c81-104">要连接到 OLE DB 数据源，请使用 OLE DB .NET Framework 数据提供程序的 <xref:System.Data.OleDb.OleDbConnection> 对象。</span><span class="sxs-lookup"><span data-stu-id="e9c81-104">To connect to an OLE DB data source, use the <xref:System.Data.OleDb.OleDbConnection> object of the .NET Framework Data Provider for OLE DB.</span></span> <span data-ttu-id="e9c81-105">要连接到 ODBC 数据源，请使用 ODBC .NET Framework 数据提供程序的 <xref:System.Data.Odbc.OdbcConnection> 对象。</span><span class="sxs-lookup"><span data-stu-id="e9c81-105">To connect to an ODBC data source, use the <xref:System.Data.Odbc.OdbcConnection> object of the .NET Framework Data Provider for ODBC.</span></span> <span data-ttu-id="e9c81-106">要连接到 Oracle 数据源，请使用 Oracle .NET Framework 数据提供程序的 <xref:System.Data.OracleClient.OracleConnection> 对象。</span><span class="sxs-lookup"><span data-stu-id="e9c81-106">To connect to an Oracle data source, use the <xref:System.Data.OracleClient.OracleConnection> object of the .NET Framework Data Provider for Oracle.</span></span> <span data-ttu-id="e9c81-107">为了安全地存储和检索连接字符串，请参阅 [保护连接信息](protecting-connection-information.md)。</span><span class="sxs-lookup"><span data-stu-id="e9c81-107">For securely storing and retrieving connection strings, see [Protecting Connection Information](protecting-connection-information.md).</span></span>  
  
## <a name="closing-connections"></a><span data-ttu-id="e9c81-108">关闭连接</span><span class="sxs-lookup"><span data-stu-id="e9c81-108">Closing Connections</span></span>  

 <span data-ttu-id="e9c81-109">我们建议您在使用完连接时一定要关闭连接，以便连接可以返回池。</span><span class="sxs-lookup"><span data-stu-id="e9c81-109">We recommend that you always close the connection when you are finished using it, so that the connection can be returned to the pool.</span></span> <span data-ttu-id="e9c81-110">如果 Visual Basic 或 C# 的代码中存在 `Using` 块，将自动断开连接，即使发生无法处理的异常。</span><span class="sxs-lookup"><span data-stu-id="e9c81-110">The `Using` block in Visual Basic or C# automatically disposes of the connection when the code exits the block, even in the case of an unhandled exception.</span></span> <span data-ttu-id="e9c81-111">有关详细信息，请参阅 [Using 语句](../../../csharp/language-reference/keywords/using-statement.md) 和 [using 语句](../../../visual-basic/language-reference/statements/using-statement.md) 。</span><span class="sxs-lookup"><span data-stu-id="e9c81-111">See [using Statement](../../../csharp/language-reference/keywords/using-statement.md) and [Using Statement](../../../visual-basic/language-reference/statements/using-statement.md) for more information.</span></span>  
  
 <span data-ttu-id="e9c81-112">也可以使用适合所使用的提供程序的连接对象的 `Close` 或 `Dispose` 方法。</span><span class="sxs-lookup"><span data-stu-id="e9c81-112">You can also use the `Close` or `Dispose` methods of the connection object for the provider that you are using.</span></span> <span data-ttu-id="e9c81-113">不是显式关闭的连接可能不会添加或返回到池中。</span><span class="sxs-lookup"><span data-stu-id="e9c81-113">Connections that are not explicitly closed might not be added or returned to the pool.</span></span> <span data-ttu-id="e9c81-114">例如，如果连接已超出范围但没有显式关闭，则仅当达到最大池大小而该连接仍然有效时，该连接才会返回到连接池中。</span><span class="sxs-lookup"><span data-stu-id="e9c81-114">For example, a connection that has gone out of scope but that has not been explicitly closed will only be returned to the connection pool if the maximum pool size has been reached and the connection is still valid.</span></span> <span data-ttu-id="e9c81-115">有关详细信息，请参阅 [OLE DB、ODBC 和 Oracle 连接池](ole-db-odbc-and-oracle-connection-pooling.md)。</span><span class="sxs-lookup"><span data-stu-id="e9c81-115">For more information, see [OLE DB, ODBC, and Oracle Connection Pooling](ole-db-odbc-and-oracle-connection-pooling.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e9c81-116">不要在 `Close` 类的 `Dispose` 方法中对 **连接**、 **DataReader**或任何其他托管对象调用或 `Finalize` 。</span><span class="sxs-lookup"><span data-stu-id="e9c81-116">Do not call `Close` or `Dispose` on a **Connection**, a **DataReader**, or any other managed object in the `Finalize` method of your class.</span></span> <span data-ttu-id="e9c81-117">在终结器中，仅释放类直接拥有的非托管资源。</span><span class="sxs-lookup"><span data-stu-id="e9c81-117">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="e9c81-118">如果类不拥有任何非托管资源，则不要在类定义中包含 `Finalize` 方法。</span><span class="sxs-lookup"><span data-stu-id="e9c81-118">If your class does not own any unmanaged resources, do not include a `Finalize` method in your class definition.</span></span> <span data-ttu-id="e9c81-119">有关详细信息，请参阅 [垃圾回收](../../../standard/garbage-collection/index.md)。</span><span class="sxs-lookup"><span data-stu-id="e9c81-119">For more information, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e9c81-120">从连接池中提取连接或将连接返回到连接池时，服务器上不会引发登录和注销事件，这是因为在将连接返回到连接池时实际上并没有将其关闭。</span><span class="sxs-lookup"><span data-stu-id="e9c81-120">Login and logout events will not be raised on the server when a connection is fetched from or returned to the connection pool, because the connection is not actually closed when it is returned to the connection pool.</span></span> <span data-ttu-id="e9c81-121">有关详细信息，请参阅 [SQL Server 连接池 (ADO.NET)](sql-server-connection-pooling.md)。</span><span class="sxs-lookup"><span data-stu-id="e9c81-121">For more information, see [SQL Server Connection Pooling (ADO.NET)](sql-server-connection-pooling.md).</span></span>  
  
## <a name="connecting-to-sql-server"></a><span data-ttu-id="e9c81-122">连接到 SQL Server</span><span class="sxs-lookup"><span data-stu-id="e9c81-122">Connecting to SQL Server</span></span>  

 <span data-ttu-id="e9c81-123">SQL Server .NET Framework 数据提供程序支持类似于 OLE DB (ADO) 连接字符串格式的连接字符串格式。</span><span class="sxs-lookup"><span data-stu-id="e9c81-123">The .NET Framework Data Provider for SQL Server supports a connection string format that is similar to the OLE DB (ADO) connection string format.</span></span> <span data-ttu-id="e9c81-124">有关有效的字符串格式名称和值，请参见 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> 对象的 <xref:System.Data.SqlClient.SqlConnection> 属性。</span><span class="sxs-lookup"><span data-stu-id="e9c81-124">For valid string format names and values, see the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="e9c81-125">您也可以使用 <xref:System.Data.SqlClient.SqlConnectionStringBuilder> 类在运行时创建具有有效语法的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="e9c81-125">You can also use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> class to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="e9c81-126">有关详细信息，请参阅[连接字符串生成器](connection-string-builders.md)。</span><span class="sxs-lookup"><span data-stu-id="e9c81-126">For more information, see [Connection String Builders](connection-string-builders.md).</span></span>  
  
 <span data-ttu-id="e9c81-127">以下代码示例演示如何创建并打开与 SQL Server 数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="e9c81-127">The following code example demonstrates how to create and open a connection to a SQL Server database.</span></span>  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New SqlConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (SqlConnection connection = new SqlConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
### <a name="integrated-security-and-aspnet"></a><span data-ttu-id="e9c81-128">集成安全性和 ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e9c81-128">Integrated Security and ASP.NET</span></span>  

 <span data-ttu-id="e9c81-129">SQL Server 集成安全性（也称为受信任连接）有助于在连接到 SQL Server 时提供保护，因为它不会在连接字符串中公开用户 ID 和密码，是对连接进行身份验证的建议方法。</span><span class="sxs-lookup"><span data-stu-id="e9c81-129">SQL Server integrated security (also known as trusted connections) helps to provide protection when connecting to SQL Server as it does not expose a user ID and password in the connection string and is the recommended method for authenticating a connection.</span></span> <span data-ttu-id="e9c81-130">集成安全性使用正在执行的进程的当前安全标识或标记。</span><span class="sxs-lookup"><span data-stu-id="e9c81-130">Integrated security uses the current security identity, or token, of the executing process.</span></span> <span data-ttu-id="e9c81-131">对于桌面应用程序，安全标识或标记通常是当前登录的用户的标识。</span><span class="sxs-lookup"><span data-stu-id="e9c81-131">For desktop applications, this is typically the identity of the currently logged-on user.</span></span>  
  
 <span data-ttu-id="e9c81-132">ASP.NET 应用程序的安全标识可设置为几个不同的选项之一。</span><span class="sxs-lookup"><span data-stu-id="e9c81-132">The security identity for ASP.NET applications can be set to one of several different options.</span></span> <span data-ttu-id="e9c81-133">为了更好地了解 ASP.NET 应用程序连接到 SQL Server 时使用的安全标识，请参阅 [ASP.NET 模拟](/previous-versions/aspnet/xh507fc5(v=vs.100))、 [ASP.NET 身份验证](/previous-versions/aspnet/eeyk640h(v=vs.100))和 [如何：使用 Windows 集成安全性访问 SQL Server](/previous-versions/aspnet/bsz5788z(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="e9c81-133">To better understand the security identity that an ASP.NET application uses when connecting to SQL Server, see [ASP.NET Impersonation](/previous-versions/aspnet/xh507fc5(v=vs.100)), [ASP.NET Authentication](/previous-versions/aspnet/eeyk640h(v=vs.100)), and [How to: Access SQL Server Using Windows Integrated Security](/previous-versions/aspnet/bsz5788z(v=vs.100)).</span></span>  
  
## <a name="connecting-to-an-ole-db-data-source"></a><span data-ttu-id="e9c81-134">连接到 OLE DB 数据源</span><span class="sxs-lookup"><span data-stu-id="e9c81-134">Connecting to an OLE DB Data Source</span></span>  

 <span data-ttu-id="e9c81-135">OLE DB 的 .NET Framework 数据提供程序提供了与使用 OLE DB (通过 SQLOLEDB （使用 **OleDbConnection** 对象的 OLE DB SQL Server 提供程序）公开的数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="e9c81-135">The .NET Framework Data Provider for OLE DB provides connectivity to data sources exposed using OLE DB (through SQLOLEDB, the OLE DB Provider for SQL Server), using the **OleDbConnection** object.</span></span>  
  
 <span data-ttu-id="e9c81-136">对于 OLE DB .NET Framework 数据提供程序，连接字符串格式与 ADO 中使用的连接字符串格式基本相同，但存在以下例外：</span><span class="sxs-lookup"><span data-stu-id="e9c81-136">For the .NET Framework Data Provider for OLE DB, the connection string format is identical to the connection string format used in ADO, with the following exceptions:</span></span>  
  
- <span data-ttu-id="e9c81-137">**Provider**关键字是必需的。</span><span class="sxs-lookup"><span data-stu-id="e9c81-137">The **Provider** keyword is required.</span></span>  
  
- <span data-ttu-id="e9c81-138">不支持 **URL**、 **远程提供程序**和 **远程服务器** 关键字。</span><span class="sxs-lookup"><span data-stu-id="e9c81-138">The **URL**, **Remote Provider**, and **Remote Server** keywords are not supported.</span></span>  
  
 <span data-ttu-id="e9c81-139">有关 OLE DB 连接字符串的更多信息，请参见 <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> 主题。</span><span class="sxs-lookup"><span data-stu-id="e9c81-139">For more information about OLE DB connection strings, see the <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> topic.</span></span> <span data-ttu-id="e9c81-140">您也可以使用 <xref:System.Data.OleDb.OleDbConnectionStringBuilder> 在运行时创建连接字符串。</span><span class="sxs-lookup"><span data-stu-id="e9c81-140">You can also use the <xref:System.Data.OleDb.OleDbConnectionStringBuilder> to create connection strings at run time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e9c81-141">**OleDbConnection**对象不支持设置或检索特定于 OLE DB 提供程序的动态属性。</span><span class="sxs-lookup"><span data-stu-id="e9c81-141">The **OleDbConnection** object does not support setting or retrieving dynamic properties specific to an OLE DB provider.</span></span> <span data-ttu-id="e9c81-142">只支持可在 OLE DB 提供程序连接字符串中传递的属性。</span><span class="sxs-lookup"><span data-stu-id="e9c81-142">Only properties that can be passed in the connection string for the OLE DB provider are supported.</span></span>  
  
 <span data-ttu-id="e9c81-143">以下代码示例演示如何创建和打开与 OLE DB 数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="e9c81-143">The following code example demonstrates how to create and open a connection to an OLE DB data source.</span></span>  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OleDbConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OleDbConnection connection =
  new OleDbConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
## <a name="do-not-use-universal-data-link-files"></a><span data-ttu-id="e9c81-144">不要使用通用数据链接文件</span><span class="sxs-lookup"><span data-stu-id="e9c81-144">Do Not Use Universal Data Link Files</span></span>  

 <span data-ttu-id="e9c81-145">可以 (UDL) 文件中的通用数据链接提供 **OleDbConnection** 的连接信息;但是，应避免这样做。</span><span class="sxs-lookup"><span data-stu-id="e9c81-145">It is possible to supply connection information for an **OleDbConnection** in a Universal Data Link (UDL) file; however you should avoid doing so.</span></span> <span data-ttu-id="e9c81-146">UDL 文件未加密，会以明文形式公开连接字符串信息。</span><span class="sxs-lookup"><span data-stu-id="e9c81-146">UDL files are not encrypted, and expose connection string information in clear text.</span></span> <span data-ttu-id="e9c81-147">因为 UDL 文件对您的应用程序来说是一个基于文件的外部资源，所以无法使用 .NET Framework 保护该文件。</span><span class="sxs-lookup"><span data-stu-id="e9c81-147">Because a UDL file is an external file-based resource to your application, it cannot be secured using the .NET Framework.</span></span>  
  
## <a name="connecting-to-an-odbc-data-source"></a><span data-ttu-id="e9c81-148">连接到 ODBC 数据源</span><span class="sxs-lookup"><span data-stu-id="e9c81-148">Connecting to an ODBC Data Source</span></span>  

 <span data-ttu-id="e9c81-149">适用于 ODBC 的 .NET Framework 数据提供程序提供了使用 **OdbcConnection** 对象与使用 ODBC 公开的数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="e9c81-149">The .NET Framework Data Provider for ODBC provides connectivity to data sources exposed using ODBC using the **OdbcConnection** object.</span></span>  
  
 <span data-ttu-id="e9c81-150">对于 ODBC .NET Framework 数据提供程序，连接字符串的格式设计为尽可能与 ODBC 连接字符串的格式相匹配。</span><span class="sxs-lookup"><span data-stu-id="e9c81-150">For the .NET Framework Data Provider for ODBC, the connection string format is designed to match the ODBC connection string format as closely as possible.</span></span> <span data-ttu-id="e9c81-151">您还可以提供一个 ODBC 数据源名称 (DSN)。</span><span class="sxs-lookup"><span data-stu-id="e9c81-151">You may also supply an ODBC data source name (DSN).</span></span> <span data-ttu-id="e9c81-152">有关 **OdbcConnection** 的更多详细信息，请参阅 <xref:System.Data.Odbc.OdbcConnection> 。</span><span class="sxs-lookup"><span data-stu-id="e9c81-152">For more detail on the **OdbcConnection** , see the <xref:System.Data.Odbc.OdbcConnection>.</span></span>  
  
 <span data-ttu-id="e9c81-153">以下代码示例演示如何创建和打开与 ODBC 数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="e9c81-153">The following code example demonstrates how to create and open a connection to an ODBC data source.</span></span>  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OdbcConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OdbcConnection connection =
  new OdbcConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
## <a name="connecting-to-an-oracle-data-source"></a><span data-ttu-id="e9c81-154">连接到 Oracle 数据源</span><span class="sxs-lookup"><span data-stu-id="e9c81-154">Connecting to an Oracle Data Source</span></span>  

 <span data-ttu-id="e9c81-155">用于 Oracle 的 .NET Framework 数据提供程序使用 **OracleConnection** 对象提供与 oracle 数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="e9c81-155">The .NET Framework Data Provider for Oracle provides connectivity to Oracle data sources using the **OracleConnection** object.</span></span>  
  
 <span data-ttu-id="e9c81-156">对于 Oracle .NET Framework 数据提供程序，连接字符串的格式设计为尽可能与用于 Oracle 的 OLE DB 提供程序 (MSDAORA) 连接字符串格式相匹配。</span><span class="sxs-lookup"><span data-stu-id="e9c81-156">For the .NET Framework Data Provider for Oracle, the connection string format is designed to match the OLE DB Provider for Oracle (MSDAORA) connection string format as closely as possible.</span></span> <span data-ttu-id="e9c81-157">有关 **OracleConnection**的更多详细信息，请参阅 <xref:System.Data.OracleClient.OracleConnection> 。</span><span class="sxs-lookup"><span data-stu-id="e9c81-157">For more detail on the **OracleConnection**, see the <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
 <span data-ttu-id="e9c81-158">以下代码示例演示如何创建和打开与 Oracle 数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="e9c81-158">The following code example demonstrates how to create and open a connection to an Oracle data source.</span></span>  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OracleConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OracleConnection connection =
  new OracleConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
OracleConnection nwindConn = new OracleConnection("Data Source=MyOracleServer;Integrated Security=yes;");  
nwindConn.Open();  
```  
  
## <a name="see-also"></a><span data-ttu-id="e9c81-159">请参阅</span><span class="sxs-lookup"><span data-stu-id="e9c81-159">See also</span></span>

- [<span data-ttu-id="e9c81-160">连接数据源</span><span class="sxs-lookup"><span data-stu-id="e9c81-160">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="e9c81-161">连接字符串</span><span class="sxs-lookup"><span data-stu-id="e9c81-161">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="e9c81-162">OLE DB、ODBC 和 Oracle 连接池</span><span class="sxs-lookup"><span data-stu-id="e9c81-162">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)
- [<span data-ttu-id="e9c81-163">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="e9c81-163">ADO.NET Overview</span></span>](ado-net-overview.md)

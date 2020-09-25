---
title: 连接数据源
deescription: Learn about Connection objects, used to connect to data sources in ADO.NET. The Connection object you choose depends on the type of data source.
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: b9e69b029ad37c583e51c219f87ff9d7d8e7315c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203769"
---
# <a name="connecting-to-a-data-source-in-adonet"></a><span data-ttu-id="a3165-102">连接到 ADO.NET 中的数据源</span><span class="sxs-lookup"><span data-stu-id="a3165-102">Connecting to a Data Source in ADO.NET</span></span>

<span data-ttu-id="a3165-103">在 ADO.NET 中，通过在连接字符串中提供必要的身份验证信息，使用 **连接** 对象连接到特定数据源。</span><span class="sxs-lookup"><span data-stu-id="a3165-103">In ADO.NET, you use a **Connection** object to connect to a specific data source by supplying necessary authentication information in a connection string.</span></span> <span data-ttu-id="a3165-104">使用的 **连接** 对象取决于数据源的类型。</span><span class="sxs-lookup"><span data-stu-id="a3165-104">The **Connection** object you use depends on the type of data source.</span></span>  
  
 <span data-ttu-id="a3165-105">随 .NET Framework 提供的每个 .NET Framework 数据提供程序都具有一个 <xref:System.Data.Common.DbConnection> 对象：适用于 OLE DB 的 .NET Framework 数据提供程序包括一个 <xref:System.Data.OleDb.OleDbConnection> 对象，适用于 SQL Server 的 .NET Framework 数据提供程序包括一个 <xref:System.Data.SqlClient.SqlConnection> 对象，适用于 ODBC 的 .NET Framework 数据提供程序包括一个 <xref:System.Data.Odbc.OdbcConnection> 对象，适用于 Oracle 的 .NET Framework 数据提供程序包括一个 <xref:System.Data.OracleClient.OracleConnection> 对象。</span><span class="sxs-lookup"><span data-stu-id="a3165-105">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbConnection> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbConnection> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlConnection> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcConnection> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleConnection> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a3165-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="a3165-106">In This Section</span></span>  

 <span data-ttu-id="a3165-107">[建立连接](establishing-the-connection.md)</span><span class="sxs-lookup"><span data-stu-id="a3165-107">[Establishing the Connection](establishing-the-connection.md)</span></span>\
 <span data-ttu-id="a3165-108">介绍如何使用 **连接** 对象建立与数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="a3165-108">Describes how to use a **Connection** object to establish a connection to a data source.</span></span>  
  
 <span data-ttu-id="a3165-109">[连接事件](connection-events.md)</span><span class="sxs-lookup"><span data-stu-id="a3165-109">[Connection Events](connection-events.md)</span></span>\
 <span data-ttu-id="a3165-110">介绍如何使用 **InfoMessage** 事件从数据源中检索信息性消息。</span><span class="sxs-lookup"><span data-stu-id="a3165-110">Describes how to use an **InfoMessage** event to retrieve informational messages from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3165-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="a3165-111">See also</span></span>

- [<span data-ttu-id="a3165-112">连接字符串</span><span class="sxs-lookup"><span data-stu-id="a3165-112">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="a3165-113">连接池</span><span class="sxs-lookup"><span data-stu-id="a3165-113">Connection Pooling</span></span>](connection-pooling.md)
- [<span data-ttu-id="a3165-114">命令和参数</span><span class="sxs-lookup"><span data-stu-id="a3165-114">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="a3165-115">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="a3165-115">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="a3165-116">事务和并发性</span><span class="sxs-lookup"><span data-stu-id="a3165-116">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="a3165-117">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="a3165-117">ADO.NET Overview</span></span>](ado-net-overview.md)

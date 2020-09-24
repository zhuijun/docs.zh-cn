---
title: 执行命令
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 40494916-c25a-4cb8-8f7c-fcb8d378464e
ms.openlocfilehash: d7d290c1c149f9eab2449c25e8d32f2568eb0277
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156454"
---
# <a name="executing-a-command"></a><span data-ttu-id="151ae-102">执行命令</span><span class="sxs-lookup"><span data-stu-id="151ae-102">Executing a Command</span></span>

<span data-ttu-id="151ae-103">包含在 .NET Framework 中的每个 .NET Framework 数据提供程序都拥有自己的继承自 <xref:System.Data.Common.DbCommand> 的命令对象。</span><span class="sxs-lookup"><span data-stu-id="151ae-103">Each .NET Framework data provider included with the .NET Framework has its own command object that inherits from <xref:System.Data.Common.DbCommand>.</span></span> <span data-ttu-id="151ae-104">适用于 OLE DB 的 .NET Framework 数据提供程序包括一个 <xref:System.Data.OleDb.OleDbCommand> 对象，适用于 SQL Server 的 .NET Framework 数据提供程序包括一个 <xref:System.Data.SqlClient.SqlCommand> 对象，适用于 ODBC 的 .NET Framework 数据提供程序包括一个 <xref:System.Data.Odbc.OdbcCommand> 对象，适用于 Oracle 的 .NET Framework 数据提供程序包括一个 <xref:System.Data.OracleClient.OracleCommand> 对象。</span><span class="sxs-lookup"><span data-stu-id="151ae-104">The .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbCommand> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlCommand> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcCommand> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleCommand> object.</span></span> <span data-ttu-id="151ae-105">其中每个对象都根据命令的类型和所需的返回值公开用于执行命令的方法，如下表所述。</span><span class="sxs-lookup"><span data-stu-id="151ae-105">Each of these objects exposes methods for executing commands based on the type of command and desired return value, as described in the following table.</span></span>  
  
|<span data-ttu-id="151ae-106">命令</span><span class="sxs-lookup"><span data-stu-id="151ae-106">Command</span></span>|<span data-ttu-id="151ae-107">返回值</span><span class="sxs-lookup"><span data-stu-id="151ae-107">Return Value</span></span>|  
|-------------|------------------|  
|`ExecuteReader`|<span data-ttu-id="151ae-108">返回一个 `DataReader` 对象。</span><span class="sxs-lookup"><span data-stu-id="151ae-108">Returns a `DataReader` object.</span></span>|  
|`ExecuteScalar`|<span data-ttu-id="151ae-109">返回一个标量值。</span><span class="sxs-lookup"><span data-stu-id="151ae-109">Returns a single scalar value.</span></span>|  
|`ExecuteNonQuery`|<span data-ttu-id="151ae-110">执行不返回任何行的命令。</span><span class="sxs-lookup"><span data-stu-id="151ae-110">Executes a command that does not return any rows.</span></span>|  
|`ExecuteXMLReader`|<span data-ttu-id="151ae-111">返回 <xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="151ae-111">Returns an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="151ae-112">只用于 `SqlCommand` 对象。</span><span class="sxs-lookup"><span data-stu-id="151ae-112">Available for a `SqlCommand` object only.</span></span>|  
  
 <span data-ttu-id="151ae-113">每个强类型命令对象还支持指定如何解释命令字符串的 <xref:System.Data.CommandType> 枚举，如下表所述。</span><span class="sxs-lookup"><span data-stu-id="151ae-113">Each strongly typed command object also supports a <xref:System.Data.CommandType> enumeration that specifies how a command string is interpreted, as described in the following table.</span></span>  
  
|<span data-ttu-id="151ae-114">CommandType</span><span class="sxs-lookup"><span data-stu-id="151ae-114">CommandType</span></span>|<span data-ttu-id="151ae-115">描述</span><span class="sxs-lookup"><span data-stu-id="151ae-115">Description</span></span>|  
|-----------------|-----------------|  
|`Text`|<span data-ttu-id="151ae-116">定义要在数据源处执行的语句的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="151ae-116">An SQL command defining the statements to be executed at the data source.</span></span>|  
|`StoredProcedure`|<span data-ttu-id="151ae-117">存储过程的名称。</span><span class="sxs-lookup"><span data-stu-id="151ae-117">The name of the stored procedure.</span></span> <span data-ttu-id="151ae-118">您可以使用某一命令的 `Parameters` 属性访问输入和输出参数，并返回值（无论调用哪种 `Execute` 方法）。</span><span class="sxs-lookup"><span data-stu-id="151ae-118">You can use the `Parameters` property of a command to access input and output parameters and return values, regardless of which `Execute` method is called.</span></span> <span data-ttu-id="151ae-119">当使用 `ExecuteReader` 时，在关闭 `DataReader` 后才能访问返回值和输出参数。</span><span class="sxs-lookup"><span data-stu-id="151ae-119">When using `ExecuteReader`, return values and output parameters will not be accessible until the `DataReader` is closed.</span></span>|  
|`TableDirect`|<span data-ttu-id="151ae-120">表的名称。</span><span class="sxs-lookup"><span data-stu-id="151ae-120">The name of a table.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="151ae-121">示例</span><span class="sxs-lookup"><span data-stu-id="151ae-121">Example</span></span>  

 <span data-ttu-id="151ae-122">下面的代码示例演示如何创建 <xref:System.Data.SqlClient.SqlCommand> 对象以通过设置其属性执行存储过程。</span><span class="sxs-lookup"><span data-stu-id="151ae-122">The following code example demonstrates how to create a <xref:System.Data.SqlClient.SqlCommand> object to execute a stored procedure by setting its properties.</span></span> <span data-ttu-id="151ae-123"><xref:System.Data.SqlClient.SqlParameter> 对象用于指定存储过程的输入参数。</span><span class="sxs-lookup"><span data-stu-id="151ae-123">A <xref:System.Data.SqlClient.SqlParameter> object is used to specify the input parameter to the stored procedure.</span></span> <span data-ttu-id="151ae-124">使用 <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> 方法执行此命令，并在控制台窗口中显示 <xref:System.Data.SqlClient.SqlDataReader> 的输出。</span><span class="sxs-lookup"><span data-stu-id="151ae-124">The command is executed using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method, and the output from the <xref:System.Data.SqlClient.SqlDataReader> is displayed in the console window.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
### <a name="troubleshooting-commands"></a><span data-ttu-id="151ae-125">命令疑难解答</span><span class="sxs-lookup"><span data-stu-id="151ae-125">Troubleshooting Commands</span></span>  

 <span data-ttu-id="151ae-126">用于 SQL Server 的 .NET Framework 数据提供程序添加了性能计数器，使您能够检测与失败的命令执行相关的间歇性问题。</span><span class="sxs-lookup"><span data-stu-id="151ae-126">The .NET Framework Data Provider for SQL Server adds performance counters to enable you to detect intermittent problems related to failed command executions.</span></span> <span data-ttu-id="151ae-127">有关详细信息，请参阅 [性能计数器](performance-counters.md)。</span><span class="sxs-lookup"><span data-stu-id="151ae-127">For more information see [Performance Counters](performance-counters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="151ae-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="151ae-128">See also</span></span>

- [<span data-ttu-id="151ae-129">命令和参数</span><span class="sxs-lookup"><span data-stu-id="151ae-129">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="151ae-130">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="151ae-130">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="151ae-131">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="151ae-131">ADO.NET Overview</span></span>](ado-net-overview.md)

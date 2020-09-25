---
title: 命令和参数
description: 了解如何使用每个 .NET Framework 数据提供程序的命令对象来运行命令并从数据源返回结果。
ms.date: 03/30/2017
ms.assetid: b623f810-d871-49a5-b0f5-078cc3c34db6
ms.openlocfilehash: fb7b86dc3c826805e0e1dcec4764be2e484ec40b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203821"
---
# <a name="commands-and-parameters"></a><span data-ttu-id="290d6-103">命令和参数</span><span class="sxs-lookup"><span data-stu-id="290d6-103">Commands and Parameters</span></span>

<span data-ttu-id="290d6-104">建立与数据源的连接后，可以使用 <xref:System.Data.Common.DbCommand> 对象来执行命令并从数据源中返回结果。</span><span class="sxs-lookup"><span data-stu-id="290d6-104">After establishing a connection to a data source, you can execute commands and return results from the data source using a <xref:System.Data.Common.DbCommand> object.</span></span> <span data-ttu-id="290d6-105">您可以使用命令构造函数之一为要使用的 .NET Framework 数据提供程序创建命令。</span><span class="sxs-lookup"><span data-stu-id="290d6-105">You can create a command using one of the command constructors for the .NET Framework data provider you are working with.</span></span> <span data-ttu-id="290d6-106">构造函数可以采用可选自变量，如要在数据源中执行的 SQL 语句、<xref:System.Data.Common.DbConnection> 对象或 <xref:System.Data.Common.DbTransaction> 对象。</span><span class="sxs-lookup"><span data-stu-id="290d6-106">Constructors can take optional arguments, such as an SQL statement to execute at the data source, a <xref:System.Data.Common.DbConnection> object, or a <xref:System.Data.Common.DbTransaction> object.</span></span> <span data-ttu-id="290d6-107">您也可以将这些对象配置为命令的属性。</span><span class="sxs-lookup"><span data-stu-id="290d6-107">You can also configure those objects as properties of the command.</span></span> <span data-ttu-id="290d6-108">也可以使用 <xref:System.Data.Common.DbConnection.CreateCommand%2A> 对象的 `DbConnection` 方法创建用于特定连接的命令。</span><span class="sxs-lookup"><span data-stu-id="290d6-108">You can also create a command for a particular connection using the <xref:System.Data.Common.DbConnection.CreateCommand%2A> method of a `DbConnection` object.</span></span> <span data-ttu-id="290d6-109">由命令执行的 SQL 语句可以使用 <xref:System.Data.Common.DbCommand.CommandText%2A> 属性进行配置。</span><span class="sxs-lookup"><span data-stu-id="290d6-109">The SQL statement being executed by the command can be configured using the <xref:System.Data.Common.DbCommand.CommandText%2A> property.</span></span>  
  
 <span data-ttu-id="290d6-110">随 .NET Framework 提供的每个 .NET Framework 数据提供程序都具有一个 `Command` 对象。</span><span class="sxs-lookup"><span data-stu-id="290d6-110">Each .NET Framework data provider included with the .NET Framework has a `Command` object.</span></span> <span data-ttu-id="290d6-111">适用于 OLE DB 的 .NET Framework 数据提供程序包括一个 <xref:System.Data.OleDb.OleDbCommand> 对象，适用于 SQL Server 的 .NET Framework 数据提供程序包括一个 <xref:System.Data.SqlClient.SqlCommand> 对象，适用于 ODBC 的 .NET Framework 数据提供程序包括一个 <xref:System.Data.Odbc.OdbcCommand> 对象，适用于 Oracle 的 .NET Framework 数据提供程序包括一个 <xref:System.Data.OracleClient.OracleCommand> 对象。</span><span class="sxs-lookup"><span data-stu-id="290d6-111">The .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbCommand> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlCommand> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcCommand> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleCommand> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="290d6-112">本节内容</span><span class="sxs-lookup"><span data-stu-id="290d6-112">In This Section</span></span>  

 [<span data-ttu-id="290d6-113">执行命令</span><span class="sxs-lookup"><span data-stu-id="290d6-113">Executing a Command</span></span>](executing-a-command.md)  
 <span data-ttu-id="290d6-114">说明 ADO.NET `Command` 对象以及如何使用该对象对数据源执行查询和命令。</span><span class="sxs-lookup"><span data-stu-id="290d6-114">Describes the ADO.NET `Command` object and how to use it to execute queries and commands against a data source.</span></span>  
  
 [<span data-ttu-id="290d6-115">配置参数和参数数据类型</span><span class="sxs-lookup"><span data-stu-id="290d6-115">Configuring Parameters and Parameter Data Types</span></span>](configuring-parameters-and-parameter-data-types.md)  
 <span data-ttu-id="290d6-116">说明如何使用 `Command` 参数，包括方向、数据类型和参数语法。</span><span class="sxs-lookup"><span data-stu-id="290d6-116">Describes working with `Command` parameters, including direction, data types, and parameter syntax.</span></span>  
  
 [<span data-ttu-id="290d6-117">使用 CommandBuilder 生成命令</span><span class="sxs-lookup"><span data-stu-id="290d6-117">Generating Commands with CommandBuilders</span></span>](generating-commands-with-commandbuilders.md)  
 <span data-ttu-id="290d6-118">说明如何使用命令生成器为具有单表 SELECT 命令的 `DataAdapter` 自动生成 INSERT、UPDATE 和 DELETE 命令。</span><span class="sxs-lookup"><span data-stu-id="290d6-118">Describes how to use command builders to automatically generate INSERT, UPDATE, and DELETE commands for a `DataAdapter` that has a single-table SELECT command.</span></span>  
  
 [<span data-ttu-id="290d6-119">从数据库获取单一值</span><span class="sxs-lookup"><span data-stu-id="290d6-119">Obtaining a Single Value from a Database</span></span>](obtaining-a-single-value-from-a-database.md)  
 <span data-ttu-id="290d6-120">说明如何使用 `ExecuteScalar`对象的 `Command` 方法从数据库查询中返回单个值。</span><span class="sxs-lookup"><span data-stu-id="290d6-120">Describes how to use the `ExecuteScalar` method of a `Command` object to return a single value from a database query.</span></span>  
  
 [<span data-ttu-id="290d6-121">使用命令修改数据</span><span class="sxs-lookup"><span data-stu-id="290d6-121">Using Commands to Modify Data</span></span>](using-commands-to-modify-data.md)  
 <span data-ttu-id="290d6-122">说明如何使用数据提供程序来执行存储过程或数据定义语言 (DDL) 语句。</span><span class="sxs-lookup"><span data-stu-id="290d6-122">Describes how to use a data provider to execute stored procedures or data definition language (DDL) statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="290d6-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="290d6-123">See also</span></span>

- [<span data-ttu-id="290d6-124">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="290d6-124">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="290d6-125">数据集、数据表和数据视图</span><span class="sxs-lookup"><span data-stu-id="290d6-125">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)
- [<span data-ttu-id="290d6-126">连接数据源</span><span class="sxs-lookup"><span data-stu-id="290d6-126">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="290d6-127">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="290d6-127">ADO.NET Overview</span></span>](ado-net-overview.md)

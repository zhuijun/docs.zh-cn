---
title: 命令和参数
description: 了解如何使用每个 .NET Framework 数据提供程序的命令对象来运行命令并从数据源返回结果。
ms.date: 03/30/2017
ms.assetid: b623f810-d871-49a5-b0f5-078cc3c34db6
ms.openlocfilehash: c0baec4d6c3984cb50178c3aa7f9ed3878055bb6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287137"
---
# <a name="commands-and-parameters"></a>命令和参数
建立与数据源的连接后，可以使用 <xref:System.Data.Common.DbCommand> 对象来执行命令并从数据源中返回结果。 您可以使用命令构造函数之一为要使用的 .NET Framework 数据提供程序创建命令。 构造函数可以采用可选自变量，如要在数据源中执行的 SQL 语句、<xref:System.Data.Common.DbConnection> 对象或 <xref:System.Data.Common.DbTransaction> 对象。 您也可以将这些对象配置为命令的属性。 也可以使用 <xref:System.Data.Common.DbConnection.CreateCommand%2A> 对象的 `DbConnection` 方法创建用于特定连接的命令。 由命令执行的 SQL 语句可以使用 <xref:System.Data.Common.DbCommand.CommandText%2A> 属性进行配置。  
  
 随 .NET Framework 提供的每个 .NET Framework 数据提供程序都具有一个 `Command` 对象。 适用于 OLE DB 的 .NET Framework 数据提供程序包括一个 <xref:System.Data.OleDb.OleDbCommand> 对象，适用于 SQL Server 的 .NET Framework 数据提供程序包括一个 <xref:System.Data.SqlClient.SqlCommand> 对象，适用于 ODBC 的 .NET Framework 数据提供程序包括一个 <xref:System.Data.Odbc.OdbcCommand> 对象，适用于 Oracle 的 .NET Framework 数据提供程序包括一个 <xref:System.Data.OracleClient.OracleCommand> 对象。  
  
## <a name="in-this-section"></a>本节内容  
 [执行命令](executing-a-command.md)  
 说明 ADO.NET `Command` 对象以及如何使用该对象对数据源执行查询和命令。  
  
 [配置参数和参数数据类型](configuring-parameters-and-parameter-data-types.md)  
 说明如何使用 `Command` 参数，包括方向、数据类型和参数语法。  
  
 [使用 CommandBuilder 生成命令](generating-commands-with-commandbuilders.md)  
 说明如何使用命令生成器为具有单表 SELECT 命令的 `DataAdapter` 自动生成 INSERT、UPDATE 和 DELETE 命令。  
  
 [从数据库获取单一值](obtaining-a-single-value-from-a-database.md)  
 说明如何使用 `ExecuteScalar`对象的 `Command` 方法从数据库查询中返回单个值。  
  
 [使用命令修改数据](using-commands-to-modify-data.md)  
 说明如何使用数据提供程序来执行存储过程或数据定义语言 (DDL) 语句。  
  
## <a name="see-also"></a>另请参阅

- [DataAdapter 和 DataReader](dataadapters-and-datareaders.md)
- [数据集、数据表和数据视图](./dataset-datatable-dataview/index.md)
- [连接到数据源](connecting-to-a-data-source.md)
- [ADO.NET 概述](ado-net-overview.md)

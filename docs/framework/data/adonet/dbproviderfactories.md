---
title: DbProviderFactories
ms.date: 03/30/2017
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
ms.openlocfilehash: b5f2dbb687348afac98247cb21bae831dea26bfe
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183307"
---
# <a name="dbproviderfactories"></a><span data-ttu-id="68e36-102">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="68e36-102">DbProviderFactories</span></span>

<span data-ttu-id="68e36-103"><xref:System.Data.Common> 命名空间提供用于创建与特定数据源一起使用的 <xref:System.Data.Common.DbProviderFactory> 实例的类。</span><span class="sxs-lookup"><span data-stu-id="68e36-103">The <xref:System.Data.Common> namespace provides classes for creating <xref:System.Data.Common.DbProviderFactory> instances to work with specific data sources.</span></span> <span data-ttu-id="68e36-104">当创建 <xref:System.Data.Common.DbProviderFactory> 实例并向其传递有关数据提供程序的信息时，`DbProviderFactory` 可以根据为其提供的信息确定要返回的正确的强类型连接对象。</span><span class="sxs-lookup"><span data-stu-id="68e36-104">When you create a <xref:System.Data.Common.DbProviderFactory> instance and pass it information about the data provider, the `DbProviderFactory` can determine the correct, strongly typed connection object to return based on the information it has been provided.</span></span>  
  
 <span data-ttu-id="68e36-105">从 .NET Framework 4 开始，machine.config 文件中不再列出诸如 <xref:System.Data.Odbc>、<xref:System.Data.OleDb>、<xref:System.Data.SqlClient> 和 <xref:System.Data.OracleClient> 等数据提供程序，但会继续列出自定义提供程序。</span><span class="sxs-lookup"><span data-stu-id="68e36-105">Beginning in the .NET Framework version 4, data providers such as <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient>, and <xref:System.Data.OracleClient> are no longer listed in machine.config file, but custom providers will continue to be listed there.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="68e36-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="68e36-106">In This Section</span></span>  

 [<span data-ttu-id="68e36-107">工厂模型概述</span><span class="sxs-lookup"><span data-stu-id="68e36-107">Factory Model Overview</span></span>](factory-model-overview.md)  
 <span data-ttu-id="68e36-108">提供工厂设计样式和编程接口概述。</span><span class="sxs-lookup"><span data-stu-id="68e36-108">Provides an overview of the factory design pattern and programming interface.</span></span>  
  
 [<span data-ttu-id="68e36-109">获取 DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="68e36-109">Obtaining a DbProviderFactory</span></span>](obtaining-a-dbproviderfactory.md)  
 <span data-ttu-id="68e36-110">演示如何列出安装的数据提供程序以及如何从 <xref:System.Data.Common.DbConnection> 创建 `DbProviderFactory`。</span><span class="sxs-lookup"><span data-stu-id="68e36-110">Demonstrates how to list the installed data providers and create a <xref:System.Data.Common.DbConnection> from a `DbProviderFactory`.</span></span>  
  
 [<span data-ttu-id="68e36-111">DbConnection、DbCommand 和 DbException</span><span class="sxs-lookup"><span data-stu-id="68e36-111">DbConnection, DbCommand and DbException</span></span>](dbconnection-dbcommand-and-dbexception.md)  
 <span data-ttu-id="68e36-112">演示如何创建 <xref:System.Data.Common.DbCommand> 和 <xref:System.Data.Common.DbDataReader>，以及如何使用 <xref:System.Data.Common.DbException> 处理数据错误。</span><span class="sxs-lookup"><span data-stu-id="68e36-112">Demonstrates how to create a <xref:System.Data.Common.DbCommand> and <xref:System.Data.Common.DbDataReader>, and how to handle data errors using <xref:System.Data.Common.DbException>.</span></span>  
  
 [<span data-ttu-id="68e36-113">使用 DbDataAdapter 修改数据</span><span class="sxs-lookup"><span data-stu-id="68e36-113">Modifying Data with a DbDataAdapter</span></span>](modifying-data-with-a-dbdataadapter.md)  
 <span data-ttu-id="68e36-114">演示如何使用 <xref:System.Data.Common.DbCommandBuilder> 和 <xref:System.Data.Common.DbDataAdapter> 检索并修改数据。</span><span class="sxs-lookup"><span data-stu-id="68e36-114">Demonstrates how to use a <xref:System.Data.Common.DbCommandBuilder> with a <xref:System.Data.Common.DbDataAdapter> to retrieve and modify data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68e36-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="68e36-115">See also</span></span>

- [<span data-ttu-id="68e36-116">在 ADO.NET 中检索和修改数据</span><span class="sxs-lookup"><span data-stu-id="68e36-116">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="68e36-117">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="68e36-117">ADO.NET Overview</span></span>](ado-net-overview.md)

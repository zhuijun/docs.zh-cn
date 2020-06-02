---
title: 检索和修改数据
description: 在 .NET Framework 中，ADO.NET 中的数据提供程序充当应用程序和数据源之间的桥梁，用于读取和更新数据。
ms.date: 03/30/2017
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.openlocfilehash: f916324dc829526a5e6b0078021b09786755f666
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286606"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a><span data-ttu-id="92e04-103">在 ADO.NET 中检索和修改数据</span><span class="sxs-lookup"><span data-stu-id="92e04-103">Retrieving and Modifying Data in ADO.NET</span></span>
<span data-ttu-id="92e04-104">任何数据库应用程序的一项主要功能是连接数据源并检索数据源中包含的数据。</span><span class="sxs-lookup"><span data-stu-id="92e04-104">A primary function of any database application is connecting to a data source and retrieving the data that it contains.</span></span> <span data-ttu-id="92e04-105">ADO.NET 的 .NET Framework 数据提供程序充当应用程序和数据源之间的桥梁，使你能够执行命令以及使用**DataReader**或**DataAdapter**检索数据。</span><span class="sxs-lookup"><span data-stu-id="92e04-105">The .NET Framework data providers of ADO.NET serve as a bridge between an application and a data source, allowing you to execute commands as well as to retrieve data by using a **DataReader** or a **DataAdapter**.</span></span> <span data-ttu-id="92e04-106">任何数据库应用程序的一项关键功能是更新数据库中存储的数据的能力。</span><span class="sxs-lookup"><span data-stu-id="92e04-106">A key function of any database application is the ability to update the data that is stored in the database.</span></span> <span data-ttu-id="92e04-107">在 ADO.NET 中，更新数据涉及使用**DataAdapter**和和 <xref:System.Data.DataSet> **Command**对象; 它还可能涉及使用事务。</span><span class="sxs-lookup"><span data-stu-id="92e04-107">In ADO.NET, updating data involves using the **DataAdapter** and <xref:System.Data.DataSet>, and **Command** objects; and it may also involve using transactions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="92e04-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="92e04-108">In This Section</span></span>  
 [<span data-ttu-id="92e04-109">连接到数据源</span><span class="sxs-lookup"><span data-stu-id="92e04-109">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)  
 <span data-ttu-id="92e04-110">说明如何建立到数据源的连接及如何使用连接事件。</span><span class="sxs-lookup"><span data-stu-id="92e04-110">Describes how to establish a connection to a data source and how to work with connection events.</span></span>  
  
 [<span data-ttu-id="92e04-111">连接字符串</span><span class="sxs-lookup"><span data-stu-id="92e04-111">Connection Strings</span></span>](connection-strings.md)  
 <span data-ttu-id="92e04-112">包含说明使用连接字符串（包括连接字符串关键字、安全信息以及存储和检索连接字符串）的各个方面的主题。</span><span class="sxs-lookup"><span data-stu-id="92e04-112">Contains topics describing various aspects of using connection strings, including connection string keywords, security info, and storing and retrieving them.</span></span>  
  
 [<span data-ttu-id="92e04-113">连接池</span><span class="sxs-lookup"><span data-stu-id="92e04-113">Connection Pooling</span></span>](connection-pooling.md)  
 <span data-ttu-id="92e04-114">描述 .NET Framework 数据提供程序的连接池。</span><span class="sxs-lookup"><span data-stu-id="92e04-114">Describes connection pooling for the .NET Framework data providers.</span></span>  
  
 [<span data-ttu-id="92e04-115">命令和参数</span><span class="sxs-lookup"><span data-stu-id="92e04-115">Commands and Parameters</span></span>](commands-and-parameters.md)  
 <span data-ttu-id="92e04-116">包含说明如何创建命令和命令生成器、配置参数以及如何执行命令来检索和修改数据的主题。</span><span class="sxs-lookup"><span data-stu-id="92e04-116">Contains topics describing how to create commands and command builders, configure parameters, and how to execute commands to retrieve and modify data.</span></span>  
  
 [<span data-ttu-id="92e04-117">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="92e04-117">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)  
 <span data-ttu-id="92e04-118">包含说明 DataReader、DataAdapter、参数、处理 DataAdapter 事件和执行批操作的主题。</span><span class="sxs-lookup"><span data-stu-id="92e04-118">Contains topics describing DataReaders, DataAdapters, parameters, handling DataAdapter events and performing batch operations.</span></span>  
  
 [<span data-ttu-id="92e04-119">事务和并发性</span><span class="sxs-lookup"><span data-stu-id="92e04-119">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)  
 <span data-ttu-id="92e04-120">包含说明如何执行本地事务、分布式事务及使用开放式并发的主题。</span><span class="sxs-lookup"><span data-stu-id="92e04-120">Contains topics describing how to perform local transactions, distributed transactions, and work with optimistic concurrency.</span></span>  
  
 [<span data-ttu-id="92e04-121">检索标识或自动编号值</span><span class="sxs-lookup"><span data-stu-id="92e04-121">Retrieving Identity or Autonumber Values</span></span>](retrieving-identity-or-autonumber-values.md)  
 <span data-ttu-id="92e04-122">提供一个示例，该示例将为 SQL Server 表中的**标识**列或 Microsoft Access 表中的**Autonumber**字段生成的值映射到表中插入行的列。</span><span class="sxs-lookup"><span data-stu-id="92e04-122">Provides an example of mapping the values generated for an **identity** column in a SQL Server table or for an **Autonumber** field in a Microsoft Access table, to a column of an inserted row in a table.</span></span> <span data-ttu-id="92e04-123">讨论在 `DataTable` 中合并标识值。</span><span class="sxs-lookup"><span data-stu-id="92e04-123">Discusses merging identity values in a `DataTable`.</span></span>  
  
 [<span data-ttu-id="92e04-124">检索二进制数据</span><span class="sxs-lookup"><span data-stu-id="92e04-124">Retrieving Binary Data</span></span>](retrieving-binary-data.md)  
 <span data-ttu-id="92e04-125">介绍如何使用检索二进制数据或大数据结构 `CommandBehavior` 。`SequentialAccess`</span><span class="sxs-lookup"><span data-stu-id="92e04-125">Describes how to retrieve binary data or large data structures using `CommandBehavior`.`SequentialAccess`</span></span> <span data-ttu-id="92e04-126">修改的默认行为 `DataReader` 。</span><span class="sxs-lookup"><span data-stu-id="92e04-126">to modify the default behavior of a `DataReader`.</span></span>  
  
 [<span data-ttu-id="92e04-127">使用存储过程修改数据</span><span class="sxs-lookup"><span data-stu-id="92e04-127">Modifying Data with Stored Procedures</span></span>](modifying-data-with-stored-procedures.md)  
 <span data-ttu-id="92e04-128">说明如何使用存储过程的输入参数和输出参数在数据库中插入行，同时返回新标识值。</span><span class="sxs-lookup"><span data-stu-id="92e04-128">Describes how to use stored procedure input parameters and output parameters to insert a row in a database, returning a new identity value.</span></span>  
  
 [<span data-ttu-id="92e04-129">检索数据库架构信息</span><span class="sxs-lookup"><span data-stu-id="92e04-129">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)  
 <span data-ttu-id="92e04-130">说明如何获取可用数据库或编录、数据库中的表和视图、表存在的约束以及数据源中的其他架构信息。</span><span class="sxs-lookup"><span data-stu-id="92e04-130">Describes how to obtain available databases or catalogs, tables and views in a database, constraints that exist for tables, and other schema information from a data source.</span></span>  
  
 [<span data-ttu-id="92e04-131">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="92e04-131">DbProviderFactories</span></span>](dbproviderfactories.md)  
 <span data-ttu-id="92e04-132">描述提供程序工厂模型及说明如何在 `System.Data.Common` 命名空间中使用基类。</span><span class="sxs-lookup"><span data-stu-id="92e04-132">Describes the provider factory model and demonstrates how to use the base classes in the `System.Data.Common` namespace.</span></span>  
  
 [<span data-ttu-id="92e04-133">ADO.NET 中的数据跟踪</span><span class="sxs-lookup"><span data-stu-id="92e04-133">Data Tracing in ADO.NET</span></span>](data-tracing.md)  
 <span data-ttu-id="92e04-134">说明 ADO.NET 如何提供内置的数据跟踪功能。</span><span class="sxs-lookup"><span data-stu-id="92e04-134">Describes how ADO.NET provides built-in data tracing functionality.</span></span>  
  
 [<span data-ttu-id="92e04-135">性能计数器</span><span class="sxs-lookup"><span data-stu-id="92e04-135">Performance Counters</span></span>](performance-counters.md)  
 <span data-ttu-id="92e04-136">说明 `SqlClient` 和 `OracleClient` 可用的性能计数器。</span><span class="sxs-lookup"><span data-stu-id="92e04-136">Describes performance counters available for `SqlClient` and `OracleClient`.</span></span>  
  
 [<span data-ttu-id="92e04-137">异步编程</span><span class="sxs-lookup"><span data-stu-id="92e04-137">Asynchronous Programming</span></span>](asynchronous-programming.md)  
 <span data-ttu-id="92e04-138">介绍异步编程的 ADO.NET 支持。</span><span class="sxs-lookup"><span data-stu-id="92e04-138">Describes ADO.NET support for asynchronous programming.</span></span>  
  
 [<span data-ttu-id="92e04-139">SqlClient 流支持</span><span class="sxs-lookup"><span data-stu-id="92e04-139">SqlClient Streaming Support</span></span>](sqlclient-streaming-support.md)  
 <span data-ttu-id="92e04-140">讨论如何编写从 SQL Server 流式传输数据的应用程序，而无需将其完全加载到内存中。</span><span class="sxs-lookup"><span data-stu-id="92e04-140">Discusses how to write applications that stream data from SQL Server without having it fully loaded in memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92e04-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="92e04-141">See also</span></span>

- [<span data-ttu-id="92e04-142">ADO.NET 中的数据类型映射</span><span class="sxs-lookup"><span data-stu-id="92e04-142">Data Type Mappings in ADO.NET</span></span>](data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="92e04-143">数据集、数据表和数据视图</span><span class="sxs-lookup"><span data-stu-id="92e04-143">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)
- [<span data-ttu-id="92e04-144">保证 ADO.NET 应用程序的安全</span><span class="sxs-lookup"><span data-stu-id="92e04-144">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)
- [<span data-ttu-id="92e04-145">SQL Server 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="92e04-145">SQL Server and ADO.NET</span></span>](./sql/index.md)
- [<span data-ttu-id="92e04-146">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="92e04-146">ADO.NET Overview</span></span>](ado-net-overview.md)

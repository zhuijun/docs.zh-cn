---
title: SQL Server 和 ADO.NET
description: 了解用于 SQL Server 的 .NET Framework 数据提供程序的功能和行为，用于封装特定于数据库的协议。
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.openlocfilehash: eeb0ab69a68dfc2fc0faa1b4e833f80b307fffe5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286438"
---
# <a name="sql-server-and-adonet"></a><span data-ttu-id="63d03-103">SQL Server 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="63d03-103">SQL Server and ADO.NET</span></span>
<span data-ttu-id="63d03-104">本节描述适用于 SQL Server 的 .NET Framework 数据提供程序 (<xref:System.Data.SqlClient>) 特定的功能和行为。</span><span class="sxs-lookup"><span data-stu-id="63d03-104">This section describes features and behaviors that are specific to the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>).</span></span>  
  
 <span data-ttu-id="63d03-105"><xref:System.Data.SqlClient> 提供对 SQL Server 各版本的访问权限，这些版本封装有数据库特定的协议。</span><span class="sxs-lookup"><span data-stu-id="63d03-105"><xref:System.Data.SqlClient> provides access to versions of SQL Server, which encapsulates database-specific protocols.</span></span> <span data-ttu-id="63d03-106">该数据提供程序设计的功能与 OLE DB、ODBC 和 Oracle 的 .NET Framework 数据提供程序的功能类似。</span><span class="sxs-lookup"><span data-stu-id="63d03-106">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for OLE DB, ODBC, and Oracle.</span></span> <span data-ttu-id="63d03-107"><xref:System.Data.SqlClient> 包含一个表格格式数据流 (TDS) 分析程序，它用于直接与 SQL Server 通信。</span><span class="sxs-lookup"><span data-stu-id="63d03-107"><xref:System.Data.SqlClient> includes a tabular data stream (TDS) parser to communicate directly with SQL Server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="63d03-108">要使用 SQL Server .NET Framework 数据提供程序，应用程序必须引用 <xref:System.Data.SqlClient> 命名空间。</span><span class="sxs-lookup"><span data-stu-id="63d03-108">To use the .NET Framework Data Provider for SQL Server, an application must reference the <xref:System.Data.SqlClient> namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="63d03-109">本节内容</span><span class="sxs-lookup"><span data-stu-id="63d03-109">In This Section</span></span>  
 [<span data-ttu-id="63d03-110">SQL Server 安全性</span><span class="sxs-lookup"><span data-stu-id="63d03-110">SQL Server Security</span></span>](sql-server-security.md)  
 <span data-ttu-id="63d03-111">简要介绍 SQL Server 安全功能，以及创建面向 SQL Server 的安全 ADO.NET 应用程序的应用程序方案。</span><span class="sxs-lookup"><span data-stu-id="63d03-111">Provides an overview of SQL Server security features, and application scenarios for creating secure ADO.NET applications that target SQL Server.</span></span>  
  
 [<span data-ttu-id="63d03-112">SQL Server 数据类型和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="63d03-112">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)  
 <span data-ttu-id="63d03-113">描述如何使用 SQL Server 数据类型以及这些数据类型如何与 .NET Framework 数据类型进行交互。</span><span class="sxs-lookup"><span data-stu-id="63d03-113">Describes how to work with SQL Server data types and how they interact with .NET Framework data types.</span></span>  
  
 [<span data-ttu-id="63d03-114">SQL Server 二进制和大值数据</span><span class="sxs-lookup"><span data-stu-id="63d03-114">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)  
 <span data-ttu-id="63d03-115">介绍如何在 SQL Server 中使用大值数据。</span><span class="sxs-lookup"><span data-stu-id="63d03-115">Describes how to work with large value data in SQL Server.</span></span>  
  
 [<span data-ttu-id="63d03-116">ADO.NET 中的 SQL Server 数据操作</span><span class="sxs-lookup"><span data-stu-id="63d03-116">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)  
 <span data-ttu-id="63d03-117">介绍如何使用 SQL Server 中的数据。</span><span class="sxs-lookup"><span data-stu-id="63d03-117">Describes how to work with data in SQL Server.</span></span> <span data-ttu-id="63d03-118">包含有关大容量复制操作、MARS、异步操作和表值参数的部分。</span><span class="sxs-lookup"><span data-stu-id="63d03-118">Contains sections about bulk copy operations, MARS, asynchronous operations, and table-valued parameters.</span></span>  
  
 [<span data-ttu-id="63d03-119">SQL Server 功能和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="63d03-119">SQL Server Features and ADO.NET</span></span>](sql-server-features-and-adonet.md)  
 <span data-ttu-id="63d03-120">介绍对 ADO.NET 应用程序开发人员而言有用的 SQL Server 功能。</span><span class="sxs-lookup"><span data-stu-id="63d03-120">Describes SQL Server features that are useful for ADO.NET application developers.</span></span>  
  
 [<span data-ttu-id="63d03-121">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="63d03-121">LINQ to SQL</span></span>](./linq/index.md)  
 <span data-ttu-id="63d03-122">描述创建 LINQ to SQL 应用程序所需的基本构造块、进程和技术。</span><span class="sxs-lookup"><span data-stu-id="63d03-122">Describes the basic building blocks, processes, and techniques required for creating LINQ to SQL applications.</span></span>  
  
 <span data-ttu-id="63d03-123">有关 SQL Server 数据库引擎的完整文档，请参见你正在使用的 SQL Server 版本的 SQL Server 联机丛书。</span><span class="sxs-lookup"><span data-stu-id="63d03-123">For complete documentation of the SQL Server Database Engine, see SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 [<span data-ttu-id="63d03-124">QL Server 联机丛书</span><span class="sxs-lookup"><span data-stu-id="63d03-124">SQL Server Books Online</span></span>](/sql/sql-server/sql-server-technical-documentation)  
  
## <a name="see-also"></a><span data-ttu-id="63d03-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="63d03-125">See also</span></span>

- [<span data-ttu-id="63d03-126">保证 ADO.NET 应用程序的安全</span><span class="sxs-lookup"><span data-stu-id="63d03-126">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="63d03-127">ADO.NET 中的数据类型映射</span><span class="sxs-lookup"><span data-stu-id="63d03-127">Data Type Mappings in ADO.NET</span></span>](../data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="63d03-128">数据集、数据表和数据视图</span><span class="sxs-lookup"><span data-stu-id="63d03-128">DataSets, DataTables, and DataViews</span></span>](../dataset-datatable-dataview/index.md)
- [<span data-ttu-id="63d03-129">在 ADO.NET 中检索和修改数据</span><span class="sxs-lookup"><span data-stu-id="63d03-129">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="63d03-130">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="63d03-130">ADO.NET Overview</span></span>](../ado-net-overview.md)

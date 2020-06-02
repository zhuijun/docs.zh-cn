---
title: SQL Server 中的批量复制操作
description: 了解如何使用 SqlBulkCopy 类编写将大型文件大容量复制到 SQL Server 数据库中的表或视图中的托管代码解决方案。
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: 4f877836aa45efe162cce3c42cb5733f86deab2c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286515"
---
# <a name="bulk-copy-operations-in-sql-server"></a><span data-ttu-id="97e28-103">SQL Server 中的批量复制操作</span><span class="sxs-lookup"><span data-stu-id="97e28-103">Bulk Copy Operations in SQL Server</span></span>
<span data-ttu-id="97e28-104">Microsoft SQL Server 包含一个名为 bcp 的受欢迎的命令行实用工具，以便将较大文件快速大容量复制到 SQL Server 数据库的表或视图中  。</span><span class="sxs-lookup"><span data-stu-id="97e28-104">Microsoft SQL Server includes a popular command-line utility named **bcp** for quickly bulk copying large files into tables or views in SQL Server databases.</span></span> <span data-ttu-id="97e28-105"><xref:System.Data.SqlClient.SqlBulkCopy> 类允许你编写可提供类似功能的托管代码解决方案。</span><span class="sxs-lookup"><span data-stu-id="97e28-105">The <xref:System.Data.SqlClient.SqlBulkCopy> class allows you to write managed code solutions that provide similar functionality.</span></span> <span data-ttu-id="97e28-106">还可通过其他方法将数据加载到 SQL Server 表（例如 INSERT 语句），但 <xref:System.Data.SqlClient.SqlBulkCopy> 可提供显著的性能优势。</span><span class="sxs-lookup"><span data-stu-id="97e28-106">There are other ways to load data into a SQL Server table (INSERT statements, for example) but <xref:System.Data.SqlClient.SqlBulkCopy> offers a significant performance advantage over them.</span></span>  
  
 <span data-ttu-id="97e28-107"><xref:System.Data.SqlClient.SqlBulkCopy> 类可用于只将数据写入 SQL Server 表。</span><span class="sxs-lookup"><span data-stu-id="97e28-107">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="97e28-108">但是，数据源不限于 SQL Server；可以使用任何数据源，只要数据可以加载到 <xref:System.Data.DataTable> 实例或使用 <xref:System.Data.IDataReader> 实例读取即可。</span><span class="sxs-lookup"><span data-stu-id="97e28-108">But the data source is not limited to SQL Server; any data source can be used, as long as the data can be loaded to a <xref:System.Data.DataTable> instance or read with a <xref:System.Data.IDataReader> instance.</span></span>  
  
 <span data-ttu-id="97e28-109">使用 <xref:System.Data.SqlClient.SqlBulkCopy> 类，你可以执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="97e28-109">Using the <xref:System.Data.SqlClient.SqlBulkCopy> class, you can perform:</span></span>  
  
- <span data-ttu-id="97e28-110">单次大容量复制操作</span><span class="sxs-lookup"><span data-stu-id="97e28-110">A single bulk copy operation</span></span>  
  
- <span data-ttu-id="97e28-111">多次大容量复制操作</span><span class="sxs-lookup"><span data-stu-id="97e28-111">Multiple bulk copy operations</span></span>  
  
- <span data-ttu-id="97e28-112">事务中的大容量复制操作</span><span class="sxs-lookup"><span data-stu-id="97e28-112">A bulk copy operation within a transaction</span></span>  
  
> [!NOTE]
> <span data-ttu-id="97e28-113">在使用 .NET Framework 1.1 版或更低版本时（不支持 <xref:System.Data.SqlClient.SqlBulkCopy> 类），可以使用 <xref:System.Data.SqlClient.SqlCommand> 对象执行 SQL Server Transact-SQL BULK INSERT 语句\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="97e28-113">When using .NET Framework version 1.1 or earlier (which does not support the <xref:System.Data.SqlClient.SqlBulkCopy> class), you can execute the SQL Server Transact-SQL **BULK INSERT** statement using the <xref:System.Data.SqlClient.SqlCommand> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="97e28-114">本节内容</span><span class="sxs-lookup"><span data-stu-id="97e28-114">In This Section</span></span>  
 [<span data-ttu-id="97e28-115">大容量复制示例设置</span><span class="sxs-lookup"><span data-stu-id="97e28-115">Bulk Copy Example Setup</span></span>](bulk-copy-example-setup.md)  
 <span data-ttu-id="97e28-116">介绍用于大容量复制示例的表，并提供用于在 AdventureWorks 数据库中创建表的 SQL 脚本。</span><span class="sxs-lookup"><span data-stu-id="97e28-116">Describes the tables used in the bulk copy examples and provides SQL scripts for creating the tables in the AdventureWorks database.</span></span>  
  
 [<span data-ttu-id="97e28-117">单次大容量复制操作</span><span class="sxs-lookup"><span data-stu-id="97e28-117">Single Bulk Copy Operations</span></span>](single-bulk-copy-operations.md)  
 <span data-ttu-id="97e28-118">介绍如何使用 <xref:System.Data.SqlClient.SqlBulkCopy> 类将单个大容量数据复制到 SQL Server 实例，以及如何使用 Transact-SQL 语句和 <xref:System.Data.SqlClient.SqlCommand> 类执行大容量复制操作。</span><span class="sxs-lookup"><span data-stu-id="97e28-118">Describes how to do a single bulk copy of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class, and how to perform the bulk copy operation using Transact-SQL statements and the <xref:System.Data.SqlClient.SqlCommand> class.</span></span>  
  
 [<span data-ttu-id="97e28-119">多个大容量复制操作</span><span class="sxs-lookup"><span data-stu-id="97e28-119">Multiple Bulk Copy Operations</span></span>](multiple-bulk-copy-operations.md)  
 <span data-ttu-id="97e28-120">介绍如何使用 <xref:System.Data.SqlClient.SqlBulkCopy> 类在 SQL Server 的实例中执行多次大容量复制操作。</span><span class="sxs-lookup"><span data-stu-id="97e28-120">Describes how to do multiple bulk copy operations of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span>  
  
 [<span data-ttu-id="97e28-121">事务和大容量复制操作</span><span class="sxs-lookup"><span data-stu-id="97e28-121">Transaction and Bulk Copy Operations</span></span>](transaction-and-bulk-copy-operations.md)  
 <span data-ttu-id="97e28-122">介绍如何在事务中执行大容量复制操作，包括如何提交或回滚事务。</span><span class="sxs-lookup"><span data-stu-id="97e28-122">Describes how to perform a bulk copy operation within a transaction, including how to commit or rollback the transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97e28-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="97e28-123">See also</span></span>

- [<span data-ttu-id="97e28-124">SQL Server 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="97e28-124">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="97e28-125">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="97e28-125">ADO.NET Overview</span></span>](../ado-net-overview.md)

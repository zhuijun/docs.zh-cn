---
title: 连接池
description: 了解连接池，一种优化技术，ADO.NET 使用它来最大程度地降低打开到数据源的连接的成本。
ms.date: 03/30/2017
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
ms.openlocfilehash: f16b3ba733cce4a1efe72e3f4eee48a431a96fb7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198712"
---
# <a name="connection-pooling"></a><span data-ttu-id="a09bd-103">连接池</span><span class="sxs-lookup"><span data-stu-id="a09bd-103">Connection Pooling</span></span>

<span data-ttu-id="a09bd-104">连接到数据源可能需要很长时间。</span><span class="sxs-lookup"><span data-stu-id="a09bd-104">Connecting to a data source can be time consuming.</span></span> <span data-ttu-id="a09bd-105">为了最大程度地降低打开连接的成本，ADO.NET 使用一种称为 *连接池*的优化技术，这会最大程度地降低重复打开和关闭连接的成本。</span><span class="sxs-lookup"><span data-stu-id="a09bd-105">To minimize the cost of opening connections, ADO.NET uses an optimization technique called *connection pooling*, which minimizes the cost of repeatedly opening and closing connections.</span></span> <span data-ttu-id="a09bd-106">.NET Framework 数据提供程序处理连接池的方式有所不同。</span><span class="sxs-lookup"><span data-stu-id="a09bd-106">Connection pooling is handled differently for the .NET Framework data providers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a09bd-107">本节内容</span><span class="sxs-lookup"><span data-stu-id="a09bd-107">In This Section</span></span>  

 [<span data-ttu-id="a09bd-108">SQL Server 连接池 (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="a09bd-108">SQL Server Connection Pooling (ADO.NET)</span></span>](sql-server-connection-pooling.md)  
 <span data-ttu-id="a09bd-109">提供连接池的概述，并介绍连接池在 SQL Server 中的工作原理。</span><span class="sxs-lookup"><span data-stu-id="a09bd-109">Provides an overview of connection pooling and describes how connection pooling works in SQL Server.</span></span>  
  
 [<span data-ttu-id="a09bd-110">OLE DB、ODBC 和 Oracle 连接池</span><span class="sxs-lookup"><span data-stu-id="a09bd-110">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)  
 <span data-ttu-id="a09bd-111">说明适用于 OLE DB 的 .NET Framework 数据提供程序、适用于 ODBC 的 .NET Framework 数据提供程序和适用于 Oracle 的 .NET Framework 数据提供程序的连接池。</span><span class="sxs-lookup"><span data-stu-id="a09bd-111">Describes connection pooling for the .NET Framework Data Provider for OLE DB, the .NET Framework Data Provider for ODBC, and the .NET Framework Data Provider for Oracle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a09bd-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="a09bd-112">See also</span></span>

- [<span data-ttu-id="a09bd-113">在 ADO.NET 中检索和修改数据</span><span class="sxs-lookup"><span data-stu-id="a09bd-113">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="a09bd-114">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="a09bd-114">ADO.NET Overview</span></span>](ado-net-overview.md)

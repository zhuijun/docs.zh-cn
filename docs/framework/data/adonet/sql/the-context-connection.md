---
title: 上下文连接
ms.date: 03/30/2017
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
ms.openlocfilehash: 85b303d62b619a8139ca56b23cacd3411cebc17b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91188845"
---
# <a name="the-context-connection"></a><span data-ttu-id="312f2-102">上下文连接</span><span class="sxs-lookup"><span data-stu-id="312f2-102">The Context Connection</span></span>

<span data-ttu-id="312f2-103">内部数据访问问题是一种非常常见的情况。</span><span class="sxs-lookup"><span data-stu-id="312f2-103">The problem of internal data access is a fairly common scenario.</span></span> <span data-ttu-id="312f2-104">即您希望访问正在执行公共语言运行时 (CLR) 存储过程或函数的相同服务器。</span><span class="sxs-lookup"><span data-stu-id="312f2-104">That is, you wish to access the same server on which your common language runtime (CLR) stored procedure or function is executing.</span></span> <span data-ttu-id="312f2-105">一种选择是使用 <xref:System.Data.SqlClient.SqlConnection> 创建连接，指定指向本地服务器的连接字符串，然后打开该连接。</span><span class="sxs-lookup"><span data-stu-id="312f2-105">One option is to create a connection using <xref:System.Data.SqlClient.SqlConnection>, specify a connection string that points to the local server, and open the connection.</span></span> <span data-ttu-id="312f2-106">这要求指定登录凭据。</span><span class="sxs-lookup"><span data-stu-id="312f2-106">This requires specifying credentials for logging in.</span></span> <span data-ttu-id="312f2-107">连接与存储过程或函数处于不同的数据库会话中，它可能具有不同的 `SET` 选项，位于单独的事务中，找不到临时表等等。</span><span class="sxs-lookup"><span data-stu-id="312f2-107">The connection is in a different database session than the stored procedure or function, it may have different `SET` options, it is in a separate transaction, it does not see your temporary tables, and so on.</span></span> <span data-ttu-id="312f2-108">如果托管存储过程或函数代码正在 SQL Server 进程中执行，则是因为有人连接到了该服务器并执行了 SQL 语句调用它。</span><span class="sxs-lookup"><span data-stu-id="312f2-108">If your managed stored procedure or function code is executing in the SQL Server process, it is because someone connected to that server and executed a SQL statement to invoke it.</span></span> <span data-ttu-id="312f2-109">您可能希望在该连接上下文中执行存储过程或函数，以及其事务、`SET` 选项等。</span><span class="sxs-lookup"><span data-stu-id="312f2-109">You probably want the stored procedure or function to execute in the context of that connection, along with its transaction, `SET` options, and so on.</span></span> <span data-ttu-id="312f2-110">这称为上下文连接。</span><span class="sxs-lookup"><span data-stu-id="312f2-110">This is called the context connection.</span></span>  
  
 <span data-ttu-id="312f2-111">利用上下文连接，您可以在首先调用代码的同一上下文中执行 Transact-SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="312f2-111">The context connection lets you execute Transact-SQL statements in the same context that your code was invoked in the first place.</span></span> <span data-ttu-id="312f2-112">有关更多详细信息，请参见您正在使用的 SQL Server 版本的“SQL Server 联机丛书”版本。</span><span class="sxs-lookup"><span data-stu-id="312f2-112">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="312f2-113">**SQL Server 文档**</span><span class="sxs-lookup"><span data-stu-id="312f2-113">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="312f2-114">上下文连接</span><span class="sxs-lookup"><span data-stu-id="312f2-114">The Context Connection</span></span>](/sql/relational-databases/clr-integration/data-access/context-connection)  
  
## <a name="see-also"></a><span data-ttu-id="312f2-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="312f2-115">See also</span></span>

- [<span data-ttu-id="312f2-116">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="312f2-116">ADO.NET Overview</span></span>](../ado-net-overview.md)

---
title: 从数据库获取单一值
description: 了解如何在 ADO.NET 中返回单个值。 此示例代码返回已插入记录的标识列值。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: 9ce29bc1321814bd60cfaacd222fc55a3fbf12ed
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150721"
---
# <a name="obtaining-a-single-value-from-a-database"></a><span data-ttu-id="963e8-104">从数据库获取单一值</span><span class="sxs-lookup"><span data-stu-id="963e8-104">Obtaining a Single Value from a Database</span></span>

<span data-ttu-id="963e8-105">您可能需要返回只是单个值的数据库信息，而不需要返回表或数据流形式的数据库信息。</span><span class="sxs-lookup"><span data-stu-id="963e8-105">You may need to return database information that is simply a single value rather than in the form of a table or data stream.</span></span> <span data-ttu-id="963e8-106">例如，您可能希望返回聚合函数的结果，如计数 (\*) 、SUM (Price) 或 AVG (数量) 。</span><span class="sxs-lookup"><span data-stu-id="963e8-106">For example, you may want to return the result of an aggregate function such as COUNT(\*), SUM(Price), or AVG(Quantity).</span></span> <span data-ttu-id="963e8-107">**Command**对象提供使用**ExecuteScalar**方法返回单个值的功能。</span><span class="sxs-lookup"><span data-stu-id="963e8-107">The **Command** object provides the capability to return single values using the **ExecuteScalar** method.</span></span> <span data-ttu-id="963e8-108">**ExecuteScalar**方法以标量值的形式返回结果集第一行的第一列的值。</span><span class="sxs-lookup"><span data-stu-id="963e8-108">The **ExecuteScalar** method returns, as a scalar value, the value of the first column of the first row of the result set.</span></span>  
  
 <span data-ttu-id="963e8-109">下面的代码示例使用 <xref:System.Data.SqlClient.SqlCommand> 在数据库中插入一个新值。</span><span class="sxs-lookup"><span data-stu-id="963e8-109">The following code example inserts a new value in the database using a <xref:System.Data.SqlClient.SqlCommand>.</span></span> <span data-ttu-id="963e8-110">使用 <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> 方法可返回已插入记录的标识列值。</span><span class="sxs-lookup"><span data-stu-id="963e8-110">The <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> method is used to return the identity column value for the inserted record.</span></span>  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="963e8-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="963e8-111">See also</span></span>

- [<span data-ttu-id="963e8-112">命令和参数</span><span class="sxs-lookup"><span data-stu-id="963e8-112">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="963e8-113">执行命令</span><span class="sxs-lookup"><span data-stu-id="963e8-113">Executing a Command</span></span>](executing-a-command.md)
- [<span data-ttu-id="963e8-114">DbConnection、DbCommand 和 DbException</span><span class="sxs-lookup"><span data-stu-id="963e8-114">DbConnection, DbCommand and DbException</span></span>](dbconnection-dbcommand-and-dbexception.md)
- [<span data-ttu-id="963e8-115">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="963e8-115">ADO.NET Overview</span></span>](ado-net-overview.md)

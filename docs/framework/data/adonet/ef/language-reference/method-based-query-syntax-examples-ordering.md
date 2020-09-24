---
title: 基于方法的查询语法示例：中间件排序
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5d21b178-d731-471a-8534-1f8184a2ef06
ms.openlocfilehash: 02889fb4172d24634cdcb1c8384a804b2ce1a0e8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191926"
---
# <a name="method-based-query-syntax-examples-ordering"></a><span data-ttu-id="f8911-102">基于方法的查询语法示例：中间件排序</span><span class="sxs-lookup"><span data-stu-id="f8911-102">Method-Based Query Syntax Examples: Ordering</span></span>

<span data-ttu-id="f8911-103">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.ThenBy%2A> 方法通过使用基于方法的查询语法来查询 [AdventureWorks 销售模型](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) 。</span><span class="sxs-lookup"><span data-stu-id="f8911-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ThenBy%2A> method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="f8911-104">这些示例中使用的 AdventureWorks 销售模型从 AdventureWorks 示例数据库中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 等表生成。</span><span class="sxs-lookup"><span data-stu-id="f8911-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="f8911-105">本主题中的示例使用以下 `using` / `Imports` 语句：</span><span class="sxs-lookup"><span data-stu-id="f8911-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="thenby"></a><span data-ttu-id="f8911-106">ThenBy</span><span class="sxs-lookup"><span data-stu-id="f8911-106">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="f8911-107">示例</span><span class="sxs-lookup"><span data-stu-id="f8911-107">Example</span></span>  

 <span data-ttu-id="f8911-108">采用基于方法的查询语法的以下示例使用 <xref:System.Linq.Queryable.OrderBy%2A> 和 <xref:System.Linq.Queryable.ThenBy%2A> 以返回先按姓氏后按名字排序的联系人列表。</span><span class="sxs-lookup"><span data-stu-id="f8911-108">The following example in method-based query syntax uses <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenBy%2A> to return a list of contacts ordered by last name and then by first name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby_mq)]
 [!code-vb[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby_mq)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="f8911-109">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="f8911-109">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="f8911-110">示例</span><span class="sxs-lookup"><span data-stu-id="f8911-110">Example</span></span>  

 <span data-ttu-id="f8911-111">以下示例使用 <xref:System.Linq.Queryable.OrderBy%2A> 和 <xref:System.Linq.Queryable.ThenByDescending%2A> 方法以首先按标价排序，然后执行产品名称的降序排序。</span><span class="sxs-lookup"><span data-stu-id="f8911-111">The following example uses the <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenByDescending%2A> methods to first sort by list price, and then perform a descending sort of the product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescending_mq)]
 [!code-vb[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescending_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="f8911-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="f8911-112">See also</span></span>

- [<span data-ttu-id="f8911-113">LINQ to Entities 中的查询</span><span class="sxs-lookup"><span data-stu-id="f8911-113">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)

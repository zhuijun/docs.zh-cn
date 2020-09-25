---
title: 查询表达式语法示例：分区
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e41aed0-3be9-4f75-98de-860a85552a3c
ms.openlocfilehash: 548701f375b550e3a533a012bf34dc686ed42ac1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203600"
---
# <a name="query-expression-syntax-examples-partitioning"></a><span data-ttu-id="fffff-102">查询表达式语法示例：分区</span><span class="sxs-lookup"><span data-stu-id="fffff-102">Query Expression Syntax Examples: Partitioning</span></span>

<span data-ttu-id="fffff-103">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.Skip%2A> 和 <xref:System.Linq.Enumerable.Take%2A> 方法通过使用查询表达式语法来查询 [AdventureWorks 销售模型](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) 。</span><span class="sxs-lookup"><span data-stu-id="fffff-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="fffff-104">这些示例中使用的 AdventureWorks 销售模型从 AdventureWorks 示例数据库中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 等表生成。</span><span class="sxs-lookup"><span data-stu-id="fffff-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="fffff-105">本主题中的示例使用以下 `using` / `Imports` 语句：</span><span class="sxs-lookup"><span data-stu-id="fffff-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a><span data-ttu-id="fffff-106">跳过</span><span class="sxs-lookup"><span data-stu-id="fffff-106">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="fffff-107">示例</span><span class="sxs-lookup"><span data-stu-id="fffff-107">Example</span></span>  

 <span data-ttu-id="fffff-108">以下示例使用 <xref:System.Linq.Enumerable.Skip%2A> 方法以获取 Seattle 的前两个地址之外的所有地址。</span><span class="sxs-lookup"><span data-stu-id="fffff-108">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="fffff-109">Take</span><span class="sxs-lookup"><span data-stu-id="fffff-109">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="fffff-110">示例</span><span class="sxs-lookup"><span data-stu-id="fffff-110">Example</span></span>  

 <span data-ttu-id="fffff-111">以下示例使用 <xref:System.Linq.Enumerable.Take%2A> 方法以获取 Seattle 的前三个地址。</span><span class="sxs-lookup"><span data-stu-id="fffff-111">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="fffff-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="fffff-112">See also</span></span>

- [<span data-ttu-id="fffff-113">LINQ to Entities 中的查询</span><span class="sxs-lookup"><span data-stu-id="fffff-113">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)

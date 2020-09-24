---
title: 如何：以内联方式调用用户定义的函数
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
ms.openlocfilehash: 24b23c436fd7d4d5f3fdd0c364c0bdaf6feb8d1b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161342"
---
# <a name="how-to-call-user-defined-functions-inline"></a><span data-ttu-id="cabc2-102">如何：以内联方式调用用户定义的函数</span><span class="sxs-lookup"><span data-stu-id="cabc2-102">How to: Call User-Defined Functions Inline</span></span>

<span data-ttu-id="cabc2-103">尽管您可以内联调用用户定义的函数，但延迟执行的查询中包含的函数直到此查询执行时才会执行。</span><span class="sxs-lookup"><span data-stu-id="cabc2-103">Although you can call user-defined functions inline, functions that are included in a query whose execution is deferred are not executed until the query is executed.</span></span> <span data-ttu-id="cabc2-104">有关详细信息，请参阅 [LINQ 查询简介 (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="cabc2-104">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="cabc2-105">当您在查询外部调用同一函数时，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 会用方法调用表达式创建一个简单查询。</span><span class="sxs-lookup"><span data-stu-id="cabc2-105">When you call the same function outside a query, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates a simple query from the method call expression.</span></span> <span data-ttu-id="cabc2-106">下面是相应的 SQL 语法（`@p0` 参数绑定到传入的常量）：</span><span class="sxs-lookup"><span data-stu-id="cabc2-106">The following is the SQL syntax (the parameter `@p0` is bound to the constant passed in):</span></span>  
  
```sql  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="cabc2-107">会创建如下内容：</span><span class="sxs-lookup"><span data-stu-id="cabc2-107">creates the following:</span></span>  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="cabc2-108">示例</span><span class="sxs-lookup"><span data-stu-id="cabc2-108">Example</span></span>  

 <span data-ttu-id="cabc2-109">在下面的 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查询中，您可以看到对生成的用户定义函数方法 `ReverseCustName` 的内联调用。</span><span class="sxs-lookup"><span data-stu-id="cabc2-109">In the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query, you can see an inline call to the generated user-defined function method `ReverseCustName`.</span></span> <span data-ttu-id="cabc2-110">此函数不会立即执行，这是因为查询会延迟执行。</span><span class="sxs-lookup"><span data-stu-id="cabc2-110">The function is not executed immediately because query execution is deferred.</span></span> <span data-ttu-id="cabc2-111">为此查询生成的 SQL 会转换成对数据库中用户定义函数的调用（请参见此查询后面的 SQL 代码）。</span><span class="sxs-lookup"><span data-stu-id="cabc2-111">The SQL built for this query translates to a call to the user-defined function in the database (see the SQL code following the query).</span></span>  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```sql  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a><span data-ttu-id="cabc2-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="cabc2-112">See also</span></span>

- [<span data-ttu-id="cabc2-113">用户定义函数</span><span class="sxs-lookup"><span data-stu-id="cabc2-113">User-Defined Functions</span></span>](user-defined-functions.md)

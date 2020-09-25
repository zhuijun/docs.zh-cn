---
title: 返回两个序列的并集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: 0fe32d8c3c37e99a50ca03262dc6184337b4450e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200194"
---
# <a name="return-the-set-union-of-two-sequences"></a><span data-ttu-id="1bb93-102">返回两个序列的并集</span><span class="sxs-lookup"><span data-stu-id="1bb93-102">Return the Set Union of Two Sequences</span></span>

<span data-ttu-id="1bb93-103">使用 <xref:System.Linq.Queryable.Union%2A> 运算符可返回两个序列的并集。</span><span class="sxs-lookup"><span data-stu-id="1bb93-103">Use the <xref:System.Linq.Queryable.Union%2A> operator to return the set union of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bb93-104">示例</span><span class="sxs-lookup"><span data-stu-id="1bb93-104">Example</span></span>  

 <span data-ttu-id="1bb93-105">此示例使用 <xref:System.Linq.Queryable.Union%2A> 返回有或的所有国家/地区的序列 `Customers` `Employees` 。</span><span class="sxs-lookup"><span data-stu-id="1bb93-105">This example uses <xref:System.Linq.Queryable.Union%2A> to return a sequence of all countries/regions in which there are either `Customers` or `Employees`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 <span data-ttu-id="1bb93-106">在中 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ， <xref:System.Linq.Queryable.Union%2A> 运算符是为多重集定义的，因为多重集的无序串联 (实际上是 [`UNION ALL`](/sql/t-sql/language-elements/set-operators-union-transact-sql) SQL) 中子句的结果。</span><span class="sxs-lookup"><span data-stu-id="1bb93-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Union%2A> operator is defined for multisets as the unordered concatenation of the multisets (effectively the result of the [`UNION ALL`](/sql/t-sql/language-elements/set-operators-union-transact-sql) clause in SQL).</span></span>

<span data-ttu-id="1bb93-107">有关详细信息和示例，请参阅 <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="1bb93-107">For more info and examples, see <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1bb93-108">请参阅</span><span class="sxs-lookup"><span data-stu-id="1bb93-108">See also</span></span>

- [<span data-ttu-id="1bb93-109">查询示例</span><span class="sxs-lookup"><span data-stu-id="1bb93-109">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="1bb93-110">标准查询运算符转换</span><span class="sxs-lookup"><span data-stu-id="1bb93-110">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)

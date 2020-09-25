---
title: 返回两个序列的交集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
ms.openlocfilehash: 421ec544345e41f910bf80c855a3a6b4de1c46a6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200220"
---
# <a name="return-the-set-intersection-of-two-sequences"></a><span data-ttu-id="4a662-102">返回两个序列的交集</span><span class="sxs-lookup"><span data-stu-id="4a662-102">Return the Set Intersection of Two Sequences</span></span>

<span data-ttu-id="4a662-103">使用 <xref:System.Linq.Queryable.Intersect%2A> 运算符可返回两个序列的交集。</span><span class="sxs-lookup"><span data-stu-id="4a662-103">Use the <xref:System.Linq.Queryable.Intersect%2A> operator to return the set intersection of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a662-104">示例</span><span class="sxs-lookup"><span data-stu-id="4a662-104">Example</span></span>  

 <span data-ttu-id="4a662-105">此示例使用 <xref:System.Linq.Queryable.Intersect%2A> 返回和居住的所有国家/地区的序列 `Customers` `Employees` 。</span><span class="sxs-lookup"><span data-stu-id="4a662-105">This example uses <xref:System.Linq.Queryable.Intersect%2A> to return a sequence of all countries/regions in which both `Customers` and `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 <span data-ttu-id="4a662-106">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，<xref:System.Linq.Queryable.Intersect%2A> 运算仅对集合而言是定义完善的。</span><span class="sxs-lookup"><span data-stu-id="4a662-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Intersect%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="4a662-107">针对多重集的语义尚未定义。</span><span class="sxs-lookup"><span data-stu-id="4a662-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a662-108">请参阅</span><span class="sxs-lookup"><span data-stu-id="4a662-108">See also</span></span>

- [<span data-ttu-id="4a662-109">查询示例</span><span class="sxs-lookup"><span data-stu-id="4a662-109">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="4a662-110">标准查询运算符转换</span><span class="sxs-lookup"><span data-stu-id="4a662-110">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)

---
title: 返回两个序列之间的差集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 49a8d22377ef1f7d0fde16880a82002754e1bbc4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200324"
---
# <a name="return-the-set-difference-between-two-sequences"></a><span data-ttu-id="ca87b-102">返回两个序列之间的差集</span><span class="sxs-lookup"><span data-stu-id="ca87b-102">Return the Set Difference Between Two Sequences</span></span>

<span data-ttu-id="ca87b-103">使用 <xref:System.Linq.Queryable.Except%2A> 运算符可返回两个序列之间的差集。</span><span class="sxs-lookup"><span data-stu-id="ca87b-103">Use the <xref:System.Linq.Queryable.Except%2A> operator to return the set difference between two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca87b-104">示例</span><span class="sxs-lookup"><span data-stu-id="ca87b-104">Example</span></span>  

 <span data-ttu-id="ca87b-105">此示例使用 <xref:System.Linq.Queryable.Except%2A> 返回 `Customers` 居住但不居住的所有国家/地区的序列 `Employees` 。</span><span class="sxs-lookup"><span data-stu-id="ca87b-105">This example uses <xref:System.Linq.Queryable.Except%2A> to return a sequence of all countries/regions in which `Customers` live but in which no `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 <span data-ttu-id="ca87b-106">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，<xref:System.Linq.Queryable.Except%2A> 运算仅对集合而言是定义完善的。</span><span class="sxs-lookup"><span data-stu-id="ca87b-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Except%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="ca87b-107">针对多重集的语义尚未定义。</span><span class="sxs-lookup"><span data-stu-id="ca87b-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca87b-108">请参阅</span><span class="sxs-lookup"><span data-stu-id="ca87b-108">See also</span></span>

- [<span data-ttu-id="ca87b-109">查询示例</span><span class="sxs-lookup"><span data-stu-id="ca87b-109">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="ca87b-110">标准查询运算符转换</span><span class="sxs-lookup"><span data-stu-id="ca87b-110">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)

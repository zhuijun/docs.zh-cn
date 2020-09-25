---
title: 返回序列中的第一个元素
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: 4506ef1a79c8f7e77160df4d55d0f93ee79f5a41
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200337"
---
# <a name="return-the-first-element-in-a-sequence"></a><span data-ttu-id="1f230-102">返回序列中的第一个元素</span><span class="sxs-lookup"><span data-stu-id="1f230-102">Return the First Element in a Sequence</span></span>

<span data-ttu-id="1f230-103">使用 <xref:System.Linq.Enumerable.First%2A> 运算符可返回序列中的第一个元素。</span><span class="sxs-lookup"><span data-stu-id="1f230-103">Use the <xref:System.Linq.Enumerable.First%2A> operator to return the first element in a sequence.</span></span> <span data-ttu-id="1f230-104">使用 <xref:System.Linq.Enumerable.First%2A> 的查询是立即执行的。</span><span class="sxs-lookup"><span data-stu-id="1f230-104">Queries that use <xref:System.Linq.Enumerable.First%2A> are executed immediately.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="1f230-105">不支持 <xref:System.Linq.Enumerable.Last%2A> 运算符。</span><span class="sxs-lookup"><span data-stu-id="1f230-105">does not support the <xref:System.Linq.Enumerable.Last%2A> operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f230-106">示例</span><span class="sxs-lookup"><span data-stu-id="1f230-106">Example</span></span>  

 <span data-ttu-id="1f230-107">下面的代码查找表中的第一个 `Shipper`：</span><span class="sxs-lookup"><span data-stu-id="1f230-107">The following code finds the first `Shipper` in a table:</span></span>  
  
 <span data-ttu-id="1f230-108">如果您对 Northwind 示例数据库运行此查询，则结果为</span><span class="sxs-lookup"><span data-stu-id="1f230-108">If you run this query against the Northwind sample database, the results are</span></span>  
  
 <span data-ttu-id="1f230-109">`ID = 1, Company = Speedy Express`.</span><span class="sxs-lookup"><span data-stu-id="1f230-109">`ID = 1, Company = Speedy Express`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="1f230-110">示例</span><span class="sxs-lookup"><span data-stu-id="1f230-110">Example</span></span>  

 <span data-ttu-id="1f230-111">下面的代码查找具有 `Customer` BONAP 的单个 `CustomerID`。</span><span class="sxs-lookup"><span data-stu-id="1f230-111">The following code finds the single `Customer` that has the `CustomerID` BONAP.</span></span>  
  
 <span data-ttu-id="1f230-112">如果您对 Northwind 示例数据库运行此查询，则结果为 `ID = BONAP, Contact = Laurence Lebihan`。</span><span class="sxs-lookup"><span data-stu-id="1f230-112">If you run this query against the Northwind sample database, the results are `ID = BONAP, Contact = Laurence Lebihan`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="1f230-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="1f230-113">See also</span></span>

- [<span data-ttu-id="1f230-114">查询示例</span><span class="sxs-lookup"><span data-stu-id="1f230-114">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="1f230-115">下载示例数据库</span><span class="sxs-lookup"><span data-stu-id="1f230-115">Downloading Sample Databases</span></span>](downloading-sample-databases.md)

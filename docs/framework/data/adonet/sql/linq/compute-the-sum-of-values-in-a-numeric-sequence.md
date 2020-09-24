---
title: 计算数值序列中值的和
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
ms.openlocfilehash: 3d160e2cce5f3e0a7eea305657260b6fa4ded7fe
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164436"
---
# <a name="compute-the-sum-of-values-in-a-numeric-sequence"></a><span data-ttu-id="f9dde-102">计算数值序列中值的和</span><span class="sxs-lookup"><span data-stu-id="f9dde-102">Compute the Sum of Values in a Numeric Sequence</span></span>

<span data-ttu-id="f9dde-103">使用 <xref:System.Linq.Enumerable.Sum%2A> 运算符可以计算序列中数值的和。</span><span class="sxs-lookup"><span data-stu-id="f9dde-103">Use the <xref:System.Linq.Enumerable.Sum%2A> operator to compute the sum of numeric values in a sequence.</span></span>  
  
 <span data-ttu-id="f9dde-104">请注意 `Sum` 中 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 运算符的以下特征：</span><span class="sxs-lookup"><span data-stu-id="f9dde-104">Note the following characteristics of the `Sum` operator in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
- <span data-ttu-id="f9dde-105">使用标准查询运算符中的聚合运算符 `Sum` 计算空序列或只包含 null 的序列时，所得结果为零。</span><span class="sxs-lookup"><span data-stu-id="f9dde-105">The Standard Query Operator aggregate operator `Sum` evaluates to zero for an empty sequence or a sequence that contains only nulls.</span></span> <span data-ttu-id="f9dde-106">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，SQL 的语义保持不变。</span><span class="sxs-lookup"><span data-stu-id="f9dde-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the semantics of SQL are left unchanged.</span></span> <span data-ttu-id="f9dde-107">因此，使用 `Sum` 计算空序列或只包含 null 的序列时，所得结果为 null 而非零。</span><span class="sxs-lookup"><span data-stu-id="f9dde-107">For this reason, `Sum` evaluates to null instead of to zero for an empty sequence or for a sequence that contains only nulls.</span></span>  
  
- <span data-ttu-id="f9dde-108">针对中间结果的 SQL 限制适用于 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中的聚合。</span><span class="sxs-lookup"><span data-stu-id="f9dde-108">SQL limitations on intermediate results apply to aggregates in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="f9dde-109">32 位整型量之和不是使用 64 位结果计算的，且在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 转换 `Sum` 时可能会发生溢出。</span><span class="sxs-lookup"><span data-stu-id="f9dde-109">Sum of 32-bit integer quantities is not computed by using 64-bit results, and overflow can occur for the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of `Sum`.</span></span> <span data-ttu-id="f9dde-110">即使对于内存中的对应序列，标准查询运算符的实现不会造成溢出，仍存在这种可能性。</span><span class="sxs-lookup"><span data-stu-id="f9dde-110">This possibility exists even if the Standard Query Operator implementation does not cause an overflow for the corresponding in-memory sequence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9dde-111">示例</span><span class="sxs-lookup"><span data-stu-id="f9dde-111">Example</span></span>  

 <span data-ttu-id="f9dde-112">下面的示例查找 `Order` 表中所有订单的总运费。</span><span class="sxs-lookup"><span data-stu-id="f9dde-112">The following example finds the total freight of all orders in the `Order` table.</span></span>  
  
 <span data-ttu-id="f9dde-113">如果您对 Northwind 示例数据库运行此查询，则输出为：`64942.6900`。</span><span class="sxs-lookup"><span data-stu-id="f9dde-113">If you run this query against the Northwind sample database, the output is: `64942.6900`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="f9dde-114">示例</span><span class="sxs-lookup"><span data-stu-id="f9dde-114">Example</span></span>  

 <span data-ttu-id="f9dde-115">下面的示例查找所有产品总的订购件数。</span><span class="sxs-lookup"><span data-stu-id="f9dde-115">The following example finds the total number of units on order for all products.</span></span>  
  
 <span data-ttu-id="f9dde-116">如果您对 Northwind 示例数据库运行此查询，则输出为：`780`。</span><span class="sxs-lookup"><span data-stu-id="f9dde-116">If you run this query against the Northwind sample database, the output is: `780`.</span></span>  
  
 <span data-ttu-id="f9dde-117">请注意，您必须对 `short` 类型（例如，`UnitsOnOrder`）进行强制转换，因为 `Sum` 没有 short 类型的重载。</span><span class="sxs-lookup"><span data-stu-id="f9dde-117">Note that you must cast `short` types (for example, `UnitsOnOrder`) because `Sum` has no overload for short types.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="f9dde-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="f9dde-118">See also</span></span>

- [<span data-ttu-id="f9dde-119">聚合查询</span><span class="sxs-lookup"><span data-stu-id="f9dde-119">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="f9dde-120">下载示例数据库</span><span class="sxs-lookup"><span data-stu-id="f9dde-120">Downloading Sample Databases</span></span>](downloading-sample-databases.md)

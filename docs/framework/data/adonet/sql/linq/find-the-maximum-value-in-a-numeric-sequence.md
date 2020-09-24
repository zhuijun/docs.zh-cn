---
title: 查找数值序列中的最大值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70d7c058-0280-4815-a008-6f290093591a
ms.openlocfilehash: b70b94338ca7bdbb600bac697d3a36ff117d757e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155999"
---
# <a name="find-the-maximum-value-in-a-numeric-sequence"></a><span data-ttu-id="f7c9d-102">查找数值序列中的最大值</span><span class="sxs-lookup"><span data-stu-id="f7c9d-102">Find the Maximum Value in a Numeric Sequence</span></span>

<span data-ttu-id="f7c9d-103">使用 <xref:System.Linq.Enumerable.Max%2A> 运算符可查找数值序列中的最高值。</span><span class="sxs-lookup"><span data-stu-id="f7c9d-103">Use the <xref:System.Linq.Enumerable.Max%2A> operator to find the highest value in a sequence of numeric values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7c9d-104">示例</span><span class="sxs-lookup"><span data-stu-id="f7c9d-104">Example</span></span>  

 <span data-ttu-id="f7c9d-105">下面的示例查找任何员工的最近雇佣日期。</span><span class="sxs-lookup"><span data-stu-id="f7c9d-105">The following example finds the latest date of hire for any employee.</span></span>  
  
 <span data-ttu-id="f7c9d-106">如果您对 Northwind 示例数据库运行此查询，则输出为：`11/15/1994 12:00:00 AM`。</span><span class="sxs-lookup"><span data-stu-id="f7c9d-106">If you run this query against the sample Northwind database, the output is: `11/15/1994 12:00:00 AM`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#6)]
 [!code-vb[DLinqQueryExamples#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="f7c9d-107">示例</span><span class="sxs-lookup"><span data-stu-id="f7c9d-107">Example</span></span>  

 <span data-ttu-id="f7c9d-108">下面的示例查找任何产品的最大库存件数。</span><span class="sxs-lookup"><span data-stu-id="f7c9d-108">The following example finds the most units in stock for any product.</span></span>  
  
 <span data-ttu-id="f7c9d-109">如果您对 Northwind 示例数据库运行此示例，则输出为：`125`。</span><span class="sxs-lookup"><span data-stu-id="f7c9d-109">If you run this example against the sample Northwind database, the output is: `125`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#7)]
 [!code-vb[DLinqQueryExamples#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#7)]  
  
## <a name="example"></a><span data-ttu-id="f7c9d-110">示例</span><span class="sxs-lookup"><span data-stu-id="f7c9d-110">Example</span></span>  

 <span data-ttu-id="f7c9d-111">下面的示例使用 Max 查找每个类别中单价最高的 `Products`。</span><span class="sxs-lookup"><span data-stu-id="f7c9d-111">The following example uses Max to find the `Products` that have the highest unit price in each category.</span></span> <span data-ttu-id="f7c9d-112">然后，按类别列出输出结果。</span><span class="sxs-lookup"><span data-stu-id="f7c9d-112">The output then lists the results by category.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#8)]
 [!code-vb[DLinqQueryExamples#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#8)]  
  
 <span data-ttu-id="f7c9d-113">如果您对 Northwind 示例数据库运行上一个查询，所得到的结果将与如下内容类似：</span><span class="sxs-lookup"><span data-stu-id="f7c9d-113">If you run the previous query against the Northwind sample database, your results will resemble the following:</span></span>  
  
 `1`  
  
 `Côte de Blaye`  
  
 `2`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `4`  
  
 `Raclette Courdavault`  
  
 `5`  
  
 `Gnocchi di nonna Alice`  
  
 `6`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Carnarvon Tigers`  
  
## <a name="see-also"></a><span data-ttu-id="f7c9d-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="f7c9d-114">See also</span></span>

- [<span data-ttu-id="f7c9d-115">聚合查询</span><span class="sxs-lookup"><span data-stu-id="f7c9d-115">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="f7c9d-116">下载示例数据库</span><span class="sxs-lookup"><span data-stu-id="f7c9d-116">Downloading Sample Databases</span></span>](downloading-sample-databases.md)

---
title: 如何：编写自定义 PLINQ 聚合函数
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
ms.openlocfilehash: 644d6b6f929e040a0fe688c18c774de6f434c4b3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290767"
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a><span data-ttu-id="8f979-102">如何：编写自定义 PLINQ 聚合函数</span><span class="sxs-lookup"><span data-stu-id="8f979-102">How to: Write a Custom PLINQ Aggregate Function</span></span>
<span data-ttu-id="8f979-103">此示例展示了如何使用 <xref:System.Linq.ParallelEnumerable.Aggregate%2A> 方法，将自定义聚合函数应用于源序列。</span><span class="sxs-lookup"><span data-stu-id="8f979-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.Aggregate%2A> method to apply a custom aggregation function to a source sequence.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="8f979-104">本示例旨在演示用法，运行速度可能不如等效的顺序 LINQ to Objects 查询快。</span><span class="sxs-lookup"><span data-stu-id="8f979-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="8f979-105">若要详细了解加速，请参阅[了解 PLINQ 中的加速](understanding-speedup-in-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="8f979-105">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f979-106">示例</span><span class="sxs-lookup"><span data-stu-id="8f979-106">Example</span></span>  
 <span data-ttu-id="8f979-107">下面的示例计算整数序列的标准偏差。</span><span class="sxs-lookup"><span data-stu-id="8f979-107">The following example calculates the standard deviation of a sequence of integers.</span></span>  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 <span data-ttu-id="8f979-108">此示例使用 PLINQ 独有的聚合标准查询运算符的重载。</span><span class="sxs-lookup"><span data-stu-id="8f979-108">This example uses an overload of the Aggregate standard query operator that is unique to PLINQ.</span></span> <span data-ttu-id="8f979-109">此重载需要使用额外的 <xref:System.Func%603?displayProperty=nameWithType> 作为第三个输入参数。</span><span class="sxs-lookup"><span data-stu-id="8f979-109">This overload takes an extra <xref:System.Func%603?displayProperty=nameWithType> as the third input parameter.</span></span> <span data-ttu-id="8f979-110">此委托先合并所有线程的结果，再对聚合结果执行最终计算。</span><span class="sxs-lookup"><span data-stu-id="8f979-110">This delegate combines the results from all threads before it performs the final calculation on the aggregated results.</span></span> <span data-ttu-id="8f979-111">此示例将所有线程的总和结果相加到一起。</span><span class="sxs-lookup"><span data-stu-id="8f979-111">In this example we add together the sums from all the threads.</span></span>  
  
 <span data-ttu-id="8f979-112">请注意，如果 Lambda 表达式主体由一个表达式组成，<xref:System.Func%602?displayProperty=nameWithType> 委托的返回值就是表达式值。</span><span class="sxs-lookup"><span data-stu-id="8f979-112">Note that when a lambda expression body consists of a single expression, the return value of the <xref:System.Func%602?displayProperty=nameWithType> delegate is the value of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f979-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8f979-113">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="8f979-114">并行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="8f979-114">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)

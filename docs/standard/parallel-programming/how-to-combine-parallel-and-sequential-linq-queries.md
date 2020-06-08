---
title: 如何：合并并行和顺序 LINQ 查询
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel queries, combine parallel and sequential
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
ms.openlocfilehash: 2bdf074bc2977dc501e0726a52e825c89828565f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289533"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a><span data-ttu-id="1eaae-102">如何：合并并行和顺序 LINQ 查询</span><span class="sxs-lookup"><span data-stu-id="1eaae-102">How to: Combine Parallel and Sequential LINQ Queries</span></span>

<span data-ttu-id="1eaae-103">此示例展示了如何使用 <xref:System.Linq.ParallelEnumerable.AsSequential%2A> 方法，指示 PLINQ 顺序处理查询中的所有后续运算符。</span><span class="sxs-lookup"><span data-stu-id="1eaae-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.AsSequential%2A> method to instruct PLINQ to process all subsequent operators in the query sequentially.</span></span> <span data-ttu-id="1eaae-104">尽管顺序处理通常比并行处理慢，但有时却是生成正确结果的必要条件。</span><span class="sxs-lookup"><span data-stu-id="1eaae-104">Although sequential processing is often slower than parallel, sometimes it's necessary to produce correct results.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1eaae-105">本示例旨在演示用法，运行速度可能不如等效的顺序 LINQ to Objects 查询快。</span><span class="sxs-lookup"><span data-stu-id="1eaae-105">This example is intended to demonstrate usage and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="1eaae-106">若要详细了解加速，请参阅[了解 PLINQ 中的加速](understanding-speedup-in-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="1eaae-106">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1eaae-107">示例</span><span class="sxs-lookup"><span data-stu-id="1eaae-107">Example</span></span>  
 <span data-ttu-id="1eaae-108">下面的示例展示了一种需要 <xref:System.Linq.ParallelEnumerable.AsSequential%2A> 的情况，即暂留在旧查询子句中建立的顺序。</span><span class="sxs-lookup"><span data-stu-id="1eaae-108">The following example shows one scenario in which <xref:System.Linq.ParallelEnumerable.AsSequential%2A> is required, namely to preserve the ordering that was established in a previous clause of the query.</span></span>  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1eaae-109">编译代码</span><span class="sxs-lookup"><span data-stu-id="1eaae-109">Compiling the Code</span></span>  
 <span data-ttu-id="1eaae-110">若要编译并运行此代码，请将它粘贴到 [PLINQ 数据样本](plinq-data-sample.md)项目中，添加用于从 `Main` 调用方法的代码行，再按 F5  。</span><span class="sxs-lookup"><span data-stu-id="1eaae-110">To compile and run this code, paste it into the [PLINQ Data Sample](plinq-data-sample.md) project, add a line to call the method from `Main`, and press **F5**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1eaae-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="1eaae-111">See also</span></span>

- [<span data-ttu-id="1eaae-112">并行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="1eaae-112">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)

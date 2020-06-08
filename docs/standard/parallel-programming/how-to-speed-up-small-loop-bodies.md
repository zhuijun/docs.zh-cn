---
title: 如何：加快小型循环体的速度
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to speed up
ms.assetid: c7a66677-cb59-4cbf-969a-d2e8fc61a6ce
ms.openlocfilehash: 4983cafb9d4a72262dc7a6a6c37fab23937b3274
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288077"
---
# <a name="how-to-speed-up-small-loop-bodies"></a><span data-ttu-id="42fcf-102">如何：加快小型循环体的速度</span><span class="sxs-lookup"><span data-stu-id="42fcf-102">How to: Speed Up Small Loop Bodies</span></span>
<span data-ttu-id="42fcf-103">如果 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> 循环的主体很小，它的执行速度可能慢于相当的顺序循环，如 C# 中的 [for](../../csharp/language-reference/keywords/for.md) 循环和 Visual Basic 中的 [For](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) 循环。</span><span class="sxs-lookup"><span data-stu-id="42fcf-103">When a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop has a small body, it might perform more slowly than the equivalent sequential loop, such as the [for](../../csharp/language-reference/keywords/for.md) loop in C# and the [For](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) loop in Visual Basic.</span></span> <span data-ttu-id="42fcf-104">性能下降是由数据分区中的开销和在每个循环迭代上调用委托的成本所引起的。</span><span class="sxs-lookup"><span data-stu-id="42fcf-104">Slower performance is caused by the overhead involved in partitioning the data and the cost of invoking a delegate on each loop iteration.</span></span> <span data-ttu-id="42fcf-105">若要解决这种情况下，<xref:System.Collections.Concurrent.Partitioner> 类提供了 <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> 方法，使你能够为委托主体提供一个顺序循环，以便每个分区仅调用一次委托，而不是每个迭代调用一次委托。</span><span class="sxs-lookup"><span data-stu-id="42fcf-105">To address such scenarios, the <xref:System.Collections.Concurrent.Partitioner> class provides the <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> method, which enables you to provide a sequential loop for the delegate body, so that the delegate is invoked only once per partition, instead of once per iteration.</span></span> <span data-ttu-id="42fcf-106">有关详细信息，请参阅 [PLINQ 和 TPL 的自定义分区程序](custom-partitioners-for-plinq-and-tpl.md)。</span><span class="sxs-lookup"><span data-stu-id="42fcf-106">For more information, see [Custom Partitioners for PLINQ and TPL](custom-partitioners-for-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="42fcf-107">示例</span><span class="sxs-lookup"><span data-stu-id="42fcf-107">Example</span></span>  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 <span data-ttu-id="42fcf-108">在循环执行最少量的工作时，此示例中演示的方法很有用。</span><span class="sxs-lookup"><span data-stu-id="42fcf-108">The approach demonstrated in this example is useful when the loop performs a minimal amount of work.</span></span> <span data-ttu-id="42fcf-109">随着工作变得更占用计算资源，通过默认分区程序，使用 <xref:System.Threading.Tasks.Parallel.For%2A> 或 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 循环，很有可能会获得相同或更好的性能。</span><span class="sxs-lookup"><span data-stu-id="42fcf-109">As the work becomes more computationally expensive, you will probably get the same or better performance by using a <xref:System.Threading.Tasks.Parallel.For%2A> or <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop with the default partitioner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42fcf-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="42fcf-110">See also</span></span>

- [<span data-ttu-id="42fcf-111">数据并行</span><span class="sxs-lookup"><span data-stu-id="42fcf-111">Data Parallelism</span></span>](data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="42fcf-112">PLINQ 和 TPL 的自定义分区程序</span><span class="sxs-lookup"><span data-stu-id="42fcf-112">Custom Partitioners for PLINQ and TPL</span></span>](custom-partitioners-for-plinq-and-tpl.md)
- [<span data-ttu-id="42fcf-113">迭代器 (C#)</span><span class="sxs-lookup"><span data-stu-id="42fcf-113">Iterators (C#)</span></span>](../../csharp/programming-guide/concepts/iterators.md)
- [<span data-ttu-id="42fcf-114">迭代器 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42fcf-114">Iterators (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/iterators.md)
- [<span data-ttu-id="42fcf-115">PLINQ 和 TPL 中的 Lambda 表达式</span><span class="sxs-lookup"><span data-stu-id="42fcf-115">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)

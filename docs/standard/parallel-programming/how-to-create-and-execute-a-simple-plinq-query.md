---
title: 如何：创建并执行简单的 PLINQ 查询
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create
ms.assetid: 983b4213-bddd-4a44-9262-cbe59186df4c
ms.openlocfilehash: a9c044254423d0f9d266539c728a6604f562e97d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290001"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a><span data-ttu-id="ed0e2-102">如何：创建并执行简单的 PLINQ 查询</span><span class="sxs-lookup"><span data-stu-id="ed0e2-102">How to: Create and Execute a Simple PLINQ Query</span></span>

<span data-ttu-id="ed0e2-103">本文中的示例演示如何通过对源序列使用 <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> 扩展方法来创建一个简单的并行语言集成查询 (LINQ) 查询，并使用 <xref:System.Linq.ParallelEnumerable.ForAll%2A?displayProperty=nameWithTyp> 方法执行该查询。</span><span class="sxs-lookup"><span data-stu-id="ed0e2-103">The example in this article shows how to create a simple Parallel Language Integrated Query (LINQ) query by using the <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> extension method on the source sequence and executing the query by using the <xref:System.Linq.ParallelEnumerable.ForAll%2A?displayProperty=nameWithTyp> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ed0e2-104">本文档使用 lambda 表达式在 PLINQ 中定义委托。</span><span class="sxs-lookup"><span data-stu-id="ed0e2-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="ed0e2-105">如果不熟悉 C# 或 Visual Basic 中的 lambda 表达式，请参阅 [PLINQ 和 TPL 中的 Lambda 表达式](lambda-expressions-in-plinq-and-tpl.md)。</span><span class="sxs-lookup"><span data-stu-id="ed0e2-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed0e2-106">示例</span><span class="sxs-lookup"><span data-stu-id="ed0e2-106">Example</span></span>  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 <span data-ttu-id="ed0e2-107">此示例演示用于在结果序列的排序不重要的情况下创建和执行任何并行 LINQ 查询的基本模式.</span><span class="sxs-lookup"><span data-stu-id="ed0e2-107">This example demonstrates the basic pattern for creating and executing any Parallel LINQ query when the ordering of the result sequence is not important.</span></span> <span data-ttu-id="ed0e2-108">未排序的查询通常比已排序的查询快。</span><span class="sxs-lookup"><span data-stu-id="ed0e2-108">Unordered queries are generally faster than ordered queries.</span></span> <span data-ttu-id="ed0e2-109">查询将源分区为多个任务，这些任务将在多个线程上异步执行。</span><span class="sxs-lookup"><span data-stu-id="ed0e2-109">The query partitions the source into tasks that are executed asynchronously on multiple threads.</span></span> <span data-ttu-id="ed0e2-110">每个任务的完成顺序不仅取决于处理分区中的元素所涉及的工作量，还取决于诸如操作系统如何调度每个线程之类的外部因素。</span><span class="sxs-lookup"><span data-stu-id="ed0e2-110">The order in which each task completes depends not only on the amount of work involved to process the elements in the partition, but also on external factors such as how the operating system schedules each thread.</span></span> <span data-ttu-id="ed0e2-111">本示例旨在演示用法，运行速度可能不如等效的顺序 LINQ to Objects 查询快。</span><span class="sxs-lookup"><span data-stu-id="ed0e2-111">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="ed0e2-112">若要详细了解加速，请参阅[了解 PLINQ 中的加速](understanding-speedup-in-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="ed0e2-112">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span> <span data-ttu-id="ed0e2-113">有关如何在查询中保留元素排序的详细信息，请参阅[如何：在 PLINQ 查询中控制排序](how-to-control-ordering-in-a-plinq-query.md)。</span><span class="sxs-lookup"><span data-stu-id="ed0e2-113">For more information about how to preserve the ordering of elements in a query, see [How to: Control Ordering in a PLINQ Query](how-to-control-ordering-in-a-plinq-query.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed0e2-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="ed0e2-114">See also</span></span>

- [<span data-ttu-id="ed0e2-115">并行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="ed0e2-115">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)

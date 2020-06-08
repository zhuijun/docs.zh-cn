---
title: 如何：使用 Parallel.Invoke 执行并行操作
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
ms.openlocfilehash: 2b353fb8cb5e04ee4cab6b49f55539ecb40fab4f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290793"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a><span data-ttu-id="3125a-102">如何：使用 Parallel.Invoke 执行并行操作</span><span class="sxs-lookup"><span data-stu-id="3125a-102">How to: Use Parallel.Invoke to Execute Parallel Operations</span></span>

<span data-ttu-id="3125a-103">此示例演示如何通过使用任务并行库中的 <xref:System.Threading.Tasks.Parallel.Invoke%2A> 并行操作。</span><span class="sxs-lookup"><span data-stu-id="3125a-103">This example shows how to parallelize operations by using <xref:System.Threading.Tasks.Parallel.Invoke%2A> in the Task Parallel Library.</span></span> <span data-ttu-id="3125a-104">共享的数据源上执行三个操作。</span><span class="sxs-lookup"><span data-stu-id="3125a-104">Three operations are performed on a shared data source.</span></span> <span data-ttu-id="3125a-105">因为操作均不修改源，所以可通过直接的方式并行执行操作。</span><span class="sxs-lookup"><span data-stu-id="3125a-105">The operations can be executed in parallel in a straightforward manner, because none of them modifies the source.</span></span>

> [!NOTE]
> <span data-ttu-id="3125a-106">本文档使用 lambda 表达式在 TPL 中定义委托。</span><span class="sxs-lookup"><span data-stu-id="3125a-106">This documentation uses lambda expressions to define delegates in TPL.</span></span> <span data-ttu-id="3125a-107">如果不熟悉 C# 或 Visual Basic 中的 lambda 表达式，请参阅 [PLINQ 和 TPL 中的 Lambda 表达式](lambda-expressions-in-plinq-and-tpl.md)。</span><span class="sxs-lookup"><span data-stu-id="3125a-107">If you aren't familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="3125a-108">示例</span><span class="sxs-lookup"><span data-stu-id="3125a-108">Example</span></span>

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

<span data-ttu-id="3125a-109">借助 <xref:System.Threading.Tasks.Parallel.Invoke%2A>，你只需表达想同时运行的操作，运行时会处理所有线程计划详细信息（包括自动缩放至主计算机上的内核数）。</span><span class="sxs-lookup"><span data-stu-id="3125a-109">With <xref:System.Threading.Tasks.Parallel.Invoke%2A>, you simply express which actions you want to run concurrently, and the runtime handles all thread scheduling details, including scaling automatically to the number of cores on the host computer.</span></span>

<span data-ttu-id="3125a-110">此示例并行操作，而非数据。</span><span class="sxs-lookup"><span data-stu-id="3125a-110">This example parallelizes the operations, not the data.</span></span> <span data-ttu-id="3125a-111">此外，可使用 PLINQ 并行 LINQ 查询，并按顺序运行查询。</span><span class="sxs-lookup"><span data-stu-id="3125a-111">As an alternate approach, you can parallelize the LINQ queries by using PLINQ and run the queries sequentially.</span></span> <span data-ttu-id="3125a-112">或者，可使用 PLINQ 并行数据。</span><span class="sxs-lookup"><span data-stu-id="3125a-112">Alternatively, you could parallelize the data by using PLINQ.</span></span> <span data-ttu-id="3125a-113">另一个选项是并行查询和任务。</span><span class="sxs-lookup"><span data-stu-id="3125a-113">Another option is to parallelize both the queries and the tasks.</span></span> <span data-ttu-id="3125a-114">尽管生成的开销在处理器相对较少的主机计算机上可能会降低性能，但在处理器较多的计算机上可更好地缩放。</span><span class="sxs-lookup"><span data-stu-id="3125a-114">Although the resulting overhead might degrade performance on host computers with relatively few processors, it scales better on computers with many processors.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="3125a-115">编译代码</span><span class="sxs-lookup"><span data-stu-id="3125a-115">Compile the Code</span></span>

<span data-ttu-id="3125a-116">将完整示例复制和粘贴到 Microsoft Visual Studio 项目，并按 F5 键  。</span><span class="sxs-lookup"><span data-stu-id="3125a-116">Copy and paste the entire example into a Microsoft Visual Studio project and press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="3125a-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="3125a-117">See also</span></span>

- [<span data-ttu-id="3125a-118">并行编程</span><span class="sxs-lookup"><span data-stu-id="3125a-118">Parallel Programming</span></span>](index.md)
- [<span data-ttu-id="3125a-119">如何：取消任务及其子级</span><span class="sxs-lookup"><span data-stu-id="3125a-119">How to: Cancel a Task and Its Children</span></span>](how-to-cancel-a-task-and-its-children.md)
- [<span data-ttu-id="3125a-120">并行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="3125a-120">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)

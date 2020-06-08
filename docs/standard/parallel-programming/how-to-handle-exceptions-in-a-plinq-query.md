---
title: 如何：处理 PLINQ 查询中的异常
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to handle exceptions
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
ms.openlocfilehash: 4097d222b5fa51cc638a2d07d3fd2eddf5d9859c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278644"
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a><span data-ttu-id="e4978-102">如何：处理 PLINQ 查询中的异常</span><span class="sxs-lookup"><span data-stu-id="e4978-102">How to: Handle Exceptions in a PLINQ Query</span></span>

<span data-ttu-id="e4978-103">本主题中的第一个示例展示了如何处理 PLINQ 查询在执行时可能会抛出的 <xref:System.AggregateException?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="e4978-103">The first example in this topic shows how to handle the <xref:System.AggregateException?displayProperty=nameWithType> that can be thrown from a PLINQ query when it executes.</span></span> <span data-ttu-id="e4978-104">第二个示例展示了如何将 try-catch 块置于委托中，并尽可能靠近抛出异常的代码位置。</span><span class="sxs-lookup"><span data-stu-id="e4978-104">The second example shows how to put try-catch blocks within delegates, as close as possible to where the exception will be thrown.</span></span> <span data-ttu-id="e4978-105">这样一来，可以在异常发生时尽快捕获它们，并继续执行查询。</span><span class="sxs-lookup"><span data-stu-id="e4978-105">In this way, you can catch them as soon as they occur and possibly continue query execution.</span></span> <span data-ttu-id="e4978-106">如果允许异常向上冒泡回到联接线程，则查询也许可以在引发异常后继续处理一些项。</span><span class="sxs-lookup"><span data-stu-id="e4978-106">When exceptions are allowed to bubble up back to the joining thread, then it is possible that a query may continue to process some items after the exception is raised.</span></span>

<span data-ttu-id="e4978-107">如果 PLINQ 回退到顺序执行且发生异常，异常可能会直接传播，而不会被包装在 <xref:System.AggregateException> 中。</span><span class="sxs-lookup"><span data-stu-id="e4978-107">In some cases when PLINQ falls back to sequential execution, and an exception occurs, the exception may be propagated directly, and not wrapped in an <xref:System.AggregateException>.</span></span> <span data-ttu-id="e4978-108">此外，<xref:System.Threading.ThreadAbortException> 始终都会直接传播。</span><span class="sxs-lookup"><span data-stu-id="e4978-108">Also, <xref:System.Threading.ThreadAbortException>s are always propagated directly.</span></span>

> [!NOTE]
> <span data-ttu-id="e4978-109">选中“仅我的代码”后，Visual Studio 会在抛出异常的代码行处中断，并显示错误消息“用户代码未处理异常”。</span><span class="sxs-lookup"><span data-stu-id="e4978-109">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="e4978-110">此错误是良性的。</span><span class="sxs-lookup"><span data-stu-id="e4978-110">This error is benign.</span></span> <span data-ttu-id="e4978-111">可以按 F5 继续运行，并请参阅下面示例中所示的异常处理行为。</span><span class="sxs-lookup"><span data-stu-id="e4978-111">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="e4978-112">为了阻止 Visual Studio 在第一个错误出现时中断，只需依次转到“工具”、“选项”、“调试”、“常规”  下，取消选中“仅我的代码”复选框即可。</span><span class="sxs-lookup"><span data-stu-id="e4978-112">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>
>
> <span data-ttu-id="e4978-113">本示例旨在演示用法，运行速度可能不如等效的顺序 LINQ to Objects 查询快。</span><span class="sxs-lookup"><span data-stu-id="e4978-113">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="e4978-114">若要详细了解加速，请参阅[了解 PLINQ 中的加速](understanding-speedup-in-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="e4978-114">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>

## <a name="example"></a><span data-ttu-id="e4978-115">示例</span><span class="sxs-lookup"><span data-stu-id="e4978-115">Example</span></span>

<span data-ttu-id="e4978-116">此示例展示了如何将 try-catch 块置于执行查询以捕获抛出的任何 <xref:System.AggregateException?displayProperty=nameWithType> 的代码附近。</span><span class="sxs-lookup"><span data-stu-id="e4978-116">This example shows how to put the try-catch blocks around the code that executes the query to catch any <xref:System.AggregateException?displayProperty=nameWithType>s that are thrown.</span></span>

[!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
[!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]

<span data-ttu-id="e4978-117">在此示例中，查询无法在异常抛出后继续运行。</span><span class="sxs-lookup"><span data-stu-id="e4978-117">In this example, the query cannot continue after the exception is thrown.</span></span> <span data-ttu-id="e4978-118">在应用代码捕获到异常时，PLINQ 已停止对所有线程运行查询。</span><span class="sxs-lookup"><span data-stu-id="e4978-118">By the time your application code catches the exception, PLINQ has already stopped the query on all threads.</span></span>

## <a name="example"></a><span data-ttu-id="e4978-119">示例</span><span class="sxs-lookup"><span data-stu-id="e4978-119">Example</span></span>

<span data-ttu-id="e4978-120">下面的示例展示了如何将 try-catch 块置于委托中，以便可以捕获异常并继续执行查询。</span><span class="sxs-lookup"><span data-stu-id="e4978-120">The following example shows how to put a try-catch block in a delegate to make it possible to catch an exception and continue with the query execution.</span></span>

[!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
[!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]

## <a name="compiling-the-code"></a><span data-ttu-id="e4978-121">编译代码</span><span class="sxs-lookup"><span data-stu-id="e4978-121">Compiling the Code</span></span>

- <span data-ttu-id="e4978-122">若要编译和运行这些示例，请将它们复制到“PLINQ 数据样本”示例中，并通过 Main 调用此方法。</span><span class="sxs-lookup"><span data-stu-id="e4978-122">To compile and run these examples, copy them into the PLINQ Data Sample example and call the method from Main.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="e4978-123">可靠编程</span><span class="sxs-lookup"><span data-stu-id="e4978-123">Robust Programming</span></span>

<span data-ttu-id="e4978-124">仅在确定如何处理异常时，才捕获异常，以免破坏程序状态。</span><span class="sxs-lookup"><span data-stu-id="e4978-124">Do not catch an exception unless you know how to handle it so that you do not corrupt the state of your program.</span></span>

## <a name="see-also"></a><span data-ttu-id="e4978-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e4978-125">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="e4978-126">并行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="e4978-126">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)

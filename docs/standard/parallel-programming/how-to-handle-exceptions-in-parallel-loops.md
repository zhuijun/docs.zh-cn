---
title: 如何：处理并行循环中的异常
description: 了解如何在 .NET 中处理并行循环中的异常。 查看有关如何将循环中的所有异常包装在 System.AggregateException 中的示例。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to handle exceptions
ms.assetid: 512f0d5a-4636-4875-b766-88f20044f143
ms.openlocfilehash: 61c22d6e82282f8aeb54818c813d4489e3bc9641
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768971"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a><span data-ttu-id="80152-104">如何：处理并行循环中的异常</span><span class="sxs-lookup"><span data-stu-id="80152-104">How to: Handle Exceptions in Parallel Loops</span></span>
<span data-ttu-id="80152-105"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 重载没有任何用于处理可能引发的异常的特殊机制。</span><span class="sxs-lookup"><span data-stu-id="80152-105">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> overloads do not have any special mechanism to handle exceptions that might be thrown.</span></span> <span data-ttu-id="80152-106">在这一方面，它们类似于常规 `for` 和 `foreach` 循环（在 Visual Basic 中为 `For` 和 `For Each`）；未处理的异常会导致循环在当前运行的迭代完成后立即终止。</span><span class="sxs-lookup"><span data-stu-id="80152-106">In this respect, they resemble regular `for` and `foreach` loops (`For` and `For Each` in Visual Basic); an unhandled exception causes the loop to terminate as soon as all currently running iterations finish.</span></span>
  
 <span data-ttu-id="80152-107">向并行循环添加自己的异常处理逻辑时，将处理类似于在多个线程上同时引发相似异常的情况，以及一个线程上引发异常导致另一个线程上引发另一个异常的情况。</span><span class="sxs-lookup"><span data-stu-id="80152-107">When you add your own exception-handling logic to parallel loops, handle the case in which similar exceptions might be thrown on multiple threads concurrently, and the case in which an exception thrown on one thread causes another exception to be thrown on another thread.</span></span> <span data-ttu-id="80152-108">你可以通过将循环中的所有异常包装到一个 <xref:System.AggregateException?displayProperty=nameWithType> 中处理这两种情况。</span><span class="sxs-lookup"><span data-stu-id="80152-108">You can handle both cases by wrapping all exceptions from the loop in a <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="80152-109">下面的示例演示了一种可能的方法。</span><span class="sxs-lookup"><span data-stu-id="80152-109">The following example shows one possible approach.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="80152-110">某些情况下，当启用“仅我的代码”后，Visual Studio 会在引发异常的行中断运行并显示一条错误消息，该消息显示“用户代码未处理异常”。</span><span class="sxs-lookup"><span data-stu-id="80152-110">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="80152-111">此错误是良性的。</span><span class="sxs-lookup"><span data-stu-id="80152-111">This error is benign.</span></span> <span data-ttu-id="80152-112">可以按 F5 继续运行，并请参阅下面示例中所示的异常处理行为。</span><span class="sxs-lookup"><span data-stu-id="80152-112">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the example below.</span></span> <span data-ttu-id="80152-113">为了阻止 Visual Studio 在第一个错误出现时中断，只需依次转到“工具”、“选项”、“调试”、“常规”下，取消选中“仅我的代码”复选框即可。</span><span class="sxs-lookup"><span data-stu-id="80152-113">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80152-114">示例</span><span class="sxs-lookup"><span data-stu-id="80152-114">Example</span></span>  
 <span data-ttu-id="80152-115">在此示例中，所有异常都被捕获，并包装到引发的 <xref:System.AggregateException?displayProperty=nameWithType> 中。</span><span class="sxs-lookup"><span data-stu-id="80152-115">In this example, all exceptions are caught and then wrapped in an <xref:System.AggregateException?displayProperty=nameWithType> which is thrown.</span></span> <span data-ttu-id="80152-116">调用方可以决定要处理哪些异常。</span><span class="sxs-lookup"><span data-stu-id="80152-116">The caller can decide which exceptions to handle.</span></span>  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="80152-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="80152-117">See also</span></span>

- [<span data-ttu-id="80152-118">数据并行</span><span class="sxs-lookup"><span data-stu-id="80152-118">Data Parallelism</span></span>](data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="80152-119">PLINQ 和 TPL 中的 Lambda 表达式</span><span class="sxs-lookup"><span data-stu-id="80152-119">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)

---
title: PLINQ 和 TPL 中的 Lambda 表达式
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Func delegate, creating with lambda expression
- Action delegate, creating with lambda expression
- lambda expressions, with Action and Func
ms.assetid: 645b2c17-29d0-4ffa-8684-430743cc2f2d
ms.openlocfilehash: 3d985a003fe613699c89e38583f84be9e21b383d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290663"
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a><span data-ttu-id="91d7b-102">PLINQ 和 TPL 中的 Lambda 表达式</span><span class="sxs-lookup"><span data-stu-id="91d7b-102">Lambda Expressions in PLINQ and TPL</span></span>

<span data-ttu-id="91d7b-103">任务并行库 (TPL) 包含许多方法，需要使用 <xref:System.Func%601?displayProperty=nameWithType> 或 <xref:System.Action?displayProperty=nameWithType> 系列委托之一作为输入参数。</span><span class="sxs-lookup"><span data-stu-id="91d7b-103">The Task Parallel Library (TPL) contains many methods that take one of the <xref:System.Func%601?displayProperty=nameWithType> or <xref:System.Action?displayProperty=nameWithType> family of delegates as input parameters.</span></span> <span data-ttu-id="91d7b-104">使用这些委托将自定义程序逻辑传入到并行循环、任务或查询中。</span><span class="sxs-lookup"><span data-stu-id="91d7b-104">You use these delegates to pass in your custom program logic to the parallel loop, task or query.</span></span> <span data-ttu-id="91d7b-105">TPL 以及 PLINQ 的代码示例使用 lambda 表达式以内联代码块的形式创建这些委托的实例。</span><span class="sxs-lookup"><span data-stu-id="91d7b-105">The code examples for TPL as well as PLINQ use lambda expressions to create instances of those delegates as inline code blocks.</span></span> <span data-ttu-id="91d7b-106">本主题简要介绍 Func 和 Action，并演示如何在任务并行库和 PLINQ 中使用 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="91d7b-106">This topic provides a brief introduction to Func and Action and shows you how to use lambda expressions in the Task Parallel Library and PLINQ.</span></span>

> [!NOTE]
> <span data-ttu-id="91d7b-107">有关委托的更多常规信息，请参阅[委托](../../csharp/programming-guide/delegates/index.md)和[委托](../../visual-basic/programming-guide/language-features/delegates/index.md)。</span><span class="sxs-lookup"><span data-stu-id="91d7b-107">For more information about delegates in general, see [Delegates](../../csharp/programming-guide/delegates/index.md) and [Delegates](../../visual-basic/programming-guide/language-features/delegates/index.md).</span></span> <span data-ttu-id="91d7b-108">有关 C# 和 Visual Basic 中的 lambda 表达式的详细信息，请参阅 [Lambda 表达式](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)和 [Lambda 表达式](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="91d7b-108">For more information about lambda expressions in C# and Visual Basic, see [Lambda Expressions](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) and [Lambda Expressions](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>

## <a name="func-delegate"></a><span data-ttu-id="91d7b-109">Func 委托</span><span class="sxs-lookup"><span data-stu-id="91d7b-109">Func Delegate</span></span>

<span data-ttu-id="91d7b-110">`Func` 委托封装返回值的一个方法。</span><span class="sxs-lookup"><span data-stu-id="91d7b-110">A `Func` delegate encapsulates a method that returns a value.</span></span> <span data-ttu-id="91d7b-111">在 `Func` 签名中，最后或最右侧的类型参数始终指定返回类型。</span><span class="sxs-lookup"><span data-stu-id="91d7b-111">In a `Func` signature, the last, or rightmost, type parameter always specifies the return type.</span></span> <span data-ttu-id="91d7b-112">导致编译器错误出现的常见原因之一是，尝试将两个输入参数传入 <xref:System.Func%602?displayProperty=nameWithType>；此类型其实只需要使用一个输入参数。</span><span class="sxs-lookup"><span data-stu-id="91d7b-112">One common cause of compiler errors is to attempt to pass in two input parameters to a <xref:System.Func%602?displayProperty=nameWithType>; in fact this type takes only one input parameter.</span></span> <span data-ttu-id="91d7b-113">.NET 定义 `Func` 的 17 个版本：<xref:System.Func%601?displayProperty=nameWithType>、<xref:System.Func%602?displayProperty=nameWithType>、<xref:System.Func%603?displayProperty=nameWithType>，依此类推直到 <xref:System.Func%6017?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="91d7b-113">.NET defines 17 versions of `Func`: <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType>, and so on up through <xref:System.Func%6017?displayProperty=nameWithType>.</span></span>

## <a name="action-delegate"></a><span data-ttu-id="91d7b-114">Action 委托</span><span class="sxs-lookup"><span data-stu-id="91d7b-114">Action Delegate</span></span>

<span data-ttu-id="91d7b-115"><xref:System.Action?displayProperty=nameWithType> 委托封装了不返回值的方法（Visual Basic 中的 Sub）。</span><span class="sxs-lookup"><span data-stu-id="91d7b-115">A <xref:System.Action?displayProperty=nameWithType> delegate encapsulates a method (Sub in Visual Basic) that does not return a value.</span></span> <span data-ttu-id="91d7b-116">在 `Action` 类型签名中，类型参数仅表示输入参数。</span><span class="sxs-lookup"><span data-stu-id="91d7b-116">In an `Action` type signature, the type parameters represent only input parameters.</span></span> <span data-ttu-id="91d7b-117">与 `Func` 一样，.NET 定义了 `Action` 的 17 个版本，从没有类型参数的版本到具有 16 个类型参数的版本。</span><span class="sxs-lookup"><span data-stu-id="91d7b-117">Like `Func`, .NET defines 17 versions of `Action`, from a version that has no type parameters up through a version that has 16 type parameters.</span></span>

## <a name="example"></a><span data-ttu-id="91d7b-118">示例</span><span class="sxs-lookup"><span data-stu-id="91d7b-118">Example</span></span>

<span data-ttu-id="91d7b-119">下面的 <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> 方法示例展示了如何使用 Lambda 表达式表达 Func 和 Action 委托。</span><span class="sxs-lookup"><span data-stu-id="91d7b-119">The following example for the <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> method shows how to express both Func and Action delegates by using lambda expressions.</span></span>

[!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
[!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]

## <a name="see-also"></a><span data-ttu-id="91d7b-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="91d7b-120">See also</span></span>

- [<span data-ttu-id="91d7b-121">并行编程</span><span class="sxs-lookup"><span data-stu-id="91d7b-121">Parallel Programming</span></span>](index.md)

---
title: 异常处理 - C# 编程指南
description: 了解异常处理。 请参阅 try-catch、try-finally 和 try-catch-finally 语句的示例。
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], handling
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
ms.openlocfilehash: 8f7dc027396e327f08a591ced6bd6df176a17606
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178679"
---
# <a name="exception-handling-c-programming-guide"></a><span data-ttu-id="2e353-104">异常处理（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="2e353-104">Exception Handling (C# Programming Guide)</span></span>

<span data-ttu-id="2e353-105">C# 程序员使用 [try](../../language-reference/keywords/try-catch.md) 块来对可能受异常影响的代码进行分区。</span><span class="sxs-lookup"><span data-stu-id="2e353-105">A [try](../../language-reference/keywords/try-catch.md) block is used by C# programmers to partition code that might be affected by an exception.</span></span> <span data-ttu-id="2e353-106">关联的 [catch](../../language-reference/keywords/try-catch.md) 块用于处理生成的任何异常。</span><span class="sxs-lookup"><span data-stu-id="2e353-106">Associated [catch](../../language-reference/keywords/try-catch.md) blocks are used to handle any resulting exceptions.</span></span> <span data-ttu-id="2e353-107">[finally](../../language-reference/keywords/try-finally.md) 块包含无论 `try` 块中是否引发异常都会运行的代码，如发布 `try` 块中分配的资源。</span><span class="sxs-lookup"><span data-stu-id="2e353-107">A [finally](../../language-reference/keywords/try-finally.md) block contains code that is run regardless of whether or not an exception is thrown in the `try` block, such as releasing resources that are allocated in the `try` block.</span></span> <span data-ttu-id="2e353-108">`try` 块需要一个或多个关联的 `catch` 块或一个 `finally` 块，或两者皆之。</span><span class="sxs-lookup"><span data-stu-id="2e353-108">A `try` block requires one or more associated `catch` blocks, or a `finally` block, or both.</span></span>  
  
 <span data-ttu-id="2e353-109">下面的示例演示 `try-catch` 语句、`try-finally` 语句和 `try-catch-finally` 语句。</span><span class="sxs-lookup"><span data-stu-id="2e353-109">The following examples show a `try-catch` statement, a `try-finally` statement, and a `try-catch-finally` statement.</span></span>  
  
 [!code-csharp[csProgGuideExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#6)]  
  
 [!code-csharp[csProgGuideExceptions#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#7)]  
  
 [!code-csharp[csProgGuideExceptions#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#8)]  
  
 <span data-ttu-id="2e353-110">一个不具有 `catch` 或 `finally` 块的 `try` 块会导致编译器错误。</span><span class="sxs-lookup"><span data-stu-id="2e353-110">A `try` block without a `catch` or `finally` block causes a compiler error.</span></span>  
  
## <a name="catch-blocks"></a><span data-ttu-id="2e353-111">catch 块</span><span class="sxs-lookup"><span data-stu-id="2e353-111">Catch Blocks</span></span>  

 <span data-ttu-id="2e353-112">`catch` 块可以指定要捕获的异常的类型。</span><span class="sxs-lookup"><span data-stu-id="2e353-112">A `catch` block can specify the type of exception to catch.</span></span> <span data-ttu-id="2e353-113">该类型规范称为异常筛选器。</span><span class="sxs-lookup"><span data-stu-id="2e353-113">The type specification is called an *exception filter*.</span></span> <span data-ttu-id="2e353-114">异常类型应派生自 <xref:System.Exception>。</span><span class="sxs-lookup"><span data-stu-id="2e353-114">The exception type should be derived from <xref:System.Exception>.</span></span> <span data-ttu-id="2e353-115">一般情况下，不要将 <xref:System.Exception> 指定为异常筛选器，除非了解如何处理可能在 `try` 块中引发的所有异常，或者已在 `catch` 块的末尾处包括了 [throw](../../language-reference/keywords/throw.md) 语句。</span><span class="sxs-lookup"><span data-stu-id="2e353-115">In general, do not specify <xref:System.Exception> as the exception filter unless either you know how to handle all exceptions that might be thrown in the `try` block, or you have included a [throw](../../language-reference/keywords/throw.md) statement at the end of your `catch` block.</span></span>  
  
 <span data-ttu-id="2e353-116">可将具有不同异常筛选器的多个 `catch` 块链接在一起。</span><span class="sxs-lookup"><span data-stu-id="2e353-116">Multiple `catch` blocks with different exception filters can be chained together.</span></span> <span data-ttu-id="2e353-117">代码中 `catch` 块的计算顺序为从上到下，但针对引发的每个异常，仅执行一个 `catch` 块。</span><span class="sxs-lookup"><span data-stu-id="2e353-117">The `catch` blocks are evaluated from top to bottom in your code, but only one `catch` block is executed for each exception that is thrown.</span></span> <span data-ttu-id="2e353-118">将执行指定所引发的异常的确切类型或基类的第一个 `catch` 块。</span><span class="sxs-lookup"><span data-stu-id="2e353-118">The first `catch` block that specifies the exact type or a base class of the thrown exception is executed.</span></span> <span data-ttu-id="2e353-119">如果没有 `catch` 块指定匹配的异常筛选器，则将选择不具有筛选器的 `catch` 块（如果语句中存在）。</span><span class="sxs-lookup"><span data-stu-id="2e353-119">If no `catch` block specifies a matching exception filter, a `catch` block that does not have a filter is selected, if one is present in the statement.</span></span> <span data-ttu-id="2e353-120">务必首先定位具有最具体的（即，最底层派生的）异常类型的 `catch` 块。</span><span class="sxs-lookup"><span data-stu-id="2e353-120">It is important to position `catch` blocks with the most specific (that is, the most derived) exception types first.</span></span>  
  
 <span data-ttu-id="2e353-121">应当会在下列条件为 true 时捕获到异常：</span><span class="sxs-lookup"><span data-stu-id="2e353-121">You should catch exceptions when the following conditions are true:</span></span>  
  
- <span data-ttu-id="2e353-122">能够很好地理解可能会引发异常的原因，并且可以实现特定的恢复，例如捕获 <xref:System.IO.FileNotFoundException> 对象时提示用户输入新文件名。</span><span class="sxs-lookup"><span data-stu-id="2e353-122">You have a good understanding of why the exception might be thrown, and you can implement a specific recovery, such as prompting the user to enter a new file name when you catch a <xref:System.IO.FileNotFoundException> object.</span></span>  
  
- <span data-ttu-id="2e353-123">可以创建和引发一个新的、更具体的异常。</span><span class="sxs-lookup"><span data-stu-id="2e353-123">You can create and throw a new, more specific exception.</span></span>  
  
     [!code-csharp[csProgGuideExceptions#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#9)]  
  
- <span data-ttu-id="2e353-124">想要先对异常进行部分处理，然后再将其传递以进行额外处理。</span><span class="sxs-lookup"><span data-stu-id="2e353-124">You want to partially handle an exception before passing it on for additional handling.</span></span> <span data-ttu-id="2e353-125">在下面的示例中，`catch` 块用于在重新引发异常之前将条目添加到错误日志。</span><span class="sxs-lookup"><span data-stu-id="2e353-125">In the following example, a `catch` block is used to add an entry to an error log before re-throwing the exception.</span></span>  
  
     [!code-csharp[csProgGuideExceptions#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#10)]  
  
## <a name="finally-blocks"></a><span data-ttu-id="2e353-126">Finally 块</span><span class="sxs-lookup"><span data-stu-id="2e353-126">Finally Blocks</span></span>  

 <span data-ttu-id="2e353-127">`finally` 块让你可以清理在 `try` 块中所执行的操作。</span><span class="sxs-lookup"><span data-stu-id="2e353-127">A `finally` block enables you to clean up actions that are performed in a `try` block.</span></span> <span data-ttu-id="2e353-128">如果存在 `finally` 块，将在执行 `try` 块和任何匹配的 `catch` 块之后，最后执行它。</span><span class="sxs-lookup"><span data-stu-id="2e353-128">If present, the `finally` block executes last, after the `try` block and any matched `catch` block.</span></span> <span data-ttu-id="2e353-129">无论是否会引发异常或找到匹配异常类型的 `catch` 块，`finally` 块都将始终运行。</span><span class="sxs-lookup"><span data-stu-id="2e353-129">A `finally` block always runs, regardless of whether an exception is thrown or a `catch` block matching the exception type is found.</span></span>  
  
 <span data-ttu-id="2e353-130">`finally` 块可用于发布资源（如文件流、数据库连接和图形句柄）而无需等待运行时中的垃圾回收器来完成对象。</span><span class="sxs-lookup"><span data-stu-id="2e353-130">The `finally` block can be used to release resources such as file streams, database connections, and graphics handles without waiting for the garbage collector in the runtime to finalize the objects.</span></span> <span data-ttu-id="2e353-131">有关详细信息，请参阅 [using 语句](../../language-reference/keywords/using-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="2e353-131">See [using Statement](../../language-reference/keywords/using-statement.md) for more information.</span></span>  
  
 <span data-ttu-id="2e353-132">在下面的示例中，`finally` 块用于关闭在 `try` 块中打开的文件。</span><span class="sxs-lookup"><span data-stu-id="2e353-132">In the following example, the `finally` block is used to close a file that is opened in the `try` block.</span></span> <span data-ttu-id="2e353-133">请注意，在关闭文件之前，将检查文件句柄的状态。</span><span class="sxs-lookup"><span data-stu-id="2e353-133">Notice that the state of the file handle is checked before the file is closed.</span></span> <span data-ttu-id="2e353-134">如果 `try` 块不能打开文件，则文件句柄仍将具有值 `null` 且 `finally` 块不会尝试将其关闭。</span><span class="sxs-lookup"><span data-stu-id="2e353-134">If the `try` block cannot open the file, the file handle still has the value `null` and the `finally` block does not try to close it.</span></span> <span data-ttu-id="2e353-135">或者，如果在 `try` 块中成功打开文件，则 `finally` 块将关闭打开的文件。</span><span class="sxs-lookup"><span data-stu-id="2e353-135">Alternatively, if the file is opened successfully in the `try` block, the `finally` block closes the open file.</span></span>  
  
 [!code-csharp[csProgGuideExceptions#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#11)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="2e353-136">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="2e353-136">C# Language Specification</span></span>  

<span data-ttu-id="2e353-137">有关详细信息，请参阅 [C# 语言规范](/dotnet/csharp/language-reference/language-specification/introduction)中的[异常](~/_csharplang/spec/exceptions.md)和 [try 语句](~/_csharplang/spec/statements.md#the-try-statement)。</span><span class="sxs-lookup"><span data-stu-id="2e353-137">For more information, see [Exceptions](~/_csharplang/spec/exceptions.md) and [The try statement](~/_csharplang/spec/statements.md#the-try-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="2e353-138">该语言规范是 C# 语法和用法的权威资料。</span><span class="sxs-lookup"><span data-stu-id="2e353-138">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2e353-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="2e353-139">See also</span></span>

- [<span data-ttu-id="2e353-140">C# 参考</span><span class="sxs-lookup"><span data-stu-id="2e353-140">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="2e353-141">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="2e353-141">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2e353-142">异常和异常处理</span><span class="sxs-lookup"><span data-stu-id="2e353-142">Exceptions and Exception Handling</span></span>](./index.md)
- [<span data-ttu-id="2e353-143">try-catch</span><span class="sxs-lookup"><span data-stu-id="2e353-143">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="2e353-144">try-finally</span><span class="sxs-lookup"><span data-stu-id="2e353-144">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="2e353-145">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="2e353-145">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
- [<span data-ttu-id="2e353-146">using 语句</span><span class="sxs-lookup"><span data-stu-id="2e353-146">using Statement</span></span>](../../language-reference/keywords/using-statement.md)

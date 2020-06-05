---
title: 尝试 .。。Catch .。。Finally 语句
description: 了解如何对 Visual Basic Try/Catch/Finally 语句使用异常处理。
ms.date: 12/07/2018
f1_keywords:
- vb.Try...Catch...Finally
- vb.when
- vb.Finally
- vb.Catch
- vb.Try
helpviewer_keywords:
- Try...Catch...Finally statements
- Try statement [Visual Basic]
- try-catch exception handling, Try...Catch...Finally statements
- error handling, while running code
- Try statement [Visual Basic], Try...Catch...Finally
- Finally keyword [Visual Basic], Try...Catch...Finally
- Catch statement [Visual Basic]
- When keyword [Visual Basic]
- Visual Basic code, handling errors while running
- structured exception handling, Try...Catch...Finally statements
ms.assetid: d6488026-ccb3-42b8-a810-0d97b9d6472b
ms.openlocfilehash: 22f1611786a3da512632b5b547b7ef141c8f65c6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84391763"
---
# <a name="trycatchfinally-statement-visual-basic"></a><span data-ttu-id="14f31-103">Try...Catch...Finally 语句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14f31-103">Try...Catch...Finally Statement (Visual Basic)</span></span>

<span data-ttu-id="14f31-104">提供了一种方法，用于处理给定代码块中可能发生的一些或所有可能的错误，同时仍在运行代码。</span><span class="sxs-lookup"><span data-stu-id="14f31-104">Provides a way to handle some or all possible errors that may occur in a given block of code, while still running code.</span></span>

## <a name="syntax"></a><span data-ttu-id="14f31-105">语法</span><span class="sxs-lookup"><span data-stu-id="14f31-105">Syntax</span></span>

```vb
Try
    [ tryStatements ]
    [ Exit Try ]
[ Catch [ exception [ As type ] ] [ When expression ]
    [ catchStatements ]
    [ Exit Try ] ]
[ Catch ... ]
[ Finally
    [ finallyStatements ] ]
End Try
```

## <a name="parts"></a><span data-ttu-id="14f31-106">组成部分</span><span class="sxs-lookup"><span data-stu-id="14f31-106">Parts</span></span>

|<span data-ttu-id="14f31-107">术语</span><span class="sxs-lookup"><span data-stu-id="14f31-107">Term</span></span>|<span data-ttu-id="14f31-108">定义</span><span class="sxs-lookup"><span data-stu-id="14f31-108">Definition</span></span>|
|---|---|
|`tryStatements`|<span data-ttu-id="14f31-109">可选。</span><span class="sxs-lookup"><span data-stu-id="14f31-109">Optional.</span></span> <span data-ttu-id="14f31-110">可能发生错误的语句。</span><span class="sxs-lookup"><span data-stu-id="14f31-110">Statement(s) where an error can occur.</span></span> <span data-ttu-id="14f31-111">可以是复合语句。</span><span class="sxs-lookup"><span data-stu-id="14f31-111">Can be a compound statement.</span></span>|
|`Catch`|<span data-ttu-id="14f31-112">可选。</span><span class="sxs-lookup"><span data-stu-id="14f31-112">Optional.</span></span> <span data-ttu-id="14f31-113">允许多个 `Catch` 块。</span><span class="sxs-lookup"><span data-stu-id="14f31-113">Multiple `Catch` blocks permitted.</span></span> <span data-ttu-id="14f31-114">如果在处理块时出现异常 `Try` ， `Catch` 则将以文本顺序检查每个语句，以确定它是否处理异常，并 `exception` 表示已引发的异常。</span><span class="sxs-lookup"><span data-stu-id="14f31-114">If an exception occurs when processing the `Try` block, each `Catch` statement is examined in textual order to determine whether it handles the exception, with `exception` representing the exception that has been thrown.</span></span>|
|`exception`|<span data-ttu-id="14f31-115">可选。</span><span class="sxs-lookup"><span data-stu-id="14f31-115">Optional.</span></span> <span data-ttu-id="14f31-116">任何变量名称。</span><span class="sxs-lookup"><span data-stu-id="14f31-116">Any variable name.</span></span> <span data-ttu-id="14f31-117">`exception` 的初始值是引发的错误的值。</span><span class="sxs-lookup"><span data-stu-id="14f31-117">The initial value of `exception` is the value of the thrown error.</span></span> <span data-ttu-id="14f31-118">与一起使用 `Catch` 以指定捕获的错误。</span><span class="sxs-lookup"><span data-stu-id="14f31-118">Used with `Catch` to specify the error caught.</span></span> <span data-ttu-id="14f31-119">如果省略，则该 `Catch` 语句将捕获任何异常。</span><span class="sxs-lookup"><span data-stu-id="14f31-119">If omitted, the `Catch` statement catches any exception.</span></span>|
|`type`|<span data-ttu-id="14f31-120">可选。</span><span class="sxs-lookup"><span data-stu-id="14f31-120">Optional.</span></span> <span data-ttu-id="14f31-121">指定类筛选器的类型。</span><span class="sxs-lookup"><span data-stu-id="14f31-121">Specifies the type of class filter.</span></span> <span data-ttu-id="14f31-122">如果的值 `exception` 是由 `type` 或派生类型指定的类型，则该标识符将绑定到异常对象。</span><span class="sxs-lookup"><span data-stu-id="14f31-122">If the value of `exception` is of the type specified by `type` or of a derived type, the identifier becomes bound to the exception object.</span></span>|
|`When`|<span data-ttu-id="14f31-123">可选。</span><span class="sxs-lookup"><span data-stu-id="14f31-123">Optional.</span></span> <span data-ttu-id="14f31-124">`Catch`带有子句的语句 `When` 仅在计算结果为时才捕获异常 `expression` `True` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-124">A `Catch` statement with a `When` clause catches exceptions only when `expression` evaluates to `True`.</span></span> <span data-ttu-id="14f31-125">`When`子句仅在检查异常的类型后应用，并且 `expression` 可以引用表示异常的标识符。</span><span class="sxs-lookup"><span data-stu-id="14f31-125">A `When` clause is applied only after checking the type of the exception, and `expression` may refer to the identifier representing the exception.</span></span>|
|`expression`|<span data-ttu-id="14f31-126">可选。</span><span class="sxs-lookup"><span data-stu-id="14f31-126">Optional.</span></span> <span data-ttu-id="14f31-127">必须可隐式转换为 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-127">Must be implicitly convertible to `Boolean`.</span></span> <span data-ttu-id="14f31-128">描述泛型筛选器的任何表达式。</span><span class="sxs-lookup"><span data-stu-id="14f31-128">Any expression that describes a generic filter.</span></span> <span data-ttu-id="14f31-129">通常用于按错误号进行筛选。</span><span class="sxs-lookup"><span data-stu-id="14f31-129">Typically used to filter by error number.</span></span> <span data-ttu-id="14f31-130">与关键字一起使用 `When` ，以指定捕获错误的情况。</span><span class="sxs-lookup"><span data-stu-id="14f31-130">Used with `When` keyword to specify circumstances under which the error is caught.</span></span>|
|`catchStatements`|<span data-ttu-id="14f31-131">可选。</span><span class="sxs-lookup"><span data-stu-id="14f31-131">Optional.</span></span> <span data-ttu-id="14f31-132">用于处理关联块中发生的错误的语句 `Try` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-132">Statement(s) to handle errors that occur in the associated `Try` block.</span></span> <span data-ttu-id="14f31-133">可以是复合语句。</span><span class="sxs-lookup"><span data-stu-id="14f31-133">Can be a compound statement.</span></span>|
|`Exit Try`|<span data-ttu-id="14f31-134">可选。</span><span class="sxs-lookup"><span data-stu-id="14f31-134">Optional.</span></span> <span data-ttu-id="14f31-135">用于中断结构的关键字 `Try...Catch...Finally` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-135">Keyword that breaks out of the `Try...Catch...Finally` structure.</span></span> <span data-ttu-id="14f31-136">继续执行语句后面的代码 `End Try` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-136">Execution resumes with the code immediately following the `End Try` statement.</span></span> <span data-ttu-id="14f31-137">`Finally`语句仍将被执行。</span><span class="sxs-lookup"><span data-stu-id="14f31-137">The `Finally` statement will still be executed.</span></span> <span data-ttu-id="14f31-138">不允许在 `Finally` 块中使用。</span><span class="sxs-lookup"><span data-stu-id="14f31-138">Not allowed in `Finally` blocks.</span></span>|
|`Finally`|<span data-ttu-id="14f31-139">可选。</span><span class="sxs-lookup"><span data-stu-id="14f31-139">Optional.</span></span> <span data-ttu-id="14f31-140">`Finally`当执行离开语句的任何部分时，始终会执行块 `Try...Catch` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-140">A `Finally` block is always executed when execution leaves any part of the `Try...Catch` statement.</span></span>|
|`finallyStatements`|<span data-ttu-id="14f31-141">可选。</span><span class="sxs-lookup"><span data-stu-id="14f31-141">Optional.</span></span> <span data-ttu-id="14f31-142">在所有其他错误处理发生之后执行的语句。</span><span class="sxs-lookup"><span data-stu-id="14f31-142">Statement(s) that are executed after all other error processing has occurred.</span></span>|
|`End Try`|<span data-ttu-id="14f31-143">终止 `Try...Catch...Finally` 结构。</span><span class="sxs-lookup"><span data-stu-id="14f31-143">Terminates the `Try...Catch...Finally` structure.</span></span>|

## <a name="remarks"></a><span data-ttu-id="14f31-144">备注</span><span class="sxs-lookup"><span data-stu-id="14f31-144">Remarks</span></span>

<span data-ttu-id="14f31-145">如果预计在代码的特定部分中可能出现特定的异常，请将代码放在块中， `Try` 使用 `Catch` 块保留控件并处理异常（如果发生）。</span><span class="sxs-lookup"><span data-stu-id="14f31-145">If you expect that a particular exception might occur during a particular section of code, put the code in a `Try` block and use a `Catch` block to retain control and handle the exception if it occurs.</span></span>

<span data-ttu-id="14f31-146">`Try…Catch`语句由一个 `Try` 块后跟一个或多个 `Catch` 子句组成，这些子句指定不同异常的处理程序。</span><span class="sxs-lookup"><span data-stu-id="14f31-146">A `Try…Catch` statement consists of a `Try` block followed by one or more `Catch` clauses, which specify handlers for various exceptions.</span></span> <span data-ttu-id="14f31-147">在块中引发异常时 `Try` ，Visual Basic 将查找 `Catch` 处理异常的语句。</span><span class="sxs-lookup"><span data-stu-id="14f31-147">When an exception is thrown in a `Try` block, Visual Basic looks for the `Catch` statement that handles the exception.</span></span> <span data-ttu-id="14f31-148">如果找不到匹配的 `Catch` 语句，Visual Basic 将检查调用当前方法的方法，并在调用堆栈上向上进行。</span><span class="sxs-lookup"><span data-stu-id="14f31-148">If a matching `Catch` statement is not found, Visual Basic examines the method that called the current method, and so on up the call stack.</span></span> <span data-ttu-id="14f31-149">如果未 `Catch` 找到任何块，则 Visual Basic 向用户显示未处理的异常消息，并停止执行程序。</span><span class="sxs-lookup"><span data-stu-id="14f31-149">If no `Catch` block is found, Visual Basic displays an unhandled exception message to the user and stops execution of the program.</span></span>

<span data-ttu-id="14f31-150">您可以 `Catch` 在一个语句中使用多个语句 `Try…Catch` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-150">You can use more than one `Catch` statement in a `Try…Catch` statement.</span></span> <span data-ttu-id="14f31-151">如果这样做，子句的顺序很 `Catch` 重要，因为它们是按顺序进行检查的。</span><span class="sxs-lookup"><span data-stu-id="14f31-151">If you do this, the order of the `Catch` clauses is significant because they are examined in order.</span></span> <span data-ttu-id="14f31-152">在使用更笼统的子句之前获取特定性更强的异常。</span><span class="sxs-lookup"><span data-stu-id="14f31-152">Catch the more specific exceptions before the less specific ones.</span></span>

<span data-ttu-id="14f31-153">以下 `Catch` 语句条件是最不具体的条件，将捕获派生自类的所有异常 <xref:System.Exception> 。</span><span class="sxs-lookup"><span data-stu-id="14f31-153">The following `Catch` statement conditions are the least specific, and will catch all exceptions that derive from the <xref:System.Exception> class.</span></span> <span data-ttu-id="14f31-154">在 `Catch` `Try...Catch...Finally` 捕获所需的所有特定异常后，通常应将这些变体中的一个作为结构的最后一个块。</span><span class="sxs-lookup"><span data-stu-id="14f31-154">You should ordinarily use one of these variations as the last `Catch` block in the `Try...Catch...Finally` structure, after catching all the specific exceptions you expect.</span></span> <span data-ttu-id="14f31-155">控制流永远不会到达 `Catch` 遵循这些变化之一的块。</span><span class="sxs-lookup"><span data-stu-id="14f31-155">Control flow can never reach a `Catch` block that follows either of these variations.</span></span>

- <span data-ttu-id="14f31-156">`type`为 `Exception` ，例如：`Catch ex As Exception`</span><span class="sxs-lookup"><span data-stu-id="14f31-156">The `type` is `Exception`, for example: `Catch ex As Exception`</span></span>

- <span data-ttu-id="14f31-157">语句没有 `exception` 变量，例如：`Catch`</span><span class="sxs-lookup"><span data-stu-id="14f31-157">The statement has no `exception` variable, for example: `Catch`</span></span>

<span data-ttu-id="14f31-158">如果 `Try…Catch…Finally` 语句嵌套在另一个 `Try` 块中，Visual Basic 首先检查 `Catch` 最内层块中的每个语句 `Try` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-158">When a `Try…Catch…Finally` statement is nested in another `Try` block, Visual Basic first examines each `Catch` statement in the innermost `Try` block.</span></span> <span data-ttu-id="14f31-159">如果未找到任何匹配 `Catch` 的语句，则搜索将继续对 `Catch` 外部块的语句执行 `Try…Catch…Finally` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-159">If no matching `Catch` statement is found, the search proceeds to the `Catch` statements of the outer `Try…Catch…Finally` block.</span></span>

<span data-ttu-id="14f31-160">块中的局部变量 `Try` 在块中不可用， `Catch` 因为它们是单独的块。</span><span class="sxs-lookup"><span data-stu-id="14f31-160">Local variables from a `Try` block are not available in a `Catch` block because they are separate blocks.</span></span> <span data-ttu-id="14f31-161">如果要在多个块中使用变量，请在结构外声明变量 `Try...Catch...Finally` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-161">If you want to use a variable in more than one block, declare the variable outside the `Try...Catch...Finally` structure.</span></span>

> [!TIP]
> <span data-ttu-id="14f31-162">`Try…Catch…Finally`语句作为 IntelliSense 代码段提供。</span><span class="sxs-lookup"><span data-stu-id="14f31-162">The `Try…Catch…Finally` statement is available as an IntelliSense code snippet.</span></span> <span data-ttu-id="14f31-163">在 "代码片段管理器" 中，展开 "**代码模式"-如果为，则依次尝试 Catch、Property**等，然后进行**错误处理（异常）**。</span><span class="sxs-lookup"><span data-stu-id="14f31-163">In the Code Snippets Manager, expand **Code Patterns - If, For Each, Try Catch, Property, etc**, and then **Error Handling (Exceptions)**.</span></span> <span data-ttu-id="14f31-164">有关详细信息，请参阅[代码片段](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="14f31-164">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>

## <a name="finally-block"></a><span data-ttu-id="14f31-165">Finally 块</span><span class="sxs-lookup"><span data-stu-id="14f31-165">Finally block</span></span>

<span data-ttu-id="14f31-166">如果有一个或多个必须在退出结构之前运行的语句 `Try` ，请使用 `Finally` 块。</span><span class="sxs-lookup"><span data-stu-id="14f31-166">If you have one or more statements that must run before you exit the `Try` structure, use a `Finally` block.</span></span> <span data-ttu-id="14f31-167">控件在传递到 `Finally` 结构外之前传递到块 `Try…Catch` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-167">Control passes to the `Finally` block just before it passes out of the `Try…Catch` structure.</span></span> <span data-ttu-id="14f31-168">即使结构内的任何位置发生异常，也是如此 `Try` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-168">This is true even if an exception occurs anywhere inside the `Try` structure.</span></span>

<span data-ttu-id="14f31-169">`Finally`块可用于运行任何必须执行的代码，即使存在异常也是如此。</span><span class="sxs-lookup"><span data-stu-id="14f31-169">A `Finally` block is useful for running any code that must execute even if there is an exception.</span></span> <span data-ttu-id="14f31-170">`Finally`无论块退出的方式如何，都将控制传递到块 `Try...Catch` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-170">Control is passed to the `Finally` block regardless of how the `Try...Catch` block exits.</span></span>

<span data-ttu-id="14f31-171">`Finally`即使代码遇到 `Return` 或块中的语句，块中的代码也会 `Try` 运行 `Catch` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-171">The code in a `Finally` block runs even if your code encounters a `Return` statement in a `Try` or `Catch` block.</span></span> <span data-ttu-id="14f31-172">在以下情况下，控件不会从 `Try` 或 `Catch` 块传递到相应的 `Finally` 块：</span><span class="sxs-lookup"><span data-stu-id="14f31-172">Control does not pass from a `Try` or `Catch` block to the corresponding `Finally` block in the following cases:</span></span>

- <span data-ttu-id="14f31-173">在或块中遇到[结束语句](end-statement.md) `Try` `Catch` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-173">An [End Statement](end-statement.md) is encountered in the `Try` or `Catch` block.</span></span>

- <span data-ttu-id="14f31-174">在 <xref:System.StackOverflowException> 或块中引发 `Try` `Catch` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-174">A <xref:System.StackOverflowException> is thrown in the `Try` or `Catch` block.</span></span>

<span data-ttu-id="14f31-175">将执行显式传输到块中是无效的 `Finally` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-175">It is not valid to explicitly transfer execution into a `Finally` block.</span></span> <span data-ttu-id="14f31-176">`Finally`除了通过异常以外，将执行转移到块外是无效的。</span><span class="sxs-lookup"><span data-stu-id="14f31-176">Transferring execution out of a `Finally` block is not valid, except through an exception.</span></span>

<span data-ttu-id="14f31-177">如果 `Try` 语句不包含至少一个 `Catch` 块，则它必须包含一个 `Finally` 块。</span><span class="sxs-lookup"><span data-stu-id="14f31-177">If a `Try` statement does not contain at least one `Catch` block, it must contain a `Finally` block.</span></span>

> [!TIP]
> <span data-ttu-id="14f31-178">如果不必捕获特定的异常，则该语句的 `Using` 行为类似于 `Try…Finally` 块，并保证资源的处置，而不管退出块的方式如何。</span><span class="sxs-lookup"><span data-stu-id="14f31-178">If you do not have to catch specific exceptions, the `Using` statement behaves like a `Try…Finally` block, and guarantees disposal of the resources, regardless of how you exit the block.</span></span> <span data-ttu-id="14f31-179">即使出现未经处理的异常也是如此。</span><span class="sxs-lookup"><span data-stu-id="14f31-179">This is true even with an unhandled exception.</span></span> <span data-ttu-id="14f31-180">有关详细信息，请参阅[Using 语句](using-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="14f31-180">For more information, see [Using Statement](using-statement.md).</span></span>

## <a name="exception-argument"></a><span data-ttu-id="14f31-181">异常参数</span><span class="sxs-lookup"><span data-stu-id="14f31-181">Exception argument</span></span>

<span data-ttu-id="14f31-182">`Catch`块 `exception` 参数是类的实例 <xref:System.Exception> ，或者是从类派生的类 `Exception` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-182">The `Catch` block `exception` argument is an instance of the <xref:System.Exception> class or a class that derives from the `Exception` class.</span></span> <span data-ttu-id="14f31-183">`Exception`类实例对应于块中发生的错误 `Try` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-183">The `Exception` class instance corresponds to the error that occurred in the `Try` block.</span></span>

<span data-ttu-id="14f31-184">对象的属性 `Exception` 可帮助确定异常的原因和位置。</span><span class="sxs-lookup"><span data-stu-id="14f31-184">The properties of the `Exception` object help to identify the cause and location of an exception.</span></span> <span data-ttu-id="14f31-185">例如，属性将 <xref:System.Exception.StackTrace%2A> 列出导致异常的被调用方法，从而帮助你查找代码中发生错误的位置。</span><span class="sxs-lookup"><span data-stu-id="14f31-185">For example, the <xref:System.Exception.StackTrace%2A> property lists the called methods that led to the exception, helping you find where the error occurred in the code.</span></span> <span data-ttu-id="14f31-186"><xref:System.Exception.Message%2A>返回描述异常的消息。</span><span class="sxs-lookup"><span data-stu-id="14f31-186"><xref:System.Exception.Message%2A> returns a message that describes the exception.</span></span> <span data-ttu-id="14f31-187"><xref:System.Exception.HelpLink%2A>返回指向关联帮助文件的链接。</span><span class="sxs-lookup"><span data-stu-id="14f31-187"><xref:System.Exception.HelpLink%2A> returns a link to an associated Help file.</span></span> <span data-ttu-id="14f31-188"><xref:System.Exception.InnerException%2A>返回 `Exception` 导致当前异常的对象; 或者，如果没有原始异常，则返回该对象 `Nothing` `Exception` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-188"><xref:System.Exception.InnerException%2A> returns the `Exception` object that caused the current exception, or it returns `Nothing` if there is no original `Exception`.</span></span>

## <a name="considerations-when-using-a-trycatch-statement"></a><span data-ttu-id="14f31-189">使用 Try ... 时的注意事项Catch 语句</span><span class="sxs-lookup"><span data-stu-id="14f31-189">Considerations when using a Try…Catch statement</span></span>

<span data-ttu-id="14f31-190">只使用 `Try…Catch` 语句来表明出现异常或意外的程序事件。</span><span class="sxs-lookup"><span data-stu-id="14f31-190">Use a `Try…Catch` statement only to signal the occurrence of unusual or unanticipated program events.</span></span> <span data-ttu-id="14f31-191">原因如下：</span><span class="sxs-lookup"><span data-stu-id="14f31-191">Reasons for this include the following:</span></span>

- <span data-ttu-id="14f31-192">在运行时捕获异常将产生额外的开销，并且可能比预检查更慢，以避免异常。</span><span class="sxs-lookup"><span data-stu-id="14f31-192">Catching exceptions at runtime creates additional overhead, and is likely to be slower than pre-checking to avoid exceptions.</span></span>

- <span data-ttu-id="14f31-193">如果 `Catch` 未正确处理某个块，则可能不会正确向用户报告该异常。</span><span class="sxs-lookup"><span data-stu-id="14f31-193">If a `Catch` block is not handled correctly, the exception might not be reported correctly to users.</span></span>

- <span data-ttu-id="14f31-194">异常处理使程序更复杂。</span><span class="sxs-lookup"><span data-stu-id="14f31-194">Exception handling makes a program more complex.</span></span>

<span data-ttu-id="14f31-195">并非始终需要 `Try…Catch` 语句来检查可能出现的情况。</span><span class="sxs-lookup"><span data-stu-id="14f31-195">You do not always need a `Try…Catch` statement to check for a condition that is likely to occur.</span></span> <span data-ttu-id="14f31-196">下面的示例检查文件是否存在，然后再尝试打开它。</span><span class="sxs-lookup"><span data-stu-id="14f31-196">The following example checks whether a file exists before trying to open it.</span></span> <span data-ttu-id="14f31-197">这减少了捕获由方法引发的异常的需求 <xref:System.IO.File.OpenText%2A> 。</span><span class="sxs-lookup"><span data-stu-id="14f31-197">This reduces the need for catching an exception thrown by the <xref:System.IO.File.OpenText%2A> method.</span></span>

[!code-vb[VbVbalrStatements#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#94)]

<span data-ttu-id="14f31-198">确保块中的代码 `Catch` 可以正确地向用户报告异常，无论是通过线程安全日志记录还是适当的消息。</span><span class="sxs-lookup"><span data-stu-id="14f31-198">Ensure that code in `Catch` blocks can properly report exceptions to users, whether through thread-safe logging or appropriate messages.</span></span> <span data-ttu-id="14f31-199">否则，例外可能仍然未知。</span><span class="sxs-lookup"><span data-stu-id="14f31-199">Otherwise, exceptions might remain unknown.</span></span>

## <a name="async-methods"></a><span data-ttu-id="14f31-200">异步方法</span><span class="sxs-lookup"><span data-stu-id="14f31-200">Async methods</span></span>

<span data-ttu-id="14f31-201">如果用[Async](../modifiers/async.md)修饰符标记方法，可以在方法中使用[Await](../operators/await-operator.md)运算符。</span><span class="sxs-lookup"><span data-stu-id="14f31-201">If you mark a method with the [Async](../modifiers/async.md) modifier, you can use the [Await](../operators/await-operator.md) operator in the method.</span></span> <span data-ttu-id="14f31-202">带有运算符的语句 `Await` 挂起了方法的执行，直到等待的任务完成。</span><span class="sxs-lookup"><span data-stu-id="14f31-202">A statement with the `Await` operator suspends execution of the method until the awaited task completes.</span></span> <span data-ttu-id="14f31-203">任务表示正在进行的工作。</span><span class="sxs-lookup"><span data-stu-id="14f31-203">The task represents ongoing work.</span></span> <span data-ttu-id="14f31-204">当与运算符关联的任务完成时 `Await` ，将在同一方法中继续执行。</span><span class="sxs-lookup"><span data-stu-id="14f31-204">When the task that's associated with the `Await` operator finishes, execution resumes in the same method.</span></span> <span data-ttu-id="14f31-205">有关详细信息，请参阅[异步程序中的控制流](../../programming-guide/concepts/async/control-flow-in-async-programs.md)。</span><span class="sxs-lookup"><span data-stu-id="14f31-205">For more information, see [Control Flow in Async Programs](../../programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>

<span data-ttu-id="14f31-206">异步方法返回的任务可能会以错误状态结束，这表示它由于未处理的异常而完成。</span><span class="sxs-lookup"><span data-stu-id="14f31-206">A task returned by an Async method may end in a faulted state, indicating that it completed due to an unhandled exception.</span></span> <span data-ttu-id="14f31-207">任务还可以以 "已取消" 状态结束，导致 `OperationCanceledException` 从 await 表达式引发。</span><span class="sxs-lookup"><span data-stu-id="14f31-207">A task may also end in a canceled state, which results in an `OperationCanceledException` being thrown out of the await expression.</span></span> <span data-ttu-id="14f31-208">若要捕获任一类型的异常，请将 `Await` 与任务关联的表达式放置在 `Try` 块中，并在块中捕获该异常 `Catch` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-208">To catch either type of exception, place the `Await` expression that's associated with the task in a `Try` block, and catch the exception in the `Catch` block.</span></span> <span data-ttu-id="14f31-209">本主题后面提供了一个示例。</span><span class="sxs-lookup"><span data-stu-id="14f31-209">An example is provided later in this topic.</span></span>

<span data-ttu-id="14f31-210">任务可能处于错误状态，因为多个异常负责错误的发生。</span><span class="sxs-lookup"><span data-stu-id="14f31-210">A task can be in a faulted state because multiple exceptions were responsible for its faulting.</span></span> <span data-ttu-id="14f31-211">例如，任务可能是对 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> 调用的结果。</span><span class="sxs-lookup"><span data-stu-id="14f31-211">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="14f31-212">当你等待此类任务时，捕获的异常只是异常之一，你无法预测将捕获的异常。</span><span class="sxs-lookup"><span data-stu-id="14f31-212">When you await such a task, the caught exception is only one of the exceptions, and you can't predict which exception will be caught.</span></span> <span data-ttu-id="14f31-213">本主题后面提供了一个示例。</span><span class="sxs-lookup"><span data-stu-id="14f31-213">An example is provided later in this topic.</span></span>

<span data-ttu-id="14f31-214">`Await`表达式不能位于 `Catch` 块或块中 `Finally` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-214">An `Await` expression can't be inside a `Catch` block or `Finally` block.</span></span>

## <a name="iterators"></a><span data-ttu-id="14f31-215">迭代器</span><span class="sxs-lookup"><span data-stu-id="14f31-215">Iterators</span></span>

<span data-ttu-id="14f31-216">迭代器函数或 `Get` 访问器对集合执行自定义迭代。</span><span class="sxs-lookup"><span data-stu-id="14f31-216">An iterator function or `Get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="14f31-217">迭代器使用[Yield](yield-statement.md)语句每次返回集合中的每个元素。</span><span class="sxs-lookup"><span data-stu-id="14f31-217">An iterator uses a [Yield](yield-statement.md) statement to return each element of the collection one at a time.</span></span> <span data-ttu-id="14f31-218">您可以通过[对每个 .。。下一语句](for-each-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="14f31-218">You call an iterator function by using a [For Each...Next Statement](for-each-next-statement.md).</span></span>

<span data-ttu-id="14f31-219">`Yield`语句可以在 `Try` 块内。</span><span class="sxs-lookup"><span data-stu-id="14f31-219">A `Yield` statement can be inside a `Try` block.</span></span> <span data-ttu-id="14f31-220">`Try`包含语句的块 `Yield` 可以有 `Catch` 块，并且可以有 `Finally` 块。</span><span class="sxs-lookup"><span data-stu-id="14f31-220">A `Try` block that contains a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span> <span data-ttu-id="14f31-221">有关示例，请参阅[迭代](../../programming-guide/concepts/iterators.md)器中的 "Try 块 Visual Basic" 部分。</span><span class="sxs-lookup"><span data-stu-id="14f31-221">See the "Try Blocks in Visual Basic" section of [Iterators](../../programming-guide/concepts/iterators.md) for an example.</span></span>

<span data-ttu-id="14f31-222">`Yield`语句不能位于 `Catch` 块或 `Finally` 块中。</span><span class="sxs-lookup"><span data-stu-id="14f31-222">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>

<span data-ttu-id="14f31-223">如果 `For Each` 主体（在迭代器函数之外）引发异常，则 `Catch` 不会执行迭代器函数中的块，但 `Finally` 会执行迭代器函数中的块。</span><span class="sxs-lookup"><span data-stu-id="14f31-223">If the `For Each` body (outside of the iterator function) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="14f31-224">`Catch`Iterator 函数内的块仅捕获 iterator 函数内发生的异常。</span><span class="sxs-lookup"><span data-stu-id="14f31-224">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>

## <a name="partial-trust-situations"></a><span data-ttu-id="14f31-225">部分信任情况</span><span class="sxs-lookup"><span data-stu-id="14f31-225">Partial-trust situations</span></span>

<span data-ttu-id="14f31-226">在部分信任的情况下（例如在网络共享上托管的应用程序），不 `Try...Catch...Finally` 会捕获在调用包含调用的方法之前出现的安全异常。</span><span class="sxs-lookup"><span data-stu-id="14f31-226">In partial-trust situations, such as an application hosted on a network share, `Try...Catch...Finally` does not catch security exceptions that occur before the method that contains the call is invoked.</span></span> <span data-ttu-id="14f31-227">在以下示例中，当你将其放在服务器共享上并从该位置运行时，将产生错误 "SecurityException：请求失败"。</span><span class="sxs-lookup"><span data-stu-id="14f31-227">The following example, when you put it on a server share and run from there, produces the error "System.Security.SecurityException: Request Failed."</span></span> <span data-ttu-id="14f31-228">有关安全异常的详细信息，请参阅 <xref:System.Security.SecurityException> 类。</span><span class="sxs-lookup"><span data-stu-id="14f31-228">For more information about security exceptions, see the <xref:System.Security.SecurityException> class.</span></span>

[!code-vb[VbVbalrStatements#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#85)]

<span data-ttu-id="14f31-229">在这种部分信任情况下，必须将 `Process.Start` 语句放在单独的中 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-229">In such a partial-trust situation, you have to put the `Process.Start` statement in a separate `Sub`.</span></span> <span data-ttu-id="14f31-230">对的初始调用 `Sub` 将失败。</span><span class="sxs-lookup"><span data-stu-id="14f31-230">The initial call to the `Sub` will fail.</span></span> <span data-ttu-id="14f31-231">这样，便可以 `Try...Catch` 在包含的开始之前捕获它 `Sub` `Process.Start` 并生成安全异常。</span><span class="sxs-lookup"><span data-stu-id="14f31-231">This enables `Try...Catch` to catch it before the `Sub` that contains `Process.Start` is started and the security exception produced.</span></span>

## <a name="examples"></a><span data-ttu-id="14f31-232">示例</span><span class="sxs-lookup"><span data-stu-id="14f31-232">Examples</span></span>

### <a name="the-structure-of-trycatchfinally"></a><span data-ttu-id="14f31-233">Try ... 的结构Catch .。。最后</span><span class="sxs-lookup"><span data-stu-id="14f31-233">The structure of Try...Catch...Finally</span></span>

<span data-ttu-id="14f31-234">下面的示例阐释了语句的结构 `Try...Catch...Finally` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-234">The following example illustrates the structure of the `Try...Catch...Finally` statement.</span></span>

[!code-vb[VbVbalrStatements#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#86)]  

### <a name="exception-in-a-method-called-from-a-try-block"></a><span data-ttu-id="14f31-235">从 Try 块调用的方法中的异常</span><span class="sxs-lookup"><span data-stu-id="14f31-235">Exception in a method called from a Try block</span></span>

<span data-ttu-id="14f31-236">在下面的示例中， `CreateException` 方法引发 `NullReferenceException` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-236">In the following example, the `CreateException` method throws a `NullReferenceException`.</span></span> <span data-ttu-id="14f31-237">生成异常的代码不在 `Try` 块中。</span><span class="sxs-lookup"><span data-stu-id="14f31-237">The code that generates the exception is not in a `Try` block.</span></span> <span data-ttu-id="14f31-238">因此，该 `CreateException` 方法不会处理异常。</span><span class="sxs-lookup"><span data-stu-id="14f31-238">Therefore, the `CreateException` method does not handle the exception.</span></span> <span data-ttu-id="14f31-239">`RunSample`由于对方法的调用 `CreateException` 在块中，因此该方法会处理异常 `Try` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-239">The `RunSample` method does handle the exception because the call to the `CreateException` method is in a `Try` block.</span></span>

<span data-ttu-id="14f31-240">该示例包含 `Catch` 多个异常类型的语句，按从最具体到最常见的顺序排序。</span><span class="sxs-lookup"><span data-stu-id="14f31-240">The example includes `Catch` statements for several types of exceptions, ordered from the most specific to the most general.</span></span>

[!code-vb[VbVbalrStatements#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#91)]

### <a name="the-catch-when-statement"></a><span data-ttu-id="14f31-241">Catch When 语句</span><span class="sxs-lookup"><span data-stu-id="14f31-241">The Catch When statement</span></span>

<span data-ttu-id="14f31-242">下面的示例演示如何使用 `Catch When` 语句根据条件表达式进行筛选。</span><span class="sxs-lookup"><span data-stu-id="14f31-242">The following example shows how to use a `Catch When` statement to filter on a conditional expression.</span></span> <span data-ttu-id="14f31-243">如果条件表达式的计算结果为 `True` ，则块中的代码将 `Catch` 运行。</span><span class="sxs-lookup"><span data-stu-id="14f31-243">If the conditional expression evaluates to `True`, the code in the `Catch` block runs.</span></span>

[!code-vb[VbVbalrStatements#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#92)]

### <a name="nested-try-statements"></a><span data-ttu-id="14f31-244">嵌套 Try 语句</span><span class="sxs-lookup"><span data-stu-id="14f31-244">Nested Try statements</span></span>

<span data-ttu-id="14f31-245">下面的示例包含 `Try…Catch` 包含在块中的语句 `Try` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-245">The following example has a `Try…Catch` statement that is contained in a `Try` block.</span></span> <span data-ttu-id="14f31-246">内部 `Catch` 块引发了一个异常，该异常的 `InnerException` 属性设置为原始异常。</span><span class="sxs-lookup"><span data-stu-id="14f31-246">The inner `Catch` block throws an exception that has its `InnerException` property set to the original exception.</span></span> <span data-ttu-id="14f31-247">外部 `Catch` 块报告其自己的异常和内部异常。</span><span class="sxs-lookup"><span data-stu-id="14f31-247">The outer `Catch` block reports its own exception and the inner exception.</span></span>

[!code-vb[VbVbalrStatements#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#93)]

### <a name="exception-handling-for-async-methods"></a><span data-ttu-id="14f31-248">异步方法的异常处理</span><span class="sxs-lookup"><span data-stu-id="14f31-248">Exception handling for async methods</span></span>

<span data-ttu-id="14f31-249">下面的示例阐释异步方法的异常处理。</span><span class="sxs-lookup"><span data-stu-id="14f31-249">The following example illustrates exception handling for async methods.</span></span> <span data-ttu-id="14f31-250">若要捕获适用于异步任务的异常，该 `Await` 表达式位于 `Try` 调用方的块中，而在块中捕获该异常 `Catch` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-250">To catch an exception that applies to an async task, the `Await` expression is in a `Try` block of the caller, and the exception is caught in the `Catch` block.</span></span>

<span data-ttu-id="14f31-251">在示例中取消注释 `Throw New Exception` 行以演示异常处理。</span><span class="sxs-lookup"><span data-stu-id="14f31-251">Uncomment the `Throw New Exception` line in the example to demonstrate exception handling.</span></span> <span data-ttu-id="14f31-252">异常捕获于 `Catch` 块中，任务的 `IsFaulted` 属性设置为 `True` ，任务的 `Exception.InnerException` 属性设置为异常。</span><span class="sxs-lookup"><span data-stu-id="14f31-252">The exception is caught in the `Catch` block, the task's `IsFaulted` property is set to `True`, and the task's `Exception.InnerException` property is set to the exception.</span></span>

<span data-ttu-id="14f31-253">取消注释 `Throw New OperationCancelledException` 行以演示在取消异步进程时发生的情况。</span><span class="sxs-lookup"><span data-stu-id="14f31-253">Uncomment the `Throw New OperationCancelledException` line to demonstrate what happens when you cancel an asynchronous process.</span></span> <span data-ttu-id="14f31-254">异常捕获到 `Catch` 块中，任务的 `IsCanceled` 属性设置为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-254">The exception is caught in the `Catch` block, and the task's `IsCanceled` property is set to `True`.</span></span> <span data-ttu-id="14f31-255">但是，在某些不适用于此示例的情况下，将 `IsFaulted` 设置为 `True` ，并将 `IsCanceled` 设置为 `False` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-255">However, under some conditions that don't apply to this example, `IsFaulted` is set to `True` and `IsCanceled` is set to `False`.</span></span>

[!code-vb[csAsyncExceptions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#1)]

### <a name="handling-multiple-exceptions-in-async-methods"></a><span data-ttu-id="14f31-256">在异步方法中处理多个异常</span><span class="sxs-lookup"><span data-stu-id="14f31-256">Handling multiple exceptions in async methods</span></span>

<span data-ttu-id="14f31-257">下面的示例阐释了在多个任务可能导致多个异常的情况中的异常处理。</span><span class="sxs-lookup"><span data-stu-id="14f31-257">The following example illustrates exception handling where multiple tasks can result in multiple exceptions.</span></span> <span data-ttu-id="14f31-258">`Try`块具有返回的 `Await` 任务的表达式 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="14f31-258">The `Try` block has the `Await` expression for the task that <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> returned.</span></span> <span data-ttu-id="14f31-259">当应用的三个任务完成时，任务完成 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="14f31-259">The task is complete when the three tasks to which <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> is applied are complete.</span></span>

<span data-ttu-id="14f31-260">三个任务中的每一个都会导致异常。</span><span class="sxs-lookup"><span data-stu-id="14f31-260">Each of the three tasks causes an exception.</span></span> <span data-ttu-id="14f31-261">`Catch`块循环访问异常，这些异常在返回的任务的 `Exception.InnerExceptions` 属性中找到 `Task.WhenAll` 。</span><span class="sxs-lookup"><span data-stu-id="14f31-261">The `Catch` block iterates through the exceptions, which are found in the `Exception.InnerExceptions` property of the task that `Task.WhenAll` returned.</span></span>

[!code-vb[csAsyncExceptions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#3)]

## <a name="see-also"></a><span data-ttu-id="14f31-262">另请参阅</span><span class="sxs-lookup"><span data-stu-id="14f31-262">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:System.Exception>
- [<span data-ttu-id="14f31-263">Exit 语句</span><span class="sxs-lookup"><span data-stu-id="14f31-263">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="14f31-264">On Error 语句</span><span class="sxs-lookup"><span data-stu-id="14f31-264">On Error Statement</span></span>](on-error-statement.md)
- [<span data-ttu-id="14f31-265">使用代码片段的最佳做法</span><span class="sxs-lookup"><span data-stu-id="14f31-265">Best Practices for Using Code Snippets</span></span>](/visualstudio/ide/best-practices-for-using-code-snippets)
- [<span data-ttu-id="14f31-266">异常处理</span><span class="sxs-lookup"><span data-stu-id="14f31-266">Exception Handling</span></span>](../../../standard/parallel-programming/exception-handling-task-parallel-library.md)
- [<span data-ttu-id="14f31-267">Throw 语句</span><span class="sxs-lookup"><span data-stu-id="14f31-267">Throw Statement</span></span>](throw-statement.md)

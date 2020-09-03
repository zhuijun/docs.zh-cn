---
description: try-catch - C# 参考
title: try-catch - C# 参考
ms.date: 07/20/2015
f1_keywords:
- try
- try_CSharpKeyword
- catch
- catch_CSharpKeyword
helpviewer_keywords:
- catch keyword [C#]
- try-catch statement [C#]
ms.assetid: cb5503c7-bfa1-4610-8fc2-ddcd2e84c438
ms.openlocfilehash: e3154da2103029f704abd6873d16d372f1ae19ac
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141993"
---
# <a name="try-catch-c-reference"></a><span data-ttu-id="13a2f-103">try-catch（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="13a2f-103">try-catch (C# Reference)</span></span>

<span data-ttu-id="13a2f-104">Try-catch 语句包含一个后接一个或多个 `catch` 子句的 `try` 块，这些子句指定不同异常的处理程序。</span><span class="sxs-lookup"><span data-stu-id="13a2f-104">The try-catch statement consists of a `try` block followed by one or more `catch` clauses, which specify handlers for different exceptions.</span></span>

<span data-ttu-id="13a2f-105">引发异常时，公共语言运行时 (CLR) 查找处理此异常的 `catch` 语句。</span><span class="sxs-lookup"><span data-stu-id="13a2f-105">When an exception is thrown, the common language runtime (CLR) looks for the `catch` statement that handles this exception.</span></span> <span data-ttu-id="13a2f-106">如果当前正在执行的方法不包含此类 `catch` 块，则 CLR 查看调用了当前方法的方法，并以此类推遍历调用堆栈。</span><span class="sxs-lookup"><span data-stu-id="13a2f-106">If the currently executing method does not contain such a `catch` block, the CLR looks at the method that called the current method, and so on up the call stack.</span></span> <span data-ttu-id="13a2f-107">如果未找到任何 `catch` 块，则 CLR 向用户显示一条未处理的异常消息，并停止执行程序。</span><span class="sxs-lookup"><span data-stu-id="13a2f-107">If no `catch` block is found, then the CLR displays an unhandled exception message to the user and stops execution of the program.</span></span>

<span data-ttu-id="13a2f-108">`try` 块包含可能导致异常的受保护的代码。</span><span class="sxs-lookup"><span data-stu-id="13a2f-108">The `try` block contains the guarded code that may cause the exception.</span></span> <span data-ttu-id="13a2f-109">将执行此块，直至引发异常或其成功完成。</span><span class="sxs-lookup"><span data-stu-id="13a2f-109">The block is executed until an exception is thrown or it is completed successfully.</span></span> <span data-ttu-id="13a2f-110">例如，强制转换 `null` 对象的以下尝试会引发 <xref:System.NullReferenceException> 异常：</span><span class="sxs-lookup"><span data-stu-id="13a2f-110">For example, the following attempt to cast a `null` object raises the <xref:System.NullReferenceException> exception:</span></span>

```csharp
object o2 = null;
try
{
    int i2 = (int)o2;   // Error
}
```

<span data-ttu-id="13a2f-111">尽管可以不带参数使用 `catch` 子句来捕获任何类型的异常，但不推荐这种用法。</span><span class="sxs-lookup"><span data-stu-id="13a2f-111">Although the `catch` clause can be used without arguments to catch any type of exception, this usage is not recommended.</span></span> <span data-ttu-id="13a2f-112">一般情况下，只应捕获你知道如何从其恢复的异常。</span><span class="sxs-lookup"><span data-stu-id="13a2f-112">In general, you should only catch those exceptions that you know how to recover from.</span></span> <span data-ttu-id="13a2f-113">因此，应始终指定派生自 <xref:System.Exception?displayProperty=nameWithType> 的对象参数，例如：</span><span class="sxs-lookup"><span data-stu-id="13a2f-113">Therefore, you should always specify an object argument derived from <xref:System.Exception?displayProperty=nameWithType> For example:</span></span>

```csharp
catch (InvalidCastException e)
{
}
```

<span data-ttu-id="13a2f-114">可以使用同一 try-catch 语句中的多个特定 `catch` 子句。</span><span class="sxs-lookup"><span data-stu-id="13a2f-114">It is possible to use more than one specific `catch` clause in the same try-catch statement.</span></span> <span data-ttu-id="13a2f-115">在这种情况下，`catch` 子句的顺序很重要，因为 `catch` 子句是按顺序检查的。</span><span class="sxs-lookup"><span data-stu-id="13a2f-115">In this case, the order of the `catch` clauses is important because the `catch` clauses are examined in order.</span></span> <span data-ttu-id="13a2f-116">在使用更笼统的子句之前获取特定性更强的异常。</span><span class="sxs-lookup"><span data-stu-id="13a2f-116">Catch the more specific exceptions before the less specific ones.</span></span> <span data-ttu-id="13a2f-117">如果捕获块的排序使得永不会达到之后的块，则编译器将产生错误。</span><span class="sxs-lookup"><span data-stu-id="13a2f-117">The compiler produces an error if you order your catch blocks so that a later block can never be reached.</span></span>

<span data-ttu-id="13a2f-118">筛选想要处理的异常的一种方式是使用 `catch` 参数。</span><span class="sxs-lookup"><span data-stu-id="13a2f-118">Using `catch` arguments is one way to filter for the exceptions you want to handle.</span></span>  <span data-ttu-id="13a2f-119">也可以使用异常筛选器进一步检查该异常以决定是否要对其进行处理。</span><span class="sxs-lookup"><span data-stu-id="13a2f-119">You can also use an exception filter that further examines the exception to decide whether to handle it.</span></span>  <span data-ttu-id="13a2f-120">如果异常筛选器返回 false，则继续搜索处理程序。</span><span class="sxs-lookup"><span data-stu-id="13a2f-120">If the exception filter returns false, then the search for a handler continues.</span></span>

```csharp
catch (ArgumentException e) when (e.ParamName == "…")
{
}
```

<span data-ttu-id="13a2f-121">异常筛选器要优于捕获和重新引发（如下所述），因为筛选器将保留堆栈不受损坏。</span><span class="sxs-lookup"><span data-stu-id="13a2f-121">Exception filters are preferable to catching and rethrowing (explained below) because filters leave the stack unharmed.</span></span>  <span data-ttu-id="13a2f-122">如果之后的处理程序转储堆栈，可以查看到异常的原始来源，而不只是重新引发它的最后一个位置。</span><span class="sxs-lookup"><span data-stu-id="13a2f-122">If a later handler dumps the stack, you can see where the exception originally came from, rather than just the last place it was rethrown.</span></span>  <span data-ttu-id="13a2f-123">异常筛选器表达式的一个常见用途是日志记录。</span><span class="sxs-lookup"><span data-stu-id="13a2f-123">A common use of exception filter expressions is logging.</span></span>  <span data-ttu-id="13a2f-124">可以创建一个始终返回 false 并输出到日志的筛选器，能在异常通过时进行记录，且无需处理并重新引发它们。</span><span class="sxs-lookup"><span data-stu-id="13a2f-124">You can create a filter that always returns false that also outputs to a log, you can log exceptions as they go by without having to handle them and rethrow.</span></span>

<span data-ttu-id="13a2f-125">可在 `catch` 块中使用 [throw](throw.md) 语句以重新引发已由 `catch` 语句捕获的异常。</span><span class="sxs-lookup"><span data-stu-id="13a2f-125">A [throw](throw.md) statement can be used in a `catch` block to re-throw the exception that is caught by the `catch` statement.</span></span> <span data-ttu-id="13a2f-126">下面的示例从 <xref:System.IO.IOException> 异常提取源信息，然后向父方法引发异常。</span><span class="sxs-lookup"><span data-stu-id="13a2f-126">The following example extracts source information from an <xref:System.IO.IOException> exception, and then throws the exception to the parent method.</span></span>

```csharp
catch (FileNotFoundException e)
{
    // FileNotFoundExceptions are handled here.
}
catch (IOException e)
{
    // Extract some information from this exception, and then
    // throw it to the parent method.
    if (e.Source != null)
        Console.WriteLine("IOException source: {0}", e.Source);
    throw;
}
```

<span data-ttu-id="13a2f-127">你可以捕获一个异常而引发一个不同的异常。</span><span class="sxs-lookup"><span data-stu-id="13a2f-127">You can catch one exception and throw a different exception.</span></span> <span data-ttu-id="13a2f-128">执行此操作时，请指定作为内部异常捕获的异常，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="13a2f-128">When you do this, specify the exception that you caught as the inner exception, as shown in the following example.</span></span>

```csharp
catch (InvalidCastException e)
{
    // Perform some action here, and then throw a new exception.
    throw new YourCustomException("Put your error message here.", e);
}
```

<span data-ttu-id="13a2f-129">当指定的条件为 true 时，你还可以重新引发异常，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="13a2f-129">You can also re-throw an exception when a specified condition is true, as shown in the following example.</span></span>

```csharp
catch (InvalidCastException e)
{
    if (e.Data == null)
    {
        throw;
    }
    else
    {
        // Take some action.
    }
}
```

> [!NOTE]
> <span data-ttu-id="13a2f-130">还可以使用异常筛选器以更简洁的方式获取类似的结果（不修改堆栈，如本文档前面的部分所述）。</span><span class="sxs-lookup"><span data-stu-id="13a2f-130">It is also possible to use an exception filter to get a similar result in an often cleaner fashion (as well as not modifying the stack, as explained earlier in this document).</span></span> <span data-ttu-id="13a2f-131">下面的示例中，调用方的行为类似于前面的示例。</span><span class="sxs-lookup"><span data-stu-id="13a2f-131">The following example has a similar behavior for callers as the previous example.</span></span> <span data-ttu-id="13a2f-132">当 `e.Data` 为 `null` 时，该函数引发 `InvalidCastException` 返回至调用方。</span><span class="sxs-lookup"><span data-stu-id="13a2f-132">The function throws the `InvalidCastException` back to the caller when `e.Data` is `null`.</span></span>
>
> ```csharp
> catch (InvalidCastException e) when (e.Data != null)
> {
>     // Take some action.
> }
> ```

<span data-ttu-id="13a2f-133">从 `try` 块内，仅初始化在其中声明的变量。</span><span class="sxs-lookup"><span data-stu-id="13a2f-133">From inside a `try` block, initialize only variables that are declared therein.</span></span> <span data-ttu-id="13a2f-134">否则，在完成执行块之前，可能会出现异常。</span><span class="sxs-lookup"><span data-stu-id="13a2f-134">Otherwise, an exception can occur before the execution of the block is completed.</span></span> <span data-ttu-id="13a2f-135">例如，在下面的代码示例中，变量 `n` 在 `try` 块内部初始化。</span><span class="sxs-lookup"><span data-stu-id="13a2f-135">For example, in the following code example, the variable `n` is initialized inside the `try` block.</span></span> <span data-ttu-id="13a2f-136">尝试在 `Write(n)` 语句的 `try` 块外部使用此变量将生成编译器错误。</span><span class="sxs-lookup"><span data-stu-id="13a2f-136">An attempt to use this variable outside the `try` block in the `Write(n)` statement will generate a compiler error.</span></span>

```csharp
static void Main()
{
    int n;
    try
    {
        // Do not initialize this variable here.
        n = 123;
    }
    catch
    {
    }
    // Error: Use of unassigned local variable 'n'.
    Console.Write(n);
}
```

<span data-ttu-id="13a2f-137">有关 catch 的详细信息，请参阅 [try-catch-finally](try-catch-finally.md)。</span><span class="sxs-lookup"><span data-stu-id="13a2f-137">For more information about catch, see [try-catch-finally](try-catch-finally.md).</span></span>

## <a name="exceptions-in-async-methods"></a><span data-ttu-id="13a2f-138">异步方法中的异常</span><span class="sxs-lookup"><span data-stu-id="13a2f-138">Exceptions in async methods</span></span>

<span data-ttu-id="13a2f-139">异步方法由 [async](async.md) 修饰符标记，通常包含一个或多个 await 表达式或语句。</span><span class="sxs-lookup"><span data-stu-id="13a2f-139">An async method is marked  by an  [async](async.md) modifier and usually contains one or more await expressions or statements.</span></span> <span data-ttu-id="13a2f-140">await 表达式将 [await](../operators/await.md) 运算符应用于 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="13a2f-140">An await expression applies the [await](../operators/await.md) operator to a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span>

<span data-ttu-id="13a2f-141">当控件到达异步方法中的 `await` 时，将挂起方法中的进度，直到所等待的任务完成。</span><span class="sxs-lookup"><span data-stu-id="13a2f-141">When control reaches an `await` in the async method, progress in the method is suspended until the awaited task completes.</span></span> <span data-ttu-id="13a2f-142">任务完成后，可以在方法中恢复执行。</span><span class="sxs-lookup"><span data-stu-id="13a2f-142">When the task  is complete, execution can resume in the method.</span></span> <span data-ttu-id="13a2f-143">有关详细信息，请参阅[使用 Async 和 Await 的异步编程](../../programming-guide/concepts/async/index.md)。</span><span class="sxs-lookup"><span data-stu-id="13a2f-143">For more information, see [Asynchronous programming with async and await](../../programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="13a2f-144">应用了 `await` 的完成任务可能由于返回此任务的方法中存在未处理的异常而处于错误状态。</span><span class="sxs-lookup"><span data-stu-id="13a2f-144">The completed task to which `await` is applied might be in a faulted state because of an unhandled exception in the method that returns the task.</span></span> <span data-ttu-id="13a2f-145">等待该任务引发异常。</span><span class="sxs-lookup"><span data-stu-id="13a2f-145">Awaiting the task throws an exception.</span></span> <span data-ttu-id="13a2f-146">如果取消了返回任务的异步进程，此任务最后也可能为已取消状态。</span><span class="sxs-lookup"><span data-stu-id="13a2f-146">A task can also end up in a canceled state if the asynchronous process that returns it is canceled.</span></span> <span data-ttu-id="13a2f-147">等待已取消的任务时将引发 `OperationCanceledException`。</span><span class="sxs-lookup"><span data-stu-id="13a2f-147">Awaiting a canceled task throws an `OperationCanceledException`.</span></span>

<span data-ttu-id="13a2f-148">若要捕获异常，请在 `try` 块中等待任务并在关联的 `catch` 块中捕获异常。</span><span class="sxs-lookup"><span data-stu-id="13a2f-148">To catch the exception, await the task in a `try` block, and catch the exception in the associated `catch` block.</span></span> <span data-ttu-id="13a2f-149">有关示例，请参阅[异步方法示例](#async-method-example)部分。</span><span class="sxs-lookup"><span data-stu-id="13a2f-149">For an example, see the [Async method example](#async-method-example) section.</span></span>

<span data-ttu-id="13a2f-150">任务可能处于错误状态，因为等待的异步方法中发生了多个异常。</span><span class="sxs-lookup"><span data-stu-id="13a2f-150">A task can be in a faulted state because multiple exceptions occurred in the awaited async method.</span></span> <span data-ttu-id="13a2f-151">例如，任务可能是对 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> 调用的结果。</span><span class="sxs-lookup"><span data-stu-id="13a2f-151">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="13a2f-152">当等待此类任务时，仅捕捉到其中一个异常，而且你无法预测将会捕获到哪个异常。</span><span class="sxs-lookup"><span data-stu-id="13a2f-152">When you await such a task, only one of the exceptions is caught, and you can't predict which exception will be caught.</span></span> <span data-ttu-id="13a2f-153">有关示例，请参阅 [Task.WhenAll 示例](#taskwhenall-example)部分。</span><span class="sxs-lookup"><span data-stu-id="13a2f-153">For an example, see the [Task.WhenAll example](#taskwhenall-example) section.</span></span>

## <a name="example"></a><span data-ttu-id="13a2f-154">示例</span><span class="sxs-lookup"><span data-stu-id="13a2f-154">Example</span></span>

<span data-ttu-id="13a2f-155">在下面的示例中，`try` 块包含对可能引发异常的 `ProcessString` 方法的调用。</span><span class="sxs-lookup"><span data-stu-id="13a2f-155">In the following example, the `try` block contains a call to the `ProcessString` method that may cause an exception.</span></span> <span data-ttu-id="13a2f-156">`catch` 子句包含只在屏幕上显示一条消息的异常处理程序。</span><span class="sxs-lookup"><span data-stu-id="13a2f-156">The `catch` clause contains the exception handler that just displays a message on the screen.</span></span> <span data-ttu-id="13a2f-157">当从 `ProcessString` 内部调用 `throw` 语句时，系统将查找 `catch` 语句并显示消息 `Exception caught`。</span><span class="sxs-lookup"><span data-stu-id="13a2f-157">When the `throw` statement is called from inside `ProcessString`, the system looks for the `catch` statement and displays the message `Exception caught`.</span></span>

[!code-csharp[csrefKeywordsExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#2)]

## <a name="two-catch-blocks-example"></a><span data-ttu-id="13a2f-158">两个 catch 块示例</span><span class="sxs-lookup"><span data-stu-id="13a2f-158">Two catch blocks example</span></span>

<span data-ttu-id="13a2f-159">在下面的示例中，使用了两个 catch 块，并捕获到最先出现的最具体的异常。</span><span class="sxs-lookup"><span data-stu-id="13a2f-159">In the following example, two catch blocks are used, and the most specific exception, which comes first, is caught.</span></span>

<span data-ttu-id="13a2f-160">若要捕获最不具体的异常，你可以将 `ProcessString` 中的 throw 语句替换为以下语句：`throw new Exception()`。</span><span class="sxs-lookup"><span data-stu-id="13a2f-160">To catch the least specific exception, you can replace the throw statement in `ProcessString` with the following statement: `throw new Exception()`.</span></span>

<span data-ttu-id="13a2f-161">如果将最不具体的 catch 块置于示例中第一个，将显示以下错误消息：`A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`。</span><span class="sxs-lookup"><span data-stu-id="13a2f-161">If you place the least-specific catch block first in the example, the following  error message appears: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.</span></span>

[!code-csharp[csrefKeywordsExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#3)]

## <a name="async-method-example"></a><span data-ttu-id="13a2f-162">异步方法示例</span><span class="sxs-lookup"><span data-stu-id="13a2f-162">Async method example</span></span>

<span data-ttu-id="13a2f-163">下面的示例阐释异步方法的异常处理。</span><span class="sxs-lookup"><span data-stu-id="13a2f-163">The following example illustrates exception handling for async methods.</span></span> <span data-ttu-id="13a2f-164">若要捕获异步任务引发的异常，将 `await` 表达式置于 `try` 块中，并在 `catch` 块中捕获该异常。</span><span class="sxs-lookup"><span data-stu-id="13a2f-164">To catch an exception that an async task throws, place the `await` expression in a `try` block, and catch the exception in a `catch` block.</span></span>

<span data-ttu-id="13a2f-165">在示例中取消注释 `throw new Exception` 行以演示异常处理。</span><span class="sxs-lookup"><span data-stu-id="13a2f-165">Uncomment the `throw new Exception` line in the example to demonstrate exception handling.</span></span> <span data-ttu-id="13a2f-166">任务的 `IsFaulted` 属性设置为 `True`，任务的 `Exception.InnerException` 属性设置为异常，并在 `catch` 块中捕获该异常。</span><span class="sxs-lookup"><span data-stu-id="13a2f-166">The task's `IsFaulted` property is set to `True`, the task's `Exception.InnerException` property is set to the exception, and the exception is caught in the `catch` block.</span></span>

<span data-ttu-id="13a2f-167">取消注释 `throw new OperationCanceledException` 行以演示在取消异步进程时发生的情况。</span><span class="sxs-lookup"><span data-stu-id="13a2f-167">Uncomment the `throw new OperationCanceledException` line to demonstrate what happens when you cancel an asynchronous process.</span></span> <span data-ttu-id="13a2f-168">任务的 `IsCanceled` 属性设置为 `true`，并在 `catch` 块中捕获异常。</span><span class="sxs-lookup"><span data-stu-id="13a2f-168">The task's `IsCanceled` property is set to `true`, and the exception is caught in the `catch` block.</span></span> <span data-ttu-id="13a2f-169">在某些不适用于此示例的情况下，任务的 `IsFaulted` 属性设置为 `true` 且 `IsCanceled` 设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="13a2f-169">Under some conditions that don't apply to this example, the task's `IsFaulted` property is set to `true` and `IsCanceled` is set to `false`.</span></span>

[!code-csharp[csAsyncExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#2)]  

## <a name="taskwhenall-example"></a><span data-ttu-id="13a2f-170">Task.WhenAll 示例</span><span class="sxs-lookup"><span data-stu-id="13a2f-170">Task.WhenAll example</span></span>

<span data-ttu-id="13a2f-171">下面的示例阐释了在多个任务可能导致多个异常的情况中的异常处理。</span><span class="sxs-lookup"><span data-stu-id="13a2f-171">The following example illustrates exception handling where multiple tasks can result in multiple exceptions.</span></span> <span data-ttu-id="13a2f-172">`try` 块等待由 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> 的调用返回的任务。</span><span class="sxs-lookup"><span data-stu-id="13a2f-172">The `try` block awaits the task that's returned by a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="13a2f-173">应用了 WhenAll 的三个任务完成后，该任务完成。</span><span class="sxs-lookup"><span data-stu-id="13a2f-173">The task is complete when the three tasks to which WhenAll is applied are complete.</span></span>

<span data-ttu-id="13a2f-174">三个任务中的每一个都会导致异常。</span><span class="sxs-lookup"><span data-stu-id="13a2f-174">Each of the three tasks causes an exception.</span></span> <span data-ttu-id="13a2f-175">`catch` 块循环访问异常，这些异常位于由 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> 返回的任务的 `Exception.InnerExceptions` 属性中。</span><span class="sxs-lookup"><span data-stu-id="13a2f-175">The `catch` block iterates through the exceptions, which are found in the `Exception.InnerExceptions` property of the task that was returned by <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span>

[!code-csharp[csAsyncExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="13a2f-176">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="13a2f-176">C# language specification</span></span>

<span data-ttu-id="13a2f-177">有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)中的 [try 语句](~/_csharplang/spec/statements.md#the-try-statement)部分。</span><span class="sxs-lookup"><span data-stu-id="13a2f-177">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="13a2f-178">另请参阅</span><span class="sxs-lookup"><span data-stu-id="13a2f-178">See also</span></span>

- [<span data-ttu-id="13a2f-179">C# 参考</span><span class="sxs-lookup"><span data-stu-id="13a2f-179">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="13a2f-180">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="13a2f-180">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="13a2f-181">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="13a2f-181">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="13a2f-182">try、throw 和 catch 语句 (C++)</span><span class="sxs-lookup"><span data-stu-id="13a2f-182">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="13a2f-183">throw</span><span class="sxs-lookup"><span data-stu-id="13a2f-183">throw</span></span>](throw.md)
- [<span data-ttu-id="13a2f-184">try-finally</span><span class="sxs-lookup"><span data-stu-id="13a2f-184">try-finally</span></span>](try-finally.md)
- [<span data-ttu-id="13a2f-185">如何：显式引发异常</span><span class="sxs-lookup"><span data-stu-id="13a2f-185">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)

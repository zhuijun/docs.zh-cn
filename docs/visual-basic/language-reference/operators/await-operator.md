---
title: Await 运算符
ms.date: 07/20/2015
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
ms.openlocfilehash: 9d55ba82547dfcb0336c3a3fd12521c0dcb3eb58
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371825"
---
# <a name="await-operator-visual-basic"></a><span data-ttu-id="13161-102">Await 运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13161-102">Await Operator (Visual Basic)</span></span>

<span data-ttu-id="13161-103">在异步方法或 Lambda 表达式中对操作数应用 `Await` 运算符可暂停执行方法，直到所等待的任务完成。</span><span class="sxs-lookup"><span data-stu-id="13161-103">You apply the `Await` operator to an operand in an asynchronous method or lambda expression to suspend execution of the method until the awaited task completes.</span></span> <span data-ttu-id="13161-104">任务表示正在进行的工作。</span><span class="sxs-lookup"><span data-stu-id="13161-104">The task represents ongoing work.</span></span>

<span data-ttu-id="13161-105">使用的方法 `Await` 必须具有[Async](../modifiers/async.md)修饰符。</span><span class="sxs-lookup"><span data-stu-id="13161-105">The method in which `Await` is used must have an [Async](../modifiers/async.md) modifier.</span></span> <span data-ttu-id="13161-106">此类方法通过使用 `Async` 修饰符定义，通常包含一个或多个表达式， `Await` 称为*异步方法*。</span><span class="sxs-lookup"><span data-stu-id="13161-106">Such a method, defined by using the `Async` modifier, and usually containing one or more `Await` expressions, is referred to as an *async method*.</span></span>

> [!NOTE]
> <span data-ttu-id="13161-107">`Async` 和 `Await` 关键字是在 Visual Studio 2012 中引入的。</span><span class="sxs-lookup"><span data-stu-id="13161-107">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="13161-108">有关异步编程的介绍，请参阅[使用 async 和 Await 进行异步编程](../../programming-guide/concepts/async/index.md)。</span><span class="sxs-lookup"><span data-stu-id="13161-108">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="13161-109">通常，应用操作员的任务 `Await` 是对实现[基于任务的异步模式](https://www.microsoft.com/download/details.aspx?id=19957)的方法（即或）的调用的返回值 <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> 。</span><span class="sxs-lookup"><span data-stu-id="13161-109">Typically, the task to which you apply the `Await` operator is the return value from a call to a method that implements the [Task-Based Asynchronous Pattern](https://www.microsoft.com/download/details.aspx?id=19957), that is, a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601>.</span></span>

<span data-ttu-id="13161-110">在以下代码中，<xref:System.Net.Http.HttpClient> 方法 <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> 返回 `getContentsTask`，一个 `Task(Of Byte())`。</span><span class="sxs-lookup"><span data-stu-id="13161-110">In the following code, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> returns `getContentsTask`, a `Task(Of Byte())`.</span></span> <span data-ttu-id="13161-111">当操作完成时，任务约定生成一个实际字节数组。</span><span class="sxs-lookup"><span data-stu-id="13161-111">The task is a promise to produce the actual byte array when the operation is complete.</span></span> <span data-ttu-id="13161-112">`Await` 运算符应用于 `getContentsTask` 以在 `SumPageSizesAsync` 中挂起执行，直到 `getContentsTask` 完成。</span><span class="sxs-lookup"><span data-stu-id="13161-112">The `Await` operator is applied to `getContentsTask` to suspend execution in `SumPageSizesAsync` until `getContentsTask` is complete.</span></span> <span data-ttu-id="13161-113">同时，控制权会返回给 `SumPageSizesAsync` 的调用方。</span><span class="sxs-lookup"><span data-stu-id="13161-113">In the meantime, control is returned to the caller of `SumPageSizesAsync`.</span></span> <span data-ttu-id="13161-114">当 `getContentsTask` 完成之后，`Await` 表达式计算为字节数组。</span><span class="sxs-lookup"><span data-stu-id="13161-114">When `getContentsTask` is finished, the `Await` expression evaluates to a byte array.</span></span>

```vb
Private Async Function SumPageSizesAsync() As Task

    ' To use the HttpClient type in desktop apps, you must include a using directive and add a
    ' reference for the System.Net.Http namespace.
    Dim client As HttpClient = New HttpClient()
    ' . . .
    Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
    Dim urlContents As Byte() = Await getContentsTask

    ' Equivalently, now that you see how it works, you can write the same thing in a single line.
    'Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
    ' . . .
End Function
```

> [!IMPORTANT]
> <span data-ttu-id="13161-115">有关完整示例，请参阅[演练：使用 async 和 await 访问 Web](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。</span><span class="sxs-lookup"><span data-stu-id="13161-115">For the complete example, see [Walkthrough: Accessing the Web by Using Async and Await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="13161-116">可以从 Microsoft 网站的[开发者代码示例](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)中下载示例。</span><span class="sxs-lookup"><span data-stu-id="13161-116">You can download the sample from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) on the Microsoft website.</span></span> <span data-ttu-id="13161-117">该示例处于 AsyncWalkthrough_HttpClient 项目中。</span><span class="sxs-lookup"><span data-stu-id="13161-117">The example is in the AsyncWalkthrough_HttpClient project.</span></span>

<span data-ttu-id="13161-118">如果 `Await` 应用于返回 `Task(Of TResult)` 的方法调用结果，则 `Await` 表达式的类型为 TResult。</span><span class="sxs-lookup"><span data-stu-id="13161-118">If `Await` is applied to the result of a method call that returns a `Task(Of TResult)`, the type of the `Await` expression is TResult.</span></span> <span data-ttu-id="13161-119">如果 `Await` 应用于返回 `Task` 的方法调用结果，则 `Await` 表达式不返回值。</span><span class="sxs-lookup"><span data-stu-id="13161-119">If `Await` is applied to the result of a method call that returns a `Task`, the `Await` expression doesn't return a value.</span></span> <span data-ttu-id="13161-120">以下示例演示了差异。</span><span class="sxs-lookup"><span data-stu-id="13161-120">The following example illustrates the difference.</span></span>

```vb
' Await used with a method that returns a Task(Of TResult).
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()

' Await used with a method that returns a Task.
Await AsyncMethodThatReturnsTask()
```

<span data-ttu-id="13161-121">`Await` 表达式或声明不阻止正在执行它的线程。</span><span class="sxs-lookup"><span data-stu-id="13161-121">An `Await` expression or statement does not block the thread on which it is executing.</span></span> <span data-ttu-id="13161-122">而是导致编译器在 `Await` 表达式之后，将剩下的异步方法注册为等待任务的后续部分。</span><span class="sxs-lookup"><span data-stu-id="13161-122">Instead, it causes the compiler to sign up the rest of the async method, after the `Await` expression, as a continuation on the awaited task.</span></span> <span data-ttu-id="13161-123">控制权随后会返回给异步方法的调用方。</span><span class="sxs-lookup"><span data-stu-id="13161-123">Control then returns to the caller of the async method.</span></span> <span data-ttu-id="13161-124">任务完成时，它会调用其延续任务，异步方法的执行会在暂停的位置处恢复。</span><span class="sxs-lookup"><span data-stu-id="13161-124">When the task completes, it invokes its continuation, and execution of the async method resumes where it left off.</span></span>

<span data-ttu-id="13161-125">`Await` 表达式只出现在由 `Async` 修饰符标记的一个立即封闭方法体或 lambda 表达式中。</span><span class="sxs-lookup"><span data-stu-id="13161-125">An `Await` expression can occur only in the body of an immediately enclosing method or lambda expression that is marked by an `Async` modifier.</span></span> <span data-ttu-id="13161-126">术语 " *Await* " 在该上下文中仅用作关键字。</span><span class="sxs-lookup"><span data-stu-id="13161-126">The term *Await* serves as a keyword only in that context.</span></span> <span data-ttu-id="13161-127">在其他位置，它会解释为标识符。</span><span class="sxs-lookup"><span data-stu-id="13161-127">Elsewhere, it is interpreted as an identifier.</span></span> <span data-ttu-id="13161-128">在 `Async` 方法或 lambda 表达式中， `Await` 表达式不能出现在查询表达式中，在 `Catch` `Finally` [Try .。。Catch .。。Finally 语句](../statements/try-catch-finally-statement.md)，在或循环的循环控制变量表达式 `For` 中 `For Each` ，或在[SyncLock](../statements/synclock-statement.md)语句的正文中。</span><span class="sxs-lookup"><span data-stu-id="13161-128">Within the `Async` method or lambda expression, an `Await` expression cannot occur in a query expression, in the `Catch` or `Finally` block of a [Try…Catch…Finally statement](../statements/try-catch-finally-statement.md), in the loop control variable expression of a `For` or `For Each` loop, or in the body of a [SyncLock](../statements/synclock-statement.md) statement.</span></span>

## <a name="exceptions"></a><span data-ttu-id="13161-129">例外</span><span class="sxs-lookup"><span data-stu-id="13161-129">Exceptions</span></span>

<span data-ttu-id="13161-130">大多数异步方法返回 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="13161-130">Most async methods return a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="13161-131">返回任务的属性携带有关其状态和历史记录的信息，如任务是否完成、异步方法是否导致异常或已取消以及最终结果是什么。</span><span class="sxs-lookup"><span data-stu-id="13161-131">The properties of the returned task carry information about its status and history, such as whether the task is complete, whether the async method caused an exception or was canceled, and what the final result is.</span></span> <span data-ttu-id="13161-132">`Await` 运算符可访问这些属性。</span><span class="sxs-lookup"><span data-stu-id="13161-132">The `Await` operator accesses those properties.</span></span>

<span data-ttu-id="13161-133">如果等待的任务返回异步方法导致异常，则 `Await` 运算符会重新引发异常。</span><span class="sxs-lookup"><span data-stu-id="13161-133">If you await a task-returning async method that causes an exception, the  `Await` operator rethrows the exception.</span></span>

<span data-ttu-id="13161-134">如果等待的返回任务的异步方法取消，`Await` 运算符将重新引发 <xref:System.OperationCanceledException>。</span><span class="sxs-lookup"><span data-stu-id="13161-134">If you await a task-returning async method that is canceled, the `Await` operator rethrows an <xref:System.OperationCanceledException>.</span></span>

<span data-ttu-id="13161-135">处于故障状态的单个任务可以反映多个异常。</span><span class="sxs-lookup"><span data-stu-id="13161-135">A single task that is in a faulted state can reflect multiple exceptions.</span></span>  <span data-ttu-id="13161-136">例如，任务可能是对 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> 调用的结果。</span><span class="sxs-lookup"><span data-stu-id="13161-136">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="13161-137">等待此类任务时，等待操作仅重新引发异常之一。</span><span class="sxs-lookup"><span data-stu-id="13161-137">When you await such a task, the await operation rethrows only one of the exceptions.</span></span> <span data-ttu-id="13161-138">但是，无法预测重新引发的异常。</span><span class="sxs-lookup"><span data-stu-id="13161-138">However, you can't predict which of the exceptions is rethrown.</span></span>

<span data-ttu-id="13161-139">有关异步方法中的错误处理的示例，请参阅[Try .。。Catch .。。Finally 语句](../statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="13161-139">For examples of error handling in async methods, see [Try...Catch...Finally Statement](../statements/try-catch-finally-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="13161-140">示例</span><span class="sxs-lookup"><span data-stu-id="13161-140">Example</span></span>

<span data-ttu-id="13161-141">下面的 Windows 窗体示例阐释如何在异步方法 `WaitAsynchronouslyAsync` 中使用 `Await`。</span><span class="sxs-lookup"><span data-stu-id="13161-141">The following Windows Forms example illustrates the use of `Await` in an async method, `WaitAsynchronouslyAsync`.</span></span> <span data-ttu-id="13161-142">将该方法的行为与 `WaitSynchronously` 的行为进行对比。</span><span class="sxs-lookup"><span data-stu-id="13161-142">Contrast the behavior of that method with the behavior of `WaitSynchronously`.</span></span> <span data-ttu-id="13161-143">如果没有应用 `Await` 运算符，`WaitSynchronously` 就会同步运行，而不管其定义中是否使用了 `Async` 修饰符和在主体中是否调用了 <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="13161-143">Without an `Await` operator, `WaitSynchronously` runs synchronously despite the use of the `Async` modifier in its definition and a call to <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> in its body.</span></span>

```vb
Private Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
    ' Call the method that runs asynchronously.
    Dim result As String = Await WaitAsynchronouslyAsync()

    ' Call the method that runs synchronously.
    'Dim result As String = Await WaitSynchronously()

    ' Display the result.
    TextBox1.Text &= result
End Sub

' The following method runs asynchronously. The UI thread is not
' blocked during the delay. You can move or resize the Form1 window
' while Task.Delay is running.
Public Async Function WaitAsynchronouslyAsync() As Task(Of String)
    Await Task.Delay(10000)
    Return "Finished"
End Function

' The following method runs synchronously, despite the use of Async.
' You cannot move or resize the Form1 window while Thread.Sleep
' is running because the UI thread is blocked.
Public Async Function WaitSynchronously() As Task(Of String)
    ' Import System.Threading for the Sleep method.
    Thread.Sleep(10000)
    Return "Finished"
End Function
```

## <a name="see-also"></a><span data-ttu-id="13161-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="13161-144">See also</span></span>

- [<span data-ttu-id="13161-145">采用 Async 和 Await 的异步编程</span><span class="sxs-lookup"><span data-stu-id="13161-145">Asynchronous Programming with Async and Await</span></span>](../../programming-guide/concepts/async/index.md)
- [<span data-ttu-id="13161-146">演练：使用 Async 和 Await 访问 Web</span><span class="sxs-lookup"><span data-stu-id="13161-146">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="13161-147">异步</span><span class="sxs-lookup"><span data-stu-id="13161-147">Async</span></span>](../modifiers/async.md)

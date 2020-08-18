---
title: async - C# 参考
ms.date: 05/22/2017
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
ms.openlocfilehash: 279ea2f9875681401c9c7acab922d9e4424e6827
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062530"
---
# <a name="async-c-reference"></a><span data-ttu-id="f9cf4-102">async（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="f9cf4-102">async (C# Reference)</span></span>

<span data-ttu-id="f9cf4-103">使用 `async` 修饰符可将方法、[lambda 表达式](../operators/lambda-expressions.md)或[匿名方法](../operators/delegate-operator.md)指定为异步。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-103">Use the `async` modifier to specify that a method, [lambda expression](../operators/lambda-expressions.md), or [anonymous method](../operators/delegate-operator.md) is asynchronous.</span></span> <span data-ttu-id="f9cf4-104">如果对方法或表达式使用此修饰符，则其称为异步方法  。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-104">If you use this modifier on a method or expression, it's referred to as an *async method*.</span></span> <span data-ttu-id="f9cf4-105">如下示例定义了一个名为 `ExampleMethodAsync` 的异步方法：</span><span class="sxs-lookup"><span data-stu-id="f9cf4-105">The following example defines an async method named `ExampleMethodAsync`:</span></span>
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  

<span data-ttu-id="f9cf4-106">如果不熟悉异步编程，或者不了解异步方法如何在不阻止调用方线程的情况下使用 [`await` 运算符](../operators/await.md)完成可能需要长时间运行的工作，请阅读[使用 async 和 await 的异步编程](../../programming-guide/concepts/async/index.md)中的说明。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-106">If you're new to asynchronous programming or do not understand how an async method uses the [`await` operator](../operators/await.md) to do potentially long-running work without blocking the caller's thread, read the introduction in [Asynchronous Programming with async and await](../../programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="f9cf4-107">如下代码见于一种异步方法中，且调用 <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> 方法：</span><span class="sxs-lookup"><span data-stu-id="f9cf4-107">The following code is found inside an async method and calls the <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> method:</span></span>
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
<span data-ttu-id="f9cf4-108">异步方法同步运行，直至到达其第一个 `await` 表达式，此时会将方法挂起，直到等待的任务完成。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-108">An async method runs synchronously until it reaches its first `await` expression, at which point the method is suspended until the awaited task is complete.</span></span> <span data-ttu-id="f9cf4-109">同时，如下节示例中所示，控件将返回到方法的调用方。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-109">In the meantime, control returns to the caller of the method, as the example in the next section shows.</span></span>  
  
<span data-ttu-id="f9cf4-110">如果 `async` 关键字修改的方法不包含 `await` 表达式或语句，则该方法将同步执行。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-110">If the method that the `async` keyword modifies doesn't contain an `await` expression or statement, the method executes synchronously.</span></span> <span data-ttu-id="f9cf4-111">编译器警告将通知你不包含 `await` 语句的任何异步方法，因为该情况可能表示存在错误。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-111">A compiler warning alerts you to any async methods that don't contain `await` statements, because that situation might indicate an error.</span></span> <span data-ttu-id="f9cf4-112">请参阅[编译器警告（等级 1）CS4014](../compiler-messages/cs4014.md)。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-112">See [Compiler Warning (level 1) CS4014](../compiler-messages/cs4014.md).</span></span>  
  
 <span data-ttu-id="f9cf4-113">`async` 关键字是上下文关键字，原因在于只有当它修饰方法、lambda 表达式或匿名方法时，它才是关键字。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-113">The `async` keyword is contextual in that it's a keyword only when it modifies a method, a lambda expression, or an anonymous method.</span></span> <span data-ttu-id="f9cf4-114">在所有其他上下文中，都会将其解释为标识符。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-114">In all other contexts, it's interpreted as an identifier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9cf4-115">示例</span><span class="sxs-lookup"><span data-stu-id="f9cf4-115">Example</span></span>  
<span data-ttu-id="f9cf4-116">下面的示例展示了异步事件处理程序 `StartButton_Click` 和异步方法 `ExampleMethodAsync` 之间的控制结构和流程。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-116">The following example shows the structure and flow of control between an async event handler, `StartButton_Click`, and an async method, `ExampleMethodAsync`.</span></span> <span data-ttu-id="f9cf4-117">此异步方法的结果是 Web 页面的字符数。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-117">The result from the async method is the number of characters of a web page.</span></span> <span data-ttu-id="f9cf4-118">此代码适用于在 Visual Studio 中创建的 Windows Presentation Foundation (WPF) 应用或 Windows 应用商店应用；请参见有关设置应用的代码注释。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-118">The code is suitable for a Windows Presentation Foundation (WPF) app or Windows Store app that you create in Visual Studio; see the code comments for setting up the app.</span></span>  

<span data-ttu-id="f9cf4-119">可以在 Visual Studio 中将此代码作为 Windows Presentation Foundation (WPF) 应用或 Windows 应用商店应用运行。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-119">You can run this code in Visual Studio as a Windows Presentation Foundation (WPF) app or a Windows Store app.</span></span> <span data-ttu-id="f9cf4-120">需要一个名为 `StartButton` 的按钮控件和一个名为 `ResultsTextBox` 的文本框控件。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-120">You need a Button control named `StartButton` and a Textbox control named `ResultsTextBox`.</span></span> <span data-ttu-id="f9cf4-121">切勿忘记设置名称和处理程序，以便获得类似于以下代码的内容：</span><span class="sxs-lookup"><span data-stu-id="f9cf4-121">Remember to set the names and handler so that you have something like this:</span></span>  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
<span data-ttu-id="f9cf4-122">将代码作为 WPF 应用运行：</span><span class="sxs-lookup"><span data-stu-id="f9cf4-122">To run the code as a WPF app:</span></span>  

- <span data-ttu-id="f9cf4-123">将此代码粘贴到 MainWindow.xaml.cs 中的 `MainWindow` 类中。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-123">Paste this code into the `MainWindow` class in MainWindow.xaml.cs.</span></span>  
- <span data-ttu-id="f9cf4-124">添加对 System.Net.Http 的引用。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-124">Add a reference to System.Net.Http.</span></span>  
- <span data-ttu-id="f9cf4-125">为 System.Net.Http 添加一个 `using` 指令。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-125">Add a `using` directive for System.Net.Http.</span></span>  
  
<span data-ttu-id="f9cf4-126">将此代码作为 Windows 应用商店应用运行：</span><span class="sxs-lookup"><span data-stu-id="f9cf4-126">To run the code as a Windows Store app:</span></span>  

- <span data-ttu-id="f9cf4-127">将此代码粘贴到 MainPage.xaml.cs 中的 `MainPage` 类中。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-127">Paste this code into the `MainPage` class in MainPage.xaml.cs.</span></span>  
- <span data-ttu-id="f9cf4-128">为 System.Net.Http 和 System.Threading.Tasks 添加 using 指令。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-128">Add using directives for System.Net.Http and System.Threading.Tasks.</span></span>  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
> <span data-ttu-id="f9cf4-129">若要深入了解各项任务以及在等待任务期间所执行的代码，请参阅[使用 async 和 await 的异步编程](../../programming-guide/concepts/async/index.md)。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-129">For more information about tasks and the code that executes while waiting for a task, see [Asynchronous Programming with async and await](../../programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="f9cf4-130">有关使用类似元素的完整 WPF 示例，请参阅[演练：使用 Async 和 Await 访问 Web](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-130">For a full WPF example that uses similar elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
## <a name="return-types"></a><span data-ttu-id="f9cf4-131">返回类型</span><span class="sxs-lookup"><span data-stu-id="f9cf4-131">Return Types</span></span>  
<span data-ttu-id="f9cf4-132">异步方法可具有以下返回类型：</span><span class="sxs-lookup"><span data-stu-id="f9cf4-132">An async method can have the following return types:</span></span>

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- <span data-ttu-id="f9cf4-133">[void](../builtin-types/void.md)。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-133">[void](../builtin-types/void.md).</span></span> <span data-ttu-id="f9cf4-134">对于除事件处理程序以外的代码，通常不鼓励使用 `async void` 方法，因为调用方不能 `await` 那些方法，并且必须实现不同的机制来报告成功完成或错误条件。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-134">`async void` methods are generally discouraged for code other than event handlers because callers cannot `await` those methods and must implement a different mechanism to report successful completion or error conditions.</span></span>
- <span data-ttu-id="f9cf4-135">从 C# 7.0 开始，任何具有可访问的 `GetAwaiter` 方法的类型。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-135">Starting with C# 7.0, any type that has an accessible `GetAwaiter` method.</span></span> <span data-ttu-id="f9cf4-136">`System.Threading.Tasks.ValueTask<TResult>` 类型属于此类实现。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-136">The `System.Threading.Tasks.ValueTask<TResult>` type is one such implementation.</span></span> <span data-ttu-id="f9cf4-137">它通过添加 NuGet 包 `System.Threading.Tasks.Extensions` 的方式可用。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-137">It is available by adding the NuGet package `System.Threading.Tasks.Extensions`.</span></span>

<span data-ttu-id="f9cf4-138">此异步方法既不能声明任何 [in](./in-parameter-modifier.md)、[ref](./ref.md) 或 [out](./out-parameter-modifier.md) 参数，也不能具有[引用返回值](../../programming-guide/classes-and-structs/ref-returns.md)，但它可以调用具有此类参数的方法。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-138">The async method can't declare any [in](./in-parameter-modifier.md), [ref](./ref.md) or [out](./out-parameter-modifier.md) parameters, nor can it have a [reference return value](../../programming-guide/classes-and-structs/ref-returns.md), but it can call methods that have such parameters.</span></span>  
  
<span data-ttu-id="f9cf4-139">如果异步方法的 语句指定一个 类型的操作数，则应指定 `Task<TResult>` 作为方法的[返回](./return.md)类型`TResult`。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-139">You specify `Task<TResult>` as the return type of an async method if the [return](./return.md) statement of the method specifies an operand of type `TResult`.</span></span> <span data-ttu-id="f9cf4-140">如果当方法完成时未返回有意义的值，则应使用 `Task`。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-140">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="f9cf4-141">即，对方法的调用将返回一个 `Task`，但是当 `Task` 完成时，任何等待 `await` 的所有 `Task` 表达式的计算结果都为 `void`。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-141">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `await` expression that's awaiting the `Task` evaluates to `void`.</span></span>  
  
<span data-ttu-id="f9cf4-142">你应主要使用 `void` 返回类型来定义事件处理程序，这些处理程序需要此返回类型。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-142">You use the `void` return type primarily to define event handlers, which require that return type.</span></span> <span data-ttu-id="f9cf4-143">`void` 返回异步方法的调用方不能等待，并且无法捕获该方法引发的异常。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-143">The caller of a `void`-returning async method can't await it and can't catch exceptions that the method throws.</span></span>  

<span data-ttu-id="f9cf4-144">从 C# 7.0 开始，返回另一个类型（通常为值类型），该类型具有 `GetAwaiter` 方法，可尽可能减少性能关键代码段中的内存分配。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-144">Starting with C# 7.0, you return another type, typically a value type, that has a `GetAwaiter` method to minimize memory allocations in performance-critical sections of code.</span></span>

<span data-ttu-id="f9cf4-145">有关详细信息和示例，请参阅[异步返回类型](../../programming-guide/concepts/async/async-return-types.md)。</span><span class="sxs-lookup"><span data-stu-id="f9cf4-145">For more information and examples, see [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9cf4-146">请参阅</span><span class="sxs-lookup"><span data-stu-id="f9cf4-146">See also</span></span>

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [<span data-ttu-id="f9cf4-147">await</span><span class="sxs-lookup"><span data-stu-id="f9cf4-147">await</span></span>](../operators/await.md)
- [<span data-ttu-id="f9cf4-148">演练：使用 Async 和 Await 访问 Web</span><span class="sxs-lookup"><span data-stu-id="f9cf4-148">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="f9cf4-149">使用 async 和 await 的异步编程</span><span class="sxs-lookup"><span data-stu-id="f9cf4-149">Asynchronous Programming with async and await</span></span>](../../programming-guide/concepts/async/index.md)

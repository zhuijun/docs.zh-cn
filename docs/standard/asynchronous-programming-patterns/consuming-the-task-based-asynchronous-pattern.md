---
title: 使用基于任务的异步模式
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: 033cf871-ae24-433d-8939-7a3793e547bf
ms.openlocfilehash: 64a9b963ce6a8554a581f9d5d0f77cf4edfa71b4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289455"
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a><span data-ttu-id="e6cdd-102">使用基于任务的异步模式</span><span class="sxs-lookup"><span data-stu-id="e6cdd-102">Consuming the Task-based Asynchronous Pattern</span></span>

<span data-ttu-id="e6cdd-103">使用基于任务的异步模式 (TAP) 处理异步操作时，可以使用回叫实现等待，而不会阻塞。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-103">When you use the Task-based Asynchronous Pattern (TAP) to work with asynchronous operations, you can use callbacks to achieve waiting without blocking.</span></span>  <span data-ttu-id="e6cdd-104">对于任务，这可通过 <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> 等方法实现。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-104">For tasks, this is achieved through methods such as <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e6cdd-105">通过允许在正常控制流中等待异步操纵，基于语言的异步支持可隐藏回叫，并且编译器生成的代码可提供此相同 API 级别的支持。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-105">Language-based asynchronous support hides callbacks by allowing asynchronous operations to be awaited within normal control flow, and compiler-generated code provides this same API-level support.</span></span>

## <a name="suspending-execution-with-await"></a><span data-ttu-id="e6cdd-106">使用 Await 挂起执行</span><span class="sxs-lookup"><span data-stu-id="e6cdd-106">Suspending Execution with Await</span></span>
 <span data-ttu-id="e6cdd-107">自 .NET Framework 4.5 起，可以使用 C# 中的 [await](../../csharp/language-reference/operators/await.md) 关键字和 Visual Basic 中的 [Await 运算符](../../visual-basic/language-reference/operators/await-operator.md)，异步等待 <xref:System.Threading.Tasks.Task> 和 <xref:System.Threading.Tasks.Task%601> 对象。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-107">Starting with the .NET Framework 4.5, you can use the [await](../../csharp/language-reference/operators/await.md) keyword in C# and the [Await Operator](../../visual-basic/language-reference/operators/await-operator.md) in Visual Basic to asynchronously await <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> objects.</span></span> <span data-ttu-id="e6cdd-108">等待 <xref:System.Threading.Tasks.Task> 时，`await` 表达式的类型为 `void`。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-108">When you're awaiting a <xref:System.Threading.Tasks.Task>, the `await` expression is of type `void`.</span></span> <span data-ttu-id="e6cdd-109">等待 <xref:System.Threading.Tasks.Task%601> 时，`await` 表达式的类型为 `TResult`。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-109">When you're awaiting a <xref:System.Threading.Tasks.Task%601>, the `await` expression is of type `TResult`.</span></span> <span data-ttu-id="e6cdd-110">`await` 表达式必须出现在异步方法的正文内。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-110">An `await` expression must occur inside the body of an asynchronous method.</span></span> <span data-ttu-id="e6cdd-111">若要详细了解 .NET Framework 4.5 中的 C# 和 Visual Basic 语言支持，请参阅 C# 和 Visual Basic 语言规范。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-111">For more information about C# and Visual Basic language support in the .NET Framework 4.5, see the C# and Visual Basic language specifications.</span></span>

 <span data-ttu-id="e6cdd-112">实际上，await 功能通过使用延续任务在任务上安装回叫。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-112">Under the covers, the await functionality installs a callback on the task by using a continuation.</span></span>  <span data-ttu-id="e6cdd-113">此回叫在挂起点恢复异步方法。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-113">This callback resumes the asynchronous method at the point of suspension.</span></span> <span data-ttu-id="e6cdd-114">恢复异步方法时，如果等待的操作已成功完成且为 <xref:System.Threading.Tasks.Task%601>，返回的是 `TResult`。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-114">When the asynchronous method is resumed, if the awaited operation completed successfully and was a <xref:System.Threading.Tasks.Task%601>, its `TResult` is returned.</span></span>  <span data-ttu-id="e6cdd-115">如果等待的 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 以 <xref:System.Threading.Tasks.TaskStatus.Canceled> 状态结束，就会抛出 <xref:System.OperationCanceledException> 异常。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-115">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state, an <xref:System.OperationCanceledException> exception is thrown.</span></span>  <span data-ttu-id="e6cdd-116">如果等待的 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 以 <xref:System.Threading.Tasks.TaskStatus.Faulted> 状态结束，就会抛出导致它发生故障的异常。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-116">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state, the exception that caused it to fault is thrown.</span></span> <span data-ttu-id="e6cdd-117">一个 `Task` 可能由于多个异常而出错，但只会传播一个异常。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-117">A `Task` can fault as a result of multiple exceptions, but only one of these exceptions is propagated.</span></span> <span data-ttu-id="e6cdd-118">不过，<xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> 属性会返回包含所有错误的 <xref:System.AggregateException> 异常。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-118">However, the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property returns an <xref:System.AggregateException> exception that contains all the errors.</span></span>

 <span data-ttu-id="e6cdd-119">如果同步上下文（<xref:System.Threading.SynchronizationContext> 对象）与暂停时正在执行异步方法的线程（例如，如果 <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> 属性不是 `null`）相关联，异步方法使用上下文的 <xref:System.Threading.SynchronizationContext.Post%2A> 方法，恢复相同的同步上下文。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-119">If a synchronization context (<xref:System.Threading.SynchronizationContext> object) is associated with the thread that was executing the asynchronous method at the time of suspension (for example, if the <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> property is not `null`), the asynchronous method resumes on that same synchronization context by using the context’s <xref:System.Threading.SynchronizationContext.Post%2A> method.</span></span> <span data-ttu-id="e6cdd-120">否则，它依赖暂停时的当前任务计划程序（<xref:System.Threading.Tasks.TaskScheduler> 对象）。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-120">Otherwise, it relies on the task scheduler (<xref:System.Threading.Tasks.TaskScheduler> object) that was current at the time of suspension.</span></span> <span data-ttu-id="e6cdd-121">通常情况下，这是定目标到线程池的默认任务计划程序 (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>)。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-121">Typically, this is the default task scheduler (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), which targets the thread pool.</span></span> <span data-ttu-id="e6cdd-122">此任务计划程序确定等待的异步操作是否应在该操作完成时恢复，或是否应计划该恢复。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-122">This task scheduler determines whether the awaited asynchronous operation should resume where it completed or whether the resumption should be scheduled.</span></span> <span data-ttu-id="e6cdd-123">默认计划程序通常允许在完成等待操作的线程上延续任务。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-123">The default scheduler typically allows the continuation to run on the thread that the awaited operation completed.</span></span>

 <span data-ttu-id="e6cdd-124">调用异步方法时，将同步执行函数的正文，直到遇见尚未完成的可等待实例上的第一个 await 表达式，此时调用返回到调用方。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-124">When an asynchronous method is called, it synchronously executes the body of the function up until the first await expression on an awaitable instance that has not yet completed, at which point the invocation returns to the caller.</span></span> <span data-ttu-id="e6cdd-125">如果异步方法不返回 `void`，将会返回 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 对象，以表示正在进行的计算。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-125">If the asynchronous method does not return `void`, a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object is returned to represent the ongoing computation.</span></span> <span data-ttu-id="e6cdd-126">在非 void 异步方法中，如果遇到 return 语句或到达方法正文末尾，任务就以 <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> 最终状态完成。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-126">In a non-void asynchronous method, if a return statement is encountered or the end of the method body is reached, the task is completed in the <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> final state.</span></span> <span data-ttu-id="e6cdd-127">如果未经处理的异常导致无法控制异步方法正文，任务就以 <xref:System.Threading.Tasks.TaskStatus.Faulted> 状态结束。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-127">If an unhandled exception causes control to leave the body of the asynchronous method, the task ends in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state.</span></span> <span data-ttu-id="e6cdd-128">如果异常为 <xref:System.OperationCanceledException>，任务改为以 <xref:System.Threading.Tasks.TaskStatus.Canceled> 状态结束。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-128">If that exception is an <xref:System.OperationCanceledException>, the task instead ends in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state.</span></span> <span data-ttu-id="e6cdd-129">通过此方式，最终将发布结果或异常。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-129">In this manner, the result or exception is eventually published.</span></span>

 <span data-ttu-id="e6cdd-130">此行为有几种重要特殊情况。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-130">There are several important variations of this behavior.</span></span>  <span data-ttu-id="e6cdd-131">出于性能原因，如果任务在等待时已完成，则不会生成控件，并且该函数将继续执行。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-131">For performance reasons, if a task has already completed by the time the task is awaited, control is not yielded, and the function continues to execute.</span></span>  <span data-ttu-id="e6cdd-132">返回到原始上下文并不总是所需的行为，可对其进行更改；将在下一节中更详细地描述此内容。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-132">Additionally, returning to the original context isn't always the desired behavior and can be changed; this is described in more detail in the next section.</span></span>

### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a><span data-ttu-id="e6cdd-133">使用 Yield 和 ConfigureAwait 配置挂起和恢复</span><span class="sxs-lookup"><span data-stu-id="e6cdd-133">Configuring Suspension and Resumption with Yield and ConfigureAwait</span></span>
 <span data-ttu-id="e6cdd-134">有多种方法可更好地控制异步方法的执行。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-134">Several methods provide more control over an asynchronous method’s execution.</span></span> <span data-ttu-id="e6cdd-135">例如，可以使用 <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> 方法，将暂停点引入异步方法：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-135">For example, you can use the <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> method to introduce a yield point into the asynchronous method:</span></span>

```csharp
public class Task : …
{
    public static YieldAwaitable Yield();
    …
}
```

 <span data-ttu-id="e6cdd-136">这相当于以异步方式发布或计划返回当前上下文。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-136">This is equivalent to asynchronously posting or scheduling back to the current context.</span></span>

```csharp
Task.Run(async delegate
{
    for(int i=0; i<1000000; i++)
    {
        await Task.Yield(); // fork the continuation into a separate work item
        ...
    }
});
```

 <span data-ttu-id="e6cdd-137">还可以使用 <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> 方法，更好地控制异步方法中的暂停和恢复。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-137">You can also use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method for better control over suspension and resumption in an asynchronous method.</span></span>  <span data-ttu-id="e6cdd-138">如前所述，默认情况下，异步方法挂起时会捕获当前上下文，捕获的上下文用于在恢复时调用异步方法的延续。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-138">As mentioned previously, by default, the current context is captured at the time an asynchronous  method is suspended, and that captured context is used to invoke the asynchronous  method’s continuation upon resumption.</span></span>  <span data-ttu-id="e6cdd-139">在多数情况下，这就是你所需的确切行为。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-139">In many cases, this is the exact behavior you want.</span></span>  <span data-ttu-id="e6cdd-140">在其他情况下，你可能不关心延续上下文，则可以通过避免此类发布返回原始上下文来获得更好的性能。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-140">In other cases, you may not care about the continuation context, and you can achieve better performance by avoiding such posts back to the original context.</span></span>  <span data-ttu-id="e6cdd-141">若要启用此功能，请使用 <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> 方法，指示等待操作不要捕获和恢复上下文，而是继续执行正在等待完成的所有异步操作：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-141">To enable this, use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method to inform the await operation not to capture and resume on the context, but to continue execution wherever the asynchronous operation that was being awaited completed:</span></span>

```csharp
await someTask.ConfigureAwait(continueOnCapturedContext:false);
```

## <a name="canceling-an-asynchronous-operation"></a><span data-ttu-id="e6cdd-142">取消异步操作</span><span class="sxs-lookup"><span data-stu-id="e6cdd-142">Canceling an Asynchronous Operation</span></span>
 <span data-ttu-id="e6cdd-143">从 .NET Framework 4 开始，支持取消操作的 TAP 方法提供至少一个接受取消令牌（<xref:System.Threading.CancellationToken> 对象）的重载。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-143">Starting with the .NET Framework 4, TAP methods that support cancellation provide at least one overload that accepts a cancellation token (<xref:System.Threading.CancellationToken> object).</span></span>

 <span data-ttu-id="e6cdd-144">可通过取消令牌源（<xref:System.Threading.CancellationTokenSource> 对象）创建取消令牌。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-144">A cancellation token is created through a cancellation token source (<xref:System.Threading.CancellationTokenSource> object).</span></span>  <span data-ttu-id="e6cdd-145">源的 <xref:System.Threading.CancellationTokenSource.Token%2A> 属性返回取消令牌，它在源的 <xref:System.Threading.CancellationTokenSource.Cancel%2A> 方法获得调用收到信号。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-145">The source’s <xref:System.Threading.CancellationTokenSource.Token%2A> property returns the cancellation token that will be signaled when the source’s <xref:System.Threading.CancellationTokenSource.Cancel%2A> method is called.</span></span>  <span data-ttu-id="e6cdd-146">例如，若要下载一个网页，并且希望能够取消此操作，请创建 <xref:System.Threading.CancellationTokenSource> 对象，将它的令牌传递给 TAP 方法，再在准备好取消此操作时，调用源的 <xref:System.Threading.CancellationTokenSource.Cancel%2A> 方法：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-146">For example, if you want to download a single webpage and you want to be able to cancel the operation, you create a <xref:System.Threading.CancellationTokenSource> object, pass its token to the TAP method, and then call the source’s <xref:System.Threading.CancellationTokenSource.Cancel%2A> method when you're ready to cancel the operation:</span></span>

```csharp
var cts = new CancellationTokenSource();
string result = await DownloadStringAsync(url, cts.Token);
… // at some point later, potentially on another thread
cts.Cancel();
```

 <span data-ttu-id="e6cdd-147">若要取消多个异步调用，可以将相同令牌传递给所有调用：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-147">To cancel multiple asynchronous invocations, you can pass the same token to all invocations:</span></span>

```csharp
var cts = new CancellationTokenSource();
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));
    // at some point later, potentially on another thread
    …
    cts.Cancel();
```

 <span data-ttu-id="e6cdd-148">或者，将相同令牌传递给操作的选择性子集：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-148">Or, you can pass the same token to a selective subset of operations:</span></span>

```csharp
var cts = new CancellationTokenSource();
    byte [] data = await DownloadDataAsync(url, cts.Token);
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);
    … // at some point later, potentially on another thread
    cts.Cancel();
```

 <span data-ttu-id="e6cdd-149">可以从任意线程启动取消请求。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-149">Cancellation requests may be initiated from any thread.</span></span>

 <span data-ttu-id="e6cdd-150">可以将 <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> 值传递给接受取消令牌的任何方法，指明绝不会请求取消操作。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-150">You can pass the <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> value to any method that accepts a cancellation token to indicate that cancellation will never be requested.</span></span>  <span data-ttu-id="e6cdd-151">这会导致 <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> 属性返回 `false`，并且调用的方法可以相应地进行优化。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-151">This causes the <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> property to return `false`, and the called method can optimize accordingly.</span></span>  <span data-ttu-id="e6cdd-152">出于测试目的，还可以通过传入预取消标记（该标记使用接受布尔值的构造函数进行实例化）来指示是否应以已取消或未取消状态启动标记。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-152">For testing purposes, you can also pass in a pre-canceled cancellation token that is instantiated by using the constructor that accepts a Boolean value to indicate whether the token should start in an already-canceled or not-cancelable state.</span></span>

 <span data-ttu-id="e6cdd-153">使用此方法进行取消具有以下优点：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-153">This approach to cancellation has several advantages:</span></span>

- <span data-ttu-id="e6cdd-154">可以将相同的取消标记传递给任意数量的异步和同步操作。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-154">You can pass the same cancellation token to any number of asynchronous and synchronous operations.</span></span>

- <span data-ttu-id="e6cdd-155">相同的取消请求可能会扩展到任意数量的侦听器。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-155">The same cancellation request may be proliferated to any number of listeners.</span></span>

- <span data-ttu-id="e6cdd-156">异步 API 的开发人员可完全控制是否可以请求取消以及取消何时生效。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-156">The developer of the asynchronous API is in complete control of whether cancellation may be requested and when it may take effect.</span></span>

- <span data-ttu-id="e6cdd-157">使用 API 的代码可以选择性地确定将对其传播取消请求的异步调用。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-157">The code that consumes the API may selectively determine the asynchronous invocations that cancellation requests will be propagated to.</span></span>

## <a name="monitoring-progress"></a><span data-ttu-id="e6cdd-158">监视进度</span><span class="sxs-lookup"><span data-stu-id="e6cdd-158">Monitoring Progress</span></span>
 <span data-ttu-id="e6cdd-159">某些异步方法通过传入异步方法的进度接口来公开进度。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-159">Some asynchronous methods expose progress through a progress interface passed into the asynchronous method.</span></span>  <span data-ttu-id="e6cdd-160">例如，设想某个函数以异步方式下载文本字符串，并在该过程中引发包括到目前为止下载完成百分比的进度更新。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-160">For example, consider a function which asynchronously downloads a string of text, and along the way raises progress updates that include the percentage of the download that has completed thus far.</span></span>  <span data-ttu-id="e6cdd-161">此类方法可在 Windows Presentation Foundation (WPF) 应用程序中使用，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-161">Such a method could be consumed in a Windows Presentation Foundation (WPF) application as follows:</span></span>

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtResult.Text = await DownloadStringAsync(txtUrl.Text,
            new Progress<int>(p => pbDownloadProgress.Value = p));
    }
    finally { btnDownload.IsEnabled = true; }
}
```

<a name="combinators"></a>
## <a name="using-the-built-in-task-based-combinators"></a><span data-ttu-id="e6cdd-162">使用内置的基于任务的连结符</span><span class="sxs-lookup"><span data-stu-id="e6cdd-162">Using the Built-in Task-based Combinators</span></span>
 <span data-ttu-id="e6cdd-163"><xref:System.Threading.Tasks> 命名空间包含多个方法，可用于撰写和处理任务。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-163">The <xref:System.Threading.Tasks> namespace includes several methods for composing and working with tasks.</span></span>

### <a name="taskrun"></a><span data-ttu-id="e6cdd-164">Task.Run</span><span class="sxs-lookup"><span data-stu-id="e6cdd-164">Task.Run</span></span>
 <span data-ttu-id="e6cdd-165"><xref:System.Threading.Tasks.Task> 类包含多个 <xref:System.Threading.Tasks.Task.Run%2A> 方法，以便于将工作作为 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 轻松卸载到线程池，例如：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-165">The <xref:System.Threading.Tasks.Task> class includes several <xref:System.Threading.Tasks.Task.Run%2A> methods that let you easily offload work as a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> to the thread pool, for example:</span></span>

```csharp
public async void button1_Click(object sender, EventArgs e)
{
    textBox1.Text = await Task.Run(() =>
    {
        // … do compute-bound work here
        return answer;
    });
}
```

 <span data-ttu-id="e6cdd-166">其中部分 <xref:System.Threading.Tasks.Task.Run%2A> 方法（如 <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> 重载）以 <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> 方法的简约表示形式存在。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-166">Some of these <xref:System.Threading.Tasks.Task.Run%2A> methods, such as the <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> overload, exist as shorthand for the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="e6cdd-167">借助其他重载（如 <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>），可以在卸载的工作内使用 await，例如：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-167">Other overloads, such as <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, enable you to use await within the offloaded work, for example:</span></span>

```csharp
public async void button1_Click(object sender, EventArgs e)
{
    pictureBox1.Image = await Task.Run(async() =>
    {
        using(Bitmap bmp1 = await DownloadFirstImageAsync())
        using(Bitmap bmp2 = await DownloadSecondImageAsync())
        return Mashup(bmp1, bmp2);
    });
}
```

 <span data-ttu-id="e6cdd-168">此类重载在逻辑上相当于结合使用 <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> 方法和任务并行库中的 <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> 扩展方法。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-168">Such overloads are logically equivalent to using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method in conjunction with the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension method in the Task Parallel Library.</span></span>

### <a name="taskfromresult"></a><span data-ttu-id="e6cdd-169">Task.FromResult</span><span class="sxs-lookup"><span data-stu-id="e6cdd-169">Task.FromResult</span></span>
 <span data-ttu-id="e6cdd-170"><xref:System.Threading.Tasks.Task.FromResult%2A> 方法的适用情景为，数据可能已存在，且只需通过提升到 <xref:System.Threading.Tasks.Task%601> 的任务返回方法返回：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-170">Use the <xref:System.Threading.Tasks.Task.FromResult%2A> method in scenarios where data may already be available and just needs to be returned from a task-returning method lifted into a <xref:System.Threading.Tasks.Task%601>:</span></span>

```csharp
public Task<int> GetValueAsync(string key)
{
    int cachedValue;
    return TryGetCachedValue(out cachedValue) ?
        Task.FromResult(cachedValue) :
        GetValueAsyncInternal();
}

private async Task<int> GetValueAsyncInternal(string key)
{
    …
}
```

### <a name="taskwhenall"></a><span data-ttu-id="e6cdd-171">Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="e6cdd-171">Task.WhenAll</span></span>
 <span data-ttu-id="e6cdd-172"><xref:System.Threading.Tasks.Task.WhenAll%2A> 方法可用于异步等待多个表示为任务的异步操作。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-172">Use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method to asynchronously wait on multiple asynchronous operations that are represented as tasks.</span></span>  <span data-ttu-id="e6cdd-173">该方法所具有的多个重载支持一组非泛型任务或一组不统一的常规任务（如异步等待多个返回 void 的操作，或异步等待多个返回值的方法，其中每个值可能具有不同类型），并支持一组统一的常规任务（如异步等待多个 `TResult` 返回方法）。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-173">The method has multiple overloads that support a set of non-generic tasks or a non-uniform set of generic tasks (for example, asynchronously waiting for multiple void-returning operations, or asynchronously waiting for multiple value-returning methods where each value may have a different type) and to support a uniform set of generic tasks (such as asynchronously waiting for multiple `TResult`-returning methods).</span></span>

 <span data-ttu-id="e6cdd-174">假设你想要向多个客户发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-174">Let's say you want to send email messages to several customers.</span></span> <span data-ttu-id="e6cdd-175">你可以重叠发送邮件，因此发送邮件时无需等待上一封邮件完成发送。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-175">You can overlap sending the messages so you're not waiting for one message to complete before sending the next.</span></span> <span data-ttu-id="e6cdd-176">还可以查看发送操作完成的时间，以及是否发生了错误：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-176">You can also find out when the send operations have completed and whether any errors have occurred:</span></span>

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
await Task.WhenAll(asyncOps);
```

 <span data-ttu-id="e6cdd-177">此代码不显式处理可能发生的异常，而是通过对 <xref:System.Threading.Tasks.Task.WhenAll%2A> 生成的任务执行 `await` 传播异常。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-177">This code doesn't explicitly handle exceptions that may occur, but lets exceptions propagate out of the `await` on the resulting task from <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span></span>  <span data-ttu-id="e6cdd-178">若要处理该异常，可以使用以下代码：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-178">To handle the exceptions, you can use code such as the following:</span></span>

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    ...
}
```

 <span data-ttu-id="e6cdd-179">在这种情况下，如果任意异步操作失败，所有异常都会合并到 <xref:System.AggregateException> 异常中，此异常存储在 <xref:System.Threading.Tasks.Task.WhenAll%2A> 方法返回的 <xref:System.Threading.Tasks.Task> 中。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-179">In this case, if any asynchronous operation fails, all the exceptions will be consolidated in an <xref:System.AggregateException> exception, which is stored in the <xref:System.Threading.Tasks.Task> that is returned from the <xref:System.Threading.Tasks.Task.WhenAll%2A> method.</span></span>  <span data-ttu-id="e6cdd-180">但是，仅通过 `await` 关键字传播其中一个异常。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-180">However, only one of those exceptions is propagated by the `await` keyword.</span></span>  <span data-ttu-id="e6cdd-181">如果想要检查所有异常，可以重写前面的代码，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-181">If you want to examine all the exceptions, you can rewrite the previous code as follows:</span></span>

```csharp
Task [] asyncOps = (from addr in addrs select SendMailAsync(addr)).ToArray();
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    foreach(Task faulted in asyncOps.Where(t => t.IsFaulted))
    {
        … // work with faulted and faulted.Exception
    }
}
```

 <span data-ttu-id="e6cdd-182">让我们考虑一下以异步方式从 Web 下载多个文件的示例。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-182">Let's consider an example of downloading multiple files from the web asynchronously.</span></span>  <span data-ttu-id="e6cdd-183">在此示例中，所有异步操作具有相同的结果类型，并很容易对结果进行访问：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-183">In this case, all the asynchronous operations have homogeneous result types, and it's easy to access the results:</span></span>

```csharp
string [] pages = await Task.WhenAll(
    from url in urls select DownloadStringAsync(url));
```

 <span data-ttu-id="e6cdd-184">可以使用上一个返回 void 方案中所讨论的异常处理技术：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-184">You can use the same exception-handling techniques we discussed in the previous void-returning scenario:</span></span>

```csharp
Task [] asyncOps =
    (from url in urls select DownloadStringAsync(url)).ToArray();
try
{
    string [] pages = await Task.WhenAll(asyncOps);
    ...
}
catch(Exception exc)
{
    foreach(Task<string> faulted in asyncOps.Where(t => t.IsFaulted))
    {
        … // work with faulted and faulted.Exception
    }
}
```

### <a name="taskwhenany"></a><span data-ttu-id="e6cdd-185">Task.WhenAny</span><span class="sxs-lookup"><span data-stu-id="e6cdd-185">Task.WhenAny</span></span>
 <span data-ttu-id="e6cdd-186"><xref:System.Threading.Tasks.Task.WhenAny%2A> 方法可用于异步等待多个表示为要完成的任务的异步操作之一。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-186">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to asynchronously wait for just one of multiple asynchronous operations represented as tasks to complete.</span></span>  <span data-ttu-id="e6cdd-187">此方法适用于四个主要用例：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-187">This method serves four primary use cases:</span></span>

- <span data-ttu-id="e6cdd-188">冗余：多次执行一个操作并选择最先完成的一次（例如，联系将生成一个结果的多个股市行情 Web 服务并选择最快完成的一个）。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-188">Redundancy:  Performing an operation multiple times and selecting the one that completes first (for example, contacting multiple stock quote web services that will produce a single result and selecting the one that completes the fastest).</span></span>

- <span data-ttu-id="e6cdd-189">交错：启动多个操作并等待所有这些操作完成，但在这些操作完成时对其进行处理。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-189">Interleaving:  Launching multiple operations and waiting for all of them to complete, but processing them as they complete.</span></span>

- <span data-ttu-id="e6cdd-190">限制：允许在其他操作完成时开始附加操作。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-190">Throttling:  Allowing additional operations to begin as others complete.</span></span>  <span data-ttu-id="e6cdd-191">这是交错方案的扩展。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-191">This is an extension of the interleaving scenario.</span></span>

- <span data-ttu-id="e6cdd-192">早期释放：例如，用任务 t1 表示的操作可以与任务 t2 组成 <xref:System.Threading.Tasks.Task.WhenAny%2A> 任务，并且可以等待 <xref:System.Threading.Tasks.Task.WhenAny%2A> 任务。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-192">Early bailout:  For example, an operation represented by task t1 can be grouped in a <xref:System.Threading.Tasks.Task.WhenAny%2A> task with another task t2, and you can wait on the <xref:System.Threading.Tasks.Task.WhenAny%2A> task.</span></span> <span data-ttu-id="e6cdd-193">任务 t2 可以表示超时、取消或其他一些导致 <xref:System.Threading.Tasks.Task.WhenAny%2A> 任务先于 t1 完成的信号。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-193">Task t2 could represent a time-out, or cancellation, or some other signal that causes the <xref:System.Threading.Tasks.Task.WhenAny%2A> task to complete before t1 completes.</span></span>

#### <a name="redundancy"></a><span data-ttu-id="e6cdd-194">冗余</span><span class="sxs-lookup"><span data-stu-id="e6cdd-194">Redundancy</span></span>
 <span data-ttu-id="e6cdd-195">假设你想要决定是否购买股票。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-195">Consider a case where you want to make a decision about whether to buy a stock.</span></span>  <span data-ttu-id="e6cdd-196">你信任一些股票建议 Web 服务，但每个服务最终会在不同的时间段变得很慢，具体取决于每日负载。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-196">There are several stock recommendation web services that you trust, but depending on daily load, each service can end up being slow at different times.</span></span>  <span data-ttu-id="e6cdd-197"><xref:System.Threading.Tasks.Task.WhenAny%2A> 方法可用于在任何操作完成时接收通知：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-197">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to receive a notification when any operation completes:</span></span>

```csharp
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol),
    GetBuyRecommendation2Async(symbol),
    GetBuyRecommendation3Async(symbol)
};
Task<bool> recommendation = await Task.WhenAny(recommendations);
if (await recommendation) BuyStock(symbol);
```

 <span data-ttu-id="e6cdd-198"><xref:System.Threading.Tasks.Task.WhenAll%2A> 返回已成功完成的所有任务的取消包装结果。与它不同，<xref:System.Threading.Tasks.Task.WhenAny%2A> 返回已完成的任意任务。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-198">Unlike <xref:System.Threading.Tasks.Task.WhenAll%2A>, which returns the unwrapped results of all tasks that completed successfully, <xref:System.Threading.Tasks.Task.WhenAny%2A> returns the task that completed.</span></span> <span data-ttu-id="e6cdd-199">如果任务失败，重要的是知道该任务失败，如果任务成功，重要的是知道返回值与哪个任务相关联。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-199">If a task fails, it’s important to know that it failed, and if a task succeeds, it’s important to know which task the return value is associated with.</span></span>  <span data-ttu-id="e6cdd-200">因此，你需要访问返回任务的结果，或进一步等待，如本示例中所示。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-200">Therefore, you need to access the result of the returned task, or further await it, as  this example shows.</span></span>

 <span data-ttu-id="e6cdd-201">与 <xref:System.Threading.Tasks.Task.WhenAll%2A> 一样，必须能够容纳异常。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-201">As with <xref:System.Threading.Tasks.Task.WhenAll%2A>, you have to be able to accommodate exceptions.</span></span>  <span data-ttu-id="e6cdd-202">因为接收到完成的任务后，可以等待返回的任务传播错误，并适当地进行 `try/catch`，例如：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-202">Because you receive the completed task back, you can await the returned task to have errors propagated, and `try/catch` them appropriately; for example:</span></span>

```csharp
Task<bool> [] recommendations = …;
while(recommendations.Count > 0)
{
    Task<bool> recommendation = await Task.WhenAny(recommendations);
    try
    {
        if (await recommendation) BuyStock(symbol);
        break;
    }
    catch(WebException exc)
    {
        recommendations.Remove(recommendation);
    }
}
```

 <span data-ttu-id="e6cdd-203">此外，即使第一个任务成功完成，后续任务也可能会失败。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-203">Additionally, even if a first task completes successfully, subsequent tasks may fail.</span></span>  <span data-ttu-id="e6cdd-204">此时，有多个用于处理异常的选项：可以等待所有启动的任务完成，在这种情况下可以使用 <xref:System.Threading.Tasks.Task.WhenAll%2A> 方法；或者做出所有异常都重要且必须记录的决定。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-204">At this point, you have several options for dealing with exceptions:  You can wait until all the launched tasks have completed, in which case you can use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method, or you can decide that all exceptions are important and must be logged.</span></span>  <span data-ttu-id="e6cdd-205">为此，可以使用延续任务以在任务异步完成时接收通知：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-205">For this, you can use continuations to receive a notification when tasks have completed asynchronously:</span></span>

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => { if (t.IsFaulted) Log(t.Exception); });
}
```

 <span data-ttu-id="e6cdd-206">或：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-206">or:</span></span>

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => Log(t.Exception), TaskContinuationOptions.OnlyOnFaulted);
}
```

 <span data-ttu-id="e6cdd-207">或者甚至：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-207">or even:</span></span>

```csharp
private static async void LogCompletionIfFailed(IEnumerable<Task> tasks)
{
    foreach(var task in tasks)
    {
        try { await task; }
        catch(Exception exc) { Log(exc); }
    }
}
…
LogCompletionIfFailed(recommendations);
```

 <span data-ttu-id="e6cdd-208">最后，若要取消所有剩余操作：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-208">Finally, you may want to cancel all the remaining operations:</span></span>

```csharp
var cts = new CancellationTokenSource();
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol, cts.Token),
    GetBuyRecommendation2Async(symbol, cts.Token),
    GetBuyRecommendation3Async(symbol, cts.Token)
};

Task<bool> recommendation = await Task.WhenAny(recommendations);
cts.Cancel();
if (await recommendation) BuyStock(symbol);
```

#### <a name="interleaving"></a><span data-ttu-id="e6cdd-209">交错</span><span class="sxs-lookup"><span data-stu-id="e6cdd-209">Interleaving</span></span>
 <span data-ttu-id="e6cdd-210">假设你要从 Web 下载图像，并且处理每个图像（例如，将图像添加到 UI 控件）。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-210">Consider a case where you're downloading images from the web and processing each image (for example, adding the image to a UI control).</span></span>  <span data-ttu-id="e6cdd-211">必须在 UI 线程上按顺序对其进行处理，但你希望尽可能同时下载图像。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-211">You have to do the processing sequentially on the UI thread, but you want to download the images as concurrently as possible.</span></span> <span data-ttu-id="e6cdd-212">此外，你不想直到所有图像都下载完成才将图像添加到 UI — 你希望图像下载完成后就进行添加：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-212">Also, you don’t want to hold up adding the images to the UI until they’re all downloaded—you want to add them as they complete:</span></span>

```csharp
List<Task<Bitmap>> imageTasks =
    (from imageUrl in urls select GetBitmapAsync(imageUrl)).ToList();
while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch{}
}
```

 <span data-ttu-id="e6cdd-213">还可以将交错应用于涉及下载图像 <xref:System.Threading.ThreadPool> 的计算密集型处理的方案；例如：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-213">You can also apply interleaving to a scenario that involves computationally intensive processing on the <xref:System.Threading.ThreadPool> of the downloaded images; for example:</span></span>

```csharp
List<Task<Bitmap>> imageTasks =
    (from imageUrl in urls select GetBitmapAsync(imageUrl)
         .ContinueWith(t => ConvertImage(t.Result)).ToList();
while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch{}
}
```

#### <a name="throttling"></a><span data-ttu-id="e6cdd-214">遏制</span><span class="sxs-lookup"><span data-stu-id="e6cdd-214">Throttling</span></span>
 <span data-ttu-id="e6cdd-215">请考虑交错示例，因用户大量下载图像而导致下载必须受到遏制除外；例如，你希望仅能同时下载特定数目的内容。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-215">Consider the interleaving example, except that the user is downloading so many images that the downloads have to be throttled; for example, you want only a specific number of downloads to happen concurrently.</span></span> <span data-ttu-id="e6cdd-216">为此，可以启动异步操作的子集。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-216">To achieve this, you can start a subset of the asynchronous operations.</span></span>  <span data-ttu-id="e6cdd-217">操作完成后，你可以启动其他操作对其进行替代：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-217">As operations complete, you can start additional operations to take their place:</span></span>

```csharp
const int CONCURRENCY_LEVEL = 15;
Uri [] urls = …;
int nextIndex = 0;
var imageTasks = new List<Task<Bitmap>>();
while(nextIndex < CONCURRENCY_LEVEL && nextIndex < urls.Length)
{
    imageTasks.Add(GetBitmapAsync(urls[nextIndex]));
    nextIndex++;
}

while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch(Exception exc) { Log(exc); }

    if (nextIndex < urls.Length)
    {
        imageTasks.Add(GetBitmapAsync(urls[nextIndex]));
        nextIndex++;
    }
}
```

#### <a name="early-bailout"></a><span data-ttu-id="e6cdd-218">早期释放</span><span class="sxs-lookup"><span data-stu-id="e6cdd-218">Early Bailout</span></span>
 <span data-ttu-id="e6cdd-219">假设正在异步等待某个操作完成的同时，对用户的取消请求的进行响应（例如，用户单击取消按钮）。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-219">Consider that you're waiting asynchronously for an operation to complete while simultaneously responding to a user’s cancellation request (for example, the user clicked a cancel button).</span></span> <span data-ttu-id="e6cdd-220">以下代码阐释了此方案：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-220">The following code illustrates this scenario:</span></span>

```csharp
private CancellationTokenSource m_cts;

public void btnCancel_Click(object sender, EventArgs e)
{
    if (m_cts != null) m_cts.Cancel();
}

public async void btnRun_Click(object sender, EventArgs e)
{
    m_cts = new CancellationTokenSource();
    btnRun.Enabled = false;
    try
    {
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text);
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);
        if (imageDownload.IsCompleted)
        {
            Bitmap image = await imageDownload;
            panel.AddImage(image);
        }
        else imageDownload.ContinueWith(t => Log(t));
    }
    finally { btnRun.Enabled = true; }
}

private static async Task UntilCompletionOrCancellation(
    Task asyncOp, CancellationToken ct)
{
    var tcs = new TaskCompletionSource<bool>();
    using(ct.Register(() => tcs.TrySetResult(true)))
        await Task.WhenAny(asyncOp, tcs.Task);
    return asyncOp;
}
```

 <span data-ttu-id="e6cdd-221">一旦决定退出，此实现将重新启用用户界面，但不会取消基础异步操作。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-221">This implementation re-enables the user interface as soon as you decide to bail out, but doesn't cancel the underlying asynchronous operations.</span></span>  <span data-ttu-id="e6cdd-222">另一种选择是决定退出时，取消挂起的操作，但在操作实际完成之前不重新建立用户界面，可能会由于取消请求而提前结束：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-222">Another alternative would be to cancel the pending operations when you decide to bail out, but not reestablish the user interface until the operations actually complete, potentially due to ending early due to the cancellation request:</span></span>

```csharp
private CancellationTokenSource m_cts;

public async void btnRun_Click(object sender, EventArgs e)
{
    m_cts = new CancellationTokenSource();

    btnRun.Enabled = false;
    try
    {
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text, m_cts.Token);
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);
        Bitmap image = await imageDownload;
        panel.AddImage(image);
    }
    catch(OperationCanceledException) {}
    finally { btnRun.Enabled = true; }
}
```

 <span data-ttu-id="e6cdd-223">另一个早期释放示例涉及结合使用 <xref:System.Threading.Tasks.Task.WhenAny%2A> 方法和 <xref:System.Threading.Tasks.Task.Delay%2A> 方法，下一部分将对此进行介绍。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-223">Another example of early bailout involves using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method in conjunction with the <xref:System.Threading.Tasks.Task.Delay%2A> method, as discussed in the next section.</span></span>

### <a name="taskdelay"></a><span data-ttu-id="e6cdd-224">Task.Delay</span><span class="sxs-lookup"><span data-stu-id="e6cdd-224">Task.Delay</span></span>
 <span data-ttu-id="e6cdd-225"><xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> 方法可用于将暂停引入异步方法的执行中。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-225">You can use the <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method to introduce pauses into an asynchronous method’s execution.</span></span>  <span data-ttu-id="e6cdd-226">这对于许多功能都非常有用，包括构建轮询循环和延迟预定时间段的用户输入处理。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-226">This is useful for many kinds of functionality, including building polling loops and delaying the handling of user input for a predetermined period of time.</span></span>  <span data-ttu-id="e6cdd-227"><xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> 方法还可以与 <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> 结合使用，以对 await 实现超时。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-227">The <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method can also be useful in combination with <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> for implementing time-outs on awaits.</span></span>

 <span data-ttu-id="e6cdd-228">如果某任务属于较大型异步操作（如 ASP.NET Web 服务）中的一部分，由于花费时间过长而不能完成，则整体操作可能会受到影响（尤其是此任务一直不能完成的情况下）。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-228">If a task that’s part of a larger asynchronous operation (for example, an ASP.NET web service) takes too long to complete, the overall operation could suffer, especially if it fails to ever complete.</span></span>  <span data-ttu-id="e6cdd-229">因此，等待异步操作时可以超时非常重要。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-229">For this reason, it’s important to be able to time out when waiting on an asynchronous operation.</span></span>  <span data-ttu-id="e6cdd-230">虽然同步 <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>、<xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> 方法接受超时值，但相应的 <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> 和前述 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> 方法不接受。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-230">The synchronous <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> methods accept time-out values, but the corresponding <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> and the previously mentioned <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> methods do not.</span></span>  <span data-ttu-id="e6cdd-231">相反，可以将 <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> 与 <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>结合使用，以实现超时。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-231">Instead, you can use <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> in combination to implement a time-out.</span></span>

 <span data-ttu-id="e6cdd-232">例如，在 UI 应用程序中，假设你想要下载图像，并在图像下载期间禁用该 UI。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-232">For example, in your UI application, let's say that you want to download an image and disable the UI while the image is downloading.</span></span> <span data-ttu-id="e6cdd-233">但是，如果下载时间过长，你希望重新启用 UI 并放弃下载：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-233">However, if the download takes too long, you want to re-enable the UI and discard the download:</span></span>

```csharp
public async void btnDownload_Click(object sender, EventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap> download = GetBitmapAsync(url);
        if (download == await Task.WhenAny(download, Task.Delay(3000)))
        {
            Bitmap bmp = await download;
            pictureBox.Image = bmp;
            status.Text = "Downloaded";
        }
        else
        {
            pictureBox.Image = null;
            status.Text = "Timed out";
            var ignored = download.ContinueWith(
                t => Trace("Task finally completed"));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

 <span data-ttu-id="e6cdd-234">这同样适用于多个下载，因为 <xref:System.Threading.Tasks.Task.WhenAll%2A> 返回任务：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-234">The same applies to multiple downloads, because <xref:System.Threading.Tasks.Task.WhenAll%2A> returns a task:</span></span>

```csharp
public async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap[]> downloads =
            Task.WhenAll(from url in urls select GetBitmapAsync(url));
        if (downloads == await Task.WhenAny(downloads, Task.Delay(3000)))
        {
            foreach(var bmp in downloads) panel.AddImage(bmp);
            status.Text = "Downloaded";
        }
        else
        {
            status.Text = "Timed out";
            downloads.ContinueWith(t => Log(t));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

## <a name="building-task-based-combinators"></a><span data-ttu-id="e6cdd-235">构建基于任务的连结符</span><span class="sxs-lookup"><span data-stu-id="e6cdd-235">Building Task-based Combinators</span></span>
 <span data-ttu-id="e6cdd-236">因为任务可以完全代表异步操作、提供同步和异步功能来加入操作、检索其结果等，所以可以构建组成任务的连结符的库以构建更大的模式。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-236">Because a task is able to completely represent an asynchronous operation and provide synchronous and asynchronous capabilities for joining with the operation, retrieving its results, and so on, you can build useful libraries of combinators that compose tasks to build larger patterns.</span></span>  <span data-ttu-id="e6cdd-237">如前一部分所述，.NET Framework 包括一些内置连结符，但是，你也可以构建自己的连结符。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-237">As discussed in the previous section, the .NET Framework includes several built-in combinators, but you can also build your own.</span></span> <span data-ttu-id="e6cdd-238">以下各节提供了一些潜在的连结符方法和类型的示例。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-238">The following sections provide several examples of potential combinator methods and types.</span></span>

### <a name="retryonfault"></a><span data-ttu-id="e6cdd-239">RetryOnFault</span><span class="sxs-lookup"><span data-stu-id="e6cdd-239">RetryOnFault</span></span>
 <span data-ttu-id="e6cdd-240">在许多情况下，如果上次尝试失败，你可能想要重试操作。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-240">In many situations, you may want to retry an operation if a previous attempt fails.</span></span>  <span data-ttu-id="e6cdd-241">对于同步代码，你可能会构建一个帮助器方法来实现此目的，如下例中的 `RetryOnFault`：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-241">For synchronous code, you might build a helper method such as `RetryOnFault` in the following example to accomplish this:</span></span>

```csharp
public static T RetryOnFault<T>(
    Func<T> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return function(); }
        catch { if (i == maxTries-1) throw; }
    }
    return default(T);
}
```

 <span data-ttu-id="e6cdd-242">你可以为异步操作（使用 TAP 实现，因此返回任务）构建几乎相同的帮助器方法：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-242">You can build an almost identical helper method for asynchronous operations that are implemented with TAP and thus return tasks:</span></span>

```csharp
public static async Task<T> RetryOnFault<T>(
    Func<Task<T>> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return await function().ConfigureAwait(false); }
        catch { if (i == maxTries-1) throw; }
    }
    return default(T);
}
```

 <span data-ttu-id="e6cdd-243">然后，可以使用此连结符将重试编码到应用程序的逻辑中，例如：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-243">You can then use this combinator to encode retries into the application’s logic; for example:</span></span>

```csharp
// Download the URL, trying up to three times in case of failure
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3);
```

 <span data-ttu-id="e6cdd-244">可以进一步扩展 `RetryOnFault` 函数。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-244">You could extend the `RetryOnFault` function further.</span></span> <span data-ttu-id="e6cdd-245">例如，该函数可以接受另一个 `Func<Task>`（在重试间隔期间调用以确定何时重试该操作）：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-245">For example, the function could accept another `Func<Task>` that will be invoked between retries to determine when to try the operation again; for example:</span></span>

```csharp
public static async Task<T> RetryOnFault<T>(
    Func<Task<T>> function, int maxTries, Func<Task> retryWhen)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return await function().ConfigureAwait(false); }
        catch { if (i == maxTries-1) throw; }
        await retryWhen().ConfigureAwait(false);
    }
    return default(T);
}
```

 <span data-ttu-id="e6cdd-246">重试该操作前，可以使用以下函数等待片刻：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-246">You could then use the function as follows to wait for a second before retrying the operation:</span></span>

```csharp
// Download the URL, trying up to three times in case of failure,
// and delaying for a second between retries
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));
```

### <a name="needonlyone"></a><span data-ttu-id="e6cdd-247">NeedOnlyOne</span><span class="sxs-lookup"><span data-stu-id="e6cdd-247">NeedOnlyOne</span></span>
 <span data-ttu-id="e6cdd-248">有时，你可以利用冗余改进操作延迟和提高成功的可能性。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-248">Sometimes, you can take advantage of redundancy to improve an operation’s latency and chances for success.</span></span>  <span data-ttu-id="e6cdd-249">假设有多个 Web 服务提供股票报价，但在一天中的不同时间，每个服务可能提供不同级别的质量和响应时间。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-249">Consider multiple web services that provide stock quotes, but at various times of the day, each service may provide different levels of quality and response times.</span></span>  <span data-ttu-id="e6cdd-250">为了应对这些波动，你可能会向所有 Web 服务发出请求，并且只要从其中一个获得响应，立刻取消剩余的请求。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-250">To deal with these fluctuations, you may issue requests to all the web services, and as soon as you get a response from one, cancel the remaining requests.</span></span>  <span data-ttu-id="e6cdd-251">你可以通过 helper 函数更轻松地实现此启动多个操作的通用模式：等待任何操作，然后取消其余部分。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-251">You can implement a helper function to make it easier to implement this common pattern of launching multiple operations, waiting for any, and then canceling the rest.</span></span> <span data-ttu-id="e6cdd-252">以下示例中的 `NeedOnlyOne` 函数阐释了这种方案：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-252">The `NeedOnlyOne` function in the following example illustrates this scenario:</span></span>

```csharp
public static async Task<T> NeedOnlyOne(
    params Func<CancellationToken,Task<T>> [] functions)
{
    var cts = new CancellationTokenSource();
    var tasks = (from function in functions
                 select function(cts.Token)).ToArray();
    var completed = await Task.WhenAny(tasks).ConfigureAwait(false);
    cts.Cancel();
    foreach(var task in tasks)
    {
        var ignored = task.ContinueWith(
            t => Log(t), TaskContinuationOptions.OnlyOnFaulted);
    }
    return completed;
}
```

 <span data-ttu-id="e6cdd-253">然后，你可以使用此函数，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-253">You can then use this function as follows:</span></span>

```csharp
double currentPrice = await NeedOnlyOne(
    ct => GetCurrentPriceFromServer1Async("msft", ct),
    ct => GetCurrentPriceFromServer2Async("msft", ct),
    ct => GetCurrentPriceFromServer3Async("msft", ct));
```

### <a name="interleaved-operations"></a><span data-ttu-id="e6cdd-254">交错操作</span><span class="sxs-lookup"><span data-stu-id="e6cdd-254">Interleaved Operations</span></span>
 <span data-ttu-id="e6cdd-255">处理大型任务集时，如果使用 <xref:System.Threading.Tasks.Task.WhenAny%2A> 方法支持交错方案，可能存在潜在性能问题。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-255">There is a potential performance problem with using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to support an interleaving scenario when you're working with very large sets of tasks.</span></span> <span data-ttu-id="e6cdd-256">每次调用 <xref:System.Threading.Tasks.Task.WhenAny%2A> 都会向每个任务注册延续。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-256">Every call to <xref:System.Threading.Tasks.Task.WhenAny%2A> results in a continuation being registered with each task.</span></span> <span data-ttu-id="e6cdd-257">对于 N 个任务，这将导致在交错操作的操作期间创建 O(N<sup>2</sup>) 次延续。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-257">For N number of tasks, this results in O(N<sup>2</sup>) continuations created over the lifetime of the interleaving operation.</span></span> <span data-ttu-id="e6cdd-258">如果处理大型任务集，则可以使用连结符（以下示例中的 `Interleaved`）来解决性能问题：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-258">If you're working with a large set of tasks, you can use a combinator (`Interleaved` in the following example) to address the performance issue:</span></span>

```csharp
static IEnumerable<Task<T>> Interleaved<T>(IEnumerable<Task<T>> tasks)
{
    var inputTasks = tasks.ToList();
    var sources = (from _ in Enumerable.Range(0, inputTasks.Count)
                   select new TaskCompletionSource<T>()).ToList();
    int nextTaskIndex = -1;
    foreach (var inputTask in inputTasks)
    {
        inputTask.ContinueWith(completed =>
        {
            var source = sources[Interlocked.Increment(ref nextTaskIndex)];
            if (completed.IsFaulted)
                source.TrySetException(completed.Exception.InnerExceptions);
            else if (completed.IsCanceled)
                source.TrySetCanceled();
            else
                source.TrySetResult(completed.Result);
        }, CancellationToken.None,
           TaskContinuationOptions.ExecuteSynchronously,
           TaskScheduler.Default);
    }
    return from source in sources
           select source.Task;
}
```

 <span data-ttu-id="e6cdd-259">然后，可以在任务完成时，使用连结符来处理任务的结果，例如：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-259">You can then use the combinator to process the results of tasks as they complete; for example:</span></span>

```csharp
IEnumerable<Task<int>> tasks = ...;
foreach(var task in Interleaved(tasks))
{
    int result = await task;
    …
}
```

### <a name="whenallorfirstexception"></a><span data-ttu-id="e6cdd-260">WhenAllOrFirstException</span><span class="sxs-lookup"><span data-stu-id="e6cdd-260">WhenAllOrFirstException</span></span>
 <span data-ttu-id="e6cdd-261">在特定的分散/集中情况下，你可能想要等待集中的所有任务，除非某个任务发生错误。在这种情况下，你希望在异常发生时停止等待。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-261">In certain scatter/gather scenarios, you might want to wait for all tasks in a set, unless one of them faults, in which case you want to stop waiting as soon as the exception occurs.</span></span>  <span data-ttu-id="e6cdd-262">你可以通过使用连结符方法（如 `WhenAllOrFirstException`）实现该目的，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-262">You can accomplish that with a combinator method such as `WhenAllOrFirstException` in the following example:</span></span>

```csharp
public static Task<T[]> WhenAllOrFirstException<T>(IEnumerable<Task<T>> tasks)
{
    var inputs = tasks.ToList();
    var ce = new CountdownEvent(inputs.Count);
    var tcs = new TaskCompletionSource<T[]>();

    Action<Task> onCompleted = (Task completed) =>
    {
        if (completed.IsFaulted)
            tcs.TrySetException(completed.Exception.InnerExceptions);
        if (ce.Signal() && !tcs.Task.IsCompleted)
            tcs.TrySetResult(inputs.Select(t => t.Result).ToArray());
    };

    foreach (var t in inputs) t.ContinueWith(onCompleted);
    return tcs.Task;
}
```

## <a name="building-task-based-data-structures"></a><span data-ttu-id="e6cdd-263">构建基于任务的数据结构</span><span class="sxs-lookup"><span data-stu-id="e6cdd-263">Building Task-based Data Structures</span></span>
 <span data-ttu-id="e6cdd-264">除了能够生成基于任务的自定义组合器外，<xref:System.Threading.Tasks.Task> 和表示异步操作结果和联接所必需同步操作结果的 <xref:System.Threading.Tasks.Task%601> 中有数据结构，这令其成为功能非常强大的类型，可用于生成在异步方案中使用的自定义数据结构。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-264">In addition to the ability to build custom task-based combinators, having a data structure in <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> that represents both the results of an asynchronous operation and the necessary synchronization to join with it makes it a very powerful type on which to build custom data structures to be used in asynchronous scenarios.</span></span>

### <a name="asynccache"></a><span data-ttu-id="e6cdd-265">AsyncCache</span><span class="sxs-lookup"><span data-stu-id="e6cdd-265">AsyncCache</span></span>
 <span data-ttu-id="e6cdd-266">任务的重要方面之一是，它可能会分发到多个使用者，所有使用者都可以等待任务、向任务注册延续、获取任务结果或异常（如果是 <xref:System.Threading.Tasks.Task%601> 的话）等。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-266">One important aspect of a task is that it may be handed out to multiple consumers, all of whom may await it, register continuations with it, get its result or exceptions (in the case of <xref:System.Threading.Tasks.Task%601>), and so on.</span></span>  <span data-ttu-id="e6cdd-267">这样一来，<xref:System.Threading.Tasks.Task> 和 <xref:System.Threading.Tasks.Task%601> 就非常适用于异步缓存基础结构。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-267">This makes <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> perfectly suited to be used in an asynchronous caching infrastructure.</span></span>  <span data-ttu-id="e6cdd-268">下面的示例展示了在 <xref:System.Threading.Tasks.Task%601> 基础之上生成的功能非常强大的小型异步缓存：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-268">Here’s an example of a small but powerful asynchronous cache built on top of <xref:System.Threading.Tasks.Task%601>:</span></span>

```csharp
public class AsyncCache<TKey, TValue>
{
    private readonly Func<TKey, Task<TValue>> _valueFactory;
    private readonly ConcurrentDictionary<TKey, Lazy<Task<TValue>>> _map;

    public AsyncCache(Func<TKey, Task<TValue>> valueFactory)
    {
        if (valueFactory == null) throw new ArgumentNullException("loader");
        _valueFactory = valueFactory;
        _map = new ConcurrentDictionary<TKey, Lazy<Task<TValue>>>();
    }

    public Task<TValue> this[TKey key]
    {
        get
        {
            if (key == null) throw new ArgumentNullException("key");
            return _map.GetOrAdd(key, toAdd =>
                new Lazy<Task<TValue>>(() => _valueFactory(toAdd))).Value;
        }
    }
}
```

 <span data-ttu-id="e6cdd-269">[AsyncCache\<TKey,TValue>](https://devblogs.microsoft.com/pfxteam/parallelextensionsextras-tour-12-asynccache/) 类接受需要使用 `TKey` 且返回 <xref:System.Threading.Tasks.Task%601> 的函数作为构造函数的委托。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-269">The [AsyncCache\<TKey,TValue>](https://devblogs.microsoft.com/pfxteam/parallelextensionsextras-tour-12-asynccache/) class accepts as a delegate to its constructor a function that takes a `TKey` and returns a <xref:System.Threading.Tasks.Task%601>.</span></span>  <span data-ttu-id="e6cdd-270">以前从缓存访问的所有值都存储在内部字典中，`AsyncCache` 可以确保每个密钥仅生成一个任务，即便同时访问缓存也是如此。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-270">Any previously accessed values from the cache are stored in the internal dictionary, and the `AsyncCache` ensures that only one task is generated per key, even if the cache is accessed concurrently.</span></span>

 <span data-ttu-id="e6cdd-271">例如，你可以生成下载网页的缓存：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-271">For example, you can build a cache for downloaded web pages:</span></span>

```csharp
private AsyncCache<string,string> m_webPages =
    new AsyncCache<string,string>(DownloadStringAsync);
```

 <span data-ttu-id="e6cdd-272">然后可以在任何需要网页内容的时候，以异步方式使用此缓存。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-272">You can then use this cache in asynchronous methods whenever you need the contents of a web page.</span></span> <span data-ttu-id="e6cdd-273">`AsyncCache` 类可确保下载尽可能少的页面，并缓存结果。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-273">The `AsyncCache` class ensures that you’re downloading as few pages as possible, and caches the results.</span></span>

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtContents.Text = await m_webPages["https://www.microsoft.com"];
    }
    finally { btnDownload.IsEnabled = true; }
}
```

### <a name="asyncproducerconsumercollection"></a><span data-ttu-id="e6cdd-274">AsyncProducerConsumerCollection</span><span class="sxs-lookup"><span data-stu-id="e6cdd-274">AsyncProducerConsumerCollection</span></span>
 <span data-ttu-id="e6cdd-275">你还可以使用任务来构建协调异步活动的数据结构。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-275">You can also use tasks to build data structures for coordinating asynchronous activities.</span></span>  <span data-ttu-id="e6cdd-276">请考虑经典的并行设计模式之一：制造者/使用者。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-276">Consider one of the classic parallel design patterns: producer/consumer.</span></span>  <span data-ttu-id="e6cdd-277">在此模式下，制造者生成数据，使用者使用数据，制造者和使用者可能会并行运行。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-277">In this pattern, producers generate data that is consumed by consumers, and the producers and consumers may run in parallel.</span></span> <span data-ttu-id="e6cdd-278">例如，使用者处理之前由制造者生成的第 1 项，而制造者现在正在制造第 2 项。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-278">For example, the consumer processes item 1, which was previously generated by a producer who is now producing item 2.</span></span>  <span data-ttu-id="e6cdd-279">对于制造者/使用者模式，总是需要某种数据结构来存储制造者创建的工作，以便使用者可以收到新数据的通知并及时发现新数据。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-279">For the producer/consumer pattern, you invariably need some data structure to store the work created by producers so that the consumers may be notified of new data and find it when available.</span></span>

 <span data-ttu-id="e6cdd-280">以下是基于任务构建的简单数据结构，可以将异步方法用作制造者和使用者：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-280">Here’s a simple data structure built on top of tasks that enables asynchronous methods to be used as producers and consumers:</span></span>

```csharp
public class AsyncProducerConsumerCollection<T>
{
    private readonly Queue<T> m_collection = new Queue<T>();
    private readonly Queue<TaskCompletionSource<T>> m_waiting =
        new Queue<TaskCompletionSource<T>>();

    public void Add(T item)
    {
        TaskCompletionSource<T> tcs = null;
        lock (m_collection)
        {
            if (m_waiting.Count > 0) tcs = m_waiting.Dequeue();
            else m_collection.Enqueue(item);
        }
        if (tcs != null) tcs.TrySetResult(item);
    }

    public Task<T> Take()
    {
        lock (m_collection)
        {
            if (m_collection.Count > 0)
            {
                return Task.FromResult(m_collection.Dequeue());
            }
            else
            {
                var tcs = new TaskCompletionSource<T>();
                m_waiting.Enqueue(tcs);
                return tcs.Task;
            }
        }
    }
}
```

 <span data-ttu-id="e6cdd-281">通过该数据结构，可以编写如下所示的代码：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-281">With that data structure in place, you can write code such as the following:</span></span>

```csharp
private static AsyncProducerConsumerCollection<int> m_data = …;
…
private static async Task ConsumerAsync()
{
    while(true)
    {
        int nextItem = await m_data.Take();
        ProcessNextItem(nextItem);
    }
}
…
private static void Produce(int data)
{
    m_data.Add(data);
}
```

<span data-ttu-id="e6cdd-282"><xref:System.Threading.Tasks.Dataflow> 命名空间包括 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 类型，可以类似方式使用它，但无需生成自定义集合类型：</span><span class="sxs-lookup"><span data-stu-id="e6cdd-282">The <xref:System.Threading.Tasks.Dataflow> namespace includes the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> type, which you can use in a similar manner, but without having to build a custom collection type:</span></span>

```csharp
private static BufferBlock<int> m_data = …;
…
private static async Task ConsumerAsync()
{
    while(true)
    {
        int nextItem = await m_data.ReceiveAsync();
        ProcessNextItem(nextItem);
    }
}
…
private static void Produce(int data)
{
    m_data.Post(data);
}
```

> [!NOTE]
> <span data-ttu-id="e6cdd-283"><xref:System.Threading.Tasks.Dataflow> 命名空间通过 NuGet 可用于 .NET Framework 4.5。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-283">The <xref:System.Threading.Tasks.Dataflow> namespace is available in the .NET Framework 4.5 through **NuGet**.</span></span> <span data-ttu-id="e6cdd-284">若要安装包含 <xref:System.Threading.Tasks.Dataflow> 命名空间的程序集，请在 Visual Studio 中打开项目，选择“项目”菜单中的“管理 NuGet 包”，再在线搜索 Microsoft.Tpl.Dataflow 包。</span><span class="sxs-lookup"><span data-stu-id="e6cdd-284">To install the assembly that contains the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in Visual Studio, choose **Manage NuGet Packages** from the Project menu, and search online for the Microsoft.Tpl.Dataflow package.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6cdd-285">请参阅</span><span class="sxs-lookup"><span data-stu-id="e6cdd-285">See also</span></span>

- [<span data-ttu-id="e6cdd-286">基于任务的异步模式 (TAP)</span><span class="sxs-lookup"><span data-stu-id="e6cdd-286">Task-based Asynchronous Pattern (TAP)</span></span>](task-based-asynchronous-pattern-tap.md)
- [<span data-ttu-id="e6cdd-287">实现基于任务的异步模式</span><span class="sxs-lookup"><span data-stu-id="e6cdd-287">Implementing the Task-based Asynchronous Pattern</span></span>](implementing-the-task-based-asynchronous-pattern.md)
- [<span data-ttu-id="e6cdd-288">与其他异步模式和类型互操作</span><span class="sxs-lookup"><span data-stu-id="e6cdd-288">Interop with Other Asynchronous Patterns and Types</span></span>](interop-with-other-asynchronous-patterns-and-types.md)

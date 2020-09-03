---
title: 异步文件访问 (C#)
description: 了解如何使用异步功能访问 C# 文件。 可以调用异步方法而无需使用回调，也不需要跨方法拆分代码。
ms.date: 08/19/2020
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: 9a8db6004e8fff2cb39f0c350b403b56ea619e54
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812037"
---
# <a name="asynchronous-file-access-c"></a><span data-ttu-id="4f2cf-104">异步文件访问 (C#)</span><span class="sxs-lookup"><span data-stu-id="4f2cf-104">Asynchronous file access (C#)</span></span>

<span data-ttu-id="4f2cf-105">可使用异步功能访问文件。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-105">You can use the async feature to access files.</span></span> <span data-ttu-id="4f2cf-106">通过使用异步功能，你可以调用异步方法而无需使用回调，也不需要跨多个方法或 lambda 表达式来拆分代码。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-106">By using the async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="4f2cf-107">若要使同步代码异步，只需调用异步方法而非同步方法，并向代码中添加几个关键字。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-107">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>

<span data-ttu-id="4f2cf-108">可能出于以下原因向文件访问调用中添加异步：</span><span class="sxs-lookup"><span data-stu-id="4f2cf-108">You might consider the following reasons for adding asynchrony to file access calls:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="4f2cf-109">异步使 UI 应用程序响应速度更快，因为启动该操作的 UI 线程可以执行其他操作。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-109">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="4f2cf-110">如果 UI 线程必须执行耗时较长的代码（例如超过 50 毫秒），UI 可能会冻结，直到 I/O 完成，此时 UI 线程可以再次处理键盘和鼠标输入及其他事件。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-110">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>
> - <span data-ttu-id="4f2cf-111">异步可减少对线程的需要，进而提高 ASP.NET 和其他基于服务器的应用程序的可伸缩性。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-111">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="4f2cf-112">如果应用程序对每次响应都使用专用线程，同时处理 1000 个请求时，则需要 1000 个线程。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-112">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="4f2cf-113">异步操作在等待期间通常不需要使用线程。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-113">Asynchronous operations often don't need to use a thread during the wait.</span></span> <span data-ttu-id="4f2cf-114">异步操作仅需在结束时短暂使用现有 I/O 完成线程。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-114">They use the existing I/O completion thread briefly at the end.</span></span>
> - <span data-ttu-id="4f2cf-115">当前条件下，文件访问操作的延迟可能非常低，但以后可能大幅增加。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-115">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="4f2cf-116">例如，文件可能会移动到覆盖全球的服务器。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-116">For example, a file may be moved to a server that's across the world.</span></span>
> - <span data-ttu-id="4f2cf-117">使用异步功能所增加的开销很小。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-117">The added overhead of using the Async feature is small.</span></span>
> - <span data-ttu-id="4f2cf-118">异步任务可以轻松地并行运行。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-118">Asynchronous tasks can easily be run in parallel.</span></span>

## <a name="use-appropriate-classes"></a><span data-ttu-id="4f2cf-119">使用适当的类</span><span class="sxs-lookup"><span data-stu-id="4f2cf-119">Use appropriate classes</span></span>

<span data-ttu-id="4f2cf-120">本主题中的简单示例演示 <xref:System.IO.File.WriteAllTextAsync%2A?displayProperty=nameWithType> 和 <xref:System.IO.File.ReadAllTextAsync%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-120">The simple examples in this topic demonstrate <xref:System.IO.File.WriteAllTextAsync%2A?displayProperty=nameWithType> and <xref:System.IO.File.ReadAllTextAsync%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4f2cf-121">要对文件 I/O 操作进行有限的控制，请使用 <xref:System.IO.FileStream> 类，该类有一个可导致在操作系统级别出现异步 I/O 的选项。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-121">For finite control over the file I/O operations, use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="4f2cf-122">使用此选项可避免在许多情况下阻止线程池线程。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-122">By using this option, you can avoid blocking a thread pool thread in many cases.</span></span> <span data-ttu-id="4f2cf-123">若要启用此选项，可在构造函数调用中指定 `useAsync=true` 或 `options=FileOptions.Asynchronous` 参数。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-123">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>

<span data-ttu-id="4f2cf-124">如果通过指定文件路径直接打开 <xref:System.IO.StreamReader> 和 <xref:System.IO.StreamWriter>，则无法将此选项与这二者配合使用。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-124">You can't use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="4f2cf-125">但是，如果为二者提供已由 <xref:System.IO.FileStream> 类打开的 <xref:System.IO.Stream>，则可以使用此选项。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-125">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="4f2cf-126">即使线程池线程受到阻止，UI 应用中的异步调用也会更快，因为 UI 线程在等待期间不会受到阻止。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-126">Asynchronous calls are faster in UI apps even if a thread pool thread is blocked, because the UI thread isn't blocked during the wait.</span></span>

## <a name="write-text"></a><span data-ttu-id="4f2cf-127">写入文本</span><span class="sxs-lookup"><span data-stu-id="4f2cf-127">Write text</span></span>

<span data-ttu-id="4f2cf-128">下面的示例将文本写入文件。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-128">The following examples write text to a file.</span></span> <span data-ttu-id="4f2cf-129">在每个 await 语句中，该方法会立即退出。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-129">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="4f2cf-130">文件 I/O 完成后，该方法将在 await 语句后面的语句中继续。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-130">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="4f2cf-131">Async 修饰符位于使用 await 语句的方法定义中。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-131">The async modifier is in the definition of methods that use the await statement.</span></span>

### <a name="simple-example"></a><span data-ttu-id="4f2cf-132">简单示例</span><span class="sxs-lookup"><span data-stu-id="4f2cf-132">Simple example</span></span>

:::code language="csharp" source="snippets/file-access/Program.cs" id="SimpleWrite":::

### <a name="finite-control-example"></a><span data-ttu-id="4f2cf-133">有限控制示例</span><span class="sxs-lookup"><span data-stu-id="4f2cf-133">Finite control example</span></span>

:::code language="csharp" source="snippets/file-access/Program.cs" id="WriteText":::

<span data-ttu-id="4f2cf-134">原始示例包含 `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);` 语句，它是下面两个语句的缩写式：</span><span class="sxs-lookup"><span data-stu-id="4f2cf-134">The original example has the statement `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, which is a contraction of the following two statements:</span></span>

```csharp
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);
await theTask;
```

<span data-ttu-id="4f2cf-135">第一条语句返回任务，并会导致文件处理启动。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-135">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="4f2cf-136">具有 await 的第二条语句将使方法立即退出并返回一个不同的任务。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-136">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="4f2cf-137">文件处理稍后完成后，执行将返回到 await 后面的语句中。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-137">When the file processing later completes, execution returns to the statement that follows the await.</span></span>

## <a name="read-text"></a><span data-ttu-id="4f2cf-138">读取文本</span><span class="sxs-lookup"><span data-stu-id="4f2cf-138">Read text</span></span>

<span data-ttu-id="4f2cf-139">下面的示例从文件中读取文本。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-139">The following examples read text from a file.</span></span>

### <a name="simple-example"></a><span data-ttu-id="4f2cf-140">简单示例</span><span class="sxs-lookup"><span data-stu-id="4f2cf-140">Simple example</span></span>

:::code language="csharp" source="snippets/file-access/Program.cs" id="SimpleRead":::

### <a name="finite-control-example"></a><span data-ttu-id="4f2cf-141">有限控制示例</span><span class="sxs-lookup"><span data-stu-id="4f2cf-141">Finite control example</span></span>

<span data-ttu-id="4f2cf-142">将会缓冲文本，并且在此情况下，会将其放入 <xref:System.Text.StringBuilder>。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-142">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="4f2cf-143">与前一示例不同，await 的计算将生成一个值。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-143">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="4f2cf-144"><xref:System.IO.Stream.ReadAsync%2A> 方法返回 <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>，因此在操作完成后 await 的评估会得出 `Int32` 值 `numRead`。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-144">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value `numRead` after the operation completes.</span></span> <span data-ttu-id="4f2cf-145">有关详细信息，请参阅[异步返回类型 (C#)](async-return-types.md)。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-145">For more information, see [Async Return Types (C#)](async-return-types.md).</span></span>

:::code language="csharp" source="snippets/file-access/Program.cs" id="ReadText":::

## <a name="parallel-asynchronous-io"></a><span data-ttu-id="4f2cf-146">并行异步 I/O</span><span class="sxs-lookup"><span data-stu-id="4f2cf-146">Parallel asynchronous I/O</span></span>

<span data-ttu-id="4f2cf-147">下面的示例通过编写 10 个文本文件来演示并行处理。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-147">The following examples demonstrate parallel processing by writing 10 text files.</span></span>

### <a name="simple-example"></a><span data-ttu-id="4f2cf-148">简单示例</span><span class="sxs-lookup"><span data-stu-id="4f2cf-148">Simple example</span></span>

:::code language="csharp" source="snippets/file-access/Program.cs" id="SimpleParallelWrite":::

### <a name="finite-control-example"></a><span data-ttu-id="4f2cf-149">有限控制示例</span><span class="sxs-lookup"><span data-stu-id="4f2cf-149">Finite control example</span></span>

<span data-ttu-id="4f2cf-150">对于每个文件，<xref:System.IO.Stream.WriteAsync%2A> 方法将返回一个任务，此任务随后将添加到任务列表中。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-150">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="4f2cf-151">`await Task.WhenAll(tasks);` 语句将退出该方法，并在所有任务的文件处理完成时在此方法中继续。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-151">The `await Task.WhenAll(tasks);` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>

<span data-ttu-id="4f2cf-152">该示例将在任务完成后关闭 `finally` 块中的所有 <xref:System.IO.FileStream> 实例。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-152">The example closes all <xref:System.IO.FileStream> instances in a `finally` block after the tasks are complete.</span></span> <span data-ttu-id="4f2cf-153">如果每个 `FileStream` 均已在 `using` 语句中创建，则可能在任务完成前释放 `FileStream`。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-153">If each `FileStream` was instead created in a `using` statement, the `FileStream` might be disposed of before the task was complete.</span></span>

<span data-ttu-id="4f2cf-154">任何性能提升都几乎完全来自并行处理而不是异步处理。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-154">Any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="4f2cf-155">异步的优点在于它不会占用多个线程，也不会占用用户界面线程。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-155">The advantages of asynchrony are that it doesn't tie up multiple threads, and that it doesn't tie up the user interface thread.</span></span>

:::code language="csharp" source="snippets/file-access/Program.cs" id="ParallelWriteText":::

<span data-ttu-id="4f2cf-156">当使用 <xref:System.IO.Stream.WriteAsync%2A> 和 <xref:System.IO.Stream.ReadAsync%2A> 方法时，可以指定可用于取消操作中间流的 <xref:System.Threading.CancellationToken>。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-156">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="4f2cf-157">有关详细信息，请参阅[托管线程中的取消](../../../../standard/threading/cancellation-in-managed-threads.md)。</span><span class="sxs-lookup"><span data-stu-id="4f2cf-157">For more information, see [Cancellation in managed threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4f2cf-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4f2cf-158">See also</span></span>

- [<span data-ttu-id="4f2cf-159">使用 Async 和 Await 的异步编程 (C#)</span><span class="sxs-lookup"><span data-stu-id="4f2cf-159">Asynchronous programming with async and await (C#)</span></span>](index.md)
- [<span data-ttu-id="4f2cf-160">异步返回类型 (C#)</span><span class="sxs-lookup"><span data-stu-id="4f2cf-160">Async return types (C#)</span></span>](async-return-types.md)

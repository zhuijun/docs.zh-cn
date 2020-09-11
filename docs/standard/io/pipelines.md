---
title: I/O 管道 - .NET
description: 了解如何在 .NET 中有效地使用 I/O 管道，并避免在代码中出现问题。
ms.date: 08/27/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- Pipelines
- Pipelines I/O
- I/O [.NET], Pipelines
author: rick-anderson
ms.author: riande
ms.openlocfilehash: a24d7f5c22c936cd3fd3fdc51f0f3ace56386574
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271979"
---
# <a name="systemiopipelines-in-net"></a><span data-ttu-id="6b09d-103">.NET 中的 System.IO.Pipelines</span><span class="sxs-lookup"><span data-stu-id="6b09d-103">System.IO.Pipelines in .NET</span></span>

<span data-ttu-id="6b09d-104"><xref:System.IO.Pipelines> 是一个新库，旨在使在 .NET 中执行高性能 I/O 更加容易。</span><span class="sxs-lookup"><span data-stu-id="6b09d-104"><xref:System.IO.Pipelines> is a new library that is designed to make it easier to do high-performance I/O in .NET.</span></span> <span data-ttu-id="6b09d-105">该库的目标为适用于所有 .NET 实现的 .NET Standard。</span><span class="sxs-lookup"><span data-stu-id="6b09d-105">It's a library targeting .NET Standard that works on all .NET implementations.</span></span>

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a><span data-ttu-id="6b09d-106">System.IO.Pipelines 解决什么问题</span><span class="sxs-lookup"><span data-stu-id="6b09d-106">What problem does System.IO.Pipelines solve</span></span>

<!-- corner case doesn't MT (machine translate)   -->
<span data-ttu-id="6b09d-107">分析流数据的应用由样板代码组成，后者由许多专门且不寻常的代码流组成。</span><span class="sxs-lookup"><span data-stu-id="6b09d-107">Apps that parse streaming data are composed of boilerplate code having many specialized and unusual code flows.</span></span> <span data-ttu-id="6b09d-108">样板代码和特殊情况代码很复杂且难以进行维护。</span><span class="sxs-lookup"><span data-stu-id="6b09d-108">The boilerplate and special case code is complex and difficult to maintain.</span></span>

<span data-ttu-id="6b09d-109">`System.IO.Pipelines` 已构建为：</span><span class="sxs-lookup"><span data-stu-id="6b09d-109">`System.IO.Pipelines` was architected to:</span></span>

* <span data-ttu-id="6b09d-110">具有高性能的流数据分析功能。</span><span class="sxs-lookup"><span data-stu-id="6b09d-110">Have high performance parsing streaming data.</span></span>
* <span data-ttu-id="6b09d-111">减少代码复杂性。</span><span class="sxs-lookup"><span data-stu-id="6b09d-111">Reduce code complexity.</span></span>

<span data-ttu-id="6b09d-112">下面的代码是典型的 TCP 服务器，它从客户机接收行分隔的消息（由 `'\n'` 分隔）：</span><span class="sxs-lookup"><span data-stu-id="6b09d-112">The following code is typical for a TCP server that receives line-delimited messages (delimited by `'\n'`) from a client:</span></span>

```csharp
async Task ProcessLinesAsync(NetworkStream stream)
{
    var buffer = new byte[1024];
    await stream.ReadAsync(buffer, 0, buffer.Length);

    // Process a single line from the buffer
    ProcessLine(buffer);
}
```

<span data-ttu-id="6b09d-113">前面的代码有几个问题：</span><span class="sxs-lookup"><span data-stu-id="6b09d-113">The preceding code has several problems:</span></span>

* <span data-ttu-id="6b09d-114">单次调用 `ReadAsync` 可能无法接收整条消息（行尾）。</span><span class="sxs-lookup"><span data-stu-id="6b09d-114">The entire message (end of line) might not be received in a single call to `ReadAsync`.</span></span>
* <span data-ttu-id="6b09d-115">忽略了 `stream.ReadAsync` 的结果。</span><span class="sxs-lookup"><span data-stu-id="6b09d-115">It's ignoring the result of `stream.ReadAsync`.</span></span> <span data-ttu-id="6b09d-116">`stream.ReadAsync` 返回读取的数据量。</span><span class="sxs-lookup"><span data-stu-id="6b09d-116">`stream.ReadAsync` returns how much data was read.</span></span>
* <span data-ttu-id="6b09d-117">它不能处理在单个 `ReadAsync` 调用中读取多行的情况。</span><span class="sxs-lookup"><span data-stu-id="6b09d-117">It doesn't handle the case where multiple lines are read in a single `ReadAsync` call.</span></span>
* <span data-ttu-id="6b09d-118">它为每次读取分配一个 `byte` 数组。</span><span class="sxs-lookup"><span data-stu-id="6b09d-118">It allocates a `byte` array with each read.</span></span>

<span data-ttu-id="6b09d-119">要解决上述问题，需要进行以下更改：</span><span class="sxs-lookup"><span data-stu-id="6b09d-119">To fix the preceding problems, the following changes are required:</span></span>

* <span data-ttu-id="6b09d-120">缓冲传入的数据，直到找到新行。</span><span class="sxs-lookup"><span data-stu-id="6b09d-120">Buffer the incoming data until a new line is found.</span></span>
* <span data-ttu-id="6b09d-121">分析缓冲区中返回的所有行。</span><span class="sxs-lookup"><span data-stu-id="6b09d-121">Parse all the lines returned in the buffer.</span></span>
* <span data-ttu-id="6b09d-122">该行可能大于 1KB（1024 字节）。</span><span class="sxs-lookup"><span data-stu-id="6b09d-122">It's possible that the line is bigger than 1 KB (1024 bytes).</span></span> <span data-ttu-id="6b09d-123">此代码需要调整输入缓冲区的大小，直到找到分隔符后，才能在缓冲区内容纳完整行。</span><span class="sxs-lookup"><span data-stu-id="6b09d-123">The code needs to resize the input buffer until the delimiter is found in order to fit the complete line inside the buffer.</span></span>

  * <span data-ttu-id="6b09d-124">如果调整缓冲区的大小，当输入中出现较长的行时，将生成更多缓冲区副本。</span><span class="sxs-lookup"><span data-stu-id="6b09d-124">If the buffer is resized, more buffer copies are made as longer lines appear in the input.</span></span>
  * <span data-ttu-id="6b09d-125">压缩用于读取行的缓冲区，以减少空余。</span><span class="sxs-lookup"><span data-stu-id="6b09d-125">To reduce wasted space, compact the buffer used for reading lines.</span></span>

* <span data-ttu-id="6b09d-126">请考虑使用缓冲池来避免重复分配内存。</span><span class="sxs-lookup"><span data-stu-id="6b09d-126">Consider using buffer pooling to avoid allocating memory repeatedly.</span></span>
* <span data-ttu-id="6b09d-127">下面的代码解决了其中一些问题：</span><span class="sxs-lookup"><span data-stu-id="6b09d-127">The following code addresses some of these problems:</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs" id="snippet":::

<span data-ttu-id="6b09d-128">前面的代码很复杂，不能解决所识别的所有问题。</span><span class="sxs-lookup"><span data-stu-id="6b09d-128">The previous code is complex and doesn't address all the problems identified.</span></span> <span data-ttu-id="6b09d-129">高性能网络通常意味着编写非常复杂的代码以使性能最大化。</span><span class="sxs-lookup"><span data-stu-id="6b09d-129">High-performance networking usually means writing very complex code to maximize performance.</span></span> <span data-ttu-id="6b09d-130">`System.IO.Pipelines` 的设计目的是使编写此类代码更容易。</span><span class="sxs-lookup"><span data-stu-id="6b09d-130">`System.IO.Pipelines` was designed to make writing this type of code easier.</span></span>

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="pipe"></a><span data-ttu-id="6b09d-131">管道</span><span class="sxs-lookup"><span data-stu-id="6b09d-131">Pipe</span></span>

<span data-ttu-id="6b09d-132"><xref:System.IO.Pipelines.Pipe> 类可用于创建 `PipeWriter/PipeReader` 对。</span><span class="sxs-lookup"><span data-stu-id="6b09d-132">The <xref:System.IO.Pipelines.Pipe> class can be used to create a `PipeWriter/PipeReader` pair.</span></span> <span data-ttu-id="6b09d-133">写入 `PipeWriter` 的所有数据都可用于 `PipeReader`：</span><span class="sxs-lookup"><span data-stu-id="6b09d-133">All data written into the `PipeWriter` is available in the `PipeReader`:</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/Pipe.cs" id="snippet2":::

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a><span data-ttu-id="6b09d-134">管道基本用法</span><span class="sxs-lookup"><span data-stu-id="6b09d-134">Pipe basic usage</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/Pipe.cs" id="snippet":::

<span data-ttu-id="6b09d-135">有两个循环：</span><span class="sxs-lookup"><span data-stu-id="6b09d-135">There are two loops:</span></span>

* <span data-ttu-id="6b09d-136">`FillPipeAsync` 从 `Socket` 读取并写入 `PipeWriter`。</span><span class="sxs-lookup"><span data-stu-id="6b09d-136">`FillPipeAsync` reads from the `Socket` and writes to the `PipeWriter`.</span></span>
* <span data-ttu-id="6b09d-137">`ReadPipeAsync` 从 `PipeReader` 读取并分析传入的行。</span><span class="sxs-lookup"><span data-stu-id="6b09d-137">`ReadPipeAsync` reads from the `PipeReader` and parses incoming lines.</span></span>

<span data-ttu-id="6b09d-138">没有分配显式缓冲区。</span><span class="sxs-lookup"><span data-stu-id="6b09d-138">There are no explicit buffers allocated.</span></span> <span data-ttu-id="6b09d-139">所有缓冲区管理都委托给 `PipeReader` 和 `PipeWriter` 实现。</span><span class="sxs-lookup"><span data-stu-id="6b09d-139">All buffer management is delegated to the `PipeReader` and `PipeWriter` implementations.</span></span> <span data-ttu-id="6b09d-140">委派缓冲区管理使使用代码更容易集中关注业务逻辑。</span><span class="sxs-lookup"><span data-stu-id="6b09d-140">Delegating buffer management makes it easier for consuming code to focus solely on the business logic.</span></span>

<span data-ttu-id="6b09d-141">在第一个循环中：</span><span class="sxs-lookup"><span data-stu-id="6b09d-141">In the first loop:</span></span>

* <span data-ttu-id="6b09d-142">调用 <xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> 从基础编写器获取内存。</span><span class="sxs-lookup"><span data-stu-id="6b09d-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> is called to get memory from the underlying writer.</span></span>
* <span data-ttu-id="6b09d-143">调用 <xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> 以告知 `PipeWriter` 有多少数据已写入缓冲区。</span><span class="sxs-lookup"><span data-stu-id="6b09d-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> is called to tell the `PipeWriter` how much data was written to the buffer.</span></span>
* <span data-ttu-id="6b09d-144">调用 <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> 以使数据可用于 `PipeReader`。</span><span class="sxs-lookup"><span data-stu-id="6b09d-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> is called to make the data available to the `PipeReader`.</span></span>

<span data-ttu-id="6b09d-145">在第二个循环中，`PipeReader` 使用由 `PipeWriter` 写入的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="6b09d-145">In the second loop, the `PipeReader` consumes the buffers written by `PipeWriter`.</span></span> <span data-ttu-id="6b09d-146">缓冲区来自套接字。</span><span class="sxs-lookup"><span data-stu-id="6b09d-146">The buffers come from the socket.</span></span> <span data-ttu-id="6b09d-147">对 `PipeReader.ReadAsync` 的调用：</span><span class="sxs-lookup"><span data-stu-id="6b09d-147">The call to `PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="6b09d-148">返回包含两条重要信息的 <xref:System.IO.Pipelines.ReadResult>：</span><span class="sxs-lookup"><span data-stu-id="6b09d-148">Returns a <xref:System.IO.Pipelines.ReadResult> that contains two important pieces of information:</span></span>

  * <span data-ttu-id="6b09d-149">以 `ReadOnlySequence<byte>` 形式读取的数据。</span><span class="sxs-lookup"><span data-stu-id="6b09d-149">The data that was read in the form of `ReadOnlySequence<byte>`.</span></span>
  * <span data-ttu-id="6b09d-150">布尔值 `IsCompleted`，指示是否已到达数据结尾 (EOF)。</span><span class="sxs-lookup"><span data-stu-id="6b09d-150">A boolean `IsCompleted` that indicates if the end of data (EOF) has been reached.</span></span>

<span data-ttu-id="6b09d-151">找到行尾 (EOL) 分隔符并分析该行后：</span><span class="sxs-lookup"><span data-stu-id="6b09d-151">After finding the end of line (EOL) delimiter and parsing the line:</span></span>

* <span data-ttu-id="6b09d-152">该逻辑处理缓冲区以跳过已处理的内容。</span><span class="sxs-lookup"><span data-stu-id="6b09d-152">The logic processes the buffer to skip what's already processed.</span></span>
* <span data-ttu-id="6b09d-153">调用 `PipeReader.AdvanceTo` 以告知 `PipeReader` 已消耗和检查了多少数据。</span><span class="sxs-lookup"><span data-stu-id="6b09d-153">`PipeReader.AdvanceTo` is called to tell the `PipeReader` how much data has been consumed and examined.</span></span>

<span data-ttu-id="6b09d-154">读取器和编写器循环通过调用 `Complete` 结束。</span><span class="sxs-lookup"><span data-stu-id="6b09d-154">The reader and writer loops end by calling `Complete`.</span></span> <span data-ttu-id="6b09d-155">`Complete` 使基础管道释放其分配的内存。</span><span class="sxs-lookup"><span data-stu-id="6b09d-155">`Complete` lets the underlying Pipe release the memory it allocated.</span></span>

### <a name="backpressure-and-flow-control"></a><span data-ttu-id="6b09d-156">反压和流量控制</span><span class="sxs-lookup"><span data-stu-id="6b09d-156">Backpressure and flow control</span></span>

<span data-ttu-id="6b09d-157">理想情况下，读取和分析可协同工作：</span><span class="sxs-lookup"><span data-stu-id="6b09d-157">Ideally, reading and parsing work together:</span></span>

* <span data-ttu-id="6b09d-158">写入线程使用来自网络的数据并将其放入缓冲区。</span><span class="sxs-lookup"><span data-stu-id="6b09d-158">The writing thread consumes data from the network and puts it in buffers.</span></span>
* <span data-ttu-id="6b09d-159">分析线程负责构造适当的数据结构。</span><span class="sxs-lookup"><span data-stu-id="6b09d-159">The parsing thread is responsible for constructing the appropriate data structures.</span></span>

<span data-ttu-id="6b09d-160">通常，分析所花费的时间比仅从网络复制数据块所用时间更长：</span><span class="sxs-lookup"><span data-stu-id="6b09d-160">Typically, parsing takes more time than just copying blocks of data from the network:</span></span>

* <span data-ttu-id="6b09d-161">读取线程领先于分析线程。</span><span class="sxs-lookup"><span data-stu-id="6b09d-161">The reading thread gets ahead of the parsing thread.</span></span>
* <span data-ttu-id="6b09d-162">读取线程必须减缓或分配更多内存来存储用于分析线程的数据。</span><span class="sxs-lookup"><span data-stu-id="6b09d-162">The reading thread has to either slow down or allocate more memory to store the data for the parsing thread.</span></span>

<span data-ttu-id="6b09d-163">为了获得最佳性能，需要在频繁暂停和分配更多内存之间取得平衡。</span><span class="sxs-lookup"><span data-stu-id="6b09d-163">For optimal performance, there's a balance between frequent pauses and allocating more memory.</span></span>

<span data-ttu-id="6b09d-164">为解决上述问题，`Pipe` 提供了两个设置来控制数据流：</span><span class="sxs-lookup"><span data-stu-id="6b09d-164">To solve the preceding problem, the `Pipe` has two settings to control the flow of data:</span></span>

* <span data-ttu-id="6b09d-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>：确定在调用 <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> 暂停之前应缓冲多少数据。</span><span class="sxs-lookup"><span data-stu-id="6b09d-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Determines how much data should be buffered before calls to <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> pause.</span></span>
* <span data-ttu-id="6b09d-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>：确定在恢复对 `PipeWriter.FlushAsync` 的调用之前，读取器必须观察多少数据。</span><span class="sxs-lookup"><span data-stu-id="6b09d-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Determines how much data the reader has to observe before calls to `PipeWriter.FlushAsync` resume.</span></span>

![具有 ResumeWriterThreshold 和 PauseWriterThreshold 的图](media/pipelines/resume-pause.png)

<span data-ttu-id="6b09d-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>：</span><span class="sxs-lookup"><span data-stu-id="6b09d-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="6b09d-169">当 `Pipe` 中的数据量超过 `PauseWriterThreshold` 时，返回不完整的 `ValueTask<FlushResult>`。</span><span class="sxs-lookup"><span data-stu-id="6b09d-169">Returns an incomplete `ValueTask<FlushResult>` when the amount of data in the `Pipe` crosses `PauseWriterThreshold`.</span></span>
* <span data-ttu-id="6b09d-170">低于 `ResumeWriterThreshold` 时，返回完整的 `ValueTask<FlushResult>`。</span><span class="sxs-lookup"><span data-stu-id="6b09d-170">Completes `ValueTask<FlushResult>` when it becomes lower than `ResumeWriterThreshold`.</span></span>

<span data-ttu-id="6b09d-171">使用两个值可防止快速循环，如果只使用一个值，则可能发生这种循环。</span><span class="sxs-lookup"><span data-stu-id="6b09d-171">Two values are used to prevent rapid cycling, which can occur if one value is used.</span></span>

### <a name="examples"></a><span data-ttu-id="6b09d-172">示例</span><span class="sxs-lookup"><span data-stu-id="6b09d-172">Examples</span></span>

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a><span data-ttu-id="6b09d-173">PipeScheduler</span><span class="sxs-lookup"><span data-stu-id="6b09d-173">PipeScheduler</span></span>

<span data-ttu-id="6b09d-174">通常在使用 `async` 和 `await` 时，异步代码会在 <xref:System.Threading.Tasks.TaskScheduler> 或当前 <xref:System.Threading.SynchronizationContext> 上恢复。</span><span class="sxs-lookup"><span data-stu-id="6b09d-174">Typically when using `async` and `await`, asynchronous code resumes on either on a <xref:System.Threading.Tasks.TaskScheduler> or on the current <xref:System.Threading.SynchronizationContext>.</span></span>

<span data-ttu-id="6b09d-175">在执行 I/O 时，对执行 I/O 的位置进行细粒度控制非常重要。</span><span class="sxs-lookup"><span data-stu-id="6b09d-175">When doing I/O, it's important to have fine-grained control over where the I/O is performed.</span></span> <span data-ttu-id="6b09d-176">此控件允许高效利用 CPU 缓存。</span><span class="sxs-lookup"><span data-stu-id="6b09d-176">This control allows taking advantage of CPU caches effectively.</span></span> <span data-ttu-id="6b09d-177">高效的缓存对于 Web 服务器等高性能应用至关重要。</span><span class="sxs-lookup"><span data-stu-id="6b09d-177">Efficient caching is critical for high-performance apps like web servers.</span></span> <span data-ttu-id="6b09d-178"><xref:System.IO.Pipelines.PipeScheduler> 提供对异步回调运行位置的控制。</span><span class="sxs-lookup"><span data-stu-id="6b09d-178"><xref:System.IO.Pipelines.PipeScheduler> provides control over where asynchronous callbacks run.</span></span> <span data-ttu-id="6b09d-179">默认情况下：</span><span class="sxs-lookup"><span data-stu-id="6b09d-179">By default:</span></span>

* <span data-ttu-id="6b09d-180">使用当前的 <xref:System.Threading.SynchronizationContext>。</span><span class="sxs-lookup"><span data-stu-id="6b09d-180">The current <xref:System.Threading.SynchronizationContext> is used.</span></span>
* <span data-ttu-id="6b09d-181">如果没有 `SynchronizationContext`，它将使用线程池运行回调。</span><span class="sxs-lookup"><span data-stu-id="6b09d-181">If there's no `SynchronizationContext`, it uses the thread pool to run callbacks.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/Program.cs" id="snippet":::

<span data-ttu-id="6b09d-182">[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) 是 <xref:System.IO.Pipelines.PipeScheduler> 实现，用于对线程池的回调进行排队。</span><span class="sxs-lookup"><span data-stu-id="6b09d-182">[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) is the <xref:System.IO.Pipelines.PipeScheduler> implementation that queues callbacks to the thread pool.</span></span> <span data-ttu-id="6b09d-183">`PipeScheduler.ThreadPool` 是默认选项，通常也是最佳选项。</span><span class="sxs-lookup"><span data-stu-id="6b09d-183">`PipeScheduler.ThreadPool` is the default and generally the best choice.</span></span> <span data-ttu-id="6b09d-184">[PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) 可能会导致意外后果，如死锁。</span><span class="sxs-lookup"><span data-stu-id="6b09d-184">[PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) can cause unintended consequences such as deadlocks.</span></span>

### <a name="pipe-reset"></a><span data-ttu-id="6b09d-185">管道重置</span><span class="sxs-lookup"><span data-stu-id="6b09d-185">Pipe reset</span></span>

<span data-ttu-id="6b09d-186">通常重用 `Pipe` 对象即可重置。</span><span class="sxs-lookup"><span data-stu-id="6b09d-186">It's frequently efficient to reuse the `Pipe` object.</span></span> <span data-ttu-id="6b09d-187">若要重置管道，请在 `PipeReader` 和 `PipeWriter` 完成时调用 <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A>。</span><span class="sxs-lookup"><span data-stu-id="6b09d-187">To reset the pipe, call <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> when both the `PipeReader` and `PipeWriter` are complete.</span></span>

## <a name="pipereader"></a><span data-ttu-id="6b09d-188">PipeReader</span><span class="sxs-lookup"><span data-stu-id="6b09d-188">PipeReader</span></span>

<span data-ttu-id="6b09d-189"><xref:System.IO.Pipelines.PipeReader> 代表调用方管理内存。</span><span class="sxs-lookup"><span data-stu-id="6b09d-189"><xref:System.IO.Pipelines.PipeReader> manages memory on the caller's behalf.</span></span> <span data-ttu-id="6b09d-190">在调用 <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType> 之后始终调用 <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType>  。</span><span class="sxs-lookup"><span data-stu-id="6b09d-190">**Always** call <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> after calling <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6b09d-191">这使 `PipeReader` 知道调用方何时用完内存，以便可以对其进行跟踪。</span><span class="sxs-lookup"><span data-stu-id="6b09d-191">This lets the `PipeReader` know when the caller is done with the memory so that it can be tracked.</span></span> <span data-ttu-id="6b09d-192">从 `PipeReader.ReadAsync` 返回的 `ReadOnlySequence<byte>` 仅在调用 `PipeReader.AdvanceTo` 之前有效。</span><span class="sxs-lookup"><span data-stu-id="6b09d-192">The `ReadOnlySequence<byte>` returned from `PipeReader.ReadAsync` is only valid until the call the `PipeReader.AdvanceTo`.</span></span> <span data-ttu-id="6b09d-193">调用 `PipeReader.AdvanceTo` 后，不能使用 `ReadOnlySequence<byte>`。</span><span class="sxs-lookup"><span data-stu-id="6b09d-193">It's illegal to use `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo`.</span></span>

<span data-ttu-id="6b09d-194">`PipeReader.AdvanceTo` 采用两个 <xref:System.SequencePosition> 参数：</span><span class="sxs-lookup"><span data-stu-id="6b09d-194">`PipeReader.AdvanceTo` takes two <xref:System.SequencePosition> arguments:</span></span>

* <span data-ttu-id="6b09d-195">第一个参数确定消耗的内存量。</span><span class="sxs-lookup"><span data-stu-id="6b09d-195">The first argument determines how much memory was consumed.</span></span>
* <span data-ttu-id="6b09d-196">第二个参数确定观察到的缓冲区数。</span><span class="sxs-lookup"><span data-stu-id="6b09d-196">The second argument determines how much of the buffer was observed.</span></span>

<span data-ttu-id="6b09d-197">将数据标记为“已使用”意味着管道可以将内存返回到底层缓冲池。</span><span class="sxs-lookup"><span data-stu-id="6b09d-197">Marking data as consumed means that the pipe can return the memory to the underlying buffer pool.</span></span> <span data-ttu-id="6b09d-198">将数据标记为“已观察”可控制对 `PipeReader.ReadAsync` 的下一个调用的操作。</span><span class="sxs-lookup"><span data-stu-id="6b09d-198">Marking data as observed controls what the next call to `PipeReader.ReadAsync` does.</span></span> <span data-ttu-id="6b09d-199">将所有内容都标记为“已观察”意味着下次对 `PipeReader.ReadAsync` 的调用将不会返回，直到有更多数据写入管道。</span><span class="sxs-lookup"><span data-stu-id="6b09d-199">Marking everything as observed means that the next call to `PipeReader.ReadAsync` won't return until there's more data written to the pipe.</span></span> <span data-ttu-id="6b09d-200">任何其他值都将使对 `PipeReader.ReadAsync` 的下一次调用立即返回并包含已观察到的和未观察到的数据，但不是已被使用的数据  。</span><span class="sxs-lookup"><span data-stu-id="6b09d-200">Any other value will make the next call to `PipeReader.ReadAsync` return immediately with the observed *and* unobserved data, but not data that has already been consumed.</span></span>

### <a name="read-streaming-data-scenarios"></a><span data-ttu-id="6b09d-201">读取流数据方案</span><span class="sxs-lookup"><span data-stu-id="6b09d-201">Read streaming data scenarios</span></span>

<span data-ttu-id="6b09d-202">尝试读取流数据时会出现以下几种典型模式：</span><span class="sxs-lookup"><span data-stu-id="6b09d-202">There are a couple of typical patterns that emerge when trying to read streaming data:</span></span>

* <span data-ttu-id="6b09d-203">给定数据流时，分析单条消息。</span><span class="sxs-lookup"><span data-stu-id="6b09d-203">Given a stream of data, parse a single message.</span></span>
* <span data-ttu-id="6b09d-204">给定数据流时，分析所有可用消息。</span><span class="sxs-lookup"><span data-stu-id="6b09d-204">Given a stream of data, parse all available messages.</span></span>

<span data-ttu-id="6b09d-205">以下示例使用 `TryParseMessage` 方法分析来自 `ReadOnlySequence<byte>` 的消息。</span><span class="sxs-lookup"><span data-stu-id="6b09d-205">The following examples use the `TryParseMessage` method for parsing messages from a `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="6b09d-206">`TryParseMessage` 分析单条消息并更新输入缓冲区，以从缓冲区中剪裁已分析的消息。</span><span class="sxs-lookup"><span data-stu-id="6b09d-206">`TryParseMessage` parses a single message and update the input buffer to trim the parsed message from the buffer.</span></span> <span data-ttu-id="6b09d-207">`TryParseMessage` 不是 .NET 的一部分，它是在以下部分中使用的用户编写的方法。</span><span class="sxs-lookup"><span data-stu-id="6b09d-207">`TryParseMessage` is not part of .NET, it's a user written method used in the following sections.</span></span>

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a><span data-ttu-id="6b09d-208">读取单条消息</span><span class="sxs-lookup"><span data-stu-id="6b09d-208">Read a single message</span></span>

<span data-ttu-id="6b09d-209">下面的代码从 `PipeReader` 读取一条消息并将其返回给调用方。</span><span class="sxs-lookup"><span data-stu-id="6b09d-209">The following code reads a single message from a `PipeReader` and returns it to the caller.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs" id="snippet":::

<span data-ttu-id="6b09d-210">前面的代码：</span><span class="sxs-lookup"><span data-stu-id="6b09d-210">The preceding code:</span></span>

* <span data-ttu-id="6b09d-211">分析单条消息。</span><span class="sxs-lookup"><span data-stu-id="6b09d-211">Parses a single message.</span></span>
* <span data-ttu-id="6b09d-212">更新已使用的 `SequencePosition` 并检查 `SequencePosition` 以指向已剪裁的输入缓冲区的开始。</span><span class="sxs-lookup"><span data-stu-id="6b09d-212">Updates the consumed `SequencePosition` and examined `SequencePosition` to point to the start of the trimmed input buffer.</span></span>

<span data-ttu-id="6b09d-213">因为 `TryParseMessage` 从输入缓冲区中删除了已分析的消息，所以更新了两个 `SequencePosition` 参数。</span><span class="sxs-lookup"><span data-stu-id="6b09d-213">The two `SequencePosition` arguments are updated because `TryParseMessage` removes the parsed message from the input buffer.</span></span> <span data-ttu-id="6b09d-214">通常，分析来自缓冲区的单条消息时，检查的位置应为以下位置之一：</span><span class="sxs-lookup"><span data-stu-id="6b09d-214">Generally, when parsing a single message from the buffer, the examined position should be one of the following:</span></span>

* <span data-ttu-id="6b09d-215">消息的结尾。</span><span class="sxs-lookup"><span data-stu-id="6b09d-215">The end of the message.</span></span>
* <span data-ttu-id="6b09d-216">如果未找到消息，则返回接收缓冲区的结尾。</span><span class="sxs-lookup"><span data-stu-id="6b09d-216">The end of the received buffer if no message was found.</span></span>

<span data-ttu-id="6b09d-217">单条消息案例最有可能出现错误。</span><span class="sxs-lookup"><span data-stu-id="6b09d-217">The single message case has the most potential for errors.</span></span> <span data-ttu-id="6b09d-218">将错误的值传递给“已检查”可能会导致内存不足异常或无限循环  。</span><span class="sxs-lookup"><span data-stu-id="6b09d-218">Passing the wrong values to *examined* can result in an out of memory exception or an infinite loop.</span></span> <span data-ttu-id="6b09d-219">有关详细信息，请参阅本文中的 [PipeReader 常见问题](#gotchas)部分。</span><span class="sxs-lookup"><span data-stu-id="6b09d-219">For more information, see the [PipeReader common problems](#gotchas) section in this article.</span></span>

### <a name="reading-multiple-messages"></a><span data-ttu-id="6b09d-220">读取多条消息</span><span class="sxs-lookup"><span data-stu-id="6b09d-220">Reading multiple messages</span></span>

<span data-ttu-id="6b09d-221">以下代码从 `PipeReader` 读取所有消息，并在每条消息上调用 `ProcessMessageAsync`。</span><span class="sxs-lookup"><span data-stu-id="6b09d-221">The following code reads all messages from a `PipeReader` and calls `ProcessMessageAsync` on each.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyConnection1.cs" id="snippet":::

### <a name="cancellation"></a><span data-ttu-id="6b09d-222">取消</span><span class="sxs-lookup"><span data-stu-id="6b09d-222">Cancellation</span></span>

<span data-ttu-id="6b09d-223">`PipeReader.ReadAsync`：</span><span class="sxs-lookup"><span data-stu-id="6b09d-223">`PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="6b09d-224">支持传递 <xref:System.Threading.CancellationToken>。</span><span class="sxs-lookup"><span data-stu-id="6b09d-224">Supports passing a <xref:System.Threading.CancellationToken>.</span></span>
* <span data-ttu-id="6b09d-225">如果在读取挂起期间取消了 `CancellationToken`，则会引发 <xref:System.OperationCanceledException>。</span><span class="sxs-lookup"><span data-stu-id="6b09d-225">Throws an <xref:System.OperationCanceledException> if the `CancellationToken` is canceled while there's a read pending.</span></span>
* <span data-ttu-id="6b09d-226">支持通过 <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType> 取消当前读取操作的方法，这样可以避免引发异常。</span><span class="sxs-lookup"><span data-stu-id="6b09d-226">Supports a way to cancel the current read operation via <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>, which avoids raising an exception.</span></span> <span data-ttu-id="6b09d-227">调用 `PipeReader.CancelPendingRead` 将导致对 `PipeReader.ReadAsync` 的当前或下次调用返回 <xref:System.IO.Pipelines.ReadResult>，并将 `IsCanceled` 设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="6b09d-227">Calling `PipeReader.CancelPendingRead` causes the current or next call to `PipeReader.ReadAsync` to return a <xref:System.IO.Pipelines.ReadResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="6b09d-228">这对于以非破坏性和非异常的方式停止现有的读取循环非常有用。</span><span class="sxs-lookup"><span data-stu-id="6b09d-228">This can be useful for halting the existing read loop in a non-destructive and non-exceptional way.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyConnection.cs" id="snippet":::

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a><span data-ttu-id="6b09d-229">PipeReader 常见问题</span><span class="sxs-lookup"><span data-stu-id="6b09d-229">PipeReader common problems</span></span>

* <span data-ttu-id="6b09d-230">将错误的值传递给 `consumed` 或 `examined` 可能会导致读取已读取的数据。</span><span class="sxs-lookup"><span data-stu-id="6b09d-230">Passing the wrong values to `consumed` or `examined` may result in reading already read data.</span></span>
* <span data-ttu-id="6b09d-231">传递 `buffer.End` 作为检查对象可能会导致以下问题：</span><span class="sxs-lookup"><span data-stu-id="6b09d-231">Passing `buffer.End` as examined may result in:</span></span>

  * <span data-ttu-id="6b09d-232">数据停止</span><span class="sxs-lookup"><span data-stu-id="6b09d-232">Stalled data</span></span>
  * <span data-ttu-id="6b09d-233">如果数据未使用，可能最终会出现内存不足 (OOM) 异常。</span><span class="sxs-lookup"><span data-stu-id="6b09d-233">Possibly an eventual Out of Memory (OOM) exception if data isn't consumed.</span></span> <span data-ttu-id="6b09d-234">例如，当一次处理来自缓冲区的单条消息时，可能会出现 `PipeReader.AdvanceTo(position, buffer.End)`。</span><span class="sxs-lookup"><span data-stu-id="6b09d-234">For example, `PipeReader.AdvanceTo(position, buffer.End)` when processing a single message at a time from the buffer.</span></span>

* <span data-ttu-id="6b09d-235">将错误的值传递给 `consumed` 或 `examined` 可能会导致无限循环。</span><span class="sxs-lookup"><span data-stu-id="6b09d-235">Passing the wrong values to `consumed` or `examined` may result in an infinite loop.</span></span> <span data-ttu-id="6b09d-236">例如，如果 `buffer.Start` 没有更改，则 `PipeReader.AdvanceTo(buffer.Start)` 将导致在下一个对 `PipeReader.ReadAsync` 的调用在新数据到来之前立即返回。</span><span class="sxs-lookup"><span data-stu-id="6b09d-236">For example, `PipeReader.AdvanceTo(buffer.Start)` if `buffer.Start` hasn't changed will cause the next call to `PipeReader.ReadAsync` to return immediately before new data arrives.</span></span>
* <span data-ttu-id="6b09d-237">将错误的值传递给 `consumed` 或 `examined` 可能会导致无限缓冲（最终导致 OOM）。</span><span class="sxs-lookup"><span data-stu-id="6b09d-237">Passing the wrong values to `consumed` or `examined` may result in infinite buffering (eventual OOM).</span></span>
* <span data-ttu-id="6b09d-238">在调用 `PipeReader.AdvanceTo` 之后使用 `ReadOnlySequence<byte>` 可能会导致内存损坏（在释放之后使用）。</span><span class="sxs-lookup"><span data-stu-id="6b09d-238">Using the `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo` may result in memory corruption (use after free).</span></span>
* <span data-ttu-id="6b09d-239">未能调用 `PipeReader.Complete/CompleteAsync` 可能会导致内存泄漏。</span><span class="sxs-lookup"><span data-stu-id="6b09d-239">Failing to call `PipeReader.Complete/CompleteAsync` may result in a memory leak.</span></span>
* <span data-ttu-id="6b09d-240">在处理缓冲区之前检查 <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> 并退出读取逻辑会导致数据丢失。</span><span class="sxs-lookup"><span data-stu-id="6b09d-240">Checking <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> and exiting the reading logic before processing the buffer results in data loss.</span></span> <span data-ttu-id="6b09d-241">循环退出条件应基于 `ReadResult.Buffer.IsEmpty` 和 `ReadResult.IsCompleted`。</span><span class="sxs-lookup"><span data-stu-id="6b09d-241">The loop exit condition should be based on `ReadResult.Buffer.IsEmpty` and `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="6b09d-242">如果错误执行此操作，可能会导致无限循环。</span><span class="sxs-lookup"><span data-stu-id="6b09d-242">Doing this incorrectly could result in an infinite loop.</span></span>

#### <a name="problematic-code"></a><span data-ttu-id="6b09d-243">有问题的代码</span><span class="sxs-lookup"><span data-stu-id="6b09d-243">Problematic code</span></span>

<span data-ttu-id="6b09d-244">❌ **数据丢失**</span><span class="sxs-lookup"><span data-stu-id="6b09d-244">❌ **Data loss**</span></span>

<span data-ttu-id="6b09d-245">当 `IsCompleted` 被设置为 `true` 时，`ReadResult` 可能会返回最后一段数据。</span><span class="sxs-lookup"><span data-stu-id="6b09d-245">The `ReadResult` can return the final segment of data when `IsCompleted` is set to `true`.</span></span> <span data-ttu-id="6b09d-246">在退出读循环之前不读取该数据将导致数据丢失。</span><span class="sxs-lookup"><span data-stu-id="6b09d-246">Not reading that data before exiting the read loop will result in data loss.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="6b09d-247">❌ **无限循环**</span><span class="sxs-lookup"><span data-stu-id="6b09d-247">❌ **Infinite loop**</span></span>

<span data-ttu-id="6b09d-248">如果 `Result.IsCompleted` 是 `true`，则以下逻辑可能会导致无限循环，但缓冲区中永远不会有完整的消息。</span><span class="sxs-lookup"><span data-stu-id="6b09d-248">The following logic may result in an infinite loop if the `Result.IsCompleted` is `true` but there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet2":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="6b09d-249">下面是另一段具有相同问题的代码。</span><span class="sxs-lookup"><span data-stu-id="6b09d-249">Here's another piece of code with the same problem.</span></span> <span data-ttu-id="6b09d-250">该代码在检查 `ReadResult.IsCompleted` 之前检查非空缓冲区。</span><span class="sxs-lookup"><span data-stu-id="6b09d-250">It's checking for a non-empty buffer before checking `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="6b09d-251">由于该代码位于 `else if` 中，如果缓冲区中没有完整的消息，它将永远循环。</span><span class="sxs-lookup"><span data-stu-id="6b09d-251">Because it's in an `else if`, it will loop forever if there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet3":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="6b09d-252">❌ **意外挂起**</span><span class="sxs-lookup"><span data-stu-id="6b09d-252">❌ **Unexpected Hang**</span></span>

<span data-ttu-id="6b09d-253">在分析单条消息时，如果无条件调用 `PipeReader.AdvanceTo` 而 `buffer.End` 位于 `examined` 位置，则可能导致挂起。</span><span class="sxs-lookup"><span data-stu-id="6b09d-253">Unconditionally calling `PipeReader.AdvanceTo` with `buffer.End` in the `examined` position may result in hangs when parsing a single message.</span></span> <span data-ttu-id="6b09d-254">对 `PipeReader.AdvanceTo` 的下次调用将在以下情况下返回：</span><span class="sxs-lookup"><span data-stu-id="6b09d-254">The next call to `PipeReader.AdvanceTo` won't return until:</span></span>

* <span data-ttu-id="6b09d-255">有更多数据写入管道。</span><span class="sxs-lookup"><span data-stu-id="6b09d-255">There's more data written to the pipe.</span></span>
* <span data-ttu-id="6b09d-256">以及之前未检查过新数据。</span><span class="sxs-lookup"><span data-stu-id="6b09d-256">And the new data wasn't previously examined.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet4":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="6b09d-257">❌ **内存不足 (OOM)**</span><span class="sxs-lookup"><span data-stu-id="6b09d-257">❌ **Out of Memory (OOM)**</span></span>

<span data-ttu-id="6b09d-258">在满足以下条件的情况下，以下代码将保持缓冲，直到发生 <xref:System.OutOfMemoryException>：</span><span class="sxs-lookup"><span data-stu-id="6b09d-258">With the following conditions, the following code keeps buffering until an <xref:System.OutOfMemoryException> occurs:</span></span>

* <span data-ttu-id="6b09d-259">没有最大消息大小。</span><span class="sxs-lookup"><span data-stu-id="6b09d-259">There's no maximum message size.</span></span>
* <span data-ttu-id="6b09d-260">从 `PipeReader` 返回的数据不会生成完整的消息。</span><span class="sxs-lookup"><span data-stu-id="6b09d-260">The data returned from the `PipeReader` doesn't make a complete message.</span></span> <span data-ttu-id="6b09d-261">例如，它不会生成完整的消息，因为另一端正在编写一条大消息（例如，一条为 4GB 的消息）。</span><span class="sxs-lookup"><span data-stu-id="6b09d-261">For example, it doesn't make a complete message because the other side is writing a large message (For example, a 4-GB message).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet5":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="6b09d-262">❌ **内存损坏**</span><span class="sxs-lookup"><span data-stu-id="6b09d-262">❌ **Memory Corruption**</span></span>

<span data-ttu-id="6b09d-263">当写入读取缓冲区的帮助程序时，应在调用 `Advance` 之前复制任何返回的有效负载。</span><span class="sxs-lookup"><span data-stu-id="6b09d-263">When writing helpers that read the buffer, any returned payload should be copied before calling `Advance`.</span></span> <span data-ttu-id="6b09d-264">下面的示例将返回 `Pipe` 已丢弃的内存，并可能将其重新用于下一个操作（读/写）。</span><span class="sxs-lookup"><span data-stu-id="6b09d-264">The following example will return memory that the `Pipe` has discarded and may reuse it for the next operation (read/write).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippetMessage":::

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet6":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a><span data-ttu-id="6b09d-265">PipeWriter</span><span class="sxs-lookup"><span data-stu-id="6b09d-265">PipeWriter</span></span>

<span data-ttu-id="6b09d-266"><xref:System.IO.Pipelines.PipeWriter> 管理用于代表调用方写入的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="6b09d-266">The <xref:System.IO.Pipelines.PipeWriter> manages buffers for writing on the caller's behalf.</span></span> <span data-ttu-id="6b09d-267">`PipeWriter` 实现[`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601)。</span><span class="sxs-lookup"><span data-stu-id="6b09d-267">`PipeWriter` implements [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601).</span></span> <span data-ttu-id="6b09d-268">`IBufferWriter<byte>` 使得无需额外的缓冲区副本就可以访问缓冲区来执行写入操作。</span><span class="sxs-lookup"><span data-stu-id="6b09d-268">`IBufferWriter<byte>` makes it possible to get access to buffers to perform writes without additional buffer copies.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyPipeWriter.cs" id="snippet":::

<span data-ttu-id="6b09d-269">之前的代码：</span><span class="sxs-lookup"><span data-stu-id="6b09d-269">The previous code:</span></span>

* <span data-ttu-id="6b09d-270">使用 <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> 从 `PipeWriter` 请求至少 5 个字节的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="6b09d-270">Requests a buffer of at least 5 bytes from the `PipeWriter` using <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>.</span></span>
* <span data-ttu-id="6b09d-271">将 ASCII 字符串 `"Hello"` 的字节写入返回的 `Memory<byte>`。</span><span class="sxs-lookup"><span data-stu-id="6b09d-271">Writes bytes for the ASCII string `"Hello"` to the returned `Memory<byte>`.</span></span>
* <span data-ttu-id="6b09d-272">调用 <xref:System.IO.Pipelines.PipeWriter.Advance%2A> 以指示写入缓冲区的字节数。</span><span class="sxs-lookup"><span data-stu-id="6b09d-272">Calls <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to indicate how many bytes were written to the buffer.</span></span>
* <span data-ttu-id="6b09d-273">刷新 `PipeWriter`，以便将字节发送到基础设备。</span><span class="sxs-lookup"><span data-stu-id="6b09d-273">Flushes the `PipeWriter`, which sends the bytes to the underlying device.</span></span>

<span data-ttu-id="6b09d-274">以前的写入方法使用 `PipeWriter` 提供的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="6b09d-274">The previous method of writing uses the buffers provided by the `PipeWriter`.</span></span> <span data-ttu-id="6b09d-275">或者，<xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>：</span><span class="sxs-lookup"><span data-stu-id="6b09d-275">Alternatively, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="6b09d-276">将现有缓冲区复制到 `PipeWriter`。</span><span class="sxs-lookup"><span data-stu-id="6b09d-276">Copies the existing buffer to the `PipeWriter`.</span></span>
* <span data-ttu-id="6b09d-277">根据需要调用 `GetSpan``Advance`，然后调用 <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>。</span><span class="sxs-lookup"><span data-stu-id="6b09d-277">Calls `GetSpan`, `Advance` as appropriate and calls <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyPipeWriter.cs" id="snippet2":::

### <a name="cancellation"></a><span data-ttu-id="6b09d-278">取消</span><span class="sxs-lookup"><span data-stu-id="6b09d-278">Cancellation</span></span>

<span data-ttu-id="6b09d-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> 支持传递 <xref:System.Threading.CancellationToken>。</span><span class="sxs-lookup"><span data-stu-id="6b09d-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> supports passing a <xref:System.Threading.CancellationToken>.</span></span> <span data-ttu-id="6b09d-280">如果令牌在刷新挂起时被取消，则传递 `CancellationToken` 将导致 `OperationCanceledException`。</span><span class="sxs-lookup"><span data-stu-id="6b09d-280">Passing a `CancellationToken` results in an `OperationCanceledException` if the token is canceled while there's a flush pending.</span></span> <span data-ttu-id="6b09d-281">`PipeWriter.FlushAsync` 支持通过 <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> 取消当前刷新操作而不引发异常的方法。</span><span class="sxs-lookup"><span data-stu-id="6b09d-281">`PipeWriter.FlushAsync` supports a way to cancel the current flush operation via <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> without raising an exception.</span></span> <span data-ttu-id="6b09d-282">调用 `PipeWriter.CancelPendingFlush` 将导致对 `PipeWriter.FlushAsync` 或 `PipeWriter.WriteAsync` 的当前或下次调用返回 <xref:System.IO.Pipelines.FlushResult>，并将 `IsCanceled` 设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="6b09d-282">Calling `PipeWriter.CancelPendingFlush` causes the current or next call to `PipeWriter.FlushAsync` or `PipeWriter.WriteAsync` to return a <xref:System.IO.Pipelines.FlushResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="6b09d-283">这对于以非破坏性和非异常的方式停止暂停刷新非常有用。</span><span class="sxs-lookup"><span data-stu-id="6b09d-283">This can be useful for halting the yielding flush in a non-destructive and non-exceptional way.</span></span>

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a><span data-ttu-id="6b09d-284">PipeWriter 常见问题</span><span class="sxs-lookup"><span data-stu-id="6b09d-284">PipeWriter common problems</span></span>

* <span data-ttu-id="6b09d-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> 和 <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> 返回至少具有请求内存量的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="6b09d-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> and <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="6b09d-286">请勿假设确切的缓冲区大小  。</span><span class="sxs-lookup"><span data-stu-id="6b09d-286">**Don't** assume exact buffer sizes.</span></span>
* <span data-ttu-id="6b09d-287">无法保证连续的调用将返回相同的缓冲区或相同大小的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="6b09d-287">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
* <span data-ttu-id="6b09d-288">在调用 <xref:System.IO.Pipelines.PipeWriter.Advance%2A> 之后，必须请求一个新的缓冲区来继续写入更多数据。</span><span class="sxs-lookup"><span data-stu-id="6b09d-288">A new buffer must be requested after calling <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to continue writing more data.</span></span> <span data-ttu-id="6b09d-289">不能写入先前获得的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="6b09d-289">The previously acquired buffer can't be written to.</span></span>
* <span data-ttu-id="6b09d-290">如果未完成对 `FlushAsync` 的调用，则调用 `GetMemory` 或 `GetSpan` 将不安全。</span><span class="sxs-lookup"><span data-stu-id="6b09d-290">Calling `GetMemory` or `GetSpan` while there's an incomplete call to `FlushAsync` isn't safe.</span></span>
* <span data-ttu-id="6b09d-291">如果未刷新数据，则调用 `Complete` 或 `CompleteAsync` 可能导致内存损坏。</span><span class="sxs-lookup"><span data-stu-id="6b09d-291">Calling `Complete` or `CompleteAsync` while there's unflushed data can result in memory corruption.</span></span>

## <a name="iduplexpipe"></a><span data-ttu-id="6b09d-292">IDuplexPipe</span><span class="sxs-lookup"><span data-stu-id="6b09d-292">IDuplexPipe</span></span>

<span data-ttu-id="6b09d-293"><xref:System.IO.Pipelines.IDuplexPipe> 是支持读写的类型的协定。</span><span class="sxs-lookup"><span data-stu-id="6b09d-293">The <xref:System.IO.Pipelines.IDuplexPipe> is a contract for types that support both reading and writing.</span></span> <span data-ttu-id="6b09d-294">例如，网络连接将由 `IDuplexPipe` 表示。</span><span class="sxs-lookup"><span data-stu-id="6b09d-294">For example, a network connection would be represented by an `IDuplexPipe`.</span></span>

 <span data-ttu-id="6b09d-295">与包含 `PipeReader` 和 `PipeWriter` 的 `Pipe` 不同，`IDuplexPipe` 表示全双工连接的一侧。</span><span class="sxs-lookup"><span data-stu-id="6b09d-295">Unlike `Pipe`, which contains a `PipeReader` and a `PipeWriter`, `IDuplexPipe` represents a single side of a full duplex connection.</span></span> <span data-ttu-id="6b09d-296">这意味着写入 `PipeWriter` 的内容不会从 `PipeReader` 中读取。</span><span class="sxs-lookup"><span data-stu-id="6b09d-296">That means what is written to the `PipeWriter` will not be read from the `PipeReader`.</span></span>

## <a name="streams"></a><span data-ttu-id="6b09d-297">流</span><span class="sxs-lookup"><span data-stu-id="6b09d-297">Streams</span></span>

<span data-ttu-id="6b09d-298">在读取或写入流数据时，通常使用反序列化程序读取数据，并使用序列化程序写入数据。</span><span class="sxs-lookup"><span data-stu-id="6b09d-298">When reading or writing stream data, you typically read data using a de-serializer and write data using a serializer.</span></span> <span data-ttu-id="6b09d-299">大多数读取和写入流 API 都有一个 `Stream` 参数。</span><span class="sxs-lookup"><span data-stu-id="6b09d-299">Most of these read and write stream APIs have a `Stream` parameter.</span></span> <span data-ttu-id="6b09d-300">为了更轻松地与这些现有 API 集成，`PipeReader` 和 `PipeWriter` 公开了一个 <xref:System.IO.Pipelines.PipeReader.AsStream%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="6b09d-300">To make it easier to integrate with these existing APIs, `PipeReader` and `PipeWriter` expose an <xref:System.IO.Pipelines.PipeReader.AsStream%2A> method.</span></span> <span data-ttu-id="6b09d-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A> 返回围绕 `PipeReader` 或 `PipeWriter` 的 `Stream` 实现。</span><span class="sxs-lookup"><span data-stu-id="6b09d-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A> returns a `Stream` implementation around the `PipeReader` or `PipeWriter`.</span></span>

### <a name="stream-example"></a><span data-ttu-id="6b09d-302">流示例</span><span class="sxs-lookup"><span data-stu-id="6b09d-302">Stream example</span></span>

<span data-ttu-id="6b09d-303">可使用给定了 <xref:System.IO.Stream> 对象和可选的相应创建选项的静态 `Create` 方法创建 `PipeReader` 和 `PipeWriter` 实例。</span><span class="sxs-lookup"><span data-stu-id="6b09d-303">`PipeReader` and `PipeWriter` instances can be created using the static `Create` methods given a <xref:System.IO.Stream> object and optional corresponding creation options.</span></span>

<span data-ttu-id="6b09d-304"><xref:System.IO.Pipelines.StreamPipeReaderOptions> 允许使用以下参数控制 `PipeReader` 实例的创建：</span><span class="sxs-lookup"><span data-stu-id="6b09d-304">The <xref:System.IO.Pipelines.StreamPipeReaderOptions> allow for control over the creation of the `PipeReader` instance with the following parameters:</span></span>

- <span data-ttu-id="6b09d-305"><xref:System.IO.Pipelines.StreamPipeReaderOptions.BufferSize?displayProperty=nameWithType> 是从池中租用内存时使用的最小缓冲区大小（以字节为单位），默认值为 `4096`。</span><span class="sxs-lookup"><span data-stu-id="6b09d-305"><xref:System.IO.Pipelines.StreamPipeReaderOptions.BufferSize?displayProperty=nameWithType> is the minimum buffer size in bytes used when renting memory from the pool, and defaults to `4096`.</span></span>
- <span data-ttu-id="6b09d-306"><xref:System.IO.Pipelines.StreamPipeReaderOptions.LeaveOpen?displayProperty=nameWithType> 标志确定在 `PipeReader` 完成之后基础流是否保持打开状态，默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="6b09d-306"><xref:System.IO.Pipelines.StreamPipeReaderOptions.LeaveOpen?displayProperty=nameWithType> flag determines whether or not the underlying stream is left open after the `PipeReader` completes, and defaults to `false`.</span></span>
- <span data-ttu-id="6b09d-307"><xref:System.IO.Pipelines.StreamPipeReaderOptions.MinimumReadSize?displayProperty=nameWithType> 表示分配新缓冲区之前缓冲区中剩余字节的阈值，默认值为 `1024`。</span><span class="sxs-lookup"><span data-stu-id="6b09d-307"><xref:System.IO.Pipelines.StreamPipeReaderOptions.MinimumReadSize?displayProperty=nameWithType> represents the threshold of remaining bytes in the buffer before a new buffer is allocated, and defaults to `1024`.</span></span>
- <span data-ttu-id="6b09d-308"><xref:System.IO.Pipelines.StreamPipeReaderOptions.Pool?displayProperty=nameWithType> 是分配内存时使用的 `MemoryPool<byte>`，默认值为 `null`。</span><span class="sxs-lookup"><span data-stu-id="6b09d-308"><xref:System.IO.Pipelines.StreamPipeReaderOptions.Pool?displayProperty=nameWithType> is the `MemoryPool<byte>` used when allocating memory, and defaults to `null`.</span></span>

<span data-ttu-id="6b09d-309"><xref:System.IO.Pipelines.StreamPipeWriterOptions> 允许使用以下参数控制 `PipeWriter` 实例的创建：</span><span class="sxs-lookup"><span data-stu-id="6b09d-309">The <xref:System.IO.Pipelines.StreamPipeWriterOptions> allow for control over the creation of the `PipeWriter` instance with the following parameters:</span></span>

- <span data-ttu-id="6b09d-310"><xref:System.IO.Pipelines.StreamPipeWriterOptions.LeaveOpen?displayProperty=nameWithType> 标志确定在 `PipeWriter` 完成之后基础流是否保持打开状态，默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="6b09d-310"><xref:System.IO.Pipelines.StreamPipeWriterOptions.LeaveOpen?displayProperty=nameWithType> flag determines whether or not the underlying stream is left open after the `PipeWriter` completes, and defaults to `false`.</span></span>
- <span data-ttu-id="6b09d-311"><xref:System.IO.Pipelines.StreamPipeWriterOptions.MinimumBufferSize?displayProperty=nameWithType> 表示从 <xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool> 租用内存时要使用的最小缓冲区大小，默认值为 `4096`。</span><span class="sxs-lookup"><span data-stu-id="6b09d-311"><xref:System.IO.Pipelines.StreamPipeWriterOptions.MinimumBufferSize?displayProperty=nameWithType> represents the minimum buffer size to use when renting memory from the <xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool>, and defaults to `4096`.</span></span>
- <span data-ttu-id="6b09d-312"><xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool?displayProperty=nameWithType> 是分配内存时使用的 `MemoryPool<byte>`，默认值为 `null`。</span><span class="sxs-lookup"><span data-stu-id="6b09d-312"><xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool?displayProperty=nameWithType> is the `MemoryPool<byte>` used when allocating memory, and defaults to `null`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6b09d-313">使用 `Create` 方法创建 `PipeReader` 和 `PipeWriter` 实例时，需要考虑 `Stream` 对象的生存期。</span><span class="sxs-lookup"><span data-stu-id="6b09d-313">When creating `PipeReader` and `PipeWriter` instances using the `Create` methods, you need to consider the `Stream` object lifetime.</span></span> <span data-ttu-id="6b09d-314">如果在读取器或编写器使用该方法完成操作后，你需要访问流，则需要在创建选项上将 `LeaveOpen` 标志设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="6b09d-314">If you need access to the stream after the reader or writer is done with it, you'll need to set the `LeaveOpen` flag to `true` on the creation options.</span></span> <span data-ttu-id="6b09d-315">否则，流将关闭。</span><span class="sxs-lookup"><span data-stu-id="6b09d-315">Otherwise, the stream will be closed.</span></span>

<span data-ttu-id="6b09d-316">以下代码演示了使用 `Create` 方法从流中创建 `PipeReader` 和 `PipeWriter` 实例。</span><span class="sxs-lookup"><span data-stu-id="6b09d-316">The following code demonstrates the creation of `PipeReader` and `PipeWriter` instances using the `Create` methods from a stream.</span></span>

:::code language="csharp" source="snippets/pipelines/Program.cs":::

<span data-ttu-id="6b09d-317">应用程序使用 <xref:System.IO.StreamReader> 将 lorem-ipsum.txt 文件作为流进行读取。</span><span class="sxs-lookup"><span data-stu-id="6b09d-317">The application uses a <xref:System.IO.StreamReader> to read the *lorem-ipsum.txt* file as a stream.</span></span> <span data-ttu-id="6b09d-318"><xref:System.IO.FileStream> 传递给 <xref:System.IO.Pipelines.PipeReader.Create%2A?displayProperty=nameWithType>，后者实例化 `PipeReader` 对象。</span><span class="sxs-lookup"><span data-stu-id="6b09d-318">The <xref:System.IO.FileStream> is passed to <xref:System.IO.Pipelines.PipeReader.Create%2A?displayProperty=nameWithType>, which instantiates a `PipeReader` object.</span></span> <span data-ttu-id="6b09d-319">然后，控制台应用程序使用 <xref:System.Console.OpenStandardOutput?displayProperty=nameWithType> 将其标准输出流传递到 <xref:System.IO.Pipelines.PipeWriter.Create%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="6b09d-319">The console application then passes its standard output stream to <xref:System.IO.Pipelines.PipeWriter.Create%2A?displayProperty=nameWithType> using <xref:System.Console.OpenStandardOutput?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6b09d-320">示例支持[取消](#cancellation)。</span><span class="sxs-lookup"><span data-stu-id="6b09d-320">The example supports [cancellation](#cancellation).</span></span>

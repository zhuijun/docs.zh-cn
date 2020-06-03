---
title: System.Buffers - .NET
ms.date: 12/05/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- buffers [.NET]
- I/O [.NET], buffers
author: rick-anderson
ms.author: riande
ms.openlocfilehash: d113def0182dc6a5bcea6c18b2d0e4b475946e31
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739619"
---
# <a name="work-with-buffers-in-net"></a><span data-ttu-id="01a95-102">使用 .NET 中的缓冲区</span><span class="sxs-lookup"><span data-stu-id="01a95-102">Work with Buffers in .NET</span></span>

<span data-ttu-id="01a95-103">本文概述了有助于读取跨多个缓冲区运行的数据的类型。</span><span class="sxs-lookup"><span data-stu-id="01a95-103">This article provides an overview of types that help read data that runs across multiple buffers.</span></span> <span data-ttu-id="01a95-104">它们主要用于支持 <xref:System.IO.Pipelines.PipeReader> 对象。</span><span class="sxs-lookup"><span data-stu-id="01a95-104">They're primarily used to support <xref:System.IO.Pipelines.PipeReader> objects.</span></span>

## <a name="ibufferwritert"></a><span data-ttu-id="01a95-105">IBufferWriter\<T\></span><span class="sxs-lookup"><span data-stu-id="01a95-105">IBufferWriter\<T\></span></span>

<span data-ttu-id="01a95-106"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName> 是同步缓冲写入的协定。</span><span class="sxs-lookup"><span data-stu-id="01a95-106"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName> is a contract for synchronous buffered writing.</span></span> <span data-ttu-id="01a95-107">在最低级别上，接口：</span><span class="sxs-lookup"><span data-stu-id="01a95-107">At the lowest level, the interface:</span></span>

- <span data-ttu-id="01a95-108">是基本的，不难使用。</span><span class="sxs-lookup"><span data-stu-id="01a95-108">Is basic and not difficult to use.</span></span>
- <span data-ttu-id="01a95-109">允许访问 <xref:System.Memory%601> 或 <xref:System.Span%601>。</span><span class="sxs-lookup"><span data-stu-id="01a95-109">Allows access to a <xref:System.Memory%601> or <xref:System.Span%601>.</span></span> <span data-ttu-id="01a95-110">可以写入 `Memory<T>` 或 `Span<T>`，而且你可以确定写入了多少个 `T` 项。</span><span class="sxs-lookup"><span data-stu-id="01a95-110">The `Memory<T>` or `Span<T>` can be written to and you can determine how many `T` items were written.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

<span data-ttu-id="01a95-111">前面的方法：</span><span class="sxs-lookup"><span data-stu-id="01a95-111">The preceding method:</span></span>

- <span data-ttu-id="01a95-112">使用 `GetSpan(5)` 从 `IBufferWriter<byte>` 请求至少 5 个字节的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="01a95-112">Requests a buffer of at least 5 bytes from the `IBufferWriter<byte>` using `GetSpan(5)`.</span></span>
- <span data-ttu-id="01a95-113">将 ASCII 字符串“Hello”的字节写入返回的 `Span<byte>`。</span><span class="sxs-lookup"><span data-stu-id="01a95-113">Writes bytes for the ASCII string "Hello" to the returned `Span<byte>`.</span></span>
- <span data-ttu-id="01a95-114">调用 <xref:System.Buffers.IBufferWriter%601> 以指示写入缓冲区的字节数。</span><span class="sxs-lookup"><span data-stu-id="01a95-114">Calls  <xref:System.Buffers.IBufferWriter%601> to indicate how many bytes were written to the buffer.</span></span>

<span data-ttu-id="01a95-115">此写入方法使用 `IBufferWriter<T>` 提供的 `Memory<T>`/`Span<T>` 缓冲区。</span><span class="sxs-lookup"><span data-stu-id="01a95-115">This method of writing uses the `Memory<T>`/`Span<T>` buffer provided by the `IBufferWriter<T>`.</span></span> <span data-ttu-id="01a95-116">或者，可以使用 <xref:System.Buffers.BuffersExtensions.Write%2A> 扩展方法将现有缓冲区复制到 `IBufferWriter<T>`。</span><span class="sxs-lookup"><span data-stu-id="01a95-116">Alternatively, the <xref:System.Buffers.BuffersExtensions.Write%2A> extension method can be used to copy an existing buffer to the `IBufferWriter<T>`.</span></span> <span data-ttu-id="01a95-117">`Write` 根据需要调用 `GetSpan`/`Advance`，因此在写入后无需调用 `Advance`：</span><span class="sxs-lookup"><span data-stu-id="01a95-117">`Write` does the work of calling `GetSpan`/`Advance` as appropriate, so there's no need to call `Advance` after writing:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<span data-ttu-id="01a95-118"><xref:System.Buffers.ArrayBufferWriter%601> 是 `IBufferWriter<T>` 的实现，其后备存储是单个连续数组。</span><span class="sxs-lookup"><span data-stu-id="01a95-118"><xref:System.Buffers.ArrayBufferWriter%601> is an implementation of `IBufferWriter<T>` whose backing store is a single contiguous array.</span></span>

### <a name="ibufferwriter-common-problems"></a><span data-ttu-id="01a95-119">IBufferWriter 常见问题</span><span class="sxs-lookup"><span data-stu-id="01a95-119">IBufferWriter common problems</span></span>

- <span data-ttu-id="01a95-120">`GetSpan` 和 `GetMemory` 返回至少具有请求内存量的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="01a95-120">`GetSpan` and `GetMemory` return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="01a95-121">请勿假设确切的缓冲区大小。</span><span class="sxs-lookup"><span data-stu-id="01a95-121">Don't assume exact buffer sizes.</span></span>
- <span data-ttu-id="01a95-122">无法保证连续的调用将返回相同的缓冲区或相同大小的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="01a95-122">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
- <span data-ttu-id="01a95-123">在调用 `Advance` 之后，必须请求一个新的缓冲区来继续写入更多数据。</span><span class="sxs-lookup"><span data-stu-id="01a95-123">A new buffer must be requested after calling `Advance` to continue writing more data.</span></span> <span data-ttu-id="01a95-124">调用 `Advance` 后无法写入先前获取的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="01a95-124">A previously acquired buffer cannot be written to after `Advance` has been called.</span></span>

## <a name="readonlysequencet"></a><span data-ttu-id="01a95-125">ReadOnlySequence\<T\></span><span class="sxs-lookup"><span data-stu-id="01a95-125">ReadOnlySequence\<T\></span></span>

![显示管道中的内存且低于只读内存序列位置的 ReadOnlySequence](media/buffers/ro-sequence.png)

<span data-ttu-id="01a95-127"><xref:System.Buffers.ReadOnlySequence%601> 是一个可以表示 `T` 的连续或非连续序列的结构。</span><span class="sxs-lookup"><span data-stu-id="01a95-127"><xref:System.Buffers.ReadOnlySequence%601> is a struct that can represent a contiguous or noncontiguous sequence of `T`.</span></span> <span data-ttu-id="01a95-128">它通过以下方法进行构造：</span><span class="sxs-lookup"><span data-stu-id="01a95-128">It can be constructed from:</span></span>

1. <span data-ttu-id="01a95-129">一个 `T[]`</span><span class="sxs-lookup"><span data-stu-id="01a95-129">A `T[]`</span></span>
1. <span data-ttu-id="01a95-130">一个 `ReadOnlyMemory<T>`</span><span class="sxs-lookup"><span data-stu-id="01a95-130">A `ReadOnlyMemory<T>`</span></span>
1. <span data-ttu-id="01a95-131">一对链接列表节点 <xref:System.Buffers.ReadOnlySequenceSegment%601> 和索引，用于表示序列的开始位置和结束位置。</span><span class="sxs-lookup"><span data-stu-id="01a95-131">A pair of linked list node <xref:System.Buffers.ReadOnlySequenceSegment%601> and index to represent the start and end position of the sequence.</span></span>

<span data-ttu-id="01a95-132">第三种表示形式最值得关注，因为它对 `ReadOnlySequence<T>` 上的各种操作有性能影响：</span><span class="sxs-lookup"><span data-stu-id="01a95-132">The third representation is the most interesting one as it has performance implications on various operations on the `ReadOnlySequence<T>`:</span></span>

|<span data-ttu-id="01a95-133">表示形式</span><span class="sxs-lookup"><span data-stu-id="01a95-133">Representation</span></span>|<span data-ttu-id="01a95-134">操作</span><span class="sxs-lookup"><span data-stu-id="01a95-134">Operation</span></span>|<span data-ttu-id="01a95-135">复杂性</span><span class="sxs-lookup"><span data-stu-id="01a95-135">Complexity</span></span>|
---|---|---|
|`T[]`/`ReadOnlyMemory<T>`|`Length`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`GetPosition(long)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(int, int)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(SequencePostion,  SequencePostion)`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`Length`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`GetPosition(long)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(int, int)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(SequencePostion, SequencePostion)`|`O(1)`|

<span data-ttu-id="01a95-136">由于这种混合表示形式，`ReadOnlySequence<T>` 将索引作为 `SequencePosition`（而不是整数）公开。</span><span class="sxs-lookup"><span data-stu-id="01a95-136">Because of this mixed representation, the `ReadOnlySequence<T>` exposes indexes as `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="01a95-137">`SequencePosition`：</span><span class="sxs-lookup"><span data-stu-id="01a95-137">A `SequencePosition`:</span></span>

- <span data-ttu-id="01a95-138">是一个不透明的值，该值将索引表示为其起源的 `ReadOnlySequence<T>`。</span><span class="sxs-lookup"><span data-stu-id="01a95-138">Is an opaque value that represents an index into the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="01a95-139">由两个部分组成：整数和对象。</span><span class="sxs-lookup"><span data-stu-id="01a95-139">Consists of two parts, an integer and an object.</span></span> <span data-ttu-id="01a95-140">这两个值的含义与 `ReadOnlySequence<T>` 的实现相关联。</span><span class="sxs-lookup"><span data-stu-id="01a95-140">What these two values represent are tied to the implementation of `ReadOnlySequence<T>`.</span></span>

### <a name="access-data"></a><span data-ttu-id="01a95-141">访问数据</span><span class="sxs-lookup"><span data-stu-id="01a95-141">Access data</span></span>

<span data-ttu-id="01a95-142">`ReadOnlySequence<T>` 将数据作为 `ReadOnlyMemory<T>` 的枚举公开。</span><span class="sxs-lookup"><span data-stu-id="01a95-142">The `ReadOnlySequence<T>` exposes data as an enumerable of `ReadOnlyMemory<T>`.</span></span> <span data-ttu-id="01a95-143">可以使用基本 foreach 来枚举每个段：</span><span class="sxs-lookup"><span data-stu-id="01a95-143">Enumerating each of the segments can be done using a basic foreach:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

<span data-ttu-id="01a95-144">前面的方法搜索特定字节的每个段。</span><span class="sxs-lookup"><span data-stu-id="01a95-144">The preceding method searches each segment for a specific byte.</span></span> <span data-ttu-id="01a95-145">如果需要跟踪每个段的 `SequencePosition`，则 <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> 更为合适。</span><span class="sxs-lookup"><span data-stu-id="01a95-145">If you need to keep track of each segment's `SequencePosition`, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> is more appropriate.</span></span> <span data-ttu-id="01a95-146">下一个示例更改前面的代码，以返回 `SequencePosition` 而不是整数。</span><span class="sxs-lookup"><span data-stu-id="01a95-146">The next sample changes the preceding code to return a `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="01a95-147">返回 `SequencePosition` 的好处是使调用方能够避免第二次扫描以获取特定索引处的数据。</span><span class="sxs-lookup"><span data-stu-id="01a95-147">Returning a `SequencePosition` has the benefit of allowing the caller to avoid a second scan to get the data at a specific index.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

<span data-ttu-id="01a95-148">`SequencePosition` 和 `TryGet` 的组合类似于枚举器。</span><span class="sxs-lookup"><span data-stu-id="01a95-148">The combination of `SequencePosition` and `TryGet` acts like an enumerator.</span></span> <span data-ttu-id="01a95-149">将在每次迭代开始时修改位置字段，使其为 `ReadOnlySequence<T>` 中的每个段的开头。</span><span class="sxs-lookup"><span data-stu-id="01a95-149">The position field is modified at the start of each iteration to be start of each segment within the `ReadOnlySequence<T>`.</span></span>

<span data-ttu-id="01a95-150">前面的方法作为 `ReadOnlySequence<T>` 的扩展方法存在。</span><span class="sxs-lookup"><span data-stu-id="01a95-150">The preceding method exists as an extension method on `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="01a95-151"><xref:System.Buffers.BuffersExtensions.PositionOf%2A> 可用于简化前面的代码：</span><span class="sxs-lookup"><span data-stu-id="01a95-151"><xref:System.Buffers.BuffersExtensions.PositionOf%2A> can be used to simplify the preceding code:</span></span>

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a><span data-ttu-id="01a95-152">处理 ReadOnlySequence\<T\></span><span class="sxs-lookup"><span data-stu-id="01a95-152">Process a ReadOnlySequence\<T\></span></span>

<span data-ttu-id="01a95-153">处理 `ReadOnlySequence<T>` 可能比较困难，因为数据可能会拆分到序列中的多个段。</span><span class="sxs-lookup"><span data-stu-id="01a95-153">Processing a `ReadOnlySequence<T>` can be challenging since data may be split across multiple segments within the sequence.</span></span> <span data-ttu-id="01a95-154">为了获得最佳性能，请将代码拆分为两个路径：</span><span class="sxs-lookup"><span data-stu-id="01a95-154">For the best performance, split code into two paths:</span></span>

- <span data-ttu-id="01a95-155">处理单段情况的快速路径。</span><span class="sxs-lookup"><span data-stu-id="01a95-155">A fast path that deals with the single segment case.</span></span>
- <span data-ttu-id="01a95-156">处理拆分到各个段中的数据的慢速路径。</span><span class="sxs-lookup"><span data-stu-id="01a95-156">A slow path that deals with the data split across segments.</span></span>

<span data-ttu-id="01a95-157">可以使用多种方法来处理多段序列中的数据：</span><span class="sxs-lookup"><span data-stu-id="01a95-157">There are a few approaches that can be used to process data in multi-segmented sequences:</span></span>

- <span data-ttu-id="01a95-158">使用 [`SequenceReader<T>`](#sequencereadert)。</span><span class="sxs-lookup"><span data-stu-id="01a95-158">Use the [`SequenceReader<T>`](#sequencereadert).</span></span>
- <span data-ttu-id="01a95-159">逐段分析数据，同时跟踪已分析的段内的 `SequencePosition` 和索引。</span><span class="sxs-lookup"><span data-stu-id="01a95-159">Parse data segment by segment, keeping track of the `SequencePosition` and index within the segment parsed.</span></span> <span data-ttu-id="01a95-160">这样可以避免不必要的分配，但可能效率会很低，尤其是对于小型缓冲区。</span><span class="sxs-lookup"><span data-stu-id="01a95-160">This avoids unnecessary allocations but may be inefficient, especially for small buffers.</span></span>
- <span data-ttu-id="01a95-161">将 `ReadOnlySequence<T>` 复制到连续数组，并将其视为单个缓冲区：</span><span class="sxs-lookup"><span data-stu-id="01a95-161">Copy the `ReadOnlySequence<T>` to a contiguous array and treat it like a single buffer:</span></span>
  - <span data-ttu-id="01a95-162">如果 `ReadOnlySequence<T>` 的大小较小，则可以使用 [stackalloc](../../csharp/language-reference/operators/stackalloc.md) 运算符将数据复制到堆栈分配的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="01a95-162">If the size of the `ReadOnlySequence<T>` is small, it may be reasonable to copy the data into a stack-allocated buffer using the [stackalloc](../../csharp/language-reference/operators/stackalloc.md) operator.</span></span>
  - <span data-ttu-id="01a95-163">使用 <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType> 将 `ReadOnlySequence<T>` 复制到共用的数组。</span><span class="sxs-lookup"><span data-stu-id="01a95-163">Copy the `ReadOnlySequence<T>` into a pooled array using <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="01a95-164">使用 [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A)。</span><span class="sxs-lookup"><span data-stu-id="01a95-164">Use [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A).</span></span> <span data-ttu-id="01a95-165">不建议在热路径中使用这种方法，因为它会在堆上分配新的 `T[]`。</span><span class="sxs-lookup"><span data-stu-id="01a95-165">This isn't recommended in hot paths as it allocates a new `T[]` on the heap.</span></span>

<span data-ttu-id="01a95-166">以下示例演示了处理 `ReadOnlySequence<byte>` 的一些常见情况：</span><span class="sxs-lookup"><span data-stu-id="01a95-166">The following examples demonstrate some common cases for processing `ReadOnlySequence<byte>`:</span></span>

##### <a name="process-binary-data"></a><span data-ttu-id="01a95-167">处理二进制数据</span><span class="sxs-lookup"><span data-stu-id="01a95-167">Process binary data</span></span>

<span data-ttu-id="01a95-168">以下示例从 `ReadOnlySequence<byte>` 的开头分析 4 字节的大端整数长度。</span><span class="sxs-lookup"><span data-stu-id="01a95-168">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

##### <a name="process-text-data"></a><span data-ttu-id="01a95-169">处理文本数据</span><span class="sxs-lookup"><span data-stu-id="01a95-169">Process text data</span></span>

<span data-ttu-id="01a95-170">如下示例中：</span><span class="sxs-lookup"><span data-stu-id="01a95-170">The following example:</span></span>

- <span data-ttu-id="01a95-171">查找 `ReadOnlySequence<byte>` 中的第一个换行符 (`\r\n`)，并通过 out 'line' 参数返回该符号。</span><span class="sxs-lookup"><span data-stu-id="01a95-171">Finds the first newline (`\r\n`) in the `ReadOnlySequence<byte>` and returns it via the out 'line' parameter.</span></span>
- <span data-ttu-id="01a95-172">剪裁该行，从输入缓冲区中排除 `\r\n`。</span><span class="sxs-lookup"><span data-stu-id="01a95-172">Trims that line, excluding the `\r\n` from the input buffer.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a><span data-ttu-id="01a95-173">空段</span><span class="sxs-lookup"><span data-stu-id="01a95-173">Empty segments</span></span>

<span data-ttu-id="01a95-174">将空段存储在 `ReadOnlySequence<T>` 中是有效的。</span><span class="sxs-lookup"><span data-stu-id="01a95-174">It's valid to store empty segments inside of a `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="01a95-175">显式枚举段时，可能会出现空段：</span><span class="sxs-lookup"><span data-stu-id="01a95-175">Empty segments may occur while enumerating segments explicitly:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

<span data-ttu-id="01a95-176">前面的代码将创建一个包含空段的 `ReadOnlySequence<byte>`，并显示这些空段对各种 API 的影响：</span><span class="sxs-lookup"><span data-stu-id="01a95-176">The preceding code creates a `ReadOnlySequence<byte>` with empty segments and shows how those empty segments affect the various APIs:</span></span>

- <span data-ttu-id="01a95-177">包含指向空段的 `SequencePosition` 的 `ReadOnlySequence<T>.Slice` 会保留该段。</span><span class="sxs-lookup"><span data-stu-id="01a95-177">`ReadOnlySequence<T>.Slice` with a `SequencePosition` pointing to an empty segment preserves that segment.</span></span>
- <span data-ttu-id="01a95-178">包含 int 的 `ReadOnlySequence<T>.Slice` 会跳过空段。</span><span class="sxs-lookup"><span data-stu-id="01a95-178">`ReadOnlySequence<T>.Slice` with an int skips over the empty segments.</span></span>
- <span data-ttu-id="01a95-179">枚举 `ReadOnlySequence<T>` 会枚举空段。</span><span class="sxs-lookup"><span data-stu-id="01a95-179">Enumerating the `ReadOnlySequence<T>` enumerates the empty segments.</span></span>

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a><span data-ttu-id="01a95-180">ReadOnlySequence\<T> 和 SequencePosition 的潜在问题</span><span class="sxs-lookup"><span data-stu-id="01a95-180">Potential problems with ReadOnlySequence\<T> and SequencePosition</span></span>

<span data-ttu-id="01a95-181">处理 `ReadOnlySequence<T>`/`SequencePosition` 与常规 `ReadOnlySpan<T>`/`ReadOnlyMemory<T>`/`T[]`/`int` 时，有几个异常的结果：</span><span class="sxs-lookup"><span data-stu-id="01a95-181">There are several unusual outcomes when dealing with a `ReadOnlySequence<T>`/`SequencePosition` vs. a normal `ReadOnlySpan<T>`/`ReadOnlyMemory<T>`/`T[]`/`int`:</span></span>

- <span data-ttu-id="01a95-182">`SequencePosition` 是特定 `ReadOnlySequence<T>` 的位置标记，而不是绝对位置。</span><span class="sxs-lookup"><span data-stu-id="01a95-182">`SequencePosition` is a position marker for a specific `ReadOnlySequence<T>`, not an absolute position.</span></span> <span data-ttu-id="01a95-183">由于它是相对于特定 `ReadOnlySequence<T>` 的，因此如果在其起源的 `ReadOnlySequence<T>` 之外使用，则没有意义。</span><span class="sxs-lookup"><span data-stu-id="01a95-183">Because it's relative to a specific `ReadOnlySequence<T>`, it doesn't have meaning if used outside of the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="01a95-184">不能对没有 `ReadOnlySequence<T>` 的 `SequencePosition` 执行算术运算。</span><span class="sxs-lookup"><span data-stu-id="01a95-184">Arithmetic can't be performed on `SequencePosition` without the `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="01a95-185">这意味着，执行 `position++` 等基本操作将以 `ReadOnlySequence<T>.GetPosition(position, 1)` 的形式写入。</span><span class="sxs-lookup"><span data-stu-id="01a95-185">That means doing basic things like `position++` is written `ReadOnlySequence<T>.GetPosition(position, 1)`.</span></span>
- <span data-ttu-id="01a95-186">`GetPosition(long)` 不支持负索引。</span><span class="sxs-lookup"><span data-stu-id="01a95-186">`GetPosition(long)` does **not** support negative indexes.</span></span> <span data-ttu-id="01a95-187">这意味着，如果没有遍历所有段，就无法获取倒数第二个字符。</span><span class="sxs-lookup"><span data-stu-id="01a95-187">That means it's impossible to get the second to last character without walking all segments.</span></span>
- <span data-ttu-id="01a95-188">无法比较两个 `SequencePosition`，这使得难以：</span><span class="sxs-lookup"><span data-stu-id="01a95-188">Two `SequencePosition` can't be compared, making it difficult to:</span></span>
  - <span data-ttu-id="01a95-189">了解一个位置是否大于或小于另一个位置。</span><span class="sxs-lookup"><span data-stu-id="01a95-189">Know if one position is greater than or less than another position.</span></span>
  - <span data-ttu-id="01a95-190">编写一些分析算法。</span><span class="sxs-lookup"><span data-stu-id="01a95-190">Write some parsing algorithms.</span></span>
- <span data-ttu-id="01a95-191">`ReadOnlySequence<T>` 大于对象引用，并且应尽可能通过 [in](../../csharp/language-reference/keywords/in-parameter-modifier.md) 或 [ref](../../csharp/language-reference/keywords/ref.md) 进行传递。</span><span class="sxs-lookup"><span data-stu-id="01a95-191">`ReadOnlySequence<T>` is bigger than an object reference and should be passed by [in](../../csharp/language-reference/keywords/in-parameter-modifier.md) or [ref](../../csharp/language-reference/keywords/ref.md) where possible.</span></span> <span data-ttu-id="01a95-192">通过 `in` 或 `ref` 传递 `ReadOnlySequence<T>` 可减少[结构](../../csharp/language-reference/builtin-types/struct.md)的复制。</span><span class="sxs-lookup"><span data-stu-id="01a95-192">Passing `ReadOnlySequence<T>` by `in` or `ref` reduces copies of the [struct](../../csharp/language-reference/builtin-types/struct.md).</span></span>
- <span data-ttu-id="01a95-193">空段：</span><span class="sxs-lookup"><span data-stu-id="01a95-193">Empty segments:</span></span>
  - <span data-ttu-id="01a95-194">在 `ReadOnlySequence<T>` 中有效。</span><span class="sxs-lookup"><span data-stu-id="01a95-194">Are valid within a `ReadOnlySequence<T>`.</span></span>
  - <span data-ttu-id="01a95-195">可能会在使用 `ReadOnlySequence<T>.TryGet` 方法进行循环访问时出现。</span><span class="sxs-lookup"><span data-stu-id="01a95-195">Can appear when iterating using the `ReadOnlySequence<T>.TryGet` method.</span></span>
  - <span data-ttu-id="01a95-196">可能会在结合使用 `ReadOnlySequence<T>.Slice()` 方法与 `SequencePosition` 对象来对序列进行切片时出现。</span><span class="sxs-lookup"><span data-stu-id="01a95-196">Can appear slicing the sequence using the `ReadOnlySequence<T>.Slice()` method with `SequencePosition` objects.</span></span>

## <a name="sequencereadert"></a><span data-ttu-id="01a95-197">SequenceReader\<T\></span><span class="sxs-lookup"><span data-stu-id="01a95-197">SequenceReader\<T\></span></span>

<span data-ttu-id="01a95-198"><xref:System.Buffers.SequenceReader%601>：</span><span class="sxs-lookup"><span data-stu-id="01a95-198"><xref:System.Buffers.SequenceReader%601>:</span></span>

- <span data-ttu-id="01a95-199">是 .NET Core 3.0 中引入的一种新类型，用于简化 `ReadOnlySequence<T>` 的处理。</span><span class="sxs-lookup"><span data-stu-id="01a95-199">Is a new type that was introduced in .NET Core 3.0 to simplify the processing of a `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="01a95-200">统一了单段 `ReadOnlySequence<T>` 和多段 `ReadOnlySequence<T>` 之间的差异。</span><span class="sxs-lookup"><span data-stu-id="01a95-200">Unifies the differences between a single segment `ReadOnlySequence<T>` and multi-segment `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="01a95-201">提供用于读取二进制数据和文本数据（`byte` 和 `char`，不一定拆分到各个段）的帮助程序。</span><span class="sxs-lookup"><span data-stu-id="01a95-201">Provides helpers for reading binary and text data (`byte` and `char`) that may or may not be split across segments.</span></span>

<span data-ttu-id="01a95-202">提供用于处理二进制数据和带分隔符的数据的内置方法。</span><span class="sxs-lookup"><span data-stu-id="01a95-202">There are built-in methods for dealing with processing both binary and delimited data.</span></span> <span data-ttu-id="01a95-203">以下部分演示了与 `SequenceReader<T>` 相同的方法：</span><span class="sxs-lookup"><span data-stu-id="01a95-203">The following section demonstrates what those same methods look like with the `SequenceReader<T>`:</span></span>

### <a name="access-data"></a><span data-ttu-id="01a95-204">访问数据</span><span class="sxs-lookup"><span data-stu-id="01a95-204">Access data</span></span>

<span data-ttu-id="01a95-205">`SequenceReader<T>` 具有用于直接枚举 `ReadOnlySequence<T>` 内的数据的方法。</span><span class="sxs-lookup"><span data-stu-id="01a95-205">`SequenceReader<T>` has methods for enumerating data inside of the `ReadOnlySequence<T>` directly.</span></span> <span data-ttu-id="01a95-206">以下代码是一次处理 `ReadOnlySequence<byte>` 和 `byte` 的示例：</span><span class="sxs-lookup"><span data-stu-id="01a95-206">The following code is an example of processing a `ReadOnlySequence<byte>` a `byte` at a time:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

<span data-ttu-id="01a95-207">`CurrentSpan` 公开了当前段的 `Span`，这类似于在方法中手动完成的操作。</span><span class="sxs-lookup"><span data-stu-id="01a95-207">The `CurrentSpan` exposes the current segment's `Span`, which is similar to what was done in the method manually.</span></span>

### <a name="use-position"></a><span data-ttu-id="01a95-208">使用位置</span><span class="sxs-lookup"><span data-stu-id="01a95-208">Use position</span></span>

<span data-ttu-id="01a95-209">以下代码是使用 `SequenceReader<T>` 实现 `FindIndexOf` 的示例：</span><span class="sxs-lookup"><span data-stu-id="01a95-209">The following code is an example implementation of `FindIndexOf` using the `SequenceReader<T>`:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a><span data-ttu-id="01a95-210">处理二进制数据</span><span class="sxs-lookup"><span data-stu-id="01a95-210">Process binary data</span></span>

<span data-ttu-id="01a95-211">以下示例从 `ReadOnlySequence<byte>` 的开头分析 4 字节的大端整数长度。</span><span class="sxs-lookup"><span data-stu-id="01a95-211">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a><span data-ttu-id="01a95-212">处理文本数据</span><span class="sxs-lookup"><span data-stu-id="01a95-212">Process text data</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a><span data-ttu-id="01a95-213">SequenceReader\<T\> 常见问题</span><span class="sxs-lookup"><span data-stu-id="01a95-213">SequenceReader\<T\> common problems</span></span>

- <span data-ttu-id="01a95-214">由于 `SequenceReader<T>` 是可变结构，因此应始终通过[引用](../../csharp/language-reference/keywords/ref.md)进行传递。</span><span class="sxs-lookup"><span data-stu-id="01a95-214">Because `SequenceReader<T>` is a mutable struct, it should always be passed by [reference](../../csharp/language-reference/keywords/ref.md).</span></span>
- <span data-ttu-id="01a95-215">`SequenceReader<T>` 是[引用结构](../../csharp/language-reference/builtin-types/struct.md#ref-struct)，因此只能在同步方法中使用，不能存储在字段中。</span><span class="sxs-lookup"><span data-stu-id="01a95-215">`SequenceReader<T>` is a [ref struct](../../csharp/language-reference/builtin-types/struct.md#ref-struct) so it can only be used in synchronous methods and can't be stored in fields.</span></span> <span data-ttu-id="01a95-216">有关详细信息，请参阅[编写安全有效的 C# 代码](../../csharp/write-safe-efficient-code.md)。</span><span class="sxs-lookup"><span data-stu-id="01a95-216">For more information, see [Write safe and efficient C# code](../../csharp/write-safe-efficient-code.md).</span></span>
- <span data-ttu-id="01a95-217">`SequenceReader<T>` 已进行了优化，可用作只进读取器。</span><span class="sxs-lookup"><span data-stu-id="01a95-217">`SequenceReader<T>` is optimized for use as a forward-only reader.</span></span> <span data-ttu-id="01a95-218">`Rewind` 适用于无法利用其他 `Read`、`Peek` 和 `IsNext` API 来解决的小型备份。</span><span class="sxs-lookup"><span data-stu-id="01a95-218">`Rewind` is intended for small backups that can't be addressed utilizing other `Read`, `Peek`, and `IsNext` APIs.</span></span>

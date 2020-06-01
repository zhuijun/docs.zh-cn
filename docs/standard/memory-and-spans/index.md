---
title: 内存和跨度
ms.date: 10/03/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Memory<T>
- Span<T>
- buffers"
- pipeline processing
ms.openlocfilehash: c60c08d27c0e41228a15e8acdf01a9af28a23762
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201966"
---
# <a name="memory--and-span-related-types"></a><span data-ttu-id="8247f-102">内存和跨度相关类型</span><span class="sxs-lookup"><span data-stu-id="8247f-102">Memory- and span-related types</span></span>

<span data-ttu-id="8247f-103">从 .NET Core 2.1 开始，.NET 包含多个相互关联的类型，它们表示任意内存的相邻强类型区域。</span><span class="sxs-lookup"><span data-stu-id="8247f-103">Starting with .NET Core 2.1, .NET includes a number of interrelated types that represent a contiguous, strongly typed region of arbitrary memory.</span></span> <span data-ttu-id="8247f-104">这些方法包括：</span><span class="sxs-lookup"><span data-stu-id="8247f-104">These include:</span></span>

- <span data-ttu-id="8247f-105"><xref:System.Span%601?displayProperty=nameWithType>，用于访问连续内存区域的类型。</span><span class="sxs-lookup"><span data-stu-id="8247f-105"><xref:System.Span%601?displayProperty=nameWithType>, a type that is used to access a contiguous region of memory.</span></span> <span data-ttu-id="8247f-106"><xref:System.Span%601> 实例可由一组 `T` 类型、一个 <xref:System.String>、一个使用 [stackalloc](../../csharp/language-reference/operators/stackalloc.md) 分配的缓冲区或一个指向非托管内存的指针提供支持。</span><span class="sxs-lookup"><span data-stu-id="8247f-106">A <xref:System.Span%601> instance can be backed by an array of type `T`, a <xref:System.String>, a buffer allocated with [stackalloc](../../csharp/language-reference/operators/stackalloc.md), or a pointer to unmanaged memory.</span></span> <span data-ttu-id="8247f-107">由于它必须在堆栈上进行分配，因此存在诸多限制。</span><span class="sxs-lookup"><span data-stu-id="8247f-107">Because it has to be allocated on the stack, it has a number of restrictions.</span></span> <span data-ttu-id="8247f-108">例如，类中的字段不能是 <xref:System.Span%601> 类型，跨度类型也不能在异步操作中使用。</span><span class="sxs-lookup"><span data-stu-id="8247f-108">For example, a field in a class cannot be of type <xref:System.Span%601>, nor can span be used in asynchronous operations.</span></span>

- <span data-ttu-id="8247f-109"><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>，<xref:System.Span%601> 结构的不可变版本。</span><span class="sxs-lookup"><span data-stu-id="8247f-109"><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, an immutable version of the <xref:System.Span%601> structure.</span></span>

- <span data-ttu-id="8247f-110"><xref:System.Memory%601?displayProperty=nameWithType>，在托管堆而不是堆栈上分配的内存的相邻区域。</span><span class="sxs-lookup"><span data-stu-id="8247f-110"><xref:System.Memory%601?displayProperty=nameWithType>, a contiguous region of memory that is allocated on the managed heap rather than the stack.</span></span> <span data-ttu-id="8247f-111"><xref:System.Memory%601> 实例可以由一组 `T` 类型或一个 <xref:System.String> 提供支持。</span><span class="sxs-lookup"><span data-stu-id="8247f-111">A <xref:System.Memory%601> instance can be backed by an array of type `T` or a <xref:System.String>.</span></span> <span data-ttu-id="8247f-112">因为它可以存储在托管堆上，所以 <xref:System.Memory%601> 没有任何 <xref:System.Span%601> 限制。</span><span class="sxs-lookup"><span data-stu-id="8247f-112">Because it can be stored on the managed heap, <xref:System.Memory%601> has none of the limitations of <xref:System.Span%601>.</span></span>

- <span data-ttu-id="8247f-113"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>，<xref:System.Memory%601> 结构的不可变版本。</span><span class="sxs-lookup"><span data-stu-id="8247f-113"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, an immutable version of the <xref:System.Memory%601> structure.</span></span>

- <span data-ttu-id="8247f-114"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>，它将强类型内存块从内存池分配给所有者。</span><span class="sxs-lookup"><span data-stu-id="8247f-114"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, which allocates strongly typed blocks of memory from a memory pool to an owner.</span></span> <span data-ttu-id="8247f-115"><xref:System.Buffers.IMemoryOwner%601> 实例可以通过调用 <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> 从池中租用，并通过调用 <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType> 将其释放回池中。</span><span class="sxs-lookup"><span data-stu-id="8247f-115"><xref:System.Buffers.IMemoryOwner%601> instances can be rented from the pool by calling <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> and released back to the pool by calling <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="8247f-116"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>，表示内存块的所有者并控制其生存期管理。</span><span class="sxs-lookup"><span data-stu-id="8247f-116"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, which represents the owner of a block of memory and controls its lifetime management.</span></span>

- <span data-ttu-id="8247f-117"><xref:System.Buffers.MemoryManager%601>，一个抽象基类，可用于替换 <xref:System.Memory%601> 的实现，以便 <xref:System.Memory%601> 可以由其他类型（如安全句柄）提供支持。</span><span class="sxs-lookup"><span data-stu-id="8247f-117"><xref:System.Buffers.MemoryManager%601>, an abstract base class that can be used to replace the implementation of <xref:System.Memory%601> so that <xref:System.Memory%601> can be backed by additional types, such as safe handles.</span></span> <span data-ttu-id="8247f-118"><xref:System.Buffers.MemoryManager%601> 适用于高级方案。</span><span class="sxs-lookup"><span data-stu-id="8247f-118"><xref:System.Buffers.MemoryManager%601> is intended for advanced scenarios.</span></span>

- <span data-ttu-id="8247f-119"><xref:System.ArraySegment%601>，从特定索引开始的特定数量数组元素的包装器。</span><span class="sxs-lookup"><span data-stu-id="8247f-119"><xref:System.ArraySegment%601>, a wrapper for a particular number of array elements starting at a particular index.</span></span>

- <span data-ttu-id="8247f-120"><xref:System.MemoryExtensions?displayProperty=nameWithType>，用于将字符串、数组和数组段转换为 <xref:System.Memory%601> 块的扩展方法集合。</span><span class="sxs-lookup"><span data-stu-id="8247f-120"><xref:System.MemoryExtensions?displayProperty=nameWithType>, a collection of extension methods for converting strings, arrays, and array segments to <xref:System.Memory%601> blocks.</span></span>

> [!NOTE]
> <span data-ttu-id="8247f-121">对于早期框架，<xref:System.Span%601> 和 <xref:System.Memory%601> 在 [System.Memory NuGet 包](https://www.nuget.org/packages/System.Memory/)中提供。</span><span class="sxs-lookup"><span data-stu-id="8247f-121">For earlier frameworks, <xref:System.Span%601> and <xref:System.Memory%601> are available in the [System.Memory NuGet package](https://www.nuget.org/packages/System.Memory/).</span></span>

<span data-ttu-id="8247f-122">有关更多信息，请参见 <xref:System.Buffers?displayProperty=nameWithType> 命名空间。</span><span class="sxs-lookup"><span data-stu-id="8247f-122">For more information, see the <xref:System.Buffers?displayProperty=nameWithType> namespace.</span></span>

## <a name="working-with-memory-and-span"></a><span data-ttu-id="8247f-123">使用内存和跨度</span><span class="sxs-lookup"><span data-stu-id="8247f-123">Working with memory and span</span></span>

<span data-ttu-id="8247f-124">由于内存和跨度相关类型通常用于在处理管道中存储数据，因此开发人员在使用 <xref:System.Span%601>、<xref:System.Memory%601> 和相关类型时要务必遵循一套最佳做法。</span><span class="sxs-lookup"><span data-stu-id="8247f-124">Because the memory- and span-related types are typically used to store data in a processing pipeline, it is important that developers follow a set of best practices when using <xref:System.Span%601>, <xref:System.Memory%601>, and related types.</span></span> <span data-ttu-id="8247f-125">[内存\<T>> 和跨度\<T>> 使用准则](memory-t-usage-guidelines.md)中介绍了这些最佳做法。</span><span class="sxs-lookup"><span data-stu-id="8247f-125">These best practices are documented in [Memory\<T> and Span\<T> usage guidelines](memory-t-usage-guidelines.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8247f-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="8247f-126">See also</span></span>

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>

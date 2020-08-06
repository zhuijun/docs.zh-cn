---
title: 固定大小的缓冲区 - C# 编程指南
description: 了解固定大小的缓冲区。 固定大小的缓冲区用于编写与其他语言的数据源进行互操作的方法。
ms.date: 04/23/2020
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 1d4f5068121cdc98976954f2d99f4ac020c3b2a8
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381237"
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="941bd-104">固定大小的缓冲区（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="941bd-104">Fixed Size Buffers (C# Programming Guide)</span></span>

<span data-ttu-id="941bd-105">在 C# 中，可以使用 [fixed](../../language-reference/keywords/fixed-statement.md) 语句来创建在数据结构中具有固定大小的数组的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="941bd-105">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="941bd-106">当编写与其他语言或平台的数据源进行互操作的方法时，固定大小的缓冲区很有用。</span><span class="sxs-lookup"><span data-stu-id="941bd-106">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span></span> <span data-ttu-id="941bd-107">固定的数组可以采用允许用于常规结构成员的任何属性或修饰符。</span><span class="sxs-lookup"><span data-stu-id="941bd-107">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="941bd-108">唯一的限制是数组类型必须为 `bool`、`byte`、`char`、`short`、`int`, `long`、`sbyte`、`ushort`、`uint`、`ulong`、`float` 或 `double`。</span><span class="sxs-lookup"><span data-stu-id="941bd-108">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

## <a name="remarks"></a><span data-ttu-id="941bd-109">备注</span><span class="sxs-lookup"><span data-stu-id="941bd-109">Remarks</span></span>

<span data-ttu-id="941bd-110">在安全代码中，包含数组的 C# 结构不包含该数组元素。</span><span class="sxs-lookup"><span data-stu-id="941bd-110">In safe code, a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="941bd-111">而该结构包含对元素的引用。</span><span class="sxs-lookup"><span data-stu-id="941bd-111">Instead, the struct contains a reference to the elements.</span></span> <span data-ttu-id="941bd-112">当在[不安全的](../../language-reference/keywords/unsafe.md)代码块中使用数组时，可以在[结构](../../language-reference/builtin-types/struct.md)中嵌入该固定大小的数组。</span><span class="sxs-lookup"><span data-stu-id="941bd-112">You can embed an array of fixed size in a [struct](../../language-reference/builtin-types/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="941bd-113">以下 `struct` 的大小不依赖于数组中的元素数，因为 `pathName` 是一个引用：</span><span class="sxs-lookup"><span data-stu-id="941bd-113">Size of the following `struct` doesn't depend on the number of elements in the array, since `pathName` is a reference:</span></span>

[!code-csharp[Struct with embedded array](snippets/FixedKeywordExamples.cs#6)]

<span data-ttu-id="941bd-114">`struct` 可以在不安全代码中包含嵌入的数组。</span><span class="sxs-lookup"><span data-stu-id="941bd-114">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="941bd-115">在下面的示例中，`fixedBuffer` 数组具有固定的大小。</span><span class="sxs-lookup"><span data-stu-id="941bd-115">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="941bd-116">使用 `fixed` 语句建立指向第一个元素的指针。</span><span class="sxs-lookup"><span data-stu-id="941bd-116">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="941bd-117">通过此指针访问数组的元素。</span><span class="sxs-lookup"><span data-stu-id="941bd-117">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="941bd-118">`fixed` 语句将 `fixedBuffer` 实例字段固定到内存中的特定位置。</span><span class="sxs-lookup"><span data-stu-id="941bd-118">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

[!code-csharp[Struct with embedded inline array](snippets/FixedKeywordExamples.cs#7)]

<span data-ttu-id="941bd-119">包含 128 个元素的 `char` 数组的大小为 256 个字节。</span><span class="sxs-lookup"><span data-stu-id="941bd-119">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="941bd-120">固定大小的 [char](../../language-reference/builtin-types/char.md) 缓冲区每个字符始终占用两个字节，而不考虑编码。</span><span class="sxs-lookup"><span data-stu-id="941bd-120">Fixed size [char](../../language-reference/builtin-types/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="941bd-121">甚至在将 char 缓冲区封送到 API 方法或具有 `CharSet = CharSet.Auto` 或 `CharSet = CharSet.Ansi` 的结构时，这也为 true。</span><span class="sxs-lookup"><span data-stu-id="941bd-121">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="941bd-122">有关更多信息，请参见<xref:System.Runtime.InteropServices.CharSet>。</span><span class="sxs-lookup"><span data-stu-id="941bd-122">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="941bd-123">前面的示例演示访问未固定的 `fixed` 字段，此功能从 C# 7.3 开始提供。</span><span class="sxs-lookup"><span data-stu-id="941bd-123">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3.</span></span>

<span data-ttu-id="941bd-124">另一常见的固定大小的数组是 [bool](../../language-reference/builtin-types/bool.md) 数组。</span><span class="sxs-lookup"><span data-stu-id="941bd-124">Another common fixed-size array is the [bool](../../language-reference/builtin-types/bool.md) array.</span></span> <span data-ttu-id="941bd-125">`bool` 数组中的元素大小始终为一个字节。</span><span class="sxs-lookup"><span data-stu-id="941bd-125">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="941bd-126">`bool` 数组不适用于创建位数组或缓冲区。</span><span class="sxs-lookup"><span data-stu-id="941bd-126">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>

<span data-ttu-id="941bd-127">固定大小的缓冲区使用 <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType> 进行编译，它指示公共语言运行时 (CLR) 某个类型包含可能溢出的非托管数组。</span><span class="sxs-lookup"><span data-stu-id="941bd-127">Fixed size buffers are compiled with the <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType>, which instructs the common language runtime (CLR) that a type contains an unmanaged array that can potentially overflow.</span></span> <span data-ttu-id="941bd-128">这类似于使用 [stackalloc](../../language-reference/operators/stackalloc.md) 创建的内存，它会自动启用 CLR 中的缓冲区溢出检测功能。</span><span class="sxs-lookup"><span data-stu-id="941bd-128">This is similar to memory created using [stackalloc](../../language-reference/operators/stackalloc.md), which automatically enables buffer overrun detection features in the CLR.</span></span> <span data-ttu-id="941bd-129">前面的示例演示如何在 `unsafe struct` 中存在固定大小的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="941bd-129">The previous example shows how a fixed size buffer could exist in an `unsafe struct`.</span></span>

```csharp
internal unsafe struct Buffer
{
    public fixed char fixedBuffer[128];
}
```

<span data-ttu-id="941bd-130">为 `Buffer` 生成 C# 的编译器的特性如下：</span><span class="sxs-lookup"><span data-stu-id="941bd-130">The compiler generated C# for `Buffer`, is attributed as follows:</span></span>

```csharp
internal struct Buffer
{
    [StructLayout(LayoutKind.Sequential, Size = 256)]
    [CompilerGenerated]
    [UnsafeValueType]
    public struct <fixedBuffer>e__FixedBuffer
    {
        public char FixedElementField;
    }

    [FixedBuffer(typeof(char), 128)]
    public <fixedBuffer>e__FixedBuffer fixedBuffer;
}
```

<span data-ttu-id="941bd-131">固定大小的缓冲区与常规数组的区别体现在以下方面：</span><span class="sxs-lookup"><span data-stu-id="941bd-131">Fixed size buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="941bd-132">只能在 [unsafe](../../language-reference/keywords/unsafe.md) 上下文中使用。</span><span class="sxs-lookup"><span data-stu-id="941bd-132">May only be used in an [unsafe](../../language-reference/keywords/unsafe.md) context.</span></span>
- <span data-ttu-id="941bd-133">只能是结构的实例字段。</span><span class="sxs-lookup"><span data-stu-id="941bd-133">May only be instance fields of structs.</span></span>
- <span data-ttu-id="941bd-134">它们始终是矢量或一维数组。</span><span class="sxs-lookup"><span data-stu-id="941bd-134">They're always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="941bd-135">声明应包括长度，如 `fixed char id[8]`。</span><span class="sxs-lookup"><span data-stu-id="941bd-135">The declaration should include the length, such as `fixed char id[8]`.</span></span> <span data-ttu-id="941bd-136">不能使用 `fixed char id[]`。</span><span class="sxs-lookup"><span data-stu-id="941bd-136">You cannot use `fixed char id[]`.</span></span>

## <a name="see-also"></a><span data-ttu-id="941bd-137">请参阅</span><span class="sxs-lookup"><span data-stu-id="941bd-137">See also</span></span>

- [<span data-ttu-id="941bd-138">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="941bd-138">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="941bd-139">不安全代码和指针</span><span class="sxs-lookup"><span data-stu-id="941bd-139">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="941bd-140">fixed 语句</span><span class="sxs-lookup"><span data-stu-id="941bd-140">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="941bd-141">互操作性</span><span class="sxs-lookup"><span data-stu-id="941bd-141">Interoperability</span></span>](../interop/index.md)

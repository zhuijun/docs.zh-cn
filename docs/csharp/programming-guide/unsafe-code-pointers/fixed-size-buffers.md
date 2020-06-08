---
title: 固定大小的缓冲区 - C# 编程指南
ms.date: 04/23/2020
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 932ff3d57995ce47c4b74e8e888a479f0d09d0ed
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397423"
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="db995-102">固定大小的缓冲区（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="db995-102">Fixed Size Buffers (C# Programming Guide)</span></span>

<span data-ttu-id="db995-103">在 C# 中，可以使用 [fixed](../../language-reference/keywords/fixed-statement.md) 语句来创建在数据结构中具有固定大小的数组的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="db995-103">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="db995-104">当编写与其他语言或平台的数据源进行互操作的方法时，固定大小的缓冲区很有用。</span><span class="sxs-lookup"><span data-stu-id="db995-104">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span></span> <span data-ttu-id="db995-105">固定的数组可以采用允许用于常规结构成员的任何属性或修饰符。</span><span class="sxs-lookup"><span data-stu-id="db995-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="db995-106">唯一的限制是数组类型必须为 `bool`、`byte`、`char`、`short`、`int`, `long`、`sbyte`、`ushort`、`uint`、`ulong`、`float` 或 `double`。</span><span class="sxs-lookup"><span data-stu-id="db995-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

## <a name="remarks"></a><span data-ttu-id="db995-107">备注</span><span class="sxs-lookup"><span data-stu-id="db995-107">Remarks</span></span>

<span data-ttu-id="db995-108">在安全代码中，包含数组的 C# 结构不包含该数组元素。</span><span class="sxs-lookup"><span data-stu-id="db995-108">In safe code, a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="db995-109">而该结构包含对元素的引用。</span><span class="sxs-lookup"><span data-stu-id="db995-109">Instead, the struct contains a reference to the elements.</span></span> <span data-ttu-id="db995-110">当在[不安全的](../../language-reference/keywords/unsafe.md)代码块中使用数组时，可以在[结构](../../language-reference/builtin-types/struct.md)中嵌入该固定大小的数组。</span><span class="sxs-lookup"><span data-stu-id="db995-110">You can embed an array of fixed size in a [struct](../../language-reference/builtin-types/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="db995-111">以下 `struct` 的大小不依赖于数组中的元素数，因为 `pathName` 是一个引用：</span><span class="sxs-lookup"><span data-stu-id="db995-111">Size of the following `struct` doesn't depend on the number of elements in the array, since `pathName` is a reference:</span></span>

[!code-csharp[Struct with embedded array](snippets/FixedKeywordExamples.cs#6)]

<span data-ttu-id="db995-112">`struct` 可以在不安全代码中包含嵌入的数组。</span><span class="sxs-lookup"><span data-stu-id="db995-112">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="db995-113">在下面的示例中，`fixedBuffer` 数组具有固定的大小。</span><span class="sxs-lookup"><span data-stu-id="db995-113">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="db995-114">使用 `fixed` 语句建立指向第一个元素的指针。</span><span class="sxs-lookup"><span data-stu-id="db995-114">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="db995-115">通过此指针访问数组的元素。</span><span class="sxs-lookup"><span data-stu-id="db995-115">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="db995-116">`fixed` 语句将 `fixedBuffer` 实例字段固定到内存中的特定位置。</span><span class="sxs-lookup"><span data-stu-id="db995-116">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

[!code-csharp[Struct with embedded inline array](snippets/FixedKeywordExamples.cs#7)]

<span data-ttu-id="db995-117">包含 128 个元素的 `char` 数组的大小为 256 个字节。</span><span class="sxs-lookup"><span data-stu-id="db995-117">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="db995-118">固定大小的 [char](../../language-reference/builtin-types/char.md) 缓冲区每个字符始终占用两个字节，而不考虑编码。</span><span class="sxs-lookup"><span data-stu-id="db995-118">Fixed size [char](../../language-reference/builtin-types/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="db995-119">甚至在将 char 缓冲区封送到 API 方法或具有 `CharSet = CharSet.Auto` 或 `CharSet = CharSet.Ansi` 的结构时，这也为 true。</span><span class="sxs-lookup"><span data-stu-id="db995-119">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="db995-120">有关更多信息，请参见<xref:System.Runtime.InteropServices.CharSet>。</span><span class="sxs-lookup"><span data-stu-id="db995-120">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="db995-121">前面的示例演示访问未固定的 `fixed` 字段，此功能从 C# 7.3 开始提供。</span><span class="sxs-lookup"><span data-stu-id="db995-121">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3.</span></span>

<span data-ttu-id="db995-122">另一常见的固定大小的数组是 [bool](../../language-reference/builtin-types/bool.md) 数组。</span><span class="sxs-lookup"><span data-stu-id="db995-122">Another common fixed-size array is the [bool](../../language-reference/builtin-types/bool.md) array.</span></span> <span data-ttu-id="db995-123">`bool` 数组中的元素大小始终为一个字节。</span><span class="sxs-lookup"><span data-stu-id="db995-123">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="db995-124">`bool` 数组不适用于创建位数组或缓冲区。</span><span class="sxs-lookup"><span data-stu-id="db995-124">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>

<span data-ttu-id="db995-125">固定大小的缓冲区使用 <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType> 进行编译，它指示公共语言运行时 (CLR) 某个类型包含可能溢出的非托管数组。</span><span class="sxs-lookup"><span data-stu-id="db995-125">Fixed size buffers are compiled with the <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType>, which instructs the common language runtime (CLR) that a type contains an unmanaged array that can potentially overflow.</span></span> <span data-ttu-id="db995-126">这类似于使用 [stackalloc](../../language-reference/operators/stackalloc.md) 创建的内存，它会自动启用 CLR 中的缓冲区溢出检测功能。</span><span class="sxs-lookup"><span data-stu-id="db995-126">This is similar to memory created using [stackalloc](../../language-reference/operators/stackalloc.md), which automatically enables buffer overrun detection features in the CLR.</span></span> <span data-ttu-id="db995-127">前面的示例演示如何在 `unsafe struct` 中存在固定大小的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="db995-127">The previous example shows how a fixed size buffer could exist in an `unsafe struct`.</span></span>

```csharp
internal unsafe struct Buffer
{
    public fixed char fixedBuffer[128];
}
```

<span data-ttu-id="db995-128">为 `Buffer` 生成 C# 的编译器的特性如下：</span><span class="sxs-lookup"><span data-stu-id="db995-128">The compiler generated C# for `Buffer`, is attributed as follows:</span></span>

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

<span data-ttu-id="db995-129">固定大小的缓冲区与常规数组的区别体现在以下方面：</span><span class="sxs-lookup"><span data-stu-id="db995-129">Fixed size buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="db995-130">只能在 [unsafe](../../language-reference/keywords/unsafe.md) 上下文中使用。</span><span class="sxs-lookup"><span data-stu-id="db995-130">May only be used in an [unsafe](../../language-reference/keywords/unsafe.md) context.</span></span>
- <span data-ttu-id="db995-131">只能是结构的实例字段。</span><span class="sxs-lookup"><span data-stu-id="db995-131">May only be instance fields of structs.</span></span>
- <span data-ttu-id="db995-132">它们始终是矢量或一维数组。</span><span class="sxs-lookup"><span data-stu-id="db995-132">They're always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="db995-133">声明应包括长度，如 `fixed char id[8]`。</span><span class="sxs-lookup"><span data-stu-id="db995-133">The declaration should include the length, such as `fixed char id[8]`.</span></span> <span data-ttu-id="db995-134">不能使用 `fixed char id[]`。</span><span class="sxs-lookup"><span data-stu-id="db995-134">You cannot use `fixed char id[]`.</span></span>

## <a name="see-also"></a><span data-ttu-id="db995-135">请参阅</span><span class="sxs-lookup"><span data-stu-id="db995-135">See also</span></span>

- [<span data-ttu-id="db995-136">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="db995-136">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="db995-137">不安全代码和指针</span><span class="sxs-lookup"><span data-stu-id="db995-137">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="db995-138">fixed 语句</span><span class="sxs-lookup"><span data-stu-id="db995-138">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="db995-139">互操作性</span><span class="sxs-lookup"><span data-stu-id="db995-139">Interoperability</span></span>](../interop/index.md)

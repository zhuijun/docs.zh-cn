---
title: 'F # 4.5 中的新增功能-F # 指南'
description: '获取 F # 4.5 中提供的新功能的概述。'
ms.date: 11/27/2019
ms.openlocfilehash: 2c978c66a4bf231398508cbc1cbb8839228ea8e9
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202355"
---
# <a name="whats-new-in-f-45"></a><span data-ttu-id="677a4-103">F # 4.5 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="677a4-103">What's new in F# 4.5</span></span>

<span data-ttu-id="677a4-104">F # 4.5 添加了对 F # 语言的多项改进。</span><span class="sxs-lookup"><span data-stu-id="677a4-104">F# 4.5 adds multiple improvements to the F# language.</span></span> <span data-ttu-id="677a4-105">其中的许多功能都一起添加，使你能够以 F # 编写有效的代码，同时确保此代码是安全的。</span><span class="sxs-lookup"><span data-stu-id="677a4-105">Many of these features were added together to enable you to write efficient code in F# while also ensuring this code is safe.</span></span> <span data-ttu-id="677a4-106">这样做意味着在使用这些构造时，将一些概念添加到语言，并进行大量的编译器分析。</span><span class="sxs-lookup"><span data-stu-id="677a4-106">Doing so means adding a few concepts to the language and a significant amount of compiler analysis when using these constructs.</span></span>

## <a name="get-started"></a><span data-ttu-id="677a4-107">入门</span><span class="sxs-lookup"><span data-stu-id="677a4-107">Get started</span></span>

<span data-ttu-id="677a4-108">F # 4.5 适用于所有 .NET Core 分发版和 Visual Studio 工具。</span><span class="sxs-lookup"><span data-stu-id="677a4-108">F# 4.5 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="677a4-109">[开始处理 F #](../get-started/index.md)以了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="677a4-109">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="span-and-byref-like-structs"></a><span data-ttu-id="677a4-110">跨越和 byref 类似的结构</span><span class="sxs-lookup"><span data-stu-id="677a4-110">Span and byref-like structs</span></span>

<span data-ttu-id="677a4-111"><xref:System.Span%601>.Net Core 中引入的类型允许以强类型方式表示内存中的缓冲区，这在 f # 中现在允许 f # 4.5 开始。</span><span class="sxs-lookup"><span data-stu-id="677a4-111">The <xref:System.Span%601> type introduced in .NET Core allows you to represent buffers in memory in a strongly typed manner, which is now allowed in F# starting with F# 4.5.</span></span> <span data-ttu-id="677a4-112">下面的示例演示如何重新使用在 <xref:System.Span%601> 具有不同缓冲区表示形式的上操作的函数：</span><span class="sxs-lookup"><span data-stu-id="677a4-112">The following example shows how you can re-use a function operating on a <xref:System.Span%601> with different buffer representations:</span></span>

```fsharp
let safeSum (bytes: Span<byte>) =
    let mutable sum = 0
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    sum

// managed memory
let arrayMemory = Array.zeroCreate<byte>(100)
let arraySpan = new Span<byte>(arrayMemory)

safeSum(arraySpan) |> printfn "res = %d"

// native memory
let nativeMemory = Marshal.AllocHGlobal(100);
let nativeSpan = new Span<byte>(nativeMemory.ToPointer(), 100)

safeSum(nativeSpan) |> printfn "res = %d"
Marshal.FreeHGlobal(nativeMemory)

// stack memory
let mem = NativePtr.stackalloc<byte>(100)
let mem2 = mem |> NativePtr.toVoidPtr
let stackSpan = Span<byte>(mem2, 100)

safeSum(stackSpan) |> printfn "res = %d"
```

<span data-ttu-id="677a4-113">这项工作的一个重要方面是，跨越和其他[类似 byref 的结构](../language-reference/structures.md#byreflike-structs)都具有非常严格的静态分析，这些分析会将其使用方式限制为意外的方式。</span><span class="sxs-lookup"><span data-stu-id="677a4-113">An important aspect to this is that Span and other [byref-like structs](../language-reference/structures.md#byreflike-structs) have very rigid static analysis performed by the compiler that restrict their usage in ways you might find to be unexpected.</span></span> <span data-ttu-id="677a4-114">这是 F # 4.5 中引入的性能、表现力和安全之间的基本折衷。</span><span class="sxs-lookup"><span data-stu-id="677a4-114">This is the fundamental tradeoff between performance, expressiveness, and safety that is introduced in F# 4.5.</span></span>

## <a name="revamped-byrefs"></a><span data-ttu-id="677a4-115">改进 byref</span><span class="sxs-lookup"><span data-stu-id="677a4-115">Revamped byrefs</span></span>

<span data-ttu-id="677a4-116">在 F # 4.5 之前，F # 中的[byref](../language-reference/byrefs.md)不安全，错误适用于许多应用程序。</span><span class="sxs-lookup"><span data-stu-id="677a4-116">Prior to F# 4.5, [Byrefs](../language-reference/byrefs.md) in F# were unsafe and unsound for numerous applications.</span></span> <span data-ttu-id="677a4-117">F # 4.5 中解决了有关 byref 的 Soundness 问题，同时还应用了对 span 和类似 byref 的结构执行相同的静态分析。</span><span class="sxs-lookup"><span data-stu-id="677a4-117">Soundness issues around byrefs have been addressed in F# 4.5 and the same static analysis done for span and byref-like structs was also applied.</span></span>

### <a name="inreft-and-outreft"></a><span data-ttu-id="677a4-118">inref< 不> 和 outref<></span><span class="sxs-lookup"><span data-stu-id="677a4-118">inref<'T> and outref<'T></span></span>

<span data-ttu-id="677a4-119">为了表示只读、只写和读/写托管指针的概念，F # 4.5 引入了 `inref<'T>` ， `outref<'T>` 分别表示只读和只写指针的类型。</span><span class="sxs-lookup"><span data-stu-id="677a4-119">To represent the notion of a read-only, write-only, and read/write managed pointer, F# 4.5 introduces the `inref<'T>`, `outref<'T>` types to represent read-only and write-only pointers, respectively.</span></span> <span data-ttu-id="677a4-120">每个都有不同的语义。</span><span class="sxs-lookup"><span data-stu-id="677a4-120">Each have different semantics.</span></span> <span data-ttu-id="677a4-121">例如，无法写入 `inref<'T>` ：</span><span class="sxs-lookup"><span data-stu-id="677a4-121">For example, you cannot write to an `inref<'T>`:</span></span>

```fsharp
let f (dt: inref<DateTime>) =
    dt <- DateTime.Now // ERROR - cannot write to an inref!
```

<span data-ttu-id="677a4-122">默认情况下，类型推理会将托管指针推断为 `inref<'T>` 包含 F # 代码的不可变性质的行，除非已将某些内容声明为可变。</span><span class="sxs-lookup"><span data-stu-id="677a4-122">By default, type inference will infer managed pointers as `inref<'T>` to be in line with the immutable nature of F# code, unless something has already been declared as mutable.</span></span> <span data-ttu-id="677a4-123">若要使某些内容成为可写的，需要在将 `mutable` 其地址传递给操作它的函数或成员之前声明类型。</span><span class="sxs-lookup"><span data-stu-id="677a4-123">To make something writable, you'll need to declare a type as `mutable` before passing its address to a function or member that manipulates it.</span></span> <span data-ttu-id="677a4-124">若要了解详细信息，请参阅[byref](../language-reference/byrefs.md)。</span><span class="sxs-lookup"><span data-stu-id="677a4-124">To learn more, see [Byrefs](../language-reference/byrefs.md).</span></span>

## <a name="readonly-structs"></a><span data-ttu-id="677a4-125">只读结构</span><span class="sxs-lookup"><span data-stu-id="677a4-125">Readonly structs</span></span>

<span data-ttu-id="677a4-126">从 F # 4.5 开始，你可以使用批注结构， <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> 如下所示：</span><span class="sxs-lookup"><span data-stu-id="677a4-126">Starting with F# 4.5, you can annotate a struct with <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> as such:</span></span>

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="677a4-127">这不允许您在结构中声明可变成员，并发出允许 F # 和 c # 在从程序集使用时将其视为只读的元数据。</span><span class="sxs-lookup"><span data-stu-id="677a4-127">This disallows you from declaring a mutable member in the struct and emits metadata that allows F# and C# to treat it as readonly when consumed from an assembly.</span></span> <span data-ttu-id="677a4-128">若要了解详细信息，请参阅[ReadOnly 结构](../language-reference/structures.md#readonly-structs)。</span><span class="sxs-lookup"><span data-stu-id="677a4-128">To learn more, see [ReadOnly structs](../language-reference/structures.md#readonly-structs).</span></span>

## <a name="void-pointers"></a><span data-ttu-id="677a4-129">Void 指针</span><span class="sxs-lookup"><span data-stu-id="677a4-129">Void pointers</span></span>

<span data-ttu-id="677a4-130">`voidptr`类型已添加到 F # 4.5，如下函数所示：</span><span class="sxs-lookup"><span data-stu-id="677a4-130">The `voidptr` type is added to F# 4.5, as are the following functions:</span></span>

* <span data-ttu-id="677a4-131">`NativePtr.ofVoidPtr`将 void 指针转换为本机 int 指针</span><span class="sxs-lookup"><span data-stu-id="677a4-131">`NativePtr.ofVoidPtr` to convert a void pointer into a native int pointer</span></span>
* <span data-ttu-id="677a4-132">`NativePtr.toVoidPtr`将本机 int 指针转换为 void 指针</span><span class="sxs-lookup"><span data-stu-id="677a4-132">`NativePtr.toVoidPtr` to convert a native int pointer to a void pointer</span></span>

<span data-ttu-id="677a4-133">与使用 void 指针的本机组件进行互操作时，这非常有用。</span><span class="sxs-lookup"><span data-stu-id="677a4-133">This is helpful when interoperating with a native component that makes use of void pointers.</span></span>

## <a name="the-match-keyword"></a><span data-ttu-id="677a4-134">`match!` 关键字</span><span class="sxs-lookup"><span data-stu-id="677a4-134">The `match!` keyword</span></span>

<span data-ttu-id="677a4-135">`match!`关键字可在计算表达式内部增强模式匹配：</span><span class="sxs-lookup"><span data-stu-id="677a4-135">The `match!` keyword enhances pattern matching when inside a computation expression:</span></span>

```fsharp
// Code that returns an asynchronous option
let checkBananaAsync (s: string) =
    async {
        if s = "banana" then
            return Some s
        else
            return None
    }

// Now you can use 'match!'
let funcWithString (s: string) =
    async {
        match! checkBananaAsync s with
        | Some bananaString -> printfn "It's banana!"
        | None -> printfn "%s" s
}
```

<span data-ttu-id="677a4-136">这允许您缩短经常涉及混合选项（或其他类型）和计算表达式（如 async）的代码。</span><span class="sxs-lookup"><span data-stu-id="677a4-136">This allows you to shorten code that often involves mixing options (or other types) with computation expressions such as async.</span></span> <span data-ttu-id="677a4-137">若要了解详细信息，请参阅[match！](../language-reference/computation-expressions.md#match)。</span><span class="sxs-lookup"><span data-stu-id="677a4-137">To learn more, see [match!](../language-reference/computation-expressions.md#match).</span></span>

## <a name="relaxed-upcasting-requirements-in-array-list-and-sequence-expressions"></a><span data-ttu-id="677a4-138">数组、列表和序列表达式中的宽松向上转换要求</span><span class="sxs-lookup"><span data-stu-id="677a4-138">Relaxed upcasting requirements in array, list, and sequence expressions</span></span>

<span data-ttu-id="677a4-139">通常情况下，混合类型可以从数组、列表和序列表达式中的另一个继承，而这种混合类型需要将任何派生类型通过或向上转换为其父类型 `:>` `upcast` 。</span><span class="sxs-lookup"><span data-stu-id="677a4-139">Mixing types where one may inherit from another inside of array, list, and sequence expressions has traditionally required you to upcast any derived type to its parent type with `:>` or `upcast`.</span></span> <span data-ttu-id="677a4-140">这现在是宽松的，如下所示：</span><span class="sxs-lookup"><span data-stu-id="677a4-140">This is now relaxed, demonstrated as follows:</span></span>

```fsharp
let x0 : obj list  = [ "a" ] // ok pre-F# 4.5
let x1 : obj list  = [ "a"; "b" ] // ok pre-F# 4.5
let x2 : obj list  = [ yield "a" :> obj ] // ok pre-F# 4.5

let x3 : obj list  = [ yield "a" ] // Now ok for F# 4.5, and can replace x2
```

## <a name="indentation-relaxation-for-array-and-list-expressions"></a><span data-ttu-id="677a4-141">数组和列表表达式的缩进 relaxation</span><span class="sxs-lookup"><span data-stu-id="677a4-141">Indentation relaxation for array and list expressions</span></span>

<span data-ttu-id="677a4-142">在 F # 4.5 之前，需要在将数组和列表表达式作为参数传递给方法调用时过度缩进。</span><span class="sxs-lookup"><span data-stu-id="677a4-142">Prior to F# 4.5, you needed to excessively indent array and list expressions when passed as arguments to method calls.</span></span> <span data-ttu-id="677a4-143">不再需要此操作：</span><span class="sxs-lookup"><span data-stu-id="677a4-143">This is no longer required:</span></span>

```fsharp
module NoExcessiveIndenting =
    System.Console.WriteLine(format="{0}", arg = [|
        "hello"
    |])
    System.Console.WriteLine([|
        "hello"
    |])
```

---
title: 切片
description: '了解如何使用现有 F # 数据类型的切片，以及如何为其他数据类型定义自己的切片。'
ms.date: 12/23/2019
ms.openlocfilehash: d3ddb2c247c36a85842f565f051372c5f2c9a9e9
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559006"
---
# <a name="slices"></a><span data-ttu-id="72d7e-103">切片</span><span class="sxs-lookup"><span data-stu-id="72d7e-103">Slices</span></span>

<span data-ttu-id="72d7e-104">在 F # 中，切片是 `GetSlice` 在其定义或范围内 [类型扩展](type-extensions.md)中具有方法的任何数据类型的子集。</span><span class="sxs-lookup"><span data-stu-id="72d7e-104">In F#, a slice is a subset of any data type that has a `GetSlice` method in its definition or in an in-scope [type extension](type-extensions.md).</span></span> <span data-ttu-id="72d7e-105">它最常用于 F # 数组和列表。</span><span class="sxs-lookup"><span data-stu-id="72d7e-105">It is most commonly used with F# arrays and lists.</span></span> <span data-ttu-id="72d7e-106">本文介绍如何从现有的 F # 类型中获取切片，以及如何定义自己的切片。</span><span class="sxs-lookup"><span data-stu-id="72d7e-106">This article explains how to take slices from existing F# types and how to define your own slices.</span></span>

<span data-ttu-id="72d7e-107">切片与 [索引器](./members/indexed-properties.md)相似，但它不是从基础数据结构产生单个值，而是生成多个值。</span><span class="sxs-lookup"><span data-stu-id="72d7e-107">Slices are similar to [indexers](./members/indexed-properties.md), but instead of yielding a single value from the underlying data structure, they yield multiple ones.</span></span>

<span data-ttu-id="72d7e-108">F # 目前对切片字符串、列表、数组和二维数组具有内部支持。</span><span class="sxs-lookup"><span data-stu-id="72d7e-108">F# currently has intrinsic support for slicing strings, lists, arrays, and 2D arrays.</span></span>

## <a name="basic-slicing-with-f-lists-and-arrays"></a><span data-ttu-id="72d7e-109">带有 F # 列表和数组的基本切片</span><span class="sxs-lookup"><span data-stu-id="72d7e-109">Basic slicing with F# lists and arrays</span></span>

<span data-ttu-id="72d7e-110">切片最常见的数据类型是 F # 列表和数组。</span><span class="sxs-lookup"><span data-stu-id="72d7e-110">The most common data types that are sliced are F# lists and arrays.</span></span> <span data-ttu-id="72d7e-111">下面的示例演示如何通过列表执行此操作：</span><span class="sxs-lookup"><span data-stu-id="72d7e-111">The following example demonstrates how to do this with lists:</span></span>

```fsharp
// Generate a list of 100 integers
let fullList = [ 1 .. 100 ]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullList.[1..5]
printfn "Small slice: %A" smallSlice

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullList.[..5]
printfn "Unbounded beginning slice: %A" unboundedBeginning

// Create a slice from an index to the end of the list
let unboundedEnd = fullList.[94..]
printfn "Unbounded end slice: %A" unboundedEnd
```

<span data-ttu-id="72d7e-112">切片数组与切片列表类似：</span><span class="sxs-lookup"><span data-stu-id="72d7e-112">Slicing arrays is just like slicing lists:</span></span>

```fsharp
// Generate an array of 100 integers
let fullArray = [| 1 .. 100 |]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullArray.[1..5]
printfn "Small slice: %A" smallSlice

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullArray.[..5]
printfn "Unbounded beginning slice: %A" unboundedBeginning

// Create a slice from an index to the end of the list
let unboundedEnd = fullArray.[94..]
printfn "Unbounded end slice: %A" unboundedEnd
```

## <a name="slicing-multidimensional-arrays"></a><span data-ttu-id="72d7e-113">切片多维数组</span><span class="sxs-lookup"><span data-stu-id="72d7e-113">Slicing multidimensional arrays</span></span>

<span data-ttu-id="72d7e-114">F # 支持 F # 核心库中的多维数组。</span><span class="sxs-lookup"><span data-stu-id="72d7e-114">F# supports multidimensional arrays in the F# core library.</span></span> <span data-ttu-id="72d7e-115">与一维数组一样，多维数组的切片也很有用。</span><span class="sxs-lookup"><span data-stu-id="72d7e-115">As with one-dimensional arrays, slices of multidimensional arrays can also be useful.</span></span> <span data-ttu-id="72d7e-116">但是，附加维度的引入要求使用略微不同的语法，以便能够获取特定行和列的切片。</span><span class="sxs-lookup"><span data-stu-id="72d7e-116">However, the introduction of additional dimensions mandates a slightly different syntax so that you can take slices of specific rows and columns.</span></span>

<span data-ttu-id="72d7e-117">下面的示例演示如何切分二维数组：</span><span class="sxs-lookup"><span data-stu-id="72d7e-117">The following examples demonstrate how to slice a 2D array:</span></span>

```fsharp
// Generate a 3x3 2D matrix
let A = array2D [[1;2;3];[4;5;6];[7;8;9]]
printfn "Full matrix:\n %A" A

// Take the first row
let row0 = A.[0,*]
printfn "Row 0: %A" row0

// Take the first column
let col0 = A.[*,0]
printfn "Column 0: %A" col0

// Take all rows but only two columns
let subA = A.[*,0..1]
printfn "%A" subA

// Take two rows and all columns
let subA' = A.[0..1,*]
printfn "%A" subA'

// Slice a 2x2 matrix out of the full 3x3 matrix
let twoByTwo = A.[0..1,0..1]
printfn "%A" twoByTwo
```

<span data-ttu-id="72d7e-118">F # core 库当前没有 `GetSlice` 为三维数组定义。</span><span class="sxs-lookup"><span data-stu-id="72d7e-118">The F# core library does not currently define `GetSlice` for 3D arrays.</span></span> <span data-ttu-id="72d7e-119">如果要对三维数组或其他维度的其他数组进行切片，请 `GetSlice` 自行定义成员。</span><span class="sxs-lookup"><span data-stu-id="72d7e-119">If you wish to slice 3D arrays or other arrays of more dimensions, define the `GetSlice` member yourself.</span></span>

## <a name="defining-slices-for-other-data-structures"></a><span data-ttu-id="72d7e-120">为其他数据结构定义切片</span><span class="sxs-lookup"><span data-stu-id="72d7e-120">Defining slices for other data structures</span></span>

<span data-ttu-id="72d7e-121">F # 核心库定义了有限类型集的切片。</span><span class="sxs-lookup"><span data-stu-id="72d7e-121">The F# core library defines slices for a limited set of types.</span></span> <span data-ttu-id="72d7e-122">如果要定义更多数据类型的切片，可以在类型定义本身或类型扩展中执行此操作。</span><span class="sxs-lookup"><span data-stu-id="72d7e-122">If you wish to define slices for more data types, you can do so either in the type definition itself or in a type extension.</span></span>

<span data-ttu-id="72d7e-123">例如，下面介绍了如何为类定义切片， <xref:System.ArraySegment%601> 以方便进行数据操作：</span><span class="sxs-lookup"><span data-stu-id="72d7e-123">For example, here's how you might define slices for the <xref:System.ArraySegment%601> class to allow for convenient data manipulation:</span></span>

```fsharp
open System

type ArraySegment<'TItem> with
    member segment.GetSlice(start, finish) =
        let start = defaultArg start 0
        let finish = defaultArg finish segment.Count
        ArraySegment(segment.Array, segment.Offset + start, finish - start)

let arr = ArraySegment [| 1 .. 10 |]
let slice = arr.[2..5] //[ 3; 4; 5]
```

<span data-ttu-id="72d7e-124">使用和类型的另一个示例 <xref:System.Span%601> <xref:System.ReadOnlySpan%601> ：</span><span class="sxs-lookup"><span data-stu-id="72d7e-124">Another example using the <xref:System.Span%601> and <xref:System.ReadOnlySpan%601> types:</span></span>

```fsharp
open System

type ReadOnlySpan<'T> with
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

type Span<'T> with
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

let printSpan (sp: Span<int>) =
    let arr = sp.ToArray()
    printfn "%A" arr

let sp = [| 1; 2; 3; 4; 5 |].AsSpan()
printSpan sp.[0..] // [|1; 2; 3; 4; 5|]
printSpan sp.[..5] // [|1; 2; 3; 4; 5|]
printSpan sp.[0..3] // [|1; 2; 3|]
printSpan sp.[1..3] // |2; 3|]
```

## <a name="built-in-f-slices-are-end-inclusive"></a><span data-ttu-id="72d7e-125">内置 F # 切片包含结尾</span><span class="sxs-lookup"><span data-stu-id="72d7e-125">Built-in F# slices are end-inclusive</span></span>

<span data-ttu-id="72d7e-126">F # 中的所有内部切片都是结尾的;也就是说，切片中包括上限。</span><span class="sxs-lookup"><span data-stu-id="72d7e-126">All intrinsic slices in F# are end-inclusive; that is, the upper bound is included in the slice.</span></span> <span data-ttu-id="72d7e-127">对于具有起始索引 `x` 和结束索引的给定切片 `y` ，生成的切片将包含 *yth* 值。</span><span class="sxs-lookup"><span data-stu-id="72d7e-127">For a given slice with starting index `x` and ending index `y`, the resulting slice will include the *yth* value.</span></span>

```fsharp
// Define a new list
let xs = [1 .. 10]

printfn "%A" xs.[2..5] // Includes the 5th index
```

## <a name="see-also"></a><span data-ttu-id="72d7e-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="72d7e-128">See also</span></span>

- [<span data-ttu-id="72d7e-129">索引属性</span><span class="sxs-lookup"><span data-stu-id="72d7e-129">Indexed properties</span></span>](./members/indexed-properties.md)

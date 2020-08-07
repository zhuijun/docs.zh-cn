---
title: 序列
description: '如果有大量的有序数据集合，但不一定要使用所有元素，请了解如何使用 F # 序列。'
ms.date: 11/04/2019
ms.openlocfilehash: fa5073f33b9dae52371c249bfb257a2446b4d26a
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855317"
---
# <a name="sequences"></a><span data-ttu-id="6cfd4-103">序列</span><span class="sxs-lookup"><span data-stu-id="6cfd4-103">Sequences</span></span>

<span data-ttu-id="6cfd4-104">*序列*是所有类型的元素的逻辑系列。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-104">A *sequence* is a logical series of elements all of one type.</span></span> <span data-ttu-id="6cfd4-105">如果有大量的有序数据集合，但不一定需要使用所有元素，则序列将特别有用。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-105">Sequences are particularly useful when you have a large, ordered collection of data but do not necessarily expect to use all of the elements.</span></span> <span data-ttu-id="6cfd4-106">单个序列元素只会根据需要计算，因此，在不使用所有元素的情况下，序列可提供比列表更好的性能。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-106">Individual sequence elements are computed only as required, so a sequence can provide better performance than a list in situations in which not all the elements are used.</span></span> <span data-ttu-id="6cfd4-107">序列由 `seq<'T>` 类型表示，该类型是的别名 <xref:System.Collections.Generic.IEnumerable%601> 。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-107">Sequences are represented by the `seq<'T>` type, which is an alias for <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="6cfd4-108">因此，实现接口的任何 .NET 类型 <xref:System.Collections.Generic.IEnumerable%601> 都可用作序列。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-108">Therefore, any .NET type that implements <xref:System.Collections.Generic.IEnumerable%601> interface can be used as a sequence.</span></span> <span data-ttu-id="6cfd4-109">[Seq 模块](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)为涉及序列的操作提供支持。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-109">The [Seq module](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) provides support for manipulations involving sequences.</span></span>

> [!NOTE]
> <span data-ttu-id="6cfd4-110">F # 的 docs.microsoft.com API 参考未完成。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-110">The docs.microsoft.com API reference for F# is not complete.</span></span> <span data-ttu-id="6cfd4-111">如果遇到任何断开的链接，请参阅[F # 核心库文档](https://fsharp.github.io/fsharp-core-docs/)。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-111">If you encounter any broken links, reference [F# Core Library Documentation](https://fsharp.github.io/fsharp-core-docs/) instead.</span></span>

## <a name="sequence-expressions"></a><span data-ttu-id="6cfd4-112">序列表达式</span><span class="sxs-lookup"><span data-stu-id="6cfd4-112">Sequence Expressions</span></span>

<span data-ttu-id="6cfd4-113">*序列表达式*是计算结果为序列的表达式。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-113">A *sequence expression* is an expression that evaluates to a sequence.</span></span> <span data-ttu-id="6cfd4-114">序列表达式可以采用多种形式。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-114">Sequence expressions can take a number of forms.</span></span> <span data-ttu-id="6cfd4-115">最简单的形式是指定一个范围。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-115">The simplest form specifies a range.</span></span> <span data-ttu-id="6cfd4-116">例如， `seq { 1 .. 5 }` 创建一个包含五个元素的序列，包括终结点1和5。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-116">For example, `seq { 1 .. 5 }` creates a sequence that contains five elements, including the endpoints 1 and 5.</span></span> <span data-ttu-id="6cfd4-117">您还可以指定增量 (或减量) 两个双句点之间。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-117">You can also specify an increment (or decrement) between two double periods.</span></span> <span data-ttu-id="6cfd4-118">例如，下面的代码创建10的倍数序列。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-118">For example, the following code creates the sequence of multiples of 10.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1502.fs)]

<span data-ttu-id="6cfd4-119">序列表达式由生成序列值的 F # 表达式组成。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-119">Sequence expressions are made up of F# expressions that produce values of the sequence.</span></span> <span data-ttu-id="6cfd4-120">还可以通过编程方式生成值：</span><span class="sxs-lookup"><span data-stu-id="6cfd4-120">You can also generate values programmatically:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1503.fs)]

<span data-ttu-id="6cfd4-121">前面的示例使用 `->` 运算符，这允许您指定一个表达式，该表达式的值将成为序列的一部分。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-121">The previous sample uses the `->` operator, which allows you to specify an expression whose value will become a part of the sequence.</span></span> <span data-ttu-id="6cfd4-122">仅 `->` 当其后的代码的每个部分都返回值时，才能使用。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-122">You can only use `->` if every part of the code that follows it returns a value.</span></span>

<span data-ttu-id="6cfd4-123">另外，还可以指定 `do` 关键字，其中包含以下选项 `yield` ：</span><span class="sxs-lookup"><span data-stu-id="6cfd4-123">Alternatively, you can specify the `do` keyword, with an optional `yield` that follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1504.fs)]

<span data-ttu-id="6cfd4-124">下面的代码将生成一个坐标对列表，以及一个表示该网格的数组的索引。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-124">The following code generates a list of coordinate pairs along with an index into an array that represents the grid.</span></span> <span data-ttu-id="6cfd4-125">请注意，第一个 `for` 表达式需要 `do` 指定。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-125">Note that the first `for` expression requires a `do` to be specified.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1505.fs)]

<span data-ttu-id="6cfd4-126">`if`序列中使用的表达式是筛选器。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-126">An `if` expression used in a sequence is a filter.</span></span> <span data-ttu-id="6cfd4-127">例如，若要生成一个仅包含质数的序列，假设你有一个 `isprime` 类型的函数 `int -> bool` ，请按如下所示构造序列。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-127">For example, to generate a sequence of only prime numbers, assuming that you have a function `isprime` of type `int -> bool`, construct the sequence as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1506.fs)]

<span data-ttu-id="6cfd4-128">如前文所述， `do` 此处是必需的，因为没有 `else` 与一起的分支 `if` 。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-128">As mentioned previously, `do` is required here because there is no `else` branch that goes with the `if`.</span></span> <span data-ttu-id="6cfd4-129">如果你尝试使用 `->` ，将收到一条错误消息，指出并非所有分支都返回值。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-129">If you try to use `->`, you'll get an error saying that not all branches return a value.</span></span>

## <a name="the-yield-keyword"></a><span data-ttu-id="6cfd4-130">`yield!` 关键字</span><span class="sxs-lookup"><span data-stu-id="6cfd4-130">The `yield!` keyword</span></span>

<span data-ttu-id="6cfd4-131">有时，你可能希望将一系列元素包含在另一个序列中。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-131">Sometimes, you may wish to include a sequence of elements into another sequence.</span></span> <span data-ttu-id="6cfd4-132">若要在另一个序列内包含序列，需要使用 `yield!` 关键字：</span><span class="sxs-lookup"><span data-stu-id="6cfd4-132">To include a sequence within another sequence, you'll need to use the `yield!` keyword:</span></span>

```fsharp
// Repeats '1 2 3 4 5' ten times
seq {
    for _ in 1..10 do
        yield! seq { 1; 2; 3; 4; 5}
}
```

<span data-ttu-id="6cfd4-133">考虑到的另一种方法 `yield!` 是将内部序列平展，然后将其包含在包含序列中。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-133">Another way of thinking of `yield!` is that it flattens an inner sequence and then includes that in the containing sequence.</span></span>

<span data-ttu-id="6cfd4-134">`yield!`在表达式中使用时，所有其他单个值必须使用 `yield` 关键字：</span><span class="sxs-lookup"><span data-stu-id="6cfd4-134">When `yield!` is used in an expression, all other single values must use the `yield` keyword:</span></span>

```fsharp
// Combine repeated values with their values
seq {
    for x in 1..10 do
        yield x
        yield! seq { for i in 1..x -> i}
}
```

<span data-ttu-id="6cfd4-135">仅 `x` 在前面的示例中指定将导致序列不生成值。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-135">Specifying only `x` in the previous example will result in the sequence generating no values.</span></span>

## <a name="examples"></a><span data-ttu-id="6cfd4-136">示例</span><span class="sxs-lookup"><span data-stu-id="6cfd4-136">Examples</span></span>

<span data-ttu-id="6cfd4-137">第一个示例使用包含迭代、筛选器和 yield 的序列表达式来生成数组。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-137">The first example uses a sequence expression that contains an iteration, a filter, and a yield to generate an array.</span></span> <span data-ttu-id="6cfd4-138">此代码会将1到100之间的质数序列输出到控制台。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-138">This code prints a sequence of prime numbers between 1 and 100 to the console.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1507.fs)]

<span data-ttu-id="6cfd4-139">下面的示例创建一个乘法表，其中包含三个元素的元组，每个元素包含两个因素和产品：</span><span class="sxs-lookup"><span data-stu-id="6cfd4-139">The following example creates a multiplication table that consists of tuples of three elements, each consisting of two factors and the product:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1508.fs)]

<span data-ttu-id="6cfd4-140">下面的示例演示 `yield!` 如何使用将各个序列合并为一个最终序列。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-140">The following example demonstrates the use of `yield!` to combine individual sequences into a single final sequence.</span></span> <span data-ttu-id="6cfd4-141">在这种情况下，将在一个递归函数中串联二元树中每个子树的序列，以生成最终序列。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-141">In this case, the sequences for each subtree in a binary tree are concatenated in a recursive function to produce the final sequence.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1509.fs)]

## <a name="using-sequences"></a><span data-ttu-id="6cfd4-142">使用序列</span><span class="sxs-lookup"><span data-stu-id="6cfd4-142">Using Sequences</span></span>

<span data-ttu-id="6cfd4-143">序列支持许多与[列表](lists.md)相同的函数。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-143">Sequences support many of the same functions as [lists](lists.md).</span></span> <span data-ttu-id="6cfd4-144">序列还支持通过使用键生成函数进行分组和计数等操作。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-144">Sequences also support operations such as grouping and counting by using key-generating functions.</span></span> <span data-ttu-id="6cfd4-145">序列还支持用于提取个子序列的更广泛的函数。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-145">Sequences also support more diverse functions for extracting subsequences.</span></span>

<span data-ttu-id="6cfd4-146">许多数据类型（例如列表、数组、集和映射）都是隐式的，因为它们是可枚举的集合。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-146">Many data types, such as lists, arrays, sets, and maps are implicitly sequences because they are enumerable collections.</span></span> <span data-ttu-id="6cfd4-147">采用序列作为参数的函数除了实现的任何 .NET 数据类型外，还适用于任何常见的 F # 数据类型 `System.Collections.Generic.IEnumerable<'T>` 。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-147">A function that takes a sequence as an argument works with any of the common F# data types, in addition to any .NET data type that implements `System.Collections.Generic.IEnumerable<'T>`.</span></span> <span data-ttu-id="6cfd4-148">将此与采用列表作为参数的函数相反，只能采用列表。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-148">Contrast this to a function that takes a list as an argument, which can only take lists.</span></span> <span data-ttu-id="6cfd4-149">类型 `seq<'T>` 是的类型缩写 `IEnumerable<'T>` 。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-149">The type `seq<'T>` is a type abbreviation for `IEnumerable<'T>`.</span></span> <span data-ttu-id="6cfd4-150">这意味着，实现泛型的任何类型 `System.Collections.Generic.IEnumerable<'T>` （包括数组、列表、集和 F # 中的映射）以及大多数 .net 集合类型都与类型兼容， `seq` 可在需要序列的任何位置使用。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-150">This means that any type that implements the generic `System.Collections.Generic.IEnumerable<'T>`, which includes arrays, lists, sets, and maps in F#, and also most .NET collection types, is compatible with the `seq` type and can be used wherever a sequence is expected.</span></span>

## <a name="module-functions"></a><span data-ttu-id="6cfd4-151">模块函数</span><span class="sxs-lookup"><span data-stu-id="6cfd4-151">Module Functions</span></span>

<span data-ttu-id="6cfd4-152">[Fsharp.core 命名空间](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f)中的[Seq 模块](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)包含用于处理序列的函数。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-152">The [Seq module](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) in the [Microsoft.FSharp.Collections namespace](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f) contains functions for working with sequences.</span></span> <span data-ttu-id="6cfd4-153">这些函数也适用于列表、数组、映射和集，因为这些类型都是可枚举的，因此可以视为序列。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-153">These functions work with lists, arrays, maps, and sets as well, because all of those types are enumerable, and therefore can be treated as sequences.</span></span>

## <a name="creating-sequences"></a><span data-ttu-id="6cfd4-154">创建序列</span><span class="sxs-lookup"><span data-stu-id="6cfd4-154">Creating Sequences</span></span>

<span data-ttu-id="6cfd4-155">您可以使用序列表达式（如前文所述）或使用特定函数来创建序列。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-155">You can create sequences by using sequence expressions, as described previously, or by using certain functions.</span></span>

<span data-ttu-id="6cfd4-156">您可以通过使用[序列 empty](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59)创建一个空序列，也可以通过使用[seq. singleton](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7)创建只具有一个指定元素的序列。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-156">You can create an empty sequence by using [Seq.empty](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59), or you can create a sequence of just one specified element by using [Seq.singleton](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet9.fs)]

<span data-ttu-id="6cfd4-157">您可以使用[Seq.init](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576)创建使用您提供的函数为其创建元素的序列。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-157">You can use [Seq.init](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576) to create a sequence for which the elements are created by using a function that you provide.</span></span> <span data-ttu-id="6cfd4-158">还可为序列提供大小。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-158">You also provide a size for the sequence.</span></span> <span data-ttu-id="6cfd4-159">此函数与[List.init](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83)类似，只是在遍历序列之前不会创建元素。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-159">This function is just like [List.init](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83), except that the elements are not created until you iterate through the sequence.</span></span> <span data-ttu-id="6cfd4-160">下面的代码演示如何使用 `Seq.init` 。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-160">The following code illustrates the use of `Seq.init`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet10.fs)]

<span data-ttu-id="6cfd4-161">输出为</span><span class="sxs-lookup"><span data-stu-id="6cfd4-161">The output is</span></span>

```console
0 10 20 30 40
```

<span data-ttu-id="6cfd4-162">通过使用[list.ofarray](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99)和[array.oflist&#60; 不&#62; 函数](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d)，你可以从数组和列表创建序列。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-162">By using [Seq.ofArray](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99) and [Seq.ofList&#60;'T&#62; Function](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d), you can create sequences from arrays and lists.</span></span> <span data-ttu-id="6cfd4-163">不过，还可以使用转换运算符将数组和列表转换为序列。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-163">However, you can also convert arrays and lists to sequences by using a cast operator.</span></span> <span data-ttu-id="6cfd4-164">下面的代码演示了这两种方法。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-164">Both techniques are shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet11.fs)]

<span data-ttu-id="6cfd4-165">通过使用[Seq](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334)，你可以从弱类型集合中创建一个序列，如中定义的集合 `System.Collections` 。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-165">By using [Seq.cast](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334), you can create a sequence from a weakly typed collection, such as those defined in `System.Collections`.</span></span> <span data-ttu-id="6cfd4-166">此类弱类型集合具有元素类型 `System.Object` ，并使用非泛型类型进行枚举 `System.Collections.Generic.IEnumerable&#96;1` 。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-166">Such weakly typed collections have the element type `System.Object` and are enumerated by using the non-generic `System.Collections.Generic.IEnumerable&#96;1` type.</span></span> <span data-ttu-id="6cfd4-167">下面的代码演示 `Seq.cast` 如何使用将转换为 `System.Collections.ArrayList` 序列。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-167">The following code illustrates the use of `Seq.cast` to convert an `System.Collections.ArrayList` into a sequence.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet12.fs)]

<span data-ttu-id="6cfd4-168">可以通过使用[Seq.initInfinite](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef)函数来定义无限序列。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-168">You can define infinite sequences by using the [Seq.initInfinite](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef) function.</span></span> <span data-ttu-id="6cfd4-169">对于这种序列，你提供了一个函数，该函数从元素的索引生成每个元素。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-169">For such a sequence, you provide a function that generates each element from the index of the element.</span></span> <span data-ttu-id="6cfd4-170">由于延迟计算，可能会出现无限序列;根据需要通过调用指定的函数来创建元素。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-170">Infinite sequences are possible because of lazy evaluation; elements are created as needed by calling the function that you specify.</span></span> <span data-ttu-id="6cfd4-171">下面的代码示例生成一个无限的浮点数序列，在此示例中，为连续整数的 reciprocals 序列。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-171">The following code example produces an infinite sequence of floating point numbers, in this case the alternating series of reciprocals of squares of successive integers.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet13.fs)]

<span data-ttu-id="6cfd4-172">[Seq：](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21)从采用状态并将其转换为生成序列中每个后续元素的计算函数生成序列。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-172">[Seq.unfold](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21) generates a sequence from a computation function that takes a state and transforms it to produce each subsequent element in the sequence.</span></span> <span data-ttu-id="6cfd4-173">状态只是用于计算每个元素的值，并且可以在计算每个元素时进行更改。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-173">The state is just a value that is used to compute each element, and can change as each element is computed.</span></span> <span data-ttu-id="6cfd4-174">的第二个参数 `Seq.unfold` 是用于启动序列的初始值。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-174">The second argument to `Seq.unfold` is the initial value that is used to start the sequence.</span></span> <span data-ttu-id="6cfd4-175">`Seq.unfold`将选项类型用于状态，这使你可以通过返回值来终止序列 `None` 。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-175">`Seq.unfold` uses an option type for the state, which enables you to terminate the sequence by returning the `None` value.</span></span> <span data-ttu-id="6cfd4-176">下面的代码演示了两个序列的示例， `seq1` 以及 `fib` 由操作生成的 `unfold` 。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-176">The following code shows two examples of sequences, `seq1` and `fib`, that are generated by an `unfold` operation.</span></span> <span data-ttu-id="6cfd4-177">第一个 `seq1` 是，它是数字最多为20的简单序列。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-177">The first, `seq1`, is just a simple sequence with numbers up to 20.</span></span> <span data-ttu-id="6cfd4-178">第二个 `fib` 使用 `unfold` 来计算斐波那契序列。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-178">The second, `fib`, uses `unfold` to compute the Fibonacci sequence.</span></span> <span data-ttu-id="6cfd4-179">因为波那契序列中的每个元素都是前两个斐波那契数的总和，所以，状态值是包含序列中前两个数字的元组。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-179">Because each element in the Fibonacci sequence is the sum of the previous two Fibonacci numbers, the state value is a tuple that consists of the previous two numbers in the sequence.</span></span> <span data-ttu-id="6cfd4-180">初始值为 `(1,1)` ，序列中的前两个数字。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-180">The initial value is `(1,1)`, the first two numbers in the sequence.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet14.fs)]

<span data-ttu-id="6cfd4-181">输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="6cfd4-181">The output is as follows:</span></span>

```console
The sequence seq1 contains numbers from 0 to 20.

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20

The sequence fib contains Fibonacci numbers.

2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

<span data-ttu-id="6cfd4-182">下面的代码示例使用此处所述的许多序列模块函数来生成和计算无限序列的值。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-182">The following code is an example that uses many of the sequence module functions described here to generate and compute the values of infinite sequences.</span></span> <span data-ttu-id="6cfd4-183">此代码可能需要几分钟才能运行。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-183">The code might take a few minutes to run.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet15.fs)]

## <a name="searching-and-finding-elements"></a><span data-ttu-id="6cfd4-184">搜索和查找元素</span><span class="sxs-lookup"><span data-stu-id="6cfd4-184">Searching and Finding Elements</span></span>

<span data-ttu-id="6cfd4-185">序列支持可用于列表的功能[： seq.](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1) [array.exists2](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565)， [findIndex](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3)，seq [Seq.find](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8)， [seq，](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d) [tryFind](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47)，，array.tryfindindex. [Seq.tryFindIndex](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a)。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-185">Sequences support functionality available with lists: [Seq.exists](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1), [Seq.exists2](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565), [Seq.find](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8), [Seq.findIndex](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3), [Seq.pick](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d), [Seq.tryFind](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47), and [Seq.tryFindIndex](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a).</span></span> <span data-ttu-id="6cfd4-186">可用于序列的这些函数的版本仅计算到所搜索的元素的顺序。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-186">The versions of these functions that are available for sequences evaluate the sequence only up to the element that is being searched for.</span></span> <span data-ttu-id="6cfd4-187">有关示例，请参阅[列表](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d)。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-187">For examples, see [Lists](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d).</span></span>

## <a name="obtaining-subsequences"></a><span data-ttu-id="6cfd4-188">获取个子序列</span><span class="sxs-lookup"><span data-stu-id="6cfd4-188">Obtaining Subsequences</span></span>

<span data-ttu-id="6cfd4-189">[Seq. filter](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770)和[seq。 choose](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395)类似于列表可用的相应函数，但在计算序列元素之前，不会发生筛选和选择。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-189">[Seq.filter](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770) and [Seq.choose](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395) are like the corresponding functions that are available for lists, except that the filtering and choosing does not occur until the sequence elements are evaluated.</span></span>

<span data-ttu-id="6cfd4-190">[Seq](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244)从另一个序列创建序列，但将序列限制为指定数量的元素。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-190">[Seq.truncate](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244) creates a sequence from another sequence, but limits the sequence to a specified number of elements.</span></span> <span data-ttu-id="6cfd4-191">[Seq。 take 会](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596)创建一个新序列，该序列只包含序列开头的指定数量的元素。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-191">[Seq.take](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596) creates a new sequence that contains only a specified number of elements from the start of a sequence.</span></span> <span data-ttu-id="6cfd4-192">如果序列中的元素少于您指定要执行的元素， `Seq.take` 则将引发 `System.InvalidOperationException` 。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-192">If there are fewer elements in the sequence than you specify to take, `Seq.take` throws a `System.InvalidOperationException`.</span></span> <span data-ttu-id="6cfd4-193">与之间的区别在于， `Seq.take` `Seq.truncate` `Seq.truncate` 如果元素数少于指定的数目，则不会产生错误。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-193">The difference between `Seq.take` and `Seq.truncate` is that `Seq.truncate` does not produce an error if the number of elements is fewer than the number you specify.</span></span>

<span data-ttu-id="6cfd4-194">下面的代码演示了和之间的行为 `Seq.truncate` `Seq.take` 。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-194">The following code shows the behavior of and differences between `Seq.truncate` and `Seq.take`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet16.fs)]

<span data-ttu-id="6cfd4-195">出现错误之前的输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-195">The output, before the error occurs, is as follows.</span></span>

```console
1 4 9 16 25
1 4 9 16 25 36 49 64 81 100
1 4 9 16 25
1 4 9 16 25 36 49 64 81 100
```

<span data-ttu-id="6cfd4-196">通过使用[takeWhile](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92)，你可以 (布尔函数指定一个谓词函数) 并从另一个序列中创建一个序列，该序列由该谓词的原始序列的那些元素组成 `true` ，但在该谓词返回的第一个元素之前停止 `false` 。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-196">By using [Seq.takeWhile](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92), you can specify a predicate function (a Boolean function) and create a sequence from another sequence made up of those elements of the original sequence for which the predicate is `true`, but stop before the first element for which the predicate returns `false`.</span></span> <span data-ttu-id="6cfd4-197">[Seq： skip](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1)返回一个序列，该序列跳过另一个序列的指定数目的第一个元素，并返回剩余的元素。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-197">[Seq.skip](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1) returns a sequence that skips a specified number of the first elements of another sequence and returns the remaining elements.</span></span> <span data-ttu-id="6cfd4-198">[SkipWhile](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16)返回一个序列，该序列在谓词返回的情况下跳过另一个序列的第一个元素 `true` ，然后返回剩余的元素（从该谓词返回的第一个元素开始） `false` 。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-198">[Seq.skipWhile](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16) returns a sequence that skips the first elements of another sequence as long as the predicate returns `true`, and then returns the remaining elements, starting with the first element for which the predicate returns `false`.</span></span>

<span data-ttu-id="6cfd4-199">下面的代码示例演示了、和的行为 `Seq.takeWhile` `Seq.skip` `Seq.skipWhile` 。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-199">The following code example illustrates the behavior of and differences between `Seq.takeWhile`, `Seq.skip`, and `Seq.skipWhile`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet17.fs)]

<span data-ttu-id="6cfd4-200">输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-200">The output is as follows.</span></span>

```console
1 4 9
36 49 64 81 100
16 25 36 49 64 81 100
```

## <a name="transforming-sequences"></a><span data-ttu-id="6cfd4-201">转换序列</span><span class="sxs-lookup"><span data-stu-id="6cfd4-201">Transforming Sequences</span></span>

<span data-ttu-id="6cfd4-202">[Seq。](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1)将创建一个新序列，其中输入序列的连续元素分为元组。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-202">[Seq.pairwise](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1) creates a new sequence in which successive elements of the input sequence are grouped into tuples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet18.fs)]

<span data-ttu-id="6cfd4-203">[Seq](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744)类似 `Seq.pairwise` ，只是它会生成一系列数组，其中包含序列中的*窗口*)  (相邻元素的副本。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-203">[Seq.windowed](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744) is like `Seq.pairwise`, except that instead of producing a sequence of tuples, it produces a sequence of arrays that contain copies of adjacent elements (a *window*) from the sequence.</span></span> <span data-ttu-id="6cfd4-204">指定每个数组中所需的相邻元素的数目。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-204">You specify the number of adjacent elements you want in each array.</span></span>

<span data-ttu-id="6cfd4-205">以下代码示例演示了 `Seq.windowed` 的用法。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-205">The following code example demonstrates the use of `Seq.windowed`.</span></span> <span data-ttu-id="6cfd4-206">在此示例中，窗口中的元素数为3。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-206">In this case the number of elements in the window is 3.</span></span> <span data-ttu-id="6cfd4-207">该示例使用 `printSeq` 上一个代码示例中定义的。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-207">The example uses `printSeq`, which is defined in the previous code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet180.fs)]

<span data-ttu-id="6cfd4-208">输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-208">The output is as follows.</span></span>

<span data-ttu-id="6cfd4-209">初始顺序：</span><span class="sxs-lookup"><span data-stu-id="6cfd4-209">Initial sequence:</span></span>

```console
1.0 1.5 2.0 1.5 1.0 1.5

Windows of length 3:
[|1.0; 1.5; 2.0|] [|1.5; 2.0; 1.5|] [|2.0; 1.5; 1.0|] [|1.5; 1.0; 1.5|]

Moving average:
1.5 1.666666667 1.5 1.333333333
```

## <a name="operations-with-multiple-sequences"></a><span data-ttu-id="6cfd4-210">具有多个序列的操作</span><span class="sxs-lookup"><span data-stu-id="6cfd4-210">Operations with Multiple Sequences</span></span>

<span data-ttu-id="6cfd4-211">[Seq.zip](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4)和[Seq.zip3](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16)接受两个或三个序列，并生成元组序列。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-211">[Seq.zip](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4) and [Seq.zip3](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16) take two or three sequences and produce a sequence of tuples.</span></span> <span data-ttu-id="6cfd4-212">这些函数类似于[列表](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d)可用的对应函数。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-212">These functions are like the corresponding functions available for [lists](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d).</span></span> <span data-ttu-id="6cfd4-213">没有相应的功能可将一个序列分隔成两个或更多个序列。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-213">There is no corresponding functionality to separate one sequence into two or more sequences.</span></span> <span data-ttu-id="6cfd4-214">如果需要为序列使用此功能，请将序列转换为列表，并使用[list。](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21)</span><span class="sxs-lookup"><span data-stu-id="6cfd4-214">If you need this functionality for a sequence, convert the sequence to a list and use [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span></span>

## <a name="sorting-comparing-and-grouping"></a><span data-ttu-id="6cfd4-215">排序、比较和分组</span><span class="sxs-lookup"><span data-stu-id="6cfd4-215">Sorting, Comparing, and Grouping</span></span>

<span data-ttu-id="6cfd4-216">列表支持的排序函数也适用于序列。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-216">The sorting functions supported for lists also work with sequences.</span></span> <span data-ttu-id="6cfd4-217">这包括[seq](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e)和[sortBy](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f)。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-217">This includes [Seq.sort](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e) and [Seq.sortBy](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f).</span></span> <span data-ttu-id="6cfd4-218">这些函数循环访问整个序列。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-218">These functions iterate through the whole sequence.</span></span>

<span data-ttu-id="6cfd4-219">使用[seq.comparewith](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f)函数比较两个序列。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-219">You compare two sequences by using the [Seq.compareWith](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f) function.</span></span> <span data-ttu-id="6cfd4-220">函数依次比较连续的元素，并在遇到第一个不相等对时停止。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-220">The function compares successive elements in turn, and stops when it encounters the first unequal pair.</span></span> <span data-ttu-id="6cfd4-221">任何其他元素不参与比较。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-221">Any additional elements do not contribute to the comparison.</span></span>

<span data-ttu-id="6cfd4-222">以下代码显示了 `Seq.compareWith` 的用法。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-222">The following code shows the use of `Seq.compareWith`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet19.fs)]

<span data-ttu-id="6cfd4-223">在前面的代码中，只计算并检查第一个元素，结果为-1。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-223">In the previous code, only the first element is computed and examined, and the result is -1.</span></span>

<span data-ttu-id="6cfd4-224">[CountBy](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f)采用一个函数，该函数为每个元素生成一个名为*key*的值。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-224">[Seq.countBy](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f) takes a function that generates a value called a *key* for each element.</span></span> <span data-ttu-id="6cfd4-225">通过对每个元素调用此函数，为每个元素生成一个密钥。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-225">A key is generated for each element by calling this function on each element.</span></span> <span data-ttu-id="6cfd4-226">`Seq.countBy`然后返回一个序列，其中包含键值，以及生成每个密钥值的元素数的计数。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-226">`Seq.countBy` then returns a sequence that contains the key values, and a count of the number of elements that generated each value of the key.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet201.fs)]

<span data-ttu-id="6cfd4-227">输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-227">The output is as follows.</span></span>

```console
(1, 34) (2, 33) (0, 33)
```

<span data-ttu-id="6cfd4-228">前面的输出显示，原始序列中有34个元素，这些元素生成了键1，33值生成了键2，并显示了生成密钥0的33值。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-228">The previous output shows that there were 34 elements of the original sequence that produced the key 1, 33 values that produced the key 2, and 33 values that produced the key 0.</span></span>

<span data-ttu-id="6cfd4-229">可以通过调用序列[groupBy](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd)对序列中的元素进行分组。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-229">You can group elements of a sequence by calling [Seq.groupBy](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd).</span></span> <span data-ttu-id="6cfd4-230">`Seq.groupBy`采用一个序列和一个从元素生成键的函数。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-230">`Seq.groupBy` takes a sequence and a function that generates a key from an element.</span></span> <span data-ttu-id="6cfd4-231">函数在序列的每个元素上执行。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-231">The function is executed on each element of the sequence.</span></span> <span data-ttu-id="6cfd4-232">`Seq.groupBy`返回一个元组序列，其中每个元组的第一个元素是键，第二个元素是生成该键的元素的序列。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-232">`Seq.groupBy` returns a sequence of tuples, where the first element of each tuple is the key and the second is a sequence of elements that produce that key.</span></span>

<span data-ttu-id="6cfd4-233">下面的代码示例演示 `Seq.groupBy` 如何使用将编号从1到100的序列分为三个组，这些组具有非重复键值0、1和2。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-233">The following code example shows the use of `Seq.groupBy` to partition the sequence of numbers from 1 to 100 into three groups that have the distinct key values 0, 1, and 2.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet202.fs)]

<span data-ttu-id="6cfd4-234">输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-234">The output is as follows.</span></span>

```console
(1, seq [1; 4; 7; 10; ...]) (2, seq [2; 5; 8; 11; ...]) (0, seq [3; 6; 9; 12; ...])
```

<span data-ttu-id="6cfd4-235">通过调用 Seq，可以创建一个消除重复元素的序列[。](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401)</span><span class="sxs-lookup"><span data-stu-id="6cfd4-235">You can create a sequence that eliminates duplicate elements by calling [Seq.distinct](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401).</span></span> <span data-ttu-id="6cfd4-236">或者，可以使用[seq.distinctby](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75)，它采用在每个元素上调用的键生成函数。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-236">Or you can use [Seq.distinctBy](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75), which takes a key-generating function to be called on each element.</span></span> <span data-ttu-id="6cfd4-237">生成的序列包含具有唯一键的原始序列的元素;随后将丢弃向早期元素生成重复键的元素。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-237">The resulting sequence contains elements of the original sequence that have unique keys; later elements that produce a duplicate key to an earlier element are discarded.</span></span>

<span data-ttu-id="6cfd4-238">下面的代码示例阐释了的用法 `Seq.distinct` 。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-238">The following code example illustrates the use of `Seq.distinct`.</span></span> <span data-ttu-id="6cfd4-239">`Seq.distinct`通过生成表示二进制数字的序列，并显示唯一不同的元素是0和1来演示。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-239">`Seq.distinct` is demonstrated by generating sequences that represent binary numbers, and then showing that the only distinct elements are 0 and 1.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet22.fs)]

<span data-ttu-id="6cfd4-240">下面的代码演示了 `Seq.distinctBy` 一个序列，该序列包含负数和正数，并使用绝对值函数作为键生成函数。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-240">The following code demonstrates `Seq.distinctBy` by starting with a sequence that contains negative and positive numbers and using the absolute value function as the key-generating function.</span></span> <span data-ttu-id="6cfd4-241">生成的序列缺少与序列中的负数相对应的所有正数，因为负数出现在序列的前面，因此选择了，而不是具有相同绝对值或键的正数。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-241">The resulting sequence is missing all the positive numbers that correspond to the negative numbers in the sequence, because the negative numbers appear earlier in the sequence and therefore are selected instead of the positive numbers that have the same absolute value, or key.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet23.fs)]

## <a name="readonly-and-cached-sequences"></a><span data-ttu-id="6cfd4-242">Readonly 和缓存序列</span><span class="sxs-lookup"><span data-stu-id="6cfd4-242">Readonly and Cached Sequences</span></span>

<span data-ttu-id="6cfd4-243">[Seq readonly](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7)创建序列的只读副本。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-243">[Seq.readonly](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7) creates a read-only copy of a sequence.</span></span> <span data-ttu-id="6cfd4-244">`Seq.readonly`当你具有读写集合（如数组），并且你不希望修改原始集合时，此方法非常有用。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-244">`Seq.readonly` is useful when you have a read-write collection, such as an array, and you do not want to modify the original collection.</span></span> <span data-ttu-id="6cfd4-245">此函数可用于保留数据封装。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-245">This function can be used to preserve data encapsulation.</span></span> <span data-ttu-id="6cfd4-246">在下面的代码示例中，创建了一个包含数组的类型。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-246">In the following code example, a type that contains an array is created.</span></span> <span data-ttu-id="6cfd4-247">属性将公开数组，但不返回数组，而是返回从数组使用创建的序列 `Seq.readonly` 。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-247">A property exposes the array, but instead of returning an array, it returns a sequence that is created from the array by using `Seq.readonly`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet24.fs)]

<span data-ttu-id="6cfd4-248">[Seq：](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0)创建序列的存储版本。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-248">[Seq.cache](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0) creates a stored version of a sequence.</span></span> <span data-ttu-id="6cfd4-249">使用 `Seq.cache` 可以避免重新计算序列，或者当你有多个使用序列的线程时，但必须确保每个元素仅被处理一次。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-249">Use `Seq.cache` to avoid reevaluation of a sequence, or when you have multiple threads that use a sequence, but you must make sure that each element is acted upon only one time.</span></span> <span data-ttu-id="6cfd4-250">如果有多个线程正在使用的序列，则可以让一个线程枚举并计算原始序列的值，其余线程可以使用缓存的序列。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-250">When you have a sequence that is being used by multiple threads, you can have one thread that enumerates and computes the values for the original sequence, and remaining threads can use the cached sequence.</span></span>

## <a name="performing-computations-on-sequences"></a><span data-ttu-id="6cfd4-251">对序列执行计算</span><span class="sxs-lookup"><span data-stu-id="6cfd4-251">Performing Computations on Sequences</span></span>

<span data-ttu-id="6cfd4-252">简单的算术运算类似于列表的操作，如[seq](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8)、seq、 [sum](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a)、 [averageBy](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8)、 [sumBy](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1)等。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-252">Simple arithmetic operations are like those of lists, such as [Seq.average](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8), [Seq.sum](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a), [Seq.averageBy](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8), [Seq.sumBy](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1), and so on.</span></span>

<span data-ttu-id="6cfd4-253">[序列摺](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3)、 [seq、化简](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9)和[seq。扫描](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e)类似于列表可用的对应函数。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-253">[Seq.fold](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3), [Seq.reduce](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9), and [Seq.scan](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e) are like the corresponding functions that are available for lists.</span></span> <span data-ttu-id="6cfd4-254">序列支持列出支持的这些功能的一部分完全不同。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-254">Sequences support a subset of the full variations of these functions that lists support.</span></span> <span data-ttu-id="6cfd4-255">有关详细信息和示例，请参阅[列表](lists.md)。</span><span class="sxs-lookup"><span data-stu-id="6cfd4-255">For more information and examples, see [Lists](lists.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6cfd4-256">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6cfd4-256">See also</span></span>

- [<span data-ttu-id="6cfd4-257">F# 语言参考</span><span class="sxs-lookup"><span data-stu-id="6cfd4-257">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="6cfd4-258">F# 类型</span><span class="sxs-lookup"><span data-stu-id="6cfd4-258">F# Types</span></span>](fsharp-types.md)

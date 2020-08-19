---
title: 数组
description: '了解如何在 F # 编程语言中创建和使用数组。'
ms.date: 08/13/2020
ms.openlocfilehash: 93d524046ff93a7f1b04e72d580d9d0e1360ba0b
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558876"
---
# <a name="arrays"></a><span data-ttu-id="5f1d7-103">数组</span><span class="sxs-lookup"><span data-stu-id="5f1d7-103">Arrays</span></span>

<span data-ttu-id="5f1d7-104">数组是固定大小的、从零开始、可变的连续数据元素集合，这些元素属于同一类型。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-104">Arrays are fixed-size, zero-based, mutable collections of consecutive data elements that are all of the same type.</span></span>

## <a name="create-arrays"></a><span data-ttu-id="5f1d7-105">创建数组</span><span class="sxs-lookup"><span data-stu-id="5f1d7-105">Create arrays</span></span>

<span data-ttu-id="5f1d7-106">可以通过多种方式创建数组。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-106">You can create arrays in several ways.</span></span> <span data-ttu-id="5f1d7-107">您可以通过在和之间列出连续的值并 `[|` 用分号分隔，来创建一个小型数组 `|]` ，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-107">You can create a small array by listing consecutive values between `[|` and `|]` and separated by semicolons, as shown in the following examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet1.fs)]

<span data-ttu-id="5f1d7-108">您还可以将每个元素放在单独的行上，在这种情况下，分号分隔符是可选的。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-108">You can also put each element on a separate line, in which case the semicolon separator is optional.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet2.fs)]

<span data-ttu-id="5f1d7-109">数组元素的类型是从使用的文本中推断出来的，并且必须一致。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-109">The type of the array elements is inferred from the literals used and must be consistent.</span></span> <span data-ttu-id="5f1d7-110">下面的代码会导致错误，因为1.0 为 float，2和3是整数。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-110">The following code causes an error because 1.0 is a float and 2 and 3 are integers.</span></span>

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

<span data-ttu-id="5f1d7-111">您还可以使用序列表达式来创建数组。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-111">You can also use sequence expressions to create arrays.</span></span> <span data-ttu-id="5f1d7-112">下面的示例创建一个从1到10的整数的平方的数组。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-112">Following is an example that creates an array of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet3.fs)]

<span data-ttu-id="5f1d7-113">若要创建将所有元素都初始化为零的数组，请使用 `Array.zeroCreate` 。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-113">To create an array in which all the elements are initialized to zero, use `Array.zeroCreate`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet4.fs)]

## <a name="access-elements"></a><span data-ttu-id="5f1d7-114">访问元素</span><span class="sxs-lookup"><span data-stu-id="5f1d7-114">Access elements</span></span>

<span data-ttu-id="5f1d7-115">您可以使用点运算符 (`.`) 和括号 (和) 来访问数组 `[` 元素 `]` 。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-115">You can access array elements by using a dot operator (`.`) and brackets (`[` and `]`).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet5.fs)]

<span data-ttu-id="5f1d7-116">数组索引从0开始。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-116">Array indexes start at 0.</span></span>

<span data-ttu-id="5f1d7-117">您还可以通过使用切片表示法来访问数组元素，这使您能够指定数组的子范围。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-117">You can also access array elements by using slice notation, which enables you to specify a subrange of the array.</span></span> <span data-ttu-id="5f1d7-118">下面是切片表示法的示例。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-118">Examples of slice notation follow.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet51.fs)]

<span data-ttu-id="5f1d7-119">使用切片表示法时，将创建数组的新副本。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-119">When slice notation is used, a new copy of the array is created.</span></span>

## <a name="array-types-and-modules"></a><span data-ttu-id="5f1d7-120">数组类型和模块</span><span class="sxs-lookup"><span data-stu-id="5f1d7-120">Array types and modules</span></span>

<span data-ttu-id="5f1d7-121">所有 F # 数组的类型都是 .NET Framework 类型 <xref:System.Array?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-121">The type of all F# arrays is the .NET Framework type <xref:System.Array?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5f1d7-122">因此，F # 数组支持中所有可用的功能 <xref:System.Array?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-122">Therefore, F# arrays support all the functionality available in <xref:System.Array?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="5f1d7-123">[ `Array` 模块](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html)支持对一维数组进行的操作。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-123">The [`Array` module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html) supports operations on one-dimensional arrays.</span></span> <span data-ttu-id="5f1d7-124">模块 `Array2D` 、 `Array3D` 和 `Array4D` 包含的函数分别支持对2、3和4维数组的操作。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-124">The modules `Array2D`, `Array3D`, and `Array4D` contain functions that support operations on arrays of two, three, and four dimensions, respectively.</span></span> <span data-ttu-id="5f1d7-125">可以使用创建秩大于四的数组 <xref:System.Array?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-125">You can create arrays of rank greater than four by using <xref:System.Array?displayProperty=nameWithType>.</span></span>

### <a name="simple-functions"></a><span data-ttu-id="5f1d7-126">简单函数</span><span class="sxs-lookup"><span data-stu-id="5f1d7-126">Simple functions</span></span>

<span data-ttu-id="5f1d7-127">[`Array.get`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#get) 获取元素。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-127">[`Array.get`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#get) gets an element.</span></span> <span data-ttu-id="5f1d7-128">[`Array.length`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#length) 给出数组的长度。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-128">[`Array.length`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#length) gives the length of an array.</span></span> <span data-ttu-id="5f1d7-129">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) 将元素设置为指定值。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-129">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) sets an element to a specified value.</span></span> <span data-ttu-id="5f1d7-130">下面的代码示例阐释了这些函数的用法。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-130">The following code example illustrates the use of these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet9.fs)]

<span data-ttu-id="5f1d7-131">输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-131">The output is as follows.</span></span>

```console
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a><span data-ttu-id="5f1d7-132">创建数组的函数</span><span class="sxs-lookup"><span data-stu-id="5f1d7-132">Functions that create arrays</span></span>

<span data-ttu-id="5f1d7-133">多个函数创建数组，无需现有数组。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-133">Several functions create arrays without requiring an existing array.</span></span> <span data-ttu-id="5f1d7-134">[`Array.empty`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#empty) 创建不包含任何元素的新数组。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-134">[`Array.empty`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#empty) creates a new array that does not contain any elements.</span></span> <span data-ttu-id="5f1d7-135">[`Array.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#create) 创建指定大小的数组，并将所有元素设置为提供的值。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-135">[`Array.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#create) creates an array of a specified size and sets all the elements to provided values.</span></span> <span data-ttu-id="5f1d7-136">[`Array.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#init) 在给定维度和函数以生成元素的情况下，创建一个数组。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-136">[`Array.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#init) creates an array, given a dimension and a function to generate the elements.</span></span> <span data-ttu-id="5f1d7-137">[`Array.zeroCreate`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zeroCreate) 创建一个数组，其中所有元素都初始化为数组的类型的零值。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-137">[`Array.zeroCreate`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zeroCreate) creates an array in which all the elements are initialized to the zero value for the array's type.</span></span> <span data-ttu-id="5f1d7-138">下面的代码演示了这些函数。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-138">The following code demonstrates these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet91.fs)]

<span data-ttu-id="5f1d7-139">输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-139">The output is as follows.</span></span>

```console
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

<span data-ttu-id="5f1d7-140">[`Array.copy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#copy) 创建一个新数组，其中包含从现有数组中复制的元素。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-140">[`Array.copy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#copy) creates a new array that contains elements that are copied from an existing array.</span></span> <span data-ttu-id="5f1d7-141">请注意，副本是一个浅表复制，这意味着，如果元素类型为引用类型，则仅复制引用，而不复制基础对象。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-141">Note that the copy is a shallow copy, which means that if the element type is a reference type, only the reference is copied, not the underlying object.</span></span> <span data-ttu-id="5f1d7-142">下面的代码示例阐释了这一点。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-142">The following code example illustrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet11.fs)]

<span data-ttu-id="5f1d7-143">上述代码的输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="5f1d7-143">The output of the preceding code is as follows:</span></span>

```console
[|Test1; Test2; |]
[|; Test2; |]
```

<span data-ttu-id="5f1d7-144">字符串 `Test1` 仅出现在第一个数组中，因为创建新元素的操作会覆盖中的引用， `firstArray` 但不会影响对仍存在于中的空字符串的原始引用 `secondArray` 。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-144">The string `Test1` appears only in the first array because the operation of creating a new element overwrites the reference in `firstArray` but does not affect the original reference to an empty string that is still present in `secondArray`.</span></span> <span data-ttu-id="5f1d7-145">此字符串 `Test2` 出现在两个数组中 `Insert` ，因为对该类型的操作 <xref:System.Text.StringBuilder?displayProperty=nameWithType> 会影响 <xref:System.Text.StringBuilder?displayProperty=nameWithType> 在这两个数组中引用的基础对象。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-145">The string `Test2` appears in both arrays because the `Insert` operation on the <xref:System.Text.StringBuilder?displayProperty=nameWithType> type affects the underlying <xref:System.Text.StringBuilder?displayProperty=nameWithType> object, which is referenced in both arrays.</span></span>

<span data-ttu-id="5f1d7-146">[`Array.sub`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sub) 从数组的子范围生成新数组。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-146">[`Array.sub`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sub) generates a new array from a subrange of an array.</span></span> <span data-ttu-id="5f1d7-147">可以通过提供起始索引和长度来指定子范围。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-147">You specify the subrange by providing the starting index and the length.</span></span> <span data-ttu-id="5f1d7-148">以下代码演示了 `Array.sub` 的用法。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-148">The following code demonstrates the use of `Array.sub`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet12.fs)]

<span data-ttu-id="5f1d7-149">输出显示子数组从元素5开始，包含10个元素。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-149">The output shows that the subarray starts at element 5 and contains 10 elements.</span></span>

```console
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```

<span data-ttu-id="5f1d7-150">[`Array.append`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#append) 通过合并两个现有的数组创建新的数组。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-150">[`Array.append`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#append) creates a new array by combining two existing arrays.</span></span>

<span data-ttu-id="5f1d7-151">下面的代码演示了 **数组 append**。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-151">The following code demonstrates **Array.append**.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet13.fs)]

<span data-ttu-id="5f1d7-152">上述代码的输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-152">The output of the preceding code is as follows.</span></span>

```console
[|1; 2; 3; 4; 5; 6|]
```

<span data-ttu-id="5f1d7-153">[`Array.choose`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#choose) 选择要包含在新数组中的数组元素。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-153">[`Array.choose`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#choose) selects elements of an array to include in a new array.</span></span> <span data-ttu-id="5f1d7-154">下面的代码演示了 `Array.choose` 。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-154">The following code demonstrates `Array.choose`.</span></span> <span data-ttu-id="5f1d7-155">请注意，数组的元素类型不必与选项类型中返回的值的类型相匹配。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-155">Note that the element type of the array does not have to match the type of the value returned in the option type.</span></span> <span data-ttu-id="5f1d7-156">在此示例中，元素类型为 `int` ，而选项是多项式函数的结果， `elem*elem - 1` 作为浮点数。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-156">In this example, the element type is `int` and the option is the result of a polynomial function, `elem*elem - 1`, as a floating point number.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet14.fs)]

<span data-ttu-id="5f1d7-157">上述代码的输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-157">The output of the preceding code is as follows.</span></span>

```console
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

<span data-ttu-id="5f1d7-158">[`Array.collect`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#collect) 在现有数组的每个数组元素上运行指定函数，然后收集该函数生成的元素，并将它们合并到新数组中。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-158">[`Array.collect`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#collect) runs a specified function on each array element of an existing array and then collects the elements generated by the function and combines them into a new array.</span></span> <span data-ttu-id="5f1d7-159">下面的代码演示了 `Array.collect` 。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-159">The following code demonstrates `Array.collect`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet15.fs)]

<span data-ttu-id="5f1d7-160">上述代码的输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-160">The output of the preceding code is as follows.</span></span>

```console
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

<span data-ttu-id="5f1d7-161">[`Array.concat`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#concat) 采用一系列数组，并将它们合并到一个数组中。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-161">[`Array.concat`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#concat) takes a sequence of arrays and combines them into a single array.</span></span> <span data-ttu-id="5f1d7-162">下面的代码演示了 `Array.concat` 。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-162">The following code demonstrates `Array.concat`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet16.fs)]

<span data-ttu-id="5f1d7-163">上述代码的输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-163">The output of the preceding code is as follows.</span></span>

```console
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

<span data-ttu-id="5f1d7-164">[`Array.filter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#filter) 采用布尔条件函数并生成一个新数组，该数组仅包含其条件为 true 的输入数组中的元素。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-164">[`Array.filter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#filter) takes a Boolean condition function and generates a new array that contains only those elements from the input array for which the condition is true.</span></span> <span data-ttu-id="5f1d7-165">下面的代码演示了 `Array.filter` 。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-165">The following code demonstrates `Array.filter`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet17.fs)]

<span data-ttu-id="5f1d7-166">上述代码的输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-166">The output of the preceding code is as follows.</span></span>

```console
[|2; 4; 6; 8; 10|]
```

<span data-ttu-id="5f1d7-167">[`Array.rev`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#rev) 通过反转现有数组的顺序生成新的数组。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-167">[`Array.rev`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#rev) generates a new array by reversing the order of an existing array.</span></span> <span data-ttu-id="5f1d7-168">下面的代码演示了 `Array.rev` 。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-168">The following code demonstrates `Array.rev`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet18.fs)]

<span data-ttu-id="5f1d7-169">上述代码的输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-169">The output of the preceding code is as follows.</span></span>

```console
"Hello world!"
```

<span data-ttu-id="5f1d7-170">您可以通过使用管道运算符 () 轻松地组合数组模块中的函数 `|>` ，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-170">You can easily combine functions in the array module that transform arrays by using the pipeline operator (`|>`), as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet19.fs)]

<span data-ttu-id="5f1d7-171">输出为</span><span class="sxs-lookup"><span data-stu-id="5f1d7-171">The output is</span></span>

```console
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a><span data-ttu-id="5f1d7-172">多维数组</span><span class="sxs-lookup"><span data-stu-id="5f1d7-172">Multidimensional arrays</span></span>

<span data-ttu-id="5f1d7-173">可以创建多维数组，但没有用于写入多维数组文本的语法。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-173">A multidimensional array can be created, but there is no syntax for writing a multidimensional array literal.</span></span> <span data-ttu-id="5f1d7-174">使用运算符 [`array2D`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html) 可从数组元素序列序列创建数组。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-174">Use the operator [`array2D`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html) to create an array from a sequence of sequences of array elements.</span></span> <span data-ttu-id="5f1d7-175">序列可以是数组或列表文本。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-175">The sequences can be array or list literals.</span></span> <span data-ttu-id="5f1d7-176">例如，下面的代码创建一个二维数组。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-176">For example, the following code creates a two-dimensional array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet20.fs)]

<span data-ttu-id="5f1d7-177">您还可以使用函数 [`Array2D.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#init) 初始化两个维度的数组，并且类似的函数可用于三个和四个维度的数组。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-177">You can also use the function [`Array2D.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#init) to initialize arrays of two dimensions, and similar functions are available for arrays of three and four dimensions.</span></span> <span data-ttu-id="5f1d7-178">这些函数采用用于创建元素的函数。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-178">These functions take a function that is used to create the elements.</span></span> <span data-ttu-id="5f1d7-179">若要创建一个二维数组，其中包含设置为初始值的元素，而不是指定函数，请使用 [`Array2D.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#create) 函数，该函数也可用于最多四个维度的数组。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-179">To create a two-dimensional array that contains elements set to an initial value instead of specifying a function, use the [`Array2D.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#create) function, which is also available for arrays up to four dimensions.</span></span> <span data-ttu-id="5f1d7-180">下面的代码示例首先演示如何创建包含所需元素的数组数组，然后使用 `Array2D.init` 生成所需的二维数组。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-180">The following code example first shows how to create an array of arrays that contain the desired elements, and then uses `Array2D.init` to generate the desired two-dimensional array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet21.fs)]

<span data-ttu-id="5f1d7-181">秩为4的数组支持数组索引和切片语法。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-181">Array indexing and slicing syntax is supported for arrays up to rank 4.</span></span> <span data-ttu-id="5f1d7-182">当在多个维度中指定索引时，可以使用逗号分隔索引，如以下代码示例中所示。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-182">When you specify an index in multiple dimensions, you use commas to separate the indexes, as illustrated in the following code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet22.fs)]

<span data-ttu-id="5f1d7-183">二维数组的类型被写出为 `<type>[,]` (例如， `int[,]` `double[,]`) ，而将三维数组的类型编写为 `<type>[,,]` ，依此类推，对于更高维度的数组，也是如此。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-183">The type of a two-dimensional array is written out as `<type>[,]` (for example, `int[,]`, `double[,]`), and the type of a three-dimensional array is written as `<type>[,,]`, and so on for arrays of higher dimensions.</span></span>

<span data-ttu-id="5f1d7-184">对于多维数组，只能使用适用于一维数组的函数子集。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-184">Only a subset of the functions available for one-dimensional arrays is also available for multidimensional arrays.</span></span>

### <a name="array-slicing-and-multidimensional-arrays"></a><span data-ttu-id="5f1d7-185">数组切片和多维数组</span><span class="sxs-lookup"><span data-stu-id="5f1d7-185">Array slicing and multidimensional arrays</span></span>

<span data-ttu-id="5f1d7-186">在矩阵)  (二维数组中，可以通过指定范围并使用通配符 (`*`) 字符来指定整行或整列来提取子矩阵。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-186">In a two-dimensional array (a matrix), you can extract a sub-matrix by specifying ranges and using a wildcard (`*`) character to specify whole rows or columns.</span></span>

```fsharp
// Get rows 1 to N from an NxM matrix (returns a matrix):
matrix.[1.., *]

// Get rows 1 to 3 from a matrix (returns a matrix):
matrix.[1..3, *]

// Get columns 1 to 3 from a matrix (returns a matrix):
matrix.[*, 1..3]

// Get a 3x3 submatrix:
matrix.[1..3, 1..3]
```

<span data-ttu-id="5f1d7-187">可以将多维数组分解为相同或较低维度的子。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-187">You can decompose a multidimensional array into subarrays of the same or lower dimension.</span></span> <span data-ttu-id="5f1d7-188">例如，您可以通过指定单个行或列从矩阵获取向量。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-188">For example, you can obtain a vector from a matrix by specifying a single row or column.</span></span>

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

<span data-ttu-id="5f1d7-189">可以将此切片语法用于实现元素访问运算符和重载方法的类型 `GetSlice` 。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-189">You can use this slicing syntax for types that implement the element access operators and overloaded `GetSlice` methods.</span></span> <span data-ttu-id="5f1d7-190">例如，下面的代码创建一个矩阵类型，该类型包装 F # 二维二维数组，实现项属性以提供对数组索引的支持，并实现的三个版本 `GetSlice` 。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-190">For example, the following code creates a Matrix type that wraps the F# 2D array, implements an Item property to provide support for array indexing, and implements three versions of `GetSlice`.</span></span> <span data-ttu-id="5f1d7-191">如果可以将此代码用作矩阵类型的模板，则可以使用本部分所述的所有切片操作。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-191">If you can use this code as a template for your matrix types, you can use all the slicing operations that this section describes.</span></span>

```fsharp
type Matrix<'T>(N: int, M: int) =
    let internalArray = Array2D.zeroCreate<'T> N M

    member this.Item
        with get(a: int, b: int) = internalArray.[a, b]
        and set(a: int, b: int) (value:'T) = internalArray.[a, b] <- value

    member this.GetSlice(rowStart: int option, rowFinish : int option, colStart: int option, colFinish : int option) =
        let rowStart =
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        let colStart =
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish =
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[rowStart..rowFinish, colStart..colFinish]

    member this.GetSlice(row: int, colStart: int option, colFinish: int option) =
        let colStart =
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish =
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[row, colStart..colFinish]

    member this.GetSlice(rowStart: int option, rowFinish: int option, col: int) =
        let rowStart =
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        internalArray.[rowStart..rowFinish, col]

module test =
    let generateTestMatrix x y =
        let matrix = new Matrix<float>(3, 3)
        for i in 0..2 do
            for j in 0..2 do
                matrix.[i, j] <- float(i) * x - float(j) * y
        matrix

    let test1 = generateTestMatrix 2.3 1.1
    let submatrix = test1.[0..1, 0..1]
    printfn "%A" submatrix

    let firstRow = test1.[0,*]
    let secondRow = test1.[1,*]
    let firstCol = test1.[*,0]
    printfn "%A" firstCol
```

### <a name="boolean-functions-on-arrays"></a><span data-ttu-id="5f1d7-192">数组上的布尔函数</span><span class="sxs-lookup"><span data-stu-id="5f1d7-192">Boolean functions on arrays</span></span>

<span data-ttu-id="5f1d7-193">分别为 [`Array.exists`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists) [`Array.exists2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists2) 一个或两个数组中的函数和测试元素。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-193">The functions [`Array.exists`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists) and [`Array.exists2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists2) test elements in either one or two arrays, respectively.</span></span> <span data-ttu-id="5f1d7-194">`true`如果满足条件的) 有元素 (或元素对，则这些函数将采用测试函数并返回 `Array.exists2` 。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-194">These functions take a test function and return `true` if there is an element (or element pair for `Array.exists2`) that satisfies the condition.</span></span>

<span data-ttu-id="5f1d7-195">下面的代码演示如何使用 `Array.exists` 和 `Array.exists2` 。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-195">The following code demonstrates the use of `Array.exists` and `Array.exists2`.</span></span> <span data-ttu-id="5f1d7-196">在这些示例中，通过仅应用一个自变量（在这种情况下为函数参数）来创建新函数。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-196">In these examples, new functions are created by applying only one of the arguments, in these cases, the function argument.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet23.fs)]

<span data-ttu-id="5f1d7-197">上述代码的输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-197">The output of the preceding code is as follows.</span></span>

```console
true
false
false
true
```

<span data-ttu-id="5f1d7-198">同样，函数 [`Array.forall`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall) 测试数组以确定每个元素是否都满足布尔条件。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-198">Similarly, the function [`Array.forall`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall) tests an array to determine whether every element satisfies a Boolean condition.</span></span> <span data-ttu-id="5f1d7-199">变体 [`Array.forall2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall2) 通过使用包含长度相等的两个数组的元素的布尔函数来执行相同的操作。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-199">The variation [`Array.forall2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall2) does the same thing by using a Boolean function that involves elements of two arrays of equal length.</span></span> <span data-ttu-id="5f1d7-200">下面的代码阐释了这些函数的用法。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-200">The following code illustrates the use of these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet24.fs)]

<span data-ttu-id="5f1d7-201">这些示例的输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-201">The output for these examples is as follows.</span></span>

```console
false
true
true
false
```

### <a name="search-arrays"></a><span data-ttu-id="5f1d7-202">搜索数组</span><span class="sxs-lookup"><span data-stu-id="5f1d7-202">Search arrays</span></span>

<span data-ttu-id="5f1d7-203">[`Array.find`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#find) 采用布尔函数并返回函数为其返回的第一个元素 `true` ， <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> 如果找不到满足条件的元素，则引发。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-203">[`Array.find`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#find) takes a Boolean function and returns the first element for which the function returns `true`, or raises a <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> if no element that satisfies the condition is found.</span></span> <span data-ttu-id="5f1d7-204">[`Array.findIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#findIndex) 类似于 `Array.find` ，但它返回元素的索引，而不是元素本身。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-204">[`Array.findIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#findIndex) is like `Array.find`, except that it returns the index of the element instead of the element itself.</span></span>

<span data-ttu-id="5f1d7-205">下面的代码使用 `Array.find` 和 `Array.findIndex` 来查找同时为完全方形和完全相同的多维数据集的数字。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-205">The following code uses `Array.find` and `Array.findIndex` to locate a number that is both a perfect square and perfect cube.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet25.fs)]

<span data-ttu-id="5f1d7-206">输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-206">The output is as follows.</span></span>

```console
The first element that is both a square and a cube is 64 and its index is 62.
```

<span data-ttu-id="5f1d7-207">[`Array.tryFind`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFind) 类似于 `Array.find` ，只不过其结果是选项类型， `None` 如果未找到元素，则返回。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-207">[`Array.tryFind`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFind) is like `Array.find`, except that its result is an option type, and it returns `None` if no element is found.</span></span> <span data-ttu-id="5f1d7-208">`Array.tryFind``Array.find`如果你不知道匹配的元素是否在数组中，则应使用而不是。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-208">`Array.tryFind` should be used instead of `Array.find` when you do not know whether a matching element is in the array.</span></span> <span data-ttu-id="5f1d7-209">同样， [`Array.tryFindIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFindIndex) 类似于， `Array.findIndex` 只不过选项类型是返回值。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-209">Similarly, [`Array.tryFindIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFindIndex) is like `Array.findIndex` except that the option type is the return value.</span></span> <span data-ttu-id="5f1d7-210">如果未找到元素，则选项为 `None` 。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-210">If no element is found, the option is `None`.</span></span>

<span data-ttu-id="5f1d7-211">以下代码演示了 `Array.tryFind` 的用法。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-211">The following code demonstrates the use of `Array.tryFind`.</span></span> <span data-ttu-id="5f1d7-212">此代码依赖于前面的代码。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-212">This code depends on the previous code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet26.fs)]

<span data-ttu-id="5f1d7-213">输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-213">The output is as follows.</span></span>

```console
Found an element: 1
Found an element: 729
Failed to find a matching element.
```

<span data-ttu-id="5f1d7-214">[`Array.tryPick`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryPick)除了查找元素外，还需要转换某个元素。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-214">Use [`Array.tryPick`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryPick) when you need to transform an element in addition to finding it.</span></span> <span data-ttu-id="5f1d7-215">结果是函数为其返回转换后的元素作为选项值的第一个元素; `None` 如果未找到这样的元素，则为。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-215">The result is the first element for which the function returns the transformed element as an option value, or `None` if no such element is found.</span></span>

<span data-ttu-id="5f1d7-216">以下代码显示了 `Array.tryPick` 的用法。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-216">The following code shows the use of `Array.tryPick`.</span></span> <span data-ttu-id="5f1d7-217">在这种情况下，不是 lambda 表达式，而是定义了若干本地 helper 函数以简化代码。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-217">In this case, instead of a lambda expression, several local helper functions are defined to simplify the code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet27.fs)]

<span data-ttu-id="5f1d7-218">输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-218">The output is as follows.</span></span>

```console
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
Did not find an element that is both a perfect square and a perfect cube.
```

### <a name="perform-computations-on-arrays"></a><span data-ttu-id="5f1d7-219">对数组执行计算</span><span class="sxs-lookup"><span data-stu-id="5f1d7-219">Perform computations on arrays</span></span>

<span data-ttu-id="5f1d7-220">[`Array.average`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#average)函数返回数组中每个元素的平均值。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-220">The [`Array.average`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#average) function returns the average of each element in an array.</span></span> <span data-ttu-id="5f1d7-221">它限制为支持完全除以整数的元素类型，包括浮点类型，但不支持整数类型。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-221">It is limited to element types that support exact division by an integer, which includes floating point types but not integral types.</span></span> <span data-ttu-id="5f1d7-222">[`Array.averageBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#averageBy)函数返回对每个元素调用函数的结果的平均值。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-222">The [`Array.averageBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#averageBy) function returns the average of the results of calling a function on each element.</span></span> <span data-ttu-id="5f1d7-223">对于整型类型的数组，可以使用 `Array.averageBy` ，并让函数将每个元素转换为浮点类型进行计算。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-223">For an array of integral type, you can use `Array.averageBy` and have the function convert each element to a floating point type for the computation.</span></span>

<span data-ttu-id="5f1d7-224">[`Array.max`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#max) [`Array.min`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#min) 如果元素类型支持，则使用或获取最大或最小元素。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-224">Use [`Array.max`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#max) or [`Array.min`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#min) to get the maximum or minimum element, if the element type supports it.</span></span> <span data-ttu-id="5f1d7-225">同样， [`Array.maxBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#maxBy) 和 [`Array.minBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#minBy) 允许先执行函数，也许是转换为支持比较的类型。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-225">Similarly, [`Array.maxBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#maxBy) and [`Array.minBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#minBy) allow a function to be executed first, perhaps to transform to a type that supports comparison.</span></span>

<span data-ttu-id="5f1d7-226">[`Array.sum`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sum) 添加数组的元素，并对 [`Array.sumBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sumBy) 每个元素调用一个函数，并将结果添加到一起。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-226">[`Array.sum`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sum) adds the elements of an array, and [`Array.sumBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sumBy) calls a function on each element and adds the results together.</span></span>

<span data-ttu-id="5f1d7-227">若要对数组中的每个元素执行函数而不存储返回值，请使用 [`Array.iter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter) 。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-227">To execute a function on each element in an array without storing the return values, use [`Array.iter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter).</span></span> <span data-ttu-id="5f1d7-228">对于涉及两个相等长度数组的函数，请使用 [`Array.iter2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter2) 。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-228">For a function involving two arrays of equal length, use [`Array.iter2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter2).</span></span> <span data-ttu-id="5f1d7-229">如果还需要保留函数结果的数组，请使用 [`Array.map`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map) 或 [`Array.map2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map2) ，这一次在两个数组上进行操作。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-229">If you also need to keep an array of the results of the function, use [`Array.map`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map) or [`Array.map2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map2), which operates on two arrays at a time.</span></span>

<span data-ttu-id="5f1d7-230">变体 [`Array.iteri`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri) 和 [`Array.iteri2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri2) 允许在计算中涉及元素的索引; 对于和，情况也是如此 [`Array.mapi`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi) [`Array.mapi2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi2) 。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-230">The variations [`Array.iteri`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri) and [`Array.iteri2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri2) allow the index of the element to be involved in the computation; the same is true for [`Array.mapi`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi) and [`Array.mapi2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi2).</span></span>

<span data-ttu-id="5f1d7-231">函数、、、、 [`Array.fold`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold) [`Array.foldBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack) [`Array.reduce`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduce) [`Array.reduceBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduceBack) [`Array.scan`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scan) 和 [`Array.scanBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scanBack) 执行的算法涉及数组的所有元素。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-231">The functions [`Array.fold`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold), [`Array.foldBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack), [`Array.reduce`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduce), [`Array.reduceBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduceBack), [`Array.scan`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scan), and [`Array.scanBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scanBack) execute algorithms that involve all the elements of an array.</span></span> <span data-ttu-id="5f1d7-232">同样，在 [`Array.fold2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold2) [`Array.foldBack2`](foldBack2) 两个数组上进行变化并执行计算。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-232">Similarly, the variations [`Array.fold2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold2) and [`Array.foldBack2`](foldBack2) perform computations on two arrays.</span></span>

<span data-ttu-id="5f1d7-233">用于执行计算的这些函数对应于 [列表模块](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html)中具有相同名称的函数。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-233">These functions for performing computations correspond to the functions of the same name in the [List module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span></span> <span data-ttu-id="5f1d7-234">有关用法示例，请参阅 [列表](lists.md)。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-234">For usage examples, see [Lists](lists.md).</span></span>

### <a name="modify-arrays"></a><span data-ttu-id="5f1d7-235">修改数组</span><span class="sxs-lookup"><span data-stu-id="5f1d7-235">Modify arrays</span></span>

<span data-ttu-id="5f1d7-236">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) 将元素设置为指定值。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-236">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) sets an element to a specified value.</span></span> <span data-ttu-id="5f1d7-237">[`Array.fill`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fill) 将数组中的一系列元素设置为指定值。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-237">[`Array.fill`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fill) sets a range of elements in an array to a specified value.</span></span> <span data-ttu-id="5f1d7-238">下面的代码提供了一个示例 `Array.fill` 。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-238">The following code provides an example of `Array.fill`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet28.fs)]

<span data-ttu-id="5f1d7-239">输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-239">The output is as follows.</span></span>

```console
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

<span data-ttu-id="5f1d7-240">您可以使用将 [`Array.blit`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#blit) 一个数组的子节复制到另一个数组。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-240">You can use [`Array.blit`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#blit) to copy a subsection of one array to another array.</span></span>

### <a name="convert-to-and-from-other-types"></a><span data-ttu-id="5f1d7-241">与其他类型相互转换</span><span class="sxs-lookup"><span data-stu-id="5f1d7-241">Convert to and from other types</span></span>

<span data-ttu-id="5f1d7-242">[`Array.ofList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofList) 从列表创建数组。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-242">[`Array.ofList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofList) creates an array from a list.</span></span> <span data-ttu-id="5f1d7-243">[`Array.ofSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofSeq) 从序列创建数组。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-243">[`Array.ofSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofSeq) creates an array from a sequence.</span></span> <span data-ttu-id="5f1d7-244">[`Array.toList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toList) 并 [`Array.toSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toSeq) 从数组类型转换为这些其他集合类型。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-244">[`Array.toList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toList) and [`Array.toSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toSeq) convert to these other collection types from the array type.</span></span>

### <a name="sort-arrays"></a><span data-ttu-id="5f1d7-245">数组排序</span><span class="sxs-lookup"><span data-stu-id="5f1d7-245">Sort arrays</span></span>

<span data-ttu-id="5f1d7-246">使用 [`Array.sort`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sort) 可通过泛型比较函数对数组进行排序。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-246">Use [`Array.sort`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sort) to sort an array by using the generic comparison function.</span></span> <span data-ttu-id="5f1d7-247">用于 [`Array.sortBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortBy) 指定一个函数，该函数生成一个值（称为 *密钥*），以便通过对键使用泛型比较函数进行排序。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-247">Use [`Array.sortBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortBy) to specify a function that generates a value, referred to as a *key*, to sort by using the generic comparison function on the key.</span></span> <span data-ttu-id="5f1d7-248">[`Array.sortWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortWith)如果要提供自定义比较函数，请使用。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-248">Use [`Array.sortWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortWith) if you want to provide a custom comparison function.</span></span> <span data-ttu-id="5f1d7-249">`Array.sort`、 `Array.sortBy` 和 `Array.sortWith` 都作为新数组返回已排序的数组。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-249">`Array.sort`, `Array.sortBy`, and `Array.sortWith` all return the sorted array as a new array.</span></span> <span data-ttu-id="5f1d7-250">变体 [`Array.sortInPlace`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlace) 、 [`Array.sortInPlaceBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceBy) 和 [`Array.sortInPlaceWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceWith) 修改现有数组，而不是返回新数组。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-250">The variations [`Array.sortInPlace`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlace), [`Array.sortInPlaceBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceBy), and [`Array.sortInPlaceWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceWith) modify the existing array instead of returning a new one.</span></span>

### <a name="arrays-and-tuples"></a><span data-ttu-id="5f1d7-251">数组和元组</span><span class="sxs-lookup"><span data-stu-id="5f1d7-251">Arrays and tuples</span></span>

<span data-ttu-id="5f1d7-252">函数 [`Array.zip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip) 和 [`Array.unzip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip) 将元组对的数组转换为数组的元组，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-252">The functions [`Array.zip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip) and [`Array.unzip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip) convert arrays of tuple pairs to tuples of arrays and vice versa.</span></span> <span data-ttu-id="5f1d7-253">[`Array.zip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip3) 和 [`Array.unzip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip3) 类似，只不过它们适用于三个元素的元组或三个数组的元组。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-253">[`Array.zip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip3) and [`Array.unzip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip3) are similar except that they work with tuples of three elements or tuples of three arrays.</span></span>

## <a name="parallel-computations-on-arrays"></a><span data-ttu-id="5f1d7-254">数组上的并行计算</span><span class="sxs-lookup"><span data-stu-id="5f1d7-254">Parallel computations on arrays</span></span>

<span data-ttu-id="5f1d7-255">模块 [`Array.Parallel`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule-parallel.html) 包含用于对数组执行并行计算的函数。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-255">The module [`Array.Parallel`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule-parallel.html) contains functions for performing parallel computations on arrays.</span></span> <span data-ttu-id="5f1d7-256">此模块在面向版本4之前的 .NET Framework 版本的应用程序中不可用。</span><span class="sxs-lookup"><span data-stu-id="5f1d7-256">This module is not available in applications that target versions of the .NET Framework prior to version 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="5f1d7-257">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5f1d7-257">See also</span></span>

- [<span data-ttu-id="5f1d7-258">F# 语言参考</span><span class="sxs-lookup"><span data-stu-id="5f1d7-258">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="5f1d7-259">F# 类型</span><span class="sxs-lookup"><span data-stu-id="5f1d7-259">F# Types</span></span>](fsharp-types.md)

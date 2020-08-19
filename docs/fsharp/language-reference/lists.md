---
title: 列表
description: '了解 F # 列表，它是一个具有相同类型的有序、不可变的元素系列。'
ms.date: 08/13/2020
ms.openlocfilehash: 16d7195039d25cf63630f5cc3be6563b1bf45c44
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559162"
---
# <a name="lists"></a><span data-ttu-id="9b3b0-103">列表</span><span class="sxs-lookup"><span data-stu-id="9b3b0-103">Lists</span></span>

<span data-ttu-id="9b3b0-104">F# 中的列表是一个有序的、不可变的同类型元素系列。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-104">A list in F# is an ordered, immutable series of elements of the same type.</span></span> <span data-ttu-id="9b3b0-105">若要对列表执行基本操作，请使用 [列表模块](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html)中的函数。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-105">To perform basic operations on lists, use the functions in the [List module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span></span>

## <a name="creating-and-initializing-lists"></a><span data-ttu-id="9b3b0-106">创建和初始化列表</span><span class="sxs-lookup"><span data-stu-id="9b3b0-106">Creating and Initializing Lists</span></span>

<span data-ttu-id="9b3b0-107">可以通过以下方式来定义列表：显式列出元素并用分号分隔各个元素，然后将这些元素用方括号括起来，如下面的代码行所示。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-107">You can define a list by explicitly listing out the elements, separated by semicolons and enclosed in square brackets, as shown in the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

<span data-ttu-id="9b3b0-108">也可以在各个元素之间插入换行符，在这种情况下，分号是可选的。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-108">You can also put line breaks between elements, in which case the semicolons are optional.</span></span> <span data-ttu-id="9b3b0-109">当元素初始化表达式较长或你希望为每个元素包含一个注释时，后一种语法会产生可读性更高的代码。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-109">The latter syntax can result in more readable code when the element initialization expressions are longer, or when you want to include a comment for each element.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

<span data-ttu-id="9b3b0-110">通常，所有列表元素都必须是同一类型。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-110">Normally, all list elements must be the same type.</span></span> <span data-ttu-id="9b3b0-111">但存在一种例外情况，即其元素被指定为基类型的列表中包含的元素可以是派生类型。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-111">An exception is that a list in which the elements are specified to be a base type can have elements that are derived types.</span></span> <span data-ttu-id="9b3b0-112">由于 `Button` 和 `CheckBox` 都派生自 `Control`，因此以下内容是可接受的。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-112">Thus the following is acceptable, because both `Button` and `CheckBox` derive from `Control`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

<span data-ttu-id="9b3b0-113">也可以使用由范围分隔符 (`..`) 分隔的整数所指示的范围来定义列表元素，如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-113">You can also define list elements by using a range indicated by integers separated by the range operator (`..`), as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

<span data-ttu-id="9b3b0-114">可使用一对中间不包含任何内容的方括号来指定空列表。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-114">An empty list is specified by a pair of square brackets with nothing in between them.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

<span data-ttu-id="9b3b0-115">也可以使用序列表达式来创建列表。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-115">You can also use a sequence expression to create a list.</span></span> <span data-ttu-id="9b3b0-116">有关详细信息，请参阅 [序列表达式](sequences.md#sequence-expressions) 。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-116">See [Sequence Expressions](sequences.md#sequence-expressions) for more information.</span></span> <span data-ttu-id="9b3b0-117">例如，以下代码创建一个从 1 到 10 的整数的平方值的列表。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-117">For example, the following code creates a list of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a><span data-ttu-id="9b3b0-118">用于处理列表的运算符</span><span class="sxs-lookup"><span data-stu-id="9b3b0-118">Operators for Working with Lists</span></span>

<span data-ttu-id="9b3b0-119">可以使用 `::` (cons) 运算符将元素附加到列表中。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-119">You can attach elements to a list by using the `::` (cons) operator.</span></span> <span data-ttu-id="9b3b0-120">如果 `list1` 为 `[2; 3; 4]`，则以下代码会将 `list2` 创建为 `[100; 2; 3; 4]`。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-120">If `list1` is `[2; 3; 4]`, the following code creates `list2` as `[100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

<span data-ttu-id="9b3b0-121">可以使用 `@` 运算符来串联具有可兼容类型的列表，如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-121">You can concatenate lists that have compatible types by using the `@` operator, as in the following code.</span></span> <span data-ttu-id="9b3b0-122">如果 `list1` 为 `[2; 3; 4]`，且 `list2` 为 `[100; 2; 3; 4]`，则此代码会将 `list3` 创建为 `[2; 3; 4; 100; 2; 3; 4]`。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-122">If `list1` is `[2; 3; 4]` and `list2` is `[100; 2; 3; 4]`, this code creates `list3` as `[2; 3; 4; 100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

<span data-ttu-id="9b3b0-123">[列表模块](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html)中提供了用于对列表执行操作的函数。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-123">Functions for performing operations on lists are available in the [List module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span></span>

<span data-ttu-id="9b3b0-124">由于 F# 中的列表是不可变的，因此任何修改操作都会生成新列表，而不是修改现有列表。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-124">Because lists in F# are immutable, any modifying operations generate new lists instead of modifying existing lists.</span></span>

<span data-ttu-id="9b3b0-125">F # 中的列表实现为单独链接列表，这意味着仅访问列表头的操作是 O (1) ，元素访问是 O (*n*) 。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-125">Lists in F# are implemented as singly linked lists, which means that operations that access only the head of the list are O(1), and element access is O(*n*).</span></span>

## <a name="properties"></a><span data-ttu-id="9b3b0-126">属性</span><span class="sxs-lookup"><span data-stu-id="9b3b0-126">Properties</span></span>

<span data-ttu-id="9b3b0-127">列表类型支持以下属性：</span><span class="sxs-lookup"><span data-stu-id="9b3b0-127">The list type supports the following properties:</span></span>

|<span data-ttu-id="9b3b0-128">properties</span><span class="sxs-lookup"><span data-stu-id="9b3b0-128">Property</span></span>|<span data-ttu-id="9b3b0-129">类型</span><span class="sxs-lookup"><span data-stu-id="9b3b0-129">Type</span></span>|<span data-ttu-id="9b3b0-130">说明</span><span class="sxs-lookup"><span data-stu-id="9b3b0-130">Description</span></span>|
|--------|----|-----------|
|[<span data-ttu-id="9b3b0-131">头</span><span class="sxs-lookup"><span data-stu-id="9b3b0-131">Head</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Head)|`'T`|<span data-ttu-id="9b3b0-132">第一个元素。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-132">The first element.</span></span>|
|[<span data-ttu-id="9b3b0-133">Empty</span><span class="sxs-lookup"><span data-stu-id="9b3b0-133">Empty</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Empty)|`'T list`|<span data-ttu-id="9b3b0-134">返回适合类型的空列表的静态属性。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-134">A static property that returns an empty list of the appropriate type.</span></span>|
|[<span data-ttu-id="9b3b0-135">IsEmpty</span><span class="sxs-lookup"><span data-stu-id="9b3b0-135">IsEmpty</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#IsEmpty)|`bool`|<span data-ttu-id="9b3b0-136">如果列表不包含任何元素，则为 `true`。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-136">`true` if the list has no elements.</span></span>|
|[<span data-ttu-id="9b3b0-137">项目</span><span class="sxs-lookup"><span data-stu-id="9b3b0-137">Item</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Item)|`'T`|<span data-ttu-id="9b3b0-138">位于指定索引处（从零开始）的元素。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-138">The element at the specified index (zero-based).</span></span>|
|[<span data-ttu-id="9b3b0-139">长度</span><span class="sxs-lookup"><span data-stu-id="9b3b0-139">Length</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Length)|`int`|<span data-ttu-id="9b3b0-140">元素数量。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-140">The number of elements.</span></span>|
|[<span data-ttu-id="9b3b0-141">Tail</span><span class="sxs-lookup"><span data-stu-id="9b3b0-141">Tail</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Tail)|`'T list`|<span data-ttu-id="9b3b0-142">不带第一个元素的列表。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-142">The list without the first element.</span></span>|

<span data-ttu-id="9b3b0-143">以下是一些使用这些属性的示例。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-143">Following are some examples of using these properties.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]

## <a name="using-lists"></a><span data-ttu-id="9b3b0-144">使用列表</span><span class="sxs-lookup"><span data-stu-id="9b3b0-144">Using Lists</span></span>

<span data-ttu-id="9b3b0-145">利用列表进行编程，你可以使用少量代码来执行复杂的操作。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-145">Programming with lists enables you to perform complex operations with a small amount of code.</span></span> <span data-ttu-id="9b3b0-146">本节介绍针对列表的常见操作，这些操作对于函数编程很重要。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-146">This section describes common operations on lists that are important to functional programming.</span></span>

### <a name="recursion-with-lists"></a><span data-ttu-id="9b3b0-147">利用列表进行递归</span><span class="sxs-lookup"><span data-stu-id="9b3b0-147">Recursion with Lists</span></span>

<span data-ttu-id="9b3b0-148">列表特别适合于递归编程技术。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-148">Lists are uniquely suited to recursive programming techniques.</span></span> <span data-ttu-id="9b3b0-149">假设要对列表的每个元素执行某个操作。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-149">Consider an operation that must be performed on every element of a list.</span></span> <span data-ttu-id="9b3b0-150">可以通过以下方式来实现递归：对列表头执行操作，然后再次将列表尾（一个更小的列表，它由不带第一个元素的原始列表组成）传递回下一级递归。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-150">You can do this recursively by operating on the head of the list and then passing the tail of the list, which is a smaller list that consists of the original list without the first element, back again to the next level of recursion.</span></span>

<span data-ttu-id="9b3b0-151">若要编写此类递归函数，可在模式匹配中使用 cons 运算符 (`::`)，以便将列表头与列表尾分离。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-151">To write such a recursive function, you use the cons operator (`::`) in pattern matching, which enables you to separate the head of a list from the tail.</span></span>

<span data-ttu-id="9b3b0-152">以下代码示例显示了如何使用模式匹配来实现对列表执行操作的递归函数。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-152">The following code example shows how to use pattern matching to implement a recursive function that performs operations on a list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

<span data-ttu-id="9b3b0-153">上面的代码非常适用于小型列表，但对于大型列表，它可能会溢出堆栈。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-153">The previous code works well for small lists, but for larger lists, it could overflow the stack.</span></span> <span data-ttu-id="9b3b0-154">以下代码通过使用累加器自变量（一种用于处理递归函数的标准技术）对该代码进行了改进。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-154">The following code improves on this code by using an accumulator argument, a standard technique for working with recursive functions.</span></span> <span data-ttu-id="9b3b0-155">使用累加器参数会使函数进行尾递归，这将节省堆栈空间。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-155">The use of the accumulator argument makes the function tail recursive, which saves stack space.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

<span data-ttu-id="9b3b0-156">函数 `RemoveAllMultiples` 是一个递归函数，它采用两个列表。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-156">The function `RemoveAllMultiples` is a recursive function that takes two lists.</span></span> <span data-ttu-id="9b3b0-157">第一个列表包含一些数字（将移除这些数字的倍数），第二个列表是要从中移除这些倍数数字的列表。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-157">The first list contains the numbers whose multiples will be removed, and the second list is the list from which to remove the numbers.</span></span> <span data-ttu-id="9b3b0-158">以下示例中的代码使用此递归函数来消除列表中的所有非质数，结果是得到一个质数列表。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-158">The code in the following example uses this recursive function to eliminate all the non-prime numbers from a list, leaving a list of prime numbers as the result.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

<span data-ttu-id="9b3b0-159">输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="9b3b0-159">The output is as follows:</span></span>

```console
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a><span data-ttu-id="9b3b0-160">模块函数</span><span class="sxs-lookup"><span data-stu-id="9b3b0-160">Module Functions</span></span>

<span data-ttu-id="9b3b0-161">[List 模块](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html)提供了用于访问列表元素的函数。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-161">The [List module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html) provides functions that access the elements of a list.</span></span> <span data-ttu-id="9b3b0-162">访问头元素的速度最快且最为容易。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-162">The head element is the fastest and easiest to access.</span></span> <span data-ttu-id="9b3b0-163">使用属性 [head](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Head) 或模块函数 [列表 head](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#head)。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-163">Use the property [Head](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Head) or the module function [List.head](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#head).</span></span> <span data-ttu-id="9b3b0-164">您可以使用 [tail](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Tail) 属性或 [list tail](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#tail) 函数访问列表的尾部。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-164">You can access the tail of a list by using the [Tail](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Tail) property or the [List.tail](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#tail) function.</span></span> <span data-ttu-id="9b3b0-165">若要按索引查找元素，请使用 [List n](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#nth) 函数。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-165">To find an element by index, use the [List.nth](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#nth) function.</span></span> <span data-ttu-id="9b3b0-166">`List.nth` 将遍历列表。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-166">`List.nth` traverses the list.</span></span> <span data-ttu-id="9b3b0-167">因此，它是 O (*n*) 。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-167">Therefore, it is O(*n*).</span></span> <span data-ttu-id="9b3b0-168">如果你的代码经常使用 `List.nth`，那么可能需要考虑使用数组而不是列表。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-168">If your code uses `List.nth` frequently, you might want to consider using an array instead of a list.</span></span> <span data-ttu-id="9b3b0-169">数组中的元素访问的运算复杂度为 O(1)。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-169">Element access in arrays is O(1).</span></span>

### <a name="boolean-operations-on-lists"></a><span data-ttu-id="9b3b0-170">针对列表的布尔操作</span><span class="sxs-lookup"><span data-stu-id="9b3b0-170">Boolean Operations on Lists</span></span>

<span data-ttu-id="9b3b0-171">[IsEmpty](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#isEmpty)函数确定列表是否包含任何元素。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-171">The [List.isEmpty](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#isEmpty) function determines whether a list has any elements.</span></span>

<span data-ttu-id="9b3b0-172">[List exists](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists)函数向列表的元素应用布尔测试，并在 `true` 有任何元素满足测试时返回。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-172">The [List.exists](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists) function applies a Boolean test to elements of a list and returns `true` if any element satisfies the test.</span></span> <span data-ttu-id="9b3b0-173">[Array.exists2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists2) 类似于，但操作在两个列表中连续的元素对。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-173">[List.exists2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists2) is similar but operates on successive pairs of elements in two lists.</span></span>

<span data-ttu-id="9b3b0-174">以下代码演示了 `List.exists` 的用法。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-174">The following code demonstrates the use of `List.exists`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet1.fs)]

<span data-ttu-id="9b3b0-175">输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="9b3b0-175">The output is as follows:</span></span>

```console
For list [0; 1; 2; 3], contains zero is true
```

<span data-ttu-id="9b3b0-176">以下示例演示了 `List.exists2` 的用法。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-176">The following example demonstrates the use of `List.exists2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet2.fs)]

<span data-ttu-id="9b3b0-177">输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="9b3b0-177">The output is as follows:</span></span>

```console
Lists [1; 2; 3; 4; 5] and [5; 4; 3; 2; 1] have at least one equal element at the same position.
```

<span data-ttu-id="9b3b0-178">如果要测试列表中的所有元素是否都满足条件，可以使用 [forall](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#forall) 。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-178">You can use [List.forall](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#forall) if you want to test whether all the elements of a list meet a condition.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet3.fs)]

<span data-ttu-id="9b3b0-179">输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="9b3b0-179">The output is as follows:</span></span>

```console
true
false
```

<span data-ttu-id="9b3b0-180">同样， [array.forall2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#forall2) 确定两个列表中相应位置的所有元素是否都满足涉及每对元素的布尔表达式。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-180">Similarly, [List.forall2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#forall2) determines whether all elements in the corresponding positions in two lists satisfy a Boolean expression that involves each pair of elements.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet4.fs)]

<span data-ttu-id="9b3b0-181">输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="9b3b0-181">The output is as follows:</span></span>

```console
true
false
```

### <a name="sort-operations-on-lists"></a><span data-ttu-id="9b3b0-182">针对列表的排序操作</span><span class="sxs-lookup"><span data-stu-id="9b3b0-182">Sort Operations on Lists</span></span>

<span data-ttu-id="9b3b0-183">[List](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sort)、 [sortBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sortBy)和[array.sortwith](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sortWith)函数对列表进行排序。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-183">The [List.sort](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sort), [List.sortBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sortBy), and [List.sortWith](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sortWith) functions sort lists.</span></span> <span data-ttu-id="9b3b0-184">排序函数可确定要使用上面三个函数中的哪一个函数。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-184">The sorting function determines which of these three functions to use.</span></span> <span data-ttu-id="9b3b0-185">`List.sort` 使用默认的泛型比较。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-185">`List.sort` uses default generic comparison.</span></span> <span data-ttu-id="9b3b0-186">泛型比较根据泛型比较函数使用全局运算符来比较值。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-186">Generic comparison uses global operators based on the generic compare function to compare values.</span></span> <span data-ttu-id="9b3b0-187">它能够有效地处理各种元素类型，例如简单数值类型、元组、记录、可区分联合、列表、数组以及任何实现 `System.IComparable` 的类型。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-187">It works efficiently with a wide variety of element types, such as simple numeric types, tuples, records, discriminated unions, lists, arrays, and any type that implements `System.IComparable`.</span></span> <span data-ttu-id="9b3b0-188">对于实现 `System.IComparable` 的类型，泛型比较将使用 `System.IComparable.CompareTo()` 函数。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-188">For types that implement `System.IComparable`, generic comparison uses the `System.IComparable.CompareTo()` function.</span></span> <span data-ttu-id="9b3b0-189">泛型比较还可处理字符串，只不过使用的是不依赖于区域性的排序顺序。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-189">Generic comparison also works with strings, but uses a culture-independent sorting order.</span></span> <span data-ttu-id="9b3b0-190">不应对不支持的类型（例如函数类型）使用泛型比较。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-190">Generic comparison should not be used on unsupported types, such as function types.</span></span> <span data-ttu-id="9b3b0-191">此外，默认泛型比较的性能最适用于小型结构化类型；对于需要经常比较和排序的大型结构化类型，请考虑实现 `System.IComparable` 并提供 `System.IComparable.CompareTo()` 方法的有效实现。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-191">Also, the performance of the default generic comparison is best for small structured types; for larger structured types that need to be compared and sorted frequently, consider implementing `System.IComparable` and providing an efficient implementation of the `System.IComparable.CompareTo()` method.</span></span>

<span data-ttu-id="9b3b0-192">`List.sortBy` 使用一个函数，此函数返回一个用作排序条件的值，而 `List.sortWith` 将比较函数用作参数。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-192">`List.sortBy` takes a function that returns a value that is used as the sort criterion, and `List.sortWith` takes a comparison function as an argument.</span></span> <span data-ttu-id="9b3b0-193">当你使用不支持比较的类型或比较需要更复杂的比较语义（对于区域性识别字符串）时，后面这两个函数会很有用。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-193">These latter two functions are useful when you are working with types that do not support comparison, or when the comparison requires more complex comparison semantics, as in the case of culture-aware strings.</span></span>

<span data-ttu-id="9b3b0-194">以下示例演示了 `List.sort` 的用法。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-194">The following example demonstrates the use of `List.sort`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet5.fs)]

<span data-ttu-id="9b3b0-195">输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="9b3b0-195">The output is as follows:</span></span>

```console
[-2; 1; 4; 5; 8]
```

<span data-ttu-id="9b3b0-196">以下示例演示了 `List.sortBy` 的用法。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-196">The following example demonstrates the use of `List.sortBy`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet6.fs)]

<span data-ttu-id="9b3b0-197">输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="9b3b0-197">The output is as follows:</span></span>

```console
[1; -2; 4; 5; 8]
```

<span data-ttu-id="9b3b0-198">下一个示例演示了 `List.sortWith` 的用法。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-198">The next example demonstrates the use of `List.sortWith`.</span></span> <span data-ttu-id="9b3b0-199">在此示例中，使用自定义比较函数 `compareWidgets` 首先比较自定义类型的一个字段，在第一个字段的值相等的情况下，再比较另一个字段。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-199">In this example, the custom comparison function `compareWidgets` is used to first compare one field of a custom type, and then another when the values of the first field are equal.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet7.fs)]

<span data-ttu-id="9b3b0-200">输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="9b3b0-200">The output is as follows:</span></span>

```console
[{ID = 92;
Rev = 1;}; {ID = 92;
Rev = 1;}; {ID = 100;
Rev = 2;}; {ID = 100;
Rev = 5;}; {ID = 110;
Rev = 1;}]
```

### <a name="search-operations-on-lists"></a><span data-ttu-id="9b3b0-201">针对列表的搜索操作</span><span class="sxs-lookup"><span data-stu-id="9b3b0-201">Search Operations on Lists</span></span>

<span data-ttu-id="9b3b0-202">可以对列表执行各种搜索操作。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-202">Numerous search operations are supported for lists.</span></span> <span data-ttu-id="9b3b0-203">最简单的 [列表查找](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#find)可用于查找与给定条件匹配的第一个元素。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-203">The simplest, [List.find](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#find), enables you to find the first element that matches a given condition.</span></span>

<span data-ttu-id="9b3b0-204">以下代码示例演示了如何使用 `List.find` 来查找列表中可被 5 整除的第一个元素。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-204">The following code example demonstrates the use of `List.find` to find the first number that is divisible by 5 in a list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet8.fs)]

<span data-ttu-id="9b3b0-205">结果为 5。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-205">The result is 5.</span></span>

<span data-ttu-id="9b3b0-206">如果必须首先转换元素，请调用 [List. pick](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#pick)，它采用一个返回选项的函数，并查找的第一个选项值为 `Some(x)` 。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-206">If the elements must be transformed first, call [List.pick](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#pick), which takes a function that returns an option, and looks for the first option value that is `Some(x)`.</span></span> <span data-ttu-id="9b3b0-207">`List.pick` 返回结果 `x`，而不是返回元素。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-207">Instead of returning the element, `List.pick` returns the result `x`.</span></span> <span data-ttu-id="9b3b0-208">如果未找到匹配的元素，则 `List.pick` 将引发 `System.Collections.Generic.KeyNotFoundException`。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-208">If no matching element is found, `List.pick` throws `System.Collections.Generic.KeyNotFoundException`.</span></span> <span data-ttu-id="9b3b0-209">以下代码显示了 `List.pick` 的用法。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-209">The following code shows the use of `List.pick`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet9.fs)]

<span data-ttu-id="9b3b0-210">输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="9b3b0-210">The output is as follows:</span></span>

```console
"b"
```

<span data-ttu-id="9b3b0-211">另一组搜索操作、 [tryFind](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#tryFind) 和相关函数返回一个选项值。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-211">Another group of search operations, [List.tryFind](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#tryFind) and related functions, return an option value.</span></span> <span data-ttu-id="9b3b0-212">`List.tryFind` 函数返回列表中满足条件的第一个元素（如果该元素存在）；如果该元素不存在，则返回选项值 `None`。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-212">The `List.tryFind` function returns the first element of a list that satisfies a condition if such an element exists, but the option value `None` if not.</span></span> <span data-ttu-id="9b3b0-213">变体 [列表。](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#tryFindIndex) 如果找到元素，则为 array.tryfindindex 返回元素的索引，而不是元素本身。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-213">The variation [List.tryFindIndex](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#tryFindIndex) returns the index of the element, if one is found, rather than the element itself.</span></span> <span data-ttu-id="9b3b0-214">下面的代码中阐释了这些函数。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-214">These functions are illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet10.fs)]

<span data-ttu-id="9b3b0-215">输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="9b3b0-215">The output is as follows:</span></span>

```console
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a><span data-ttu-id="9b3b0-216">针对列表的算术运算</span><span class="sxs-lookup"><span data-stu-id="9b3b0-216">Arithmetic Operations on Lists</span></span>

<span data-ttu-id="9b3b0-217">常见算术运算（如 sum 和 average）内置于 [列表模块](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html)中。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-217">Common arithmetic operations such as sum and average are built into the [List module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span></span> <span data-ttu-id="9b3b0-218">若要使用 [list. sum](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sum)，List 元素类型必须支持 `+` 运算符并且值为零。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-218">To work with [List.sum](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sum), the list element type must support the `+` operator and have a zero value.</span></span> <span data-ttu-id="9b3b0-219">所有内置算术类型都满足这些条件。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-219">All built-in arithmetic types satisfy these conditions.</span></span> <span data-ttu-id="9b3b0-220">若要使用 [List](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#average)，元素类型必须支持不含余数的除法，这会排除整数类型但允许浮点类型。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-220">To work with [List.average](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#average), the element type must support division without a remainder, which excludes integral types but allows for floating point types.</span></span> <span data-ttu-id="9b3b0-221">[SumBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sumBy)和[averageBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#averageBy)函数将函数作为参数使用，此函数的结果用于计算 sum 或 average 的值。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-221">The [List.sumBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sumBy) and [List.averageBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#averageBy) functions take a function as a parameter, and this function's results are used to calculate the values for the sum or average.</span></span>

<span data-ttu-id="9b3b0-222">以下代码演示了 `List.sum`、`List.sumBy` 和 `List.average` 的用法。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-222">The following code demonstrates the use of `List.sum`, `List.sumBy`, and `List.average`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet11.fs)]

<span data-ttu-id="9b3b0-223">输出为 `1.000000`。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-223">The output is `1.000000`.</span></span>

<span data-ttu-id="9b3b0-224">以下代码显示了 `List.averageBy` 的用法。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-224">The following code shows the use of `List.averageBy`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet12.fs)]

<span data-ttu-id="9b3b0-225">输出为 `5.5`。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-225">The output is `5.5`.</span></span>

### <a name="lists-and-tuples"></a><span data-ttu-id="9b3b0-226">列表和元组</span><span class="sxs-lookup"><span data-stu-id="9b3b0-226">Lists and Tuples</span></span>

<span data-ttu-id="9b3b0-227">包含元组的列表可由压缩和解压缩函数操作。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-227">Lists that contain tuples can be manipulated by zip and unzip functions.</span></span> <span data-ttu-id="9b3b0-228">这些函数将两个包含单值的列表合并为一个元组列表，或将一个元组列表分成两个包含单值的列表。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-228">These functions combine two lists of single values into one list of tuples or separate one list of tuples into two lists of single values.</span></span> <span data-ttu-id="9b3b0-229">最简单的 [List.zip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#zip) 函数使用单个元素的两个列表，并生成一个元组对列表。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-229">The simplest [List.zip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#zip) function takes two lists of single elements and produces a single list of tuple pairs.</span></span> <span data-ttu-id="9b3b0-230">另一个版本（ [List.zip3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#zip3)）采用单个元素的三个列表，并生成包含三个元素的元组的单个列表。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-230">Another version, [List.zip3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#zip3), takes three lists of single elements and produces a single list of tuples that have three elements.</span></span> <span data-ttu-id="9b3b0-231">以下代码示例演示了 `List.zip` 的用法。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-231">The following code example demonstrates the use of `List.zip`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet13.fs)]

<span data-ttu-id="9b3b0-232">输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="9b3b0-232">The output is as follows:</span></span>

```console
[(1, -1); (2, -2); (3; -3)]
```

<span data-ttu-id="9b3b0-233">以下代码示例演示了 `List.zip3` 的用法。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-233">The following code example demonstrates the use of `List.zip3`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet14.fs)]

<span data-ttu-id="9b3b0-234">输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="9b3b0-234">The output is as follows:</span></span>

```console
[(1, -1, 0); (2, -2, 0); (3, -3, 0)]
```

<span data-ttu-id="9b3b0-235">对应的解压缩版本（ [list.unzip3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#unzip3) [）采用](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#unzip)元组的列表并返回元组中的列表，其中，第一个列表包含每个元组中的第一个元素，第二个列表包含每个元组的第二个元素，依此类推。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-235">The corresponding unzip versions, [List.unzip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#unzip) and [List.unzip3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#unzip3), take lists of tuples and return lists in a tuple, where the first list contains all the elements that were first in each tuple, and the second list contains the second element of each tuple, and so on.</span></span>

<span data-ttu-id="9b3b0-236">下面的代码示例演示如何使用[列表。](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21)</span><span class="sxs-lookup"><span data-stu-id="9b3b0-236">The following code example demonstrates the use of [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet15.fs)]

<span data-ttu-id="9b3b0-237">输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="9b3b0-237">The output is as follows:</span></span>

```console
([1; 3], [2; 4])
[1; 3] [2; 4]
```

<span data-ttu-id="9b3b0-238">下面的代码示例演示如何使用 [list.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4)。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-238">The following code example demonstrates the use of [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet16.fs)]

<span data-ttu-id="9b3b0-239">输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="9b3b0-239">The output is as follows:</span></span>

```console
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a><span data-ttu-id="9b3b0-240">针对列表元素的操作</span><span class="sxs-lookup"><span data-stu-id="9b3b0-240">Operating on List Elements</span></span>

<span data-ttu-id="9b3b0-241">F# 支持针对列表元素执行各种操作。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-241">F# supports a variety of operations on list elements.</span></span> <span data-ttu-id="9b3b0-242">最简单的是 [iter](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iter)，它使你可以对列表的每个元素调用函数。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-242">The simplest is [List.iter](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iter), which enables you to call a function on every element of a list.</span></span> <span data-ttu-id="9b3b0-243">变体包括[array.iter2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iter2)，它使你能够对两个列表的元素执行操作， [array.iteri](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iteri)，这类似于， `List.iter` 只不过每个元素的索引将作为参数传递给为每个元素调用的函数和[list.iteri2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iteri2)，这是和功能的组合。 `List.iter2` `List.iteri`</span><span class="sxs-lookup"><span data-stu-id="9b3b0-243">Variations include [List.iter2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iter2), which enables you to perform an operation on elements of two lists, [List.iteri](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iteri), which is like `List.iter` except that the index of each element is passed as an argument to the function that is called for each element, and [List.iteri2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iteri2), which is a combination of the functionality of `List.iter2` and `List.iteri`.</span></span> <span data-ttu-id="9b3b0-244">以下代码示例阐释了这些函数。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-244">The following code example illustrates these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet17.fs)]

<span data-ttu-id="9b3b0-245">输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="9b3b0-245">The output is as follows:</span></span>

```console
List.iter: element is 1
List.iter: element is 2
List.iter: element is 3
List.iteri: element 0 is 1
List.iteri: element 1 is 2
List.iteri: element 2 is 3
List.iter2: elements are 1 4
List.iter2: elements are 2 5
List.iter2: elements are 3 6
List.iteri2: element 0 of list1 is 1; element 0 of list2 is 4
List.iteri2: element 1 of list1 is 2; element 1 of list2 is 5
List.iteri2: element 2 of list1 is 3; element 2 of list2 is 6
```

<span data-ttu-id="9b3b0-246">转换列表元素的另一个常用函数是 [list](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map)，这使你可以将函数应用于列表的每个元素，并将所有结果放入新列表中。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-246">Another frequently used function that transforms list elements is [List.map](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map), which enables you to apply a function to each element of a list and put all the results into a new list.</span></span> <span data-ttu-id="9b3b0-247">[Array.map2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map2) 和 [list.map3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map3) 是采用多个列表的变体。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-247">[List.map2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map2) and [List.map3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map3) are variations that take multiple lists.</span></span> <span data-ttu-id="9b3b0-248">还可以使用[list.mapi2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#mapi2)，如果除了元素外，还需要将每个元素的索引传递给[函数。](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#mapi)</span><span class="sxs-lookup"><span data-stu-id="9b3b0-248">You can also use [List.mapi](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#mapi) and [List.mapi2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#mapi2), if, in addition to the element, the function needs to be passed the index of each element.</span></span> <span data-ttu-id="9b3b0-249">`List.mapi2` 和 `List.mapi` 之间的唯一区别在于 `List.mapi2` 使用了两个列表。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-249">The only difference between `List.mapi2` and `List.mapi` is that `List.mapi2` works with two lists.</span></span> <span data-ttu-id="9b3b0-250">下面的示例阐释了[List。](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map)</span><span class="sxs-lookup"><span data-stu-id="9b3b0-250">The following example illustrates [List.map](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet18.fs)]

<span data-ttu-id="9b3b0-251">输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="9b3b0-251">The output is as follows:</span></span>

```console
[2; 3; 4]
```

<span data-ttu-id="9b3b0-252">以下示例演示如何使用 `List.map2`。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-252">The following example shows the use of `List.map2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet19.fs)]

<span data-ttu-id="9b3b0-253">输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="9b3b0-253">The output is as follows:</span></span>

```console
[5; 7; 9]
```

<span data-ttu-id="9b3b0-254">以下示例演示如何使用 `List.map3`。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-254">The following example shows the use of `List.map3`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet20.fs)]

<span data-ttu-id="9b3b0-255">输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="9b3b0-255">The output is as follows:</span></span>

```console
[7; 10; 13]
```

<span data-ttu-id="9b3b0-256">以下示例演示如何使用 `List.mapi`。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-256">The following example shows the use of `List.mapi`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet21.fs)]

<span data-ttu-id="9b3b0-257">输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="9b3b0-257">The output is as follows:</span></span>

```console
[1; 3; 5]
```

<span data-ttu-id="9b3b0-258">以下示例演示如何使用 `List.mapi2`。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-258">The following example shows the use of `List.mapi2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet22.fs)]

<span data-ttu-id="9b3b0-259">输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="9b3b0-259">The output is as follows:</span></span>

```console
[0; 7; 18]
```

<span data-ttu-id="9b3b0-260">[List. collect](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#collect) 类似于 `List.map` ，只不过每个元素都生成一个列表，并将所有这些列表连接到一个最终列表。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-260">[List.collect](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#collect) is like `List.map`, except that each element produces a list and all these lists are concatenated into a final list.</span></span> <span data-ttu-id="9b3b0-261">在以下代码中，列表的每个元素均生成三个数字。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-261">In the following code, each element of the list generates three numbers.</span></span> <span data-ttu-id="9b3b0-262">所有这些数字将收集到一个列表中。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-262">These are all collected into one list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet23.fs)]

<span data-ttu-id="9b3b0-263">输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="9b3b0-263">The output is as follows:</span></span>

```console
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

<span data-ttu-id="9b3b0-264">你还可以使用 [List. filter](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#filter)，它采用布尔条件，并生成仅包含满足给定条件的元素的新列表。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-264">You can also use [List.filter](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#filter), which takes a Boolean condition and produces a new list that consists only of elements that satisfy the given condition.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet24.fs)]

<span data-ttu-id="9b3b0-265">生成的列表为 `[2; 4; 6]`。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-265">The resulting list is `[2; 4; 6]`.</span></span>

<span data-ttu-id="9b3b0-266">Map 和 filter，List 的组合 [。选择](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#choose) 使您能够同时转换和选择元素。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-266">A combination of map and filter, [List.choose](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#choose) enables you to transform and select elements at the same time.</span></span> <span data-ttu-id="9b3b0-267">`List.choose` 对列表的每个元素应用一个返回选项的函数，并在该函数返回选项值 `Some` 时为元素返回新的结果列表。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-267">`List.choose` applies a function that returns an option to each element of a list, and returns a new list of the results for elements when the function returns the option value `Some`.</span></span>

<span data-ttu-id="9b3b0-268">以下代码演示了如何使用 `List.choose` 从单词列表中选择大写单词。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-268">The following code demonstrates the use of `List.choose` to select capitalized words out of a list of words.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet25.fs)]

<span data-ttu-id="9b3b0-269">输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="9b3b0-269">The output is as follows:</span></span>

```console
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a><span data-ttu-id="9b3b0-270">针对多个列表的操作</span><span class="sxs-lookup"><span data-stu-id="9b3b0-270">Operating on Multiple Lists</span></span>

<span data-ttu-id="9b3b0-271">可以将多个列表联接在一起。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-271">Lists can be joined together.</span></span> <span data-ttu-id="9b3b0-272">若要将两个列表联接为一个列表，请使用[List。](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#append)</span><span class="sxs-lookup"><span data-stu-id="9b3b0-272">To join two lists into one, use [List.append](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#append).</span></span> <span data-ttu-id="9b3b0-273">若要加入两个以上的列表，请使用[列表。](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#concat)</span><span class="sxs-lookup"><span data-stu-id="9b3b0-273">To join more than two lists, use [List.concat](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#concat).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet26.fs)]

### <a name="fold-and-scan-operations"></a><span data-ttu-id="9b3b0-274">Fold 和 Scan 操作</span><span class="sxs-lookup"><span data-stu-id="9b3b0-274">Fold and Scan Operations</span></span>

<span data-ttu-id="9b3b0-275">一些列表操作涉及所有列表元素之间的相互依赖关系。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-275">Some list operations involve interdependencies between all of the list elements.</span></span> <span data-ttu-id="9b3b0-276">折叠和扫描操作类似于， `List.iter` `List.map` 在中，您对每个元素调用一个函数，但这些操作提供了一个名为 *累加器* 的附加参数，该参数通过计算传递信息。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-276">The fold and scan operations are like `List.iter` and `List.map` in that you invoke a function on each element, but these operations provide an additional parameter called the *accumulator* that carries information through the computation.</span></span>

<span data-ttu-id="9b3b0-277">使用 `List.fold` 可对列表执行计算。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-277">Use `List.fold` to perform a calculation on a list.</span></span>

<span data-ttu-id="9b3b0-278">下面的代码示例演示如何使用 [List](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#fold) 进行各种操作。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-278">The following code example demonstrates the use of [List.fold](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#fold) to perform various operations.</span></span>

<span data-ttu-id="9b3b0-279">将遍历列表；累加器 `acc` 是一个在计算过程中不断传递的值。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-279">The list is traversed; the accumulator `acc` is a value that is passed along as the calculation proceeds.</span></span> <span data-ttu-id="9b3b0-280">第一个参数采用累加器和列表元素，并返回针对列表元素的计算的中间结果。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-280">The first argument takes the accumulator and the list element, and returns the interim result of the calculation for that list element.</span></span> <span data-ttu-id="9b3b0-281">第二个自变量为累加器的初始值。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-281">The second argument is the initial value of the accumulator.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet27.fs)]

<span data-ttu-id="9b3b0-282">这些函数的各个版本（函数名中有一个数字）对多个列表执行操作。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-282">The versions of these functions that have a digit in the function name operate on more than one list.</span></span> <span data-ttu-id="9b3b0-283">例如， [list.fold2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#fold2) 对两个列表执行计算。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-283">For example, [List.fold2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#fold2) performs computations on two lists.</span></span>

<span data-ttu-id="9b3b0-284">以下示例演示了 `List.fold2` 的用法。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-284">The following example demonstrates the use of `List.fold2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet28.fs)]

<span data-ttu-id="9b3b0-285">`List.fold` 和 [列表。](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#scan) 中的扫描不同于 `List.fold` 返回额外参数的最终值，而 `List.scan` 是返回中间值的列表 (以及额外参数) 的最终值。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-285">`List.fold` and [List.scan](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#scan) differ in that `List.fold` returns the final value of the extra parameter, but `List.scan` returns the list of the intermediate values (along with the final value) of the extra parameter.</span></span>

<span data-ttu-id="9b3b0-286">其中每个函数都包含反向变体（例如 [list.foldback](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#foldBack)），这不同于列表的遍历顺序和参数的顺序。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-286">Each of these functions includes a reverse variation, for example, [List.foldBack](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#foldBack), which differs in the order in which the list is traversed and the order of the arguments.</span></span> <span data-ttu-id="9b3b0-287">另外， `List.fold` 和 `List.foldBack` 具有变体、 [list.fold2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#fold2) 和 [array.foldback2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#foldBack2)，这两个列表的长度相等。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-287">Also, `List.fold` and `List.foldBack` have variations, [List.fold2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#fold2) and [List.foldBack2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#foldBack2), that take two lists of equal length.</span></span> <span data-ttu-id="9b3b0-288">对每个元素执行的函数可以使用两个列表的对应元素来执行一些操作。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-288">The function that executes on each element can use corresponding elements of both lists to perform some action.</span></span> <span data-ttu-id="9b3b0-289">两个列表的元素类型可以不同（如以下示例所示），其中一个列表包含银行帐户的交易金额，而另一个列表包含交易的类型：存款或取款。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-289">The element types of the two lists can be different, as in the following example, in which one list contains transaction amounts for a bank account, and the other list contains the type of transaction: deposit or withdrawal.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet29.fs)]

<span data-ttu-id="9b3b0-290">对于类似于求和这样的计算，`List.fold` 和 `List.foldBack` 具有相同的效果，因为结果不依赖于遍历顺序。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-290">For a calculation like summation, `List.fold` and `List.foldBack` have the same effect because the result does not depend on the order of traversal.</span></span> <span data-ttu-id="9b3b0-291">在以下示例中，`List.foldBack` 用于在列表中添加元素。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-291">In the following example, `List.foldBack` is used to add the elements in a list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet30.fs)]

<span data-ttu-id="9b3b0-292">以下示例将返回到银行帐户示例。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-292">The following example returns to the bank account example.</span></span> <span data-ttu-id="9b3b0-293">这次，添加一个新的事务类型：利息计算。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-293">This time a new transaction type is added: an interest calculation.</span></span> <span data-ttu-id="9b3b0-294">期末余额现在取决于交易顺序。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-294">The ending balance now depends on the order of transactions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet34.fs)]

<span data-ttu-id="9b3b0-295">函数 [列表](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#reduce) 类似于 `List.fold` 和 `List.scan` ，只不过只 `List.reduce` 需使用元素类型的两个自变量（而不是一个），而是使用一个函数，该函数采用元素类型的两个参数而不是一个参数，这意味着它将存储计算的中间结果。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-295">The function [List.reduce](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#reduce) is somewhat like `List.fold` and `List.scan`, except that instead of passing around a separate accumulator, `List.reduce` takes a function that takes two arguments of the element type instead of just one, and one of those arguments acts as the accumulator, meaning that it stores the intermediate result of the computation.</span></span> <span data-ttu-id="9b3b0-296">`List.reduce` 首先对前两个列表元素执行操作，然后将操作的结果和下一个元素一起使用。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-296">`List.reduce` starts by operating on the first two list elements, and then uses the result of the operation along with the next element.</span></span> <span data-ttu-id="9b3b0-297">由于不存在具有自己的类型的单独累加器，因此只可以在累加器和元素类型的类型相同时，使用 `List.reduce` 代替 `List.fold`。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-297">Because there is not a separate accumulator that has its own type, `List.reduce` can be used in place of `List.fold` only when the accumulator and the element type have the same type.</span></span> <span data-ttu-id="9b3b0-298">以下代码演示了 `List.reduce` 的用法。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-298">The following code demonstrates the use of `List.reduce`.</span></span> <span data-ttu-id="9b3b0-299">如果提供的列表中不包含任何元素，则 `List.reduce` 将引发异常。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-299">`List.reduce` throws an exception if the list provided has no elements.</span></span>

<span data-ttu-id="9b3b0-300">在以下代码中，对 lambda 表达式的第一个调用提供了自变量 2 和 4，并返回 6；下一个调用提供了自变量 6 和 10，因此结果为 16。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-300">In the following code, the first call to the lambda expression is given the arguments 2 and 4, and returns 6, and the next call is given the arguments 6 and 10, so the result is 16.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet33.fs)]

### <a name="converting-between-lists-and-other-collection-types"></a><span data-ttu-id="9b3b0-301">在列表和其他集合类型之间进行转换</span><span class="sxs-lookup"><span data-stu-id="9b3b0-301">Converting Between Lists and Other Collection Types</span></span>

<span data-ttu-id="9b3b0-302">`List` 模块提供了用于来回转换序列和数组的函数。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-302">The `List` module provides functions for converting to and from both sequences and arrays.</span></span> <span data-ttu-id="9b3b0-303">若要转换为序列，请使用 [list.toseq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#toSeq) 或 [list.ofseq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#ofSeq)。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-303">To convert to or from a sequence, use [List.toSeq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#toSeq) or [List.ofSeq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#ofSeq).</span></span> <span data-ttu-id="9b3b0-304">若要转换为数组，请使用 [toArray](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#toArray) 或 [list.ofarray](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#ofArray)。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-304">To convert to or from an array, use [List.toArray](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#toArray) or [List.ofArray](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#ofArray).</span></span>

### <a name="additional-operations"></a><span data-ttu-id="9b3b0-305">其他操作</span><span class="sxs-lookup"><span data-stu-id="9b3b0-305">Additional Operations</span></span>

<span data-ttu-id="9b3b0-306">有关列表中其他操作的信息，请参阅库参考主题 [列表模块](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html)。</span><span class="sxs-lookup"><span data-stu-id="9b3b0-306">For information about additional operations on lists, see the library reference topic [List Module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span></span>

## <a name="see-also"></a><span data-ttu-id="9b3b0-307">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9b3b0-307">See also</span></span>

- [<span data-ttu-id="9b3b0-308">F# 语言参考</span><span class="sxs-lookup"><span data-stu-id="9b3b0-308">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="9b3b0-309">F# 类型</span><span class="sxs-lookup"><span data-stu-id="9b3b0-309">F# Types</span></span>](fsharp-types.md)
- [<span data-ttu-id="9b3b0-310">序列</span><span class="sxs-lookup"><span data-stu-id="9b3b0-310">Sequences</span></span>](sequences.md)
- [<span data-ttu-id="9b3b0-311">数组</span><span class="sxs-lookup"><span data-stu-id="9b3b0-311">Arrays</span></span>](arrays.md)
- [<span data-ttu-id="9b3b0-312">选项</span><span class="sxs-lookup"><span data-stu-id="9b3b0-312">Options</span></span>](options.md)

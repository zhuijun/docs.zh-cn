---
title: 可变类型
description: '了解如何使用 F # 挠性类型批注，该批注指示参数、变量或值具有与指定类型兼容的类型。'
ms.date: 08/15/2020
ms.openlocfilehash: 44241ad082cd7f3de9e0cc6a48b8a8946e7b33d3
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557745"
---
# <a name="flexible-types"></a><span data-ttu-id="8117a-103">可变类型</span><span class="sxs-lookup"><span data-stu-id="8117a-103">Flexible Types</span></span>

<span data-ttu-id="8117a-104">*可变类型批注*指示参数、变量或值具有与指定类型兼容的类型，其中的兼容性由类或接口的面向对象的层次结构中的位置确定。</span><span class="sxs-lookup"><span data-stu-id="8117a-104">A *flexible type annotation* indicates that a parameter, variable, or value has a type that is compatible with a specified type, where compatibility is determined by position in an object-oriented hierarchy of classes or interfaces.</span></span> <span data-ttu-id="8117a-105">当不发生类型层次结构中较高的类型的自动转换但仍希望使你的功能可以与层次结构中的任何类型或实现接口的任何类型一起使用时，灵活类型特别有用。</span><span class="sxs-lookup"><span data-stu-id="8117a-105">Flexible types are useful specifically when the automatic conversion to types higher in the type hierarchy does not occur but you still want to enable your functionality to work with any type in the hierarchy or any type that implements an interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="8117a-106">语法</span><span class="sxs-lookup"><span data-stu-id="8117a-106">Syntax</span></span>

```fsharp
#type
```

## <a name="remarks"></a><span data-ttu-id="8117a-107">备注</span><span class="sxs-lookup"><span data-stu-id="8117a-107">Remarks</span></span>

<span data-ttu-id="8117a-108">在前面的语法中， *类型* 表示基类型或接口。</span><span class="sxs-lookup"><span data-stu-id="8117a-108">In the previous syntax, *type* represents a base type or an interface.</span></span>

<span data-ttu-id="8117a-109">灵活类型等效于具有约束的泛型类型，该约束将允许的类型限制为与基类型或接口类型兼容的类型。</span><span class="sxs-lookup"><span data-stu-id="8117a-109">A flexible type is equivalent to a generic type that has a constraint that limits the allowed types to types that are compatible with the base or interface type.</span></span> <span data-ttu-id="8117a-110">也就是说，以下两行代码是等效的。</span><span class="sxs-lookup"><span data-stu-id="8117a-110">That is, the following two lines of code are equivalent.</span></span>

```fsharp
#SomeType

'T when 'T :> SomeType
```

<span data-ttu-id="8117a-111">灵活类型在多种情况下都很有用。</span><span class="sxs-lookup"><span data-stu-id="8117a-111">Flexible types are useful in several types of situations.</span></span> <span data-ttu-id="8117a-112">例如，如果您的 order 函数 (将函数作为参数) 的函数，则使函数返回灵活类型通常很有用。</span><span class="sxs-lookup"><span data-stu-id="8117a-112">For example, when you have a higher order function (a function that takes a function as an argument), it is often useful to have the function return a flexible type.</span></span> <span data-ttu-id="8117a-113">在下面的示例中，在中使用带序列参数的灵活类型 `iterate2` 使高阶函数能够使用生成序列、数组、列表和任何其他可枚举类型的函数。</span><span class="sxs-lookup"><span data-stu-id="8117a-113">In the following example, the use of a flexible type with a sequence argument in `iterate2` enables the higher order function to work with functions that generate sequences, arrays, lists, and any other enumerable type.</span></span>

<span data-ttu-id="8117a-114">请考虑以下两个函数，其中一个函数返回一个序列，另一个返回一个可变类型。</span><span class="sxs-lookup"><span data-stu-id="8117a-114">Consider the following two functions, one of which returns a sequence, the other of which returns a flexible type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

<span data-ttu-id="8117a-115">作为另一个示例，请考虑 [Seq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#concat) library 函数：</span><span class="sxs-lookup"><span data-stu-id="8117a-115">As another example, consider the [Seq.concat](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#concat) library function:</span></span>

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

<span data-ttu-id="8117a-116">可以将以下任一可枚举序列传递到此函数：</span><span class="sxs-lookup"><span data-stu-id="8117a-116">You can pass any of the following enumerable sequences to this function:</span></span>

- <span data-ttu-id="8117a-117">列表列表</span><span class="sxs-lookup"><span data-stu-id="8117a-117">A list of lists</span></span>
- <span data-ttu-id="8117a-118">数组的列表</span><span class="sxs-lookup"><span data-stu-id="8117a-118">A list of arrays</span></span>
- <span data-ttu-id="8117a-119">列表的数组</span><span class="sxs-lookup"><span data-stu-id="8117a-119">An array of lists</span></span>
- <span data-ttu-id="8117a-120">序列数组</span><span class="sxs-lookup"><span data-stu-id="8117a-120">An array of sequences</span></span>
- <span data-ttu-id="8117a-121">可枚举序列的任何其他组合</span><span class="sxs-lookup"><span data-stu-id="8117a-121">Any other combination of enumerable sequences</span></span>

<span data-ttu-id="8117a-122">下面的代码使用 `Seq.concat` 灵活的类型来演示可支持的方案。</span><span class="sxs-lookup"><span data-stu-id="8117a-122">The following code uses `Seq.concat` to demonstrate the scenarios that you can support by using flexible types.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

<span data-ttu-id="8117a-123">输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="8117a-123">The output is as follows.</span></span>

```console
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

<span data-ttu-id="8117a-124">在 F # 中，与在其他面向对象的语言中一样，某些上下文中实现接口的派生类型或类型会自动转换为基类型或接口类型。</span><span class="sxs-lookup"><span data-stu-id="8117a-124">In F#, as in other object-oriented languages, there are contexts in which derived types or types that implement interfaces are automatically converted to a base type or interface type.</span></span> <span data-ttu-id="8117a-125">这些自动转换在直接参数中进行，但当类型位于从属位置时，不会发生在作为更复杂类型（如函数类型的返回类型）或类型参数的一部分的情况下。</span><span class="sxs-lookup"><span data-stu-id="8117a-125">These automatic conversions occur in direct arguments, but not when the type is in a subordinate position, as part of a more complex type such as a return type of a function type, or as a type argument.</span></span> <span data-ttu-id="8117a-126">因此，当您要将它应用到的类型是更复杂类型的一部分时，灵活的类型表示法主要非常有用。</span><span class="sxs-lookup"><span data-stu-id="8117a-126">Thus, the flexible type notation is primarily useful when the type you are applying it to is part of a more complex type.</span></span>

## <a name="see-also"></a><span data-ttu-id="8117a-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8117a-127">See also</span></span>

- [<span data-ttu-id="8117a-128">F# 语言参考</span><span class="sxs-lookup"><span data-stu-id="8117a-128">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="8117a-129">泛型</span><span class="sxs-lookup"><span data-stu-id="8117a-129">Generics</span></span>](./generics/index.md)

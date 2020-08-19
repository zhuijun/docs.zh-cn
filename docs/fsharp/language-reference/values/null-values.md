---
title: Null 值
description: '了解如何在 F # 编程语言中使用 null 值。'
ms.date: 08/15/2020
ms.openlocfilehash: 3b2c7ebe7b8eff08f7c3e76b9715ccab1bbd5d36
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558343"
---
# <a name="null-values"></a><span data-ttu-id="71ad6-103">Null 值</span><span class="sxs-lookup"><span data-stu-id="71ad6-103">Null Values</span></span>

<span data-ttu-id="71ad6-104">本主题介绍如何在 F # 中使用 null 值。</span><span class="sxs-lookup"><span data-stu-id="71ad6-104">This topic describes how the null value is used in F#.</span></span>

## <a name="null-value"></a><span data-ttu-id="71ad6-105">空值</span><span class="sxs-lookup"><span data-stu-id="71ad6-105">Null Value</span></span>

<span data-ttu-id="71ad6-106">Null 值通常不在 F # 中用于值或变量。</span><span class="sxs-lookup"><span data-stu-id="71ad6-106">The null value is not normally used in F# for values or variables.</span></span> <span data-ttu-id="71ad6-107">但是，在某些情况下，null 显示为异常值。</span><span class="sxs-lookup"><span data-stu-id="71ad6-107">However, null appears as an abnormal value in certain situations.</span></span> <span data-ttu-id="71ad6-108">如果在 F # 中定义了类型，则不允许将 null 作为常规值，除非将 [AllowNullLiteral](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-allownullliteralattribute.html#Value) 属性应用于该类型。</span><span class="sxs-lookup"><span data-stu-id="71ad6-108">If a type is defined in F#, null is not permitted as a regular value unless the [AllowNullLiteral](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-allownullliteralattribute.html#Value) attribute is applied to the type.</span></span> <span data-ttu-id="71ad6-109">如果某个类型是在其他某个 .NET 语言中定义的，则 null 是可能的值，当您与此类类型进行互操作时，F # 代码可能会遇到 null 值。</span><span class="sxs-lookup"><span data-stu-id="71ad6-109">If a type is defined in some other .NET language, null is a possible value, and when you are interoperating with such types, your F# code might encounter null values.</span></span>

<span data-ttu-id="71ad6-110">对于 F # 中定义并严格从 F # 中使用的类型，使用 F # 库直接创建 null 值的唯一方法是使用 [unchecked.defaultof](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-operators-unchecked.html#defaultof) 或 [array.zerocreate](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zeroCreate)。</span><span class="sxs-lookup"><span data-stu-id="71ad6-110">For a type defined in F# and used strictly from F#, the only way to create a null value using the F# library directly is to use [Unchecked.defaultof](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-operators-unchecked.html#defaultof) or [Array.zeroCreate](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zeroCreate).</span></span> <span data-ttu-id="71ad6-111">但是，对于其他 .NET 语言中使用的 F # 类型，或者如果使用的是不是用 F # 编写的 API （如 .NET Framework），则可能会出现 null 值。</span><span class="sxs-lookup"><span data-stu-id="71ad6-111">However, for an F# type that is used from other .NET languages, or if you are using that type with an API that is not written in F#, such as the .NET Framework, null values can occur.</span></span>

<span data-ttu-id="71ad6-112">`option`如果可以在另一种 .net 语言中使用具有可能为 null 值的引用变量，则可以在 F # 中使用类型。</span><span class="sxs-lookup"><span data-stu-id="71ad6-112">You can use the `option` type in F# when you might use a reference variable with a possible null value in another .NET language.</span></span> <span data-ttu-id="71ad6-113">`option`如果没有对象，则可以使用选项值，而不是使用 F # 类型的 null `None` 。</span><span class="sxs-lookup"><span data-stu-id="71ad6-113">Instead of null, with an F# `option` type, you use the option value `None` if there is no object.</span></span> <span data-ttu-id="71ad6-114">`Some(obj)`当有对象时，可将选项值用于对象 `obj` 。</span><span class="sxs-lookup"><span data-stu-id="71ad6-114">You use the option value `Some(obj)` with an object `obj` when there is an object.</span></span> <span data-ttu-id="71ad6-115">有关详细信息，请参阅 [选项](../options.md)。</span><span class="sxs-lookup"><span data-stu-id="71ad6-115">For more information, see [Options](../options.md).</span></span> <span data-ttu-id="71ad6-116">请注意， `null` 如果的为，则仍可将值打包到选项中 `Some x` `x` `null` 。</span><span class="sxs-lookup"><span data-stu-id="71ad6-116">Note that you can still pack a `null` value into an Option if, for `Some x`, `x` happens to be `null`.</span></span> <span data-ttu-id="71ad6-117">因此，在值为时使用非常重要 `None` `null` 。</span><span class="sxs-lookup"><span data-stu-id="71ad6-117">Because of this, it is important you use `None` when a value is `null`.</span></span>

<span data-ttu-id="71ad6-118">`null`关键字是 F # 语言中的有效关键字，当你使用以其他 .net 语言编写的 .NET Framework api 或其他 api 时，你必须使用它。</span><span class="sxs-lookup"><span data-stu-id="71ad6-118">The `null` keyword is a valid keyword in the F# language, and you have to use it when you are working with .NET Framework APIs or other APIs that are written in another .NET language.</span></span> <span data-ttu-id="71ad6-119">在以下两种情况下，您可能需要 null 值：调用 .NET API 并将 null 值作为参数传递，以及从 .NET 方法调用解释返回值或输出参数。</span><span class="sxs-lookup"><span data-stu-id="71ad6-119">The two situations in which you might need a null value are when you call a .NET API and pass a null value as an argument, and when you interpret the return value or an output parameter from a .NET method call.</span></span>

<span data-ttu-id="71ad6-120">若要将 null 值传递到 .NET 方法，只需 `null` 在调用代码中使用关键字。</span><span class="sxs-lookup"><span data-stu-id="71ad6-120">To pass a null value to a .NET method, just use the `null` keyword in the calling code.</span></span> <span data-ttu-id="71ad6-121">下面的代码示例阐释了这一点。</span><span class="sxs-lookup"><span data-stu-id="71ad6-121">The following code example illustrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

<span data-ttu-id="71ad6-122">若要解释从 .NET 方法获取的 null 值，请在可以时使用模式匹配。</span><span class="sxs-lookup"><span data-stu-id="71ad6-122">To interpret a null value that is obtained from a .NET method, use pattern matching if you can.</span></span> <span data-ttu-id="71ad6-123">下面的代码示例演示如何使用模式匹配来解释在 `ReadLine` 其尝试读取超出输入流末尾时返回的 null 值。</span><span class="sxs-lookup"><span data-stu-id="71ad6-123">The following code example shows how to use pattern matching to interpret the null value that is returned from `ReadLine` when it tries to read past the end of an input stream.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

<span data-ttu-id="71ad6-124">F # 类型的 Null 值还可以通过其他方式生成，例如，在使用时，将 `Array.zeroCreate` 调用 `Unchecked.defaultof` 。</span><span class="sxs-lookup"><span data-stu-id="71ad6-124">Null values for F# types can also be generated in other ways, such as when you use `Array.zeroCreate`, which calls `Unchecked.defaultof`.</span></span> <span data-ttu-id="71ad6-125">必须谨慎处理此类代码，使封装的值保持为空值。</span><span class="sxs-lookup"><span data-stu-id="71ad6-125">You must be careful with such code to keep the null values encapsulated.</span></span> <span data-ttu-id="71ad6-126">在仅用于 F # 的库中，无需在每个函数中检查 null 值。</span><span class="sxs-lookup"><span data-stu-id="71ad6-126">In a library intended only for F#, you do not have to check for null values in every function.</span></span> <span data-ttu-id="71ad6-127">如果要编写与其他 .NET 语言的互操作性的库，则可能必须添加对 null 输入参数的检查并引发 `ArgumentNullException` ，就像在 c # 或 Visual Basic 代码中执行的操作一样。</span><span class="sxs-lookup"><span data-stu-id="71ad6-127">If you are writing a library for interoperation with other .NET languages, you might have to add checks for null input parameters and throw an `ArgumentNullException`, just as you do in C# or Visual Basic code.</span></span>

<span data-ttu-id="71ad6-128">可以使用以下代码检查任意值是否为 null。</span><span class="sxs-lookup"><span data-stu-id="71ad6-128">You can use the following code to check if an arbitrary value is null.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a><span data-ttu-id="71ad6-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="71ad6-129">See also</span></span>

- [<span data-ttu-id="71ad6-130">值</span><span class="sxs-lookup"><span data-stu-id="71ad6-130">Values</span></span>](index.md)
- [<span data-ttu-id="71ad6-131">Match 表达式</span><span class="sxs-lookup"><span data-stu-id="71ad6-131">Match Expressions</span></span>](../match-expressions.md)

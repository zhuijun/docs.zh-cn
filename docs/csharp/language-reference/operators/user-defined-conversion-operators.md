---
title: 用户定义转换运算符 - C# 引用
description: 了解如何在 C# 中定义自定义隐式和显式类型转换。
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
- explicit
- implicit
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: ab977408ed891bd7c996ce3644b22ea984425664
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90536374"
---
# <a name="user-defined-conversion-operators-c-reference"></a><span data-ttu-id="7ff75-103">用户定义转换运算符（C# 引用）</span><span class="sxs-lookup"><span data-stu-id="7ff75-103">User-defined conversion operators (C# reference)</span></span>

<span data-ttu-id="7ff75-104">用户定义类型可以定义从或到另一个类型的自定义隐式或显式转换。</span><span class="sxs-lookup"><span data-stu-id="7ff75-104">A user-defined type can define a custom implicit or explicit conversion from or to another type.</span></span>

<span data-ttu-id="7ff75-105">隐式转换无需调用特殊语法，并且可以在各种情况（例如，在赋值和方法调用中）下发生。</span><span class="sxs-lookup"><span data-stu-id="7ff75-105">Implicit conversions don't require special syntax to be invoked and can occur in a variety of situations, for example, in assignments and methods invocations.</span></span> <span data-ttu-id="7ff75-106">预定义的 C# 隐式转换始终成功，且永远不会引发异常。</span><span class="sxs-lookup"><span data-stu-id="7ff75-106">Predefined C# implicit conversions always succeed and never throw an exception.</span></span> <span data-ttu-id="7ff75-107">用户定义隐式转换也应如此。</span><span class="sxs-lookup"><span data-stu-id="7ff75-107">User-defined implicit conversions should behave in that way as well.</span></span> <span data-ttu-id="7ff75-108">如果自定义转换可能会引发异常或丢失信息，请将其定义为显式转换。</span><span class="sxs-lookup"><span data-stu-id="7ff75-108">If a custom conversion can throw an exception or lose information, define it as an explicit conversion.</span></span>

<span data-ttu-id="7ff75-109">[is](type-testing-and-cast.md#is-operator) 和 [as](type-testing-and-cast.md#as-operator) 运算符不考虑使用用户定义转换。</span><span class="sxs-lookup"><span data-stu-id="7ff75-109">User-defined conversions are not considered by the [is](type-testing-and-cast.md#is-operator) and [as](type-testing-and-cast.md#as-operator) operators.</span></span> <span data-ttu-id="7ff75-110">[强制转换表达式](type-testing-and-cast.md#cast-expression)用于调用用户定义显式转换。</span><span class="sxs-lookup"><span data-stu-id="7ff75-110">Use a [cast expression](type-testing-and-cast.md#cast-expression) to invoke a user-defined explicit conversion.</span></span>

<span data-ttu-id="7ff75-111">`operator` 和 `implicit` 或 `explicit` 关键字分别用于定义隐式转换或显式转换。</span><span class="sxs-lookup"><span data-stu-id="7ff75-111">Use the `operator` and `implicit` or `explicit` keywords to define an implicit or explicit conversion, respectively.</span></span> <span data-ttu-id="7ff75-112">定义转换的类型必须是该转换的源类型或目标类型。</span><span class="sxs-lookup"><span data-stu-id="7ff75-112">The type that defines a conversion must be either a source type or a target type of that conversion.</span></span> <span data-ttu-id="7ff75-113">可用两种类型中的任何一种类型来定义两种用户定义类型之间的转换。</span><span class="sxs-lookup"><span data-stu-id="7ff75-113">A conversion between two user-defined types can be defined in either of the two types.</span></span>

<span data-ttu-id="7ff75-114">下面的示例展示如何定义隐式转换和显式转换：</span><span class="sxs-lookup"><span data-stu-id="7ff75-114">The following example demonstrates how to define an implicit and explicit conversion:</span></span>

[!code-csharp[implicit an explicit conversions](snippets/shared/UserDefinedConversions.cs)]

<span data-ttu-id="7ff75-115">`operator` 关键字也可用于重载预定义的 C# 运算符。</span><span class="sxs-lookup"><span data-stu-id="7ff75-115">You also use the `operator` keyword to overload a predefined C# operator.</span></span> <span data-ttu-id="7ff75-116">有关详细信息，请参阅[运算符重载](operator-overloading.md)。</span><span class="sxs-lookup"><span data-stu-id="7ff75-116">For more information, see [Operator overloading](operator-overloading.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7ff75-117">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="7ff75-117">C# language specification</span></span>

<span data-ttu-id="7ff75-118">有关更多信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)的以下部分：</span><span class="sxs-lookup"><span data-stu-id="7ff75-118">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="7ff75-119">转换运算符</span><span class="sxs-lookup"><span data-stu-id="7ff75-119">Conversion operators</span></span>](~/_csharplang/spec/classes.md#conversion-operators)
- [<span data-ttu-id="7ff75-120">用户定义的转换</span><span class="sxs-lookup"><span data-stu-id="7ff75-120">User-defined conversions</span></span>](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [<span data-ttu-id="7ff75-121">隐式转换</span><span class="sxs-lookup"><span data-stu-id="7ff75-121">Implicit conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-conversions)
- [<span data-ttu-id="7ff75-122">显式转换</span><span class="sxs-lookup"><span data-stu-id="7ff75-122">Explicit conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a><span data-ttu-id="7ff75-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="7ff75-123">See also</span></span>

- [<span data-ttu-id="7ff75-124">C# 参考</span><span class="sxs-lookup"><span data-stu-id="7ff75-124">C# reference</span></span>](../index.md)
- [<span data-ttu-id="7ff75-125">C# 运算符和表达式</span><span class="sxs-lookup"><span data-stu-id="7ff75-125">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="7ff75-126">运算符重载</span><span class="sxs-lookup"><span data-stu-id="7ff75-126">Operator overloading</span></span>](operator-overloading.md)
- [<span data-ttu-id="7ff75-127">类型测试和强制转换运算符</span><span class="sxs-lookup"><span data-stu-id="7ff75-127">Type-testing and cast operators</span></span>](type-testing-and-cast.md)
- [<span data-ttu-id="7ff75-128">强制转换和类型转换</span><span class="sxs-lookup"><span data-stu-id="7ff75-128">Casting and type conversion</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="7ff75-129">设计准则 - 转换运算符</span><span class="sxs-lookup"><span data-stu-id="7ff75-129">Design guidelines - Conversion operators</span></span>](../../../standard/design-guidelines/operator-overloads.md#conversion-operators)
- <span data-ttu-id="7ff75-130">[Chained user-defined explicit conversions in C#](/archive/blogs/ericlippert/chained-user-defined-explicit-conversions-in-c)（C# 中链接在一起的用户定义的显式转换）</span><span class="sxs-lookup"><span data-stu-id="7ff75-130">[Chained user-defined explicit conversions in C#](/archive/blogs/ericlippert/chained-user-defined-explicit-conversions-in-c)</span></span>

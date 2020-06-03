---
title: 比较运算符 - C# 参考
description: 了解可用于检查数值顺序的 C# 比较运算符。
ms.date: 05/11/2020
author: pkulikov
f1_keywords:
- <_CSharpKeyword
- '>_CSharpKeyword'
- <=_CSharpKeyword
- '>=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- less than operator [C#]
- < operator [C#]
- greater than operator [C#]
- '> operator [C#]'
- less than or equal to operator [C#]
- <= operator [C#]
- greater than or equal to operator [C#]
- '>= operator [C#]'
ms.openlocfilehash: eda039d950e4be13d9c041c8bb95b6ea773b83f6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207229"
---
# <a name="comparison-operators-c-reference"></a><span data-ttu-id="960a9-103">比较运算符（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="960a9-103">Comparison operators (C# reference)</span></span>

<span data-ttu-id="960a9-104">[`<`（小于）](#less-than-operator-)、[`>`（大于）](#greater-than-operator-)、[`<=`（小于或等于）](#less-than-or-equal-operator-)和 [`>=`（大于或等于）](#greater-than-or-equal-operator-)比较（也称为关系）运算符比较其操作数。</span><span class="sxs-lookup"><span data-stu-id="960a9-104">The [`<` (less than)](#less-than-operator-), [`>` (greater than)](#greater-than-operator-), [`<=` (less than or equal)](#less-than-or-equal-operator-), and [`>=` (greater than or equal)](#greater-than-or-equal-operator-) comparison, also known as relational, operators compare their operands.</span></span> <span data-ttu-id="960a9-105">所有[整型](../builtin-types/integral-numeric-types.md)和[浮点](../builtin-types/floating-point-numeric-types.md)数值类型都支持这些运算符。</span><span class="sxs-lookup"><span data-stu-id="960a9-105">Those operators are supported by all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

> [!NOTE]
> <span data-ttu-id="960a9-106">对于 `==`、`<`、`>`、`<=` 和 `>=` 运算符，如果所有操作数都不是数字（<xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType>），则运算结果为 `false`。</span><span class="sxs-lookup"><span data-stu-id="960a9-106">For the `==`, `<`, `>`, `<=`, and `>=` operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="960a9-107">这意味着 `NaN` 值不大于、小于或等于任何其他 `double`（或 `float`）值，包括 `NaN`。</span><span class="sxs-lookup"><span data-stu-id="960a9-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="960a9-108">有关更多信息和示例，请参阅 <xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType> 参考文章。</span><span class="sxs-lookup"><span data-stu-id="960a9-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="960a9-109">[char](../builtin-types/char.md) 类型也支持比较运算符。</span><span class="sxs-lookup"><span data-stu-id="960a9-109">The [char](../builtin-types/char.md) type also supports comparison operators.</span></span> <span data-ttu-id="960a9-110">在使用 `char` 操作数时，将比较对应的字符代码。</span><span class="sxs-lookup"><span data-stu-id="960a9-110">In the case of `char` operands, the corresponding character codes are compared.</span></span>

<span data-ttu-id="960a9-111">枚举类型也支持比较运算符。</span><span class="sxs-lookup"><span data-stu-id="960a9-111">Enumeration types also support comparison operators.</span></span> <span data-ttu-id="960a9-112">对于相同[枚举](../builtin-types/enum.md)类型的操作数，基础整数类型的相应值会进行比较。</span><span class="sxs-lookup"><span data-stu-id="960a9-112">For operands of the same [enum](../builtin-types/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

<span data-ttu-id="960a9-113">[`==` 和 `!=` 运算符](equality-operators.md)检查其操作数是否相等。</span><span class="sxs-lookup"><span data-stu-id="960a9-113">The [`==` and `!=` operators](equality-operators.md) check if their operands are equal or not.</span></span>

## <a name="less-than-operator-"></a><span data-ttu-id="960a9-114">小于运算符 \<</span><span class="sxs-lookup"><span data-stu-id="960a9-114">Less than operator \<</span></span>

<span data-ttu-id="960a9-115">如果左侧操作数小于右侧操作数，`<` 运算符返回 `true`，否则返回 `false`：</span><span class="sxs-lookup"><span data-stu-id="960a9-115">The `<` operator returns `true` if its left-hand operand is less than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than example](snippets/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a><span data-ttu-id="960a9-116">大于运算符 ></span><span class="sxs-lookup"><span data-stu-id="960a9-116">Greater than operator ></span></span>

<span data-ttu-id="960a9-117">如果左侧操作数大于右侧操作数，`>` 运算符返回 `true`，否则返回 `false`：</span><span class="sxs-lookup"><span data-stu-id="960a9-117">The `>` operator returns `true` if its left-hand operand is greater than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than example](snippets/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a><span data-ttu-id="960a9-118">小于或等于运算符 \<=</span><span class="sxs-lookup"><span data-stu-id="960a9-118">Less than or equal operator \<=</span></span>

<span data-ttu-id="960a9-119">如果左侧操作数小于或等于右侧操作数，`<=` 运算符返回 `true`，否则返回 `false`：</span><span class="sxs-lookup"><span data-stu-id="960a9-119">The `<=` operator returns `true` if its left-hand operand is less than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than or equal example](snippets/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a><span data-ttu-id="960a9-120">大于或等于运算符 >=</span><span class="sxs-lookup"><span data-stu-id="960a9-120">Greater than or equal operator >=</span></span>

<span data-ttu-id="960a9-121">如果左侧操作数大于或等于右侧操作数，`>=` 运算符返回 `true`，否则返回 `false`：</span><span class="sxs-lookup"><span data-stu-id="960a9-121">The `>=` operator returns `true` if its left-hand operand is greater than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than or equal example](snippets/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a><span data-ttu-id="960a9-122">运算符可重载性</span><span class="sxs-lookup"><span data-stu-id="960a9-122">Operator overloadability</span></span>

<span data-ttu-id="960a9-123">用户定义类型可以[重载](operator-overloading.md)`<`、`>`、`<=` 和 `>=` 运算符。</span><span class="sxs-lookup"><span data-stu-id="960a9-123">A user-defined type can [overload](operator-overloading.md) the `<`, `>`, `<=`, and `>=` operators.</span></span>

<span data-ttu-id="960a9-124">如果某类型重载 `<` 或 `>` 运算符之一，它必须同时重载 `<` 和 `>`。</span><span class="sxs-lookup"><span data-stu-id="960a9-124">If a type overloads one of the `<` or `>` operators, it must overload both `<` and `>`.</span></span> <span data-ttu-id="960a9-125">如果某类型重载 `<=` 或 `>=` 运算符之一，它必须同时重载 `<=` 和 `>=`。</span><span class="sxs-lookup"><span data-stu-id="960a9-125">If a type overloads one of the `<=` or `>=` operators, it must overload both `<=` and `>=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="960a9-126">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="960a9-126">C# language specification</span></span>

<span data-ttu-id="960a9-127">有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)中的[关系和类型测试运算符](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators)部分。</span><span class="sxs-lookup"><span data-stu-id="960a9-127">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="960a9-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="960a9-128">See also</span></span>

- [<span data-ttu-id="960a9-129">C# 参考</span><span class="sxs-lookup"><span data-stu-id="960a9-129">C# reference</span></span>](../index.md)
- [<span data-ttu-id="960a9-130">C# 运算符</span><span class="sxs-lookup"><span data-stu-id="960a9-130">C# operators</span></span>](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [<span data-ttu-id="960a9-131">相等运算符</span><span class="sxs-lookup"><span data-stu-id="960a9-131">Equality operators</span></span>](equality-operators.md)

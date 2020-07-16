---
title: 相等运算符 - C# 参考
description: 了解 C# 相等比较运算符和 C# 类型相等。
ms.date: 06/26/2019
author: pkulikov
f1_keywords:
- ==_CSharpKeyword
- '!=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- equality operator [C#]
- equals operator [C#]
- == operator [C#]
- inequality operator [C#]
- not equals operator [C#]
- '!= operator [C#]'
ms.openlocfilehash: 011ef8b570a0bbbc38ec71df4286c3b08c3109da
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174778"
---
# <a name="equality-operators-c-reference"></a><span data-ttu-id="4347a-103">相等运算符（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="4347a-103">Equality operators (C# reference)</span></span>

<span data-ttu-id="4347a-104">[`==`（相等）](#equality-operator-) 和 [`!=`（不等）](#inequality-operator-) 运算符检查其操作数是否相等。</span><span class="sxs-lookup"><span data-stu-id="4347a-104">The [`==` (equality)](#equality-operator-) and [`!=` (inequality)](#inequality-operator-) operators check if their operands are equal or not.</span></span>

## <a name="equality-operator-"></a><span data-ttu-id="4347a-105">相等运算符 ==</span><span class="sxs-lookup"><span data-stu-id="4347a-105">Equality operator ==</span></span>

<span data-ttu-id="4347a-106">如果操作数相等，等于运算符 `==` 返回 `true`，否则返回 `false`。</span><span class="sxs-lookup"><span data-stu-id="4347a-106">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

### <a name="value-types-equality"></a><span data-ttu-id="4347a-107">值类型的相等性</span><span class="sxs-lookup"><span data-stu-id="4347a-107">Value types equality</span></span>

<span data-ttu-id="4347a-108">如果[内置值类型](../builtin-types/value-types.md#built-in-value-types)的值相等，则其操作数相等：</span><span class="sxs-lookup"><span data-stu-id="4347a-108">Operands of the [built-in value types](../builtin-types/value-types.md#built-in-value-types) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](snippets/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="4347a-109">对于 `==`、[`<`、`>`、`<=` 和 `>=`](comparison-operators.md) 运算符，如果任何操作数不是数字（<xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType>），则运算的结果为 `false`。</span><span class="sxs-lookup"><span data-stu-id="4347a-109">For the `==`, [`<`, `>`, `<=`, and `>=`](comparison-operators.md) operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="4347a-110">这意味着 `NaN` 值不大于、小于或等于任何其他 `double`（或 `float`）值，包括 `NaN`。</span><span class="sxs-lookup"><span data-stu-id="4347a-110">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="4347a-111">有关更多信息和示例，请参阅 <xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType> 参考文章。</span><span class="sxs-lookup"><span data-stu-id="4347a-111">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="4347a-112">如果基本整数类型的相应值相等，则相同[枚举](../builtin-types/enum.md)类型的两个操作数相等。</span><span class="sxs-lookup"><span data-stu-id="4347a-112">Two operands of the same [enum](../builtin-types/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="4347a-113">用户定义的 [struct](../builtin-types/struct.md) 类型默认情况下不支持 `==` 运算符。</span><span class="sxs-lookup"><span data-stu-id="4347a-113">User-defined [struct](../builtin-types/struct.md) types don't support the `==` operator by default.</span></span> <span data-ttu-id="4347a-114">要支持 `==` 运算符，用户定义的结构必须[重载](operator-overloading.md)它。</span><span class="sxs-lookup"><span data-stu-id="4347a-114">To support the `==` operator, a user-defined struct must [overload](operator-overloading.md) it.</span></span>

<span data-ttu-id="4347a-115">从 C# 7.3 开始，`==` 和 `!=` 运算符由 C# [元组](../builtin-types/value-tuples.md)支持。</span><span class="sxs-lookup"><span data-stu-id="4347a-115">Beginning with C# 7.3, the `==` and `!=` operators are supported by C# [tuples](../builtin-types/value-tuples.md).</span></span> <span data-ttu-id="4347a-116">有关详细信息，请参阅[元组类型](../builtin-types/value-tuples.md)一文的[元组相等](../builtin-types/value-tuples.md#tuple-equality)部分。</span><span class="sxs-lookup"><span data-stu-id="4347a-116">For more information, see the [Tuple equality](../builtin-types/value-tuples.md#tuple-equality) section of the [Tuple types](../builtin-types/value-tuples.md) article.</span></span>

### <a name="reference-types-equality"></a><span data-ttu-id="4347a-117">引用类型的相等性</span><span class="sxs-lookup"><span data-stu-id="4347a-117">Reference types equality</span></span>

<span data-ttu-id="4347a-118">默认情况下，如果两个引用类型操作符引用同一对象，则这两个操作符相等：</span><span class="sxs-lookup"><span data-stu-id="4347a-118">By default, two reference-type operands are equal if they refer to the same object:</span></span>

[!code-csharp[reference type equality](snippets/EqualityOperators.cs#ReferenceTypesEquality)]

<span data-ttu-id="4347a-119">如示例所示，默认情况下，用户定义的引用类型支持 `==` 运算符。</span><span class="sxs-lookup"><span data-stu-id="4347a-119">As the example shows, user-defined reference types support the `==` operator by default.</span></span> <span data-ttu-id="4347a-120">但是，引用类型可重载 `==` 运算符。</span><span class="sxs-lookup"><span data-stu-id="4347a-120">However, a reference type can overload the `==` operator.</span></span> <span data-ttu-id="4347a-121">如果引用类型重载 `==` 运算符，使用 <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> 方法来检查该类型的两个引用是否引用同一对象。</span><span class="sxs-lookup"><span data-stu-id="4347a-121">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

### <a name="string-equality"></a><span data-ttu-id="4347a-122">字符串相等性</span><span class="sxs-lookup"><span data-stu-id="4347a-122">String equality</span></span>

<span data-ttu-id="4347a-123">如果两个字符串均为 `null` 或者两个字符串实例具有相等长度且在每个字符位置有相同字符，则这两个[字符串](../builtin-types/reference-types.md#the-string-type)操作数相等：</span><span class="sxs-lookup"><span data-stu-id="4347a-123">Two [string](../builtin-types/reference-types.md#the-string-type) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](snippets/EqualityOperators.cs#StringEquality)]

<span data-ttu-id="4347a-124">这就是区分大小写的序号比较。</span><span class="sxs-lookup"><span data-stu-id="4347a-124">That is a case-sensitive ordinal comparison.</span></span> <span data-ttu-id="4347a-125">有关字符串比较的详细信息，请参阅[如何在 C# 中比较字符串](../../how-to/compare-strings.md)。</span><span class="sxs-lookup"><span data-stu-id="4347a-125">For more information about string comparison, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

### <a name="delegate-equality"></a><span data-ttu-id="4347a-126">委托相等</span><span class="sxs-lookup"><span data-stu-id="4347a-126">Delegate equality</span></span>

<span data-ttu-id="4347a-127">当两个[委托](../../programming-guide/delegates/index.md)操作数都是 `null` 或它们的调用列表长度相同并且在每个位置具有相同的条目时，运行时类型相同的两个委托操作数是相等的：</span><span class="sxs-lookup"><span data-stu-id="4347a-127">Two [delegate](../../programming-guide/delegates/index.md) operands of the same runtime type are equal when both of them are `null` or their invocation lists are of the same length and have equal entries in each position:</span></span>

[!code-csharp-interactive[delegate equality](snippets/EqualityOperators.cs#DelegateEquality)]

<span data-ttu-id="4347a-128">有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)中的[委托相等运算符](~/_csharplang/spec/expressions.md#delegate-equality-operators)部分。</span><span class="sxs-lookup"><span data-stu-id="4347a-128">For more information, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="4347a-129">通过计算语义上相同的 [Lambda 表达式](../../programming-guide/statements-expressions-operators/lambda-expressions.md)生成的委托不相等，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="4347a-129">Delegates that are produced from evaluation of semantically identical [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) are not equal, as the following example shows:</span></span>

[!code-csharp-interactive[from identical lambdas](snippets/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a><span data-ttu-id="4347a-130">不等运算符 !=</span><span class="sxs-lookup"><span data-stu-id="4347a-130">Inequality operator !=</span></span>

<span data-ttu-id="4347a-131">如果操作数不相等，不等于运算符 `!=` 返回 `true`，否则返回 `false`。</span><span class="sxs-lookup"><span data-stu-id="4347a-131">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="4347a-132">对于[内置类型](../builtin-types/built-in-types.md)的操作数，表达式 `x != y` 生成与表达式 `!(x == y)` 相同的结果。</span><span class="sxs-lookup"><span data-stu-id="4347a-132">For the operands of the [built-in types](../builtin-types/built-in-types.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="4347a-133">有关类型相等性的更多信息，请参阅[相等运算符](#equality-operator-)部分。</span><span class="sxs-lookup"><span data-stu-id="4347a-133">For more information about type equality, see the [Equality operator](#equality-operator-) section.</span></span>

<span data-ttu-id="4347a-134">下面的示例演示 `!=` 运算符的用法：</span><span class="sxs-lookup"><span data-stu-id="4347a-134">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](snippets/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="4347a-135">运算符可重载性</span><span class="sxs-lookup"><span data-stu-id="4347a-135">Operator overloadability</span></span>

<span data-ttu-id="4347a-136">用户定义类型可以[重载](operator-overloading.md)`==` 和 `!=` 运算符。</span><span class="sxs-lookup"><span data-stu-id="4347a-136">A user-defined type can [overload](operator-overloading.md) the `==` and `!=` operators.</span></span> <span data-ttu-id="4347a-137">如果某类型重载这两个运算符之一，它还必须重载另一个运算符。</span><span class="sxs-lookup"><span data-stu-id="4347a-137">If a type overloads one of the two operators, it must also overload the other one.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4347a-138">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="4347a-138">C# language specification</span></span>

<span data-ttu-id="4347a-139">有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)中的[关系和类型测试运算符](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators)部分。</span><span class="sxs-lookup"><span data-stu-id="4347a-139">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4347a-140">请参阅</span><span class="sxs-lookup"><span data-stu-id="4347a-140">See also</span></span>

- [<span data-ttu-id="4347a-141">C# 参考</span><span class="sxs-lookup"><span data-stu-id="4347a-141">C# reference</span></span>](../index.md)
- [<span data-ttu-id="4347a-142">C# 运算符</span><span class="sxs-lookup"><span data-stu-id="4347a-142">C# operators</span></span>](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="4347a-143">相等性比较</span><span class="sxs-lookup"><span data-stu-id="4347a-143">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [<span data-ttu-id="4347a-144">比较运算符</span><span class="sxs-lookup"><span data-stu-id="4347a-144">Comparison operators</span></span>](comparison-operators.md)

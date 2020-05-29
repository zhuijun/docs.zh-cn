---
title: 算术运算符 - C# 参考
description: 了解对数值类型执行乘法、除法、余数、加法和减法运算的 C# 运算符。
ms.date: 05/11/2020
author: pkulikov
f1_keywords:
- ++_CSharpKeyword
- --_CSharpKeyword
- '*_CSharpKeyword'
- /_CSharpKeyword
- '%_CSharpKeyword'
- +_CSharpKeyword
- -_CSharpKeyword
helpviewer_keywords:
- arithmetic operators [C#]
- increment operator [C#]
- ++ operator [C#]
- decrement operator [C#]
- -- operator [C#]
- multiplication operator [C#]
- '* operator [C#]'
- division operator [C#]
- / operator [C#]
- remainder operator [C#]
- '% operator [C#]'
- addition operator [C#]
- + operator [C#]
- subtraction operator [C#]
- '- operator [C#]'
ms.openlocfilehash: d004ab466bc053ed286d85bcbee2766d8a087286
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207243"
---
# <a name="arithmetic-operators-c-reference"></a><span data-ttu-id="7ca05-103">算术运算符（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="7ca05-103">Arithmetic operators (C# reference)</span></span>

<span data-ttu-id="7ca05-104">以下运算符对数值类型的操作数执行算术运算：</span><span class="sxs-lookup"><span data-stu-id="7ca05-104">The following operators perform arithmetic operations with operands of numeric types:</span></span>

- <span data-ttu-id="7ca05-105">一元 [`++`（增量）](#increment-operator-)、[`--`（减量）](#decrement-operator---)、[`+`（加）](#unary-plus-and-minus-operators)和 [`-`（减）](#unary-plus-and-minus-operators)运算符</span><span class="sxs-lookup"><span data-stu-id="7ca05-105">Unary [`++` (increment)](#increment-operator-), [`--` (decrement)](#decrement-operator---), [`+` (plus)](#unary-plus-and-minus-operators), and [`-` (minus)](#unary-plus-and-minus-operators) operators</span></span>
- <span data-ttu-id="7ca05-106">二元 [`*`（乘法）](#multiplication-operator-)、[`/`（除法）](#division-operator-)、[`%`（余数）](#remainder-operator-)、[`+`（加法）](#addition-operator-)和 [`-`（减法）](#subtraction-operator--)运算符</span><span class="sxs-lookup"><span data-stu-id="7ca05-106">Binary [`*` (multiplication)](#multiplication-operator-), [`/` (division)](#division-operator-), [`%` (remainder)](#remainder-operator-), [`+` (addition)](#addition-operator-), and [`-` (subtraction)](#subtraction-operator--) operators</span></span>

<span data-ttu-id="7ca05-107">所有[整型](../builtin-types/integral-numeric-types.md)和[浮点](../builtin-types/floating-point-numeric-types.md)数值类型都支持这些运算符。</span><span class="sxs-lookup"><span data-stu-id="7ca05-107">Those operators are supported by all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

<span data-ttu-id="7ca05-108">对于整型类型，这些运算符（除 `++` 和 `--` 运算符以外）是为 `int`、`uint`、`long` 和 `ulong` 类型定义的。</span><span class="sxs-lookup"><span data-stu-id="7ca05-108">In the case of integral types, those operators (except the `++` and `--` operators) are defined for the `int`, `uint`, `long`, and `ulong` types.</span></span> <span data-ttu-id="7ca05-109">如果操作数都是其他整型类型（`sbyte`、`byte`、`short`、`ushort` 或 `char`），它们的值将转换为 `int` 类型，这也是一个运算的结果类型。</span><span class="sxs-lookup"><span data-stu-id="7ca05-109">When operands are of other integral types (`sbyte`, `byte`, `short`, `ushort`, or `char`), their values are converted to the `int` type, which is also the result type of an operation.</span></span> <span data-ttu-id="7ca05-110">如果操作数是不同的整型类型或浮点类型，它们的值将转换为最接近的包含类型（如果存在该类型）。</span><span class="sxs-lookup"><span data-stu-id="7ca05-110">When operands are of different integral or floating-point types, their values are converted to the closest containing type, if such a type exists.</span></span> <span data-ttu-id="7ca05-111">有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)的[数值提升](~/_csharplang/spec/expressions.md#numeric-promotions)部分。</span><span class="sxs-lookup"><span data-stu-id="7ca05-111">For more information, see the [Numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span> <span data-ttu-id="7ca05-112">`++` 和 `--` 运算符是为所有整型和浮点数值类型以及 [char](../builtin-types/char.md) 类型定义的。</span><span class="sxs-lookup"><span data-stu-id="7ca05-112">The `++` and `--` operators are defined for all integral and floating-point numeric types and the [char](../builtin-types/char.md) type.</span></span>

## <a name="increment-operator-"></a><span data-ttu-id="7ca05-113">增量运算符 ++</span><span class="sxs-lookup"><span data-stu-id="7ca05-113">Increment operator ++</span></span>

<span data-ttu-id="7ca05-114">一元增量运算符 `++` 按 1 递增其操作数。</span><span class="sxs-lookup"><span data-stu-id="7ca05-114">The unary increment operator `++` increments its operand by 1.</span></span> <span data-ttu-id="7ca05-115">操作数必须是变量、[属性](../../programming-guide/classes-and-structs/properties.md)访问或[索引器](../../programming-guide/indexers/index.md)访问。</span><span class="sxs-lookup"><span data-stu-id="7ca05-115">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="7ca05-116">增量运算符以两种形式进行支持：后缀增量运算符 `x++` 和前缀增量运算符 `++x`。</span><span class="sxs-lookup"><span data-stu-id="7ca05-116">The increment operator is supported in two forms: the postfix increment operator, `x++`, and the prefix increment operator, `++x`.</span></span>

### <a name="postfix-increment-operator"></a><span data-ttu-id="7ca05-117">后缀递增运算符</span><span class="sxs-lookup"><span data-stu-id="7ca05-117">Postfix increment operator</span></span>

<span data-ttu-id="7ca05-118">`x++` 的结果是此操作前的 `x` 的值，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="7ca05-118">The result of `x++` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix increment](snippets/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a><span data-ttu-id="7ca05-119">前缀增量运算符</span><span class="sxs-lookup"><span data-stu-id="7ca05-119">Prefix increment operator</span></span>

<span data-ttu-id="7ca05-120">`++x` 的结果是此操作后的 `x` 的值，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="7ca05-120">The result of `++x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix increment](snippets/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a><span data-ttu-id="7ca05-121">减量运算符 --</span><span class="sxs-lookup"><span data-stu-id="7ca05-121">Decrement operator --</span></span>

<span data-ttu-id="7ca05-122">一元减量运算符 `--` 按 1 递减其操作数。</span><span class="sxs-lookup"><span data-stu-id="7ca05-122">The unary decrement operator `--` decrements its operand by 1.</span></span> <span data-ttu-id="7ca05-123">操作数必须是变量、[属性](../../programming-guide/classes-and-structs/properties.md)访问或[索引器](../../programming-guide/indexers/index.md)访问。</span><span class="sxs-lookup"><span data-stu-id="7ca05-123">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="7ca05-124">减量运算符以两种形式进行支持：后缀减量运算符`x--` 和前缀减量运算符 `--x`。</span><span class="sxs-lookup"><span data-stu-id="7ca05-124">The decrement operator is supported in two forms: the postfix decrement operator, `x--`, and the prefix decrement operator, `--x`.</span></span>

### <a name="postfix-decrement-operator"></a><span data-ttu-id="7ca05-125">后缀递减运算符</span><span class="sxs-lookup"><span data-stu-id="7ca05-125">Postfix decrement operator</span></span>

<span data-ttu-id="7ca05-126">`x--` 的结果是此操作前的 `x` 的值，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="7ca05-126">The result of `x--` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix decrement](snippets/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a><span data-ttu-id="7ca05-127">前缀减量运算符</span><span class="sxs-lookup"><span data-stu-id="7ca05-127">Prefix decrement operator</span></span>

<span data-ttu-id="7ca05-128">`--x` 的结果是此操作后的 `x` 的值，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="7ca05-128">The result of `--x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix decrement](snippets/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a><span data-ttu-id="7ca05-129">一元加和减运算符</span><span class="sxs-lookup"><span data-stu-id="7ca05-129">Unary plus and minus operators</span></span>

<span data-ttu-id="7ca05-130">一元 `+` 运算符返回其操作数的值。</span><span class="sxs-lookup"><span data-stu-id="7ca05-130">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="7ca05-131">一元 `-` 运算符对其操作数的数值取负。</span><span class="sxs-lookup"><span data-stu-id="7ca05-131">The unary `-` operator computes the numeric negation of its operand.</span></span>

[!code-csharp-interactive[unary plus and minus](snippets/ArithmeticOperators.cs#UnaryPlusAndMinus)]

<span data-ttu-id="7ca05-132">[ulong](../builtin-types/integral-numeric-types.md) 类型不支持一元 `-` 运算符。</span><span class="sxs-lookup"><span data-stu-id="7ca05-132">The [ulong](../builtin-types/integral-numeric-types.md) type doesn't support the unary `-` operator.</span></span>

## <a name="multiplication-operator-"></a><span data-ttu-id="7ca05-133">乘法运算符 \*</span><span class="sxs-lookup"><span data-stu-id="7ca05-133">Multiplication operator \*</span></span>

<span data-ttu-id="7ca05-134">乘法运算符 `*` 计算其操作数的乘积：</span><span class="sxs-lookup"><span data-stu-id="7ca05-134">The multiplication operator `*` computes the product of its operands:</span></span>

[!code-csharp-interactive[multiplication operator](snippets/ArithmeticOperators.cs#Multiplication)]

<span data-ttu-id="7ca05-135">一元 `*` 运算符是[指针间接运算符](pointer-related-operators.md#pointer-indirection-operator-)。</span><span class="sxs-lookup"><span data-stu-id="7ca05-135">The unary `*` operator is the [pointer indirection operator](pointer-related-operators.md#pointer-indirection-operator-).</span></span>

## <a name="division-operator-"></a><span data-ttu-id="7ca05-136">除法运算符 /</span><span class="sxs-lookup"><span data-stu-id="7ca05-136">Division operator /</span></span>

<span data-ttu-id="7ca05-137">除法运算符 `/` 用它的左侧操作数除以右侧操作数。</span><span class="sxs-lookup"><span data-stu-id="7ca05-137">The division operator `/` divides its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-division"></a><span data-ttu-id="7ca05-138">整数除法</span><span class="sxs-lookup"><span data-stu-id="7ca05-138">Integer division</span></span>

<span data-ttu-id="7ca05-139">对于整数类型的操作数，`/` 运算符的结果为整数类型，并且等于两个操作数之商向零舍入后的结果：</span><span class="sxs-lookup"><span data-stu-id="7ca05-139">For the operands of integer types, the result of the `/` operator is of an integer type and equals the quotient of the two operands rounded towards zero:</span></span>

[!code-csharp-interactive[integer division](snippets/ArithmeticOperators.cs#IntegerDivision)]

<span data-ttu-id="7ca05-140">若要获取浮点数形式的两个操作数之商，请使用 `float`、`double` 或 `decimal` 类型：</span><span class="sxs-lookup"><span data-stu-id="7ca05-140">To obtain the quotient of the two operands as a floating-point number, use the `float`, `double`, or `decimal` type:</span></span>

[!code-csharp-interactive[integer as floating-point division](snippets/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a><span data-ttu-id="7ca05-141">浮点除法</span><span class="sxs-lookup"><span data-stu-id="7ca05-141">Floating-point division</span></span>

<span data-ttu-id="7ca05-142">对于 `float`、`double` 和 `decimal` 类型，`/` 运算符的结果为两个操作数之商：</span><span class="sxs-lookup"><span data-stu-id="7ca05-142">For the `float`, `double`, and `decimal` types, the result of the `/` operator is the quotient of the two operands:</span></span>

[!code-csharp-interactive[floating-point division](snippets/ArithmeticOperators.cs#FloatingPointDivision)]

<span data-ttu-id="7ca05-143">如果操作数之一为 `decimal`，那么另一个操作数不得为 `float` 和 `double`，因为 `float` 和 `double` 都无法隐式转换为 `decimal`。</span><span class="sxs-lookup"><span data-stu-id="7ca05-143">If one of the operands is `decimal`, another operand can be neither `float` nor `double`, because neither `float` nor `double` is implicitly convertible to `decimal`.</span></span> <span data-ttu-id="7ca05-144">必须将 `float` 或 `double` 操作数显式转换为 `decimal` 类型。</span><span class="sxs-lookup"><span data-stu-id="7ca05-144">You must explicitly convert the `float` or `double` operand to the `decimal` type.</span></span> <span data-ttu-id="7ca05-145">如需详细了解数值类型之间的转换，请参阅[内置数值转换](../builtin-types/numeric-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="7ca05-145">For more information about conversions between numeric types, see [Built-in numeric conversions](../builtin-types/numeric-conversions.md).</span></span>

## <a name="remainder-operator-"></a><span data-ttu-id="7ca05-146">余数运算符 %</span><span class="sxs-lookup"><span data-stu-id="7ca05-146">Remainder operator %</span></span>

<span data-ttu-id="7ca05-147">余数运算符 `%` 计算左侧操作数除以右侧操作数后的余数。</span><span class="sxs-lookup"><span data-stu-id="7ca05-147">The remainder operator `%` computes the remainder after dividing its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-remainder"></a><span data-ttu-id="7ca05-148">整数余数</span><span class="sxs-lookup"><span data-stu-id="7ca05-148">Integer remainder</span></span>

<span data-ttu-id="7ca05-149">对于整数类型的操作数，`a % b` 的结果是 `a - (a / b) * b` 得出的值。</span><span class="sxs-lookup"><span data-stu-id="7ca05-149">For the operands of integer types, the result of `a % b` is the value produced by `a - (a / b) * b`.</span></span> <span data-ttu-id="7ca05-150">非零余数的符号与左侧操作数的符号相同，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="7ca05-150">The sign of the non-zero remainder is the same as that of the left-hand operand, as the following example shows:</span></span>

[!code-csharp-interactive[integer remainder](snippets/ArithmeticOperators.cs#IntegerRemainder)]

<span data-ttu-id="7ca05-151">使用 <xref:System.Math.DivRem%2A?displayProperty=nameWithType> 方法计算整数除法和余数结果。</span><span class="sxs-lookup"><span data-stu-id="7ca05-151">Use the <xref:System.Math.DivRem%2A?displayProperty=nameWithType> method to compute both integer division and remainder results.</span></span>

### <a name="floating-point-remainder"></a><span data-ttu-id="7ca05-152">浮点余数</span><span class="sxs-lookup"><span data-stu-id="7ca05-152">Floating-point remainder</span></span>

<span data-ttu-id="7ca05-153">对于 `float` 和 `double` 操作数，有限的 `x` 和 `y` 的 `x % y` 的结果是值 `z`，因此</span><span class="sxs-lookup"><span data-stu-id="7ca05-153">For the `float` and `double` operands, the result of `x % y` for the finite `x` and `y` is the value `z` such that</span></span>

- <span data-ttu-id="7ca05-154">`z`（如果不为零）的符号与 `x` 的符号相同。</span><span class="sxs-lookup"><span data-stu-id="7ca05-154">The sign of `z`, if non-zero, is the same as the sign of `x`.</span></span>
- <span data-ttu-id="7ca05-155">`z` 的绝对值是 `|x| - n * |y|` 得出的值，其中 `n` 是小于或等于 `|x| / |y|` 的最大可能整数，`|x|` 和 `|y|` 分别是 `x` 和 `y` 的绝对值。</span><span class="sxs-lookup"><span data-stu-id="7ca05-155">The absolute value of `z` is the value produced by `|x| - n * |y|` where `n` is the largest possible integer that is less than or equal to `|x| / |y|` and `|x|` and `|y|` are the absolute values of `x` and `y`, respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="7ca05-156">计算余数的此方法类似于用于整数操作数的方法，但与 IEEE 754 规范不同。</span><span class="sxs-lookup"><span data-stu-id="7ca05-156">This method of computing the remainder is analogous to that used for integer operands, but different from the IEEE 754 specification.</span></span> <span data-ttu-id="7ca05-157">如果需要符合 IEEE 754 规范的余数运算，请使用 <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="7ca05-157">If you need the remainder operation that complies with the IEEE 754 specification, use the <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="7ca05-158">有关非限定操作数的 `%` 运算符行为的信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)的[余数运算符](~/_csharplang/spec/expressions.md#remainder-operator)章节。</span><span class="sxs-lookup"><span data-stu-id="7ca05-158">For information about the behavior of the `%` operator with non-finite operands, see the [Remainder operator](~/_csharplang/spec/expressions.md#remainder-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="7ca05-159">对于 `decimal` 操作数，余数运算符 `%` 等效于 <xref:System.Decimal?displayProperty=nameWithType> 类型的[余数运算符](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>)。</span><span class="sxs-lookup"><span data-stu-id="7ca05-159">For the `decimal` operands, the remainder operator `%` is equivalent to the [remainder operator](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) of the <xref:System.Decimal?displayProperty=nameWithType> type.</span></span>

<span data-ttu-id="7ca05-160">以下示例演示了具有浮动操作数的余数运算符的行为：</span><span class="sxs-lookup"><span data-stu-id="7ca05-160">The following example demonstrates the behavior of the remainder operator with floating-point operands:</span></span>

[!code-csharp-interactive[floating-point remainder](snippets/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a><span data-ttu-id="7ca05-161">加法运算符 +</span><span class="sxs-lookup"><span data-stu-id="7ca05-161">Addition operator +</span></span>

<span data-ttu-id="7ca05-162">加法运算符 `+` 计算其操作数的和。</span><span class="sxs-lookup"><span data-stu-id="7ca05-162">The addition operator `+` computes the sum of its operands:</span></span>

[!code-csharp-interactive[addition operator](snippets/ArithmeticOperators.cs#Addition)]

<span data-ttu-id="7ca05-163">还可以将 `+` 运算符用于字符串串联和委托组合。</span><span class="sxs-lookup"><span data-stu-id="7ca05-163">You can also use the `+` operator for string concatenation and delegate combination.</span></span> <span data-ttu-id="7ca05-164">有关详细信息，请参阅 [`+` 和 `+=` 运算符](addition-operator.md)一文。</span><span class="sxs-lookup"><span data-stu-id="7ca05-164">For more information, see the [`+` and `+=` operators](addition-operator.md) article.</span></span>

## <a name="subtraction-operator--"></a><span data-ttu-id="7ca05-165">减法运算符 -</span><span class="sxs-lookup"><span data-stu-id="7ca05-165">Subtraction operator -</span></span>

<span data-ttu-id="7ca05-166">减法运算符 `-` 从其左侧操作数中减去其右侧操作数：</span><span class="sxs-lookup"><span data-stu-id="7ca05-166">The subtraction operator `-` subtracts its right-hand operand from its left-hand operand:</span></span>

[!code-csharp-interactive[subtraction operator](snippets/ArithmeticOperators.cs#Subtraction)]

<span data-ttu-id="7ca05-167">还可以使用 `-` 运算符删除委托。</span><span class="sxs-lookup"><span data-stu-id="7ca05-167">You can also use the `-` operator for delegate removal.</span></span> <span data-ttu-id="7ca05-168">有关详细信息，请参阅 [`-` 和 `-=` 运算符](subtraction-operator.md)一文。</span><span class="sxs-lookup"><span data-stu-id="7ca05-168">For more information, see the [`-` and `-=` operators](subtraction-operator.md) article.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="7ca05-169">复合赋值</span><span class="sxs-lookup"><span data-stu-id="7ca05-169">Compound assignment</span></span>

<span data-ttu-id="7ca05-170">对于二元运算符 `op`，窗体的复合赋值表达式</span><span class="sxs-lookup"><span data-stu-id="7ca05-170">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="7ca05-171">等效于</span><span class="sxs-lookup"><span data-stu-id="7ca05-171">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="7ca05-172">不同的是 `x` 只计算一次。</span><span class="sxs-lookup"><span data-stu-id="7ca05-172">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="7ca05-173">以下示例使用算术运算符演示了复合赋值的用法：</span><span class="sxs-lookup"><span data-stu-id="7ca05-173">The following example demonstrates the usage of compound assignment with arithmetic operators:</span></span>

[!code-csharp-interactive[compound assignment](snippets/ArithmeticOperators.cs#CompoundAssignment)]

<span data-ttu-id="7ca05-174">由于[数值提升](~/_csharplang/spec/expressions.md#numeric-promotions)，`op` 运算的结果可能不会隐式转换为 `x` 的 `T` 类型。</span><span class="sxs-lookup"><span data-stu-id="7ca05-174">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="7ca05-175">在这种情况下，如果 `op` 是预定义的运算符并且运算的结果可以显式转换为 `x` 的类型 `T`，则形式为 `x op= y` 的复合赋值表达式等效于 `x = (T)(x op y)`，但 `x` 仅计算一次。</span><span class="sxs-lookup"><span data-stu-id="7ca05-175">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="7ca05-176">以下示例演示了该行为：</span><span class="sxs-lookup"><span data-stu-id="7ca05-176">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](snippets/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

<span data-ttu-id="7ca05-177">你还可以使用 `+=` 和 `-=` 运算符分别订阅和取消订阅[事件](../keywords/event.md)。</span><span class="sxs-lookup"><span data-stu-id="7ca05-177">You also use the `+=` and `-=` operators to subscribe to and unsubscribe from an [event](../keywords/event.md), respectively.</span></span> <span data-ttu-id="7ca05-178">有关详细信息，请参阅[如何订阅和取消订阅事件](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)。</span><span class="sxs-lookup"><span data-stu-id="7ca05-178">For more information, see [How to subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-precedence-and-associativity"></a><span data-ttu-id="7ca05-179">运算符优先级和关联性</span><span class="sxs-lookup"><span data-stu-id="7ca05-179">Operator precedence and associativity</span></span>

<span data-ttu-id="7ca05-180">以下列表对优先级由高到低的顺序对算术运算符进行排序：</span><span class="sxs-lookup"><span data-stu-id="7ca05-180">The following list orders arithmetic operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="7ca05-181">后缀增量 `x++` 和减量 `x--` 运算符</span><span class="sxs-lookup"><span data-stu-id="7ca05-181">Postfix increment `x++` and decrement `x--` operators</span></span>
- <span data-ttu-id="7ca05-182">前缀增量 `++x` 和减量 `--x` 以及一元 `+` 和 `-` 运算符</span><span class="sxs-lookup"><span data-stu-id="7ca05-182">Prefix increment `++x` and decrement `--x` and unary `+` and `-` operators</span></span>
- <span data-ttu-id="7ca05-183">乘法 `*`、`/` 和 `%` 运算符</span><span class="sxs-lookup"><span data-stu-id="7ca05-183">Multiplicative `*`, `/`, and `%` operators</span></span>
- <span data-ttu-id="7ca05-184">加法 `+` 和 `-` 运算符</span><span class="sxs-lookup"><span data-stu-id="7ca05-184">Additive `+` and `-` operators</span></span>

<span data-ttu-id="7ca05-185">二元算数运算符是左结合运算符。</span><span class="sxs-lookup"><span data-stu-id="7ca05-185">Binary arithmetic operators are left-associative.</span></span> <span data-ttu-id="7ca05-186">也就是说，具有相同优先级的运算符按从左至右的顺序计算。</span><span class="sxs-lookup"><span data-stu-id="7ca05-186">That is, operators with the same precedence level are evaluated from left to right.</span></span>

<span data-ttu-id="7ca05-187">使用括号 `()` 更改由运算符优先级和关联性决定的计算顺序。</span><span class="sxs-lookup"><span data-stu-id="7ca05-187">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence and associativity.</span></span>

[!code-csharp-interactive[precedence and associativity](snippets/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

<span data-ttu-id="7ca05-188">如需了解按优先级排序的完整 C# 运算符列表，请参阅 [C# 运算符](index.md#operator-precedence)一文中的[运算符优先级](index.md)部分。</span><span class="sxs-lookup"><span data-stu-id="7ca05-188">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="arithmetic-overflow-and-division-by-zero"></a><span data-ttu-id="7ca05-189">算术溢出和被零除</span><span class="sxs-lookup"><span data-stu-id="7ca05-189">Arithmetic overflow and division by zero</span></span>

<span data-ttu-id="7ca05-190">当算术运算的结果超出所涉及数值类型的可能有限值范围时，算术运算符的行为取决于其操作数的类型。</span><span class="sxs-lookup"><span data-stu-id="7ca05-190">When the result of an arithmetic operation is outside the range of possible finite values of the involved numeric type, the behavior of an arithmetic operator depends on the type of its operands.</span></span>

### <a name="integer-arithmetic-overflow"></a><span data-ttu-id="7ca05-191">整数算术溢出</span><span class="sxs-lookup"><span data-stu-id="7ca05-191">Integer arithmetic overflow</span></span>

<span data-ttu-id="7ca05-192">整数被零除总是引发 <xref:System.DivideByZeroException>。</span><span class="sxs-lookup"><span data-stu-id="7ca05-192">Integer division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

<span data-ttu-id="7ca05-193">在整数算术溢出的情况下，溢出检查上下文（可能[已检查或未检查](../keywords/checked-and-unchecked.md)）将控制引发的行为：</span><span class="sxs-lookup"><span data-stu-id="7ca05-193">In case of integer arithmetic overflow, an overflow checking context, which can be [checked or unchecked](../keywords/checked-and-unchecked.md), controls the resulting behavior:</span></span>

- <span data-ttu-id="7ca05-194">在已检查的上下文中，如果在常数表达式中发生溢出，则会发生编译时错误。</span><span class="sxs-lookup"><span data-stu-id="7ca05-194">In a checked context, if overflow happens in a constant expression, a compile-time error occurs.</span></span> <span data-ttu-id="7ca05-195">否则，当在运行时执行此运算时，则引发 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="7ca05-195">Otherwise, when the operation is performed at run time, an <xref:System.OverflowException> is thrown.</span></span>
- <span data-ttu-id="7ca05-196">在未检查的上下文中，会通过丢弃任何不适应目标类型的高序位来将结果截断。</span><span class="sxs-lookup"><span data-stu-id="7ca05-196">In an unchecked context, the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>

<span data-ttu-id="7ca05-197">在使用[已检查和未检查的](../keywords/checked-and-unchecked.md)语句时，可以使用 `checked` 和 `unchecked` 运算符来控制溢出检查上下文，在该上下文中将计算一个表达式：</span><span class="sxs-lookup"><span data-stu-id="7ca05-197">Along with the [checked and unchecked](../keywords/checked-and-unchecked.md) statements, you can use the `checked` and `unchecked` operators to control the overflow checking context, in which an expression is evaluated:</span></span>

[!code-csharp-interactive[checked and unchecked](snippets/ArithmeticOperators.cs#CheckedUnchecked)]

<span data-ttu-id="7ca05-198">默认情况下，算术运算发生在 *unchecked* 上下文中。</span><span class="sxs-lookup"><span data-stu-id="7ca05-198">By default, arithmetic operations occur in an *unchecked* context.</span></span>

### <a name="floating-point-arithmetic-overflow"></a><span data-ttu-id="7ca05-199">浮点运算溢出</span><span class="sxs-lookup"><span data-stu-id="7ca05-199">Floating-point arithmetic overflow</span></span>

<span data-ttu-id="7ca05-200">使用 `float` 和 `double` 类型的算术运算永远不会引发异常。</span><span class="sxs-lookup"><span data-stu-id="7ca05-200">Arithmetic operations with the `float` and `double` types never throw an exception.</span></span> <span data-ttu-id="7ca05-201">使用这些类型的算术运算的结果可能是表示无穷大和非数字的特殊值之一：</span><span class="sxs-lookup"><span data-stu-id="7ca05-201">The result of arithmetic operations with those types can be one of special values that represent infinity and not-a-number:</span></span>

[!code-csharp-interactive[double non-finite values](snippets/ArithmeticOperators.cs#FloatingPointOverflow)]

<span data-ttu-id="7ca05-202">对于 `decimal` 类型的操作数，算术溢出始终会引发 <xref:System.OverflowException>，并且被零除始终会引发 <xref:System.DivideByZeroException>。</span><span class="sxs-lookup"><span data-stu-id="7ca05-202">For the operands of the `decimal` type, arithmetic overflow always throws an <xref:System.OverflowException> and division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

## <a name="round-off-errors"></a><span data-ttu-id="7ca05-203">舍入误差</span><span class="sxs-lookup"><span data-stu-id="7ca05-203">Round-off errors</span></span>

<span data-ttu-id="7ca05-204">由于实数和浮点运算的浮点表达形式的常规限制，在使用浮点类型的计算中可能会发生舍入误差。</span><span class="sxs-lookup"><span data-stu-id="7ca05-204">Because of general limitations of the floating-point representation of real numbers and floating-point arithmetic, round-off errors might occur in calculations with floating-point types.</span></span> <span data-ttu-id="7ca05-205">也就是说，表达式得出的结果可能与预期的数学运算结果不同。</span><span class="sxs-lookup"><span data-stu-id="7ca05-205">That is, the produced result of an expression might differ from the expected mathematical result.</span></span> <span data-ttu-id="7ca05-206">以下示例演示了几种此类情况：</span><span class="sxs-lookup"><span data-stu-id="7ca05-206">The following example demonstrates several such cases:</span></span>

[!code-csharp-interactive[round-off errors](snippets/ArithmeticOperators.cs#RoundOffErrors)]

<span data-ttu-id="7ca05-207">有关详细信息，请参阅 [System.Double](/dotnet/api/system.double#remarks)、[System.Single](/dotnet/api/system.single#remarks) 或 [System.Decimal](/dotnet/api/system.decimal#remarks) 参考页上的注解。</span><span class="sxs-lookup"><span data-stu-id="7ca05-207">For more information, see remarks at the [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks), or [System.Decimal](/dotnet/api/system.decimal#remarks) reference pages.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="7ca05-208">运算符可重载性</span><span class="sxs-lookup"><span data-stu-id="7ca05-208">Operator overloadability</span></span>

<span data-ttu-id="7ca05-209">用户定义类型可以[重载](operator-overloading.md)一元（`++`、`--`、`+` 和 `-`）和二元（`*`、`/`、`%`、`+` 和 `-`）算术运算符。</span><span class="sxs-lookup"><span data-stu-id="7ca05-209">A user-defined type can [overload](operator-overloading.md) the unary (`++`, `--`, `+`, and `-`) and binary (`*`, `/`, `%`, `+`, and `-`) arithmetic operators.</span></span> <span data-ttu-id="7ca05-210">重载二元运算符时，对应的复合赋值运算符也会隐式重载。</span><span class="sxs-lookup"><span data-stu-id="7ca05-210">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="7ca05-211">用户定义类型不能显式重载复合赋值运算符。</span><span class="sxs-lookup"><span data-stu-id="7ca05-211">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7ca05-212">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="7ca05-212">C# language specification</span></span>

<span data-ttu-id="7ca05-213">有关更多信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)的以下部分：</span><span class="sxs-lookup"><span data-stu-id="7ca05-213">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="7ca05-214">后缀增量和减量运算符</span><span class="sxs-lookup"><span data-stu-id="7ca05-214">Postfix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [<span data-ttu-id="7ca05-215">前缀增量和减量运算符</span><span class="sxs-lookup"><span data-stu-id="7ca05-215">Prefix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [<span data-ttu-id="7ca05-216">一元加运算符</span><span class="sxs-lookup"><span data-stu-id="7ca05-216">Unary plus operator</span></span>](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [<span data-ttu-id="7ca05-217">一元减运算符</span><span class="sxs-lookup"><span data-stu-id="7ca05-217">Unary minus operator</span></span>](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [<span data-ttu-id="7ca05-218">乘法运算符</span><span class="sxs-lookup"><span data-stu-id="7ca05-218">Multiplication operator</span></span>](~/_csharplang/spec/expressions.md#multiplication-operator)
- [<span data-ttu-id="7ca05-219">除法运算符</span><span class="sxs-lookup"><span data-stu-id="7ca05-219">Division operator</span></span>](~/_csharplang/spec/expressions.md#division-operator)
- [<span data-ttu-id="7ca05-220">余数运算符</span><span class="sxs-lookup"><span data-stu-id="7ca05-220">Remainder operator</span></span>](~/_csharplang/spec/expressions.md#remainder-operator)
- [<span data-ttu-id="7ca05-221">加法运算符</span><span class="sxs-lookup"><span data-stu-id="7ca05-221">Addition operator</span></span>](~/_csharplang/spec/expressions.md#addition-operator)
- [<span data-ttu-id="7ca05-222">减法运算符</span><span class="sxs-lookup"><span data-stu-id="7ca05-222">Subtraction operator</span></span>](~/_csharplang/spec/expressions.md#subtraction-operator)
- [<span data-ttu-id="7ca05-223">复合赋值</span><span class="sxs-lookup"><span data-stu-id="7ca05-223">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="7ca05-224">checked 和 unchecked 运算符</span><span class="sxs-lookup"><span data-stu-id="7ca05-224">The checked and unchecked operators</span></span>](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [<span data-ttu-id="7ca05-225">数值提升</span><span class="sxs-lookup"><span data-stu-id="7ca05-225">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="7ca05-226">请参阅</span><span class="sxs-lookup"><span data-stu-id="7ca05-226">See also</span></span>

- [<span data-ttu-id="7ca05-227">C# 参考</span><span class="sxs-lookup"><span data-stu-id="7ca05-227">C# reference</span></span>](../index.md)
- [<span data-ttu-id="7ca05-228">C# 运算符</span><span class="sxs-lookup"><span data-stu-id="7ca05-228">C# operators</span></span>](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [<span data-ttu-id="7ca05-229">.NET 中的数字</span><span class="sxs-lookup"><span data-stu-id="7ca05-229">Numerics in .NET</span></span>](../../../standard/numerics.md)

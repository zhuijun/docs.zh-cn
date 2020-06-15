---
title: 浮点数值类型 - C# 引用
description: 了解内置 C# 浮点类型：float、double 和 decimal
ms.date: 02/10/2020
f1_keywords:
- float
- float_CSharpKeyword
- double
- double_CSharpKeyword
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- floating-point numbers [C#]
- ranges of floating-point types [C#]
- size of floating-point types [C#]
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: a1142d1aa04003ae1942902672cfc7a05edc99c0
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662662"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="d9e0a-103">浮点数值类型（C# 引用）</span><span class="sxs-lookup"><span data-stu-id="d9e0a-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="d9e0a-104">浮点数值类型表示实数。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-104">The *floating-point numeric types* represent real numbers.</span></span> <span data-ttu-id="d9e0a-105">所有浮点型数值类型均为[值类型](value-types.md)。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-105">All floating-point numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="d9e0a-106">它们还是[简单类型](value-types.md#built-in-value-types)，可以使用[文本](#real-literals)进行初始化。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#real-literals).</span></span> <span data-ttu-id="d9e0a-107">所有浮点数值类型都支持[算术](../operators/arithmetic-operators.md)、[比较](../operators/comparison-operators.md)和[相等](../operators/equality-operators.md)运算符。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-107">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="d9e0a-108">浮点类型的特征</span><span class="sxs-lookup"><span data-stu-id="d9e0a-108">Characteristics of the floating-point types</span></span>

<span data-ttu-id="d9e0a-109">C# 支持以下预定义浮点类型：</span><span class="sxs-lookup"><span data-stu-id="d9e0a-109">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="d9e0a-110">C# 类型/关键字</span><span class="sxs-lookup"><span data-stu-id="d9e0a-110">C# type/keyword</span></span>|<span data-ttu-id="d9e0a-111">大致范围</span><span class="sxs-lookup"><span data-stu-id="d9e0a-111">Approximate range</span></span>|<span data-ttu-id="d9e0a-112">精度</span><span class="sxs-lookup"><span data-stu-id="d9e0a-112">Precision</span></span>|<span data-ttu-id="d9e0a-113">大小</span><span class="sxs-lookup"><span data-stu-id="d9e0a-113">Size</span></span>|<span data-ttu-id="d9e0a-114">.NET 类型</span><span class="sxs-lookup"><span data-stu-id="d9e0a-114">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|<span data-ttu-id="d9e0a-115">±1.5 x 10<sup>−45</sup> 至 ±3.4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="d9e0a-115">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="d9e0a-116">大约 6-9 位数字</span><span class="sxs-lookup"><span data-stu-id="d9e0a-116">~6-9 digits</span></span>|<span data-ttu-id="d9e0a-117">4 个字节</span><span class="sxs-lookup"><span data-stu-id="d9e0a-117">4 bytes</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="d9e0a-118">±5.0 × 10<sup>−324</sup> 到 ±1.7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="d9e0a-118">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="d9e0a-119">大约 15-17 位数字</span><span class="sxs-lookup"><span data-stu-id="d9e0a-119">~15-17 digits</span></span>|<span data-ttu-id="d9e0a-120">8 个字节</span><span class="sxs-lookup"><span data-stu-id="d9e0a-120">8 bytes</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="d9e0a-121">±1.0 x 10<sup>-28</sup> 至 ±7.9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="d9e0a-121">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="d9e0a-122">28-29 位</span><span class="sxs-lookup"><span data-stu-id="d9e0a-122">28-29 digits</span></span>|<span data-ttu-id="d9e0a-123">16 个字节</span><span class="sxs-lookup"><span data-stu-id="d9e0a-123">16 bytes</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="d9e0a-124">在上表中，最左侧列中的每个 C# 类型关键字都是相应 .NET 类型的别名。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-124">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="d9e0a-125">它们是可互换的。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-125">They are interchangeable.</span></span> <span data-ttu-id="d9e0a-126">例如，以下声明声明了相同类型的变量：</span><span class="sxs-lookup"><span data-stu-id="d9e0a-126">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="d9e0a-127">每个浮点类型的默认值都为零，`0`。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-127">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="d9e0a-128">每个浮点类型都有 `MinValue` 和 `MaxValue` 常量，提供该类型的最小值和最大有限值。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-128">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="d9e0a-129">`float` and `double` 类型还提供可表示非数字和无穷大值的常量。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-129">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="d9e0a-130">例如，`double` 类型提供以下常量：<xref:System.Double.NaN?displayProperty=nameWithType>、<xref:System.Double.NegativeInfinity?displayProperty=nameWithType> 和 <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-130">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="d9e0a-131">与 `float` 和 `double` 相比，`decimal` 类型具有更高的精度和更小的范围，因此它适合于财务和货币计算。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-131">Because the `decimal` type has more precision and a smaller range than both `float` and `double`, it's appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="d9e0a-132">可在表达式中将[整型](integral-numeric-types.md)类型与 `float` 和 `double` 类型混合使用功能。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-132">You can mix [integral](integral-numeric-types.md) types and the `float` and `double` types in an expression.</span></span> <span data-ttu-id="d9e0a-133">在这种情况下，整型类型隐式转换为其中一种浮点类型，且必要时，`float` 类型隐式转换为 `double`。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-133">In this case, integral types are implicitly converted to one of the floating-point types and, if necessary, the `float` type is implicitly converted to `double`.</span></span> <span data-ttu-id="d9e0a-134">此表达式的计算方式如下：</span><span class="sxs-lookup"><span data-stu-id="d9e0a-134">The expression is evaluated as follows:</span></span>

- <span data-ttu-id="d9e0a-135">如果表达式中有 `double` 类型，则表达式在关系比较和相等比较中求值得到 `double` 或 [`bool`](bool.md)。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-135">If there is `double` type in the expression, the expression evaluates to `double`, or to [`bool`](bool.md) in relational and equality comparisons.</span></span>
- <span data-ttu-id="d9e0a-136">如果表达式中没有 `double` 类型，则表达式在关系比较和相等比较中求值得到 `float` 或 `bool`。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-136">If there is no `double` type in the expression, the expression evaluates to `float`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="d9e0a-137">你还可在表达式中混合使用整型类型和 `decimal` 类型。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-137">You can also mix integral types and the `decimal` type in an expression.</span></span> <span data-ttu-id="d9e0a-138">在这种情况下，整型类型隐式转换为 `decimal` 类型，并且表达式在关系比较和相等比较中求值得到 `decimal` 或 `bool`。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-138">In this case, integral types are implicitly converted to the `decimal` type and the expression evaluates to `decimal`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="d9e0a-139">不能在表达式中将 `decimal` 类型与 `float` 和 `double` 类型混合使用。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-139">You cannot mix the `decimal` type with the `float` and `double` types in an expression.</span></span> <span data-ttu-id="d9e0a-140">在这种情况下，如果你想要执行算术运算、比较运算或相等运算，则必须将操作数显式转换为 `decimal` 或反向转换，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="d9e0a-140">In this case, if you want to perform arithmetic, comparison, or equality operations, you must explicitly convert the operands either from or to the `decimal` type, as the following example shows:</span></span>

```csharp-interactive
double a = 1.0;
decimal b = 2.1m;
Console.WriteLine(a + (double)b);
Console.WriteLine((decimal)a + b);
```

<span data-ttu-id="d9e0a-141">可以使用[标准数字格式字符串](../../../standard/base-types/standard-numeric-format-strings.md)或[自定义数字格式字符串](../../../standard/base-types/custom-numeric-format-strings.md)设置浮点值的格式。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-141">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="real-literals"></a><span data-ttu-id="d9e0a-142">真实文本</span><span class="sxs-lookup"><span data-stu-id="d9e0a-142">Real literals</span></span>

<span data-ttu-id="d9e0a-143">真实文本的类型由其后缀确定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d9e0a-143">The type of a real literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="d9e0a-144">不带后缀的文本或带有 `d` 或 `D` 后缀的文本的类型为 `double`</span><span class="sxs-lookup"><span data-stu-id="d9e0a-144">The literal without suffix or with the `d` or `D` suffix is of type `double`</span></span>
- <span data-ttu-id="d9e0a-145">带有 `f` 或 `F` 后缀的文本的类型为 `float`</span><span class="sxs-lookup"><span data-stu-id="d9e0a-145">The literal with the `f` or `F` suffix is of type `float`</span></span>
- <span data-ttu-id="d9e0a-146">带有 `m` 或 `M` 后缀的文本的类型为 `decimal`</span><span class="sxs-lookup"><span data-stu-id="d9e0a-146">The literal with the `m` or `M` suffix is of type `decimal`</span></span>

<span data-ttu-id="d9e0a-147">下面的代码演示每种类型的示例：</span><span class="sxs-lookup"><span data-stu-id="d9e0a-147">The following code demonstrates an example of each:</span></span>

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

<span data-ttu-id="d9e0a-148">前面的示例还演示了如何将 `_` 用作数字分隔符（从 C# 7.0 开始提供支持）。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-148">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="d9e0a-149">可以将数字分隔符用于所有类型的数字文本。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-149">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="d9e0a-150">还可以使用科学记数法，即指定真实文本的指数部分，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="d9e0a-150">You can also use scientific notation, that is, specify an exponent part of a real literal, as the following example shows:</span></span>

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a><span data-ttu-id="d9e0a-151">转换</span><span class="sxs-lookup"><span data-stu-id="d9e0a-151">Conversions</span></span>

<span data-ttu-id="d9e0a-152">浮点数值类型之间只有一种隐式转换：从 `float` 到 `double`。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-152">There is only one implicit conversion between floating-point numeric types: from `float` to `double`.</span></span> <span data-ttu-id="d9e0a-153">但是，可以使用[显式强制转换](../operators/type-testing-and-cast.md#cast-expression)将任何浮点类型转换为任何其他浮点类型。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-153">However, you can convert any floating-point type to any other floating-point type with the [explicit cast](../operators/type-testing-and-cast.md#cast-expression).</span></span> <span data-ttu-id="d9e0a-154">有关详细信息，请参阅[内置数值转换](numeric-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-154">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d9e0a-155">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="d9e0a-155">C# language specification</span></span>

<span data-ttu-id="d9e0a-156">有关更多信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)的以下部分：</span><span class="sxs-lookup"><span data-stu-id="d9e0a-156">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="d9e0a-157">浮点类型</span><span class="sxs-lookup"><span data-stu-id="d9e0a-157">Floating-point types</span></span>](~/_csharplang/spec/types.md#floating-point-types)
- [<span data-ttu-id="d9e0a-158">十进制类型</span><span class="sxs-lookup"><span data-stu-id="d9e0a-158">The decimal type</span></span>](~/_csharplang/spec/types.md#the-decimal-type)
- [<span data-ttu-id="d9e0a-159">真实文本</span><span class="sxs-lookup"><span data-stu-id="d9e0a-159">Real literals</span></span>](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a><span data-ttu-id="d9e0a-160">请参阅</span><span class="sxs-lookup"><span data-stu-id="d9e0a-160">See also</span></span>

- [<span data-ttu-id="d9e0a-161">C# 参考</span><span class="sxs-lookup"><span data-stu-id="d9e0a-161">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d9e0a-162">值类型</span><span class="sxs-lookup"><span data-stu-id="d9e0a-162">Value types</span></span>](value-types.md)
- [<span data-ttu-id="d9e0a-163">整型类型</span><span class="sxs-lookup"><span data-stu-id="d9e0a-163">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="d9e0a-164">标准数字格式字符串</span><span class="sxs-lookup"><span data-stu-id="d9e0a-164">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="d9e0a-165">.NET 中的数字</span><span class="sxs-lookup"><span data-stu-id="d9e0a-165">Numerics in .NET</span></span>](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>

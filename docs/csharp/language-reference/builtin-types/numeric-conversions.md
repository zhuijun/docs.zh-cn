---
description: 了解 C# 中内置数值转换间的隐式转换和显式转换
title: 内置数值转换 - C# 参考
ms.date: 10/22/2019
helpviewer_keywords:
- implicit numeric conversions [C#]
- explicit numeric conversion [C#]
- numeric conversions [C#], implicit
- numeric conversions [C#], explicit
- conversions [C#], implicit numeric
- conversions [C#], explicit numeric
ms.openlocfilehash: ee5def3b5e0e067919a8c8335db701dbb6dd4d88
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142240"
---
# <a name="built-in-numeric-conversions-c-reference"></a><span data-ttu-id="aaa54-103">内置数值转换（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="aaa54-103">Built-in numeric conversions (C# reference)</span></span>

<span data-ttu-id="aaa54-104">C# 提供了一组[整型](integral-numeric-types.md)和[浮点](floating-point-numeric-types.md)数值类型。</span><span class="sxs-lookup"><span data-stu-id="aaa54-104">C# provides a set of [integral](integral-numeric-types.md) and [floating-point](floating-point-numeric-types.md) numeric types.</span></span> <span data-ttu-id="aaa54-105">任何两种数值类型之间都可以进行隐式或显式转换。</span><span class="sxs-lookup"><span data-stu-id="aaa54-105">There exists a conversion between any two numeric types, either implicit or explicit.</span></span> <span data-ttu-id="aaa54-106">必须使用[强制转换表达式](../operators/type-testing-and-cast.md#cast-expression)来执行显式转换。</span><span class="sxs-lookup"><span data-stu-id="aaa54-106">You must use a [cast expression](../operators/type-testing-and-cast.md#cast-expression) to perform an explicit conversion.</span></span>

## <a name="implicit-numeric-conversions"></a><span data-ttu-id="aaa54-107">隐式数值转换</span><span class="sxs-lookup"><span data-stu-id="aaa54-107">Implicit numeric conversions</span></span>

<span data-ttu-id="aaa54-108">下表显示内置数值类型之间的预定义隐式转换：</span><span class="sxs-lookup"><span data-stu-id="aaa54-108">The following table shows the predefined implicit conversions between the built-in numeric types:</span></span>

|<span data-ttu-id="aaa54-109">From</span><span class="sxs-lookup"><span data-stu-id="aaa54-109">From</span></span>|<span data-ttu-id="aaa54-110">到</span><span class="sxs-lookup"><span data-stu-id="aaa54-110">To</span></span>|
|----------|--------|
|[<span data-ttu-id="aaa54-111">sbyte</span><span class="sxs-lookup"><span data-stu-id="aaa54-111">sbyte</span></span>](integral-numeric-types.md)|<span data-ttu-id="aaa54-112">`short`、`int`、`long`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="aaa54-112">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="aaa54-113">byte</span><span class="sxs-lookup"><span data-stu-id="aaa54-113">byte</span></span>](integral-numeric-types.md)|<span data-ttu-id="aaa54-114">`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="aaa54-114">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="aaa54-115">short</span><span class="sxs-lookup"><span data-stu-id="aaa54-115">short</span></span>](integral-numeric-types.md)|<span data-ttu-id="aaa54-116">`int`、`long`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="aaa54-116">`int`, `long`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="aaa54-117">ushort</span><span class="sxs-lookup"><span data-stu-id="aaa54-117">ushort</span></span>](integral-numeric-types.md)|<span data-ttu-id="aaa54-118">`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`。</span><span class="sxs-lookup"><span data-stu-id="aaa54-118">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="aaa54-119">int</span><span class="sxs-lookup"><span data-stu-id="aaa54-119">int</span></span>](integral-numeric-types.md)|<span data-ttu-id="aaa54-120">`long`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="aaa54-120">`long`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="aaa54-121">uint</span><span class="sxs-lookup"><span data-stu-id="aaa54-121">uint</span></span>](integral-numeric-types.md)|<span data-ttu-id="aaa54-122">`long`、`ulong`、`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="aaa54-122">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="aaa54-123">long</span><span class="sxs-lookup"><span data-stu-id="aaa54-123">long</span></span>](integral-numeric-types.md)|<span data-ttu-id="aaa54-124">`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="aaa54-124">`float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="aaa54-125">ulong</span><span class="sxs-lookup"><span data-stu-id="aaa54-125">ulong</span></span>](integral-numeric-types.md)|<span data-ttu-id="aaa54-126">`float`、`double` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="aaa54-126">`float`, `double`, or `decimal`</span></span>|
|[<span data-ttu-id="aaa54-127">float</span><span class="sxs-lookup"><span data-stu-id="aaa54-127">float</span></span>](floating-point-numeric-types.md)|`double`|

> [!NOTE]
> <span data-ttu-id="aaa54-128">从 `int`、`uint``long` 或 `ulong` 到 `float` 的隐式转换以及从 `long` 或 `ulong` 到 `double` 的隐式转换可能会丢失精准率，但绝不会丢失一个数量级。</span><span class="sxs-lookup"><span data-stu-id="aaa54-128">The implicit conversions from `int`, `uint`, `long`, or `ulong` to `float` and from `long` or `ulong` to `double` may cause a loss of precision, but never a loss of an order of magnitude.</span></span> <span data-ttu-id="aaa54-129">其他隐式数值转换不会丢失任何信息。</span><span class="sxs-lookup"><span data-stu-id="aaa54-129">The other implicit numeric conversions never lose any information.</span></span>

<span data-ttu-id="aaa54-130">另请注意</span><span class="sxs-lookup"><span data-stu-id="aaa54-130">Also note that</span></span>

- <span data-ttu-id="aaa54-131">任何[整型数值类型](integral-numeric-types.md)都可以隐式转换为任何[浮点数值类型](floating-point-numeric-types.md)。</span><span class="sxs-lookup"><span data-stu-id="aaa54-131">Any [integral numeric type](integral-numeric-types.md) is implicitly convertible to any [floating-point numeric type](floating-point-numeric-types.md).</span></span>

- <span data-ttu-id="aaa54-132">不存在针对 `byte` 和 `sbyte` 类型的隐式转换。</span><span class="sxs-lookup"><span data-stu-id="aaa54-132">There are no implicit conversions to the `byte` and `sbyte` types.</span></span> <span data-ttu-id="aaa54-133">不存在从 `double` 和 `decimal` 类型的隐式转换。</span><span class="sxs-lookup"><span data-stu-id="aaa54-133">There are no implicit conversions from the `double` and `decimal` types.</span></span>

- <span data-ttu-id="aaa54-134">`decimal` 类型和 `float` 或 `double` 类型之间不存在隐式转换。</span><span class="sxs-lookup"><span data-stu-id="aaa54-134">There are no implicit conversions between the `decimal` type and the `float` or `double` types.</span></span>

- <span data-ttu-id="aaa54-135">类型 `int` 的常量表达式的值（例如，由整数文本所表示的值）如果在目标类型的范围内，则可隐式转换为 `sbyte`、`byte`、`short`、`ushort`、`uint` 或 `ulong`：</span><span class="sxs-lookup"><span data-stu-id="aaa54-135">A value of a constant expression of type `int` (for example, a value represented by an integer literal) can be implicitly converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, if it's within the range of the destination type:</span></span>

  ```csharp
  byte a = 13;
  byte b = 300;  // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

  <span data-ttu-id="aaa54-136">如前面的示例所示，如果该常量值不在目标类型的范围内，则发生编译器错误 [CS0031](../../misc/cs0031.md)。</span><span class="sxs-lookup"><span data-stu-id="aaa54-136">As the preceding example shows, if the constant value is not within the range of the destination type, a compiler error [CS0031](../../misc/cs0031.md) occurs.</span></span>

## <a name="explicit-numeric-conversions"></a><span data-ttu-id="aaa54-137">显式数值转换</span><span class="sxs-lookup"><span data-stu-id="aaa54-137">Explicit numeric conversions</span></span>

<span data-ttu-id="aaa54-138">下表显示不存在[隐式转换](#implicit-numeric-conversions)的内置数值类型之间的预定义显式转换：</span><span class="sxs-lookup"><span data-stu-id="aaa54-138">The following table shows the predefined explicit conversions between the built-in numeric types for which there is no [implicit conversion](#implicit-numeric-conversions):</span></span>

|<span data-ttu-id="aaa54-139">From</span><span class="sxs-lookup"><span data-stu-id="aaa54-139">From</span></span>|<span data-ttu-id="aaa54-140">到</span><span class="sxs-lookup"><span data-stu-id="aaa54-140">To</span></span>|
|----------|--------|
|[<span data-ttu-id="aaa54-141">sbyte</span><span class="sxs-lookup"><span data-stu-id="aaa54-141">sbyte</span></span>](integral-numeric-types.md)|<span data-ttu-id="aaa54-142">`byte`、`ushort`、`uint` 或 `ulong`</span><span class="sxs-lookup"><span data-stu-id="aaa54-142">`byte`, `ushort`, `uint`, or `ulong`</span></span>|
|[<span data-ttu-id="aaa54-143">byte</span><span class="sxs-lookup"><span data-stu-id="aaa54-143">byte</span></span>](integral-numeric-types.md)|`sbyte`|
|[<span data-ttu-id="aaa54-144">short</span><span class="sxs-lookup"><span data-stu-id="aaa54-144">short</span></span>](integral-numeric-types.md)|<span data-ttu-id="aaa54-145">`sbyte`、`byte`、`ushort`、`uint` 或 `ulong`</span><span class="sxs-lookup"><span data-stu-id="aaa54-145">`sbyte`, `byte`, `ushort`, `uint`, or `ulong`</span></span>|
|[<span data-ttu-id="aaa54-146">ushort</span><span class="sxs-lookup"><span data-stu-id="aaa54-146">ushort</span></span>](integral-numeric-types.md)|<span data-ttu-id="aaa54-147">`sbyte`、`byte` 或 `short`</span><span class="sxs-lookup"><span data-stu-id="aaa54-147">`sbyte`, `byte`, or `short`</span></span>|
|[<span data-ttu-id="aaa54-148">int</span><span class="sxs-lookup"><span data-stu-id="aaa54-148">int</span></span>](integral-numeric-types.md)|<span data-ttu-id="aaa54-149">`sbyte`、`byte`、`short`、`ushort`、`uint` 或 `ulong`</span><span class="sxs-lookup"><span data-stu-id="aaa54-149">`sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`</span></span>|
|[<span data-ttu-id="aaa54-150">uint</span><span class="sxs-lookup"><span data-stu-id="aaa54-150">uint</span></span>](integral-numeric-types.md)|<span data-ttu-id="aaa54-151">`sbyte`、`byte`、`short`、`ushort` 或 `int`</span><span class="sxs-lookup"><span data-stu-id="aaa54-151">`sbyte`, `byte`, `short`, `ushort`, or `int`</span></span>|
|[<span data-ttu-id="aaa54-152">long</span><span class="sxs-lookup"><span data-stu-id="aaa54-152">long</span></span>](integral-numeric-types.md)|<span data-ttu-id="aaa54-153">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint` 或 `ulong`。</span><span class="sxs-lookup"><span data-stu-id="aaa54-153">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, or `ulong`</span></span>|
|[<span data-ttu-id="aaa54-154">ulong</span><span class="sxs-lookup"><span data-stu-id="aaa54-154">ulong</span></span>](integral-numeric-types.md)|<span data-ttu-id="aaa54-155">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint` 或 `long`。</span><span class="sxs-lookup"><span data-stu-id="aaa54-155">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, or `long`</span></span>|
|[<span data-ttu-id="aaa54-156">float</span><span class="sxs-lookup"><span data-stu-id="aaa54-156">float</span></span>](floating-point-numeric-types.md)|<span data-ttu-id="aaa54-157">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="aaa54-157">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, or `decimal`</span></span>|
|[<span data-ttu-id="aaa54-158">double</span><span class="sxs-lookup"><span data-stu-id="aaa54-158">double</span></span>](floating-point-numeric-types.md)|<span data-ttu-id="aaa54-159">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`float` 或 `decimal`</span><span class="sxs-lookup"><span data-stu-id="aaa54-159">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, or `decimal`</span></span>|
|[<span data-ttu-id="aaa54-160">decimal</span><span class="sxs-lookup"><span data-stu-id="aaa54-160">decimal</span></span>](floating-point-numeric-types.md)|<span data-ttu-id="aaa54-161">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`float` 或 `double`</span><span class="sxs-lookup"><span data-stu-id="aaa54-161">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, or `double`</span></span>|

> [!NOTE]
> <span data-ttu-id="aaa54-162">显式数值转换可能会导致数据丢失或引发异常，通常为 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="aaa54-162">An explicit numeric conversion might result in data loss or throw an exception, typically an <xref:System.OverflowException>.</span></span>

<span data-ttu-id="aaa54-163">另请注意</span><span class="sxs-lookup"><span data-stu-id="aaa54-163">Also note that</span></span>

- <span data-ttu-id="aaa54-164">将整数类型的值转换为另一个整数类型时，结果取决于溢出[检查上下文](../keywords/checked-and-unchecked.md)。</span><span class="sxs-lookup"><span data-stu-id="aaa54-164">When you convert a value of an integral type to another integral type, the result depends on the overflow [checking context](../keywords/checked-and-unchecked.md).</span></span> <span data-ttu-id="aaa54-165">在已检查的上下文中，如果源值在目标类型的范围内，则转换成功。</span><span class="sxs-lookup"><span data-stu-id="aaa54-165">In a checked context, the conversion succeeds if the source value is within the range of the destination type.</span></span> <span data-ttu-id="aaa54-166">否则会引发 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="aaa54-166">Otherwise, an <xref:System.OverflowException> is thrown.</span></span> <span data-ttu-id="aaa54-167">在未检查的上下文中，转换始终成功，并按如下方式进行：</span><span class="sxs-lookup"><span data-stu-id="aaa54-167">In an unchecked context, the conversion always succeeds, and proceeds as follows:</span></span>

  - <span data-ttu-id="aaa54-168">如果源类型大于目标类型，则通过放弃其“额外”最高有效位来截断源值。</span><span class="sxs-lookup"><span data-stu-id="aaa54-168">If the source type is larger than the destination type, then the source value is truncated by discarding its "extra" most significant bits.</span></span> <span data-ttu-id="aaa54-169">结果会被视为目标类型的值。</span><span class="sxs-lookup"><span data-stu-id="aaa54-169">The result is then treated as a value of the destination type.</span></span>

  - <span data-ttu-id="aaa54-170">如果源类型小于目标类型，则源值是符号扩展或零扩展，以使其与目标类型的大小相同。</span><span class="sxs-lookup"><span data-stu-id="aaa54-170">If the source type is smaller than the destination type, then the source value is either sign-extended or zero-extended so that it's of the same size as the destination type.</span></span> <span data-ttu-id="aaa54-171">如果源类型带符号，则是符号扩展；如果源类型是无符号的，则是零扩展。</span><span class="sxs-lookup"><span data-stu-id="aaa54-171">Sign-extension is used if the source type is signed; zero-extension is used if the source type is unsigned.</span></span> <span data-ttu-id="aaa54-172">结果会被视为目标类型的值。</span><span class="sxs-lookup"><span data-stu-id="aaa54-172">The result is then treated as a value of the destination type.</span></span>

  - <span data-ttu-id="aaa54-173">如果源类型与目标类型的大小相同，则源值将被视为目标类型的值。</span><span class="sxs-lookup"><span data-stu-id="aaa54-173">If the source type is the same size as the destination type, then the source value is treated as a value of the destination type.</span></span>

- <span data-ttu-id="aaa54-174">将 `decimal` 值转换为整型类型时，此值会向零舍入到最接近的整数值。</span><span class="sxs-lookup"><span data-stu-id="aaa54-174">When you convert a `decimal` value to an integral type, this value is rounded towards zero to the nearest integral value.</span></span> <span data-ttu-id="aaa54-175">如果生成的整数值处于目标类型的范围之外，则会引发 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="aaa54-175">If the resulting integral value is outside the range of the destination type, an <xref:System.OverflowException> is thrown.</span></span>

- <span data-ttu-id="aaa54-176">将 `double` 或 `float` 值转换为整型类型时，此值会向零舍入到最接近的整数值。</span><span class="sxs-lookup"><span data-stu-id="aaa54-176">When you convert a `double` or `float` value to an integral type, this value is rounded towards zero to the nearest integral value.</span></span> <span data-ttu-id="aaa54-177">如果生成的整数值处于目标类型范围之外，则结果会取决于溢出[上下文](../keywords/checked-and-unchecked.md)。</span><span class="sxs-lookup"><span data-stu-id="aaa54-177">If the resulting integral value is outside the range of the destination type, the result depends on the overflow [checking context](../keywords/checked-and-unchecked.md).</span></span> <span data-ttu-id="aaa54-178">在已检查的上下文中，引发 <xref:System.OverflowException>；而在未检查的上下文中，结果是目标类型的未指定值。</span><span class="sxs-lookup"><span data-stu-id="aaa54-178">In a checked context, an <xref:System.OverflowException> is thrown, while in an unchecked context, the result is an unspecified value of the destination type.</span></span>

- <span data-ttu-id="aaa54-179">将 `double` 转换为 `float` 时，`double` 值舍入为最接近的 `float` 值。</span><span class="sxs-lookup"><span data-stu-id="aaa54-179">When you convert `double` to `float`, the `double` value is rounded to the nearest `float` value.</span></span> <span data-ttu-id="aaa54-180">如果 `double` 值太小或太大，无法匹配 `float` 类型，结果将为零或无穷大。</span><span class="sxs-lookup"><span data-stu-id="aaa54-180">If the `double` value is too small or too large to fit into the `float` type, the result is zero or infinity.</span></span>

- <span data-ttu-id="aaa54-181">将 `float` 或 `double` 转换为 `decimal` 时，源值转换为 `decimal` 表示形式，并并五入到第 28 位小数后最接近的数（如果需要）。</span><span class="sxs-lookup"><span data-stu-id="aaa54-181">When you convert `float` or `double` to `decimal`, the source value is converted to `decimal` representation and rounded to the nearest number after the 28th decimal place if required.</span></span> <span data-ttu-id="aaa54-182">根据源值的值，可能出现以下结果之一：</span><span class="sxs-lookup"><span data-stu-id="aaa54-182">Depending on the value of the source value, one of the following results may occur:</span></span>

  - <span data-ttu-id="aaa54-183">如果源值太小，无法表示为 `decimal`，结果则为零。</span><span class="sxs-lookup"><span data-stu-id="aaa54-183">If the source value is too small to be represented as a `decimal`, the result becomes zero.</span></span>

  - <span data-ttu-id="aaa54-184">如果源值为 NaN（非数值）、无穷大或太大而无法表示为 `decimal`，则引发 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="aaa54-184">If the source value is NaN (not a number), infinity, or too large to be represented as a `decimal`, an <xref:System.OverflowException> is thrown.</span></span>

- <span data-ttu-id="aaa54-185">将 `decimal` 转换为 `float` 或 `double` 时，源值分别舍入为最接近的 `float` 或 `double` 值。</span><span class="sxs-lookup"><span data-stu-id="aaa54-185">When you convert `decimal` to `float` or `double`, the source value is rounded to the nearest `float` or `double` value, respectively.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="aaa54-186">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="aaa54-186">C# language specification</span></span>

<span data-ttu-id="aaa54-187">有关更多信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)的以下部分：</span><span class="sxs-lookup"><span data-stu-id="aaa54-187">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="aaa54-188">隐式数值转换</span><span class="sxs-lookup"><span data-stu-id="aaa54-188">Implicit numeric conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-numeric-conversions)
- [<span data-ttu-id="aaa54-189">显式数值转换</span><span class="sxs-lookup"><span data-stu-id="aaa54-189">Explicit numeric conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-numeric-conversions)

## <a name="see-also"></a><span data-ttu-id="aaa54-190">请参阅</span><span class="sxs-lookup"><span data-stu-id="aaa54-190">See also</span></span>

- [<span data-ttu-id="aaa54-191">C# 参考</span><span class="sxs-lookup"><span data-stu-id="aaa54-191">C# reference</span></span>](../index.md)
- [<span data-ttu-id="aaa54-192">强制转换和类型转换</span><span class="sxs-lookup"><span data-stu-id="aaa54-192">Casting and type conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)

---
title: Decimal 数据类型
ms.date: 07/20/2015
f1_keywords:
- vb.Decimal
helpviewer_keywords:
- literal type characters [Visual Basic], D
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- Decimal data type
- D literal type character [Visual Basic]
- decimals, Decimal data type
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- decimal keyword [Visual Basic]
- numbers [Visual Basic], real
- variable-precision numbers
- zeros, trailing
- '@ identifier type character'
- identifier type characters [Visual Basic], @
ms.assetid: 1d855b45-afe2-45b0-a623-96b6f63a43d5
ms.openlocfilehash: 690c8061b6df1115aa24668520170b44edfa8287
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415642"
---
# <a name="decimal-data-type-visual-basic"></a><span data-ttu-id="ce2fd-102">Decimal 数据类型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce2fd-102">Decimal Data Type (Visual Basic)</span></span>

<span data-ttu-id="ce2fd-103">保存由表示 96 位（12 字节）整数按 10 的可变次幂缩放所得的 128 位（16 字节）值。</span><span class="sxs-lookup"><span data-stu-id="ce2fd-103">Holds signed 128-bit (16-byte) values representing 96-bit (12-byte) integer numbers scaled by a variable power of 10.</span></span> <span data-ttu-id="ce2fd-104">缩放系数指定小数点右侧的数字位数;范围为0到28。</span><span class="sxs-lookup"><span data-stu-id="ce2fd-104">The scaling factor specifies the number of digits to the right of the decimal point; it ranges from 0 through 28.</span></span> <span data-ttu-id="ce2fd-105">当小数位数为0（没有小数位数）时，可能的最大值为 +/-79228162514264337593543950335 （+/-7.9228162514264337593543950335E + 28）。</span><span class="sxs-lookup"><span data-stu-id="ce2fd-105">With a scale of 0 (no decimal places), the largest possible value is +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E+28).</span></span> <span data-ttu-id="ce2fd-106">如果有28个小数位数，则最大值为 +/-7.9228162514264337593543950335，最小非零值为 +/-0.0000000000000000000000000001 （+/-1E-28）。</span><span class="sxs-lookup"><span data-stu-id="ce2fd-106">With 28 decimal places, the largest value is +/-7.9228162514264337593543950335, and the smallest nonzero value is +/-0.0000000000000000000000000001 (+/-1E-28).</span></span>

## <a name="remarks"></a><span data-ttu-id="ce2fd-107">备注</span><span class="sxs-lookup"><span data-stu-id="ce2fd-107">Remarks</span></span>

<span data-ttu-id="ce2fd-108">`Decimal`数据类型为数字提供的有效位数最多。</span><span class="sxs-lookup"><span data-stu-id="ce2fd-108">The `Decimal` data type provides the greatest number of significant digits for a number.</span></span> <span data-ttu-id="ce2fd-109">它最多支持29个有效位数，并可表示超过 7.9228 x 10 ^ 28 的值。</span><span class="sxs-lookup"><span data-stu-id="ce2fd-109">It supports up to 29 significant digits and can represent values in excess of 7.9228 x 10^28.</span></span> <span data-ttu-id="ce2fd-110">它特别适用于需要大量数字但不允许舍入误差的计算（例如财务）。</span><span class="sxs-lookup"><span data-stu-id="ce2fd-110">It is particularly suitable for calculations, such as financial, that require a large number of digits but cannot tolerate rounding errors.</span></span>

<span data-ttu-id="ce2fd-111">`Decimal` 的默认值为 0。</span><span class="sxs-lookup"><span data-stu-id="ce2fd-111">The default value of `Decimal` is 0.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="ce2fd-112">编程提示</span><span class="sxs-lookup"><span data-stu-id="ce2fd-112">Programming Tips</span></span>

- <span data-ttu-id="ce2fd-113">**Precision.**</span><span class="sxs-lookup"><span data-stu-id="ce2fd-113">**Precision.**</span></span> <span data-ttu-id="ce2fd-114">`Decimal`不是浮点数据类型。</span><span class="sxs-lookup"><span data-stu-id="ce2fd-114">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="ce2fd-115">`Decimal`结构包含一个二进制整数值以及一个符号位和一个整数比例因子，用于指定值的哪一部分是小数部分。</span><span class="sxs-lookup"><span data-stu-id="ce2fd-115">The `Decimal` structure holds a binary integer value, together with a sign bit and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span> <span data-ttu-id="ce2fd-116">因此， `Decimal` 在内存中，数字的表示形式比浮点类型（和）更精确 `Single` `Double` 。</span><span class="sxs-lookup"><span data-stu-id="ce2fd-116">Because of this, `Decimal` numbers have a more precise representation in memory than floating-point types (`Single` and `Double`).</span></span>

- <span data-ttu-id="ce2fd-117">**性能。**</span><span class="sxs-lookup"><span data-stu-id="ce2fd-117">**Performance.**</span></span> <span data-ttu-id="ce2fd-118">`Decimal`数据类型是所有数值类型的最慢。</span><span class="sxs-lookup"><span data-stu-id="ce2fd-118">The `Decimal` data type is the slowest of all the numeric types.</span></span> <span data-ttu-id="ce2fd-119">在选择数据类型之前，应权衡精度与性能的重要性。</span><span class="sxs-lookup"><span data-stu-id="ce2fd-119">You should weigh the importance of precision against performance before choosing a data type.</span></span>

- <span data-ttu-id="ce2fd-120">**扩大.**</span><span class="sxs-lookup"><span data-stu-id="ce2fd-120">**Widening.**</span></span> <span data-ttu-id="ce2fd-121">`Decimal`数据类型扩大到 `Single` 或 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="ce2fd-121">The `Decimal` data type widens to `Single` or `Double`.</span></span> <span data-ttu-id="ce2fd-122">这意味着你可以转换 `Decimal` 为这些类型中的任何一种，而不会遇到 <xref:System.OverflowException?displayProperty=nameWithType> 错误。</span><span class="sxs-lookup"><span data-stu-id="ce2fd-122">This means you can convert `Decimal` to either of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="ce2fd-123">**尾随零。**</span><span class="sxs-lookup"><span data-stu-id="ce2fd-123">**Trailing Zeros.**</span></span> <span data-ttu-id="ce2fd-124">Visual Basic 不会在文本中存储尾随零 `Decimal` 。</span><span class="sxs-lookup"><span data-stu-id="ce2fd-124">Visual Basic does not store trailing zeros in a `Decimal` literal.</span></span> <span data-ttu-id="ce2fd-125">但是， `Decimal` 变量保留了任何尾随零获取计算。</span><span class="sxs-lookup"><span data-stu-id="ce2fd-125">However, a `Decimal` variable preserves any trailing zeros acquired computationally.</span></span> <span data-ttu-id="ce2fd-126">下面的示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="ce2fd-126">The following example illustrates this.</span></span>

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  <span data-ttu-id="ce2fd-127">`MsgBox`上一示例中的输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="ce2fd-127">The output of `MsgBox` in the preceding example is as follows:</span></span>

  ```console
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- <span data-ttu-id="ce2fd-128">**键入字符。**</span><span class="sxs-lookup"><span data-stu-id="ce2fd-128">**Type Characters.**</span></span> <span data-ttu-id="ce2fd-129">将文本类型字符 `D` 追加到文本会将其强制转换为 `Decimal` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="ce2fd-129">Appending the literal type character `D` to a literal forces it to the `Decimal` data type.</span></span> <span data-ttu-id="ce2fd-130">将标识符类型字符 `@` 追加到任何标识符会将其强制转换为 `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="ce2fd-130">Appending the identifier type character `@` to any identifier forces it to `Decimal`.</span></span>

- <span data-ttu-id="ce2fd-131">**Framework 类型。**</span><span class="sxs-lookup"><span data-stu-id="ce2fd-131">**Framework Type.**</span></span> <span data-ttu-id="ce2fd-132">.NET Framework 中的对应类型是 <xref:System.Decimal?displayProperty=nameWithType> 结构。</span><span class="sxs-lookup"><span data-stu-id="ce2fd-132">The corresponding type in the .NET Framework is the <xref:System.Decimal?displayProperty=nameWithType> structure.</span></span>

## <a name="range"></a><span data-ttu-id="ce2fd-133">范围</span><span class="sxs-lookup"><span data-stu-id="ce2fd-133">Range</span></span>

 <span data-ttu-id="ce2fd-134">你可能需要使用 `D` 类型字符将较大的值分配给 `Decimal` 变量或常数。</span><span class="sxs-lookup"><span data-stu-id="ce2fd-134">You might need to use the `D` type character to assign a large value to a `Decimal` variable or constant.</span></span> <span data-ttu-id="ce2fd-135">此要求是因为编译器会将文本解释为 `Long` ，除非文本类型字符跟在文本后，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="ce2fd-135">This requirement is because the compiler interprets a literal as `Long` unless a literal type character follows the literal, as the following example shows.</span></span>

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

<span data-ttu-id="ce2fd-136">的声明 `bigDec1` 不会产生溢出，因为赋给它的值落在范围内 `Long` 。</span><span class="sxs-lookup"><span data-stu-id="ce2fd-136">The declaration for `bigDec1` doesn't produce an overflow because the value that's assigned to it falls within the range for `Long`.</span></span> <span data-ttu-id="ce2fd-137">`Long`可以将值分配给 `Decimal` 变量。</span><span class="sxs-lookup"><span data-stu-id="ce2fd-137">The `Long` value can be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="ce2fd-138">的声明 `bigDec2` 会生成溢出错误，因为赋给它的值太大 `Long` 。</span><span class="sxs-lookup"><span data-stu-id="ce2fd-138">The declaration for `bigDec2` generates an overflow error because the value that's assigned to it is too large for `Long`.</span></span> <span data-ttu-id="ce2fd-139">由于不能首先将数字文本解释为 `Long` ，因此不能将其分配给 `Decimal` 变量。</span><span class="sxs-lookup"><span data-stu-id="ce2fd-139">Because the numeric literal can't first be interpreted as a `Long`, it can't be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="ce2fd-140">对于 `bigDec3` ，文本类型字符 `D` 通过强制编译器将文本解释为而不是，来解决此问题 `Decimal` `Long` 。</span><span class="sxs-lookup"><span data-stu-id="ce2fd-140">For `bigDec3`, the literal type character `D` solves the problem by forcing the compiler to interpret the literal as a `Decimal` instead of as a `Long`.</span></span>

## <a name="see-also"></a><span data-ttu-id="ce2fd-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ce2fd-141">See also</span></span>

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [<span data-ttu-id="ce2fd-142">数据类型</span><span class="sxs-lookup"><span data-stu-id="ce2fd-142">Data Types</span></span>](index.md)
- [<span data-ttu-id="ce2fd-143">Single 数据类型</span><span class="sxs-lookup"><span data-stu-id="ce2fd-143">Single Data Type</span></span>](single-data-type.md)
- [<span data-ttu-id="ce2fd-144">Double 数据类型</span><span class="sxs-lookup"><span data-stu-id="ce2fd-144">Double Data Type</span></span>](double-data-type.md)
- [<span data-ttu-id="ce2fd-145">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="ce2fd-145">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="ce2fd-146">转换摘要</span><span class="sxs-lookup"><span data-stu-id="ce2fd-146">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="ce2fd-147">有效使用数据类型</span><span class="sxs-lookup"><span data-stu-id="ce2fd-147">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)

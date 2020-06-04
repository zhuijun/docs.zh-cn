---
title: SByte 数据类型
ms.date: 04/20/2017
f1_keywords:
- vb.sbyte
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- SByte data type
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
ms.openlocfilehash: e7d45c74056ce5b6aa66674c99e48b5ab60015f0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415565"
---
# <a name="sbyte-data-type-visual-basic"></a><span data-ttu-id="5de27-102">SByte 数据类型（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="5de27-102">SByte data type (Visual Basic)</span></span>

<span data-ttu-id="5de27-103">保存8位有符号整数，其值范围从-128 到127。</span><span class="sxs-lookup"><span data-stu-id="5de27-103">Holds signed 8-bit (1-byte) integers that range in value from -128 through 127.</span></span>

## <a name="remarks"></a><span data-ttu-id="5de27-104">备注</span><span class="sxs-lookup"><span data-stu-id="5de27-104">Remarks</span></span>

<span data-ttu-id="5de27-105">使用 `SByte` 数据类型可包含整数值，这些值不需要的完整数据宽度 `Integer` 甚至一半数据宽度 `Short` 。</span><span class="sxs-lookup"><span data-stu-id="5de27-105">Use the `SByte` data type to contain integer values that do not require the full data width of `Integer` or even the half data width of `Short`.</span></span> <span data-ttu-id="5de27-106">在某些情况下，公共语言运行时可以将变量紧密地打包在 `SByte` 一起，并节省内存消耗。</span><span class="sxs-lookup"><span data-stu-id="5de27-106">In some cases, the common language runtime might be able to pack your `SByte` variables closely together and save memory consumption.</span></span>

<span data-ttu-id="5de27-107">`SByte` 的默认值为 0。</span><span class="sxs-lookup"><span data-stu-id="5de27-107">The default value of `SByte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="5de27-108">文本赋值</span><span class="sxs-lookup"><span data-stu-id="5de27-108">Literal assignments</span></span>

<span data-ttu-id="5de27-109">可以 `SByte` 通过将变量指定为十进制文本、十六进制文本、八进制文本或（从 Visual Basic 2017）作为二进制文本来声明和初始化变量。</span><span class="sxs-lookup"><span data-stu-id="5de27-109">You can declare and initialize an `SByte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span>

<span data-ttu-id="5de27-110">在下面的示例中，将表示为十进制、十六进制和二进制文本的整数等于-102，并将其分配给 `SByte` 值。</span><span class="sxs-lookup"><span data-stu-id="5de27-110">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are assigned to `SByte` values.</span></span> <span data-ttu-id="5de27-111">此示例要求你编译 `/removeintchecks` 编译器开关。</span><span class="sxs-lookup"><span data-stu-id="5de27-111">This example requires that you compile with the `/removeintchecks` compiler switch.</span></span>

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> <span data-ttu-id="5de27-112">使用前缀 `&h` 或 `&H` 表示十六进制文本，使用前缀 `&b` 或表示 `&B` 二进制文本，使用前缀 `&o` 或 `&O` 表示八进制文本。</span><span class="sxs-lookup"><span data-stu-id="5de27-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="5de27-113">十进制文本没有前缀。</span><span class="sxs-lookup"><span data-stu-id="5de27-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="5de27-114">从 Visual Basic 2017 开始，还可以使用下划线字符 `_` 作为数字分隔符来增强可读性，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="5de27-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

<span data-ttu-id="5de27-115">从 Visual Basic 15.5 开始，还可以使用下划线字符（ `_` ）作为前缀和十六进制、二进制或八进制数字之间的前导分隔符。</span><span class="sxs-lookup"><span data-stu-id="5de27-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="5de27-116">例如：</span><span class="sxs-lookup"><span data-stu-id="5de27-116">For example:</span></span>

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="5de27-117">如果整数文本在 `SByte` 范围之外（即，如果它小于 <xref:System.SByte.MinValue?displayProperty=nameWithType> 或大于 <xref:System.SByte.MaxValue?displayProperty=nameWithType>），会发生编译错误。</span><span class="sxs-lookup"><span data-stu-id="5de27-117">If the integer literal is outside the range of `SByte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="5de27-118">如果整数文本没有后缀，则会推理[整数](integer-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="5de27-118">When an integer literal has no suffix, an [Integer](integer-data-type.md) is inferred.</span></span> <span data-ttu-id="5de27-119">如果整数文本超出了类型的范围 `Integer` ，则会推断一个[长](long-data-type.md)整型值。</span><span class="sxs-lookup"><span data-stu-id="5de27-119">If the integer literal is outside the range of the `Integer` type, a [Long](long-data-type.md) is inferred.</span></span> <span data-ttu-id="5de27-120">这意味着，在前面的示例中，数字文本 `0x9A` 和 `0b10011010` 被解释为值为156的32位有符号整数，该值超过了 <xref:System.SByte.MaxValue?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="5de27-120">This means that, in the previous examples, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5de27-121">若要成功地编译将非十进制整数赋给的代码 `SByte` ，可以执行以下任一操作：</span><span class="sxs-lookup"><span data-stu-id="5de27-121">To successfully compile code like this that assigns a non-decimal integer to an `SByte`, you can do either of the following:</span></span>

- <span data-ttu-id="5de27-122">通过使用编译器开关进行编译来禁用整数边界检查 `/removeintchecks` 。</span><span class="sxs-lookup"><span data-stu-id="5de27-122">Disable integer bounds checks by compiling with the `/removeintchecks` compiler switch.</span></span>

- <span data-ttu-id="5de27-123">使用[类型字符](../../programming-guide/language-features/data-types/type-characters.md)显式定义要分配给的文本值 `SByte` 。</span><span class="sxs-lookup"><span data-stu-id="5de27-123">Use a [type character](../../programming-guide/language-features/data-types/type-characters.md) to explicitly define the literal value that you want to assign to the `SByte`.</span></span> <span data-ttu-id="5de27-124">下面的示例将一个负值文本 `Short` 值分配给 `SByte` 。</span><span class="sxs-lookup"><span data-stu-id="5de27-124">The following example assigns a negative literal `Short` value to an `SByte`.</span></span> <span data-ttu-id="5de27-125">请注意，对于负数，必须设置数值文本的高序位字的高阶位。</span><span class="sxs-lookup"><span data-stu-id="5de27-125">Note that, for negative numbers, the high-order bit of the high-order word of the numeric literal must be set.</span></span> <span data-ttu-id="5de27-126">对于我们的示例，此值为文本值的位 15 `Short` 。</span><span class="sxs-lookup"><span data-stu-id="5de27-126">In the case of our example, this is bit 15 of the literal `Short` value.</span></span>

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a><span data-ttu-id="5de27-127">编程提示</span><span class="sxs-lookup"><span data-stu-id="5de27-127">Programming tips</span></span>

- <span data-ttu-id="5de27-128">**CLS 遵从性。**</span><span class="sxs-lookup"><span data-stu-id="5de27-128">**CLS Compliance.**</span></span> <span data-ttu-id="5de27-129">`SByte`数据类型不是[公共语言规范](https://www.ecma-international.org/publications/standards/Ecma-335.htm)（cls）的一部分，因此符合 CLS 的代码无法使用使用它的组件。</span><span class="sxs-lookup"><span data-stu-id="5de27-129">The `SByte` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="5de27-130">**扩大.**</span><span class="sxs-lookup"><span data-stu-id="5de27-130">**Widening.**</span></span> <span data-ttu-id="5de27-131">`SByte`数据类型扩大到、、、 `Short` `Integer` `Long` `Decimal` 、 `Single` 和 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="5de27-131">The `SByte` data type widens to `Short`, `Integer`, `Long`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="5de27-132">这意味着你可以转换 `SByte` 为这些类型中的任何一种，而不会遇到 <xref:System.OverflowException?displayProperty=nameWithType> 错误。</span><span class="sxs-lookup"><span data-stu-id="5de27-132">This means you can convert `SByte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="5de27-133">**键入字符。**</span><span class="sxs-lookup"><span data-stu-id="5de27-133">**Type Characters.**</span></span> <span data-ttu-id="5de27-134">`SByte`没有文本类型字符或标识符类型字符。</span><span class="sxs-lookup"><span data-stu-id="5de27-134">`SByte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="5de27-135">**Framework 类型。**</span><span class="sxs-lookup"><span data-stu-id="5de27-135">**Framework Type.**</span></span> <span data-ttu-id="5de27-136">.NET Framework 中的对应类型是 <xref:System.SByte?displayProperty=nameWithType> 结构。</span><span class="sxs-lookup"><span data-stu-id="5de27-136">The corresponding type in the .NET Framework is the <xref:System.SByte?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="5de27-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5de27-137">See also</span></span>

- <xref:System.SByte?displayProperty=nameWithType>
- [<span data-ttu-id="5de27-138">数据类型</span><span class="sxs-lookup"><span data-stu-id="5de27-138">Data Types</span></span>](index.md)
- [<span data-ttu-id="5de27-139">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="5de27-139">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="5de27-140">转换摘要</span><span class="sxs-lookup"><span data-stu-id="5de27-140">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="5de27-141">Short 数据类型</span><span class="sxs-lookup"><span data-stu-id="5de27-141">Short Data Type</span></span>](short-data-type.md)
- [<span data-ttu-id="5de27-142">Integer 数据类型</span><span class="sxs-lookup"><span data-stu-id="5de27-142">Integer Data Type</span></span>](integer-data-type.md)
- [<span data-ttu-id="5de27-143">Long 数据类型</span><span class="sxs-lookup"><span data-stu-id="5de27-143">Long Data Type</span></span>](long-data-type.md)
- [<span data-ttu-id="5de27-144">有效使用数据类型</span><span class="sxs-lookup"><span data-stu-id="5de27-144">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)

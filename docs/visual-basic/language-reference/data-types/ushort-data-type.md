---
title: UShort 数据类型
ms.date: 01/31/2018
f1_keywords:
- vb.ushort
helpviewer_keywords:
- numbers [Visual Basic], whole
- literal type characters [Visual Basic], US
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- UShort data type
- US literal type characters [Visual Basic]
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
ms.openlocfilehash: ee31156e00059699125fd72a7f091afbb21beab0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415474"
---
# <a name="ushort-data-type-visual-basic"></a><span data-ttu-id="f8c2d-102">UShort 数据类型（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="f8c2d-102">UShort data type (Visual Basic)</span></span>

<span data-ttu-id="f8c2d-103">保存16位（2字节）无符号整数，范围介于0到65535之间。</span><span class="sxs-lookup"><span data-stu-id="f8c2d-103">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8c2d-104">备注</span><span class="sxs-lookup"><span data-stu-id="f8c2d-104">Remarks</span></span>

 <span data-ttu-id="f8c2d-105">使用 `UShort` 数据类型来包含对而言太大的二进制数据 `Byte` 。</span><span class="sxs-lookup"><span data-stu-id="f8c2d-105">Use the `UShort` data type to contain binary data too large for `Byte`.</span></span>  
  
 <span data-ttu-id="f8c2d-106">`UShort` 的默认值为 0。</span><span class="sxs-lookup"><span data-stu-id="f8c2d-106">The default value of `UShort` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="f8c2d-107">文本赋值</span><span class="sxs-lookup"><span data-stu-id="f8c2d-107">Literal assignments</span></span>

<span data-ttu-id="f8c2d-108">您可以 `UShort` 通过将变量指定为十进制文本、十六进制文本、八进制文本或（从 Visual Basic 2017）作为二进制文本来声明和初始化变量。</span><span class="sxs-lookup"><span data-stu-id="f8c2d-108">You can declare and initialize a `UShort` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="f8c2d-109">如果整数文本在 `UShort` 范围之外（即，如果它小于 <xref:System.UInt16.MinValue?displayProperty=nameWithType> 或大于 <xref:System.UInt16.MaxValue?displayProperty=nameWithType>），会发生编译错误。</span><span class="sxs-lookup"><span data-stu-id="f8c2d-109">If the integer literal is outside the range of `UShort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="f8c2d-110">在下面的示例中，表示为十进制、十六进制和二进制文本的整数等于65034，分配给 `UShort` 值。</span><span class="sxs-lookup"><span data-stu-id="f8c2d-110">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are assigned to `UShort` values.</span></span>
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> <span data-ttu-id="f8c2d-111">使用前缀 `&h` 或 `&H` 表示十六进制文本，使用前缀 `&b` 或表示 `&B` 二进制文本，使用前缀 `&o` 或 `&O` 表示八进制文本。</span><span class="sxs-lookup"><span data-stu-id="f8c2d-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="f8c2d-112">十进制文本没有前缀。</span><span class="sxs-lookup"><span data-stu-id="f8c2d-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="f8c2d-113">从 Visual Basic 2017 开始，还可以使用下划线字符 `_` 作为数字分隔符来增强可读性，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="f8c2d-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

<span data-ttu-id="f8c2d-114">从 Visual Basic 15.5 开始，还可以使用下划线字符（ `_` ）作为前缀和十六进制、二进制或八进制数字之间的前导分隔符。</span><span class="sxs-lookup"><span data-stu-id="f8c2d-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="f8c2d-115">例如：</span><span class="sxs-lookup"><span data-stu-id="f8c2d-115">For example:</span></span>

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="f8c2d-116">数字文本还可以包含 `US` 或 `us` [类型字符](../../programming-guide/language-features/data-types/type-characters.md)来表示 `UShort` 数据类型，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="f8c2d-116">Numeric literals can also include the `US` or `us` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UShort` data type, as the following example shows.</span></span>

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a><span data-ttu-id="f8c2d-117">编程提示</span><span class="sxs-lookup"><span data-stu-id="f8c2d-117">Programming tips</span></span>
  
- <span data-ttu-id="f8c2d-118">**负数。**</span><span class="sxs-lookup"><span data-stu-id="f8c2d-118">**Negative Numbers.**</span></span> <span data-ttu-id="f8c2d-119">由于 `UShort` 是一个无符号类型，因此它不能表示负数。</span><span class="sxs-lookup"><span data-stu-id="f8c2d-119">Because `UShort` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="f8c2d-120">如果 `-` 对计算结果为类型的表达式使用一元减号（）运算符 `UShort` ，Visual Basic 会将表达式转换为 `Integer` 第一个表达式。</span><span class="sxs-lookup"><span data-stu-id="f8c2d-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span></span>  
  
- <span data-ttu-id="f8c2d-121">**CLS 遵从性。**</span><span class="sxs-lookup"><span data-stu-id="f8c2d-121">**CLS Compliance.**</span></span> <span data-ttu-id="f8c2d-122">`UShort`数据类型不是[公共语言规范](https://www.ecma-international.org/publications/standards/Ecma-335.htm)（cls）的一部分，因此符合 CLS 的代码无法使用使用它的组件。</span><span class="sxs-lookup"><span data-stu-id="f8c2d-122">The `UShort` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
- <span data-ttu-id="f8c2d-123">**扩大.**</span><span class="sxs-lookup"><span data-stu-id="f8c2d-123">**Widening.**</span></span> <span data-ttu-id="f8c2d-124">`UShort`数据类型扩大到、、、 `Integer` `UInteger` 、、 `Long` `ULong` `Decimal` `Single` 和 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="f8c2d-124">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="f8c2d-125">这意味着你可以转换 `UShort` 为这些类型中的任何一种，而不会遇到 <xref:System.OverflowException?displayProperty=nameWithType> 错误。</span><span class="sxs-lookup"><span data-stu-id="f8c2d-125">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="f8c2d-126">**键入字符。**</span><span class="sxs-lookup"><span data-stu-id="f8c2d-126">**Type Characters.**</span></span> <span data-ttu-id="f8c2d-127">将文本类型字符追加 `US` 到文本会将其强制转换为 `UShort` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="f8c2d-127">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span></span> <span data-ttu-id="f8c2d-128">`UShort`没有标识符类型字符。</span><span class="sxs-lookup"><span data-stu-id="f8c2d-128">`UShort` has no identifier type character.</span></span>  
  
- <span data-ttu-id="f8c2d-129">**Framework 类型。**</span><span class="sxs-lookup"><span data-stu-id="f8c2d-129">**Framework Type.**</span></span> <span data-ttu-id="f8c2d-130">.NET Framework 中的对应类型是 <xref:System.UInt16?displayProperty=nameWithType> 结构。</span><span class="sxs-lookup"><span data-stu-id="f8c2d-130">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8c2d-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f8c2d-131">See also</span></span>

- <xref:System.UInt16>
- [<span data-ttu-id="f8c2d-132">数据类型</span><span class="sxs-lookup"><span data-stu-id="f8c2d-132">Data Types</span></span>](index.md)
- [<span data-ttu-id="f8c2d-133">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="f8c2d-133">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="f8c2d-134">转换摘要</span><span class="sxs-lookup"><span data-stu-id="f8c2d-134">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="f8c2d-135">如何：调用需要使用无符号类型的 Windows 函数</span><span class="sxs-lookup"><span data-stu-id="f8c2d-135">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="f8c2d-136">有效使用数据类型</span><span class="sxs-lookup"><span data-stu-id="f8c2d-136">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)

---
title: ULong 数据类型
ms.date: 01/31/2018
f1_keywords:
- vb.ulong
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- literal type characters [Visual Basic], UL
- ULong data type
- UL literal type characters [Visual Basic]
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
ms.openlocfilehash: ee9297ae917345d44d8e630bd09beea2245b56da
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415513"
---
# <a name="ulong-data-type-visual-basic"></a><span data-ttu-id="ecc5e-102">ULong 数据类型（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="ecc5e-102">ULong data type (Visual Basic)</span></span>

<span data-ttu-id="ecc5e-103">保留未签名的64位（8字节）整数，范围为0到18446744073709551615（超过1.84 倍 10 ^ 19）。</span><span class="sxs-lookup"><span data-stu-id="ecc5e-103">Holds unsigned 64-bit (8-byte) integers ranging in value from 0 through 18,446,744,073,709,551,615 (more than 1.84 times 10 ^ 19).</span></span>

## <a name="remarks"></a><span data-ttu-id="ecc5e-104">备注</span><span class="sxs-lookup"><span data-stu-id="ecc5e-104">Remarks</span></span>

<span data-ttu-id="ecc5e-105">使用 `ULong` 数据类型可包含太大的二进制数据 `UInteger` 或可能的最大无符号整数值。</span><span class="sxs-lookup"><span data-stu-id="ecc5e-105">Use the `ULong` data type to contain binary data too large for `UInteger`, or the largest possible unsigned integer values.</span></span>

<span data-ttu-id="ecc5e-106">`ULong` 的默认值为 0。</span><span class="sxs-lookup"><span data-stu-id="ecc5e-106">The default value of `ULong` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="ecc5e-107">文本赋值</span><span class="sxs-lookup"><span data-stu-id="ecc5e-107">Literal assignments</span></span>

<span data-ttu-id="ecc5e-108">您可以 `ULong` 通过将变量指定为十进制文本、十六进制文本、八进制文本或（从 Visual Basic 2017）作为二进制文本来声明和初始化变量。</span><span class="sxs-lookup"><span data-stu-id="ecc5e-108">You can declare and initialize a `ULong` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="ecc5e-109">如果整数文本在 `ULong` 范围之外（即，如果它小于 <xref:System.UInt64.MinValue?displayProperty=nameWithType> 或大于 <xref:System.UInt64.MaxValue?displayProperty=nameWithType>），会发生编译错误。</span><span class="sxs-lookup"><span data-stu-id="ecc5e-109">If the integer literal is outside the range of `ULong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="ecc5e-110">在以下示例中，表示为十进制、十六进制和二进制文本且等于 7,934,076,125 的整数被分配给 `ULong` 值。</span><span class="sxs-lookup"><span data-stu-id="ecc5e-110">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ULong` values.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE]
> <span data-ttu-id="ecc5e-111">使用前缀 `&h` 或 `&H` 表示十六进制文本，使用前缀 `&b` 或表示 `&B` 二进制文本，使用前缀 `&o` 或 `&O` 表示八进制文本。</span><span class="sxs-lookup"><span data-stu-id="ecc5e-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="ecc5e-112">十进制文本没有前缀。</span><span class="sxs-lookup"><span data-stu-id="ecc5e-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="ecc5e-113">从 Visual Basic 2017 开始，还可以使用下划线字符 `_` 作为数字分隔符来增强可读性，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="ecc5e-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="ecc5e-114">从 Visual Basic 15.5 开始，还可以使用下划线字符（ `_` ）作为前缀和十六进制、二进制或八进制数字之间的前导分隔符。</span><span class="sxs-lookup"><span data-stu-id="ecc5e-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="ecc5e-115">例如：</span><span class="sxs-lookup"><span data-stu-id="ecc5e-115">For example:</span></span>

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="ecc5e-116">数字文本还可以包含 `UL` 或 `ul` [类型字符](../../programming-guide/language-features/data-types/type-characters.md)来表示 `ULong` 数据类型，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="ecc5e-116">Numeric literals can also include the `UL` or `ul` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `ULong` data type, as the following example shows.</span></span>

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a><span data-ttu-id="ecc5e-117">编程提示</span><span class="sxs-lookup"><span data-stu-id="ecc5e-117">Programming tips</span></span>

- <span data-ttu-id="ecc5e-118">**负数。**</span><span class="sxs-lookup"><span data-stu-id="ecc5e-118">**Negative Numbers.**</span></span> <span data-ttu-id="ecc5e-119">由于 `ULong` 是一个无符号类型，因此它不能表示负数。</span><span class="sxs-lookup"><span data-stu-id="ecc5e-119">Because `ULong` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="ecc5e-120">如果 `-` 对计算结果为类型的表达式使用一元减号（）运算符 `ULong` ，Visual Basic 会将表达式转换为 `Decimal` 第一个表达式。</span><span class="sxs-lookup"><span data-stu-id="ecc5e-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `ULong`, Visual Basic converts the expression to `Decimal` first.</span></span>

- <span data-ttu-id="ecc5e-121">**CLS 遵从性。**</span><span class="sxs-lookup"><span data-stu-id="ecc5e-121">**CLS Compliance.**</span></span> <span data-ttu-id="ecc5e-122">`ULong`数据类型不是[公共语言规范](https://www.ecma-international.org/publications/standards/Ecma-335.htm)（cls）的一部分，因此符合 CLS 的代码无法使用使用它的组件。</span><span class="sxs-lookup"><span data-stu-id="ecc5e-122">The `ULong` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="ecc5e-123">**互操作注意事项。**</span><span class="sxs-lookup"><span data-stu-id="ecc5e-123">**Interop Considerations.**</span></span> <span data-ttu-id="ecc5e-124">如果你与不是为 .NET Framework 编写的组件（如自动化或 COM 对象）进行交互，请记住，如之类的类型 `ulong` 可以在其他环境中具有不同的数据宽度（32位）。</span><span class="sxs-lookup"><span data-stu-id="ecc5e-124">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `ulong` can have a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="ecc5e-125">如果要将32位参数传递给此类组件，请 `UInteger` `ULong` 在托管的 Visual Basic 代码中将其声明为而不是。</span><span class="sxs-lookup"><span data-stu-id="ecc5e-125">If you are passing a 32-bit argument to such a component, declare it as `UInteger` instead of `ULong` in your managed Visual Basic code.</span></span>

  <span data-ttu-id="ecc5e-126">此外，在 Windows 95、Windows 98、Windows ME 或 Windows 2000 上，自动化不支持64位整数。</span><span class="sxs-lookup"><span data-stu-id="ecc5e-126">Furthermore, Automation does not support 64-bit integers on Windows 95, Windows 98, Windows ME, or Windows 2000.</span></span> <span data-ttu-id="ecc5e-127">不能将 Visual Basic `ULong` 参数传递到这些平台上的自动化组件。</span><span class="sxs-lookup"><span data-stu-id="ecc5e-127">You cannot pass a Visual Basic `ULong` argument to an Automation component on these platforms.</span></span>

- <span data-ttu-id="ecc5e-128">**扩大.**</span><span class="sxs-lookup"><span data-stu-id="ecc5e-128">**Widening.**</span></span> <span data-ttu-id="ecc5e-129">`ULong`数据类型扩大到 `Decimal` 、 `Single` 和 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="ecc5e-129">The `ULong` data type widens to `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="ecc5e-130">这意味着你可以转换 `ULong` 为这些类型中的任何一种，而不会遇到 <xref:System.OverflowException?displayProperty=nameWithType> 错误。</span><span class="sxs-lookup"><span data-stu-id="ecc5e-130">This means you can convert `ULong` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="ecc5e-131">**键入字符。**</span><span class="sxs-lookup"><span data-stu-id="ecc5e-131">**Type Characters.**</span></span> <span data-ttu-id="ecc5e-132">将文本类型字符追加 `UL` 到文本会将其强制转换为 `ULong` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="ecc5e-132">Appending the literal type characters `UL` to a literal forces it to the `ULong` data type.</span></span> <span data-ttu-id="ecc5e-133">`ULong`没有标识符类型字符。</span><span class="sxs-lookup"><span data-stu-id="ecc5e-133">`ULong` has no identifier type character.</span></span>

- <span data-ttu-id="ecc5e-134">**Framework 类型。**</span><span class="sxs-lookup"><span data-stu-id="ecc5e-134">**Framework Type.**</span></span> <span data-ttu-id="ecc5e-135">.NET Framework 中的对应类型是 <xref:System.UInt64?displayProperty=nameWithType> 结构。</span><span class="sxs-lookup"><span data-stu-id="ecc5e-135">The corresponding type in the .NET Framework is the <xref:System.UInt64?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="ecc5e-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ecc5e-136">See also</span></span>

- <xref:System.UInt64>
- [<span data-ttu-id="ecc5e-137">数据类型</span><span class="sxs-lookup"><span data-stu-id="ecc5e-137">Data Types</span></span>](index.md)
- [<span data-ttu-id="ecc5e-138">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="ecc5e-138">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="ecc5e-139">转换摘要</span><span class="sxs-lookup"><span data-stu-id="ecc5e-139">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="ecc5e-140">如何：调用需要使用无符号类型的 Windows 函数</span><span class="sxs-lookup"><span data-stu-id="ecc5e-140">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="ecc5e-141">有效使用数据类型</span><span class="sxs-lookup"><span data-stu-id="ecc5e-141">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)

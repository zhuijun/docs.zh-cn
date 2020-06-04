---
title: Integer 数据类型
ms.date: 01/31/2018
f1_keywords:
- vb.Integer
- Integer
helpviewer_keywords:
- numbers [Visual Basic], whole
- enumerated values [Visual Basic]
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- literal type characters [Visual Basic], I
- integers [Visual Basic], types
- data types [Visual Basic], integral
- '% identifier type character'
- data types [Visual Basic], assigning
- identifier type characters [Visual Basic], %
- I literal type character [Visual Basic]
- Integer data type
ms.assetid: a8f233b4-4be3-455c-861b-05af2fbb6c60
ms.openlocfilehash: aa7b64162308d6af2763b29034c5a7276c973876
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415604"
---
# <a name="integer-data-type-visual-basic"></a><span data-ttu-id="6d6e8-102">Integer 数据类型（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="6d6e8-102">Integer data type (Visual Basic)</span></span>

<span data-ttu-id="6d6e8-103">保存 32 位（4 字节）带符号整数，值的范围为 -2,147,483,648 到 2,147,483,647。</span><span class="sxs-lookup"><span data-stu-id="6d6e8-103">Holds signed 32-bit (4-byte) integers that range in value from -2,147,483,648 through 2,147,483,647.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d6e8-104">备注</span><span class="sxs-lookup"><span data-stu-id="6d6e8-104">Remarks</span></span>

 <span data-ttu-id="6d6e8-105">`Integer` 数据类型为 32 位处理器提供了优化性能。</span><span class="sxs-lookup"><span data-stu-id="6d6e8-105">The `Integer` data type provides optimal performance on a 32-bit processor.</span></span> <span data-ttu-id="6d6e8-106">其他整数类型在内存中的加载和存储的速度都要稍慢一些。</span><span class="sxs-lookup"><span data-stu-id="6d6e8-106">The other integral types are slower to load and store from and to memory.</span></span>  
  
 <span data-ttu-id="6d6e8-107">`Integer` 的默认值为 0。</span><span class="sxs-lookup"><span data-stu-id="6d6e8-107">The default value of `Integer` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="6d6e8-108">文本赋值</span><span class="sxs-lookup"><span data-stu-id="6d6e8-108">Literal assignments</span></span>

<span data-ttu-id="6d6e8-109">可以 `Integer` 通过将变量指定为十进制文本、十六进制文本、八进制文本或（从 Visual Basic 2017）作为二进制文本来声明和初始化变量。</span><span class="sxs-lookup"><span data-stu-id="6d6e8-109">You can declare and initialize an `Integer` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="6d6e8-110">如果整数文本在 `Integer` 范围之外（即，如果它小于 <xref:System.Int32.MinValue?displayProperty=nameWithType> 或大于 <xref:System.Int32.MaxValue?displayProperty=nameWithType>），会发生编译错误。</span><span class="sxs-lookup"><span data-stu-id="6d6e8-110">If the integer literal is outside the range of `Integer` (that is, if it is less than <xref:System.Int32.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="6d6e8-111">在以下示例中，表示为十进制、十六进制和二进制文本且等于 90,946 的整数被分配给 `Integer` 值。</span><span class="sxs-lookup"><span data-stu-id="6d6e8-111">In the following example, integers equal to 90,946 that are represented as decimal, hexadecimal, and binary literals are assigned to `Integer` values.</span></span>

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> <span data-ttu-id="6d6e8-112">使用前缀 `&h` 或 `&H` 表示十六进制文本，使用前缀 `&b` 或表示 `&B` 二进制文本，使用前缀 `&o` 或 `&O` 表示八进制文本。</span><span class="sxs-lookup"><span data-stu-id="6d6e8-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="6d6e8-113">十进制文本没有前缀。</span><span class="sxs-lookup"><span data-stu-id="6d6e8-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="6d6e8-114">从 Visual Basic 2017 开始，还可以使用下划线字符 `_` 作为数字分隔符来增强可读性，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="6d6e8-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

<span data-ttu-id="6d6e8-115">从 Visual Basic 15.5 开始，还可以使用下划线字符（ `_` ）作为前缀和十六进制、二进制或八进制数字之间的前导分隔符。</span><span class="sxs-lookup"><span data-stu-id="6d6e8-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="6d6e8-116">例如：</span><span class="sxs-lookup"><span data-stu-id="6d6e8-116">For example:</span></span>

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="6d6e8-117">数字文本还可包含 `I` 用于表示数据类型的[类型字符](../../programming-guide/language-features/data-types/type-characters.md) `Integer` ，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="6d6e8-117">Numeric literals can also include the `I` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Integer` data type, as the following example shows.</span></span>

```vb
Dim number = &H_035826I
```

## <a name="programming-tips"></a><span data-ttu-id="6d6e8-118">编程提示</span><span class="sxs-lookup"><span data-stu-id="6d6e8-118">Programming tips</span></span>

- <span data-ttu-id="6d6e8-119">**互操作注意事项。**</span><span class="sxs-lookup"><span data-stu-id="6d6e8-119">**Interop Considerations.**</span></span> <span data-ttu-id="6d6e8-120">如果与不是为 .NET Framework 编写的组件（如自动化或 COM 对象）交互，请记住， `Integer` 在其他环境中具有不同的数据宽度（16位）。</span><span class="sxs-lookup"><span data-stu-id="6d6e8-120">If you are interfacing with components not written for the .NET Framework, such as Automation or COM objects, remember that `Integer` has a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="6d6e8-121">如果将一个 16 位自变量传递给此类组件，请在新的 Visual Basic 代码中将其声明为 `Short` 而不是 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="6d6e8-121">If you are passing a 16-bit argument to such a component, declare it as `Short` instead of `Integer` in your new Visual Basic code.</span></span>  
  
- <span data-ttu-id="6d6e8-122">**扩大.**</span><span class="sxs-lookup"><span data-stu-id="6d6e8-122">**Widening.**</span></span> <span data-ttu-id="6d6e8-123">`Integer` 数据类型加宽到 `Long`、`Decimal`、`Single` 或 `Double`。</span><span class="sxs-lookup"><span data-stu-id="6d6e8-123">The `Integer` data type widens to `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="6d6e8-124">这意味着，你可以将 `Integer` 转换为这些类型中的任意类型，而不会遇到 <xref:System.OverflowException?displayProperty=nameWithType> 错误。</span><span class="sxs-lookup"><span data-stu-id="6d6e8-124">This means you can convert `Integer` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="6d6e8-125">**键入字符。**</span><span class="sxs-lookup"><span data-stu-id="6d6e8-125">**Type Characters.**</span></span> <span data-ttu-id="6d6e8-126">将文本类型字符 `I` 追加到文本会将其强制转换为 `Integer` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="6d6e8-126">Appending the literal type character `I` to a literal forces it to the `Integer` data type.</span></span> <span data-ttu-id="6d6e8-127">将标识符类型字符 `%` 追加到任何标识符会将其强制转换为 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="6d6e8-127">Appending the identifier type character `%` to any identifier forces it to `Integer`.</span></span>  
  
- <span data-ttu-id="6d6e8-128">**Framework 类型。**</span><span class="sxs-lookup"><span data-stu-id="6d6e8-128">**Framework Type.**</span></span> <span data-ttu-id="6d6e8-129">.NET Framework 中的对应类型是 <xref:System.Int32?displayProperty=nameWithType> 结构。</span><span class="sxs-lookup"><span data-stu-id="6d6e8-129">The corresponding type in the .NET Framework is the <xref:System.Int32?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="range"></a><span data-ttu-id="6d6e8-130">范围</span><span class="sxs-lookup"><span data-stu-id="6d6e8-130">Range</span></span>

<span data-ttu-id="6d6e8-131">如果尝试将整型变量设置为其类型范围以外的数字，则将出错。</span><span class="sxs-lookup"><span data-stu-id="6d6e8-131">If you try to set a variable of an integral type to a number outside the range for that type, an error occurs.</span></span> <span data-ttu-id="6d6e8-132">如果尝试将其设置为小数，则数字将向上或向下舍入为最接近的整数值。</span><span class="sxs-lookup"><span data-stu-id="6d6e8-132">If you try to set it to a fraction, the number is rounded up or down to the nearest integer value.</span></span> <span data-ttu-id="6d6e8-133">如果数字同样接近两个整数值，则值将舍入为最接近的偶数整数。</span><span class="sxs-lookup"><span data-stu-id="6d6e8-133">If the number is equally close to two integer values, the value is rounded to the nearest even integer.</span></span> <span data-ttu-id="6d6e8-134">这种做法可将因单方向持续舍入中点值而导致的舍入误差降到最低。</span><span class="sxs-lookup"><span data-stu-id="6d6e8-134">This behavior minimizes rounding errors that result from consistently rounding a midpoint value in a single direction.</span></span> <span data-ttu-id="6d6e8-135">下面的代码演示了舍入的示例。</span><span class="sxs-lookup"><span data-stu-id="6d6e8-135">The following code shows examples of rounding.</span></span>  

```vb  
' The valid range of an Integer variable is -2147483648 through +2147483647.  
Dim k As Integer  
' The following statement causes an error because the value is too large.  
k = 2147483648  
' The following statement sets k to 6.  
k = 5.9  
' The following statement sets k to 4  
k = 4.5  
' The following statement sets k to 6  
' Note, Visual Basic uses banker’s rounding (toward nearest even number)  
k = 5.5  
```

## <a name="see-also"></a><span data-ttu-id="6d6e8-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6d6e8-136">See also</span></span>

- <xref:System.Int32?displayProperty=nameWithType>
- [<span data-ttu-id="6d6e8-137">数据类型</span><span class="sxs-lookup"><span data-stu-id="6d6e8-137">Data Types</span></span>](index.md)
- [<span data-ttu-id="6d6e8-138">Long 数据类型</span><span class="sxs-lookup"><span data-stu-id="6d6e8-138">Long Data Type</span></span>](long-data-type.md)
- [<span data-ttu-id="6d6e8-139">Short 数据类型</span><span class="sxs-lookup"><span data-stu-id="6d6e8-139">Short Data Type</span></span>](short-data-type.md)
- [<span data-ttu-id="6d6e8-140">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="6d6e8-140">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="6d6e8-141">转换摘要</span><span class="sxs-lookup"><span data-stu-id="6d6e8-141">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="6d6e8-142">有效使用数据类型</span><span class="sxs-lookup"><span data-stu-id="6d6e8-142">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)

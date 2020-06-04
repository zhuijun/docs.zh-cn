---
title: Short 数据类型
ms.date: 01/31/2018
f1_keywords:
- vb.Short
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- S literal type character [Visual Basic]
- Short data type
- literal type characters [Visual Basic], S
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
ms.openlocfilehash: 176d27c86127dac1d9c9c0231790f7a5c2a2fefc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415552"
---
# <a name="short-data-type-visual-basic"></a><span data-ttu-id="6c1b9-102">Short 数据类型（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="6c1b9-102">Short data type (Visual Basic)</span></span>

<span data-ttu-id="6c1b9-103">保存16位有符号整数，其值范围从-32768 到32767。</span><span class="sxs-lookup"><span data-stu-id="6c1b9-103">Holds signed 16-bit (2-byte) integers that range in value from -32,768 through 32,767.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c1b9-104">备注</span><span class="sxs-lookup"><span data-stu-id="6c1b9-104">Remarks</span></span>  

 <span data-ttu-id="6c1b9-105">使用 `Short` 数据类型可包含不需要完整数据宽度的整数值 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="6c1b9-105">Use the `Short` data type to contain integer values that do not require the full data width of `Integer`.</span></span> <span data-ttu-id="6c1b9-106">在某些情况下，公共语言运行时可以将 `Short` 变量紧密地打包在一起，并节省内存消耗。</span><span class="sxs-lookup"><span data-stu-id="6c1b9-106">In some cases, the common language runtime can pack your `Short` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="6c1b9-107">`Short` 的默认值为 0。</span><span class="sxs-lookup"><span data-stu-id="6c1b9-107">The default value of `Short` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="6c1b9-108">文本赋值</span><span class="sxs-lookup"><span data-stu-id="6c1b9-108">Literal assignments</span></span>

<span data-ttu-id="6c1b9-109">您可以 `Short` 通过将变量指定为十进制文本、十六进制文本、八进制文本或（从 Visual Basic 2017）作为二进制文本来声明和初始化变量。</span><span class="sxs-lookup"><span data-stu-id="6c1b9-109">You can declare and initialize a `Short` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="6c1b9-110">如果整数文本在 `Short` 范围之外（即，如果它小于 <xref:System.Int16.MinValue?displayProperty=nameWithType> 或大于 <xref:System.Int16.MaxValue?displayProperty=nameWithType>），会发生编译错误。</span><span class="sxs-lookup"><span data-stu-id="6c1b9-110">If the integer literal is outside the range of `Short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="6c1b9-111">在下面的示例中，表示为十进制、十六进制和二进制文本的整数等于1034将从[整数](integer-data-type.md)隐式转换为 `Short` 值。</span><span class="sxs-lookup"><span data-stu-id="6c1b9-111">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `Short` values.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> <span data-ttu-id="6c1b9-112">使用前缀 `&h` 或 `&H` 表示十六进制文本，使用前缀 `&b` 或表示 `&B` 二进制文本，使用前缀 `&o` 或 `&O` 表示八进制文本。</span><span class="sxs-lookup"><span data-stu-id="6c1b9-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="6c1b9-113">十进制文本没有前缀。</span><span class="sxs-lookup"><span data-stu-id="6c1b9-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="6c1b9-114">从 Visual Basic 2017 开始，还可以使用下划线字符 `_` 作为数字分隔符来增强可读性，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="6c1b9-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

<span data-ttu-id="6c1b9-115">从 Visual Basic 15.5 开始，还可以使用下划线字符（ `_` ）作为前缀和十六进制、二进制或八进制数字之间的前导分隔符。</span><span class="sxs-lookup"><span data-stu-id="6c1b9-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="6c1b9-116">例如：</span><span class="sxs-lookup"><span data-stu-id="6c1b9-116">For example:</span></span>

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="6c1b9-117">数字文本还可包含 `S` 用于表示数据类型的[类型字符](../../programming-guide/language-features/data-types/type-characters.md) `Short` ，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="6c1b9-117">Numeric literals can also include the `S` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Short` data type, as the following example shows.</span></span>

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a><span data-ttu-id="6c1b9-118">编程提示</span><span class="sxs-lookup"><span data-stu-id="6c1b9-118">Programming tips</span></span>

- <span data-ttu-id="6c1b9-119">**扩大.**</span><span class="sxs-lookup"><span data-stu-id="6c1b9-119">**Widening.**</span></span> <span data-ttu-id="6c1b9-120">`Short`数据类型扩大到、、、 `Integer` `Long` `Decimal` `Single` 或 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="6c1b9-120">The `Short` data type widens to `Integer`, `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="6c1b9-121">这意味着，你可以将 `Short` 转换为这些类型中的任意类型，而不会遇到 <xref:System.OverflowException?displayProperty=nameWithType> 错误。</span><span class="sxs-lookup"><span data-stu-id="6c1b9-121">This means you can convert `Short` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="6c1b9-122">**键入字符。**</span><span class="sxs-lookup"><span data-stu-id="6c1b9-122">**Type Characters.**</span></span> <span data-ttu-id="6c1b9-123">将文本类型字符 `S` 追加到文本会将其强制转换为 `Short` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="6c1b9-123">Appending the literal type character `S` to a literal forces it to the `Short` data type.</span></span> <span data-ttu-id="6c1b9-124">`Short`没有标识符类型字符。</span><span class="sxs-lookup"><span data-stu-id="6c1b9-124">`Short` has no identifier type character.</span></span>  
  
- <span data-ttu-id="6c1b9-125">**Framework 类型。**</span><span class="sxs-lookup"><span data-stu-id="6c1b9-125">**Framework Type.**</span></span> <span data-ttu-id="6c1b9-126">.NET Framework 中的对应类型是 <xref:System.Int16?displayProperty=nameWithType> 结构。</span><span class="sxs-lookup"><span data-stu-id="6c1b9-126">The corresponding type in the .NET Framework is the <xref:System.Int16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c1b9-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6c1b9-127">See also</span></span>

- <xref:System.Int16?displayProperty=nameWithType>
- [<span data-ttu-id="6c1b9-128">数据类型</span><span class="sxs-lookup"><span data-stu-id="6c1b9-128">Data Types</span></span>](index.md)
- [<span data-ttu-id="6c1b9-129">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="6c1b9-129">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="6c1b9-130">转换摘要</span><span class="sxs-lookup"><span data-stu-id="6c1b9-130">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="6c1b9-131">Integer 数据类型</span><span class="sxs-lookup"><span data-stu-id="6c1b9-131">Integer Data Type</span></span>](integer-data-type.md)
- [<span data-ttu-id="6c1b9-132">Long 数据类型</span><span class="sxs-lookup"><span data-stu-id="6c1b9-132">Long Data Type</span></span>](long-data-type.md)
- [<span data-ttu-id="6c1b9-133">有效使用数据类型</span><span class="sxs-lookup"><span data-stu-id="6c1b9-133">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)

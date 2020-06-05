---
title: Char 数据类型
ms.date: 07/20/2015
f1_keywords:
- vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
ms.openlocfilehash: 3dbbf9f6a2c4079775e05f5d2dcd8704c1ec4259
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387473"
---
# <a name="char-data-type-visual-basic"></a><span data-ttu-id="0a2da-102">Char 数据类型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a2da-102">Char Data Type (Visual Basic)</span></span>

<span data-ttu-id="0a2da-103">保存16位（2字节）无符号码位，范围介于0到65535之间。</span><span class="sxs-lookup"><span data-stu-id="0a2da-103">Holds unsigned 16-bit (2-byte) code points ranging in value from 0 through 65535.</span></span> <span data-ttu-id="0a2da-104">每个*码位*或字符代码都表示一个 Unicode 字符。</span><span class="sxs-lookup"><span data-stu-id="0a2da-104">Each *code point*, or character code, represents a single Unicode character.</span></span>

## <a name="remarks"></a><span data-ttu-id="0a2da-105">备注</span><span class="sxs-lookup"><span data-stu-id="0a2da-105">Remarks</span></span>

<span data-ttu-id="0a2da-106">`Char`当需要仅保存单个字符且无需开销时，请使用数据类型 `String` 。</span><span class="sxs-lookup"><span data-stu-id="0a2da-106">Use the `Char` data type when you need to hold only a single character and do not need the overhead of `String`.</span></span> <span data-ttu-id="0a2da-107">在某些情况下，可以使用 `Char()` （元素数组 `Char` ）保存多个字符。</span><span class="sxs-lookup"><span data-stu-id="0a2da-107">In some cases you can use `Char()`, an array of `Char` elements, to hold multiple characters.</span></span>

<span data-ttu-id="0a2da-108">的默认值 `Char` 为码位为0的字符。</span><span class="sxs-lookup"><span data-stu-id="0a2da-108">The default value of `Char` is the character with a code point of 0.</span></span>

## <a name="unicode-characters"></a><span data-ttu-id="0a2da-109">Unicode 字符</span><span class="sxs-lookup"><span data-stu-id="0a2da-109">Unicode Characters</span></span>

<span data-ttu-id="0a2da-110">Unicode 的第一个128码位（0–127）对应于标准美式键盘上的字母和符号。</span><span class="sxs-lookup"><span data-stu-id="0a2da-110">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="0a2da-111">这前128码位与 ASCII 字符集定义的代码点相同。</span><span class="sxs-lookup"><span data-stu-id="0a2da-111">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="0a2da-112">第二个128码位（128–255）表示特殊字符，例如基于拉丁语的字母表号、重音、货币符号和分数。</span><span class="sxs-lookup"><span data-stu-id="0a2da-112">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="0a2da-113">Unicode 对各种符号（包括全球文本字符、音调符号和数学符号和技术符号）使用剩余的代码点（256-65535）。</span><span class="sxs-lookup"><span data-stu-id="0a2da-113">Unicode uses the remaining code points (256-65535) for a wide variety of symbols, including worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>

<span data-ttu-id="0a2da-114">您可以对变量使用 <xref:System.Char.IsDigit%2A> 和等方法 <xref:System.Char.IsPunctuation%2A> `Char` 来确定其 Unicode 分类。</span><span class="sxs-lookup"><span data-stu-id="0a2da-114">You can use methods like <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on a `Char` variable to determine its Unicode classification.</span></span>

## <a name="type-conversions"></a><span data-ttu-id="0a2da-115">类型转换</span><span class="sxs-lookup"><span data-stu-id="0a2da-115">Type Conversions</span></span>

<span data-ttu-id="0a2da-116">Visual Basic 不会直接在 `Char` 和数值类型之间转换。</span><span class="sxs-lookup"><span data-stu-id="0a2da-116">Visual Basic does not convert directly between `Char` and the numeric types.</span></span> <span data-ttu-id="0a2da-117">您可以使用 <xref:Microsoft.VisualBasic.Strings.Asc%2A> 或 <xref:Microsoft.VisualBasic.Strings.AscW%2A> 函数将 `Char` 值转换为 `Integer` 表示其码位的。</span><span class="sxs-lookup"><span data-stu-id="0a2da-117">You can use the <xref:Microsoft.VisualBasic.Strings.Asc%2A> or <xref:Microsoft.VisualBasic.Strings.AscW%2A> function to convert a `Char` value to an `Integer` that represents its code point.</span></span> <span data-ttu-id="0a2da-118">您可以使用 <xref:Microsoft.VisualBasic.Strings.Chr%2A> 或 <xref:Microsoft.VisualBasic.Strings.ChrW%2A> 函数将 `Integer` 值转换为 `Char` 具有该码位的。</span><span class="sxs-lookup"><span data-stu-id="0a2da-118">You can use the <xref:Microsoft.VisualBasic.Strings.Chr%2A> or <xref:Microsoft.VisualBasic.Strings.ChrW%2A> function to convert an `Integer` value to a `Char` that has that code point.</span></span>

<span data-ttu-id="0a2da-119">如果类型检查开关（ [Option Strict 语句](../statements/option-strict-statement.md)）为 on，则必须将文本类型字符追加到单字符字符串文本中，以将其标识为 `Char` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="0a2da-119">If the type checking switch (the [Option Strict Statement](../statements/option-strict-statement.md)) is on, you must append the literal type character to a single-character string literal to identify it as the `Char` data type.</span></span> <span data-ttu-id="0a2da-120">下面的示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="0a2da-120">The following example illustrates this.</span></span> <span data-ttu-id="0a2da-121">对变量的第一次赋值将 `charVar` 生成编译器错误[BC30512](../../misc/bc30512.md) ，因为 `Option Strict` 处于打开。</span><span class="sxs-lookup"><span data-stu-id="0a2da-121">The first assignment to the `charVar` variable generates compiler error [BC30512](../../misc/bc30512.md) because `Option Strict` is on.</span></span> <span data-ttu-id="0a2da-122">第二个编译成功，因为 `c` 文本类型字符将文本标识为 `Char` 值。</span><span class="sxs-lookup"><span data-stu-id="0a2da-122">The second compiles successfully because the `c` literal type character identifies the literal as a `Char` value.</span></span>

```vb
Option Strict On

Module CharType
    Public Sub Main()
        Dim charVar As Char

        ' This statement generates compiler error BC30512 because Option Strict is On.  
        charVar = "Z"  

        ' The following statement succeeds because it specifies a Char literal.  
        charVar = "Z"c
    End Sub
End Module
```

## <a name="programming-tips"></a><span data-ttu-id="0a2da-123">编程提示</span><span class="sxs-lookup"><span data-stu-id="0a2da-123">Programming Tips</span></span>

- <span data-ttu-id="0a2da-124">**负数。**</span><span class="sxs-lookup"><span data-stu-id="0a2da-124">**Negative Numbers.**</span></span> <span data-ttu-id="0a2da-125">`Char`是无符号类型，不能表示负值。</span><span class="sxs-lookup"><span data-stu-id="0a2da-125">`Char` is an unsigned type and cannot represent a negative value.</span></span> <span data-ttu-id="0a2da-126">在任何情况下，不应使用 `Char` 来保存数值。</span><span class="sxs-lookup"><span data-stu-id="0a2da-126">In any case, you should not use `Char` to hold numeric values.</span></span>

- <span data-ttu-id="0a2da-127">**互操作注意事项。**</span><span class="sxs-lookup"><span data-stu-id="0a2da-127">**Interop Considerations.**</span></span> <span data-ttu-id="0a2da-128">如果你使用不是为 .NET Framework 编写的组件（如自动化或 COM 对象）进行交互，请记住，在其他环境中字符类型具有不同的数据宽度（8位）。</span><span class="sxs-lookup"><span data-stu-id="0a2da-128">If you interface with components not written for the .NET Framework, for example Automation or COM objects, remember that character types have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="0a2da-129">如果将一个8位参数传递给此类组件，请 `Byte` `Char` 在新的 Visual Basic 代码中将其声明为而不是。</span><span class="sxs-lookup"><span data-stu-id="0a2da-129">If you pass an 8-bit argument to such a component, declare it as `Byte` instead of `Char` in your new Visual Basic code.</span></span>

- <span data-ttu-id="0a2da-130">**扩大.**</span><span class="sxs-lookup"><span data-stu-id="0a2da-130">**Widening.**</span></span> <span data-ttu-id="0a2da-131">`Char`数据类型扩大到 `String` 。</span><span class="sxs-lookup"><span data-stu-id="0a2da-131">The `Char` data type widens to `String`.</span></span> <span data-ttu-id="0a2da-132">这意味着你可以将转换 `Char` 为 `String` ，而不会遇到 <xref:System.OverflowException?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="0a2da-132">This means you can convert `Char` to `String` and will not encounter a <xref:System.OverflowException?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="0a2da-133">**键入字符。**</span><span class="sxs-lookup"><span data-stu-id="0a2da-133">**Type Characters.**</span></span> <span data-ttu-id="0a2da-134">将文本类型字符追加 `C` 到单字符字符串文本会将其强制转换为 `Char` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="0a2da-134">Appending the literal type character `C` to a single-character string literal forces it to the `Char` data type.</span></span> <span data-ttu-id="0a2da-135">`Char`没有标识符类型字符。</span><span class="sxs-lookup"><span data-stu-id="0a2da-135">`Char` has no identifier type character.</span></span>

- <span data-ttu-id="0a2da-136">**Framework 类型。**</span><span class="sxs-lookup"><span data-stu-id="0a2da-136">**Framework Type.**</span></span> <span data-ttu-id="0a2da-137">.NET Framework 中的对应类型是 <xref:System.Char?displayProperty=nameWithType> 结构。</span><span class="sxs-lookup"><span data-stu-id="0a2da-137">The corresponding type in the .NET Framework is the <xref:System.Char?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a2da-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0a2da-138">See also</span></span>

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="0a2da-139">数据类型</span><span class="sxs-lookup"><span data-stu-id="0a2da-139">Data Types</span></span>](index.md)
- [<span data-ttu-id="0a2da-140">String 数据类型</span><span class="sxs-lookup"><span data-stu-id="0a2da-140">String Data Type</span></span>](string-data-type.md)
- [<span data-ttu-id="0a2da-141">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="0a2da-141">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="0a2da-142">转换摘要</span><span class="sxs-lookup"><span data-stu-id="0a2da-142">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="0a2da-143">如何：调用需要使用无符号类型的 Windows 函数</span><span class="sxs-lookup"><span data-stu-id="0a2da-143">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="0a2da-144">有效使用数据类型</span><span class="sxs-lookup"><span data-stu-id="0a2da-144">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)

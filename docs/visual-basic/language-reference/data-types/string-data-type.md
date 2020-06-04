---
title: String 数据类型
ms.date: 07/20/2015
f1_keywords:
- vb.String
helpviewer_keywords:
- strings [Visual Basic], character
- strings [Visual Basic], fixed-length
- string keyword [Visual Basic]
- fixed-length strings [Visual Basic], string data type
- literals [Visual Basic], string
- text [Visual Basic], String data type
- $ identifier type character
- String data type
- fixed-length strings
- string literals [Visual Basic]
- data types [Visual Basic], assigning
- String literals [Visual Basic]
- identifier type characters [Visual Basic], $
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
ms.openlocfilehash: cd4b64c101ae56928e84a04649e49c17b6f4023c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415500"
---
# <a name="string-data-type-visual-basic"></a><span data-ttu-id="4891f-102">String 数据类型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4891f-102">String Data Type (Visual Basic)</span></span>

<span data-ttu-id="4891f-103">保存范围介于0到65535之间的16位无符号16位（2字节）码位序列。</span><span class="sxs-lookup"><span data-stu-id="4891f-103">Holds sequences of unsigned 16-bit (2-byte) code points that range in value from 0 through 65535.</span></span> <span data-ttu-id="4891f-104">每个*码位*或字符代码都表示一个 Unicode 字符。</span><span class="sxs-lookup"><span data-stu-id="4891f-104">Each *code point*, or character code, represents a single Unicode character.</span></span> <span data-ttu-id="4891f-105">字符串可以包含0到约2000000000（2 ^ 31）个 Unicode 字符。</span><span class="sxs-lookup"><span data-stu-id="4891f-105">A string can contain from 0 to approximately two billion (2 ^ 31) Unicode characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4891f-106">备注</span><span class="sxs-lookup"><span data-stu-id="4891f-106">Remarks</span></span>  

 <span data-ttu-id="4891f-107">使用 `String` 数据类型来存储多个字符，而无需数组管理开销 `Char()` ，即 `Char` 元素数组。</span><span class="sxs-lookup"><span data-stu-id="4891f-107">Use the `String` data type to hold multiple characters without the array management overhead of `Char()`, an array of `Char` elements.</span></span>  
  
 <span data-ttu-id="4891f-108">的默认值 `String` 为 `Nothing` （空引用）。</span><span class="sxs-lookup"><span data-stu-id="4891f-108">The default value of `String` is `Nothing` (a null reference).</span></span> <span data-ttu-id="4891f-109">请注意，这与空字符串（值 `""` ）不同。</span><span class="sxs-lookup"><span data-stu-id="4891f-109">Note that this is not the same as the empty string (value `""`).</span></span>  
  
## <a name="unicode-characters"></a><span data-ttu-id="4891f-110">Unicode 字符</span><span class="sxs-lookup"><span data-stu-id="4891f-110">Unicode Characters</span></span>  

 <span data-ttu-id="4891f-111">Unicode 的第一个128码位（0–127）对应于标准美式键盘上的字母和符号。</span><span class="sxs-lookup"><span data-stu-id="4891f-111">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="4891f-112">这前128码位与 ASCII 字符集定义的代码点相同。</span><span class="sxs-lookup"><span data-stu-id="4891f-112">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="4891f-113">第二个128码位（128–255）表示特殊字符，例如基于拉丁语的字母表号、重音、货币符号和分数。</span><span class="sxs-lookup"><span data-stu-id="4891f-113">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="4891f-114">Unicode 对各种符号使用剩余的代码点（256-65535）。</span><span class="sxs-lookup"><span data-stu-id="4891f-114">Unicode uses the remaining code points (256-65535) for a wide variety of symbols.</span></span> <span data-ttu-id="4891f-115">这包括全球文本字符、音调符号、数学和技术符号。</span><span class="sxs-lookup"><span data-stu-id="4891f-115">This includes worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>  
  
 <span data-ttu-id="4891f-116">可以在 <xref:System.Char.IsDigit%2A> <xref:System.Char.IsPunctuation%2A> 变量中的单个字符上使用和等方法 `String` 来确定其 Unicode 分类。</span><span class="sxs-lookup"><span data-stu-id="4891f-116">You can use methods such as <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on an individual character in a `String` variable to determine its Unicode classification.</span></span>  
  
## <a name="format-requirements"></a><span data-ttu-id="4891f-117">格式要求</span><span class="sxs-lookup"><span data-stu-id="4891f-117">Format Requirements</span></span>  

 <span data-ttu-id="4891f-118">必须将文本括 `String` 在引号（）中 `" "` 。</span><span class="sxs-lookup"><span data-stu-id="4891f-118">You must enclose a `String` literal within quotation marks (`" "`).</span></span> <span data-ttu-id="4891f-119">如果必须将引号作为字符串中的一个字符包含，请使用两个连续的引号（ `""` ）。</span><span class="sxs-lookup"><span data-stu-id="4891f-119">If you must include a quotation mark as one of the characters in the string, you use two contiguous quotation marks (`""`).</span></span> <span data-ttu-id="4891f-120">下面的示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="4891f-120">The following example illustrates this.</span></span>  
  
```vb  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 <span data-ttu-id="4891f-121">请注意，表示字符串中的引号的连续引号与开始和结束文本的引号无关 `String` 。</span><span class="sxs-lookup"><span data-stu-id="4891f-121">Note that the contiguous quotation marks that represent a quotation mark in the string are independent of the quotation marks that begin and end the `String` literal.</span></span>  
  
## <a name="string-manipulations"></a><span data-ttu-id="4891f-122">字符串操作</span><span class="sxs-lookup"><span data-stu-id="4891f-122">String Manipulations</span></span>  

 <span data-ttu-id="4891f-123">将字符串分配给变量后， `String` 该字符串是*不可变*的，这意味着你无法更改其长度或内容。</span><span class="sxs-lookup"><span data-stu-id="4891f-123">Once you assign a string to a `String` variable, that string is *immutable*, which means you cannot change its length or contents.</span></span> <span data-ttu-id="4891f-124">以任何方式更改字符串时，Visual Basic 会创建一个新字符串，并放弃上一个字符串。</span><span class="sxs-lookup"><span data-stu-id="4891f-124">When you alter a string in any way, Visual Basic creates a new string and abandons the previous one.</span></span> <span data-ttu-id="4891f-125">然后，该 `String` 变量指向新的字符串。</span><span class="sxs-lookup"><span data-stu-id="4891f-125">The `String` variable then points to the new string.</span></span>  
  
 <span data-ttu-id="4891f-126">您可以 `String` 使用各种字符串函数来处理变量的内容。</span><span class="sxs-lookup"><span data-stu-id="4891f-126">You can manipulate the contents of a `String` variable by using a variety of string functions.</span></span> <span data-ttu-id="4891f-127">下面的示例阐释了 <xref:Microsoft.VisualBasic.Strings.Left%2A> 函数</span><span class="sxs-lookup"><span data-stu-id="4891f-127">The following example illustrates the <xref:Microsoft.VisualBasic.Strings.Left%2A> function</span></span>  
  
```vb  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 <span data-ttu-id="4891f-128">其他组件创建的字符串可能用前导空格或尾随空格填充。</span><span class="sxs-lookup"><span data-stu-id="4891f-128">A string created by another component might be padded with leading or trailing spaces.</span></span> <span data-ttu-id="4891f-129">如果收到这样的字符串，可以使用 <xref:Microsoft.VisualBasic.Strings.Trim%2A> 、 <xref:Microsoft.VisualBasic.Strings.LTrim%2A> 和 <xref:Microsoft.VisualBasic.Strings.RTrim%2A> 函数来删除这些空格。</span><span class="sxs-lookup"><span data-stu-id="4891f-129">If you receive such a string, you can use the <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, and <xref:Microsoft.VisualBasic.Strings.RTrim%2A> functions to remove these spaces.</span></span>  
  
 <span data-ttu-id="4891f-130">有关字符串操作的详细信息，请参阅[字符串](../../programming-guide/language-features/strings/index.md)。</span><span class="sxs-lookup"><span data-stu-id="4891f-130">For more information about string manipulations, see [Strings](../../programming-guide/language-features/strings/index.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="4891f-131">编程提示</span><span class="sxs-lookup"><span data-stu-id="4891f-131">Programming Tips</span></span>  
  
- <span data-ttu-id="4891f-132">**负数。**</span><span class="sxs-lookup"><span data-stu-id="4891f-132">**Negative Numbers.**</span></span> <span data-ttu-id="4891f-133">请记住，保留的字符 `String` 是无符号的，不能表示负值。</span><span class="sxs-lookup"><span data-stu-id="4891f-133">Remember that the characters held by `String` are unsigned and cannot represent negative values.</span></span> <span data-ttu-id="4891f-134">在任何情况下，不应使用 `String` 来保存数值。</span><span class="sxs-lookup"><span data-stu-id="4891f-134">In any case, you should not use `String` to hold numeric values.</span></span>  
  
- <span data-ttu-id="4891f-135">**互操作注意事项。**</span><span class="sxs-lookup"><span data-stu-id="4891f-135">**Interop Considerations.**</span></span> <span data-ttu-id="4891f-136">如果你与不是为 .NET Framework 编写的组件（如自动化或 COM 对象）进行交互，请记住，在其他环境中，字符串字符具有不同的数据宽度（8位）。</span><span class="sxs-lookup"><span data-stu-id="4891f-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that string characters have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="4891f-137">如果将8位字符的字符串参数传递给此类组件，则将其声明为 `Byte()` 元素数组， `Byte` 而不是 `String` 新的 Visual Basic 代码。</span><span class="sxs-lookup"><span data-stu-id="4891f-137">If you are passing a string argument of 8-bit characters to such a component, declare it as `Byte()`, an array of `Byte` elements, instead of `String` in your new Visual Basic code.</span></span>  
  
- <span data-ttu-id="4891f-138">**键入字符。**</span><span class="sxs-lookup"><span data-stu-id="4891f-138">**Type Characters.**</span></span> <span data-ttu-id="4891f-139">如果将标识符类型字符追加 `$` 到任何标识符，则会将其强制转换为 `String` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="4891f-139">Appending the identifier type character `$` to any identifier forces it to the `String` data type.</span></span> <span data-ttu-id="4891f-140">`String`没有文本类型字符。</span><span class="sxs-lookup"><span data-stu-id="4891f-140">`String` has no literal type character.</span></span> <span data-ttu-id="4891f-141">但编译器会将括在引号（）中的文本视为 `" "` `String` 。</span><span class="sxs-lookup"><span data-stu-id="4891f-141">However, the compiler treats literals enclosed in quotation marks (`" "`) as `String`.</span></span>  
  
- <span data-ttu-id="4891f-142">**Framework 类型。**</span><span class="sxs-lookup"><span data-stu-id="4891f-142">**Framework Type.**</span></span> <span data-ttu-id="4891f-143">.NET Framework 中的相应类型是 <xref:System.String?displayProperty=nameWithType> 类。</span><span class="sxs-lookup"><span data-stu-id="4891f-143">The corresponding type in the .NET Framework is the <xref:System.String?displayProperty=nameWithType> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4891f-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4891f-144">See also</span></span>

- <xref:System.String?displayProperty=nameWithType>
- [<span data-ttu-id="4891f-145">数据类型</span><span class="sxs-lookup"><span data-stu-id="4891f-145">Data Types</span></span>](index.md)
- [<span data-ttu-id="4891f-146">Char 数据类型</span><span class="sxs-lookup"><span data-stu-id="4891f-146">Char Data Type</span></span>](char-data-type.md)
- [<span data-ttu-id="4891f-147">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="4891f-147">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="4891f-148">转换摘要</span><span class="sxs-lookup"><span data-stu-id="4891f-148">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="4891f-149">如何：调用需要使用无符号类型的 Windows 函数</span><span class="sxs-lookup"><span data-stu-id="4891f-149">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="4891f-150">有效使用数据类型</span><span class="sxs-lookup"><span data-stu-id="4891f-150">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)

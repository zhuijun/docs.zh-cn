---
title: 字符串
description: '了解 F # "string" 类型如何将不可变文本表示为 Unicode 字符序列。'
ms.date: 08/15/2020
ms.openlocfilehash: f6ec36feeb197bf785c702e7b626cf5cf80696ab
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812206"
---
# <a name="strings"></a><span data-ttu-id="f52e3-103">字符串</span><span class="sxs-lookup"><span data-stu-id="f52e3-103">Strings</span></span>

<span data-ttu-id="f52e3-104">`string`类型将不可变文本表示为 Unicode 字符序列。</span><span class="sxs-lookup"><span data-stu-id="f52e3-104">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="f52e3-105">`string` 是 `System.String` 在 .NET 中的别名。</span><span class="sxs-lookup"><span data-stu-id="f52e3-105">`string` is an alias for `System.String` in .NET.</span></span>

## <a name="remarks"></a><span data-ttu-id="f52e3-106">注解</span><span class="sxs-lookup"><span data-stu-id="f52e3-106">Remarks</span></span>

<span data-ttu-id="f52e3-107">字符串文本由引号 ( ") 字符分隔。</span><span class="sxs-lookup"><span data-stu-id="f52e3-107">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="f52e3-108">反斜杠字符 ( \\ ) 用于对某些特殊字符进行编码。</span><span class="sxs-lookup"><span data-stu-id="f52e3-108">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="f52e3-109">反斜杠和下一个字符共同称为 *转义序列*。</span><span class="sxs-lookup"><span data-stu-id="f52e3-109">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="f52e3-110">下表显示了 F # 字符串文本中支持的转义序列。</span><span class="sxs-lookup"><span data-stu-id="f52e3-110">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="f52e3-111">字符</span><span class="sxs-lookup"><span data-stu-id="f52e3-111">Character</span></span>|<span data-ttu-id="f52e3-112">转义序列</span><span class="sxs-lookup"><span data-stu-id="f52e3-112">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="f52e3-113">警报</span><span class="sxs-lookup"><span data-stu-id="f52e3-113">Alert</span></span>|`\a`|
|<span data-ttu-id="f52e3-114">Backspace</span><span class="sxs-lookup"><span data-stu-id="f52e3-114">Backspace</span></span>|`\b`|
|<span data-ttu-id="f52e3-115">换页</span><span class="sxs-lookup"><span data-stu-id="f52e3-115">Form feed</span></span>|`\f`|
|<span data-ttu-id="f52e3-116">换行符</span><span class="sxs-lookup"><span data-stu-id="f52e3-116">Newline</span></span>|`\n`|
|<span data-ttu-id="f52e3-117">回车</span><span class="sxs-lookup"><span data-stu-id="f52e3-117">Carriage return</span></span>|`\r`|
|<span data-ttu-id="f52e3-118">选项卡</span><span class="sxs-lookup"><span data-stu-id="f52e3-118">Tab</span></span>|`\t`|
|<span data-ttu-id="f52e3-119">垂直制表符</span><span class="sxs-lookup"><span data-stu-id="f52e3-119">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="f52e3-120">反斜杠</span><span class="sxs-lookup"><span data-stu-id="f52e3-120">Backslash</span></span>|`\\`|
|<span data-ttu-id="f52e3-121">引号</span><span class="sxs-lookup"><span data-stu-id="f52e3-121">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="f52e3-122">撇号</span><span class="sxs-lookup"><span data-stu-id="f52e3-122">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="f52e3-123">Unicode 字符</span><span class="sxs-lookup"><span data-stu-id="f52e3-123">Unicode character</span></span>|<span data-ttu-id="f52e3-124">`\DDD` (，其中 `D` 指示十进制数字; 范围为 000-255; 例如， `\231` = "ç" ) </span><span class="sxs-lookup"><span data-stu-id="f52e3-124">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; for example, `\231` = "ç")</span></span>|
|<span data-ttu-id="f52e3-125">Unicode 字符</span><span class="sxs-lookup"><span data-stu-id="f52e3-125">Unicode character</span></span>|<span data-ttu-id="f52e3-126">`\xHH` (，其中 `H` 指示十六进制数字; 范围为 00-FF; 例如， `\xE7` = "ç" ) </span><span class="sxs-lookup"><span data-stu-id="f52e3-126">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; for example, `\xE7` = "ç")</span></span>|
|<span data-ttu-id="f52e3-127">Unicode 字符</span><span class="sxs-lookup"><span data-stu-id="f52e3-127">Unicode character</span></span>|<span data-ttu-id="f52e3-128">`\uHHHH` (UTF-16)  (，其中 `H` 指示十六进制数字; 范围为 0000-FFFF; 例如， `\u00E7` = "ç" ) </span><span class="sxs-lookup"><span data-stu-id="f52e3-128">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  for example, `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="f52e3-129">Unicode 字符</span><span class="sxs-lookup"><span data-stu-id="f52e3-129">Unicode character</span></span>|<span data-ttu-id="f52e3-130">`\U00HHHHHH` (32)  (，其中 `H` 指示十六进制数字; 10FFFF 的范围; 例如， `\U0001F47D` = " 👽 " ) </span><span class="sxs-lookup"><span data-stu-id="f52e3-130">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  for example, `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="f52e3-131">`\DDD`转义序列是十进制符号，而不是八进制表示法，这与大多数其他语言类似。</span><span class="sxs-lookup"><span data-stu-id="f52e3-131">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="f52e3-132">因此，数字 `8` 和 `9` 都是有效的，序列 `\032` 表示 (U + 0020) 的空间，而八进制表示法中的码位就是 `\040` 。</span><span class="sxs-lookup"><span data-stu-id="f52e3-132">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="f52e3-133">由于被限制为 0-255 (0xFF) 的范围， `\DDD` 且和 `\x` 转义序列实际上是 [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) 字符集，因为它匹配第一个 256 Unicode 码位。</span><span class="sxs-lookup"><span data-stu-id="f52e3-133">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

## <a name="verbatim-strings"></a><span data-ttu-id="f52e3-134">原义字符串</span><span class="sxs-lookup"><span data-stu-id="f52e3-134">Verbatim Strings</span></span>

<span data-ttu-id="f52e3-135">如果前面带有 @ 符号，则文本为逐字字符串。</span><span class="sxs-lookup"><span data-stu-id="f52e3-135">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="f52e3-136">这意味着将忽略任何转义序列，只不过两个引号字符被解释为一个引号字符。</span><span class="sxs-lookup"><span data-stu-id="f52e3-136">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

## <a name="triple-quoted-strings"></a><span data-ttu-id="f52e3-137">三个带引号的字符串</span><span class="sxs-lookup"><span data-stu-id="f52e3-137">Triple Quoted Strings</span></span>

<span data-ttu-id="f52e3-138">此外，字符串可以用三个引号括起来。</span><span class="sxs-lookup"><span data-stu-id="f52e3-138">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="f52e3-139">在这种情况下，将忽略所有转义序列，包括双引号字符。</span><span class="sxs-lookup"><span data-stu-id="f52e3-139">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="f52e3-140">若要指定包含嵌入的带引号的字符串的字符串，可以使用逐字字符串或带三个引号的字符串。</span><span class="sxs-lookup"><span data-stu-id="f52e3-140">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="f52e3-141">如果使用逐字字符串，则必须指定两个引号字符来指示单引号字符。</span><span class="sxs-lookup"><span data-stu-id="f52e3-141">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="f52e3-142">如果使用三个带引号的字符串，则可以使用单引号字符，而不会将它们分析为字符串的末尾。</span><span class="sxs-lookup"><span data-stu-id="f52e3-142">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="f52e3-143">当使用包含嵌入引号的 XML 或其他结构时，此方法会很有用。</span><span class="sxs-lookup"><span data-stu-id="f52e3-143">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="f52e3-144">在代码中，将接受带有分行符的字符串，分行符将按原义解释为换行符，除非反斜杠字符为换行符前的最后一个字符。</span><span class="sxs-lookup"><span data-stu-id="f52e3-144">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="f52e3-145">使用反斜杠字符时，将忽略下一行的前导空格。</span><span class="sxs-lookup"><span data-stu-id="f52e3-145">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="f52e3-146">下面的代码将生成一个字符串 `str1` ，该字符串具有值 `"abc\ndef"` 和 `str2` 具有值的字符串 `"abcdef"` 。</span><span class="sxs-lookup"><span data-stu-id="f52e3-146">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a><span data-ttu-id="f52e3-147">字符串索引和切片</span><span class="sxs-lookup"><span data-stu-id="f52e3-147">String Indexing and Slicing</span></span>

<span data-ttu-id="f52e3-148">您可以使用类似数组的语法来访问字符串中的单个字符，如下所示。</span><span class="sxs-lookup"><span data-stu-id="f52e3-148">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="f52e3-149">输出为 `b`。</span><span class="sxs-lookup"><span data-stu-id="f52e3-149">The output is `b`.</span></span>

<span data-ttu-id="f52e3-150">或者，您可以使用数组切片语法来提取子字符串，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="f52e3-150">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="f52e3-151">输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="f52e3-151">The output is as follows.</span></span>

```console
abc
def
```

<span data-ttu-id="f52e3-152">可以按无符号字节的数组（类型）表示 ASCII 字符串 `byte[]` 。</span><span class="sxs-lookup"><span data-stu-id="f52e3-152">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="f52e3-153">将后缀添加 `B` 到字符串文字，以指示它是 ASCII 字符串。</span><span class="sxs-lookup"><span data-stu-id="f52e3-153">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="f52e3-154">与 byte 数组一起使用的 ASCII 字符串文本除了 Unicode 转义序列外，与 Unicode 字符串支持相同的转义序列。</span><span class="sxs-lookup"><span data-stu-id="f52e3-154">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="f52e3-155">字符串运算符</span><span class="sxs-lookup"><span data-stu-id="f52e3-155">String Operators</span></span>

<span data-ttu-id="f52e3-156">`+`运算符可用于连接字符串，保持与 .NET Framework 字符串处理功能的兼容性。</span><span class="sxs-lookup"><span data-stu-id="f52e3-156">The `+` operator can be used to concatenate strings, maintaining compatibility with the .NET Framework string handling features.</span></span> <span data-ttu-id="f52e3-157">下面的示例演示字符串串联。</span><span class="sxs-lookup"><span data-stu-id="f52e3-157">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="f52e3-158">String 类</span><span class="sxs-lookup"><span data-stu-id="f52e3-158">String Class</span></span>

<span data-ttu-id="f52e3-159">由于 F # 中的字符串类型实际上是 .NET Framework `System.String` 类型，因此所有 `System.String` 成员都可用。</span><span class="sxs-lookup"><span data-stu-id="f52e3-159">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="f52e3-160">这包括 `+` 用于连接字符串、属性和属性的运算符，该运算符将 `Length` `Chars` 字符串作为 Unicode 字符数组返回。</span><span class="sxs-lookup"><span data-stu-id="f52e3-160">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="f52e3-161">有关字符串的详细信息，请参阅 `System.String` 。</span><span class="sxs-lookup"><span data-stu-id="f52e3-161">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="f52e3-162">通过使用的 `Chars` 属性 `System.String` ，可以通过指定索引来访问字符串中的各个字符，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="f52e3-162">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="f52e3-163">字符串模块</span><span class="sxs-lookup"><span data-stu-id="f52e3-163">String Module</span></span>

<span data-ttu-id="f52e3-164">命名空间中的模块包含了用于字符串处理的其他功能 `String` `FSharp.Core` 。</span><span class="sxs-lookup"><span data-stu-id="f52e3-164">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="f52e3-165">有关详细信息，请参阅 [字符串模块](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-stringmodule.html)。</span><span class="sxs-lookup"><span data-stu-id="f52e3-165">For more information, see [String Module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-stringmodule.html).</span></span>

## <a name="see-also"></a><span data-ttu-id="f52e3-166">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f52e3-166">See also</span></span>

- [<span data-ttu-id="f52e3-167">F# 语言参考</span><span class="sxs-lookup"><span data-stu-id="f52e3-167">F# Language Reference</span></span>](index.md)

---
title: 字符串函数
ms.date: 07/20/2015
helpviewer_keywords:
- string functions
ms.assetid: f1bf9ac2-cbcf-4298-ae51-53182076bdc8
ms.openlocfilehash: 778e57eadd75baf1aabd100f9d8d41a490f79a04
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406283"
---
# <a name="string-functions-visual-basic"></a><span data-ttu-id="7bed8-102">字符串函数 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7bed8-102">String Functions (Visual Basic)</span></span>

<span data-ttu-id="7bed8-103">下表列出了 Visual Basic 在类中提供的 <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType> 用于搜索和操作字符串的函数。</span><span class="sxs-lookup"><span data-stu-id="7bed8-103">The following table lists the functions that Visual Basic provides in the <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType> class to search and manipulate strings.</span></span> <span data-ttu-id="7bed8-104">它们可以视为 Visual Basic 内部函数;也就是说，您不必将它们作为类的显式成员进行调用，如示例所示。</span><span class="sxs-lookup"><span data-stu-id="7bed8-104">They can be regarded as Visual Basic intrinsic functions; that is, you do not have to call them as explicit members of a class, as the examples show.</span></span> <span data-ttu-id="7bed8-105">类中提供了其他方法，在某些情况下为互补方法 <xref:System.String?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="7bed8-105">Additional methods, and in some cases complementary methods, are available in the <xref:System.String?displayProperty=nameWithType> class.</span></span>

|<span data-ttu-id="7bed8-106">.NET Framework 方法</span><span class="sxs-lookup"><span data-stu-id="7bed8-106">.NET Framework method</span></span>|<span data-ttu-id="7bed8-107">说明</span><span class="sxs-lookup"><span data-stu-id="7bed8-107">Description</span></span>|
|---------------------------|-----------------|
|<span data-ttu-id="7bed8-108"><xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A></span><span class="sxs-lookup"><span data-stu-id="7bed8-108"><xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A></span></span>|<span data-ttu-id="7bed8-109">返回一个 `Integer` 值，该值表示与某个字符相对应的字符代码。</span><span class="sxs-lookup"><span data-stu-id="7bed8-109">Returns an `Integer` value representing the character code corresponding to a character.</span></span>|
|<span data-ttu-id="7bed8-110"><xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A></span><span class="sxs-lookup"><span data-stu-id="7bed8-110"><xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A></span></span>|<span data-ttu-id="7bed8-111">返回与指定字符代码相关联的字符。</span><span class="sxs-lookup"><span data-stu-id="7bed8-111">Returns the character associated with the specified character code.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Filter%2A>|<span data-ttu-id="7bed8-112">返回一个从零开始的数组，该数组包含基于指定筛选条件的 `String` 数组的子集。</span><span class="sxs-lookup"><span data-stu-id="7bed8-112">Returns a zero-based array containing a subset of a `String` array based on specified filter criteria.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Format%2A>|<span data-ttu-id="7bed8-113">返回根据格式 `String` 表达式中包含的指令设置格式的字符串。</span><span class="sxs-lookup"><span data-stu-id="7bed8-113">Returns a string formatted according to instructions contained in a format `String` expression.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.FormatCurrency%2A>|<span data-ttu-id="7bed8-114">返回一个格式为货币值的表达式，该货币值使用系统控制面板中定义的货币符号。</span><span class="sxs-lookup"><span data-stu-id="7bed8-114">Returns an expression formatted as a currency value using the currency symbol defined in the system control panel.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>|<span data-ttu-id="7bed8-115">返回一个表示日期/时间值的字符串表达式。</span><span class="sxs-lookup"><span data-stu-id="7bed8-115">Returns a string expression representing a date/time value.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.FormatNumber%2A>|<span data-ttu-id="7bed8-116">返回格式化为数字的表达式。</span><span class="sxs-lookup"><span data-stu-id="7bed8-116">Returns an expression formatted as a number.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.FormatPercent%2A>|<span data-ttu-id="7bed8-117">返回以 % 字符结尾的百分比格式的表达式（即乘以 100）。</span><span class="sxs-lookup"><span data-stu-id="7bed8-117">Returns an expression formatted as a percentage (that is, multiplied by 100) with a trailing % character.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.InStr%2A>|<span data-ttu-id="7bed8-118">返回一个整数，该整数指定一个字符串在另一个字符串中的第一个匹配项的起始位置。</span><span class="sxs-lookup"><span data-stu-id="7bed8-118">Returns an integer specifying the start position of the first occurrence of one string within another.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.InStrRev%2A>|<span data-ttu-id="7bed8-119">返回某一字符串从另一字符串的右侧开始算起第一次出现的位置。</span><span class="sxs-lookup"><span data-stu-id="7bed8-119">Returns the position of the first occurrence of one string within another, starting from the right side of the string.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Join%2A>|<span data-ttu-id="7bed8-120">返回通过连接一个数组中包含的若干子字符串创建的字符串。</span><span class="sxs-lookup"><span data-stu-id="7bed8-120">Returns a string created by joining a number of substrings contained in an array.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.LCase%2A>|<span data-ttu-id="7bed8-121">返回将转换为小写的字符串或字符。</span><span class="sxs-lookup"><span data-stu-id="7bed8-121">Returns a string or character converted to lowercase.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Left%2A>|<span data-ttu-id="7bed8-122">返回一个字符串，该字符串包含从某字符串左侧算起的指定数量的字符。</span><span class="sxs-lookup"><span data-stu-id="7bed8-122">Returns a string containing a specified number of characters from the left side of a string.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Len%2A>|<span data-ttu-id="7bed8-123">返回一个整数，该整数包含字符串中的字符数。</span><span class="sxs-lookup"><span data-stu-id="7bed8-123">Returns an integer that contains the number of characters in a string.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.LSet%2A>|<span data-ttu-id="7bed8-124">返回一个左对齐字符串，该字符串包含调整为指定长度的指定的字符串。</span><span class="sxs-lookup"><span data-stu-id="7bed8-124">Returns a left-aligned string containing the specified string adjusted to the specified length.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.LTrim%2A>|<span data-ttu-id="7bed8-125">返回一个字符串，该字符串包含不带前导空格的指定字符串的副本。</span><span class="sxs-lookup"><span data-stu-id="7bed8-125">Returns a string containing a copy of a specified string with no leading spaces.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Mid%2A>|<span data-ttu-id="7bed8-126">返回一个字符串，该字符串包含字符串中指定数目的字符。</span><span class="sxs-lookup"><span data-stu-id="7bed8-126">Returns a string containing a specified number of characters from a string.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Replace%2A>|<span data-ttu-id="7bed8-127">返回一个字符串，其中的指定子字符串已由另一个子字符串替换了指定的次数。</span><span class="sxs-lookup"><span data-stu-id="7bed8-127">Returns a string in which a specified substring has been replaced with another substring a specified number of times.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Right%2A>|<span data-ttu-id="7bed8-128">返回一个字符串，其中包含从某个字符串右端开始的指定数量的字符。</span><span class="sxs-lookup"><span data-stu-id="7bed8-128">Returns a string containing a specified number of characters from the right side of a string.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.RSet%2A>|<span data-ttu-id="7bed8-129">返回包含调整为指定长度的指定字符串的右对齐字符串。</span><span class="sxs-lookup"><span data-stu-id="7bed8-129">Returns a right-aligned string containing the specified string adjusted to the specified length.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.RTrim%2A>|<span data-ttu-id="7bed8-130">返回一个字符串，该字符串包含不带尾随空格的指定字符串的副本。</span><span class="sxs-lookup"><span data-stu-id="7bed8-130">Returns a string containing a copy of a specified string with no trailing spaces.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Space%2A>|<span data-ttu-id="7bed8-131">返回由指定数量空格组成的字符串。</span><span class="sxs-lookup"><span data-stu-id="7bed8-131">Returns a string consisting of the specified number of spaces.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Split%2A>|<span data-ttu-id="7bed8-132">返回一个从零开始的一维数组，其中包含指定数量的子字符串。</span><span class="sxs-lookup"><span data-stu-id="7bed8-132">Returns a zero-based, one-dimensional array containing a specified number of substrings.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.StrComp%2A>|<span data-ttu-id="7bed8-133">根据字符串的比较结果返回 -1、0 或 1。</span><span class="sxs-lookup"><span data-stu-id="7bed8-133">Returns -1, 0, or 1, based on the result of a string comparison.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.StrConv%2A>|<span data-ttu-id="7bed8-134">返回按照指定方式转换的字符串。</span><span class="sxs-lookup"><span data-stu-id="7bed8-134">Returns a string converted as specified.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.StrDup%2A>|<span data-ttu-id="7bed8-135">返回由指定字符重复指定次数后形成的字符串或对象。</span><span class="sxs-lookup"><span data-stu-id="7bed8-135">Returns a string or object consisting of the specified character repeated the specified number of times.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.StrReverse%2A>|<span data-ttu-id="7bed8-136">返回指定字符串的字符顺序是相反的字符串。</span><span class="sxs-lookup"><span data-stu-id="7bed8-136">Returns a string in which the character order of a specified string is reversed.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Trim%2A>|<span data-ttu-id="7bed8-137">返回一个字符串，该字符串包含不带前导空格或尾随空格的指定字符串的副本。</span><span class="sxs-lookup"><span data-stu-id="7bed8-137">Returns a string containing a copy of a specified string with no leading or trailing spaces.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.UCase%2A>|<span data-ttu-id="7bed8-138">返回一个字符串或字符，其中包含转换为大写的指定字符串。</span><span class="sxs-lookup"><span data-stu-id="7bed8-138">Returns a string or character containing the specified string converted to uppercase.</span></span>|

<span data-ttu-id="7bed8-139">您可以使用[Option Compare](../statements/option-compare-statement.md)语句来设置是使用不区分大小写的文本排序顺序（由系统的区域设置（ `Text` ）决定），还是通过字符的内部二进制表示形式来比较字符串（ `Binary` ）。</span><span class="sxs-lookup"><span data-stu-id="7bed8-139">You can use the [Option Compare](../statements/option-compare-statement.md) statement to set whether strings are compared using a case-insensitive text sort order determined by your system's locale (`Text`) or by the internal binary representations of the characters (`Binary`).</span></span> <span data-ttu-id="7bed8-140">默认的文本比较方法是 `Binary`。</span><span class="sxs-lookup"><span data-stu-id="7bed8-140">The default text comparison method is `Binary`.</span></span>

## <a name="example-ucase"></a><span data-ttu-id="7bed8-141">示例： UCase</span><span class="sxs-lookup"><span data-stu-id="7bed8-141">Example: UCase</span></span>

<span data-ttu-id="7bed8-142">本例使用 `UCase` 函数返回字符串的大写版本。</span><span class="sxs-lookup"><span data-stu-id="7bed8-142">This example uses the `UCase` function to return an uppercase version of a string.</span></span>
[!code-vb[VbVbalrStrings#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#31)]

## <a name="example-ltrim"></a><span data-ttu-id="7bed8-143">示例： LTrim</span><span class="sxs-lookup"><span data-stu-id="7bed8-143">Example: LTrim</span></span>

<span data-ttu-id="7bed8-144">此示例使用 `LTrim` 函数去除字符串变量的前导空格，使用 `RTrim` 函数去除尾随空格，</span><span class="sxs-lookup"><span data-stu-id="7bed8-144">This example uses the `LTrim` function to strip leading spaces and the `RTrim` function to strip trailing spaces from a string variable.</span></span> <span data-ttu-id="7bed8-145">并使用 `Trim` 函数同时去除这两种类型的空格。</span><span class="sxs-lookup"><span data-stu-id="7bed8-145">It uses the `Trim` function to strip both types of spaces.</span></span>

[!code-vb[VbVbalrStrings#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#25)]

## <a name="example-mid"></a><span data-ttu-id="7bed8-146">示例： Mid</span><span class="sxs-lookup"><span data-stu-id="7bed8-146">Example: Mid</span></span>

<span data-ttu-id="7bed8-147">此示例使用 `Mid` 函数从字符串返回指定数目的字符。</span><span class="sxs-lookup"><span data-stu-id="7bed8-147">This example uses the `Mid` function to return a specified number of characters from a string.</span></span>

[!code-vb[VbVbalrStrings#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#17)]

## <a name="example-len"></a><span data-ttu-id="7bed8-148">示例： Len</span><span class="sxs-lookup"><span data-stu-id="7bed8-148">Example: Len</span></span>

<span data-ttu-id="7bed8-149">本例使用 `Len` 返回字符串中的字符数。</span><span class="sxs-lookup"><span data-stu-id="7bed8-149">This example uses `Len` to return the number of characters in a string.</span></span>

[!code-vb[VbVbalrStrings#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#33)]

## <a name="example-instr"></a><span data-ttu-id="7bed8-150">示例： InStr</span><span class="sxs-lookup"><span data-stu-id="7bed8-150">Example: InStr</span></span>

<span data-ttu-id="7bed8-151">本例使用 `InStr` 函数返回一个字符串在另一个字符串中的第一个匹配项的位置。</span><span class="sxs-lookup"><span data-stu-id="7bed8-151">This example uses the `InStr` function to return the position of the first occurrence of one string within another.</span></span>

[!code-vb[VbVbalrStrings#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#8)]

## <a name="example-format"></a><span data-ttu-id="7bed8-152">示例：格式</span><span class="sxs-lookup"><span data-stu-id="7bed8-152">Example: Format</span></span>

<span data-ttu-id="7bed8-153">此示例演示同时使用 `Format` 格式和用户定义格式格式化值的 `String` 函数的各种用法。</span><span class="sxs-lookup"><span data-stu-id="7bed8-153">This example shows various uses of the `Format` function to format values using both `String` formats and user-defined formats.</span></span> <span data-ttu-id="7bed8-154">对于日期分隔符 (`/`)、时间分隔符 (`:`) 和 AM/PM 指示符（`t` 和 `tt`），系统显示的实际格式化输出取决于代码使用的区域设置。</span><span class="sxs-lookup"><span data-stu-id="7bed8-154">For the date separator (`/`), time separator (`:`), and the AM/PM indicators (`t` and `tt`), the actual formatted output displayed by your system depends on the locale settings the code is using.</span></span> <span data-ttu-id="7bed8-155">当在开发环境中显示时间和日期时，使用代码区域设置的短时间格式和短日期格式。</span><span class="sxs-lookup"><span data-stu-id="7bed8-155">When times and dates are displayed in the development environment, the short time format and short date format of the code locale are used.</span></span>

> [!NOTE]
> <span data-ttu-id="7bed8-156">对于使用 24 小时制的区域设置，AM/PM 指示符（`t` 和 `tt`）不显示任何内容。</span><span class="sxs-lookup"><span data-stu-id="7bed8-156">For locales that use a 24-hour clock, the AM/PM indicators (`t` and `tt`) display nothing.</span></span>

[!code-vb[VbVbalrStrings#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#27)]

## <a name="see-also"></a><span data-ttu-id="7bed8-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7bed8-157">See also</span></span>

- [<span data-ttu-id="7bed8-158">关键字</span><span class="sxs-lookup"><span data-stu-id="7bed8-158">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="7bed8-159">Visual Basic 运行库成员</span><span class="sxs-lookup"><span data-stu-id="7bed8-159">Visual Basic Runtime Library Members</span></span>](../runtime-library-members.md)
- [<span data-ttu-id="7bed8-160">字符串操作摘要</span><span class="sxs-lookup"><span data-stu-id="7bed8-160">String Manipulation Summary</span></span>](../keywords/string-manipulation-summary.md)
- [<span data-ttu-id="7bed8-161">System.string 类方法</span><span class="sxs-lookup"><span data-stu-id="7bed8-161">System.String class methods</span></span>](xref:System.String#methods)

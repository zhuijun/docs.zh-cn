---
title: 如何确认字符串是有效的电子邮件格式
description: 阅读有关正则表达式如何在 .NET 中验证字符串是否为有效电子邮件格式的示例。
ms.date: 06/30/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, examples
- user input, examples
- Regex.IsMatch method
- regular expressions [.NET Framework], examples
- examples [Visual Basic], strings
- IsValidEmail
- validation, email strings
- input, checking
- strings [.NET Framework], examples [Visual Basic]
- email [.NET Framework], validating
- IsMatch method
ms.assetid: 7536af08-4e86-4953-98a1-a8298623df92
ms.openlocfilehash: d303c13dead6b4ba29cb7476c2a9b382a9395aff
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803191"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a><span data-ttu-id="b9c33-103">如何确认字符串是有效的电子邮件格式</span><span class="sxs-lookup"><span data-stu-id="b9c33-103">How to verify that strings are in valid email format</span></span>

<span data-ttu-id="b9c33-104">下面的示例使用正则表达式来验证一个字符串是否为有效的电子邮件格式。</span><span class="sxs-lookup"><span data-stu-id="b9c33-104">The following example uses a regular expression to verify that a string is in valid email format.</span></span>

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a><span data-ttu-id="b9c33-105">示例</span><span class="sxs-lookup"><span data-stu-id="b9c33-105">Example</span></span>

<span data-ttu-id="b9c33-106">该示例定义 `IsValidEmail` 方法，如果字符串包含有效的电子邮件地址，则该方法返回 `true` ，否则返回 `false` ，但不采取其他任何操作。</span><span class="sxs-lookup"><span data-stu-id="b9c33-106">The example defines an `IsValidEmail` method, which returns `true` if the string contains a valid email address and `false` if it does not, but takes no other action.</span></span>

<span data-ttu-id="b9c33-107">若要验证电子邮件地址是否有效，方法 `IsValidEmail` 将使用 <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> 正则表达式模式调用 `(@)(.+)$` 方法将域名从电子邮件地址分离。</span><span class="sxs-lookup"><span data-stu-id="b9c33-107">To verify that the email address is valid, the `IsValidEmail` method calls the <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> method with the `(@)(.+)$` regular expression pattern to separate the domain name from the email address.</span></span> <span data-ttu-id="b9c33-108">第三个参数是表示了处理和替换匹配文本的方法的 <xref:System.Text.RegularExpressions.MatchEvaluator> 委托。</span><span class="sxs-lookup"><span data-stu-id="b9c33-108">The third parameter is a <xref:System.Text.RegularExpressions.MatchEvaluator> delegate that represents the method that processes and replaces the matched text.</span></span> <span data-ttu-id="b9c33-109">正则表达式模式的解释如下。</span><span class="sxs-lookup"><span data-stu-id="b9c33-109">The regular expression pattern is interpreted as follows.</span></span>

|<span data-ttu-id="b9c33-110">模式</span><span class="sxs-lookup"><span data-stu-id="b9c33-110">Pattern</span></span>|<span data-ttu-id="b9c33-111">描述</span><span class="sxs-lookup"><span data-stu-id="b9c33-111">Description</span></span>|
|-------------|-----------------|
|`(@)`|<span data-ttu-id="b9c33-112">匹配 @ 字符。</span><span class="sxs-lookup"><span data-stu-id="b9c33-112">Match the @ character.</span></span> <span data-ttu-id="b9c33-113">这是第一个捕获组。</span><span class="sxs-lookup"><span data-stu-id="b9c33-113">This is the first capturing group.</span></span>|
|`(.+)`|<span data-ttu-id="b9c33-114">匹配任意字符的一个或多个匹配项。</span><span class="sxs-lookup"><span data-stu-id="b9c33-114">Match one or more occurrences of any character.</span></span> <span data-ttu-id="b9c33-115">这是第二个捕获组。</span><span class="sxs-lookup"><span data-stu-id="b9c33-115">This is the second capturing group.</span></span>|
|`$`|<span data-ttu-id="b9c33-116">在字符串的结尾结束匹配。</span><span class="sxs-lookup"><span data-stu-id="b9c33-116">End the match at the end of the string.</span></span>|

<span data-ttu-id="b9c33-117">使用 @ 字符的域名已传递给 `DomainMapper` 方法，该方法使用 <xref:System.Globalization.IdnMapping> 类将 US-ASCII 字符范围外的 Unicode 字符转换为 Punycode。</span><span class="sxs-lookup"><span data-stu-id="b9c33-117">The domain name along with the @ character is passed to the `DomainMapper` method, which uses the <xref:System.Globalization.IdnMapping> class to translate Unicode characters that are outside the US-ASCII character range to Punycode.</span></span> <span data-ttu-id="b9c33-118">如果 `invalid` 方法在域名中检测到任何无效字符，该方法还会将 `True` 标志设置为 <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="b9c33-118">The method also sets the `invalid` flag to `True` if the <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> method detects any invalid characters in the domain name.</span></span> <span data-ttu-id="b9c33-119">该方法将冠以 @ 符号的 Punycode 域名返回给 `IsValidEmail` 方法。</span><span class="sxs-lookup"><span data-stu-id="b9c33-119">The method returns the Punycode domain name preceded by the @ symbol to the `IsValidEmail` method.</span></span>

<span data-ttu-id="b9c33-120">然后 `IsValidEmail` 方法调用 <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> 方法验证该地址是否符合正则表达式模式。</span><span class="sxs-lookup"><span data-stu-id="b9c33-120">The `IsValidEmail` method then calls the <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> method to verify that the address conforms to a regular expression pattern.</span></span>

<span data-ttu-id="b9c33-121">请注意， `IsValidEmail` 方法不执行身份验证来验证电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="b9c33-121">Note that the `IsValidEmail` method does not perform authentication to validate the email address.</span></span> <span data-ttu-id="b9c33-122">它只确定其格式对于电子邮件地址是否有效。</span><span class="sxs-lookup"><span data-stu-id="b9c33-122">It merely determines whether its format is valid for an email address.</span></span> <span data-ttu-id="b9c33-123">此外， `IsValidEmail` 方法不对顶级域名是否是 [IANA 根区域数据库](https://www.iana.org/domains/root/db)中列出的有效域名进行验证，这需执行查找操作。</span><span class="sxs-lookup"><span data-stu-id="b9c33-123">In addition, the `IsValidEmail` method does not verify that the top-level domain name is a valid domain name listed at the [IANA Root Zone Database](https://www.iana.org/domains/root/db), which would require a look-up operation.</span></span> <span data-ttu-id="b9c33-124">相反，正则表达式仅验证由二到二十四个 ASCII 字符组成的顶级域名，该域名以字母数字开头并以字符结尾，且其余的字符是字母数字或连字符 (-)。</span><span class="sxs-lookup"><span data-stu-id="b9c33-124">Instead, the regular expression merely verifies that the top-level domain name consists of between two and twenty-four ASCII characters, with alphanumeric first and last characters and the remaining characters being either alphanumeric or a hyphen (-).</span></span>

[!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
[!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]

<span data-ttu-id="b9c33-125">在本例中，正则表达式模式 ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*)(?<=[0-9a-z])@))(?(\[)(\[(\d{1,3}\.){3}\d{1,3}\])|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))$`` 的解释如以下图例所示。</span><span class="sxs-lookup"><span data-stu-id="b9c33-125">In this example, the regular expression pattern ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*)(?<=[0-9a-z])@))(?(\[)(\[(\d{1,3}\.){3}\d{1,3}\])|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))$`` is interpreted as shown in the following legend.</span></span> <span data-ttu-id="b9c33-126">使用 <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> 标志编译正则表达式。</span><span class="sxs-lookup"><span data-stu-id="b9c33-126">The regular expression is compiled using the <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> flag.</span></span>

<span data-ttu-id="b9c33-127">模式 `^`：从字符串的开头部分开始匹配。</span><span class="sxs-lookup"><span data-stu-id="b9c33-127">Pattern `^`: Begin the match at the start of the string.</span></span>

<span data-ttu-id="b9c33-128">模式 `(?(")`：确定第一个字符是否为引号。</span><span class="sxs-lookup"><span data-stu-id="b9c33-128">Pattern `(?(")`: Determine whether the first character is a quotation mark.</span></span> <span data-ttu-id="b9c33-129">`(?(")` 为替换构造的开头。</span><span class="sxs-lookup"><span data-stu-id="b9c33-129">`(?(")` is the beginning of an alternation construct.</span></span>

<span data-ttu-id="b9c33-130">模式 `(?(")(".+?(?<!\\)"@)`：如果第一个字符是引号，则匹配一个开始引号，后跟至少一个任意字符，再后跟一个结束引号。</span><span class="sxs-lookup"><span data-stu-id="b9c33-130">Pattern `(?(")(".+?(?<!\\)"@)`: If the first character is a quotation mark, match a beginning quotation mark followed by at least one occurrence of any character, followed by an ending quotation mark.</span></span> <span data-ttu-id="b9c33-131">不得在结束引号前面加反斜杠字符 (\\)。</span><span class="sxs-lookup"><span data-stu-id="b9c33-131">The ending quotation mark must not be preceded by a backslash character (\\).</span></span> <span data-ttu-id="b9c33-132">`(?<!` 是零宽度负预测先行断言的开头。</span><span class="sxs-lookup"><span data-stu-id="b9c33-132">`(?<!` is the beginning of a zero-width negative lookbehind assertion.</span></span> <span data-ttu-id="b9c33-133">字符串应以 at 符号 (@) 结束。</span><span class="sxs-lookup"><span data-stu-id="b9c33-133">The string should conclude with an at sign (@).</span></span>

<span data-ttu-id="b9c33-134">模式 `|(([0-9a-z]`：如果第一个字符不是引号，则匹配从 a 到 z 或 A 到 Z（比较不区分大小写）的任意字母字符或从 0 到 9 的任意数字字符。</span><span class="sxs-lookup"><span data-stu-id="b9c33-134">Pattern `|(([0-9a-z]`: If the first character is not a quotation mark, match any alphabetic character from a to z or A to Z (the comparison is case insensitive), or any numeric character from 0 to 9.</span></span>

<span data-ttu-id="b9c33-135">模式 `(\.(?!\.))`：如果下一个字符为句点，则匹配它。</span><span class="sxs-lookup"><span data-stu-id="b9c33-135">Pattern `(\.(?!\.))`: If the next character is a period, match it.</span></span> <span data-ttu-id="b9c33-136">如果下一个字符不为句点，则看下一个字符并继续进行匹配。</span><span class="sxs-lookup"><span data-stu-id="b9c33-136">If it is not a period, look ahead to the next character and continue the match.</span></span> <span data-ttu-id="b9c33-137">`(?!\.)` 是宽度为零的负预测先行断言，可防止两个连续句号出现在电子邮件地址的本地部分中。</span><span class="sxs-lookup"><span data-stu-id="b9c33-137">`(?!\.)` is a zero-width negative lookahead assertion that prevents two consecutive periods from appearing in the local part of an email address.</span></span>

<span data-ttu-id="b9c33-138">模式 ``|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w]``：如果下一个字符不为句点，则匹配任何单词字符或以下字符之一：-!#$%&'\*+/=?^\`{}|~</span><span class="sxs-lookup"><span data-stu-id="b9c33-138">Pattern ``|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w]``: If the next character is not a period, match any word character or one of the following characters: -!#$%&'\*+/=?^\`{}|~</span></span>

<span data-ttu-id="b9c33-139">模式 ``((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*``：匹配替换模式（一个句点，后跟一个非句点或许多字符中的某个字符）零次或多次。</span><span class="sxs-lookup"><span data-stu-id="b9c33-139">Pattern ``((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*``: Match the alternation pattern (a period followed by a non-period, or one of a number of characters) zero or more times.</span></span>

<span data-ttu-id="b9c33-140">模式 `@`：匹配 @ 字符。</span><span class="sxs-lookup"><span data-stu-id="b9c33-140">Pattern `@`: Match the @ character.</span></span>

<span data-ttu-id="b9c33-141">模式 `(?<=[0-9a-z])`：如果 @ 字符之前的字符为从 A 到 Z、从 a 到 z 或从 0 到 9 的字符，则继续进行匹配。</span><span class="sxs-lookup"><span data-stu-id="b9c33-141">Pattern `(?<=[0-9a-z])`: Continue the match if the character that precedes the @ character is A through Z, a through z, or 0 through 9.</span></span> <span data-ttu-id="b9c33-142">此模式定义了一个零宽度的正后行断言。</span><span class="sxs-lookup"><span data-stu-id="b9c33-142">This pattern defines a zero-width positive lookbehind assertion.</span></span>

<span data-ttu-id="b9c33-143">模式 `(?(\[)`：检查 @ 后面的字符是否为左括号。</span><span class="sxs-lookup"><span data-stu-id="b9c33-143">Pattern `(?(\[)`: Check whether the character that follows @ is an opening bracket.</span></span>

<span data-ttu-id="b9c33-144">模式 `(\[(\d{1,3}\.){3}\d{1,3}\])`：如果该字符为左括号，则匹配该左括号，后跟 IP 地址（四个数字组，每个数字组包含一到三位数字，并且每个数字组用句点隔开）和右括号。</span><span class="sxs-lookup"><span data-stu-id="b9c33-144">Pattern `(\[(\d{1,3}\.){3}\d{1,3}\])`: If it is an opening bracket, match the opening bracket followed by an IP address (four sets of one to three digits, with each set separated by a period) and a closing bracket.</span></span>

<span data-ttu-id="b9c33-145">模式 `|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+`：如果 @ 后面的字符不是左括号，匹配一个字母数字字符（A-Z、a-z 或 0-9 中的某个值），后跟零个或多个连字符，再后跟零个或一个字母数字字符（A-Z、a-z 或 0-9 中的某个值），再后跟一个句点。</span><span class="sxs-lookup"><span data-stu-id="b9c33-145">Pattern `|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+`: If the character that follows @ is not an opening bracket, match one alphanumeric character with a value of A-Z, a-z, or 0-9, followed by zero or more occurrences of a hyphen, followed by zero or one alphanumeric character with a value of A-Z, a-z, or 0-9, followed by a period.</span></span> <span data-ttu-id="b9c33-146">此模式可以重复一次或多次，并且必须后跟顶级域名。</span><span class="sxs-lookup"><span data-stu-id="b9c33-146">This pattern can be repeated one or more times, and must be followed by the top-level domain name.</span></span>

<span data-ttu-id="b9c33-147">模式 `[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`：顶级域名必须以字母数字字符（a-z、A-Z 和 0-9）开始和结束。</span><span class="sxs-lookup"><span data-stu-id="b9c33-147">Pattern `[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`: The top-level domain name must begin and end with an alphanumeric character (a-z, A-Z, and 0-9).</span></span> <span data-ttu-id="b9c33-148">它还可以包括从零到 22 个字母数字或连字符的 ASCII 字符。</span><span class="sxs-lookup"><span data-stu-id="b9c33-148">It can also include from zero to 22 ASCII characters that are either alphanumeric or hyphens.</span></span>

<span data-ttu-id="b9c33-149">模式 `$`：在字符串的结尾结束匹配。</span><span class="sxs-lookup"><span data-stu-id="b9c33-149">Pattern `$`: End the match at the end of the string.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="b9c33-150">编译代码</span><span class="sxs-lookup"><span data-stu-id="b9c33-150">Compile the code</span></span>

<span data-ttu-id="b9c33-151">`IsValidEmail` 方法和 `DomainMapper` 方法可以包括在正则表达式实用工具方法库中，或者作为私有静态或实例方法包括在应用程序类中。</span><span class="sxs-lookup"><span data-stu-id="b9c33-151">The `IsValidEmail` and `DomainMapper` methods can be included in a library of regular expression utility methods, or they can be included as private static or instance methods in the application class.</span></span>

<span data-ttu-id="b9c33-152">还可以使用 <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> 方法将此正则表达式包含到正则表达式库中。</span><span class="sxs-lookup"><span data-stu-id="b9c33-152">You can also use the <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> method to include this regular expression in a regular expression library.</span></span>

<span data-ttu-id="b9c33-153">如果在正则表达式库中对其进行使用，则可使用例如以下代码对其进行调用：</span><span class="sxs-lookup"><span data-stu-id="b9c33-153">If they are used in a regular expression library, you can call them by using code such as the following:</span></span>

[!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
[!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]

## <a name="see-also"></a><span data-ttu-id="b9c33-154">请参阅</span><span class="sxs-lookup"><span data-stu-id="b9c33-154">See also</span></span>

- [<span data-ttu-id="b9c33-155">.NET Framework 正则表达式</span><span class="sxs-lookup"><span data-stu-id="b9c33-155">.NET Framework Regular Expressions</span></span>](regular-expressions.md)

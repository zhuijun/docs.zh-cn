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
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>如何确认字符串是有效的电子邮件格式

下面的示例使用正则表达式来验证一个字符串是否为有效的电子邮件格式。

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a>示例

该示例定义 `IsValidEmail` 方法，如果字符串包含有效的电子邮件地址，则该方法返回 `true` ，否则返回 `false` ，但不采取其他任何操作。

若要验证电子邮件地址是否有效，方法 `IsValidEmail` 将使用 <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> 正则表达式模式调用 `(@)(.+)$` 方法将域名从电子邮件地址分离。 第三个参数是表示了处理和替换匹配文本的方法的 <xref:System.Text.RegularExpressions.MatchEvaluator> 委托。 正则表达式模式的解释如下。

|模式|描述|
|-------------|-----------------|
|`(@)`|匹配 @ 字符。 这是第一个捕获组。|
|`(.+)`|匹配任意字符的一个或多个匹配项。 这是第二个捕获组。|
|`$`|在字符串的结尾结束匹配。|

使用 @ 字符的域名已传递给 `DomainMapper` 方法，该方法使用 <xref:System.Globalization.IdnMapping> 类将 US-ASCII 字符范围外的 Unicode 字符转换为 Punycode。 如果 `invalid` 方法在域名中检测到任何无效字符，该方法还会将 `True` 标志设置为 <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> 。 该方法将冠以 @ 符号的 Punycode 域名返回给 `IsValidEmail` 方法。

然后 `IsValidEmail` 方法调用 <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> 方法验证该地址是否符合正则表达式模式。

请注意， `IsValidEmail` 方法不执行身份验证来验证电子邮件地址。 它只确定其格式对于电子邮件地址是否有效。 此外， `IsValidEmail` 方法不对顶级域名是否是 [IANA 根区域数据库](https://www.iana.org/domains/root/db)中列出的有效域名进行验证，这需执行查找操作。 相反，正则表达式仅验证由二到二十四个 ASCII 字符组成的顶级域名，该域名以字母数字开头并以字符结尾，且其余的字符是字母数字或连字符 (-)。

[!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
[!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]

在本例中，正则表达式模式 ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*)(?<=[0-9a-z])@))(?(\[)(\[(\d{1,3}\.){3}\d{1,3}\])|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))$`` 的解释如以下图例所示。 使用 <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> 标志编译正则表达式。

模式 `^`：从字符串的开头部分开始匹配。

模式 `(?(")`：确定第一个字符是否为引号。 `(?(")` 为替换构造的开头。

模式 `(?(")(".+?(?<!\\)"@)`：如果第一个字符是引号，则匹配一个开始引号，后跟至少一个任意字符，再后跟一个结束引号。 不得在结束引号前面加反斜杠字符 (\\)。 `(?<!` 是零宽度负预测先行断言的开头。 字符串应以 at 符号 (@) 结束。

模式 `|(([0-9a-z]`：如果第一个字符不是引号，则匹配从 a 到 z 或 A 到 Z（比较不区分大小写）的任意字母字符或从 0 到 9 的任意数字字符。

模式 `(\.(?!\.))`：如果下一个字符为句点，则匹配它。 如果下一个字符不为句点，则看下一个字符并继续进行匹配。 `(?!\.)` 是宽度为零的负预测先行断言，可防止两个连续句号出现在电子邮件地址的本地部分中。

模式 ``|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w]``：如果下一个字符不为句点，则匹配任何单词字符或以下字符之一：-!#$%&'\*+/=?^\`{}|~

模式 ``((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*``：匹配替换模式（一个句点，后跟一个非句点或许多字符中的某个字符）零次或多次。

模式 `@`：匹配 @ 字符。

模式 `(?<=[0-9a-z])`：如果 @ 字符之前的字符为从 A 到 Z、从 a 到 z 或从 0 到 9 的字符，则继续进行匹配。 此模式定义了一个零宽度的正后行断言。

模式 `(?(\[)`：检查 @ 后面的字符是否为左括号。

模式 `(\[(\d{1,3}\.){3}\d{1,3}\])`：如果该字符为左括号，则匹配该左括号，后跟 IP 地址（四个数字组，每个数字组包含一到三位数字，并且每个数字组用句点隔开）和右括号。

模式 `|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+`：如果 @ 后面的字符不是左括号，匹配一个字母数字字符（A-Z、a-z 或 0-9 中的某个值），后跟零个或多个连字符，再后跟零个或一个字母数字字符（A-Z、a-z 或 0-9 中的某个值），再后跟一个句点。 此模式可以重复一次或多次，并且必须后跟顶级域名。

模式 `[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`：顶级域名必须以字母数字字符（a-z、A-Z 和 0-9）开始和结束。 它还可以包括从零到 22 个字母数字或连字符的 ASCII 字符。

模式 `$`：在字符串的结尾结束匹配。

## <a name="compile-the-code"></a>编译代码

`IsValidEmail` 方法和 `DomainMapper` 方法可以包括在正则表达式实用工具方法库中，或者作为私有静态或实例方法包括在应用程序类中。

还可以使用 <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> 方法将此正则表达式包含到正则表达式库中。

如果在正则表达式库中对其进行使用，则可使用例如以下代码对其进行调用：

[!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
[!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]

## <a name="see-also"></a>请参阅

- [.NET Framework 正则表达式](regular-expressions.md)

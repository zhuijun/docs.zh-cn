---
title: 如何搜索字符串（C# 指南）
ms.date: 02/21/2018
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with String methods
- strings [C#], searching with regular expressions
ms.assetid: fb1d9a6d-598d-4a35-bd5f-b86012edcb2b
ms.openlocfilehash: f5fd61452d6f83bd035b5c6930bd09673c0ded23
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662948"
---
# <a name="how-to-search-strings"></a><span data-ttu-id="f5229-102">如何搜索字符串</span><span class="sxs-lookup"><span data-stu-id="f5229-102">How to search strings</span></span>

<span data-ttu-id="f5229-103">可以使用两种主要策略搜索字符串中的文本。</span><span class="sxs-lookup"><span data-stu-id="f5229-103">You can use two main strategies to search for text in strings.</span></span> <span data-ttu-id="f5229-104"><xref:System.String> 类的方法搜索特定文本。</span><span class="sxs-lookup"><span data-stu-id="f5229-104">Methods of the <xref:System.String> class search for specific text.</span></span> <span data-ttu-id="f5229-105">正则表达式搜索文本中的模式。</span><span class="sxs-lookup"><span data-stu-id="f5229-105">Regular expressions search for patterns in text.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="f5229-106">[string](../language-reference/builtin-types/reference-types.md#the-string-type) 类型是 <xref:System.String?displayProperty=nameWithType> 类的别名，可提供多种有效方法用于搜索字符串的内容。</span><span class="sxs-lookup"><span data-stu-id="f5229-106">The [string](../language-reference/builtin-types/reference-types.md#the-string-type) type, which is an alias for the <xref:System.String?displayProperty=nameWithType> class, provides a number of useful methods for searching the contents of a string.</span></span> <span data-ttu-id="f5229-107">其中包括 <xref:System.String.Contains%2A>、<xref:System.String.StartsWith%2A>、<xref:System.String.EndsWith%2A>、<xref:System.String.IndexOf%2A> 以及 <xref:System.String.LastIndexOf%2A>。</span><span class="sxs-lookup"><span data-stu-id="f5229-107">Among them are <xref:System.String.Contains%2A>, <xref:System.String.StartsWith%2A>, <xref:System.String.EndsWith%2A>, <xref:System.String.IndexOf%2A>, <xref:System.String.LastIndexOf%2A>.</span></span> <span data-ttu-id="f5229-108"><xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> 类具备丰富的词汇来对文本中的模式进行搜索。</span><span class="sxs-lookup"><span data-stu-id="f5229-108">The <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> class provides a rich vocabulary to search for patterns in text.</span></span> <span data-ttu-id="f5229-109">你将在本文中了解这些技术以及如何选择符合需求的最佳方法。</span><span class="sxs-lookup"><span data-stu-id="f5229-109">In this article, you learn these techniques and how to choose the best method for your needs.</span></span>

## <a name="does-a-string-contain-text"></a><span data-ttu-id="f5229-110">字符串包含文本吗？</span><span class="sxs-lookup"><span data-stu-id="f5229-110">Does a string contain text?</span></span>

<span data-ttu-id="f5229-111"><xref:System.String.Contains%2A?displayProperty=nameWithType>、<xref:System.String.StartsWith%2A?displayProperty=nameWithType> 和 <xref:System.String.EndsWith%2A?displayProperty=nameWithType> 方法搜索字符串中的特定文本。</span><span class="sxs-lookup"><span data-stu-id="f5229-111">The <xref:System.String.Contains%2A?displayProperty=nameWithType>, <xref:System.String.StartsWith%2A?displayProperty=nameWithType> and <xref:System.String.EndsWith%2A?displayProperty=nameWithType> methods search a string for specific text.</span></span> <span data-ttu-id="f5229-112">下面的示例显示了每一个方法以及使用不区分大小写的搜索的差异：</span><span class="sxs-lookup"><span data-stu-id="f5229-112">The following example shows each of these methods and a variation that uses a case insensitive search:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs" id="Snippet1":::

<span data-ttu-id="f5229-113">前面的示例演示了使用这些方法的重点。</span><span class="sxs-lookup"><span data-stu-id="f5229-113">The preceding example demonstrates an important point for using these methods.</span></span> <span data-ttu-id="f5229-114">默认情况下搜索是区分大小写的。</span><span class="sxs-lookup"><span data-stu-id="f5229-114">Searches are **case-sensitive** by default.</span></span> <span data-ttu-id="f5229-115">使用 <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> 枚举值指定区分大小写的搜索。</span><span class="sxs-lookup"><span data-stu-id="f5229-115">You use the <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> enum value to specify a case insensitive search.</span></span>

## <a name="where-does-the-sought-text-occur-in-a-string"></a><span data-ttu-id="f5229-116">寻找的文本出现在字符串的什么位置？</span><span class="sxs-lookup"><span data-stu-id="f5229-116">Where does the sought text occur in a string?</span></span>

<span data-ttu-id="f5229-117"><xref:System.String.IndexOf%2A> 和 <xref:System.String.LastIndexOf%2A> 方法也搜索字符串中的文本。</span><span class="sxs-lookup"><span data-stu-id="f5229-117">The <xref:System.String.IndexOf%2A> and <xref:System.String.LastIndexOf%2A> methods also search for text in strings.</span></span> <span data-ttu-id="f5229-118">这些方法返回查找到的文本的位置。</span><span class="sxs-lookup"><span data-stu-id="f5229-118">These methods return the location of the text being sought.</span></span> <span data-ttu-id="f5229-119">如果未找到文本，则返回 `-1`。</span><span class="sxs-lookup"><span data-stu-id="f5229-119">If the text isn't found, they return `-1`.</span></span> <span data-ttu-id="f5229-120">下面的示例显示“methods”第一次出现和最后一次出现的搜索结果，并显示了它们之间的文本。</span><span class="sxs-lookup"><span data-stu-id="f5229-120">The following example shows a search for the first and last occurrence of the word "methods" and displays the text in between.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs" id="Snippet2":::

## <a name="finding-specific-text-using-regular-expressions"></a><span data-ttu-id="f5229-121">使用正则表达式查找特定文本</span><span class="sxs-lookup"><span data-stu-id="f5229-121">Finding specific text using regular expressions</span></span>

<span data-ttu-id="f5229-122"><xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> 类可用于搜索字符串。</span><span class="sxs-lookup"><span data-stu-id="f5229-122">The <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> class can be used to search strings.</span></span> <span data-ttu-id="f5229-123">这些搜索的范围可以从简单的内容到复杂的文本模式。</span><span class="sxs-lookup"><span data-stu-id="f5229-123">These searches can range in complexity from simple to complicated text patterns.</span></span>

<span data-ttu-id="f5229-124">下面的代码示例在一个句子中搜索了“the”或“their”（忽略大小写）。</span><span class="sxs-lookup"><span data-stu-id="f5229-124">The following code example searches for the word "the" or "their" in a sentence, ignoring case.</span></span> <span data-ttu-id="f5229-125">静态方法 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> 执行此次搜索。</span><span class="sxs-lookup"><span data-stu-id="f5229-125">The static method <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> performs the search.</span></span> <span data-ttu-id="f5229-126">你向它提供要搜索的字符串以及搜索模式。</span><span class="sxs-lookup"><span data-stu-id="f5229-126">You give it the string to search and a search pattern.</span></span> <span data-ttu-id="f5229-127">在这种情况下，第三个参数指定不区分大小写的搜索。</span><span class="sxs-lookup"><span data-stu-id="f5229-127">In this case, a third argument specifies case-insensitive search.</span></span> <span data-ttu-id="f5229-128">有关详细信息，请参阅 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="f5229-128">For more information, see <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="f5229-129">搜索模式描述你所搜索的文本。</span><span class="sxs-lookup"><span data-stu-id="f5229-129">The search pattern describes the text you search for.</span></span> <span data-ttu-id="f5229-130">下表描述搜索模式的每个元素。</span><span class="sxs-lookup"><span data-stu-id="f5229-130">The following table describes each element of the search pattern.</span></span> <span data-ttu-id="f5229-131">（下表使用单个 `\`，它在 C# 字符串中必须转义为 `\\`）。</span><span class="sxs-lookup"><span data-stu-id="f5229-131">(The table below uses the single `\` which must be escaped as `\\` in a C# string).</span></span>

| <span data-ttu-id="f5229-132">模式</span><span class="sxs-lookup"><span data-stu-id="f5229-132">Pattern</span></span>  | <span data-ttu-id="f5229-133">含义</span><span class="sxs-lookup"><span data-stu-id="f5229-133">Meaning</span></span>                          |
|----------|----------------------------------|
| `the`    | <span data-ttu-id="f5229-134">匹配文本“the”</span><span class="sxs-lookup"><span data-stu-id="f5229-134">match the text "the"</span></span>             |
| `(eir)?` | <span data-ttu-id="f5229-135">匹配 0 个或 1 个“eir”</span><span class="sxs-lookup"><span data-stu-id="f5229-135">match 0 or 1 occurrence of "eir"</span></span> |
| `\s`     | <span data-ttu-id="f5229-136">与空白符匹配</span><span class="sxs-lookup"><span data-stu-id="f5229-136">match a white-space character</span></span>    |

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs" id="Snippet3":::

> [!TIP]
> <span data-ttu-id="f5229-137">搜索精确的字符串时，`string` 方法通常是更好的选择。</span><span class="sxs-lookup"><span data-stu-id="f5229-137">The `string` methods are usually better choices when you are searching for an exact string.</span></span> <span data-ttu-id="f5229-138">搜索源字符串中的一些模式时，正则表达式更适用。</span><span class="sxs-lookup"><span data-stu-id="f5229-138">Regular expressions are better when you are searching for some pattern in a source string.</span></span>

## <a name="does-a-string-follow-a-pattern"></a><span data-ttu-id="f5229-139">字符串是否遵循模式？</span><span class="sxs-lookup"><span data-stu-id="f5229-139">Does a string follow a pattern?</span></span>

<span data-ttu-id="f5229-140">以下代码使用正则表达式验证数组中每个字符串的格式。</span><span class="sxs-lookup"><span data-stu-id="f5229-140">The following code uses regular expressions to validate the format of each string in an array.</span></span> <span data-ttu-id="f5229-141">验证要求每个字符串具备电话号码的形式：用短划线分隔成三组数字，前两组包含 3 个数字，而第三组包含 4 个数字。</span><span class="sxs-lookup"><span data-stu-id="f5229-141">The validation requires that each string have the form of a telephone number in which three groups of digits are separated by dashes, the first two groups contain three digits, and the third group contains four digits.</span></span> <span data-ttu-id="f5229-142">搜索模式采用正则表达式 `^\\d{3}-\\d{3}-\\d{4}$`。</span><span class="sxs-lookup"><span data-stu-id="f5229-142">The search pattern uses the regular expression `^\\d{3}-\\d{3}-\\d{4}$`.</span></span> <span data-ttu-id="f5229-143">有关更多信息，请参见[正则表达式语言 - 快速参考](../../standard/base-types/regular-expression-language-quick-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="f5229-143">For more information, see [Regular Expression Language - Quick Reference](../../standard/base-types/regular-expression-language-quick-reference.md).</span></span>

| <span data-ttu-id="f5229-144">模式</span><span class="sxs-lookup"><span data-stu-id="f5229-144">Pattern</span></span> | <span data-ttu-id="f5229-145">含义</span><span class="sxs-lookup"><span data-stu-id="f5229-145">Meaning</span></span>                             |
|---------|-------------------------------------|
| `^`     | <span data-ttu-id="f5229-146">匹配字符串的开头部分</span><span class="sxs-lookup"><span data-stu-id="f5229-146">matches the beginning of the string</span></span> |
| `\d{3}` | <span data-ttu-id="f5229-147">完全匹配 3 位字符</span><span class="sxs-lookup"><span data-stu-id="f5229-147">matches exactly 3 digit characters</span></span>  |
| `-`     | <span data-ttu-id="f5229-148">匹配字符“-”</span><span class="sxs-lookup"><span data-stu-id="f5229-148">matches the '-' character</span></span>           |
| `\d{3}` | <span data-ttu-id="f5229-149">完全匹配 3 位字符</span><span class="sxs-lookup"><span data-stu-id="f5229-149">matches exactly 3 digit characters</span></span>  |
| `-`     | <span data-ttu-id="f5229-150">匹配字符“-”</span><span class="sxs-lookup"><span data-stu-id="f5229-150">matches the '-' character</span></span>           |
| `\d{4}` | <span data-ttu-id="f5229-151">完全匹配 4 位字符</span><span class="sxs-lookup"><span data-stu-id="f5229-151">matches exactly 4 digit characters</span></span>  |
| `$`     | <span data-ttu-id="f5229-152">匹配字符串的结尾部分</span><span class="sxs-lookup"><span data-stu-id="f5229-152">matches the end of the string</span></span>       |

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs" id="Snippet4":::

<span data-ttu-id="f5229-153">此单个搜索模式匹配很多有效字符串。</span><span class="sxs-lookup"><span data-stu-id="f5229-153">This single search pattern matches many valid strings.</span></span> <span data-ttu-id="f5229-154">正则表达式更适用于搜索或验证模式，而不是单个文本字符串。</span><span class="sxs-lookup"><span data-stu-id="f5229-154">Regular expressions are better to search for or validate against a pattern, rather than a single text string.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5229-155">请参阅</span><span class="sxs-lookup"><span data-stu-id="f5229-155">See also</span></span>

- [<span data-ttu-id="f5229-156">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="f5229-156">C# programming guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="f5229-157">字符串</span><span class="sxs-lookup"><span data-stu-id="f5229-157">Strings</span></span>](../programming-guide/strings/index.md)
- [<span data-ttu-id="f5229-158">LINQ 和字符串</span><span class="sxs-lookup"><span data-stu-id="f5229-158">LINQ and strings</span></span>](../programming-guide/concepts/linq/linq-and-strings.md)
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- [<span data-ttu-id="f5229-159">.NET Framework 正则表达式</span><span class="sxs-lookup"><span data-stu-id="f5229-159">.NET Framework regular expressions</span></span>](../../standard/base-types/regular-expressions.md)
- [<span data-ttu-id="f5229-160">正则表达式语言 - 快速参考</span><span class="sxs-lookup"><span data-stu-id="f5229-160">Regular expression language - quick reference</span></span>](../../standard/base-types/regular-expression-language-quick-reference.md)
- [<span data-ttu-id="f5229-161">有关使用 .NET 中字符串的最佳做法</span><span class="sxs-lookup"><span data-stu-id="f5229-161">Best practices for using strings in .NET</span></span>](../../standard/base-types/best-practices-strings.md)

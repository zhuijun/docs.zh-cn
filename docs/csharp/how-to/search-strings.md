---
title: 如何搜索字符串（C# 指南）
description: 了解有关使用 C# 在字符串中搜索文本的两种策略。 字符串类方法搜索特定文本。 正则表达式搜索文本中的模式。
ms.date: 02/21/2018
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with String methods
- strings [C#], searching with regular expressions
ms.assetid: fb1d9a6d-598d-4a35-bd5f-b86012edcb2b
ms.openlocfilehash: 17bf6e080542242d30791b70ffbf00b05f03a7b0
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/20/2020
ms.locfileid: "86473989"
---
# <a name="how-to-search-strings"></a><span data-ttu-id="87694-105">如何搜索字符串</span><span class="sxs-lookup"><span data-stu-id="87694-105">How to search strings</span></span>

<span data-ttu-id="87694-106">可以使用两种主要策略搜索字符串中的文本。</span><span class="sxs-lookup"><span data-stu-id="87694-106">You can use two main strategies to search for text in strings.</span></span> <span data-ttu-id="87694-107"><xref:System.String> 类的方法搜索特定文本。</span><span class="sxs-lookup"><span data-stu-id="87694-107">Methods of the <xref:System.String> class search for specific text.</span></span> <span data-ttu-id="87694-108">正则表达式搜索文本中的模式。</span><span class="sxs-lookup"><span data-stu-id="87694-108">Regular expressions search for patterns in text.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="87694-109">[string](../language-reference/builtin-types/reference-types.md#the-string-type) 类型是 <xref:System.String?displayProperty=nameWithType> 类的别名，可提供多种有效方法用于搜索字符串的内容。</span><span class="sxs-lookup"><span data-stu-id="87694-109">The [string](../language-reference/builtin-types/reference-types.md#the-string-type) type, which is an alias for the <xref:System.String?displayProperty=nameWithType> class, provides a number of useful methods for searching the contents of a string.</span></span> <span data-ttu-id="87694-110">其中包括 <xref:System.String.Contains%2A>、<xref:System.String.StartsWith%2A>、<xref:System.String.EndsWith%2A>、<xref:System.String.IndexOf%2A> 以及 <xref:System.String.LastIndexOf%2A>。</span><span class="sxs-lookup"><span data-stu-id="87694-110">Among them are <xref:System.String.Contains%2A>, <xref:System.String.StartsWith%2A>, <xref:System.String.EndsWith%2A>, <xref:System.String.IndexOf%2A>, <xref:System.String.LastIndexOf%2A>.</span></span> <span data-ttu-id="87694-111"><xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> 类具备丰富的词汇来对文本中的模式进行搜索。</span><span class="sxs-lookup"><span data-stu-id="87694-111">The <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> class provides a rich vocabulary to search for patterns in text.</span></span> <span data-ttu-id="87694-112">你将在本文中了解这些技术以及如何选择符合需求的最佳方法。</span><span class="sxs-lookup"><span data-stu-id="87694-112">In this article, you learn these techniques and how to choose the best method for your needs.</span></span>

## <a name="does-a-string-contain-text"></a><span data-ttu-id="87694-113">字符串包含文本吗？</span><span class="sxs-lookup"><span data-stu-id="87694-113">Does a string contain text?</span></span>

<span data-ttu-id="87694-114"><xref:System.String.Contains%2A?displayProperty=nameWithType>、<xref:System.String.StartsWith%2A?displayProperty=nameWithType> 和 <xref:System.String.EndsWith%2A?displayProperty=nameWithType> 方法搜索字符串中的特定文本。</span><span class="sxs-lookup"><span data-stu-id="87694-114">The <xref:System.String.Contains%2A?displayProperty=nameWithType>, <xref:System.String.StartsWith%2A?displayProperty=nameWithType>, and <xref:System.String.EndsWith%2A?displayProperty=nameWithType> methods search a string for specific text.</span></span> <span data-ttu-id="87694-115">下面的示例显示了每一个方法以及使用不区分大小写的搜索的差异：</span><span class="sxs-lookup"><span data-stu-id="87694-115">The following example shows each of these methods and a variation that uses a case-insensitive search:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs" id="Snippet1":::

<span data-ttu-id="87694-116">前面的示例演示了使用这些方法的重点。</span><span class="sxs-lookup"><span data-stu-id="87694-116">The preceding example demonstrates an important point for using these methods.</span></span> <span data-ttu-id="87694-117">默认情况下搜索是区分大小写的。</span><span class="sxs-lookup"><span data-stu-id="87694-117">Searches are **case-sensitive** by default.</span></span> <span data-ttu-id="87694-118">使用 <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> 枚举值指定区分大小写的搜索。</span><span class="sxs-lookup"><span data-stu-id="87694-118">You use the <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> enumeration value to specify a case-insensitive search.</span></span>

## <a name="where-does-the-sought-text-occur-in-a-string"></a><span data-ttu-id="87694-119">寻找的文本出现在字符串的什么位置？</span><span class="sxs-lookup"><span data-stu-id="87694-119">Where does the sought text occur in a string?</span></span>

<span data-ttu-id="87694-120"><xref:System.String.IndexOf%2A> 和 <xref:System.String.LastIndexOf%2A> 方法也搜索字符串中的文本。</span><span class="sxs-lookup"><span data-stu-id="87694-120">The <xref:System.String.IndexOf%2A> and <xref:System.String.LastIndexOf%2A> methods also search for text in strings.</span></span> <span data-ttu-id="87694-121">这些方法返回查找到的文本的位置。</span><span class="sxs-lookup"><span data-stu-id="87694-121">These methods return the location of the text being sought.</span></span> <span data-ttu-id="87694-122">如果未找到文本，则返回 `-1`。</span><span class="sxs-lookup"><span data-stu-id="87694-122">If the text isn't found, they return `-1`.</span></span> <span data-ttu-id="87694-123">下面的示例显示“methods”第一次出现和最后一次出现的搜索结果，并显示了它们之间的文本。</span><span class="sxs-lookup"><span data-stu-id="87694-123">The following example shows a search for the first and last occurrence of the word "methods" and displays the text in between.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs" id="Snippet2":::

## <a name="finding-specific-text-using-regular-expressions"></a><span data-ttu-id="87694-124">使用正则表达式查找特定文本</span><span class="sxs-lookup"><span data-stu-id="87694-124">Finding specific text using regular expressions</span></span>

<span data-ttu-id="87694-125"><xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> 类可用于搜索字符串。</span><span class="sxs-lookup"><span data-stu-id="87694-125">The <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> class can be used to search strings.</span></span> <span data-ttu-id="87694-126">这些搜索的范围可以从简单的内容到复杂的文本模式。</span><span class="sxs-lookup"><span data-stu-id="87694-126">These searches can range in complexity from simple to complicated text patterns.</span></span>

<span data-ttu-id="87694-127">下面的代码示例在一个句子中搜索了“the”或“their”（忽略大小写）。</span><span class="sxs-lookup"><span data-stu-id="87694-127">The following code example searches for the word "the" or "their" in a sentence, ignoring case.</span></span> <span data-ttu-id="87694-128">静态方法 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> 执行此次搜索。</span><span class="sxs-lookup"><span data-stu-id="87694-128">The static method <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> performs the search.</span></span> <span data-ttu-id="87694-129">你向它提供要搜索的字符串以及搜索模式。</span><span class="sxs-lookup"><span data-stu-id="87694-129">You give it the string to search and a search pattern.</span></span> <span data-ttu-id="87694-130">在这种情况下，第三个参数指定不区分大小写的搜索。</span><span class="sxs-lookup"><span data-stu-id="87694-130">In this case, a third argument specifies case-insensitive search.</span></span> <span data-ttu-id="87694-131">有关详细信息，请参阅 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="87694-131">For more information, see <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="87694-132">搜索模式描述你所搜索的文本。</span><span class="sxs-lookup"><span data-stu-id="87694-132">The search pattern describes the text you search for.</span></span> <span data-ttu-id="87694-133">下表描述搜索模式的每个元素。</span><span class="sxs-lookup"><span data-stu-id="87694-133">The following table describes each element of the search pattern.</span></span> <span data-ttu-id="87694-134">（下表使用单个 `\`，它在 C# 字符串中必须转义为 `\\`）。</span><span class="sxs-lookup"><span data-stu-id="87694-134">(The table below uses the single `\`, which must be escaped as `\\` in a C# string).</span></span>

| <span data-ttu-id="87694-135">模式</span><span class="sxs-lookup"><span data-stu-id="87694-135">Pattern</span></span>  | <span data-ttu-id="87694-136">含义</span><span class="sxs-lookup"><span data-stu-id="87694-136">Meaning</span></span>                          |
|----------|----------------------------------|
| `the`    | <span data-ttu-id="87694-137">匹配文本“the”</span><span class="sxs-lookup"><span data-stu-id="87694-137">match the text "the"</span></span>             |
| `(eir)?` | <span data-ttu-id="87694-138">匹配 0 个或 1 个“eir”</span><span class="sxs-lookup"><span data-stu-id="87694-138">match 0 or 1 occurrence of "eir"</span></span> |
| `\s`     | <span data-ttu-id="87694-139">与空白符匹配</span><span class="sxs-lookup"><span data-stu-id="87694-139">match a white-space character</span></span>    |

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs" id="Snippet3":::

> [!TIP]
> <span data-ttu-id="87694-140">搜索精确的字符串时，`string` 方法通常是更好的选择。</span><span class="sxs-lookup"><span data-stu-id="87694-140">The `string` methods are usually better choices when you are searching for an exact string.</span></span> <span data-ttu-id="87694-141">搜索源字符串中的一些模式时，正则表达式更适用。</span><span class="sxs-lookup"><span data-stu-id="87694-141">Regular expressions are better when you are searching for some pattern in a source string.</span></span>

## <a name="does-a-string-follow-a-pattern"></a><span data-ttu-id="87694-142">字符串是否遵循模式？</span><span class="sxs-lookup"><span data-stu-id="87694-142">Does a string follow a pattern?</span></span>

<span data-ttu-id="87694-143">以下代码使用正则表达式验证数组中每个字符串的格式。</span><span class="sxs-lookup"><span data-stu-id="87694-143">The following code uses regular expressions to validate the format of each string in an array.</span></span> <span data-ttu-id="87694-144">验证要求每个字符串具备电话号码的形式：用短划线分隔成三组数字，前两组包含 3 个数字，而第三组包含 4 个数字。</span><span class="sxs-lookup"><span data-stu-id="87694-144">The validation requires that each string have the form of a telephone number in which three groups of digits are separated by dashes, the first two groups contain three digits, and the third group contains four digits.</span></span> <span data-ttu-id="87694-145">搜索模式采用正则表达式 `^\\d{3}-\\d{3}-\\d{4}$`。</span><span class="sxs-lookup"><span data-stu-id="87694-145">The search pattern uses the regular expression `^\\d{3}-\\d{3}-\\d{4}$`.</span></span> <span data-ttu-id="87694-146">有关更多信息，请参见[正则表达式语言 - 快速参考](../../standard/base-types/regular-expression-language-quick-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="87694-146">For more information, see [Regular Expression Language - Quick Reference](../../standard/base-types/regular-expression-language-quick-reference.md).</span></span>

| <span data-ttu-id="87694-147">模式</span><span class="sxs-lookup"><span data-stu-id="87694-147">Pattern</span></span> | <span data-ttu-id="87694-148">含义</span><span class="sxs-lookup"><span data-stu-id="87694-148">Meaning</span></span>                             |
|---------|-------------------------------------|
| `^`     | <span data-ttu-id="87694-149">匹配字符串的开头部分</span><span class="sxs-lookup"><span data-stu-id="87694-149">matches the beginning of the string</span></span> |
| `\d{3}` | <span data-ttu-id="87694-150">完全匹配 3 位字符</span><span class="sxs-lookup"><span data-stu-id="87694-150">matches exactly 3 digit characters</span></span>  |
| `-`     | <span data-ttu-id="87694-151">匹配字符“-”</span><span class="sxs-lookup"><span data-stu-id="87694-151">matches the '-' character</span></span>           |
| `\d{3}` | <span data-ttu-id="87694-152">完全匹配 3 位字符</span><span class="sxs-lookup"><span data-stu-id="87694-152">matches exactly 3 digit characters</span></span>  |
| `-`     | <span data-ttu-id="87694-153">匹配字符“-”</span><span class="sxs-lookup"><span data-stu-id="87694-153">matches the '-' character</span></span>           |
| `\d{4}` | <span data-ttu-id="87694-154">完全匹配 4 位字符</span><span class="sxs-lookup"><span data-stu-id="87694-154">matches exactly 4 digit characters</span></span>  |
| `$`     | <span data-ttu-id="87694-155">匹配字符串的结尾部分</span><span class="sxs-lookup"><span data-stu-id="87694-155">matches the end of the string</span></span>       |

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs" id="Snippet4":::

<span data-ttu-id="87694-156">此单个搜索模式匹配很多有效字符串。</span><span class="sxs-lookup"><span data-stu-id="87694-156">This single search pattern matches many valid strings.</span></span> <span data-ttu-id="87694-157">正则表达式更适用于搜索或验证模式，而不是单个文本字符串。</span><span class="sxs-lookup"><span data-stu-id="87694-157">Regular expressions are better to search for or validate against a pattern, rather than a single text string.</span></span>

## <a name="see-also"></a><span data-ttu-id="87694-158">请参阅</span><span class="sxs-lookup"><span data-stu-id="87694-158">See also</span></span>

- [<span data-ttu-id="87694-159">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="87694-159">C# programming guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="87694-160">字符串</span><span class="sxs-lookup"><span data-stu-id="87694-160">Strings</span></span>](../programming-guide/strings/index.md)
- [<span data-ttu-id="87694-161">LINQ 和字符串</span><span class="sxs-lookup"><span data-stu-id="87694-161">LINQ and strings</span></span>](../programming-guide/concepts/linq/linq-and-strings.md)
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- [<span data-ttu-id="87694-162">.NET Framework 正则表达式</span><span class="sxs-lookup"><span data-stu-id="87694-162">.NET Framework regular expressions</span></span>](../../standard/base-types/regular-expressions.md)
- [<span data-ttu-id="87694-163">正则表达式语言 - 快速参考</span><span class="sxs-lookup"><span data-stu-id="87694-163">Regular expression language - quick reference</span></span>](../../standard/base-types/regular-expression-language-quick-reference.md)
- [<span data-ttu-id="87694-164">有关使用 .NET 中字符串的最佳做法</span><span class="sxs-lookup"><span data-stu-id="87694-164">Best practices for using strings in .NET</span></span>](../../standard/base-types/best-practices-strings.md)

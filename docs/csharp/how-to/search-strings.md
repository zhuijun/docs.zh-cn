---
title: 如何搜索字符串（C# 指南）
ms.date: 02/21/2018
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with String methods
- strings [C#], searching with regular expressions
ms.assetid: fb1d9a6d-598d-4a35-bd5f-b86012edcb2b
ms.openlocfilehash: f3e6d95eb4a01d48fac5b5e2c951b9c346206004
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121494"
---
# <a name="how-to-search-strings"></a><span data-ttu-id="5914e-102">如何搜索字符串</span><span class="sxs-lookup"><span data-stu-id="5914e-102">How to search strings</span></span>

<span data-ttu-id="5914e-103">可以使用两种主要策略搜索字符串中的文本。</span><span class="sxs-lookup"><span data-stu-id="5914e-103">You can use two main strategies to search for text in strings.</span></span> <span data-ttu-id="5914e-104"><xref:System.String> 类的方法搜索特定文本。</span><span class="sxs-lookup"><span data-stu-id="5914e-104">Methods of the <xref:System.String> class search for specific text.</span></span> <span data-ttu-id="5914e-105">正则表达式搜索文本中的模式。</span><span class="sxs-lookup"><span data-stu-id="5914e-105">Regular expressions search for patterns in text.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="5914e-106">[string](../language-reference/builtin-types/reference-types.md#the-string-type) 类型是 <xref:System.String?displayProperty=nameWithType> 类的别名，可提供多种有效方法用于搜索字符串的内容。</span><span class="sxs-lookup"><span data-stu-id="5914e-106">The [string](../language-reference/builtin-types/reference-types.md#the-string-type) type, which is an alias for the <xref:System.String?displayProperty=nameWithType> class, provides a number of useful methods for searching the contents of a string.</span></span> <span data-ttu-id="5914e-107">其中包括 <xref:System.String.Contains%2A>、<xref:System.String.StartsWith%2A>、<xref:System.String.EndsWith%2A>、<xref:System.String.IndexOf%2A> 以及 <xref:System.String.LastIndexOf%2A>。</span><span class="sxs-lookup"><span data-stu-id="5914e-107">Among them are <xref:System.String.Contains%2A>, <xref:System.String.StartsWith%2A>, <xref:System.String.EndsWith%2A>, <xref:System.String.IndexOf%2A>, <xref:System.String.LastIndexOf%2A>.</span></span> <span data-ttu-id="5914e-108"><xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> 类具备丰富的词汇来对文本中的模式进行搜索。</span><span class="sxs-lookup"><span data-stu-id="5914e-108">The <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> class provides a rich vocabulary to search for patterns in text.</span></span> <span data-ttu-id="5914e-109">你将在本文中了解这些技术以及如何选择符合需求的最佳方法。</span><span class="sxs-lookup"><span data-stu-id="5914e-109">In this article, you learn these techniques and how to choose the best method for your needs.</span></span>

## <a name="does-a-string-contain-text"></a><span data-ttu-id="5914e-110">字符串包含文本吗？</span><span class="sxs-lookup"><span data-stu-id="5914e-110">Does a string contain text?</span></span>

<span data-ttu-id="5914e-111"><xref:System.String.Contains%2A?displayProperty=nameWithType>、<xref:System.String.StartsWith%2A?displayProperty=nameWithType> 和 <xref:System.String.EndsWith%2A?displayProperty=nameWithType> 方法搜索字符串中的特定文本。</span><span class="sxs-lookup"><span data-stu-id="5914e-111">The <xref:System.String.Contains%2A?displayProperty=nameWithType>, <xref:System.String.StartsWith%2A?displayProperty=nameWithType> and <xref:System.String.EndsWith%2A?displayProperty=nameWithType> methods search a string for specific text.</span></span> <span data-ttu-id="5914e-112">下面的示例显示了每一个方法以及使用不区分大小写的搜索的差异：</span><span class="sxs-lookup"><span data-stu-id="5914e-112">The following example shows each of these methods and a variation that uses a case insensitive search:</span></span>

[!code-csharp-interactive[search strings using methods](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#1)]

<span data-ttu-id="5914e-113">前面的示例演示了使用这些方法的重点。</span><span class="sxs-lookup"><span data-stu-id="5914e-113">The preceding example demonstrates an important point for using these methods.</span></span> <span data-ttu-id="5914e-114">默认情况下搜索是区分大小写的。</span><span class="sxs-lookup"><span data-stu-id="5914e-114">Searches are **case-sensitive** by default.</span></span> <span data-ttu-id="5914e-115">使用 <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> 枚举值指定区分大小写的搜索。</span><span class="sxs-lookup"><span data-stu-id="5914e-115">You use the <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> enum value to specify a case insensitive search.</span></span>

## <a name="where-does-the-sought-text-occur-in-a-string"></a><span data-ttu-id="5914e-116">寻找的文本出现在字符串的什么位置？</span><span class="sxs-lookup"><span data-stu-id="5914e-116">Where does the sought text occur in a string?</span></span>

<span data-ttu-id="5914e-117"><xref:System.String.IndexOf%2A> 和 <xref:System.String.LastIndexOf%2A> 方法也搜索字符串中的文本。</span><span class="sxs-lookup"><span data-stu-id="5914e-117">The <xref:System.String.IndexOf%2A> and <xref:System.String.LastIndexOf%2A> methods also search for text in strings.</span></span> <span data-ttu-id="5914e-118">这些方法返回查找到的文本的位置。</span><span class="sxs-lookup"><span data-stu-id="5914e-118">These methods return the location of the text being sought.</span></span> <span data-ttu-id="5914e-119">如果未找到文本，则返回 `-1`。</span><span class="sxs-lookup"><span data-stu-id="5914e-119">If the text isn't found, they return `-1`.</span></span> <span data-ttu-id="5914e-120">下面的示例显示“methods”第一次出现和最后一次出现的搜索结果，并显示了它们之间的文本。</span><span class="sxs-lookup"><span data-stu-id="5914e-120">The following example shows a search for the first and last occurrence of the word "methods" and displays the text in between.</span></span>
  
[!code-csharp-interactive[search strings for indices](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#2)]

## <a name="finding-specific-text-using-regular-expressions"></a><span data-ttu-id="5914e-121">使用正则表达式查找特定文本</span><span class="sxs-lookup"><span data-stu-id="5914e-121">Finding specific text using regular expressions</span></span>

<span data-ttu-id="5914e-122"><xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> 类可用于搜索字符串。</span><span class="sxs-lookup"><span data-stu-id="5914e-122">The <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> class can be used to search strings.</span></span> <span data-ttu-id="5914e-123">这些搜索的范围可以从简单的内容到复杂的文本模式。</span><span class="sxs-lookup"><span data-stu-id="5914e-123">These searches can range in complexity from simple to complicated text patterns.</span></span>

<span data-ttu-id="5914e-124">下面的代码示例在一个句子中搜索了“the”或“their”（忽略大小写）。</span><span class="sxs-lookup"><span data-stu-id="5914e-124">The following code example searches for the word "the" or "their" in a sentence, ignoring case.</span></span> <span data-ttu-id="5914e-125">静态方法 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> 执行此次搜索。</span><span class="sxs-lookup"><span data-stu-id="5914e-125">The static method <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> performs the search.</span></span> <span data-ttu-id="5914e-126">你向它提供要搜索的字符串以及搜索模式。</span><span class="sxs-lookup"><span data-stu-id="5914e-126">You give it the string to search and a search pattern.</span></span> <span data-ttu-id="5914e-127">在这种情况下，第三个参数指定不区分大小写的搜索。</span><span class="sxs-lookup"><span data-stu-id="5914e-127">In this case, a third argument specifies case-insensitive search.</span></span> <span data-ttu-id="5914e-128">有关详细信息，请参阅 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="5914e-128">For more information, see <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.</span></span>  

<span data-ttu-id="5914e-129">搜索模式描述你所搜索的文本。</span><span class="sxs-lookup"><span data-stu-id="5914e-129">The search pattern describes the text you search for.</span></span> <span data-ttu-id="5914e-130">下表描述搜索模式的每个元素。</span><span class="sxs-lookup"><span data-stu-id="5914e-130">The following table describes each element of the search pattern.</span></span> <span data-ttu-id="5914e-131">（下表使用单个 `\`，它在 C# 字符串中必须转义为 `\\`）。</span><span class="sxs-lookup"><span data-stu-id="5914e-131">(The table below uses the single `\` which must be escaped as `\\` in a C# string).</span></span>

| <span data-ttu-id="5914e-132">pattern</span><span class="sxs-lookup"><span data-stu-id="5914e-132">pattern</span></span>  | <span data-ttu-id="5914e-133">含义</span><span class="sxs-lookup"><span data-stu-id="5914e-133">Meaning</span></span>     |
| -------- |-------------|
| <span data-ttu-id="5914e-134">the</span><span class="sxs-lookup"><span data-stu-id="5914e-134">the</span></span>      | <span data-ttu-id="5914e-135">匹配文本“the”</span><span class="sxs-lookup"><span data-stu-id="5914e-135">match the text "the"</span></span> |
| <span data-ttu-id="5914e-136">(eir)?</span><span class="sxs-lookup"><span data-stu-id="5914e-136">(eir)?</span></span>   | <span data-ttu-id="5914e-137">匹配 0 个或 1 个“eir”</span><span class="sxs-lookup"><span data-stu-id="5914e-137">match 0 or 1 occurrence of "eir"</span></span> |
| <span data-ttu-id="5914e-138">\s</span><span class="sxs-lookup"><span data-stu-id="5914e-138">\s</span></span>       | <span data-ttu-id="5914e-139">与空白符匹配</span><span class="sxs-lookup"><span data-stu-id="5914e-139">match a white-space character</span></span>    |
  
[!code-csharp-interactive[Search using regular expressions](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#3)]
  
> [!TIP]
> <span data-ttu-id="5914e-140">搜索精确的字符串时，`string` 方法通常是更好的选择。</span><span class="sxs-lookup"><span data-stu-id="5914e-140">The `string` methods are usually better choices when you are searching for an exact string.</span></span> <span data-ttu-id="5914e-141">搜索源字符串中的一些模式时，正则表达式更适用。</span><span class="sxs-lookup"><span data-stu-id="5914e-141">Regular expressions are better when you are searching for some pattern in a source string.</span></span>

## <a name="does-a-string-follow-a-pattern"></a><span data-ttu-id="5914e-142">字符串是否遵循模式？</span><span class="sxs-lookup"><span data-stu-id="5914e-142">Does a string follow a pattern?</span></span>

<span data-ttu-id="5914e-143">以下代码使用正则表达式验证数组中每个字符串的格式。</span><span class="sxs-lookup"><span data-stu-id="5914e-143">The following code uses regular expressions to validate the format of each string in an array.</span></span> <span data-ttu-id="5914e-144">验证要求每个字符串具备电话号码的形式：用短划线分隔成三组数字，前两组包含 3 个数字，而第三组包含 4 个数字。</span><span class="sxs-lookup"><span data-stu-id="5914e-144">The validation requires that each string have the form of a telephone number in which three groups of digits are separated by dashes, the first two groups contain three digits, and the third group contains four digits.</span></span> <span data-ttu-id="5914e-145">搜索模式采用正则表达式 `^\\d{3}-\\d{3}-\\d{4}$`。</span><span class="sxs-lookup"><span data-stu-id="5914e-145">The search pattern uses the regular expression `^\\d{3}-\\d{3}-\\d{4}$`.</span></span> <span data-ttu-id="5914e-146">有关更多信息，请参见[正则表达式语言 - 快速参考](../../standard/base-types/regular-expression-language-quick-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="5914e-146">For more information, see [Regular Expression Language - Quick Reference](../../standard/base-types/regular-expression-language-quick-reference.md).</span></span>

| <span data-ttu-id="5914e-147">pattern</span><span class="sxs-lookup"><span data-stu-id="5914e-147">pattern</span></span>  | <span data-ttu-id="5914e-148">含义</span><span class="sxs-lookup"><span data-stu-id="5914e-148">Meaning</span></span>                             |
| -------- |-------------------------------------|
| ^        | <span data-ttu-id="5914e-149">匹配字符串的开头部分</span><span class="sxs-lookup"><span data-stu-id="5914e-149">matches the beginning of the string</span></span> |
| <span data-ttu-id="5914e-150">\d{3}</span><span class="sxs-lookup"><span data-stu-id="5914e-150">\d{3}</span></span>    | <span data-ttu-id="5914e-151">完全匹配 3 位字符</span><span class="sxs-lookup"><span data-stu-id="5914e-151">matches exactly 3 digit characters</span></span>  |
| -        | <span data-ttu-id="5914e-152">匹配字符“-”</span><span class="sxs-lookup"><span data-stu-id="5914e-152">matches the '-' character</span></span>           |
| <span data-ttu-id="5914e-153">\d{3}</span><span class="sxs-lookup"><span data-stu-id="5914e-153">\d{3}</span></span>    | <span data-ttu-id="5914e-154">完全匹配 3 位字符</span><span class="sxs-lookup"><span data-stu-id="5914e-154">matches exactly 3 digit characters</span></span>  |
| -        | <span data-ttu-id="5914e-155">匹配字符“-”</span><span class="sxs-lookup"><span data-stu-id="5914e-155">matches the '-' character</span></span>           |
| <span data-ttu-id="5914e-156">\d{4}</span><span class="sxs-lookup"><span data-stu-id="5914e-156">\d{4}</span></span>    | <span data-ttu-id="5914e-157">完全匹配 4 位字符</span><span class="sxs-lookup"><span data-stu-id="5914e-157">matches exactly 4 digit characters</span></span>  |
| $        | <span data-ttu-id="5914e-158">匹配字符串的结尾部分</span><span class="sxs-lookup"><span data-stu-id="5914e-158">matches the end of the string</span></span>       |

[!code-csharp-interactive[csProgGuideStrings#4](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#4)]

<span data-ttu-id="5914e-159">此单个搜索模式匹配很多有效字符串。</span><span class="sxs-lookup"><span data-stu-id="5914e-159">This single search pattern matches many valid strings.</span></span> <span data-ttu-id="5914e-160">正则表达式更适用于搜索或验证模式，而不是单个文本字符串。</span><span class="sxs-lookup"><span data-stu-id="5914e-160">Regular expressions are better to search for or validate against a pattern, rather than a single text string.</span></span>

<span data-ttu-id="5914e-161">可通过查看 [GitHub 存储库](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings)中的代码来尝试这些示例。</span><span class="sxs-lookup"><span data-stu-id="5914e-161">You can try these samples by looking at the code in our [GitHub repository](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="5914e-162">也可以下载这些示例的 [zip 文件](../../../samples/snippets/csharp/how-to/strings.zip)。</span><span class="sxs-lookup"><span data-stu-id="5914e-162">Or you can download the samples [as a zip file](../../../samples/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="5914e-163">请参阅</span><span class="sxs-lookup"><span data-stu-id="5914e-163">See also</span></span>

- [<span data-ttu-id="5914e-164">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="5914e-164">C# Programming Guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="5914e-165">字符串</span><span class="sxs-lookup"><span data-stu-id="5914e-165">Strings</span></span>](../programming-guide/strings/index.md)
- [<span data-ttu-id="5914e-166">LINQ 和字符串</span><span class="sxs-lookup"><span data-stu-id="5914e-166">LINQ and Strings</span></span>](../programming-guide/concepts/linq/linq-and-strings.md)
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- [<span data-ttu-id="5914e-167">.NET Framework 正则表达式</span><span class="sxs-lookup"><span data-stu-id="5914e-167">.NET Framework Regular Expressions</span></span>](../../standard/base-types/regular-expressions.md)
- [<span data-ttu-id="5914e-168">正则表达式语言 - 快速参考</span><span class="sxs-lookup"><span data-stu-id="5914e-168">Regular Expression Language - Quick Reference</span></span>](../../standard/base-types/regular-expression-language-quick-reference.md)
- [<span data-ttu-id="5914e-169">有关使用 .NET 中字符串的最佳做法</span><span class="sxs-lookup"><span data-stu-id="5914e-169">Best practices for using strings in .NET</span></span>](../../standard/base-types/best-practices-strings.md)

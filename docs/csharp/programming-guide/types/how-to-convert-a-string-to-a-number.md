---
title: 如何将字符串转换为数字 - C# 编程指南
description: 了解如何通过调用 Parse、TryParse 或 Convert 类方法，在 C# 中将字符串转换为数字。
ms.date: 02/11/2019
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
ms.openlocfilehash: 8c46117579a5b787e5d9f3f317296d33bdd1cce1
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381965"
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a><span data-ttu-id="a7a0b-103">如何将字符串转换为数字（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="a7a0b-103">How to convert a string to a number (C# Programming Guide)</span></span>

<span data-ttu-id="a7a0b-104">可以调用各种数值类型（`int`、`long`、`double` 等）中找到的 `Parse` 或 `TryParse` 方法或使用 <xref:System.Convert?displayProperty=nameWithType> 类中的方法将[字符串](../../language-reference/builtin-types/reference-types.md)转换为数字。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-104">You can convert a [string](../../language-reference/builtin-types/reference-types.md) to a number by calling the `Parse` or `TryParse` method found on the various numeric types (`int`, `long`, `double`, etc.), or by using methods in the <xref:System.Convert?displayProperty=nameWithType> class.</span></span>  
  
 <span data-ttu-id="a7a0b-105">如果有字符串，则调用 `TryParse` 方法（例如，[`int.TryParse("11", out number)`](xref:System.Int32.TryParse%2A)）或 `Parse` 方法（例如，[`var number = int.Parse("11")`](xref:System.Int32.Parse%2A)）会稍微更加高效且简单。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-105">If you have a string, it is slightly more efficient and straightforward to call a `TryParse` method (for example, [`int.TryParse("11", out number)`](xref:System.Int32.TryParse%2A)) or `Parse` method (for example, [`var number = int.Parse("11")`](xref:System.Int32.Parse%2A)).</span></span>  <span data-ttu-id="a7a0b-106">使用 <xref:System.Convert> 方法对于实现 <xref:System.IConvertible> 的常规对象更有用。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-106">Using a <xref:System.Convert> method is more useful for general objects that implement <xref:System.IConvertible>.</span></span>  
  
 <span data-ttu-id="a7a0b-107">可以对预期字符串会包含的数值类型（如 <xref:System.Int32?displayProperty=nameWithType> 类型）使用 `Parse` 或 `TryParse` 方法。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-107">You can use `Parse` or `TryParse` methods on the numeric type you expect the string contains, such as the <xref:System.Int32?displayProperty=nameWithType> type.</span></span>  <span data-ttu-id="a7a0b-108"><xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> 方法在内部使用 <xref:System.Int32.Parse%2A>。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-108">The <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> method uses <xref:System.Int32.Parse%2A> internally.</span></span>  <span data-ttu-id="a7a0b-109">`Parse` 方法返回转换后的数字；`TryParse` 方法返回 <xref:System.Boolean> 值，该值指示转换是否成功，并以 [`out` 参数](../../language-reference/keywords/out.md)形式返回转换后的数字。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-109">The `Parse` method returns the converted number; the `TryParse` method returns a <xref:System.Boolean> value that indicates whether the conversion succeeded, and returns the converted number in an [`out` parameter](../../language-reference/keywords/out.md).</span></span> <span data-ttu-id="a7a0b-110">如果字符串的格式无效，则 `Parse` 会引发异常，而 `TryParse` 会返回 `false`。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-110">If the string is not in a valid format, `Parse` throws an exception, whereas `TryParse` returns `false`.</span></span> <span data-ttu-id="a7a0b-111">调用 `Parse` 方法时，应始终使用异常处理来捕获分析操作失败时的 <xref:System.FormatException>。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-111">When calling a `Parse` method, you should always use exception handling to catch a <xref:System.FormatException> in the event that the parse operation fails.</span></span>  
  
## <a name="calling-the-parse-and-tryparse-methods"></a><span data-ttu-id="a7a0b-112">调用 Parse 和 TryParse 方法</span><span class="sxs-lookup"><span data-stu-id="a7a0b-112">Calling the Parse and TryParse methods</span></span>

<span data-ttu-id="a7a0b-113">`Parse` 和 `TryParse` 方法会忽略字符串开头和末尾的空格，但所有其他字符都必须是组成合适数值类型（`int`、`long`、`ulong`、`float`、`decimal` 等）的字符。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-113">The `Parse` and `TryParse` methods ignore white space at the beginning and at the end of the string, but all other characters must be characters that form the appropriate numeric type (`int`, `long`, `ulong`, `float`, `decimal`, etc.).</span></span>  <span data-ttu-id="a7a0b-114">如果组成数字的字符串中有任何空格，都会导致错误。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-114">Any white space within the string that forms the number causes an error.</span></span>  <span data-ttu-id="a7a0b-115">例如，可以使用 `decimal.TryParse` 分析“10”、“10.3”或“  10  ”，但不能使用此方法分析从“10X”、“1 0”（注意嵌入的空格）、“10 .3”（注意嵌入的空格）、“10e1”（`float.TryParse` 在此处适用）等中分析出 10。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-115">For example, you can use `decimal.TryParse` to parse "10", "10.3", or "  10  ", but you cannot use this method to parse 10 from "10X", "1 0" (note the embedded space), "10 .3" (note the embedded space), "10e1" (`float.TryParse` works here), and so on.</span></span> <span data-ttu-id="a7a0b-116">此外，无法成功分析值为 `null` 或 <xref:System.String.Empty?displayProperty=nameWithType> 的字符串。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-116">In addition, a string whose value is `null` or <xref:System.String.Empty?displayProperty=nameWithType> fails to parse successfully.</span></span> <span data-ttu-id="a7a0b-117">在尝试通过调用 <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> 方法分析字符串之前，可以检查字符串是否为 Null 或为空。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-117">You can check for a null or empty string before attempting to parse it by calling the <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="a7a0b-118">下面的示例演示了对 `Parse` 和 `TryParse` 的成功调用和不成功的调用。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-118">The following example demonstrates both successful and unsuccessful calls to `Parse` and `TryParse`.</span></span>  
  
[!code-csharp[Parse and TryParse](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse/program.cs)]  

<span data-ttu-id="a7a0b-119">下面的示例演示了一种分析字符串的方法，该字符串应包含前导数字字符（包括十六进制字符）和尾随的非数字字符。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-119">The following example illustrates one a approach to parsing a string that is expected to include leading numeric characters (including hexadecimal characters) and trailing non-numeric characters.</span></span> <span data-ttu-id="a7a0b-120">在调用 <xref:System.Int32.TryParse%2A> 方法之前，它从字符串的开头向新字符串分配有效字符。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-120">It assigns valid characters from the beginning of a string to a new string before calling the <xref:System.Int32.TryParse%2A> method.</span></span> <span data-ttu-id="a7a0b-121">因为要分析的字符串包含少量字符，所以本示例调用 <xref:System.String.Concat%2A?displayProperty=nameWithType> 方法将有效字符分配给新字符串。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-121">Because the strings to be parsed contain a small number of characters, the example calls the <xref:System.String.Concat%2A?displayProperty=nameWithType> method to assign valid characters to a new string.</span></span> <span data-ttu-id="a7a0b-122">对于较大的字符串，可以改用 <xref:System.Text.StringBuilder> 类。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-122">For a larger string, the <xref:System.Text.StringBuilder> class can be used instead.</span></span>
  
[!code-csharp[Removing invalid characters](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse2/program.cs)]  

## <a name="calling-the-convert-methods"></a><span data-ttu-id="a7a0b-123">调用转换方法</span><span class="sxs-lookup"><span data-stu-id="a7a0b-123">Calling the Convert methods</span></span>

<span data-ttu-id="a7a0b-124">下表列出了 <xref:System.Convert> 类中可用于将字符串转换为数字的一些方法。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-124">The following table lists some of the methods from the <xref:System.Convert> class that you can use to convert a string to a number.</span></span>  
  
|<span data-ttu-id="a7a0b-125">数值类型</span><span class="sxs-lookup"><span data-stu-id="a7a0b-125">Numeric Type</span></span>|<span data-ttu-id="a7a0b-126">方法</span><span class="sxs-lookup"><span data-stu-id="a7a0b-126">Method</span></span>|  
|------------------|------------|  
|`decimal`|<xref:System.Convert.ToDecimal%28System.String%29>|  
|`float`|<xref:System.Convert.ToSingle%28System.String%29>|  
|`double`|<xref:System.Convert.ToDouble%28System.String%29>|  
|`short`|<xref:System.Convert.ToInt16%28System.String%29>|  
|`int`|<xref:System.Convert.ToInt32%28System.String%29>|  
|`long`|<xref:System.Convert.ToInt64%28System.String%29>|  
|`ushort`|<xref:System.Convert.ToUInt16%28System.String%29>|  
|`uint`|<xref:System.Convert.ToUInt32%28System.String%29>|  
|`ulong`|<xref:System.Convert.ToUInt64%28System.String%29>|  
  
 <span data-ttu-id="a7a0b-127">下面的示例调用 <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> 方法将输入字符串转换为 [int](../../language-reference/builtin-types/integral-numeric-types.md)。该示例将捕获此方法可能引发的最常见的两个异常：<xref:System.FormatException> 和 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-127">The following example calls the <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> method to convert an input string to an [int](../../language-reference/builtin-types/integral-numeric-types.md). The example catches the two most common exceptions that can be thrown by this method, <xref:System.FormatException> and <xref:System.OverflowException>.</span></span> <span data-ttu-id="a7a0b-128">如果生成的数字可以在不超过 <xref:System.Int32.MaxValue?displayProperty=nameWithType> 的情况下递增，则示例将向结果添加 1 并显示输出。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-128">If the resulting number can be incremented without exceeding <xref:System.Int32.MaxValue?displayProperty=nameWithType>, the example adds 1 to the result and displays the output.</span></span>  
  
[!code-csharp[Parsing with Convert methods](~/samples/snippets/csharp/programming-guide/string-to-number/convert/program.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a7a0b-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="a7a0b-129">See also</span></span>

- [<span data-ttu-id="a7a0b-130">类型</span><span class="sxs-lookup"><span data-stu-id="a7a0b-130">Types</span></span>](./index.md)
- [<span data-ttu-id="a7a0b-131">如何确定字符串是否表示数值</span><span class="sxs-lookup"><span data-stu-id="a7a0b-131">How to determine whether a string represents a numeric value</span></span>](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
- [<span data-ttu-id="a7a0b-132">示例：.NET Core WinForms 格式设置实用工具 (C#)</span><span class="sxs-lookup"><span data-stu-id="a7a0b-132">Sample: .NET Core WinForms Formatting Utility (C#)</span></span>](https://docs.microsoft.com/samples/dotnet/samples/windowsforms-formatting-utility-cs)

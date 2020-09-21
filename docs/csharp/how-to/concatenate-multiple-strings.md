---
title: 如何连接多个字符串（C# 指南）
description: 可以在 C# 中通过多种方法串联字符串。 了解多种选项和进行不同选择的原因。
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: f2aae14deac967a833fb3510acdb32e0971485b5
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537478"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a><span data-ttu-id="349db-104">如何连接多个字符串（C# 指南）</span><span class="sxs-lookup"><span data-stu-id="349db-104">How to concatenate multiple strings (C# Guide)</span></span>

<span data-ttu-id="349db-105">串联是将一个字符串追加到另一字符串末尾的过程。 </span><span class="sxs-lookup"><span data-stu-id="349db-105">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="349db-106">可使用 `+` 运算符连接字符串。</span><span class="sxs-lookup"><span data-stu-id="349db-106">You concatenate strings by using the `+` operator.</span></span> <span data-ttu-id="349db-107">对于字符串文本和字符串常量，会在编译时进行串联，运行时不串联。</span><span class="sxs-lookup"><span data-stu-id="349db-107">For string literals and string constants, concatenation occurs at compile time; no run-time concatenation occurs.</span></span> <span data-ttu-id="349db-108">对于字符串变量，仅在运行时串联。</span><span class="sxs-lookup"><span data-stu-id="349db-108">For string variables, concatenation occurs only at run time.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="349db-109">以下示例通过串联将长字符串文本拆分为较短的字符串，从而提高源代码的可读性。</span><span class="sxs-lookup"><span data-stu-id="349db-109">The following example uses concatenation to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="349db-110">编译时将这些部分连接到单个字符串中。</span><span class="sxs-lookup"><span data-stu-id="349db-110">These parts are concatenated into a single string at compile time.</span></span> <span data-ttu-id="349db-111">无论涉及到多少个字符串，均不产生运行时性能开销。</span><span class="sxs-lookup"><span data-stu-id="349db-111">There is no run-time performance cost regardless of the number of strings involved.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet1":::

<span data-ttu-id="349db-112">若要连接字符串变量，可使用 `+` 或 `+=` 运算符、[字符串内插](../language-reference/tokens/interpolated.md)或 <xref:System.String.Format%2A?displayProperty=nameWithType>、<xref:System.String.Concat%2A?displayProperty=nameWithType>、<xref:System.String.Join%2A?displayProperty=nameWithType>、<xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="349db-112">To concatenate string variables, you can use the `+` or `+=` operators, [string interpolation](../language-reference/tokens/interpolated.md) or the <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="349db-113">`+` 运算符易于使用，有利于产生直观代码。</span><span class="sxs-lookup"><span data-stu-id="349db-113">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="349db-114">即使在一个语句中使用多个 `+` 运算符，字符串内容也仅会被复制一次。</span><span class="sxs-lookup"><span data-stu-id="349db-114">Even if you use several `+` operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="349db-115">以下代码演示使用 `+` 和 `+=` 运算符串联字符串的示例：</span><span class="sxs-lookup"><span data-stu-id="349db-115">The following code shows examples of using the `+` and `+=` operators to concatenate strings:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet2":::

<span data-ttu-id="349db-116">在某些表达式中，使用字符串内插进行字符串串联更简单，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="349db-116">In some expressions, it's easier to concatenate strings using string interpolation, as the following code shows:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet3":::

> [!NOTE]
> <span data-ttu-id="349db-117">在字符串串联操作中，C# 编译器将 null 字符串视为空字符串进行处理。</span><span class="sxs-lookup"><span data-stu-id="349db-117">In string concatenation operations, the C# compiler treats a null string the same as an empty string.</span></span>

<span data-ttu-id="349db-118">另一个字符串连接方法为 <xref:System.String.Format%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="349db-118">Other method to concatenate strings is <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="349db-119">此方法非常适用于从少量组件字符串生成字符串的情况。</span><span class="sxs-lookup"><span data-stu-id="349db-119">This method works well when you are building a string from a small number of component strings.</span></span>

<span data-ttu-id="349db-120">在其他情况下，可能需要将字符串合并在循环中，此时不知道要合并的源字符串的数量，而且源字符串的实际数量可能很大。</span><span class="sxs-lookup"><span data-stu-id="349db-120">In other cases, you may be combining strings in a loop where you don't know how many source strings you're combining, and the actual number of source strings may be large.</span></span> <span data-ttu-id="349db-121"><xref:System.Text.StringBuilder> 类专门用于此类方案。</span><span class="sxs-lookup"><span data-stu-id="349db-121">The <xref:System.Text.StringBuilder> class was designed for these scenarios.</span></span> <span data-ttu-id="349db-122">以下代码使用 <xref:System.Text.StringBuilder> 类的 <xref:System.Text.StringBuilder.Append%2A> 方法串联字符串。</span><span class="sxs-lookup"><span data-stu-id="349db-122">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet4":::

<span data-ttu-id="349db-123">有关详细信息，请阅读[选择字符串串联或 `StringBuilder` 类的原因](/dotnet/api/system.text.stringbuilder#the-string-and-stringbuilder-types)。</span><span class="sxs-lookup"><span data-stu-id="349db-123">You can read more about the [reasons to choose string concatenation or the `StringBuilder` class](/dotnet/api/system.text.stringbuilder#the-string-and-stringbuilder-types).</span></span>

<span data-ttu-id="349db-124">还可使用 <xref:System.String.Concat%2A?displayProperty=nameWithType> 方法联接集合中的字符串。</span><span class="sxs-lookup"><span data-stu-id="349db-124">Another option to join strings from a collection is to use <xref:System.String.Concat%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="349db-125">如果源字符串应使用分隔符分隔，请使用 <xref:System.String.Join%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="349db-125">Use <xref:System.String.Join%2A?displayProperty=nameWithType> method if source strings should be separated by a delimiter.</span></span> <span data-ttu-id="349db-126">以下代码使用这两种方法合并单词数组：</span><span class="sxs-lookup"><span data-stu-id="349db-126">The following code combines an array of words using both methods:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet5":::

<span data-ttu-id="349db-127">最后，可以使用 [LINQ](../programming-guide/concepts/linq/index.md) 和 <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> 方法联接集合中的字符串。</span><span class="sxs-lookup"><span data-stu-id="349db-127">At last, you can use [LINQ](../programming-guide/concepts/linq/index.md) and the <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> method to join strings from a collection.</span></span> <span data-ttu-id="349db-128">此方法利用 lambda 表达式合并源字符串。</span><span class="sxs-lookup"><span data-stu-id="349db-128">This method combines the source strings using a lambda expression.</span></span> <span data-ttu-id="349db-129">lambda 表达式用于将所有字符串添加到现有累积。</span><span class="sxs-lookup"><span data-stu-id="349db-129">The lambda expression does the work to add each string to the existing accumulation.</span></span> <span data-ttu-id="349db-130">下面的示例通过在数组中的每两个单词之间添加一个空格来合并一组单词：</span><span class="sxs-lookup"><span data-stu-id="349db-130">The following example combines an array of words by adding a space between each word in the array:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet6":::

## <a name="see-also"></a><span data-ttu-id="349db-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="349db-131">See also</span></span>

- <xref:System.String>
- <xref:System.Text.StringBuilder>
- [<span data-ttu-id="349db-132">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="349db-132">C# programming guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="349db-133">字符串</span><span class="sxs-lookup"><span data-stu-id="349db-133">Strings</span></span>](../programming-guide/strings/index.md)

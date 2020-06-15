---
title: 如何使用 String.Split 分析字符串（C# 指南）
description: String.Split 返回从一组分隔符中拆分的字符串数组。 这是分析字符串的一种简单方法。
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: 4f0056426fb29ec3d76093e57fa45e2046f27a4f
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662987"
---
# <a name="how-to-parse-strings-using-stringsplit-in-c"></a>如何使用 String.Split 分析字符串（C\# 指南）

<xref:System.String.Split%2A?displayProperty=nameWithType> 方法通过基于一个或多个分隔符拆分输入字符串来创建子字符串数组。 最简单的方法通常是分隔字边界上的字符串。 它也用于拆分其他特定字符或字符串上的字符串。

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

下方代码将一个常用短语拆分为一个由每个单词组成的字符串数组。

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet1":::

分隔符的每个实例都会在返回的数组中产生一个值。 连续的分隔符将生成空字符串作为返回的数组中的值。 下面的示例介绍如何创建空字符串，该示例使用空格字符作为分隔符。

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet2":::

该行为可以更容易地用逗号分隔值 (CSV) 文件之类的格式表示表格数据。 连续的逗号表示空白列。

可传递可选 <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> 参数来排除返回数组中的任何空字符串。 要对返回的集合进行更复杂的处理，可使用 [LINQ](../programming-guide/concepts/linq/index.md) 来处理结果序列。

<xref:System.String.Split%2A?displayProperty=nameWithType> 可使用多个分隔符。
以下示例使用空格、逗号、句点、冒号和制表符，所有内容均在包含这些分隔字符的数组中传递到 <xref:System.String.Split%2A>。
代码底部的循环显示返回数组中的每个单词。

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet3":::

任何分隔符的连续实例都会在输出数组中生成空字符串：

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet4":::

<xref:System.String.Split%2A?displayProperty=nameWithType> 可采用字符串数组（充当用于分析目标字符串的分隔符的字符序列，而非单个字符）。

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet5":::

## <a name="see-also"></a>请参阅

- [C# 编程指南](../programming-guide/index.md)
- [字符串](../programming-guide/strings/index.md)
- [.NET 正则表达式](../../standard/base-types/regular-expressions.md)

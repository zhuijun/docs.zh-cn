---
title: 如何查找父级的属性 (XPath-LINQ to XML) (C#)
description: 了解如何查找父元素的特性。 查看使用示例 XML 文档的代码示例。
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: 03344bb66f617970d9598c91366eb7d69514397a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303291"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a>如何查找父级的属性 (XPath-LINQ to XML) (C#)

本主题演示如何定位到父元素并查找其属性。

XPath 表达式为：

`../@id`

## <a name="example"></a>示例

此示例首先查找 `Author` 元素。 然后，查找父元素的 `id` 属性。

本示例使用下面的 XML 文档：[示例 XML 文件：图书 (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md)。

```csharp
XDocument books = XDocument.Load("Books.xml");

XElement author =
    books
    .Root
    .Element("Book")
    .Element("Author");

// LINQ to XML query
XAttribute att1 =
    author
    .Parent
    .Attribute("id");

// XPath expression
XAttribute att2 = ((IEnumerable)author.XPathEvaluate("../@id")).Cast<XAttribute>().First();

if (att1 == att2)
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
Console.WriteLine(att1);
```

该示例产生下面的输出：

```output
Results are identical
id="bk101"
```

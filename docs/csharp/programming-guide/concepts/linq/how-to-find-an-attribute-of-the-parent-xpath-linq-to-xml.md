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
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a><span data-ttu-id="b0595-104">如何查找父级的属性 (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b0595-104">How to find an attribute of the parent (XPath-LINQ to XML) (C#)</span></span>

<span data-ttu-id="b0595-105">本主题演示如何定位到父元素并查找其属性。</span><span class="sxs-lookup"><span data-stu-id="b0595-105">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>

<span data-ttu-id="b0595-106">XPath 表达式为：</span><span class="sxs-lookup"><span data-stu-id="b0595-106">The XPath expression is:</span></span>

`../@id`

## <a name="example"></a><span data-ttu-id="b0595-107">示例</span><span class="sxs-lookup"><span data-stu-id="b0595-107">Example</span></span>

<span data-ttu-id="b0595-108">此示例首先查找 `Author` 元素。</span><span class="sxs-lookup"><span data-stu-id="b0595-108">This example first finds an `Author` element.</span></span> <span data-ttu-id="b0595-109">然后，查找父元素的 `id` 属性。</span><span class="sxs-lookup"><span data-stu-id="b0595-109">It then finds the `id` attribute of the parent element.</span></span>

<span data-ttu-id="b0595-110">本示例使用下面的 XML 文档：[示例 XML 文件：图书 (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="b0595-110">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>

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

<span data-ttu-id="b0595-111">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="b0595-111">This example produces the following output:</span></span>

```output
Results are identical
id="bk101"
```

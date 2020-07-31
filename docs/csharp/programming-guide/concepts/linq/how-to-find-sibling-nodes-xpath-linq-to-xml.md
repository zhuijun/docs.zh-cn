---
title: 如何查找同级节点 (XPath-LINQ to XML) (C#)
description: 此 C# 示例比较了 XPath 与 LINQ to XML，以了解如何查找所有具有特定名称的节点同级。
ms.date: 07/20/2015
ms.assetid: e2c73d10-a8ca-4e11-b5aa-d055de285874
ms.openlocfilehash: 2936fc4ad088580a9644f79f1797e679fe877e00
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105218"
---
# <a name="how-to-find-sibling-nodes-xpath-linq-to-xml-c"></a><span data-ttu-id="c46c2-103">如何查找同级节点 (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c46c2-103">How to find sibling nodes (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="c46c2-104">您可能需要查找某一节点的具有特定名称的所有同级。</span><span class="sxs-lookup"><span data-stu-id="c46c2-104">You might want to find all siblings of a node that have a specific name.</span></span> <span data-ttu-id="c46c2-105">如果上下文节点也具有该特定名称，则生成的集合可能会包括上下文节点。</span><span class="sxs-lookup"><span data-stu-id="c46c2-105">The resulting collection might include the context node if the context node also has the specific name.</span></span>  
  
 <span data-ttu-id="c46c2-106">XPath 表达式为：</span><span class="sxs-lookup"><span data-stu-id="c46c2-106">The XPath expression is:</span></span>  
  
 `../Book`  
  
## <a name="example"></a><span data-ttu-id="c46c2-107">示例</span><span class="sxs-lookup"><span data-stu-id="c46c2-107">Example</span></span>  
 <span data-ttu-id="c46c2-108">本示例首先查找一个 `Book` 元素，然后查找名为 `Book` 的所有同级元素。</span><span class="sxs-lookup"><span data-stu-id="c46c2-108">This example first finds a `Book` element, and then finds all sibling elements named `Book`.</span></span> <span data-ttu-id="c46c2-109">生成的集合包括上下文节点。</span><span class="sxs-lookup"><span data-stu-id="c46c2-109">The resulting collection includes the context node.</span></span>  
  
 <span data-ttu-id="c46c2-110">本示例使用下面的 XML 文档：[示例 XML 文件：图书 (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="c46c2-110">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument books = XDocument.Load("Books.xml");  
  
XElement book =
    books  
    .Root  
    .Elements("Book")  
    .Skip(1)  
    .First();  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    book  
    .Parent  
    .Elements("Book");  
  
// XPath expression  
IEnumerable<XElement> list2 = book.XPathSelectElements("../Book");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="c46c2-111">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="c46c2-111">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<Book id="bk101">  
  <Author>Garghentini, Davide</Author>  
  <Title>XML Developer's Guide</Title>  
  <Genre>Computer</Genre>  
  <Price>44.95</Price>  
  <PublishDate>2000-10-01</PublishDate>  
  <Description>An in-depth look at creating applications
      with XML.</Description>  
</Book>  
<Book id="bk102">  
  <Author>Garcia, Debra</Author>  
  <Title>Midnight Rain</Title>  
  <Genre>Fantasy</Genre>  
  <Price>5.95</Price>  
  <PublishDate>2000-12-16</PublishDate>  
  <Description>A former architect battles corporate zombies,
      an evil sorceress, and her own childhood to become queen
      of the world.</Description>  
</Book>  
```  

---
title: 如何：查找同级节点 (XPath-LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 73082738-2113-4438-8545-98d5df0927cb
ms.openlocfilehash: add51249dbc7cc4d33c79fcf6f82126f6bdb5612
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364534"
---
# <a name="how-to-find-sibling-nodes-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="e87e7-102">如何查找同级节点（XPath LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="e87e7-102">How to: Find Sibling Nodes (XPath-LINQ to XML) (Visual Basic)</span></span>

<span data-ttu-id="e87e7-103">您可能需要查找某一节点的具有特定名称的所有同级。</span><span class="sxs-lookup"><span data-stu-id="e87e7-103">You might want to find all siblings of a node that have a specific name.</span></span> <span data-ttu-id="e87e7-104">如果上下文节点也具有该特定名称，则生成的集合可能会包括上下文节点。</span><span class="sxs-lookup"><span data-stu-id="e87e7-104">The resulting collection might include the context node if the context node also has the specific name.</span></span>

<span data-ttu-id="e87e7-105">XPath 表达式为：</span><span class="sxs-lookup"><span data-stu-id="e87e7-105">The XPath expression is:</span></span>

`../Book`

## <a name="example"></a><span data-ttu-id="e87e7-106">示例</span><span class="sxs-lookup"><span data-stu-id="e87e7-106">Example</span></span>

<span data-ttu-id="e87e7-107">本示例首先查找一个 `Book` 元素，然后查找名为 `Book` 的所有同级元素。</span><span class="sxs-lookup"><span data-stu-id="e87e7-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`.</span></span> <span data-ttu-id="e87e7-108">生成的集合包括上下文节点。</span><span class="sxs-lookup"><span data-stu-id="e87e7-108">The resulting collection includes the context node.</span></span>

<span data-ttu-id="e87e7-109">本示例使用以下 XML 文档：[示例 XML 文件：图书 (LINQ to XML)](sample-xml-file-books-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="e87e7-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](sample-xml-file-books-linq-to-xml.md).</span></span>

```vb
Dim books As XDocument = XDocument.Load("Books.xml")
Dim book As XElement = books.Root.<Book>.Skip(1).First()

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = book.Parent.<Book>

' XPath expression
Dim list2 As IEnumerable(Of XElement) = book.XPathSelectElements("../Book")

If list1.Count() = list2.Count() And _
        list1.Intersect(list2).Count() = list1.Count() Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
For Each el As XElement In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="e87e7-110">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="e87e7-110">This example produces the following output:</span></span>

```console
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

## <a name="see-also"></a><span data-ttu-id="e87e7-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="e87e7-111">See also</span></span>

- [<span data-ttu-id="e87e7-112">XPath 用户的 LINQ to XML （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="e87e7-112">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)

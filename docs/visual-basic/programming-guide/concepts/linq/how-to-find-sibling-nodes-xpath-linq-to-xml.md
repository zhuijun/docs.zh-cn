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
# <a name="how-to-find-sibling-nodes-xpath-linq-to-xml-visual-basic"></a>如何查找同级节点（XPath LINQ to XML）（Visual Basic）

您可能需要查找某一节点的具有特定名称的所有同级。 如果上下文节点也具有该特定名称，则生成的集合可能会包括上下文节点。

XPath 表达式为：

`../Book`

## <a name="example"></a>示例

本示例首先查找一个 `Book` 元素，然后查找名为 `Book` 的所有同级元素。 生成的集合包括上下文节点。

本示例使用以下 XML 文档：[示例 XML 文件：图书 (LINQ to XML)](sample-xml-file-books-linq-to-xml.md)。

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

该示例产生下面的输出：

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

## <a name="see-also"></a>请参阅

- [XPath 用户的 LINQ to XML （Visual Basic）](linq-to-xml-for-xpath-users.md)

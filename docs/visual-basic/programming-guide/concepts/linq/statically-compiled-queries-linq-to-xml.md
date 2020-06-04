---
title: 静态编译的查询 (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 3f4825c7-c3b0-48da-ba4e-8e97fb2a2f34
ms.openlocfilehash: f020c1ed8627df8c8386a059f0cea372e8df363e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406763"
---
# <a name="statically-compiled-queries-linq-to-xml-visual-basic"></a>静态编译的查询（LINQ to XML）（Visual Basic）

LINQ to XML 的一个最重要的性能优势（与 <xref:System.Xml.XmlDocument> 相比）为：LINQ to XML 中的查询是静态编译的，而 XPath 查询则必须在运行时进行解释。 此功能是 LINQ to XML 的内置功能，因此您不必执行额外的步骤即可利用此功能，但在这两项技术之间做出选择时了解它们的区别将很有帮助。 本主题解释了其中的区别。

## <a name="statically-compiled-queries-vs-xpath"></a>静态编译的查询与 XPath 对比

下面的示例演示如何获取具有指定名称并包含带有指定值的属性的子代元素。

以下是等效的 XPath 表达式：

```vb
//Address[@Type='Shipping']
```

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 = From el In po.Descendants("Address")
            Where el.@Type = "Shipping"

For Each el In list1
    Console.WriteLine(el)
Next
```

编译器将本示例中的查询表达式重新编写为基于方法的查询语法。 以下使用基于方法的查询语法编写的示例将生成与上一示例相同的结果：

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

<xref:System.Linq.Enumerable.Where%2A> 方法为扩展方法。 有关详细信息，请参阅[扩展方法](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)。 由于 <xref:System.Linq.Enumerable.Where%2A> 是一个扩展方法，因此会将上面的查询视为按以下形式编写的查询进行编译：

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

此示例将生成与前面两个示例完全相同的结果。 这一结果表明：这些查询已被有效地编译成静态链接的方法调用。 这与迭代器的延迟执行语义一起可提高性能。 有关迭代器的延迟执行语义的详细信息，请参阅[LINQ to XML （Visual Basic）中的延迟执行和迟缓计算](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)。

> [!NOTE]
> 这些示例代表了编译器可能编写的代码。 这些示例的实际实现可能会略有不同，但对于这些示例来说，执行的性能是相同或类似的。

## <a name="executing-xpath-expressions-with-xmldocument"></a>使用 XmlDocument 执行 XPath 表达式

下面的示例使用 <xref:System.Xml.XmlDocument> 来完成与前面的示例相同的结果：

```vb
Dim reader = Xml.XmlReader.Create("PurchaseOrders.xml")
Dim doc As New Xml.XmlDocument()
doc.Load(reader)
Dim nl As Xml.XmlNodeList = doc.SelectNodes(".//Address[@Type='Shipping']")
For Each n As Xml.XmlNode In nl
    Console.WriteLine(n.OuterXml)
Next
reader.Close()
```

此查询将返回与使用 LINQ to XML 的示例相同的输出；唯一的差别是：LINQ to XML 会缩进输出的 XML，而 <xref:System.Xml.XmlDocument> 不会。

但是，<xref:System.Xml.XmlDocument> 方法的执行性能通常不如 LINQ to XML，因为在每次调用 <xref:System.Xml.XmlNode.SelectNodes%2A> 方法时，它都必须在内部执行以下操作：

- 分析包含 XPath 表达式的字符串，并将字符串划分成多个标记。

- 验证这些标记以确保 XPath 表达式有效。

- 将表达式转换为内部表达式树。

- 循环访问节点，为基于表达式计算的结果集选择适当的节点。

与相应的 LINQ to XML 查询完成的工作相比，这需要执行非常多的工作。 特定的性能差异将因不同的查询类型而异，但一般来说，与使用 <xref:System.Xml.XmlDocument> 计算 XPath 表达式相比，LINQ to XML 查询执行的工作较少，因此会获得更好的性能。

## <a name="see-also"></a>另请参阅

- [性能（LINQ to XML）（Visual Basic）](performance-linq-to-xml.md)

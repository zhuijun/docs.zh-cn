---
title: 原子化的 XName 和 XNamespace 对象 (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 21ee7585-7df9-40b4-8c76-a12bb5f29bb3
ms.openlocfilehash: 6a94bc0f2fd8013997e233b300fa19c12671bf29
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84383684"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-visual-basic"></a>原子化的 XName 和 XNamespace 对象（LINQ to XML）（Visual Basic）

<xref:System.Xml.Linq.XName> 和 <xref:System.Xml.Linq.XNamespace> 对象进行了原子化  ；即，如果这两个对象包含相同的限定名，则它们将引用同一个对象。 这将提高查询性能：当比较两个原子化名称是否相等时，基础中间语言只需确定这两个引用是否指向同一个对象。 基础代码不必进行很耗费时间的字符串比较。

## <a name="atomization-semantics"></a>原子化语义

原子化是指如果两个 <xref:System.Xml.Linq.XName> 对象具有相同的本地名称并且位于同一个命名空间中，则它们共享相同的实例。 同样，如果两个 <xref:System.Xml.Linq.XNamespace> 对象具有相同的命名空间 URI，则它们共享同一个实例。

对于启用原子化对象的类，该类的构造函数必须是私有的，而不是公共的。 这是因为如果构造函数是公共的，则您可以创建非原子化对象。 <xref:System.Xml.Linq.XName> 和 <xref:System.Xml.Linq.XNamespace> 类实现一个隐式转换运算符，以将字符串转换为 <xref:System.Xml.Linq.XName> 或 <xref:System.Xml.Linq.XNamespace>。 这是获取这些对象的实例的方式。 不能通过使用构造函数来获得实例，因为构造函数是不可访问的。

<xref:System.Xml.Linq.XName> 和 <xref:System.Xml.Linq.XNamespace> 还实现相等运算符和不相等运算符，以确定进行比较的两个对象是否引用相同的实例。

## <a name="example"></a>示例

下面的代码创建一些 <xref:System.Xml.Linq.XElement> 对象，并演示相同的名称共享同一个实例。

```vb
Dim r1 As New XElement("Root", "data1")
Dim r2 As XElement = XElement.Parse("<Root>data2</Root>")

If DirectCast(r1.Name, Object) = DirectCast(r2.Name, Object) Then
    Console.WriteLine("r1 and r2 have names that refer to the same instance.")
Else
    Console.WriteLine("Different")
End If

Dim n As XName = "Root"

If DirectCast(n, Object) = DirectCast(r1.Name, Object) Then
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.")
Else
    Console.WriteLine("Different")
End If
```

该示例产生下面的输出：

```console
r1 and r2 have names that refer to the same instance.
The name of r1 and the name in 'n' refer to the same instance.
```

如前面所述，原子化对象的好处是：当使用某个采用 <xref:System.Xml.Linq.XName> 作为参数的轴方法时，该轴方法只需确定这两个名称引用同一个实例来选择所需的元素。

下面的示例将 <xref:System.Xml.Linq.XName> 传递给 <xref:System.Xml.Linq.XContainer.Descendants%2A> 方法调用，该调用会由于使用原子化模式而获得更好的性能。

```vb
Dim root As New XElement("Root", New XElement("C1", 1), New XElement("Z1", New XElement("C1", 2), New XElement("C1", 1)))

Dim query = From e In root.Descendants("C1") Where CInt(e) = 1e

For Each z As var In query
    Console.WriteLine(z)
Next
```

该示例产生下面的输出：

```xml
<C1>1</C1>
<C1>1</C1>
```

## <a name="see-also"></a>请参阅

- [性能（LINQ to XML）（Visual Basic）](performance-linq-to-xml.md)

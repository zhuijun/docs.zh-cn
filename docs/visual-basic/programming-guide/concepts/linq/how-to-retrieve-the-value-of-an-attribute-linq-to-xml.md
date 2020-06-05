---
title: 如何：检索属性的值 (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
ms.openlocfilehash: 48ad3c0ab079012793fd9eea89d52fc3a7b1698f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397799"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a>如何：检索特性的值（LINQ to XML）（Visual Basic）
本主题说明如何获取属性的值。 主要有两种方法：可以将 <xref:System.Xml.Linq.XAttribute> 强制转换为所需的类型；然后，显式转换运算符将元素或属性的内容转换为指定的类型。 此外，还可以使用 <xref:System.Xml.Linq.XAttribute.Value%2A> 属性。 但是，强制转换通常是更好的方法。 在检索不一定存在的属性的值时，如果将属性强制转换为可以为 null 的值类型，则代码会更易于编写。 有关此技术的示例，请参阅[如何：检索元素的值（LINQ to XML）（Visual Basic）](how-to-retrieve-the-value-of-an-element-linq-to-xml.md)。  
  
## <a name="example"></a>示例  
 在 Visual Basic 中，可以使用集成的属性 (Attribute) 属性 (Property) 来检索属性 (Attribute) 的值。  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 该示例产生下面的输出：  
  
```xml  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a>示例  
 在 Visual Basic 中，可以使用集成的属性 (Attribute) 属性 (Property) 来设置属性 (Attribute) 的值。 此外，如果使用集成的属性 (Attribute) 属性 (Property) 来设置不存在的属性 (Attribute) 的值，则会创建该属性 (Attribute)。  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 该示例产生下面的输出：  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a>示例  
 下面的示例演示在属性处于命名空间中时，如何检索属性的值。 有关详细信息，请参阅[命名空间概述（LINQ to XML）（Visual Basic）](namespaces-overview-linq-to-xml.md)。  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root aw:Attr="abcde"/>  
        Dim str As String = root.@aw:Attr  
        Console.WriteLine(str)  
    End Sub  
End Module  
```  
  
 该示例产生下面的输出：  
  
```console  
abcde  
```  
  
## <a name="see-also"></a>请参阅

- [LINQ to XML 轴 (Visual Basic)](linq-to-xml-axes.md)

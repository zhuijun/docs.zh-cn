---
title: 如何：检索元素的值 (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 76b9b2a5-b3ba-49da-ba74-82100e1bd21c
ms.openlocfilehash: b8ff44416f0fbb590119af7e11714e449185d977
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397786"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-visual-basic"></a>如何：检索元素的值（LINQ to XML）（Visual Basic）
本主题演示如何获取元素的值。 有两种主要方法可以完成此操作。 一种方法是将 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute> 强制转换为所需的类型。 然后，显式转换运算符将元素或属性的内容转换为指定的类型，并将其分配给变量。 此外，还可以使用 <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> 属性或 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> 属性。  
  
 对于 Visual Basic，最好的方法是使用 <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> 属性。  
  
## <a name="example"></a>示例  
 若要检索元素的值，只需将 <xref:System.Xml.Linq.XElement> 对象强制转换为所需的类型即可。 任何时候都可以将元素强制转换为字符串，如下所示：  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 该示例产生下面的输出：  
  
```xml  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a>示例  
 此外，还可以将元素强制转换为字符串以外的其他类型。 例如，如果有一个包含一个整数的元素，可以将它强制转换为 `int`，如下面的代码所示：  
  
```vb  
Dim e As XElement = <Age>44</Age>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & CInt(e))  
```  
  
 该示例产生下面的输出：  
  
```xml  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 提供了以下数据类型的显式强制转换运算符：`string`、`bool`、`bool?`、`int`、`int?`、`uint`、`uint?`、`long`、`long?`、`ulong`、`ulong?`、`float`、`float?`、`double`、`double?`、`decimal`、`decimal?`、`DateTime`、`DateTime?`、`TimeSpan`、`TimeSpan?`、`GUID` 和 `GUID?`。  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 为 <xref:System.Xml.Linq.XAttribute> 对象提供了相同的强制转换运算符。  
  
## <a name="example"></a>示例  
 可以使用 <xref:System.Xml.Linq.XElement.Value%2A> 属性来检索元素的内容：  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 该示例产生下面的输出：  
  
```xml  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a>示例  
 有时，尽管不能确定某个元素是否存在，还是会尝试检索该元素的值。 在这种情况下，当你将强制转换元素分配给可以为 null 的类型（ `string` 或 .NET Framework 中可为 null 的值类型之一）时，如果该元素不存在，则分配的变量只会设置为 `Nothing` 。 下面的代码演示当元素可能存在也可能不存在时，使用强制转换比使用 <xref:System.Xml.Linq.XElement.Value%2A> 属性更加简单。  
  
```vb  
Dim root As XElement = <Root>  
                           <Child1>child 1 content</Child1>  
                           <Child2>2</Child2>  
                       </Root>  
  
' The following assignments show why it is easier to use  
' casting when the element might or might not exist.  
  
Dim c1 As String = CStr(root.Element("Child1"))  
Console.WriteLine("c1:{0}", IIf(c1 Is Nothing, "element does not exist", c1))  
  
Dim c2 As Nullable(Of Integer) = CType(root.Element("Child2"), Nullable(Of Integer))  
Console.WriteLine("c2:{0}", IIf(Not (c2.HasValue), "element does not exist", c2.ToString()))  
  
Dim c3 As String = CStr(root.Element("Child3"))  
Console.WriteLine("c3:{0}", IIf(c3 Is Nothing, "element does not exist", c3))  
  
Dim c4 As Nullable(Of Integer) = CType(root.Element("Child4"), Nullable(Of Integer))  
Console.WriteLine("c4:{0}", IIf(Not (c4.HasValue), "element does not exist", c4.ToString()))  
  
Console.WriteLine()  
  
' The following assignments show the required code when using  
' the Value property when the attribute might or might not exist.  
' Notice that this is more difficult than the casting approach.  
  
Dim e1 As XElement = root.Element("Child1")  
Dim v1 As String  
If (e1 Is Nothing) Then  
    v1 = Nothing  
Else  
    v1 = e1.Value  
End If  
Console.WriteLine("v1:{0}", IIf(v1 Is Nothing, "element does not exist", v1))  
  
Dim e2 As XElement = root.Element("Child2")  
Dim v2 As Nullable(Of Integer)  
If (e2 Is Nothing) Then  
    v2 = Nothing  
Else  
    v2 = e2.Value  
End If  
Console.WriteLine("v2:{0}", IIf(Not (v2.HasValue), "element does not exist", v2))  
  
Dim e3 As XElement = root.Element("Child3")  
Dim v3 As String  
If (e3 Is Nothing) Then  
    v3 = Nothing  
Else  
    v3 = e3.Value  
End If  
Console.WriteLine("v3:{0}", IIf(v3 Is Nothing, "element does not exist", v3))  
  
Dim e4 As XElement = root.Element("Child4")  
Dim v4 As Nullable(Of Integer)  
If (e4 Is Nothing) Then  
    v4 = Nothing  
Else  
    v4 = e4.Value  
End If  
Console.WriteLine("v4:{0}", IIf(Not (v4.HasValue), "element does not exist", v4))  
```  
  
 此代码生成以下输出：  
  
```console  
c1:child 1 content  
c2:2  
c3:element does not exist  
c4:element does not exist  
  
v1:child 1 content  
v2:2  
v3:element does not exist  
v4:element does not exist  
```  
  
 通常情况下，当使用强制转换来检索元素和属性的内容时，可以编写更简易的代码。  
  
## <a name="see-also"></a>请参阅

- [LINQ to XML 轴 (Visual Basic)](linq-to-xml-axes.md)

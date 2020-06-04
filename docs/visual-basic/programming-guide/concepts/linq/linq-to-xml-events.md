---
title: LINQ to XML 事件
ms.date: 07/20/2015
ms.assetid: 34923928-b99c-4004-956e-38f6db25e910
ms.openlocfilehash: d00f6f1b2a14ac73c1bcd4a1f74b9714ca304da3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368811"
---
# <a name="linq-to-xml-events-visual-basic"></a>LINQ to XML 事件（Visual Basic）
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 事件使你可以在 XML 树发生改变时得到通知。  
  
 可以将事件添加到任何 <xref:System.Xml.Linq.XObject> 的实例。 事件处理程序然后将接收对该 <xref:System.Xml.Linq.XObject> 及其所有子代进行修改的事件。 例如，可以将事件处理程序添加到树根，然后从该事件处理程序中处理对树进行的所有修改。  
  
 有关 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 事件的示例，请参阅 <xref:System.Xml.Linq.XObject.Changing> 和 <xref:System.Xml.Linq.XObject.Changed>。  
  
## <a name="types-and-events"></a>类型和事件  
 在处理事件时使用下面的类型：  
  
|类型|说明|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|当 <xref:System.Xml.Linq.XObject> 发生事件时指定事件类型。|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|提供有关 <xref:System.Xml.Linq.XObject.Changing> 和 <xref:System.Xml.Linq.XObject.Changed> 事件的数据。|  
  
 修改 XML 树时将引发以下事件：  
  
|ㄆン|说明|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|在此 <xref:System.Xml.Linq.XObject> 或它的任何子代即将发生更改之前发生。|  
|<xref:System.Xml.Linq.XObject.Changed>|在 <xref:System.Xml.Linq.XObject> 或它的任何子代已经更改时发生。|  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>说明  
 当您希望在 XML 树中保留一些聚合信息时事件非常有用。 例如，您可能想保留一份发票合计，计算发票上各个项目的总和。 本示例使用事件来维护复杂元素 `Items` 之下所有子元素的总和。  
  
### <a name="code"></a>代码  
  
```vb  
Module Module1  
    Dim WithEvents items As XElement = Nothing  
    Dim total As XElement = Nothing  
    Dim root As XElement = _  
            <Root>  
                <Total>0</Total>  
                <Items></Items>  
            </Root>  
  
    Private Sub XObjectChanged( _  
            ByVal sender As Object, _  
            ByVal cea As XObjectChangeEventArgs) _  
            Handles items.Changed  
        Select Case cea.ObjectChange  
            Case XObjectChange.Add  
                If sender.GetType() Is GetType(XElement) Then  
                    total.Value = CStr(CInt(total.Value) + _  
                            CInt((DirectCast(sender, XElement)).Value))  
                End If  
                If sender.GetType() Is GetType(XText) Then  
                    total.Value = CStr(CInt(total.Value) + _  
                            CInt((DirectCast(sender, XText)).Value))  
                End If  
            Case XObjectChange.Remove  
                If sender.GetType() Is GetType(XElement) Then  
                    total.Value = CStr(CInt(total.Value) - _  
                            CInt((DirectCast(sender, XElement)).Value))  
                End If  
                If sender.GetType() Is GetType(XText) Then  
                    total.Value = CStr(CInt(total.Value) - _  
                            CInt((DirectCast(sender, XText)).Value))  
                End If  
        End Select  
        Console.WriteLine("Changed {0} {1}", _  
                            sender.GetType().ToString(), _  
                            cea.ObjectChange.ToString())  
    End Sub  
  
    Sub Main()  
        total = root.<Total>(0)  
        items = root.<Items>(0)  
        items.SetElementValue("Item1", 25)  
        items.SetElementValue("Item2", 50)  
        items.SetElementValue("Item2", 75)  
        items.SetElementValue("Item3", 133)  
        items.SetElementValue("Item1", Nothing)  
        items.SetElementValue("Item4", 100)  
        Console.WriteLine("Total:{0}", CInt(total))  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
### <a name="comments"></a>注释  
 此代码生成以下输出：  
  
```console  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XText Remove  
Changed System.Xml.Linq.XText Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Remove  
Changed System.Xml.Linq.XElement Add  
Total:308  
<Root>  
  <Total>308</Total>  
  <Items>  
    <Item2>75</Item2>  
    <Item3>133</Item3>  
    <Item4>100</Item4>  
  </Items>  
</Root>  
```  
  
## <a name="see-also"></a>另请参阅

- [高级 LINQ to XML 编程（Visual Basic）](advanced-linq-to-xml-programming.md)

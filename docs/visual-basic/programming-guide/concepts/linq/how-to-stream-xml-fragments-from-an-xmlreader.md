---
title: 如何：从 XmlReader 流式处理 XML 片段
ms.date: 07/20/2015
ms.assetid: f67ce598-4a12-4dcb-9a07-24deca02a111
ms.openlocfilehash: ff22625767c4e0752ca19d5a315395934b566230
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397695"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-visual-basic"></a>如何：从 XmlReader 流式处理 XML 片段（Visual Basic）
如果必须处理很大的 XML 文件，将整个 XML 树加载到内存可能不可行。 本主题演示如何使用 <xref:System.Xml.XmlReader> 对片段进行流式处理。  
  
 使用 <xref:System.Xml.XmlReader> 读取 <xref:System.Xml.Linq.XElement> 对象的一种最有效方式是编写您自己的自定义轴方法。 轴方法通常会返回一个集合，比如 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement>，如本主题中的示例所示。 在自定义轴方法中，在通过调用 <xref:System.Xml.Linq.XNode.ReadFrom%2A> 方法创建 XML 片段后，可以使用 `yield return` 返回该集合。 这可为您的自定义轴方法提供延迟执行语义。  
  
 在从 <xref:System.Xml.XmlReader> 对象创建 XML 树时，<xref:System.Xml.XmlReader> 必须位于元素上。 <xref:System.Xml.Linq.XNode.ReadFrom%2A> 方法在读取该元素的结束标记之前不会返回。  
  
 如果想要创建一个部分树，可实例化 <xref:System.Xml.XmlReader>，将读取器定位在要转换为 <xref:System.Xml.Linq.XElement> 树的节点上，然后创建 <xref:System.Xml.Linq.XElement> 对象。  
  
 主题[如何：流式处理包含访问标头信息的 XML 片段（Visual Basic）](how-to-stream-xml-fragments-with-access-to-header-information.md)包含有关如何对更复杂的文档进行流式处理的信息和示例。  
  
 主题[如何：执行大型 Xml 文档的流式转换（Visual Basic）](how-to-perform-streaming-transform-of-large-xml-documents.md)包含一个使用 LINQ to XML 转换极大的 xml 文档的示例，同时保持较小的内存需求量。  
  
## <a name="example"></a>示例  
 本示例创建一个自定义轴方法。 可以通过使用 LINQ 查询来查询该方法。 自定义轴方法 `StreamRootChildDoc` 是一个专门设计的方法，用于读取具有重复 `Child` 元素的文档。  
  
```vb  
Module Module1  
    Sub Main()  
        Dim markup = "<Root>" &  
                     "  <Child Key=""01"">" &  
                     "    <GrandChild>aaa</GrandChild>" &  
                     "  </Child>" &  
                     "  <Child Key=""02"">" &  
                     "    <GrandChild>bbb</GrandChild>" &  
                     "  </Child>" &  
                     "  <Child Key=""03"">" &  
                     "    <GrandChild>ccc</GrandChild>" &  
                     "  </Child>" &  
                     "</Root>"  
  
        Dim grandChildData =  
             From el In New StreamRootChildDoc(New IO.StringReader(markup))  
             Where CInt(el.@Key) > 1  
             Select el.<GrandChild>.Value  
  
        For Each s In grandChildData  
            Console.WriteLine(s)  
        Next  
    End Sub  
End Module  
  
Public Class StreamRootChildDoc  
    Implements IEnumerable(Of XElement)  
  
    Private _stringReader As IO.StringReader  
  
    Public Sub New(ByVal stringReader As IO.StringReader)  
        _stringReader = stringReader  
    End Sub  
  
    Public Function GetEnumerator() As IEnumerator(Of XElement) Implements IEnumerable(Of XElement).GetEnumerator  
        Return New StreamChildEnumerator(_stringReader)  
    End Function  
  
    Public Function GetEnumerator1() As IEnumerator Implements IEnumerable.GetEnumerator  
        Return Me.GetEnumerator()  
    End Function  
End Class  
  
Public Class StreamChildEnumerator  
    Implements IEnumerator(Of XElement)  
  
    Private _current As XElement  
    Private _reader As Xml.XmlReader  
    Private _stringReader As IO.StringReader  
  
    Public Sub New(ByVal stringReader As IO.StringReader)  
        _stringReader = stringReader  
        _reader = Xml.XmlReader.Create(_stringReader)  
        _reader.MoveToContent()  
    End Sub  
  
    Public ReadOnly Property Current As XElement Implements IEnumerator(Of XElement).Current  
        Get  
            Return _current  
        End Get  
    End Property  
  
    Public ReadOnly Property Current1 As Object Implements IEnumerator.Current  
        Get  
            Return Me.Current  
        End Get  
    End Property  
  
    Public Function MoveNext() As Boolean Implements IEnumerator.MoveNext  
        While _reader.Read()  
            Select Case _reader.NodeType  
                Case Xml.XmlNodeType.Element  
                    Dim el = TryCast(XElement.ReadFrom(_reader), XElement)  
                    If el IsNot Nothing Then  
                        _current = el  
                        Return True  
                    End If  
            End Select  
        End While  
  
        Return False  
    End Function  
  
    Public Sub Reset() Implements IEnumerator.Reset  
        _reader = Xml.XmlReader.Create(_stringReader)  
        _reader.MoveToContent()  
    End Sub  
  
#Region "IDisposable Support"  
    Private disposedValue As Boolean ' To detect redundant calls  
  
    ' IDisposable  
    Protected Overridable Sub Dispose(ByVal disposing As Boolean)  
        If Not Me.disposedValue Then  
            If disposing Then  
                _reader.Close()  
            End If  
        End If  
        Me.disposedValue = True  
    End Sub  
  
    Public Sub Dispose() Implements IDisposable.Dispose  
        Dispose(True)  
        GC.SuppressFinalize(Me)  
    End Sub  
#End Region  
  
End Class  
```  
  
 该示例产生下面的输出：  
  
```console  
bbb  
ccc  
```  
  
 在本示例中，源文档非常小。 但是即使有数百万个 `Child` 元素，本示例也仍具有很小的内存需求量。  
  
## <a name="see-also"></a>另请参阅

- [演练：在 Visual Basic 中实现 IEnumerable(Of T)](../../language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md)
- [分析 XML （Visual Basic）](parsing-xml.md)

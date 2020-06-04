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
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-visual-basic"></a><span data-ttu-id="3f834-102">如何：从 XmlReader 流式处理 XML 片段（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="3f834-102">How to: Stream XML Fragments from an XmlReader (Visual Basic)</span></span>
<span data-ttu-id="3f834-103">如果必须处理很大的 XML 文件，将整个 XML 树加载到内存可能不可行。</span><span class="sxs-lookup"><span data-stu-id="3f834-103">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="3f834-104">本主题演示如何使用 <xref:System.Xml.XmlReader> 对片段进行流式处理。</span><span class="sxs-lookup"><span data-stu-id="3f834-104">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="3f834-105">使用 <xref:System.Xml.XmlReader> 读取 <xref:System.Xml.Linq.XElement> 对象的一种最有效方式是编写您自己的自定义轴方法。</span><span class="sxs-lookup"><span data-stu-id="3f834-105">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="3f834-106">轴方法通常会返回一个集合，比如 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement>，如本主题中的示例所示。</span><span class="sxs-lookup"><span data-stu-id="3f834-106">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="3f834-107">在自定义轴方法中，在通过调用 <xref:System.Xml.Linq.XNode.ReadFrom%2A> 方法创建 XML 片段后，可以使用 `yield return` 返回该集合。</span><span class="sxs-lookup"><span data-stu-id="3f834-107">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="3f834-108">这可为您的自定义轴方法提供延迟执行语义。</span><span class="sxs-lookup"><span data-stu-id="3f834-108">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="3f834-109">在从 <xref:System.Xml.XmlReader> 对象创建 XML 树时，<xref:System.Xml.XmlReader> 必须位于元素上。</span><span class="sxs-lookup"><span data-stu-id="3f834-109">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="3f834-110"><xref:System.Xml.Linq.XNode.ReadFrom%2A> 方法在读取该元素的结束标记之前不会返回。</span><span class="sxs-lookup"><span data-stu-id="3f834-110">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="3f834-111">如果想要创建一个部分树，可实例化 <xref:System.Xml.XmlReader>，将读取器定位在要转换为 <xref:System.Xml.Linq.XElement> 树的节点上，然后创建 <xref:System.Xml.Linq.XElement> 对象。</span><span class="sxs-lookup"><span data-stu-id="3f834-111">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
 <span data-ttu-id="3f834-112">主题[如何：流式处理包含访问标头信息的 XML 片段（Visual Basic）](how-to-stream-xml-fragments-with-access-to-header-information.md)包含有关如何对更复杂的文档进行流式处理的信息和示例。</span><span class="sxs-lookup"><span data-stu-id="3f834-112">The topic [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>  
  
 <span data-ttu-id="3f834-113">主题[如何：执行大型 Xml 文档的流式转换（Visual Basic）](how-to-perform-streaming-transform-of-large-xml-documents.md)包含一个使用 LINQ to XML 转换极大的 xml 文档的示例，同时保持较小的内存需求量。</span><span class="sxs-lookup"><span data-stu-id="3f834-113">The topic [How to: Perform Streaming Transform of Large XML Documents (Visual Basic)](how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f834-114">示例</span><span class="sxs-lookup"><span data-stu-id="3f834-114">Example</span></span>  
 <span data-ttu-id="3f834-115">本示例创建一个自定义轴方法。</span><span class="sxs-lookup"><span data-stu-id="3f834-115">This example creates a custom axis method.</span></span> <span data-ttu-id="3f834-116">可以通过使用 LINQ 查询来查询该方法。</span><span class="sxs-lookup"><span data-stu-id="3f834-116">You can query it by using a LINQ query.</span></span> <span data-ttu-id="3f834-117">自定义轴方法 `StreamRootChildDoc` 是一个专门设计的方法，用于读取具有重复 `Child` 元素的文档。</span><span class="sxs-lookup"><span data-stu-id="3f834-117">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
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
  
 <span data-ttu-id="3f834-118">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="3f834-118">This example produces the following output:</span></span>  
  
```console  
bbb  
ccc  
```  
  
 <span data-ttu-id="3f834-119">在本示例中，源文档非常小。</span><span class="sxs-lookup"><span data-stu-id="3f834-119">In this example, the source document is very small.</span></span> <span data-ttu-id="3f834-120">但是即使有数百万个 `Child` 元素，本示例也仍具有很小的内存需求量。</span><span class="sxs-lookup"><span data-stu-id="3f834-120">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f834-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3f834-121">See also</span></span>

- [<span data-ttu-id="3f834-122">演练：在 Visual Basic 中实现 IEnumerable(Of T)</span><span class="sxs-lookup"><span data-stu-id="3f834-122">Walkthrough: Implementing IEnumerable(Of T) in Visual Basic</span></span>](../../language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md)
- [<span data-ttu-id="3f834-123">分析 XML （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="3f834-123">Parsing XML (Visual Basic)</span></span>](parsing-xml.md)

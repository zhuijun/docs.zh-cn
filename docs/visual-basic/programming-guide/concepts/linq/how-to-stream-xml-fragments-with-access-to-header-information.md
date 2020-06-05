---
title: 如何：通过对标头信息的访问流式处理 XML 片段
ms.date: 07/20/2015
ms.assetid: effd10df-87c4-4d7a-8a9a-1434d829dca5
ms.openlocfilehash: 8d0543ff5a772768292c0e3117f41bea9367d23a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397682"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-visual-basic"></a><span data-ttu-id="286e4-102">如何：通过对标头信息的访问来流式处理 XML 片段（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="286e4-102">How to: Stream XML Fragments with Access to Header Information (Visual Basic)</span></span>
<span data-ttu-id="286e4-103">有时，您必须读取任意大的 XML 文件并在编写您的应用程序时可以预测应用程序的内存需求量。</span><span class="sxs-lookup"><span data-stu-id="286e4-103">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="286e4-104">如果您试图用大 XML 文件填充 XML 树，则内存占用量将与文件大小成正比，也就是说会占用过多内存。</span><span class="sxs-lookup"><span data-stu-id="286e4-104">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="286e4-105">因此，您应改用流处理技术。</span><span class="sxs-lookup"><span data-stu-id="286e4-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="286e4-106">一种选择是使用 <xref:System.Xml.XmlReader> 来编写应用程序。</span><span class="sxs-lookup"><span data-stu-id="286e4-106">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="286e4-107">但你可能需要使用 LINQ 来查询 XML 树。</span><span class="sxs-lookup"><span data-stu-id="286e4-107">However, you might want to use LINQ to query the XML tree.</span></span> <span data-ttu-id="286e4-108">在这种情况下，您可以编写自己的自定义轴方法。</span><span class="sxs-lookup"><span data-stu-id="286e4-108">If this is the case, you can write your own custom axis method.</span></span> <span data-ttu-id="286e4-109">有关详细信息，请参阅[如何：编写 LINQ to XML 轴方法（Visual Basic）](how-to-write-a-linq-to-xml-axis-method.md)。</span><span class="sxs-lookup"><span data-stu-id="286e4-109">For more information, see [How to: Write a LINQ to XML Axis Method (Visual Basic)](how-to-write-a-linq-to-xml-axis-method.md).</span></span>  
  
 <span data-ttu-id="286e4-110">若要编写您自己的轴方法，请编写一个小方法，让该方法使用 <xref:System.Xml.XmlReader> 来读取各个节点，直到达到您感兴趣的节点之一。</span><span class="sxs-lookup"><span data-stu-id="286e4-110">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you are interested.</span></span> <span data-ttu-id="286e4-111">该方法然后调用 <xref:System.Xml.Linq.XNode.ReadFrom%2A>，后者将从 <xref:System.Xml.XmlReader> 中读取数据并实例化 XML 片段。</span><span class="sxs-lookup"><span data-stu-id="286e4-111">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="286e4-112">然后，您可以对自定义轴方法编写 LINQ 查询。</span><span class="sxs-lookup"><span data-stu-id="286e4-112">You can then write LINQ queries on your custom axis method.</span></span>  
  
 <span data-ttu-id="286e4-113">流处理技术最适合只需处理一次源文档的情况，您可以按文档顺序处理各个元素。</span><span class="sxs-lookup"><span data-stu-id="286e4-113">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="286e4-114">某些标准查询运算符（如 <xref:System.Linq.Enumerable.OrderBy%2A>）可以循环访问其源、收集所有数据、对数据排序，最后生成序列中的第一项。</span><span class="sxs-lookup"><span data-stu-id="286e4-114">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="286e4-115">请注意，如果使用可在生成第一项之前具体化源的查询运算符，则不会保持小的内存需求量。</span><span class="sxs-lookup"><span data-stu-id="286e4-115">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="286e4-116">示例</span><span class="sxs-lookup"><span data-stu-id="286e4-116">Example</span></span>  
 <span data-ttu-id="286e4-117">有时，问题会变得更有意思。</span><span class="sxs-lookup"><span data-stu-id="286e4-117">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="286e4-118">在下面的 XML 文档中，自定义轴方法的使用方也必须知道每一项所属的使用方名称。</span><span class="sxs-lookup"><span data-stu-id="286e4-118">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root>  
  <Customer>  
    <Name>A. Datum Corporation</Name>  
    <Item>  
      <Key>0001</Key>  
    </Item>  
    <Item>  
      <Key>0002</Key>  
    </Item>  
    <Item>  
      <Key>0003</Key>  
    </Item>  
    <Item>  
      <Key>0004</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Fabrikam, Inc.</Name>  
    <Item>  
      <Key>0005</Key>  
    </Item>  
    <Item>  
      <Key>0006</Key>  
    </Item>  
    <Item>  
      <Key>0007</Key>  
    </Item>  
    <Item>  
      <Key>0008</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Southridge Video</Name>  
    <Item>  
      <Key>0009</Key>  
    </Item>  
    <Item>  
      <Key>0010</Key>  
    </Item>  
  </Customer>  
</Root>  
```  
  
 <span data-ttu-id="286e4-119">本示例采用的方法还将监视此标头信息、保存标头信息，然后生成包含标头信息和所要枚举的详细信息的小型 XML 树。</span><span class="sxs-lookup"><span data-stu-id="286e4-119">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you are enumerating.</span></span> <span data-ttu-id="286e4-120">该轴方法然后生成这个新的小型 XML 树。</span><span class="sxs-lookup"><span data-stu-id="286e4-120">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="286e4-121">之后，查询将可以访问标头信息以及详细信息。</span><span class="sxs-lookup"><span data-stu-id="286e4-121">The query then has access to the header information as well as the detail information.</span></span>  
  
 <span data-ttu-id="286e4-122">此方法具有小的内存需求量。</span><span class="sxs-lookup"><span data-stu-id="286e4-122">This approach has a small memory footprint.</span></span> <span data-ttu-id="286e4-123">由于生成了所有的详细 XML 片段，不再需要保留对前一个片段的引用，因此，此方法可用于垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="286e4-123">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it is available for garbage collection.</span></span> <span data-ttu-id="286e4-124">请注意，此技术会在堆上创建许多短生存期的对象。</span><span class="sxs-lookup"><span data-stu-id="286e4-124">Note that this technique creates many short lived objects on the heap.</span></span>  
  
 <span data-ttu-id="286e4-125">下面的示例演示如何实现和使用可流处理由 URI 指定的文件中的 XML 片段的自定义轴方法。</span><span class="sxs-lookup"><span data-stu-id="286e4-125">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="286e4-126">此自定义轴经过专门编写，可以处理具有 `Customer`、`Name` 和 `Item` 元素，并且这些元素按上述 `Source.xml` 文档排列的文档。</span><span class="sxs-lookup"><span data-stu-id="286e4-126">This custom axis is specifically written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="286e4-127">这是一个过于简单的实现。</span><span class="sxs-lookup"><span data-stu-id="286e4-127">It is a simplistic implementation.</span></span> <span data-ttu-id="286e4-128">将会准备一个更可靠的实现以分析无效文档。</span><span class="sxs-lookup"><span data-stu-id="286e4-128">A more robust implementation would be prepared to parse an invalid document.</span></span>  
  
```vb  
Module Module1  
  
    Sub Main()  
        Dim xmlTree = <Root>  
                          <%=  
                              From el In New StreamCustomerItem("Source.xml")  
                              Let itemKey = CInt(el.<Key>.Value)  
                              Where itemKey >= 3 AndAlso itemKey <= 7  
                              Select <Item>  
                                         <Customer><%= el.Parent.<Name>.Value %></Customer>  
                                         <%= el.<Key> %>  
                                     </Item>  
                          %>  
                      </Root>  
  
        Console.WriteLine(xmlTree)  
    End Sub  
  
End Module  
  
Public Class StreamCustomerItem  
    Implements IEnumerable(Of XElement)  
  
    Private _uri As String  
  
    Public Sub New(ByVal uri As String)  
        _uri = uri  
    End Sub  
  
    Public Function GetEnumerator() As IEnumerator(Of XElement) Implements IEnumerable(Of XElement).GetEnumerator  
        Return New StreamCustomerItemEnumerator(_uri)  
    End Function  
  
    Public Function GetEnumerator1() As IEnumerator Implements IEnumerable.GetEnumerator  
        Return Me.GetEnumerator()  
    End Function  
End Class  
  
Public Class StreamCustomerItemEnumerator  
    Implements IEnumerator(Of XElement)  
  
    Private _current As XElement  
    Private _customerName As String  
    Private _reader As Xml.XmlReader  
    Private _uri As String  
  
    Public Sub New(ByVal uri As String)  
        _uri = uri  
        _reader = Xml.XmlReader.Create(_uri)  
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
        Dim item As XElement  
        Dim name As XElement  
  
        ' Parse the file, save header information when encountered, and return the  
        ' current Item XElement.  
  
        ' loop through Customer elements  
        While _reader.Read()  
            If _reader.NodeType = Xml.XmlNodeType.Element Then  
                Select Case _reader.Name  
                    Case "Customer"  
                        ' move to Name element  
                        While _reader.Read()  
  
                            If _reader.NodeType = Xml.XmlNodeType.Element AndAlso  
                                _reader.Name = "Name" Then  
  
                                name = TryCast(XElement.ReadFrom(_reader), XElement)  
                                _customerName = If(name IsNot Nothing, name.Value, "")  
                                Exit While  
                            End If  
  
                        End While  
                    Case "Item"  
                        item = TryCast(XElement.ReadFrom(_reader), XElement)  
                        Dim tempRoot = <Root>  
                                           <Name><%= _customerName %></Name>  
                                           <%= item %>  
                                       </Root>  
                        _current = item  
                        Return True  
                End Select  
            End If  
        End While  
  
        Return False  
    End Function  
  
    Public Sub Reset() Implements IEnumerator.Reset  
        _reader = Xml.XmlReader.Create(_uri)  
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
  
 <span data-ttu-id="286e4-129">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="286e4-129">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="286e4-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="286e4-130">See also</span></span>

- [<span data-ttu-id="286e4-131">高级 LINQ to XML 编程（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="286e4-131">Advanced LINQ to XML Programming (Visual Basic)</span></span>](advanced-linq-to-xml-programming.md)

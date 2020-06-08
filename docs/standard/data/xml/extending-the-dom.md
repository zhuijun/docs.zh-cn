---
title: 扩展 DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: b5489c96-4afd-439a-a25d-fc82eb4a148d
ms.openlocfilehash: 4a1a7af0e841601542a30c7bd3f71395faa6cb57
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287787"
---
# <a name="extending-the-dom"></a><span data-ttu-id="53cfc-102">扩展 DOM</span><span class="sxs-lookup"><span data-stu-id="53cfc-102">Extending the DOM</span></span>

<span data-ttu-id="53cfc-103">Microsoft .NET Framework 包含一组基类，用于实现 XML 文档对象模型 (DOM)。</span><span class="sxs-lookup"><span data-stu-id="53cfc-103">The Microsoft .NET Framework includes a base set of classes that provides an implementation of the XML Document Object Model (DOM).</span></span> <span data-ttu-id="53cfc-104"><xref:System.Xml.XmlNode> 及其派生类提供的方法和属性可以浏览、查询和修改 XML 文档的内容和结构。</span><span class="sxs-lookup"><span data-stu-id="53cfc-104">The <xref:System.Xml.XmlNode>, and its derived classes, provides methods and properties that allow you to navigate, query, and modify the content and structure of an XML document.</span></span>

<span data-ttu-id="53cfc-105">当使用 DOM 将 XML 内容加载到内存中时，所创建的节点包含节点名、节点类型等信息。</span><span class="sxs-lookup"><span data-stu-id="53cfc-105">When XML content is loaded into memory using the DOM, the nodes created contain information such as node name, node type, and so on.</span></span> <span data-ttu-id="53cfc-106">可能存在需要特定节点信息但基类未提供的情况。</span><span class="sxs-lookup"><span data-stu-id="53cfc-106">There may be occasions where you require specific node information that the base classes do not provide.</span></span> <span data-ttu-id="53cfc-107">例如，可能需要查看节点的行号和位置。</span><span class="sxs-lookup"><span data-stu-id="53cfc-107">For example, you may want to see the line number and position of the node.</span></span> <span data-ttu-id="53cfc-108">这种情况下，可以从现有的 DOM 类派生新类并添加附加功能。</span><span class="sxs-lookup"><span data-stu-id="53cfc-108">In this case, you can derive new classes from the existing DOM classes and add additional functionality.</span></span>

<span data-ttu-id="53cfc-109">派生新类时有两个一般原则：</span><span class="sxs-lookup"><span data-stu-id="53cfc-109">There are two general guidelines when deriving new classes:</span></span>

- <span data-ttu-id="53cfc-110">建议永远不要从 <xref:System.Xml.XmlNode> 类派生。</span><span class="sxs-lookup"><span data-stu-id="53cfc-110">It is recommended that you never derive from the <xref:System.Xml.XmlNode> class.</span></span> <span data-ttu-id="53cfc-111">相反，建议从与对您有用的节点类型对应的类派生类。</span><span class="sxs-lookup"><span data-stu-id="53cfc-111">Instead, it is recommended that you derive classes from the class corresponding to the node type that you are interested in.</span></span> <span data-ttu-id="53cfc-112">例如，如果要返回属性节点的其他信息，可从 <xref:System.Xml.XmlAttribute> 类派生。</span><span class="sxs-lookup"><span data-stu-id="53cfc-112">For example, if you want to return additional information on attribute nodes, you can derive from the <xref:System.Xml.XmlAttribute> class.</span></span>

- <span data-ttu-id="53cfc-113">除了节点创建方法外，建议在重写函数时总是调用基本版本的函数，然后添加任何附加处理。</span><span class="sxs-lookup"><span data-stu-id="53cfc-113">Except for the node creation methods, it is recommended that when overriding a function, you should always call the base version of the function and then add any additional processing.</span></span>

## <a name="creating-your-own-node-instances"></a><span data-ttu-id="53cfc-114">创建您自己的节点实例</span><span class="sxs-lookup"><span data-stu-id="53cfc-114">Creating Your Own Node Instances</span></span>

<span data-ttu-id="53cfc-115"><xref:System.Xml.XmlDocument> 类包含节点创建方法。</span><span class="sxs-lookup"><span data-stu-id="53cfc-115">The <xref:System.Xml.XmlDocument> class contains node creation methods.</span></span> <span data-ttu-id="53cfc-116">加载 XML 文件时，调用这些方法来创建节点。</span><span class="sxs-lookup"><span data-stu-id="53cfc-116">When an XML file is loaded, these methods are called to create the nodes.</span></span> <span data-ttu-id="53cfc-117">可以重写这些方法，以便在加载文档时创建节点实例。</span><span class="sxs-lookup"><span data-stu-id="53cfc-117">You can override these methods so that your node instances are created when a document is loaded.</span></span> <span data-ttu-id="53cfc-118">例如，如果已经扩展了 <xref:System.Xml.XmlElement> 类，则可以继承 <xref:System.Xml.XmlDocument> 类并重写 <xref:System.Xml.XmlDocument.CreateElement%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="53cfc-118">For example, if you have extended the <xref:System.Xml.XmlElement> class, you would inherit the <xref:System.Xml.XmlDocument> class and override the <xref:System.Xml.XmlDocument.CreateElement%2A> method.</span></span>

<span data-ttu-id="53cfc-119">下面的示例显示如何重写 <xref:System.Xml.XmlDocument.CreateElement%2A> 方法以返回 <xref:System.Xml.XmlElement> 类的实现。</span><span class="sxs-lookup"><span data-stu-id="53cfc-119">The following example shows how to override the <xref:System.Xml.XmlDocument.CreateElement%2A> method to return your implementation of the <xref:System.Xml.XmlElement> class.</span></span>

```vb
Class LineInfoDocument
    Inherits XmlDocument
        Public Overrides Function CreateElement(prefix As String, localname As String, nsURI As String) As XmlElement
        Dim elem As New LineInfoElement(prefix, localname, nsURI, Me)
        Return elem
    End Function 'CreateElement
End Class 'LineInfoDocument
```

```csharp
class LineInfoDocument : XmlDocument
{
    public override XmlElement CreateElement(string prefix, string localname, string nsURI)
    {
        LineInfoElement elem = new LineInfoElement(prefix, localname, nsURI, this);
        return elem;
    }
}
```

## <a name="extending-a-class"></a><span data-ttu-id="53cfc-120">扩展类</span><span class="sxs-lookup"><span data-stu-id="53cfc-120">Extending a Class</span></span>

<span data-ttu-id="53cfc-121">若要扩展类，请从现有 DOM 类之一派生类。</span><span class="sxs-lookup"><span data-stu-id="53cfc-121">To extend a class, derive your class from one of the existing DOM classes.</span></span> <span data-ttu-id="53cfc-122">然后，可以重写基类中的任何虚拟方法或属性或添加您自己的虚拟方法或属性。</span><span class="sxs-lookup"><span data-stu-id="53cfc-122">You can then override any of the virtual methods or properties in the base class, or add your own.</span></span>

<span data-ttu-id="53cfc-123">在下面的示例中，创建了一个新类，该类实现 <xref:System.Xml.XmlElement> 类和 <xref:System.Xml.IXmlLineInfo> 接口。</span><span class="sxs-lookup"><span data-stu-id="53cfc-123">In the following example, a new class is created, which implements the <xref:System.Xml.XmlElement> class and the <xref:System.Xml.IXmlLineInfo> interface.</span></span> <span data-ttu-id="53cfc-124">定义了允许用户收集行信息的附加方法和属性。</span><span class="sxs-lookup"><span data-stu-id="53cfc-124">Additional methods and properties are defined which allows users to gather line information.</span></span>

```vb
Class LineInfoElement
   Inherits XmlElement
   Implements IXmlLineInfo
   Private lineNumber As Integer = 0
   Private linePosition As Integer = 0

   Friend Sub New(prefix As String, localname As String, nsURI As String, doc As XmlDocument)
      MyBase.New(prefix, localname, nsURI, doc)
      CType(doc, LineInfoDocument).IncrementElementCount()
   End Sub

   Public Sub SetLineInfo(linenum As Integer, linepos As Integer)
      lineNumber = linenum
      linePosition = linepos
   End Sub

   Public ReadOnly Property LineNumber() As Integer
      Get
         Return lineNumber
      End Get
   End Property

   Public ReadOnly Property LinePosition() As Integer
      Get
         Return linePosition
      End Get
   End Property

   Public Function HasLineInfo() As Boolean
      Return True
   End Function
End Class ' End LineInfoElement class.
```

```csharp
class LineInfoElement : XmlElement, IXmlLineInfo {
   int lineNumber = 0;
   int linePosition = 0;
   internal LineInfoElement( string prefix, string localname, string nsURI, XmlDocument doc ) : base( prefix, localname, nsURI, doc ) {
       ( (LineInfoDocument)doc ).IncrementElementCount();
  }
  public void SetLineInfo( int linenum, int linepos ) {
      lineNumber = linenum;
      linePosition = linepos;
  }
  public int LineNumber {
     get {
       return lineNumber;
     }
  }
  public int LinePosition {
      get {
        return linePosition;
      }
  }
  public bool HasLineInfo() {
    return true;
  }
} // End LineInfoElement class.
```

### <a name="example"></a><span data-ttu-id="53cfc-125">示例</span><span class="sxs-lookup"><span data-stu-id="53cfc-125">Example</span></span>

<span data-ttu-id="53cfc-126">以下示例计算 XML 文档中的元素数：</span><span class="sxs-lookup"><span data-stu-id="53cfc-126">The following example counts the number of elements in an XML document:</span></span>

```vb
Imports System.Xml
Imports System.IO

Class LineInfoDocument
   Inherits XmlDocument

   Private elementCount As Integer

   Friend Sub New()
      elementCount = 0
   End Sub

   Public Overrides Function CreateElement(prefix As String, localname As String, nsURI As String) As XmlElement
      Dim elem As New LineInfoElement(prefix, localname, nsURI, Me)
      Return elem
   End Function

   Public Sub IncrementElementCount()
      elementCount += 1
   End Sub

   Public Function GetCount() As Integer
      Return elementCount
   End Function
End Class 'End LineInfoDocument class.

Class LineInfoElement
   Inherits XmlElement

   Friend Sub New(prefix As String, localname As String, nsURI As String, doc As XmlDocument)
      MyBase.New(prefix, localname, nsURI, doc)
      CType(doc, LineInfoDocument).IncrementElementCount()
   End Sub 'New
End Class 'LineInfoElement
 _ 'End LineInfoElement class.

Public Class Test

   Private filename As [String] = "book.xml"

   Public Shared Sub Main()

      Dim doc As New LineInfoDocument()
      doc.Load(filename)
      Console.WriteLine("Number of elements in {0}: {1}", filename, doc.GetCount())
   End Sub
End Class
```

```csharp
using System;
using System.Xml;
using System.IO;

class LineInfoDocument : XmlDocument {

  int elementCount;
  internal LineInfoDocument():base() {
    elementCount = 0;
  }

  public override XmlElement CreateElement( string prefix, string localname, string nsURI) {
    LineInfoElement elem = new LineInfoElement(prefix, localname, nsURI, this );
    return elem;
  }

  public void IncrementElementCount() {
     elementCount++;
  }

  public int GetCount() {
     return elementCount;
  }
} // End LineInfoDocument class.

class LineInfoElement:XmlElement {

    internal LineInfoElement( string prefix, string localname, string nsURI, XmlDocument doc ):base( prefix,localname,nsURI, doc ){
      ((LineInfoDocument)doc).IncrementElementCount();
    }
} // End LineInfoElement class.

public class Test {

  const String filename = "book.xml";
  public static void Main() {

     LineInfoDocument doc =new LineInfoDocument();
     doc.Load(filename);
     Console.WriteLine("Number of elements in {0}: {1}", filename, doc.GetCount());

  }
}
```

#### <a name="input"></a><span data-ttu-id="53cfc-127">输入</span><span class="sxs-lookup"><span data-stu-id="53cfc-127">Input</span></span>

<span data-ttu-id="53cfc-128">book.xml</span><span class="sxs-lookup"><span data-stu-id="53cfc-128">book.xml</span></span>

```xml
<!--sample XML fragment-->
<book genre='novel' ISBN='1-861001-57-5' misc='sale-item'>
  <title>The Handmaid's Tale</title>
  <price>14.95</price>
</book>
```

#### <a name="output"></a><span data-ttu-id="53cfc-129">Output</span><span class="sxs-lookup"><span data-stu-id="53cfc-129">Output</span></span>

```console
Number of elements in book.xml: 3
```

## <a name="node-event-handler"></a><span data-ttu-id="53cfc-130">节点事件处理程序</span><span class="sxs-lookup"><span data-stu-id="53cfc-130">Node Event Handler</span></span>

<span data-ttu-id="53cfc-131">DOM 的 .NET Framework 实现还包括一个事件系统，使您能够在 XML 文档中的节点更改时接收并处理事件。</span><span class="sxs-lookup"><span data-stu-id="53cfc-131">The .NET Framework implementation of the DOM also includes an event system that enables you to receive and handle events when nodes in an XML document change.</span></span> <span data-ttu-id="53cfc-132">使用 <xref:System.Xml.XmlNodeChangedEventHandler> 和 <xref:System.Xml.XmlNodeChangedEventArgs> 类可以捕获 `NodeChanged`、`NodeChanging`、`NodeInserted`、`NodeInserting`、`NodeRemoved` 和 `NodeRemoving` 事件。</span><span class="sxs-lookup"><span data-stu-id="53cfc-132">Using the <xref:System.Xml.XmlNodeChangedEventHandler> and <xref:System.Xml.XmlNodeChangedEventArgs> classes, you can capture `NodeChanged`, `NodeChanging`, `NodeInserted`, `NodeInserting`, `NodeRemoved`, and `NodeRemoving` events.</span></span>

<span data-ttu-id="53cfc-133">该事件处理过程在派生类中的工作方式同它在原始 DOM 类中的工作方式完全相同。</span><span class="sxs-lookup"><span data-stu-id="53cfc-133">The event-handling process works exactly the same in derived classes as it would in the original DOM classes.</span></span>

<span data-ttu-id="53cfc-134">若要详细了解节点事件处理，请参阅[事件](../../events/index.md)和 <xref:System.Xml.XmlNodeChangedEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="53cfc-134">For more information regarding node event handling, see [Events](../../events/index.md) and <xref:System.Xml.XmlNodeChangedEventHandler>.</span></span>

## <a name="default-attributes-and-the-createelement-method"></a><span data-ttu-id="53cfc-135">默认属性和 CreateElement 方法</span><span class="sxs-lookup"><span data-stu-id="53cfc-135">Default Attributes and the CreateElement Method</span></span>

<span data-ttu-id="53cfc-136">如果要重写派生类中的 <xref:System.Xml.XmlDocument.CreateElement%2A> 方法，则在编辑文档期间创建新元素时不添加默认属性。</span><span class="sxs-lookup"><span data-stu-id="53cfc-136">If you are overriding the <xref:System.Xml.XmlDocument.CreateElement%2A> method in a derived class, default attributes are not added when you are creating new elements while editing the document.</span></span> <span data-ttu-id="53cfc-137">这只有在编辑时才是问题。</span><span class="sxs-lookup"><span data-stu-id="53cfc-137">This is only an issue while editing.</span></span> <span data-ttu-id="53cfc-138">由于 <xref:System.Xml.XmlDocument.CreateElement%2A> 方法负责向 <xref:System.Xml.XmlDocument> 添加默认属性，因此必须在 <xref:System.Xml.XmlDocument.CreateElement%2A> 方法中编写此功能的代码。</span><span class="sxs-lookup"><span data-stu-id="53cfc-138">Because the <xref:System.Xml.XmlDocument.CreateElement%2A> method is responsible for adding default attributes to an <xref:System.Xml.XmlDocument>, you must code this functionality in the <xref:System.Xml.XmlDocument.CreateElement%2A> method.</span></span> <span data-ttu-id="53cfc-139">如果要加载包含默认属性的 <xref:System.Xml.XmlDocument>，则这些属性将被正确处理。</span><span class="sxs-lookup"><span data-stu-id="53cfc-139">If you are loading an <xref:System.Xml.XmlDocument> that includes default attributes, they will be handled correctly.</span></span> <span data-ttu-id="53cfc-140">若要详细了解默认属性，请参阅[新建 DOM 中元素的属性](creating-new-attributes-for-elements-in-the-dom.md)。</span><span class="sxs-lookup"><span data-stu-id="53cfc-140">For more information on default attributes, see [Creating New Attributes for Elements in the DOM](creating-new-attributes-for-elements-in-the-dom.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="53cfc-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="53cfc-141">See also</span></span>

- [<span data-ttu-id="53cfc-142">XML 文档对象模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="53cfc-142">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)

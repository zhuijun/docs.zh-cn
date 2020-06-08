---
title: 使用 mlNodeChangedEventArgs 的 XML 文档中的事件处理
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 0fe844e3-5b6f-4fe7-ad15-22459501738b
ms.openlocfilehash: 7bca8600468d3715b1d1cca46049eb07bb8e3d03
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287774"
---
# <a name="event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs"></a><span data-ttu-id="17cc3-102">使用 mlNodeChangedEventArgs 的 XML 文档中的事件处理</span><span class="sxs-lookup"><span data-stu-id="17cc3-102">Event Handling in an XML Document Using the XmlNodeChangedEventArgs</span></span>
<span data-ttu-id="17cc3-103">XmlNodeChangedEventArgs  封装传递给事件处理程序的参数，这些处理程序在 XmlDocument  对象上注册为用于处理事件。</span><span class="sxs-lookup"><span data-stu-id="17cc3-103">The **XmlNodeChangedEventArgs** encapsulates the arguments passed to the event handlers registered on the **XmlDocument** object for handling events.</span></span> <span data-ttu-id="17cc3-104">下表提供了事件以及关于何时引发事件的说明。</span><span class="sxs-lookup"><span data-stu-id="17cc3-104">The events and a description of when they are fired is given in the following table.</span></span>  
  
|<span data-ttu-id="17cc3-105">事件</span><span class="sxs-lookup"><span data-stu-id="17cc3-105">Event</span></span>|<span data-ttu-id="17cc3-106">引发</span><span class="sxs-lookup"><span data-stu-id="17cc3-106">Fired</span></span>|  
|-----------|-----------|  
|<xref:System.Xml.XmlDocument.NodeInserting>|<span data-ttu-id="17cc3-107">当准备将属于当前文档的节点插入到另一个节点时。</span><span class="sxs-lookup"><span data-stu-id="17cc3-107">When a node belonging to the current document is about to be inserted into another node.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeInserted>|<span data-ttu-id="17cc3-108">当已经将属于当前文档的节点插入到另一个节点时。</span><span class="sxs-lookup"><span data-stu-id="17cc3-108">When a node belonging to the current document has been inserted into another node.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeRemoving>|<span data-ttu-id="17cc3-109">当准备将属于此文档的节点从文档中移除时。</span><span class="sxs-lookup"><span data-stu-id="17cc3-109">When a node belonging to this document is about to be removed from the document.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeRemoved>|<span data-ttu-id="17cc3-110">当已经将属于此文档的节点从其父级中移除时。</span><span class="sxs-lookup"><span data-stu-id="17cc3-110">When a node belonging to this document has been removed from its parent.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeChanging>|<span data-ttu-id="17cc3-111">当准备更改节点值时。</span><span class="sxs-lookup"><span data-stu-id="17cc3-111">When the value of a node is about to be changed.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeChanged>|<span data-ttu-id="17cc3-112">当节点值已经更改时。</span><span class="sxs-lookup"><span data-stu-id="17cc3-112">When the value of a node has been changed.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="17cc3-113">如果 XmlDataDocument  内存使用完全优化为使用 DataSet  存储，那么基础 DataSet  有更改时，XmlDataDocument  可能不会抛出上面列出的任何事件。</span><span class="sxs-lookup"><span data-stu-id="17cc3-113">If the **XmlDataDocument** memory usage is fully optimized to use **DataSet** storage, the **XmlDataDocument** might not raise any of the events listed above when changes are made to the underlying **DataSet**.</span></span> <span data-ttu-id="17cc3-114">如果需要这些事件，必须遍历整个 XmlDocument  一遍，才能非完全优化内存使用。</span><span class="sxs-lookup"><span data-stu-id="17cc3-114">If you need these events, you must traverse the whole **XmlDocument** once to make the memory usage non-fully optimized.</span></span>  
  
 <span data-ttu-id="17cc3-115">下面的代码示例显示如何定义事件处理程序以及如何将该事件处理程序添加到事件。</span><span class="sxs-lookup"><span data-stu-id="17cc3-115">The following code example shows how to define an event handler and how to add the event handler to an event.</span></span>  
  
```vb  
' Attach the event handler, NodeInsertedHandler, to the NodeInserted  
' event.  
Dim doc as XmlDocument = new XmlDocument()  
Dim XmlNodeChgEHdlr as XmlNodeChangedEventHandler = new XmlNodeChangedEventHandler(addressof MyNodeChangedEvent)
AddHandler doc.NodeInserted, XmlNodeChgEHdlr
  
Dim n as XmlNode = doc.CreateElement( "element" )  
Console.WriteLine( "Before Event Inserting" )
  
' This is the point where the new node is being inserted in the tree,  
' and this is the point where the NodeInserted event is raised.  
doc.AppendChild( n )  
Console.WriteLine( "After Event Inserting" )
  
' Define the event handler that handles the NodeInserted event.  
sub NodeInsertedHandler(src as Object, args as XmlNodeChangedEventArgs)  
    Console.WriteLine("Node " + args.Node.Name + " inserted!!")  
end sub  
```  
  
```csharp  
// Attach the event handler, NodeInsertedHandler, to the NodeInserted  
// event.  
XmlDocument doc = new XmlDocument();  
doc.NodeInserted += new XmlNodeChangedEventHandler(NodeInsertedHandler);  
XmlNode n = doc.CreateElement( "element" );  
Console.WriteLine( "Before Event Inserting" );  
  
// This is the point where the new node is being inserted in the tree,  
// and this is the point where the NodeInserted event is raised.  
doc.AppendChild( n );  
Console.WriteLine( "After Event Inserting" );
  
// Define the event handler that handles the NodeInserted event.  
void NodeInsertedHandler(Object src, XmlNodeChangedEventArgs args)  
{  
    Console.WriteLine("Node " + args.Node.Name + " inserted!!");  
}  
```  
  
 <span data-ttu-id="17cc3-116">某些 XML 文档对象模型 (DOM) 操作是可导致引发多个事件的复合操作。</span><span class="sxs-lookup"><span data-stu-id="17cc3-116">Some XML Document Object Model (DOM) operations are compound operations that can result in multiple events being fired.</span></span> <span data-ttu-id="17cc3-117">例如，AppendChild  可能还必须删除从上一个父级追加的节点。</span><span class="sxs-lookup"><span data-stu-id="17cc3-117">For example, **AppendChild** may also have to remove the node being appended from its previous parent.</span></span> <span data-ttu-id="17cc3-118">在此示例中，依次抛出 NodeRemoved  事件和 NodeInserted  事件。</span><span class="sxs-lookup"><span data-stu-id="17cc3-118">In this case, you see a **NodeRemoved** event fired first, followed by a **NodeInserted** event.</span></span> <span data-ttu-id="17cc3-119">设置 InnerXml  等操作可能会导致多个事件发生。</span><span class="sxs-lookup"><span data-stu-id="17cc3-119">Operations like setting **InnerXml** could result in multiple events.</span></span>  
  
 <span data-ttu-id="17cc3-120">下面的代码示例展示了如何创建事件处理程序，以及如何处理 NodeInserted  事件。</span><span class="sxs-lookup"><span data-stu-id="17cc3-120">The following code example shows the creation of the event handler and the handling of the **NodeInserted** event.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports Microsoft.VisualBasic  
  
Public Class Sample  
  
    Private Const filename As String = "books.xml"  
  
    Shared Sub Main()  
        Dim mySample As Sample = New Sample()  
        mySample.Run(filename)  
    End Sub  
  
    Public Sub Run(ByVal args As String)  
        ' Create and load the XML document.  
        Console.WriteLine("Loading file 0 ...", args)  
        Dim doc As XmlDocument = New XmlDocument()  
        doc.Load(args)  
  
        ' Create the event handlers.  
        Dim XmlNodeChgEHdlr As XmlNodeChangedEventHandler = New XmlNodeChangedEventHandler(AddressOf MyNodeChangedEvent)  
        Dim XmlNodeInsrtEHdlr As XmlNodeChangedEventHandler = New XmlNodeChangedEventHandler(AddressOf MyNodeInsertedEvent)  
        AddHandler doc.NodeChanged, XmlNodeChgEHdlr  
        AddHandler doc.NodeInserted, XmlNodeInsrtEHdlr  
  
        ' Change the book price.  
        doc.DocumentElement.LastChild.InnerText = "5.95"  
  
        ' Add a new element.  
        Dim newElem As XmlElement = doc.CreateElement("style")  
        newElem.InnerText = "hardcover"  
        doc.DocumentElement.AppendChild(newElem)  
  
        Console.WriteLine(Chr(13) + Chr(10) + "Display the modified XML...")  
        Console.WriteLine(doc.OuterXml)  
    End Sub  
  
    ' Handle the NodeChanged event.  
    Public Sub MyNodeChangedEvent(ByVal src As Object, ByVal args As XmlNodeChangedEventArgs)  
        Console.Write("Node Changed Event: <0> changed", args.Node.Name)  
        If Not (args.Node.Value Is Nothing) Then  
            Console.WriteLine(" with value  0", args.Node.Value)  
        Else  
            Console.WriteLine("")  
        End If  
    End Sub  
  
    ' Handle the NodeInserted event.  
    Public Sub MyNodeInsertedEvent(ByVal src As Object, ByVal args As XmlNodeChangedEventArgs)  
        Console.Write("Node Inserted Event: <0> inserted", args.Node.Name)  
        If Not (args.Node.Value Is Nothing) Then  
            Console.WriteLine(" with value 0", args.Node.Value)  
        Else  
            Console.WriteLine("")  
        End If  
    End Sub  
  
End Class        ' End class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  private const String filename = "books.xml";  
  
  public static void Main()  
  {  
     Sample mySample = new Sample();  
     mySample.Run(filename);  
  }  
  
  public void Run(String args)  
  {  
  
     // Create and load the XML document.  
     Console.WriteLine ("Loading file {0} ...", args);  
     XmlDocument doc = new XmlDocument();  
     doc.Load (args);  
  
     // Create the event handlers.  
     doc.NodeChanged += new XmlNodeChangedEventHandler(this.MyNodeChangedEvent);  
     doc.NodeInserted += new XmlNodeChangedEventHandler(this.MyNodeInsertedEvent);  
  
     // Change the book price.  
     doc.DocumentElement.LastChild.InnerText = "5.95";  
  
     // Add a new element.  
     XmlElement newElem = doc.CreateElement("style");  
     newElem.InnerText = "hardcover";  
     doc.DocumentElement.AppendChild(newElem);  
  
     Console.WriteLine("\r\nDisplay the modified XML...");  
     Console.WriteLine(doc.OuterXml);
  
  }  
  
  // Handle the NodeChanged event.  
  public void MyNodeChangedEvent(Object src, XmlNodeChangedEventArgs args)  
  {  
     Console.Write("Node Changed Event: <{0}> changed", args.Node.Name);  
     if (args.Node.Value != null)  
     {  
        Console.WriteLine(" with value  {0}", args.Node.Value);  
     }  
     else  
       Console.WriteLine("");  
  }  
  
  // Handle the NodeInserted event.  
  public void MyNodeInsertedEvent(Object src, XmlNodeChangedEventArgs args)  
  {  
     Console.Write("Node Inserted Event: <{0}> inserted", args.Node.Name);  
     if (args.Node.Value != null)  
     {  
        Console.WriteLine(" with value {0}", args.Node.Value);  
     }  
     else  
        Console.WriteLine("");  
  }  
  
} // End class
```  
  
 <span data-ttu-id="17cc3-121">有关详细信息，请参阅 <xref:System.Xml.XmlNodeChangedEventArgs> 和 <xref:System.Xml.XmlNodeChangedEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="17cc3-121">For more information, see <xref:System.Xml.XmlNodeChangedEventArgs> and <xref:System.Xml.XmlNodeChangedEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17cc3-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="17cc3-122">See also</span></span>

- [<span data-ttu-id="17cc3-123">XML 文档对象模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="17cc3-123">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)

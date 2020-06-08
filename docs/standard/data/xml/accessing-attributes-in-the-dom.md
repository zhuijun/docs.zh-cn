---
title: 访问 DOM 中的属性
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: ce2df341-a1a4-4e97-8e1b-cd45b8e3e71e
ms.openlocfilehash: a77780621032e2ce59b9db04a179c7086588219b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291638"
---
# <a name="accessing-attributes-in-the-dom"></a><span data-ttu-id="93821-102">访问 DOM 中的属性</span><span class="sxs-lookup"><span data-stu-id="93821-102">Accessing Attributes in the DOM</span></span>

<span data-ttu-id="93821-103">属性是元素的属性，不是元素的子级。</span><span class="sxs-lookup"><span data-stu-id="93821-103">Attributes are properties of the element, not children of the element.</span></span> <span data-ttu-id="93821-104">这一区别很重要，因为用来浏览 XML 文档对象模型 (DOM) 的同级、父级和子节点的方法不同。</span><span class="sxs-lookup"><span data-stu-id="93821-104">This distinction is important because of the methods used to navigate sibling, parent, and child nodes of the XML Document Object Model (DOM).</span></span> <span data-ttu-id="93821-105">例如，PreviousSibling  和 NextSibling  方法不用于从元素转到属性，也不用于在属性之间导航。</span><span class="sxs-lookup"><span data-stu-id="93821-105">For example, the **PreviousSibling** and **NextSibling** methods are not used to navigate from an element to an attribute or between attributes.</span></span> <span data-ttu-id="93821-106">相反，属性是元素属性，归元素所有，包含 OwnerElement  属性，而不是 parentNode  属性，并且有不同的导航方法。</span><span class="sxs-lookup"><span data-stu-id="93821-106">Instead, an attribute is a property of an element and is owned by an element, has an **OwnerElement** property and not a **parentNode** property, and has distinct methods of navigation.</span></span>

<span data-ttu-id="93821-107">如果当前节点是元素，请使用 HasAttribute  方法，确定是否有任何与此元素关联的属性。</span><span class="sxs-lookup"><span data-stu-id="93821-107">When the current node is an element, use the **HasAttribute** method to see if there are any attributes associated with the element.</span></span> <span data-ttu-id="93821-108">如果已知元素具有属性，有多种方法可以访问这些属性。</span><span class="sxs-lookup"><span data-stu-id="93821-108">Once it is known that an element has attributes, there are multiple methods for accessing attributes.</span></span> <span data-ttu-id="93821-109">若要从元素中检索一个属性，可以使用 XmlElement  的 GetAttribute  和 GetAttributeNode  方法，也可以将所有属性获取到集合中。</span><span class="sxs-lookup"><span data-stu-id="93821-109">To retrieve a single attribute from the element, you can use the **GetAttribute** and **GetAttributeNode** methods of the **XmlElement** or you can obtain all the attributes into a collection.</span></span> <span data-ttu-id="93821-110">如果需要循环访问集合，获取集合就很有用。</span><span class="sxs-lookup"><span data-stu-id="93821-110">Obtaining the collection is useful if you need to iterate over the collection.</span></span> <span data-ttu-id="93821-111">如果需要元素中的所有属性，请使用元素的 Attributes  属性，将所有属性检索到集合中。</span><span class="sxs-lookup"><span data-stu-id="93821-111">If you want all attributes from the element, use the **Attributes** property of the element to retrieve all the attributes into a collection.</span></span>

## <a name="retrieving-all-attributes-into-a-collection"></a><span data-ttu-id="93821-112">将所有属性检索到一个集合中</span><span class="sxs-lookup"><span data-stu-id="93821-112">Retrieving All Attributes into a Collection</span></span>

<span data-ttu-id="93821-113">如果需要将元素节点的所有属性添加到集合中，请调用 XmlElement.Attributes  属性。</span><span class="sxs-lookup"><span data-stu-id="93821-113">If you want all the attributes of an element node put into a collection, call the **XmlElement.Attributes** property.</span></span> <span data-ttu-id="93821-114">这会获取包含元素的所有属性的 XmlAttributeCollection  。</span><span class="sxs-lookup"><span data-stu-id="93821-114">This gets the **XmlAttributeCollection** that contains all the attributes of an element.</span></span> <span data-ttu-id="93821-115">XmlAttributeCollection  类继承自 XmlNamedNode  映射。</span><span class="sxs-lookup"><span data-stu-id="93821-115">The **XmlAttributeCollection** class inherits from the **XmlNamedNode** map.</span></span> <span data-ttu-id="93821-116">因此，集合中的方法和属性除了包括 XmlAttributeCollection  类专用方法和属性（如 ItemOf  属性或 Append  方法）外，还包括命名节点映射中的方法和属性。</span><span class="sxs-lookup"><span data-stu-id="93821-116">Therefore, the methods and properties available on the collection include those available on a named node map in addition to methods and properties specific to the **XmlAttributeCollection** class, such as the **ItemOf** property or the **Append** method.</span></span> <span data-ttu-id="93821-117">属性集合中的每一项都表示 XmlAttribute  节点。</span><span class="sxs-lookup"><span data-stu-id="93821-117">Each item in the attribute collection represents an **XmlAttribute** node.</span></span> <span data-ttu-id="93821-118">若要确定元素的属性数，请获取 XmlAttributeCollection  ，并使用 Count  属性确定集合中的 XmlAttribute  节点数。</span><span class="sxs-lookup"><span data-stu-id="93821-118">To find the number of attributes on an element, get the **XmlAttributeCollection**, and use the **Count** property to see how many **XmlAttribute** nodes are in the collection.</span></span>

<span data-ttu-id="93821-119">下面的代码示例展示了如何检索属性集合，以及如何通过对循环索引使用 Count  方法来循环访问集合。</span><span class="sxs-lookup"><span data-stu-id="93821-119">The following code example shows how to retrieve an attribute collection and, using the **Count** method for the looping index, iterate over it.</span></span> <span data-ttu-id="93821-120">然后，此代码显示如何从集合中检索单个属性并显示其值。</span><span class="sxs-lookup"><span data-stu-id="93821-120">The code then shows how to retrieve a single attribute from the collection and display its value.</span></span>

```vb
Imports System.IO
Imports System.Xml

Public Class Sample

    Public Shared Sub Main()

        Dim doc As XmlDocument = New XmlDocument()
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" & _
               "<title>The Handmaid's Tale</title>" & _
               "<price>14.95</price>" & _
               "</book>")

        ' Move to an element.
        Dim myElement As XmlElement = doc.DocumentElement

        ' Create an attribute collection from the element.
        Dim attrColl As XmlAttributeCollection = myElement.Attributes

        ' Show the collection by iterating over it.
        Console.WriteLine("Display all the attributes in the collection...")
        Dim i As Integer
        For i = 0 To attrColl.Count - 1
            Console.Write("{0} = ", attrColl.ItemOf(i).Name)
            Console.Write("{0}", attrColl.ItemOf(i).Value)
            Console.WriteLine()
        Next

        ' Retrieve a single attribute from the collection; specifically, the
        ' attribute with the name "misc".
        Dim attr As XmlAttribute = attrColl("misc")

        ' Retrieve the value from that attribute.
        Dim miscValue As String = attr.InnerXml

        Console.WriteLine("Display the attribute information.")
        Console.WriteLine(miscValue)

    End Sub
End Class
```

```csharp
using System;
using System.IO;
using System.Xml;

public class Sample
{

    public static void Main()
    {
        XmlDocument doc = new XmlDocument();
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" +
                      "<title>The Handmaid's Tale</title>" +
                      "<price>14.95</price>" +
                      "</book>");

        // Move to an element.
        XmlElement myElement = doc.DocumentElement;

        // Create an attribute collection from the element.
        XmlAttributeCollection attrColl = myElement.Attributes;

        // Show the collection by iterating over it.
        Console.WriteLine("Display all the attributes in the collection...");
        for (int i = 0; i < attrColl.Count; i++)
        {
            Console.Write("{0} = ", attrColl[i].Name);
            Console.Write("{0}", attrColl[i].Value);
            Console.WriteLine();
        }

        // Retrieve a single attribute from the collection; specifically, the
        // attribute with the name "misc".
        XmlAttribute attr = attrColl["misc"];

        // Retrieve the value from that attribute.
        String miscValue = attr.InnerXml;

        Console.WriteLine("Display the attribute information.");
        Console.WriteLine(miscValue);

    }
}
```

<span data-ttu-id="93821-121">此示例显示以下输出内容：</span><span class="sxs-lookup"><span data-stu-id="93821-121">This example displays the following output:</span></span>

<span data-ttu-id="93821-122">**输出**</span><span class="sxs-lookup"><span data-stu-id="93821-122">**Output**</span></span>

<span data-ttu-id="93821-123">显示集合中的所有属性。</span><span class="sxs-lookup"><span data-stu-id="93821-123">Display all the attributes in the collection.</span></span>

```console
genre = novel
ISBN = 1-861001-57-5
misc = sale item
Display the attribute information.
sale item
```

<span data-ttu-id="93821-124">可按名称或索引号检索属性集合中的信息。</span><span class="sxs-lookup"><span data-stu-id="93821-124">The information in an attribute collection can be retrieved by name or index number.</span></span> <span data-ttu-id="93821-125">上例显示了如何按名称检索数据。</span><span class="sxs-lookup"><span data-stu-id="93821-125">The example above shows how to retrieve data by name.</span></span> <span data-ttu-id="93821-126">下例将显示如何按索引编号检索数据。</span><span class="sxs-lookup"><span data-stu-id="93821-126">The next example shows how to retrieve data by index number.</span></span>

<span data-ttu-id="93821-127">因为 XmlAttributeCollection  是可以按名称或按索引循环访问的集合，所以此示例展示了如何使用从零开始编制的索引，并使用下面的 baseuri.xml  文件作为输入文件，选择集合中的第一个属性。</span><span class="sxs-lookup"><span data-stu-id="93821-127">Because the **XmlAttributeCollection** is a collection and can be iterated over by name or index, this example shows selecting the first attribute out of the collection using a zero-based index and using the following file, **baseuri.xml**, as input.</span></span>

### <a name="input"></a><span data-ttu-id="93821-128">输入</span><span class="sxs-lookup"><span data-stu-id="93821-128">Input</span></span>

```xml
<!-- XML fragment -->
<book genre="novel">
  <title>Pride And Prejudice</title>
</book>
```

```vb
Option Explicit On
Option Strict On

Imports System.IO
Imports System.Xml

Public Class Sample

    Public Shared Sub Main()
        ' Create the XmlDocument.
        Dim doc As New XmlDocument()
        doc.Load("http://localhost/baseuri.xml")

        ' Display information on the attribute node. The value
        ' returned for BaseURI is 'http://localhost/baseuri.xml'.
        Dim attr As XmlAttribute = doc.DocumentElement.Attributes(0)
        Console.WriteLine("Name of the attribute:  {0}", attr.Name)
        Console.WriteLine("Base URI of the attribute:  {0}", attr.BaseURI)
        Console.WriteLine("The value of the attribute:  {0}", attr.InnerText)
    End Sub 'Main
End Class 'Sample
```

```csharp
using System;
using System.IO;
using System.Xml;

public class Sample
{
  public static void Main()
  {
    // Create the XmlDocument.
    XmlDocument doc = new XmlDocument();

    doc.Load("http://localhost/baseuri.xml");

    // Display information on the attribute node. The value
    // returned for BaseURI is 'http://localhost/baseuri.xml'.
    XmlAttribute attr = doc.DocumentElement.Attributes[0];
    Console.WriteLine("Name of the attribute:  {0}", attr.Name);
    Console.WriteLine("Base URI of the attribute:  {0}", attr.BaseURI);
    Console.WriteLine("The value of the attribute:  {0}", attr.InnerText);
  }
}
```

## <a name="retrieving-an-individual-attribute-node"></a><span data-ttu-id="93821-129">检索单个属性节点</span><span class="sxs-lookup"><span data-stu-id="93821-129">Retrieving an Individual Attribute Node</span></span>

<span data-ttu-id="93821-130">若要从元素中检索单个属性节点，请使用 <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="93821-130">To retrieve a single attribute node from an element, the <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType> method is used.</span></span> <span data-ttu-id="93821-131">它返回类型为 XmlAttribute  的对象。</span><span class="sxs-lookup"><span data-stu-id="93821-131">It returns an object of type **XmlAttribute**.</span></span> <span data-ttu-id="93821-132">有了 XmlAttribute  对象后，<xref:System.Xml.XmlAttribute?displayProperty=nameWithType> 类中的所有方法和属性都可用于此对象，如查找 OwnerElement  。</span><span class="sxs-lookup"><span data-stu-id="93821-132">Once you have an **XmlAttribute**, all the methods and properties available in the <xref:System.Xml.XmlAttribute?displayProperty=nameWithType> class are available on that object, such as finding the **OwnerElement**.</span></span>

```vb
Imports System.IO
Imports System.Xml

Public Class Sample

    Public Shared Sub Main()

        Dim doc As XmlDocument = New XmlDocument()
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" & _
               "<title>The Handmaid's Tale</title>" & _
               "<price>14.95</price>" & _
               "</book>")

        ' Move to an element.
        Dim root As XmlElement
        root = doc.DocumentElement

        ' Get an attribute.
        Dim attr As XmlAttribute
        attr = root.GetAttributeNode("ISBN")

        ' Display the value of the attribute.
        Dim attrValue As String
        attrValue = attr.InnerXml
        Console.WriteLine(attrValue)

    End Sub
End Class
```

```csharp
using System;
using System.IO;
using System.Xml;

 public class Sample
 {
      public static void Main()
      {
    XmlDocument doc = new XmlDocument();
     doc.LoadXml("<book genre='novel' ISBN='1-861003-78' misc='sale item'>" +
                   "<title>The Handmaid's Tale</title>" +
                   "<price>14.95</price>" +
                   "</book>");

    // Move to an element.
     XmlElement root = doc.DocumentElement;

    // Get an attribute.
     XmlAttribute attr = root.GetAttributeNode("ISBN");

    // Display the value of the attribute.
     String attrValue = attr.InnerXml;
     Console.WriteLine(attrValue);

    }
}
```

<span data-ttu-id="93821-133">您也可以如前例所示，从属性集合中检索单个属性节点。</span><span class="sxs-lookup"><span data-stu-id="93821-133">You can also do as shown in the previous example, where a single attribute node is retrieved from the attribute collection.</span></span> <span data-ttu-id="93821-134">下面的代码示例展示了如何编写一行代码，以按索引号从 XML 文档树的根节点（亦称为 DocumentElement  属性）检索一个属性。</span><span class="sxs-lookup"><span data-stu-id="93821-134">The following code example shows how one line of code can be written to retrieve a single attribute by index number from the root of the XML document tree, also known as the **DocumentElement** property.</span></span>

```csharp
XmlAttribute attr = doc.DocumentElement.Attributes[0];
```

## <a name="see-also"></a><span data-ttu-id="93821-135">请参阅</span><span class="sxs-lookup"><span data-stu-id="93821-135">See also</span></span>

- [<span data-ttu-id="93821-136">XML 文档对象模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="93821-136">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)

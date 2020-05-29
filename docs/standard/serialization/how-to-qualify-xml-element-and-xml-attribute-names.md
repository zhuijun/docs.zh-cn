---
title: 如何限定 XML 元素和 XML 属性名
description: 本文说明如何在 XML 文档中限定 XML 元素和 XML 属性的名称。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- qualifying XML names
- qualifying XML elements
- XML namespaces, qualifying elements and names in
ms.assetid: 44719f90-7e15-42e8-a9e2-282287e2b5bf
ms.openlocfilehash: 6c29e03d9ce28e5b0abc68a5d7e8d82f4485ac93
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378417"
---
# <a name="how-to-qualify-xml-element-and-xml-attribute-names"></a><span data-ttu-id="72811-103">如何限定 XML 元素和 XML 属性名</span><span class="sxs-lookup"><span data-stu-id="72811-103">How to qualify XML element and XML attribute names</span></span>

<span data-ttu-id="72811-104"><xref:System.Xml.Serialization.XmlSerializerNamespaces> 类的实例所包含的 XML 命名空间必须符合万维网联合会 (W3C) 规范，即 [XML 中的命名空间](https://www.w3.org/TR/REC-xml-names/)。</span><span class="sxs-lookup"><span data-stu-id="72811-104">XML namespaces contained by instances of the <xref:System.Xml.Serialization.XmlSerializerNamespaces> class must conform to the World Wide Web Consortium (W3C) specification called [Namespaces in XML](https://www.w3.org/TR/REC-xml-names/).</span></span>

<span data-ttu-id="72811-105">XML 命名空间提供了一种方法，用来限定 XML 文档中 XML 元素和 XML 特性的名称。</span><span class="sxs-lookup"><span data-stu-id="72811-105">XML namespaces provide a method for qualifying the names of XML elements and XML attributes in XML documents.</span></span> <span data-ttu-id="72811-106">限定名由前缀和本地名称组成，两者之间用冒号分隔。</span><span class="sxs-lookup"><span data-stu-id="72811-106">A qualified name consists of a prefix and a local name, separated by a colon.</span></span> <span data-ttu-id="72811-107">前缀仅用作占位符；它将映射到用于指定命名空间的 URI。</span><span class="sxs-lookup"><span data-stu-id="72811-107">The prefix functions only as a placeholder; it is mapped to a URI that specifies a namespace.</span></span> <span data-ttu-id="72811-108">统一管理的 URI 命名空间和本地名称的组合能够产生保证为全局唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="72811-108">The combination of the universally managed URI namespace and the local name produces a name that is guaranteed to be universally unique.</span></span>

<span data-ttu-id="72811-109">通过创建 `XmlSerializerNamespaces` 的实例，并向对象中添加命名空间对，可以指定在 XML 文档中使用的前缀。</span><span class="sxs-lookup"><span data-stu-id="72811-109">By creating an instance of `XmlSerializerNamespaces` and adding the namespace pairs to the object, you can specify the prefixes used in an XML document.</span></span>

## <a name="to-create-qualified-names-in-an-xml-document"></a><span data-ttu-id="72811-110">在 XML 文档中创建限定名称</span><span class="sxs-lookup"><span data-stu-id="72811-110">To create qualified names in an XML document</span></span>

1. <span data-ttu-id="72811-111">创建 `XmlSerializerNamespaces` 类的一个实例。</span><span class="sxs-lookup"><span data-stu-id="72811-111">Create an instance of the `XmlSerializerNamespaces` class.</span></span>

2. <span data-ttu-id="72811-112">将所有的前缀和命名空间对添加至 `XmlSerializerNamespaces`。</span><span class="sxs-lookup"><span data-stu-id="72811-112">Add all prefixes and namespace pairs to the `XmlSerializerNamespaces`.</span></span>

3. <span data-ttu-id="72811-113">对每个由 `System.Xml.Serialization` 序列化为 XML 文档的成员或类应用相应的 <xref:System.Xml.Serialization.XmlSerializer> 特性。</span><span class="sxs-lookup"><span data-stu-id="72811-113">Apply the appropriate `System.Xml.Serialization` attribute to each member or class that the <xref:System.Xml.Serialization.XmlSerializer> is to serialize into an XML document.</span></span>

    <span data-ttu-id="72811-114">可用的特性包括：<xref:System.Xml.Serialization.XmlAnyElementAttribute>、<xref:System.Xml.Serialization.XmlArrayAttribute>、<xref:System.Xml.Serialization.XmlArrayItemAttribute>、<xref:System.Xml.Serialization.XmlAttributeAttribute>、<xref:System.Xml.Serialization.XmlElementAttribute>、<xref:System.Xml.Serialization.XmlRootAttribute> 和 <xref:System.Xml.Serialization.XmlTypeAttribute>。</span><span class="sxs-lookup"><span data-stu-id="72811-114">The available attributes are: <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute>, and <xref:System.Xml.Serialization.XmlTypeAttribute>.</span></span>

4. <span data-ttu-id="72811-115">将每个属性 (Attribute) 的 `Namespace` 属性 (Property) 设置为 `XmlSerializerNamespaces` 的命名空间值之一。</span><span class="sxs-lookup"><span data-stu-id="72811-115">Set the `Namespace` property of each attribute to one of the namespace values from the `XmlSerializerNamespaces`.</span></span>

5. <span data-ttu-id="72811-116">将 `XmlSerializerNamespaces` 传递到 `Serialize` 的 `XmlSerializer` 方法。</span><span class="sxs-lookup"><span data-stu-id="72811-116">Pass the `XmlSerializerNamespaces` to the `Serialize` method of the `XmlSerializer`.</span></span>

## <a name="example"></a><span data-ttu-id="72811-117">示例</span><span class="sxs-lookup"><span data-stu-id="72811-117">Example</span></span>

<span data-ttu-id="72811-118">下面的示例创建一个 `XmlSerializerNamespaces`，并向对象添加两个前缀和命名空间对。</span><span class="sxs-lookup"><span data-stu-id="72811-118">The following example creates an `XmlSerializerNamespaces`, and adds two prefix and namespace pairs to the object.</span></span> <span data-ttu-id="72811-119">该代码创建了用来序列化 `XmlSerializer` 类实例的 `Books`，</span><span class="sxs-lookup"><span data-stu-id="72811-119">The code creates an `XmlSerializer` that is used to serialize an instance of the `Books` class.</span></span> <span data-ttu-id="72811-120">并通过 `Serialize` 调用 `XmlSerializerNamespaces` 方法，使 XML 可以包含带前缀的命名空间。</span><span class="sxs-lookup"><span data-stu-id="72811-120">The code calls the `Serialize` method with the `XmlSerializerNamespaces`, allowing the XML to contain prefixed namespaces.</span></span>

```vb
Imports System.IO
Imports System.Xml
Imports System.Xml.Serialization

Public Module Program

    Public Sub Main()
        SerializeObject("XmlNamespaces.xml")
    End Sub

    Public Sub SerializeObject(filename As String)
        Dim mySerializer As New XmlSerializer(GetType(Books))
        ' Writing a file requires a TextWriter.
        Dim myWriter As New StreamWriter(filename)

        ' Creates an XmlSerializerNamespaces and adds two
        ' prefix-namespace pairs.
        Dim myNamespaces As New XmlSerializerNamespaces()
        myNamespaces.Add("books", "http://www.cpandl.com")
        myNamespaces.Add("money", "http://www.cohowinery.com")

        ' Creates a Book.
        Dim myBook As New Book()
        myBook.TITLE = "A Book Title"
        Dim myPrice As New Price()
        myPrice.price = CDec(9.95)
        myPrice.currency = "US Dollar"
        myBook.PRICE = myPrice
        Dim myBooks As New Books()
        myBooks.Book = myBook
        mySerializer.Serialize(myWriter, myBooks, myNamespaces)
        myWriter.Close()
    End Sub
End Module

Public Class Books
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _
    Public Book As Book
End Class

<XmlType([Namespace] := "http://www.cpandl.com")> _
Public Class Book
    <XmlElement([Namespace] := "http://www.cpandl.com")> _
    Public TITLE As String
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _
    Public PRICE As Price
End Class

Public Class Price
    <XmlAttribute([Namespace] := "http://www.cpandl.com")> _
    Public currency As String
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _
    Public price As Decimal
End Class
```

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Serialization;

public class Program
{
    public static void Main()
    {
        SerializeObject("XmlNamespaces.xml");
    }

    public static void SerializeObject(string filename)
    {
        var mySerializer = new XmlSerializer(typeof(Books));
        // Writing a file requires a TextWriter.
        TextWriter myWriter = new StreamWriter(filename);

        // Creates an XmlSerializerNamespaces and adds two
        // prefix-namespace pairs.
        var myNamespaces = new XmlSerializerNamespaces();
        myNamespaces.Add("books", "http://www.cpandl.com");
        myNamespaces.Add("money", "http://www.cohowinery.com");

        // Creates a Book.
        var myBook = new Book();
        myBook.TITLE = "A Book Title";
        var myPrice = new Price();
        myPrice.price = (decimal) 9.95;
        myPrice.currency = "US Dollar";
        myBook.PRICE = myPrice;
        var myBooks = new Books();
        myBooks.Book = myBook;
        mySerializer.Serialize(myWriter, myBooks, myNamespaces);
        myWriter.Close();
    }
}

public class Books
{
    [XmlElement(Namespace = "http://www.cohowinery.com")]
    public Book Book;
}

[XmlType(Namespace ="http://www.cpandl.com")]
public class Book
{
    [XmlElement(Namespace = "http://www.cpandl.com")]
    public string TITLE;
    [XmlElement(Namespace ="http://www.cohowinery.com")]
    public Price PRICE;
}

public class Price
{
    [XmlAttribute(Namespace = "http://www.cpandl.com")]
    public string currency;
    [XmlElement(Namespace = "http://www.cohowinery.com")]
    public decimal price;
}
```

## <a name="see-also"></a><span data-ttu-id="72811-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="72811-121">See also</span></span>

- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="72811-122">XML 架构定义工具和 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="72811-122">The XML Schema Definition Tool and XML Serialization</span></span>](the-xml-schema-definition-tool-and-xml-serialization.md)
- [<span data-ttu-id="72811-123">XML 序列化简介</span><span class="sxs-lookup"><span data-stu-id="72811-123">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="72811-124">XmlSerializer 类</span><span class="sxs-lookup"><span data-stu-id="72811-124">XmlSerializer Class</span></span>](xref:System.Xml.Serialization.XmlSerializer)
- [<span data-ttu-id="72811-125">用来控制 XML 序列化的属性</span><span class="sxs-lookup"><span data-stu-id="72811-125">Attributes That Control XML Serialization</span></span>](attributes-that-control-xml-serialization.md)
- [<span data-ttu-id="72811-126">如何：指定 XML 流的替代元素名称</span><span class="sxs-lookup"><span data-stu-id="72811-126">How to: Specify an Alternate Element Name for an XML Stream</span></span>](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)
- [<span data-ttu-id="72811-127">如何：序列化对象</span><span class="sxs-lookup"><span data-stu-id="72811-127">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="72811-128">如何：反序列化对象</span><span class="sxs-lookup"><span data-stu-id="72811-128">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)

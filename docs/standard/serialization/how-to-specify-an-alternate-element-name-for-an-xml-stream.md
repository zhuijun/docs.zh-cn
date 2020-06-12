---
title: 如何：指定 XML 流的替代元素名称
description: 了解如何使用替代元素名称创建 XML 流，例如，对于需要大体相同信息（略有差异）的 XML Web service。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XML serialization, overriding
- serialization, overriding
- XML stream, specifying alternate element name for
- overriding XML serialization
- classes, overriding
- overriding classes
ms.assetid: 5cc1c0b0-f94b-4525-9a41-88a582cd6668
ms.openlocfilehash: d7e482ee6e1e1a7318ab05766508537d4b87789e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "84289585"
---
# <a name="how-to-specify-an-alternate-element-name-for-an-xml-stream"></a><span data-ttu-id="72122-103">如何：指定 XML 流的替代元素名称</span><span class="sxs-lookup"><span data-stu-id="72122-103">How to: Specify an Alternate Element Name for an XML Stream</span></span>
  
<span data-ttu-id="72122-104">使用 <xref:System.Xml.Serialization.XmlSerializer>，可以用同一组类生成多个 XML 流。</span><span class="sxs-lookup"><span data-stu-id="72122-104">Using the <xref:System.Xml.Serialization.XmlSerializer>, you can generate more than one XML stream with the same set of classes.</span></span> <span data-ttu-id="72122-105">由于两个不同的 XML Web services 需要的基本信息相同（略有差异），因此您或许希望用同一组类生成多个 XML 流。</span><span class="sxs-lookup"><span data-stu-id="72122-105">You might want to do this because two different XML Web services require the same basic information, with only slight differences.</span></span> <span data-ttu-id="72122-106">例如，假设有两个处理书籍订单的 XML Web services，它们都需要 ISBN 号。</span><span class="sxs-lookup"><span data-stu-id="72122-106">For example, imagine two XML Web services that process orders for books, and thus both require ISBN numbers.</span></span> <span data-ttu-id="72122-107">一个服务使用标记 \<ISBN>，而另一个使用标记 \<BookID>。</span><span class="sxs-lookup"><span data-stu-id="72122-107">One service uses the tag \<ISBN> while the second uses the tag \<BookID>.</span></span> <span data-ttu-id="72122-108">您已经有一个名为 `Book` 的类，其中包含名为 `ISBN` 的字段。</span><span class="sxs-lookup"><span data-stu-id="72122-108">You have a class named `Book` that contains a field named `ISBN`.</span></span> <span data-ttu-id="72122-109">当序列化 `Book` 类的实例时，该实例将在默认情况下使用成员名称 (ISBN) 作为标记元素名称。</span><span class="sxs-lookup"><span data-stu-id="72122-109">When an instance of the `Book` class is serialized, it will, by default, use the member name (ISBN) as the tag element name.</span></span> <span data-ttu-id="72122-110">对于第一个 XML Web services，以上行为与预期相同。</span><span class="sxs-lookup"><span data-stu-id="72122-110">For the first XML Web service, this is as expected.</span></span> <span data-ttu-id="72122-111">但如果要将 XML 流发送至第二个 XML Web services，则必须重写序列化，以便使标记的元素名称采用 `BookID`。</span><span class="sxs-lookup"><span data-stu-id="72122-111">But to send the XML stream to the second XML Web service, you must override the serialization so that the tag's element name is `BookID`.</span></span>  
  
## <a name="to-create-an-xml-stream-with-an-alternate-element-name"></a><span data-ttu-id="72122-112">用替代元素名称创建 XML 流</span><span class="sxs-lookup"><span data-stu-id="72122-112">To create an XML stream with an alternate element name</span></span>  
  
1. <span data-ttu-id="72122-113">创建 <xref:System.Xml.Serialization.XmlElementAttribute> 类的一个实例。</span><span class="sxs-lookup"><span data-stu-id="72122-113">Create an instance of the <xref:System.Xml.Serialization.XmlElementAttribute> class.</span></span>  
  
2. <span data-ttu-id="72122-114">将 <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> 的 <xref:System.Xml.Serialization.XmlElementAttribute> 设置为“BookID”。</span><span class="sxs-lookup"><span data-stu-id="72122-114">Set the <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> of the <xref:System.Xml.Serialization.XmlElementAttribute> to "BookID".</span></span>  
  
3. <span data-ttu-id="72122-115">创建 <xref:System.Xml.Serialization.XmlAttributes> 类的一个实例。</span><span class="sxs-lookup"><span data-stu-id="72122-115">Create an instance of the <xref:System.Xml.Serialization.XmlAttributes> class.</span></span>  
  
4. <span data-ttu-id="72122-116">向通过 `XmlElementAttribute` 的 <xref:System.Xml.Serialization.XmlAttributes.XmlElements%2A> 属性访问的集合中添加 <xref:System.Xml.Serialization.XmlAttributes> 对象。</span><span class="sxs-lookup"><span data-stu-id="72122-116">Add the `XmlElementAttribute` object to the collection accessed through the <xref:System.Xml.Serialization.XmlAttributes.XmlElements%2A> property of <xref:System.Xml.Serialization.XmlAttributes> .</span></span>  
  
5. <span data-ttu-id="72122-117">创建 <xref:System.Xml.Serialization.XmlAttributeOverrides> 类的一个实例。</span><span class="sxs-lookup"><span data-stu-id="72122-117">Create an instance of the <xref:System.Xml.Serialization.XmlAttributeOverrides> class.</span></span>  
  
6. <span data-ttu-id="72122-118">将 `XmlAttributes` 添加至 <xref:System.Xml.Serialization.XmlAttributeOverrides>，同时传递要重写的对象类型以及要被重写的成员名称。</span><span class="sxs-lookup"><span data-stu-id="72122-118">Add the `XmlAttributes` to the <xref:System.Xml.Serialization.XmlAttributeOverrides>, passing the type of the object to override and the name of the member being overridden.</span></span>  
  
7. <span data-ttu-id="72122-119">用 `XmlSerializer` 创建 `XmlAttributeOverrides` 类的实例。</span><span class="sxs-lookup"><span data-stu-id="72122-119">Create an instance of the `XmlSerializer` class with `XmlAttributeOverrides`.</span></span>  
  
8. <span data-ttu-id="72122-120">创建 `Book` 类的实例，并将其序列化或反序列化。</span><span class="sxs-lookup"><span data-stu-id="72122-120">Create an instance of the `Book` class, and serialize or deserialize it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72122-121">示例</span><span class="sxs-lookup"><span data-stu-id="72122-121">Example</span></span>  
  
```vb  
Public Function SerializeOverride()  
    ' Creates an XmlElementAttribute with the alternate name.  
    Dim myElementAttribute As XmlElementAttribute = _  
    New XmlElementAttribute()  
    myElementAttribute.ElementName = "BookID"  
    Dim myAttributes As XmlAttributes = New XmlAttributes()  
    myAttributes.XmlElements.Add(myElementAttribute)  
    Dim myOverrides As XmlAttributeOverrides = New XmlAttributeOverrides()  
    myOverrides.Add(typeof(Book), "ISBN", myAttributes)  
    Dim mySerializer As XmlSerializer = _  
    New XmlSerializer(GetType(Book), myOverrides)  
    Dim b As Book = New Book()  
    b.ISBN = "123456789"  
    ' Creates a StreamWriter to write the XML stream to.  
    Dim writer As StreamWriter = New StreamWriter("Book.xml")  
    mySerializer.Serialize(writer, b);  
End Class  
```  
  
```csharp  
public void SerializeOverride()  
{  
    // Creates an XmlElementAttribute with the alternate name.  
    XmlElementAttribute myElementAttribute = new XmlElementAttribute();  
    myElementAttribute.ElementName = "BookID";  
    XmlAttributes myAttributes = new XmlAttributes();  
    myAttributes.XmlElements.Add(myElementAttribute);  
    XmlAttributeOverrides myOverrides = new XmlAttributeOverrides();  
    myOverrides.Add(typeof(Book), "ISBN", myAttributes);  
    XmlSerializer mySerializer =
    new XmlSerializer(typeof(Book), myOverrides)  
    Book b = new Book();  
    b.ISBN = "123456789"  
    // Creates a StreamWriter to write the XML stream to.  
    StreamWriter writer = new StreamWriter("Book.xml");  
    mySerializer.Serialize(writer, b);  
}  
```  
  
 <span data-ttu-id="72122-122">XML 流可能如下所示。</span><span class="sxs-lookup"><span data-stu-id="72122-122">The XML stream might resemble the following.</span></span>  
  
```xml  
<Book>  
    <BookID>123456789</BookID>  
</Book>  
```  
  
## <a name="see-also"></a><span data-ttu-id="72122-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="72122-123">See also</span></span>

- <xref:System.Xml.Serialization.XmlElementAttribute>
- <xref:System.Xml.Serialization.XmlAttributes>
- <xref:System.Xml.Serialization.XmlAttributeOverrides>
- [<span data-ttu-id="72122-124">XML 和 SOAP 序列化</span><span class="sxs-lookup"><span data-stu-id="72122-124">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="72122-125">如何：序列化对象</span><span class="sxs-lookup"><span data-stu-id="72122-125">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="72122-126">如何：反序列化对象</span><span class="sxs-lookup"><span data-stu-id="72122-126">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)

---
title: 强类型扩展示例
ms.date: 03/30/2017
ms.assetid: 02220f11-1a83-441c-9e5a-85f9a9367572
ms.openlocfilehash: e8c3bf202a1fb76d383f0a3fe15084d19a1d51fb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600875"
---
# <a name="strongly-typed-extensions-sample"></a><span data-ttu-id="3b32b-102">强类型扩展示例</span><span class="sxs-lookup"><span data-stu-id="3b32b-102">Strongly typed extensions sample</span></span>

<span data-ttu-id="3b32b-103">此示例使用 <xref:System.ServiceModel.Syndication.SyndicationFeed> 类作为示例。</span><span class="sxs-lookup"><span data-stu-id="3b32b-103">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="3b32b-104">但是，此示例中演示的模式可用于支持扩展数据的所有 Syndication 类。</span><span class="sxs-lookup"><span data-stu-id="3b32b-104">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data.</span></span>  
  
 <span data-ttu-id="3b32b-105">联合对象模型（<xref:System.ServiceModel.Syndication.SyndicationFeed>、<xref:System.ServiceModel.Syndication.SyndicationItem> 和相关类）支持通过使用 <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> 和 <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> 属性对扩展数据进行松散类型的访问。</span><span class="sxs-lookup"><span data-stu-id="3b32b-105">The Syndication object model (<xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, and related classes) supports loosely-typed access to extension data by using the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> properties.</span></span> <span data-ttu-id="3b32b-106">此示例演示如何通过实现的自定义派生类 <xref:System.ServiceModel.Syndication.SyndicationFeed> 并 <xref:System.ServiceModel.Syndication.SyndicationItem> 使特定于应用程序的扩展成为强类型属性，来提供对扩展数据的强类型访问。</span><span class="sxs-lookup"><span data-stu-id="3b32b-106">This sample shows how to provide strongly typed access to extension data by implementing custom derived classes of <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> that make available certain application-specific extensions as strongly typed properties.</span></span>  
  
 <span data-ttu-id="3b32b-107">此示例演示如何实现建议的 Atom Threading Extensions RFC 中定义的一个扩展元素，以作为示例。</span><span class="sxs-lookup"><span data-stu-id="3b32b-107">As an example, this sample shows how to implement an extension element defined in the proposed Atom Threading Extensions RFC.</span></span> <span data-ttu-id="3b32b-108">此示例仅用于演示，不应作为该建议规范的完整实现。</span><span class="sxs-lookup"><span data-stu-id="3b32b-108">This is for demonstration purposes only and this sample is not intended to be a full implementation of the proposed specification.</span></span>  
  
## <a name="sample-xml"></a><span data-ttu-id="3b32b-109">示例 XML</span><span class="sxs-lookup"><span data-stu-id="3b32b-109">Sample XML</span></span>  
 <span data-ttu-id="3b32b-110">下面的 XML 示例显示一个具有附加的 `<in-reply-to>` 扩展元素的 Atom 1.0 项。</span><span class="sxs-lookup"><span data-stu-id="3b32b-110">The following XML example shows an Atom 1.0 entry with an additional `<in-reply-to>` extension element.</span></span>  
  
```xml  
<entry>  
    <id>tag:example.org,2005:1,2</id>  
    <title type="text">Another response to the original</title>  
    <summary type="text">  
         This is a response to the original entry</summary>  
    <updated>2006-03-01T12:12:13Z</updated>  
    <link href="http://www.example.org/entries/1/2" />  
    <in-reply-to p3:ref="tag:example.org,2005:1"
                 p3:href="http://www.example.org/entries/1"
                 p3:type="application/xhtml+xml"
                 xmlns:p3="http://contoso.org/syndication/thread/1.0"
                 xmlns="http://contoso.org/syndication/thread/1.0">  
      <anotherElement xmlns="http://www.w3.org/2005/Atom">  
                     Some more data</anotherElement>  
      <aDifferentElement xmlns="http://www.w3.org/2005/Atom">  
                     Even more data</aDifferentElement>  
    </in-reply-to>  
</entry>  
```  
  
 <span data-ttu-id="3b32b-111">`<in-reply-to>`元素指定了三个必需特性 `ref` （ `type` 和 `href` ），同时还允许存在其他扩展特性和扩展元素。</span><span class="sxs-lookup"><span data-stu-id="3b32b-111">The `<in-reply-to>` element specifies three required attributes (`ref`, `type` and `href`) while also allowing for the presence of additional extension attributes and extension elements.</span></span>  
  
## <a name="modeling-the-in-reply-to-element"></a><span data-ttu-id="3b32b-112">对 In-Reply-To 元素建模</span><span class="sxs-lookup"><span data-stu-id="3b32b-112">Modeling the In-Reply-To element</span></span>  
 <span data-ttu-id="3b32b-113">在此示例中，`<in-reply-to>` 元素建模为实现 <xref:System.Xml.Serialization.IXmlSerializable> 的 CLR，从而可以与 <xref:System.Runtime.Serialization.DataContractSerializer> 一起使用。</span><span class="sxs-lookup"><span data-stu-id="3b32b-113">In this sample, the `<in-reply-to>` element is modeled as CLR that implements <xref:System.Xml.Serialization.IXmlSerializable>, which enables its use with the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="3b32b-114">它还实现了一些方法和属性来访问元素的数据，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="3b32b-114">It also implements some methods and properties for accessing the element's data, as shown in the following sample code.</span></span>  
  
```csharp  
[XmlRoot(ElementName = "in-reply-to", Namespace = "http://contoso.org/syndication/thread/1.0")]  
public class InReplyToElement : IXmlSerializable  
{  
    internal const string ElementName = "in-reply-to";  
    internal const string NsUri =
                  "http://contoso.org/syndication/thread/1.0";  
    private Dictionary<XmlQualifiedName, string> extensionAttributes;  
    private Collection<XElement> extensionElements;  
  
    public InReplyToElement()  
    {  
        this.extensionElements = new Collection<XElement>();  
        this.extensionAttributes = new Dictionary<XmlQualifiedName,
                                                          string>();  
    }  
  
    public Dictionary<XmlQualifiedName, string> AttributeExtensions  
    {  
        get { return this.extensionAttributes; }  
    }  
  
    public Collection<XElement> ElementExtensions  
    {  
        get { return this.extensionElements; }  
    }  
  
    public Uri Href  
    { get; set; }  
  
    public string MediaType  
    { get; set; }  
  
    public string Ref  
    { get; set; }  
  
    public Uri Source  
    { get; set; }  
}  
```  
  
 <span data-ttu-id="3b32b-115">`InReplyToElement` 类实现所需属性 (Attribute) 的属性 (Property)（`HRef`、`MediaType` 和 `Source`）以及用于保存 <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> 和 <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> 的集合。</span><span class="sxs-lookup"><span data-stu-id="3b32b-115">The `InReplyToElement` class implements properties for the required attribute (`HRef`, `MediaType`, and `Source`) as well as collections to hold <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.</span></span>  
  
 <span data-ttu-id="3b32b-116">`InReplyToElement` 类实现 <xref:System.Xml.Serialization.IXmlSerializable> 接口，该接口允许直接控制从 XML 读取对象实例和向 XML 写入对象实例的方式。</span><span class="sxs-lookup"><span data-stu-id="3b32b-116">The `InReplyToElement` class implements the <xref:System.Xml.Serialization.IXmlSerializable> interface, which allows direct control over how object instances are read from and written to XML.</span></span> <span data-ttu-id="3b32b-117">`ReadXml` 方法首先从传递给它的 `Ref` 读取 `HRef`、`Source`、`MediaType` 和 <xref:System.Xml.XmlReader> 属性的值。</span><span class="sxs-lookup"><span data-stu-id="3b32b-117">The `ReadXml` method first reads the values for the `Ref`, `HRef`, `Source`, and `MediaType` properties from the <xref:System.Xml.XmlReader> passed to it.</span></span> <span data-ttu-id="3b32b-118">所有未知的属性都存储在 <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> 集合中。</span><span class="sxs-lookup"><span data-stu-id="3b32b-118">Any unknown attributes are stored in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection.</span></span> <span data-ttu-id="3b32b-119">读取所有属性之后，将调用 <xref:System.Xml.XmlReader.ReadStartElement> 使读取器前进到下一个元素。</span><span class="sxs-lookup"><span data-stu-id="3b32b-119">When all the attributes have been read, <xref:System.Xml.XmlReader.ReadStartElement> is called to advance the reader to the next element.</span></span> <span data-ttu-id="3b32b-120">由于由该类建模的元素没有所需的子元素，因此子元素缓冲到 `XElement` 实例中并存储在 <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> 集合中，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="3b32b-120">Because the element modeled by this class has no required children, the child elements get buffered into `XElement` instances and stored in the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection, as shown in the following code.</span></span>  
  
```csharp
public void ReadXml(System.Xml.XmlReader reader)  
{  
    bool isEmpty = reader.IsEmptyElement;  
  
    if (reader.HasAttributes)  
    {  
        for (int i = 0; i < reader.AttributeCount; i++)  
        {  
            reader.MoveToNextAttribute();  
  
            if (reader.NamespaceURI == "")  
            {  
                if (reader.LocalName == "ref")  
                {  
                    this.Ref = reader.Value;  
                }  
                else if (reader.LocalName == "href")  
                {  
                    this.Href = new Uri(reader.Value);  
                }  
                else if (reader.LocalName == "source")  
                {  
                    this.Source = new Uri(reader.Value);  
                }  
                else if (reader.LocalName == "type")  
                {  
                    this.MediaType = reader.Value;  
                }  
                else  
                {  
                    this.AttributeExtensions.Add(new
                                 XmlQualifiedName(reader.LocalName,
                                 reader.NamespaceURI),
                                 reader.Value);  
                }  
            }  
        }  
    }  
  
    reader.ReadStartElement();  
  
    if (!isEmpty)  
    {  
        while (reader.IsStartElement())  
        {  
            ElementExtensions.Add(  
                  (XElement) XElement.ReadFrom(reader));  
        }  
        reader.ReadEndElement();  
    }  
}  
```  
  
 <span data-ttu-id="3b32b-121">在 `WriteXml` 中，`InReplyToElement` 方法首先将 `Ref`、`HRef`、`Source` 和 `MediaType` 属性的值写出为 XML 属性。（`WriteXml` 并不负责编写实际的外部元素本身，该工作是由 `WriteXml` 的调用方完成的。）</span><span class="sxs-lookup"><span data-stu-id="3b32b-121">In `WriteXml`, the `InReplyToElement` method first writes out the values of the `Ref`, `HRef`, `Source`, and `MediaType` properties as XML attributes (`WriteXml` is not responsible for writing the actual outer element itself, as that done by the caller of `WriteXml`).</span></span> <span data-ttu-id="3b32b-122">它还将 <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> 和 <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> 的内容写入编写器，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="3b32b-122">It also writes the contents of the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> to the writer, as shown in the following code.</span></span>  
  
```csharp
public void WriteXml(System.Xml.XmlWriter writer)  
{  
    if (this.Ref != null)  
    {  
        writer.WriteAttributeString("ref", InReplyToElement.NsUri,
                                            this.Ref);  
    }  
    if (this.Href != null)  
    {  
        writer.WriteAttributeString("href", InReplyToElement.NsUri,
                                                this.Href.ToString());  
    }  
    if (this.Source != null)  
    {  
        writer.WriteAttributeString("source", InReplyToElement.NsUri,
                                              this.Source.ToString());  
    }  
    if (this.MediaType != null)  
    {  
        writer.WriteAttributeString("type", InReplyToElement.NsUri,
                                                    this.MediaType);  
    }  
  
    foreach (KeyValuePair<XmlQualifiedName, string> kvp in
                                             this.AttributeExtensions)  
    {  
        writer.WriteAttributeString(kvp.Key.Name, kvp.Key.Namespace,
                                                   kvp.Value);  
    }  
  
    foreach (XElement element in this.ElementExtensions)  
    {  
        element.WriteTo(writer);  
    }  
}  
```  
  
## <a name="threadedfeed-and-threadeditem"></a><span data-ttu-id="3b32b-123">ThreadedFeed 和 ThreadedItem</span><span class="sxs-lookup"><span data-stu-id="3b32b-123">ThreadedFeed and ThreadedItem</span></span>  
 <span data-ttu-id="3b32b-124">在此示例中，`SyndicationItems` 类对具有 `InReplyTo` 扩展的 `ThreadedItem` 进行建模。</span><span class="sxs-lookup"><span data-stu-id="3b32b-124">In the sample, `SyndicationItems` with `InReplyTo` extensions are modeled by the `ThreadedItem` class.</span></span> <span data-ttu-id="3b32b-125">同样，`ThreadedFeed` 类是一个其项是 `SyndicationFeed` 的所有实例的 `ThreadedItem`。</span><span class="sxs-lookup"><span data-stu-id="3b32b-125">Similarly, the `ThreadedFeed` class is a `SyndicationFeed` whose items are all instances of `ThreadedItem`.</span></span>  
  
 <span data-ttu-id="3b32b-126">`ThreadedFeed` 类从 `SyndicationFeed` 继承，并重写 `OnCreateItem` 以返回一个 `ThreadedItem`。</span><span class="sxs-lookup"><span data-stu-id="3b32b-126">The `ThreadedFeed` class inherits from `SyndicationFeed` and overrides `OnCreateItem` to return a `ThreadedItem`.</span></span> <span data-ttu-id="3b32b-127">它还实现用于将 `Items` 集合作为 `ThreadedItems` 访问的方法，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="3b32b-127">It also implements a method for accessing the `Items` collection as `ThreadedItems`, as shown in the following code.</span></span>  
  
```csharp
public class ThreadedFeed : SyndicationFeed  
{  
    public ThreadedFeed()  
    {  
    }  
  
    public IEnumerable<ThreadedItem> ThreadedItems  
    {  
        get  
        {  
            return this.Items.Cast<ThreadedItem>();  
        }  
    }  
  
    protected override SyndicationItem CreateItem()  
    {  
        return new ThreadedItem();  
    }  
}  
```  
  
 <span data-ttu-id="3b32b-128">类 `ThreadedItem` 继承自 `SyndicationItem` ，并 `InReplyToElement` 作为强类型属性进行。</span><span class="sxs-lookup"><span data-stu-id="3b32b-128">The class `ThreadedItem` inherits from `SyndicationItem` and makes `InReplyToElement` as a strongly typed property.</span></span> <span data-ttu-id="3b32b-129">这样便可以方便地对 `InReplyTo` 扩展数据进行编程访问。</span><span class="sxs-lookup"><span data-stu-id="3b32b-129">This provides for convenient programmatic access to the `InReplyTo` extension data.</span></span> <span data-ttu-id="3b32b-130">它还实现 `TryParseElement` 和 `WriteElementExtensions`，用于读取和写入其扩展数据，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="3b32b-130">It also implements `TryParseElement` and `WriteElementExtensions` for reading and writing its extension data, as shown in the following code.</span></span>  
  
```csharp
public class ThreadedItem : SyndicationItem  
{  
    private InReplyToElement inReplyTo;  
    // Constructors  
        public ThreadedItem()  
        {  
            inReplyTo = new InReplyToElement();  
        }  
  
        public ThreadedItem(string title, string content, Uri itemAlternateLink, string id, DateTimeOffset lastUpdatedTime) : base(title, content, itemAlternateLink, id, lastUpdatedTime)  
        {  
            inReplyTo = new InReplyToElement();  
        }  
  
    public InReplyToElement InReplyTo  
    {  
        get { return this.inReplyTo; }  
    }  
  
    protected override bool TryParseElement(  
                        System.Xml.XmlReader reader,
                        string version)  
    {  
        if (version == SyndicationVersions.Atom10 &&  
            reader.NamespaceURI == InReplyToElement.NsUri &&  
            reader.LocalName == InReplyToElement.ElementName)  
        {  
            this.inReplyTo = new InReplyToElement();  
  
            this.InReplyTo.ReadXml(reader);  
  
            return true;  
        }  
        else  
        {  
            return base.TryParseElement(reader, version);  
        }  
    }  
  
    protected override void WriteElementExtensions(XmlWriter writer,
                                                 string version)  
    {  
        if (this.InReplyTo != null &&
                     version == SyndicationVersions.Atom10)  
        {  
            writer.WriteStartElement(InReplyToElement.ElementName,
                                           InReplyToElement.NsUri);  
            this.InReplyTo.WriteXml(writer);  
            writer.WriteEndElement();  
        }  
  
        base.WriteElementExtensions(writer, version);  
    }  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3b32b-131">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="3b32b-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3b32b-132">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="3b32b-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3b32b-133">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="3b32b-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="3b32b-134">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="3b32b-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3b32b-135">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="3b32b-135">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3b32b-136">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="3b32b-136">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3b32b-137">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="3b32b-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3b32b-138">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="3b32b-138">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StronglyTypedExtensions`  

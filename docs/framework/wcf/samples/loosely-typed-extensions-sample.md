---
title: 松散类型化扩展示例
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: 5d3defacc4a0acee69e32667d0d9213320b3ccec
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202226"
---
# <a name="loosely-typed-extensions-sample"></a><span data-ttu-id="569eb-102">松散类型化扩展示例</span><span class="sxs-lookup"><span data-stu-id="569eb-102">Loosely-Typed Extensions Sample</span></span>
<span data-ttu-id="569eb-103">联合对象模型为处理扩展数据（在联合源的 XML 表示形式中存在，但是未由 <xref:System.ServiceModel.Syndication.SyndicationFeed> 和 <xref:System.ServiceModel.Syndication.SyndicationItem> 等类显式公开的信息）提供了丰富的支持。</span><span class="sxs-lookup"><span data-stu-id="569eb-103">The Syndication object model provides rich support for working with extension data—information that is present in a syndication feed's XML representation but not explicitly exposed by classes such as <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem>.</span></span> <span data-ttu-id="569eb-104">此示例阐释用来处理扩展数据的基本技术。</span><span class="sxs-lookup"><span data-stu-id="569eb-104">This sample illustrates the basic techniques for working with extension data.</span></span>  
  
 <span data-ttu-id="569eb-105">此示例使用 <xref:System.ServiceModel.Syndication.SyndicationFeed> 类作为示例。</span><span class="sxs-lookup"><span data-stu-id="569eb-105">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="569eb-106">但是，此示例中演示的模式可用于支持扩展数据的所有 Syndication 类。</span><span class="sxs-lookup"><span data-stu-id="569eb-106">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data:</span></span>  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a><span data-ttu-id="569eb-107">示例 XML</span><span class="sxs-lookup"><span data-stu-id="569eb-107">Sample XML</span></span>  
 <span data-ttu-id="569eb-108">下面是此示例中所使用的 XML 文档，可供您参考。</span><span class="sxs-lookup"><span data-stu-id="569eb-108">For reference, the following XML document is used in this sample.</span></span>  
  
```xml  
<?xml version="1.0" encoding="IBM437"?>  
<feed myAttribute="someValue" xmlns="http://www.w3.org/2005/Atom">  
  <title type="text"></title>  
  <id>uuid:8f60c7b3-a3c0-4de7-a642-2165d77ce3c1;id=1</id>  
  <updated>2007-09-07T22:15:34Z</updated>  
  <simpleString xmlns="">hello, world!</simpleString>  
  <simpleString xmlns="">another simple string</simpleString>  
  <DataContractExtension xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.d  
atacontract.org/2004/07/Microsoft.Syndication.Samples">  
    <Key>X</Key>  
    <Value>4</Value>  
  </DataContractExtension>  
  <XmlSerializerExtension xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://ww  
w.w3.org/2001/XMLSchema" xmlns="">  
    <Key>Y</Key>  
    <Value>8</Value>  
  </XmlSerializerExtension>  
  <xElementExtension xmlns="">  
    <Key attr1="someValue">Z</Key>  
    <Value attr1="someValue">15</Value>  
  </xElementExtension>  
</feed>  
```  
  
 <span data-ttu-id="569eb-109">此文档包含扩展数据的以下部分：</span><span class="sxs-lookup"><span data-stu-id="569eb-109">This document contains the following pieces of extension data:</span></span>  
  
- <span data-ttu-id="569eb-110">`myAttribute` 元素的 `<feed>` 属性。</span><span class="sxs-lookup"><span data-stu-id="569eb-110">The `myAttribute` attribute of the `<feed>` element.</span></span>  
  
- <span data-ttu-id="569eb-111">`<simpleString>` 元素。</span><span class="sxs-lookup"><span data-stu-id="569eb-111">`<simpleString>` element.</span></span>  
  
- <span data-ttu-id="569eb-112">`<DataContractExtension>` 元素。</span><span class="sxs-lookup"><span data-stu-id="569eb-112">`<DataContractExtension>` element.</span></span>  
  
- <span data-ttu-id="569eb-113">`<XmlSerializerExtension>` 元素。</span><span class="sxs-lookup"><span data-stu-id="569eb-113">`<XmlSerializerExtension>` element.</span></span>  
  
- <span data-ttu-id="569eb-114">`<xElementExtension>` 元素。</span><span class="sxs-lookup"><span data-stu-id="569eb-114">`<xElementExtension>` element.</span></span>  
  
## <a name="writing-extension-data"></a><span data-ttu-id="569eb-115">编写扩展数据</span><span class="sxs-lookup"><span data-stu-id="569eb-115">Writing Extension Data</span></span>  
 <span data-ttu-id="569eb-116">属性扩展是通过向 <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> 集合添加条目来创建的，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="569eb-116">Attribute extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection as shown in the following sample code.</span></span>  
  
```csharp  
//Attribute extensions are stored in a dictionary indexed by
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 <span data-ttu-id="569eb-117">元素扩展是通过向 <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> 集合添加条目来创建的。</span><span class="sxs-lookup"><span data-stu-id="569eb-117">Element extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection.</span></span> <span data-ttu-id="569eb-118">这些扩展可以是基本值（如字符串）、.NET Framework 对象的 XML 序列化或者是手动编码的 XML 节点。</span><span class="sxs-lookup"><span data-stu-id="569eb-118">These extensions can by basic values such as strings, XML serializations of .NET Framework objects, or XML nodes coded by hand.</span></span>  
  
 <span data-ttu-id="569eb-119">下面的示例代码创建一个名为 `simpleString` 的扩展元素。</span><span class="sxs-lookup"><span data-stu-id="569eb-119">The following sample code creates an extension element named `simpleString`.</span></span>  
  
```csharp  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 <span data-ttu-id="569eb-120">此元素的 XML 命名空间为空命名空间（""），其值为包含字符串 "hello，world！" 的文本节点。</span><span class="sxs-lookup"><span data-stu-id="569eb-120">The XML namespace for this element is the empty namespace ("") and its value is a text node that contains the string "hello, world!".</span></span>  
  
 <span data-ttu-id="569eb-121">如果要创建包含许多嵌套元素的复杂元素扩展，一种方法是使用 .NET Framework API 进行序列化（均支持 <xref:System.Runtime.Serialization.DataContractSerializer> 和 <xref:System.Xml.Serialization.XmlSerializer>），如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="569eb-121">One way to create complex element extensions that consist of many nested elements is to use the .NET Framework APIs for serialization (both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Xml.Serialization.XmlSerializer> are supported) as shown in the following examples.</span></span>  
  
```csharp  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 <span data-ttu-id="569eb-122">在本示例中，`DataContractExtension` 和 `XmlSerializerExtension` 属于自定义类型，它们是为与序列化程序协同使用而编写的。</span><span class="sxs-lookup"><span data-stu-id="569eb-122">In this example, the `DataContractExtension` and `XmlSerializerExtension` are custom types written for use with a serializer.</span></span>  
  
 <span data-ttu-id="569eb-123"><xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> 类还可以用来从 <xref:System.Xml.XmlReader> 实例创建元素扩展。</span><span class="sxs-lookup"><span data-stu-id="569eb-123">The <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> class can also be used to create element extensions from an <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="569eb-124">这允许与 XML 处理 API（如 <xref:System.Xml.Linq.XElement>）进行简单集成，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="569eb-124">This allows for easy integration with XML processing APIs such as <xref:System.Xml.Linq.XElement> as shown in the following sample code.</span></span>  
  
```csharp  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a><span data-ttu-id="569eb-125">读取扩展数据</span><span class="sxs-lookup"><span data-stu-id="569eb-125">Reading Extension Data</span></span>  
 <span data-ttu-id="569eb-126">属性扩展的值可以通过在 <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> 集合中按 <xref:System.Xml.XmlQualifiedName> 查找属性来获取，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="569eb-126">The values for attribute extensions can be obtained by looking up the attribute in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection by its <xref:System.Xml.XmlQualifiedName> as shown in the following sample code.</span></span>  
  
```csharp  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 <span data-ttu-id="569eb-127">元素扩展是借助于 `ReadElementExtensions<T>` 方法来访问的。</span><span class="sxs-lookup"><span data-stu-id="569eb-127">Element extensions are accessed using the `ReadElementExtensions<T>` method.</span></span>  
  
```csharp  
foreach( string s in feed2.ElementExtensions.ReadElementExtensions<string>("simpleString", ""))  
{  
    Console.WriteLine(s);  
}  
  
foreach (DataContractExtension dce in feed2.ElementExtensions.ReadElementExtensions<DataContractExtension>("DataContractExtension",  
"http://schemas.datacontract.org/2004/07/SyndicationExtensions"))  
{  
    Console.WriteLine(dce.ToString());  
}  
  
foreach (XmlSerializerExtension xse in feed2.ElementExtensions.ReadElementExtensions<XmlSerializerExtension>("XmlSerializerExtension", "", new XmlSerializer(typeof(XmlSerializerExtension))))  
{  
    Console.WriteLine(xse.ToString());  
}  
```  
  
 <span data-ttu-id="569eb-128">还可以通过使用 `XmlReader` 方法来在个别元素扩展上获取 <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader>。</span><span class="sxs-lookup"><span data-stu-id="569eb-128">It is also possible to obtain an `XmlReader` at individual element extensions by using the <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> method.</span></span>  
  
```csharp  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="569eb-129">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="569eb-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="569eb-130">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="569eb-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="569eb-131">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="569eb-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="569eb-132">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="569eb-132">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="569eb-133">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="569eb-133">The samples may already be installed on your machine.</span></span> <span data-ttu-id="569eb-134">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="569eb-134">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="569eb-135">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="569eb-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="569eb-136">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="569eb-136">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a><span data-ttu-id="569eb-137">请参阅</span><span class="sxs-lookup"><span data-stu-id="569eb-137">See also</span></span>

- [<span data-ttu-id="569eb-138">强类型扩展</span><span class="sxs-lookup"><span data-stu-id="569eb-138">Strongly typed Extensions</span></span>](../../../../docs/framework/wcf/samples/strongly-typed-extensions-sample.md)
- [<span data-ttu-id="569eb-139">WCF 联合</span><span class="sxs-lookup"><span data-stu-id="569eb-139">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)

---
title: 如何执行大型 XML 文档的流式转换 (C#)
description: 了解如何使用 C# 执行文本到 XML 的流式转换，以避免某些文件过度占用内存。
ms.date: 07/20/2015
ms.assetid: 5f16d1f8-5370-4b55-b0c8-e497df163037
ms.openlocfilehash: e1ab2866079b2244dc764271d7ba63173349e2f3
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104861"
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-c"></a><span data-ttu-id="23888-103">如何执行大型 XML 文档的流式转换 (C#)</span><span class="sxs-lookup"><span data-stu-id="23888-103">How to perform streaming transform of large XML documents (C#)</span></span>
<span data-ttu-id="23888-104">有时，你必须转换任意大的 XML 文件并在编写你的应用程序时可以预测应用程序的内存需求量。</span><span class="sxs-lookup"><span data-stu-id="23888-104">Sometimes you have to transform large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="23888-105">如果您试图用大 XML 文件填充 XML 树，则内存占用量将与文件大小成正比，也就是说会占用过多内存。</span><span class="sxs-lookup"><span data-stu-id="23888-105">If you try to populate an XML tree with a very large XML file, your memory usage will be proportional to the size of the file (that is, excessive).</span></span> <span data-ttu-id="23888-106">因此，您应改用流处理技术。</span><span class="sxs-lookup"><span data-stu-id="23888-106">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="23888-107">流处理技术最适合只需处理一次源文档的情况，您可以按文档顺序处理各个元素。</span><span class="sxs-lookup"><span data-stu-id="23888-107">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="23888-108">某些标准查询运算符（如 <xref:System.Linq.Enumerable.OrderBy%2A>）可以循环访问其源、收集所有数据、对数据排序，最后生成序列中的第一项。</span><span class="sxs-lookup"><span data-stu-id="23888-108">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="23888-109">请注意，如果使用可在生成第一项之前具体化源的查询运算符，则不会使应用程序保持小的内存需求量。</span><span class="sxs-lookup"><span data-stu-id="23888-109">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint for your application.</span></span>  
  
<span data-ttu-id="23888-110">即使使用[如何流处理可访问标头信息的 XML 片段 (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) 中说明的技术，在试图装配包含转换的文档的 XML 树时，内存占用量也会过大。</span><span class="sxs-lookup"><span data-stu-id="23888-110">Even if you use the technique described in [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md), if you try to assemble an XML tree that contains the transformed document, memory usage will be too great.</span></span>
  
 <span data-ttu-id="23888-111">主要方法有两种。</span><span class="sxs-lookup"><span data-stu-id="23888-111">There are two main approaches.</span></span> <span data-ttu-id="23888-112">一种方法是使用 <xref:System.Xml.Linq.XStreamingElement> 的延迟处理特性。</span><span class="sxs-lookup"><span data-stu-id="23888-112">One approach is to use the deferred processing characteristics of <xref:System.Xml.Linq.XStreamingElement>.</span></span> <span data-ttu-id="23888-113">另一种方法是创建一个 <xref:System.Xml.XmlWriter> 并使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 的功能将元素写入 <xref:System.Xml.XmlWriter>。</span><span class="sxs-lookup"><span data-stu-id="23888-113">Another approach is to create an <xref:System.Xml.XmlWriter>, and use the capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="23888-114">本主题演示这两种方法。</span><span class="sxs-lookup"><span data-stu-id="23888-114">This topic demonstrates both approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23888-115">示例</span><span class="sxs-lookup"><span data-stu-id="23888-115">Example</span></span>  
 <span data-ttu-id="23888-116">以下示例在[如何流处理可访问标头信息的 XML 片段 (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) 中的示例基础上建立。</span><span class="sxs-lookup"><span data-stu-id="23888-116">The following example builds on the example in [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>
  
 <span data-ttu-id="23888-117">本示例使用 <xref:System.Xml.Linq.XStreamingElement> 的延迟执行功能对输出进行流式处理。</span><span class="sxs-lookup"><span data-stu-id="23888-117">This example uses the deferred execution capabilities of <xref:System.Xml.Linq.XStreamingElement> to stream the output.</span></span> <span data-ttu-id="23888-118">本示例可在保持很小的内存需求量的同时转换非常大的文档。</span><span class="sxs-lookup"><span data-stu-id="23888-118">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="23888-119">请注意，自定义轴 (`StreamCustomerItem`) 经过专门编写，可以处理具有 `Customer`、`Name` 和 `Item` 元素，并且这些元素将按下面 Source.xml 文档排列的文档。</span><span class="sxs-lookup"><span data-stu-id="23888-119">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="23888-120">不过，将会准备一个更可靠的实现以分析无效文档。</span><span class="sxs-lookup"><span data-stu-id="23888-120">A more robust implementation, however, would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="23888-121">下面是源文档 Source.xml：</span><span class="sxs-lookup"><span data-stu-id="23888-121">The following is the source document, Source.xml:</span></span>  
  
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
  
```csharp  
static IEnumerable<XElement> StreamCustomerItem(string uri)  
{  
    using (XmlReader reader = XmlReader.Create(uri))  
    {  
        XElement name = null;  
        XElement item = null;  
  
        reader.MoveToContent();  
  
        // Parse the file, save header information when encountered, and yield the  
        // Item XElement objects as they are created.  
  
        // loop through Customer elements  
        while (reader.Read())  
        {  
            if (reader.NodeType == XmlNodeType.Element  
                && reader.Name == "Customer")  
            {  
                // move to Name element  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.Element &&  
                        reader.Name == "Name")  
                    {  
                        name = XElement.ReadFrom(reader) as XElement;  
                        break;  
                    }  
                }  
  
                // loop through Item elements  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.EndElement)  
                        break;  
                    if (reader.NodeType == XmlNodeType.Element  
                        && reader.Name == "Item")  
                    {  
                        item = XElement.ReadFrom(reader) as XElement;  
                        if (item != null)  
                        {  
                            XElement tempRoot = new XElement("Root",  
                                new XElement(name)  
                            );  
                            tempRoot.Add(item);  
                            yield return item;  
                        }  
                    }  
                }  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    XStreamingElement root = new XStreamingElement("Root",  
        from el in StreamCustomerItem("Source.xml")  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        )  
    );  
    root.Save("Test.xml");  
    Console.WriteLine(File.ReadAllText("Test.xml"));  
}  
```  
  
 <span data-ttu-id="23888-122">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="23888-122">This code produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0001</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0002</Key>  
  </Item>  
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
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0008</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0009</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0010</Key>  
  </Item>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="23888-123">示例</span><span class="sxs-lookup"><span data-stu-id="23888-123">Example</span></span>  
<span data-ttu-id="23888-124">以下示例同样在[如何流处理可访问标头信息的 XML 片段 (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) 中的示例基础上建立。</span><span class="sxs-lookup"><span data-stu-id="23888-124">The following example also builds on the example in [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>
  
 <span data-ttu-id="23888-125">本示例使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 的功能将元素写入 <xref:System.Xml.XmlWriter>。</span><span class="sxs-lookup"><span data-stu-id="23888-125">This example uses the capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="23888-126">本示例可在保持很小的内存需求量的同时转换非常大的文档。</span><span class="sxs-lookup"><span data-stu-id="23888-126">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="23888-127">请注意，自定义轴 (`StreamCustomerItem`) 经过专门编写，可以处理具有 `Customer`、`Name` 和 `Item` 元素，并且这些元素将按下面 Source.xml 文档排列的文档。</span><span class="sxs-lookup"><span data-stu-id="23888-127">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="23888-128">不过，更可靠的实现将会使用 XSD 验证源文档或将会准备一个更可靠的实现以分析无效文档。</span><span class="sxs-lookup"><span data-stu-id="23888-128">A more robust implementation, however, would either validate the source document with an XSD, or would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="23888-129">本示例与本主题中的前一示例使用同一个源文档 Source.xml。</span><span class="sxs-lookup"><span data-stu-id="23888-129">This example uses the same source document, Source.xml, as the previous example in this topic.</span></span> <span data-ttu-id="23888-130">它也生成完全相同的输出。</span><span class="sxs-lookup"><span data-stu-id="23888-130">It also produces exactly the same output.</span></span>  
  
 <span data-ttu-id="23888-131">使用 <xref:System.Xml.Linq.XStreamingElement> 对输出 XML 进行流式处理胜于写入到 <xref:System.Xml.XmlWriter>。</span><span class="sxs-lookup"><span data-stu-id="23888-131">Using <xref:System.Xml.Linq.XStreamingElement> for streaming the output XML is preferred over writing to an <xref:System.Xml.XmlWriter>.</span></span>  
  
```csharp  
static IEnumerable<XElement> StreamCustomerItem(string uri)  
{  
    using (XmlReader reader = XmlReader.Create(uri))  
    {  
        XElement name = null;  
        XElement item = null;  
  
        reader.MoveToContent();  
  
        // Parse the file, save header information when encountered, and yield the  
        // Item XElement objects as they are created.  
  
        // loop through Customer elements  
        while (reader.Read())  
        {  
            if (reader.NodeType == XmlNodeType.Element  
                && reader.Name == "Customer")  
            {  
                // move to Name element  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.Element &&  
                        reader.Name == "Name")  
                    {  
                        name = XElement.ReadFrom(reader) as XElement;  
                        break;  
                    }  
                }  
  
                // loop through Item elements  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.EndElement)  
                        break;  
                    if (reader.NodeType == XmlNodeType.Element  
                        && reader.Name == "Item")  
                    {  
                        item = XElement.ReadFrom(reader) as XElement;  
                        if (item != null) {  
                            XElement tempRoot = new XElement("Root",  
                                new XElement(name)  
                            );  
                            tempRoot.Add(item);  
                            yield return item;  
                        }  
                    }  
                }  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    IEnumerable<XElement> srcTree =  
        from el in StreamCustomerItem("Source.xml")  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        );  
    XmlWriterSettings xws = new XmlWriterSettings();  
    xws.OmitXmlDeclaration = true;  
    xws.Indent = true;  
    using (XmlWriter xw = XmlWriter.Create("Output.xml", xws)) {  
        xw.WriteStartElement("Root");  
        foreach (XElement el in srcTree)  
            el.WriteTo(xw);  
        xw.WriteEndElement();  
    }  
  
    string str = File.ReadAllText("Output.xml");  
    Console.WriteLine(str);  
}  
```  
  
 <span data-ttu-id="23888-132">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="23888-132">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0001</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0002</Key>  
  </Item>  
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
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0008</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0009</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0010</Key>  
  </Item>  
</Root>  
```  
  
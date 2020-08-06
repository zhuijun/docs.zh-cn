---
title: 如何通过对标头信息的访问流式处理 XML 片段 (C#)
description: 了解如何通过对标头信息的访问流式处理 XML 片段。 流式处理技术有助于避免过多的内存占用量。
ms.date: 07/20/2015
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: 8bfded96ea1fa6b096d56ae0736002b9062d58b6
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303213"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-c"></a><span data-ttu-id="2314b-104">如何通过对标头信息的访问流式处理 XML 片段 (C#)</span><span class="sxs-lookup"><span data-stu-id="2314b-104">How to stream XML fragments with access to header information (C#)</span></span>
<span data-ttu-id="2314b-105">有时，您必须读取任意大的 XML 文件并在编写您的应用程序时可以预测应用程序的内存需求量。</span><span class="sxs-lookup"><span data-stu-id="2314b-105">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="2314b-106">如果您试图用大 XML 文件填充 XML 树，则内存占用量将与文件大小成正比，也就是说会占用过多内存。</span><span class="sxs-lookup"><span data-stu-id="2314b-106">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="2314b-107">因此，您应改用流处理技术。</span><span class="sxs-lookup"><span data-stu-id="2314b-107">Therefore, you should use a streaming technique instead.</span></span>  
  
<span data-ttu-id="2314b-108">一种选择是使用 <xref:System.Xml.XmlReader> 来编写应用程序。</span><span class="sxs-lookup"><span data-stu-id="2314b-108">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="2314b-109">但你可能需要使用 LINQ 来查询 XML 树。</span><span class="sxs-lookup"><span data-stu-id="2314b-109">However, you might want to use LINQ to query the XML tree.</span></span> <span data-ttu-id="2314b-110">在这种情况下，您可以编写自己的自定义轴方法。</span><span class="sxs-lookup"><span data-stu-id="2314b-110">If this is the case, you can write your own custom axis method.</span></span> <span data-ttu-id="2314b-111">有关详细信息，请参阅[如何编写 LINQ to XML 轴方法 (C#)](./how-to-write-a-linq-to-xml-axis-method.md)。</span><span class="sxs-lookup"><span data-stu-id="2314b-111">For more information, see [How to write a LINQ to XML axis method (C#)](./how-to-write-a-linq-to-xml-axis-method.md).</span></span>
  
 <span data-ttu-id="2314b-112">若要编写您自己的轴方法，请编写一个小方法，让该方法使用 <xref:System.Xml.XmlReader> 来读取各个节点，直到达到您感兴趣的节点之一。</span><span class="sxs-lookup"><span data-stu-id="2314b-112">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you are interested.</span></span> <span data-ttu-id="2314b-113">该方法然后调用 <xref:System.Xml.Linq.XNode.ReadFrom%2A>，后者将从 <xref:System.Xml.XmlReader> 中读取数据并实例化 XML 片段。</span><span class="sxs-lookup"><span data-stu-id="2314b-113">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="2314b-114">然后，该方法生成从 `yield return` 到该方法（枚举您的自定义轴方法的方法）的每个片段。</span><span class="sxs-lookup"><span data-stu-id="2314b-114">It then yields each fragment through `yield return` to the method that is enumerating your custom axis method.</span></span> <span data-ttu-id="2314b-115">然后，您可以对自定义轴方法编写 LINQ 查询。</span><span class="sxs-lookup"><span data-stu-id="2314b-115">You can then write LINQ queries on your custom axis method.</span></span>  
  
 <span data-ttu-id="2314b-116">流处理技术最适合只需处理一次源文档的情况，您可以按文档顺序处理各个元素。</span><span class="sxs-lookup"><span data-stu-id="2314b-116">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="2314b-117">某些标准查询运算符（如 <xref:System.Linq.Enumerable.OrderBy%2A>）可以循环访问其源、收集所有数据、对数据排序，最后生成序列中的第一项。</span><span class="sxs-lookup"><span data-stu-id="2314b-117">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="2314b-118">如果使用可在生成第一项之前具体化源的查询运算符，则不会保持小的内存需求量。</span><span class="sxs-lookup"><span data-stu-id="2314b-118">If you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2314b-119">示例</span><span class="sxs-lookup"><span data-stu-id="2314b-119">Example</span></span>  

<span data-ttu-id="2314b-120">有时，问题会变得更有意思。</span><span class="sxs-lookup"><span data-stu-id="2314b-120">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="2314b-121">在下面的 XML 文档中，自定义轴方法的使用方也必须知道每一项所属的使用方名称。</span><span class="sxs-lookup"><span data-stu-id="2314b-121">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>  
  
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
  
 <span data-ttu-id="2314b-122">本示例采用的方法还将监视此标头信息、保存标头信息，然后生成包含标头信息和所要枚举的详细信息的小型 XML 树。</span><span class="sxs-lookup"><span data-stu-id="2314b-122">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you are enumerating.</span></span> <span data-ttu-id="2314b-123">该轴方法然后生成这个新的小型 XML 树。</span><span class="sxs-lookup"><span data-stu-id="2314b-123">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="2314b-124">之后，查询将可以访问标头信息以及详细信息。</span><span class="sxs-lookup"><span data-stu-id="2314b-124">The query then has access to the header information as well as the detail information.</span></span>  
  
 <span data-ttu-id="2314b-125">此方法具有小的内存需求量。</span><span class="sxs-lookup"><span data-stu-id="2314b-125">This approach has a small memory footprint.</span></span> <span data-ttu-id="2314b-126">由于生成了所有的详细 XML 片段，不再需要保留对前一个片段的引用，因此，此方法可用于垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="2314b-126">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it is available for garbage collection.</span></span> <span data-ttu-id="2314b-127">此技术会在堆上创建许多短生存期的对象。</span><span class="sxs-lookup"><span data-stu-id="2314b-127">This technique creates many short lived objects on the heap.</span></span>  
  
 <span data-ttu-id="2314b-128">下面的示例演示如何实现和使用可流处理由 URI 指定的文件中的 XML 片段的自定义轴方法。</span><span class="sxs-lookup"><span data-stu-id="2314b-128">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="2314b-129">此自定义轴经过编写，可以处理具有 `Customer`、`Name` 和 `Item` 元素，并且这些元素按上述 `Source.xml` 文档排列的文档。</span><span class="sxs-lookup"><span data-stu-id="2314b-129">This custom axis is written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="2314b-130">这是一个过于简单的实现。</span><span class="sxs-lookup"><span data-stu-id="2314b-130">It is a simplistic implementation.</span></span> <span data-ttu-id="2314b-131">将会准备一个更可靠的实现以分析无效文档。</span><span class="sxs-lookup"><span data-stu-id="2314b-131">A more robust implementation would be prepared to parse an invalid document.</span></span>  
  
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
    XElement xmlTree = new XElement("Root",  
        from el in StreamCustomerItem("Source.xml")  
        where (int)el.Element("Key") >= 3 && (int)el.Element("Key") <= 7  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        )  
    );  
    Console.WriteLine(xmlTree);  
}  
```  
  
 <span data-ttu-id="2314b-132">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="2314b-132">This code produces the following output:</span></span>  
  
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

---
title: "高级 LINQ to XML 编程 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 2e012d40-532b-49ea-b1fc-152e616bdfa3
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4419d05874f8e4883711d0f4abb98bc4a416b7fd
ms.contentlocale: zh-cn
ms.lasthandoff: 07/28/2017

---
# <a name="advanced-linq-to-xml-programming-c"></a><span data-ttu-id="2f0ad-102">高级 LINQ to XML 编程 (C#)</span><span class="sxs-lookup"><span data-stu-id="2f0ad-102">Advanced LINQ to XML Programming (C#)</span></span>
<span data-ttu-id="2f0ad-103">本节为高级开发人员提供一些只适用于某些 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 方案的信息。</span><span class="sxs-lookup"><span data-stu-id="2f0ad-103">This section provides information that will only be applicable to advanced developers in certain [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2f0ad-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="2f0ad-104">In This Section</span></span>  
  
|<span data-ttu-id="2f0ad-105">主题</span><span class="sxs-lookup"><span data-stu-id="2f0ad-105">Topic</span></span>|<span data-ttu-id="2f0ad-106">描述</span><span class="sxs-lookup"><span data-stu-id="2f0ad-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="2f0ad-107">LINQ to XML 批注</span><span class="sxs-lookup"><span data-stu-id="2f0ad-107">LINQ to XML Annotations</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-annotations.md)|<span data-ttu-id="2f0ad-108">介绍如何将批注添加到 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 节点和属性。</span><span class="sxs-lookup"><span data-stu-id="2f0ad-108">Describes how to add annotations to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nodes and attributes.</span></span>|  
|[<span data-ttu-id="2f0ad-109">LINQ to XML 事件 (C#)</span><span class="sxs-lookup"><span data-stu-id="2f0ad-109">LINQ to XML Events (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-events.md)|<span data-ttu-id="2f0ad-110">介绍如何为更改 XML 树时所发生的事件编写事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="2f0ad-110">Describes how to write event handlers for events that occur when you alter an XML tree.</span></span>|  
|[<span data-ttu-id="2f0ad-111">使用节点进行编程 (C#)</span><span class="sxs-lookup"><span data-stu-id="2f0ad-111">Programming with Nodes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-with-nodes.md)|<span data-ttu-id="2f0ad-112">介绍如何在比元素和属性更精细的粒度级别上查询和操作节点。</span><span class="sxs-lookup"><span data-stu-id="2f0ad-112">Describes how to query and manipulate nodes at a finer level of granularity than elements and attributes.</span></span>|  
|[<span data-ttu-id="2f0ad-113">混合声明性代码/命令性代码的问题 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2f0ad-113">Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md)|<span data-ttu-id="2f0ad-114">介绍在混合声明性代码（查询）与命令性代码（修改 XML 树的代码）时所出现的问题。</span><span class="sxs-lookup"><span data-stu-id="2f0ad-114">Describes the problems that appear when you mix declarative code (queries) with imperative code (code that modifies the XML tree).</span></span>|  
|[<span data-ttu-id="2f0ad-115">如何：通过对标头信息的访问流式处理 XML 片段 (C#)</span><span class="sxs-lookup"><span data-stu-id="2f0ad-115">How to: Stream XML Fragments with Access to Header Information (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md)|<span data-ttu-id="2f0ad-116">介绍如何在 <xref:System.Xml.XmlReader> 中对 XML 片段进行流式处理。</span><span class="sxs-lookup"><span data-stu-id="2f0ad-116">Describes how to stream XML fragments from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="2f0ad-117">使用此技术，可以控制应用程序的内存需求量。</span><span class="sxs-lookup"><span data-stu-id="2f0ad-117">You can use this technique to control the memory footprint of your application.</span></span>|  
|[<span data-ttu-id="2f0ad-118">如何：执行大型 XML 文档的流式转换 (C#)</span><span class="sxs-lookup"><span data-stu-id="2f0ad-118">How to: Perform Streaming Transform of Large XML Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md)|<span data-ttu-id="2f0ad-119">介绍如何在 <xref:System.Xml.XmlReader> 中对 XML 进行流式处理，如何转换 XML 片段，如何使用 <xref:System.Xml.Linq.XStreamingElement> 对输出进行流式处理。</span><span class="sxs-lookup"><span data-stu-id="2f0ad-119">Describes how to stream XML from an <xref:System.Xml.XmlReader>, transform the XML fragment, and stream the output using <xref:System.Xml.Linq.XStreamingElement>.</span></span>|  
|[<span data-ttu-id="2f0ad-120">如何：读取和写入编码的文档 (C#)</span><span class="sxs-lookup"><span data-stu-id="2f0ad-120">How to: Read and Write an Encoded Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-read-and-write-an-encoded-document.md)|<span data-ttu-id="2f0ad-121">介绍如何读取和写入经过编码的 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="2f0ad-121">Describes how to read and write XML documents that are encoded.</span></span>|  
|[<span data-ttu-id="2f0ad-122">使用 XSLT 转换 XML 树 (C#)</span><span class="sxs-lookup"><span data-stu-id="2f0ad-122">Using XSLT to Transform an XML Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/using-xslt-to-transform-an-xml-tree.md)|<span data-ttu-id="2f0ad-123">介绍如何使用 XSLT 转换 XML 树。</span><span class="sxs-lookup"><span data-stu-id="2f0ad-123">Describes how to transform an XML tree using XSLT.</span></span>|  
|[<span data-ttu-id="2f0ad-124">如何：使用批注以 XSLT 样式转换 LINQ to XML 树 (C#)</span><span class="sxs-lookup"><span data-stu-id="2f0ad-124">How to: Use Annotations to Transform LINQ to XML Trees in an XSLT Style (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style.md)|<span data-ttu-id="2f0ad-125">介绍如何使用批注来帮助进行 XML 树的转换。</span><span class="sxs-lookup"><span data-stu-id="2f0ad-125">Describes how annotations can be used to facilitate transforms of an XML tree.</span></span>|  
|[<span data-ttu-id="2f0ad-126">序列化包含 XElement 对象的对象图 (C#)</span><span class="sxs-lookup"><span data-stu-id="2f0ad-126">Serializing Object Graphs that Contain XElement Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-object-graphs-that-contain-xelement-objects.md)|<span data-ttu-id="2f0ad-127">介绍如何序列化包含 <xref:System.Xml.Linq.XElement> 和 <xref:System.Xml.Linq.XDocument> 对象的对象图。</span><span class="sxs-lookup"><span data-stu-id="2f0ad-127">Describes how to serialize object graphs that contain <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> objects.</span></span>|  
|[<span data-ttu-id="2f0ad-128">使用 LINQ to XML 进行 WPF 数据绑定</span><span class="sxs-lookup"><span data-stu-id="2f0ad-128">WPF Data Binding with LINQ to XML</span></span>](/visualstudio/designers/wpf-data-binding-with-linq-to-xml)|<span data-ttu-id="2f0ad-129">介绍如何将 LINQ to XML 用作 Windows Presentation Foundation 应用程序中数据绑定的数据源。</span><span class="sxs-lookup"><span data-stu-id="2f0ad-129">Describes how to use LINQ to XML as the data source for data binding in Windows Presentation Foundation applications.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2f0ad-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="2f0ad-130">See Also</span></span>  
 [<span data-ttu-id="2f0ad-131">编程指南 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2f0ad-131">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)

---
title: XML 文档和数据
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: e695047f-3c0f-4045-8708-5baea91cc380
ms.openlocfilehash: 6d2a52567a1fc8bdbbb1d039ac583c889d77d4af
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540129"
---
# <a name="xml-documents-and-data"></a><span data-ttu-id="86e4d-102">XML 文档和数据</span><span class="sxs-lookup"><span data-stu-id="86e4d-102">XML Documents and Data</span></span>

<span data-ttu-id="86e4d-103">.NET Framework 提供了一组全面而集成的类，可用来方便地生成可以识别 XML 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="86e4d-103">The .NET Framework provides a comprehensive and integrated set of classes that enable you to build XML-aware apps easily.</span></span> <span data-ttu-id="86e4d-104">通过以下命名空间中的类，可以分析和编写 XML，编辑内存中的 XML 数据，进行数据验证以及 XSLT 转换。</span><span class="sxs-lookup"><span data-stu-id="86e4d-104">The classes in the following namespaces support parsing and writing XML, editing XML data in memory, data validation, and XSLT transformation.</span></span>

- <xref:System.Xml>

- <xref:System.Xml.XPath>

- <xref:System.Xml.Xsl>

- <xref:System.Xml.Schema>

- <xref:System.Xml.Linq>

<span data-ttu-id="86e4d-105">若要查看完整的列表，请在 [.NET API 浏览器](../../../../api/index.md?term=system.xml)上搜索“System.Xml”。</span><span class="sxs-lookup"><span data-stu-id="86e4d-105">For a full list, search for "System.Xml" on the [.NET API browser](../../../../api/index.md?term=system.xml).</span></span>

<span data-ttu-id="86e4d-106">这些命名空间中的类支持万维网联合会 (W3C) 建议。</span><span class="sxs-lookup"><span data-stu-id="86e4d-106">The classes in these namespaces support World Wide Web Consortium (W3C) recommendations.</span></span> <span data-ttu-id="86e4d-107">例如：</span><span class="sxs-lookup"><span data-stu-id="86e4d-107">For example:</span></span>

- <span data-ttu-id="86e4d-108"><xref:System.Xml.XmlDocument?displayProperty=nameWithType> 类可实现 [W3C 文档对象模型 (DOM) 级别 1 核心](https://www.w3.org/TR/REC-DOM-Level-1/)和 [DOM 级别 2 核心](https://www.w3.org/TR/DOM-Level-2-Core/)建议。</span><span class="sxs-lookup"><span data-stu-id="86e4d-108">The <xref:System.Xml.XmlDocument?displayProperty=nameWithType> class implements the [W3C Document Object Model (DOM) Level 1 Core](https://www.w3.org/TR/REC-DOM-Level-1/) and [DOM Level 2 Core](https://www.w3.org/TR/DOM-Level-2-Core/) recommendations.</span></span>

- <span data-ttu-id="86e4d-109"><xref:System.Xml.XmlReader?displayProperty=nameWithType> 和 <xref:System.Xml.XmlWriter?displayProperty=nameWithType> 类支持 [W3C XML 1.0](https://www.w3.org/TR/2006/REC-xml-20060816/) 和 [XML 中的命名空间](https://www.w3.org/TR/REC-xml-names/)建议。</span><span class="sxs-lookup"><span data-stu-id="86e4d-109">The <xref:System.Xml.XmlReader?displayProperty=nameWithType> and <xref:System.Xml.XmlWriter?displayProperty=nameWithType> classes support the [W3C XML 1.0](https://www.w3.org/TR/2006/REC-xml-20060816/) and the [Namespaces in XML](https://www.w3.org/TR/REC-xml-names/) recommendations.</span></span>

- <span data-ttu-id="86e4d-110"><xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> 类中的架构支持 [W3C XML 架构第 1 部分：结构](https://www.w3.org/TR/xmlschema-1/)和 [XML 架构第 2 部分：数据类型](https://www.w3.org/TR/xmlschema-2/)建议。</span><span class="sxs-lookup"><span data-stu-id="86e4d-110">Schemas in the <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> class support the [W3C XML Schema Part 1: Structures](https://www.w3.org/TR/xmlschema-1/) and [XML Schema Part 2: Datatypes](https://www.w3.org/TR/xmlschema-2/) recommendations.</span></span>

- <span data-ttu-id="86e4d-111"><xref:System.Xml.Xsl?displayProperty=nameWithType> 命名空间中的类支持符合 [W3C XSLT 1.0](https://www.w3.org/TR/xslt) 建议的 XSLT 转换。</span><span class="sxs-lookup"><span data-stu-id="86e4d-111">Classes in the <xref:System.Xml.Xsl?displayProperty=nameWithType> namespace support XSLT transformations that conform to the [W3C XSLT 1.0](https://www.w3.org/TR/xslt) recommendation.</span></span>

<span data-ttu-id="86e4d-112">.NET Framework 中的 XML 类具有以下优点：</span><span class="sxs-lookup"><span data-stu-id="86e4d-112">The XML classes in the .NET Framework provide these benefits:</span></span>

- <span data-ttu-id="86e4d-113">**高效率。**</span><span class="sxs-lookup"><span data-stu-id="86e4d-113">**Productivity.**</span></span> <span data-ttu-id="86e4d-114">通过 [LINQ to XML (C#)](../../linq/linq-xml-overview.md) 和 [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md)，能够更轻松地使用 XML 编程，并且能够得到与 SQL 类似的查询体验。</span><span class="sxs-lookup"><span data-stu-id="86e4d-114">[LINQ to XML (C#)](../../linq/linq-xml-overview.md) and [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md) makes it easier to program with XML and provides a query experience that is similar to SQL.</span></span>

- <span data-ttu-id="86e4d-115">**扩展性。**</span><span class="sxs-lookup"><span data-stu-id="86e4d-115">**Extensibility.**</span></span> <span data-ttu-id="86e4d-116">.NET Framework 中的 XML 类可使用抽象基类和虚拟方法进行扩展。</span><span class="sxs-lookup"><span data-stu-id="86e4d-116">The XML classes in the .NET Framework are extensible through the use of abstract base classes and virtual methods.</span></span> <span data-ttu-id="86e4d-117">例如，您可以创建 <xref:System.Xml.XmlUrlResolver> 类的一个派生类，用以将缓存流存储到本地磁盘。</span><span class="sxs-lookup"><span data-stu-id="86e4d-117">For example, you can create a derived class of the <xref:System.Xml.XmlUrlResolver> class that stores the cache stream to the local disk.</span></span>

- <span data-ttu-id="86e4d-118">**可插入的体系结构。**</span><span class="sxs-lookup"><span data-stu-id="86e4d-118">**Pluggable architecture.**</span></span> <span data-ttu-id="86e4d-119">.NET Framework 提供了一种体系结构，其中的组件可以相互利用，数据可以在各组件之间传送。</span><span class="sxs-lookup"><span data-stu-id="86e4d-119">The .NET Framework provides an architecture in which components can utilize one another, and data can be streamed between components.</span></span> <span data-ttu-id="86e4d-120">例如，可以使用 <xref:System.Xml.XPath.XPathDocument> 类来转换数据存储（例如，<xref:System.Xml.XmlDocument> 或 <xref:System.Xml.Xsl.XslCompiledTransform> 对象），然后可将输出传送到另一个存储或作为 Web 服务的流返回。</span><span class="sxs-lookup"><span data-stu-id="86e4d-120">For example, a data store, such as an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object, can be transformed with the <xref:System.Xml.Xsl.XslCompiledTransform> class, and the output can then be streamed either into another store or returned as a stream from a web service.</span></span>

- <span data-ttu-id="86e4d-121">**性能。**</span><span class="sxs-lookup"><span data-stu-id="86e4d-121">**Performance.**</span></span> <span data-ttu-id="86e4d-122">为获得更佳应用程序性能，.NET Framework 中设计的某些 XML 类支持基于流的模型并具有以下特性：</span><span class="sxs-lookup"><span data-stu-id="86e4d-122">For better app performance, some of the XML classes in the .NET Framework support a streaming-based model with the following characteristics:</span></span>

  - <span data-ttu-id="86e4d-123">只进、拉出模型分析使用最小缓存 (<xref:System.Xml.XmlReader>)。</span><span class="sxs-lookup"><span data-stu-id="86e4d-123">Minimal caching for forward-only, pull-model parsing (<xref:System.Xml.XmlReader>).</span></span>

  - <span data-ttu-id="86e4d-124">只进验证 (<xref:System.Xml.XmlReader>)。</span><span class="sxs-lookup"><span data-stu-id="86e4d-124">Forward-only validation (<xref:System.Xml.XmlReader>).</span></span>

  - <span data-ttu-id="86e4d-125">游标式导航，可使创建的节点减少到单个虚拟节点，同时提供对文档的随机访问 (<xref:System.Xml.XPath.XPathNavigator>)。</span><span class="sxs-lookup"><span data-stu-id="86e4d-125">Cursor style navigation that minimizes node creation to a single virtual node while providing random access to the document (<xref:System.Xml.XPath.XPathNavigator>).</span></span>

  <span data-ttu-id="86e4d-126">为了在需要进行 XSLT 处理时都获得更佳性能，您可以使用 <xref:System.Xml.XPath.XPathDocument> 类，这是一个用于 XPath 查询的经过优化的只读存储，旨在高效地与 <xref:System.Xml.Xsl.XslCompiledTransform> 类结合使用。</span><span class="sxs-lookup"><span data-stu-id="86e4d-126">For better performance whenever XSLT processing is required, you can use the <xref:System.Xml.XPath.XPathDocument> class, which is an optimized, read-only store for XPath queries designed to work efficiently with the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>

- <span data-ttu-id="86e4d-127">**与 ADO.NET 集成。**</span><span class="sxs-lookup"><span data-stu-id="86e4d-127">**Integration with ADO.NET.**</span></span> <span data-ttu-id="86e4d-128">XML 类和 [ADO.NET](../../../framework/data/adonet/index.md) 紧密集成，将关系数据和 XML 组合在一起。</span><span class="sxs-lookup"><span data-stu-id="86e4d-128">The XML classes and [ADO.NET](../../../framework/data/adonet/index.md) are tightly integrated to bring together relational data and XML.</span></span> <span data-ttu-id="86e4d-129"><xref:System.Data.DataSet> 类是从数据库中检索到的数据在内存中的缓存。</span><span class="sxs-lookup"><span data-stu-id="86e4d-129">The <xref:System.Data.DataSet> class is an in-memory cache of data retrieved from a database.</span></span> <span data-ttu-id="86e4d-130"><xref:System.Data.DataSet> 类能够使用 <xref:System.Xml.XmlReader> 和 <xref:System.Xml.XmlWriter> 类读取和写入 XML，以 XML 架构 (XSD) 形式保持其内部关系架构结构，并可以推断 XML 文档的架构结构。</span><span class="sxs-lookup"><span data-stu-id="86e4d-130">The <xref:System.Data.DataSet> class has the ability to read and write XML by using the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> classes, to persist its internal relational schema structure as XML schemas (XSD), and to infer the schema structure of an XML document.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="86e4d-131">本节内容</span><span class="sxs-lookup"><span data-stu-id="86e4d-131">In This Section</span></span>

<span data-ttu-id="86e4d-132">[XML 处理选项](xml-processing-options.md) 讨论用于处理 XML 数据的选项。</span><span class="sxs-lookup"><span data-stu-id="86e4d-132">[XML Processing Options](xml-processing-options.md) Discusses options for processing XML data.</span></span>

<span data-ttu-id="86e4d-133">[处理内存中 XML 数据](processing-xml-data-in-memory.md) 讨论用于处理内存中 XML 数据的三种模型：[LINQ to XML (C#)](../../linq/linq-xml-overview.md) 和 [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md)、<xref:System.Xml.XmlDocument> 类（基于 W3C 文档对象模型）以及 <xref:System.Xml.XPath.XPathDocument> 类（基于 XPath 数据模型）。</span><span class="sxs-lookup"><span data-stu-id="86e4d-133">[Processing XML Data In-Memory](processing-xml-data-in-memory.md) Discusses the three models for processing XML data in-memory: [LINQ to XML (C#)](../../linq/linq-xml-overview.md) and [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md), the <xref:System.Xml.XmlDocument> class (based on the W3C Document Object Model), and the <xref:System.Xml.XPath.XPathDocument> class (based on the XPath data model).</span></span>

<span data-ttu-id="86e4d-134">[XSLT 转换](xslt-transformations.md)</span><span class="sxs-lookup"><span data-stu-id="86e4d-134">[XSLT Transformations](xslt-transformations.md)</span></span>\
<span data-ttu-id="86e4d-135">描述如何使用 XSLT 处理器。</span><span class="sxs-lookup"><span data-stu-id="86e4d-135">Describes how to use the XSLT processor.</span></span>

<span data-ttu-id="86e4d-136">[XML 架构对象模型 (SOM)](xml-schema-object-model-som.md)</span><span class="sxs-lookup"><span data-stu-id="86e4d-136">[XML Schema Object Model (SOM)](xml-schema-object-model-som.md)</span></span>\
<span data-ttu-id="86e4d-137">描述用于通过提供 <xref:System.Xml.Schema.XmlSchema> 类加载和编辑架构来生成和处理 XML 架构 (XSD) 的类。</span><span class="sxs-lookup"><span data-stu-id="86e4d-137">Describes the classes used for building and manipulating XML Schemas (XSD) by providing an <xref:System.Xml.Schema.XmlSchema> class to load and edit a schema.</span></span>

<span data-ttu-id="86e4d-138">[关系数据和 ADO.NET 的 XML 集成](xml-integration-with-relational-data-and-adonet.md)</span><span class="sxs-lookup"><span data-stu-id="86e4d-138">[XML Integration with Relational Data and ADO.NET](xml-integration-with-relational-data-and-adonet.md)</span></span>\
<span data-ttu-id="86e4d-139">描述 .NET Framework 如何通过 <xref:System.Data.DataSet> 对象和 <xref:System.Xml.XmlDataDocument> 对象启用对数据的关系和分层表示形式的实时同步访问。</span><span class="sxs-lookup"><span data-stu-id="86e4d-139">Describes how the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the <xref:System.Data.DataSet> object and the <xref:System.Xml.XmlDataDocument> object.</span></span>

<span data-ttu-id="86e4d-140">[管理 XML 文档中的命名空间](managing-namespaces-in-an-xml-document.md)</span><span class="sxs-lookup"><span data-stu-id="86e4d-140">[Managing Namespaces in an XML Document](managing-namespaces-in-an-xml-document.md)</span></span>\
<span data-ttu-id="86e4d-141">描述 <xref:System.Xml.XmlNamespaceManager> 类如何用于存储和维护命名空间信息。</span><span class="sxs-lookup"><span data-stu-id="86e4d-141">Describes how the <xref:System.Xml.XmlNamespaceManager> class is used to store and maintain namespace information.</span></span>

<span data-ttu-id="86e4d-142">[System.Xml 类中的类型支持](type-support-in-the-system-xml-classes.md)</span><span class="sxs-lookup"><span data-stu-id="86e4d-142">[Type Support in the System.Xml Classes](type-support-in-the-system-xml-classes.md)</span></span>\
<span data-ttu-id="86e4d-143">描述如何将 XML 数据类型映射到 CLR 类型，如何转换 XML 类型，并描述 <xref:System.Xml> 类中的其它类型支持功能。</span><span class="sxs-lookup"><span data-stu-id="86e4d-143">Describes how XML data types map to CLR types, how to convert XML data types, and other type support features in the <xref:System.Xml> classes.</span></span>

## <a name="related-sections"></a><span data-ttu-id="86e4d-144">相关章节</span><span class="sxs-lookup"><span data-stu-id="86e4d-144">Related Sections</span></span>

<span data-ttu-id="86e4d-145">[ADO.NET](../../../framework/data/adonet/index.md)</span><span class="sxs-lookup"><span data-stu-id="86e4d-145">[ADO.NET](../../../framework/data/adonet/index.md)</span></span>\
<span data-ttu-id="86e4d-146">提供如何使用 ADO.NET 访问数据的信息。</span><span class="sxs-lookup"><span data-stu-id="86e4d-146">Provides information on how to access data using ADO.NET.</span></span>

<span data-ttu-id="86e4d-147">[安全性](../../security/index.md)</span><span class="sxs-lookup"><span data-stu-id="86e4d-147">[Security](../../security/index.md)</span></span>\
<span data-ttu-id="86e4d-148">提供对 .NET Framework 安全系统的概述。</span><span class="sxs-lookup"><span data-stu-id="86e4d-148">Provides an overview of the .NET Framework security system.</span></span>

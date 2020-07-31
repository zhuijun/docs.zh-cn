---
title: LINQ to XML 类概述 (C#)
description: 本文总结了 System.Xml.Linq 命名空间的 C# 中的 LINQ to XML 类，并对每个类进行了简短说明。
ms.date: 07/20/2015
ms.assetid: bf666100-5392-4968-97f4-f6b9d3287d7b
ms.openlocfilehash: 34508f86792cdc7589569b8f12584ffc4379a5fb
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165428"
---
# <a name="linq-to-xml-classes-overview-c"></a><span data-ttu-id="73786-103">LINQ to XML 类概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="73786-103">LINQ to XML Classes Overview (C#)</span></span>
<span data-ttu-id="73786-104">本主题提供 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 命名空间中 <xref:System.Xml.Linq> 类的列表及每个类的简短说明。</span><span class="sxs-lookup"><span data-stu-id="73786-104">This topic provides a list of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] classes in the <xref:System.Xml.Linq> namespace, and a short description of each.</span></span>  
  
## <a name="linq-to-xml-classes"></a><span data-ttu-id="73786-105">LINQ to XML 类</span><span class="sxs-lookup"><span data-stu-id="73786-105">LINQ to XML Classes</span></span>  
  
### <a name="xattribute-class"></a><span data-ttu-id="73786-106">XAttribute 类</span><span class="sxs-lookup"><span data-stu-id="73786-106">XAttribute Class</span></span>  
 <span data-ttu-id="73786-107"><xref:System.Xml.Linq.XAttribute> 表示一个 XML 属性。</span><span class="sxs-lookup"><span data-stu-id="73786-107"><xref:System.Xml.Linq.XAttribute> represents an XML attribute.</span></span> <span data-ttu-id="73786-108">有关详细信息和示例，请参阅 [XAttribute 类概述 (C#)](./xattribute-class-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="73786-108">For detailed information and examples, see [XAttribute Class Overview (C#)](./xattribute-class-overview.md).</span></span>  
  
### <a name="xcdata-class"></a><span data-ttu-id="73786-109">XCData 类</span><span class="sxs-lookup"><span data-stu-id="73786-109">XCData Class</span></span>  
 <span data-ttu-id="73786-110"><xref:System.Xml.Linq.XCData> 表示一个 CDATA 文本节点。</span><span class="sxs-lookup"><span data-stu-id="73786-110"><xref:System.Xml.Linq.XCData> represents a CDATA text node.</span></span>  
  
### <a name="xcomment-class"></a><span data-ttu-id="73786-111">XComment 类</span><span class="sxs-lookup"><span data-stu-id="73786-111">XComment Class</span></span>  
 <span data-ttu-id="73786-112"><xref:System.Xml.Linq.XComment> 表示一个 XML 注释。</span><span class="sxs-lookup"><span data-stu-id="73786-112"><xref:System.Xml.Linq.XComment> represents an XML comment.</span></span>  
  
### <a name="xcontainer-class"></a><span data-ttu-id="73786-113">XContainer 类</span><span class="sxs-lookup"><span data-stu-id="73786-113">XContainer Class</span></span>  
 <span data-ttu-id="73786-114"><xref:System.Xml.Linq.XContainer> 是适用于可能具有子节点的所有节点的抽象基类。</span><span class="sxs-lookup"><span data-stu-id="73786-114"><xref:System.Xml.Linq.XContainer> is an abstract base class for all nodes that can have child nodes.</span></span> <span data-ttu-id="73786-115">下面的类派生自 <xref:System.Xml.Linq.XContainer> 类：</span><span class="sxs-lookup"><span data-stu-id="73786-115">The following classes derive from the <xref:System.Xml.Linq.XContainer> class:</span></span>  
  
- <xref:System.Xml.Linq.XElement>  
  
- <xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a><span data-ttu-id="73786-116">XDeclaration 类</span><span class="sxs-lookup"><span data-stu-id="73786-116">XDeclaration Class</span></span>  
 <span data-ttu-id="73786-117"><xref:System.Xml.Linq.XDeclaration> 表示一个 XML 声明。</span><span class="sxs-lookup"><span data-stu-id="73786-117"><xref:System.Xml.Linq.XDeclaration> represents an XML declaration.</span></span> <span data-ttu-id="73786-118">XML 声明用于声明 XML 版本和文档的编码。</span><span class="sxs-lookup"><span data-stu-id="73786-118">An XML declaration is used to declare the XML version and the encoding of a document.</span></span> <span data-ttu-id="73786-119">此外，XML 声明还指定 XML 文档是否为独立文档。</span><span class="sxs-lookup"><span data-stu-id="73786-119">In addition, an XML declaration specifies whether the XML document is stand-alone.</span></span> <span data-ttu-id="73786-120">如果文档是独立文档，则在外部 DTD 或从内部子集引用的外部参数实体中不存在外部标记声明。</span><span class="sxs-lookup"><span data-stu-id="73786-120">If a document is stand-alone, there are no external markup declarations, either in an external DTD, or in an external parameter entity referenced from the internal subset.</span></span>  
  
### <a name="xdocument-class"></a><span data-ttu-id="73786-121">XDocument 类</span><span class="sxs-lookup"><span data-stu-id="73786-121">XDocument Class</span></span>  
 <span data-ttu-id="73786-122"><xref:System.Xml.Linq.XDocument> 表示一个 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="73786-122"><xref:System.Xml.Linq.XDocument> represents an XML document.</span></span> <span data-ttu-id="73786-123">有关详细信息和示例，请参阅 [XDocument 类概述 (C#)](./xdocument-class-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="73786-123">For detailed information and examples, see [XDocument Class Overview (C#)](./xdocument-class-overview.md).</span></span>  
  
### <a name="xdocumenttype-class"></a><span data-ttu-id="73786-124">XDocumentType 类</span><span class="sxs-lookup"><span data-stu-id="73786-124">XDocumentType Class</span></span>  
 <span data-ttu-id="73786-125"><xref:System.Xml.Linq.XDocumentType> 表示一个 XML 文档类型定义 (DTD)。</span><span class="sxs-lookup"><span data-stu-id="73786-125"><xref:System.Xml.Linq.XDocumentType> represents an XML Document Type Definition (DTD).</span></span>  
  
### <a name="xelement-class"></a><span data-ttu-id="73786-126">XElement 类</span><span class="sxs-lookup"><span data-stu-id="73786-126">XElement Class</span></span>  
 <span data-ttu-id="73786-127"><xref:System.Xml.Linq.XElement> 表示一个 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="73786-127"><xref:System.Xml.Linq.XElement> represents an XML element.</span></span> <span data-ttu-id="73786-128">有关详细信息和示例，请参阅 [XElement 类概述 (C#)](./xelement-class-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="73786-128">For detailed information and examples, see [XElement Class Overview (C#)](./xelement-class-overview.md).</span></span>  
  
### <a name="xname-class"></a><span data-ttu-id="73786-129">XName 类</span><span class="sxs-lookup"><span data-stu-id="73786-129">XName Class</span></span>  
 <span data-ttu-id="73786-130"><xref:System.Xml.Linq.XName> 表示元素 (<xref:System.Xml.Linq.XElement>) 和属性 (<xref:System.Xml.Linq.XAttribute>) 的名称。</span><span class="sxs-lookup"><span data-stu-id="73786-130"><xref:System.Xml.Linq.XName> represents names of elements (<xref:System.Xml.Linq.XElement>) and attributes (<xref:System.Xml.Linq.XAttribute>).</span></span> <span data-ttu-id="73786-131">有关详细信息和示例，请参阅 [XDocument 类概述 (C#)](./xdocument-class-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="73786-131">For detailed information and examples, see [XDocument Class Overview (C#)](./xdocument-class-overview.md).</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="73786-132">旨在使 XML 名称尽可能简单。</span><span class="sxs-lookup"><span data-stu-id="73786-132">is designed to make XML names as straightforward as possible.</span></span> <span data-ttu-id="73786-133">XML 名称由于复杂而通常被视为 XML 中的高级主题。</span><span class="sxs-lookup"><span data-stu-id="73786-133">Due to their complexity, XML names are often considered to be an advanced topic in XML.</span></span> <span data-ttu-id="73786-134">有证据证明，这种复杂性不是由开发人员编程时通常使用的命名空间造成的，而是由命名空间前缀造成的。</span><span class="sxs-lookup"><span data-stu-id="73786-134">Arguably, this complexity comes not from namespaces, which developers use regularly in programming, but from namespace prefixes.</span></span> <span data-ttu-id="73786-135">使用命名空间前缀可以减少输入 XML 时需要的击键数或使 XML 更具可读性。</span><span class="sxs-lookup"><span data-stu-id="73786-135">Namespace prefixes can be useful to reduce the keystrokes required when you input XML, or to make XML easier to read.</span></span> <span data-ttu-id="73786-136">但是，前缀通常只是使用完整的 XML 命名空间的快捷方式，而且在大多数情况下都不是必需的。</span><span class="sxs-lookup"><span data-stu-id="73786-136">However, prefixes are often just a shortcut for using the full XML namespace, and are not required in most cases.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="73786-137">通过将所有前缀解析为其对应的 XML 命名空间来简化 XML 名称。</span><span class="sxs-lookup"><span data-stu-id="73786-137">simplifies XML names by resolving all prefixes to their corresponding XML namespace.</span></span> <span data-ttu-id="73786-138">如果需要，可以通过 <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> 方法可以使用前缀。</span><span class="sxs-lookup"><span data-stu-id="73786-138">Prefixes are available, if they are required, through the <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> method.</span></span>  
  
 <span data-ttu-id="73786-139">如果有必要，可以控制命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="73786-139">It is possible, if necessary, to control namespace prefixes.</span></span> <span data-ttu-id="73786-140">在某些情况下，如果使用的是其他 XML 系统（如 XSLT 或 XAML），则需要控制命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="73786-140">In some circumstances, if you are working with other XML systems, such as XSLT or XAML, you need to control namespace prefixes.</span></span> <span data-ttu-id="73786-141">例如，如果 XPath 表达式使用命名空间前缀且嵌入在 XSLT 样式表中，则将必须确保使用与 XPath 表达式中使用的前缀相匹配的命名空间前缀来序列化 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="73786-141">For example, if you have an XPath expression that uses namespace prefixes and is embedded in an XSLT stylesheet, you must make sure that your XML document is serialized with namespace prefixes that match those used in the XPath expression.</span></span>  
  
### <a name="xnamespace-class"></a><span data-ttu-id="73786-142">XNamespace 类</span><span class="sxs-lookup"><span data-stu-id="73786-142">XNamespace Class</span></span>  
 <span data-ttu-id="73786-143"><xref:System.Xml.Linq.XNamespace> 表示 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute> 的命名空间。</span><span class="sxs-lookup"><span data-stu-id="73786-143"><xref:System.Xml.Linq.XNamespace> represents a namespace for an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="73786-144">命名空间是 <xref:System.Xml.Linq.XName> 的一个组件。</span><span class="sxs-lookup"><span data-stu-id="73786-144">Namespaces are a component of an <xref:System.Xml.Linq.XName>.</span></span>  
  
### <a name="xnode-class"></a><span data-ttu-id="73786-145">XNode 类</span><span class="sxs-lookup"><span data-stu-id="73786-145">XNode Class</span></span>  
 <span data-ttu-id="73786-146"><xref:System.Xml.Linq.XNode> 是一个抽象类，它表示 XML 树的节点。</span><span class="sxs-lookup"><span data-stu-id="73786-146"><xref:System.Xml.Linq.XNode> is an abstract class that represents the nodes of an XML tree.</span></span> <span data-ttu-id="73786-147">下面的类派生自 <xref:System.Xml.Linq.XNode> 类：</span><span class="sxs-lookup"><span data-stu-id="73786-147">The following classes derive from the <xref:System.Xml.Linq.XNode> class:</span></span>  
  
- <xref:System.Xml.Linq.XText>  
  
- <xref:System.Xml.Linq.XContainer>  
  
- <xref:System.Xml.Linq.XComment>  
  
- <xref:System.Xml.Linq.XProcessingInstruction>  
  
- <xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a><span data-ttu-id="73786-148">XNodeDocumentOrderComparer 类</span><span class="sxs-lookup"><span data-stu-id="73786-148">XNodeDocumentOrderComparer Class</span></span>  
 <span data-ttu-id="73786-149"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> 提供用于比较节点的文档顺序的功能。</span><span class="sxs-lookup"><span data-stu-id="73786-149"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> provides functionality to compare nodes for their document order.</span></span>  
  
### <a name="xnodeequalitycomparer-class"></a><span data-ttu-id="73786-150">XNodeEqualityComparer 类</span><span class="sxs-lookup"><span data-stu-id="73786-150">XNodeEqualityComparer Class</span></span>  
 <span data-ttu-id="73786-151"><xref:System.Xml.Linq.XNodeEqualityComparer> 提供用于比较节点的值是否相等的功能。</span><span class="sxs-lookup"><span data-stu-id="73786-151"><xref:System.Xml.Linq.XNodeEqualityComparer> provides functionality to compare nodes for value equality.</span></span>  
  
### <a name="xobject-class"></a><span data-ttu-id="73786-152">XObject 类</span><span class="sxs-lookup"><span data-stu-id="73786-152">XObject Class</span></span>  
 <span data-ttu-id="73786-153"><xref:System.Xml.Linq.XObject> 是 <xref:System.Xml.Linq.XNode> 和 <xref:System.Xml.Linq.XAttribute> 的抽象基类。</span><span class="sxs-lookup"><span data-stu-id="73786-153"><xref:System.Xml.Linq.XObject> is an abstract base class of <xref:System.Xml.Linq.XNode> and <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="73786-154">它提供批注和事件功能。</span><span class="sxs-lookup"><span data-stu-id="73786-154">It provides annotation and event functionality.</span></span>  
  
### <a name="xobjectchange-class"></a><span data-ttu-id="73786-155">XObjectChange 类</span><span class="sxs-lookup"><span data-stu-id="73786-155">XObjectChange Class</span></span>  
 <span data-ttu-id="73786-156"><xref:System.Xml.Linq.XObjectChange> 指定对 <xref:System.Xml.Linq.XObject> 引发事件时的事件类型。</span><span class="sxs-lookup"><span data-stu-id="73786-156"><xref:System.Xml.Linq.XObjectChange> specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>  
  
### <a name="xobjectchangeeventargs-class"></a><span data-ttu-id="73786-157">XObjectChangeEventArgs 类</span><span class="sxs-lookup"><span data-stu-id="73786-157">XObjectChangeEventArgs Class</span></span>  
 <span data-ttu-id="73786-158"><xref:System.Xml.Linq.XObjectChangeEventArgs> 为 <xref:System.Xml.Linq.XObject.Changing> 和 <xref:System.Xml.Linq.XObject.Changed> 事件提供数据。</span><span class="sxs-lookup"><span data-stu-id="73786-158"><xref:System.Xml.Linq.XObjectChangeEventArgs> provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>  
  
### <a name="xprocessinginstruction-class"></a><span data-ttu-id="73786-159">XProcessingInstruction 类</span><span class="sxs-lookup"><span data-stu-id="73786-159">XProcessingInstruction Class</span></span>  
 <span data-ttu-id="73786-160"><xref:System.Xml.Linq.XProcessingInstruction> 表示一个 XML 处理指令。</span><span class="sxs-lookup"><span data-stu-id="73786-160"><xref:System.Xml.Linq.XProcessingInstruction> represents an XML processing instruction.</span></span> <span data-ttu-id="73786-161">处理指令将信息传递给处理 XML 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="73786-161">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
### <a name="xtext-class"></a><span data-ttu-id="73786-162">XText 类</span><span class="sxs-lookup"><span data-stu-id="73786-162">XText Class</span></span>  
 <span data-ttu-id="73786-163"><xref:System.Xml.Linq.XText> 表示一个文本节点。</span><span class="sxs-lookup"><span data-stu-id="73786-163"><xref:System.Xml.Linq.XText> represents a text node.</span></span> <span data-ttu-id="73786-164">多数情况下都不必使用此类。</span><span class="sxs-lookup"><span data-stu-id="73786-164">In most cases, you do not have to use this class.</span></span> <span data-ttu-id="73786-165">此类主要用于混合内容。</span><span class="sxs-lookup"><span data-stu-id="73786-165">This class is primarily used for mixed content.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73786-166">请参阅</span><span class="sxs-lookup"><span data-stu-id="73786-166">See also</span></span>

- [<span data-ttu-id="73786-167">LINQ to XML 编程概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="73786-167">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)

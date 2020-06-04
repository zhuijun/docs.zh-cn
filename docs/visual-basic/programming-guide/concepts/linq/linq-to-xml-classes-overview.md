---
title: LINQ to XML 类概述
ms.date: 07/20/2015
ms.assetid: f11b62b5-d522-4c23-92ae-23186dc16447
ms.openlocfilehash: 468435a0dfac64c85b3447f15f9cde63eb98aeb0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368876"
---
# <a name="linq-to-xml-classes-overview-visual-basic"></a><span data-ttu-id="bd51d-102">LINQ to XML 类概述（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="bd51d-102">LINQ to XML Classes Overview (Visual Basic)</span></span>
<span data-ttu-id="bd51d-103">本主题提供 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 命名空间中 <xref:System.Xml.Linq> 类的列表及每个类的简短说明。</span><span class="sxs-lookup"><span data-stu-id="bd51d-103">This topic provides a list of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] classes in the <xref:System.Xml.Linq> namespace, and a short description of each.</span></span>  
  
## <a name="linq-to-xml-classes"></a><span data-ttu-id="bd51d-104">LINQ to XML 类</span><span class="sxs-lookup"><span data-stu-id="bd51d-104">LINQ to XML Classes</span></span>  
  
### <a name="xattribute-class"></a><span data-ttu-id="bd51d-105">XAttribute 类</span><span class="sxs-lookup"><span data-stu-id="bd51d-105">XAttribute Class</span></span>  
 <span data-ttu-id="bd51d-106"><xref:System.Xml.Linq.XAttribute> 表示一个 XML 属性。</span><span class="sxs-lookup"><span data-stu-id="bd51d-106"><xref:System.Xml.Linq.XAttribute> represents an XML attribute.</span></span> <span data-ttu-id="bd51d-107">有关详细信息和示例，请参阅[System.xml.linq.xattribute> 类概述（Visual Basic）](xattribute-class-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="bd51d-107">For detailed information and examples, see [XAttribute Class Overview (Visual Basic)](xattribute-class-overview.md).</span></span>  
  
### <a name="xcdata-class"></a><span data-ttu-id="bd51d-108">XCData 类</span><span class="sxs-lookup"><span data-stu-id="bd51d-108">XCData Class</span></span>  
 <span data-ttu-id="bd51d-109"><xref:System.Xml.Linq.XCData> 表示一个 CDATA 文本节点。</span><span class="sxs-lookup"><span data-stu-id="bd51d-109"><xref:System.Xml.Linq.XCData> represents a CDATA text node.</span></span>  
  
### <a name="xcomment-class"></a><span data-ttu-id="bd51d-110">XComment 类</span><span class="sxs-lookup"><span data-stu-id="bd51d-110">XComment Class</span></span>  
 <span data-ttu-id="bd51d-111"><xref:System.Xml.Linq.XComment> 表示一个 XML 注释。</span><span class="sxs-lookup"><span data-stu-id="bd51d-111"><xref:System.Xml.Linq.XComment> represents an XML comment.</span></span>  
  
### <a name="xcontainer-class"></a><span data-ttu-id="bd51d-112">XContainer 类</span><span class="sxs-lookup"><span data-stu-id="bd51d-112">XContainer Class</span></span>  
 <span data-ttu-id="bd51d-113"><xref:System.Xml.Linq.XContainer> 是适用于可能具有子节点的所有节点的抽象基类。</span><span class="sxs-lookup"><span data-stu-id="bd51d-113"><xref:System.Xml.Linq.XContainer> is an abstract base class for all nodes that can have child nodes.</span></span> <span data-ttu-id="bd51d-114">下面的类派生自 <xref:System.Xml.Linq.XContainer> 类：</span><span class="sxs-lookup"><span data-stu-id="bd51d-114">The following classes derive from the <xref:System.Xml.Linq.XContainer> class:</span></span>  
  
- <xref:System.Xml.Linq.XElement>  
  
- <xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a><span data-ttu-id="bd51d-115">XDeclaration 类</span><span class="sxs-lookup"><span data-stu-id="bd51d-115">XDeclaration Class</span></span>  
 <span data-ttu-id="bd51d-116"><xref:System.Xml.Linq.XDeclaration> 表示一个 XML 声明。</span><span class="sxs-lookup"><span data-stu-id="bd51d-116"><xref:System.Xml.Linq.XDeclaration> represents an XML declaration.</span></span> <span data-ttu-id="bd51d-117">XML 声明用于声明 XML 版本和文档的编码。</span><span class="sxs-lookup"><span data-stu-id="bd51d-117">An XML declaration is used to declare the XML version and the encoding of a document.</span></span> <span data-ttu-id="bd51d-118">此外，XML 声明还指定 XML 文档是否为独立文档。</span><span class="sxs-lookup"><span data-stu-id="bd51d-118">In addition, an XML declaration specifies whether the XML document is stand-alone.</span></span> <span data-ttu-id="bd51d-119">如果文档是独立文档，则在外部 DTD 或从内部子集引用的外部参数实体中不存在外部标记声明。</span><span class="sxs-lookup"><span data-stu-id="bd51d-119">If a document is stand-alone, there are no external markup declarations, either in an external DTD, or in an external parameter entity referenced from the internal subset.</span></span>  
  
### <a name="xdocument-class"></a><span data-ttu-id="bd51d-120">XDocument 类</span><span class="sxs-lookup"><span data-stu-id="bd51d-120">XDocument Class</span></span>  
 <span data-ttu-id="bd51d-121"><xref:System.Xml.Linq.XDocument> 表示一个 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="bd51d-121"><xref:System.Xml.Linq.XDocument> represents an XML document.</span></span> <span data-ttu-id="bd51d-122">有关详细信息和示例，请参阅[XDocument 类概述（Visual Basic）](xdocument-class-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="bd51d-122">For detailed information and examples, see [XDocument Class Overview (Visual Basic)](xdocument-class-overview.md).</span></span>  
  
### <a name="xdocumenttype-class"></a><span data-ttu-id="bd51d-123">XDocumentType 类</span><span class="sxs-lookup"><span data-stu-id="bd51d-123">XDocumentType Class</span></span>  
 <span data-ttu-id="bd51d-124"><xref:System.Xml.Linq.XDocumentType> 表示一个 XML 文档类型定义 (DTD)。</span><span class="sxs-lookup"><span data-stu-id="bd51d-124"><xref:System.Xml.Linq.XDocumentType> represents an XML Document Type Definition (DTD).</span></span>  
  
### <a name="xelement-class"></a><span data-ttu-id="bd51d-125">XElement 类</span><span class="sxs-lookup"><span data-stu-id="bd51d-125">XElement Class</span></span>  
 <span data-ttu-id="bd51d-126"><xref:System.Xml.Linq.XElement> 表示一个 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="bd51d-126"><xref:System.Xml.Linq.XElement> represents an XML element.</span></span> <span data-ttu-id="bd51d-127">有关详细信息和示例，请参阅[System.xml.linq.xelement> 类概述（Visual Basic）](xelement-class-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="bd51d-127">For detailed information and examples, see [XElement Class Overview (Visual Basic)](xelement-class-overview.md).</span></span>  
  
### <a name="xname-class"></a><span data-ttu-id="bd51d-128">XName 类</span><span class="sxs-lookup"><span data-stu-id="bd51d-128">XName Class</span></span>  
 <span data-ttu-id="bd51d-129"><xref:System.Xml.Linq.XName> 表示元素 (<xref:System.Xml.Linq.XElement>) 和属性 (<xref:System.Xml.Linq.XAttribute>) 的名称。</span><span class="sxs-lookup"><span data-stu-id="bd51d-129"><xref:System.Xml.Linq.XName> represents names of elements (<xref:System.Xml.Linq.XElement>) and attributes (<xref:System.Xml.Linq.XAttribute>).</span></span> <span data-ttu-id="bd51d-130">有关详细信息和示例，请参阅[XDocument 类概述（Visual Basic）](xdocument-class-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="bd51d-130">For detailed information and examples, see [XDocument Class Overview (Visual Basic)](xdocument-class-overview.md).</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="bd51d-131">旨在使 XML 名称尽可能简单。</span><span class="sxs-lookup"><span data-stu-id="bd51d-131">is designed to make XML names as straightforward as possible.</span></span> <span data-ttu-id="bd51d-132">XML 名称由于复杂而通常被视为 XML 中的高级主题。</span><span class="sxs-lookup"><span data-stu-id="bd51d-132">Due to their complexity, XML names are often considered to be an advanced topic in XML.</span></span> <span data-ttu-id="bd51d-133">有证据证明，这种复杂性不是由开发人员编程时通常使用的命名空间造成的，而是由命名空间前缀造成的。</span><span class="sxs-lookup"><span data-stu-id="bd51d-133">Arguably, this complexity comes not from namespaces, which developers use regularly in programming, but from namespace prefixes.</span></span> <span data-ttu-id="bd51d-134">使用命名空间前缀可以减少输入 XML 时需要的击键数或使 XML 更具可读性。</span><span class="sxs-lookup"><span data-stu-id="bd51d-134">Namespace prefixes can be useful to reduce the keystrokes required when you input XML, or to make XML easier to read.</span></span> <span data-ttu-id="bd51d-135">但是，前缀通常只是使用完整的 XML 命名空间的快捷方式，而且在大多数情况下都不是必需的。</span><span class="sxs-lookup"><span data-stu-id="bd51d-135">However, prefixes are often just a shortcut for using the full XML namespace, and are not required in most cases.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="bd51d-136">通过将所有前缀解析为其对应的 XML 命名空间来简化 XML 名称。</span><span class="sxs-lookup"><span data-stu-id="bd51d-136">simplifies XML names by resolving all prefixes to their corresponding XML namespace.</span></span> <span data-ttu-id="bd51d-137">如果需要，可以通过 <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> 方法可以使用前缀。</span><span class="sxs-lookup"><span data-stu-id="bd51d-137">Prefixes are available, if they are required, through the <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> method.</span></span>  
  
 <span data-ttu-id="bd51d-138">如果有必要，可以控制命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="bd51d-138">It is possible, if necessary, to control namespace prefixes.</span></span> <span data-ttu-id="bd51d-139">在某些情况下，如果使用的是其他 XML 系统（如 XSLT 或 XAML），则需要控制命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="bd51d-139">In some circumstances, if you are working with other XML systems, such as XSLT or XAML, you need to control namespace prefixes.</span></span> <span data-ttu-id="bd51d-140">例如，如果 XPath 表达式使用命名空间前缀且嵌入在 XSLT 样式表中，则将必须确保使用与 XPath 表达式中使用的前缀相匹配的命名空间前缀来序列化 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="bd51d-140">For example, if you have an XPath expression that uses namespace prefixes and is embedded in an XSLT stylesheet, you must make sure that your XML document is serialized with namespace prefixes that match those used in the XPath expression.</span></span>  
  
### <a name="xnamespace-class"></a><span data-ttu-id="bd51d-141">XNamespace 类</span><span class="sxs-lookup"><span data-stu-id="bd51d-141">XNamespace Class</span></span>  
 <span data-ttu-id="bd51d-142"><xref:System.Xml.Linq.XNamespace> 表示 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute> 的命名空间。</span><span class="sxs-lookup"><span data-stu-id="bd51d-142"><xref:System.Xml.Linq.XNamespace> represents a namespace for an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="bd51d-143">命名空间是 <xref:System.Xml.Linq.XName> 的一个组件。</span><span class="sxs-lookup"><span data-stu-id="bd51d-143">Namespaces are a component of an <xref:System.Xml.Linq.XName>.</span></span>  
  
### <a name="xnode-class"></a><span data-ttu-id="bd51d-144">XNode 类</span><span class="sxs-lookup"><span data-stu-id="bd51d-144">XNode Class</span></span>  
 <span data-ttu-id="bd51d-145"><xref:System.Xml.Linq.XNode> 是一个抽象类，它表示 XML 树的节点。</span><span class="sxs-lookup"><span data-stu-id="bd51d-145"><xref:System.Xml.Linq.XNode> is an abstract class that represents the nodes of an XML tree.</span></span> <span data-ttu-id="bd51d-146">下面的类派生自 <xref:System.Xml.Linq.XNode> 类：</span><span class="sxs-lookup"><span data-stu-id="bd51d-146">The following classes derive from the <xref:System.Xml.Linq.XNode> class:</span></span>  
  
- <xref:System.Xml.Linq.XText>  
  
- <xref:System.Xml.Linq.XContainer>  
  
- <xref:System.Xml.Linq.XComment>  
  
- <xref:System.Xml.Linq.XProcessingInstruction>  
  
- <xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a><span data-ttu-id="bd51d-147">XNodeDocumentOrderComparer 类</span><span class="sxs-lookup"><span data-stu-id="bd51d-147">XNodeDocumentOrderComparer Class</span></span>  
 <span data-ttu-id="bd51d-148"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> 提供用于比较节点的文档顺序的功能。</span><span class="sxs-lookup"><span data-stu-id="bd51d-148"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> provides functionality to compare nodes for their document order.</span></span>  
  
### <a name="xnodeequalitycomparer-class"></a><span data-ttu-id="bd51d-149">XNodeEqualityComparer 类</span><span class="sxs-lookup"><span data-stu-id="bd51d-149">XNodeEqualityComparer Class</span></span>  
 <span data-ttu-id="bd51d-150"><xref:System.Xml.Linq.XNodeEqualityComparer> 提供用于比较节点的值是否相等的功能。</span><span class="sxs-lookup"><span data-stu-id="bd51d-150"><xref:System.Xml.Linq.XNodeEqualityComparer> provides functionality to compare nodes for value equality.</span></span>  
  
### <a name="xobject-class"></a><span data-ttu-id="bd51d-151">XObject 类</span><span class="sxs-lookup"><span data-stu-id="bd51d-151">XObject Class</span></span>  
 <span data-ttu-id="bd51d-152"><xref:System.Xml.Linq.XObject> 是 <xref:System.Xml.Linq.XNode> 和 <xref:System.Xml.Linq.XAttribute> 的抽象基类。</span><span class="sxs-lookup"><span data-stu-id="bd51d-152"><xref:System.Xml.Linq.XObject> is an abstract base class of <xref:System.Xml.Linq.XNode> and <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="bd51d-153">它提供批注和事件功能。</span><span class="sxs-lookup"><span data-stu-id="bd51d-153">It provides annotation and event functionality.</span></span>  
  
### <a name="xobjectchange-class"></a><span data-ttu-id="bd51d-154">XObjectChange 类</span><span class="sxs-lookup"><span data-stu-id="bd51d-154">XObjectChange Class</span></span>  
 <span data-ttu-id="bd51d-155"><xref:System.Xml.Linq.XObjectChange> 指定对 <xref:System.Xml.Linq.XObject> 引发事件时的事件类型。</span><span class="sxs-lookup"><span data-stu-id="bd51d-155"><xref:System.Xml.Linq.XObjectChange> specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>  
  
### <a name="xobjectchangeeventargs-class"></a><span data-ttu-id="bd51d-156">XObjectChangeEventArgs 类</span><span class="sxs-lookup"><span data-stu-id="bd51d-156">XObjectChangeEventArgs Class</span></span>  
 <span data-ttu-id="bd51d-157"><xref:System.Xml.Linq.XObjectChangeEventArgs> 为 <xref:System.Xml.Linq.XObject.Changing> 和 <xref:System.Xml.Linq.XObject.Changed> 事件提供数据。</span><span class="sxs-lookup"><span data-stu-id="bd51d-157"><xref:System.Xml.Linq.XObjectChangeEventArgs> provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>  
  
### <a name="xprocessinginstruction-class"></a><span data-ttu-id="bd51d-158">XProcessingInstruction 类</span><span class="sxs-lookup"><span data-stu-id="bd51d-158">XProcessingInstruction Class</span></span>  
 <span data-ttu-id="bd51d-159"><xref:System.Xml.Linq.XProcessingInstruction> 表示一个 XML 处理指令。</span><span class="sxs-lookup"><span data-stu-id="bd51d-159"><xref:System.Xml.Linq.XProcessingInstruction> represents an XML processing instruction.</span></span> <span data-ttu-id="bd51d-160">处理指令将信息传递给处理 XML 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="bd51d-160">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
### <a name="xtext-class"></a><span data-ttu-id="bd51d-161">XText 类</span><span class="sxs-lookup"><span data-stu-id="bd51d-161">XText Class</span></span>  
 <span data-ttu-id="bd51d-162"><xref:System.Xml.Linq.XText> 表示一个文本节点。</span><span class="sxs-lookup"><span data-stu-id="bd51d-162"><xref:System.Xml.Linq.XText> represents a text node.</span></span> <span data-ttu-id="bd51d-163">多数情况下都不必使用此类。</span><span class="sxs-lookup"><span data-stu-id="bd51d-163">In most cases, you do not have to use this class.</span></span> <span data-ttu-id="bd51d-164">此类主要用于混合内容。</span><span class="sxs-lookup"><span data-stu-id="bd51d-164">This class is primarily used for mixed content.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd51d-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bd51d-165">See also</span></span>

- [<span data-ttu-id="bd51d-166">LINQ to XML 编程概述（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="bd51d-166">LINQ to XML Programming Overview (Visual Basic)</span></span>](linq-to-xml-programming-overview.md)

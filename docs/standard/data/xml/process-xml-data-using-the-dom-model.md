---
title: 使用 DOM 模型处理 XML 数据
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 56b6e9c7-ed82-4a65-a647-7be32c83bcc8
ms.openlocfilehash: 242554cc948ef16972ffd26d5464dae2727ed339
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290832"
---
# <a name="process-xml-data-using-the-dom-model"></a><span data-ttu-id="010d3-102">使用 DOM 模型处理 XML 数据</span><span class="sxs-lookup"><span data-stu-id="010d3-102">Process XML Data Using the DOM Model</span></span>
<span data-ttu-id="010d3-103">XML 文档对象模型 (DOM) 将 XML 数据作为一组标准的对象对待，用于处理内存中的 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="010d3-103">The XML Document Object Model (DOM) treats XML data as a standard set of objects and is used to process XML data in memory.</span></span> <span data-ttu-id="010d3-104">`System.Xml` 命名空间提供 XML 文档、片断、节点或节点集的编程表示形式。</span><span class="sxs-lookup"><span data-stu-id="010d3-104">The `System.Xml` namespace provides a programmatic representation of XML documents, fragments, nodes, or node-sets.</span></span> <span data-ttu-id="010d3-105">基于万维网联合会 (W3C) DOM 级别 1 核心和 DOM 级别 2 核心建议。</span><span class="sxs-lookup"><span data-stu-id="010d3-105">It is based on the World Wide Web Consortium (W3C) DOM Level 1 Core and the DOM Level 2 Core recommendations.</span></span>  
  
 <span data-ttu-id="010d3-106"><xref:System.Xml.XmlDocument> 类表示 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="010d3-106">The <xref:System.Xml.XmlDocument> class represents an XML document.</span></span> <span data-ttu-id="010d3-107">包括用于检索和创建所有其他 XML 对象的成员。</span><span class="sxs-lookup"><span data-stu-id="010d3-107">It includes members for retrieving and creating all other XML objects.</span></span> <span data-ttu-id="010d3-108">使用 <xref:System.Xml.XmlDocument> 及其相关的类，可以构造 XML 文档、加载和访问数据、修改数据以及保存更改。</span><span class="sxs-lookup"><span data-stu-id="010d3-108">Using the <xref:System.Xml.XmlDocument>, and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="010d3-109">本节内容</span><span class="sxs-lookup"><span data-stu-id="010d3-109">In This Section</span></span>  
  
- [<span data-ttu-id="010d3-110">XML 文档对象模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="010d3-110">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)  
  
- [<span data-ttu-id="010d3-111">XML 节点类型</span><span class="sxs-lookup"><span data-stu-id="010d3-111">Types of XML Nodes</span></span>](types-of-xml-nodes.md)  
  
- [<span data-ttu-id="010d3-112">XML 文档对象模型 (DOM) 层次结构</span><span class="sxs-lookup"><span data-stu-id="010d3-112">XML Document Object Model (DOM) Hierarchy</span></span>](xml-document-object-model-dom-hierarchy.md)  
  
- [<span data-ttu-id="010d3-113">将对象层次结构映射到 XML 数据</span><span class="sxs-lookup"><span data-stu-id="010d3-113">Mapping the Object Hierarchy to XML Data</span></span>](mapping-the-object-hierarchy-to-xml-data.md)  
  
- [<span data-ttu-id="010d3-114">创建 XML 文档</span><span class="sxs-lookup"><span data-stu-id="010d3-114">XML Document Creation</span></span>](xml-document-creation.md)  
  
- [<span data-ttu-id="010d3-115">将 XML 文档读入 DOM</span><span class="sxs-lookup"><span data-stu-id="010d3-115">Reading an XML Document into the DOM</span></span>](reading-an-xml-document-into-the-dom.md)  
  
- [<span data-ttu-id="010d3-116">将节点插入 XML 文档中</span><span class="sxs-lookup"><span data-stu-id="010d3-116">Inserting Nodes into an XML Document</span></span>](inserting-nodes-into-an-xml-document.md)  
  
- [<span data-ttu-id="010d3-117">从 XML 删除文档中的节点、内容和值</span><span class="sxs-lookup"><span data-stu-id="010d3-117">Removing Nodes, Content, and Values from an XML Document</span></span>](removing-nodes-content-and-values-from-an-xml-document.md)  
  
- [<span data-ttu-id="010d3-118">修改 XML 文档中的节点、内容和值</span><span class="sxs-lookup"><span data-stu-id="010d3-118">Modifying Nodes, Content, and Values in an XML Document</span></span>](modifying-nodes-content-and-values-in-an-xml-document.md)  
  
- [<span data-ttu-id="010d3-119">在 DOM 中验证 XML 文档</span><span class="sxs-lookup"><span data-stu-id="010d3-119">Validating an XML Document in the DOM</span></span>](validating-an-xml-document-in-the-dom.md)  
  
- [<span data-ttu-id="010d3-120">保存和编写文档</span><span class="sxs-lookup"><span data-stu-id="010d3-120">Saving and Writing a Document</span></span>](saving-and-writing-a-document.md)  
  
- [<span data-ttu-id="010d3-121">使用 XPath 导航选择节点</span><span class="sxs-lookup"><span data-stu-id="010d3-121">Select Nodes Using XPath Navigation</span></span>](select-nodes-using-xpath-navigation.md)  
  
- [<span data-ttu-id="010d3-122">解析外部资源</span><span class="sxs-lookup"><span data-stu-id="010d3-122">Resolving External Resources</span></span>](resolving-external-resources.md)  
  
- [<span data-ttu-id="010d3-123">使用 XmlNameTable 的对象比较</span><span class="sxs-lookup"><span data-stu-id="010d3-123">Object Comparison Using XmlNameTable</span></span>](object-comparison-using-xmlnametable.md)  
  
- [<span data-ttu-id="010d3-124">NamedNodeMap 和 NodeList 中的节点集合</span><span class="sxs-lookup"><span data-stu-id="010d3-124">Node Collections in NamedNodeMaps and NodeLists</span></span>](node-collections-in-namednodemaps-and-nodelists.md)  
  
- [<span data-ttu-id="010d3-125">NodeList 和 NamedNodeMap 的动态更新</span><span class="sxs-lookup"><span data-stu-id="010d3-125">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>](dynamic-updates-to-nodelists-and-namednodemaps.md)  
  
- [<span data-ttu-id="010d3-126">DOM 中的命名空间支持</span><span class="sxs-lookup"><span data-stu-id="010d3-126">Namespace Support in the DOM</span></span>](namespace-support-in-the-dom.md)  
  
- [<span data-ttu-id="010d3-127">使用 XmlNodeChangedEventArgs 的 XML 文档中的事件处理</span><span class="sxs-lookup"><span data-stu-id="010d3-127">Event Handling in an XML Document Using the XmlNodeChangedEventArgs</span></span>](event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md)  
  
- [<span data-ttu-id="010d3-128">扩展 DOM</span><span class="sxs-lookup"><span data-stu-id="010d3-128">Extending the DOM</span></span>](extending-the-dom.md)  
  
## <a name="related-sections"></a><span data-ttu-id="010d3-129">相关章节</span><span class="sxs-lookup"><span data-stu-id="010d3-129">Related Sections</span></span>  
 [<span data-ttu-id="010d3-130">使用 XPath 数据模型处理 XML 数据</span><span class="sxs-lookup"><span data-stu-id="010d3-130">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="010d3-131">讨论如何使用 <xref:System.Xml.XPath.XPathNavigator> 类进行 XML 处理。</span><span class="sxs-lookup"><span data-stu-id="010d3-131">Discusses XML processing using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>

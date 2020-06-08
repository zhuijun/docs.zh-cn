---
title: 使用 XPath 数据模型处理 XML 数据
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 536c6fce-1453-4654-9c72-bca54d47e081
ms.openlocfilehash: d449fe19640b19b1417c41b3a1ac7bd3a4de907a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291287"
---
# <a name="process-xml-data-using-the-xpath-data-model"></a><span data-ttu-id="2372d-102">使用 XPath 数据模型处理 XML 数据</span><span class="sxs-lookup"><span data-stu-id="2372d-102">Process XML Data Using the XPath Data Model</span></span>
<span data-ttu-id="2372d-103"><xref:System.Xml?displayProperty=nameWithType> 命名空间使用 <xref:System.Xml.XmlDocument> 或 <xref:System.Xml.XPath.XPathDocument> 类提供内存中 XML 文档、片断、节点或节点集的编程表示形式。</span><span class="sxs-lookup"><span data-stu-id="2372d-103">The <xref:System.Xml?displayProperty=nameWithType> namespace provides a programmatic representation of XML documents, fragments, nodes, or node-sets in-memory, using the <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument> classes.</span></span>  
  
 <span data-ttu-id="2372d-104"><xref:System.Xml.XPath.XPathDocument> 类使用 XPath 数据模型提供 XML 文档在内存中的快速只读表示形式。</span><span class="sxs-lookup"><span data-stu-id="2372d-104">The <xref:System.Xml.XPath.XPathDocument> class provides a fast, read-only, in-memory representation of an XML document using the XPath data model.</span></span> <span data-ttu-id="2372d-105"><xref:System.Xml.XmlDocument> 类提供实现 W3C 文档对象模型 (DOM) 级别 1 核心和核心 DOM 级别 2 的 XML 文档在内存中的可编辑表示形式。</span><span class="sxs-lookup"><span data-stu-id="2372d-105">The <xref:System.Xml.XmlDocument> class provides an editable in-memory representation of an XML document implementing W3C Document Object Model (DOM) Level 1 Core and Core DOM Level 2.</span></span> <span data-ttu-id="2372d-106">这两个类均实现 <xref:System.Xml.XPath.IXPathNavigable> 接口，并返回 <xref:System.Xml.XPath.XPathNavigator> 对象，用于选择、计算、浏览和（在某些情况下）编辑基础 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="2372d-106">Both classes implement the <xref:System.Xml.XPath.IXPathNavigable> interface and return an <xref:System.Xml.XPath.XPathNavigator> object used to select, evaluate, navigate, and in some cases, edit the underlying XML data.</span></span>  
  
 <span data-ttu-id="2372d-107">下面各节介绍 <xref:System.Xml.XPath.XPathNavigator> 类的功能（基于返回该类的类）。</span><span class="sxs-lookup"><span data-stu-id="2372d-107">The following sections describe the functionality of the <xref:System.Xml.XPath.XPathNavigator> class based on the class that returns it.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2372d-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="2372d-108">In This Section</span></span>  
 [<span data-ttu-id="2372d-109">使用 XPathDocument 和 XmlDocument 读取 XML 数据</span><span class="sxs-lookup"><span data-stu-id="2372d-109">Reading XML Data using XPathDocument and XmlDocument</span></span>](reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 <span data-ttu-id="2372d-110">描述如何创建只读 <xref:System.Xml.XPath.XPathDocument> 类对象来读取 XML 文档以及如何创建可编辑的 <xref:System.Xml.XmlDocument> 类对象来读取和编辑 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="2372d-110">Describes how to create a read-only <xref:System.Xml.XPath.XPathDocument> class object to read an XML document and how to create an editable <xref:System.Xml.XmlDocument> class object to read and edit an XML document.</span></span> <span data-ttu-id="2372d-111">本主题还描述如何从每个类返回 <xref:System.Xml.XPath.XPathNavigator> 对象，以浏览和编辑 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="2372d-111">This topic also describes how return an <xref:System.Xml.XPath.XPathNavigator> object from each class to navigate and edit an XML document.</span></span>  
  
 [<span data-ttu-id="2372d-112">使用 XPathNavigator 选择、计算和匹配 XML 数据</span><span class="sxs-lookup"><span data-stu-id="2372d-112">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="2372d-113">介绍 <xref:System.Xml.XPath.XPathNavigator> 类中的方法，这些方法用于使用 XPath 查询在 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 对象中选择节点，计算和检查 XPath 表达式的结果，并确定 XML 文档中的节点是否与给定的 XPath 表达式匹配。</span><span class="sxs-lookup"><span data-stu-id="2372d-113">Describes the methods of the <xref:System.Xml.XPath.XPathNavigator> class used to select nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath query, evaluate and examine the results of an XPath expression, and determine if a node in an XML document matches a given XPath expression.</span></span>  
  
 [<span data-ttu-id="2372d-114">使用 XPathNavigator 访问 XML 数据</span><span class="sxs-lookup"><span data-stu-id="2372d-114">Accessing XML Data using XPathNavigator</span></span>](accessing-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="2372d-115">介绍 <xref:System.Xml.XPath.XPathNavigator> 类中的方法，这些方法用于在 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 对象中浏览节点，提取 XML 数据，以及访问强类型 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="2372d-115">Describes the methods of the <xref:System.Xml.XPath.XPathNavigator> class used to navigate nodes, extract XML data and access strongly typed XML data in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="2372d-116">使用 XPathNavigator 编辑 XML 数据</span><span class="sxs-lookup"><span data-stu-id="2372d-116">Editing XML Data using XPathNavigator</span></span>](editing-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="2372d-117">介绍 <xref:System.Xml.XPath.XPathNavigator> 类中的方法，这些方法用于在 <xref:System.Xml.XmlDocument> 对象包含的 XML 文档中插入、修改和移除节点和值。</span><span class="sxs-lookup"><span data-stu-id="2372d-117">Describes the methods of the <xref:System.Xml.XPath.XPathNavigator> class used to insert, modify and remove nodes and values from an XML document contained in an <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="2372d-118">使用 XPathNavigator 验证架构</span><span class="sxs-lookup"><span data-stu-id="2372d-118">Schema Validation using XPathNavigator</span></span>](schema-validation-using-xpathnavigator.md)  
 <span data-ttu-id="2372d-119">描述如何验证 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 对象中包含的 XML 内容。</span><span class="sxs-lookup"><span data-stu-id="2372d-119">Describes the ways to validate the XML content contained in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2372d-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="2372d-120">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="2372d-121">使用 DOM 模型处理 XML 数据</span><span class="sxs-lookup"><span data-stu-id="2372d-121">Process XML Data Using the DOM Model</span></span>](process-xml-data-using-the-dom-model.md)

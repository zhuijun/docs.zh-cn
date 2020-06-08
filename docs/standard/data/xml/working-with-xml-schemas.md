---
title: 使用 XML 架构
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: bbbcc70c-bf9a-4f6a-af72-1bab5384a187
ms.openlocfilehash: f239d67d959c1f7a0bfebfaaaa49de9cf9c9a111
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281682"
---
# <a name="working-with-xml-schemas"></a><span data-ttu-id="c52f4-102">使用 XML 架构</span><span class="sxs-lookup"><span data-stu-id="c52f4-102">Working with XML Schemas</span></span>
<span data-ttu-id="c52f4-103">要定义 XML 文档的结构及其元素关系、数据类型和内容约束，请使用文档类型定义 (DTD) 或 XML 架构定义语言 (XSD) 架构。</span><span class="sxs-lookup"><span data-stu-id="c52f4-103">To define the structure of an XML document, as well as its element relationships, data types, and content constraints, you use a document type definition (DTD) or XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="c52f4-104">尽管 XML 文档如果符合万维网联合会 (W3C) 可扩展标记语言 (XML) 1.0 建议定义的所有语法要求，就被认为格式正确，但是，除非其格式正确并且符合其 DTD 或架构定义的约束，否则，不会认为该文档有效。</span><span class="sxs-lookup"><span data-stu-id="c52f4-104">Although an XML document is considered to be well-formed if it meets all the syntactical requirements defined by the World Wide Web Consortium (W3C) Extensible Markup Language (XML) 1.0 Recommendation, it is not considered valid unless it is both well-formed and conforms to the constraints defined by its DTD or schema.</span></span> <span data-ttu-id="c52f4-105">因此，尽管所有有效 XML 文档的格式都是正确的，但是并非所有格式正确的 XML 文档都有效。</span><span class="sxs-lookup"><span data-stu-id="c52f4-105">Therefore, although all valid XML documents are well-formed, not all well-formed XML documents are valid.</span></span>  
  
 <span data-ttu-id="c52f4-106">若要详细了解 XML，请参阅 [W3C XML 1.0 建议](https://www.w3.org/TR/REC-xml/)。</span><span class="sxs-lookup"><span data-stu-id="c52f4-106">For more information about XML, see the [W3C XML 1.0 Recommendation](https://www.w3.org/TR/REC-xml/).</span></span> <span data-ttu-id="c52f4-107">有关 XML 架构的详细信息，请参阅 [W3C XML 架构第 1 部分：Structures Recommendation](https://www.w3.org/TR/xmlschema-1/)（W3C XML 架构第 1 部分：结构建议）和 [W3C XML Schema Part 2:Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/)（W3C XML 架构第 2 部分：数据类型建议）建议。</span><span class="sxs-lookup"><span data-stu-id="c52f4-107">For more information about XML Schema, see the [W3C XML Schema Part 1: Structures Recommendation](https://www.w3.org/TR/xmlschema-1/) and the [W3C XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/) recommendations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c52f4-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="c52f4-108">In This Section</span></span>  
 [<span data-ttu-id="c52f4-109">XML 架构对象模型 (SOM)</span><span class="sxs-lookup"><span data-stu-id="c52f4-109">XML Schema Object Model (SOM)</span></span>](xml-schema-object-model-som.md)  
 <span data-ttu-id="c52f4-110">讨论 <xref:System.Xml.Schema?displayProperty=nameWithType> 命名空间中的架构对象模型 (SOM)，SOM 提供一组类，用于从文件读取架构定义语言 (XSD) 架构或通过编程创建内存中架构。</span><span class="sxs-lookup"><span data-stu-id="c52f4-110">Discusses the Schema Object Model (SOM) in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that provides a set of classes that allows you to read a Schema definition language (XSD) schema from a file or programmatically create a schema in-memory.</span></span>  
  
 [<span data-ttu-id="c52f4-111">用于编译架构的 XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="c52f4-111">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)  
 <span data-ttu-id="c52f4-112">讨论 <xref:System.Xml.Schema.XmlSchemaSet> 类，该类是可以存储和验证 XSD 架构的缓存。</span><span class="sxs-lookup"><span data-stu-id="c52f4-112">Discusses the <xref:System.Xml.Schema.XmlSchemaSet> class that is a cache where XSD schemas can be stored and validated.</span></span>  
  
 [<span data-ttu-id="c52f4-113">XmlSchemaValidator 基于推送的验证</span><span class="sxs-lookup"><span data-stu-id="c52f4-113">XmlSchemaValidator Push-Based Validation</span></span>](xmlschemavalidator-push-based-validation.md)  
 <span data-ttu-id="c52f4-114">讨论 <xref:System.Xml.Schema.XmlSchemaValidator> 类，该类提供了一种高效、高性能的机制，通过基于推送的方式针对 XSD 架构验证 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="c52f4-114">Discusses the <xref:System.Xml.Schema.XmlSchemaValidator> class that provides an efficient, high-performance mechanism to validate XML data against XSD schemas in a push-based manner.</span></span>  
  
 [<span data-ttu-id="c52f4-115">推断 XML 架构</span><span class="sxs-lookup"><span data-stu-id="c52f4-115">Inferring an XML Schema</span></span>](inferring-an-xml-schema.md)  
 <span data-ttu-id="c52f4-116">讨论如何使用 <xref:System.Xml.Schema.XmlSchemaInference> 类从 XML 文档的结构推断 XSD 架构。</span><span class="sxs-lookup"><span data-stu-id="c52f4-116">Discusses how to use the <xref:System.Xml.Schema.XmlSchemaInference> class to infer an XSD schema from the structure of an XML document.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c52f4-117">参考</span><span class="sxs-lookup"><span data-stu-id="c52f4-117">Reference</span></span>  
 <span data-ttu-id="c52f4-118"><xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="c52f4-118"><xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader></span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c52f4-119">相关章节</span><span class="sxs-lookup"><span data-stu-id="c52f4-119">Related Sections</span></span>  
 [<span data-ttu-id="c52f4-120">在 DOM 中验证 XML 文档</span><span class="sxs-lookup"><span data-stu-id="c52f4-120">Validating an XML Document in the DOM</span></span>](validating-an-xml-document-in-the-dom.md)  
 <span data-ttu-id="c52f4-121">讨论如何在文档对象模型 (DOM) 中验证 XML。</span><span class="sxs-lookup"><span data-stu-id="c52f4-121">Discusses how to validate the XML in the Document Object Model (DOM).</span></span> <span data-ttu-id="c52f4-122">可以在 XML 加载到 DOM 中时进行验证，也可以在 DOM 中验证以前未经过验证的 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="c52f4-122">You can validate the XML as it is loaded into the DOM, or validate a previously unvalidated XML document in the DOM.</span></span>  
  
 [<span data-ttu-id="c52f4-123">使用 XPathNavigator 验证架构</span><span class="sxs-lookup"><span data-stu-id="c52f4-123">Schema Validation using XPathNavigator</span></span>](schema-validation-using-xpathnavigator.md)  
 <span data-ttu-id="c52f4-124">讨论如何验证使用 <xref:System.Xml.XPath.XPathNavigator> 类浏览和编辑的 XML。</span><span class="sxs-lookup"><span data-stu-id="c52f4-124">Discusses how to validate XML being navigated and edited using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>

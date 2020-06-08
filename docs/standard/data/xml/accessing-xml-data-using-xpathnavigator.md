---
title: 使用 XPathNavigator 访问 XML 数据
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: c57b46e6-5c77-408f-bc4e-67a5dcc9cc05
ms.openlocfilehash: 717937ebca9b5775619b0dde749f0566c73ca116
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290923"
---
# <a name="accessing-xml-data-using-xpathnavigator"></a><span data-ttu-id="630b7-102">使用 XPathNavigator 访问 XML 数据</span><span class="sxs-lookup"><span data-stu-id="630b7-102">Accessing XML Data using XPathNavigator</span></span>
<span data-ttu-id="630b7-103"><xref:System.Xml.XPath.XPathNavigator> 类提供的方法用于在 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 对象中浏览节点，提取 XML 数据，以及访问强类型 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="630b7-103">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to navigate nodes, extract XML data and access strongly typed XML data in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="630b7-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="630b7-104">In This Section</span></span>  
 [<span data-ttu-id="630b7-105">使用 XPathNavigator 的节点集定位</span><span class="sxs-lookup"><span data-stu-id="630b7-105">Node Set Navigation Using XPathNavigator</span></span>](node-set-navigation-using-xpathnavigator.md)  
 <span data-ttu-id="630b7-106">介绍用于在 <xref:System.Xml.XPath.XPathNavigator> 或 <xref:System.Xml.XPath.XPathDocument> 对象中浏览节点的 <xref:System.Xml.XmlDocument> 类的节点集浏览方法。</span><span class="sxs-lookup"><span data-stu-id="630b7-106">Describes the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class used to navigate nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="630b7-107">使用 XPathNavigator 的属性和命名空间节点定位</span><span class="sxs-lookup"><span data-stu-id="630b7-107">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
 <span data-ttu-id="630b7-108">介绍 <xref:System.Xml.XPath.XPathNavigator> 类的属性和命名空间节点浏览方法。</span><span class="sxs-lookup"><span data-stu-id="630b7-108">Describes the attribute and namespace node navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 [<span data-ttu-id="630b7-109">使用 XPathNavigator 提取 XML 数据</span><span class="sxs-lookup"><span data-stu-id="630b7-109">Extract XML Data Using XPathNavigator</span></span>](extract-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="630b7-110">介绍从 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 对象提取 XML 数据的各种方法。</span><span class="sxs-lookup"><span data-stu-id="630b7-110">Describes the various methods of extracting XML data from an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="630b7-111">使用 XPathNavigator 访问强类型 XML 数据</span><span class="sxs-lookup"><span data-stu-id="630b7-111">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](accessing-strongly-typed-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="630b7-112">描述如何使用 <xref:System.Xml.XPath.XPathDocument> 类访问 <xref:System.Xml.XmlDocument> 或 <xref:System.Xml.XPath.XPathNavigator> 对象中的强类型 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="630b7-112">Describes accessing strongly typed XML data in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 [<span data-ttu-id="630b7-113">用户定义的函数和变量</span><span class="sxs-lookup"><span data-stu-id="630b7-113">User Defined Functions and Variables</span></span>](user-defined-functions-and-variables.md)  
 <span data-ttu-id="630b7-114">描述如何实现一个自定义 <xref:System.Xml.Xsl.XsltContext> 类，以及用于支持扩展函数和变量的接口 <xref:System.Xml.Xsl.IXsltContextFunction> 和 <xref:System.Xml.Xsl.IXsltContextVariable>。</span><span class="sxs-lookup"><span data-stu-id="630b7-114">Describes implementing a custom <xref:System.Xml.Xsl.XsltContext> class along with the interfaces <xref:System.Xml.Xsl.IXsltContextFunction> and <xref:System.Xml.Xsl.IXsltContextVariable> that support extension functions and variables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="630b7-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="630b7-115">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="630b7-116">使用 XPath 数据模型处理 XML 数据</span><span class="sxs-lookup"><span data-stu-id="630b7-116">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="630b7-117">使用 XPathDocument 和 XmlDocument 读取 XML 数据</span><span class="sxs-lookup"><span data-stu-id="630b7-117">Reading XML Data using XPathDocument and XmlDocument</span></span>](reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [<span data-ttu-id="630b7-118">使用 XPathNavigator 选择、计算和匹配 XML 数据</span><span class="sxs-lookup"><span data-stu-id="630b7-118">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="630b7-119">使用 XPathNavigator 编辑 XML 数据</span><span class="sxs-lookup"><span data-stu-id="630b7-119">Editing XML Data using XPathNavigator</span></span>](editing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="630b7-120">使用 XPathNavigator 验证架构</span><span class="sxs-lookup"><span data-stu-id="630b7-120">Schema Validation using XPathNavigator</span></span>](schema-validation-using-xpathnavigator.md)

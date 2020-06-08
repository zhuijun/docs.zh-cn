---
title: 转换中的节点集
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ad034f0e-ff8b-4a71-9a4c-528c754263c4
ms.openlocfilehash: 33cbae05cf35904903189ce767090d3d3cca8e4d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288740"
---
# <a name="node-sets-in-transformations"></a><span data-ttu-id="c00db-102">转换中的节点集</span><span class="sxs-lookup"><span data-stu-id="c00db-102">Node Sets in Transformations</span></span>
<span data-ttu-id="c00db-103">节点集是从 XML 路径语言 (XPath) 表达式返回的四种基本数据类型之一。</span><span class="sxs-lookup"><span data-stu-id="c00db-103">Node sets are one of four basic data types that are returned from XML Path Language (XPath) expressions.</span></span> <span data-ttu-id="c00db-104">节点集是按文档顺序创建的无重复节点的无序集合，可将其分配给样式表中的某个变量。</span><span class="sxs-lookup"><span data-stu-id="c00db-104">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c00db-105"><xref:System.Xml.Xsl.XslTransform> 类在 .NET Framework 2.0 中已过时。</span><span class="sxs-lookup"><span data-stu-id="c00db-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="c00db-106">可以使用 <xref:System.Xml.Xsl.XslCompiledTransform> 类执行可扩展样式表语言转换 (XSLT) 转换。</span><span class="sxs-lookup"><span data-stu-id="c00db-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="c00db-107">请参阅[使用 XslCompiledTransform 类](using-the-xslcompiledtransform-class.md)和[从 XslTransform 类迁移](migrating-from-the-xsltransform-class.md)，以获取详细信息。</span><span class="sxs-lookup"><span data-stu-id="c00db-107">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="c00db-108">节点集是从 XPath 表达式返回的四种基本数据类型之一。</span><span class="sxs-lookup"><span data-stu-id="c00db-108">Node sets are one of four basic data types that are returned from XPath expressions.</span></span> <span data-ttu-id="c00db-109">节点集是按文档顺序创建的无重复节点的无序集合，可将其分配给样式表中的某个变量。</span><span class="sxs-lookup"><span data-stu-id="c00db-109">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span> <span data-ttu-id="c00db-110">此节点集是在转换中的 `select` 属性中使用的 XPath 表达式的结果，它与 XML 文档对象模型 (DOM) 中的节点集有相同的行为。</span><span class="sxs-lookup"><span data-stu-id="c00db-110">This node set, which is a result of an XPath expression used in a `select` attribute in a transformation, has the same behavior as a node set from the XML Document Object Model (DOM).</span></span> <span data-ttu-id="c00db-111">可以使用[使用 XPathNavigator 的节点集定位](node-set-navigation-using-xpathnavigator.md)中介绍的一组方法浏览节点集，与结果树片断不同，后者使用 <xref:System.Xml.XPath.XPathNodeIterator> 进行浏览。</span><span class="sxs-lookup"><span data-stu-id="c00db-111">You can navigate a node set using a set of methods shown in [Node Set Navigation Using XPathNavigator](node-set-navigation-using-xpathnavigator.md), unlike a result tree fragment or result tree fragment, which uses the <xref:System.Xml.XPath.XPathNodeIterator> for navigation.</span></span>  
  
 <span data-ttu-id="c00db-112">下面的代码示例显示了当样式表中的某个 `variable` 或 `parameter` 元素计算结果为节点集时如何循环访问节点集。</span><span class="sxs-lookup"><span data-stu-id="c00db-112">The following code sample shows how to iterate over a node set when a `variable` or `parameter` element in a style sheet evaluates to a node set.</span></span>  
  
## <a name="style-sheet"></a><span data-ttu-id="c00db-113">样式表</span><span class="sxs-lookup"><span data-stu-id="c00db-113">Style Sheet</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
  
    <xsl:variable name="x" select="bookstore/book/title"></xsl:variable>  
  
    <xsl:template match="/">  
        <xsl:for-each select="$x">  
            ******  
            <xsl:value-of select="."></xsl:value-of>  
            ******  
        </xsl:for-each>  
    </xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="input"></a><span data-ttu-id="c00db-114">输入</span><span class="sxs-lookup"><span data-stu-id="c00db-114">Input</span></span>  
  
```xml  
<bookstore>  
   <book style="autobiography">  
      <title>Seven Years in Trenton</title>  
   </book>  
  
   <book style="autobiography">  
      <title>Seven Years in Trenton2</title>  
   </book>  
  
   <book style="textbook">  
      <title>History of Trenton Vol 3</title>  
   </book>  
</bookstore>  
```  
  
## <a name="output"></a><span data-ttu-id="c00db-115">Output</span><span class="sxs-lookup"><span data-stu-id="c00db-115">Output</span></span>  
  
```output  
******  
Seven Years in Trenton  
******  
  
******  
Seven Years in Trenton2  
******  
  
******  
History of Trenton Vol 3  
******  
```  
  
## <a name="see-also"></a><span data-ttu-id="c00db-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="c00db-116">See also</span></span>

- <xref:System.Xml.XPath.XPathNodeIterator>
- [<span data-ttu-id="c00db-117">XslTransform 类的 XSLT 转换</span><span class="sxs-lookup"><span data-stu-id="c00db-117">XSLT Transformations with the XslTransform Class</span></span>](xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="c00db-118">XslTransform 类实现 XSLT 处理器</span><span class="sxs-lookup"><span data-stu-id="c00db-118">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)

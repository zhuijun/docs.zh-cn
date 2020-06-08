---
title: 对 msxsl:node-set() 函数的支持
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d0cbf517-d9f6-4097-9851-4fa62903decd
ms.openlocfilehash: 747a0ff8c155f7635d5a6d2ebc76f287cf8646d4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291443"
---
# <a name="support-for-the-msxslnode-set-function"></a><span data-ttu-id="d0886-102">对 msxsl:node-set() 函数的支持</span><span class="sxs-lookup"><span data-stu-id="d0886-102">Support for the msxsl:node-set() Function</span></span>
<span data-ttu-id="d0886-103">`msxsl:node-set` 函数使你能够将结果树片段转换成节点集。</span><span class="sxs-lookup"><span data-stu-id="d0886-103">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="d0886-104">生成的节点集总是包含单个节点并且是树的根节点。</span><span class="sxs-lookup"><span data-stu-id="d0886-104">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0886-105"><xref:System.Xml.Xsl.XslTransform> 类在 .NET Framework 2.0 中已过时。</span><span class="sxs-lookup"><span data-stu-id="d0886-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="d0886-106">可以使用 <xref:System.Xml.Xsl.XslCompiledTransform> 类执行可扩展样式表语言转换 (XSLT) 转换。</span><span class="sxs-lookup"><span data-stu-id="d0886-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="d0886-107">请参阅[使用 XslCompiledTransform 类](using-the-xslcompiledtransform-class.md)和[从 XslTransform 类迁移](migrating-from-the-xsltransform-class.md)，以获取详细信息。</span><span class="sxs-lookup"><span data-stu-id="d0886-107">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="d0886-108">`msxsl:node-set` 函数使你能够将结果树片段转换成节点集。</span><span class="sxs-lookup"><span data-stu-id="d0886-108">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="d0886-109">生成的节点集总是包含单个节点并且是树的根节点。</span><span class="sxs-lookup"><span data-stu-id="d0886-109">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0886-110">示例</span><span class="sxs-lookup"><span data-stu-id="d0886-110">Example</span></span>  
 <span data-ttu-id="d0886-111">在下面的示例中，`$var` 是一个变量，是样式表中的一个节点树。</span><span class="sxs-lookup"><span data-stu-id="d0886-111">In the following example, `$var` is a variable that is a node tree in the style sheet.</span></span> <span data-ttu-id="d0886-112">for-each 语句与 `node-set` 函数组合使用，允许用户将此节点树作为节点集循环访问。</span><span class="sxs-lookup"><span data-stu-id="d0886-112">The for-each statement combined with the `node-set` function allows the user to iterate over this node tree as a node set.</span></span>  
  
## <a name="nodesetxsl"></a><span data-ttu-id="d0886-113">nodeset.xsl</span><span class="sxs-lookup"><span data-stu-id="d0886-113">nodeset.xsl</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
                xmlns:user="http://www.contoso.com"  
                version="1.0">  
    <xsl:variable name="books">  
        <book author="Michael Howard">Writing Secure Code</book>  
        <book author="Michael Kay">XSLT Reference</book>  
    </xsl:variable>  
  
    <xsl:template match="/">  
        <authors>  
            <xsl:for-each select="msxsl:node-set($books)/book">
                <author><xsl:value-of select="@author"/></author>  
            </xsl:for-each>  
        </authors>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a><span data-ttu-id="d0886-114">Output</span><span class="sxs-lookup"><span data-stu-id="d0886-114">Output</span></span>  
 <span data-ttu-id="d0886-115">转换的输出为</span><span class="sxs-lookup"><span data-stu-id="d0886-115">The output of the transformation is</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<authors><author>Michael Howard</author><author>Michael Kay</author></authors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0886-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="d0886-116">See also</span></span>

- [<span data-ttu-id="d0886-117">XslTransform 类实现 XSLT 处理器</span><span class="sxs-lookup"><span data-stu-id="d0886-117">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)

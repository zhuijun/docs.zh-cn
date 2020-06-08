---
title: XslTransform 的 XmlDocument 输入
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 97115892-410a-4657-ab47-1e14dfba73f8
ms.openlocfilehash: e990c8ca3bb2a7145157fcedd06da4ea769c6ad3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290248"
---
# <a name="xmldocument-input-to-xsltransform"></a><span data-ttu-id="69b2c-102">XslTransform 的 XmlDocument 输入</span><span class="sxs-lookup"><span data-stu-id="69b2c-102">XmlDocument Input to XslTransform</span></span>
<span data-ttu-id="69b2c-103"><xref:System.Xml.XmlDocument> 类提供对 XML 文档的编辑功能。</span><span class="sxs-lookup"><span data-stu-id="69b2c-103">The <xref:System.Xml.XmlDocument> class provides editing capabilities for an XML document.</span></span> <span data-ttu-id="69b2c-104">如果 XML 在发送到 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法之前需要编辑或修改，请将 XML 加载到 <xref:System.Xml.XmlDocument> 中进行编辑，然后发送到 <xref:System.Xml.Xsl.XslTransform>。</span><span class="sxs-lookup"><span data-stu-id="69b2c-104">If the XML needs to be edited or modified before being sent to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, load the XML into an <xref:System.Xml.XmlDocument>, edit it, and send it in to the <xref:System.Xml.Xsl.XslTransform>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="69b2c-105"><xref:System.Xml.Xsl.XslTransform> 类在 .NET Framework 2.0 中已过时。</span><span class="sxs-lookup"><span data-stu-id="69b2c-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="69b2c-106">可以使用 <xref:System.Xml.Xsl.XslCompiledTransform> 类执行可扩展样式表语言转换 (XSLT) 转换。</span><span class="sxs-lookup"><span data-stu-id="69b2c-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="69b2c-107">请参阅[使用 XslCompiledTransform 类](using-the-xslcompiledtransform-class.md)和[从 XslTransform 类迁移](migrating-from-the-xsltransform-class.md)，以获取详细信息。</span><span class="sxs-lookup"><span data-stu-id="69b2c-107">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="69b2c-108"><xref:System.Xml.XmlDocument> 实现了 <xref:System.Xml.XPath.IXPathNavigable> 接口，所以，文档在编辑后可以传递给 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="69b2c-108">The <xref:System.Xml.XmlDocument> implements the <xref:System.Xml.XPath.IXPathNavigable> interface, so the document can be passed to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method after editing.</span></span>  
  
 <span data-ttu-id="69b2c-109">因为 <xref:System.Xml.XmlDocument> 的编辑功能，对于可扩展样式表语言转换 (XSLT) 转换，使用 <xref:System.Xml.XmlDocument> 类作为转换的输入比使用 <xref:System.Xml.XPath.XPathDocument> 速度要慢，因为 <xref:System.Xml.XPath.XPathDocument> 是内部存储，已针对 XML 路径语言 (XPath) 查询进行优化。</span><span class="sxs-lookup"><span data-stu-id="69b2c-109">Due to the editing capability of the <xref:System.Xml.XmlDocument>, using the <xref:System.Xml.XmlDocument> class as input to a transformation is slower than using an <xref:System.Xml.XPath.XPathDocument> for the Extensible Stylesheet Language for Transformations (XSLT) transformations, as the <xref:System.Xml.XPath.XPathDocument> is optimized for XML Path Language (XPath) queries due to the internal storage.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69b2c-110">示例</span><span class="sxs-lookup"><span data-stu-id="69b2c-110">Example</span></span>  
 <span data-ttu-id="69b2c-111">下面的代码示例显示如何将 <xref:System.Xml.XmlDocument> 提供给 <xref:System.Xml.Xsl.XslTransform>，同时将输出发送到 <xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="69b2c-111">The following code example shows how an <xref:System.Xml.XmlDocument> can be supplied to the <xref:System.Xml.Xsl.XslTransform>, with the output sent to an <xref:System.Xml.XmlReader>.</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.Load("books.xml")  
Dim trans As XslTransform = new XslTransform()  
trans.Load("book.xsl")  
Dim rdr As XmlReader = trans.Transform(doc, Nothing, Nothing)  
while (rdr.Read())  
end while  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.Load("books.xml");  
XslTransform trans = new XslTransform();  
trans.Load("book.xsl");  
XmlReader rdr = trans.Transform(doc, null, null);  
while (rdr.Read()) {}  
```  
  
## <a name="see-also"></a><span data-ttu-id="69b2c-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="69b2c-112">See also</span></span>

- <xref:System.Xml.XmlDocument>
- [<span data-ttu-id="69b2c-113">XslTransform 类的 XSLT 转换</span><span class="sxs-lookup"><span data-stu-id="69b2c-113">XSLT Transformations with the XslTransform Class</span></span>](xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="69b2c-114">XslTransform 类实现 XSLT 处理器</span><span class="sxs-lookup"><span data-stu-id="69b2c-114">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
- [<span data-ttu-id="69b2c-115">转换中的 XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="69b2c-115">XPathNavigator in Transformations</span></span>](xpathnavigator-in-transformations.md)
- [<span data-ttu-id="69b2c-116">转换中的 XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="69b2c-116">XPathNodeIterator in Transformations</span></span>](xpathnodeiterator-in-transformations.md)
- [<span data-ttu-id="69b2c-117">XslTransform 的 XPathDocument 输入</span><span class="sxs-lookup"><span data-stu-id="69b2c-117">XPathDocument Input to XslTransform</span></span>](xpathdocument-input-to-xsltransform.md)
- [<span data-ttu-id="69b2c-118">XslTransform 的 XmlDataDocument 输入</span><span class="sxs-lookup"><span data-stu-id="69b2c-118">XmlDataDocument Input to XslTransform</span></span>](xmldatadocument-input-to-xsltransform.md)

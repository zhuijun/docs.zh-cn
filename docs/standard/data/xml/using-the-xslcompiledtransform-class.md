---
title: 使用 XslCompiledTransform 类
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
ms.openlocfilehash: b9d14a79347610abcd2f770488acb53218ce3e46
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556767"
---
# <a name="using-the-xslcompiledtransform-class"></a><span data-ttu-id="ed551-102">使用 XslCompiledTransform 类</span><span class="sxs-lookup"><span data-stu-id="ed551-102">Using the XslCompiledTransform Class</span></span>
<span data-ttu-id="ed551-103"><xref:System.Xml.Xsl.XslCompiledTransform> 类是 Microsoft .NET Framework XSLT 处理器。</span><span class="sxs-lookup"><span data-stu-id="ed551-103">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the Microsoft .NET Framework XSLT processor.</span></span> <span data-ttu-id="ed551-104">此类用于编译样式表并执行 XSLT 转换。</span><span class="sxs-lookup"><span data-stu-id="ed551-104">This class is used to compile style sheets and execute XSLT transformations.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ed551-105">尽管 <xref:System.Xml.Xsl.XslCompiledTransform> 类的总体性能优于 <xref:System.Xml.Xsl.XslTransform> 类，但在首次对转换调用时，<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> 类的 <xref:System.Xml.Xsl.XslCompiledTransform> 方法可能比 <xref:System.Xml.Xsl.XslTransform.Load%2A> 类的 <xref:System.Xml.Xsl.XslTransform> 方法慢。</span><span class="sxs-lookup"><span data-stu-id="ed551-105">Although the overall performance of the <xref:System.Xml.Xsl.XslCompiledTransform> class is better than the <xref:System.Xml.Xsl.XslTransform> class, the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslCompiledTransform> class might perform more slowly than the <xref:System.Xml.Xsl.XslTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslTransform> class the first time it is called on a transformation.</span></span> <span data-ttu-id="ed551-106">这是因为必须先编译 XSLT 文件，才能加载该文件。</span><span class="sxs-lookup"><span data-stu-id="ed551-106">This is because the XSLT file must be compiled before it is loaded.</span></span> <span data-ttu-id="ed551-107">有关详细信息，请参阅以下博客文章：[XslCompiledTransform Slower than XslTransform?](/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)（XslCompiledTransform 比 XslTransform 慢？）</span><span class="sxs-lookup"><span data-stu-id="ed551-107">For more information, see the following blog post: [XslCompiledTransform Slower than XslTransform?](/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ed551-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="ed551-108">In This Section</span></span>  
 [<span data-ttu-id="ed551-109">XslCompiledTransform 类的输入</span><span class="sxs-lookup"><span data-stu-id="ed551-109">Inputs to the XslCompiledTransform Class</span></span>](inputs-to-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="ed551-110">介绍可用的 XSLT 输入选项。</span><span class="sxs-lookup"><span data-stu-id="ed551-110">Describes the available XSLT input options.</span></span>  
  
 [<span data-ttu-id="ed551-111">XslCompiledTransform 类的输出选项</span><span class="sxs-lookup"><span data-stu-id="ed551-111">Output Options on the XslCompiledTransform Class</span></span>](output-options-on-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="ed551-112">介绍可用的 XSLT 输出选项。</span><span class="sxs-lookup"><span data-stu-id="ed551-112">Describes the available XSLT output options.</span></span>  
  
 [<span data-ttu-id="ed551-113">在 XSLT 处理期间解析外部资源</span><span class="sxs-lookup"><span data-stu-id="ed551-113">Resolving External Resources During XSLT Processing</span></span>](resolving-external-resources-during-xslt-processing.md)  
 <span data-ttu-id="ed551-114">讨论如何使用 <xref:System.Xml.XmlResolver> 类解析外部资源。</span><span class="sxs-lookup"><span data-stu-id="ed551-114">Discusses using the <xref:System.Xml.XmlResolver> class to resolve external resources.</span></span>  
  
 [<span data-ttu-id="ed551-115">扩展 XSLT 样式表</span><span class="sxs-lookup"><span data-stu-id="ed551-115">Extending XSLT Style Sheets</span></span>](extending-xslt-style-sheets.md)  
 <span data-ttu-id="ed551-116">讨论如何支持 XSLT 扩展。</span><span class="sxs-lookup"><span data-stu-id="ed551-116">Discusses how XSLT extensions are supported.</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="ed551-117">可恢复的 XSLT 错误</span><span class="sxs-lookup"><span data-stu-id="ed551-117">Recoverable XSLT Errors</span></span>](recoverable-xslt-errors.md)|<span data-ttu-id="ed551-118">列出万维网联合会 (W3C) XSLT 1.0 建议所允许的任意行为，并介绍如何通过 <xref:System.Xml.Xsl.XslCompiledTransform> 类处理这些行为。</span><span class="sxs-lookup"><span data-stu-id="ed551-118">Lists discretionary behaviors allowed by the World Wide Web Consortium (W3C) XSLT 1.0 recommendation and describes how these behaviors are handled by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>|  
|[<span data-ttu-id="ed551-119">如何：转换节点片断</span><span class="sxs-lookup"><span data-stu-id="ed551-119">How to: Transform a Node Fragment</span></span>](how-to-transform-a-node-fragment.md)|<span data-ttu-id="ed551-120">介绍如何转换节点片断。</span><span class="sxs-lookup"><span data-stu-id="ed551-120">Describes how to transform a node fragment.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="ed551-121">相关章节</span><span class="sxs-lookup"><span data-stu-id="ed551-121">Related Sections</span></span>  
 [<span data-ttu-id="ed551-122">从 XslTransform 类迁移</span><span class="sxs-lookup"><span data-stu-id="ed551-122">Migrating From the XslTransform Class</span></span>](migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="ed551-123">讨论如何从 <xref:System.Xml.Xsl.XslTransform> 类迁移代码。</span><span class="sxs-lookup"><span data-stu-id="ed551-123">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed551-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="ed551-124">See also</span></span>

- <xref:System.Xml.Xsl.XsltSettings>
- <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>

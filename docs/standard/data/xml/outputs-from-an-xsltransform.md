---
title: XslTransform 的输出
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
ms.openlocfilehash: 5fa8c8228382f7f326a8d2243ed0450fca31f6fb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288688"
---
# <a name="outputs-from-an-xsltransform"></a><span data-ttu-id="aca8c-102">XslTransform 的输出</span><span class="sxs-lookup"><span data-stu-id="aca8c-102">Outputs from an XslTransform</span></span>
<span data-ttu-id="aca8c-103">样式表可以结合使用 `<xsl:output>` 语句和 `method` 属性来确定输出格式，下表说明了使用 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法写入输出并将输出格式声明为 <xref:System.IO.Stream> 或 <xref:System.IO.TextWriter> 时的输出格式。</span><span class="sxs-lookup"><span data-stu-id="aca8c-103">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aca8c-104"><xref:System.Xml.Xsl.XslTransform> 类在 .NET Framework 2.0 中已过时。</span><span class="sxs-lookup"><span data-stu-id="aca8c-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="aca8c-105">可以使用 <xref:System.Xml.Xsl.XslCompiledTransform> 类执行可扩展样式表语言转换 (XSLT) 转换。</span><span class="sxs-lookup"><span data-stu-id="aca8c-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="aca8c-106">请参阅[使用 XslCompiledTransform 类](using-the-xslcompiledtransform-class.md)和[从 XslTransform 类迁移](migrating-from-the-xsltransform-class.md)，以获取详细信息。</span><span class="sxs-lookup"><span data-stu-id="aca8c-106">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="aca8c-107">样式表可以结合使用 `<xsl:output>` 语句和 `method` 属性来确定输出格式，下表说明了使用 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法写入输出并将输出格式声明为 <xref:System.IO.Stream> 或 <xref:System.IO.TextWriter> 时的输出格式。</span><span class="sxs-lookup"><span data-stu-id="aca8c-107">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="aca8c-108">下表说明了结合使用 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法和 `<xsl:output>` 语句来声明输出类型时的结果：</span><span class="sxs-lookup"><span data-stu-id="aca8c-108">The following table describes what happens when an output type is declared by the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method in conjunction with the use of an `<xsl:output>` statement:</span></span>  
  
|<span data-ttu-id="aca8c-109">\<xsl:output method = > 特性</span><span class="sxs-lookup"><span data-stu-id="aca8c-109">\<xsl:output method = > attribute</span></span>|<span data-ttu-id="aca8c-110">结果格式</span><span class="sxs-lookup"><span data-stu-id="aca8c-110">Result format</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="aca8c-111">method="xml"</span><span class="sxs-lookup"><span data-stu-id="aca8c-111">method="xml"</span></span>|<span data-ttu-id="aca8c-112">XML</span><span class="sxs-lookup"><span data-stu-id="aca8c-112">XML</span></span>|  
|<span data-ttu-id="aca8c-113">method="html"</span><span class="sxs-lookup"><span data-stu-id="aca8c-113">method="html"</span></span>|<span data-ttu-id="aca8c-114">HTML</span><span class="sxs-lookup"><span data-stu-id="aca8c-114">HTML</span></span>|  
|<span data-ttu-id="aca8c-115">method="text"</span><span class="sxs-lookup"><span data-stu-id="aca8c-115">method="text"</span></span>|<span data-ttu-id="aca8c-116">Text</span><span class="sxs-lookup"><span data-stu-id="aca8c-116">Text</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="aca8c-117">注意：当 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法的输出为 <xref:System.Xml.XmlReader> 或 <xref:System.Xml.XmlWriter> 时，将忽略 `<xsl:output>` 语句。</span><span class="sxs-lookup"><span data-stu-id="aca8c-117">Note: The `<xsl:output>` statement is ignored when the output of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="aca8c-118">如果 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法的输出为 <xref:System.IO.Stream> 或 <xref:System.IO.TextWriter>，将支持下列属性：</span><span class="sxs-lookup"><span data-stu-id="aca8c-118">The following attributes are supported when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>:</span></span>  
  
- <span data-ttu-id="aca8c-119">encoding\*</span><span class="sxs-lookup"><span data-stu-id="aca8c-119">encoding\*</span></span>  
  
- <span data-ttu-id="aca8c-120">omit-xml-declaration</span><span class="sxs-lookup"><span data-stu-id="aca8c-120">omit-xml-declaration</span></span>  
  
- <span data-ttu-id="aca8c-121">独立</span><span class="sxs-lookup"><span data-stu-id="aca8c-121">standalone</span></span>  
  
- <span data-ttu-id="aca8c-122">doctype-public</span><span class="sxs-lookup"><span data-stu-id="aca8c-122">doctype-public</span></span>  
  
- <span data-ttu-id="aca8c-123">doctype-system</span><span class="sxs-lookup"><span data-stu-id="aca8c-123">doctype-system</span></span>  
  
- <span data-ttu-id="aca8c-124">cdata-section-elements</span><span class="sxs-lookup"><span data-stu-id="aca8c-124">cdata-section-elements</span></span>  
  
- <span data-ttu-id="aca8c-125">indent</span><span class="sxs-lookup"><span data-stu-id="aca8c-125">indent</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="aca8c-126">\*如果 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法将其输出发送到 <xref:System.IO.TextWriter>，将忽略 encoding 属性。</span><span class="sxs-lookup"><span data-stu-id="aca8c-126">\*The encoding attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is sending its output to a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="aca8c-127">而是改用 <xref:System.IO.TextWriter> 的 encoding 属性。</span><span class="sxs-lookup"><span data-stu-id="aca8c-127">The encoding property on the <xref:System.IO.TextWriter> is used instead.</span></span>
  
 <span data-ttu-id="aca8c-128">如果 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法的输出为 <xref:System.IO.Stream> 时，将忽略下列属性：</span><span class="sxs-lookup"><span data-stu-id="aca8c-128">The following attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream>:</span></span>  
  
- <span data-ttu-id="aca8c-129">version：版本始终为 1.0</span><span class="sxs-lookup"><span data-stu-id="aca8c-129">version: the version is always 1.0</span></span>  
  
- <span data-ttu-id="aca8c-130">media-type：媒体类型</span><span class="sxs-lookup"><span data-stu-id="aca8c-130">media-type: the media-type</span></span>  
  
## <a name="escaping-special-characters"></a><span data-ttu-id="aca8c-131">转义特殊字符</span><span class="sxs-lookup"><span data-stu-id="aca8c-131">Escaping Special Characters</span></span>  
 <span data-ttu-id="aca8c-132">`<xsl:text disable-output-escaping>` 标记用于指示特殊字符是需要转义为 XML 形式（例如使用 `<&lt>` 替代 `"<"` 符号）还是保持现在的状态。</span><span class="sxs-lookup"><span data-stu-id="aca8c-132">The `<xsl:text disable-output-escaping>` tag is used to indicate whether or not special characters need to be escaped into an XML form (for example, using `<&lt>` in place of the `"<"` symbol) or left in the present condition.</span></span> <span data-ttu-id="aca8c-133">如果转换为 `disable-output-escaping` 或 <xref:System.Xml.XmlReader> 对象，将忽略 <xref:System.Xml.XmlWriter> 属性，对特殊字符没有影响。</span><span class="sxs-lookup"><span data-stu-id="aca8c-133">The `disable-output-escaping` attribute is ignored when transforming to an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter> object and has no effect on special characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aca8c-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="aca8c-134">See also</span></span>

- [<span data-ttu-id="aca8c-135">XslTransform 类实现 XSLT 处理器</span><span class="sxs-lookup"><span data-stu-id="aca8c-135">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)

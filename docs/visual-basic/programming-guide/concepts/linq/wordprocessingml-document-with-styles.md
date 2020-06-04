---
title: 带有 Styles2 的 WordprocessingML 文档
ms.date: 07/20/2015
ms.assetid: a9136e4d-c368-4661-8049-7d45c679a236
ms.openlocfilehash: caf80014077bf57dc1ffb8eaeac6390cf4258015
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403545"
---
# <a name="wordprocessingml-document-with-styles"></a><span data-ttu-id="5123b-102">具有样式的 WordprocessingML 文档</span><span class="sxs-lookup"><span data-stu-id="5123b-102">WordprocessingML Document with Styles</span></span>
<span data-ttu-id="5123b-103">较为复杂的 WordprocessingML 文档具有使用样式格式的段落。</span><span class="sxs-lookup"><span data-stu-id="5123b-103">More complicated WordprocessingML documents have paragraphs that are formatted with styles.</span></span>  
  
 <span data-ttu-id="5123b-104">对 WordprocessingML 文档的结构做一些注释是很有帮助的。</span><span class="sxs-lookup"><span data-stu-id="5123b-104">A few notes about the makeup of WordprocessingML documents are helpful.</span></span> <span data-ttu-id="5123b-105">WordprocessingML 文档存储在包中。</span><span class="sxs-lookup"><span data-stu-id="5123b-105">WordprocessingML documents are stored in packages.</span></span> <span data-ttu-id="5123b-106">包具有多个部分（“部分”在包上下文中具有明确的意义，部分实质上是压缩在一起组成包的多个文件）。</span><span class="sxs-lookup"><span data-stu-id="5123b-106">Packages have multiple parts (parts have an explicit meaning when used in the context of packages; essentially, parts are files that are zipped together to comprise a package).</span></span> <span data-ttu-id="5123b-107">如果一个文档包含使用样式格式的段落，将会有一个文档部分包含应用了样式的段落。</span><span class="sxs-lookup"><span data-stu-id="5123b-107">If a document contains paragraphs that are formatted with styles, there will be a document part that contains paragraphs that have styles applied to them.</span></span> <span data-ttu-id="5123b-108">还会有一个样式部分包含文档引用的样式。</span><span class="sxs-lookup"><span data-stu-id="5123b-108">There will also be a style part that contains the styles that are referred to by the document.</span></span>  
  
 <span data-ttu-id="5123b-109">访问包时，重要的是通过部分之间的关系来访问包，而不是使用任意路径来访问包。</span><span class="sxs-lookup"><span data-stu-id="5123b-109">When accessing packages, it is important that you do so through the relationships between parts, rather than using an arbitrary path.</span></span> <span data-ttu-id="5123b-110">此问题超出了在 WordprocessingML 文档教程中使用内容的范围，但是本教程包含的示例程序演示了正确的方法。</span><span class="sxs-lookup"><span data-stu-id="5123b-110">This issue is beyond the scope of the Manipulating Content in a WordprocessingML Document tutorial, but the example programs that are included in this tutorial demonstrate the correct approach.</span></span>  
  
## <a name="a-document-that-uses-styles"></a><span data-ttu-id="5123b-111">使用样式的文档</span><span class="sxs-lookup"><span data-stu-id="5123b-111">A Document that Uses Styles</span></span>  
 <span data-ttu-id="5123b-112">[WordprocessingML Documents （Visual Basic）](shape-of-wordprocessingml-documents.md)主题中提供的 WordML 示例是非常简单的文档。</span><span class="sxs-lookup"><span data-stu-id="5123b-112">The WordML example presented in the [Shape of WordprocessingML Documents (Visual Basic)](shape-of-wordprocessingml-documents.md) topic is a very simple one.</span></span> <span data-ttu-id="5123b-113">下面的文档则更为复杂：它具有使用样式格式的段落。</span><span class="sxs-lookup"><span data-stu-id="5123b-113">The following document is more complicated: It has paragraphs that are formatted with styles.</span></span> <span data-ttu-id="5123b-114">若要查看构成 Office Open XML 文档的 XML，最简单的方法是运行[输出 Office OPEN Xml 文档部件的示例（Visual Basic）](example-that-outputs-office-open-xml-document-parts.md)。</span><span class="sxs-lookup"><span data-stu-id="5123b-114">The easiest way to see the XML that makes up an Office Open XML document is to run the [Example that Outputs Office Open XML Document Parts (Visual Basic)](example-that-outputs-office-open-xml-document-parts.md).</span></span>  
  
 <span data-ttu-id="5123b-115">在下面的文档中，第一段具有 `Heading1` 样式。</span><span class="sxs-lookup"><span data-stu-id="5123b-115">In the following document, the first paragraph has the style `Heading1`.</span></span> <span data-ttu-id="5123b-116">很多段落具有默认样式。</span><span class="sxs-lookup"><span data-stu-id="5123b-116">There are a number of paragraphs that have the default style.</span></span> <span data-ttu-id="5123b-117">还有一些段落具有 `Code` 样式。</span><span class="sxs-lookup"><span data-stu-id="5123b-117">There are also a number of paragraphs that have the style `Code`.</span></span> <span data-ttu-id="5123b-118">由于这种相对复杂性，这个文档更值得使用 LINQ to XML 来解析。</span><span class="sxs-lookup"><span data-stu-id="5123b-118">Because of this relative complexity, this is a more interesting document to parse with LINQ to XML.</span></span>  
  
 <span data-ttu-id="5123b-119">在那些使用非默认样式的段落中，段落元素具有名为 `w:pPr` 的子元素，该子元素又具有子元素 `w:pStyle`。</span><span class="sxs-lookup"><span data-stu-id="5123b-119">In those paragraphs with non-default styles, the paragraph elements have a child element named `w:pPr`, which in turn has a child element `w:pStyle`.</span></span> <span data-ttu-id="5123b-120">该元素具有属性 `w:val`，该属性包含样式名称。</span><span class="sxs-lookup"><span data-stu-id="5123b-120">That element has an attribute, `w:val`, which contains the style name.</span></span> <span data-ttu-id="5123b-121">如果段落具有默认样式，则意味着段落元素不具有 `w:p.Pr` 子元素。</span><span class="sxs-lookup"><span data-stu-id="5123b-121">If the paragraph has the default style, it means that the paragraph element does not have a `w:p.Pr` child element.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<w:document  
    xmlns:ve="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    xmlns:o="urn:schemas-microsoft-com:office:office"  
    xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"  
    xmlns:m="http://schemas.openxmlformats.org/officeDocument/2006/math"  
    xmlns:v="urn:schemas-microsoft-com:vml"  
    xmlns:wp="http://schemas.openxmlformats.org/drawingml/2006/wordprocessingDrawing"  
    xmlns:w10="urn:schemas-microsoft-com:office:word"  
    xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
    xmlns:wne="http://schemas.microsoft.com/office/word/2006/wordml">  
  <w:body>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Heading1" />  
      </w:pPr>  
      <w:r>  
        <w:t>Parsing WordprocessingML with LINQ to XML</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0">  
      <w:r>  
        <w:t>The following example prints to the console.</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r>  
        <w:t>using System;</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t>class Program {</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t xml:space="preserve">    public static void </w:t>  
      </w:r>  
      <w:smartTag w:uri="urn:schemas-microsoft-com:office:smarttags" w:element="place">  
        <w:r w:rsidRPr="00876F34">  
          <w:t>Main</w:t>  
        </w:r>  
      </w:smartTag>  
      <w:r w:rsidRPr="00876F34">  
        <w:t>(string[] args) {</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t xml:space="preserve">        Console.WriteLine("Hello World");</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t xml:space="preserve">    }</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t>}</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0">  
      <w:r>  
        <w:t>This example produces the following output:</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r>  
        <w:t>Hello World</w:t>  
      </w:r>  
    </w:p>  
    <w:sectPr w:rsidR="00A75AE0" w:rsidSect="00A75AE0">  
      <w:pgSz w:w="12240" w:h="15840" />  
      <w:pgMar w:top="1440" w:right="1800" w:bottom="1440" w:left="1800" w:header="720" w:footer="720" w:gutter="0" />  
      <w:cols w:space="720" />  
      <w:docGrid w:linePitch="360" />  
    </w:sectPr>  
  </w:body>  
</w:document>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5123b-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5123b-122">See also</span></span>

- [<span data-ttu-id="5123b-123">Office Open XML WordprocessingML 文档的详细信息（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="5123b-123">Details of Office Open XML WordprocessingML Documents (Visual Basic)</span></span>](details-of-office-open-xml-wordprocessingml-documents.md)

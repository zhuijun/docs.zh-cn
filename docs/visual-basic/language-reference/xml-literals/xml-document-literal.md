---
title: XML 文档文本
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
ms.openlocfilehash: bd1b2f43fce563af431d67b3817b05c7c1048314
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866021"
---
# <a name="xml-document-literal-visual-basic"></a><span data-ttu-id="1616d-102">XML 文档文本 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1616d-102">XML Document Literal (Visual Basic)</span></span>

<span data-ttu-id="1616d-103">表示对象的文本 <xref:System.Xml.Linq.XDocument> 。</span><span class="sxs-lookup"><span data-stu-id="1616d-103">A literal representing an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1616d-104">语法</span><span class="sxs-lookup"><span data-stu-id="1616d-104">Syntax</span></span>  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a><span data-ttu-id="1616d-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="1616d-105">Parts</span></span>  
  
|<span data-ttu-id="1616d-106">术语</span><span class="sxs-lookup"><span data-stu-id="1616d-106">Term</span></span>|<span data-ttu-id="1616d-107">定义</span><span class="sxs-lookup"><span data-stu-id="1616d-107">Definition</span></span>|  
|---|---|  
|`encoding`|<span data-ttu-id="1616d-108">可选。</span><span class="sxs-lookup"><span data-stu-id="1616d-108">Optional.</span></span> <span data-ttu-id="1616d-109">声明文档使用的编码的文本文本。</span><span class="sxs-lookup"><span data-stu-id="1616d-109">Literal text declaring which encoding the document uses.</span></span>|  
|`standalone`|<span data-ttu-id="1616d-110">可选。</span><span class="sxs-lookup"><span data-stu-id="1616d-110">Optional.</span></span> <span data-ttu-id="1616d-111">文本。</span><span class="sxs-lookup"><span data-stu-id="1616d-111">Literal text.</span></span> <span data-ttu-id="1616d-112">必须是 "是" 或 "否"。</span><span class="sxs-lookup"><span data-stu-id="1616d-112">Must be "yes" or "no".</span></span>|  
|`piCommentList`|<span data-ttu-id="1616d-113">可选。</span><span class="sxs-lookup"><span data-stu-id="1616d-113">Optional.</span></span> <span data-ttu-id="1616d-114">XML 处理指令和 XML 注释的列表。</span><span class="sxs-lookup"><span data-stu-id="1616d-114">List of XML processing instructions and XML comments.</span></span> <span data-ttu-id="1616d-115">采用以下格式：</span><span class="sxs-lookup"><span data-stu-id="1616d-115">Takes the following format:</span></span><br /><br /> <span data-ttu-id="1616d-116">`piComment [` `piComment` `... ]`</span><span class="sxs-lookup"><span data-stu-id="1616d-116">`piComment [` `piComment` `... ]`</span></span><br /><br /> <span data-ttu-id="1616d-117">每个 `piComment` 可以是以下各项之一：</span><span class="sxs-lookup"><span data-stu-id="1616d-117">Each `piComment` can be one of the following:</span></span><br /><br /> <span data-ttu-id="1616d-118">-   [XML 处理指令文本](xml-processing-instruction-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="1616d-118">-   [XML Processing Instruction Literal](xml-processing-instruction-literal.md).</span></span><br /><span data-ttu-id="1616d-119">-   [XML 注释文本](xml-comment-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="1616d-119">-   [XML Comment Literal](xml-comment-literal.md).</span></span>|  
|`rootElement`|<span data-ttu-id="1616d-120">必需。</span><span class="sxs-lookup"><span data-stu-id="1616d-120">Required.</span></span> <span data-ttu-id="1616d-121">文档的根元素。</span><span class="sxs-lookup"><span data-stu-id="1616d-121">Root element of the document.</span></span> <span data-ttu-id="1616d-122">格式为以下格式之一：</span><span class="sxs-lookup"><span data-stu-id="1616d-122">The format is one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="1616d-123">[XML 元素文本](xml-element-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="1616d-123">[XML Element Literal](xml-element-literal.md).</span></span></li><li><span data-ttu-id="1616d-124">窗体的嵌入式表达式 `<%=` `elementExp` `%>` 。</span><span class="sxs-lookup"><span data-stu-id="1616d-124">Embedded expression of the form `<%=` `elementExp` `%>`.</span></span> <span data-ttu-id="1616d-125">`elementExp`返回以下内容之一：</span><span class="sxs-lookup"><span data-stu-id="1616d-125">The `elementExp` returns one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="1616d-126">一个 <xref:System.Xml.Linq.XElement> 对象。</span><span class="sxs-lookup"><span data-stu-id="1616d-126">An <xref:System.Xml.Linq.XElement> object.</span></span></li><li><span data-ttu-id="1616d-127">一个集合，其中包含一个 <xref:System.Xml.Linq.XElement> 对象和任意数量的 <xref:System.Xml.Linq.XProcessingInstruction> 和 <xref:System.Xml.Linq.XComment> 对象。</span><span class="sxs-lookup"><span data-stu-id="1616d-127">A collection that contains one <xref:System.Xml.Linq.XElement> object and any number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects.</span></span></li></ul></li></ul><br /> <span data-ttu-id="1616d-128">有关详细信息，请参阅 [XML 中的嵌入式表达式](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="1616d-128">For more information, see [Embedded Expressions in XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="1616d-129">返回值</span><span class="sxs-lookup"><span data-stu-id="1616d-129">Return Value</span></span>  

 <span data-ttu-id="1616d-130">一个 <xref:System.Xml.Linq.XDocument> 对象。</span><span class="sxs-lookup"><span data-stu-id="1616d-130">An <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1616d-131">备注</span><span class="sxs-lookup"><span data-stu-id="1616d-131">Remarks</span></span>  

 <span data-ttu-id="1616d-132">XML 文档文本由文本开头的 XML 声明标识。</span><span class="sxs-lookup"><span data-stu-id="1616d-132">An XML document literal is identified by the XML declaration at the start of the literal.</span></span> <span data-ttu-id="1616d-133">虽然每个 XML 文档文本必须只有一个根 XML 元素，但是它可以有任意数量的 XML 处理指令和 XML 注释。</span><span class="sxs-lookup"><span data-stu-id="1616d-133">Although each XML document literal must have exactly one root XML element, it can have any number of XML processing instructions and XML comments.</span></span>  
  
 <span data-ttu-id="1616d-134">Xml 文档文字不能出现在 XML 元素中。</span><span class="sxs-lookup"><span data-stu-id="1616d-134">An XML document literal cannot appear in an XML element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1616d-135">XML 文本可以跨多行，而无需使用行继续符。</span><span class="sxs-lookup"><span data-stu-id="1616d-135">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="1616d-136">这使你可以从 XML 文档复制内容并将其直接粘贴到 Visual Basic 程序。</span><span class="sxs-lookup"><span data-stu-id="1616d-136">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="1616d-137">Visual Basic 编译器将 XML 文档文本转换为对 <xref:System.Xml.Linq.XDocument.%23ctor%2A> 和 <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> 构造函数的调用。</span><span class="sxs-lookup"><span data-stu-id="1616d-137">The Visual Basic compiler converts the XML document literal into calls to the <xref:System.Xml.Linq.XDocument.%23ctor%2A> and <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> constructors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1616d-138">示例</span><span class="sxs-lookup"><span data-stu-id="1616d-138">Example</span></span>  

 <span data-ttu-id="1616d-139">下面的示例创建一个 XML 文档，该文档具有 XML 声明、处理指令、注释以及包含其他元素的元素。</span><span class="sxs-lookup"><span data-stu-id="1616d-139">The following example creates an XML document that has an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
 [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="1616d-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1616d-140">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XDocument>
- [<span data-ttu-id="1616d-141">XML 处理指令文本</span><span class="sxs-lookup"><span data-stu-id="1616d-141">XML Processing Instruction Literal</span></span>](xml-processing-instruction-literal.md)
- [<span data-ttu-id="1616d-142">XML 注释文本</span><span class="sxs-lookup"><span data-stu-id="1616d-142">XML Comment Literal</span></span>](xml-comment-literal.md)
- [<span data-ttu-id="1616d-143">XML 元素文本</span><span class="sxs-lookup"><span data-stu-id="1616d-143">XML Element Literal</span></span>](xml-element-literal.md)
- [<span data-ttu-id="1616d-144">XML 文本</span><span class="sxs-lookup"><span data-stu-id="1616d-144">XML Literals</span></span>](index.md)
- [<span data-ttu-id="1616d-145">在 Visual Basic 中创建 XML</span><span class="sxs-lookup"><span data-stu-id="1616d-145">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="1616d-146">XML 中的嵌入式表达式</span><span class="sxs-lookup"><span data-stu-id="1616d-146">Embedded Expressions in XML</span></span>](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)

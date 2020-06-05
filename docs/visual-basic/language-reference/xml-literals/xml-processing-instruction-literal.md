---
title: XML 处理指令文本
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
ms.openlocfilehash: 9bd1781e01bc4cbf1ce5da8c454ab2f5a679aead
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400171"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a><span data-ttu-id="20a8b-102">XML 处理指令文本 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20a8b-102">XML Processing Instruction Literal (Visual Basic)</span></span>
<span data-ttu-id="20a8b-103">表示对象的文本 <xref:System.Xml.Linq.XProcessingInstruction> 。</span><span class="sxs-lookup"><span data-stu-id="20a8b-103">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20a8b-104">语法</span><span class="sxs-lookup"><span data-stu-id="20a8b-104">Syntax</span></span>  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a><span data-ttu-id="20a8b-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="20a8b-105">Parts</span></span>  
 `<?`  
 <span data-ttu-id="20a8b-106">必需。</span><span class="sxs-lookup"><span data-stu-id="20a8b-106">Required.</span></span> <span data-ttu-id="20a8b-107">表示 XML 处理指令文本的开头。</span><span class="sxs-lookup"><span data-stu-id="20a8b-107">Denotes the start of the XML processing instruction literal.</span></span>  
  
 `piName`  
 <span data-ttu-id="20a8b-108">必需。</span><span class="sxs-lookup"><span data-stu-id="20a8b-108">Required.</span></span> <span data-ttu-id="20a8b-109">指示处理指令的目标应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="20a8b-109">Name indicating which application the processing instruction targets.</span></span> <span data-ttu-id="20a8b-110">不能以 "xml" 或 "XML" 开头。</span><span class="sxs-lookup"><span data-stu-id="20a8b-110">Cannot begin with "xml" or "XML".</span></span>  
  
 `piData`  
 <span data-ttu-id="20a8b-111">可选。</span><span class="sxs-lookup"><span data-stu-id="20a8b-111">Optional.</span></span> <span data-ttu-id="20a8b-112">字符串，指示的目标应用程序 `piName` 应如何处理 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="20a8b-112">String indicating how the application targeted by `piName` should process the XML document.</span></span>  
  
 `?>`  
 <span data-ttu-id="20a8b-113">必需。</span><span class="sxs-lookup"><span data-stu-id="20a8b-113">Required.</span></span> <span data-ttu-id="20a8b-114">表示处理指令的结束。</span><span class="sxs-lookup"><span data-stu-id="20a8b-114">Denotes the end of the processing instruction.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20a8b-115">返回值</span><span class="sxs-lookup"><span data-stu-id="20a8b-115">Return Value</span></span>  
 <span data-ttu-id="20a8b-116">一个 <xref:System.Xml.Linq.XProcessingInstruction> 对象。</span><span class="sxs-lookup"><span data-stu-id="20a8b-116">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20a8b-117">备注</span><span class="sxs-lookup"><span data-stu-id="20a8b-117">Remarks</span></span>  
 <span data-ttu-id="20a8b-118">XML 处理指令文本指示应用程序应如何处理 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="20a8b-118">XML processing instruction literals indicate how applications should process an XML document.</span></span> <span data-ttu-id="20a8b-119">当应用程序加载 XML 文档时，应用程序可以检查 XML 处理指令以确定如何处理文档。</span><span class="sxs-lookup"><span data-stu-id="20a8b-119">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span></span> <span data-ttu-id="20a8b-120">应用程序解释和的含义 `piName` `piData` 。</span><span class="sxs-lookup"><span data-stu-id="20a8b-120">The application interprets the meaning of `piName` and `piData`.</span></span>  
  
 <span data-ttu-id="20a8b-121">XML 文档文本使用类似于 XML 处理指令的语法。</span><span class="sxs-lookup"><span data-stu-id="20a8b-121">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span></span> <span data-ttu-id="20a8b-122">有关详细信息，请参阅[XML 文档文本](xml-document-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="20a8b-122">For more information, see [XML Document Literal](xml-document-literal.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="20a8b-123">`piName`元素不能以字符串 "xml" 或 "xml" 开头，因为 xml 1.0 规范保留这些标识符。</span><span class="sxs-lookup"><span data-stu-id="20a8b-123">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span></span>  
  
 <span data-ttu-id="20a8b-124">可以将 XML 处理指令文本分配给变量或将其包含在 XML 文档文本中。</span><span class="sxs-lookup"><span data-stu-id="20a8b-124">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="20a8b-125">XML 文本可以跨多个行，而不需要行继续符。</span><span class="sxs-lookup"><span data-stu-id="20a8b-125">An XML literal can span multiple lines without needing line continuation characters.</span></span> <span data-ttu-id="20a8b-126">这使你可以从 XML 文档复制内容并将其直接粘贴到 Visual Basic 程序。</span><span class="sxs-lookup"><span data-stu-id="20a8b-126">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="20a8b-127">Visual Basic 编译器将 XML 处理指令文本转换为对构造函数的调用 <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> 。</span><span class="sxs-lookup"><span data-stu-id="20a8b-127">The Visual Basic compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20a8b-128">示例</span><span class="sxs-lookup"><span data-stu-id="20a8b-128">Example</span></span>  
 <span data-ttu-id="20a8b-129">下面的示例创建一个处理指令，该指令标识 XML 文档的样式表。</span><span class="sxs-lookup"><span data-stu-id="20a8b-129">The following example creates a processing instruction identifying a style-sheet for an XML document.</span></span>  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="20a8b-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="20a8b-130">See also</span></span>

- <xref:System.Xml.Linq.XProcessingInstruction>
- [<span data-ttu-id="20a8b-131">XML 文档文本</span><span class="sxs-lookup"><span data-stu-id="20a8b-131">XML Document Literal</span></span>](xml-document-literal.md)
- [<span data-ttu-id="20a8b-132">XML 文本</span><span class="sxs-lookup"><span data-stu-id="20a8b-132">XML Literals</span></span>](index.md)
- [<span data-ttu-id="20a8b-133">在 Visual Basic 中创建 XML</span><span class="sxs-lookup"><span data-stu-id="20a8b-133">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)

---
title: XML CDATA 文本
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
ms.openlocfilehash: 4447ad6cf0fb251b0d2d1387c109b06d32f69cb8
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866094"
---
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="7339a-102">XML CDATA 文本 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7339a-102">XML CDATA Literal (Visual Basic)</span></span>

<span data-ttu-id="7339a-103">表示对象的文本 <xref:System.Xml.Linq.XCData> 。</span><span class="sxs-lookup"><span data-stu-id="7339a-103">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7339a-104">语法</span><span class="sxs-lookup"><span data-stu-id="7339a-104">Syntax</span></span>  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="7339a-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="7339a-105">Parts</span></span>  

 `<![CDATA[`  
 <span data-ttu-id="7339a-106">必需。</span><span class="sxs-lookup"><span data-stu-id="7339a-106">Required.</span></span> <span data-ttu-id="7339a-107">表示 XML CDATA 部分的开头。</span><span class="sxs-lookup"><span data-stu-id="7339a-107">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="7339a-108">必需。</span><span class="sxs-lookup"><span data-stu-id="7339a-108">Required.</span></span> <span data-ttu-id="7339a-109">要显示在 XML CDATA 节中的文本内容。</span><span class="sxs-lookup"><span data-stu-id="7339a-109">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="7339a-110">必需。</span><span class="sxs-lookup"><span data-stu-id="7339a-110">Required.</span></span> <span data-ttu-id="7339a-111">表示部分的结尾。</span><span class="sxs-lookup"><span data-stu-id="7339a-111">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7339a-112">返回值</span><span class="sxs-lookup"><span data-stu-id="7339a-112">Return Value</span></span>  

 <span data-ttu-id="7339a-113">一个 <xref:System.Xml.Linq.XCData> 对象。</span><span class="sxs-lookup"><span data-stu-id="7339a-113">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7339a-114">备注</span><span class="sxs-lookup"><span data-stu-id="7339a-114">Remarks</span></span>  

 <span data-ttu-id="7339a-115">XML CDATA 节包含应包含的原始文本，但不应在包含它的 XML 中进行分析。</span><span class="sxs-lookup"><span data-stu-id="7339a-115">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="7339a-116">XML CDATA 节可以包含任何文本。</span><span class="sxs-lookup"><span data-stu-id="7339a-116">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="7339a-117">其中包括保留的 XML 字符。</span><span class="sxs-lookup"><span data-stu-id="7339a-117">This includes reserved XML characters.</span></span> <span data-ttu-id="7339a-118">XML CDATA 部分以序列 "]] 结尾 >"。</span><span class="sxs-lookup"><span data-stu-id="7339a-118">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="7339a-119">这意味着：</span><span class="sxs-lookup"><span data-stu-id="7339a-119">This implies the following points:</span></span>  
  
- <span data-ttu-id="7339a-120">不能在 XML CDATA 文本中使用嵌入式表达式，因为嵌入式表达式分隔符是有效的 XML CDATA 内容。</span><span class="sxs-lookup"><span data-stu-id="7339a-120">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
- <span data-ttu-id="7339a-121">XML CDATA 节不能嵌套，因为 `content` 不能包含值 "]] >"。</span><span class="sxs-lookup"><span data-stu-id="7339a-121">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="7339a-122">可以将 XML CDATA 文本分配给一个变量，也可以将其包含在 XML 元素文本中。</span><span class="sxs-lookup"><span data-stu-id="7339a-122">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7339a-123">XML 文本可以跨多行，但不使用行继续符。</span><span class="sxs-lookup"><span data-stu-id="7339a-123">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="7339a-124">这使你可以从 XML 文档复制内容并将其直接粘贴到 Visual Basic 程序。</span><span class="sxs-lookup"><span data-stu-id="7339a-124">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="7339a-125">Visual Basic 编译器会将 XML CDATA 文本转换为对 <xref:System.Xml.Linq.XCData.%23ctor%2A> 构造函数的调用。</span><span class="sxs-lookup"><span data-stu-id="7339a-125">The Visual Basic compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7339a-126">示例</span><span class="sxs-lookup"><span data-stu-id="7339a-126">Example</span></span>  

 <span data-ttu-id="7339a-127">下面的示例创建一个 CDATA 节，其中包含文本 "可以包含文本 \<XML> 标记"。</span><span class="sxs-lookup"><span data-stu-id="7339a-127">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="7339a-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7339a-128">See also</span></span>

- <xref:System.Xml.Linq.XCData>
- [<span data-ttu-id="7339a-129">XML 元素文本</span><span class="sxs-lookup"><span data-stu-id="7339a-129">XML Element Literal</span></span>](xml-element-literal.md)
- [<span data-ttu-id="7339a-130">XML 文本</span><span class="sxs-lookup"><span data-stu-id="7339a-130">XML Literals</span></span>](index.md)
- [<span data-ttu-id="7339a-131">在 Visual Basic 中创建 XML</span><span class="sxs-lookup"><span data-stu-id="7339a-131">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)

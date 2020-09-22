---
title: XML 注释文本
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
ms.openlocfilehash: 3272cc0f976d6e8819e51bb5d5fce73066007963
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875182"
---
# <a name="xml-comment-literal-visual-basic"></a><span data-ttu-id="0a0a0-102">XML 注释文本 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a0a0-102">XML Comment Literal (Visual Basic)</span></span>

<span data-ttu-id="0a0a0-103">表示对象的文本 <xref:System.Xml.Linq.XComment> 。</span><span class="sxs-lookup"><span data-stu-id="0a0a0-103">A literal representing an <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a0a0-104">语法</span><span class="sxs-lookup"><span data-stu-id="0a0a0-104">Syntax</span></span>  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a><span data-ttu-id="0a0a0-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="0a0a0-105">Parts</span></span>  
  
|<span data-ttu-id="0a0a0-106">术语</span><span class="sxs-lookup"><span data-stu-id="0a0a0-106">Term</span></span>|<span data-ttu-id="0a0a0-107">定义</span><span class="sxs-lookup"><span data-stu-id="0a0a0-107">Definition</span></span>|  
|---|---|  
|`<!--`|<span data-ttu-id="0a0a0-108">必需。</span><span class="sxs-lookup"><span data-stu-id="0a0a0-108">Required.</span></span> <span data-ttu-id="0a0a0-109">表示 XML 注释的开头。</span><span class="sxs-lookup"><span data-stu-id="0a0a0-109">Denotes the start of the XML comment.</span></span>|  
|`content`|<span data-ttu-id="0a0a0-110">必需。</span><span class="sxs-lookup"><span data-stu-id="0a0a0-110">Required.</span></span> <span data-ttu-id="0a0a0-111">要在 XML 注释中显示的文本。</span><span class="sxs-lookup"><span data-stu-id="0a0a0-111">Text to appear in the XML comment.</span></span> <span data-ttu-id="0a0a0-112">不能包含由两个连字符组成的序列 (--) 或以与结束标记相邻的连字符结尾。</span><span class="sxs-lookup"><span data-stu-id="0a0a0-112">Cannot contain a series of two hyphens (--) or end with a hyphen adjacent to the closing tag.</span></span>|  
|`-->`|<span data-ttu-id="0a0a0-113">必需。</span><span class="sxs-lookup"><span data-stu-id="0a0a0-113">Required.</span></span> <span data-ttu-id="0a0a0-114">表示 XML 注释的结尾。</span><span class="sxs-lookup"><span data-stu-id="0a0a0-114">Denotes the end of the XML comment.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="0a0a0-115">返回值</span><span class="sxs-lookup"><span data-stu-id="0a0a0-115">Return Value</span></span>  

 <span data-ttu-id="0a0a0-116">一个 <xref:System.Xml.Linq.XComment> 对象。</span><span class="sxs-lookup"><span data-stu-id="0a0a0-116">An <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a0a0-117">备注</span><span class="sxs-lookup"><span data-stu-id="0a0a0-117">Remarks</span></span>  

 <span data-ttu-id="0a0a0-118">XML 注释文本不包含文档内容;它们包含有关文档的信息。</span><span class="sxs-lookup"><span data-stu-id="0a0a0-118">XML comment literals do not contain document content; they contain information about the document.</span></span> <span data-ttu-id="0a0a0-119">XML 注释部分以序列 "-->" 结尾。</span><span class="sxs-lookup"><span data-stu-id="0a0a0-119">The XML comment section ends with the sequence "-->".</span></span> <span data-ttu-id="0a0a0-120">这意味着：</span><span class="sxs-lookup"><span data-stu-id="0a0a0-120">This implies the following points:</span></span>  
  
- <span data-ttu-id="0a0a0-121">不能在 XML 注释文本中使用嵌入表达式，因为嵌入式表达式分隔符是有效的 XML 注释内容。</span><span class="sxs-lookup"><span data-stu-id="0a0a0-121">You cannot use an embedded expression in an XML comment literal because the embedded expression delimiters are valid XML comment content.</span></span>  
  
- <span data-ttu-id="0a0a0-122">XML 注释部分不能嵌套，因为 `content` 不能包含值 "-->"。</span><span class="sxs-lookup"><span data-stu-id="0a0a0-122">XML comment sections cannot be nested, because `content` cannot contain the value "-->".</span></span>  
  
 <span data-ttu-id="0a0a0-123">可以将 XML 注释文本分配给一个变量，也可以将其包含在 XML 元素文本中。</span><span class="sxs-lookup"><span data-stu-id="0a0a0-123">You can assign an XML comment literal to a variable, or you can include it in an XML element literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0a0a0-124">XML 文本可以跨多行，而无需使用行继续符。</span><span class="sxs-lookup"><span data-stu-id="0a0a0-124">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="0a0a0-125">此功能使你能够从 XML 文档复制内容并将其直接粘贴到 Visual Basic 程序。</span><span class="sxs-lookup"><span data-stu-id="0a0a0-125">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="0a0a0-126">Visual Basic 编译器将 XML 注释文本转换为对构造函数的调用 <xref:System.Xml.Linq.XComment.%23ctor%2A> 。</span><span class="sxs-lookup"><span data-stu-id="0a0a0-126">The Visual Basic compiler converts the XML comment literal to a call to the <xref:System.Xml.Linq.XComment.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a0a0-127">示例</span><span class="sxs-lookup"><span data-stu-id="0a0a0-127">Example</span></span>  

 <span data-ttu-id="0a0a0-128">下面的示例创建一个包含文本 "This is a comment" 的 XML 注释。</span><span class="sxs-lookup"><span data-stu-id="0a0a0-128">The following example creates an XML comment that contains the text "This is a comment".</span></span>  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="0a0a0-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0a0a0-129">See also</span></span>

- <xref:System.Xml.Linq.XComment>
- [<span data-ttu-id="0a0a0-130">XML 元素文本</span><span class="sxs-lookup"><span data-stu-id="0a0a0-130">XML Element Literal</span></span>](xml-element-literal.md)
- [<span data-ttu-id="0a0a0-131">XML 文本</span><span class="sxs-lookup"><span data-stu-id="0a0a0-131">XML Literals</span></span>](index.md)
- [<span data-ttu-id="0a0a0-132">在 Visual Basic 中创建 XML</span><span class="sxs-lookup"><span data-stu-id="0a0a0-132">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)

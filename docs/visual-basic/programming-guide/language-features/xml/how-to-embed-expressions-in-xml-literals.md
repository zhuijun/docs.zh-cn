---
title: 如何：在 XML 文本中嵌入表达式
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 59ba03be6e132203523427d3b7af5a163b6f05ac
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392309"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a><span data-ttu-id="60dfb-102">如何：在 XML 文本中嵌入表达式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60dfb-102">How to: Embed Expressions in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="60dfb-103">可以结合使用 XML 文本和嵌入式表达式来创建 XML 文档、片段或元素，该元素包含在运行时创建的内容。</span><span class="sxs-lookup"><span data-stu-id="60dfb-103">You can combine XML literals with embedded expressions to create an XML document, fragment, or element that contains content created at run time.</span></span> <span data-ttu-id="60dfb-104">下面的示例演示如何在运行时使用嵌入式表达式填充元素内容、属性和元素名称。</span><span class="sxs-lookup"><span data-stu-id="60dfb-104">The following examples demonstrate how to use embedded expressions to populate element content, attributes, and element names at run time.</span></span>  
  
 <span data-ttu-id="60dfb-105">嵌入式表达式的语法是 `<%=` `exp` `%>` ，这与 ASP.NET 使用的语法相同。</span><span class="sxs-lookup"><span data-stu-id="60dfb-105">The syntax for an embedded expression is `<%=` `exp` `%>`, which is the same syntax that ASP.NET uses.</span></span> <span data-ttu-id="60dfb-106">有关详细信息，请参阅[XML 中的嵌入式表达式](embedded-expressions-in-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="60dfb-106">For more information, see [Embedded Expressions in XML](embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="60dfb-107">你还可以使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] api 来创建 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 对象。</span><span class="sxs-lookup"><span data-stu-id="60dfb-107">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="60dfb-108">有关详细信息，请参阅 <xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="60dfb-108">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="60dfb-109">过程</span><span class="sxs-lookup"><span data-stu-id="60dfb-109">Procedures</span></span>  
  
#### <a name="to-insert-text-as-element-content"></a><span data-ttu-id="60dfb-110">插入文本作为元素内容</span><span class="sxs-lookup"><span data-stu-id="60dfb-110">To insert text as element content</span></span>  
  
- <span data-ttu-id="60dfb-111">下面的示例演示如何在 `contactName` 开始和结束名称元素之间插入变量中包含的文本。</span><span class="sxs-lookup"><span data-stu-id="60dfb-111">The following example shows how to insert the text that is contained in the `contactName` variable between the opening and closing name elements.</span></span>  
  
     [!code-vb[VbXMLSamples#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#39)]  
  
     <span data-ttu-id="60dfb-112">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="60dfb-112">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a><span data-ttu-id="60dfb-113">插入文本作为属性值</span><span class="sxs-lookup"><span data-stu-id="60dfb-113">To insert text as an attribute value</span></span>  
  
- <span data-ttu-id="60dfb-114">下面的示例演示如何插入变量中包含的文本 `phoneType` 作为属性的值 `type` 。</span><span class="sxs-lookup"><span data-stu-id="60dfb-114">The following example shows how to insert the text that is contained in the `phoneType` variable as the value of the `type` attribute.</span></span>  
  
     [!code-vb[VbXMLSamples#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#40)]  
  
     <span data-ttu-id="60dfb-115">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="60dfb-115">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a><span data-ttu-id="60dfb-116">插入元素名称的文本</span><span class="sxs-lookup"><span data-stu-id="60dfb-116">To insert text for an element name</span></span>  
  
- <span data-ttu-id="60dfb-117">下面的示例演示如何插入变量中包含的文本 `elementName` 作为元素的名称。</span><span class="sxs-lookup"><span data-stu-id="60dfb-117">The following example shows how to insert the text that is contained in the `elementName` variable as the name of an element.</span></span>  
  
     <span data-ttu-id="60dfb-118">使用此方法创建元素时，必须使用标记将其关闭 \</> 。</span><span class="sxs-lookup"><span data-stu-id="60dfb-118">When creating elements by using this technique, you must close them with the \</> tag.</span></span>  
  
     [!code-vb[VbXMLSamples#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#41)]  
  
     <span data-ttu-id="60dfb-119">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="60dfb-119">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="60dfb-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="60dfb-120">See also</span></span>

- [<span data-ttu-id="60dfb-121">如何：创建 XML 文本</span><span class="sxs-lookup"><span data-stu-id="60dfb-121">How to: Create XML Literals</span></span>](how-to-create-xml-literals.md)
- [<span data-ttu-id="60dfb-122">XML 中的嵌入式表达式</span><span class="sxs-lookup"><span data-stu-id="60dfb-122">Embedded Expressions in XML</span></span>](embedded-expressions-in-xml.md)
- [<span data-ttu-id="60dfb-123">在 Visual Basic 中创建 XML</span><span class="sxs-lookup"><span data-stu-id="60dfb-123">Creating XML in Visual Basic</span></span>](creating-xml.md)
- [<span data-ttu-id="60dfb-124">XML</span><span class="sxs-lookup"><span data-stu-id="60dfb-124">XML</span></span>](index.md)

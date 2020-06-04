---
title: XML 文本中的空白
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: b3caf7ac052f3fed3fe5427da0cc96bbdd955ea6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360470"
---
# <a name="white-space-in-xml-literals-visual-basic"></a><span data-ttu-id="cea3b-102">XML 文本中的空白 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cea3b-102">White Space in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="cea3b-103">Visual Basic 编译器在创建对象时仅合并 XML 文本中的有效空白字符 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cea3b-103">The Visual Basic compiler incorporates only the significant white space characters from an XML literal when it creates a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object.</span></span> <span data-ttu-id="cea3b-104">不包含无意义的空白字符。</span><span class="sxs-lookup"><span data-stu-id="cea3b-104">The insignificant white space characters are not incorporated.</span></span>  
  
## <a name="significant-and-insignificant-white-space"></a><span data-ttu-id="cea3b-105">重要且无意义的空白</span><span class="sxs-lookup"><span data-stu-id="cea3b-105">Significant and Insignificant White Space</span></span>  
 <span data-ttu-id="cea3b-106">XML 文本中的空格字符仅在三个区域中很重要：</span><span class="sxs-lookup"><span data-stu-id="cea3b-106">White space characters in XML literals are significant in only three areas:</span></span>  
  
- <span data-ttu-id="cea3b-107">在属性值中。</span><span class="sxs-lookup"><span data-stu-id="cea3b-107">When they are in an attribute value.</span></span>  
  
- <span data-ttu-id="cea3b-108">当它们是元素的文本内容的一部分并且文本还包含其他字符时。</span><span class="sxs-lookup"><span data-stu-id="cea3b-108">When they are part of an element's text content and the text also contains other characters.</span></span>  
  
- <span data-ttu-id="cea3b-109">当它们位于元素的文本内容的嵌入式表达式中时。</span><span class="sxs-lookup"><span data-stu-id="cea3b-109">When they are in an embedded expression for an element's text content.</span></span>  
  
 <span data-ttu-id="cea3b-110">否则，编译器会将空白字符视为不重要的，并且不会在文本的对象中包括 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cea3b-110">Otherwise, the compiler treats white space characters as insignificant and does not include then in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object for the literal.</span></span>  
  
 <span data-ttu-id="cea3b-111">若要在 XML 文本中包含无意义的空白，请使用包含带有空格的字符串文字的嵌入式表达式。</span><span class="sxs-lookup"><span data-stu-id="cea3b-111">To include insignificant white space in an XML literal, use an embedded expression that contains a string literal with the white space.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cea3b-112">如果 `xml:space` 属性出现在 XML 元素文本中，则 Visual Basic 编译器在对象中包括属性 <xref:System.Xml.Linq.XElement> ，但添加此属性不会更改编译器处理空白的方式。</span><span class="sxs-lookup"><span data-stu-id="cea3b-112">If the `xml:space` attribute appears in an XML element literal, the Visual Basic compiler includes the attribute in the <xref:System.Xml.Linq.XElement> object, but adding this attribute does not change how the compiler treats white space.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="cea3b-113">示例</span><span class="sxs-lookup"><span data-stu-id="cea3b-113">Examples</span></span>  
 <span data-ttu-id="cea3b-114">下面的示例包含两个 XML 元素：外部和内部。</span><span class="sxs-lookup"><span data-stu-id="cea3b-114">The following example contains two XML elements, outer and inner.</span></span> <span data-ttu-id="cea3b-115">这两个元素在其文本内容中都包含空格。</span><span class="sxs-lookup"><span data-stu-id="cea3b-115">Both elements contain white space in their text content.</span></span> <span data-ttu-id="cea3b-116">外部元素中的空白是无意义的，因为它仅包含空格和 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="cea3b-116">The white space in the outer element is insignificant because it contains only white space and an XML element.</span></span> <span data-ttu-id="cea3b-117">内部元素中的空格非常重要，因为它包含空格和文本。</span><span class="sxs-lookup"><span data-stu-id="cea3b-117">The white space in the inner element is significant because it contains white space and text.</span></span>  
  
 [!code-vb[VbXMLSamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#29)]  
  
 <span data-ttu-id="cea3b-118">运行时，此代码显示以下文本。</span><span class="sxs-lookup"><span data-stu-id="cea3b-118">When run, this code displays the following text.</span></span>  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cea3b-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cea3b-119">See also</span></span>

- [<span data-ttu-id="cea3b-120">在 Visual Basic 中创建 XML</span><span class="sxs-lookup"><span data-stu-id="cea3b-120">Creating XML in Visual Basic</span></span>](creating-xml.md)

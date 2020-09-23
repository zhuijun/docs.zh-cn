---
title: 如何：访问 XML 子代元素
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: dcbaf1f9022d86f40a90ef6a1e0033f627caeef2
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058204"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a><span data-ttu-id="81f95-102">如何：访问 XML 后代元素 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81f95-102">How to: Access XML Descendant Elements (Visual Basic)</span></span>

<span data-ttu-id="81f95-103">此示例演示如何使用子代轴属性访问具有指定名称并包含在 XML 元素下的所有 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="81f95-103">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span></span> <span data-ttu-id="81f95-104">具体而言，它使用 `Value` 属性获取 `name` 子代轴属性返回的集合中第一个元素的值。</span><span class="sxs-lookup"><span data-stu-id="81f95-104">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span></span> <span data-ttu-id="81f95-105">`name`子代轴属性获取 `name` 对象中包含的所有名为的元素 `contacts` 。</span><span class="sxs-lookup"><span data-stu-id="81f95-105">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span></span> <span data-ttu-id="81f95-106">此示例还使用 `phone` 子代轴属性来访问 `phone` 对象中包含的所有名为的后代 `contacts` 。</span><span class="sxs-lookup"><span data-stu-id="81f95-106">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81f95-107">示例</span><span class="sxs-lookup"><span data-stu-id="81f95-107">Example</span></span>  

 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="81f95-108">编译代码</span><span class="sxs-lookup"><span data-stu-id="81f95-108">Compile the code</span></span>  

 <span data-ttu-id="81f95-109">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="81f95-109">This example requires:</span></span>  
  
- <span data-ttu-id="81f95-110">对 <xref:System.Xml.Linq> 命名空间的引用。</span><span class="sxs-lookup"><span data-stu-id="81f95-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81f95-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="81f95-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [<span data-ttu-id="81f95-112">XML Descendant Axis Property</span><span class="sxs-lookup"><span data-stu-id="81f95-112">XML Descendant Axis Property</span></span>](../../../language-reference/xml-axis/xml-descendant-axis-property.md)
- [<span data-ttu-id="81f95-113">XML 值属性</span><span class="sxs-lookup"><span data-stu-id="81f95-113">XML Value Property</span></span>](../../../language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="81f95-114">在 Visual Basic 中访问 XML</span><span class="sxs-lookup"><span data-stu-id="81f95-114">Accessing XML in Visual Basic</span></span>](accessing-xml.md)
- [<span data-ttu-id="81f95-115">XML</span><span class="sxs-lookup"><span data-stu-id="81f95-115">XML</span></span>](index.md)

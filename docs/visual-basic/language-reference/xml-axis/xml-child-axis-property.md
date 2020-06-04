---
title: XML Child Axis Property
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyChildAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 89a59d00-985e-4f5c-b59f-29b47bad11cb
ms.openlocfilehash: 90dc22d12be5566fa1ee40f6b0e48eff8088e67b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400261"
---
# <a name="xml-child-axis-property-visual-basic"></a><span data-ttu-id="3c289-102">XML 子轴属性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c289-102">XML Child Axis Property (Visual Basic)</span></span>
<span data-ttu-id="3c289-103">提供对以下一项的子级的访问：<xref:System.Xml.Linq.XElement> 对象、<xref:System.Xml.Linq.XDocument> 对象、<xref:System.Xml.Linq.XElement> 对象的集合或 <xref:System.Xml.Linq.XDocument> 对象的集合。</span><span class="sxs-lookup"><span data-stu-id="3c289-103">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c289-104">语法</span><span class="sxs-lookup"><span data-stu-id="3c289-104">Syntax</span></span>  
  
```vb  
object.<child>  
```  
  
## <a name="parts"></a><span data-ttu-id="3c289-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="3c289-105">Parts</span></span>  
  
|<span data-ttu-id="3c289-106">术语</span><span class="sxs-lookup"><span data-stu-id="3c289-106">Term</span></span>|<span data-ttu-id="3c289-107">定义</span><span class="sxs-lookup"><span data-stu-id="3c289-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="3c289-108">必需。</span><span class="sxs-lookup"><span data-stu-id="3c289-108">Required.</span></span> <span data-ttu-id="3c289-109"><xref:System.Xml.Linq.XElement> 对象、<xref:System.Xml.Linq.XDocument> 对象、<xref:System.Xml.Linq.XElement> 对象的集合或 <xref:System.Xml.Linq.XDocument> 对象的集合。</span><span class="sxs-lookup"><span data-stu-id="3c289-109">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>|  
|<span data-ttu-id="3c289-110">。 <</span><span class="sxs-lookup"><span data-stu-id="3c289-110">.<</span></span>|<span data-ttu-id="3c289-111">必需。</span><span class="sxs-lookup"><span data-stu-id="3c289-111">Required.</span></span> <span data-ttu-id="3c289-112">表示子轴属性的开头。</span><span class="sxs-lookup"><span data-stu-id="3c289-112">Denotes the start of a child axis property.</span></span>|  
|`child`|<span data-ttu-id="3c289-113">必需。</span><span class="sxs-lookup"><span data-stu-id="3c289-113">Required.</span></span> <span data-ttu-id="3c289-114">要访问的子节点的名称，格式为 `[prefix:]name` 。</span><span class="sxs-lookup"><span data-stu-id="3c289-114">Name of the child nodes to access, of the form `[prefix:]name`.</span></span><br /><br /> <span data-ttu-id="3c289-115">-   `Prefix`可有可无.</span><span class="sxs-lookup"><span data-stu-id="3c289-115">-   `Prefix` - Optional.</span></span> <span data-ttu-id="3c289-116">子节点的 XML 命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="3c289-116">XML namespace prefix for the child node.</span></span> <span data-ttu-id="3c289-117">必须是使用 `Imports` 语句定义的全局 XML 命名空间。</span><span class="sxs-lookup"><span data-stu-id="3c289-117">Must be a global XML namespace defined with an `Imports` statement.</span></span><br /><span data-ttu-id="3c289-118">-   `Name`请求.</span><span class="sxs-lookup"><span data-stu-id="3c289-118">-   `Name` - Required.</span></span> <span data-ttu-id="3c289-119">本地子节点名。</span><span class="sxs-lookup"><span data-stu-id="3c289-119">Local child node name.</span></span> <span data-ttu-id="3c289-120">请参阅已[声明的 XML 元素和属性的名称](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="3c289-120">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
|>|<span data-ttu-id="3c289-121">必需。</span><span class="sxs-lookup"><span data-stu-id="3c289-121">Required.</span></span> <span data-ttu-id="3c289-122">表示子轴属性的结尾。</span><span class="sxs-lookup"><span data-stu-id="3c289-122">Denotes the end of a child axis property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="3c289-123">返回值</span><span class="sxs-lookup"><span data-stu-id="3c289-123">Return Value</span></span>  
 <span data-ttu-id="3c289-124"><xref:System.Xml.Linq.XElement> 对象的集合。</span><span class="sxs-lookup"><span data-stu-id="3c289-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c289-125">备注</span><span class="sxs-lookup"><span data-stu-id="3c289-125">Remarks</span></span>  
 <span data-ttu-id="3c289-126">可以使用 XML 子轴属性，从 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument> 对象，或从 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument> 对象的集合，按名称访问子节点。</span><span class="sxs-lookup"><span data-stu-id="3c289-126">You can use an XML child axis property to access child nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="3c289-127">使用 XML `Value` 属性来访问返回的集合中第一个子节点的值。</span><span class="sxs-lookup"><span data-stu-id="3c289-127">Use the XML `Value` property to access the value of the first child node in the returned collection.</span></span> <span data-ttu-id="3c289-128">有关详细信息，请参阅[XML Value 属性](xml-value-property.md)。</span><span class="sxs-lookup"><span data-stu-id="3c289-128">For more information, see [XML Value Property](xml-value-property.md).</span></span>  
  
 <span data-ttu-id="3c289-129">Visual Basic 编译器将子轴属性转换为对方法的调用 <xref:System.Xml.Linq.XContainer.Elements%2A> 。</span><span class="sxs-lookup"><span data-stu-id="3c289-129">The Visual Basic compiler converts child axis properties to calls to the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="3c289-130">XML 命名空间</span><span class="sxs-lookup"><span data-stu-id="3c289-130">XML Namespaces</span></span>  
 <span data-ttu-id="3c289-131">子轴属性中的名称仅可使用通过 `Imports` 语句全局声明的 XML 命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="3c289-131">The name in a child axis property can use only XML namespace prefixes declared globally with the `Imports` statement.</span></span> <span data-ttu-id="3c289-132">它不能使用在 XML 元素文本中局部声明的 XML 命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="3c289-132">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="3c289-133">有关详细信息，请参阅[Imports 语句（XML 命名空间）](../statements/imports-statement-xml-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="3c289-133">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c289-134">示例</span><span class="sxs-lookup"><span data-stu-id="3c289-134">Example</span></span>  
 <span data-ttu-id="3c289-135">下面的示例演示如何从 `contact` 对象访问名为 `phone` 的子节点。</span><span class="sxs-lookup"><span data-stu-id="3c289-135">The following example shows how to access the child nodes named `phone` from the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#17)]  
  
 <span data-ttu-id="3c289-136">此代码显示以下文本：</span><span class="sxs-lookup"><span data-stu-id="3c289-136">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="3c289-137">示例</span><span class="sxs-lookup"><span data-stu-id="3c289-137">Example</span></span>  
 <span data-ttu-id="3c289-138">下面的示例演示如何从由 `contacts` 对象的 `contact` 子轴属性返回的集合访问名为 `phone` 的子节点。</span><span class="sxs-lookup"><span data-stu-id="3c289-138">The following example shows how to access the child nodes named `phone` from the collection returned by the `contact` child axis property of the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#18)]  
  
 <span data-ttu-id="3c289-139">此代码显示以下文本：</span><span class="sxs-lookup"><span data-stu-id="3c289-139">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="3c289-140">示例</span><span class="sxs-lookup"><span data-stu-id="3c289-140">Example</span></span>  
 <span data-ttu-id="3c289-141">下面的示例声明 `ns` 作为 XML 命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="3c289-141">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="3c289-142">然后它使用该命名空间前缀来创建 XML 文本并访问具有限定名称 `ns:name` 的第一个子节点。</span><span class="sxs-lookup"><span data-stu-id="3c289-142">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 <span data-ttu-id="3c289-143">此代码显示以下文本：</span><span class="sxs-lookup"><span data-stu-id="3c289-143">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="3c289-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3c289-144">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="3c289-145">XML 轴属性</span><span class="sxs-lookup"><span data-stu-id="3c289-145">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="3c289-146">XML 文本</span><span class="sxs-lookup"><span data-stu-id="3c289-146">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="3c289-147">在 Visual Basic 中创建 XML</span><span class="sxs-lookup"><span data-stu-id="3c289-147">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="3c289-148">已声明的 XML 元素和属性的名称</span><span class="sxs-lookup"><span data-stu-id="3c289-148">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)

---
title: XML Descendant Axis Property
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Basic]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
ms.openlocfilehash: 52544619171dbc7034baeb5feb61395d81096387
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400248"
---
# <a name="xml-descendant-axis-property-visual-basic"></a><span data-ttu-id="0858f-102">XML 后代轴属性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0858f-102">XML Descendant Axis Property (Visual Basic)</span></span>

<span data-ttu-id="0858f-103">提供对以下各项的后代的访问： <xref:System.Xml.Linq.XElement> 对象、对象 <xref:System.Xml.Linq.XDocument> 、对象的集合 <xref:System.Xml.Linq.XElement> 或对象的集合 <xref:System.Xml.Linq.XDocument> 。</span><span class="sxs-lookup"><span data-stu-id="0858f-103">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>

## <a name="syntax"></a><span data-ttu-id="0858f-104">语法</span><span class="sxs-lookup"><span data-stu-id="0858f-104">Syntax</span></span>

```vb
object...<descendant>
```

## <a name="parts"></a><span data-ttu-id="0858f-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="0858f-105">Parts</span></span>

<span data-ttu-id="0858f-106">`object`（必需）。</span><span class="sxs-lookup"><span data-stu-id="0858f-106">`object` Required.</span></span> <span data-ttu-id="0858f-107"><xref:System.Xml.Linq.XElement> 对象、<xref:System.Xml.Linq.XDocument> 对象、<xref:System.Xml.Linq.XElement> 对象的集合或 <xref:System.Xml.Linq.XDocument> 对象的集合。</span><span class="sxs-lookup"><span data-stu-id="0858f-107">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>

<span data-ttu-id="0858f-108">`...<`（必需）。</span><span class="sxs-lookup"><span data-stu-id="0858f-108">`...<` Required.</span></span> <span data-ttu-id="0858f-109">表示子代轴属性的开头。</span><span class="sxs-lookup"><span data-stu-id="0858f-109">Denotes the start of a descendant axis property.</span></span>

<span data-ttu-id="0858f-110">`descendant`（必需）。</span><span class="sxs-lookup"><span data-stu-id="0858f-110">`descendant` Required.</span></span> <span data-ttu-id="0858f-111">要访问的子代节点的名称，格式为 [ `prefix:]name` 。</span><span class="sxs-lookup"><span data-stu-id="0858f-111">Name of the descendant nodes to access, of the form [`prefix:]name`.</span></span>

|<span data-ttu-id="0858f-112">组成部分</span><span class="sxs-lookup"><span data-stu-id="0858f-112">Part</span></span>|<span data-ttu-id="0858f-113">说明</span><span class="sxs-lookup"><span data-stu-id="0858f-113">Description</span></span>|
|----------|-----------------|
|`prefix`|<span data-ttu-id="0858f-114">可选。</span><span class="sxs-lookup"><span data-stu-id="0858f-114">Optional.</span></span> <span data-ttu-id="0858f-115">子代节点的 XML 命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="0858f-115">XML namespace prefix for the descendant node.</span></span> <span data-ttu-id="0858f-116">必须是使用语句定义的全局 XML 命名空间 `Imports` 。</span><span class="sxs-lookup"><span data-stu-id="0858f-116">Must be a global XML namespace that is defined by using an `Imports` statement.</span></span>|
|`name`|<span data-ttu-id="0858f-117">必需。</span><span class="sxs-lookup"><span data-stu-id="0858f-117">Required.</span></span> <span data-ttu-id="0858f-118">子代节点的本地名称。</span><span class="sxs-lookup"><span data-stu-id="0858f-118">Local name of the descendant node.</span></span> <span data-ttu-id="0858f-119">请参阅已[声明的 XML 元素和属性的名称](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="0858f-119">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|

<span data-ttu-id="0858f-120">`>`（必需）。</span><span class="sxs-lookup"><span data-stu-id="0858f-120">`>` Required.</span></span> <span data-ttu-id="0858f-121">表示子代轴属性的结尾。</span><span class="sxs-lookup"><span data-stu-id="0858f-121">Denotes the end of a descendant axis property.</span></span>

## <a name="return-value"></a><span data-ttu-id="0858f-122">返回值</span><span class="sxs-lookup"><span data-stu-id="0858f-122">Return Value</span></span>

<span data-ttu-id="0858f-123"><xref:System.Xml.Linq.XElement> 对象的集合。</span><span class="sxs-lookup"><span data-stu-id="0858f-123">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>

## <a name="remarks"></a><span data-ttu-id="0858f-124">备注</span><span class="sxs-lookup"><span data-stu-id="0858f-124">Remarks</span></span>

<span data-ttu-id="0858f-125">您可以使用 XML 子代轴属性，按名称从或对象访问子代节点 <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> ，或者从或对象的集合访问子代节点 <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> 。</span><span class="sxs-lookup"><span data-stu-id="0858f-125">You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="0858f-126">使用 XML `Value` 属性可访问返回的集合中的第一个子代节点的值。</span><span class="sxs-lookup"><span data-stu-id="0858f-126">Use the XML `Value` property to access the value of the first descendant node in the returned collection.</span></span> <span data-ttu-id="0858f-127">有关详细信息，请参阅[XML Value 属性](xml-value-property.md)。</span><span class="sxs-lookup"><span data-stu-id="0858f-127">For more information, see [XML Value Property](xml-value-property.md).</span></span>

<span data-ttu-id="0858f-128">Visual Basic 编译器将子代轴属性转换为对方法的调用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 。</span><span class="sxs-lookup"><span data-stu-id="0858f-128">The Visual Basic compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.</span></span>

## <a name="xml-namespaces"></a><span data-ttu-id="0858f-129">XML 命名空间</span><span class="sxs-lookup"><span data-stu-id="0858f-129">XML Namespaces</span></span>

<span data-ttu-id="0858f-130">子代轴属性中的名称只能使用通过语句全局声明的 XML 命名空间 `Imports` 。</span><span class="sxs-lookup"><span data-stu-id="0858f-130">The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement.</span></span> <span data-ttu-id="0858f-131">它不能使用在 XML 元素文本中本地声明的 XML 命名空间。</span><span class="sxs-lookup"><span data-stu-id="0858f-131">It cannot use XML namespaces declared locally within XML element literals.</span></span> <span data-ttu-id="0858f-132">有关详细信息，请参阅[Imports 语句（XML 命名空间）](../statements/imports-statement-xml-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="0858f-132">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>

## <a name="example"></a><span data-ttu-id="0858f-133">示例</span><span class="sxs-lookup"><span data-stu-id="0858f-133">Example</span></span>

<span data-ttu-id="0858f-134">下面的示例演示如何从对象中访问名为的第一个子代节点的值 `name` 以及名为的所有子代节点的值 `phone` `contacts` 。</span><span class="sxs-lookup"><span data-stu-id="0858f-134">The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.</span></span>

[!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]

<span data-ttu-id="0858f-135">此代码显示以下文本：</span><span class="sxs-lookup"><span data-stu-id="0858f-135">This code displays the following text:</span></span>

`Name: Patrick Hines`

`Home Phone = 206-555-0144`

## <a name="example"></a><span data-ttu-id="0858f-136">示例</span><span class="sxs-lookup"><span data-stu-id="0858f-136">Example</span></span>

<span data-ttu-id="0858f-137">下面的示例声明 `ns` 作为 XML 命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="0858f-137">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="0858f-138">然后，它使用命名空间的前缀创建 XML 文本，并访问具有限定名称的第一个子节点的值 `ns:name` 。</span><span class="sxs-lookup"><span data-stu-id="0858f-138">It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.</span></span>

[!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]

<span data-ttu-id="0858f-139">此代码显示以下文本：</span><span class="sxs-lookup"><span data-stu-id="0858f-139">This code displays the following text:</span></span>

`Name: Patrick Hines`

## <a name="see-also"></a><span data-ttu-id="0858f-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0858f-140">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="0858f-141">XML 轴属性</span><span class="sxs-lookup"><span data-stu-id="0858f-141">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="0858f-142">XML 文本</span><span class="sxs-lookup"><span data-stu-id="0858f-142">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="0858f-143">在 Visual Basic 中创建 XML</span><span class="sxs-lookup"><span data-stu-id="0858f-143">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="0858f-144">已声明的 XML 元素和属性的名称</span><span class="sxs-lookup"><span data-stu-id="0858f-144">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)

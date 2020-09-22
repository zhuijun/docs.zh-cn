---
title: XML Attribute Axis Property
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyAttributeAxis
helpviewer_keywords:
- attribute axis property [Visual Basic]
- Visual Basic code, accessing XML
- XML attribute axis property [Visual Basic]
- XML axis [Visual Basic], attribute
- XML [Visual Basic], accessing
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
ms.openlocfilehash: 9eddd132b2d4dd6ffbd935a0c8c57a03a3d65435
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869438"
---
# <a name="xml-attribute-axis-property-visual-basic"></a><span data-ttu-id="e0252-102">XML 特性轴属性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0252-102">XML Attribute Axis Property (Visual Basic)</span></span>

<span data-ttu-id="e0252-103">提供对对象的属性值 <xref:System.Xml.Linq.XElement> 或对象集合中第一个元素的访问 <xref:System.Xml.Linq.XElement> 。</span><span class="sxs-lookup"><span data-stu-id="e0252-103">Provides access to the value of an attribute for an <xref:System.Xml.Linq.XElement> object or to the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0252-104">语法</span><span class="sxs-lookup"><span data-stu-id="e0252-104">Syntax</span></span>  
  
```vb  
object.@attribute  
' -or-  
object.@<attribute>  
```  
  
## <a name="parts"></a><span data-ttu-id="e0252-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="e0252-105">Parts</span></span>  

 `object`  
 <span data-ttu-id="e0252-106">必需。</span><span class="sxs-lookup"><span data-stu-id="e0252-106">Required.</span></span> <span data-ttu-id="e0252-107"><xref:System.Xml.Linq.XElement>对象或对象的集合 <xref:System.Xml.Linq.XElement> 。</span><span class="sxs-lookup"><span data-stu-id="e0252-107">An <xref:System.Xml.Linq.XElement> object or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="e0252-108">.@</span><span class="sxs-lookup"><span data-stu-id="e0252-108">.@</span></span>  
 <span data-ttu-id="e0252-109">必需。</span><span class="sxs-lookup"><span data-stu-id="e0252-109">Required.</span></span> <span data-ttu-id="e0252-110">表示属性轴属性的开头。</span><span class="sxs-lookup"><span data-stu-id="e0252-110">Denotes the start of an attribute axis property.</span></span>  
  
 <  
 <span data-ttu-id="e0252-111">可选。</span><span class="sxs-lookup"><span data-stu-id="e0252-111">Optional.</span></span> <span data-ttu-id="e0252-112">表示当不是 Visual Basic 中的有效标识符时属性名称的开头 `attribute` 。</span><span class="sxs-lookup"><span data-stu-id="e0252-112">Denotes the beginning of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
 `attribute`  
 <span data-ttu-id="e0252-113">必需。</span><span class="sxs-lookup"><span data-stu-id="e0252-113">Required.</span></span> <span data-ttu-id="e0252-114">要访问的属性的名称，格式为 [ `prefix` ：] `name` 。</span><span class="sxs-lookup"><span data-stu-id="e0252-114">Name of the attribute to access, of the form [`prefix`:]`name`.</span></span>  
  
|<span data-ttu-id="e0252-115">部件</span><span class="sxs-lookup"><span data-stu-id="e0252-115">Part</span></span>|<span data-ttu-id="e0252-116">描述</span><span class="sxs-lookup"><span data-stu-id="e0252-116">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="e0252-117">可选。</span><span class="sxs-lookup"><span data-stu-id="e0252-117">Optional.</span></span> <span data-ttu-id="e0252-118">特性的 XML 命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="e0252-118">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="e0252-119">必须是使用 `Imports` 语句定义的全局 XML 命名空间。</span><span class="sxs-lookup"><span data-stu-id="e0252-119">Must be a global XML namespace defined with an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="e0252-120">必需。</span><span class="sxs-lookup"><span data-stu-id="e0252-120">Required.</span></span> <span data-ttu-id="e0252-121">本地属性名称。</span><span class="sxs-lookup"><span data-stu-id="e0252-121">Local attribute name.</span></span> <span data-ttu-id="e0252-122">请参阅已 [声明的 XML 元素和属性的名称](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="e0252-122">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="e0252-123">可选。</span><span class="sxs-lookup"><span data-stu-id="e0252-123">Optional.</span></span> <span data-ttu-id="e0252-124">表示当不是 `attribute` Visual Basic 中的有效标识符时属性名称的末尾。</span><span class="sxs-lookup"><span data-stu-id="e0252-124">Denotes the end of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0252-125">返回值</span><span class="sxs-lookup"><span data-stu-id="e0252-125">Return Value</span></span>  

 <span data-ttu-id="e0252-126">一个包含的值的字符串 `attribute` 。</span><span class="sxs-lookup"><span data-stu-id="e0252-126">A string that contains the value of `attribute`.</span></span> <span data-ttu-id="e0252-127">如果属性名不存在， `Nothing` 则返回。</span><span class="sxs-lookup"><span data-stu-id="e0252-127">If the attribute name does not exist, `Nothing` is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0252-128">备注</span><span class="sxs-lookup"><span data-stu-id="e0252-128">Remarks</span></span>  

 <span data-ttu-id="e0252-129">您可以使用 XML 特性轴属性，按名称从 <xref:System.Xml.Linq.XElement> 对象或对象集合中的第一个元素访问属性值 <xref:System.Xml.Linq.XElement> 。</span><span class="sxs-lookup"><span data-stu-id="e0252-129">You can use an XML attribute axis property to access the value of an attribute by name from an <xref:System.Xml.Linq.XElement> object or from the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="e0252-130">可以按名称检索属性值，也可以通过指定一个新名称（前面带有 @ 标识符）来向元素添加一个新的属性。</span><span class="sxs-lookup"><span data-stu-id="e0252-130">You can retrieve an attribute value by name, or add a new attribute to an element by specifying a new name preceded by the @ identifier.</span></span>  
  
 <span data-ttu-id="e0252-131">当使用 @ 标识符引用 XML 特性时，特性值将以字符串的形式返回，无需显式指定 <xref:System.Xml.Linq.XAttribute.Value%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="e0252-131">When you refer to an XML attribute using the @ identifier, the attribute value is returned as a string and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="e0252-132">XML 特性的命名规则不同于 Visual Basic 标识符的命名规则。</span><span class="sxs-lookup"><span data-stu-id="e0252-132">The naming rules for XML attributes differ from the naming rules for Visual Basic identifiers.</span></span> <span data-ttu-id="e0252-133">若要访问名称不是有效 Visual Basic 标识符的 XML 特性，请将该名称括在尖括号中 (\< and >) 。</span><span class="sxs-lookup"><span data-stu-id="e0252-133">To access an XML attribute that has a name that is not a valid Visual Basic identifier, enclose the name in angle brackets (\< and >).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="e0252-134">XML 命名空间</span><span class="sxs-lookup"><span data-stu-id="e0252-134">XML Namespaces</span></span>  

 <span data-ttu-id="e0252-135">特性轴属性中的名称只能使用语句在全局声明的 XML 命名空间前缀 `Imports` 。</span><span class="sxs-lookup"><span data-stu-id="e0252-135">The name in an attribute axis property can use only XML namespace prefixes declared globally by using the `Imports` statement.</span></span> <span data-ttu-id="e0252-136">它不能使用在 XML 元素文本中局部声明的 XML 命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="e0252-136">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="e0252-137">有关详细信息，请参阅 [ (XML 命名空间) 的 Imports 语句 ](../statements/imports-statement-xml-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="e0252-137">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0252-138">示例</span><span class="sxs-lookup"><span data-stu-id="e0252-138">Example</span></span>  

 <span data-ttu-id="e0252-139">下面的示例演示如何 `type` 从名为的 xml 元素集合中获取名为的 xml 特性的值 `phone` 。</span><span class="sxs-lookup"><span data-stu-id="e0252-139">The following example shows how to get the values of the XML attributes named `type` from a collection of XML elements that are named `phone`.</span></span>  
  
 [!code-vb[VbXMLSamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#12)]  
  
 <span data-ttu-id="e0252-140">此代码显示以下文本：</span><span class="sxs-lookup"><span data-stu-id="e0252-140">This code displays the following text:</span></span>  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a><span data-ttu-id="e0252-141">示例</span><span class="sxs-lookup"><span data-stu-id="e0252-141">Example</span></span>  

 <span data-ttu-id="e0252-142">下面的示例演示如何在 XML 中以声明方式同时创建 XML 元素的特性，并通过将特性添加到对象的实例来动态创建属性 <xref:System.Xml.Linq.XElement> 。</span><span class="sxs-lookup"><span data-stu-id="e0252-142">The following example shows how to create attributes for an XML element both declaratively, as part of the XML, and dynamically by adding an attribute to an instance of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="e0252-143">`type`属性以声明方式创建，并 `owner` 动态创建属性。</span><span class="sxs-lookup"><span data-stu-id="e0252-143">The `type` attribute is created declaratively and the `owner` attribute is created dynamically.</span></span>  
  
 [!code-vb[VbXMLSamples#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#44)]  
  
 <span data-ttu-id="e0252-144">此代码显示以下文本：</span><span class="sxs-lookup"><span data-stu-id="e0252-144">This code displays the following text:</span></span>  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a><span data-ttu-id="e0252-145">示例</span><span class="sxs-lookup"><span data-stu-id="e0252-145">Example</span></span>  

 <span data-ttu-id="e0252-146">下面的示例使用尖括号语法来获取名为的 XML 属性的值 `number-type` ，该属性不是 Visual Basic 中的有效标识符。</span><span class="sxs-lookup"><span data-stu-id="e0252-146">The following example uses the angle bracket syntax to get the value of the XML attribute named `number-type`, which is not a valid identifier in Visual Basic.</span></span>  
  
 [!code-vb[VbXMLSamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#13)]  
  
 <span data-ttu-id="e0252-147">此代码显示以下文本：</span><span class="sxs-lookup"><span data-stu-id="e0252-147">This code displays the following text:</span></span>  
  
 `Phone type: work`  
  
## <a name="example"></a><span data-ttu-id="e0252-148">示例</span><span class="sxs-lookup"><span data-stu-id="e0252-148">Example</span></span>  

 <span data-ttu-id="e0252-149">下面的示例声明 `ns` 作为 XML 命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="e0252-149">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="e0252-150">然后，它使用命名空间的前缀创建 XML 文本，并访问具有限定名 "" 的第一个子节点 `ns:name` 。</span><span class="sxs-lookup"><span data-stu-id="e0252-150">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name "`ns:name`".</span></span>  
  
 [!code-vb[VbXMLSamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples6.vb#14)]  
  
 <span data-ttu-id="e0252-151">此代码显示以下文本：</span><span class="sxs-lookup"><span data-stu-id="e0252-151">This code displays the following text:</span></span>  
  
 `Phone type: home`  
  
## <a name="see-also"></a><span data-ttu-id="e0252-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e0252-152">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="e0252-153">XML 轴属性</span><span class="sxs-lookup"><span data-stu-id="e0252-153">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="e0252-154">XML 文本</span><span class="sxs-lookup"><span data-stu-id="e0252-154">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="e0252-155">在 Visual Basic 中创建 XML</span><span class="sxs-lookup"><span data-stu-id="e0252-155">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="e0252-156">已声明的 XML 元素和属性的名称</span><span class="sxs-lookup"><span data-stu-id="e0252-156">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)

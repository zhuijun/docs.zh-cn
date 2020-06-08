---
title: 从 XML 文档推断架构
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: f3d97d53-614d-4a04-a174-87965b7405f6
ms.openlocfilehash: 5b0f9bea33346083ce0015fbf3cdfeb0e0ea1181
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287657"
---
# <a name="inferring-schemas-from-xml-documents"></a><span data-ttu-id="fe065-102">从 XML 文档推断架构</span><span class="sxs-lookup"><span data-stu-id="fe065-102">Inferring Schemas from XML Documents</span></span>
<span data-ttu-id="fe065-103">此主题描述如何使用 <xref:System.Xml.Schema.XmlSchemaInference> 类从 XML 文档的结构推断 XML 架构定义语言 (XSD) 架构。</span><span class="sxs-lookup"><span data-stu-id="fe065-103">This topic describes how to use the <xref:System.Xml.Schema.XmlSchemaInference> class to infer an XML Schema definition language (XSD) schema from the structure of an XML document.</span></span>  
  
## <a name="the-schema-inference-process"></a><span data-ttu-id="fe065-104">架构推断过程</span><span class="sxs-lookup"><span data-stu-id="fe065-104">The Schema Inference Process</span></span>  
 <span data-ttu-id="fe065-105"><xref:System.Xml.Schema.XmlSchemaInference> 命名空间的 <xref:System.Xml.Schema?displayProperty=nameWithType> 类用于从 XML 文档的结构生成一个或多个 XML 架构定义语言 (XSD) 架构。</span><span class="sxs-lookup"><span data-stu-id="fe065-105">The <xref:System.Xml.Schema.XmlSchemaInference> class of the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace is used to generate one or more XML Schema definition language (XSD) schemas from the structure of an XML document.</span></span> <span data-ttu-id="fe065-106">生成的架构可以用于验证原始 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="fe065-106">The generated schemas may be used to validate the original XML document.</span></span>  
  
 <span data-ttu-id="fe065-107">XML 文档由 <xref:System.Xml.Schema.XmlSchemaInference> 类处理时，<xref:System.Xml.Schema.XmlSchemaInference> 类假定架构组件描述了 XML 文档中的元素和属性。</span><span class="sxs-lookup"><span data-stu-id="fe065-107">As an XML document is processed by the <xref:System.Xml.Schema.XmlSchemaInference> class, the <xref:System.Xml.Schema.XmlSchemaInference> class makes assumptions about the schema components that describe the elements and attributes in the XML document.</span></span> <span data-ttu-id="fe065-108"><xref:System.Xml.Schema.XmlSchemaInference> 类还通过为特定元素或属性推断限制性最强的类型，以约束的方式推断架构组件。</span><span class="sxs-lookup"><span data-stu-id="fe065-108">The <xref:System.Xml.Schema.XmlSchemaInference> class also infers schema components in a constrained way by inferring the most restrictive type for a particular element or attribute.</span></span> <span data-ttu-id="fe065-109">随着收集到的 XML 文档信息越来越多，将推断限制性较弱的类型，从而放松这些约束。</span><span class="sxs-lookup"><span data-stu-id="fe065-109">As more information about the XML document is gathered, these constraints are loosened by inferring less restrictive types.</span></span> <span data-ttu-id="fe065-110">可以推断的限制性最弱的类型为 `xs:string`。</span><span class="sxs-lookup"><span data-stu-id="fe065-110">The least restrictive type that can be inferred is `xs:string`.</span></span>  
  
 <span data-ttu-id="fe065-111">以 XML 文档的以下片断为例。</span><span class="sxs-lookup"><span data-stu-id="fe065-111">Take, for example, the following piece of an XML document.</span></span>  
  
```xml  
<parent attribute1="6">  
    <child>One</child>  
    <child>Two</child>  
</parent>  
<parent attribute1="A" />
```  
  
 <span data-ttu-id="fe065-112">在上述示例中，当 `attribute1` 过程遇到值为 `6` 的 <xref:System.Xml.Schema.XmlSchemaInference> 属性时，假定类型为 `xs:unsignedByte`。</span><span class="sxs-lookup"><span data-stu-id="fe065-112">In the example above, when the `attribute1` attribute is encountered with a value of `6` by the <xref:System.Xml.Schema.XmlSchemaInference> process, it is assumed to be of type `xs:unsignedByte`.</span></span> <span data-ttu-id="fe065-113">当 `parent` 过程遇到第二个 <xref:System.Xml.Schema.XmlSchemaInference> 元素时，类型将修改为 `xs:string`，从而放松约束，因为现在 `attribute1` 属性的值为 `A`。</span><span class="sxs-lookup"><span data-stu-id="fe065-113">When the second `parent` element is encountered by the <xref:System.Xml.Schema.XmlSchemaInference> process, the constraint is loosened by modifying the type to `xs:string` because the value of the `attribute1` attribute is now `A`.</span></span> <span data-ttu-id="fe065-114">同样，在架构中推断的所有 `minOccurs` 元素的 `child` 属性均放松为 `minOccurs="0"`，因为第二个父元素没有子元素。</span><span class="sxs-lookup"><span data-stu-id="fe065-114">Similarly, the `minOccurs` attribute for all the `child` elements inferred in the schema are loosened to `minOccurs="0"` because the second parent element has no child elements.</span></span>  
  
## <a name="inferring-schemas-from-xml-documents"></a><span data-ttu-id="fe065-115">从 XML 文档推断架构</span><span class="sxs-lookup"><span data-stu-id="fe065-115">Inferring Schemas from XML Documents</span></span>  
 <span data-ttu-id="fe065-116"><xref:System.Xml.Schema.XmlSchemaInference> 类使用两个重载 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> 方法从 XML 文档推断架构。</span><span class="sxs-lookup"><span data-stu-id="fe065-116">The <xref:System.Xml.Schema.XmlSchemaInference> class uses two overloaded <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> methods to infer a schema from an XML document.</span></span>  
  
 <span data-ttu-id="fe065-117">第一种 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> 方法用于基于 XML 文档创建架构。</span><span class="sxs-lookup"><span data-stu-id="fe065-117">The first <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method is used to create a schema based on an XML document.</span></span> <span data-ttu-id="fe065-118">第二种 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> 方法用于推断描述多个 XML 文档的架构。</span><span class="sxs-lookup"><span data-stu-id="fe065-118">The second <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method is used to infer a schema that describes multiple XML documents.</span></span> <span data-ttu-id="fe065-119">例如，可以将多个 XML 文档传入 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> 方法，一次传入一个，以生成描述整个 XML 文档集的架构。</span><span class="sxs-lookup"><span data-stu-id="fe065-119">For example, you can feed multiple XML documents to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method one at a time to produce a schema that describes the entire set of XML documents.</span></span>  
  
 <span data-ttu-id="fe065-120">第一种 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> 方法从 <xref:System.Xml.XmlReader> 对象中包含的 XML 文档推断架构，并返回包含推断出的架构的 <xref:System.Xml.Schema.XmlSchemaSet> 对象。</span><span class="sxs-lookup"><span data-stu-id="fe065-120">The first <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method infers a schema from an XML document contained in an <xref:System.Xml.XmlReader> object, and returns an <xref:System.Xml.Schema.XmlSchemaSet> object containing the inferred schema.</span></span> <span data-ttu-id="fe065-121">第二种 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> 方法在 <xref:System.Xml.Schema.XmlSchemaSet> 对象中搜索目标命名空间与 <xref:System.Xml.XmlReader> 对象中包含的 XML 文档相同的架构，精选现有架构，并返回包含推断出的架构的 <xref:System.Xml.Schema.XmlSchemaSet> 对象。</span><span class="sxs-lookup"><span data-stu-id="fe065-121">The second <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method searches an <xref:System.Xml.Schema.XmlSchemaSet> object for a schema with the same target namespace as the XML document contained in the <xref:System.Xml.XmlReader> object, refines the existing schema, and returns an <xref:System.Xml.Schema.XmlSchemaSet> object containing the inferred schema.</span></span>  
  
 <span data-ttu-id="fe065-122">对精选的架构所做的更改基于 XML 文档中的新结构。</span><span class="sxs-lookup"><span data-stu-id="fe065-122">The changes made to the refined schema are based on new structure found in the XML document.</span></span> <span data-ttu-id="fe065-123">例如，在遍历 XML 文档时，假定发现的数据类型，并基于这些假定创建架构。</span><span class="sxs-lookup"><span data-stu-id="fe065-123">For example, as an XML document is traversed, assumptions are made about the data types found, and the schema is created based on those assumptions.</span></span> <span data-ttu-id="fe065-124">但是，如果在另一次推断过程中遇到与原始假定不同的数据，将精选该架构。</span><span class="sxs-lookup"><span data-stu-id="fe065-124">However, if data is encountered on a second inference pass that differs from the original assumption, the schema is refined.</span></span> <span data-ttu-id="fe065-125">下面的示例阐释此精选过程。</span><span class="sxs-lookup"><span data-stu-id="fe065-125">The following example illustrates the refinement process.</span></span>  
  
 [!code-cpp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaInferenceExamples/CPP/XmlSchemaInferenceExamples.cpp#4)]
 [!code-csharp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaInferenceExamples/CS/XmlSchemaInferenceExamples.cs#4)]
 [!code-vb[XmlSchemaInferenceExamples#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaInferenceExamples/VB/XmlSchemaInferenceExamples.vb#4)]  
  
 <span data-ttu-id="fe065-126">该示例使用以下 `item1.xml` 文件作为第一个输入。</span><span class="sxs-lookup"><span data-stu-id="fe065-126">The example takes the following file, `item1.xml`, as its first input.</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#13](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item1.xml#13)]  
  
 <span data-ttu-id="fe065-127">然后使用 `item2.xml` 文件作为第二个输入：</span><span class="sxs-lookup"><span data-stu-id="fe065-127">The example then takes the `item2.xml` file as its second input:</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#14](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item2.xml#14)]  
  
 <span data-ttu-id="fe065-128">在第一个 XML 文档中遇到 `productID` 属性时，`123456789` 的值将假定为 `xs:unsignedInt` 类型。</span><span class="sxs-lookup"><span data-stu-id="fe065-128">When the `productID` attribute is encountered in the first XML document, the value of `123456789` is assumed to be an `xs:unsignedInt` type.</span></span> <span data-ttu-id="fe065-129">但是，在读取第二个 XML 文档并发现 `A53-246` 值时，就不再假定 `xs:unsignedInt` 类型。</span><span class="sxs-lookup"><span data-stu-id="fe065-129">However, when the second XML document is read and the value of `A53-246` is found, the `xs:unsignedInt` type can no longer be assumed.</span></span> <span data-ttu-id="fe065-130">将精选该架构，`productID` 的类型更改为 `xs:string`。</span><span class="sxs-lookup"><span data-stu-id="fe065-130">The schema is refined and the type of `productID` is changed to `xs:string`.</span></span> <span data-ttu-id="fe065-131">此外，`minOccurs` 元素的 `supplierID` 属性设置为 `0`，因为第二个 XML 文档中没有 `supplierID` 元素。</span><span class="sxs-lookup"><span data-stu-id="fe065-131">In addition, the `minOccurs` attribute for the `supplierID` element is set to `0`, because the second XML document contains no `supplierID` element.</span></span>  
  
 <span data-ttu-id="fe065-132">以下是从第一个 XML 文档推断的架构。</span><span class="sxs-lookup"><span data-stu-id="fe065-132">The following is the schema inferred from the first XML document.</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#15](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema1.xml#15)]  
  
 <span data-ttu-id="fe065-133">以下是从第一个 XML 文档推断的架构，通过第二个 XML 文档进行精选。</span><span class="sxs-lookup"><span data-stu-id="fe065-133">The following is the schema inferred from the first XML document, refined by the second XML document.</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#16](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema2.xml#16)]  
  
## <a name="inline-schemas"></a><span data-ttu-id="fe065-134">内联架构</span><span class="sxs-lookup"><span data-stu-id="fe065-134">Inline Schemas</span></span>  
 <span data-ttu-id="fe065-135">如果在 <xref:System.Xml.Schema.XmlSchemaInference> 过程中遇到内联 XML 架构定义语言 (XSD) 架构，将引发 <xref:System.Xml.Schema.XmlSchemaInferenceException>。</span><span class="sxs-lookup"><span data-stu-id="fe065-135">If an inline XML Schema definition language (XSD) schema is encountered during the <xref:System.Xml.Schema.XmlSchemaInference> process, an <xref:System.Xml.Schema.XmlSchemaInferenceException> is thrown.</span></span> <span data-ttu-id="fe065-136">例如，以下内联架构将引发 <xref:System.Xml.Schema.XmlSchemaInferenceException>。</span><span class="sxs-lookup"><span data-stu-id="fe065-136">For example, the following inline schema throws an <xref:System.Xml.Schema.XmlSchemaInferenceException>.</span></span>  
  
```xml  
<root xmlns:ex="http://www.contoso.com" xmlns="http://www.tempuri.org">  
    <xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://www.contoso.com">  
        <xs:element name="Contoso" type="xs:normalizedString" />  
    </xs:schema>  
    <ex:Contoso>Test</ex:Contoso>  
</root>  
```  
  
## <a name="schemas-that-cannot-be-refined"></a><span data-ttu-id="fe065-137">无法精选的架构</span><span class="sxs-lookup"><span data-stu-id="fe065-137">Schemas that Cannot be Refined</span></span>  
 <span data-ttu-id="fe065-138">如果给定要精选的类型，有些 W3C XML 架构构造是 XML 架构定义语言 (XSD) 架构的 <xref:System.Xml.Schema.XmlSchemaInference> 过程无法处理的，并会引发异常。</span><span class="sxs-lookup"><span data-stu-id="fe065-138">There are W3C XML Schema constructs that the XML Schema definition language (XSD) schema <xref:System.Xml.Schema.XmlSchemaInference> process cannot handle if given a type to refine and cause an exception to be thrown.</span></span> <span data-ttu-id="fe065-139">例如顶级复合器不是序列的复杂类型。</span><span class="sxs-lookup"><span data-stu-id="fe065-139">Such as a complex type whose top-level compositor is anything other than a sequence.</span></span> <span data-ttu-id="fe065-140">在架构对象模型 (SOM) 中，这相对于 <xref:System.Xml.Schema.XmlSchemaComplexType>，它的 <xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> 属性不是 <xref:System.Xml.Schema.XmlSchemaSequence> 的实例。</span><span class="sxs-lookup"><span data-stu-id="fe065-140">In the Schema Object Model (SOM), this corresponds to an <xref:System.Xml.Schema.XmlSchemaComplexType> whose <xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> property is not an instance of <xref:System.Xml.Schema.XmlSchemaSequence>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe065-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="fe065-141">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaInference>
- [<span data-ttu-id="fe065-142">XML 架构对象模型 (SOM)</span><span class="sxs-lookup"><span data-stu-id="fe065-142">XML Schema Object Model (SOM)</span></span>](xml-schema-object-model-som.md)
- [<span data-ttu-id="fe065-143">推断 XML 架构</span><span class="sxs-lookup"><span data-stu-id="fe065-143">Inferring an XML Schema</span></span>](inferring-an-xml-schema.md)
- [<span data-ttu-id="fe065-144">推断架构节点类型和结构的规则</span><span class="sxs-lookup"><span data-stu-id="fe065-144">Rules for Inferring Schema Node Types and Structure</span></span>](rules-for-inferring-schema-node-types-and-structure.md)
- [<span data-ttu-id="fe065-145">推断简单类型的规则</span><span class="sxs-lookup"><span data-stu-id="fe065-145">Rules for Inferring Simple Types</span></span>](rules-for-inferring-simple-types.md)

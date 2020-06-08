---
title: 后架构编译信息集
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 7f1bc7f4-401b-459f-9078-f099cc711fde
ms.openlocfilehash: 3bd0c6063fee1fa1a9f046a8be2ebfde07aea9ee
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291508"
---
# <a name="post-schema-compilation-infoset"></a><span data-ttu-id="ef85a-102">后架构编译信息集</span><span class="sxs-lookup"><span data-stu-id="ef85a-102">Post-Schema Compilation Infoset</span></span>
<span data-ttu-id="ef85a-103">[万维网联合会 (W3C) XML 架构建议](https://www.w3.org/XML/Schema)介绍了必须公开的架构验证前和架构编译后信息集。</span><span class="sxs-lookup"><span data-stu-id="ef85a-103">The [World Wide Web Consortium (W3C) XML Schema Recommendation](https://www.w3.org/XML/Schema) discusses the information set (infoset) that must be exposed for pre-schema validation and post-schema compilation.</span></span> <span data-ttu-id="ef85a-104">XML 架构对象模型 (SOM) 在调用 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> 的 <xref:System.Xml.Schema.XmlSchemaSet> 方法之前或之后查看此信息集。</span><span class="sxs-lookup"><span data-stu-id="ef85a-104">The XML Schema Object Model (SOM) views this exposure before and after the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is called.</span></span>  
  
 <span data-ttu-id="ef85a-105">前架构验证信息集在编辑架构过程中生成。</span><span class="sxs-lookup"><span data-stu-id="ef85a-105">The pre-schema validation infoset is built during the editing of the schema.</span></span> <span data-ttu-id="ef85a-106">后架构编译信息集在调用 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> 的 <xref:System.Xml.Schema.XmlSchemaSet> 方法之后、编译架构期间生成，并以属性的形式公开。</span><span class="sxs-lookup"><span data-stu-id="ef85a-106">The post-schema compilation infoset is generated after the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is called, during compilation of the schema, and is exposed as properties.</span></span>  
  
 <span data-ttu-id="ef85a-107">SOM 是表示前架构验证和后架构编译信息集的对象模型；该模型由 <xref:System.Xml.Schema?displayProperty=nameWithType> 命名空间中的类组成。</span><span class="sxs-lookup"><span data-stu-id="ef85a-107">The SOM is the object model that represents the pre-schema validation and post-schema compilation infosets; it consists of the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="ef85a-108"><xref:System.Xml.Schema> 命名空间中的类的所有读取和写入属性属于前架构验证信息集，而 <xref:System.Xml.Schema> 命名空间中的类的所有只读属性属于后架构编译信息集。</span><span class="sxs-lookup"><span data-stu-id="ef85a-108">All read and write properties of classes in the <xref:System.Xml.Schema> namespace belong to the pre-schema validation infoset, while all read-only properties of classes in the <xref:System.Xml.Schema> namespace belong to the post-schema compilation infoset.</span></span> <span data-ttu-id="ef85a-109">此规则不适用于下列属性，下列属性既是前架构验证信息集属性也是后架构编译信息集属性。</span><span class="sxs-lookup"><span data-stu-id="ef85a-109">The exception to this rule are the following properties, which are both pre-schema validation infoset and post-schema compilation infoset properties.</span></span>  
  
|<span data-ttu-id="ef85a-110">类</span><span class="sxs-lookup"><span data-stu-id="ef85a-110">Class</span></span>|<span data-ttu-id="ef85a-111">Property</span><span class="sxs-lookup"><span data-stu-id="ef85a-111">Property</span></span>|  
|-----------|--------------|  
|<xref:System.Xml.Schema.XmlSchemaObject>|<xref:System.Xml.Schema.XmlSchemaObject.Parent%2A>|  
|<xref:System.Xml.Schema.XmlSchema>|<span data-ttu-id="ef85a-112"><xref:System.Xml.Schema.XmlSchema.AttributeFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.BlockDefault%2A>, <xref:System.Xml.Schema.XmlSchema.ElementFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.FinalDefault%2A>, <xref:System.Xml.Schema.XmlSchema.TargetNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="ef85a-112"><xref:System.Xml.Schema.XmlSchema.AttributeFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.BlockDefault%2A>, <xref:System.Xml.Schema.XmlSchema.ElementFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.FinalDefault%2A>, <xref:System.Xml.Schema.XmlSchema.TargetNamespace%2A></span></span>|  
|<xref:System.Xml.Schema.XmlSchemaExternal>|<xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A>|  
|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup.AnyAttribute%2A>|  
|<xref:System.Xml.Schema.XmlSchemaParticle>|<span data-ttu-id="ef85a-113"><xref:System.Xml.Schema.XmlSchemaParticle.MaxOccurs%2A>，<xref:System.Xml.Schema.XmlSchemaParticle.MinOccurs%2A></span><span class="sxs-lookup"><span data-stu-id="ef85a-113"><xref:System.Xml.Schema.XmlSchemaParticle.MaxOccurs%2A>, <xref:System.Xml.Schema.XmlSchemaParticle.MinOccurs%2A></span></span>|  
|<xref:System.Xml.Schema.XmlSchemaComplexType>|<xref:System.Xml.Schema.XmlSchemaComplexType.AnyAttribute%2A>|  
  
 <span data-ttu-id="ef85a-114">例如，<xref:System.Xml.Schema.XmlSchemaElement> 和 <xref:System.Xml.Schema.XmlSchemaComplexType> 类均具有 `BlockResolved` 和 `FinalResolved` 属性。</span><span class="sxs-lookup"><span data-stu-id="ef85a-114">For example, the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaComplexType> classes both have `BlockResolved` and `FinalResolved` properties.</span></span> <span data-ttu-id="ef85a-115">在编译并验证了架构之后，这些属性用于存放 `Block` 和 `Final` 属性的值。</span><span class="sxs-lookup"><span data-stu-id="ef85a-115">These properties are used to hold the values for the `Block` and `Final` properties after the schema has been compiled and validated.</span></span> <span data-ttu-id="ef85a-116">`BlockResolved` 和 `FinalResolved` 是属于后架构编译信息集的只读属性。</span><span class="sxs-lookup"><span data-stu-id="ef85a-116">`BlockResolved` and `FinalResolved` are read-only properties that are part of the post-schema compilation infoset.</span></span>  
  
 <span data-ttu-id="ef85a-117">以下示例显示在验证架构之后设置的 <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> 类的 <xref:System.Xml.Schema.XmlSchemaElement> 属性。</span><span class="sxs-lookup"><span data-stu-id="ef85a-117">The following example shows the <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> class set after validating the schema.</span></span> <span data-ttu-id="ef85a-118">在验证之前，该属性包含 `null` 引用，<xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> 设置为相应类型的名称。</span><span class="sxs-lookup"><span data-stu-id="ef85a-118">Before validation, the property contains a `null` reference, and the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> is set to the name of the type in question.</span></span> <span data-ttu-id="ef85a-119">在验证之后，<xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> 被解析为有效类型，并且可以通过 <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> 属性使用类型对象。</span><span class="sxs-lookup"><span data-stu-id="ef85a-119">After validation, the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> is resolved to a valid type, and the type object is available through the <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> property.</span></span>  
  
 [!code-cpp[PsciSample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/PsciSample/CPP/PsciSample.cpp#1)]
 [!code-csharp[PsciSample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/PsciSample/CS/PsciSample.cs#1)]
 [!code-vb[PsciSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/PsciSample/VB/PsciSample.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ef85a-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="ef85a-120">See also</span></span>

- [<span data-ttu-id="ef85a-121">XML 架构对象模型 (SOM)</span><span class="sxs-lookup"><span data-stu-id="ef85a-121">XML Schema Object Model (SOM)</span></span>](xml-schema-object-model-som.md)

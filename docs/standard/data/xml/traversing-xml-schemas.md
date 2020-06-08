---
title: 遍历 XML 架构
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: cce69574-5861-4a30-b730-2e18d915d8ee
ms.openlocfilehash: 0951e83c3035de751801d194696eb64993260ef8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289832"
---
# <a name="traversing-xml-schemas"></a><span data-ttu-id="0466a-102">遍历 XML 架构</span><span class="sxs-lookup"><span data-stu-id="0466a-102">Traversing XML Schemas</span></span>

<span data-ttu-id="0466a-103">使用架构对象模型 (SOM) API 遍历 XML 架构，可以访问 SOM 中存储的元素、属性和类型。</span><span class="sxs-lookup"><span data-stu-id="0466a-103">Traversing an XML schema using the Schema Object Model (SOM) API provides access to the elements, attributes, and types stored in the SOM.</span></span> <span data-ttu-id="0466a-104">遍历加载到 SOM 的 XML 架构也是使用 SOM API 编辑 XML 架构的第一步。</span><span class="sxs-lookup"><span data-stu-id="0466a-104">Traversing an XML schema loaded into the SOM is also the first step in editing an XML schema using the SOM API.</span></span>

## <a name="traversing-an-xml-schema"></a><span data-ttu-id="0466a-105">遍历 XML 架构</span><span class="sxs-lookup"><span data-stu-id="0466a-105">Traversing an XML Schema</span></span>

<span data-ttu-id="0466a-106">使用 <xref:System.Xml.Schema.XmlSchema> 类的下列属性可以访问添加到 XML 架构的所有全局项的集合。</span><span class="sxs-lookup"><span data-stu-id="0466a-106">The following properties of the <xref:System.Xml.Schema.XmlSchema> class provide access to the collection of all global items added to the XML schema.</span></span>

|<span data-ttu-id="0466a-107">Property</span><span class="sxs-lookup"><span data-stu-id="0466a-107">Property</span></span>|<span data-ttu-id="0466a-108">存储在集合或数组中的对象类型</span><span class="sxs-lookup"><span data-stu-id="0466a-108">Object type stored in the collection or array</span></span>|
|--------------|---------------------------------------------------|
|<xref:System.Xml.Schema.XmlSchema.Elements%2A>|<xref:System.Xml.Schema.XmlSchemaElement>|
|<xref:System.Xml.Schema.XmlSchema.Attributes%2A>|<xref:System.Xml.Schema.XmlSchemaAttribute>|
|<xref:System.Xml.Schema.XmlSchema.AttributeGroups%2A>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|
|<xref:System.Xml.Schema.XmlSchema.Groups%2A>|<xref:System.Xml.Schema.XmlSchemaGroup>|
|<xref:System.Xml.Schema.XmlSchema.Includes%2A>|<span data-ttu-id="0466a-109"><xref:System.Xml.Schema.XmlSchemaExternal>、<xref:System.Xml.Schema.XmlSchemaInclude>、<xref:System.Xml.Schema.XmlSchemaImport> 或 <xref:System.Xml.Schema.XmlSchemaRedefine></span><span class="sxs-lookup"><span data-stu-id="0466a-109"><xref:System.Xml.Schema.XmlSchemaExternal>, <xref:System.Xml.Schema.XmlSchemaInclude>, <xref:System.Xml.Schema.XmlSchemaImport>, or <xref:System.Xml.Schema.XmlSchemaRedefine></span></span>|
|<xref:System.Xml.Schema.XmlSchema.Items%2A>|<span data-ttu-id="0466a-110"><xref:System.Xml.Schema.XmlSchemaObject>（提供对所有全局级元素、属性和类型的访问）</span><span class="sxs-lookup"><span data-stu-id="0466a-110"><xref:System.Xml.Schema.XmlSchemaObject> (provides access to all global level elements, attributes, and types).</span></span>|
|<xref:System.Xml.Schema.XmlSchema.Notations%2A>|<xref:System.Xml.Schema.XmlSchemaNotation>|
|<xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A>|<span data-ttu-id="0466a-111"><xref:System.Xml.Schema.XmlSchemaType>, <xref:System.Xml.Schema.XmlSchemaSimpleType>, <xref:System.Xml.Schema.XmlSchemaComplexType></span><span class="sxs-lookup"><span data-stu-id="0466a-111"><xref:System.Xml.Schema.XmlSchemaType>, <xref:System.Xml.Schema.XmlSchemaSimpleType>, <xref:System.Xml.Schema.XmlSchemaComplexType></span></span>|
|<xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A>|<span data-ttu-id="0466a-112"><xref:System.Xml.XmlAttribute>（提供对不属于架构命名空间的属性的访问）</span><span class="sxs-lookup"><span data-stu-id="0466a-112"><xref:System.Xml.XmlAttribute> (provides access to attributes that do not belong to the schema namespace)</span></span>|

> [!NOTE]
> <span data-ttu-id="0466a-113">上表列出的所有属性（<xref:System.Xml.Schema.XmlSchema.Items%2A> 属性除外）是后架构编译信息集 (PSCI) 属性，直到架构编译后才可用。</span><span class="sxs-lookup"><span data-stu-id="0466a-113">All of the properties listed in the table above, except for the <xref:System.Xml.Schema.XmlSchema.Items%2A> property, are Post-Schema-Compilation-Infoset (PSCI) properties that are not available until the schema has been compiled.</span></span> <span data-ttu-id="0466a-114"><xref:System.Xml.Schema.XmlSchema.Items%2A> 属性是前架构编译属性，可以在架构编译之前使用，以访问和编辑所有全局级元素、属性和类型。</span><span class="sxs-lookup"><span data-stu-id="0466a-114">The <xref:System.Xml.Schema.XmlSchema.Items%2A> property is a pre-schema-compilation property that can be used before the schema has been compiled to access and edit all global level elements, attributes, and types.</span></span>
>
> <span data-ttu-id="0466a-115"><xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A> 属性提供对不属于架构命名空间的所有属性的访问。</span><span class="sxs-lookup"><span data-stu-id="0466a-115">The <xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A> property provides access to all the attributes that do not belong to the schema namespace.</span></span> <span data-ttu-id="0466a-116">架构处理器不处理这些属性。</span><span class="sxs-lookup"><span data-stu-id="0466a-116">These attributes are not processed by the schema processor.</span></span>

<span data-ttu-id="0466a-117">随后的代码示例展示了如何遍历[生成 XML 架构](building-xml-schemas.md)主题中创建的客户架构。</span><span class="sxs-lookup"><span data-stu-id="0466a-117">The code example that follows demonstrates traversing the customer schema created in the [Building XML Schemas](building-xml-schemas.md) topic.</span></span> <span data-ttu-id="0466a-118">代码示例演示如何使用上述集合遍历架构并将架构中的所有元素和属性写入控制台。</span><span class="sxs-lookup"><span data-stu-id="0466a-118">The code example demonstrates traversing the schema using the collections described above and writes all the elements and attributes in the schema to the console.</span></span>

<span data-ttu-id="0466a-119">示例通过下列步骤遍历客户架构。</span><span class="sxs-lookup"><span data-stu-id="0466a-119">The sample traverses the customer schema in the following steps.</span></span>

1. <span data-ttu-id="0466a-120">将客户架构添加到新的 <xref:System.Xml.Schema.XmlSchemaSet> 对象并进行编译。</span><span class="sxs-lookup"><span data-stu-id="0466a-120">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="0466a-121">在读取或编译架构时遇到的任何架构验证警告和错误由 <xref:System.Xml.Schema.ValidationEventHandler> 委托进行处理。</span><span class="sxs-lookup"><span data-stu-id="0466a-121">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>

2. <span data-ttu-id="0466a-122">通过循环访问 <xref:System.Xml.Schema.XmlSchema> 属性，从 <xref:System.Xml.Schema.XmlSchemaSet> 中检索已编译的 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 对象。</span><span class="sxs-lookup"><span data-stu-id="0466a-122">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="0466a-123">因为架构已编译，所以，可以访问后架构编译信息集 (PSCI) 属性。</span><span class="sxs-lookup"><span data-stu-id="0466a-123">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>

3. <span data-ttu-id="0466a-124">在将每个元素的名称写入控制台的后架构编译 <xref:System.Xml.Schema.XmlSchemaElement> 集合的 <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> 集合中循环访问每个 <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="0466a-124">Iterates over each <xref:System.Xml.Schema.XmlSchemaElement> in the <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> collection of the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection writing the name of each element to the console.</span></span>

4. <span data-ttu-id="0466a-125">使用 `Customer` 类获取 <xref:System.Xml.Schema.XmlSchemaComplexType> 元素的复杂类型。</span><span class="sxs-lookup"><span data-stu-id="0466a-125">Gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>

5. <span data-ttu-id="0466a-126">如果复杂类型具有任何属性，请获取 <xref:System.Collections.IDictionaryEnumerator> 以循环访问每个 <xref:System.Xml.Schema.XmlSchemaAttribute> 并将其名称写入控制台。</span><span class="sxs-lookup"><span data-stu-id="0466a-126">If the complex type has any attributes, gets an <xref:System.Collections.IDictionaryEnumerator> to enumerate over each <xref:System.Xml.Schema.XmlSchemaAttribute> and writes its name to the console.</span></span>

6. <span data-ttu-id="0466a-127">使用 <xref:System.Xml.Schema.XmlSchemaSequence> 类获取复杂类型的序列粒子。</span><span class="sxs-lookup"><span data-stu-id="0466a-127">Gets the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>

7. <span data-ttu-id="0466a-128">在将每个子元素的名称写入控制台的 <xref:System.Xml.Schema.XmlSchemaElement> 集合中循环访问每个 <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="0466a-128">Iterates over each <xref:System.Xml.Schema.XmlSchemaElement> in the <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> collection writing the name of each child element to the console.</span></span>

<span data-ttu-id="0466a-129">以下是完整的代码示例。</span><span class="sxs-lookup"><span data-stu-id="0466a-129">The following is the complete code example.</span></span>

[!code-cpp[XmlSchemaTraverseExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaTraverseExample/CPP/XmlSchemaTraverseExample.cpp#1)]
[!code-csharp[XmlSchemaTraverseExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaTraverseExample/CS/XmlSchemaTraverseExample.cs#1)]
[!code-vb[XmlSchemaTraverseExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaTraverseExample/VB/XmlSchemaTraverseExample.vb#1)]

<span data-ttu-id="0466a-130">如果是用户定义的简单类型或复杂类型，<xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A?displayProperty=nameWithType> 属性可以为 <xref:System.Xml.Schema.XmlSchemaSimpleType> 或 <xref:System.Xml.Schema.XmlSchemaComplexType>。</span><span class="sxs-lookup"><span data-stu-id="0466a-130">The <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A?displayProperty=nameWithType> property can be <xref:System.Xml.Schema.XmlSchemaSimpleType>, or <xref:System.Xml.Schema.XmlSchemaComplexType> if it is a user-defined simple type or a complex type.</span></span> <span data-ttu-id="0466a-131">如果是 W3C XML 架构建议中定义的一个内置数据类型，此属性也可以为 <xref:System.Xml.Schema.XmlSchemaDatatype>。</span><span class="sxs-lookup"><span data-stu-id="0466a-131">It can also be <xref:System.Xml.Schema.XmlSchemaDatatype> if it is one of the built-in datatypes defined in the W3C XML Schema Recommendation.</span></span> <span data-ttu-id="0466a-132">在客户架构中，<xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> 元素的 `Customer` 为 <xref:System.Xml.Schema.XmlSchemaComplexType>，`FirstName` 和 `LastName` 元素为 <xref:System.Xml.Schema.XmlSchemaSimpleType>。</span><span class="sxs-lookup"><span data-stu-id="0466a-132">In the customer schema, the <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> of the `Customer` element is <xref:System.Xml.Schema.XmlSchemaComplexType>, and the `FirstName` and `LastName` elements are <xref:System.Xml.Schema.XmlSchemaSimpleType>.</span></span>

<span data-ttu-id="0466a-133">[生成 XML 架构](building-xml-schemas.md)主题中的代码示例使用了 <xref:System.Xml.Schema.XmlSchemaComplexType.Attributes%2A?displayProperty=nameWithType> 集合，将属性 `CustomerId` 添加到 `Customer` 元素。</span><span class="sxs-lookup"><span data-stu-id="0466a-133">The code example in the [Building XML Schemas](building-xml-schemas.md) topic used the <xref:System.Xml.Schema.XmlSchemaComplexType.Attributes%2A?displayProperty=nameWithType> collection to add the attribute `CustomerId` to the `Customer` element.</span></span> <span data-ttu-id="0466a-134">此属性是前架构编译属性。</span><span class="sxs-lookup"><span data-stu-id="0466a-134">This is a pre-schema-compilation property.</span></span> <span data-ttu-id="0466a-135">对应的后架构编译信息集属性为 <xref:System.Xml.Schema.XmlSchemaComplexType.AttributeUses%2A?displayProperty=nameWithType> 集合，该集合包含复杂类型的所有属性，包括通过类型派生继承的属性。</span><span class="sxs-lookup"><span data-stu-id="0466a-135">The corresponding Post-Schema-Compilation-Infoset property is the <xref:System.Xml.Schema.XmlSchemaComplexType.AttributeUses%2A?displayProperty=nameWithType> collection, which holds all the attributes of the complex type, including the ones that are inherited through type derivation.</span></span>

## <a name="see-also"></a><span data-ttu-id="0466a-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="0466a-136">See also</span></span>

- [<span data-ttu-id="0466a-137">XML 架构对象模型概述</span><span class="sxs-lookup"><span data-stu-id="0466a-137">XML Schema Object Model Overview</span></span>](xml-schema-object-model-overview.md)
- [<span data-ttu-id="0466a-138">读取和编写 XML 架构</span><span class="sxs-lookup"><span data-stu-id="0466a-138">Reading and Writing XML Schemas</span></span>](reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="0466a-139">生成 XML 架构</span><span class="sxs-lookup"><span data-stu-id="0466a-139">Building XML Schemas</span></span>](building-xml-schemas.md)
- [<span data-ttu-id="0466a-140">编辑 XML 架构</span><span class="sxs-lookup"><span data-stu-id="0466a-140">Editing XML Schemas</span></span>](editing-xml-schemas.md)
- [<span data-ttu-id="0466a-141">包含或导入 XML 架构</span><span class="sxs-lookup"><span data-stu-id="0466a-141">Including or Importing XML Schemas</span></span>](including-or-importing-xml-schemas.md)
- [<span data-ttu-id="0466a-142">用于编译架构的 XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="0466a-142">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="0466a-143">后架构编译信息集</span><span class="sxs-lookup"><span data-stu-id="0466a-143">Post-Schema Compilation Infoset</span></span>](post-schema-compilation-infoset.md)

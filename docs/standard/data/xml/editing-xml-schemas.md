---
title: 编辑 XML 架构
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fa09c8e5-c2b9-49d2-bb0d-40330cd13e4d
ms.openlocfilehash: b309c390ede3afc38122188337fa0dc3336e3ad5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292054"
---
# <a name="editing-xml-schemas"></a><span data-ttu-id="7dad9-102">编辑 XML 架构</span><span class="sxs-lookup"><span data-stu-id="7dad9-102">Editing XML Schemas</span></span>

<span data-ttu-id="7dad9-103">编辑 XML 架构是架构对象模型 (SOM) 最重要的功能之一。</span><span class="sxs-lookup"><span data-stu-id="7dad9-103">Editing an XML schema is one of the most important features of the Schema Object Model (SOM).</span></span> <span data-ttu-id="7dad9-104">SOM 的所有前架构编译属性均可以用于更改 XML 架构中的现有值。</span><span class="sxs-lookup"><span data-stu-id="7dad9-104">All of the pre-schema-compilation properties of the SOM can be used to change the existing values in an XML schema.</span></span> <span data-ttu-id="7dad9-105">然后，可以重新编译 XML 架构以反映更改。</span><span class="sxs-lookup"><span data-stu-id="7dad9-105">The XML schema can then be recompiled to reflect the changes.</span></span>

<span data-ttu-id="7dad9-106">编辑加载到 SOM 中的架构的第一步是遍历架构。</span><span class="sxs-lookup"><span data-stu-id="7dad9-106">The first step in editing a schema loaded into the SOM is to traverse the schema.</span></span> <span data-ttu-id="7dad9-107">在尝试编辑架构之前，应熟悉如何使用 SOM API 遍历架构。</span><span class="sxs-lookup"><span data-stu-id="7dad9-107">You should be familiar with traversing a schema using the SOM API before you attempt to edit a schema.</span></span> <span data-ttu-id="7dad9-108">还应熟悉后架构编译信息集 (PSCI) 的前架构编译属性和后架构编译属性。</span><span class="sxs-lookup"><span data-stu-id="7dad9-108">You should also be familiar with the pre- and post-schema-compilation properties of the Post-Schema-Compilation-Infoset (PSCI).</span></span>

## <a name="editing-an-xml-schema"></a><span data-ttu-id="7dad9-109">编辑 XML 架构</span><span class="sxs-lookup"><span data-stu-id="7dad9-109">Editing an XML Schema</span></span>

<span data-ttu-id="7dad9-110">此部分中收录了两个代码示例，均编辑[生成 XML 架构](building-xml-schemas.md)主题中创建的客户架构。</span><span class="sxs-lookup"><span data-stu-id="7dad9-110">In this section, two code examples are provided, both of which edit the customer schema created in the [Building XML Schemas](building-xml-schemas.md) topic.</span></span> <span data-ttu-id="7dad9-111">第一个代码示例向 `PhoneNumber` 元素中添加新的 `Customer` 元素，第二个代码示例向 `Title` 元素中添加新的 `FirstName` 属性。</span><span class="sxs-lookup"><span data-stu-id="7dad9-111">The first code example adds a new `PhoneNumber` element to the `Customer` element and the second code example adds a new `Title` attribute to the `FirstName` element.</span></span> <span data-ttu-id="7dad9-112">第一个示例还使用后架构编译 <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> 集合遍历客户架构，而第二个代码示例使用前架构编译 <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> 集合遍历客户架构。</span><span class="sxs-lookup"><span data-stu-id="7dad9-112">The first sample also uses the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection as the means of traversing the customer schema while the second code example uses the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>

### <a name="phonenumber-element-example"></a><span data-ttu-id="7dad9-113">PhoneNumber 元素示例</span><span class="sxs-lookup"><span data-stu-id="7dad9-113">PhoneNumber Element Example</span></span>

<span data-ttu-id="7dad9-114">第一个代码示例向客户架构的 `PhoneNumber` 元素中添加新的 `Customer` 元素。</span><span class="sxs-lookup"><span data-stu-id="7dad9-114">This first code example adds a new `PhoneNumber` element to the `Customer` element of the customer schema.</span></span> <span data-ttu-id="7dad9-115">代码示例通过下列步骤编辑客户架构。</span><span class="sxs-lookup"><span data-stu-id="7dad9-115">The code example edits the customer schema in the following steps.</span></span>

1. <span data-ttu-id="7dad9-116">将客户架构添加到新的 <xref:System.Xml.Schema.XmlSchemaSet> 对象并进行编译。</span><span class="sxs-lookup"><span data-stu-id="7dad9-116">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="7dad9-117">在读取或编译架构时遇到的任何架构验证警告和错误由 <xref:System.Xml.Schema.ValidationEventHandler> 委托进行处理。</span><span class="sxs-lookup"><span data-stu-id="7dad9-117">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>

2. <span data-ttu-id="7dad9-118">通过循环访问 <xref:System.Xml.Schema.XmlSchema> 属性，从 <xref:System.Xml.Schema.XmlSchemaSet> 中检索已编译的 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 对象。</span><span class="sxs-lookup"><span data-stu-id="7dad9-118">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="7dad9-119">因为架构已编译，所以，可以访问后架构编译信息集 (PSCI) 属性。</span><span class="sxs-lookup"><span data-stu-id="7dad9-119">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>

3. <span data-ttu-id="7dad9-120">使用 `PhoneNumber` 类创建 <xref:System.Xml.Schema.XmlSchemaElement> 元素，使用 `xs:string` 和 <xref:System.Xml.Schema.XmlSchemaSimpleType> 类创建 <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> 简单类型限制，将模式方面添加到限制的 <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> 属性，然后将限制添加到简单类型的 <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> 并将简单类型添加到 <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> 元素的 `PhoneNumber`。</span><span class="sxs-lookup"><span data-stu-id="7dad9-120">Creates the `PhoneNumber` element using the <xref:System.Xml.Schema.XmlSchemaElement> class, the `xs:string` simple type restriction using the <xref:System.Xml.Schema.XmlSchemaSimpleType> and <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> classes, adds a pattern facet to the <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> property of the restriction, and adds the restriction to the <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> property of the simple type and the simple type to the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> of the `PhoneNumber` element.</span></span>

4. <span data-ttu-id="7dad9-121">在后架构编译 <xref:System.Xml.Schema.XmlSchemaElement> 集合的 <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> 集合中循环访问每个 <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="7dad9-121">Iterates over each <xref:System.Xml.Schema.XmlSchemaElement> in the <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> collection of the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span>

5. <span data-ttu-id="7dad9-122">如果元素的 <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> 为 `"Customer"`，请使用 `Customer` 类获取 <xref:System.Xml.Schema.XmlSchemaComplexType> 元素的复杂类型并使用 <xref:System.Xml.Schema.XmlSchemaSequence> 类获取复杂类型的序列粒子。</span><span class="sxs-lookup"><span data-stu-id="7dad9-122">If the <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> of the element is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>

6. <span data-ttu-id="7dad9-123">使用序列的前架构编译 `PhoneNumber` 集合将新的 `FirstName` 元素添加到包含现有 `LastName` 和 <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> 元素的序列中。</span><span class="sxs-lookup"><span data-stu-id="7dad9-123">Adds the new `PhoneNumber` element to the sequence containing the existing `FirstName` and `LastName` elements using the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> collection of the sequence.</span></span>

7. <span data-ttu-id="7dad9-124">最后，使用 <xref:System.Xml.Schema.XmlSchema> 类的 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> 和 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> 方法重新处理并编译已修改的 <xref:System.Xml.Schema.XmlSchemaSet> 对象并将其写入控制台。</span><span class="sxs-lookup"><span data-stu-id="7dad9-124">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>

<span data-ttu-id="7dad9-125">以下是完整的代码示例。</span><span class="sxs-lookup"><span data-stu-id="7dad9-125">The following is the complete code example.</span></span>

[!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
[!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
[!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]

<span data-ttu-id="7dad9-126">下面展示了[生成 XML 架构](building-xml-schemas.md)主题中创建的已修改客户架构。</span><span class="sxs-lookup"><span data-stu-id="7dad9-126">The following is the modified customer schema created in the [Building XML Schemas](building-xml-schemas.md) topic.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="Customer">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="FirstName" type="xs:string" />
        <xs:element name="LastName" type="tns:LastNameType" />
        <xs:element name="PhoneNumber">           <xs:simpleType>             <xs:restriction base="xs:string">               <xs:pattern value="\d{3}-\d{3}-\d(4)" />             </xs:restriction>           </xs:simpleType>         </xs:element>
      </xs:sequence>
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" />
    </xs:complexType>
  </xs:element>
  <xs:simpleType name="LastNameType">
    <xs:restriction base="xs:string">
      <xs:maxLength value="20" />
    </xs:restriction>
  </xs:simpleType>
</xs:schema>
```

### <a name="title-attribute-example"></a><span data-ttu-id="7dad9-127">Title 属性示例</span><span class="sxs-lookup"><span data-stu-id="7dad9-127">Title Attribute Example</span></span>

<span data-ttu-id="7dad9-128">第二个代码示例向客户架构的 `Title` 元素中添加新的 `FirstName` 属性。</span><span class="sxs-lookup"><span data-stu-id="7dad9-128">This second code example, adds a new `Title` attribute to the `FirstName` element of the customer schema.</span></span> <span data-ttu-id="7dad9-129">在第一个代码示例中，`FirstName` 元素的类型为 `xs:string`。</span><span class="sxs-lookup"><span data-stu-id="7dad9-129">In the first code example, the type of the `FirstName` element is `xs:string`.</span></span> <span data-ttu-id="7dad9-130">为了使 `FirstName` 元素包含属性以及字符串内容，其类型必须使用简单内容扩展内容模型更改为复杂类型。</span><span class="sxs-lookup"><span data-stu-id="7dad9-130">For the `FirstName` element to have an attribute along with string content, its type must be changed to a complex type with a simple content extension content model.</span></span>

<span data-ttu-id="7dad9-131">代码示例通过下列步骤编辑客户架构。</span><span class="sxs-lookup"><span data-stu-id="7dad9-131">The code example edits the customer schema in the following steps.</span></span>

1. <span data-ttu-id="7dad9-132">将客户架构添加到新的 <xref:System.Xml.Schema.XmlSchemaSet> 对象并进行编译。</span><span class="sxs-lookup"><span data-stu-id="7dad9-132">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="7dad9-133">在读取或编译架构时遇到的任何架构验证警告和错误由 <xref:System.Xml.Schema.ValidationEventHandler> 委托进行处理。</span><span class="sxs-lookup"><span data-stu-id="7dad9-133">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>

2. <span data-ttu-id="7dad9-134">通过循环访问 <xref:System.Xml.Schema.XmlSchema> 属性，从 <xref:System.Xml.Schema.XmlSchemaSet> 中检索已编译的 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 对象。</span><span class="sxs-lookup"><span data-stu-id="7dad9-134">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="7dad9-135">因为架构已编译，所以，可以访问后架构编译信息集 (PSCI) 属性。</span><span class="sxs-lookup"><span data-stu-id="7dad9-135">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>

3. <span data-ttu-id="7dad9-136">使用 `FirstName` 类为 <xref:System.Xml.Schema.XmlSchemaComplexType> 元素创建新的复杂类型。</span><span class="sxs-lookup"><span data-stu-id="7dad9-136">Creates a new complex type for the `FirstName` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>

4. <span data-ttu-id="7dad9-137">使用 `xs:string` 和 <xref:System.Xml.Schema.XmlSchemaSimpleContent> 类创建新的简单内容扩展，基类型为 <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension>。</span><span class="sxs-lookup"><span data-stu-id="7dad9-137">Creates a new simple content extension, with a base type of `xs:string`, using the <xref:System.Xml.Schema.XmlSchemaSimpleContent> and <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> classes.</span></span>

5. <span data-ttu-id="7dad9-138">使用 `Title` 类创建新的 <xref:System.Xml.Schema.XmlSchemaAttribute> 属性，<xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> 为 `xs:string`，并将该属性添加到简单内容扩展。</span><span class="sxs-lookup"><span data-stu-id="7dad9-138">Creates the new `Title` attribute using the <xref:System.Xml.Schema.XmlSchemaAttribute> class, with a <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> of `xs:string` and adds the attribute to the simple content extension.</span></span>

6. <span data-ttu-id="7dad9-139">将简单内容的内容模型设置为简单内容扩展，将复杂类型的内容模型设置为简单内容。</span><span class="sxs-lookup"><span data-stu-id="7dad9-139">Sets the content model of the simple content to the simple content extension and the content model of the complex type to the simple content.</span></span>

7. <span data-ttu-id="7dad9-140">将新的复杂类型添加到前架构编译 <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> 集合。</span><span class="sxs-lookup"><span data-stu-id="7dad9-140">Adds the new complex type to the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>

8. <span data-ttu-id="7dad9-141">在前架构编译 <xref:System.Xml.Schema.XmlSchemaObject> 集合中循环访问每个 <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="7dad9-141">Iterates over each <xref:System.Xml.Schema.XmlSchemaObject> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>

> [!NOTE]
> <span data-ttu-id="7dad9-142">因为 `FirstName` 元素不是架构中的全局元素，所以，不能在 <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> 或 <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> 集合中使用。</span><span class="sxs-lookup"><span data-stu-id="7dad9-142">Because the `FirstName` element is not a global element in the schema, it is not available in the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> or <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collections.</span></span> <span data-ttu-id="7dad9-143">代码示例通过首先定位 `FirstName` 元素来定位 `Customer` 元素。</span><span class="sxs-lookup"><span data-stu-id="7dad9-143">The code example locates the `FirstName` element by first locating the `Customer` element.</span></span>
>
> <span data-ttu-id="7dad9-144">第一个代码示例使用后架构编译 <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> 集合遍历了架构。</span><span class="sxs-lookup"><span data-stu-id="7dad9-144">The first code example traversed the schema using the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span> <span data-ttu-id="7dad9-145">在此示例中，前架构编译 <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> 集合用于遍历架构。</span><span class="sxs-lookup"><span data-stu-id="7dad9-145">In this sample, the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection is used to traverse the schema.</span></span> <span data-ttu-id="7dad9-146">尽管两个集合均提供对架构中的全局元素的访问，但是循环访问 <xref:System.Xml.Schema.XmlSchema.Items%2A> 集合使用的时间更长，因为必须循环访问架构中的所有全局元素，没有任何 PSCI 属性。</span><span class="sxs-lookup"><span data-stu-id="7dad9-146">While both collections provide access to the global elements in the schema, iterating through the <xref:System.Xml.Schema.XmlSchema.Items%2A> collection is more time consuming because you must iterate over all global elements in the schema and it does not have any PSCI properties.</span></span> <span data-ttu-id="7dad9-147">PSCI 集合（<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>、<xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>、<xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType> 等）提供对其全局元素、属性和类型及其 PSCI 属性的直接访问。</span><span class="sxs-lookup"><span data-stu-id="7dad9-147">The PSCI collections (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>, and so on) provide direct access to their global elements, attributes, and types and their PSCI properties.</span></span>

1. <span data-ttu-id="7dad9-148">如果 <xref:System.Xml.Schema.XmlSchemaObject> 为元素，该元素的 <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> 为 `"Customer"`，请使用 `Customer` 类获取 <xref:System.Xml.Schema.XmlSchemaComplexType> 元素的复杂类型并使用 <xref:System.Xml.Schema.XmlSchemaSequence> 类获取复杂类型的序列粒子。</span><span class="sxs-lookup"><span data-stu-id="7dad9-148">If the <xref:System.Xml.Schema.XmlSchemaObject> is an element, whose <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>

2. <span data-ttu-id="7dad9-149">在前架构编译 <xref:System.Xml.Schema.XmlSchemaParticle> 集合中循环访问每个 <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="7dad9-149">Iterates over each <xref:System.Xml.Schema.XmlSchemaParticle> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> collection.</span></span>

3. <span data-ttu-id="7dad9-150">如果 <xref:System.Xml.Schema.XmlSchemaParticle> 为元素，该元素的 <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> 为 `"FirstName"`，请将 <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> 元素的 `FirstName` 设置为新的 `FirstName` 复杂类型。</span><span class="sxs-lookup"><span data-stu-id="7dad9-150">If the <xref:System.Xml.Schema.XmlSchemaParticle> is an element, who's <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"FirstName"`, sets the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> of the `FirstName` element to the new `FirstName` complex type.</span></span>

4. <span data-ttu-id="7dad9-151">最后，使用 <xref:System.Xml.Schema.XmlSchema> 类的 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> 和 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> 方法重新处理并编译已修改的 <xref:System.Xml.Schema.XmlSchemaSet> 对象并将其写入控制台。</span><span class="sxs-lookup"><span data-stu-id="7dad9-151">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>

<span data-ttu-id="7dad9-152">以下是完整的代码示例。</span><span class="sxs-lookup"><span data-stu-id="7dad9-152">The following is the complete code example.</span></span>

[!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
[!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
[!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]

<span data-ttu-id="7dad9-153">下面展示了[生成 XML 架构](building-xml-schemas.md)主题中创建的已修改客户架构。</span><span class="sxs-lookup"><span data-stu-id="7dad9-153">The following is the modified customer schema created in the [Building XML Schemas](building-xml-schemas.md) topic.</span></span>

```xml
<?xml version="1.0" encoding=" utf-8"?>
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="Customer">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="FirstName" type="tns:FirstNameComplexType" />
        <xs:element name="LastName" type="tns:LastNameType" />
      </xs:sequence>
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" />
    </xs:complexType>
  </xs:element>
  <xs:simpleType name="LastNameType">
    <xs:restriction base="xs:string">
      <xs:maxLength value="20" />
    </xs:restriction>
  </xs:simpleType>
  <xs:complexType name="FirstNameComplexType">     <xs:simpleContent>       <xs:extension base="xs:string">         <xs:attribute name="Title" type="xs:string" />       </xs:extension>     </xs:simpleContent>   </xs:complexType>
</xs:schema>
```

## <a name="see-also"></a><span data-ttu-id="7dad9-154">请参阅</span><span class="sxs-lookup"><span data-stu-id="7dad9-154">See also</span></span>

- [<span data-ttu-id="7dad9-155">XML 架构对象模型概述</span><span class="sxs-lookup"><span data-stu-id="7dad9-155">XML Schema Object Model Overview</span></span>](xml-schema-object-model-overview.md)
- [<span data-ttu-id="7dad9-156">读取和编写 XML 架构</span><span class="sxs-lookup"><span data-stu-id="7dad9-156">Reading and Writing XML Schemas</span></span>](reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="7dad9-157">生成 XML 架构</span><span class="sxs-lookup"><span data-stu-id="7dad9-157">Building XML Schemas</span></span>](building-xml-schemas.md)
- [<span data-ttu-id="7dad9-158">遍历 XML 架构</span><span class="sxs-lookup"><span data-stu-id="7dad9-158">Traversing XML Schemas</span></span>](traversing-xml-schemas.md)
- [<span data-ttu-id="7dad9-159">包含或导入 XML 架构</span><span class="sxs-lookup"><span data-stu-id="7dad9-159">Including or Importing XML Schemas</span></span>](including-or-importing-xml-schemas.md)
- [<span data-ttu-id="7dad9-160">用于编译架构的 XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="7dad9-160">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="7dad9-161">后架构编译信息集</span><span class="sxs-lookup"><span data-stu-id="7dad9-161">Post-Schema Compilation Infoset</span></span>](post-schema-compilation-infoset.md)

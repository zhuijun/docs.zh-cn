---
title: 生成 XML 架构
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 8a5ea56c-0140-4b51-8997-875ae6a8e0cb
ms.openlocfilehash: adc1a10bb9acb14ee88589c13e28c49773e42100
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291586"
---
# <a name="building-xml-schemas"></a><span data-ttu-id="72cd4-102">生成 XML 架构</span><span class="sxs-lookup"><span data-stu-id="72cd4-102">Building XML Schemas</span></span>
<span data-ttu-id="72cd4-103"><xref:System.Xml.Schema?displayProperty=nameWithType> 命名空间中的类映射到万维网联合会 (W3C) XML 架构建议中定义的结构，可以用于在内存中生成 XML 架构。</span><span class="sxs-lookup"><span data-stu-id="72cd4-103">The classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace map to the structures defined in the World Wide Web Consortium (W3C) XML Schema Recommendation and can be used to build XML schemas in-memory.</span></span>  
  
## <a name="building-an-xml-schema"></a><span data-ttu-id="72cd4-104">生成 XML 架构</span><span class="sxs-lookup"><span data-stu-id="72cd4-104">Building an XML Schema</span></span>  
 <span data-ttu-id="72cd4-105">在下面的代码示例中，SOM API 用于在内存中生成客户 XML 架构。</span><span class="sxs-lookup"><span data-stu-id="72cd4-105">In the code examples that follow, the SOM API is used to build a customer XML schema in-memory.</span></span>  
  
### <a name="creating-element-and-attributes"></a><span data-ttu-id="72cd4-106">创建元素和属性</span><span class="sxs-lookup"><span data-stu-id="72cd4-106">Creating Element and Attributes</span></span>  
 <span data-ttu-id="72cd4-107">代码示例从下至上生成客户架构，先创建子元素、属性及其相应的类型，然后创建顶级元素。</span><span class="sxs-lookup"><span data-stu-id="72cd4-107">The code examples build the customer schema from the bottom up, creating the child elements, attributes, and their corresponding types first, and then the top-level elements.</span></span>  
  
 <span data-ttu-id="72cd4-108">在下面的代码示例中，客户架构的 `FirstName` 和 `LastName` 元素以及 `CustomerId` 属性使用 SOM 的 <xref:System.Xml.Schema.XmlSchemaElement> 和 <xref:System.Xml.Schema.XmlSchemaAttribute> 类创建。</span><span class="sxs-lookup"><span data-stu-id="72cd4-108">In the following code example, the `FirstName` and `LastName` elements, as well as the `CustomerId` attribute of the customer schema are created using the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes of the SOM.</span></span> <span data-ttu-id="72cd4-109">除了 <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> 和 <xref:System.Xml.Schema.XmlSchemaElement> 类的 <xref:System.Xml.Schema.XmlSchemaAttribute> 属性（对应于 XML 架构中 `<xs:element />` 和 `<xs:attribute />` 元素的“name”属性）之外，架构所允许的所有其他属性（`defaultValue`、`fixedValue`、`form` 等）在 <xref:System.Xml.Schema.XmlSchemaElement> 和 <xref:System.Xml.Schema.XmlSchemaAttribute> 类中均有对应的属性。</span><span class="sxs-lookup"><span data-stu-id="72cd4-109">Apart from the <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> properties of the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes, which correspond to the "name" attribute of the `<xs:element />` and `<xs:attribute />` elements in an XML schema, all other attributes allowed by the schema (`defaultValue`, `fixedValue`, `form`, and so on) have corresponding properties in the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#2)]
 [!code-csharp[XmlSchemaCreateExample#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#2)]
 [!code-vb[XmlSchemaCreateExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#2)]  
  
### <a name="creating-schema-types"></a><span data-ttu-id="72cd4-110">创建架构类型</span><span class="sxs-lookup"><span data-stu-id="72cd4-110">Creating Schema Types</span></span>  
 <span data-ttu-id="72cd4-111">元素和属性的内容通过其类型定义。</span><span class="sxs-lookup"><span data-stu-id="72cd4-111">The content of elements and attributes is defined by their types.</span></span> <span data-ttu-id="72cd4-112">要创建类型属于一种内置架构类型的元素和属性，<xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> 或 <xref:System.Xml.Schema.XmlSchemaElement> 类的 <xref:System.Xml.Schema.XmlSchemaAttribute> 属性应使用 <xref:System.Xml.XmlQualifiedName> 类设置该内置类型相应的限定名。</span><span class="sxs-lookup"><span data-stu-id="72cd4-112">To create elements and attributes whose types are one of the built-in schema types, the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes are set with the corresponding qualified name of the built-in type using the <xref:System.Xml.XmlQualifiedName> class.</span></span> <span data-ttu-id="72cd4-113">要为元素和属性创建用户定义类型，应使用 <xref:System.Xml.Schema.XmlSchemaSimpleType> 或 <xref:System.Xml.Schema.XmlSchemaComplexType> 类创建新的简单类型或复杂类型。</span><span class="sxs-lookup"><span data-stu-id="72cd4-113">To create a user-defined type for elements and attributes, a new simple or complex type is created using the <xref:System.Xml.Schema.XmlSchemaSimpleType> or <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="72cd4-114">要创建未命名的简单类型或复杂类型，并且属于元素或属性的匿名子级（只有简单类型适用于属性），应将 <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> 或 <xref:System.Xml.Schema.XmlSchemaElement> 类的 <xref:System.Xml.Schema.XmlSchemaAttribute> 属性设置为未命名的简单类型或复杂类型，而不是设置 <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> 或 <xref:System.Xml.Schema.XmlSchemaElement> 类的 <xref:System.Xml.Schema.XmlSchemaAttribute> 属性。</span><span class="sxs-lookup"><span data-stu-id="72cd4-114">To create unnamed simple or complex types that are anonymous children of an element or attribute (only simple types apply for attributes), set the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes to the unnamed simple or complex type, instead of the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes.</span></span>  
  
 <span data-ttu-id="72cd4-115">XML 架构允许通过限制从其他简单类型（内置或用户定义）派生的匿名和命名的简单类型，或作为其他简单类型的列表或联合构造的匿名和命名的简单类型。</span><span class="sxs-lookup"><span data-stu-id="72cd4-115">XML schemas allow both anonymous and named simple types to be derived by restriction from other simple types (built-in or user-defined) or constructed as a list or union of other simple types.</span></span> <span data-ttu-id="72cd4-116"><xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> 类用于通过限制内置 `xs:string` 类型来创建简单类型。</span><span class="sxs-lookup"><span data-stu-id="72cd4-116">The <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> class is used to create a simple type by restricting the built-in `xs:string` type.</span></span> <span data-ttu-id="72cd4-117">也可以使用 <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> 或 <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> 类创建列表或联合类型。</span><span class="sxs-lookup"><span data-stu-id="72cd4-117">You can also use the <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> or <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> classes to create list or union types.</span></span> <span data-ttu-id="72cd4-118"><xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> 属性表明属于简单类型限制、列表还是联合。</span><span class="sxs-lookup"><span data-stu-id="72cd4-118">The <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> property denotes whether it is a simple type restriction, list, or union.</span></span>  
  
 <span data-ttu-id="72cd4-119">在下面的代码示例中，`FirstName` 元素的类型是内置类型 `xs:string`，`LastName` 元素的类型是命名的简单类型，属于内置类型 `xs:string` 的限制，`MaxLength` 方面的值为 20，`CustomerId` 属性的类型是内置类型 `xs:positiveInteger`。</span><span class="sxs-lookup"><span data-stu-id="72cd4-119">In the following code example, the `FirstName` element's type is the built-in type `xs:string`, the `LastName` element's type is a named simple type that is a restriction of the built-in type `xs:string`, with a `MaxLength` facet value of 20, and the `CustomerId` attribute's type is the built-in type `xs:positiveInteger`.</span></span> <span data-ttu-id="72cd4-120">`Customer` 元素是匿名的复杂类型，其粒子是 `FirstName` 和 `LastName` 元素的序列，其属性包含 `CustomerId` 属性。</span><span class="sxs-lookup"><span data-stu-id="72cd4-120">The `Customer` element is an anonymous complex type whose particle is the sequence of the `FirstName` and `LastName` elements and whose attributes contains the `CustomerId` attribute.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="72cd4-121">也可以使用 <xref:System.Xml.Schema.XmlSchemaChoice> 或 <xref:System.Xml.Schema.XmlSchemaAll> 类作为复杂类型的粒子，以复制 `<xs:choice />` 或 `<xs:all />` 语义。</span><span class="sxs-lookup"><span data-stu-id="72cd4-121">You can also use the <xref:System.Xml.Schema.XmlSchemaChoice> or <xref:System.Xml.Schema.XmlSchemaAll> classes as the particle of the complex type to replicate `<xs:choice />` or `<xs:all />` semantics.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#3](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#3)]
 [!code-csharp[XmlSchemaCreateExample#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#3)]
 [!code-vb[XmlSchemaCreateExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#3)]  
  
### <a name="creating-and-compiling-schemas"></a><span data-ttu-id="72cd4-122">创建和编译架构</span><span class="sxs-lookup"><span data-stu-id="72cd4-122">Creating and Compiling Schemas</span></span>  
 <span data-ttu-id="72cd4-123">现在，已使用 SOM API 在内存中创建了子元素和属性及其相应的类型以及顶级 `Customer` 元素。</span><span class="sxs-lookup"><span data-stu-id="72cd4-123">At this point, the child elements and attributes, their corresponding types, and the top-level `Customer` element have been created in-memory using the SOM API.</span></span> <span data-ttu-id="72cd4-124">在下面的代码示例中，架构元素使用 <xref:System.Xml.Schema.XmlSchema> 类创建，顶级元素和类型使用 <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> 属性添加到该元素，完整的架构使用 <xref:System.Xml.Schema.XmlSchemaSet> 类进行编译并写入控制台。</span><span class="sxs-lookup"><span data-stu-id="72cd4-124">In the following code example, the schema element is created using the <xref:System.Xml.Schema.XmlSchema> class, the top-level elements and types are added to it using the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> property and the complete schema is compiled using the <xref:System.Xml.Schema.XmlSchemaSet> class and written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#4)]
 [!code-csharp[XmlSchemaCreateExample#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#4)]
 [!code-vb[XmlSchemaCreateExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#4)]  
  
 <span data-ttu-id="72cd4-125"><xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> 方法针对 XML 架构的规则验证客户架构，并使后架构编译属性可用。</span><span class="sxs-lookup"><span data-stu-id="72cd4-125">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> method validates the customer schema against the rules for an XML schema and makes post-schema-compilation properties available.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="72cd4-126">SOM API 中的所有后架构编译属性与后架构验证信息集不同。</span><span class="sxs-lookup"><span data-stu-id="72cd4-126">All post-schema-compilation properties in the SOM API differ from the Post-Schema-Validation-Infoset.</span></span>  
  
 <span data-ttu-id="72cd4-127">添加到 <xref:System.Xml.Schema.ValidationEventHandler> 的 <xref:System.Xml.Schema.XmlSchemaSet> 是一个委托，用于调用回调方法 `ValidationCallback` 来处理架构验证警告和错误。</span><span class="sxs-lookup"><span data-stu-id="72cd4-127">The <xref:System.Xml.Schema.ValidationEventHandler> added to the <xref:System.Xml.Schema.XmlSchemaSet> is a delegate that calls the callback method `ValidationCallback` to handle schema validation warnings and errors.</span></span>  
  
 <span data-ttu-id="72cd4-128">以下是完整的代码示例以及写入控制台的客户架构。</span><span class="sxs-lookup"><span data-stu-id="72cd4-128">The following is the complete code example, and the customer schema written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#1)]
 [!code-csharp[XmlSchemaCreateExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#1)]
 [!code-vb[XmlSchemaCreateExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#1)]  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
   <xs:element name="Customer">  
      <xs:complexType>  
         <xs:sequence>  
            <xs:element name="FirstName" type="xs:string" />  
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
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="72cd4-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="72cd4-129">See also</span></span>

- [<span data-ttu-id="72cd4-130">XML 架构对象模型概述</span><span class="sxs-lookup"><span data-stu-id="72cd4-130">XML Schema Object Model Overview</span></span>](xml-schema-object-model-overview.md)
- [<span data-ttu-id="72cd4-131">读取和编写 XML 架构</span><span class="sxs-lookup"><span data-stu-id="72cd4-131">Reading and Writing XML Schemas</span></span>](reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="72cd4-132">遍历 XML 架构</span><span class="sxs-lookup"><span data-stu-id="72cd4-132">Traversing XML Schemas</span></span>](traversing-xml-schemas.md)
- [<span data-ttu-id="72cd4-133">编辑 XML 架构</span><span class="sxs-lookup"><span data-stu-id="72cd4-133">Editing XML Schemas</span></span>](editing-xml-schemas.md)
- [<span data-ttu-id="72cd4-134">包含或导入 XML 架构</span><span class="sxs-lookup"><span data-stu-id="72cd4-134">Including or Importing XML Schemas</span></span>](including-or-importing-xml-schemas.md)
- [<span data-ttu-id="72cd4-135">用于编译架构的 XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="72cd4-135">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="72cd4-136">后架构编译信息集</span><span class="sxs-lookup"><span data-stu-id="72cd4-136">Post-Schema Compilation Infoset</span></span>](post-schema-compilation-infoset.md)

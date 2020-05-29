---
title: XmlSchemaValidator 基于推送的验证
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 911d4460-dd91-4958-85b2-2ca3299f9ec6
ms.openlocfilehash: d5b2fe4325000023acc98580a2a6d014f56fecbd
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419104"
---
# <a name="xmlschemavalidator-push-based-validation"></a><span data-ttu-id="a5229-102">XmlSchemaValidator 基于推送的验证</span><span class="sxs-lookup"><span data-stu-id="a5229-102">XmlSchemaValidator Push-Based Validation</span></span>

<span data-ttu-id="a5229-103"><xref:System.Xml.Schema.XmlSchemaValidator> 类提供了一种高效、高性能的机制，通过基于推送的方式针对 XML 架构验证 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="a5229-103">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides an efficient, high-performance mechanism to validate XML data against XML schemas in a push-based manner.</span></span> <span data-ttu-id="a5229-104">例如，使用 <xref:System.Xml.Schema.XmlSchemaValidator> 类可以就地验证 XML 信息集，而不必将其序列化为 XML 文档，然后使用验证 XML 读取器重新分析该文档。</span><span class="sxs-lookup"><span data-stu-id="a5229-104">For example, the <xref:System.Xml.Schema.XmlSchemaValidator> class allows you to validate an XML infoset in-place without having to serialize it as an XML document and then reparse the document using a validating XML reader.</span></span>

<span data-ttu-id="a5229-105"><xref:System.Xml.Schema.XmlSchemaValidator> 类可以在一些高级方案中使用（例如在自定义的 XML 数据源上生成验证引擎），也可以作为生成验证 XML 写入器的一种方式。</span><span class="sxs-lookup"><span data-stu-id="a5229-105">The <xref:System.Xml.Schema.XmlSchemaValidator> class can be used in advanced scenarios such as building validation engines over custom XML data sources or as a way to build a validating XML writer.</span></span>

<span data-ttu-id="a5229-106">以下示例使用 <xref:System.Xml.Schema.XmlSchemaValidator> 类针对 `contosoBooks.xml` 架构验证 `contosoBooks.xsd` 文件。</span><span class="sxs-lookup"><span data-stu-id="a5229-106">The following is an example of using the <xref:System.Xml.Schema.XmlSchemaValidator> class to validate the `contosoBooks.xml` file against the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="a5229-107">该示例使用 <xref:System.Xml.Serialization.XmlSerializer> 类反序列化 `contosoBooks.xml` 文件，并将节点的值传递给 <xref:System.Xml.Schema.XmlSchemaValidator> 类的方法。</span><span class="sxs-lookup"><span data-stu-id="a5229-107">The example uses the <xref:System.Xml.Serialization.XmlSerializer> class to deserialize the `contosoBooks.xml` file and pass the value of the nodes to the methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>

> [!NOTE]
> <span data-ttu-id="a5229-108">此示例在本主题的所有章节中使用。</span><span class="sxs-lookup"><span data-stu-id="a5229-108">This example is used throughout the sections of this topic.</span></span>

[!code-csharp[XmlSchemaValidatorExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaValidatorExamples/CS/XmlSchemaValidatorExamples.cs#1)]
[!code-vb[XmlSchemaValidatorExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaValidatorExamples/VB/XmlSchemaValidatorExamples.vb#1)]

<span data-ttu-id="a5229-109">该示例使用 `contosoBooks.xml` 文件作为输入。</span><span class="sxs-lookup"><span data-stu-id="a5229-109">The example takes the `contosoBooks.xml` file as input.</span></span>

[!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]

<span data-ttu-id="a5229-110">该示例还使用 `contosoBooks.xsd` 作为输入。</span><span class="sxs-lookup"><span data-stu-id="a5229-110">The example also takes the `contosoBooks.xsd` as an input.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" targetNamespace="http://www.contoso.com/books" xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <xs:element name="bookstore">
        <xs:complexType>
            <xs:sequence>
                <xs:element maxOccurs="unbounded" name="book">
                    <xs:complexType>
                        <xs:sequence>
                            <xs:element name="title" type="xs:string" />
                            <xs:element name="author">
                                <xs:complexType>
                                    <xs:sequence>
                                        <xs:element minOccurs="0" name="name" type="xs:string" />
                                        <xs:element minOccurs="0" name="first-name" type="xs:string" />
                                        <xs:element minOccurs="0" name="last-name" type="xs:string" />
                                    </xs:sequence>
                                </xs:complexType>
                            </xs:element>
                            <xs:element name="price" type="xs:decimal" />
                        </xs:sequence>
                        <xs:attribute name="genre" type="xs:string" use="required" />
                        <xs:attribute name="publicationdate" type="xs:date" use="required" />
                        <xs:attribute name="ISBN" type="xs:string" use="required" />
                    </xs:complexType>
                </xs:element>
            </xs:sequence>
        </xs:complexType>
    </xs:element>
</xs:schema>
```

## <a name="validating-xml-data-using-xmlschemavalidator"></a><span data-ttu-id="a5229-111">使用 XmlSchemaValidator 验证 XML 数据</span><span class="sxs-lookup"><span data-stu-id="a5229-111">Validating XML Data using XmlSchemaValidator</span></span>

<span data-ttu-id="a5229-112">要开始验证 XML 信息集，必须先使用 <xref:System.Xml.Schema.XmlSchemaValidator> 构造函数初始化 <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> 类的新实例。</span><span class="sxs-lookup"><span data-stu-id="a5229-112">To begin validating an XML infoset, you must first initialize a new instance of the <xref:System.Xml.Schema.XmlSchemaValidator> class using the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor.</span></span>

<span data-ttu-id="a5229-113"><xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> 构造函数使用 <xref:System.Xml.XmlNameTable>、<xref:System.Xml.Schema.XmlSchemaSet> 和 <xref:System.Xml.XmlNamespaceManager> 对象作为参数，同时也将 <xref:System.Xml.Schema.XmlSchemaValidationFlags> 值用作参数。</span><span class="sxs-lookup"><span data-stu-id="a5229-113">The <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor takes <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet>, and <xref:System.Xml.XmlNamespaceManager> objects as parameters as well as a <xref:System.Xml.Schema.XmlSchemaValidationFlags> value as a parameter.</span></span> <span data-ttu-id="a5229-114"><xref:System.Xml.XmlNameTable> 对象用于原子化众所周知的命名空间字符串，例如架构命名空间、XML 命名空间等，并在验证简单内容时传递给 <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="a5229-114">The <xref:System.Xml.XmlNameTable> object is used to atomize well-known namespace strings like the schema namespace, the XML namespace, and so on, and is passed to the <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> method while validating simple content.</span></span> <span data-ttu-id="a5229-115"><xref:System.Xml.Schema.XmlSchemaSet> 对象包含用于验证 XML 信息集的 XML 架构。</span><span class="sxs-lookup"><span data-stu-id="a5229-115">The <xref:System.Xml.Schema.XmlSchemaSet> object contains the XML schemas used to validate the XML infoset.</span></span> <span data-ttu-id="a5229-116"><xref:System.Xml.XmlNamespaceManager> 对象用于解析在验证期间遇到的命名空间。</span><span class="sxs-lookup"><span data-stu-id="a5229-116">The <xref:System.Xml.XmlNamespaceManager> object is used to resolve namespaces encountered during validation.</span></span> <span data-ttu-id="a5229-117"><xref:System.Xml.Schema.XmlSchemaValidationFlags> 值用于禁用验证的某些功能。</span><span class="sxs-lookup"><span data-stu-id="a5229-117">The <xref:System.Xml.Schema.XmlSchemaValidationFlags> value is used to disable certain features of validation.</span></span>

<span data-ttu-id="a5229-118">有关 <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> 构造函数的更多信息，请参见 <xref:System.Xml.Schema.XmlSchemaValidator> 类参考文档。</span><span class="sxs-lookup"><span data-stu-id="a5229-118">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="initializing-validation"></a><span data-ttu-id="a5229-119">初始化验证</span><span class="sxs-lookup"><span data-stu-id="a5229-119">Initializing Validation</span></span>

<span data-ttu-id="a5229-120">构造了 <xref:System.Xml.Schema.XmlSchemaValidator> 对象之后，有两个重载 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 方法可用于初始化 <xref:System.Xml.Schema.XmlSchemaValidator> 对象的状态。</span><span class="sxs-lookup"><span data-stu-id="a5229-120">After an <xref:System.Xml.Schema.XmlSchemaValidator> object has been constructed, there are two overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods used to initialize the state of the <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span> <span data-ttu-id="a5229-121">以下是这两个 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="a5229-121">The following are the two <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods.</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

<span data-ttu-id="a5229-122">默认的 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> 方法将 <xref:System.Xml.Schema.XmlSchemaValidator> 对象初始化为起始状态，使用 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> 作为参数的重载 <xref:System.Xml.Schema.XmlSchemaObject> 方法将 <xref:System.Xml.Schema.XmlSchemaValidator> 对象初始化为起始状态，以进行部分验证。</span><span class="sxs-lookup"><span data-stu-id="a5229-122">The default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state, and the overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state for partial validation.</span></span>

<span data-ttu-id="a5229-123">这两个 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 方法只能在构造了 <xref:System.Xml.Schema.XmlSchemaValidator> 对象之后或调用了 <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A> 之后立即调用。</span><span class="sxs-lookup"><span data-stu-id="a5229-123">Both <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods can only be called immediately after an <xref:System.Xml.Schema.XmlSchemaValidator> object has been constructed or after a call to <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.</span></span>

<span data-ttu-id="a5229-124">有关 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> 方法的示例，请参见简介中的示例。</span><span class="sxs-lookup"><span data-stu-id="a5229-124">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method, see the example in the introduction.</span></span> <span data-ttu-id="a5229-125">有关 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 方法的更多信息，请参见 <xref:System.Xml.Schema.XmlSchemaValidator> 类参考文档。</span><span class="sxs-lookup"><span data-stu-id="a5229-125">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="partial-validation"></a><span data-ttu-id="a5229-126">部分验证</span><span class="sxs-lookup"><span data-stu-id="a5229-126">Partial Validation</span></span>

<span data-ttu-id="a5229-127">使用 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> 作为参数的 <xref:System.Xml.Schema.XmlSchemaObject> 方法将 <xref:System.Xml.Schema.XmlSchemaValidator> 对象初始化为起始状态，以进行部分验证。</span><span class="sxs-lookup"><span data-stu-id="a5229-127">The <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state for partial validation.</span></span>

<span data-ttu-id="a5229-128">在以下示例中，使用 <xref:System.Xml.Schema.XmlSchemaObject> 方法对 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> 进行初始化，以进行部分验证。</span><span class="sxs-lookup"><span data-stu-id="a5229-128">In the following example, an <xref:System.Xml.Schema.XmlSchemaObject> is initialized for partial validation using the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a5229-129">在 `orderNumber` 对象的 <xref:System.Xml.XmlQualifiedName> 属性返回的 <xref:System.Xml.Schema.XmlSchemaObjectTable> 集合中，通过其中的 <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> 选择架构元素，来传递 <xref:System.Xml.Schema.XmlSchemaSet> 架构元素。</span><span class="sxs-lookup"><span data-stu-id="a5229-129">The `orderNumber` schema element is passed by selecting the schema element by <xref:System.Xml.XmlQualifiedName> in the <xref:System.Xml.Schema.XmlSchemaObjectTable> collection returned by the <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> object.</span></span> <span data-ttu-id="a5229-130">然后，<xref:System.Xml.Schema.XmlSchemaValidator> 对象验证这个特定的元素。</span><span class="sxs-lookup"><span data-stu-id="a5229-130">The <xref:System.Xml.Schema.XmlSchemaValidator> object then validates this specific element.</span></span>

```vb
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()
schemaSet.Add(Nothing, "schema.xsd")
schemaSet.Compile()
Dim nameTable As NameTable = New NameTable()
Dim manager As XmlNamespaceManager = New XmlNamespaceManager(nameTable)

Dim validator As XmlSchemaValidator = New XmlSchemaValidator(nameTable, schemaSet, manager, XmlSchemaValidationFlags.None)
validator.Initialize(schemaSet.GlobalElements.Item(New XmlQualifiedName("orderNumber")))

validator.ValidateElement("orderNumber", "", Nothing)
validator.ValidateEndOfAttributes(Nothing)
validator.ValidateText("123")
validator.ValidateEndElement(Nothing)
```

```csharp
XmlSchemaSet schemaSet = new XmlSchemaSet();
schemaSet.Add(null, "schema.xsd");
schemaSet.Compile();
NameTable nameTable = new NameTable();
XmlNamespaceManager manager = new XmlNamespaceManager(nameTable);

XmlSchemaValidator validator = new XmlSchemaValidator(nameTable, schemaSet, manager, XmlSchemaValidationFlags.None);
validator.Initialize(schemaSet.GlobalElements[new XmlQualifiedName("orderNumber")]);

validator.ValidateElement("orderNumber", "", null);
validator.ValidateEndOfAttributes(null);
validator.ValidateText("123");
validator.ValidateEndElement(null);
```

<span data-ttu-id="a5229-131">该示例使用以下 XML 架构作为输入。</span><span class="sxs-lookup"><span data-stu-id="a5229-131">The example takes the following XML schema as input.</span></span>

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="orderNumber" type="xs:int" />
</xs:schema>
```

<span data-ttu-id="a5229-132">有关 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 方法的更多信息，请参见 <xref:System.Xml.Schema.XmlSchemaValidator> 类参考文档。</span><span class="sxs-lookup"><span data-stu-id="a5229-132">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="adding-additional-schemas"></a><span data-ttu-id="a5229-133">添加其他架构</span><span class="sxs-lookup"><span data-stu-id="a5229-133">Adding Additional Schemas</span></span>

<span data-ttu-id="a5229-134"><xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> 类的 <xref:System.Xml.Schema.XmlSchemaValidator> 方法用于将 XML 架构添加到验证期间使用的架构集中。</span><span class="sxs-lookup"><span data-stu-id="a5229-134">The <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method of the <xref:System.Xml.Schema.XmlSchemaValidator> class is used to add an XML schema to the set of schemas used during validation.</span></span> <span data-ttu-id="a5229-135"><xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> 方法可以用于模拟在所验证的 XML 信息集中遇到内联 XML 架构的效果。</span><span class="sxs-lookup"><span data-stu-id="a5229-135">The <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method can be used to simulate the effect of encountering an inline XML schema in the XML infoset being validated.</span></span>

> [!NOTE]
> <span data-ttu-id="a5229-136"><xref:System.Xml.Schema.XmlSchema> 参数的目标命名空间无法与 <xref:System.Xml.Schema.XmlSchemaValidator> 对象已遇到的任何元素或属性的目标命名空间匹配。</span><span class="sxs-lookup"><span data-stu-id="a5229-136">The target namespace of the <xref:System.Xml.Schema.XmlSchema> parameter cannot match that of any element or attribute already encountered by the <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span>
>
> <span data-ttu-id="a5229-137">如果 <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> 值未作为参数传递给 <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> 构造函数，<xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> 方法不会执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="a5229-137">If the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> value was not passed as a parameter to the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor, the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method does nothing.</span></span>

<span data-ttu-id="a5229-138"><xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> 方法的结果取决于所验证的当前 XML 节点上下文。</span><span class="sxs-lookup"><span data-stu-id="a5229-138">The result of the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method is dependant on the current XML node context being validated.</span></span> <span data-ttu-id="a5229-139">有关验证上下文的更多信息，请参见本主题的“验证上下文”一节。</span><span class="sxs-lookup"><span data-stu-id="a5229-139">For more information about validation contexts, see the "Validation Context" section of this topic.</span></span>

<span data-ttu-id="a5229-140">有关 <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> 方法的更多信息，请参见 <xref:System.Xml.Schema.XmlSchemaValidator> 类参考文档。</span><span class="sxs-lookup"><span data-stu-id="a5229-140">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="validating-elements-attributes-and-content"></a><span data-ttu-id="a5229-141">验证元素、属性和内容</span><span class="sxs-lookup"><span data-stu-id="a5229-141">Validating Elements, Attributes, and Content</span></span>

<span data-ttu-id="a5229-142"><xref:System.Xml.Schema.XmlSchemaValidator> 类提供多种方法用于针对 XML 架构验证 XML 信息集中的元素、属性和内容。</span><span class="sxs-lookup"><span data-stu-id="a5229-142">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides several methods used to validate elements, attributes, and content in an XML infoset against XML schemas.</span></span> <span data-ttu-id="a5229-143">下表介绍每种方法。</span><span class="sxs-lookup"><span data-stu-id="a5229-143">The following table describes each of these methods.</span></span>

|<span data-ttu-id="a5229-144">方法</span><span class="sxs-lookup"><span data-stu-id="a5229-144">Method</span></span>|<span data-ttu-id="a5229-145">描述</span><span class="sxs-lookup"><span data-stu-id="a5229-145">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|<span data-ttu-id="a5229-146">在当前上下文中验证元素名。</span><span class="sxs-lookup"><span data-stu-id="a5229-146">Validates the element name in the current context.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|<span data-ttu-id="a5229-147">在当前元素上下文中验证属性，或针对作为参数传递给 <xref:System.Xml.Schema.XmlSchemaAttribute> 方法的 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 对象验证属性。</span><span class="sxs-lookup"><span data-stu-id="a5229-147">Validates the attribute in the current element context or against the <xref:System.Xml.Schema.XmlSchemaAttribute> object passed as a parameter to the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<span data-ttu-id="a5229-148">验证元素上下文中所有必需的属性是否已存在，并且 <xref:System.Xml.Schema.XmlSchemaValidator> 对象是否已准备好验证元素的子内容。</span><span class="sxs-lookup"><span data-stu-id="a5229-148">Verifies whether all the required attributes in the element context are present and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate the child content of the element.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|<span data-ttu-id="a5229-149">验证当前元素上下文中是否允许包含文本，并累积文本，以验证当前元素是否包含简单内容。</span><span class="sxs-lookup"><span data-stu-id="a5229-149">Validates whether text is allowed in the current element context, and accumulates the text for validation if the current element has simple content.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|<span data-ttu-id="a5229-150">验证当前元素上下文中是否允许包含空白，并累积空白，以验证当前元素是否包含简单内容。</span><span class="sxs-lookup"><span data-stu-id="a5229-150">Validates whether white-space is allowed in the current element context, and accumulates the white-space for validation whether the current element has simple content.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<span data-ttu-id="a5229-151">对于包含简单内容的元素，验证元素的文本内容是否符合其数据类型，对于包含复杂内容的元素，验证当前元素的内容是否完整。</span><span class="sxs-lookup"><span data-stu-id="a5229-151">Verifies whether the text content of the element is valid according to its data type for elements with simple content, and verifies whether the content of the current element is complete for elements with complex content.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<span data-ttu-id="a5229-152">跳过当前元素内容的验证并准备 <xref:System.Xml.Schema.XmlSchemaValidator> 对象以验证父元素的上下文中的内容。</span><span class="sxs-lookup"><span data-stu-id="a5229-152">Skips validation of the current element content and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate content in the parent element's context.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<span data-ttu-id="a5229-153">如果设置了 <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> 验证选项，结束验证并检查整个 XML 文档的标识约束。</span><span class="sxs-lookup"><span data-stu-id="a5229-153">Ends validation and checks identity constraints for the entire XML document if the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> validation option is set.</span></span>|

> [!NOTE]
> <span data-ttu-id="a5229-154"><xref:System.Xml.Schema.XmlSchemaValidator> 类包含已定义的状态转换，强制按顺序执行对上表中所述的每种方法的调用。</span><span class="sxs-lookup"><span data-stu-id="a5229-154">The <xref:System.Xml.Schema.XmlSchemaValidator> class has a defined state transition that enforces the sequence and occurrence of calls made to each of the methods described in the previous table.</span></span> <span data-ttu-id="a5229-155"><xref:System.Xml.Schema.XmlSchemaValidator> 类特定的状态转换在本主题的“XmlSchemaValidator 状态转换”一节中介绍。</span><span class="sxs-lookup"><span data-stu-id="a5229-155">The specific state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class is described in the "XmlSchemaValidator State Transition" section of this topic.</span></span>

<span data-ttu-id="a5229-156">有关用于验证 XML 信息集中的元素、属性和内容的方法的示例，请参见上一节中的示例。</span><span class="sxs-lookup"><span data-stu-id="a5229-156">For an example of the methods used to validate elements, attributes, and content in an XML infoset, see the example in the previous section.</span></span> <span data-ttu-id="a5229-157">有关这些方法的更多信息，请参见 <xref:System.Xml.Schema.XmlSchemaValidator> 类参考文档。</span><span class="sxs-lookup"><span data-stu-id="a5229-157">For more information about these methods, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="validating-content-using-an-xmlvaluegetter"></a><span data-ttu-id="a5229-158">使用 XmlValueGetter 编写内容</span><span class="sxs-lookup"><span data-stu-id="a5229-158">Validating Content Using an XmlValueGetter</span></span>

<span data-ttu-id="a5229-159"><xref:System.Xml.Schema.XmlValueGetter>`delegate` 可用于将属性、文本或空格节点的值传递为公共语言运行时 (CLR) 类型，与属性、文本或空格节点的 XML 架构定义语言 (XSD) 类型兼容。</span><span class="sxs-lookup"><span data-stu-id="a5229-159">The <xref:System.Xml.Schema.XmlValueGetter>`delegate` can be used to pass the value of attribute, text, or white-space nodes as a Common Language Runtime (CLR) types compatible with the XML Schema Definition Language (XSD) type of the attribute, text, or white-space node.</span></span> <span data-ttu-id="a5229-160">如果属性、文本或空格节点的 CLR 值已可用，<xref:System.Xml.Schema.XmlValueGetter>`delegate` 非常有用，这样就免去了将它转换为 `string` 并重新分析以供验证的成本。</span><span class="sxs-lookup"><span data-stu-id="a5229-160">An <xref:System.Xml.Schema.XmlValueGetter>`delegate` is useful if the CLR value of an attribute, text, or white-space node is already available, and avoids the cost of converting it to a `string` and then reparsing it again for validation.</span></span>

<span data-ttu-id="a5229-161"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>、<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> 和 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> 方法是重载方法，使用属性、文本或空白节点的值作为 `string` 或 <xref:System.Xml.Schema.XmlValueGetter>`delegate`。</span><span class="sxs-lookup"><span data-stu-id="a5229-161">The <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> methods are overloaded and accept the value of attribute, text, or white-space nodes as a `string` or <xref:System.Xml.Schema.XmlValueGetter>`delegate`.</span></span>

<span data-ttu-id="a5229-162"><xref:System.Xml.Schema.XmlSchemaValidator> 类的下列方法接受 <xref:System.Xml.Schema.XmlValueGetter>`delegate` 作为参数。</span><span class="sxs-lookup"><span data-stu-id="a5229-162">The following methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class accept an <xref:System.Xml.Schema.XmlValueGetter>`delegate` as a parameter.</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>

<span data-ttu-id="a5229-163">下面是从简介中的 <xref:System.Xml.Schema.XmlValueGetter> 类示例获取的示例 `delegate`<xref:System.Xml.Schema.XmlSchemaValidator>。</span><span class="sxs-lookup"><span data-stu-id="a5229-163">The following is an example <xref:System.Xml.Schema.XmlValueGetter>`delegate` taken from the <xref:System.Xml.Schema.XmlSchemaValidator> class example in the introduction.</span></span> <span data-ttu-id="a5229-164"><xref:System.Xml.Schema.XmlValueGetter>`delegate` 以 <xref:System.DateTime> 对象的形式返回属性的值。</span><span class="sxs-lookup"><span data-stu-id="a5229-164">The <xref:System.Xml.Schema.XmlValueGetter>`delegate` returns the value of an attribute as a <xref:System.DateTime> object.</span></span> <span data-ttu-id="a5229-165">要验证 <xref:System.DateTime> 返回的此 <xref:System.Xml.Schema.XmlValueGetter> 对象，<xref:System.Xml.Schema.XmlSchemaValidator> 对象先将其转换为属性数据类型的 ValueType（ValueType 是该 XSD 类型默认的 CLR 映射），然后检查转换后的值的各个方面。</span><span class="sxs-lookup"><span data-stu-id="a5229-165">To validate this <xref:System.DateTime> object returned by the <xref:System.Xml.Schema.XmlValueGetter>, the <xref:System.Xml.Schema.XmlSchemaValidator> object first converts it to the ValueType (ValueType is the default CLR mapping for the XSD type) for the data type of the attribute and then checks facets on the converted value.</span></span>

```vb
Shared dateTimeGetterContent As Object

Shared Function DateTimeGetterHandle() As Object
    Return dateTimeGetterContent
End Function

Shared Function DateTimeGetter(dateTime As DateTime) As XmlValueGetter
    dateTimeGetterContent = dateTime
    Return New XmlValueGetter(AddressOf DateTimeGetterHandle)
End Function
```

```csharp
static object dateTimeGetterContent;

static object DateTimeGetterHandle()
{
    return dateTimeGetterContent;
}

static XmlValueGetter DateTimeGetter(DateTime dateTime)
{
    dateTimeGetterContent = dateTime;
    return new XmlValueGetter(dateTimeGetterHandle);
}
```

<span data-ttu-id="a5229-166">有关 <xref:System.Xml.Schema.XmlValueGetter>`delegate` 的完整示例，请参见简介中的示例。</span><span class="sxs-lookup"><span data-stu-id="a5229-166">For a complete example of the <xref:System.Xml.Schema.XmlValueGetter>`delegate`, see the example in the introduction.</span></span> <span data-ttu-id="a5229-167">若要详细了解 <xref:System.Xml.Schema.XmlValueGetter>`delegate`，请参阅 <xref:System.Xml.Schema.XmlValueGetter> 和 <xref:System.Xml.Schema.XmlSchemaValidator> 类的参考文档。</span><span class="sxs-lookup"><span data-stu-id="a5229-167">For more information about the <xref:System.Xml.Schema.XmlValueGetter>`delegate`, see the <xref:System.Xml.Schema.XmlValueGetter>, and <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="post-schema-validation-information"></a><span data-ttu-id="a5229-168">后架构验证信息</span><span class="sxs-lookup"><span data-stu-id="a5229-168">Post-Schema-Validation-Information</span></span>

<span data-ttu-id="a5229-169"><xref:System.Xml.Schema.XmlSchemaInfo> 类表示通过 <xref:System.Xml.Schema.XmlSchemaValidator> 类验证的 XML 节点的一些后架构验证信息。</span><span class="sxs-lookup"><span data-stu-id="a5229-169">The <xref:System.Xml.Schema.XmlSchemaInfo> class represents some of the Post-Schema-Validation-Information of an XML node validated by the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span> <span data-ttu-id="a5229-170"><xref:System.Xml.Schema.XmlSchemaValidator> 类的各种方法使用 <xref:System.Xml.Schema.XmlSchemaInfo> 对象作为可选的 (`null`) `out` 参数。</span><span class="sxs-lookup"><span data-stu-id="a5229-170">Various methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class accept an <xref:System.Xml.Schema.XmlSchemaInfo> object as an optional, (`null`) `out` parameter.</span></span>

<span data-ttu-id="a5229-171">在成功地验证之后，<xref:System.Xml.Schema.XmlSchemaInfo> 对象的属性将使用验证结果进行设置。</span><span class="sxs-lookup"><span data-stu-id="a5229-171">Upon successful validation, properties of the <xref:System.Xml.Schema.XmlSchemaInfo> object are set with the results of the validation.</span></span> <span data-ttu-id="a5229-172">例如，使用 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> 方法成功地验证某个属性之后，<xref:System.Xml.Schema.XmlSchemaInfo> 对象的（如果指定）<xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>、<xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>、<xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A> 和 <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> 属性将使用验证结果进行设置。</span><span class="sxs-lookup"><span data-stu-id="a5229-172">For example, upon successful validation of an attribute using the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method, the <xref:System.Xml.Schema.XmlSchemaInfo> object's (if specified) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>, and <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> properties are set with the results of the validation.</span></span>

<span data-ttu-id="a5229-173">下列 <xref:System.Xml.Schema.XmlSchemaValidator> 类方法使用 <xref:System.Xml.Schema.XmlSchemaInfo> 对象作为输出参数。</span><span class="sxs-lookup"><span data-stu-id="a5229-173">The following <xref:System.Xml.Schema.XmlSchemaValidator> class methods accept an <xref:System.Xml.Schema.XmlSchemaInfo> object as an out parameter.</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>

<span data-ttu-id="a5229-174">有关 <xref:System.Xml.Schema.XmlSchemaInfo> 类的完整示例，请参见简介中的示例。</span><span class="sxs-lookup"><span data-stu-id="a5229-174">For a complete example of the <xref:System.Xml.Schema.XmlSchemaInfo> class, see the example in the introduction.</span></span> <span data-ttu-id="a5229-175">有关 <xref:System.Xml.Schema.XmlSchemaInfo> 类的更多信息，请参见 <xref:System.Xml.Schema.XmlSchemaInfo> 类参考文档。</span><span class="sxs-lookup"><span data-stu-id="a5229-175">For more information about the <xref:System.Xml.Schema.XmlSchemaInfo> class, see the <xref:System.Xml.Schema.XmlSchemaInfo> class reference documentation.</span></span>

### <a name="retrieving-expected-particles-attributes-and-unspecified-default-attributes"></a><span data-ttu-id="a5229-176">检索预计的粒子、属性和未指定的默认属性</span><span class="sxs-lookup"><span data-stu-id="a5229-176">Retrieving Expected Particles, Attributes, and Unspecified Default Attributes</span></span>

<span data-ttu-id="a5229-177"><xref:System.Xml.Schema.XmlSchemaValidator> 类提供 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>、<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 和 <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> 方法来检索当前验证上下文中预计的粒子、属性和未指定的默认属性。</span><span class="sxs-lookup"><span data-stu-id="a5229-177">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> methods to retrieve the expected particles, attributes, and unspecified default attributes in the current validation context.</span></span>

#### <a name="retrieving-expected-particles"></a><span data-ttu-id="a5229-178">检索预计的粒子</span><span class="sxs-lookup"><span data-stu-id="a5229-178">Retrieving Expected Particles</span></span>

<span data-ttu-id="a5229-179"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 方法返回一个 <xref:System.Xml.Schema.XmlSchemaParticle> 对象数组，包含当前元素上下文中预计的粒子。</span><span class="sxs-lookup"><span data-stu-id="a5229-179">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an array of <xref:System.Xml.Schema.XmlSchemaParticle> objects containing the expected particles in the current element context.</span></span> <span data-ttu-id="a5229-180"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 方法可以返回的有效粒子是 <xref:System.Xml.Schema.XmlSchemaElement> 和 <xref:System.Xml.Schema.XmlSchemaAny> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="a5229-180">The valid particles that can be returned by the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method are instances of the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAny> classes.</span></span>

<span data-ttu-id="a5229-181">如果内容模型的复合器是 `xs:sequence`，则只返回序列中的下一个粒子。</span><span class="sxs-lookup"><span data-stu-id="a5229-181">When the compositor for the content model is an `xs:sequence`, only the next particle in the sequence is returned.</span></span> <span data-ttu-id="a5229-182">如果内容模型的复合器是 `xs:all` 或 `xs:choice`，则返回当前元素上下文中可能出现的所有有效粒子。</span><span class="sxs-lookup"><span data-stu-id="a5229-182">If the compositor for the content model is an `xs:all` or an `xs:choice`, then all valid particles that could follow in the current element context are returned.</span></span>

> [!NOTE]
> <span data-ttu-id="a5229-183">如果 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 方法在调用 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 方法之后立即调用，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 方法将返回所有全局元素。</span><span class="sxs-lookup"><span data-stu-id="a5229-183">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called immediately after calling the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns all global elements.</span></span>

<span data-ttu-id="a5229-184">例如，在下面的 XML 架构定义语言 (XSD) 架构和 XML 文档中，在验证 `book` 元素之后，`book` 元素是当前的元素上下文。</span><span class="sxs-lookup"><span data-stu-id="a5229-184">For example, in the XML Schema Definition Language (XSD) schema and XML document that follow, after validating the `book` element, the `book` element is the current element context.</span></span> <span data-ttu-id="a5229-185"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 方法返回一个数组，包含表示 <xref:System.Xml.Schema.XmlSchemaElement> 元素的单个 `title` 对象。</span><span class="sxs-lookup"><span data-stu-id="a5229-185">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an array containing a single <xref:System.Xml.Schema.XmlSchemaElement> object representing the `title` element.</span></span> <span data-ttu-id="a5229-186">如果验证上下文是 `title` 元素，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 方法将返回一个空数组。</span><span class="sxs-lookup"><span data-stu-id="a5229-186">When the validation context is the `title` element, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an empty array.</span></span> <span data-ttu-id="a5229-187">如果 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 方法在验证了 `title` 元素之后但是在验证 `description` 元素之前调用，将返回一个数组，包含表示 <xref:System.Xml.Schema.XmlSchemaElement> 元素的单个 `description` 对象。</span><span class="sxs-lookup"><span data-stu-id="a5229-187">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called after the `title` element has been validated but before the `description` element has been validated, it returns an array containing a single <xref:System.Xml.Schema.XmlSchemaElement> object representing the `description` element.</span></span> <span data-ttu-id="a5229-188">如果 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 方法在验证了 `description` 元素之后调用，将返回一个数组，包含表示通配符的单个 <xref:System.Xml.Schema.XmlSchemaAny> 对象。</span><span class="sxs-lookup"><span data-stu-id="a5229-188">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called after the `description` element has been validated then it returns an array containing a single <xref:System.Xml.Schema.XmlSchemaAny> object representing the wildcard.</span></span>

```vb
Dim reader As XmlReader =  XmlReader.Create("input.xml")

Dim schemaSet As New XmlSchemaSet()
schemaSet.Add(Nothing, "schema.xsd")
Dim manager As New XmlNamespaceManager(reader.NameTable)

Dim validator As New XmlSchemaValidator(reader.NameTable,schemaSet,manager,XmlSchemaValidationFlags.None)
validator.Initialize()

validator.ValidateElement("book", "", Nothing)

validator.ValidateEndOfAttributes(Nothing)
For Each element As XmlSchemaElement In validator.GetExpectedParticles()
    Console.WriteLine(element.Name)
Next

validator.ValidateElement("title", "", Nothing)
validator.ValidateEndOfAttributes(Nothing)
For Each element As XmlSchemaElement In validator.GetExpectedParticles()
    Console.WriteLine(element.Name)
Next
validator.ValidateEndElement(Nothing)

For Each element As XmlSchemaElement In validator.GetExpectedParticles()
    Console.WriteLine(element.Name)
Next

validator.ValidateElement("description", "", Nothing)
validator.ValidateEndOfAttributes(Nothing)
validator.ValidateEndElement(Nothing)

For Each particle As XmlSchemaParticle In validator.GetExpectedParticles()
    Console.WriteLine(particle.GetType())
Next

validator.ValidateElement("namespace", "", Nothing)
validator.ValidateEndOfAttributes(Nothing)
validator.ValidateEndElement(Nothing)

validator.ValidateEndElement(Nothing)
```

```csharp
XmlReader reader = XmlReader.Create("input.xml");

var schemaSet = new XmlSchemaSet();
schemaSet.Add(null, "schema.xsd");
var manager = new XmlNamespaceManager(reader.NameTable);

var validator = new XmlSchemaValidator(reader.NameTable, schemaSet, manager, XmlSchemaValidationFlags.None);
validator.Initialize();

validator.ValidateElement("book", "", null);

validator.ValidateEndOfAttributes(null);
foreach (XmlSchemaElement element in validator.GetExpectedParticles())
{
    Console.WriteLine(element.Name);
}

validator.ValidateElement("title", "", null);
validator.ValidateEndOfAttributes(null);
foreach (XmlSchemaElement element in validator.GetExpectedParticles())
{
    Console.WriteLine(element.Name);
}
validator.ValidateEndElement(null);

foreach (XmlSchemaElement element in validator.GetExpectedParticles())
{
    Console.WriteLine(element.Name);
}

validator.ValidateElement("description", "", null);
validator.ValidateEndOfAttributes(null);
validator.ValidateEndElement(null);

foreach (XmlSchemaParticle particle in validator.GetExpectedParticles())
{
    Console.WriteLine(particle.GetType());
}

validator.ValidateElement("namespace", "", null);
validator.ValidateEndOfAttributes(null);
validator.ValidateEndElement(null);

validator.ValidateEndElement(null);
```

 <span data-ttu-id="a5229-189">该示例使用以下 XML 作为输入：</span><span class="sxs-lookup"><span data-stu-id="a5229-189">The example takes the following XML as input:</span></span>

```xml
<xs:schema xmlns:xs="http://www.w3c.org/2001/XMLSchema">
  <xs:element name="book">
    <xs:sequence>
      <xs:element name="title" type="xs:string" />
      <xs:element name="description" type="xs:string" />
      <xs:any processContent="lax" maxOccurs="unbounded" />
    </xs:sequence>
  </xs:element>
</xs:schema>
```

<span data-ttu-id="a5229-190">该示例使用以下 XSD 架构作为输入：</span><span class="sxs-lookup"><span data-stu-id="a5229-190">The example takes the following XSD schema as input:</span></span>

```xml
<book>
  <title>My Book</title>
  <description>My Book's Description</description>
  <namespace>System.Xml.Schema</namespace>
</book>
```

> [!NOTE]
> <span data-ttu-id="a5229-191"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 类的 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>、<xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> 和 <xref:System.Xml.Schema.XmlSchemaValidator> 方法的结果取决于正在验证的当前上下文。</span><span class="sxs-lookup"><span data-stu-id="a5229-191">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span> <span data-ttu-id="a5229-192">有关更多信息，请参见本主题的“验证上下文”一节。</span><span class="sxs-lookup"><span data-stu-id="a5229-192">For more information, see the "Validation Context" section of this topic.</span></span>

<span data-ttu-id="a5229-193">有关 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 方法的示例，请参见简介中的示例。</span><span class="sxs-lookup"><span data-stu-id="a5229-193">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method, see the example in the introduction.</span></span> <span data-ttu-id="a5229-194">有关 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 方法的更多信息，请参见 <xref:System.Xml.Schema.XmlSchemaValidator> 类参考文档。</span><span class="sxs-lookup"><span data-stu-id="a5229-194">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="retrieving-expected-attributes"></a><span data-ttu-id="a5229-195">检索预计的属性</span><span class="sxs-lookup"><span data-stu-id="a5229-195">Retrieving Expected Attributes</span></span>

<span data-ttu-id="a5229-196"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 方法返回一个 <xref:System.Xml.Schema.XmlSchemaAttribute> 对象数组，包含当前元素上下文中预计的属性。</span><span class="sxs-lookup"><span data-stu-id="a5229-196">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method returns an array of <xref:System.Xml.Schema.XmlSchemaAttribute> objects containing the expected attributes in the current element context.</span></span>

<span data-ttu-id="a5229-197">例如，在简介的示例中，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 方法用于检索 `book` 元素的所有属性。</span><span class="sxs-lookup"><span data-stu-id="a5229-197">For example, in the example in the introduction, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method is used to retrieve all the attributes of the `book` element.</span></span>

<span data-ttu-id="a5229-198">如果在调用 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 方法之后立即调用 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> 方法，将返回 XML 文档中可能出现的所有属性。</span><span class="sxs-lookup"><span data-stu-id="a5229-198">If you call the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method immediately after the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> method, all the attributes that could appear in the XML document are returned.</span></span> <span data-ttu-id="a5229-199">但是，如果在一次或多次调用 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 方法之后调用 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> 方法，将返回当前元素尚未进行验证的属性。</span><span class="sxs-lookup"><span data-stu-id="a5229-199">However, if you call the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method after one or more calls to the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method, the attributes that have not yet been validated for the current element are returned.</span></span>

> [!NOTE]
> <span data-ttu-id="a5229-200"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 类的 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>、<xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> 和 <xref:System.Xml.Schema.XmlSchemaValidator> 方法的结果取决于正在验证的当前上下文。</span><span class="sxs-lookup"><span data-stu-id="a5229-200">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span> <span data-ttu-id="a5229-201">有关更多信息，请参见本主题的“验证上下文”一节。</span><span class="sxs-lookup"><span data-stu-id="a5229-201">For more information, see the "Validation Context" section of this topic.</span></span>

<span data-ttu-id="a5229-202">有关 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 方法的示例，请参见简介中的示例。</span><span class="sxs-lookup"><span data-stu-id="a5229-202">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method, see the example in the introduction.</span></span> <span data-ttu-id="a5229-203">有关 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 方法的更多信息，请参见 <xref:System.Xml.Schema.XmlSchemaValidator> 类参考文档。</span><span class="sxs-lookup"><span data-stu-id="a5229-203">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="retrieving-unspecified-default-attributes"></a><span data-ttu-id="a5229-204">检索未指定的默认属性</span><span class="sxs-lookup"><span data-stu-id="a5229-204">Retrieving Unspecified Default Attributes</span></span>

<span data-ttu-id="a5229-205"><xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> 方法使用元素上下文中以前尚未使用 <xref:System.Collections.ArrayList> 方法进行验证的默认值填充使用任何属性的 <xref:System.Xml.Schema.XmlSchemaAttribute> 对象指定的 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>。</span><span class="sxs-lookup"><span data-stu-id="a5229-205">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method populates the <xref:System.Collections.ArrayList> specified with <xref:System.Xml.Schema.XmlSchemaAttribute> objects for any attributes with default values that have not been previously validated using the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method in the element context.</span></span> <span data-ttu-id="a5229-206"><xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> 方法应在元素上下文中的每个属性上调用了 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> 方法之后调用。</span><span class="sxs-lookup"><span data-stu-id="a5229-206">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method should be called after calling the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method on each attribute in the element context.</span></span> <span data-ttu-id="a5229-207"><xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> 方法应用于确定要插入正在验证的 XML 文档的默认属性。</span><span class="sxs-lookup"><span data-stu-id="a5229-207">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method should be used to determine what default attributes are to be inserted into the XML document being validated.</span></span>

<span data-ttu-id="a5229-208">有关 <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> 方法的更多信息，请参见 <xref:System.Xml.Schema.XmlSchemaValidator> 类参考文档。</span><span class="sxs-lookup"><span data-stu-id="a5229-208">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="handling-schema-validation-events"></a><span data-ttu-id="a5229-209">处理架构验证事件</span><span class="sxs-lookup"><span data-stu-id="a5229-209">Handling Schema Validation Events</span></span>

<span data-ttu-id="a5229-210">在验证过程中遇到的架构验证警告和错误由 <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> 类的 <xref:System.Xml.Schema.XmlSchemaValidator> 事件进行处理。</span><span class="sxs-lookup"><span data-stu-id="a5229-210">Schema validation warnings and errors encountered during validation are handled by the <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> event of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>

<span data-ttu-id="a5229-211">架构验证警告的 <xref:System.Xml.Schema.XmlSeverityType> 值为 <xref:System.Xml.Schema.XmlSeverityType.Warning>，架构验证错误的 <xref:System.Xml.Schema.XmlSeverityType> 值为 <xref:System.Xml.Schema.XmlSeverityType.Error>。</span><span class="sxs-lookup"><span data-stu-id="a5229-211">Schema validation warnings have an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Warning> and schema validation errors have an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Error>.</span></span> <span data-ttu-id="a5229-212">如果尚未分配任何 <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler>，所有 <xref:System.Xml.Schema.XmlSchemaValidationException> 值为 <xref:System.Xml.Schema.XmlSeverityType> 的架构验证错误将引发 <xref:System.Xml.Schema.XmlSeverityType.Error>。</span><span class="sxs-lookup"><span data-stu-id="a5229-212">If no <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> has been assigned, an <xref:System.Xml.Schema.XmlSchemaValidationException> is thrown for all schema validation errors with an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Error>.</span></span> <span data-ttu-id="a5229-213">但是，<xref:System.Xml.Schema.XmlSchemaValidationException> 值为 <xref:System.Xml.Schema.XmlSeverityType> 的架构验证警告不会引发 <xref:System.Xml.Schema.XmlSeverityType.Warning>。</span><span class="sxs-lookup"><span data-stu-id="a5229-213">However, an <xref:System.Xml.Schema.XmlSchemaValidationException> is not thrown for schema validation warnings with an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Warning>.</span></span>

<span data-ttu-id="a5229-214">以下 <xref:System.Xml.Schema.ValidationEventHandler> 示例接收在架构验证过程中遇到的架构验证警告和错误，该示例从简介的示例中获取。</span><span class="sxs-lookup"><span data-stu-id="a5229-214">The following is an example of a <xref:System.Xml.Schema.ValidationEventHandler> that receives schema validation warnings and errors encountered during schema validation taken from the example in the introduction.</span></span>

```vb
Shared Sub SchemaValidationEventHandler(sender As Object, e As ValidationEventArgs)

    Select Case e.Severity
        Case XmlSeverityType.Error
            Console.WriteLine(vbCrLf & "Error: {0}", e.Message)
            Exit Sub
        Case XmlSeverityType.Warning
            Console.WriteLine(vbCrLf & "Warning: {0}", e.Message)
            Exit Sub
    End Select
End Sub
```

```csharp
static void SchemaValidationEventHandler(object sender, ValidationEventArgs e)
{
    switch (e.Severity)
    {
        case XmlSeverityType.Error:
            Console.WriteLine("\nError: {0}", e.Message);
            break;
        case XmlSeverityType.Warning:
            Console.WriteLine("\nWarning: {0}", e.Message);
            break;
    }
}
```

<span data-ttu-id="a5229-215">有关 <xref:System.Xml.Schema.ValidationEventHandler> 的完整示例，请参见简介中的示例。</span><span class="sxs-lookup"><span data-stu-id="a5229-215">For a complete example of the <xref:System.Xml.Schema.ValidationEventHandler>, see the example in the introduction.</span></span> <span data-ttu-id="a5229-216">有关更多信息，请参见 <xref:System.Xml.Schema.XmlSchemaInfo> 类参考文档。</span><span class="sxs-lookup"><span data-stu-id="a5229-216">For more information, see the <xref:System.Xml.Schema.XmlSchemaInfo> class reference documentation.</span></span>

## <a name="xmlschemavalidator-state-transition"></a><span data-ttu-id="a5229-217">XmlSchemaValidator 状态转换</span><span class="sxs-lookup"><span data-stu-id="a5229-217">XmlSchemaValidator State Transition</span></span>

<span data-ttu-id="a5229-218"><xref:System.Xml.Schema.XmlSchemaValidator> 类包含已定义的状态转换，强制按顺序执行对用于验证 XML 信息集中的元素、属性和内容的每种方法的调用。</span><span class="sxs-lookup"><span data-stu-id="a5229-218">The <xref:System.Xml.Schema.XmlSchemaValidator> class has a defined state transition that enforces the sequence and occurrence of calls made to each of the methods used to validate elements, attributes, and content in an XML infoset.</span></span>

<span data-ttu-id="a5229-219">下表介绍 <xref:System.Xml.Schema.XmlSchemaValidator> 类的状态转换以及每个状态可以按顺序执行的方法调用。</span><span class="sxs-lookup"><span data-stu-id="a5229-219">The following table describes the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class, and the sequence and occurrence of method calls that can be made in each state.</span></span>

|<span data-ttu-id="a5229-220">状态</span><span class="sxs-lookup"><span data-stu-id="a5229-220">State</span></span>|<span data-ttu-id="a5229-221">切换</span><span class="sxs-lookup"><span data-stu-id="a5229-221">Transition</span></span>|
|-----------|----------------|
|<span data-ttu-id="a5229-222">Validate</span><span class="sxs-lookup"><span data-stu-id="a5229-222">Validate</span></span>|<span data-ttu-id="a5229-223"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel\*) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A></span><span class="sxs-lookup"><span data-stu-id="a5229-223"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel\*) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A></span></span>|
|<span data-ttu-id="a5229-224">TopLevel</span><span class="sxs-lookup"><span data-stu-id="a5229-224">TopLevel</span></span>|<span data-ttu-id="a5229-225"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span><span class="sxs-lookup"><span data-stu-id="a5229-225"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span></span>|
|<span data-ttu-id="a5229-226">元素</span><span class="sxs-lookup"><span data-stu-id="a5229-226">Element</span></span>|<span data-ttu-id="a5229-227"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\*)?</span><span class="sxs-lookup"><span data-stu-id="a5229-227"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\*)?</span></span> <span data-ttu-id="a5229-228"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;</span><span class="sxs-lookup"><span data-stu-id="a5229-228"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;</span></span><br /><br /> <span data-ttu-id="a5229-229"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span><span class="sxs-lookup"><span data-stu-id="a5229-229"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span></span><br /><br /> <span data-ttu-id="a5229-230"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span><span class="sxs-lookup"><span data-stu-id="a5229-230"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span></span>|
|<span data-ttu-id="a5229-231">内容</span><span class="sxs-lookup"><span data-stu-id="a5229-231">Content</span></span>|<span data-ttu-id="a5229-232"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span><span class="sxs-lookup"><span data-stu-id="a5229-232"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span></span>|

> [!NOTE]
> <span data-ttu-id="a5229-233">如果调用方法的顺序不符合 <xref:System.InvalidOperationException> 对象的当前状态，上表中的每种方法将引发 <xref:System.Xml.Schema.XmlSchemaValidator>。</span><span class="sxs-lookup"><span data-stu-id="a5229-233">An <xref:System.InvalidOperationException> is thrown by each of the methods in the table above when the call to the method is made in the incorrect sequence according to the current state of an <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span>

<span data-ttu-id="a5229-234">上面的状态转换表使用标点符号描述 <xref:System.Xml.Schema.XmlSchemaValidator> 类中状态转换的每种状态可以调用的方法和其他状态。</span><span class="sxs-lookup"><span data-stu-id="a5229-234">The state transition table above uses punctuation symbols to describe the methods and other states that can be called for each state of the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span> <span data-ttu-id="a5229-235">使用的符号与文档类型定义 (DTD) 的 XML 标准引用中出现的符号相同。</span><span class="sxs-lookup"><span data-stu-id="a5229-235">The symbols used are the same symbols found in the XML Standards reference for Document Type Definition (DTD).</span></span>

<span data-ttu-id="a5229-236">下表描述上面的状态转换表中出现的标点符号如何影响 <xref:System.Xml.Schema.XmlSchemaValidator> 类中状态转换的每种状态可以调用的方法和其他状态。</span><span class="sxs-lookup"><span data-stu-id="a5229-236">The following table describes how the punctuation symbols found in the state transition table above affect the methods and other states that can be called for each state in the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>

|<span data-ttu-id="a5229-237">符号</span><span class="sxs-lookup"><span data-stu-id="a5229-237">Symbol</span></span>|<span data-ttu-id="a5229-238">描述</span><span class="sxs-lookup"><span data-stu-id="a5229-238">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="a5229-239">&#124;</span><span class="sxs-lookup"><span data-stu-id="a5229-239">&#124;</span></span>|<span data-ttu-id="a5229-240">可以调用（竖线之前或竖线之后的）方法或状态。</span><span class="sxs-lookup"><span data-stu-id="a5229-240">Either method or state (the one before the bar or the one after it) can be called.</span></span>|
|<span data-ttu-id="a5229-241">?</span><span class="sxs-lookup"><span data-stu-id="a5229-241">?</span></span>|<span data-ttu-id="a5229-242">问号之前的方法或状态是可选的，但是如果调用，只能调用一次。</span><span class="sxs-lookup"><span data-stu-id="a5229-242">The method or state that precedes the question mark is optional but if it is called it can only be called once.</span></span>|
|\*|<span data-ttu-id="a5229-243">\* 符号之前的方法或状态是可选的，可以调用多次。</span><span class="sxs-lookup"><span data-stu-id="a5229-243">The method or state that precedes the \* symbol is optional, and can be called more than once.</span></span>|

## <a name="validation-context"></a><span data-ttu-id="a5229-244">验证上下文</span><span class="sxs-lookup"><span data-stu-id="a5229-244">Validation Context</span></span>

<span data-ttu-id="a5229-245"><xref:System.Xml.Schema.XmlSchemaValidator> 类中用于验证 XML 信息集中的元素、属性和内容的方法会更改 <xref:System.Xml.Schema.XmlSchemaValidator> 对象的验证上下文。</span><span class="sxs-lookup"><span data-stu-id="a5229-245">The methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class used to validate elements, attributes, and content in an XML infoset, change the validation context of an <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span> <span data-ttu-id="a5229-246">例如，<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> 方法跳过当前元素内容的验证并准备 <xref:System.Xml.Schema.XmlSchemaValidator> 对象，以验证父元素上下文中的内容；这等效于跳过当前元素的所有子级的验证并调用 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="a5229-246">For example, the <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> method skips validation of the current element content and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate content in the parent element's context; it is equivalent to skipping validation for all the children of the current element and then calling the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> method.</span></span>

<span data-ttu-id="a5229-247"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 类的 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>、<xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> 和 <xref:System.Xml.Schema.XmlSchemaValidator> 方法的结果取决于正在验证的当前上下文。</span><span class="sxs-lookup"><span data-stu-id="a5229-247">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span>

<span data-ttu-id="a5229-248">下表介绍在调用 <xref:System.Xml.Schema.XmlSchemaValidator> 类中的一个用于验证 XML 信息集中的元素、属性和内容的方法之后调用这些方法的结果。</span><span class="sxs-lookup"><span data-stu-id="a5229-248">The following table describes the results of calling these methods after calling one of the methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class used to validate elements, attributes, and content in an XML infoset.</span></span>

|<span data-ttu-id="a5229-249">方法</span><span class="sxs-lookup"><span data-stu-id="a5229-249">Method</span></span>|<span data-ttu-id="a5229-250">GetExpectedParticles</span><span class="sxs-lookup"><span data-stu-id="a5229-250">GetExpectedParticles</span></span>|<span data-ttu-id="a5229-251">GetExpectedAttributes</span><span class="sxs-lookup"><span data-stu-id="a5229-251">GetExpectedAttributes</span></span>|<span data-ttu-id="a5229-252">AddSchema</span><span class="sxs-lookup"><span data-stu-id="a5229-252">AddSchema</span></span>|
|------------|--------------------------|---------------------------|---------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>|<span data-ttu-id="a5229-253">如果调用默认的 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 方法，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 将返回包含所有全局元素的数组。</span><span class="sxs-lookup"><span data-stu-id="a5229-253">If the default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method is called, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an array containing all global elements.</span></span><br /><br /> <span data-ttu-id="a5229-254">如果调用使用 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 作为参数的重载 <xref:System.Xml.Schema.XmlSchemaObject> 方法来初始化元素的部分验证，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 将只返回 <xref:System.Xml.Schema.XmlSchemaValidator> 对象初始化所针对的元素。</span><span class="sxs-lookup"><span data-stu-id="a5229-254">If the overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter is called to initialize partial validation of an element, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns only the element to which the <xref:System.Xml.Schema.XmlSchemaValidator> object was initialized.</span></span>|<span data-ttu-id="a5229-255">如果调用默认的 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 方法，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 将返回一个空数组。</span><span class="sxs-lookup"><span data-stu-id="a5229-255">If the default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method is called, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="a5229-256">如果调用使用 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> 作为参数的重载 <xref:System.Xml.Schema.XmlSchemaObject> 方法来初始化属性的部分验证，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 将只返回 <xref:System.Xml.Schema.XmlSchemaValidator> 对象初始化所针对的属性。</span><span class="sxs-lookup"><span data-stu-id="a5229-256">If the overload of the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter is called to initialize partial validation of an attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns only the attribute to which the <xref:System.Xml.Schema.XmlSchemaValidator> object was initialized.</span></span>|<span data-ttu-id="a5229-257">如果没有预处理错误，将架构添加到 <xref:System.Xml.Schema.XmlSchemaSet> 对象的 <xref:System.Xml.Schema.XmlSchemaValidator> 中。</span><span class="sxs-lookup"><span data-stu-id="a5229-257">Adds the schema to the <xref:System.Xml.Schema.XmlSchemaSet> of the <xref:System.Xml.Schema.XmlSchemaValidator> object if it has no preprocessing errors.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|<span data-ttu-id="a5229-258">如果上下文元素有效，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 将返回预计作为上下文元素子级的元素序列。</span><span class="sxs-lookup"><span data-stu-id="a5229-258">If the context element is valid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as children of the context element.</span></span><br /><br /> <span data-ttu-id="a5229-259">如果上下文元素无效，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 将返回一个空数组。</span><span class="sxs-lookup"><span data-stu-id="a5229-259">If the context element is invalid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span>|<span data-ttu-id="a5229-260">如果上下文元素有效，并且以前未调用过 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 将返回上下文元素上定义的所有属性的列表。</span><span class="sxs-lookup"><span data-stu-id="a5229-260">If the context element is valid, and if no call to <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> has been previously made, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of all the attributes defined on the context element.</span></span><br /><br /> <span data-ttu-id="a5229-261">如果某些属性已进行验证，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 将返回其他要验证的属性的列表。</span><span class="sxs-lookup"><span data-stu-id="a5229-261">If some attributes have already been validated, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of the remaining attributes to be validated.</span></span><br /><br /> <span data-ttu-id="a5229-262">如果上下文元素无效，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 将返回一个空数组。</span><span class="sxs-lookup"><span data-stu-id="a5229-262">If the context element is invalid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span>|<span data-ttu-id="a5229-263">同上。</span><span class="sxs-lookup"><span data-stu-id="a5229-263">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|<span data-ttu-id="a5229-264">如果上下文属性是顶级属性，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 将返回一个空数组。</span><span class="sxs-lookup"><span data-stu-id="a5229-264">If the context attribute is a top-level attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="a5229-265">否则，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 将返回预计作为上下文元素的第一个子级的元素序列。</span><span class="sxs-lookup"><span data-stu-id="a5229-265">Otherwise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="a5229-266">如果上下文属性是顶级属性，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 将返回一个空数组。</span><span class="sxs-lookup"><span data-stu-id="a5229-266">If the context attribute is a top-level attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="a5229-267">否则，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 将返回其他要验证的属性的列表。</span><span class="sxs-lookup"><span data-stu-id="a5229-267">Otherwise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the list of remaining attributes to be validated.</span></span>|<span data-ttu-id="a5229-268">同上。</span><span class="sxs-lookup"><span data-stu-id="a5229-268">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>|<span data-ttu-id="a5229-269"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 将返回需要作为上下文元素的第一个子级的元素的序列。</span><span class="sxs-lookup"><span data-stu-id="a5229-269"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="a5229-270"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 将返回仍需要验证的上下文元素的必选属性和可选属性的列表。</span><span class="sxs-lookup"><span data-stu-id="a5229-270"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of the required and optional attributes that are yet to be validated for the context element.</span></span>|<span data-ttu-id="a5229-271">同上。</span><span class="sxs-lookup"><span data-stu-id="a5229-271">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<span data-ttu-id="a5229-272"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 将返回需要作为上下文元素的第一个子级的元素的序列。</span><span class="sxs-lookup"><span data-stu-id="a5229-272"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="a5229-273"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 将返回一个空数组。</span><span class="sxs-lookup"><span data-stu-id="a5229-273"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span>|<span data-ttu-id="a5229-274">同上。</span><span class="sxs-lookup"><span data-stu-id="a5229-274">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|<span data-ttu-id="a5229-275">如果上下文元素的 contentType 为 Mixed，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 将返回下一个位置预计的元素序列。</span><span class="sxs-lookup"><span data-stu-id="a5229-275">If the context element's contentType is Mixed, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected in the next position.</span></span><br /><br /> <span data-ttu-id="a5229-276">如果上下文元素的 contentType 为 TextOnly 或 Empty，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 将返回一个空数组。</span><span class="sxs-lookup"><span data-stu-id="a5229-276">If the context element's contentType is TextOnly or Empty, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="a5229-277">如果上下文元素的 contentType 为 ElementOnly，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 将返回下一个位置预计的、但是已出现验证错误的元素序列。</span><span class="sxs-lookup"><span data-stu-id="a5229-277">If the context element's contentType is ElementOnly, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected in the next position but a validation error has already occurred.</span></span>|<span data-ttu-id="a5229-278"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 将返回未验证的上下文元素属性列表。</span><span class="sxs-lookup"><span data-stu-id="a5229-278"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the context element's list of attributes not validated.</span></span>|<span data-ttu-id="a5229-279">同上。</span><span class="sxs-lookup"><span data-stu-id="a5229-279">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|<span data-ttu-id="a5229-280">如果上下文空白是顶级空白，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 将返回一个空数组。</span><span class="sxs-lookup"><span data-stu-id="a5229-280">If the context white-space is top-level white-space, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="a5229-281">否则，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 方法的行为与 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> 中相同。</span><span class="sxs-lookup"><span data-stu-id="a5229-281">Otherwise the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method's behavior is the same as in <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span></span>|<span data-ttu-id="a5229-282">如果上下文空白是顶级空白，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 将返回一个空数组。</span><span class="sxs-lookup"><span data-stu-id="a5229-282">If the context white-space is top-level white-space, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="a5229-283">否则，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 方法的行为与 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> 中相同。</span><span class="sxs-lookup"><span data-stu-id="a5229-283">Otherwise the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method's behavior is the same as in <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span></span>|<span data-ttu-id="a5229-284">同上。</span><span class="sxs-lookup"><span data-stu-id="a5229-284">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<span data-ttu-id="a5229-285"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> 返回上下文元素之后预计的元素序列（可能是同级）。</span><span class="sxs-lookup"><span data-stu-id="a5229-285"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected after the context element (possible siblings).</span></span>|<span data-ttu-id="a5229-286"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 将返回未验证的上下文元素属性列表。</span><span class="sxs-lookup"><span data-stu-id="a5229-286"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the context element's list of attributes not validated.</span></span><br /><br /> <span data-ttu-id="a5229-287">如果上下文元素没有父级，<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> 将返回一个空列表（上下文元素是调用 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> 的当前元素的父级）。</span><span class="sxs-lookup"><span data-stu-id="a5229-287">If the context element has no parent then <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty list (the context element is the parent of the current element on which <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> was called).</span></span>|<span data-ttu-id="a5229-288">同上。</span><span class="sxs-lookup"><span data-stu-id="a5229-288">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<span data-ttu-id="a5229-289">与 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> 相同。</span><span class="sxs-lookup"><span data-stu-id="a5229-289">Same as <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span></span>|<span data-ttu-id="a5229-290">与 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> 相同。</span><span class="sxs-lookup"><span data-stu-id="a5229-290">Same as <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span></span>|<span data-ttu-id="a5229-291">同上。</span><span class="sxs-lookup"><span data-stu-id="a5229-291">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<span data-ttu-id="a5229-292">返回一个空数组。</span><span class="sxs-lookup"><span data-stu-id="a5229-292">Returns an empty array.</span></span>|<span data-ttu-id="a5229-293">返回一个空数组。</span><span class="sxs-lookup"><span data-stu-id="a5229-293">Returns an empty array.</span></span>|<span data-ttu-id="a5229-294">同上。</span><span class="sxs-lookup"><span data-stu-id="a5229-294">Same as above.</span></span>|

> [!NOTE]
> <span data-ttu-id="a5229-295">调用上表中的任何方法时不会更改 <xref:System.Xml.Schema.XmlSchemaValidator> 类的各种属性返回的值。</span><span class="sxs-lookup"><span data-stu-id="a5229-295">The values returned by the various properties of the <xref:System.Xml.Schema.XmlSchemaValidator> class are not altered by calling any of the methods in the above table.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5229-296">请参阅</span><span class="sxs-lookup"><span data-stu-id="a5229-296">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator>

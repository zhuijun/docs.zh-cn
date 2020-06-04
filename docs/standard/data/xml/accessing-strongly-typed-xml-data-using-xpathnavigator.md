---
title: 使用 XPathNavigator 访问强类型 XML 数据
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 898e0f52-8a7c-4d1f-afcd-6ffb28b050b4
ms.openlocfilehash: afbfd516ef25eff94a9eed841f313892007c58a1
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202336"
---
# <a name="accessing-strongly-typed-xml-data-using-xpathnavigator"></a><span data-ttu-id="7e726-102">使用 XPathNavigator 访问强类型 XML 数据</span><span class="sxs-lookup"><span data-stu-id="7e726-102">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>
<span data-ttu-id="7e726-103">作为 XPath 2.0 数据模型的实例，<xref:System.Xml.XPath.XPathNavigator> 类可以包含映射到公共语言运行库 (CLR) 类型的强类型数据。</span><span class="sxs-lookup"><span data-stu-id="7e726-103">As an instance of the XPath 2.0 data model, the <xref:System.Xml.XPath.XPathNavigator> class can contain strongly typed data that maps to common language runtime (CLR) types.</span></span> <span data-ttu-id="7e726-104">根据 XPath 2.0 数据模型，只有元素和属性可以包含强类型数据。</span><span class="sxs-lookup"><span data-stu-id="7e726-104">According to the XPath 2.0 data model, only elements and attributes can contain strongly typed data.</span></span> <span data-ttu-id="7e726-105"><xref:System.Xml.XPath.XPathNavigator> 类提供将 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 对象中的数据作为强类型数据访问的机制，以及将一种数据类型转换为另一种数据类型的机制。</span><span class="sxs-lookup"><span data-stu-id="7e726-105">The <xref:System.Xml.XPath.XPathNavigator> class provides mechanisms for accessing data within an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object as strongly typed data as well as mechanisms for converting from one data type to another.</span></span>  
  
## <a name="type-information-exposed-by-xpathnavigator"></a><span data-ttu-id="7e726-106">通过 XPathNavigator 公开的类型信息</span><span class="sxs-lookup"><span data-stu-id="7e726-106">Type Information Exposed by XPathNavigator</span></span>  
 <span data-ttu-id="7e726-107">XML 1.0 数据在技术角度没有类型，除非使用 DTD、XML 架构定义语言 (XSD) 架构或其他机制进行处理。</span><span class="sxs-lookup"><span data-stu-id="7e726-107">XML 1.0 data is technically without type, unless processed with a DTD, XML schema definition language (XSD) schema, or other mechanism.</span></span> <span data-ttu-id="7e726-108">有许多类别的类型信息可以与 XML 元素或属性关联。</span><span class="sxs-lookup"><span data-stu-id="7e726-108">There are a number of categories of type information that can be associated with an XML element or attribute.</span></span>  
  
- <span data-ttu-id="7e726-109">简单 CLR 类型：所有 XML 架构语言都不直接支持公共语言运行时 (CLR) 类型。</span><span class="sxs-lookup"><span data-stu-id="7e726-109">Simple CLR Types: None of the XML Schema languages support Common Language Runtime (CLR) types directly.</span></span> <span data-ttu-id="7e726-110">因为能够以最适合的 CLR 类型查看简单元素和属性内容非常有用，所以，在缺少架构信息以及任何添加的架构信息（可能会将此内容优化为更适合的类型）时，可以将所有简单内容类型化为 <xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="7e726-110">Because it is useful to be able to view simple element and attribute content as the most appropriate CLR type, all simple content can be typed as <xref:System.String> in the absence of schema information with any added schema information potentially refining this content to a more appropriate type.</span></span> <span data-ttu-id="7e726-111">可以使用 <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> 属性找到简单元素和属性内容最匹配的 CLR 类型。</span><span class="sxs-lookup"><span data-stu-id="7e726-111">You can find the best matching CLR type of simple element and attribute content by using the <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> property.</span></span> <span data-ttu-id="7e726-112">若要详细了解如何从架构内置类型映射到 CLR 类型，请参阅 [System.Xml 类中的类型支持](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="7e726-112">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
- <span data-ttu-id="7e726-113">简单 (CLR) 类型列表：包含简单内容的元素或属性可以包含以空格分隔的值列表。</span><span class="sxs-lookup"><span data-stu-id="7e726-113">Lists of Simple (CLR) Types: An element or attribute with simple content can contain a list of values separated by white space.</span></span> <span data-ttu-id="7e726-114">XML 架构将这些值指定为“列表类型”。</span><span class="sxs-lookup"><span data-stu-id="7e726-114">The values are specified by an XML Schema to be a "list type."</span></span> <span data-ttu-id="7e726-115">在缺少 XML 架构时，此类简单内容将作为单个文本节点对待。</span><span class="sxs-lookup"><span data-stu-id="7e726-115">In the absence of an XML Schema, such simple content would be treated as a single text node.</span></span> <span data-ttu-id="7e726-116">在 XML 架构可用时，此简单内容可以作为一系列原子值公开，每个值都具有一种映射到 CLR 对象集合的简单类型。</span><span class="sxs-lookup"><span data-stu-id="7e726-116">When an XML Schema is available, this simple content can be exposed as a series of atomic values each having a simple type that maps to a collection of CLR objects.</span></span> <span data-ttu-id="7e726-117">若要详细了解如何从架构内置类型映射到 CLR 类型，请参阅 [System.Xml 类中的类型支持](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="7e726-117">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
- <span data-ttu-id="7e726-118">类型化值：包含简单内容的已经过架构验证的属性或元素有类型化值。</span><span class="sxs-lookup"><span data-stu-id="7e726-118">Typed Value: A schema-validated attribute or element with a simple type has a typed value.</span></span> <span data-ttu-id="7e726-119">此值是基元类型，例如数字、字符串或日期类型。</span><span class="sxs-lookup"><span data-stu-id="7e726-119">This value is a primitive type such as a numeric, string, or date type.</span></span> <span data-ttu-id="7e726-120">XSD 中的所有内置简单类型均可以映射到 CLR 类型，通过 CLR 类型可以以更适合的类型（而不只是以 <xref:System.String>）访问节点的值。</span><span class="sxs-lookup"><span data-stu-id="7e726-120">All the built-in simple types in XSD can be mapped to CLR types that provide access to the value of a node as a more appropriate type instead of just as a <xref:System.String>.</span></span> <span data-ttu-id="7e726-121">具有属性或元素子级的元素被认为是复杂类型。</span><span class="sxs-lookup"><span data-stu-id="7e726-121">An element with attributes or element children is considered to be a complex type.</span></span> <span data-ttu-id="7e726-122">包含简单内容（只有文本节点作为子级）的复杂类型的类型化值与其内容的简单类型的类型化值相同。</span><span class="sxs-lookup"><span data-stu-id="7e726-122">The typed value of a complex type with simple content (only text nodes as children) is the same as that of the simple type of its content.</span></span> <span data-ttu-id="7e726-123">包含复杂内容（一个或多个子元素）的复杂类型的类型化值是串联以 <xref:System.String> 形式返回的所有子文本节点的字符串值。</span><span class="sxs-lookup"><span data-stu-id="7e726-123">The typed value of a complex type with complex content (one or more child elements) is the string value of the concatenation of all its child text nodes returned as a <xref:System.String>.</span></span> <span data-ttu-id="7e726-124">若要详细了解如何从架构内置类型映射到 CLR 类型，请参阅 [System.Xml 类中的类型支持](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="7e726-124">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
- <span data-ttu-id="7e726-125">架构语言专用类型名称：在大多数情况下，作为应用外部架构附带后果设置的 CLR 类型用于提供对节点值的访问权限。</span><span class="sxs-lookup"><span data-stu-id="7e726-125">Schema-Language Specific Type Name: In most cases, the CLR types, which are set as a side-effect of applying an external schema, are used to provide access to the value of a node.</span></span> <span data-ttu-id="7e726-126">但是，有时可能需要检查与应用于 XML 文档的特定架构相关联的类型。</span><span class="sxs-lookup"><span data-stu-id="7e726-126">However, there may be situations where you may want to examine the type associated with a particular schema applied to an XML document.</span></span> <span data-ttu-id="7e726-127">例如，可能希望搜索 XML 文档，根据附加的架构提取确定包含“PurchaseOrder”类型内容的所有元素。</span><span class="sxs-lookup"><span data-stu-id="7e726-127">For example, you may wish to search through an XML document, extracting all elements that are determined to have content of type "PurchaseOrder" according to an attached schema.</span></span> <span data-ttu-id="7e726-128">此类信息只能设置为架构验证的结果，此信息通过 <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> 类的 <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> 和 <xref:System.Xml.XPath.XPathNavigator> 属性访问。</span><span class="sxs-lookup"><span data-stu-id="7e726-128">Such type information can be set only as a result of schema validation and this information is accessed through the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> and <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="7e726-129">有关更多信息，请参见下面的“后架构验证信息集 (PSVI)”一节。</span><span class="sxs-lookup"><span data-stu-id="7e726-129">For more information, see The Post Schema Validation Infoset (PSVI) section below.</span></span>  
  
- <span data-ttu-id="7e726-130">架构语言专用类型反射：在其他情况下，建议获取应用于 XML 文档的架构专用类型的更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="7e726-130">Schema-Language Specific Type Reflection: In other cases, you may want to obtain further details of the schema-specific type applied to an XML document.</span></span> <span data-ttu-id="7e726-131">例如，在读取 XML 文件时，可能需要为 XML 文档中的每个有效节点提取 `maxOccurs` 属性，以便执行某项自定义计算。</span><span class="sxs-lookup"><span data-stu-id="7e726-131">For example, when reading an XML file, you may want to extract the `maxOccurs` attribute for each valid node in the XML document in order to perform some custom calculation.</span></span> <span data-ttu-id="7e726-132">因为此信息仅通过架构验证设置，所以，通过 <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> 类的 <xref:System.Xml.XPath.XPathNavigator> 属性访问。</span><span class="sxs-lookup"><span data-stu-id="7e726-132">Because this information is set only through schema validation, it is accessed through the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="7e726-133">有关更多信息，请参见下面的“后架构验证信息集 (PSVI)”一节。</span><span class="sxs-lookup"><span data-stu-id="7e726-133">For more information, see The Post Schema Validation Infoset (PSVI) section below.</span></span>  
  
## <a name="xpathnavigator-typed-accessors"></a><span data-ttu-id="7e726-134">XPathNavigator 类型化访问器</span><span class="sxs-lookup"><span data-stu-id="7e726-134">XPathNavigator Typed Accessors</span></span>  
 <span data-ttu-id="7e726-135">下表显示 <xref:System.Xml.XPath.XPathNavigator> 类中可以用于访问节点的类型信息的各种属性和方法。</span><span class="sxs-lookup"><span data-stu-id="7e726-135">The following table shows the various properties and methods of the <xref:System.Xml.XPath.XPathNavigator> class that can be used to access the type information about a node.</span></span>  
  
|<span data-ttu-id="7e726-136">Property</span><span class="sxs-lookup"><span data-stu-id="7e726-136">Property</span></span>|<span data-ttu-id="7e726-137">描述</span><span class="sxs-lookup"><span data-stu-id="7e726-137">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.XmlType%2A>|<span data-ttu-id="7e726-138">此属性包含节点（如果有效）的 XML 架构类型信息。</span><span class="sxs-lookup"><span data-stu-id="7e726-138">This contains the XML schema type information for the node if it is valid.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A>|<span data-ttu-id="7e726-139">此属性包含在验证之后添加的节点的后架构验证信息集。</span><span class="sxs-lookup"><span data-stu-id="7e726-139">This contains the Post Schema Validation Infoset of the node that is added after validation.</span></span> <span data-ttu-id="7e726-140">其中包括 XML 架构类型信息以及有效性信息。</span><span class="sxs-lookup"><span data-stu-id="7e726-140">This includes the XML schema type information, as well as validity information.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueType%2A>|<span data-ttu-id="7e726-141">节点的类型化值的 CLR 类型。</span><span class="sxs-lookup"><span data-stu-id="7e726-141">The CLR type of the typed value of the node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>|<span data-ttu-id="7e726-142">作为类型与节点的 XML 架构类型最匹配的一个或多个 CLR 值的节点内容。</span><span class="sxs-lookup"><span data-stu-id="7e726-142">The content of the node as one or more CLR values whose type is the closest match to the XML schema type of the node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsBoolean%2A>|<span data-ttu-id="7e726-143">当前节点的 <xref:System.String> 值根据 <xref:System.Boolean> 的 XPath 2.0 强制转换规则强制转换为 `xs:boolean` 值。</span><span class="sxs-lookup"><span data-stu-id="7e726-143">The <xref:System.String> value of the current node cast to a <xref:System.Boolean> value, according to the XPath 2.0 casting rules for `xs:boolean`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDateTime%2A>|<span data-ttu-id="7e726-144">当前节点的 <xref:System.String> 值根据 <xref:System.DateTime> 的 XPath 2.0 强制转换规则强制转换为 `xs:datetime` 值。</span><span class="sxs-lookup"><span data-stu-id="7e726-144">The <xref:System.String> value of the current node cast to a <xref:System.DateTime> value, according to the XPath 2.0 casting rules for `xs:datetime`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>|<span data-ttu-id="7e726-145">当前节点的 <xref:System.String> 值根据 <xref:System.Double> 的 XPath 2.0 强制转换规则强制转换为 `xsd:double` 值。</span><span class="sxs-lookup"><span data-stu-id="7e726-145">The <xref:System.String> value of the current node cast to a <xref:System.Double> value, according to the XPath 2.0 casting rules for `xsd:double`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>|<span data-ttu-id="7e726-146">当前节点的 <xref:System.String> 值根据 <xref:System.Int32> 的 XPath 2.0 强制转换规则强制转换为 `xs:integer` 值。</span><span class="sxs-lookup"><span data-stu-id="7e726-146">The <xref:System.String> value of the current node cast to a <xref:System.Int32> value, according to the XPath 2.0 casting rules for `xs:integer`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A>|<span data-ttu-id="7e726-147">当前节点的 <xref:System.String> 值根据 <xref:System.Int64> 的 XPath 2.0 强制转换规则强制转换为 `xs:integer` 值。</span><span class="sxs-lookup"><span data-stu-id="7e726-147">The <xref:System.String> value of the current node cast to a <xref:System.Int64> value, according to the XPath 2.0 casting rules for `xs:integer`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAs%2A>|<span data-ttu-id="7e726-148">节点内容根据 XPath 2.0 强制转换规则强制转换为目标类型。</span><span class="sxs-lookup"><span data-stu-id="7e726-148">The contents of the node cast to the target type according to the XPath 2.0 casting rules.</span></span>|  
  
 <span data-ttu-id="7e726-149">若要详细了解如何从架构内置类型映射到 CLR 类型，请参阅 [System.Xml 类中的类型支持](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="7e726-149">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
## <a name="the-post-schema-validation-infoset-psvi"></a><span data-ttu-id="7e726-150">后架构验证信息集 (PSVI)</span><span class="sxs-lookup"><span data-stu-id="7e726-150">The Post Schema Validation Infoset (PSVI)</span></span>  
 <span data-ttu-id="7e726-151">XML 架构处理器使用 XML 信息集作为输入，并将其转换为后架构验证信息集 (PSVI)。</span><span class="sxs-lookup"><span data-stu-id="7e726-151">An XML Schema processor accepts an XML Infoset as input and converts it into a Post Schema Validation Infoset (PSVI).</span></span> <span data-ttu-id="7e726-152">PSVI 是原始输入 XML 信息集，包含添加的新信息项以及在现有信息项中添加的新属性。</span><span class="sxs-lookup"><span data-stu-id="7e726-152">A PSVI is the original input XML infoset with new information items added and new properties added to existing information items.</span></span> <span data-ttu-id="7e726-153">在 PSVI 的 XML 信息集中添加了三种广义信息类，通过 <xref:System.Xml.XPath.XPathNavigator> 公开。</span><span class="sxs-lookup"><span data-stu-id="7e726-153">There are three broad classes of information added to the XML Infoset in the PSVI that are exposed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
1. <span data-ttu-id="7e726-154">验证结果：有关是否已成功验证元素或属性的信息。</span><span class="sxs-lookup"><span data-stu-id="7e726-154">Validation Outcomes: Information as to whether an element or attribute was successfully validated or not.</span></span> <span data-ttu-id="7e726-155">此信息通过 <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> 类的 <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> 属性的 <xref:System.Xml.XPath.XPathNavigator> 属性公开。</span><span class="sxs-lookup"><span data-stu-id="7e726-155">This is exposed by the <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> property of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
2. <span data-ttu-id="7e726-156">默认信息：有关是否已通过架构中指定的默认值获取元素或属性的值的信息。</span><span class="sxs-lookup"><span data-stu-id="7e726-156">Default Information: Indications as to whether the value of the element or attribute was obtained via default values specified in the schema or not.</span></span> <span data-ttu-id="7e726-157">此信息通过 <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> 类的 <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> 属性的 <xref:System.Xml.XPath.XPathNavigator> 属性公开。</span><span class="sxs-lookup"><span data-stu-id="7e726-157">This is exposed by the <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> property of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
3. <span data-ttu-id="7e726-158">类型批注：对架构组件的引用，可能是类型定义或元素和属性的声明。</span><span class="sxs-lookup"><span data-stu-id="7e726-158">Type Annotations: References to schema components that may be type definitions or element and attribute declarations.</span></span> <span data-ttu-id="7e726-159"><xref:System.Xml.XPath.XPathNavigator.XmlType%2A> 的 <xref:System.Xml.XPath.XPathNavigator> 属性包含节点（如果有效）的特定类型信息。</span><span class="sxs-lookup"><span data-stu-id="7e726-159">The <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property of the <xref:System.Xml.XPath.XPathNavigator> contains the specific type information of the node if it is valid.</span></span> <span data-ttu-id="7e726-160">如果节点的有效性未知，例如节点在验证后进行了编辑，</span><span class="sxs-lookup"><span data-stu-id="7e726-160">If the validity of a node is unknown, such as when it was validated then subsequently edited.</span></span> <span data-ttu-id="7e726-161"><xref:System.Xml.XPath.XPathNavigator.XmlType%2A> 属性将设置为 `null`，但是类型信息仍可以通过 <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> 类的 <xref:System.Xml.XPath.XPathNavigator> 属性的各种属性访问。</span><span class="sxs-lookup"><span data-stu-id="7e726-161">then the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property is set to `null` but type information is still available from the various properties of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 <span data-ttu-id="7e726-162">以下示例说明如何使用通过 <xref:System.Xml.XPath.XPathNavigator> 公开的后架构验证信息集中的信息。</span><span class="sxs-lookup"><span data-stu-id="7e726-162">The following example illustrates using information in the Post Schema Validation Infoset exposed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "books.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("books.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
navigator.MoveToChild("books", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("published", "http://www.contoso.com/books")  
  
Console.WriteLine(navigator.SchemaInfo.SchemaType.Name)  
Console.WriteLine(navigator.SchemaInfo.Validity)  
Console.WriteLine(navigator.SchemaInfo.SchemaElement.MinOccurs)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "books.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("books.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
navigator.MoveToChild("books", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("published", "http://www.contoso.com/books");  
  
Console.WriteLine(navigator.SchemaInfo.SchemaType.Name);  
Console.WriteLine(navigator.SchemaInfo.Validity);  
Console.WriteLine(navigator.SchemaInfo.SchemaElement.MinOccurs);  
```  
  
 <span data-ttu-id="7e726-163">该示例使用 `books.xml` 文件作为输入。</span><span class="sxs-lookup"><span data-stu-id="7e726-163">The example takes the `books.xml` file as input.</span></span>  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="7e726-164">该示例还使用 `books.xsd` 架构作为输入。</span><span class="sxs-lookup"><span data-stu-id="7e726-164">The example also takes the `books.xsd` schema as input.</span></span>  
  
```xml  
<xs:schema xmlns="http://www.contoso.com/books"
attributeFormDefault="unqualified" elementFormDefault="qualified"
targetNamespace="http://www.contoso.com/books"
xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="publishedType">  
        <xs:restriction base="xs:date">  
            <xs:minInclusive value="2003-01-01" />  
            <xs:maxInclusive value="2003-12-31" />  
        </xs:restriction>  
    </xs:simpleType>  
    <xs:complexType name="bookType">  
        <xs:sequence>  
            <xs:element name="title" type="xs:string"/>  
            <xs:element name="price" type="xs:decimal"/>  
            <xs:element name="published" type="publishedType"/>  
        </xs:sequence>  
    </xs:complexType>  
    <xs:complexType name="booksType">  
        <xs:sequence>  
            <xs:element name="book" type="bookType" />  
        </xs:sequence>  
    </xs:complexType>  
    <xs:element name="books" type="booksType" />  
</xs:schema>  
```  
  
## <a name="obtain-typed-values-using-valueas-properties"></a><span data-ttu-id="7e726-165">使用 ValueAs 属性获取类型化值</span><span class="sxs-lookup"><span data-stu-id="7e726-165">Obtain Typed Values Using ValueAs Properties</span></span>  
 <span data-ttu-id="7e726-166">节点的类型化值可以通过访问 <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> 的 <xref:System.Xml.XPath.XPathNavigator> 属性进行检索。</span><span class="sxs-lookup"><span data-stu-id="7e726-166">The typed value of a node can be retrieved by accessing the <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> property of the <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="7e726-167">在某些情况下，可能需要将节点的类型化值转换为其他类型。</span><span class="sxs-lookup"><span data-stu-id="7e726-167">In certain cases you may want to convert the typed value of a node to a different type.</span></span> <span data-ttu-id="7e726-168">常见的示例是从 XML 节点获取数值。</span><span class="sxs-lookup"><span data-stu-id="7e726-168">A common example is to get a numeric value from an XML node.</span></span> <span data-ttu-id="7e726-169">例如，考虑以下未经过验证和非类型化的 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="7e726-169">For example, consider the following unvalidated and untyped XML document.</span></span>  
  
```xml  
<books>  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="7e726-170">如果 <xref:System.Xml.XPath.XPathNavigator> 位于 `price` 元素上，<xref:System.Xml.XPath.XPathNavigator.XmlType%2A> 属性将为 `null`，<xref:System.Xml.XPath.XPathNavigator.ValueType%2A> 属性将为 <xref:System.String>，<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> 属性将为字符串 `10.00`。</span><span class="sxs-lookup"><span data-stu-id="7e726-170">If the <xref:System.Xml.XPath.XPathNavigator> is positioned on the `price` element the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property would be `null`, the <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> property would be <xref:System.String>, and the <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> property would be the string `10.00`.</span></span>  
  
 <span data-ttu-id="7e726-171">但是，仍可以使用 <xref:System.Xml.XPath.XPathItem.ValueAs%2A>、<xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>、<xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A> 或 <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> 方法和属性以数值形式提取该值。</span><span class="sxs-lookup"><span data-stu-id="7e726-171">However, it is still possible to extract the value as a numeric value using the <xref:System.Xml.XPath.XPathItem.ValueAs%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>, or <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> method and properties.</span></span> <span data-ttu-id="7e726-172">以下示例说明如何使用 <xref:System.Xml.XPath.XPathItem.ValueAs%2A> 方法执行此类强制转换。</span><span class="sxs-lookup"><span data-stu-id="7e726-172">The following example illustrates performing such a cast using the <xref:System.Xml.XPath.XPathItem.ValueAs%2A> method.</span></span>  
  
```vb  
Dim document As New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
navigator.MoveToChild("books", "")  
navigator.MoveToChild("book", "")  
navigator.MoveToChild("price", "")  
  
Dim price = navigator.ValueAs(GetType(Decimal))  
Dim discount As Decimal = 0.2  
  
Console.WriteLine("The price of the book has been dropped 20% from {0:C} to {1:C}", navigator.Value, (price - price * discount))  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
navigator.MoveToChild("books", "");  
navigator.MoveToChild("book", "");  
navigator.MoveToChild("price", "");  
  
Decimal price = (decimal)navigator.ValueAs(typeof(decimal));  
  
Console.WriteLine("The price of the book has been dropped 20% from {0:C} to {1:C}", navigator.Value, (price - price * (decimal)0.20));  
```  
  
 <span data-ttu-id="7e726-173">若要详细了解如何从架构内置类型映射到 CLR 类型，请参阅 [System.Xml 类中的类型支持](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="7e726-173">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e726-174">请参阅</span><span class="sxs-lookup"><span data-stu-id="7e726-174">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="7e726-175">System.Xml 类中的类型支持</span><span class="sxs-lookup"><span data-stu-id="7e726-175">Type Support in the System.Xml Classes</span></span>](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
- [<span data-ttu-id="7e726-176">使用 XPath 数据模型处理 XML 数据</span><span class="sxs-lookup"><span data-stu-id="7e726-176">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="7e726-177">使用 XPathNavigator 的节点集定位</span><span class="sxs-lookup"><span data-stu-id="7e726-177">Node Set Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="7e726-178">使用 XPathNavigator 的属性和命名空间节点定位</span><span class="sxs-lookup"><span data-stu-id="7e726-178">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="7e726-179">使用 XPathNavigator 提取 XML 数据</span><span class="sxs-lookup"><span data-stu-id="7e726-179">Extract XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)

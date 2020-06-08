---
title: 在 DOM 中验证 XML 文档
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2c61c920-d0f8-4c72-bfcc-6524570f3060
ms.openlocfilehash: 949dc52c332b17784b0e1851d178465fe4881b6f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287631"
---
# <a name="validating-an-xml-document-in-the-dom"></a><span data-ttu-id="e7830-102">在 DOM 中验证 XML 文档</span><span class="sxs-lookup"><span data-stu-id="e7830-102">Validating an XML Document in the DOM</span></span>

<span data-ttu-id="e7830-103">默认情况下，在文档对象模型 (DOM) 中，<xref:System.Xml.XmlDocument> 类不针对 XML 架构定义语言 (XSD) 架构或文档类型定义 (DTD) 验证 XML；只验证 XML 的格式是否正确。</span><span class="sxs-lookup"><span data-stu-id="e7830-103">The<xref:System.Xml.XmlDocument> class does not validate the XML in the Document Object Model (DOM) against an XML Schema definition language (XSD) schema or document type definition (DTD) by default; the XML is only verified to be well-formed.</span></span>

<span data-ttu-id="e7830-104">要在 DOM 中验证 XML，可以在 XML 加载到 DOM 时进行验证，方法是将架构验证 <xref:System.Xml.XmlReader> 传递给 <xref:System.Xml.XmlDocument.Load%2A> 类的 <xref:System.Xml.XmlDocument> 方法，也可以在 DOM 中使用 <xref:System.Xml.XmlDocument.Validate%2A> 类的 <xref:System.Xml.XmlDocument> 方法来验证以前未经过验证的 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="e7830-104">To validate the XML in the DOM, you can validate the XML as it is loaded into the DOM by passing a schema-validating <xref:System.Xml.XmlReader> to the <xref:System.Xml.XmlDocument.Load%2A> method of the <xref:System.Xml.XmlDocument> class, or validate a previously unvalidated XML document in the DOM using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>

## <a name="validating-an-xml-document-as-it-is-loaded-into-the-dom"></a><span data-ttu-id="e7830-105">在 XML 文档加载到 DOM 时进行验证</span><span class="sxs-lookup"><span data-stu-id="e7830-105">Validating an XML Document As It Is Loaded into the DOM</span></span>

<span data-ttu-id="e7830-106">如果将验证 <xref:System.Xml.XmlDocument> 传递给 <xref:System.Xml.XmlReader> 类的 <xref:System.Xml.XmlDocument.Load%2A> 方法，<xref:System.Xml.XmlDocument> 类将在 XML 数据加载到 DOM 时对其进行验证。</span><span class="sxs-lookup"><span data-stu-id="e7830-106">The <xref:System.Xml.XmlDocument> class validates the XML data as it is loaded into the DOM when a validating <xref:System.Xml.XmlReader> is passed to the <xref:System.Xml.XmlDocument.Load%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>

<span data-ttu-id="e7830-107">成功验证之后，将应用架构的默认值，文本值根据需要转换为原子值，类型信息与经过验证的信息项关联。</span><span class="sxs-lookup"><span data-stu-id="e7830-107">After successful validation, schema defaults are applied, text values are converted to atomic values as necessary, and type information is associated with validated information items.</span></span> <span data-ttu-id="e7830-108">因此，类型化 XML 数据将替换以前非类型化的 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="e7830-108">As a result, typed XML data replaces previously untyped XML data.</span></span>

### <a name="creating-an-xml-schema-validating-xmlreader"></a><span data-ttu-id="e7830-109">创建 XML 架构验证 XmlReader</span><span class="sxs-lookup"><span data-stu-id="e7830-109">Creating an XML Schema-Validating XmlReader</span></span>

<span data-ttu-id="e7830-110">要创建 XML 架构验证 <xref:System.Xml.XmlReader>，请执行下列步骤。</span><span class="sxs-lookup"><span data-stu-id="e7830-110">To create an XML schema-validating <xref:System.Xml.XmlReader>, follow these steps.</span></span>

1. <span data-ttu-id="e7830-111">构造一个新的 <xref:System.Xml.XmlReaderSettings> 实例。</span><span class="sxs-lookup"><span data-stu-id="e7830-111">Construct a new <xref:System.Xml.XmlReaderSettings> instance.</span></span>

2. <span data-ttu-id="e7830-112">将 XML 架构添加到 <xref:System.Xml.XmlReaderSettings.Schemas%2A> 实例的 <xref:System.Xml.XmlReaderSettings> 属性中。</span><span class="sxs-lookup"><span data-stu-id="e7830-112">Add an XML schema to the <xref:System.Xml.XmlReaderSettings.Schemas%2A> property of the <xref:System.Xml.XmlReaderSettings> instance.</span></span>

3. <span data-ttu-id="e7830-113">将 `Schema` 指定为 <xref:System.Xml.XmlReaderSettings.ValidationType%2A>。</span><span class="sxs-lookup"><span data-stu-id="e7830-113">Specify `Schema` as the <xref:System.Xml.XmlReaderSettings.ValidationType%2A>.</span></span>

4. <span data-ttu-id="e7830-114">可以选择指定 <xref:System.Xml.XmlReaderSettings.ValidationFlags%2A> 和 <xref:System.Xml.XmlReaderSettings.ValidationEventHandler>，用于处理在验证期间遇到的架构验证错误和警告。</span><span class="sxs-lookup"><span data-stu-id="e7830-114">Optionally specify <xref:System.Xml.XmlReaderSettings.ValidationFlags%2A> and a <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> to handle schema validation errors and warnings encountered during validation.</span></span>

5. <span data-ttu-id="e7830-115">最后，将 <xref:System.Xml.XmlReaderSettings> 对象与 XML 文档一起传递给 <xref:System.Xml.XmlReader.Create%2A> 类的 <xref:System.Xml.XmlReader> 方法，创建架构验证 <xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="e7830-115">Finally, pass the <xref:System.Xml.XmlReaderSettings> object to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class along with the XML document, creating a schema-validating <xref:System.Xml.XmlReader>.</span></span>

### <a name="example"></a><span data-ttu-id="e7830-116">示例</span><span class="sxs-lookup"><span data-stu-id="e7830-116">Example</span></span>

<span data-ttu-id="e7830-117">在下面的代码示例中，架构验证 <xref:System.Xml.XmlReader> 验证加载到 DOM 的 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="e7830-117">In the code example that follows, a schema-validating <xref:System.Xml.XmlReader> validates the XML data loaded into the DOM.</span></span> <span data-ttu-id="e7830-118">对 XML 文档进行无效的修改，然后重新验证文档，造成架构验证错误。</span><span class="sxs-lookup"><span data-stu-id="e7830-118">Invalid modifications are made to the XML document and the document is then revalidated, causing schema validation errors.</span></span> <span data-ttu-id="e7830-119">最后，更正其中一个错误，然后对 XML 文档的一部分进行部分验证。</span><span class="sxs-lookup"><span data-stu-id="e7830-119">Finally, one of the errors is corrected, and then part of the XML document is partially validated.</span></span>

[!code-cpp[XmlDocumentValidation.Load#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlDocumentValidation.Load/CPP/XmlDocumentValidationExample.cpp#1)]
[!code-csharp[XmlDocumentValidation.Load#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Load/CS/XmlDocumentValidationExample.cs#1)]
[!code-vb[XmlDocumentValidation.Load#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Load/VB/XmlDocumentValidationExample.vb#1)]

<span data-ttu-id="e7830-120">该示例使用 `contosoBooks.xml` 文件作为输入。</span><span class="sxs-lookup"><span data-stu-id="e7830-120">The example takes the `contosoBooks.xml` file as input.</span></span>

[!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]

<span data-ttu-id="e7830-121">该示例还使用 `contosoBooks.xsd` 文件作为输入。</span><span class="sxs-lookup"><span data-stu-id="e7830-121">The example also takes the `contosoBooks.xsd` file as input.</span></span>

[!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]

<span data-ttu-id="e7830-122">如果在 XML 数据加载到 DOM 时进行验证，请考虑下列事项。</span><span class="sxs-lookup"><span data-stu-id="e7830-122">Consider the following when validating XML data as it is loaded into the DOM.</span></span>

- <span data-ttu-id="e7830-123">在上述示例中，每当遇到无效类型时就会调用 <xref:System.Xml.XmlReaderSettings.ValidationEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="e7830-123">In the above example, the <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> is called whenever an invalid type is encountered.</span></span> <span data-ttu-id="e7830-124">如果 <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> 在验证 <xref:System.Xml.XmlReader> 时未设置，则在任何属性或元素类型与验证架构中指定的相应类型不匹配的情况下调用 <xref:System.Xml.Schema.XmlSchemaValidationException> 时会引发 <xref:System.Xml.XmlDocument.Load%2A>。</span><span class="sxs-lookup"><span data-stu-id="e7830-124">If a <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> is not set on the validating <xref:System.Xml.XmlReader>,an <xref:System.Xml.Schema.XmlSchemaValidationException> is thrown when <xref:System.Xml.XmlDocument.Load%2A> is called if any attribute or element type does not match the corresponding type specified in the validating schema.</span></span>

- <span data-ttu-id="e7830-125">如果 XML 文档加载到 <xref:System.Xml.XmlDocument> 对象，并且具有关联的架构来定义默认值，<xref:System.Xml.XmlDocument> 会像在 XML 文档中一样对待这些默认值。</span><span class="sxs-lookup"><span data-stu-id="e7830-125">When an XML document is loaded into an <xref:System.Xml.XmlDocument> object with an associated schema that defines default values, the <xref:System.Xml.XmlDocument> treats these defaults as if they appeared in the XML document.</span></span> <span data-ttu-id="e7830-126">这意味着，对于架构中的默认元素，<xref:System.Xml.XmlReader.IsEmptyElement%2A> 属性始终返回 `false`。</span><span class="sxs-lookup"><span data-stu-id="e7830-126">This means that the <xref:System.Xml.XmlReader.IsEmptyElement%2A> property always returns `false` for an element that was defaulted from the schema.</span></span> <span data-ttu-id="e7830-127">即使在 XML 文档中，也将编写为空元素。</span><span class="sxs-lookup"><span data-stu-id="e7830-127">Even if in the XML document, it was written as an empty element.</span></span>

## <a name="validating-an-xml-document-in-the-dom"></a><span data-ttu-id="e7830-128">在 DOM 中验证 XML 文档</span><span class="sxs-lookup"><span data-stu-id="e7830-128">Validating an XML Document in the DOM</span></span>

<span data-ttu-id="e7830-129"><xref:System.Xml.XmlDocument.Validate%2A> 类的 <xref:System.Xml.XmlDocument> 方法针对 <xref:System.Xml.XmlDocument> 对象的 <xref:System.Xml.XmlDocument.Schemas%2A> 属性中的架构，验证加载到 DOM 的 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="e7830-129">The <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class validates the XML data loaded in the DOM against the schemas in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property.</span></span> <span data-ttu-id="e7830-130">成功验证之后，将应用架构的默认值，文本值根据需要转换为原子值，类型信息与经过验证的信息项关联。</span><span class="sxs-lookup"><span data-stu-id="e7830-130">After successful validation, schema defaults are applied, text values are converted to atomic values as necessary, and type information is associated with validated information items.</span></span> <span data-ttu-id="e7830-131">因此，类型化 XML 数据将替换以前非类型化的 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="e7830-131">As a result, typed XML data replaces previously untyped XML data.</span></span>

<span data-ttu-id="e7830-132">下面的示例与上面“在 XML 文档加载到 DOM 时进行验证”中的示例类似。</span><span class="sxs-lookup"><span data-stu-id="e7830-132">The example below is similar to the example in "Validating an XML Document As It Is Loaded into the DOM" above.</span></span> <span data-ttu-id="e7830-133">在此示例中，XML 文档不是在加载到 DOM 时进行验证，而是在加载到 DOM 之后，使用 <xref:System.Xml.XmlDocument.Validate%2A> 类的 <xref:System.Xml.XmlDocument> 方法进行验证。</span><span class="sxs-lookup"><span data-stu-id="e7830-133">In this example, the XML document is not validated as it is loaded into the DOM, but rather is validated after it has been loaded into the DOM using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="e7830-134"><xref:System.Xml.XmlDocument.Validate%2A> 方法针对 <xref:System.Xml.XmlDocument.Schemas%2A> 的 <xref:System.Xml.XmlDocument> 属性中包含的 XML 架构验证 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="e7830-134">The <xref:System.Xml.XmlDocument.Validate%2A> method validates the XML document against the XML schemas contained in the <xref:System.Xml.XmlDocument.Schemas%2A> property of the <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="e7830-135">对 XML 文档进行无效的修改，然后重新验证文档，造成架构验证错误。</span><span class="sxs-lookup"><span data-stu-id="e7830-135">Invalid modifications are then made to the XML document, and the document is then revalidated, causing schema validation errors.</span></span> <span data-ttu-id="e7830-136">最后，更正其中一个错误，然后对 XML 文档的一部分进行部分验证。</span><span class="sxs-lookup"><span data-stu-id="e7830-136">Finally, one of the errors is corrected, and then part of the XML document is partially validated.</span></span>

[!code-csharp[XmlDocumentValidation.Validate#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Validate/CS/XmlDocumentValidationExample.cs#1)]
[!code-vb[XmlDocumentValidation.Validate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Validate/VB/XmlDocumentValidationExample.vb#1)]

<span data-ttu-id="e7830-137">该示例使用 `contosoBooks.xml` 和 `contosoBooks.xsd` 文件作为输入，这两个文件在上面的“在 XML 文档加载到 DOM 时进行验证”中提到。</span><span class="sxs-lookup"><span data-stu-id="e7830-137">The example takes as input the `contosoBooks.xml` and `contosoBooks.xsd` files referred to in "Validating an XML Document as it is Loaded into the DOM" above.</span></span>

## <a name="handling-validation-errors-and-warnings"></a><span data-ttu-id="e7830-138">处理验证错误和警告</span><span class="sxs-lookup"><span data-stu-id="e7830-138">Handling Validation Errors and Warnings</span></span>

<span data-ttu-id="e7830-139">XML 架构验证错误在验证加载到 DOM 的 XML 数据时报告。</span><span class="sxs-lookup"><span data-stu-id="e7830-139">XML schema validation errors are reported when validating XML data loaded in the DOM.</span></span> <span data-ttu-id="e7830-140">会通知您在以下过程中发现的所有架构验证错误：在验证正在加载的 XML 数据的时，或在验证以前未经过验证的 XML 文档时。</span><span class="sxs-lookup"><span data-stu-id="e7830-140">You are notified about all schema validation errors found while validating the XML data as it is being loaded, or when validating a previously unvalidated XML document.</span></span>

<span data-ttu-id="e7830-141">验证错误由 <xref:System.Xml.Schema.ValidationEventHandler> 进行处理。</span><span class="sxs-lookup"><span data-stu-id="e7830-141">Validation errors are handled by the <xref:System.Xml.Schema.ValidationEventHandler>.</span></span> <span data-ttu-id="e7830-142">如果 <xref:System.Xml.Schema.ValidationEventHandler> 已分配给 <xref:System.Xml.XmlReaderSettings> 实例或传递给 <xref:System.Xml.XmlDocument.Validate%2A> 类的 <xref:System.Xml.XmlDocument> 方法，<xref:System.Xml.Schema.ValidationEventHandler> 将处理架构验证错误；否则，在遇到架构验证错误时，将引发 <xref:System.Xml.Schema.XmlSchemaValidationException>。</span><span class="sxs-lookup"><span data-stu-id="e7830-142">If a <xref:System.Xml.Schema.ValidationEventHandler> was assigned to the <xref:System.Xml.XmlReaderSettings> instance, or passed to the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class, the <xref:System.Xml.Schema.ValidationEventHandler> will handle schema validation errors; otherwise an <xref:System.Xml.Schema.XmlSchemaValidationException> is raised when a schema validation error is encountered.</span></span>

> [!NOTE]
> <span data-ttu-id="e7830-143">尽管遇到架构验证错误，XML 数据仍会加载到 DOM 中，<xref:System.Xml.Schema.ValidationEventHandler> 引发异常来停止该进程时除外。</span><span class="sxs-lookup"><span data-stu-id="e7830-143">The XML data is loaded into the DOM despite schema validation errors unless your <xref:System.Xml.Schema.ValidationEventHandler> raises an exception to stop the process.</span></span>
>
> <span data-ttu-id="e7830-144">除非为 <xref:System.Xml.Schema.XmlSchemaValidationFlags.ReportValidationWarnings> 对象指定了 <xref:System.Xml.XmlReaderSettings> 标志，否则，不会报告架构验证警告。</span><span class="sxs-lookup"><span data-stu-id="e7830-144">Schema validation warnings are not reported unless the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ReportValidationWarnings> flag is specified to the <xref:System.Xml.XmlReaderSettings> object.</span></span>

 <span data-ttu-id="e7830-145">有关说明 <xref:System.Xml.Schema.ValidationEventHandler> 的示例，请参见上面的“在 XML 文档加载到 DOM 时进行验证”和“在 DOM 中验证 XML 文档”。</span><span class="sxs-lookup"><span data-stu-id="e7830-145">For examples illustrating the <xref:System.Xml.Schema.ValidationEventHandler>, see "Validating an XML Document As It Is Loaded into the DOM" and "Validating an XML Document in the DOM" above.</span></span>

## <a name="see-also"></a><span data-ttu-id="e7830-146">请参阅</span><span class="sxs-lookup"><span data-stu-id="e7830-146">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XmlReader>
- <xref:System.Xml.Schema.ValidationEventHandler>
- <xref:System.Xml.XmlReaderSettings>
- [<span data-ttu-id="e7830-147">使用 DOM 模型处理 XML 数据</span><span class="sxs-lookup"><span data-stu-id="e7830-147">Process XML Data Using the DOM Model</span></span>](process-xml-data-using-the-dom-model.md)
- [<span data-ttu-id="e7830-148">使用 XML 架构</span><span class="sxs-lookup"><span data-stu-id="e7830-148">Working with XML Schemas</span></span>](working-with-xml-schemas.md)

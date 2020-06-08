---
title: 使用 XPathNavigator 验证架构
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 81fa0e41-d9c9-46f0-b22b-50da839c77f5
ms.openlocfilehash: f6e56616543bf7d2ad2e6be4d7bf7cbc50ba3a23
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292002"
---
# <a name="schema-validation-using-xpathnavigator"></a><span data-ttu-id="62ea5-102">使用 XPathNavigator 验证架构</span><span class="sxs-lookup"><span data-stu-id="62ea5-102">Schema Validation using XPathNavigator</span></span>
<span data-ttu-id="62ea5-103">使用 <xref:System.Xml.XmlDocument> 类，可以通过两种方式验证 <xref:System.Xml.XmlDocument> 对象中包含的 XML 内容。</span><span class="sxs-lookup"><span data-stu-id="62ea5-103">Using the <xref:System.Xml.XmlDocument> class, you can validate the XML content contained in an <xref:System.Xml.XmlDocument> object in two ways.</span></span> <span data-ttu-id="62ea5-104">第一种方式是使用验证 <xref:System.Xml.XmlReader> 对象验证 XML 内容，第二种方式是使用 <xref:System.Xml.XmlDocument.Validate%2A> 类的 <xref:System.Xml.XmlDocument> 方法。</span><span class="sxs-lookup"><span data-stu-id="62ea5-104">The first way is to validate the XML content using a validating <xref:System.Xml.XmlReader> object and the second way is to use the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="62ea5-105">还可以使用 <xref:System.Xml.XPath.XPathDocument> 类对 XML 内容执行只读验证。</span><span class="sxs-lookup"><span data-stu-id="62ea5-105">You can also perform read-only validation of XML content using the <xref:System.Xml.XPath.XPathDocument> class.</span></span>  
  
## <a name="validating-xml-data"></a><span data-ttu-id="62ea5-106">验证 XML 数据</span><span class="sxs-lookup"><span data-stu-id="62ea5-106">Validating XML Data</span></span>  
 <span data-ttu-id="62ea5-107">默认情况下，<xref:System.Xml.XmlDocument> 类不使用 DTD 或 XML 架构定义语言 (XSD) 架构验证来验证 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="62ea5-107">The <xref:System.Xml.XmlDocument> class does not validate an XML document using either DTD or XML schema definition language (XSD) schema validation by default.</span></span> <span data-ttu-id="62ea5-108">只验证 XML 文档的格式是否正确。</span><span class="sxs-lookup"><span data-stu-id="62ea5-108">It only verifies that the XML document is well formed.</span></span>  
  
 <span data-ttu-id="62ea5-109">第一种验证 XML 文档的方式是使用验证 <xref:System.Xml.XmlDocument> 对象，在文档加载到 <xref:System.Xml.XmlReader> 对象时进行验证。</span><span class="sxs-lookup"><span data-stu-id="62ea5-109">The first way to validate an XML document is to validate the document as it is loaded into an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="62ea5-110">第二种方式是使用 <xref:System.Xml.XmlDocument.Validate%2A> 类的 <xref:System.Xml.XmlDocument> 方法验证以前非类型化的 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="62ea5-110">The second way is to validate a previously untyped XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="62ea5-111">在这两种情况下，均可以使用 <xref:System.Xml.XmlDocument.Validate%2A> 类的 <xref:System.Xml.XmlDocument> 方法重新验证对经过验证的 XML 文档的更改。</span><span class="sxs-lookup"><span data-stu-id="62ea5-111">In both cases, changes to the validated XML document can be revalidated using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
### <a name="validating-a-document-as-it-is-loaded"></a><span data-ttu-id="62ea5-112">在文档加载时进行验证</span><span class="sxs-lookup"><span data-stu-id="62ea5-112">Validating a Document as it is Loaded</span></span>  
 <span data-ttu-id="62ea5-113">验证 <xref:System.Xml.XmlReader> 对象通过将 <xref:System.Xml.XmlReaderSettings> 对象传递给 <xref:System.Xml.XmlReader.Create%2A> 类的 <xref:System.Xml.XmlReader> 方法进行创建，该方法使用 <xref:System.Xml.XmlReaderSettings> 对象作为参数。</span><span class="sxs-lookup"><span data-stu-id="62ea5-113">A validating <xref:System.Xml.XmlReader> object is created by passing an <xref:System.Xml.XmlReaderSettings> object to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class that takes an <xref:System.Xml.XmlReaderSettings> object as a parameter.</span></span> <span data-ttu-id="62ea5-114">作为参数传递的 <xref:System.Xml.XmlReaderSettings> 对象将 <xref:System.Xml.XmlReaderSettings.ValidationType%2A> 属性设置为 `Schema`，并将 <xref:System.Xml.XmlDocument> 对象中包含的 XML 文档的 XML 架构添加到其 <xref:System.Xml.XmlReaderSettings.Schemas%2A> 属性中。</span><span class="sxs-lookup"><span data-stu-id="62ea5-114">The <xref:System.Xml.XmlReaderSettings> object passed as a parameter has a <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property set to `Schema` and an XML Schema for the XML document contained in the <xref:System.Xml.XmlDocument> object added to its <xref:System.Xml.XmlReaderSettings.Schemas%2A> property.</span></span> <span data-ttu-id="62ea5-115">然后，使用验证 <xref:System.Xml.XmlReader> 对象创建 <xref:System.Xml.XmlDocument> 对象。</span><span class="sxs-lookup"><span data-stu-id="62ea5-115">The validating <xref:System.Xml.XmlReader> object is then used to create the <xref:System.Xml.XmlDocument> object.</span></span>  
  
 <span data-ttu-id="62ea5-116">以下示例在 `contosoBooks.xml` 文件加载到 <xref:System.Xml.XmlDocument> 对象时进行验证，方法是使用验证 <xref:System.Xml.XmlDocument> 对象创建 <xref:System.Xml.XmlReader> 对象。</span><span class="sxs-lookup"><span data-stu-id="62ea5-116">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="62ea5-117">因为 XML 文档符合其架构，所以，未生成任何架构验证错误或警告。</span><span class="sxs-lookup"><span data-stu-id="62ea5-117">Because the XML document is valid according to its schema, no schema validation errors or warnings are generated.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Schema  
Imports System.Xml.XPath  
  
Class ValidatingReaderExample  
  
    Shared Sub Main(ByVal args() As String)  
  
        Try  
            Dim settings As XmlReaderSettings = New XmlReaderSettings()  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
            settings.ValidationType = ValidationType.Schema  
  
            Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
            Dim document As XmlDocument = New XmlDocument()  
            document.Load(reader)  
            Dim navigator As XPathNavigator = document.CreateNavigator()  
  
        Catch e As Exception  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message)  
        End Try  
  
    End Sub  
  
    Shared Sub SchemaValidationHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
        Select Case e.Severity  
            Case XmlSeverityType.Error  
                Console.WriteLine("Schema Validation Error: {0}", e.Message)  
                Exit Sub  
            Case XmlSeverityType.Warning  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message)  
                Exit Sub  
        End Select  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.Xml.XPath;  
  
class ValidatingReaderExample  
{  
    static void Main(string[] args)  
    {  
        try  
        {  
            XmlReaderSettings settings = new XmlReaderSettings();  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
            settings.ValidationType = ValidationType.Schema;  
  
            XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
            XmlDocument document = new XmlDocument();  
            document.Load(reader);  
            XPathNavigator navigator = document.CreateNavigator();  
        }  
        catch (Exception e)  
        {  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message);  
        }  
    }  
  
    static void SchemaValidationHandler(object sender, ValidationEventArgs e)  
    {  
        switch (e.Severity)  
        {  
            case XmlSeverityType.Error:  
                Console.WriteLine("Schema Validation Error: {0}", e.Message);  
                break;  
            case XmlSeverityType.Warning:  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message);  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="62ea5-118">该示例使用 `contosoBooks.xml` 文件作为输入。</span><span class="sxs-lookup"><span data-stu-id="62ea5-118">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="62ea5-119">该示例还使用 `contosoBooks.xsd` 作为输入。</span><span class="sxs-lookup"><span data-stu-id="62ea5-119">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="62ea5-120">在上面的示例中，如果任何属性或元素类型不匹配验证架构中指定的相应类型，则调用 <xref:System.Xml.Schema.XmlSchemaValidationException> 时将引发 <xref:System.Xml.XmlDocument.Load%2A>。</span><span class="sxs-lookup"><span data-stu-id="62ea5-120">In the above example, an <xref:System.Xml.Schema.XmlSchemaValidationException> will be thrown when <xref:System.Xml.XmlDocument.Load%2A> is called if any attribute or element type does not match the corresponding type specified in the validating schema.</span></span> <span data-ttu-id="62ea5-121">如果在验证 <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> 时设置 <xref:System.Xml.XmlReader>，则遇到无效类型时将调用 <xref:System.Xml.XmlReaderSettings.ValidationEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="62ea5-121">If a <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> is set on the validating <xref:System.Xml.XmlReader>, the <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> will get called whenever an invalid type is encountered.</span></span>  
  
 <span data-ttu-id="62ea5-122">由 <xref:System.Xml.Schema.XmlSchemaException> 访问 <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> 设置为 `invalid` 的属性或元素时，将引发 <xref:System.Xml.XPath.XPathNavigator>。</span><span class="sxs-lookup"><span data-stu-id="62ea5-122">An <xref:System.Xml.Schema.XmlSchemaException> will be thrown when an attribute or element with <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> set to `invalid` is accessed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
 <span data-ttu-id="62ea5-123"><xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> 属性可用于确定用 <xref:System.Xml.XPath.XPathNavigator> 访问属性或元素时单个属性或元素是否有效。</span><span class="sxs-lookup"><span data-stu-id="62ea5-123">The <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> property can be used to determine whether or not an individual attribute or element is valid when accessing attributes or elements with the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="62ea5-124">如果 XML 文档加载到 <xref:System.Xml.XmlDocument> 对象，并且具有关联的架构来定义默认值，<xref:System.Xml.XmlDocument> 对象对待这些默认值就像出现在 XML 文档中一样。</span><span class="sxs-lookup"><span data-stu-id="62ea5-124">When an XML document is loaded into an <xref:System.Xml.XmlDocument> object with an associated schema that defines default values, the <xref:System.Xml.XmlDocument> object treats these defaults as if they appeared in the XML document.</span></span> <span data-ttu-id="62ea5-125">这意味着对于架构中的默认元素，<xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> 属性始终返回 `false`，即使在 XML 文档中，也将编写为空元素。</span><span class="sxs-lookup"><span data-stu-id="62ea5-125">This means that the <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> property  always returns `false` for an element that was defaulted from the schema, even if in the XML document it was written as an empty element.</span></span>  
  
### <a name="validating-a-document-using-the-validate-method"></a><span data-ttu-id="62ea5-126">使用验证方法验证文档</span><span class="sxs-lookup"><span data-stu-id="62ea5-126">Validating a Document using the Validate Method</span></span>  
 <span data-ttu-id="62ea5-127"><xref:System.Xml.XmlDocument.Validate%2A> 类的 <xref:System.Xml.XmlDocument> 方法针对 <xref:System.Xml.XmlDocument> 对象的 <xref:System.Xml.XmlDocument> 属性中指定的架构验证 <xref:System.Xml.XmlDocument.Schemas%2A> 对象中包含的 XML 文档，然后执行信息集增加。</span><span class="sxs-lookup"><span data-stu-id="62ea5-127">The <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class validates the XML document contained in an <xref:System.Xml.XmlDocument> object against the schemas specified in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property and performs infoset augmentation.</span></span> <span data-ttu-id="62ea5-128">结果是 <xref:System.Xml.XmlDocument> 中以前非类型化的 XML 文档由类型化的文档取代。</span><span class="sxs-lookup"><span data-stu-id="62ea5-128">The result is a previously untyped XML document in the <xref:System.Xml.XmlDocument> object replaced with a typed document.</span></span>  
  
 <span data-ttu-id="62ea5-129"><xref:System.Xml.XmlDocument> 对象使用作为参数传递给 <xref:System.Xml.Schema.ValidationEventHandler> 方法的 <xref:System.Xml.XmlDocument.Validate%2A> 委托报告架构验证错误和警告。</span><span class="sxs-lookup"><span data-stu-id="62ea5-129">The <xref:System.Xml.XmlDocument> object reports schema validation errors and warnings using the <xref:System.Xml.Schema.ValidationEventHandler> delegate passed as a parameter to the <xref:System.Xml.XmlDocument.Validate%2A> method.</span></span>  
  
 <span data-ttu-id="62ea5-130">以下示例针对 `contosoBooks.xml` 对象的 <xref:System.Xml.XmlDocument> 属性中包含的 `contosoBooks.xsd` 架构验证 <xref:System.Xml.XmlDocument> 对象中包含的 <xref:System.Xml.XmlDocument.Schemas%2A> 文件。</span><span class="sxs-lookup"><span data-stu-id="62ea5-130">The following example validates the `contosoBooks.xml` file contained in the <xref:System.Xml.XmlDocument> object against the `contosoBooks.xsd` schema contained in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Schema  
Imports System.Xml.XPath  
  
Class ValidateExample  
  
    Shared Sub Main(ByVal args() As String)  
  
        Dim document As XmlDocument = New XmlDocument()  
        document.Load("contosoBooks.xml")  
        Dim navigator As XPathNavigator = document.CreateNavigator()  
  
        document.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
        Dim validation As ValidationEventHandler = New ValidationEventHandler(AddressOf SchemaValidationHandler)  
  
        document.Validate(validation)  
  
    End Sub  
  
    Shared Sub SchemaValidationHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
        Select Case e.Severity  
            Case XmlSeverityType.Error  
                Console.WriteLine("Schema Validation Error: {0}", e.Message)  
                Exit Sub  
            Case XmlSeverityType.Warning  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message)  
                Exit Sub  
        End Select  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.Xml.XPath;  
  
class ValidateExample  
{  
    static void Main(string[] args)  
    {  
        XmlDocument document = new XmlDocument();  
        document.Load("contosoBooks.xml");  
        XPathNavigator navigator = document.CreateNavigator();  
  
        document.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
        ValidationEventHandler validation = new ValidationEventHandler(SchemaValidationHandler);  
  
        document.Validate(validation);  
    }  
  
    static void SchemaValidationHandler(object sender, ValidationEventArgs e)  
    {  
        switch (e.Severity)  
        {  
            case XmlSeverityType.Error:  
                Console.WriteLine("Schema Validation Error: {0}", e.Message);  
                break;  
            case XmlSeverityType.Warning:  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message);  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="62ea5-131">该示例使用 `contosoBooks.xml` 文件作为输入。</span><span class="sxs-lookup"><span data-stu-id="62ea5-131">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="62ea5-132">该示例还使用 `contosoBooks.xsd` 作为输入。</span><span class="sxs-lookup"><span data-stu-id="62ea5-132">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a><span data-ttu-id="62ea5-133">验证修改</span><span class="sxs-lookup"><span data-stu-id="62ea5-133">Validating Modifications</span></span>  
 <span data-ttu-id="62ea5-134">对 XML 文档进行修改之后，可以使用 <xref:System.Xml.XmlDocument.Validate%2A> 类的 <xref:System.Xml.XmlDocument> 方法针对 XML 文档的架构验证修改。</span><span class="sxs-lookup"><span data-stu-id="62ea5-134">After modifications are made to an XML document, you can validate the modifications against the schema for the XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="62ea5-135">以下示例在 `contosoBooks.xml` 文件加载到 <xref:System.Xml.XmlDocument> 对象时进行验证，方法是使用验证 <xref:System.Xml.XmlDocument> 对象创建 <xref:System.Xml.XmlReader> 对象。</span><span class="sxs-lookup"><span data-stu-id="62ea5-135">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="62ea5-136">XML 文档在加载时成功进行验证，未生成任何架构验证错误或警告。</span><span class="sxs-lookup"><span data-stu-id="62ea5-136">The XML document is validated successfully as it is loaded without generating any schema validation errors or warnings.</span></span> <span data-ttu-id="62ea5-137">然后，示例对 XML 文档进行了两处符合 `contosoBooks.xsd` 架构的修改。</span><span class="sxs-lookup"><span data-stu-id="62ea5-137">The example then makes two modifications to the XML document that are invalid according to the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="62ea5-138">第一处修改是插入一个无效的子元素，从而引发架构验证错误，第二处修改是将类型化节点的值设置为不符合节点类型的值，从而引发异常。</span><span class="sxs-lookup"><span data-stu-id="62ea5-138">The first modification inserts an invalid child element resulting in a schema validation error, and the second modification sets the value of a typed node to a value that is invalid according to the type of the node resulting in an exception.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Schema  
Imports System.Xml.XPath  
  
Class ValidatingReaderExample  
  
    Shared Sub Main(ByVal args() As String)  
  
        Try  
            Dim settings As XmlReaderSettings = New XmlReaderSettings()  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
            settings.ValidationType = ValidationType.Schema  
  
            Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
            Dim document As XmlDocument = New XmlDocument()  
            document.Load(reader)  
            Dim navigator As XPathNavigator = document.CreateNavigator()  
  
            Dim validation As ValidationEventHandler = New ValidationEventHandler(AddressOf SchemaValidationHandler)  
  
            navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
            navigator.MoveToChild("book", "http://www.contoso.com/books")  
            navigator.MoveToChild("author", "http://www.contoso.com/books")  
  
            navigator.AppendChild("<title>Book Title</title>")  
  
            document.Validate(validation)  
  
            navigator.MoveToParent()  
            navigator.MoveToChild("price", "http://www.contoso.com/books")  
            navigator.SetTypedValue(DateTime.Now)  
        Catch e As Exception  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message)  
        End Try  
  
    End Sub  
  
    Shared Sub SchemaValidationHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
        Select Case e.Severity  
            Case XmlSeverityType.Error  
                Console.WriteLine("Schema Validation Error: {0}", e.Message)  
                Exit Sub  
            Case XmlSeverityType.Warning  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message)  
                Exit Sub  
        End Select  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.Xml.XPath;  
  
class ValidatingReaderExample  
{  
    static void Main(string[] args)  
    {  
        try  
        {  
            XmlReaderSettings settings = new XmlReaderSettings();  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
            settings.ValidationType = ValidationType.Schema;  
  
            XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
            XmlDocument document = new XmlDocument();  
            document.Load(reader);  
            XPathNavigator navigator = document.CreateNavigator();  
  
            ValidationEventHandler validation = new ValidationEventHandler(SchemaValidationHandler);  
  
            navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
            navigator.MoveToChild("book", "http://www.contoso.com/books");  
            navigator.MoveToChild("author", "http://www.contoso.com/books");  
  
            navigator.AppendChild("<title>Book Title</title>");  
  
            document.Validate(validation);  
  
            navigator.MoveToParent();  
            navigator.MoveToChild("price", "http://www.contoso.com/books");  
            navigator.SetTypedValue(DateTime.Now);  
        }  
        catch (Exception e)  
        {  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message);  
        }  
    }  
  
    static void SchemaValidationHandler(object sender, ValidationEventArgs e)  
    {  
        switch (e.Severity)  
        {  
            case XmlSeverityType.Error:  
                Console.WriteLine("Schema Validation Error: {0}", e.Message);  
                break;  
            case XmlSeverityType.Warning:  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message);  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="62ea5-139">该示例使用 `contosoBooks.xml` 文件作为输入。</span><span class="sxs-lookup"><span data-stu-id="62ea5-139">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="62ea5-140">该示例还使用 `contosoBooks.xsd` 作为输入。</span><span class="sxs-lookup"><span data-stu-id="62ea5-140">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="62ea5-141">在上面的示例中，对 <xref:System.Xml.XmlDocument> 对象中包含的 XML 文档进行了两处修改。</span><span class="sxs-lookup"><span data-stu-id="62ea5-141">In the example above, two modifications are made to the XML document contained in the <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="62ea5-142">在 XML 文档加载时，遇到的任何架构验证错误将通过验证事件处理程序方法进行处理并写入控制台。</span><span class="sxs-lookup"><span data-stu-id="62ea5-142">As the XML document was loaded, any schema validation errors encountered would have been handled by the validation event handler method and written to the console.</span></span>  
  
 <span data-ttu-id="62ea5-143">在此示例中，加载 XML 文档之后引入验证错误，并使用 <xref:System.Xml.XmlDocument.Validate%2A> 类的 <xref:System.Xml.XmlDocument> 方法发现错误。</span><span class="sxs-lookup"><span data-stu-id="62ea5-143">In this example, the validation errors were introduced after the XML document was loaded and were found using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="62ea5-144">使用 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 类的 <xref:System.Xml.XPath.XPathNavigator> 方法进行的修改引发了 <xref:System.InvalidCastException>，因为新值不符合节点的架构类型。</span><span class="sxs-lookup"><span data-stu-id="62ea5-144">Modifications made using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class resulted in an <xref:System.InvalidCastException> because the new value was invalid according to the schema type of the node.</span></span>  
  
 <span data-ttu-id="62ea5-145">若要详细了解如何使用 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 方法修改值，请参阅[使用 XPathNavigator 修改 XML 数据](modify-xml-data-using-xpathnavigator.md)主题。</span><span class="sxs-lookup"><span data-stu-id="62ea5-145">For more information about modifying values using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method, see the [Modify XML Data using XPathNavigator](modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
### <a name="read-only-validation"></a><span data-ttu-id="62ea5-146">只读验证</span><span class="sxs-lookup"><span data-stu-id="62ea5-146">Read-Only Validation</span></span>  
 <span data-ttu-id="62ea5-147"><xref:System.Xml.XPath.XPathDocument> 类是 XML 文档在内存中的只读表示形式。</span><span class="sxs-lookup"><span data-stu-id="62ea5-147">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory representation of an XML document.</span></span> <span data-ttu-id="62ea5-148"><xref:System.Xml.XPath.XPathDocument> 类和 <xref:System.Xml.XmlDocument> 类均创建 <xref:System.Xml.XPath.XPathNavigator> 对象来浏览和编辑 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="62ea5-148">Both the <xref:System.Xml.XPath.XPathDocument> class and the <xref:System.Xml.XmlDocument> class create <xref:System.Xml.XPath.XPathNavigator> objects to navigate and edit XML documents.</span></span> <span data-ttu-id="62ea5-149">因为 <xref:System.Xml.XPath.XPathDocument> 类是只读类，从 <xref:System.Xml.XPath.XPathNavigator> 对象返回的 <xref:System.Xml.XPath.XPathDocument> 对象不能编辑 <xref:System.Xml.XPath.XPathDocument> 对象中包含的 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="62ea5-149">Because the <xref:System.Xml.XPath.XPathDocument> class is a read-only class, <xref:System.Xml.XPath.XPathNavigator> object's returned from <xref:System.Xml.XPath.XPathDocument> objects cannot edit the XML document contained in the <xref:System.Xml.XPath.XPathDocument> object.</span></span>  
  
 <span data-ttu-id="62ea5-150">在验证时，可以创建一个 <xref:System.Xml.XPath.XPathDocument> 对象，就好像使用验证 <xref:System.Xml.XmlDocument> 对象创建 <xref:System.Xml.XmlReader> 对象一样，如本主题前面所述。</span><span class="sxs-lookup"><span data-stu-id="62ea5-150">In the case of validation, you can create an <xref:System.Xml.XPath.XPathDocument> object just like you create an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object as described earlier in this topic.</span></span> <span data-ttu-id="62ea5-151"><xref:System.Xml.XPath.XPathDocument> 对象在 XML 文档加载时进行验证，但是因为不能编辑 <xref:System.Xml.XPath.XPathDocument> 对象中的 XML 数据，所以，无法重新验证 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="62ea5-151">The <xref:System.Xml.XPath.XPathDocument> object validates the XML document as it is loaded, but because you cannot edit the XML data in the <xref:System.Xml.XPath.XPathDocument> object, you cannot revalidate the XML document.</span></span>  
  
 <span data-ttu-id="62ea5-152">若要详细了解只读和可编辑 <xref:System.Xml.XPath.XPathNavigator> 对象，请参阅[使用 XPathDocument 和 XmlDocument 读取 XML 数据](reading-xml-data-using-xpathdocument-and-xmldocument.md)主题。</span><span class="sxs-lookup"><span data-stu-id="62ea5-152">For more information about read-only and editable <xref:System.Xml.XPath.XPathNavigator> objects, see the [Reading XML Data using XPathDocument and XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62ea5-153">请参阅</span><span class="sxs-lookup"><span data-stu-id="62ea5-153">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="62ea5-154">使用 XPath 数据模型处理 XML 数据</span><span class="sxs-lookup"><span data-stu-id="62ea5-154">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="62ea5-155">使用 XPathDocument 和 XmlDocument 读取 XML 数据</span><span class="sxs-lookup"><span data-stu-id="62ea5-155">Reading XML Data using XPathDocument and XmlDocument</span></span>](reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [<span data-ttu-id="62ea5-156">使用 XPathNavigator 选择、计算和匹配 XML 数据</span><span class="sxs-lookup"><span data-stu-id="62ea5-156">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="62ea5-157">使用 XPathNavigator 访问 XML 数据</span><span class="sxs-lookup"><span data-stu-id="62ea5-157">Accessing XML Data using XPathNavigator</span></span>](accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="62ea5-158">使用 XPathNavigator 编辑 XML 数据</span><span class="sxs-lookup"><span data-stu-id="62ea5-158">Editing XML Data using XPathNavigator</span></span>](editing-xml-data-using-xpathnavigator.md)

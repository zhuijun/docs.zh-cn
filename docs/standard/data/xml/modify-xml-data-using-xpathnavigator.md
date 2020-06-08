---
title: 使用 XPathNavigator 修改 XML 数据
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 03a7c5a1-b296-4af4-b209-043c958dc0a5
ms.openlocfilehash: 3b64bc8666274798ebaefc87ef3883fcec1ef6b1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288831"
---
# <a name="modify-xml-data-using-xpathnavigator"></a><span data-ttu-id="91165-102">使用 XPathNavigator 修改 XML 数据</span><span class="sxs-lookup"><span data-stu-id="91165-102">Modify XML Data using XPathNavigator</span></span>
<span data-ttu-id="91165-103"><xref:System.Xml.XPath.XPathNavigator> 类提供一组方法用于修改 XML 文档中的节点和值。</span><span class="sxs-lookup"><span data-stu-id="91165-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to modify nodes and values in an XML document.</span></span> <span data-ttu-id="91165-104">要使用这些方法，<xref:System.Xml.XPath.XPathNavigator> 对象必须可编辑，即其 <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> 属性必须为 `true`。</span><span class="sxs-lookup"><span data-stu-id="91165-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="91165-105">可以编辑 XML 文档的 <xref:System.Xml.XPath.XPathNavigator> 对象由 <xref:System.Xml.XmlDocument.CreateNavigator%2A> 类的 <xref:System.Xml.XmlDocument> 方法创建。</span><span class="sxs-lookup"><span data-stu-id="91165-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="91165-106">由 <xref:System.Xml.XPath.XPathNavigator> 类创建的 <xref:System.Xml.XPath.XPathDocument> 对象是只读的，如果尝试使用由 <xref:System.Xml.XPath.XPathNavigator> 对象创建的 <xref:System.Xml.XPath.XPathDocument> 对象的编辑方法，将引发 <xref:System.NotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="91165-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object result in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="91165-107">若要详细了解如何创建可编辑 <xref:System.Xml.XPath.XPathNavigator> 对象，请参阅[使用 XPathDocument 和 XmlDocument 读取 XML 数据](reading-xml-data-using-xpathdocument-and-xmldocument.md)。</span><span class="sxs-lookup"><span data-stu-id="91165-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="modifying-nodes"></a><span data-ttu-id="91165-108">修改节点</span><span class="sxs-lookup"><span data-stu-id="91165-108">Modifying Nodes</span></span>  
 <span data-ttu-id="91165-109">更改节点值的一种简单的方法是，使用 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 类的 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 和 <xref:System.Xml.XPath.XPathNavigator> 方法。</span><span class="sxs-lookup"><span data-stu-id="91165-109">A simple technique for changing the value of a node is to use the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 <span data-ttu-id="91165-110">下表列出在不同节点类型上使用这些方法的结果。</span><span class="sxs-lookup"><span data-stu-id="91165-110">The following table lists the effects of these methods on different node types.</span></span>  
  
|<xref:System.Xml.XPath.XPathNodeType>|<span data-ttu-id="91165-111">更改的数据</span><span class="sxs-lookup"><span data-stu-id="91165-111">Data Changed</span></span>|  
|---------------------------------------------------------------------------------------------------------------------------------------------|------------------|  
|<xref:System.Xml.XPath.XPathNodeType.Root>|<span data-ttu-id="91165-112">不支持。</span><span class="sxs-lookup"><span data-stu-id="91165-112">Not supported.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Element>|<span data-ttu-id="91165-113">元素的内容。</span><span class="sxs-lookup"><span data-stu-id="91165-113">The content of the element.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Attribute>|<span data-ttu-id="91165-114">属性的值。</span><span class="sxs-lookup"><span data-stu-id="91165-114">The value of the attribute.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Text>|<span data-ttu-id="91165-115">文本内容。</span><span class="sxs-lookup"><span data-stu-id="91165-115">The text content.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>|<span data-ttu-id="91165-116">内容（不包括目标）。</span><span class="sxs-lookup"><span data-stu-id="91165-116">The content, excluding the target.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Comment>|<span data-ttu-id="91165-117">注释的内容。</span><span class="sxs-lookup"><span data-stu-id="91165-117">The content of the comment.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Namespace>|<span data-ttu-id="91165-118">不受支持。</span><span class="sxs-lookup"><span data-stu-id="91165-118">Not Supported.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="91165-119">不支持编辑 <xref:System.Xml.XPath.XPathNodeType.Namespace> 节点或 <xref:System.Xml.XPath.XPathNodeType.Root> 节点。</span><span class="sxs-lookup"><span data-stu-id="91165-119">Editing <xref:System.Xml.XPath.XPathNodeType.Namespace> nodes or the <xref:System.Xml.XPath.XPathNodeType.Root> node is not supported.</span></span>  
  
 <span data-ttu-id="91165-120"><xref:System.Xml.XPath.XPathNavigator> 类还提供一组方法，用于插入和移除节点。</span><span class="sxs-lookup"><span data-stu-id="91165-120">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of methods used to insert and remove nodes.</span></span> <span data-ttu-id="91165-121">若要详细了解如何在 XML 文档中插入和删除节点，请参阅[使用 XPathNavigator 插入 XML 数据](insert-xml-data-using-xpathnavigator.md)和[使用 XPathNavigator 删除 XML 数据](remove-xml-data-using-xpathnavigator.md)主题。</span><span class="sxs-lookup"><span data-stu-id="91165-121">For more information about inserting and removing nodes from an XML document, see the [Insert XML Data using XPathNavigator](insert-xml-data-using-xpathnavigator.md) and [Remove XML Data using XPathNavigator](remove-xml-data-using-xpathnavigator.md) topics.</span></span>  
  
### <a name="modifying-untyped-values"></a><span data-ttu-id="91165-122">修改非类型化的值</span><span class="sxs-lookup"><span data-stu-id="91165-122">Modifying Untyped Values</span></span>  
 <span data-ttu-id="91165-123"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 方法只需将作为参数传递的非类型化的 `string` 值作为 <xref:System.Xml.XPath.XPathNavigator> 对象当前所处的节点的值插入。</span><span class="sxs-lookup"><span data-stu-id="91165-123">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="91165-124">插入的值没有任何类型或不验证新值是否符合节点的类型（如果架构信息可用）。</span><span class="sxs-lookup"><span data-stu-id="91165-124">The value is inserted without any type or without verifying that the new value is valid according to the type of the node if schema information is available.</span></span>  
  
 <span data-ttu-id="91165-125">在以下示例中，<xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 方法用于更新 `price` 文件中的所有 `contosoBooks.xml` 元素。</span><span class="sxs-lookup"><span data-stu-id="91165-125">In the following example, the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method is used to update all `price` elements in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 <span data-ttu-id="91165-126">该示例使用 `contosoBooks.xml` 文件作为输入。</span><span class="sxs-lookup"><span data-stu-id="91165-126">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="modifying-typed-values"></a><span data-ttu-id="91165-127">修改类型化的值</span><span class="sxs-lookup"><span data-stu-id="91165-127">Modifying Typed Values</span></span>  
 <span data-ttu-id="91165-128">如果节点的类型为 W3C XML 架构的简单类型，在设置值之前，将针对简单类型的各个方面检查通过 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 方法插入的新值。</span><span class="sxs-lookup"><span data-stu-id="91165-128">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="91165-129">如果新值不符合节点的类型（例如在类型为 `-1` 的元素上设置值 `xs:positiveInteger`），将引发异常。</span><span class="sxs-lookup"><span data-stu-id="91165-129">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span>  
  
 <span data-ttu-id="91165-130">以下示例尝试将 `price` 文件中第一个 `book` 元素的 `contosoBooks.xml` 元素的值更改为 <xref:System.DateTime> 值。</span><span class="sxs-lookup"><span data-stu-id="91165-130">The following example attempts to change the value of the `price` element of the first `book` element in the `contosoBooks.xml` file to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="91165-131">因为在 `price` 文件中将 `xs:decimal` 元素的 XML 架构类型定义为 `contosoBooks.xsd`，所以，这样做将引发异常。</span><span class="sxs-lookup"><span data-stu-id="91165-131">Because the XML Schema type of the `price` element is defined as `xs:decimal` in the `contosoBooks.xsd` files, this results in an exception.</span></span>  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetTypedValue(DateTime.Now)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetTypedValue(DateTime.Now);  
```  
  
 <span data-ttu-id="91165-132">该示例使用 `contosoBooks.xml` 文件作为输入。</span><span class="sxs-lookup"><span data-stu-id="91165-132">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="91165-133">该示例还使用 `contosoBooks.xsd` 作为输入。</span><span class="sxs-lookup"><span data-stu-id="91165-133">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
#### <a name="the-effects-of-editing-strongly-typed-xml-data"></a><span data-ttu-id="91165-134">编辑强类型的 XML 数据的结果</span><span class="sxs-lookup"><span data-stu-id="91165-134">The Effects of Editing Strongly Typed XML Data</span></span>  
 <span data-ttu-id="91165-135"><xref:System.Xml.XPath.XPathNavigator> 类使用 W3C XML 架构作为描述强类型 XML 的基础。</span><span class="sxs-lookup"><span data-stu-id="91165-135">The <xref:System.Xml.XPath.XPathNavigator> class uses the W3C XML Schema as a basis for describing strongly typed XML.</span></span> <span data-ttu-id="91165-136">元素和属性可以基于对 W3C XML 架构文档的验证，使用类型信息添加批注。</span><span class="sxs-lookup"><span data-stu-id="91165-136">Elements and attributes can be annotated with type information based on validation against a W3C XML Schema document.</span></span> <span data-ttu-id="91165-137">可以包含其他元素或属性的元素称为复杂类型，而只能包含文本内容的元素称为简单类型。</span><span class="sxs-lookup"><span data-stu-id="91165-137">Elements that can contain other elements or attributes are called complex types, while those that can only contain textual content are called simple types.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="91165-138">属性只能具有简单类型。</span><span class="sxs-lookup"><span data-stu-id="91165-138">Attributes can only have simple types.</span></span>  
  
 <span data-ttu-id="91165-139">如果元素或属性符合其类型定义特定的所有规则，将被认为架构有效。</span><span class="sxs-lookup"><span data-stu-id="91165-139">An element or attribute can be considered to be schema-valid if it conforms to all the rules specific to its type definition.</span></span> <span data-ttu-id="91165-140">具有简单类型 `xs:int` 的元素必须包含介于 -2147483648 到 2147483647 之间的数值，才属于架构有效。</span><span class="sxs-lookup"><span data-stu-id="91165-140">An element that has the simple type `xs:int` has to contain a numeric value between -2147483648 and 2147483647 to be schema-valid.</span></span> <span data-ttu-id="91165-141">对于复杂类型，元素的架构有效性取决于其子元素和属性的架构有效性。</span><span class="sxs-lookup"><span data-stu-id="91165-141">For complex types, the schema-validity of the element is dependent on the schema-validity of its child elements and attributes.</span></span> <span data-ttu-id="91165-142">因此，如果元素符合其复杂类型定义，其所有子元素和属性也符合各自的类型定义。</span><span class="sxs-lookup"><span data-stu-id="91165-142">Thus if an element is valid against its complex type definition, all its child elements and attributes are valid against their type definitions.</span></span> <span data-ttu-id="91165-143">同样，即使元素只有一个子元素或属性不符合其类型定义，或有效性未知，该元素也将无效或属于有效性未知。</span><span class="sxs-lookup"><span data-stu-id="91165-143">Similarly, if even one of the child elements or attributes of an element is invalid against its type definition, or has an unknown validity, the element is also either invalid or of unknown validity.</span></span>  
  
 <span data-ttu-id="91165-144">假设元素的有效性取决于其子元素和属性的有效性，对任意一项的修改都会造成元素有效性的改变（如果元素以前有效）。</span><span class="sxs-lookup"><span data-stu-id="91165-144">Given that the validity of an element is dependent on the validity of its child elements and attributes, modifications to either result in altering the validity of the element if it was previously valid.</span></span> <span data-ttu-id="91165-145">尤其是，如果插入、更新或删除了元素的子元素或属性，元素的有效性将变为未知。</span><span class="sxs-lookup"><span data-stu-id="91165-145">Specifically, if the child elements or attributes of an element are inserted, updated, or deleted, then the validity of the element becomes unknown.</span></span> <span data-ttu-id="91165-146">此情况通过将元素的 <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> 属性的 <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> 属性设置 <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown> 来表示。</span><span class="sxs-lookup"><span data-stu-id="91165-146">This is represented by the <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> property of the element's <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property being set to <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>.</span></span> <span data-ttu-id="91165-147">另外，此结果将在 XML 文档中循环向上层叠，因为元素的父元素（及其父元素，依此类推）的有效性也将变为未知。</span><span class="sxs-lookup"><span data-stu-id="91165-147">Furthermore, this effect cascades upwards recursively across the XML document, because the validity of the element's parent element (and its parent element, and so on) also becomes unknown.</span></span>  
  
 <span data-ttu-id="91165-148">若要详细了解架构有效性和 <xref:System.Xml.XPath.XPathNavigator> 类，请参阅[使用 XPathNavigator 验证架构](schema-validation-using-xpathnavigator.md)。</span><span class="sxs-lookup"><span data-stu-id="91165-148">For more information about schema validation and the <xref:System.Xml.XPath.XPathNavigator> class, see [Schema Validation using XPathNavigator](schema-validation-using-xpathnavigator.md).</span></span>  
  
### <a name="modifying-attributes"></a><span data-ttu-id="91165-149">修改属性</span><span class="sxs-lookup"><span data-stu-id="91165-149">Modifying Attributes</span></span>  
 <span data-ttu-id="91165-150"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 和 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 方法可以用于修改非类型化和类型化的属性节点以及“修改节点”一节中列出的其他节点类型。</span><span class="sxs-lookup"><span data-stu-id="91165-150">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods can be used to modify untyped and typed attribute nodes as well as the other node types listed in the "Modifying Nodes" section.</span></span>  
  
 <span data-ttu-id="91165-151">以下示例更改 `genre` 文件中第一个 `book` 元素的 `books.xml` 属性值。</span><span class="sxs-lookup"><span data-stu-id="91165-151">The following example changes the value of the `genre` attribute of the first `book` element in the `books.xml` file.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", String.Empty)  
navigator.MoveToChild("book", String.Empty)  
navigator.MoveToAttribute("genre", String.Empty)  
  
navigator.SetValue("non-fiction")  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", String.Empty);  
navigator.MoveToChild("book", String.Empty);  
navigator.MoveToAttribute("genre", String.Empty);  
  
navigator.SetValue("non-fiction");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="91165-152">有关 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 和 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 方法的更多信息，请参见“修改非类型化的值”和“修改类型化的值”小节。</span><span class="sxs-lookup"><span data-stu-id="91165-152">For more information about the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods, see the "Modifying Untyped Values" and "Modifying Typed Values" sections.</span></span>  
  
## <a name="innerxml-and-outerxml-properties"></a><span data-ttu-id="91165-153">InnerXml 和 OuterXml 属性</span><span class="sxs-lookup"><span data-stu-id="91165-153">InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="91165-154"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> 类的 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 和 <xref:System.Xml.XPath.XPathNavigator> 属性更改 <xref:System.Xml.XPath.XPathNavigator> 对象当前所处的节点的 XML 标记。</span><span class="sxs-lookup"><span data-stu-id="91165-154">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="91165-155"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> 属性更改 <xref:System.Xml.XPath.XPathNavigator> 对象当前所处的子节点以及给定 XML `string` 的已分析内容的 XML 标记。</span><span class="sxs-lookup"><span data-stu-id="91165-155">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="91165-156">同样，<xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 属性更改 <xref:System.Xml.XPath.XPathNavigator> 对象当前所处的子节点以及当前节点本身的 XML 标记。</span><span class="sxs-lookup"><span data-stu-id="91165-156">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="91165-157">以下示例使用 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 属性修改 `price` 元素的值，并在 `discount` 文件中的第一个 `book` 元素上插入新的 `contosoBooks.xml` 属性。</span><span class="sxs-lookup"><span data-stu-id="91165-157">The following example uses the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property to modify the value of the `price` element and insert a new `discount` attribute on the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml");  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>"  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>";  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="91165-158">该示例使用 `contosoBooks.xml` 文件作为输入。</span><span class="sxs-lookup"><span data-stu-id="91165-158">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
## <a name="modifying-namespace-nodes"></a><span data-ttu-id="91165-159">修改命名空间节点</span><span class="sxs-lookup"><span data-stu-id="91165-159">Modifying Namespace Nodes</span></span>  
 <span data-ttu-id="91165-160">在文档对象模型 (DOM) 中，将命名空间声明看做就好像是可以插入、更新和删除的常规属性。</span><span class="sxs-lookup"><span data-stu-id="91165-160">In the Document Object Model (DOM), namespace declarations are treated as if they are regular attributes that can be inserted, updated and deleted.</span></span> <span data-ttu-id="91165-161"><xref:System.Xml.XPath.XPathNavigator> 类不允许对命名空间节点执行此类操作，因为更改命名空间节点的值可能会更改元素和属性在命名空间节点范围内的标识，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="91165-161">The <xref:System.Xml.XPath.XPathNavigator> class does not allow such operations on namespace nodes because altering the value of a namespace node can change the identity of the elements and attributes within the scope of the namespace node as illustrated in the following example.</span></span>  
  
```xml  
<root xmlns="http://www.contoso.com">  
    <child />  
</root>  
```  
  
 <span data-ttu-id="91165-162">如果上面的 XML 示例通过以下方式更改，可以有效地为文档中的每个元素重命名，因为每个元素的命名空间 URI 的值已更改。</span><span class="sxs-lookup"><span data-stu-id="91165-162">If the XML example above is changed in the following way, this effectively renames every element in the document because the value of each element's namespace URI is changed.</span></span>  
  
```xml  
<root xmlns="urn:contoso.com">  
    <child />  
</root>  
```  
  
 <span data-ttu-id="91165-163"><xref:System.Xml.XPath.XPathNavigator> 类允许插入与所插入范围的命名空间声明不冲突的命名空间节点。</span><span class="sxs-lookup"><span data-stu-id="91165-163">Inserting namespace nodes that do not conflict with namespace declarations at the scope that they are inserted in is allowed by the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="91165-164">在这种情况下，命名空间声明不是在 XML 文档中的较低范围声明，不会造成以下示例中所示的重命名情况。</span><span class="sxs-lookup"><span data-stu-id="91165-164">In this case, the namespace declarations are not declared at lower scopes in the XML document and does not result in renaming as illustrated in the following example.</span></span>  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent>  
        <a:child />  
    </parent>  
</root>  
```  
  
 <span data-ttu-id="91165-165">如果上面的 XML 示例通过以下方式更改，命名空间声明将在 XML 文档中其他命名空间声明范围以下正确地传播。</span><span class="sxs-lookup"><span data-stu-id="91165-165">If the XML example above is changed in the following way, the namespace declarations are correctly propagated across the XML document below the scope of the other namespace declaration.</span></span>  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent a:parent-id="1234" xmlns:a="http://www.contoso.com/parent-id">  
        <a:child xmlns:a="http://www.contoso.com/" />  
    </parent>  
</root>  
```  
  
 <span data-ttu-id="91165-166">在上面的 XML 示例中，在 `a:parent-id` 命名空间的 `parent` 元素上插入了属性 `http://www.contoso.com/parent-id`。</span><span class="sxs-lookup"><span data-stu-id="91165-166">In the XML example above, the attribute `a:parent-id` is inserted on the `parent` element in the `http://www.contoso.com/parent-id` namespace.</span></span> <span data-ttu-id="91165-167"><xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> 方法用于在位于 `parent` 元素时插入属性。</span><span class="sxs-lookup"><span data-stu-id="91165-167">The <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> method is used to insert the attribute while positioned on the `parent` element.</span></span> <span data-ttu-id="91165-168">`http://www.contoso.com` 命名空间声明通过 <xref:System.Xml.XPath.XPathNavigator> 类自动插入，以保持 XML 文档其他部分的一致性。</span><span class="sxs-lookup"><span data-stu-id="91165-168">The `http://www.contoso.com` namespace declaration is automatically inserted by the <xref:System.Xml.XPath.XPathNavigator> class to preserve the consistency of the rest of the XML document.</span></span>  
  
## <a name="modifying-entity-reference-nodes"></a><span data-ttu-id="91165-169">修改实体引用节点</span><span class="sxs-lookup"><span data-stu-id="91165-169">Modifying Entity Reference Nodes</span></span>  
 <span data-ttu-id="91165-170"><xref:System.Xml.XmlDocument> 对象中的实体引用节点是只读的，不能使用 <xref:System.Xml.XPath.XPathNavigator> 或 <xref:System.Xml.XmlNode> 类进行编辑。</span><span class="sxs-lookup"><span data-stu-id="91165-170">Entity reference nodes in an <xref:System.Xml.XmlDocument> object are read-only and cannot be edited using either the <xref:System.Xml.XPath.XPathNavigator> or <xref:System.Xml.XmlNode> classes.</span></span> <span data-ttu-id="91165-171">如果尝试修改实体引用节点，将引发 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="91165-171">Any attempt to modify an entity reference node results in an <xref:System.InvalidOperationException>.</span></span>  
  
## <a name="modifying-xsinil-nodes"></a><span data-ttu-id="91165-172">修改 xsi:nil 节点</span><span class="sxs-lookup"><span data-stu-id="91165-172">Modifying xsi:nil Nodes</span></span>  
 <span data-ttu-id="91165-173">W3C XML 架构建议引入了元素可为零的概念。</span><span class="sxs-lookup"><span data-stu-id="91165-173">The W3C XML Schema recommendation introduces the concept of an element being nillable.</span></span> <span data-ttu-id="91165-174">如果元素可为零，元素可能会没有任何内容并且仍然有效。</span><span class="sxs-lookup"><span data-stu-id="91165-174">When an element is nillable, it is possible for the element to have no content and still be valid.</span></span> <span data-ttu-id="91165-175">元素可为零的概念与对象可为 `null` 的概念类似。</span><span class="sxs-lookup"><span data-stu-id="91165-175">The concept of an element being nillable is similar to the concept of an object being `null`.</span></span> <span data-ttu-id="91165-176">主要区别是 `null` 对象不能通过任何方式访问，而 `xsi:nil` 元素仍具有可以访问的属性，但是没有任何内容（子元素或文本）。</span><span class="sxs-lookup"><span data-stu-id="91165-176">The main difference is that a `null` object cannot be accessed in any way, while an `xsi:nil` element still has properties such as attributes that can be accessed, but has no content (child elements or text).</span></span> <span data-ttu-id="91165-177">如果 XML 文档中的某个元素上存在值为 `xsi:nil` 的 `true` 属性，表示元素没有任何内容。</span><span class="sxs-lookup"><span data-stu-id="91165-177">The existence of the `xsi:nil` attribute with a value of `true` on an element in an XML document is used to indicate that an element has no content.</span></span>  
  
 <span data-ttu-id="91165-178">如果使用 <xref:System.Xml.XPath.XPathNavigator> 对象向 `xsi:nil` 属性值为 `true` 的有效元素中添加内容，其 `xsi:nil` 属性的值将设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="91165-178">If an <xref:System.Xml.XPath.XPathNavigator> object is used to add content to a valid element with an `xsi:nil` attribute with a value of `true`, the value of its `xsi:nil` attribute is set to `false`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="91165-179">如果 `xsi:nil` 属性设置为 `false` 的元素的内容已删除，该属性的值不会更改为 `true`。</span><span class="sxs-lookup"><span data-stu-id="91165-179">If the content of an element with an `xsi:nil` attribute set to `false` is deleted, the value of the attribute is not changed to `true`.</span></span>  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="91165-180">保存 XML 文档</span><span class="sxs-lookup"><span data-stu-id="91165-180">Saving an XML Document</span></span>  
 <span data-ttu-id="91165-181">使用 <xref:System.Xml.XmlDocument> 类的方法保存本主题中所述的编辑方法对 <xref:System.Xml.XmlDocument> 对象的更改。</span><span class="sxs-lookup"><span data-stu-id="91165-181">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the editing methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="91165-182">若要详细了解如何保存对 <xref:System.Xml.XmlDocument> 对象所做的更改，请参阅[保存和编写文档](saving-and-writing-a-document.md)。</span><span class="sxs-lookup"><span data-stu-id="91165-182">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91165-183">请参阅</span><span class="sxs-lookup"><span data-stu-id="91165-183">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="91165-184">使用 XPath 数据模型处理 XML 数据</span><span class="sxs-lookup"><span data-stu-id="91165-184">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="91165-185">使用 XPathNavigator 插入 XML 数据</span><span class="sxs-lookup"><span data-stu-id="91165-185">Insert XML Data using XPathNavigator</span></span>](insert-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="91165-186">使用 XPathNavigator 删除 XML 数据</span><span class="sxs-lookup"><span data-stu-id="91165-186">Remove XML Data using XPathNavigator</span></span>](remove-xml-data-using-xpathnavigator.md)

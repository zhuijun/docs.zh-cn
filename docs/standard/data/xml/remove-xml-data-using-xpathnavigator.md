---
title: 使用 XPathNavigator 移除 XML 数据
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9f436bca-1b96-494b-a6d2-e102c7551752
ms.openlocfilehash: fa331757fac3f30ee86a24bbd0ee12b5f1031a4b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288662"
---
# <a name="remove-xml-data-using-xpathnavigator"></a><span data-ttu-id="8fc40-102">使用 XPathNavigator 移除 XML 数据</span><span class="sxs-lookup"><span data-stu-id="8fc40-102">Remove XML Data using XPathNavigator</span></span>
<span data-ttu-id="8fc40-103"><xref:System.Xml.XPath.XPathNavigator> 类提供一组方法用于移除 XML 文档中的节点和值。</span><span class="sxs-lookup"><span data-stu-id="8fc40-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to remove nodes and values from an XML document.</span></span> <span data-ttu-id="8fc40-104">要使用这些方法，<xref:System.Xml.XPath.XPathNavigator> 对象必须可编辑，即其 <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> 属性必须为 `true`。</span><span class="sxs-lookup"><span data-stu-id="8fc40-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="8fc40-105">可以编辑 XML 文档的 <xref:System.Xml.XPath.XPathNavigator> 对象由 <xref:System.Xml.XmlDocument.CreateNavigator%2A> 类的 <xref:System.Xml.XmlDocument> 方法创建。</span><span class="sxs-lookup"><span data-stu-id="8fc40-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="8fc40-106">由 <xref:System.Xml.XPath.XPathNavigator> 类创建的 <xref:System.Xml.XPath.XPathDocument> 对象是只读的，如果尝试使用由 <xref:System.Xml.XPath.XPathNavigator> 对象创建的 <xref:System.Xml.XPath.XPathDocument> 对象的编辑方法，将引发 <xref:System.NotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="8fc40-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object results in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="8fc40-107">若要详细了解如何创建可编辑 <xref:System.Xml.XPath.XPathNavigator> 对象，请参阅[使用 XPathDocument 和 XmlDocument 读取 XML 数据](reading-xml-data-using-xpathdocument-and-xmldocument.md)。</span><span class="sxs-lookup"><span data-stu-id="8fc40-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="removing-nodes"></a><span data-ttu-id="8fc40-108">移除节点</span><span class="sxs-lookup"><span data-stu-id="8fc40-108">Removing Nodes</span></span>  
 <span data-ttu-id="8fc40-109"><xref:System.Xml.XPath.XPathNavigator> 类提供 <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> 方法来移除 XML 文档中的节点。</span><span class="sxs-lookup"><span data-stu-id="8fc40-109">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method to remove nodes from an XML document.</span></span>  
  
### <a name="removing-a-node"></a><span data-ttu-id="8fc40-110">移除节点</span><span class="sxs-lookup"><span data-stu-id="8fc40-110">Removing a Node</span></span>  
 <span data-ttu-id="8fc40-111"><xref:System.Xml.XPath.XPathNavigator> 类提供 <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> 方法来删除 XML 文档中 <xref:System.Xml.XPath.XPathNavigator> 对象当前所处的节点。</span><span class="sxs-lookup"><span data-stu-id="8fc40-111">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method to delete the current node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on from an XML document.</span></span>  
  
 <span data-ttu-id="8fc40-112">使用 <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> 方法删除了某个节点之后，该节点无法再从 <xref:System.Xml.XmlDocument> 对象的根节点访问。</span><span class="sxs-lookup"><span data-stu-id="8fc40-112">After a node has been deleted using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method, it is no longer reachable from the root of the <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="8fc40-113">节点删除之后，<xref:System.Xml.XPath.XPathNavigator> 将位于所删除节点的父节点。</span><span class="sxs-lookup"><span data-stu-id="8fc40-113">After a node has been deleted, the <xref:System.Xml.XPath.XPathNavigator> is positioned on the parent node of the deleted node.</span></span>  
  
 <span data-ttu-id="8fc40-114">删除操作不会影响位于所删除节点上的任何 <xref:System.Xml.XPath.XPathNavigator> 对象的位置。</span><span class="sxs-lookup"><span data-stu-id="8fc40-114">A delete operation doesn't affect the position of any <xref:System.Xml.XPath.XPathNavigator> object positioned on the deleted node.</span></span> <span data-ttu-id="8fc40-115">这些 <xref:System.Xml.XPath.XPathNavigator> 对象可以在已删除的子树内移动，在这方面看是有效的，但是不能使用 <xref:System.Xml.XPath.XPathNavigator> 类常规的节点集浏览方法移至主节点树。</span><span class="sxs-lookup"><span data-stu-id="8fc40-115">These <xref:System.Xml.XPath.XPathNavigator> objects are valid in the sense that they can move within the deleted subtree, but cannot be moved to the main node tree using the regular node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8fc40-116"><xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> 类的 <xref:System.Xml.XPath.XPathNavigator> 方法可以用于将这些 <xref:System.Xml.XPath.XPathNavigator> 对象移回主节点树，或从主节点树移至已删除的子树。</span><span class="sxs-lookup"><span data-stu-id="8fc40-116">The <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class can be used to move these <xref:System.Xml.XPath.XPathNavigator> objects back into the main node tree, or from the main node tree to the deleted subtree.</span></span>  
  
 <span data-ttu-id="8fc40-117">在以下示例中，`price` 文件的第一个 `book` 元素的 `contosoBooks.xml` 元素使用 <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> 方法删除。</span><span class="sxs-lookup"><span data-stu-id="8fc40-117">In the following example, the `price` element of the first `book` element of the `contosoBooks.xml` file is deleted using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method.</span></span> <span data-ttu-id="8fc40-118">在 <xref:System.Xml.XPath.XPathNavigator> 元素删除之后，`price` 对象的位置位于父级的 `book` 元素上。</span><span class="sxs-lookup"><span data-stu-id="8fc40-118">The position of the <xref:System.Xml.XPath.XPathNavigator> object after the `price` element is deleted is on the parent `book` element.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.DeleteSelf()  
  
Console.WriteLine("Position after delete: {0}", navigator.Name)  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.DeleteSelf();  
  
Console.WriteLine("Position after delete: {0}", navigator.Name);  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="8fc40-119">该示例使用 `contosoBooks.xml` 文件作为输入。</span><span class="sxs-lookup"><span data-stu-id="8fc40-119">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-an-attribute-node"></a><span data-ttu-id="8fc40-120">移除属性节点</span><span class="sxs-lookup"><span data-stu-id="8fc40-120">Removing an Attribute Node</span></span>  
 <span data-ttu-id="8fc40-121">属性节点使用 <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> 方法从 XML 文档中移除。</span><span class="sxs-lookup"><span data-stu-id="8fc40-121">Attribute nodes are removed from an XML document using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method.</span></span>  
  
 <span data-ttu-id="8fc40-122">属性节点删除之后，无法再从 <xref:System.Xml.XmlDocument> 对象的根节点中访问，<xref:System.Xml.XPath.XPathNavigator> 对象将位于父元素上。</span><span class="sxs-lookup"><span data-stu-id="8fc40-122">After an attribute node has been deleted, it is no longer reachable from the root node of an <xref:System.Xml.XmlDocument> object and the <xref:System.Xml.XPath.XPathNavigator> object is positioned on the parent element.</span></span>  
  
#### <a name="default-attributes"></a><span data-ttu-id="8fc40-123">默认属性</span><span class="sxs-lookup"><span data-stu-id="8fc40-123">Default Attributes</span></span>  
 <span data-ttu-id="8fc40-124">无论用于移除属性的方法是什么，当移除在 XML 文档的 DTD 或 XML 架构中定义为默认属性的属性时有特殊限制。</span><span class="sxs-lookup"><span data-stu-id="8fc40-124">Regardless of the method used to remove attributes, there are special limitations on removing attributes that are defined as default attributes in the DTD or XML Schema for the XML document.</span></span> <span data-ttu-id="8fc40-125">除非同时移除了默认属性所属的元素，否则不能移除默认属性。</span><span class="sxs-lookup"><span data-stu-id="8fc40-125">Default attributes cannot be removed unless the element they belong to is also removed.</span></span> <span data-ttu-id="8fc40-126">对于声明了默认属性的元素，默认属性始终存在，因此，删除默认属性将使替换属性插入元素并初始化为所声明的默认值。</span><span class="sxs-lookup"><span data-stu-id="8fc40-126">Default attributes are always present for elements that have default attributes declared, and as a result, deleting a default attribute results in a replacement attribute being inserted into the element and initialized to the default value that was declared.</span></span>  
  
## <a name="removing-values"></a><span data-ttu-id="8fc40-127">移除值</span><span class="sxs-lookup"><span data-stu-id="8fc40-127">Removing Values</span></span>  
 <span data-ttu-id="8fc40-128"><xref:System.Xml.XPath.XPathNavigator> 类提供 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 和 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 方法来移除 XML 文档中非类型化的和类型化的值。</span><span class="sxs-lookup"><span data-stu-id="8fc40-128">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods to remove untyped and typed values from an XML document.</span></span>  
  
### <a name="removing-untyped-values"></a><span data-ttu-id="8fc40-129">移除非类型化的值</span><span class="sxs-lookup"><span data-stu-id="8fc40-129">Removing Untyped Values</span></span>  
 <span data-ttu-id="8fc40-130"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 方法只需将作为参数传递的非类型化的 `string` 值作为 <xref:System.Xml.XPath.XPathNavigator> 对象当前所处的节点的值插入。</span><span class="sxs-lookup"><span data-stu-id="8fc40-130">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="8fc40-131">如果将空字符串传递给 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 方法，将移除当前节点的值。</span><span class="sxs-lookup"><span data-stu-id="8fc40-131">Passing an empty string to the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method removes the value of the current node.</span></span>  
  
 <span data-ttu-id="8fc40-132">以下示例使用 `price` 方法移除 `book` 文件中第一个 `contosoBooks.xml` 元素的 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 元素的值。</span><span class="sxs-lookup"><span data-stu-id="8fc40-132">The following example removes the value of the `price` element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetValue("")  
  
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
  
navigator.SetValue("");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="8fc40-133">该示例使用 `contosoBooks.xml` 文件作为输入。</span><span class="sxs-lookup"><span data-stu-id="8fc40-133">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-typed-values"></a><span data-ttu-id="8fc40-134">移除类型化的值</span><span class="sxs-lookup"><span data-stu-id="8fc40-134">Removing Typed Values</span></span>  
 <span data-ttu-id="8fc40-135">如果节点的类型为 W3C XML 架构的简单类型，在设置值之前，将针对简单类型的各个方面检查通过 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 方法插入的新值。</span><span class="sxs-lookup"><span data-stu-id="8fc40-135">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="8fc40-136">如果新值不符合节点的类型（例如在类型为 `-1` 的元素上设置值 `xs:positiveInteger`），将引发异常。</span><span class="sxs-lookup"><span data-stu-id="8fc40-136">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span> <span data-ttu-id="8fc40-137"><xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 方法也不能作为参数传递 `null`。</span><span class="sxs-lookup"><span data-stu-id="8fc40-137">The <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method also cannot be passed `null` as a parameter.</span></span> <span data-ttu-id="8fc40-138">因此，移除类型化节点的值必须符合节点的架构类型。</span><span class="sxs-lookup"><span data-stu-id="8fc40-138">As a result removing the value of a typed node must comply with the schema type of the node.</span></span>  
  
 <span data-ttu-id="8fc40-139">以下示例使用 `price` 方法移除 `book` 文件中第一个 `contosoBooks.xml` 元素的 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 元素的值，方法是将值设置为 `0`。</span><span class="sxs-lookup"><span data-stu-id="8fc40-139">The following example removes the value of the `price` element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method by setting the value to `0`.</span></span> <span data-ttu-id="8fc40-140">节点的值未移除，但是图书的价格已根据 `xs:decimal` 的数据类型移除。</span><span class="sxs-lookup"><span data-stu-id="8fc40-140">The value of the node is not removed, but the price of the book has been removed according to its data type of `xs:decimal`.</span></span>  
  
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
  
navigator.SetTypedValue(0)  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
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
  
navigator.SetTypedValue(0);  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
## <a name="namespace-nodes"></a><span data-ttu-id="8fc40-141">命名空间节点</span><span class="sxs-lookup"><span data-stu-id="8fc40-141">Namespace Nodes</span></span>  
 <span data-ttu-id="8fc40-142">命名空间节点不能从 <xref:System.Xml.XmlDocument> 对象中删除。</span><span class="sxs-lookup"><span data-stu-id="8fc40-142">Namespace nodes cannot be deleted from an <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="8fc40-143">如果尝试使用 <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> 方法删除命名空间节点，将引发异常。</span><span class="sxs-lookup"><span data-stu-id="8fc40-143">Attempts to delete namespace nodes using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method results in an exception.</span></span>  
  
## <a name="the-innerxml-and-outerxml-properties"></a><span data-ttu-id="8fc40-144">InnerXml 和 OuterXml 属性</span><span class="sxs-lookup"><span data-stu-id="8fc40-144">The InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="8fc40-145"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> 类的 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 和 <xref:System.Xml.XPath.XPathNavigator> 属性更改 <xref:System.Xml.XPath.XPathNavigator> 对象当前所处的节点的 XML 标记。</span><span class="sxs-lookup"><span data-stu-id="8fc40-145">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="8fc40-146"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> 属性更改 <xref:System.Xml.XPath.XPathNavigator> 对象当前所处的子节点以及给定 XML `string` 的已分析内容的 XML 标记。</span><span class="sxs-lookup"><span data-stu-id="8fc40-146">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="8fc40-147">同样，<xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 属性更改 <xref:System.Xml.XPath.XPathNavigator> 对象当前所处的子节点以及当前节点本身的 XML 标记。</span><span class="sxs-lookup"><span data-stu-id="8fc40-147">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="8fc40-148">除了本主题中所述的方法之外，<xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> 和 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 属性也可以用于移除 XML 文档中的节点和值。</span><span class="sxs-lookup"><span data-stu-id="8fc40-148">In addition to the methods described in this topic, the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties can be used to remove nodes and values from an XML document.</span></span> <span data-ttu-id="8fc40-149">若要详细了解如何使用 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> 和 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 属性修改节点，请参阅[使用 XPathNavigator 修改 XML 数据](modify-xml-data-using-xpathnavigator.md)主题。</span><span class="sxs-lookup"><span data-stu-id="8fc40-149">For more information about using the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties to modify nodes, see the [Modify XML Data using XPathNavigator](modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="8fc40-150">保存 XML 文档</span><span class="sxs-lookup"><span data-stu-id="8fc40-150">Saving an XML Document</span></span>  
 <span data-ttu-id="8fc40-151">使用 <xref:System.Xml.XmlDocument> 类的方法保存本主题中所述的方法对 <xref:System.Xml.XmlDocument> 对象的更改。</span><span class="sxs-lookup"><span data-stu-id="8fc40-151">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="8fc40-152">若要详细了解如何保存对 <xref:System.Xml.XmlDocument> 对象所做的更改，请参阅[保存和编写文档](saving-and-writing-a-document.md)。</span><span class="sxs-lookup"><span data-stu-id="8fc40-152">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fc40-153">请参阅</span><span class="sxs-lookup"><span data-stu-id="8fc40-153">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="8fc40-154">使用 XPath 数据模型处理 XML 数据</span><span class="sxs-lookup"><span data-stu-id="8fc40-154">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="8fc40-155">使用 XPathNavigator 插入 XML 数据</span><span class="sxs-lookup"><span data-stu-id="8fc40-155">Insert XML Data using XPathNavigator</span></span>](insert-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="8fc40-156">使用 XPathNavigator 修改 XML 数据</span><span class="sxs-lookup"><span data-stu-id="8fc40-156">Modify XML Data using XPathNavigator</span></span>](modify-xml-data-using-xpathnavigator.md)

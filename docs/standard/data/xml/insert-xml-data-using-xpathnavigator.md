---
title: 使用 XPathNavigator 插入 XML 数据
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2ed8c28b-b88d-4be7-9c87-92df01f0821f
ms.openlocfilehash: 1dbe1a709f7c1b527a1754ab943a0a10ff52c6e8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289182"
---
# <a name="insert-xml-data-using-xpathnavigator"></a><span data-ttu-id="33152-102">使用 XPathNavigator 插入 XML 数据</span><span class="sxs-lookup"><span data-stu-id="33152-102">Insert XML Data using XPathNavigator</span></span>
<span data-ttu-id="33152-103"><xref:System.Xml.XPath.XPathNavigator> 类提供一组方法用于在 XML 文档中插入同级节点、子节点和属性节点。</span><span class="sxs-lookup"><span data-stu-id="33152-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to insert sibling, child, and attribute nodes in an XML document.</span></span> <span data-ttu-id="33152-104">要使用这些方法，<xref:System.Xml.XPath.XPathNavigator> 对象必须可编辑，即其 <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> 属性必须为 `true`。</span><span class="sxs-lookup"><span data-stu-id="33152-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="33152-105">可以编辑 XML 文档的 <xref:System.Xml.XPath.XPathNavigator> 对象由 <xref:System.Xml.XmlDocument.CreateNavigator%2A> 类的 <xref:System.Xml.XmlDocument> 方法创建。</span><span class="sxs-lookup"><span data-stu-id="33152-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="33152-106">由 <xref:System.Xml.XPath.XPathNavigator> 类创建的 <xref:System.Xml.XPath.XPathDocument> 对象是只读的，如果尝试使用由 <xref:System.Xml.XPath.XPathNavigator> 对象创建的 <xref:System.Xml.XPath.XPathDocument> 对象的编辑方法，将引发 <xref:System.NotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="33152-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object results in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="33152-107">若要详细了解如何创建可编辑 <xref:System.Xml.XPath.XPathNavigator> 对象，请参阅[使用 XPathDocument 和 XmlDocument 读取 XML 数据](reading-xml-data-using-xpathdocument-and-xmldocument.md)。</span><span class="sxs-lookup"><span data-stu-id="33152-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="inserting-nodes"></a><span data-ttu-id="33152-108">插入节点</span><span class="sxs-lookup"><span data-stu-id="33152-108">Inserting Nodes</span></span>  
 <span data-ttu-id="33152-109"><xref:System.Xml.XPath.XPathNavigator> 类提供在 XML 文档中插入同级节点、子节点和属性节点的方法。</span><span class="sxs-lookup"><span data-stu-id="33152-109">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to insert sibling, child, and attribute nodes in an XML document.</span></span> <span data-ttu-id="33152-110">通过这些方法可以在与 <xref:System.Xml.XPath.XPathNavigator> 对象的当前位置有关的不同位置插入节点和属性，如下面各节所述。</span><span class="sxs-lookup"><span data-stu-id="33152-110">These methods allow you to insert nodes and attributes in different locations in relation to the current position of an <xref:System.Xml.XPath.XPathNavigator> object and are described in the following sections.</span></span>  
  
### <a name="inserting-sibling-nodes"></a><span data-ttu-id="33152-111">插入同级节点</span><span class="sxs-lookup"><span data-stu-id="33152-111">Inserting Sibling Nodes</span></span>  
 <span data-ttu-id="33152-112"><xref:System.Xml.XPath.XPathNavigator> 类提供下列方法来插入同辈节点。</span><span class="sxs-lookup"><span data-stu-id="33152-112">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert sibling nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 <span data-ttu-id="33152-113">这些方法在 <xref:System.Xml.XPath.XPathNavigator> 对象当前所处的节点之前和之后插入同辈节点。</span><span class="sxs-lookup"><span data-stu-id="33152-113">These methods insert sibling nodes before and after the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="33152-114"><xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> 和 <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> 方法是重载方法，接受 `string`、<xref:System.Xml.XmlReader> 对象或包含要作为参数添加的同级节点的 <xref:System.Xml.XPath.XPathNavigator> 对象。</span><span class="sxs-lookup"><span data-stu-id="33152-114">The <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> methods are overloaded and accept a `string`, <xref:System.Xml.XmlReader> object, or <xref:System.Xml.XPath.XPathNavigator> object containing the sibling node to add as parameters.</span></span> <span data-ttu-id="33152-115">这两种方法还会返回用于插入同级节点的 <xref:System.Xml.XmlWriter> 对象。</span><span class="sxs-lookup"><span data-stu-id="33152-115">Both methods also return an <xref:System.Xml.XmlWriter> object used to insert sibling nodes.</span></span>  
  
 <span data-ttu-id="33152-116"><xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> 和 <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> 方法使用命名空间前缀、本地名称、命名空间 URI 以及作为参数指定的值在 <xref:System.Xml.XPath.XPathNavigator> 对象当前所处的节点之前和之后插入单个同级节点。</span><span class="sxs-lookup"><span data-stu-id="33152-116">The <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> methods insert a single sibling node before and after the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span>  
  
 <span data-ttu-id="33152-117">在以下示例中，在 `pages` 文件中第一个 `price` 元素的 `book` 子元素之前插入新的 `contosoBooks.xml` 元素。</span><span class="sxs-lookup"><span data-stu-id="33152-117">In the following example a new `pages` element is inserted before the `price` child element of the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 <span data-ttu-id="33152-118">该示例使用 `contosoBooks.xml` 文件作为输入。</span><span class="sxs-lookup"><span data-stu-id="33152-118">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="33152-119">有关 <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>、<xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>、<xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> 和 <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> 方法的更多信息，请参见 <xref:System.Xml.XPath.XPathNavigator> 类参考文档。</span><span class="sxs-lookup"><span data-stu-id="33152-119">For more information about the <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
### <a name="inserting-child-nodes"></a><span data-ttu-id="33152-120">插入子节点</span><span class="sxs-lookup"><span data-stu-id="33152-120">Inserting Child Nodes</span></span>  
 <span data-ttu-id="33152-121"><xref:System.Xml.XPath.XPathNavigator> 类提供下列方法来插入子节点。</span><span class="sxs-lookup"><span data-stu-id="33152-121">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert child nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 <span data-ttu-id="33152-122">这些方法在 <xref:System.Xml.XPath.XPathNavigator> 对象当前所处的节点的子节点列表的结尾和开头添加子节点。</span><span class="sxs-lookup"><span data-stu-id="33152-122">These methods append and prepend child nodes to the end of and the beginning of the list of child nodes of the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="33152-123">与“插入同级节点”一节中的方法类似，<xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> 和 <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> 方法接受 `string`、<xref:System.Xml.XmlReader> 对象或包含要作为参数添加的子节点的 <xref:System.Xml.XPath.XPathNavigator> 对象。</span><span class="sxs-lookup"><span data-stu-id="33152-123">Like the methods in the "Inserting Sibling Nodes" section, the <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> methods accept a `string`, <xref:System.Xml.XmlReader> object, or <xref:System.Xml.XPath.XPathNavigator> object containing the child node to add as parameters.</span></span> <span data-ttu-id="33152-124">这两种方法还会返回用于插入子节点的 <xref:System.Xml.XmlWriter> 对象。</span><span class="sxs-lookup"><span data-stu-id="33152-124">Both methods also return an <xref:System.Xml.XmlWriter> object used to insert child nodes.</span></span>  
  
 <span data-ttu-id="33152-125"><xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> 和 <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> 方法也与“插入同级节点”一节中的方法类似，使用命名空间前缀、本地名称、命名空间 URI 以及作为参数指定的值在 <xref:System.Xml.XPath.XPathNavigator> 对象当前所处的节点的子节点列表的结尾和开头插入单个子节点。</span><span class="sxs-lookup"><span data-stu-id="33152-125">Also like the methods in the "Inserting Sibling Nodes" section, the <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> methods insert a single child node to the end of and the beginning of the list of child nodes of the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span>  
  
 <span data-ttu-id="33152-126">在以下示例中，在 `pages` 文件中第一个 `book` 元素的子元素列表上追加新的 `contosoBooks.xml` 子元素。</span><span class="sxs-lookup"><span data-stu-id="33152-126">In the following example, a new `pages` child element is appended to the list of child elements of the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 <span data-ttu-id="33152-127">该示例使用 `contosoBooks.xml` 文件作为输入。</span><span class="sxs-lookup"><span data-stu-id="33152-127">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="33152-128">有关 <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>、<xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>、<xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> 和 <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> 方法的更多信息，请参见 <xref:System.Xml.XPath.XPathNavigator> 类参考文档。</span><span class="sxs-lookup"><span data-stu-id="33152-128">For more information about the <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
### <a name="inserting-attribute-nodes"></a><span data-ttu-id="33152-129">插入属性节点</span><span class="sxs-lookup"><span data-stu-id="33152-129">Inserting Attribute Nodes</span></span>  
 <span data-ttu-id="33152-130"><xref:System.Xml.XPath.XPathNavigator> 类提供下列方法来插入属性节点。</span><span class="sxs-lookup"><span data-stu-id="33152-130">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert attribute nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 <span data-ttu-id="33152-131">这些方法在 <xref:System.Xml.XPath.XPathNavigator> 对象当前所处的元素节点上插入属性节点。</span><span class="sxs-lookup"><span data-stu-id="33152-131">These methods insert attribute nodes on the element node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="33152-132"><xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> 方法使用命名空间前缀、本地名称、命名空间 URI 以及作为参数指定的值在 <xref:System.Xml.XPath.XPathNavigator> 对象当前所处的元素节点上创建属性节点。</span><span class="sxs-lookup"><span data-stu-id="33152-132">The <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> method creates an attribute node on the element node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span> <span data-ttu-id="33152-133"><xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> 方法返回用于插入属性节点的 <xref:System.Xml.XmlWriter> 对象。</span><span class="sxs-lookup"><span data-stu-id="33152-133">The <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> method returns an <xref:System.Xml.XmlWriter> object used to insert attribute nodes.</span></span>  
  
 <span data-ttu-id="33152-134">在以下示例中，使用从 `discount` 方法返回的 `currency` 对象在 `price` 文件中第一个 `book` 元素的 `contosoBooks.xml` 子元素上创建新的 <xref:System.Xml.XmlWriter> 和 <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="33152-134">In the following example, new `discount` and `currency` attributes are created on the `price` child element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XmlWriter> object returned from the <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> method.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 <span data-ttu-id="33152-135">该示例使用 `contosoBooks.xml` 文件作为输入。</span><span class="sxs-lookup"><span data-stu-id="33152-135">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="33152-136">有关 <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> 和 <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> 方法的更多信息，请参见 <xref:System.Xml.XPath.XPathNavigator> 类参考文档。</span><span class="sxs-lookup"><span data-stu-id="33152-136">For more information about the <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> and <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
## <a name="copying-nodes"></a><span data-ttu-id="33152-137">复制节点</span><span class="sxs-lookup"><span data-stu-id="33152-137">Copying Nodes</span></span>  
 <span data-ttu-id="33152-138">在某些情况下，可能需要使用另一个 XML 文档中的内容填充 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="33152-138">In certain cases you may want to populate an XML document with the contents from another XML document.</span></span> <span data-ttu-id="33152-139"><xref:System.Xml.XPath.XPathNavigator> 类和 <xref:System.Xml.XmlWriter> 类均可以将节点从现有的 <xref:System.Xml.XmlDocument> 对象或 <xref:System.Xml.XmlReader> 对象复制到 <xref:System.Xml.XPath.XPathNavigator> 对象。</span><span class="sxs-lookup"><span data-stu-id="33152-139">Both the <xref:System.Xml.XPath.XPathNavigator> class and the <xref:System.Xml.XmlWriter> class can copy nodes to an <xref:System.Xml.XmlDocument> object from an existing <xref:System.Xml.XmlReader> object or <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
 <span data-ttu-id="33152-140"><xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> 类的 <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>、<xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>、<xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> 和 <xref:System.Xml.XPath.XPathNavigator> 方法全部具有重载，可以接受 <xref:System.Xml.XPath.XPathNavigator> 对象或 <xref:System.Xml.XmlReader> 对象作为参数。</span><span class="sxs-lookup"><span data-stu-id="33152-140">The <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class all have overloads that can accept an <xref:System.Xml.XPath.XPathNavigator> object or an <xref:System.Xml.XmlReader> object as a parameter.</span></span>  
  
 <span data-ttu-id="33152-141"><xref:System.Xml.XmlWriter.WriteNode%2A> 类的 <xref:System.Xml.XmlWriter> 方法具有重载，可以接受 <xref:System.Xml.XmlNode>、<xref:System.Xml.XmlReader> 或 <xref:System.Xml.XPath.XPathNavigator> 对象。</span><span class="sxs-lookup"><span data-stu-id="33152-141">The <xref:System.Xml.XmlWriter.WriteNode%2A> method of the <xref:System.Xml.XmlWriter> class has overloads that can accept an <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>, or <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
 <span data-ttu-id="33152-142">以下示例将所有 `book` 元素从一个文档复制到另一个文档。</span><span class="sxs-lookup"><span data-stu-id="33152-142">The following example copies all the `book` elements from one document to another.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", String.Empty)  
  
Dim newBooks As XPathDocument = New XPathDocument("newBooks.xml")  
Dim newBooksNavigator As XPathNavigator = newBooks.CreateNavigator()  
  
Dim nav As XPathNavigator  
For Each nav in newBooksNavigator.SelectDescendants("book", "", false)  
    navigator.AppendChild(nav)  
Next  
  
document.Save("newBooks.xml");  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", String.Empty);  
  
XPathDocument newBooks = new XPathDocument("newBooks.xml");  
XPathNavigator newBooksNavigator = newBooks.CreateNavigator();  
  
foreach (XPathNavigator nav in newBooksNavigator.SelectDescendants("book", "", false))  
{  
    navigator.AppendChild(nav);  
}  
  
document.Save("newBooks.xml");  
```  
  
## <a name="inserting-values"></a><span data-ttu-id="33152-143">插入值</span><span class="sxs-lookup"><span data-stu-id="33152-143">Inserting Values</span></span>  
 <span data-ttu-id="33152-144"><xref:System.Xml.XPath.XPathNavigator> 类提供 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 和 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 方法来将节点的值插入 <xref:System.Xml.XmlDocument> 对象。</span><span class="sxs-lookup"><span data-stu-id="33152-144">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods to insert values for a node into an <xref:System.Xml.XmlDocument> object.</span></span>  
  
### <a name="inserting-untyped-values"></a><span data-ttu-id="33152-145">插入非类型化的值</span><span class="sxs-lookup"><span data-stu-id="33152-145">Inserting Untyped Values</span></span>  
 <span data-ttu-id="33152-146"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 方法只需将作为参数传递的非类型化的 `string` 值作为 <xref:System.Xml.XPath.XPathNavigator> 对象当前所处的节点的值插入。</span><span class="sxs-lookup"><span data-stu-id="33152-146">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="33152-147">插入的值没有任何类型或不验证新值是否符合节点的类型（如果架构信息可用）。</span><span class="sxs-lookup"><span data-stu-id="33152-147">The value is inserted without any type or without verifying that the new value is valid according to the type of the node if schema information is available.</span></span>  
  
 <span data-ttu-id="33152-148">在以下示例中，<xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 方法用于更新 `price` 文件中的所有 `contosoBooks.xml` 元素。</span><span class="sxs-lookup"><span data-stu-id="33152-148">In the following example, the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method is used to update all `price` elements in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 <span data-ttu-id="33152-149">该示例使用 `contosoBooks.xml` 文件作为输入。</span><span class="sxs-lookup"><span data-stu-id="33152-149">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a><span data-ttu-id="33152-150">插入类型化的值</span><span class="sxs-lookup"><span data-stu-id="33152-150">Inserting Typed Values</span></span>  
 <span data-ttu-id="33152-151">如果节点的类型为 W3C XML 架构的简单类型，在设置值之前，将针对简单类型的各个方面检查通过 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 方法插入的新值。</span><span class="sxs-lookup"><span data-stu-id="33152-151">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="33152-152">如果新值不符合节点的类型（例如在类型为 `-1` 的元素上设置值 `xs:positiveInteger`），将引发异常。</span><span class="sxs-lookup"><span data-stu-id="33152-152">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span>  
  
 <span data-ttu-id="33152-153">以下示例尝试将 `price` 文件中第一个 `book` 元素的 `contosoBooks.xml` 元素的值更改为 <xref:System.DateTime> 值。</span><span class="sxs-lookup"><span data-stu-id="33152-153">The following example attempts to change the value of the `price` element of the first `book` element in the `contosoBooks.xml` file to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="33152-154">因为在 `price` 文件中将 `xs:decimal` 元素的 XML 架构类型定义为 `contosoBooks.xsd`，所以，这样做将引发异常。</span><span class="sxs-lookup"><span data-stu-id="33152-154">Because the XML Schema type of the `price` element is defined as `xs:decimal` in the `contosoBooks.xsd` files, this results in an exception.</span></span>  
  
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
  
 <span data-ttu-id="33152-155">该示例使用 `contosoBooks.xml` 文件作为输入。</span><span class="sxs-lookup"><span data-stu-id="33152-155">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="33152-156">该示例还使用 `contosoBooks.xsd` 作为输入。</span><span class="sxs-lookup"><span data-stu-id="33152-156">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
## <a name="the-innerxml-and-outerxml-properties"></a><span data-ttu-id="33152-157">InnerXml 和 OuterXml 属性</span><span class="sxs-lookup"><span data-stu-id="33152-157">The InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="33152-158"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> 类的 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 和 <xref:System.Xml.XPath.XPathNavigator> 属性更改 <xref:System.Xml.XPath.XPathNavigator> 对象当前所处的节点的 XML 标记。</span><span class="sxs-lookup"><span data-stu-id="33152-158">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="33152-159"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> 属性更改 <xref:System.Xml.XPath.XPathNavigator> 对象当前所处的子节点以及给定 XML `string` 的已分析内容的 XML 标记。</span><span class="sxs-lookup"><span data-stu-id="33152-159">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="33152-160">同样，<xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 属性更改 <xref:System.Xml.XPath.XPathNavigator> 对象当前所处的子节点以及当前节点本身的 XML 标记。</span><span class="sxs-lookup"><span data-stu-id="33152-160">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="33152-161">除了本主题中所述的方法之外，<xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> 和 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 属性也可以用于在 XML 文档中插入节点和值。</span><span class="sxs-lookup"><span data-stu-id="33152-161">In addition to the methods described in this topic, the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties can be used to insert nodes and values in an XML document.</span></span> <span data-ttu-id="33152-162">若要详细了解如何使用 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> 和 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 属性插入节点和值，请参阅[使用 XPathNavigator 修改 XML 数据](modify-xml-data-using-xpathnavigator.md)主题。</span><span class="sxs-lookup"><span data-stu-id="33152-162">For more information about using the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties to insert nodes and values, see the [Modify XML Data using XPathNavigator](modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
## <a name="namespace-and-xmllang-conflicts"></a><span data-ttu-id="33152-163">命名空间和 xml:lang 冲突</span><span class="sxs-lookup"><span data-stu-id="33152-163">Namespace and xml:lang Conflicts</span></span>  
 <span data-ttu-id="33152-164">在使用 `xml:lang` 类的 <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>、<xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>、<xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> 和 <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> 方法（这些方法使用 <xref:System.Xml.XPath.XPathNavigator> 对象作为参数）插入 XML 数据时，可能会发生某些与命名空间和 <xref:System.Xml.XmlReader> 声明的范围有关的冲突，。</span><span class="sxs-lookup"><span data-stu-id="33152-164">Certain conflicts related to the scope of namespace and `xml:lang` declarations can occur when inserting XML data using the <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class that take <xref:System.Xml.XmlReader> objects as parameters.</span></span>  
  
 <span data-ttu-id="33152-165">以下是可能发生的命名空间冲突。</span><span class="sxs-lookup"><span data-stu-id="33152-165">The following are the possible namespace conflicts.</span></span>  
  
- <span data-ttu-id="33152-166">如果在 <xref:System.Xml.XmlReader> 对象的上下文范围内存在命名空间，其中命名空间 URI 映射的前缀不在 <xref:System.Xml.XPath.XPathNavigator> 对象的上下文中，新的命名空间声明将添加到新插入的节点。</span><span class="sxs-lookup"><span data-stu-id="33152-166">If there is a namespace in-scope within the <xref:System.Xml.XmlReader> object's context, where the prefix to namespace URI mapping is not in the <xref:System.Xml.XPath.XPathNavigator> object's context, a new namespace declaration is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="33152-167">如果 <xref:System.Xml.XmlReader> 对象的上下文和 <xref:System.Xml.XPath.XPathNavigator> 对象的上下文范围内存在相同的命名空间 URI，但是两个上下文中映射到该命名空间 URI 的前缀不同，新的命名空间声明将添加到新插入的节点，前缀和命名空间 URI 从 <xref:System.Xml.XmlReader> 对象获取。</span><span class="sxs-lookup"><span data-stu-id="33152-167">If the same namespace URI is in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but has a different prefix mapped to it in both contexts, a new namespace declaration is added to the newly inserted node, with the prefix and namespace URI taken from the <xref:System.Xml.XmlReader> object.</span></span>  
  
- <span data-ttu-id="33152-168">如果 <xref:System.Xml.XmlReader> 对象的上下文和 <xref:System.Xml.XPath.XPathNavigator> 对象的上下文范围内存在相同的命名空间前缀，但是两个上下文中映射到该命名空间前缀的命名空间 URI 不同，新的命名空间声明将添加到新插入的节点，该声明使用从 <xref:System.Xml.XmlReader> 对象获取的命名空间 URI 重新声明该前缀。</span><span class="sxs-lookup"><span data-stu-id="33152-168">If the same namespace prefix is in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but has a different namespace URI mapped to it in both contexts, a new namespace declaration is added to the newly inserted node which re-declares that prefix with the namespace URI taken from <xref:System.Xml.XmlReader> object.</span></span>  
  
- <span data-ttu-id="33152-169">如果 <xref:System.Xml.XmlReader> 对象的上下文和 <xref:System.Xml.XPath.XPathNavigator> 对象的上下文中的前缀以及命名空间 URI 相同，则不会向新插入的节点添加新的命名空间声明。</span><span class="sxs-lookup"><span data-stu-id="33152-169">If the prefix as well as the namespace URI in both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context is the same, no new namespace declaration is added to the newly inserted node.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="33152-170">上面的说明同样适用于使用空 `string` 作为前缀的命名空间声明（例如默认的命名空间声明）。</span><span class="sxs-lookup"><span data-stu-id="33152-170">The description above also applies to namespace declarations with the empty `string` as a prefix (for example, the default namespace declaration).</span></span>  
  
 <span data-ttu-id="33152-171">以下是可能发生的 `xml:lang` 冲突。</span><span class="sxs-lookup"><span data-stu-id="33152-171">The following are the possible `xml:lang` conflicts.</span></span>  
  
- <span data-ttu-id="33152-172">如果 `xml:lang` 对象的上下文范围内存在 <xref:System.Xml.XmlReader> 属性，但是 <xref:System.Xml.XPath.XPathNavigator> 对象的上下文范围内没有，从 `xml:lang` 对象获取值的 <xref:System.Xml.XmlReader> 属性将添加到新插入的节点。</span><span class="sxs-lookup"><span data-stu-id="33152-172">If there is an `xml:lang` attribute in-scope within the <xref:System.Xml.XmlReader> object's context but not in the <xref:System.Xml.XPath.XPathNavigator> object's context, an `xml:lang` attribute whose value is taken from the <xref:System.Xml.XmlReader> object is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="33152-173">如果 `xml:lang` 对象的上下文和 <xref:System.Xml.XmlReader> 对象的上下文范围内均存在 <xref:System.Xml.XPath.XPathNavigator> 属性，但是每个属性的值不同，从 `xml:lang` 对象获取值的 <xref:System.Xml.XmlReader> 属性将添加到新插入的节点。</span><span class="sxs-lookup"><span data-stu-id="33152-173">If there is an `xml:lang` attribute in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but each has a different value, an `xml:lang` attribute whose value is taken from the <xref:System.Xml.XmlReader> object is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="33152-174">如果 `xml:lang` 对象的上下文和 <xref:System.Xml.XmlReader> 对象的上下文范围内均存在 <xref:System.Xml.XPath.XPathNavigator> 属性，但是每个属性的值相同，则不会向新插入的节点添加新的 `xml:lang` 属性。</span><span class="sxs-lookup"><span data-stu-id="33152-174">If there is an `xml:lang` attribute in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but each with the same value, no new `xml:lang` attribute is added on the newly inserted node.</span></span>  
  
- <span data-ttu-id="33152-175">如果 `xml:lang` 对象的上下文范围内存在 <xref:System.Xml.XPath.XPathNavigator> 属性，但是 <xref:System.Xml.XmlReader> 对象的上下文范围内不存在，则不会向新插入的节点添加 `xml:lang` 属性。</span><span class="sxs-lookup"><span data-stu-id="33152-175">If there is an `xml:lang` attribute in-scope within the <xref:System.Xml.XPath.XPathNavigator> object's context, but none existing in the <xref:System.Xml.XmlReader> object's context, no `xml:lang` attribute is added to the newly inserted node.</span></span>  
  
## <a name="inserting-nodes-with-xmlwriter"></a><span data-ttu-id="33152-176">使用 XmlWriter 插入节点</span><span class="sxs-lookup"><span data-stu-id="33152-176">Inserting Nodes with XmlWriter</span></span>  
 <span data-ttu-id="33152-177">“插入节点和值”一节中所述的用于插入同级节点、子节点和属性节点的方法均是重载方法。</span><span class="sxs-lookup"><span data-stu-id="33152-177">The methods used to insert sibling, child and attribute nodes described in the "Inserting Nodes and Values" section are overloaded.</span></span> <span data-ttu-id="33152-178"><xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> 类的 <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>、<xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>、<xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>、<xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> 和 <xref:System.Xml.XPath.XPathNavigator> 方法返回用于插入节点的 <xref:System.Xml.XmlWriter> 对象。</span><span class="sxs-lookup"><span data-stu-id="33152-178">The <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> and <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class return an <xref:System.Xml.XmlWriter> object used to insert nodes.</span></span>  
  
### <a name="unsupported-xmlwriter-methods"></a><span data-ttu-id="33152-179">不支持的 XmlWriter 方法</span><span class="sxs-lookup"><span data-stu-id="33152-179">Unsupported XmlWriter Methods</span></span>  
 <span data-ttu-id="33152-180">因为 XPath 数据模型与文档对象模型 (DOM) 之间存在差异，所以，<xref:System.Xml.XmlWriter> 类并非支持所有用于使用 <xref:System.Xml.XPath.XPathNavigator> 类向 XML 文档写入信息的方法。</span><span class="sxs-lookup"><span data-stu-id="33152-180">Not all of the methods used for writing information to an XML document using the <xref:System.Xml.XmlWriter> class are supported by the <xref:System.Xml.XPath.XPathNavigator> class due to difference between the XPath data model and the Document Object Model (DOM).</span></span>  
  
 <span data-ttu-id="33152-181">下表说明 <xref:System.Xml.XmlWriter> 类不支持的 <xref:System.Xml.XPath.XPathNavigator> 类方法。</span><span class="sxs-lookup"><span data-stu-id="33152-181">The following table describes the <xref:System.Xml.XmlWriter> class methods not supported by the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
|<span data-ttu-id="33152-182">方法</span><span class="sxs-lookup"><span data-stu-id="33152-182">Method</span></span>|<span data-ttu-id="33152-183">描述</span><span class="sxs-lookup"><span data-stu-id="33152-183">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|<span data-ttu-id="33152-184">引发 <xref:System.NotSupportedException> 异常。</span><span class="sxs-lookup"><span data-stu-id="33152-184">Throws a <xref:System.NotSupportedException> exception.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|<span data-ttu-id="33152-185">在根级别忽略，如果在 XML 文档中的任何其他级别调用，将引发 <xref:System.NotSupportedException> 异常。</span><span class="sxs-lookup"><span data-stu-id="33152-185">Ignored at the root level and throws a <xref:System.NotSupportedException> exception if called at any other level in the XML document.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|<span data-ttu-id="33152-186">看作对等效字符调用 <xref:System.Xml.XmlWriter.WriteString%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="33152-186">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|<span data-ttu-id="33152-187">看作对等效字符调用 <xref:System.Xml.XmlWriter.WriteString%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="33152-187">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|<span data-ttu-id="33152-188">看作对等效字符调用 <xref:System.Xml.XmlWriter.WriteString%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="33152-188">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
  
 <span data-ttu-id="33152-189">有关 <xref:System.Xml.XmlWriter> 类的更多信息，请参见 <xref:System.Xml.XmlWriter> 类参考文档。</span><span class="sxs-lookup"><span data-stu-id="33152-189">For more information about the <xref:System.Xml.XmlWriter> class, see the <xref:System.Xml.XmlWriter> class reference documentation.</span></span>  
  
### <a name="multiple-xmlwriter-objects"></a><span data-ttu-id="33152-190">多个 XmlWriter 对象</span><span class="sxs-lookup"><span data-stu-id="33152-190">Multiple XmlWriter Objects</span></span>  
 <span data-ttu-id="33152-191">可能存在多个 <xref:System.Xml.XPath.XPathNavigator> 对象，指向包含一个或多个打开的 <xref:System.Xml.XmlWriter> 对象的 XML 文档的不同部分。</span><span class="sxs-lookup"><span data-stu-id="33152-191">It is possible to have multiple <xref:System.Xml.XPath.XPathNavigator> objects pointing to different parts of an XML document with one or more open <xref:System.Xml.XmlWriter> objects.</span></span> <span data-ttu-id="33152-192">在单线程方案中允许并支持多个 <xref:System.Xml.XmlWriter> 对象。</span><span class="sxs-lookup"><span data-stu-id="33152-192">Multiple <xref:System.Xml.XmlWriter> objects are allowed and supported in single-threaded scenarios.</span></span>  
  
 <span data-ttu-id="33152-193">以下是在使用多个 <xref:System.Xml.XmlWriter> 对象时要考虑的重要事项。</span><span class="sxs-lookup"><span data-stu-id="33152-193">The following are important notes to consider when using multiple <xref:System.Xml.XmlWriter> objects.</span></span>  
  
- <span data-ttu-id="33152-194">在调用每个 <xref:System.Xml.XmlWriter> 对象的 <xref:System.Xml.XmlWriter.Close%2A> 方法时，通过 <xref:System.Xml.XmlWriter> 对象编写的 XML 片断将添加到 XML 文档中。</span><span class="sxs-lookup"><span data-stu-id="33152-194">XML fragments written by <xref:System.Xml.XmlWriter> objects are added to the XML document when the <xref:System.Xml.XmlWriter.Close%2A> method of each <xref:System.Xml.XmlWriter> object is called.</span></span> <span data-ttu-id="33152-195">直到此时，<xref:System.Xml.XmlWriter> 对象一直在编写断开的片断。</span><span class="sxs-lookup"><span data-stu-id="33152-195">Until that point, the <xref:System.Xml.XmlWriter> object is writing a disconnected fragment.</span></span> <span data-ttu-id="33152-196">如果对 XML 文档执行某项操作，在调用 <xref:System.Xml.XmlWriter> 之前，任何通过 <xref:System.Xml.XmlWriter.Close%2A> 对象编写的片断不会受影响。</span><span class="sxs-lookup"><span data-stu-id="33152-196">If an operation is performed on the XML document, any fragments being written by an <xref:System.Xml.XmlWriter> object, before the <xref:System.Xml.XmlWriter.Close%2A> has been called, are not affected.</span></span>  
  
- <span data-ttu-id="33152-197">如果特定 XML 子树上存在打开的 <xref:System.Xml.XmlWriter> 对象并且该子树已删除，<xref:System.Xml.XmlWriter> 对象仍可以添加到子树上。</span><span class="sxs-lookup"><span data-stu-id="33152-197">If there is an open <xref:System.Xml.XmlWriter> object on a particular XML subtree and that subtree is deleted, the <xref:System.Xml.XmlWriter> object may still add to the sub-tree.</span></span> <span data-ttu-id="33152-198">只是子树成为已删除的片断。</span><span class="sxs-lookup"><span data-stu-id="33152-198">The subtree simply becomes a deleted fragment.</span></span>  
  
- <span data-ttu-id="33152-199">如果在 XML 文档的相同位置打开多个 <xref:System.Xml.XmlWriter> 对象，这些对象将按照 <xref:System.Xml.XmlWriter> 对象关闭的顺序添加到 XML 文档，而不是按照对象打开的顺序。</span><span class="sxs-lookup"><span data-stu-id="33152-199">If multiple <xref:System.Xml.XmlWriter> objects are opened at the same point in the XML document, they are added to the XML document in the order in which the <xref:System.Xml.XmlWriter> objects are closed, not in the order in which they were opened.</span></span>  
  
 <span data-ttu-id="33152-200">以下示例创建一个 <xref:System.Xml.XmlDocument> 对象，创建一个 <xref:System.Xml.XPath.XPathNavigator> 对象，然后使用 <xref:System.Xml.XmlWriter> 方法返回的 <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> 对象在 `books.xml` 文件中创建第一本图书的结构。</span><span class="sxs-lookup"><span data-stu-id="33152-200">The following example creates an <xref:System.Xml.XmlDocument> object, creates an <xref:System.Xml.XPath.XPathNavigator> object, and then uses the <xref:System.Xml.XmlWriter> object returned by the <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> method to create the structure of the first book in the `books.xml` file.</span></span> <span data-ttu-id="33152-201">然后，示例将其保存为 `book.xml` 文件。</span><span class="sxs-lookup"><span data-stu-id="33152-201">The example then saves it as the `book.xml` file.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Using writer As XmlWriter = navigator.PrependChild()  
  
    writer.WriteStartElement("bookstore")  
    writer.WriteStartElement("book")  
    writer.WriteAttributeString("genre", "autobiography")  
    writer.WriteAttributeString("publicationdate", "1981-03-22")  
    writer.WriteAttributeString("ISBN", "1-861003-11-0")  
    writer.WriteElementString("title", "The Autobiography of Benjamin Franklin")  
    writer.WriteStartElement("author")  
    writer.WriteElementString("first-name", "Benjamin")  
    writer.WriteElementString("last-name", "Franklin")  
    writer.WriteElementString("price", "8.99")  
    writer.WriteEndElement()  
    writer.WriteEndElement()  
    writer.WriteEndElement()  
  
End Using  
  
document.Save("book.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
XPathNavigator navigator = document.CreateNavigator();  
  
using (XmlWriter writer = navigator.PrependChild())  
{  
    writer.WriteStartElement("bookstore");  
    writer.WriteStartElement("book");  
    writer.WriteAttributeString("genre", "autobiography");  
    writer.WriteAttributeString("publicationdate", "1981-03-22");  
    writer.WriteAttributeString("ISBN", "1-861003-11-0");  
    writer.WriteElementString("title", "The Autobiography of Benjamin Franklin");  
    writer.WriteStartElement("author");  
    writer.WriteElementString("first-name", "Benjamin");  
    writer.WriteElementString("last-name", "Franklin");  
    writer.WriteElementString("price", "8.99");  
    writer.WriteEndElement();  
    writer.WriteEndElement();  
    writer.WriteEndElement();  
}  
document.Save("book.xml");  
```  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="33152-202">保存 XML 文档</span><span class="sxs-lookup"><span data-stu-id="33152-202">Saving an XML Document</span></span>  
 <span data-ttu-id="33152-203">使用 <xref:System.Xml.XmlDocument> 类的方法保存本主题中所述的方法对 <xref:System.Xml.XmlDocument> 对象的更改。</span><span class="sxs-lookup"><span data-stu-id="33152-203">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="33152-204">若要详细了解如何保存对 <xref:System.Xml.XmlDocument> 对象所做的更改，请参阅[保存和编写文档](saving-and-writing-a-document.md)。</span><span class="sxs-lookup"><span data-stu-id="33152-204">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33152-205">请参阅</span><span class="sxs-lookup"><span data-stu-id="33152-205">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="33152-206">使用 XPath 数据模型处理 XML 数据</span><span class="sxs-lookup"><span data-stu-id="33152-206">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="33152-207">使用 XPathNavigator 修改 XML 数据</span><span class="sxs-lookup"><span data-stu-id="33152-207">Modify XML Data using XPathNavigator</span></span>](modify-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="33152-208">使用 XPathNavigator 删除 XML 数据</span><span class="sxs-lookup"><span data-stu-id="33152-208">Remove XML Data using XPathNavigator</span></span>](remove-xml-data-using-xpathnavigator.md)

---
title: XPath 查询和命名空间
description: 了解 XPath 查询和命名空间。 XPath 查询支持 XML 文档中的命名空间，可以使用命名空间前缀来限定元素和属性的名称。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: ef6402be-2f8e-4be2-8d3e-a80891cdef8b
ms.openlocfilehash: e8533d372a747432201dfbc4d879ecd3fbceaf8e
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769244"
---
# <a name="xpath-queries-and-namespaces"></a><span data-ttu-id="08551-104">XPath 查询和命名空间</span><span class="sxs-lookup"><span data-stu-id="08551-104">XPath Queries and Namespaces</span></span>
<span data-ttu-id="08551-105">XPath 查询支持 XML 文档中的命名空间，可以使用命名空间前缀来限定元素和属性的名称。</span><span class="sxs-lookup"><span data-stu-id="08551-105">XPath queries are aware of namespaces in an XML document and can use namespace prefixes to qualify element and attribute names.</span></span> <span data-ttu-id="08551-106">使用命名空间前缀来限定元素和属性的名称可以限制 XPath 查询只返回属于特定命名空间的节点。</span><span class="sxs-lookup"><span data-stu-id="08551-106">Qualifying element and attribute names with a namespace prefix limits the nodes returned by an XPath query to only those nodes that belong to a specific namespace.</span></span>  
  
 <span data-ttu-id="08551-107">例如，如果前缀 `books` 映射到命名空间 `http://www.contoso.com/books`，以下 XPath 查询 `/books:books/books:book` 将只选择命名空间 `book` 中的 `http://www.contoso.com/books` 元素。</span><span class="sxs-lookup"><span data-stu-id="08551-107">For example if the prefix `books` maps to the namespace `http://www.contoso.com/books`, then the following XPath query `/books:books/books:book` selects only those `book` elements in the namespace `http://www.contoso.com/books`.</span></span>  
  
## <a name="the-xmlnamespacemanager"></a><span data-ttu-id="08551-108">XmlNamespaceManager</span><span class="sxs-lookup"><span data-stu-id="08551-108">The XmlNamespaceManager</span></span>  
 <span data-ttu-id="08551-109">要在 XPath 查询中使用命名空间，构造一个从 <xref:System.Xml.IXmlNamespaceResolver> 接口派生的对象（例如 <xref:System.Xml.XmlNamespaceManager> 类），包含要加入 XPath 查询的命名空间 URI 和前缀。</span><span class="sxs-lookup"><span data-stu-id="08551-109">To use namespaces in an XPath query, an object derived from the <xref:System.Xml.IXmlNamespaceResolver> interface like the <xref:System.Xml.XmlNamespaceManager> class is constructed with the namespace URI and prefix to include in the XPath query.</span></span>  
  
 <span data-ttu-id="08551-110"><xref:System.Xml.XmlNamespaceManager> 对象可以通过下列任意方式在查询中使用。</span><span class="sxs-lookup"><span data-stu-id="08551-110">The <xref:System.Xml.XmlNamespaceManager> object may be used in the query in each of the following ways.</span></span>  
  
- <span data-ttu-id="08551-111">使用 <xref:System.Xml.XmlNamespaceManager> 对象的 <xref:System.Xml.XPath.XPathExpression> 方法将 <xref:System.Xml.XPath.XPathExpression.SetContext%2A> 对象与现有的 <xref:System.Xml.XPath.XPathExpression> 对象关联。</span><span class="sxs-lookup"><span data-stu-id="08551-111">The <xref:System.Xml.XmlNamespaceManager> object is associated with an existing <xref:System.Xml.XPath.XPathExpression> object by using the <xref:System.Xml.XPath.XPathExpression.SetContext%2A> method of the <xref:System.Xml.XPath.XPathExpression> object.</span></span> <span data-ttu-id="08551-112">还可以使用静态 <xref:System.Xml.XPath.XPathExpression> 方法编译新的 <xref:System.Xml.XPath.XPathExpression.Compile%2A> 对象，该方法使用表示 XPath 表达式的字符串和 <xref:System.Xml.XmlNamespaceManager> 对象作为参数，并返回一个新的 <xref:System.Xml.XPath.XPathExpression> 对象。</span><span class="sxs-lookup"><span data-stu-id="08551-112">You may also compile a new <xref:System.Xml.XPath.XPathExpression> object using the static <xref:System.Xml.XPath.XPathExpression.Compile%2A> method which takes a string representing the XPath expression and an <xref:System.Xml.XmlNamespaceManager> object as parameters and returns a new <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
- <span data-ttu-id="08551-113"><xref:System.Xml.XmlNamespaceManager> 对象本身与表示 XPath 表达式的字符串一起作为参数传递给接受方的 <xref:System.Xml.XPath.XPathNavigator> 类方法。</span><span class="sxs-lookup"><span data-stu-id="08551-113">The <xref:System.Xml.XmlNamespaceManager> object itself is passed as a parameter to an accepting <xref:System.Xml.XPath.XPathNavigator> class method along with a string representing the XPath expression.</span></span>  
  
 <span data-ttu-id="08551-114">以下是 <xref:System.Xml.XPath.XPathNavigator> 类中接受从 <xref:System.Xml.IXmlNamespaceResolver> 接口派生的对象作为参数的方法。</span><span class="sxs-lookup"><span data-stu-id="08551-114">The following are the methods of the <xref:System.Xml.XPath.XPathNavigator> class that accept an object derived from the <xref:System.Xml.IXmlNamespaceResolver> interface as a parameter.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
### <a name="the-default-namespace"></a><span data-ttu-id="08551-115">默认命名空间</span><span class="sxs-lookup"><span data-stu-id="08551-115">The Default Namespace</span></span>  
 <span data-ttu-id="08551-116">在下面的 XML 文档中，具有空前缀的默认命名空间用于声明 `http://www.contoso.com/books` 命名空间。</span><span class="sxs-lookup"><span data-stu-id="08551-116">In the XML document that follows, the default namespace with an empty prefix is used to declare the `http://www.contoso.com/books` namespace.</span></span>  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <author>Author Name</author>  
        <price>5.50</price>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="08551-117">XPath 将空前缀作为 `null` 命名空间对待。</span><span class="sxs-lookup"><span data-stu-id="08551-117">XPath treats the empty prefix as the `null` namespace.</span></span> <span data-ttu-id="08551-118">也就是说，XPath 查询中只能使用映射到命名空间上的前缀。</span><span class="sxs-lookup"><span data-stu-id="08551-118">In other words, only prefixes mapped to namespaces can be used in XPath queries.</span></span> <span data-ttu-id="08551-119">这意味着如果要针对 XML 文档中的某个命名空间进行查询，即使是默认的命名空间，也需要为其定义前缀。</span><span class="sxs-lookup"><span data-stu-id="08551-119">This means that if you want to query against a namespace in an XML document, even if it is the default namespace, you need to define a prefix for it.</span></span>  
  
 <span data-ttu-id="08551-120">例如，在没有为上面的 XML 文档定义前缀的情况下，XPath 查询 `/books/book` 不会返回任何结果。</span><span class="sxs-lookup"><span data-stu-id="08551-120">For example, without defining a prefix for the XML document above, the XPath query `/books/book` would not return any results.</span></span>  
  
 <span data-ttu-id="08551-121">必须绑定前缀，这样，如果查询的文档中有些节点在某个命名空间，有些节点在默认命名空间，可以避免混淆情况。</span><span class="sxs-lookup"><span data-stu-id="08551-121">A prefix must be bound to prevent ambiguity when querying documents with some nodes not in a namespace, and some in a default namespace.</span></span>  
  
 <span data-ttu-id="08551-122">以下代码为默认命名空间定义前缀，并选择 `book` 命名空间中的所有 `http://www.contoso.com/books` 元素。</span><span class="sxs-lookup"><span data-stu-id="08551-122">The following code defines a prefix for the default namespace and selects all the `book` elements from the `http://www.contoso.com/books` namespace.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
Dim query As XPathExpression = navigator.Compile("/books:books/books:book")  
Dim manager As XmlNamespaceManager = New XmlNamespaceManager(navigator.NameTable)  
manager.AddNamespace("books", "http://www.contoso.com/books")  
query.SetContext(manager)  
Dim nodes As XPathNodeIterator = navigator.Select(query)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
XPathExpression query = navigator.Compile("/books:books/books:book");  
XmlNamespaceManager manager = new XmlNamespaceManager(navigator.NameTable);  
manager.AddNamespace("books", "http://www.contoso.com/books");  
query.SetContext(manager);  
XPathNodeIterator nodes = navigator.Select(query);  
```  
  
## <a name="see-also"></a><span data-ttu-id="08551-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="08551-123">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="08551-124">使用 XPath 数据模型处理 XML 数据</span><span class="sxs-lookup"><span data-stu-id="08551-124">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="08551-125">使用 XPathNavigator 选择 XML 数据</span><span class="sxs-lookup"><span data-stu-id="08551-125">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="08551-126">使用 XPathNavigator 计算 XPath 表达式</span><span class="sxs-lookup"><span data-stu-id="08551-126">Evaluate XPath Expressions using XPathNavigator</span></span>](evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="08551-127">使用 XPathNavigator 匹配节点</span><span class="sxs-lookup"><span data-stu-id="08551-127">Matching Nodes using XPathNavigator</span></span>](matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="08551-128">XPath 查询识别的节点类型</span><span class="sxs-lookup"><span data-stu-id="08551-128">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="08551-129">已编译的 XPath 表达式</span><span class="sxs-lookup"><span data-stu-id="08551-129">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)

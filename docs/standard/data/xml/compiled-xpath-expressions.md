---
title: 已编译的 XPath 表达式
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e25dd95f-b64c-4d8b-a3a4-379e1aa0ad55
ms.openlocfilehash: e74b52e471699fc663504fa42d6c7e502859adda
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291521"
---
# <a name="compiled-xpath-expressions"></a><span data-ttu-id="0291b-102">已编译的 XPath 表达式</span><span class="sxs-lookup"><span data-stu-id="0291b-102">Compiled XPath Expressions</span></span>
<span data-ttu-id="0291b-103"><xref:System.Xml.XPath.XPathExpression> 对象表示从 <xref:System.Xml.XPath.XPathExpression.Compile%2A> 类的静态 <xref:System.Xml.XPath.XPathExpression> 方法或 <xref:System.Xml.XPath.XPathNavigator.Compile%2A> 类的 <xref:System.Xml.XPath.XPathNavigator> 方法返回的已编译 XPath 查询。</span><span class="sxs-lookup"><span data-stu-id="0291b-103">An <xref:System.Xml.XPath.XPathExpression> object represents a compiled XPath query returned from either the static <xref:System.Xml.XPath.XPathExpression.Compile%2A> method of the <xref:System.Xml.XPath.XPathExpression> class or the <xref:System.Xml.XPath.XPathNavigator.Compile%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="the-xpathexpression-class"></a><span data-ttu-id="0291b-104">XPathExpression 类</span><span class="sxs-lookup"><span data-stu-id="0291b-104">The XPathExpression Class</span></span>  
 <span data-ttu-id="0291b-105">如果多次使用相同的 XPath 查询，通过 <xref:System.Xml.XPath.XPathExpression> 对象表示的已编译 XPath 查询非常有用。</span><span class="sxs-lookup"><span data-stu-id="0291b-105">A compiled XPath query represented by an <xref:System.Xml.XPath.XPathExpression> object is useful if the same XPath query is being used more than once.</span></span>  
  
 <span data-ttu-id="0291b-106">例如，如果多次调用 <xref:System.Xml.XPath.XPathNavigator.Select%2A> 方法，而不是每次使用表示 XPath 查询的字符串，请使用 <xref:System.Xml.XPath.XPathExpression.Compile%2A> 类的 <xref:System.Xml.XPath.XPathExpression> 方法或 <xref:System.Xml.XPath.XPathNavigator.Compile%2A> 类的 <xref:System.Xml.XPath.XPathNavigator> 方法来编译并缓存 <xref:System.Xml.XPath.XPathExpression> 对象中的 XPath 查询，以便重复使用并提高性能。</span><span class="sxs-lookup"><span data-stu-id="0291b-106">For example, when calling the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method multiple times, instead of using a string representing the XPath query each time, use the <xref:System.Xml.XPath.XPathExpression.Compile%2A> method of the <xref:System.Xml.XPath.XPathExpression> class or the <xref:System.Xml.XPath.XPathNavigator.Compile%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class to compile and cache the XPath query in an <xref:System.Xml.XPath.XPathExpression> object for reuse and improved performance.</span></span>  
  
 <span data-ttu-id="0291b-107">编译后，根据从 XPath 查询返回的类型，<xref:System.Xml.XPath.XPathExpression> 对象也许可以作为下列 <xref:System.Xml.XPath.XPathNavigator> 类方法的输入。</span><span class="sxs-lookup"><span data-stu-id="0291b-107">Once compiled, the <xref:System.Xml.XPath.XPathExpression> object may be used as input to the following <xref:System.Xml.XPath.XPathNavigator> class methods depending on the type returned from the XPath query.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <span data-ttu-id="0291b-108">下表介绍每种 W3C XPath 返回类型、其等效的 Microsoft .NET Framework 类型以及 <xref:System.Xml.XPath.XPathExpression> 对象基于其返回类型也许可以用于的方法。</span><span class="sxs-lookup"><span data-stu-id="0291b-108">The following table describes each of the W3C XPath return types, their Microsoft .NET Framework equivalencies, and what methods the <xref:System.Xml.XPath.XPathExpression> object may be used with based on its return type.</span></span>  
  
|<span data-ttu-id="0291b-109">W3C XPath 返回类型</span><span class="sxs-lookup"><span data-stu-id="0291b-109">W3C XPath Return Type</span></span>|<span data-ttu-id="0291b-110">等效的 .NET Framework 类型</span><span class="sxs-lookup"><span data-stu-id="0291b-110">.NET Framework Equivalent Type</span></span>|<span data-ttu-id="0291b-111">描述</span><span class="sxs-lookup"><span data-stu-id="0291b-111">Description</span></span>|<span data-ttu-id="0291b-112">方法</span><span class="sxs-lookup"><span data-stu-id="0291b-112">Methods</span></span>|  
|---------------------------|------------------------------------|-----------------|-------------|  
|`Node set`|<xref:System.Xml.XPath.XPathNodeIterator>|<span data-ttu-id="0291b-113">未排序的节点集合，按照文档顺序创建，没有重复。</span><span class="sxs-lookup"><span data-stu-id="0291b-113">An unordered collection of nodes without duplicates created in document order.</span></span>|<span data-ttu-id="0291b-114"><xref:System.Xml.XPath.XPathNavigator.Select%2A> 或 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A></span><span class="sxs-lookup"><span data-stu-id="0291b-114"><xref:System.Xml.XPath.XPathNavigator.Select%2A> or <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A></span></span>|  
|`Boolean`|<xref:System.Boolean>|<span data-ttu-id="0291b-115">`true` 或 `false` 值。</span><span class="sxs-lookup"><span data-stu-id="0291b-115">A `true` or `false` value.</span></span>|<span data-ttu-id="0291b-116"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 或</span><span class="sxs-lookup"><span data-stu-id="0291b-116"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> or</span></span><br /><br /> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>|  
|`Number`|<xref:System.Double>|<span data-ttu-id="0291b-117">一个浮点数字。</span><span class="sxs-lookup"><span data-stu-id="0291b-117">A floating-point number.</span></span>|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`String`|<xref:System.String>|<span data-ttu-id="0291b-118">UCS 字符序列。</span><span class="sxs-lookup"><span data-stu-id="0291b-118">A sequence of UCS characters.</span></span>|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
  
> [!NOTE]
> <span data-ttu-id="0291b-119"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> 方法允许将 XPath 表达式作为其参数。</span><span class="sxs-lookup"><span data-stu-id="0291b-119">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method accepts an XPath expression as its parameter.</span></span> <span data-ttu-id="0291b-120"><xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> 方法返回 <xref:System.Xml.XPath.XPathNavigator> 对象，而不是一种 W3C XPath 返回类型。</span><span class="sxs-lookup"><span data-stu-id="0291b-120">The <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method returns an <xref:System.Xml.XPath.XPathNavigator> object, not one of the W3C XPath return types.</span></span>  
  
### <a name="the-returntype-property"></a><span data-ttu-id="0291b-121">ReturnType 属性</span><span class="sxs-lookup"><span data-stu-id="0291b-121">The ReturnType Property</span></span>  
 <span data-ttu-id="0291b-122">在 XPath 查询编译为 <xref:System.Xml.XPath.XPathExpression> 对象之后，可以使用 <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> 对象的 <xref:System.Xml.XPath.XPathExpression> 属性来确定 XPath 查询返回的内容。</span><span class="sxs-lookup"><span data-stu-id="0291b-122">After an XPath query has been compiled into an <xref:System.Xml.XPath.XPathExpression> object, you can use the <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property of the <xref:System.Xml.XPath.XPathExpression> object to determine what the XPath query returns.</span></span>  
  
 <span data-ttu-id="0291b-123"><xref:System.Xml.XPath.XPathExpression.ReturnType%2A> 属性返回表示 W3C XPath 返回类型的下列 <xref:System.Xml.XPath.XPathResultType> 枚举值之一。</span><span class="sxs-lookup"><span data-stu-id="0291b-123">The <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property returns one of the following <xref:System.Xml.XPath.XPathResultType> enumeration values representing the W3C XPath return types.</span></span>  
  
- <xref:System.Xml.XPath.XPathResultType.Any>  
  
- <xref:System.Xml.XPath.XPathResultType.Boolean>  
  
- <xref:System.Xml.XPath.XPathResultType.Error>  
  
- <xref:System.Xml.XPath.XPathResultType.Navigator>  
  
- <xref:System.Xml.XPath.XPathResultType.NodeSet>  
  
- <xref:System.Xml.XPath.XPathResultType.Number>  
  
- <xref:System.Xml.XPath.XPathResultType.String>  
  
 <span data-ttu-id="0291b-124">以下示例使用 <xref:System.Xml.XPath.XPathExpression> 对象从 `books.xml` 文件中返回一个数字和一个节点集。</span><span class="sxs-lookup"><span data-stu-id="0291b-124">The following example uses the <xref:System.Xml.XPath.XPathExpression> object to return a number and a node set from the `books.xml` file.</span></span> <span data-ttu-id="0291b-125">每个 <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> 对象的 <xref:System.Xml.XPath.XPathExpression> 属性以及 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 和 <xref:System.Xml.XPath.XPathNavigator.Select%2A> 方法的返回结果将写入控制台。</span><span class="sxs-lookup"><span data-stu-id="0291b-125">The <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property of each <xref:System.Xml.XPath.XPathExpression> object as well as the results from the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> and <xref:System.Xml.XPath.XPathNavigator.Select%2A> methods are written to the console.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Returns a number.  
Dim query1 As XPathExpression = navigator.Compile("bookstore/book/price/text()*10")  
Console.WriteLine(query1.ReturnType)  
  
Dim number As Double = CType(navigator.Evaluate(query1), Double)  
Console.WriteLine(number)  
  
' Returns a node set.  
Dim query2 As XPathExpression = navigator.Compile("bookstore/book/price")  
Console.WriteLine(query2.ReturnType)  
  
Dim nodes As XPathNodeIterator = navigator.Select(query2)  
nodes.MoveNext()  
Console.WriteLine(nodes.Current.Value)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Returns a number.  
XPathExpression query1 = navigator.Compile("bookstore/book/price/text()*10");  
Console.WriteLine(query1.ReturnType);  
  
Double number = (Double)navigator.Evaluate(query1);  
Console.WriteLine(number);  
  
// Returns a node set.  
XPathExpression query2 = navigator.Compile("bookstore/book/price");  
Console.WriteLine(query2.ReturnType);  
  
XPathNodeIterator nodes = navigator.Select(query2);  
nodes.MoveNext();  
Console.WriteLine(nodes.Current.Value);  
```  
  
 <span data-ttu-id="0291b-126">该示例使用 `books.xml` 文件作为输入。</span><span class="sxs-lookup"><span data-stu-id="0291b-126">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="higher-performance-xpath-expressions"></a><span data-ttu-id="0291b-127">性能更强的 XPath 表达式</span><span class="sxs-lookup"><span data-stu-id="0291b-127">Higher Performance XPath Expressions</span></span>  
 <span data-ttu-id="0291b-128">为了获得更好的性能，请尽可能在查询中使用最具体的 XPath 表达式。</span><span class="sxs-lookup"><span data-stu-id="0291b-128">For better performance, use the most specific XPath expression possible in your queries.</span></span> <span data-ttu-id="0291b-129">例如，如果 `book` 节点是 `bookstore` 节点的子节点，并且 `bookstore` 节点是 XML 文档的顶级元素，使用 XPath 表达式 `/bookstore/book` 比使用 `//book` 速度更快。</span><span class="sxs-lookup"><span data-stu-id="0291b-129">For example, if the `book` node is a child node of the `bookstore` node and the `bookstore` node is the top-most element in an XML document, using the XPath expression `/bookstore/book` is faster than using `//book`.</span></span> <span data-ttu-id="0291b-130">`//book` XPath 表达式将扫描 XML 树中的每个节点来标识匹配的节点。</span><span class="sxs-lookup"><span data-stu-id="0291b-130">The `//book` XPath expression will scan every node in the XML tree to identify matching nodes.</span></span>  
  
 <span data-ttu-id="0291b-131">此外，如果选择条件很简单，使用 <xref:System.Xml.XPath.XPathNavigator> 类提供的节点集浏览方法的性能可能会强于 <xref:System.Xml.XPath.XPathNavigator> 类提供的选择方法。</span><span class="sxs-lookup"><span data-stu-id="0291b-131">Additionally, using the node set navigation methods supplied by the <xref:System.Xml.XPath.XPathNavigator> class may result in improved performance over the selection methods supplied by the <xref:System.Xml.XPath.XPathNavigator> class in cases where your selection criteria are simple.</span></span> <span data-ttu-id="0291b-132">例如，如果需要选择当前节点的第一个子级，使用 <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> 方法比使用 `child::*[1]` XPath 表达式和 <xref:System.Xml.XPath.XPathNavigator.Select%2A> 方法速度更快。</span><span class="sxs-lookup"><span data-stu-id="0291b-132">For example, if you need to select the first child of the current node, it is faster to use the <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> method than to use the `child::*[1]` XPath expression and the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method.</span></span>  
  
 <span data-ttu-id="0291b-133">若要详细了解 <xref:System.Xml.XPath.XPathNavigator> 类的节点集导航方法，请参阅[使用 XPathNavigator 的节点集定位](node-set-navigation-using-xpathnavigator.md)。</span><span class="sxs-lookup"><span data-stu-id="0291b-133">For more information about the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class, see [Node Set Navigation Using XPathNavigator](node-set-navigation-using-xpathnavigator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0291b-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="0291b-134">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="0291b-135">使用 XPath 数据模型处理 XML 数据</span><span class="sxs-lookup"><span data-stu-id="0291b-135">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="0291b-136">使用 XPathNavigator 选择 XML 数据</span><span class="sxs-lookup"><span data-stu-id="0291b-136">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="0291b-137">使用 XPathNavigator 计算 XPath 表达式</span><span class="sxs-lookup"><span data-stu-id="0291b-137">Evaluate XPath Expressions using XPathNavigator</span></span>](evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="0291b-138">使用 XPathNavigator 匹配节点</span><span class="sxs-lookup"><span data-stu-id="0291b-138">Matching Nodes using XPathNavigator</span></span>](matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="0291b-139">XPath 查询识别的节点类型</span><span class="sxs-lookup"><span data-stu-id="0291b-139">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="0291b-140">XPath 查询和命名空间</span><span class="sxs-lookup"><span data-stu-id="0291b-140">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)

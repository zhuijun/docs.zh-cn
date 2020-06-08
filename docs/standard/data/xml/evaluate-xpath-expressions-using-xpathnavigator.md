---
title: 使用 XPathNavigator 计算 XPath 表达式
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
ms.openlocfilehash: b6e18fe02a828ae307ac7ade15650d3303f2600c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287800"
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a><span data-ttu-id="e1b03-102">使用 XPathNavigator 计算 XPath 表达式</span><span class="sxs-lookup"><span data-stu-id="e1b03-102">Evaluate XPath Expressions using XPathNavigator</span></span>
<span data-ttu-id="e1b03-103"><xref:System.Xml.XPath.XPathNavigator> 类提供了 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 方法来计算 XPath 表达式。</span><span class="sxs-lookup"><span data-stu-id="e1b03-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method to evaluate an XPath expression.</span></span> <span data-ttu-id="e1b03-104"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 方法使用 XPath 表达式，计算表达式，然后基于 XPath 表达式的结果返回 Boolean、Number、String 或 Node Set 的 W3C XPath 类型。</span><span class="sxs-lookup"><span data-stu-id="e1b03-104">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it and returns a W3C XPath type of Boolean, Number, String, or Node Set based on the result of the XPath expression.</span></span>  
  
## <a name="the-evaluate-method"></a><span data-ttu-id="e1b03-105">Evaluate 方法</span><span class="sxs-lookup"><span data-stu-id="e1b03-105">The Evaluate Method</span></span>  
 <span data-ttu-id="e1b03-106"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 方法使用 XPath 表达式，计算表达式，然后返回 Boolean (<xref:System.Boolean>)、Number (<xref:System.Double>)、String (<xref:System.String>) 或 Node Set (<xref:System.Xml.XPath.XPathNodeIterator>) 的类型化结果。</span><span class="sxs-lookup"><span data-stu-id="e1b03-106">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it, and returns a typed result of Boolean (<xref:System.Boolean>), Number (<xref:System.Double>), String (<xref:System.String>), or Node Set (<xref:System.Xml.XPath.XPathNodeIterator>).</span></span> <span data-ttu-id="e1b03-107">例如，<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 方法可以在数学方法中使用。</span><span class="sxs-lookup"><span data-stu-id="e1b03-107">For example, the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method could be used in a mathematical method.</span></span> <span data-ttu-id="e1b03-108">以下示例代码计算 `books.xml` 文件中的所有图书的总价格。</span><span class="sxs-lookup"><span data-stu-id="e1b03-108">The following example code calculates the total price of all the books in the `books.xml` file.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Dim query As XPathExpression = navigator.Compile("sum(//price/text())")  
Dim total As Double = CType(navigator.Evaluate(query), Double)  
Console.WriteLine(total)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
XPathExpression query = navigator.Compile("sum(//price/text())");  
Double total = (Double)navigator.Evaluate(query);  
Console.WriteLine(total);  
```  
  
 <span data-ttu-id="e1b03-109">该示例使用 `books.xml` 文件作为输入。</span><span class="sxs-lookup"><span data-stu-id="e1b03-109">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="position-and-last-functions"></a><span data-ttu-id="e1b03-110">position 和 last 函数</span><span class="sxs-lookup"><span data-stu-id="e1b03-110">position and last Functions</span></span>  
 <span data-ttu-id="e1b03-111"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 方法是重载方法。</span><span class="sxs-lookup"><span data-stu-id="e1b03-111">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is overloaded.</span></span> <span data-ttu-id="e1b03-112">一个 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 方法使用 <xref:System.Xml.XPath.XPathNodeIterator> 对象作为参数。</span><span class="sxs-lookup"><span data-stu-id="e1b03-112">One of the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> methods takes an <xref:System.Xml.XPath.XPathNodeIterator> object as a parameter.</span></span> <span data-ttu-id="e1b03-113">此特定的 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 方法与只使用 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 对象作为参数的 <xref:System.Xml.XPath.XPathExpression> 方法相同，只是允许使用节点集参数指定要执行计算的当前上下文。</span><span class="sxs-lookup"><span data-stu-id="e1b03-113">This particular <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is identical to the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method that takes only an <xref:System.Xml.XPath.XPathExpression> object as a parameter, except that it allows a node set argument to specify the current context to perform the evaluation on.</span></span> <span data-ttu-id="e1b03-114">XPath `position()` 和 `last()` 函数需要此上下文，因为这两个函数相对于当前上下文节点。</span><span class="sxs-lookup"><span data-stu-id="e1b03-114">This context is required for the XPath `position()` and `last()` functions as they are relative to the current context node.</span></span> <span data-ttu-id="e1b03-115">除非在定位步骤中作为谓词使用，`position()` 和 `last()` 函数要求引用节点集以便进行计算，否则，`position` 和 `last` 函数将返回 `0`。</span><span class="sxs-lookup"><span data-stu-id="e1b03-115">Unless used as a predicate in a location step, the `position()` and `last()` functions require a reference to a node set in order to be evaluated otherwise, the `position` and `last` functions return `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1b03-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="e1b03-116">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="e1b03-117">使用 XPath 数据模型处理 XML 数据</span><span class="sxs-lookup"><span data-stu-id="e1b03-117">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="e1b03-118">使用 XPathNavigator 选择 XML 数据</span><span class="sxs-lookup"><span data-stu-id="e1b03-118">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="e1b03-119">使用 XPathNavigator 匹配节点</span><span class="sxs-lookup"><span data-stu-id="e1b03-119">Matching Nodes using XPathNavigator</span></span>](matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="e1b03-120">XPath 查询识别的节点类型</span><span class="sxs-lookup"><span data-stu-id="e1b03-120">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="e1b03-121">XPath 查询和命名空间</span><span class="sxs-lookup"><span data-stu-id="e1b03-121">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)
- [<span data-ttu-id="e1b03-122">已编译的 XPath 表达式</span><span class="sxs-lookup"><span data-stu-id="e1b03-122">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)

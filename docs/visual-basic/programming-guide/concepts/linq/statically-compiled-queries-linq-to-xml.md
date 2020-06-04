---
title: 静态编译的查询 (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 3f4825c7-c3b0-48da-ba4e-8e97fb2a2f34
ms.openlocfilehash: f020c1ed8627df8c8386a059f0cea372e8df363e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406763"
---
# <a name="statically-compiled-queries-linq-to-xml-visual-basic"></a><span data-ttu-id="f62e4-102">静态编译的查询（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="f62e4-102">Statically Compiled Queries (LINQ to XML) (Visual Basic)</span></span>

<span data-ttu-id="f62e4-103">LINQ to XML 的一个最重要的性能优势（与 <xref:System.Xml.XmlDocument> 相比）为：LINQ to XML 中的查询是静态编译的，而 XPath 查询则必须在运行时进行解释。</span><span class="sxs-lookup"><span data-stu-id="f62e4-103">One of the most important performance benefits LINQ to XML, as opposed to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="f62e4-104">此功能是 LINQ to XML 的内置功能，因此您不必执行额外的步骤即可利用此功能，但在这两项技术之间做出选择时了解它们的区别将很有帮助。</span><span class="sxs-lookup"><span data-stu-id="f62e4-104">This feature is built in to LINQ to XML, so you do not have to perform extra steps to take advantage of it, but it is helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="f62e4-105">本主题解释了其中的区别。</span><span class="sxs-lookup"><span data-stu-id="f62e4-105">This topic explains the difference.</span></span>

## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="f62e4-106">静态编译的查询与 XPath 对比</span><span class="sxs-lookup"><span data-stu-id="f62e4-106">Statically Compiled Queries vs. XPath</span></span>

<span data-ttu-id="f62e4-107">下面的示例演示如何获取具有指定名称并包含带有指定值的属性的子代元素。</span><span class="sxs-lookup"><span data-stu-id="f62e4-107">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>

<span data-ttu-id="f62e4-108">以下是等效的 XPath 表达式：</span><span class="sxs-lookup"><span data-stu-id="f62e4-108">The following is the equivalent XPath expression:</span></span>

```vb
//Address[@Type='Shipping']
```

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 = From el In po.Descendants("Address")
            Where el.@Type = "Shipping"

For Each el In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="f62e4-109">编译器将本示例中的查询表达式重新编写为基于方法的查询语法。</span><span class="sxs-lookup"><span data-stu-id="f62e4-109">The query expression in this example is re-written by the compiler to method-based query syntax.</span></span> <span data-ttu-id="f62e4-110">以下使用基于方法的查询语法编写的示例将生成与上一示例相同的结果：</span><span class="sxs-lookup"><span data-stu-id="f62e4-110">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="f62e4-111"><xref:System.Linq.Enumerable.Where%2A> 方法为扩展方法。</span><span class="sxs-lookup"><span data-stu-id="f62e4-111">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="f62e4-112">有关详细信息，请参阅[扩展方法](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="f62e4-112">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="f62e4-113">由于 <xref:System.Linq.Enumerable.Where%2A> 是一个扩展方法，因此会将上面的查询视为按以下形式编写的查询进行编译：</span><span class="sxs-lookup"><span data-stu-id="f62e4-113">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="f62e4-114">此示例将生成与前面两个示例完全相同的结果。</span><span class="sxs-lookup"><span data-stu-id="f62e4-114">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="f62e4-115">这一结果表明：这些查询已被有效地编译成静态链接的方法调用。</span><span class="sxs-lookup"><span data-stu-id="f62e4-115">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="f62e4-116">这与迭代器的延迟执行语义一起可提高性能。</span><span class="sxs-lookup"><span data-stu-id="f62e4-116">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="f62e4-117">有关迭代器的延迟执行语义的详细信息，请参阅[LINQ to XML （Visual Basic）中的延迟执行和迟缓计算](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="f62e4-117">For more information about the deferred execution semantics of iterators, see [Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>

> [!NOTE]
> <span data-ttu-id="f62e4-118">这些示例代表了编译器可能编写的代码。</span><span class="sxs-lookup"><span data-stu-id="f62e4-118">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="f62e4-119">这些示例的实际实现可能会略有不同，但对于这些示例来说，执行的性能是相同或类似的。</span><span class="sxs-lookup"><span data-stu-id="f62e4-119">The actual implementation might differ slightly from these examples, but the performance will be the same or similar to these examples.</span></span>

## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="f62e4-120">使用 XmlDocument 执行 XPath 表达式</span><span class="sxs-lookup"><span data-stu-id="f62e4-120">Executing XPath Expressions with XmlDocument</span></span>

<span data-ttu-id="f62e4-121">下面的示例使用 <xref:System.Xml.XmlDocument> 来完成与前面的示例相同的结果：</span><span class="sxs-lookup"><span data-stu-id="f62e4-121">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>

```vb
Dim reader = Xml.XmlReader.Create("PurchaseOrders.xml")
Dim doc As New Xml.XmlDocument()
doc.Load(reader)
Dim nl As Xml.XmlNodeList = doc.SelectNodes(".//Address[@Type='Shipping']")
For Each n As Xml.XmlNode In nl
    Console.WriteLine(n.OuterXml)
Next
reader.Close()
```

<span data-ttu-id="f62e4-122">此查询将返回与使用 LINQ to XML 的示例相同的输出；唯一的差别是：LINQ to XML 会缩进输出的 XML，而 <xref:System.Xml.XmlDocument> 不会。</span><span class="sxs-lookup"><span data-stu-id="f62e4-122">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> does not.</span></span>

<span data-ttu-id="f62e4-123">但是，<xref:System.Xml.XmlDocument> 方法的执行性能通常不如 LINQ to XML，因为在每次调用 <xref:System.Xml.XmlNode.SelectNodes%2A> 方法时，它都必须在内部执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="f62e4-123">However, the <xref:System.Xml.XmlDocument> approach generally does not perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following internally every time it is called:</span></span>

- <span data-ttu-id="f62e4-124">分析包含 XPath 表达式的字符串，并将字符串划分成多个标记。</span><span class="sxs-lookup"><span data-stu-id="f62e4-124">It parses the string that contains the XPath expression, breaking the string into tokens.</span></span>

- <span data-ttu-id="f62e4-125">验证这些标记以确保 XPath 表达式有效。</span><span class="sxs-lookup"><span data-stu-id="f62e4-125">It validates the tokens to make sure that the XPath expression is valid.</span></span>

- <span data-ttu-id="f62e4-126">将表达式转换为内部表达式树。</span><span class="sxs-lookup"><span data-stu-id="f62e4-126">It translates the expression into an internal expression tree.</span></span>

- <span data-ttu-id="f62e4-127">循环访问节点，为基于表达式计算的结果集选择适当的节点。</span><span class="sxs-lookup"><span data-stu-id="f62e4-127">It iterates through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>

<span data-ttu-id="f62e4-128">与相应的 LINQ to XML 查询完成的工作相比，这需要执行非常多的工作。</span><span class="sxs-lookup"><span data-stu-id="f62e4-128">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="f62e4-129">特定的性能差异将因不同的查询类型而异，但一般来说，与使用 <xref:System.Xml.XmlDocument> 计算 XPath 表达式相比，LINQ to XML 查询执行的工作较少，因此会获得更好的性能。</span><span class="sxs-lookup"><span data-stu-id="f62e4-129">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>

## <a name="see-also"></a><span data-ttu-id="f62e4-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f62e4-130">See also</span></span>

- [<span data-ttu-id="f62e4-131">性能（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="f62e4-131">Performance (LINQ to XML) (Visual Basic)</span></span>](performance-linq-to-xml.md)

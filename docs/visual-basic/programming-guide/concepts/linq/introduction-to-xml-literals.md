---
title: Visual Basic2 中的 XML 文本简介
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: 8b92d22727c50274d57a5e407a0ca42807de3a94
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397579"
---
# <a name="introduction-to-xml-literals-in-visual-basic"></a><span data-ttu-id="a1ad9-102">Visual Basic 中的 XML 文本简介</span><span class="sxs-lookup"><span data-stu-id="a1ad9-102">Introduction to XML Literals in Visual Basic</span></span>
<span data-ttu-id="a1ad9-103">本部分提供有关在 Visual Basic 中创建 XML 树的信息。</span><span class="sxs-lookup"><span data-stu-id="a1ad9-103">This section provides information about creating XML trees in Visual Basic.</span></span>  
  
 <span data-ttu-id="a1ad9-104">有关使用 LINQ 查询结果作为 XML 树的内容的信息，请参阅[功能构造（LINQ to XML）（Visual Basic）](functional-construction-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="a1ad9-104">For information about using the results of LINQ queries as the content for an XML tree, see [Functional Construction (LINQ to XML) (Visual Basic)](functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="a1ad9-105">有关 Visual Basic 中的 XML 文本的详细信息，请参阅[Visual Basic 中的 LINQ to XML 概述](../../language-features/xml/overview-of-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="a1ad9-105">For more information on XML literals in Visual Basic, see [Overview of LINQ to XML in Visual Basic](../../language-features/xml/overview-of-linq-to-xml.md).</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="a1ad9-106">创建 XML 树</span><span class="sxs-lookup"><span data-stu-id="a1ad9-106">Creating XML Trees</span></span>  
 <span data-ttu-id="a1ad9-107">下面的示例演示如何创建一个 <xref:System.Xml.Linq.XElement>，在本例中为 `contacts`：</span><span class="sxs-lookup"><span data-stu-id="a1ad9-107">The following example shows how to create an <xref:System.Xml.Linq.XElement>, in this case `contacts`:</span></span>  
  
```vb  
Dim contacts As XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone>206-555-0144</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
### <a name="creating-an-xelement-with-simple-content"></a><span data-ttu-id="a1ad9-108">创建包含简单内容的 XElement</span><span class="sxs-lookup"><span data-stu-id="a1ad9-108">Creating an XElement with Simple Content</span></span>  
 <span data-ttu-id="a1ad9-109">可以创建包含简单内容的 <xref:System.Xml.Linq.XElement>，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a1ad9-109">You can create an <xref:System.Xml.Linq.XElement> that contains simple content, as follows:</span></span>  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)
```  
  
 <span data-ttu-id="a1ad9-110">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="a1ad9-110">This example produces the following output:</span></span>  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a><span data-ttu-id="a1ad9-111">创建空元素</span><span class="sxs-lookup"><span data-stu-id="a1ad9-111">Creating an Empty Element</span></span>  
 <span data-ttu-id="a1ad9-112">可以创建一个空 <xref:System.Xml.Linq.XElement>，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a1ad9-112">You can create an empty <xref:System.Xml.Linq.XElement>, as follows:</span></span>  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="a1ad9-113">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="a1ad9-113">This example produces the following output:</span></span>  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a><span data-ttu-id="a1ad9-114">使用嵌入式表达式</span><span class="sxs-lookup"><span data-stu-id="a1ad9-114">Using Embedded Expressions</span></span>  
 <span data-ttu-id="a1ad9-115">XML 文本的一个重要特性是允许使用嵌入式表达式。</span><span class="sxs-lookup"><span data-stu-id="a1ad9-115">An important feature of XML literals is that they allow embedded expressions.</span></span> <span data-ttu-id="a1ad9-116">使用嵌入式表达式可以对表达式进行计算，并将表达式的结果插入到 XML 树中。</span><span class="sxs-lookup"><span data-stu-id="a1ad9-116">Embedded expressions enable you to evaluate an expression and insert the results of the expression into the XML tree.</span></span> <span data-ttu-id="a1ad9-117">如果表达式计算结果为 <xref:System.Xml.Linq.XElement> 类型，则向树中插入元素。</span><span class="sxs-lookup"><span data-stu-id="a1ad9-117">If the expression evaluates to a type of <xref:System.Xml.Linq.XElement>, an element is inserted into the tree.</span></span> <span data-ttu-id="a1ad9-118">如果表达式计算结果为 <xref:System.Xml.Linq.XAttribute> 类型，则向树中插入属性。</span><span class="sxs-lookup"><span data-stu-id="a1ad9-118">If the expression evaluates to a type of <xref:System.Xml.Linq.XAttribute>, an attribute is inserted into the tree.</span></span> <span data-ttu-id="a1ad9-119">只能将元素和属性插入到它们在树中有效的位置。</span><span class="sxs-lookup"><span data-stu-id="a1ad9-119">You can insert elements and attributes into the tree only where they are valid.</span></span>  
  
 <span data-ttu-id="a1ad9-120">应当注意，只能将单个表达式放入嵌入式表达式。</span><span class="sxs-lookup"><span data-stu-id="a1ad9-120">It is important to note that only a single expression can go into an embedded expression.</span></span> <span data-ttu-id="a1ad9-121">不能嵌入多个语句。</span><span class="sxs-lookup"><span data-stu-id="a1ad9-121">You cannot embed multiple statements.</span></span> <span data-ttu-id="a1ad9-122">如果表达式超过一行，必须使用行继续符。</span><span class="sxs-lookup"><span data-stu-id="a1ad9-122">If an expression extends beyond a single line, you must use the line continuation character.</span></span>  
  
 <span data-ttu-id="a1ad9-123">如果使用嵌入式表达式将现有的节点（包括元素）和属性添加到新的 XML 树中，并且如果这些现有的节点已经有父级，则会克隆这些节点。</span><span class="sxs-lookup"><span data-stu-id="a1ad9-123">If you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree and if the existing nodes are already parented, the nodes are cloned.</span></span> <span data-ttu-id="a1ad9-124">新克隆的节点将附加到新 XML 树中。</span><span class="sxs-lookup"><span data-stu-id="a1ad9-124">The newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="a1ad9-125">如果现有节点没有父级，则直接将这些节点附加到新 XML 树中。</span><span class="sxs-lookup"><span data-stu-id="a1ad9-125">If the existing nodes are not parented, the nodes are simply attached to the new XML tree.</span></span> <span data-ttu-id="a1ad9-126">本主题最后一个示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="a1ad9-126">The last example in this topic demonstrates this.</span></span>  
  
 <span data-ttu-id="a1ad9-127">下面的示例使用嵌入式表达式将一个元素插入到树中：</span><span class="sxs-lookup"><span data-stu-id="a1ad9-127">The following example uses an embedded expression to insert an element into the tree:</span></span>  
  
```vb  
xmlTree1 As XElement = _  
    <Root>  
        <Child>Contents</Child>  
    </Root>  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child> %>  
    </Root>  
Console.WriteLine(xmlTree2)  
```  
  
 <span data-ttu-id="a1ad9-128">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="a1ad9-128">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>Contents</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-content"></a><span data-ttu-id="a1ad9-129">使用嵌入式表达式提供内容</span><span class="sxs-lookup"><span data-stu-id="a1ad9-129">Using Embedded Expressions for Content</span></span>  
 <span data-ttu-id="a1ad9-130">可以使用嵌入式表达式来提供元素的内容：</span><span class="sxs-lookup"><span data-stu-id="a1ad9-130">You can use an embedded expression to supply the content of an element:</span></span>  
  
```vb  
Dim str As String  
str = "Some content"  
Dim root As XElement = <Root><%= str %></Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="a1ad9-131">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="a1ad9-131">This example produces the following output:</span></span>  
  
```xml  
<Root>Some content</Root>  
```  
  
### <a name="using-a-linq-query-in-an-embedded-expression"></a><span data-ttu-id="a1ad9-132">在嵌入式表达式中使用 LINQ 查询</span><span class="sxs-lookup"><span data-stu-id="a1ad9-132">Using a LINQ Query in an Embedded Expression</span></span>  
 <span data-ttu-id="a1ad9-133">可以使用 LINQ 查询结果作为元素的内容：</span><span class="sxs-lookup"><span data-stu-id="a1ad9-133">You can use the results of a LINQ query for the content of an element:</span></span>  
  
```vb  
Dim arr As Integer() = {1, 2, 3}  
  
Dim n As XElement = _  
    <Root>  
        <%= From i In arr Select <Child><%= i %></Child> %>  
    </Root>  
  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="a1ad9-134">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="a1ad9-134">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Child>3</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-node-names"></a><span data-ttu-id="a1ad9-135">使用嵌入式表达式提供节点名称</span><span class="sxs-lookup"><span data-stu-id="a1ad9-135">Using Embedded Expressions for Node Names</span></span>  
 <span data-ttu-id="a1ad9-136">还可以使用嵌入式表达式计算属性名称、属性值、元素名称和元素值：</span><span class="sxs-lookup"><span data-stu-id="a1ad9-136">You can also use embedded expressions to calculate attribute names, attribute values, element names, and element values:</span></span>  
  
```vb  
Dim eleName As String = "ele"  
Dim attName As String = "att"  
Dim attValue As String = "aValue"  
Dim eleValue As String = "eValue"  
Dim n As XElement = _  
    <Root <%= attName %>=<%= attValue %>>  
        <<%= eleName %>>  
            <%= eleValue %>  
        </>  
    </Root>  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="a1ad9-137">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="a1ad9-137">This example produces the following output:</span></span>  
  
```xml  
<Root att="aValue">  
  <ele>eValue</ele>  
</Root>  
```  
  
### <a name="cloning-vs-attaching"></a><span data-ttu-id="a1ad9-138">克隆与附加</span><span class="sxs-lookup"><span data-stu-id="a1ad9-138">Cloning vs. Attaching</span></span>  
 <span data-ttu-id="a1ad9-139">如前面所述，如果使用嵌入式表达式将现有节点（包括元素）和属性添加到新的 XML 树中，并且如果这些现有节点已经有父级，则克隆这些节点，并将新克隆的节点附加到新的 XML 树中。</span><span class="sxs-lookup"><span data-stu-id="a1ad9-139">As mentioned earlier, if you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree, if the existing nodes are already parented, the nodes are cloned and the newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="a1ad9-140">如果现有节点没有父级，则直接将这些节点附加到新 XML 树中。</span><span class="sxs-lookup"><span data-stu-id="a1ad9-140">If the existing nodes are not parented, they are simply attached to the new XML tree.</span></span>  
  
```vb  
' Create a tree with a child element.  
Dim xmlTree1 As XElement = _  
    <Root>  
        <Child1>1</Child1>  
    </Root>  
  
' Create an element that is not parented.  
Dim child2 As XElement = <Child2>2</Child2>  
  
' Create a tree and add Child1 and Child2 to it.  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child1>(0) %>  
        <%= child2 %>  
    </Root>  
  
' Compare Child1 identity.  
Console.WriteLine("Child1 was {0}", _  
    IIf(xmlTree1.Element("Child1") Is xmlTree2.Element("Child1"), _  
    "attached", "cloned"))  
  
' Compare Child2 identity.  
Console.WriteLine("Child2 was {0}", _  
    IIf(child2 Is xmlTree2.Element("Child2"), _  
    "attached", "cloned"))  
```  
  
 <span data-ttu-id="a1ad9-141">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="a1ad9-141">This example produces the following output:</span></span>  
  
```console  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="a1ad9-142">请参阅</span><span class="sxs-lookup"><span data-stu-id="a1ad9-142">See also</span></span>

- [<span data-ttu-id="a1ad9-143">创建 XML 树（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="a1ad9-143">Creating XML Trees (Visual Basic)</span></span>](creating-xml-trees.md)

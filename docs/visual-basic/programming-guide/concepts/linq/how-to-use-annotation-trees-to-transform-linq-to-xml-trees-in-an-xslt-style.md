---
title: 如何：使用批注转换 XSLT 样式的 LINQ to XML 树
ms.date: 07/20/2015
ms.assetid: 08e91fa2-dac2-4463-9ef1-87b1ac3fa890
ms.openlocfilehash: 099457eaab8c80605138d7e67d7bc2823e316234
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364443"
---
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-visual-basic"></a><span data-ttu-id="1ccf6-102">如何：使用批注以 XSLT 样式转换 LINQ to XML 树（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="1ccf6-102">How to: Use Annotations to Transform LINQ to XML Trees in an XSLT Style (Visual Basic)</span></span>

<span data-ttu-id="1ccf6-103">使用批注可帮助进行 XML 树的转换。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-103">Annotations can be used to facilitate transforms of an XML tree.</span></span>

<span data-ttu-id="1ccf6-104">有些 XML 文档“以文档为中心兼有混合内容”。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-104">Some XML documents are "document centric with mixed content."</span></span> <span data-ttu-id="1ccf6-105">对于这样的文档，您不必知道元素的子节点的形状。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-105">With such documents, you don't necessarily know the shape of child nodes of an element.</span></span> <span data-ttu-id="1ccf6-106">例如，包含文本的节点可能具有像下面这样的外观：</span><span class="sxs-lookup"><span data-stu-id="1ccf6-106">For instance, a node that contains text may look like this:</span></span>

```xml
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>
```

<span data-ttu-id="1ccf6-107">任何给定的文本节点都可以具有任意数量的子 `<b>` 和 `<i>` 元素。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-107">For any given text node, there may be any number of child `<b>` and `<i>` elements.</span></span> <span data-ttu-id="1ccf6-108">此方法扩展到多种其他情况：例如，可以包含各种子元素（如常规段落、项目符号段落和位图）的页面。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-108">This approach extends to a number of other situations: such as, pages that can contain a variety of child elements, such as regular paragraphs, bulleted paragraphs, and bitmaps.</span></span> <span data-ttu-id="1ccf6-109">表中的单元格可以包含文本，下拉列表或位图。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-109">Cells in a table may contain text, drop down lists, or bitmaps.</span></span> <span data-ttu-id="1ccf6-110">以文档为中心的 XML 的一个主要特性是您不必知道任一特定元素将具有哪些子元素。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-110">One of the primary characteristics of document centric XML is that you do not know which child element any particular element will have.</span></span>

<span data-ttu-id="1ccf6-111">如果在转换树中的元素时不必知道有关要转换元素的子级的太多信息，则这种方法（使用批注）就是一种有效的方法。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-111">If you want to transform elements in a tree where you don't necessarily know much about the children of the elements that you want to transform, then this approach that uses annotations is an effective approach.</span></span>

<span data-ttu-id="1ccf6-112">这种方法摘要如下：</span><span class="sxs-lookup"><span data-stu-id="1ccf6-112">The summary of the approach is:</span></span>

- <span data-ttu-id="1ccf6-113">首先，用替换元素批注树中的元素。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-113">First, annotate elements in the tree with a replacement element.</span></span>

- <span data-ttu-id="1ccf6-114">然后，循环访问整个树，创建一个新树，并用其批注替换树中的每个元素。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-114">Second, iterate through the entire tree, creating a new tree where you replace each element with its annotation.</span></span> <span data-ttu-id="1ccf6-115">本示例在名为 `XForm` 的函数中实现迭代和创建新树。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-115">This example implements the iteration and creation of the new tree in a function named `XForm`.</span></span>

<span data-ttu-id="1ccf6-116">具体地说，此方法包括：</span><span class="sxs-lookup"><span data-stu-id="1ccf6-116">In detail, the approach consists of:</span></span>

- <span data-ttu-id="1ccf6-117">执行一个或多个 LINQ to XML 查询，用这些查询返回要从一种形状转换为另一种形状的元素集。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-117">Execute one or more LINQ to XML queries that return the set of elements that you want to transform from one shape to another.</span></span> <span data-ttu-id="1ccf6-118">对于查询中的每个元素，添加一个新 <xref:System.Xml.Linq.XElement> 对象作为该元素的批注。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-118">For each element in the query, add a new <xref:System.Xml.Linq.XElement> object as an annotation to the element.</span></span> <span data-ttu-id="1ccf6-119">在转换的新树中会用此新元素替换批注的元素。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-119">This new element will replace the annotated element in the new, transformed tree.</span></span> <span data-ttu-id="1ccf6-120">这是示例中所示的唯一需要编写的代码。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-120">This is simple code to write, as demonstrated by the example.</span></span>

- <span data-ttu-id="1ccf6-121">作为批注添加的新元素可以包含新的子节点，它可以形成一个具有任意形状的子树。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-121">The new element that is added as an annotation can contain new child nodes; it can form a sub-tree with any desired shape.</span></span>

- <span data-ttu-id="1ccf6-122">有一条特殊规则：如果新元素的子节点位于不同的命名空间，即专门为此建立的命名空间（在本示例中，此命名空间为 `http://www.microsoft.com/LinqToXmlTransform/2007`），则不会将该子元素复制到新树。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-122">There is a special rule: If a child node of the new element is in a different namespace, a namespace that is made up for this purpose (in this example, the namespace is `http://www.microsoft.com/LinqToXmlTransform/2007`), then that child element is not copied to the new tree.</span></span> <span data-ttu-id="1ccf6-123">而如果命名空间是上面提到的特殊命名空间，并且元素的本地名称为 `ApplyTransforms`，则会迭代源树中该元素的子节点并将其复制到新树（但批注的子元素本身例外，它们将根据这些规则进行转换）。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-123">Instead, if the namespace is the above mentioned special namespace, and the local name of the element is `ApplyTransforms`, then the child nodes of the element in the source tree are iterated, and copied to the new tree (with the exception that annotated child elements are themselves transformed according to these rules).</span></span>

- <span data-ttu-id="1ccf6-124">这有些类似于 XSL 中的转换规范。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-124">This is somewhat analogous to the specification of transforms in XSL.</span></span> <span data-ttu-id="1ccf6-125">用于选择一组节点的查询类似于用于模板的 XPath 表达式。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-125">The query that selects a set of nodes is analogous to the XPath expression for a template.</span></span> <span data-ttu-id="1ccf6-126">用于创建以批注形式保存的新 <xref:System.Xml.Linq.XElement> 的代码类似于 XSL 中的序列构造函数，`ApplyTransforms` 元素的功能类似于 XSL 中的 `xsl:apply-templates` 元素。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-126">The code to create the new <xref:System.Xml.Linq.XElement> that is saved as an annotation is analogous to the sequence constructor in XSL, and the `ApplyTransforms` element is analogous in function to the `xsl:apply-templates` element in XSL.</span></span>

- <span data-ttu-id="1ccf6-127">采用此方法的优势之一是在用公式表述查询时，您始终是对未修改的源树编写查询。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-127">One advantage to taking this approach - as you formulate queries, you are always writing queries on the unmodified source tree.</span></span> <span data-ttu-id="1ccf6-128">您不必担心对树所做的修改如何影响要编写的查询。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-128">You need not worry about how modifications to the tree affect the queries that you are writing.</span></span>

## <a name="transforming-a-tree"></a><span data-ttu-id="1ccf6-129">转换一个树</span><span class="sxs-lookup"><span data-stu-id="1ccf6-129">Transforming a Tree</span></span>

<span data-ttu-id="1ccf6-130">第一个示例将所有 `Paragraph` 节点重命名为 `para` ：</span><span class="sxs-lookup"><span data-stu-id="1ccf6-130">This first example renames all `Paragraph` nodes to `para`:</span></span>

```vb
Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">

Module Module1
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"

    Sub Main()
        Dim root As XElement = _
            <Root>
                <Paragraph>This is a sentence with <b>bold</b> and <i>italic</i> text.</Paragraph>
                <Paragraph>More text.</Paragraph>
            </Root>

        ' Replace Paragraph with p.
        For Each el In root...<Paragraph>
            ' same idea as xsl:apply-templates
            el.AddAnnotation( _
                <para>
                    <<%= at %>></>
                </para>)
        Next

        ' The XForm function, shown later in this topic, accomplishes the transform
        Dim newRoot As XElement = XForm(root)
        Console.WriteLine(newRoot)
    End Sub
End Module
```

 <span data-ttu-id="1ccf6-131">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="1ccf6-131">This example produces the following output:</span></span>

```xml
<Root>
  <para>This is a sentence with <b>bold</b> and <i>italic</i> text.</para>
  <para>More text.</para>
</Root>
```

## <a name="a-more-complicated-transform"></a><span data-ttu-id="1ccf6-132">更复杂的转换</span><span class="sxs-lookup"><span data-stu-id="1ccf6-132">A more complicated transform</span></span>

<span data-ttu-id="1ccf6-133">下面的示例对树进行查询并计算 `Data` 元素的平均值和总和，并将它们作为新元素添加到树中。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-133">The following example queries the tree and calculates the average and sum of the `Data` elements, and adds them as new elements to the tree.</span></span>

```vb
Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">

Module Module1
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"

    Sub Main()
        Dim data As XElement = _
            <Root>
                <Data>20</Data>
                <Data>10</Data>
                <Data>3</Data>
            </Root>

        ' While adding annotations, you can query the source tree all you want,
        ' as the tree is not mutated while annotating.
        data.AddAnnotation( _
            <Root>
                <<%= at %>/>
                <Average>
                    <%= _
                        String.Format("{0:F4}", _
                        data.Elements("Data") _
                        .Select(Function(z) CDec(z)).Average()) _
                    %>
                </Average>
                <Sum>
                    <%= _
                        data.Elements("Data").Select(Function(z) CInt(z)).Sum() _
                    %>
                </Sum>
            </Root> _
        )

        Console.WriteLine("Before Transform")
        Console.WriteLine("----------------")
        Console.WriteLine(data)
        Console.WriteLine(vbNewLine)

        ' The XForm function, shown later in this topic, accomplishes the transform
        Dim newData As XElement = XForm(data)

        Console.WriteLine("After Transform")
        Console.WriteLine("----------------")
        Console.WriteLine(newData)
    End Sub
End Module
```

<span data-ttu-id="1ccf6-134">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="1ccf6-134">This example produces the following output:</span></span>

```console
Before Transform
----------------
<Root>
  <Data>20</Data>
  <Data>10</Data>
  <Data>3</Data>
</Root>

After Transform
----------------
<Root>
  <Data>20</Data>
  <Data>10</Data>
  <Data>3</Data>
  <Average>11.0000</Average>
  <Sum>33</Sum>
</Root>
```

## <a name="effecting-the-transform"></a><span data-ttu-id="1ccf6-135">影响转换</span><span class="sxs-lookup"><span data-stu-id="1ccf6-135">Effecting the transform</span></span>

<span data-ttu-id="1ccf6-136">小函数 `XForm` 可以从原始的、已批注的树创建新的、转换后的树。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-136">A small function, `XForm`, creates a new transformed tree from the original, annotated tree.</span></span>

<span data-ttu-id="1ccf6-137">该函数的伪代码非常简单：</span><span class="sxs-lookup"><span data-stu-id="1ccf6-137">The pseudo code for the function is quite simple:</span></span>

> <span data-ttu-id="1ccf6-138">函数采用 System.xml.linq.xelement> 作为参数，并返回 System.xml.linq.xelement>。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-138">The function takes an XElement as an argument and returns an XElement.</span></span>
>
> <span data-ttu-id="1ccf6-139">如果元素具有 System.xml.linq.xelement> 批注，则返回新的 System.xml.linq.xelement>：</span><span class="sxs-lookup"><span data-stu-id="1ccf6-139">If an element has an XElement annotation, then return a new XElement:</span></span>
>
> - <span data-ttu-id="1ccf6-140">新 System.xml.linq.xelement> 的名称是 annotation 元素的名称。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-140">The name of the new XElement is the annotation element's name.</span></span>
> - <span data-ttu-id="1ccf6-141">所有属性都将从注释复制到新节点。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-141">All attributes are copied from the annotation to the new node.</span></span>
> - <span data-ttu-id="1ccf6-142">所有子节点都从批注进行复制，但特殊节点 xf： ApplyTransforms 被识别，并且源元素的子节点会进行迭代。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-142">All child nodes are copied from the annotation, with the exception that the special node xf:ApplyTransforms is recognized, and the source element's child nodes are iterated.</span></span> <span data-ttu-id="1ccf6-143">如果源子节点不是 System.xml.linq.xelement>，则会将其复制到新树。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-143">If the source child node is not an XElement, it is copied to the new tree.</span></span> <span data-ttu-id="1ccf6-144">如果源子级是 System.xml.linq.xelement>，则通过以递归方式调用此函数来转换它。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-144">If the source child is an XElement, then it is transformed by calling this function recursively.</span></span>
>
> <span data-ttu-id="1ccf6-145">如果未对元素进行批注：</span><span class="sxs-lookup"><span data-stu-id="1ccf6-145">If an element is not annotated:</span></span>
>
> - <span data-ttu-id="1ccf6-146">返回新的 System.xml.linq.xelement></span><span class="sxs-lookup"><span data-stu-id="1ccf6-146">Return a new XElement</span></span>
>   - <span data-ttu-id="1ccf6-147">新 System.xml.linq.xelement> 的名称为源元素的名称。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-147">The name of the new XElement is the source element's name.</span></span>
>   - <span data-ttu-id="1ccf6-148">所有属性均从源元素复制到目标的元素。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-148">All attributes are copied from the source element to the destination's element.</span></span>
>   - <span data-ttu-id="1ccf6-149">从源元素复制所有子节点。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-149">All child nodes are copied from the source element.</span></span>
>   - <span data-ttu-id="1ccf6-150">如果源子节点不是 System.xml.linq.xelement>，则会将其复制到新树。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-150">If the source child node is not an XElement, it is copied to the new tree.</span></span> <span data-ttu-id="1ccf6-151">如果源子级是 System.xml.linq.xelement>，则通过以递归方式调用此函数来转换它。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-151">If the source child is an XElement, then it is transformed by calling this function recursively.</span></span>

<span data-ttu-id="1ccf6-152">下面的代码是此函数的实现：</span><span class="sxs-lookup"><span data-stu-id="1ccf6-152">The following code is the implementation of this function:</span></span>

```vb
' Build a transformed XML tree per the annotations.
Function XForm(ByVal source As XElement) As XElement
    If source.Annotation(Of XElement)() IsNot Nothing Then
        Dim anno As XElement = source.Annotation(Of XElement)()
        Return _
            <<%= anno.Name.ToString() %>>
                <%= anno.Attributes() %>
                <%= anno.Nodes().Select(Function(n As XNode) _
                    GetSubNodes(n, source)) %>
            </>
    Else
        Return _
            <<%= source.Name %>>
                <%= source.Attributes() %>
                <%= source.Nodes().Select(Function(n) GetExpandedNodes(n)) %>
            </>
    End If
End Function

Private Function GetSubNodes(ByVal n As XNode, ByVal s As XElement) As Object
    Dim annoEl As XElement = TryCast(n, XElement)
    If annoEl IsNot Nothing Then
        If annoEl.Name = at Then
            Return s.Nodes().Select(Function(n2 As XNode) GetExpandedNodes(n2))
        End If
    End If
    Return n
End Function

Private Function GetExpandedNodes(ByVal n2 As XNode) As XNode
    Dim e2 As XElement = TryCast(n2, XElement)
    If e2 Is Nothing Then
        Return n2
    Else
        Return XForm(e2)
    End If
End Function
```

## <a name="complete-example"></a><span data-ttu-id="1ccf6-153">完整示例</span><span class="sxs-lookup"><span data-stu-id="1ccf6-153">Complete example</span></span>

<span data-ttu-id="1ccf6-154">下面的代码是包括 `XForm` 函数的完整示例。</span><span class="sxs-lookup"><span data-stu-id="1ccf6-154">The following code is a complete example that includes the `XForm` function.</span></span> <span data-ttu-id="1ccf6-155">它包括此类型转换的几种典型用法：</span><span class="sxs-lookup"><span data-stu-id="1ccf6-155">It includes a few of the typical uses of this type of transform:</span></span>

```vb
Imports System.Collections.Generic
Imports System.Linq
Imports System.Text
Imports System.Xml
Imports System.Xml.Linq

Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">

Module Module1
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"

    ' Build a transformed XML tree per the annotations.
    Function XForm(ByVal source As XElement) As XElement
        If source.Annotation(Of XElement)() IsNot Nothing Then
            Dim anno As XElement = source.Annotation(Of XElement)()
            Return _
                <<%= anno.Name.ToString() %>>
                    <%= anno.Attributes() %>
                    <%= anno.Nodes().Select(Function(n As XNode) _
                        GetSubNodes(n, source)) %>
                </>
        Else
            Return _
                <<%= source.Name %>>
                    <%= source.Attributes() %>
                    <%= source.Nodes().Select(Function(n) GetExpandedNodes(n)) %>
                </>
        End If
    End Function

    Private Function GetSubNodes(ByVal n As XNode, ByVal s As XElement) As Object
        Dim annoEl As XElement = TryCast(n, XElement)
        If annoEl IsNot Nothing Then
            If annoEl.Name = at Then
                Return s.Nodes().Select(Function(n2 As XNode) GetExpandedNodes(n2))
            End If
        End If
        Return n
    End Function

    Private Function GetExpandedNodes(ByVal n2 As XNode) As XNode
        Dim e2 As XElement = TryCast(n2, XElement)
        If e2 Is Nothing Then
            Return n2
        Else
            Return XForm(e2)
        End If
    End Function

    Sub Main()
        Dim root As XElement = _
<Root Att1='123'>
    <!--A comment-->
    <Child>1</Child>
    <Child>2</Child>
    <Other>
        <GC>3</GC>
        <GC>4</GC>
    </Other>
    <SomeMixedContent>This is <i>an</i> element that <b>has</b> some mixed content</SomeMixedContent>
    <AnUnchangedElement>42</AnUnchangedElement>
</Root>

        ' Each of the following serves the same semantic purpose as
        ' XSLT templates and sequence constructors.

        ' Replace Child with NewChild.
        For Each el In root.<Child>
            el.AddAnnotation(<NewChild><%= CStr(el) %></NewChild>)
        Next

        ' Replace first GC with GrandChild, add an attribute.
        For Each el In root...<GC>.Take(1)
            el.AddAnnotation(<GrandChild ANewAttribute='999'><%= CStr(el) %></GrandChild>)
        Next

        ' Replace Other with NewOther, add new child elements around original content.
        For Each el In root.<Other>
            el.AddAnnotation( _
                <NewOther>
                    <MyNewChild>1</MyNewChild>
                    <<%= at %>></>
                    <ChildThatComesAfter/>
                </NewOther>)
        Next

        ' Change name of element that has mixed content.
        root...<SomeMixedContent>(0).AddAnnotation( _
                <MixedContent><<%= at %>></></MixedContent>)

        ' Replace <b> with <Bold>.
        For Each el In root...<b>
            el.AddAnnotation(<Bold><<%= at %>></></Bold>)
        Next

        ' Replace <i> with <Italic>.
        For Each el In root...<i>
            el.AddAnnotation(<Italic><<%= at %>></></Italic>)
        Next

        Console.WriteLine("Before Transform")
        Console.WriteLine("----------------")
        Console.WriteLine(root)
        Console.WriteLine(vbNewLine)
        Dim newRoot As XElement = XForm(root)

        Console.WriteLine("After Transform")
        Console.WriteLine("----------------")
        Console.WriteLine(newRoot)
    End Sub
End Module
```

<span data-ttu-id="1ccf6-156">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="1ccf6-156">This example produces the following output:</span></span>

```console
Before Transform
----------------
<Root Att1="123">
  <!--A comment-->
  <Child>1</Child>
  <Child>2</Child>
  <Other>
    <GC>3</GC>
    <GC>4</GC>
  </Other>
  <SomeMixedContent>This is <i>an</i> element that <b>has</b> some mixed content</SomeMixedContent>
  <AnUnchangedElement>42</AnUnchangedElement>
</Root>

After Transform
----------------
<Root Att1="123">
  <!--A comment-->
  <NewChild>1</NewChild>
  <NewChild>2</NewChild>
  <NewOther>
    <MyNewChild>1</MyNewChild>
    <GrandChild ANewAttribute="999">3</GrandChild>
    <GC>4</GC>
    <ChildThatComesAfter />
  </NewOther>
  <MixedContent>This is <Italic>an</Italic> element that <Bold>has</Bold> some mixed content</MixedContent>
  <AnUnchangedElement>42</AnUnchangedElement>
</Root>
```

## <a name="see-also"></a><span data-ttu-id="1ccf6-157">请参阅</span><span class="sxs-lookup"><span data-stu-id="1ccf6-157">See also</span></span>

- [<span data-ttu-id="1ccf6-158">高级 LINQ to XML 编程（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="1ccf6-158">Advanced LINQ to XML Programming (Visual Basic)</span></span>](advanced-linq-to-xml-programming.md)

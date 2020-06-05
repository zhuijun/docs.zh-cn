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
# <a name="introduction-to-xml-literals-in-visual-basic"></a>Visual Basic 中的 XML 文本简介
本部分提供有关在 Visual Basic 中创建 XML 树的信息。  
  
 有关使用 LINQ 查询结果作为 XML 树的内容的信息，请参阅[功能构造（LINQ to XML）（Visual Basic）](functional-construction-linq-to-xml.md)。  
  
 有关 Visual Basic 中的 XML 文本的详细信息，请参阅[Visual Basic 中的 LINQ to XML 概述](../../language-features/xml/overview-of-linq-to-xml.md)。  
  
## <a name="creating-xml-trees"></a>创建 XML 树  
 下面的示例演示如何创建一个 <xref:System.Xml.Linq.XElement>，在本例中为 `contacts`：  
  
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
  
### <a name="creating-an-xelement-with-simple-content"></a>创建包含简单内容的 XElement  
 可以创建包含简单内容的 <xref:System.Xml.Linq.XElement>，如下所示：  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)
```  
  
 该示例产生下面的输出：  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a>创建空元素  
 可以创建一个空 <xref:System.Xml.Linq.XElement>，如下所示：  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 该示例产生下面的输出：  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a>使用嵌入式表达式  
 XML 文本的一个重要特性是允许使用嵌入式表达式。 使用嵌入式表达式可以对表达式进行计算，并将表达式的结果插入到 XML 树中。 如果表达式计算结果为 <xref:System.Xml.Linq.XElement> 类型，则向树中插入元素。 如果表达式计算结果为 <xref:System.Xml.Linq.XAttribute> 类型，则向树中插入属性。 只能将元素和属性插入到它们在树中有效的位置。  
  
 应当注意，只能将单个表达式放入嵌入式表达式。 不能嵌入多个语句。 如果表达式超过一行，必须使用行继续符。  
  
 如果使用嵌入式表达式将现有的节点（包括元素）和属性添加到新的 XML 树中，并且如果这些现有的节点已经有父级，则会克隆这些节点。 新克隆的节点将附加到新 XML 树中。 如果现有节点没有父级，则直接将这些节点附加到新 XML 树中。 本主题最后一个示例对此进行了演示。  
  
 下面的示例使用嵌入式表达式将一个元素插入到树中：  
  
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
  
 该示例产生下面的输出：  
  
```xml  
<Root>  
  <Child>Contents</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-content"></a>使用嵌入式表达式提供内容  
 可以使用嵌入式表达式来提供元素的内容：  
  
```vb  
Dim str As String  
str = "Some content"  
Dim root As XElement = <Root><%= str %></Root>  
Console.WriteLine(root)  
```  
  
 该示例产生下面的输出：  
  
```xml  
<Root>Some content</Root>  
```  
  
### <a name="using-a-linq-query-in-an-embedded-expression"></a>在嵌入式表达式中使用 LINQ 查询  
 可以使用 LINQ 查询结果作为元素的内容：  
  
```vb  
Dim arr As Integer() = {1, 2, 3}  
  
Dim n As XElement = _  
    <Root>  
        <%= From i In arr Select <Child><%= i %></Child> %>  
    </Root>  
  
Console.WriteLine(n)  
```  
  
 该示例产生下面的输出：  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Child>3</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-node-names"></a>使用嵌入式表达式提供节点名称  
 还可以使用嵌入式表达式计算属性名称、属性值、元素名称和元素值：  
  
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
  
 该示例产生下面的输出：  
  
```xml  
<Root att="aValue">  
  <ele>eValue</ele>  
</Root>  
```  
  
### <a name="cloning-vs-attaching"></a>克隆与附加  
 如前面所述，如果使用嵌入式表达式将现有节点（包括元素）和属性添加到新的 XML 树中，并且如果这些现有节点已经有父级，则克隆这些节点，并将新克隆的节点附加到新的 XML 树中。 如果现有节点没有父级，则直接将这些节点附加到新 XML 树中。  
  
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
  
 该示例产生下面的输出：  
  
```console  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a>请参阅

- [创建 XML 树（Visual Basic）](creating-xml-trees.md)

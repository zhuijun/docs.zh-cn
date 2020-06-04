---
title: XElement 类概述
ms.date: 07/20/2015
ms.assetid: 52331fcd-6023-4d19-b423-7b24f2d86ded
ms.openlocfilehash: a0e50c8a5a14150ee09a328f4dcdd5bc88363621
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413214"
---
# <a name="xelement-class-overview-visual-basic"></a>System.xml.linq.xelement> 类概述（Visual Basic）
<xref:System.Xml.Linq.XElement> 类是 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中的基础类之一。 它表示一个 XML 元素。 可以使用该类创建元素；更改元素内容；添加、更改或删除子元素；向元素中添加属性；或以文本格式序列化元素内容。 还可以与 <xref:System.Xml?displayProperty=nameWithType> 中的其他类（例如 <xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter> 和 <xref:System.Xml.Xsl.XslCompiledTransform>）进行互操作。  
  
## <a name="xelement-functionality"></a>XElement 功能  
 本主题描述 <xref:System.Xml.Linq.XElement> 类提供的功能。  
  
### <a name="constructing-xml-trees"></a>构造 XML 树  
 可以使用各种方式构造 XML 树，包括以下方式：  
  
- 可以在代码中构造 XML 树。 有关详细信息，请参阅[创建 XML 树（Visual Basic）](creating-xml-trees.md)。  
  
- 可以从包括 <xref:System.IO.TextReader>、文本文件或 Web 地址 (URL) 在内的各种源解析 XML。 有关详细信息，请参阅[分析 XML （Visual Basic）](parsing-xml.md)。  
  
- 可以使用 <xref:System.Xml.XmlReader> 来填充树。 有关详细信息，请参阅 <xref:System.Xml.Linq.XNode.ReadFrom%2A>。  
  
- 如果您有一个可以将内容写入 <xref:System.Xml.XmlWriter> 的模块，则可以使用 <xref:System.Xml.Linq.XContainer.CreateWriter%2A> 方法来创建编写器，将该编写器传递到该模块，然后使用写入 <xref:System.Xml.XmlWriter> 的内容来填充 XML 树。  
  
 但是，创建 XML 树的最常见的方法如下：  
  
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
  
 另一个创建 XML 树的十分常用的方法是使用 LINQ 查询的结果来填充 XML 树，如下面的示例所示：  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where el.Value > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 该示例产生下面的输出：  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
### <a name="serializing-xml-trees"></a>序列化 XML 树  
 可以将 XML 树序列化为 <xref:System.IO.File>、<xref:System.IO.TextWriter> 或 <xref:System.Xml.XmlWriter>。  
  
 有关详细信息，请参阅[序列化 XML 树（Visual Basic）](serializing-xml-trees.md)。  
  
### <a name="retrieving-xml-data-via-axis-methods"></a>通过轴方法检索 XML 数据  
 可以使用轴方法检索属性、子元素、子代元素和上级元素。 LINQ 查询对轴方法进行操作，并提供了多种灵活而有效的方法导航和处理 XML 树。  
  
 有关详细信息，请参阅[LINQ to XML 轴（Visual Basic）](linq-to-xml-axes.md)。  
  
### <a name="querying-xml-trees"></a>查询 XML 树  
 可以编写从 XML 树提取数据的 LINQ 查询。  
  
 有关详细信息，请参阅[查询 XML 树（Visual Basic）](querying-xml-trees.md)。  
  
### <a name="modifying-xml-trees"></a>修改 XML 树  
 可以通过各种方式修改元素，例如更改元素的内容或属性。 还可以从元素的父级移除元素。  
  
 有关详细信息，请参阅[修改 XML 树（LINQ to XML）（Visual Basic）](modifying-xml-trees-linq-to-xml.md)。  
  
## <a name="see-also"></a>另请参阅

- [LINQ to XML 编程概述（Visual Basic）](linq-to-xml-programming-overview.md)

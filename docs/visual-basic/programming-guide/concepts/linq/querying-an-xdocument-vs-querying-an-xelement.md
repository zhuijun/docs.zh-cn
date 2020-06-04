---
title: 查询 XDocument 与查询 XElement
ms.date: 07/20/2015
ms.assetid: 2d111f84-0ded-4cde-8d93-5440557a726d
ms.openlocfilehash: 3cd79c8f2cde101de43a9b9e983709e2e0d11814
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396293"
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-visual-basic"></a>查询 XDocument 与查询 System.xml.linq.xelement> （Visual Basic）
通过 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> 加载文档时，您会注意到，您要编写的查询与通过 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> 加载文档时稍有不同。  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a>XDocument.Load 与 XElement.Load 的比较  
 通过 <xref:System.Xml.Linq.XElement> 将 XML 文档加载到 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> 中时，位于 XML 树根部的 <xref:System.Xml.Linq.XElement> 包含所加载文档的根元素。 然而，通过 <xref:System.Xml.Linq.XDocument> 将同一个 XML 文档加载到 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> 中时，树根部为 <xref:System.Xml.Linq.XDocument> 节点，所加载文档的根元素为 <xref:System.Xml.Linq.XElement> 所允许的一个子 <xref:System.Xml.Linq.XDocument> 节点。 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 轴相对于根节点进行操作。  
  
 第一个示例使用 <xref:System.Xml.Linq.XElement.Load%2A> 加载 XML 树。 然后它查询树根部的子元素。  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XElement.Load")  
Console.WriteLine("----")  
Dim doc As XElement = XElement.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 此示例将按预期产生以下输出：  
  
```console
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 下面的示例与上面的基本相同，不同之处在于 XML 树是加载到 <xref:System.Xml.Linq.XDocument>，而不是加载到 <xref:System.Xml.Linq.XElement>。  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XDocument.Load")  
Console.WriteLine("----")  
Dim doc As XDocument = XDocument.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 该示例产生下面的输出：  
  
```console
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 请注意，同样的查询返回一个 `Root` 节点，而不是返回三个子节点。  
  
 处理这一问题的一种方法是在访问轴方法之前使用 <xref:System.Xml.Linq.XDocument.Root%2A> 属性，如下所示：  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XDocument.Load")  
Console.WriteLine("----")  
Dim doc As XDocument = XDocument.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Root.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 此查询现在的执行方式与根部位于 <xref:System.Xml.Linq.XElement> 中的树中的查询相同。 此示例产生以下输出：  
  
```console
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
## <a name="see-also"></a>另请参阅

- [基本查询（LINQ to XML）（Visual Basic）](basic-queries-linq-to-xml.md)

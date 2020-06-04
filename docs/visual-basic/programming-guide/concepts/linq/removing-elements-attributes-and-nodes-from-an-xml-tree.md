---
title: 从 XML 树中移除元素、特性和节点
ms.date: 07/20/2015
ms.assetid: 5cf21919-4360-4b49-b29d-58ea3164ac72
ms.openlocfilehash: f8be7fe521fb3c2662b105e34fd96fea1d1ac6e7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413397"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-visual-basic"></a>从 XML 树中移除元素、特性和节点（Visual Basic）
可以修改 XML 树，移除元素、属性和其他类型的节点。  
  
 从 XML 文档中移除单个元素或单个属性的操作非常简单。 但是，若要移除多个元素或属性的集合，则应首先将一个集合具体化为一个列表，然后从该列表中删除相应元素或属性。 最好的方法是使用 <xref:System.Xml.Linq.Extensions.Remove%2A> 扩展方法，该方法可以实现此操作。  
  
 这么做的主要原因在于，从 XML 树检索的大多数集合都是用延迟执行生成的。 如果不首先将集合具体化为列表，或者不使用扩展方法，则可能会遇到某类 Bug。 有关详细信息，请参阅[混合声明性代码/命令性代码 bug （LINQ to XML）（Visual Basic）](mixed-declarative-code-imperative-code-bugs-linq-to-xml.md)。  
  
 下列方法可以从 XML 树中移除节点和属性。  
  
|方法|说明|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|从父节点中移除 <xref:System.Xml.Linq.XAttribute>。|  
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|从 <xref:System.Xml.Linq.XContainer> 中移除子节点。|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|从 <xref:System.Xml.Linq.XElement> 中移除内容和属性。|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|移除 <xref:System.Xml.Linq.XElement> 的属性。|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|如果传递 `null` 作为值，则移除该属性。|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|如果传递 `null` 作为值，则移除该子元素。|  
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|从父节点中移除 <xref:System.Xml.Linq.XNode>。|  
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|从父元素中移除源集合中的每个属性或元素。|  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>说明  
 此示例演示三种移除元素的方法。 第一种，移除单个元素。 第二种，检索元素的集合，使用 <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> 运算符将它们具体化，然后移除集合。 最后一种，检索元素的集合，使用 <xref:System.Xml.Linq.Extensions.Remove%2A> 扩展方法移除元素。  
  
 有关运算符的详细信息 <xref:System.Linq.Enumerable.ToList%2A> ，请参阅[转换数据类型（Visual Basic）](converting-data-types.md)。  
  
### <a name="code"></a>代码  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>  
            <GrandChild1/>  
            <GrandChild2/>  
            <GrandChild3/>  
        </Child1>  
        <Child2>  
            <GrandChild4/>  
            <GrandChild5/>  
            <GrandChild6/>  
        </Child2>  
        <Child3>  
            <GrandChild7/>  
            <GrandChild8/>  
            <GrandChild9/>  
        </Child3>  
    </Root>  
root.<Child1>.<GrandChild1>.Remove()  
root.<Child2>.Elements().ToList().Remove()  
root.<Child3>.Elements().Remove()  
Console.WriteLine(root)  
```  
  
### <a name="comments"></a>注释  
 此代码生成以下输出：  
  
```xml  
<Root>  
  <Child1>  
    <GrandChild2 />  
    <GrandChild3 />  
  </Child1>  
  <Child2 />  
  <Child3 />  
</Root>  
```  
  
 请注意，第一个孙元素已从 `Child1` 中移除。 所有孙元素都已从 `Child2` 和 `Child3` 中移除。  
  
## <a name="see-also"></a>另请参阅

- [修改 XML 树（LINQ to XML）（Visual Basic）](modifying-xml-trees-linq-to-xml.md)

---
title: 向 XML 树添加元素、属性和节点 (C#)
description: 了解用于将内容（例如元素、属性、注释、处理指令和文本）添加到现有 XML 树中的方法。
ms.date: 07/20/2015
ms.assetid: db911e4f-40aa-499a-9500-a9763bb6df56
ms.openlocfilehash: 78a84401494e2d4280799632fa42dc95574e3e10
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105549"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-c"></a>向 XML 树添加元素、属性和节点 (C#)
可以向现有的 XML 树中添加内容（包括元素、属性、注释、处理指令、文本和 CDATA）。  
  
## <a name="methods-for-adding-content"></a>添加内容的方法  
 下面的方法将子内容添加到 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument> 中：  
  
|方法|说明|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|在 <xref:System.Xml.Linq.XContainer> 的子内容的末尾添加内容。|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|在 <xref:System.Xml.Linq.XContainer> 的子内容的开头添加内容。|  
  
 下面的方法将内容添加为 <xref:System.Xml.Linq.XNode> 的同级节点。 向其中添加同级内容的最常见的节点是 <xref:System.Xml.Linq.XElement>，不过你也可以将有效的同级内容添加到其他类型的节点，例如 <xref:System.Xml.Linq.XText> 或 <xref:System.Xml.Linq.XComment>。  
  
|方法|说明|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|在 <xref:System.Xml.Linq.XNode> 后面添加内容。|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|在 <xref:System.Xml.Linq.XNode> 前面添加内容。|  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>说明  
 下面的示例创建两个 XML 树，然后修改其中一个树。  
  
### <a name="code"></a>代码  
  
```csharp  
XElement srcTree = new XElement("Root",
    new XElement("Element1", 1),  
    new XElement("Element2", 2),  
    new XElement("Element3", 3),  
    new XElement("Element4", 4),  
    new XElement("Element5", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child1", 1),  
    new XElement("Child2", 2),  
    new XElement("Child3", 3),  
    new XElement("Child4", 4),  
    new XElement("Child5", 5)  
);  
xmlTree.Add(new XElement("NewChild", "new content"));  
xmlTree.Add(  
    from el in srcTree.Elements()  
    where (int)el > 3  
    select el  
);  
// Even though Child9 does not exist in srcTree, the following statement will not  
// throw an exception, and nothing will be added to xmlTree.  
xmlTree.Add(srcTree.Element("Child9"));  
Console.WriteLine(xmlTree);  
```  
  
### <a name="comments"></a>注释  
 此代码生成以下输出：  
  
```xml  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
  <Child4>4</Child4>  
  <Child5>5</Child5>  
  <NewChild>new content</NewChild>  
  <Element4>4</Element4>  
  <Element5>5</Element5>  
</Root>  
```  
  
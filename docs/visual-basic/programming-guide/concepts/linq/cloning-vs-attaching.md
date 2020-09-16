---
title: 克隆与附加
ms.date: 07/20/2015
ms.assetid: 3c3bd105-c9d3-49bd-875b-27ab4e8bc7a3
ms.openlocfilehash: 1974e10579e87f17746d5a9ba8a86ea8d819d9ea
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555752"
---
# <a name="cloning-vs-attaching-visual-basic"></a>克隆与附加 (Visual Basic) 
在将 <xref:System.Xml.Linq.XNode>（包括 <xref:System.Xml.Linq.XElement>）或 <xref:System.Xml.Linq.XAttribute> 对象添加到新树中时，如果新内容没有父级，则直接将这些对象附加到 XML 树中。 如果新内容已经有父级，并且是另一 XML 树的一部分，则克隆新内容。 然后将新克隆的内容附加到 XML 树中。  
  
## <a name="example"></a>示例  
 下面的代码演示将有父级的元素添加到树中，以及将没有父级的元素添加到树中时的行为。  
  
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

- [ (Visual Basic 创建 XML 树) ](../../../../standard/linq/xml-literals.md)

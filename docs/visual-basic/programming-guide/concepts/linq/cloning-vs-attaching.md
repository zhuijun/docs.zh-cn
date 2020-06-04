---
title: 克隆与附加
ms.date: 07/20/2015
ms.assetid: 3c3bd105-c9d3-49bd-875b-27ab4e8bc7a3
ms.openlocfilehash: aaf3344c0439d96a01006ee000d0a827884a5af9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410872"
---
# <a name="cloning-vs-attaching-visual-basic"></a><span data-ttu-id="c53e3-102">克隆与附加（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="c53e3-102">Cloning vs. Attaching (Visual Basic)</span></span>
<span data-ttu-id="c53e3-103">在将 <xref:System.Xml.Linq.XNode>（包括 <xref:System.Xml.Linq.XElement>）或 <xref:System.Xml.Linq.XAttribute> 对象添加到新树中时，如果新内容没有父级，则直接将这些对象附加到 XML 树中。</span><span class="sxs-lookup"><span data-stu-id="c53e3-103">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects to a new tree, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="c53e3-104">如果新内容已经有父级，并且是另一 XML 树的一部分，则克隆新内容。</span><span class="sxs-lookup"><span data-stu-id="c53e3-104">If the new content already is parented, and is part of another XML tree, the new content is cloned.</span></span> <span data-ttu-id="c53e3-105">然后将新克隆的内容附加到 XML 树中。</span><span class="sxs-lookup"><span data-stu-id="c53e3-105">The newly cloned content is then attached to the XML tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c53e3-106">示例</span><span class="sxs-lookup"><span data-stu-id="c53e3-106">Example</span></span>  
 <span data-ttu-id="c53e3-107">下面的代码演示将有父级的元素添加到树中，以及将没有父级的元素添加到树中时的行为。</span><span class="sxs-lookup"><span data-stu-id="c53e3-107">The following code demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>  
  
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
  
 <span data-ttu-id="c53e3-108">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="c53e3-108">This example produces the following output:</span></span>  
  
```console  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="c53e3-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="c53e3-109">See also</span></span>

- [<span data-ttu-id="c53e3-110">创建 XML 树（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="c53e3-110">Creating XML Trees (Visual Basic)</span></span>](creating-xml-trees.md)

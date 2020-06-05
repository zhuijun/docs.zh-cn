---
title: 将元素、特性和节点添加到 XML 树
ms.date: 07/20/2015
ms.assetid: e243e694-c987-43aa-8b22-1e33dace582c
ms.openlocfilehash: 5b80a19c952388c2591536077f382df2f69fe80f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84383892"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-visual-basic"></a><span data-ttu-id="b3f28-102">向 XML 树添加元素、属性和节点（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="b3f28-102">Adding Elements, Attributes, and Nodes to an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="b3f28-103">可以向现有的 XML 树中添加内容（包括元素、属性、注释、处理指令、文本和 CDATA）。</span><span class="sxs-lookup"><span data-stu-id="b3f28-103">You can add content (elements, attributes, comments, processing instructions, text, and CDATA) to an existing XML tree.</span></span>  
  
## <a name="methods-for-adding-content"></a><span data-ttu-id="b3f28-104">添加内容的方法</span><span class="sxs-lookup"><span data-stu-id="b3f28-104">Methods for Adding Content</span></span>  
 <span data-ttu-id="b3f28-105">下面的方法将子内容添加到 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument> 中：</span><span class="sxs-lookup"><span data-stu-id="b3f28-105">The following methods add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="b3f28-106">方法</span><span class="sxs-lookup"><span data-stu-id="b3f28-106">Method</span></span>|<span data-ttu-id="b3f28-107">说明</span><span class="sxs-lookup"><span data-stu-id="b3f28-107">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="b3f28-108">在 <xref:System.Xml.Linq.XContainer> 的子内容的末尾添加内容。</span><span class="sxs-lookup"><span data-stu-id="b3f28-108">Adds content at the end of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="b3f28-109">在 <xref:System.Xml.Linq.XContainer> 的子内容的开头添加内容。</span><span class="sxs-lookup"><span data-stu-id="b3f28-109">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
  
 <span data-ttu-id="b3f28-110">下面的方法将内容添加为 <xref:System.Xml.Linq.XNode> 的同级节点。</span><span class="sxs-lookup"><span data-stu-id="b3f28-110">The following methods add content as sibling nodes of an <xref:System.Xml.Linq.XNode>.</span></span> <span data-ttu-id="b3f28-111">向其中添加同级内容的最常见的节点是 <xref:System.Xml.Linq.XElement>，不过你也可以将有效的同级内容添加到其他类型的节点，例如 <xref:System.Xml.Linq.XText> 或 <xref:System.Xml.Linq.XComment>。</span><span class="sxs-lookup"><span data-stu-id="b3f28-111">The most common node to which you add sibling content is <xref:System.Xml.Linq.XElement>, although you can add valid sibling content to other types of nodes such as <xref:System.Xml.Linq.XText> or <xref:System.Xml.Linq.XComment>.</span></span>  
  
|<span data-ttu-id="b3f28-112">方法</span><span class="sxs-lookup"><span data-stu-id="b3f28-112">Method</span></span>|<span data-ttu-id="b3f28-113">说明</span><span class="sxs-lookup"><span data-stu-id="b3f28-113">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="b3f28-114">在 <xref:System.Xml.Linq.XNode> 后面添加内容。</span><span class="sxs-lookup"><span data-stu-id="b3f28-114">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="b3f28-115">在 <xref:System.Xml.Linq.XNode> 前面添加内容。</span><span class="sxs-lookup"><span data-stu-id="b3f28-115">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b3f28-116">示例</span><span class="sxs-lookup"><span data-stu-id="b3f28-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="b3f28-117">说明</span><span class="sxs-lookup"><span data-stu-id="b3f28-117">Description</span></span>  
 <span data-ttu-id="b3f28-118">下面的示例创建两个 XML 树，然后修改其中一个树。</span><span class="sxs-lookup"><span data-stu-id="b3f28-118">The following example creates two XML trees, and then modifies one of the trees.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b3f28-119">代码</span><span class="sxs-lookup"><span data-stu-id="b3f28-119">Code</span></span>  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element1>1</Element1>  
        <Element2>2</Element2>  
        <Element3>3</Element3>  
        <Element4>4</Element4>  
        <Element5>5</Element5>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child1>1</Child1>  
        <Child2>2</Child2>  
        <Child3>3</Child3>  
        <Child4>4</Child4>  
        <Child5>5</Child5>  
    </Root>  
  
xmlTree.Add(<NewChild>new content</NewChild>)  
xmlTree.Add( _  
    From el In srcTree.Elements() _  
    Where CInt(el) > 3 _  
    Select el)  
  
' Even though Child9 does not exist in srcTree, the following statement  
' will not throw an exception, and nothing will be added to xmlTree.  
xmlTree.Add(srcTree.Element("Child9"))  
Console.WriteLine(xmlTree)  
```  
  
### <a name="comments"></a><span data-ttu-id="b3f28-120">注释</span><span class="sxs-lookup"><span data-stu-id="b3f28-120">Comments</span></span>  
 <span data-ttu-id="b3f28-121">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="b3f28-121">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b3f28-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b3f28-122">See also</span></span>

- [<span data-ttu-id="b3f28-123">修改 XML 树（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="b3f28-123">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](modifying-xml-trees-linq-to-xml.md)

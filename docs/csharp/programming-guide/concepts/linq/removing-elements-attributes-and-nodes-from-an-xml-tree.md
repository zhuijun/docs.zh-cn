---
title: 从 XML 树中删除元素、属性和节点 (C#)
description: 了解如何从 XML 树中删除元素、属性和节点。 参阅删除方法和代码示例的列表。
ms.date: 07/20/2015
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: 4e753c3d96c4cbc050b08076ca8bff8c17b2e252
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87300041"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-c"></a><span data-ttu-id="51f29-104">从 XML 树中删除元素、属性和节点 (C#)</span><span class="sxs-lookup"><span data-stu-id="51f29-104">Removing Elements, Attributes, and Nodes from an XML Tree (C#)</span></span>

<span data-ttu-id="51f29-105">可以修改 XML 树，移除元素、属性和其他类型的节点。</span><span class="sxs-lookup"><span data-stu-id="51f29-105">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>

<span data-ttu-id="51f29-106">从 XML 文档中移除单个元素或单个属性的操作非常简单。</span><span class="sxs-lookup"><span data-stu-id="51f29-106">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="51f29-107">但是，若要移除多个元素或属性的集合，则应首先将一个集合具体化为一个列表，然后从该列表中删除相应元素或属性。</span><span class="sxs-lookup"><span data-stu-id="51f29-107">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="51f29-108">最好的方法是使用 <xref:System.Xml.Linq.Extensions.Remove%2A> 扩展方法，该方法可以实现此操作。</span><span class="sxs-lookup"><span data-stu-id="51f29-108">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>

<span data-ttu-id="51f29-109">这么做的主要原因在于，从 XML 树检索的大多数集合都是用延迟执行生成的。</span><span class="sxs-lookup"><span data-stu-id="51f29-109">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="51f29-110">如果不首先将集合具体化为列表，或者不使用扩展方法，则可能会遇到某类 Bug。</span><span class="sxs-lookup"><span data-stu-id="51f29-110">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="51f29-111">有关详细信息，请参阅[混合声明性代码/命令性代码的问题 (LINQ to XML) (C#)](./mixed-declarative-code-imperative-code-bugs-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="51f29-111">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)](./mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>

<span data-ttu-id="51f29-112">下列方法可以从 XML 树中移除节点和属性。</span><span class="sxs-lookup"><span data-stu-id="51f29-112">The following methods remove nodes and attributes from an XML tree.</span></span>

|<span data-ttu-id="51f29-113">方法</span><span class="sxs-lookup"><span data-stu-id="51f29-113">Method</span></span>|<span data-ttu-id="51f29-114">说明</span><span class="sxs-lookup"><span data-stu-id="51f29-114">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="51f29-115">从父节点中移除 <xref:System.Xml.Linq.XAttribute>。</span><span class="sxs-lookup"><span data-stu-id="51f29-115">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="51f29-116">从 <xref:System.Xml.Linq.XContainer> 中移除子节点。</span><span class="sxs-lookup"><span data-stu-id="51f29-116">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="51f29-117">从 <xref:System.Xml.Linq.XElement> 中移除内容和属性。</span><span class="sxs-lookup"><span data-stu-id="51f29-117">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="51f29-118">移除 <xref:System.Xml.Linq.XElement> 的属性。</span><span class="sxs-lookup"><span data-stu-id="51f29-118">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="51f29-119">如果传递 `null` 作为值，则移除该属性。</span><span class="sxs-lookup"><span data-stu-id="51f29-119">If you pass `null` for value, then removes the attribute.</span></span>|
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="51f29-120">如果传递 `null` 作为值，则移除该子元素。</span><span class="sxs-lookup"><span data-stu-id="51f29-120">If you pass `null` for value, then removes the child element.</span></span>|
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="51f29-121">从父节点中移除 <xref:System.Xml.Linq.XNode>。</span><span class="sxs-lookup"><span data-stu-id="51f29-121">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="51f29-122">从父元素中移除源集合中的每个属性或元素。</span><span class="sxs-lookup"><span data-stu-id="51f29-122">Removes every attribute or element in the source collection from its parent element.</span></span>|

## <a name="example"></a><span data-ttu-id="51f29-123">示例</span><span class="sxs-lookup"><span data-stu-id="51f29-123">Example</span></span>

### <a name="description"></a><span data-ttu-id="51f29-124">说明</span><span class="sxs-lookup"><span data-stu-id="51f29-124">Description</span></span>

<span data-ttu-id="51f29-125">此示例演示三种移除元素的方法。</span><span class="sxs-lookup"><span data-stu-id="51f29-125">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="51f29-126">第一种，移除单个元素。</span><span class="sxs-lookup"><span data-stu-id="51f29-126">First, it removes a single element.</span></span> <span data-ttu-id="51f29-127">第二种，检索元素的集合，使用 <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> 运算符将它们具体化，然后移除集合。</span><span class="sxs-lookup"><span data-stu-id="51f29-127">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and removes the collection.</span></span> <span data-ttu-id="51f29-128">最后一种，检索元素的集合，使用 <xref:System.Xml.Linq.Extensions.Remove%2A> 扩展方法移除元素。</span><span class="sxs-lookup"><span data-stu-id="51f29-128">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>

<span data-ttu-id="51f29-129">有关 <xref:System.Linq.Enumerable.ToList%2A> 运算符的详细信息，请参阅[转换数据类型 (C#)](./converting-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="51f29-129">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (C#)](./converting-data-types.md).</span></span>

### <a name="code"></a><span data-ttu-id="51f29-130">代码</span><span class="sxs-lookup"><span data-stu-id="51f29-130">Code</span></span>

```csharp
XElement root = XElement.Parse(@"<Root>
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
</Root>");
root.Element("Child1").Element("GrandChild1").Remove();
root.Element("Child2").Elements().ToList().Remove();
root.Element("Child3").Elements().Remove();
Console.WriteLine(root);
```

### <a name="comments"></a><span data-ttu-id="51f29-131">注释</span><span class="sxs-lookup"><span data-stu-id="51f29-131">Comments</span></span>

<span data-ttu-id="51f29-132">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="51f29-132">This code produces the following output:</span></span>

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

<span data-ttu-id="51f29-133">请注意，第一个孙元素已从 `Child1` 中移除。</span><span class="sxs-lookup"><span data-stu-id="51f29-133">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="51f29-134">所有孙元素都已从 `Child2` 和 `Child3` 中移除。</span><span class="sxs-lookup"><span data-stu-id="51f29-134">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>

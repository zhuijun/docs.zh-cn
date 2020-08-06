---
title: XElement 和 XDocument 对象的有效内容3
description: 了解可以传递给构造函数以及用于向元素和文档添加内容的方法的有效参数。
ms.date: 07/20/2015
ms.assetid: 0d253586-2b97-459f-b1a7-f30f38f3ed9f
ms.openlocfilehash: dfafbe76b078db6c22b475770ebadaff38c75ba8
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302251"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a><span data-ttu-id="19610-103">XElement 和 XDocument 对象的有效内容</span><span class="sxs-lookup"><span data-stu-id="19610-103">Valid Content of XElement and XDocument Objects</span></span>
<span data-ttu-id="19610-104">本主题描述可以传递给构造函数以及用于向元素和文档添加内容的方法的有效参数。</span><span class="sxs-lookup"><span data-stu-id="19610-104">This topic describes the valid arguments that can be passed to constructors and methods that you use to add content to elements and documents.</span></span>  
  
## <a name="valid-content"></a><span data-ttu-id="19610-105">有效内容</span><span class="sxs-lookup"><span data-stu-id="19610-105">Valid Content</span></span>  
 <span data-ttu-id="19610-106">查询计算的结果通常是 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement> 或 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XAttribute>。</span><span class="sxs-lookup"><span data-stu-id="19610-106">Queries often evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="19610-107">可以将 <xref:System.Xml.Linq.XElement> 集合或 <xref:System.Xml.Linq.XAttribute> 对象传递到 <xref:System.Xml.Linq.XElement> 构造函数。</span><span class="sxs-lookup"><span data-stu-id="19610-107">You can pass collections of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects to the <xref:System.Xml.Linq.XElement> constructor.</span></span> <span data-ttu-id="19610-108">所以，可以很方便地将查询的结果作为内容，传递给用于填充 XML 树的方法和构造函数。</span><span class="sxs-lookup"><span data-stu-id="19610-108">Therefore, it is convenient to pass the results of a query as content into methods and constructors that you use to populate XML trees.</span></span>  
  
 <span data-ttu-id="19610-109">添加简单内容时，可以将多种类型传递给此方法。</span><span class="sxs-lookup"><span data-stu-id="19610-109">When adding simple content, various types can be passed to this method.</span></span> <span data-ttu-id="19610-110">有效类型包括：</span><span class="sxs-lookup"><span data-stu-id="19610-110">Valid types include the following:</span></span>  
  
- <xref:System.String>  
  
- <xref:System.Double>  
  
- <xref:System.Single>  
  
- <xref:System.Decimal>  
  
- <xref:System.Boolean>  
  
- <xref:System.DateTime>  
  
- <xref:System.TimeSpan>  
  
- <xref:System.DateTimeOffset>  
  
- <span data-ttu-id="19610-111">实现 `Object.ToString` 的任何类型。</span><span class="sxs-lookup"><span data-stu-id="19610-111">Any type that implements `Object.ToString`.</span></span>  
  
- <span data-ttu-id="19610-112">实现 <xref:System.Collections.Generic.IEnumerable%601> 的任何类型。</span><span class="sxs-lookup"><span data-stu-id="19610-112">Any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="19610-113">添加复杂内容时，可以将多种类型传递给此方法：</span><span class="sxs-lookup"><span data-stu-id="19610-113">When adding complex content, various types can be passed to this method:</span></span>  
  
- <xref:System.Xml.Linq.XObject>  
  
- <xref:System.Xml.Linq.XNode>  
  
- <xref:System.Xml.Linq.XAttribute>  
  
- <span data-ttu-id="19610-114">实现 <xref:System.Collections.Generic.IEnumerable%601> 的任何类型</span><span class="sxs-lookup"><span data-stu-id="19610-114">Any type that implements <xref:System.Collections.Generic.IEnumerable%601></span></span>  
  
 <span data-ttu-id="19610-115">如果对象实现 <xref:System.Collections.Generic.IEnumerable%601>，则枚举对象中的集合，并添加集合中的所有项。</span><span class="sxs-lookup"><span data-stu-id="19610-115">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="19610-116">如果集合包含 <xref:System.Xml.Linq.XNode> 或 <xref:System.Xml.Linq.XAttribute> 对象，则单独添加集合中的每一项。</span><span class="sxs-lookup"><span data-stu-id="19610-116">If the collection contains <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="19610-117">如果集合包含文本（或转换成文本的对象），则集合中的文本是串联在一起的，并作为单个文本节点添加。</span><span class="sxs-lookup"><span data-stu-id="19610-117">If the collection contains text (or objects that are converted to text), the text in the collection is concatenated and added as a single text node.</span></span>  
  
 <span data-ttu-id="19610-118">如果内容为 `null`，则不添加任何内容。</span><span class="sxs-lookup"><span data-stu-id="19610-118">If content is `null`, nothing is added.</span></span> <span data-ttu-id="19610-119">传递集合时，集合中的项可以为 `null`。</span><span class="sxs-lookup"><span data-stu-id="19610-119">When passing a collection items in the collection can be `null`.</span></span> <span data-ttu-id="19610-120">集合中的 `null` 项对树没有任何影响。</span><span class="sxs-lookup"><span data-stu-id="19610-120">A `null` item in the collection has no effect on the tree.</span></span>  
  
 <span data-ttu-id="19610-121">添加的属性必须在其包含元素内具有唯一名称。</span><span class="sxs-lookup"><span data-stu-id="19610-121">An added attribute must have a unique name within its containing element.</span></span>  
  
 <span data-ttu-id="19610-122">在添加 <xref:System.Xml.Linq.XNode> 或 <xref:System.Xml.Linq.XAttribute> 对象时，如果新内容没有父级，则直接将这些对象附加到 XML 树中。</span><span class="sxs-lookup"><span data-stu-id="19610-122">When adding <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, then the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="19610-123">如果新内容已经有父级，并且是另一 XML 树的一部分，则克隆新内容，并将新克隆的内容附加到 XML 树。</span><span class="sxs-lookup"><span data-stu-id="19610-123">If the new content already is parented and is part of another XML tree, then the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
## <a name="valid-content-for-documents"></a><span data-ttu-id="19610-124">文档的有效内容</span><span class="sxs-lookup"><span data-stu-id="19610-124">Valid Content for Documents</span></span>  
 <span data-ttu-id="19610-125">属性和简单内容无法添加到文档。</span><span class="sxs-lookup"><span data-stu-id="19610-125">Attributes and simple content cannot be added to a document.</span></span>  
  
 <span data-ttu-id="19610-126">需要您创建 <xref:System.Xml.Linq.XDocument> 的情况不是很多。</span><span class="sxs-lookup"><span data-stu-id="19610-126">There are not many scenarios that require you to create an <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="19610-127">而是通常使用 <xref:System.Xml.Linq.XElement> 根节点创建 XML 树。</span><span class="sxs-lookup"><span data-stu-id="19610-127">Instead, you can usually create your XML trees with an <xref:System.Xml.Linq.XElement> root node.</span></span> <span data-ttu-id="19610-128">除非对创建文档有特定要求（例如，因为必须在顶级创建处理指令和注释，或者必须支持文档类型），否则使用 <xref:System.Xml.Linq.XElement> 作为根节点通常更为方便。</span><span class="sxs-lookup"><span data-stu-id="19610-128">Unless you have a specific requirement to create a document (for example, because you have to create processing instructions and comments at the top level, or you have to support document types), it is often more convenient to use <xref:System.Xml.Linq.XElement> as your root node.</span></span>  
  
 <span data-ttu-id="19610-129">文档的有效内容包括：</span><span class="sxs-lookup"><span data-stu-id="19610-129">Valid content for a document includes the following:</span></span>  
  
- <span data-ttu-id="19610-130">零个或一个 <xref:System.Xml.Linq.XDocumentType> 对象。</span><span class="sxs-lookup"><span data-stu-id="19610-130">Zero or one <xref:System.Xml.Linq.XDocumentType> objects.</span></span> <span data-ttu-id="19610-131">文档类型必须在元素之前。</span><span class="sxs-lookup"><span data-stu-id="19610-131">The document types must come before the element.</span></span>  
  
- <span data-ttu-id="19610-132">零个或一个元素。</span><span class="sxs-lookup"><span data-stu-id="19610-132">Zero or one element.</span></span>  
  
- <span data-ttu-id="19610-133">零个或多个注释。</span><span class="sxs-lookup"><span data-stu-id="19610-133">Zero or more comments.</span></span>  
  
- <span data-ttu-id="19610-134">零个或多个处理指令。</span><span class="sxs-lookup"><span data-stu-id="19610-134">Zero or more processing instructions.</span></span>  
  
- <span data-ttu-id="19610-135">零个或多个仅包含空白的文本节点。</span><span class="sxs-lookup"><span data-stu-id="19610-135">Zero or more text nodes that contain only white space.</span></span>  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a><span data-ttu-id="19610-136">允许添加内容的构造函数和函数</span><span class="sxs-lookup"><span data-stu-id="19610-136">Constructors and Functions that Allow Adding Content</span></span>  
 <span data-ttu-id="19610-137">下面的方法允许您将子内容添加到 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument> 中：</span><span class="sxs-lookup"><span data-stu-id="19610-137">The following methods allow you to add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="19610-138">方法</span><span class="sxs-lookup"><span data-stu-id="19610-138">Method</span></span>|<span data-ttu-id="19610-139">说明</span><span class="sxs-lookup"><span data-stu-id="19610-139">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|<span data-ttu-id="19610-140">构造一个 <xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="19610-140">Constructs an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|<span data-ttu-id="19610-141">构造一个 <xref:System.Xml.Linq.XDocument>。</span><span class="sxs-lookup"><span data-stu-id="19610-141">Constructs a <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="19610-142">添加到 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument> 的子内容的末尾。</span><span class="sxs-lookup"><span data-stu-id="19610-142">Adds to the end of the child content of the <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="19610-143">在 <xref:System.Xml.Linq.XNode> 后面添加内容。</span><span class="sxs-lookup"><span data-stu-id="19610-143">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="19610-144">在 <xref:System.Xml.Linq.XNode> 前面添加内容。</span><span class="sxs-lookup"><span data-stu-id="19610-144">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="19610-145">在 <xref:System.Xml.Linq.XContainer> 的子内容的开头添加内容。</span><span class="sxs-lookup"><span data-stu-id="19610-145">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|<span data-ttu-id="19610-146">替换 <xref:System.Xml.Linq.XElement> 的所有内容（子节点和属性）。</span><span class="sxs-lookup"><span data-stu-id="19610-146">Replaces all content (child nodes and attributes) of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|<span data-ttu-id="19610-147">替换 <xref:System.Xml.Linq.XElement> 的属性。</span><span class="sxs-lookup"><span data-stu-id="19610-147">Replaces the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|<span data-ttu-id="19610-148">用新内容替换子节点。</span><span class="sxs-lookup"><span data-stu-id="19610-148">Replaces the children nodes with new content.</span></span>|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|<span data-ttu-id="19610-149">用新内容替换节点。</span><span class="sxs-lookup"><span data-stu-id="19610-149">Replaces a node with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="19610-150">请参阅</span><span class="sxs-lookup"><span data-stu-id="19610-150">See also</span></span>

- [<span data-ttu-id="19610-151">创建 XML 树 (C#)</span><span class="sxs-lookup"><span data-stu-id="19610-151">Creating XML Trees (C#)</span></span>](./linq-to-xml-overview.md)

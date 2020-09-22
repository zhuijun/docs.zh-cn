---
title: 扩展索引器属性
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
ms.openlocfilehash: 23417cd982c2ddf06afce69d9b120ae0737fb87d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866109"
---
# <a name="extension-indexer-property-visual-basic"></a><span data-ttu-id="d4717-102">扩展索引器属性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4717-102">Extension Indexer Property (Visual Basic)</span></span>

<span data-ttu-id="d4717-103">提供对集合中各个元素的访问。</span><span class="sxs-lookup"><span data-stu-id="d4717-103">Provides access to individual elements in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4717-104">语法</span><span class="sxs-lookup"><span data-stu-id="d4717-104">Syntax</span></span>  
  
```vb  
object(index)  
```  
  
## <a name="parts"></a><span data-ttu-id="d4717-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="d4717-105">Parts</span></span>  
  
|<span data-ttu-id="d4717-106">术语</span><span class="sxs-lookup"><span data-stu-id="d4717-106">Term</span></span>|<span data-ttu-id="d4717-107">定义</span><span class="sxs-lookup"><span data-stu-id="d4717-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="d4717-108">必需。</span><span class="sxs-lookup"><span data-stu-id="d4717-108">Required.</span></span> <span data-ttu-id="d4717-109">可查询的集合。</span><span class="sxs-lookup"><span data-stu-id="d4717-109">A queryable collection.</span></span> <span data-ttu-id="d4717-110">即，实现或的集合 <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Linq.IQueryable%601> 。</span><span class="sxs-lookup"><span data-stu-id="d4717-110">That is, a collection that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>|  
|<span data-ttu-id="d4717-111">(</span><span class="sxs-lookup"><span data-stu-id="d4717-111">(</span></span>|<span data-ttu-id="d4717-112">必需。</span><span class="sxs-lookup"><span data-stu-id="d4717-112">Required.</span></span> <span data-ttu-id="d4717-113">表示索引器属性的开头。</span><span class="sxs-lookup"><span data-stu-id="d4717-113">Denotes the start of the indexer property.</span></span>|  
|`index`|<span data-ttu-id="d4717-114">必需。</span><span class="sxs-lookup"><span data-stu-id="d4717-114">Required.</span></span> <span data-ttu-id="d4717-115">一个整数表达式，指定集合的元素的从零开始的位置。</span><span class="sxs-lookup"><span data-stu-id="d4717-115">An integer expression that specifies the zero-based position of an element of the collection.</span></span>|  
|<span data-ttu-id="d4717-116">)</span><span class="sxs-lookup"><span data-stu-id="d4717-116">)</span></span>|<span data-ttu-id="d4717-117">必需。</span><span class="sxs-lookup"><span data-stu-id="d4717-117">Required.</span></span> <span data-ttu-id="d4717-118">表示索引器属性的结尾。</span><span class="sxs-lookup"><span data-stu-id="d4717-118">Denotes the end of the indexer property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="d4717-119">返回值</span><span class="sxs-lookup"><span data-stu-id="d4717-119">Return Value</span></span>  

 <span data-ttu-id="d4717-120">集合中指定位置的对象; `Nothing` 如果索引超出范围，则为。</span><span class="sxs-lookup"><span data-stu-id="d4717-120">The object from the specified location in the collection, or `Nothing` if the index is out of range.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4717-121">备注</span><span class="sxs-lookup"><span data-stu-id="d4717-121">Remarks</span></span>  

 <span data-ttu-id="d4717-122">可以使用扩展索引器属性访问集合中的单个元素。</span><span class="sxs-lookup"><span data-stu-id="d4717-122">You can use the extension indexer property to access individual elements in a collection.</span></span> <span data-ttu-id="d4717-123">此索引器属性通常用于 XML 轴属性的输出。</span><span class="sxs-lookup"><span data-stu-id="d4717-123">This indexer property is typically used on the output of XML axis properties.</span></span> <span data-ttu-id="d4717-124">XML 子和 XML 子代轴属性返回对象的集合 <xref:System.Xml.Linq.XElement> 或属性值。</span><span class="sxs-lookup"><span data-stu-id="d4717-124">The XML child and XML descendent axis properties return collections of <xref:System.Xml.Linq.XElement> objects or an attribute value.</span></span>  
  
 <span data-ttu-id="d4717-125">Visual Basic 编译器将扩展索引器属性转换为对方法的调用 `ElementAtOrDefault` 。</span><span class="sxs-lookup"><span data-stu-id="d4717-125">The Visual Basic compiler converts extension indexer properties to calls to the `ElementAtOrDefault` method.</span></span> <span data-ttu-id="d4717-126">与数组索引器不同， `ElementAtOrDefault` 如果索引超出范围，则该方法返回 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="d4717-126">Unlike an array indexer, the `ElementAtOrDefault` method returns `Nothing` if the index is out of range.</span></span> <span data-ttu-id="d4717-127">如果无法轻松确定集合中的元素数，则此行为很有用。</span><span class="sxs-lookup"><span data-stu-id="d4717-127">This behavior is useful when you cannot easily determine the number of elements in a collection.</span></span>  
  
 <span data-ttu-id="d4717-128">此索引器属性类似于实现或的集合的扩展 <xref:System.Collections.Generic.IEnumerable%601> 属性 <xref:System.Linq.IQueryable%601> ：只有当集合没有索引器或默认属性时，才使用此属性。</span><span class="sxs-lookup"><span data-stu-id="d4717-128">This indexer property is like an extension property for collections that implement <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>: it is used only if the collection does not have an indexer or a default property.</span></span>  
  
 <span data-ttu-id="d4717-129">若要访问或对象的集合中第一个元素的 <xref:System.Xml.Linq.XElement> 值 <xref:System.Xml.Linq.XAttribute> ，可以使用 XML `Value` 属性。</span><span class="sxs-lookup"><span data-stu-id="d4717-129">To access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, you can use the XML `Value` property.</span></span> <span data-ttu-id="d4717-130">有关详细信息，请参阅 [XML Value 属性](xml-value-property.md)。</span><span class="sxs-lookup"><span data-stu-id="d4717-130">For more information, see [XML Value Property](xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4717-131">示例</span><span class="sxs-lookup"><span data-stu-id="d4717-131">Example</span></span>  

 <span data-ttu-id="d4717-132">下面的示例演示如何使用扩展索引器访问对象集合中的第二个子节点 <xref:System.Xml.Linq.XElement> 。</span><span class="sxs-lookup"><span data-stu-id="d4717-132">The following example shows how to use the extension indexer to access the second child node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="d4717-133">使用子轴属性访问该集合，该属性可获取对象中命名的所有子元素 `phone` `contact` 。</span><span class="sxs-lookup"><span data-stu-id="d4717-133">The collection is accessed by using the child axis property, which gets all child elements named `phone` in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#24)]  
  
 <span data-ttu-id="d4717-134">此代码显示以下文本：</span><span class="sxs-lookup"><span data-stu-id="d4717-134">This code displays the following text:</span></span>  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a><span data-ttu-id="d4717-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d4717-135">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="d4717-136">XML 轴属性</span><span class="sxs-lookup"><span data-stu-id="d4717-136">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="d4717-137">XML 文本</span><span class="sxs-lookup"><span data-stu-id="d4717-137">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="d4717-138">在 Visual Basic 中创建 XML</span><span class="sxs-lookup"><span data-stu-id="d4717-138">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="d4717-139">XML 值属性</span><span class="sxs-lookup"><span data-stu-id="d4717-139">XML Value Property</span></span>](xml-value-property.md)

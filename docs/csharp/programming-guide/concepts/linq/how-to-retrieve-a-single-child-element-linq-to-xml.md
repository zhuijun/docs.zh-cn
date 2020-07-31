---
title: 如何检索单个子元素 (LINQ to XML) (C#)
description: 了解如何使用 LINQ to XML 通过名称检索单个子元素。 在此 C# 示例中，Element 方法返回第一个指定的子元素。
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: c3a044f30cf2e411bdff52586c7a370b626f41bc
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103274"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a><span data-ttu-id="93de0-104">如何检索单个子元素 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="93de0-104">How to retrieve a single child element (LINQ to XML) (C#)</span></span>
<span data-ttu-id="93de0-105">本主题说明如何在给定子元素名称的情况下检索单个子元素。</span><span class="sxs-lookup"><span data-stu-id="93de0-105">This topic explains how to retrieve a single child element, given the name of the child element.</span></span> <span data-ttu-id="93de0-106">如果知道子元素的名称并且只有一个元素具有此名称，则只检索一个元素而不是一个集合会很方便。</span><span class="sxs-lookup"><span data-stu-id="93de0-106">When you know the name of the child element and that there is only one element that has this name, it can be convenient to retrieve just one element, instead of a collection.</span></span>  
  
 <span data-ttu-id="93de0-107"><xref:System.Xml.Linq.XContainer.Element%2A> 方法返回具有指定 <xref:System.Xml.Linq.XElement> 的第一个子 <xref:System.Xml.Linq.XName>。</span><span class="sxs-lookup"><span data-stu-id="93de0-107">The <xref:System.Xml.Linq.XContainer.Element%2A> method returns the first child <xref:System.Xml.Linq.XElement> with the specified <xref:System.Xml.Linq.XName>.</span></span>  
  
 <span data-ttu-id="93de0-108">如果想要在 Visual Basic 中检索单个子元素，常用的方法是使用 XML 属性，然后使用数组索引器表示法检索第一个元素。</span><span class="sxs-lookup"><span data-stu-id="93de0-108">If you want to retrieve a single child element in Visual Basic, a common approach is to use the XML property, and then retrieve the first element using array indexer notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93de0-109">示例</span><span class="sxs-lookup"><span data-stu-id="93de0-109">Example</span></span>  
 <span data-ttu-id="93de0-110">下面的示例演示 <xref:System.Xml.Linq.XContainer.Element%2A> 方法的用法。</span><span class="sxs-lookup"><span data-stu-id="93de0-110">The following example demonstrates the use of the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="93de0-111">本示例采用名为 `po` 的 XML 树并查找名为 `Comment` 的第一个元素。</span><span class="sxs-lookup"><span data-stu-id="93de0-111">This example takes the XML tree named `po` and finds the first element named `Comment`.</span></span>  
  
 <span data-ttu-id="93de0-112">Visual Basic 示例演示如何使用数组索引器表示法来检索单个元素。</span><span class="sxs-lookup"><span data-stu-id="93de0-112">The Visual Basic example shows using array indexer notation to retrieve a single element.</span></span>  
  
 <span data-ttu-id="93de0-113">本示例使用下面的 XML 文档：[示例 XML 文件：典型采购订单 (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) 中所述。</span><span class="sxs-lookup"><span data-stu-id="93de0-113">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
XElement e = po.Element("DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="93de0-114">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="93de0-114">This example produces the following output:</span></span>  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a><span data-ttu-id="93de0-115">示例</span><span class="sxs-lookup"><span data-stu-id="93de0-115">Example</span></span>  
 <span data-ttu-id="93de0-116">下面的示例演示如何对命名空间中的 XML 使用相同的代码。</span><span class="sxs-lookup"><span data-stu-id="93de0-116">The following example shows the same code for XML that is in a namespace.</span></span> <span data-ttu-id="93de0-117">有关详细信息，请参阅[命名空间概述(LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="93de0-117">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="93de0-118">本示例使用下面的 XML 文档：[示例 XML 文件：命名空间中的典型采购单](./sample-xml-file-typical-purchase-order-in-a-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="93de0-118">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement e = po.Element(aw + "DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="93de0-119">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="93de0-119">This example produces the following output:</span></span>  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="93de0-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="93de0-120">See also</span></span>

- [<span data-ttu-id="93de0-121">LINQ to XML 轴 (C#)</span><span class="sxs-lookup"><span data-stu-id="93de0-121">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)

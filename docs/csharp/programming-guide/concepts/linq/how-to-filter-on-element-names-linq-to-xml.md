---
title: 如何筛选元素名称 (LINQ to XML) (C#)
description: 了解如何在调用可返回 XElement 的 IEnumerable 的方法时筛选元素名称。
ms.date: 07/20/2015
ms.assetid: 1849fb03-f075-421f-863c-e8fb32773cdf
ms.openlocfilehash: be660a69b8d860ad907661ce17002379b8842121
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301744"
---
# <a name="how-to-filter-on-element-names-linq-to-xml-c"></a><span data-ttu-id="7c449-103">如何筛选元素名称 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="7c449-103">How to filter on element names (LINQ to XML) (C#)</span></span>
<span data-ttu-id="7c449-104">当调用返回 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement> 的方法之一时，可以根据元素名称进行筛选。</span><span class="sxs-lookup"><span data-stu-id="7c449-104">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c449-105">示例</span><span class="sxs-lookup"><span data-stu-id="7c449-105">Example</span></span>  
 <span data-ttu-id="7c449-106">本示例说明如何检索经过筛选仅包含具有指定名称的子代的集合。</span><span class="sxs-lookup"><span data-stu-id="7c449-106">This example retrieves a collection of descendants that is filtered to contain only descendants with the specified name.</span></span>  
  
 <span data-ttu-id="7c449-107">本示例使用下面的 XML 文档：[示例 XML 文件：典型采购订单 (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)。</span><span class="sxs-lookup"><span data-stu-id="7c449-107">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants("ProductName")  
    select el;  
foreach(XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string) prdName);  
```  
  
 <span data-ttu-id="7c449-108">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="7c449-108">This code produces the following output:</span></span>  
  
```output  
ProductName:Lawnmower  
ProductName:Baby Monitor  
```  
  
 <span data-ttu-id="7c449-109">其他返回 <xref:System.Collections.Generic.IEnumerable%601> 集合的 <xref:System.Xml.Linq.XElement> 的方法都遵循相同的模式。</span><span class="sxs-lookup"><span data-stu-id="7c449-109">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="7c449-110">它们的签名类似于 <xref:System.Xml.Linq.XContainer.Elements%2A> 和 <xref:System.Xml.Linq.XContainer.Descendants%2A>。</span><span class="sxs-lookup"><span data-stu-id="7c449-110">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="7c449-111">以下是具有相似方法签名的完整方法列表：</span><span class="sxs-lookup"><span data-stu-id="7c449-111">The following is the complete list of methods that have similar method signatures:</span></span>  
  
- <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
- <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
- <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a><span data-ttu-id="7c449-112">示例</span><span class="sxs-lookup"><span data-stu-id="7c449-112">Example</span></span>  
 <span data-ttu-id="7c449-113">下面的示例演示如何对命名空间中的 XML 进行同样的查询。</span><span class="sxs-lookup"><span data-stu-id="7c449-113">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="7c449-114">有关详细信息，请参阅[命名空间概述(LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="7c449-114">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="7c449-115">本示例使用下面的 XML 文档：[示例 XML 文件：命名空间中的典型采购单](./sample-xml-file-typical-purchase-order-in-a-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="7c449-115">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants(aw + "ProductName")  
    select el;  
foreach (XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string)prdName);  
```  
  
 <span data-ttu-id="7c449-116">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="7c449-116">This code produces the following output:</span></span>  
  
```output  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a><span data-ttu-id="7c449-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="7c449-117">See also</span></span>

- [<span data-ttu-id="7c449-118">LINQ to XML 轴 (C#)</span><span class="sxs-lookup"><span data-stu-id="7c449-118">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)

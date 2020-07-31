---
title: 如何检索元素集合 (LINQ to XML) (C#)
description: C# 中的 Elements 方法检索元素的子元素集合。 本 LINQ to XML 示例循环访问元素的子元素。
ms.date: 07/20/2015
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: 4f9b6ae4713af9ce1a4eeb5257f57cd9724f68b2
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103354"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a><span data-ttu-id="c65ce-104">如何检索元素集合 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c65ce-104">How to retrieve a collection of elements (LINQ to XML) (C#)</span></span>
<span data-ttu-id="c65ce-105">本主题演示 <xref:System.Xml.Linq.XContainer.Elements%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="c65ce-105">This topic demonstrates the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span> <span data-ttu-id="c65ce-106">此方法检索元素的子元素集合。</span><span class="sxs-lookup"><span data-stu-id="c65ce-106">This method retrieves a collection of the child elements of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c65ce-107">示例</span><span class="sxs-lookup"><span data-stu-id="c65ce-107">Example</span></span>  
 <span data-ttu-id="c65ce-108">本示例循环访问 `purchaseOrder` 元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="c65ce-108">This example iterates through the child elements of the `purchaseOrder` element.</span></span>  
  
 <span data-ttu-id="c65ce-109">本示例使用下面的 XML 文档：[示例 XML 文件：典型采购订单 (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) 中所述。</span><span class="sxs-lookup"><span data-stu-id="c65ce-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> childElements =  
    from el in po.Elements()  
    select el;  
foreach (XElement el in childElements)  
    Console.WriteLine("Name: " + el.Name);  
```  
  
 <span data-ttu-id="c65ce-110">本示例生成以下输出。</span><span class="sxs-lookup"><span data-stu-id="c65ce-110">This example produces the following output.</span></span>  
  
```output  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a><span data-ttu-id="c65ce-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="c65ce-111">See also</span></span>

- [<span data-ttu-id="c65ce-112">LINQ to XML 轴 (C#)</span><span class="sxs-lookup"><span data-stu-id="c65ce-112">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)

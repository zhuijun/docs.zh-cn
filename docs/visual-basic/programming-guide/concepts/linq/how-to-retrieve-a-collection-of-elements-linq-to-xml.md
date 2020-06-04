---
title: 如何：检索元素集合 (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 2269f9de-8fb9-4666-b8a1-a4e754fa6a81
ms.openlocfilehash: 13aa9ce10df1e23ba5191b523db0272aa52ea581
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397864"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-visual-basic"></a><span data-ttu-id="19cf9-102">如何：检索元素集合（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="19cf9-102">How to: Retrieve a Collection of Elements (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="19cf9-103">本主题演示 <xref:System.Xml.Linq.XContainer.Elements%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="19cf9-103">This topic demonstrates the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span> <span data-ttu-id="19cf9-104">此方法检索元素的子元素集合。</span><span class="sxs-lookup"><span data-stu-id="19cf9-104">This method retrieves a collection of the child elements of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19cf9-105">示例</span><span class="sxs-lookup"><span data-stu-id="19cf9-105">Example</span></span>  
 <span data-ttu-id="19cf9-106">本示例循环访问 `purchaseOrder` 元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="19cf9-106">This example iterates through the child elements of the `purchaseOrder` element.</span></span>  
  
 <span data-ttu-id="19cf9-107">本示例使用以下 XML 文档：[示例 XML 文件：典型采购订单 (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="19cf9-107">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim childElements As IEnumerable(Of XElement)  
childElements = _  
    From el In po.Elements() _  
    Select el  
For Each el As XElement In childElements  
    Console.WriteLine("Name: " & el.Name.ToString())  
Next  
```  
  
 <span data-ttu-id="19cf9-108">本示例生成以下输出。</span><span class="sxs-lookup"><span data-stu-id="19cf9-108">This example produces the following output.</span></span>  
  
```console  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a><span data-ttu-id="19cf9-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="19cf9-109">See also</span></span>

- [<span data-ttu-id="19cf9-110">LINQ to XML 轴 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19cf9-110">LINQ to XML Axes (Visual Basic)</span></span>](linq-to-xml-axes.md)

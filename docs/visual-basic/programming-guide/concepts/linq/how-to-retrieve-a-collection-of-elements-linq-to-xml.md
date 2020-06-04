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
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-visual-basic"></a>如何：检索元素集合（LINQ to XML）（Visual Basic）
本主题演示 <xref:System.Xml.Linq.XContainer.Elements%2A> 方法。 此方法检索元素的子元素集合。  
  
## <a name="example"></a>示例  
 本示例循环访问 `purchaseOrder` 元素的子元素。  
  
 本示例使用以下 XML 文档：[示例 XML 文件：典型采购订单 (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md)。  
  
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
  
 本示例生成以下输出。  
  
```console  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a>另请参阅

- [LINQ to XML 轴 (Visual Basic)](linq-to-xml-axes.md)

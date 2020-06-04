---
title: 如何：编写使用复杂筛选的查询
ms.date: 07/20/2015
ms.assetid: bf286ffc-7990-4b00-a4eb-ee3d70129950
ms.openlocfilehash: 18ed4379b7ec9c8007cc3c189fc45571b5161911
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397617"
---
# <a name="how-to-write-queries-with-complex-filtering-visual-basic"></a>如何：编写具有复杂筛选的查询（Visual Basic）
有时，您需要编写使用复杂筛选器的 LINQ to XML 查询。 例如，您可能必须查找其子元素具有特定名称和值的所有元素。 本主题提供一个编写使用复杂筛选的查询的示例。  
  
## <a name="example"></a>示例  
 本示例演示如何查找具有 `PurchaseOrder` 属性等于“Shipping”的子 `Address` 元素和等于“NY”的子 `Type` 元素的所有 `State` 元素。 示例在 `Where` 子句中使用嵌套查询，如果集合中有任何元素，则 `Any` 运算符返回 `True`。  
  
 本示例使用以下 XML 文档：[示例 XML 文件：多个采购订单 (LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。  
  
 有关运算符的详细信息 `Any` ，请参阅[限定符运算（Visual Basic）](quantifier-operations.md)。  
  
```vb  
Dim root As XElement = XElement.Load("PurchaseOrders.xml")  
Dim purchaseOrders As IEnumerable(Of XElement) = _  
    From el In root.<PurchaseOrder> _  
    Where _  
        (From add In el.<Address> _  
        Where _  
             add.@Type = "Shipping" And _  
             add.<State>.Value = "NY" _  
        Select add) _  
    .Any() _  
    Select el  
For Each el As XElement In purchaseOrders  
    Console.WriteLine(el.@PurchaseOrderNumber)  
Next  
```  
  
 此代码生成以下输出：  
  
```console  
99505  
```  
  
## <a name="example"></a>示例  
 下面的示例演示如何对命名空间中的 XML 进行同样的查询。 有关详细信息，请参阅[命名空间概述（LINQ to XML）（Visual Basic）](namespaces-overview-linq-to-xml.md)。  
  
 本示例使用以下 XML 文档：[示例 XML 文件：命名空间中的多个采购订单](sample-xml-file-multiple-purchase-orders-in-a-namespace.md)。  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")  
        Dim purchaseOrders As IEnumerable(Of XElement) = _  
            From el In root.<aw:PurchaseOrder> _  
            Where _  
                (From add In el.<aw:Address> _  
                Where _  
                     add.@aw:Type = "Shipping" And _  
                     add.<aw:State>.Value = "NY" _  
                Select add) _  
            .Any() _  
            Select el  
        For Each el As XElement In purchaseOrders  
            Console.WriteLine(el.@aw:PurchaseOrderNumber)  
        Next  
    End Sub  
End Module  
```  
  
 此代码生成以下输出：  
  
```console  
99505  
```  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [基本查询（LINQ to XML）（Visual Basic）](basic-queries-linq-to-xml.md)
- [XML Child Axis Property](../../../language-reference/xml-axis/xml-child-axis-property.md)
- [XML Attribute Axis Property](../../../language-reference/xml-axis/xml-attribute-axis-property.md)
- [XML 值属性](../../../language-reference/xml-axis/xml-value-property.md)
- [投影操作（Visual Basic）](projection-operations.md)
- [限定符运算（Visual Basic）](quantifier-operations.md)

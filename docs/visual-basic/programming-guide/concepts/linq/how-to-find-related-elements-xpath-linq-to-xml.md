---
title: 如何：查找相关元素 (XPath-LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 6b0ef058-d704-48a5-98cd-33f00d088af9
ms.openlocfilehash: 5819ef216f767367aa16b20f818b2bbc537d54b7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364651"
---
# <a name="how-to-find-related-elements-xpath-linq-to-xml-visual-basic"></a>如何：查找相关元素（XPath LINQ to XML）（Visual Basic）
本主题演示如何在由其他元素的值所引用的属性上获取元素选择。  
  
 XPath 表达式为：  
  
 `.//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]`  
  
## <a name="example"></a>示例  
 本示例查找第 12 个 `Order` 元素，然后查找该订单的客户。  
  
 请注意，在 .NET 中，列表索引是从零开始编制。 在 XPath 谓词中，对节点集合的索引是从 1 开始的。 本示例反映了这种差别。  
  
 本示例使用下面的 XML 文档：[示例 XML 文件：客户和订单 (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md)。  
  
```vb  
Dim co As XDocument = XDocument.Load("CustomersOrders.xml")  
  
' LINQ to XML query  
Dim customer1 As XElement = ( _  
    From el In co...<Customer> _  
    Where el.@CustomerID = co.<Root>.<Orders>.<Order>. _  
        ToList()(11).<CustomerID>(0).Value _  
    Select el).First()  
  
' An alternate way to write the query that avoids creation  
' of a System.Collections.Generic.List:  
Dim customer2 As XElement = ( _  
    From el In co...<Customer> _  
    Where el.@CustomerID = co.<Root>.<Orders>.<Order>. _  
        Skip(11).First().<CustomerID>(0).Value _  
    Select el).First()  
  
' XPath expression  
Dim customer3 As XElement = co.XPathSelectElement _  
    (".//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]")  
  
If customer1 Is customer2 And customer1 Is customer3 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(customer1)  
```  
  
 该示例产生下面的输出：  
  
```console
Results are identical  
<Customer CustomerID="HUNGC">  
  <CompanyName>Hungry Coyote Import Store</CompanyName>  
  <ContactName>Yoshi Latimer</ContactName>  
  <ContactTitle>Sales Representative</ContactTitle>  
  <Phone>(503) 555-6874</Phone>  
  <Fax>(503) 555-2376</Fax>  
  <FullAddress>  
    <Address>City Center Plaza 516 Main St.</Address>  
    <City>Elgin</City>  
    <Region>OR</Region>  
    <PostalCode>97827</PostalCode>  
    <Country>USA</Country>  
  </FullAddress>  
</Customer>  
```  
  
## <a name="see-also"></a>请参阅

- [XPath 用户的 LINQ to XML （Visual Basic）](linq-to-xml-for-xpath-users.md)

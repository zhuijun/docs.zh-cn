---
title: 如何：投影匿名类型
ms.date: 07/20/2015
ms.assetid: 30b42987-0e0e-4b2b-adb1-5255ddfbcd7b
ms.openlocfilehash: c486fbd7ee8ae917cd0ccf57e2b04e472784b11d
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88810555"
---
# <a name="how-to-project-an-anonymous-type-visual-basic"></a>如何：投影匿名类型 (Visual Basic) 
在某些情况下，您可能需要将查询投影到新类型，即使您知道只是短时间使用此类型。 创建仅在投影中使用的新类型需要大量额外工作。 在这种情况下，一种更有效的方法是投影到匿名类型。 匿名类型允许您定义一个类，然后在不给出类名称的情况下声明并初始化该类的对象。  
  
 匿名类型是“元组”这一数学概念的 C# 实现。 数学术语元组源自序列单元组、双元组、三元组、四元组、五元组和 n 元组。 它指有限的对象序列，每个对象具有特定的类型。 有时，它称为名称/值对的列表。 例如，[示例 XML 文件：典型采购订单 (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md) XML 文档中某一地址的内容可表示为如下形式：  
  
```
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 在创建匿名类型的实例时，可以将其想像为创建 n 阶元组。 如果编写一个将在 `Select` 子句中创建元组的查询，该查询将返回该元组的一个 `IEnumerable`。  
  
## <a name="example"></a>示例  
 在此示例中，`Select` 子句投影一个匿名类型。 然后，示例使用 `Dim` 创建 `IEnumerable` 对象。 在 `For Each` 循环中，该迭代变量成为在查询表达式中创建的匿名类型的实例。  
  
 本示例使用下面的 XML 文档：[示例 XML 文件：客户和订单 (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md) 的架构定义。  
  
```vb  
Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")  
Dim custList = _  
    From el In custOrd.<Customers>.<Customer> _  
    Select New With { _  
        .CustomerID = el.@<CustomerID>, _  
        .CompanyName = el.<CompanyName>.Value, _  
        .ContactName = el.<ContactName>.Value _  
    }  
For Each cust In custList  
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName)  
Next  
```  
  
 此代码生成以下输出：  
  
```console  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a>另请参阅

- [投影和转换 (LINQ to XML)  (Visual Basic) ](projections-and-transformations-linq-to-xml.md)

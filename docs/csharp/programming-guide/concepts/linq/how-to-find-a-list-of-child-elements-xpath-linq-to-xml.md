---
title: 如何查找子元素的列表 (XPath-LINQ to XML) (C#)
description: 了解如何使用 XPath 表达式查找子元素的列表。 查看用于查找特定元素的所有子元素的代码示例。
ms.date: 07/20/2015
ms.assetid: 7c589dd8-f680-4cdb-9d6a-78d57e2555e8
ms.openlocfilehash: a3025aca7fb1055acd55e5ce98914d8359ebe4b7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301718"
---
# <a name="how-to-find-a-list-of-child-elements-xpath-linq-to-xml-c"></a>如何查找子元素的列表 (XPath-LINQ to XML) (C#)
本主题将 XPath 子元素轴与 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> 轴进行比较。  
  
 XPath 表达式为：`./*`  
  
## <a name="example"></a>示例  
 本示例查找 `Address` 元素的所有子元素。  
  
 本示例使用下面的 XML 文档：[示例 XML 文件：多个采购订单 (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。  
  
```csharp  
XDocument cpo = XDocument.Load("PurchaseOrders.xml");  
XElement po = cpo.Root.Element("PurchaseOrder").Element("Address");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 = po.Elements();  
  
// XPath expression  
IEnumerable<XElement> list2 = po.XPathSelectElements("./*");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 该示例产生下面的输出：  
  
```output  
Results are identical  
<Name>Ellen Adams</Name>  
<Street>123 Maple Street</Street>  
<City>Mill Valley</City>  
<State>CA</State>  
<Zip>10999</Zip>  
<Country>USA</Country>  
```  

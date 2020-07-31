---
title: 如何查找根元素 (XPath-LINQ to XML) (C#)
description: 此 C# 示例比较了 XPath 和 LINQ to XML，以了解如何获取示例 XML 文档的根元素。
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: 220899823210c5cd6e9834541ca87e4d8394b4ff
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105195"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a>如何查找根元素 (XPath-LINQ to XML) (C#)
本主题演示如何使用 XPath 和 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 获取根元素。  
  
 XPath 表达式为：  
  
 `/PurchaseOrders`  
  
## <a name="example"></a>示例  
 此示例查找根元素。  
  
 本示例使用下面的 XML 文档：[示例 XML 文件：多个采购订单 (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
// LINQ to XML query  
XElement el1 = po.Root;  
  
// XPath expression  
XElement el2 = po.XPathSelectElement("/PurchaseOrders");  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1.Name);  
```  
  
 该示例产生下面的输出：  
  
```output  
Results are identical  
PurchaseOrders  
```  

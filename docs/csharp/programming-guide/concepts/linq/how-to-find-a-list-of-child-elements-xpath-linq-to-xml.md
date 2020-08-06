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
# <a name="how-to-find-a-list-of-child-elements-xpath-linq-to-xml-c"></a><span data-ttu-id="e4909-104">如何查找子元素的列表 (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e4909-104">How to find a list of child elements (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="e4909-105">本主题将 XPath 子元素轴与 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> 轴进行比较。</span><span class="sxs-lookup"><span data-stu-id="e4909-105">This topic compares the XPath child elements axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span>  
  
 <span data-ttu-id="e4909-106">XPath 表达式为：`./*`</span><span class="sxs-lookup"><span data-stu-id="e4909-106">The XPath expression is: `./*`</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4909-107">示例</span><span class="sxs-lookup"><span data-stu-id="e4909-107">Example</span></span>  
 <span data-ttu-id="e4909-108">本示例查找 `Address` 元素的所有子元素。</span><span class="sxs-lookup"><span data-stu-id="e4909-108">This example finds all of the child elements of the `Address` element.</span></span>  
  
 <span data-ttu-id="e4909-109">本示例使用下面的 XML 文档：[示例 XML 文件：多个采购订单 (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="e4909-109">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="e4909-110">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="e4909-110">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<Name>Ellen Adams</Name>  
<Street>123 Maple Street</Street>  
<City>Mill Valley</City>  
<State>CA</State>  
<Zip>10999</Zip>  
<Country>USA</Country>  
```  

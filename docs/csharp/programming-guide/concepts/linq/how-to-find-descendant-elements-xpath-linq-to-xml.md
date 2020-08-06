---
title: 如何查找子代元素 (XPath-LINQ to XML) (C#)
description: 了解如何使用 XPath 表达式查找具有特定名称的子代元素。 查看使用示例 XML 文件的代码示例。
ms.date: 07/20/2015
ms.assetid: b318da39-bb8b-4c56-a019-e13b12b01831
ms.openlocfilehash: c5a998a05f866203f3b684b8847a4a5647c12e5b
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303265"
---
# <a name="how-to-find-descendant-elements-xpath-linq-to-xml-c"></a><span data-ttu-id="5b5ae-104">如何查找子代元素 (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="5b5ae-104">How to find descendant elements (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="5b5ae-105">本主题演示如何获取具有特定名称的后代元素。</span><span class="sxs-lookup"><span data-stu-id="5b5ae-105">This topic shows how to get the descendant elements with a particular name.</span></span>  
  
 <span data-ttu-id="5b5ae-106">XPath 表达式为 `//Name`。</span><span class="sxs-lookup"><span data-stu-id="5b5ae-106">The XPath expression is `//Name`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b5ae-107">示例</span><span class="sxs-lookup"><span data-stu-id="5b5ae-107">Example</span></span>  
 <span data-ttu-id="5b5ae-108">本示例查找名为 `Name` 的所有后代。</span><span class="sxs-lookup"><span data-stu-id="5b5ae-108">This example finds all descendants named `Name`.</span></span>  
  
 <span data-ttu-id="5b5ae-109">本示例使用下面的 XML 文档：[示例 XML 文件：多个采购订单 (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="5b5ae-109">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 = po.Root.Descendants("Name");  
  
// XPath expression  
IEnumerable<XElement> list2 = po.XPathSelectElements("//Name");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="5b5ae-110">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="5b5ae-110">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  

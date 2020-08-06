---
title: 如何查找子元素 (XPath-LINQ to XML) (C#)
description: 了解如何通过将 XPath 子元素轴与 LINQ to XML 元素方法进行比较，来查找子元素。
ms.date: 07/20/2015
ms.assetid: 4fa6182d-6196-4ed1-9c9e-82949ff89c71
ms.openlocfilehash: 57d1a4e636e3443512020129a76cc2de7bb3f244
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301731"
---
# <a name="how-to-find-a-child-element-xpath-linq-to-xml-c"></a><span data-ttu-id="85097-103">如何查找子元素 (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="85097-103">How to find a child element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="85097-104">本主题将 XPath 子元素轴与 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> 方法进行比较。</span><span class="sxs-lookup"><span data-stu-id="85097-104">This topic compares the XPath child element axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  
  
 <span data-ttu-id="85097-105">XPath 表达式为 `DeliveryNotes`。</span><span class="sxs-lookup"><span data-stu-id="85097-105">The XPath expression is `DeliveryNotes`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85097-106">示例</span><span class="sxs-lookup"><span data-stu-id="85097-106">Example</span></span>  
 <span data-ttu-id="85097-107">本示例查找子元素 `DeliveryNotes`。</span><span class="sxs-lookup"><span data-stu-id="85097-107">This example finds the child element `DeliveryNotes`.</span></span>  
  
 <span data-ttu-id="85097-108">本示例使用下面的 XML 文档：[示例 XML 文件：多个采购订单 (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="85097-108">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument cpo = XDocument.Load("PurchaseOrders.xml");  
XElement po = cpo.Root.Element("PurchaseOrder");  
  
// LINQ to XML query  
XElement el1 = po.Element("DeliveryNotes");  
  
// XPath expression  
XElement el2 = po.XPathSelectElement("DeliveryNotes");  
// same as "child::DeliveryNotes"  
// same as "./DeliveryNotes"  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1);  
```  
  
 <span data-ttu-id="85097-109">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="85097-109">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
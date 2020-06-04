---
title: 如何：查找子元素列表 (XPath-LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 2868abfd-9f7b-412a-9cb5-f643f0fed146
ms.openlocfilehash: d03b89f93fede3abd2d482c01979e93876d60c0b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410768"
---
# <a name="how-to-find-a-list-of-child-elements-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="b02ba-102">如何：查找子元素的列表（XPath LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="b02ba-102">How to: Find a List of Child Elements (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="b02ba-103">本主题将 XPath 子元素轴与 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> 轴进行比较。</span><span class="sxs-lookup"><span data-stu-id="b02ba-103">This topic compares the XPath child elements axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span>  
  
 <span data-ttu-id="b02ba-104">XPath 表达式为：`./*`</span><span class="sxs-lookup"><span data-stu-id="b02ba-104">The XPath expression is: `./*`</span></span>  
  
## <a name="example"></a><span data-ttu-id="b02ba-105">示例</span><span class="sxs-lookup"><span data-stu-id="b02ba-105">Example</span></span>  
 <span data-ttu-id="b02ba-106">本示例查找 `Address` 元素的所有子元素。</span><span class="sxs-lookup"><span data-stu-id="b02ba-106">This example finds all of the child elements of the `Address` element.</span></span>  
  
 <span data-ttu-id="b02ba-107">本示例使用下面的 XML 文档：[示例 XML 文件：多个采购订单 (LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="b02ba-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim cpo As XDocument = XDocument.Load("PurchaseOrders.xml")  
Dim po As XElement = cpo.Root.<PurchaseOrder>.<Address>.FirstOrDefault  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = po.Elements()  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = po.XPathSelectElements("./*")  
  
If (list1.Count() = list2.Count()) AndAlso _  
    (list1.Intersect(list2).Count() = list1.Count()) Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="b02ba-108">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="b02ba-108">This example produces the following output:</span></span>  
  
```console
Results are identical  
<Name>Ellen Adams</Name>  
<Street>123 Maple Street</Street>  
<City>Mill Valley</City>  
<State>CA</State>  
<Zip>10999</Zip>  
<Country>USA</Country>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b02ba-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="b02ba-109">See also</span></span>

- [<span data-ttu-id="b02ba-110">XPath 用户的 LINQ to XML （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="b02ba-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)

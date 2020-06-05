---
title: 如何：查找两个位置路径的联合 (XPath-LINQ to XML)
ms.date: 07/20/2015
ms.assetid: c82c09b4-cb0a-47ec-8cc3-a124144c2788
ms.openlocfilehash: 36528d1748d5675231f14de92dcd78734a696711
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406867"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="27a77-102">如何：查找两个位置路径的并集（XPath LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="27a77-102">How to: Find a Union of Two Location Paths (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="27a77-103">使用 XPath 可以查找两个 XPath 位置路径结果的联合。</span><span class="sxs-lookup"><span data-stu-id="27a77-103">XPath allows you to find the union of the results of two XPath location paths.</span></span>  
  
 <span data-ttu-id="27a77-104">XPath 表达式为：</span><span class="sxs-lookup"><span data-stu-id="27a77-104">The XPath expression is:</span></span>  
  
 `//Category|//Price`  
  
 <span data-ttu-id="27a77-105">通过使用 <xref:System.Linq.Enumerable.Concat%2A> 标准查询运算符可以获得相同的结果。</span><span class="sxs-lookup"><span data-stu-id="27a77-105">You can achieve the same results by using the <xref:System.Linq.Enumerable.Concat%2A> standard query operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27a77-106">示例</span><span class="sxs-lookup"><span data-stu-id="27a77-106">Example</span></span>  
 <span data-ttu-id="27a77-107">本示例查找所有 `Category` 元素和所有 `Price` 元素，并将它们连接到单个集合中。</span><span class="sxs-lookup"><span data-stu-id="27a77-107">This example finds all of the `Category` elements and all of the `Price` elements, and concatenates them into a single collection.</span></span> <span data-ttu-id="27a77-108">请注意，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查询会调用 <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> 以对结果进行排序。</span><span class="sxs-lookup"><span data-stu-id="27a77-108">Note that the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to order the results.</span></span> <span data-ttu-id="27a77-109">XPath 表达式的计算结果也按文档顺序排列。</span><span class="sxs-lookup"><span data-stu-id="27a77-109">The results of the XPath expression evaluation are also in document order.</span></span>  
  
 <span data-ttu-id="27a77-110">本示例使用下面的 XML 文档：[示例 XML 文件：数值数据 (LINQ to XML)](sample-xml-file-numerical-data-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="27a77-110">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```vb  
Dim data As XDocument = XDocument.Load("Data.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    data...<Category>.Concat(data...<Price>).InDocumentOrder()  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = _  
    data.XPathSelectElements("//Category|//Price")  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="27a77-111">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="27a77-111">This example produces the following output:</span></span>  
  
```console
Results are identical  
<Category>A</Category>  
<Price>24.50</Price>  
<Category>B</Category>  
<Price>89.99</Price>  
<Category>A</Category>  
<Price>4.95</Price>  
<Category>A</Category>  
<Price>66.00</Price>  
<Category>B</Category>  
<Price>.99</Price>  
<Category>A</Category>  
<Price>29.00</Price>  
<Category>B</Category>  
<Price>6.99</Price>  
```  
  
## <a name="see-also"></a><span data-ttu-id="27a77-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="27a77-112">See also</span></span>

- [<span data-ttu-id="27a77-113">XPath 用户的 LINQ to XML （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="27a77-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)

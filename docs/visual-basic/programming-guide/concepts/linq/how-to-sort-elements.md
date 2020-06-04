---
title: 如何：对元素进行排序
ms.date: 07/20/2015
ms.assetid: c2c09279-6c8a-482e-8e71-b1453a815052
ms.openlocfilehash: 1204fb4dc190d68956d01ffce225ce40e11538a4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397747"
---
# <a name="how-to-sort-elements-visual-basic"></a><span data-ttu-id="cc4b4-102">如何：对元素进行排序（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="cc4b4-102">How to: Sort Elements (Visual Basic)</span></span>
<span data-ttu-id="cc4b4-103">本示例演示如何编写对查询结果进行排序的查询。</span><span class="sxs-lookup"><span data-stu-id="cc4b4-103">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc4b4-104">示例</span><span class="sxs-lookup"><span data-stu-id="cc4b4-104">Example</span></span>  
 <span data-ttu-id="cc4b4-105">本示例使用下面的 XML 文档：[示例 XML 文件：数值数据 (LINQ to XML)](sample-xml-file-numerical-data-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="cc4b4-105">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
Dim prices As IEnumerable(Of Decimal) = _  
    From el In root.<Data> _  
    Let price = Convert.ToDecimal(el.<Price>.Value) _  
    Order By (price) _  
    Select price  
For Each el As Decimal In prices  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="cc4b4-106">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="cc4b4-106">This code produces the following output:</span></span>  
  
```console  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="cc4b4-107">示例</span><span class="sxs-lookup"><span data-stu-id="cc4b4-107">Example</span></span>  
 <span data-ttu-id="cc4b4-108">下面的示例演示如何对命名空间中的 XML 进行同样的查询。</span><span class="sxs-lookup"><span data-stu-id="cc4b4-108">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="cc4b4-109">有关详细信息，请参阅[命名空间概述（LINQ to XML）（Visual Basic）](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="cc4b4-109">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="cc4b4-110">本示例使用下面的 XML 文档：[示例 XML 文件：命名空间中的数值数据](sample-xml-file-numerical-data-in-a-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="cc4b4-110">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("DataInNamespace.xml")  
        Dim prices As IEnumerable(Of Decimal) = _  
            From el In root.<Data> _  
            Let price = Convert.ToDecimal(el.<Price>.Value) _  
            Order By (price) _  
            Select price  
        For Each el As Decimal In prices  
            Console.WriteLine(el)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="cc4b4-111">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="cc4b4-111">This code produces the following output:</span></span>  
  
```console  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="cc4b4-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cc4b4-112">See also</span></span>

- [<span data-ttu-id="cc4b4-113">对数据进行排序</span><span class="sxs-lookup"><span data-stu-id="cc4b4-113">Sorting Data</span></span>](sorting-data.md)
- [<span data-ttu-id="cc4b4-114">基本查询（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="cc4b4-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](basic-queries-linq-to-xml.md)

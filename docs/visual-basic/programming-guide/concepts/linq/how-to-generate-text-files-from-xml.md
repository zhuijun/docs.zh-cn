---
title: 如何：从 XML 生成文本文件
ms.date: 07/20/2015
ms.assetid: 3b33f191-4abe-4419-b81b-3cb81d9a317f
ms.openlocfilehash: 9d89d8d5e929574fa26cc5c11346980e8b235ac5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396566"
---
# <a name="how-to-generate-text-files-from-xml-visual-basic"></a><span data-ttu-id="cbb19-102">如何：从 XML 生成文本文件（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="cbb19-102">How to: Generate Text Files from XML (Visual Basic)</span></span>
<span data-ttu-id="cbb19-103">本示例演示如何从 XML 文件生成逗号分隔值 (CSV) 文件。</span><span class="sxs-lookup"><span data-stu-id="cbb19-103">This example shows how to generate a comma-separated values (CSV) file from an XML file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbb19-104">示例</span><span class="sxs-lookup"><span data-stu-id="cbb19-104">Example</span></span>  
 <span data-ttu-id="cbb19-105">Visual Basic 版本使用过程代码将字符串集合聚合为一个字符串。</span><span class="sxs-lookup"><span data-stu-id="cbb19-105">The Visual Basic version uses procedural code to aggregate the collection of strings into a single string.</span></span>  
  
 <span data-ttu-id="cbb19-106">本示例使用下面的 XML 文档：[示例 XML 文件：客户和订单 (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="cbb19-106">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")  
Dim strCollection As IEnumerable(Of String) = _  
    From el In custOrd.<Customers>.<Customer> _  
    Select _  
        String.Format("{0},{1},{2},{3},{4},{5},{6},{7},{8},{9}{10}", _  
            el.@CustomerID, _  
            el.<CompanyName>.Value, _  
            el.<ContactName>.Value, _  
            el.<ContactTitle>.Value, _  
            el.<Phone>.Value, _  
            el.<FullAddress>.<Address>.Value, _  
            el.<FullAddress>.<City>.Value, _  
            el.<FullAddress>.<Region>.Value, _  
            el.<FullAddress>.<PostalCode>.Value, _  
            el.<FullAddress>.<Country>.Value, _  
            Environment.NewLine _  
        )  
Dim sb As StringBuilder = New StringBuilder()  
For Each str As String In strCollection  
    sb.Append(str)  
Next  
Console.WriteLine(sb.ToString())  
```  
  
 <span data-ttu-id="cbb19-107">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="cbb19-107">This code produces the following output:</span></span>  
  
```console  
GREAL,Great Lakes Food Market,Howard Snyder,Marketing Manager,(503) 555-7555,2732 Baker Blvd.,Eugene,OR,97403,USA  
HUNGC,Hungry Coyote Import Store,Yoshi Latimer,Sales Representative,(503) 555-6874,City Center Plaza 516 Main St.,Elgin,OR,97827,USA  
LAZYK,Lazy K Kountry Store,John Steel,Marketing Manager,(509) 555-7969,12 Orchestra Terrace,Walla Walla,WA,99362,USA  
LETSS,Let's Stop N Shop,Jaime Yorres,Owner,(415) 555-5938,87 Polk St. Suite 5,San Francisco,CA,94117,USA  
```  
  
## <a name="see-also"></a><span data-ttu-id="cbb19-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cbb19-108">See also</span></span>

- [<span data-ttu-id="cbb19-109">投影和转换（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="cbb19-109">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](projections-and-transformations-linq-to-xml.md)

---
title: 如何查找两个位置路径的并集 (XPath-LINQ to XML) (C#)
description: 了解如何使用 XPath 表达式查找两个 XPath 位置路径的并集。 查看使用示例 XML 文件的代码示例。
ms.date: 07/20/2015
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: 65b20fe25a0990fd82ce3bd08c3433499e728512
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303317"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-c"></a><span data-ttu-id="c1a9f-104">如何查找两个位置路径的并集 (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c1a9f-104">How to find a union of two location paths (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="c1a9f-105">使用 XPath 可以查找两个 XPath 位置路径结果的联合。</span><span class="sxs-lookup"><span data-stu-id="c1a9f-105">XPath allows you to find the union of the results of two XPath location paths.</span></span>  
  
 <span data-ttu-id="c1a9f-106">XPath 表达式为：</span><span class="sxs-lookup"><span data-stu-id="c1a9f-106">The XPath expression is:</span></span>  
  
 `//Category|//Price`  
  
 <span data-ttu-id="c1a9f-107">通过使用 <xref:System.Linq.Enumerable.Concat%2A> 标准查询运算符可以获得相同的结果。</span><span class="sxs-lookup"><span data-stu-id="c1a9f-107">You can achieve the same results by using the <xref:System.Linq.Enumerable.Concat%2A> standard query operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1a9f-108">示例</span><span class="sxs-lookup"><span data-stu-id="c1a9f-108">Example</span></span>  
 <span data-ttu-id="c1a9f-109">本示例查找所有 `Category` 元素和所有 `Price` 元素，并将它们连接到单个集合中。</span><span class="sxs-lookup"><span data-stu-id="c1a9f-109">This example finds all of the `Category` elements and all of the `Price` elements, and concatenates them into a single collection.</span></span> <span data-ttu-id="c1a9f-110">请注意，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查询会调用 <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> 以对结果进行排序。</span><span class="sxs-lookup"><span data-stu-id="c1a9f-110">Note that the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to order the results.</span></span> <span data-ttu-id="c1a9f-111">XPath 表达式的计算结果也按文档顺序排列。</span><span class="sxs-lookup"><span data-stu-id="c1a9f-111">The results of the XPath expression evaluation are also in document order.</span></span>  
  
 <span data-ttu-id="c1a9f-112">本示例使用下面的 XML 文档：[示例 XML 文件：数值数据 (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="c1a9f-112">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument data = XDocument.Load("Data.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    data  
    .Descendants("Category")  
    .Concat(  
        data  
        .Descendants("Price")  
    )  
    .InDocumentOrder();  
  
// XPath expression  
IEnumerable<XElement> list2 = data.XPathSelectElements("//Category|//Price");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="c1a9f-113">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="c1a9f-113">This example produces the following output:</span></span>  
  
```output  
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
  
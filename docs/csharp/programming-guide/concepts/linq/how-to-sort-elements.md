---
title: 如何对元素进行排序 (C#)
description: 了解如何对元素进行排序。 参阅示例，了解如何编写对 XML 文档中的结果进行排序的查询。
ms.date: 07/20/2015
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: 669d9cf583e6ab70c93be39ad271eaf104f88718
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301432"
---
# <a name="how-to-sort-elements-c"></a><span data-ttu-id="18f9b-104">如何对元素进行排序 (C#)</span><span class="sxs-lookup"><span data-stu-id="18f9b-104">How to sort elements (C#)</span></span>
<span data-ttu-id="18f9b-105">本示例演示如何编写对查询结果进行排序的查询。</span><span class="sxs-lookup"><span data-stu-id="18f9b-105">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18f9b-106">示例</span><span class="sxs-lookup"><span data-stu-id="18f9b-106">Example</span></span>  
 <span data-ttu-id="18f9b-107">本示例使用下面的 XML 文档：[示例 XML 文件：数值数据 (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="18f9b-107">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
IEnumerable<decimal> prices =  
    from el in root.Elements("Data")  
    let price = (decimal)el.Element("Price")  
    orderby price  
    select price;  
foreach (decimal el in prices)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="18f9b-108">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="18f9b-108">This code produces the following output:</span></span>  
  
```output  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="18f9b-109">示例</span><span class="sxs-lookup"><span data-stu-id="18f9b-109">Example</span></span>  
 <span data-ttu-id="18f9b-110">下面的示例演示如何对命名空间中的 XML 进行同样的查询。</span><span class="sxs-lookup"><span data-stu-id="18f9b-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="18f9b-111">有关详细信息，请参阅[命名空间概述(LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="18f9b-111">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="18f9b-112">本示例使用下面的 XML 文档：[示例 XML 文件：命名空间中的数值数据](./sample-xml-file-numerical-data-in-a-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="18f9b-112">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("DataInNamespace.xml");  
XNamespace aw = "http://www.adatum.com";  
IEnumerable<decimal> prices =  
    from el in root.Elements(aw + "Data")  
    let price = (decimal)el.Element(aw + "Price")  
    orderby price  
    select price;  
foreach (decimal el in prices)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="18f9b-113">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="18f9b-113">This code produces the following output:</span></span>  
  
```output  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="18f9b-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="18f9b-114">See also</span></span>

- [<span data-ttu-id="18f9b-115">对数据进行排序 (C#)</span><span class="sxs-lookup"><span data-stu-id="18f9b-115">Sorting Data (C#)</span></span>](./sorting-data.md)

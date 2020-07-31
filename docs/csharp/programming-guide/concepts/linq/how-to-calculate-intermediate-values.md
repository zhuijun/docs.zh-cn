---
title: 如何计算中间值 (C#)
description: 本 C# 中的 LINQ to XML 示例演示如何计算可用于进行排序、筛选和选择的中间值。
ms.date: 07/20/2015
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: fc648f20550de13735a1f6da6b2f811fd0d39004
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103615"
---
# <a name="how-to-calculate-intermediate-values-c"></a><span data-ttu-id="eb205-103">如何计算中间值 (C#)</span><span class="sxs-lookup"><span data-stu-id="eb205-103">How to calculate intermediate values (C#)</span></span>
<span data-ttu-id="eb205-104">本示例演示如何计算可用于进行排序、筛选和选择的中间值。</span><span class="sxs-lookup"><span data-stu-id="eb205-104">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb205-105">示例</span><span class="sxs-lookup"><span data-stu-id="eb205-105">Example</span></span>  
 <span data-ttu-id="eb205-106">下面的示例使用 `Let` 子句。</span><span class="sxs-lookup"><span data-stu-id="eb205-106">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="eb205-107">本示例使用下面的 XML 文档：[示例 XML 文件：数值数据 (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="eb205-107">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
IEnumerable<decimal> extensions =  
    from el in root.Elements("Data")  
    let extension = (decimal)el.Element("Quantity") * (decimal)el.Element("Price")  
    where extension >= 25  
    orderby extension  
    select extension;  
foreach (decimal ex in extensions)  
    Console.WriteLine(ex);  
```  
  
 <span data-ttu-id="eb205-108">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="eb205-108">This code produces the following output:</span></span>  
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="eb205-109">示例</span><span class="sxs-lookup"><span data-stu-id="eb205-109">Example</span></span>  
 <span data-ttu-id="eb205-110">下面的示例演示如何对命名空间中的 XML 进行同样的查询。</span><span class="sxs-lookup"><span data-stu-id="eb205-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="eb205-111">有关详细信息，请参阅[命名空间概述(LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="eb205-111">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="eb205-112">本示例使用下面的 XML 文档：[示例 XML 文件：命名空间中的数值数据](./sample-xml-file-numerical-data-in-a-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="eb205-112">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("DataInNamespace.xml");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<decimal> extensions =  
    from el in root.Elements(ad + "Data")  
    let extension = (decimal)el.Element(ad + "Quantity") * (decimal)el.Element(ad + "Price")  
    where extension >= 25  
    orderby extension  
    select extension;  
foreach (decimal ex in extensions)  
    Console.WriteLine(ex);  
```  
  
 <span data-ttu-id="eb205-113">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="eb205-113">This code produces the following output:</span></span>  
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  

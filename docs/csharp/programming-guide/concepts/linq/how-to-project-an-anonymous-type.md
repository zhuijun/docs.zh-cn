---
title: 如何投影匿名类型 (C#)
description: 了解如何将查询投影到 C# 中的匿名类型。 与创建新类型以供暂时使用相比，使用匿名类型更容易。
ms.date: 07/20/2015
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: 6598796a4ba95362340f2551b1da6ac6d857eaae
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104627"
---
# <a name="how-to-project-an-anonymous-type-c"></a><span data-ttu-id="50fe0-104">如何投影匿名类型 (C#)</span><span class="sxs-lookup"><span data-stu-id="50fe0-104">How to project an anonymous type (C#)</span></span>
<span data-ttu-id="50fe0-105">在某些情况下，您可能需要将查询投影到新类型，即使您知道只是短时间使用此类型。</span><span class="sxs-lookup"><span data-stu-id="50fe0-105">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span></span> <span data-ttu-id="50fe0-106">创建仅在投影中使用的新类型需要大量额外工作。</span><span class="sxs-lookup"><span data-stu-id="50fe0-106">It is a lot of extra work to create a new type just to use in the projection.</span></span> <span data-ttu-id="50fe0-107">在这种情况下，一种更有效的方法是投影到匿名类型。</span><span class="sxs-lookup"><span data-stu-id="50fe0-107">A more efficient approach in this case is to project to an anonymous type.</span></span> <span data-ttu-id="50fe0-108">匿名类型允许您定义一个类，然后在不给出类名称的情况下声明并初始化该类的对象。</span><span class="sxs-lookup"><span data-stu-id="50fe0-108">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span></span>  
  
 <span data-ttu-id="50fe0-109">匿名类型是“元组”这一数学概念的 C# 实现。</span><span class="sxs-lookup"><span data-stu-id="50fe0-109">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span></span> <span data-ttu-id="50fe0-110">数学术语元组源自序列单元组、双元组、三元组、四元组、五元组和 n 元组。</span><span class="sxs-lookup"><span data-stu-id="50fe0-110">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span></span> <span data-ttu-id="50fe0-111">它指有限的对象序列，每个对象具有特定的类型。</span><span class="sxs-lookup"><span data-stu-id="50fe0-111">It refers to a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="50fe0-112">有时，它称为名称/值对的列表。</span><span class="sxs-lookup"><span data-stu-id="50fe0-112">Sometimes this is called a list of name/value pairs.</span></span> <span data-ttu-id="50fe0-113">例如，[示例 XML 文件：典型采购订单 (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML 文档中某一地址的内容可表示为如下形式：</span><span class="sxs-lookup"><span data-stu-id="50fe0-113">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML document could be expressed as follows:</span></span>  
  
```text  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 <span data-ttu-id="50fe0-114">在创建匿名类型的实例时，可以将其想像为创建 n 阶元组。</span><span class="sxs-lookup"><span data-stu-id="50fe0-114">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span></span> <span data-ttu-id="50fe0-115">如果编写一个将在 `select` 子句中创建元组的查询，该查询将返回该元组的一个 `IEnumerable`。</span><span class="sxs-lookup"><span data-stu-id="50fe0-115">If you write a query that creates a tuple in the `select` clause, the query returns an `IEnumerable` of the tuple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50fe0-116">示例</span><span class="sxs-lookup"><span data-stu-id="50fe0-116">Example</span></span>  
 <span data-ttu-id="50fe0-117">在此示例中，`select` 子句投影一个匿名类型。</span><span class="sxs-lookup"><span data-stu-id="50fe0-117">In this example, the `select` clause projects an anonymous type.</span></span> <span data-ttu-id="50fe0-118">然后，示例使用 `var` 创建 `IEnumerable` 对象。</span><span class="sxs-lookup"><span data-stu-id="50fe0-118">The example then uses `var` to create the `IEnumerable` object.</span></span> <span data-ttu-id="50fe0-119">在 `foreach` 循环中，该迭代变量成为在查询表达式中创建的匿名类型的实例。</span><span class="sxs-lookup"><span data-stu-id="50fe0-119">Within the `foreach` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span></span>  
  
 <span data-ttu-id="50fe0-120">本示例使用下面的 XML 文档：[示例 XML 文件：客户和订单 (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) 的架构定义。</span><span class="sxs-lookup"><span data-stu-id="50fe0-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
XElement custOrd = XElement.Load("CustomersOrders.xml");  
var custList =  
    from el in custOrd.Element("Customers").Elements("Customer")  
    select new {  
        CustomerID = (string)el.Attribute("CustomerID"),  
        CompanyName = (string)el.Element("CompanyName"),  
        ContactName = (string)el.Element("ContactName")  
    };  
foreach (var cust in custList)  
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName);  
```  
  
 <span data-ttu-id="50fe0-121">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="50fe0-121">This code produces the following output:</span></span>  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
---
title: 如何：投影匿名类型
ms.date: 07/20/2015
ms.assetid: 30b42987-0e0e-4b2b-adb1-5255ddfbcd7b
ms.openlocfilehash: 459602eb7ede0bd055e00d3c7620cb95ec5408ff
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396475"
---
# <a name="how-to-project-an-anonymous-type-visual-basic"></a><span data-ttu-id="d4fd7-102">如何：投影匿名类型（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="d4fd7-102">How to: Project an Anonymous Type (Visual Basic)</span></span>
<span data-ttu-id="d4fd7-103">在某些情况下，您可能需要将查询投影到新类型，即使您知道只是短时间使用此类型。</span><span class="sxs-lookup"><span data-stu-id="d4fd7-103">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span></span> <span data-ttu-id="d4fd7-104">创建仅在投影中使用的新类型需要大量额外工作。</span><span class="sxs-lookup"><span data-stu-id="d4fd7-104">It is a lot of extra work to create a new type just to use in the projection.</span></span> <span data-ttu-id="d4fd7-105">在这种情况下，一种更有效的方法是投影到匿名类型。</span><span class="sxs-lookup"><span data-stu-id="d4fd7-105">A more efficient approach in this case is to project to an anonymous type.</span></span> <span data-ttu-id="d4fd7-106">匿名类型允许您定义一个类，然后在不给出类名称的情况下声明并初始化该类的对象。</span><span class="sxs-lookup"><span data-stu-id="d4fd7-106">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span></span>  
  
 <span data-ttu-id="d4fd7-107">匿名类型是“元组”这一数学概念的 C# 实现。 </span><span class="sxs-lookup"><span data-stu-id="d4fd7-107">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span></span> <span data-ttu-id="d4fd7-108">数学术语元组源自序列单元组、双元组、三元组、四元组、五元组和 n 元组。</span><span class="sxs-lookup"><span data-stu-id="d4fd7-108">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span></span> <span data-ttu-id="d4fd7-109">它指有限的对象序列，每个对象具有特定的类型。</span><span class="sxs-lookup"><span data-stu-id="d4fd7-109">It refers to a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="d4fd7-110">有时，它称为名称/值对的列表。</span><span class="sxs-lookup"><span data-stu-id="d4fd7-110">Sometimes this is called a list of name/value pairs.</span></span> <span data-ttu-id="d4fd7-111">例如，[示例 XML 文件：典型采购订单 (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md) XML 文档中某一地址的内容可表示为如下形式：</span><span class="sxs-lookup"><span data-stu-id="d4fd7-111">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md) XML document could be expressed as follows:</span></span>  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 <span data-ttu-id="d4fd7-112">在创建匿名类型的实例时，可以将其想像为创建 n 阶元组。</span><span class="sxs-lookup"><span data-stu-id="d4fd7-112">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span></span> <span data-ttu-id="d4fd7-113">如果编写一个将在 `Select` 子句中创建元组的查询，该查询将返回该元组的一个 `IEnumerable`。</span><span class="sxs-lookup"><span data-stu-id="d4fd7-113">If you write a query that creates a tuple in the `Select` clause, the query returns an `IEnumerable` of the tuple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4fd7-114">示例</span><span class="sxs-lookup"><span data-stu-id="d4fd7-114">Example</span></span>  
 <span data-ttu-id="d4fd7-115">在此示例中，`Select` 子句投影一个匿名类型。</span><span class="sxs-lookup"><span data-stu-id="d4fd7-115">In this example, the `Select` clause projects an anonymous type.</span></span> <span data-ttu-id="d4fd7-116">然后，示例使用 `Dim` 创建 `IEnumerable` 对象。</span><span class="sxs-lookup"><span data-stu-id="d4fd7-116">The example then uses `Dim` to create the `IEnumerable` object.</span></span> <span data-ttu-id="d4fd7-117">在 `For Each` 循环中，该迭代变量成为在查询表达式中创建的匿名类型的实例。</span><span class="sxs-lookup"><span data-stu-id="d4fd7-117">Within the `For Each` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span></span>  
  
 <span data-ttu-id="d4fd7-118">本示例使用下面的 XML 文档：[示例 XML 文件：客户和订单 (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="d4fd7-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")  
Dim custList = _  
    From el In custOrd.<Customers>.<Customer> _  
    Select New With { _  
        .CustomerID = el.@<CustomerID>, _  
        .CompanyName = el.<CompanyName>.Value, _  
        .ContactName = el.<ContactName>.Value _  
    }  
For Each cust In custList  
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName)  
Next  
```  
  
 <span data-ttu-id="d4fd7-119">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="d4fd7-119">This code produces the following output:</span></span>  
  
```console  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="d4fd7-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d4fd7-120">See also</span></span>

- [<span data-ttu-id="d4fd7-121">投影和转换（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="d4fd7-121">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](projections-and-transformations-linq-to-xml.md)

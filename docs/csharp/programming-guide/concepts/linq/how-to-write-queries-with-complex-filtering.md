---
title: 如何使用复杂筛选编写查询 (C#)
description: 了解如何编写具有复杂筛选器的 LINQ to XML 查询。 查看代码示例和其他资源。
ms.date: 07/20/2015
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: 5d2c1aafc210b35d4d6b1f1b2d74b11966d90c80
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303421"
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a><span data-ttu-id="ed0de-104">如何使用复杂筛选编写查询 (C#)</span><span class="sxs-lookup"><span data-stu-id="ed0de-104">How to write queries with complex filtering (C#)</span></span>
<span data-ttu-id="ed0de-105">有时，您需要编写使用复杂筛选器的 LINQ to XML 查询。</span><span class="sxs-lookup"><span data-stu-id="ed0de-105">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="ed0de-106">例如，您可能必须查找其子元素具有特定名称和值的所有元素。</span><span class="sxs-lookup"><span data-stu-id="ed0de-106">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="ed0de-107">本主题提供一个编写使用复杂筛选的查询的示例。</span><span class="sxs-lookup"><span data-stu-id="ed0de-107">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed0de-108">示例</span><span class="sxs-lookup"><span data-stu-id="ed0de-108">Example</span></span>  
 <span data-ttu-id="ed0de-109">本示例演示如何查找具有 `PurchaseOrder` 属性等于“Shipping”的子 `Address` 元素和等于“NY”的子 `Type` 元素的所有 `State` 元素。</span><span class="sxs-lookup"><span data-stu-id="ed0de-109">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="ed0de-110">示例在 `Where` 子句中使用嵌套查询，如果集合中有任何元素，则 `Any` 运算符返回 `true`。</span><span class="sxs-lookup"><span data-stu-id="ed0de-110">It uses a nested query in the `Where` clause, and the `Any` operator returns `true` if the collection has any elements in it.</span></span> <span data-ttu-id="ed0de-111">有关使用基于方法的查询语法的信息，请参阅 [LINQ 中的查询语法和方法语法](./query-syntax-and-method-syntax-in-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="ed0de-111">For information about using method-based query syntax, see [Query Syntax and Method Syntax in LINQ](./query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
 <span data-ttu-id="ed0de-112">本示例使用下面的 XML 文档：[示例 XML 文件：多个采购订单 (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="ed0de-112">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="ed0de-113">有关 `Any` 运算符的详细信息，请参阅[限定符运算 (C#)](./quantifier-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="ed0de-113">For more information about the `Any` operator, see [Quantifier Operations (C#)](./quantifier-operations.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrders.xml");  
IEnumerable<XElement> purchaseOrders =  
    from el in root.Elements("PurchaseOrder")  
    where
        (from add in el.Elements("Address")  
        where  
            (string)add.Attribute("Type") == "Shipping" &&  
            (string)add.Element("State") == "NY"  
        select add)  
        .Any()  
    select el;  
foreach (XElement el in purchaseOrders)  
    Console.WriteLine((string)el.Attribute("PurchaseOrderNumber"));  
```  
  
 <span data-ttu-id="ed0de-114">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="ed0de-114">This code produces the following output:</span></span>  
  
```output  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="ed0de-115">示例</span><span class="sxs-lookup"><span data-stu-id="ed0de-115">Example</span></span>  
 <span data-ttu-id="ed0de-116">下面的示例演示如何对命名空间中的 XML 进行同样的查询。</span><span class="sxs-lookup"><span data-stu-id="ed0de-116">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="ed0de-117">有关详细信息，请参阅[命名空间概述(LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="ed0de-117">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="ed0de-118">本示例使用下面的 XML 文档：[示例 XML 文件：命名空间中的多个采购订单](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="ed0de-118">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrdersInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> purchaseOrders =  
    from el in root.Elements(aw + "PurchaseOrder")  
    where  
        (from add in el.Elements(aw + "Address")  
         where  
             (string)add.Attribute(aw + "Type") == "Shipping" &&  
             (string)add.Element(aw + "State") == "NY"  
         select add)  
        .Any()  
    select el;  
foreach (XElement el in purchaseOrders)  
    Console.WriteLine((string)el.Attribute(aw + "PurchaseOrderNumber"));  
```  
  
 <span data-ttu-id="ed0de-119">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="ed0de-119">This code produces the following output:</span></span>  
  
```output  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="ed0de-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ed0de-120">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="ed0de-121">投影运算 (C#)</span><span class="sxs-lookup"><span data-stu-id="ed0de-121">Projection Operations (C#)</span></span>](./projection-operations.md)
- [<span data-ttu-id="ed0de-122">限定符运算 (C#)</span><span class="sxs-lookup"><span data-stu-id="ed0de-122">Quantifier Operations (C#)</span></span>](./quantifier-operations.md)

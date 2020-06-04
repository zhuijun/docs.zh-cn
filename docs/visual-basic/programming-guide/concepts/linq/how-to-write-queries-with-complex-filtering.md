---
title: 如何：编写使用复杂筛选的查询
ms.date: 07/20/2015
ms.assetid: bf286ffc-7990-4b00-a4eb-ee3d70129950
ms.openlocfilehash: 18ed4379b7ec9c8007cc3c189fc45571b5161911
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397617"
---
# <a name="how-to-write-queries-with-complex-filtering-visual-basic"></a><span data-ttu-id="facff-102">如何：编写具有复杂筛选的查询（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="facff-102">How to: Write Queries with Complex Filtering (Visual Basic)</span></span>
<span data-ttu-id="facff-103">有时，您需要编写使用复杂筛选器的 LINQ to XML 查询。</span><span class="sxs-lookup"><span data-stu-id="facff-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="facff-104">例如，您可能必须查找其子元素具有特定名称和值的所有元素。</span><span class="sxs-lookup"><span data-stu-id="facff-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="facff-105">本主题提供一个编写使用复杂筛选的查询的示例。</span><span class="sxs-lookup"><span data-stu-id="facff-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="facff-106">示例</span><span class="sxs-lookup"><span data-stu-id="facff-106">Example</span></span>  
 <span data-ttu-id="facff-107">本示例演示如何查找具有 `PurchaseOrder` 属性等于“Shipping”的子 `Address` 元素和等于“NY”的子 `Type` 元素的所有 `State` 元素。</span><span class="sxs-lookup"><span data-stu-id="facff-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="facff-108">示例在 `Where` 子句中使用嵌套查询，如果集合中有任何元素，则 `Any` 运算符返回 `True`。</span><span class="sxs-lookup"><span data-stu-id="facff-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `True` if the collection has any elements in it.</span></span>  
  
 <span data-ttu-id="facff-109">本示例使用以下 XML 文档：[示例 XML 文件：多个采购订单 (LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="facff-109">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="facff-110">有关运算符的详细信息 `Any` ，请参阅[限定符运算（Visual Basic）](quantifier-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="facff-110">For more information about the `Any` operator, see [Quantifier Operations (Visual Basic)](quantifier-operations.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("PurchaseOrders.xml")  
Dim purchaseOrders As IEnumerable(Of XElement) = _  
    From el In root.<PurchaseOrder> _  
    Where _  
        (From add In el.<Address> _  
        Where _  
             add.@Type = "Shipping" And _  
             add.<State>.Value = "NY" _  
        Select add) _  
    .Any() _  
    Select el  
For Each el As XElement In purchaseOrders  
    Console.WriteLine(el.@PurchaseOrderNumber)  
Next  
```  
  
 <span data-ttu-id="facff-111">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="facff-111">This code produces the following output:</span></span>  
  
```console  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="facff-112">示例</span><span class="sxs-lookup"><span data-stu-id="facff-112">Example</span></span>  
 <span data-ttu-id="facff-113">下面的示例演示如何对命名空间中的 XML 进行同样的查询。</span><span class="sxs-lookup"><span data-stu-id="facff-113">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="facff-114">有关详细信息，请参阅[命名空间概述（LINQ to XML）（Visual Basic）](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="facff-114">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="facff-115">本示例使用以下 XML 文档：[示例 XML 文件：命名空间中的多个采购订单](sample-xml-file-multiple-purchase-orders-in-a-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="facff-115">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")  
        Dim purchaseOrders As IEnumerable(Of XElement) = _  
            From el In root.<aw:PurchaseOrder> _  
            Where _  
                (From add In el.<aw:Address> _  
                Where _  
                     add.@aw:Type = "Shipping" And _  
                     add.<aw:State>.Value = "NY" _  
                Select add) _  
            .Any() _  
            Select el  
        For Each el As XElement In purchaseOrders  
            Console.WriteLine(el.@aw:PurchaseOrderNumber)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="facff-116">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="facff-116">This code produces the following output:</span></span>  
  
```console  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="facff-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="facff-117">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="facff-118">基本查询（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="facff-118">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](basic-queries-linq-to-xml.md)
- [<span data-ttu-id="facff-119">XML Child Axis Property</span><span class="sxs-lookup"><span data-stu-id="facff-119">XML Child Axis Property</span></span>](../../../language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="facff-120">XML Attribute Axis Property</span><span class="sxs-lookup"><span data-stu-id="facff-120">XML Attribute Axis Property</span></span>](../../../language-reference/xml-axis/xml-attribute-axis-property.md)
- [<span data-ttu-id="facff-121">XML 值属性</span><span class="sxs-lookup"><span data-stu-id="facff-121">XML Value Property</span></span>](../../../language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="facff-122">投影操作（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="facff-122">Projection Operations (Visual Basic)</span></span>](projection-operations.md)
- [<span data-ttu-id="facff-123">限定符运算（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="facff-123">Quantifier Operations (Visual Basic)</span></span>](quantifier-operations.md)

---
title: 如何投影新类型 (LINQ to XML) (C#)
description: 了解如何在 C# 中的 LINQ to XML 中创建查询，该查询返回除 XElement、string 或 int 以外的类型的 IEnumerable<T>，如其他示例中所述。
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: 013ea852a64b77c04ac583b4d9b71e8006cd4976
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104638"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a><span data-ttu-id="58a1c-103">如何投影新类型 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="58a1c-103">How to project a new type (LINQ to XML) (C#)</span></span>

<span data-ttu-id="58a1c-104">本节中的其他示例已演示了一些查询，这些查询以 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement>、<xref:System.Collections.Generic.IEnumerable%601> 的 `string` 和 <xref:System.Collections.Generic.IEnumerable%601> 的 `int` 的形式返回结果。</span><span class="sxs-lookup"><span data-stu-id="58a1c-104">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="58a1c-105">这些是常见结果类型，但它们不是对所有情况都适用。</span><span class="sxs-lookup"><span data-stu-id="58a1c-105">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="58a1c-106">在很多情况下，会希望查询返回其他类型的 <xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="58a1c-106">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>

## <a name="example"></a><span data-ttu-id="58a1c-107">示例</span><span class="sxs-lookup"><span data-stu-id="58a1c-107">Example</span></span>

<span data-ttu-id="58a1c-108">此示例演示如何在 `select` 子句中实例化对象。</span><span class="sxs-lookup"><span data-stu-id="58a1c-108">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="58a1c-109">代码首先定义一个具有一个构造函数的新类，然后修改 `select` 语句，使该表达式成为新类的新实例。</span><span class="sxs-lookup"><span data-stu-id="58a1c-109">The code first defines a new class with a constructor, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span>

<span data-ttu-id="58a1c-110">本示例使用下面的 XML 文档：[示例 XML 文件：典型采购订单 (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) 中所述。</span><span class="sxs-lookup"><span data-stu-id="58a1c-110">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>

```csharp
class NameQty
{
    public string name;
    public int qty;
    public NameQty(string n, int q)
    {
        name = n;
        qty = q;
    }
};

class Program {
    public static void Main()
    {
        XElement po = XElement.Load("PurchaseOrder.xml");
  
        IEnumerable<NameQty> nqList =
            from n in po.Descendants("Item")
            select new NameQty(
                    (string)n.Element("ProductName"),
                    (int)n.Element("Quantity")
                );
  
        foreach (NameQty n in nqList)
            Console.WriteLine(n.name + ":" + n.qty);
    }
}
```

<span data-ttu-id="58a1c-111">本示例使用主题[如何检索单个子元素 (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md)中引入的 <xref:System.Xml.Linq.XContainer.Element%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="58a1c-111">This example uses the <xref:System.Xml.Linq.XContainer.Element%2A> method that was introduced in the topic [How to retrieve a single child element (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="58a1c-112">还使用强制转换来检索 <xref:System.Xml.Linq.XContainer.Element%2A> 方法返回的元素值。</span><span class="sxs-lookup"><span data-stu-id="58a1c-112">It also uses casts to retrieve the values of the elements that are returned by the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  

<span data-ttu-id="58a1c-113">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="58a1c-113">This example produces the following output:</span></span>

```output
Lawnmower:1
Baby Monitor:2
```

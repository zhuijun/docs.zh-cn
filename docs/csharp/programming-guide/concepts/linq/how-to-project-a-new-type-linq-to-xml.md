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
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a>如何投影新类型 (LINQ to XML) (C#)

本节中的其他示例已演示了一些查询，这些查询以 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement>、<xref:System.Collections.Generic.IEnumerable%601> 的 `string` 和 <xref:System.Collections.Generic.IEnumerable%601> 的 `int` 的形式返回结果。 这些是常见结果类型，但它们不是对所有情况都适用。 在很多情况下，会希望查询返回其他类型的 <xref:System.Collections.Generic.IEnumerable%601>。

## <a name="example"></a>示例

此示例演示如何在 `select` 子句中实例化对象。 代码首先定义一个具有一个构造函数的新类，然后修改 `select` 语句，使该表达式成为新类的新实例。

本示例使用下面的 XML 文档：[示例 XML 文件：典型采购订单 (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) 中所述。

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

本示例使用主题[如何检索单个子元素 (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md)中引入的 <xref:System.Xml.Linq.XContainer.Element%2A> 方法。 还使用强制转换来检索 <xref:System.Xml.Linq.XContainer.Element%2A> 方法返回的元素值。  

该示例产生下面的输出：

```output
Lawnmower:1
Baby Monitor:2
```

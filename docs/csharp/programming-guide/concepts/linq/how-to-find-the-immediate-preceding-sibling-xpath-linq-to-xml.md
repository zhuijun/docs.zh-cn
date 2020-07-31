---
title: 如何查找前面紧邻的同级 (XPath-LINQ to XML) (C#)
description: 此 C# 示例比较了 XPath 与 LINQ to XML，以了解如何查找节点前面的紧邻同级。
ms.date: 07/20/2015
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: eaee7f1205ce0d0b2a9c2c41d96ba532573a1384
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105196"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-c"></a><span data-ttu-id="32c52-103">如何查找前面紧邻的同级 (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="32c52-103">How to find the immediate preceding sibling (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="32c52-104">有时，您需要查找某一节点的前面紧邻同级。</span><span class="sxs-lookup"><span data-stu-id="32c52-104">Sometimes you want to find the immediate preceding sibling to a node.</span></span> <span data-ttu-id="32c52-105">由于与 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 相比，XPath 中前面紧邻轴的位置谓词的语义同，因此这是一个更值得关注的比较。</span><span class="sxs-lookup"><span data-stu-id="32c52-105">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], this is one of the more interesting comparisons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32c52-106">示例</span><span class="sxs-lookup"><span data-stu-id="32c52-106">Example</span></span>  
 <span data-ttu-id="32c52-107">在本示例中，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查询使用 <xref:System.Linq.Enumerable.Last%2A> 运算符查找由 <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A> 返回的集合中的最后一个节点。</span><span class="sxs-lookup"><span data-stu-id="32c52-107">In this example, the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="32c52-108">相比之下，XPath 表达式使用值为 1 的谓词来查找前面紧邻的元素。</span><span class="sxs-lookup"><span data-stu-id="32c52-108">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
    @"<Root>  
    <Child1/>  
    <Child2/>  
    <Child3/>  
    <Child4/>  
</Root>");  
XElement child4 = root.Element("Child4");  
  
// LINQ to XML query  
XElement el1 =  
    child4  
    .ElementsBeforeSelf()  
    .Last();  
  
// XPath expression  
XElement el2 =  
    ((IEnumerable)child4  
                 .XPathEvaluate("preceding-sibling::*[1]"))  
                 .Cast<XElement>()  
                 .First();  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1);  
```  
  
 <span data-ttu-id="32c52-109">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="32c52-109">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<Child3 />  
```  

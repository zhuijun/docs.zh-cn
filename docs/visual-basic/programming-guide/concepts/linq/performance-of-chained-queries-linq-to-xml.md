---
title: 链接的查询的性能 (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 589f2adc-69f9-404d-b9d6-4c28dabea7f7
ms.openlocfilehash: 6b87f2744f663ebd45dceb036dcaac71b80765fc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396384"
---
# <a name="performance-of-chained-queries-linq-to-xml-visual-basic"></a><span data-ttu-id="8709c-102">链式查询的性能（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="8709c-102">Performance of Chained Queries (LINQ to XML) (Visual Basic)</span></span>

<span data-ttu-id="8709c-103">LINQ（以及 LINQ to XML）的一个最重要优点是，链接查询的执行性能与单个更大更复杂的查询一样好。</span><span class="sxs-lookup"><span data-stu-id="8709c-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>

<span data-ttu-id="8709c-104">链接查询是一种将另一个查询作为其源的查询。</span><span class="sxs-lookup"><span data-stu-id="8709c-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="8709c-105">例如，在下面的简单代码中，`query2` 使用 `query1` 作为其源：</span><span class="sxs-lookup"><span data-stu-id="8709c-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>

```vb
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))

Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x

Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e

For Each i As var In query2
    Console.WriteLine("{0}", CInt(i))
Next
```

<span data-ttu-id="8709c-106">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="8709c-106">This example produces the following output:</span></span>

```console
4
```

<span data-ttu-id="8709c-107">此链接查询提供与循环访问链接列表相同的性能配置文件。</span><span class="sxs-lookup"><span data-stu-id="8709c-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>

- <span data-ttu-id="8709c-108"><xref:System.Xml.Linq.XContainer.Elements%2A> 轴具有与循环访问链接列表基本相同的性能。</span><span class="sxs-lookup"><span data-stu-id="8709c-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="8709c-109"><xref:System.Xml.Linq.XContainer.Elements%2A> 作为具有延迟执行功能的迭代器实现。</span><span class="sxs-lookup"><span data-stu-id="8709c-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="8709c-110">这意味着它除了循环访问链接列表外还执行一些操作，例如分配迭代器对象和跟踪执行状态。</span><span class="sxs-lookup"><span data-stu-id="8709c-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="8709c-111">此项工作可以分为两类：设置迭代器时完成的工作和每次迭代过程中完成的工作。</span><span class="sxs-lookup"><span data-stu-id="8709c-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="8709c-112">设置工作是固定的少量工作，而每次迭代过程中完成的工作与源集合中的项数成正比。</span><span class="sxs-lookup"><span data-stu-id="8709c-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>

- <span data-ttu-id="8709c-113">在 `query1` 中，`Where` 子句将使查询调用 <xref:System.Linq.Enumerable.Where%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="8709c-113">In `query1`, the `Where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="8709c-114">此方法也作为迭代器实现。</span><span class="sxs-lookup"><span data-stu-id="8709c-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="8709c-115">设置工作包括实例化将引用 lambda 表达式的委托和对迭代器的常规设置。</span><span class="sxs-lookup"><span data-stu-id="8709c-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="8709c-116">每次迭代时，都将调用该委托以执行谓词。</span><span class="sxs-lookup"><span data-stu-id="8709c-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="8709c-117">设置工作和每次迭代过程中完成的工作类似于循环访问轴期间完成的工作。</span><span class="sxs-lookup"><span data-stu-id="8709c-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>

- <span data-ttu-id="8709c-118">在 `query1` 中，select 子句将使查询调用 <xref:System.Linq.Enumerable.Select%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="8709c-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="8709c-119">此方法与 <xref:System.Linq.Enumerable.Where%2A> 方法具有相同的性能配置文件。</span><span class="sxs-lookup"><span data-stu-id="8709c-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>

- <span data-ttu-id="8709c-120">`query2` 中的 `Where` 子句和 `Select` 子句与 `query1` 中的相应语句具有相同的性能配置文件。</span><span class="sxs-lookup"><span data-stu-id="8709c-120">In `query2`, both the `Where` clause and the `Select` clause have the same performance profile as in `query1`.</span></span>

 <span data-ttu-id="8709c-121">因此，通过 `query2` 执行的迭代与第一个查询源中的项数（即，线形时间）成正比。</span><span class="sxs-lookup"><span data-stu-id="8709c-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span>

## <a name="see-also"></a><span data-ttu-id="8709c-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8709c-122">See also</span></span>

- [<span data-ttu-id="8709c-123">性能（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="8709c-123">Performance (LINQ to XML) (Visual Basic)</span></span>](performance-linq-to-xml.md)

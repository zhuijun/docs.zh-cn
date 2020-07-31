---
title: LINQ to XML 中的延迟执行和迟缓计算 (C#)
description: 查询和轴操作可以使用 C# 中的延迟执行。 了解延迟执行的要求和优点，以及实现注意事项。
ms.date: 07/20/2015
ms.assetid: 8683d1b4-b7ec-407b-be12-906ebe958a09
ms.openlocfilehash: 8559505572404f895d75e0d9895f9ae2c07b795e
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105461"
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-c"></a><span data-ttu-id="9ac86-104">LINQ to XML 中的延迟执行和迟缓计算 (C#)</span><span class="sxs-lookup"><span data-stu-id="9ac86-104">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>
<span data-ttu-id="9ac86-105">实现查询和轴操作通常是为了使用延迟执行。</span><span class="sxs-lookup"><span data-stu-id="9ac86-105">Query and axis operations are often implemented to use deferred execution.</span></span> <span data-ttu-id="9ac86-106">本主题解释延迟执行的要求和优点，以及某些实现注意事项。</span><span class="sxs-lookup"><span data-stu-id="9ac86-106">This topic explains the requirements and advantages of deferred execution, and some implementation considerations.</span></span>  
  
## <a name="deferred-execution"></a><span data-ttu-id="9ac86-107">延迟执行</span><span class="sxs-lookup"><span data-stu-id="9ac86-107">Deferred Execution</span></span>  
 <span data-ttu-id="9ac86-108">延迟执行意味着表达式的计算延迟，直到真正需要其实现值为止。</span><span class="sxs-lookup"><span data-stu-id="9ac86-108">Deferred execution means that the evaluation of an expression is delayed until its *realized* value is actually required.</span></span> <span data-ttu-id="9ac86-109">当必须操作大型数据集合，特别是在包含一系列链接的查询或操作的程序中操作时，延迟执行可以大大改善性能。</span><span class="sxs-lookup"><span data-stu-id="9ac86-109">Deferred execution can greatly improve performance when you have to manipulate large data collections, especially in programs that contain a series of chained queries or manipulations.</span></span> <span data-ttu-id="9ac86-110">在最佳情况下，延迟执行只允许对源集合的单个循环访问。</span><span class="sxs-lookup"><span data-stu-id="9ac86-110">In the best case, deferred execution enables only a single iteration through the source collection.</span></span>  
  
 <span data-ttu-id="9ac86-111">LINQ 技术广泛应用了延迟执行，包括在核心 <xref:System.Linq?displayProperty=nameWithType> 类的成员和不同 LINQ 命名空间中的扩展方法（如 <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>）中使用。</span><span class="sxs-lookup"><span data-stu-id="9ac86-111">The LINQ technologies make extensive use of deferred execution in both the members of core <xref:System.Linq?displayProperty=nameWithType> classes and in the extension methods in the various LINQ namespaces, such as <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="9ac86-112">在迭代器块内使用时，C# 语言可以通过 [yield](../../../language-reference/keywords/yield.md) 关键字（以 `yield-return` 语句形式），直接支持延迟执行。</span><span class="sxs-lookup"><span data-stu-id="9ac86-112">Deferred execution is supported directly in the C# language by the [yield](../../../language-reference/keywords/yield.md) keyword (in the form of the `yield-return` statement) when used within an iterator block.</span></span> <span data-ttu-id="9ac86-113">此类迭代器必须返回类型为 <xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601>（或派生类型）的集合。</span><span class="sxs-lookup"><span data-stu-id="9ac86-113">Such an iterator must return a collection of type <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> (or a derived type).</span></span>  
  
## <a name="eager-vs-lazy-evaluation"></a><span data-ttu-id="9ac86-114">积极计算与迟缓计算</span><span class="sxs-lookup"><span data-stu-id="9ac86-114">Eager vs. Lazy Evaluation</span></span>  
 <span data-ttu-id="9ac86-115">当您编写实现延迟执行的方法时，还必须确定是使用迟缓计算还是积极计算来实现该方法。</span><span class="sxs-lookup"><span data-stu-id="9ac86-115">When you write a method that implements deferred execution, you also have to decide whether to implement the method using lazy evaluation or eager evaluation.</span></span>  
  
- <span data-ttu-id="9ac86-116">在迟缓计算中，每次调用迭代器时都会处理源集合的一个元素。</span><span class="sxs-lookup"><span data-stu-id="9ac86-116">In *lazy evaluation*, a single element of the source collection is processed during each call to the iterator.</span></span> <span data-ttu-id="9ac86-117">这是实现迭代器的典型方式。</span><span class="sxs-lookup"><span data-stu-id="9ac86-117">This is the typical way in which iterators are implemented.</span></span>  
  
- <span data-ttu-id="9ac86-118">在积极计算中，第一次调用迭代器时就会对整个集合进行处理。</span><span class="sxs-lookup"><span data-stu-id="9ac86-118">In *eager evaluation*, the first call to the iterator will result in the entire collection being processed.</span></span> <span data-ttu-id="9ac86-119">还可能需要源集合的临时副本。</span><span class="sxs-lookup"><span data-stu-id="9ac86-119">A temporary copy of the source collection might also be required.</span></span> <span data-ttu-id="9ac86-120">例如，<xref:System.Linq.Enumerable.OrderBy%2A> 方法必须在返回第一个元素前对整个集合进行排序。</span><span class="sxs-lookup"><span data-stu-id="9ac86-120">For example, the <xref:System.Linq.Enumerable.OrderBy%2A> method has to sort the entire collection before it returns the first element.</span></span>  
  
 <span data-ttu-id="9ac86-121">迟缓计算通常产生更好的性能，因为它将系统开销处理平均分配到整个集合的计算中，并将临时数据的使用降至最低。</span><span class="sxs-lookup"><span data-stu-id="9ac86-121">Lazy evaluation usually yields better performance because it distributes overhead processing evenly throughout the evaluation of the collection and minimizes the use of temporary data.</span></span> <span data-ttu-id="9ac86-122">当然，对于某些操作，除了具体化中间结果之外，再没有其他选择。</span><span class="sxs-lookup"><span data-stu-id="9ac86-122">Of course, for some operations, there is no other option than to materialize intermediate results.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="9ac86-123">后续步骤</span><span class="sxs-lookup"><span data-stu-id="9ac86-123">Next Steps</span></span>  
 <span data-ttu-id="9ac86-124">本教程的下一个主题将解释延迟执行：</span><span class="sxs-lookup"><span data-stu-id="9ac86-124">The next topic in this tutorial illustrates deferred execution:</span></span>  
  
- [<span data-ttu-id="9ac86-125">延迟执行示例 (C#)</span><span class="sxs-lookup"><span data-stu-id="9ac86-125">Deferred Execution Example (C#)</span></span>](./deferred-execution-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="9ac86-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="9ac86-126">See also</span></span>

- [<span data-ttu-id="9ac86-127">教程：将查询链接在一起 (C#)</span><span class="sxs-lookup"><span data-stu-id="9ac86-127">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
- [<span data-ttu-id="9ac86-128">概念和术语（功能转换）(C#)</span><span class="sxs-lookup"><span data-stu-id="9ac86-128">Concepts and Terminology (Functional Transformation) (C#)</span></span>](./concepts-and-terminology-functional-transformation.md)
- [<span data-ttu-id="9ac86-129">聚合运算 (C#)</span><span class="sxs-lookup"><span data-stu-id="9ac86-129">Aggregation Operations (C#)</span></span>](./aggregation-operations.md)
- [<span data-ttu-id="9ac86-130">yield</span><span class="sxs-lookup"><span data-stu-id="9ac86-130">yield</span></span>](../../../language-reference/keywords/yield.md)

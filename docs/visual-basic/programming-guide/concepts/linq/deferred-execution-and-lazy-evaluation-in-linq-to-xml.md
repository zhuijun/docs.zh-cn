---
title: LINQ to XML 中的延迟执行和迟缓计算
ms.date: 07/20/2015
ms.assetid: 31998eed-b95e-47fb-a865-9de1f337d1fb
ms.openlocfilehash: 98a5010de6ea7ef46d845c6a921c54d4e7692370
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410807"
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-visual-basic"></a><span data-ttu-id="f7b27-102">LINQ to XML （Visual Basic）中的延迟执行和迟缓计算</span><span class="sxs-lookup"><span data-stu-id="f7b27-102">Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)</span></span>
<span data-ttu-id="f7b27-103">实现查询和轴操作通常是为了使用延迟执行。</span><span class="sxs-lookup"><span data-stu-id="f7b27-103">Query and axis operations are often implemented to use deferred execution.</span></span> <span data-ttu-id="f7b27-104">本主题解释延迟执行的要求和优点，以及某些实现注意事项。</span><span class="sxs-lookup"><span data-stu-id="f7b27-104">This topic explains the requirements and advantages of deferred execution, and some implementation considerations.</span></span>  
  
## <a name="deferred-execution"></a><span data-ttu-id="f7b27-105">延迟执行</span><span class="sxs-lookup"><span data-stu-id="f7b27-105">Deferred Execution</span></span>  
 <span data-ttu-id="f7b27-106">延迟执行意味着表达式的计算延迟，直到真正需要其实现  值为止。</span><span class="sxs-lookup"><span data-stu-id="f7b27-106">Deferred execution means that the evaluation of an expression is delayed until its *realized* value is actually required.</span></span> <span data-ttu-id="f7b27-107">当必须操作大型数据集合，特别是在包含一系列链接的查询或操作的程序中操作时，延迟执行可以大大改善性能。</span><span class="sxs-lookup"><span data-stu-id="f7b27-107">Deferred execution can greatly improve performance when you have to manipulate large data collections, especially in programs that contain a series of chained queries or manipulations.</span></span> <span data-ttu-id="f7b27-108">在最佳情况下，延迟执行只允许对源集合的单个循环访问。</span><span class="sxs-lookup"><span data-stu-id="f7b27-108">In the best case, deferred execution enables only a single iteration through the source collection.</span></span>  
  
 <span data-ttu-id="f7b27-109">LINQ 技术广泛应用了延迟执行，包括在核心 <xref:System.Linq?displayProperty=nameWithType> 类的成员和不同 LINQ 命名空间中的扩展方法（如 <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>）中使用。</span><span class="sxs-lookup"><span data-stu-id="f7b27-109">The LINQ technologies make extensive use of deferred execution in both the members of core <xref:System.Linq?displayProperty=nameWithType> classes and in the extension methods in the various LINQ namespaces, such as <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="eager-vs-lazy-evaluation"></a><span data-ttu-id="f7b27-110">积极与迟缓计算</span><span class="sxs-lookup"><span data-stu-id="f7b27-110">Eager vs. Lazy Evaluation</span></span>  
 <span data-ttu-id="f7b27-111">当您编写实现延迟执行的方法时，还必须确定是使用迟缓计算还是积极计算来实现该方法。</span><span class="sxs-lookup"><span data-stu-id="f7b27-111">When you write a method that implements deferred execution, you also have to decide whether to implement the method using lazy evaluation or eager evaluation.</span></span>  
  
- <span data-ttu-id="f7b27-112">在迟缓计算\*\* 中，每次调用迭代器时都会处理源集合的一个元素。</span><span class="sxs-lookup"><span data-stu-id="f7b27-112">In *lazy evaluation*, a single element of the source collection is processed during each call to the iterator.</span></span> <span data-ttu-id="f7b27-113">这是实现迭代器的典型方式。</span><span class="sxs-lookup"><span data-stu-id="f7b27-113">This is the typical way in which iterators are implemented.</span></span>  
  
- <span data-ttu-id="f7b27-114">在积极计算\*\* 中，第一次调用迭代器时就会对整个集合进行处理。</span><span class="sxs-lookup"><span data-stu-id="f7b27-114">In *eager evaluation*, the first call to the iterator will result in the entire collection being processed.</span></span> <span data-ttu-id="f7b27-115">还可能需要源集合的临时副本。</span><span class="sxs-lookup"><span data-stu-id="f7b27-115">A temporary copy of the source collection might also be required.</span></span> <span data-ttu-id="f7b27-116">例如，<xref:System.Linq.Enumerable.OrderBy%2A> 方法必须在返回第一个元素前对整个集合进行排序。</span><span class="sxs-lookup"><span data-stu-id="f7b27-116">For example, the <xref:System.Linq.Enumerable.OrderBy%2A> method has to sort the entire collection before it returns the first element.</span></span>  
  
 <span data-ttu-id="f7b27-117">迟缓计算通常产生更好的性能，因为它将系统开销处理平均分配到整个集合的计算中，并将临时数据的使用降至最低。</span><span class="sxs-lookup"><span data-stu-id="f7b27-117">Lazy evaluation usually yields better performance because it distributes overhead processing evenly throughout the evaluation of the collection and minimizes the use of temporary data.</span></span> <span data-ttu-id="f7b27-118">当然，对于某些操作，除了具体化中间结果之外，再没有其他选择。</span><span class="sxs-lookup"><span data-stu-id="f7b27-118">Of course, for some operations, there is no other option than to materialize intermediate results.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f7b27-119">后续步骤</span><span class="sxs-lookup"><span data-stu-id="f7b27-119">Next Steps</span></span>  
 <span data-ttu-id="f7b27-120">本教程的下一个主题将解释延迟执行：</span><span class="sxs-lookup"><span data-stu-id="f7b27-120">The next topic in this tutorial illustrates deferred execution:</span></span>  
  
- [<span data-ttu-id="f7b27-121">延迟执行示例（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="f7b27-121">Deferred Execution Example (Visual Basic)</span></span>](deferred-execution-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="f7b27-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f7b27-122">See also</span></span>

- [<span data-ttu-id="f7b27-123">教程：延迟执行（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="f7b27-123">Tutorial: Deferred Execution (Visual Basic)</span></span>](tutorial-deferred-execution.md)
- [<span data-ttu-id="f7b27-124">概念和术语（功能转换）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="f7b27-124">Concepts and Terminology (Functional Transformation) (Visual Basic)</span></span>](concepts-and-terminology-functional-transformation.md)
- [<span data-ttu-id="f7b27-125">聚合运算（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="f7b27-125">Aggregation Operations (Visual Basic)</span></span>](aggregation-operations.md)

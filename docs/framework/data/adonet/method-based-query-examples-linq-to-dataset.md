---
title: 基于方法的查询示例 (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: d340775c-7f39-4087-a290-5cbec6cfa68e
ms.openlocfilehash: 1c1ef8f1b6c05415ac6f5ee59d9a415bfab2c410
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175377"
---
# <a name="method-based-query-examples-linq-to-dataset"></a><span data-ttu-id="dab6c-102">基于方法的查询示例 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="dab6c-102">Method-Based Query Examples (LINQ to DataSet)</span></span>

<span data-ttu-id="dab6c-103">本节提供使用标准查询运算符的基于方法的查询语法中的 LINQ to DataSet 编程示例。</span><span class="sxs-lookup"><span data-stu-id="dab6c-103">This section provides LINQ to DataSet programming examples in method-based query syntax that use the standard query operators.</span></span> <span data-ttu-id="dab6c-104"><xref:System.Data.DataSet>这些示例中使用的是使用方法填充的 `FillDataSet` ，该方法是在将[数据加载到数据集](loading-data-into-a-dataset.md)时指定的。</span><span class="sxs-lookup"><span data-stu-id="dab6c-104">The <xref:System.Data.DataSet> used in these examples is populated by using the `FillDataSet` method, which is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span> <span data-ttu-id="dab6c-105">有关详细信息，请参阅 [标准查询运算符概述 (c # ) ](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) 或 [标准查询运算符概述 (Visual Basic) ](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="dab6c-105">For more information, see [Standard Query Operators Overview (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dab6c-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="dab6c-106">In This Section</span></span>  

 [<span data-ttu-id="dab6c-107">投影</span><span class="sxs-lookup"><span data-stu-id="dab6c-107">Projection</span></span>](method-based-query-syntax-examples-projection.md)  
 <span data-ttu-id="dab6c-108">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.Select%2A> 和 <xref:System.Linq.Enumerable.SelectMany%2A> 方法来查询 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="dab6c-108">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="dab6c-109">分区</span><span class="sxs-lookup"><span data-stu-id="dab6c-109">Partitioning</span></span>](method-based-query-syntax-examples-partitioning-linq.md)  
 <span data-ttu-id="dab6c-110">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.Skip%2A> 和 <xref:System.Linq.Enumerable.Take%2A> 方法来查询 <xref:System.Data.DataSet> 并分隔结果。</span><span class="sxs-lookup"><span data-stu-id="dab6c-110">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query a <xref:System.Data.DataSet> and partition the results.</span></span>  
  
 [<span data-ttu-id="dab6c-111">中间件排序</span><span class="sxs-lookup"><span data-stu-id="dab6c-111">Ordering</span></span>](method-based-query-syntax-examples-ordering-linq-to-dataset.md)  
 <span data-ttu-id="dab6c-112">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.OrderBy%2A>、<xref:System.Linq.Enumerable.OrderByDescending%2A>、<xref:System.Linq.Enumerable.Reverse%2A> 和 <xref:System.Linq.Enumerable.ThenByDescending%2A> 方法来查询 <xref:System.Data.DataSet> 并排序结果。</span><span class="sxs-lookup"><span data-stu-id="dab6c-112">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results.</span></span>  
  
 [<span data-ttu-id="dab6c-113">集合运算符</span><span class="sxs-lookup"><span data-stu-id="dab6c-113">Set Operators</span></span>](method-based-query-syntax-examples-set-operators.md)  
 <span data-ttu-id="dab6c-114">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.Distinct%2A>、<xref:System.Linq.Enumerable.Except%2A>、<xref:System.Linq.Enumerable.Intersect%2A> 和 <xref:System.Linq.Enumerable.Union%2A> 运算符对多组数据行执行基于值的比较运算。</span><span class="sxs-lookup"><span data-stu-id="dab6c-114">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, and <xref:System.Linq.Enumerable.Union%2A> operators to perform value-based comparison operations on sets of data rows.</span></span>  
  
 [<span data-ttu-id="dab6c-115">转换运算符</span><span class="sxs-lookup"><span data-stu-id="dab6c-115">Conversion Operators</span></span>](method-based-query-syntax-examples-conversion-operators.md)  
 <span data-ttu-id="dab6c-116">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.ToArray%2A>、<xref:System.Linq.Enumerable.ToDictionary%2A> 和 <xref:System.Linq.Enumerable.ToList%2A> 方法立即执行查询表达式。</span><span class="sxs-lookup"><span data-stu-id="dab6c-116">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A>, and <xref:System.Linq.Enumerable.ToList%2A> methods to immediately execute a query expression.</span></span>  
  
 [<span data-ttu-id="dab6c-117">元素运算符</span><span class="sxs-lookup"><span data-stu-id="dab6c-117">Element Operators</span></span>](method-based-query-syntax-examples-element-operators.md)  
 <span data-ttu-id="dab6c-118">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.First%2A> 和 <xref:System.Linq.Enumerable.ElementAt%2A> 方法来获取 <xref:System.Data.DataRow> 中的 <xref:System.Data.DataSet> 元素。</span><span class="sxs-lookup"><span data-stu-id="dab6c-118">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="dab6c-119">聚合运算符</span><span class="sxs-lookup"><span data-stu-id="dab6c-119">Aggregate Operators</span></span>](method-based-query-syntax-examples-aggregate-operators.md)  
 <span data-ttu-id="dab6c-120">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Count%2A>、<xref:System.Linq.Enumerable.Max%2A>、<xref:System.Linq.Enumerable.Min%2A> 和 <xref:System.Linq.Enumerable.Sum%2A> 方法来查询 <xref:System.Data.DataSet> 并聚合数据。</span><span class="sxs-lookup"><span data-stu-id="dab6c-120">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query a <xref:System.Data.DataSet> and aggregate data.</span></span>  
  
 [<span data-ttu-id="dab6c-121">Join</span><span class="sxs-lookup"><span data-stu-id="dab6c-121">Join</span></span>](method-based-query-syntax-examples-join-linq-to-dataset.md)  
 <span data-ttu-id="dab6c-122">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.GroupJoin%2A> 和 <xref:System.Linq.Enumerable.Join%2A> 方法来查询 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="dab6c-122">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dab6c-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="dab6c-123">See also</span></span>

- [<span data-ttu-id="dab6c-124">查询表达式示例</span><span class="sxs-lookup"><span data-stu-id="dab6c-124">Query Expression Examples</span></span>](query-expression-examples-linq-to-dataset.md)
- [<span data-ttu-id="dab6c-125">数据集特定的运算符示例</span><span class="sxs-lookup"><span data-stu-id="dab6c-125">DataSet-Specific Operator Examples</span></span>](dataset-specific-operator-examples-linq-to-dataset.md)
- [<span data-ttu-id="dab6c-126">LINQ to DataSet 示例</span><span class="sxs-lookup"><span data-stu-id="dab6c-126">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)

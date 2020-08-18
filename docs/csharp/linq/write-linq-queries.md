---
title: 在 C# 中编写 LINQ 查询
description: 了解如何在 C# 中编写 LINQ 查询。
ms.date: 12/01/2016
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.openlocfilehash: bd7da81f2873c6a25570cab32fafecc66fd98be4
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063440"
---
# <a name="write-linq-queries-in-c"></a><span data-ttu-id="170e0-103">在 C\# 中编写 LINQ 查询</span><span class="sxs-lookup"><span data-stu-id="170e0-103">Write LINQ queries in C\#</span></span>

<span data-ttu-id="170e0-104">本文介绍可以用于在 C# 中编写 LINQ 查询的三种方法：</span><span class="sxs-lookup"><span data-stu-id="170e0-104">This article shows the three ways in which you can write a LINQ query in C#:</span></span>

1. <span data-ttu-id="170e0-105">使用查询语法。</span><span class="sxs-lookup"><span data-stu-id="170e0-105">Use query syntax.</span></span>

2. <span data-ttu-id="170e0-106">使用方法语法。</span><span class="sxs-lookup"><span data-stu-id="170e0-106">Use method syntax.</span></span>

3. <span data-ttu-id="170e0-107">结合使用查询语法和方法语法。</span><span class="sxs-lookup"><span data-stu-id="170e0-107">Use a combination of query syntax and method syntax.</span></span>

<span data-ttu-id="170e0-108">下面的示例演示使用前面列出的每种方法的一些简单 LINQ 查询。</span><span class="sxs-lookup"><span data-stu-id="170e0-108">The following examples demonstrate some simple LINQ queries by using each approach listed previously.</span></span> <span data-ttu-id="170e0-109">一般情况下，规则是尽可能使用 (1)，每当需要时使用 (2) 和 (3)。</span><span class="sxs-lookup"><span data-stu-id="170e0-109">In general, the rule is to use (1) whenever possible, and use (2) and (3) whenever necessary.</span></span>

> [!NOTE]
> <span data-ttu-id="170e0-110">这些查询对简单的内存中集合进行操作；但是，基本语法等同于在 LINQ to Entities 和 LINQ to XML 中使用的语法。</span><span class="sxs-lookup"><span data-stu-id="170e0-110">These queries operate on simple in-memory collections; however, the basic syntax is identical to that used in LINQ to Entities and LINQ to XML.</span></span>

## <a name="example---query-syntax"></a><span data-ttu-id="170e0-111">示例 - 查询语法</span><span class="sxs-lookup"><span data-stu-id="170e0-111">Example - Query syntax</span></span>

<span data-ttu-id="170e0-112">编写大多数查询的推荐方式是使用查询语法  创建查询表达式  。</span><span class="sxs-lookup"><span data-stu-id="170e0-112">The recommended way to write most queries is to use *query syntax* to create *query expressions*.</span></span> <span data-ttu-id="170e0-113">下面的示例演示三个查询表达式。</span><span class="sxs-lookup"><span data-stu-id="170e0-113">The following example shows three query expressions.</span></span> <span data-ttu-id="170e0-114">第一个查询表达式演示如何通过应用包含 `where` 子句的条件来筛选或限制结果。</span><span class="sxs-lookup"><span data-stu-id="170e0-114">The first query expression demonstrates how to filter or restrict results by applying conditions with a `where` clause.</span></span> <span data-ttu-id="170e0-115">它返回源序列中值大于 7 或小于 3 的所有元素。</span><span class="sxs-lookup"><span data-stu-id="170e0-115">It returns all elements in the source sequence whose values are greater than 7 or less than 3.</span></span> <span data-ttu-id="170e0-116">第二个表达式演示如何对返回的结果进行排序。</span><span class="sxs-lookup"><span data-stu-id="170e0-116">The second expression demonstrates how to order the returned results.</span></span> <span data-ttu-id="170e0-117">第三个表达式演示如何根据某个键对结果进行分组。</span><span class="sxs-lookup"><span data-stu-id="170e0-117">The third expression demonstrates how to group results according to a key.</span></span> <span data-ttu-id="170e0-118">此查询基于单词的第一个字母返回两个组。</span><span class="sxs-lookup"><span data-stu-id="170e0-118">This query returns two groups based on the first letter of the word.</span></span>

[!code-csharp[csProgGuideLINQ#5](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]

<span data-ttu-id="170e0-119">注意，查询类型为 <xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="170e0-119">Note that the type of the queries is <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="170e0-120">可以使用 `var` 编写所有这些查询，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="170e0-120">All of these queries could be written using `var` as shown in the following example:</span></span>

`var query = from num in numbers...`

<span data-ttu-id="170e0-121">在前面的每个示例中，在 `foreach` 语句或其他语句中循环访问查询变量之前，查询不会实际执行。</span><span class="sxs-lookup"><span data-stu-id="170e0-121">In each previous example, the queries do not actually execute until you iterate over the query variable in a `foreach` statement or other statement.</span></span> <span data-ttu-id="170e0-122">有关详细信息，请参阅 [LINQ 查询介绍](../programming-guide/concepts/linq/introduction-to-linq-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="170e0-122">For more information, see [Introduction to LINQ Queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

## <a name="example---method-syntax"></a><span data-ttu-id="170e0-123">示例 - 方法语法</span><span class="sxs-lookup"><span data-stu-id="170e0-123">Example - Method syntax</span></span>

<span data-ttu-id="170e0-124">某些查询操作必须表示为方法调用。</span><span class="sxs-lookup"><span data-stu-id="170e0-124">Some query operations must be expressed as a method call.</span></span> <span data-ttu-id="170e0-125">最常见的此类方法是可返回单一数值的方法，例如 <xref:System.Linq.Enumerable.Sum%2A>、<xref:System.Linq.Enumerable.Max%2A>、<xref:System.Linq.Enumerable.Min%2A>、<xref:System.Linq.Enumerable.Average%2A> 等。</span><span class="sxs-lookup"><span data-stu-id="170e0-125">The most common such methods are those that return singleton numeric values, such as <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>, and so on.</span></span> <span data-ttu-id="170e0-126">这些方法在任何查询中都必须始终最后一个调用，因为它们只表示单个值，不能用作其他查询操作的源。</span><span class="sxs-lookup"><span data-stu-id="170e0-126">These methods must always be called last in any query because they represent only a single value and cannot serve as the source for an additional query operation.</span></span> <span data-ttu-id="170e0-127">下面的示例演示查询表达式中的方法调用：</span><span class="sxs-lookup"><span data-stu-id="170e0-127">The following example shows a method call in a query expression:</span></span>

[!code-csharp[csProgGuideLINQ#6](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]

<span data-ttu-id="170e0-128">如果方法具有 Action 或 Func 参数，则这些参数以 [lambda](../language-reference/operators/lambda-expressions.md) 表达式的形式提供，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="170e0-128">If the method has Action or Func parameters, these are provided in the form of a [lambda](../language-reference/operators/lambda-expressions.md) expression, as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#7](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]

<span data-ttu-id="170e0-129">在上面的查询中，只有查询 #4 立即执行。</span><span class="sxs-lookup"><span data-stu-id="170e0-129">In the previous queries, only Query #4 executes immediately.</span></span> <span data-ttu-id="170e0-130">这是因为它将返回单个值，而不是泛型 <xref:System.Collections.Generic.IEnumerable%601> 集合。</span><span class="sxs-lookup"><span data-stu-id="170e0-130">This is because it returns a single value, and not a generic <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="170e0-131">该方法本身必须使用 `foreach` 才能计算其值。</span><span class="sxs-lookup"><span data-stu-id="170e0-131">The method itself has to use `foreach` in order to compute its value.</span></span>

<span data-ttu-id="170e0-132">上面的每个查询可以通过 [var](../language-reference/keywords/var.md) 使用隐式类型化进行编写，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="170e0-132">Each of the previous queries can be written by using implicit typing with [var](../language-reference/keywords/var.md), as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#8](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]

## <a name="example---mixed-query-and-method-syntax"></a><span data-ttu-id="170e0-133">示例 - 混合查询和方法语法</span><span class="sxs-lookup"><span data-stu-id="170e0-133">Example - Mixed query and method syntax</span></span>

<span data-ttu-id="170e0-134">此示例演示如何对查询子句的结果使用方法语法。</span><span class="sxs-lookup"><span data-stu-id="170e0-134">This example shows how to use method syntax on the results of a query clause.</span></span> <span data-ttu-id="170e0-135">只需将查询表达式括在括号中，然后应用点运算符并调用方法。</span><span class="sxs-lookup"><span data-stu-id="170e0-135">Just enclose the query expression in parentheses, and then apply the dot operator and call the method.</span></span> <span data-ttu-id="170e0-136">在下面的示例中，查询 #7 返回对值介于 3 与 7 之间的数字进行的计数。</span><span class="sxs-lookup"><span data-stu-id="170e0-136">In the following example, query #7 returns a count of the numbers whose value is between 3 and 7.</span></span> <span data-ttu-id="170e0-137">但是通常情况下，最好使用另一个变量存储方法调用的结果。</span><span class="sxs-lookup"><span data-stu-id="170e0-137">In general, however, it is better to use a second variable to store the result of the method call.</span></span> <span data-ttu-id="170e0-138">采用此方法时，查询不太可能与查询的结果相混淆。</span><span class="sxs-lookup"><span data-stu-id="170e0-138">In this manner, the query is less likely to be confused with the results of the query.</span></span>

[!code-csharp[csProgGuideLINQ#9](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]

<span data-ttu-id="170e0-139">由于查询 #7 返回单个值而不是集合，因此查询立即执行。</span><span class="sxs-lookup"><span data-stu-id="170e0-139">Because Query #7 returns a single value and not a collection, the query executes immediately.</span></span>

<span data-ttu-id="170e0-140">前面的查询可以通过 `var` 使用隐式类型化进行编写，如下所示：</span><span class="sxs-lookup"><span data-stu-id="170e0-140">The previous query can be written by using implicit typing with `var`, as follows:</span></span>

```csharp
var numCount = (from num in numbers...
```

<span data-ttu-id="170e0-141">它可以采用方法语法进行编写，如下所示：</span><span class="sxs-lookup"><span data-stu-id="170e0-141">It can be written in method syntax as follows:</span></span>

```csharp
var numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

<span data-ttu-id="170e0-142">它可以使用显式类型化进行编写，如下所示：</span><span class="sxs-lookup"><span data-stu-id="170e0-142">It can be written by using explicit typing, as follows:</span></span>

```csharp
int numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

## <a name="see-also"></a><span data-ttu-id="170e0-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="170e0-143">See also</span></span>

- [<span data-ttu-id="170e0-144">演练：用 C# 编写查询</span><span class="sxs-lookup"><span data-stu-id="170e0-144">Walkthrough: Writing Queries in C#</span></span>](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
- [<span data-ttu-id="170e0-145">语言集成查询 (LINQ)</span><span class="sxs-lookup"><span data-stu-id="170e0-145">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="170e0-146">where 子句</span><span class="sxs-lookup"><span data-stu-id="170e0-146">where clause</span></span>](../language-reference/keywords/where-clause.md)

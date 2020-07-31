---
title: 基本 LINQ 查询操作 (C#)
description: 介绍一下 LINQ 查询表达式以及在查询中可能执行的一些操作。
ms.date: 07/20/2015
helpviewer_keywords:
- orderby clause [LINQ in C#]
- ordering data [LINQ in C#]
- selecting data [LINQ in C#]
- queries [LINQ in C#], basic operations
- grouping data [LINQ in C#]
- data sources [LINQ in C#]
- sorting data [LINQ in C#]
- projections [LINQ in C#]
- filtering data [LINQ in C#]
- joining data [LINQ in C#]
- select clause [LINQ in C#]
- LINQ [C#], basic query operations
- join clause [LINQ in C#]
- group clause [LINQ in C#]
ms.assetid: a7ea3421-1cf4-4df7-832a-aa22fe6379e9
ms.openlocfilehash: d9653be8b67ef4d971c157b8dd8d82b2ae3c2287
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105524"
---
# <a name="basic-linq-query-operations-c"></a><span data-ttu-id="5d78a-103">基本 LINQ 查询操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="5d78a-103">Basic LINQ Query Operations (C#)</span></span>
<span data-ttu-id="5d78a-104">本主题简要介绍了 LINQ 查询表达式和一些在查询中执行的典型操作。</span><span class="sxs-lookup"><span data-stu-id="5d78a-104">This topic gives a brief introduction to LINQ query expressions and some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="5d78a-105">下面各主题中提供了更具体的信息：</span><span class="sxs-lookup"><span data-stu-id="5d78a-105">More detailed information is in the following topics:</span></span>  
  
 [<span data-ttu-id="5d78a-106">LINQ 查询表达式</span><span class="sxs-lookup"><span data-stu-id="5d78a-106">LINQ Query Expressions</span></span>](../../../linq/index.md)  
  
 [<span data-ttu-id="5d78a-107">标准查询运算符概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="5d78a-107">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)  
  
 [<span data-ttu-id="5d78a-108">演练：用 C# 编写查询</span><span class="sxs-lookup"><span data-stu-id="5d78a-108">Walkthrough: Writing Queries in C#</span></span>](./walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
> <span data-ttu-id="5d78a-109">如果你已熟悉查询语言（如 SQL 或 XQuery），则可以跳过本主题的大部分内容。</span><span class="sxs-lookup"><span data-stu-id="5d78a-109">If you already are familiar with a query language such as SQL or XQuery, you can skip most of this topic.</span></span> <span data-ttu-id="5d78a-110">请参阅下一节中的“`from` 子句”部分，了解 LINQ 查询表达式中的子句顺序。</span><span class="sxs-lookup"><span data-stu-id="5d78a-110">Read about the "`from` clause" in the next section to learn about the order of clauses in LINQ query expressions.</span></span>  
  
## <a name="obtaining-a-data-source"></a><span data-ttu-id="5d78a-111">获取数据源</span><span class="sxs-lookup"><span data-stu-id="5d78a-111">Obtaining a Data Source</span></span>  
 <span data-ttu-id="5d78a-112">在 LINQ 查询中，第一步是指定数据源。</span><span class="sxs-lookup"><span data-stu-id="5d78a-112">In a LINQ query, the first step is to specify the data source.</span></span> <span data-ttu-id="5d78a-113">和大多数编程语言相同，在使用 C# 时也必须先声明变量，然后才能使用它。</span><span class="sxs-lookup"><span data-stu-id="5d78a-113">In C# as in most programming languages a variable must be declared before it can be used.</span></span> <span data-ttu-id="5d78a-114">在 LINQ 查询中，先使用 `from` 子句引入数据源 (`customers`) 和范围变量 (`cust`)。</span><span class="sxs-lookup"><span data-stu-id="5d78a-114">In a LINQ query, the `from` clause comes first in order to introduce the data source (`customers`) and the *range variable* (`cust`).</span></span>  
  
 [!code-csharp[csLINQGettingStarted#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#23)]  
  
 <span data-ttu-id="5d78a-115">范围变量就像 `foreach` 循环中的迭代变量，但查询表达式中不会真正发生迭代。</span><span class="sxs-lookup"><span data-stu-id="5d78a-115">The range variable is like the iteration variable in a `foreach` loop except that no actual iteration occurs in a query expression.</span></span> <span data-ttu-id="5d78a-116">当执行查询时，范围变量将充当对 `customers` 中每个连续的元素的引用。</span><span class="sxs-lookup"><span data-stu-id="5d78a-116">When the query is executed, the range variable will serve as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="5d78a-117">由于编译器可以推断 `cust` 的类型，因此无需显式指定它。</span><span class="sxs-lookup"><span data-stu-id="5d78a-117">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="5d78a-118">可通过 `let` 子句引入其他范围变量。</span><span class="sxs-lookup"><span data-stu-id="5d78a-118">Additional range variables can be introduced by a `let` clause.</span></span> <span data-ttu-id="5d78a-119">有关详细信息，请参阅 [let 子句](../../../language-reference/keywords/let-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="5d78a-119">For more information, see [let clause](../../../language-reference/keywords/let-clause.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5d78a-120">对于非泛型数据源（例如 <xref:System.Collections.ArrayList>），必须显式键入范围变量。</span><span class="sxs-lookup"><span data-stu-id="5d78a-120">For non-generic data sources such as <xref:System.Collections.ArrayList>, the range variable must be explicitly typed.</span></span> <span data-ttu-id="5d78a-121">有关详细信息，请参阅[如何使用 LINQ (C#)](./how-to-query-an-arraylist-with-linq.md) 和 [From 子句](../../../language-reference/keywords/from-clause.md)查询 ArrayList。</span><span class="sxs-lookup"><span data-stu-id="5d78a-121">For more information, see [How to query an ArrayList with LINQ (C#)](./how-to-query-an-arraylist-with-linq.md) and [from clause](../../../language-reference/keywords/from-clause.md).</span></span>  
  
## <a name="filtering"></a><span data-ttu-id="5d78a-122">筛选</span><span class="sxs-lookup"><span data-stu-id="5d78a-122">Filtering</span></span>  
 <span data-ttu-id="5d78a-123">或许，最常见的查询操作是以布尔表达式的形式应用筛选器。</span><span class="sxs-lookup"><span data-stu-id="5d78a-123">Probably the most common query operation is to apply a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="5d78a-124">筛选器使查询仅返回表达式为 true 的元素。</span><span class="sxs-lookup"><span data-stu-id="5d78a-124">The filter causes the query to return only those elements for which the expression is true.</span></span> <span data-ttu-id="5d78a-125">将通过使用 `where` 子句生成结果。</span><span class="sxs-lookup"><span data-stu-id="5d78a-125">The result is produced by using the `where` clause.</span></span> <span data-ttu-id="5d78a-126">筛选器实际指定要从源序列排除哪些元素。</span><span class="sxs-lookup"><span data-stu-id="5d78a-126">The filter in effect specifies which elements to exclude from the source sequence.</span></span> <span data-ttu-id="5d78a-127">在下列示例中，仅返回地址位于“London”的 `customers`。</span><span class="sxs-lookup"><span data-stu-id="5d78a-127">In the following example, only those `customers` who have an address in London are returned.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#24)]  
  
 <span data-ttu-id="5d78a-128">可使用熟悉的 C# 逻辑 `AND` 和 `OR` 运算符，在 `where` 子句中根据需要应用尽可能多的筛选器表达式。</span><span class="sxs-lookup"><span data-stu-id="5d78a-128">You can use the familiar C# logical `AND` and `OR` operators to apply as many filter expressions as necessary in the `where` clause.</span></span> <span data-ttu-id="5d78a-129">例如，若要仅返回来自“London”的客户 `AND` 该客户名称为“Devon”，可编写以下代码：</span><span class="sxs-lookup"><span data-stu-id="5d78a-129">For example, to return only customers from "London" `AND` whose name is "Devon" you would write the following code:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#25)]  
  
 <span data-ttu-id="5d78a-130">要返回来自 London 或 Paris 的客户，可编写以下代码：</span><span class="sxs-lookup"><span data-stu-id="5d78a-130">To return customers from London or Paris, you would write the following code:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#26)]  
  
 <span data-ttu-id="5d78a-131">有关详细信息，请参阅 [where 子句](../../../language-reference/keywords/where-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="5d78a-131">For more information, see [where clause](../../../language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="ordering"></a><span data-ttu-id="5d78a-132">中间件排序</span><span class="sxs-lookup"><span data-stu-id="5d78a-132">Ordering</span></span>  
 <span data-ttu-id="5d78a-133">对返回的数据进行排序通常很方便。</span><span class="sxs-lookup"><span data-stu-id="5d78a-133">Often it is convenient to sort the returned data.</span></span> <span data-ttu-id="5d78a-134">`orderby` 子句根据要排序类型的默认比较器，对返回序列中的元素排序。</span><span class="sxs-lookup"><span data-stu-id="5d78a-134">The `orderby` clause will cause the elements in the returned sequence to be sorted according to the default comparer for the type being sorted.</span></span> <span data-ttu-id="5d78a-135">例如，基于 `Name` 属性，可将下列查询扩展为对结果排序。</span><span class="sxs-lookup"><span data-stu-id="5d78a-135">For example, the following query can be extended to sort the results based on the `Name` property.</span></span> <span data-ttu-id="5d78a-136">由于 `Name` 是字符串，默认比较器将按字母顺序从 A 到 Z 进行排序。</span><span class="sxs-lookup"><span data-stu-id="5d78a-136">Because `Name` is a string, the default comparer performs an alphabetical sort from A to Z.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#27)]  
  
 <span data-ttu-id="5d78a-137">要对结果进行从 Z 到 A 的逆序排序，请使用 `orderby…descending` 子句。</span><span class="sxs-lookup"><span data-stu-id="5d78a-137">To order the results in reverse order, from Z to A, use the `orderby…descending` clause.</span></span>  
  
 <span data-ttu-id="5d78a-138">有关详细信息，请参阅 [orderby 子句](../../../language-reference/keywords/orderby-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="5d78a-138">For more information, see [orderby clause](../../../language-reference/keywords/orderby-clause.md).</span></span>  
  
## <a name="grouping"></a><span data-ttu-id="5d78a-139">分组</span><span class="sxs-lookup"><span data-stu-id="5d78a-139">Grouping</span></span>  
 <span data-ttu-id="5d78a-140">`group` 子句用于对根据您指定的键所获得的结果进行分组。</span><span class="sxs-lookup"><span data-stu-id="5d78a-140">The `group` clause enables you to group your results based on a key that you specify.</span></span> <span data-ttu-id="5d78a-141">例如，可指定按 `City` 对结果进行分组，使来自 London 或 Paris 的所有客户位于单独的组内。</span><span class="sxs-lookup"><span data-stu-id="5d78a-141">For example you could specify that the results should be grouped by the `City` so that all customers from London or Paris are in individual groups.</span></span> <span data-ttu-id="5d78a-142">在这种情况下，`cust.City` 是键。</span><span class="sxs-lookup"><span data-stu-id="5d78a-142">In this case, `cust.City` is the key.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#28)]  
  
 <span data-ttu-id="5d78a-143">使用 `group` 子句结束查询时，结果将以列表的形式列出。</span><span class="sxs-lookup"><span data-stu-id="5d78a-143">When you end a query with a `group` clause, your results take the form of a list of lists.</span></span> <span data-ttu-id="5d78a-144">列表中的每个元素都是具有 `Key` 成员的对象，列表中的元素根据该键被分组。</span><span class="sxs-lookup"><span data-stu-id="5d78a-144">Each element in the list is an object that has a `Key` member and a list of elements that are grouped under that key.</span></span> <span data-ttu-id="5d78a-145">在循环访问生成组序列的查询时，必须使用嵌套 `foreach` 循环。</span><span class="sxs-lookup"><span data-stu-id="5d78a-145">When you iterate over a query that produces a sequence of groups, you must use a nested `foreach` loop.</span></span> <span data-ttu-id="5d78a-146">外层循环循环访问每个组，内层循环循环访问每个组的成员。</span><span class="sxs-lookup"><span data-stu-id="5d78a-146">The outer loop iterates over each group, and the inner loop iterates over each group's members.</span></span>  
  
 <span data-ttu-id="5d78a-147">如果必须引用某个组操作的结果，可使用 `into` 关键字创建能被进一步查询的标识符。</span><span class="sxs-lookup"><span data-stu-id="5d78a-147">If you must refer to the results of a group operation, you can use the `into` keyword to create an identifier that can be queried further.</span></span> <span data-ttu-id="5d78a-148">下列查询仅返回包含两个以上客户的组：</span><span class="sxs-lookup"><span data-stu-id="5d78a-148">The following query returns only those groups that contain more than two customers:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#29)]  
  
 <span data-ttu-id="5d78a-149">有关详细信息，请参阅 [group 子句](../../../language-reference/keywords/group-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="5d78a-149">For more information, see [group clause](../../../language-reference/keywords/group-clause.md).</span></span>  
  
## <a name="joining"></a><span data-ttu-id="5d78a-150">联接</span><span class="sxs-lookup"><span data-stu-id="5d78a-150">Joining</span></span>  
 <span data-ttu-id="5d78a-151">联接操作在不同序列间创建关联，这些序列在数据源中未被显式模块化。</span><span class="sxs-lookup"><span data-stu-id="5d78a-151">Join operations create associations between sequences that are not explicitly modeled in the data sources.</span></span> <span data-ttu-id="5d78a-152">例如，可通过执行联接来查找所有位置相同的客户和分销商。</span><span class="sxs-lookup"><span data-stu-id="5d78a-152">For example you can perform a join to find all the customers and distributors who have the same location.</span></span> <span data-ttu-id="5d78a-153">在 LINQ 中，`join` 子句始终作用于对象集合，而非直接作用于数据库表。</span><span class="sxs-lookup"><span data-stu-id="5d78a-153">In LINQ the `join` clause always works against object collections instead of database tables directly.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#36)]  
  
 <span data-ttu-id="5d78a-154">在 LINQ 中，不必像在 SQL 中那样频繁使用 `join`，因为 LINQ 中的外键在对象模型中表示为包含项集合的属性。</span><span class="sxs-lookup"><span data-stu-id="5d78a-154">In LINQ, you do not have to use `join` as often as you do in SQL, because foreign keys in LINQ are represented in the object model as properties that hold a collection of items.</span></span> <span data-ttu-id="5d78a-155">例如 `Customer` 对象包含 `Order` 对象的集合。</span><span class="sxs-lookup"><span data-stu-id="5d78a-155">For example, a `Customer` object contains a collection of `Order` objects.</span></span> <span data-ttu-id="5d78a-156">不必执行联接，只需使用点表示法访问订单：</span><span class="sxs-lookup"><span data-stu-id="5d78a-156">Rather than performing a join, you access the orders by using dot notation:</span></span>  
  
```csharp
from order in Customer.Orders...  
```  
  
 <span data-ttu-id="5d78a-157">有关详细信息，请参阅 [join 子句](../../../language-reference/keywords/join-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="5d78a-157">For more information, see [join clause](../../../language-reference/keywords/join-clause.md).</span></span>  
  
## <a name="selecting-projections"></a><span data-ttu-id="5d78a-158">选择（投影）</span><span class="sxs-lookup"><span data-stu-id="5d78a-158">Selecting (Projections)</span></span>  
 <span data-ttu-id="5d78a-159">`select` 子句生成查询结果并指定每个返回的元素的“形状”或类型。</span><span class="sxs-lookup"><span data-stu-id="5d78a-159">The `select` clause produces the results of the query and specifies the "shape" or type of each returned element.</span></span> <span data-ttu-id="5d78a-160">例如，可以指定结果包含的是整个 `Customer` 对象、仅一个成员、成员的子集，还是某个基于计算或新对象创建的完全不同的结果类型。</span><span class="sxs-lookup"><span data-stu-id="5d78a-160">For example, you can specify whether your results will consist of complete `Customer` objects, just one member, a subset of members, or some completely different result type based on a computation or new object creation.</span></span> <span data-ttu-id="5d78a-161">当 `select` 子句生成除源元素副本以外的内容时，该操作称为投影。</span><span class="sxs-lookup"><span data-stu-id="5d78a-161">When the `select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span> <span data-ttu-id="5d78a-162">使用投影转换数据是 LINQ 查询表达式的一种强大功能。</span><span class="sxs-lookup"><span data-stu-id="5d78a-162">The use of projections to transform data is a powerful capability of LINQ query expressions.</span></span> <span data-ttu-id="5d78a-163">有关详细信息，请参阅[使用 LINQ (C#)](./data-transformations-with-linq.md) 和 [select 子句](../../../language-reference/keywords/select-clause.md)进行数据转换。</span><span class="sxs-lookup"><span data-stu-id="5d78a-163">For more information, see [Data Transformations with LINQ (C#)](./data-transformations-with-linq.md) and [select clause](../../../language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d78a-164">请参阅</span><span class="sxs-lookup"><span data-stu-id="5d78a-164">See also</span></span>

- [<span data-ttu-id="5d78a-165">LINQ 查询表达式</span><span class="sxs-lookup"><span data-stu-id="5d78a-165">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="5d78a-166">演练：用 C# 编写查询</span><span class="sxs-lookup"><span data-stu-id="5d78a-166">Walkthrough: Writing Queries in C#</span></span>](./walkthrough-writing-queries-linq.md)
- [<span data-ttu-id="5d78a-167">查询关键字 (LINQ)</span><span class="sxs-lookup"><span data-stu-id="5d78a-167">Query Keywords (LINQ)</span></span>](../../../language-reference/keywords/query-keywords.md)
- [<span data-ttu-id="5d78a-168">匿名类型</span><span class="sxs-lookup"><span data-stu-id="5d78a-168">Anonymous Types</span></span>](../../classes-and-structs/anonymous-types.md)

---
title: LINQ 查询简介 (C#)
description: LINQ 为跨各种数据源和格式的数据查询提供了一种一致的模型。 在 LINQ 查询中，始终会用到对象。
ms.date: 07/20/2015
helpviewer_keywords:
- deferred execution [LINQ]
- LINQ, queries
- LINQ, deferred execution
- queries [LINQ], about LINQ queries
ms.assetid: 37895c02-268c-41d5-be39-f7d936fa88a8
ms.openlocfilehash: f81c3f4e355215f1a750a764c617ad47430adc31
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170566"
---
# <a name="introduction-to-linq-queries-c"></a><span data-ttu-id="17b29-104">LINQ 查询简介 (C#)</span><span class="sxs-lookup"><span data-stu-id="17b29-104">Introduction to LINQ Queries (C#)</span></span>

<span data-ttu-id="17b29-105">*查询*是一种从数据源检索数据的表达式。</span><span class="sxs-lookup"><span data-stu-id="17b29-105">A *query* is an expression that retrieves data from a data source.</span></span> <span data-ttu-id="17b29-106">查询通常用专门的查询语言来表示。</span><span class="sxs-lookup"><span data-stu-id="17b29-106">Queries are usually expressed in a specialized query language.</span></span> <span data-ttu-id="17b29-107">随着时间的推移，人们已经为各种数据源开发了不同的语言；例如，用于关系数据库的 SQL 和用于 XML 的 XQuery。</span><span class="sxs-lookup"><span data-stu-id="17b29-107">Different languages have been developed over time for the various types of data sources, for example SQL for relational databases and XQuery for XML.</span></span> <span data-ttu-id="17b29-108">因此，开发人员对于他们必须支持的每种数据源或数据格式，都不得不学习一种新的查询语言。</span><span class="sxs-lookup"><span data-stu-id="17b29-108">Therefore, developers have had to learn a new query language for each type of data source or data format that they must support.</span></span> <span data-ttu-id="17b29-109">LINQ 通过提供处理各种数据源和数据格式的数据的一致模型，简化了这一情况。</span><span class="sxs-lookup"><span data-stu-id="17b29-109">LINQ simplifies this situation by offering a consistent model for working with data across various kinds of data sources and formats.</span></span> <span data-ttu-id="17b29-110">在 LINQ 查询中，始终会用到对象。</span><span class="sxs-lookup"><span data-stu-id="17b29-110">In a LINQ query, you are always working with objects.</span></span> <span data-ttu-id="17b29-111">可以使用相同的基本编码模式来查询和转换 XML 文档、SQL 数据库、ADO.NET 数据集、.NET 集合中的数据以及 LINQ 提供程序可用的任何其他格式的数据。</span><span class="sxs-lookup"><span data-stu-id="17b29-111">You use the same basic coding patterns to query and transform data in XML documents, SQL databases, ADO.NET Datasets, .NET collections, and any other format for which a LINQ provider is available.</span></span>  
  
## <a name="three-parts-of-a-query-operation"></a><span data-ttu-id="17b29-112">查询操作的三个部分</span><span class="sxs-lookup"><span data-stu-id="17b29-112">Three Parts of a Query Operation</span></span>  

 <span data-ttu-id="17b29-113">所有 LINQ 查询操作都由以下三个不同的操作组成：</span><span class="sxs-lookup"><span data-stu-id="17b29-113">All LINQ query operations consist of three distinct actions:</span></span>  
  
1. <span data-ttu-id="17b29-114">获取数据源。</span><span class="sxs-lookup"><span data-stu-id="17b29-114">Obtain the data source.</span></span>  
  
2. <span data-ttu-id="17b29-115">创建查询。</span><span class="sxs-lookup"><span data-stu-id="17b29-115">Create the query.</span></span>  
  
3. <span data-ttu-id="17b29-116">执行查询。</span><span class="sxs-lookup"><span data-stu-id="17b29-116">Execute the query.</span></span>  
  
 <span data-ttu-id="17b29-117">下面的示例演示如何用源代码表示查询操作的三个部分。</span><span class="sxs-lookup"><span data-stu-id="17b29-117">The following example shows how the three parts of a query operation are expressed in source code.</span></span> <span data-ttu-id="17b29-118">为方便起见，此示例将一个整数数组用作数据源；但其中涉及的概念同样适用于其他数据源。</span><span class="sxs-lookup"><span data-stu-id="17b29-118">The example uses an integer array as a data source for convenience; however, the same concepts apply to other data sources also.</span></span> <span data-ttu-id="17b29-119">本主题的其余部分也会引用此示例。</span><span class="sxs-lookup"><span data-stu-id="17b29-119">This example is referred to throughout the rest of this topic.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#1)]  
  
 <span data-ttu-id="17b29-120">下图演示完整的查询操作。</span><span class="sxs-lookup"><span data-stu-id="17b29-120">The following illustration shows the complete query operation.</span></span> <span data-ttu-id="17b29-121">在 LINQ 中，查询的执行不同于查询本身。</span><span class="sxs-lookup"><span data-stu-id="17b29-121">In LINQ, the execution of the query is distinct from the query itself.</span></span> <span data-ttu-id="17b29-122">换句话说，仅通过创建查询变量不会检索到任何数据。</span><span class="sxs-lookup"><span data-stu-id="17b29-122">In other words, you have not retrieved any data just by creating a query variable.</span></span>  
  
 ![完整 LINQ 查询运算的图表。](./media/introduction-to-linq-queries/linq-query-complete-operation.png)  
  
## <a name="the-data-source"></a><span data-ttu-id="17b29-124">数据源</span><span class="sxs-lookup"><span data-stu-id="17b29-124">The Data Source</span></span>  

 <span data-ttu-id="17b29-125">上例中，数据源是一个数组，因此它隐式支持泛型 <xref:System.Collections.Generic.IEnumerable%601> 接口。</span><span class="sxs-lookup"><span data-stu-id="17b29-125">In the previous example, because the data source is an array, it implicitly supports the generic <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="17b29-126">这一事实意味着该数据源可以用 LINQ 进行查询。</span><span class="sxs-lookup"><span data-stu-id="17b29-126">This fact means it can be queried with LINQ.</span></span> <span data-ttu-id="17b29-127">查询在 `foreach` 语句中执行，且 `foreach` 需要 <xref:System.Collections.IEnumerable> 或 <xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="17b29-127">A query is executed in a `foreach` statement, and `foreach` requires <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="17b29-128">支持 <xref:System.Collections.Generic.IEnumerable%601> 或派生接口（如泛型 <xref:System.Linq.IQueryable%601>）的类型称为可查询类型  。</span><span class="sxs-lookup"><span data-stu-id="17b29-128">Types that support <xref:System.Collections.Generic.IEnumerable%601> or a derived interface such as the generic <xref:System.Linq.IQueryable%601> are called *queryable types*.</span></span>  
  
 <span data-ttu-id="17b29-129">可查询类型不需要进行修改或特殊处理就可以用作 LINQ 数据源。</span><span class="sxs-lookup"><span data-stu-id="17b29-129">A queryable type requires no modification or special treatment to serve as a LINQ data source.</span></span> <span data-ttu-id="17b29-130">如果源数据还没有作为可查询类型出现在内存中，则 LINQ 提供程序必须以此方式表示源数据。</span><span class="sxs-lookup"><span data-stu-id="17b29-130">If the source data is not already in memory as a queryable type, the LINQ provider must represent it as such.</span></span> <span data-ttu-id="17b29-131">例如，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 将 XML 文档加载到可查询的 <xref:System.Xml.Linq.XElement> 类型中：</span><span class="sxs-lookup"><span data-stu-id="17b29-131">For example, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] loads an XML document into a queryable <xref:System.Xml.Linq.XElement> type:</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#2)]  
  
 <span data-ttu-id="17b29-132">借助 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]，首先手动或使用 [Visual Studio 中的 LINQ to SQL 工具](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)在设计时创建对象关系映射。</span><span class="sxs-lookup"><span data-stu-id="17b29-132">With [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], you first create an object-relational mapping at design time either manually or by using the [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span> <span data-ttu-id="17b29-133">针对这些对象编写查询，然后由 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 在运行时处理与数据库的通信。</span><span class="sxs-lookup"><span data-stu-id="17b29-133">You write your queries against the objects, and at run-time [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] handles the communication with the database.</span></span> <span data-ttu-id="17b29-134">下例中，`Customers` 表示数据库中的特定表，而查询结果的类型 <xref:System.Linq.IQueryable%601> 派生自 <xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="17b29-134">In the following example, `Customers` represents a specific table in the database, and the type of the query result, <xref:System.Linq.IQueryable%601>, derives from <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
```csharp  
Northwnd db = new Northwnd(@"c:\northwnd.mdf");  
  
// Query for customers in London.  
IQueryable<Customer> custQuery =  
    from cust in db.Customers  
    where cust.City == "London"  
    select cust;  
```  
  
 <span data-ttu-id="17b29-135">有关如何创建特定类型的数据源的详细信息，请参阅各种 LINQ 提供程序的文档。</span><span class="sxs-lookup"><span data-stu-id="17b29-135">For more information about how to create specific types of data sources, see the documentation for the various LINQ providers.</span></span> <span data-ttu-id="17b29-136">但基本规则很简单：LINQ 数据源是支持泛型 <xref:System.Collections.Generic.IEnumerable%601> 接口或从中继承的接口的任意对象。</span><span class="sxs-lookup"><span data-stu-id="17b29-136">However, the basic rule is very simple: a LINQ data source is any object that supports the generic <xref:System.Collections.Generic.IEnumerable%601> interface, or an interface that inherits from it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="17b29-137">支持非泛型 <xref:System.Collections.IEnumerable> 接口的类型（如 <xref:System.Collections.ArrayList>）还可用作 LINQ 数据源。</span><span class="sxs-lookup"><span data-stu-id="17b29-137">Types such as <xref:System.Collections.ArrayList> that support the non-generic <xref:System.Collections.IEnumerable> interface can also be used as a LINQ data source.</span></span> <span data-ttu-id="17b29-138">有关详细信息，请参阅[如何使用 LINQ 查询 ArrayList (C#)](./how-to-query-an-arraylist-with-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="17b29-138">For more information, see [How to query an ArrayList with LINQ (C#)](./how-to-query-an-arraylist-with-linq.md).</span></span>  
  
## <a name="the-query"></a><a name="query"></a> <span data-ttu-id="17b29-139">查询</span><span class="sxs-lookup"><span data-stu-id="17b29-139">The Query</span></span>  

 <span data-ttu-id="17b29-140">查询指定要从数据源中检索的信息。</span><span class="sxs-lookup"><span data-stu-id="17b29-140">The query specifies what information to retrieve from the data source or sources.</span></span> <span data-ttu-id="17b29-141">查询还可以指定在返回这些信息之前如何对其进行排序、分组和结构化。</span><span class="sxs-lookup"><span data-stu-id="17b29-141">Optionally, a query also specifies how that information should be sorted, grouped, and shaped before it is returned.</span></span> <span data-ttu-id="17b29-142">查询存储在查询变量中，并用查询表达式进行初始化。</span><span class="sxs-lookup"><span data-stu-id="17b29-142">A query is stored in a query variable and initialized with a query expression.</span></span> <span data-ttu-id="17b29-143">为使编写查询的工作变得更加容易，C# 引入了新的查询语法。</span><span class="sxs-lookup"><span data-stu-id="17b29-143">To make it easier to write queries, C# has introduced new query syntax.</span></span>  
  
 <span data-ttu-id="17b29-144">上一个示例中的查询从整数数组中返回所有偶数。</span><span class="sxs-lookup"><span data-stu-id="17b29-144">The query in the previous example returns all the even numbers from the integer array.</span></span> <span data-ttu-id="17b29-145">该查询表达式包含三个子句：`from`、`where` 和 `select`。</span><span class="sxs-lookup"><span data-stu-id="17b29-145">The query expression contains three clauses: `from`, `where` and `select`.</span></span> <span data-ttu-id="17b29-146">（如果熟悉 SQL，会注意到这些子句的顺序与 SQL 中的顺序相反。）`from` 子句指定数据源，`where` 子句应用筛选器，`select` 子句指定返回的元素的类型。</span><span class="sxs-lookup"><span data-stu-id="17b29-146">(If you are familiar with SQL, you will have noticed that the ordering of the clauses is reversed from the order in SQL.) The `from` clause specifies the data source, the `where` clause applies the filter, and the `select` clause specifies the type of the returned elements.</span></span> <span data-ttu-id="17b29-147">[语言集成查询 (LINQ) ](../../../linq/index.md)一节中详细讨论了这些子句和其他查询子句。</span><span class="sxs-lookup"><span data-stu-id="17b29-147">These and the other query clauses are discussed in detail in the [Language Integrated Query (LINQ)](../../../linq/index.md) section.</span></span> <span data-ttu-id="17b29-148">目前需要注意的是，在 LINQ 中，查询变量本身不执行任何操作并且不返回任何数据。</span><span class="sxs-lookup"><span data-stu-id="17b29-148">For now, the important point is that in LINQ, the query variable itself takes no action and returns no data.</span></span> <span data-ttu-id="17b29-149">它只是存储在以后某个时刻执行查询时为生成结果而必需的信息。</span><span class="sxs-lookup"><span data-stu-id="17b29-149">It just stores the information that is required to produce the results when the query is executed at some later point.</span></span> <span data-ttu-id="17b29-150">有关在后台如何构造查询的详细信息，请参阅[标准查询运算符概述 (C#)](./standard-query-operators-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="17b29-150">For more information about how queries are constructed behind the scenes, see [Standard Query Operators Overview (C#)](./standard-query-operators-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="17b29-151">还可以使用方法语法来表示查询。</span><span class="sxs-lookup"><span data-stu-id="17b29-151">Queries can also be expressed by using method syntax.</span></span> <span data-ttu-id="17b29-152">有关详细信息，请参阅 [LINQ 中的查询语法和方法语法](./query-syntax-and-method-syntax-in-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="17b29-152">For more information, see [Query Syntax and Method Syntax in LINQ](./query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
## <a name="query-execution"></a><span data-ttu-id="17b29-153">查询执行</span><span class="sxs-lookup"><span data-stu-id="17b29-153">Query Execution</span></span>  
  
### <a name="deferred-execution"></a><span data-ttu-id="17b29-154">延迟执行</span><span class="sxs-lookup"><span data-stu-id="17b29-154">Deferred Execution</span></span>  

 <span data-ttu-id="17b29-155">如前所述，查询变量本身只存储查询命令。</span><span class="sxs-lookup"><span data-stu-id="17b29-155">As stated previously, the query variable itself only stores the query commands.</span></span> <span data-ttu-id="17b29-156">查询的实际执行将推迟到在 `foreach` 语句中循环访问查询变量之后进行。</span><span class="sxs-lookup"><span data-stu-id="17b29-156">The actual execution of the query is deferred until you iterate over the query variable in a `foreach` statement.</span></span> <span data-ttu-id="17b29-157">此概念称为*延迟执行*，下面的示例对此进行了演示：</span><span class="sxs-lookup"><span data-stu-id="17b29-157">This concept is referred to as *deferred execution* and is demonstrated in the following example:</span></span>  
  
 [!code-csharp[csLinqGettingStarted#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#4)]  
  
 <span data-ttu-id="17b29-158">`foreach` 语句也是检索查询结果的地方。</span><span class="sxs-lookup"><span data-stu-id="17b29-158">The `foreach` statement is also where the query results are retrieved.</span></span> <span data-ttu-id="17b29-159">例如，在上一个查询中，迭代变量 `num` 保存了返回的序列中的每个值（一次保存一个值）。</span><span class="sxs-lookup"><span data-stu-id="17b29-159">For example, in the previous query, the iteration variable `num` holds each value (one at a time) in the returned sequence.</span></span>  
  
 <span data-ttu-id="17b29-160">由于查询变量本身从不保存查询结果，因此可以根据需要随意执行查询。</span><span class="sxs-lookup"><span data-stu-id="17b29-160">Because the query variable itself never holds the query results, you can execute it as often as you like.</span></span> <span data-ttu-id="17b29-161">例如，可以通过一个单独的应用程序持续更新数据库。</span><span class="sxs-lookup"><span data-stu-id="17b29-161">For example, you may have a database that is being updated continually by a separate application.</span></span> <span data-ttu-id="17b29-162">在应用程序中，可以创建一个检索最新数据的查询，并可以按某一时间间隔反复执行该查询以便每次检索不同的结果。</span><span class="sxs-lookup"><span data-stu-id="17b29-162">In your application, you could create one query that retrieves the latest data, and you could execute it repeatedly at some interval to retrieve different results every time.</span></span>  
  
### <a name="forcing-immediate-execution"></a><span data-ttu-id="17b29-163">强制立即执行</span><span class="sxs-lookup"><span data-stu-id="17b29-163">Forcing Immediate Execution</span></span>  

 <span data-ttu-id="17b29-164">对一系列源元素执行聚合函数的查询必须首先循环访问这些元素。</span><span class="sxs-lookup"><span data-stu-id="17b29-164">Queries that perform aggregation functions over a range of source elements must first iterate over those elements.</span></span> <span data-ttu-id="17b29-165">`Count`、`Max`、`Average` 和 `First` 就属于此类查询。</span><span class="sxs-lookup"><span data-stu-id="17b29-165">Examples of such queries are `Count`, `Max`, `Average`, and `First`.</span></span> <span data-ttu-id="17b29-166">由于查询本身必须使用 `foreach` 以便返回结果，因此这些查询在执行时不使用显式 `foreach` 语句。</span><span class="sxs-lookup"><span data-stu-id="17b29-166">These execute without an explicit `foreach` statement because the query itself must use `foreach` in order to return a result.</span></span> <span data-ttu-id="17b29-167">另外还要注意，这些类型的查询返回单个值，而不是 `IEnumerable` 集合。</span><span class="sxs-lookup"><span data-stu-id="17b29-167">Note also that these types of queries return a single value, not an `IEnumerable` collection.</span></span> <span data-ttu-id="17b29-168">下面的查询返回源数组中偶数的计数：</span><span class="sxs-lookup"><span data-stu-id="17b29-168">The following query returns a count of the even numbers in the source array:</span></span>  
  
 [!code-csharp[csLinqGettingStarted#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#5)]  
  
 <span data-ttu-id="17b29-169">要强制立即执行任何查询并缓存其结果，可调用 <xref:System.Linq.Enumerable.ToList%2A> 或 <xref:System.Linq.Enumerable.ToArray%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="17b29-169">To force immediate execution of any query and cache its results, you can call the <xref:System.Linq.Enumerable.ToList%2A> or <xref:System.Linq.Enumerable.ToArray%2A> methods.</span></span>  
  
 [!code-csharp[csLinqGettingStarted#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#6)]  
  
 <span data-ttu-id="17b29-170">此外，还可以通过在紧跟查询表达式之后的位置放置一个 `foreach` 循环来强制执行查询。</span><span class="sxs-lookup"><span data-stu-id="17b29-170">You can also force execution by putting the `foreach` loop immediately after the query expression.</span></span> <span data-ttu-id="17b29-171">但是，通过调用 `ToList` 或 `ToArray`，也可以将所有数据缓存在单个集合对象中。</span><span class="sxs-lookup"><span data-stu-id="17b29-171">However, by calling `ToList` or `ToArray` you also cache all the data in a single collection object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17b29-172">请参阅</span><span class="sxs-lookup"><span data-stu-id="17b29-172">See also</span></span>

- [<span data-ttu-id="17b29-173">C# 中的 LINQ 入门</span><span class="sxs-lookup"><span data-stu-id="17b29-173">Getting Started with LINQ in C#</span></span>](index.md)
- [<span data-ttu-id="17b29-174">演练：用 C# 编写查询</span><span class="sxs-lookup"><span data-stu-id="17b29-174">Walkthrough: Writing Queries in C#</span></span>](./walkthrough-writing-queries-linq.md)
- [<span data-ttu-id="17b29-175">语言集成查询 (LINQ)</span><span class="sxs-lookup"><span data-stu-id="17b29-175">Language Integrated Query (LINQ)</span></span>](../../../linq/index.md)
- [<span data-ttu-id="17b29-176">foreach, in</span><span class="sxs-lookup"><span data-stu-id="17b29-176">foreach, in</span></span>](../../../language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="17b29-177">查询关键字 (LINQ)</span><span class="sxs-lookup"><span data-stu-id="17b29-177">Query Keywords (LINQ)</span></span>](../../../language-reference/keywords/query-keywords.md)

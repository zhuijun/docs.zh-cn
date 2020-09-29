---
title: 标准查询运算符概述 (C#)
description: LINQ 标准查询运算符提供包括 C# 中的筛选、投影、聚合和排序在内的查询功能。
ms.date: 07/20/2015
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
ms.openlocfilehash: 1ff98e47641dbe7a884b7d6c7758c1fe61b95091
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178770"
---
# <a name="standard-query-operators-overview-c"></a><span data-ttu-id="44640-103">标准查询运算符概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="44640-103">Standard Query Operators Overview (C#)</span></span>

<span data-ttu-id="44640-104">*标准查询运算符*是组成 LINQ 模式的方法。</span><span class="sxs-lookup"><span data-stu-id="44640-104">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="44640-105">这些方法中的大多数都作用于序列；其中序列指其类型实现 <xref:System.Collections.Generic.IEnumerable%601> 接口或 <xref:System.Linq.IQueryable%601> 接口的对象。</span><span class="sxs-lookup"><span data-stu-id="44640-105">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="44640-106">标准查询运算符提供包括筛选、投影、聚合、排序等在内的查询功能。</span><span class="sxs-lookup"><span data-stu-id="44640-106">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>  
  
 <span data-ttu-id="44640-107">共有两组 LINQ 标准查询运算符，一组作用于类型 <xref:System.Collections.Generic.IEnumerable%601> 的对象，另一组作用于类型 <xref:System.Linq.IQueryable%601> 的对象。</span><span class="sxs-lookup"><span data-stu-id="44640-107">There are two sets of LINQ standard query operators: one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601>, another that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="44640-108">构成每个集合的方法分别是 <xref:System.Linq.Enumerable> 和 <xref:System.Linq.Queryable> 类的静态成员。</span><span class="sxs-lookup"><span data-stu-id="44640-108">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="44640-109">这些方法被定义为作为方法运行目标的类型的*扩展方法*。</span><span class="sxs-lookup"><span data-stu-id="44640-109">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="44640-110">可以使用静态方法语法或实例方法语法来调用扩展方法。</span><span class="sxs-lookup"><span data-stu-id="44640-110">Extension methods can be called by using either static method syntax or instance method syntax.</span></span>  
  
 <span data-ttu-id="44640-111">此外，多个标准查询运算符方法作用于那些基于 <xref:System.Collections.Generic.IEnumerable%601> 或 <xref:System.Linq.IQueryable%601> 的类型外的类型。</span><span class="sxs-lookup"><span data-stu-id="44640-111">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="44640-112"><xref:System.Linq.Enumerable> 类型定义了两种这样的方法，这两种方法都作用于类型 <xref:System.Collections.IEnumerable> 的对象。</span><span class="sxs-lookup"><span data-stu-id="44640-112">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="44640-113">这些方法（<xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> 和 <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>）均允许在 LINQ 模式中查询非参数化或非泛型集合。</span><span class="sxs-lookup"><span data-stu-id="44640-113">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="44640-114">这些方法通过创建一个强类型的对象集合来实现这一点。</span><span class="sxs-lookup"><span data-stu-id="44640-114">They do this by creating a strongly typed collection of objects.</span></span> <span data-ttu-id="44640-115"><xref:System.Linq.Queryable> 类定义了两种类似的方法 <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> 和 <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>，这两种方法都作用于类型 <xref:System.Linq.Queryable> 的对象。</span><span class="sxs-lookup"><span data-stu-id="44640-115">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>  
  
 <span data-ttu-id="44640-116">各个标准查询运算符在执行时间上有所不同，具体情况取决于它们是返回单一值还是值序列。</span><span class="sxs-lookup"><span data-stu-id="44640-116">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="44640-117">返回单一实例值的这些方法（例如 <xref:System.Linq.Enumerable.Average%2A> 和 <xref:System.Linq.Enumerable.Sum%2A>）立即执行。</span><span class="sxs-lookup"><span data-stu-id="44640-117">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="44640-118">返回序列的方法会延迟查询执行，并返回一个可枚举的对象。</span><span class="sxs-lookup"><span data-stu-id="44640-118">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>  
  
 <span data-ttu-id="44640-119">对于在内存中集合上运行的方法（即扩展 <xref:System.Collections.Generic.IEnumerable%601> 的那些方法），返回的可枚举对象将捕获传递到方法的参数。</span><span class="sxs-lookup"><span data-stu-id="44640-119">For methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="44640-120">在枚举该对象时，将使用查询运算符的逻辑，并返回查询结果。</span><span class="sxs-lookup"><span data-stu-id="44640-120">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>  
  
 <span data-ttu-id="44640-121">相反，扩展 <xref:System.Linq.IQueryable%601> 的方法不会实现任何查询行为。</span><span class="sxs-lookup"><span data-stu-id="44640-121">In contrast, methods that extend <xref:System.Linq.IQueryable%601> don't implement any querying behavior.</span></span> <span data-ttu-id="44640-122">它们生成一个表示要执行的查询的表达式树。</span><span class="sxs-lookup"><span data-stu-id="44640-122">They build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="44640-123">源 <xref:System.Linq.IQueryable%601> 对象执行查询处理。</span><span class="sxs-lookup"><span data-stu-id="44640-123">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>  
  
 <span data-ttu-id="44640-124">可以在一个查询中将对查询方法的调用链接在一起，这就使得查询的复杂性可能会变得不确定。</span><span class="sxs-lookup"><span data-stu-id="44640-124">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>  
  
 <span data-ttu-id="44640-125">下面的代码示例演示如何使用标准查询运算符来获取有关序列的信息。</span><span class="sxs-lookup"><span data-stu-id="44640-125">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>  
  
```csharp  
string sentence = "the quick brown fox jumps over the lazy dog";  
// Split the string into individual words to create a collection.  
string[] words = sentence.Split(' ');  
  
// Using query expression syntax.  
var query = from word in words  
            group word.ToUpper() by word.Length into gr  
            orderby gr.Key  
            select new { Length = gr.Key, Words = gr };  
  
// Using method-based query syntax.  
var query2 = words.  
    GroupBy(w => w.Length, w => w.ToUpper()).  
    Select(g => new { Length = g.Key, Words = g }).  
    OrderBy(o => o.Length);  
  
foreach (var obj in query)  
{  
    Console.WriteLine("Words of length {0}:", obj.Length);  
    foreach (string word in obj.Words)  
        Console.WriteLine(word);  
}  
  
// This code example produces the following output:  
//  
// Words of length 3:  
// THE  
// FOX  
// THE  
// DOG  
// Words of length 4:  
// OVER  
// LAZY  
// Words of length 5:  
// QUICK  
// BROWN  
// JUMPS
```  
  
## <a name="query-expression-syntax"></a><span data-ttu-id="44640-126">查询表达式语法</span><span class="sxs-lookup"><span data-stu-id="44640-126">Query Expression Syntax</span></span>  

 <span data-ttu-id="44640-127">某些使用更频繁的标准查询运算符具有专用的 C# 和 Visual Basic 语言关键字语法，使用这些语法可以在“查询表达式”中调用这些运算符 。</span><span class="sxs-lookup"><span data-stu-id="44640-127">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="44640-128">有关具有专用关键字及其对应语法的标准查询运算符的详细信息，请参阅[标准查询运算符的查询表达式语法 (C#)](./query-expression-syntax-for-standard-query-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="44640-128">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (C#)](./query-expression-syntax-for-standard-query-operators.md).</span></span>  
  
## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="44640-129">扩展标准查询运算符</span><span class="sxs-lookup"><span data-stu-id="44640-129">Extending the Standard Query Operators</span></span>  

 <span data-ttu-id="44640-130">通过创建适合于目标域或技术的特定于域的方法，可以增大标准查询运算符的集合。</span><span class="sxs-lookup"><span data-stu-id="44640-130">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="44640-131">也可以用自己的实现来替换标准查询运算符，这些实现提供诸如远程计算、查询转换和优化之类的附加服务。</span><span class="sxs-lookup"><span data-stu-id="44640-131">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="44640-132">有关示例，请参见 <xref:System.Linq.Enumerable.AsEnumerable%2A>。</span><span class="sxs-lookup"><span data-stu-id="44640-132">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="44640-133">相关章节</span><span class="sxs-lookup"><span data-stu-id="44640-133">Related Sections</span></span>  

 <span data-ttu-id="44640-134">通过以下链接可转到一些文章，这些文章基于功能提供有关各种标准查询运算符的附加信息。</span><span class="sxs-lookup"><span data-stu-id="44640-134">The following links take you to articles that provide additional information about the various standard query operators based on functionality.</span></span>  
  
 [<span data-ttu-id="44640-135">对数据进行排序 (C#)</span><span class="sxs-lookup"><span data-stu-id="44640-135">Sorting Data (C#)</span></span>](./sorting-data.md)  
  
 [<span data-ttu-id="44640-136">集运算 (C#)</span><span class="sxs-lookup"><span data-stu-id="44640-136">Set Operations (C#)</span></span>](./set-operations.md)  
  
 [<span data-ttu-id="44640-137">筛选数据 (C#)</span><span class="sxs-lookup"><span data-stu-id="44640-137">Filtering Data (C#)</span></span>](./filtering-data.md)  
  
 [<span data-ttu-id="44640-138">限定符运算 (C#)</span><span class="sxs-lookup"><span data-stu-id="44640-138">Quantifier Operations (C#)</span></span>](./quantifier-operations.md)  
  
 [<span data-ttu-id="44640-139">投影运算 (C#)</span><span class="sxs-lookup"><span data-stu-id="44640-139">Projection Operations (C#)</span></span>](./projection-operations.md)  
  
 [<span data-ttu-id="44640-140">数据分区 (C#)</span><span class="sxs-lookup"><span data-stu-id="44640-140">Partitioning Data (C#)</span></span>](./partitioning-data.md)  
  
 [<span data-ttu-id="44640-141">联接运算 (C#)</span><span class="sxs-lookup"><span data-stu-id="44640-141">Join Operations (C#)</span></span>](./join-operations.md)  
  
 [<span data-ttu-id="44640-142">数据分组 (C#)</span><span class="sxs-lookup"><span data-stu-id="44640-142">Grouping Data (C#)</span></span>](./grouping-data.md)  
  
 [<span data-ttu-id="44640-143">生成运算 (C#)</span><span class="sxs-lookup"><span data-stu-id="44640-143">Generation Operations (C#)</span></span>](./generation-operations.md)  
  
 [<span data-ttu-id="44640-144">相等运算 (C#)</span><span class="sxs-lookup"><span data-stu-id="44640-144">Equality Operations (C#)</span></span>](./equality-operations.md)  
  
 [<span data-ttu-id="44640-145">元素运算 (C#)</span><span class="sxs-lookup"><span data-stu-id="44640-145">Element Operations (C#)</span></span>](./element-operations.md)  
  
 [<span data-ttu-id="44640-146">转换数据类型 (C#)</span><span class="sxs-lookup"><span data-stu-id="44640-146">Converting Data Types (C#)</span></span>](./converting-data-types.md)  
  
 [<span data-ttu-id="44640-147">串联运算 (C#)</span><span class="sxs-lookup"><span data-stu-id="44640-147">Concatenation Operations (C#)</span></span>](./concatenation-operations.md)  
  
 [<span data-ttu-id="44640-148">聚合运算 (C#)</span><span class="sxs-lookup"><span data-stu-id="44640-148">Aggregation Operations (C#)</span></span>](./aggregation-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="44640-149">请参阅</span><span class="sxs-lookup"><span data-stu-id="44640-149">See also</span></span>

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [<span data-ttu-id="44640-150">LINQ 查询简介 (C#)</span><span class="sxs-lookup"><span data-stu-id="44640-150">Introduction to LINQ Queries (C#)</span></span>](./introduction-to-linq-queries.md)
- [<span data-ttu-id="44640-151">标准查询运算符的查询表达式语法 (C#)</span><span class="sxs-lookup"><span data-stu-id="44640-151">Query Expression Syntax for Standard Query Operators (C#)</span></span>](./query-expression-syntax-for-standard-query-operators.md)
- [<span data-ttu-id="44640-152">标准查询运算符按执行方式的分类 (C#)</span><span class="sxs-lookup"><span data-stu-id="44640-152">Classification of Standard Query Operators by Manner of Execution (C#)</span></span>](./classification-of-standard-query-operators-by-manner-of-execution.md)
- [<span data-ttu-id="44640-153">扩展方法</span><span class="sxs-lookup"><span data-stu-id="44640-153">Extension Methods</span></span>](../../classes-and-structs/extension-methods.md)

---
description: from 子句 - C# 参考
title: from 子句 - C# 参考
ms.date: 07/20/2015
f1_keywords:
- from_CSharpKeyword
- from
helpviewer_keywords:
- from clause [C#]
- from keyword [C#]
ms.assetid: 1aefd18c-1314-47f8-99ec-9bcefb09e699
ms.openlocfilehash: 474b22f5a9d8f12c8a4365159817f878761b563c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89140784"
---
# <a name="from-clause-c-reference"></a><span data-ttu-id="f8734-103">from 子句（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="f8734-103">from clause (C# Reference)</span></span>

<span data-ttu-id="f8734-104">查询表达式必须以 `from` 子句开头。</span><span class="sxs-lookup"><span data-stu-id="f8734-104">A query expression must begin with a `from` clause.</span></span> <span data-ttu-id="f8734-105">此外，查询表达式可包含也以 `from` 子句开头的子查询。</span><span class="sxs-lookup"><span data-stu-id="f8734-105">Additionally, a query expression can contain sub-queries, which also begin with a `from` clause.</span></span> <span data-ttu-id="f8734-106">`from` 子句指定下列各项：</span><span class="sxs-lookup"><span data-stu-id="f8734-106">The `from` clause specifies the following:</span></span>

- <span data-ttu-id="f8734-107">将在其上运行查询或子查询的数据源。</span><span class="sxs-lookup"><span data-stu-id="f8734-107">The data source on which the query or sub-query will be run.</span></span>

- <span data-ttu-id="f8734-108">表示源序列中每个元素的本地范围变量\*\*。</span><span class="sxs-lookup"><span data-stu-id="f8734-108">A local *range variable* that represents each element in the source sequence.</span></span>

<span data-ttu-id="f8734-109">范围变量和数据源已强类型化。</span><span class="sxs-lookup"><span data-stu-id="f8734-109">Both the range variable and the data source are strongly typed.</span></span> <span data-ttu-id="f8734-110">`from` 子句中引用的数据源必须具有 <xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601> 类型之一，或 <xref:System.Linq.IQueryable%601> 等派生类型。</span><span class="sxs-lookup"><span data-stu-id="f8734-110">The data source referenced in the `from` clause must have a type of <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, or a derived type such as <xref:System.Linq.IQueryable%601>.</span></span>

<span data-ttu-id="f8734-111">在下面的示例中，`numbers` 是数据源，`num` 是范围变量。</span><span class="sxs-lookup"><span data-stu-id="f8734-111">In the following example, `numbers` is the data source and `num` is the range variable.</span></span> <span data-ttu-id="f8734-112">请注意，这两个变量都已强类型化，即使使用 [var](var.md) 关键字也是如此。</span><span class="sxs-lookup"><span data-stu-id="f8734-112">Note that both variables are strongly typed even though the [var](var.md) keyword is used.</span></span>

[!code-csharp[cscsrefQueryKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#1)]

## <a name="the-range-variable"></a><span data-ttu-id="f8734-113">范围变量</span><span class="sxs-lookup"><span data-stu-id="f8734-113">The range variable</span></span>

<span data-ttu-id="f8734-114">数据源实现 <xref:System.Collections.Generic.IEnumerable%601> 时，编译器推断范围变量的类型。</span><span class="sxs-lookup"><span data-stu-id="f8734-114">The compiler infers the type of the range variable when the data source implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="f8734-115">例如，如果源具有 `IEnumerable<Customer>` 类型，则范围变量会被推断为 `Customer`。</span><span class="sxs-lookup"><span data-stu-id="f8734-115">For example, if the source has a type of `IEnumerable<Customer>`, then the range variable is inferred to be `Customer`.</span></span> <span data-ttu-id="f8734-116">仅在以下情况下必须显式指定类型：源是 <xref:System.Collections.ArrayList> 等非泛型 `IEnumerable` 类型时。</span><span class="sxs-lookup"><span data-stu-id="f8734-116">The only time that you must specify the type explicitly is when the source is a non-generic `IEnumerable` type such as <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="f8734-117">有关详细信息，请参阅[如何使用 LINQ 查询 ArrayList](../../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="f8734-117">For more information, see [How to query an ArrayList with LINQ](../../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).</span></span>

<span data-ttu-id="f8734-118">在以上示例中，`num` 推断为 `int` 类型。</span><span class="sxs-lookup"><span data-stu-id="f8734-118">In the previous example `num` is inferred to be of type `int`.</span></span> <span data-ttu-id="f8734-119">由于强类型化了范围变量，所以可以在其上调用方法，或将其用于其他操作中。</span><span class="sxs-lookup"><span data-stu-id="f8734-119">Because the range variable is strongly typed, you can call methods on it or use it in other operations.</span></span> <span data-ttu-id="f8734-120">例如，不再编写 `select num`，而编写 `select num.ToString()`，使查询表达式返回字符串序列，而不是整数序列。</span><span class="sxs-lookup"><span data-stu-id="f8734-120">For example, instead of writing `select num`, you could write `select num.ToString()` to cause the query expression to return a sequence of strings instead of integers.</span></span> <span data-ttu-id="f8734-121">或者可以编写 `select num + 10`，使表达式返回序列 14、11、13、12、10。</span><span class="sxs-lookup"><span data-stu-id="f8734-121">Or you could write `select num + 10` to cause the expression to return the sequence 14, 11, 13, 12, 10.</span></span> <span data-ttu-id="f8734-122">有关详细信息，请参阅 [select 子句](select-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="f8734-122">For more information, see [select clause](select-clause.md).</span></span>

<span data-ttu-id="f8734-123">范围变量与 [foreach](foreach-in.md) 语句中的迭代变量类似，一项非常重要的区别除外：范围变量从不实际存储来自源的数据。</span><span class="sxs-lookup"><span data-stu-id="f8734-123">The range variable is like an iteration variable in a [foreach](foreach-in.md) statement except for one very important difference: a range variable never actually stores data from the source.</span></span> <span data-ttu-id="f8734-124">它只是一种语法上的便利，让查询能够描述执行查询时将发生的情况。</span><span class="sxs-lookup"><span data-stu-id="f8734-124">It's just a syntactic convenience that enables the query to describe what will occur when the query is executed.</span></span> <span data-ttu-id="f8734-125">有关详细信息，请参阅 [LINQ 查询简介 (C#)](../../programming-guide/concepts/linq/introduction-to-linq-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="f8734-125">For more information, see [Introduction to LINQ Queries (C#)](../../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

## <a name="compound-from-clauses"></a><span data-ttu-id="f8734-126">复合 from 子句</span><span class="sxs-lookup"><span data-stu-id="f8734-126">Compound from clauses</span></span>

<span data-ttu-id="f8734-127">在某些情况下，源序列中的每个元素可能本身就是一个序列，或者包含一个序列。</span><span class="sxs-lookup"><span data-stu-id="f8734-127">In some cases, each element in the source sequence may itself be either a sequence or contain a sequence.</span></span> <span data-ttu-id="f8734-128">例如，数据源可能是 `IEnumerable<Student>`，其中序列中的每个学生对象都包含测试分数的列表。</span><span class="sxs-lookup"><span data-stu-id="f8734-128">For example, your data source may be an `IEnumerable<Student>` where each student object in the sequence contains a list of test scores.</span></span> <span data-ttu-id="f8734-129">要访问每个 `Student` 元素的内部列表，可以使用复合 `from` 子句。</span><span class="sxs-lookup"><span data-stu-id="f8734-129">To access the inner list within each `Student` element, you can use compound `from` clauses.</span></span> <span data-ttu-id="f8734-130">这种方法类似于使用嵌套的 [foreach](foreach-in.md) 语句。</span><span class="sxs-lookup"><span data-stu-id="f8734-130">The technique is like using nested [foreach](foreach-in.md) statements.</span></span> <span data-ttu-id="f8734-131">可以向任一 `from`子句添加 [where](partial-method.md) 或 [orderby](orderby-clause.md) 子句筛选结果。</span><span class="sxs-lookup"><span data-stu-id="f8734-131">You can add [where](partial-method.md) or [orderby](orderby-clause.md) clauses to either `from` clause to filter the results.</span></span> <span data-ttu-id="f8734-132">下面的示例演示 `Student` 对象的序列，其中每个对象都包含一个整数内部 `List`，表示测验分数。</span><span class="sxs-lookup"><span data-stu-id="f8734-132">The following example shows a sequence of `Student` objects, each of which contains an inner `List` of integers representing test scores.</span></span> <span data-ttu-id="f8734-133">访问内部列表可使用复合 `from` 子句。</span><span class="sxs-lookup"><span data-stu-id="f8734-133">To access the inner list, use a compound `from` clause.</span></span> <span data-ttu-id="f8734-134">如有必要，可以在这两个 `from` 子句间插入子句。</span><span class="sxs-lookup"><span data-stu-id="f8734-134">You can insert clauses between the two `from` clauses if necessary.</span></span>

[!code-csharp[cscsrefQueryKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#2)]

## <a name="using-multiple-from-clauses-to-perform-joins"></a><span data-ttu-id="f8734-135">使用多个 from 子句执行联接</span><span class="sxs-lookup"><span data-stu-id="f8734-135">Using Multiple from Clauses to Perform Joins</span></span>

<span data-ttu-id="f8734-136">复合 `from` 子句用于访问单个数据源中的内部集合。</span><span class="sxs-lookup"><span data-stu-id="f8734-136">A compound `from` clause is used to access inner collections in a single data source.</span></span> <span data-ttu-id="f8734-137">但是，查询也可以包含多个 `from` 子句，这些子句从独立的数据源生成补充查询。</span><span class="sxs-lookup"><span data-stu-id="f8734-137">However, a query can also contain multiple `from` clauses that generate supplemental queries from independent data sources.</span></span> <span data-ttu-id="f8734-138">通过此方法，可以执行使用 [join 子句](join-clause.md) 无法实现的某类联接操作。</span><span class="sxs-lookup"><span data-stu-id="f8734-138">This technique enables you to perform certain types of join operations that are not possible by using the [join clause](join-clause.md).</span></span>

<span data-ttu-id="f8734-139">下面的示例演示两个 `from` 子句如何用于形成两个数据源的完全交叉联接。</span><span class="sxs-lookup"><span data-stu-id="f8734-139">The following example shows how two `from` clauses can be used to form a complete cross join of two data sources.</span></span>

[!code-csharp[cscsrefQueryKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#3)]

<span data-ttu-id="f8734-140">若要详细了解使用多个 `from` 子句的联接操作，请参阅[执行左外部联结](../../linq/perform-left-outer-joins.md)。</span><span class="sxs-lookup"><span data-stu-id="f8734-140">For more information about join operations that use multiple `from` clauses, see [Perform left outer joins](../../linq/perform-left-outer-joins.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f8734-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f8734-141">See also</span></span>

- [<span data-ttu-id="f8734-142">查询关键字 (LINQ)</span><span class="sxs-lookup"><span data-stu-id="f8734-142">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="f8734-143">语言集成查询 (LINQ)</span><span class="sxs-lookup"><span data-stu-id="f8734-143">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)

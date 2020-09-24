---
title: FROM (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ff3e3048-0d5d-4502-ae5c-9187fcbd0514
ms.openlocfilehash: 8affac82fb1813aa0282540b5dc2f47d42234a1b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148045"
---
# <a name="from-entity-sql"></a><span data-ttu-id="db788-102">FROM (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="db788-102">FROM (Entity SQL)</span></span>

<span data-ttu-id="db788-103">指定在 [SELECT](select-entity-sql.md) 语句中使用的集合。</span><span class="sxs-lookup"><span data-stu-id="db788-103">Specifies the collection used in [SELECT](select-entity-sql.md) statements.</span></span>

## <a name="syntax"></a><span data-ttu-id="db788-104">语法</span><span class="sxs-lookup"><span data-stu-id="db788-104">Syntax</span></span>

```sql
FROM expression [ ,...n ] AS C
```

## <a name="arguments"></a><span data-ttu-id="db788-105">参数</span><span class="sxs-lookup"><span data-stu-id="db788-105">Arguments</span></span>

`expression` \
<span data-ttu-id="db788-106">任何可生成集合以用作 `SELECT` 语句中的源的有效查询表达式。</span><span class="sxs-lookup"><span data-stu-id="db788-106">Any valid query expression that yields a collection to use as a source in a `SELECT` statement.</span></span>

## <a name="remarks"></a><span data-ttu-id="db788-107">备注</span><span class="sxs-lookup"><span data-stu-id="db788-107">Remarks</span></span>

<span data-ttu-id="db788-108">`FROM` 子句是一个或多个 `FROM` 子句项的逗号分隔列表。</span><span class="sxs-lookup"><span data-stu-id="db788-108">A `FROM` clause is a comma-separated list of one or more `FROM` clause items.</span></span> <span data-ttu-id="db788-109">`FROM` 子句可用来为 `SELECT` 语句指定一个或多个源。</span><span class="sxs-lookup"><span data-stu-id="db788-109">The `FROM` clause can be used to specify one or more sources for a `SELECT` statement.</span></span> <span data-ttu-id="db788-110">`FROM` 子句的最简单形式是单个查询表达式，标识用作 `SELECT` 语句中的源的集合和别名，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="db788-110">The simplest form of a `FROM` clause is a single query expression that identifies a collection and an alias used as the source in a `SELECT` statement, as illustrated in the following example:</span></span>

`FROM C as c`

## <a name="from-clause-items"></a><span data-ttu-id="db788-111">FROM 子句项</span><span class="sxs-lookup"><span data-stu-id="db788-111">FROM Clause Items</span></span>

<span data-ttu-id="db788-112">每个 `FROM` 子句项都引用 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查询中的一个源集合。</span><span class="sxs-lookup"><span data-stu-id="db788-112">Each `FROM` clause item refers to a source collection in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="db788-113">支持 `FROM` 子句项的以下类：简单的 `FROM` 子句项、`JOIN FROM` 子句项和 `APPLY FROM` 子句项。</span><span class="sxs-lookup"><span data-stu-id="db788-113">supports the following classes of `FROM` clause items: simple `FROM` clause items, `JOIN FROM` clause items, and `APPLY FROM` clause items.</span></span> <span data-ttu-id="db788-114">下面几节将对这些 `FROM` 子句项逐一进行更详细地介绍。</span><span class="sxs-lookup"><span data-stu-id="db788-114">Each of these `FROM` clause items is described in more detail in the following sections.</span></span>

### <a name="simple-from-clause-item"></a><span data-ttu-id="db788-115">简单 FROM 子句项</span><span class="sxs-lookup"><span data-stu-id="db788-115">Simple FROM Clause Item</span></span>

<span data-ttu-id="db788-116">最简单的 `FROM` 子句项是标识一个集合和一个别名的单个表达式。</span><span class="sxs-lookup"><span data-stu-id="db788-116">The simplest `FROM` clause item is a single expression that identifies a collection and an alias.</span></span> <span data-ttu-id="db788-117">表达式可以只是实体集或子查询，或任何其他类型为集合的表达式。</span><span class="sxs-lookup"><span data-stu-id="db788-117">The expression can simply be an entity set, or a subquery, or any other expression that is a collection type.</span></span> <span data-ttu-id="db788-118">以下是一个示例：</span><span class="sxs-lookup"><span data-stu-id="db788-118">The following is an example:</span></span>

```sql
LOB.Customers as c
```

<span data-ttu-id="db788-119">别名规范是可选的。</span><span class="sxs-lookup"><span data-stu-id="db788-119">The alias specification is optional.</span></span> <span data-ttu-id="db788-120">上面的 From 子句项的备选规范可以是：</span><span class="sxs-lookup"><span data-stu-id="db788-120">An alternate specification of the above from clause item could be the following:</span></span>

```sql
LOB.Customers
```

<span data-ttu-id="db788-121">如果未指定别名，[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 会尝试根据集合表达式生成别名。</span><span class="sxs-lookup"><span data-stu-id="db788-121">If no alias is specified, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias based on the collection expression.</span></span>

### <a name="join-from-clause-item"></a><span data-ttu-id="db788-122">JOIN FROM 子句项</span><span class="sxs-lookup"><span data-stu-id="db788-122">JOIN FROM Clause Item</span></span>

<span data-ttu-id="db788-123">`JOIN FROM` 子句项表示两个 `FROM` 子句项之间的联接。</span><span class="sxs-lookup"><span data-stu-id="db788-123">A `JOIN FROM` clause item represents a join between two `FROM` clause items.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="db788-124">支持交叉联接、内部联接、左右外部联接和完全外部联接。</span><span class="sxs-lookup"><span data-stu-id="db788-124">supports cross joins, inner joins, left and right outer joins, and full outer joins.</span></span> <span data-ttu-id="db788-125">支持所有这些联接，这与在 Transact-sql 中受支持的方式相似。</span><span class="sxs-lookup"><span data-stu-id="db788-125">All these joins are supported similar to the way that they are supported in Transact-SQL.</span></span> <span data-ttu-id="db788-126">与 Transact-sql 一样，中涉及的两个 `FROM` 子句项 `JOIN` 必须是独立的。</span><span class="sxs-lookup"><span data-stu-id="db788-126">As in Transact-SQL, the two `FROM` clause items involved in the `JOIN` must be independent.</span></span> <span data-ttu-id="db788-127">即，它们不能相关。</span><span class="sxs-lookup"><span data-stu-id="db788-127">That is, they cannot be correlated.</span></span> <span data-ttu-id="db788-128">`CROSS APPLY` 或 `OUTER APPLY` 可用于这些情况。</span><span class="sxs-lookup"><span data-stu-id="db788-128">A `CROSS APPLY` or `OUTER APPLY` can be used for these cases.</span></span>

#### <a name="cross-joins"></a><span data-ttu-id="db788-129">交叉联接</span><span class="sxs-lookup"><span data-stu-id="db788-129">Cross Joins</span></span>

<span data-ttu-id="db788-130">`CROSS JOIN` 查询表达式生成两个集合的笛卡儿积，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="db788-130">A `CROSS JOIN` query expression produces the Cartesian product of the two collections, as illustrated in the following example:</span></span>

`FROM C AS c CROSS JOIN D as d`

#### <a name="inner-joins"></a><span data-ttu-id="db788-131">内部联接</span><span class="sxs-lookup"><span data-stu-id="db788-131">Inner Joins</span></span>

<span data-ttu-id="db788-132">`INNER JOIN` 生成两个集合的约束笛卡儿积，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="db788-132">An `INNER JOIN` produces a constrained Cartesian product of the two collections, as illustrated in the following example:</span></span>

`FROM C AS c [INNER] JOIN D AS d ON e`

<span data-ttu-id="db788-133">前面的查询表达式将 `ON` 条件为 true 的每一个左侧集合元素与其右侧集合的配对元素组合起来。</span><span class="sxs-lookup"><span data-stu-id="db788-133">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="db788-134">如果未指定 `ON` 条件，则 `INNER JOIN` 退化为 `CROSS JOIN`。</span><span class="sxs-lookup"><span data-stu-id="db788-134">If no `ON` condition is specified, an `INNER JOIN` degenerates to a `CROSS JOIN`.</span></span>

#### <a name="left-outer-joins-and-right-outer-joins"></a><span data-ttu-id="db788-135">左外部联接和右外部联接</span><span class="sxs-lookup"><span data-stu-id="db788-135">Left Outer Joins and Right Outer Joins</span></span>

<span data-ttu-id="db788-136">`OUTER JOIN` 查询表达式生成两个集合的约束笛卡儿积，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="db788-136">An `OUTER JOIN` query expression produces a constrained Cartesian product of the two collections, as illustrated in the following example:</span></span>

`FROM C AS c LEFT OUTER JOIN D AS d ON e`

<span data-ttu-id="db788-137">前面的查询表达式将 `ON` 条件为 true 的每一个左侧集合元素与其右侧集合的配对元素组合起来。</span><span class="sxs-lookup"><span data-stu-id="db788-137">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="db788-138">如果 `ON` 条件为 false，表达式仍处理与右侧元素（值为 null）配对的单个左侧元素实例。</span><span class="sxs-lookup"><span data-stu-id="db788-138">If the `ON` condition is false, the expression still processes a single instance of the element on the left paired against the element on the right, with the value null.</span></span>

<span data-ttu-id="db788-139">`RIGHT OUTER JOIN` 可以以类似方式表示。</span><span class="sxs-lookup"><span data-stu-id="db788-139">A `RIGHT OUTER JOIN` may be expressed in a similar manner.</span></span>

#### <a name="full-outer-joins"></a><span data-ttu-id="db788-140">完全外部联接</span><span class="sxs-lookup"><span data-stu-id="db788-140">Full Outer Joins</span></span>

<span data-ttu-id="db788-141">显式 `FULL OUTER JOIN` 生成两个集合的约束笛卡儿积，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="db788-141">An explicit `FULL OUTER JOIN` produces a constrained Cartesian product of the two collections as illustrated in the following example:</span></span>

`FROM C AS c FULL OUTER JOIN D AS d ON e`

<span data-ttu-id="db788-142">前面的查询表达式将 `ON` 条件为 true 的每一个左侧集合元素与其右侧集合的配对元素组合起来。</span><span class="sxs-lookup"><span data-stu-id="db788-142">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="db788-143">如果 `ON` 条件为 false，表达式仍处理与右侧元素（值为 null）配对的一个左侧元素实例。</span><span class="sxs-lookup"><span data-stu-id="db788-143">If the `ON` condition is false, the expression still processes one instance of the element on the left paired against the element on the right, with the value null.</span></span> <span data-ttu-id="db788-144">此外，它还处理与左侧元素（值为 null）配对的一个左侧元素实例。</span><span class="sxs-lookup"><span data-stu-id="db788-144">It also processes one instance of the element on the right paired against the element on the left, with the value null.</span></span>

> [!NOTE]
> <span data-ttu-id="db788-145">为了保持与 SQL-92 的兼容性，在 Transact-sql 中，OUTER 关键字是可选的。</span><span class="sxs-lookup"><span data-stu-id="db788-145">To preserve compatibility with SQL-92, in Transact-SQL the OUTER keyword is optional.</span></span> <span data-ttu-id="db788-146">因此 `LEFT JOIN`、`RIGHT JOIN` 和 `FULL JOIN` 是 `LEFT OUTER JOIN`、`RIGHT OUTER JOIN` 和 `FULL OUTER JOIN` 的同义词。</span><span class="sxs-lookup"><span data-stu-id="db788-146">Therefore, `LEFT JOIN`, `RIGHT JOIN`, and `FULL JOIN` are synonyms for `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, and `FULL OUTER JOIN`.</span></span>

### <a name="apply-clause-item"></a><span data-ttu-id="db788-147">APPLY 子句项</span><span class="sxs-lookup"><span data-stu-id="db788-147">APPLY Clause Item</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="db788-148">支持两种 `APPLY`：`CROSS APPLY` 和 `OUTER APPLY`。</span><span class="sxs-lookup"><span data-stu-id="db788-148">supports two kinds of `APPLY`: `CROSS APPLY` and `OUTER APPLY`.</span></span>

<span data-ttu-id="db788-149">`CROSS APPLY` 生成左侧集合的每个元素与通过计算右侧表达式得出的集合的元素的唯一配对。</span><span class="sxs-lookup"><span data-stu-id="db788-149">A `CROSS APPLY` produces a unique pairing of each element of the collection on the left with an element of the collection produced by evaluating the expression on the right.</span></span> <span data-ttu-id="db788-150">利用 `CROSS APPLY`，右侧表达式在功能上依赖于左侧元素，如下面的关联集合示例所示：</span><span class="sxs-lookup"><span data-stu-id="db788-150">With a `CROSS APPLY`, the expression on the right is functionally dependent on the element on the left, as illustrated in the following associated collection example:</span></span>

`SELECT c, f FROM C AS c CROSS APPLY c.Assoc AS f`

<span data-ttu-id="db788-151">`CROSS APPLY` 的行为与联接列表类似。</span><span class="sxs-lookup"><span data-stu-id="db788-151">The behavior of `CROSS APPLY` is similar to the join list.</span></span> <span data-ttu-id="db788-152">如果右侧表达式的计算结果为空集合，则 `CROSS APPLY` 不生成左侧元素实例的配对。</span><span class="sxs-lookup"><span data-stu-id="db788-152">If the expression on the right evaluates to an empty collection, the `CROSS APPLY` produces no pairings for that instance of the element on the left.</span></span>

<span data-ttu-id="db788-153">`OUTER APPLY` 与 `CROSS APPLY` 类似，区别在于当右侧表达式计算结果为空集合时，仍然生成配对。</span><span class="sxs-lookup"><span data-stu-id="db788-153">An `OUTER APPLY` resembles a `CROSS APPLY`, except a pairing is still produced even when the expression on the right evaluates to an empty collection.</span></span> <span data-ttu-id="db788-154">下面是一个 `OUTER APPLY` 的示例：</span><span class="sxs-lookup"><span data-stu-id="db788-154">The following is an example of an `OUTER APPLY`:</span></span>

`SELECT c, f FROM C AS c OUTER APPLY c.Assoc AS f`

> [!NOTE]
> <span data-ttu-id="db788-155">与 Transact-sql 不同，中不需要显式 unnest 步骤 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="db788-155">Unlike in Transact-SQL, there is no need for an explicit unnest step in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

> [!NOTE]
> <span data-ttu-id="db788-156">`CROSS` 和 `OUTER APPLY` 运算符是在 SQL Server 2005 中引入的。</span><span class="sxs-lookup"><span data-stu-id="db788-156">`CROSS` and `OUTER APPLY` operators were introduced in SQL Server 2005.</span></span> <span data-ttu-id="db788-157">在某些情况下，查询管道可能生成包含 `CROSS APPLY` 和/或 `OUTER APPLY` 运算符的 Transact-SQL。</span><span class="sxs-lookup"><span data-stu-id="db788-157">In some cases, the query pipeline might produce Transact-SQL that contains `CROSS APPLY` and/or `OUTER APPLY` operators.</span></span> <span data-ttu-id="db788-158">因为某些后端提供程序（包括早于 SQL Server 2005 的 SQL Server 版本）不支持这些运算符，所以不能对这些后端提供程序执行此类查询。</span><span class="sxs-lookup"><span data-stu-id="db788-158">Because some backend providers, including versions of SQL Server earlier than SQL Server 2005, do not support these operators, such queries cannot be executed on these backend providers.</span></span>
>
> <span data-ttu-id="db788-159">下面是一些可能导致输出查询中出现 `CROSS APPLY` 和/或 `OUTER APPLY`运算符的典型情况：分页相关子查询；相关子查询或导航所生成的集合上的 AnyElement；使用接受元素选择器的分组方法的 LINQ 查询；显式指定 `CROSS APPLY` 或 `OUTER APPLY` 的查询；在 `DEREF` 构造上具有 `REF` 构造的查询。</span><span class="sxs-lookup"><span data-stu-id="db788-159">Some typical scenarios that might lead to the presence of `CROSS APPLY` and/or `OUTER APPLY` operators in the output query are the following: a correlated subquery with paging; AnyElement over a correlated subquery or over a collection produced by navigation; LINQ queries that use grouping methods that accept an element selector; a query in which a `CROSS APPLY` or an `OUTER APPLY` are explicitly specified; a query that has a `DEREF` construct over a `REF` construct.</span></span>

## <a name="multiple-collections-in-the-from-clause"></a><span data-ttu-id="db788-160">FROM 子句中的多个集合</span><span class="sxs-lookup"><span data-stu-id="db788-160">Multiple Collections in the FROM Clause</span></span>

<span data-ttu-id="db788-161">`FROM` 子句不能包含逗号分隔的多个集合。</span><span class="sxs-lookup"><span data-stu-id="db788-161">The `FROM` clause can contain more than one collection separated by commas.</span></span> <span data-ttu-id="db788-162">在这些情况下，假定集合将联接在一起。</span><span class="sxs-lookup"><span data-stu-id="db788-162">In these cases, the collections are assumed to be joined together.</span></span> <span data-ttu-id="db788-163">将它们视为一个 n 向 CROSS JOIN。</span><span class="sxs-lookup"><span data-stu-id="db788-163">Think of these as an n-way CROSS JOIN.</span></span>

<span data-ttu-id="db788-164">在下面的示例中， `C` 和 `D` 是独立集合，但 `c.Names` 依赖于 `C` 。</span><span class="sxs-lookup"><span data-stu-id="db788-164">In the following example, `C` and `D` are independent collections, but `c.Names` is dependent on `C`.</span></span>

```sql
FROM C AS c, D AS d, c.Names AS e
```

<span data-ttu-id="db788-165">下面的示例与前面的示例在逻辑上是等效的：</span><span class="sxs-lookup"><span data-stu-id="db788-165">The previous example is logically equivalent to the following example:</span></span>

`FROM (C AS c JOIN D AS d) CROSS APPLY c.Names AS e`

## <a name="left-correlation"></a><span data-ttu-id="db788-166">左相关</span><span class="sxs-lookup"><span data-stu-id="db788-166">Left Correlation</span></span>

 <span data-ttu-id="db788-167">`FROM` 子句中的项可以引用前面子句中指定的项。</span><span class="sxs-lookup"><span data-stu-id="db788-167">Items in the `FROM` clause can refer to items specified in earlier clauses.</span></span> <span data-ttu-id="db788-168">在下面的示例中，`C` 和 `D` 是独立集合，但 `c.Names` 依赖于 `C`：</span><span class="sxs-lookup"><span data-stu-id="db788-168">In the following example, `C` and `D` are independent collections, but `c.Names` is dependent on `C`:</span></span>

```sql
from C as c, D as d, c.Names as e
```

<span data-ttu-id="db788-169">这在逻辑上等效于：</span><span class="sxs-lookup"><span data-stu-id="db788-169">This is logically equivalent to:</span></span>

```sql
from (C as c join D as d) cross apply c.Names as e
```

## <a name="semantics"></a><span data-ttu-id="db788-170">语义</span><span class="sxs-lookup"><span data-stu-id="db788-170">Semantics</span></span>

<span data-ttu-id="db788-171">在逻辑上，`FROM` 子句中的集合假定为 `n` 向交叉联接的一部分（1 向交叉联接除外）。</span><span class="sxs-lookup"><span data-stu-id="db788-171">Logically, the collections in the `FROM` clause are assumed to be part of an `n`-way cross join (except in the case of a 1-way cross join).</span></span> <span data-ttu-id="db788-172">`FROM` 子句中的别名是从左到右处理的，它们被添加到当前范围供以后引用。</span><span class="sxs-lookup"><span data-stu-id="db788-172">Aliases in the `FROM` clause are processed left to right, and are added to the current scope for later reference.</span></span> <span data-ttu-id="db788-173">`FROM` 子句假定生成行的多重集。</span><span class="sxs-lookup"><span data-stu-id="db788-173">The `FROM` clause is assumed to produce a multiset of rows.</span></span> <span data-ttu-id="db788-174">`FROM` 子句中的每一项都有一个字段，表示该集合项中的单个元素。</span><span class="sxs-lookup"><span data-stu-id="db788-174">There will be one field for each item in the `FROM` clause that represents a single element from that collection item.</span></span>

<span data-ttu-id="db788-175">在逻辑上，`FROM` 子句生成类型为 Row(c, d, e) 的行多重集，其中字段 c、d 和 e 假定为元素类型 `C`、`D` 和 `c.Names`。</span><span class="sxs-lookup"><span data-stu-id="db788-175">The `FROM` clause logically produces a multiset of rows of type Row(c, d, e) where fields c, d, and e are assumed to be of the element type of `C`, `D`, and `c.Names`.</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="db788-176">为范围中的每个简单 `FROM` 子句项都引入一个别名。</span><span class="sxs-lookup"><span data-stu-id="db788-176">introduces an alias for each simple `FROM` clause item in scope.</span></span> <span data-ttu-id="db788-177">例如，在下面的 FROM 子句代码段中，引入范围的名称为 c、d 和 e。</span><span class="sxs-lookup"><span data-stu-id="db788-177">For example, in the following FROM clause snippet, The names introduced into scope are c, d, and e.</span></span>

```sql
from (C as c join D as d) cross apply c.Names as e
```

<span data-ttu-id="db788-178">在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (与 transact-sql) 不同， `FROM` 子句仅将别名引入作用域。</span><span class="sxs-lookup"><span data-stu-id="db788-178">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (unlike Transact-SQL), the `FROM` clause only introduces the aliases into scope.</span></span> <span data-ttu-id="db788-179">任何对这些集合的列（属性）的引用都必须以别名进行限定。</span><span class="sxs-lookup"><span data-stu-id="db788-179">Any references to columns (properties) of these collections must be qualified with the alias.</span></span>

## <a name="pulling-up-keys-from-nested-queries"></a><span data-ttu-id="db788-180">从嵌套查询中拉取键</span><span class="sxs-lookup"><span data-stu-id="db788-180">Pulling Up Keys from Nested Queries</span></span>

<span data-ttu-id="db788-181">某些需要从嵌套查询提取键的查询类型不受支持。</span><span class="sxs-lookup"><span data-stu-id="db788-181">Certain types of queries that require pulling up keys from a nested query are not supported.</span></span> <span data-ttu-id="db788-182">例如，下面的查询是有效的：</span><span class="sxs-lookup"><span data-stu-id="db788-182">For example, the following query is valid:</span></span>

```sql
select c.Orders from Customers as c
```

<span data-ttu-id="db788-183">但是，下面的查询无效，因为该嵌套查询没有任何键：</span><span class="sxs-lookup"><span data-stu-id="db788-183">However, the following query is not valid, because the nested query does not have any keys:</span></span>

```sql
select {1} from {2, 3}
```

## <a name="see-also"></a><span data-ttu-id="db788-184">请参阅</span><span class="sxs-lookup"><span data-stu-id="db788-184">See also</span></span>

- [<span data-ttu-id="db788-185">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="db788-185">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="db788-186">查询表达式</span><span class="sxs-lookup"><span data-stu-id="db788-186">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="db788-187">可以为 NULL 的结构化类型</span><span class="sxs-lookup"><span data-stu-id="db788-187">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)

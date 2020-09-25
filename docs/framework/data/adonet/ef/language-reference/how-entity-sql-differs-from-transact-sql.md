---
title: Entity SQL 与 Transact-SQL 有何不同
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 9433e7a7ffdc3a7e32900981dca95eefde32f290
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204432"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="5527d-102">实体 SQL 与 Transact-sql 的区别</span><span class="sxs-lookup"><span data-stu-id="5527d-102">How Entity SQL differs from Transact-SQL</span></span>

<span data-ttu-id="5527d-103">本文介绍实体 SQL 和 Transact-sql 之间的差异。</span><span class="sxs-lookup"><span data-stu-id="5527d-103">This article describes the differences between Entity SQL and Transact-SQL.</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="5527d-104">继承和关系支持</span><span class="sxs-lookup"><span data-stu-id="5527d-104">Inheritance and Relationships Support</span></span>  

 <span data-ttu-id="5527d-105">实体 SQL 可直接处理概念实体架构，并支持诸如继承和关系等概念模型功能。</span><span class="sxs-lookup"><span data-stu-id="5527d-105">Entity SQL works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="5527d-106">使用继承时，从父类型实例集合中选择子类型的实例通常是有用的。</span><span class="sxs-lookup"><span data-stu-id="5527d-106">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="5527d-107">实体 SQL 中的 [oftype](oftype-entity-sql.md) 运算符与 c # 序列中 (类似， `oftype`) 提供此功能。</span><span class="sxs-lookup"><span data-stu-id="5527d-107">The [oftype](oftype-entity-sql.md) operator in Entity SQL (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="5527d-108">集合支持</span><span class="sxs-lookup"><span data-stu-id="5527d-108">Support for Collections</span></span>  

 <span data-ttu-id="5527d-109">实体 SQL 将集合视为第一类实体。</span><span class="sxs-lookup"><span data-stu-id="5527d-109">Entity SQL treats collections as first-class entities.</span></span> <span data-ttu-id="5527d-110">例如：</span><span class="sxs-lookup"><span data-stu-id="5527d-110">For example:</span></span>  
  
- <span data-ttu-id="5527d-111">集合表达式在 `from` 子句中有效。</span><span class="sxs-lookup"><span data-stu-id="5527d-111">Collection expressions are valid in a `from` clause.</span></span>  
  
- <span data-ttu-id="5527d-112">`in` 和 `exists` 子查询已被一般化，以允许使用任何集合。</span><span class="sxs-lookup"><span data-stu-id="5527d-112">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="5527d-113">子查询是一种集合。</span><span class="sxs-lookup"><span data-stu-id="5527d-113">A subquery is one kind of collection.</span></span> <span data-ttu-id="5527d-114">`e1 in e2` 和 `exists(e)` 是用于执行这些操作的实体 SQL 构造。</span><span class="sxs-lookup"><span data-stu-id="5527d-114">`e1 in e2` and `exists(e)` are the Entity SQL constructs to perform these operations.</span></span>  
  
- <span data-ttu-id="5527d-115">集运算（例如 `union`、`intersect` 和 `except`）现在对集合执行运算。</span><span class="sxs-lookup"><span data-stu-id="5527d-115">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
- <span data-ttu-id="5527d-116">联接对集合执行运算。</span><span class="sxs-lookup"><span data-stu-id="5527d-116">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="5527d-117">对表达式的支持</span><span class="sxs-lookup"><span data-stu-id="5527d-117">Support for Expressions</span></span>  

 <span data-ttu-id="5527d-118">Transact-sql 具有 (表的子查询) 和 (行和列的表达式) 。</span><span class="sxs-lookup"><span data-stu-id="5527d-118">Transact-SQL has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="5527d-119">为了支持集合和嵌套集合，实体 SQL 使所有内容成为表达式。</span><span class="sxs-lookup"><span data-stu-id="5527d-119">To support collections and nested collections, Entity SQL makes everything an expression.</span></span> <span data-ttu-id="5527d-120">实体 SQL 比 Transact-sql 更具可组合，则每个表达式都可在任何地方使用。</span><span class="sxs-lookup"><span data-stu-id="5527d-120">Entity SQL is more composable than Transact-SQL—every expression can be used anywhere.</span></span> <span data-ttu-id="5527d-121">查询表达式总是产生投影类型的集合，并且可以在允许使用集合表达式的任何地方使用。</span><span class="sxs-lookup"><span data-stu-id="5527d-121">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="5527d-122">有关实体 SQL 中不支持的 Transact-sql 表达式的信息，请参阅不支持的 [表达式](unsupported-expressions-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="5527d-122">For information about Transact-SQL expressions that are not supported in Entity SQL, see [Unsupported Expressions](unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="5527d-123">下面是所有有效的实体 SQL 查询：</span><span class="sxs-lookup"><span data-stu-id="5527d-123">The following are all valid Entity SQL queries:</span></span>  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="5527d-124">子查询统一处理</span><span class="sxs-lookup"><span data-stu-id="5527d-124">Uniform Treatment of Subqueries</span></span>  

 <span data-ttu-id="5527d-125">考虑到其对表的关注，Transact-sql 会对子查询执行上下文解释。</span><span class="sxs-lookup"><span data-stu-id="5527d-125">Given its emphasis on tables, Transact-SQL performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="5527d-126">例如，`from` 子句中的子查询被视为多集（表）。</span><span class="sxs-lookup"><span data-stu-id="5527d-126">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="5527d-127">但是，`select` 子句中使用的同一子查询被视为标量子查询。</span><span class="sxs-lookup"><span data-stu-id="5527d-127">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="5527d-128">同样，运算符左侧使用的子查询被 `in` 视为标量子查询，而右侧应为多集子查询。</span><span class="sxs-lookup"><span data-stu-id="5527d-128">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 <span data-ttu-id="5527d-129">实体 SQL 消除了这些差异。</span><span class="sxs-lookup"><span data-stu-id="5527d-129">Entity SQL eliminates these differences.</span></span> <span data-ttu-id="5527d-130">表达式具有不依赖于使用它的上下文的统一解释。</span><span class="sxs-lookup"><span data-stu-id="5527d-130">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> <span data-ttu-id="5527d-131">实体 SQL 将所有子查询视为多集子查询。</span><span class="sxs-lookup"><span data-stu-id="5527d-131">Entity SQL considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="5527d-132">如果需要从子查询中使用标量值，实体 SQL 将提供对 `anyelement` 集合进行操作 (在此例中，子查询) ，并从集合中提取单一实例值。</span><span class="sxs-lookup"><span data-stu-id="5527d-132">If a scalar value is desired from the subquery, Entity SQL provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="5527d-133">避免对子查询执行隐式强制转换</span><span class="sxs-lookup"><span data-stu-id="5527d-133">Avoiding Implicit Coercions for Subqueries</span></span>  

 <span data-ttu-id="5527d-134">与统一处理子查询相关的一个副作用是将子查询隐式转换为标量值。</span><span class="sxs-lookup"><span data-stu-id="5527d-134">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="5527d-135">具体而言，在 Transact-sql 中，与单个字段)  (的行多重集将隐式转换为其数据类型为该字段的数据类型的标量值。</span><span class="sxs-lookup"><span data-stu-id="5527d-135">Specifically, in Transact-SQL, a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 <span data-ttu-id="5527d-136">实体 SQL 不支持此隐式强制。</span><span class="sxs-lookup"><span data-stu-id="5527d-136">Entity SQL does not support this implicit coercion.</span></span> <span data-ttu-id="5527d-137">实体 SQL 提供 `ANYELEMENT` 运算符来从集合中提取单一实例值，并提供 `select value` 子句以避免在查询表达式中创建行包装器。</span><span class="sxs-lookup"><span data-stu-id="5527d-137">Entity SQL provides the `ANYELEMENT` operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="5527d-138">Select Value：避免隐式行包装</span><span class="sxs-lookup"><span data-stu-id="5527d-138">Select Value: Avoiding the Implicit Row Wrapper</span></span>  

 <span data-ttu-id="5527d-139">Transact-sql 子查询中的 select 子句会在子句中的项的周围隐式创建行包装。</span><span class="sxs-lookup"><span data-stu-id="5527d-139">The select clause in a Transact-SQL subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="5527d-140">这意味着我们无法创建标量或对象的集合。</span><span class="sxs-lookup"><span data-stu-id="5527d-140">This implies that we cannot create collections of scalars or objects.</span></span> <span data-ttu-id="5527d-141">Transact-sql 允许在 `rowtype` 具有一个字段和相同数据类型的单一实例值之间进行隐式强制转换。</span><span class="sxs-lookup"><span data-stu-id="5527d-141">Transact-SQL allows an implicit coercion between a `rowtype` with one field and a singleton value of the same data type.</span></span>  
  
 <span data-ttu-id="5527d-142">实体 SQL 提供了 `select value` 子句来跳过隐式行构造。</span><span class="sxs-lookup"><span data-stu-id="5527d-142">Entity SQL provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="5527d-143">在 `select value` 子句中只能指定一个项。</span><span class="sxs-lookup"><span data-stu-id="5527d-143">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="5527d-144">使用这样的子句时，不会围绕子句中的项构造行包装器 `select` ，并且可能生成所需形状的集合，例如 `select value a` 。</span><span class="sxs-lookup"><span data-stu-id="5527d-144">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example, `select value a`.</span></span>  
  
 <span data-ttu-id="5527d-145">实体 SQL 还提供了用于构造任意行的行构造函数。</span><span class="sxs-lookup"><span data-stu-id="5527d-145">Entity SQL also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="5527d-146">`select` 采用投影中的一个或多个元素，并生成包含字段的数据记录：</span><span class="sxs-lookup"><span data-stu-id="5527d-146">`select` takes one or more elements in the projection and results in a data record with fields:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="5527d-147">左相关与别名化</span><span class="sxs-lookup"><span data-stu-id="5527d-147">Left Correlation and Aliasing</span></span>  

 <span data-ttu-id="5527d-148">在 Transact-sql 中，给定作用域中的表达式 (或) 的单个 `select` 子句 `from` 不能引用前面在同一范围内定义的表达式。</span><span class="sxs-lookup"><span data-stu-id="5527d-148">In Transact-SQL, expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="5527d-149">SQL (的一些方言（包括 Transact-sql) ）支持子句中的有限形式 `from` 。</span><span class="sxs-lookup"><span data-stu-id="5527d-149">Some dialects of SQL (including Transact-SQL) do support limited forms of these in the `from` clause.</span></span>  
  
 <span data-ttu-id="5527d-150">实体 SQL 通用化中的左关联 `from` ，并统一对待它们。</span><span class="sxs-lookup"><span data-stu-id="5527d-150">Entity SQL generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="5527d-151">`from` 子句中的表达式无需使用额外的语法，即可引用同一子句中先前的定义（位于左侧的定义）。</span><span class="sxs-lookup"><span data-stu-id="5527d-151">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 <span data-ttu-id="5527d-152">实体 SQL 还对涉及子句的查询施加了额外限制 `group by` 。</span><span class="sxs-lookup"><span data-stu-id="5527d-152">Entity SQL also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="5527d-153">此类查询的 `select` 子句和 `having` 子句中的表达式只能通过其别名引用 `group by` 关键字。</span><span class="sxs-lookup"><span data-stu-id="5527d-153">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="5527d-154">以下构造在 Transact-sql 中有效，但不在实体 SQL 中：</span><span class="sxs-lookup"><span data-stu-id="5527d-154">The following construct is valid in Transact-SQL but are not in Entity SQL:</span></span>  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 <span data-ttu-id="5527d-155">若要在实体 SQL 执行此操作：</span><span class="sxs-lookup"><span data-stu-id="5527d-155">To do this in Entity SQL:</span></span>  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="5527d-156">引用表（集合）的列（属性）</span><span class="sxs-lookup"><span data-stu-id="5527d-156">Referencing Columns (Properties) of Tables (Collections)</span></span>  

 <span data-ttu-id="5527d-157">实体 SQL 中的所有列引用都必须用表别名限定。</span><span class="sxs-lookup"><span data-stu-id="5527d-157">All column references in Entity SQL must be qualified with the table alias.</span></span> <span data-ttu-id="5527d-158">以下构造 (假设 `a` 是表) 的有效列 `T` 在 transact-sql 中有效，但在实体 SQL 中不有效。</span><span class="sxs-lookup"><span data-stu-id="5527d-158">The following construct (assuming that `a` is a valid column of table `T`) is valid in Transact-SQL but not in Entity SQL.</span></span>  
  
```sql  
SELECT a FROM T
```  
  
 <span data-ttu-id="5527d-159">实体 SQL 窗体是</span><span class="sxs-lookup"><span data-stu-id="5527d-159">The Entity SQL form is</span></span>  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 <span data-ttu-id="5527d-160">表别名在 `from` 子句中是可选的。</span><span class="sxs-lookup"><span data-stu-id="5527d-160">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="5527d-161">表名称被用作隐式别名。</span><span class="sxs-lookup"><span data-stu-id="5527d-161">The name of the table is used as the implicit alias.</span></span> <span data-ttu-id="5527d-162">实体 SQL 还允许以下形式：</span><span class="sxs-lookup"><span data-stu-id="5527d-162">Entity SQL allows the following form as well:</span></span>  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="5527d-163">通过对象导航</span><span class="sxs-lookup"><span data-stu-id="5527d-163">Navigation Through Objects</span></span>  

 <span data-ttu-id="5527d-164">Transact-sql 使用 "." 表示法来引用表)  (的列。</span><span class="sxs-lookup"><span data-stu-id="5527d-164">Transact-SQL uses the "." notation for referencing columns of (a row of) a table.</span></span> <span data-ttu-id="5527d-165">实体 SQL 将此表示法扩展 (从编程语言中借用) ，以支持通过对象的属性进行导航。</span><span class="sxs-lookup"><span data-stu-id="5527d-165">Entity SQL extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="5527d-166">例如，如果 `p` 是 "Person" 类型的表达式，则下面是用于引用此人地址所在城市的实体 SQL 语法。</span><span class="sxs-lookup"><span data-stu-id="5527d-166">For example, if `p` is an expression of type Person, the following is the Entity SQL syntax for referencing the city of the address of this person.</span></span>  
  
```sql  
p.Address.City
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="5527d-167">不支持 \*</span><span class="sxs-lookup"><span data-stu-id="5527d-167">No Support for \*</span></span>  

 <span data-ttu-id="5527d-168">Transact-sql 支持将非限定 \* 语法作为整行的别名，而限定 \* 语法 (t. \*) 作为该表字段的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="5527d-168">Transact-SQL supports the unqualified \* syntax as an alias for the entire row, and the qualified \* syntax (t.\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="5527d-169">此外，Transact-sql 允许) 聚合 (包含 null 的特殊计数 \* 。</span><span class="sxs-lookup"><span data-stu-id="5527d-169">In addition, Transact-SQL allows for a special count(\*) aggregate, which includes nulls.</span></span>  
  
 <span data-ttu-id="5527d-170">实体 SQL 不支持 \* 构造。</span><span class="sxs-lookup"><span data-stu-id="5527d-170">Entity SQL does not support the \* construct.</span></span> <span data-ttu-id="5527d-171">格式为的 transact-sql 查询 `select * from T` ， `select T1.* from T1, T2...` 可以分别以和实体 SQL 表示 `select value t from T as t` `select value t1 from T1 as t1, T2 as t2...` 。</span><span class="sxs-lookup"><span data-stu-id="5527d-171">Transact-SQL queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in Entity SQL as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="5527d-172">此外，这些构造还处理继承（值可替换性），同时将 `select *` 变体限制到所声明类型的顶级属性。</span><span class="sxs-lookup"><span data-stu-id="5527d-172">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 <span data-ttu-id="5527d-173">实体 SQL 不支持 `count(*)` 聚合。</span><span class="sxs-lookup"><span data-stu-id="5527d-173">Entity SQL does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="5527d-174">请改用 `count(0)`。</span><span class="sxs-lookup"><span data-stu-id="5527d-174">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="5527d-175">对 Group By 的更改</span><span class="sxs-lookup"><span data-stu-id="5527d-175">Changes to Group By</span></span>  

 <span data-ttu-id="5527d-176">实体 SQL 支持密钥的别名 `group by` 。</span><span class="sxs-lookup"><span data-stu-id="5527d-176">Entity SQL supports aliasing of `group by` keys.</span></span> <span data-ttu-id="5527d-177">`select` 子句和 `having` 子句中的表达式必须通过这些别名引用 `group by` 关键字。</span><span class="sxs-lookup"><span data-stu-id="5527d-177">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="5527d-178">例如，以下实体 SQL 语法：</span><span class="sxs-lookup"><span data-stu-id="5527d-178">For example, this Entity SQL syntax:</span></span>  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 <span data-ttu-id="5527d-179">...等效于以下 Transact-sql：</span><span class="sxs-lookup"><span data-stu-id="5527d-179">...is equivalent to the following Transact-SQL:</span></span>  
  
```sql  
SELECT b + c, count(*), sum(a)
FROM T
GROUP BY b + c
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="5527d-180">基于集合的聚合</span><span class="sxs-lookup"><span data-stu-id="5527d-180">Collection-Based Aggregates</span></span>  

 <span data-ttu-id="5527d-181">实体 SQL 支持两种类型的聚合。</span><span class="sxs-lookup"><span data-stu-id="5527d-181">Entity SQL supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="5527d-182">基于集合的合计对集合进行运算，并且产生合计结果。</span><span class="sxs-lookup"><span data-stu-id="5527d-182">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="5527d-183">它们可以出现在查询中的任何位置，并且不需要 `group by` 子句。</span><span class="sxs-lookup"><span data-stu-id="5527d-183">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="5527d-184">例如：</span><span class="sxs-lookup"><span data-stu-id="5527d-184">For example:</span></span>  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 <span data-ttu-id="5527d-185">实体 SQL 还支持 SQL 样式的聚合。</span><span class="sxs-lookup"><span data-stu-id="5527d-185">Entity SQL also supports SQL-style aggregates.</span></span> <span data-ttu-id="5527d-186">例如：</span><span class="sxs-lookup"><span data-stu-id="5527d-186">For example:</span></span>  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="5527d-187">ORDER BY 子句用法</span><span class="sxs-lookup"><span data-stu-id="5527d-187">ORDER BY Clause Usage</span></span>  

<span data-ttu-id="5527d-188">Transact-sql `ORDER BY` 仅允许在最顶部的块中指定子句 `SELECT .. FROM .. WHERE` 。</span><span class="sxs-lookup"><span data-stu-id="5527d-188">Transact-SQL allows `ORDER BY` clauses to be specified only in the topmost `SELECT .. FROM .. WHERE` block.</span></span> <span data-ttu-id="5527d-189">在实体 SQL 中，您可以使用嵌套 `ORDER BY` 表达式，并将其放在查询中的任何位置，但不会保留嵌套查询中的排序。</span><span class="sxs-lookup"><span data-stu-id="5527d-189">In Entity SQL, you can use a nested `ORDER BY` expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
```sql  
-- The following query will order the results by the last name  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact AS C1
        ORDER BY C1.LastName  
```  
  
```sql  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="identifiers"></a><span data-ttu-id="5527d-190">标识符</span><span class="sxs-lookup"><span data-stu-id="5527d-190">Identifiers</span></span>  

 <span data-ttu-id="5527d-191">在 Transact-sql 中，标识符比较基于当前数据库的排序规则。</span><span class="sxs-lookup"><span data-stu-id="5527d-191">In Transact-SQL, identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="5527d-192">在实体 SQL 中，标识符始终不区分大小写且区分重音 (也就是说，实体 SQL 区分重音字符和非重音字符;例如，"a" 不等于 "ấ" ) 。</span><span class="sxs-lookup"><span data-stu-id="5527d-192">In Entity SQL, identifiers are always case insensitive and accent sensitive (that is, Entity SQL distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> <span data-ttu-id="5527d-193">实体 SQL 将看起来相同但来自不同代码页的字母版本视为不同的字符。</span><span class="sxs-lookup"><span data-stu-id="5527d-193">Entity SQL treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="5527d-194">有关详细信息，请参阅 [输入字符集](input-character-set-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="5527d-194">For more information, see [Input Character Set](input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="5527d-195">Transact-SQL 功能在 Entity SQL 中不可用</span><span class="sxs-lookup"><span data-stu-id="5527d-195">Transact-SQL Functionality Not Available in Entity SQL</span></span>  

 <span data-ttu-id="5527d-196">以下 Transact-sql 功能在实体 SQL 中不可用。</span><span class="sxs-lookup"><span data-stu-id="5527d-196">The following Transact-SQL functionality is not available in Entity SQL.</span></span>  
  
 <span data-ttu-id="5527d-197">DML</span><span class="sxs-lookup"><span data-stu-id="5527d-197">DML</span></span>  
 <span data-ttu-id="5527d-198">实体 SQL 当前不提供对 DML 语句 (insert、update、delete) 的支持。</span><span class="sxs-lookup"><span data-stu-id="5527d-198">Entity SQL currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="5527d-199">DDL</span><span class="sxs-lookup"><span data-stu-id="5527d-199">DDL</span></span>  
 <span data-ttu-id="5527d-200">实体 SQL 在当前版本中不支持 DDL。</span><span class="sxs-lookup"><span data-stu-id="5527d-200">Entity SQL provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="5527d-201">命令式编程</span><span class="sxs-lookup"><span data-stu-id="5527d-201">Imperative Programming</span></span>  
 <span data-ttu-id="5527d-202">与 Transact-sql 不同，实体 SQL 不提供对命令性编程的支持。</span><span class="sxs-lookup"><span data-stu-id="5527d-202">Entity SQL provides no support for imperative programming, unlike Transact-SQL.</span></span> <span data-ttu-id="5527d-203">请改而使用编程语言。</span><span class="sxs-lookup"><span data-stu-id="5527d-203">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="5527d-204">分组函数</span><span class="sxs-lookup"><span data-stu-id="5527d-204">Grouping Functions</span></span>  
 <span data-ttu-id="5527d-205">实体 SQL 尚不支持分组函数 (例如，多维数据集、汇总和 GROUPING_SET) 。</span><span class="sxs-lookup"><span data-stu-id="5527d-205">Entity SQL does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="5527d-206">分析函数</span><span class="sxs-lookup"><span data-stu-id="5527d-206">Analytic Functions</span></span>  
 <span data-ttu-id="5527d-207">实体 SQL 尚不 () 提供对分析功能的支持。</span><span class="sxs-lookup"><span data-stu-id="5527d-207">Entity SQL does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="5527d-208">内置函数、运算符</span><span class="sxs-lookup"><span data-stu-id="5527d-208">Built-in Functions, Operators</span></span>  
 <span data-ttu-id="5527d-209">实体 SQL 支持 Transact-sql 的内置函数和运算符的子集。</span><span class="sxs-lookup"><span data-stu-id="5527d-209">Entity SQL supports a subset of Transact-SQL's built in functions and operators.</span></span> <span data-ttu-id="5527d-210">这些运算符和函数可能受到主要存储提供程序的支持。</span><span class="sxs-lookup"><span data-stu-id="5527d-210">These operators and functions are likely to be supported by the major store providers.</span></span> <span data-ttu-id="5527d-211">实体 SQL 使用在提供程序清单中声明的特定于存储的函数。</span><span class="sxs-lookup"><span data-stu-id="5527d-211">Entity SQL uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="5527d-212">此外，实体框架允许声明内置的和用户定义的现有存储函数，以供实体 SQL 使用。</span><span class="sxs-lookup"><span data-stu-id="5527d-212">Additionally, the Entity Framework allows you to declare built-in and user-defined existing store functions, for Entity SQL to use.</span></span>  
  
 <span data-ttu-id="5527d-213">提示</span><span class="sxs-lookup"><span data-stu-id="5527d-213">Hints</span></span>  
 <span data-ttu-id="5527d-214">实体 SQL 不提供查询提示的机制。</span><span class="sxs-lookup"><span data-stu-id="5527d-214">Entity SQL does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="5527d-215">查询结果批处理</span><span class="sxs-lookup"><span data-stu-id="5527d-215">Batching Query Results</span></span>  
 <span data-ttu-id="5527d-216">实体 SQL 不支持批处理查询结果。</span><span class="sxs-lookup"><span data-stu-id="5527d-216">Entity SQL does not support batching query results.</span></span> <span data-ttu-id="5527d-217">例如，以下是以批处理) 形式发送的有效 Transact-sql (：</span><span class="sxs-lookup"><span data-stu-id="5527d-217">For example, the following is valid Transact-SQL (sending as a batch):</span></span>  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 <span data-ttu-id="5527d-218">但是，不支持等效的实体 SQL：</span><span class="sxs-lookup"><span data-stu-id="5527d-218">However, the equivalent Entity SQL is not supported:</span></span>  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 <span data-ttu-id="5527d-219">实体 SQL 仅支持一个结果-每个命令生成查询语句。</span><span class="sxs-lookup"><span data-stu-id="5527d-219">Entity SQL only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5527d-220">请参阅</span><span class="sxs-lookup"><span data-stu-id="5527d-220">See also</span></span>

- [<span data-ttu-id="5527d-221">Entity SQL 概述</span><span class="sxs-lookup"><span data-stu-id="5527d-221">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="5527d-222">不支持的表达式</span><span class="sxs-lookup"><span data-stu-id="5527d-222">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)

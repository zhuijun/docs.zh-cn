---
title: SELECT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
ms.openlocfilehash: 860e2a9a3e484e8d09cad282be8c0126c8235b46
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202209"
---
# <a name="select-entity-sql"></a><span data-ttu-id="30cc7-102">SELECT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="30cc7-102">SELECT (Entity SQL)</span></span>

<span data-ttu-id="30cc7-103">指定查询所返回的元素。</span><span class="sxs-lookup"><span data-stu-id="30cc7-103">Specifies the elements returned by a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30cc7-104">语法</span><span class="sxs-lookup"><span data-stu-id="30cc7-104">Syntax</span></span>  
  
```sql  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
-- or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a><span data-ttu-id="30cc7-105">参数</span><span class="sxs-lookup"><span data-stu-id="30cc7-105">Arguments</span></span>  

 <span data-ttu-id="30cc7-106">ALL</span><span class="sxs-lookup"><span data-stu-id="30cc7-106">ALL</span></span>  
 <span data-ttu-id="30cc7-107">指定结果集中可以出现重复项。</span><span class="sxs-lookup"><span data-stu-id="30cc7-107">Specifies that duplicates can appear in the result set.</span></span> <span data-ttu-id="30cc7-108">ALL 为默认值。</span><span class="sxs-lookup"><span data-stu-id="30cc7-108">ALL is the default.</span></span>  
  
 <span data-ttu-id="30cc7-109">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="30cc7-109">DISTINCT</span></span>  
 <span data-ttu-id="30cc7-110">指定结果集中只能出现唯一的结果。</span><span class="sxs-lookup"><span data-stu-id="30cc7-110">Specifies that only unique results can appear in the result set.</span></span>  
  
 <span data-ttu-id="30cc7-111">值</span><span class="sxs-lookup"><span data-stu-id="30cc7-111">VALUE</span></span>  
 <span data-ttu-id="30cc7-112">仅允许指定一个项，且不添加到行包装上。</span><span class="sxs-lookup"><span data-stu-id="30cc7-112">Allows only one item to be specified, and does not add on a row wrapper.</span></span>  
  
 `topSubclause`  
 <span data-ttu-id="30cc7-113">任何指示从查询返回的首批结果数的有效表达式（形式为 `top(expr)`）。</span><span class="sxs-lookup"><span data-stu-id="30cc7-113">Any valid expression that indicates the number of first results to return from the query, of the form `top(expr)`.</span></span>  
  
 <span data-ttu-id="30cc7-114">使用 [ORDER BY](order-by-entity-sql.md) 运算符的 LIMIT 参数，还可以选择结果集中的前 n 个项。</span><span class="sxs-lookup"><span data-stu-id="30cc7-114">The LIMIT parameter of the [ORDER BY](order-by-entity-sql.md) operator also lets you select the first n items in the result set.</span></span>  
  
 `aliasedExpr`  
 <span data-ttu-id="30cc7-115">形式如下的表达式：</span><span class="sxs-lookup"><span data-stu-id="30cc7-115">An expression of the form:</span></span>  
  
 <span data-ttu-id="30cc7-116">`expr` 作为 `identifier` &#124; `expr`</span><span class="sxs-lookup"><span data-stu-id="30cc7-116">`expr` as `identifier` &#124; `expr`</span></span>  
  
 `expr`  
 <span data-ttu-id="30cc7-117">文本或表达式。</span><span class="sxs-lookup"><span data-stu-id="30cc7-117">A literal or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30cc7-118">备注</span><span class="sxs-lookup"><span data-stu-id="30cc7-118">Remarks</span></span>  

 <span data-ttu-id="30cc7-119">在计算 [from](from-entity-sql.md)、 [GROUP BY](group-by-entity-sql.md)和 [HAVING](having-entity-sql.md) 子句之后计算 SELECT 子句。</span><span class="sxs-lookup"><span data-stu-id="30cc7-119">The SELECT clause is evaluated after the [FROM](from-entity-sql.md), [GROUP BY](group-by-entity-sql.md), and [HAVING](having-entity-sql.md) clauses have been evaluated.</span></span> <span data-ttu-id="30cc7-120">SELECT 子句只能引用当前处于范围内的项（FROM 子句指定的范围或外部范围）。</span><span class="sxs-lookup"><span data-stu-id="30cc7-120">The SELECT clause can only refer to items currently in-scope (from the FROM clause, or from outer scopes).</span></span> <span data-ttu-id="30cc7-121">如果指定了 GROUP BY 子句，则仅允许 SELECT 子句引用 GROUP BY 键的别名。</span><span class="sxs-lookup"><span data-stu-id="30cc7-121">If a GROUP BY clause has been specified, the SELECT clause is only allowed to reference the aliases for the GROUP BY keys.</span></span> <span data-ttu-id="30cc7-122">仅允许在聚合函数中引用 FROM 子句项。</span><span class="sxs-lookup"><span data-stu-id="30cc7-122">Referring to the FROM clause items is only permitted in aggregate functions.</span></span>  
  
 <span data-ttu-id="30cc7-123">跟在 SELECT 关键字之后的一个或多个查询表达式的列表称为“选择列表”，更加正式的名称为“投影”。</span><span class="sxs-lookup"><span data-stu-id="30cc7-123">The list of one or more query expressions following the SELECT keyword is known as the select list, or more formally as the projection.</span></span> <span data-ttu-id="30cc7-124">最普通的投影形式为单个查询表达式。</span><span class="sxs-lookup"><span data-stu-id="30cc7-124">The most general form of projection is a single query expression.</span></span> <span data-ttu-id="30cc7-125">如果从集合 `member1` 选择一个成员 `collection1`，则会生成 `member1` 中每个对象的所有 `collection1`值的新集合（如下面的示例所示）。</span><span class="sxs-lookup"><span data-stu-id="30cc7-125">If you select a member `member1` from a collection `collection1`, you will produce a new collection of all the `member1` values for each object in `collection1`, as illustrated in the following example.</span></span>  
  
```sql  
SELECT collection1.member1 FROM collection1  
```  
  
 <span data-ttu-id="30cc7-126">例如，如果 `customers` 是类型为 `Customer` 的集合，且该类型有类型为 `Name` 的属性 `string`，则从 `Name` 选择 `customers` 将生成一个字符串集合（如下面的示例所示）。</span><span class="sxs-lookup"><span data-stu-id="30cc7-126">For example, if `customers` is a collection of type `Customer` that has a property `Name` that is of type `string`, selecting `Name` from `customers` will yield a collection of strings, as illustrated in the following example.</span></span>  
  
```sql  
SELECT customers.Name FROM customers AS c  
```  
  
 <span data-ttu-id="30cc7-127">也可以使用 JOIN 语法（FULL、INNER、LEFT、OUTER、ON 和 RIGHT）。</span><span class="sxs-lookup"><span data-stu-id="30cc7-127">It is also possible to use JOIN syntax (FULL, INNER, LEFT, OUTER, ON, and RIGHT).</span></span> <span data-ttu-id="30cc7-128">ON 是内部联接的必需语法，但不允许用于交叉联接。</span><span class="sxs-lookup"><span data-stu-id="30cc7-128">ON is required for inner joins and is nto allowed for cross joins.</span></span>  
  
## <a name="row-and-value-select-clauses"></a><span data-ttu-id="30cc7-129">行和值选择子句</span><span class="sxs-lookup"><span data-stu-id="30cc7-129">Row and Value Select Clauses</span></span>  

 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="30cc7-130">支持 SELECT 子句的两种变体。</span><span class="sxs-lookup"><span data-stu-id="30cc7-130">supports two variants of the SELECT clause.</span></span> <span data-ttu-id="30cc7-131">第一种变体是行选择，由 SELECT 关键字标识，可用于指定一个或多个应被投影的值。由于在返回的值周围隐式添加了行包装，因此查询表达式的结果始终为行的多集。</span><span class="sxs-lookup"><span data-stu-id="30cc7-131">The first variant, row select, is identified by the SELECT keyword, and can be used to specify one or more values that should be projected out. Because a row wrapper is implicitly added around the values returned, the result of the query expression is always a multiset of rows.</span></span>  
  
 <span data-ttu-id="30cc7-132">行选择中的每个查询表达式都必须指定一个别名。</span><span class="sxs-lookup"><span data-stu-id="30cc7-132">Each query expression in a row select must specify an alias.</span></span> <span data-ttu-id="30cc7-133">如果不指定别名，[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 会尝试使用别名生成规则生成别名。</span><span class="sxs-lookup"><span data-stu-id="30cc7-133">If no alias is specified,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias by using the alias generation rules.</span></span>  
  
 <span data-ttu-id="30cc7-134">SELECT 子句的另一种变体为值选择，由 SELECT VALUE 关键字标识。</span><span class="sxs-lookup"><span data-stu-id="30cc7-134">The other variant of the SELECT clause, value select, is identified by the SELECT VALUE keyword.</span></span> <span data-ttu-id="30cc7-135">该变体仅允许指定一个值，且不添加行包装。</span><span class="sxs-lookup"><span data-stu-id="30cc7-135">It allows only one value to be specified, and does not add a row wrapper.</span></span>  
  
 <span data-ttu-id="30cc7-136">行选择总是可通过 VALUE SELECT 进行表示（如下面的示例所示）。</span><span class="sxs-lookup"><span data-stu-id="30cc7-136">A row select is always expressible in terms of VALUE SELECT, as illustrated in the following example.</span></span>  
  
```sql  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C
```  
  
## <a name="all-and-distinct-modifiers"></a><span data-ttu-id="30cc7-137">All 和 Distinct 修饰符</span><span class="sxs-lookup"><span data-stu-id="30cc7-137">All and Distinct Modifiers</span></span>  

 <span data-ttu-id="30cc7-138">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中的两种 SELECT 变体都允许指定 ALL 或 DISTINCT 修饰符。</span><span class="sxs-lookup"><span data-stu-id="30cc7-138">Both variants of SELECT in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allow the specification of an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="30cc7-139">如果指定 DISTINCT 修饰符，则将从查询表达式（直到并包括 SELECT 子句）生成的集合中消除重复项。</span><span class="sxs-lookup"><span data-stu-id="30cc7-139">If the DISTINCT modifier is specified, duplicates are eliminated from the collection produced by the query expression (up to and including the SELECT clause).</span></span> <span data-ttu-id="30cc7-140">如果指定 ALL 修饰符，则不消除重复项；ALL 为默认值。</span><span class="sxs-lookup"><span data-stu-id="30cc7-140">If the ALL modifier is specified, no duplicate elimination is performed; ALL is the default.</span></span>  
  
## <a name="differences-from-transact-sql"></a><span data-ttu-id="30cc7-141">与 Transact-SQL 的区别</span><span class="sxs-lookup"><span data-stu-id="30cc7-141">Differences from Transact-SQL</span></span>  

 <span data-ttu-id="30cc7-142">与 Transact-SQL 不同， [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 不支持在 SELECT 子句中使用 \* 参数。</span><span class="sxs-lookup"><span data-stu-id="30cc7-142">Unlike Transact-SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support use of the \* argument in the SELECT clause.</span></span>  <span data-ttu-id="30cc7-143">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 允许查询通过从 FROM 子句引用集合别名来提取出完整的记录（如下面的示例所示）。</span><span class="sxs-lookup"><span data-stu-id="30cc7-143">Instead, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows queries to project out entire records by referencing the collection aliases from the FROM clause, as illustrated in the following example.</span></span>  
  
```sql  
SELECT * FROM T1, T2  
```  
  
 <span data-ttu-id="30cc7-144">上一 Transact-sql 查询表达式 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 的表示方式如下所示。</span><span class="sxs-lookup"><span data-stu-id="30cc7-144">The previous Transact-SQL query expression is expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] in the following way.</span></span>  
  
```sql  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a><span data-ttu-id="30cc7-145">示例</span><span class="sxs-lookup"><span data-stu-id="30cc7-145">Example</span></span>  

 <span data-ttu-id="30cc7-146">下面的 Entity SQL 查询使用 SELECT 运算符指定查询要返回的元素。</span><span class="sxs-lookup"><span data-stu-id="30cc7-146">The following Entity SQL query uses the SELECT operator to specify the elements to be returned by a query.</span></span> <span data-ttu-id="30cc7-147">此查询基于 AdventureWorks 销售模型。</span><span class="sxs-lookup"><span data-stu-id="30cc7-147">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="30cc7-148">若要编译并运行此查询，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="30cc7-148">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="30cc7-149">执行 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的过程。</span><span class="sxs-lookup"><span data-stu-id="30cc7-149">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="30cc7-150">将以下查询作为参数传递给 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="30cc7-150">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LESS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less)]  
  
## <a name="see-also"></a><span data-ttu-id="30cc7-151">请参阅</span><span class="sxs-lookup"><span data-stu-id="30cc7-151">See also</span></span>

- [<span data-ttu-id="30cc7-152">查询表达式</span><span class="sxs-lookup"><span data-stu-id="30cc7-152">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="30cc7-153">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="30cc7-153">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="30cc7-154">TOP</span><span class="sxs-lookup"><span data-stu-id="30cc7-154">TOP</span></span>](top-entity-sql.md)

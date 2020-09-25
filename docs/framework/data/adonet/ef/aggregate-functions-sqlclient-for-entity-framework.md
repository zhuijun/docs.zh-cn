---
title: 聚合函数（用于实体框架的 SqlClient）
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 1c32ccfe18c67c9baeb7df0f981c9129b3bbc8bb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204510"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="f437f-102">聚合函数（用于实体框架的 SqlClient）</span><span class="sxs-lookup"><span data-stu-id="f437f-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>

<span data-ttu-id="f437f-103">SQL Server .NET Framework 数据提供程序 (SqlClient) 提供聚合函数。</span><span class="sxs-lookup"><span data-stu-id="f437f-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="f437f-104">聚合函数对一组输入值执行计算并返回一个值。</span><span class="sxs-lookup"><span data-stu-id="f437f-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="f437f-105">这些函数位于 SqlServer 命名空间中，该命名空间在您使用 SqlClient 时可用。</span><span class="sxs-lookup"><span data-stu-id="f437f-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="f437f-106">提供程序的命名空间属性使实体框架可以确定此提供程序对特定构造（如类型和函数）使用哪个前缀。</span><span class="sxs-lookup"><span data-stu-id="f437f-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="f437f-107">下面是 SqlClient 聚合函数。</span><span class="sxs-lookup"><span data-stu-id="f437f-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="f437f-108">AVG (表达式) </span><span class="sxs-lookup"><span data-stu-id="f437f-108">AVG(expression)</span></span>

<span data-ttu-id="f437f-109">返回集合中各值的平均值。</span><span class="sxs-lookup"><span data-stu-id="f437f-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="f437f-110">Null 值会被忽略。</span><span class="sxs-lookup"><span data-stu-id="f437f-110">Null values are ignored.</span></span>

<span data-ttu-id="f437f-111">**参数**</span><span class="sxs-lookup"><span data-stu-id="f437f-111">**Arguments**</span></span>

<span data-ttu-id="f437f-112">`Int32`、、 `Int64` `Double` 和 `Decimal` 。</span><span class="sxs-lookup"><span data-stu-id="f437f-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="f437f-113">**返回值**</span><span class="sxs-lookup"><span data-stu-id="f437f-113">**Return Value**</span></span>

<span data-ttu-id="f437f-114">`expression` 的类型。</span><span class="sxs-lookup"><span data-stu-id="f437f-114">The type of `expression`.</span></span>

<span data-ttu-id="f437f-115">**示例**</span><span class="sxs-lookup"><span data-stu-id="f437f-115">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a><span data-ttu-id="f437f-116">CHECKSUM_AGG (集合) </span><span class="sxs-lookup"><span data-stu-id="f437f-116">CHECKSUM_AGG(collection)</span></span>

 <span data-ttu-id="f437f-117">返回集合中各值的校验和。</span><span class="sxs-lookup"><span data-stu-id="f437f-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="f437f-118">Null 值会被忽略。</span><span class="sxs-lookup"><span data-stu-id="f437f-118">Null values are ignored.</span></span>

 <span data-ttu-id="f437f-119">**参数**</span><span class="sxs-lookup"><span data-stu-id="f437f-119">**Arguments**</span></span>

 <span data-ttu-id="f437f-120">)  (集合 `Int32` 。</span><span class="sxs-lookup"><span data-stu-id="f437f-120">A Collection(`Int32`).</span></span>

 <span data-ttu-id="f437f-121">**返回值**</span><span class="sxs-lookup"><span data-stu-id="f437f-121">**Return Value**</span></span>

 <span data-ttu-id="f437f-122">一个 `Int32`。</span><span class="sxs-lookup"><span data-stu-id="f437f-122">An `Int32`.</span></span>

 <span data-ttu-id="f437f-123">**示例**</span><span class="sxs-lookup"><span data-stu-id="f437f-123">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]

## <a name="countexpression"></a><span data-ttu-id="f437f-124">计数 (表达式) </span><span class="sxs-lookup"><span data-stu-id="f437f-124">COUNT(expression)</span></span>

<span data-ttu-id="f437f-125">以 `Int32` 形式返回集合中的项数。</span><span class="sxs-lookup"><span data-stu-id="f437f-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="f437f-126">**参数**</span><span class="sxs-lookup"><span data-stu-id="f437f-126">**Arguments**</span></span>

<span data-ttu-id="f437f-127">一个集合 \<T> ，其中 T 为以下类型之一：</span><span class="sxs-lookup"><span data-stu-id="f437f-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="f437f-128">`Guid` SQL Server 2000 中未返回 () </span><span class="sxs-lookup"><span data-stu-id="f437f-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="f437f-129">**返回值**</span><span class="sxs-lookup"><span data-stu-id="f437f-129">**Return Value**</span></span>

<span data-ttu-id="f437f-130">一个 `Int32`。</span><span class="sxs-lookup"><span data-stu-id="f437f-130">An `Int32`.</span></span>

<span data-ttu-id="f437f-131">**示例**</span><span class="sxs-lookup"><span data-stu-id="f437f-131">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]

## <a name="count_bigexpression"></a><span data-ttu-id="f437f-132"> (表达式的 COUNT_BIG) </span><span class="sxs-lookup"><span data-stu-id="f437f-132">COUNT_BIG(expression)</span></span>

<span data-ttu-id="f437f-133">以 `bigint` 形式返回集合中的项数。</span><span class="sxs-lookup"><span data-stu-id="f437f-133">Returns the number of items in a collection as a `bigint`.</span></span>

 <span data-ttu-id="f437f-134">**参数**</span><span class="sxs-lookup"><span data-stu-id="f437f-134">**Arguments**</span></span>

 <span data-ttu-id="f437f-135">集合 (T) ，其中 T 为以下类型之一：</span><span class="sxs-lookup"><span data-stu-id="f437f-135">A Collection(T), where T is one of the following types:</span></span>

 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="f437f-136">`Guid` SQL Server 2000 中未返回 () </span><span class="sxs-lookup"><span data-stu-id="f437f-136">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="f437f-137">**返回值**</span><span class="sxs-lookup"><span data-stu-id="f437f-137">**Return Value**</span></span>

<span data-ttu-id="f437f-138">一个 `Int64`。</span><span class="sxs-lookup"><span data-stu-id="f437f-138">An `Int64`.</span></span>

<span data-ttu-id="f437f-139">**示例**</span><span class="sxs-lookup"><span data-stu-id="f437f-139">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="f437f-140">MAX (表达式) </span><span class="sxs-lookup"><span data-stu-id="f437f-140">MAX(expression)</span></span>

<span data-ttu-id="f437f-141">返回集合中的最大值。</span><span class="sxs-lookup"><span data-stu-id="f437f-141">Returns the maximum value the collection.</span></span>

<span data-ttu-id="f437f-142">**参数**</span><span class="sxs-lookup"><span data-stu-id="f437f-142">**Arguments**</span></span>

<span data-ttu-id="f437f-143">集合 (T) ，其中 T 为以下类型之一：</span><span class="sxs-lookup"><span data-stu-id="f437f-143">A Collection(T), where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="f437f-144">**返回值**</span><span class="sxs-lookup"><span data-stu-id="f437f-144">**Return Value**</span></span>

<span data-ttu-id="f437f-145">`expression` 的类型。</span><span class="sxs-lookup"><span data-stu-id="f437f-145">The type of `expression`.</span></span>

<span data-ttu-id="f437f-146">**示例**</span><span class="sxs-lookup"><span data-stu-id="f437f-146">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="f437f-147">MIN (表达式) </span><span class="sxs-lookup"><span data-stu-id="f437f-147">MIN(expression)</span></span>

<span data-ttu-id="f437f-148">返回集合中的最小值。</span><span class="sxs-lookup"><span data-stu-id="f437f-148">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="f437f-149">**参数**</span><span class="sxs-lookup"><span data-stu-id="f437f-149">**Arguments**</span></span>

<span data-ttu-id="f437f-150">集合 (T) ，其中 T 为以下类型之一：</span><span class="sxs-lookup"><span data-stu-id="f437f-150">A Collection(T), where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="f437f-151">**返回值**</span><span class="sxs-lookup"><span data-stu-id="f437f-151">**Return Value**</span></span>

<span data-ttu-id="f437f-152">`expression` 的类型。</span><span class="sxs-lookup"><span data-stu-id="f437f-152">The type of `expression`.</span></span>

<span data-ttu-id="f437f-153">**示例**</span><span class="sxs-lookup"><span data-stu-id="f437f-153">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="f437f-154">STDEV (表达式) </span><span class="sxs-lookup"><span data-stu-id="f437f-154">STDEV(expression)</span></span>

<span data-ttu-id="f437f-155">返回指定表达式中所有值的标准偏差。</span><span class="sxs-lookup"><span data-stu-id="f437f-155">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="f437f-156">**参数**</span><span class="sxs-lookup"><span data-stu-id="f437f-156">**Arguments**</span></span>

<span data-ttu-id="f437f-157">)  (集合 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="f437f-157">A Collection(`Double`).</span></span>

<span data-ttu-id="f437f-158">**返回值**</span><span class="sxs-lookup"><span data-stu-id="f437f-158">**Return Value**</span></span>

<span data-ttu-id="f437f-159">`Double`。</span><span class="sxs-lookup"><span data-stu-id="f437f-159">A `Double`.</span></span>

<span data-ttu-id="f437f-160">**示例**</span><span class="sxs-lookup"><span data-stu-id="f437f-160">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="f437f-161">STDEVP (表达式) </span><span class="sxs-lookup"><span data-stu-id="f437f-161">STDEVP(expression)</span></span>

<span data-ttu-id="f437f-162">返回指定表达式中所有值的总体标准偏差。</span><span class="sxs-lookup"><span data-stu-id="f437f-162">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="f437f-163">**参数**</span><span class="sxs-lookup"><span data-stu-id="f437f-163">**Arguments**</span></span>

<span data-ttu-id="f437f-164">)  (集合 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="f437f-164">A Collection(`Double`).</span></span>

<span data-ttu-id="f437f-165">**返回值**</span><span class="sxs-lookup"><span data-stu-id="f437f-165">**Return Value**</span></span>

<span data-ttu-id="f437f-166">`Double`。</span><span class="sxs-lookup"><span data-stu-id="f437f-166">A `Double`.</span></span>

<span data-ttu-id="f437f-167">**示例**</span><span class="sxs-lookup"><span data-stu-id="f437f-167">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="f437f-168">SUM (表达式) </span><span class="sxs-lookup"><span data-stu-id="f437f-168">SUM(expression)</span></span>

<span data-ttu-id="f437f-169">返回集合中所有值的总和。</span><span class="sxs-lookup"><span data-stu-id="f437f-169">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="f437f-170">**参数**</span><span class="sxs-lookup"><span data-stu-id="f437f-170">**Arguments**</span></span>

<span data-ttu-id="f437f-171">集合 (T) 其中 T 为以下类型之一： `Int32` 、 `Int64` 、 `Double` 和 `Decimal` 。</span><span class="sxs-lookup"><span data-stu-id="f437f-171">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="f437f-172">**返回值**</span><span class="sxs-lookup"><span data-stu-id="f437f-172">**Return Value**</span></span>

<span data-ttu-id="f437f-173">`expression` 的类型。</span><span class="sxs-lookup"><span data-stu-id="f437f-173">The type of `expression`.</span></span>

<span data-ttu-id="f437f-174">**示例**</span><span class="sxs-lookup"><span data-stu-id="f437f-174">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="f437f-175">VAR (表达式) </span><span class="sxs-lookup"><span data-stu-id="f437f-175">VAR(expression)</span></span>

<span data-ttu-id="f437f-176">返回指定表达式中所有值的方差。</span><span class="sxs-lookup"><span data-stu-id="f437f-176">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="f437f-177">**参数**</span><span class="sxs-lookup"><span data-stu-id="f437f-177">**Arguments**</span></span>

<span data-ttu-id="f437f-178">)  (集合 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="f437f-178">A Collection(`Double`).</span></span>

<span data-ttu-id="f437f-179">**返回值**</span><span class="sxs-lookup"><span data-stu-id="f437f-179">**Return Value**</span></span>

<span data-ttu-id="f437f-180">`Double`。</span><span class="sxs-lookup"><span data-stu-id="f437f-180">A `Double`.</span></span>

<span data-ttu-id="f437f-181">**示例**</span><span class="sxs-lookup"><span data-stu-id="f437f-181">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="f437f-182">VARP (表达式) </span><span class="sxs-lookup"><span data-stu-id="f437f-182">VARP(expression)</span></span>

<span data-ttu-id="f437f-183">返回指定表达式中所有值的总体统计方差。</span><span class="sxs-lookup"><span data-stu-id="f437f-183">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="f437f-184">**参数**</span><span class="sxs-lookup"><span data-stu-id="f437f-184">**Arguments**</span></span>

<span data-ttu-id="f437f-185">)  (集合 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="f437f-185">A Collection(`Double`).</span></span>

<span data-ttu-id="f437f-186">**返回值**</span><span class="sxs-lookup"><span data-stu-id="f437f-186">**Return Value**</span></span>

<span data-ttu-id="f437f-187">`Double`。</span><span class="sxs-lookup"><span data-stu-id="f437f-187">A `Double`.</span></span>

<span data-ttu-id="f437f-188">**示例**</span><span class="sxs-lookup"><span data-stu-id="f437f-188">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)]
  
## <a name="see-also"></a><span data-ttu-id="f437f-189">请参阅</span><span class="sxs-lookup"><span data-stu-id="f437f-189">See also</span></span>

- [<span data-ttu-id="f437f-190">聚合函数 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f437f-190">Aggregate Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/aggregate-functions-transact-sql)
- [<span data-ttu-id="f437f-191">Entity SQL 语言</span><span class="sxs-lookup"><span data-stu-id="f437f-191">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
- [<span data-ttu-id="f437f-192">聚合规范函数</span><span class="sxs-lookup"><span data-stu-id="f437f-192">Aggregate Canonical Functions</span></span>](./language-reference/aggregate-canonical-functions.md)

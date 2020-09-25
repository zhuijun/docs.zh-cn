---
title: SqlClient 中的已知问题（实体框架）
ms.date: 03/30/2017
ms.assetid: 48fe4912-4d0f-46b6-be96-3a42c54780f6
ms.openlocfilehash: 707c749e4dff5d1bbc8d372632aae502092db060
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198101"
---
# <a name="known-issues-in-sqlclient-for-entity-framework"></a><span data-ttu-id="f42f0-102">SqlClient 中的已知问题（实体框架）</span><span class="sxs-lookup"><span data-stu-id="f42f0-102">Known Issues in SqlClient for Entity Framework</span></span>

<span data-ttu-id="f42f0-103">本节介绍与 SQL Server .NET Framework 数据提供程序 (SqlClient) 有关的已知问题。</span><span class="sxs-lookup"><span data-stu-id="f42f0-103">This section describes known issues related to the .NET Framework Data Provider for SQL Server (SqlClient).</span></span>  
  
## <a name="trailing-spaces-in-string-functions"></a><span data-ttu-id="f42f0-104">字符串函数中的尾随空格</span><span class="sxs-lookup"><span data-stu-id="f42f0-104">Trailing Spaces in String Functions</span></span>  

 <span data-ttu-id="f42f0-105">SQL Server 忽略字符串值中的尾随空格。</span><span class="sxs-lookup"><span data-stu-id="f42f0-105">SQL Server ignores trailing spaces in string values.</span></span> <span data-ttu-id="f42f0-106">因此，传递字符串中的尾随空格可能导致意外的结果，甚至会导致失败。</span><span class="sxs-lookup"><span data-stu-id="f42f0-106">Therefore, passing trailing spaces in the string can lead to unpredictable results, even failures.</span></span>  
  
 <span data-ttu-id="f42f0-107">如果字符串中必须包含尾随空格，则应考虑在末尾追加一个空格字符，以便 SQL Server 不会剪裁字符串。</span><span class="sxs-lookup"><span data-stu-id="f42f0-107">If you have to have trailing spaces in your string, you should consider appending a white space character at the end, so that SQL Server does not trim the string.</span></span> <span data-ttu-id="f42f0-108">如果尾随空格不是必需的，应在传递给查询管道之前进行修整。</span><span class="sxs-lookup"><span data-stu-id="f42f0-108">If the trailing spaces are not required, they should be trimmed before they are passed down the query pipeline.</span></span>  
  
## <a name="right-function"></a><span data-ttu-id="f42f0-109">RIGHT 函数</span><span class="sxs-lookup"><span data-stu-id="f42f0-109">RIGHT Function</span></span>  

 <span data-ttu-id="f42f0-110">如果将非 `null` 值和 0 分别作为第一个自变量和第二个自变量传递给 `RIGHT(nvarchar(max)`, 0`)` 或 `RIGHT(varchar(max)`, 0`)`，将返回 `NULL` 值，而不是 `empty` 字符串。</span><span class="sxs-lookup"><span data-stu-id="f42f0-110">If a non-`null` value is passed as a first argument and 0 is passed as a second argument to `RIGHT(nvarchar(max)`, 0`)` or `RIGHT(varchar(max)`, 0`)`, a `NULL` value will be returned instead of an `empty` string.</span></span>  
  
## <a name="cross-and-outer-apply-operators"></a><span data-ttu-id="f42f0-111">CROSS 和 OUTER APPLY 运算符</span><span class="sxs-lookup"><span data-stu-id="f42f0-111">CROSS and OUTER APPLY Operators</span></span>  

 <span data-ttu-id="f42f0-112">SQL Server 2005 中引入了交叉和外部 APPLY 运算符。</span><span class="sxs-lookup"><span data-stu-id="f42f0-112">CROSS and OUTER APPLY operators were introduced in SQL Server 2005.</span></span> <span data-ttu-id="f42f0-113">在某些情况下，查询管道可能生成包含 CROSS APPLY 和/或 OUTER APPLY 运算符的 Transact-SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="f42f0-113">In some cases the query pipeline might produce a Transact-SQL statement that contains CROSS APPLY and/or OUTER APPLY operators.</span></span> <span data-ttu-id="f42f0-114">因为某些后端提供程序（包括早于 SQL Server 2005 的 SQL Server 版本）不支持这些运算符，所以不能对这些后端提供程序执行此类查询。</span><span class="sxs-lookup"><span data-stu-id="f42f0-114">Because some backend providers, including versions of SQL Server earlier than SQL Server 2005, do not support these operators, such queries cannot be executed on these backend providers.</span></span>  
  
 <span data-ttu-id="f42f0-115">下面是一些可能导致输出查询中出现 CROSS APPLY 和/或 OUTER APPLY 运算符的典型情况：</span><span class="sxs-lookup"><span data-stu-id="f42f0-115">The following are some typical scenarios that might lead to the presence of CROSS APPLY and/or OUTER APPLY operators in the output query:</span></span>  
  
- <span data-ttu-id="f42f0-116">带分页的相关子查询。</span><span class="sxs-lookup"><span data-stu-id="f42f0-116">A correlated subquery with paging.</span></span>  
  
- <span data-ttu-id="f42f0-117">相关子查询或导航所生成的集合上的 `AnyElement`。</span><span class="sxs-lookup"><span data-stu-id="f42f0-117">An `AnyElement` over a correlated sub-query, or over a collection produced by navigation.</span></span>  
  
- <span data-ttu-id="f42f0-118">使用接受元素选择器的分组方法的 LINQ 查询。</span><span class="sxs-lookup"><span data-stu-id="f42f0-118">LINQ queries that use grouping methods that accept an element selector.</span></span>  
  
- <span data-ttu-id="f42f0-119">显式指定了 CROSS APPLY 或 OUTER APPLY 的查询</span><span class="sxs-lookup"><span data-stu-id="f42f0-119">A query in which a CROSS APPLY or an OUTER APPLY is explicitly specified</span></span>  
  
- <span data-ttu-id="f42f0-120">在 REF 构造上具有 DEREF 构造的查询。</span><span class="sxs-lookup"><span data-stu-id="f42f0-120">A query that has a DEREF construct over a REF construct.</span></span>  
  
## <a name="skip-operator"></a><span data-ttu-id="f42f0-121">SKIP 运算符</span><span class="sxs-lookup"><span data-stu-id="f42f0-121">SKIP Operator</span></span>  

 <span data-ttu-id="f42f0-122">如果使用的是 SQL Server 2000，则对非键列使用带有 ORDER BY 的 SKIP 可能会返回不正确的结果。</span><span class="sxs-lookup"><span data-stu-id="f42f0-122">If you are using SQL Server 2000, using SKIP with ORDER BY on non-key columns might return incorrect results.</span></span> <span data-ttu-id="f42f0-123">如果非键列中有重复数据，那么跳过的行数可能多于指定的行数。</span><span class="sxs-lookup"><span data-stu-id="f42f0-123">More than the specified number of rows might be skipped if the non-key column has duplicate data in it.</span></span> <span data-ttu-id="f42f0-124">这是因为如何为 SQL Server 2000 转换 SKIP。</span><span class="sxs-lookup"><span data-stu-id="f42f0-124">This is due to how SKIP is translated for SQL Server 2000.</span></span> <span data-ttu-id="f42f0-125">例如，在下面的查询中，如果 `E.NonKeyColumn` 有重复值，则跳过的行可能超过 5 行：</span><span class="sxs-lookup"><span data-stu-id="f42f0-125">For example, in the following query, more than five rows might be skipped if `E.NonKeyColumn` has duplicate values:</span></span>  
  
```sql  
SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L  
```  
  
## <a name="targeting-the-correct-sql-server-version"></a><span data-ttu-id="f42f0-126">以正确的 SQL Server 版本为目标</span><span class="sxs-lookup"><span data-stu-id="f42f0-126">Targeting the Correct SQL Server Version</span></span>  

 <span data-ttu-id="f42f0-127">实体框架根据 `ProviderManifestToken` 存储模型 ( ssdl) 文件中架构元素的属性中指定的 SQL Server 版本来面向 transact-sql 查询。</span><span class="sxs-lookup"><span data-stu-id="f42f0-127">The Entity Framework targets the Transact-SQL query based on the SQL Server version that is specified in the `ProviderManifestToken` attribute of the Schema element in the storage model (.ssdl) file.</span></span> <span data-ttu-id="f42f0-128">您实际连接到的 SQL Server 的版本可能不是这一版本。</span><span class="sxs-lookup"><span data-stu-id="f42f0-128">This version might differ from the version of the actual SQL Server you are connected to.</span></span> <span data-ttu-id="f42f0-129">例如，如果使用 SQL Server 2005，但 `ProviderManifestToken` 属性设置为2008，则生成的 transact-sql 查询可能不会在服务器上执行。</span><span class="sxs-lookup"><span data-stu-id="f42f0-129">For example, if you are using SQL Server 2005, but your `ProviderManifestToken` attribute is set to 2008, the generated Transact-SQL query might not execute on the server.</span></span> <span data-ttu-id="f42f0-130">例如，在 SQL Server 的早期版本上，无法执行使用了 SQL Server 2008 所引入的新日期时间类型的查询。</span><span class="sxs-lookup"><span data-stu-id="f42f0-130">For example, a query that uses the new date time types that were introduced in SQL Server 2008 will not execute on earlier versions of the SQL Server.</span></span> <span data-ttu-id="f42f0-131">如果你使用的是 SQL Server 2005，但你 `ProviderManifestToken` 的特性设置为2000，则生成的 transact-sql 查询可能比较少，或者你可能会收到一个异常，指出不支持该查询。</span><span class="sxs-lookup"><span data-stu-id="f42f0-131">If you are using SQL Server 2005, but your `ProviderManifestToken` attribute is set to 2000, the generated Transact-SQL query might be less optimized, or you might get an exception that says that the query is not supported.</span></span> <span data-ttu-id="f42f0-132">有关更多信息，请参见本主题前面的“CROSS 和 OUTER APPLY 运算符”部分。</span><span class="sxs-lookup"><span data-stu-id="f42f0-132">For more information, see the CROSS and OUTER APPLY Operators section, earlier in this topic.</span></span>  
  
 <span data-ttu-id="f42f0-133">某些数据库行为取决于为数据库设置的兼容级别。</span><span class="sxs-lookup"><span data-stu-id="f42f0-133">Certain database behaviors depend on the compatibility level set to the database.</span></span> <span data-ttu-id="f42f0-134">如果 `ProviderManifestToken` 将属性设置为2005，并且 SQL Server 版本为2005，但数据库的兼容级别设置为 "80" (SQL Server 2000) ，则生成的 transact-sql 将面向 SQL Server 2005，但可能无法按预期执行，因为兼容性级别设置。</span><span class="sxs-lookup"><span data-stu-id="f42f0-134">If your `ProviderManifestToken` attribute is set to 2005 and your SQL Server version is 2005, but the compatibility level of a database is set to "80" (SQL Server 2000), the generated Transact-SQL will be targeting SQL Server 2005, but might not execute as expected due to the compatibility level setting.</span></span> <span data-ttu-id="f42f0-135">例如，如果 ORDER BY 列表中的列名与选择器中的列名相同，则可能会丢失排序信息。</span><span class="sxs-lookup"><span data-stu-id="f42f0-135">For example, you might lose ordering information if a column name in the ORDER BY list matches a column name in the selector.</span></span>  
  
## <a name="nested-queries-in-projection"></a><span data-ttu-id="f42f0-136">投影中的嵌套查询</span><span class="sxs-lookup"><span data-stu-id="f42f0-136">Nested Queries in Projection</span></span>  

 <span data-ttu-id="f42f0-137">投影子句中的嵌套查询可在服务器上转换为笛卡尔积查询。</span><span class="sxs-lookup"><span data-stu-id="f42f0-137">Nested queries in a projection clause might get translated into Cartesian product queries on the server.</span></span> <span data-ttu-id="f42f0-138">在某些后端服务器（包括 SQL Server）上，这会导致 TempDB 表变得很大。</span><span class="sxs-lookup"><span data-stu-id="f42f0-138">On some back-end servers, including SQL Server, this can cause the TempDB table to get quite large.</span></span> <span data-ttu-id="f42f0-139">这样会降低服务器性能。</span><span class="sxs-lookup"><span data-stu-id="f42f0-139">This can decrease server performance.</span></span>  
  
 <span data-ttu-id="f42f0-140">下面是投影子句中嵌套查询的示例：</span><span class="sxs-lookup"><span data-stu-id="f42f0-140">The following is an example of a nested query in a projection clause:</span></span>  
  
```sql  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="server-generated-guid-identity-values"></a><span data-ttu-id="f42f0-141">服务器生成的 GUID 标识值</span><span class="sxs-lookup"><span data-stu-id="f42f0-141">Server Generated GUID Identity Values</span></span>  

 <span data-ttu-id="f42f0-142">实体框架支持服务器生成的 GUID 类型标识值，但提供程序必须支持在插入行后返回服务器生成的标识值。</span><span class="sxs-lookup"><span data-stu-id="f42f0-142">The Entity Framework supports server-generated GUID type identity values, but the provider must support returning the server-generated identity value after a row was inserted.</span></span> <span data-ttu-id="f42f0-143">从 SQL Server 2005 开始，可以通过 [OUTPUT 子句](/sql/t-sql/queries/output-clause-transact-sql)返回 SQL Server 数据库中服务器生成的 GUID 类型。</span><span class="sxs-lookup"><span data-stu-id="f42f0-143">Starting with SQL Server 2005, you can return the server-generated GUID type in a SQL Server database through the [OUTPUT clause](/sql/t-sql/queries/output-clause-transact-sql).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f42f0-144">请参阅</span><span class="sxs-lookup"><span data-stu-id="f42f0-144">See also</span></span>

- [<span data-ttu-id="f42f0-145">用于实体框架的 SqlClient</span><span class="sxs-lookup"><span data-stu-id="f42f0-145">SqlClient for the Entity Framework</span></span>](sqlclient-for-the-entity-framework.md)
- [<span data-ttu-id="f42f0-146">LINQ to Entities 中的已知问题和注意事项</span><span class="sxs-lookup"><span data-stu-id="f42f0-146">Known Issues and Considerations in LINQ to Entities</span></span>](./language-reference/known-issues-and-considerations-in-linq-to-entities.md)

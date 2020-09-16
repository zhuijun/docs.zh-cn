---
title: 撰写嵌套的 Entity SQL 查询
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: b28c46ba9a89ffffe8cd95ad55eb502eb8ea48a6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541091"
---
# <a name="composing-nested-entity-sql-queries"></a><span data-ttu-id="9790d-102">撰写嵌套的 Entity SQL 查询</span><span class="sxs-lookup"><span data-stu-id="9790d-102">Composing Nested Entity SQL Queries</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="9790d-103">是一种功能丰富的语言。</span><span class="sxs-lookup"><span data-stu-id="9790d-103">is a rich functional language.</span></span> <span data-ttu-id="9790d-104">的构建基块 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 是一个表达式。</span><span class="sxs-lookup"><span data-stu-id="9790d-104">The building block of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is an expression.</span></span> <span data-ttu-id="9790d-105">与传统的 SQL 不同， [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 并不局限于表格结果集： [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 支持组合可以具有文本、参数或嵌套表达式的复杂表达式。</span><span class="sxs-lookup"><span data-stu-id="9790d-105">Unlike conventional SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not limited to a tabular result set: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] supports composing complex expressions that can have literals, parameters, or nested expressions.</span></span> <span data-ttu-id="9790d-106">表达式中的值可以参数化，或者也可以由其他表达式构成。</span><span class="sxs-lookup"><span data-stu-id="9790d-106">A value in the expression can be parameterized or composed of some other expression.</span></span>  
  
## <a name="nested-expressions"></a><span data-ttu-id="9790d-107">嵌套表达式</span><span class="sxs-lookup"><span data-stu-id="9790d-107">Nested Expressions</span></span>  
 <span data-ttu-id="9790d-108">嵌套表达式可以放置在任何可接受其返回类型值的位置。</span><span class="sxs-lookup"><span data-stu-id="9790d-108">A nested expression can be placed anywhere a value of the type it returns is accepted.</span></span> <span data-ttu-id="9790d-109">例如：</span><span class="sxs-lookup"><span data-stu-id="9790d-109">For example:</span></span>  
  
```sql  
-- Returns a hierarchical collection of three elements at top-level.
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 <span data-ttu-id="9790d-110">嵌套查询可以放在投影子句中。</span><span class="sxs-lookup"><span data-stu-id="9790d-110">A nested query can be placed in a projection clause.</span></span> <span data-ttu-id="9790d-111">例如：</span><span class="sxs-lookup"><span data-stu-id="9790d-111">For example:</span></span>  
  
```sql  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 <span data-ttu-id="9790d-112">在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中，嵌套查询必须括在括号中：</span><span class="sxs-lookup"><span data-stu-id="9790d-112">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], nested queries must always be enclosed in parentheses:</span></span>  
  
```sql  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 <span data-ttu-id="9790d-113">下面的示例演示如何在中正确嵌套表达式 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ： [如何：对两个查询的并集进行排序](/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="9790d-113">The following example demonstrates how to properly nest expressions in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [How to: Order the Union of Two Queries](/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).</span></span>  
  
## <a name="nested-queries-in-projection"></a><span data-ttu-id="9790d-114">投影中的嵌套查询</span><span class="sxs-lookup"><span data-stu-id="9790d-114">Nested Queries in Projection</span></span>  
 <span data-ttu-id="9790d-115">投影子句中的嵌套查询可在服务器上转换为笛卡尔积查询。</span><span class="sxs-lookup"><span data-stu-id="9790d-115">Nested queries in the project clause might get translated into Cartesian product queries on the server.</span></span> <span data-ttu-id="9790d-116">在某些后端服务器（包括 SQL Server）中，这可能会导致 TempDB 表变得非常大，这可能会对服务器性能产生负面影响。</span><span class="sxs-lookup"><span data-stu-id="9790d-116">In some backend servers, including SQL Server, this can cause the TempDB table to get very large, which can adversely affect server performance.</span></span>  
  
 <span data-ttu-id="9790d-117">以下是这种查询的一个示例：</span><span class="sxs-lookup"><span data-stu-id="9790d-117">The following is an example of such a query:</span></span>  
  
```sql  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="9790d-118">嵌套查询排序</span><span class="sxs-lookup"><span data-stu-id="9790d-118">Ordering Nested Queries</span></span>  
 <span data-ttu-id="9790d-119">在实体框架中，嵌套表达式可置于查询中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="9790d-119">In the Entity Framework, a nested expression can be placed anywhere in the query.</span></span> <span data-ttu-id="9790d-120">Entity SQL 为编写查询提供了非常大的灵活性，可以在编写的查询中包含对嵌套查询的排序。</span><span class="sxs-lookup"><span data-stu-id="9790d-120">Because Entity SQL allows great flexibility in writing queries, it is possible to write a query that contains an ordering of nested queries.</span></span> <span data-ttu-id="9790d-121">但是，将不保留嵌套查询的顺序。</span><span class="sxs-lookup"><span data-stu-id="9790d-121">However, the order of a nested query is not preserved.</span></span>  
  
```sql  
-- The following query will order the results by last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```sql  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="see-also"></a><span data-ttu-id="9790d-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="9790d-122">See also</span></span>

- [<span data-ttu-id="9790d-123">Entity SQL 概述</span><span class="sxs-lookup"><span data-stu-id="9790d-123">Entity SQL Overview</span></span>](entity-sql-overview.md)

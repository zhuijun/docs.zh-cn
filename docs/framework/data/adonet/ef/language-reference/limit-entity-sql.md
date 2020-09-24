---
title: LIMIT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: 81d135785e567d46a105adcafbf083f48cb4868e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161758"
---
# <a name="limit-entity-sql"></a><span data-ttu-id="86bee-102">LIMIT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="86bee-102">LIMIT (Entity SQL)</span></span>

<span data-ttu-id="86bee-103">在 ORDER BY 子句中使用 LIMIT 子子句可执行物理分页。</span><span class="sxs-lookup"><span data-stu-id="86bee-103">Physical paging can be performed by using LIMIT sub-clause in ORDER BY clause.</span></span> <span data-ttu-id="86bee-104">LIMIT 不能脱离 ORDER BY 子句单独使用。</span><span class="sxs-lookup"><span data-stu-id="86bee-104">LIMIT can not be used separately from ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86bee-105">语法</span><span class="sxs-lookup"><span data-stu-id="86bee-105">Syntax</span></span>  
  
```sql  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="86bee-106">参数</span><span class="sxs-lookup"><span data-stu-id="86bee-106">Arguments</span></span>  

 `n`  
 <span data-ttu-id="86bee-107">将选择的项的数量。</span><span class="sxs-lookup"><span data-stu-id="86bee-107">The number of items that will be selected.</span></span>  
  
 <span data-ttu-id="86bee-108">如果 ORDER BY 子句中存在 LIMIT 表达式子子句，则将根据排序规范对查询排序，并且结果行数将受到 LIMIT 表达式限制。</span><span class="sxs-lookup"><span data-stu-id="86bee-108">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="86bee-109">例如，LIMIT 5 将结果集限制为 5 个实例或行。</span><span class="sxs-lookup"><span data-stu-id="86bee-109">For instance, LIMIT 5 will restrict the result set to 5 instances or rows.</span></span> <span data-ttu-id="86bee-110">LIMIT 的功能与 TOP 相当，区别之处是 LIMIT 要求 ORDER BY 子句存在。</span><span class="sxs-lookup"><span data-stu-id="86bee-110">LIMIT is functionally equivalent to TOP with the exception that LIMIT requires ORDER BY clause to be present.</span></span> <span data-ttu-id="86bee-111">SKIP 和 LIMIT 可独立与 ORDER BY 子句一起使用。</span><span class="sxs-lookup"><span data-stu-id="86bee-111">SKIP and LIMIT can be used independently along with ORDER BY clause.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="86bee-112">如果 TOP 修饰符和 SKIP 子子句出现在同一个查询表达式中，Entity SQL 查询将被视为无效。</span><span class="sxs-lookup"><span data-stu-id="86bee-112">An Entity Sql query will be considered invalid if TOP modifier and SKIP sub-clause is present in the same query expression.</span></span> <span data-ttu-id="86bee-113">应重写查询，将 TOP 表达式更改为 LIMIT 表达式。</span><span class="sxs-lookup"><span data-stu-id="86bee-113">The query should be rewritten by changing TOP expression to LIMIT expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86bee-114">示例</span><span class="sxs-lookup"><span data-stu-id="86bee-114">Example</span></span>  

 <span data-ttu-id="86bee-115">下面的 Entity SQL 查询将 LIMIT 和 ORDER BY 运算符结合使用来指定用于 SELECT 语句所返回的对象的排序顺序。</span><span class="sxs-lookup"><span data-stu-id="86bee-115">The following Entity SQL query uses the ORDER BY operator with LIMIT to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="86bee-116">此查询基于 AdventureWorks 销售模型。</span><span class="sxs-lookup"><span data-stu-id="86bee-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="86bee-117">若要编译并运行此查询，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="86bee-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="86bee-118">执行 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的过程。</span><span class="sxs-lookup"><span data-stu-id="86bee-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="86bee-119">将以下查询作为参数传递给 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="86bee-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LIMIT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#limit)]  
  
## <a name="see-also"></a><span data-ttu-id="86bee-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="86bee-120">See also</span></span>

- [<span data-ttu-id="86bee-121">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="86bee-121">ORDER BY</span></span>](order-by-entity-sql.md)
- <span data-ttu-id="86bee-122">[如何：按页查看查询结果](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="86bee-122">[How to: Page Through Query Results](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
- [<span data-ttu-id="86bee-123">分页</span><span class="sxs-lookup"><span data-stu-id="86bee-123">Paging</span></span>](paging-entity-sql.md)
- [<span data-ttu-id="86bee-124">TOP</span><span class="sxs-lookup"><span data-stu-id="86bee-124">TOP</span></span>](top-entity-sql.md)

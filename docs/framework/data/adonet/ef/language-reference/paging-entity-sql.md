---
title: 分页 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
ms.openlocfilehash: 42f685e0b84109f3099b501b2a75e681af1ea1bb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177470"
---
# <a name="paging-entity-sql"></a><span data-ttu-id="64355-102">分页 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="64355-102">Paging (Entity SQL)</span></span>

<span data-ttu-id="64355-103">通过在[ORDER by](order-by-entity-sql.md)子句中使用[SKIP](skip-entity-sql.md)和[LIMIT](limit-entity-sql.md)子子句可执行物理分页。</span><span class="sxs-lookup"><span data-stu-id="64355-103">Physical paging can be performed by using the [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses in the [ORDER BY](order-by-entity-sql.md) clause.</span></span> <span data-ttu-id="64355-104">若要以确定的方式执行物理分页，应使用 SKIP 和 LIMIT。</span><span class="sxs-lookup"><span data-stu-id="64355-104">To perform physical paging deterministically, you should use SKIP and LIMIT.</span></span> <span data-ttu-id="64355-105">如果只想按不确定的方式限制结果中的行数，则应使用 [TOP](top-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="64355-105">If you only want to restrict the number of rows in the result in a non-deterministic way, you should use [TOP](top-entity-sql.md).</span></span> <span data-ttu-id="64355-106">TOP 和 SKIP/LIMIT 是互斥的。</span><span class="sxs-lookup"><span data-stu-id="64355-106">TOP and SKIP/LIMIT are mutually exclusive.</span></span>  
  
## <a name="top-overview"></a><span data-ttu-id="64355-107">TOP 概述</span><span class="sxs-lookup"><span data-stu-id="64355-107">TOP Overview</span></span>  

 <span data-ttu-id="64355-108">SELECT 子句可以在可选的 ALL/DISTINCT 修饰符之后具有可选的 TOP 子子句。</span><span class="sxs-lookup"><span data-stu-id="64355-108">The SELECT clause can have an optional TOP sub-clause following the optional ALL/DISTINCT modifier.</span></span> <span data-ttu-id="64355-109">TOP 子子句指定查询结果中将只返回第一组行。</span><span class="sxs-lookup"><span data-stu-id="64355-109">The TOP sub-clause specifies that only the first set of rows will be returned from the query result.</span></span> <span data-ttu-id="64355-110">有关详细信息，请参阅 [顶部](top-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="64355-110">For more information, see [TOP](top-entity-sql.md).</span></span>  
  
## <a name="skip-and-limit-overview"></a><span data-ttu-id="64355-111">SKIP 和 LIMIT 概述</span><span class="sxs-lookup"><span data-stu-id="64355-111">SKIP And LIMIT Overview</span></span>  

 <span data-ttu-id="64355-112">SKIP 和 LIMIT 是 ORDER BY 子句的组成部分。</span><span class="sxs-lookup"><span data-stu-id="64355-112">SKIP and LIMIT are part of the ORDER BY clause.</span></span> <span data-ttu-id="64355-113">如果 ORDER BY 子句中存在 SKIP 表达式子子句，则将根据排序规范对结果排序，结果集将包含从紧接着 SKIP 表达式之后的下一行开始的行。</span><span class="sxs-lookup"><span data-stu-id="64355-113">If a SKIP expression sub-clause is present in a ORDER BY clause, the results will be sorted according to the sort specification and the result set will include row(s) starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="64355-114">例如，SKIP 5 将跳过前五行，并返回第六行以及后续行。</span><span class="sxs-lookup"><span data-stu-id="64355-114">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span> <span data-ttu-id="64355-115">如果 ORDER BY 子句中存在 LIMIT 表达式子子句，则将根据排序规范对查询排序，并且结果行数将受到 LIMIT 表达式限制。</span><span class="sxs-lookup"><span data-stu-id="64355-115">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="64355-116">例如，LIMIT 5 将结果集限制为五个实例或行。</span><span class="sxs-lookup"><span data-stu-id="64355-116">For instance, LIMIT 5 will restrict the result set to five instances or rows.</span></span> <span data-ttu-id="64355-117">SKIP 和 LIMIT 不必一起使用，可以只将 SKIP 或 LIMIT 用于 ORDER BY 子句。</span><span class="sxs-lookup"><span data-stu-id="64355-117">SKIP and LIMIT do not have to be used together; you can use just SKIP or just LIMIT with ORDER BY clause.</span></span> <span data-ttu-id="64355-118">有关详情，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="64355-118">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="64355-119">SKIP</span><span class="sxs-lookup"><span data-stu-id="64355-119">SKIP</span></span>](skip-entity-sql.md)  
  
- [<span data-ttu-id="64355-120">上限</span><span class="sxs-lookup"><span data-stu-id="64355-120">LIMIT</span></span>](limit-entity-sql.md)  
  
- [<span data-ttu-id="64355-121">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="64355-121">ORDER BY</span></span>](order-by-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="64355-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="64355-122">See also</span></span>

- [<span data-ttu-id="64355-123">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="64355-123">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="64355-124">Entity SQL 概述</span><span class="sxs-lookup"><span data-stu-id="64355-124">Entity SQL Overview</span></span>](entity-sql-overview.md)
- <span data-ttu-id="64355-125">[如何：按页查看查询结果](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="64355-125">[How to: Page Through Query Results](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>

---
title: 查询表达式 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
ms.openlocfilehash: ca6b79b4b3d3326a74780345decf58367596adb0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175598"
---
# <a name="query-expressions-entity-sql"></a><span data-ttu-id="ebdd9-102">查询表达式 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ebdd9-102">Query Expressions (Entity SQL)</span></span>

<span data-ttu-id="ebdd9-103">查询表达式将许多不同的查询运算符组合成单个语法。</span><span class="sxs-lookup"><span data-stu-id="ebdd9-103">A query expression combines many different query operators into a single syntax.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="ebdd9-104">提供各种类型的表达式，包括： [文本](literals-entity-sql.md)、 [参数](parameters-entity-sql.md)、 [变量](variables-entity-sql.md)、运算符、 [函数](functions-entity-sql.md)、集运算符等等。</span><span class="sxs-lookup"><span data-stu-id="ebdd9-104">provides various kinds of expressions, including the following: [literals](literals-entity-sql.md), [parameters](parameters-entity-sql.md), [variables](variables-entity-sql.md), operators, [functions](functions-entity-sql.md), set operators, and so on.</span></span> <span data-ttu-id="ebdd9-105">有关详细信息，请参阅 [实体 SQL 引用](entity-sql-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="ebdd9-105">For more information, see [Entity SQL Reference](entity-sql-reference.md).</span></span>  
  
## <a name="clauses"></a><span data-ttu-id="ebdd9-106">子句</span><span class="sxs-lookup"><span data-stu-id="ebdd9-106">Clauses</span></span>  

 <span data-ttu-id="ebdd9-107">查询表达式由一系列子句组成，这些子句将连续的操作应用于一个对象集合。</span><span class="sxs-lookup"><span data-stu-id="ebdd9-107">A query expression is composed of a series of clauses that apply successive operations to a collection of objects.</span></span> <span data-ttu-id="ebdd9-108">它们基于在标准 SQL select 语句中找到的相同子句： [select](select-entity-sql.md)、 [FROM](from-entity-sql.md)、 [WHERE](where-entity-sql.md)、 [GROUP BY](group-by-entity-sql.md)、 [HAVING](having-entity-sql.md)和 [ORDER by](order-by-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="ebdd9-108">They are based on the same clauses found in standard a SQL select statement: [SELECT](select-entity-sql.md), [FROM](from-entity-sql.md), [WHERE](where-entity-sql.md), [GROUP BY](group-by-entity-sql.md), [HAVING](having-entity-sql.md), and [ORDER BY](order-by-entity-sql.md).</span></span>  
  
## <a name="scope"></a><span data-ttu-id="ebdd9-109">范围</span><span class="sxs-lookup"><span data-stu-id="ebdd9-109">Scope</span></span>  

 <span data-ttu-id="ebdd9-110">在 FROM 子句中定义的名称以从左到右的出现顺序引入到 FROM 作用域。</span><span class="sxs-lookup"><span data-stu-id="ebdd9-110">Names defined in the FROM clause are introduced into the FROM scope in order of appearance, left to right.</span></span> <span data-ttu-id="ebdd9-111">在 JOIN 列表中，表达式可以引用以前在列表中定义的名称。</span><span class="sxs-lookup"><span data-stu-id="ebdd9-111">In the JOIN list, expressions can refer to names defined earlier in the list.</span></span> <span data-ttu-id="ebdd9-112">在 FROM 子句中标识的元素的公共属性不添加到 FROM 作用域：始终必须通过别名限定名称来引用这些属性。</span><span class="sxs-lookup"><span data-stu-id="ebdd9-112">Public properties of elements identified in the FROM clause are not added to the FROM scope: They must be always referenced through the alias-qualified name.</span></span> <span data-ttu-id="ebdd9-113">通常，SELECT 表达式的所有部分都视作在 FROM 作用域内。</span><span class="sxs-lookup"><span data-stu-id="ebdd9-113">Normally, all parts of the select expression are considered within the FROM scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebdd9-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="ebdd9-114">See also</span></span>

- [<span data-ttu-id="ebdd9-115">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="ebdd9-115">Entity SQL Reference</span></span>](entity-sql-reference.md)

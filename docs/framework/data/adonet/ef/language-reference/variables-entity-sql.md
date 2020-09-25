---
title: 变量 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: af6d586a22f14a04bfc7ec339d0aa8e9ba7c66c7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180993"
---
# <a name="variables-entity-sql"></a><span data-ttu-id="db538-102">变量 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="db538-102">Variables (Entity SQL)</span></span>

## <a name="variable"></a><span data-ttu-id="db538-103">变量</span><span class="sxs-lookup"><span data-stu-id="db538-103">Variable</span></span>  

 <span data-ttu-id="db538-104">变量表达式是对当前作用域中定义的命名表达式的引用。</span><span class="sxs-lookup"><span data-stu-id="db538-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="db538-105">变量引用必须是 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] [标识符](identifiers-entity-sql.md)中定义的有效标识符。</span><span class="sxs-lookup"><span data-stu-id="db538-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="db538-106">以下示例演示如何在表达式中使用变量。</span><span class="sxs-lookup"><span data-stu-id="db538-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="db538-107">FROM 子句中的 `c` 是变量定义。</span><span class="sxs-lookup"><span data-stu-id="db538-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="db538-108">在 SELECT 子句中使用的 `c` 表示变量引用。</span><span class="sxs-lookup"><span data-stu-id="db538-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```sql  
select c
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="db538-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="db538-109">See also</span></span>

- [<span data-ttu-id="db538-110">标识符</span><span class="sxs-lookup"><span data-stu-id="db538-110">Identifiers</span></span>](identifiers-entity-sql.md)
- [<span data-ttu-id="db538-111">参数</span><span class="sxs-lookup"><span data-stu-id="db538-111">Parameters</span></span>](parameters-entity-sql.md)
- [<span data-ttu-id="db538-112">Entity SQL 概述</span><span class="sxs-lookup"><span data-stu-id="db538-112">Entity SQL Overview</span></span>](entity-sql-overview.md)

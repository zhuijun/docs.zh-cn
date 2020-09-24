---
title: '! (NOT) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 0eb9be9ed4cbce45a51d15eea68e9fb1a26f0107
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191835"
---
# <a name="-not-entity-sql"></a><span data-ttu-id="0771d-103">!</span><span class="sxs-lookup"><span data-stu-id="0771d-103">!</span></span> <span data-ttu-id="0771d-104">(NOT) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0771d-104">(NOT) (Entity SQL)</span></span>

<span data-ttu-id="0771d-105">对 `Boolean` 表达式求反。</span><span class="sxs-lookup"><span data-stu-id="0771d-105">Negates a `Boolean` expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0771d-106">语法</span><span class="sxs-lookup"><span data-stu-id="0771d-106">Syntax</span></span>  
  
```sql  
NOT boolean_expression  
-- or  
! boolean_expression  
```
  
## <a name="arguments"></a><span data-ttu-id="0771d-107">参数</span><span class="sxs-lookup"><span data-stu-id="0771d-107">Arguments</span></span>  

 `boolean_expression`  
 <span data-ttu-id="0771d-108">返回 Boolean 的任何有效表达式。</span><span class="sxs-lookup"><span data-stu-id="0771d-108">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0771d-109">备注</span><span class="sxs-lookup"><span data-stu-id="0771d-109">Remarks</span></span>  

 <span data-ttu-id="0771d-110">惊叹号 (!) 与 NOT 运算符具有相同的功能。</span><span class="sxs-lookup"><span data-stu-id="0771d-110">The exclamation point (!) has the same functionality as the NOT operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0771d-111">示例</span><span class="sxs-lookup"><span data-stu-id="0771d-111">Example</span></span>  

 <span data-ttu-id="0771d-112">以下 Entity SQL 查询使用 NOT 运算符以对 `Boolean` 表达式求反。</span><span class="sxs-lookup"><span data-stu-id="0771d-112">The following Entity SQL query uses the NOT operator to negates a `Boolean` expression.</span></span> <span data-ttu-id="0771d-113">此查询基于 AdventureWorks 销售模型。</span><span class="sxs-lookup"><span data-stu-id="0771d-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0771d-114">若要编译并运行此查询，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="0771d-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="0771d-115">执行 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的过程。</span><span class="sxs-lookup"><span data-stu-id="0771d-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="0771d-116">将以下查询作为参数传递给 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="0771d-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NOT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not)]  
  
## <a name="see-also"></a><span data-ttu-id="0771d-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="0771d-117">See also</span></span>

- [<span data-ttu-id="0771d-118">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="0771d-118">Entity SQL Reference</span></span>](entity-sql-reference.md)

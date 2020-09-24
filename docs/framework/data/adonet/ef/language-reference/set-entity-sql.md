---
title: SET (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: 2ac7db5b22ad21eb152788b6c6d6a8e65c1f6a7b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169630"
---
# <a name="set-entity-sql"></a><span data-ttu-id="72ff0-102">SET (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="72ff0-102">SET (Entity SQL)</span></span>

<span data-ttu-id="72ff0-103">SET 表达式用于通过生成一个新集合（其中移除了所有重复元素）将对象集合转换为一个集。</span><span class="sxs-lookup"><span data-stu-id="72ff0-103">The SET expression is used to convert a collection of objects into a set by yielding a new collection with all duplicate elements removed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72ff0-104">语法</span><span class="sxs-lookup"><span data-stu-id="72ff0-104">Syntax</span></span>  
  
```sql  
SET ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="72ff0-105">参数</span><span class="sxs-lookup"><span data-stu-id="72ff0-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="72ff0-106">任何返回集合的有效查询表达式。</span><span class="sxs-lookup"><span data-stu-id="72ff0-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72ff0-107">备注</span><span class="sxs-lookup"><span data-stu-id="72ff0-107">Remarks</span></span>  

 <span data-ttu-id="72ff0-108">SET 表达式 `SET(c)` 在逻辑上等效于以下 select 语句：</span><span class="sxs-lookup"><span data-stu-id="72ff0-108">The set expression `SET(c)` is logically equivalent to the following select statement:</span></span>  
  
```sql  
SELECT VALUE DISTINCT c FROM c  
```  
  
 <span data-ttu-id="72ff0-109">`SET` 是 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 集运算符之一。</span><span class="sxs-lookup"><span data-stu-id="72ff0-109">`SET` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="72ff0-110">所有 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 集运算符都是从左到右进行求值。</span><span class="sxs-lookup"><span data-stu-id="72ff0-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="72ff0-111">有关集运算符 [的优先级信息，请参阅](except-entity-sql.md) [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="72ff0-111">See [EXCEPT](except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72ff0-112">示例</span><span class="sxs-lookup"><span data-stu-id="72ff0-112">Example</span></span>  

 <span data-ttu-id="72ff0-113">以下 Entity SQL 查询使用 SET 表达式将一个对象集合转换为一个集。</span><span class="sxs-lookup"><span data-stu-id="72ff0-113">The following Entity SQL query uses the SET expression to convert a collection of objects into a set.</span></span> <span data-ttu-id="72ff0-114">此查询基于 AdventureWorks 销售模型。</span><span class="sxs-lookup"><span data-stu-id="72ff0-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="72ff0-115">若要编译并运行此查询，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="72ff0-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="72ff0-116">按照 [如何：执行返回 PrimitiveType 结果的查询](../how-to-execute-a-query-that-returns-primitivetype-results.md)中的过程进行操作。</span><span class="sxs-lookup"><span data-stu-id="72ff0-116">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="72ff0-117">将以下查询作为参数传递给 `ExecutePrimitiveTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="72ff0-117">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#SET](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#set)]  
  
## <a name="see-also"></a><span data-ttu-id="72ff0-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="72ff0-118">See also</span></span>

- [<span data-ttu-id="72ff0-119">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="72ff0-119">Entity SQL Reference</span></span>](entity-sql-reference.md)

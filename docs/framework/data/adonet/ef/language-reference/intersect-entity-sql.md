---
title: INTERSECT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 93c6fe33-f341-4b52-911e-adf503891951
ms.openlocfilehash: 217cd9b2a428c890d83d2b55d45321a04488398e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203639"
---
# <a name="intersect-entity-sql"></a><span data-ttu-id="cf041-102">INTERSECT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="cf041-102">INTERSECT (Entity SQL)</span></span>

<span data-ttu-id="cf041-103">返回 INTERSECT 操作数左右两边的两个查询表达式均返回的所有非重复值的集合。</span><span class="sxs-lookup"><span data-stu-id="cf041-103">Returns a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="cf041-104">所有表达式都必须与 `expression`一样属于同一类型或属于公共基类型或派生类型。</span><span class="sxs-lookup"><span data-stu-id="cf041-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf041-105">语法</span><span class="sxs-lookup"><span data-stu-id="cf041-105">Syntax</span></span>  
  
```sql  
expression INTERSECT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="cf041-106">参数</span><span class="sxs-lookup"><span data-stu-id="cf041-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="cf041-107">返回一个集合以与从其他查询表达式返回的集合进行比较的任何有效查询表达式。</span><span class="sxs-lookup"><span data-stu-id="cf041-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cf041-108">返回值</span><span class="sxs-lookup"><span data-stu-id="cf041-108">Return Value</span></span>  

 <span data-ttu-id="cf041-109">与 `expression`具有相同类型或属于公共基类型或派生类型的一个集合。</span><span class="sxs-lookup"><span data-stu-id="cf041-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf041-110">备注</span><span class="sxs-lookup"><span data-stu-id="cf041-110">Remarks</span></span>  

 <span data-ttu-id="cf041-111">INTERSECT 是 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 集运算符之一。</span><span class="sxs-lookup"><span data-stu-id="cf041-111">INTERSECT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="cf041-112">所有 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 集运算符都是从左到右进行求值。</span><span class="sxs-lookup"><span data-stu-id="cf041-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="cf041-113">有关集运算符的优先级信息 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ，请参阅 [EXCEPT](except-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="cf041-113">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf041-114">示例</span><span class="sxs-lookup"><span data-stu-id="cf041-114">Example</span></span>  

 <span data-ttu-id="cf041-115">以下 Entity SQL 查询使用 INTERSECT 运算符以返回 INTERSECT 操作数左右两边的两个查询表达式均返回的所有非重复值的集合。</span><span class="sxs-lookup"><span data-stu-id="cf041-115">The following Entity SQL query uses the INTERSECT operator to return a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="cf041-116">此查询基于 AdventureWorks 销售模型。</span><span class="sxs-lookup"><span data-stu-id="cf041-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="cf041-117">若要编译并运行此查询，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="cf041-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="cf041-118">执行 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的过程。</span><span class="sxs-lookup"><span data-stu-id="cf041-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="cf041-119">将以下查询作为参数传递给 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="cf041-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#INTERSECT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#intersect)]  
  
## <a name="see-also"></a><span data-ttu-id="cf041-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="cf041-120">See also</span></span>

- [<span data-ttu-id="cf041-121">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="cf041-121">Entity SQL Reference</span></span>](entity-sql-reference.md)

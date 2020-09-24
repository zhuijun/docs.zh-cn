---
title: EXISTS (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
ms.openlocfilehash: f08b3ea60a985e56e05e4686cd531f94e0bd4e18
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166763"
---
# <a name="exists-entity-sql"></a><span data-ttu-id="91a0b-102">EXISTS (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="91a0b-102">EXISTS (Entity SQL)</span></span>

<span data-ttu-id="91a0b-103">确定集合是否为空。</span><span class="sxs-lookup"><span data-stu-id="91a0b-103">Determines if a collection is empty.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91a0b-104">语法</span><span class="sxs-lookup"><span data-stu-id="91a0b-104">Syntax</span></span>  
  
```sql  
[NOT] EXISTS ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="91a0b-105">参数</span><span class="sxs-lookup"><span data-stu-id="91a0b-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="91a0b-106">返回集合的任何有效的表达式。</span><span class="sxs-lookup"><span data-stu-id="91a0b-106">Any valid expression that returns a collection.</span></span>  
  
 <span data-ttu-id="91a0b-107">NOT</span><span class="sxs-lookup"><span data-stu-id="91a0b-107">NOT</span></span>  
 <span data-ttu-id="91a0b-108">指定对 EXISTS 的结果取反。</span><span class="sxs-lookup"><span data-stu-id="91a0b-108">Specifies that the result of EXISTS be negated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91a0b-109">返回值</span><span class="sxs-lookup"><span data-stu-id="91a0b-109">Return Value</span></span>  

 <span data-ttu-id="91a0b-110">如果集合不为空，则为 `true`；否则为 `false`。</span><span class="sxs-lookup"><span data-stu-id="91a0b-110">`true` if the collection is not empty; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91a0b-111">备注</span><span class="sxs-lookup"><span data-stu-id="91a0b-111">Remarks</span></span>  

 <span data-ttu-id="91a0b-112">EXISTS 是 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 集运算符之一。</span><span class="sxs-lookup"><span data-stu-id="91a0b-112">EXISTS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="91a0b-113">所有 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 集运算符都是从左到右进行求值。</span><span class="sxs-lookup"><span data-stu-id="91a0b-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="91a0b-114">有关集运算符的优先级信息 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ，请参阅 [EXCEPT](except-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="91a0b-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="91a0b-115">示例</span><span class="sxs-lookup"><span data-stu-id="91a0b-115">Example</span></span>  

 <span data-ttu-id="91a0b-116">以下 Entity SQL 查询使用 EXISTS 运算符以确定集合是否为空。</span><span class="sxs-lookup"><span data-stu-id="91a0b-116">The following Entity SQL query uses the EXISTS operator to determine whether the collection is empty.</span></span> <span data-ttu-id="91a0b-117">此查询基于 AdventureWorks 销售模型。</span><span class="sxs-lookup"><span data-stu-id="91a0b-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="91a0b-118">若要编译并运行此查询，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="91a0b-118">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="91a0b-119">执行 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的过程。</span><span class="sxs-lookup"><span data-stu-id="91a0b-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="91a0b-120">将以下查询作为参数传递给 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="91a0b-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EXISTS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#exists)]  
  
## <a name="see-also"></a><span data-ttu-id="91a0b-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="91a0b-121">See also</span></span>

- [<span data-ttu-id="91a0b-122">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="91a0b-122">Entity SQL Reference</span></span>](entity-sql-reference.md)

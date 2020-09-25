---
title: '!=（不等于）(Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: bebe85072f5a2cf6a133b88c6d3f5c97299aa63f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191770"
---
# <a name="-not-equal-to-entity-sql"></a><span data-ttu-id="021a3-102">!=（不等于）(Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="021a3-102">!= (Not Equal To) (Entity SQL)</span></span>

<span data-ttu-id="021a3-103">比较两个表达式以确定左侧表达式是否不等于右侧表达式。</span><span class="sxs-lookup"><span data-stu-id="021a3-103">Compares two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="021a3-104">!=（不等于）运算符在功能上等效于 <> 运算符。</span><span class="sxs-lookup"><span data-stu-id="021a3-104">The != (Not Equal To) operator is functionally equivalent to the <> operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="021a3-105">语法</span><span class="sxs-lookup"><span data-stu-id="021a3-105">Syntax</span></span>  
  
```sql  
expression != expression  
-- or  
expression <> expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="021a3-106">参数</span><span class="sxs-lookup"><span data-stu-id="021a3-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="021a3-107">任何有效表达式。</span><span class="sxs-lookup"><span data-stu-id="021a3-107">Any valid expression.</span></span> <span data-ttu-id="021a3-108">两个表达式都必须包含可隐式转换的数据类型。</span><span class="sxs-lookup"><span data-stu-id="021a3-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="021a3-109">结果类型</span><span class="sxs-lookup"><span data-stu-id="021a3-109">Result Types</span></span>  

 <span data-ttu-id="021a3-110">如果左侧表达式不等于右侧表达式，则为`true` ；否则为 `false`。</span><span class="sxs-lookup"><span data-stu-id="021a3-110">`true` if the left expression is not equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="021a3-111">示例</span><span class="sxs-lookup"><span data-stu-id="021a3-111">Example</span></span>  

 <span data-ttu-id="021a3-112">下面的 Entity SQL 查询使用 != 运算符比较两个表达式，以确定左侧表达式是否不等于右侧表达式。</span><span class="sxs-lookup"><span data-stu-id="021a3-112">The following Entity SQL query uses the != operator to compare two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="021a3-113">此查询基于 AdventureWorks 销售模型。</span><span class="sxs-lookup"><span data-stu-id="021a3-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="021a3-114">若要编译并运行此查询，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="021a3-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="021a3-115">执行 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的过程。</span><span class="sxs-lookup"><span data-stu-id="021a3-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="021a3-116">将以下查询作为参数传递给 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="021a3-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NOT_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="021a3-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="021a3-117">See also</span></span>

- [<span data-ttu-id="021a3-118">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="021a3-118">Entity SQL Reference</span></span>](entity-sql-reference.md)

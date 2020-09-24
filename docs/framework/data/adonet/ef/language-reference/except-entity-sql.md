---
title: EXCEPT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: 6797f8038a83533b5a6bd41ad402daec7abdc7de
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148044"
---
# <a name="except-entity-sql"></a><span data-ttu-id="08828-102">EXCEPT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="08828-102">EXCEPT (Entity SQL)</span></span>

<span data-ttu-id="08828-103">返回由 EXCEPT 操作数左侧的查询表达式返回而不由 EXCEPT 操作数右侧的查询表达式返回的任何非重复值的集合。</span><span class="sxs-lookup"><span data-stu-id="08828-103">Returns a collection of any distinct values from the query expression to the left of the EXCEPT operand that are not also returned from the query expression to the right of the EXCEPT operand.</span></span> <span data-ttu-id="08828-104">所有表达式都必须与 `expression`一样属于同一类型或属于公共基类型或派生类型。</span><span class="sxs-lookup"><span data-stu-id="08828-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08828-105">语法</span><span class="sxs-lookup"><span data-stu-id="08828-105">Syntax</span></span>  
  
```sql  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="08828-106">参数</span><span class="sxs-lookup"><span data-stu-id="08828-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="08828-107">返回一个集合以与从其他查询表达式返回的集合进行比较的任何有效查询表达式。</span><span class="sxs-lookup"><span data-stu-id="08828-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08828-108">返回值</span><span class="sxs-lookup"><span data-stu-id="08828-108">Return Value</span></span>  

 <span data-ttu-id="08828-109">与 `expression`具有相同类型或属于公共基类型或派生类型的一个集合。</span><span class="sxs-lookup"><span data-stu-id="08828-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08828-110">备注</span><span class="sxs-lookup"><span data-stu-id="08828-110">Remarks</span></span>  

 <span data-ttu-id="08828-111">EXCEPT 是 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 集运算符之一。</span><span class="sxs-lookup"><span data-stu-id="08828-111">EXCEPT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="08828-112">所有 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 集运算符都是从左到右进行求值。</span><span class="sxs-lookup"><span data-stu-id="08828-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="08828-113">下表显示 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 集运算符的优先级。</span><span class="sxs-lookup"><span data-stu-id="08828-113">The following table shows the precedence of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
|<span data-ttu-id="08828-114">优先级</span><span class="sxs-lookup"><span data-stu-id="08828-114">Precedence</span></span>|<span data-ttu-id="08828-115">运算符</span><span class="sxs-lookup"><span data-stu-id="08828-115">Operators</span></span>|  
|----------------|---------------|  
|<span data-ttu-id="08828-116">最高</span><span class="sxs-lookup"><span data-stu-id="08828-116">Highest</span></span>|<span data-ttu-id="08828-117">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="08828-117">INTERSECT</span></span>|  
||<span data-ttu-id="08828-118">UNION</span><span class="sxs-lookup"><span data-stu-id="08828-118">UNION</span></span><br /><br /> <span data-ttu-id="08828-119">UNION ALL</span><span class="sxs-lookup"><span data-stu-id="08828-119">UNION ALL</span></span>|  
||<span data-ttu-id="08828-120">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="08828-120">EXCEPT</span></span>|  
|<span data-ttu-id="08828-121">最低</span><span class="sxs-lookup"><span data-stu-id="08828-121">Lowest</span></span>|<span data-ttu-id="08828-122">EXISTS</span><span class="sxs-lookup"><span data-stu-id="08828-122">EXISTS</span></span><br /><br /> <span data-ttu-id="08828-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="08828-123">OVERLAPS</span></span><br /><br /> <span data-ttu-id="08828-124">FLATTEN</span><span class="sxs-lookup"><span data-stu-id="08828-124">FLATTEN</span></span><br /><br /> <span data-ttu-id="08828-125">SET</span><span class="sxs-lookup"><span data-stu-id="08828-125">SET</span></span>|  
  
## <a name="example"></a><span data-ttu-id="08828-126">示例</span><span class="sxs-lookup"><span data-stu-id="08828-126">Example</span></span>  

 <span data-ttu-id="08828-127">以下 Entity SQL 查询使用 EXCEPT 运算符以返回从两个查询表达式返回的任何非重复值的集合。</span><span class="sxs-lookup"><span data-stu-id="08828-127">The following Entity SQL query uses the EXCEPT operator to return a collection of any distinct values from two query expressions.</span></span> <span data-ttu-id="08828-128">此查询基于 AdventureWorks 销售模型。</span><span class="sxs-lookup"><span data-stu-id="08828-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="08828-129">若要编译并运行此查询，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="08828-129">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="08828-130">执行 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的过程。</span><span class="sxs-lookup"><span data-stu-id="08828-130">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="08828-131">将以下查询作为参数传递给 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="08828-131">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EXCEPT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#except)]  
  
## <a name="see-also"></a><span data-ttu-id="08828-132">请参阅</span><span class="sxs-lookup"><span data-stu-id="08828-132">See also</span></span>

- [<span data-ttu-id="08828-133">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="08828-133">Entity SQL Reference</span></span>](entity-sql-reference.md)

---
title: '|| (OR) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: 89c0a92030f2f067d5e5d45b58d475414a224ce4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150799"
---
# <a name="-or-entity-sql"></a><span data-ttu-id="1e058-102">|| (OR) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1e058-102">|| (OR) (Entity SQL)</span></span>

<span data-ttu-id="1e058-103">组合两个 `Boolean` 表达式。</span><span class="sxs-lookup"><span data-stu-id="1e058-103">Combines two `Boolean` expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e058-104">语法</span><span class="sxs-lookup"><span data-stu-id="1e058-104">Syntax</span></span>  
  
```sql  
boolean_expression OR boolean_expression  
-- or
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="1e058-105">参数</span><span class="sxs-lookup"><span data-stu-id="1e058-105">Arguments</span></span>  

 `boolean_expression`  
 <span data-ttu-id="1e058-106">返回 `Boolean`的任何有效表达式。</span><span class="sxs-lookup"><span data-stu-id="1e058-106">Any valid expression that returns a `Boolean`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e058-107">返回值</span><span class="sxs-lookup"><span data-stu-id="1e058-107">Return Value</span></span>  

 <span data-ttu-id="1e058-108">当任何一个条件为`true` 时，为 `true`；否则为 `false`。</span><span class="sxs-lookup"><span data-stu-id="1e058-108">`true` when either of the conditions is `true`; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e058-109">备注</span><span class="sxs-lookup"><span data-stu-id="1e058-109">Remarks</span></span>  

 <span data-ttu-id="1e058-110">OR 是 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 逻辑运算符。</span><span class="sxs-lookup"><span data-stu-id="1e058-110">OR is an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] logical operator.</span></span> <span data-ttu-id="1e058-111">它用于组合两个条件。</span><span class="sxs-lookup"><span data-stu-id="1e058-111">It is used to combine two conditions.</span></span> <span data-ttu-id="1e058-112">在一个语句中使用多个逻辑运算符时，在 AND 运算符之后对 OR 运算符求值。</span><span class="sxs-lookup"><span data-stu-id="1e058-112">When more than one logical operator is used in a statement, OR operators are evaluated after AND operators.</span></span> <span data-ttu-id="1e058-113">不过，使用括号可以更改求值的顺序。</span><span class="sxs-lookup"><span data-stu-id="1e058-113">However, you can change the order of evaluation by using parentheses.</span></span>  
  
 <span data-ttu-id="1e058-114">双竖线 ( # A2) 与 OR 运算符具有相同的功能。</span><span class="sxs-lookup"><span data-stu-id="1e058-114">Double vertical bars (&#124;&#124;) have the same functionality as the OR operator.</span></span>  
  
 <span data-ttu-id="1e058-115">下表显示可能的输入值和返回类型。</span><span class="sxs-lookup"><span data-stu-id="1e058-115">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="1e058-116">TRUE</span><span class="sxs-lookup"><span data-stu-id="1e058-116">TRUE</span></span>|<span data-ttu-id="1e058-117">TRUE</span><span class="sxs-lookup"><span data-stu-id="1e058-117">TRUE</span></span>|<span data-ttu-id="1e058-118">TRUE</span><span class="sxs-lookup"><span data-stu-id="1e058-118">TRUE</span></span>|  
|`FALSE`|<span data-ttu-id="1e058-119">true</span><span class="sxs-lookup"><span data-stu-id="1e058-119">TRUE</span></span>|<span data-ttu-id="1e058-120">FALSE</span><span class="sxs-lookup"><span data-stu-id="1e058-120">FALSE</span></span>|<span data-ttu-id="1e058-121">Null</span><span class="sxs-lookup"><span data-stu-id="1e058-121">NULL</span></span>|  
|`NULL`|<span data-ttu-id="1e058-122">TRUE</span><span class="sxs-lookup"><span data-stu-id="1e058-122">TRUE</span></span>|<span data-ttu-id="1e058-123">Null</span><span class="sxs-lookup"><span data-stu-id="1e058-123">NULL</span></span>|<span data-ttu-id="1e058-124">Null</span><span class="sxs-lookup"><span data-stu-id="1e058-124">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1e058-125">示例</span><span class="sxs-lookup"><span data-stu-id="1e058-125">Example</span></span>  

 <span data-ttu-id="1e058-126">以下 Entity SQL 查询使用 OR 运算符以组合两个 `Boolean` 表达式。</span><span class="sxs-lookup"><span data-stu-id="1e058-126">The following Entity SQL query uses the OR operator to combine two `Boolean` expressions.</span></span> <span data-ttu-id="1e058-127">此查询基于 AdventureWorks 销售模型。</span><span class="sxs-lookup"><span data-stu-id="1e058-127">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1e058-128">若要编译并运行此查询，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="1e058-128">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="1e058-129">执行 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的过程。</span><span class="sxs-lookup"><span data-stu-id="1e058-129">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="1e058-130">将以下查询作为参数传递给 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="1e058-130">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts 2#OR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#or)]  
  
## <a name="see-also"></a><span data-ttu-id="1e058-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="1e058-131">See also</span></span>

- [<span data-ttu-id="1e058-132">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="1e058-132">Entity SQL Reference</span></span>](entity-sql-reference.md)

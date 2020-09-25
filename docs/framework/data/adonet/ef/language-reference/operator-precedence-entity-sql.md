---
title: 运算符优先级 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
ms.openlocfilehash: f8aa0f213a24d6431d8910af849571a67fbd9f57
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175637"
---
# <a name="operator-precedence-entity-sql"></a><span data-ttu-id="bf40b-102">运算符优先级 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="bf40b-102">Operator Precedence (Entity SQL)</span></span>

<span data-ttu-id="bf40b-103">当 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查询具有多个运算符时，运算符优先级确定执行操作的顺序。</span><span class="sxs-lookup"><span data-stu-id="bf40b-103">When an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query has multiple operators, operator precedence determines the sequence in which the operations are performed.</span></span> <span data-ttu-id="bf40b-104">执行顺序可能对查询结果有明显的影响。</span><span class="sxs-lookup"><span data-stu-id="bf40b-104">The order of execution can significantly affect the query result.</span></span>  
  
 <span data-ttu-id="bf40b-105">运算符的优先级别如下表中所示。</span><span class="sxs-lookup"><span data-stu-id="bf40b-105">Operators have the precedence levels shown in the following table.</span></span> <span data-ttu-id="bf40b-106">在较低级别的运算符之前先对较高级别的运算符进行求值。</span><span class="sxs-lookup"><span data-stu-id="bf40b-106">An operator with a higher level is evaluated before an operator with a lower level.</span></span>  
  
|<span data-ttu-id="bf40b-107">级别</span><span class="sxs-lookup"><span data-stu-id="bf40b-107">Level</span></span>|<span data-ttu-id="bf40b-108">操作类型</span><span class="sxs-lookup"><span data-stu-id="bf40b-108">Operation type</span></span>|<span data-ttu-id="bf40b-109">操作员</span><span class="sxs-lookup"><span data-stu-id="bf40b-109">Operator</span></span>|  
|-----------|--------------------|--------------|  
|<span data-ttu-id="bf40b-110">1</span><span class="sxs-lookup"><span data-stu-id="bf40b-110">1</span></span>|<span data-ttu-id="bf40b-111">主要</span><span class="sxs-lookup"><span data-stu-id="bf40b-111">Primary</span></span>|`. , [] ()`|  
|<span data-ttu-id="bf40b-112">2</span><span class="sxs-lookup"><span data-stu-id="bf40b-112">2</span></span>|<span data-ttu-id="bf40b-113">一元</span><span class="sxs-lookup"><span data-stu-id="bf40b-113">Unary</span></span>|`! not`|  
|<span data-ttu-id="bf40b-114">3</span><span class="sxs-lookup"><span data-stu-id="bf40b-114">3</span></span>|<span data-ttu-id="bf40b-115">乘法</span><span class="sxs-lookup"><span data-stu-id="bf40b-115">Multiplicative</span></span>|`* / %`|  
|<span data-ttu-id="bf40b-116">4</span><span class="sxs-lookup"><span data-stu-id="bf40b-116">4</span></span>|<span data-ttu-id="bf40b-117">加法</span><span class="sxs-lookup"><span data-stu-id="bf40b-117">Additive</span></span>|`+ -`|  
|<span data-ttu-id="bf40b-118">5</span><span class="sxs-lookup"><span data-stu-id="bf40b-118">5</span></span>|<span data-ttu-id="bf40b-119">中间件排序</span><span class="sxs-lookup"><span data-stu-id="bf40b-119">Ordering</span></span>|`< > <= >=`|  
|<span data-ttu-id="bf40b-120">6</span><span class="sxs-lookup"><span data-stu-id="bf40b-120">6</span></span>|<span data-ttu-id="bf40b-121">等式</span><span class="sxs-lookup"><span data-stu-id="bf40b-121">Equality</span></span>|`= != <>`|  
|<span data-ttu-id="bf40b-122">7</span><span class="sxs-lookup"><span data-stu-id="bf40b-122">7</span></span>|<span data-ttu-id="bf40b-123">条件“与”</span><span class="sxs-lookup"><span data-stu-id="bf40b-123">Conditional AND</span></span>|`and &&`|  
|<span data-ttu-id="bf40b-124">8</span><span class="sxs-lookup"><span data-stu-id="bf40b-124">8</span></span>|<span data-ttu-id="bf40b-125">条件“或”</span><span class="sxs-lookup"><span data-stu-id="bf40b-125">Conditional OR</span></span>|`or &#124;&#124;`|  
  
 <span data-ttu-id="bf40b-126">当一个表达式中的两个运算符有相同的运算符优先级别时，将按照它们在查询中的位置对其从左到右进行求值。</span><span class="sxs-lookup"><span data-stu-id="bf40b-126">When two operators in an expression have the same operator precedence level, they are evaluated left to right, based on their position in the query.</span></span> <span data-ttu-id="bf40b-127">例如，`x+y-z` 将计算为 `(x+y)-z`。</span><span class="sxs-lookup"><span data-stu-id="bf40b-127">For example, `x+y-z` is evaluated as `(x+y)-z`.</span></span>  
  
 <span data-ttu-id="bf40b-128">在查询中可以使用括号替代所定义的运算符的优先级。</span><span class="sxs-lookup"><span data-stu-id="bf40b-128">You can use parentheses to override the defined precedence of the operators in a query.</span></span> <span data-ttu-id="bf40b-129">首先对括号中的内容进行求值，从而产生一个结果，然后括号外的运算符才可以使用这个结果。</span><span class="sxs-lookup"><span data-stu-id="bf40b-129">Everything within parentheses is evaluated first to yield a single result before that result can be used by any operator outside the parentheses.</span></span> <span data-ttu-id="bf40b-130">例如，将 `x+y*z` 乘以 `y` ， `z` 然后添加 `x` ，但 `(x+y)*z` 将添加 `x` 到，然后将结果与 `y` 相乘 `z` 。</span><span class="sxs-lookup"><span data-stu-id="bf40b-130">For example, `x+y*z` multiplies `y` by `z` and then adds `x`, but `(x+y)*z` adds `x` to `y` and then multiplies the result by `z`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf40b-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="bf40b-131">See also</span></span>

- [<span data-ttu-id="bf40b-132">Entity SQL 概述</span><span class="sxs-lookup"><span data-stu-id="bf40b-132">Entity SQL Overview</span></span>](entity-sql-overview.md)

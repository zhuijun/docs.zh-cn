---
title: From 子句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
ms.openlocfilehash: 120ba6da11bffc3a0e81873d1fd606633724723d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875258"
---
# <a name="from-clause-visual-basic"></a><span data-ttu-id="fd421-102">From 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fd421-102">From Clause (Visual Basic)</span></span>

<span data-ttu-id="fd421-103">指定一个或多个范围变量以及要查询的集合。</span><span class="sxs-lookup"><span data-stu-id="fd421-103">Specifies one or more range variables and a collection to query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd421-104">语法</span><span class="sxs-lookup"><span data-stu-id="fd421-104">Syntax</span></span>  
  
```vb  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="fd421-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="fd421-105">Parts</span></span>  
  
|<span data-ttu-id="fd421-106">术语</span><span class="sxs-lookup"><span data-stu-id="fd421-106">Term</span></span>|<span data-ttu-id="fd421-107">定义</span><span class="sxs-lookup"><span data-stu-id="fd421-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="fd421-108">必需。</span><span class="sxs-lookup"><span data-stu-id="fd421-108">Required.</span></span> <span data-ttu-id="fd421-109">用于循环访问集合中的元素的 *范围变量* 。</span><span class="sxs-lookup"><span data-stu-id="fd421-109">A *range variable* used to iterate through the elements of the collection.</span></span> <span data-ttu-id="fd421-110">`collection`当查询循环访问时，范围变量用于引用的每个成员 `collection` 。</span><span class="sxs-lookup"><span data-stu-id="fd421-110">A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`.</span></span> <span data-ttu-id="fd421-111">必须为可枚举类型。</span><span class="sxs-lookup"><span data-stu-id="fd421-111">Must be an enumerable type.</span></span>|  
|`type`|<span data-ttu-id="fd421-112">可选。</span><span class="sxs-lookup"><span data-stu-id="fd421-112">Optional.</span></span> <span data-ttu-id="fd421-113">`element` 的类型。</span><span class="sxs-lookup"><span data-stu-id="fd421-113">The type of `element`.</span></span> <span data-ttu-id="fd421-114">如果未 `type` 指定，则 `element` 将从中推断出的类型 `collection` 。</span><span class="sxs-lookup"><span data-stu-id="fd421-114">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="fd421-115">必需。</span><span class="sxs-lookup"><span data-stu-id="fd421-115">Required.</span></span> <span data-ttu-id="fd421-116">引用要查询的集合。</span><span class="sxs-lookup"><span data-stu-id="fd421-116">Refers to the collection to be queried.</span></span> <span data-ttu-id="fd421-117">必须为可枚举类型。</span><span class="sxs-lookup"><span data-stu-id="fd421-117">Must be an enumerable type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd421-118">备注</span><span class="sxs-lookup"><span data-stu-id="fd421-118">Remarks</span></span>  

 <span data-ttu-id="fd421-119">`From`子句用于标识查询的源数据和用于引用源集合中的元素的变量。</span><span class="sxs-lookup"><span data-stu-id="fd421-119">The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection.</span></span> <span data-ttu-id="fd421-120">这些变量称为 *范围变量*。</span><span class="sxs-lookup"><span data-stu-id="fd421-120">These variables are called *range variables*.</span></span> <span data-ttu-id="fd421-121">`From`对于查询，子句是必需的，除非 `Aggregate` 使用子句标识仅返回聚合结果的查询。</span><span class="sxs-lookup"><span data-stu-id="fd421-121">The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results.</span></span> <span data-ttu-id="fd421-122">有关详细信息，请参阅 [Aggregate 子句](aggregate-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="fd421-122">For more information, see [Aggregate Clause](aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="fd421-123">您可以 `From` 在查询中指定多个子句，以标识要联接的多个集合。</span><span class="sxs-lookup"><span data-stu-id="fd421-123">You can specify multiple `From` clauses in a query to identify multiple collections to be joined.</span></span> <span data-ttu-id="fd421-124">指定多个集合时，它们将被单独循环访问，如果相关，可以联接它们。</span><span class="sxs-lookup"><span data-stu-id="fd421-124">When multiple collections are specified, they are iterated over independently, or you can join them if they are related.</span></span> <span data-ttu-id="fd421-125">您可以使用子句隐式联接集合 `Select` ，或使用 or 子句显式联接 `Join` 集合 `Group Join` 。</span><span class="sxs-lookup"><span data-stu-id="fd421-125">You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses.</span></span> <span data-ttu-id="fd421-126">作为替代方法，您可以在单个子句中指定多个范围变量和集合 `From` ，其中每个相关范围变量和集合用逗号分隔开。</span><span class="sxs-lookup"><span data-stu-id="fd421-126">As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma.</span></span> <span data-ttu-id="fd421-127">下面的代码示例演示了子句的两种语法选项 `From` 。</span><span class="sxs-lookup"><span data-stu-id="fd421-127">The following code example shows both syntax options for the `From` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 <span data-ttu-id="fd421-128">`From`子句定义查询的作用域，该作用域类似于循环的作用域 `For` 。</span><span class="sxs-lookup"><span data-stu-id="fd421-128">The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop.</span></span> <span data-ttu-id="fd421-129">因此， `element` 查询作用域中的每个范围变量都必须具有唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="fd421-129">Therefore, each `element` range variable in the scope of a query must have a unique name.</span></span> <span data-ttu-id="fd421-130">由于可以为查询指定多个 `From` 子句，因此后续 `From` 子句可以引用子句中的范围变量 `From` ，或者可以引用上一个子句中的范围变量 `From` 。</span><span class="sxs-lookup"><span data-stu-id="fd421-130">Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause.</span></span> <span data-ttu-id="fd421-131">例如，下面的示例显示一个嵌套 `From` 子句，其中第二个子句中的集合基于第一个子句中范围变量的属性。</span><span class="sxs-lookup"><span data-stu-id="fd421-131">For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 <span data-ttu-id="fd421-132">每个 `From` 子句可以后跟其他查询子句的任意组合，以优化查询。</span><span class="sxs-lookup"><span data-stu-id="fd421-132">Each `From` clause can be followed by any combination of additional query clauses to refine the query.</span></span> <span data-ttu-id="fd421-133">可以通过以下方式优化查询：</span><span class="sxs-lookup"><span data-stu-id="fd421-133">You can refine the query in the following ways:</span></span>  
  
- <span data-ttu-id="fd421-134">使用和子句隐式组合多个集合 `From` `Select` ，或使用 `Join` or 子句显式组合多个集合 `Group Join` 。</span><span class="sxs-lookup"><span data-stu-id="fd421-134">Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.</span></span>  
  
- <span data-ttu-id="fd421-135">使用 `Where` 子句来筛选查询结果。</span><span class="sxs-lookup"><span data-stu-id="fd421-135">Use the `Where` clause to filter the query result.</span></span>  
  
- <span data-ttu-id="fd421-136">使用子句对结果进行排序 `Order By` 。</span><span class="sxs-lookup"><span data-stu-id="fd421-136">Sort the result by using the `Order By` clause.</span></span>  
  
- <span data-ttu-id="fd421-137">使用子句将相似结果组合在一起 `Group By` 。</span><span class="sxs-lookup"><span data-stu-id="fd421-137">Group similar results together by using the `Group By` clause.</span></span>  
  
- <span data-ttu-id="fd421-138">使用 `Aggregate` 子句标识要为整个查询结果计算的聚合函数。</span><span class="sxs-lookup"><span data-stu-id="fd421-138">Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.</span></span>  
  
- <span data-ttu-id="fd421-139">使用 `Let` 子句引入一个迭代变量，该变量的值由表达式而不是集合确定。</span><span class="sxs-lookup"><span data-stu-id="fd421-139">Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.</span></span>  
  
- <span data-ttu-id="fd421-140">使用 `Distinct` 子句可忽略重复的查询结果。</span><span class="sxs-lookup"><span data-stu-id="fd421-140">Use the `Distinct` clause to ignore duplicate query results.</span></span>  
  
- <span data-ttu-id="fd421-141">使用 `Skip` 、 `Take` 、 `Skip While` 和子句标识要返回的结果的各个部分 `Take While` 。</span><span class="sxs-lookup"><span data-stu-id="fd421-141">Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd421-142">示例</span><span class="sxs-lookup"><span data-stu-id="fd421-142">Example</span></span>  

 <span data-ttu-id="fd421-143">下面的查询表达式使用 `From` 子句为 `cust` 集合中的每个对象声明一个范围变量 `Customer` `customers` 。</span><span class="sxs-lookup"><span data-stu-id="fd421-143">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="fd421-144">`Where`子句使用范围变量将输出限制为指定区域的客户。</span><span class="sxs-lookup"><span data-stu-id="fd421-144">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="fd421-145">该 `For Each` 循环将在查询结果中显示每个客户的公司名称。</span><span class="sxs-lookup"><span data-stu-id="fd421-145">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="fd421-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fd421-146">See also</span></span>

- [<span data-ttu-id="fd421-147">查询</span><span class="sxs-lookup"><span data-stu-id="fd421-147">Queries</span></span>](index.md)
- [<span data-ttu-id="fd421-148">Visual Basic 中的 LINQ 简介</span><span class="sxs-lookup"><span data-stu-id="fd421-148">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="fd421-149">For Each...Next 语句</span><span class="sxs-lookup"><span data-stu-id="fd421-149">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
- [<span data-ttu-id="fd421-150">For...Next 语句</span><span class="sxs-lookup"><span data-stu-id="fd421-150">For...Next Statement</span></span>](../statements/for-next-statement.md)
- [<span data-ttu-id="fd421-151">Select 子句</span><span class="sxs-lookup"><span data-stu-id="fd421-151">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="fd421-152">Where 子句</span><span class="sxs-lookup"><span data-stu-id="fd421-152">Where Clause</span></span>](where-clause.md)
- [<span data-ttu-id="fd421-153">Aggregate Clause</span><span class="sxs-lookup"><span data-stu-id="fd421-153">Aggregate Clause</span></span>](aggregate-clause.md)
- [<span data-ttu-id="fd421-154">Distinct 子句</span><span class="sxs-lookup"><span data-stu-id="fd421-154">Distinct Clause</span></span>](distinct-clause.md)
- [<span data-ttu-id="fd421-155">Join 子句</span><span class="sxs-lookup"><span data-stu-id="fd421-155">Join Clause</span></span>](join-clause.md)
- [<span data-ttu-id="fd421-156">Group Join 子句</span><span class="sxs-lookup"><span data-stu-id="fd421-156">Group Join Clause</span></span>](group-join-clause.md)
- [<span data-ttu-id="fd421-157">Order By 子句</span><span class="sxs-lookup"><span data-stu-id="fd421-157">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="fd421-158">Let 子句</span><span class="sxs-lookup"><span data-stu-id="fd421-158">Let Clause</span></span>](let-clause.md)
- [<span data-ttu-id="fd421-159">Skip 子句</span><span class="sxs-lookup"><span data-stu-id="fd421-159">Skip Clause</span></span>](skip-clause.md)
- [<span data-ttu-id="fd421-160">Take 子句</span><span class="sxs-lookup"><span data-stu-id="fd421-160">Take Clause</span></span>](take-clause.md)
- [<span data-ttu-id="fd421-161">Skip While 子句</span><span class="sxs-lookup"><span data-stu-id="fd421-161">Skip While Clause</span></span>](skip-while-clause.md)
- [<span data-ttu-id="fd421-162">Take While 子句</span><span class="sxs-lookup"><span data-stu-id="fd421-162">Take While Clause</span></span>](take-while-clause.md)

---
title: Group Join 子句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryGroupJoinIn
- vb.QueryGroupJoinOn
- vb.QueryGroupJoin
- vb.QueryGroupJoinInto
helpviewer_keywords:
- Group Join clause [Visual Basic]
- Group Join statement [Visual Basic]
- queries [Visual Basic], Group Join
ms.assetid: 37dbf79c-7b5c-421b-bbb7-dadfd2b92a1c
ms.openlocfilehash: 7916e51293c06016b2581b7109df3f0a599404ca
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359824"
---
# <a name="group-join-clause-visual-basic"></a><span data-ttu-id="4dfb0-102">Group Join 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4dfb0-102">Group Join Clause (Visual Basic)</span></span>
<span data-ttu-id="4dfb0-103">将两个集合合并为单个分层集合。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-103">Combines two collections into a single hierarchical collection.</span></span> <span data-ttu-id="4dfb0-104">联接运算基于匹配键。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-104">The join operation is based on matching keys.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dfb0-105">语法</span><span class="sxs-lookup"><span data-stu-id="4dfb0-105">Syntax</span></span>  
  
```vb  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## <a name="parts"></a><span data-ttu-id="4dfb0-106">组成部分</span><span class="sxs-lookup"><span data-stu-id="4dfb0-106">Parts</span></span>  
  
|<span data-ttu-id="4dfb0-107">术语</span><span class="sxs-lookup"><span data-stu-id="4dfb0-107">Term</span></span>|<span data-ttu-id="4dfb0-108">定义</span><span class="sxs-lookup"><span data-stu-id="4dfb0-108">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="4dfb0-109">必需。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-109">Required.</span></span> <span data-ttu-id="4dfb0-110">要联接的集合的控件变量。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-110">The control variable for the collection being joined.</span></span>|  
|`type`|<span data-ttu-id="4dfb0-111">可选。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-111">Optional.</span></span> <span data-ttu-id="4dfb0-112">`element` 的类型。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-112">The type of `element`.</span></span> <span data-ttu-id="4dfb0-113">如果未 `type` 指定，则 `element` 将从中推断出的类型 `collection` 。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-113">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="4dfb0-114">必需。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-114">Required.</span></span> <span data-ttu-id="4dfb0-115">要与运算符左侧的集合组合的集合 `Group Join` 。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-115">The collection to combine with the collection that is on the left side of the `Group Join` operator.</span></span> <span data-ttu-id="4dfb0-116">`Group Join`子句可以嵌套在子句中，也可以嵌套在 `Join` 另一 `Group Join` 子句中。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-116">A `Group Join` clause can be nested in a `Join` clause or in another `Group Join` clause.</span></span>|  
|<span data-ttu-id="4dfb0-117">`key1` `Equals` `key2`</span><span class="sxs-lookup"><span data-stu-id="4dfb0-117">`key1` `Equals` `key2`</span></span>|<span data-ttu-id="4dfb0-118">必需。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-118">Required.</span></span> <span data-ttu-id="4dfb0-119">标识要联接的集合的键。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-119">Identifies keys for the collections being joined.</span></span> <span data-ttu-id="4dfb0-120">必须使用 `Equals` 运算符来比较要联接的集合中的键。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-120">You must use the `Equals` operator to compare keys from the collections being joined.</span></span> <span data-ttu-id="4dfb0-121">可以通过使用 `And` 运算符来标识多个键，从而组合联接条件。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-121">You can combine join conditions by using the `And` operator to identify multiple keys.</span></span> <span data-ttu-id="4dfb0-122">`key1`参数必须位于运算符左侧的集合中 `Join` 。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-122">The `key1` parameter must be from the collection on the left side of the `Join` operator.</span></span> <span data-ttu-id="4dfb0-123">`key2`参数必须来自运算符右侧的集合 `Join` 。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-123">The `key2` parameter must be from the collection on the right side of the `Join` operator.</span></span><br /><br /> <span data-ttu-id="4dfb0-124">联接条件中使用的键可以是包含集合中多个项的表达式。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-124">The keys used in the join condition can be expressions that include more than one item from the collection.</span></span> <span data-ttu-id="4dfb0-125">但是，每个键表达式只能包含其各自集合中的项。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-125">However, each key expression can contain only items from its respective collection.</span></span>|  
|`expressionList`|<span data-ttu-id="4dfb0-126">必需。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-126">Required.</span></span> <span data-ttu-id="4dfb0-127">一个或多个表达式，用于标识集合中的元素组的聚合方式。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-127">One or more expressions that identify how the groups of elements from the collection are aggregated.</span></span> <span data-ttu-id="4dfb0-128">若要标识分组结果的成员名称，请使用 `Group` 关键字（ `<alias> = Group` ）。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-128">To identify a member name for the grouped results, use the `Group` keyword (`<alias> = Group`).</span></span> <span data-ttu-id="4dfb0-129">还可以包含聚合函数以将其应用于该组。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-129">You can also include aggregate functions to apply to the group.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4dfb0-130">备注</span><span class="sxs-lookup"><span data-stu-id="4dfb0-130">Remarks</span></span>  
 <span data-ttu-id="4dfb0-131">`Group Join`子句组合了两个集合，这些集合基于要联接的集合中的匹配键值。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-131">The `Group Join` clause combines two collections based on matching key values from the collections being joined.</span></span> <span data-ttu-id="4dfb0-132">生成的集合可以包含一个成员，该成员引用第二个集合中与第一个集合中的键值相匹配的元素的集合。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-132">The resulting collection can contain a member that references a collection of elements from the second collection that match the key value from the first collection.</span></span> <span data-ttu-id="4dfb0-133">还可以指定要应用于第二个集合中的分组元素的聚合函数。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-133">You can also specify aggregate functions to apply to the grouped elements from the second collection.</span></span> <span data-ttu-id="4dfb0-134">有关聚合函数的信息，请参阅[Aggregate 子句](aggregate-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-134">For information about aggregate functions, see [Aggregate Clause](aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="4dfb0-135">例如，考虑一个经理集合和一组雇员。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-135">Consider, for example, a collection of managers and a collection of employees.</span></span> <span data-ttu-id="4dfb0-136">这两个集合中的元素都具有 ManagerID 属性，该属性标识向特定经理报告的员工。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-136">Elements from both collections have a ManagerID property that identifies the employees that report to a particular manager.</span></span> <span data-ttu-id="4dfb0-137">联接操作的结果将包含具有匹配的 ManagerID 值的每个经理和员工的结果。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-137">The results from a join operation would contain a result for each manager and employee with a matching ManagerID value.</span></span> <span data-ttu-id="4dfb0-138">操作的结果 `Group Join` 将包含管理器的完整列表。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-138">The results from a `Group Join` operation would contain the complete list of managers.</span></span> <span data-ttu-id="4dfb0-139">每个管理器结果都有一个成员，该成员引用了与特定经理匹配的员工列表。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-139">Each manager result would have a member that referenced the list of employees that were a match for the specific manager.</span></span>  
  
 <span data-ttu-id="4dfb0-140">由操作生成的集合 `Group Join` 可以包含子句中标识的集合中的任何值组合 `From` 和子句的子句中标识的表达式 `Into` `Group Join` 。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-140">The collection resulting from a `Group Join` operation can contain any combination of values from the collection identified in the `From` clause and the expressions identified in the `Into` clause of the `Group Join` clause.</span></span> <span data-ttu-id="4dfb0-141">有关子句的有效表达式的详细信息 `Into` ，请参阅[Aggregate 子句](aggregate-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-141">For more information about valid expressions for the `Into` clause, see [Aggregate Clause](aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="4dfb0-142">`Group Join`操作将返回位于运算符左侧标识的集合中的所有结果 `Group Join` 。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-142">A `Group Join` operation will return all results from the collection identified on the left side of the `Group Join` operator.</span></span> <span data-ttu-id="4dfb0-143">即使要联接的集合中没有匹配项，也是如此。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-143">This is true even if there are no matches in the collection being joined.</span></span> <span data-ttu-id="4dfb0-144">这类似于 `LEFT OUTER JOIN` SQL 中的。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-144">This is like a `LEFT OUTER JOIN` in SQL.</span></span>  
  
 <span data-ttu-id="4dfb0-145">可以使用子句将 `Join` 集合合并为单个集合。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-145">You can use the `Join` clause to combine collections into a single collection.</span></span> <span data-ttu-id="4dfb0-146">这等效于 `INNER JOIN` SQL 中的。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-146">This is equivalent to an `INNER JOIN` in SQL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4dfb0-147">示例</span><span class="sxs-lookup"><span data-stu-id="4dfb0-147">Example</span></span>  
 <span data-ttu-id="4dfb0-148">下面的代码示例使用子句联接两个集合 `Group Join` 。</span><span class="sxs-lookup"><span data-stu-id="4dfb0-148">The following code example joins two collections by using the `Group Join` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="4dfb0-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4dfb0-149">See also</span></span>

- [<span data-ttu-id="4dfb0-150">Visual Basic 中的 LINQ 简介</span><span class="sxs-lookup"><span data-stu-id="4dfb0-150">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="4dfb0-151">查询</span><span class="sxs-lookup"><span data-stu-id="4dfb0-151">Queries</span></span>](index.md)
- [<span data-ttu-id="4dfb0-152">Select 子句</span><span class="sxs-lookup"><span data-stu-id="4dfb0-152">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="4dfb0-153">From 子句</span><span class="sxs-lookup"><span data-stu-id="4dfb0-153">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="4dfb0-154">Join 子句</span><span class="sxs-lookup"><span data-stu-id="4dfb0-154">Join Clause</span></span>](join-clause.md)
- [<span data-ttu-id="4dfb0-155">Where 子句</span><span class="sxs-lookup"><span data-stu-id="4dfb0-155">Where Clause</span></span>](where-clause.md)
- [<span data-ttu-id="4dfb0-156">Group By 子句</span><span class="sxs-lookup"><span data-stu-id="4dfb0-156">Group By Clause</span></span>](group-by-clause.md)

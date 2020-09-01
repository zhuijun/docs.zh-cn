---
description: join 子句 - C# 参考
title: join 子句 - C# 参考
ms.date: 07/20/2015
f1_keywords:
- join
- join_CSharpKeyword
helpviewer_keywords:
- join clause [C#]
- join keyword [C#]
ms.assetid: 76e9df84-092c-41a6-9537-c3f1cbd7f0fb
ms.openlocfilehash: 44b35bd1243e4715f81513eef9968f30a8f315a3
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139744"
---
# <a name="join-clause-c-reference"></a><span data-ttu-id="f0920-103">join 子句（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="f0920-103">join clause (C# Reference)</span></span>

<span data-ttu-id="f0920-104">`join` 子句可用于将来自不同源序列并且在对象模型中没有直接关系的元素相关联。</span><span class="sxs-lookup"><span data-stu-id="f0920-104">The `join` clause is useful for associating elements from different source sequences that have no direct relationship in the object model.</span></span> <span data-ttu-id="f0920-105">唯一的要求是每个源中的元素需要共享某个可以进行比较以判断是否相等的值。</span><span class="sxs-lookup"><span data-stu-id="f0920-105">The only requirement is that the elements in each source share some value that can be compared for equality.</span></span> <span data-ttu-id="f0920-106">例如，食品经销商可能拥有某种产品的供应商列表以及买主列表。</span><span class="sxs-lookup"><span data-stu-id="f0920-106">For example, a food distributor might have a list of suppliers of a certain product, and a list of buyers.</span></span> <span data-ttu-id="f0920-107">例如，可以使用 `join` 子句创建该产品同一指定地区供应商和买主的列表。</span><span class="sxs-lookup"><span data-stu-id="f0920-107">A `join` clause can be used, for example, to create a list of the suppliers and buyers of that product who are all in the same specified region.</span></span>

<span data-ttu-id="f0920-108">`join` 子句将 2 个源序列作为输入。</span><span class="sxs-lookup"><span data-stu-id="f0920-108">A `join` clause takes two source sequences as input.</span></span> <span data-ttu-id="f0920-109">每个序列中的元素都必须是可以与其他序列中的相应属性进行比较的属性，或者包含一个这样的属性。</span><span class="sxs-lookup"><span data-stu-id="f0920-109">The elements in each sequence must either be or contain a property that can be compared to a corresponding property in the other sequence.</span></span> <span data-ttu-id="f0920-110">`join` 子句使用特殊 `equals` 关键字比较指定的键是否相等。</span><span class="sxs-lookup"><span data-stu-id="f0920-110">The `join` clause compares the specified keys for equality by using the special `equals` keyword.</span></span> <span data-ttu-id="f0920-111">`join` 子句执行的所有联接都是同等联接。</span><span class="sxs-lookup"><span data-stu-id="f0920-111">All joins performed by the `join` clause are equijoins.</span></span> <span data-ttu-id="f0920-112">`join` 子句的输出形式取决于执行的联接的具体类型。</span><span class="sxs-lookup"><span data-stu-id="f0920-112">The shape of the output of a `join` clause depends on the specific type of join you are performing.</span></span> <span data-ttu-id="f0920-113">以下是 3 种最常见的联接类型：</span><span class="sxs-lookup"><span data-stu-id="f0920-113">The following are three most common join types:</span></span>

- <span data-ttu-id="f0920-114">内部联接</span><span class="sxs-lookup"><span data-stu-id="f0920-114">Inner join</span></span>

- <span data-ttu-id="f0920-115">分组联接</span><span class="sxs-lookup"><span data-stu-id="f0920-115">Group join</span></span>

- <span data-ttu-id="f0920-116">左外部联接</span><span class="sxs-lookup"><span data-stu-id="f0920-116">Left outer join</span></span>

## <a name="inner-join"></a><span data-ttu-id="f0920-117">内部联接</span><span class="sxs-lookup"><span data-stu-id="f0920-117">Inner join</span></span>

<span data-ttu-id="f0920-118">以下示例演示了一个简单的内部同等联接。</span><span class="sxs-lookup"><span data-stu-id="f0920-118">The following example shows a simple inner equijoin.</span></span> <span data-ttu-id="f0920-119">此查询生成一个“产品名称/类别”对平面序列。</span><span class="sxs-lookup"><span data-stu-id="f0920-119">This query produces a flat sequence of "product name / category" pairs.</span></span> <span data-ttu-id="f0920-120">同一类别字符串将出现在多个元素中。</span><span class="sxs-lookup"><span data-stu-id="f0920-120">The same category string will appear in multiple elements.</span></span> <span data-ttu-id="f0920-121">如果 `categories` 中的某个元素不具有匹配的 `products`，则该类别不会出现在结果中。</span><span class="sxs-lookup"><span data-stu-id="f0920-121">If an element from `categories` has no matching `products`, that category will not appear in the results.</span></span>

[!code-csharp[cscsrefQueryKeywords#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#24)]

<span data-ttu-id="f0920-122">有关详细信息，请参阅[执行内联](../../linq/perform-inner-joins.md)。</span><span class="sxs-lookup"><span data-stu-id="f0920-122">For more information, see [Perform inner joins](../../linq/perform-inner-joins.md).</span></span>

## <a name="group-join"></a><span data-ttu-id="f0920-123">分组联接</span><span class="sxs-lookup"><span data-stu-id="f0920-123">Group join</span></span>

<span data-ttu-id="f0920-124">含有 `into` 表达式的 `join` 子句称为分组联接。</span><span class="sxs-lookup"><span data-stu-id="f0920-124">A `join` clause with an `into` expression is called a group join.</span></span>

[!code-csharp[cscsrefQueryKeywords#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#25)]

<span data-ttu-id="f0920-125">分组联接会生成分层的结果序列，该序列将左侧源序列中的元素与右侧源序列中的一个或多个匹配元素相关联。</span><span class="sxs-lookup"><span data-stu-id="f0920-125">A group join produces a hierarchical result sequence, which associates elements in the left source sequence with one or more matching elements in the right side source sequence.</span></span> <span data-ttu-id="f0920-126">分组联接没有等效的关系术语；它本质上是一个对象数组序列。</span><span class="sxs-lookup"><span data-stu-id="f0920-126">A group join has no equivalent in relational terms; it is essentially a sequence of object arrays.</span></span>

<span data-ttu-id="f0920-127">如果在右侧源序列中找不到与左侧源中的元素相匹配的元素，则 `join` 子句会为该项生成一个空数组。</span><span class="sxs-lookup"><span data-stu-id="f0920-127">If no elements from the right source sequence are found to match an element in the left source, the `join` clause will produce an empty array for that item.</span></span> <span data-ttu-id="f0920-128">因此，分组联接基本上仍然是一种内部同等联接，区别在于分组联接将结果序列组织为多个组。</span><span class="sxs-lookup"><span data-stu-id="f0920-128">Therefore, the group join is still basically an inner-equijoin except that the result sequence is organized into groups.</span></span>

<span data-ttu-id="f0920-129">如果只选择分组联接的结果，则可访问各项，但无法识别结果所匹配的项。</span><span class="sxs-lookup"><span data-stu-id="f0920-129">If you just select the results of a group join, you can access the items, but you cannot identify the key that they match on.</span></span> <span data-ttu-id="f0920-130">因此，通常更为有用的做法是：选择分组联接的结果并将其放入一个也包含该项名的新类型中，如上例所示。</span><span class="sxs-lookup"><span data-stu-id="f0920-130">Therefore, it is generally more useful to select the results of the group join into a new type that also has the key name, as shown in the previous example.</span></span>

<span data-ttu-id="f0920-131">当然，还可以将分组联接的结果用作其他子查询的生成器：</span><span class="sxs-lookup"><span data-stu-id="f0920-131">You can also, of course, use the result of a group join as the generator of another subquery:</span></span>

[!code-csharp[cscsrefQueryKeywords#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#26)]

<span data-ttu-id="f0920-132">有关详细信息，请参阅[执行分组联接](../../linq/perform-grouped-joins.md)。</span><span class="sxs-lookup"><span data-stu-id="f0920-132">For more information, see [Perform grouped joins](../../linq/perform-grouped-joins.md).</span></span>

## <a name="left-outer-join"></a><span data-ttu-id="f0920-133">左外部联接</span><span class="sxs-lookup"><span data-stu-id="f0920-133">Left outer join</span></span>

<span data-ttu-id="f0920-134">在左外部联接中，将返回左侧源序列中的所有元素，即使右侧序列中没有其匹配元素也是如此。</span><span class="sxs-lookup"><span data-stu-id="f0920-134">In a left outer join, all the elements in the left source sequence are returned, even if no matching elements are in the right sequence.</span></span> <span data-ttu-id="f0920-135">若要在 LINQ 中执行左外部联接，请结合使用 `DefaultIfEmpty` 方法与分组联接，指定要在某个左侧元素不具有匹配元素时生成的默认右侧元素。</span><span class="sxs-lookup"><span data-stu-id="f0920-135">To perform a left outer join in LINQ, use the `DefaultIfEmpty` method in combination with a group join to specify a default right-side element to produce if a left-side element has no matches.</span></span> <span data-ttu-id="f0920-136">可以使用 `null` 作为任何引用类型的默认值，也可以指定用户定义的默认类型。</span><span class="sxs-lookup"><span data-stu-id="f0920-136">You can use `null` as the default value for any reference type, or you can specify a user-defined default type.</span></span> <span data-ttu-id="f0920-137">以下示例演示了用户定义的默认类型：</span><span class="sxs-lookup"><span data-stu-id="f0920-137">In the following example, a user-defined default type is shown:</span></span>

[!code-csharp[cscsrefQueryKeywords#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#27)]

<span data-ttu-id="f0920-138">有关详细信息，请参阅[执行左外部联接](../../linq/perform-left-outer-joins.md)。</span><span class="sxs-lookup"><span data-stu-id="f0920-138">For more information, see [Perform left outer joins](../../linq/perform-left-outer-joins.md).</span></span>

## <a name="the-equals-operator"></a><span data-ttu-id="f0920-139">等于运算符</span><span class="sxs-lookup"><span data-stu-id="f0920-139">The equals operator</span></span>

<span data-ttu-id="f0920-140">`join` 子句执行同等联接。</span><span class="sxs-lookup"><span data-stu-id="f0920-140">A `join` clause performs an equijoin.</span></span> <span data-ttu-id="f0920-141">换言之，只能基于 2 个项之间的相等关系进行匹配。</span><span class="sxs-lookup"><span data-stu-id="f0920-141">In other words, you can only base matches on the equality of two keys.</span></span> <span data-ttu-id="f0920-142">不支持其他类型的比较，例如“大于”或“不等于”。</span><span class="sxs-lookup"><span data-stu-id="f0920-142">Other types of comparisons such as "greater than" or "not equals" are not supported.</span></span> <span data-ttu-id="f0920-143">为了表明所有联接都是同等联接，`join` 子句使用 `equals` 关键字而不是 `==` 运算符。</span><span class="sxs-lookup"><span data-stu-id="f0920-143">To make clear that all joins are equijoins, the `join` clause uses the `equals` keyword instead of the `==` operator.</span></span> <span data-ttu-id="f0920-144">`equals` 关键字只能在 `join` 子句中使用，并且其与 `==` 运算符之间存在一个重要差别。</span><span class="sxs-lookup"><span data-stu-id="f0920-144">The `equals` keyword can only be used in a `join` clause and it differs from the `==` operator in one important way.</span></span> <span data-ttu-id="f0920-145">对于 `equals`，左键使用外部源序列，而右键使用内部源序列。</span><span class="sxs-lookup"><span data-stu-id="f0920-145">With `equals`, the left key consumes the outer source sequence, and the right key consumes the inner source.</span></span> <span data-ttu-id="f0920-146">外部源仅在 `equals` 的左侧位于范围内，而内部源序列仅在其右侧位于范围内。</span><span class="sxs-lookup"><span data-stu-id="f0920-146">The outer source is only in scope on the left side of `equals` and the inner source sequence is only in scope on the right side.</span></span>

## <a name="non-equijoins"></a><span data-ttu-id="f0920-147">非同等联接</span><span class="sxs-lookup"><span data-stu-id="f0920-147">Non-equijoins</span></span>

<span data-ttu-id="f0920-148">通过使用多个 `from` 子句将新序列单独引入查询，可以执行非同等联接、交叉联接和其他自定义联接操作。</span><span class="sxs-lookup"><span data-stu-id="f0920-148">You can perform non-equijoins, cross joins, and other custom join operations by using multiple `from` clauses to introduce new sequences independently into a query.</span></span> <span data-ttu-id="f0920-149">有关详细信息，请参阅[执行自定义联接操作](../../linq/perform-custom-join-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="f0920-149">For more information, see [Perform custom join operations](../../linq/perform-custom-join-operations.md).</span></span>

## <a name="joins-on-object-collections-vs-relational-tables"></a><span data-ttu-id="f0920-150">对象集合联接与关系表</span><span class="sxs-lookup"><span data-stu-id="f0920-150">Joins on object collections vs. relational tables</span></span>

<span data-ttu-id="f0920-151">在 LINQ 查询表达式中，联接操作是在对象集合上执行的。</span><span class="sxs-lookup"><span data-stu-id="f0920-151">In a LINQ query expression, join operations are performed on object collections.</span></span> <span data-ttu-id="f0920-152">不能使用与 2 个关系表完全相同的方式“联接”对象集合。</span><span class="sxs-lookup"><span data-stu-id="f0920-152">Object collections cannot be "joined" in exactly the same way as two relational tables.</span></span> <span data-ttu-id="f0920-153">在 LINQ 中，仅当 2 个源序列没有通过任何关系相互联系时，才需要使用显式 `join` 子句。</span><span class="sxs-lookup"><span data-stu-id="f0920-153">In LINQ, explicit `join` clauses are only required when two source sequences are not tied by any relationship.</span></span> <span data-ttu-id="f0920-154">使用 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 时，外键表在对象模型中表示为主表的属性。</span><span class="sxs-lookup"><span data-stu-id="f0920-154">When working with [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], foreign key tables are represented in the object model as properties of the primary table.</span></span> <span data-ttu-id="f0920-155">例如，在 Northwind 数据库中，Customer 表与 Orders 表之间具有外键关系。</span><span class="sxs-lookup"><span data-stu-id="f0920-155">For example, in the Northwind database, the Customer table has a foreign key relationship with the Orders table.</span></span> <span data-ttu-id="f0920-156">将这两个表映射到对象模型时，Customer 类具有一个 Orders 属性，其中包含与该 Customer 相关联的 Orders 集合。</span><span class="sxs-lookup"><span data-stu-id="f0920-156">When you map the tables to the object model, the Customer class has an Orders property that contains the collection of Orders associated with that Customer.</span></span> <span data-ttu-id="f0920-157">实际上，已经为你执行了联接。</span><span class="sxs-lookup"><span data-stu-id="f0920-157">In effect, the join has already been done for you.</span></span>

<span data-ttu-id="f0920-158">若要深入了解如何在 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 的上下文中跨相关表执行查询，请参阅[如何：映射数据库关系](../../../framework/data/adonet/sql/linq/how-to-map-database-relationships.md)。</span><span class="sxs-lookup"><span data-stu-id="f0920-158">For more information about querying across related tables in the context of [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], see [How to: Map Database Relationships](../../../framework/data/adonet/sql/linq/how-to-map-database-relationships.md).</span></span>

## <a name="composite-keys"></a><span data-ttu-id="f0920-159">组合键</span><span class="sxs-lookup"><span data-stu-id="f0920-159">Composite keys</span></span>

<span data-ttu-id="f0920-160">可通过使用组合键测试多个值是否相等。</span><span class="sxs-lookup"><span data-stu-id="f0920-160">You can test for equality of multiple values by using a composite key.</span></span> <span data-ttu-id="f0920-161">有关详细信息，请参阅[使用组合键进行联接](../../linq/join-by-using-composite-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="f0920-161">For more information, see [Join by using composite keys](../../linq/join-by-using-composite-keys.md).</span></span> <span data-ttu-id="f0920-162">还可以在 `group` 子句中使用组合键。</span><span class="sxs-lookup"><span data-stu-id="f0920-162">Composite keys can be also used in a `group` clause.</span></span>

## <a name="example"></a><span data-ttu-id="f0920-163">示例</span><span class="sxs-lookup"><span data-stu-id="f0920-163">Example</span></span>

<span data-ttu-id="f0920-164">以下示例比较了使用相同的匹配键对相同数据源执行内部联接、分组联接和左外部联接的结果。</span><span class="sxs-lookup"><span data-stu-id="f0920-164">The following example compares the results of an inner join, a group join, and a left outer join on the same data sources by using the same matching keys.</span></span> <span data-ttu-id="f0920-165">这些示例中添加了一些额外的代码，以便在控制台显示中阐明结果。</span><span class="sxs-lookup"><span data-stu-id="f0920-165">Some extra code is added to these examples to clarify the results in the console display.</span></span>

[!code-csharp[cscsrefQueryKeywords#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#23)]

## <a name="remarks"></a><span data-ttu-id="f0920-166">备注</span><span class="sxs-lookup"><span data-stu-id="f0920-166">Remarks</span></span>

<span data-ttu-id="f0920-167">后面未跟 `into` 的 `join` 子句转换为 <xref:System.Linq.Enumerable.Join%2A> 方法调用。</span><span class="sxs-lookup"><span data-stu-id="f0920-167">A `join` clause that is not followed by `into` is translated into a <xref:System.Linq.Enumerable.Join%2A> method call.</span></span> <span data-ttu-id="f0920-168">后面跟 `into` 的 `join` 子句转换为 <xref:System.Linq.Enumerable.GroupJoin%2A> 方法调用。</span><span class="sxs-lookup"><span data-stu-id="f0920-168">A `join` clause that is followed by `into` is translated to a <xref:System.Linq.Enumerable.GroupJoin%2A> method call.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0920-169">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f0920-169">See also</span></span>

- [<span data-ttu-id="f0920-170">查询关键字 (LINQ)</span><span class="sxs-lookup"><span data-stu-id="f0920-170">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="f0920-171">语言集成查询 (LINQ)</span><span class="sxs-lookup"><span data-stu-id="f0920-171">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)
- [<span data-ttu-id="f0920-172">联接运算</span><span class="sxs-lookup"><span data-stu-id="f0920-172">Join Operations</span></span>](../../programming-guide/concepts/linq/join-operations.md)
- [<span data-ttu-id="f0920-173">group 子句</span><span class="sxs-lookup"><span data-stu-id="f0920-173">group clause</span></span>](group-clause.md)
- [<span data-ttu-id="f0920-174">执行左外部联接</span><span class="sxs-lookup"><span data-stu-id="f0920-174">Perform left outer joins</span></span>](../../linq/perform-left-outer-joins.md)
- [<span data-ttu-id="f0920-175">执行内部联接</span><span class="sxs-lookup"><span data-stu-id="f0920-175">Perform inner joins</span></span>](../../linq/perform-inner-joins.md)
- [<span data-ttu-id="f0920-176">执行分组联接</span><span class="sxs-lookup"><span data-stu-id="f0920-176">Perform grouped joins</span></span>](../../linq/perform-grouped-joins.md)
- [<span data-ttu-id="f0920-177">对 Join 子句的结果进行排序</span><span class="sxs-lookup"><span data-stu-id="f0920-177">Order the results of a join clause</span></span>](../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="f0920-178">使用组合键进行联接</span><span class="sxs-lookup"><span data-stu-id="f0920-178">Join by using composite keys</span></span>](../../linq/join-by-using-composite-keys.md)
- [<span data-ttu-id="f0920-179">适用于 Visual Studio 的兼容数据库系统</span><span class="sxs-lookup"><span data-stu-id="f0920-179">Compatible database systems for Visual Studio</span></span>](/visualstudio/data-tools/installing-database-systems-tools-and-samples)

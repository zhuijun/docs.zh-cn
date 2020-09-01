---
description: group 子句 - C# 参考
title: group 子句 - C# 参考
ms.date: 07/20/2015
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
ms.openlocfilehash: 5e642492b4b36bb0464baf16baa80c58c19ba9f1
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138223"
---
# <a name="group-clause-c-reference"></a><span data-ttu-id="9c12e-103">group 子句（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="9c12e-103">group clause (C# Reference)</span></span>

<span data-ttu-id="9c12e-104">`group` 子句返回一个 <xref:System.Linq.IGrouping%602> 对象序列，这些对象包含零个或更多与该组的键值匹配的项。</span><span class="sxs-lookup"><span data-stu-id="9c12e-104">The `group` clause returns a sequence of <xref:System.Linq.IGrouping%602> objects that contain zero or more items that match the key value for the group.</span></span> <span data-ttu-id="9c12e-105">例如，可以按照每个字符串中的第一个字母对字符串序列进行分组。</span><span class="sxs-lookup"><span data-stu-id="9c12e-105">For example, you can group a sequence of strings according to the first letter in each string.</span></span> <span data-ttu-id="9c12e-106">在这种情况下，第一个字母就是键，类型为 [char](../builtin-types/char.md)，并且存储在每个 <xref:System.Linq.IGrouping%602> 对象的 `Key` 属性中。</span><span class="sxs-lookup"><span data-stu-id="9c12e-106">In this case, the first letter is the key and has a type [char](../builtin-types/char.md), and is stored in the `Key` property of each <xref:System.Linq.IGrouping%602> object.</span></span> <span data-ttu-id="9c12e-107">编译器可推断键的类型。</span><span class="sxs-lookup"><span data-stu-id="9c12e-107">The compiler infers the type of the key.</span></span>

<span data-ttu-id="9c12e-108">可以用 `group` 子句结束查询表达式，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="9c12e-108">You can end a query expression with a `group` clause, as shown in the following example:</span></span>

[!code-csharp[cscsrefQueryKeywords#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#10)]

<span data-ttu-id="9c12e-109">如果要对每个组执行附加查询操作，可使用上下文关键字 [into](into.md) 指定一个临时标识符。</span><span class="sxs-lookup"><span data-stu-id="9c12e-109">If you want to perform additional query operations on each group, you can specify a temporary identifier by using the [into](into.md) contextual keyword.</span></span> <span data-ttu-id="9c12e-110">使用 `into` 时，必须继续编写该查询，并最终使用一个`select` 语句或另一个 `group` 子句结束该查询，如以下代码摘录所示：</span><span class="sxs-lookup"><span data-stu-id="9c12e-110">When you use `into`, you must continue with the query, and eventually end it with either a `select` statement or another `group` clause, as shown in the following excerpt:</span></span>

[!code-csharp[cscsrefQueryKeywords#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#11)]

<span data-ttu-id="9c12e-111">对于含有和不含 `into` 的 `group`，本文中的“示例”部分提供有关其用法的更完整示例。</span><span class="sxs-lookup"><span data-stu-id="9c12e-111">More complete examples of the use of `group` with and without `into` are provided in the Example section of this article.</span></span>

## <a name="enumerating-the-results-of-a-group-query"></a><span data-ttu-id="9c12e-112">枚举查询分组的结果</span><span class="sxs-lookup"><span data-stu-id="9c12e-112">Enumerating the results of a group query</span></span>

<span data-ttu-id="9c12e-113">由于 `group` 查询产生的 <xref:System.Linq.IGrouping%602> 对象实质上是一个由列表组成的列表，因此必须使用嵌套的 [foreach](foreach-in.md) 循环来访问每一组中的各个项。</span><span class="sxs-lookup"><span data-stu-id="9c12e-113">Because the <xref:System.Linq.IGrouping%602> objects produced by a `group` query are essentially a list of lists, you must use a nested [foreach](foreach-in.md) loop to access the items in each group.</span></span> <span data-ttu-id="9c12e-114">外部循环用于循环访问组键，内部循环用于循环访问组本身包含的每个项。</span><span class="sxs-lookup"><span data-stu-id="9c12e-114">The outer loop iterates over the group keys, and the inner loop iterates over each item in the group itself.</span></span> <span data-ttu-id="9c12e-115">组可能具有键，但没有元素。</span><span class="sxs-lookup"><span data-stu-id="9c12e-115">A group may have a key but no elements.</span></span> <span data-ttu-id="9c12e-116">下面的 `foreach` 循环执行上述代码示例中的查询：</span><span class="sxs-lookup"><span data-stu-id="9c12e-116">The following is the `foreach` loop that executes the query in the previous code examples:</span></span>

[!code-csharp[cscsrefQueryKeywords#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#12)]

## <a name="key-types"></a><span data-ttu-id="9c12e-117">键类型</span><span class="sxs-lookup"><span data-stu-id="9c12e-117">Key types</span></span>

<span data-ttu-id="9c12e-118">组键可以是任何类型，如字符串、内置数值类型、用户定义的命名类型或匿名类型。</span><span class="sxs-lookup"><span data-stu-id="9c12e-118">Group keys can be any type, such as a string, a built-in numeric type, or a user-defined named type or anonymous type.</span></span>

### <a name="grouping-by-string"></a><span data-ttu-id="9c12e-119">按字符串分组</span><span class="sxs-lookup"><span data-stu-id="9c12e-119">Grouping by string</span></span>

<span data-ttu-id="9c12e-120">上述代码示例使用 `char`。</span><span class="sxs-lookup"><span data-stu-id="9c12e-120">The previous code examples used a `char`.</span></span> <span data-ttu-id="9c12e-121">可轻松改为指定字符串键，如完整的姓氏：</span><span class="sxs-lookup"><span data-stu-id="9c12e-121">A string key could easily have been specified instead, for example the complete last name:</span></span>

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

### <a name="grouping-by-bool"></a><span data-ttu-id="9c12e-122">按布尔值分组</span><span class="sxs-lookup"><span data-stu-id="9c12e-122">Grouping by bool</span></span>

<span data-ttu-id="9c12e-123">下面的示例演示使用布尔值作为键将结果划分成两个组。</span><span class="sxs-lookup"><span data-stu-id="9c12e-123">The following example shows the use of a bool value for a key to divide the results into two groups.</span></span> <span data-ttu-id="9c12e-124">请注意，该值由 `group` 子句中的子表达式生成。</span><span class="sxs-lookup"><span data-stu-id="9c12e-124">Note that the value is produced by a sub-expression in the `group` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#14)]

### <a name="grouping-by-numeric-range"></a><span data-ttu-id="9c12e-125">按数值范围分组</span><span class="sxs-lookup"><span data-stu-id="9c12e-125">Grouping by numeric range</span></span>

<span data-ttu-id="9c12e-126">下一示例使用表达式创建表示百分比范围的数值组键。</span><span class="sxs-lookup"><span data-stu-id="9c12e-126">The next example uses an expression to create numeric group keys that represent a percentile range.</span></span> <span data-ttu-id="9c12e-127">请注意，该示例使用 [let](let-clause.md) 作为方法调用结果的方便存储位置，因此无需在 `group` 子句中调用该方法两次。</span><span class="sxs-lookup"><span data-stu-id="9c12e-127">Note the use of [let](let-clause.md) as a convenient location to store a method call result, so that you don't have to call the method two times in the `group` clause.</span></span> <span data-ttu-id="9c12e-128">若要详细了解如何在查询表达式中安全使用方法，请参阅[在查询表达式中处理异常](../../linq/handle-exceptions-in-query-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="9c12e-128">For more information about how to safely use methods in query expressions, see [Handle exceptions in query expressions](../../linq/handle-exceptions-in-query-expressions.md).</span></span>

[!code-csharp[cscsrefQueryKeywords#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#15)]

### <a name="grouping-by-composite-keys"></a><span data-ttu-id="9c12e-129">按复合键分组</span><span class="sxs-lookup"><span data-stu-id="9c12e-129">Grouping by composite keys</span></span>

<span data-ttu-id="9c12e-130">希望按照多个键对元素进行分组时，可使用复合键。</span><span class="sxs-lookup"><span data-stu-id="9c12e-130">Use a composite key when you want to group elements according to more than one key.</span></span> <span data-ttu-id="9c12e-131">使用匿名类型或命名类型来存储键元素，创建复合键。</span><span class="sxs-lookup"><span data-stu-id="9c12e-131">You create a composite key by using an anonymous type or a named type to hold the key element.</span></span> <span data-ttu-id="9c12e-132">在下面的示例中，假定已经使用名为 `surname` 和 `city` 的两个成员声明了类 `Person`。</span><span class="sxs-lookup"><span data-stu-id="9c12e-132">In the following example, assume that a class `Person` has been declared with members named `surname` and `city`.</span></span> <span data-ttu-id="9c12e-133">`group` 子句会为每组姓氏和城市相同的人员创建一个单独的组。</span><span class="sxs-lookup"><span data-stu-id="9c12e-133">The `group` clause causes a separate group to be created for each set of persons with the same last name and the same city.</span></span>

```csharp
group person by new {name = person.surname, city = person.city};
```

<span data-ttu-id="9c12e-134">如果必须将查询变量传递给其他方法，请使用命名类型。</span><span class="sxs-lookup"><span data-stu-id="9c12e-134">Use a named type if you must pass the query variable to another method.</span></span> <span data-ttu-id="9c12e-135">使用键的自动实现的属性创建一个特殊类，然后替代 <xref:System.Object.Equals%2A> 和 <xref:System.Object.GetHashCode%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="9c12e-135">Create a special class using auto-implemented properties for the keys, and then override the <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods.</span></span> <span data-ttu-id="9c12e-136">还可以使用结构，在此情况下，并不严格要求替代这些方法。</span><span class="sxs-lookup"><span data-stu-id="9c12e-136">You can also use a struct, in which case you do not strictly have to override those methods.</span></span> <span data-ttu-id="9c12e-137">有关详细信息，请参阅[如何使用自动实现的属性实现轻量类](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md)和[如何在目录树中查询重复文件](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="9c12e-137">For more information see [How to implement a lightweight class with auto-implemented properties](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) and [How to query for duplicate files in a directory tree](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md).</span></span> <span data-ttu-id="9c12e-138">后文包含的代码示例演示了如何将复合键与命名类型结合使用。</span><span class="sxs-lookup"><span data-stu-id="9c12e-138">The latter article has a code example that demonstrates how to use a composite key with a named type.</span></span>

## <a name="example"></a><span data-ttu-id="9c12e-139">示例</span><span class="sxs-lookup"><span data-stu-id="9c12e-139">Example</span></span>

<span data-ttu-id="9c12e-140">下面的示例演示在没有向组应用附加查询逻辑时，将源数据按顺序放入组中的标准模式。</span><span class="sxs-lookup"><span data-stu-id="9c12e-140">The following example shows the standard pattern for ordering source data into groups when no additional query logic is applied to the groups.</span></span> <span data-ttu-id="9c12e-141">这称为不带延续的分组。</span><span class="sxs-lookup"><span data-stu-id="9c12e-141">This is called a grouping without a continuation.</span></span> <span data-ttu-id="9c12e-142">字符串数组中的元素按照它们的首字母进行分组。</span><span class="sxs-lookup"><span data-stu-id="9c12e-142">The elements in an array of strings are grouped according to their first letter.</span></span> <span data-ttu-id="9c12e-143">查询的结果是 <xref:System.Linq.IGrouping%602> 类型（包含一个 `char` 类型的公共 `Key` 属性）和一个 <xref:System.Collections.Generic.IEnumerable%601> 集合（在分组中包含每个项）。</span><span class="sxs-lookup"><span data-stu-id="9c12e-143">The result of the query is an <xref:System.Linq.IGrouping%602> type that contains a public `Key` property of type `char` and an <xref:System.Collections.Generic.IEnumerable%601> collection that contains each item in the grouping.</span></span>

<span data-ttu-id="9c12e-144">`group` 子句的结果是由序列组成的序列。</span><span class="sxs-lookup"><span data-stu-id="9c12e-144">The result of a `group` clause is a sequence of sequences.</span></span> <span data-ttu-id="9c12e-145">因此，若要访问返回的每个组中的单个元素，请在循环访问组键的循环内使用嵌套的 `foreach` 循环，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="9c12e-145">Therefore, to access the individual elements within each returned group, use a nested `foreach` loop inside the loop that iterates the group keys, as shown in the following example.</span></span>

[!code-csharp[cscsrefQueryKeywords#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#16)]

## <a name="example"></a><span data-ttu-id="9c12e-146">示例</span><span class="sxs-lookup"><span data-stu-id="9c12e-146">Example</span></span>

<span data-ttu-id="9c12e-147">此示例演示在创建组之后，如何使用通过 `into` 实现的延续\*\* 对这些组执行附加逻辑。</span><span class="sxs-lookup"><span data-stu-id="9c12e-147">This example shows how to perform additional logic on the groups after you have created them, by using a *continuation* with `into`.</span></span> <span data-ttu-id="9c12e-148">有关详细信息，请参阅 [into](into.md)。</span><span class="sxs-lookup"><span data-stu-id="9c12e-148">For more information, see [into](into.md).</span></span> <span data-ttu-id="9c12e-149">下面的示例查询每个组，仅选择键值为元音的元素。</span><span class="sxs-lookup"><span data-stu-id="9c12e-149">The following example queries each group to select only those whose key value is a vowel.</span></span>

[!code-csharp[cscsrefQueryKeywords#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#17)]

## <a name="remarks"></a><span data-ttu-id="9c12e-150">备注</span><span class="sxs-lookup"><span data-stu-id="9c12e-150">Remarks</span></span>

<span data-ttu-id="9c12e-151">在编译时，`group` 子句转换为对 <xref:System.Linq.Enumerable.GroupBy%2A> 方法的调用。</span><span class="sxs-lookup"><span data-stu-id="9c12e-151">At compile time, `group` clauses are translated into calls to the <xref:System.Linq.Enumerable.GroupBy%2A> method.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c12e-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9c12e-152">See also</span></span>

- <xref:System.Linq.IGrouping%602>
- <xref:System.Linq.Enumerable.GroupBy%2A>
- <xref:System.Linq.Enumerable.ThenBy%2A>
- <xref:System.Linq.Enumerable.ThenByDescending%2A>
- [<span data-ttu-id="9c12e-153">查询关键字</span><span class="sxs-lookup"><span data-stu-id="9c12e-153">Query Keywords</span></span>](query-keywords.md)
- [<span data-ttu-id="9c12e-154">语言集成查询 (LINQ)</span><span class="sxs-lookup"><span data-stu-id="9c12e-154">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)
- [<span data-ttu-id="9c12e-155">创建嵌套组</span><span class="sxs-lookup"><span data-stu-id="9c12e-155">Create a nested group</span></span>](../../linq/create-a-nested-group.md)
- [<span data-ttu-id="9c12e-156">对查询结果进行分组</span><span class="sxs-lookup"><span data-stu-id="9c12e-156">Group query results</span></span>](../../linq/group-query-results.md)
- [<span data-ttu-id="9c12e-157">对分组操作执行子查询</span><span class="sxs-lookup"><span data-stu-id="9c12e-157">Perform a subquery on a grouping operation</span></span>](../../linq/perform-a-subquery-on-a-grouping-operation.md)

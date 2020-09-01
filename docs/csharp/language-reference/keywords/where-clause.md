---
description: where 子句 - C# 参考
title: where 子句 - C# 参考
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: 58a8dc226bb2720b6a8251f028712a80f74e893c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141681"
---
# <a name="where-clause-c-reference"></a><span data-ttu-id="111ad-103">where 子句（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="111ad-103">where clause (C# Reference)</span></span>

<span data-ttu-id="111ad-104">`where` 子句用在查询表达式中，用于指定将在查询表达式中返回数据源中的哪些元素。</span><span class="sxs-lookup"><span data-stu-id="111ad-104">The `where` clause is used in a query expression to specify which elements from the data source will be returned in the query expression.</span></span> <span data-ttu-id="111ad-105">它将一个布尔条件（谓词\*\*）应用于每个源元素（由范围变量引用），并返回满足指定条件的元素。</span><span class="sxs-lookup"><span data-stu-id="111ad-105">It applies a Boolean condition (*predicate*) to each source element (referenced by the range variable) and returns those for which the specified condition is true.</span></span> <span data-ttu-id="111ad-106">一个查询表达式可以包含多个 `where` 子句，一个子句可以包含多个谓词子表达式。</span><span class="sxs-lookup"><span data-stu-id="111ad-106">A single query expression may contain multiple `where` clauses and a single clause may contain multiple predicate subexpressions.</span></span>

## <a name="example"></a><span data-ttu-id="111ad-107">示例</span><span class="sxs-lookup"><span data-stu-id="111ad-107">Example</span></span>

<span data-ttu-id="111ad-108">在下面的示例中，`where` 子句筛选出除小于五的数字外的所有数字。</span><span class="sxs-lookup"><span data-stu-id="111ad-108">In the following example, the `where` clause filters out all numbers except those that are less than five.</span></span> <span data-ttu-id="111ad-109">如果删除 `where` 子句，则会返回数据源中的所有数字。</span><span class="sxs-lookup"><span data-stu-id="111ad-109">If you remove the `where` clause, all numbers from the data source would be returned.</span></span> <span data-ttu-id="111ad-110">表达式 `num < 5` 是应用于每个元素的谓词。</span><span class="sxs-lookup"><span data-stu-id="111ad-110">The expression `num < 5` is the predicate that is applied to each element.</span></span>

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a><span data-ttu-id="111ad-111">示例</span><span class="sxs-lookup"><span data-stu-id="111ad-111">Example</span></span>

<span data-ttu-id="111ad-112">在单个 `where` 子句中，可以使用 [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) 和 [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) 运算符根据需要指定任意多个谓词。</span><span class="sxs-lookup"><span data-stu-id="111ad-112">Within a single `where` clause, you can specify as many predicates as necessary by using the [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) and [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="111ad-113">在下面的示例中，查询将指定两个谓词，以便只选择小于五的偶数。</span><span class="sxs-lookup"><span data-stu-id="111ad-113">In the following example, the query specifies two predicates in order to select only the even numbers that are less than five.</span></span>

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a><span data-ttu-id="111ad-114">示例</span><span class="sxs-lookup"><span data-stu-id="111ad-114">Example</span></span>

<span data-ttu-id="111ad-115">一个 `where` 子句可以包含一个或多个返回布尔值的方法。</span><span class="sxs-lookup"><span data-stu-id="111ad-115">A `where` clause may contain one or more methods that return Boolean values.</span></span> <span data-ttu-id="111ad-116">在下面的示例中，`where` 子句使用一种方法来确定范围变量的当前值是偶数还是奇数。</span><span class="sxs-lookup"><span data-stu-id="111ad-116">In the following example, the `where` clause uses a method to determine whether the current value of the range variable is even or odd.</span></span>

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a><span data-ttu-id="111ad-117">备注</span><span class="sxs-lookup"><span data-stu-id="111ad-117">Remarks</span></span>

<span data-ttu-id="111ad-118">`where` 子句是一种筛选机制。</span><span class="sxs-lookup"><span data-stu-id="111ad-118">The `where` clause is a filtering mechanism.</span></span> <span data-ttu-id="111ad-119">除了不能是第一个或最后一个子句外，它几乎可以放在查询表达式中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="111ad-119">It can be positioned almost anywhere in a query expression, except it cannot be the first or last clause.</span></span> <span data-ttu-id="111ad-120">`where` 子句可以出现在 [group](group-clause.md) 子句的前面或后面，具体取决于时必须在对源元素进行分组之前还是之后来筛选源元素。</span><span class="sxs-lookup"><span data-stu-id="111ad-120">A `where` clause may appear either before or after a [group](group-clause.md) clause depending on whether you have to filter the source elements before or after they are grouped.</span></span>

<span data-ttu-id="111ad-121">如果指定的谓词对于数据源中的元素无效，则会发生编译时错误。</span><span class="sxs-lookup"><span data-stu-id="111ad-121">If a specified predicate is not valid for the elements in the data source, a compile-time error will result.</span></span> <span data-ttu-id="111ad-122">这是 LINQ 提供的强类型检查的一个优点。</span><span class="sxs-lookup"><span data-stu-id="111ad-122">This is one benefit of the strong type-checking provided by LINQ.</span></span>

<span data-ttu-id="111ad-123">在编译时，`where` 关键字将转换为对 <xref:System.Linq.Enumerable.Where%2A> 标准查询运算符方法的调用。</span><span class="sxs-lookup"><span data-stu-id="111ad-123">At compile time the `where` keyword is converted into a call to the <xref:System.Linq.Enumerable.Where%2A> Standard Query Operator method.</span></span>

## <a name="see-also"></a><span data-ttu-id="111ad-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="111ad-124">See also</span></span>

- [<span data-ttu-id="111ad-125">查询关键字 (LINQ)</span><span class="sxs-lookup"><span data-stu-id="111ad-125">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="111ad-126">from 子句</span><span class="sxs-lookup"><span data-stu-id="111ad-126">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="111ad-127">select 子句</span><span class="sxs-lookup"><span data-stu-id="111ad-127">select clause</span></span>](select-clause.md)
- [<span data-ttu-id="111ad-128">筛选数据</span><span class="sxs-lookup"><span data-stu-id="111ad-128">Filtering Data</span></span>](../../programming-guide/concepts/linq/filtering-data.md)
- [<span data-ttu-id="111ad-129">C# 中的 LINQ</span><span class="sxs-lookup"><span data-stu-id="111ad-129">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="111ad-130">语言集成查询 (LINQ)</span><span class="sxs-lookup"><span data-stu-id="111ad-130">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)

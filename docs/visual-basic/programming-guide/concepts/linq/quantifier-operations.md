---
title: 限定符运算
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: 9a2e35e0511915cb17b99550a8bf382bd9d46526
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396306"
---
# <a name="quantifier-operations-visual-basic"></a><span data-ttu-id="ebd88-102">限定符运算（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="ebd88-102">Quantifier Operations (Visual Basic)</span></span>
<span data-ttu-id="ebd88-103">限定符运算返回一个 <xref:System.Boolean> 值，该值指示序列中是否有一些元素满足条件或是否所有元素都满足条件。</span><span class="sxs-lookup"><span data-stu-id="ebd88-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="ebd88-104">下图描述了两个不同源序列上的两个不同限定符运算。</span><span class="sxs-lookup"><span data-stu-id="ebd88-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="ebd88-105">第一个运算询问是否有一个或多个元素为字符“A”，结果为 `true`。</span><span class="sxs-lookup"><span data-stu-id="ebd88-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="ebd88-106">第二个运算询问是否所有元素都为字符“A”，结果为 `true`。</span><span class="sxs-lookup"><span data-stu-id="ebd88-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![LINQ 限定符操作](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="ebd88-108">下节列出了执行限定符运算的标准查询运算符方法。</span><span class="sxs-lookup"><span data-stu-id="ebd88-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ebd88-109">方法</span><span class="sxs-lookup"><span data-stu-id="ebd88-109">Methods</span></span>  
  
|<span data-ttu-id="ebd88-110">方法名</span><span class="sxs-lookup"><span data-stu-id="ebd88-110">Method Name</span></span>|<span data-ttu-id="ebd88-111">说明</span><span class="sxs-lookup"><span data-stu-id="ebd88-111">Description</span></span>|<span data-ttu-id="ebd88-112">Visual Basic 查询表达式语法</span><span class="sxs-lookup"><span data-stu-id="ebd88-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="ebd88-113">详细信息</span><span class="sxs-lookup"><span data-stu-id="ebd88-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="ebd88-114">All</span><span class="sxs-lookup"><span data-stu-id="ebd88-114">All</span></span>|<span data-ttu-id="ebd88-115">确定是否序列中的所有元素都满足条件。</span><span class="sxs-lookup"><span data-stu-id="ebd88-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ebd88-116">任意</span><span class="sxs-lookup"><span data-stu-id="ebd88-116">Any</span></span>|<span data-ttu-id="ebd88-117">确定序列中是否有元素满足条件。</span><span class="sxs-lookup"><span data-stu-id="ebd88-117">Determines whether any elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ebd88-118">包含</span><span class="sxs-lookup"><span data-stu-id="ebd88-118">Contains</span></span>|<span data-ttu-id="ebd88-119">确定序列是否包含指定的元素。</span><span class="sxs-lookup"><span data-stu-id="ebd88-119">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="ebd88-120">不适用。</span><span class="sxs-lookup"><span data-stu-id="ebd88-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="ebd88-121">查询表达式语法示例</span><span class="sxs-lookup"><span data-stu-id="ebd88-121">Query Expression Syntax Examples</span></span>  
 <span data-ttu-id="ebd88-122">这些示例使用 `Aggregate` Visual Basic 中的子句作为 LINQ 查询中筛选条件的一部分。</span><span class="sxs-lookup"><span data-stu-id="ebd88-122">These examples use the `Aggregate` clause in Visual Basic as part of the filtering condition in a LINQ query.</span></span>  
  
 <span data-ttu-id="ebd88-123">下面的示例使用 `Aggregate` 子句和 <xref:System.Linq.Enumerable.All%2A> 扩展方法从集合中返回所有宠物都早于指定年龄的人。</span><span class="sxs-lookup"><span data-stu-id="ebd88-123">The following example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.All%2A> extension method to return from a collection those people whose pets are all older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#1)]  
  
 <span data-ttu-id="ebd88-124">下一个示例使用 `Aggregate` 子句和 <xref:System.Linq.Enumerable.Any%2A> 扩展方法从集合中返回至少具有一个早于指定年龄的宠物的用户。</span><span class="sxs-lookup"><span data-stu-id="ebd88-124">The next example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.Any%2A> extension method to return from a collection those people who have at least one pet that is older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ebd88-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ebd88-125">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="ebd88-126">标准查询运算符概述 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ebd88-126">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="ebd88-127">Aggregate Clause</span><span class="sxs-lookup"><span data-stu-id="ebd88-127">Aggregate Clause</span></span>](../../../language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="ebd88-128">如何：查询包含一组指定词语的句子 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ebd88-128">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

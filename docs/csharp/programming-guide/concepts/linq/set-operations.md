---
title: 集运算 (C#)
description: 了解设置操作以及使用 C# 中的 LINQ 执行设置操作的标准查询运算符方法。
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: 8679f804adaaeada390206e3e1dd2a0711a2cbf6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195605"
---
# <a name="set-operations-c"></a><span data-ttu-id="ba434-103">集运算 (C#)</span><span class="sxs-lookup"><span data-stu-id="ba434-103">Set Operations (C#)</span></span>

<span data-ttu-id="ba434-104">LINQ 中的集运算是指根据相同或不同集合（或集）中是否存在等效元素来生成结果集的查询运算。</span><span class="sxs-lookup"><span data-stu-id="ba434-104">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="ba434-105">下节列出了执行集运算的标准查询运算符方法。</span><span class="sxs-lookup"><span data-stu-id="ba434-105">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ba434-106">方法</span><span class="sxs-lookup"><span data-stu-id="ba434-106">Methods</span></span>  
  
|<span data-ttu-id="ba434-107">方法名</span><span class="sxs-lookup"><span data-stu-id="ba434-107">Method Name</span></span>|<span data-ttu-id="ba434-108">描述</span><span class="sxs-lookup"><span data-stu-id="ba434-108">Description</span></span>|<span data-ttu-id="ba434-109">C# 查询表达式语法</span><span class="sxs-lookup"><span data-stu-id="ba434-109">C# Query Expression Syntax</span></span>|<span data-ttu-id="ba434-110">更多信息</span><span class="sxs-lookup"><span data-stu-id="ba434-110">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="ba434-111">Distinct</span><span class="sxs-lookup"><span data-stu-id="ba434-111">Distinct</span></span>|<span data-ttu-id="ba434-112">删除集合中的重复值。</span><span class="sxs-lookup"><span data-stu-id="ba434-112">Removes duplicate values from a collection.</span></span>|<span data-ttu-id="ba434-113">不适用。</span><span class="sxs-lookup"><span data-stu-id="ba434-113">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ba434-114">Except</span><span class="sxs-lookup"><span data-stu-id="ba434-114">Except</span></span>|<span data-ttu-id="ba434-115">返回差集，差集指位于一个集合但不位于另一个集合的元素。</span><span class="sxs-lookup"><span data-stu-id="ba434-115">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="ba434-116">不适用。</span><span class="sxs-lookup"><span data-stu-id="ba434-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ba434-117">相交</span><span class="sxs-lookup"><span data-stu-id="ba434-117">Intersect</span></span>|<span data-ttu-id="ba434-118">返回交集，交集指同时出现在两个集合中的元素。</span><span class="sxs-lookup"><span data-stu-id="ba434-118">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="ba434-119">不适用。</span><span class="sxs-lookup"><span data-stu-id="ba434-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ba434-120">联合</span><span class="sxs-lookup"><span data-stu-id="ba434-120">Union</span></span>|<span data-ttu-id="ba434-121">返回并集，并集指位于两个集合中任一集合的唯一的元素。</span><span class="sxs-lookup"><span data-stu-id="ba434-121">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="ba434-122">不适用。</span><span class="sxs-lookup"><span data-stu-id="ba434-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="ba434-123">比较集运算</span><span class="sxs-lookup"><span data-stu-id="ba434-123">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="ba434-124">Distinct</span><span class="sxs-lookup"><span data-stu-id="ba434-124">Distinct</span></span>  

 <span data-ttu-id="ba434-125">以下示例演示字符序列上 <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> 方法的行为。</span><span class="sxs-lookup"><span data-stu-id="ba434-125">The following example depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="ba434-126">返回的序列包含输入序列的唯一元素。</span><span class="sxs-lookup"><span data-stu-id="ba434-126">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 ![显示 Distinct() 的行为的图。](./media/set-operations/distinct-method-behavior.png)  

 [!code-csharp-interactive[Distinct](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#1)]
  
### <a name="except"></a><span data-ttu-id="ba434-128">Except</span><span class="sxs-lookup"><span data-stu-id="ba434-128">Except</span></span>  

 <span data-ttu-id="ba434-129">以下示例演示 <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType> 的行为。</span><span class="sxs-lookup"><span data-stu-id="ba434-129">The following example depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ba434-130">返回的序列只包含位于第一个输入序列但不位于第二个输入序列的元素。</span><span class="sxs-lookup"><span data-stu-id="ba434-130">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="ba434-131">![显示 Except() 的操作的图](./media/set-operations/except-behavior-graphic.png "显示 Except 的行为。")</span><span class="sxs-lookup"><span data-stu-id="ba434-131">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>  
  
[!code-csharp-interactive[Except](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#2)]

### <a name="intersect"></a><span data-ttu-id="ba434-132">相交</span><span class="sxs-lookup"><span data-stu-id="ba434-132">Intersect</span></span>  

 <span data-ttu-id="ba434-133">以下示例演示 <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType> 的行为。</span><span class="sxs-lookup"><span data-stu-id="ba434-133">The following example depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ba434-134">返回的序列包含两个输入序列共有的元素。</span><span class="sxs-lookup"><span data-stu-id="ba434-134">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 ![显示两个序列的交集的图。](./media/set-operations/intersection-two-sequences.png)  

[!code-csharp-interactive[Intersect](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#3)]

### <a name="union"></a><span data-ttu-id="ba434-136">联合</span><span class="sxs-lookup"><span data-stu-id="ba434-136">Union</span></span>  

 <span data-ttu-id="ba434-137">以下示例演示对两个字符序列执行的联合操作。</span><span class="sxs-lookup"><span data-stu-id="ba434-137">The following example depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="ba434-138">返回的序列包含两个输入序列的唯一元素。</span><span class="sxs-lookup"><span data-stu-id="ba434-138">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 ![显示两个序列的并集的图。](./media/set-operations/union-operation-two-sequences.png)  

[!code-csharp-interactive[Union](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#4)]

## <a name="see-also"></a><span data-ttu-id="ba434-140">请参阅</span><span class="sxs-lookup"><span data-stu-id="ba434-140">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="ba434-141">标准查询运算符概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="ba434-141">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="ba434-142">如何合并和比较字符串集合 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ba434-142">How to combine and compare string collections (LINQ) (C#)</span></span>](./how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="ba434-143">如何查找两个列表之间的差集 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ba434-143">How to find the set difference between two lists (LINQ) (C#)</span></span>](./how-to-find-the-set-difference-between-two-lists-linq.md)

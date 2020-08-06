---
title: 限定符运算 (C#)
description: 了解限定符运算。 这些限定符运算返回一个布尔值，该值指示序列中是否有一些元素满足条件或是否所有元素都满足条件。
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: ce06f887d3ad7b10cbdedf9e33072df2c0819ef1
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299144"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="b2503-104">限定符运算 (C#)</span><span class="sxs-lookup"><span data-stu-id="b2503-104">Quantifier Operations (C#)</span></span>
<span data-ttu-id="b2503-105">限定符运算返回一个 <xref:System.Boolean> 值，该值指示序列中是否有一些元素满足条件或是否所有元素都满足条件。</span><span class="sxs-lookup"><span data-stu-id="b2503-105">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="b2503-106">下图描述了两个不同源序列上的两个不同限定符运算。</span><span class="sxs-lookup"><span data-stu-id="b2503-106">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="b2503-107">第一个运算询问是否有一个或多个元素为字符“A”，结果为 `true`。</span><span class="sxs-lookup"><span data-stu-id="b2503-107">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="b2503-108">第二个运算询问是否所有元素都为字符“A”，结果为 `true`。</span><span class="sxs-lookup"><span data-stu-id="b2503-108">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![LINQ 限定符运算](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="b2503-110">下节列出了执行限定符运算的标准查询运算符方法。</span><span class="sxs-lookup"><span data-stu-id="b2503-110">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b2503-111">方法</span><span class="sxs-lookup"><span data-stu-id="b2503-111">Methods</span></span>  
  
|<span data-ttu-id="b2503-112">方法名</span><span class="sxs-lookup"><span data-stu-id="b2503-112">Method Name</span></span>|<span data-ttu-id="b2503-113">描述</span><span class="sxs-lookup"><span data-stu-id="b2503-113">Description</span></span>|<span data-ttu-id="b2503-114">C# 查询表达式语法</span><span class="sxs-lookup"><span data-stu-id="b2503-114">C# Query Expression Syntax</span></span>|<span data-ttu-id="b2503-115">更多信息</span><span class="sxs-lookup"><span data-stu-id="b2503-115">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="b2503-116">全部</span><span class="sxs-lookup"><span data-stu-id="b2503-116">All</span></span>|<span data-ttu-id="b2503-117">确定是否序列中的所有元素都满足条件。</span><span class="sxs-lookup"><span data-stu-id="b2503-117">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="b2503-118">不适用。</span><span class="sxs-lookup"><span data-stu-id="b2503-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b2503-119">任意</span><span class="sxs-lookup"><span data-stu-id="b2503-119">Any</span></span>|<span data-ttu-id="b2503-120">确定序列中是否有元素满足条件。</span><span class="sxs-lookup"><span data-stu-id="b2503-120">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="b2503-121">不适用。</span><span class="sxs-lookup"><span data-stu-id="b2503-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b2503-122">包含</span><span class="sxs-lookup"><span data-stu-id="b2503-122">Contains</span></span>|<span data-ttu-id="b2503-123">确定序列是否包含指定的元素。</span><span class="sxs-lookup"><span data-stu-id="b2503-123">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="b2503-124">不适用。</span><span class="sxs-lookup"><span data-stu-id="b2503-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="b2503-125">查询表达式语法示例</span><span class="sxs-lookup"><span data-stu-id="b2503-125">Query Expression Syntax Examples</span></span>  
  
### <a name="all"></a><span data-ttu-id="b2503-126">全部</span><span class="sxs-lookup"><span data-stu-id="b2503-126">All</span></span>  
<span data-ttu-id="b2503-127">以下示例使用 `All` 检查所有字符串是否为特定长度。</span><span class="sxs-lookup"><span data-stu-id="b2503-127">The following example uses the `All` to check that all strings are of a specific length.</span></span>
  
[!code-csharp[All](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#All)]  
  
### <a name="any"></a><span data-ttu-id="b2503-128">任意</span><span class="sxs-lookup"><span data-stu-id="b2503-128">Any</span></span>  
<span data-ttu-id="b2503-129">以下示例使用 `Any` 检查所有字符串是否以“o”开头。</span><span class="sxs-lookup"><span data-stu-id="b2503-129">The following example uses the `Any` to check that any strings are start with 'o'.</span></span>  
  
[!code-csharp[Any](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Any)]  
  
### <a name="contains"></a><span data-ttu-id="b2503-130">包含</span><span class="sxs-lookup"><span data-stu-id="b2503-130">Contains</span></span>  
<span data-ttu-id="b2503-131">以下示例使用 `Contains` 检查所有数组是否具有特定元素。</span><span class="sxs-lookup"><span data-stu-id="b2503-131">The following example uses the `Contains` to check an array have a specific element.</span></span>  
  
[!code-csharp[Contains](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Contains)]  
  
## <a name="see-also"></a><span data-ttu-id="b2503-132">请参阅</span><span class="sxs-lookup"><span data-stu-id="b2503-132">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="b2503-133">标准查询运算符概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="b2503-133">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="b2503-134">在运行时动态指定谓词筛选器</span><span class="sxs-lookup"><span data-stu-id="b2503-134">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="b2503-135">如何查询包含一组指定词语的句子 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="b2503-135">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

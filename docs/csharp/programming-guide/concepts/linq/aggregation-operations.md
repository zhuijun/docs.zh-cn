---
title: 聚合运算 (C#)
description: 了解执行聚合操作的方法。 聚合运算从值的集合中计算出单个值。
ms.date: 07/20/2015
ms.assetid: 6fc035e5-7639-48b8-bc7f-b093dd31b039
ms.openlocfilehash: 3d5a52249520478571db2fcfd7aa5d10fb013565
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104303"
---
# <a name="aggregation-operations-c"></a><span data-ttu-id="56770-104">聚合运算 (C#)</span><span class="sxs-lookup"><span data-stu-id="56770-104">Aggregation Operations (C#)</span></span>
<span data-ttu-id="56770-105">聚合运算从值的集合中计算出单个值。</span><span class="sxs-lookup"><span data-stu-id="56770-105">An aggregation operation computes a single value from a collection of values.</span></span> <span data-ttu-id="56770-106">例如，从一个月累计的每日温度值计算出日平均温度值就是一个聚合运算。</span><span class="sxs-lookup"><span data-stu-id="56770-106">An example of an aggregation operation is calculating the average daily temperature from a month's worth of daily temperature values.</span></span>  
  
 <span data-ttu-id="56770-107">下图显示对数字序列进行两种不同聚合操作所得结果。</span><span class="sxs-lookup"><span data-stu-id="56770-107">The following illustration shows the results of two different aggregation operations on a sequence of numbers.</span></span> <span data-ttu-id="56770-108">第一个操作累加数字。</span><span class="sxs-lookup"><span data-stu-id="56770-108">The first operation sums the numbers.</span></span> <span data-ttu-id="56770-109">第二个操作返回序列中的最大值。</span><span class="sxs-lookup"><span data-stu-id="56770-109">The second operation returns the maximum value in the sequence.</span></span>  
  
 ![显示 LINQ 聚合运算的插图。](./media/aggregation-operations/linq-aggregation-operations.png)  
  
 <span data-ttu-id="56770-111">下节列出了执行聚合运算的标准查询运算符方法。</span><span class="sxs-lookup"><span data-stu-id="56770-111">The standard query operator methods that perform aggregation operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="56770-112">方法</span><span class="sxs-lookup"><span data-stu-id="56770-112">Methods</span></span>  
  
|<span data-ttu-id="56770-113">方法名</span><span class="sxs-lookup"><span data-stu-id="56770-113">Method Name</span></span>|<span data-ttu-id="56770-114">描述</span><span class="sxs-lookup"><span data-stu-id="56770-114">Description</span></span>|<span data-ttu-id="56770-115">C# 查询表达式语法</span><span class="sxs-lookup"><span data-stu-id="56770-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="56770-116">详细信息</span><span class="sxs-lookup"><span data-stu-id="56770-116">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="56770-117">聚合</span><span class="sxs-lookup"><span data-stu-id="56770-117">Aggregate</span></span>|<span data-ttu-id="56770-118">对集合的值执行自定义聚合运算。</span><span class="sxs-lookup"><span data-stu-id="56770-118">Performs a custom aggregation operation on the values of a collection.</span></span>|<span data-ttu-id="56770-119">不适用。</span><span class="sxs-lookup"><span data-stu-id="56770-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="56770-120">平均值</span><span class="sxs-lookup"><span data-stu-id="56770-120">Average</span></span>|<span data-ttu-id="56770-121">计算值集合的平均值。</span><span class="sxs-lookup"><span data-stu-id="56770-121">Calculates the average value of a collection of values.</span></span>|<span data-ttu-id="56770-122">不适用。</span><span class="sxs-lookup"><span data-stu-id="56770-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="56770-123">计数</span><span class="sxs-lookup"><span data-stu-id="56770-123">Count</span></span>|<span data-ttu-id="56770-124">对集合中元素计数，可选择仅对满足谓词函数的元素计数。</span><span class="sxs-lookup"><span data-stu-id="56770-124">Counts the elements in a collection, optionally only those elements that satisfy a predicate function.</span></span>|<span data-ttu-id="56770-125">不适用。</span><span class="sxs-lookup"><span data-stu-id="56770-125">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="56770-126">LongCount</span><span class="sxs-lookup"><span data-stu-id="56770-126">LongCount</span></span>|<span data-ttu-id="56770-127">对大型集合中元素计数，可选择仅对满足谓词函数的元素计数。</span><span class="sxs-lookup"><span data-stu-id="56770-127">Counts the elements in a large collection, optionally only those elements that satisfy a predicate function.</span></span>|<span data-ttu-id="56770-128">不适用。</span><span class="sxs-lookup"><span data-stu-id="56770-128">Not applicable.</span></span>|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="56770-129">最大值</span><span class="sxs-lookup"><span data-stu-id="56770-129">Max</span></span>|<span data-ttu-id="56770-130">确定集合中的最大值。</span><span class="sxs-lookup"><span data-stu-id="56770-130">Determines the maximum value in a collection.</span></span>|<span data-ttu-id="56770-131">不适用。</span><span class="sxs-lookup"><span data-stu-id="56770-131">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="56770-132">最小值</span><span class="sxs-lookup"><span data-stu-id="56770-132">Min</span></span>|<span data-ttu-id="56770-133">确定集合中的最小值。</span><span class="sxs-lookup"><span data-stu-id="56770-133">Determines the minimum value in a collection.</span></span>|<span data-ttu-id="56770-134">不适用。</span><span class="sxs-lookup"><span data-stu-id="56770-134">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="56770-135">Sum</span><span class="sxs-lookup"><span data-stu-id="56770-135">Sum</span></span>|<span data-ttu-id="56770-136">对集合中的值求和。</span><span class="sxs-lookup"><span data-stu-id="56770-136">Calculates the sum of the values in a collection.</span></span>|<span data-ttu-id="56770-137">不适用。</span><span class="sxs-lookup"><span data-stu-id="56770-137">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="56770-138">请参阅</span><span class="sxs-lookup"><span data-stu-id="56770-138">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="56770-139">标准查询运算符概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="56770-139">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="56770-140">如何在 CSV 文本文件中计算列值 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="56770-140">How to compute column values in a CSV text file (LINQ) (C#)</span></span>](./how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [<span data-ttu-id="56770-141">如何查询目录树中的一个或多个最大的文件 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="56770-141">How to query for the largest file or files in a directory tree (LINQ) (C#)</span></span>](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)
- [<span data-ttu-id="56770-142">如何查询一组文件夹中的总字节数 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="56770-142">How to query for the total number of bytes in a set of folders (LINQ) (C#)</span></span>](./how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)

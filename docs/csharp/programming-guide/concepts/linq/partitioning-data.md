---
title: 数据分区 (C#)
description: 了解如何在 LINQ 中对数据进行分区。 查看显示分区操作结果的图示。
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: 31beacd672addb3eb38ade8f2bf9cfae25f4d27a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176261"
---
# <a name="partitioning-data-c"></a><span data-ttu-id="a92ab-104">数据分区 (C#)</span><span class="sxs-lookup"><span data-stu-id="a92ab-104">Partitioning Data (C#)</span></span>

<span data-ttu-id="a92ab-105">LINQ 中的分区是指将输入序列划分为两个部分的操作，无需重新排列元素，然后返回其中一个部分。</span><span class="sxs-lookup"><span data-stu-id="a92ab-105">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="a92ab-106">下图显示对字符序列进行三种不同的分区操作的结果。</span><span class="sxs-lookup"><span data-stu-id="a92ab-106">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="a92ab-107">第一个操作返回序列中的前三个元素。</span><span class="sxs-lookup"><span data-stu-id="a92ab-107">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="a92ab-108">第二个操作跳过前三个元素，返回剩余元素。</span><span class="sxs-lookup"><span data-stu-id="a92ab-108">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="a92ab-109">第三个操作跳过序列中的前两个元素，返回接下来的三个元素。</span><span class="sxs-lookup"><span data-stu-id="a92ab-109">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![显示三个 LINQ 分区操作的图示。](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="a92ab-111">下面一节列出了对序列进行分区的标准查询运算符方法。</span><span class="sxs-lookup"><span data-stu-id="a92ab-111">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="a92ab-112">运算符</span><span class="sxs-lookup"><span data-stu-id="a92ab-112">Operators</span></span>  
  
|<span data-ttu-id="a92ab-113">运算符名称</span><span class="sxs-lookup"><span data-stu-id="a92ab-113">Operator Name</span></span>|<span data-ttu-id="a92ab-114">描述</span><span class="sxs-lookup"><span data-stu-id="a92ab-114">Description</span></span>|<span data-ttu-id="a92ab-115">C# 查询表达式语法</span><span class="sxs-lookup"><span data-stu-id="a92ab-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="a92ab-116">更多信息</span><span class="sxs-lookup"><span data-stu-id="a92ab-116">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="a92ab-117">Skip</span><span class="sxs-lookup"><span data-stu-id="a92ab-117">Skip</span></span>|<span data-ttu-id="a92ab-118">跳过序列中指定位置之前的元素。</span><span class="sxs-lookup"><span data-stu-id="a92ab-118">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="a92ab-119">不适用。</span><span class="sxs-lookup"><span data-stu-id="a92ab-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a92ab-120">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="a92ab-120">SkipWhile</span></span>|<span data-ttu-id="a92ab-121">基于谓词函数跳过元素，直到元素不符合条件。</span><span class="sxs-lookup"><span data-stu-id="a92ab-121">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="a92ab-122">不适用。</span><span class="sxs-lookup"><span data-stu-id="a92ab-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a92ab-123">Take</span><span class="sxs-lookup"><span data-stu-id="a92ab-123">Take</span></span>|<span data-ttu-id="a92ab-124">获取序列中指定位置之前的元素。</span><span class="sxs-lookup"><span data-stu-id="a92ab-124">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="a92ab-125">不适用。</span><span class="sxs-lookup"><span data-stu-id="a92ab-125">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a92ab-126">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="a92ab-126">TakeWhile</span></span>|<span data-ttu-id="a92ab-127">基于谓词函数获取元素，直到元素不符合条件。</span><span class="sxs-lookup"><span data-stu-id="a92ab-127">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="a92ab-128">不适用。</span><span class="sxs-lookup"><span data-stu-id="a92ab-128">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="a92ab-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="a92ab-129">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="a92ab-130">标准查询运算符概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="a92ab-130">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)

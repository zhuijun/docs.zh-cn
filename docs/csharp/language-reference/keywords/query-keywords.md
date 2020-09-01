---
description: 查询关键字 - C# 参考
title: 查询关键字 - C# 参考
ms.date: 07/20/2015
helpviewer_keywords:
- query keywords [C#]
- LINQ [C#], query keywords
ms.assetid: 6c9bec16-dbd7-4a7c-a060-fe4600b2021f
ms.openlocfilehash: 0beea8634d13222aa18f14d79fdbd95a35cc832e
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137131"
---
# <a name="query-keywords-c-reference"></a><span data-ttu-id="09215-103">查询关键字（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="09215-103">Query keywords (C# Reference)</span></span>

<span data-ttu-id="09215-104">本部分包含在查询表达式中使用的上下文关键字。</span><span class="sxs-lookup"><span data-stu-id="09215-104">This section contains the contextual keywords used in query expressions.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="09215-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="09215-105">In this section</span></span>

|<span data-ttu-id="09215-106">子句</span><span class="sxs-lookup"><span data-stu-id="09215-106">Clause</span></span>|<span data-ttu-id="09215-107">说明</span><span class="sxs-lookup"><span data-stu-id="09215-107">Description</span></span>|
|------------|-----------------|
|[<span data-ttu-id="09215-108">from</span><span class="sxs-lookup"><span data-stu-id="09215-108">from</span></span>](from-clause.md)|<span data-ttu-id="09215-109">指定数据源和范围变量（类似于迭代变量）。</span><span class="sxs-lookup"><span data-stu-id="09215-109">Specifies a data source and a range variable (similar to an iteration variable).</span></span>|
|[<span data-ttu-id="09215-110">where</span><span class="sxs-lookup"><span data-stu-id="09215-110">where</span></span>](where-clause.md)|<span data-ttu-id="09215-111">基于由逻辑 AND 和 OR 运算符（`&&` 或 <code>&#124;&#124;</code>）分隔的一个或多个布尔表达式筛选源元素。</span><span class="sxs-lookup"><span data-stu-id="09215-111">Filters source elements based on one or more Boolean expressions separated by logical AND and OR operators ( `&&` or <code>&#124;&#124;</code> ).</span></span>|
|[<span data-ttu-id="09215-112">select</span><span class="sxs-lookup"><span data-stu-id="09215-112">select</span></span>](select-clause.md)|<span data-ttu-id="09215-113">指定执行查询时，所返回序列中元素的类型和形状。</span><span class="sxs-lookup"><span data-stu-id="09215-113">Specifies the type and shape that the elements in the returned sequence will have when the query is executed.</span></span>|
|[<span data-ttu-id="09215-114">group</span><span class="sxs-lookup"><span data-stu-id="09215-114">group</span></span>](group-clause.md)|<span data-ttu-id="09215-115">根据指定的密钥值对查询结果分组。</span><span class="sxs-lookup"><span data-stu-id="09215-115">Groups query results according to a specified key value.</span></span>|
|[<span data-ttu-id="09215-116">into</span><span class="sxs-lookup"><span data-stu-id="09215-116">into</span></span>](into.md)|<span data-ttu-id="09215-117">提供可作为对 join、group 或 select 子句结果引用的标识符。</span><span class="sxs-lookup"><span data-stu-id="09215-117">Provides an identifier that can serve as a reference to the results of a join, group or select clause.</span></span>|
|[<span data-ttu-id="09215-118">orderby</span><span class="sxs-lookup"><span data-stu-id="09215-118">orderby</span></span>](orderby-clause.md)|<span data-ttu-id="09215-119">根据元素类型的默认比较器对查询结果进行升序或降序排序。</span><span class="sxs-lookup"><span data-stu-id="09215-119">Sorts query results in ascending or descending order based on the default comparer for the element type.</span></span>|
|[<span data-ttu-id="09215-120">join</span><span class="sxs-lookup"><span data-stu-id="09215-120">join</span></span>](join-clause.md)|<span data-ttu-id="09215-121">基于两个指定匹配条件间的相等比较而联接两个数据源。</span><span class="sxs-lookup"><span data-stu-id="09215-121">Joins two data sources based on an equality comparison between two specified matching criteria.</span></span>|
|[<span data-ttu-id="09215-122">let</span><span class="sxs-lookup"><span data-stu-id="09215-122">let</span></span>](let-clause.md)|<span data-ttu-id="09215-123">引入范围变量，在查询表达式中存储子表达式结果。</span><span class="sxs-lookup"><span data-stu-id="09215-123">Introduces a range variable to store sub-expression results in a query expression.</span></span>|
|[<span data-ttu-id="09215-124">in</span><span class="sxs-lookup"><span data-stu-id="09215-124">in</span></span>](in.md)|<span data-ttu-id="09215-125">[join](join-clause.md) 子句中的上下文关键字。</span><span class="sxs-lookup"><span data-stu-id="09215-125">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="09215-126">on</span><span class="sxs-lookup"><span data-stu-id="09215-126">on</span></span>](on.md)|<span data-ttu-id="09215-127">[join](join-clause.md) 子句中的上下文关键字。</span><span class="sxs-lookup"><span data-stu-id="09215-127">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="09215-128">equals</span><span class="sxs-lookup"><span data-stu-id="09215-128">equals</span></span>](equals.md)|<span data-ttu-id="09215-129">[join](join-clause.md) 子句中的上下文关键字。</span><span class="sxs-lookup"><span data-stu-id="09215-129">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="09215-130">by</span><span class="sxs-lookup"><span data-stu-id="09215-130">by</span></span>](by.md)|<span data-ttu-id="09215-131">[group](group-clause.md) 子句中的上下文关键字。</span><span class="sxs-lookup"><span data-stu-id="09215-131">Contextual keyword in a [group](group-clause.md) clause.</span></span>|
|[<span data-ttu-id="09215-132">ascending</span><span class="sxs-lookup"><span data-stu-id="09215-132">ascending</span></span>](ascending.md)|<span data-ttu-id="09215-133">[orderby](orderby-clause.md) 子句中的上下文关键字。</span><span class="sxs-lookup"><span data-stu-id="09215-133">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|
|[<span data-ttu-id="09215-134">descending</span><span class="sxs-lookup"><span data-stu-id="09215-134">descending</span></span>](descending.md)|<span data-ttu-id="09215-135">[orderby](orderby-clause.md) 子句中的上下文关键字。</span><span class="sxs-lookup"><span data-stu-id="09215-135">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|

## <a name="see-also"></a><span data-ttu-id="09215-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="09215-136">See also</span></span>

- [<span data-ttu-id="09215-137">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="09215-137">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="09215-138">LINQ（语言集成查询）</span><span class="sxs-lookup"><span data-stu-id="09215-138">LINQ (Language-Integrated Query)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="09215-139">C# 中的 LINQ</span><span class="sxs-lookup"><span data-stu-id="09215-139">LINQ in C#</span></span>](../../linq/index.md)

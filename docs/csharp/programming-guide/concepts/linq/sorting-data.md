---
title: 对数据排序 (C#)
description: 了解排序操作以及使用 C# 中的 LINQ 执行排序操作的标准查询运算符方法。
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 5feeb0e2229fc370fdcb9608817f41832bffd7cc
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302329"
---
# <a name="sorting-data-c"></a><span data-ttu-id="69a8f-103">对数据排序 (C#)</span><span class="sxs-lookup"><span data-stu-id="69a8f-103">Sorting Data (C#)</span></span>
<span data-ttu-id="69a8f-104">排序操作基于一个或多个属性对序列的元素进行排序。</span><span class="sxs-lookup"><span data-stu-id="69a8f-104">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="69a8f-105">第一个排序条件对元素执行主要排序。</span><span class="sxs-lookup"><span data-stu-id="69a8f-105">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="69a8f-106">通过指定第二个排序条件，您可以对每个主要排序组内的元素进行排序。</span><span class="sxs-lookup"><span data-stu-id="69a8f-106">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="69a8f-107">下图展示了对一系列字符执行按字母顺序排序操作的结果。</span><span class="sxs-lookup"><span data-stu-id="69a8f-107">The following illustration shows the results of an alphabetical sort operation on a sequence of characters:</span></span>
  
 ![展示按字母顺序排序操作的图。](./media/sorting-data/alphabetical-sort-operation.png)  
  
 <span data-ttu-id="69a8f-109">下节列出了对数据进行排序的标准查询运算符方法。</span><span class="sxs-lookup"><span data-stu-id="69a8f-109">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="69a8f-110">方法</span><span class="sxs-lookup"><span data-stu-id="69a8f-110">Methods</span></span>  
  
|<span data-ttu-id="69a8f-111">方法名</span><span class="sxs-lookup"><span data-stu-id="69a8f-111">Method Name</span></span>|<span data-ttu-id="69a8f-112">描述</span><span class="sxs-lookup"><span data-stu-id="69a8f-112">Description</span></span>|<span data-ttu-id="69a8f-113">C# 查询表达式语法</span><span class="sxs-lookup"><span data-stu-id="69a8f-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="69a8f-114">更多信息</span><span class="sxs-lookup"><span data-stu-id="69a8f-114">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="69a8f-115">OrderBy</span><span class="sxs-lookup"><span data-stu-id="69a8f-115">OrderBy</span></span>|<span data-ttu-id="69a8f-116">按升序对值排序。</span><span class="sxs-lookup"><span data-stu-id="69a8f-116">Sorts values in ascending order.</span></span>|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="69a8f-117">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="69a8f-117">OrderByDescending</span></span>|<span data-ttu-id="69a8f-118">按降序对值排序。</span><span class="sxs-lookup"><span data-stu-id="69a8f-118">Sorts values in descending order.</span></span>|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="69a8f-119">ThenBy</span><span class="sxs-lookup"><span data-stu-id="69a8f-119">ThenBy</span></span>|<span data-ttu-id="69a8f-120">按升序执行次要排序。</span><span class="sxs-lookup"><span data-stu-id="69a8f-120">Performs a secondary sort in ascending order.</span></span>|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="69a8f-121">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="69a8f-121">ThenByDescending</span></span>|<span data-ttu-id="69a8f-122">按降序执行次要排序。</span><span class="sxs-lookup"><span data-stu-id="69a8f-122">Performs a secondary sort in descending order.</span></span>|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="69a8f-123">Reverse</span><span class="sxs-lookup"><span data-stu-id="69a8f-123">Reverse</span></span>|<span data-ttu-id="69a8f-124">反转集合中元素的顺序。</span><span class="sxs-lookup"><span data-stu-id="69a8f-124">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="69a8f-125">不适用。</span><span class="sxs-lookup"><span data-stu-id="69a8f-125">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="69a8f-126">查询表达式语法示例</span><span class="sxs-lookup"><span data-stu-id="69a8f-126">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="69a8f-127">主要排序示例</span><span class="sxs-lookup"><span data-stu-id="69a8f-127">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="69a8f-128">主要升序排序</span><span class="sxs-lookup"><span data-stu-id="69a8f-128">Primary Ascending Sort</span></span>  
 <span data-ttu-id="69a8f-129">下面的示例演示如何在 LINQ 查询中使用 `orderby` 子句按字符串长度对数组中的字符串进行升序排序。</span><span class="sxs-lookup"><span data-stu-id="69a8f-129">The following example demonstrates how to use the `orderby` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
    quick  
    brown  
    jumps  
*/  
```  
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="69a8f-130">主要降序排序</span><span class="sxs-lookup"><span data-stu-id="69a8f-130">Primary Descending Sort</span></span>  
 <span data-ttu-id="69a8f-131">下面的示例演示如何在 LINQ 查询中使用 `orderby descending` 子句按字符串的第一个字母对字符串进行降序排序。</span><span class="sxs-lookup"><span data-stu-id="69a8f-131">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Substring(0, 1) descending  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    quick  
    jumps  
    fox  
    brown  
*/  
```  
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="69a8f-132">次要排序示例</span><span class="sxs-lookup"><span data-stu-id="69a8f-132">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="69a8f-133">次要升序排序</span><span class="sxs-lookup"><span data-stu-id="69a8f-133">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="69a8f-134">下面的示例演示如何在 LINQ 查询中使用 `orderby` 子句对数组中的字符串执行主要和次要排序。</span><span class="sxs-lookup"><span data-stu-id="69a8f-134">The following example demonstrates how to use the `orderby` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="69a8f-135">首先按字符串长度，其次按字符串的第一个字母，对字符串进行升序排序。</span><span class="sxs-lookup"><span data-stu-id="69a8f-135">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length, word.Substring(0, 1)  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    fox  
    the  
    brown  
    jumps  
    quick  
*/  
```  
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="69a8f-136">次要降序排序</span><span class="sxs-lookup"><span data-stu-id="69a8f-136">Secondary Descending Sort</span></span>  
 <span data-ttu-id="69a8f-137">下面的示例演示如何在 LINQ 查询中使用 `orderby descending` 子句按升序执行主要排序，按降序执行次要排序。</span><span class="sxs-lookup"><span data-stu-id="69a8f-137">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="69a8f-138">首先按字符串长度，其次按字符串的第一个字母，对字符串进行排序。</span><span class="sxs-lookup"><span data-stu-id="69a8f-138">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length, word.Substring(0, 1) descending  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
    quick  
    jumps  
    brown  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="69a8f-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="69a8f-139">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="69a8f-140">标准查询运算符概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="69a8f-140">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="69a8f-141">orderby 子句</span><span class="sxs-lookup"><span data-stu-id="69a8f-141">orderby clause</span></span>](../../../language-reference/keywords/orderby-clause.md)
- [<span data-ttu-id="69a8f-142">对 Join 子句的结果进行排序</span><span class="sxs-lookup"><span data-stu-id="69a8f-142">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="69a8f-143">如何按任意词或字段对文本数据进行排序或筛选 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="69a8f-143">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

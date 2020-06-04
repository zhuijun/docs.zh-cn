---
title: 转换数据类型
ms.date: 07/20/2015
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
ms.openlocfilehash: 1394f53923ba850ae11fbc326a25c279589c3be1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410846"
---
# <a name="converting-data-types-visual-basic"></a><span data-ttu-id="5b47d-102">转换数据类型（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="5b47d-102">Converting Data Types (Visual Basic)</span></span>

<span data-ttu-id="5b47d-103">转换方法可更改输入对象的类型。</span><span class="sxs-lookup"><span data-stu-id="5b47d-103">Conversion methods change the type of input objects.</span></span>

 <span data-ttu-id="5b47d-104">LINQ 查询中的转换运算可用于各种应用程序。</span><span class="sxs-lookup"><span data-stu-id="5b47d-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="5b47d-105">下面是一些示例：</span><span class="sxs-lookup"><span data-stu-id="5b47d-105">The following are some examples:</span></span>

- <span data-ttu-id="5b47d-106"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> 方法可用于隐藏类型的标准查询运算符自定义实现。</span><span class="sxs-lookup"><span data-stu-id="5b47d-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>

- <span data-ttu-id="5b47d-107"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> 方法可用于为 LINQ 查询启用非参数化集合。</span><span class="sxs-lookup"><span data-stu-id="5b47d-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>

- <span data-ttu-id="5b47d-108"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>、<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>、<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> 和 <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> 方法可用于强制执行即时的查询，而不是将其推迟到枚举该查询时。</span><span class="sxs-lookup"><span data-stu-id="5b47d-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>

## <a name="methods"></a><span data-ttu-id="5b47d-109">方法</span><span class="sxs-lookup"><span data-stu-id="5b47d-109">Methods</span></span>

<span data-ttu-id="5b47d-110">下表列出了执行数据类型转换的标准查询运算符方法。</span><span class="sxs-lookup"><span data-stu-id="5b47d-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>

<span data-ttu-id="5b47d-111">本表中名称以“As”开头的转换方法可更改源集合的静态类型，但不对其进行枚举。</span><span class="sxs-lookup"><span data-stu-id="5b47d-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="5b47d-112">名称以“To”开头的方法可枚举源集合，并将项放入相应的集合类型。</span><span class="sxs-lookup"><span data-stu-id="5b47d-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>

|<span data-ttu-id="5b47d-113">方法名称</span><span class="sxs-lookup"><span data-stu-id="5b47d-113">Method Name</span></span>|<span data-ttu-id="5b47d-114">说明</span><span class="sxs-lookup"><span data-stu-id="5b47d-114">Description</span></span>|<span data-ttu-id="5b47d-115">Visual Basic 查询表达式语法</span><span class="sxs-lookup"><span data-stu-id="5b47d-115">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="5b47d-116">更多信息</span><span class="sxs-lookup"><span data-stu-id="5b47d-116">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="5b47d-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="5b47d-117">AsEnumerable</span></span>|<span data-ttu-id="5b47d-118">返回类型化为 <xref:System.Collections.Generic.IEnumerable%601> 的输入。</span><span class="sxs-lookup"><span data-stu-id="5b47d-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="5b47d-119">不适用。</span><span class="sxs-lookup"><span data-stu-id="5b47d-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="5b47d-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="5b47d-120">AsQueryable</span></span>|<span data-ttu-id="5b47d-121">将（泛型）<xref:System.Collections.IEnumerable> 转换为（泛型）<xref:System.Linq.IQueryable>。</span><span class="sxs-lookup"><span data-stu-id="5b47d-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="5b47d-122">不适用。</span><span class="sxs-lookup"><span data-stu-id="5b47d-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="5b47d-123">Cast</span><span class="sxs-lookup"><span data-stu-id="5b47d-123">Cast</span></span>|<span data-ttu-id="5b47d-124">将集合中的元素转换为指定类型。</span><span class="sxs-lookup"><span data-stu-id="5b47d-124">Casts the elements of a collection to a specified type.</span></span>|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|<span data-ttu-id="5b47d-125">OfType</span><span class="sxs-lookup"><span data-stu-id="5b47d-125">OfType</span></span>|<span data-ttu-id="5b47d-126">根据其转换为指定类型的能力筛选值。</span><span class="sxs-lookup"><span data-stu-id="5b47d-126">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="5b47d-127">不适用。</span><span class="sxs-lookup"><span data-stu-id="5b47d-127">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="5b47d-128">ToArray</span><span class="sxs-lookup"><span data-stu-id="5b47d-128">ToArray</span></span>|<span data-ttu-id="5b47d-129">将集合转换为数组。</span><span class="sxs-lookup"><span data-stu-id="5b47d-129">Converts a collection to an array.</span></span> <span data-ttu-id="5b47d-130">此方法强制执行查询。</span><span class="sxs-lookup"><span data-stu-id="5b47d-130">This method forces query execution.</span></span>|<span data-ttu-id="5b47d-131">不适用。</span><span class="sxs-lookup"><span data-stu-id="5b47d-131">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|<span data-ttu-id="5b47d-132">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="5b47d-132">ToDictionary</span></span>|<span data-ttu-id="5b47d-133">根据键选择器函数将元素放入 <xref:System.Collections.Generic.Dictionary%602>。</span><span class="sxs-lookup"><span data-stu-id="5b47d-133">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="5b47d-134">此方法强制执行查询。</span><span class="sxs-lookup"><span data-stu-id="5b47d-134">This method forces query execution.</span></span>|<span data-ttu-id="5b47d-135">不适用。</span><span class="sxs-lookup"><span data-stu-id="5b47d-135">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|<span data-ttu-id="5b47d-136">ToList</span><span class="sxs-lookup"><span data-stu-id="5b47d-136">ToList</span></span>|<span data-ttu-id="5b47d-137">将集合转换为 <xref:System.Collections.Generic.List%601>。</span><span class="sxs-lookup"><span data-stu-id="5b47d-137">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="5b47d-138">此方法强制执行查询。</span><span class="sxs-lookup"><span data-stu-id="5b47d-138">This method forces query execution.</span></span>|<span data-ttu-id="5b47d-139">不适用。</span><span class="sxs-lookup"><span data-stu-id="5b47d-139">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|<span data-ttu-id="5b47d-140">ToLookup</span><span class="sxs-lookup"><span data-stu-id="5b47d-140">ToLookup</span></span>|<span data-ttu-id="5b47d-141">根据键选择器函数将元素放入 <xref:System.Linq.Lookup%602>（一对多字典）。</span><span class="sxs-lookup"><span data-stu-id="5b47d-141">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="5b47d-142">此方法强制执行查询。</span><span class="sxs-lookup"><span data-stu-id="5b47d-142">This method forces query execution.</span></span>|<span data-ttu-id="5b47d-143">不适用。</span><span class="sxs-lookup"><span data-stu-id="5b47d-143">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="5b47d-144">查询表达式语法示例</span><span class="sxs-lookup"><span data-stu-id="5b47d-144">Query Expression Syntax Example</span></span>

<span data-ttu-id="5b47d-145">下面的代码示例使用 `From As` 子句将类型转换为子类型，然后访问仅在子类型上可用的成员。</span><span class="sxs-lookup"><span data-stu-id="5b47d-145">The following code example uses the `From As` clause to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>

```vb
Class Plant
    Public Property Name As String
End Class

Class CarnivorousPlant
    Inherits Plant
    Public Property TrapType As String
End Class

Sub Cast()

    Dim plants() As Plant = {
        New CarnivorousPlant With {.Name = "Venus Fly Trap", .TrapType = "Snap Trap"},
        New CarnivorousPlant With {.Name = "Pitcher Plant", .TrapType = "Pitfall Trap"},
        New CarnivorousPlant With {.Name = "Sundew", .TrapType = "Flypaper Trap"},
        New CarnivorousPlant With {.Name = "Waterwheel Plant", .TrapType = "Snap Trap"}}

    Dim query = From plant As CarnivorousPlant In plants
                Where plant.TrapType = "Snap Trap"
                Select plant

    Dim sb As New System.Text.StringBuilder()
    For Each plant In query
        sb.AppendLine(plant.Name)
    Next

    ' Display the results.
    MsgBox(sb.ToString())

    ' This code produces the following output:

    ' Venus Fly Trap
    ' Waterwheel Plant

End Sub
```

## <a name="see-also"></a><span data-ttu-id="5b47d-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5b47d-146">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="5b47d-147">标准查询运算符概述 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b47d-147">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="5b47d-148">From 子句</span><span class="sxs-lookup"><span data-stu-id="5b47d-148">From Clause</span></span>](../../../language-reference/queries/from-clause.md)
- [<span data-ttu-id="5b47d-149">如何：使用 LINQ 查询 ArrayList （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="5b47d-149">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](how-to-query-an-arraylist-with-linq.md)

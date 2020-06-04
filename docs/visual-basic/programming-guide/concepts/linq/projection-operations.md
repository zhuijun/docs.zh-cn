---
title: 投影运算
ms.date: 07/20/2015
ms.assetid: b8d38e6d-21cf-4619-8dbb-94476f4badc7
ms.openlocfilehash: 4795bdaba53949b34fe380ea9c51025ce43c40db
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396332"
---
# <a name="projection-operations-visual-basic"></a><span data-ttu-id="9013e-102">投影操作（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="9013e-102">Projection Operations (Visual Basic)</span></span>

<span data-ttu-id="9013e-103">投影是指将对象转换为一种新形式的操作，该形式通常只包含那些将随后使用的属性。</span><span class="sxs-lookup"><span data-stu-id="9013e-103">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="9013e-104">通过使用投影，您可以构造从每个对象生成的新类型。</span><span class="sxs-lookup"><span data-stu-id="9013e-104">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="9013e-105">可以投影属性，并对该属性执行数学函数。</span><span class="sxs-lookup"><span data-stu-id="9013e-105">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="9013e-106">还可以在不更改原始对象的情况下投影该对象。</span><span class="sxs-lookup"><span data-stu-id="9013e-106">You can also project the original object without changing it.</span></span>

<span data-ttu-id="9013e-107">下面一节列出了执行投影的标准查询运算符方法。</span><span class="sxs-lookup"><span data-stu-id="9013e-107">The standard query operator methods that perform projection are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="9013e-108">方法</span><span class="sxs-lookup"><span data-stu-id="9013e-108">Methods</span></span>

|<span data-ttu-id="9013e-109">方法名</span><span class="sxs-lookup"><span data-stu-id="9013e-109">Method Name</span></span>|<span data-ttu-id="9013e-110">说明</span><span class="sxs-lookup"><span data-stu-id="9013e-110">Description</span></span>|<span data-ttu-id="9013e-111">Visual Basic 查询表达式语法</span><span class="sxs-lookup"><span data-stu-id="9013e-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="9013e-112">详细信息</span><span class="sxs-lookup"><span data-stu-id="9013e-112">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="9013e-113">选择</span><span class="sxs-lookup"><span data-stu-id="9013e-113">Select</span></span>|<span data-ttu-id="9013e-114">投影基于转换函数的值。</span><span class="sxs-lookup"><span data-stu-id="9013e-114">Projects values that are based on a transform function.</span></span>|`Select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|
|<span data-ttu-id="9013e-115">SelectMany</span><span class="sxs-lookup"><span data-stu-id="9013e-115">SelectMany</span></span>|<span data-ttu-id="9013e-116">投影基于转换函数的值序列，然后将它们展平为一个序列。</span><span class="sxs-lookup"><span data-stu-id="9013e-116">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="9013e-117">使用多个 `From` 子句</span><span class="sxs-lookup"><span data-stu-id="9013e-117">Use multiple `From` clauses</span></span>|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="9013e-118">查询表达式语法示例</span><span class="sxs-lookup"><span data-stu-id="9013e-118">Query Expression Syntax Examples</span></span>

### <a name="select"></a><span data-ttu-id="9013e-119">选择</span><span class="sxs-lookup"><span data-stu-id="9013e-119">Select</span></span>

<span data-ttu-id="9013e-120">下面的示例使用 `Select` 子句来投影字符串列表中每个字符串的第一个字母。</span><span class="sxs-lookup"><span data-stu-id="9013e-120">The following example uses the `Select` clause to project the first letter from each string in a list of strings.</span></span>

```vb
Dim words = New List(Of String) From {"an", "apple", "a", "day"}

Dim query = From word In words
            Select word.Substring(0, 1)

Dim sb As New System.Text.StringBuilder()
For Each letter As String In query
    sb.AppendLine(letter)
Next

' Display the output.
MsgBox(sb.ToString())

' This code produces the following output:

' a
' a
' a
' d
```

### <a name="selectmany"></a><span data-ttu-id="9013e-121">SelectMany</span><span class="sxs-lookup"><span data-stu-id="9013e-121">SelectMany</span></span>

<span data-ttu-id="9013e-122">下面的示例使用多个 `From` 子句来投影字符串列表中每个字符串的每个单词。</span><span class="sxs-lookup"><span data-stu-id="9013e-122">The following example uses multiple `From` clauses to project each word from each string in a list of strings.</span></span>

```vb
Dim phrases = New List(Of String) From {"an apple a day", "the quick brown fox"}

Dim query = From phrase In phrases
            From word In phrase.Split(" "c)
            Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In query
    sb.AppendLine(str)
Next

' Display the output.
MsgBox(sb.ToString())

' This code produces the following output:

' an
' apple
' a
' day
' the
' quick
' brown
' fox
```

## <a name="select-versus-selectmany"></a><span data-ttu-id="9013e-123">Select 与 SelectMany</span><span class="sxs-lookup"><span data-stu-id="9013e-123">Select versus SelectMany</span></span>

<span data-ttu-id="9013e-124">`Select()` 和 `SelectMany()` 的工作都是依据源值生成一个或多个结果值。</span><span class="sxs-lookup"><span data-stu-id="9013e-124">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="9013e-125">`Select()` 为每个源值生成一个结果值。</span><span class="sxs-lookup"><span data-stu-id="9013e-125">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="9013e-126">因此，总体结果是一个与源集合具有相同元素数目的集合。</span><span class="sxs-lookup"><span data-stu-id="9013e-126">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="9013e-127">与之相反，`SelectMany()` 生成单个总体结果，其中包含来自每个源值的串联子集合。</span><span class="sxs-lookup"><span data-stu-id="9013e-127">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="9013e-128">作为参数传递到 `SelectMany()` 的转换函数必须为每个源值返回一个可枚举值序列。</span><span class="sxs-lookup"><span data-stu-id="9013e-128">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="9013e-129">然后，`SelectMany()` 串联这些可枚举序列，以创建一个大的序列。</span><span class="sxs-lookup"><span data-stu-id="9013e-129">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>

<span data-ttu-id="9013e-130">下面两个插图演示了这两个方法的操作之间的概念性区别。</span><span class="sxs-lookup"><span data-stu-id="9013e-130">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="9013e-131">在每种情况下，假定选择器（转换）函数从每个源值中选择一个由花卉数据组成的数组。</span><span class="sxs-lookup"><span data-stu-id="9013e-131">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>

<span data-ttu-id="9013e-132">下图描述 `Select()` 如何返回一个与源集合具有相同元素数目的集合。</span><span class="sxs-lookup"><span data-stu-id="9013e-132">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>

![显示 Select() 的操作的图](./media/projection-operations/select-action-graphic.png)

<span data-ttu-id="9013e-134">下图描述 `SelectMany()` 如何将中间数组序列串联为一个最终结果值，其中包含每个中间数组中的每个值。</span><span class="sxs-lookup"><span data-stu-id="9013e-134">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>

![显示 SelectMany() 的操作的图。](./media/projection-operations/select-many-action-graphic.png )

### <a name="code-example"></a><span data-ttu-id="9013e-136">代码示例</span><span class="sxs-lookup"><span data-stu-id="9013e-136">Code Example</span></span>

<span data-ttu-id="9013e-137">下面的示例比较 `Select()` 和 `SelectMany()` 的行为。</span><span class="sxs-lookup"><span data-stu-id="9013e-137">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="9013e-138">代码通过从源集合的每个花卉名称列表中提取前两项来创建一个“花束”。</span><span class="sxs-lookup"><span data-stu-id="9013e-138">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="9013e-139">此示例中，transform 函数 <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> 使用的“单值”本身即是值的集合。</span><span class="sxs-lookup"><span data-stu-id="9013e-139">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="9013e-140">这需要额外的 `For Each` 循环，以便枚举每个子序列中的每个字符串。</span><span class="sxs-lookup"><span data-stu-id="9013e-140">This requires the extra `For Each` loop in order to enumerate each string in each sub-sequence.</span></span>

```vb
Class Bouquet
    Public Flowers As List(Of String)
End Class

Sub SelectVsSelectMany()
    Dim bouquets = New List(Of Bouquet) From {
        New Bouquet With {.Flowers = New List(Of String)(New String() {"sunflower", "daisy", "daffodil", "larkspur"})},
        New Bouquet With {.Flowers = New List(Of String)(New String() {"tulip", "rose", "orchid"})},
        New Bouquet With {.Flowers = New List(Of String)(New String() {"gladiolis", "lily", "snapdragon", "aster", "protea"})},
        New Bouquet With {.Flowers = New List(Of String)(New String() {"larkspur", "lilac", "iris", "dahlia"})}}

    Dim output As New System.Text.StringBuilder

    ' Select()
    Dim query1 = bouquets.Select(Function(b) b.Flowers)

    output.AppendLine("Using Select():")
    For Each flowerList In query1
        For Each str As String In flowerList
            output.AppendLine(str)
        Next
    Next

    ' SelectMany()
    Dim query2 = bouquets.SelectMany(Function(b) b.Flowers)

    output.AppendLine(vbCrLf & "Using SelectMany():")
    For Each str As String In query2
        output.AppendLine(str)
    Next

    ' Display the output
    MsgBox(output.ToString())

    ' This code produces the following output:
    '
    ' Using Select():
    ' sunflower
    ' daisy
    ' daffodil
    ' larkspur
    ' tulip
    ' rose
    ' orchid
    ' gladiolis
    ' lily
    ' snapdragon
    ' aster
    ' protea
    ' larkspur
    ' lilac
    ' iris
    ' dahlia

    ' Using SelectMany()
    ' sunflower
    ' daisy
    ' daffodil
    ' larkspur
    ' tulip
    ' rose
    ' orchid
    ' gladiolis
    ' lily
    ' snapdragon
    ' aster
    ' protea
    ' larkspur
    ' lilac
    ' iris
    ' dahlia

End Sub
```

## <a name="see-also"></a><span data-ttu-id="9013e-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9013e-141">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="9013e-142">标准查询运算符概述 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9013e-142">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="9013e-143">Select 子句</span><span class="sxs-lookup"><span data-stu-id="9013e-143">Select Clause</span></span>](../../../language-reference/queries/select-clause.md)
- [<span data-ttu-id="9013e-144">如何：使用联接合并数据</span><span class="sxs-lookup"><span data-stu-id="9013e-144">How to: Combine Data with Joins</span></span>](../../language-features/linq/how-to-combine-data-with-linq-by-using-joins.md)
- [<span data-ttu-id="9013e-145">如何：从多个源填充对象集合（LINQ）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="9013e-145">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)
- [<span data-ttu-id="9013e-146">如何：以特定类型返回 LINQ 查询结果</span><span class="sxs-lookup"><span data-stu-id="9013e-146">How to: Return a LINQ Query Result as a Specific Type</span></span>](../../language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md)
- [<span data-ttu-id="9013e-147">如何：使用组将一个文件拆分成多个文件（LINQ）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="9013e-147">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)

---
title: 如何：为 LINQ 查询添加自定义方法
ms.date: 07/20/2015
ms.assetid: 099b2e2a-83cd-45c6-aa4d-01b398b5faaf
ms.openlocfilehash: 55004441d2d1d74556da6841f28d113b876d1048
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400599"
---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a><span data-ttu-id="d4d5a-102">如何：为 LINQ 查询添加自定义方法（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="d4d5a-102">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span></span>

<span data-ttu-id="d4d5a-103">可通过向 <xref:System.Collections.Generic.IEnumerable%601> 接口添加扩展方法扩展可用于 LINQ 查询的方法集。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-103">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="d4d5a-104">例如，除了标准平均值或最大值运算，还可以创建自定义聚合方法，从一系列值计算单个值。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-104">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="d4d5a-105">此外可以创建一个方法，用作一个值序列的自定义筛选器或用于对其进行特定数据转换，并返回新的序列。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-105">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="d4d5a-106"><xref:System.Linq.Enumerable.Distinct%2A>、<xref:System.Linq.Enumerable.Skip%2A> 和 <xref:System.Linq.Enumerable.Reverse%2A> 就是此类方法的示例。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-106">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>

<span data-ttu-id="d4d5a-107">扩展 <xref:System.Collections.Generic.IEnumerable%601> 接口时，可以将自定义方法应用于任何可枚举集合。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-107">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="d4d5a-108">有关详细信息，请参阅[扩展方法](../../language-features/procedures/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-108">For more information, see [Extension Methods](../../language-features/procedures/extension-methods.md).</span></span>

## <a name="adding-an-aggregate-method"></a><span data-ttu-id="d4d5a-109">添加聚合对象</span><span class="sxs-lookup"><span data-stu-id="d4d5a-109">Adding an Aggregate Method</span></span>

<span data-ttu-id="d4d5a-110">聚合方法可从一组值计算单个值。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-110">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="d4d5a-111">LINQ 提供多个聚合方法，包括 <xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Min%2A> 和 <xref:System.Linq.Enumerable.Max%2A>。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-111">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="d4d5a-112">可以通过向 <xref:System.Collections.Generic.IEnumerable%601> 接口添加扩展方法来创建自己的聚合方法。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-112">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="d4d5a-113">下面的代码示例演示如何创建名为 `Median` 的扩展方法来计算类型为 `double` 的数字序列的中间值。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-113">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>

```vb
Imports System.Runtime.CompilerServices

Module LINQExtension

    ' Extension method for the IEnumerable(of T) interface.
    ' The method accepts only values of the Double type.
    <Extension()>
    Function Median(ByVal source As IEnumerable(Of Double)) As Double
        If source.Count = 0 Then
            Throw New InvalidOperationException("Cannot compute median for an empty set.")
        End If

        Dim sortedSource = From number In source
                           Order By number

        Dim itemIndex = sortedSource.Count \ 2

        If sortedSource.Count Mod 2 = 0 Then
            ' Even number of items in list.
            Return (sortedSource(itemIndex) + sortedSource(itemIndex - 1)) / 2
        Else
            ' Odd number of items in list.
            Return sortedSource(itemIndex)
        End If
    End Function
End Module
```

<span data-ttu-id="d4d5a-114">使用从 <xref:System.Collections.Generic.IEnumerable%601> 接口调用其他聚合方法的方式为任何可枚举集合调用此扩展方法。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-114">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

> [!NOTE]
> <span data-ttu-id="d4d5a-115">在 Visual Basic 中，可以对或子句使用方法调用或标准查询语法 `Aggregate` `Group By` 。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-115">In Visual Basic, you can either use a method call or standard query syntax for the `Aggregate` or `Group By` clause.</span></span> <span data-ttu-id="d4d5a-116">有关详细信息，请参阅[Aggregate 子句](../../../language-reference/queries/aggregate-clause.md)和[Group By 子句](../../../language-reference/queries/group-by-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-116">For more information, see [Aggregate Clause](../../../language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../language-reference/queries/group-by-clause.md).</span></span>

<span data-ttu-id="d4d5a-117">下面的代码示例说明如何为类型 `double` 的数组使用 `Median` 方法。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-117">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>

```vb
Dim numbers1() As Double = {1.9, 2, 8, 4, 5.7, 6, 7.2, 0}

Dim query1 = Aggregate num In numbers1 Into Median()

Console.WriteLine("Double: Median = " & query1)
```

```vb
' This code produces the following output:
'
' Double: Median = 4.85
```

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="d4d5a-118">重载聚合方法以接受各种类型</span><span class="sxs-lookup"><span data-stu-id="d4d5a-118">Overloading an Aggregate Method to Accept Various Types</span></span>

<span data-ttu-id="d4d5a-119">可以重载聚合方法，以便其接受各种类型的序列。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-119">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="d4d5a-120">标准做法是为每种类型都创建一个重载。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-120">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="d4d5a-121">另一种方法是创建一个采用泛型类型的重载，并使用委托将其转换为特定类型。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-121">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="d4d5a-122">还可以将两种方法结合。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-122">You can also combine both approaches.</span></span>

#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="d4d5a-123">为每种类型创建重载</span><span class="sxs-lookup"><span data-stu-id="d4d5a-123">To create an overload for each type</span></span>

<span data-ttu-id="d4d5a-124">可以为要支持的每种类型创建特定重载。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-124">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="d4d5a-125">下面的代码示例演示 `integer` 类型的 `Median` 方法的重载。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-125">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>

```vb
' Integer overload

<Extension()>
Function Median(ByVal source As IEnumerable(Of Integer)) As Double
    Return Aggregate num In source Select CDbl(num) Into med = Median()
End Function
```

<span data-ttu-id="d4d5a-126">现在便可以为 `integer` 和 `double` 类型调用 `Median` 重载了，如以下代码中所示：</span><span class="sxs-lookup"><span data-stu-id="d4d5a-126">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>

```vb
Dim numbers1() As Double = {1.9, 2, 8, 4, 5.7, 6, 7.2, 0}

Dim query1 = Aggregate num In numbers1 Into Median()

Console.WriteLine("Double: Median = " & query1)
```

```vb
Dim numbers2() As Integer = {1, 2, 3, 4, 5}

Dim query2 = Aggregate num In numbers2 Into Median()

Console.WriteLine("Integer: Median = " & query2)
```

```vb
' This code produces the following output:
'
' Double: Median = 4.85
' Integer: Median = 3
```

#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="d4d5a-127">创建一般重载</span><span class="sxs-lookup"><span data-stu-id="d4d5a-127">To create a generic overload</span></span>

<span data-ttu-id="d4d5a-128">还可以创建接受泛型对象序列的重载。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-128">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="d4d5a-129">此重载采用委托作为参数，并使用该参数将泛型类型的对象序列转换为特定类型。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-129">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>

<span data-ttu-id="d4d5a-130">下面的代码展示 `Median` 方法的重载，该重载将 <xref:System.Func%602> 委托作为参数。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-130">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="d4d5a-131">此委托采用泛型类型 T 的对象，并返回类型 `double` 的对象。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-131">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>

```vb
' Generic overload.

<Extension()>
Function Median(Of T)(ByVal source As IEnumerable(Of T),
                      ByVal selector As Func(Of T, Double)) As Double
    Return Aggregate num In source Select selector(num) Into med = Median()
End Function
```

<span data-ttu-id="d4d5a-132">现在，可以为任何类型的对象序列调用 `Median` 方法。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-132">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="d4d5a-133">如果类型不具有自己的方法重载，必须手动传递委托参数。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-133">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="d4d5a-134">在 Visual Basic 中，可以使用 lambda 表达式来实现此目的。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-134">In Visual Basic, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="d4d5a-135">此外，如果使用 `Aggregate` 或 `Group By` 子句而不是方法调用，则可以传递此子句范围内的任何值或表达式。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-135">Also, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>

<span data-ttu-id="d4d5a-136">下面的代码示例演示如何为整数数组和字符串数组调用 `Median` 方法。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-136">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="d4d5a-137">对于字符串，将计算数组中字符串长度的中值。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-137">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="d4d5a-138">该示例演示如何将 <xref:System.Func%602> 委托参数传递给每个用例的 `Median` 方法。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-138">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>

```vb
Dim numbers3() As Integer = {1, 2, 3, 4, 5}

' You can use num as a parameter for the Median method
' so that the compiler will implicitly convert its value to double.
' If there is no implicit conversion, the compiler will
' display an error message.

Dim query3 = Aggregate num In numbers3 Into Median(num)

Console.WriteLine("Integer: Median = " & query3)

Dim numbers4() As String = {"one", "two", "three", "four", "five"}

' With the generic overload, you can also use numeric properties of objects.

Dim query4 = Aggregate str In numbers4 Into Median(str.Length)

Console.WriteLine("String: Median = " & query4)

' This code produces the following output:
'
' Integer: Median = 3
' String: Median = 4
```

## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="d4d5a-139">添加返回集合的方法</span><span class="sxs-lookup"><span data-stu-id="d4d5a-139">Adding a Method That Returns a Collection</span></span>

<span data-ttu-id="d4d5a-140">可以使用会返回值序列的自定义查询方法来扩展 <xref:System.Collections.Generic.IEnumerable%601> 接口。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-140">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="d4d5a-141">在这种情况下，该方法必须返回类型 <xref:System.Collections.Generic.IEnumerable%601> 的集合。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-141">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="d4d5a-142">此类方法可用于将筛选器或数据转换应用于值序列。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-142">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>

<span data-ttu-id="d4d5a-143">下面的示例演示如何创建名为 `AlternateElements` 的扩展方法，该方法从集合中第一个元素开始按相隔一个元素的方式返回集合中的元素。</span><span class="sxs-lookup"><span data-stu-id="d4d5a-143">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>

```vb
' Extension method for the IEnumerable(of T) interface.
' The method returns every other element of a sequence.

<Extension()>
Function AlternateElements(Of T)(
    ByVal source As IEnumerable(Of T)
    ) As IEnumerable(Of T)

    Dim list As New List(Of T)
    Dim i = 0
    For Each element In source
        If (i Mod 2 = 0) Then
            list.Add(element)
        End If
        i = i + 1
    Next
    Return list
End Function
```

<span data-ttu-id="d4d5a-144">可使用从 <xref:System.Collections.Generic.IEnumerable%601> 接口调用其他方法的方式对任何可枚举集合调用此扩展方法，如下面的代码中所示：</span><span class="sxs-lookup"><span data-stu-id="d4d5a-144">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>

```vb
Dim strings() As String = {"a", "b", "c", "d", "e"}

Dim query = strings.AlternateElements()

For Each element In query
    Console.WriteLine(element)
Next

' This code produces the following output:
'
' a
' c
' e
```

## <a name="see-also"></a><span data-ttu-id="d4d5a-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d4d5a-145">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="d4d5a-146">扩展方法</span><span class="sxs-lookup"><span data-stu-id="d4d5a-146">Extension Methods</span></span>](../../language-features/procedures/extension-methods.md)

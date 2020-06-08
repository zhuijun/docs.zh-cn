---
title: 如何为 LINQ 查询添加自定义方法 (C#)
ms.date: 07/20/2015
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: e3f8ba8810d06a2e79093e6022ad6e79f3599468
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447025"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a><span data-ttu-id="33823-102">如何为 LINQ 查询添加自定义方法 (C#)</span><span class="sxs-lookup"><span data-stu-id="33823-102">How to add custom methods for LINQ queries (C#)</span></span>

<span data-ttu-id="33823-103">可通过向 <xref:System.Collections.Generic.IEnumerable%601> 接口添加扩展方法扩展可用于 LINQ 查询的方法集。</span><span class="sxs-lookup"><span data-stu-id="33823-103">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="33823-104">例如，除了标准平均值或最大值运算，还可以创建自定义聚合方法，从一系列值计算单个值。</span><span class="sxs-lookup"><span data-stu-id="33823-104">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="33823-105">此外可以创建一个方法，用作一个值序列的自定义筛选器或用于对其进行特定数据转换，并返回新的序列。</span><span class="sxs-lookup"><span data-stu-id="33823-105">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="33823-106"><xref:System.Linq.Enumerable.Distinct%2A>、<xref:System.Linq.Enumerable.Skip%2A> 和 <xref:System.Linq.Enumerable.Reverse%2A> 就是此类方法的示例。</span><span class="sxs-lookup"><span data-stu-id="33823-106">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>

<span data-ttu-id="33823-107">扩展 <xref:System.Collections.Generic.IEnumerable%601> 接口时，可以将自定义方法应用于任何可枚举集合。</span><span class="sxs-lookup"><span data-stu-id="33823-107">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="33823-108">有关详细信息，请参阅[扩展方法](../../classes-and-structs/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="33823-108">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span>

## <a name="adding-an-aggregate-method"></a><span data-ttu-id="33823-109">添加聚合对象</span><span class="sxs-lookup"><span data-stu-id="33823-109">Adding an Aggregate Method</span></span>

<span data-ttu-id="33823-110">聚合方法可从一组值计算单个值。</span><span class="sxs-lookup"><span data-stu-id="33823-110">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="33823-111">LINQ 提供多个聚合方法，包括 <xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Min%2A> 和 <xref:System.Linq.Enumerable.Max%2A>。</span><span class="sxs-lookup"><span data-stu-id="33823-111">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="33823-112">可以通过向 <xref:System.Collections.Generic.IEnumerable%601> 接口添加扩展方法来创建自己的聚合方法。</span><span class="sxs-lookup"><span data-stu-id="33823-112">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="33823-113">下面的代码示例演示如何创建名为 `Median` 的扩展方法来计算类型为 `double` 的数字序列的中间值。</span><span class="sxs-lookup"><span data-stu-id="33823-113">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>

```csharp
public static class LINQExtension
{
    public static double Median(this IEnumerable<double> source)
    {
        var countOfElementsInTheSet = source?.Count() ?? 0;

        if (countOfElementsInTheSet == 0)
        {
            throw new InvalidOperationException("Cannot compute median for a null or empty set.");
        }

        var sortedList = (from number in source
                         orderby number
                         select number).ToList();

        int itemIndex = countOfElementsInTheSet / 2;

        if (countOfElementsInTheSet % 2 == 0)
        {
            // Even number of items.
            return (sortedList[itemIndex] + sortedList[itemIndex - 1]) / 2;
        }
        else
        {
            // Odd number of items.
            return sortedList[itemIndex];
        }
    }
}
```

<span data-ttu-id="33823-114">使用从 <xref:System.Collections.Generic.IEnumerable%601> 接口调用其他聚合方法的方式为任何可枚举集合调用此扩展方法。</span><span class="sxs-lookup"><span data-stu-id="33823-114">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="33823-115">下面的代码示例说明如何为类型 `double` 的数组使用 `Median` 方法。</span><span class="sxs-lookup"><span data-stu-id="33823-115">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>

```csharp
double[] numbers1 = { 1.9, 2, 8, 4, 5.7, 6, 7.2, 0 };

var query1 = numbers1.Median();

Console.WriteLine("double: Median = " + query1);
```

```csharp
/*
 This code produces the following output:

 Double: Median = 4.85
*/
```

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="33823-116">重载聚合方法以接受各种类型</span><span class="sxs-lookup"><span data-stu-id="33823-116">Overloading an Aggregate Method to Accept Various Types</span></span>

<span data-ttu-id="33823-117">可以重载聚合方法，以便其接受各种类型的序列。</span><span class="sxs-lookup"><span data-stu-id="33823-117">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="33823-118">标准做法是为每种类型都创建一个重载。</span><span class="sxs-lookup"><span data-stu-id="33823-118">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="33823-119">另一种方法是创建一个采用泛型类型的重载，并使用委托将其转换为特定类型。</span><span class="sxs-lookup"><span data-stu-id="33823-119">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="33823-120">还可以将两种方法结合。</span><span class="sxs-lookup"><span data-stu-id="33823-120">You can also combine both approaches.</span></span>

#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="33823-121">为每种类型创建重载</span><span class="sxs-lookup"><span data-stu-id="33823-121">To create an overload for each type</span></span>

<span data-ttu-id="33823-122">可以为要支持的每种类型创建特定重载。</span><span class="sxs-lookup"><span data-stu-id="33823-122">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="33823-123">下面的代码示例演示 `integer` 类型的 `Median` 方法的重载。</span><span class="sxs-lookup"><span data-stu-id="33823-123">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>

```csharp
//int overload

public static double Median(this IEnumerable<int> source)
{
    return (from num in source select (double)num).Median();
}
```

<span data-ttu-id="33823-124">现在便可以为 `integer` 和 `double` 类型调用 `Median` 重载了，如以下代码中所示：</span><span class="sxs-lookup"><span data-stu-id="33823-124">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>

```csharp
double[] numbers1 = { 1.9, 2, 8, 4, 5.7, 6, 7.2, 0 };

var query1 = numbers1.Median();

Console.WriteLine("double: Median = " + query1);
```

```csharp
int[] numbers2 = { 1, 2, 3, 4, 5 };

var query2 = numbers2.Median();

Console.WriteLine("int: Median = " + query2);
```

```csharp
/*
 This code produces the following output:

 Double: Median = 4.85
 Integer: Median = 3
*/
```

#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="33823-125">创建一般重载</span><span class="sxs-lookup"><span data-stu-id="33823-125">To create a generic overload</span></span>

<span data-ttu-id="33823-126">还可以创建接受泛型对象序列的重载。</span><span class="sxs-lookup"><span data-stu-id="33823-126">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="33823-127">此重载采用委托作为参数，并使用该参数将泛型类型的对象序列转换为特定类型。</span><span class="sxs-lookup"><span data-stu-id="33823-127">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>

<span data-ttu-id="33823-128">下面的代码展示 `Median` 方法的重载，该重载将 <xref:System.Func%602> 委托作为参数。</span><span class="sxs-lookup"><span data-stu-id="33823-128">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="33823-129">此委托采用泛型类型 T 的对象，并返回类型 `double` 的对象。</span><span class="sxs-lookup"><span data-stu-id="33823-129">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>

```csharp
// Generic overload.

public static double Median<T>(this IEnumerable<T> numbers,
                       Func<T, double> selector)
{
    return (from num in numbers select selector(num)).Median();
}
```

<span data-ttu-id="33823-130">现在，可以为任何类型的对象序列调用 `Median` 方法。</span><span class="sxs-lookup"><span data-stu-id="33823-130">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="33823-131">如果类型不具有自己的方法重载，必须手动传递委托参数。</span><span class="sxs-lookup"><span data-stu-id="33823-131">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="33823-132">在 C# 中，可以使用 lambda 表达式实现此目的。</span><span class="sxs-lookup"><span data-stu-id="33823-132">In C#, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="33823-133">此外，仅限在 Visual Basic 中，如果使用 `Aggregate` 或 `Group By` 子句而不是方法调用，可以传递此子句范围内的任何值或表达式。</span><span class="sxs-lookup"><span data-stu-id="33823-133">Also, in Visual Basic only, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>

<span data-ttu-id="33823-134">下面的代码示例演示如何为整数数组和字符串数组调用 `Median` 方法。</span><span class="sxs-lookup"><span data-stu-id="33823-134">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="33823-135">对于字符串，将计算数组中字符串长度的中值。</span><span class="sxs-lookup"><span data-stu-id="33823-135">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="33823-136">该示例演示如何将 <xref:System.Func%602> 委托参数传递给每个用例的 `Median` 方法。</span><span class="sxs-lookup"><span data-stu-id="33823-136">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>

```csharp
int[] numbers3 = { 1, 2, 3, 4, 5 };

/*
  You can use the num=>num lambda expression as a parameter for the Median method
  so that the compiler will implicitly convert its value to double.
  If there is no implicit conversion, the compiler will display an error message.
*/

var query3 = numbers3.Median(num => num);

Console.WriteLine("int: Median = " + query3);

string[] numbers4 = { "one", "two", "three", "four", "five" };

// With the generic overload, you can also use numeric properties of objects.

var query4 = numbers4.Median(str => str.Length);

Console.WriteLine("String: Median = " + query4);

/*
 This code produces the following output:

 Integer: Median = 3
 String: Median = 4
*/
```

## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="33823-137">添加返回集合的方法</span><span class="sxs-lookup"><span data-stu-id="33823-137">Adding a Method That Returns a Collection</span></span>

<span data-ttu-id="33823-138">可以使用会返回值序列的自定义查询方法来扩展 <xref:System.Collections.Generic.IEnumerable%601> 接口。</span><span class="sxs-lookup"><span data-stu-id="33823-138">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="33823-139">在这种情况下，该方法必须返回类型 <xref:System.Collections.Generic.IEnumerable%601> 的集合。</span><span class="sxs-lookup"><span data-stu-id="33823-139">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="33823-140">此类方法可用于将筛选器或数据转换应用于值序列。</span><span class="sxs-lookup"><span data-stu-id="33823-140">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>

<span data-ttu-id="33823-141">下面的示例演示如何创建名为 `AlternateElements` 的扩展方法，该方法从集合中第一个元素开始按相隔一个元素的方式返回集合中的元素。</span><span class="sxs-lookup"><span data-stu-id="33823-141">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>

```csharp
// Extension method for the IEnumerable<T> interface.
// The method returns every other element of a sequence.

public static IEnumerable<T> AlternateElements<T>(this IEnumerable<T> source)
{
    List<T> list = new List<T>();

    int i = 0;

    foreach (var element in source)
    {
        if (i % 2 == 0)
        {
            list.Add(element);
        }

        i++;
    }

    return list;
}
```

<span data-ttu-id="33823-142">可使用从 <xref:System.Collections.Generic.IEnumerable%601> 接口调用其他方法的方式对任何可枚举集合调用此扩展方法，如下面的代码中所示：</span><span class="sxs-lookup"><span data-stu-id="33823-142">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>

```csharp
string[] strings = { "a", "b", "c", "d", "e" };

var query = strings.AlternateElements();

foreach (var element in query)
{
    Console.WriteLine(element);
}
/*
 This code produces the following output:

 a
 c
 e
*/
```

## <a name="see-also"></a><span data-ttu-id="33823-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="33823-143">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="33823-144">扩展方法</span><span class="sxs-lookup"><span data-stu-id="33823-144">Extension Methods</span></span>](../../classes-and-structs/extension-methods.md)

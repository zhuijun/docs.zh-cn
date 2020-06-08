---
title: LINQ（语言集成查询）
description: 了解 LINQ 如何向 C# 和 Visual Basic 中提供语言级查询功能和 API，以便能够编写具有表达力度的声明性代码。
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
dev_langs:
- csharp
- vb
ms.technology: dotnet-standard
ms.assetid: c00939e1-59e3-4e61-8fe9-08ad6b3f1295
ms.openlocfilehash: cd0260de3facdd37c46e9fb2f09ddc4cac08e71b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291066"
---
# <a name="linq-language-integrated-query"></a><span data-ttu-id="ffdc4-103">LINQ（语言集成查询）</span><span class="sxs-lookup"><span data-stu-id="ffdc4-103">LINQ (Language Integrated Query)</span></span>

## <a name="what-is-it"></a><span data-ttu-id="ffdc4-104">什么是 LINQ？</span><span class="sxs-lookup"><span data-stu-id="ffdc4-104">What is it?</span></span>

<span data-ttu-id="ffdc4-105">LINQ 在 C# 和 Visual Basic 中提供语言级查询功能和[高阶函数](https://en.wikipedia.org/wiki/Higher-order_function) API，以便能够编写具有很高表达力度的声明性代码。</span><span class="sxs-lookup"><span data-stu-id="ffdc4-105">LINQ provides language-level querying capabilities and a [higher-order function](https://en.wikipedia.org/wiki/Higher-order_function) API to C# and Visual Basic as a way to write expressive, declarative code.</span></span>

<span data-ttu-id="ffdc4-106">语言级查询语法：</span><span class="sxs-lookup"><span data-stu-id="ffdc4-106">Language-level query syntax:</span></span>

```csharp
var linqExperts = from p in programmers
                  where p.IsNewToLINQ
                  select new LINQExpert(p);
```

```vb
Dim linqExperts = From p in programmers
                  Where p.IsNewToLINQ
                  Select New LINQExpert(p)
```

<span data-ttu-id="ffdc4-107">同一个示例使用 `IEnumerable<T>` API 的情况：</span><span class="sxs-lookup"><span data-stu-id="ffdc4-107">Same example using the `IEnumerable<T>` API:</span></span>

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

```vb
Dim linqExperts = programmers.Where(Function(p) p.IsNewToLINQ).
                             Select(Function(p) New LINQExpert(p))
```

## <a name="linq-is-expressive"></a><span data-ttu-id="ffdc4-108">LINQ 具有很高的表达力度</span><span class="sxs-lookup"><span data-stu-id="ffdc4-108">LINQ is Expressive</span></span>

<span data-ttu-id="ffdc4-109">假设你有一份宠物列表，但想要将它转换为字典，以便可以使用宠物的 `RFID` 值直接访问宠物信息。</span><span class="sxs-lookup"><span data-stu-id="ffdc4-109">Imagine you have a list of pets, but want to convert it into a dictionary where you can access a pet directly by its `RFID` value.</span></span>

<span data-ttu-id="ffdc4-110">传统的命令性代码：</span><span class="sxs-lookup"><span data-stu-id="ffdc4-110">Traditional imperative code:</span></span>

```csharp
var petLookup = new Dictionary<int, Pet>();

foreach (var pet in pets)
{
    petLookup.Add(pet.RFID, pet);
}
```

```vb
Dim petLookup = New Dictionary(Of Integer, Pet)()

For Each pet in pets
    petLookup.Add(pet.RFID, pet)
Next
```

<span data-ttu-id="ffdc4-111">代码的意图不是创建新的 `Dictionary<int, Pet>` 并通过循环在其中添加条目，而是将现有列表转换为字典！</span><span class="sxs-lookup"><span data-stu-id="ffdc4-111">The intention behind the code is not to create a new `Dictionary<int, Pet>` and add to it via a loop, it is to convert an existing list into a dictionary!</span></span> <span data-ttu-id="ffdc4-112">LINQ 维持这种意图，而命令性代码则不会。</span><span class="sxs-lookup"><span data-stu-id="ffdc4-112">LINQ preserves the intention whereas the imperative code does not.</span></span>

<span data-ttu-id="ffdc4-113">等效的 LINQ 表达式：</span><span class="sxs-lookup"><span data-stu-id="ffdc4-113">Equivalent LINQ expression:</span></span>

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

```vb
Dim petLookup = pets.ToDictionary(Function(pet) pet.RFID)
```

<span data-ttu-id="ffdc4-114">使用 LINQ 的代码非常有效，因为在程序员的推理过程中，LINQ 能够在意图与代码之间找到合理的平衡。</span><span class="sxs-lookup"><span data-stu-id="ffdc4-114">The code using LINQ is valuable because it evens the playing field between intent and code when reasoning as a programmer.</span></span> <span data-ttu-id="ffdc4-115">另一个好处就是精简代码。</span><span class="sxs-lookup"><span data-stu-id="ffdc4-115">Another bonus is code brevity.</span></span> <span data-ttu-id="ffdc4-116">想像一下，如果能够像上面一样将大部分的基本代码减掉 1/3，情况会怎样？</span><span class="sxs-lookup"><span data-stu-id="ffdc4-116">Imagine reducing large portions of a codebase by 1/3 as done above.</span></span> <span data-ttu-id="ffdc4-117">很爽，对吧？</span><span class="sxs-lookup"><span data-stu-id="ffdc4-117">Pretty sweet deal, right?</span></span>

## <a name="linq-providers-simplify-data-access"></a><span data-ttu-id="ffdc4-118">LINQ 提供程序简化数据访问</span><span class="sxs-lookup"><span data-stu-id="ffdc4-118">LINQ Providers Simplify Data Access</span></span>

<span data-ttu-id="ffdc4-119">对于生产环境中的软件，其重要功能块的任务不外乎就是来自某些源（数据库、JSON、XML 等）的数据。</span><span class="sxs-lookup"><span data-stu-id="ffdc4-119">For a significant chunk of software out in the wild, everything revolves around dealing with data from some source (Databases, JSON, XML, etc).</span></span> <span data-ttu-id="ffdc4-120">通常，这就需要用户学习每个数据源的新 API，而这是一个枯燥的过程。</span><span class="sxs-lookup"><span data-stu-id="ffdc4-120">Often this involves learning a new API for each data source, which can be annoying.</span></span> <span data-ttu-id="ffdc4-121">LINQ 可将用于数据访问的常用元素抽象化成查询语法，不过你选择哪种数据源，这种语法看上去都是相同的，因而简化了此任务。</span><span class="sxs-lookup"><span data-stu-id="ffdc4-121">LINQ simplifies this by abstracting common elements of data access into a query syntax which looks the same no matter which data source you pick.</span></span>

<span data-ttu-id="ffdc4-122">考虑以下操作：查找具有特定属性值的所有 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="ffdc4-122">Consider the following: finding all XML elements with a specific attribute value.</span></span>

```csharp
public static IEnumerable<XElement> FindAllElementsWithAttribute(XElement documentRoot, string elementName,
                                           string attributeName, string value)
{
    return from el in documentRoot.Elements(elementName)
           where (string)el.Element(attributeName) == value
           select el;
}
```

```vb
Public Shared Function FindAllElementsWithAttribute(documentRoot As XElement, elementName As String,
                                           attributeName As String, value As String) As IEnumerable(Of XElement)
    Return From el In documentRoot.Elements(elementName)
           Where el.Element(attributeName).ToString() = value
           Select el
End Function

```

<span data-ttu-id="ffdc4-123">为了执行此任务而编写代码来手动遍历 XML 文档会带来重重困难。</span><span class="sxs-lookup"><span data-stu-id="ffdc4-123">Writing code to manually traverse the XML document to perform this task would be far more challenging.</span></span>

<span data-ttu-id="ffdc4-124">LINQ 提供程序的作用不仅仅是与 XML 交互。</span><span class="sxs-lookup"><span data-stu-id="ffdc4-124">Interacting with XML isn’t the only thing you can do with LINQ Providers.</span></span> <span data-ttu-id="ffdc4-125">[Linq to SQL](../framework/data/adonet/sql/linq/index.md) 是适用于 MSSQL Server 数据库的极其简练的对象关系映射器 (ORM)。</span><span class="sxs-lookup"><span data-stu-id="ffdc4-125">[Linq to SQL](../framework/data/adonet/sql/linq/index.md) is a fairly bare-bones Object-Relational Mapper (ORM) for an MSSQL Server Database.</span></span> <span data-ttu-id="ffdc4-126">使用 [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) 库可以通过 LINQ 有效遍历 JSON 文档。</span><span class="sxs-lookup"><span data-stu-id="ffdc4-126">The [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) library provides efficient JSON Document traversal via LINQ.</span></span> <span data-ttu-id="ffdc4-127">此外，如果没有哪个库可以解决你的需要，你还可以[编写自己的 LINQ 提供程序](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))！</span><span class="sxs-lookup"><span data-stu-id="ffdc4-127">Furthermore, if there isn’t a library which does what you need, you can also [write your own LINQ Provider](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))!</span></span>

## <a name="why-use-the-query-syntax"></a><span data-ttu-id="ffdc4-128">为何使用查询语法？</span><span class="sxs-lookup"><span data-stu-id="ffdc4-128">Why Use the Query Syntax?</span></span>

<span data-ttu-id="ffdc4-129">这是用户经常提出的一个问题。</span><span class="sxs-lookup"><span data-stu-id="ffdc4-129">This is a question which often comes up.</span></span> <span data-ttu-id="ffdc4-130">毕竟，下面的代码</span><span class="sxs-lookup"><span data-stu-id="ffdc4-130">After all, this,</span></span>

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

```vb
Dim filteredItems = myItems.Where(Function(item) item.Foo)
```

<span data-ttu-id="ffdc4-131">要比下面的代码简洁得多：</span><span class="sxs-lookup"><span data-stu-id="ffdc4-131">is a lot more concise than this:</span></span>

```csharp
var filteredItems = from item in myItems
                    where item.Foo
                    select item;
```

```vb
Dim filteredItems = From item In myItems
                    Where item.Foo
                    Select item
```

<span data-ttu-id="ffdc4-132">难道 API 语法不比查询语法更简洁吗？</span><span class="sxs-lookup"><span data-stu-id="ffdc4-132">Isn’t the API syntax just a more concise way to do the query syntax?</span></span>

<span data-ttu-id="ffdc4-133">否。</span><span class="sxs-lookup"><span data-stu-id="ffdc4-133">No.</span></span> <span data-ttu-id="ffdc4-134">查询语法允许使用 let 子句，这样，便可以在表达式的作用域内引入和绑定变量，然后在表达式的后续片段中使用该变量  。</span><span class="sxs-lookup"><span data-stu-id="ffdc4-134">The query syntax allows for the use of the **let** clause, which allows you to introduce and bind a variable within the scope of the expression, using it in subsequent pieces of the expression.</span></span> <span data-ttu-id="ffdc4-135">只使用 API 语法重现相同的代码也是可行的，不过，这很可能会导致代码难以阅读。</span><span class="sxs-lookup"><span data-stu-id="ffdc4-135">Reproducing the same code with only the API syntax can be done, but will most likely lead to code which is hard to read.</span></span>

<span data-ttu-id="ffdc4-136">那么，问题来了，**只使用查询语法可以吗？**</span><span class="sxs-lookup"><span data-stu-id="ffdc4-136">So this begs the question, **should you just use the query syntax?**</span></span>

<span data-ttu-id="ffdc4-137">在以下情况下，此问题的答案是**可以**...</span><span class="sxs-lookup"><span data-stu-id="ffdc4-137">The answer to this question is **yes** if...</span></span>

* <span data-ttu-id="ffdc4-138">现有的基本代码已使用查询语法</span><span class="sxs-lookup"><span data-stu-id="ffdc4-138">Your existing codebase already uses the query syntax</span></span>
* <span data-ttu-id="ffdc4-139">由于复杂性的问题，需要在查询中限定变量的作用域</span><span class="sxs-lookup"><span data-stu-id="ffdc4-139">You need to scope variables within your queries due to complexity</span></span>
* <span data-ttu-id="ffdc4-140">你偏好使用查询语法，并且它不会使基本代码变得混乱</span><span class="sxs-lookup"><span data-stu-id="ffdc4-140">You prefer the query syntax and it won’t distract from your codebase</span></span>

<span data-ttu-id="ffdc4-141">在以下情况下，此问题的答案是**不可以**...</span><span class="sxs-lookup"><span data-stu-id="ffdc4-141">The answer to this question is **no** if...</span></span>

* <span data-ttu-id="ffdc4-142">现有的基本代码已使用 API 语法</span><span class="sxs-lookup"><span data-stu-id="ffdc4-142">Your existing codebase already uses the API syntax</span></span>
* <span data-ttu-id="ffdc4-143">不需要在查询中限定变量的作用域</span><span class="sxs-lookup"><span data-stu-id="ffdc4-143">You have no need to scope variables within your queries</span></span>
* <span data-ttu-id="ffdc4-144">你偏好使用 API 语法，并且它不会使基本代码变得混乱</span><span class="sxs-lookup"><span data-stu-id="ffdc4-144">You prefer the API syntax and it won’t distract from your codebase</span></span>

## <a name="essential-samples"></a><span data-ttu-id="ffdc4-145">重要片段示例</span><span class="sxs-lookup"><span data-stu-id="ffdc4-145">Essential Samples</span></span>

<span data-ttu-id="ffdc4-146">有关 LINQ 示例的完整列表，请访问 [101 个 LINQ 示例](https://docs.microsoft.com/samples/dotnet/try-samples/101-linq-samples/)。</span><span class="sxs-lookup"><span data-stu-id="ffdc4-146">For a truly comprehensive list of LINQ samples, visit [101 LINQ Samples](https://docs.microsoft.com/samples/dotnet/try-samples/101-linq-samples/).</span></span>

<span data-ttu-id="ffdc4-147">下面简单演示了 LINQ 的一些重要片段。</span><span class="sxs-lookup"><span data-stu-id="ffdc4-147">The following is a quick demonstration of some of the essential pieces of LINQ.</span></span> <span data-ttu-id="ffdc4-148">没有办法演示完整的代码，因为 LINQ 提供的功能比此处演示的要多得多。</span><span class="sxs-lookup"><span data-stu-id="ffdc4-148">This is in no way comprehensive, as LINQ provides significantly more functionality than what is showcased here.</span></span>

* <span data-ttu-id="ffdc4-149">语句构成 - `Where`、`Select` 和 `Aggregate`：</span><span class="sxs-lookup"><span data-stu-id="ffdc4-149">The bread and butter - `Where`, `Select`, and `Aggregate`:</span></span>

```csharp
// Filtering a list.
var germanShepards = dogs.Where(dog => dog.Breed == DogBreed.GermanShepard);

// Using the query syntax.
var queryGermanShepards = from dog in dogs
                          where dog.Breed == DogBreed.GermanShepard
                          select dog;

// Mapping a list from type A to type B.
var cats = dogs.Select(dog => dog.TurnIntoACat());

// Using the query syntax.
var queryCats = from dog in dogs
                select dog.TurnIntoACat();

// Summing the lengths of a set of strings.
int seed = 0;
int sumOfStrings = strings.Aggregate(seed, (s1, s2) => s1.Length + s2.Length);
```

```vb
' Filtering a list.
Dim germanShepards = dogs.Where(Function(dog) dog.Breed = DogBreed.GermanShepard)

' Using the query syntax.
Dim queryGermanShepards = From dog In dogs
                          Where dog.Breed = DogBreed.GermanShepard
                          Select dog

' Mapping a list from type A to type B.
Dim cats = dogs.Select(Function(dog) dog.TurnIntoACat())

' Using the query syntax.
Dim queryCats = From dog In dogs
                Select dog.TurnIntoACat()

' Summing the lengths of a set of strings.
Dim seed As Integer = 0
Dim sumOfStrings As Integer = strings.Aggregate(seed, Function(s1, s2) s1.Length + s2.Length)
```

* <span data-ttu-id="ffdc4-150">平展列表的列表：</span><span class="sxs-lookup"><span data-stu-id="ffdc4-150">Flattening a list of lists:</span></span>

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

```vb
' Transforms the list of kennels into a list of all their dogs.
Dim allDogsFromKennels = kennels.SelectMany(Function(kennel) kennel.Dogs)
```

* <span data-ttu-id="ffdc4-151">两个集之间的联合（使用自定义比较运算符）：</span><span class="sxs-lookup"><span data-stu-id="ffdc4-151">Union between two sets (with custom comparator):</span></span>

```csharp
public class DogHairLengthComparer : IEqualityComparer<Dog>
{
    public bool Equals(Dog a, Dog b)
    {
        if (a == null && b == null)
        {
            return true;
        }
        else if ((a == null && b != null) ||
                 (a != null && b == null))
        {
            return false;
        }
        else
        {
            return a.HairLengthType == b.HairLengthType;
        }
    }

    public int GetHashCode(Dog d)
    {
        // Default hashcode is enough here, as these are simple objects.
        return d.GetHashCode();
    }
}

...

// Gets all the short-haired dogs between two different kennels.
var allShortHairedDogs = kennel1.Dogs.Union(kennel2.Dogs, new DogHairLengthComparer());
```

```vb
Public Class DogHairLengthComparer
  Inherits IEqualityComparer(Of Dog)

  Public Function Equals(a As Dog,b As Dog) As Boolean
      If a Is Nothing AndAlso b Is Nothing Then
          Return True
      ElseIf (a Is Nothing AndAlso b IsNot Nothing) OrElse (a IsNot Nothing AndAlso b Is Nothing) Then
          Return False
      Else
          Return a.HairLengthType = b.HairLengthType
      End If
  End Function

  Public Function GetHashCode(d As Dog) As Integer
      ' Default hashcode is enough here, as these are simple objects.
      Return d.GetHashCode()
  End Function
End Class

...

' Gets all the short-haired dogs between two different kennels.
Dim allShortHairedDogs = kennel1.Dogs.Union(kennel2.Dogs, New DogHairLengthComparer())
```

* <span data-ttu-id="ffdc4-152">两个集之间的交集：</span><span class="sxs-lookup"><span data-stu-id="ffdc4-152">Intersection between two sets:</span></span>

```csharp
// Gets the volunteers who spend share time with two humane societies.
var volunteers = humaneSociety1.Volunteers.Intersect(humaneSociety2.Volunteers,
                                                     new VolunteerTimeComparer());
```

```vb
' Gets the volunteers who spend share time with two humane societies.
Dim volunteers = humaneSociety1.Volunteers.Intersect(humaneSociety2.Volunteers,
                                                     New VolunteerTimeComparer())
```

* <span data-ttu-id="ffdc4-153">排序：</span><span class="sxs-lookup"><span data-stu-id="ffdc4-153">Ordering:</span></span>

```csharp
// Get driving directions, ordering by if it's toll-free before estimated driving time.
var results = DirectionsProcessor.GetDirections(start, end)
              .OrderBy(direction => direction.HasNoTolls)
              .ThenBy(direction => direction.EstimatedTime);
```

```vb
' Get driving directions, ordering by if it's toll-free before estimated driving time.
Dim results = DirectionsProcessor.GetDirections(start, end).
                OrderBy(Function(direction) direction.HasNoTolls).
                ThenBy(Function(direction) direction.EstimatedTime)
```

* <span data-ttu-id="ffdc4-154">最后，我们演示一个更高级的示例：确定相同类型的两个实例的属性值是否相等（该示例摘自[此 StackOverflow 文章](https://stackoverflow.com/a/844855)，不过已做修改）：</span><span class="sxs-lookup"><span data-stu-id="ffdc4-154">Finally, a more advanced sample: determining if the values of the properties of two instances of the same type are equal (Borrowed and modified from [this StackOverflow post](https://stackoverflow.com/a/844855)):</span></span>

```csharp
public static bool PublicInstancePropertiesEqual<T>(this T self, T to, params string[] ignore) where T : class
{
    if (self == null || to == null)
    {
        return self == to;
    }

    // Selects the properties which have unequal values into a sequence of those properties.
    var unequalProperties = from property in typeof(T).GetProperties(BindingFlags.Public | BindingFlags.Instance)
                            where !ignore.Contains(property.Name)
                            let selfValue = property.GetValue(self, null)
                            let toValue = property.GetValue(to, null)
                            where !Equals(selfValue, toValue)
                            select property;
    return !unequalProperties.Any();
}
```

```vb
<System.Runtime.CompilerServices.Extension()>
Public Function PublicInstancePropertiesEqual(Of T As Class)(self As T, [to] As T, ParamArray ignore As String()) As Boolean
    If self Is Nothing OrElse [to] Is Nothing Then
        Return self Is [to]
    End If

    ' Selects the properties which have unequal values into a sequence of those properties.
    Dim unequalProperties = From [property] In GetType(T).GetProperties(BindingFlags.Public Or BindingFlags.Instance)
                            Where Not ignore.Contains([property].Name)
                            Let selfValue = [property].GetValue(self, Nothing)
                            Let toValue = [property].GetValue([to], Nothing)
                            Where Not Equals(selfValue, toValue) Select [property]
    Return Not unequalProperties.Any()
End Function
```

## <a name="plinq"></a><span data-ttu-id="ffdc4-155">PLINQ</span><span class="sxs-lookup"><span data-stu-id="ffdc4-155">PLINQ</span></span>

<span data-ttu-id="ffdc4-156">PLINQ（又称并行 LINQ）是 LINQ 表达式的并行执行引擎。</span><span class="sxs-lookup"><span data-stu-id="ffdc4-156">PLINQ, or Parallel LINQ, is a parallel execution engine for LINQ expressions.</span></span> <span data-ttu-id="ffdc4-157">换言之，LINQ 正则表达式可能会没有意义地在任意数量的线程之间并行化。</span><span class="sxs-lookup"><span data-stu-id="ffdc4-157">In other words, a regular LINQ expression can be trivially parallelized across any number of threads.</span></span> <span data-ttu-id="ffdc4-158">为此，可以调用表达式前面的 `AsParallel()`。</span><span class="sxs-lookup"><span data-stu-id="ffdc4-158">This is accomplished via a call to `AsParallel()` preceding the expression.</span></span>

<span data-ttu-id="ffdc4-159">请考虑下列各项：</span><span class="sxs-lookup"><span data-stu-id="ffdc4-159">Consider the following:</span></span>

```csharp
public static string GetAllFacebookUserLikesMessage(IEnumerable<FacebookUser> facebookUsers)
{
    var seed = default(UInt64);

    Func<UInt64, UInt64, UInt64> threadAccumulator = (t1, t2) => t1 + t2;
    Func<UInt64, UInt64, UInt64> threadResultAccumulator = (t1, t2) => t1 + t2;
    Func<Uint64, string> resultSelector = total => $"Facebook has {total} likes!";

    return facebookUsers.AsParallel()
                        .Aggregate(seed, threadAccumulator, threadResultAccumulator, resultSelector);
}
```

```vb
Public Shared GetAllFacebookUserLikesMessage(facebookUsers As IEnumerable(Of FacebookUser)) As String
{
    Dim seed As UInt64 = 0

    Dim threadAccumulator As Func(Of UInt64, UInt64, UInt64) = Function(t1, t2) t1 + t2
    Dim threadResultAccumulator As Func(Of UInt64, UInt64, UInt64) = Function(t1, t2) t1 + t2
    Dim resultSelector As Func(Of Uint64, string) = Function(total) $"Facebook has {total} likes!"

    Return facebookUsers.AsParallel().
                        Aggregate(seed, threadAccumulator, threadResultAccumulator, resultSelector)
}
```

<span data-ttu-id="ffdc4-160">此代码将会根据需要在系统线程之间将 `facebookUsers` 分区，累加每个并行线程上的类似项总计，累加每个线程计算的结果，然后将该结果投影为一个合理的字符串。</span><span class="sxs-lookup"><span data-stu-id="ffdc4-160">This code will partition `facebookUsers` across system threads as necessary, sum up the total likes on each thread in parallel, sum the results computed by each thread, and project that result into a nice string.</span></span>

<span data-ttu-id="ffdc4-161">图示：</span><span class="sxs-lookup"><span data-stu-id="ffdc4-161">In diagram form:</span></span>

![PLINQ 图示](./media/using-linq/plinq-diagram.png)

<span data-ttu-id="ffdc4-163">可通过 LINQ 能够轻松表达的可并行化 CPU 密集型作业（即，没有副作用的纯函数）非常适合使用 PLINQ 来处理。</span><span class="sxs-lookup"><span data-stu-id="ffdc4-163">Parallelizable CPU-bound jobs which can be easily expressed via LINQ (in other words, are pure functions and have no side effects) are a great candidate for PLINQ.</span></span> <span data-ttu-id="ffdc4-164">对于_确实_有副作用的作业，请考虑使用[任务并行库](./parallel-programming/task-parallel-library-tpl.md)。</span><span class="sxs-lookup"><span data-stu-id="ffdc4-164">For jobs which _do_ have a side effect, consider using the [Task Parallel Library](./parallel-programming/task-parallel-library-tpl.md).</span></span>

## <a name="further-resources"></a><span data-ttu-id="ffdc4-165">其他资源：</span><span class="sxs-lookup"><span data-stu-id="ffdc4-165">Further Resources:</span></span>

* [<span data-ttu-id="ffdc4-166">101 LINQ 示例</span><span class="sxs-lookup"><span data-stu-id="ffdc4-166">101 LINQ Samples</span></span>](https://docs.microsoft.com/samples/dotnet/try-samples/101-linq-samples/)
* <span data-ttu-id="ffdc4-167">[Linqpad](https://www.linqpad.net/)，适用于 C#/F#/Visual Basic 的演练环境和数据库查询引擎</span><span class="sxs-lookup"><span data-stu-id="ffdc4-167">[Linqpad](https://www.linqpad.net/), a playground environment and Database querying engine for C#/F#/Visual Basic</span></span>
* <span data-ttu-id="ffdc4-168">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/)，帮助用户了解如何实现 LINQ 到对象的电子书</span><span class="sxs-lookup"><span data-stu-id="ffdc4-168">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), an e-book for learning how LINQ-to-objects is implemented</span></span>

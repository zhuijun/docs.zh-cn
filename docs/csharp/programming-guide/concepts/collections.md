---
title: 集合 (C#)
ms.date: 07/20/2015
ms.assetid: 317d7dc3-8587-4873-8b3e-556f86497939
ms.openlocfilehash: ecab30d50be58f810246e58e637b331d492e4a47
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241391"
---
# <a name="collections-c"></a><span data-ttu-id="ffb45-102">集合 (C#)</span><span class="sxs-lookup"><span data-stu-id="ffb45-102">Collections (C#)</span></span>

<span data-ttu-id="ffb45-103">对于许多应用程序，你会想要创建和管理相关对象的组。</span><span class="sxs-lookup"><span data-stu-id="ffb45-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="ffb45-104">有两种方法对对象进行分组：通过创建对象的数组，以及通过创建对象的集合。</span><span class="sxs-lookup"><span data-stu-id="ffb45-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>

<span data-ttu-id="ffb45-105">数组最适用于创建和使用固定数量的强类型化对象。</span><span class="sxs-lookup"><span data-stu-id="ffb45-105">Arrays are most useful for creating and working with a fixed number of strongly typed objects.</span></span> <span data-ttu-id="ffb45-106">有关数组的信息，请参阅[数组](../arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="ffb45-106">For information about arrays, see [Arrays](../arrays/index.md).</span></span>

<span data-ttu-id="ffb45-107">集合提供更灵活的方式来使用对象组。</span><span class="sxs-lookup"><span data-stu-id="ffb45-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="ffb45-108">与数组不同，你使用的对象组随着应用程序更改的需要动态地放大和缩小。</span><span class="sxs-lookup"><span data-stu-id="ffb45-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="ffb45-109">对于某些集合，你可以为放入集合中的任何对象分配一个密钥，这样你便可以使用该密钥快速检索此对象。</span><span class="sxs-lookup"><span data-stu-id="ffb45-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>

<span data-ttu-id="ffb45-110">集合是一个类，因此必须在向该集合添加元素之前，声明类的实例。</span><span class="sxs-lookup"><span data-stu-id="ffb45-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>

<span data-ttu-id="ffb45-111">如果集合中只包含一种数据类型的元素，则可以使用 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空间中的一个类。</span><span class="sxs-lookup"><span data-stu-id="ffb45-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="ffb45-112">泛型集合强制类型安全，因此无法向其添加任何其他数据类型。</span><span class="sxs-lookup"><span data-stu-id="ffb45-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="ffb45-113">当你从泛型集合检索元素时，你无需确定其数据类型或对其进行转换。</span><span class="sxs-lookup"><span data-stu-id="ffb45-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>

> [!NOTE]
> <span data-ttu-id="ffb45-114">在本主题的示例中，针对 `System.Collections.Generic` 和 `System.Linq` 命名空间包括 [using](../../language-reference/keywords/using-directive.md) 指令。</span><span class="sxs-lookup"><span data-stu-id="ffb45-114">For the examples in this topic, include [using](../../language-reference/keywords/using-directive.md) directives for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>

 <span data-ttu-id="ffb45-115">**在本主题中**</span><span class="sxs-lookup"><span data-stu-id="ffb45-115">**In this topic**</span></span>

- [<span data-ttu-id="ffb45-116">使用简单集合</span><span class="sxs-lookup"><span data-stu-id="ffb45-116">Using a Simple Collection</span></span>](#BKMK_SimpleCollection)

- [<span data-ttu-id="ffb45-117">集合的类型</span><span class="sxs-lookup"><span data-stu-id="ffb45-117">Kinds of Collections</span></span>](#BKMK_KindsOfCollections)

  - [<span data-ttu-id="ffb45-118">System.Collections.Generic 类</span><span class="sxs-lookup"><span data-stu-id="ffb45-118">System.Collections.Generic Classes</span></span>](#BKMK_Generic)

  - [<span data-ttu-id="ffb45-119">System.Collections.Concurrent 类</span><span class="sxs-lookup"><span data-stu-id="ffb45-119">System.Collections.Concurrent Classes</span></span>](#BKMK_Concurrent)

  - [<span data-ttu-id="ffb45-120">System.Collections 类</span><span class="sxs-lookup"><span data-stu-id="ffb45-120">System.Collections Classes</span></span>](#BKMK_Collections)

- [<span data-ttu-id="ffb45-121">实现键/值对集合</span><span class="sxs-lookup"><span data-stu-id="ffb45-121">Implementing a Collection of Key/Value Pairs</span></span>](#BKMK_KeyValuePairs)

- [<span data-ttu-id="ffb45-122">使用 LINQ 访问集合</span><span class="sxs-lookup"><span data-stu-id="ffb45-122">Using LINQ to Access a Collection</span></span>](#BKMK_LINQ)

- [<span data-ttu-id="ffb45-123">对集合排序</span><span class="sxs-lookup"><span data-stu-id="ffb45-123">Sorting a Collection</span></span>](#BKMK_Sorting)

- [<span data-ttu-id="ffb45-124">定义自定义集合</span><span class="sxs-lookup"><span data-stu-id="ffb45-124">Defining a Custom Collection</span></span>](#BKMK_CustomCollection)

- [<span data-ttu-id="ffb45-125">迭代器</span><span class="sxs-lookup"><span data-stu-id="ffb45-125">Iterators</span></span>](#BKMK_Iterators)

<a name="BKMK_SimpleCollection"></a>

## <a name="using-a-simple-collection"></a><span data-ttu-id="ffb45-126">使用简单集合</span><span class="sxs-lookup"><span data-stu-id="ffb45-126">Using a Simple Collection</span></span>

<span data-ttu-id="ffb45-127">本部分中的示例使用泛型 <xref:System.Collections.Generic.List%601> 类，通过此类可使用对象的强类型列表。</span><span class="sxs-lookup"><span data-stu-id="ffb45-127">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>

<span data-ttu-id="ffb45-128">以下示例创建字符串列表，并通过使用 [foreach](../../language-reference/keywords/foreach-in.md) 语句循环访问字符串。</span><span class="sxs-lookup"><span data-stu-id="ffb45-128">The following example creates a list of strings and then iterates through the strings by using a [foreach](../../language-reference/keywords/foreach-in.md) statement.</span></span>

```csharp
// Create a list of strings.
var salmons = new List<string>();
salmons.Add("chinook");
salmons.Add("coho");
salmons.Add("pink");
salmons.Add("sockeye");

// Iterate through the list.
foreach (var salmon in salmons)
{
    Console.Write(salmon + " ");
}
// Output: chinook coho pink sockeye
```

<span data-ttu-id="ffb45-129">如果集合中的内容是事先已知的，则可以使用集合初始值设定项来初始化集合。</span><span class="sxs-lookup"><span data-stu-id="ffb45-129">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="ffb45-130">有关详细信息，请参阅[对象和集合初始值设定项](../classes-and-structs/object-and-collection-initializers.md)。</span><span class="sxs-lookup"><span data-stu-id="ffb45-130">For more information, see [Object and Collection Initializers](../classes-and-structs/object-and-collection-initializers.md).</span></span>

<span data-ttu-id="ffb45-131">以下示例与上一示例相同，除了有一个集合初始值设定项用于将元素添加到集合。</span><span class="sxs-lookup"><span data-stu-id="ffb45-131">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>

```csharp
// Create a list of strings by using a
// collection initializer.
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };

// Iterate through the list.
foreach (var salmon in salmons)
{
    Console.Write(salmon + " ");
}
// Output: chinook coho pink sockeye
```

<span data-ttu-id="ffb45-132">可以使用 [for](../../language-reference/keywords/for.md) 语句，而不是 `foreach` 语句来循环访问集合。</span><span class="sxs-lookup"><span data-stu-id="ffb45-132">You can use a [for](../../language-reference/keywords/for.md) statement instead of a `foreach` statement to iterate through a collection.</span></span> <span data-ttu-id="ffb45-133">通过按索引位置访问集合元素实现此目的。</span><span class="sxs-lookup"><span data-stu-id="ffb45-133">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="ffb45-134">元素的索引开始于 0，结束于元素计数减 1。</span><span class="sxs-lookup"><span data-stu-id="ffb45-134">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>

<span data-ttu-id="ffb45-135">以下示例通过使用 `for` 而不是 `foreach` 循环访问集合中的元素。</span><span class="sxs-lookup"><span data-stu-id="ffb45-135">The following example iterates through the elements of a collection by using `for` instead of `foreach`.</span></span>

```csharp
// Create a list of strings by using a
// collection initializer.
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };

for (var index = 0; index < salmons.Count; index++)
{
    Console.Write(salmons[index] + " ");
}
// Output: chinook coho pink sockeye
```

<span data-ttu-id="ffb45-136">以下示例通过指定要删除的对象，从集合中删除一个元素。</span><span class="sxs-lookup"><span data-stu-id="ffb45-136">The following example removes an element from the collection by specifying the object to remove.</span></span>

```csharp
// Create a list of strings by using a
// collection initializer.
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };

// Remove an element from the list by specifying
// the object.
salmons.Remove("coho");

// Iterate through the list.
foreach (var salmon in salmons)
{
    Console.Write(salmon + " ");
}
// Output: chinook pink sockeye
```

<span data-ttu-id="ffb45-137">以下示例从一个泛型列表中删除元素。</span><span class="sxs-lookup"><span data-stu-id="ffb45-137">The following example removes elements from a generic list.</span></span> <span data-ttu-id="ffb45-138">使用以降序进行循环访问的 [for](../../language-reference/keywords/for.md) 语句，而非 `foreach` 语句。</span><span class="sxs-lookup"><span data-stu-id="ffb45-138">Instead of a `foreach` statement, a [for](../../language-reference/keywords/for.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="ffb45-139">这是因为 <xref:System.Collections.Generic.List%601.RemoveAt%2A> 方法将导致已移除的元素后的元素的索引值减小。</span><span class="sxs-lookup"><span data-stu-id="ffb45-139">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>

```csharp
var numbers = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };

// Remove odd numbers.
for (var index = numbers.Count - 1; index >= 0; index--)
{
    if (numbers[index] % 2 == 1)
    {
        // Remove the element by specifying
        // the zero-based index in the list.
        numbers.RemoveAt(index);
    }
}

// Iterate through the list.
// A lambda expression is placed in the ForEach method
// of the List(T) object.
numbers.ForEach(
    number => Console.Write(number + " "));
// Output: 0 2 4 6 8
```

<span data-ttu-id="ffb45-140">对于 <xref:System.Collections.Generic.List%601> 中的元素类型，还可以定义自己的类。</span><span class="sxs-lookup"><span data-stu-id="ffb45-140">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="ffb45-141">在下面的示例中，由 <xref:System.Collections.Generic.List%601> 使用的 `Galaxy` 类在代码中定义。</span><span class="sxs-lookup"><span data-stu-id="ffb45-141">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>

```csharp
private static void IterateThroughList()
{
    var theGalaxies = new List<Galaxy>
        {
            new Galaxy() { Name="Tadpole", MegaLightYears=400},
            new Galaxy() { Name="Pinwheel", MegaLightYears=25},
            new Galaxy() { Name="Milky Way", MegaLightYears=0},
            new Galaxy() { Name="Andromeda", MegaLightYears=3}
        };

    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears);
    }

    // Output:
    //  Tadpole  400
    //  Pinwheel  25
    //  Milky Way  0
    //  Andromeda  3
}

public class Galaxy
{
    public string Name { get; set; }
    public int MegaLightYears { get; set; }
}
```

<a name="BKMK_KindsOfCollections"></a>

## <a name="kinds-of-collections"></a><span data-ttu-id="ffb45-142">集合的类型</span><span class="sxs-lookup"><span data-stu-id="ffb45-142">Kinds of Collections</span></span>

<span data-ttu-id="ffb45-143">许多通用集合由 .NET 提供。</span><span class="sxs-lookup"><span data-stu-id="ffb45-143">Many common collections are provided by .NET.</span></span> <span data-ttu-id="ffb45-144">每种类型的集合用于特定的用途。</span><span class="sxs-lookup"><span data-stu-id="ffb45-144">Each type of collection is designed for a specific purpose.</span></span>

<span data-ttu-id="ffb45-145">本部分介绍了一些通用集合类：</span><span class="sxs-lookup"><span data-stu-id="ffb45-145">Some of the common collection classes are described in this section:</span></span>

- <span data-ttu-id="ffb45-146"><xref:System.Collections.Generic> 类</span><span class="sxs-lookup"><span data-stu-id="ffb45-146"><xref:System.Collections.Generic> classes</span></span>

- <span data-ttu-id="ffb45-147"><xref:System.Collections.Concurrent> 类</span><span class="sxs-lookup"><span data-stu-id="ffb45-147"><xref:System.Collections.Concurrent> classes</span></span>

- <span data-ttu-id="ffb45-148"><xref:System.Collections> 类</span><span class="sxs-lookup"><span data-stu-id="ffb45-148"><xref:System.Collections> classes</span></span>

<a name="BKMK_Generic"></a>

### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="ffb45-149">System.Collections.Generic 类</span><span class="sxs-lookup"><span data-stu-id="ffb45-149">System.Collections.Generic Classes</span></span>

<span data-ttu-id="ffb45-150">可以使用 <xref:System.Collections.Generic> 命名空间中的某个类来创建泛型集合。</span><span class="sxs-lookup"><span data-stu-id="ffb45-150">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="ffb45-151">当集合中的所有项都具有相同的数据类型时，泛型集合会非常有用。</span><span class="sxs-lookup"><span data-stu-id="ffb45-151">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="ffb45-152">泛型集合通过仅允许添加所需的数据类型，强制实施强类型化。</span><span class="sxs-lookup"><span data-stu-id="ffb45-152">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>

<span data-ttu-id="ffb45-153">下表列出了 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空间中的一些常用类：</span><span class="sxs-lookup"><span data-stu-id="ffb45-153">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="ffb45-154">类</span><span class="sxs-lookup"><span data-stu-id="ffb45-154">Class</span></span>|<span data-ttu-id="ffb45-155">描述</span><span class="sxs-lookup"><span data-stu-id="ffb45-155">Description</span></span>|
|---|---|
|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="ffb45-156">表示基于键进行组织的键/值对的集合。</span><span class="sxs-lookup"><span data-stu-id="ffb45-156">Represents a collection of key/value pairs that are organized based on the key.</span></span>|
|<xref:System.Collections.Generic.List%601>|<span data-ttu-id="ffb45-157">表示可按索引访问的对象的列表。</span><span class="sxs-lookup"><span data-stu-id="ffb45-157">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="ffb45-158">提供用于对列表进行搜索、排序和修改的方法。</span><span class="sxs-lookup"><span data-stu-id="ffb45-158">Provides methods to search, sort, and modify lists.</span></span>|
|<xref:System.Collections.Generic.Queue%601>|<span data-ttu-id="ffb45-159">表示对象的先进先出 (FIFO) 集合。</span><span class="sxs-lookup"><span data-stu-id="ffb45-159">Represents a first in, first out (FIFO) collection of objects.</span></span>|
|<xref:System.Collections.Generic.SortedList%602>|<span data-ttu-id="ffb45-160">表示基于相关的 <xref:System.Collections.Generic.IComparer%601> 实现按键进行排序的键/值对的集合。</span><span class="sxs-lookup"><span data-stu-id="ffb45-160">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|
|<xref:System.Collections.Generic.Stack%601>|<span data-ttu-id="ffb45-161">表示对象的后进先出 (LIFO) 集合。</span><span class="sxs-lookup"><span data-stu-id="ffb45-161">Represents a last in, first out (LIFO) collection of objects.</span></span>|

<span data-ttu-id="ffb45-162">有关其他信息，请参阅[常用集合类型](../../../standard/collections/commonly-used-collection-types.md)、[选择集合类](../../../standard/collections/selecting-a-collection-class.md)和 <xref:System.Collections.Generic>。</span><span class="sxs-lookup"><span data-stu-id="ffb45-162">For additional information, see [Commonly Used Collection Types](../../../standard/collections/commonly-used-collection-types.md), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic>.</span></span>

<a name="BKMK_Concurrent"></a>

### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="ffb45-163">System.Collections.Concurrent 类</span><span class="sxs-lookup"><span data-stu-id="ffb45-163">System.Collections.Concurrent Classes</span></span>

<span data-ttu-id="ffb45-164">在 .NET Framework 4 以及更新的版本中，<xref:System.Collections.Concurrent> 命名空间中的集合可提供高效的线程安全操作，以便从多个线程访问集合项。</span><span class="sxs-lookup"><span data-stu-id="ffb45-164">In .NET Framework 4 and later versions, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>

<span data-ttu-id="ffb45-165">只要多个线程同时访问集合，就应使用 <xref:System.Collections.Concurrent> 命名空间中的类，而不是 <xref:System.Collections.Generic?displayProperty=nameWithType> 和 <xref:System.Collections?displayProperty=nameWithType> 命名空间中的相应类型。</span><span class="sxs-lookup"><span data-stu-id="ffb45-165">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=nameWithType> and <xref:System.Collections?displayProperty=nameWithType> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="ffb45-166">有关详细信息，请参阅[线程安全集合](../../../standard/collections/thread-safe/index.md)和 <xref:System.Collections.Concurrent>。</span><span class="sxs-lookup"><span data-stu-id="ffb45-166">For more information, see [Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span></span>

<span data-ttu-id="ffb45-167">包含在 <xref:System.Collections.Concurrent> 命名空间中的一些类为 <xref:System.Collections.Concurrent.BlockingCollection%601>、<xref:System.Collections.Concurrent.ConcurrentDictionary%602>、<xref:System.Collections.Concurrent.ConcurrentQueue%601> 和 <xref:System.Collections.Concurrent.ConcurrentStack%601>。</span><span class="sxs-lookup"><span data-stu-id="ffb45-167">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>

<a name="BKMK_Collections"></a>

### <a name="systemcollections-classes"></a><span data-ttu-id="ffb45-168">System.Collections 类</span><span class="sxs-lookup"><span data-stu-id="ffb45-168">System.Collections Classes</span></span>

<span data-ttu-id="ffb45-169"><xref:System.Collections?displayProperty=nameWithType> 命名空间中的类不会将元素作为特别类型化的对象存储，而是作为 `Object` 类型的对象存储。</span><span class="sxs-lookup"><span data-stu-id="ffb45-169">The classes in the <xref:System.Collections?displayProperty=nameWithType> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>

<span data-ttu-id="ffb45-170">只要可能，则应使用 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空间或 <xref:System.Collections.Concurrent> 命名空间中的泛型集合，而不是 `System.Collections` 命名空间中的旧类型。</span><span class="sxs-lookup"><span data-stu-id="ffb45-170">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>

<span data-ttu-id="ffb45-171">下表列出了 `System.Collections` 命名空间中的一些常用类：</span><span class="sxs-lookup"><span data-stu-id="ffb45-171">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>

|<span data-ttu-id="ffb45-172">类</span><span class="sxs-lookup"><span data-stu-id="ffb45-172">Class</span></span>|<span data-ttu-id="ffb45-173">描述</span><span class="sxs-lookup"><span data-stu-id="ffb45-173">Description</span></span>|
|---|---|
|<xref:System.Collections.ArrayList>|<span data-ttu-id="ffb45-174">表示对象的数组，这些对象的大小会根据需要动态增加。</span><span class="sxs-lookup"><span data-stu-id="ffb45-174">Represents an array of objects whose size is dynamically increased as required.</span></span>|
|<xref:System.Collections.Hashtable>|<span data-ttu-id="ffb45-175">表示根据键的哈希代码进行组织的键/值对的集合。</span><span class="sxs-lookup"><span data-stu-id="ffb45-175">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|
|<xref:System.Collections.Queue>|<span data-ttu-id="ffb45-176">表示对象的先进先出 (FIFO) 集合。</span><span class="sxs-lookup"><span data-stu-id="ffb45-176">Represents a first in, first out (FIFO) collection of objects.</span></span>|
|<xref:System.Collections.Stack>|<span data-ttu-id="ffb45-177">表示对象的后进先出 (LIFO) 集合。</span><span class="sxs-lookup"><span data-stu-id="ffb45-177">Represents a last in, first out (LIFO) collection of objects.</span></span>|

<span data-ttu-id="ffb45-178"><xref:System.Collections.Specialized> 命名空间提供专门类型化以及强类型化的集合类，例如只包含字符串的集合以及链接列表和混合字典。</span><span class="sxs-lookup"><span data-stu-id="ffb45-178">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>

<a name="BKMK_KeyValuePairs"></a>

## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="ffb45-179">实现键/值对集合</span><span class="sxs-lookup"><span data-stu-id="ffb45-179">Implementing a Collection of Key/Value Pairs</span></span>

<span data-ttu-id="ffb45-180"><xref:System.Collections.Generic.Dictionary%602> 泛型集合可通过每个元素的键访问集合中的元素。</span><span class="sxs-lookup"><span data-stu-id="ffb45-180">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="ffb45-181">每次对字典的添加都包含一个值和与其关联的键。</span><span class="sxs-lookup"><span data-stu-id="ffb45-181">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="ffb45-182">通过使用键来检索值十分快捷，因为 `Dictionary` 类实现为哈希表。</span><span class="sxs-lookup"><span data-stu-id="ffb45-182">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>

<span data-ttu-id="ffb45-183">以下示例创建 `Dictionary` 集合并通过使用 `foreach` 语句循环访问字典。</span><span class="sxs-lookup"><span data-stu-id="ffb45-183">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `foreach` statement.</span></span>

```csharp
private static void IterateThruDictionary()
{
    Dictionary<string, Element> elements = BuildDictionary();

    foreach (KeyValuePair<string, Element> kvp in elements)
    {
        Element theElement = kvp.Value;

        Console.WriteLine("key: " + kvp.Key);
        Console.WriteLine("values: " + theElement.Symbol + " " +
            theElement.Name + " " + theElement.AtomicNumber);
    }
}

private static Dictionary<string, Element> BuildDictionary()
{
    var elements = new Dictionary<string, Element>();

    AddToDictionary(elements, "K", "Potassium", 19);
    AddToDictionary(elements, "Ca", "Calcium", 20);
    AddToDictionary(elements, "Sc", "Scandium", 21);
    AddToDictionary(elements, "Ti", "Titanium", 22);

    return elements;
}

private static void AddToDictionary(Dictionary<string, Element> elements,
    string symbol, string name, int atomicNumber)
{
    Element theElement = new Element();

    theElement.Symbol = symbol;
    theElement.Name = name;
    theElement.AtomicNumber = atomicNumber;

    elements.Add(key: theElement.Symbol, value: theElement);
}

public class Element
{
    public string Symbol { get; set; }
    public string Name { get; set; }
    public int AtomicNumber { get; set; }
}
```

<span data-ttu-id="ffb45-184">若要转而使用集合初始值设定项生成 `Dictionary` 集合，可使用以下方法替换 `BuildDictionary` 和 `AddToDictionary`。</span><span class="sxs-lookup"><span data-stu-id="ffb45-184">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>

```csharp
private static Dictionary<string, Element> BuildDictionary2()
{
    return new Dictionary<string, Element>
    {
        {"K",
            new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},
        {"Ca",
            new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},
        {"Sc",
            new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},
        {"Ti",
            new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}
    };
}
```

<span data-ttu-id="ffb45-185">以下示例使用 <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> 方法和 `Dictionary` 的 <xref:System.Collections.Generic.Dictionary%602.Item%2A> 属性按键快速查找某个项。</span><span class="sxs-lookup"><span data-stu-id="ffb45-185">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="ffb45-186">使用 `Item` 属性可通过 C# 中的 `elements[symbol]` 来访问 `elements` 集合中的项。</span><span class="sxs-lookup"><span data-stu-id="ffb45-186">The `Item` property enables you to access an item in the `elements` collection by using the `elements[symbol]` in C#.</span></span>

```csharp
private static void FindInDictionary(string symbol)
{
    Dictionary<string, Element> elements = BuildDictionary();

    if (elements.ContainsKey(symbol) == false)
    {
        Console.WriteLine(symbol + " not found");
    }
    else
    {
        Element theElement = elements[symbol];
        Console.WriteLine("found: " + theElement.Name);
    }
}
```

<span data-ttu-id="ffb45-187">以下示例则使用 <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> 方法按键快速查找某个项。</span><span class="sxs-lookup"><span data-stu-id="ffb45-187">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>

```csharp
private static void FindInDictionary2(string symbol)
{
    Dictionary<string, Element> elements = BuildDictionary();

    Element theElement = null;
    if (elements.TryGetValue(symbol, out theElement) == false)
        Console.WriteLine(symbol + " not found");
    else
        Console.WriteLine("found: " + theElement.Name);
}
```

<a name="BKMK_LINQ"></a>

## <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="ffb45-188">使用 LINQ 访问集合</span><span class="sxs-lookup"><span data-stu-id="ffb45-188">Using LINQ to Access a Collection</span></span>

<span data-ttu-id="ffb45-189">可以使用 LINQ（语言集成查询）来访问集合。</span><span class="sxs-lookup"><span data-stu-id="ffb45-189">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="ffb45-190">LINQ 查询提供筛选、排序和分组功能。</span><span class="sxs-lookup"><span data-stu-id="ffb45-190">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="ffb45-191">有关详细信息，请参阅 [C# 中的 LINQ 入门](linq/index.md)。</span><span class="sxs-lookup"><span data-stu-id="ffb45-191">For more information, see [Getting Started with LINQ in C#](linq/index.md).</span></span>

<span data-ttu-id="ffb45-192">以下示例运行一个对泛型 `List` 的 LINQ 查询。</span><span class="sxs-lookup"><span data-stu-id="ffb45-192">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="ffb45-193">LINQ 查询返回一个包含结果的不同集合。</span><span class="sxs-lookup"><span data-stu-id="ffb45-193">The LINQ query returns a different collection that contains the results.</span></span>

```csharp
private static void ShowLINQ()
{
    List<Element> elements = BuildList();

    // LINQ Query.
    var subset = from theElement in elements
                 where theElement.AtomicNumber < 22
                 orderby theElement.Name
                 select theElement;

    foreach (Element theElement in subset)
    {
        Console.WriteLine(theElement.Name + " " + theElement.AtomicNumber);
    }

    // Output:
    //  Calcium 20
    //  Potassium 19
    //  Scandium 21
}

private static List<Element> BuildList()
{
    return new List<Element>
    {
        { new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},
        { new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},
        { new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},
        { new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}
    };
}

public class Element
{
    public string Symbol { get; set; }
    public string Name { get; set; }
    public int AtomicNumber { get; set; }
}
```

<a name="BKMK_Sorting"></a>

## <a name="sorting-a-collection"></a><span data-ttu-id="ffb45-194">对集合排序</span><span class="sxs-lookup"><span data-stu-id="ffb45-194">Sorting a Collection</span></span>

<span data-ttu-id="ffb45-195">以下示例阐释了对集合排序的过程。</span><span class="sxs-lookup"><span data-stu-id="ffb45-195">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="ffb45-196">该示例对 <xref:System.Collections.Generic.List%601> 中存储的 `Car` 类的实例进行排序。</span><span class="sxs-lookup"><span data-stu-id="ffb45-196">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="ffb45-197">`Car` 类实现 <xref:System.IComparable%601> 接口，此操作需要实现 <xref:System.IComparable%601.CompareTo%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="ffb45-197">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>

<span data-ttu-id="ffb45-198">每次对 <xref:System.IComparable%601.CompareTo%2A> 方法的调用均会执行用于排序的单一比较。</span><span class="sxs-lookup"><span data-stu-id="ffb45-198">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="ffb45-199">`CompareTo` 方法中用户编写的代码针对当前对象与另一个对象的每个比较返回一个值。</span><span class="sxs-lookup"><span data-stu-id="ffb45-199">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="ffb45-200">如果当前对象小于另一个对象，则返回的值小于零；如果当前对象大于另一个对象，则返回的值大于零；如果当前对象等于另一个对象，则返回的值等于零。</span><span class="sxs-lookup"><span data-stu-id="ffb45-200">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="ffb45-201">这使你可以在代码中定义大于、小于和等于条件。</span><span class="sxs-lookup"><span data-stu-id="ffb45-201">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>

<span data-ttu-id="ffb45-202">在 `ListCars` 方法中，`cars.Sort()` 语句对列表进行排序。</span><span class="sxs-lookup"><span data-stu-id="ffb45-202">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="ffb45-203">对 <xref:System.Collections.Generic.List%601> 的 <xref:System.Collections.Generic.List%601.Sort%2A> 方法的此调用将导致为 `List` 中的 `Car` 对象自动调用 `CompareTo` 方法。</span><span class="sxs-lookup"><span data-stu-id="ffb45-203">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>

```csharp
private static void ListCars()
{
    var cars = new List<Car>
    {
        { new Car() { Name = "car1", Color = "blue", Speed = 20}},
        { new Car() { Name = "car2", Color = "red", Speed = 50}},
        { new Car() { Name = "car3", Color = "green", Speed = 10}},
        { new Car() { Name = "car4", Color = "blue", Speed = 50}},
        { new Car() { Name = "car5", Color = "blue", Speed = 30}},
        { new Car() { Name = "car6", Color = "red", Speed = 60}},
        { new Car() { Name = "car7", Color = "green", Speed = 50}}
    };

    // Sort the cars by color alphabetically, and then by speed
    // in descending order.
    cars.Sort();

    // View all of the cars.
    foreach (Car thisCar in cars)
    {
        Console.Write(thisCar.Color.PadRight(5) + " ");
        Console.Write(thisCar.Speed.ToString() + " ");
        Console.Write(thisCar.Name);
        Console.WriteLine();
    }

    // Output:
    //  blue  50 car4
    //  blue  30 car5
    //  blue  20 car1
    //  green 50 car7
    //  green 10 car3
    //  red   60 car6
    //  red   50 car2
}

public class Car : IComparable<Car>
{
    public string Name { get; set; }
    public int Speed { get; set; }
    public string Color { get; set; }

    public int CompareTo(Car other)
    {
        // A call to this method makes a single comparison that is
        // used for sorting.

        // Determine the relative order of the objects being compared.
        // Sort by color alphabetically, and then by speed in
        // descending order.

        // Compare the colors.
        int compare;
        compare = String.Compare(this.Color, other.Color, true);

        // If the colors are the same, compare the speeds.
        if (compare == 0)
        {
            compare = this.Speed.CompareTo(other.Speed);

            // Use descending order for speed.
            compare = -compare;
        }

        return compare;
    }
}
```

<a name="BKMK_CustomCollection"></a>

## <a name="defining-a-custom-collection"></a><span data-ttu-id="ffb45-204">定义自定义集合</span><span class="sxs-lookup"><span data-stu-id="ffb45-204">Defining a Custom Collection</span></span>

<span data-ttu-id="ffb45-205">可以通过实现 <xref:System.Collections.Generic.IEnumerable%601> 或 <xref:System.Collections.IEnumerable> 接口来定义集合。</span><span class="sxs-lookup"><span data-stu-id="ffb45-205">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span>

<span data-ttu-id="ffb45-206">尽管可以定义自定义集合，但通常最好使用包含在 .NET 中的集合，这在本文前面的[集合类型](#BKMK_KindsOfCollections)中进行了介绍。</span><span class="sxs-lookup"><span data-stu-id="ffb45-206">Although you can define a custom collection, it is usually better to instead use the collections that are included in .NET, which are described in [Kinds of Collections](#BKMK_KindsOfCollections) earlier in this article.</span></span>

<span data-ttu-id="ffb45-207">以下示例定义一个名为 `AllColors` 的自定义集合类。</span><span class="sxs-lookup"><span data-stu-id="ffb45-207">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="ffb45-208">此类实现 <xref:System.Collections.IEnumerable> 接口，此操作需要实现 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="ffb45-208">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>

<span data-ttu-id="ffb45-209">`GetEnumerator` 方法返回 `ColorEnumerator` 类的一个实例。</span><span class="sxs-lookup"><span data-stu-id="ffb45-209">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="ffb45-210">`ColorEnumerator` 实现 <xref:System.Collections.IEnumerator> 接口，此操作需要实现 <xref:System.Collections.IEnumerator.Current%2A> 属性、<xref:System.Collections.IEnumerator.MoveNext%2A> 方法以及 <xref:System.Collections.IEnumerator.Reset%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="ffb45-210">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>

```csharp
private static void ListColors()
{
    var colors = new AllColors();

    foreach (Color theColor in colors)
    {
        Console.Write(theColor.Name + " ");
    }
    Console.WriteLine();
    // Output: red blue green
}

// Collection class.
public class AllColors : System.Collections.IEnumerable
{
    Color[] _colors =
    {
        new Color() { Name = "red" },
        new Color() { Name = "blue" },
        new Color() { Name = "green" }
    };

    public System.Collections.IEnumerator GetEnumerator()
    {
        return new ColorEnumerator(_colors);

        // Instead of creating a custom enumerator, you could
        // use the GetEnumerator of the array.
        //return _colors.GetEnumerator();
    }

    // Custom enumerator.
    private class ColorEnumerator : System.Collections.IEnumerator
    {
        private Color[] _colors;
        private int _position = -1;

        public ColorEnumerator(Color[] colors)
        {
            _colors = colors;
        }

        object System.Collections.IEnumerator.Current
        {
            get
            {
                return _colors[_position];
            }
        }

        bool System.Collections.IEnumerator.MoveNext()
        {
            _position++;
            return (_position < _colors.Length);
        }

        void System.Collections.IEnumerator.Reset()
        {
            _position = -1;
        }
    }
}

// Element class.
public class Color
{
    public string Name { get; set; }
}
```

<a name="BKMK_Iterators"></a>

## <a name="iterators"></a><span data-ttu-id="ffb45-211">迭代器</span><span class="sxs-lookup"><span data-stu-id="ffb45-211">Iterators</span></span>

<span data-ttu-id="ffb45-212">迭代器用于对集合执行自定义迭代。</span><span class="sxs-lookup"><span data-stu-id="ffb45-212">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="ffb45-213">迭代器可以是一种方法，或是一个 `get` 访问器。</span><span class="sxs-lookup"><span data-stu-id="ffb45-213">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="ffb45-214">迭代器使用 [yield return](../../language-reference/keywords/yield.md) 语句返回集合的每一个元素，每次返回一个元素。</span><span class="sxs-lookup"><span data-stu-id="ffb45-214">An iterator uses a [yield return](../../language-reference/keywords/yield.md) statement to return each element of the collection one at a time.</span></span>

<span data-ttu-id="ffb45-215">通过使用 [foreach](../../language-reference/keywords/foreach-in.md) 语句调用迭代器。</span><span class="sxs-lookup"><span data-stu-id="ffb45-215">You call an iterator by using a [foreach](../../language-reference/keywords/foreach-in.md) statement.</span></span> <span data-ttu-id="ffb45-216">`foreach` 循环的每次迭代都会调用迭代器。</span><span class="sxs-lookup"><span data-stu-id="ffb45-216">Each iteration of the `foreach` loop calls the iterator.</span></span> <span data-ttu-id="ffb45-217">迭代器中到达 `yield return` 语句时，会返回一个表达式，并保留当前在代码中的位置。</span><span class="sxs-lookup"><span data-stu-id="ffb45-217">When a `yield return` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="ffb45-218">下次调用迭代器时，将从该位置重新开始执行。</span><span class="sxs-lookup"><span data-stu-id="ffb45-218">Execution is restarted from that location the next time that the iterator is called.</span></span>

<span data-ttu-id="ffb45-219">有关详细信息，请参阅[迭代器 (C#)](./iterators.md)。</span><span class="sxs-lookup"><span data-stu-id="ffb45-219">For more information, see [Iterators (C#)](./iterators.md).</span></span>

<span data-ttu-id="ffb45-220">下面的示例使用迭代器方法。</span><span class="sxs-lookup"><span data-stu-id="ffb45-220">The following example uses an iterator method.</span></span> <span data-ttu-id="ffb45-221">迭代器方法具有位于 [for](../../language-reference/keywords/for.md) 循环中的 `yield return` 语句。</span><span class="sxs-lookup"><span data-stu-id="ffb45-221">The iterator method has a `yield return` statement that is inside a [for](../../language-reference/keywords/for.md) loop.</span></span> <span data-ttu-id="ffb45-222">在 `ListEvenNumbers` 方法中，`foreach` 语句体的每次迭代都会创建对迭代器方法的调用，并将继续到下一个 `yield return` 语句。</span><span class="sxs-lookup"><span data-stu-id="ffb45-222">In the `ListEvenNumbers` method, each iteration of the `foreach` statement body creates a call to the iterator method, which proceeds to the next `yield return` statement.</span></span>

```csharp
private static void ListEvenNumbers()
{
    foreach (int number in EvenSequence(5, 18))
    {
        Console.Write(number.ToString() + " ");
    }
    Console.WriteLine();
    // Output: 6 8 10 12 14 16 18
}

private static IEnumerable<int> EvenSequence(
    int firstNumber, int lastNumber)
{
    // Yield even numbers in the range.
    for (var number = firstNumber; number <= lastNumber; number++)
    {
        if (number % 2 == 0)
        {
            yield return number;
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="ffb45-223">请参阅</span><span class="sxs-lookup"><span data-stu-id="ffb45-223">See also</span></span>

- [<span data-ttu-id="ffb45-224">对象和集合初始值设定项</span><span class="sxs-lookup"><span data-stu-id="ffb45-224">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)
- [<span data-ttu-id="ffb45-225">编程概念 (C#)</span><span class="sxs-lookup"><span data-stu-id="ffb45-225">Programming Concepts (C#)</span></span>](./index.md)
- [<span data-ttu-id="ffb45-226">Option Strict 语句</span><span class="sxs-lookup"><span data-stu-id="ffb45-226">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="ffb45-227">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="ffb45-227">LINQ to Objects (C#)</span></span>](./linq/linq-to-objects.md)
- [<span data-ttu-id="ffb45-228">并行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="ffb45-228">Parallel LINQ (PLINQ)</span></span>](../../../standard/parallel-programming/introduction-to-plinq.md)
- [<span data-ttu-id="ffb45-229">集合和数据结构</span><span class="sxs-lookup"><span data-stu-id="ffb45-229">Collections and Data Structures</span></span>](../../../standard/collections/index.md)
- [<span data-ttu-id="ffb45-230">选择集合类</span><span class="sxs-lookup"><span data-stu-id="ffb45-230">Selecting a Collection Class</span></span>](../../../standard/collections/selecting-a-collection-class.md)
- [<span data-ttu-id="ffb45-231">集合内的比较和排序</span><span class="sxs-lookup"><span data-stu-id="ffb45-231">Comparisons and Sorts Within Collections</span></span>](../../../standard/collections/comparisons-and-sorts-within-collections.md)
- [<span data-ttu-id="ffb45-232">何时使用泛型集合</span><span class="sxs-lookup"><span data-stu-id="ffb45-232">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)

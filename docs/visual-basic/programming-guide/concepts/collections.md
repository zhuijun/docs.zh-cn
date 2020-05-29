---
title: 集合
ms.date: 07/20/2015
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
ms.openlocfilehash: d27761ba7a955d1dc8843ad168a82a9c9c27a6f6
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202449"
---
# <a name="collections-visual-basic"></a><span data-ttu-id="4de75-102">集合 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4de75-102">Collections (Visual Basic)</span></span>

<span data-ttu-id="4de75-103">对于许多应用程序，你会想要创建和管理相关对象的组。</span><span class="sxs-lookup"><span data-stu-id="4de75-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="4de75-104">有两种方法对对象进行分组：通过创建对象的数组，以及通过创建对象的集合。</span><span class="sxs-lookup"><span data-stu-id="4de75-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>

<span data-ttu-id="4de75-105">数组最适用于创建和使用固定数量的强类型化对象。</span><span class="sxs-lookup"><span data-stu-id="4de75-105">Arrays are most useful for creating and working with a fixed number of strongly typed objects.</span></span> <span data-ttu-id="4de75-106">有关数组的信息，请参阅[数组](../../../visual-basic/programming-guide/language-features/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="4de75-106">For information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>

<span data-ttu-id="4de75-107">集合提供更灵活的方式来使用对象组。</span><span class="sxs-lookup"><span data-stu-id="4de75-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="4de75-108">与数组不同，你使用的对象组随着应用程序更改的需要动态地放大和缩小。</span><span class="sxs-lookup"><span data-stu-id="4de75-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="4de75-109">对于某些集合，你可以为放入集合中的任何对象分配一个密钥，这样你便可以使用该密钥快速检索此对象。</span><span class="sxs-lookup"><span data-stu-id="4de75-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>

<span data-ttu-id="4de75-110">集合是一个类，因此必须在向该集合添加元素之前，声明类的实例。</span><span class="sxs-lookup"><span data-stu-id="4de75-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>

<span data-ttu-id="4de75-111">如果集合中只包含一种数据类型的元素，则可以使用 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空间中的一个类。</span><span class="sxs-lookup"><span data-stu-id="4de75-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="4de75-112">泛型集合强制类型安全，因此无法向其添加任何其他数据类型。</span><span class="sxs-lookup"><span data-stu-id="4de75-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="4de75-113">当你从泛型集合检索元素时，你无需确定其数据类型或对其进行转换。</span><span class="sxs-lookup"><span data-stu-id="4de75-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>

> [!NOTE]
> <span data-ttu-id="4de75-114">对于本主题中的示例，包括[Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)用于 `System.Collections.Generic` 和命名空间的 Imports 语句 `System.Linq` 。</span><span class="sxs-lookup"><span data-stu-id="4de75-114">For the examples in this topic, include [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>

<a name="BKMK_SimpleCollection"></a>

## <a name="using-a-simple-collection"></a><span data-ttu-id="4de75-115">使用简单集合</span><span class="sxs-lookup"><span data-stu-id="4de75-115">Using a Simple Collection</span></span>

<span data-ttu-id="4de75-116">本部分中的示例使用泛型 <xref:System.Collections.Generic.List%601> 类，通过此类可使用对象的强类型列表。</span><span class="sxs-lookup"><span data-stu-id="4de75-116">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>

<span data-ttu-id="4de75-117">下面的示例创建一个字符串列表，然后使用[For Each .。。下一](../../../visual-basic/language-reference/statements/for-each-next-statement.md)语句。</span><span class="sxs-lookup"><span data-stu-id="4de75-117">The following example creates a list of strings and then iterates through the strings by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span>

```vb
' Create a list of strings.
Dim salmons As New List(Of String)
salmons.Add("chinook")
salmons.Add("coho")
salmons.Add("pink")
salmons.Add("sockeye")

' Iterate through the list.
For Each salmon As String In salmons
    Console.Write(salmon & " ")
Next
'Output: chinook coho pink sockeye
```

<span data-ttu-id="4de75-118">如果集合中的内容是事先已知的，则可以使用集合初始值设定项\*\* 来初始化集合。</span><span class="sxs-lookup"><span data-stu-id="4de75-118">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="4de75-119">有关详细信息，请参阅[集合初始值设定项](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="4de75-119">For more information, see [Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span></span>

<span data-ttu-id="4de75-120">以下示例与上一示例相同，除了有一个集合初始值设定项用于将元素添加到集合。</span><span class="sxs-lookup"><span data-stu-id="4de75-120">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>

```vb
' Create a list of strings by using a
' collection initializer.
Dim salmons As New List(Of String) From
    {"chinook", "coho", "pink", "sockeye"}

For Each salmon As String In salmons
    Console.Write(salmon & " ")
Next
'Output: chinook coho pink sockeye
```

<span data-ttu-id="4de75-121">你可以使用[For .。。Next](../../../visual-basic/language-reference/statements/for-next-statement.md)语句，而不是 `For Each` 语句来循环访问集合。</span><span class="sxs-lookup"><span data-stu-id="4de75-121">You can use a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement instead of a `For Each` statement to iterate through a collection.</span></span> <span data-ttu-id="4de75-122">通过按索引位置访问集合元素实现此目的。</span><span class="sxs-lookup"><span data-stu-id="4de75-122">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="4de75-123">元素的索引开始于 0，结束于元素计数减 1。</span><span class="sxs-lookup"><span data-stu-id="4de75-123">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>

<span data-ttu-id="4de75-124">以下示例通过使用 `For…Next` 而不是 `For Each` 循环访问集合中的元素。</span><span class="sxs-lookup"><span data-stu-id="4de75-124">The following example iterates through the elements of a collection by using `For…Next` instead of `For Each`.</span></span>

```vb
Dim salmons As New List(Of String) From
    {"chinook", "coho", "pink", "sockeye"}

For index = 0 To salmons.Count - 1
    Console.Write(salmons(index) & " ")
Next
'Output: chinook coho pink sockeye
```

<span data-ttu-id="4de75-125">以下示例通过指定要删除的对象，从集合中删除一个元素。</span><span class="sxs-lookup"><span data-stu-id="4de75-125">The following example removes an element from the collection by specifying the object to remove.</span></span>

```vb
' Create a list of strings by using a
' collection initializer.
Dim salmons As New List(Of String) From
    {"chinook", "coho", "pink", "sockeye"}

' Remove an element in the list by specifying
' the object.
salmons.Remove("coho")

For Each salmon As String In salmons
    Console.Write(salmon & " ")
Next
'Output: chinook pink sockeye
```

<span data-ttu-id="4de75-126">以下示例从一个泛型列表中删除元素。</span><span class="sxs-lookup"><span data-stu-id="4de75-126">The following example removes elements from a generic list.</span></span> <span data-ttu-id="4de75-127">而不是 `For Each` 语句， [For .。。使用下一个](../../../visual-basic/language-reference/statements/for-next-statement.md)循环访问顺序的语句。</span><span class="sxs-lookup"><span data-stu-id="4de75-127">Instead of a `For Each` statement, a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="4de75-128">这是因为 <xref:System.Collections.Generic.List%601.RemoveAt%2A> 方法将导致已移除的元素后的元素的索引值减小。</span><span class="sxs-lookup"><span data-stu-id="4de75-128">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>

```vb
Dim numbers As New List(Of Integer) From
    {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}

' Remove odd numbers.
For index As Integer = numbers.Count - 1 To 0 Step -1
    If numbers(index) Mod 2 = 1 Then
        ' Remove the element by specifying
        ' the zero-based index in the list.
        numbers.RemoveAt(index)
    End If
Next

' Iterate through the list.
' A lambda expression is placed in the ForEach method
' of the List(T) object.
numbers.ForEach(
    Sub(number) Console.Write(number & " "))
' Output: 0 2 4 6 8
```

<span data-ttu-id="4de75-129">对于 <xref:System.Collections.Generic.List%601> 中的元素类型，还可以定义自己的类。</span><span class="sxs-lookup"><span data-stu-id="4de75-129">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="4de75-130">在下面的示例中，由 <xref:System.Collections.Generic.List%601> 使用的 `Galaxy` 类在代码中定义。</span><span class="sxs-lookup"><span data-stu-id="4de75-130">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>

```vb
Private Sub IterateThroughList()
    Dim theGalaxies As New List(Of Galaxy) From
        {
            New Galaxy With {.Name = "Tadpole", .MegaLightYears = 400},
            New Galaxy With {.Name = "Pinwheel", .MegaLightYears = 25},
            New Galaxy With {.Name = "Milky Way", .MegaLightYears = 0},
            New Galaxy With {.Name = "Andromeda", .MegaLightYears = 3}
        }

    For Each theGalaxy In theGalaxies
        With theGalaxy
            Console.WriteLine(.Name & "  " & .MegaLightYears)
        End With
    Next

    ' Output:
    '  Tadpole  400
    '  Pinwheel  25
    '  Milky Way  0
    '  Andromeda  3
End Sub

Public Class Galaxy
    Public Property Name As String
    Public Property MegaLightYears As Integer
End Class
```

<a name="BKMK_KindsOfCollections"></a>

## <a name="kinds-of-collections"></a><span data-ttu-id="4de75-131">集合的类型</span><span class="sxs-lookup"><span data-stu-id="4de75-131">Kinds of Collections</span></span>

<span data-ttu-id="4de75-132">许多通用集合由 .NET Framework 提供。</span><span class="sxs-lookup"><span data-stu-id="4de75-132">Many common collections are provided by the .NET Framework.</span></span> <span data-ttu-id="4de75-133">每种类型的集合用于特定的用途。</span><span class="sxs-lookup"><span data-stu-id="4de75-133">Each type of collection is designed for a specific purpose.</span></span>

<span data-ttu-id="4de75-134">本部分介绍了一些通用集合类：</span><span class="sxs-lookup"><span data-stu-id="4de75-134">Some of the common collection classes are described in this section:</span></span>

- <span data-ttu-id="4de75-135"><xref:System.Collections.Generic> 类</span><span class="sxs-lookup"><span data-stu-id="4de75-135"><xref:System.Collections.Generic> classes</span></span>

- <span data-ttu-id="4de75-136"><xref:System.Collections.Concurrent> 类</span><span class="sxs-lookup"><span data-stu-id="4de75-136"><xref:System.Collections.Concurrent> classes</span></span>

- <span data-ttu-id="4de75-137"><xref:System.Collections> 类</span><span class="sxs-lookup"><span data-stu-id="4de75-137"><xref:System.Collections> classes</span></span>

- <span data-ttu-id="4de75-138">Visual Basic `Collection` 类</span><span class="sxs-lookup"><span data-stu-id="4de75-138">Visual Basic `Collection` class</span></span>

<a name="BKMK_Generic"></a>

### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="4de75-139">System.Collections.Generic 类</span><span class="sxs-lookup"><span data-stu-id="4de75-139">System.Collections.Generic Classes</span></span>

<span data-ttu-id="4de75-140">可以使用 <xref:System.Collections.Generic> 命名空间中的某个类来创建泛型集合。</span><span class="sxs-lookup"><span data-stu-id="4de75-140">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="4de75-141">当集合中的所有项都具有相同的数据类型时，泛型集合会非常有用。</span><span class="sxs-lookup"><span data-stu-id="4de75-141">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="4de75-142">泛型集合通过仅允许添加所需的数据类型，强制实施强类型化。</span><span class="sxs-lookup"><span data-stu-id="4de75-142">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>

<span data-ttu-id="4de75-143">下表列出了 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空间中的一些常用类：</span><span class="sxs-lookup"><span data-stu-id="4de75-143">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="4de75-144">类</span><span class="sxs-lookup"><span data-stu-id="4de75-144">Class</span></span>|<span data-ttu-id="4de75-145">说明</span><span class="sxs-lookup"><span data-stu-id="4de75-145">Description</span></span>|
|---|---|
|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="4de75-146">表示基于键进行组织的键/值对的集合。</span><span class="sxs-lookup"><span data-stu-id="4de75-146">Represents a collection of key/value pairs that are organized based on the key.</span></span>|
|<xref:System.Collections.Generic.List%601>|<span data-ttu-id="4de75-147">表示可按索引访问的对象的列表。</span><span class="sxs-lookup"><span data-stu-id="4de75-147">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="4de75-148">提供用于对列表进行搜索、排序和修改的方法。</span><span class="sxs-lookup"><span data-stu-id="4de75-148">Provides methods to search, sort, and modify lists.</span></span>|
|<xref:System.Collections.Generic.Queue%601>|<span data-ttu-id="4de75-149">表示对象的先进先出 (FIFO) 集合。</span><span class="sxs-lookup"><span data-stu-id="4de75-149">Represents a first in, first out (FIFO) collection of objects.</span></span>|
|<xref:System.Collections.Generic.SortedList%602>|<span data-ttu-id="4de75-150">表示基于相关的 <xref:System.Collections.Generic.IComparer%601> 实现按键进行排序的键/值对的集合。</span><span class="sxs-lookup"><span data-stu-id="4de75-150">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|
|<xref:System.Collections.Generic.Stack%601>|<span data-ttu-id="4de75-151">表示对象的后进先出 (LIFO) 集合。</span><span class="sxs-lookup"><span data-stu-id="4de75-151">Represents a last in, first out (LIFO) collection of objects.</span></span>|

<span data-ttu-id="4de75-152">有关其他信息，请参阅[常用集合类型](../../../standard/collections/commonly-used-collection-types.md)、[选择集合类](../../../standard/collections/selecting-a-collection-class.md)和 <xref:System.Collections.Generic?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="4de75-152">For additional information, see [Commonly Used Collection Types](../../../standard/collections/commonly-used-collection-types.md), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic?displayProperty=nameWithType>.</span></span>

<a name="BKMK_Concurrent"></a>

### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="4de75-153">System.Collections.Concurrent 类</span><span class="sxs-lookup"><span data-stu-id="4de75-153">System.Collections.Concurrent Classes</span></span>

<span data-ttu-id="4de75-154">在 .NET Framework 4 或更新的版本中，<xref:System.Collections.Concurrent> 命名空间中的集合可提供高效的线程安全操作，以便从多个线程访问集合项。</span><span class="sxs-lookup"><span data-stu-id="4de75-154">In the .NET Framework 4 or newer, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>

<span data-ttu-id="4de75-155">只要多个线程同时访问集合，就应使用 <xref:System.Collections.Concurrent> 命名空间中的类，而不是 <xref:System.Collections.Generic?displayProperty=nameWithType> 和 <xref:System.Collections?displayProperty=nameWithType> 命名空间中的相应类型。</span><span class="sxs-lookup"><span data-stu-id="4de75-155">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=nameWithType> and <xref:System.Collections?displayProperty=nameWithType> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="4de75-156">有关详细信息，请参阅[线程安全集合](../../../standard/collections/thread-safe/index.md)和 <xref:System.Collections.Concurrent>。</span><span class="sxs-lookup"><span data-stu-id="4de75-156">For more information, see [Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span></span>

<span data-ttu-id="4de75-157">包含在 <xref:System.Collections.Concurrent> 命名空间中的一些类为 <xref:System.Collections.Concurrent.BlockingCollection%601>、<xref:System.Collections.Concurrent.ConcurrentDictionary%602>、<xref:System.Collections.Concurrent.ConcurrentQueue%601> 和 <xref:System.Collections.Concurrent.ConcurrentStack%601>。</span><span class="sxs-lookup"><span data-stu-id="4de75-157">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>

<a name="BKMK_Collections"></a>

### <a name="systemcollections-classes"></a><span data-ttu-id="4de75-158">System.Collections 类</span><span class="sxs-lookup"><span data-stu-id="4de75-158">System.Collections Classes</span></span>

<span data-ttu-id="4de75-159"><xref:System.Collections?displayProperty=nameWithType> 命名空间中的类不会将元素作为特别类型化的对象存储，而是作为 `Object` 类型的对象存储。</span><span class="sxs-lookup"><span data-stu-id="4de75-159">The classes in the <xref:System.Collections?displayProperty=nameWithType> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>

<span data-ttu-id="4de75-160">只要可能，则应使用 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空间或 <xref:System.Collections.Concurrent> 命名空间中的泛型集合，而不是 `System.Collections` 命名空间中的旧类型。</span><span class="sxs-lookup"><span data-stu-id="4de75-160">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>

<span data-ttu-id="4de75-161">下表列出了 `System.Collections` 命名空间中的一些常用类：</span><span class="sxs-lookup"><span data-stu-id="4de75-161">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>

|<span data-ttu-id="4de75-162">类</span><span class="sxs-lookup"><span data-stu-id="4de75-162">Class</span></span>|<span data-ttu-id="4de75-163">说明</span><span class="sxs-lookup"><span data-stu-id="4de75-163">Description</span></span>|
|---|---|
|<xref:System.Collections.ArrayList>|<span data-ttu-id="4de75-164">表示对象的数组，这些对象的大小会根据需要动态增加。</span><span class="sxs-lookup"><span data-stu-id="4de75-164">Represents an array of objects whose size is dynamically increased as required.</span></span>|
|<xref:System.Collections.Hashtable>|<span data-ttu-id="4de75-165">表示根据键的哈希代码进行组织的键/值对的集合。</span><span class="sxs-lookup"><span data-stu-id="4de75-165">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|
|<xref:System.Collections.Queue>|<span data-ttu-id="4de75-166">表示对象的先进先出 (FIFO) 集合。</span><span class="sxs-lookup"><span data-stu-id="4de75-166">Represents a first in, first out (FIFO) collection of objects.</span></span>|
|<xref:System.Collections.Stack>|<span data-ttu-id="4de75-167">表示对象的后进先出 (LIFO) 集合。</span><span class="sxs-lookup"><span data-stu-id="4de75-167">Represents a last in, first out (LIFO) collection of objects.</span></span>|

<span data-ttu-id="4de75-168"><xref:System.Collections.Specialized> 命名空间提供专门类型化以及强类型化的集合类，例如只包含字符串的集合以及链接列表和混合字典。</span><span class="sxs-lookup"><span data-stu-id="4de75-168">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>

<a name="BKMK_VisualBasic"></a>

### <a name="visual-basic-collection-class"></a><span data-ttu-id="4de75-169">Visual Basic 集合类</span><span class="sxs-lookup"><span data-stu-id="4de75-169">Visual Basic Collection Class</span></span>

<span data-ttu-id="4de75-170">可以使用 Visual Basic <xref:Microsoft.VisualBasic.Collection> 类以使用数字索引或 `String` 键访问集合项。</span><span class="sxs-lookup"><span data-stu-id="4de75-170">You can use the Visual Basic <xref:Microsoft.VisualBasic.Collection> class to access a collection item by using either a numeric index or a `String` key.</span></span> <span data-ttu-id="4de75-171">你可以向集合对象中添加一个已经或还未指定键的项。</span><span class="sxs-lookup"><span data-stu-id="4de75-171">You can add items to a collection object either with or without specifying a key.</span></span> <span data-ttu-id="4de75-172">如果你添加了不带有键的项，必须使用其数字索引来访问它。</span><span class="sxs-lookup"><span data-stu-id="4de75-172">If you add an item without a key, you must use its numeric index to access it.</span></span>

<span data-ttu-id="4de75-173">Visual Basic `Collection` 类将其所有元素存储为 `Object` 类型，因此你可以添加任何数据类型的项。</span><span class="sxs-lookup"><span data-stu-id="4de75-173">The Visual Basic `Collection` class stores all its elements as type `Object`, so you can add an item of any data type.</span></span> <span data-ttu-id="4de75-174">没有任何保护措施来防止添加不适当的数据类型。</span><span class="sxs-lookup"><span data-stu-id="4de75-174">There is no safeguard against inappropriate data types being added.</span></span>

<span data-ttu-id="4de75-175">当你使用 Visual Basic `Collection` 类时，集合中的第一项的索引为 1。</span><span class="sxs-lookup"><span data-stu-id="4de75-175">When you use the Visual Basic `Collection` class, the first item in a collection has an index of 1.</span></span> <span data-ttu-id="4de75-176">这不同于 .NET Framework 集合类，其起始索引为 0。</span><span class="sxs-lookup"><span data-stu-id="4de75-176">This differs from the .NET Framework collection classes, for which the starting index is 0.</span></span>

<span data-ttu-id="4de75-177">只要可能，则应使用 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空间或 <xref:System.Collections.Concurrent> 命名空间中的泛型集合而不是 Visual Basic `Collection` 类。</span><span class="sxs-lookup"><span data-stu-id="4de75-177">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the Visual Basic `Collection` class.</span></span>

<span data-ttu-id="4de75-178">有关详细信息，请参阅 <xref:Microsoft.VisualBasic.Collection>。</span><span class="sxs-lookup"><span data-stu-id="4de75-178">For more information, see <xref:Microsoft.VisualBasic.Collection>.</span></span>

<a name="BKMK_KeyValuePairs"></a>

## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="4de75-179">实现键/值对集合</span><span class="sxs-lookup"><span data-stu-id="4de75-179">Implementing a Collection of Key/Value Pairs</span></span>

<span data-ttu-id="4de75-180"><xref:System.Collections.Generic.Dictionary%602> 泛型集合可通过每个元素的键访问集合中的元素。</span><span class="sxs-lookup"><span data-stu-id="4de75-180">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="4de75-181">每次对字典的添加都包含一个值和与其关联的键。</span><span class="sxs-lookup"><span data-stu-id="4de75-181">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="4de75-182">通过使用键来检索值十分快捷，因为 `Dictionary` 类实现为哈希表。</span><span class="sxs-lookup"><span data-stu-id="4de75-182">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>

<span data-ttu-id="4de75-183">以下示例创建 `Dictionary` 集合并通过使用 `For Each` 语句循环访问字典。</span><span class="sxs-lookup"><span data-stu-id="4de75-183">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `For Each` statement.</span></span>

```vb
Private Sub IterateThroughDictionary()
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()

    For Each kvp As KeyValuePair(Of String, Element) In elements
        Dim theElement As Element = kvp.Value

        Console.WriteLine("key: " & kvp.Key)
        With theElement
            Console.WriteLine("values: " & .Symbol & " " &
                .Name & " " & .AtomicNumber)
        End With
    Next
End Sub

Private Function BuildDictionary() As Dictionary(Of String, Element)
    Dim elements As New Dictionary(Of String, Element)

    AddToDictionary(elements, "K", "Potassium", 19)
    AddToDictionary(elements, "Ca", "Calcium", 20)
    AddToDictionary(elements, "Sc", "Scandium", 21)
    AddToDictionary(elements, "Ti", "Titanium", 22)

    Return elements
End Function

Private Sub AddToDictionary(ByVal elements As Dictionary(Of String, Element),
ByVal symbol As String, ByVal name As String, ByVal atomicNumber As Integer)
    Dim theElement As New Element

    theElement.Symbol = symbol
    theElement.Name = name
    theElement.AtomicNumber = atomicNumber

    elements.Add(Key:=theElement.Symbol, value:=theElement)
End Sub

Public Class Element
    Public Property Symbol As String
    Public Property Name As String
    Public Property AtomicNumber As Integer
End Class
```

<span data-ttu-id="4de75-184">若要转而使用集合初始值设定项生成 `Dictionary` 集合，可使用以下方法替换 `BuildDictionary` 和 `AddToDictionary`。</span><span class="sxs-lookup"><span data-stu-id="4de75-184">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>

```vb
Private Function BuildDictionary2() As Dictionary(Of String, Element)
    Return New Dictionary(Of String, Element) From
        {
            {"K", New Element With
                {.Symbol = "K", .Name = "Potassium", .AtomicNumber = 19}},
            {"Ca", New Element With
                {.Symbol = "Ca", .Name = "Calcium", .AtomicNumber = 20}},
            {"Sc", New Element With
                {.Symbol = "Sc", .Name = "Scandium", .AtomicNumber = 21}},
            {"Ti", New Element With
                {.Symbol = "Ti", .Name = "Titanium", .AtomicNumber = 22}}
        }
End Function
```

<span data-ttu-id="4de75-185">以下示例使用 <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> 方法和 `Dictionary` 的 <xref:System.Collections.Generic.Dictionary%602.Item%2A> 属性按键快速查找某个项。</span><span class="sxs-lookup"><span data-stu-id="4de75-185">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="4de75-186">`Item`属性使你能够 `elements` 使用 Visual Basic 中的代码访问集合中的项 `elements(symbol)` 。</span><span class="sxs-lookup"><span data-stu-id="4de75-186">The `Item` property enables you to access an item in the `elements` collection by using the `elements(symbol)` code in Visual Basic.</span></span>

```vb
Private Sub FindInDictionary(ByVal symbol As String)
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()

    If elements.ContainsKey(symbol) = False Then
        Console.WriteLine(symbol & " not found")
    Else
        Dim theElement = elements(symbol)
        Console.WriteLine("found: " & theElement.Name)
    End If
End Sub
```

<span data-ttu-id="4de75-187">以下示例则使用 <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> 方法按键快速查找某个项。</span><span class="sxs-lookup"><span data-stu-id="4de75-187">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>

```vb
Private Sub FindInDictionary2(ByVal symbol As String)
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()

    Dim theElement As Element = Nothing
    If elements.TryGetValue(symbol, theElement) = False Then
        Console.WriteLine(symbol & " not found")
    Else
        Console.WriteLine("found: " & theElement.Name)
    End If
End Sub
```

<a name="BKMK_LINQ"></a>

## <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="4de75-188">使用 LINQ 访问集合</span><span class="sxs-lookup"><span data-stu-id="4de75-188">Using LINQ to Access a Collection</span></span>

<span data-ttu-id="4de75-189">可以使用 LINQ（语言集成查询）来访问集合。</span><span class="sxs-lookup"><span data-stu-id="4de75-189">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="4de75-190">LINQ 查询提供筛选、排序和分组功能。</span><span class="sxs-lookup"><span data-stu-id="4de75-190">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="4de75-191">有关详细信息，请参阅[Visual Basic 中的入门 LINQ](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="4de75-191">For more information, see [Getting Started with LINQ in Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>

<span data-ttu-id="4de75-192">以下示例运行一个对泛型 `List` 的 LINQ 查询。</span><span class="sxs-lookup"><span data-stu-id="4de75-192">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="4de75-193">LINQ 查询返回一个包含结果的不同集合。</span><span class="sxs-lookup"><span data-stu-id="4de75-193">The LINQ query returns a different collection that contains the results.</span></span>

```vb
Private Sub ShowLINQ()
    Dim elements As List(Of Element) = BuildList()

    ' LINQ Query.
    Dim subset = From theElement In elements
                  Where theElement.AtomicNumber < 22
                  Order By theElement.Name

    For Each theElement In subset
        Console.WriteLine(theElement.Name & " " & theElement.AtomicNumber)
    Next

    ' Output:
    '  Calcium 20
    '  Potassium 19
    '  Scandium 21
End Sub

Private Function BuildList() As List(Of Element)
    Return New List(Of Element) From
        {
            {New Element With
                {.Symbol = "K", .Name = "Potassium", .AtomicNumber = 19}},
            {New Element With
                {.Symbol = "Ca", .Name = "Calcium", .AtomicNumber = 20}},
            {New Element With
                {.Symbol = "Sc", .Name = "Scandium", .AtomicNumber = 21}},
            {New Element With
                {.Symbol = "Ti", .Name = "Titanium", .AtomicNumber = 22}}
        }
End Function

Public Class Element
    Public Property Symbol As String
    Public Property Name As String
    Public Property AtomicNumber As Integer
End Class
```

<a name="BKMK_Sorting"></a>

## <a name="sorting-a-collection"></a><span data-ttu-id="4de75-194">对集合排序</span><span class="sxs-lookup"><span data-stu-id="4de75-194">Sorting a Collection</span></span>

<span data-ttu-id="4de75-195">以下示例阐释了对集合排序的过程。</span><span class="sxs-lookup"><span data-stu-id="4de75-195">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="4de75-196">该示例对 <xref:System.Collections.Generic.List%601> 中存储的 `Car` 类的实例进行排序。</span><span class="sxs-lookup"><span data-stu-id="4de75-196">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="4de75-197">`Car` 类实现 <xref:System.IComparable%601> 接口，此操作需要实现 <xref:System.IComparable%601.CompareTo%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="4de75-197">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>

<span data-ttu-id="4de75-198">每次对 <xref:System.IComparable%601.CompareTo%2A> 方法的调用均会执行用于排序的单一比较。</span><span class="sxs-lookup"><span data-stu-id="4de75-198">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="4de75-199">`CompareTo` 方法中用户编写的代码针对当前对象与另一个对象的每个比较返回一个值。</span><span class="sxs-lookup"><span data-stu-id="4de75-199">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="4de75-200">如果当前对象小于另一个对象，则返回的值小于零；如果当前对象大于另一个对象，则返回的值大于零；如果当前对象等于另一个对象，则返回的值等于零。</span><span class="sxs-lookup"><span data-stu-id="4de75-200">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="4de75-201">这使你可以在代码中定义大于、小于和等于条件。</span><span class="sxs-lookup"><span data-stu-id="4de75-201">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>

<span data-ttu-id="4de75-202">在 `ListCars` 方法中，`cars.Sort()` 语句对列表进行排序。</span><span class="sxs-lookup"><span data-stu-id="4de75-202">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="4de75-203">对 <xref:System.Collections.Generic.List%601> 的 <xref:System.Collections.Generic.List%601.Sort%2A> 方法的此调用将导致为 `List` 中的 `Car` 对象自动调用 `CompareTo` 方法。</span><span class="sxs-lookup"><span data-stu-id="4de75-203">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>

```vb
Public Sub ListCars()

    ' Create some new cars.
    Dim cars As New List(Of Car) From
    {
        New Car With {.Name = "car1", .Color = "blue", .Speed = 20},
        New Car With {.Name = "car2", .Color = "red", .Speed = 50},
        New Car With {.Name = "car3", .Color = "green", .Speed = 10},
        New Car With {.Name = "car4", .Color = "blue", .Speed = 50},
        New Car With {.Name = "car5", .Color = "blue", .Speed = 30},
        New Car With {.Name = "car6", .Color = "red", .Speed = 60},
        New Car With {.Name = "car7", .Color = "green", .Speed = 50}
    }

    ' Sort the cars by color alphabetically, and then by speed
    ' in descending order.
    cars.Sort()

    ' View all of the cars.
    For Each thisCar As Car In cars
        Console.Write(thisCar.Color.PadRight(5) & " ")
        Console.Write(thisCar.Speed.ToString & " ")
        Console.Write(thisCar.Name)
        Console.WriteLine()
    Next

    ' Output:
    '  blue  50 car4
    '  blue  30 car5
    '  blue  20 car1
    '  green 50 car7
    '  green 10 car3
    '  red   60 car6
    '  red   50 car2
End Sub

Public Class Car
    Implements IComparable(Of Car)

    Public Property Name As String
    Public Property Speed As Integer
    Public Property Color As String

    Public Function CompareTo(ByVal other As Car) As Integer _
        Implements System.IComparable(Of Car).CompareTo
        ' A call to this method makes a single comparison that is
        ' used for sorting.

        ' Determine the relative order of the objects being compared.
        ' Sort by color alphabetically, and then by speed in
        ' descending order.

        ' Compare the colors.
        Dim compare As Integer
        compare = String.Compare(Me.Color, other.Color, True)

        ' If the colors are the same, compare the speeds.
        If compare = 0 Then
            compare = Me.Speed.CompareTo(other.Speed)

            ' Use descending order for speed.
            compare = -compare
        End If

        Return compare
    End Function
End Class
```

<a name="BKMK_CustomCollection"></a>

## <a name="defining-a-custom-collection"></a><span data-ttu-id="4de75-204">定义自定义集合</span><span class="sxs-lookup"><span data-stu-id="4de75-204">Defining a Custom Collection</span></span>

<span data-ttu-id="4de75-205">可以通过实现 <xref:System.Collections.Generic.IEnumerable%601> 或 <xref:System.Collections.IEnumerable> 接口来定义集合。</span><span class="sxs-lookup"><span data-stu-id="4de75-205">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="4de75-206">有关其他信息，请参阅[枚举集合](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hwyysy67(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="4de75-206">For additional information, see [Enumerating a Collection](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hwyysy67(v=vs.100)).</span></span>

<span data-ttu-id="4de75-207">尽管可以定义自定义集合，但通常最好使用包含在 .NET Framework 中的集合，这在本主题前面的[集合类型](#kinds-of-collections)中进行了介绍。</span><span class="sxs-lookup"><span data-stu-id="4de75-207">Although you can define a custom collection, it is usually better to instead use the collections that are included in the .NET Framework, which are described in [Kinds of Collections](#kinds-of-collections) earlier in this topic.</span></span>

<span data-ttu-id="4de75-208">以下示例定义一个名为 `AllColors` 的自定义集合类。</span><span class="sxs-lookup"><span data-stu-id="4de75-208">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="4de75-209">此类实现 <xref:System.Collections.IEnumerable> 接口，此操作需要实现 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="4de75-209">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>

<span data-ttu-id="4de75-210">`GetEnumerator` 方法返回 `ColorEnumerator` 类的一个实例。</span><span class="sxs-lookup"><span data-stu-id="4de75-210">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="4de75-211">`ColorEnumerator` 实现 <xref:System.Collections.IEnumerator> 接口，此操作需要实现 <xref:System.Collections.IEnumerator.Current%2A> 属性、<xref:System.Collections.IEnumerator.MoveNext%2A> 方法以及 <xref:System.Collections.IEnumerator.Reset%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="4de75-211">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>

```vb
Public Sub ListColors()
    Dim colors As New AllColors()

    For Each theColor As Color In colors
        Console.Write(theColor.Name & " ")
    Next
    Console.WriteLine()
    ' Output: red blue green
End Sub

' Collection class.
Public Class AllColors
    Implements System.Collections.IEnumerable

    Private _colors() As Color =
    {
        New Color With {.Name = "red"},
        New Color With {.Name = "blue"},
        New Color With {.Name = "green"}
    }

    Public Function GetEnumerator() As System.Collections.IEnumerator _
        Implements System.Collections.IEnumerable.GetEnumerator

        Return New ColorEnumerator(_colors)

        ' Instead of creating a custom enumerator, you could
        ' use the GetEnumerator of the array.
        'Return _colors.GetEnumerator
    End Function

    ' Custom enumerator.
    Private Class ColorEnumerator
        Implements System.Collections.IEnumerator

        Private _colors() As Color
        Private _position As Integer = -1

        Public Sub New(ByVal colors() As Color)
            _colors = colors
        End Sub

        Public ReadOnly Property Current() As Object _
            Implements System.Collections.IEnumerator.Current
            Get
                Return _colors(_position)
            End Get
        End Property

        Public Function MoveNext() As Boolean _
            Implements System.Collections.IEnumerator.MoveNext
            _position += 1
            Return (_position < _colors.Length)
        End Function

        Public Sub Reset() Implements System.Collections.IEnumerator.Reset
            _position = -1
        End Sub
    End Class
End Class

' Element class.
Public Class Color
    Public Property Name As String
End Class
```

<a name="BKMK_Iterators"></a>

## <a name="iterators"></a><span data-ttu-id="4de75-212">迭代器</span><span class="sxs-lookup"><span data-stu-id="4de75-212">Iterators</span></span>

<span data-ttu-id="4de75-213">迭代器\*\* 用于对集合执行自定义迭代。</span><span class="sxs-lookup"><span data-stu-id="4de75-213">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="4de75-214">迭代器可以是一种方法，或是一个 `get` 访问器。</span><span class="sxs-lookup"><span data-stu-id="4de75-214">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="4de75-215">迭代器使用[Yield](../../../visual-basic/language-reference/statements/yield-statement.md)语句每次返回集合中的每个元素。</span><span class="sxs-lookup"><span data-stu-id="4de75-215">An iterator uses a [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element of the collection one at a time.</span></span>

<span data-ttu-id="4de75-216">您可以通过[对每个 .。。下一](../../../visual-basic/language-reference/statements/for-each-next-statement.md)语句。</span><span class="sxs-lookup"><span data-stu-id="4de75-216">You call an iterator by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span> <span data-ttu-id="4de75-217">`For Each` 循环的每次迭代都会调用迭代器。</span><span class="sxs-lookup"><span data-stu-id="4de75-217">Each iteration of the `For Each` loop calls the iterator.</span></span> <span data-ttu-id="4de75-218">迭代器中到达 `Yield` 语句时，会返回一个表达式，并保留当前在代码中的位置。</span><span class="sxs-lookup"><span data-stu-id="4de75-218">When a `Yield` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="4de75-219">下次调用迭代器时，将从该位置重新开始执行。</span><span class="sxs-lookup"><span data-stu-id="4de75-219">Execution is restarted from that location the next time that the iterator is called.</span></span>

<span data-ttu-id="4de75-220">有关详细信息，请参阅[迭代器（Visual Basic）](../../../visual-basic/programming-guide/concepts/iterators.md)。</span><span class="sxs-lookup"><span data-stu-id="4de75-220">For more information, see [Iterators (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span></span>

<span data-ttu-id="4de75-221">下面的示例使用迭代器方法。</span><span class="sxs-lookup"><span data-stu-id="4de75-221">The following example uses an iterator method.</span></span> <span data-ttu-id="4de75-222">迭代器方法的 `Yield` 语句位于[For .。。下一个](../../../visual-basic/language-reference/statements/for-next-statement.md)循环。</span><span class="sxs-lookup"><span data-stu-id="4de75-222">The iterator method has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="4de75-223">在 `ListEvenNumbers` 方法中，`For Each` 语句体的每次迭代都会创建对迭代器方法的调用，并将继续到下一个 `Yield` 语句。</span><span class="sxs-lookup"><span data-stu-id="4de75-223">In the `ListEvenNumbers` method, each iteration of the `For Each` statement body creates a call to the iterator method, which proceeds to the next `Yield` statement.</span></span>

```vb
Public Sub ListEvenNumbers()
    For Each number As Integer In EvenSequence(5, 18)
        Console.Write(number & " ")
    Next
    Console.WriteLine()
    ' Output: 6 8 10 12 14 16 18
End Sub

Private Iterator Function EvenSequence(
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _
As IEnumerable(Of Integer)

' Yield even numbers in the range.
    For number = firstNumber To lastNumber
        If number Mod 2 = 0 Then
            Yield number
        End If
    Next
End Function
```

## <a name="see-also"></a><span data-ttu-id="4de75-224">请参阅</span><span class="sxs-lookup"><span data-stu-id="4de75-224">See also</span></span>

- [<span data-ttu-id="4de75-225">集合初始值设定项</span><span class="sxs-lookup"><span data-stu-id="4de75-225">Collection Initializers</span></span>](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [<span data-ttu-id="4de75-226">编程概念（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="4de75-226">Programming Concepts (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="4de75-227">Option Strict 语句</span><span class="sxs-lookup"><span data-stu-id="4de75-227">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="4de75-228">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4de75-228">LINQ to Objects (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="4de75-229">并行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="4de75-229">Parallel LINQ (PLINQ)</span></span>](../../../standard/parallel-programming/introduction-to-plinq.md)
- [<span data-ttu-id="4de75-230">集合和数据结构</span><span class="sxs-lookup"><span data-stu-id="4de75-230">Collections and Data Structures</span></span>](../../../standard/collections/index.md)
- [<span data-ttu-id="4de75-231">选择集合类</span><span class="sxs-lookup"><span data-stu-id="4de75-231">Selecting a Collection Class</span></span>](../../../standard/collections/selecting-a-collection-class.md)
- [<span data-ttu-id="4de75-232">集合内的比较和排序</span><span class="sxs-lookup"><span data-stu-id="4de75-232">Comparisons and Sorts Within Collections</span></span>](../../../standard/collections/comparisons-and-sorts-within-collections.md)
- [<span data-ttu-id="4de75-233">何时使用泛型集合</span><span class="sxs-lookup"><span data-stu-id="4de75-233">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)

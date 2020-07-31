---
title: 泛型接口中的变体 (C#)
description: 查看泛型接口的变体支持信息，包括 .NET Framework 4 和 4.5 中现有接口的更新信息。
ms.date: 06/06/2019
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: 91218742c01eeb6e65ea26d9dc41ed7c98827377
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105634"
---
# <a name="variance-in-generic-interfaces-c"></a><span data-ttu-id="57d48-103">泛型接口中的变体 (C#)</span><span class="sxs-lookup"><span data-stu-id="57d48-103">Variance in Generic Interfaces (C#)</span></span>

<span data-ttu-id="57d48-104">.NET Framework 4 引入了对多个现有泛型接口的变体支持。</span><span class="sxs-lookup"><span data-stu-id="57d48-104">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="57d48-105">变体支持允许实现这些接口的类进行隐式转换。</span><span class="sxs-lookup"><span data-stu-id="57d48-105">Variance support enables implicit conversion of classes that implement these interfaces.</span></span>

<span data-ttu-id="57d48-106">自 .NET Framework 4 起，以下接口为变体：</span><span class="sxs-lookup"><span data-stu-id="57d48-106">Starting with .NET Framework 4, the following interfaces are variant:</span></span>

- <span data-ttu-id="57d48-107"><xref:System.Collections.Generic.IEnumerable%601>（T 是协变）</span><span class="sxs-lookup"><span data-stu-id="57d48-107"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>

- <span data-ttu-id="57d48-108"><xref:System.Collections.Generic.IEnumerator%601>（T 是协变）</span><span class="sxs-lookup"><span data-stu-id="57d48-108"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>

- <span data-ttu-id="57d48-109"><xref:System.Linq.IQueryable%601>（T 是协变）</span><span class="sxs-lookup"><span data-stu-id="57d48-109"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>

- <span data-ttu-id="57d48-110"><xref:System.Linq.IGrouping%602>（`TKey` 和 `TElement` 都是协变）</span><span class="sxs-lookup"><span data-stu-id="57d48-110"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>

- <span data-ttu-id="57d48-111"><xref:System.Collections.Generic.IComparer%601>（T 是逆变）</span><span class="sxs-lookup"><span data-stu-id="57d48-111"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="57d48-112"><xref:System.Collections.Generic.IEqualityComparer%601>（T 是逆变）</span><span class="sxs-lookup"><span data-stu-id="57d48-112"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="57d48-113"><xref:System.IComparable%601>（T 是逆变）</span><span class="sxs-lookup"><span data-stu-id="57d48-113"><xref:System.IComparable%601> (T is contravariant)</span></span>

<span data-ttu-id="57d48-114">自 .NET Framework 4.5 起，以下接口是变体：</span><span class="sxs-lookup"><span data-stu-id="57d48-114">Starting with .NET Framework 4.5, the following interfaces are variant:</span></span>

- <span data-ttu-id="57d48-115"><xref:System.Collections.Generic.IReadOnlyList%601>（T 是协变）</span><span class="sxs-lookup"><span data-stu-id="57d48-115"><xref:System.Collections.Generic.IReadOnlyList%601> (T is covariant)</span></span>

- <span data-ttu-id="57d48-116"><xref:System.Collections.Generic.IReadOnlyCollection%601>（T 是协变）</span><span class="sxs-lookup"><span data-stu-id="57d48-116"><xref:System.Collections.Generic.IReadOnlyCollection%601> (T is covariant)</span></span>

<span data-ttu-id="57d48-117">协变允许方法具有的返回类型比接口的泛型类型参数定义的返回类型的派生程度更大。</span><span class="sxs-lookup"><span data-stu-id="57d48-117">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="57d48-118">若要演示协变功能，请考虑以下泛型接口：`IEnumerable<Object>` 和 `IEnumerable<String>`。</span><span class="sxs-lookup"><span data-stu-id="57d48-118">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable<Object>` and `IEnumerable<String>`.</span></span> <span data-ttu-id="57d48-119">`IEnumerable<String>` 接口不继承 `IEnumerable<Object>` 接口。</span><span class="sxs-lookup"><span data-stu-id="57d48-119">The `IEnumerable<String>` interface does not inherit the `IEnumerable<Object>` interface.</span></span> <span data-ttu-id="57d48-120">但是，`String` 类型会继承 `Object` 类型，在某些情况下，建议为这些接口互相指派彼此的对象。</span><span class="sxs-lookup"><span data-stu-id="57d48-120">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="57d48-121">下面的代码示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="57d48-121">This is shown in the following code example.</span></span>

```csharp
IEnumerable<String> strings = new List<String>();
IEnumerable<Object> objects = strings;
```

<span data-ttu-id="57d48-122">在旧版 .NET Framework 中，此代码会导致 C# 中出现编译错误；如果启用 `Option Strict` 条件，则会导致在 Visual Basic 中出现编译错误。</span><span class="sxs-lookup"><span data-stu-id="57d48-122">In earlier versions of .NET Framework, this code causes a compilation error in C# and, if `Option Strict` is on, in Visual Basic.</span></span> <span data-ttu-id="57d48-123">但现在可使用 `strings` 代替 `objects`，如上例所示，因为 <xref:System.Collections.Generic.IEnumerable%601> 接口是协变接口。</span><span class="sxs-lookup"><span data-stu-id="57d48-123">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>

<span data-ttu-id="57d48-124">逆变允许方法具有的实参类型比接口的泛型形参定义的类型的派生程度更小。</span><span class="sxs-lookup"><span data-stu-id="57d48-124">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="57d48-125">若要演示逆变，假设已创建了 `BaseComparer` 类来比较 `BaseClass` 类的实例。</span><span class="sxs-lookup"><span data-stu-id="57d48-125">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="57d48-126">`BaseComparer` 类实现 `IEqualityComparer<BaseClass>` 接口。</span><span class="sxs-lookup"><span data-stu-id="57d48-126">The `BaseComparer` class implements the `IEqualityComparer<BaseClass>` interface.</span></span> <span data-ttu-id="57d48-127">因为 <xref:System.Collections.Generic.IEqualityComparer%601> 接口现在是逆变接口，因此可使用 `BaseComparer` 比较继承 `BaseClass` 类的类的实例。</span><span class="sxs-lookup"><span data-stu-id="57d48-127">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="57d48-128">下面的代码示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="57d48-128">This is shown in the following code example.</span></span>

```csharp
// Simple hierarchy of classes.
class BaseClass { }
class DerivedClass : BaseClass { }

// Comparer class.
class BaseComparer : IEqualityComparer<BaseClass>
{
    public int GetHashCode(BaseClass baseInstance)
    {
        return baseInstance.GetHashCode();
    }
    public bool Equals(BaseClass x, BaseClass y)
    {
        return x == y;
    }
}
class Program
{
    static void Test()
    {
        IEqualityComparer<BaseClass> baseComparer = new BaseComparer();

        // Implicit conversion of IEqualityComparer<BaseClass> to
        // IEqualityComparer<DerivedClass>.
        IEqualityComparer<DerivedClass> childComparer = baseComparer;
    }
}
```

<span data-ttu-id="57d48-129">有关更多示例，请参阅[在泛型集合的接口中使用变体 (C#)](./using-variance-in-interfaces-for-generic-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="57d48-129">For more examples, see [Using Variance in Interfaces for Generic Collections (C#)](./using-variance-in-interfaces-for-generic-collections.md).</span></span>

<span data-ttu-id="57d48-130">只有引用类型才支持使用泛型接口中的变体。</span><span class="sxs-lookup"><span data-stu-id="57d48-130">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="57d48-131">值类型不支持变体。</span><span class="sxs-lookup"><span data-stu-id="57d48-131">Value types do not support variance.</span></span> <span data-ttu-id="57d48-132">例如，无法将 `IEnumerable<int>` 隐式转换为 `IEnumerable<object>`，因为整数由值类型表示。</span><span class="sxs-lookup"><span data-stu-id="57d48-132">For example, `IEnumerable<int>` cannot be implicitly converted to `IEnumerable<object>`, because integers are represented by a value type.</span></span>

```csharp
IEnumerable<int> integers = new List<int>();
// The following statement generates a compiler error,
// because int is a value type.
// IEnumerable<Object> objects = integers;
```

<span data-ttu-id="57d48-133">还需记住，实现变体接口的类仍是固定类。</span><span class="sxs-lookup"><span data-stu-id="57d48-133">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="57d48-134">例如，虽然 <xref:System.Collections.Generic.List%601> 实现协变接口 <xref:System.Collections.Generic.IEnumerable%601>，但不能将 `List<String>` 隐式转换为 `List<Object>`。</span><span class="sxs-lookup"><span data-stu-id="57d48-134">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List<String>` to `List<Object>`.</span></span> <span data-ttu-id="57d48-135">以下代码示例阐释了这一点。</span><span class="sxs-lookup"><span data-stu-id="57d48-135">This is illustrated in the following code example.</span></span>

```csharp
// The following line generates a compiler error
// because classes are invariant.
// List<Object> list = new List<String>();

// You can use the interface object instead.
IEnumerable<Object> listObjects = new List<String>();
```

## <a name="see-also"></a><span data-ttu-id="57d48-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="57d48-136">See also</span></span>

- [<span data-ttu-id="57d48-137">在泛型集合的接口中使用变体 (C#)</span><span class="sxs-lookup"><span data-stu-id="57d48-137">Using Variance in Interfaces for Generic Collections (C#)</span></span>](./using-variance-in-interfaces-for-generic-collections.md)
- [<span data-ttu-id="57d48-138">创建变体泛型接口 (C#)</span><span class="sxs-lookup"><span data-stu-id="57d48-138">Creating Variant Generic Interfaces (C#)</span></span>](./creating-variant-generic-interfaces.md)
- [<span data-ttu-id="57d48-139">泛型接口</span><span class="sxs-lookup"><span data-stu-id="57d48-139">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)
- [<span data-ttu-id="57d48-140">委托中的变体 (C#)</span><span class="sxs-lookup"><span data-stu-id="57d48-140">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)

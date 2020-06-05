---
title: 泛型接口中的变体
ms.date: 07/20/2015
ms.assetid: cf4096d0-4bb3-45a9-9a6b-f01e29a60333
ms.openlocfilehash: df28a9f24518f24d1be89acba726da7dfbbf9570
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375585"
---
# <a name="variance-in-generic-interfaces-visual-basic"></a><span data-ttu-id="dbc6c-102">泛型接口中的变体 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dbc6c-102">Variance in Generic Interfaces (Visual Basic)</span></span>

<span data-ttu-id="dbc6c-103">.NET Framework 4 引入了对多个现有泛型接口的变体支持。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="dbc6c-104">变体支持允许实现这些接口的类进行隐式转换。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> <span data-ttu-id="dbc6c-105">下面的接口现在是变体：</span><span class="sxs-lookup"><span data-stu-id="dbc6c-105">The following interfaces are now variant:</span></span>

- <span data-ttu-id="dbc6c-106"><xref:System.Collections.Generic.IEnumerable%601>（T 是协变）</span><span class="sxs-lookup"><span data-stu-id="dbc6c-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>

- <span data-ttu-id="dbc6c-107"><xref:System.Collections.Generic.IEnumerator%601>（T 是协变）</span><span class="sxs-lookup"><span data-stu-id="dbc6c-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>

- <span data-ttu-id="dbc6c-108"><xref:System.Linq.IQueryable%601>（T 是协变）</span><span class="sxs-lookup"><span data-stu-id="dbc6c-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>

- <span data-ttu-id="dbc6c-109"><xref:System.Linq.IGrouping%602>（`TKey` 和 `TElement` 都是协变）</span><span class="sxs-lookup"><span data-stu-id="dbc6c-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>

- <span data-ttu-id="dbc6c-110"><xref:System.Collections.Generic.IComparer%601>（T 是逆变）</span><span class="sxs-lookup"><span data-stu-id="dbc6c-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="dbc6c-111"><xref:System.Collections.Generic.IEqualityComparer%601>（T 是逆变）</span><span class="sxs-lookup"><span data-stu-id="dbc6c-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="dbc6c-112"><xref:System.IComparable%601>（T 是逆变）</span><span class="sxs-lookup"><span data-stu-id="dbc6c-112"><xref:System.IComparable%601> (T is contravariant)</span></span>

<span data-ttu-id="dbc6c-113">协变允许方法具有的返回类型比接口的泛型类型参数定义的返回类型的派生程度更大。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-113">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="dbc6c-114">若要演示协变功能，请考虑以下泛型接口：`IEnumerable(Of Object)` 和 `IEnumerable(Of String)`。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-114">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable(Of Object)` and `IEnumerable(Of String)`.</span></span> <span data-ttu-id="dbc6c-115">`IEnumerable(Of String)` 接口不继承 `IEnumerable(Of Object)` 接口。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-115">The `IEnumerable(Of String)` interface does not inherit the `IEnumerable(Of Object)` interface.</span></span> <span data-ttu-id="dbc6c-116">但是，`String` 类型会继承 `Object` 类型，在某些情况下，建议为这些接口互相指派彼此的对象。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-116">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="dbc6c-117">以下代码示例显示了此特点。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-117">This is shown in the following code example.</span></span>

```vb
Dim strings As IEnumerable(Of String) = New List(Of String)
Dim objects As IEnumerable(Of Object) = strings
```

<span data-ttu-id="dbc6c-118">在 .NET Framework 的早期版本中，此代码会导致在 Visual Basic 中出现编译错误 `Option Strict On` 。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-118">In earlier versions of the .NET Framework, this code causes a compilation error in Visual Basic with `Option Strict On`.</span></span> <span data-ttu-id="dbc6c-119">但现在可使用 `strings` 代替 `objects`，如上例所示，因为 <xref:System.Collections.Generic.IEnumerable%601> 接口是协变接口。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-119">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>

<span data-ttu-id="dbc6c-120">逆变允许方法具有的实参类型比接口的泛型形参定义的类型的派生程度更小。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-120">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="dbc6c-121">若要演示逆变，假设已创建了 `BaseComparer` 类来比较 `BaseClass` 类的实例。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-121">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="dbc6c-122">`BaseComparer` 类实现 `IEqualityComparer(Of BaseClass)` 接口。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-122">The `BaseComparer` class implements the `IEqualityComparer(Of BaseClass)` interface.</span></span> <span data-ttu-id="dbc6c-123">因为 <xref:System.Collections.Generic.IEqualityComparer%601> 接口现在是逆变接口，因此可使用 `BaseComparer` 比较继承 `BaseClass` 类的类的实例。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-123">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="dbc6c-124">以下代码示例显示了此特点。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-124">This is shown in the following code example.</span></span>

```vb
' Simple hierarchy of classes.
Class BaseClass
End Class

Class DerivedClass
    Inherits BaseClass
End Class

' Comparer class.
Class BaseComparer
    Implements IEqualityComparer(Of BaseClass)

    Public Function Equals1(ByVal x As BaseClass,
                            ByVal y As BaseClass) As Boolean _
                            Implements IEqualityComparer(Of BaseClass).Equals
        Return (x.Equals(y))
    End Function

    Public Function GetHashCode1(ByVal obj As BaseClass) As Integer _
        Implements IEqualityComparer(Of BaseClass).GetHashCode
        Return obj.GetHashCode
    End Function
End Class
Sub Test()
    Dim baseComparer As IEqualityComparer(Of BaseClass) = New BaseComparer
    ' Implicit conversion of IEqualityComparer(Of BaseClass) to
    ' IEqualityComparer(Of DerivedClass).
    Dim childComparer As IEqualityComparer(Of DerivedClass) = baseComparer
End Sub
```

<span data-ttu-id="dbc6c-125">有关更多示例，请参阅[在泛型集合的接口中使用变体（Visual Basic）](using-variance-in-interfaces-for-generic-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-125">For more examples, see [Using Variance in Interfaces for Generic Collections (Visual Basic)](using-variance-in-interfaces-for-generic-collections.md).</span></span>

<span data-ttu-id="dbc6c-126">只有引用类型才支持使用泛型接口中的变体。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-126">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="dbc6c-127">值类型不支持变体。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-127">Value types do not support variance.</span></span> <span data-ttu-id="dbc6c-128">例如，无法将 `IEnumerable(Of Integer)` 隐式转换为 `IEnumerable(Of Object)`，因为整数由值类型表示。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-128">For example, `IEnumerable(Of Integer)` cannot be implicitly converted to `IEnumerable(Of Object)`, because integers are represented by a value type.</span></span>

```vb
Dim integers As IEnumerable(Of Integer) = New List(Of Integer)
' The following statement generates a compiler error
' with Option Strict On, because Integer is a value type.
' Dim objects As IEnumerable(Of Object) = integers
```

<span data-ttu-id="dbc6c-129">还需记住，实现变体接口的类仍是固定类。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-129">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="dbc6c-130">例如，虽然 <xref:System.Collections.Generic.List%601> 实现协变接口 <xref:System.Collections.Generic.IEnumerable%601>，但不能将 `List(Of Object)` 隐式转换为 `List(Of String)`。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-130">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List(Of Object)` to `List(Of String)`.</span></span> <span data-ttu-id="dbc6c-131">以下代码示例阐释了这一点。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-131">This is illustrated in the following code example.</span></span>

```vb
' The following statement generates a compiler error
' because classes are invariant.
' Dim list As List(Of Object) = New List(Of String)

' You can use the interface object instead.
Dim listObjects As IEnumerable(Of Object) = New List(Of String)
```

## <a name="see-also"></a><span data-ttu-id="dbc6c-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dbc6c-132">See also</span></span>

- [<span data-ttu-id="dbc6c-133">在泛型集合的接口中使用变体 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dbc6c-133">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>](using-variance-in-interfaces-for-generic-collections.md)
- [<span data-ttu-id="dbc6c-134">创建变体泛型接口 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dbc6c-134">Creating Variant Generic Interfaces (Visual Basic)</span></span>](creating-variant-generic-interfaces.md)
- [<span data-ttu-id="dbc6c-135">泛型接口</span><span class="sxs-lookup"><span data-stu-id="dbc6c-135">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)
- [<span data-ttu-id="dbc6c-136">委托中的变体 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dbc6c-136">Variance in Delegates (Visual Basic)</span></span>](variance-in-delegates.md)

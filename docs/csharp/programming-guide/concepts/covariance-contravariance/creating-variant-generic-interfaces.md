---
title: 创建变体泛型接口 (C#)
ms.date: 07/20/2015
ms.assetid: 30330ec4-9df2-4838-a535-6c406d0ed4df
ms.openlocfilehash: a8e3e010c0e5d5490aee35603cad4fd6c1dc29e0
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990055"
---
# <a name="creating-variant-generic-interfaces-c"></a><span data-ttu-id="b7b04-102">创建变体泛型接口 (C#)</span><span class="sxs-lookup"><span data-stu-id="b7b04-102">Creating Variant Generic Interfaces (C#)</span></span>

<span data-ttu-id="b7b04-103">接口中的泛型类型参数可以声明为协变或逆变。</span><span class="sxs-lookup"><span data-stu-id="b7b04-103">You can declare generic type parameters in interfaces as covariant or contravariant.</span></span> <span data-ttu-id="b7b04-104">协变\*\* 允许接口方法具有与泛型类型参数定义的返回类型相比，派生程度更大的返回类型。</span><span class="sxs-lookup"><span data-stu-id="b7b04-104">*Covariance* allows interface methods to have more derived return types than that defined by the generic type parameters.</span></span> <span data-ttu-id="b7b04-105">逆变\*\* 允许接口方法具有与泛型形参指定的实参类型相比，派生程度更小的实参类型。</span><span class="sxs-lookup"><span data-stu-id="b7b04-105">*Contravariance* allows interface methods to have argument types that are less derived than that specified by the generic parameters.</span></span> <span data-ttu-id="b7b04-106">具有协变或逆变泛型类型参数的泛型接口称为“变体”\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7b04-106">A generic interface that has covariant or contravariant generic type parameters is called *variant*.</span></span>

> [!NOTE]
> <span data-ttu-id="b7b04-107">.NET Framework 4 引入了对多个现有泛型接口的变体支持。</span><span class="sxs-lookup"><span data-stu-id="b7b04-107">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="b7b04-108">有关 .NET 中变体接口的列表，请参阅[泛型接口中的变体 (C#)](./variance-in-generic-interfaces.md)。</span><span class="sxs-lookup"><span data-stu-id="b7b04-108">For the list of the variant interfaces in .NET, see [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md).</span></span>

## <a name="declaring-variant-generic-interfaces"></a><span data-ttu-id="b7b04-109">声明变体泛型接口</span><span class="sxs-lookup"><span data-stu-id="b7b04-109">Declaring Variant Generic Interfaces</span></span>

<span data-ttu-id="b7b04-110">可通过对泛型类型参数使用 `in` 和 `out` 关键字来声明变体泛型接口。</span><span class="sxs-lookup"><span data-stu-id="b7b04-110">You can declare variant generic interfaces by using the `in` and `out` keywords for generic type parameters.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b7b04-111">C# 中的 `ref`、`in` 和 `out` 参数不能为变体。</span><span class="sxs-lookup"><span data-stu-id="b7b04-111">`ref`, `in`, and `out` parameters in C# cannot be variant.</span></span> <span data-ttu-id="b7b04-112">值类型也不支持变体。</span><span class="sxs-lookup"><span data-stu-id="b7b04-112">Value types also do not support variance.</span></span>

<span data-ttu-id="b7b04-113">可以使用 `out` 关键字将泛型类型参数声明为协变。</span><span class="sxs-lookup"><span data-stu-id="b7b04-113">You can declare a generic type parameter covariant by using the `out` keyword.</span></span> <span data-ttu-id="b7b04-114">协变类型必须满足以下条件：</span><span class="sxs-lookup"><span data-stu-id="b7b04-114">The covariant type must satisfy the following conditions:</span></span>

- <span data-ttu-id="b7b04-115">类型仅用作接口方法的返回类型，不用作方法参数的类型。</span><span class="sxs-lookup"><span data-stu-id="b7b04-115">The type is used only as a return type of interface methods and not used as a type of method arguments.</span></span> <span data-ttu-id="b7b04-116">下例演示了此要求，其中类型 `R` 为声明的协变。</span><span class="sxs-lookup"><span data-stu-id="b7b04-116">This is illustrated in the following example, in which the type `R` is declared covariant.</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        R GetSomething();
        // The following statement generates a compiler error.
        // void SetSomething(R sampleArg);

    }
    ```

    <span data-ttu-id="b7b04-117">此规则有一个例外。</span><span class="sxs-lookup"><span data-stu-id="b7b04-117">There is one exception to this rule.</span></span> <span data-ttu-id="b7b04-118">如果具有用作方法参数的逆变泛型委托，则可将类型用作该委托的泛型类型参数。</span><span class="sxs-lookup"><span data-stu-id="b7b04-118">If you have a contravariant generic delegate as a method parameter, you can use the type as a generic type parameter for the delegate.</span></span> <span data-ttu-id="b7b04-119">下例中的类型 `R` 演示了此情形。</span><span class="sxs-lookup"><span data-stu-id="b7b04-119">This is illustrated by the type `R` in the following example.</span></span> <span data-ttu-id="b7b04-120">有关详细信息，请参阅[委托中的变体 (C#)](./variance-in-delegates.md) 和[对 Func 和 Action 泛型委托使用变体 (C#)](./using-variance-for-func-and-action-generic-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="b7b04-120">For more information, see [Variance in Delegates (C#)](./variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        void DoSomething(Action<R> callback);
    }
    ```

- <span data-ttu-id="b7b04-121">类型不用作接口方法的泛型约束。</span><span class="sxs-lookup"><span data-stu-id="b7b04-121">The type is not used as a generic constraint for the interface methods.</span></span> <span data-ttu-id="b7b04-122">下面的代码阐释了这一点。</span><span class="sxs-lookup"><span data-stu-id="b7b04-122">This is illustrated in the following code.</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        // The following statement generates a compiler error
        // because you can use only contravariant or invariant types
        // in generic constraints.
        // void DoSomething<T>() where T : R;
    }
    ```

<span data-ttu-id="b7b04-123">可以使用 `in` 关键字将泛型类型参数声明为逆变。</span><span class="sxs-lookup"><span data-stu-id="b7b04-123">You can declare a generic type parameter contravariant by using the `in` keyword.</span></span> <span data-ttu-id="b7b04-124">逆变类型只能用作方法参数的类型，不能用作接口方法的返回类型。</span><span class="sxs-lookup"><span data-stu-id="b7b04-124">The contravariant type can be used only as a type of method arguments and not as a return type of interface methods.</span></span> <span data-ttu-id="b7b04-125">逆变类型还可用于泛型约束。</span><span class="sxs-lookup"><span data-stu-id="b7b04-125">The contravariant type can also be used for generic constraints.</span></span> <span data-ttu-id="b7b04-126">以下代码演示如何声明逆变接口，以及如何将泛型约束用于其方法之一。</span><span class="sxs-lookup"><span data-stu-id="b7b04-126">The following code shows how to declare a contravariant interface and use a generic constraint for one of its methods.</span></span>

```csharp
interface IContravariant<in A>
{
    void SetSomething(A sampleArg);
    void DoSomething<T>() where T : A;
    // The following statement generates a compiler error.
    // A GetSomething();
}
```

<span data-ttu-id="b7b04-127">此外，还可以在同一接口中同时支持协变和逆变，但需应用于不同的类型参数，如以下代码示例所示。</span><span class="sxs-lookup"><span data-stu-id="b7b04-127">It is also possible to support both covariance and contravariance in the same interface, but for different type parameters, as shown in the following code example.</span></span>

```csharp
interface IVariant<out R, in A>
{
    R GetSomething();
    void SetSomething(A sampleArg);
    R GetSetSomethings(A sampleArg);
}
```

## <a name="implementing-variant-generic-interfaces"></a><span data-ttu-id="b7b04-128">实现变体泛型接口</span><span class="sxs-lookup"><span data-stu-id="b7b04-128">Implementing Variant Generic Interfaces</span></span>

<span data-ttu-id="b7b04-129">在类中实现变体泛型接口时，所用语法和用于固定接口的语法相同。</span><span class="sxs-lookup"><span data-stu-id="b7b04-129">You implement variant generic interfaces in classes by using the same syntax that is used for invariant interfaces.</span></span> <span data-ttu-id="b7b04-130">以下代码示例演示如何在泛型类中实现协变接口。</span><span class="sxs-lookup"><span data-stu-id="b7b04-130">The following code example shows how to implement a covariant interface in a generic class.</span></span>

```csharp
interface ICovariant<out R>
{
    R GetSomething();
}
class SampleImplementation<R> : ICovariant<R>
{
    public R GetSomething()
    {
        // Some code.
        return default(R);
    }
}
```

<span data-ttu-id="b7b04-131">实现变体接口的类是固定类。</span><span class="sxs-lookup"><span data-stu-id="b7b04-131">Classes that implement variant interfaces are invariant.</span></span> <span data-ttu-id="b7b04-132">例如，考虑下面的代码。</span><span class="sxs-lookup"><span data-stu-id="b7b04-132">For example, consider the following code.</span></span>

```csharp
// The interface is covariant.
ICovariant<Button> ibutton = new SampleImplementation<Button>();
ICovariant<Object> iobj = ibutton;

// The class is invariant.
SampleImplementation<Button> button = new SampleImplementation<Button>();
// The following statement generates a compiler error
// because classes are invariant.
// SampleImplementation<Object> obj = button;
```

## <a name="extending-variant-generic-interfaces"></a><span data-ttu-id="b7b04-133">扩展变体泛型接口</span><span class="sxs-lookup"><span data-stu-id="b7b04-133">Extending Variant Generic Interfaces</span></span>

<span data-ttu-id="b7b04-134">扩展变体泛型接口时，必须使用 `in` 和 `out` 关键字来显式指定派生接口是否支持变体。</span><span class="sxs-lookup"><span data-stu-id="b7b04-134">When you extend a variant generic interface, you have to use the `in` and `out` keywords to explicitly specify whether the derived interface supports variance.</span></span> <span data-ttu-id="b7b04-135">编译器不会根据正在扩展的接口来推断变体。</span><span class="sxs-lookup"><span data-stu-id="b7b04-135">The compiler does not infer the variance from the interface that is being extended.</span></span> <span data-ttu-id="b7b04-136">例如，考虑以下接口。</span><span class="sxs-lookup"><span data-stu-id="b7b04-136">For example, consider the following interfaces.</span></span>

```csharp
interface ICovariant<out T> { }
interface IInvariant<T> : ICovariant<T> { }
interface IExtCovariant<out T> : ICovariant<T> { }
```

<span data-ttu-id="b7b04-137">尽管 `IInvariant<T>` 接口和 `IExtCovariant<out T>` 接口扩展的是同一个接口，但泛型类型参数 `T` 在前者中为固定参数，在后者中为协变参数。</span><span class="sxs-lookup"><span data-stu-id="b7b04-137">In the `IInvariant<T>` interface, the generic type parameter `T` is invariant, whereas in `IExtCovariant<out T>` the type parameter is covariant, although both interfaces extend the same interface.</span></span> <span data-ttu-id="b7b04-138">此规则也适用于逆变泛型类型参数。</span><span class="sxs-lookup"><span data-stu-id="b7b04-138">The same rule is applied to contravariant generic type parameters.</span></span>

<span data-ttu-id="b7b04-139">无论泛型类型参数 `T` 在接口中是协变还是逆变，都可以创建一个接口来扩展这两类接口，只要在扩展接口中，该 `T` 泛型类型参数为固定参数。</span><span class="sxs-lookup"><span data-stu-id="b7b04-139">You can create an interface that extends both the interface where the generic type parameter `T` is covariant and the interface where it is contravariant if in the extending interface the generic type parameter `T` is invariant.</span></span> <span data-ttu-id="b7b04-140">以下代码示例阐释了这一点。</span><span class="sxs-lookup"><span data-stu-id="b7b04-140">This is illustrated in the following code example.</span></span>

```csharp
interface ICovariant<out T> { }
interface IContravariant<in T> { }
interface IInvariant<T> : ICovariant<T>, IContravariant<T> { }
```

<span data-ttu-id="b7b04-141">但是，如果泛型类型参数 `T` 在一个接口中声明为协变，则无法在扩展接口中将其声明为逆变，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="b7b04-141">However, if a generic type parameter `T` is declared covariant in one interface, you cannot declare it contravariant in the extending interface, or vice versa.</span></span> <span data-ttu-id="b7b04-142">以下代码示例阐释了这一点。</span><span class="sxs-lookup"><span data-stu-id="b7b04-142">This is illustrated in the following code example.</span></span>

```csharp
interface ICovariant<out T> { }
// The following statement generates a compiler error.
// interface ICoContraVariant<in T> : ICovariant<T> { }
```

### <a name="avoiding-ambiguity"></a><span data-ttu-id="b7b04-143">避免多义性</span><span class="sxs-lookup"><span data-stu-id="b7b04-143">Avoiding Ambiguity</span></span>

<span data-ttu-id="b7b04-144">实现变体泛型接口时，变体有时可能会导致多义性。</span><span class="sxs-lookup"><span data-stu-id="b7b04-144">When you implement variant generic interfaces, variance can sometimes lead to ambiguity.</span></span> <span data-ttu-id="b7b04-145">应避免这样的多义性。</span><span class="sxs-lookup"><span data-stu-id="b7b04-145">Such ambiguity should be avoided.</span></span>

<span data-ttu-id="b7b04-146">例如，如果在一个类中使用不同的泛型类型参数来显式实现同一变体泛型接口，便会产生多义性。</span><span class="sxs-lookup"><span data-stu-id="b7b04-146">For example, if you explicitly implement the same variant generic interface with different generic type parameters in one class, it can create ambiguity.</span></span> <span data-ttu-id="b7b04-147">在这种情况下，编译器不会产生错误，但未指定将在运行时选择哪个接口实现。</span><span class="sxs-lookup"><span data-stu-id="b7b04-147">The compiler does not produce an error in this case, but it's not specified which interface implementation will be chosen at run time.</span></span> <span data-ttu-id="b7b04-148">这种多义性可能导致代码中出现小 bug。</span><span class="sxs-lookup"><span data-stu-id="b7b04-148">This ambiguity could lead to subtle bugs in your code.</span></span> <span data-ttu-id="b7b04-149">请考虑以下代码示例。</span><span class="sxs-lookup"><span data-stu-id="b7b04-149">Consider the following code example.</span></span>

```csharp
// Simple class hierarchy.
class Animal { }
class Cat : Animal { }
class Dog : Animal { }

// This class introduces ambiguity
// because IEnumerable<out T> is covariant.
class Pets : IEnumerable<Cat>, IEnumerable<Dog>
{
    IEnumerator<Cat> IEnumerable<Cat>.GetEnumerator()
    {
        Console.WriteLine("Cat");
        // Some code.
        return null;
    }

    IEnumerator IEnumerable.GetEnumerator()
    {
        // Some code.
        return null;
    }

    IEnumerator<Dog> IEnumerable<Dog>.GetEnumerator()
    {
        Console.WriteLine("Dog");
        // Some code.
        return null;
    }
}
class Program
{
    public static void Test()
    {
        IEnumerable<Animal> pets = new Pets();
        pets.GetEnumerator();
    }
}
```

<span data-ttu-id="b7b04-150">在此示例中，没有指定 `pets.GetEnumerator` 方法如何在 `Cat` 和 `Dog` 之间选择。</span><span class="sxs-lookup"><span data-stu-id="b7b04-150">In this example, it is unspecified how the `pets.GetEnumerator` method chooses between `Cat` and `Dog`.</span></span> <span data-ttu-id="b7b04-151">这可能导致代码中出现问题。</span><span class="sxs-lookup"><span data-stu-id="b7b04-151">This could cause problems in your code.</span></span>

## <a name="see-also"></a><span data-ttu-id="b7b04-152">请参阅</span><span class="sxs-lookup"><span data-stu-id="b7b04-152">See also</span></span>

- [<span data-ttu-id="b7b04-153">泛型接口中的变体 (C#)</span><span class="sxs-lookup"><span data-stu-id="b7b04-153">Variance in Generic Interfaces (C#)</span></span>](./variance-in-generic-interfaces.md)
- [<span data-ttu-id="b7b04-154">对 Func 和 Action 泛型委托使用变体 (C#)</span><span class="sxs-lookup"><span data-stu-id="b7b04-154">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)

---
title: System.Delegate 和 `delegate` 关键字
description: 详细介绍 .NET 中支持委托的类以及这些类映射到“delegate”关键字的方式。
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 9df8ad68f6bfa62863ee047875b6419fc81ad779
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062458"
---
# <a name="systemdelegate-and-the-delegate-keyword"></a><span data-ttu-id="76bff-103">System.Delegate 和 `delegate` 关键字</span><span class="sxs-lookup"><span data-stu-id="76bff-103">System.Delegate and the `delegate` keyword</span></span>

[<span data-ttu-id="76bff-104">上一页</span><span class="sxs-lookup"><span data-stu-id="76bff-104">Previous</span></span>](delegates-overview.md)

<span data-ttu-id="76bff-105">本文介绍 .NET 中支持委托的类以及这些类映射到 `delegate` 关键字的方式。</span><span class="sxs-lookup"><span data-stu-id="76bff-105">This article covers the classes in .NET that support delegates, and how those map to the `delegate` keyword.</span></span>

## <a name="define-delegate-types"></a><span data-ttu-id="76bff-106">定义委托类型</span><span class="sxs-lookup"><span data-stu-id="76bff-106">Define delegate types</span></span>

<span data-ttu-id="76bff-107">我们从“delegate”关键字开始，因为这是你在使用委托时会使用的主要方法。</span><span class="sxs-lookup"><span data-stu-id="76bff-107">Let's start with the 'delegate' keyword, because that's primarily what you will use as you work with delegates.</span></span> <span data-ttu-id="76bff-108">编译器在你使用 `delegate` 关键字时生成的代码会映射到调用 <xref:System.Delegate> 和 <xref:System.MulticastDelegate> 类的成员的方法调用。</span><span class="sxs-lookup"><span data-stu-id="76bff-108">The code that the compiler generates when you use the `delegate` keyword will map to method calls that invoke members of the <xref:System.Delegate> and <xref:System.MulticastDelegate> classes.</span></span>

<span data-ttu-id="76bff-109">可使用类似于定义方法签名的语法来定义委托类型。</span><span class="sxs-lookup"><span data-stu-id="76bff-109">You define a delegate type using syntax that is similar to defining a method signature.</span></span> <span data-ttu-id="76bff-110">只需向定义添加 `delegate` 关键字即可。</span><span class="sxs-lookup"><span data-stu-id="76bff-110">You just add the `delegate` keyword to the definition.</span></span>

<span data-ttu-id="76bff-111">我们继续使用 List.Sort() 方法作为示例。</span><span class="sxs-lookup"><span data-stu-id="76bff-111">Let's continue to use the List.Sort() method as our example.</span></span> <span data-ttu-id="76bff-112">第一步是为比较委托创建类型：</span><span class="sxs-lookup"><span data-stu-id="76bff-112">The first step is to create a type for the comparison delegate:</span></span>

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

<span data-ttu-id="76bff-113">编译器会生成一个类，它派生自与使用的签名匹配的 `System.Delegate`（在此例中，是返回一个整数并具有两个参数的方法）。</span><span class="sxs-lookup"><span data-stu-id="76bff-113">The compiler generates a class, derived from `System.Delegate` that matches the signature used (in this case, a method that returns an integer, and has two arguments).</span></span> <span data-ttu-id="76bff-114">该委托的类型是 `Comparison`。</span><span class="sxs-lookup"><span data-stu-id="76bff-114">The type of that delegate is `Comparison`.</span></span> <span data-ttu-id="76bff-115">`Comparison` 委托类型是泛型类型。</span><span class="sxs-lookup"><span data-stu-id="76bff-115">The `Comparison` delegate type is a generic type.</span></span> <span data-ttu-id="76bff-116">有关泛型的详细信息，请参阅[此处](programming-guide/generics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="76bff-116">For details on generics see [here](programming-guide/generics/index.md).</span></span>

<span data-ttu-id="76bff-117">请注意，语法可能看起来像是声明变量，但它实际上是声明类型  。</span><span class="sxs-lookup"><span data-stu-id="76bff-117">Notice that the syntax may appear as though it is declaring a variable, but it is actually declaring a *type*.</span></span> <span data-ttu-id="76bff-118">可以在类中、直接在命名空间中、甚至是在全局命名空间中定义委托类型。</span><span class="sxs-lookup"><span data-stu-id="76bff-118">You can define delegate types inside classes, directly inside namespaces, or even in the global namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="76bff-119">建议不要直接在全局命名空间中声明委托类型（或其他类型）。</span><span class="sxs-lookup"><span data-stu-id="76bff-119">Declaring delegate types (or other types) directly in the global namespace is not recommended.</span></span>

<span data-ttu-id="76bff-120">编译器还会为此新类型生成添加和移除处理程序，以便此类的客户端可以对实例的调用列表添加和移除方法。</span><span class="sxs-lookup"><span data-stu-id="76bff-120">The compiler also generates add and remove handlers for this new type so that clients of this class can add and remove methods from an instance's invocation list.</span></span> <span data-ttu-id="76bff-121">编译器会强制所添加或移除的方法的签名与声明该方法时使用的签名匹配。</span><span class="sxs-lookup"><span data-stu-id="76bff-121">The compiler will enforce that the signature of the method being added or removed matches the signature used when declaring the method.</span></span>

## <a name="declare-instances-of-delegates"></a><span data-ttu-id="76bff-122">声明委托的实例</span><span class="sxs-lookup"><span data-stu-id="76bff-122">Declare instances of delegates</span></span>

<span data-ttu-id="76bff-123">定义委托之后，可以创建该类型的实例。</span><span class="sxs-lookup"><span data-stu-id="76bff-123">After defining the delegate, you can create an instance of that type.</span></span>
<span data-ttu-id="76bff-124">与 C# 中的所有变量一样，不能直接在命名空间中或全局命名空间中声明委托实例。</span><span class="sxs-lookup"><span data-stu-id="76bff-124">Like all variables in C#, you cannot declare delegate instances directly in a namespace, or in the global namespace.</span></span>

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

<span data-ttu-id="76bff-125">变量的类型是 `Comparison<T>`（前面定义的委托类型）。</span><span class="sxs-lookup"><span data-stu-id="76bff-125">The type of the variable is `Comparison<T>`, the delegate type defined earlier.</span></span> <span data-ttu-id="76bff-126">变量的名称是 `comparator`。</span><span class="sxs-lookup"><span data-stu-id="76bff-126">The name of the variable is `comparator`.</span></span>

 <span data-ttu-id="76bff-127">上面的代码片段在类中声明了一个成员变量。</span><span class="sxs-lookup"><span data-stu-id="76bff-127">That code snippet above declared a member variable inside a class.</span></span> <span data-ttu-id="76bff-128">还可以声明作为局部变量或方法参数的委托变量。</span><span class="sxs-lookup"><span data-stu-id="76bff-128">You can also declare delegate variables that are local variables, or arguments to methods.</span></span>

## <a name="invoke-delegates"></a><span data-ttu-id="76bff-129">调用委托</span><span class="sxs-lookup"><span data-stu-id="76bff-129">Invoke delegates</span></span>

<span data-ttu-id="76bff-130">可通过调用某个委托来调用处于该委托调用列表中的方法。</span><span class="sxs-lookup"><span data-stu-id="76bff-130">You invoke the methods that are in the invocation list of a delegate by calling that delegate.</span></span> <span data-ttu-id="76bff-131">在 `Sort()` 方法内部，代码会调用比较方法以确定放置对象的顺序：</span><span class="sxs-lookup"><span data-stu-id="76bff-131">Inside the `Sort()` method, the code will call the comparison method to determine which order to place objects:</span></span>

```csharp
int result = comparator(left, right);
```

<span data-ttu-id="76bff-132">在上面的行中，代码会调用  附加到委托的方法。</span><span class="sxs-lookup"><span data-stu-id="76bff-132">In the line above, the code *invokes* the method attached to the delegate.</span></span>
<span data-ttu-id="76bff-133">可将变量视为方法名称，并使用普通方法调用语法调用它。</span><span class="sxs-lookup"><span data-stu-id="76bff-133">You treat the variable as a method name, and invoke it using normal method call syntax.</span></span>

<span data-ttu-id="76bff-134">该代码行进行了不安全假设：不保证目标已添加到委托。</span><span class="sxs-lookup"><span data-stu-id="76bff-134">That line of code makes an unsafe assumption: There's no guarantee that a target has been added to the delegate.</span></span> <span data-ttu-id="76bff-135">如果未附加目标，则上面的行会导致引发 `NullReferenceException`。</span><span class="sxs-lookup"><span data-stu-id="76bff-135">If no targets have been attached, the line above would cause a `NullReferenceException` to be thrown.</span></span> <span data-ttu-id="76bff-136">用于解决此问题的惯例比简单 null 检查更加复杂，在此[系列](delegates-patterns.md)的后面部分中会进行介绍。</span><span class="sxs-lookup"><span data-stu-id="76bff-136">The idioms used to address this problem are more complicated than a simple null-check, and are covered later in this [series](delegates-patterns.md).</span></span>

## <a name="assign-add-and-remove-invocation-targets"></a><span data-ttu-id="76bff-137">分配、添加和删除调用目标</span><span class="sxs-lookup"><span data-stu-id="76bff-137">Assign, add, and remove invocation targets</span></span>

<span data-ttu-id="76bff-138">这是委托类型的定义方式，以及声明和调用委托实例的方式。</span><span class="sxs-lookup"><span data-stu-id="76bff-138">That's how a delegate type is defined, and how delegate instances are declared and invoked.</span></span>

<span data-ttu-id="76bff-139">要使用 `List.Sort()` 方法的开发人员需要定义签名与委托类型定义匹配的方法，并将它分配给排序方法使用的委托。</span><span class="sxs-lookup"><span data-stu-id="76bff-139">Developers that want to use the `List.Sort()` method need to define a method whose signature matches the delegate type definition, and assign it to the delegate used by the sort method.</span></span> <span data-ttu-id="76bff-140">此分配会将方法添加到该委托对象的调用列表。</span><span class="sxs-lookup"><span data-stu-id="76bff-140">This assignment adds the method to the invocation list of that delegate object.</span></span>

<span data-ttu-id="76bff-141">假设要按长度对字符串列表进行排序。</span><span class="sxs-lookup"><span data-stu-id="76bff-141">Suppose you wanted to sort a list of strings by their length.</span></span> <span data-ttu-id="76bff-142">比较函数可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="76bff-142">Your comparison function might be the following:</span></span>

```csharp
private static int CompareLength(string left, string right) =>
    left.Length.CompareTo(right.Length);
```

<span data-ttu-id="76bff-143">方法声明为私有方法。</span><span class="sxs-lookup"><span data-stu-id="76bff-143">The method is declared as a private method.</span></span> <span data-ttu-id="76bff-144">这没有什么不对。</span><span class="sxs-lookup"><span data-stu-id="76bff-144">That's fine.</span></span> <span data-ttu-id="76bff-145">你可能不希望此方法是公共接口的一部分。</span><span class="sxs-lookup"><span data-stu-id="76bff-145">You may not want this method to be part of your public interface.</span></span> <span data-ttu-id="76bff-146">它仍可以在附加到委托时用作比较方法。</span><span class="sxs-lookup"><span data-stu-id="76bff-146">It can still be used as the comparison method when attached to a delegate.</span></span> <span data-ttu-id="76bff-147">调用代码会将此方法附加到委托对象的目标列表，并且可以通过该委托访问它。</span><span class="sxs-lookup"><span data-stu-id="76bff-147">The calling code will have this method attached to the target list of the delegate object, and can access it through that delegate.</span></span>

<span data-ttu-id="76bff-148">通过将该方法传递给 `List.Sort()` 方法来创建该关系：</span><span class="sxs-lookup"><span data-stu-id="76bff-148">You create that relationship by passing that method to the `List.Sort()` method:</span></span>

```csharp
phrases.Sort(CompareLength);
```

<span data-ttu-id="76bff-149">请注意，在不带括号的情况下使用方法名称。</span><span class="sxs-lookup"><span data-stu-id="76bff-149">Notice that the method name is used, without parentheses.</span></span> <span data-ttu-id="76bff-150">将方法用作参数会告知编译器将方法引用转换为可以用作委托调用目标的引用，并将该方法作为调用目标进行附加。</span><span class="sxs-lookup"><span data-stu-id="76bff-150">Using the method as an argument tells the compiler to convert the method reference into a reference that can be used as a delegate invocation target, and attach that method as an invocation target.</span></span>

<span data-ttu-id="76bff-151">还可以通过声明“`Comparison<string>`”类型的变量并进行分配来显式执行操作：</span><span class="sxs-lookup"><span data-stu-id="76bff-151">You could also have been explicit by declaring a variable of type `Comparison<string>` and doing an assignment:</span></span>

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

<span data-ttu-id="76bff-152">在用作委托目标的方法是小型方法的用法中，经常使用 [lambda 表达式](language-reference/operators/lambda-expressions.md)语法来执行分配：</span><span class="sxs-lookup"><span data-stu-id="76bff-152">In uses where the method being used as a delegate target is a small method, it's common to use [lambda expression](language-reference/operators/lambda-expressions.md) syntax to perform the assignment:</span></span>

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

<span data-ttu-id="76bff-153">[后续部分](delegates-patterns.md)中更详细地介绍了如何对委托目标使用 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="76bff-153">Using lambda expressions for delegate targets is covered more in a [later section](delegates-patterns.md).</span></span>

<span data-ttu-id="76bff-154">Sort() 示例通常将单个目标方法附加到委托。</span><span class="sxs-lookup"><span data-stu-id="76bff-154">The Sort() example typically attaches a single target method to the delegate.</span></span> <span data-ttu-id="76bff-155">但是，委托对象支持将多个目标方法附加到委托对象的调用列表。</span><span class="sxs-lookup"><span data-stu-id="76bff-155">However, delegate objects do support invocation lists that have multiple target methods attached to a delegate object.</span></span>

## <a name="delegate-and-multicastdelegate-classes"></a><span data-ttu-id="76bff-156">委托和 MulticastDelegate 类</span><span class="sxs-lookup"><span data-stu-id="76bff-156">Delegate and MulticastDelegate classes</span></span>

<span data-ttu-id="76bff-157">上面介绍的语言支持可提供在使用委托时通常需要的功能和支持。</span><span class="sxs-lookup"><span data-stu-id="76bff-157">The language support described above provides the features and support you'll typically need to work with delegates.</span></span> <span data-ttu-id="76bff-158">这些功能采用 .NET Core Framework 中的两个类进行构建：<xref:System.Delegate> 和 <xref:System.MulticastDelegate>。</span><span class="sxs-lookup"><span data-stu-id="76bff-158">These features are built on two classes in the .NET Core framework: <xref:System.Delegate> and <xref:System.MulticastDelegate>.</span></span>

<span data-ttu-id="76bff-159">`System.Delegate` 类及其单个直接子类 `System.MulticastDelegate` 可提供框架支持，以便创建委托、将方法注册为委托目标以及调用注册为委托目标的所有方法。</span><span class="sxs-lookup"><span data-stu-id="76bff-159">The `System.Delegate` class and its single direct subclass, `System.MulticastDelegate`, provide the framework support for creating delegates, registering methods as delegate targets, and invoking all methods that are registered as a delegate target.</span></span>

<span data-ttu-id="76bff-160">有趣的是，`System.Delegate` 和 `System.MulticastDelegate` 类本身不是委托类型。</span><span class="sxs-lookup"><span data-stu-id="76bff-160">Interestingly, the `System.Delegate` and `System.MulticastDelegate` classes are not themselves delegate types.</span></span> <span data-ttu-id="76bff-161">它们为所有特定委托类型提供基础。</span><span class="sxs-lookup"><span data-stu-id="76bff-161">They do provide the basis for all specific delegate types.</span></span> <span data-ttu-id="76bff-162">相同的语言设计过程要求不能声明派生自 `Delegate` 或 `MulticastDelegate` 的类。</span><span class="sxs-lookup"><span data-stu-id="76bff-162">That same language design process mandated that you cannot declare a class that derives from `Delegate` or `MulticastDelegate`.</span></span> <span data-ttu-id="76bff-163">C# 语言规则禁止这样做。</span><span class="sxs-lookup"><span data-stu-id="76bff-163">The C# language rules prohibit it.</span></span>

<span data-ttu-id="76bff-164">相反，C# 编译器会在你使用 C# 语言关键字声明委托类型时，创建派生自 `MulticastDelegate` 的类的实例。</span><span class="sxs-lookup"><span data-stu-id="76bff-164">Instead, the C# compiler creates instances of a class derived from `MulticastDelegate` when you use the C# language keyword to declare delegate types.</span></span>

<span data-ttu-id="76bff-165">此设计起源于 C# 和 .NET 的第一版。</span><span class="sxs-lookup"><span data-stu-id="76bff-165">This design has its roots in the first release of C# and .NET.</span></span> <span data-ttu-id="76bff-166">设计团队的一个目标是确保在使用委托时，语言强制实施类型安全。</span><span class="sxs-lookup"><span data-stu-id="76bff-166">One goal for the design team was to ensure that the language enforced type safety when using delegates.</span></span> <span data-ttu-id="76bff-167">这意味着确保使用正确类型和数量的参数来调用委托。</span><span class="sxs-lookup"><span data-stu-id="76bff-167">That meant ensuring that delegates were invoked with the right type and number of arguments.</span></span> <span data-ttu-id="76bff-168">并且在编译时正确指示任何返回类型。</span><span class="sxs-lookup"><span data-stu-id="76bff-168">And, that any return type was correctly indicated at compile time.</span></span> <span data-ttu-id="76bff-169">委托是 1.0 .NET 版本的一部分（在泛型出现之前）。</span><span class="sxs-lookup"><span data-stu-id="76bff-169">Delegates were part of the 1.0 .NET release, which was before generics.</span></span>

<span data-ttu-id="76bff-170">强制实施此类型安全的最佳方法是让编辑器创建表示所使用的方法签名的具体委托类。</span><span class="sxs-lookup"><span data-stu-id="76bff-170">The best way to enforce this type safety was for the compiler to create the concrete delegate classes that represented the method signature being used.</span></span>

<span data-ttu-id="76bff-171">即使不能直接创建派生类，也会使用对这些类定义的方法。</span><span class="sxs-lookup"><span data-stu-id="76bff-171">Even though you cannot create derived classes directly, you will use the methods defined on these classes.</span></span> <span data-ttu-id="76bff-172">我们来讨论一下在使用委托时会使用的最常见方法。</span><span class="sxs-lookup"><span data-stu-id="76bff-172">Let's go through the most common methods that you will use when you work with delegates.</span></span>

<span data-ttu-id="76bff-173">要记住的首要且最重要的事实是，使用的每个委托都派生自 `MulticastDelegate`。</span><span class="sxs-lookup"><span data-stu-id="76bff-173">The first, most important fact to remember is that every delegate you work with is derived from `MulticastDelegate`.</span></span> <span data-ttu-id="76bff-174">多播委托意味着通过委托进行调用时，可以调用多个方法目标。</span><span class="sxs-lookup"><span data-stu-id="76bff-174">A multicast delegate means that more than one method target can be invoked when invoking through a delegate.</span></span> <span data-ttu-id="76bff-175">原始设计考虑区分只能附加并调用一个目标方法的委托与可以附加并调用多个目标方法的委托。</span><span class="sxs-lookup"><span data-stu-id="76bff-175">The original design considered making a distinction between delegates where only one target method could be attached and invoked, and delegates where multiple target methods could be attached and invoked.</span></span> <span data-ttu-id="76bff-176">该区分被证明在实际中不如最初设想那么有用。</span><span class="sxs-lookup"><span data-stu-id="76bff-176">That distinction proved to be less useful in practice than originally thought.</span></span> <span data-ttu-id="76bff-177">已创建了两个不同的类，并且自初始公开发行以来便一直处于框架中。</span><span class="sxs-lookup"><span data-stu-id="76bff-177">The two different classes were already created, and have been in the framework since its initial public release.</span></span>

<span data-ttu-id="76bff-178">对委托最常使用的方法是 `Invoke()` 和 `BeginInvoke()` / `EndInvoke()`。</span><span class="sxs-lookup"><span data-stu-id="76bff-178">The methods that you will use the most with delegates are `Invoke()` and `BeginInvoke()` / `EndInvoke()`.</span></span> <span data-ttu-id="76bff-179">`Invoke()` 会调用已附加到特定委托实例的所有方法。</span><span class="sxs-lookup"><span data-stu-id="76bff-179">`Invoke()` will invoke all the methods that have been attached to a particular delegate instance.</span></span> <span data-ttu-id="76bff-180">如上面所见，通常会通过对委托变量使用方法调用语法来调用委托。</span><span class="sxs-lookup"><span data-stu-id="76bff-180">As you saw above, you typically invoke delegates using the method call syntax on the delegate variable.</span></span> <span data-ttu-id="76bff-181">如在[此系列后面部分](delegates-patterns.md)中所见，一些模式可直接使用这些方法。</span><span class="sxs-lookup"><span data-stu-id="76bff-181">As you'll see [later in this series](delegates-patterns.md), there are patterns that work directly with these methods.</span></span>

<span data-ttu-id="76bff-182">现在你已了解支持委托的语言语法和类，我们来看一下如何使用、创建和调用强类型委托。</span><span class="sxs-lookup"><span data-stu-id="76bff-182">Now that you've seen the language syntax and the classes that support delegates, let's examine how strongly typed delegates are used, created, and invoked.</span></span>

[<span data-ttu-id="76bff-183">下一部分</span><span class="sxs-lookup"><span data-stu-id="76bff-183">Next</span></span>](delegates-strongly-typed.md)

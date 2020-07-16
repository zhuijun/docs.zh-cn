---
title: C# 7.3 中的新增功能
description: C# 7.3 中的新增功能概述
ms.date: 05/16/2018
ms.openlocfilehash: cd8f554516fb5078d9d2ed1eec787f36e8f4c7a7
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174752"
---
# <a name="whats-new-in-c-73"></a><span data-ttu-id="ce34b-103">C# 7.3 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="ce34b-103">What's new in C# 7.3</span></span>

<span data-ttu-id="ce34b-104">C# 7.3 版本有两个主要主题。</span><span class="sxs-lookup"><span data-stu-id="ce34b-104">There are two main themes to the C# 7.3 release.</span></span> <span data-ttu-id="ce34b-105">第一个主题提供使安全代码的性能与不安全代码的性能一样好的功能。</span><span class="sxs-lookup"><span data-stu-id="ce34b-105">One theme provides features that enable safe code to be as performant as unsafe code.</span></span> <span data-ttu-id="ce34b-106">第二个主题提供对现有功能的增量改进。</span><span class="sxs-lookup"><span data-stu-id="ce34b-106">The second theme provides incremental improvements to existing features.</span></span> <span data-ttu-id="ce34b-107">此外，在此版本中添加了新的编译器选项。</span><span class="sxs-lookup"><span data-stu-id="ce34b-107">In addition, new compiler options were added in this release.</span></span>

<span data-ttu-id="ce34b-108">以下新增功能支持使安全代码获得更好的性能的主题：</span><span class="sxs-lookup"><span data-stu-id="ce34b-108">The following new features support the theme of better performance for safe code:</span></span>

- <span data-ttu-id="ce34b-109">无需固定即可访问固定的字段。</span><span class="sxs-lookup"><span data-stu-id="ce34b-109">You can access fixed fields without pinning.</span></span>
- <span data-ttu-id="ce34b-110">可以重新分配 `ref` 本地变量。</span><span class="sxs-lookup"><span data-stu-id="ce34b-110">You can reassign `ref` local variables.</span></span>
- <span data-ttu-id="ce34b-111">可以使用 `stackalloc` 数组上的初始值设定项。</span><span class="sxs-lookup"><span data-stu-id="ce34b-111">You can use initializers on `stackalloc` arrays.</span></span>
- <span data-ttu-id="ce34b-112">可以对支持模式的任何类型使用 `fixed` 语句。</span><span class="sxs-lookup"><span data-stu-id="ce34b-112">You can use `fixed` statements with any type that supports a pattern.</span></span>
- <span data-ttu-id="ce34b-113">可以使用其他泛型约束。</span><span class="sxs-lookup"><span data-stu-id="ce34b-113">You can use additional generic constraints.</span></span>

<span data-ttu-id="ce34b-114">对现有功能进行了以下增强：</span><span class="sxs-lookup"><span data-stu-id="ce34b-114">The following enhancements were made to existing features:</span></span>

- <span data-ttu-id="ce34b-115">可以使用元组类型测试 `==` 和 `!=`。</span><span class="sxs-lookup"><span data-stu-id="ce34b-115">You can test `==` and `!=` with tuple types.</span></span>
- <span data-ttu-id="ce34b-116">可以在多个位置使用表达式变量。</span><span class="sxs-lookup"><span data-stu-id="ce34b-116">You can use expression variables in more locations.</span></span>
- <span data-ttu-id="ce34b-117">可以将属性附加到自动实现的属性的支持字段。</span><span class="sxs-lookup"><span data-stu-id="ce34b-117">You may attach attributes to the backing field of auto-implemented properties.</span></span>
- <span data-ttu-id="ce34b-118">由 `in` 区分的参数的方法解析得到了改进。</span><span class="sxs-lookup"><span data-stu-id="ce34b-118">Method resolution when arguments differ by `in` has been improved.</span></span>
- <span data-ttu-id="ce34b-119">重载解析的多义情况现在变得更少。</span><span class="sxs-lookup"><span data-stu-id="ce34b-119">Overload resolution now has fewer ambiguous cases.</span></span>

<span data-ttu-id="ce34b-120">新的编译器选项为：</span><span class="sxs-lookup"><span data-stu-id="ce34b-120">The new compiler options are:</span></span>

- <span data-ttu-id="ce34b-121">`-publicsign`，用于启用程序集的开放源代码软件 (OSS) 签名。</span><span class="sxs-lookup"><span data-stu-id="ce34b-121">`-publicsign` to enable Open Source Software (OSS) signing of assemblies.</span></span>
- <span data-ttu-id="ce34b-122">`-pathmap`用于提供源目录的映射。</span><span class="sxs-lookup"><span data-stu-id="ce34b-122">`-pathmap` to provide a mapping for source directories.</span></span>

<span data-ttu-id="ce34b-123">本文的剩余部分提供了详细信息和链接，以便你详细了解每项改进。</span><span class="sxs-lookup"><span data-stu-id="ce34b-123">The remainder of this article provides details and links to learn more about each of the improvements.</span></span> <span data-ttu-id="ce34b-124">可以使用 `dotnet try` 全局工具在环境中浏览这些功能：</span><span class="sxs-lookup"><span data-stu-id="ce34b-124">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="ce34b-125">安装 [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) 全局工具。</span><span class="sxs-lookup"><span data-stu-id="ce34b-125">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="ce34b-126">克隆 [dotnet/try-samples](https://github.com/dotnet/try-samples) 存储库。</span><span class="sxs-lookup"><span data-stu-id="ce34b-126">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="ce34b-127">将当前目录设置为 try-samples 存储库的 csharp7 子目录 。</span><span class="sxs-lookup"><span data-stu-id="ce34b-127">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="ce34b-128">运行 `dotnet try`。</span><span class="sxs-lookup"><span data-stu-id="ce34b-128">Run `dotnet try`.</span></span>

## <a name="enabling-more-efficient-safe-code"></a><span data-ttu-id="ce34b-129">启用更高效的安全代码</span><span class="sxs-lookup"><span data-stu-id="ce34b-129">Enabling more efficient safe code</span></span>

<span data-ttu-id="ce34b-130">你应能够安全地编写性能与不安全代码一样好的 C# 代码。</span><span class="sxs-lookup"><span data-stu-id="ce34b-130">You should be able to write C# code safely that performs as well as unsafe code.</span></span> <span data-ttu-id="ce34b-131">安全代码可避免错误类，例如缓冲区溢出、杂散指针和其他内存访问错误。</span><span class="sxs-lookup"><span data-stu-id="ce34b-131">Safe code avoids classes of errors, such as buffer overruns, stray pointers, and other memory access errors.</span></span> <span data-ttu-id="ce34b-132">这些新功能扩展了可验证安全代码的功能。</span><span class="sxs-lookup"><span data-stu-id="ce34b-132">These new features expand the capabilities of verifiable safe code.</span></span> <span data-ttu-id="ce34b-133">努力使用安全结构编写更多代码。</span><span class="sxs-lookup"><span data-stu-id="ce34b-133">Strive to write more of your code using safe constructs.</span></span> <span data-ttu-id="ce34b-134">这些功能使其更容易实现。</span><span class="sxs-lookup"><span data-stu-id="ce34b-134">These features make that easier.</span></span>

### <a name="indexing-fixed-fields-does-not-require-pinning"></a><span data-ttu-id="ce34b-135">索引 `fixed` 字段不需要进行固定</span><span class="sxs-lookup"><span data-stu-id="ce34b-135">Indexing `fixed` fields does not require pinning</span></span>

<span data-ttu-id="ce34b-136">请考虑此结构：</span><span class="sxs-lookup"><span data-stu-id="ce34b-136">Consider this struct:</span></span>

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

<span data-ttu-id="ce34b-137">在早期版本的 C# 中，需要固定变量才能访问属于 `myFixedField` 的整数之一。</span><span class="sxs-lookup"><span data-stu-id="ce34b-137">In earlier versions of C#, you needed to pin a variable to access one of the integers that are part of `myFixedField`.</span></span> <span data-ttu-id="ce34b-138">现在，以下代码进行编译，而不将变量 `p` 固定到单独的 `fixed` 语句中：</span><span class="sxs-lookup"><span data-stu-id="ce34b-138">Now, the following code compiles without pinning the variable `p` inside a separate `fixed` statement:</span></span>

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        int p = s.myFixedField[5];
    }
}
```

<span data-ttu-id="ce34b-139">变量 `p` 访问 `myFixedField` 中的一个元素。</span><span class="sxs-lookup"><span data-stu-id="ce34b-139">The variable `p` accesses one element in `myFixedField`.</span></span> <span data-ttu-id="ce34b-140">无需声明单独的 `int*` 变量。</span><span class="sxs-lookup"><span data-stu-id="ce34b-140">You don't need to declare a separate `int*` variable.</span></span> <span data-ttu-id="ce34b-141">请注意，你仍然需要 `unsafe` 上下文。</span><span class="sxs-lookup"><span data-stu-id="ce34b-141">Note that you still need an `unsafe` context.</span></span> <span data-ttu-id="ce34b-142">在早期版本的 C# 中，需要声明第二个固定的指针：</span><span class="sxs-lookup"><span data-stu-id="ce34b-142">In earlier versions of C#, you need to declare a second fixed pointer:</span></span>

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        fixed (int* ptr = s.myFixedField)
        {
            int p = ptr[5];
        }
    }
}
```

<span data-ttu-id="ce34b-143">有关详细信息，请参阅有关 [`fixed` 语句](../language-reference/keywords/fixed-statement.md)的文章。</span><span class="sxs-lookup"><span data-stu-id="ce34b-143">For more information, see the article on the [`fixed` statement](../language-reference/keywords/fixed-statement.md).</span></span>

### <a name="ref-local-variables-may-be-reassigned"></a><span data-ttu-id="ce34b-144">可能会重新分配 `ref` 局部变量</span><span class="sxs-lookup"><span data-stu-id="ce34b-144">`ref` local variables may be reassigned</span></span>

<span data-ttu-id="ce34b-145">现在，在对 `ref` 局部变量进行初始化后，可能会对其重新分配，以引用不同的实例。</span><span class="sxs-lookup"><span data-stu-id="ce34b-145">Now, `ref` locals may be reassigned to refer to different instances after being initialized.</span></span> <span data-ttu-id="ce34b-146">以下代码现在编译：</span><span class="sxs-lookup"><span data-stu-id="ce34b-146">The following code now compiles:</span></span>

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

<span data-ttu-id="ce34b-147">有关详细信息，请参阅有关 [`ref` 返回和 `ref` 局部变量](../programming-guide/classes-and-structs/ref-returns.md)以及 [`foreach`](../language-reference/keywords/foreach-in.md) 的文章。</span><span class="sxs-lookup"><span data-stu-id="ce34b-147">For more information, see the article on [`ref` returns and `ref` locals](../programming-guide/classes-and-structs/ref-returns.md), and the article on [`foreach`](../language-reference/keywords/foreach-in.md).</span></span>

### <a name="stackalloc-arrays-support-initializers"></a><span data-ttu-id="ce34b-148">`stackalloc` 数组支持初始值设定项</span><span class="sxs-lookup"><span data-stu-id="ce34b-148">`stackalloc` arrays support initializers</span></span>

<span data-ttu-id="ce34b-149">当你对数组中的元素的值进行初始值设定时，你已能够指定该值：</span><span class="sxs-lookup"><span data-stu-id="ce34b-149">You've been able to specify the values for elements in an array when you initialize it:</span></span>

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

<span data-ttu-id="ce34b-150">现在，可向使用 `stackalloc` 进行声明的数组应用同一语法：</span><span class="sxs-lookup"><span data-stu-id="ce34b-150">Now, that same syntax can be applied to arrays that are declared with `stackalloc`:</span></span>

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

<span data-ttu-id="ce34b-151">有关详细信息，请参阅[`stackalloc`运算符](../language-reference/operators/stackalloc.md)一文。</span><span class="sxs-lookup"><span data-stu-id="ce34b-151">For more information, see the [`stackalloc` operator](../language-reference/operators/stackalloc.md) article.</span></span>

### <a name="more-types-support-the-fixed-statement"></a><span data-ttu-id="ce34b-152">更多类型支持 `fixed` 语句</span><span class="sxs-lookup"><span data-stu-id="ce34b-152">More types support the `fixed` statement</span></span>

<span data-ttu-id="ce34b-153">`fixed` 语句支持有限的一组类型。</span><span class="sxs-lookup"><span data-stu-id="ce34b-153">The `fixed` statement supported a limited set of types.</span></span> <span data-ttu-id="ce34b-154">从 C# 7.3 开始，任何包含返回 `ref T` 或 `ref readonly T` 的 `GetPinnableReference()` 方法的类型均有可能为 `fixed`。</span><span class="sxs-lookup"><span data-stu-id="ce34b-154">Starting with C# 7.3, any type that contains a `GetPinnableReference()` method that returns a `ref T` or `ref readonly T` may be `fixed`.</span></span> <span data-ttu-id="ce34b-155">添加此功能意味着 `fixed` 可与 <xref:System.Span%601?displayProperty=nameWithType> 和相关类型配合使用。</span><span class="sxs-lookup"><span data-stu-id="ce34b-155">Adding this feature means that `fixed` can be used with <xref:System.Span%601?displayProperty=nameWithType> and related types.</span></span>

<span data-ttu-id="ce34b-156">有关详细信息，请参阅语言参考中的 [`fixed` 语句](../language-reference/keywords/fixed-statement.md)一文。</span><span class="sxs-lookup"><span data-stu-id="ce34b-156">For more information, see the [`fixed` statement](../language-reference/keywords/fixed-statement.md) article in the language reference.</span></span>

### <a name="enhanced-generic-constraints"></a><span data-ttu-id="ce34b-157">增强的泛型约束</span><span class="sxs-lookup"><span data-stu-id="ce34b-157">Enhanced generic constraints</span></span>

<span data-ttu-id="ce34b-158">现在，可以将类型 <xref:System.Enum?displayProperty=nameWithType> 或 <xref:System.Delegate?displayProperty=nameWithType> 指定为类型参数的基类约束。</span><span class="sxs-lookup"><span data-stu-id="ce34b-158">You can now specify the type <xref:System.Enum?displayProperty=nameWithType> or <xref:System.Delegate?displayProperty=nameWithType> as base class constraints for a type parameter.</span></span>

<span data-ttu-id="ce34b-159">现在也可以使用新的 `unmanaged` 约束来指定类型参数必须是不可为 null 的[“非托管类型”](../language-reference/builtin-types/unmanaged-types.md)。</span><span class="sxs-lookup"><span data-stu-id="ce34b-159">You can also use the new `unmanaged` constraint, to specify that a type parameter must be a non-nullable [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span>

<span data-ttu-id="ce34b-160">有关详细信息，请参阅有关 [`where` 泛型约束](../language-reference/keywords/where-generic-type-constraint.md)和[类型参数的约束](../programming-guide/generics/constraints-on-type-parameters.md)的文章。</span><span class="sxs-lookup"><span data-stu-id="ce34b-160">For more information, see the articles on [`where` generic constraints](../language-reference/keywords/where-generic-type-constraint.md) and [constraints on type parameters](../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="ce34b-161">将这些约束添加到现有类型是[不兼容的更改](version-update-considerations.md#incompatible-changes)。</span><span class="sxs-lookup"><span data-stu-id="ce34b-161">Adding these constraints to existing types is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="ce34b-162">封闭式泛型类型可能不再满足这些新约束的要求。</span><span class="sxs-lookup"><span data-stu-id="ce34b-162">Closed generic types may no longer meet these new constraints.</span></span>

## <a name="make-existing-features-better"></a><span data-ttu-id="ce34b-163">提升了现有功能</span><span class="sxs-lookup"><span data-stu-id="ce34b-163">Make existing features better</span></span>

<span data-ttu-id="ce34b-164">第二个主题提供了对语言中的功能的改进。</span><span class="sxs-lookup"><span data-stu-id="ce34b-164">The second theme provides improvements to features in the language.</span></span> <span data-ttu-id="ce34b-165">这些功能提升了在编写 C# 时的效率。</span><span class="sxs-lookup"><span data-stu-id="ce34b-165">These features improve productivity when writing C#.</span></span>

### <a name="tuples-support--and-"></a><span data-ttu-id="ce34b-166">元组支持 `==` 和 `!=`</span><span class="sxs-lookup"><span data-stu-id="ce34b-166">Tuples support `==` and `!=`</span></span>

<span data-ttu-id="ce34b-167">C# 元组类型现在支持 `==` 和 `!=`。</span><span class="sxs-lookup"><span data-stu-id="ce34b-167">The C# tuple types now support `==` and `!=`.</span></span> <span data-ttu-id="ce34b-168">有关详细信息，请参阅[元组类型](../language-reference/builtin-types/value-tuples.md)一文的[元组相等](../language-reference/builtin-types/value-tuples.md#tuple-equality)部分。</span><span class="sxs-lookup"><span data-stu-id="ce34b-168">For more information, see the [Tuple equality](../language-reference/builtin-types/value-tuples.md#tuple-equality) section of the [Tuple types](../language-reference/builtin-types/value-tuples.md) article.</span></span>

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a><span data-ttu-id="ce34b-169">将特性添加到自动实现的属性的支持字段</span><span class="sxs-lookup"><span data-stu-id="ce34b-169">Attach attributes to the backing fields for auto-implemented properties</span></span>

<span data-ttu-id="ce34b-170">现在支持此语法：</span><span class="sxs-lookup"><span data-stu-id="ce34b-170">This syntax is now supported:</span></span>

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

<span data-ttu-id="ce34b-171">属性 `SomeThingAboutFieldAttribute` 应用于编译器生成的 `SomeProperty` 的支持字段。</span><span class="sxs-lookup"><span data-stu-id="ce34b-171">The attribute `SomeThingAboutFieldAttribute` is applied to the compiler generated backing field for `SomeProperty`.</span></span> <span data-ttu-id="ce34b-172">有关详细信息，请参阅 C# 编程指南中的[属性](../programming-guide/concepts/attributes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="ce34b-172">For more information, see [attributes](../programming-guide/concepts/attributes/index.md) in the C# programming guide.</span></span>

### <a name="in-method-overload-resolution-tiebreaker"></a><span data-ttu-id="ce34b-173">`in` 方法重载解析决胜属性</span><span class="sxs-lookup"><span data-stu-id="ce34b-173">`in` method overload resolution tiebreaker</span></span>

<span data-ttu-id="ce34b-174">在添加 `in` 参数修饰符时，这两个方法将导致多义性：</span><span class="sxs-lookup"><span data-stu-id="ce34b-174">When the `in` argument modifier was added, these two methods would cause an ambiguity:</span></span>

```csharp
static void M(S arg);
static void M(in S arg);
```

<span data-ttu-id="ce34b-175">现在，通过值（前面示例中的第一个）的重载比通过只读引用版本的重载更好。</span><span class="sxs-lookup"><span data-stu-id="ce34b-175">Now, the by value (first in the preceding example) overload is better than the by readonly reference version.</span></span> <span data-ttu-id="ce34b-176">若要使用只读引用参数调用版本，必须在调用方法前添加 `in` 修饰符。</span><span class="sxs-lookup"><span data-stu-id="ce34b-176">To call the version with the readonly reference argument, you must include the `in` modifier when calling the method.</span></span>

> [!NOTE]
> <span data-ttu-id="ce34b-177">这将作为 bug 修复来实现。</span><span class="sxs-lookup"><span data-stu-id="ce34b-177">This was implemented as a bug fix.</span></span> <span data-ttu-id="ce34b-178">即使在设置为“7.2”的语言版本中，这也不再具有多义性。</span><span class="sxs-lookup"><span data-stu-id="ce34b-178">This no longer is ambiguous even with the language version set to "7.2".</span></span>

<span data-ttu-id="ce34b-179">有关详细信息，请参阅有关 [`in` 参数修饰符](../language-reference/keywords/in-parameter-modifier.md)的文章。</span><span class="sxs-lookup"><span data-stu-id="ce34b-179">For more information, see the article on the [`in` parameter modifier](../language-reference/keywords/in-parameter-modifier.md).</span></span>

### <a name="extend-expression-variables-in-initializers"></a><span data-ttu-id="ce34b-180">扩展初始值设定项中的表达式变量</span><span class="sxs-lookup"><span data-stu-id="ce34b-180">Extend expression variables in initializers</span></span>

<span data-ttu-id="ce34b-181">已对在 C# 7.0 中添加的允许 `out` 变量声明的语法进行了扩展，以包含字段初始值设定项、属性初始值设定项、构造函数初始值设定项和查询子句。</span><span class="sxs-lookup"><span data-stu-id="ce34b-181">The syntax added in C# 7.0 to allow `out` variable declarations has been extended to include field initializers, property initializers, constructor initializers, and query clauses.</span></span> <span data-ttu-id="ce34b-182">它允许使用如以下示例中所示的代码：</span><span class="sxs-lookup"><span data-stu-id="ce34b-182">It enables code such as the following example:</span></span>

```csharp
public class B
{
   public B(int i, out int j)
   {
      j = i;
   }
}

public class D : B
{
   public D(int i) : base(i, out var j)
   {
      Console.WriteLine($"The value of 'j' is {j}");
   }
}
```

### <a name="improved-overload-candidates"></a><span data-ttu-id="ce34b-183">改进了重载候选项</span><span class="sxs-lookup"><span data-stu-id="ce34b-183">Improved overload candidates</span></span>

<span data-ttu-id="ce34b-184">在每个版本中，对重载解析规则进行了更新，以解决多义方法调用具有“明显”选择的情况。</span><span class="sxs-lookup"><span data-stu-id="ce34b-184">In every release, the overload resolution rules get updated to address situations where ambiguous method invocations have an "obvious" choice.</span></span> <span data-ttu-id="ce34b-185">此版本添加了三个新规则，以帮助编译器选取明显的选择：</span><span class="sxs-lookup"><span data-stu-id="ce34b-185">This release adds three new rules to help the compiler pick the obvious choice:</span></span>

1. <span data-ttu-id="ce34b-186">当方法组同时包含实例和静态成员时，如果方法在不含实例接收器或上下文的情况下被调用，则编译器将丢弃实例成员。</span><span class="sxs-lookup"><span data-stu-id="ce34b-186">When a method group contains both instance and static members, the compiler discards the instance members if the method was invoked without an instance receiver or context.</span></span> <span data-ttu-id="ce34b-187">如果方法在含有实例接收器的情况下被调用，则编译器将丢弃静态成员。</span><span class="sxs-lookup"><span data-stu-id="ce34b-187">The compiler discards the static members if the method was invoked with an instance receiver.</span></span> <span data-ttu-id="ce34b-188">在没有接收器时，编译器将仅添加静态上下文中的静态成员，否则，将同时添加静态成员和实例成员。</span><span class="sxs-lookup"><span data-stu-id="ce34b-188">When there is no receiver, the compiler includes only static members in a static context, otherwise both static and instance members.</span></span> <span data-ttu-id="ce34b-189">当接收器是不明确的实例或类型时，编译器将同时添加两者。</span><span class="sxs-lookup"><span data-stu-id="ce34b-189">When the receiver is ambiguously an instance or type, the compiler includes both.</span></span> <span data-ttu-id="ce34b-190">静态上下文（其中隐式 `this` 实例接收器无法使用）包含未定义 `this` 的成员的正文（例如，静态成员），以及不能使用 `this` 的位置（例如，字段初始值设定项和构造函数初始值设定项）。</span><span class="sxs-lookup"><span data-stu-id="ce34b-190">A static context, where an implicit `this` instance receiver cannot be used, includes the body of members where no `this` is defined, such as static members, as well as places where `this` cannot be used, such as field initializers and constructor-initializers.</span></span>
1. <span data-ttu-id="ce34b-191">当一个方法组包含类型参数不满足其约束的某些泛型方法时，这些成员将从候选集中移除。</span><span class="sxs-lookup"><span data-stu-id="ce34b-191">When a method group contains some generic methods whose type arguments do not satisfy their constraints, these members are removed from the candidate set.</span></span>
1. <span data-ttu-id="ce34b-192">对于方法组转换，返回类型与委托的返回类型不匹配的候选方法将从集中移除。</span><span class="sxs-lookup"><span data-stu-id="ce34b-192">For a method group conversion, candidate methods whose return type doesn't match up with the delegate's return type are removed from the set.</span></span>

<span data-ttu-id="ce34b-193">你将注意到此更改，因为当你确定哪个方法更好时，你将发现多义方法重载具有更少的编译器错误。</span><span class="sxs-lookup"><span data-stu-id="ce34b-193">You'll only notice this change because you'll find fewer compiler errors for ambiguous method overloads when you are sure which method is better.</span></span>

## <a name="new-compiler-options"></a><span data-ttu-id="ce34b-194">新的编译器选项</span><span class="sxs-lookup"><span data-stu-id="ce34b-194">New compiler options</span></span>

<span data-ttu-id="ce34b-195">新的编译器选项支持 C# 程序的新版本和 DevOps 方案。</span><span class="sxs-lookup"><span data-stu-id="ce34b-195">New compiler options support new build and DevOps scenarios for C# programs.</span></span>

### <a name="public-or-open-source-signing"></a><span data-ttu-id="ce34b-196">公共或开放源代码签名</span><span class="sxs-lookup"><span data-stu-id="ce34b-196">Public or Open Source signing</span></span>

<span data-ttu-id="ce34b-197">`-publicsign` 编译器选项指示编译器使用公钥对程序集进行签名。</span><span class="sxs-lookup"><span data-stu-id="ce34b-197">The `-publicsign` compiler option instructs the compiler to sign the assembly using a public key.</span></span> <span data-ttu-id="ce34b-198">程序集被标记为已签名，但签名取自公钥。</span><span class="sxs-lookup"><span data-stu-id="ce34b-198">The assembly is marked as signed, but the signature is taken from the public key.</span></span> <span data-ttu-id="ce34b-199">此选项使你能够使用公钥在开放源代码项目中构建签名的程序集。</span><span class="sxs-lookup"><span data-stu-id="ce34b-199">This option enables you to build signed assemblies from open-source projects using a public key.</span></span>

<span data-ttu-id="ce34b-200">有关详细信息，请参阅 [-publicsign 编译器选项](../language-reference/compiler-options/publicsign-compiler-option.md)一文。</span><span class="sxs-lookup"><span data-stu-id="ce34b-200">For more information, see the [-publicsign compiler option](../language-reference/compiler-options/publicsign-compiler-option.md) article.</span></span>

### <a name="pathmap"></a><span data-ttu-id="ce34b-201">pathmap</span><span class="sxs-lookup"><span data-stu-id="ce34b-201">pathmap</span></span>

<span data-ttu-id="ce34b-202">`-pathmap` 编译器选项指示编译器将生成环境中的源路径替换为映射的源路径。</span><span class="sxs-lookup"><span data-stu-id="ce34b-202">The `-pathmap` compiler option instructs the compiler to replace source paths from the build environment with mapped source paths.</span></span> <span data-ttu-id="ce34b-203">`-pathmap` 选项控制由编译器编写入 PDB 文件或为 <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> 编写的源路径。</span><span class="sxs-lookup"><span data-stu-id="ce34b-203">The `-pathmap` option controls the source path written by the compiler to PDB files or for the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span></span>

<span data-ttu-id="ce34b-204">有关详细信息，请参阅 [-pathmap 编译器选项](../language-reference/compiler-options/pathmap-compiler-option.md)一文。</span><span class="sxs-lookup"><span data-stu-id="ce34b-204">For more information, see the [-pathmap compiler option](../language-reference/compiler-options/pathmap-compiler-option.md) article.</span></span>

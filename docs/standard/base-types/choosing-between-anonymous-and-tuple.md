---
title: 在匿名类型和元组类型之间进行选择
description: 了解何时适合选择匿名类型和元组类型。
author: IEvangelist
ms.author: dapine
ms.date: 07/01/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 9c186133a639faf187c89d872856d860a20f5a2d
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174213"
---
# <a name="choosing-between-anonymous-and-tuple-types"></a><span data-ttu-id="d55e8-103">在匿名类型和元组类型之间进行选择</span><span class="sxs-lookup"><span data-stu-id="d55e8-103">Choosing between anonymous and tuple types</span></span>

<span data-ttu-id="d55e8-104">选择适当的类型需要考虑其可用性和性能，还要与其他类型相比较并进行权衡。</span><span class="sxs-lookup"><span data-stu-id="d55e8-104">Choosing the appropriate type involves considering its usability, performance, and tradeoffs compared to other types.</span></span> <span data-ttu-id="d55e8-105">匿名类型自 C# 3.0 即可使用，而泛型 <xref:System.Tuple%602?displayProperty=nameWithType> 类型是随 .NET Framework 4.0 引入的。</span><span class="sxs-lookup"><span data-stu-id="d55e8-105">Anonymous types have been available since C# 3.0, while generic <xref:System.Tuple%602?displayProperty=nameWithType> types were introduced with .NET Framework 4.0.</span></span> <span data-ttu-id="d55e8-106">自那时起，通过语言级别支持引入了多个新选项，例如 <xref:System.ValueTuple%602?displayProperty=nameWithType>（它名副其实，提供具有匿名类型灵活性的值类型）。</span><span class="sxs-lookup"><span data-stu-id="d55e8-106">Since then new options have been introduced with language level support, such as <xref:System.ValueTuple%602?displayProperty=nameWithType> - which as the name implies, provide a value type with the flexibility of anonymous types.</span></span> <span data-ttu-id="d55e8-107">在本文中，你将了解何时应选择一种类型而不是另一种。</span><span class="sxs-lookup"><span data-stu-id="d55e8-107">In this article, you'll learn when it's appropriate to choose one type over the other.</span></span>

## <a name="usability-and-functionality"></a><span data-ttu-id="d55e8-108">可用性和功能</span><span class="sxs-lookup"><span data-stu-id="d55e8-108">Usability and functionality</span></span>

<span data-ttu-id="d55e8-109">匿名类型是在 C# 3.0 中随语言集成查询 (LINQ) 表达式引入的。</span><span class="sxs-lookup"><span data-stu-id="d55e8-109">Anonymous types were introduced in C# 3.0 with Language-Integrated Query (LINQ) expressions.</span></span> <span data-ttu-id="d55e8-110">使用 LINQ，开发人员通常会将查询结果投影到匿名类型中，这些类型保存着来自其所处理对象的几个选择属性。</span><span class="sxs-lookup"><span data-stu-id="d55e8-110">With LINQ, developers often project results from queries into anonymous types that hold a few select properties from the objects they're working with.</span></span> <span data-ttu-id="d55e8-111">请考虑以下示例，它实例化 <xref:System.DateTime> 对象的一个数组，然后循环访问它们，并将其投影到具有两个属性的匿名类型。</span><span class="sxs-lookup"><span data-stu-id="d55e8-111">Consider the following example, that instantiates an array of <xref:System.DateTime> objects, and iterates through them projecting into an anonymous type with two properties.</span></span>

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var anonymous in
             dates.Select(
                 date => new { Formatted = $"{date:MMM dd, yyyy hh:mm zzz}", date.Ticks }))
{
    Console.WriteLine($"Ticks: {anonymous.Ticks}, formatted: {anonymous.Formatted}");
}
```

<span data-ttu-id="d55e8-112">使用 [`new`](../../csharp/language-reference/operators/new-operator.md) 运算符来实例化匿名类型，从声明推断属性名称和类型。</span><span class="sxs-lookup"><span data-stu-id="d55e8-112">Anonymous types are instantiated by using the [`new`](../../csharp/language-reference/operators/new-operator.md) operator, and the property names and types are inferred from the declaration.</span></span> <span data-ttu-id="d55e8-113">如果同一程序集中的两个或多个匿名对象初始值设定项指定了属性序列，这些属性采用相同顺序且具有相同的名称和类型，则编译器将对象视为相同类型的实例。</span><span class="sxs-lookup"><span data-stu-id="d55e8-113">If two or more anonymous object initializers in the same assembly specify a sequence of properties that are in the same order and that have the same names and types, the compiler treats the objects as instances of the same type.</span></span> <span data-ttu-id="d55e8-114">它们共享同一编译器生成的类型信息。</span><span class="sxs-lookup"><span data-stu-id="d55e8-114">They share the same compiler-generated type information.</span></span>

<span data-ttu-id="d55e8-115">以上 C# 代码片段投影具有两个属性的匿名类型，非常类似于以下编译器生成的 C# 类：</span><span class="sxs-lookup"><span data-stu-id="d55e8-115">The previous C# snippet projects an anonymous type with two properties, much like the following compiler-generated C# class:</span></span>

```csharp
internal sealed class f__AnonymousType0
{
    public string Formatted { get; }
    public long Ticks { get; }

    public f__AnonymousType0(string formatted, long ticks)
    {
        Formatted = formatted;
        Ticks = ticks;
    }
}
```

<span data-ttu-id="d55e8-116">有关详细信息，请参阅[匿名类型](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="d55e8-116">For more information, see [anonymous types](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span> <span data-ttu-id="d55e8-117">投影到 LINQ 查询时，元组具有相同的功能，你可以选择添加属性到元组。</span><span class="sxs-lookup"><span data-stu-id="d55e8-117">The same functionality exists with tuples when projecting into LINQ queries, you can select properties into tuples.</span></span> <span data-ttu-id="d55e8-118">这些元组会贯穿查询，就像匿名类型一样。</span><span class="sxs-lookup"><span data-stu-id="d55e8-118">These tuples flow through the query, just as anonymous types would.</span></span> <span data-ttu-id="d55e8-119">现在请考虑以下使用 `System.Tuple<string, long>` 的示例。</span><span class="sxs-lookup"><span data-stu-id="d55e8-119">Now consider the following example using the `System.Tuple<string, long>`.</span></span>

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var tuple in
            dates.Select(
                date => new Tuple<string, long>($"{date:MMM dd, yyyy hh:mm zzz}", date.Ticks)))
{
    Console.WriteLine($"Ticks: {tuple.Item2}, formatted: {tuple.Item1}");
}
```

<span data-ttu-id="d55e8-120">在 <xref:System.Tuple%602?displayProperty=nameWithType> 中，实例公开编号项属性，如 `Item1`和 `Item2`。</span><span class="sxs-lookup"><span data-stu-id="d55e8-120">With the <xref:System.Tuple%602?displayProperty=nameWithType>, the instance exposes numbered item properties, such as `Item1`, and `Item2`.</span></span> <span data-ttu-id="d55e8-121">由于属性名称只提供序号，因此这些属性名称让人更难理解属性值的意图。</span><span class="sxs-lookup"><span data-stu-id="d55e8-121">These property names can make it more difficult to understand the intent of the property values, as the property name only provides the ordinal.</span></span> <span data-ttu-id="d55e8-122">此外，`System.Tuple` 类型是引用 `class` 类型。</span><span class="sxs-lookup"><span data-stu-id="d55e8-122">Furthermore, the `System.Tuple` types are reference `class` types.</span></span> <span data-ttu-id="d55e8-123">而 <xref:System.ValueTuple%602?displayProperty=nameWithType> 是值 `struct` 类型。</span><span class="sxs-lookup"><span data-stu-id="d55e8-123">The <xref:System.ValueTuple%602?displayProperty=nameWithType> however, is a value `struct` type.</span></span> <span data-ttu-id="d55e8-124">以下 C# 代码片段使用 `ValueTuple<string, long>` 投影。</span><span class="sxs-lookup"><span data-stu-id="d55e8-124">The following C# snippet, uses `ValueTuple<string, long>` to project into.</span></span> <span data-ttu-id="d55e8-125">在此过程中，它使用文字语法进行分配。</span><span class="sxs-lookup"><span data-stu-id="d55e8-125">In doing so, it assigns using a literal syntax.</span></span>

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var (formatted, ticks) in
            dates.Select(
                date => (Formatted: $"{date:MMM dd, yyyy at hh:mm zzz}", date.Ticks)))
{
    Console.WriteLine($"Ticks: {ticks}, formatted: {formatted}");
}
```

<span data-ttu-id="d55e8-126">有关元组的详细信息，请参阅[元组类型（C# 参考）](../../csharp/language-reference/builtin-types/value-tuples.md)或[元组 (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/tuples.md)。</span><span class="sxs-lookup"><span data-stu-id="d55e8-126">For more information about tuples, see [Tuple types (C# reference)](../../csharp/language-reference/builtin-types/value-tuples.md) or [Tuples (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/tuples.md).</span></span>

<span data-ttu-id="d55e8-127">以上示例在功能上是等效的；但其可用性和基础实现存在细微差异。</span><span class="sxs-lookup"><span data-stu-id="d55e8-127">The previous examples are all functionally equivalent, however; there are slight differences in their usability and their underlying implementations.</span></span>

## <a name="tradeoffs"></a><span data-ttu-id="d55e8-128">权衡</span><span class="sxs-lookup"><span data-stu-id="d55e8-128">Tradeoffs</span></span>

<span data-ttu-id="d55e8-129">你可能希望始终使用 <xref:System.ValueTuple>（而不是 <xref:System.Tuple>）和匿名类型，但应进行一些权衡考虑。</span><span class="sxs-lookup"><span data-stu-id="d55e8-129">You might want to always use <xref:System.ValueTuple> over <xref:System.Tuple>, and anonymous types, but there are tradeoffs you should consider.</span></span> <span data-ttu-id="d55e8-130"><xref:System.ValueTuple> 类型是可变的，而 <xref:System.Tuple> 是只读的。</span><span class="sxs-lookup"><span data-stu-id="d55e8-130">The <xref:System.ValueTuple> types are mutable, whereas <xref:System.Tuple> are read-only.</span></span> <span data-ttu-id="d55e8-131">匿名类型可用于表达式树，而元组不行。</span><span class="sxs-lookup"><span data-stu-id="d55e8-131">Anonymous types can be used in expression trees, while tuples cannot.</span></span> <span data-ttu-id="d55e8-132">下表概述了一些关键区别。</span><span class="sxs-lookup"><span data-stu-id="d55e8-132">The following table is an overview of some of the key differences.</span></span>

### <a name="key-differences"></a><span data-ttu-id="d55e8-133">主要区别</span><span class="sxs-lookup"><span data-stu-id="d55e8-133">Key differences</span></span>

| <span data-ttu-id="d55e8-134">“属性”</span><span class="sxs-lookup"><span data-stu-id="d55e8-134">Name</span></span>                     | <span data-ttu-id="d55e8-135">访问修饰符</span><span class="sxs-lookup"><span data-stu-id="d55e8-135">Access modifier</span></span> | <span data-ttu-id="d55e8-136">类型</span><span class="sxs-lookup"><span data-stu-id="d55e8-136">Type</span></span>     | <span data-ttu-id="d55e8-137">自定义成员名称</span><span class="sxs-lookup"><span data-stu-id="d55e8-137">Custom member name</span></span> | <span data-ttu-id="d55e8-138">析构支持</span><span class="sxs-lookup"><span data-stu-id="d55e8-138">Deconstruction support</span></span> | <span data-ttu-id="d55e8-139">表达式树支持</span><span class="sxs-lookup"><span data-stu-id="d55e8-139">Expression tree support</span></span> |
|--------------------------|-----------------|----------|----------------------|------------------------|-------------------------|
| <span data-ttu-id="d55e8-140">匿名类型</span><span class="sxs-lookup"><span data-stu-id="d55e8-140">Anonymous types</span></span>          | `internal`      | `class`  | <span data-ttu-id="d55e8-141">✔️</span><span class="sxs-lookup"><span data-stu-id="d55e8-141">✔️</span></span>                   | ❌                     | <span data-ttu-id="d55e8-142">✔️</span><span class="sxs-lookup"><span data-stu-id="d55e8-142">✔️</span></span>                     |
| <xref:System.Tuple>      | `public`        | `class`  | ❌                   | ❌                     | <span data-ttu-id="d55e8-143">✔️</span><span class="sxs-lookup"><span data-stu-id="d55e8-143">✔️</span></span>                     |
| <xref:System.ValueTuple> | `public`        | `struct` | <span data-ttu-id="d55e8-144">✔️</span><span class="sxs-lookup"><span data-stu-id="d55e8-144">✔️</span></span>                   | <span data-ttu-id="d55e8-145">✔️</span><span class="sxs-lookup"><span data-stu-id="d55e8-145">✔️</span></span>                     | ❌                     |

### <a name="serialization"></a><span data-ttu-id="d55e8-146">序列化</span><span class="sxs-lookup"><span data-stu-id="d55e8-146">Serialization</span></span>

<span data-ttu-id="d55e8-147">选择类型时的一个重要考量是，是否需要对其进行序列化。</span><span class="sxs-lookup"><span data-stu-id="d55e8-147">One important consideration when choosing a type, is whether or not it will need to be serialized.</span></span> <span data-ttu-id="d55e8-148">序列化是将对象状态转换为可保持或传输的形式的过程。</span><span class="sxs-lookup"><span data-stu-id="d55e8-148">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="d55e8-149">有关详细信息，请参阅[序列化](../../csharp/programming-guide/concepts/serialization/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d55e8-149">For more information, see [serialization](../../csharp/programming-guide/concepts/serialization/index.md).</span></span> <span data-ttu-id="d55e8-150">当序列化非常重要时，创建 `class` 或 `struct` 优于使用匿名类型或元组类型。</span><span class="sxs-lookup"><span data-stu-id="d55e8-150">When serialization is important, creating a `class` or `struct` is preferred over anonymous types or tuple types.</span></span>

## <a name="performance"></a><span data-ttu-id="d55e8-151">性能</span><span class="sxs-lookup"><span data-stu-id="d55e8-151">Performance</span></span>

<span data-ttu-id="d55e8-152">这些类型各自的性能取决于场景。</span><span class="sxs-lookup"><span data-stu-id="d55e8-152">Performance between these types depends on the scenario.</span></span> <span data-ttu-id="d55e8-153">主要影响涉及分配和复制之间的权衡。</span><span class="sxs-lookup"><span data-stu-id="d55e8-153">The major impact involves the tradeoff between allocations and copying.</span></span> <span data-ttu-id="d55e8-154">在大多数情况下，影响很小。</span><span class="sxs-lookup"><span data-stu-id="d55e8-154">In most scenarios, the impact is small.</span></span> <span data-ttu-id="d55e8-155">如果可能出现重大影响，应采取措施来通知决策者。</span><span class="sxs-lookup"><span data-stu-id="d55e8-155">When major impacts could arise, measurements should be taken to inform the decision.</span></span>

## <a name="conclusion"></a><span data-ttu-id="d55e8-156">结束语</span><span class="sxs-lookup"><span data-stu-id="d55e8-156">Conclusion</span></span>

<span data-ttu-id="d55e8-157">开发人员在元组和匿名类型之间进行选择时，需要考虑几个因素。</span><span class="sxs-lookup"><span data-stu-id="d55e8-157">As a developer choosing between tuples and anonymous types, there are several factors to consider.</span></span> <span data-ttu-id="d55e8-158">一般来说，如果不使用[表达式树](../../csharp/expression-trees.md)，并且你熟悉元组语法，请选择 <xref:System.ValueTuple>，因为它们提供可灵活命名属性的值类型。</span><span class="sxs-lookup"><span data-stu-id="d55e8-158">Generally speaking, if you're not working with [expression trees](../../csharp/expression-trees.md), and you're comfortable with tuple syntax then choose <xref:System.ValueTuple> as they provide a value type with the flexibility to name properties.</span></span> <span data-ttu-id="d55e8-159">如果使用表达式树并且想要命名属性，请选择匿名类型。</span><span class="sxs-lookup"><span data-stu-id="d55e8-159">If you're working with expression trees, and you'd prefer to name properties, choose anonymous types.</span></span> <span data-ttu-id="d55e8-160">否则，请使用 <xref:System.Tuple>。</span><span class="sxs-lookup"><span data-stu-id="d55e8-160">Otherwise, use <xref:System.Tuple>.</span></span>

## <a name="see-also"></a><span data-ttu-id="d55e8-161">请参阅</span><span class="sxs-lookup"><span data-stu-id="d55e8-161">See also</span></span>

- [<span data-ttu-id="d55e8-162">匿名类型</span><span class="sxs-lookup"><span data-stu-id="d55e8-162">Anonymous types</span></span>](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="d55e8-163">表达式树</span><span class="sxs-lookup"><span data-stu-id="d55e8-163">Expression trees</span></span>](../../csharp/expression-trees.md)
- [<span data-ttu-id="d55e8-164">元组类型（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="d55e8-164">Tuple types (C# reference)</span></span>](../../csharp/language-reference/builtin-types/value-tuples.md)
- [<span data-ttu-id="d55e8-165">元组 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d55e8-165">Tuples (Visual Basic)</span></span>](../../visual-basic/programming-guide/language-features/data-types/tuples.md)
- [<span data-ttu-id="d55e8-166">类型设计准则</span><span class="sxs-lookup"><span data-stu-id="d55e8-166">Type design guidelines</span></span>](../design-guidelines/type.md)

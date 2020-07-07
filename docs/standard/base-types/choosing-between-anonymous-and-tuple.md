---
title: 在匿名类型和元组类型之间进行选择
description: 了解何时适合选择匿名类型和元组类型。
ms.date: 07/01/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 24ab770d709b9f3968f4c7fe4b01eb0729dbd751
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853982"
---
# <a name="choosing-between-anonymous-and-tuple-types"></a><span data-ttu-id="a31cc-103">在匿名类型和元组类型之间进行选择</span><span class="sxs-lookup"><span data-stu-id="a31cc-103">Choosing between anonymous and tuple types</span></span>

<span data-ttu-id="a31cc-104">选择适当的类型需要考虑其可用性和性能，还要与其他类型相比较并进行权衡。</span><span class="sxs-lookup"><span data-stu-id="a31cc-104">Choosing the appropriate type involves considering its usability, performance, and tradeoffs compared to other types.</span></span> <span data-ttu-id="a31cc-105">匿名类型自 C# 3.0 即可使用，而泛型 <xref:System.Tuple%602?displayProperty=nameWithType> 类型是随 .NET Framework 4.0 引入的。</span><span class="sxs-lookup"><span data-stu-id="a31cc-105">Anonymous types have been available since C# 3.0, while generic <xref:System.Tuple%602?displayProperty=nameWithType> types were introduced with .NET Framework 4.0.</span></span> <span data-ttu-id="a31cc-106">自那时起，通过语言级别支持引入了多个新选项，例如 <xref:System.ValueTuple%602?displayProperty=nameWithType>（它名副其实，提供具有匿名类型灵活性的值类型）。</span><span class="sxs-lookup"><span data-stu-id="a31cc-106">Since then new options have been introduced with language level support, such as <xref:System.ValueTuple%602?displayProperty=nameWithType> - which as the name implies, provide a value type with the flexibility of anonymous types.</span></span> <span data-ttu-id="a31cc-107">在本文中，你将了解何时应选择一种类型而不是另一种。</span><span class="sxs-lookup"><span data-stu-id="a31cc-107">In this article, you'll learn when it's appropriate to choose one type over the other.</span></span>

## <a name="usability-and-functionality"></a><span data-ttu-id="a31cc-108">可用性和功能</span><span class="sxs-lookup"><span data-stu-id="a31cc-108">Usability and functionality</span></span>

<span data-ttu-id="a31cc-109">匿名类型是在 C# 3.0 中随语言集成查询 (LINQ) 表达式引入的。</span><span class="sxs-lookup"><span data-stu-id="a31cc-109">Anonymous types were introduced in C# 3.0 with Language-Integrated Query (LINQ) expressions.</span></span> <span data-ttu-id="a31cc-110">使用 LINQ，开发人员通常会将查询结果投影到匿名类型中，这些类型保存着来自其所处理对象的几个选择属性。</span><span class="sxs-lookup"><span data-stu-id="a31cc-110">With LINQ, developers often project results from queries into anonymous types that hold a few select properties from the objects they're working with.</span></span> <span data-ttu-id="a31cc-111">请考虑以下示例，它实例化 <xref:System.DateTime> 对象的一个数组，然后循环访问它们，并将其投影到具有两个属性的匿名类型。</span><span class="sxs-lookup"><span data-stu-id="a31cc-111">Consider the following example, that instantiates an array of <xref:System.DateTime> objects, and iterates through them projecting into an anonymous type with two properties.</span></span>

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

<span data-ttu-id="a31cc-112">使用 [`new`](../../csharp/language-reference/operators/new-operator.md) 运算符来实例化匿名类型，从声明推断属性名称和类型。</span><span class="sxs-lookup"><span data-stu-id="a31cc-112">Anonymous types are instantiated by using the [`new`](../../csharp/language-reference/operators/new-operator.md) operator, and the property names and types are inferred from the declaration.</span></span> <span data-ttu-id="a31cc-113">如果同一程序集中的两个或多个匿名对象初始值设定项指定了属性序列，这些属性采用相同顺序且具有相同的名称和类型，则编译器将对象视为相同类型的实例。</span><span class="sxs-lookup"><span data-stu-id="a31cc-113">If two or more anonymous object initializers in the same assembly specify a sequence of properties that are in the same order and that have the same names and types, the compiler treats the objects as instances of the same type.</span></span> <span data-ttu-id="a31cc-114">它们共享同一编译器生成的类型信息。</span><span class="sxs-lookup"><span data-stu-id="a31cc-114">They share the same compiler-generated type information.</span></span>

<span data-ttu-id="a31cc-115">以上 C# 代码片段投影具有两个属性的匿名类型，非常类似于以下编译器生成的 C# 类：</span><span class="sxs-lookup"><span data-stu-id="a31cc-115">The previous C# snippet projects an anonymous type with two properties, much like the following compiler-generated C# class:</span></span>

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

<span data-ttu-id="a31cc-116">有关详细信息，请参阅[匿名类型](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="a31cc-116">For more information, see [anonymous types](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span> <span data-ttu-id="a31cc-117">投影到 LINQ 查询时，元组具有相同的功能，你可以选择添加属性到元组。</span><span class="sxs-lookup"><span data-stu-id="a31cc-117">The same functionality exists with tuples when projecting into LINQ queries, you can select properties into tuples.</span></span> <span data-ttu-id="a31cc-118">这些元组会贯穿查询，就像匿名类型一样。</span><span class="sxs-lookup"><span data-stu-id="a31cc-118">These tuples flow through the query, just as anonymous types would.</span></span> <span data-ttu-id="a31cc-119">现在请考虑以下使用 `System.Tuple<string, long>` 的示例。</span><span class="sxs-lookup"><span data-stu-id="a31cc-119">Now consider the following example using the `System.Tuple<string, long>`.</span></span>

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

<span data-ttu-id="a31cc-120">在 <xref:System.Tuple%602?displayProperty=nameWithType> 中，实例公开编号项属性，如 `Item1`和 `Item2`。</span><span class="sxs-lookup"><span data-stu-id="a31cc-120">With the <xref:System.Tuple%602?displayProperty=nameWithType>, the instance exposes numbered item properties, such as `Item1`, and `Item2`.</span></span> <span data-ttu-id="a31cc-121">由于属性名称只提供序号，因此这些属性名称让人更难理解属性值的意图。</span><span class="sxs-lookup"><span data-stu-id="a31cc-121">These property names can make it more difficult to understand the intent of the property values, as the property name only provides the ordinal.</span></span> <span data-ttu-id="a31cc-122">此外，`System.Tuple` 类型是引用 `class` 类型。</span><span class="sxs-lookup"><span data-stu-id="a31cc-122">Furthermore, the `System.Tuple` types are reference `class` types.</span></span> <span data-ttu-id="a31cc-123">而 <xref:System.ValueTuple%602?displayProperty=nameWithType> 是值 `struct` 类型。</span><span class="sxs-lookup"><span data-stu-id="a31cc-123">The <xref:System.ValueTuple%602?displayProperty=nameWithType> however, is a value `struct` type.</span></span> <span data-ttu-id="a31cc-124">以下 C# 代码片段使用 `ValueTuple<string, long>` 投影。</span><span class="sxs-lookup"><span data-stu-id="a31cc-124">The following C# snippet, uses `ValueTuple<string, long>` to project into.</span></span> <span data-ttu-id="a31cc-125">在此过程中，它使用文字语法进行分配。</span><span class="sxs-lookup"><span data-stu-id="a31cc-125">In doing so, it assigns using a literal syntax.</span></span>

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

<span data-ttu-id="a31cc-126">C# 通过 <xref:System.ValueTuple> 类型提供对元组的语言支持，还提供用于以下目的的语义：</span><span class="sxs-lookup"><span data-stu-id="a31cc-126">C# provides language support of tuples with the <xref:System.ValueTuple> type, and semantics for:</span></span>

- [<span data-ttu-id="a31cc-127">元组赋值</span><span class="sxs-lookup"><span data-stu-id="a31cc-127">Tuple assignment</span></span>](../../csharp/tuples.md#assignment-and-tuples)
- <span data-ttu-id="a31cc-128">[元组析构](../../csharp/deconstruct.md)（不限于元组）</span><span class="sxs-lookup"><span data-stu-id="a31cc-128">[Tuple deconstruction](../../csharp/deconstruct.md) (not limited to tuples)</span></span>
- [<span data-ttu-id="a31cc-129">元组相等性检查</span><span class="sxs-lookup"><span data-stu-id="a31cc-129">Tuple equality checks</span></span>](../../csharp/tuples.md#equality-and-tuples)
- [<span data-ttu-id="a31cc-130">元组投影初始值设定项</span><span class="sxs-lookup"><span data-stu-id="a31cc-130">Tuple projection initializers</span></span>](../../csharp/tuples.md#tuple-projection-initializers)

<span data-ttu-id="a31cc-131">以上示例在功能上是等效的；但其可用性和基础实现存在细微差异。</span><span class="sxs-lookup"><span data-stu-id="a31cc-131">The previous examples are all functionally equivalent, however; there are slight differences in their usability and their underlying implementations.</span></span>

## <a name="tradeoffs"></a><span data-ttu-id="a31cc-132">权衡</span><span class="sxs-lookup"><span data-stu-id="a31cc-132">Tradeoffs</span></span>

<span data-ttu-id="a31cc-133">你可能希望始终使用 <xref:System.ValueTuple>（而不是 <xref:System.Tuple>）和匿名类型，但应进行一些权衡考虑。</span><span class="sxs-lookup"><span data-stu-id="a31cc-133">You might want to always use <xref:System.ValueTuple> over <xref:System.Tuple>, and anonymous types, but there are tradeoffs you should consider.</span></span> <span data-ttu-id="a31cc-134"><xref:System.ValueTuple> 类型是可变的，而 <xref:System.Tuple> 是只读的。</span><span class="sxs-lookup"><span data-stu-id="a31cc-134">The <xref:System.ValueTuple> types are mutable, whereas <xref:System.Tuple> are read-only.</span></span> <span data-ttu-id="a31cc-135">匿名类型可用于表达式树，而元组不行。</span><span class="sxs-lookup"><span data-stu-id="a31cc-135">Anonymous types can be used in expression trees, while tuples cannot.</span></span> <span data-ttu-id="a31cc-136">下表概述了一些关键区别。</span><span class="sxs-lookup"><span data-stu-id="a31cc-136">The following table is an overview of some of the key differences.</span></span>

### <a name="key-differences"></a><span data-ttu-id="a31cc-137">主要区别</span><span class="sxs-lookup"><span data-stu-id="a31cc-137">Key differences</span></span>

| <span data-ttu-id="a31cc-138">“属性”</span><span class="sxs-lookup"><span data-stu-id="a31cc-138">Name</span></span>                     | <span data-ttu-id="a31cc-139">访问修饰符</span><span class="sxs-lookup"><span data-stu-id="a31cc-139">Access modifier</span></span> | <span data-ttu-id="a31cc-140">类型</span><span class="sxs-lookup"><span data-stu-id="a31cc-140">Type</span></span>     | <span data-ttu-id="a31cc-141">自定义属性名称</span><span class="sxs-lookup"><span data-stu-id="a31cc-141">Custom property name</span></span> | <span data-ttu-id="a31cc-142">析构支持</span><span class="sxs-lookup"><span data-stu-id="a31cc-142">Deconstruction support</span></span> | <span data-ttu-id="a31cc-143">表达式树支持</span><span class="sxs-lookup"><span data-stu-id="a31cc-143">Expression tree support</span></span> |
|--------------------------|-----------------|----------|----------------------|------------------------|-------------------------|
| <span data-ttu-id="a31cc-144">匿名类型</span><span class="sxs-lookup"><span data-stu-id="a31cc-144">Anonymous types</span></span>          | `internal`      | `class`  | <span data-ttu-id="a31cc-145">✔️</span><span class="sxs-lookup"><span data-stu-id="a31cc-145">✔️</span></span>                   | ❌                     | <span data-ttu-id="a31cc-146">✔️</span><span class="sxs-lookup"><span data-stu-id="a31cc-146">✔️</span></span>                     |
| <xref:System.Tuple>      | `public`        | `class`  | ❌                   | ❌                     | <span data-ttu-id="a31cc-147">✔️</span><span class="sxs-lookup"><span data-stu-id="a31cc-147">✔️</span></span>                     |
| <xref:System.ValueTuple> | `public`        | `struct` | <span data-ttu-id="a31cc-148">✔️</span><span class="sxs-lookup"><span data-stu-id="a31cc-148">✔️</span></span>                   | <span data-ttu-id="a31cc-149">✔️</span><span class="sxs-lookup"><span data-stu-id="a31cc-149">✔️</span></span>                     | ❌                     |

### <a name="serialization"></a><span data-ttu-id="a31cc-150">序列化</span><span class="sxs-lookup"><span data-stu-id="a31cc-150">Serialization</span></span>

<span data-ttu-id="a31cc-151">选择类型时的一个重要考量是，是否需要对其进行序列化。</span><span class="sxs-lookup"><span data-stu-id="a31cc-151">One important consideration when choosing a type, is whether or not it will need to be serialized.</span></span> <span data-ttu-id="a31cc-152">序列化是将对象状态转换为可保持或传输的形式的过程。</span><span class="sxs-lookup"><span data-stu-id="a31cc-152">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="a31cc-153">有关详细信息，请参阅[序列化](../../csharp/programming-guide/concepts/serialization/index.md)。</span><span class="sxs-lookup"><span data-stu-id="a31cc-153">For more information, see [serialization](../../csharp/programming-guide/concepts/serialization/index.md).</span></span> <span data-ttu-id="a31cc-154">当序列化非常重要时，创建 `class` 或 `struct` 优于使用匿名类型或元组类型。</span><span class="sxs-lookup"><span data-stu-id="a31cc-154">When serialization is important, creating a `class` or `struct` is preferred over anonymous types or tuple types.</span></span>

## <a name="performance"></a><span data-ttu-id="a31cc-155">性能</span><span class="sxs-lookup"><span data-stu-id="a31cc-155">Performance</span></span>

<span data-ttu-id="a31cc-156">这些类型各自的性能取决于场景。</span><span class="sxs-lookup"><span data-stu-id="a31cc-156">Performance between these types depends on the scenario.</span></span> <span data-ttu-id="a31cc-157">主要影响涉及分配和复制之间的权衡。</span><span class="sxs-lookup"><span data-stu-id="a31cc-157">The major impact involves the tradeoff between allocations and copying.</span></span> <span data-ttu-id="a31cc-158">在大多数情况下，影响很小。</span><span class="sxs-lookup"><span data-stu-id="a31cc-158">In most scenarios, the impact is small.</span></span> <span data-ttu-id="a31cc-159">如果可能出现重大影响，应采取措施来通知决策者。</span><span class="sxs-lookup"><span data-stu-id="a31cc-159">When major impacts could arise, measurements should be taken to inform the decision.</span></span>

## <a name="conclusion"></a><span data-ttu-id="a31cc-160">结束语</span><span class="sxs-lookup"><span data-stu-id="a31cc-160">Conclusion</span></span>

<span data-ttu-id="a31cc-161">开发人员在元组和匿名类型之间进行选择时，需要考虑几个因素。</span><span class="sxs-lookup"><span data-stu-id="a31cc-161">As a developer choosing between tuples and anonymous types, there are several factors to consider.</span></span> <span data-ttu-id="a31cc-162">一般来说，如果不使用[表达式树](../../csharp/expression-trees.md)，并且你熟悉元组语法，请选择 <xref:System.ValueTuple>，因为它们提供可灵活命名属性的值类型。</span><span class="sxs-lookup"><span data-stu-id="a31cc-162">Generally speaking, if you're not working with [expression trees](../../csharp/expression-trees.md), and you're comfortable with tuple syntax then choose <xref:System.ValueTuple> as they provide a value type with the flexibility to name properties.</span></span> <span data-ttu-id="a31cc-163">如果使用表达式树并且想要命名属性，请选择匿名类型。</span><span class="sxs-lookup"><span data-stu-id="a31cc-163">If you're working with expression trees, and you'd prefer to name properties, choose anonymous types.</span></span> <span data-ttu-id="a31cc-164">否则，请使用 <xref:System.Tuple>。</span><span class="sxs-lookup"><span data-stu-id="a31cc-164">Otherwise, use <xref:System.Tuple>.</span></span>

## <a name="see-also"></a><span data-ttu-id="a31cc-165">请参阅</span><span class="sxs-lookup"><span data-stu-id="a31cc-165">See also</span></span>

- [<span data-ttu-id="a31cc-166">匿名类型</span><span class="sxs-lookup"><span data-stu-id="a31cc-166">Anonymous types</span></span>](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="a31cc-167">表达式树</span><span class="sxs-lookup"><span data-stu-id="a31cc-167">Expression trees</span></span>](../../csharp/expression-trees.md)
- [<span data-ttu-id="a31cc-168">元组类型</span><span class="sxs-lookup"><span data-stu-id="a31cc-168">Tuple types</span></span>](../../csharp/tuples.md)
- [<span data-ttu-id="a31cc-169">类型设计准则</span><span class="sxs-lookup"><span data-stu-id="a31cc-169">Type design guidelines</span></span>](../design-guidelines/type.md)

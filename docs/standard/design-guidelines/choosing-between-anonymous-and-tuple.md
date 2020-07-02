---
title: 在匿名类型和元组类型之间进行选择
description: 了解何时适合在匿名类型和元组类型之间进行选择。
ms.date: 06/29/2020
ms.technology: dotnet-standard
ms.openlocfilehash: bc17695830a42a6eed9d60c0e097ee9d02a7957e
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803763"
---
# <a name="choosing-between-anonymous-and-tuple-types"></a>在匿名类型和元组类型之间进行选择

选择适当的类型需要考虑其可用性、性能以及与其他类型相比的权衡。 自 c # 3.0 起，匿名类型可用，而泛型 <xref:System.Tuple%602?displayProperty=nameWithType> 类型是在 .NET Framework 4.0 中引入的。 自那时起，使用语言级别支持引入了新的选项，例如，如名称所示 <xref:System.ValueTuple%602?displayProperty=nameWithType> ，提供一个具有匿名类型灵活性的值类型。 在本文中，你将了解如何在另一种类型上选择一种类型。

## <a name="usability-and-functionality"></a>可用性和功能

在 c # 3.0 中引入了匿名类型，并提供语言集成查询（LINQ）表达式。 使用 LINQ，开发人员通常会将查询结果投影到匿名类型中，这些类型保存了他们正在处理的对象中的几个选择属性。 请考虑以下示例，该示例实例化一个 <xref:System.DateTime> 对象数组，并循环访问它们，并将其投影到具有两个属性的匿名类型。

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

匿名类型是使用运算符实例化的 [`new`](../../csharp/language-reference/operators/new-operator.md) ，属性名称和类型是从声明中推断出来的。 如果同一程序集中的两个或多个匿名对象初始值设定项指定了顺序相同且具有相同名称和类型的属性序列，则编译器将对象视为相同类型的实例。 它们共享同一编译器生成的类型信息。

前面的 c # 代码段投影一个具有两个属性的匿名类型，非常类似于下面的编译器生成的 c # 类：

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

有关详细信息，请参阅[匿名类型](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)。 在投影到 LINQ 查询时，元组具有相同的功能，你可以选择属性到元组。 这些元组会流过查询，就像匿名类型一样。 现在，请考虑以下使用的示例 `System.Tuple<string, long>` 。

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

对于 <xref:System.Tuple%602?displayProperty=nameWithType> ，实例公开编号项属性，如 `Item1` 、和 `Item2` 。 由于属性名称只提供序号，因此这些属性名称使更难理解属性值的意图。 而且， `System.Tuple` 类型是引用 `class` 类型。 <xref:System.ValueTuple%602?displayProperty=nameWithType>不过，是值 `struct` 类型。 下面的 c # 代码段使用 `ValueTuple<string, long>` 将投影到。 在此过程中，它使用文字语法进行分配。

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

C # 提供具有类型的元组的语言支持 <xref:System.ValueTuple> ，并提供以下语义：

- [元组赋值](../../csharp/tuples.md#assignment-and-tuples)
- [元组析构](../../csharp/deconstruct.md)（不限于元组）
- [元组相等性检查](../../csharp/tuples.md#equality-and-tuples)
- [元组投影初始值设定项](../../csharp/tuples.md#tuple-projection-initializers)

但前面的示例在功能上是等效的;它们的可用性和基础实现之间存在细微的差异。

## <a name="tradeoffs"></a>权衡

你可能希望始终使用 <xref:System.ValueTuple> over <xref:System.Tuple> 和匿名类型，但有一些需要考虑的权衡。 <xref:System.ValueTuple>类型是可变的，而 <xref:System.Tuple> 是只读的。 可在表达式树中使用匿名类型，而元组则无法使用。 下表概述了一些主要区别。

### <a name="key-differences"></a>主要差异

| “属性”                     | 访问修饰符 | 类型     | 自定义属性名称 | 析构支持 | 表达式树支持 |
|--------------------------|-----------------|----------|----------------------|------------------------|-------------------------|
| 匿名类型          | `internal`      | `class`  | ✔️                   | ❌                     | ✔️                     |
| <xref:System.Tuple>      | `public`        | `class`  | ❌                   | ❌                     | ✔️                     |
| <xref:System.ValueTuple> | `public`        | `struct` | ✔️                   | ✔️                     | ❌                     |

### <a name="serialization"></a>序列化

选择类型时的一个重要注意事项是是否需要对其进行序列化。 序列化是将对象状态转换为可保持或传输的形式的过程。 有关详细信息，请参阅[序列化](../../csharp/programming-guide/concepts/serialization/index.md)。 当序列化非常重要时，创建 `class` 或优先 `struct` 于匿名类型或元组类型。

## <a name="performance"></a>性能

这些类型之间的性能取决于方案。 主要影响涉及分配和复制之间的权衡。 在大多数情况下，影响很小。 如果可能出现重大影响，则应采取度量来通知决策。

## <a name="conclusion"></a>结束语

当开发人员在元组和匿名类型之间进行选择时，需要考虑几个因素。 一般来说，如果您不使用[表达式树](../../csharp/expression-trees.md)，并且您习惯使用元组语法，则请选择 <xref:System.ValueTuple> 它们提供可灵活地命名属性的值类型。 如果使用表达式树，并且想要命名属性，请选择 "匿名类型"。 否则使用 <xref:System.Tuple>。

## <a name="see-also"></a>请参阅

- [匿名类型](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [表达式树](../../csharp/expression-trees.md)
- [框架设计准则](index.md)
- [元组类型](../../csharp/tuples.md)
- [类型设计准则](type.md)

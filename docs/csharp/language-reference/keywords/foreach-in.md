---
title: C# foreach 语句
ms.date: 06/03/2020
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 1645a246c9feee2a92c0d4e4bbeda47f0afde7d9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401883"
---
# <a name="foreach-in-c-reference"></a>foreach，in（C# 参考）

`foreach` 语句为类型实例中实现 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 接口的每个元素执行语句或语句块。 `foreach` 语句不局限于这些类型，它可应用于满足以下条件的任何类型的实例：

- 具有公共无参数 `GetEnumerator` 方法，其返回类型为类、结构或接口类型。
- `GetEnumerator` 方法的返回类型具有公共 `Current` 属性和公共无参数 `MoveNext` 方法（其返回类型为 <xref:System.Boolean>）。

在大多数情况下，`foreach` 会循环访问其中每个元素都是 `T` 类型的 `IEnumerable<T>` 表达式。 但是，这些元素可以是从 `Current` 属性的类型中进行隐式或显式转换的任何类型。 如果 `Current` 属性返回 `SomeType`，则元素的类型可能如下：

- `SomeType` 的任何基类。
- `SomeType` 实现的任何接口。

此外，如果 `SomeType` 是 `class` 或 `interface` 而不是 `sealed`，则元素的类型可能包括：

- 派生自 `SomeType` 的任何类型。
- 任何任意接口。 允许任何接口，因为任何接口都可以由派生自或实现 `SomeType` 的类实现。

可以使用与上述规则匹配的任何类型来声明迭代变量。 如果从 `SomeType` 转换为迭代变量的类型需要显式强制转换，则该操作可能在转换失败时引发 <xref:System.InvalidCastException>。

从 C# 7.3 开始，如果枚举器的 `Current` 属性返回 [引用返回值](ref.md#reference-return-values)（`ref T`，其中 `T` 为集合元素类型），就可以使用 `ref` 或 `ref readonly` 修饰符来声明迭代变量。

从 C# 8.0 开始，集合类型实现 <xref:System.Collections.Generic.IAsyncEnumerable%601> 接口时，`await` 运算符可以应用于 `foreach` 语句。 异步检索下一个元素时，可能会挂起循环的每次迭代。 默认情况下，在捕获的上下文中处理流元素。 如果要禁用上下文捕获，请使用 <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> 扩展方法。 有关同步上下文并捕获当前上下文的详细信息，请参阅有关[使用基于任务的异步模式](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)的文章。

在 `foreach` 语句块中的任何点上，可以使用 [break](break.md) 语句中断循环，或者可以使用 [continue](continue.md) 语句继续执行到循环中的下一次迭代。 还可以使用 [goto](goto.md)、[return](return.md) 或 [throw](throw.md) 语句退出 `foreach` 循环。

如果 `foreach` 语句应用为 `null`，则会引发 <xref:System.NullReferenceException>。 如果 `foreach` 语句的源集合为空，则 `foreach` 循环的正文不会被执行，而是被跳过。

## <a name="examples"></a>示例

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

以下示例介绍 `foreach` 语句的使用，其中包含实现 <xref:System.Collections.Generic.IEnumerable%601> 接口的 <xref:System.Collections.Generic.List%601> 类型的实例：

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="1" interactive="try-dotnet-method" :::

下一个示例使用 `foreach` 语句，其中包含 <xref:System.Span%601?displayProperty=nameWithType> 类型的实例，该实例不实现任何接口：

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="2" :::

下面的示例使用 `ref` 迭代变量来设置 stackalloc 数组中每个项的值。 `ref readonly` 版本循环访问该集合以打印所有值。 `readonly` 声明使用隐式局部变量声明。 隐式变量声明可与 `ref` 或 `ref readonly` 声明配合使用，显式类型化变量声明也一样。

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="RefSpan" :::

以下示例使用 `await foreach` 循环访问异步生成每个元素的集合：

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="AwaitForeach"  :::

## <a name="c-language-specification"></a>C# 语言规范

有关详细信息，请参阅 [C# 语言规范](/dotnet/csharp/language-reference/language-specification/introduction)中的 [foreach 语句](~/_csharplang/spec/statements.md#the-foreach-statement)部分。

## <a name="see-also"></a>请参阅

- [C# 参考](../index.md)
- [C# 编程指南](../../programming-guide/index.md)
- [C# 关键字](index.md)
- [对数组使用 foreach](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [for 语句](for.md)

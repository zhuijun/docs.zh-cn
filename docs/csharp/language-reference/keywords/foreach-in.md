---
description: foreach，in（C# 参考）
title: C# foreach 语句
ms.date: 09/18/2020
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: ea8a6f86595348a32b707caf9782f84147fefc87
ms.sourcegitcommit: 43ed174f085840ca18a791dc89fe833174da766d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/21/2020
ms.locfileid: "90828885"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="596b7-103">foreach，in（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="596b7-103">foreach, in (C# reference)</span></span>

<span data-ttu-id="596b7-104">`foreach` 语句为类型实例中实现 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 接口的每个元素执行语句或语句块，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="596b7-104">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface, as the following example shows:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="1" interactive="try-dotnet-method" :::

<span data-ttu-id="596b7-105">`foreach` 语句并不限于这些类型。</span><span class="sxs-lookup"><span data-stu-id="596b7-105">The `foreach` statement isn't limited to those types.</span></span> <span data-ttu-id="596b7-106">可以将其与满足以下条件的任何类型的实例一起使用：</span><span class="sxs-lookup"><span data-stu-id="596b7-106">You can use it with an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="596b7-107">类型具有公共无参数 `GetEnumerator` 方法，其返回类型为类、结构或接口类型。</span><span class="sxs-lookup"><span data-stu-id="596b7-107">A type has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type.</span></span> <span data-ttu-id="596b7-108">从 C# 9.0 开始，`GetEnumerator` 方法可以是类型的[扩展方法](../../programming-guide/classes-and-structs/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="596b7-108">Beginning with C# 9.0, the `GetEnumerator` method can be a type's [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>
- <span data-ttu-id="596b7-109">`GetEnumerator` 方法的返回类型具有公共 `Current` 属性和公共无参数 `MoveNext` 方法（其返回类型为 <xref:System.Boolean>）。</span><span class="sxs-lookup"><span data-stu-id="596b7-109">The return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="596b7-110">下面的示例使用 `foreach` 语句，其中包含 <xref:System.Span%601?displayProperty=nameWithType> 类型的实例，该实例不实现任何接口：</span><span class="sxs-lookup"><span data-stu-id="596b7-110">The following example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="2" :::

<span data-ttu-id="596b7-111">从 C# 7.3 开始，如果枚举器的 `Current` 属性返回[引用返回值](ref.md#reference-return-values)（`ref T`，其中 `T` 为集合元素类型），就可以使用 `ref` 或 `ref readonly` 修饰符来声明迭代变量，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="596b7-111">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](ref.md#reference-return-values) (`ref T` where `T` is the type of a collection element), you can declare an iteration variable with the `ref` or `ref readonly` modifier, as the following example shows:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="RefSpan" :::

<span data-ttu-id="596b7-112">从 C# 8.0 开始，可以使用 `await foreach` 语句来使用异步数据流，即实现 <xref:System.Collections.Generic.IAsyncEnumerable%601> 接口的集合类型。</span><span class="sxs-lookup"><span data-stu-id="596b7-112">Beginning with C# 8.0, you can use the `await foreach` statement to consume an asynchronous stream of data, that is, the collection type that implements the <xref:System.Collections.Generic.IAsyncEnumerable%601> interface.</span></span> <span data-ttu-id="596b7-113">异步检索下一个元素时，可能会挂起循环的每次迭代。</span><span class="sxs-lookup"><span data-stu-id="596b7-113">Each iteration of the loop may be suspended while the next element is retrieved asynchronously.</span></span> <span data-ttu-id="596b7-114">下面的示例演示如何使用 `await foreach` 语句：</span><span class="sxs-lookup"><span data-stu-id="596b7-114">The following example shows how to use the `await foreach` statement:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="AwaitForeach" :::

<span data-ttu-id="596b7-115">默认情况下，在捕获的上下文中处理流元素。</span><span class="sxs-lookup"><span data-stu-id="596b7-115">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="596b7-116">如果要禁用上下文捕获，请使用 <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> 扩展方法。</span><span class="sxs-lookup"><span data-stu-id="596b7-116">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="596b7-117">有关同步上下文并捕获当前上下文的详细信息，请参阅[使用基于任务的异步模式](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="596b7-117">For more information about synchronization contexts and capturing the current context, see [Consuming the Task-based asynchronous pattern](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span> <span data-ttu-id="596b7-118">有关异步流的详细信息，请参阅 [C# 8.0 新增功能](../../whats-new/csharp-8.md)一文中的[异步流](../../whats-new/csharp-8.md#asynchronous-streams)部分。</span><span class="sxs-lookup"><span data-stu-id="596b7-118">For more information about asynchronous streams, see the [Asynchronous streams](../../whats-new/csharp-8.md#asynchronous-streams) section of the [What's new in C# 8.0](../../whats-new/csharp-8.md) article.</span></span>

<span data-ttu-id="596b7-119">在 `foreach` 语句块中的任何点上，可以使用 [break](break.md) 语句中断循环，或者可以使用 [continue](continue.md) 语句继续执行到循环中的下一次迭代。</span><span class="sxs-lookup"><span data-stu-id="596b7-119">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="596b7-120">还可以使用 [goto](goto.md)、[return](return.md) 或 [throw](throw.md) 语句退出 `foreach` 循环。</span><span class="sxs-lookup"><span data-stu-id="596b7-120">You can also exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

<span data-ttu-id="596b7-121">如果 `foreach` 语句应用为 `null`，则会引发 <xref:System.NullReferenceException>。</span><span class="sxs-lookup"><span data-stu-id="596b7-121">If the `foreach` statement is applied to `null`, a <xref:System.NullReferenceException> is thrown.</span></span> <span data-ttu-id="596b7-122">如果 `foreach` 语句的源集合为空，则 `foreach` 循环的正文不会被执行，而是被跳过。</span><span class="sxs-lookup"><span data-stu-id="596b7-122">If the source collection of the `foreach` statement is empty, the body of the `foreach` loop isn't executed and skipped.</span></span>

## <a name="type-of-an-iteration-variable"></a><span data-ttu-id="596b7-123">迭代变量的类型</span><span class="sxs-lookup"><span data-stu-id="596b7-123">Type of an iteration variable</span></span>

<span data-ttu-id="596b7-124">可以使用 `var` 关键字让编译器推断 `foreach` 语句中迭代变量的类型，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="596b7-124">You can use the `var` keyword to let the compiler infer the type of an iteration variable in the `foreach` statement, as the following code shows:</span></span>

```csharp
foreach (var item in collection) { }
```

<span data-ttu-id="596b7-125">还可以显式指定迭代变量的类型，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="596b7-125">You can also explicitly specify the type of an iteration variable, as the following code shows:</span></span>

```csharp
IEnumerable<T> collection = new T[5];
foreach (V item in collection) { }
```

<span data-ttu-id="596b7-126">在上述窗体中，集合元素的类型 `T` 必须可隐式或显式地转换为迭代变量的类型 `V`。</span><span class="sxs-lookup"><span data-stu-id="596b7-126">In the preceding form, type `T` of a collection element must be implicitly or explicitly convertible to type `V` of an iteration variable.</span></span> <span data-ttu-id="596b7-127">如果从 `T` 到 `V` 的显式转换在运行时失败，`foreach` 语句将引发 <xref:System.InvalidCastException>。</span><span class="sxs-lookup"><span data-stu-id="596b7-127">If an explicit conversion from `T` to `V` fails at run time, the `foreach` statement throws an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="596b7-128">例如，如果 `T` 是非密封类类型，则 `V` 可以是任何接口类型，甚至可以是 `T` 未实现的接口类型。</span><span class="sxs-lookup"><span data-stu-id="596b7-128">For example, if `T` is a non-sealed class type, `V` can be any interface type, even the one that `T` doesn't implement.</span></span> <span data-ttu-id="596b7-129">在运行时，集合元素的类型可以是从 `T` 派生并且实际实现 `V` 的类型。</span><span class="sxs-lookup"><span data-stu-id="596b7-129">At run time, the type of a collection element may be the one that derives from `T` and actually implements `V`.</span></span> <span data-ttu-id="596b7-130">如果不是这样，则会引发 <xref:System.InvalidCastException>。</span><span class="sxs-lookup"><span data-stu-id="596b7-130">If that's not the case, an <xref:System.InvalidCastException> is thrown.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="596b7-131">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="596b7-131">C# language specification</span></span>

<span data-ttu-id="596b7-132">有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)中的 [foreach 语句](~/_csharplang/spec/statements.md#the-foreach-statement)部分。</span><span class="sxs-lookup"><span data-stu-id="596b7-132">For more information, see [The foreach statement](~/_csharplang/spec/statements.md#the-foreach-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="596b7-133">有关 C# 8.0 及更高版本中添加的功能的详细信息，请参阅以下功能建议说明：</span><span class="sxs-lookup"><span data-stu-id="596b7-133">For more information about features added in C# 8.0 and later, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="596b7-134">异步流 (C# 8.0)</span><span class="sxs-lookup"><span data-stu-id="596b7-134">Async streams (C# 8.0)</span></span>](~/_csharplang/proposals/csharp-8.0/async-streams.md)
- [<span data-ttu-id="596b7-135">扩展 `GetEnumerator` 支持 `foreach` 循环 (C# 9.0)</span><span class="sxs-lookup"><span data-stu-id="596b7-135">Extension `GetEnumerator` support for `foreach` loops (C# 9.0)</span></span>](~/_csharplang/proposals/csharp-9.0/extension-getenumerator.md)

## <a name="see-also"></a><span data-ttu-id="596b7-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="596b7-136">See also</span></span>

- [<span data-ttu-id="596b7-137">C# 参考</span><span class="sxs-lookup"><span data-stu-id="596b7-137">C# reference</span></span>](../index.md)
- [<span data-ttu-id="596b7-138">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="596b7-138">C# keywords</span></span>](index.md)
- [<span data-ttu-id="596b7-139">对数组使用 foreach</span><span class="sxs-lookup"><span data-stu-id="596b7-139">Using foreach with arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="596b7-140">for 语句</span><span class="sxs-lookup"><span data-stu-id="596b7-140">for statement</span></span>](for.md)

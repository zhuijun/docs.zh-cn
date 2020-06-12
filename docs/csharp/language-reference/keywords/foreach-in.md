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
# <a name="foreach-in-c-reference"></a><span data-ttu-id="75868-102">foreach，in（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="75868-102">foreach, in (C# reference)</span></span>

<span data-ttu-id="75868-103">`foreach` 语句为类型实例中实现 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 接口的每个元素执行语句或语句块。</span><span class="sxs-lookup"><span data-stu-id="75868-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="75868-104">`foreach` 语句不局限于这些类型，它可应用于满足以下条件的任何类型的实例：</span><span class="sxs-lookup"><span data-stu-id="75868-104">The `foreach` statement isn't limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="75868-105">具有公共无参数 `GetEnumerator` 方法，其返回类型为类、结构或接口类型。</span><span class="sxs-lookup"><span data-stu-id="75868-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="75868-106">`GetEnumerator` 方法的返回类型具有公共 `Current` 属性和公共无参数 `MoveNext` 方法（其返回类型为 <xref:System.Boolean>）。</span><span class="sxs-lookup"><span data-stu-id="75868-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="75868-107">在大多数情况下，`foreach` 会循环访问其中每个元素都是 `T` 类型的 `IEnumerable<T>` 表达式。</span><span class="sxs-lookup"><span data-stu-id="75868-107">In most uses, `foreach` iterates an `IEnumerable<T>` expression where each element is of type `T`.</span></span> <span data-ttu-id="75868-108">但是，这些元素可以是从 `Current` 属性的类型中进行隐式或显式转换的任何类型。</span><span class="sxs-lookup"><span data-stu-id="75868-108">However, the elements may be any type that has an implicit or explicit conversion from the type of the `Current` property.</span></span> <span data-ttu-id="75868-109">如果 `Current` 属性返回 `SomeType`，则元素的类型可能如下：</span><span class="sxs-lookup"><span data-stu-id="75868-109">If the `Current` property returns `SomeType`, the type of the elements may be:</span></span>

- <span data-ttu-id="75868-110">`SomeType` 的任何基类。</span><span class="sxs-lookup"><span data-stu-id="75868-110">Any of the base classes of `SomeType`.</span></span>
- <span data-ttu-id="75868-111">`SomeType` 实现的任何接口。</span><span class="sxs-lookup"><span data-stu-id="75868-111">Any of the interfaces implemented by `SomeType`.</span></span>

<span data-ttu-id="75868-112">此外，如果 `SomeType` 是 `class` 或 `interface` 而不是 `sealed`，则元素的类型可能包括：</span><span class="sxs-lookup"><span data-stu-id="75868-112">Furthermore, if `SomeType` is a `class` or an `interface` and not `sealed`, the type of elements may include:</span></span>

- <span data-ttu-id="75868-113">派生自 `SomeType` 的任何类型。</span><span class="sxs-lookup"><span data-stu-id="75868-113">Any type derived from `SomeType`.</span></span>
- <span data-ttu-id="75868-114">任何任意接口。</span><span class="sxs-lookup"><span data-stu-id="75868-114">Any arbitrary interface.</span></span> <span data-ttu-id="75868-115">允许任何接口，因为任何接口都可以由派生自或实现 `SomeType` 的类实现。</span><span class="sxs-lookup"><span data-stu-id="75868-115">Any interface is allowed because any interface may be implemented by a class derived from or implementing `SomeType`.</span></span>

<span data-ttu-id="75868-116">可以使用与上述规则匹配的任何类型来声明迭代变量。</span><span class="sxs-lookup"><span data-stu-id="75868-116">You may declare the iteration variable using any type that matches the preceding rules.</span></span> <span data-ttu-id="75868-117">如果从 `SomeType` 转换为迭代变量的类型需要显式强制转换，则该操作可能在转换失败时引发 <xref:System.InvalidCastException>。</span><span class="sxs-lookup"><span data-stu-id="75868-117">If the conversion from `SomeType` to the type of the iteration variable requires an explicit cast, that operation may throw an <xref:System.InvalidCastException> when the conversion fails.</span></span>

<span data-ttu-id="75868-118">从 C# 7.3 开始，如果枚举器的 `Current` 属性返回 [引用返回值](ref.md#reference-return-values)（`ref T`，其中 `T` 为集合元素类型），就可以使用 `ref` 或 `ref readonly` 修饰符来声明迭代变量。</span><span class="sxs-lookup"><span data-stu-id="75868-118">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](ref.md#reference-return-values) (`ref T` where `T` is the type of the collection element), you can declare the iteration variable with the `ref` or `ref readonly` modifier.</span></span>

<span data-ttu-id="75868-119">从 C# 8.0 开始，集合类型实现 <xref:System.Collections.Generic.IAsyncEnumerable%601> 接口时，`await` 运算符可以应用于 `foreach` 语句。</span><span class="sxs-lookup"><span data-stu-id="75868-119">Beginning with C# 8.0, the `await` operator may be applied to the `foreach` statement when the collection type implements the <xref:System.Collections.Generic.IAsyncEnumerable%601> interface.</span></span> <span data-ttu-id="75868-120">异步检索下一个元素时，可能会挂起循环的每次迭代。</span><span class="sxs-lookup"><span data-stu-id="75868-120">Each iteration of the loop may be suspended while the next element is retrieved asynchronously.</span></span> <span data-ttu-id="75868-121">默认情况下，在捕获的上下文中处理流元素。</span><span class="sxs-lookup"><span data-stu-id="75868-121">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="75868-122">如果要禁用上下文捕获，请使用 <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> 扩展方法。</span><span class="sxs-lookup"><span data-stu-id="75868-122">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="75868-123">有关同步上下文并捕获当前上下文的详细信息，请参阅有关[使用基于任务的异步模式](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)的文章。</span><span class="sxs-lookup"><span data-stu-id="75868-123">For more information about synchronization contexts and capturing the current context, see the article on [consuming the Task-based asynchronous pattern](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span>

<span data-ttu-id="75868-124">在 `foreach` 语句块中的任何点上，可以使用 [break](break.md) 语句中断循环，或者可以使用 [continue](continue.md) 语句继续执行到循环中的下一次迭代。</span><span class="sxs-lookup"><span data-stu-id="75868-124">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="75868-125">还可以使用 [goto](goto.md)、[return](return.md) 或 [throw](throw.md) 语句退出 `foreach` 循环。</span><span class="sxs-lookup"><span data-stu-id="75868-125">You can also exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

<span data-ttu-id="75868-126">如果 `foreach` 语句应用为 `null`，则会引发 <xref:System.NullReferenceException>。</span><span class="sxs-lookup"><span data-stu-id="75868-126">If the `foreach` statement is applied to `null`, a <xref:System.NullReferenceException> is thrown.</span></span> <span data-ttu-id="75868-127">如果 `foreach` 语句的源集合为空，则 `foreach` 循环的正文不会被执行，而是被跳过。</span><span class="sxs-lookup"><span data-stu-id="75868-127">If the source collection of the `foreach` statement is empty, the body of the `foreach` loop isn't executed and skipped.</span></span>

## <a name="examples"></a><span data-ttu-id="75868-128">示例</span><span class="sxs-lookup"><span data-stu-id="75868-128">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="75868-129">以下示例介绍 `foreach` 语句的使用，其中包含实现 <xref:System.Collections.Generic.IEnumerable%601> 接口的 <xref:System.Collections.Generic.List%601> 类型的实例：</span><span class="sxs-lookup"><span data-stu-id="75868-129">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="1" interactive="try-dotnet-method" :::

<span data-ttu-id="75868-130">下一个示例使用 `foreach` 语句，其中包含 <xref:System.Span%601?displayProperty=nameWithType> 类型的实例，该实例不实现任何接口：</span><span class="sxs-lookup"><span data-stu-id="75868-130">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="2" :::

<span data-ttu-id="75868-131">下面的示例使用 `ref` 迭代变量来设置 stackalloc 数组中每个项的值。</span><span class="sxs-lookup"><span data-stu-id="75868-131">The following example uses a `ref` iteration variable to set the value of each item in a stackalloc array.</span></span> <span data-ttu-id="75868-132">`ref readonly` 版本循环访问该集合以打印所有值。</span><span class="sxs-lookup"><span data-stu-id="75868-132">The `ref readonly` version iterates the collection to print all the values.</span></span> <span data-ttu-id="75868-133">`readonly` 声明使用隐式局部变量声明。</span><span class="sxs-lookup"><span data-stu-id="75868-133">The `readonly` declaration uses an implicit local variable declaration.</span></span> <span data-ttu-id="75868-134">隐式变量声明可与 `ref` 或 `ref readonly` 声明配合使用，显式类型化变量声明也一样。</span><span class="sxs-lookup"><span data-stu-id="75868-134">Implicit variable declarations can be used with either `ref` or `ref readonly` declarations, as can explicitly typed variable declarations.</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="RefSpan" :::

<span data-ttu-id="75868-135">以下示例使用 `await foreach` 循环访问异步生成每个元素的集合：</span><span class="sxs-lookup"><span data-stu-id="75868-135">The following example uses `await foreach` to iterate a collection that generates each element asynchronously:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="AwaitForeach"  :::

## <a name="c-language-specification"></a><span data-ttu-id="75868-136">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="75868-136">C# language specification</span></span>

<span data-ttu-id="75868-137">有关详细信息，请参阅 [C# 语言规范](/dotnet/csharp/language-reference/language-specification/introduction)中的 [foreach 语句](~/_csharplang/spec/statements.md#the-foreach-statement)部分。</span><span class="sxs-lookup"><span data-stu-id="75868-137">For more information, see [The foreach statement](~/_csharplang/spec/statements.md#the-foreach-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="75868-138">请参阅</span><span class="sxs-lookup"><span data-stu-id="75868-138">See also</span></span>

- [<span data-ttu-id="75868-139">C# 参考</span><span class="sxs-lookup"><span data-stu-id="75868-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="75868-140">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="75868-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="75868-141">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="75868-141">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="75868-142">对数组使用 foreach</span><span class="sxs-lookup"><span data-stu-id="75868-142">Using foreach with arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="75868-143">for 语句</span><span class="sxs-lookup"><span data-stu-id="75868-143">for statement</span></span>](for.md)

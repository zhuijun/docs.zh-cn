---
title: 计算表达式
description: '了解如何创建方便的语法，以便在 F # 中编写可使用控制流构造和绑定进行序列化和组合的计算。'
ms.date: 08/15/2020
f1_keywords:
- let!_FS
ms.openlocfilehash: 1649d8c57ea9e025d40ef6d39d92b96795964150
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812154"
---
# <a name="computation-expressions"></a><span data-ttu-id="6620a-103">计算表达式</span><span class="sxs-lookup"><span data-stu-id="6620a-103">Computation Expressions</span></span>

<span data-ttu-id="6620a-104">F # 中的计算表达式提供了一种方便的语法，用于写入可使用控制流结构和绑定进行序列化和组合的计算。</span><span class="sxs-lookup"><span data-stu-id="6620a-104">Computation expressions in F# provide a convenient syntax for writing computations that can be sequenced and combined using control flow constructs and bindings.</span></span> <span data-ttu-id="6620a-105">根据计算表达式的类型，可以将其视为表示 monad、monoids、monad 转换器和 applicative 函子的一种方法。</span><span class="sxs-lookup"><span data-stu-id="6620a-105">Depending on the kind of computation expression, they can be thought of as a way to express monads, monoids, monad transformers, and applicative functors.</span></span> <span data-ttu-id="6620a-106">但与其他语言不同 (如 Haskell) 中 *的 notation* ，它们不与单个抽象相关，也不依赖于宏或其他形式的元编程来实现方便且上下文相关的语法。</span><span class="sxs-lookup"><span data-stu-id="6620a-106">However, unlike other languages (such as *do-notation* in Haskell), they are not tied to a single abstraction, and do not rely on macros or other forms of metaprogramming to accomplish a convenient and context-sensitive syntax.</span></span>

## <a name="overview"></a><span data-ttu-id="6620a-107">概述</span><span class="sxs-lookup"><span data-stu-id="6620a-107">Overview</span></span>

<span data-ttu-id="6620a-108">计算可以采用多种形式。</span><span class="sxs-lookup"><span data-stu-id="6620a-108">Computations can take many forms.</span></span> <span data-ttu-id="6620a-109">最常见的计算形式是单线程执行，它易于理解和修改。</span><span class="sxs-lookup"><span data-stu-id="6620a-109">The most common form of computation is single-threaded execution, which is easy to understand and modify.</span></span> <span data-ttu-id="6620a-110">但是，并非所有形式的计算都像单线程执行一样简单。</span><span class="sxs-lookup"><span data-stu-id="6620a-110">However, not all forms of computation are as straightforward as single-threaded execution.</span></span> <span data-ttu-id="6620a-111">示例包括：</span><span class="sxs-lookup"><span data-stu-id="6620a-111">Some examples include:</span></span>

- <span data-ttu-id="6620a-112">非确定性计算</span><span class="sxs-lookup"><span data-stu-id="6620a-112">Non-deterministic computations</span></span>
- <span data-ttu-id="6620a-113">异步计算</span><span class="sxs-lookup"><span data-stu-id="6620a-113">Asynchronous computations</span></span>
- <span data-ttu-id="6620a-114">Effectful 计算</span><span class="sxs-lookup"><span data-stu-id="6620a-114">Effectful computations</span></span>
- <span data-ttu-id="6620a-115">生成计算</span><span class="sxs-lookup"><span data-stu-id="6620a-115">Generative computations</span></span>

<span data-ttu-id="6620a-116">通常，在应用程序的某些部分，您必须执行 *上下文相关* 的计算。</span><span class="sxs-lookup"><span data-stu-id="6620a-116">More generally, there are *context-sensitive* computations that you must perform in certain parts of an application.</span></span> <span data-ttu-id="6620a-117">编写上下文相关的代码可能会很难，因为在没有抽象的情况下，可以轻松地在给定上下文之外 "泄漏" 计算，以防您这样做。</span><span class="sxs-lookup"><span data-stu-id="6620a-117">Writing context-sensitive code can be challenging, as it is easy to "leak" computations outside of a given context without abstractions to prevent you from doing so.</span></span> <span data-ttu-id="6620a-118">这些抽象通常很难自行编写，这就是 F # 有一种通用的方法来执行所谓的 **计算表达式**。</span><span class="sxs-lookup"><span data-stu-id="6620a-118">These abstractions are often challenging to write by yourself, which is why F# has a generalized way to do so called **computation expressions**.</span></span>

<span data-ttu-id="6620a-119">计算表达式为区分上下文的计算提供统一的语法和抽象模型。</span><span class="sxs-lookup"><span data-stu-id="6620a-119">Computation expressions offer a uniform syntax and abstraction model for encoding context-sensitive computations.</span></span>

<span data-ttu-id="6620a-120">每个计算表达式都是由 *生成器* 类型支持的。</span><span class="sxs-lookup"><span data-stu-id="6620a-120">Every computation expression is backed by a *builder* type.</span></span> <span data-ttu-id="6620a-121">生成器类型定义可用于计算表达式的操作。</span><span class="sxs-lookup"><span data-stu-id="6620a-121">The builder type defines the operations that are available for the computation expression.</span></span> <span data-ttu-id="6620a-122">请参阅 [创建新类型的计算表达式](computation-expressions.md#creating-a-new-type-of-computation-expression)，其中显示了如何创建自定义计算表达式。</span><span class="sxs-lookup"><span data-stu-id="6620a-122">See [Creating a New Type of Computation Expression](computation-expressions.md#creating-a-new-type-of-computation-expression), which shows how to create a custom computation expression.</span></span>

### <a name="syntax-overview"></a><span data-ttu-id="6620a-123">语法概述</span><span class="sxs-lookup"><span data-stu-id="6620a-123">Syntax overview</span></span>

<span data-ttu-id="6620a-124">所有计算表达式具有以下形式：</span><span class="sxs-lookup"><span data-stu-id="6620a-124">All computation expressions have the following form:</span></span>

```fsharp
builder-expr { cexper }
```

<span data-ttu-id="6620a-125">其中， `builder-expr` 是用于定义计算表达式的生成器类型的名称， `cexper` 是计算表达式的表达式主体。</span><span class="sxs-lookup"><span data-stu-id="6620a-125">where `builder-expr` is the name of a builder type that defines the computation expression, and `cexper` is the expression body of the computation expression.</span></span> <span data-ttu-id="6620a-126">例如， `async` 计算表达式代码可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="6620a-126">For example, `async` computation expression code can look like this:</span></span>

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

<span data-ttu-id="6620a-127">计算表达式中有一种特殊的附加语法，如前面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="6620a-127">There is a special, additional syntax available within a computation expression, as shown in the previous example.</span></span> <span data-ttu-id="6620a-128">以下表达式窗体可用于计算表达式：</span><span class="sxs-lookup"><span data-stu-id="6620a-128">The following expression forms are possible with computation expressions:</span></span>

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

<span data-ttu-id="6620a-129">每个关键字和其他标准 F # 关键字仅在计算表达式中可用（如果已在后备生成器类型中定义）。</span><span class="sxs-lookup"><span data-stu-id="6620a-129">Each of these keywords, and other standard F# keywords are only available in a computation expression if they have been defined in the backing builder type.</span></span> <span data-ttu-id="6620a-130">此情况的唯一例外是 `match!` ，这本身就是语法，可以在结果中使用 `let!` 模式匹配。</span><span class="sxs-lookup"><span data-stu-id="6620a-130">The only exception to this is `match!`, which is itself syntactic sugar for the use of `let!` followed by a pattern match on the result.</span></span>

<span data-ttu-id="6620a-131">生成器类型是一个对象，该对象定义控制计算表达式片段的组合方式的特殊方法;也就是说，其方法控制计算表达式的行为方式。</span><span class="sxs-lookup"><span data-stu-id="6620a-131">The builder type is an object that defines special methods that govern the way the fragments of the computation expression are combined; that is, its methods control how the computation expression behaves.</span></span> <span data-ttu-id="6620a-132">描述生成器类的另一种方法是，它使您能够自定义多个 F # 构造（如循环和绑定）的操作。</span><span class="sxs-lookup"><span data-stu-id="6620a-132">Another way to describe a builder class is to say that it enables you to customize the operation of many F# constructs, such as loops and bindings.</span></span>

### `let!`

<span data-ttu-id="6620a-133">`let!`关键字将调用的结果绑定到一个名称：</span><span class="sxs-lookup"><span data-stu-id="6620a-133">The `let!` keyword binds the result of a call to another computation expression to a name:</span></span>

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

<span data-ttu-id="6620a-134">如果将对的计算表达式的调用绑定到 `let` ，则不会获得计算表达式的结果。</span><span class="sxs-lookup"><span data-stu-id="6620a-134">If you bind the call to a computation expression with `let`, you will not get the result of the computation expression.</span></span> <span data-ttu-id="6620a-135">而是将未 *实现* 的调用的值绑定到该计算表达式。</span><span class="sxs-lookup"><span data-stu-id="6620a-135">Instead, you will have bound the value of the *unrealized* call to that computation expression.</span></span> <span data-ttu-id="6620a-136">使用 `let!` 绑定到结果。</span><span class="sxs-lookup"><span data-stu-id="6620a-136">Use `let!` to bind to the result.</span></span>

<span data-ttu-id="6620a-137">`let!` 由 `Bind(x, f)` 生成器类型上的成员定义。</span><span class="sxs-lookup"><span data-stu-id="6620a-137">`let!` is defined by the `Bind(x, f)` member on the builder type.</span></span>

### `do!`

<span data-ttu-id="6620a-138">`do!`关键字用于调用一个计算表达式，该表达式返回 `unit` (由 `Zero` 生成器) 上的成员定义的类似类型：</span><span class="sxs-lookup"><span data-stu-id="6620a-138">The `do!` keyword is for calling a computation expression that returns a `unit`-like type (defined by the `Zero` member on the builder):</span></span>

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

<span data-ttu-id="6620a-139">对于 [异步工作流](asynchronous-workflows.md)，此类型为 `Async<unit>` 。</span><span class="sxs-lookup"><span data-stu-id="6620a-139">For the [async workflow](asynchronous-workflows.md), this type is `Async<unit>`.</span></span> <span data-ttu-id="6620a-140">对于其他计算表达式，类型可能是 `CExpType<unit>` 。</span><span class="sxs-lookup"><span data-stu-id="6620a-140">For other computation expressions, the type is likely to be `CExpType<unit>`.</span></span>

<span data-ttu-id="6620a-141">`do!` 由 `Bind(x, f)` 生成器类型上的成员定义，其中 `f` 生成 `unit` 。</span><span class="sxs-lookup"><span data-stu-id="6620a-141">`do!` is defined by the `Bind(x, f)` member on the builder type, where `f` produces a `unit`.</span></span>

### `yield`

<span data-ttu-id="6620a-142">`yield`关键字用于从计算表达式返回值，以便可以将其用作 <xref:System.Collections.Generic.IEnumerable%601> ：</span><span class="sxs-lookup"><span data-stu-id="6620a-142">The `yield` keyword is for returning a value from the computation expression so that it can be consumed as an <xref:System.Collections.Generic.IEnumerable%601>:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

<span data-ttu-id="6620a-143">在大多数情况下，调用方可以省略它。</span><span class="sxs-lookup"><span data-stu-id="6620a-143">In most cases, it can be omitted by callers.</span></span> <span data-ttu-id="6620a-144">若要忽略，最常见的方法 `yield` 是用 `->` 运算符：</span><span class="sxs-lookup"><span data-stu-id="6620a-144">The most common way to omit `yield` is with the `->` operator:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..10 -> i * i
    }

for sq in squares do
    printfn "%d" sq
```

<span data-ttu-id="6620a-145">对于更复杂的表达式，可能会产生许多不同的值，并且可能有条件地省略关键字：</span><span class="sxs-lookup"><span data-stu-id="6620a-145">For more complex expressions that might yield many different values, and perhaps conditionally, simply omitting the keyword can do:</span></span>

```fsharp
let weekdays includeWeekend =
    seq {
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then
            "Saturday"
            "Sunday"
    }
```

<span data-ttu-id="6620a-146">与 [c # 中的 yield 关键字](../../csharp/language-reference/keywords/yield.md)一样，计算表达式中的每个元素都是在迭代时重新生成的。</span><span class="sxs-lookup"><span data-stu-id="6620a-146">As with the [yield keyword in C#](../../csharp/language-reference/keywords/yield.md), each element in the computation expression is yielded back as it is iterated.</span></span>

<span data-ttu-id="6620a-147">`yield` 由 `Yield(x)` 生成器类型上的成员定义，其中 `x` 是要返回的项。</span><span class="sxs-lookup"><span data-stu-id="6620a-147">`yield` is defined by the `Yield(x)` member on the builder type, where `x` is the item to yield back.</span></span>

### `yield!`

<span data-ttu-id="6620a-148">`yield!`关键字用于从计算表达式平展值集合：</span><span class="sxs-lookup"><span data-stu-id="6620a-148">The `yield!` keyword is for flattening a collection of values from a computation expression:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..3 -> i * i
    }

let cubes =
    seq {
        for i in 1..3 -> i * i * i
    }

let squaresAndCubes =
    seq {
        yield! squares
        yield! cubes
    }

printfn "%A" squaresAndCubes // Prints - 1; 4; 9; 1; 8; 27
```

<span data-ttu-id="6620a-149">当计算时，由调用的计算表达式 `yield!` 将每次生成一个项，从而平展结果。</span><span class="sxs-lookup"><span data-stu-id="6620a-149">When evaluated, the computation expression called by `yield!` will have its items yielded back one-by-one, flattening the result.</span></span>

<span data-ttu-id="6620a-150">`yield!` 由 `YieldFrom(x)` 生成器类型上的成员定义，其中 `x` 是值的集合。</span><span class="sxs-lookup"><span data-stu-id="6620a-150">`yield!` is defined by the `YieldFrom(x)` member on the builder type, where `x` is a collection of values.</span></span>

<span data-ttu-id="6620a-151">与不同 `yield` ， `yield!` 必须显式指定。</span><span class="sxs-lookup"><span data-stu-id="6620a-151">Unlike `yield`, `yield!` must be explicitly specified.</span></span> <span data-ttu-id="6620a-152">它的行为在计算表达式中是隐式的。</span><span class="sxs-lookup"><span data-stu-id="6620a-152">Its behavior isn't implicit in computation expressions.</span></span>

### `return`

<span data-ttu-id="6620a-153">`return`关键字在与计算表达式对应的类型中包装值。</span><span class="sxs-lookup"><span data-stu-id="6620a-153">The `return` keyword wraps a value in the type corresponding to the computation expression.</span></span> <span data-ttu-id="6620a-154">除了使用计算表达式以外 `yield` ，它还用于 "完成" 计算表达式：</span><span class="sxs-lookup"><span data-stu-id="6620a-154">Aside from computation expressions using `yield`, it is used to "complete" a computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="6620a-155">`return` 由 `Return(x)` 生成器类型上的成员定义，其中 `x` 是要包装的项。</span><span class="sxs-lookup"><span data-stu-id="6620a-155">`return` is defined by the `Return(x)` member on the builder type, where `x` is the item to wrap.</span></span>

### `return!`

<span data-ttu-id="6620a-156">`return!`关键字实现计算表达式的值，并将结果与计算表达式对应的类型进行包装：</span><span class="sxs-lookup"><span data-stu-id="6620a-156">The `return!` keyword realizes the value of a computation expression and wraps that result in the type corresponding to the computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="6620a-157">`return!` 由 `ReturnFrom(x)` 生成器类型上的成员定义，其中 `x` 是另一个计算表达式。</span><span class="sxs-lookup"><span data-stu-id="6620a-157">`return!` is defined by the `ReturnFrom(x)` member on the builder type, where `x` is another computation expression.</span></span>

### `match!`

<span data-ttu-id="6620a-158">`match!`关键字允许您在其结果中内联调用另一个计算表达式和模式匹配：</span><span class="sxs-lookup"><span data-stu-id="6620a-158">The `match!` keyword allows you to inline a call to another computation expression and pattern match on its result:</span></span>

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

<span data-ttu-id="6620a-159">当使用调用计算表达式时 `match!` ，它将实现调用的结果，如 `let!` 。</span><span class="sxs-lookup"><span data-stu-id="6620a-159">When calling a computation expression with `match!`, it will realize the result of the call like `let!`.</span></span> <span data-ttu-id="6620a-160">这通常在调用计算表达式（其中的结果是 [可选](options.md)的）时使用。</span><span class="sxs-lookup"><span data-stu-id="6620a-160">This is often used when calling a computation expression where the result is an [optional](options.md).</span></span>

## <a name="built-in-computation-expressions"></a><span data-ttu-id="6620a-161">内置计算表达式</span><span class="sxs-lookup"><span data-stu-id="6620a-161">Built-in computation expressions</span></span>

<span data-ttu-id="6620a-162">F # 核心库定义了三个内置计算表达式： [序列表达式](sequences.md)、 [异步工作流](asynchronous-workflows.md)和 [查询表达式](query-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="6620a-162">The F# core library defines three built-in computation expressions: [Sequence Expressions](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Query Expressions](query-expressions.md).</span></span>

## <a name="creating-a-new-type-of-computation-expression"></a><span data-ttu-id="6620a-163">创建新类型的计算表达式</span><span class="sxs-lookup"><span data-stu-id="6620a-163">Creating a New Type of Computation Expression</span></span>

<span data-ttu-id="6620a-164">您可以通过创建生成器类并在类上定义某些特殊方法，定义自己的计算表达式的特征。</span><span class="sxs-lookup"><span data-stu-id="6620a-164">You can define the characteristics of your own computation expressions by creating a builder class and defining certain special methods on the class.</span></span> <span data-ttu-id="6620a-165">Builder 类可以选择定义下表中列出的方法。</span><span class="sxs-lookup"><span data-stu-id="6620a-165">The builder class can optionally define the methods as listed in the following table.</span></span>

<span data-ttu-id="6620a-166">下表描述了可在工作流生成器类中使用的方法。</span><span class="sxs-lookup"><span data-stu-id="6620a-166">The following table describes methods that can be used in a workflow builder class.</span></span>

|<span data-ttu-id="6620a-167">**方法**</span><span class="sxs-lookup"><span data-stu-id="6620a-167">**Method**</span></span>|<span data-ttu-id="6620a-168">\*\*典型签名 (s) \*\*</span><span class="sxs-lookup"><span data-stu-id="6620a-168">**Typical signature(s)**</span></span>|<span data-ttu-id="6620a-169">**说明**</span><span class="sxs-lookup"><span data-stu-id="6620a-169">**Description**</span></span>|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|<span data-ttu-id="6620a-170">`let!` `do!` 在计算表达式中为和调用。</span><span class="sxs-lookup"><span data-stu-id="6620a-170">Called for `let!` and `do!` in computation expressions.</span></span>|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|<span data-ttu-id="6620a-171">将计算表达式包装为函数。</span><span class="sxs-lookup"><span data-stu-id="6620a-171">Wraps a computation expression as a function.</span></span>|
|`Return`|`'T -> M<'T>`|<span data-ttu-id="6620a-172">`return`在计算表达式中调用。</span><span class="sxs-lookup"><span data-stu-id="6620a-172">Called for `return` in computation expressions.</span></span>|
|`ReturnFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="6620a-173">`return!`在计算表达式中调用。</span><span class="sxs-lookup"><span data-stu-id="6620a-173">Called for `return!` in computation expressions.</span></span>|
|`Run`|<span data-ttu-id="6620a-174">`M<'T> -> M<'T>` 或</span><span class="sxs-lookup"><span data-stu-id="6620a-174">`M<'T> -> M<'T>` or</span></span><br /><br />`M<'T> -> 'T`|<span data-ttu-id="6620a-175">执行计算表达式。</span><span class="sxs-lookup"><span data-stu-id="6620a-175">Executes a computation expression.</span></span>|
|`Combine`|<span data-ttu-id="6620a-176">`M<'T> * M<'T> -> M<'T>` 或</span><span class="sxs-lookup"><span data-stu-id="6620a-176">`M<'T> * M<'T> -> M<'T>` or</span></span><br /><br />`M<unit> * M<'T> -> M<'T>`|<span data-ttu-id="6620a-177">在计算表达式中调用以进行序列化。</span><span class="sxs-lookup"><span data-stu-id="6620a-177">Called for sequencing in computation expressions.</span></span>|
|`For`|<span data-ttu-id="6620a-178">`seq<'T> * ('T -> M<'U>) -> M<'U>` 或</span><span class="sxs-lookup"><span data-stu-id="6620a-178">`seq<'T> * ('T -> M<'U>) -> M<'U>` or</span></span><br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|<span data-ttu-id="6620a-179">为 `for...do` 计算表达式中的表达式调用。</span><span class="sxs-lookup"><span data-stu-id="6620a-179">Called for `for...do` expressions in computation expressions.</span></span>|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|<span data-ttu-id="6620a-180">为 `try...finally` 计算表达式中的表达式调用。</span><span class="sxs-lookup"><span data-stu-id="6620a-180">Called for `try...finally` expressions in computation expressions.</span></span>|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|<span data-ttu-id="6620a-181">为 `try...with` 计算表达式中的表达式调用。</span><span class="sxs-lookup"><span data-stu-id="6620a-181">Called for `try...with` expressions in computation expressions.</span></span>|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'T :> IDisposable`|<span data-ttu-id="6620a-182">`use`在计算表达式中为绑定调用。</span><span class="sxs-lookup"><span data-stu-id="6620a-182">Called for `use` bindings in computation expressions.</span></span>|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|<span data-ttu-id="6620a-183">为 `while...do` 计算表达式中的表达式调用。</span><span class="sxs-lookup"><span data-stu-id="6620a-183">Called for `while...do` expressions in computation expressions.</span></span>|
|`Yield`|`'T -> M<'T>`|<span data-ttu-id="6620a-184">为 `yield` 计算表达式中的表达式调用。</span><span class="sxs-lookup"><span data-stu-id="6620a-184">Called for `yield` expressions in computation expressions.</span></span>|
|`YieldFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="6620a-185">为 `yield!` 计算表达式中的表达式调用。</span><span class="sxs-lookup"><span data-stu-id="6620a-185">Called for `yield!` expressions in computation expressions.</span></span>|
|`Zero`|`unit -> M<'T>`|<span data-ttu-id="6620a-186">`else` `if...then` 在计算表达式中为表达式的空分支调用。</span><span class="sxs-lookup"><span data-stu-id="6620a-186">Called for empty `else` branches of `if...then` expressions in computation expressions.</span></span>|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|<span data-ttu-id="6620a-187">指示将计算表达式 `Run` 作为一个引号传递给成员。</span><span class="sxs-lookup"><span data-stu-id="6620a-187">Indicates that the computation expression is passed to the `Run` member as a quotation.</span></span> <span data-ttu-id="6620a-188">它将计算的所有实例都转换为引号。</span><span class="sxs-lookup"><span data-stu-id="6620a-188">It translates all instances of a computation into a quotation.</span></span>|

<span data-ttu-id="6620a-189">生成器类中的许多方法都使用并返回 `M<'T>` 构造，这通常是一种单独定义的类型，用于确定要合并的计算种类，例如， `Async<'T>` 对于异步工作流和 `Seq<'T>` 序列工作流。</span><span class="sxs-lookup"><span data-stu-id="6620a-189">Many of the methods in a builder class use and return an `M<'T>` construct, which is typically a separately defined type that characterizes the kind of computations being combined, for example, `Async<'T>` for asynchronous workflows and `Seq<'T>` for sequence workflows.</span></span> <span data-ttu-id="6620a-190">这些方法的签名使它们相互组合起来并彼此嵌套，以便可以将从一个构造返回的工作流对象传递到下一个构造。</span><span class="sxs-lookup"><span data-stu-id="6620a-190">The signatures of these methods enable them to be combined and nested with each other, so that the workflow object returned from one construct can be passed to the next.</span></span> <span data-ttu-id="6620a-191">编译器在分析计算表达式时，通过使用上表中的方法和计算表达式中的代码，将表达式转换为一系列嵌套函数调用。</span><span class="sxs-lookup"><span data-stu-id="6620a-191">The compiler, when it parses a computation expression, converts the expression into a series of nested function calls by using the methods in the preceding table and the code in the computation expression.</span></span>

<span data-ttu-id="6620a-192">嵌套表达式的格式如下：</span><span class="sxs-lookup"><span data-stu-id="6620a-192">The nested expression is of the following form:</span></span>

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

<span data-ttu-id="6620a-193">在上面的代码中， `Run` `Delay` 如果未在计算表达式生成器类中定义，则将忽略对和的调用。</span><span class="sxs-lookup"><span data-stu-id="6620a-193">In the above code, the calls to `Run` and `Delay` are omitted if they are not defined in the computation expression builder class.</span></span> <span data-ttu-id="6620a-194">下面的表中所述的翻译将计算表达式的主体（此处表示为 `{| cexpr |}` ）转换为涉及生成器类方法的调用。</span><span class="sxs-lookup"><span data-stu-id="6620a-194">The body of the computation expression, here denoted as `{| cexpr |}`, is translated into calls involving the methods of the builder class by the translations described in the following table.</span></span> <span data-ttu-id="6620a-195">`{| cexpr |}`根据这些转换以递归方式定义计算表达式，其中 `expr` 是 F # 表达式， `cexpr` 是计算表达式。</span><span class="sxs-lookup"><span data-stu-id="6620a-195">The computation expression `{| cexpr |}` is defined recursively according to these translations where `expr` is an F# expression and `cexpr` is a computation expression.</span></span>

|<span data-ttu-id="6620a-196">Expression</span><span class="sxs-lookup"><span data-stu-id="6620a-196">Expression</span></span>|<span data-ttu-id="6620a-197">翻译</span><span class="sxs-lookup"><span data-stu-id="6620a-197">Translation</span></span>|
|----------|-----------|
|<code>{ let binding in cexpr }</code>|<code>let binding in {&#124; cexpr &#124;}</code>|
|<code>{ let! pattern = expr in cexpr }</code>|<code>builder.Bind(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{ do! expr in cexpr }</code>|<code>builder.Bind(expr, (fun () -> {&#124; cexpr &#124;}))</code>|
|<code>{ yield expr }</code>|`builder.Yield(expr)`|
|<code>{ yield! expr }</code>|`builder.YieldFrom(expr)`|
|<code>{ return expr }</code>|`builder.Return(expr)`|
|<code>{ return! expr }</code>|`builder.ReturnFrom(expr)`|
|<code>{ use pattern = expr in cexpr }</code>|<code>builder.Using(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{ use! value = expr in cexpr }</code>|<code>builder.Bind(expr, (fun value -> builder.Using(value, (fun value -> { cexpr }))))</code>|
|<code>{ if expr then cexpr0 &#124;}</code>|<code>if expr then { cexpr0 } else builder.Zero()</code>|
|<code>{ if expr then cexpr0 else cexpr1 &#124;}</code>|<code>if expr then { cexpr0 } else { cexpr1 }</code>|
|<code>{ match expr with &#124; pattern_i -> cexpr_i }</code>|<code>match expr with &#124; pattern_i -> { cexpr_i }</code>|
|<code>{ for pattern in expr do cexpr }</code>|<code>builder.For(enumeration, (fun pattern -> { cexpr }))</code>|
|<code>{ for identifier = expr1 to expr2 do cexpr }</code>|<code>builder.For(enumeration, (fun identifier -> { cexpr }))</code>|
|<code>{ while expr do cexpr }</code>|<code>builder.While(fun () -> expr, builder.Delay({ cexpr }))</code>|
|<code>{ try cexpr with &#124; pattern_i -> expr_i }</code>|<code>builder.TryWith(builder.Delay({ cexpr }), (fun value -> match value with &#124; pattern_i -> expr_i &#124; exn -> reraise exn)))</code>|
|<code>{ try cexpr finally expr }</code>|<code>builder.TryFinally(builder.Delay( { cexpr }), (fun () -> expr))</code>|
|<code>{ cexpr1; cexpr2 }</code>|<code>builder.Combine({ cexpr1 }, { cexpr2 })</code>|
|<code>{ other-expr; cexpr }</code>|<code>expr; { cexpr }</code>|
|<code>{ other-expr }</code>|`expr; builder.Zero()`|

<span data-ttu-id="6620a-198">在上表中， `other-expr` 描述了表中未列出的表达式。</span><span class="sxs-lookup"><span data-stu-id="6620a-198">In the previous table, `other-expr` describes an expression that is not otherwise listed in the table.</span></span> <span data-ttu-id="6620a-199">生成器类不需要实现所有方法并支持上表中列出的所有翻译。</span><span class="sxs-lookup"><span data-stu-id="6620a-199">A builder class does not need to implement all of the methods and support all of the translations listed in the previous table.</span></span> <span data-ttu-id="6620a-200">未实现的这些构造在该类型的计算表达式中不可用。</span><span class="sxs-lookup"><span data-stu-id="6620a-200">Those constructs that are not implemented are not available in computation expressions of that type.</span></span> <span data-ttu-id="6620a-201">例如，如果不想 `use` 在计算表达式中支持关键字，则可以 `Use` 在生成器类中省略的定义。</span><span class="sxs-lookup"><span data-stu-id="6620a-201">For example, if you do not want to support the `use` keyword in your computation expressions, you can omit the definition of `Use` in your builder class.</span></span>

<span data-ttu-id="6620a-202">下面的代码示例演示一个计算表达式，该表达式将计算封装为一系列步骤，一次只能对一个步骤进行计算。</span><span class="sxs-lookup"><span data-stu-id="6620a-202">The following code example shows a computation expression that encapsulates a computation as a series of steps that can be evaluated one step at a time.</span></span> <span data-ttu-id="6620a-203">一种可区分联合类型，用于 `OkOrException` 对迄今为止计算的表达式的错误状态进行编码。</span><span class="sxs-lookup"><span data-stu-id="6620a-203">A discriminated union type, `OkOrException`, encodes the error state of the expression as evaluated so far.</span></span> <span data-ttu-id="6620a-204">此代码演示了几种可在计算表达式中使用的典型模式，如某些生成器方法的样本实现。</span><span class="sxs-lookup"><span data-stu-id="6620a-204">This code demonstrates several typical patterns that you can use in your computation expressions, such as boilerplate implementations of some of the builder methods.</span></span>

```fsharp
// Computations that can be run step by step
type Eventually<'T> =
    | Done of 'T
    | NotYetDone of (unit -> Eventually<'T>)

module Eventually =
    // The bind for the computations. Append 'func' to the
    // computation.
    let rec bind func expr =
        match expr with
        | Done value -> func value
        | NotYetDone work -> NotYetDone (fun () -> bind func (work()))

    // Return the final value wrapped in the Eventually type.
    let result value = Done value

    type OkOrException<'T> =
        | Ok of 'T
        | Exception of System.Exception

    // The catch for the computations. Stitch try/with throughout
    // the computation, and return the overall result as an OkOrException.
    let rec catch expr =
        match expr with
        | Done value -> result (Ok value)
        | NotYetDone work ->
            NotYetDone (fun () ->
                let res = try Ok(work()) with | exn -> Exception exn
                match res with
                | Ok cont -> catch cont // note, a tailcall
                | Exception exn -> result (Exception exn))

    // The delay operator.
    let delay func = NotYetDone (fun () -> func())

    // The stepping action for the computations.
    let step expr =
        match expr with
        | Done _ -> expr
        | NotYetDone func -> func ()

    // The rest of the operations are boilerplate.
    // The tryFinally operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryFinally expr compensation =
        catch (expr)
        |> bind (fun res ->
            compensation();
            match res with
            | Ok value -> result value
            | Exception exn -> raise exn)

    // The tryWith operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryWith exn handler =
        catch exn
        |> bind (function Ok value -> result value | Exception exn -> handler exn)

    // The whileLoop operator.
    // This is boilerplate in terms of "result" and "bind".
    let rec whileLoop pred body =
        if pred() then body |> bind (fun _ -> whileLoop pred body)
        else result ()

    // The sequential composition operator.
    // This is boilerplate in terms of "result" and "bind".
    let combine expr1 expr2 =
        expr1 |> bind (fun () -> expr2)

    // The using operator.
    let using (resource: #System.IDisposable) func =
        tryFinally (func resource) (fun () -> resource.Dispose())

    // The forLoop operator.
    // This is boilerplate in terms of "catch", "result", and "bind".
    let forLoop (collection:seq<_>) func =
        let ie = collection.GetEnumerator()
        tryFinally
            (whileLoop
                (fun () -> ie.MoveNext())
                (delay (fun () -> let value = ie.Current in func value)))
            (fun () -> ie.Dispose())

// The builder class.
type EventuallyBuilder() =
    member x.Bind(comp, func) = Eventually.bind func comp
    member x.Return(value) = Eventually.result value
    member x.ReturnFrom(value) = value
    member x.Combine(expr1, expr2) = Eventually.combine expr1 expr2
    member x.Delay(func) = Eventually.delay func
    member x.Zero() = Eventually.result ()
    member x.TryWith(expr, handler) = Eventually.tryWith expr handler
    member x.TryFinally(expr, compensation) = Eventually.tryFinally expr compensation
    member x.For(coll:seq<_>, func) = Eventually.forLoop coll func
    member x.Using(resource, expr) = Eventually.using resource expr

let eventually = new EventuallyBuilder()

let comp = eventually {
    for x in 1..2 do
        printfn " x = %d" x
    return 3 + 4 }

// Try the remaining lines in F# interactive to see how this
// computation expression works in practice.
let step x = Eventually.step x

// returns "NotYetDone <closure>"
comp |> step

// prints "x = 1"
// returns "NotYetDone <closure>"
comp |> step |> step

// prints "x = 1"
// prints "x = 2"
// returns "Done 7"
comp |> step |> step |> step |> step
```

<span data-ttu-id="6620a-205">计算表达式具有表达式返回的基础类型。</span><span class="sxs-lookup"><span data-stu-id="6620a-205">A computation expression has an underlying type, which the expression returns.</span></span> <span data-ttu-id="6620a-206">基础类型可能表示可以执行的计算结果或延迟计算，或者它可能提供一种方法来循环访问某些类型的集合。</span><span class="sxs-lookup"><span data-stu-id="6620a-206">The underlying type may represent a computed result or a delayed computation that can be performed, or it may provide a way to iterate through some type of collection.</span></span> <span data-ttu-id="6620a-207">在上面的示例中，基础类型 **最终**是。</span><span class="sxs-lookup"><span data-stu-id="6620a-207">In the previous example, the underlying type was **Eventually**.</span></span> <span data-ttu-id="6620a-208">对于序列表达式，基础类型是 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="6620a-208">For a sequence expression, the underlying type is <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6620a-209">对于查询表达式，基础类型是 <xref:System.Linq.IQueryable?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="6620a-209">For a query expression, the underlying type is <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6620a-210">对于异步工作流，基础类型是 [`Async`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync-1.html) 。</span><span class="sxs-lookup"><span data-stu-id="6620a-210">For an asynchronous workflow, the underlying type is [`Async`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync-1.html).</span></span> <span data-ttu-id="6620a-211">`Async`对象表示要执行的工作来计算结果。</span><span class="sxs-lookup"><span data-stu-id="6620a-211">The `Async` object represents the work to be performed to compute the result.</span></span> <span data-ttu-id="6620a-212">例如，调用 [`Async.RunSynchronously`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#RunSynchronously) 以执行计算并返回结果。</span><span class="sxs-lookup"><span data-stu-id="6620a-212">For example, you call [`Async.RunSynchronously`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#RunSynchronously) to execute a computation and return the result.</span></span>

## <a name="custom-operations"></a><span data-ttu-id="6620a-213">自定义操作</span><span class="sxs-lookup"><span data-stu-id="6620a-213">Custom Operations</span></span>

<span data-ttu-id="6620a-214">可以在计算表达式中定义自定义操作，并使用自定义操作作为计算表达式中的运算符。</span><span class="sxs-lookup"><span data-stu-id="6620a-214">You can define a custom operation on a computation expression and use a custom operation as an operator in a computation expression.</span></span> <span data-ttu-id="6620a-215">例如，可以在查询表达式中包含查询运算符。</span><span class="sxs-lookup"><span data-stu-id="6620a-215">For example, you can include a query operator in a query expression.</span></span> <span data-ttu-id="6620a-216">定义自定义操作时，必须在计算表达式中定义 Yield 和方法。</span><span class="sxs-lookup"><span data-stu-id="6620a-216">When you define a custom operation, you must define the Yield and For methods in the computation expression.</span></span> <span data-ttu-id="6620a-217">若要定义自定义操作，请将其放在计算表达式的 builder 类中，然后应用 [`CustomOperationAttribute`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-customoperationattribute.html) 。</span><span class="sxs-lookup"><span data-stu-id="6620a-217">To define a custom operation, put it in a builder class for the computation expression, and then apply the [`CustomOperationAttribute`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-customoperationattribute.html).</span></span> <span data-ttu-id="6620a-218">此属性采用字符串作为参数，该参数是要在自定义操作中使用的名称。</span><span class="sxs-lookup"><span data-stu-id="6620a-218">This attribute takes a string as an argument, which is the name to be used in a custom operation.</span></span> <span data-ttu-id="6620a-219">此名称将出现在计算表达式的左大括号开头的范围内。</span><span class="sxs-lookup"><span data-stu-id="6620a-219">This name comes into scope at the start of the opening curly brace of the computation expression.</span></span> <span data-ttu-id="6620a-220">因此，不应使用与此块中的自定义操作名称相同的标识符。</span><span class="sxs-lookup"><span data-stu-id="6620a-220">Therefore, you shouldn't use identifiers that have the same name as a custom operation in this block.</span></span> <span data-ttu-id="6620a-221">例如，避免在 `all` 查询表达式中使用标识符（如或） `last` 。</span><span class="sxs-lookup"><span data-stu-id="6620a-221">For example, avoid the use of identifiers such as `all` or `last` in query expressions.</span></span>

### <a name="extending-existing-builders-with-new-custom-operations"></a><span data-ttu-id="6620a-222">利用新的自定义操作扩展现有生成器</span><span class="sxs-lookup"><span data-stu-id="6620a-222">Extending existing Builders with new Custom Operations</span></span>

<span data-ttu-id="6620a-223">如果已经有一个生成器类，则可以从该生成器类的外部扩展其自定义操作。</span><span class="sxs-lookup"><span data-stu-id="6620a-223">If you already have a builder class, its custom operations can be extended from outside of this builder class.</span></span> <span data-ttu-id="6620a-224">扩展必须在模块中声明。</span><span class="sxs-lookup"><span data-stu-id="6620a-224">Extensions must be declared in modules.</span></span> <span data-ttu-id="6620a-225">命名空间不能包含在定义该类型的同一文件和相同的命名空间声明组中的扩展成员。</span><span class="sxs-lookup"><span data-stu-id="6620a-225">Namespaces cannot contain extension members except in the same file and the same namespace declaration group where the type is defined.</span></span>

<span data-ttu-id="6620a-226">下面的示例演示了现有类的扩展 `FSharp.Linq.QueryBuilder` 。</span><span class="sxs-lookup"><span data-stu-id="6620a-226">The following example shows the extension of the existing `FSharp.Linq.QueryBuilder` class.</span></span>

```fsharp
type FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member _.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a><span data-ttu-id="6620a-227">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6620a-227">See also</span></span>

- [<span data-ttu-id="6620a-228">F# 语言参考</span><span class="sxs-lookup"><span data-stu-id="6620a-228">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="6620a-229">异步工作流</span><span class="sxs-lookup"><span data-stu-id="6620a-229">Asynchronous Workflows</span></span>](asynchronous-workflows.md)
- [<span data-ttu-id="6620a-230">序列</span><span class="sxs-lookup"><span data-stu-id="6620a-230">Sequences</span></span>](sequences.md)
- [<span data-ttu-id="6620a-231">查询表达式</span><span class="sxs-lookup"><span data-stu-id="6620a-231">Query Expressions</span></span>](query-expressions.md)

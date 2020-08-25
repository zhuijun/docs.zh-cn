---
title: 异步编程
description: '了解 F # 如何基于从核心函数编程概念派生的语言级编程模型，为异步提供干净支持。'
ms.date: 08/15/2020
ms.openlocfilehash: 2e5d4fb744b4443eb9caf90cc1bf01473b809127
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811764"
---
# <a name="async-programming-in-f"></a><span data-ttu-id="e3f6b-103">F 中的异步编程\#</span><span class="sxs-lookup"><span data-stu-id="e3f6b-103">Async programming in F\#</span></span>

<span data-ttu-id="e3f6b-104">异步编程是一种对新式应用程序至关重要的机制，原因多种多样。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-104">Asynchronous programming is a mechanism that is essential to modern applications for diverse reasons.</span></span> <span data-ttu-id="e3f6b-105">大多数开发人员都将遇到两个主要用例：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-105">There are two primary use cases that most developers will encounter:</span></span>

- <span data-ttu-id="e3f6b-106">提供可为大量并发传入请求提供服务的服务器进程，同时最大限度地减少在请求处理过程中所占用的系统资源，等待来自该进程外部的系统或服务的输入</span><span class="sxs-lookup"><span data-stu-id="e3f6b-106">Presenting a server process that can service a significant number of concurrent incoming requests, while minimizing the system resources occupied while request processing awaits inputs from systems or services external to that process</span></span>
- <span data-ttu-id="e3f6b-107">在并发后台工作的同时维护响应式 UI 或主线程</span><span class="sxs-lookup"><span data-stu-id="e3f6b-107">Maintaining a responsive UI or main thread while concurrently progressing background work</span></span>

<span data-ttu-id="e3f6b-108">尽管后台工作通常涉及多个线程的使用率，但请务必分别考虑异步和多线程的概念。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-108">Although background work often does involve the utilization of multiple threads, it's important to consider the concepts of asynchrony and multi-threading separately.</span></span> <span data-ttu-id="e3f6b-109">事实上，它们是单独的问题，而另一个则不是。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-109">In fact, they are separate concerns, and one does not imply the other.</span></span> <span data-ttu-id="e3f6b-110">本文更详细地介绍了单独的概念。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-110">This article describes the separate concepts in more detail.</span></span>

## <a name="asynchrony-defined"></a><span data-ttu-id="e3f6b-111">已定义异步</span><span class="sxs-lookup"><span data-stu-id="e3f6b-111">Asynchrony defined</span></span>

<span data-ttu-id="e3f6b-112">之前的一点是，异步独立于多个线程的利用率，值得进一步解释。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-112">The previous point - that asynchrony is independent of the utilization of multiple threads - is worth explaining a bit further.</span></span> <span data-ttu-id="e3f6b-113">有时有三个相关概念，但彼此完全独立：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-113">There are three concepts that are sometimes related, but strictly independent of one another:</span></span>

- <span data-ttu-id="e3f6b-114">能力当多个计算在重叠的时间段内执行时。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-114">Concurrency; when multiple computations execute in overlapping time periods.</span></span>
- <span data-ttu-id="e3f6b-115">度当一个计算的多个计算或多个部分在同一时间运行时。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-115">Parallelism; when multiple computations or several parts of a single computation run at exactly the same time.</span></span>
- <span data-ttu-id="e3f6b-116">异步当一个或多个计算可与主程序流分开执行时。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-116">Asynchrony; when one or more computations can execute separately from the main program flow.</span></span>

<span data-ttu-id="e3f6b-117">这三种概念都是直角概念，但可以很容易地与父，尤其是在它们一起使用时。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-117">All three are orthogonal concepts, but can be easily conflated, especially when they are used together.</span></span> <span data-ttu-id="e3f6b-118">例如，可能需要并行执行多个异步计算。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-118">For example, you may need to execute multiple asynchronous computations in parallel.</span></span> <span data-ttu-id="e3f6b-119">这种关系并不意味着并行或异步彼此不同。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-119">This relationship does not mean that parallelism or asynchrony imply one another.</span></span>

<span data-ttu-id="e3f6b-120">如果你考虑 "异步" 一词的 etymology，则涉及两个部分：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-120">If you consider the etymology of the word "asynchronous", there are two pieces involved:</span></span>

- <span data-ttu-id="e3f6b-121">"a"，表示 "not"。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-121">"a", meaning "not".</span></span>
- <span data-ttu-id="e3f6b-122">"同步"，表示 "同时"。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-122">"synchronous", meaning "at the same time".</span></span>

<span data-ttu-id="e3f6b-123">将这两个术语组合在一起后，会看到 "异步" 表示 "不同时"。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-123">When you put these two terms together, you'll see that "asynchronous" means "not at the same time".</span></span> <span data-ttu-id="e3f6b-124">就这么简单！</span><span class="sxs-lookup"><span data-stu-id="e3f6b-124">That's it!</span></span> <span data-ttu-id="e3f6b-125">此定义中不存在并发或并行性的含义。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-125">There is no implication of concurrency or parallelism in this definition.</span></span> <span data-ttu-id="e3f6b-126">实际上也是如此。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-126">This is also true in practice.</span></span>

<span data-ttu-id="e3f6b-127">在实际情况下，F # 中的异步计算计划为独立于主程序流执行。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-127">In practical terms, asynchronous computations in F# are scheduled to execute independently of the main program flow.</span></span> <span data-ttu-id="e3f6b-128">此独立执行并不意味着并发性或并行性，也不表示计算始终发生在后台。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-128">This independent execution doesn't imply concurrency or parallelism, nor does it imply that a computation always happens in the background.</span></span> <span data-ttu-id="e3f6b-129">事实上，异步计算甚至可以同步执行，具体取决于计算的性质和正在执行计算的环境。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-129">In fact, asynchronous computations can even execute synchronously, depending on the nature of the computation and the environment the computation is executing in.</span></span>

<span data-ttu-id="e3f6b-130">应该具有的主要要点在于是异步计算与主程序流无关。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-130">The main takeaway you should have is that asynchronous computations are independent of the main program flow.</span></span> <span data-ttu-id="e3f6b-131">尽管对异步计算的执行时间或方式有一些保证，但还是有一些用于协调和安排这些方法的方法。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-131">Although there are few guarantees about when or how an asynchronous computation executes, there are some approaches to orchestrating and scheduling them.</span></span> <span data-ttu-id="e3f6b-132">本文的其余部分将探讨 F # 异步的核心概念，以及如何使用 F # 中内置的类型、函数和表达式。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-132">The rest of this article explores core concepts for F# asynchrony and how to use the types, functions, and expressions built into F#.</span></span>

## <a name="core-concepts"></a><span data-ttu-id="e3f6b-133">核心概念</span><span class="sxs-lookup"><span data-stu-id="e3f6b-133">Core concepts</span></span>

<span data-ttu-id="e3f6b-134">在 F # 中，异步编程围绕三个核心概念：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-134">In F#, asynchronous programming is centered around three core concepts:</span></span>

- <span data-ttu-id="e3f6b-135">`Async<'T>`类型，它表示可组合的异步计算。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-135">The `Async<'T>` type, which represents a composable asynchronous computation.</span></span>
- <span data-ttu-id="e3f6b-136">`Async`模块函数，可让你计划异步工作、撰写异步计算以及转换异步结果。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-136">The `Async` module functions, which let you schedule asynchronous work, compose asynchronous computations, and transform asynchronous results.</span></span>
- <span data-ttu-id="e3f6b-137">`async { }`[计算表达式](../../language-reference/computation-expressions.md)，提供用于生成和控制异步计算的方便语法。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-137">The `async { }` [computation expression](../../language-reference/computation-expressions.md), which provides a convenient syntax for building and controlling asynchronous computations.</span></span>

<span data-ttu-id="e3f6b-138">在以下示例中，可以看到这三个概念：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-138">You can see these three concepts in the following example:</span></span>

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    printTotalFileBytes "path-to-file.txt"
    |> Async.RunSynchronously

    Console.Read() |> ignore
    0
```

<span data-ttu-id="e3f6b-139">在此示例中， `printTotalFileBytes` 函数的类型为 `string -> Async<unit>` 。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-139">In the example, the `printTotalFileBytes` function is of type `string -> Async<unit>`.</span></span> <span data-ttu-id="e3f6b-140">调用函数实际上不会执行异步计算。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-140">Calling the function does not actually execute the asynchronous computation.</span></span> <span data-ttu-id="e3f6b-141">相反，它会返回一个 `Async<unit>` ，它充当要异步执行的工作的 *规范* 。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-141">Instead, it returns an `Async<unit>` that acts as a *specification* of the work that is to execute asynchronously.</span></span> <span data-ttu-id="e3f6b-142">它 `Async.AwaitTask` 在其正文中调用，后者将的结果转换 <xref:System.IO.File.ReadAllBytesAsync%2A> 为适当的类型。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-142">It calls `Async.AwaitTask` in its body, which converts the result of <xref:System.IO.File.ReadAllBytesAsync%2A> to an appropriate type.</span></span>

<span data-ttu-id="e3f6b-143">另一个重要的行是对的调用 `Async.RunSynchronously` 。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-143">Another important line is the call to `Async.RunSynchronously`.</span></span> <span data-ttu-id="e3f6b-144">这是要实际执行 F # 异步计算时需要调用的异步模块启动函数之一。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-144">This is one of the Async module starting functions that you'll need to call if you want to actually execute an F# asynchronous computation.</span></span>

<span data-ttu-id="e3f6b-145">这与 c #/Visual 基本的编程方式之间存在根本性的差别 `async` 。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-145">This is a fundamental difference with the C#/Visual Basic style of `async` programming.</span></span> <span data-ttu-id="e3f6b-146">在 F # 中，可将异步计算视为 **冷任务**。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-146">In F#, asynchronous computations can be thought of as **Cold tasks**.</span></span> <span data-ttu-id="e3f6b-147">它们必须显式启动才能实际执行。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-147">They must be explicitly started to actually execute.</span></span> <span data-ttu-id="e3f6b-148">这有一些优点，因为它允许你像在 c # 或 Visual Basic 中更轻松地组合和序列化异步工作。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-148">This has some advantages, as it allows you to combine and sequence asynchronous work much more easily than in C# or Visual Basic.</span></span>

## <a name="combine-asynchronous-computations"></a><span data-ttu-id="e3f6b-149">合并异步计算</span><span class="sxs-lookup"><span data-stu-id="e3f6b-149">Combine asynchronous computations</span></span>

<span data-ttu-id="e3f6b-150">下面是通过组合计算在上一个示例中生成的示例：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-150">Here is an example that builds upon the previous one by combining computations:</span></span>

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    argv
    |> Array.map printTotalFileBytes
    |> Async.Parallel
    |> Async.Ignore
    |> Async.RunSynchronously

    0
```

<span data-ttu-id="e3f6b-151">正如您所看到的，该 `main` 函数有更多调用次数。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-151">As you can see, the `main` function has quite a few more calls made.</span></span> <span data-ttu-id="e3f6b-152">从概念上讲，它执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-152">Conceptually, it does the following:</span></span>

1. <span data-ttu-id="e3f6b-153">将命令行参数转换为 `Async<unit>` 具有的计算结果 `Array.map` 。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-153">Transform the command-line arguments into `Async<unit>` computations with `Array.map`.</span></span>
2. <span data-ttu-id="e3f6b-154">创建一个 `Async<'T[]>` 计划并 `printTotalFileBytes` 在运行时并行运行计算的。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-154">Create an `Async<'T[]>` that schedules and runs the `printTotalFileBytes` computations in parallel when it runs.</span></span>
3. <span data-ttu-id="e3f6b-155">创建一个 `Async<unit>` 将运行并行计算并忽略其结果的。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-155">Create an `Async<unit>` that will run the parallel computation and ignore its result.</span></span>
4. <span data-ttu-id="e3f6b-156">用显式运行上次计算 `Async.RunSynchronously` ，并在完成之前一直阻止。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-156">Explicitly run the last computation with `Async.RunSynchronously` and block until it completes.</span></span>

<span data-ttu-id="e3f6b-157">运行此程序时，将 `printTotalFileBytes` 并行运行每个命令行参数。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-157">When this program runs, `printTotalFileBytes` runs in parallel for each command-line argument.</span></span> <span data-ttu-id="e3f6b-158">由于异步计算独立于程序流执行，因此它们不会打印其信息并完成执行。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-158">Because asynchronous computations execute independently of program flow, there is no order in which they print their information and finish executing.</span></span> <span data-ttu-id="e3f6b-159">将并行计划计算，但不保证其执行顺序。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-159">The computations will be scheduled in parallel, but their order of execution is not guaranteed.</span></span>

## <a name="sequence-asynchronous-computations"></a><span data-ttu-id="e3f6b-160">序列异步计算</span><span class="sxs-lookup"><span data-stu-id="e3f6b-160">Sequence asynchronous computations</span></span>

<span data-ttu-id="e3f6b-161">由于 `Async<'T>` 是一项规范，而不是已运行的任务，因此您可以轻松地执行更复杂的转换。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-161">Because `Async<'T>` is a specification of work rather than an already-running task, you can perform more intricate transformations easily.</span></span> <span data-ttu-id="e3f6b-162">下面是一个示例，该示例对一组异步计算进行排序，以便它们逐个执行。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-162">Here is an example that sequences a set of Async computations so they execute one after another.</span></span>

```fsharp
let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    argv
    |> Array.map printTotalFileBytes
    |> Async.Sequential
    |> Async.Ignore
    |> Async.RunSynchronously
    |> ignore
```

<span data-ttu-id="e3f6b-163">这会计划按 `printTotalFileBytes` 元素的顺序执行， `argv` 而不是以并行方式进行调度。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-163">This will schedule `printTotalFileBytes` to execute in the order of the elements of `argv` rather than scheduling them in parallel.</span></span> <span data-ttu-id="e3f6b-164">因为在上一次计算执行完成后将不会计划下一项，所以，计算的顺序就是在执行时没有重叠。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-164">Because the next item will not be scheduled until after the last computation has finished executing, the computations are sequenced such that there is no overlap in their execution.</span></span>

## <a name="important-async-module-functions"></a><span data-ttu-id="e3f6b-165">重要的异步模块函数</span><span class="sxs-lookup"><span data-stu-id="e3f6b-165">Important Async module functions</span></span>

<span data-ttu-id="e3f6b-166">在 F # 中编写异步代码时，通常会与用于处理计算计划的框架交互。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-166">When you write async code in F#, you'll usually interact with a framework that handles scheduling of computations for you.</span></span> <span data-ttu-id="e3f6b-167">但是，这并不总是如此，因此最好了解用于计划异步工作的各种开始函数。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-167">However, this is not always the case, so it is good to learn the various starting functions to schedule asynchronous work.</span></span>

<span data-ttu-id="e3f6b-168">由于 F # 异步计算是工作 _规范_ ，而不是已执行的工作表示形式，因此必须使用启动函数显式启动它们。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-168">Because F# asynchronous computations are a _specification_ of work rather than a representation of work that is already executing, they must be explicitly started with a starting function.</span></span> <span data-ttu-id="e3f6b-169">许多 [异步启动方法](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#section0) 在不同的上下文中很有用。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-169">There are many [Async starting methods](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#section0) that are helpful in different contexts.</span></span> <span data-ttu-id="e3f6b-170">以下部分介绍了一些更常见的启动函数。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-170">The following section describes some of the more common starting functions.</span></span>

### <a name="asyncstartchild"></a><span data-ttu-id="e3f6b-171">StartChild</span><span class="sxs-lookup"><span data-stu-id="e3f6b-171">Async.StartChild</span></span>

<span data-ttu-id="e3f6b-172">在异步计算中启动子计算。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-172">Starts a child computation within an asynchronous computation.</span></span> <span data-ttu-id="e3f6b-173">这允许并发执行多个异步计算。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-173">This allows multiple asynchronous computations to be executed concurrently.</span></span> <span data-ttu-id="e3f6b-174">子计算与父计算共享取消标记。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-174">The child computation shares a cancellation token with the parent computation.</span></span> <span data-ttu-id="e3f6b-175">如果取消了父计算，则子计算也将被取消。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-175">If the parent computation is canceled, the child computation is also canceled.</span></span>

<span data-ttu-id="e3f6b-176">签名：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-176">Signature:</span></span>

```fsharp
computation: Async<'T> * timeout: ?int -> Async<Async<'T>>
```

<span data-ttu-id="e3f6b-177">使用场合：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-177">When to use:</span></span>

- <span data-ttu-id="e3f6b-178">如果要同时执行多个异步计算，而不是一次执行多个异步计算，但不需要并行计划它们。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-178">When you want to execute multiple asynchronous computations concurrently rather than one at a time, but not have them scheduled in parallel.</span></span>
- <span data-ttu-id="e3f6b-179">如果希望将子计算的生存期与父计算的生存期关联，则为。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-179">When you wish to tie the lifetime of a child computation to that of a parent computation.</span></span>

<span data-ttu-id="e3f6b-180">需要注意的事项：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-180">What to watch out for:</span></span>

- <span data-ttu-id="e3f6b-181">启动多个计算与 `Async.StartChild` 并行计划它们不同。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-181">Starting multiple computations with `Async.StartChild` isn't the same as scheduling them in parallel.</span></span> <span data-ttu-id="e3f6b-182">如果要并行计划计算，请使用 `Async.Parallel` 。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-182">If you wish to schedule computations in parallel, use `Async.Parallel`.</span></span>
- <span data-ttu-id="e3f6b-183">取消父计算将触发它开始的所有子计算的取消。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-183">Canceling a parent computation will trigger cancellation of all child computations it started.</span></span>

### <a name="asyncstartimmediate"></a><span data-ttu-id="e3f6b-184">StartImmediate</span><span class="sxs-lookup"><span data-stu-id="e3f6b-184">Async.StartImmediate</span></span>

<span data-ttu-id="e3f6b-185">运行异步计算，在当前操作系统线程上立即启动。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-185">Runs an asynchronous computation, starting immediately on the current operating system thread.</span></span> <span data-ttu-id="e3f6b-186">如果需要在计算过程中在调用线程上更新某些内容，这会很有帮助。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-186">This is helpful if you need to update something on the calling thread during the computation.</span></span> <span data-ttu-id="e3f6b-187">例如，如果异步计算必须更新 UI (例如更新进度栏) ，则 `Async.StartImmediate` 应使用。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-187">For example, if an asynchronous computation must update a UI (such as updating a progress bar), then `Async.StartImmediate` should be used.</span></span>

<span data-ttu-id="e3f6b-188">签名：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-188">Signature:</span></span>

```fsharp
computation: Async<unit> * cancellationToken: ?CancellationToken -> unit
```

<span data-ttu-id="e3f6b-189">使用场合：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-189">When to use:</span></span>

- <span data-ttu-id="e3f6b-190">需要在异步计算的中间对调用线程进行更新时。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-190">When you need to update something on the calling thread in the middle of an asynchronous computation.</span></span>

<span data-ttu-id="e3f6b-191">需要注意的事项：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-191">What to watch out for:</span></span>

- <span data-ttu-id="e3f6b-192">异步计算中的代码将在要计划的任何线程上运行。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-192">Code in the asynchronous computation will run on whatever thread one happens to be scheduled on.</span></span> <span data-ttu-id="e3f6b-193">如果该线程以某种方式（例如，UI 线程）进行敏感，则可能会出现问题。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-193">This can be problematic if that thread is in some way sensitive, such as a UI thread.</span></span> <span data-ttu-id="e3f6b-194">在这种情况下， `Async.StartImmediate` 可能不适合使用。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-194">In such cases, `Async.StartImmediate` is likely inappropriate to use.</span></span>

### <a name="asyncstartastask"></a><span data-ttu-id="e3f6b-195">Async.startastask</span><span class="sxs-lookup"><span data-stu-id="e3f6b-195">Async.StartAsTask</span></span>

<span data-ttu-id="e3f6b-196">在线程池中执行计算。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-196">Executes a computation in the thread pool.</span></span> <span data-ttu-id="e3f6b-197">返回一个 <xref:System.Threading.Tasks.Task%601> ，它将在计算终止 (生成结果、引发异常或取消) 后，在相应的状态下完成。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-197">Returns a <xref:System.Threading.Tasks.Task%601> that will be completed on the corresponding state once the computation terminates (produces the result, throws exception, or gets canceled).</span></span> <span data-ttu-id="e3f6b-198">如果未提供取消标记，则使用默认取消标记。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-198">If no cancellation token is provided, then the default cancellation token is used.</span></span>

<span data-ttu-id="e3f6b-199">签名：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-199">Signature:</span></span>

```fsharp
computation: Async<'T> * taskCreationOptions: ?TaskCreationOptions * cancellationToken: ?CancellationToken -> Task<'T>
```

<span data-ttu-id="e3f6b-200">使用场合：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-200">When to use:</span></span>

- <span data-ttu-id="e3f6b-201">需要调入需要的 .NET API 来 <xref:System.Threading.Tasks.Task%601> 表示异步计算的结果时。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-201">When you need to call into a .NET API that expects a <xref:System.Threading.Tasks.Task%601> to represent the result of an asynchronous computation.</span></span>

<span data-ttu-id="e3f6b-202">需要注意的事项：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-202">What to watch out for:</span></span>

- <span data-ttu-id="e3f6b-203">此调用将分配一个额外的 `Task` 对象，如果经常使用此对象，则可能会增加开销。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-203">This call will allocate an additional `Task` object, which can increase overhead if it is used often.</span></span>

### <a name="asyncparallel"></a><span data-ttu-id="e3f6b-204">Async 并行</span><span class="sxs-lookup"><span data-stu-id="e3f6b-204">Async.Parallel</span></span>

<span data-ttu-id="e3f6b-205">计划要并行执行的异步计算序列。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-205">Schedules a sequence of asynchronous computations to be executed in parallel.</span></span> <span data-ttu-id="e3f6b-206">通过指定参数，可以选择性地优化/限制并行度 `maxDegreesOfParallelism` 。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-206">The degree of parallelism can be optionally tuned/throttled by specifying the `maxDegreesOfParallelism` parameter.</span></span>

<span data-ttu-id="e3f6b-207">签名：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-207">Signature:</span></span>

```fsharp
computations: seq<Async<'T>> * ?maxDegreesOfParallelism: int -> Async<'T[]>
```

<span data-ttu-id="e3f6b-208">何时使用:</span><span class="sxs-lookup"><span data-stu-id="e3f6b-208">When to use it:</span></span>

- <span data-ttu-id="e3f6b-209">如果需要同时运行一组计算，而不依赖于其执行顺序。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-209">If you need to run a set of computations at the same time and have no reliance on their order of execution.</span></span>
- <span data-ttu-id="e3f6b-210">如果无需并行计划的计算结果，直到它们全部完成。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-210">If you don't require results from computations scheduled in parallel until they have all completed.</span></span>

<span data-ttu-id="e3f6b-211">需要注意的事项：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-211">What to watch out for:</span></span>

- <span data-ttu-id="e3f6b-212">所有计算完成后，只能访问生成的值数组。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-212">You can only access the resulting array of values once all computations have finished.</span></span>
- <span data-ttu-id="e3f6b-213">每当计算结束时，计算都将运行。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-213">Computations will be run whenever they end up getting scheduled.</span></span> <span data-ttu-id="e3f6b-214">此行为意味着你不能依赖其执行顺序。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-214">This behavior means you cannot rely on their order of their execution.</span></span>

### <a name="asyncsequential"></a><span data-ttu-id="e3f6b-215">异步顺序</span><span class="sxs-lookup"><span data-stu-id="e3f6b-215">Async.Sequential</span></span>

<span data-ttu-id="e3f6b-216">计划一系列要按其传递顺序执行的异步计算。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-216">Schedules a sequence of asynchronous computations to be executed in the order that they are passed.</span></span> <span data-ttu-id="e3f6b-217">将执行第一个计算，然后执行下一次计算，依次类推。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-217">The first computation will be executed, then the next, and so on.</span></span> <span data-ttu-id="e3f6b-218">不会并行执行任何计算。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-218">No computations will be executed in parallel.</span></span>

<span data-ttu-id="e3f6b-219">签名：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-219">Signature:</span></span>

```fsharp
computations: seq<Async<'T>> -> Async<'T[]>
```

<span data-ttu-id="e3f6b-220">何时使用:</span><span class="sxs-lookup"><span data-stu-id="e3f6b-220">When to use it:</span></span>

- <span data-ttu-id="e3f6b-221">如果需要按顺序执行多个计算。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-221">If you need to execute multiple computations in order.</span></span>

<span data-ttu-id="e3f6b-222">需要注意的事项：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-222">What to watch out for:</span></span>

- <span data-ttu-id="e3f6b-223">所有计算完成后，只能访问生成的值数组。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-223">You can only access the resulting array of values once all computations have finished.</span></span>
- <span data-ttu-id="e3f6b-224">计算将按其传递到此函数的顺序运行，这可能意味着返回结果之前需要更多时间。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-224">Computations will be run in the order that they are passed to this function, which can mean that more time will elapse before the results are returned.</span></span>

### <a name="asyncawaittask"></a><span data-ttu-id="e3f6b-225">Async.awaittask</span><span class="sxs-lookup"><span data-stu-id="e3f6b-225">Async.AwaitTask</span></span>

<span data-ttu-id="e3f6b-226">返回一个异步计算，该计算等待给定的 <xref:System.Threading.Tasks.Task%601> 完成，并将其结果作为 `Async<'T>`</span><span class="sxs-lookup"><span data-stu-id="e3f6b-226">Returns an asynchronous computation that waits for the given <xref:System.Threading.Tasks.Task%601> to complete and returns its result as an `Async<'T>`</span></span>

<span data-ttu-id="e3f6b-227">签名：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-227">Signature:</span></span>

```fsharp
task: Task<'T> -> Async<'T>
```

<span data-ttu-id="e3f6b-228">使用场合：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-228">When to use:</span></span>

- <span data-ttu-id="e3f6b-229">当你使用的 .NET API 在 <xref:System.Threading.Tasks.Task%601> F # 异步计算中返回时。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-229">When you are consuming a .NET API that returns a <xref:System.Threading.Tasks.Task%601> within an F# asynchronous computation.</span></span>

<span data-ttu-id="e3f6b-230">需要注意的事项：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-230">What to watch out for:</span></span>

- <span data-ttu-id="e3f6b-231"><xref:System.AggregateException>按照任务并行库的约定，包装异常，此行为不同于 F # async 通常曲面异常的方式。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-231">Exceptions are wrapped in <xref:System.AggregateException> following the convention of the Task Parallel Library, and this behavior is different from how F# async generally surfaces exceptions.</span></span>

### <a name="asynccatch"></a><span data-ttu-id="e3f6b-232">Async Catch</span><span class="sxs-lookup"><span data-stu-id="e3f6b-232">Async.Catch</span></span>

<span data-ttu-id="e3f6b-233">创建一个执行给定的异步计算 `Async<'T>` ，并返回 `Async<Choice<'T, exn>>` 。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-233">Creates an asynchronous computation that executes a given `Async<'T>`, returning an `Async<Choice<'T, exn>>`.</span></span> <span data-ttu-id="e3f6b-234">如果给定的 `Async<'T>` 成功完成，则将 `Choice1Of2` 返回并返回结果值。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-234">If the given `Async<'T>` completes successfully, then a `Choice1Of2` is returned with the resultant value.</span></span> <span data-ttu-id="e3f6b-235">如果在异常完成之前引发异常，则返回， `Choice2of2` 并引发异常。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-235">If an exception is thrown before it completes, then a `Choice2of2` is returned with the raised exception.</span></span> <span data-ttu-id="e3f6b-236">如果它用于由多个计算组成的异步计算，并且其中一个计算引发异常，则会完全停止包含计算。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-236">If it is used on an asynchronous computation that is itself composed of many computations, and one of those computations throws an exception, the encompassing computation will be stopped entirely.</span></span>

<span data-ttu-id="e3f6b-237">签名：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-237">Signature:</span></span>

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

<span data-ttu-id="e3f6b-238">使用场合：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-238">When to use:</span></span>

- <span data-ttu-id="e3f6b-239">当你执行的异步工作可能会失败并出现异常，你希望在调用方中处理该异常。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-239">When you are performing asynchronous work that may fail with an exception and you want to handle that exception in the caller.</span></span>

<span data-ttu-id="e3f6b-240">需要注意的事项：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-240">What to watch out for:</span></span>

- <span data-ttu-id="e3f6b-241">使用组合的或序列化的异步计算时，如果其中一个 "内部" 计算引发异常，则会完全停止包含计算。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-241">When using combined or sequenced asynchronous computations, the encompassing computation will fully stop if one of its "internal" computations throws an exception.</span></span>

### <a name="asyncignore"></a><span data-ttu-id="e3f6b-242">Async。 Ignore</span><span class="sxs-lookup"><span data-stu-id="e3f6b-242">Async.Ignore</span></span>

<span data-ttu-id="e3f6b-243">创建一个异步计算，该异步计算将运行给定的计算并忽略其结果。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-243">Creates an asynchronous computation that runs the given computation and ignores its result.</span></span>

<span data-ttu-id="e3f6b-244">签名：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-244">Signature:</span></span>

```fsharp
computation: Async<'T> -> Async<unit>
```

<span data-ttu-id="e3f6b-245">使用场合：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-245">When to use:</span></span>

- <span data-ttu-id="e3f6b-246">如果具有不需要其结果的异步计算。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-246">When you have an asynchronous computation whose result is not needed.</span></span> <span data-ttu-id="e3f6b-247">这类似于 `ignore` 非异步代码的代码。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-247">This is analogous to the `ignore` code for non-asynchronous code.</span></span>

<span data-ttu-id="e3f6b-248">需要注意的事项：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-248">What to watch out for:</span></span>

- <span data-ttu-id="e3f6b-249">如果你必须使用 `Async.Ignore` ，因为你希望使用 `Async.Start` 或需要的另一个函数 `Async<unit>` ，请考虑是否放弃结果是否正常。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-249">If you must use `Async.Ignore` because you wish to use `Async.Start` or another function that requires `Async<unit>`, consider if discarding the result is okay.</span></span> <span data-ttu-id="e3f6b-250">避免仅在满足类型签名的情况下丢弃结果。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-250">Avoid discarding results just to fit a type signature.</span></span>

### <a name="asyncrunsynchronously"></a><span data-ttu-id="e3f6b-251">RunSynchronously</span><span class="sxs-lookup"><span data-stu-id="e3f6b-251">Async.RunSynchronously</span></span>

<span data-ttu-id="e3f6b-252">运行异步计算，并在调用线程上等待其结果。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-252">Runs an asynchronous computation and awaits its result on the calling thread.</span></span> <span data-ttu-id="e3f6b-253">此调用正在阻止。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-253">This call is blocking.</span></span>

<span data-ttu-id="e3f6b-254">签名：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-254">Signature:</span></span>

```fsharp
computation: Async<'T> * timeout: ?int * cancellationToken: ?CancellationToken -> 'T
```

<span data-ttu-id="e3f6b-255">何时使用:</span><span class="sxs-lookup"><span data-stu-id="e3f6b-255">When to use it:</span></span>

- <span data-ttu-id="e3f6b-256">如果需要，请在应用程序的入口点（可执行文件）中使用它一次。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-256">If you need it, use it only once in an application - at the entry point for an executable.</span></span>
- <span data-ttu-id="e3f6b-257">当你不关心性能并希望同时执行一组其他异步操作时。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-257">When you don't care about performance and want to execute a set of other asynchronous operations at once.</span></span>

<span data-ttu-id="e3f6b-258">需要注意的事项：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-258">What to watch out for:</span></span>

- <span data-ttu-id="e3f6b-259">调用会 `Async.RunSynchronously` 阻止调用线程，直到执行完成。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-259">Calling `Async.RunSynchronously` blocks the calling thread until the execution completes.</span></span>

### <a name="asyncstart"></a><span data-ttu-id="e3f6b-260">Async. Start</span><span class="sxs-lookup"><span data-stu-id="e3f6b-260">Async.Start</span></span>

<span data-ttu-id="e3f6b-261">在线程池中启动返回的异步计算 `unit` 。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-261">Starts an asynchronous computation in the thread pool that returns `unit`.</span></span> <span data-ttu-id="e3f6b-262">不会等待其结果。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-262">Doesn't wait for its result.</span></span> <span data-ttu-id="e3f6b-263">启动的嵌套计算 `Async.Start` 独立于调用它们的父计算。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-263">Nested computations started with `Async.Start` are started independently of the parent computation that called them.</span></span> <span data-ttu-id="e3f6b-264">它们的生存期未绑定到任何父计算。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-264">Their lifetime is not tied to any parent computation.</span></span> <span data-ttu-id="e3f6b-265">如果取消了父计算，则不会取消任何子计算。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-265">If the parent computation is canceled, no child computations are canceled.</span></span>

<span data-ttu-id="e3f6b-266">签名：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-266">Signature:</span></span>

```fsharp
computation: Async<unit> * cancellationToken: ?CancellationToken -> unit
```

<span data-ttu-id="e3f6b-267">仅在以下情况时使用：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-267">Use only when:</span></span>

- <span data-ttu-id="e3f6b-268">您有一个异步计算，该计算不产生结果和/或需要处理一个结果。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-268">You have an asynchronous computation that doesn't yield a result and/or require processing of one.</span></span>
- <span data-ttu-id="e3f6b-269">不需要知道异步计算何时完成。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-269">You don't need to know when an asynchronous computation completes.</span></span>
- <span data-ttu-id="e3f6b-270">您不关心异步计算在哪个线程上运行。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-270">You don't care which thread an asynchronous computation runs on.</span></span>
- <span data-ttu-id="e3f6b-271">您无需注意或报告由任务生成的异常。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-271">You don't have any need to be aware of or report exceptions resulting from the task.</span></span>

<span data-ttu-id="e3f6b-272">需要注意的事项：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-272">What to watch out for:</span></span>

- <span data-ttu-id="e3f6b-273">通过开始的计算引发的异常 `Async.Start` 不会传播到调用方。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-273">Exceptions raised by computations started with `Async.Start` aren't propagated to the caller.</span></span> <span data-ttu-id="e3f6b-274">调用堆栈将被完全展开。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-274">The call stack will be completely unwound.</span></span>
- <span data-ttu-id="e3f6b-275">任何工作 (例如从 `printfn` 开始时调用) `Async.Start` 不会导致在程序执行的主线程上发生效果。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-275">Any work (such as calling `printfn`) started with `Async.Start` won't cause the effect to happen on the main thread of a program's execution.</span></span>

## <a name="interoperate-with-net"></a><span data-ttu-id="e3f6b-276">与 .NET 交互</span><span class="sxs-lookup"><span data-stu-id="e3f6b-276">Interoperate with .NET</span></span>

<span data-ttu-id="e3f6b-277">你可能使用了使用 [async/await](../../../standard/async.md)-样式异步编程的 .net 库或 c # 基本代码。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-277">You may be working with a .NET library or C# codebase that uses [async/await](../../../standard/async.md)-style asynchronous programming.</span></span> <span data-ttu-id="e3f6b-278">由于 c # 和 .NET 库使用 <xref:System.Threading.Tasks.Task%601> 和 <xref:System.Threading.Tasks.Task> 类型作为其核心抽象，而不是 `Async<'T>` ，因此必须将这两种方法之间的边界跨越到异步。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-278">Because C# and the majority of .NET libraries use the <xref:System.Threading.Tasks.Task%601> and <xref:System.Threading.Tasks.Task> types as their core abstractions rather than `Async<'T>`, you must cross a boundary between these two approaches to asynchrony.</span></span>

### <a name="how-to-work-with-net-async-and-taskt"></a><span data-ttu-id="e3f6b-279">如何使用 .NET async 和 `Task<T>`</span><span class="sxs-lookup"><span data-stu-id="e3f6b-279">How to work with .NET async and `Task<T>`</span></span>

<span data-ttu-id="e3f6b-280">使用 (的 .NET 异步库和基本代码 <xref:System.Threading.Tasks.Task%601> ，即) 具有返回值的异步计算非常简单，并具有 F # 的内置支持。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-280">Working with .NET async libraries and codebases that use <xref:System.Threading.Tasks.Task%601> (that is, async computations that have return values) is straightforward and has built-in support with F#.</span></span>

<span data-ttu-id="e3f6b-281">您可以使用 `Async.AwaitTask` 函数来等待 .net 异步计算：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-281">You can use the `Async.AwaitTask` function to await a .NET asynchronous computation:</span></span>

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

<span data-ttu-id="e3f6b-282">可以使用函数将 `Async.StartAsTask` 异步计算传递到 .net 调用方：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-282">You can use the `Async.StartAsTask` function to pass an asynchronous computation to a .NET caller:</span></span>

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a><span data-ttu-id="e3f6b-283">如何使用 .NET async 和 `Task`</span><span class="sxs-lookup"><span data-stu-id="e3f6b-283">How to work with .NET async and `Task`</span></span>

<span data-ttu-id="e3f6b-284">若要处理使用 <xref:System.Threading.Tasks.Task> (的 api，而不将值返回) 的 .net async 计算，则可能需要添加一个将转换 `Async<'T>` 为的其他函数 <xref:System.Threading.Tasks.Task> ：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-284">To work with APIs that use <xref:System.Threading.Tasks.Task> (that is, .NET async computations that do not return a value), you may need to add an additional function that will convert an `Async<'T>` to a <xref:System.Threading.Tasks.Task>:</span></span>

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

<span data-ttu-id="e3f6b-285">已存在 `Async.AwaitTask` 接受 <xref:System.Threading.Tasks.Task> 作为输入的。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-285">There is already an `Async.AwaitTask` that accepts a <xref:System.Threading.Tasks.Task> as input.</span></span> <span data-ttu-id="e3f6b-286">使用此和以前定义的 `startTaskFromAsyncUnit` 函数，可以 <xref:System.Threading.Tasks.Task> 从 F # async 计算启动和等待类型。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-286">With this and the previously defined `startTaskFromAsyncUnit` function, you can start and await <xref:System.Threading.Tasks.Task> types from an F# async computation.</span></span>

## <a name="relationship-to-multi-threading"></a><span data-ttu-id="e3f6b-287">与多线程的关系</span><span class="sxs-lookup"><span data-stu-id="e3f6b-287">Relationship to multi-threading</span></span>

<span data-ttu-id="e3f6b-288">尽管本文介绍了线程处理，但要记住以下两个重要事项：</span><span class="sxs-lookup"><span data-stu-id="e3f6b-288">Although threading is mentioned throughout this article, there are two important things to remember:</span></span>

1. <span data-ttu-id="e3f6b-289">除非在当前线程上显式启动，否则异步计算与线程之间没有关联。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-289">There is no affinity between an asynchronous computation and a thread, unless explicitly started on the current thread.</span></span>
1. <span data-ttu-id="e3f6b-290">F # 中的异步编程不是用于多线程的抽象。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-290">Asynchronous programming in F# is not an abstraction for multi-threading.</span></span>

<span data-ttu-id="e3f6b-291">例如，根据工作的性质，计算实际上可以在其调用方的线程上运行。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-291">For example, a computation may actually run on its caller's thread, depending on the nature of the work.</span></span> <span data-ttu-id="e3f6b-292">计算还可以在线程之间 "跳转"，从而在 "等待" (（例如，当网络调用传输) 时，将其用于在 "等待" 时间间隔内完成有用的工作。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-292">A computation could also "jump" between threads, borrowing them for a small amount of time to do useful work in between periods of "waiting" (such as when a network call is in transit).</span></span>

<span data-ttu-id="e3f6b-293">尽管 F # 提供了一些功能来在当前线程上启动异步计算 (或明确地不是在当前线程) 上，异步通常不与特定的线程策略相关联。</span><span class="sxs-lookup"><span data-stu-id="e3f6b-293">Although F# provides some abilities to start an asynchronous computation on the current thread (or explicitly not on the current thread), asynchrony generally is not associated with a particular threading strategy.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3f6b-294">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e3f6b-294">See also</span></span>

- [<span data-ttu-id="e3f6b-295">F # 异步编程模型</span><span class="sxs-lookup"><span data-stu-id="e3f6b-295">The F# Asynchronous Programming Model</span></span>](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [<span data-ttu-id="e3f6b-296">Jet .com 的 F # Async Guide</span><span class="sxs-lookup"><span data-stu-id="e3f6b-296">Jet.com's F# Async Guide</span></span>](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [<span data-ttu-id="e3f6b-297">F # 用于趣味和利润的异步编程指南</span><span class="sxs-lookup"><span data-stu-id="e3f6b-297">F# for fun and profit's Asynchronous Programming guide</span></span>](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [<span data-ttu-id="e3f6b-298">C # 和 F # 中的异步： C 中的异步陷阱#</span><span class="sxs-lookup"><span data-stu-id="e3f6b-298">Async in C# and F#: Asynchronous gotchas in C#</span></span>](http://tomasp.net/blog/csharp-async-gotchas.aspx/)

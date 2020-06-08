---
title: C# 中的异步编程
description: 对使用 async、await、Task 和 Task<T> 的异步编程的 C# 语言支持的概述
ms.date: 06/04/2020
ms.openlocfilehash: fbbd08f8c0e650c366ca1d283825e629fcb952d7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446419"
---
# <a name="asynchronous-programming-with-async-and-await"></a><span data-ttu-id="87ca6-103">使用 Async 和 Await 的异步编程</span><span class="sxs-lookup"><span data-stu-id="87ca6-103">Asynchronous programming with async and await</span></span>

<span data-ttu-id="87ca6-104">[基于任务的异步编程模型 (TAP)](task-asynchronous-programming-model.md) 提供了异步代码的抽象化。</span><span class="sxs-lookup"><span data-stu-id="87ca6-104">The [Task asynchronous programming model (TAP)](task-asynchronous-programming-model.md) provides an abstraction over asynchronous code.</span></span> <span data-ttu-id="87ca6-105">你只需像往常一样将代码编写为一连串语句即可。</span><span class="sxs-lookup"><span data-stu-id="87ca6-105">You write code as a sequence of statements, just like always.</span></span> <span data-ttu-id="87ca6-106">就如每条语句在下一句开始之前完成一样，你可以流畅地阅读代码。</span><span class="sxs-lookup"><span data-stu-id="87ca6-106">You can read that code as though each statement completes before the next begins.</span></span> <span data-ttu-id="87ca6-107">编译器将执行若干转换，因为其中一些语句可能会开始运行并返回表示正在运行中的 <xref:System.Threading.Tasks.Task>。</span><span class="sxs-lookup"><span data-stu-id="87ca6-107">The compiler performs a number of transformations because some of those statements may start work and return a <xref:System.Threading.Tasks.Task> that represents the ongoing work.</span></span>

<span data-ttu-id="87ca6-108">这就是此语法的目标：支持读起来像一连串语句的代码，但会根据外部资源分配和任务完成时间以更复杂的顺序执行。</span><span class="sxs-lookup"><span data-stu-id="87ca6-108">That's the goal of this syntax: enable code that reads like a sequence of statements, but executes in a much more complicated order based on external resource allocation and when tasks complete.</span></span> <span data-ttu-id="87ca6-109">这与人们为包含异步任务的流程给予指令的方式类似。</span><span class="sxs-lookup"><span data-stu-id="87ca6-109">It's analogous to how people give instructions for processes that include asynchronous tasks.</span></span> <span data-ttu-id="87ca6-110">在本文中，你将通过做早餐的指令示例来查看如何使用 `async` 和 `await` 关键字更轻松地推断包含一系列异步指令的代码。</span><span class="sxs-lookup"><span data-stu-id="87ca6-110">Throughout this article, you'll use an example of instructions for making a breakfast to see how the `async` and `await` keywords make it easier to reason about code, that includes a series of asynchronous instructions.</span></span> <span data-ttu-id="87ca6-111">你可能会写出与以下列表类似的指令来解释如何做早餐：</span><span class="sxs-lookup"><span data-stu-id="87ca6-111">You'd write the instructions something like the following list to explain how to make a breakfast:</span></span>

1. <span data-ttu-id="87ca6-112">倒一杯咖啡。</span><span class="sxs-lookup"><span data-stu-id="87ca6-112">Pour a cup of coffee.</span></span>
1. <span data-ttu-id="87ca6-113">加热平底锅，然后煎两个鸡蛋。</span><span class="sxs-lookup"><span data-stu-id="87ca6-113">Heat up a pan, then fry two eggs.</span></span>
1. <span data-ttu-id="87ca6-114">煎三片培根。</span><span class="sxs-lookup"><span data-stu-id="87ca6-114">Fry three slices of bacon.</span></span>
1. <span data-ttu-id="87ca6-115">烤两片面包。</span><span class="sxs-lookup"><span data-stu-id="87ca6-115">Toast two pieces of bread.</span></span>
1. <span data-ttu-id="87ca6-116">在烤面包上加黄油和果酱。</span><span class="sxs-lookup"><span data-stu-id="87ca6-116">Add butter and jam to the toast.</span></span>
1. <span data-ttu-id="87ca6-117">倒一杯橙汁。</span><span class="sxs-lookup"><span data-stu-id="87ca6-117">Pour a glass of orange juice.</span></span>

<span data-ttu-id="87ca6-118">如果你有烹饪经验，便可通过异步方式执行这些指令。</span><span class="sxs-lookup"><span data-stu-id="87ca6-118">If you have experience with cooking, you'd execute those instructions **asynchronously**.</span></span> <span data-ttu-id="87ca6-119">你会先开始加热平底锅以备煎蛋，接着再从培根着手。</span><span class="sxs-lookup"><span data-stu-id="87ca6-119">You'd start warming the pan for eggs, then start the bacon.</span></span> <span data-ttu-id="87ca6-120">你可将面包放进烤面包机，然后再煎鸡蛋。</span><span class="sxs-lookup"><span data-stu-id="87ca6-120">You'd put the bread in the toaster, then start the eggs.</span></span> <span data-ttu-id="87ca6-121">在此过程的每一步，你都可以先开始一项任务，然后将注意力转移到准备进行的其他任务上。</span><span class="sxs-lookup"><span data-stu-id="87ca6-121">At each step of the process, you'd start a task, then turn your attention to tasks that are ready for your attention.</span></span>

<span data-ttu-id="87ca6-122">做早餐是非并行异步工作的一个好示例。</span><span class="sxs-lookup"><span data-stu-id="87ca6-122">Cooking breakfast is a good example of asynchronous work that isn't parallel.</span></span> <span data-ttu-id="87ca6-123">单人（或单线程）即可处理所有这些任务。</span><span class="sxs-lookup"><span data-stu-id="87ca6-123">One person (or thread) can handle all these tasks.</span></span> <span data-ttu-id="87ca6-124">继续讲解早餐的类比，一个人可以以异步方式做早餐，即在第一个任务完成之前开始进行下一个任务。</span><span class="sxs-lookup"><span data-stu-id="87ca6-124">Continuing the breakfast analogy, one person can make breakfast asynchronously by starting the next task before the first completes.</span></span> <span data-ttu-id="87ca6-125">不管是否有人在看着，做早餐的过程都在进行。</span><span class="sxs-lookup"><span data-stu-id="87ca6-125">The cooking progresses whether or not someone is watching it.</span></span> <span data-ttu-id="87ca6-126">在开始加热平底锅准备煎蛋的同时就可以开始煎了培根。</span><span class="sxs-lookup"><span data-stu-id="87ca6-126">As soon as you start warming the pan for the eggs, you can begin frying the bacon.</span></span> <span data-ttu-id="87ca6-127">在开始煎培根后，你可以将面包放进烤面包机。</span><span class="sxs-lookup"><span data-stu-id="87ca6-127">Once the bacon starts, you can put the bread into the toaster.</span></span>

<span data-ttu-id="87ca6-128">对于并行算法而言，你则需要多名厨师（或线程）。</span><span class="sxs-lookup"><span data-stu-id="87ca6-128">For a parallel algorithm, you'd need multiple cooks (or threads).</span></span> <span data-ttu-id="87ca6-129">一名厨师煎鸡蛋，一名厨师煎培根，依次类推。</span><span class="sxs-lookup"><span data-stu-id="87ca6-129">One would make the eggs, one the bacon, and so on.</span></span> <span data-ttu-id="87ca6-130">每名厨师将仅专注于一项任务。</span><span class="sxs-lookup"><span data-stu-id="87ca6-130">Each one would be focused on just that one task.</span></span> <span data-ttu-id="87ca6-131">每名厨师（或线程）都在同步等待需要翻动培根或面包弹出时都将受到阻。</span><span class="sxs-lookup"><span data-stu-id="87ca6-131">Each cook (or thread) would be blocked synchronously waiting for bacon to be ready to flip, or the toast to pop.</span></span>

<span data-ttu-id="87ca6-132">现在，考虑一下编写为 C# 语句的相同指令：</span><span class="sxs-lookup"><span data-stu-id="87ca6-132">Now, consider those same instructions written as C# statements:</span></span>

:::code language="csharp" source="snippets/index/AsyncBreakfast-starter/Program.cs" highlight="8-27":::

:::image type="content" source="media/synchronous-breakfast.png" alt-text="同步早餐":::

<span data-ttu-id="87ca6-134">同步准备的早餐大约花费了 30 分钟，因为总耗时是每个任务耗时的总和。</span><span class="sxs-lookup"><span data-stu-id="87ca6-134">The synchronously prepared breakfast, took roughly 30 minutes because the total is the sum of each individual task.</span></span>

> [!NOTE]
> <span data-ttu-id="87ca6-135">`Coffee`、`Egg`、`Bacon`、`Toast` 和 `Juice` 类为空。</span><span class="sxs-lookup"><span data-stu-id="87ca6-135">The `Coffee`, `Egg`, `Bacon`, `Toast`, and `Juice` classes are empty.</span></span> <span data-ttu-id="87ca6-136">它们是仅用于演示的简单标记类，不含任何属性，且不用于其他用途。</span><span class="sxs-lookup"><span data-stu-id="87ca6-136">They are simply marker classes for the purpose of demonstration, contain no properties, and serve no other purpose.</span></span>

<span data-ttu-id="87ca6-137">计算机不会按人类的方式来解释这些指令。</span><span class="sxs-lookup"><span data-stu-id="87ca6-137">Computers don't interpret those instructions the same way people do.</span></span> <span data-ttu-id="87ca6-138">计算机将阻塞每条语句，直到工作完成，然后再继续运行下一条语句。</span><span class="sxs-lookup"><span data-stu-id="87ca6-138">The computer will block on each statement until the work is complete before moving on to the next statement.</span></span> <span data-ttu-id="87ca6-139">这将创造出令人不满意的早餐。</span><span class="sxs-lookup"><span data-stu-id="87ca6-139">That creates an unsatisfying breakfast.</span></span> <span data-ttu-id="87ca6-140">后续任务直到早前任务完成后才会启动。</span><span class="sxs-lookup"><span data-stu-id="87ca6-140">The later tasks wouldn't be started until the earlier tasks had completed.</span></span> <span data-ttu-id="87ca6-141">这样做早餐花费的时间要长得多，有些食物在上桌之前就已经凉了。</span><span class="sxs-lookup"><span data-stu-id="87ca6-141">It would take much longer to create the breakfast, and some items would have gotten cold before being served.</span></span>

<span data-ttu-id="87ca6-142">如果你希望计算机异步执行上述指令，则必须编写异步代码。</span><span class="sxs-lookup"><span data-stu-id="87ca6-142">If you want the computer to execute the above instructions asynchronously, you must write asynchronous code.</span></span>

<span data-ttu-id="87ca6-143">这些问题对即将编写的程序而言至关重要。</span><span class="sxs-lookup"><span data-stu-id="87ca6-143">These concerns are important for the programs you write today.</span></span> <span data-ttu-id="87ca6-144">编写客户端程序时，你希望 UI 能够响应用户输入。</span><span class="sxs-lookup"><span data-stu-id="87ca6-144">When you write client programs, you want the UI to be responsive to user input.</span></span> <span data-ttu-id="87ca6-145">从 Web 下载数据时，你的应用程序不应让手机出现卡顿。</span><span class="sxs-lookup"><span data-stu-id="87ca6-145">Your application shouldn't make a phone appear frozen while it's downloading data from the web.</span></span> <span data-ttu-id="87ca6-146">编写服务器程序时，你不希望线程受到阻塞。</span><span class="sxs-lookup"><span data-stu-id="87ca6-146">When you write server programs, you don't want threads blocked.</span></span> <span data-ttu-id="87ca6-147">这些线程可以用于处理其他请求。</span><span class="sxs-lookup"><span data-stu-id="87ca6-147">Those threads could be serving other requests.</span></span> <span data-ttu-id="87ca6-148">存在异步替代项的情况下使用同步代码会增加你进行扩展的成本。</span><span class="sxs-lookup"><span data-stu-id="87ca6-148">Using synchronous code when asynchronous alternatives exist hurts your ability to scale out less expensively.</span></span> <span data-ttu-id="87ca6-149">你需要为这些受阻线程付费。</span><span class="sxs-lookup"><span data-stu-id="87ca6-149">You pay for those blocked threads.</span></span>

<span data-ttu-id="87ca6-150">成功的现代应用程序需要异步代码。</span><span class="sxs-lookup"><span data-stu-id="87ca6-150">Successful modern applications require asynchronous code.</span></span> <span data-ttu-id="87ca6-151">在没有语言支持的情况下，编写异步代码需要回调、完成事件，或其他掩盖代码原始意图的方法。</span><span class="sxs-lookup"><span data-stu-id="87ca6-151">Without language support, writing asynchronous code required callbacks, completion events, or other means that obscured the original intent of the code.</span></span> <span data-ttu-id="87ca6-152">同步代码的优点在于易于理解。</span><span class="sxs-lookup"><span data-stu-id="87ca6-152">The advantage of the synchronous code is that it's easy to understand.</span></span> <span data-ttu-id="87ca6-153">分布操作使其易于查看和理解。</span><span class="sxs-lookup"><span data-stu-id="87ca6-153">The step-by-step actions make it easy to scan and understand.</span></span> <span data-ttu-id="87ca6-154">传统的异步模型迫使你侧重于代码的异步性质，而不是代码的基本操作。</span><span class="sxs-lookup"><span data-stu-id="87ca6-154">Traditional asynchronous models forced you to focus on the asynchronous nature of the code, not on the fundamental actions of the code.</span></span>

## <a name="dont-block-await-instead"></a><span data-ttu-id="87ca6-155">不要阻塞，而要 await</span><span class="sxs-lookup"><span data-stu-id="87ca6-155">Don't block, await instead</span></span>

<span data-ttu-id="87ca6-156">上述代码演示了不正确的实践：构造同步代码来执行异步操作。</span><span class="sxs-lookup"><span data-stu-id="87ca6-156">The preceding code demonstrates a bad practice: constructing synchronous code to perform asynchronous operations.</span></span> <span data-ttu-id="87ca6-157">顾名思义，此代码将阻止执行这段代码的线程执行任何其他操作。</span><span class="sxs-lookup"><span data-stu-id="87ca6-157">As written, this code blocks the thread executing it from doing any other work.</span></span> <span data-ttu-id="87ca6-158">在任何任务进行过程中，此代码也不会被中断。</span><span class="sxs-lookup"><span data-stu-id="87ca6-158">It won't be interrupted while any of the tasks are in progress.</span></span> <span data-ttu-id="87ca6-159">就如同你将面包放进烤面包机后盯着此烤面包机一样。</span><span class="sxs-lookup"><span data-stu-id="87ca6-159">It would be as though you stared at the toaster after putting the bread in.</span></span> <span data-ttu-id="87ca6-160">你会无视任何跟你说话的人，直到面包弹出。</span><span class="sxs-lookup"><span data-stu-id="87ca6-160">You'd ignore anyone talking to you until the toast popped.</span></span>

<span data-ttu-id="87ca6-161">我们首先更新此代码，使线程在任务运行时不会阻塞。</span><span class="sxs-lookup"><span data-stu-id="87ca6-161">Let's start by updating this code so that the thread doesn't block while tasks are running.</span></span> <span data-ttu-id="87ca6-162">`await` 关键字提供了一种非阻塞方式来启动任务，然后在此任务完成时继续执行。</span><span class="sxs-lookup"><span data-stu-id="87ca6-162">The `await` keyword provides a non-blocking way to start a task, then continue execution when that task completes.</span></span> <span data-ttu-id="87ca6-163">“做早餐”代码的简单异步版本类似于以下片段：</span><span class="sxs-lookup"><span data-stu-id="87ca6-163">A simple asynchronous version of the make a breakfast code would look like the following snippet:</span></span>

:::code language="csharp" source="snippets/index/AsyncBreakfast-V2/Program.cs" id="SnippetMain":::

> [!IMPORTANT]
> <span data-ttu-id="87ca6-164">总实耗时间和最初同步版本大致相同。</span><span class="sxs-lookup"><span data-stu-id="87ca6-164">The total elapsed time is roughly the same as the initial synchonous version.</span></span> <span data-ttu-id="87ca6-165">此代码尚未利用某些关键功能异步编程。</span><span class="sxs-lookup"><span data-stu-id="87ca6-165">The code has yet to take advantage of some of the key features asynchronous programming.</span></span>

> [!TIP]
> <span data-ttu-id="87ca6-166">`FryEggsAsync`、`FryBaconAsync` 和 `ToastBreadAsync` 的方法主体都已更新，现会分别返回 `Task<Egg>`、`Task<Bacon>` 和 `Task<Toast>`。</span><span class="sxs-lookup"><span data-stu-id="87ca6-166">The method bodies of the `FryEggsAsync`, `FryBaconAsync`, and `ToastBreadAsync` have all been updated to return `Task<Egg>`, `Task<Bacon>`, and `Task<Toast>` respectively.</span></span> <span data-ttu-id="87ca6-167">这些方法的名称与其原始版本不同，将包含“Async”后缀。</span><span class="sxs-lookup"><span data-stu-id="87ca6-167">The methods are renamed from their original version to include the "Async" suffix.</span></span> <span data-ttu-id="87ca6-168">它们的实现在本文的稍后部分显示为[最终版本](#final-version)的一部分。</span><span class="sxs-lookup"><span data-stu-id="87ca6-168">Their implementations are shown as part of the [final version](#final-version) later in this article.</span></span>

<span data-ttu-id="87ca6-169">在煎鸡蛋或培根时，此代码不会阻塞。</span><span class="sxs-lookup"><span data-stu-id="87ca6-169">This code doesn't block while the eggs or the bacon are cooking.</span></span> <span data-ttu-id="87ca6-170">不过，此代码也不会启动任何其他任务。</span><span class="sxs-lookup"><span data-stu-id="87ca6-170">This code won't start any other tasks though.</span></span> <span data-ttu-id="87ca6-171">你还是会将面包放进烤面包机里，然后盯着烤面包机直到面包弹出。</span><span class="sxs-lookup"><span data-stu-id="87ca6-171">You'd still put the toast in the toaster and stare at it until it pops.</span></span> <span data-ttu-id="87ca6-172">但至少，你会回应任何想引起你注意的人。</span><span class="sxs-lookup"><span data-stu-id="87ca6-172">But at least, you'd respond to anyone that wanted your attention.</span></span> <span data-ttu-id="87ca6-173">在接受了多份订单的一家餐馆里，厨师可能会在做第一份早餐的同时开始制作另一份早餐。</span><span class="sxs-lookup"><span data-stu-id="87ca6-173">In a restaurant where multiple orders are placed, the cook could start another breakfast while the first is cooking.</span></span>

<span data-ttu-id="87ca6-174">现在，在等待任何尚未完成的已启动任务时，处理早餐的线程将不会被阻塞。</span><span class="sxs-lookup"><span data-stu-id="87ca6-174">Now, the thread working on the breakfast isn't blocked while awaiting any started task that hasn't yet finished.</span></span> <span data-ttu-id="87ca6-175">对于某些应用程序而言，此更改是必需的。</span><span class="sxs-lookup"><span data-stu-id="87ca6-175">For some applications, this change is all that's needed.</span></span> <span data-ttu-id="87ca6-176">仅凭借此更改，GUI 应用程序仍然会响应用户。</span><span class="sxs-lookup"><span data-stu-id="87ca6-176">A GUI application still responds to the user with just this change.</span></span> <span data-ttu-id="87ca6-177">然而，对于此方案而言，你需要更多的内容。</span><span class="sxs-lookup"><span data-stu-id="87ca6-177">However, for this scenario, you want more.</span></span> <span data-ttu-id="87ca6-178">你不希望每个组件任务都按顺序执行。</span><span class="sxs-lookup"><span data-stu-id="87ca6-178">You don't want each of the component tasks to be executed sequentially.</span></span> <span data-ttu-id="87ca6-179">最好首先启动每个组件任务，然后再等待之前任务的完成。</span><span class="sxs-lookup"><span data-stu-id="87ca6-179">It's better to start each of the component tasks before awaiting the previous task's completion.</span></span>

## <a name="start-tasks-concurrently"></a><span data-ttu-id="87ca6-180">同时启动任务</span><span class="sxs-lookup"><span data-stu-id="87ca6-180">Start tasks concurrently</span></span>

<span data-ttu-id="87ca6-181">在许多方案中，你希望立即启动若干独立的任务。</span><span class="sxs-lookup"><span data-stu-id="87ca6-181">In many scenarios, you want to start several independent tasks immediately.</span></span> <span data-ttu-id="87ca6-182">然后，在每个任务完成时，你可以继续进行已准备的其他工作。</span><span class="sxs-lookup"><span data-stu-id="87ca6-182">Then, as each task finishes, you can continue other work that's ready.</span></span> <span data-ttu-id="87ca6-183">在早餐类比中，这就是更快完成做早餐的方法。</span><span class="sxs-lookup"><span data-stu-id="87ca6-183">In the breakfast analogy, that's how you get breakfast done more quickly.</span></span> <span data-ttu-id="87ca6-184">你也几乎将在同一时间完成所有工作。</span><span class="sxs-lookup"><span data-stu-id="87ca6-184">You also get everything done close to the same time.</span></span> <span data-ttu-id="87ca6-185">你将吃到一顿热气腾腾的早餐。</span><span class="sxs-lookup"><span data-stu-id="87ca6-185">You'll get a hot breakfast.</span></span>

<span data-ttu-id="87ca6-186"><xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 和相关类型是可以用于推断正在进行中的任务的类。</span><span class="sxs-lookup"><span data-stu-id="87ca6-186">The <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> and related types are classes you can use to reason about tasks that are in progress.</span></span> <span data-ttu-id="87ca6-187">这使你能够编写更类似于实际做早餐方式的代码。</span><span class="sxs-lookup"><span data-stu-id="87ca6-187">That enables you to write code that more closely resembles the way you'd actually create breakfast.</span></span> <span data-ttu-id="87ca6-188">你可以同时开始煎鸡蛋、培根和烤面包。</span><span class="sxs-lookup"><span data-stu-id="87ca6-188">You'd start cooking the eggs, bacon, and toast at the same time.</span></span> <span data-ttu-id="87ca6-189">由于每个任务都需要操作，所以你会将注意力转移到那个任务上，进行下一个操作，然后等待其他需要你注意的事情。</span><span class="sxs-lookup"><span data-stu-id="87ca6-189">As each requires action, you'd turn your attention to that task, take care of the next action, then await for something else that requires your attention.</span></span>

<span data-ttu-id="87ca6-190">启动一项任务并等待表示运行的 <xref:System.Threading.Tasks.Task> 对象。</span><span class="sxs-lookup"><span data-stu-id="87ca6-190">You start a task and hold on to the <xref:System.Threading.Tasks.Task> object that represents the work.</span></span> <span data-ttu-id="87ca6-191">你将首先 `await` 每项任务，然后再处理它的结果。</span><span class="sxs-lookup"><span data-stu-id="87ca6-191">You'll `await` each task before working with its result.</span></span>

<span data-ttu-id="87ca6-192">让我们对早餐代码进行这些更改。</span><span class="sxs-lookup"><span data-stu-id="87ca6-192">Let's make these changes to the breakfast code.</span></span> <span data-ttu-id="87ca6-193">第一步是存储任务以便在这些任务启动时进行操作，而不是等待：</span><span class="sxs-lookup"><span data-stu-id="87ca6-193">The first step is to store the tasks for operations when they start, rather than awaiting them:</span></span>

```csharp
Coffee cup = PourCoffee();
Console.WriteLine("coffee is ready");

Task<Egg> eggsTask = FryEggsAsync(2);
Egg eggs = await eggsTask;
Console.WriteLine("eggs are ready");

Task<Bacon> baconTask = FryBaconAsync(3);
Bacon bacon = await baconTask;
Console.WriteLine("bacon is ready");

Task<Toast> toastTask = ToastBreadAsync(2);
Toast toast = await toastTask;
ApplyButter(toast);
ApplyJam(toast);
Console.WriteLine("toast is ready");

Juice oj = PourOJ();
Console.WriteLine("oj is ready");
Console.WriteLine("Breakfast is ready!");
```

<span data-ttu-id="87ca6-194">接下来，可以在提供早餐之前将用于处理培根和鸡蛋的 `await` 语句移动到此方法的末尾：</span><span class="sxs-lookup"><span data-stu-id="87ca6-194">Next, you can move the `await` statements for the bacon and eggs to the end of the method, before serving breakfast:</span></span>

```csharp
Coffee cup = PourCoffee();
Console.WriteLine("coffee is ready");

Task<Egg> eggsTask = FryEggsAsync(2);
Task<Bacon> baconTask = FryBaconAsync(3);
Task<Toast> toastTask = ToastBreadAsync(2);

Toast toast = await toastTask;
ApplyButter(toast);
ApplyJam(toast);
Console.WriteLine("toast is ready");
Juice oj = PourOJ();
Console.WriteLine("oj is ready");

Egg eggs = await eggsTask;
Console.WriteLine("eggs are ready");
Bacon bacon = await baconTask;
Console.WriteLine("bacon is ready");

Console.WriteLine("Breakfast is ready!");
```

:::image type="content" source="media/asynchronous-breakfast.png" alt-text="异步早餐":::

<span data-ttu-id="87ca6-196">异步准备的早餐大约花费了 20 分钟，这是因为一些任务可以并发运行。</span><span class="sxs-lookup"><span data-stu-id="87ca6-196">The asynchronously prepared breakfast took roughly 20 minutes, this is because some tasks were able to run concurrently.</span></span>

<span data-ttu-id="87ca6-197">上述代码效果更好。</span><span class="sxs-lookup"><span data-stu-id="87ca6-197">The preceding code works better.</span></span> <span data-ttu-id="87ca6-198">你可以一次启动所有的异步任务。</span><span class="sxs-lookup"><span data-stu-id="87ca6-198">You start all the asynchronous tasks at once.</span></span> <span data-ttu-id="87ca6-199">你仅在需要结果时才会等待每项任务。</span><span class="sxs-lookup"><span data-stu-id="87ca6-199">You await each task only when you need the results.</span></span> <span data-ttu-id="87ca6-200">上述代码可能类似于 Web 应用程序中请求各种微服务，然后将结果合并到单个页面中的代码。</span><span class="sxs-lookup"><span data-stu-id="87ca6-200">The preceding code may be similar to code in a web application that makes requests of different microservices, then combines the results into a single page.</span></span> <span data-ttu-id="87ca6-201">你将立即发出所有请求，然后 `await` 所有这些任务并组成 Web 页面。</span><span class="sxs-lookup"><span data-stu-id="87ca6-201">You'll make all the requests immediately, then `await` all those tasks and compose the web page.</span></span>

## <a name="composition-with-tasks"></a><span data-ttu-id="87ca6-202">与任务组合</span><span class="sxs-lookup"><span data-stu-id="87ca6-202">Composition with tasks</span></span>

 <span data-ttu-id="87ca6-203">除了吐司外，你准备好了做早餐的所有材料。</span><span class="sxs-lookup"><span data-stu-id="87ca6-203">You have everything ready for breakfast at the same time except the toast.</span></span> <span data-ttu-id="87ca6-204">吐司制作由异步操作（烤面包）和同步操作（添加黄油和果酱）组成。</span><span class="sxs-lookup"><span data-stu-id="87ca6-204">Making the toast is the composition of an asynchronous operation (toasting the bread), and synchronous operations (adding the butter and the jam).</span></span> <span data-ttu-id="87ca6-205">更新此代码说明了一个重要的概念：</span><span class="sxs-lookup"><span data-stu-id="87ca6-205">Updating this code illustrates an important concept:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="87ca6-206">异步操作后跟同步操作的这种组合是一个异步操作。</span><span class="sxs-lookup"><span data-stu-id="87ca6-206">The composition of an asynchronous operation followed by synchronous work is an asynchronous operation.</span></span> <span data-ttu-id="87ca6-207">换言之，如果操作的任何部分是异步的，整个操作就是异步的。</span><span class="sxs-lookup"><span data-stu-id="87ca6-207">Stated another way, if any portion of an operation is asynchronous, the entire operation is asynchronous.</span></span>

<span data-ttu-id="87ca6-208">上述代码展示了可以使用 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 对象来保存运行中的任务。</span><span class="sxs-lookup"><span data-stu-id="87ca6-208">The preceding code showed you that you can use <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> objects to hold running tasks.</span></span> <span data-ttu-id="87ca6-209">你首先需要 `await` 每项任务，然后再使用它的结果。</span><span class="sxs-lookup"><span data-stu-id="87ca6-209">You `await` each task before using its result.</span></span> <span data-ttu-id="87ca6-210">下一步是创建表示其他工作组合的方式。</span><span class="sxs-lookup"><span data-stu-id="87ca6-210">The next step is to create methods that represent the combination of other work.</span></span> <span data-ttu-id="87ca6-211">在提供早餐之前，你希望等待表示先烤面包再添加黄油和果酱的任务完成。</span><span class="sxs-lookup"><span data-stu-id="87ca6-211">Before serving breakfast, you want to await the task that represents toasting the bread before adding butter and jam.</span></span> <span data-ttu-id="87ca6-212">你可以使用以下代码表示此工作：</span><span class="sxs-lookup"><span data-stu-id="87ca6-212">You can represent that work with the following code:</span></span>

:::code language="csharp" source="snippets/index/AsyncBreakfast-V3/Program.cs" id="SnippetComposeToastTask":::

<span data-ttu-id="87ca6-213">上述方式的签名中具有 `async` 修饰符。</span><span class="sxs-lookup"><span data-stu-id="87ca6-213">The preceding method has the `async` modifier in its signature.</span></span> <span data-ttu-id="87ca6-214">它会向编译器发出信号，说明此方法包含 `await` 语句；也包含异步操作。</span><span class="sxs-lookup"><span data-stu-id="87ca6-214">That signals to the compiler that this method contains an `await` statement; it contains asynchronous operations.</span></span> <span data-ttu-id="87ca6-215">此方法表示先烤面包，然后再添加黄油和果酱的任务。</span><span class="sxs-lookup"><span data-stu-id="87ca6-215">This method represents the task that toasts the bread, then adds butter and jam.</span></span> <span data-ttu-id="87ca6-216">此方法返回表示这三个操作的组合的 <xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="87ca6-216">This method returns a <xref:System.Threading.Tasks.Task%601> that represents the composition of those three operations.</span></span> <span data-ttu-id="87ca6-217">主要代码块现在变成了：</span><span class="sxs-lookup"><span data-stu-id="87ca6-217">The main block of code now becomes:</span></span>

:::code language="csharp" source="snippets/index/AsyncBreakfast-V3/Program.cs" id="SnippetMain":::

<span data-ttu-id="87ca6-218">上述更改说明了使用异步代码的一项重要技术。</span><span class="sxs-lookup"><span data-stu-id="87ca6-218">The previous change illustrated an important technique for working with asynchronous code.</span></span> <span data-ttu-id="87ca6-219">你可以通过将操作分离到一个返回任务的新方法中来组合任务。</span><span class="sxs-lookup"><span data-stu-id="87ca6-219">You compose tasks by separating the operations into a new method that returns a task.</span></span> <span data-ttu-id="87ca6-220">可以选择等待此任务的时间。</span><span class="sxs-lookup"><span data-stu-id="87ca6-220">You can choose when to await that task.</span></span> <span data-ttu-id="87ca6-221">可以同时启动其他任务。</span><span class="sxs-lookup"><span data-stu-id="87ca6-221">You can start other tasks concurrently.</span></span>

## <a name="await-tasks-efficiently"></a><span data-ttu-id="87ca6-222">高效地等待任务</span><span class="sxs-lookup"><span data-stu-id="87ca6-222">Await tasks efficiently</span></span>

<span data-ttu-id="87ca6-223">可以通过使用 `Task` 类的方法改进上述代码末尾的一系列 `await` 语句。</span><span class="sxs-lookup"><span data-stu-id="87ca6-223">The series of `await` statements at the end of the preceding code can be improved by using methods of the `Task` class.</span></span> <span data-ttu-id="87ca6-224">其中一个 API 是 <xref:System.Threading.Tasks.Task.WhenAll%2A>，它将返回一个其参数列表中的所有任务都已完成时才完成的 <xref:System.Threading.Tasks.Task>，如以下代码中所示：</span><span class="sxs-lookup"><span data-stu-id="87ca6-224">One of those APIs is <xref:System.Threading.Tasks.Task.WhenAll%2A>, which returns a <xref:System.Threading.Tasks.Task> that completes when all the tasks in its argument list have completed, as shown in the following code:</span></span>

```csharp
await Task.WhenAll(eggsTask, baconTask, toastTask);
Console.WriteLine("eggs are ready");
Console.WriteLine("bacon is ready");
Console.WriteLine("toast is ready");
Console.WriteLine("Breakfast is ready!");
```

<span data-ttu-id="87ca6-225">另一种选择是使用 <xref:System.Threading.Tasks.Task.WhenAny%2A>，它将返回一个当其参数完成时才完成的 `Task<Task>`。</span><span class="sxs-lookup"><span data-stu-id="87ca6-225">Another option is to use <xref:System.Threading.Tasks.Task.WhenAny%2A>, which returns a `Task<Task>` that completes when any of its arguments completes.</span></span> <span data-ttu-id="87ca6-226">你可以等待返回的任务，了解它已经完成了。</span><span class="sxs-lookup"><span data-stu-id="87ca6-226">You can await the returned task, knowing that it has already finished.</span></span> <span data-ttu-id="87ca6-227">以下代码展示了可以如何使用 <xref:System.Threading.Tasks.Task.WhenAny%2A> 等待第一个任务完成，然后再处理其结果。</span><span class="sxs-lookup"><span data-stu-id="87ca6-227">The following code shows how you could use <xref:System.Threading.Tasks.Task.WhenAny%2A> to await the first task to finish and then process its result.</span></span> <span data-ttu-id="87ca6-228">处理已完成任务的结果之后，可以从传递给 `WhenAny` 的任务列表中删除此已完成的任务。</span><span class="sxs-lookup"><span data-stu-id="87ca6-228">After processing the result from the completed task, you remove that completed task from the list of tasks passed to `WhenAny`.</span></span>

```csharp
var breakfastTasks = new List<Task> { eggsTask, baconTask, toastTask };
while (breakfastTasks.Count > 0)
{
    Task finishedTask = await Task.WhenAny(breakfastTasks);
    if (finishedTask == eggsTask)
    {
        Console.WriteLine("eggs are ready");
    }
    else if (finishedTask == baconTask)
    {
        Console.WriteLine("bacon is ready");
    }
    else if (finishedTask == toastTask)
    {
        Console.WriteLine("toast is ready");
    }
    breakfastTasks.Remove(finishedTask);
}
```

<span data-ttu-id="87ca6-229">进行所有这些更改之后，代码的最终版本将如下所示：<a id="final-version"></a></span><span class="sxs-lookup"><span data-stu-id="87ca6-229">After all those changes, the final version of the code looks like this: <a id="final-version"></a></span></span>
:::code language="csharp" source="snippets/index/AsyncBreakfast-final/Program.cs" highlight="9-40":::

:::image type="content" source="media/whenany-async-breakfast.png" alt-text="when any 异步早餐":::

<span data-ttu-id="87ca6-231">异步准备的早餐的最终版本大约花费了 15 分钟，这是因为一些任务能够同时运行，并且该代码能够同时监视多个任务，只在需要时才执行操作。</span><span class="sxs-lookup"><span data-stu-id="87ca6-231">The final version of the asynchronously prepared breakfast took roughly 15 minutes, this is because some tasks were able to run concurrently, and the code was able to monitor multiple tasks at once and only take action when it was needed.</span></span>

<span data-ttu-id="87ca6-232">此最终代码是异步的。</span><span class="sxs-lookup"><span data-stu-id="87ca6-232">This final code is asynchronous.</span></span> <span data-ttu-id="87ca6-233">它更为准确地反映了一个人做早餐的流程。</span><span class="sxs-lookup"><span data-stu-id="87ca6-233">It more accurately reflects how a person would cook a breakfast.</span></span> <span data-ttu-id="87ca6-234">将上述代码与本文中的第一个代码示例进行比较。</span><span class="sxs-lookup"><span data-stu-id="87ca6-234">Compare the preceding code with the first code sample in this article.</span></span> <span data-ttu-id="87ca6-235">阅读代码时，核心操作仍然很明确。</span><span class="sxs-lookup"><span data-stu-id="87ca6-235">The core actions are still clear from reading the code.</span></span> <span data-ttu-id="87ca6-236">你可以按照阅读本文开始时早餐制作说明的相同方式阅读此代码。</span><span class="sxs-lookup"><span data-stu-id="87ca6-236">You can read this code the same way you'd read those instructions for making a breakfast at the beginning of this article.</span></span> <span data-ttu-id="87ca6-237">`async` 和 `await` 的语言功能支持每个人做出转变以遵循这些书面指示：尽可能启动任务，不要在等待任务完成时造成阻塞。</span><span class="sxs-lookup"><span data-stu-id="87ca6-237">The language features for `async` and `await` provide the translation every person makes to follow those written instructions: start tasks as you can and don't block waiting for tasks to complete.</span></span>

## <a name="next-steps"></a><span data-ttu-id="87ca6-238">后续步骤</span><span class="sxs-lookup"><span data-stu-id="87ca6-238">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="87ca6-239">了解基于任务的异步编程模型</span><span class="sxs-lookup"><span data-stu-id="87ca6-239">Learn about the task asynchronous programming model</span></span>](task-asynchronous-programming-model.md)

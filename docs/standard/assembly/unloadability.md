---
title: 如何在 .NET Core 中使用和调试程序集可卸载性
description: 了解如何使用可回收的 AssemblyLoadContext 来加载和卸载托管程序集，以及如何调试可能阻止卸载成功的问题。
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: 9d1f604816dcbd7a84a3692b3cfd24481532789a
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865341"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a><span data-ttu-id="dc4a0-103">如何在 .NET Core 中使用和调试程序集可卸载性</span><span class="sxs-lookup"><span data-stu-id="dc4a0-103">How to use and debug assembly unloadability in .NET Core</span></span>

<span data-ttu-id="dc4a0-104">从 .NET Core 3.0 开始，支持加载和随后卸载一组程序集功能。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-104">Starting with .NET Core 3.0, the ability to load and later unload a set of assemblies is supported.</span></span> <span data-ttu-id="dc4a0-105">在 .NET Framework 中，自定义应用域用于此目的，但 .NET Core 仅支持单个默认应用域。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-105">In .NET Framework, custom app domains were used for this purpose, but .NET Core only supports a single default app domain.</span></span>

<span data-ttu-id="dc4a0-106">.NET Core 3.0 及更高版本支持通过 <xref:System.Runtime.Loader.AssemblyLoadContext> 进行卸载。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-106">.NET Core 3.0 and later versions support unloadability through <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="dc4a0-107">可将一组程序集加载到可回收的 `AssemblyLoadContext` 中，在其中执行方法或仅使用反射检查它们，最后卸载 `AssemblyLoadContext`。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-107">You can load a set of assemblies into a collectible `AssemblyLoadContext`, execute methods in them or just inspect them using reflection, and finally unload the `AssemblyLoadContext`.</span></span> <span data-ttu-id="dc4a0-108">这会卸载加载到 `AssemblyLoadContext` 中的程序集。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-108">That unloads the assemblies loaded into the `AssemblyLoadContext`.</span></span>

<span data-ttu-id="dc4a0-109">使用 `AssemblyLoadContext` 和使用 AppDomain 进行卸载之间存在一个值得注意的差异。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-109">There's one noteworthy difference between the unloading using `AssemblyLoadContext` and using AppDomains.</span></span> <span data-ttu-id="dc4a0-110">对于 Appdomain，卸载为强制执行。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-110">With AppDomains, the unloading is forced.</span></span> <span data-ttu-id="dc4a0-111">卸载时，会中止目标 AppDomain 中运行的所有线程，会销毁目标 AppDomain 中创建的托管 COM 对象，等等。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-111">At unload time, all threads running in the target AppDomain are aborted, managed COM objects created in the target AppDomain are destroyed, and so on.</span></span> <span data-ttu-id="dc4a0-112">对于 `AssemblyLoadContext`，卸载是“协作式的”。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-112">With `AssemblyLoadContext`, the unload is "cooperative".</span></span> <span data-ttu-id="dc4a0-113">调用 <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> 方法只是为了启动卸载。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-113">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> method just initiates the unloading.</span></span> <span data-ttu-id="dc4a0-114">以下目标达成后，卸载完成：</span><span class="sxs-lookup"><span data-stu-id="dc4a0-114">The unloading finishes after:</span></span>

- <span data-ttu-id="dc4a0-115">没有线程将程序集中的方法加载到其调用堆栈上的 `AssemblyLoadContext` 中。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-115">No threads have methods from the assemblies loaded into the `AssemblyLoadContext` on their call stacks.</span></span>
- <span data-ttu-id="dc4a0-116">程序集中的任何类型都不会加载到 `AssemblyLoadContext`，这些类型的实例本身由以下引用：</span><span class="sxs-lookup"><span data-stu-id="dc4a0-116">None of the types from the assemblies loaded into the `AssemblyLoadContext`, instances of those types, and the assemblies themselves are referenced by:</span></span>
  - <span data-ttu-id="dc4a0-117">`AssemblyLoadContext` 外部的引用，弱引用（<xref:System.WeakReference> 或 <xref:System.WeakReference%601>）除外。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-117">References outside of the `AssemblyLoadContext`, except of weak references (<xref:System.WeakReference> or <xref:System.WeakReference%601>).</span></span>
  - <span data-ttu-id="dc4a0-118">`AssemblyLoadContext` 内部和外部的强垃圾回收器 (GC) 句柄（[GCHandleType.Normal](xref:System.Runtime.InteropServices.GCHandleType.Normal) 或 [GCHandleType.Pinned](xref:System.Runtime.InteropServices.GCHandleType.Pinned)）。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-118">Strong garbage collector (GC) handles ([GCHandleType.Normal](xref:System.Runtime.InteropServices.GCHandleType.Normal) or [GCHandleType.Pinned](xref:System.Runtime.InteropServices.GCHandleType.Pinned)) from both inside and outside of the `AssemblyLoadContext`.</span></span>

## <a name="use-collectible-assemblyloadcontext"></a><span data-ttu-id="dc4a0-119">使用可回收的 AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="dc4a0-119">Use collectible AssemblyLoadContext</span></span>

<span data-ttu-id="dc4a0-120">本部分包含详细的分步教程，其中演示了一种简单方法，可以将 .NET Core 应用程序加载到可回收的 `AssemblyLoadContext` 中，执行其入口点，然后将其卸载。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-120">This section contains a detailed step-by-step tutorial that shows a simple way to load a .NET Core application into a collectible `AssemblyLoadContext`, execute its entry point, and then unload it.</span></span> <span data-ttu-id="dc4a0-121">可以在 [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading) 中找到完整示例。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-121">You can find a complete sample at [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading).</span></span>

### <a name="create-a-collectible-assemblyloadcontext"></a><span data-ttu-id="dc4a0-122">创建可回收的 AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="dc4a0-122">Create a collectible AssemblyLoadContext</span></span>

<span data-ttu-id="dc4a0-123">需要从 <xref:System.Runtime.Loader.AssemblyLoadContext> 派生类，并替代其 <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-123">You need to derive your class from the <xref:System.Runtime.Loader.AssemblyLoadContext> and override its <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="dc4a0-124">该方法解析对所有程序集的引用，这些程序集是加载到该 `AssemblyLoadContext` 中的程序集的依赖项。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-124">That method resolves references to all assemblies that are dependencies of assemblies loaded into that `AssemblyLoadContext`.</span></span>

<span data-ttu-id="dc4a0-125">以下代码是最简单的自定义 `AssemblyLoadContext` 示例：</span><span class="sxs-lookup"><span data-stu-id="dc4a0-125">The following code is an example of the simplest custom `AssemblyLoadContext`:</span></span>

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

<span data-ttu-id="dc4a0-126">如你所见，`Load` 方法返回 `null`。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-126">As you can see, the `Load` method returns `null`.</span></span> <span data-ttu-id="dc4a0-127">这意味着所有依赖项程序集都会加载到默认上下文中，而新上下文仅包含显式加载到其中的程序集。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-127">That means that all the dependency assemblies are loaded into the default context, and the new context contains only the assemblies explicitly loaded into it.</span></span>

<span data-ttu-id="dc4a0-128">若要在 `AssemblyLoadContext` 中加载部分或全部依赖项，可以在 `Load` 方法中使用 `AssemblyDependencyResolver`。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-128">If you want to load some or all of the dependencies into the `AssemblyLoadContext` too, you can use the `AssemblyDependencyResolver` in the `Load` method.</span></span> <span data-ttu-id="dc4a0-129">`AssemblyDependencyResolver` 将程序集名称解析为绝对程序集文件路径。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-129">The `AssemblyDependencyResolver` resolves the assembly names to absolute assembly file paths.</span></span> <span data-ttu-id="dc4a0-130">解析程序使用加载到上下文中的主程序集的目录中的 .deps.json 文件和程序集文件  。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-130">The resolver uses the *.deps.json* file and assembly files in the directory of the main assembly loaded into the context.</span></span>

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a><span data-ttu-id="dc4a0-131">使用自定义且可回收的 AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="dc4a0-131">Use a custom collectible AssemblyLoadContext</span></span>

<span data-ttu-id="dc4a0-132">本部分假定使用的是 `TestAssemblyLoadContext` 的较简单版本。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-132">This section assumes the simpler version of the `TestAssemblyLoadContext` is being used.</span></span>

<span data-ttu-id="dc4a0-133">可以创建自定义 `AssemblyLoadContext` 实例并将程序集加载到其中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="dc4a0-133">You can create an instance of the custom `AssemblyLoadContext` and load an assembly into it as follows:</span></span>

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

<span data-ttu-id="dc4a0-134">对于已加载的程序集引用的每个程序集，将调用 `TestAssemblyLoadContext.Load` 方法，这样 `TestAssemblyLoadContext` 可以决定从何处获取程序集。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-134">For each of the assemblies referenced by the loaded assembly, the `TestAssemblyLoadContext.Load` method is called so that the `TestAssemblyLoadContext` can decide where to get the assembly from.</span></span> <span data-ttu-id="dc4a0-135">在示例中，它返回 `null` 以指示它应从运行时默认加载程序集的位置加载到默认上下文中。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-135">In our case, it returns `null` to indicate that it should be loaded into the default context from locations that the runtime uses to load assemblies by default.</span></span>

<span data-ttu-id="dc4a0-136">现在程序集已加载，可从中执行方法。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-136">Now that an assembly was loaded, you can execute a method from it.</span></span> <span data-ttu-id="dc4a0-137">运行 `Main` 方法：</span><span class="sxs-lookup"><span data-stu-id="dc4a0-137">Run the `Main` method:</span></span>

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

<span data-ttu-id="dc4a0-138">在 `Main` 方法返回后，可通过在自定义 `AssemblyLoadContext` 上调用 `Unload` 方法或删除对 `AssemblyLoadContext` 的引用来启动卸载：</span><span class="sxs-lookup"><span data-stu-id="dc4a0-138">After the `Main` method returns, you can initiate unloading by either calling the `Unload` method on the custom `AssemblyLoadContext` or getting rid of the reference you have to the `AssemblyLoadContext`:</span></span>

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

<span data-ttu-id="dc4a0-139">这足以卸载测试程序集。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-139">This is sufficient to unload the test assembly.</span></span> <span data-ttu-id="dc4a0-140">将所有上述内容放入单独的非可内联方法中，以确保 `TestAssemblyLoadContext`、`Assembly` 和 `MethodInfo` (`Assembly.EntryPoint`) 无法通过堆栈槽引用（实际或 JIT 引入的本地变量）保持活动状态。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-140">Let's actually put all of this into a separate non-inlineable method to ensure that the `TestAssemblyLoadContext`, `Assembly`, and `MethodInfo` (the `Assembly.EntryPoint`) can't be kept alive by stack slot references (real- or JIT-introduced locals).</span></span> <span data-ttu-id="dc4a0-141">这可以使 `TestAssemblyLoadContext` 保持活动状态并阻止其卸载。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-141">That could keep the `TestAssemblyLoadContext` alive and prevent the unload.</span></span>

<span data-ttu-id="dc4a0-142">此外，返回对 `AssemblyLoadContext` 的弱引用，以便之后可以使用它来检测卸载是否已完成。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-142">Also, return a weak reference to the `AssemblyLoadContext` so that you can use it later to detect unload completion.</span></span>

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

<span data-ttu-id="dc4a0-143">现在，可运行此函数以加载、执行和卸载程序集。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-143">Now you can run this function to load, execute, and unload the assembly.</span></span>

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

<span data-ttu-id="dc4a0-144">但是，卸载不会立即完成。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-144">However, the unload doesn't complete immediately.</span></span> <span data-ttu-id="dc4a0-145">如上所述，它依赖于垃圾回收器来收集测试程序集中的所有对象。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-145">As previously mentioned, it relies on the garbage collector to collect all the objects from the test assembly.</span></span> <span data-ttu-id="dc4a0-146">在许多情况下，没有必要等待卸载完成。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-146">In many cases, it isn't necessary to wait for the unload completion.</span></span> <span data-ttu-id="dc4a0-147">但是，某些情况下，了解卸载已经完成非常有用。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-147">However, there are cases where it's useful to know that the unload has finished.</span></span> <span data-ttu-id="dc4a0-148">例如，你可能希望删除从磁盘加载到自定义 `AssemblyLoadContext` 中的程序集文件。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-148">For example, you may want to delete the assembly file that was loaded into the custom `AssemblyLoadContext` from disk.</span></span> <span data-ttu-id="dc4a0-149">在这种情况下，可以使用以下代码片段。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-149">In such a case, the following code snippet can be used.</span></span> <span data-ttu-id="dc4a0-150">它会触发垃圾回收并等待循环中挂起的终结器，直到自定义 `AssemblyLoadContext` 的弱引用被设置为 `null`，表示已收集目标对象。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-150">It triggers garbage collection and waits for pending finalizers in a loop until the weak reference to the custom `AssemblyLoadContext` is set to `null`, indicating the target object was collected.</span></span> <span data-ttu-id="dc4a0-151">在大多数情况下，只需要通过循环传递一次。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-151">In most cases, just one pass through the loop is required.</span></span> <span data-ttu-id="dc4a0-152">但对于更复杂的情况，由 `AssemblyLoadContext` 中运行的代码所创建的对象具有终结器，则可能需要更多传递。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-152">However, for more complex cases where objects created by the code running in the `AssemblyLoadContext` have finalizers, more passes may be needed.</span></span>

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a><span data-ttu-id="dc4a0-153">卸载事件</span><span class="sxs-lookup"><span data-stu-id="dc4a0-153">The Unloading event</span></span>

<span data-ttu-id="dc4a0-154">某些情况下，加载到自定义 `AssemblyLoadContext` 中的代码可能需要在启动卸载时执行一些清理。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-154">In some cases, it may be necessary for the code loaded into a custom `AssemblyLoadContext` to perform some cleanup when the unloading is initiated.</span></span> <span data-ttu-id="dc4a0-155">例如，可能需要停止线程或清理某些强 GC 句柄。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-155">For example, it may need to stop threads or clean up strong GC handles.</span></span> <span data-ttu-id="dc4a0-156">在这种情况下可以使用 `Unloading` 事件。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-156">The `Unloading` event can be used in such cases.</span></span> <span data-ttu-id="dc4a0-157">执行必要清理的处理程序可与此事件挂钩。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-157">A handler that performs the necessary cleanup can be hooked to this event.</span></span>

### <a name="troubleshoot-unloadability-issues"></a><span data-ttu-id="dc4a0-158">解决可卸载性问题</span><span class="sxs-lookup"><span data-stu-id="dc4a0-158">Troubleshoot unloadability issues</span></span>

<span data-ttu-id="dc4a0-159">由于卸载的协作性质，很容易忘记可能使内容在可回收的 `AssemblyLoadContext` 中保持活动状态并阻止卸载的引用。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-159">Due to the cooperative nature of the unloading, it's easy to forget about references that may be keeping the stuff in a collectible `AssemblyLoadContext` alive and preventing unload.</span></span> <span data-ttu-id="dc4a0-160">以下是可以包含引用实体（其中一些不明显）的摘要：</span><span class="sxs-lookup"><span data-stu-id="dc4a0-160">Here is a summary of entities (some of them non-obvious) that can hold the references:</span></span>

- <span data-ttu-id="dc4a0-161">保存于可回收的 `AssemblyLoadContext` 外部、存储在堆栈槽或处理器寄存器（由用户代码显式创建或由实时 (JIT) 编译器隐式创建的方法本地变量）中的常规引用、静态变量或强（固定）GC 句柄以及以可传递的方式指向：</span><span class="sxs-lookup"><span data-stu-id="dc4a0-161">Regular references held from outside of the collectible `AssemblyLoadContext` that are stored in a stack slot or a processor register (method locals, either explicitly created by the user code or implicitly by the just-in-time (JIT) compiler), a static variable, or a strong (pinning) GC handle, and transitively pointing to:</span></span>
  - <span data-ttu-id="dc4a0-162">加载到可回收的 `AssemblyLoadContext` 中的程序集。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-162">An assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
  - <span data-ttu-id="dc4a0-163">此类程序集中的类型。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-163">A type from such an assembly.</span></span>
  - <span data-ttu-id="dc4a0-164">此类程序集中的类型的实例。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-164">An instance of a type from such an assembly.</span></span>
- <span data-ttu-id="dc4a0-165">从加载到可回收的 `AssemblyLoadContext` 程序集中运行代码的线程。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-165">Threads running code from an assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
- <span data-ttu-id="dc4a0-166">在可回收的 `AssemblyLoadContext` 中创建的自定义非可回收 `AssemblyLoadContext` 类型的实例。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-166">Instances of custom, non-collectible `AssemblyLoadContext` types created inside of the collectible `AssemblyLoadContext`.</span></span>
- <span data-ttu-id="dc4a0-167">将回调设置为自定义 `AssemblyLoadContext` 中的方法的挂起 <xref:System.Threading.RegisteredWaitHandle> 实例。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-167">Pending <xref:System.Threading.RegisteredWaitHandle> instances with callbacks set to methods in the custom `AssemblyLoadContext`.</span></span>

> [!TIP]
> <span data-ttu-id="dc4a0-168">在以下情况下可能会出现存储在堆栈槽或处理器寄存器中、可阻止卸载 `AssemblyLoadContext` 的对象引用：</span><span class="sxs-lookup"><span data-stu-id="dc4a0-168">Object references that are stored in stack slots or processor registers and that could prevent unloading of an `AssemblyLoadContext` can occur in the following situations:</span></span>
>
> - <span data-ttu-id="dc4a0-169">当直接将函数调用结果传递给另一个函数时，即使没有用户创建的本地变量。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-169">When function call results are passed directly to another function, even though there is no user-created local variable.</span></span>
> - <span data-ttu-id="dc4a0-170">当 JIT 编译器保留对可在方法中的某个点使用的对象的引用时。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-170">When the JIT compiler keeps a reference to an object that was available at some point in a method.</span></span>

## <a name="debug-unloading-issues"></a><span data-ttu-id="dc4a0-171">调试卸载问题</span><span class="sxs-lookup"><span data-stu-id="dc4a0-171">Debug unloading issues</span></span>

<span data-ttu-id="dc4a0-172">调试卸载问题可能比较繁琐。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-172">Debugging issues with unloading can be tedious.</span></span> <span data-ttu-id="dc4a0-173">你可能会遇到这样的情况：你不知道哪些内容可以使 `AssemblyLoadContext` 保持活动状态，但卸载会失败。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-173">You can get into situations where you don't know what can be holding an `AssemblyLoadContext` alive, but the unload fails.</span></span> <span data-ttu-id="dc4a0-174">帮助解决此问题的最佳武器是带有 SOS 插件的 WinDbg（Unix 上的 LLDB）。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-174">The best weapon to help with that is WinDbg (LLDB on Unix) with the SOS plugin.</span></span> <span data-ttu-id="dc4a0-175">需要查找哪些内容使属于特定 `AssemblyLoadContext` 的 `LoaderAllocator` 保持活动状态。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-175">You need to find what's keeping a `LoaderAllocator` belonging to the specific `AssemblyLoadContext` alive.</span></span> <span data-ttu-id="dc4a0-176">SOS 插件可让你查看 GC 堆对象、其层次结构和根。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-176">The SOS plugin allows you to look at GC heap objects, their hierarchies, and roots.</span></span>

<span data-ttu-id="dc4a0-177">若要将插件加载到调试器中，请在调试器命令行中输入以下命令：</span><span class="sxs-lookup"><span data-stu-id="dc4a0-177">To load the plugin into the debugger, enter the following command in the debugger command line:</span></span>

<span data-ttu-id="dc4a0-178">在 WinDbg（似乎 WinDbg 在进入 .NET Core 应用程序时会自动执行此操作）中：</span><span class="sxs-lookup"><span data-stu-id="dc4a0-178">In WinDbg (it seems WinDbg does that automatically when breaking into .NET Core application):</span></span>

```console
.loadby sos coreclr
```

<span data-ttu-id="dc4a0-179">在 LLDB 中：</span><span class="sxs-lookup"><span data-stu-id="dc4a0-179">In LLDB:</span></span>

```console
plugin load /path/to/libsosplugin.so
```

<span data-ttu-id="dc4a0-180">调试卸载时出现问题的示例程序。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-180">Let's debug an example program that has problems with unloading.</span></span> <span data-ttu-id="dc4a0-181">源代码包含在以下内容中。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-181">Source code is included below.</span></span> <span data-ttu-id="dc4a0-182">在 WinDbg 下运行它时，程序将在尝试检查卸载是否成功后立即进入调试器。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-182">When you run it under WinDbg, the program breaks into the debugger right after attempting to check for the unload success.</span></span> <span data-ttu-id="dc4a0-183">然后即可开始查找原因。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-183">You can then start looking for the culprits.</span></span>

> [!TIP]
> <span data-ttu-id="dc4a0-184">如果使用 Unix 上的 LLDB 进行调试，则以下示例中的 SOS 命令的前面没有 `!`。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-184">If you debug using LLDB on Unix, the SOS commands in the following examples don't have the `!` in front of them.</span></span>

```console
!dumpheap -type LoaderAllocator
```

<span data-ttu-id="dc4a0-185">此命令转储类型名称包含 GC 堆中的 `LoaderAllocator` 的所有对象。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-185">This command dumps all objects with a type name containing `LoaderAllocator` that are in the GC heap.</span></span> <span data-ttu-id="dc4a0-186">下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="dc4a0-186">Here is an example:</span></span>

```console
         Address               MT     Size
000002b78000ce40 00007ffadc93a288       48
000002b78000ceb0 00007ffadc93a218       24

Statistics:
              MT    Count    TotalSize Class Name
00007ffadc93a218        1           24 System.Reflection.LoaderAllocatorScout
00007ffadc93a288        1           48 System.Reflection.LoaderAllocator
Total 2 objects
```

<span data-ttu-id="dc4a0-187">在下面的“Statistics:”部分中，检查属于 `System.Reflection.LoaderAllocator` 的 `MT` (`MethodTable`)，这是我们关注的对象。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-187">In the "Statistics:" part below, check the `MT` (`MethodTable`) belonging to the `System.Reflection.LoaderAllocator`, which is the object we care about.</span></span> <span data-ttu-id="dc4a0-188">然后在开头的列表中，查找 `MT` 匹配该条目的条目，并获取对象本身的地址。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-188">Then, in the list at the beginning, find the entry with `MT` matching that one and get the address of the object itself.</span></span> <span data-ttu-id="dc4a0-189">在示例中，其为“000002b78000ce40”。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-189">In our case, it is "000002b78000ce40".</span></span>

<span data-ttu-id="dc4a0-190">现在我们知道了 `LoaderAllocator` 对象的地址，可使用另一个命令来查找其 GC 根：</span><span class="sxs-lookup"><span data-stu-id="dc4a0-190">Now that we know the address of the `LoaderAllocator` object, we can use another command to find its GC roots:</span></span>

```console
!gcroot -all 0x000002b78000ce40
```

<span data-ttu-id="dc4a0-191">此命令转储通向 `LoaderAllocator` 实例的对象引用链。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-191">This command dumps the chain of object references that lead to the `LoaderAllocator` instance.</span></span> <span data-ttu-id="dc4a0-192">该列表以根（使 `LoaderAllocator` 保持活动状态的实体）开头，因此为问题的核心。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-192">The list starts with the root, which is the entity that keeps our `LoaderAllocator` alive and thus is the core of the problem.</span></span> <span data-ttu-id="dc4a0-193">根可以是堆栈槽、处理器寄存器、GC 句柄或静态变量。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-193">The root can be a stack slot, a processor register, a GC handle, or a static variable.</span></span>

<span data-ttu-id="dc4a0-194">以下是 `gcroot` 命令输出的示例：</span><span class="sxs-lookup"><span data-stu-id="dc4a0-194">Here is an example of the output of the `gcroot` command:</span></span>

```console
Thread 4ac:
    000000cf9499dd20 00007ffa7d0236bc example.Program.Main(System.String[]) [E:\unloadability\example\Program.cs @ 70]
        rbp-20: 000000cf9499dd90
            ->  000002b78000d328 System.Reflection.RuntimeMethodInfo
            ->  000002b78000d1f8 System.RuntimeType+RuntimeTypeCache
            ->  000002b78000d1d0 System.RuntimeType
            ->  000002b78000ce40 System.Reflection.LoaderAllocator

HandleTable:
    000002b7f8a81198 (strong handle)
    -> 000002b78000d948 test.Test
    -> 000002b78000ce40 System.Reflection.LoaderAllocator

    000002b7f8a815f8 (pinned handle)
    -> 000002b790001038 System.Object[]
    -> 000002b78000d390 example.TestInfo
    -> 000002b78000d328 System.Reflection.RuntimeMethodInfo
    -> 000002b78000d1f8 System.RuntimeType+RuntimeTypeCache
    -> 000002b78000d1d0 System.RuntimeType
    -> 000002b78000ce40 System.Reflection.LoaderAllocator

Found 3 roots.
```

<span data-ttu-id="dc4a0-195">下一步是确定根所在的位置以便对其进行修复。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-195">The next step is to figure out where the root is located so you can fix it.</span></span> <span data-ttu-id="dc4a0-196">最简单的情况是根为堆栈槽或处理器寄存器。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-196">The easiest case is when the root is a stack slot or a processor register.</span></span> <span data-ttu-id="dc4a0-197">在这种情况下，`gcroot` 会显示其框架包含根的函数的名称以及执行该函数的线程。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-197">In that case, the `gcroot` shows the name of the function whose frame contains the root and the thread executing that function.</span></span> <span data-ttu-id="dc4a0-198">困难的情况是根为静态变量或 GC 句柄。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-198">The difficult case is when the root is a static variable or a GC handle.</span></span>

<span data-ttu-id="dc4a0-199">在上面的示例中，第一个根为 `System.Reflection.RuntimeMethodInfo` 类型的本地变量，存储在函数 `example.Program.Main(System.String[])` 的框架中，地址为 `rbp-20`（`rbp` 意为处理器寄存器 `rbp`，-20 意为该寄存器的十六进制偏移量）。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-199">In the previous example, the first root is a local of type `System.Reflection.RuntimeMethodInfo` stored in the frame of the function `example.Program.Main(System.String[])` at address `rbp-20` (`rbp` is the processor register `rbp` and -20 is a hexadecimal offset from that register).</span></span>

<span data-ttu-id="dc4a0-200">第二个根为普通（强）`GCHandle`，其包含对 `test.Test` 类实例的引用。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-200">The second root is a normal (strong) `GCHandle` that holds a reference to an instance of the `test.Test` class.</span></span>

<span data-ttu-id="dc4a0-201">第三个根为固定的 `GCHandle`。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-201">The third root is a pinned `GCHandle`.</span></span> <span data-ttu-id="dc4a0-202">这实际上是一个静态变量，但遗憾的是，无法进行澄清。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-202">This one is actually a static variable, but unfortunately, there is no way to tell.</span></span> <span data-ttu-id="dc4a0-203">引用类型的静态变量存储在内部运行时结构中的托管对象数组中。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-203">Statics for reference types are stored in a managed object array in internal runtime structures.</span></span>

<span data-ttu-id="dc4a0-204">另一种可阻止卸载 `AssemblyLoadContext` 的情况为，线程具有来源于加载到其堆栈上的 `AssemblyLoadContext` 程序集的方法框架。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-204">Another case that can prevent unloading of an `AssemblyLoadContext` is when a thread has a frame of a method from an assembly loaded into the `AssemblyLoadContext` on its stack.</span></span> <span data-ttu-id="dc4a0-205">可通过转储所有线程的托管调用堆栈进行检查：</span><span class="sxs-lookup"><span data-stu-id="dc4a0-205">You can check that by dumping managed call stacks of all threads:</span></span>

```console
~*e !clrstack
```

<span data-ttu-id="dc4a0-206">此命令表示“将 `!clrstack` 命令应用于所有线程”。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-206">The command means "apply to all threads the `!clrstack` command".</span></span> <span data-ttu-id="dc4a0-207">以下是此示例中该命令的输出。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-207">The following is the output of that command for the example.</span></span> <span data-ttu-id="dc4a0-208">遗憾的是，Unix 上的 LLDB 无法将命令应用于所有线程，因此，必须手动切换线程并重复 `clrstack` 命令。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-208">Unfortunately, LLDB on Unix doesn't have any way to apply a command to all threads, so you must manually switch threads and repeat the `clrstack` command.</span></span> <span data-ttu-id="dc4a0-209">忽略调试器显示“无法审核托管堆栈”的所有线程。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-209">Ignore all threads where the debugger says "Unable to walk the managed stack".</span></span>

```console
OS Thread Id: 0x6ba8 (0)
        Child SP               IP Call Site
0000001fc697d5c8 00007ffb50d9de12 [HelperMethodFrame: 0000001fc697d5c8] System.Diagnostics.Debugger.BreakInternal()
0000001fc697d6d0 00007ffa864765fa System.Diagnostics.Debugger.Break()
0000001fc697d700 00007ffa864736bc example.Program.Main(System.String[]) [E:\unloadability\example\Program.cs @ 70]
0000001fc697d998 00007ffae5fdc1e3 [GCFrame: 0000001fc697d998]
0000001fc697df28 00007ffae5fdc1e3 [GCFrame: 0000001fc697df28]
OS Thread Id: 0x2ae4 (1)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x61a4 (2)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x7fdc (3)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x5390 (4)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x5ec8 (5)
        Child SP               IP Call Site
0000001fc70ff6e0 00007ffb5437f6e4 [DebuggerU2MCatchHandlerFrame: 0000001fc70ff6e0]
OS Thread Id: 0x4624 (6)
        Child SP               IP Call Site
GetFrameContext failed: 1
0000000000000000 0000000000000000
OS Thread Id: 0x60bc (7)
        Child SP               IP Call Site
0000001fc727f158 00007ffb5437fce4 [HelperMethodFrame: 0000001fc727f158] System.Threading.Thread.SleepInternal(Int32)
0000001fc727f260 00007ffb37ea7c2b System.Threading.Thread.Sleep(Int32)
0000001fc727f290 00007ffa865005b3 test.Program.ThreadProc() [E:\unloadability\test\Program.cs @ 17]
0000001fc727f2c0 00007ffb37ea6a5b System.Threading.Thread.ThreadMain_ThreadStart()
0000001fc727f2f0 00007ffadbc4cbe3 System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object)
0000001fc727f568 00007ffae5fdc1e3 [GCFrame: 0000001fc727f568]
0000001fc727f7f0 00007ffae5fdc1e3 [DebuggerU2MCatchHandlerFrame: 0000001fc727f7f0]

```

<span data-ttu-id="dc4a0-210">如你所见，最后一个线程具有 `test.Program.ThreadProc()`。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-210">As you can see, the last thread has `test.Program.ThreadProc()`.</span></span> <span data-ttu-id="dc4a0-211">这是从加载到 `AssemblyLoadContext` 的程序集中的函数，因此它使 `AssemblyLoadContext` 保持活动状态。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-211">This is a function from the assembly loaded into the `AssemblyLoadContext`, and so it keeps the `AssemblyLoadContext` alive.</span></span>

## <a name="example-source-with-unloadability-issues"></a><span data-ttu-id="dc4a0-212">具有可卸载性问题的示例源</span><span class="sxs-lookup"><span data-stu-id="dc4a0-212">Example source with unloadability issues</span></span>

<span data-ttu-id="dc4a0-213">上面的调试示例中使用了以下代码。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-213">The following code is used in the previous debugging example.</span></span>

### <a name="main-testing-program"></a><span data-ttu-id="dc4a0-214">主要测试程序</span><span class="sxs-lookup"><span data-stu-id="dc4a0-214">Main testing program</span></span>

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a><span data-ttu-id="dc4a0-215">程序已加载到 TestAssemblyLoadContext 中</span><span class="sxs-lookup"><span data-stu-id="dc4a0-215">Program loaded into the TestAssemblyLoadContext</span></span>

<span data-ttu-id="dc4a0-216">以下代码表示传递给主测试程序中 `ExecuteAndUnload` 方法的 test.dll。</span><span class="sxs-lookup"><span data-stu-id="dc4a0-216">The following code represents the *test.dll* passed to the `ExecuteAndUnload` method in the main testing program.</span></span>

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]

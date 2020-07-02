---
title: 清理未托管资源
description: 请参阅如何清理不由 .NET 垃圾回收器处理的非托管资源，如文件、窗口、网络或数据库连接。
ms.date: 05/13/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- Close method
- Dispose method
- garbage collector
- garbage collection, unmanaged resources
- cleanup operations
- explicit cleanups
- unmanaged resource cleanup
- Finalize method
ms.assetid: a17b0066-71c2-4ba4-9822-8e19332fc213
ms.openlocfilehash: 07a8d754f1fc2612ae53407fa1b12a1eab7e38f2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599824"
---
# <a name="cleaning-up-unmanaged-resources"></a><span data-ttu-id="077f9-103">清理未托管资源</span><span class="sxs-lookup"><span data-stu-id="077f9-103">Cleaning up unmanaged resources</span></span>

<span data-ttu-id="077f9-104">对于应用创建的大多数对象，可以依赖 [.NET 垃圾回收器](index.md)来进行内存管理。</span><span class="sxs-lookup"><span data-stu-id="077f9-104">For the majority of the objects that your app creates, you can rely on the [.NET garbage collector](index.md) to handle memory management.</span></span> <span data-ttu-id="077f9-105">但是，如果创建包含非托管资源的对象，则当你使用完非托管资源后，必须显式释放这些资源。</span><span class="sxs-lookup"><span data-stu-id="077f9-105">However, when you create objects that include unmanaged resources, you must explicitly release those resources when you finish using them.</span></span> <span data-ttu-id="077f9-106">最常用的非托管资源类型是包装操作系统资源的对象，如文件、窗口、网络连接或数据库连接。</span><span class="sxs-lookup"><span data-stu-id="077f9-106">The most common types of unmanaged resources are objects that wrap operating system resources, such as files, windows, network connections, or database connections.</span></span> <span data-ttu-id="077f9-107">虽然垃圾回收器可以跟踪封装非托管资源的对象的生存期，但无法了解如何发布并清理这些非托管资源。</span><span class="sxs-lookup"><span data-stu-id="077f9-107">Although the garbage collector is able to track the lifetime of an object that encapsulates an unmanaged resource, it doesn't know how to release and clean up the unmanaged resource.</span></span>

<span data-ttu-id="077f9-108">如果你的类型使用非托管资源，则应执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="077f9-108">If your types use unmanaged resources, you should do the following:</span></span>

- <span data-ttu-id="077f9-109">实现[清理模式](implementing-dispose.md)。</span><span class="sxs-lookup"><span data-stu-id="077f9-109">Implement the [dispose pattern](implementing-dispose.md).</span></span> <span data-ttu-id="077f9-110">这要求你提供 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 实现以启用非托管资源的确定性释放。</span><span class="sxs-lookup"><span data-stu-id="077f9-110">This requires that you provide an <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation to enable the deterministic release of unmanaged resources.</span></span> <span data-ttu-id="077f9-111">当不再需要此对象（或其使用的资源）时，类型使用者可调用 <xref:System.IDisposable.Dispose%2A>。</span><span class="sxs-lookup"><span data-stu-id="077f9-111">A consumer of your type calls <xref:System.IDisposable.Dispose%2A> when the object (and the resources it uses) are no longer needed.</span></span> <span data-ttu-id="077f9-112"><xref:System.IDisposable.Dispose%2A> 方法立即释放非托管资源。</span><span class="sxs-lookup"><span data-stu-id="077f9-112">The <xref:System.IDisposable.Dispose%2A> method immediately releases the unmanaged resources.</span></span>

- <span data-ttu-id="077f9-113">在类型使用者忘记调用 <xref:System.IDisposable.Dispose%2A> 的情况下，请提供一种方法来释放非托管资源。</span><span class="sxs-lookup"><span data-stu-id="077f9-113">In the event that a consumer of your type forgets to call <xref:System.IDisposable.Dispose%2A>, provide a way for your unmanaged resources to be released.</span></span> <span data-ttu-id="077f9-114">有两种方法可以实现此目的：</span><span class="sxs-lookup"><span data-stu-id="077f9-114">There are two ways to do this:</span></span>

  - <span data-ttu-id="077f9-115">使用安全句柄包装非托管资源。</span><span class="sxs-lookup"><span data-stu-id="077f9-115">Use a safe handle to wrap your unmanaged resource.</span></span> <span data-ttu-id="077f9-116">这是推荐采用的方法。</span><span class="sxs-lookup"><span data-stu-id="077f9-116">This is the recommended technique.</span></span> <span data-ttu-id="077f9-117">安全句柄派生自 <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> 抽象类，并包含可靠的 <xref:System.Object.Finalize%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="077f9-117">Safe handles are derived from the <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> abstract class and include a robust <xref:System.Object.Finalize%2A> method.</span></span> <span data-ttu-id="077f9-118">在使用安全句柄时，只需实现 <xref:System.IDisposable> 接口并在 <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> 实现中调用安全句柄的 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="077f9-118">When you use a safe handle, you simply implement the <xref:System.IDisposable> interface and call your safe handle's <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> method in your <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="077f9-119">如果未调用安全句柄的 <xref:System.IDisposable.Dispose%2A> 方法，则垃圾回收器将自动调用安全句柄的终结器。</span><span class="sxs-lookup"><span data-stu-id="077f9-119">The safe handle's finalizer is called automatically by the garbage collector if its <xref:System.IDisposable.Dispose%2A> method is not called.</span></span>

    <span data-ttu-id="077f9-120">—或—</span><span class="sxs-lookup"><span data-stu-id="077f9-120">—**or**—</span></span>

  - <span data-ttu-id="077f9-121">重写 <xref:System.Object.Finalize%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="077f9-121">Override the <xref:System.Object.Finalize%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="077f9-122">当类型使用者无法调用 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 以确定性地释放非托管资源时，终止会启用对非托管资源的非确定性释放。</span><span class="sxs-lookup"><span data-stu-id="077f9-122">Finalization enables the non-deterministic release of unmanaged resources when the consumer of a type fails to call <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> to dispose of them deterministically.</span></span> <span data-ttu-id="077f9-123">通过重写 <xref:System.Object.Finalize%2A?displayProperty=nameWithType> 方法来定义[终结器](../../csharp/programming-guide/classes-and-structs/destructors.md)。</span><span class="sxs-lookup"><span data-stu-id="077f9-123">Define a [finalizer](../../csharp/programming-guide/classes-and-structs/destructors.md) by overriding the <xref:System.Object.Finalize%2A?displayProperty=nameWithType> method.</span></span>

  > [!WARNING]
  > <span data-ttu-id="077f9-124">但是，由于对象终止是一项复杂且易出错的操作，建议你使用安全句柄，而不是提供你自己的终结器。</span><span class="sxs-lookup"><span data-stu-id="077f9-124">However, because object finalization can be a complex and an error-prone operation, we recommend that you use a safe handle instead of providing your own finalizer.</span></span>

<span data-ttu-id="077f9-125">然后，类型使用者可直接调用 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 实现以释放非托管资源使用的内存。</span><span class="sxs-lookup"><span data-stu-id="077f9-125">Consumers of your type can then call your <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation directly to free memory used by unmanaged resources.</span></span> <span data-ttu-id="077f9-126">在正确实现 <xref:System.IDisposable.Dispose%2A> 方法时，安全句柄的 <xref:System.Object.Finalize%2A> 方法或 <xref:System.Object.Finalize%2A?displayProperty=nameWithType> 方法的重写会在未调用 <xref:System.IDisposable.Dispose%2A> 方法的情况下阻止清理资源。</span><span class="sxs-lookup"><span data-stu-id="077f9-126">When you properly implement a <xref:System.IDisposable.Dispose%2A> method, either your safe handle's <xref:System.Object.Finalize%2A> method or your own override of the <xref:System.Object.Finalize%2A?displayProperty=nameWithType> method becomes a safeguard to clean up resources in the event that the <xref:System.IDisposable.Dispose%2A> method is not called.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="077f9-127">本节内容</span><span class="sxs-lookup"><span data-stu-id="077f9-127">In this section</span></span>

<span data-ttu-id="077f9-128">[实现 Dispose 方法](implementing-dispose.md)介绍如何实现用于释放非托管资源的释放模式。</span><span class="sxs-lookup"><span data-stu-id="077f9-128">[Implementing a Dispose method](implementing-dispose.md) describes how to implement the dispose pattern for releasing unmanaged resources.</span></span>

<span data-ttu-id="077f9-129">[使用实现 `IDisposable` 的对象](using-objects.md)介绍类型使用者如何确保调用其 <xref:System.IDisposable.Dispose%2A> 实现。</span><span class="sxs-lookup"><span data-stu-id="077f9-129">[Using objects that implement `IDisposable`](using-objects.md) describes how consumers of a type ensure that its <xref:System.IDisposable.Dispose%2A> implementation is called.</span></span> <span data-ttu-id="077f9-130">建议使用 C# `using`（或 Visual Basic `Using`）语句来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="077f9-130">We recommend using the C# `using` (or the Visual Basic `Using`) statement to do this.</span></span>

## <a name="reference"></a><span data-ttu-id="077f9-131">参考</span><span class="sxs-lookup"><span data-stu-id="077f9-131">Reference</span></span>

| <span data-ttu-id="077f9-132">类型/成员</span><span class="sxs-lookup"><span data-stu-id="077f9-132">Type / Member</span></span> | <span data-ttu-id="077f9-133">描述</span><span class="sxs-lookup"><span data-stu-id="077f9-133">Description</span></span> |
|--|--|
| <xref:System.IDisposable?displayProperty=nameWithType> | <span data-ttu-id="077f9-134">定义用于释放非托管资源的 <xref:System.IDisposable.Dispose%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="077f9-134">Defines the <xref:System.IDisposable.Dispose%2A> method for releasing unmanaged resources.</span></span> |
| <xref:System.Object.Finalize%2A?displayProperty=nameWithType> | <span data-ttu-id="077f9-135">如果 <xref:System.IDisposable.Dispose%2A> 方法未释放非托管资源，则准备对象终止。</span><span class="sxs-lookup"><span data-stu-id="077f9-135">Provides for object finalization if unmanaged resources are not released by the <xref:System.IDisposable.Dispose%2A> method.</span></span> |
| <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> | <span data-ttu-id="077f9-136">取消终止。</span><span class="sxs-lookup"><span data-stu-id="077f9-136">Suppresses finalization.</span></span> <span data-ttu-id="077f9-137">通常，从 `Dispose` 方法调用此方法来阻止执行终结器。</span><span class="sxs-lookup"><span data-stu-id="077f9-137">This method is customarily called from a `Dispose` method to prevent a finalizer from executing.</span></span> |

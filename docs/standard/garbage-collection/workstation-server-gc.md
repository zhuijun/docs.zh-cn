---
title: 工作站和服务器垃圾回收 (GC)
description: 了解 .NET 中的工作站和服务器垃圾回收。
ms.date: 04/21/2020
helpviewer_keywords:
- garbage collection, workstation
- garbage collection, server
- workstation garbage collection
- server garbage collection
ms.openlocfilehash: 640b5f42c1f841c2537284e4721e827248e3d300
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87917016"
---
# <a name="workstation-and-server-garbage-collection"></a><span data-ttu-id="8e984-103">工作站和服务器垃圾回收</span><span class="sxs-lookup"><span data-stu-id="8e984-103">Workstation and server garbage collection</span></span>

<span data-ttu-id="8e984-104">垃圾回收器可自行优化并且适用于多种方案。</span><span class="sxs-lookup"><span data-stu-id="8e984-104">The garbage collector is self-tuning and can work in a wide variety of scenarios.</span></span> <span data-ttu-id="8e984-105">不过，你可以基于工作负载的特征[设置垃圾回收的类型](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection)。</span><span class="sxs-lookup"><span data-stu-id="8e984-105">However, you can [set the type of garbage collection](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection) based on the characteristics of the workload.</span></span> <span data-ttu-id="8e984-106">CLR 提供了以下类型的垃圾回收：</span><span class="sxs-lookup"><span data-stu-id="8e984-106">The CLR provides the following types of garbage collection:</span></span>

- <span data-ttu-id="8e984-107">工作站垃圾回收 (GC) 是为客户端应用设计的。</span><span class="sxs-lookup"><span data-stu-id="8e984-107">Workstation garbage collection (GC), which is designed for client apps.</span></span> <span data-ttu-id="8e984-108">它是独立应用的默认 GC 风格。</span><span class="sxs-lookup"><span data-stu-id="8e984-108">It's the default GC flavor for standalone apps.</span></span> <span data-ttu-id="8e984-109">对于托管应用（例如由 ASP.NET 托管的应用），由主机确定默认 GC 风格。</span><span class="sxs-lookup"><span data-stu-id="8e984-109">For hosted apps, for example, those hosted by ASP.NET, the host determines the default GC flavor.</span></span>

  <span data-ttu-id="8e984-110">工作站垃圾回收既可以是并发的，也可以是非并发的。</span><span class="sxs-lookup"><span data-stu-id="8e984-110">Workstation garbage collection can be concurrent or non-concurrent.</span></span> <span data-ttu-id="8e984-111">并发（或后台  ）垃圾回收使托管线程能够在垃圾回收期间继续操作。</span><span class="sxs-lookup"><span data-stu-id="8e984-111">Concurrent (or *background*) garbage collection enables managed threads to continue operations during a garbage collection.</span></span> <span data-ttu-id="8e984-112">[后台垃圾回收](background-gc.md)替换 .NET Framework 4 及更高版本中的[并行垃圾回收](background-gc.md#concurrent-garbage-collection)。</span><span class="sxs-lookup"><span data-stu-id="8e984-112">[Background garbage collection](background-gc.md) replaces [concurrent garbage collection](background-gc.md#concurrent-garbage-collection) in .NET Framework 4 and later versions.</span></span>

- <span data-ttu-id="8e984-113">服务器垃圾回收，用于需要高吞吐量和可伸缩性的服务器应用程序。</span><span class="sxs-lookup"><span data-stu-id="8e984-113">Server garbage collection, which is intended for server applications that need high throughput and scalability.</span></span>

  - <span data-ttu-id="8e984-114">在 .NET Core 中，服务器垃圾回收既可以是非并发也可以是后台执行。</span><span class="sxs-lookup"><span data-stu-id="8e984-114">In .NET Core, server garbage collection can be non-concurrent or background.</span></span>

  - <span data-ttu-id="8e984-115">在 .NET Framework 4.5 和更高版本中，服务器垃圾回收既可以是非并发也可以是后台执行。</span><span class="sxs-lookup"><span data-stu-id="8e984-115">In .NET Framework 4.5 and later versions, server garbage collection can be non-concurrent or background.</span></span> <span data-ttu-id="8e984-116">在 .NET Framework 4 和以前的版本中，服务器垃圾回收非并行运行。</span><span class="sxs-lookup"><span data-stu-id="8e984-116">In .NET Framework 4 and previous versions, server garbage collection is non-concurrent.</span></span>

<span data-ttu-id="8e984-117">下图演示了服务器上执行垃圾回收的专用线程：</span><span class="sxs-lookup"><span data-stu-id="8e984-117">The following illustration shows the dedicated threads that perform the garbage collection on a server:</span></span>

![服务器垃圾回收线程](media/gc-server.png)

## <a name="performance-considerations"></a><span data-ttu-id="8e984-119">性能注意事项</span><span class="sxs-lookup"><span data-stu-id="8e984-119">Performance considerations</span></span>

### <a name="workstation-gc"></a><span data-ttu-id="8e984-120">工作站 GC</span><span class="sxs-lookup"><span data-stu-id="8e984-120">Workstation GC</span></span>

<span data-ttu-id="8e984-121">以下是工作站垃圾回收的线程处理和性能注意事项：</span><span class="sxs-lookup"><span data-stu-id="8e984-121">The following are threading and performance considerations for workstation garbage collection:</span></span>

- <span data-ttu-id="8e984-122">回收发生在触发垃圾回收的用户线程上，并保留相同优先级。</span><span class="sxs-lookup"><span data-stu-id="8e984-122">The collection occurs on the user thread that triggered the garbage collection and remains at the same priority.</span></span> <span data-ttu-id="8e984-123">因为用户线程通常以普通优先级运行，所以垃圾回收器（在普通优先级线程上运行）必须与其他线程竞争 CPU 时间。</span><span class="sxs-lookup"><span data-stu-id="8e984-123">Because user threads typically run at normal priority, the garbage collector (which runs on a normal priority thread) must compete with other threads for CPU time.</span></span> <span data-ttu-id="8e984-124">（运行本机代码的线程不会由于服务器或工作站垃圾回收而挂起。）</span><span class="sxs-lookup"><span data-stu-id="8e984-124">(Threads that run native code are not suspended on either server or workstation garbage collection.)</span></span>

- <span data-ttu-id="8e984-125">工作站垃圾回收始终用于只有一个处理器的计算机，无论[配置设置](../../core/run-time-config/garbage-collector.md#workstation-vs-server)如何。</span><span class="sxs-lookup"><span data-stu-id="8e984-125">Workstation garbage collection is always used on a computer that has only one processor, regardless of the [configuration setting](../../core/run-time-config/garbage-collector.md#workstation-vs-server).</span></span>

### <a name="server-gc"></a><span data-ttu-id="8e984-126">服务器 GC</span><span class="sxs-lookup"><span data-stu-id="8e984-126">Server GC</span></span>

<span data-ttu-id="8e984-127">以下是服务器垃圾回收的线程处理和性能注意事项：</span><span class="sxs-lookup"><span data-stu-id="8e984-127">The following are threading and performance considerations for server garbage collection:</span></span>

- <span data-ttu-id="8e984-128">回收发生在以 `THREAD_PRIORITY_HIGHEST` 优先级运行的多个专用线程上。</span><span class="sxs-lookup"><span data-stu-id="8e984-128">The collection occurs on multiple dedicated threads that are running at `THREAD_PRIORITY_HIGHEST` priority level.</span></span>

- <span data-ttu-id="8e984-129">为每个 CPU 提供一个用于执行垃圾回收的一个堆和专用线程，并将同时回收这些堆。</span><span class="sxs-lookup"><span data-stu-id="8e984-129">A heap and a dedicated thread to perform garbage collection are provided for each CPU, and the heaps are collected at the same time.</span></span> <span data-ttu-id="8e984-130">每个堆都包含一个小对象堆和一个大对象堆，并且所有的堆都可由用户代码访问。</span><span class="sxs-lookup"><span data-stu-id="8e984-130">Each heap contains a small object heap and a large object heap, and all heaps can be accessed by user code.</span></span> <span data-ttu-id="8e984-131">不同堆上的对象可以相互引用。</span><span class="sxs-lookup"><span data-stu-id="8e984-131">Objects on different heaps can refer to each other.</span></span>

- <span data-ttu-id="8e984-132">因为多个垃圾回收线程一起工作，所以对于相同大小的堆，服务器垃圾回收比工作站垃圾回收更快一些。</span><span class="sxs-lookup"><span data-stu-id="8e984-132">Because multiple garbage collection threads work together, server garbage collection is faster than workstation garbage collection on the same size heap.</span></span>

- <span data-ttu-id="8e984-133">服务器垃圾回收通常具有更大的段。</span><span class="sxs-lookup"><span data-stu-id="8e984-133">Server garbage collection often has larger size segments.</span></span> <span data-ttu-id="8e984-134">但是，这是通常情况：段大小特定于实现且可能更改。</span><span class="sxs-lookup"><span data-stu-id="8e984-134">However, this is only a generalization: segment size is implementation-specific and is subject to change.</span></span> <span data-ttu-id="8e984-135">调整应用程序时，不要假设垃圾回收器分配的段大小。</span><span class="sxs-lookup"><span data-stu-id="8e984-135">Don't make assumptions about the size of segments allocated by the garbage collector when tuning your app.</span></span>

- <span data-ttu-id="8e984-136">服务器垃圾回收会占用大量资源。</span><span class="sxs-lookup"><span data-stu-id="8e984-136">Server garbage collection can be resource-intensive.</span></span> <span data-ttu-id="8e984-137">例如，假设在一台有 4 个处理器的计算机上，运行着 12 个使用服务器 GC 的进程。</span><span class="sxs-lookup"><span data-stu-id="8e984-137">For example, imagine that there are 12 processes that use server GC running on a computer that has four processors.</span></span> <span data-ttu-id="8e984-138">如果所有进程碰巧同时回收垃圾，它们会相互干扰，因为将在同一个处理器上调度 12 个线程。</span><span class="sxs-lookup"><span data-stu-id="8e984-138">If all the processes happen to collect garbage at the same time, they would interfere with each other, as there would be 12 threads scheduled on the same processor.</span></span> <span data-ttu-id="8e984-139">如果进程处于活动状态，则最好不要让它们都使用服务器 GC。</span><span class="sxs-lookup"><span data-stu-id="8e984-139">If the processes are active, it's not a good idea to have them all use server GC.</span></span>

<span data-ttu-id="8e984-140">如果运行应用程序的数百个实例，请考虑使用工作站垃圾回收并禁用并发垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="8e984-140">If you're running hundreds of instances of an application, consider using workstation garbage collection with concurrent garbage collection disabled.</span></span> <span data-ttu-id="8e984-141">这可以减少上下文切换，从而提高性能。</span><span class="sxs-lookup"><span data-stu-id="8e984-141">This will result in less context switching, which can improve performance.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e984-142">请参阅</span><span class="sxs-lookup"><span data-stu-id="8e984-142">See also</span></span>

- [<span data-ttu-id="8e984-143">后台垃圾回收</span><span class="sxs-lookup"><span data-stu-id="8e984-143">Background garbage collection</span></span>](background-gc.md)
- [<span data-ttu-id="8e984-144">用于垃圾回收的运行时配置选项</span><span class="sxs-lookup"><span data-stu-id="8e984-144">Run-time configuration options for garbage collection</span></span>](../../core/run-time-config/garbage-collector.md)

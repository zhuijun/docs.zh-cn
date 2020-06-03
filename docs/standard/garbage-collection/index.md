---
title: .NET 垃圾回收
ms.date: 04/21/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- memory, garbage collection
- garbage collection, automatic memory management
- GC [.NET Framework]
- memory, allocating
- common language runtime, garbage collection
- garbage collector
- cleanup operations
- garbage collection
- memory, releasing
- common language runtime, automatic memory management
- automatic memory management
- runtime, automatic memory management
- runtime, garbage collection
- garbage collection, about
ms.assetid: 22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9
ms.openlocfilehash: ef7e078c6ef2f0b4081c49aa0db09316e79f0702
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286049"
---
# <a name="garbage-collection"></a><span data-ttu-id="bb89b-102">垃圾回收</span><span class="sxs-lookup"><span data-stu-id="bb89b-102">Garbage collection</span></span>

<span data-ttu-id="bb89b-103">.NET 的垃圾回收器管理应用程序的内存分配和释放。</span><span class="sxs-lookup"><span data-stu-id="bb89b-103">.NET's garbage collector manages the allocation and release of memory for your application.</span></span> <span data-ttu-id="bb89b-104">每当有对象新建时，公共语言运行时都会从托管堆为对象分配内存。</span><span class="sxs-lookup"><span data-stu-id="bb89b-104">Each time you create a new object, the common language runtime allocates memory for the object from the managed heap.</span></span> <span data-ttu-id="bb89b-105">只要托管堆中有地址空间，运行时就会继续为新对象分配空间。</span><span class="sxs-lookup"><span data-stu-id="bb89b-105">As long as address space is available in the managed heap, the runtime continues to allocate space for new objects.</span></span> <span data-ttu-id="bb89b-106">不过，内存并不是无限的。</span><span class="sxs-lookup"><span data-stu-id="bb89b-106">However, memory is not infinite.</span></span> <span data-ttu-id="bb89b-107">垃圾回收器最终必须执行垃圾回收来释放一些内存。</span><span class="sxs-lookup"><span data-stu-id="bb89b-107">Eventually the garbage collector must perform a collection in order to free some memory.</span></span> <span data-ttu-id="bb89b-108">垃圾回收器的优化引擎会根据所执行的分配来确定执行回收的最佳时机。</span><span class="sxs-lookup"><span data-stu-id="bb89b-108">The garbage collector's optimizing engine determines the best time to perform a collection, based upon the allocations being made.</span></span> <span data-ttu-id="bb89b-109">执行回收时，垃圾回收器会在托管堆中检查应用程序不再使用的对象，然后执行必要的操作来回收其内存。</span><span class="sxs-lookup"><span data-stu-id="bb89b-109">When the garbage collector performs a collection, it checks for objects in the managed heap that are no longer being used by the application and performs the necessary operations to reclaim their memory.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bb89b-110">本节内容</span><span class="sxs-lookup"><span data-stu-id="bb89b-110">In this section</span></span>
  
|<span data-ttu-id="bb89b-111">Title</span><span class="sxs-lookup"><span data-stu-id="bb89b-111">Title</span></span>|<span data-ttu-id="bb89b-112">描述</span><span class="sxs-lookup"><span data-stu-id="bb89b-112">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="bb89b-113">垃圾回收的基本知识</span><span class="sxs-lookup"><span data-stu-id="bb89b-113">Fundamentals of garbage collection</span></span>](fundamentals.md)|<span data-ttu-id="bb89b-114">描述垃圾回收的工作原理、如何在托管堆上分配对象，以及其他核心概念。</span><span class="sxs-lookup"><span data-stu-id="bb89b-114">Describes how garbage collection works, how objects are allocated on the managed heap, and other core concepts.</span></span>|  
|[<span data-ttu-id="bb89b-115">工作站和服务器垃圾回收</span><span class="sxs-lookup"><span data-stu-id="bb89b-115">Workstation and server garbage collection</span></span>](workstation-server-gc.md)|<span data-ttu-id="bb89b-116">描述了客户端应用的工作站垃圾回收与服务器应用的服务器垃圾回收之间的区别。</span><span class="sxs-lookup"><span data-stu-id="bb89b-116">Describes the differences between workstation garbage collection for client apps and server garbage collection for server apps.</span></span>|
|[<span data-ttu-id="bb89b-117">后台垃圾回收</span><span class="sxs-lookup"><span data-stu-id="bb89b-117">Background garbage collection</span></span>](background-gc.md)|<span data-ttu-id="bb89b-118">描述了后台垃圾回收，它是在进行第二代回收时对第 0 代和第 1 代对象的回收。</span><span class="sxs-lookup"><span data-stu-id="bb89b-118">Describes background garbage collection, which is the collection of generation 0 and 1 objects while generation 2 collection is in progress.</span></span>|
|[<span data-ttu-id="bb89b-119">大型对象堆</span><span class="sxs-lookup"><span data-stu-id="bb89b-119">The large object heap</span></span>](large-object-heap.md)|<span data-ttu-id="bb89b-120">描述了大型对象堆 (LOH) 及其垃圾回收方式。</span><span class="sxs-lookup"><span data-stu-id="bb89b-120">Describes the large object heap (LOH) and how large objects are garbage-collected.</span></span>|
|[<span data-ttu-id="bb89b-121">垃圾回收和性能</span><span class="sxs-lookup"><span data-stu-id="bb89b-121">Garbage collection and performance</span></span>](performance.md)|<span data-ttu-id="bb89b-122">介绍了可用来诊断垃圾回收和性能问题的性能检查。</span><span class="sxs-lookup"><span data-stu-id="bb89b-122">Describes the performance checks you can use to diagnose garbage collection and performance issues.</span></span>|  
|[<span data-ttu-id="bb89b-123">已引发回收</span><span class="sxs-lookup"><span data-stu-id="bb89b-123">Induced collections</span></span>](induced.md)|<span data-ttu-id="bb89b-124">描述如何完成垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="bb89b-124">Describes how to make a garbage collection occur.</span></span>|  
|[<span data-ttu-id="bb89b-125">延迟模式</span><span class="sxs-lookup"><span data-stu-id="bb89b-125">Latency modes</span></span>](latency.md)|<span data-ttu-id="bb89b-126">描述确定垃圾回收侵入性的模式。</span><span class="sxs-lookup"><span data-stu-id="bb89b-126">Describes the modes that determine the intrusiveness of garbage collection.</span></span>|  
|[<span data-ttu-id="bb89b-127">针对共享 Web 承载优化</span><span class="sxs-lookup"><span data-stu-id="bb89b-127">Optimization for shared web hosting</span></span>](optimization-for-shared-web-hosting.md)|<span data-ttu-id="bb89b-128">介绍了如何在多个小网站共用的服务器上优化垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="bb89b-128">Describes how to optimize garbage collection on servers shared by several small Web sites.</span></span>|  
|[<span data-ttu-id="bb89b-129">垃圾回收通知</span><span class="sxs-lookup"><span data-stu-id="bb89b-129">Garbage collection notifications</span></span>](notifications.md)|<span data-ttu-id="bb89b-130">介绍了如何确定全面垃圾回收的开始时间和结束时间。</span><span class="sxs-lookup"><span data-stu-id="bb89b-130">Describes how to determine when a full garbage collection is approaching and when it has completed.</span></span>|  
|[<span data-ttu-id="bb89b-131">应用程序域资源监视</span><span class="sxs-lookup"><span data-stu-id="bb89b-131">Application domain resource monitoring</span></span>](app-domain-resource-monitoring.md)|<span data-ttu-id="bb89b-132">介绍了如何监视应用程序域的 CPU 和内存使用情况。</span><span class="sxs-lookup"><span data-stu-id="bb89b-132">Describes how to monitor CPU and memory usage by an application domain.</span></span>|  
|[<span data-ttu-id="bb89b-133">弱引用</span><span class="sxs-lookup"><span data-stu-id="bb89b-133">Weak references</span></span>](weak-references.md)|<span data-ttu-id="bb89b-134">描述允许应用程序访问对象的同时也允许垃圾回收器收集相应对象的功能。</span><span class="sxs-lookup"><span data-stu-id="bb89b-134">Describes features that permit the garbage collector to collect an object while still allowing the application to access that object.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="bb89b-135">参考</span><span class="sxs-lookup"><span data-stu-id="bb89b-135">Reference</span></span>

- <xref:System.GC?displayProperty=nameWithType>  
- <xref:System.GCCollectionMode?displayProperty=nameWithType>  
- <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
- <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="bb89b-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="bb89b-136">See also</span></span>

- [<span data-ttu-id="bb89b-137">清理非托管资源</span><span class="sxs-lookup"><span data-stu-id="bb89b-137">Clean up unmanaged resources</span></span>](unmanaged.md)

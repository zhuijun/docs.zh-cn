---
title: 滞后时间模式
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, intrusiveness
- garbage collection, latency modes
ms.assetid: 96278bb7-6eab-4612-8594-ceebfc887d81
ms.openlocfilehash: ee45fe5e8016c7507bc3a873e615fd8379810a8e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286010"
---
# <a name="latency-modes"></a><span data-ttu-id="ffdea-102">延迟模式</span><span class="sxs-lookup"><span data-stu-id="ffdea-102">Latency modes</span></span>

<span data-ttu-id="ffdea-103">若要回收对象，垃圾回收器 (GC) 必须停止应用程序中所有正在执行的线程。</span><span class="sxs-lookup"><span data-stu-id="ffdea-103">To reclaim objects, the garbage collector (GC) must stop all the executing threads in an application.</span></span> <span data-ttu-id="ffdea-104">垃圾回收器处于活动状态的时间段称为延迟  。</span><span class="sxs-lookup"><span data-stu-id="ffdea-104">The period of time during which the garbage collector is active is referred to as its *latency*.</span></span>

<span data-ttu-id="ffdea-105">在某些情况下（例如当应用程序检索数据或显示内容时），关键时刻可能发生完整的垃圾回收，从而妨碍性能。</span><span class="sxs-lookup"><span data-stu-id="ffdea-105">In some situations, such as when an application retrieves data or displays content, a full garbage collection can occur at a critical time and impede performance.</span></span> <span data-ttu-id="ffdea-106">可以通过将 <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> 属性设置为其中一个 <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> 值来调节垃圾回收的干扰。</span><span class="sxs-lookup"><span data-stu-id="ffdea-106">You can adjust the intrusiveness of the garbage collector by setting the <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> property to one of the <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> values.</span></span>

## <a name="low-latency-settings"></a><span data-ttu-id="ffdea-107">低延迟设置</span><span class="sxs-lookup"><span data-stu-id="ffdea-107">Low latency settings</span></span>

<span data-ttu-id="ffdea-108">使用“低”延迟设置意味着垃圾回收器对应用程序的干扰较少。</span><span class="sxs-lookup"><span data-stu-id="ffdea-108">Using a "low" latency setting means the garbage collector intrudes less in your application.</span></span> <span data-ttu-id="ffdea-109">垃圾回收在回收内存方面较为保守。</span><span class="sxs-lookup"><span data-stu-id="ffdea-109">Garbage collection is more conservative about reclaiming memory.</span></span>

<span data-ttu-id="ffdea-110"><xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> 枚举提供两种低延迟设置：</span><span class="sxs-lookup"><span data-stu-id="ffdea-110">The <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> enumeration provides two low latency settings:</span></span>

- <span data-ttu-id="ffdea-111">[GCLatencyMode.LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) 禁止第 2 代回收，仅执行第 0 代和第 1 代回收。</span><span class="sxs-lookup"><span data-stu-id="ffdea-111">[GCLatencyMode.LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) suppresses generation 2 collections and performs only generation 0 and 1 collections.</span></span> <span data-ttu-id="ffdea-112">只能在短时间内使用。</span><span class="sxs-lookup"><span data-stu-id="ffdea-112">It can be used only for short periods of time.</span></span> <span data-ttu-id="ffdea-113">在更长时间内，如果系统处于内存压力下，垃圾回收器将触发一次回收，这样会暂时暂停应用程序并中断对时间要求很急的操作。</span><span class="sxs-lookup"><span data-stu-id="ffdea-113">Over longer periods, if the system is under memory pressure, the garbage collector will trigger a collection, which can briefly pause the application and disrupt a time-critical operation.</span></span> <span data-ttu-id="ffdea-114">此设置仅对工作站垃圾回收可用。</span><span class="sxs-lookup"><span data-stu-id="ffdea-114">This setting is available only for workstation garbage collection.</span></span>

- <span data-ttu-id="ffdea-115">[GCLatencyMode.SustainedLowLatency](xref:System.Runtime.GCLatencyMode.SustainedLowLatency) 禁止第 2 代前台回收，仅执行第 0 代、第 1 代回收和第 2 代后台回收。</span><span class="sxs-lookup"><span data-stu-id="ffdea-115">[GCLatencyMode.SustainedLowLatency](xref:System.Runtime.GCLatencyMode.SustainedLowLatency) suppresses foreground generation 2 collections and performs only generation 0, 1, and background generation 2 collections.</span></span> <span data-ttu-id="ffdea-116">它可以长时间使用，并对工作站和服务器垃圾回收都可用。</span><span class="sxs-lookup"><span data-stu-id="ffdea-116">It can be used for longer periods of time, and is available for both workstation and server garbage collection.</span></span> <span data-ttu-id="ffdea-117">如果后台垃圾回收已禁用，则无法使用此设置。</span><span class="sxs-lookup"><span data-stu-id="ffdea-117">This setting cannot be used if background garbage collection is disabled.</span></span>

<span data-ttu-id="ffdea-118">在低延迟期间，除非发生以下情况，否则禁止第 2 代回收：</span><span class="sxs-lookup"><span data-stu-id="ffdea-118">During low latency periods, generation 2 collections are suppressed unless the following occurs:</span></span>

- <span data-ttu-id="ffdea-119">系统收到操作系统的低内存通知。</span><span class="sxs-lookup"><span data-stu-id="ffdea-119">The system receives a low memory notification from the operating system.</span></span>

- <span data-ttu-id="ffdea-120">应用程序代码通过调用 <xref:System.GC.Collect%2A?displayProperty=nameWithType> 方法并将 `generation` 参数指定为 2 来包含回收。</span><span class="sxs-lookup"><span data-stu-id="ffdea-120">Application code induces a collection by calling the <xref:System.GC.Collect%2A?displayProperty=nameWithType> method and specifying 2 for the `generation` parameter.</span></span>

## <a name="scenarios"></a><span data-ttu-id="ffdea-121">方案</span><span class="sxs-lookup"><span data-stu-id="ffdea-121">Scenarios</span></span>

<span data-ttu-id="ffdea-122">下表列出了使用 <xref:System.Runtime.GCLatencyMode> 值的应用程序方案：</span><span class="sxs-lookup"><span data-stu-id="ffdea-122">The following table lists the application scenarios for using the <xref:System.Runtime.GCLatencyMode> values:</span></span>

|<span data-ttu-id="ffdea-123">延迟模式</span><span class="sxs-lookup"><span data-stu-id="ffdea-123">Latency mode</span></span>|<span data-ttu-id="ffdea-124">应用程序方案</span><span class="sxs-lookup"><span data-stu-id="ffdea-124">Application scenarios</span></span>|
|------------------|---------------------------|
|<xref:System.Runtime.GCLatencyMode.Batch>|<span data-ttu-id="ffdea-125">对于不具有用户界面 (UI) 或服务器端操作的应用程序。</span><span class="sxs-lookup"><span data-stu-id="ffdea-125">For applications that have no user interface (UI) or server-side operations.</span></span><br /><br /><span data-ttu-id="ffdea-126">禁用后台垃圾回收后，这将是工作站和服务器垃圾回收的默认模式。</span><span class="sxs-lookup"><span data-stu-id="ffdea-126">When background garbage collection is disabled, this is the default mode for workstation and server garbage collection.</span></span> <span data-ttu-id="ffdea-127"><xref:System.Runtime.GCLatencyMode.Batch> 模式还会替代 [gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) 设置，即它会阻止后台或并发回收。</span><span class="sxs-lookup"><span data-stu-id="ffdea-127"><xref:System.Runtime.GCLatencyMode.Batch> mode also overrides the [gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) setting, that is, it prevents background or concurrent collections.</span></span>|
|<xref:System.Runtime.GCLatencyMode.Interactive>|<span data-ttu-id="ffdea-128">对于具有 UI 的大多数应用程序。</span><span class="sxs-lookup"><span data-stu-id="ffdea-128">For most applications that have a UI.</span></span><br /><br /><span data-ttu-id="ffdea-129">这是工作站和服务器垃圾回收的默认模式。</span><span class="sxs-lookup"><span data-stu-id="ffdea-129">This is the default mode for workstation and server garbage collection.</span></span> <span data-ttu-id="ffdea-130">但是，如果托管了某个应用，则优先考虑托管进程的垃圾回收器设置。</span><span class="sxs-lookup"><span data-stu-id="ffdea-130">However, if an app is hosted, the garbage collector settings of the hosting process take precedence.</span></span>|
|<xref:System.Runtime.GCLatencyMode.LowLatency>|<span data-ttu-id="ffdea-131">对于具有短期时效性操作（操作期间垃圾回收器的干扰可能会引起中断）的应用程序。</span><span class="sxs-lookup"><span data-stu-id="ffdea-131">For applications that have short-term, time-sensitive operations during which interruptions from the garbage collector could be disruptive.</span></span> <span data-ttu-id="ffdea-132">例如，呈现动画或数据采集功能的应用程序。</span><span class="sxs-lookup"><span data-stu-id="ffdea-132">For example, applications that render animations or data acquisition functions.</span></span>|
|<xref:System.Runtime.GCLatencyMode.SustainedLowLatency>|<span data-ttu-id="ffdea-133">适用于在有限但有可能更长的时间内具有时效性操作并且在此期间垃圾回收器中断具有破环性的应用程序。</span><span class="sxs-lookup"><span data-stu-id="ffdea-133">For applications that have time-sensitive operations for a contained but potentially longer duration of time during which interruptions from the garbage collector could be disruptive.</span></span> <span data-ttu-id="ffdea-134">例如，需要随着交易时间内的市场数据变化做出快速响应的应用程序。</span><span class="sxs-lookup"><span data-stu-id="ffdea-134">For example, applications that need quick response times as market data changes during trading hours.</span></span><br /><br /><span data-ttu-id="ffdea-135">此模式会比其他模式产生更大的托管堆大小。</span><span class="sxs-lookup"><span data-stu-id="ffdea-135">This mode results in a larger managed heap size than other modes.</span></span> <span data-ttu-id="ffdea-136">由于它不压缩托管堆，因此可能产生更多碎片。</span><span class="sxs-lookup"><span data-stu-id="ffdea-136">Because it does not compact the managed heap, higher fragmentation is possible.</span></span> <span data-ttu-id="ffdea-137">确保有足够的可用内存。</span><span class="sxs-lookup"><span data-stu-id="ffdea-137">Ensure that sufficient memory is available.</span></span>|

## <a name="guidelines-for-using-low-latency"></a><span data-ttu-id="ffdea-138">低延迟使用指南</span><span class="sxs-lookup"><span data-stu-id="ffdea-138">Guidelines for using low latency</span></span>

<span data-ttu-id="ffdea-139">使用 [GCLatencyMode.LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) 模式时，请注意以下指导原则：</span><span class="sxs-lookup"><span data-stu-id="ffdea-139">When you use [GCLatencyMode.LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) mode, consider the following guidelines:</span></span>

- <span data-ttu-id="ffdea-140">尽可能地缩短低延迟时段。</span><span class="sxs-lookup"><span data-stu-id="ffdea-140">Keep the period of time in low latency as short as possible.</span></span>

- <span data-ttu-id="ffdea-141">避免在低延迟时段分配大量内存。</span><span class="sxs-lookup"><span data-stu-id="ffdea-141">Avoid allocating high amounts of memory during low latency periods.</span></span> <span data-ttu-id="ffdea-142">由于垃圾回收回收的对象较少可能出现低内存通知。</span><span class="sxs-lookup"><span data-stu-id="ffdea-142">Low memory notifications can occur because garbage collection reclaims fewer objects.</span></span>

- <span data-ttu-id="ffdea-143">在低延迟模式下，最大限度减少新的分配次数，尤其是分配到大型对象堆和固定对象的次数。</span><span class="sxs-lookup"><span data-stu-id="ffdea-143">While in the low latency mode, minimize the number of new allocations, in particular allocations onto the large object heap and pinned objects.</span></span>

- <span data-ttu-id="ffdea-144">知道可以分配的线程。</span><span class="sxs-lookup"><span data-stu-id="ffdea-144">Be aware of threads that could be allocating.</span></span> <span data-ttu-id="ffdea-145">由于 <xref:System.Runtime.GCSettings.LatencyMode%2A> 属性设置属于进程范围的设置，因此可以在分配的任何线程上生成 <xref:System.OutOfMemoryException> 异常。</span><span class="sxs-lookup"><span data-stu-id="ffdea-145">Because the <xref:System.Runtime.GCSettings.LatencyMode%2A> property setting is process-wide, <xref:System.OutOfMemoryException> exceptions can be generated on any thread that is allocating.</span></span>

- <span data-ttu-id="ffdea-146">将低延迟代码包装在受约束的执行区域中。</span><span class="sxs-lookup"><span data-stu-id="ffdea-146">Wrap the low latency code in constrained execution regions.</span></span> <span data-ttu-id="ffdea-147">有关详细信息，请参阅[受约束的执行区域](../../framework/performance/constrained-execution-regions.md)。</span><span class="sxs-lookup"><span data-stu-id="ffdea-147">For more information, see [Constrained execution regions](../../framework/performance/constrained-execution-regions.md).</span></span>

- <span data-ttu-id="ffdea-148">在低延迟期间，可以通过调用 <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType> 方法强制进行第 2 代回收。</span><span class="sxs-lookup"><span data-stu-id="ffdea-148">You can force generation 2 collections during a low latency period by calling the <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType> method.</span></span>

## <a name="see-also"></a><span data-ttu-id="ffdea-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ffdea-149">See also</span></span>

- <xref:System.GC?displayProperty=nameWithType>
- [<span data-ttu-id="ffdea-150">已引发回收</span><span class="sxs-lookup"><span data-stu-id="ffdea-150">Induced Collections</span></span>](induced.md)
- [<span data-ttu-id="ffdea-151">垃圾回收</span><span class="sxs-lookup"><span data-stu-id="ffdea-151">Garbage Collection</span></span>](index.md)

---
title: 垃圾回收 ETW 事件
description: 查看有关垃圾回收 ETW 事件的详细信息。 涉及的事件包括 GCStart_V1、GCEnd_V1、GCHeapStats_V1、GCCreateSegment_V1 等。
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
ms.openlocfilehash: 2e1e0fda5c1a80627c8dde7f49954a867b9a2b66
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720132"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="e108e-104">垃圾回收 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-104">Garbage Collection ETW Events</span></span>

<span data-ttu-id="e108e-105">这些事件可收集有关垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="e108e-105">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="e108e-106">它们可帮助进行诊断和调试，包括确定垃圾回收执行的次数、垃圾回收期间释放的内存量等。</span><span class="sxs-lookup"><span data-stu-id="e108e-106">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>

<span data-ttu-id="e108e-107">此类别包含以下事件：</span><span class="sxs-lookup"><span data-stu-id="e108e-107">This category consists of the following events:</span></span>

- [<span data-ttu-id="e108e-108">GCStart_V1 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-108">GCStart_V1 Event</span></span>](#gcstart_v1-event)
- [<span data-ttu-id="e108e-109">GCEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-109">GCEnd_V1 Event</span></span>](#gcend_v1-event)
- [<span data-ttu-id="e108e-110">GCHeapStats_V1 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-110">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1-event)
- [<span data-ttu-id="e108e-111">GCHeapStats_V2 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-111">GCHeapStats_V2 Event</span></span>](#gcheapstats_v2-event)
- [<span data-ttu-id="e108e-112">GCCreateSegment_V1 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-112">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1-event)
- [<span data-ttu-id="e108e-113">GCFreeSegment_V1 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-113">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1-event)
- [<span data-ttu-id="e108e-114">GCRestartEEBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-114">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1-event)
- [<span data-ttu-id="e108e-115">GCRestartEEEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-115">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1-event)
- [<span data-ttu-id="e108e-116">GCSuspendEE_V1 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-116">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1-event)
- [<span data-ttu-id="e108e-117">GCSuspendEEEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-117">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1-event)
- [<span data-ttu-id="e108e-118">GCAllocationTick_V2 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-118">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2-event)
- [<span data-ttu-id="e108e-119">GCAllocationTick_V3 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-119">GCAllocationTick_V3 Event</span></span>](#gcallocationtick_v3-event)
- [<span data-ttu-id="e108e-120">GCFinalizersBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-120">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1-event)
- [<span data-ttu-id="e108e-121">GCFinalizersEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-121">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1-event)
- [<span data-ttu-id="e108e-122">GCCreateConcurrentThread_V1 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-122">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1-event)
- [<span data-ttu-id="e108e-123">GCTerminateConcurrentThread_V1 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-123">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1-event)

## <a name="gcstart_v1-event"></a><span data-ttu-id="e108e-124">GCStart_V1 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-124">GCStart_V1 Event</span></span>  

<span data-ttu-id="e108e-125">下表显示了关键字和级别。</span><span class="sxs-lookup"><span data-stu-id="e108e-125">The following table shows the keyword and level.</span></span> <span data-ttu-id="e108e-126">有关详细信息，请参阅 [CLR ETW 关键字和级别](clr-etw-keywords-and-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="e108e-126">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="e108e-127">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="e108e-127">Keyword for raising the event</span></span>|<span data-ttu-id="e108e-128">级别</span><span class="sxs-lookup"><span data-stu-id="e108e-128">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e108e-129">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="e108e-129">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="e108e-130">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="e108e-130">Informational (4)</span></span>|

<span data-ttu-id="e108e-131">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="e108e-131">The following table shows the event information:</span></span>

|<span data-ttu-id="e108e-132">事件</span><span class="sxs-lookup"><span data-stu-id="e108e-132">Event</span></span>|<span data-ttu-id="e108e-133">事件 ID</span><span class="sxs-lookup"><span data-stu-id="e108e-133">Event ID</span></span>|<span data-ttu-id="e108e-134">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="e108e-134">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCStart_V1`|<span data-ttu-id="e108e-135">1</span><span class="sxs-lookup"><span data-stu-id="e108e-135">1</span></span>|<span data-ttu-id="e108e-136">垃圾回收已启动。</span><span class="sxs-lookup"><span data-stu-id="e108e-136">A garbage collection has started.</span></span>|

<span data-ttu-id="e108e-137">下表显示了事件数据：</span><span class="sxs-lookup"><span data-stu-id="e108e-137">The following table shows the event data:</span></span>

|<span data-ttu-id="e108e-138">字段名称</span><span class="sxs-lookup"><span data-stu-id="e108e-138">Field name</span></span>|<span data-ttu-id="e108e-139">数据类型</span><span class="sxs-lookup"><span data-stu-id="e108e-139">Data type</span></span>|<span data-ttu-id="e108e-140">说明</span><span class="sxs-lookup"><span data-stu-id="e108e-140">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="e108e-141">计数</span><span class="sxs-lookup"><span data-stu-id="e108e-141">Count</span></span>|<span data-ttu-id="e108e-142">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e108e-142">win:UInt32</span></span>|<span data-ttu-id="e108e-143">第 *n*代垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="e108e-143">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="e108e-144">深度</span><span class="sxs-lookup"><span data-stu-id="e108e-144">Depth</span></span>|<span data-ttu-id="e108e-145">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e108e-145">win:UInt32</span></span>|<span data-ttu-id="e108e-146">正在回收的代。</span><span class="sxs-lookup"><span data-stu-id="e108e-146">The generation that is being collected.</span></span>|
|<span data-ttu-id="e108e-147">原因</span><span class="sxs-lookup"><span data-stu-id="e108e-147">Reason</span></span>|<span data-ttu-id="e108e-148">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e108e-148">win:UInt32</span></span>|<span data-ttu-id="e108e-149">垃圾回收的触发原因：</span><span class="sxs-lookup"><span data-stu-id="e108e-149">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="e108e-150">0x0 - 小型对象堆分配。</span><span class="sxs-lookup"><span data-stu-id="e108e-150">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="e108e-151">0x1 - 已引发。</span><span class="sxs-lookup"><span data-stu-id="e108e-151">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="e108e-152">0x2 - 内存不足。</span><span class="sxs-lookup"><span data-stu-id="e108e-152">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="e108e-153">0x3 - 空。</span><span class="sxs-lookup"><span data-stu-id="e108e-153">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="e108e-154">0x4 - 大型对象堆分配。</span><span class="sxs-lookup"><span data-stu-id="e108e-154">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="e108e-155">0x5 - 空间不足（针对小型对象堆）。</span><span class="sxs-lookup"><span data-stu-id="e108e-155">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="e108e-156">0x6 - 空间不足（针对大型对象堆）。</span><span class="sxs-lookup"><span data-stu-id="e108e-156">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="e108e-157">0x7 - 已引发，但未强制为阻止。</span><span class="sxs-lookup"><span data-stu-id="e108e-157">0x7 - Induced but not forced as blocking.</span></span>|
|<span data-ttu-id="e108e-158">类型</span><span class="sxs-lookup"><span data-stu-id="e108e-158">Type</span></span>|<span data-ttu-id="e108e-159">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e108e-159">win:UInt32</span></span>|<span data-ttu-id="e108e-160">0x0 - 在后台垃圾回收外部发生了垃圾回收阻止。</span><span class="sxs-lookup"><span data-stu-id="e108e-160">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="e108e-161">0x1 - 后台垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="e108e-161">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="e108e-162">0x0 - 后台垃圾回收期间发生了垃圾回收阻止。</span><span class="sxs-lookup"><span data-stu-id="e108e-162">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|
|<span data-ttu-id="e108e-163">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e108e-163">ClrInstanceID</span></span>|<span data-ttu-id="e108e-164">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e108e-164">win:UInt16</span></span>|<span data-ttu-id="e108e-165">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="e108e-165">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcend_v1-event"></a><span data-ttu-id="e108e-166">GCEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-166">GCEnd_V1 Event</span></span>

<span data-ttu-id="e108e-167">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="e108e-167">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="e108e-168">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="e108e-168">Keyword for raising the event</span></span>|<span data-ttu-id="e108e-169">级别</span><span class="sxs-lookup"><span data-stu-id="e108e-169">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e108e-170">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="e108e-170">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="e108e-171">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="e108e-171">Informational (4)</span></span>|

<span data-ttu-id="e108e-172">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="e108e-172">The following table shows the event information:</span></span>

|<span data-ttu-id="e108e-173">事件</span><span class="sxs-lookup"><span data-stu-id="e108e-173">Event</span></span>|<span data-ttu-id="e108e-174">事件 ID</span><span class="sxs-lookup"><span data-stu-id="e108e-174">Event ID</span></span>|<span data-ttu-id="e108e-175">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="e108e-175">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCEnd_V1`|<span data-ttu-id="e108e-176">2</span><span class="sxs-lookup"><span data-stu-id="e108e-176">2</span></span>|<span data-ttu-id="e108e-177">垃圾回收已结束。</span><span class="sxs-lookup"><span data-stu-id="e108e-177">The garbage collection has ended.</span></span>|

<span data-ttu-id="e108e-178">下表显示了事件数据：</span><span class="sxs-lookup"><span data-stu-id="e108e-178">The following table shows the event data:</span></span>

|<span data-ttu-id="e108e-179">字段名称</span><span class="sxs-lookup"><span data-stu-id="e108e-179">Field name</span></span>|<span data-ttu-id="e108e-180">数据类型</span><span class="sxs-lookup"><span data-stu-id="e108e-180">Data type</span></span>|<span data-ttu-id="e108e-181">说明</span><span class="sxs-lookup"><span data-stu-id="e108e-181">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="e108e-182">计数</span><span class="sxs-lookup"><span data-stu-id="e108e-182">Count</span></span>|<span data-ttu-id="e108e-183">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e108e-183">win:UInt32</span></span>|<span data-ttu-id="e108e-184">第 *n*代垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="e108e-184">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="e108e-185">深度</span><span class="sxs-lookup"><span data-stu-id="e108e-185">Depth</span></span>|<span data-ttu-id="e108e-186">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e108e-186">win:UInt32</span></span>|<span data-ttu-id="e108e-187">已回收的代。</span><span class="sxs-lookup"><span data-stu-id="e108e-187">The generation that was collected.</span></span>|
|<span data-ttu-id="e108e-188">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e108e-188">ClrInstanceID</span></span>|<span data-ttu-id="e108e-189">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e108e-189">win:UInt16</span></span>|<span data-ttu-id="e108e-190">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="e108e-190">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcheapstats_v1-event"></a><span data-ttu-id="e108e-191">GCHeapStats_V1 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-191">GCHeapStats_V1 Event</span></span>

<span data-ttu-id="e108e-192">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="e108e-192">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="e108e-193">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="e108e-193">Keyword for raising the event</span></span>|<span data-ttu-id="e108e-194">级别</span><span class="sxs-lookup"><span data-stu-id="e108e-194">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e108e-195">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="e108e-195">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="e108e-196">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="e108e-196">Informational (4)</span></span>|

<span data-ttu-id="e108e-197">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="e108e-197">The following table shows the event information:</span></span>

|<span data-ttu-id="e108e-198">事件</span><span class="sxs-lookup"><span data-stu-id="e108e-198">Event</span></span>|<span data-ttu-id="e108e-199">事件 ID</span><span class="sxs-lookup"><span data-stu-id="e108e-199">Event ID</span></span>|<span data-ttu-id="e108e-200">说明</span><span class="sxs-lookup"><span data-stu-id="e108e-200">Description</span></span>|
|-----------|--------------|-----------------|
|`GCHeapStats_V1`|<span data-ttu-id="e108e-201">4</span><span class="sxs-lookup"><span data-stu-id="e108e-201">4</span></span>|<span data-ttu-id="e108e-202">在每次垃圾回收结束时显示堆统计信息。</span><span class="sxs-lookup"><span data-stu-id="e108e-202">Shows the heap statistics at the end of each garbage collection.</span></span>|

<span data-ttu-id="e108e-203">下表显示了事件数据：</span><span class="sxs-lookup"><span data-stu-id="e108e-203">The following table shows the event data:</span></span>

|<span data-ttu-id="e108e-204">字段名称</span><span class="sxs-lookup"><span data-stu-id="e108e-204">Field name</span></span>|<span data-ttu-id="e108e-205">数据类型</span><span class="sxs-lookup"><span data-stu-id="e108e-205">Data type</span></span>|<span data-ttu-id="e108e-206">说明</span><span class="sxs-lookup"><span data-stu-id="e108e-206">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="e108e-207">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="e108e-207">GenerationSize0</span></span>|<span data-ttu-id="e108e-208">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e108e-208">win:UInt64</span></span>|<span data-ttu-id="e108e-209">第 0 代内存的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="e108e-209">The size, in bytes, of generation 0 memory.</span></span>|
|<span data-ttu-id="e108e-210">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="e108e-210">TotalPromotedSize0</span></span>|<span data-ttu-id="e108e-211">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e108e-211">win:UInt64</span></span>|<span data-ttu-id="e108e-212">从第 0 代提升到第 1 代的字节数。</span><span class="sxs-lookup"><span data-stu-id="e108e-212">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|
|<span data-ttu-id="e108e-213">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="e108e-213">GenerationSize1</span></span>|<span data-ttu-id="e108e-214">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e108e-214">win:UInt64</span></span>|<span data-ttu-id="e108e-215">第 1 代内存的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="e108e-215">The size, in bytes, of generation 1 memory.</span></span>|
|<span data-ttu-id="e108e-216">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="e108e-216">TotalPromotedSize1</span></span>|<span data-ttu-id="e108e-217">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e108e-217">win:UInt64</span></span>|<span data-ttu-id="e108e-218">从第 1 代提升到第 2 代的字节数。</span><span class="sxs-lookup"><span data-stu-id="e108e-218">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|
|<span data-ttu-id="e108e-219">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="e108e-219">GenerationSize2</span></span>|<span data-ttu-id="e108e-220">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e108e-220">win:UInt64</span></span>|<span data-ttu-id="e108e-221">第 2 代内存的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="e108e-221">The size, in bytes, of generation 2 memory.</span></span>|
|<span data-ttu-id="e108e-222">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="e108e-222">TotalPromotedSize2</span></span>|<span data-ttu-id="e108e-223">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e108e-223">win:UInt64</span></span>|<span data-ttu-id="e108e-224">上次回收后仍存在于第 2 代中的字节数。</span><span class="sxs-lookup"><span data-stu-id="e108e-224">The number of bytes that survived in generation 2 after the last collection.</span></span>|
|<span data-ttu-id="e108e-225">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="e108e-225">GenerationSize3</span></span>|<span data-ttu-id="e108e-226">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e108e-226">win:UInt64</span></span>|<span data-ttu-id="e108e-227">大型对象堆的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="e108e-227">The size, in bytes, of the large object heap.</span></span>|
|<span data-ttu-id="e108e-228">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="e108e-228">TotalPromotedSize3</span></span>|<span data-ttu-id="e108e-229">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e108e-229">win:UInt64</span></span>|<span data-ttu-id="e108e-230">上次回收后仍存在于大型对象堆中的字节数。</span><span class="sxs-lookup"><span data-stu-id="e108e-230">The number of bytes that survived in the large object heap after the last collection.</span></span>|
|<span data-ttu-id="e108e-231">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="e108e-231">FinalizationPromotedSize</span></span>|<span data-ttu-id="e108e-232">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e108e-232">win:UInt64</span></span>|<span data-ttu-id="e108e-233">准备终结的对象的总大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="e108e-233">The total size, in bytes, of the objects that are ready for finalization.</span></span>|
|<span data-ttu-id="e108e-234">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="e108e-234">FinalizationPromotedCount</span></span>|<span data-ttu-id="e108e-235">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e108e-235">win:UInt64</span></span>|<span data-ttu-id="e108e-236">已准备好进行终结的对象的数目。</span><span class="sxs-lookup"><span data-stu-id="e108e-236">The number of objects that are ready for finalization.</span></span>|
|<span data-ttu-id="e108e-237">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="e108e-237">PinnedObjectCount</span></span>|<span data-ttu-id="e108e-238">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e108e-238">win:UInt32</span></span>|<span data-ttu-id="e108e-239">固定（不可移动）对象的数目。</span><span class="sxs-lookup"><span data-stu-id="e108e-239">The number of pinned (unmovable) objects.</span></span>|
|<span data-ttu-id="e108e-240">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="e108e-240">SinkBlockCount</span></span>|<span data-ttu-id="e108e-241">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e108e-241">win:UInt32</span></span>|<span data-ttu-id="e108e-242">正在使用的同步块的数目。</span><span class="sxs-lookup"><span data-stu-id="e108e-242">The number of synchronization blocks in use.</span></span>|
|<span data-ttu-id="e108e-243">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="e108e-243">GCHandleCount</span></span>|<span data-ttu-id="e108e-244">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e108e-244">win:UInt32</span></span>|<span data-ttu-id="e108e-245">使用中的垃圾回收句柄的数目。</span><span class="sxs-lookup"><span data-stu-id="e108e-245">The number of garbage collection handles in use.</span></span>|
|<span data-ttu-id="e108e-246">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e108e-246">ClrInstanceID</span></span>|<span data-ttu-id="e108e-247">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e108e-247">win:UInt16</span></span>|<span data-ttu-id="e108e-248">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="e108e-248">Unique ID for the instance of CLR or CoreCLR.</span></span>|
  
## <a name="gcheapstats_v2-event"></a><span data-ttu-id="e108e-249">GCHeapStats_V2 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-249">GCHeapStats_V2 Event</span></span>

<span data-ttu-id="e108e-250">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="e108e-250">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="e108e-251">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="e108e-251">Keyword for raising the event</span></span>|<span data-ttu-id="e108e-252">级别</span><span class="sxs-lookup"><span data-stu-id="e108e-252">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e108e-253">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="e108e-253">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="e108e-254">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="e108e-254">Informational (4)</span></span>|

<span data-ttu-id="e108e-255">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="e108e-255">The following table shows the event information:</span></span>

|<span data-ttu-id="e108e-256">事件</span><span class="sxs-lookup"><span data-stu-id="e108e-256">Event</span></span>|<span data-ttu-id="e108e-257">事件 ID</span><span class="sxs-lookup"><span data-stu-id="e108e-257">Event ID</span></span>|<span data-ttu-id="e108e-258">说明</span><span class="sxs-lookup"><span data-stu-id="e108e-258">Description</span></span>|
|-----------|--------------|-----------------|
|`GCHeapStats_V2`|<span data-ttu-id="e108e-259">4</span><span class="sxs-lookup"><span data-stu-id="e108e-259">4</span></span>|<span data-ttu-id="e108e-260">在每次垃圾回收结束时显示堆统计信息。</span><span class="sxs-lookup"><span data-stu-id="e108e-260">Shows the heap statistics at the end of each garbage collection.</span></span>|

<span data-ttu-id="e108e-261">下表显示了事件数据：</span><span class="sxs-lookup"><span data-stu-id="e108e-261">The following table shows the event data:</span></span>

|<span data-ttu-id="e108e-262">字段名称</span><span class="sxs-lookup"><span data-stu-id="e108e-262">Field name</span></span>|<span data-ttu-id="e108e-263">数据类型</span><span class="sxs-lookup"><span data-stu-id="e108e-263">Data type</span></span>|<span data-ttu-id="e108e-264">说明</span><span class="sxs-lookup"><span data-stu-id="e108e-264">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="e108e-265">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="e108e-265">GenerationSize0</span></span>|<span data-ttu-id="e108e-266">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e108e-266">win:UInt64</span></span>|<span data-ttu-id="e108e-267">第 0 代内存的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="e108e-267">The size, in bytes, of generation 0 memory.</span></span>|
|<span data-ttu-id="e108e-268">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="e108e-268">TotalPromotedSize0</span></span>|<span data-ttu-id="e108e-269">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e108e-269">win:UInt64</span></span>|<span data-ttu-id="e108e-270">从第 0 代提升到第 1 代的字节数。</span><span class="sxs-lookup"><span data-stu-id="e108e-270">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|
|<span data-ttu-id="e108e-271">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="e108e-271">GenerationSize1</span></span>|<span data-ttu-id="e108e-272">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e108e-272">win:UInt64</span></span>|<span data-ttu-id="e108e-273">第 1 代内存的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="e108e-273">The size, in bytes, of generation 1 memory.</span></span>|
|<span data-ttu-id="e108e-274">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="e108e-274">TotalPromotedSize1</span></span>|<span data-ttu-id="e108e-275">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e108e-275">win:UInt64</span></span>|<span data-ttu-id="e108e-276">从第 1 代提升到第 2 代的字节数。</span><span class="sxs-lookup"><span data-stu-id="e108e-276">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|
|<span data-ttu-id="e108e-277">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="e108e-277">GenerationSize2</span></span>|<span data-ttu-id="e108e-278">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e108e-278">win:UInt64</span></span>|<span data-ttu-id="e108e-279">第 2 代内存的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="e108e-279">The size, in bytes, of generation 2 memory.</span></span>|
|<span data-ttu-id="e108e-280">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="e108e-280">TotalPromotedSize2</span></span>|<span data-ttu-id="e108e-281">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e108e-281">win:UInt64</span></span>|<span data-ttu-id="e108e-282">上次回收后仍存在于第 2 代中的字节数。</span><span class="sxs-lookup"><span data-stu-id="e108e-282">The number of bytes that survived in generation 2 after the last collection.</span></span>|
|<span data-ttu-id="e108e-283">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="e108e-283">GenerationSize3</span></span>|<span data-ttu-id="e108e-284">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e108e-284">win:UInt64</span></span>|<span data-ttu-id="e108e-285">大型对象堆的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="e108e-285">The size, in bytes, of the large object heap.</span></span>|
|<span data-ttu-id="e108e-286">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="e108e-286">TotalPromotedSize3</span></span>|<span data-ttu-id="e108e-287">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e108e-287">win:UInt64</span></span>|<span data-ttu-id="e108e-288">上次回收后仍存在于大型对象堆中的字节数。</span><span class="sxs-lookup"><span data-stu-id="e108e-288">The number of bytes that survived in the large object heap after the last collection.</span></span>|
|<span data-ttu-id="e108e-289">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="e108e-289">FinalizationPromotedSize</span></span>|<span data-ttu-id="e108e-290">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e108e-290">win:UInt64</span></span>|<span data-ttu-id="e108e-291">准备终结的对象的总大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="e108e-291">The total size, in bytes, of the objects that are ready for finalization.</span></span>|
|<span data-ttu-id="e108e-292">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="e108e-292">FinalizationPromotedCount</span></span>|<span data-ttu-id="e108e-293">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e108e-293">win:UInt64</span></span>|<span data-ttu-id="e108e-294">已准备好进行终结的对象的数目。</span><span class="sxs-lookup"><span data-stu-id="e108e-294">The number of objects that are ready for finalization.</span></span>|
|<span data-ttu-id="e108e-295">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="e108e-295">PinnedObjectCount</span></span>|<span data-ttu-id="e108e-296">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e108e-296">win:UInt32</span></span>|<span data-ttu-id="e108e-297">固定（不可移动）对象的数目。</span><span class="sxs-lookup"><span data-stu-id="e108e-297">The number of pinned (unmovable) objects.</span></span>|
|<span data-ttu-id="e108e-298">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="e108e-298">SinkBlockCount</span></span>|<span data-ttu-id="e108e-299">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e108e-299">win:UInt32</span></span>|<span data-ttu-id="e108e-300">正在使用的同步块的数目。</span><span class="sxs-lookup"><span data-stu-id="e108e-300">The number of synchronization blocks in use.</span></span>|
|<span data-ttu-id="e108e-301">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="e108e-301">GCHandleCount</span></span>|<span data-ttu-id="e108e-302">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e108e-302">win:UInt32</span></span>|<span data-ttu-id="e108e-303">使用中的垃圾回收句柄的数目。</span><span class="sxs-lookup"><span data-stu-id="e108e-303">The number of garbage collection handles in use.</span></span>|
|<span data-ttu-id="e108e-304">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e108e-304">ClrInstanceID</span></span>|<span data-ttu-id="e108e-305">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e108e-305">win:UInt16</span></span>|<span data-ttu-id="e108e-306">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="e108e-306">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|<span data-ttu-id="e108e-307">GenerationSize4</span><span class="sxs-lookup"><span data-stu-id="e108e-307">GenerationSize4</span></span>|<span data-ttu-id="e108e-308">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e108e-308">win:UInt64</span></span>|<span data-ttu-id="e108e-309">固定对象堆的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="e108e-309">The size, in bytes, of the pinned object heap.</span></span>|
|<span data-ttu-id="e108e-310">TotalPromotedSize4</span><span class="sxs-lookup"><span data-stu-id="e108e-310">TotalPromotedSize4</span></span>|<span data-ttu-id="e108e-311">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e108e-311">win:UInt64</span></span>|<span data-ttu-id="e108e-312">上次回收后保留在固定对象堆中的字节数。</span><span class="sxs-lookup"><span data-stu-id="e108e-312">The number of bytes that survived in the pinned object heap after the last collection.</span></span>|
  
## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="e108e-313">GCCreateSegment_V1 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-313">GCCreateSegment_V1 Event</span></span>

<span data-ttu-id="e108e-314">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="e108e-314">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="e108e-315">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="e108e-315">Keyword for raising the event</span></span>|<span data-ttu-id="e108e-316">级别</span><span class="sxs-lookup"><span data-stu-id="e108e-316">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e108e-317">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="e108e-317">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="e108e-318">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="e108e-318">Informational (4)</span></span>|

<span data-ttu-id="e108e-319">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="e108e-319">The following table shows the event information:</span></span>

|<span data-ttu-id="e108e-320">事件</span><span class="sxs-lookup"><span data-stu-id="e108e-320">Event</span></span>|<span data-ttu-id="e108e-321">事件 ID</span><span class="sxs-lookup"><span data-stu-id="e108e-321">Event ID</span></span>|<span data-ttu-id="e108e-322">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="e108e-322">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|<span data-ttu-id="e108e-323">5</span><span class="sxs-lookup"><span data-stu-id="e108e-323">5</span></span>|<span data-ttu-id="e108e-324">已创建的新的垃圾回收段。</span><span class="sxs-lookup"><span data-stu-id="e108e-324">A new garbage collection segment has been created.</span></span> <span data-ttu-id="e108e-325">此外，当在已运行的进程中启用跟踪时，将为每个现有段引发此事件。</span><span class="sxs-lookup"><span data-stu-id="e108e-325">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|

<span data-ttu-id="e108e-326">下表显示了事件数据：</span><span class="sxs-lookup"><span data-stu-id="e108e-326">The following table shows the event data:</span></span>

|<span data-ttu-id="e108e-327">字段名称</span><span class="sxs-lookup"><span data-stu-id="e108e-327">Field name</span></span>|<span data-ttu-id="e108e-328">数据类型</span><span class="sxs-lookup"><span data-stu-id="e108e-328">Data type</span></span>|<span data-ttu-id="e108e-329">说明</span><span class="sxs-lookup"><span data-stu-id="e108e-329">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="e108e-330">地址</span><span class="sxs-lookup"><span data-stu-id="e108e-330">Address</span></span>|<span data-ttu-id="e108e-331">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e108e-331">win:UInt64</span></span>|<span data-ttu-id="e108e-332">段的地址。</span><span class="sxs-lookup"><span data-stu-id="e108e-332">The address of the segment.</span></span>|
|<span data-ttu-id="e108e-333">大小</span><span class="sxs-lookup"><span data-stu-id="e108e-333">Size</span></span>|<span data-ttu-id="e108e-334">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e108e-334">win:UInt64</span></span>|<span data-ttu-id="e108e-335">段的大小。</span><span class="sxs-lookup"><span data-stu-id="e108e-335">The size of the segment.</span></span>|
|<span data-ttu-id="e108e-336">类型</span><span class="sxs-lookup"><span data-stu-id="e108e-336">Type</span></span>|<span data-ttu-id="e108e-337">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e108e-337">win:UInt32</span></span>|<span data-ttu-id="e108e-338">0x0 - 小型对象堆。</span><span class="sxs-lookup"><span data-stu-id="e108e-338">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="e108e-339">0x0 - 大型对象堆。</span><span class="sxs-lookup"><span data-stu-id="e108e-339">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="e108e-340">0x2 - 只读堆。</span><span class="sxs-lookup"><span data-stu-id="e108e-340">0x2 - Read-only heap.</span></span>|
|<span data-ttu-id="e108e-341">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e108e-341">ClrInstanceID</span></span>|<span data-ttu-id="e108e-342">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e108e-342">win:UInt16</span></span>|<span data-ttu-id="e108e-343">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="e108e-343">Unique ID for the instance of CLR or CoreCLR.</span></span>|

<span data-ttu-id="e108e-344">请注意，由垃圾回收器分配的段的大小特定于实现，且随时可能更改（包括定期更新）。</span><span class="sxs-lookup"><span data-stu-id="e108e-344">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="e108e-345">应用程序不应假设特定段的大小或依赖于此大小，也不应尝试配置段分配可用的内存量。</span><span class="sxs-lookup"><span data-stu-id="e108e-345">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="e108e-346">GCFreeSegment_V1 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-346">GCFreeSegment_V1 Event</span></span>

<span data-ttu-id="e108e-347">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="e108e-347">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="e108e-348">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="e108e-348">Keyword for raising the event</span></span>|<span data-ttu-id="e108e-349">级别</span><span class="sxs-lookup"><span data-stu-id="e108e-349">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e108e-350">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="e108e-350">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="e108e-351">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="e108e-351">Informational (4)</span></span>|

<span data-ttu-id="e108e-352">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="e108e-352">The following table shows the event information:</span></span>

|<span data-ttu-id="e108e-353">事件</span><span class="sxs-lookup"><span data-stu-id="e108e-353">Event</span></span>|<span data-ttu-id="e108e-354">事件 ID</span><span class="sxs-lookup"><span data-stu-id="e108e-354">Event ID</span></span>|<span data-ttu-id="e108e-355">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="e108e-355">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|<span data-ttu-id="e108e-356">6</span><span class="sxs-lookup"><span data-stu-id="e108e-356">6</span></span>|<span data-ttu-id="e108e-357">已释放垃圾回收段。</span><span class="sxs-lookup"><span data-stu-id="e108e-357">A garbage collection segment has been released.</span></span>|

<span data-ttu-id="e108e-358">下表显示了事件数据：</span><span class="sxs-lookup"><span data-stu-id="e108e-358">The following table shows the event data:</span></span>

|<span data-ttu-id="e108e-359">字段名称</span><span class="sxs-lookup"><span data-stu-id="e108e-359">Field name</span></span>|<span data-ttu-id="e108e-360">数据类型</span><span class="sxs-lookup"><span data-stu-id="e108e-360">Data type</span></span>|<span data-ttu-id="e108e-361">说明</span><span class="sxs-lookup"><span data-stu-id="e108e-361">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="e108e-362">地址</span><span class="sxs-lookup"><span data-stu-id="e108e-362">Address</span></span>|<span data-ttu-id="e108e-363">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e108e-363">win:UInt64</span></span>|<span data-ttu-id="e108e-364">段的地址。</span><span class="sxs-lookup"><span data-stu-id="e108e-364">The address of the segment.</span></span>|
|<span data-ttu-id="e108e-365">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e108e-365">ClrInstanceID</span></span>|<span data-ttu-id="e108e-366">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e108e-366">win:UInt16</span></span>|<span data-ttu-id="e108e-367">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="e108e-367">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="e108e-368">GCRestartEEBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-368">GCRestartEEBegin_V1 Event</span></span>

<span data-ttu-id="e108e-369">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="e108e-369">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="e108e-370">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="e108e-370">Keyword for raising the event</span></span>|<span data-ttu-id="e108e-371">级别</span><span class="sxs-lookup"><span data-stu-id="e108e-371">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e108e-372">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="e108e-372">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="e108e-373">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="e108e-373">Informational (4)</span></span>|

<span data-ttu-id="e108e-374">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="e108e-374">The following table shows the event information:</span></span>

|<span data-ttu-id="e108e-375">事件</span><span class="sxs-lookup"><span data-stu-id="e108e-375">Event</span></span>|<span data-ttu-id="e108e-376">事件 ID</span><span class="sxs-lookup"><span data-stu-id="e108e-376">Event ID</span></span>|<span data-ttu-id="e108e-377">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="e108e-377">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|<span data-ttu-id="e108e-378">7</span><span class="sxs-lookup"><span data-stu-id="e108e-378">7</span></span>|<span data-ttu-id="e108e-379">已开始从公共语言运行时挂起进行恢复。</span><span class="sxs-lookup"><span data-stu-id="e108e-379">Resumption from common language runtime suspension has begun.</span></span>|

<span data-ttu-id="e108e-380">无事件数据。</span><span class="sxs-lookup"><span data-stu-id="e108e-380">No event data.</span></span>

## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="e108e-381">GCRestartEEEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-381">GCRestartEEEnd_V1 Event</span></span>

<span data-ttu-id="e108e-382">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="e108e-382">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="e108e-383">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="e108e-383">Keyword for raising the event</span></span>|<span data-ttu-id="e108e-384">级别</span><span class="sxs-lookup"><span data-stu-id="e108e-384">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e108e-385">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="e108e-385">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="e108e-386">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="e108e-386">Informational (4)</span></span>|

<span data-ttu-id="e108e-387">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="e108e-387">The following table shows the event information:</span></span>

|<span data-ttu-id="e108e-388">事件</span><span class="sxs-lookup"><span data-stu-id="e108e-388">Event</span></span>|<span data-ttu-id="e108e-389">事件 ID</span><span class="sxs-lookup"><span data-stu-id="e108e-389">Event Id</span></span>|<span data-ttu-id="e108e-390">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="e108e-390">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|<span data-ttu-id="e108e-391">3</span><span class="sxs-lookup"><span data-stu-id="e108e-391">3</span></span>|<span data-ttu-id="e108e-392">从公共语言运行时挂起进行的恢复已结束。</span><span class="sxs-lookup"><span data-stu-id="e108e-392">Resumption from common language runtime suspension has ended.</span></span>|

<span data-ttu-id="e108e-393">无事件数据。</span><span class="sxs-lookup"><span data-stu-id="e108e-393">No event data.</span></span>

## <a name="gcsuspendee_v1-event"></a><span data-ttu-id="e108e-394">GCSuspendEE_V1 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-394">GCSuspendEE_V1 Event</span></span>

<span data-ttu-id="e108e-395">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="e108e-395">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="e108e-396">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="e108e-396">Keyword for raising the event</span></span>|<span data-ttu-id="e108e-397">级别</span><span class="sxs-lookup"><span data-stu-id="e108e-397">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e108e-398">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="e108e-398">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="e108e-399">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="e108e-399">Informational (4)</span></span>|

<span data-ttu-id="e108e-400">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="e108e-400">The following table shows the event information:</span></span>

|<span data-ttu-id="e108e-401">事件</span><span class="sxs-lookup"><span data-stu-id="e108e-401">Event</span></span>|<span data-ttu-id="e108e-402">事件 ID</span><span class="sxs-lookup"><span data-stu-id="e108e-402">Event ID</span></span>|<span data-ttu-id="e108e-403">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="e108e-403">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEE_V1`|<span data-ttu-id="e108e-404">9</span><span class="sxs-lookup"><span data-stu-id="e108e-404">9</span></span>|<span data-ttu-id="e108e-405">开始挂起垃圾回收的执行引擎。</span><span class="sxs-lookup"><span data-stu-id="e108e-405">Start of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="e108e-406">下表显示了事件数据：</span><span class="sxs-lookup"><span data-stu-id="e108e-406">The following table shows the event data:</span></span>

|<span data-ttu-id="e108e-407">字段名称</span><span class="sxs-lookup"><span data-stu-id="e108e-407">Field name</span></span>|<span data-ttu-id="e108e-408">数据类型</span><span class="sxs-lookup"><span data-stu-id="e108e-408">Data type</span></span>|<span data-ttu-id="e108e-409">说明</span><span class="sxs-lookup"><span data-stu-id="e108e-409">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="e108e-410">原因</span><span class="sxs-lookup"><span data-stu-id="e108e-410">Reason</span></span>|<span data-ttu-id="e108e-411">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e108e-411">win:UInt16</span></span>|<span data-ttu-id="e108e-412">0x0 - 其他。</span><span class="sxs-lookup"><span data-stu-id="e108e-412">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="e108e-413">0x1 - 垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="e108e-413">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="e108e-414">0x2 - 应用程序域关闭。</span><span class="sxs-lookup"><span data-stu-id="e108e-414">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="e108e-415">0x3 - 代码间距调整。</span><span class="sxs-lookup"><span data-stu-id="e108e-415">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="e108e-416">0x4 - 关闭。</span><span class="sxs-lookup"><span data-stu-id="e108e-416">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="e108e-417">0x5 - 调试器。</span><span class="sxs-lookup"><span data-stu-id="e108e-417">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="e108e-418">0x6 - 准备垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="e108e-418">0x6 - Preparation for garbage collection.</span></span>|
|<span data-ttu-id="e108e-419">计数</span><span class="sxs-lookup"><span data-stu-id="e108e-419">Count</span></span>|<span data-ttu-id="e108e-420">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e108e-420">win:UInt32</span></span>|<span data-ttu-id="e108e-421">此时的 GC 计数。</span><span class="sxs-lookup"><span data-stu-id="e108e-421">The GC count at the time.</span></span> <span data-ttu-id="e108e-422">通常情况下，会在这之后看到后续 GC 开始事件，且在垃圾回收期间增加 GC 索引时，其计数会增加 1。</span><span class="sxs-lookup"><span data-stu-id="e108e-422">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|
|<span data-ttu-id="e108e-423">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e108e-423">ClrInstanceID</span></span>|<span data-ttu-id="e108e-424">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e108e-424">win:UInt16</span></span>|<span data-ttu-id="e108e-425">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="e108e-425">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="e108e-426">GCSuspendEEEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-426">GCSuspendEEEnd_V1 Event</span></span>

<span data-ttu-id="e108e-427">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="e108e-427">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="e108e-428">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="e108e-428">Keyword for raising the event</span></span>|<span data-ttu-id="e108e-429">级别</span><span class="sxs-lookup"><span data-stu-id="e108e-429">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e108e-430">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="e108e-430">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="e108e-431">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="e108e-431">Informational (4)</span></span>|

<span data-ttu-id="e108e-432">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="e108e-432">The following table shows the event information:</span></span>

|<span data-ttu-id="e108e-433">事件</span><span class="sxs-lookup"><span data-stu-id="e108e-433">Event</span></span>|<span data-ttu-id="e108e-434">事件 ID</span><span class="sxs-lookup"><span data-stu-id="e108e-434">Event ID</span></span>|<span data-ttu-id="e108e-435">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="e108e-435">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|<span data-ttu-id="e108e-436">8</span><span class="sxs-lookup"><span data-stu-id="e108e-436">8</span></span>|<span data-ttu-id="e108e-437">结束垃圾回收执行引擎的挂起。</span><span class="sxs-lookup"><span data-stu-id="e108e-437">End of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="e108e-438">无事件数据。</span><span class="sxs-lookup"><span data-stu-id="e108e-438">No event data.</span></span>

## <a name="gcallocationtick_v2-event"></a><span data-ttu-id="e108e-439">GCAllocationTick_V2 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-439">GCAllocationTick_V2 Event</span></span>

<span data-ttu-id="e108e-440">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="e108e-440">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="e108e-441">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="e108e-441">Keyword for raising the event</span></span>|<span data-ttu-id="e108e-442">级别</span><span class="sxs-lookup"><span data-stu-id="e108e-442">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e108e-443">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="e108e-443">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="e108e-444">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="e108e-444">Informational (4)</span></span>|

<span data-ttu-id="e108e-445">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="e108e-445">The following table shows the event information:</span></span>

|<span data-ttu-id="e108e-446">事件</span><span class="sxs-lookup"><span data-stu-id="e108e-446">Event</span></span>|<span data-ttu-id="e108e-447">事件 ID</span><span class="sxs-lookup"><span data-stu-id="e108e-447">Event ID</span></span>|<span data-ttu-id="e108e-448">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="e108e-448">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCAllocationTick_V2`|<span data-ttu-id="e108e-449">10</span><span class="sxs-lookup"><span data-stu-id="e108e-449">10</span></span>|<span data-ttu-id="e108e-450">每次大约分配 100 KB。</span><span class="sxs-lookup"><span data-stu-id="e108e-450">Each time approximately 100 KB is allocated.</span></span>|

<span data-ttu-id="e108e-451">下表显示了事件数据：</span><span class="sxs-lookup"><span data-stu-id="e108e-451">The following table shows the event data:</span></span>

|<span data-ttu-id="e108e-452">字段名称</span><span class="sxs-lookup"><span data-stu-id="e108e-452">Field name</span></span>|<span data-ttu-id="e108e-453">数据类型</span><span class="sxs-lookup"><span data-stu-id="e108e-453">Data type</span></span>|<span data-ttu-id="e108e-454">说明</span><span class="sxs-lookup"><span data-stu-id="e108e-454">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="e108e-455">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="e108e-455">AllocationAmount</span></span>|<span data-ttu-id="e108e-456">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e108e-456">win:UInt32</span></span>|<span data-ttu-id="e108e-457">分配大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="e108e-457">The allocation size, in bytes.</span></span> <span data-ttu-id="e108e-458">对于小于 ULONG（4,294,967,295 字节）长度的分配，此值为精确值。</span><span class="sxs-lookup"><span data-stu-id="e108e-458">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="e108e-459">如果分配长度更大，则此字段包含了截断的值。</span><span class="sxs-lookup"><span data-stu-id="e108e-459">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="e108e-460">对于非常大的分配使用 `AllocationAmount64` 。</span><span class="sxs-lookup"><span data-stu-id="e108e-460">Use `AllocationAmount64` for very large allocations.</span></span>|
|<span data-ttu-id="e108e-461">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="e108e-461">AllocationKind</span></span>|<span data-ttu-id="e108e-462">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e108e-462">win:UInt32</span></span>|<span data-ttu-id="e108e-463">0x0 - 小型对象分配（小型对象堆中的分配）。</span><span class="sxs-lookup"><span data-stu-id="e108e-463">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="e108e-464">0x0 - 大型对象分配（大型对象堆中的分配）。</span><span class="sxs-lookup"><span data-stu-id="e108e-464">0x1 - Large object allocation (allocation is in large object heap).</span></span>|
|<span data-ttu-id="e108e-465">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e108e-465">ClrInstanceID</span></span>|<span data-ttu-id="e108e-466">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e108e-466">win:UInt16</span></span>|<span data-ttu-id="e108e-467">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="e108e-467">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|<span data-ttu-id="e108e-468">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="e108e-468">AllocationAmount64</span></span>|<span data-ttu-id="e108e-469">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e108e-469">win:UInt64</span></span>|<span data-ttu-id="e108e-470">分配大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="e108e-470">The allocation size, in bytes.</span></span> <span data-ttu-id="e108e-471">对于非常大的分配，此值为精确值。</span><span class="sxs-lookup"><span data-stu-id="e108e-471">This value is accurate for very large allocations.</span></span>|
|<span data-ttu-id="e108e-472">TypeId</span><span class="sxs-lookup"><span data-stu-id="e108e-472">TypeId</span></span>|<span data-ttu-id="e108e-473">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="e108e-473">win:Pointer</span></span>|<span data-ttu-id="e108e-474">MethodTable 的地址。</span><span class="sxs-lookup"><span data-stu-id="e108e-474">The address of the MethodTable.</span></span> <span data-ttu-id="e108e-475">如果在此事件期间分配了几种类型的对象，则此地址为对应于分配的最后一个对象（导致超过 100 KB 阙值的对象）的 MethodTable 地址。</span><span class="sxs-lookup"><span data-stu-id="e108e-475">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="e108e-476">TypeName</span><span class="sxs-lookup"><span data-stu-id="e108e-476">TypeName</span></span>|<span data-ttu-id="e108e-477">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="e108e-477">win:UnicodeString</span></span>|<span data-ttu-id="e108e-478">已分配的类型的名称。</span><span class="sxs-lookup"><span data-stu-id="e108e-478">The name of the type that was allocated.</span></span> <span data-ttu-id="e108e-479">如果在此事件期间分配了几种类型的对象，则此地址为对应于分配的最后一个类型（导致超过 100 KB 阙值的对象）。</span><span class="sxs-lookup"><span data-stu-id="e108e-479">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="e108e-480">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="e108e-480">HeapIndex</span></span>|<span data-ttu-id="e108e-481">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e108e-481">win:UInt32</span></span>|<span data-ttu-id="e108e-482">此对象所分配到的堆。</span><span class="sxs-lookup"><span data-stu-id="e108e-482">The heap where the object was allocated.</span></span> <span data-ttu-id="e108e-483">与工作站垃圾回收一起运行时，此值为 0（零）。</span><span class="sxs-lookup"><span data-stu-id="e108e-483">This value is 0 (zero) when running with workstation garbage collection.</span></span>|

## <a name="gcallocationtick_v3-event"></a><span data-ttu-id="e108e-484">GCAllocationTick_V3 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-484">GCAllocationTick_V3 Event</span></span>

<span data-ttu-id="e108e-485">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="e108e-485">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="e108e-486">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="e108e-486">Keyword for raising the event</span></span>|<span data-ttu-id="e108e-487">级别</span><span class="sxs-lookup"><span data-stu-id="e108e-487">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e108e-488">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="e108e-488">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="e108e-489">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="e108e-489">Informational (4)</span></span>|

<span data-ttu-id="e108e-490">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="e108e-490">The following table shows the event information:</span></span>

|<span data-ttu-id="e108e-491">事件</span><span class="sxs-lookup"><span data-stu-id="e108e-491">Event</span></span>|<span data-ttu-id="e108e-492">事件 ID</span><span class="sxs-lookup"><span data-stu-id="e108e-492">Event ID</span></span>|<span data-ttu-id="e108e-493">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="e108e-493">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCAllocationTick_V3`|<span data-ttu-id="e108e-494">10</span><span class="sxs-lookup"><span data-stu-id="e108e-494">10</span></span>|<span data-ttu-id="e108e-495">每次大约分配 100 KB。</span><span class="sxs-lookup"><span data-stu-id="e108e-495">Each time approximately 100 KB is allocated.</span></span>|

<span data-ttu-id="e108e-496">下表显示了事件数据：</span><span class="sxs-lookup"><span data-stu-id="e108e-496">The following table shows the event data:</span></span>

|<span data-ttu-id="e108e-497">字段名称</span><span class="sxs-lookup"><span data-stu-id="e108e-497">Field name</span></span>|<span data-ttu-id="e108e-498">数据类型</span><span class="sxs-lookup"><span data-stu-id="e108e-498">Data type</span></span>|<span data-ttu-id="e108e-499">说明</span><span class="sxs-lookup"><span data-stu-id="e108e-499">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="e108e-500">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="e108e-500">AllocationAmount</span></span>|<span data-ttu-id="e108e-501">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e108e-501">win:UInt32</span></span>|<span data-ttu-id="e108e-502">分配大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="e108e-502">The allocation size, in bytes.</span></span> <span data-ttu-id="e108e-503">对于小于 ULONG（4,294,967,295 字节）长度的分配，此值为精确值。</span><span class="sxs-lookup"><span data-stu-id="e108e-503">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="e108e-504">如果分配长度更大，则此字段包含了截断的值。</span><span class="sxs-lookup"><span data-stu-id="e108e-504">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="e108e-505">对于非常大的分配使用 `AllocationAmount64` 。</span><span class="sxs-lookup"><span data-stu-id="e108e-505">Use `AllocationAmount64` for very large allocations.</span></span>|
|<span data-ttu-id="e108e-506">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="e108e-506">AllocationKind</span></span>|<span data-ttu-id="e108e-507">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e108e-507">win:UInt32</span></span>|<span data-ttu-id="e108e-508">0x0 - 小型对象分配（小型对象堆中的分配）。</span><span class="sxs-lookup"><span data-stu-id="e108e-508">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="e108e-509">0x0 - 大型对象分配（大型对象堆中的分配）。</span><span class="sxs-lookup"><span data-stu-id="e108e-509">0x1 - Large object allocation (allocation is in large object heap).</span></span>|
|<span data-ttu-id="e108e-510">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e108e-510">ClrInstanceID</span></span>|<span data-ttu-id="e108e-511">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e108e-511">win:UInt16</span></span>|<span data-ttu-id="e108e-512">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="e108e-512">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|<span data-ttu-id="e108e-513">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="e108e-513">AllocationAmount64</span></span>|<span data-ttu-id="e108e-514">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e108e-514">win:UInt64</span></span>|<span data-ttu-id="e108e-515">分配大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="e108e-515">The allocation size, in bytes.</span></span> <span data-ttu-id="e108e-516">对于非常大的分配，此值为精确值。</span><span class="sxs-lookup"><span data-stu-id="e108e-516">This value is accurate for very large allocations.</span></span>|
|<span data-ttu-id="e108e-517">TypeId</span><span class="sxs-lookup"><span data-stu-id="e108e-517">TypeId</span></span>|<span data-ttu-id="e108e-518">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="e108e-518">win:Pointer</span></span>|<span data-ttu-id="e108e-519">MethodTable 的地址。</span><span class="sxs-lookup"><span data-stu-id="e108e-519">The address of the MethodTable.</span></span> <span data-ttu-id="e108e-520">如果在此事件期间分配了几种类型的对象，则此地址为对应于分配的最后一个对象（导致超过 100 KB 阙值的对象）的 MethodTable 地址。</span><span class="sxs-lookup"><span data-stu-id="e108e-520">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="e108e-521">TypeName</span><span class="sxs-lookup"><span data-stu-id="e108e-521">TypeName</span></span>|<span data-ttu-id="e108e-522">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="e108e-522">win:UnicodeString</span></span>|<span data-ttu-id="e108e-523">已分配的类型的名称。</span><span class="sxs-lookup"><span data-stu-id="e108e-523">The name of the type that was allocated.</span></span> <span data-ttu-id="e108e-524">如果在此事件期间分配了几种类型的对象，则此地址为对应于分配的最后一个类型（导致超过 100 KB 阙值的对象）。</span><span class="sxs-lookup"><span data-stu-id="e108e-524">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="e108e-525">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="e108e-525">HeapIndex</span></span>|<span data-ttu-id="e108e-526">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e108e-526">win:UInt32</span></span>|<span data-ttu-id="e108e-527">此对象所分配到的堆。</span><span class="sxs-lookup"><span data-stu-id="e108e-527">The heap where the object was allocated.</span></span> <span data-ttu-id="e108e-528">与工作站垃圾回收一起运行时，此值为 0（零）。</span><span class="sxs-lookup"><span data-stu-id="e108e-528">This value is 0 (zero) when running with workstation garbage collection.</span></span>|
|<span data-ttu-id="e108e-529">地址</span><span class="sxs-lookup"><span data-stu-id="e108e-529">Address</span></span>|<span data-ttu-id="e108e-530">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="e108e-530">win:Pointer</span></span>|<span data-ttu-id="e108e-531">上次分配的对象的地址。</span><span class="sxs-lookup"><span data-stu-id="e108e-531">The address of the last allocated object.</span></span>|

## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="e108e-532">GCFinalizersBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-532">GCFinalizersBegin_V1 Event</span></span>

<span data-ttu-id="e108e-533">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="e108e-533">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="e108e-534">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="e108e-534">Keyword for raising the event</span></span>|<span data-ttu-id="e108e-535">级别</span><span class="sxs-lookup"><span data-stu-id="e108e-535">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e108e-536">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="e108e-536">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="e108e-537">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="e108e-537">Informational (4)</span></span>|

<span data-ttu-id="e108e-538">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="e108e-538">The following table shows the event information:</span></span>

|<span data-ttu-id="e108e-539">事件</span><span class="sxs-lookup"><span data-stu-id="e108e-539">Event</span></span>|<span data-ttu-id="e108e-540">事件 ID</span><span class="sxs-lookup"><span data-stu-id="e108e-540">Event ID</span></span>|<span data-ttu-id="e108e-541">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="e108e-541">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|<span data-ttu-id="e108e-542">14</span><span class="sxs-lookup"><span data-stu-id="e108e-542">14</span></span>|<span data-ttu-id="e108e-543">开始运行终结器。</span><span class="sxs-lookup"><span data-stu-id="e108e-543">The start of running finalizers.</span></span>|

<span data-ttu-id="e108e-544">无事件数据。</span><span class="sxs-lookup"><span data-stu-id="e108e-544">No event data.</span></span>

## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="e108e-545">GCFinalizersEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-545">GCFinalizersEnd_V1 Event</span></span>

<span data-ttu-id="e108e-546">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="e108e-546">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="e108e-547">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="e108e-547">Keyword for raising the event</span></span>|<span data-ttu-id="e108e-548">级别</span><span class="sxs-lookup"><span data-stu-id="e108e-548">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e108e-549">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="e108e-549">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="e108e-550">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="e108e-550">Informational (4)</span></span>|

<span data-ttu-id="e108e-551">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="e108e-551">The following table shows the event information:</span></span>

|<span data-ttu-id="e108e-552">事件</span><span class="sxs-lookup"><span data-stu-id="e108e-552">Event</span></span>|<span data-ttu-id="e108e-553">事件 ID</span><span class="sxs-lookup"><span data-stu-id="e108e-553">Event ID</span></span>|<span data-ttu-id="e108e-554">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="e108e-554">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|<span data-ttu-id="e108e-555">13</span><span class="sxs-lookup"><span data-stu-id="e108e-555">13</span></span>|<span data-ttu-id="e108e-556">结束运行终结器。</span><span class="sxs-lookup"><span data-stu-id="e108e-556">The end of running finalizers.</span></span>|

<span data-ttu-id="e108e-557">下表显示了事件数据：</span><span class="sxs-lookup"><span data-stu-id="e108e-557">The following table shows the event data:</span></span>

|<span data-ttu-id="e108e-558">字段名称</span><span class="sxs-lookup"><span data-stu-id="e108e-558">Field name</span></span>|<span data-ttu-id="e108e-559">数据类型</span><span class="sxs-lookup"><span data-stu-id="e108e-559">Data type</span></span>|<span data-ttu-id="e108e-560">说明</span><span class="sxs-lookup"><span data-stu-id="e108e-560">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="e108e-561">计数</span><span class="sxs-lookup"><span data-stu-id="e108e-561">Count</span></span>|<span data-ttu-id="e108e-562">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e108e-562">win:UInt32</span></span>|<span data-ttu-id="e108e-563">运行的终结器数。</span><span class="sxs-lookup"><span data-stu-id="e108e-563">The number of finalizers that were run.</span></span>|
|<span data-ttu-id="e108e-564">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e108e-564">ClrInstanceID</span></span>|<span data-ttu-id="e108e-565">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e108e-565">win:UInt16</span></span>|<span data-ttu-id="e108e-566">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="e108e-566">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="e108e-567">GCCreateConcurrentThread_V1 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-567">GCCreateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="e108e-568">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="e108e-568">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="e108e-569">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="e108e-569">Keyword for raising the event</span></span>|<span data-ttu-id="e108e-570">级别</span><span class="sxs-lookup"><span data-stu-id="e108e-570">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e108e-571">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="e108e-571">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="e108e-572">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="e108e-572">Informational (4)</span></span>|
|<span data-ttu-id="e108e-573">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e108e-573">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e108e-574">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="e108e-574">Informational (4)</span></span>|

<span data-ttu-id="e108e-575">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="e108e-575">The following table shows the event information:</span></span>

|<span data-ttu-id="e108e-576">事件</span><span class="sxs-lookup"><span data-stu-id="e108e-576">Event</span></span>|<span data-ttu-id="e108e-577">事件 ID</span><span class="sxs-lookup"><span data-stu-id="e108e-577">Event ID</span></span>|<span data-ttu-id="e108e-578">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="e108e-578">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="e108e-579">11</span><span class="sxs-lookup"><span data-stu-id="e108e-579">11</span></span>|<span data-ttu-id="e108e-580">已创建并发垃圾回收线程。</span><span class="sxs-lookup"><span data-stu-id="e108e-580">Concurrent garbage collection thread was created.</span></span>|

<span data-ttu-id="e108e-581">无事件数据。</span><span class="sxs-lookup"><span data-stu-id="e108e-581">No event data.</span></span>

## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="e108e-582">GCTerminateConcurrentThread_V1 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-582">GCTerminateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="e108e-583">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="e108e-583">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="e108e-584">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="e108e-584">Keyword for raising the event</span></span>|<span data-ttu-id="e108e-585">级别</span><span class="sxs-lookup"><span data-stu-id="e108e-585">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e108e-586">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="e108e-586">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="e108e-587">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="e108e-587">Informational (4)</span></span>|
|<span data-ttu-id="e108e-588">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e108e-588">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e108e-589">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="e108e-589">Informational (4)</span></span>|

<span data-ttu-id="e108e-590">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="e108e-590">The following table shows the event information:</span></span>

|<span data-ttu-id="e108e-591">事件</span><span class="sxs-lookup"><span data-stu-id="e108e-591">Event</span></span>|<span data-ttu-id="e108e-592">事件 ID</span><span class="sxs-lookup"><span data-stu-id="e108e-592">Event ID</span></span>|<span data-ttu-id="e108e-593">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="e108e-593">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="e108e-594">12</span><span class="sxs-lookup"><span data-stu-id="e108e-594">12</span></span>|<span data-ttu-id="e108e-595">已终止并发垃圾回收线程。</span><span class="sxs-lookup"><span data-stu-id="e108e-595">Concurrent garbage collection thread was terminated.</span></span>|

<span data-ttu-id="e108e-596">无事件数据。</span><span class="sxs-lookup"><span data-stu-id="e108e-596">No event data.</span></span>

## <a name="see-also"></a><span data-ttu-id="e108e-597">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e108e-597">See also</span></span>

- [<span data-ttu-id="e108e-598">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="e108e-598">CLR ETW Events</span></span>](clr-etw-events.md)

---
title: 垃圾回收 ETW 事件
description: 查看有关垃圾回收 ETW 事件的详细信息。 涉及的事件包括 GCStart_V1、GCEnd_V1、GCHeapStats_V1、GCCreateSegment_V1 等。
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
ms.openlocfilehash: 58ad874ef6a12c18c404640aa66577c391573534
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309737"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="22cc6-104">垃圾回收 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-104">Garbage Collection ETW Events</span></span>

<span data-ttu-id="22cc6-105">这些事件可收集有关垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="22cc6-105">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="22cc6-106">它们可帮助进行诊断和调试，包括确定垃圾回收执行的次数、垃圾回收期间释放的内存量等。</span><span class="sxs-lookup"><span data-stu-id="22cc6-106">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>

<span data-ttu-id="22cc6-107">此类别包含以下事件：</span><span class="sxs-lookup"><span data-stu-id="22cc6-107">This category consists of the following events:</span></span>

- [<span data-ttu-id="22cc6-108">GCStart_V1 事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-108">GCStart_V1 Event</span></span>](#gcstart_v1-event)
- [<span data-ttu-id="22cc6-109">GCEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-109">GCEnd_V1 Event</span></span>](#gcend_v1-event)
- [<span data-ttu-id="22cc6-110">GCHeapStats_V1 事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-110">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1-event)
- [<span data-ttu-id="22cc6-111">GCCreateSegment_V1 事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-111">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1-event)
- [<span data-ttu-id="22cc6-112">GCFreeSegment_V1 事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-112">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1-event)
- [<span data-ttu-id="22cc6-113">GCRestartEEBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-113">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1-event)
- [<span data-ttu-id="22cc6-114">GCRestartEEEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-114">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1-event)
- [<span data-ttu-id="22cc6-115">GCSuspendEE_V1 事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-115">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1-event)
- [<span data-ttu-id="22cc6-116">GCSuspendEEEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-116">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1-event)
- [<span data-ttu-id="22cc6-117">GCAllocationTick_V2 事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-117">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2-event)
- [<span data-ttu-id="22cc6-118">GCFinalizersBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-118">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1-event)
- [<span data-ttu-id="22cc6-119">GCFinalizersEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-119">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1-event)
- [<span data-ttu-id="22cc6-120">GCCreateConcurrentThread_V1 事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-120">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1-event)
- [<span data-ttu-id="22cc6-121">GCTerminateConcurrentThread_V1 事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-121">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1-event)

## <a name="gcstart_v1-event"></a><span data-ttu-id="22cc6-122">GCStart_V1 事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-122">GCStart_V1 Event</span></span>  

<span data-ttu-id="22cc6-123">下表显示了关键字和级别。</span><span class="sxs-lookup"><span data-stu-id="22cc6-123">The following table shows the keyword and level.</span></span> <span data-ttu-id="22cc6-124">有关详细信息，请参阅[CLR ETW 关键字和级别](clr-etw-keywords-and-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="22cc6-124">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="22cc6-125">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="22cc6-125">Keyword for raising the event</span></span>|<span data-ttu-id="22cc6-126">级别</span><span class="sxs-lookup"><span data-stu-id="22cc6-126">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="22cc6-127">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="22cc6-127">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="22cc6-128">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="22cc6-128">Informational (4)</span></span>|

<span data-ttu-id="22cc6-129">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="22cc6-129">The following table shows the event information:</span></span>

|<span data-ttu-id="22cc6-130">事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-130">Event</span></span>|<span data-ttu-id="22cc6-131">事件 ID</span><span class="sxs-lookup"><span data-stu-id="22cc6-131">Event ID</span></span>|<span data-ttu-id="22cc6-132">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="22cc6-132">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCStart_V1`|<span data-ttu-id="22cc6-133">1</span><span class="sxs-lookup"><span data-stu-id="22cc6-133">1</span></span>|<span data-ttu-id="22cc6-134">垃圾回收已启动。</span><span class="sxs-lookup"><span data-stu-id="22cc6-134">A garbage collection has started.</span></span>|

<span data-ttu-id="22cc6-135">下表显示了事件数据：</span><span class="sxs-lookup"><span data-stu-id="22cc6-135">The following table shows the event data:</span></span>

|<span data-ttu-id="22cc6-136">字段名</span><span class="sxs-lookup"><span data-stu-id="22cc6-136">Field name</span></span>|<span data-ttu-id="22cc6-137">数据类型</span><span class="sxs-lookup"><span data-stu-id="22cc6-137">Data type</span></span>|<span data-ttu-id="22cc6-138">说明</span><span class="sxs-lookup"><span data-stu-id="22cc6-138">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="22cc6-139">计数</span><span class="sxs-lookup"><span data-stu-id="22cc6-139">Count</span></span>|<span data-ttu-id="22cc6-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="22cc6-140">win:UInt32</span></span>|<span data-ttu-id="22cc6-141">第 *n*代垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="22cc6-141">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="22cc6-142">深度</span><span class="sxs-lookup"><span data-stu-id="22cc6-142">Depth</span></span>|<span data-ttu-id="22cc6-143">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="22cc6-143">win:UInt32</span></span>|<span data-ttu-id="22cc6-144">正在回收的代。</span><span class="sxs-lookup"><span data-stu-id="22cc6-144">The generation that is being collected.</span></span>|
|<span data-ttu-id="22cc6-145">原因</span><span class="sxs-lookup"><span data-stu-id="22cc6-145">Reason</span></span>|<span data-ttu-id="22cc6-146">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="22cc6-146">win:UInt32</span></span>|<span data-ttu-id="22cc6-147">垃圾回收的触发原因：</span><span class="sxs-lookup"><span data-stu-id="22cc6-147">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="22cc6-148">0x0 - 小型对象堆分配。</span><span class="sxs-lookup"><span data-stu-id="22cc6-148">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="22cc6-149">0x1 - 已引发。</span><span class="sxs-lookup"><span data-stu-id="22cc6-149">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="22cc6-150">0x2 - 内存不足。</span><span class="sxs-lookup"><span data-stu-id="22cc6-150">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="22cc6-151">0x3 - 空。</span><span class="sxs-lookup"><span data-stu-id="22cc6-151">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="22cc6-152">0x4 - 大型对象堆分配。</span><span class="sxs-lookup"><span data-stu-id="22cc6-152">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="22cc6-153">0x5 - 空间不足（针对小型对象堆）。</span><span class="sxs-lookup"><span data-stu-id="22cc6-153">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="22cc6-154">0x6 - 空间不足（针对大型对象堆）。</span><span class="sxs-lookup"><span data-stu-id="22cc6-154">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="22cc6-155">0x7 - 已引发，但未强制为阻止。</span><span class="sxs-lookup"><span data-stu-id="22cc6-155">0x7 - Induced but not forced as blocking.</span></span>|
|<span data-ttu-id="22cc6-156">类型</span><span class="sxs-lookup"><span data-stu-id="22cc6-156">Type</span></span>|<span data-ttu-id="22cc6-157">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="22cc6-157">win:UInt32</span></span>|<span data-ttu-id="22cc6-158">0x0 - 在后台垃圾回收外部发生了垃圾回收阻止。</span><span class="sxs-lookup"><span data-stu-id="22cc6-158">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="22cc6-159">0x1 - 后台垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="22cc6-159">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="22cc6-160">0x0 - 后台垃圾回收期间发生了垃圾回收阻止。</span><span class="sxs-lookup"><span data-stu-id="22cc6-160">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|
|<span data-ttu-id="22cc6-161">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="22cc6-161">ClrInstanceID</span></span>|<span data-ttu-id="22cc6-162">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="22cc6-162">win:UInt16</span></span>|<span data-ttu-id="22cc6-163">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="22cc6-163">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcend_v1-event"></a><span data-ttu-id="22cc6-164">GCEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-164">GCEnd_V1 Event</span></span>

<span data-ttu-id="22cc6-165">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="22cc6-165">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="22cc6-166">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="22cc6-166">Keyword for raising the event</span></span>|<span data-ttu-id="22cc6-167">级别</span><span class="sxs-lookup"><span data-stu-id="22cc6-167">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="22cc6-168">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="22cc6-168">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="22cc6-169">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="22cc6-169">Informational (4)</span></span>|

<span data-ttu-id="22cc6-170">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="22cc6-170">The following table shows the event information:</span></span>

|<span data-ttu-id="22cc6-171">事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-171">Event</span></span>|<span data-ttu-id="22cc6-172">事件 ID</span><span class="sxs-lookup"><span data-stu-id="22cc6-172">Event ID</span></span>|<span data-ttu-id="22cc6-173">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="22cc6-173">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCEnd_V1`|<span data-ttu-id="22cc6-174">2</span><span class="sxs-lookup"><span data-stu-id="22cc6-174">2</span></span>|<span data-ttu-id="22cc6-175">垃圾回收已结束。</span><span class="sxs-lookup"><span data-stu-id="22cc6-175">The garbage collection has ended.</span></span>|

<span data-ttu-id="22cc6-176">下表显示了事件数据：</span><span class="sxs-lookup"><span data-stu-id="22cc6-176">The following table shows the event data:</span></span>

|<span data-ttu-id="22cc6-177">字段名</span><span class="sxs-lookup"><span data-stu-id="22cc6-177">Field name</span></span>|<span data-ttu-id="22cc6-178">数据类型</span><span class="sxs-lookup"><span data-stu-id="22cc6-178">Data type</span></span>|<span data-ttu-id="22cc6-179">说明</span><span class="sxs-lookup"><span data-stu-id="22cc6-179">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="22cc6-180">计数</span><span class="sxs-lookup"><span data-stu-id="22cc6-180">Count</span></span>|<span data-ttu-id="22cc6-181">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="22cc6-181">win:UInt32</span></span>|<span data-ttu-id="22cc6-182">第 *n*代垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="22cc6-182">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="22cc6-183">深度</span><span class="sxs-lookup"><span data-stu-id="22cc6-183">Depth</span></span>|<span data-ttu-id="22cc6-184">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="22cc6-184">win:UInt32</span></span>|<span data-ttu-id="22cc6-185">已回收的代。</span><span class="sxs-lookup"><span data-stu-id="22cc6-185">The generation that was collected.</span></span>|
|<span data-ttu-id="22cc6-186">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="22cc6-186">ClrInstanceID</span></span>|<span data-ttu-id="22cc6-187">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="22cc6-187">win:UInt16</span></span>|<span data-ttu-id="22cc6-188">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="22cc6-188">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcheapstats_v1-event"></a><span data-ttu-id="22cc6-189">GCHeapStats_V1 事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-189">GCHeapStats_V1 Event</span></span>

<span data-ttu-id="22cc6-190">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="22cc6-190">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="22cc6-191">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="22cc6-191">Keyword for raising the event</span></span>|<span data-ttu-id="22cc6-192">级别</span><span class="sxs-lookup"><span data-stu-id="22cc6-192">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="22cc6-193">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="22cc6-193">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="22cc6-194">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="22cc6-194">Informational (4)</span></span>|

<span data-ttu-id="22cc6-195">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="22cc6-195">The following table shows the event information:</span></span>

|<span data-ttu-id="22cc6-196">事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-196">Event</span></span>|<span data-ttu-id="22cc6-197">事件 ID</span><span class="sxs-lookup"><span data-stu-id="22cc6-197">Event ID</span></span>|<span data-ttu-id="22cc6-198">说明</span><span class="sxs-lookup"><span data-stu-id="22cc6-198">Description</span></span>|
|-----------|--------------|-----------------|
|`GCHeapStats_V1`|<span data-ttu-id="22cc6-199">4</span><span class="sxs-lookup"><span data-stu-id="22cc6-199">4</span></span>|<span data-ttu-id="22cc6-200">在每次垃圾回收结束时显示堆统计信息。</span><span class="sxs-lookup"><span data-stu-id="22cc6-200">Shows the heap statistics at the end of each garbage collection.</span></span>|

<span data-ttu-id="22cc6-201">下表显示了事件数据：</span><span class="sxs-lookup"><span data-stu-id="22cc6-201">The following table shows the event data:</span></span>

|<span data-ttu-id="22cc6-202">字段名</span><span class="sxs-lookup"><span data-stu-id="22cc6-202">Field name</span></span>|<span data-ttu-id="22cc6-203">数据类型</span><span class="sxs-lookup"><span data-stu-id="22cc6-203">Data type</span></span>|<span data-ttu-id="22cc6-204">说明</span><span class="sxs-lookup"><span data-stu-id="22cc6-204">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="22cc6-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="22cc6-205">GenerationSize0</span></span>|<span data-ttu-id="22cc6-206">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="22cc6-206">win:UInt64</span></span>|<span data-ttu-id="22cc6-207">第 0 代内存的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="22cc6-207">The size, in bytes, of generation 0 memory.</span></span>|
|<span data-ttu-id="22cc6-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="22cc6-208">TotalPromotedSize0</span></span>|<span data-ttu-id="22cc6-209">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="22cc6-209">win:UInt64</span></span>|<span data-ttu-id="22cc6-210">从第 0 代提升到第 1 代的字节数。</span><span class="sxs-lookup"><span data-stu-id="22cc6-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|
|<span data-ttu-id="22cc6-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="22cc6-211">GenerationSize1</span></span>|<span data-ttu-id="22cc6-212">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="22cc6-212">win:UInt64</span></span>|<span data-ttu-id="22cc6-213">第 1 代内存的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="22cc6-213">The size, in bytes, of generation 1 memory.</span></span>|
|<span data-ttu-id="22cc6-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="22cc6-214">TotalPromotedSize1</span></span>|<span data-ttu-id="22cc6-215">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="22cc6-215">win:UInt64</span></span>|<span data-ttu-id="22cc6-216">从第 1 代提升到第 2 代的字节数。</span><span class="sxs-lookup"><span data-stu-id="22cc6-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|
|<span data-ttu-id="22cc6-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="22cc6-217">GenerationSize2</span></span>|<span data-ttu-id="22cc6-218">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="22cc6-218">win:UInt64</span></span>|<span data-ttu-id="22cc6-219">第 2 代内存的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="22cc6-219">The size, in bytes, of generation 2 memory.</span></span>|
|<span data-ttu-id="22cc6-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="22cc6-220">TotalPromotedSize2</span></span>|<span data-ttu-id="22cc6-221">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="22cc6-221">win:UInt64</span></span>|<span data-ttu-id="22cc6-222">上次回收后仍存在于第 2 代中的字节数。</span><span class="sxs-lookup"><span data-stu-id="22cc6-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|
|<span data-ttu-id="22cc6-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="22cc6-223">GenerationSize3</span></span>|<span data-ttu-id="22cc6-224">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="22cc6-224">win:UInt64</span></span>|<span data-ttu-id="22cc6-225">大型对象堆的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="22cc6-225">The size, in bytes, of the large object heap.</span></span>|
|<span data-ttu-id="22cc6-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="22cc6-226">TotalPromotedSize3</span></span>|<span data-ttu-id="22cc6-227">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="22cc6-227">win:UInt64</span></span>|<span data-ttu-id="22cc6-228">上次回收后仍存在于大型对象堆中的字节数。</span><span class="sxs-lookup"><span data-stu-id="22cc6-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|
|<span data-ttu-id="22cc6-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="22cc6-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="22cc6-230">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="22cc6-230">win:UInt64</span></span>|<span data-ttu-id="22cc6-231">准备终结的对象的总大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="22cc6-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|
|<span data-ttu-id="22cc6-232">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="22cc6-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="22cc6-233">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="22cc6-233">win:UInt64</span></span>|<span data-ttu-id="22cc6-234">已准备好进行终结的对象的数目。</span><span class="sxs-lookup"><span data-stu-id="22cc6-234">The number of objects that are ready for finalization.</span></span>|
|<span data-ttu-id="22cc6-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="22cc6-235">PinnedObjectCount</span></span>|<span data-ttu-id="22cc6-236">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="22cc6-236">win:UInt32</span></span>|<span data-ttu-id="22cc6-237">固定（不可移动）对象的数目。</span><span class="sxs-lookup"><span data-stu-id="22cc6-237">The number of pinned (unmovable) objects.</span></span>|
|<span data-ttu-id="22cc6-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="22cc6-238">SinkBlockCount</span></span>|<span data-ttu-id="22cc6-239">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="22cc6-239">win:UInt32</span></span>|<span data-ttu-id="22cc6-240">正在使用的同步块的数目。</span><span class="sxs-lookup"><span data-stu-id="22cc6-240">The number of synchronization blocks in use.</span></span>|
|<span data-ttu-id="22cc6-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="22cc6-241">GCHandleCount</span></span>|<span data-ttu-id="22cc6-242">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="22cc6-242">win:UInt32</span></span>|<span data-ttu-id="22cc6-243">使用中的垃圾回收句柄的数目。</span><span class="sxs-lookup"><span data-stu-id="22cc6-243">The number of garbage collection handles in use.</span></span>|
|<span data-ttu-id="22cc6-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="22cc6-244">ClrInstanceID</span></span>|<span data-ttu-id="22cc6-245">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="22cc6-245">win:UInt16</span></span>|<span data-ttu-id="22cc6-246">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="22cc6-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|
  
## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="22cc6-247">GCCreateSegment_V1 事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-247">GCCreateSegment_V1 Event</span></span>

<span data-ttu-id="22cc6-248">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="22cc6-248">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="22cc6-249">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="22cc6-249">Keyword for raising the event</span></span>|<span data-ttu-id="22cc6-250">级别</span><span class="sxs-lookup"><span data-stu-id="22cc6-250">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="22cc6-251">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="22cc6-251">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="22cc6-252">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="22cc6-252">Informational (4)</span></span>|

<span data-ttu-id="22cc6-253">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="22cc6-253">The following table shows the event information:</span></span>

|<span data-ttu-id="22cc6-254">事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-254">Event</span></span>|<span data-ttu-id="22cc6-255">事件 ID</span><span class="sxs-lookup"><span data-stu-id="22cc6-255">Event ID</span></span>|<span data-ttu-id="22cc6-256">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="22cc6-256">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|<span data-ttu-id="22cc6-257">5</span><span class="sxs-lookup"><span data-stu-id="22cc6-257">5</span></span>|<span data-ttu-id="22cc6-258">已创建的新的垃圾回收段。</span><span class="sxs-lookup"><span data-stu-id="22cc6-258">A new garbage collection segment has been created.</span></span> <span data-ttu-id="22cc6-259">此外，当在已运行的进程中启用跟踪时，将为每个现有段引发此事件。</span><span class="sxs-lookup"><span data-stu-id="22cc6-259">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|

<span data-ttu-id="22cc6-260">下表显示了事件数据：</span><span class="sxs-lookup"><span data-stu-id="22cc6-260">The following table shows the event data:</span></span>

|<span data-ttu-id="22cc6-261">字段名</span><span class="sxs-lookup"><span data-stu-id="22cc6-261">Field name</span></span>|<span data-ttu-id="22cc6-262">数据类型</span><span class="sxs-lookup"><span data-stu-id="22cc6-262">Data type</span></span>|<span data-ttu-id="22cc6-263">说明</span><span class="sxs-lookup"><span data-stu-id="22cc6-263">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="22cc6-264">地址</span><span class="sxs-lookup"><span data-stu-id="22cc6-264">Address</span></span>|<span data-ttu-id="22cc6-265">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="22cc6-265">win:UInt64</span></span>|<span data-ttu-id="22cc6-266">段的地址。</span><span class="sxs-lookup"><span data-stu-id="22cc6-266">The address of the segment.</span></span>|
|<span data-ttu-id="22cc6-267">大小</span><span class="sxs-lookup"><span data-stu-id="22cc6-267">Size</span></span>|<span data-ttu-id="22cc6-268">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="22cc6-268">win:UInt64</span></span>|<span data-ttu-id="22cc6-269">段的大小。</span><span class="sxs-lookup"><span data-stu-id="22cc6-269">The size of the segment.</span></span>|
|<span data-ttu-id="22cc6-270">类型</span><span class="sxs-lookup"><span data-stu-id="22cc6-270">Type</span></span>|<span data-ttu-id="22cc6-271">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="22cc6-271">win:UInt32</span></span>|<span data-ttu-id="22cc6-272">0x0 - 小型对象堆。</span><span class="sxs-lookup"><span data-stu-id="22cc6-272">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="22cc6-273">0x0 - 大型对象堆。</span><span class="sxs-lookup"><span data-stu-id="22cc6-273">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="22cc6-274">0x2 - 只读堆。</span><span class="sxs-lookup"><span data-stu-id="22cc6-274">0x2 - Read-only heap.</span></span>|
|<span data-ttu-id="22cc6-275">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="22cc6-275">ClrInstanceID</span></span>|<span data-ttu-id="22cc6-276">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="22cc6-276">win:UInt16</span></span>|<span data-ttu-id="22cc6-277">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="22cc6-277">Unique ID for the instance of CLR or CoreCLR.</span></span>|

<span data-ttu-id="22cc6-278">请注意，由垃圾回收器分配的段的大小特定于实现，且随时可能更改（包括定期更新）。</span><span class="sxs-lookup"><span data-stu-id="22cc6-278">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="22cc6-279">应用程序不应假设特定段的大小或依赖于此大小，也不应尝试配置段分配可用的内存量。</span><span class="sxs-lookup"><span data-stu-id="22cc6-279">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="22cc6-280">GCFreeSegment_V1 事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-280">GCFreeSegment_V1 Event</span></span>

<span data-ttu-id="22cc6-281">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="22cc6-281">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="22cc6-282">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="22cc6-282">Keyword for raising the event</span></span>|<span data-ttu-id="22cc6-283">级别</span><span class="sxs-lookup"><span data-stu-id="22cc6-283">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="22cc6-284">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="22cc6-284">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="22cc6-285">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="22cc6-285">Informational (4)</span></span>|

<span data-ttu-id="22cc6-286">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="22cc6-286">The following table shows the event information:</span></span>

|<span data-ttu-id="22cc6-287">事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-287">Event</span></span>|<span data-ttu-id="22cc6-288">事件 ID</span><span class="sxs-lookup"><span data-stu-id="22cc6-288">Event ID</span></span>|<span data-ttu-id="22cc6-289">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="22cc6-289">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|<span data-ttu-id="22cc6-290">6</span><span class="sxs-lookup"><span data-stu-id="22cc6-290">6</span></span>|<span data-ttu-id="22cc6-291">已释放垃圾回收段。</span><span class="sxs-lookup"><span data-stu-id="22cc6-291">A garbage collection segment has been released.</span></span>|

<span data-ttu-id="22cc6-292">下表显示了事件数据：</span><span class="sxs-lookup"><span data-stu-id="22cc6-292">The following table shows the event data:</span></span>

|<span data-ttu-id="22cc6-293">字段名</span><span class="sxs-lookup"><span data-stu-id="22cc6-293">Field name</span></span>|<span data-ttu-id="22cc6-294">数据类型</span><span class="sxs-lookup"><span data-stu-id="22cc6-294">Data type</span></span>|<span data-ttu-id="22cc6-295">说明</span><span class="sxs-lookup"><span data-stu-id="22cc6-295">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="22cc6-296">地址</span><span class="sxs-lookup"><span data-stu-id="22cc6-296">Address</span></span>|<span data-ttu-id="22cc6-297">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="22cc6-297">win:UInt64</span></span>|<span data-ttu-id="22cc6-298">段的地址。</span><span class="sxs-lookup"><span data-stu-id="22cc6-298">The address of the segment.</span></span>|
|<span data-ttu-id="22cc6-299">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="22cc6-299">ClrInstanceID</span></span>|<span data-ttu-id="22cc6-300">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="22cc6-300">win:UInt16</span></span>|<span data-ttu-id="22cc6-301">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="22cc6-301">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="22cc6-302">GCRestartEEBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-302">GCRestartEEBegin_V1 Event</span></span>

<span data-ttu-id="22cc6-303">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="22cc6-303">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="22cc6-304">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="22cc6-304">Keyword for raising the event</span></span>|<span data-ttu-id="22cc6-305">级别</span><span class="sxs-lookup"><span data-stu-id="22cc6-305">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="22cc6-306">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="22cc6-306">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="22cc6-307">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="22cc6-307">Informational (4)</span></span>|

<span data-ttu-id="22cc6-308">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="22cc6-308">The following table shows the event information:</span></span>

|<span data-ttu-id="22cc6-309">事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-309">Event</span></span>|<span data-ttu-id="22cc6-310">事件 ID</span><span class="sxs-lookup"><span data-stu-id="22cc6-310">Event ID</span></span>|<span data-ttu-id="22cc6-311">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="22cc6-311">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|<span data-ttu-id="22cc6-312">7</span><span class="sxs-lookup"><span data-stu-id="22cc6-312">7</span></span>|<span data-ttu-id="22cc6-313">已开始从公共语言运行时挂起进行恢复。</span><span class="sxs-lookup"><span data-stu-id="22cc6-313">Resumption from common language runtime suspension has begun.</span></span>|

<span data-ttu-id="22cc6-314">无事件数据。</span><span class="sxs-lookup"><span data-stu-id="22cc6-314">No event data.</span></span>

## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="22cc6-315">GCRestartEEEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-315">GCRestartEEEnd_V1 Event</span></span>

<span data-ttu-id="22cc6-316">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="22cc6-316">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="22cc6-317">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="22cc6-317">Keyword for raising the event</span></span>|<span data-ttu-id="22cc6-318">级别</span><span class="sxs-lookup"><span data-stu-id="22cc6-318">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="22cc6-319">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="22cc6-319">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="22cc6-320">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="22cc6-320">Informational (4)</span></span>|

<span data-ttu-id="22cc6-321">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="22cc6-321">The following table shows the event information:</span></span>

|<span data-ttu-id="22cc6-322">事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-322">Event</span></span>|<span data-ttu-id="22cc6-323">事件 ID</span><span class="sxs-lookup"><span data-stu-id="22cc6-323">Event Id</span></span>|<span data-ttu-id="22cc6-324">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="22cc6-324">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|<span data-ttu-id="22cc6-325">3</span><span class="sxs-lookup"><span data-stu-id="22cc6-325">3</span></span>|<span data-ttu-id="22cc6-326">从公共语言运行时挂起进行的恢复已结束。</span><span class="sxs-lookup"><span data-stu-id="22cc6-326">Resumption from common language runtime suspension has ended.</span></span>|

<span data-ttu-id="22cc6-327">无事件数据。</span><span class="sxs-lookup"><span data-stu-id="22cc6-327">No event data.</span></span>

## <a name="gcsuspendee_v1-event"></a><span data-ttu-id="22cc6-328">GCSuspendEE_V1 事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-328">GCSuspendEE_V1 Event</span></span>

<span data-ttu-id="22cc6-329">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="22cc6-329">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="22cc6-330">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="22cc6-330">Keyword for raising the event</span></span>|<span data-ttu-id="22cc6-331">级别</span><span class="sxs-lookup"><span data-stu-id="22cc6-331">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="22cc6-332">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="22cc6-332">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="22cc6-333">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="22cc6-333">Informational (4)</span></span>|

<span data-ttu-id="22cc6-334">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="22cc6-334">The following table shows the event information:</span></span>

|<span data-ttu-id="22cc6-335">事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-335">Event</span></span>|<span data-ttu-id="22cc6-336">事件 ID</span><span class="sxs-lookup"><span data-stu-id="22cc6-336">Event ID</span></span>|<span data-ttu-id="22cc6-337">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="22cc6-337">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEE_V1`|<span data-ttu-id="22cc6-338">9</span><span class="sxs-lookup"><span data-stu-id="22cc6-338">9</span></span>|<span data-ttu-id="22cc6-339">开始挂起垃圾回收的执行引擎。</span><span class="sxs-lookup"><span data-stu-id="22cc6-339">Start of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="22cc6-340">下表显示了事件数据：</span><span class="sxs-lookup"><span data-stu-id="22cc6-340">The following table shows the event data:</span></span>

|<span data-ttu-id="22cc6-341">字段名</span><span class="sxs-lookup"><span data-stu-id="22cc6-341">Field name</span></span>|<span data-ttu-id="22cc6-342">数据类型</span><span class="sxs-lookup"><span data-stu-id="22cc6-342">Data type</span></span>|<span data-ttu-id="22cc6-343">说明</span><span class="sxs-lookup"><span data-stu-id="22cc6-343">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="22cc6-344">原因</span><span class="sxs-lookup"><span data-stu-id="22cc6-344">Reason</span></span>|<span data-ttu-id="22cc6-345">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="22cc6-345">win:UInt16</span></span>|<span data-ttu-id="22cc6-346">0x0 - 其他。</span><span class="sxs-lookup"><span data-stu-id="22cc6-346">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="22cc6-347">0x1 - 垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="22cc6-347">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="22cc6-348">0x2 - 应用程序域关闭。</span><span class="sxs-lookup"><span data-stu-id="22cc6-348">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="22cc6-349">0x3 - 代码间距调整。</span><span class="sxs-lookup"><span data-stu-id="22cc6-349">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="22cc6-350">0x4 - 关闭。</span><span class="sxs-lookup"><span data-stu-id="22cc6-350">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="22cc6-351">0x5 - 调试器。</span><span class="sxs-lookup"><span data-stu-id="22cc6-351">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="22cc6-352">0x6 - 准备垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="22cc6-352">0x6 - Preparation for garbage collection.</span></span>|
|<span data-ttu-id="22cc6-353">计数</span><span class="sxs-lookup"><span data-stu-id="22cc6-353">Count</span></span>|<span data-ttu-id="22cc6-354">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="22cc6-354">win:UInt32</span></span>|<span data-ttu-id="22cc6-355">此时的 GC 计数。</span><span class="sxs-lookup"><span data-stu-id="22cc6-355">The GC count at the time.</span></span> <span data-ttu-id="22cc6-356">通常情况下，会在这之后看到后续 GC 开始事件，且在垃圾回收期间增加 GC 索引时，其计数会增加 1。</span><span class="sxs-lookup"><span data-stu-id="22cc6-356">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|
|<span data-ttu-id="22cc6-357">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="22cc6-357">ClrInstanceID</span></span>|<span data-ttu-id="22cc6-358">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="22cc6-358">win:UInt16</span></span>|<span data-ttu-id="22cc6-359">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="22cc6-359">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="22cc6-360">GCSuspendEEEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-360">GCSuspendEEEnd_V1 Event</span></span>

<span data-ttu-id="22cc6-361">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="22cc6-361">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="22cc6-362">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="22cc6-362">Keyword for raising the event</span></span>|<span data-ttu-id="22cc6-363">级别</span><span class="sxs-lookup"><span data-stu-id="22cc6-363">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="22cc6-364">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="22cc6-364">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="22cc6-365">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="22cc6-365">Informational (4)</span></span>|

<span data-ttu-id="22cc6-366">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="22cc6-366">The following table shows the event information:</span></span>

|<span data-ttu-id="22cc6-367">事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-367">Event</span></span>|<span data-ttu-id="22cc6-368">事件 ID</span><span class="sxs-lookup"><span data-stu-id="22cc6-368">Event ID</span></span>|<span data-ttu-id="22cc6-369">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="22cc6-369">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|<span data-ttu-id="22cc6-370">8</span><span class="sxs-lookup"><span data-stu-id="22cc6-370">8</span></span>|<span data-ttu-id="22cc6-371">结束垃圾回收执行引擎的挂起。</span><span class="sxs-lookup"><span data-stu-id="22cc6-371">End of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="22cc6-372">无事件数据。</span><span class="sxs-lookup"><span data-stu-id="22cc6-372">No event data.</span></span>

## <a name="gcallocationtick_v2-event"></a><span data-ttu-id="22cc6-373">GCAllocationTick_V2 事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-373">GCAllocationTick_V2 Event</span></span>

<span data-ttu-id="22cc6-374">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="22cc6-374">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="22cc6-375">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="22cc6-375">Keyword for raising the event</span></span>|<span data-ttu-id="22cc6-376">级别</span><span class="sxs-lookup"><span data-stu-id="22cc6-376">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="22cc6-377">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="22cc6-377">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="22cc6-378">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="22cc6-378">Informational (4)</span></span>|

<span data-ttu-id="22cc6-379">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="22cc6-379">The following table shows the event information:</span></span>

|<span data-ttu-id="22cc6-380">事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-380">Event</span></span>|<span data-ttu-id="22cc6-381">事件 ID</span><span class="sxs-lookup"><span data-stu-id="22cc6-381">Event ID</span></span>|<span data-ttu-id="22cc6-382">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="22cc6-382">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCAllocationTick_V2`|<span data-ttu-id="22cc6-383">10</span><span class="sxs-lookup"><span data-stu-id="22cc6-383">10</span></span>|<span data-ttu-id="22cc6-384">每次大约分配 100 KB。</span><span class="sxs-lookup"><span data-stu-id="22cc6-384">Each time approximately 100 KB is allocated.</span></span>|

<span data-ttu-id="22cc6-385">下表显示了事件数据：</span><span class="sxs-lookup"><span data-stu-id="22cc6-385">The following table shows the event data:</span></span>

|<span data-ttu-id="22cc6-386">字段名</span><span class="sxs-lookup"><span data-stu-id="22cc6-386">Field name</span></span>|<span data-ttu-id="22cc6-387">数据类型</span><span class="sxs-lookup"><span data-stu-id="22cc6-387">Data type</span></span>|<span data-ttu-id="22cc6-388">说明</span><span class="sxs-lookup"><span data-stu-id="22cc6-388">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="22cc6-389">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="22cc6-389">AllocationAmount</span></span>|<span data-ttu-id="22cc6-390">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="22cc6-390">win:UInt32</span></span>|<span data-ttu-id="22cc6-391">分配大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="22cc6-391">The allocation size, in bytes.</span></span> <span data-ttu-id="22cc6-392">对于小于 ULONG（4,294,967,295 字节）长度的分配，此值为精确值。</span><span class="sxs-lookup"><span data-stu-id="22cc6-392">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="22cc6-393">如果分配长度更大，则此字段包含了截断的值。</span><span class="sxs-lookup"><span data-stu-id="22cc6-393">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="22cc6-394">对于非常大的分配使用 `AllocationAmount64` 。</span><span class="sxs-lookup"><span data-stu-id="22cc6-394">Use `AllocationAmount64` for very large allocations.</span></span>|
|<span data-ttu-id="22cc6-395">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="22cc6-395">AllocationKind</span></span>|<span data-ttu-id="22cc6-396">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="22cc6-396">win:UInt32</span></span>|<span data-ttu-id="22cc6-397">0x0 - 小型对象分配（小型对象堆中的分配）。</span><span class="sxs-lookup"><span data-stu-id="22cc6-397">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="22cc6-398">0x0 - 大型对象分配（大型对象堆中的分配）。</span><span class="sxs-lookup"><span data-stu-id="22cc6-398">0x1 - Large object allocation (allocation is in large object heap).</span></span>|
|<span data-ttu-id="22cc6-399">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="22cc6-399">ClrInstanceID</span></span>|<span data-ttu-id="22cc6-400">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="22cc6-400">win:UInt16</span></span>|<span data-ttu-id="22cc6-401">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="22cc6-401">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|<span data-ttu-id="22cc6-402">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="22cc6-402">AllocationAmount64</span></span>|<span data-ttu-id="22cc6-403">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="22cc6-403">win:UInt64</span></span>|<span data-ttu-id="22cc6-404">分配大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="22cc6-404">The allocation size, in bytes.</span></span> <span data-ttu-id="22cc6-405">对于非常大的分配，此值为精确值。</span><span class="sxs-lookup"><span data-stu-id="22cc6-405">This value is accurate for very large allocations.</span></span>|
|<span data-ttu-id="22cc6-406">TypeId</span><span class="sxs-lookup"><span data-stu-id="22cc6-406">TypeId</span></span>|<span data-ttu-id="22cc6-407">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="22cc6-407">win:Pointer</span></span>|<span data-ttu-id="22cc6-408">MethodTable 的地址。</span><span class="sxs-lookup"><span data-stu-id="22cc6-408">The address of the MethodTable.</span></span> <span data-ttu-id="22cc6-409">如果在此事件期间分配了几种类型的对象，则此地址为对应于分配的最后一个对象（导致超过 100 KB 阙值的对象）的 MethodTable 地址。</span><span class="sxs-lookup"><span data-stu-id="22cc6-409">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="22cc6-410">TypeName</span><span class="sxs-lookup"><span data-stu-id="22cc6-410">TypeName</span></span>|<span data-ttu-id="22cc6-411">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="22cc6-411">win:UnicodeString</span></span>|<span data-ttu-id="22cc6-412">已分配的类型的名称。</span><span class="sxs-lookup"><span data-stu-id="22cc6-412">The name of the type that was allocated.</span></span> <span data-ttu-id="22cc6-413">如果在此事件期间分配了几种类型的对象，则此地址为对应于分配的最后一个类型（导致超过 100 KB 阙值的对象）。</span><span class="sxs-lookup"><span data-stu-id="22cc6-413">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="22cc6-414">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="22cc6-414">HeapIndex</span></span>|<span data-ttu-id="22cc6-415">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="22cc6-415">win:UInt32</span></span>|<span data-ttu-id="22cc6-416">此对象所分配到的堆。</span><span class="sxs-lookup"><span data-stu-id="22cc6-416">The heap where the object was allocated.</span></span> <span data-ttu-id="22cc6-417">与工作站垃圾回收一起运行时，此值为 0（零）。</span><span class="sxs-lookup"><span data-stu-id="22cc6-417">This value is 0 (zero) when running with workstation garbage collection.</span></span>|

## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="22cc6-418">GCFinalizersBegin_V1 事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-418">GCFinalizersBegin_V1 Event</span></span>

<span data-ttu-id="22cc6-419">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="22cc6-419">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="22cc6-420">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="22cc6-420">Keyword for raising the event</span></span>|<span data-ttu-id="22cc6-421">级别</span><span class="sxs-lookup"><span data-stu-id="22cc6-421">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="22cc6-422">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="22cc6-422">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="22cc6-423">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="22cc6-423">Informational (4)</span></span>|

<span data-ttu-id="22cc6-424">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="22cc6-424">The following table shows the event information:</span></span>

|<span data-ttu-id="22cc6-425">事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-425">Event</span></span>|<span data-ttu-id="22cc6-426">事件 ID</span><span class="sxs-lookup"><span data-stu-id="22cc6-426">Event ID</span></span>|<span data-ttu-id="22cc6-427">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="22cc6-427">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|<span data-ttu-id="22cc6-428">14</span><span class="sxs-lookup"><span data-stu-id="22cc6-428">14</span></span>|<span data-ttu-id="22cc6-429">开始运行终结器。</span><span class="sxs-lookup"><span data-stu-id="22cc6-429">The start of running finalizers.</span></span>|

<span data-ttu-id="22cc6-430">无事件数据。</span><span class="sxs-lookup"><span data-stu-id="22cc6-430">No event data.</span></span>

## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="22cc6-431">GCFinalizersEnd_V1 事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-431">GCFinalizersEnd_V1 Event</span></span>

<span data-ttu-id="22cc6-432">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="22cc6-432">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="22cc6-433">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="22cc6-433">Keyword for raising the event</span></span>|<span data-ttu-id="22cc6-434">级别</span><span class="sxs-lookup"><span data-stu-id="22cc6-434">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="22cc6-435">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="22cc6-435">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="22cc6-436">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="22cc6-436">Informational (4)</span></span>|

<span data-ttu-id="22cc6-437">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="22cc6-437">The following table shows the event information:</span></span>

|<span data-ttu-id="22cc6-438">事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-438">Event</span></span>|<span data-ttu-id="22cc6-439">事件 ID</span><span class="sxs-lookup"><span data-stu-id="22cc6-439">Event ID</span></span>|<span data-ttu-id="22cc6-440">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="22cc6-440">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|<span data-ttu-id="22cc6-441">13</span><span class="sxs-lookup"><span data-stu-id="22cc6-441">13</span></span>|<span data-ttu-id="22cc6-442">结束运行终结器。</span><span class="sxs-lookup"><span data-stu-id="22cc6-442">The end of running finalizers.</span></span>|

<span data-ttu-id="22cc6-443">下表显示了事件数据：</span><span class="sxs-lookup"><span data-stu-id="22cc6-443">The following table shows the event data:</span></span>

|<span data-ttu-id="22cc6-444">字段名</span><span class="sxs-lookup"><span data-stu-id="22cc6-444">Field name</span></span>|<span data-ttu-id="22cc6-445">数据类型</span><span class="sxs-lookup"><span data-stu-id="22cc6-445">Data type</span></span>|<span data-ttu-id="22cc6-446">说明</span><span class="sxs-lookup"><span data-stu-id="22cc6-446">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="22cc6-447">计数</span><span class="sxs-lookup"><span data-stu-id="22cc6-447">Count</span></span>|<span data-ttu-id="22cc6-448">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="22cc6-448">win:UInt32</span></span>|<span data-ttu-id="22cc6-449">运行的终结器数。</span><span class="sxs-lookup"><span data-stu-id="22cc6-449">The number of finalizers that were run.</span></span>|
|<span data-ttu-id="22cc6-450">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="22cc6-450">ClrInstanceID</span></span>|<span data-ttu-id="22cc6-451">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="22cc6-451">win:UInt16</span></span>|<span data-ttu-id="22cc6-452">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="22cc6-452">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="22cc6-453">GCCreateConcurrentThread_V1 事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-453">GCCreateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="22cc6-454">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="22cc6-454">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="22cc6-455">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="22cc6-455">Keyword for raising the event</span></span>|<span data-ttu-id="22cc6-456">级别</span><span class="sxs-lookup"><span data-stu-id="22cc6-456">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="22cc6-457">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="22cc6-457">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="22cc6-458">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="22cc6-458">Informational (4)</span></span>|
|<span data-ttu-id="22cc6-459">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="22cc6-459">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="22cc6-460">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="22cc6-460">Informational (4)</span></span>|

<span data-ttu-id="22cc6-461">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="22cc6-461">The following table shows the event information:</span></span>

|<span data-ttu-id="22cc6-462">事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-462">Event</span></span>|<span data-ttu-id="22cc6-463">事件 ID</span><span class="sxs-lookup"><span data-stu-id="22cc6-463">Event ID</span></span>|<span data-ttu-id="22cc6-464">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="22cc6-464">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="22cc6-465">11</span><span class="sxs-lookup"><span data-stu-id="22cc6-465">11</span></span>|<span data-ttu-id="22cc6-466">已创建并发垃圾回收线程。</span><span class="sxs-lookup"><span data-stu-id="22cc6-466">Concurrent garbage collection thread was created.</span></span>|

<span data-ttu-id="22cc6-467">无事件数据。</span><span class="sxs-lookup"><span data-stu-id="22cc6-467">No event data.</span></span>

## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="22cc6-468">GCTerminateConcurrentThread_V1 事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-468">GCTerminateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="22cc6-469">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="22cc6-469">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="22cc6-470">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="22cc6-470">Keyword for raising the event</span></span>|<span data-ttu-id="22cc6-471">级别</span><span class="sxs-lookup"><span data-stu-id="22cc6-471">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="22cc6-472">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="22cc6-472">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="22cc6-473">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="22cc6-473">Informational (4)</span></span>|
|<span data-ttu-id="22cc6-474">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="22cc6-474">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="22cc6-475">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="22cc6-475">Informational (4)</span></span>|

<span data-ttu-id="22cc6-476">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="22cc6-476">The following table shows the event information:</span></span>

|<span data-ttu-id="22cc6-477">事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-477">Event</span></span>|<span data-ttu-id="22cc6-478">事件 ID</span><span class="sxs-lookup"><span data-stu-id="22cc6-478">Event ID</span></span>|<span data-ttu-id="22cc6-479">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="22cc6-479">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="22cc6-480">12</span><span class="sxs-lookup"><span data-stu-id="22cc6-480">12</span></span>|<span data-ttu-id="22cc6-481">已终止并发垃圾回收线程。</span><span class="sxs-lookup"><span data-stu-id="22cc6-481">Concurrent garbage collection thread was terminated.</span></span>|

<span data-ttu-id="22cc6-482">无事件数据。</span><span class="sxs-lookup"><span data-stu-id="22cc6-482">No event data.</span></span>

## <a name="see-also"></a><span data-ttu-id="22cc6-483">另请参阅</span><span class="sxs-lookup"><span data-stu-id="22cc6-483">See also</span></span>

- [<span data-ttu-id="22cc6-484">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="22cc6-484">CLR ETW Events</span></span>](clr-etw-events.md)

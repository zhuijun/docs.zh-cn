---
title: 应用程序域资源监视 (ARM) ETW 事件
description: 阅读有关 .NET 中的应用程序域资源监视（ARM） ETW 事件的信息，例如 ThreadCreated、AppDomainMemAllocated、AppDomainMemSurvived 等。
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
ms.openlocfilehash: d118b3196b019a804df5399464cb86f7492c61b0
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309776"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="8f345-103">应用程序域资源监视 (ARM) ETW 事件</span><span class="sxs-lookup"><span data-stu-id="8f345-103">Application Domain Resource Monitoring (ARM) ETW Events</span></span>

<span data-ttu-id="8f345-104">这些事件提供有关应用程序域的状态的详细诊断信息。</span><span class="sxs-lookup"><span data-stu-id="8f345-104">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="8f345-105">你可以使用这些事件，或使用应用程序域资源监视 (ARM) 功能来获取相同的信息。</span><span class="sxs-lookup"><span data-stu-id="8f345-105">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>

## <a name="threadcreated-event"></a><span data-ttu-id="8f345-106">ThreadCreated 事件</span><span class="sxs-lookup"><span data-stu-id="8f345-106">ThreadCreated Event</span></span>

<span data-ttu-id="8f345-107">在断开的提供程序下此事件也会作为 `ThreadDC` 引发（在 `AppDomainResourceManagementRundownKeyword` 关键字下）。</span><span class="sxs-lookup"><span data-stu-id="8f345-107">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="8f345-108">这是此类别的断开提供程序下引发的唯一事件。</span><span class="sxs-lookup"><span data-stu-id="8f345-108">This is the only event that is raised under the rundown provider in this category.</span></span>

<span data-ttu-id="8f345-109">下表显示了关键字和级别。</span><span class="sxs-lookup"><span data-stu-id="8f345-109">The following table shows the keyword and level.</span></span> <span data-ttu-id="8f345-110">有关详细信息，请参阅[CLR ETW 关键字和级别](clr-etw-keywords-and-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="8f345-110">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="8f345-111">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="8f345-111">Keyword for raising the event</span></span>|<span data-ttu-id="8f345-112">级别</span><span class="sxs-lookup"><span data-stu-id="8f345-112">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="8f345-113">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="8f345-113">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="8f345-114">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="8f345-114">Informational(4)</span></span>|
|<span data-ttu-id="8f345-115">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="8f345-115">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="8f345-116">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="8f345-116">Informational(4)</span></span>|

<span data-ttu-id="8f345-117">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="8f345-117">The following table shows the event information:</span></span>

|<span data-ttu-id="8f345-118">事件</span><span class="sxs-lookup"><span data-stu-id="8f345-118">Event</span></span>|<span data-ttu-id="8f345-119">事件 ID</span><span class="sxs-lookup"><span data-stu-id="8f345-119">Event ID</span></span>|<span data-ttu-id="8f345-120">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="8f345-120">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadCreated`|<span data-ttu-id="8f345-121">85</span><span class="sxs-lookup"><span data-stu-id="8f345-121">85</span></span>|<span data-ttu-id="8f345-122">已为应用程序域创建了一个线程。</span><span class="sxs-lookup"><span data-stu-id="8f345-122">A thread was created for the application domain.</span></span>|

<span data-ttu-id="8f345-123">下表显示了事件数据：</span><span class="sxs-lookup"><span data-stu-id="8f345-123">The following table shows the event data:</span></span>

|<span data-ttu-id="8f345-124">字段名</span><span class="sxs-lookup"><span data-stu-id="8f345-124">Field name</span></span>|<span data-ttu-id="8f345-125">数据类型</span><span class="sxs-lookup"><span data-stu-id="8f345-125">Data type</span></span>|<span data-ttu-id="8f345-126">说明</span><span class="sxs-lookup"><span data-stu-id="8f345-126">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="8f345-127">ThreadID</span><span class="sxs-lookup"><span data-stu-id="8f345-127">ThreadID</span></span>|<span data-ttu-id="8f345-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="8f345-128">win:UInt64</span></span>|<span data-ttu-id="8f345-129">已创建的线程 ID。</span><span class="sxs-lookup"><span data-stu-id="8f345-129">ID of the thread that was created.</span></span>|
|<span data-ttu-id="8f345-130">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="8f345-130">AppDomainID</span></span>|<span data-ttu-id="8f345-131">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="8f345-131">win:UInt64</span></span>|<span data-ttu-id="8f345-132">正在报告其线程活动的应用程序域的标识符。</span><span class="sxs-lookup"><span data-stu-id="8f345-132">Identifier of the application domain for which thread activity is being reported.</span></span>|
|<span data-ttu-id="8f345-133">Flags</span><span class="sxs-lookup"><span data-stu-id="8f345-133">Flags</span></span>|<span data-ttu-id="8f345-134">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="8f345-134">win:UInt32</span></span>|<span data-ttu-id="8f345-135">线程创建标志。</span><span class="sxs-lookup"><span data-stu-id="8f345-135">Thread creation flags.</span></span>|
|<span data-ttu-id="8f345-136">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="8f345-136">ManagedThreadIndex</span></span>|<span data-ttu-id="8f345-137">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="8f345-137">win:UInt32</span></span>|<span data-ttu-id="8f345-138">已创建线程的托管索引。</span><span class="sxs-lookup"><span data-stu-id="8f345-138">Managed index of the thread that was created.</span></span>|
|<span data-ttu-id="8f345-139">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="8f345-139">OSThreadID</span></span>|<span data-ttu-id="8f345-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="8f345-140">win:UInt32</span></span>|<span data-ttu-id="8f345-141">已创建线程的操作系统 ID。</span><span class="sxs-lookup"><span data-stu-id="8f345-141">Operating system ID of the thread that was created.</span></span>|
|<span data-ttu-id="8f345-142">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="8f345-142">ClrInstanceID</span></span>|<span data-ttu-id="8f345-143">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="8f345-143">win:UInt16</span></span>|<span data-ttu-id="8f345-144">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="8f345-144">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemallocated-event"></a><span data-ttu-id="8f345-145">AppDomainMemAllocated 事件</span><span class="sxs-lookup"><span data-stu-id="8f345-145">AppDomainMemAllocated Event</span></span>

<span data-ttu-id="8f345-146">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="8f345-146">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="8f345-147">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="8f345-147">Keyword for raising the event</span></span>|<span data-ttu-id="8f345-148">级别</span><span class="sxs-lookup"><span data-stu-id="8f345-148">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="8f345-149">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="8f345-149">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="8f345-150">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="8f345-150">Informational(4)</span></span>|

<span data-ttu-id="8f345-151">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="8f345-151">The following table shows the event information:</span></span>

|<span data-ttu-id="8f345-152">事件</span><span class="sxs-lookup"><span data-stu-id="8f345-152">Event</span></span>|<span data-ttu-id="8f345-153">事件 ID</span><span class="sxs-lookup"><span data-stu-id="8f345-153">Event ID</span></span>|<span data-ttu-id="8f345-154">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="8f345-154">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemAllocated`|<span data-ttu-id="8f345-155">83</span><span class="sxs-lookup"><span data-stu-id="8f345-155">83</span></span>|<span data-ttu-id="8f345-156">应用程序域中分配每 4 MB 的内存（大约）。</span><span class="sxs-lookup"><span data-stu-id="8f345-156">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|

<span data-ttu-id="8f345-157">下表显示了事件数据：</span><span class="sxs-lookup"><span data-stu-id="8f345-157">The following table shows the event data:</span></span>

|<span data-ttu-id="8f345-158">字段名</span><span class="sxs-lookup"><span data-stu-id="8f345-158">Field name</span></span>|<span data-ttu-id="8f345-159">数据类型</span><span class="sxs-lookup"><span data-stu-id="8f345-159">Data type</span></span>|<span data-ttu-id="8f345-160">说明</span><span class="sxs-lookup"><span data-stu-id="8f345-160">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="8f345-161">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="8f345-161">AppDomainID</span></span>|<span data-ttu-id="8f345-162">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="8f345-162">win:UInt64</span></span>|<span data-ttu-id="8f345-163">正在报告其资源使用情况的应用程序域的标识符。</span><span class="sxs-lookup"><span data-stu-id="8f345-163">Identifier of the application domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="8f345-164">已分配</span><span class="sxs-lookup"><span data-stu-id="8f345-164">Allocated</span></span>|<span data-ttu-id="8f345-165">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="8f345-165">win:UInt64</span></span>|<span data-ttu-id="8f345-166">自应用程序域创建以来在此应用程序域中分配的字节总数（不减去已释放的内存量）。</span><span class="sxs-lookup"><span data-stu-id="8f345-166">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|
|<span data-ttu-id="8f345-167">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="8f345-167">ClrInstanceID</span></span>|<span data-ttu-id="8f345-168">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="8f345-168">win:UInt16</span></span>|<span data-ttu-id="8f345-169">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="8f345-169">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="8f345-170">AppDomainMemSurvived 事件</span><span class="sxs-lookup"><span data-stu-id="8f345-170">AppDomainMemSurvived Event</span></span>

<span data-ttu-id="8f345-171">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="8f345-171">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="8f345-172">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="8f345-172">Keyword for raising the event</span></span>|<span data-ttu-id="8f345-173">级别</span><span class="sxs-lookup"><span data-stu-id="8f345-173">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="8f345-174">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="8f345-174">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="8f345-175">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="8f345-175">Informational(4)</span></span>|

<span data-ttu-id="8f345-176">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="8f345-176">The following table shows the event information:</span></span>

|<span data-ttu-id="8f345-177">事件</span><span class="sxs-lookup"><span data-stu-id="8f345-177">Event</span></span>|<span data-ttu-id="8f345-178">事件 ID</span><span class="sxs-lookup"><span data-stu-id="8f345-178">Event ID</span></span>|<span data-ttu-id="8f345-179">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="8f345-179">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemSurvived`|<span data-ttu-id="8f345-180">84</span><span class="sxs-lookup"><span data-stu-id="8f345-180">84</span></span>|<span data-ttu-id="8f345-181">每个垃圾回收已结束。</span><span class="sxs-lookup"><span data-stu-id="8f345-181">Each garbage collection has ended.</span></span>|

<span data-ttu-id="8f345-182">下表显示了事件数据：</span><span class="sxs-lookup"><span data-stu-id="8f345-182">The following table shows the event data:</span></span>

|<span data-ttu-id="8f345-183">字段名</span><span class="sxs-lookup"><span data-stu-id="8f345-183">Field name</span></span>|<span data-ttu-id="8f345-184">数据类型</span><span class="sxs-lookup"><span data-stu-id="8f345-184">Data type</span></span>|<span data-ttu-id="8f345-185">说明</span><span class="sxs-lookup"><span data-stu-id="8f345-185">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="8f345-186">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="8f345-186">AppDomainID</span></span>|<span data-ttu-id="8f345-187">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="8f345-187">win:UInt64</span></span>|<span data-ttu-id="8f345-188">正在报告其资源使用情况的域的标识符。</span><span class="sxs-lookup"><span data-stu-id="8f345-188">Identifier of the domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="8f345-189">Survived</span><span class="sxs-lookup"><span data-stu-id="8f345-189">Survived</span></span>|<span data-ttu-id="8f345-190">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="8f345-190">win:UInt64</span></span>|<span data-ttu-id="8f345-191">上次回收后保留下来的、已知由此应用程序域保留的字节数。</span><span class="sxs-lookup"><span data-stu-id="8f345-191">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="8f345-192">此数字在完整回收之后准确且完整，但在暂时的回收之后可能不完整。</span><span class="sxs-lookup"><span data-stu-id="8f345-192">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|
|<span data-ttu-id="8f345-193">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="8f345-193">ProcessSurvived</span></span>|<span data-ttu-id="8f345-194">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="8f345-194">win:UInt64</span></span>|<span data-ttu-id="8f345-195">从上一次回收中保留的总字节数。</span><span class="sxs-lookup"><span data-stu-id="8f345-195">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="8f345-196">完整回收之后，该数字表示托管堆中实时保留的字节数。</span><span class="sxs-lookup"><span data-stu-id="8f345-196">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="8f345-197">暂时回收之后，该数字表示暂时生成中实时保留的字节数。</span><span class="sxs-lookup"><span data-stu-id="8f345-197">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|
|<span data-ttu-id="8f345-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="8f345-198">ClrInstanceID</span></span>|<span data-ttu-id="8f345-199">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="8f345-199">win:UInt16</span></span>|<span data-ttu-id="8f345-200">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="8f345-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadappdomainenter-event"></a><span data-ttu-id="8f345-201">ThreadAppDomainEnter 事件</span><span class="sxs-lookup"><span data-stu-id="8f345-201">ThreadAppDomainEnter Event</span></span>

<span data-ttu-id="8f345-202">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="8f345-202">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="8f345-203">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="8f345-203">Keyword for raising the event</span></span>|<span data-ttu-id="8f345-204">级别</span><span class="sxs-lookup"><span data-stu-id="8f345-204">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="8f345-205">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="8f345-205">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="8f345-206">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="8f345-206">Informational(4)</span></span>|
|<span data-ttu-id="8f345-207">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="8f345-207">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="8f345-208">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="8f345-208">Informational(4)</span></span>|

<span data-ttu-id="8f345-209">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="8f345-209">The following table shows the event information:</span></span>

|<span data-ttu-id="8f345-210">事件</span><span class="sxs-lookup"><span data-stu-id="8f345-210">Event</span></span>|<span data-ttu-id="8f345-211">事件 ID</span><span class="sxs-lookup"><span data-stu-id="8f345-211">Event ID</span></span>|<span data-ttu-id="8f345-212">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="8f345-212">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadAppDomainEnter`|<span data-ttu-id="8f345-213">87</span><span class="sxs-lookup"><span data-stu-id="8f345-213">87</span></span>|<span data-ttu-id="8f345-214">线程进入应用程序域。</span><span class="sxs-lookup"><span data-stu-id="8f345-214">A thread enters an application domain.</span></span>|

<span data-ttu-id="8f345-215">下表显示了事件数据：</span><span class="sxs-lookup"><span data-stu-id="8f345-215">The following table shows the event data:</span></span>

|<span data-ttu-id="8f345-216">字段名</span><span class="sxs-lookup"><span data-stu-id="8f345-216">Field name</span></span>|<span data-ttu-id="8f345-217">数据类型</span><span class="sxs-lookup"><span data-stu-id="8f345-217">Data type</span></span>|<span data-ttu-id="8f345-218">说明</span><span class="sxs-lookup"><span data-stu-id="8f345-218">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="8f345-219">ThreadID</span><span class="sxs-lookup"><span data-stu-id="8f345-219">ThreadID</span></span>|<span data-ttu-id="8f345-220">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="8f345-220">win:UInt64</span></span>|<span data-ttu-id="8f345-221">线程标识符。</span><span class="sxs-lookup"><span data-stu-id="8f345-221">The thread identifier.</span></span>|
|<span data-ttu-id="8f345-222">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="8f345-222">AppDomainID</span></span>|<span data-ttu-id="8f345-223">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="8f345-223">win:UInt64</span></span>|<span data-ttu-id="8f345-224">应用程序域标识符。</span><span class="sxs-lookup"><span data-stu-id="8f345-224">The application domain identifier.</span></span>|
|<span data-ttu-id="8f345-225">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="8f345-225">ClrInstanceID</span></span>|<span data-ttu-id="8f345-226">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="8f345-226">win:UInt16</span></span>|<span data-ttu-id="8f345-227">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="8f345-227">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadterminated-event"></a><span data-ttu-id="8f345-228">ThreadTerminated 事件</span><span class="sxs-lookup"><span data-stu-id="8f345-228">ThreadTerminated Event</span></span>

<span data-ttu-id="8f345-229">下表显示了关键字和级别：</span><span class="sxs-lookup"><span data-stu-id="8f345-229">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="8f345-230">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="8f345-230">Keyword for raising the event</span></span>|<span data-ttu-id="8f345-231">级别</span><span class="sxs-lookup"><span data-stu-id="8f345-231">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="8f345-232">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="8f345-232">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="8f345-233">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="8f345-233">Informational(4)</span></span>|
|<span data-ttu-id="8f345-234">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="8f345-234">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="8f345-235">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="8f345-235">Informational(4)</span></span>|

<span data-ttu-id="8f345-236">下表显示了事件信息：</span><span class="sxs-lookup"><span data-stu-id="8f345-236">The following table shows the event information:</span></span>

|<span data-ttu-id="8f345-237">事件</span><span class="sxs-lookup"><span data-stu-id="8f345-237">Event</span></span>|<span data-ttu-id="8f345-238">事件 ID</span><span class="sxs-lookup"><span data-stu-id="8f345-238">Event ID</span></span>|<span data-ttu-id="8f345-239">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="8f345-239">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadTerminated`|<span data-ttu-id="8f345-240">86</span><span class="sxs-lookup"><span data-stu-id="8f345-240">86</span></span>|<span data-ttu-id="8f345-241">线程终止。</span><span class="sxs-lookup"><span data-stu-id="8f345-241">A thread terminates.</span></span>|

<span data-ttu-id="8f345-242">下表显示了事件数据：</span><span class="sxs-lookup"><span data-stu-id="8f345-242">The following table shows the event data:</span></span>

|<span data-ttu-id="8f345-243">字段名</span><span class="sxs-lookup"><span data-stu-id="8f345-243">Field name</span></span>|<span data-ttu-id="8f345-244">数据类型</span><span class="sxs-lookup"><span data-stu-id="8f345-244">Data type</span></span>|<span data-ttu-id="8f345-245">说明</span><span class="sxs-lookup"><span data-stu-id="8f345-245">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="8f345-246">ThreadID</span><span class="sxs-lookup"><span data-stu-id="8f345-246">ThreadID</span></span>|<span data-ttu-id="8f345-247">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="8f345-247">win:UInt64</span></span>|<span data-ttu-id="8f345-248">线程标识符。</span><span class="sxs-lookup"><span data-stu-id="8f345-248">The thread identifier.</span></span>|
|<span data-ttu-id="8f345-249">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="8f345-249">AppDomainID</span></span>|<span data-ttu-id="8f345-250">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="8f345-250">win:UInt64</span></span>|<span data-ttu-id="8f345-251">应用程序域标识符。</span><span class="sxs-lookup"><span data-stu-id="8f345-251">The application domain identifier.</span></span>|
|<span data-ttu-id="8f345-252">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="8f345-252">ClrInstanceID</span></span>|<span data-ttu-id="8f345-253">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="8f345-253">win:UInt16</span></span>|<span data-ttu-id="8f345-254">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="8f345-254">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="8f345-255">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8f345-255">See also</span></span>

- [<span data-ttu-id="8f345-256">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="8f345-256">CLR ETW Events</span></span>](clr-etw-events.md)

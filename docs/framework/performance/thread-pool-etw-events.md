---
title: 线程池 ETW 事件
description: 查看线程池 ETW 事件，这些事件收集有关 .NET 中的线程的信息。 线程池事件为工作线程池事件或 i/o 线程池事件。
ms.date: 03/30/2017
helpviewer_keywords:
- thread pool events [.NET Framework]
- ETW, thread pool events (CLR)
ms.assetid: f2a21e3a-3b6c-4433-97f3-47ff16855ecc
ms.openlocfilehash: d3059cec5007c24d41a4a779939d4990f19305ca
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475198"
---
# <a name="thread-pool-etw-events"></a><span data-ttu-id="4fbbf-104">线程池 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="4fbbf-104">Thread Pool ETW Events</span></span>
<span data-ttu-id="4fbbf-105">这些事件收集有关工作线程和 I/O 线程的信息。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-105">These events collect information about worker and I/O threads.</span></span>  
  
 <span data-ttu-id="4fbbf-106">存在两组线程池事件：</span><span class="sxs-lookup"><span data-stu-id="4fbbf-106">There are two groups of thread pool events:</span></span>  
  
- <span data-ttu-id="4fbbf-107">[工作线程池事件](#worker-thread-pool-events)：提供有关应用程序如何使用线程池以及工作负荷如何影响并发控制的信息。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-107">[Worker thread pool events](#worker-thread-pool-events), which provide information about how an application uses the thread pool, and the effect of workloads on concurrency control.</span></span>  
  
- <span data-ttu-id="4fbbf-108">[I/O 线程池事件](#io-thread-events)：提供有关线程池中创建、停用、恢复或终止的 I/O 线程的信息。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-108">[I/O thread pool events](#io-thread-events), which provide information about I/O threads that are created, retired, unretired, or terminated in the thread pool.</span></span>  

## <a name="worker-thread-pool-events"></a><span data-ttu-id="4fbbf-109">工作线程池事件</span><span class="sxs-lookup"><span data-stu-id="4fbbf-109">Worker Thread Pool Events</span></span>
 <span data-ttu-id="4fbbf-110">这些事件与运行时工作线程池相关，并提供有关线程事件的通知（例如，创建或停止线程时）。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-110">These events relate to the runtime's worker thread pool and provide notifications for thread events (for example, when a thread is created or stopped).</span></span> <span data-ttu-id="4fbbf-111">工作线程池使用自适应算法进行并发控制，其中的线程数基于测得的吞吐量来计算。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-111">The worker thread pool uses an adaptive algorithm for concurrency control, where the number of threads is calculated based on the measured throughput.</span></span> <span data-ttu-id="4fbbf-112">工作线程池事件可用于了解应用程序如何使用线程池，以及某些工作负荷可能会对并发控制怎样的影响。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-112">Worker thread pool events can be used to understand how an application is using the thread pool, and the effect that certain workloads may have on concurrency control.</span></span>  
  
### <a name="threadpoolworkerthreadstart-and-threadpoolworkerthreadstop"></a><span data-ttu-id="4fbbf-113">ThreadPoolWorkerThreadStart 和 ThreadPoolWorkerThreadStop</span><span class="sxs-lookup"><span data-stu-id="4fbbf-113">ThreadPoolWorkerThreadStart and ThreadPoolWorkerThreadStop</span></span>  
 <span data-ttu-id="4fbbf-114">下表显示这些事件的关键字和级别。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-114">The following table shows the keyword and level for these events.</span></span> <span data-ttu-id="4fbbf-115">（有关详细信息，请参阅 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md)。）</span><span class="sxs-lookup"><span data-stu-id="4fbbf-115">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="4fbbf-116">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="4fbbf-116">Keyword for raising the event</span></span>|<span data-ttu-id="4fbbf-117">级别</span><span class="sxs-lookup"><span data-stu-id="4fbbf-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="4fbbf-118">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4fbbf-118">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4fbbf-119">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="4fbbf-119">Informational (4)</span></span>|  
  
 <span data-ttu-id="4fbbf-120">下表显示了事件信息。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-120">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="4fbbf-121">事件</span><span class="sxs-lookup"><span data-stu-id="4fbbf-121">Event</span></span>|<span data-ttu-id="4fbbf-122">事件 ID</span><span class="sxs-lookup"><span data-stu-id="4fbbf-122">Event ID</span></span>|<span data-ttu-id="4fbbf-123">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="4fbbf-123">Raised when</span></span>|  
|-|-|-|  
|`ThreadPoolWorkerThreadStart`|<span data-ttu-id="4fbbf-124">50</span><span class="sxs-lookup"><span data-stu-id="4fbbf-124">50</span></span>|<span data-ttu-id="4fbbf-125">创建工作线程。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-125">A worker thread is created.</span></span>|  
|`ThreadPoolWorkerThreadStop`|<span data-ttu-id="4fbbf-126">51</span><span class="sxs-lookup"><span data-stu-id="4fbbf-126">51</span></span>|<span data-ttu-id="4fbbf-127">停止工作线程。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-127">A worker thread is stopped.</span></span>|  
|`ThreadPoolWorkerThreadRetirementStart`|<span data-ttu-id="4fbbf-128">52</span><span class="sxs-lookup"><span data-stu-id="4fbbf-128">52</span></span>|<span data-ttu-id="4fbbf-129">停用工作线程。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-129">A worker thread retires.</span></span>|  
|`ThreadPoolWorkerThreadRetirementStop`|<span data-ttu-id="4fbbf-130">53</span><span class="sxs-lookup"><span data-stu-id="4fbbf-130">53</span></span>|<span data-ttu-id="4fbbf-131">停用的工作线程再次变为活动状态。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-131">A retired worker thread becomes active again.</span></span>|  
  
 <span data-ttu-id="4fbbf-132">下表显示了事件数据。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-132">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="4fbbf-133">字段名称</span><span class="sxs-lookup"><span data-stu-id="4fbbf-133">Field name</span></span>|<span data-ttu-id="4fbbf-134">数据类型</span><span class="sxs-lookup"><span data-stu-id="4fbbf-134">Data type</span></span>|<span data-ttu-id="4fbbf-135">说明</span><span class="sxs-lookup"><span data-stu-id="4fbbf-135">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="4fbbf-136">ActiveWorkerThreadCount</span><span class="sxs-lookup"><span data-stu-id="4fbbf-136">ActiveWorkerThreadCount</span></span>|<span data-ttu-id="4fbbf-137">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4fbbf-137">win:UInt32</span></span>|<span data-ttu-id="4fbbf-138">可用于处理工作的工作线程数，包括已在处理工作的工作线程。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-138">Number of worker threads available to process work, including those that are already processing work.</span></span>|  
|<span data-ttu-id="4fbbf-139">RetiredWorkerThreadCount</span><span class="sxs-lookup"><span data-stu-id="4fbbf-139">RetiredWorkerThreadCount</span></span>|<span data-ttu-id="4fbbf-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4fbbf-140">win:UInt32</span></span>|<span data-ttu-id="4fbbf-141">不能用于处理工作但被保留以防之后需要更多线程的工作线程数。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-141">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|  
|<span data-ttu-id="4fbbf-142">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4fbbf-142">ClrInstanceID</span></span>|<span data-ttu-id="4fbbf-143">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="4fbbf-143">Win:UInt16</span></span>|<span data-ttu-id="4fbbf-144">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-144">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="threadpoolworkerthreadadjustment"></a><span data-ttu-id="4fbbf-145">ThreadPoolWorkerThreadAdjustment</span><span class="sxs-lookup"><span data-stu-id="4fbbf-145">ThreadPoolWorkerThreadAdjustment</span></span>  
 <span data-ttu-id="4fbbf-146">这些线程池事件提供用于了解和调试线程注入（并发控制）算法行为的信息。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-146">These thread pool events provide information for understanding and debugging the behavior of the thread injection (concurrency control) algorithm.</span></span> <span data-ttu-id="4fbbf-147">这些信息由工作线程池在内部使用。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-147">The information is used internally by the worker thread pool.</span></span>  
  
#### <a name="threadpoolworkerthreadadjustmentsample"></a><span data-ttu-id="4fbbf-148">ThreadPoolWorkerThreadAdjustmentSample</span><span class="sxs-lookup"><span data-stu-id="4fbbf-148">ThreadPoolWorkerThreadAdjustmentSample</span></span>  
 <span data-ttu-id="4fbbf-149">下表显示了关键字和级别。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-149">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="4fbbf-150">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="4fbbf-150">Keyword for raising the event</span></span>|<span data-ttu-id="4fbbf-151">级别</span><span class="sxs-lookup"><span data-stu-id="4fbbf-151">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="4fbbf-152">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4fbbf-152">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4fbbf-153">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="4fbbf-153">Informational (4)</span></span>|  
  
 <span data-ttu-id="4fbbf-154">下表显示了事件信息。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-154">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="4fbbf-155">事件</span><span class="sxs-lookup"><span data-stu-id="4fbbf-155">Event</span></span>|<span data-ttu-id="4fbbf-156">事件 ID</span><span class="sxs-lookup"><span data-stu-id="4fbbf-156">Event ID</span></span>|<span data-ttu-id="4fbbf-157">说明</span><span class="sxs-lookup"><span data-stu-id="4fbbf-157">Description</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentSample`|<span data-ttu-id="4fbbf-158">54</span><span class="sxs-lookup"><span data-stu-id="4fbbf-158">54</span></span>|<span data-ttu-id="4fbbf-159">指一个示例的信息收集，即具有一定并发级别的即时吞吐量测量。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-159">Refers to the collection of information for one sample; that is, a measurement of throughput with a certain concurrency level, in an instant of time.</span></span>|  
  
 <span data-ttu-id="4fbbf-160">下表显示了事件数据。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-160">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="4fbbf-161">字段名称</span><span class="sxs-lookup"><span data-stu-id="4fbbf-161">Field name</span></span>|<span data-ttu-id="4fbbf-162">数据类型</span><span class="sxs-lookup"><span data-stu-id="4fbbf-162">Data type</span></span>|<span data-ttu-id="4fbbf-163">说明</span><span class="sxs-lookup"><span data-stu-id="4fbbf-163">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="4fbbf-164">吞吐量</span><span class="sxs-lookup"><span data-stu-id="4fbbf-164">Throughput</span></span>|<span data-ttu-id="4fbbf-165">win:Double</span><span class="sxs-lookup"><span data-stu-id="4fbbf-165">win:Double</span></span>|<span data-ttu-id="4fbbf-166">每个时间单位的完成数。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-166">Number of completions per unit of time.</span></span>|  
|<span data-ttu-id="4fbbf-167">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4fbbf-167">ClrInstanceID</span></span>|<span data-ttu-id="4fbbf-168">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="4fbbf-168">Win:UInt16</span></span>|<span data-ttu-id="4fbbf-169">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-169">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
#### <a name="threadpoolworkerthreadadjustmentadjustment"></a><span data-ttu-id="4fbbf-170">ThreadPoolWorkerThreadAdjustmentAdjustment</span><span class="sxs-lookup"><span data-stu-id="4fbbf-170">ThreadPoolWorkerThreadAdjustmentAdjustment</span></span>  
 <span data-ttu-id="4fbbf-171">下表显示了关键字和级别。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-171">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="4fbbf-172">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="4fbbf-172">Keyword for raising the event</span></span>|<span data-ttu-id="4fbbf-173">级别</span><span class="sxs-lookup"><span data-stu-id="4fbbf-173">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="4fbbf-174">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4fbbf-174">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4fbbf-175">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="4fbbf-175">Informational (4)</span></span>|  
  
 <span data-ttu-id="4fbbf-176">下表显示了事件信息。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-176">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="4fbbf-177">事件</span><span class="sxs-lookup"><span data-stu-id="4fbbf-177">Event</span></span>|<span data-ttu-id="4fbbf-178">事件 ID</span><span class="sxs-lookup"><span data-stu-id="4fbbf-178">Event ID</span></span>|<span data-ttu-id="4fbbf-179">说明</span><span class="sxs-lookup"><span data-stu-id="4fbbf-179">Description</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|<span data-ttu-id="4fbbf-180">55</span><span class="sxs-lookup"><span data-stu-id="4fbbf-180">55</span></span>|<span data-ttu-id="4fbbf-181">当线程注入（爬山）算法确定并发级别发生更改时，在控件中记录更改。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-181">Records a change in control, when the thread injection (hill-climbing) algorithm determines that a change in concurrency level is in place.</span></span>|  
  
 <span data-ttu-id="4fbbf-182">下表显示了事件数据。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-182">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="4fbbf-183">字段名称</span><span class="sxs-lookup"><span data-stu-id="4fbbf-183">Field name</span></span>|<span data-ttu-id="4fbbf-184">数据类型</span><span class="sxs-lookup"><span data-stu-id="4fbbf-184">Data type</span></span>|<span data-ttu-id="4fbbf-185">说明</span><span class="sxs-lookup"><span data-stu-id="4fbbf-185">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="4fbbf-186">AverageThroughput</span><span class="sxs-lookup"><span data-stu-id="4fbbf-186">AverageThroughput</span></span>|<span data-ttu-id="4fbbf-187">win:Double</span><span class="sxs-lookup"><span data-stu-id="4fbbf-187">win:Double</span></span>|<span data-ttu-id="4fbbf-188">测量示例的平均吞吐量。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-188">Average throughput of a sample of measurements.</span></span>|  
|<span data-ttu-id="4fbbf-189">NewWorkerThreadCount</span><span class="sxs-lookup"><span data-stu-id="4fbbf-189">NewWorkerThreadCount</span></span>|<span data-ttu-id="4fbbf-190">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4fbbf-190">win:UInt32</span></span>|<span data-ttu-id="4fbbf-191">新的活动工作线程数。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-191">New number of active worker threads.</span></span>|  
|<span data-ttu-id="4fbbf-192">Reason</span><span class="sxs-lookup"><span data-stu-id="4fbbf-192">Reason</span></span>|<span data-ttu-id="4fbbf-193">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4fbbf-193">win:UInt32</span></span>|<span data-ttu-id="4fbbf-194">调整的原因。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-194">Reason for the adjustment.</span></span><br /><br /> <span data-ttu-id="4fbbf-195">0x00 - 预热。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-195">0x00 - Warmup.</span></span><br /><br /> <span data-ttu-id="4fbbf-196">0x01 - 初始化。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-196">0x01 - Initializing.</span></span><br /><br /> <span data-ttu-id="4fbbf-197">0x02 - 随机移动。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-197">0x02 - Random move.</span></span><br /><br /> <span data-ttu-id="4fbbf-198">0x03 - 攀移。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-198">0x03 - Climbing move.</span></span><br /><br /> <span data-ttu-id="4fbbf-199">0x04 - 更改点。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-199">0x04 - Change point.</span></span><br /><br /> <span data-ttu-id="4fbbf-200">0x05 - 稳定。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-200">0x05 - Stabilizing.</span></span><br /><br /> <span data-ttu-id="4fbbf-201">0x06 - 匮乏。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-201">0x06 - Starvation.</span></span><br /><br /> <span data-ttu-id="4fbbf-202">0x07 - 线程已超时。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-202">0x07 - Thread timed out.</span></span>|  
|<span data-ttu-id="4fbbf-203">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4fbbf-203">ClrInstanceID</span></span>|<span data-ttu-id="4fbbf-204">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="4fbbf-204">Win:UInt16</span></span>|<span data-ttu-id="4fbbf-205">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-205">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
#### <a name="threadpoolworkerthreadadjustmentstats"></a><span data-ttu-id="4fbbf-206">ThreadPoolWorkerThreadAdjustmentStats</span><span class="sxs-lookup"><span data-stu-id="4fbbf-206">ThreadPoolWorkerThreadAdjustmentStats</span></span>  
 <span data-ttu-id="4fbbf-207">下表显示了关键字和级别。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-207">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="4fbbf-208">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="4fbbf-208">Keyword for raising the event</span></span>|<span data-ttu-id="4fbbf-209">级别</span><span class="sxs-lookup"><span data-stu-id="4fbbf-209">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="4fbbf-210">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4fbbf-210">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4fbbf-211">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="4fbbf-211">Informational (4)</span></span>|  
  
 <span data-ttu-id="4fbbf-212">下表显示了事件信息。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-212">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="4fbbf-213">事件</span><span class="sxs-lookup"><span data-stu-id="4fbbf-213">Event</span></span>|<span data-ttu-id="4fbbf-214">事件 ID</span><span class="sxs-lookup"><span data-stu-id="4fbbf-214">Event ID</span></span>|<span data-ttu-id="4fbbf-215">说明</span><span class="sxs-lookup"><span data-stu-id="4fbbf-215">Description</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentStats`|<span data-ttu-id="4fbbf-216">56</span><span class="sxs-lookup"><span data-stu-id="4fbbf-216">56</span></span>|<span data-ttu-id="4fbbf-217">在线程池上收集数据。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-217">Gathers data on the thread pool.</span></span>|  
  
 <span data-ttu-id="4fbbf-218">下表显示了事件数据。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-218">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="4fbbf-219">字段名称</span><span class="sxs-lookup"><span data-stu-id="4fbbf-219">Field name</span></span>|<span data-ttu-id="4fbbf-220">数据类型</span><span class="sxs-lookup"><span data-stu-id="4fbbf-220">Data type</span></span>|<span data-ttu-id="4fbbf-221">说明</span><span class="sxs-lookup"><span data-stu-id="4fbbf-221">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="4fbbf-222">Duration</span><span class="sxs-lookup"><span data-stu-id="4fbbf-222">Duration</span></span>|<span data-ttu-id="4fbbf-223">win:Double</span><span class="sxs-lookup"><span data-stu-id="4fbbf-223">win:Double</span></span>|<span data-ttu-id="4fbbf-224">收集这些统计信息的时间量（以秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-224">Amount of time, in seconds, during which these statistics were collected.</span></span>|  
|<span data-ttu-id="4fbbf-225">吞吐量</span><span class="sxs-lookup"><span data-stu-id="4fbbf-225">Throughput</span></span>|<span data-ttu-id="4fbbf-226">win:Double</span><span class="sxs-lookup"><span data-stu-id="4fbbf-226">win:Double</span></span>|<span data-ttu-id="4fbbf-227">在此间隔期间每秒完成的平均数量。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-227">Average number of completions per second during this interval.</span></span>|  
|<span data-ttu-id="4fbbf-228">ThreadWave</span><span class="sxs-lookup"><span data-stu-id="4fbbf-228">ThreadWave</span></span>|<span data-ttu-id="4fbbf-229">win:Double</span><span class="sxs-lookup"><span data-stu-id="4fbbf-229">win:Double</span></span>|<span data-ttu-id="4fbbf-230">保留以供内部使用。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-230">Reserved for internal use.</span></span>|  
|<span data-ttu-id="4fbbf-231">ThroughputWave</span><span class="sxs-lookup"><span data-stu-id="4fbbf-231">ThroughputWave</span></span>|<span data-ttu-id="4fbbf-232">win:Double</span><span class="sxs-lookup"><span data-stu-id="4fbbf-232">win:Double</span></span>|<span data-ttu-id="4fbbf-233">保留以供内部使用。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-233">Reserved for internal use.</span></span>|  
|<span data-ttu-id="4fbbf-234">ThroughputErrorEstimate</span><span class="sxs-lookup"><span data-stu-id="4fbbf-234">ThroughputErrorEstimate</span></span>|<span data-ttu-id="4fbbf-235">win:Double</span><span class="sxs-lookup"><span data-stu-id="4fbbf-235">win:Double</span></span>|<span data-ttu-id="4fbbf-236">保留以供内部使用。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-236">Reserved for internal use.</span></span>|  
|<span data-ttu-id="4fbbf-237">ThroughputErrorEstimate</span><span class="sxs-lookup"><span data-stu-id="4fbbf-237">AverageThroughputErrorEstimate</span></span>|<span data-ttu-id="4fbbf-238">win:Double</span><span class="sxs-lookup"><span data-stu-id="4fbbf-238">win:Double</span></span>|<span data-ttu-id="4fbbf-239">保留以供内部使用。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-239">Reserved for internal use.</span></span>|  
|<span data-ttu-id="4fbbf-240">ThroughputWave</span><span class="sxs-lookup"><span data-stu-id="4fbbf-240">ThroughputRatio</span></span>|<span data-ttu-id="4fbbf-241">win:Double</span><span class="sxs-lookup"><span data-stu-id="4fbbf-241">win:Double</span></span>|<span data-ttu-id="4fbbf-242">在此间隔期间因活动工作线程计数变化导致的相对吞吐量变化。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-242">The relative improvement in throughput caused by variations in active worker thread count during this interval.</span></span>|  
|<span data-ttu-id="4fbbf-243">置信度</span><span class="sxs-lookup"><span data-stu-id="4fbbf-243">Confidence</span></span>|<span data-ttu-id="4fbbf-244">win:Double</span><span class="sxs-lookup"><span data-stu-id="4fbbf-244">win:Double</span></span>|<span data-ttu-id="4fbbf-245">ThroughputRatio 字段的有效性测量。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-245">A measure of the validity of the ThroughputRatio field.</span></span>|  
|<span data-ttu-id="4fbbf-246">NewcontrolSetting</span><span class="sxs-lookup"><span data-stu-id="4fbbf-246">NewcontrolSetting</span></span>|<span data-ttu-id="4fbbf-247">win:Double</span><span class="sxs-lookup"><span data-stu-id="4fbbf-247">win:Double</span></span>|<span data-ttu-id="4fbbf-248">将作为活动线程计数未来变化基线的活动工作线程数。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-248">The number of active worker threads that will serve as the baseline for future variations in active thread count.</span></span>|  
|<span data-ttu-id="4fbbf-249">NewThreadWaveMagnitude</span><span class="sxs-lookup"><span data-stu-id="4fbbf-249">NewThreadWaveMagnitude</span></span>|<span data-ttu-id="4fbbf-250">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="4fbbf-250">Win:UInt16</span></span>|<span data-ttu-id="4fbbf-251">活动线程计数的未来变化量值。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-251">The magnitude of future variations in active thread count.</span></span>|  
|<span data-ttu-id="4fbbf-252">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4fbbf-252">ClrInstanceID</span></span>|<span data-ttu-id="4fbbf-253">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="4fbbf-253">Win:UInt16</span></span>|<span data-ttu-id="4fbbf-254">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-254">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="io-thread-events"></a><span data-ttu-id="4fbbf-255">I/O 线程事件</span><span class="sxs-lookup"><span data-stu-id="4fbbf-255">I/O Thread Events</span></span>  
 <span data-ttu-id="4fbbf-256">这些线程池事件针对 I/O 线程池（完成端口）中的线程发生，该过程是异步的。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-256">These thread pool events occur for threads in the I/O thread pool (completion ports), which is asynchronous.</span></span>  
  
### <a name="iothreadcreate_v1"></a><span data-ttu-id="4fbbf-257">IOThreadCreate_V1</span><span class="sxs-lookup"><span data-stu-id="4fbbf-257">IOThreadCreate_V1</span></span>  
 <span data-ttu-id="4fbbf-258">下表显示了关键字和级别。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-258">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="4fbbf-259">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="4fbbf-259">Keyword for raising the event</span></span>|<span data-ttu-id="4fbbf-260">级别</span><span class="sxs-lookup"><span data-stu-id="4fbbf-260">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="4fbbf-261">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4fbbf-261">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4fbbf-262">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="4fbbf-262">Informational (4)</span></span>|  
  
 <span data-ttu-id="4fbbf-263">下表显示了事件信息。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-263">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="4fbbf-264">事件</span><span class="sxs-lookup"><span data-stu-id="4fbbf-264">Event</span></span>|<span data-ttu-id="4fbbf-265">事件 ID</span><span class="sxs-lookup"><span data-stu-id="4fbbf-265">Event ID</span></span>|<span data-ttu-id="4fbbf-266">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="4fbbf-266">Raised when</span></span>|  
|-|-|-|  
|`IOThreadCreate_V1`|<span data-ttu-id="4fbbf-267">44</span><span class="sxs-lookup"><span data-stu-id="4fbbf-267">44</span></span>|<span data-ttu-id="4fbbf-268">在线程池中创建 I/O 线程。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-268">An I/O thread is created in the thread pool.</span></span>|  
  
 <span data-ttu-id="4fbbf-269">下表显示了事件数据。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-269">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="4fbbf-270">字段名称</span><span class="sxs-lookup"><span data-stu-id="4fbbf-270">Field name</span></span>|<span data-ttu-id="4fbbf-271">数据类型</span><span class="sxs-lookup"><span data-stu-id="4fbbf-271">Data type</span></span>|<span data-ttu-id="4fbbf-272">说明</span><span class="sxs-lookup"><span data-stu-id="4fbbf-272">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="4fbbf-273">计数</span><span class="sxs-lookup"><span data-stu-id="4fbbf-273">Count</span></span>|<span data-ttu-id="4fbbf-274">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4fbbf-274">win:UInt64</span></span>|<span data-ttu-id="4fbbf-275">I/O 线程数，包括新创建的线程。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-275">Number of I/O threads, including the newly created thread.</span></span>|  
|<span data-ttu-id="4fbbf-276">NumRetired</span><span class="sxs-lookup"><span data-stu-id="4fbbf-276">NumRetired</span></span>|<span data-ttu-id="4fbbf-277">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4fbbf-277">win:UInt64</span></span>|<span data-ttu-id="4fbbf-278">已停用的工作线程数。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-278">Number of retired worker threads.</span></span>|  
|<span data-ttu-id="4fbbf-279">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4fbbf-279">ClrInstanceID</span></span>|<span data-ttu-id="4fbbf-280">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="4fbbf-280">Win:UInt16</span></span>|<span data-ttu-id="4fbbf-281">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-281">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="iothreadretire_v1"></a><span data-ttu-id="4fbbf-282">IOThreadRetire_V1</span><span class="sxs-lookup"><span data-stu-id="4fbbf-282">IOThreadRetire_V1</span></span>  
 <span data-ttu-id="4fbbf-283">下表显示了关键字和级别。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="4fbbf-284">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="4fbbf-284">Keyword for raising the event</span></span>|<span data-ttu-id="4fbbf-285">级别</span><span class="sxs-lookup"><span data-stu-id="4fbbf-285">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="4fbbf-286">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4fbbf-286">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4fbbf-287">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="4fbbf-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="4fbbf-288">下表显示了事件信息。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="4fbbf-289">事件</span><span class="sxs-lookup"><span data-stu-id="4fbbf-289">Event</span></span>|<span data-ttu-id="4fbbf-290">事件 ID</span><span class="sxs-lookup"><span data-stu-id="4fbbf-290">Event ID</span></span>|<span data-ttu-id="4fbbf-291">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="4fbbf-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`IOThreadRetire_V1`|<span data-ttu-id="4fbbf-292">46</span><span class="sxs-lookup"><span data-stu-id="4fbbf-292">46</span></span>|<span data-ttu-id="4fbbf-293">I/O 线程变为停用候选项。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-293">An I/O thread becomes a retirement candidate.</span></span>|  
  
 <span data-ttu-id="4fbbf-294">下表显示了事件数据。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="4fbbf-295">字段名称</span><span class="sxs-lookup"><span data-stu-id="4fbbf-295">Field name</span></span>|<span data-ttu-id="4fbbf-296">数据类型</span><span class="sxs-lookup"><span data-stu-id="4fbbf-296">Data type</span></span>|<span data-ttu-id="4fbbf-297">说明</span><span class="sxs-lookup"><span data-stu-id="4fbbf-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="4fbbf-298">计数</span><span class="sxs-lookup"><span data-stu-id="4fbbf-298">Count</span></span>|<span data-ttu-id="4fbbf-299">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4fbbf-299">win:UInt64</span></span>|<span data-ttu-id="4fbbf-300">线程池中剩余的 I/O 线程数。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-300">Number of I/O threads remaining in the thread pool.</span></span>|  
|<span data-ttu-id="4fbbf-301">NumRetired</span><span class="sxs-lookup"><span data-stu-id="4fbbf-301">NumRetired</span></span>|<span data-ttu-id="4fbbf-302">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4fbbf-302">win:UInt64</span></span>|<span data-ttu-id="4fbbf-303">已停用的 I/O 线程数。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-303">Number of retired I/O threads.</span></span>|  
|<span data-ttu-id="4fbbf-304">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4fbbf-304">ClrInstanceID</span></span>|<span data-ttu-id="4fbbf-305">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="4fbbf-305">Win:UInt16</span></span>|<span data-ttu-id="4fbbf-306">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-306">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="iothreadunretire_v1"></a><span data-ttu-id="4fbbf-307">IOThreadUnretire_V1</span><span class="sxs-lookup"><span data-stu-id="4fbbf-307">IOThreadUnretire_V1</span></span>  
 <span data-ttu-id="4fbbf-308">下表显示了关键字和级别。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-308">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="4fbbf-309">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="4fbbf-309">Keyword for raising the event</span></span>|<span data-ttu-id="4fbbf-310">级别</span><span class="sxs-lookup"><span data-stu-id="4fbbf-310">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="4fbbf-311">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4fbbf-311">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4fbbf-312">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="4fbbf-312">Informational (4)</span></span>|  
  
 <span data-ttu-id="4fbbf-313">下表显示了事件信息。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-313">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="4fbbf-314">事件</span><span class="sxs-lookup"><span data-stu-id="4fbbf-314">Event</span></span>|<span data-ttu-id="4fbbf-315">事件 ID</span><span class="sxs-lookup"><span data-stu-id="4fbbf-315">Event ID</span></span>|<span data-ttu-id="4fbbf-316">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="4fbbf-316">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`IOThreadUnretire_V1`|<span data-ttu-id="4fbbf-317">47</span><span class="sxs-lookup"><span data-stu-id="4fbbf-317">47</span></span>|<span data-ttu-id="4fbbf-318">I/O 线程因在该线程变为停用候选项后的等待期间内达到 I/O 而恢复使用。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-318">An I/O thread is unretired because of I/O that arrives within a waiting period after the thread becomes a retirement candidate.</span></span>|  
  
 <span data-ttu-id="4fbbf-319">下表显示了事件数据。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-319">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="4fbbf-320">字段名称</span><span class="sxs-lookup"><span data-stu-id="4fbbf-320">Field name</span></span>|<span data-ttu-id="4fbbf-321">数据类型</span><span class="sxs-lookup"><span data-stu-id="4fbbf-321">Data type</span></span>|<span data-ttu-id="4fbbf-322">说明</span><span class="sxs-lookup"><span data-stu-id="4fbbf-322">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="4fbbf-323">计数</span><span class="sxs-lookup"><span data-stu-id="4fbbf-323">Count</span></span>|<span data-ttu-id="4fbbf-324">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4fbbf-324">win:UInt64</span></span>|<span data-ttu-id="4fbbf-325">线程池中的 I/O 线程数，包括这一个。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-325">Number of I/O threads in the thread pool, including this one.</span></span>|  
|<span data-ttu-id="4fbbf-326">NumRetired</span><span class="sxs-lookup"><span data-stu-id="4fbbf-326">NumRetired</span></span>|<span data-ttu-id="4fbbf-327">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4fbbf-327">win:UInt64</span></span>|<span data-ttu-id="4fbbf-328">已停用的 I/O 线程数。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-328">Number of retired I/O threads.</span></span>|  
|<span data-ttu-id="4fbbf-329">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4fbbf-329">ClrInstanceID</span></span>|<span data-ttu-id="4fbbf-330">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="4fbbf-330">Win:UInt16</span></span>|<span data-ttu-id="4fbbf-331">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-331">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="iothreadterminate"></a><span data-ttu-id="4fbbf-332">IOThreadTerminate</span><span class="sxs-lookup"><span data-stu-id="4fbbf-332">IOThreadTerminate</span></span>  
 <span data-ttu-id="4fbbf-333">下表显示了关键字和级别。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-333">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="4fbbf-334">引发事件的关键字</span><span class="sxs-lookup"><span data-stu-id="4fbbf-334">Keyword for raising the event</span></span>|<span data-ttu-id="4fbbf-335">级别</span><span class="sxs-lookup"><span data-stu-id="4fbbf-335">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="4fbbf-336">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4fbbf-336">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4fbbf-337">信息性 (4)</span><span class="sxs-lookup"><span data-stu-id="4fbbf-337">Informational (4)</span></span>|  
  
 <span data-ttu-id="4fbbf-338">下表显示了事件信息。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-338">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="4fbbf-339">事件</span><span class="sxs-lookup"><span data-stu-id="4fbbf-339">Event</span></span>|<span data-ttu-id="4fbbf-340">事件 ID</span><span class="sxs-lookup"><span data-stu-id="4fbbf-340">Event ID</span></span>|<span data-ttu-id="4fbbf-341">在发生以下情况时引发</span><span class="sxs-lookup"><span data-stu-id="4fbbf-341">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`IOThreadTerminate`|<span data-ttu-id="4fbbf-342">45</span><span class="sxs-lookup"><span data-stu-id="4fbbf-342">45</span></span>|<span data-ttu-id="4fbbf-343">线程池中的 i/o 线程终止。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-343">An I/O thread is terminated in the thread pool.</span></span>|  
  
 <span data-ttu-id="4fbbf-344">下表显示了事件数据。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-344">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="4fbbf-345">字段名称</span><span class="sxs-lookup"><span data-stu-id="4fbbf-345">Field name</span></span>|<span data-ttu-id="4fbbf-346">数据类型</span><span class="sxs-lookup"><span data-stu-id="4fbbf-346">Data type</span></span>|<span data-ttu-id="4fbbf-347">说明</span><span class="sxs-lookup"><span data-stu-id="4fbbf-347">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="4fbbf-348">计数</span><span class="sxs-lookup"><span data-stu-id="4fbbf-348">Count</span></span>|<span data-ttu-id="4fbbf-349">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4fbbf-349">win:UInt64</span></span>|<span data-ttu-id="4fbbf-350">线程池中剩余的 I/O 线程数。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-350">Number of I/O threads remaining in the thread pool.</span></span>|  
|<span data-ttu-id="4fbbf-351">NumRetired</span><span class="sxs-lookup"><span data-stu-id="4fbbf-351">NumRetired</span></span>|<span data-ttu-id="4fbbf-352">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4fbbf-352">win:UInt64</span></span>|<span data-ttu-id="4fbbf-353">已停用的 I/O 线程数。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-353">Number of retired I/O threads.</span></span>|  
|<span data-ttu-id="4fbbf-354">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4fbbf-354">ClrInstanceID</span></span>|<span data-ttu-id="4fbbf-355">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="4fbbf-355">Win:UInt16</span></span>|<span data-ttu-id="4fbbf-356">CLR 或 CoreCLR 的实例的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="4fbbf-356">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4fbbf-357">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4fbbf-357">See also</span></span>

- [<span data-ttu-id="4fbbf-358">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="4fbbf-358">CLR ETW Events</span></span>](clr-etw-events.md)

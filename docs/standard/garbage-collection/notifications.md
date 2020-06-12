---
title: 垃圾回收通知
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- garbage collection, notifications
ms.assetid: e12d8e74-31e3-4035-a87d-f3e66f0a9b89
ms.openlocfilehash: 389e851782edb82578c216951be440070b92723c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84285997"
---
# <a name="garbage-collection-notifications"></a><span data-ttu-id="b155d-102">垃圾回收通知</span><span class="sxs-lookup"><span data-stu-id="b155d-102">Garbage Collection Notifications</span></span>
<span data-ttu-id="b155d-103">在有些情况下，公共语言运行时执行的完整垃圾回收（即第 2 代回收）可能会对性能产生负面影响。</span><span class="sxs-lookup"><span data-stu-id="b155d-103">There are situations in which a full garbage collection (that is, a generation 2 collection) by the common language runtime may adversely affect performance.</span></span> <span data-ttu-id="b155d-104">特别是，处理大量请求的服务器可能会出现此问题；在这种情况下，长时间垃圾回收会导致请求超时。为了防止在关键时期发生完全回收，可以接收即将执行完全垃圾回收的通知，再采取措施将工作负载重定向到另一个服务器实例。</span><span class="sxs-lookup"><span data-stu-id="b155d-104">This can be an issue particularly with servers that process large volumes of requests; in this case, a long garbage collection can cause a request time-out. To prevent a full collection from occurring during a critical period, you can be notified that a full garbage collection is approaching and then take action to redirect the workload to another server instance.</span></span> <span data-ttu-id="b155d-105">也可以自行诱导回收，前提是当前服务器实例不需要处理请求。</span><span class="sxs-lookup"><span data-stu-id="b155d-105">You can also induce a collection yourself, provided that the current server instance does not need to process requests.</span></span>  
  
 <span data-ttu-id="b155d-106"><xref:System.GC.RegisterForFullGCNotification%2A> 方法注册为，在运行时检测到即将执行完全垃圾回收时发出通知。</span><span class="sxs-lookup"><span data-stu-id="b155d-106">The <xref:System.GC.RegisterForFullGCNotification%2A> method registers for a notification to be raised when the runtime senses that a full garbage collection is approaching.</span></span> <span data-ttu-id="b155d-107">此通知分为两个部分：完全垃圾回收何时即将执行，以及完全垃圾回收何时完成。</span><span class="sxs-lookup"><span data-stu-id="b155d-107">There are two parts to this notification: when the full garbage collection is approaching and when the full garbage collection has completed.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="b155d-108">只有阻止垃圾回收会引发通知。</span><span class="sxs-lookup"><span data-stu-id="b155d-108">Only blocking garbage collections raise notifications.</span></span> <span data-ttu-id="b155d-109">如果 [\<gcConcurrent>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) 配置元素已启用，后台垃圾回收不会发出通知。</span><span class="sxs-lookup"><span data-stu-id="b155d-109">When the [\<gcConcurrent>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) configuration element is enabled, background garbage collections will not raise notifications.</span></span>  
  
 <span data-ttu-id="b155d-110">若要确定何时发出通知，请使用 <xref:System.GC.WaitForFullGCApproach%2A> 和 <xref:System.GC.WaitForFullGCComplete%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="b155d-110">To determine when a notification has been raised, use the <xref:System.GC.WaitForFullGCApproach%2A> and <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span> <span data-ttu-id="b155d-111">通常，在 `while` 循环中使用这些方法，以持续获取表示通知状态的 <xref:System.GCNotificationStatus> 枚举。</span><span class="sxs-lookup"><span data-stu-id="b155d-111">Typically, you use these methods in a `while` loop to continually obtain a <xref:System.GCNotificationStatus> enumeration that shows the status of the notification.</span></span> <span data-ttu-id="b155d-112">如果值为 <xref:System.GCNotificationStatus.Succeeded>，可以执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="b155d-112">If that value is <xref:System.GCNotificationStatus.Succeeded>, you can do the following:</span></span>  
  
- <span data-ttu-id="b155d-113">为了响应使用 <xref:System.GC.WaitForFullGCApproach%2A> 方法获得的通知，可以重定向工作负载，并能自行诱导回收。</span><span class="sxs-lookup"><span data-stu-id="b155d-113">In response to a notification obtained with the <xref:System.GC.WaitForFullGCApproach%2A> method, you can redirect the workload and possibly induce a collection yourself.</span></span>  
  
- <span data-ttu-id="b155d-114">为了响应使用 <xref:System.GC.WaitForFullGCComplete%2A> 方法获得的通知，可以让当前服务器实例再次用于处理请求。</span><span class="sxs-lookup"><span data-stu-id="b155d-114">In response to a notification obtained with the <xref:System.GC.WaitForFullGCComplete%2A> method, you can make the current server instance available to process requests again.</span></span> <span data-ttu-id="b155d-115">也可以收集信息。</span><span class="sxs-lookup"><span data-stu-id="b155d-115">You can also gather information.</span></span> <span data-ttu-id="b155d-116">例如，可以使用 <xref:System.GC.CollectionCount%2A> 方法记录回收次数。</span><span class="sxs-lookup"><span data-stu-id="b155d-116">For example, you can use the <xref:System.GC.CollectionCount%2A> method to record the number of collections.</span></span>  
  
 <span data-ttu-id="b155d-117"><xref:System.GC.WaitForFullGCApproach%2A> 和 <xref:System.GC.WaitForFullGCComplete%2A> 方法要配合使用。</span><span class="sxs-lookup"><span data-stu-id="b155d-117">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods are designed to work together.</span></span> <span data-ttu-id="b155d-118">使用一个方法，而不使用另一个方法，可能会生成不确定的结果。</span><span class="sxs-lookup"><span data-stu-id="b155d-118">Using one without the other can produce indeterminate results.</span></span>  
  
## <a name="full-garbage-collection"></a><span data-ttu-id="b155d-119">完全垃圾回收</span><span class="sxs-lookup"><span data-stu-id="b155d-119">Full Garbage Collection</span></span>  
 <span data-ttu-id="b155d-120">如果发生下列任一情况，运行时就会执行完全垃圾回收：</span><span class="sxs-lookup"><span data-stu-id="b155d-120">The runtime causes a full garbage collection when any of the following scenarios are true:</span></span>  
  
- <span data-ttu-id="b155d-121">足够多的内存已提升到第 2 代，导致执行下一个第 2 代回收。</span><span class="sxs-lookup"><span data-stu-id="b155d-121">Enough memory has been promoted into generation 2 to cause the next generation 2 collection.</span></span>  
  
- <span data-ttu-id="b155d-122">足够多的内存已提升到大型对象堆，导致执行下一个第 2 代回收。</span><span class="sxs-lookup"><span data-stu-id="b155d-122">Enough memory has been promoted into the large object heap to cause the next generation 2 collection.</span></span>  
  
- <span data-ttu-id="b155d-123">由于其他因素，导致第 1 代回收升级为第 2 代回收。</span><span class="sxs-lookup"><span data-stu-id="b155d-123">A collection of generation 1 is escalated to a collection of generation 2 due to other factors.</span></span>  
  
 <span data-ttu-id="b155d-124">在 <xref:System.GC.RegisterForFullGCNotification%2A> 方法中指定的阈值适用于前两种情况。</span><span class="sxs-lookup"><span data-stu-id="b155d-124">The thresholds you specify in the <xref:System.GC.RegisterForFullGCNotification%2A> method apply to the first two scenarios.</span></span> <span data-ttu-id="b155d-125">不过，在第一种情况下，不一定会在与指定的阈值相称的时间收到通知，原因有下面两个：</span><span class="sxs-lookup"><span data-stu-id="b155d-125">However, in the first scenario you will not always receive the notification at the time proportional to the threshold values you specify for two reasons:</span></span>  
  
- <span data-ttu-id="b155d-126">运行时不检查每个小型对象分配（出于性能考虑）。</span><span class="sxs-lookup"><span data-stu-id="b155d-126">The runtime does not check each small object allocation (for performance reasons).</span></span>  
  
- <span data-ttu-id="b155d-127">只有第 1 代回收将内存提升到第 2 代。</span><span class="sxs-lookup"><span data-stu-id="b155d-127">Only generation 1 collections promote memory into generation 2.</span></span>  
  
 <span data-ttu-id="b155d-128">第三种情况也加剧了通知接收时间的不确定性。</span><span class="sxs-lookup"><span data-stu-id="b155d-128">The third scenario also contributes to the uncertainty of when you will receive the notification.</span></span> <span data-ttu-id="b155d-129">可以在此期间重定向请求，或在可以更好适应时自行诱导回收，从而减轻不合时宜的完全垃圾回收造成的影响。尽管并不保证有效，但确实证明这是非常实用的方法。</span><span class="sxs-lookup"><span data-stu-id="b155d-129">Although this is not a guarantee, it does prove to be a useful way to mitigate the effects of an inopportune full garbage collection by redirecting the requests during this time or inducing the collection yourself when it can be better accommodated.</span></span>  
  
## <a name="notification-threshold-parameters"></a><span data-ttu-id="b155d-130">通知阈值参数</span><span class="sxs-lookup"><span data-stu-id="b155d-130">Notification Threshold Parameters</span></span>  
 <span data-ttu-id="b155d-131"><xref:System.GC.RegisterForFullGCNotification%2A> 方法包含两个参数，用于指定第 2 代对象和大型对象堆的阈值。</span><span class="sxs-lookup"><span data-stu-id="b155d-131">The <xref:System.GC.RegisterForFullGCNotification%2A> method has two parameters to specify the threshold values of the generation 2 objects and the large object heap.</span></span> <span data-ttu-id="b155d-132">如果达到这些值，就应发出垃圾回收通知。</span><span class="sxs-lookup"><span data-stu-id="b155d-132">When those values are met, a garbage collection notification should be raised.</span></span> <span data-ttu-id="b155d-133">下表介绍了这些参数。</span><span class="sxs-lookup"><span data-stu-id="b155d-133">The following table describes these parameters.</span></span>  
  
|<span data-ttu-id="b155d-134">参数</span><span class="sxs-lookup"><span data-stu-id="b155d-134">Parameter</span></span>|<span data-ttu-id="b155d-135">描述</span><span class="sxs-lookup"><span data-stu-id="b155d-135">Description</span></span>|  
|---------------|-----------------|  
|`maxGenerationThreshold`|<span data-ttu-id="b155d-136">介于 1 和 99 之间的数字，指定根据在第 2 代中提升的对象，应何时发出通知。</span><span class="sxs-lookup"><span data-stu-id="b155d-136">A number between 1 and 99 that specifies when the notification should be raised based on the objects promoted in generation 2.</span></span>|  
|`largeObjectHeapThreshold`|<span data-ttu-id="b155d-137">介于 1 和 99 之间的数字，指定根据大型对象堆中分配的对象，应何时发出通知。</span><span class="sxs-lookup"><span data-stu-id="b155d-137">A number between 1 and 99 that specifies when the notification should be raised based on the objects that are allocated in the large object heap.</span></span>|  
  
 <span data-ttu-id="b155d-138">如果指定的值过高，很可能会出现的情况是，将会收到通知，但在运行时执行回收前等待的时间太长。</span><span class="sxs-lookup"><span data-stu-id="b155d-138">If you specify a value that is too high, there is a high probability that you will receive a notification, but it could be too long a period to wait before the runtime causes a collection.</span></span> <span data-ttu-id="b155d-139">如果自行诱导回收，回收的对象可能会多于在运行时执行回收时回收的对象。</span><span class="sxs-lookup"><span data-stu-id="b155d-139">If you induce a collection yourself, you may reclaim more objects than would be reclaimed if the runtime causes the collection.</span></span>  
  
 <span data-ttu-id="b155d-140">如果指定的值过低，在运行时执行回收前等待通知的时间可能不够长。</span><span class="sxs-lookup"><span data-stu-id="b155d-140">If you specify a value that is too low, the runtime may cause the collection before you have had sufficient time to be notified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b155d-141">示例</span><span class="sxs-lookup"><span data-stu-id="b155d-141">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="b155d-142">描述</span><span class="sxs-lookup"><span data-stu-id="b155d-142">Description</span></span>  
 <span data-ttu-id="b155d-143">在下面的示例中，一组服务器处理传入的 Web 请求。</span><span class="sxs-lookup"><span data-stu-id="b155d-143">In the following example, a group of servers service incoming Web requests.</span></span> <span data-ttu-id="b155d-144">为了模拟处理请求的工作负载，将字节数组添加到 <xref:System.Collections.Generic.List%601> 集合中。</span><span class="sxs-lookup"><span data-stu-id="b155d-144">To simulate the workload of processing requests, byte arrays are added to a <xref:System.Collections.Generic.List%601> collection.</span></span> <span data-ttu-id="b155d-145">每个服务器都会注册获取垃圾回收通知，再对 `WaitForFullGCProc` 用户方法启动线程，以持续监视 <xref:System.GC.WaitForFullGCApproach%2A> 和 <xref:System.GC.WaitForFullGCComplete%2A> 方法返回的 <xref:System.GCNotificationStatus> 枚举。</span><span class="sxs-lookup"><span data-stu-id="b155d-145">Each server registers for a garbage collection notification and then starts a thread on the `WaitForFullGCProc` user method to continuously monitor the <xref:System.GCNotificationStatus> enumeration that is returned by the <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span>  
  
 <span data-ttu-id="b155d-146">在通知发出时，<xref:System.GC.WaitForFullGCApproach%2A> 和 <xref:System.GC.WaitForFullGCComplete%2A> 方法调用它们各自的事件处理用户方法：</span><span class="sxs-lookup"><span data-stu-id="b155d-146">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods call their respective event-handling user methods when a notification is raised:</span></span>  
  
- `OnFullGCApproachNotify`  
  
     <span data-ttu-id="b155d-147">此方法调用 `RedirectRequests` 用户方法，指示请求队列服务器暂停向服务器发送请求。</span><span class="sxs-lookup"><span data-stu-id="b155d-147">This method calls the `RedirectRequests` user method, which instructs the request queuing server to suspend sending requests to the server.</span></span> <span data-ttu-id="b155d-148">具体模拟方式是，将类级别变量 `bAllocate` 设置为 `false`，这样就不会再分配对象。</span><span class="sxs-lookup"><span data-stu-id="b155d-148">This is simulated by setting the class-level variable `bAllocate` to `false` so that no more objects are allocated.</span></span>  
  
     <span data-ttu-id="b155d-149">接下来，调用 `FinishExistingRequests` 用户方法，完成处理挂起的服务器请求。</span><span class="sxs-lookup"><span data-stu-id="b155d-149">Next, the `FinishExistingRequests` user method is called to finish processing the pending server requests.</span></span> <span data-ttu-id="b155d-150">具体模拟方式是，清除 <xref:System.Collections.Generic.List%601> 集合。</span><span class="sxs-lookup"><span data-stu-id="b155d-150">This is simulated by clearing the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
     <span data-ttu-id="b155d-151">最后，由于工作负载很轻，诱导垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="b155d-151">Finally, a garbage collection is induced because the workload is light.</span></span>  
  
- `OnFullGCCompleteNotify`  
  
     <span data-ttu-id="b155d-152">此方法调用用户方法 `AcceptRequests` 以继续接受请求，因为服务器不再易受完全垃圾回收影响。</span><span class="sxs-lookup"><span data-stu-id="b155d-152">This method calls the user method `AcceptRequests` to resume accepting requests because the server is no longer susceptible to a full garbage collection.</span></span> <span data-ttu-id="b155d-153">此操作的具体模拟方式是，将 `bAllocate` 变量设置为 `true`，以便能够继续将对象添加到 <xref:System.Collections.Generic.List%601> 集合。</span><span class="sxs-lookup"><span data-stu-id="b155d-153">This action is simulated by setting the `bAllocate` variable to `true` so that objects can resume being added to the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
 <span data-ttu-id="b155d-154">下面的代码包含示例的 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="b155d-154">The following code contains the `Main` method of the example.</span></span>  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 <span data-ttu-id="b155d-155">下面的代码包含 `WaitForFullGCProc` 用户方法，其中包括持续 while 循环，用于检查是否有垃圾回收通知。</span><span class="sxs-lookup"><span data-stu-id="b155d-155">The following code contains the `WaitForFullGCProc` user method, that contains a continuous while loop to check for garbage collection notifications.</span></span>  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 <span data-ttu-id="b155d-156">下面的代码包含 `OnFullGCApproachNotify` 方法，调用自</span><span class="sxs-lookup"><span data-stu-id="b155d-156">The following code contains the `OnFullGCApproachNotify` method as called from the</span></span>  
  
 <span data-ttu-id="b155d-157">`WaitForFullGCProc` 方法。</span><span class="sxs-lookup"><span data-stu-id="b155d-157">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 <span data-ttu-id="b155d-158">下面的代码包含 `OnFullGCApproachComplete` 方法，调用自</span><span class="sxs-lookup"><span data-stu-id="b155d-158">The following code contains the `OnFullGCApproachComplete` method as called from the</span></span>  
  
 <span data-ttu-id="b155d-159">`WaitForFullGCProc` 方法。</span><span class="sxs-lookup"><span data-stu-id="b155d-159">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 <span data-ttu-id="b155d-160">下面的代码包含调用自 `OnFullGCApproachNotify` 和 `OnFullGCCompleteNotify` 方法的用户方法。</span><span class="sxs-lookup"><span data-stu-id="b155d-160">The following code contains the user methods that are called from the `OnFullGCApproachNotify` and `OnFullGCCompleteNotify` methods.</span></span> <span data-ttu-id="b155d-161">用户方法重定向请求，完成现有请求，再在发生完全垃圾回收后继续执行请求。</span><span class="sxs-lookup"><span data-stu-id="b155d-161">The user methods redirect requests, finish existing requests, and then resume requests after a full garbage collection has occurred.</span></span>  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 <span data-ttu-id="b155d-162">整个代码示例如下所示：</span><span class="sxs-lookup"><span data-stu-id="b155d-162">The entire code sample is as follows:</span></span>  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b155d-163">请参阅</span><span class="sxs-lookup"><span data-stu-id="b155d-163">See also</span></span>

- [<span data-ttu-id="b155d-164">垃圾回收</span><span class="sxs-lookup"><span data-stu-id="b155d-164">Garbage Collection</span></span>](index.md)

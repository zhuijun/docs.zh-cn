---
title: CLR ETW 事件
description: 请参阅有关 Windows 公共语言运行时（CLR）事件跟踪（ETW）事件的文章。 有两个事件提供程序：运行时提供程序和断开提供程序。
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
ms.openlocfilehash: 22a2f027462d67d5a933972a7420c5f0e38353e5
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309828"
---
# <a name="clr-etw-events"></a><span data-ttu-id="27441-104">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="27441-104">CLR ETW Events</span></span>
<span data-ttu-id="27441-105">本部分的主题介绍 Windows (ETW) 事件的事件跟踪。</span><span class="sxs-lookup"><span data-stu-id="27441-105">The topics in this section describe event tracing for Windows (ETW) events.</span></span> <span data-ttu-id="27441-106">每个事件都有关联的关键字和级别，详见 [CLR ETW 关键字和级别](clr-etw-keywords-and-levels.md)主题。</span><span class="sxs-lookup"><span data-stu-id="27441-106">Each event has an associated keyword and level, which are described in the [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md) topic.</span></span> <span data-ttu-id="27441-107">CLR 有两个事件提供程序：</span><span class="sxs-lookup"><span data-stu-id="27441-107">The CLR has two providers for the events:</span></span>  
  
- <span data-ttu-id="27441-108">运行时提供程序，根据启用的关键字（事件类别）引发事件。</span><span class="sxs-lookup"><span data-stu-id="27441-108">The runtime provider, which raises events depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="27441-109">CLR 运行时提供程序 GUID 是 e13c0d23-ccbc-4e12-931b-d9cc2eee27e4。</span><span class="sxs-lookup"><span data-stu-id="27441-109">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
- <span data-ttu-id="27441-110">断开提供程序，此提供程序具有特殊用途。</span><span class="sxs-lookup"><span data-stu-id="27441-110">The rundown provider, which has special-purpose uses.</span></span> <span data-ttu-id="27441-111">CLR 断开提供程序 GUID 是 a669021c-c450-4609-a035-5af59af4df18。</span><span class="sxs-lookup"><span data-stu-id="27441-111">The CLR rundown provider GUID is a669021c-c450-4609-a035-5af59af4df18.</span></span>  
  
 <span data-ttu-id="27441-112">有关提供程序的详细信息，请参阅 [CLR ETW 提供程序](clr-etw-providers.md)。</span><span class="sxs-lookup"><span data-stu-id="27441-112">For more information about the providers, see [CLR ETW Providers](clr-etw-providers.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="27441-113">本节内容</span><span class="sxs-lookup"><span data-stu-id="27441-113">In This Section</span></span>  
 [<span data-ttu-id="27441-114">运行时信息事件</span><span class="sxs-lookup"><span data-stu-id="27441-114">Runtime Information Events</span></span>](runtime-information-etw-events.md)  
 <span data-ttu-id="27441-115">捕获有关运行时的信息，包括 SKU、版本号、激活运行时的方式、启动运行时所使用的命令行参数、GUID（如果适用），以及其他相关信息。</span><span class="sxs-lookup"><span data-stu-id="27441-115">Captures information about the runtime, including the SKU, version number, the manner in which the runtime was activated, the command-line parameters it was started with, the GUID (if applicable), and other relevant information.</span></span>  
  
 [<span data-ttu-id="27441-116">异常 Thrown_V1 事件</span><span class="sxs-lookup"><span data-stu-id="27441-116">Exception Thrown_V1 Event</span></span>](exception-thrown-v1-etw-event.md)  
 <span data-ttu-id="27441-117">捕获有关引发的异常的信息。</span><span class="sxs-lookup"><span data-stu-id="27441-117">Captures information about exceptions that are thrown.</span></span>  
  
 [<span data-ttu-id="27441-118">争用事件</span><span class="sxs-lookup"><span data-stu-id="27441-118">Contention Events</span></span>](contention-etw-events.md)  
 <span data-ttu-id="27441-119">捕获有关对运行时使用的监控视器锁或本机锁的争用情况的信息。</span><span class="sxs-lookup"><span data-stu-id="27441-119">Captures information about contention for monitor locks or native locks that the runtime uses.</span></span>  
  
 [<span data-ttu-id="27441-120">线程池事件</span><span class="sxs-lookup"><span data-stu-id="27441-120">Thread Pool Events</span></span>](thread-pool-etw-events.md)  
 <span data-ttu-id="27441-121">捕获有关工作线程池和 I/O 线程池的信息。</span><span class="sxs-lookup"><span data-stu-id="27441-121">Captures information about worker thread pools and I/O thread pools.</span></span>  
  
 [<span data-ttu-id="27441-122">加载程序事件</span><span class="sxs-lookup"><span data-stu-id="27441-122">Loader Events</span></span>](loader-etw-events.md)  
 <span data-ttu-id="27441-123">捕获有关加载和卸载应用程序域、程序集和模块的信息。</span><span class="sxs-lookup"><span data-stu-id="27441-123">Captures information about loading and unloading application domains, assemblies, and modules.</span></span>  
  
 [<span data-ttu-id="27441-124">方法事件</span><span class="sxs-lookup"><span data-stu-id="27441-124">Method Events</span></span>](method-etw-events.md)  
 <span data-ttu-id="27441-125">捕获有关用于符号解析的 CLR 方法的信息。</span><span class="sxs-lookup"><span data-stu-id="27441-125">Captures information about CLR methods for symbol resolution.</span></span>  
  
 [<span data-ttu-id="27441-126">垃圾回收事件</span><span class="sxs-lookup"><span data-stu-id="27441-126">Garbage Collection Events</span></span>](garbage-collection-etw-events.md)  
 <span data-ttu-id="27441-127">捕获与诊断和调试中的垃圾回收和帮助有关的信息。</span><span class="sxs-lookup"><span data-stu-id="27441-127">Captures information pertaining to garbage collection, to help in diagnostics and debugging.</span></span>  
  
 [<span data-ttu-id="27441-128">JIT 跟踪事件</span><span class="sxs-lookup"><span data-stu-id="27441-128">JIT Tracing Events</span></span>](jit-tracing-etw-events.md)  
 <span data-ttu-id="27441-129">捕获有关实时 (JIT) 内联和尾调用的信息。</span><span class="sxs-lookup"><span data-stu-id="27441-129">Captures information about just-in-time (JIT) inlining and tail calls.</span></span>  
  
 [<span data-ttu-id="27441-130">互操作事件</span><span class="sxs-lookup"><span data-stu-id="27441-130">Interop Events</span></span>](interop-etw-events.md)  
 <span data-ttu-id="27441-131">捕获有关 Microsoft 中间语言 (MSIL) 存根生成和缓存的信息。</span><span class="sxs-lookup"><span data-stu-id="27441-131">Captures information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 [<span data-ttu-id="27441-132">ARM 事件</span><span class="sxs-lookup"><span data-stu-id="27441-132">ARM Events</span></span>](application-domain-resource-monitoring-arm-etw-events.md)  
 <span data-ttu-id="27441-133">捕获有关应用程序域的状态的详细诊断信息。</span><span class="sxs-lookup"><span data-stu-id="27441-133">Captures detailed diagnostic information about the state of an application domain.</span></span>  
  
 [<span data-ttu-id="27441-134">安全事件</span><span class="sxs-lookup"><span data-stu-id="27441-134">Security Events</span></span>](security-etw-events.md)  
 <span data-ttu-id="27441-135">捕获有关强名称和验证码验证的信息。</span><span class="sxs-lookup"><span data-stu-id="27441-135">Captures information about strong name and Authenticode verification.</span></span>  
  
 [<span data-ttu-id="27441-136">堆栈事件</span><span class="sxs-lookup"><span data-stu-id="27441-136">Stack Event</span></span>](stack-etw-event.md)  
 <span data-ttu-id="27441-137">捕获可用于其他事件以在引发事件后生成堆栈跟踪的信息。</span><span class="sxs-lookup"><span data-stu-id="27441-137">Captures information that is used with other events to generate stack traces after an event is raised.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27441-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="27441-138">See also</span></span>

- [<span data-ttu-id="27441-139">使用 ETW 改善调试和性能优化</span><span class="sxs-lookup"><span data-stu-id="27441-139">Improve Debugging And Performance Tuning With ETW</span></span>](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw)
- [<span data-ttu-id="27441-140">控制 .NET Framework 日志记录</span><span class="sxs-lookup"><span data-stu-id="27441-140">Controlling .NET Framework Logging</span></span>](controlling-logging.md)
- [<span data-ttu-id="27441-141">CLR ETW 提供程序</span><span class="sxs-lookup"><span data-stu-id="27441-141">CLR ETW Providers</span></span>](clr-etw-providers.md)
- [<span data-ttu-id="27441-142">CLR ETW 关键字和级别</span><span class="sxs-lookup"><span data-stu-id="27441-142">CLR ETW Keywords and Levels</span></span>](clr-etw-keywords-and-levels.md)
- [<span data-ttu-id="27441-143">公共语言运行时中的 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="27441-143">ETW Events in the Common Language Runtime</span></span>](etw-events-in-the-common-language-runtime.md)

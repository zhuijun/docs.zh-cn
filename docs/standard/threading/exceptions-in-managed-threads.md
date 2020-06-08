---
title: 托管线程中的异常
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- unhandled exceptions,in managed threads
- threading [.NET Framework],unhandled exceptions
- threading [.NET Framework],exceptions in managed threads
- managed threading
ms.assetid: 11294769-2e89-43cb-890e-ad4ad79cfbee
ms.openlocfilehash: 56900ddab5e1e6ee5375c8979dc19694d4ad9c54
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279693"
---
# <a name="exceptions-in-managed-threads"></a><span data-ttu-id="5efa0-102">托管线程中的异常</span><span class="sxs-lookup"><span data-stu-id="5efa0-102">Exceptions in Managed Threads</span></span>
<span data-ttu-id="5efa0-103">从 .NET Framework 2.0 版开始，公共语言运行时允许线程中的多数未经处理的异常正常继续。</span><span class="sxs-lookup"><span data-stu-id="5efa0-103">Starting with the .NET Framework version 2.0, the common language runtime allows most unhandled exceptions in threads to proceed naturally.</span></span> <span data-ttu-id="5efa0-104">在多数情况下，这意味着未经处理的异常会导致应用程序终止。</span><span class="sxs-lookup"><span data-stu-id="5efa0-104">In most cases this means that the unhandled exception causes the application to terminate.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5efa0-105">这是对 .NET Framework 1.0 和 1.1 版的重要更改，这两个版本对许多未经处理的异常（例如，线程池线程中未经处理的异常）提供支持。</span><span class="sxs-lookup"><span data-stu-id="5efa0-105">This is a significant change from the .NET Framework versions 1.0 and 1.1, which provide a backstop for many unhandled exceptions — for example, unhandled exceptions in thread pool threads.</span></span> <span data-ttu-id="5efa0-106">请参阅本主题后面的[对先前版本的更改](#ChangeFromPreviousVersions)。</span><span class="sxs-lookup"><span data-stu-id="5efa0-106">See [Change from Previous Versions](#ChangeFromPreviousVersions) later in this topic.</span></span>  
  
 <span data-ttu-id="5efa0-107">公共语言运行时为用于控制程序流的某些未经处理的异常提供支持：</span><span class="sxs-lookup"><span data-stu-id="5efa0-107">The common language runtime provides a backstop for certain unhandled exceptions that are used for controlling program flow:</span></span>  
  
- <span data-ttu-id="5efa0-108">由于 <xref:System.Threading.Thread.Abort%2A> 得到调用，因此 <xref:System.Threading.ThreadAbortException> 在线程中抛出。</span><span class="sxs-lookup"><span data-stu-id="5efa0-108">A <xref:System.Threading.ThreadAbortException> is thrown in a thread because <xref:System.Threading.Thread.Abort%2A> was called.</span></span>  
  
- <span data-ttu-id="5efa0-109">由于线程执行时所在的应用域正在卸载，因此 <xref:System.AppDomainUnloadedException> 在线程中抛出。</span><span class="sxs-lookup"><span data-stu-id="5efa0-109">An <xref:System.AppDomainUnloadedException> is thrown in a thread because the application domain in which the thread is executing is being unloaded.</span></span>  
  
- <span data-ttu-id="5efa0-110">公共语言运行时或主机进程通过引发内部异常来终止线程。</span><span class="sxs-lookup"><span data-stu-id="5efa0-110">The common language runtime or a host process terminates the thread by throwing an internal exception.</span></span>  
  
 <span data-ttu-id="5efa0-111">如果公共语言运行时所创建的线程中未处理这些异常中的任何一个，则异常会终止线程，但公共语言运行时不允许该异常继续下去。</span><span class="sxs-lookup"><span data-stu-id="5efa0-111">If any of these exceptions are unhandled in threads created by the common language runtime, the exception terminates the thread, but the common language runtime does not allow the exception to proceed further.</span></span>  
  
 <span data-ttu-id="5efa0-112">如果在主线程或从非托管代码进入运行时的线程中未处理这些异常，则它们会正常继续，并导致应用程序终止。</span><span class="sxs-lookup"><span data-stu-id="5efa0-112">If these exceptions are unhandled in the main thread, or in threads that entered the runtime from unmanaged code, they proceed normally, resulting in termination of the application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5efa0-113">运行时有可能在任何托管代码有机会安装异常处理程序之前，引发一个未经处理的异常。</span><span class="sxs-lookup"><span data-stu-id="5efa0-113">It is possible for the runtime to throw an unhandled exception before any managed code has had a chance to install an exception handler.</span></span> <span data-ttu-id="5efa0-114">即使托管代码没有机会处理此类异常，仍允许异常正常继续。</span><span class="sxs-lookup"><span data-stu-id="5efa0-114">Even though managed code had no chance to handle such an exception, the exception is allowed to proceed naturally.</span></span>  
  
## <a name="exposing-threading-problems-during-development"></a><span data-ttu-id="5efa0-115">在开发过程中暴露线程处理问题</span><span class="sxs-lookup"><span data-stu-id="5efa0-115">Exposing Threading Problems During Development</span></span>  
 <span data-ttu-id="5efa0-116">如果允许线程不给出任何提示就失败（不终止应用程序），则可能无法检测出重大的编程问题。</span><span class="sxs-lookup"><span data-stu-id="5efa0-116">When threads are allowed to fail silently, without terminating the application, serious programming problems can go undetected.</span></span> <span data-ttu-id="5efa0-117">对于长时间运行的服务和其他应用程序，此问题尤为严重。</span><span class="sxs-lookup"><span data-stu-id="5efa0-117">This is a particular problem for services and other applications which run for extended periods.</span></span> <span data-ttu-id="5efa0-118">当线程失败时，程序状态会逐渐损坏。</span><span class="sxs-lookup"><span data-stu-id="5efa0-118">As threads fail, program state gradually becomes corrupted.</span></span> <span data-ttu-id="5efa0-119">应用程序性能可能会降低，应用程序也可能无响应。</span><span class="sxs-lookup"><span data-stu-id="5efa0-119">Application performance may degrade, or the application might become unresponsive.</span></span>  
  
 <span data-ttu-id="5efa0-120">如果允许线程中未经处理的异常正常继续，直到操作系统终止程序为止，将会在开发和测试过程中暴露此类问题。</span><span class="sxs-lookup"><span data-stu-id="5efa0-120">Allowing unhandled exceptions in threads to proceed naturally, until the operating system terminates the program, exposes such problems during development and testing.</span></span> <span data-ttu-id="5efa0-121">程序终止的错误报告支持调试。</span><span class="sxs-lookup"><span data-stu-id="5efa0-121">Error reports on program terminations support debugging.</span></span>  
  
<a name="ChangeFromPreviousVersions"></a>
## <a name="change-from-previous-versions"></a><span data-ttu-id="5efa0-122">对先前版本的更改</span><span class="sxs-lookup"><span data-stu-id="5efa0-122">Change from Previous Versions</span></span>  
 <span data-ttu-id="5efa0-123">最重要的更改发生在托管线程上。</span><span class="sxs-lookup"><span data-stu-id="5efa0-123">The most significant change pertains to managed threads.</span></span> <span data-ttu-id="5efa0-124">在 .NET Framework 1.0 和 1.1 版中，公共语言运行时在下列情况下为未经处理的异常提供支持：</span><span class="sxs-lookup"><span data-stu-id="5efa0-124">In the .NET Framework versions 1.0 and 1.1, the common language runtime provides a backstop for unhandled exceptions in the following situations:</span></span>  
  
- <span data-ttu-id="5efa0-125">在线程池线程中，没有诸如未经处理的异常这样的内容。</span><span class="sxs-lookup"><span data-stu-id="5efa0-125">There is no such thing as an unhandled exception on a thread pool thread.</span></span> <span data-ttu-id="5efa0-126">当某个任务引发了它无法处理的异常时，运行时会将异常堆栈跟踪打印至控制台，然后将线程返回至线程池。</span><span class="sxs-lookup"><span data-stu-id="5efa0-126">When a task throws an exception that it does not handle, the runtime prints the exception stack trace to the console and then returns the thread to the thread pool.</span></span>  
  
- <span data-ttu-id="5efa0-127">在使用 <xref:System.Threading.Thread> 类的 <xref:System.Threading.Thread.Start%2A> 方法创建的线程中，不存在未经处理的异常等现象。</span><span class="sxs-lookup"><span data-stu-id="5efa0-127">There is no such thing as an unhandled exception on a thread created with the <xref:System.Threading.Thread.Start%2A> method of the <xref:System.Threading.Thread> class.</span></span> <span data-ttu-id="5efa0-128">当在此类线程中运行的代码引发它无法处理的异常时，运行时会将异常堆栈跟踪打印至控制台，然后正常终止线程。</span><span class="sxs-lookup"><span data-stu-id="5efa0-128">When code running on such a thread throws an exception that it does not handle, the runtime prints the exception stack trace to the console and then gracefully terminates the thread.</span></span>  
  
- <span data-ttu-id="5efa0-129">在终结器线程中，没有诸如未经处理的异常这样的内容。</span><span class="sxs-lookup"><span data-stu-id="5efa0-129">There is no such thing as an unhandled exception on the finalizer thread.</span></span> <span data-ttu-id="5efa0-130">当终结器引发它无法处理的异常时，运行时会将异常堆栈跟踪打印至控制台，然后允许终结器线程继续运行终结器。</span><span class="sxs-lookup"><span data-stu-id="5efa0-130">When a finalizer throws an exception that it does not handle, the runtime prints the exception stack trace to the console and then allows the finalizer thread to resume running finalizers.</span></span>  
  
 <span data-ttu-id="5efa0-131">托管线程的前台或后台状态不会影响此行为。</span><span class="sxs-lookup"><span data-stu-id="5efa0-131">The foreground or background status of a managed thread does not affect this behavior.</span></span>  
  
 <span data-ttu-id="5efa0-132">对于发自非托管代码的线程中的未经处理的异常，差别更加细微。</span><span class="sxs-lookup"><span data-stu-id="5efa0-132">For unhandled exceptions on threads originating in unmanaged code, the difference is more subtle.</span></span> <span data-ttu-id="5efa0-133">运行时 JIT 附加对话会抢占已通过本机代码的线程中的托管异常或本机异常的操作系统对话。</span><span class="sxs-lookup"><span data-stu-id="5efa0-133">The runtime JIT-attach dialog preempts the operating system dialog for managed exceptions or native exceptions on threads that have passed through native code.</span></span> <span data-ttu-id="5efa0-134">无论什么情况，进程都会终止。</span><span class="sxs-lookup"><span data-stu-id="5efa0-134">The process terminates in all cases.</span></span>  
  
### <a name="migrating-code"></a><span data-ttu-id="5efa0-135">迁移代码</span><span class="sxs-lookup"><span data-stu-id="5efa0-135">Migrating Code</span></span>  
 <span data-ttu-id="5efa0-136">通常，更改将暴露以前无法识别的编程问题，以便修复这些问题。</span><span class="sxs-lookup"><span data-stu-id="5efa0-136">In general, the change will expose previously unrecognized programming problems so that they can be fixed.</span></span> <span data-ttu-id="5efa0-137">但在某些情况下，程序员可能已经利用了运行时支持，例如用于终止线程。</span><span class="sxs-lookup"><span data-stu-id="5efa0-137">In some cases, however, programmers might have taken advantage of the runtime backstop, for example to terminate threads.</span></span> <span data-ttu-id="5efa0-138">根据具体情况，他们应考虑以下迁移策略之一：</span><span class="sxs-lookup"><span data-stu-id="5efa0-138">Depending on the situation, they should consider one of the following migration strategies:</span></span>  
  
- <span data-ttu-id="5efa0-139">重构代码，以便接收到信号时线程能够正常退出。</span><span class="sxs-lookup"><span data-stu-id="5efa0-139">Restructure the code so the thread exits gracefully when a signal is received.</span></span>  
  
- <span data-ttu-id="5efa0-140">使用 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 方法中止线程。</span><span class="sxs-lookup"><span data-stu-id="5efa0-140">Use the <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method to abort the thread.</span></span>  
  
- <span data-ttu-id="5efa0-141">如果线程必须停止才能使进程终止，请将该线程设置为后台线程，这样它就会在进程退出时自动终止。</span><span class="sxs-lookup"><span data-stu-id="5efa0-141">If a thread must be stopped so that process termination can proceed, make the thread a background thread so that it is automatically terminated on process exit.</span></span>  
  
 <span data-ttu-id="5efa0-142">在所有情况下，迁移策略均应遵循异常设计准则。</span><span class="sxs-lookup"><span data-stu-id="5efa0-142">In all cases, the strategy should follow the design guidelines for exceptions.</span></span> <span data-ttu-id="5efa0-143">请参阅[异常设计准则](../design-guidelines/exceptions.md)。</span><span class="sxs-lookup"><span data-stu-id="5efa0-143">See [Design Guidelines for Exceptions](../design-guidelines/exceptions.md).</span></span>  
  
### <a name="application-compatibility-flag"></a><span data-ttu-id="5efa0-144">应用程序兼容性标志</span><span class="sxs-lookup"><span data-stu-id="5efa0-144">Application Compatibility Flag</span></span>  
 <span data-ttu-id="5efa0-145">作为临时的兼容性措施，管理员可以将兼容性标志放在应用程序配置文件的 `<runtime>` 节中。</span><span class="sxs-lookup"><span data-stu-id="5efa0-145">As a temporary compatibility measure, administrators can place a compatibility flag in the `<runtime>` section of the application configuration file.</span></span> <span data-ttu-id="5efa0-146">这会导致公共语言运行时回到 1.0 和 1.1 版的行为。</span><span class="sxs-lookup"><span data-stu-id="5efa0-146">This causes the common language runtime to revert to the behavior of versions 1.0 and 1.1.</span></span>  
  
```xml  
<legacyUnhandledExceptionPolicy enabled="1"/>  
```  
  
## <a name="host-override"></a><span data-ttu-id="5efa0-147">主机重写</span><span class="sxs-lookup"><span data-stu-id="5efa0-147">Host Override</span></span>  
 <span data-ttu-id="5efa0-148">在 .NET Framework 2.0 版中，非托管主机可以使用宿主 API 中的 [ICLRPolicyManager](../../framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) 接口来重写公共语言运行时的默认未经处理的异常。</span><span class="sxs-lookup"><span data-stu-id="5efa0-148">In the .NET Framework version 2.0, an unmanaged host can use the [ICLRPolicyManager](../../framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface in the Hosting API to override the default unhandled exception policy of the common language runtime.</span></span> <span data-ttu-id="5efa0-149">[ICLRPolicyManager::SetUnhandledExceptionPolicy](../../framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) 函数用于设置未经处理的异常的策略。</span><span class="sxs-lookup"><span data-stu-id="5efa0-149">The [ICLRPolicyManager::SetUnhandledExceptionPolicy](../../framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) function is used to set the policy for unhandled exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5efa0-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5efa0-150">See also</span></span>

- [<span data-ttu-id="5efa0-151">托管线程处理基本知识</span><span class="sxs-lookup"><span data-stu-id="5efa0-151">Managed Threading Basics</span></span>](managed-threading-basics.md)

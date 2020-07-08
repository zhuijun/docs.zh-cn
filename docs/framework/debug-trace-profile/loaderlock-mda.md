---
title: loaderLock MDA
description: 查看 .NET 中的 loaderLock 托管调试助手（MDA），它会检测到在持有 Windows OS 加载程序锁的线程上运行托管代码的尝试。
ms.date: 03/30/2017
helpviewer_keywords:
- deadlocks [.NET Framework]
- LoaderLock MDA
- MDAs (managed debugging assistants), loader locks
- managed debugging assistants (MDAs), loader locks
- operating system loader locks
- loader locks
- locks, threads
ms.assetid: 8c10fa02-1b9c-4be5-ab03-451d943ac1ee
ms.openlocfilehash: 055b07a805c5f0b613519d6019950a9b249a4b38
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051616"
---
# <a name="loaderlock-mda"></a><span data-ttu-id="b18ec-103">loaderLock MDA</span><span class="sxs-lookup"><span data-stu-id="b18ec-103">loaderLock MDA</span></span>
<span data-ttu-id="b18ec-104">`loaderLock` 托管调试助手 (MDA) 检测在持有 Microsoft Windows 操作系统加载程序锁的线程上执行托管代码的尝试。</span><span class="sxs-lookup"><span data-stu-id="b18ec-104">The `loaderLock` managed debugging assistant (MDA) detects attempts to execute managed code on a thread that holds the Microsoft Windows operating system loader lock.</span></span>  <span data-ttu-id="b18ec-105">任何此类执行都是非法的，因为这样可能会导致死锁，并导致在操作系统的加载程序已初始化 DLL 之前使用 DLL。</span><span class="sxs-lookup"><span data-stu-id="b18ec-105">Any such execution is illegal because it can lead to deadlocks and to use of DLLs before they have been initialized by the operating system's loader.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="b18ec-106">症状</span><span class="sxs-lookup"><span data-stu-id="b18ec-106">Symptoms</span></span>  
 <span data-ttu-id="b18ec-107">在操作系统的加载程序锁中执行代码时，最常见故障是：线程在尝试调用其它也需要加载程序锁的 Win32 函数时，将产生死锁。</span><span class="sxs-lookup"><span data-stu-id="b18ec-107">The most common failure when executing code inside the operating system's loader lock is that threads will deadlock when attempting to call other Win32 functions that also require the loader lock.</span></span>  <span data-ttu-id="b18ec-108">`LoadLibrary`、`GetProcAddress`、`FreeLibrary` 和 `GetModuleHandle` 就是此类函数的示例。</span><span class="sxs-lookup"><span data-stu-id="b18ec-108">Examples of such functions are `LoadLibrary`, `GetProcAddress`, `FreeLibrary`, and `GetModuleHandle`.</span></span>  <span data-ttu-id="b18ec-109">应用程序可能不会直接调用这些函数；公共语言运行时 (CLR) 可能会将这些函数作为更高级别调用（例如 <xref:System.Reflection.Assembly.Load%2A>）或对平台调用方法的首次调用的结果进行调用。</span><span class="sxs-lookup"><span data-stu-id="b18ec-109">The application might not directly call these functions; the common language runtime (CLR) might call these functions as the result of a higher level call like <xref:System.Reflection.Assembly.Load%2A> or the first call to a platform invoke method.</span></span>  
  
 <span data-ttu-id="b18ec-110">如果一个线程正在等待另一个线程开始或结束，也可能发生死锁。</span><span class="sxs-lookup"><span data-stu-id="b18ec-110">Deadlocks can also occur if a thread is waiting for another thread to start or finish.</span></span>  <span data-ttu-id="b18ec-111">线程开始或结束执行时，必须获取操作系统的加载程序锁，才能向受影响的 DLL 交付事件。</span><span class="sxs-lookup"><span data-stu-id="b18ec-111">When a thread starts or finishes executing, it must acquire the operating system's loader lock to deliver events to affected DLLs.</span></span>  
  
 <span data-ttu-id="b18ec-112">最后，还存在这样的情况：在操作系统的加载程序正确初始化 DLL 之前，调入 DLL。</span><span class="sxs-lookup"><span data-stu-id="b18ec-112">Finally, there are cases where calls into DLLs can occur before those DLLs have been properly initialized by the operating system's loader.</span></span>  <span data-ttu-id="b18ec-113">死锁故障可通过检查死锁中涉及的所有线程的堆栈进行诊断，但这不同于死锁故障，在不使用此 MDA 的情况下很难诊断出未初始化的 DLL 的使用。</span><span class="sxs-lookup"><span data-stu-id="b18ec-113">Unlike the deadlock failures, which can be diagnosed by examining the stacks of all the threads involved in the deadlock, it is very difficult to diagnose the use of uninitialized DLLs without using this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="b18ec-114">原因</span><span class="sxs-lookup"><span data-stu-id="b18ec-114">Cause</span></span>  
 <span data-ttu-id="b18ec-115">除非采用了特殊措施（例如，与 /NOENTRY 链接），否则为 .NET Framework 1.0 或 1.1 版生成的混合托管/非托管 C++ 程序集通常尝试在加载程序锁内执行托管代码\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b18ec-115">Mixed managed/unmanaged C++ assemblies built for .NET Framework versions 1.0 or 1.1 generally attempt to execute managed code inside the loader lock unless special care has been taken, for example, linking with **/NOENTRY**.</span></span>
  
 <span data-ttu-id="b18ec-116">为 .NET Framework 2.0 版生成的混合托管/非托管 C++ 程序集与使用违反操作系统规则的非托管 DLL 的应用程序相同，风险减低，不太容易受到这些问题的影响。</span><span class="sxs-lookup"><span data-stu-id="b18ec-116">Mixed managed/unmanaged C++ assemblies built for .NET Framework version 2.0 are less susceptible to these problems, having the same reduced risk as applications using unmanaged DLLs that violate the operating system's rules.</span></span>  <span data-ttu-id="b18ec-117">例如，如果非托管 DLL 的 `DllMain` 入口点调用`CoCreateInstance` 获取已向 COM 公开的托管对象，结果就是尝试在加载程序锁内执行托管代码。</span><span class="sxs-lookup"><span data-stu-id="b18ec-117">For example, if an unmanaged DLL's `DllMain` entry point calls `CoCreateInstance` to obtain a managed object that has been exposed to COM, the result is an attempt to execute managed code inside the loader lock.</span></span> <span data-ttu-id="b18ec-118">有关 .NET Framework 2.0 及更高版本中加载程序锁问题的详细信息，请参阅[混合程序集的初始化](/cpp/dotnet/initialization-of-mixed-assemblies)。</span><span class="sxs-lookup"><span data-stu-id="b18ec-118">For more information about loader lock issues in the .NET Framework version 2.0 and later, see [Initialization of Mixed Assemblies](/cpp/dotnet/initialization-of-mixed-assemblies).</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="b18ec-119">解决方法</span><span class="sxs-lookup"><span data-stu-id="b18ec-119">Resolution</span></span>  
 <span data-ttu-id="b18ec-120">在 Visual C++ .NET 2002 和 Visual C++ .NET 2003 中，使用 `/clr` 编译器选项编译的 DLL 在加载时可能会发生不确定的死锁；此问题被称为混合 DLL 加载或加载程序锁问题。</span><span class="sxs-lookup"><span data-stu-id="b18ec-120">In Visual C++ .NET 2002 and Visual C++ .NET 2003, DLLs compiled with the `/clr` compiler option could non-deterministically deadlock when loaded; this issue was called the mixed DLL loading or loader lock issue.</span></span> <span data-ttu-id="b18ec-121">在 Visual C++ 2005 及更高版本中，已经从混合 DLL 加载进程中消除了几乎所有的不确定性。</span><span class="sxs-lookup"><span data-stu-id="b18ec-121">In Visual C++ 2005 and later, almost all non-determinism has been removed from the mixed DLL loading process.</span></span> <span data-ttu-id="b18ec-122">但是，还有一些其他情况会导致加载程序锁定发生（肯定会发生这种情况）。</span><span class="sxs-lookup"><span data-stu-id="b18ec-122">However, there are a few remaining scenarios for which loader lock can (deterministically) occur.</span></span> <span data-ttu-id="b18ec-123">有关其余加载程序锁的原因和解决方法的详细介绍，请参阅[混合程序集的初始化](/cpp/dotnet/initialization-of-mixed-assemblies)。</span><span class="sxs-lookup"><span data-stu-id="b18ec-123">For a detailed account of the causes and resolutions for the remaining loader lock issues, see [Initialization of Mixed Assemblies](/cpp/dotnet/initialization-of-mixed-assemblies).</span></span> <span data-ttu-id="b18ec-124">如果该主题没有确定加载程序锁问题，则需要检查线程的堆栈，确定出现加载程序锁的原因以及如何更正此问题。</span><span class="sxs-lookup"><span data-stu-id="b18ec-124">If that topic does not identify your loader lock problem, you have to examine the thread's stack to determine why the loader lock is occurring and how to correct the problem.</span></span> <span data-ttu-id="b18ec-125">查看堆栈跟踪，确定激活此 MDA 的线程。</span><span class="sxs-lookup"><span data-stu-id="b18ec-125">Look at the stack trace for the thread that has activated this MDA.</span></span>  <span data-ttu-id="b18ec-126">该线程在持有操作系统的加载程序锁定的同时，尝试非法调入托管代码。</span><span class="sxs-lookup"><span data-stu-id="b18ec-126">The thread is attempting to illegally call into managed code while holding the operating system's loader lock.</span></span>  <span data-ttu-id="b18ec-127">可能会在堆栈上看到 DLL 的 `DllMain` 或等效的入口点。</span><span class="sxs-lookup"><span data-stu-id="b18ec-127">You will probably see a DLL's `DllMain` or equivalent entry point on the stack.</span></span>  <span data-ttu-id="b18ec-128">操作系统关于可从这样的入口点合法执行的操作的规则具有很多限制。</span><span class="sxs-lookup"><span data-stu-id="b18ec-128">The operating system's rules for what you can legally do from inside such an entry point are quite limited.</span></span>  <span data-ttu-id="b18ec-129">这些规则排除任何托管执行。</span><span class="sxs-lookup"><span data-stu-id="b18ec-129">These rules preclude any managed execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="b18ec-130">对运行时的影响</span><span class="sxs-lookup"><span data-stu-id="b18ec-130">Effect on the Runtime</span></span>  
 <span data-ttu-id="b18ec-131">通常，进程中的若干线程将发生死锁。</span><span class="sxs-lookup"><span data-stu-id="b18ec-131">Typically, several threads inside the process will deadlock.</span></span>  <span data-ttu-id="b18ec-132">其中的某个线程可能是负责执行垃圾回收的线程，因此这种死锁对整个进程具有重大影响。</span><span class="sxs-lookup"><span data-stu-id="b18ec-132">One of those threads is likely to be a thread responsible for performing a garbage collection, so this deadlock can have a major impact on the entire process.</span></span>  <span data-ttu-id="b18ec-133">此外，它将阻止任何需要操作系统的加载程序锁的其他操作，例如加载和卸载程序集或 DLL 以及启动或停止线程。</span><span class="sxs-lookup"><span data-stu-id="b18ec-133">Furthermore, it will prevent any additional operations that require the operating system's loader lock, like loading and unloading assemblies or DLLs and starting or stopping threads.</span></span>  
  
 <span data-ttu-id="b18ec-134">在某些特殊情况下，可能还会在未初始化就被调用的 DLL 中触发访问冲突或类似问题。</span><span class="sxs-lookup"><span data-stu-id="b18ec-134">In some unusual cases, it is also possible for access violations or similar problems to be triggered in DLLs which are called before they have been initialized.</span></span>  
  
## <a name="output"></a><span data-ttu-id="b18ec-135">输出</span><span class="sxs-lookup"><span data-stu-id="b18ec-135">Output</span></span>  
 <span data-ttu-id="b18ec-136">此 MDA 报告正在尝试进行非法托管执行。</span><span class="sxs-lookup"><span data-stu-id="b18ec-136">This MDA reports that an illegal managed execution is being attempted.</span></span>  <span data-ttu-id="b18ec-137">需要检查线程的堆栈，确定出现加载程序锁的原因以及如何更正此问题。</span><span class="sxs-lookup"><span data-stu-id="b18ec-137">You need to examine the thread's stack to determine why the loader lock is occurring and how to correct the problem.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="b18ec-138">配置</span><span class="sxs-lookup"><span data-stu-id="b18ec-138">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loaderLock/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b18ec-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="b18ec-139">See also</span></span>

- [<span data-ttu-id="b18ec-140">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="b18ec-140">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)

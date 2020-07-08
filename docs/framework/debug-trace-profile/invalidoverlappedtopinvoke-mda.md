---
title: invalidOverlappedToPinvoke MDA
description: 查看 .NET 中的 invalidOverlappedToPinvoke 托管调试助手（MDA），这可能在崩溃或无法解释堆损坏期间激活。
ms.date: 03/30/2017
helpviewer_keywords:
- overlapped pointers
- managed debugging assistants (MDAs), overlapped pointers
- invalid overlapped pointer to platform invoke
- InvalidOverlappedToPinvoke MDA
- MDAs (managed debugging assistants), overlapped pointers
- pointers, overlapped
ms.assetid: 28876047-58bd-4fed-9452-c7da346d67c0
ms.openlocfilehash: 162efd55bf636cf2e8698706bd011379f2f6f11f
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051696"
---
# <a name="invalidoverlappedtopinvoke-mda"></a><span data-ttu-id="725d1-103">invalidOverlappedToPinvoke MDA</span><span class="sxs-lookup"><span data-stu-id="725d1-103">invalidOverlappedToPinvoke MDA</span></span>
<span data-ttu-id="725d1-104">当不是在垃圾回收堆上创建的重叠指针传递到特定的 Win32 函数时，会激活 `invalidOverlappedToPinvoke` 托管调试助手（MDA）。</span><span class="sxs-lookup"><span data-stu-id="725d1-104">The `invalidOverlappedToPinvoke` managed debugging assistant (MDA) is activated when an overlapped pointer that was not created on the garbage collection heap is passed to specific Win32 functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="725d1-105">默认情况下，仅当代码中定义了平台调用，并且调试器报告每个方法的 JustMyCode 状态时，才会激活此 MDA。</span><span class="sxs-lookup"><span data-stu-id="725d1-105">By default, this MDA is activated only if the platform invoke call is defined in your code and the debugger reports the JustMyCode status of each method.</span></span> <span data-ttu-id="725d1-106">不理解 JustMyCode 的调试程序（如没有扩展的 MDbg.exe）将不会激活此 MDA。</span><span class="sxs-lookup"><span data-stu-id="725d1-106">A debugger that does not understand JustMyCode (such as MDbg.exe with no extensions) will not activate this MDA.</span></span> <span data-ttu-id="725d1-107">通过使用配置文件和显式设置 .mda 配置文件中的 `justMyCode="false"` 可以为这些调试程序启用此 MDA `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`)。</span><span class="sxs-lookup"><span data-stu-id="725d1-107">This MDA can be enabled for those debuggers by using a configuration file and explicitly settting `justMyCode="false"` in the .mda.config file `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="725d1-108">症状</span><span class="sxs-lookup"><span data-stu-id="725d1-108">Symptoms</span></span>  
 <span data-ttu-id="725d1-109">故障或无法解释的堆损坏。</span><span class="sxs-lookup"><span data-stu-id="725d1-109">Crashes or unexplainable heap corruptions.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="725d1-110">原因</span><span class="sxs-lookup"><span data-stu-id="725d1-110">Cause</span></span>  
 <span data-ttu-id="725d1-111">不是在垃圾回收堆上创建的重叠指针被传递到特定的操作系统函数。</span><span class="sxs-lookup"><span data-stu-id="725d1-111">An overlapped pointer that was not created on the garbage collection heap is passed to specific operating system functions.</span></span>  
  
 <span data-ttu-id="725d1-112">下表显示了此 MDA 跟踪的函数。</span><span class="sxs-lookup"><span data-stu-id="725d1-112">The following table shows the functions that this MDA tracks.</span></span>  
  
|<span data-ttu-id="725d1-113">模块</span><span class="sxs-lookup"><span data-stu-id="725d1-113">Module</span></span>|<span data-ttu-id="725d1-114">函数</span><span class="sxs-lookup"><span data-stu-id="725d1-114">Function</span></span>|  
|------------|--------------|  
|<span data-ttu-id="725d1-115">HttpApi.dll</span><span class="sxs-lookup"><span data-stu-id="725d1-115">HttpApi.dll</span></span>|`HttpReceiveHttpRequest`|  
|<span data-ttu-id="725d1-116">IpHlpApi.dll</span><span class="sxs-lookup"><span data-stu-id="725d1-116">IpHlpApi.dll</span></span>|`NotifyAddrChange`|  
|<span data-ttu-id="725d1-117">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="725d1-117">kernel32.dll</span></span>|`ReadFile`|  
|<span data-ttu-id="725d1-118">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="725d1-118">kernel32.dll</span></span>|`ReadFileEx`|  
|<span data-ttu-id="725d1-119">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="725d1-119">kernel32.dll</span></span>|`WriteFile`|  
|<span data-ttu-id="725d1-120">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="725d1-120">kernel32.dll</span></span>|`WriteFileEx`|  
|<span data-ttu-id="725d1-121">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="725d1-121">kernel32.dll</span></span>|`ReadDirectoryChangesW`|  
|<span data-ttu-id="725d1-122">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="725d1-122">kernel32.dll</span></span>|`PostQueuedCompletionStatus`|  
|<span data-ttu-id="725d1-123">MSWSock.dll</span><span class="sxs-lookup"><span data-stu-id="725d1-123">MSWSock.dll</span></span>|`ConnectEx`|  
|<span data-ttu-id="725d1-124">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="725d1-124">WS2_32.dll</span></span>|`WSASend`|  
|<span data-ttu-id="725d1-125">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="725d1-125">WS2_32.dll</span></span>|`WSASendTo`|  
|<span data-ttu-id="725d1-126">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="725d1-126">WS2_32.dll</span></span>|`WSARecv`|  
|<span data-ttu-id="725d1-127">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="725d1-127">WS2_32.dll</span></span>|`WSARecvFrom`|  
|<span data-ttu-id="725d1-128">MQRT.dll</span><span class="sxs-lookup"><span data-stu-id="725d1-128">MQRT.dll</span></span>|`MQReceiveMessage`|  
  
 <span data-ttu-id="725d1-129">在这种情况下，堆损坏的可能性很大，因为进行调用的 <xref:System.AppDomain> 可能会卸载。</span><span class="sxs-lookup"><span data-stu-id="725d1-129">The potential for heap corruption is high for this condition because the <xref:System.AppDomain> making the call might unload.</span></span> <span data-ttu-id="725d1-130">如果 <xref:System.AppDomain> 卸载，应用程序代码将释放重叠指针的内存，导致操作完成时发生损坏，或者代码将泄漏内存，导致以后发生问题。</span><span class="sxs-lookup"><span data-stu-id="725d1-130">If the <xref:System.AppDomain> unloads, the application code will either free the memory for the overlapped pointer, causing corruption when the operation finishes, or the code will leak the memory, causing difficulties later.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="725d1-131">解决方法</span><span class="sxs-lookup"><span data-stu-id="725d1-131">Resolution</span></span>  
 <span data-ttu-id="725d1-132">使用 <xref:System.Threading.Overlapped> 对象，调用 <xref:System.Threading.Overlapped.Pack%2A> 方法以获取可以传递给函数的 <xref:System.Threading.NativeOverlapped> 结构。</span><span class="sxs-lookup"><span data-stu-id="725d1-132">Use an <xref:System.Threading.Overlapped> object, calling the <xref:System.Threading.Overlapped.Pack%2A> method to get a <xref:System.Threading.NativeOverlapped> structure that can be passed to the function.</span></span> <span data-ttu-id="725d1-133">如果卸载 <xref:System.AppDomain>，在释放指针之前，CLR 等待异步操作完成。</span><span class="sxs-lookup"><span data-stu-id="725d1-133">If the <xref:System.AppDomain> unloads, the CLR waits until the asynchronous operation completes before freeing the pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="725d1-134">对运行时的影响</span><span class="sxs-lookup"><span data-stu-id="725d1-134">Effect on the Runtime</span></span>  
 <span data-ttu-id="725d1-135">此 MDA 对 CLR 无任何影响。</span><span class="sxs-lookup"><span data-stu-id="725d1-135">This MDA had no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="725d1-136">输出</span><span class="sxs-lookup"><span data-stu-id="725d1-136">Output</span></span>  
 <span data-ttu-id="725d1-137">以下是来自此 MDA 的输出示例。</span><span class="sxs-lookup"><span data-stu-id="725d1-137">The following is an example of output from this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the Win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlapped structure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="725d1-138">配置</span><span class="sxs-lookup"><span data-stu-id="725d1-138">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidOverlappedToPinvoke/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="725d1-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="725d1-139">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="725d1-140">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="725d1-140">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="725d1-141">互操作封送处理</span><span class="sxs-lookup"><span data-stu-id="725d1-141">Interop Marshaling</span></span>](../interop/interop-marshaling.md)

---
title: invalidApartmentStateChange MDA
description: 了解 .NET 中的 invalidApartmentStateChange 托管调试助手（MDA），如果 COM 单元状态有问题，则会激活该助手。
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid apartment state
- managed debugging assistants (MDAs), invalid apartment state
- InvalidApartmentStateChange MDA
- invalid apartment state changes
- threading [.NET Framework], apartment states
- apartment states
- threading [.NET Framework], managed debugging assistants
- COM apartment states
ms.assetid: e56fb9df-5286-4be7-b313-540c4d876cd7
ms.openlocfilehash: c6f7b6a5e450d4167946d22b2ada268ea2b0135f
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051822"
---
# <a name="invalidapartmentstatechange-mda"></a><span data-ttu-id="2a877-103">invalidApartmentStateChange MDA</span><span class="sxs-lookup"><span data-stu-id="2a877-103">invalidApartmentStateChange MDA</span></span>
<span data-ttu-id="2a877-104">`invalidApartmentStateChange` 托管调试助手 (MDS) 通过以下两种问题中的任何一种激活：</span><span class="sxs-lookup"><span data-stu-id="2a877-104">The `invalidApartmentStateChange` managed debugging assistant (MDS) is activated by either of two problems:</span></span>  
  
- <span data-ttu-id="2a877-105">尝试将已由 COM 初始化的线程的 COM 单元状态更改为不同的单元状态。</span><span class="sxs-lookup"><span data-stu-id="2a877-105">An attempt is made to change the COM apartment state of a thread that has already been initialized by COM to a different apartment state.</span></span>  
  
- <span data-ttu-id="2a877-106">线程的 COM 单元状态意外更改。</span><span class="sxs-lookup"><span data-stu-id="2a877-106">The COM apartment state of a thread changes unexpectedly.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="2a877-107">症状</span><span class="sxs-lookup"><span data-stu-id="2a877-107">Symptoms</span></span>  
  
- <span data-ttu-id="2a877-108">线程的 COM 单元状态不符合请求。</span><span class="sxs-lookup"><span data-stu-id="2a877-108">A thread's COM apartment state is not what was requested.</span></span> <span data-ttu-id="2a877-109">这可能造成用于已有线程模型的 COM 组件的代理不同于现有代理。</span><span class="sxs-lookup"><span data-stu-id="2a877-109">This may cause proxies to be used for COM components that have a threading model different from the current one.</span></span> <span data-ttu-id="2a877-110">进而可能导致在通过未设置为跨单元封送的接口调用 COM 对象时，引发 <xref:System.InvalidCastException>。</span><span class="sxs-lookup"><span data-stu-id="2a877-110">This in turn may cause an <xref:System.InvalidCastException> to be thrown when calling the COM object through interfaces that are not set up for cross-apartment marshaling.</span></span>  
  
- <span data-ttu-id="2a877-111">线程的 COM 单元状态不同于预期。</span><span class="sxs-lookup"><span data-stu-id="2a877-111">The COM apartment state of the thread is different than expected.</span></span> <span data-ttu-id="2a877-112">这可能造成调用[运行时可调用包装器](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) 时，出现 <xref:System.Runtime.InteropServices.COMException>、RPC_E_WRONG_THREAD 返回 HRESULT 以及 <xref:System.InvalidCastException>。</span><span class="sxs-lookup"><span data-stu-id="2a877-112">This can cause a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD as well as a <xref:System.InvalidCastException> when making calls on a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="2a877-113">这也可能造成部分单线程 COM 组件由多个线程同时访问，进而导致损坏或数据丢失。</span><span class="sxs-lookup"><span data-stu-id="2a877-113">This can also cause some single-threaded COM components to be accessed by multiple threads at the same time, which can lead to corruption or data loss.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="2a877-114">原因</span><span class="sxs-lookup"><span data-stu-id="2a877-114">Cause</span></span>  
  
- <span data-ttu-id="2a877-115">该线程之前已初始化为不同的 COM 单元状态。</span><span class="sxs-lookup"><span data-stu-id="2a877-115">The thread was previously initialized to a different COM apartment state.</span></span> <span data-ttu-id="2a877-116">请注意，可显式或隐式设置线程的单元状态。</span><span class="sxs-lookup"><span data-stu-id="2a877-116">Note that the apartment state of a thread can be set either explicitly or implicitly.</span></span> <span data-ttu-id="2a877-117">显式操作包括 <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> 属性以及 <xref:System.Threading.Thread.SetApartmentState%2A> 和 <xref:System.Threading.Thread.TrySetApartmentState%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="2a877-117">The explicit operations include the <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> property and the <xref:System.Threading.Thread.SetApartmentState%2A> and <xref:System.Threading.Thread.TrySetApartmentState%2A> methods.</span></span> <span data-ttu-id="2a877-118">通过 <xref:System.Threading.Thread.Start%2A> 方法创建的线程可隐式设置为 <xref:System.Threading.ApartmentState.MTA>，除非 <xref:System.Threading.Thread.SetApartmentState%2A> 在线程创建之前就已调用。</span><span class="sxs-lookup"><span data-stu-id="2a877-118">A thread created using the <xref:System.Threading.Thread.Start%2A> method is implicitly set to <xref:System.Threading.ApartmentState.MTA> unless <xref:System.Threading.Thread.SetApartmentState%2A> is called before the thread is started.</span></span> <span data-ttu-id="2a877-119">应用程序主线程同样可隐式初始化为 <xref:System.Threading.ApartmentState.MTA>，除非在主方法上指定了 <xref:System.STAThreadAttribute> 属性。</span><span class="sxs-lookup"><span data-stu-id="2a877-119">The main thread of the application is also implicitly initialized to <xref:System.Threading.ApartmentState.MTA> unless the <xref:System.STAThreadAttribute> attribute is specified on the main method.</span></span>  
  
- <span data-ttu-id="2a877-120">在线程上调用具有不同并发模型的 `CoUninitialize` 方法（或 `CoInitializeEx` 方法）。</span><span class="sxs-lookup"><span data-stu-id="2a877-120">The `CoUninitialize` method (or the `CoInitializeEx` method) with a different concurrency model is called on the thread.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="2a877-121">解决方法</span><span class="sxs-lookup"><span data-stu-id="2a877-121">Resolution</span></span>  
 <span data-ttu-id="2a877-122">在单元状态开始执行前对其进行设置，或将 <xref:System.STAThreadAttribute> 属性或 <xref:System.MTAThreadAttribute> 属性应用到应用程序的主方法。</span><span class="sxs-lookup"><span data-stu-id="2a877-122">Set the apartment state of the thread before it begins executing, or apply either the <xref:System.STAThreadAttribute> attribute or the <xref:System.MTAThreadAttribute> attribute to the main method of the application.</span></span>  
  
 <span data-ttu-id="2a877-123">对于第二种结果，理想情况下，需要将调用 `CoUninitialize` 方法的代码修改为延迟调用，直到线程即将终止并且该线程停止使用 RCW 及其基础 COM 组件。</span><span class="sxs-lookup"><span data-stu-id="2a877-123">For the second cause, ideally, the code that calls the `CoUninitialize` method should be modified to delay the call until the thread is about to terminate and there are no RCWs and their underlying COM components still in use by the thread.</span></span> <span data-ttu-id="2a877-124">但是，如果无法修改调用 `CoUninitialize` 方法的代码，则未采用此方法进行初始化的线程不能使用任何 RCW。</span><span class="sxs-lookup"><span data-stu-id="2a877-124">However, if it is not possible to modify the code that calls the `CoUninitialize` method, then no RCWs should be used from threads that are uninitialized in this way.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="2a877-125">对运行时的影响</span><span class="sxs-lookup"><span data-stu-id="2a877-125">Effect on the Runtime</span></span>  
 <span data-ttu-id="2a877-126">此 MDA 对 CLR 无任何影响。</span><span class="sxs-lookup"><span data-stu-id="2a877-126">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="2a877-127">输出</span><span class="sxs-lookup"><span data-stu-id="2a877-127">Output</span></span>  
 <span data-ttu-id="2a877-128">当前线程的 COM 单元状态和试图应用的代码状态。</span><span class="sxs-lookup"><span data-stu-id="2a877-128">The COM apartment state of the current thread, and the state that the code was attempting to apply.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="2a877-129">配置</span><span class="sxs-lookup"><span data-stu-id="2a877-129">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="2a877-130">示例</span><span class="sxs-lookup"><span data-stu-id="2a877-130">Example</span></span>  
 <span data-ttu-id="2a877-131">以下代码示例展示了一种可激活该 MDA 的情况。</span><span class="sxs-lookup"><span data-stu-id="2a877-131">The following code example demonstrates a situation that can activate this MDA.</span></span>  
  
```csharp
using System.Threading;  
namespace ApartmentStateMDA  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Thread.CurrentThread.SetApartmentState(ApartmentState.STA);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a877-132">请参阅</span><span class="sxs-lookup"><span data-stu-id="2a877-132">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="2a877-133">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="2a877-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="2a877-134">互操作封送处理</span><span class="sxs-lookup"><span data-stu-id="2a877-134">Interop Marshaling</span></span>](../interop/interop-marshaling.md)

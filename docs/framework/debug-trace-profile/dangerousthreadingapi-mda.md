---
title: dangerousThreadingAPI MDA
description: 查看 dangerousThreadingAPI 托管调试助手（MDA），当在当前线程以外的线程上调用 "挂起" 时，它将被激活。
ms.date: 03/30/2017
helpviewer_keywords:
- suspending threads
- DangerousThreadingAPI MDA
- managed debugging assistants (MDAs), dangerous threading operations
- threading [.NET Framework], suspending
- MDAs (managed debugging assistants), dangerous threading operations
- Suspend method
- threading [.NET Framework], managed debugging assistants
ms.assetid: 3e5efbc5-92e4-4229-b31f-ce368a1adb96
ms.openlocfilehash: 9069ccb6f106c83db94f88bc464bc0888d28586c
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416000"
---
# <a name="dangerousthreadingapi-mda"></a><span data-ttu-id="9fab8-103">dangerousThreadingAPI MDA</span><span class="sxs-lookup"><span data-stu-id="9fab8-103">dangerousThreadingAPI MDA</span></span>
<span data-ttu-id="9fab8-104">如果在当前线程以外的线程上调用 <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> 方法，将激活 `dangerousThreadingAPI` 托管调试助手 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="9fab8-104">The `dangerousThreadingAPI` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> method is called on a thread other than the current thread.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="9fab8-105">症状</span><span class="sxs-lookup"><span data-stu-id="9fab8-105">Symptoms</span></span>  
 <span data-ttu-id="9fab8-106">应用程序无响应或无限期挂起。</span><span class="sxs-lookup"><span data-stu-id="9fab8-106">An application is unresponsive or hangs indefinitely.</span></span> <span data-ttu-id="9fab8-107">系统数据或应用程序数据可能暂时处于不可预知状态，甚至在应用程序关闭之后也可能处于不可预知状态。</span><span class="sxs-lookup"><span data-stu-id="9fab8-107">System or application data might be left in an unpredictable state temporarily or even after an application has been shut down.</span></span> <span data-ttu-id="9fab8-108">某些操作未按预期完成。</span><span class="sxs-lookup"><span data-stu-id="9fab8-108">Some operations are not completing as expected.</span></span>  
  
 <span data-ttu-id="9fab8-109">由于问题固有的随机性，因此问题的具体表现可能有极大差异。</span><span class="sxs-lookup"><span data-stu-id="9fab8-109">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="9fab8-110">原因</span><span class="sxs-lookup"><span data-stu-id="9fab8-110">Cause</span></span>  
 <span data-ttu-id="9fab8-111">一个线程使用 <xref:System.Threading.Thread.Suspend%2A> 方法将另一线程异步挂起。</span><span class="sxs-lookup"><span data-stu-id="9fab8-111">A thread is asynchronously suspended by another thread using the <xref:System.Threading.Thread.Suspend%2A> method.</span></span> <span data-ttu-id="9fab8-112">无法确定何时挂起另一个可能正在操作的线程才安全。</span><span class="sxs-lookup"><span data-stu-id="9fab8-112">There is no way to determine when it is safe to suspend another thread which might be in the middle of an operation.</span></span> <span data-ttu-id="9fab8-113">挂起线程会导致数据损坏或不变体中断。</span><span class="sxs-lookup"><span data-stu-id="9fab8-113">Suspending the thread can result in the corruption of data or the breaking of invariants.</span></span> <span data-ttu-id="9fab8-114">如果一个线程处于挂起状态且从未使用 <xref:System.Threading.Thread.Resume%2A> 方法恢复，则应用程序可能会无限期挂起且应用程序数据可能会遭到损坏。</span><span class="sxs-lookup"><span data-stu-id="9fab8-114">Should a thread be placed into a suspended state and never resumed using the <xref:System.Threading.Thread.Resume%2A> method, the application can hang indefinitely and possibly damage application data.</span></span> <span data-ttu-id="9fab8-115">这些方法已被标记为已过时。</span><span class="sxs-lookup"><span data-stu-id="9fab8-115">These methods have been marked as obsolete.</span></span>  
  
 <span data-ttu-id="9fab8-116">如果由目标线程保留同步基元，则挂起期间仍然保留这些同步基元。</span><span class="sxs-lookup"><span data-stu-id="9fab8-116">If synchronization primitives are held by the target thread, they remain held during suspension.</span></span> <span data-ttu-id="9fab8-117">如果另一线程（例如执行 <xref:System.Threading.Thread.Suspend%2A> 的线程）尝试获取对该基元的锁定，则这可能会导致死锁。</span><span class="sxs-lookup"><span data-stu-id="9fab8-117">This can lead to deadlocks should another thread, for example the thread performing the <xref:System.Threading.Thread.Suspend%2A>, attempt to acquire a lock on the primitive.</span></span> <span data-ttu-id="9fab8-118">在此情况下，该问题将自身表示为死锁。</span><span class="sxs-lookup"><span data-stu-id="9fab8-118">In this situation, the problem manifests itself as a deadlock.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="9fab8-119">解决方法</span><span class="sxs-lookup"><span data-stu-id="9fab8-119">Resolution</span></span>  
 <span data-ttu-id="9fab8-120">避免需使用 <xref:System.Threading.Thread.Suspend%2A> 和 <xref:System.Threading.Thread.Resume%2A> 的设计。</span><span class="sxs-lookup"><span data-stu-id="9fab8-120">Avoid designs that require the use of <xref:System.Threading.Thread.Suspend%2A> and <xref:System.Threading.Thread.Resume%2A>.</span></span> <span data-ttu-id="9fab8-121">对于线程之间的协作，请使用 <xref:System.Threading.Monitor>、<xref:System.Threading.ReaderWriterLock>、<xref:System.Threading.Mutex> 或 C# `lock` 语句等同步基元。</span><span class="sxs-lookup"><span data-stu-id="9fab8-121">For cooperation between threads, use synchronization primitives such as <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, or the C# `lock` statement.</span></span> <span data-ttu-id="9fab8-122">如果必须使用这些方法，则请缩短时间范围并最大限度地减少线程处于挂起状态时执行的代码量。</span><span class="sxs-lookup"><span data-stu-id="9fab8-122">If you must use these methods, reduce the window of time and minimize the amount of code that executes while the thread is in a suspended state.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="9fab8-123">对运行时的影响</span><span class="sxs-lookup"><span data-stu-id="9fab8-123">Effect on the Runtime</span></span>  
 <span data-ttu-id="9fab8-124">此 MDA 对 CLR 无任何影响。</span><span class="sxs-lookup"><span data-stu-id="9fab8-124">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="9fab8-125">它只报告有关危险线程处理操作的数据。</span><span class="sxs-lookup"><span data-stu-id="9fab8-125">It only reports data about dangerous threading operations.</span></span>  
  
## <a name="output"></a><span data-ttu-id="9fab8-126">输出</span><span class="sxs-lookup"><span data-stu-id="9fab8-126">Output</span></span>  
 <span data-ttu-id="9fab8-127">MDA 识别导致其激活的危险线程处理方法。</span><span class="sxs-lookup"><span data-stu-id="9fab8-127">The MDA identifies the dangerous threading method that caused it to be activated.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="9fab8-128">配置</span><span class="sxs-lookup"><span data-stu-id="9fab8-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="9fab8-129">示例</span><span class="sxs-lookup"><span data-stu-id="9fab8-129">Example</span></span>  
 <span data-ttu-id="9fab8-130">以下代码示例演示对造成 `dangerousThreadingAPI` 激活的 <xref:System.Threading.Thread.Suspend%2A> 方法的调用。</span><span class="sxs-lookup"><span data-stu-id="9fab8-130">The following code example demonstrates a call to the <xref:System.Threading.Thread.Suspend%2A> method that causes the activation of the `dangerousThreadingAPI`.</span></span>  
  
```csharp
using System.Threading;  
void FireMda()  
{  
Thread t = new Thread(delegate() { Thread.Sleep(1000); });  
    t.Start();  
    // The following line activates the MDA.  
    t.Suspend();
    t.Resume();  
    t.Join();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="9fab8-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="9fab8-131">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="9fab8-132">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="9fab8-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="9fab8-133">lock 语句</span><span class="sxs-lookup"><span data-stu-id="9fab8-133">lock Statement</span></span>](../../csharp/language-reference/keywords/lock-statement.md)

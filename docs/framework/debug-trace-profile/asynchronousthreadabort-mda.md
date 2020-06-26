---
title: asynchronousThreadAbort MDA
description: 查看在线程尝试将异步中止放入另一个线程时，如何激活 asynchronousThreadAbort 托管调试助手（MDA）。
ms.date: 03/30/2017
helpviewer_keywords:
- asynchronous thread aborts
- AsynchronousThreadAbort MDA
- managed debugging assistants (MDAs), asynchronous thread aborts
- threading [.NET Framework], managed debugging assistants
- MDAs (managed debugging assistants), asynchronous thread aborts
ms.assetid: 9ebe40b2-d703-421e-8660-984acc42bfe0
ms.openlocfilehash: 469372d57d9c21198353d171fec16458691eb25d
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415662"
---
# <a name="asynchronousthreadabort-mda"></a><span data-ttu-id="af36d-103">asynchronousThreadAbort MDA</span><span class="sxs-lookup"><span data-stu-id="af36d-103">asynchronousThreadAbort MDA</span></span>
<span data-ttu-id="af36d-104">当线程尝试将异步中止引入到另一个线程时，将激活 `asynchronousThreadAbort` 托管调试助手 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="af36d-104">The `asynchronousThreadAbort` managed debugging assistant (MDA) is activated when a thread attempts to introduce an asynchronous abort into another thread.</span></span> <span data-ttu-id="af36d-105">同步线程中止不会激活 `asynchronousThreadAbort` MDA。</span><span class="sxs-lookup"><span data-stu-id="af36d-105">Synchronous thread aborts do not activate the `asynchronousThreadAbort` MDA.</span></span>

## <a name="symptoms"></a><span data-ttu-id="af36d-106">症状</span><span class="sxs-lookup"><span data-stu-id="af36d-106">Symptoms</span></span>
 <span data-ttu-id="af36d-107">当主应用程序线程被中止时，应用程序会崩溃，并出现未处理的 <xref:System.Threading.ThreadAbortException>。</span><span class="sxs-lookup"><span data-stu-id="af36d-107">An application crashes with an unhandled <xref:System.Threading.ThreadAbortException> when the main application thread is aborted.</span></span> <span data-ttu-id="af36d-108">如果继续执行应用程序，可能会引起比应用程序崩溃更糟糕的后果，可能导致进一步的数据损坏。</span><span class="sxs-lookup"><span data-stu-id="af36d-108">If the application were to continue to execute, the consequences might be worse than the application crashing, possibly resulting in further data corruption.</span></span>

 <span data-ttu-id="af36d-109">应为原子操作的操作可能在部分完成后被中断，使应用程序数据处于不可预测的状态。</span><span class="sxs-lookup"><span data-stu-id="af36d-109">Operations meant to be atomic have likely been interrupted after partial completion, leaving application data in an unpredictable state.</span></span> <span data-ttu-id="af36d-110">在代码执行中，<xref:System.Threading.ThreadAbortException> 可能从看似随机的点生成，通常在不应该出现此异常的位置生成。</span><span class="sxs-lookup"><span data-stu-id="af36d-110">A <xref:System.Threading.ThreadAbortException> can be generated from seemingly random points in the execution of code, often in places from which an exception is not expected to arise.</span></span> <span data-ttu-id="af36d-111">代码可能无法处理此类异常，从而导致损坏状态。</span><span class="sxs-lookup"><span data-stu-id="af36d-111">The code might not be capable of handling such an exception, resulting in a corrupt state.</span></span>

 <span data-ttu-id="af36d-112">由于问题固有的随机性，因此问题的具体表现可能有极大差异。</span><span class="sxs-lookup"><span data-stu-id="af36d-112">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>

## <a name="cause"></a><span data-ttu-id="af36d-113">原因</span><span class="sxs-lookup"><span data-stu-id="af36d-113">Cause</span></span>
 <span data-ttu-id="af36d-114">一个线程中的代码对目标线程调用 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 方法来引入异步线程中止。</span><span class="sxs-lookup"><span data-stu-id="af36d-114">Code in one thread called the <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method on a target thread to introduce an asynchronous thread abort.</span></span> <span data-ttu-id="af36d-115">线程中止是异步的，因为对 <xref:System.Threading.Thread.Abort%2A> 进行调用的代码运行在与中止操作的目标不同的线程上。</span><span class="sxs-lookup"><span data-stu-id="af36d-115">The thread abort is asynchronous because the code that makes the call to <xref:System.Threading.Thread.Abort%2A> is running on a different thread than the target of the abort operation.</span></span> <span data-ttu-id="af36d-116">同步线程中止不应导致此问题，因为执行 <xref:System.Threading.Thread.Abort%2A> 的线程应只在应用程序状态一致的安全检查点执行此操作。</span><span class="sxs-lookup"><span data-stu-id="af36d-116">Synchronous thread aborts should not cause a problem because the thread performing the <xref:System.Threading.Thread.Abort%2A> should have done so only at a safe checkpoint where application state is consistent.</span></span>

 <span data-ttu-id="af36d-117">异步线程中止出现问题，因为它们在目标线程的执行过程中是在不可预测的点被处理的。</span><span class="sxs-lookup"><span data-stu-id="af36d-117">Asynchronous thread aborts present a problem because they are processed at unpredictable points in the target thread's execution.</span></span> <span data-ttu-id="af36d-118">若要避免此问题，所编写的代码（为了在可能以此方式被中止的线程上运行）需要在几乎每个代码行上处理 <xref:System.Threading.ThreadAbortException>，负责将应用程序数据放回到一致状态。</span><span class="sxs-lookup"><span data-stu-id="af36d-118">To avoid this, code written to run on a thread that might be aborted in this manner would need to handle a <xref:System.Threading.ThreadAbortException> at almost every line of code, taking care to put application data back into a consistent state.</span></span> <span data-ttu-id="af36d-119">在编写代码时考虑到此问题，或编写防止可能出现的所有情况的代码都是不现实的。</span><span class="sxs-lookup"><span data-stu-id="af36d-119">It is not realistic to expect code to be written with this problem in mind or to write code that protects against all possible circumstances.</span></span>

 <span data-ttu-id="af36d-120">尽管对非托管代码和 `finally` 块的调用将不会被异步中止，但在从任一这些类别中退出时将被立即中止。</span><span class="sxs-lookup"><span data-stu-id="af36d-120">Calls into unmanaged code and `finally` blocks will not be aborted asynchronously but immediately upon exit from one of these categories.</span></span>

 <span data-ttu-id="af36d-121">由于问题固有的随机性，因此可能很难确定问题的原因。</span><span class="sxs-lookup"><span data-stu-id="af36d-121">The cause might be difficult to determine due to the randomness inherent to the problem.</span></span>

## <a name="resolution"></a><span data-ttu-id="af36d-122">解决方法</span><span class="sxs-lookup"><span data-stu-id="af36d-122">Resolution</span></span>
 <span data-ttu-id="af36d-123">避免需要使用异步线程中止的代码设计。</span><span class="sxs-lookup"><span data-stu-id="af36d-123">Avoid code design that requires the use of asynchronous thread aborts.</span></span> <span data-ttu-id="af36d-124">有几种更适合用于中断目标线程的方法，这些方法无需调用 <xref:System.Threading.Thread.Abort%2A>。</span><span class="sxs-lookup"><span data-stu-id="af36d-124">There are several approaches more appropriate for interruption of a target thread that do not require a call to <xref:System.Threading.Thread.Abort%2A>.</span></span> <span data-ttu-id="af36d-125">最安全的方法是引入一种机制，如向目标线程发出信号以请求中断的一个公用属性。</span><span class="sxs-lookup"><span data-stu-id="af36d-125">The safest is to introduce a mechanism, such as a common property, that signals the target thread to request an interrupt.</span></span> <span data-ttu-id="af36d-126">此目标线程会在某些安全检查点检查信号。</span><span class="sxs-lookup"><span data-stu-id="af36d-126">The target thread checks the signal at certain safe checkpoints.</span></span> <span data-ttu-id="af36d-127">如果它发现已请求中断，则可以正常关闭。</span><span class="sxs-lookup"><span data-stu-id="af36d-127">If it notices that an interrupt has been requested, it can shut down gracefully.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="af36d-128">对运行时的影响</span><span class="sxs-lookup"><span data-stu-id="af36d-128">Effect on the Runtime</span></span>
 <span data-ttu-id="af36d-129">此 MDA 对 CLR 无任何影响。</span><span class="sxs-lookup"><span data-stu-id="af36d-129">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="af36d-130">它只报告有关异步线程中止的数据。</span><span class="sxs-lookup"><span data-stu-id="af36d-130">It only reports data about asynchronous thread aborts.</span></span>

## <a name="output"></a><span data-ttu-id="af36d-131">输出</span><span class="sxs-lookup"><span data-stu-id="af36d-131">Output</span></span>
 <span data-ttu-id="af36d-132">MDA 报告执行中止的线程 ID 以及作为此中止目标的线程 ID。</span><span class="sxs-lookup"><span data-stu-id="af36d-132">The MDA reports the ID of the thread performing the abort and the ID of the thread that is the target of the abort.</span></span> <span data-ttu-id="af36d-133">这两项绝对不会相同，因为这被限制为异步中止。</span><span class="sxs-lookup"><span data-stu-id="af36d-133">These will never be the same because this is limited to asynchronous aborts.</span></span>

## <a name="configuration"></a><span data-ttu-id="af36d-134">配置</span><span class="sxs-lookup"><span data-stu-id="af36d-134">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <asynchronousThreadAbort />
  </assistants>
</mdaConfig>
```

## <a name="example"></a><span data-ttu-id="af36d-135">示例</span><span class="sxs-lookup"><span data-stu-id="af36d-135">Example</span></span>
 <span data-ttu-id="af36d-136">激活 `asynchronousThreadAbort` MDA 仅需要在单独运行的线程上调用 <xref:System.Threading.Thread.Abort%2A>。</span><span class="sxs-lookup"><span data-stu-id="af36d-136">Activating the `asynchronousThreadAbort` MDA requires only a call to <xref:System.Threading.Thread.Abort%2A> on a separate running thread.</span></span> <span data-ttu-id="af36d-137">请考虑在线程启动功能的内容是一组更复杂操作（这些操作可能被中止在任意点处中断）的情况下的后果。</span><span class="sxs-lookup"><span data-stu-id="af36d-137">Consider the consequences if the contents of the thread start function were a set of more complex operations which might be interrupted at any arbitrary point by the abort.</span></span>

```csharp
using System.Threading;
void FireMda()
{
    Thread t = new Thread(delegate() { Thread.Sleep(1000); });
    t.Start();
    // The following line activates the MDA.
    t.Abort();
    t.Join();
}
```

## <a name="see-also"></a><span data-ttu-id="af36d-138">请参阅</span><span class="sxs-lookup"><span data-stu-id="af36d-138">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="af36d-139">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="af36d-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)

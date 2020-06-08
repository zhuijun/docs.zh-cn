---
title: 如何：使用 SpinWait 实现两阶段等待操作
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinWait, how to synchronize two-phase wait
ms.assetid: b2ac4e4a-051a-4f65-b4b9-f8e103aff195
ms.openlocfilehash: 4b2bc79a7b652c34334d5a78d9c9af328993ff44
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279201"
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a><span data-ttu-id="787dd-102">如何：使用 SpinWait 实现两阶段等待操作</span><span class="sxs-lookup"><span data-stu-id="787dd-102">How to: Use SpinWait to Implement a Two-Phase Wait Operation</span></span>
<span data-ttu-id="787dd-103">下面的示例展示了如何使用 <xref:System.Threading.SpinWait?displayProperty=nameWithType> 对象实现两阶段等待操作。</span><span class="sxs-lookup"><span data-stu-id="787dd-103">The following example shows how to use a <xref:System.Threading.SpinWait?displayProperty=nameWithType> object to implement a two-phase wait operation.</span></span> <span data-ttu-id="787dd-104">在第一阶段中，同步对象 `Latch` 旋转几个周期，同时检查锁是否可用。</span><span class="sxs-lookup"><span data-stu-id="787dd-104">In the first phase, the synchronization object, a `Latch`, spins for a few cycles while it checks whether the lock has become available.</span></span> <span data-ttu-id="787dd-105">在第二阶段中，如果锁可用，`Wait` 方法返回结果，而不使用 <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> 执行等待操作；否则，`Wait` 执行等待操作。</span><span class="sxs-lookup"><span data-stu-id="787dd-105">In the second phase, if the lock becomes available, then the `Wait` method returns without using the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> to perform its wait; otherwise, `Wait` performs the wait.</span></span>  
  
## <a name="example"></a><span data-ttu-id="787dd-106">示例</span><span class="sxs-lookup"><span data-stu-id="787dd-106">Example</span></span>  
 <span data-ttu-id="787dd-107">此示例展示了非常基本的 Latch 同步基元实现。</span><span class="sxs-lookup"><span data-stu-id="787dd-107">This example shows a very basic implementation of a Latch synchronization primitive.</span></span> <span data-ttu-id="787dd-108">如果应缩短等待时间，可以使用此数据结构。</span><span class="sxs-lookup"><span data-stu-id="787dd-108">You can use this data structure when wait times are expected to be very short.</span></span> <span data-ttu-id="787dd-109">此示例只为了方便本文演示。</span><span class="sxs-lookup"><span data-stu-id="787dd-109">This example is for demonstration purposes only.</span></span> <span data-ttu-id="787dd-110">如果需要在程序中实现 Latch 类型功能，请考虑使用 <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="787dd-110">If you require latch-type functionality in your program, consider using <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 <span data-ttu-id="787dd-111">Latch 使用 <xref:System.Threading.SpinWait> 对象进行原位旋转，仅持续到下一次调用 `SpinOnce` 导致 <xref:System.Threading.SpinWait> 生成线程的时间片。</span><span class="sxs-lookup"><span data-stu-id="787dd-111">The latch uses the <xref:System.Threading.SpinWait> object to spin in place only until the next call to `SpinOnce` causes the <xref:System.Threading.SpinWait> to yield the time slice of the thread.</span></span> <span data-ttu-id="787dd-112">此时，Latch 对 <xref:System.Threading.ManualResetEvent> 调用 <xref:System.Threading.WaitHandle.WaitOne%2A>，并传入剩余的超时值，促使自己的上下文切换。</span><span class="sxs-lookup"><span data-stu-id="787dd-112">At that point, the latch causes its own context switch by calling <xref:System.Threading.WaitHandle.WaitOne%2A> on the <xref:System.Threading.ManualResetEvent> and passing in the remainder of the time-out value.</span></span>  
  
 <span data-ttu-id="787dd-113">日志输出展示了 Latch 能够通过获取锁（而不是使用 <xref:System.Threading.ManualResetEvent>）提升性能的频率。</span><span class="sxs-lookup"><span data-stu-id="787dd-113">The logging output shows how often the Latch was able to increase performance by acquiring the lock without using the <xref:System.Threading.ManualResetEvent>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="787dd-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="787dd-114">See also</span></span>

- [<span data-ttu-id="787dd-115">SpinWait</span><span class="sxs-lookup"><span data-stu-id="787dd-115">SpinWait</span></span>](spinwait.md)
- [<span data-ttu-id="787dd-116">线程处理对象和功能</span><span class="sxs-lookup"><span data-stu-id="787dd-116">Threading Objects and Features</span></span>](threading-objects-and-features.md)

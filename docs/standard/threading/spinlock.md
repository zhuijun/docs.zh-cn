---
title: SpinLock
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
ms.openlocfilehash: a5202be5e3055702954ad7a1565999ad2496eaea
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291118"
---
# <a name="spinlock"></a><span data-ttu-id="f9ac6-102">SpinLock</span><span class="sxs-lookup"><span data-stu-id="f9ac6-102">SpinLock</span></span>
<span data-ttu-id="f9ac6-103"><xref:System.Threading.SpinLock> 结构是低级互斥同步基元，在等待获取锁时旋转。</span><span class="sxs-lookup"><span data-stu-id="f9ac6-103">The <xref:System.Threading.SpinLock> structure is a low-level, mutual-exclusion synchronization primitive that spins while it waits to acquire a lock.</span></span> <span data-ttu-id="f9ac6-104">在多核计算机上，如果应缩短等待时间且争用最少，那么 <xref:System.Threading.SpinLock> 的性能优于其他种类的锁。</span><span class="sxs-lookup"><span data-stu-id="f9ac6-104">On multicore computers, when wait times are expected to be short and when contention is minimal, <xref:System.Threading.SpinLock> can perform better than other kinds of locks.</span></span> <span data-ttu-id="f9ac6-105">不过，建议仅在通过分析确定 <xref:System.Threading.Monitor?displayProperty=nameWithType> 方法或 <xref:System.Threading.Interlocked> 方法显著降低程序性能时，才使用 <xref:System.Threading.SpinLock>。</span><span class="sxs-lookup"><span data-stu-id="f9ac6-105">However, we recommend that you use <xref:System.Threading.SpinLock> only when you determine by profiling that the <xref:System.Threading.Monitor?displayProperty=nameWithType> method or the <xref:System.Threading.Interlocked> methods are significantly slowing the performance of your program.</span></span>  
  
 <span data-ttu-id="f9ac6-106">即使尚未获取锁，<xref:System.Threading.SpinLock> 也可能会生成线程的时间片。</span><span class="sxs-lookup"><span data-stu-id="f9ac6-106"><xref:System.Threading.SpinLock> may yield the time slice of the thread even if it has not yet acquired the lock.</span></span> <span data-ttu-id="f9ac6-107">这样做是为了避免线程优先级反转，并让垃圾回收器能够取得进展。</span><span class="sxs-lookup"><span data-stu-id="f9ac6-107">It does this to avoid thread-priority inversion, and to enable the garbage collector to make progress.</span></span> <span data-ttu-id="f9ac6-108">使用 <xref:System.Threading.SpinLock> 时，请确保没有线程可以将锁保留比较久的时间，也没有线程可以在保留锁时受阻止。</span><span class="sxs-lookup"><span data-stu-id="f9ac6-108">When you use a <xref:System.Threading.SpinLock>, ensure that no thread can hold the lock for more than a very brief time span, and that no thread can block while it holds the lock.</span></span>  
  
 <span data-ttu-id="f9ac6-109">由于 SpinLock 是值类型，因此如果希望两个副本引用的是同一个锁，必须通过引用显式传递它。</span><span class="sxs-lookup"><span data-stu-id="f9ac6-109">Because SpinLock is a value type, you must explicitly pass it by reference if you intend the two copies to refer to the same lock.</span></span>  
  
 <span data-ttu-id="f9ac6-110">若要详细了解如何使用此类型，请参阅 <xref:System.Threading.SpinLock?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="f9ac6-110">For more information about how to use this type, see <xref:System.Threading.SpinLock?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f9ac6-111">有关示例，请参阅[如何：使用 SpinLock 执行低级同步](how-to-use-spinlock-for-low-level-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="f9ac6-111">For an example, see [How to: Use SpinLock for Low-Level Synchronization](how-to-use-spinlock-for-low-level-synchronization.md).</span></span>  
  
 <span data-ttu-id="f9ac6-112"><xref:System.Threading.SpinLock> 支持*线程*-*跟踪*模式，可以在开发阶段使用此模式，有助于跟踪在特定时间保留锁的线程。</span><span class="sxs-lookup"><span data-stu-id="f9ac6-112"><xref:System.Threading.SpinLock> supports a *thread*-*tracking* mode that you can use during the development phase to help track the thread that is holding the lock at a specific time.</span></span> <span data-ttu-id="f9ac6-113">虽然线程跟踪模式对于调试非常有用，但建议在程序的发行版中禁用它，因为它可能会降低性能。</span><span class="sxs-lookup"><span data-stu-id="f9ac6-113">Thread-tracking mode is very useful for debugging, but we recommend that you turn it off in the release version of your program because it may slow performance.</span></span> <span data-ttu-id="f9ac6-114">有关详细信息，请参阅[如何：在 SpinLock 中启用线程跟踪模式](how-to-enable-thread-tracking-mode-in-spinlock.md)。</span><span class="sxs-lookup"><span data-stu-id="f9ac6-114">For more information, see [How to: Enable Thread-Tracking Mode in SpinLock](how-to-enable-thread-tracking-mode-in-spinlock.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9ac6-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f9ac6-115">See also</span></span>

- [<span data-ttu-id="f9ac6-116">线程处理对象和功能</span><span class="sxs-lookup"><span data-stu-id="f9ac6-116">Threading Objects and Features</span></span>](threading-objects-and-features.md)

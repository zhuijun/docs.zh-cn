---
title: 计划线程
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], scheduling
- scheduling threads
ms.assetid: 67e4a0eb-3095-4ea7-b20f-908faa476277
ms.openlocfilehash: fea809168bf2f4f888466f87259497660afd13be
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291144"
---
# <a name="scheduling-threads"></a><span data-ttu-id="cebff-102">计划线程</span><span class="sxs-lookup"><span data-stu-id="cebff-102">Scheduling threads</span></span>

<span data-ttu-id="cebff-103">每个线程都会分配有线程优先级。</span><span class="sxs-lookup"><span data-stu-id="cebff-103">Every thread has a thread priority assigned to it.</span></span> <span data-ttu-id="cebff-104">在公共语言运行时内创建的线程初始分配有 <xref:System.Threading.ThreadPriority.Normal?displayProperty=nameWithType> 的优先级。</span><span class="sxs-lookup"><span data-stu-id="cebff-104">Threads created within the common language runtime are initially assigned the priority of <xref:System.Threading.ThreadPriority.Normal?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cebff-105">在运行时外部创建的线程保留有在进入托管环境前的优先级。</span><span class="sxs-lookup"><span data-stu-id="cebff-105">Threads created outside the runtime retain the priority they had before they entered the managed environment.</span></span> <span data-ttu-id="cebff-106">若要获取或设置任意线程的优先级，可以使用 <xref:System.Threading.Thread.Priority?displayProperty=nameWithType> 属性。</span><span class="sxs-lookup"><span data-stu-id="cebff-106">You can get or set the priority of any thread with the <xref:System.Threading.Thread.Priority?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="cebff-107">线程根据优先级被排入执行计划。</span><span class="sxs-lookup"><span data-stu-id="cebff-107">Threads are scheduled for execution based on their priority.</span></span> <span data-ttu-id="cebff-108">即使线程是在运行时内执行，操作系统也会为所有线程分配处理器时间片。</span><span class="sxs-lookup"><span data-stu-id="cebff-108">Even though threads are executing within the runtime, all threads are assigned processor time slices by the operating system.</span></span> <span data-ttu-id="cebff-109">用于确定线程执行顺序的计划算法详细信息因各个操作系统而异。</span><span class="sxs-lookup"><span data-stu-id="cebff-109">The details of the scheduling algorithm used to determine the order in which threads are executed varies with each operating system.</span></span> <span data-ttu-id="cebff-110">在一些操作系统下，（在可以执行的线程中）优先级最高的线程始终都被计划为第一个运行。</span><span class="sxs-lookup"><span data-stu-id="cebff-110">Under some operating systems, the thread with the highest priority (of those threads that can be executed) is always scheduled to run first.</span></span> <span data-ttu-id="cebff-111">如果有多个线程的优先级相同，计划程序会遍历具有此优先级的全部线程，为每个线程分配固定的执行时间片。</span><span class="sxs-lookup"><span data-stu-id="cebff-111">If multiple threads with the same priority are all available, the scheduler cycles through the threads at that priority, giving each thread a fixed time slice in which to execute.</span></span> <span data-ttu-id="cebff-112">只要有更高优先级的线程可供运行，就不会执行优先级较低的线程。</span><span class="sxs-lookup"><span data-stu-id="cebff-112">As long as a thread with a higher priority is available to run, lower priority threads do not get to execute.</span></span> <span data-ttu-id="cebff-113">如果在给定优先级没有其他任何可运行的线程，计划程序会转到下一个较低优先级，并计划执行具有此优先级的线程。</span><span class="sxs-lookup"><span data-stu-id="cebff-113">When there are no more runnable threads at a given priority, the scheduler moves to the next lower priority and schedules the threads at that priority for execution.</span></span> <span data-ttu-id="cebff-114">如果较高优先级的线程变得可运行，就会强占优先级较低的线程，并获准重新执行。</span><span class="sxs-lookup"><span data-stu-id="cebff-114">If a higher priority thread becomes runnable, the lower priority thread is preempted and the higher priority thread is allowed to execute once again.</span></span> <span data-ttu-id="cebff-115">除此之外，如果应用的用户界面在前台和后台之间转换，操作系统还可以动态调整线程优先级。</span><span class="sxs-lookup"><span data-stu-id="cebff-115">On top of all that, the operating system can also adjust thread priorities dynamically as an application's user interface is moved between foreground and background.</span></span> <span data-ttu-id="cebff-116">其他操作系统可能会选择使用不同的计划算法。</span><span class="sxs-lookup"><span data-stu-id="cebff-116">Other operating systems might choose to use a different scheduling algorithm.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cebff-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cebff-117">See also</span></span>

- [<span data-ttu-id="cebff-118">使用线程和线程处理</span><span class="sxs-lookup"><span data-stu-id="cebff-118">Using Threads and Threading</span></span>](using-threads-and-threading.md)
- [<span data-ttu-id="cebff-119">Windows 中的托管和非托管线程</span><span class="sxs-lookup"><span data-stu-id="cebff-119">Managed and Unmanaged Threading in Windows</span></span>](managed-and-unmanaged-threading-in-windows.md)

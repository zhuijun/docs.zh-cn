---
title: 托管线程处理基本知识
description: 点击链接查看其他关于托管线程的文章，其中包括异常、同步数据、前台线程和后台线程、本地存储等主题。
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
ms.openlocfilehash: d4a4ceabf29bd0f6f537e59ba477f9da686b1ef5
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769088"
---
# <a name="managed-threading-basics"></a><span data-ttu-id="3598d-103">托管线程处理基本知识</span><span class="sxs-lookup"><span data-stu-id="3598d-103">Managed threading basics</span></span>

<span data-ttu-id="3598d-104">本节的前五个主题有助于确定何时使用托管线程处理，并介绍一些基本功能。</span><span class="sxs-lookup"><span data-stu-id="3598d-104">The first five topics of this section are designed to help you determine when to use managed threading and to explain some basic features.</span></span> <span data-ttu-id="3598d-105">若要了解提供附加功能的类，请参阅[线程处理对象和功能](threading-objects-and-features.md)和[同步基元概述](overview-of-synchronization-primitives.md)。</span><span class="sxs-lookup"><span data-stu-id="3598d-105">For information on classes that provide additional features, see [Threading Objects and Features](threading-objects-and-features.md) and [Overview of Synchronization Primitives](overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="3598d-106">本节中的剩余主题涵盖了高级主题，其中包括托管线程与 Windows 操作系统的交互。</span><span class="sxs-lookup"><span data-stu-id="3598d-106">The rest of the topics in this section cover advanced topics, including the interaction of managed threading with the Windows operating system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3598d-107">在 .NET Framework 4 中，任务并行库和 PLINQ 提供了多线程程序中的任务并行和数据并行 API。</span><span class="sxs-lookup"><span data-stu-id="3598d-107">In the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs for task and data parallelism in multi-threaded programs.</span></span> <span data-ttu-id="3598d-108">有关详细信息，请参阅[并行编程](../parallel-programming/index.md)。</span><span class="sxs-lookup"><span data-stu-id="3598d-108">For more information, see [Parallel Programming](../parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3598d-109">本节内容</span><span class="sxs-lookup"><span data-stu-id="3598d-109">In this section</span></span>

 [<span data-ttu-id="3598d-110">线程与线程处理</span><span class="sxs-lookup"><span data-stu-id="3598d-110">Threads and Threading</span></span>](threads-and-threading.md)  
 <span data-ttu-id="3598d-111">介绍了多个线程的优缺点，并概述了可能创建线程或使用线程池线程的方案。</span><span class="sxs-lookup"><span data-stu-id="3598d-111">Discusses the advantages and drawbacks of multiple threads, and outlines the scenarios in which you might create threads or use thread pool threads.</span></span>  
  
 [<span data-ttu-id="3598d-112">托管线程中的异常</span><span class="sxs-lookup"><span data-stu-id="3598d-112">Exceptions in Managed Threads</span></span>](exceptions-in-managed-threads.md)  
 <span data-ttu-id="3598d-113">介绍了对于不同版本的 .NET Framework，线程中未经处理的异常行为，特别是导致应用终止的情况。</span><span class="sxs-lookup"><span data-stu-id="3598d-113">Describes the behavior of unhandled exceptions in threads for different versions of the .NET Framework, in particular the situations in which they result in termination of the application.</span></span>  
  
 [<span data-ttu-id="3598d-114">为多线程处理同步数据</span><span class="sxs-lookup"><span data-stu-id="3598d-114">Synchronizing Data for Multithreading</span></span>](synchronizing-data-for-multithreading.md)  
 <span data-ttu-id="3598d-115">介绍了在用于多个线程的类中同步数据的策略。</span><span class="sxs-lookup"><span data-stu-id="3598d-115">Describes strategies for synchronizing data in classes that will be used with multiple threads.</span></span>  
  
 [<span data-ttu-id="3598d-116">前台和后台线程</span><span class="sxs-lookup"><span data-stu-id="3598d-116">Foreground and Background Threads</span></span>](foreground-and-background-threads.md)  
 <span data-ttu-id="3598d-117">介绍了前台和后台线程的区别。</span><span class="sxs-lookup"><span data-stu-id="3598d-117">Explains the differences between foreground and background threads.</span></span>  
  
 [<span data-ttu-id="3598d-118">Windows 中的托管和非托管线程</span><span class="sxs-lookup"><span data-stu-id="3598d-118">Managed and Unmanaged Threading in Windows</span></span>](managed-and-unmanaged-threading-in-windows.md)  
 <span data-ttu-id="3598d-119">介绍了托管和非托管线程的关系，列出了 Windows 线程 API 的相当托管版本，并讨论了 COM 单元和托管线程的交互。</span><span class="sxs-lookup"><span data-stu-id="3598d-119">Discusses the relationship between managed and unmanaged threading, lists managed equivalents for Windows threading APIs, and discusses the interaction of COM apartments and managed threads.</span></span>  
  
 [<span data-ttu-id="3598d-120">线程本地存储：线程相关的静态字段和数据槽</span><span class="sxs-lookup"><span data-stu-id="3598d-120">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>](thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 <span data-ttu-id="3598d-121">介绍了线程相对存储机制。</span><span class="sxs-lookup"><span data-stu-id="3598d-121">Describes thread-relative storage mechanisms.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3598d-122">参考</span><span class="sxs-lookup"><span data-stu-id="3598d-122">Reference</span></span>

 <xref:System.Threading.Thread>  
 <span data-ttu-id="3598d-123">提供**线程**类的参考文档，无论该类是来自托管代码还是在托管应用程序中创建的，它都表示一个托管线程。</span><span class="sxs-lookup"><span data-stu-id="3598d-123">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="3598d-124">提供了一种安全实现多线程处理与用户界面对象的方式。</span><span class="sxs-lookup"><span data-stu-id="3598d-124">Provides a safe way to implement multithreading in conjunction with user-interface objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3598d-125">相关章节</span><span class="sxs-lookup"><span data-stu-id="3598d-125">Related sections</span></span>

 [<span data-ttu-id="3598d-126">同步基元概述</span><span class="sxs-lookup"><span data-stu-id="3598d-126">Overview of Synchronization Primitives</span></span>](overview-of-synchronization-primitives.md)  
 <span data-ttu-id="3598d-127">介绍了用于同步多个线程活动的托管类。</span><span class="sxs-lookup"><span data-stu-id="3598d-127">Describes the managed classes used to synchronize the activities of multiple threads.</span></span>  
  
 [<span data-ttu-id="3598d-128">托管线程处理的最佳做法</span><span class="sxs-lookup"><span data-stu-id="3598d-128">Managed Threading Best Practices</span></span>](managed-threading-best-practices.md)  
 <span data-ttu-id="3598d-129">介绍了常见的多线程处理问题，以及避免这些问题发生的策略。</span><span class="sxs-lookup"><span data-stu-id="3598d-129">Describes common problems with multithreading and strategies for avoiding problems.</span></span>  
  
 [<span data-ttu-id="3598d-130">并行编程</span><span class="sxs-lookup"><span data-stu-id="3598d-130">Parallel Programming</span></span>](../parallel-programming/index.md)  
 <span data-ttu-id="3598d-131">介绍了任务并行库和 PLINQ，它们极大地简化了创建异步和多线程 .NET Framework 应用的工作。</span><span class="sxs-lookup"><span data-stu-id="3598d-131">Describes the Task Parallel Library and PLINQ, which greatly simplify the work of creating asynchronous and multi-threaded .NET Framework applications.</span></span>

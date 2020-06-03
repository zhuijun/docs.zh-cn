---
title: 托管线程处理
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
ms.openlocfilehash: e4c19b664e8fc040fdc4a284b30f6104d676088d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279149"
---
# <a name="managed-threading"></a><span data-ttu-id="e2a88-102">托管线程处理</span><span class="sxs-lookup"><span data-stu-id="e2a88-102">Managed Threading</span></span>
<span data-ttu-id="e2a88-103">无论是要为具有一个还是多个处理器的计算机进行开发，你都希望应用程序能够提供响应最为迅速的用户交互，即使应用程序当前正在执行其他操作，也不例外。</span><span class="sxs-lookup"><span data-stu-id="e2a88-103">Whether you are developing for computers with one processor or several, you want your application to provide the most responsive interaction with the user, even if the application is currently doing other work.</span></span> <span data-ttu-id="e2a88-104">使用多线程执行是让应用程序一直迅速响应用户的最有效方式，同时也是在用户事件之间或在用户事件期间使用处理器的最有效方式。</span><span class="sxs-lookup"><span data-stu-id="e2a88-104">Using multiple threads of execution is one of the most powerful ways to keep your application responsive to the user and at the same time make use of the processor in between or even during user events.</span></span> <span data-ttu-id="e2a88-105">虽然本部分介绍的是线程基本概念，但将会重点介绍托管线程概念和如何使用托管线程。</span><span class="sxs-lookup"><span data-stu-id="e2a88-105">While this section introduces the basic concepts of threading, it focuses on managed threading concepts and using managed threading.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e2a88-106">自 .NET Framework 4 起，由于出现了 <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 类、[并行 LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md)、<xref:System.Collections.Concurrent?displayProperty=nameWithType> 命名空间中的新并发集合类以及基于任务（而非线程）概念的新编程模型，多线程编程大大得到了简化。</span><span class="sxs-lookup"><span data-stu-id="e2a88-106">Starting with the .NET Framework 4, multithreaded programming is greatly simplified with the <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> classes, [Parallel LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md), new concurrent collection classes in the <xref:System.Collections.Concurrent?displayProperty=nameWithType> namespace, and a new programming model that is based on the concept of tasks rather than threads.</span></span> <span data-ttu-id="e2a88-107">有关详细信息，请参阅[并行编程](../parallel-programming/index.md)。</span><span class="sxs-lookup"><span data-stu-id="e2a88-107">For more information, see [Parallel Programming](../parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e2a88-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="e2a88-108">In This Section</span></span>  
 [<span data-ttu-id="e2a88-109">托管线程处理基本知识</span><span class="sxs-lookup"><span data-stu-id="e2a88-109">Managed Threading Basics</span></span>](managed-threading-basics.md)  
 <span data-ttu-id="e2a88-110">概述了托管线程以及何时使用多线程。</span><span class="sxs-lookup"><span data-stu-id="e2a88-110">Provides an overview of managed threading and discusses when to use multiple threads.</span></span>  
  
 [<span data-ttu-id="e2a88-111">使用线程和线程处理</span><span class="sxs-lookup"><span data-stu-id="e2a88-111">Using Threads and Threading</span></span>](using-threads-and-threading.md)  
 <span data-ttu-id="e2a88-112">介绍了如何创建、启动、暂停、恢复和中止线程。</span><span class="sxs-lookup"><span data-stu-id="e2a88-112">Explains how to create, start, pause, resume, and abort threads.</span></span>  
  
 [<span data-ttu-id="e2a88-113">托管线程处理的最佳做法</span><span class="sxs-lookup"><span data-stu-id="e2a88-113">Managed Threading Best Practices</span></span>](managed-threading-best-practices.md)  
 <span data-ttu-id="e2a88-114">介绍了同步级别、如何避免死锁和争用条件，以及其他线程问题。</span><span class="sxs-lookup"><span data-stu-id="e2a88-114">Discusses levels of synchronization, how to avoid deadlocks and race conditions, and other threading issues.</span></span>  
  
 [<span data-ttu-id="e2a88-115">线程处理对象和功能</span><span class="sxs-lookup"><span data-stu-id="e2a88-115">Threading Objects and Features</span></span>](threading-objects-and-features.md)  
 <span data-ttu-id="e2a88-116">介绍了可用于同步在不同线程上访问的线程活动和对象数据的托管类，并概述了线程池线程。</span><span class="sxs-lookup"><span data-stu-id="e2a88-116">Describes the managed classes you can use to synchronize the activities of threads and the data of objects accessed on different threads, and provides an overview of thread pool threads.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e2a88-117">参考</span><span class="sxs-lookup"><span data-stu-id="e2a88-117">Reference</span></span>  
 <xref:System.Threading>  
 <span data-ttu-id="e2a88-118">收录了用于使用和同步托管线程的类。</span><span class="sxs-lookup"><span data-stu-id="e2a88-118">Contains classes for using and synchronizing managed threads.</span></span>  
  
 <xref:System.Collections.Concurrent>  
 <span data-ttu-id="e2a88-119">收录了可安全用于多线程的集合类。</span><span class="sxs-lookup"><span data-stu-id="e2a88-119">Contains collection classes that are safe for use with multiple threads.</span></span>  
  
 <xref:System.Threading.Tasks>  
 <span data-ttu-id="e2a88-120">收录了用于创建和计划并发处理任务的类。</span><span class="sxs-lookup"><span data-stu-id="e2a88-120">Contains classes for creating and scheduling concurrent processing tasks.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e2a88-121">相关章节</span><span class="sxs-lookup"><span data-stu-id="e2a88-121">Related Sections</span></span>  
 [<span data-ttu-id="e2a88-122">应用程序域</span><span class="sxs-lookup"><span data-stu-id="e2a88-122">Application Domains</span></span>](../../framework/app-domains/application-domains.md)  
 <span data-ttu-id="e2a88-123">概述了应用程序域及其在公共语言基础结构中的应用。</span><span class="sxs-lookup"><span data-stu-id="e2a88-123">Provides an overview of application domains and their use by the Common Language Infrastructure.</span></span>  
  
 [<span data-ttu-id="e2a88-124">异步文件 I/O</span><span class="sxs-lookup"><span data-stu-id="e2a88-124">Asynchronous File I/O</span></span>](../io/asynchronous-file-i-o.md)  
 <span data-ttu-id="e2a88-125">描述异步 I/O 的性能优势和基本操作。</span><span class="sxs-lookup"><span data-stu-id="e2a88-125">Describes the performance advantages and basic operation of asynchronous I/O.</span></span>  
  
 [<span data-ttu-id="e2a88-126">基于任务的异步模式 (TAP)</span><span class="sxs-lookup"><span data-stu-id="e2a88-126">Task-based Asynchronous Pattern (TAP)</span></span>](../asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 <span data-ttu-id="e2a88-127">概述了推荐的 .NET 异步编程模式。</span><span class="sxs-lookup"><span data-stu-id="e2a88-127">Provides an overview of the recommended pattern for asynchronous programming in .NET.</span></span>  
  
 [<span data-ttu-id="e2a88-128">使用异步方式调用同步方法</span><span class="sxs-lookup"><span data-stu-id="e2a88-128">Calling Synchronous Methods Asynchronously</span></span>](../asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="e2a88-129">介绍了如何使用委托的内置功能对线程池线程调用方法。</span><span class="sxs-lookup"><span data-stu-id="e2a88-129">Explains how to call methods on thread pool threads using built-in features of delegates.</span></span>  
  
 [<span data-ttu-id="e2a88-130">并行编程</span><span class="sxs-lookup"><span data-stu-id="e2a88-130">Parallel Programming</span></span>](../parallel-programming/index.md)  
 <span data-ttu-id="e2a88-131">介绍了并行编程库，其简化了在应用程序中使用多线程。</span><span class="sxs-lookup"><span data-stu-id="e2a88-131">Describes the parallel programming libraries, which simplify the use of multiple threads in applications.</span></span>  
  
 [<span data-ttu-id="e2a88-132">并行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="e2a88-132">Parallel LINQ (PLINQ)</span></span>](../parallel-programming/introduction-to-plinq.md)  
 <span data-ttu-id="e2a88-133">介绍了为利用多个处理器而并行运行查询的系统。</span><span class="sxs-lookup"><span data-stu-id="e2a88-133">Describes a system for running queries in parallel, to take advantage of multiple processors.</span></span>

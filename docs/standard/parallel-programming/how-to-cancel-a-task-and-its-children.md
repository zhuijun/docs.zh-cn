---
title: 如何：取消任务及其子级
description: 查看如何在 .NET 中取消任务及其子级的示例。 这些示例涵盖从取消创建任务到通知任务取消的步骤。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to cancel
ms.assetid: 08574301-8331-4719-ad50-9cf7f6ff3048
ms.openlocfilehash: 66daf00680b65aace1ce6367761e3ed81596d33b
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662675"
---
# <a name="how-to-cancel-a-task-and-its-children"></a><span data-ttu-id="1fefe-104">如何：取消任务及其子级</span><span class="sxs-lookup"><span data-stu-id="1fefe-104">How to: Cancel a Task and Its Children</span></span>
<span data-ttu-id="1fefe-105">这些示例展示了如何执行下列任务：</span><span class="sxs-lookup"><span data-stu-id="1fefe-105">These examples show how to perform the following tasks:</span></span>  
  
1. <span data-ttu-id="1fefe-106">创建并启动可取消任务。</span><span class="sxs-lookup"><span data-stu-id="1fefe-106">Create and start a cancelable task.</span></span>  
  
2. <span data-ttu-id="1fefe-107">将取消令牌传递给用户委托，并视需要传递给任务实例。</span><span class="sxs-lookup"><span data-stu-id="1fefe-107">Pass a cancellation token to your user delegate and optionally to the task instance.</span></span>  
  
3. <span data-ttu-id="1fefe-108">注意并响应用户委托中的取消请求。</span><span class="sxs-lookup"><span data-stu-id="1fefe-108">Notice and respond to the cancellation request in your user delegate.</span></span>  
  
4. <span data-ttu-id="1fefe-109">（可选）注意已取消任务的调用线程。</span><span class="sxs-lookup"><span data-stu-id="1fefe-109">Optionally notice on the calling thread that the task was canceled.</span></span>  
  
 <span data-ttu-id="1fefe-110">调用线程不会强制结束任务，只会提示取消请求已发出。</span><span class="sxs-lookup"><span data-stu-id="1fefe-110">The calling thread does not forcibly end the task; it only signals that cancellation is requested.</span></span> <span data-ttu-id="1fefe-111">如果任务已在运行，至于怎样才能注意请求并适当响应，取决于用户委托的选择。</span><span class="sxs-lookup"><span data-stu-id="1fefe-111">If the task is already running, it is up to the user delegate to notice the request and respond appropriately.</span></span> <span data-ttu-id="1fefe-112">如果取消请求在任务运行前发出，用户委托绝不会执行，任务对象的状态会转换为“已取消”。</span><span class="sxs-lookup"><span data-stu-id="1fefe-112">If cancellation is requested before the task runs, then the user delegate is never executed and the task object transitions into the Canceled state.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fefe-113">示例</span><span class="sxs-lookup"><span data-stu-id="1fefe-113">Example</span></span>  
 <span data-ttu-id="1fefe-114">此示例展示了如何终止 <xref:System.Threading.Tasks.Task> 及其子级，以响应取消请求。</span><span class="sxs-lookup"><span data-stu-id="1fefe-114">This example shows how to terminate a <xref:System.Threading.Tasks.Task> and its children in response to a cancellation request.</span></span> <span data-ttu-id="1fefe-115">还会演示，当用户委托通过引发 <xref:System.Threading.Tasks.TaskCanceledException> 终止时，调用线程可以选择使用 <xref:System.Threading.Tasks.Task.Wait%2A> 方法或 <xref:System.Threading.Tasks.Task.WaitAll%2A> 方法来等待任务完成。</span><span class="sxs-lookup"><span data-stu-id="1fefe-115">It also shows that when a user delegate terminates by throwing a <xref:System.Threading.Tasks.TaskCanceledException>, the calling thread can optionally use the <xref:System.Threading.Tasks.Task.Wait%2A> method or <xref:System.Threading.Tasks.Task.WaitAll%2A> method to wait for the tasks to finish.</span></span> <span data-ttu-id="1fefe-116">在这种情况下，必须使用 `try/catch` 块来处理调用线程上的异常。</span><span class="sxs-lookup"><span data-stu-id="1fefe-116">In this case, you must use a `try/catch` block to handle the exceptions on the calling thread.</span></span>  
  
 [!code-csharp[TPL_Cancellation#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/cancel1.cs#04)]
 [!code-vb[TPL_Cancellation#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/cancel1.vb#04)]  
  
 <span data-ttu-id="1fefe-117"><xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 类与基于 <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> 和 <xref:System.Threading.CancellationToken?displayProperty=nameWithType> 类型的取消模型完全集成。</span><span class="sxs-lookup"><span data-stu-id="1fefe-117">The <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> class is fully integrated with the cancellation model that is based on the <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> and <xref:System.Threading.CancellationToken?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="1fefe-118">有关详细信息，请参阅[托管线程中的取消](../threading/cancellation-in-managed-threads.md)和[任务取消](task-cancellation.md)。</span><span class="sxs-lookup"><span data-stu-id="1fefe-118">For more information, see [Cancellation in Managed Threads](../threading/cancellation-in-managed-threads.md) and [Task Cancellation](task-cancellation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fefe-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="1fefe-119">See also</span></span>

- <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType>
- <xref:System.Threading.CancellationToken?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>
- [<span data-ttu-id="1fefe-120">基于任务的异步编程</span><span class="sxs-lookup"><span data-stu-id="1fefe-120">Task-based Asynchronous Programming</span></span>](task-based-asynchronous-programming.md)
- [<span data-ttu-id="1fefe-121">附加和分离的子任务</span><span class="sxs-lookup"><span data-stu-id="1fefe-121">Attached and Detached Child Tasks</span></span>](attached-and-detached-child-tasks.md)
- [<span data-ttu-id="1fefe-122">PLINQ 和 TPL 中的 Lambda 表达式</span><span class="sxs-lookup"><span data-stu-id="1fefe-122">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)

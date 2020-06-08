---
title: 如何：通过轮询侦听取消请求
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to poll for requests
ms.assetid: c7f2f022-d08e-4e00-b4eb-ae84844cb1bc
ms.openlocfilehash: 6f70ce75b1d6a3d4d7e8a38d739005a261b07241
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279551"
---
# <a name="how-to-listen-for-cancellation-requests-by-polling"></a><span data-ttu-id="c6f0f-102">如何：通过轮询侦听取消请求</span><span class="sxs-lookup"><span data-stu-id="c6f0f-102">How to: Listen for Cancellation Requests by Polling</span></span>
<span data-ttu-id="c6f0f-103">下面的示例展示了一种方便用户代码定期轮询取消令牌，以确定是否已通过调用线程发出取消请求的方式。</span><span class="sxs-lookup"><span data-stu-id="c6f0f-103">The following example shows one way that user code can poll a cancellation token at regular intervals to see whether cancellation has been requested from the calling thread.</span></span> <span data-ttu-id="c6f0f-104">此示例使用 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 类型，但相同的模式适用于 <xref:System.Threading.ThreadPool?displayProperty=nameWithType> 类型或 <xref:System.Threading.Thread?displayProperty=nameWithType> 类型直接创建的异步操作。</span><span class="sxs-lookup"><span data-stu-id="c6f0f-104">This example uses the <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> type, but the same pattern applies to asynchronous operations created directly by the <xref:System.Threading.ThreadPool?displayProperty=nameWithType> type or the <xref:System.Threading.Thread?displayProperty=nameWithType> type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6f0f-105">示例</span><span class="sxs-lookup"><span data-stu-id="c6f0f-105">Example</span></span>  
 <span data-ttu-id="c6f0f-106">若要轮询，必须有某种循环或递归代码，可用于定期读取布尔 <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> 属性的值。</span><span class="sxs-lookup"><span data-stu-id="c6f0f-106">Polling requires some kind of loop or recursive code that can periodically read the value of the Boolean <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property.</span></span> <span data-ttu-id="c6f0f-107">如果使用的是 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 类型，且正在等待任务在调用线程上完成，可以使用 <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> 方法来检查属性并抛出异常。</span><span class="sxs-lookup"><span data-stu-id="c6f0f-107">If you are using the <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> type and you are waiting for the task to complete on the calling thread, you can use the <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> method to check the property and throw the exception.</span></span> <span data-ttu-id="c6f0f-108">通过使用此方法，可确保抛出正确的异常来响应请求。</span><span class="sxs-lookup"><span data-stu-id="c6f0f-108">By using this method, you ensure that the correct exception is thrown in response to a request.</span></span> <span data-ttu-id="c6f0f-109">如果使用的是 <xref:System.Threading.Tasks.Task>，那么调用此方法优于手动抛出 <xref:System.OperationCanceledException>。</span><span class="sxs-lookup"><span data-stu-id="c6f0f-109">If you are using a <xref:System.Threading.Tasks.Task>, then calling this method is better than manually throwing an <xref:System.OperationCanceledException>.</span></span> <span data-ttu-id="c6f0f-110">如果无需抛出异常，可以直接检查属性，并通过方法返回结果（如果属性是 `true` 的话）。</span><span class="sxs-lookup"><span data-stu-id="c6f0f-110">If you do not have to throw the exception, then you can just check the property and return from the method if the property is `true`.</span></span>  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 <span data-ttu-id="c6f0f-111">调用 <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> 非常快，不会在循环中产生很大的开销。</span><span class="sxs-lookup"><span data-stu-id="c6f0f-111">Calling <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> is extremely fast and does not introduce significant overhead in loops.</span></span>  
  
 <span data-ttu-id="c6f0f-112">如果调用的是 <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>，那么如果除了抛出异常之外，还要执行其他工作来响应取消，只需显式检查 <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> 属性即可。</span><span class="sxs-lookup"><span data-stu-id="c6f0f-112">If you are calling <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, you only have to explicitly check the <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property if you have other work to do in response to the cancellation besides throwing the exception.</span></span> <span data-ttu-id="c6f0f-113">在此示例中，可以看到代码实际访问属性两次：一次是显式访问，另一次是在 <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> 方法中。</span><span class="sxs-lookup"><span data-stu-id="c6f0f-113">In this example, you can see that the code actually accesses the property twice: once in the explicit access and again in the <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> method.</span></span> <span data-ttu-id="c6f0f-114">不过，由于读取 <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> 属性在每次访问时只涉及一个易失读取指令，因此从性能角度来看，双重访问的意义并不大。</span><span class="sxs-lookup"><span data-stu-id="c6f0f-114">But because the act of reading the <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property involves only one volatile read instruction per access, the double access is not significant from a performance perspective.</span></span> <span data-ttu-id="c6f0f-115">最好仍调用此方法，而不是手动抛出 <xref:System.OperationCanceledException>。</span><span class="sxs-lookup"><span data-stu-id="c6f0f-115">It is still preferable to call the method rather than manually throw the <xref:System.OperationCanceledException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6f0f-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c6f0f-116">See also</span></span>

- [<span data-ttu-id="c6f0f-117">托管线程中的取消</span><span class="sxs-lookup"><span data-stu-id="c6f0f-117">Cancellation in Managed Threads</span></span>](cancellation-in-managed-threads.md)

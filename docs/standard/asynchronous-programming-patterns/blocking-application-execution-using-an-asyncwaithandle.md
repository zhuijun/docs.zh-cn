---
title: 使用 AsyncWaitHandle 阻止应用程序的执行
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- blocks, asynchronous operations
- ending asynchronous operations
- asynchronous programming, ending operations
- asynchronous programming, blocking applications
- stopping asynchronous operations
- blocking application execution
ms.assetid: 3e32daf2-8161-4e8f-addd-9fd9ff101b03
ms.openlocfilehash: 6184e52c3f6e39e452331af27b83520e498062aa
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289923"
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a><span data-ttu-id="dd1d8-102">使用 AsyncWaitHandle 阻止应用程序的执行</span><span class="sxs-lookup"><span data-stu-id="dd1d8-102">Blocking Application Execution Using an AsyncWaitHandle</span></span>
<span data-ttu-id="dd1d8-103">如果应用无法在等待异步操作结果期间继续执行其他工作，必须阻止应用一直到操作完成。</span><span class="sxs-lookup"><span data-stu-id="dd1d8-103">Applications that cannot continue to do other work while waiting for the results of an asynchronous operation must block until the operation completes.</span></span> <span data-ttu-id="dd1d8-104">请使用下列方法之一，在应用等待异步操作完成期间阻止应用的主线程：</span><span class="sxs-lookup"><span data-stu-id="dd1d8-104">Use one of the following options to block your application's main thread while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="dd1d8-105">使用异步操作的 BeginOperationName 方法返回的 <xref:System.IAsyncResult> 的 <xref:System.IAsyncResult.AsyncWaitHandle%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="dd1d8-105">Use the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method.</span></span> <span data-ttu-id="dd1d8-106">本主题介绍的就是这种方法。</span><span class="sxs-lookup"><span data-stu-id="dd1d8-106">This approach is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="dd1d8-107">调用异步操作的 EndOperationName   方法。</span><span class="sxs-lookup"><span data-stu-id="dd1d8-107">Call the asynchronous operation's **End**_OperationName_ method.</span></span> <span data-ttu-id="dd1d8-108">有关展示这种方法的示例，请参阅[通过结束异步操作阻止应用执行](blocking-application-execution-by-ending-an-async-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="dd1d8-108">For an example that demonstrates this approach, see [Blocking Application Execution by Ending an Async Operation](blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
 <span data-ttu-id="dd1d8-109">在异步操作完成前使用一个或多个 <xref:System.Threading.WaitHandle> 对象阻止的应用，通常会调用 BeginOperationName   方法，执行任何不需要等待操作结果也可以执行的工作，并在一个或多个异步操作完成前一直处于阻止状态。</span><span class="sxs-lookup"><span data-stu-id="dd1d8-109">Applications that use one or more <xref:System.Threading.WaitHandle> objects to block until an asynchronous operation is complete will typically call the **Begin**_OperationName_ method, perform any work that can be done without the results of the operation, and then block until the asynchronous operation(s) completes.</span></span> <span data-ttu-id="dd1d8-110">可以使用 <xref:System.IAsyncResult.AsyncWaitHandle%2A> 调用 <xref:System.Threading.WaitHandle.WaitOne%2A> 方法之一，对单个操作阻止应用。</span><span class="sxs-lookup"><span data-stu-id="dd1d8-110">An application can block on a single operation by calling one of the <xref:System.Threading.WaitHandle.WaitOne%2A> methods using the <xref:System.IAsyncResult.AsyncWaitHandle%2A>.</span></span> <span data-ttu-id="dd1d8-111">若要在等待一组异步操作完成期间阻止应用，请将关联的 <xref:System.IAsyncResult.AsyncWaitHandle%2A> 对象存储到数组中，并调用 <xref:System.Threading.WaitHandle.WaitAll%2A> 方法之一。</span><span class="sxs-lookup"><span data-stu-id="dd1d8-111">To block while waiting for a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAll%2A> methods.</span></span> <span data-ttu-id="dd1d8-112">若要在等待一组异步操作中任一操作完成期间阻止应用，请将关联的 <xref:System.IAsyncResult.AsyncWaitHandle%2A> 对象存储到数组中，并调用 <xref:System.Threading.WaitHandle.WaitAny%2A> 方法之一。</span><span class="sxs-lookup"><span data-stu-id="dd1d8-112">To block while waiting for any one of a set of asynchronous operations to complete, store the associated <xref:System.IAsyncResult.AsyncWaitHandle%2A> objects in an array and call one of the <xref:System.Threading.WaitHandle.WaitAny%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd1d8-113">示例</span><span class="sxs-lookup"><span data-stu-id="dd1d8-113">Example</span></span>  
 <span data-ttu-id="dd1d8-114">下面的代码示例展示了如何使用 DNS 类中的异步方法，检索用户指定计算机的域名系统信息。</span><span class="sxs-lookup"><span data-stu-id="dd1d8-114">The following code example demonstrates using asynchronous methods in the DNS class to retrieve Domain Name System information for a user-specified computer.</span></span> <span data-ttu-id="dd1d8-115">此示例展示了如何使用与异步操作关联的 <xref:System.Threading.WaitHandle> 阻止应用。</span><span class="sxs-lookup"><span data-stu-id="dd1d8-115">The example demonstrates blocking using the <xref:System.Threading.WaitHandle> associated with the asynchronous operation.</span></span> <span data-ttu-id="dd1d8-116">请注意，对 <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` 和 `stateObject` 参数传递的是 `null`（Visual Basic 中的 `Nothing`），因为使用这种方法时这些是可选参数。</span><span class="sxs-lookup"><span data-stu-id="dd1d8-116">Note that `null` (`Nothing` in Visual Basic) is passed for the <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` and `stateObject` parameters because these are not required when using this approach.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="dd1d8-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dd1d8-117">See also</span></span>

- [<span data-ttu-id="dd1d8-118">基于事件的异步模式 (EAP)</span><span class="sxs-lookup"><span data-stu-id="dd1d8-118">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="dd1d8-119">基于事件的异步模式概述</span><span class="sxs-lookup"><span data-stu-id="dd1d8-119">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)

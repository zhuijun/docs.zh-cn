---
title: 使用 AsyncCallback 委托和状态对象
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, delegates
- AsyncCallback delegate, samples
- asynchronous programming, state objects
- IAsyncResult interface, samples
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
ms.openlocfilehash: e52ed550510253aba9401931c0f612211c7d1bf5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276421"
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a><span data-ttu-id="e31d3-102">使用 AsyncCallback 委托和状态对象</span><span class="sxs-lookup"><span data-stu-id="e31d3-102">Using an AsyncCallback Delegate and State Object</span></span>
<span data-ttu-id="e31d3-103">使用 <xref:System.AsyncCallback> 委托处理单独线程中的异步操作结果时，可以使用状态对象，在两个回调之间传递信息，并检索最终结果。</span><span class="sxs-lookup"><span data-stu-id="e31d3-103">When you use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread, you can use a state object to pass information between the callbacks and to retrieve a final result.</span></span> <span data-ttu-id="e31d3-104">本主题通过扩展[使用 AsyncCallback 委托结束异步操作](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)中的示例，展示了此做法。</span><span class="sxs-lookup"><span data-stu-id="e31d3-104">This topic demonstrates that practice by expanding the example in [Using an AsyncCallback Delegate to End an Asynchronous Operation](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e31d3-105">示例</span><span class="sxs-lookup"><span data-stu-id="e31d3-105">Example</span></span>  
 <span data-ttu-id="e31d3-106">下面的代码示例展示了如何使用 <xref:System.Net.Dns> 类中的异步方法，检索用户指定计算机的域名系统 (DNS) 信息。</span><span class="sxs-lookup"><span data-stu-id="e31d3-106">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="e31d3-107">此示例定义并使用 `HostRequest` 类存储状态信息。</span><span class="sxs-lookup"><span data-stu-id="e31d3-107">This example defines and uses the `HostRequest` class to store state information.</span></span> <span data-ttu-id="e31d3-108">`HostRequest` 对象是针对用户输入的每个计算机名进行创建。</span><span class="sxs-lookup"><span data-stu-id="e31d3-108">A `HostRequest` object gets created for each computer name entered by the user.</span></span> <span data-ttu-id="e31d3-109">此对象传递给 <xref:System.Net.Dns.BeginGetHostByName%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="e31d3-109">This object is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A> method.</span></span> <span data-ttu-id="e31d3-110">每当请求完成时，都会调用 `ProcessDnsInformation` 方法。</span><span class="sxs-lookup"><span data-stu-id="e31d3-110">The `ProcessDnsInformation` method is called each time a request completes.</span></span> <span data-ttu-id="e31d3-111">`HostRequest` 对象是使用 <xref:System.IAsyncResult.AsyncState%2A> 属性进行检索。</span><span class="sxs-lookup"><span data-stu-id="e31d3-111">The `HostRequest` object is retrieved using the <xref:System.IAsyncResult.AsyncState%2A> property.</span></span> <span data-ttu-id="e31d3-112">`ProcessDnsInformation` 方法使用 `HostRequest` 对象，存储请求返回的 <xref:System.Net.IPHostEntry> 或请求抛出的 <xref:System.Net.Sockets.SocketException>。</span><span class="sxs-lookup"><span data-stu-id="e31d3-112">The `ProcessDnsInformation` method uses the `HostRequest` object to store the <xref:System.Net.IPHostEntry> returned by the request or a <xref:System.Net.Sockets.SocketException> thrown by the request.</span></span> <span data-ttu-id="e31d3-113">所有请求完成后，应用会循环访问 `HostRequest`对象，并显示 DNS 信息或 <xref:System.Net.Sockets.SocketException> 错误消息。</span><span class="sxs-lookup"><span data-stu-id="e31d3-113">When all requests are complete, the application iterates over the `HostRequest` objects and displays the DNS information or <xref:System.Net.Sockets.SocketException> error message.</span></span>  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="e31d3-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e31d3-114">See also</span></span>

- [<span data-ttu-id="e31d3-115">基于事件的异步模式 (EAP)</span><span class="sxs-lookup"><span data-stu-id="e31d3-115">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="e31d3-116">基于事件的异步模式概述</span><span class="sxs-lookup"><span data-stu-id="e31d3-116">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="e31d3-117">使用 AsyncCallback 委托停止异步操作</span><span class="sxs-lookup"><span data-stu-id="e31d3-117">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)

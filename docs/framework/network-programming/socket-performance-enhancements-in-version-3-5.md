---
title: 版本 3.5 中的套接字性能增强
description: 了解 .NET Framework 版本 3.5 中的 System.Net.Sockets.Socket 类的性能改进。
ms.date: 03/30/2017
ms.assetid: 225aa5f9-c54b-4620-ab64-5cd100cfd54c
ms.openlocfilehash: 5a640c58e47bf1630a3a551aed72b9bc9d4fd6fe
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502140"
---
# <a name="socket-performance-enhancements-in-version-35"></a><span data-ttu-id="0f51e-103">版本 3.5 中的套接字性能增强</span><span class="sxs-lookup"><span data-stu-id="0f51e-103">Socket Performance Enhancements in Version 3.5</span></span>
<span data-ttu-id="0f51e-104">版本 3.5 中增强了 <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> 类，以供使用异步网络 I/O 实现最高性能的应用程序使用。</span><span class="sxs-lookup"><span data-stu-id="0f51e-104">The <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> class has been enhanced in Version 3.5 for use by applications that use asynchronous network I/O to achieve the highest performance.</span></span> <span data-ttu-id="0f51e-105">已添加了一系列新类，作为 <xref:System.Net.Sockets.Socket> 类的一组增强功能的一部分，这些增强功能提供了一种可供专用高性能套接字应用程序使用的替代异步模式。</span><span class="sxs-lookup"><span data-stu-id="0f51e-105">A series of new classes have been added as part of a set of enhancements to the <xref:System.Net.Sockets.Socket> class that provide an alternative asynchronous pattern that can be used by specialized high-performance socket applications.</span></span> <span data-ttu-id="0f51e-106">这些增强功能专为需要高性能的网络服务器应用程序而设计。</span><span class="sxs-lookup"><span data-stu-id="0f51e-106">These enhancements were specifically designed for network server applications that require high performance.</span></span> <span data-ttu-id="0f51e-107">应用程序可以独占方式使用增强型异步模式，或仅在其应用程序的目标热区域（例如，接收大量数据时）使用。</span><span class="sxs-lookup"><span data-stu-id="0f51e-107">An application can use the enhanced asynchronous pattern exclusively, or only in targeted hot areas of their application (when receiving large amounts of data, for example).</span></span>  
  
## <a name="class-enhancements"></a><span data-ttu-id="0f51e-108">类增强功能</span><span class="sxs-lookup"><span data-stu-id="0f51e-108">Class Enhancements</span></span>  
 <span data-ttu-id="0f51e-109">这些增强功能的主要功能是避免在大容量异步套接字 I/O 期间重复分配和同步对象。</span><span class="sxs-lookup"><span data-stu-id="0f51e-109">The main feature of these enhancements is the avoidance of the repeated allocation and synchronization of objects during high-volume asynchronous socket I/O.</span></span> <span data-ttu-id="0f51e-110">当前由异步套接字 I/O 的 <xref:System.Net.Sockets.Socket> 类实现的 Begin/End 设计模式需要为每个异步套接字操作分配一个 <xref:System.IAsyncResult?displayProperty=nameWithType> 对象。</span><span class="sxs-lookup"><span data-stu-id="0f51e-110">The Begin/End design pattern currently implemented by the <xref:System.Net.Sockets.Socket> class for asynchronous socket I/O requires a <xref:System.IAsyncResult?displayProperty=nameWithType> object be allocated for each asynchronous socket operation.</span></span>  
  
 <span data-ttu-id="0f51e-111">在新的 <xref:System.Net.Sockets.Socket> 类增强功能中，异步套接字操作由应用程序分配和维护的可重用 <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType> 类对象描述。</span><span class="sxs-lookup"><span data-stu-id="0f51e-111">In the new <xref:System.Net.Sockets.Socket> class enhancements, asynchronous socket operations are described by reusable <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType> class objects allocated and maintained by the application.</span></span> <span data-ttu-id="0f51e-112">高性能套接字应用程序非常清楚必须维持的重叠套接字操作的数量。</span><span class="sxs-lookup"><span data-stu-id="0f51e-112">High-performance socket applications know best the amount of overlapped socket operations that must be sustained.</span></span> <span data-ttu-id="0f51e-113">该应用程序可创建所需的 <xref:System.Net.Sockets.SocketAsyncEventArgs> 对象数量。</span><span class="sxs-lookup"><span data-stu-id="0f51e-113">The application can create as many of the <xref:System.Net.Sockets.SocketAsyncEventArgs> objects that it needs.</span></span> <span data-ttu-id="0f51e-114">例如，如果服务器应用程序始终需要 15 个套接字接受操作，以支持传入的客户端连接速率，则可以预先为此分配 15 个可重用的 <xref:System.Net.Sockets.SocketAsyncEventArgs> 对象。</span><span class="sxs-lookup"><span data-stu-id="0f51e-114">For example, if a server application needs to have 15 socket accept operations outstanding at all times to support incoming client connection rates, it can allocate 15 reusable <xref:System.Net.Sockets.SocketAsyncEventArgs> objects in advance for that purpose.</span></span>  
  
 <span data-ttu-id="0f51e-115">使用此类执行异步套接字操作的模式包括以下步骤：</span><span class="sxs-lookup"><span data-stu-id="0f51e-115">The pattern for performing an asynchronous socket operation with this class consists of the following steps:</span></span>  
  
1. <span data-ttu-id="0f51e-116">分配一个新的 <xref:System.Net.Sockets.SocketAsyncEventArgs> 上下文对象，或从应用程序池中获取一个空闲对象。</span><span class="sxs-lookup"><span data-stu-id="0f51e-116">Allocate a new <xref:System.Net.Sockets.SocketAsyncEventArgs> context object, or get a free one from an application pool.</span></span>  
  
2. <span data-ttu-id="0f51e-117">将上下文对象的属性设置为要执行的操作（例如，回调代理方法和数据缓冲区）。</span><span class="sxs-lookup"><span data-stu-id="0f51e-117">Set properties on the context object to the operation about to be performed (the callback delegate method and data buffer, for example).</span></span>  
  
3. <span data-ttu-id="0f51e-118">调用适当的套接字方法 (xxxAsync) 以启动异步操作。</span><span class="sxs-lookup"><span data-stu-id="0f51e-118">Call the appropriate socket method (xxxAsync) to initiate the asynchronous operation.</span></span>  
  
4. <span data-ttu-id="0f51e-119">如果异步套接字方法 (xxxAsync) 在回调中返回 true，请查询完成状态的上下文属性。</span><span class="sxs-lookup"><span data-stu-id="0f51e-119">If the asynchronous socket method (xxxAsync) returns true in the callback, query the context properties for completion status.</span></span>  
  
5. <span data-ttu-id="0f51e-120">如果异步套接字方法 (xxxAsync) 在回调中返回 false，则已同步完成该操作。</span><span class="sxs-lookup"><span data-stu-id="0f51e-120">If the asynchronous socket method (xxxAsync) returns false in the callback, the operation completed synchronously.</span></span> <span data-ttu-id="0f51e-121">可查询上下文属性获取操作结果。</span><span class="sxs-lookup"><span data-stu-id="0f51e-121">The context properties may be queried for the operation result.</span></span>  
  
6. <span data-ttu-id="0f51e-122">重新使用上下文进行另一项操作，将其放回池中，或放弃它。</span><span class="sxs-lookup"><span data-stu-id="0f51e-122">Reuse the context for another operation, put it back in the pool, or discard it.</span></span>  
  
 <span data-ttu-id="0f51e-123">新的异步套接字操作上下文对象的生存期由应用程序代码中的引用和异步 I/O 引用确定。</span><span class="sxs-lookup"><span data-stu-id="0f51e-123">The lifetime of the new asynchronous socket operation context object is determined by references in the application code and asynchronous I/O references.</span></span> <span data-ttu-id="0f51e-124">作为参数提交给异步套接字操作方法之一后，应用程序不必保留对异步套接字操作上下文对象的引用。</span><span class="sxs-lookup"><span data-stu-id="0f51e-124">It is not necessary for the application to retain a reference to an asynchronous socket operation context object after it is submitted as a parameter to one of the asynchronous socket operation methods.</span></span> <span data-ttu-id="0f51e-125">完成回调返回之前，应用程序会继续引用它。</span><span class="sxs-lookup"><span data-stu-id="0f51e-125">It will remain referenced until the completion callback returns.</span></span> <span data-ttu-id="0f51e-126">然而，应用程序保留对上下文对象的引用是有利的，这样可将其重新用于将来的异步套接字操作。</span><span class="sxs-lookup"><span data-stu-id="0f51e-126">However it is advantageous for the application to retain the reference to the context object so that it can be reused for a future asynchronous socket operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f51e-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="0f51e-127">See also</span></span>

- <xref:System.Net.Sockets.Socket?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SendPacketsElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketAsyncOperation?displayProperty=nameWithType>
- [<span data-ttu-id="0f51e-128">网络编程示例</span><span class="sxs-lookup"><span data-stu-id="0f51e-128">Network Programming Samples</span></span>](network-programming-samples.md)
- [<span data-ttu-id="0f51e-129">Socket 代码示例</span><span class="sxs-lookup"><span data-stu-id="0f51e-129">Socket Code Examples</span></span>](socket-code-examples.md)

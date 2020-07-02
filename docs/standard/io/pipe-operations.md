---
title: .NET 中的管道操作
description: 了解 .NET 中的管道操作。 管道为进程间通信提供了平台。 有两种类型的管道：匿名管道和命名管道。
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
ms.openlocfilehash: 35a3910bbab1b34f085a55524be0b18b3fa81958
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768880"
---
# <a name="pipe-operations-in-net"></a><span data-ttu-id="363b8-105">.NET 中的管道操作</span><span class="sxs-lookup"><span data-stu-id="363b8-105">Pipe Operations in .NET</span></span>
<span data-ttu-id="363b8-106">管道为进程间通信提供了平台。</span><span class="sxs-lookup"><span data-stu-id="363b8-106">Pipes provide a means for interprocess communication.</span></span> <span data-ttu-id="363b8-107">管道分为两种类型：</span><span class="sxs-lookup"><span data-stu-id="363b8-107">There are two types of pipes:</span></span>  
  
- <span data-ttu-id="363b8-108">匿名管道。</span><span class="sxs-lookup"><span data-stu-id="363b8-108">Anonymous pipes.</span></span>  
  
     <span data-ttu-id="363b8-109">匿名管道在本地计算机上提供进程间通信。</span><span class="sxs-lookup"><span data-stu-id="363b8-109">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="363b8-110">与命名管道相比，虽然匿名管道需要的开销更少，但提供的服务有限。</span><span class="sxs-lookup"><span data-stu-id="363b8-110">Anonymous pipes require less overhead than named pipes but offer limited services.</span></span> <span data-ttu-id="363b8-111">匿名管道是单向的，不能通过网络使用。</span><span class="sxs-lookup"><span data-stu-id="363b8-111">Anonymous pipes are one-way and cannot be used over a network.</span></span> <span data-ttu-id="363b8-112">仅支持一个服务器实例。</span><span class="sxs-lookup"><span data-stu-id="363b8-112">They support only a single server instance.</span></span> <span data-ttu-id="363b8-113">匿名管道可用于线程间通信，也可用于父进程和子进程之间的通信，因为管道句柄可以轻松传递给所创建的子进程。</span><span class="sxs-lookup"><span data-stu-id="363b8-113">Anonymous pipes are useful for communication between threads, or between parent and child processes where the pipe handles can be easily passed to the child process when it is created.</span></span>  
  
     <span data-ttu-id="363b8-114">在 .NET 中，可通过使用 <xref:System.IO.Pipes.AnonymousPipeServerStream> 和 <xref:System.IO.Pipes.AnonymousPipeClientStream> 类来实现匿名管道。</span><span class="sxs-lookup"><span data-stu-id="363b8-114">In .NET, you implement anonymous pipes by using the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="363b8-115">请参阅[如何：使用匿名管道进行本地进程间通信](how-to-use-anonymous-pipes-for-local-interprocess-communication.md)。</span><span class="sxs-lookup"><span data-stu-id="363b8-115">See [How to: Use Anonymous Pipes for Local Interprocess Communication](how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span></span>  
  
- <span data-ttu-id="363b8-116">命名管道。</span><span class="sxs-lookup"><span data-stu-id="363b8-116">Named pipes.</span></span>  
  
     <span data-ttu-id="363b8-117">命名管道在管道服务器和一个或多个管道客户端之间提供进程间通信。</span><span class="sxs-lookup"><span data-stu-id="363b8-117">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="363b8-118">命名管道可以是单向的，也可以是双向的。</span><span class="sxs-lookup"><span data-stu-id="363b8-118">Named pipes can be one-way or duplex.</span></span> <span data-ttu-id="363b8-119">它们支持基于消息的通信，并允许多个客户端使用相同的管道名称同时连接到服务器进程。</span><span class="sxs-lookup"><span data-stu-id="363b8-119">They support message-based communication and allow multiple clients to connect simultaneously to the server process using the same pipe name.</span></span> <span data-ttu-id="363b8-120">命名管道还支持模拟，这样连接进程就可以在远程服务器上使用自己的权限。</span><span class="sxs-lookup"><span data-stu-id="363b8-120">Named pipes also support impersonation, which enables connecting processes to use their own permissions on remote servers.</span></span>  
  
     <span data-ttu-id="363b8-121">在 .NET 中，可通过使用 <xref:System.IO.Pipes.NamedPipeServerStream> 和 <xref:System.IO.Pipes.NamedPipeClientStream> 类来实现命名管道。</span><span class="sxs-lookup"><span data-stu-id="363b8-121">In .NET, you implement named pipes by using the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="363b8-122">请参阅[如何：使用命名管道进行网络进程间通信](how-to-use-named-pipes-for-network-interprocess-communication.md)。</span><span class="sxs-lookup"><span data-stu-id="363b8-122">See [How to: Use Named Pipes for Network Interprocess Communication](how-to-use-named-pipes-for-network-interprocess-communication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="363b8-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="363b8-123">See also</span></span>

- [<span data-ttu-id="363b8-124">文件和流 I/O</span><span class="sxs-lookup"><span data-stu-id="363b8-124">File and Stream I/O</span></span>](index.md)
- [<span data-ttu-id="363b8-125">如何：使用匿名管道进行本地进程间通信</span><span class="sxs-lookup"><span data-stu-id="363b8-125">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
- [<span data-ttu-id="363b8-126">如何：使用命名管道进行网络进程间通信</span><span class="sxs-lookup"><span data-stu-id="363b8-126">How to: Use Named Pipes for Network Interprocess Communication</span></span>](how-to-use-named-pipes-for-network-interprocess-communication.md)

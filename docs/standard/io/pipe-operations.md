---
title: .NET 中的管道操作
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
ms.openlocfilehash: a634cb87a5f25b520e5fe6fd5b39eae861120a28
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278683"
---
# <a name="pipe-operations-in-net"></a><span data-ttu-id="2ac85-102">.NET 中的管道操作</span><span class="sxs-lookup"><span data-stu-id="2ac85-102">Pipe Operations in .NET</span></span>
<span data-ttu-id="2ac85-103">管道为进程间通信提供了平台。</span><span class="sxs-lookup"><span data-stu-id="2ac85-103">Pipes provide a means for interprocess communication.</span></span> <span data-ttu-id="2ac85-104">管道分为两种类型：</span><span class="sxs-lookup"><span data-stu-id="2ac85-104">There are two types of pipes:</span></span>  
  
- <span data-ttu-id="2ac85-105">匿名管道。</span><span class="sxs-lookup"><span data-stu-id="2ac85-105">Anonymous pipes.</span></span>  
  
     <span data-ttu-id="2ac85-106">匿名管道在本地计算机上提供进程间通信。</span><span class="sxs-lookup"><span data-stu-id="2ac85-106">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="2ac85-107">与命名管道相比，虽然匿名管道需要的开销更少，但提供的服务有限。</span><span class="sxs-lookup"><span data-stu-id="2ac85-107">Anonymous pipes require less overhead than named pipes but offer limited services.</span></span> <span data-ttu-id="2ac85-108">匿名管道是单向的，不能通过网络使用。</span><span class="sxs-lookup"><span data-stu-id="2ac85-108">Anonymous pipes are one-way and cannot be used over a network.</span></span> <span data-ttu-id="2ac85-109">仅支持一个服务器实例。</span><span class="sxs-lookup"><span data-stu-id="2ac85-109">They support only a single server instance.</span></span> <span data-ttu-id="2ac85-110">匿名管道可用于线程间通信，也可用于父进程和子进程之间的通信，因为管道句柄可以轻松传递给所创建的子进程。</span><span class="sxs-lookup"><span data-stu-id="2ac85-110">Anonymous pipes are useful for communication between threads, or between parent and child processes where the pipe handles can be easily passed to the child process when it is created.</span></span>  
  
     <span data-ttu-id="2ac85-111">在 .NET 中，可通过使用 <xref:System.IO.Pipes.AnonymousPipeServerStream> 和 <xref:System.IO.Pipes.AnonymousPipeClientStream> 类来实现匿名管道。</span><span class="sxs-lookup"><span data-stu-id="2ac85-111">In .NET, you implement anonymous pipes by using the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="2ac85-112">请参阅[如何：使用匿名管道进行本地进程间通信](how-to-use-anonymous-pipes-for-local-interprocess-communication.md)。</span><span class="sxs-lookup"><span data-stu-id="2ac85-112">See [How to: Use Anonymous Pipes for Local Interprocess Communication](how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span></span>  
  
- <span data-ttu-id="2ac85-113">命名管道。</span><span class="sxs-lookup"><span data-stu-id="2ac85-113">Named pipes.</span></span>  
  
     <span data-ttu-id="2ac85-114">命名管道在管道服务器和一个或多个管道客户端之间提供进程间通信。</span><span class="sxs-lookup"><span data-stu-id="2ac85-114">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="2ac85-115">命名管道可以是单向的，也可以是双向的。</span><span class="sxs-lookup"><span data-stu-id="2ac85-115">Named pipes can be one-way or duplex.</span></span> <span data-ttu-id="2ac85-116">它们支持基于消息的通信，并允许多个客户端使用相同的管道名称同时连接到服务器进程。</span><span class="sxs-lookup"><span data-stu-id="2ac85-116">They support message-based communication and allow multiple clients to connect simultaneously to the server process using the same pipe name.</span></span> <span data-ttu-id="2ac85-117">命名管道还支持模拟，这样连接进程就可以在远程服务器上使用自己的权限。</span><span class="sxs-lookup"><span data-stu-id="2ac85-117">Named pipes also support impersonation, which enables connecting processes to use their own permissions on remote servers.</span></span>  
  
     <span data-ttu-id="2ac85-118">在 .NET 中，可通过使用 <xref:System.IO.Pipes.NamedPipeServerStream> 和 <xref:System.IO.Pipes.NamedPipeClientStream> 类来实现命名管道。</span><span class="sxs-lookup"><span data-stu-id="2ac85-118">In .NET, you implement named pipes by using the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="2ac85-119">请参阅[如何：使用命名管道进行网络进程间通信](how-to-use-named-pipes-for-network-interprocess-communication.md)。</span><span class="sxs-lookup"><span data-stu-id="2ac85-119">See [How to: Use Named Pipes for Network Interprocess Communication](how-to-use-named-pipes-for-network-interprocess-communication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ac85-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2ac85-120">See also</span></span>

- [<span data-ttu-id="2ac85-121">文件和流 I/O</span><span class="sxs-lookup"><span data-stu-id="2ac85-121">File and Stream I/O</span></span>](index.md)
- [<span data-ttu-id="2ac85-122">如何：使用匿名管道进行本地进程间通信</span><span class="sxs-lookup"><span data-stu-id="2ac85-122">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
- [<span data-ttu-id="2ac85-123">如何：使用命名管道进行网络进程间通信</span><span class="sxs-lookup"><span data-stu-id="2ac85-123">How to: Use Named Pipes for Network Interprocess Communication</span></span>](how-to-use-named-pipes-for-network-interprocess-communication.md)

---
title: 如何：使用命名管道进行网络进程间通信
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- message-based communication [.NET Framework], named pipes
- named pipes [.NET Framework]
- pipes [.NET Framework]
- multiple connections via named pipes
- network communications [.NET Framework], named pipes
- impersonation [.NET Framework], named pipes
- full duplex communication [.NET Framework], named pipes
ms.assetid: 4e4d7e64-9f1b-4026-98f7-20488ac7b42b
ms.openlocfilehash: bebfd136245fd7b577ffcd71954f46ca82bfc72d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291742"
---
# <a name="how-to-use-named-pipes-for-network-interprocess-communication"></a><span data-ttu-id="d31ee-102">如何：使用命名管道进行网络进程间通信</span><span class="sxs-lookup"><span data-stu-id="d31ee-102">How to: Use Named Pipes for Network Interprocess Communication</span></span>
<span data-ttu-id="d31ee-103">命名管道在管道服务器和一个或多个管道客户端之间提供进程间通信。</span><span class="sxs-lookup"><span data-stu-id="d31ee-103">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="d31ee-104">它们比匿名管道（用于在本地计算机上提供进程间的通信）提供更多的功能。</span><span class="sxs-lookup"><span data-stu-id="d31ee-104">They offer more functionality than anonymous pipes, which provide interprocess communication on a local computer.</span></span> <span data-ttu-id="d31ee-105">命名管道支持跨网络和多个服务器实例的全双工通信、基于消息的通信以及客户端模拟，这样连接进程便可在远程服务器上使用自己的权限集。</span><span class="sxs-lookup"><span data-stu-id="d31ee-105">Named pipes support full duplex communication over a network and multiple server instances, message-based communication, and client impersonation, which enables connecting processes to use their own set of permissions on remote servers.</span></span>  
  
 <span data-ttu-id="d31ee-106">若要实现名称管道，请使用 <xref:System.IO.Pipes.NamedPipeServerStream> 和 <xref:System.IO.Pipes.NamedPipeClientStream> 类。</span><span class="sxs-lookup"><span data-stu-id="d31ee-106">To implement name pipes, use the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d31ee-107">示例</span><span class="sxs-lookup"><span data-stu-id="d31ee-107">Example</span></span>  
 <span data-ttu-id="d31ee-108">下面的示例展示了如何使用 <xref:System.IO.Pipes.NamedPipeServerStream> 类创建命名管道。</span><span class="sxs-lookup"><span data-stu-id="d31ee-108">The following example demonstrates how to create a named pipe by using the <xref:System.IO.Pipes.NamedPipeServerStream> class.</span></span> <span data-ttu-id="d31ee-109">在此示例中，服务器进程创建四个线程。</span><span class="sxs-lookup"><span data-stu-id="d31ee-109">In this example, the server process creates four threads.</span></span> <span data-ttu-id="d31ee-110">每个线程都可以接受客户端连接。</span><span class="sxs-lookup"><span data-stu-id="d31ee-110">Each thread can accept a client connection.</span></span> <span data-ttu-id="d31ee-111">然后，连接的客户端进程向服务器提供文件名。</span><span class="sxs-lookup"><span data-stu-id="d31ee-111">The connected client process then supplies the server with a file name.</span></span> <span data-ttu-id="d31ee-112">如果客户端拥有足够的权限，服务器进程就会打开文件，并将它的内容发送回客户端。</span><span class="sxs-lookup"><span data-stu-id="d31ee-112">If the client has sufficient permissions, the server process opens the file and sends its contents back to the client.</span></span>  
  
 [!code-cpp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="d31ee-113">示例</span><span class="sxs-lookup"><span data-stu-id="d31ee-113">Example</span></span>  
 <span data-ttu-id="d31ee-114">下面的示例展示了使用 <xref:System.IO.Pipes.NamedPipeClientStream> 类的客户端进程。</span><span class="sxs-lookup"><span data-stu-id="d31ee-114">The following example shows the client process, which uses the <xref:System.IO.Pipes.NamedPipeClientStream> class.</span></span> <span data-ttu-id="d31ee-115">客户端连接到服务器进程，并将文件名发送到服务器。</span><span class="sxs-lookup"><span data-stu-id="d31ee-115">The client connects to the server process and sends a file name to the server.</span></span> <span data-ttu-id="d31ee-116">因为此示例使用模拟，所以运行客户端应用的标识必须有权访问文件。</span><span class="sxs-lookup"><span data-stu-id="d31ee-116">The example uses impersonation, so the identity that is running the client application must have permission to access the file.</span></span> <span data-ttu-id="d31ee-117">然后，服务器将文件内容发送回客户端。</span><span class="sxs-lookup"><span data-stu-id="d31ee-117">The server then sends the contents of the file back to the client.</span></span> <span data-ttu-id="d31ee-118">接下来，文件内容在控制台中显示。</span><span class="sxs-lookup"><span data-stu-id="d31ee-118">The file contents are then displayed to the console.</span></span>  
  
 [!code-csharp[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="robust-programming"></a><span data-ttu-id="d31ee-119">可靠编程</span><span class="sxs-lookup"><span data-stu-id="d31ee-119">Robust Programming</span></span>  
 <span data-ttu-id="d31ee-120">因为此示例中的客户端进程和服务器进程可以在同一台计算机上运行，所以提供给 <xref:System.IO.Pipes.NamedPipeClientStream> 对象的服务器名称为 `"."`。</span><span class="sxs-lookup"><span data-stu-id="d31ee-120">The client and server processes in this example are intended to run on the same computer, so the server name provided to the <xref:System.IO.Pipes.NamedPipeClientStream> object is `"."`.</span></span> <span data-ttu-id="d31ee-121">如果客户端进程和服务器进程在不同的计算机上运行，`"."` 会被替换为运行服务器进程的计算机的网络名称。</span><span class="sxs-lookup"><span data-stu-id="d31ee-121">If the client and server processes were on separate computers, `"."` would be replaced with the network name of the computer that runs the server process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d31ee-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d31ee-122">See also</span></span>

- <xref:System.Security.Principal.TokenImpersonationLevel>
- <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName%2A>
- [<span data-ttu-id="d31ee-123">管道</span><span class="sxs-lookup"><span data-stu-id="d31ee-123">Pipes</span></span>](pipe-operations.md)
- [<span data-ttu-id="d31ee-124">如何：使用匿名管道进行本地进程间通信</span><span class="sxs-lookup"><span data-stu-id="d31ee-124">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](how-to-use-anonymous-pipes-for-local-interprocess-communication.md)

---
title: 如何：使用匿名管道进行本地进程间通信
description: 了解如何在 .NET 中的本地计算机上使用匿名管道进行本地进程间通信。 与命名管道相比，匿名管道需要的开销更少。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- anonymous pipes [.NET Framework]
- parent-child communication [.NET Framework]
- pipes [.NET Framework]
- one-way communication [.NET Framework]
- local computer communication [.NET Framework], pipes
ms.assetid: e7773c77-c646-4a01-8a96-a003d59fc4c9
ms.openlocfilehash: 090a25aea4f280fc2ad00cf7777a501c475dfc66
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594798"
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a><span data-ttu-id="1c5e3-104">如何：使用匿名管道进行本地进程间通信</span><span class="sxs-lookup"><span data-stu-id="1c5e3-104">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>
<span data-ttu-id="1c5e3-105">匿名管道在本地计算机上提供进程间通信。</span><span class="sxs-lookup"><span data-stu-id="1c5e3-105">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="1c5e3-106">它们提供的功能比命名管道少，但所需要的系统开销也少。</span><span class="sxs-lookup"><span data-stu-id="1c5e3-106">They offer less functionality than named pipes, but also require less overhead.</span></span> <span data-ttu-id="1c5e3-107">使用匿名管道，可以在本地计算机上更轻松地进行进程间通信。</span><span class="sxs-lookup"><span data-stu-id="1c5e3-107">You can use anonymous pipes to make interprocess communication on a local computer easier.</span></span> <span data-ttu-id="1c5e3-108">不能使用匿名管道进行网络通信。</span><span class="sxs-lookup"><span data-stu-id="1c5e3-108">You cannot use anonymous pipes for communication over a network.</span></span>  
  
 <span data-ttu-id="1c5e3-109">若要实现匿名管道，请使用 <xref:System.IO.Pipes.AnonymousPipeServerStream> 和 <xref:System.IO.Pipes.AnonymousPipeClientStream> 类。</span><span class="sxs-lookup"><span data-stu-id="1c5e3-109">To implement anonymous pipes, use the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c5e3-110">示例</span><span class="sxs-lookup"><span data-stu-id="1c5e3-110">Example</span></span>  
 <span data-ttu-id="1c5e3-111">下面的示例展示了如何使用匿名管道将字符串从父进程发送到子进程。</span><span class="sxs-lookup"><span data-stu-id="1c5e3-111">The following example demonstrates a way to send a string from a parent process to a child process using anonymous pipes.</span></span> <span data-ttu-id="1c5e3-112">此示例在父进程中创建 <xref:System.IO.Pipes.AnonymousPipeServerStream> 对象，它的 <xref:System.IO.Pipes.PipeDirection> 值为 <xref:System.IO.Pipes.PipeDirection.Out>。</span><span class="sxs-lookup"><span data-stu-id="1c5e3-112">This example creates an <xref:System.IO.Pipes.AnonymousPipeServerStream> object in a parent process with a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.Out>.</span></span> <span data-ttu-id="1c5e3-113">然后，父进程使用客户端句柄创建 <xref:System.IO.Pipes.AnonymousPipeClientStream> 对象，以创建子进程。</span><span class="sxs-lookup"><span data-stu-id="1c5e3-113">The parent process then creates a child process by using a client handle to create an <xref:System.IO.Pipes.AnonymousPipeClientStream> object.</span></span> <span data-ttu-id="1c5e3-114">子进程的 <xref:System.IO.Pipes.PipeDirection> 值为 <xref:System.IO.Pipes.PipeDirection.In>。</span><span class="sxs-lookup"><span data-stu-id="1c5e3-114">The child process has a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.In>.</span></span>  
  
 <span data-ttu-id="1c5e3-115">接下来，父进程将用户提供的字符串发送给子进程。</span><span class="sxs-lookup"><span data-stu-id="1c5e3-115">The parent process then sends a user-supplied string to the child process.</span></span> <span data-ttu-id="1c5e3-116">字符串在子进程的控制台中显示。</span><span class="sxs-lookup"><span data-stu-id="1c5e3-116">The string is displayed to the console in the child process.</span></span>  
  
 <span data-ttu-id="1c5e3-117">下面的示例展示了服务器进程。</span><span class="sxs-lookup"><span data-stu-id="1c5e3-117">The following example shows the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]
  
## <a name="example"></a><span data-ttu-id="1c5e3-118">示例</span><span class="sxs-lookup"><span data-stu-id="1c5e3-118">Example</span></span>  
 <span data-ttu-id="1c5e3-119">下面的示例展示了客户端进程。</span><span class="sxs-lookup"><span data-stu-id="1c5e3-119">The following example shows the client process.</span></span> <span data-ttu-id="1c5e3-120">服务器进程启动客户端进程，并为此进程提供客户端句柄。</span><span class="sxs-lookup"><span data-stu-id="1c5e3-120">The server process starts the client process and gives that process a client handle.</span></span> <span data-ttu-id="1c5e3-121">客户端代码生成的可执行文件应命名为 `pipeClient.exe`，并在运行服务器进程前复制到服务器可执行文件所在的相同目录中。</span><span class="sxs-lookup"><span data-stu-id="1c5e3-121">The resulting executable from the client code should be named `pipeClient.exe` and be copied to the same directory as the server executable before running the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="1c5e3-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="1c5e3-122">See also</span></span>

- [<span data-ttu-id="1c5e3-123">管道</span><span class="sxs-lookup"><span data-stu-id="1c5e3-123">Pipes</span></span>](pipe-operations.md)
- [<span data-ttu-id="1c5e3-124">如何：使用命名管道进行网络进程间通信</span><span class="sxs-lookup"><span data-stu-id="1c5e3-124">How to: Use Named Pipes for Network Interprocess Communication</span></span>](how-to-use-named-pipes-for-network-interprocess-communication.md)

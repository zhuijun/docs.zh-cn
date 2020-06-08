---
title: 如何：使用匿名管道进行本地进程间通信
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
ms.openlocfilehash: 9962471697888041e98e38dd5f7feaecc306894d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291781"
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a><span data-ttu-id="61306-102">如何：使用匿名管道进行本地进程间通信</span><span class="sxs-lookup"><span data-stu-id="61306-102">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>
<span data-ttu-id="61306-103">匿名管道在本地计算机上提供进程间通信。</span><span class="sxs-lookup"><span data-stu-id="61306-103">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="61306-104">它们提供的功能比命名管道少，但所需要的系统开销也少。</span><span class="sxs-lookup"><span data-stu-id="61306-104">They offer less functionality than named pipes, but also require less overhead.</span></span> <span data-ttu-id="61306-105">使用匿名管道，可以在本地计算机上更轻松地进行进程间通信。</span><span class="sxs-lookup"><span data-stu-id="61306-105">You can use anonymous pipes to make interprocess communication on a local computer easier.</span></span> <span data-ttu-id="61306-106">不能使用匿名管道进行网络通信。</span><span class="sxs-lookup"><span data-stu-id="61306-106">You cannot use anonymous pipes for communication over a network.</span></span>  
  
 <span data-ttu-id="61306-107">若要实现匿名管道，请使用 <xref:System.IO.Pipes.AnonymousPipeServerStream> 和 <xref:System.IO.Pipes.AnonymousPipeClientStream> 类。</span><span class="sxs-lookup"><span data-stu-id="61306-107">To implement anonymous pipes, use the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61306-108">示例</span><span class="sxs-lookup"><span data-stu-id="61306-108">Example</span></span>  
 <span data-ttu-id="61306-109">下面的示例展示了如何使用匿名管道将字符串从父进程发送到子进程。</span><span class="sxs-lookup"><span data-stu-id="61306-109">The following example demonstrates a way to send a string from a parent process to a child process using anonymous pipes.</span></span> <span data-ttu-id="61306-110">此示例在父进程中创建 <xref:System.IO.Pipes.AnonymousPipeServerStream> 对象，它的 <xref:System.IO.Pipes.PipeDirection> 值为 <xref:System.IO.Pipes.PipeDirection.Out>。</span><span class="sxs-lookup"><span data-stu-id="61306-110">This example creates an <xref:System.IO.Pipes.AnonymousPipeServerStream> object in a parent process with a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.Out>.</span></span> <span data-ttu-id="61306-111">然后，父进程使用客户端句柄创建 <xref:System.IO.Pipes.AnonymousPipeClientStream> 对象，以创建子进程。</span><span class="sxs-lookup"><span data-stu-id="61306-111">The parent process then creates a child process by using a client handle to create an <xref:System.IO.Pipes.AnonymousPipeClientStream> object.</span></span> <span data-ttu-id="61306-112">子进程的 <xref:System.IO.Pipes.PipeDirection> 值为 <xref:System.IO.Pipes.PipeDirection.In>。</span><span class="sxs-lookup"><span data-stu-id="61306-112">The child process has a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.In>.</span></span>  
  
 <span data-ttu-id="61306-113">接下来，父进程将用户提供的字符串发送给子进程。</span><span class="sxs-lookup"><span data-stu-id="61306-113">The parent process then sends a user-supplied string to the child process.</span></span> <span data-ttu-id="61306-114">字符串在子进程的控制台中显示。</span><span class="sxs-lookup"><span data-stu-id="61306-114">The string is displayed to the console in the child process.</span></span>  
  
 <span data-ttu-id="61306-115">下面的示例展示了服务器进程。</span><span class="sxs-lookup"><span data-stu-id="61306-115">The following example shows the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]
  
## <a name="example"></a><span data-ttu-id="61306-116">示例</span><span class="sxs-lookup"><span data-stu-id="61306-116">Example</span></span>  
 <span data-ttu-id="61306-117">下面的示例展示了客户端进程。</span><span class="sxs-lookup"><span data-stu-id="61306-117">The following example shows the client process.</span></span> <span data-ttu-id="61306-118">服务器进程启动客户端进程，并为此进程提供客户端句柄。</span><span class="sxs-lookup"><span data-stu-id="61306-118">The server process starts the client process and gives that process a client handle.</span></span> <span data-ttu-id="61306-119">客户端代码生成的可执行文件应命名为 `pipeClient.exe`，并在运行服务器进程前复制到服务器可执行文件所在的相同目录中。</span><span class="sxs-lookup"><span data-stu-id="61306-119">The resulting executable from the client code should be named `pipeClient.exe` and be copied to the same directory as the server executable before running the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="61306-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="61306-120">See also</span></span>

- [<span data-ttu-id="61306-121">管道</span><span class="sxs-lookup"><span data-stu-id="61306-121">Pipes</span></span>](pipe-operations.md)
- [<span data-ttu-id="61306-122">如何：使用命名管道进行网络进程间通信</span><span class="sxs-lookup"><span data-stu-id="61306-122">How to: Use Named Pipes for Network Interprocess Communication</span></span>](how-to-use-named-pipes-for-network-interprocess-communication.md)

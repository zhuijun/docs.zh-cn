---
title: Socket 代码示例
description: 查看以下示例，了解如何将 Socket 类用作客户端来连接到网络服务，以及如何将它用作服务器来侦听来自客户端的连接。
ms.date: 03/30/2017
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- Socket class, asynchronous server sockets
- data requests, sockets
- requesting data from Internet, sockets
- server sockets
- sockets, code examples
- receiving data, sockets
- protocols, sockets
- Internet, sockets
- client sockets
ms.assetid: f3fc7533-6956-42c6-bbc3-73e5a221027d
ms.openlocfilehash: 0a0911a779ed3d4938ad7ff57f048c176cf677fb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502153"
---
# <a name="socket-code-examples"></a><span data-ttu-id="6b4ac-103">Socket 代码示例</span><span class="sxs-lookup"><span data-stu-id="6b4ac-103">Socket Code Examples</span></span>
<span data-ttu-id="6b4ac-104">以下代码示例演示如何使用 <xref:System.Net.Sockets.Socket> 类作为客户端连接到远程网络服务，以及如何将它用作服务器以侦听来自远程客户端的连接。</span><span class="sxs-lookup"><span data-stu-id="6b4ac-104">The following code examples demonstrate how to use the <xref:System.Net.Sockets.Socket> class as a client to connect to remote network services and as a server to listen for connections from remote clients.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6b4ac-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="6b4ac-105">In This Section</span></span>  
 [<span data-ttu-id="6b4ac-106">同步客户端套接字示例</span><span class="sxs-lookup"><span data-stu-id="6b4ac-106">Synchronous Client Socket Example</span></span>](synchronous-client-socket-example.md)  
 <span data-ttu-id="6b4ac-107">演示如何实现连接到服务器的同步 <xref:System.Net.Sockets.Socket> 客户端，并显示从服务器返回的数据。</span><span class="sxs-lookup"><span data-stu-id="6b4ac-107">Shows how to implement a synchronous <xref:System.Net.Sockets.Socket> client that connects to a server and displays the data returned from the server.</span></span>  
  
 [<span data-ttu-id="6b4ac-108">同步服务器套接字示例</span><span class="sxs-lookup"><span data-stu-id="6b4ac-108">Synchronous Server Socket Example</span></span>](synchronous-server-socket-example.md)  
 <span data-ttu-id="6b4ac-109">演示如何实现接受客户端连接的同步 <xref:System.Net.Sockets.Socket> 服务器，并回传从客户端收到的数据。</span><span class="sxs-lookup"><span data-stu-id="6b4ac-109">Shows how to implement a synchronous <xref:System.Net.Sockets.Socket> server that accepts connections from a client and echoes back the data received from the client.</span></span>  
  
 [<span data-ttu-id="6b4ac-110">异步客户端套接字示例</span><span class="sxs-lookup"><span data-stu-id="6b4ac-110">Asynchronous Client Socket Example</span></span>](asynchronous-client-socket-example.md)  
 <span data-ttu-id="6b4ac-111">演示如何实现连接到服务器的同步 <xref:System.Net.Sockets.Socket> 客户端，并显示从服务器返回的数据。</span><span class="sxs-lookup"><span data-stu-id="6b4ac-111">Shows how to implement an asynchronous <xref:System.Net.Sockets.Socket> client that connects to a server and displays the data returned from the server.</span></span>  
  
 [<span data-ttu-id="6b4ac-112">异步服务器套接字示例</span><span class="sxs-lookup"><span data-stu-id="6b4ac-112">Asynchronous Server Socket Example</span></span>](asynchronous-server-socket-example.md)  
 <span data-ttu-id="6b4ac-113">演示如何实现接受客户端连接的同步 <xref:System.Net.Sockets.Socket> 服务器，并回传从客户端收到的数据。</span><span class="sxs-lookup"><span data-stu-id="6b4ac-113">Shows how to implement an asynchronous <xref:System.Net.Sockets.Socket> server that accepts connections from a client and echoes back the data received from the client.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6b4ac-114">相关章节</span><span class="sxs-lookup"><span data-stu-id="6b4ac-114">Related Sections</span></span>  
 [<span data-ttu-id="6b4ac-115">套接字</span><span class="sxs-lookup"><span data-stu-id="6b4ac-115">Sockets</span></span>](sockets.md)  
 <span data-ttu-id="6b4ac-116">提供有关 <xref:System.Net.Sockets> 命名空间和 <xref:System.Net.Sockets.Socket> 类的基本信息。</span><span class="sxs-lookup"><span data-stu-id="6b4ac-116">Provides basic information about the <xref:System.Net.Sockets> namespace and the <xref:System.Net.Sockets.Socket> class.</span></span>  
  
 [<span data-ttu-id="6b4ac-117">网络编程中的安全性</span><span class="sxs-lookup"><span data-stu-id="6b4ac-117">Security in Network Programming</span></span>](security-in-network-programming.md)  
 <span data-ttu-id="6b4ac-118">描述如何使用 Internet 标准安全性和身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="6b4ac-118">Describes how to use standard Internet security and authentication techniques.</span></span>

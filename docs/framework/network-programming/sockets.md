---
title: 套接字
description: 了解 .NET Framework Socket 类，它是 Winsock32 API 提供的套接字服务的托管代码版本。
ms.date: 03/30/2017
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- Windows Sockets
- sockets, about sockets
- Socket class, about Socket class
- sockets
- requesting data from Internet, sockets
- network, sockets
- receiving data, sockets
- protocols, sockets
- Internet, sockets
ms.assetid: 10d22735-bd37-42c1-a2be-c1932f979a7d
ms.openlocfilehash: b44409a0fafc770625be55881ccef3b57045acef
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502127"
---
# <a name="sockets"></a><span data-ttu-id="fe496-103">套接字</span><span class="sxs-lookup"><span data-stu-id="fe496-103">Sockets</span></span>
<span data-ttu-id="fe496-104"><xref:System.Net.Sockets> 命名空间包含 Windows 套接字接口的托管实现。</span><span class="sxs-lookup"><span data-stu-id="fe496-104">The <xref:System.Net.Sockets> namespace contains a managed implementation of the Windows Sockets interface.</span></span> <span data-ttu-id="fe496-105"><xref:System.Net> 命名空间中的所有其他网络访问类均建立在套接字的此实现之上。</span><span class="sxs-lookup"><span data-stu-id="fe496-105">All other network-access classes in the <xref:System.Net> namespace are built on top of this implementation of sockets.</span></span>  
  
 <span data-ttu-id="fe496-106">.NET Framework <xref:System.Net.Sockets.Socket> 类是由 Winsock32 API 提供的套接字服务的托管代码版本。</span><span class="sxs-lookup"><span data-stu-id="fe496-106">The .NET Framework <xref:System.Net.Sockets.Socket> class is a managed-code version of the socket services provided by the Winsock32 API.</span></span> <span data-ttu-id="fe496-107">大多数情况下，Socket 类方法只是将数据封送到其本机 Win32 对等体中，并负责任何必要的安全检查。</span><span class="sxs-lookup"><span data-stu-id="fe496-107">In most cases, the **Socket** class methods simply marshal data into their native Win32 counterparts and handle any necessary security checks.</span></span>  
  
 <span data-ttu-id="fe496-108">Socket 类支持同步和异步两种基本模式。</span><span class="sxs-lookup"><span data-stu-id="fe496-108">The **Socket** class supports two basic modes, synchronous and asynchronous.</span></span> <span data-ttu-id="fe496-109">在同步模式下，对执行网络操作（例如 <xref:System.Net.Sockets.Socket.Send%2A> 和 <xref:System.Net.Sockets.Socket.Receive%2A>）的函数的调用等待操作完成，再将控制权返回给调用程序。</span><span class="sxs-lookup"><span data-stu-id="fe496-109">In synchronous mode, calls to functions that perform network operations (such as <xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.Receive%2A>) wait until the operation completes before returning control to the calling program.</span></span> <span data-ttu-id="fe496-110">在异步模式下，这些调用立即返回。</span><span class="sxs-lookup"><span data-stu-id="fe496-110">In asynchronous mode, these calls return immediately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe496-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="fe496-111">See also</span></span>

- [<span data-ttu-id="fe496-112">如何：创建套接字</span><span class="sxs-lookup"><span data-stu-id="fe496-112">How to: Create a Socket</span></span>](how-to-create-a-socket.md)

- [<span data-ttu-id="fe496-113">使用应用程序协议</span><span class="sxs-lookup"><span data-stu-id="fe496-113">Using Application Protocols</span></span>](using-application-protocols.md)

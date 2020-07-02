---
title: 如何：创建套接字
description: 了解如何初始化套接字以与远程设备通信。 使用 Socket 类指定地址系列、套接字类型和协议类型。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- Networking
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- Socket class, creating sockets
- Network Resources
- receiving data, sockets
- protocols, sockets
- Internet, sockets
- sockets, creating
ms.assetid: c64a049c-5981-43bc-a2dc-1851473589c7
ms.openlocfilehash: 1d56ddea721b54192a7dd47d144b6c41bbb9a5d7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502543"
---
# <a name="how-to-create-a-socket"></a><span data-ttu-id="d12d8-104">如何：创建套接字</span><span class="sxs-lookup"><span data-stu-id="d12d8-104">How to: Create a Socket</span></span>
<span data-ttu-id="d12d8-105">必须先使用协议和网络地址信息初始化套接字，然后才能使用套接字与远程设备进行通信。</span><span class="sxs-lookup"><span data-stu-id="d12d8-105">Before you can use a socket to communicate with remote devices, the socket must be initialized with protocol and network address information.</span></span> <span data-ttu-id="d12d8-106"><xref:System.Net.Sockets.Socket> 类的构造函数包含的参数可以指定地址系列、套接字类型，以及套接字用于建立连接的协议类型。</span><span class="sxs-lookup"><span data-stu-id="d12d8-106">The constructor for the <xref:System.Net.Sockets.Socket> class has parameters that specify the address family, socket type, and protocol type that the socket uses to make connections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d12d8-107">示例</span><span class="sxs-lookup"><span data-stu-id="d12d8-107">Example</span></span>  
 <span data-ttu-id="d12d8-108">下例创建的套接字可用于与基于 TCP/IP 的网络（例如 Internet）进行通信。</span><span class="sxs-lookup"><span data-stu-id="d12d8-108">The following example creates a Socket that can be used to communicate on a TCP/IP-based network, such as the Internet.</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 <span data-ttu-id="d12d8-109">使用 UDP 而不是 TCP更改协议类型，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="d12d8-109">To use UDP instead of TCP, change the protocol type, as in the following example:</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 <span data-ttu-id="d12d8-110"><xref:System.Net.Sockets.AddressFamily> 枚举指定 Socket 类用其解析网络地址的标准地址系列（例如，AddressFamily.InterNetwork 成员指定 IP 版本 4 地址系列） 。</span><span class="sxs-lookup"><span data-stu-id="d12d8-110">The <xref:System.Net.Sockets.AddressFamily> enumeration specifies the standard address families used by the **Socket** class to resolve network addresses (for example, the **AddressFamily.InterNetwork** member specifies the IP version 4 address family).</span></span>  
  
 <span data-ttu-id="d12d8-111"><xref:System.Net.Sockets.SocketType> 枚举指定套接字的类型（例如，SocketType.Stream 成员指定用流控制来发送和接收数据的标准套接字）。</span><span class="sxs-lookup"><span data-stu-id="d12d8-111">The <xref:System.Net.Sockets.SocketType> enumeration specifies the type of socket (for example, the **SocketType.Stream** member indicates a standard socket for sending and receiving data with flow control).</span></span>  
  
 <span data-ttu-id="d12d8-112"><xref:System.Net.Sockets.ProtocolType> 枚举指定通信时套接字使用的网络协议（例如：ProtocolType.Tcp 表示套接字使用 TCP；ProtocolType.Udp 表示套接字使用 UDP）  。</span><span class="sxs-lookup"><span data-stu-id="d12d8-112">The <xref:System.Net.Sockets.ProtocolType> enumeration specifies the network protocol to use when communicating on the **Socket** (for example, **ProtocolType.Tcp** indicates that the socket uses TCP; **ProtocolType.Udp** indicates that the socket uses UDP).</span></span>  
  
 <span data-ttu-id="d12d8-113">套接字创建完成后，可启动与远程终结点的连接或接收来自远程设备的连接。</span><span class="sxs-lookup"><span data-stu-id="d12d8-113">After a **Socket** is created, it can either initiate a connection to a remote endpoint or receive connections from remote devices.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d12d8-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="d12d8-114">See also</span></span>

- [<span data-ttu-id="d12d8-115">使用客户端套接字</span><span class="sxs-lookup"><span data-stu-id="d12d8-115">Using Client Sockets</span></span>](using-client-sockets.md)
- [<span data-ttu-id="d12d8-116">使用套接字侦听</span><span class="sxs-lookup"><span data-stu-id="d12d8-116">Listening with Sockets</span></span>](listening-with-sockets.md)

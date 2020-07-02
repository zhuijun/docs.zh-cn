---
title: 使用套接字侦听
description: 了解如何创建远程服务，其中服务器套接字会打开网络上的一个端口并等待客户端连接到该端口。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- sockets, listening with sockets
- data requests, sockets
- requesting data from Internet, sockets
- receiving data, sockets
- protocols, sockets
- listening with sockets
- Internet, sockets
ms.assetid: 40e426cc-13db-4371-95eb-f7388bd23ebf
ms.openlocfilehash: 0b6de67772bae397373e307ec02ce69a71b0542e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502309"
---
# <a name="listening-with-sockets"></a><span data-ttu-id="8a626-103">使用套接字侦听</span><span class="sxs-lookup"><span data-stu-id="8a626-103">Listening with Sockets</span></span>
<span data-ttu-id="8a626-104">侦听器或服务器套接字打开网络上的端口，然后等待客户端连接到该端口。</span><span class="sxs-lookup"><span data-stu-id="8a626-104">Listener or server sockets open a port on the network and then wait for a client to connect to that port.</span></span> <span data-ttu-id="8a626-105">虽然存在其他网络地址系列和协议，但本示例演示如何创建 TCP/IP 网络的远程服务。</span><span class="sxs-lookup"><span data-stu-id="8a626-105">Although other network address families and protocols exist, this example shows how to create remote service for a TCP/IP network.</span></span>  
  
 <span data-ttu-id="8a626-106">通过将主机的 IP 地址与服务的端口号组合来定义 TCP/IP 服务的唯一地址，以创建该服务的终结点。</span><span class="sxs-lookup"><span data-stu-id="8a626-106">The unique address of a TCP/IP service is defined by combining the IP address of the host with the port number of the service to create an endpoint for the service.</span></span> <span data-ttu-id="8a626-107"><xref:System.Net.Dns> 类提供了返回有关本地网络设备支持的网络地址信息的方法。</span><span class="sxs-lookup"><span data-stu-id="8a626-107">The <xref:System.Net.Dns> class provides methods that return information about the network addresses supported by the local network device.</span></span> <span data-ttu-id="8a626-108">如果本地网络设备有多个网络地址或本地系统支持多个网络设备，该 Dns 类将返回所有网络地址信息，并且应用程序必须为此服务选择正确的地址。</span><span class="sxs-lookup"><span data-stu-id="8a626-108">When the local network device has more than one network address, or if the local system supports more than one network device, the **Dns** class returns information about all network addresses, and the application must choose the proper address for the service.</span></span> <span data-ttu-id="8a626-109">Internet 编号分配机构 (IANA) 定义公共服务的端口号；有关详细信息，请参阅 [服务名称和传输协议端口号注册表](https://www.iana.org/assignments/port-numbers)。</span><span class="sxs-lookup"><span data-stu-id="8a626-109">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services; for more information, see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/port-numbers).</span></span> <span data-ttu-id="8a626-110">其他服务可具有 1,024 到 65,535 范围内的注册端口号。</span><span class="sxs-lookup"><span data-stu-id="8a626-110">Other services can have registered port numbers in the range 1,024 to 65,535.</span></span>  
  
 <span data-ttu-id="8a626-111">通过将主机计算机的 Dns 返回的第一个 IP 地址与从已注册端口号范围内选择的端口号组合，以下示例为服务器创建 <xref:System.Net.IPEndPoint>。</span><span class="sxs-lookup"><span data-stu-id="8a626-111">The following example creates an <xref:System.Net.IPEndPoint> for a server by combining the first IP address returned by **Dns** for the host computer with a port number chosen from the registered port numbers range.</span></span>  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.GetHostEntry(Dns.GetHostName())  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
Dim localEndPoint As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.GetHostEntry(Dns.GetHostName());  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
IPEndPoint localEndPoint = new IPEndPoint(ipAddress, 11000);  
```  
  
 <span data-ttu-id="8a626-112">确定本地终结点后，<xref:System.Net.Sockets.Socket> 必须与使用 <xref:System.Net.Sockets.Socket.Bind%2A> 方法的终结点相关联，并且设置为在使用 <xref:System.Net.Sockets.Socket.Listen%2A> 方法的终结点上侦听。</span><span class="sxs-lookup"><span data-stu-id="8a626-112">After the local endpoint is determined, the <xref:System.Net.Sockets.Socket> must be associated with that endpoint using the <xref:System.Net.Sockets.Socket.Bind%2A> method and set to listen on the endpoint using the <xref:System.Net.Sockets.Socket.Listen%2A> method.</span></span> <span data-ttu-id="8a626-113">如果特定的地址和端口组合已在使用中，绑定将引发异常。</span><span class="sxs-lookup"><span data-stu-id="8a626-113">**Bind** throws an exception if the specific address and port combination is already in use.</span></span> <span data-ttu-id="8a626-114">以下示例显示了将套接字与 IPEndPoint 相关联。</span><span class="sxs-lookup"><span data-stu-id="8a626-114">The following example demonstrates associating a **Socket** with an **IPEndPoint**.</span></span>  
  
```vb  
Dim listener As New Socket(ipAddress.AddressFamily, _  
    SocketType.Stream, ProtocolType.Tcp)
listener.Bind(localEndPoint)  
listener.Listen(100)  
```  
  
```csharp  
Socket listener = new Socket(ipAddress.AddressFamily,
    SocketType.Stream, ProtocolType.Tcp);
listener.Bind(localEndPoint);  
listener.Listen(100);  
```  
  
 <span data-ttu-id="8a626-115">Listen 方法使用一个参数，该参数指定在服务器忙错误返回到连接客户端之前，允许的挂起套接字连接的数目。</span><span class="sxs-lookup"><span data-stu-id="8a626-115">The **Listen** method takes a single parameter that specifies how many pending connections to the **Socket** are allowed before a server busy error is returned to the connecting client.</span></span> <span data-ttu-id="8a626-116">在这种情况下，在服务器忙响应返回到客户端编号 101 前，最多 100 个客户端置于连接队列中。</span><span class="sxs-lookup"><span data-stu-id="8a626-116">In this case, up to 100 clients are placed in the connection queue before a server busy response is returned to client number 101.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a626-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="8a626-117">See also</span></span>

- [<span data-ttu-id="8a626-118">使用同步服务器套接字</span><span class="sxs-lookup"><span data-stu-id="8a626-118">Using a Synchronous Server Socket</span></span>](using-a-synchronous-server-socket.md)
- [<span data-ttu-id="8a626-119">使用异步服务器套接字</span><span class="sxs-lookup"><span data-stu-id="8a626-119">Using an Asynchronous Server Socket</span></span>](using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="8a626-120">使用客户端套接字</span><span class="sxs-lookup"><span data-stu-id="8a626-120">Using Client Sockets</span></span>](using-client-sockets.md)
- [<span data-ttu-id="8a626-121">如何：创建套接字</span><span class="sxs-lookup"><span data-stu-id="8a626-121">How to: Create a Socket</span></span>](how-to-create-a-socket.md)
- [<span data-ttu-id="8a626-122">套接字</span><span class="sxs-lookup"><span data-stu-id="8a626-122">Sockets</span></span>](sockets.md)

---
title: 使用客户端套接字
description: 此示例演示如何使用 .NET Framework 中的套接字创建到远程服务的 TCP/IP 连接。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- receiving data, sockets
- Socket class, client sockets
- protocols, sockets
- Internet, sockets
- sockets, client sockets
- client sockets
ms.assetid: 81de9f59-8177-4d98-b25d-43fc32a98383
ms.openlocfilehash: 1dc02d0b3651d5766d1d30752566217d8417af0c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501997"
---
# <a name="using-client-sockets"></a><span data-ttu-id="c9fcd-103">使用客户端套接字</span><span class="sxs-lookup"><span data-stu-id="c9fcd-103">Using Client Sockets</span></span>
<span data-ttu-id="c9fcd-104">在通过 <xref:System.Net.Sockets.Socket> 发起对话之前，必须在应用程序和远程设备之间创建数据管道。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-104">Before you can initiate a conversation through a <xref:System.Net.Sockets.Socket>, you must create a data pipe between your application and the remote device.</span></span> <span data-ttu-id="c9fcd-105">尽管存在其他网络地址系列和协议，但本示例说明如何创建与远程服务的 TCP/IP 连接。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-105">Although other network address families and protocols exist, this example shows how to create a TCP/IP connection to a remote service.</span></span>  
  
 <span data-ttu-id="c9fcd-106">TCP/IP 使用一个网络地址和一个服务端口号来对唯一标识设备。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-106">TCP/IP uses a network address and a service port number to uniquely identify a service.</span></span> <span data-ttu-id="c9fcd-107">网络地址标识网络上的特定设备；端口号标识该设备要连接到的特定服务。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-107">The network address identifies a specific device on the network; the port number identifies the specific service on that device to connect to.</span></span> <span data-ttu-id="c9fcd-108">网络地址和服务端口的组合称为终结点，它在 .NET Framework 中由 <xref:System.Net.EndPoint> 类表示。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-108">The combination of network address and service port is called an endpoint, which is represented in the .NET Framework by the <xref:System.Net.EndPoint> class.</span></span> <span data-ttu-id="c9fcd-109">会为每个受支持的地址系列定义 EndPoint 的后代；对于 IP 地址系列，类为 <xref:System.Net.IPEndPoint>。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-109">A descendant of **EndPoint** is defined for each supported address family; for the IP address family, the class is <xref:System.Net.IPEndPoint>.</span></span>  
  
 <span data-ttu-id="c9fcd-110"><xref:System.Net.Dns> 类向使用 TCP/IP Internet 服务的应用程序提供域名服务。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-110">The <xref:System.Net.Dns> class provides domain-name services to applications that use TCP/IP Internet services.</span></span> <span data-ttu-id="c9fcd-111"><xref:System.Net.Dns.Resolve%2A> 方法查询 DNS 服务器以将用户友好的域名（如“host.contoso.com”）映射到数字形式的 Internet 地址（如 192.168.1.1）。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-111">The <xref:System.Net.Dns.Resolve%2A> method queries a DNS server to map a user-friendly domain name (such as "host.contoso.com") to a numeric Internet address (such as 192.168.1.1).</span></span> <span data-ttu-id="c9fcd-112">Resolve 返回一个 <xref:System.Net.IPHostEntry>，其包含所请求名称的地址和别名的列表。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-112">**Resolve** returns an <xref:System.Net.IPHostEntry> that contains a list of addresses and aliases for the requested name.</span></span> <span data-ttu-id="c9fcd-113">在大多数情况下，可以使用 <xref:System.Net.IPHostEntry.AddressList%2A> 数组中返回的第一个地址。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-113">In most cases, you can use the first address returned in the <xref:System.Net.IPHostEntry.AddressList%2A> array.</span></span> <span data-ttu-id="c9fcd-114">下面的代码获取一个包含服务器 host.contoso.com 的 IP 地址的 <xref:System.Net.IPAddress>。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-114">The following code gets an <xref:System.Net.IPAddress> containing the IP address for the server host.contoso.com.</span></span>  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 <span data-ttu-id="c9fcd-115">Internet 编号分配机构 (IANA) 定义公共服务的端口号；有关详细信息，请参阅[服务名称和传输协议端口号注册表](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-115">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (for more information, see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span></span> <span data-ttu-id="c9fcd-116">其他服务可具有 1,024 到 65,535 范围内的注册端口号。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-116">Other services can have registered port numbers in the range 1,024 to 65,535.</span></span> <span data-ttu-id="c9fcd-117">以下代码将 host.contoso.com 的 IP 地址与端口号组合，为连接创建远程终结点。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-117">The following code combines the IP address for host.contoso.com with a port number to create a remote endpoint for a connection.</span></span>  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 <span data-ttu-id="c9fcd-118">确定远程设备的地址并选择要用于连接的端口后，应用程序便可以尝试建立与远程设备的连接。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-118">After determining the address of the remote device and choosing a port to use for the connection, the application can attempt to establish a connection with the remote device.</span></span> <span data-ttu-id="c9fcd-119">下面的示例使用现有的 IPEndPoint 连接到远程设备，并捕获引发的任何异常。</span><span class="sxs-lookup"><span data-stu-id="c9fcd-119">The following example uses an existing **IPEndPoint** to connect to a remote device and catches any exceptions that are thrown.</span></span>  
  
```vb  
Try  
    s.Connect(ipe)  
Catch ae As ArgumentNullException  
    Console.WriteLine("ArgumentNullException : {0}", _  
        ae.ToString())  
Catch se As SocketException  
    Console.WriteLine("SocketException : {0}", se.ToString())  
Catch e As Exception  
    Console.WriteLine("Unexpected exception : {0}", e.ToString())  
End Try  
```  
  
```csharp  
try {  
    s.Connect(ipe);  
} catch(ArgumentNullException ae) {  
    Console.WriteLine("ArgumentNullException : {0}", ae.ToString());  
} catch(SocketException se) {  
    Console.WriteLine("SocketException : {0}", se.ToString());  
} catch(Exception e) {  
    Console.WriteLine("Unexpected exception : {0}", e.ToString());  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="c9fcd-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="c9fcd-120">See also</span></span>

- [<span data-ttu-id="c9fcd-121">使用同步客户端套接字</span><span class="sxs-lookup"><span data-stu-id="c9fcd-121">Using a Synchronous Client Socket</span></span>](using-a-synchronous-client-socket.md)
- [<span data-ttu-id="c9fcd-122">使用异步客户端套接字</span><span class="sxs-lookup"><span data-stu-id="c9fcd-122">Using an Asynchronous Client Socket</span></span>](using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="c9fcd-123">如何：创建套接字</span><span class="sxs-lookup"><span data-stu-id="c9fcd-123">How to: Create a Socket</span></span>](how-to-create-a-socket.md)
- [<span data-ttu-id="c9fcd-124">套接字</span><span class="sxs-lookup"><span data-stu-id="c9fcd-124">Sockets</span></span>](sockets.md)

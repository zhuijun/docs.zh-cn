---
title: 使用 UDP 服务
description: UdpClient 类摘录详细信息，以在 .NET Framework 中创建套接字来使用 UDP 请求和接收数据。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- protocols, UDP
- network resources, UDP
- requesting data from Internet, UDP
- UDP
- receiving data, UDP
- Internet, UDP
- broadcasting messages to multiple addresses
- data requests, UDP
- UdpClient class, about UdpClient class
- sending data, UDP
- application protocols, UDP
ms.assetid: d5c3477a-e798-454c-a890-738ba14c5707
ms.openlocfilehash: 4c2e88492f737800151d30097719d7d011054a5e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501945"
---
# <a name="use-udp-services"></a><span data-ttu-id="13ea2-103">使用 UDP 服务</span><span class="sxs-lookup"><span data-stu-id="13ea2-103">Use UDP services</span></span>

<span data-ttu-id="13ea2-104"><xref:System.Net.Sockets.UdpClient> 类使用 UDP与网络服务通信。</span><span class="sxs-lookup"><span data-stu-id="13ea2-104">The <xref:System.Net.Sockets.UdpClient> class communicates with network services using UDP.</span></span> <span data-ttu-id="13ea2-105"><xref:System.Net.Sockets.UdpClient> 类的属性和方法概要说明了使用 UDP 创建 <xref:System.Net.Sockets.Socket> 以请求和接收数据的详情。</span><span class="sxs-lookup"><span data-stu-id="13ea2-105">The properties and methods of the <xref:System.Net.Sockets.UdpClient> class abstract the details of creating a <xref:System.Net.Sockets.Socket> for requesting and receiving data using UDP.</span></span>

<span data-ttu-id="13ea2-106">用户数据报协议 (UDP) 是一种简单协议，非常适合用于将数据传递到远程主机。</span><span class="sxs-lookup"><span data-stu-id="13ea2-106">User Datagram Protocol (UDP) is a simple protocol that makes a best effort to deliver data to a remote host.</span></span> <span data-ttu-id="13ea2-107">但由于 UDP 协议是一种无连接协议，因此发送到远程终结点的 UDP 数据报不一定可到达，也无法保证其能以发送的相同顺序到达。</span><span class="sxs-lookup"><span data-stu-id="13ea2-107">However, because the UDP protocol is a connectionless protocol, UDP datagrams sent to the remote endpoint are not guaranteed to arrive, nor are they guaranteed to arrive in the same sequence in which they are sent.</span></span> <span data-ttu-id="13ea2-108">使用 UDP 的应用程序必须准备好处理丢失的、重复的和乱序的数据报。</span><span class="sxs-lookup"><span data-stu-id="13ea2-108">Applications that use UDP must be prepared to handle missing, duplicate, and out-of-sequence datagrams.</span></span>

<span data-ttu-id="13ea2-109">要使用 UDP 发送数据报，必须知道承载所需服务的网络设备的网络地址以及该服务用来通信的 UDP 端口号。</span><span class="sxs-lookup"><span data-stu-id="13ea2-109">To send a datagram using UDP, you must know the network address of the network device hosting the service you need and the UDP port number that the service uses to communicate.</span></span> <span data-ttu-id="13ea2-110">Internet 编号分配机构 (IANA) 定义公共服务的端口号（请参阅[服务名称和传输协议端口号注册表](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)）。</span><span class="sxs-lookup"><span data-stu-id="13ea2-110">The Internet Assigned Numbers Authority (IANA) defines port numbers for common services (see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span></span> <span data-ttu-id="13ea2-111">不在 IANA 列表上的服务可使用 1,024 到 65,535 范围内的端口号。</span><span class="sxs-lookup"><span data-stu-id="13ea2-111">Services not on the IANA list can have port numbers in the range 1,024 to 65,535.</span></span>

<span data-ttu-id="13ea2-112">特殊网络地址用于支持基于 IP 的网络上的 UDP 广播消息。</span><span class="sxs-lookup"><span data-stu-id="13ea2-112">Special network addresses are used to support UDP broadcast messages on IP-based networks.</span></span> <span data-ttu-id="13ea2-113">下面的讨论以 Internet 上使用的 IP 版本 4 地址系列作为示例。</span><span class="sxs-lookup"><span data-stu-id="13ea2-113">The following discussion uses the IP version 4 address family used on the Internet as an example.</span></span>

<span data-ttu-id="13ea2-114">IP 版本 4 地址使用 32 位指定网络地址。</span><span class="sxs-lookup"><span data-stu-id="13ea2-114">IP version 4 addresses use 32 bits to specify a network address.</span></span> <span data-ttu-id="13ea2-115">对于使用 255.255.255.0 网络掩码的 C 类地址，这些数位被分为四个八进制数。</span><span class="sxs-lookup"><span data-stu-id="13ea2-115">For class C addresses using a netmask of 255.255.255.0, these bits are separated into four octets.</span></span> <span data-ttu-id="13ea2-116">当以十进制数表示时，这四个八进制数构成我们熟悉的以点分隔的四部分表示法，如 192.168.100.2。</span><span class="sxs-lookup"><span data-stu-id="13ea2-116">When expressed in decimal, the four octets form the familiar dotted-quad notation, such as 192.168.100.2.</span></span> <span data-ttu-id="13ea2-117">前两个八进制数（此示例中的 192.168）构成网络号码，第三个八进制数 (100) 定义子网，最后一个八进制数 (2) 则是主机标识符。</span><span class="sxs-lookup"><span data-stu-id="13ea2-117">The first two octets (192.168 in this example) form the network number, the third octet (100) defines the subnet, and the final octet (2) is the host identifier.</span></span>

<span data-ttu-id="13ea2-118">将 IP 地址的所有数位均设置为同一个（即 255.255.255.255），可构成有限的广播地址。</span><span class="sxs-lookup"><span data-stu-id="13ea2-118">Setting all the bits of an IP address to one, or 255.255.255.255, forms the limited broadcast address.</span></span> <span data-ttu-id="13ea2-119">将 UDP 数据报发送到此地址会将消息传递到本地网络段上的任何主机。</span><span class="sxs-lookup"><span data-stu-id="13ea2-119">Sending a UDP datagram to this address delivers the message to any host on the local network segment.</span></span> <span data-ttu-id="13ea2-120">由于路由器不会转发发送到此地址的消息，因此只有网络段上的主机会接收到广播消息。</span><span class="sxs-lookup"><span data-stu-id="13ea2-120">Because routers never forward messages sent to this address, only hosts on the network segment receive the broadcast message.</span></span>

<span data-ttu-id="13ea2-121">通过设置主机标识符的所有数位，可以将广播定向到网络的特定部分。</span><span class="sxs-lookup"><span data-stu-id="13ea2-121">Broadcasts can be directed to specific portions of a network by setting all bits of the host identifier.</span></span> <span data-ttu-id="13ea2-122">例如，若要将广播发送到以 192.168.1 开头的 IP 地址标识的网络上的所有主机，请使用地址 192.168.1.255。</span><span class="sxs-lookup"><span data-stu-id="13ea2-122">For example, to send a broadcast to all hosts on the network identified by IP addresses starting with 192.168.1, use the address 192.168.1.255.</span></span>

<span data-ttu-id="13ea2-123">下面的示例代码使用 <xref:System.Net.Sockets.UdpClient> 侦听端口 11,000 上的 UDP 数据报。</span><span class="sxs-lookup"><span data-stu-id="13ea2-123">The following code example uses a <xref:System.Net.Sockets.UdpClient> to listen for UDP datagrams on port 11,000.</span></span> <span data-ttu-id="13ea2-124">客户端将接收消息字符串并将消息写入控制台。</span><span class="sxs-lookup"><span data-stu-id="13ea2-124">The client receives a message string and writes the message to the console.</span></span>

```vb
Imports System.Net
Imports System.Net.Sockets
Imports System.Text

Public Class UDPListener
   Private Const listenPort As Integer = 11000

   Private Shared Sub StartListener()
      Dim listener As New UdpClient(listenPort)
      Dim groupEP As New IPEndPoint(IPAddress.Any, listenPort)
      Try
         While True
            Console.WriteLine("Waiting for broadcast")
            Dim bytes As Byte() = listener.Receive(groupEP)
            Console.WriteLine("Received broadcast from {0} :", groupEP)
            Console.WriteLine(Encoding.ASCII.GetString(bytes, 0, bytes.Length))
         End While
      Catch e As SocketException
         Console.WriteLine(e)
      Finally
         listener.Close()
      End Try
   End Sub 'StartListener

   Public Shared Sub Main()
      StartListener()
   End Sub 'Main
End Class 'UDPListener
```

```csharp
using System;
using System.Net;
using System.Net.Sockets;
using System.Text;

public class UDPListener
{
    private const int listenPort = 11000;

    private static void StartListener()
    {
        UdpClient listener = new UdpClient(listenPort);
        IPEndPoint groupEP = new IPEndPoint(IPAddress.Any, listenPort);

        try
        {
            while (true)
            {
                Console.WriteLine("Waiting for broadcast");
                byte[] bytes = listener.Receive(ref groupEP);

                Console.WriteLine($"Received broadcast from {groupEP} :");
                Console.WriteLine($" {Encoding.ASCII.GetString(bytes, 0, bytes.Length)}");
            }
        }
        catch (SocketException e)
        {
            Console.WriteLine(e);
        }
        finally
        {
            listener.Close();
        }
    }

    public static void Main()
    {
        StartListener();
    }
}
```

<span data-ttu-id="13ea2-125">下面的代码示例使用 <xref:System.Net.Sockets.Socket> 将 UDP 数据报用端口 11,000 发送到定向广播地址 192.168.1.255。</span><span class="sxs-lookup"><span data-stu-id="13ea2-125">The following code example uses a <xref:System.Net.Sockets.Socket> to send UDP datagrams to the directed broadcast address 192.168.1.255, using port 11,000.</span></span> <span data-ttu-id="13ea2-126">客户端将发送在命令行上指定的消息字符串。</span><span class="sxs-lookup"><span data-stu-id="13ea2-126">The client sends the message string specified on the command line.</span></span>

```vb
Imports System.Net
Imports System.Net.Sockets
Imports System.Text

Public Class Program
    Public Shared Sub Main(args() As [String])
      Dim s As New Socket(AddressFamily.InterNetwork, SocketType.Dgram, ProtocolType.Udp)
      Dim broadcast As IPAddress = IPAddress.Parse("192.168.1.255")
      Dim sendbuf As Byte() = Encoding.ASCII.GetBytes(args(0))
      Dim ep As New IPEndPoint(broadcast, 11000)
      s.SendTo(sendbuf, ep)
      Console.WriteLine("Message sent to the broadcast address")
   End Sub 'Main
End Class
```

```csharp
using System;
using System.Net;
using System.Net.Sockets;
using System.Text;

class Program
{
    static void Main(string[] args)
    {
        Socket s = new Socket(AddressFamily.InterNetwork, SocketType.Dgram, ProtocolType.Udp);

        IPAddress broadcast = IPAddress.Parse("192.168.1.255");

        byte[] sendbuf = Encoding.ASCII.GetBytes(args[0]);
        IPEndPoint ep = new IPEndPoint(broadcast, 11000);

        s.SendTo(sendbuf, ep);

        Console.WriteLine("Message sent to the broadcast address");
    }
}
```

## <a name="see-also"></a><span data-ttu-id="13ea2-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="13ea2-127">See also</span></span>

- <xref:System.Net.Sockets.UdpClient>
- <xref:System.Net.IPAddress>

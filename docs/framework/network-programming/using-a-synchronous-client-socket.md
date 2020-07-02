---
title: 使用同步客户端套接字
description: 此示例演示 .NET Framework 中的同步客户端套接字，这将在网络操作完成时挂起应用程序。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- synchronous client sockets
- Socket class, synchronous client sockets
- receiving data, sockets
- sockets, synchronous client sockets
- protocols, sockets
- Internet, sockets
- client sockets
ms.assetid: 945d00c6-7202-466c-9df9-140b84156d43
ms.openlocfilehash: ef682af33c10cf06ffc398c22e4a7dc1adf8290e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502062"
---
# <a name="using-a-synchronous-client-socket"></a><span data-ttu-id="6ea73-103">使用同步客户端套接字</span><span class="sxs-lookup"><span data-stu-id="6ea73-103">Using a Synchronous Client Socket</span></span>
<span data-ttu-id="6ea73-104">网络操作完成过程中，同步客户端套接字会挂起应用程序。</span><span class="sxs-lookup"><span data-stu-id="6ea73-104">A synchronous client socket suspends the application program while the network operation completes.</span></span> <span data-ttu-id="6ea73-105">同步套接字不适用于在操作中大量使用网络的应用程序，但它们可以为其他应用程序启用对网络服务的简单访问。</span><span class="sxs-lookup"><span data-stu-id="6ea73-105">Synchronous sockets are not suitable for applications that make heavy use of the network for their operation, but they can enable simple access to network services for other applications.</span></span>  
  
 <span data-ttu-id="6ea73-106">若要发送数据，请将字节数组传递到 <xref:System.Net.Sockets.Socket> 类的数据发送方法之一（<xref:System.Net.Sockets.Socket.Send%2A> 和 <xref:System.Net.Sockets.Socket.SendTo%2A>）。</span><span class="sxs-lookup"><span data-stu-id="6ea73-106">To send data, pass a byte array to one of the <xref:System.Net.Sockets.Socket> class's send-data methods (<xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.SendTo%2A>).</span></span> <span data-ttu-id="6ea73-107">下面的示例使用 <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> 属性将字符串编码到字节数组缓冲区，然后使用 Send 方法将该缓冲区传输到网络设备。</span><span class="sxs-lookup"><span data-stu-id="6ea73-107">The following example encodes a string into a byte array buffer using the <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> property and then transmits the buffer to the network device using the **Send** method.</span></span> <span data-ttu-id="6ea73-108">Send 方法返回发送到网络设备的字节数。</span><span class="sxs-lookup"><span data-stu-id="6ea73-108">The **Send** method returns the number of bytes sent to the network device.</span></span>  
  
```vb  
Dim msg As Byte() = _  
    System.Text.Encoding.ASCII.GetBytes("This is a test.")  
Dim bytesSent As Integer = s.Send(msg)  
```  
  
```csharp  
byte[] msg = System.Text.Encoding.ASCII.GetBytes("This is a test");  
int bytesSent = s.Send(msg);  
```  
  
 <span data-ttu-id="6ea73-109">Send 方法从缓冲区移除字节，并用网络接口将这些字节排队以便发送到网络设备。</span><span class="sxs-lookup"><span data-stu-id="6ea73-109">The **Send** method removes the bytes from the buffer and queues them with the network interface to be sent to the network device.</span></span> <span data-ttu-id="6ea73-110">网络接口可能不会立即发送数据，但它最终将发送，只要使用 <xref:System.Net.Sockets.Socket.Shutdown%2A> 方法正常关闭连接。</span><span class="sxs-lookup"><span data-stu-id="6ea73-110">The network interface might not send the data immediately, but it will send it eventually, as long as the connection is closed normally with the <xref:System.Net.Sockets.Socket.Shutdown%2A> method.</span></span>  
  
 <span data-ttu-id="6ea73-111">若要从网络设备接收数据，请将缓冲区传递到 Socket 类的数据接收方法之一（<xref:System.Net.Sockets.Socket.Receive%2A> 和 <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>）。 </span><span class="sxs-lookup"><span data-stu-id="6ea73-111">To receive data from a network device, pass a buffer to one of the **Socket** class's receive-data methods (<xref:System.Net.Sockets.Socket.Receive%2A> and <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>).</span></span> <span data-ttu-id="6ea73-112">同步套接字将挂起应用程序，直到从网络收到字节或者套接字关闭。</span><span class="sxs-lookup"><span data-stu-id="6ea73-112">Synchronous sockets will suspend the application until bytes are received from the network or until the socket is closed.</span></span> <span data-ttu-id="6ea73-113">下面的示例接收来自网络的数据，然后将其显示在控制台上。</span><span class="sxs-lookup"><span data-stu-id="6ea73-113">The following example receives data from the network and then displays it on the console.</span></span> <span data-ttu-id="6ea73-114">该示例假定来自网络的数据是用 ASCII 编码的文本。</span><span class="sxs-lookup"><span data-stu-id="6ea73-114">The example assumes that the data coming from the network is ASCII-encoded text.</span></span> <span data-ttu-id="6ea73-115">Receive 方法返回从网络接收的字节数。</span><span class="sxs-lookup"><span data-stu-id="6ea73-115">The **Receive** method returns the number of bytes received from the network.</span></span>  
  
```vb  
Dim bytes(1024) As Byte  
Dim bytesRec = s.Receive(bytes)  
Console.WriteLine("Echoed text = {0}", _  
    System.Text.Encoding.ASCII.GetString(bytes, 0, bytesRec))  
```  
  
```csharp  
byte[] bytes = new byte[1024];  
int bytesRec = s.Receive(bytes);  
Console.WriteLine("Echoed text = {0}",  
    System.Text.Encoding.ASCII.GetString(bytes, 0, bytesRec));  
```  
  
 <span data-ttu-id="6ea73-116">不再需要套接字时需将其释放，方法是调用 <xref:System.Net.Sockets.Socket.Shutdown%2A> 方法，再调用 Close 方法。</span><span class="sxs-lookup"><span data-stu-id="6ea73-116">When the socket is no longer needed, you need to release it by calling the <xref:System.Net.Sockets.Socket.Shutdown%2A> method and then calling the **Close** method.</span></span> <span data-ttu-id="6ea73-117">下面的示例释放套接字。</span><span class="sxs-lookup"><span data-stu-id="6ea73-117">The following example releases a **Socket**.</span></span> <span data-ttu-id="6ea73-118"><xref:System.Net.Sockets.SocketShutdown> 枚举定义常数以指示应该关闭套接字用于发送，还是用于接收，或者用于两者。</span><span class="sxs-lookup"><span data-stu-id="6ea73-118">The <xref:System.Net.Sockets.SocketShutdown> enumeration defines constants that indicate whether the socket should be closed for sending, for receiving, or for both.</span></span>  
  
```vb  
s.Shutdown(SocketShutdown.Both)  
s.Close()  
```  
  
```csharp  
s.Shutdown(SocketShutdown.Both);  
s.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="6ea73-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="6ea73-119">See also</span></span>

- [<span data-ttu-id="6ea73-120">使用异步客户端套接字</span><span class="sxs-lookup"><span data-stu-id="6ea73-120">Using an Asynchronous Client Socket</span></span>](using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="6ea73-121">使用套接字侦听</span><span class="sxs-lookup"><span data-stu-id="6ea73-121">Listening with Sockets</span></span>](listening-with-sockets.md)
- [<span data-ttu-id="6ea73-122">同步客户端套接字示例</span><span class="sxs-lookup"><span data-stu-id="6ea73-122">Synchronous Client Socket Example</span></span>](synchronous-client-socket-example.md)

---
title: 使用异步客户端套接字
description: 此示例演示异步客户端套接字。 借助 .NET Framework 异步编程，应用程序可以在处理连接时继续运行。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- asynchronous client sockets
- Socket class, asynchronous client sockets
- requesting data from Internet, sockets
- sockets, asynchronous client sockets
- receiving data, sockets
- protocols, sockets
- Internet, sockets
- client sockets
ms.assetid: fd85bc88-e06c-467d-a30d-9fd7cffcfca1
ms.openlocfilehash: 9cf46e9519bcecf4d7a20ff99b86fa5f66af2087
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502036"
---
# <a name="using-an-asynchronous-client-socket"></a><span data-ttu-id="0463a-104">使用异步客户端套接字</span><span class="sxs-lookup"><span data-stu-id="0463a-104">Using an Asynchronous Client Socket</span></span>
<span data-ttu-id="0463a-105">异步客户端套接字在等待网络操作完成时不会挂起应用程序。</span><span class="sxs-lookup"><span data-stu-id="0463a-105">An asynchronous client socket does not suspend the application while waiting for network operations to complete.</span></span> <span data-ttu-id="0463a-106">相反，它使用标准 .NET Framework 异步编程模型在一个线程上处理网络连接，而应用程序继续在原始线程上运行。</span><span class="sxs-lookup"><span data-stu-id="0463a-106">Instead, it uses the standard .NET Framework asynchronous programming model to process the network connection on one thread while the application continues to run on the original thread.</span></span> <span data-ttu-id="0463a-107">异步套接字适用于大量使用网络或不宜等待网络操作完成（才可继续运作）的应用程序。</span><span class="sxs-lookup"><span data-stu-id="0463a-107">Asynchronous sockets are appropriate for applications that make heavy use of the network or that cannot wait for network operations to complete before continuing.</span></span>  
  
 <span data-ttu-id="0463a-108"><xref:System.Net.Sockets.Socket> 类遵循异步方法的 .NET Framework 命名模式；例如，同步 <xref:System.Net.Sockets.Socket.Receive%2A> 方法对应于异步 <xref:System.Net.Sockets.Socket.BeginReceive%2A> 和 <xref:System.Net.Sockets.Socket.EndReceive%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="0463a-108">The <xref:System.Net.Sockets.Socket> class follows the .NET Framework naming pattern for asynchronous methods; for example, the synchronous <xref:System.Net.Sockets.Socket.Receive%2A> method corresponds to the asynchronous <xref:System.Net.Sockets.Socket.BeginReceive%2A> and <xref:System.Net.Sockets.Socket.EndReceive%2A> methods.</span></span>  
  
 <span data-ttu-id="0463a-109">异步操作要求使用回调方法返回操作结果。</span><span class="sxs-lookup"><span data-stu-id="0463a-109">Asynchronous operations require a callback method to return the result of the operation.</span></span> <span data-ttu-id="0463a-110">如果应用程序不需要知道结果，则不需要任何回调方法。</span><span class="sxs-lookup"><span data-stu-id="0463a-110">If your application does not need to know the result, then no callback method is required.</span></span> <span data-ttu-id="0463a-111">本节中的示例代码阐释如何使用某个方法开始连接到网络设备并使用回调方法完成此连接、如何使用某个方法开始发送数据并使用回调方法完成此次发送，以及如何使用某个方法开始接收数据并使用回调方法结束接收数据。</span><span class="sxs-lookup"><span data-stu-id="0463a-111">The example code in this section demonstrates using a method to start connecting to a network device and a callback method to complete the connection, a method to start sending data and a callback method to complete the send, and a method to start receiving data and a callback method to end receiving data.</span></span>  
  
 <span data-ttu-id="0463a-112">异步套接字使用系统线程池中的多个线程处理网络连接。</span><span class="sxs-lookup"><span data-stu-id="0463a-112">Asynchronous sockets use multiple threads from the system thread pool to process network connections.</span></span> <span data-ttu-id="0463a-113">一个线程负责发起数据的发送或接收；其他线程完成与网络设备的连接以及发送或接收数据。</span><span class="sxs-lookup"><span data-stu-id="0463a-113">One thread is responsible for initiating the sending or receiving of data; other threads complete the connection to the network device and send or receive the data.</span></span> <span data-ttu-id="0463a-114">在以下示例中，<xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> 类的实例用于挂起主线程的执行并在执行可以继续时发出信号。</span><span class="sxs-lookup"><span data-stu-id="0463a-114">In the following examples, instances of the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class are used to suspend execution of the main thread and signal when execution can continue.</span></span>  
  
 <span data-ttu-id="0463a-115">在下面的示例中，为了将异步套接字连接到网络设备，`Connect` 方法会初始化 Socket，然后调用 <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType> 方法（传递表示网络设备的远程终结点）、连接回调方法和状态对象（即客户端 Socket，用于在异步调用之间传递状态信息） 。</span><span class="sxs-lookup"><span data-stu-id="0463a-115">In the following example, to connect an asynchronous socket to a network device, the `Connect` method initializes a **Socket** and then calls the <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType> method, passing a remote endpoint that represents the network device, the connect callback method, and a state object (the client **Socket**), which is used to pass state information between asynchronous calls.</span></span> <span data-ttu-id="0463a-116">该示例实现 `Connect` 方法，将指定的 Socket 连接到指定的终结点。</span><span class="sxs-lookup"><span data-stu-id="0463a-116">The example implements the `Connect` method to connect the specified **Socket** to the specified endpoint.</span></span> <span data-ttu-id="0463a-117">它假定一个名为 `connectDone` 的全局 ManualResetEvent。</span><span class="sxs-lookup"><span data-stu-id="0463a-117">It assumes a global **ManualResetEvent** named `connectDone`.</span></span>  
  
```vb  
Public Shared Sub Connect(remoteEP As EndPoint, client As Socket)  
    client.BeginConnect(remoteEP, _  
       AddressOf ConnectCallback, client)  
  
    connectDone.WaitOne()  
End Sub 'Connect  
```  
  
```csharp  
public static void Connect(EndPoint remoteEP, Socket client) {  
    client.BeginConnect(remoteEP,
        new AsyncCallback(ConnectCallback), client );  
  
   connectDone.WaitOne();  
}  
```  
  
 <span data-ttu-id="0463a-118">连接回调方法 `ConnectCallback` 实现 <xref:System.AsyncCallback> 委托。</span><span class="sxs-lookup"><span data-stu-id="0463a-118">The connect callback method `ConnectCallback` implements the <xref:System.AsyncCallback> delegate.</span></span> <span data-ttu-id="0463a-119">它在远程设备可用时连接到远程设备，然后通过设置 ManualResetEvent `connectDone` 向应用程序线程发出连接完成的信号。</span><span class="sxs-lookup"><span data-stu-id="0463a-119">It connects to the remote device when the remote device is available and then signals the application thread that the connection is complete by setting the **ManualResetEvent** `connectDone`.</span></span> <span data-ttu-id="0463a-120">下面的代码实现 `ConnectCallback` 方法。</span><span class="sxs-lookup"><span data-stu-id="0463a-120">The following code implements the `ConnectCallback` method.</span></span>  
  
```vb  
Private Shared Sub ConnectCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the socket from the state object.  
        Dim client As Socket = CType(ar.AsyncState, Socket)  
  
        ' Complete the connection.  
        client.EndConnect(ar)  
  
        Console.WriteLine("Socket connected to {0}", _  
            client.RemoteEndPoint.ToString())  
  
        ' Signal that the connection has been made.  
        connectDone.Set()  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'ConnectCallback  
```  
  
```csharp  
private static void ConnectCallback(IAsyncResult ar) {  
    try {  
        // Retrieve the socket from the state object.  
        Socket client = (Socket) ar.AsyncState;  
  
        // Complete the connection.  
        client.EndConnect(ar);  
  
        Console.WriteLine("Socket connected to {0}",  
            client.RemoteEndPoint.ToString());  
  
        // Signal that the connection has been made.  
        connectDone.Set();  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 <span data-ttu-id="0463a-121">示例方法 `Send` 以 ASCII 格式对指定的字符串数据进行编码，并将其异步发送到指定套接字所表示的网络设备。</span><span class="sxs-lookup"><span data-stu-id="0463a-121">The example method `Send` encodes the specified string data in ASCII format and sends it asynchronously to the network device represented by the specified socket.</span></span> <span data-ttu-id="0463a-122">以下示例实现 `Send` 方法。</span><span class="sxs-lookup"><span data-stu-id="0463a-122">The following example implements the `Send` method.</span></span>  
  
```vb  
Private Shared Sub Send(client As Socket, data As [String])  
    ' Convert the string data to byte data using ASCII encoding.  
    Dim byteData As Byte() = Encoding.ASCII.GetBytes(data)  
  
    ' Begin sending the data to the remote device.  
    client.BeginSend(byteData, 0, byteData.Length, SocketFlags.None, _  
        AddressOf SendCallback, client)  
End Sub 'Send  
```  
  
```csharp  
private static void Send(Socket client, String data) {  
    // Convert the string data to byte data using ASCII encoding.  
    byte[] byteData = Encoding.ASCII.GetBytes(data);  
  
    // Begin sending the data to the remote device.  
    client.BeginSend(byteData, 0, byteData.Length, SocketFlags.None,  
        new AsyncCallback(SendCallback), client);  
}  
```  
  
 <span data-ttu-id="0463a-123">发送回调方法 `SendCallback` 实现 <xref:System.AsyncCallback> 委托。</span><span class="sxs-lookup"><span data-stu-id="0463a-123">The send callback method `SendCallback` implements the <xref:System.AsyncCallback> delegate.</span></span> <span data-ttu-id="0463a-124">它在网络设备准备好接收时发送数据。</span><span class="sxs-lookup"><span data-stu-id="0463a-124">It sends the data when the network device is ready to receive.</span></span> <span data-ttu-id="0463a-125">下面的示例演示 `SendCallback` 方法的实现。</span><span class="sxs-lookup"><span data-stu-id="0463a-125">The following example shows the implementation of the `SendCallback` method.</span></span> <span data-ttu-id="0463a-126">它假定一个名为 `sendDone` 的全局 ManualResetEvent。</span><span class="sxs-lookup"><span data-stu-id="0463a-126">It assumes a global **ManualResetEvent** named `sendDone`.</span></span>  
  
```vb  
Private Shared Sub SendCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the socket from the state object.  
        Dim client As Socket = CType(ar.AsyncState, Socket)  
  
        ' Complete sending the data to the remote device.  
        Dim bytesSent As Integer = client.EndSend(ar)  
        Console.WriteLine("Sent {0} bytes to server.", bytesSent)  
  
        ' Signal that all bytes have been sent.  
        sendDone.Set()  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'SendCallback  
```  
  
```csharp  
private static void SendCallback(IAsyncResult ar) {  
    try {  
        // Retrieve the socket from the state object.  
        Socket client = (Socket) ar.AsyncState;  
  
        // Complete sending the data to the remote device.  
        int bytesSent = client.EndSend(ar);  
        Console.WriteLine("Sent {0} bytes to server.", bytesSent);  
  
        // Signal that all bytes have been sent.  
        sendDone.Set();  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 <span data-ttu-id="0463a-127">从客户端套接字读取数据需要一个在异步调用之间传递值的状态对象。</span><span class="sxs-lookup"><span data-stu-id="0463a-127">Reading data from a client socket requires a state object that passes values between asynchronous calls.</span></span> <span data-ttu-id="0463a-128">下面的类是一个用于从客户端套接字接收数据的示例状态对象。</span><span class="sxs-lookup"><span data-stu-id="0463a-128">The following class is an example state object for receiving data from a client socket.</span></span> <span data-ttu-id="0463a-129">它包含以下各项的字段：客户端套接字、已接收数据的缓冲区，和用于保留传入数据字符串的 <xref:System.Text.StringBuilder>。</span><span class="sxs-lookup"><span data-stu-id="0463a-129">It contains a field for the client socket, a buffer for the received data, and a <xref:System.Text.StringBuilder> to hold the incoming data string.</span></span> <span data-ttu-id="0463a-130">将这些字段放入该状态对象中，使这些字段的值在多个调用之间得以保留，以便从客户端套接字读取数据。</span><span class="sxs-lookup"><span data-stu-id="0463a-130">Placing these fields in the state object allows their values to be preserved across multiple calls to read data from the client socket.</span></span>  
  
```vb  
Public Class StateObject  
    ' Client socket.  
    Public workSocket As Socket = Nothing
    ' Size of receive buffer.  
    Public BufferSize As Integer = 256  
    ' Receive buffer.  
    Public buffer(256) As Byte
    ' Received data string.  
    Public sb As New StringBuilder()  
End Class 'StateObject  
```  
  
```csharp  
public class StateObject {  
    // Client socket.  
    public Socket workSocket = null;  
    // Size of receive buffer.  
    public const int BufferSize = 256;  
    // Receive buffer.  
    public byte[] buffer = new byte[BufferSize];  
    // Received data string.  
    public StringBuilder sb = new StringBuilder();  
}  
```  
  
 <span data-ttu-id="0463a-131">`Receive` 方法示例设置状态对象，然后调用 BeginReceive 方法从客户端套接字异步读取数据。</span><span class="sxs-lookup"><span data-stu-id="0463a-131">The example `Receive` method sets up the state object and then calls the **BeginReceive** method to read the data from the client socket asynchronously.</span></span> <span data-ttu-id="0463a-132">以下示例实现 `Receive` 方法。</span><span class="sxs-lookup"><span data-stu-id="0463a-132">The following example implements the `Receive` method.</span></span>  
  
```vb  
Private Shared Sub Receive(client As Socket)  
    Try  
        ' Create the state object.  
        Dim state As New StateObject()  
        state.workSocket = client  
  
        ' Begin receiving the data from the remote device.  
        client.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
            AddressOf ReceiveCallback, state)  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'Receive  
```  
  
```csharp  
private static void Receive(Socket client) {  
    try {  
        // Create the state object.  
        StateObject state = new StateObject();  
        state.workSocket = client;  
  
        // Begin receiving the data from the remote device.  
        client.BeginReceive( state.buffer, 0, StateObject.BufferSize, 0,  
            new AsyncCallback(ReceiveCallback), state);  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 <span data-ttu-id="0463a-133">接收回调方法 `ReceiveCallback` 实现 AsyncCallback 委托。</span><span class="sxs-lookup"><span data-stu-id="0463a-133">The receive callback method `ReceiveCallback` implements the **AsyncCallback** delegate.</span></span> <span data-ttu-id="0463a-134">它接收来自网络设备的数据并生成消息字符串。</span><span class="sxs-lookup"><span data-stu-id="0463a-134">It receives the data from the network device and builds a message string.</span></span> <span data-ttu-id="0463a-135">它将来自网络的一个或多个数据字节读入数据缓冲区，然后再次调用 BeginReceive 方法，直到客户端完成数据发送为止。</span><span class="sxs-lookup"><span data-stu-id="0463a-135">It reads one or more bytes of data from the network into the data buffer and then calls the **BeginReceive** method again until the data sent by the client is complete.</span></span> <span data-ttu-id="0463a-136">从客户端读取所有数据后，`ReceiveCallback` 通过设置 ManualResetEvent `sendDone` 向应用程序线程发出数据完成的信号。</span><span class="sxs-lookup"><span data-stu-id="0463a-136">Once all the data is read from the client, `ReceiveCallback` signals the application thread that the data is complete by setting the **ManualResetEvent** `sendDone`.</span></span>  
  
 <span data-ttu-id="0463a-137">下面的示例代码实现 `ReceiveCallback` 方法。</span><span class="sxs-lookup"><span data-stu-id="0463a-137">The following example code implements the `ReceiveCallback` method.</span></span> <span data-ttu-id="0463a-138">它假定一个名为 `response` 的全局字符串（该字符串保留接收的字符串）和一个名为 `receiveDone` 的全局 ManualResetEvent。</span><span class="sxs-lookup"><span data-stu-id="0463a-138">It assumes a global string named `response` that holds the received string and a global **ManualResetEvent** named `receiveDone`.</span></span> <span data-ttu-id="0463a-139">服务器必须正常关闭客户端套接字才能结束网络会话。</span><span class="sxs-lookup"><span data-stu-id="0463a-139">The server must shut down the client socket gracefully to end the network session.</span></span>  
  
```vb  
Private Shared Sub ReceiveCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the state object and the client socket
        ' from the asynchronous state object.  
        Dim state As StateObject = CType(ar.AsyncState, StateObject)  
        Dim client As Socket = state.workSocket  
  
        ' Read data from the remote device.  
        Dim bytesRead As Integer = client.EndReceive(ar)  
  
        If bytesRead > 0 Then  
            ' There might be more data, so store the data received so far.  
            state.sb.Append(Encoding.ASCII.GetString(state.buffer, 0, _  
                bytesRead))  
  
            '  Get the rest of the data.  
            client.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
                AddressOf ReceiveCallback, state)  
        Else  
            ' All the data has arrived; put it in response.  
            If state.sb.Length > 1 Then  
                response = state.sb.ToString()  
            End If  
            ' Signal that all bytes have been received.  
            receiveDone.Set()  
        End If  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'ReceiveCallback  
```  
  
```csharp  
private static void ReceiveCallback( IAsyncResult ar ) {  
    try {  
        // Retrieve the state object and the client socket
        // from the asynchronous state object.  
        StateObject state = (StateObject) ar.AsyncState;  
        Socket client = state.workSocket;  
        // Read data from the remote device.  
        int bytesRead = client.EndReceive(ar);  
        if (bytesRead > 0) {  
            // There might be more data, so store the data received so far.  
            state.sb.Append(Encoding.ASCII.GetString(state.buffer,0,bytesRead));  
                //  Get the rest of the data.  
            client.BeginReceive(state.buffer,0,StateObject.BufferSize,0,  
                new AsyncCallback(ReceiveCallback), state);  
        } else {  
            // All the data has arrived; put it in response.  
            if (state.sb.Length > 1) {  
                response = state.sb.ToString();  
            }  
            // Signal that all bytes have been received.  
            receiveDone.Set();  
        }  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="0463a-140">请参阅</span><span class="sxs-lookup"><span data-stu-id="0463a-140">See also</span></span>

- [<span data-ttu-id="0463a-141">使用同步客户端套接字</span><span class="sxs-lookup"><span data-stu-id="0463a-141">Using a Synchronous Client Socket</span></span>](using-a-synchronous-client-socket.md)
- [<span data-ttu-id="0463a-142">使用套接字侦听</span><span class="sxs-lookup"><span data-stu-id="0463a-142">Listening with Sockets</span></span>](listening-with-sockets.md)
- [<span data-ttu-id="0463a-143">异步客户端套接字示例</span><span class="sxs-lookup"><span data-stu-id="0463a-143">Asynchronous Client Socket Example</span></span>](asynchronous-client-socket-example.md)

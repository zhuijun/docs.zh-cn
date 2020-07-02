---
title: 处理错误
description: 了解由 WebRequest 和 WebResponse 引发的系统和特定于 Web 的异常。 使用 Status 属性来了解和解决问题。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Internet, WebRequest and WebResponse classes exceptions
- Status property
- WebExceptions class, about WebExceptions class
- Timeout enumeration member
- ConnectFailure enumeration member
- TrustFailure enumeration member
- WebRequest class, exceptions
- requesting data from Internet, error handling
- Success enumeration member
- receiving data, errors
- ProtocolError enumeration member
- downloading Internet resources, error handling
- WebResponse class, exceptions
- SendFailure enumeration member
- errors [.NET Framework], WebRequest and WebResponse classes exceptions
- sending data, errors
- response to Internet request, error handling
- NameResolutionFailure enumeration member
- KeepAliveFailure enumeration member
- network resources, WebRequest and WebResponse classes exceptions
- RequestCanceled enumeration member
- ReceiveFailure enumeration member
- ServerProtocolViolation enumeration member
- ConnectionClosed enumeration member
- SecureChannelFailure enumeration member
ms.assetid: 657141cd-5cf5-4fdb-a4b2-4c040eba84b5
ms.openlocfilehash: 786b2bd8bc4d1b394bcfe920053b2f4f55d1cdea
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502569"
---
# <a name="handling-errors"></a><span data-ttu-id="68dfc-104">处理错误</span><span class="sxs-lookup"><span data-stu-id="68dfc-104">Handling Errors</span></span>

<span data-ttu-id="68dfc-105"><xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse> 类都会引发系统异常（如 <xref:System.ArgumentException>）和特定于 Web 的异常（为 <xref:System.Net.WebRequest.GetResponse%2A> 方法所引发的 <xref:System.Net.WebException>）。</span><span class="sxs-lookup"><span data-stu-id="68dfc-105">The <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes throw both system exceptions (such as <xref:System.ArgumentException>) and Web-specific exceptions (which are <xref:System.Net.WebException> thrown by the <xref:System.Net.WebRequest.GetResponse%2A> method).</span></span>  
  
<span data-ttu-id="68dfc-106">每个 WebException 包括一个 <xref:System.Net.WebException.Status%2A> 属性，它包含来自 <xref:System.Net.WebExceptionStatus> 枚举的一个值。</span><span class="sxs-lookup"><span data-stu-id="68dfc-106">Each **WebException** includes a <xref:System.Net.WebException.Status%2A> property that contains a value from the <xref:System.Net.WebExceptionStatus> enumeration.</span></span> <span data-ttu-id="68dfc-107">可以检查“状态”属性以确定发生的错误并采取适当的步骤解决该错误。</span><span class="sxs-lookup"><span data-stu-id="68dfc-107">You can examine the **Status** property to determine the error that occurred and take the proper steps to resolve the error.</span></span>  
  
<span data-ttu-id="68dfc-108">下表描述了“状态”属性可能的值。</span><span class="sxs-lookup"><span data-stu-id="68dfc-108">The following table describes the possible values for the **Status** property.</span></span>  
  
|<span data-ttu-id="68dfc-109">状态</span><span class="sxs-lookup"><span data-stu-id="68dfc-109">Status</span></span>|<span data-ttu-id="68dfc-110">描述</span><span class="sxs-lookup"><span data-stu-id="68dfc-110">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="68dfc-111">ConnectFailure</span><span class="sxs-lookup"><span data-stu-id="68dfc-111">ConnectFailure</span></span>|<span data-ttu-id="68dfc-112">无法在传输级别联系远程服务。</span><span class="sxs-lookup"><span data-stu-id="68dfc-112">The remote service could not be contacted at the transport level.</span></span>|  
|<span data-ttu-id="68dfc-113">ConnectionClosed</span><span class="sxs-lookup"><span data-stu-id="68dfc-113">ConnectionClosed</span></span>|<span data-ttu-id="68dfc-114">连接被提前关闭。</span><span class="sxs-lookup"><span data-stu-id="68dfc-114">The connection was closed prematurely.</span></span>|  
|<span data-ttu-id="68dfc-115">KeepAliveFailure</span><span class="sxs-lookup"><span data-stu-id="68dfc-115">KeepAliveFailure</span></span>|<span data-ttu-id="68dfc-116">服务器已关闭与“保持的连接”标头设置建立的连接。</span><span class="sxs-lookup"><span data-stu-id="68dfc-116">The server closed a connection made with the Keep-alive header set.</span></span>|  
|<span data-ttu-id="68dfc-117">NameResolutionFailure</span><span class="sxs-lookup"><span data-stu-id="68dfc-117">NameResolutionFailure</span></span>|<span data-ttu-id="68dfc-118">名称服务无法解析主机名。</span><span class="sxs-lookup"><span data-stu-id="68dfc-118">The name service could not resolve the host name.</span></span>|  
|<span data-ttu-id="68dfc-119">ProtocolError</span><span class="sxs-lookup"><span data-stu-id="68dfc-119">ProtocolError</span></span>|<span data-ttu-id="68dfc-120">从服务器接收的响应是完整的，但指示在协议级别出现错误。</span><span class="sxs-lookup"><span data-stu-id="68dfc-120">The response received from the server was complete but indicated an error at the protocol level.</span></span>|  
|<span data-ttu-id="68dfc-121">ReceiveFailure</span><span class="sxs-lookup"><span data-stu-id="68dfc-121">ReceiveFailure</span></span>|<span data-ttu-id="68dfc-122">无法从远程服务器接收完整的响应。</span><span class="sxs-lookup"><span data-stu-id="68dfc-122">A complete response was not received from the remote server.</span></span>|  
|<span data-ttu-id="68dfc-123">RequestCanceled</span><span class="sxs-lookup"><span data-stu-id="68dfc-123">RequestCanceled</span></span>|<span data-ttu-id="68dfc-124">请求已被取消。</span><span class="sxs-lookup"><span data-stu-id="68dfc-124">The request was canceled.</span></span>|  
|<span data-ttu-id="68dfc-125">SecureChannelFailure</span><span class="sxs-lookup"><span data-stu-id="68dfc-125">SecureChannelFailure</span></span>|<span data-ttu-id="68dfc-126">安全通道链接中出现错误。</span><span class="sxs-lookup"><span data-stu-id="68dfc-126">An error occurred in a secure channel link.</span></span>|  
|<span data-ttu-id="68dfc-127">SendFailure</span><span class="sxs-lookup"><span data-stu-id="68dfc-127">SendFailure</span></span>|<span data-ttu-id="68dfc-128">无法向远程服务器发送完整的请求。</span><span class="sxs-lookup"><span data-stu-id="68dfc-128">A complete request could not be sent to the remote server.</span></span>|  
|<span data-ttu-id="68dfc-129">ServerProtocolViolation</span><span class="sxs-lookup"><span data-stu-id="68dfc-129">ServerProtocolViolation</span></span>|<span data-ttu-id="68dfc-130">服务器响应不是有效的 HTTP 响应。</span><span class="sxs-lookup"><span data-stu-id="68dfc-130">The server response was not a valid HTTP response.</span></span>|  
|<span data-ttu-id="68dfc-131">成功</span><span class="sxs-lookup"><span data-stu-id="68dfc-131">Success</span></span>|<span data-ttu-id="68dfc-132">未遇到任何错误。</span><span class="sxs-lookup"><span data-stu-id="68dfc-132">No error was encountered.</span></span>|  
|<span data-ttu-id="68dfc-133">超时</span><span class="sxs-lookup"><span data-stu-id="68dfc-133">Timeout</span></span>|<span data-ttu-id="68dfc-134">在请求的超时设置内未接收到任何响应。</span><span class="sxs-lookup"><span data-stu-id="68dfc-134">No response was received within the time-out set for the request.</span></span>|  
|<span data-ttu-id="68dfc-135">TrustFailure</span><span class="sxs-lookup"><span data-stu-id="68dfc-135">TrustFailure</span></span>|<span data-ttu-id="68dfc-136">无法验证服务器证书。</span><span class="sxs-lookup"><span data-stu-id="68dfc-136">A server certificate could not be validated.</span></span>|  
|<span data-ttu-id="68dfc-137">MessageLengthLimitExceeded</span><span class="sxs-lookup"><span data-stu-id="68dfc-137">MessageLengthLimitExceeded</span></span>|<span data-ttu-id="68dfc-138">从服务器发送请求或接收响应时，接收到的消息超出指定限制。</span><span class="sxs-lookup"><span data-stu-id="68dfc-138">A message was received that exceeded the specified limit when sending a request or receiving a response from the server.</span></span>|  
|<span data-ttu-id="68dfc-139">挂起</span><span class="sxs-lookup"><span data-stu-id="68dfc-139">Pending</span></span>|<span data-ttu-id="68dfc-140">内部异步请求处于挂起状态。</span><span class="sxs-lookup"><span data-stu-id="68dfc-140">An internal asynchronous request is pending.</span></span>|  
|<span data-ttu-id="68dfc-141">PipelineFailure</span><span class="sxs-lookup"><span data-stu-id="68dfc-141">PipelineFailure</span></span>|<span data-ttu-id="68dfc-142">此值支持 .NET Framework 基础结构，不能在代码中直接使用。</span><span class="sxs-lookup"><span data-stu-id="68dfc-142">This value supports the .NET Framework infrastructure and is not intended to be used directly in your code.</span></span>|  
|<span data-ttu-id="68dfc-143">ProxyNameResolutionFailure</span><span class="sxs-lookup"><span data-stu-id="68dfc-143">ProxyNameResolutionFailure</span></span>|<span data-ttu-id="68dfc-144">名称解析程序服务无法解析代理主机名。</span><span class="sxs-lookup"><span data-stu-id="68dfc-144">The name resolver service could not resolve the proxy host name.</span></span>|  
|<span data-ttu-id="68dfc-145">UnknownError</span><span class="sxs-lookup"><span data-stu-id="68dfc-145">UnknownError</span></span>|<span data-ttu-id="68dfc-146">出现未知类型的异常。</span><span class="sxs-lookup"><span data-stu-id="68dfc-146">An exception of unknown type has occurred.</span></span>|  
  
<span data-ttu-id="68dfc-147">当“状态”属性为“WebExceptionStatus.ProtocolError”时，可以使用包含来自服务器的响应的 WebResponse  。</span><span class="sxs-lookup"><span data-stu-id="68dfc-147">When the **Status** property is **WebExceptionStatus.ProtocolError**, a **WebResponse** that contains the response from the server is available.</span></span> <span data-ttu-id="68dfc-148">可以检查此响应以确定协议错误的实际来源。</span><span class="sxs-lookup"><span data-stu-id="68dfc-148">You can examine this response to determine the actual source of the protocol error.</span></span>  
  
<span data-ttu-id="68dfc-149">下面的示例演示如何捕获 WebException。</span><span class="sxs-lookup"><span data-stu-id="68dfc-149">The following example shows how to catch a **WebException**.</span></span>  
  
```csharp  
try
{  
    // Create a request instance.  
    WebRequest myRequest =
    WebRequest.Create("http://www.contoso.com");  
    // Get the response.  
    WebResponse myResponse = myRequest.GetResponse();  
    //Get a readable stream from the server.
    Stream sr = myResponse.GetResponseStream();  
  
    //Read from the stream and write any data to the console.  
    bytesread = sr.Read( myBuffer, 0, length);  
    while( bytesread > 0 )
    {  
        for (int i=0; i<bytesread; i++) {  
            Console.Write( "{0}", myBuffer[i]);  
        }  
        Console.WriteLine();  
        bytesread = sr.Read( myBuffer, 0, length);  
    }  
    sr.Close();  
    myResponse.Close();  
}  
catch (WebException webExcp)
{  
    // If you reach this point, an exception has been caught.  
    Console.WriteLine("A WebException has been caught.");  
    // Write out the WebException message.  
    Console.WriteLine(webExcp.ToString());  
    // Get the WebException status code.  
    WebExceptionStatus status =  webExcp.Status;  
    // If status is WebExceptionStatus.ProtocolError,
    //   there has been a protocol error and a WebResponse
    //   should exist. Display the protocol error.  
    if (status == WebExceptionStatus.ProtocolError) {  
        Console.Write("The server returned protocol error ");  
        // Get HttpWebResponse so that you can check the HTTP status code.  
        HttpWebResponse httpResponse = (HttpWebResponse)webExcp.Response;  
        Console.WriteLine((int)httpResponse.StatusCode + " - "  
           + httpResponse.StatusCode);  
    }  
}  
catch (Exception e)
{  
    // Code to catch other exceptions goes here.  
}  
```  
  
```vb  
Try  
    ' Create a request instance.  
    Dim myRequest As WebRequest = WebRequest.Create("http://www.contoso.com")  
    ' Get the response.  
    Dim myResponse As WebResponse = myRequest.GetResponse()  
    'Get a readable stream from the server.
    Dim sr As Stream = myResponse.GetResponseStream()  
  
    Dim i As Integer
    'Read from the stream and write any data to the console.  
    bytesread = sr.Read(myBuffer, 0, length)  
    While bytesread > 0  
        For i = 0 To bytesread - 1  
            Console.Write("{0}", myBuffer(i))  
        Next i  
        Console.WriteLine()  
        bytesread = sr.Read(myBuffer, 0, length)  
    End While  
    sr.Close()  
    myResponse.Close()  
Catch webExcp As WebException  
    ' If you reach this point, an exception has been caught.  
    Console.WriteLine("A WebException has been caught.")  
    ' Write out the WebException message.  
    Console.WriteLine(webExcp.ToString())  
    ' Get the WebException status code.  
    Dim status As WebExceptionStatus = webExcp.Status  
    ' If status is WebExceptionStatus.ProtocolError,
    '   there has been a protocol error and a WebResponse
    '   should exist. Display the protocol error.  
    If status = WebExceptionStatus.ProtocolError Then  
        Console.Write("The server returned protocol error ")  
        ' Get HttpWebResponse so that you can check the HTTP status code.  
        Dim httpResponse As HttpWebResponse = _  
           CType(webExcp.Response, HttpWebResponse)  
        Console.WriteLine(CInt(httpResponse.StatusCode).ToString() & _  
           " - " & httpResponse.StatusCode.ToString())  
    End If  
Catch e As Exception  
    ' Code to catch other exceptions goes here.  
End Try  
```  
  
<span data-ttu-id="68dfc-150">当 Windows 套接字上出现错误时，使用 <xref:System.Net.Sockets.Socket> 类的应用程序将引发 <xref:System.Net.Sockets.SocketException>。</span><span class="sxs-lookup"><span data-stu-id="68dfc-150">Applications that use the <xref:System.Net.Sockets.Socket> class throw <xref:System.Net.Sockets.SocketException> when errors occur on the Windows socket.</span></span> <span data-ttu-id="68dfc-151"><xref:System.Net.Sockets.TcpClient>、<xref:System.Net.Sockets.TcpListener> 和 <xref:System.Net.Sockets.UdpClient> 类在套接字类的顶层生成，并且也会引发 SocketExceptions 。</span><span class="sxs-lookup"><span data-stu-id="68dfc-151">The <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes are built on top of the **Socket** class and throw **SocketExceptions** as well.</span></span>  
  
<span data-ttu-id="68dfc-152">引发 SocketException 时，SocketException 类将 <xref:System.Net.Sockets.SocketException.ErrorCode%2A> 属性设置为最后一次发生的操作系统套接字错误 。</span><span class="sxs-lookup"><span data-stu-id="68dfc-152">When a **SocketException** is thrown, the **SocketException** class sets the <xref:System.Net.Sockets.SocketException.ErrorCode%2A> property to the last operating system socket error that occurred.</span></span> <span data-ttu-id="68dfc-153">有关套接字错误代码的详细信息，请参阅 MSDN 中的 Winsock 2.0 API 错误代码文档。</span><span class="sxs-lookup"><span data-stu-id="68dfc-153">For more information about socket error codes, see the Winsock 2.0 API error code documentation in MSDN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68dfc-154">请参阅</span><span class="sxs-lookup"><span data-stu-id="68dfc-154">See also</span></span>

- [<span data-ttu-id="68dfc-155">在 .NET 中处理和引发异常</span><span class="sxs-lookup"><span data-stu-id="68dfc-155">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
- [<span data-ttu-id="68dfc-156">请求数据</span><span class="sxs-lookup"><span data-stu-id="68dfc-156">Requesting Data</span></span>](requesting-data.md)

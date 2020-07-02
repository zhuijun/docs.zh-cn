---
title: 在网络上使用流
description: .NET Framework 将网络资源表示为流。 NetworkStream 类实现与网络资源一起使用的 Stream 类。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- requesting data from Internet, streams
- Networking
- response to Internet request, streams
- network resources, stream capabilities
- receiving data, stream capabilities
- Network Resources
- sending data, stream capabilities
- downloading Internet resources, streams
- streams, capabilities
- Internet, streams
- streams
ms.assetid: 02b05fba-7235-45ce-94e5-060436ee0875
ms.openlocfilehash: f8d35b43c9b46a77bfd0c78f7d0118093b6fe824
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501971"
---
# <a name="using-streams-on-the-network"></a><span data-ttu-id="f15d5-104">在网络上使用流</span><span class="sxs-lookup"><span data-stu-id="f15d5-104">Using Streams on the Network</span></span>
<span data-ttu-id="f15d5-105">网络资源在 .NET Framework 中表示为流。</span><span class="sxs-lookup"><span data-stu-id="f15d5-105">Network resources are represented in the .NET Framework as streams.</span></span> <span data-ttu-id="f15d5-106">通过对流进行一般处理，.NET Framework 提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="f15d5-106">By treating streams generically, the .NET Framework offers the following capabilities:</span></span>  
  
- <span data-ttu-id="f15d5-107">发送和接收 Web 数据的通用方法。</span><span class="sxs-lookup"><span data-stu-id="f15d5-107">A common way to send and receive Web data.</span></span> <span data-ttu-id="f15d5-108">无论文件的实际内容是什么（HTML、XML 或任何其他内容），应用程序都将使用 <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> 和 <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> 发送和接收数据。</span><span class="sxs-lookup"><span data-stu-id="f15d5-108">Whatever the actual contents of the file — HTML, XML, or anything else — your application will use <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> and <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> to send and receive data.</span></span>  
  
- <span data-ttu-id="f15d5-109">跨 .NET Framework 的流兼容性。</span><span class="sxs-lookup"><span data-stu-id="f15d5-109">Compatibility with streams across the .NET Framework.</span></span> <span data-ttu-id="f15d5-110">流在 .NET Framework 中遍及使用，其具有丰富的基础结构来处理流。</span><span class="sxs-lookup"><span data-stu-id="f15d5-110">Streams are used throughout the .NET Framework, which has a rich infrastructure for handling them.</span></span> <span data-ttu-id="f15d5-111">例如，通过仅更改初始化流的几行代码，便可修改从 <xref:System.IO.FileStream> 中读取 XML 数据的应用程序而使其改为从 <xref:System.Net.Sockets.NetworkStream> 中读取数据。</span><span class="sxs-lookup"><span data-stu-id="f15d5-111">For example, you can modify an application that reads XML data from a <xref:System.IO.FileStream> to read data from a <xref:System.Net.Sockets.NetworkStream> instead by changing only the few lines of code that initialize the stream.</span></span> <span data-ttu-id="f15d5-112">NetworkStream 类和其他流之间的主要区别在于：NetworkStream 是不可查找的，<xref:System.Net.Sockets.NetworkStream.CanSeek%2A> 属性始终返回 false，且 <xref:System.Net.Sockets.NetworkStream.Seek%2A> 和 <xref:System.Net.Sockets.NetworkStream.Position%2A> 方法将引发 <xref:System.NotSupportedException>。  </span><span class="sxs-lookup"><span data-stu-id="f15d5-112">The major differences between the **NetworkStream** class and other streams are that **NetworkStream** is not seekable, the <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> property always returns **false**, and the <xref:System.Net.Sockets.NetworkStream.Seek%2A> and <xref:System.Net.Sockets.NetworkStream.Position%2A> methods throw a <xref:System.NotSupportedException>.</span></span>  
  
- <span data-ttu-id="f15d5-113">在数据到达时处理数据。</span><span class="sxs-lookup"><span data-stu-id="f15d5-113">Processing of data as it arrives.</span></span> <span data-ttu-id="f15d5-114">流在数据从网络到达目标时便提供对数据的访问，而不会强制应用程序等待整个数据集下载完成。</span><span class="sxs-lookup"><span data-stu-id="f15d5-114">Streams provide access to data as it arrives from the network, rather than forcing your application to wait for an entire data set to be downloaded.</span></span>  
  
 <span data-ttu-id="f15d5-115"><xref:System.Net.Sockets> 命名空间包含一个 NetworkStream 类，该类实现专用于网络资源的 <xref:System.IO.Stream> 类。</span><span class="sxs-lookup"><span data-stu-id="f15d5-115">The <xref:System.Net.Sockets> namespace contains a **NetworkStream** class that implements the <xref:System.IO.Stream> class specifically for use with network resources.</span></span> <span data-ttu-id="f15d5-116"><xref:System.Net.Sockets> 命名空间中的类使用 NetworkStream 类表示流。</span><span class="sxs-lookup"><span data-stu-id="f15d5-116">Classes in the <xref:System.Net.Sockets> namespace use the **NetworkStream** class to represent streams.</span></span>  
  
 <span data-ttu-id="f15d5-117">若要使用返回的流向网络发送数据，请对 <xref:System.Net.WebRequest> 调用 <xref:System.Net.WebRequest.GetRequestStream%2A>。</span><span class="sxs-lookup"><span data-stu-id="f15d5-117">To send data to the network using the returned stream, call <xref:System.Net.WebRequest.GetRequestStream%2A> on your <xref:System.Net.WebRequest>.</span></span> <span data-ttu-id="f15d5-118">WebRequest 会将请求标头发送到服务器；然后你可以通过对返回的流调用 <xref:System.IO.Stream.BeginWrite%2A>、<xref:System.IO.Stream.EndWrite%2A> 或 <xref:System.IO.Stream.Write%2A> 方法，将数据发送到网络资源。</span><span class="sxs-lookup"><span data-stu-id="f15d5-118">The **WebRequest** will send request headers to the server; then you can send data to the network resource by calling the <xref:System.IO.Stream.BeginWrite%2A>, <xref:System.IO.Stream.EndWrite%2A>, or <xref:System.IO.Stream.Write%2A> method on the returned stream.</span></span> <span data-ttu-id="f15d5-119">某些协议（如 HTTP）可能要求在发送数据之前设置协议特定的属性。</span><span class="sxs-lookup"><span data-stu-id="f15d5-119">Some protocols, such as HTTP, may require you to set protocol-specific properties before sending data.</span></span> <span data-ttu-id="f15d5-120">下面的代码示例演示如何设置 HTTP 特定的属性以发送数据。</span><span class="sxs-lookup"><span data-stu-id="f15d5-120">The following code example shows how to set HTTP-specific properties for sending data.</span></span> <span data-ttu-id="f15d5-121">该示例假定变量 `sendData` 包含要发送的数据，变量 `sendLength` 为要发送的数据的字节数。</span><span class="sxs-lookup"><span data-stu-id="f15d5-121">It assumes that the variable `sendData` contains the data to send and that the variable `sendLength` is the number of bytes of data to send.</span></span>  
  
```csharp  
HttpWebRequest request =
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
request.Method = "POST";  
request.ContentLength = sendLength;  
try  
{  
   Stream sendStream = request.GetRequestStream();  
   sendStream.Write(sendData,0,sendLength);  
   sendStream.Close();  
}  
catch  
{  
   // Handle errors . . .  
}  
```  
  
```vb  
Dim request As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
request.Method = "POST"  
request.ContentLength = sendLength  
Try  
   Dim sendStream As Stream = request.GetRequestStream()  
   sendStream.Write(sendData, 0, sendLength)  
   sendStream.Close()  
Catch  
   ' Handle errors . . .  
End Try  
```  
  
 <span data-ttu-id="f15d5-122">若要从网络接收数据，请对 <xref:System.Net.WebResponse> 调用 <xref:System.Net.WebResponse.GetResponseStream%2A>。</span><span class="sxs-lookup"><span data-stu-id="f15d5-122">To receive data from the network, call <xref:System.Net.WebResponse.GetResponseStream%2A> on your <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="f15d5-123">然后可以通过对返回的流调用 <xref:System.IO.Stream.BeginRead%2A>、<xref:System.IO.Stream.EndRead%2A> 或 <xref:System.IO.Stream.Read%2A> 方法，从网络资源读取数据。</span><span class="sxs-lookup"><span data-stu-id="f15d5-123">You can then read data from the network resource by calling the <xref:System.IO.Stream.BeginRead%2A>, <xref:System.IO.Stream.EndRead%2A>, or <xref:System.IO.Stream.Read%2A> method on the returned stream.</span></span>  
  
 <span data-ttu-id="f15d5-124">使用来自网络资源的流时，请留心以下几点：</span><span class="sxs-lookup"><span data-stu-id="f15d5-124">When using streams from network resources, keep in mind the following points:</span></span>  
  
- <span data-ttu-id="f15d5-125">CanSeek 属性将始终返回 false，因为 NetworkStream 类无法更改流中的位置。  </span><span class="sxs-lookup"><span data-stu-id="f15d5-125">The **CanSeek** property always returns **false** since the **NetworkStream** class cannot change position in the stream.</span></span> <span data-ttu-id="f15d5-126">Seek 和 Position 方法引发 NotSupportedException。  </span><span class="sxs-lookup"><span data-stu-id="f15d5-126">The **Seek** and **Position** methods throw a **NotSupportedException**.</span></span>  
  
- <span data-ttu-id="f15d5-127">当使用 WebRequest 和 WebResponse 时，通过调用 GetResponseStream 创建的流实例是只读的，而通过调用 GetRequestStream 创建的流实例是只写的。   </span><span class="sxs-lookup"><span data-stu-id="f15d5-127">When you use **WebRequest** and **WebResponse**, stream instances created by calling **GetResponseStream** are read-only and stream instances created by calling **GetRequestStream** are write-only.</span></span>  
  
- <span data-ttu-id="f15d5-128">使用 <xref:System.IO.StreamReader> 类可使编码更容易。</span><span class="sxs-lookup"><span data-stu-id="f15d5-128">Use the <xref:System.IO.StreamReader> class to make encoding easier.</span></span> <span data-ttu-id="f15d5-129">下面的代码示例使用 StreamReader 从 WebResponse 读取用 ASCII 编码的流（此示例不显示创建请求的过程）。 </span><span class="sxs-lookup"><span data-stu-id="f15d5-129">The following code example uses a **StreamReader** to read an ASCII-encoded stream from a **WebResponse** (the example does not show creating the request).</span></span>  
  
- <span data-ttu-id="f15d5-130">如果网络资源不可用，则对 GetResponse 的调用可能受到阻止。</span><span class="sxs-lookup"><span data-stu-id="f15d5-130">The call to **GetResponse** can block if network resources are not available.</span></span> <span data-ttu-id="f15d5-131">应考虑利用 <xref:System.Net.WebRequest.BeginGetResponse%2A> 和 <xref:System.Net.WebRequest.EndGetResponse%2A> 方法使用异步请求。</span><span class="sxs-lookup"><span data-stu-id="f15d5-131">You should consider using an asynchronous request with the <xref:System.Net.WebRequest.BeginGetResponse%2A> and <xref:System.Net.WebRequest.EndGetResponse%2A> methods.</span></span>  
  
- <span data-ttu-id="f15d5-132">在创建与服务器的连接时，对 GetRequestStream 的调用可能受到阻止。</span><span class="sxs-lookup"><span data-stu-id="f15d5-132">The call to **GetRequestStream** can block while the connection to the server is created.</span></span> <span data-ttu-id="f15d5-133">应考虑利用 <xref:System.Net.WebRequest.BeginGetRequestStream%2A> 和 <xref:System.Net.WebRequest.EndGetRequestStream%2A> 方法对流使用异步请求。</span><span class="sxs-lookup"><span data-stu-id="f15d5-133">You should consider using an asynchronous request for the stream with the <xref:System.Net.WebRequest.BeginGetRequestStream%2A> and <xref:System.Net.WebRequest.EndGetRequestStream%2A> methods.</span></span>  
  
```csharp  
// Create a response object.  
WebResponse response = request.GetResponse();  
// Get a readable stream from the server.  
StreamReader sr =
   new StreamReader(response.GetResponseStream(), Encoding.ASCII);  
// Use the stream. Remember when you are through with the stream to close it.  
sr.Close();  
```  
  
```vb  
' Create a response object.  
Dim response As WebResponse = request.GetResponse()  
' Get a readable stream from the server.  
Dim sr As _
   New StreamReader(response.GetResponseStream(), Encoding.ASCII)  
' Use the stream. Remember when you are through with the stream to close it.  
sr.Close()  
```  
  
## <a name="see-also"></a><span data-ttu-id="f15d5-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="f15d5-134">See also</span></span>

- [<span data-ttu-id="f15d5-135">如何：使用 WebRequest 类请求数据</span><span class="sxs-lookup"><span data-stu-id="f15d5-135">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="f15d5-136">请求数据</span><span class="sxs-lookup"><span data-stu-id="f15d5-136">Requesting Data</span></span>](requesting-data.md)

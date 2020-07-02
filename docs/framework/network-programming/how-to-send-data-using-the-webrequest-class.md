---
title: 如何：使用 WebRequest 类发送数据
description: 了解如何使用 .NET Framework 中的 WebRequest 类将数据发送到服务器。 此过程通常用于将数据发布到网页。
ms.date: 03/25/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
ms.openlocfilehash: 4b353250fec778ee8b352f13de6d7faaf15c13ee
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502439"
---
# <a name="how-to-send-data-by-using-the-webrequest-class"></a><span data-ttu-id="4032c-104">如何：使用 WebRequest 类发送数据</span><span class="sxs-lookup"><span data-stu-id="4032c-104">How to: Send data by using the WebRequest class</span></span>

<span data-ttu-id="4032c-105">以下过程描述将数据发送到服务器的步骤。</span><span class="sxs-lookup"><span data-stu-id="4032c-105">The following procedure describes the steps to send data to a server.</span></span> <span data-ttu-id="4032c-106">此过程通常用于将数据发布到 Web 页。</span><span class="sxs-lookup"><span data-stu-id="4032c-106">This procedure is commonly used to post data to a Web page.</span></span>

## <a name="to-send-data-to-a-host-server"></a><span data-ttu-id="4032c-107">将数据发送到主机服务器</span><span class="sxs-lookup"><span data-stu-id="4032c-107">To send data to a host server</span></span>

1. <span data-ttu-id="4032c-108">通过使用接受数据的资源（例如脚本或 ASP.NET 页面）的 URI 调用 <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> 来创建 <xref:System.Net.WebRequest> 实例。</span><span class="sxs-lookup"><span data-stu-id="4032c-108">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource, such as a script or ASP.NET page, that accepts data.</span></span> <span data-ttu-id="4032c-109">例如：</span><span class="sxs-lookup"><span data-stu-id="4032c-109">For example:</span></span>

    ```csharp
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")
    ```

    > [!NOTE]
    > <span data-ttu-id="4032c-110">.NET Framework 为以“http:”、“https:”、“ftp:”和“file:”开头的 URI 提供派生自 <xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse> 类的特定于协议的类   。</span><span class="sxs-lookup"><span data-stu-id="4032c-110">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>

    <span data-ttu-id="4032c-111">如果需要设置或读取特定于协议的属性，必须将 <xref:System.Net.WebRequest> 或 <xref:System.Net.WebResponse> 转换为特定于协议的对象类型。</span><span class="sxs-lookup"><span data-stu-id="4032c-111">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="4032c-112">有关详细信息，请参阅[对可插入协议进行编程](programming-pluggable-protocols.md)。</span><span class="sxs-lookup"><span data-stu-id="4032c-112">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span>

2. <span data-ttu-id="4032c-113">设置 `WebRequest` 对象中任何所需的属性值。</span><span class="sxs-lookup"><span data-stu-id="4032c-113">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="4032c-114">例如，若要启用身份验证，则将 <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> 属性设置为 <xref:System.Net.NetworkCredential> 类的实例：</span><span class="sxs-lookup"><span data-stu-id="4032c-114">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. <span data-ttu-id="4032c-115">指定允许使用请求发送数据的协议方法，如 HTTP `POST` 方法：</span><span class="sxs-lookup"><span data-stu-id="4032c-115">Specify a protocol method that permits data to be sent with a request, such as the HTTP `POST` method:</span></span>

    ```csharp
    request.Method = "POST";
    ```

    ```vb
    request.Method = "POST"
    ```

4. <span data-ttu-id="4032c-116">将 <xref:System.Web.HttpRequest.ContentLength> 属性设置为请求中包含的字节数。</span><span class="sxs-lookup"><span data-stu-id="4032c-116">Set the <xref:System.Web.HttpRequest.ContentLength> property to the number of bytes you're including with your request.</span></span> <span data-ttu-id="4032c-117">例如：</span><span class="sxs-lookup"><span data-stu-id="4032c-117">For example:</span></span>

    ```csharp
    request.ContentLength = byteArray.Length;
    ```

    ```vb
    request.ContentLength = byteArray.Length
    ```

5. <span data-ttu-id="4032c-118">将 <xref:System.Web.HttpRequest.ContentType> 属性设置为适当的值。</span><span class="sxs-lookup"><span data-stu-id="4032c-118">Set the <xref:System.Web.HttpRequest.ContentType> property to an appropriate value.</span></span> <span data-ttu-id="4032c-119">例如：</span><span class="sxs-lookup"><span data-stu-id="4032c-119">For example:</span></span>

    ```csharp
    request.ContentType = "application/x-www-form-urlencoded";
    ```

    ```vb
    request.ContentType = "application/x-www-form-urlencoded"
    ```

6. <span data-ttu-id="4032c-120">通过调用 <xref:System.Net.WebRequest.GetRequestStream%2A> 方法获取包含请求数据的流。</span><span class="sxs-lookup"><span data-stu-id="4032c-120">Get the stream that holds request data by calling the <xref:System.Net.WebRequest.GetRequestStream%2A> method.</span></span> <span data-ttu-id="4032c-121">例如：</span><span class="sxs-lookup"><span data-stu-id="4032c-121">For example:</span></span>

    ```csharp
    Stream dataStream = request.GetRequestStream();
    ```

    ```vb
    Dim dataStream As Stream = request.GetRequestStream()
    ```

7. <span data-ttu-id="4032c-122">将数据写入到 `GetRequestStream` 方法返回的 <xref:System.IO.Stream> 对象中。</span><span class="sxs-lookup"><span data-stu-id="4032c-122">Write the data to the <xref:System.IO.Stream> object returned by the `GetRequestStream` method.</span></span> <span data-ttu-id="4032c-123">例如：</span><span class="sxs-lookup"><span data-stu-id="4032c-123">For example:</span></span>

    ```csharp
    dataStream.Write(byteArray, 0, byteArray.Length);
    ```

    ```vb
    dataStream.Write(byteArray, 0, byteArray.Length)
    ```

8. <span data-ttu-id="4032c-124">通过调用 <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> 方法关闭请求流。</span><span class="sxs-lookup"><span data-stu-id="4032c-124">Close the request stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4032c-125">例如：</span><span class="sxs-lookup"><span data-stu-id="4032c-125">For example:</span></span>

    ```csharp
    dataStream.Close();
    ```

    ```vb
    dataStream.Close()
    ```

9. <span data-ttu-id="4032c-126">通过调用 <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> 向服务器发送请求。</span><span class="sxs-lookup"><span data-stu-id="4032c-126">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4032c-127">此方法返回包含服务器响应的对象。</span><span class="sxs-lookup"><span data-stu-id="4032c-127">This method returns an object containing the server's response.</span></span> <span data-ttu-id="4032c-128">返回的 `WebResponse` 对象的类型由请求的 URI 的方案决定。</span><span class="sxs-lookup"><span data-stu-id="4032c-128">The returned `WebResponse` object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="4032c-129">例如：</span><span class="sxs-lookup"><span data-stu-id="4032c-129">For example:</span></span>

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

10. <span data-ttu-id="4032c-130">可以访问 `WebResponse` 对象的属性或将其强制转换为特定于协议的实例，以读取特定于协议的属性。</span><span class="sxs-lookup"><span data-stu-id="4032c-130">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span>

    <span data-ttu-id="4032c-131">例如，要访问 <xref:System.Net.HttpWebResponse> 特定于 HTTP 的属性，请将 `WebResponse` 对象强制转换为 <xref:System.Net.HttpWebResponse> 引用。</span><span class="sxs-lookup"><span data-stu-id="4032c-131">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an <xref:System.Net.HttpWebResponse> reference.</span></span> <span data-ttu-id="4032c-132">以下代码示例演示如何显示与响应一起发送的特定于 HTTP 的 <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> 属性：</span><span class="sxs-lookup"><span data-stu-id="4032c-132">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>

    ```csharp
    Console.WriteLine(((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)
    ```

11. <span data-ttu-id="4032c-133">若要获取包含由服务器发送的响应数据的流，请调用 `WebResponse` 的 <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="4032c-133">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method of your `WebResponse` object.</span></span> <span data-ttu-id="4032c-134">例如：</span><span class="sxs-lookup"><span data-stu-id="4032c-134">For example:</span></span>

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

12. <span data-ttu-id="4032c-135">从响应对象读取数据后，可以使用 <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> 方法关闭它，也可以使用 <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> 方法关闭响应流。</span><span class="sxs-lookup"><span data-stu-id="4032c-135">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4032c-136">如果不关闭响应或流，则应用程序可能会耗尽服务器连接，并且无法处理其他请求。</span><span class="sxs-lookup"><span data-stu-id="4032c-136">If you don't close either the response or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="4032c-137">因为 `WebResponse.Close` 方法在其关闭响应时调用 `Stream.Close`，所以不必在响应和流对象上调用 `Close`，尽管这样做没有坏处。</span><span class="sxs-lookup"><span data-stu-id="4032c-137">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="4032c-138">例如：</span><span class="sxs-lookup"><span data-stu-id="4032c-138">For example:</span></span>

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a><span data-ttu-id="4032c-139">示例</span><span class="sxs-lookup"><span data-stu-id="4032c-139">Example</span></span>

<span data-ttu-id="4032c-140">以下示例演示如何将数据发送到 Web 服务器并读取其响应中的数据：</span><span class="sxs-lookup"><span data-stu-id="4032c-140">The following example shows how to send data to a web server and read the data in its response:</span></span>

[!code-csharp[SendDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/SendDataUsingWebRequest/cs/WebRequestPostExample.cs)]
[!code-vb[SendDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/SendDataUsingWebRequest/vb/WebRequestPostExample.vb)]

## <a name="see-also"></a><span data-ttu-id="4032c-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="4032c-141">See also</span></span>

- [<span data-ttu-id="4032c-142">创建 Internet 请求</span><span class="sxs-lookup"><span data-stu-id="4032c-142">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="4032c-143">在网络上使用流</span><span class="sxs-lookup"><span data-stu-id="4032c-143">Using streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="4032c-144">通过代理访问 Internet</span><span class="sxs-lookup"><span data-stu-id="4032c-144">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="4032c-145">请求数据</span><span class="sxs-lookup"><span data-stu-id="4032c-145">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="4032c-146">如何：使用 WebRequest 类请求数据</span><span class="sxs-lookup"><span data-stu-id="4032c-146">How to: Request data by using the WebRequest class</span></span>](how-to-request-data-using-the-webrequest-class.md)

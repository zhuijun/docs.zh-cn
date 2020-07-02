---
title: 创建 Internet 请求
description: 了解应用程序如何通过 WebRequest.Create 方法创建 WebRequest 实例，该方法可基于传递给它的 URI 方案创建派生类。
ms.date: 03/30/2017
helpviewer_keywords:
- WebRequest class, sending and receiving data
- Networking
- HttpWebResponse class, sending and receiving data
- requesting data from Internet, creating requests
- Network Resources
- Internet, requesting data
- data requests, creating requests
ms.assetid: faab683e-3f1e-4eee-b5e9-59f7245033d5
ms.openlocfilehash: 389c7bf5969eca4322aa680a6f28dec0b899709a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325642"
---
# <a name="create-internet-requests"></a><span data-ttu-id="197d8-103">创建 Internet 请求</span><span class="sxs-lookup"><span data-stu-id="197d8-103">Create internet requests</span></span>

<span data-ttu-id="197d8-104">应用程序通过 <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> 方法创建 <xref:System.Net.WebRequest> 实例。</span><span class="sxs-lookup"><span data-stu-id="197d8-104">Applications create <xref:System.Net.WebRequest> instances through the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="197d8-105"><xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> 是一种基于传递给它的 URI 方案创建从 <xref:System.Net.WebRequest> 派生的类的静态方法。</span><span class="sxs-lookup"><span data-stu-id="197d8-105"><xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> is a static method that creates a class derived from <xref:System.Net.WebRequest> based on the URI scheme passed to it.</span></span>  
  
## <a name="web-file-and-ftp-requests"></a><span data-ttu-id="197d8-106">Web、文件和 FTP 请求</span><span class="sxs-lookup"><span data-stu-id="197d8-106">Web, file, and FTP requests</span></span>

<span data-ttu-id="197d8-107">.NET Framework 提供从 `WebRequest` 派生的 <xref:System.Net.HttpWebRequest> 类，用以处理 HTTP 和 HTTPS 请求。</span><span class="sxs-lookup"><span data-stu-id="197d8-107">.NET Framework provides the <xref:System.Net.HttpWebRequest> class, which is derived from `WebRequest`, to handle HTTP and HTTPS requests.</span></span> <span data-ttu-id="197d8-108">在大多数情况下，`WebRequest` 类提供提出请求所需的所有属性；但是，如有必要，将 `WebRequest.Create` 方法创建的 `WebRequest` 对象转换为 `HttpWebRequest` 类型，即可访问该请求特定于 HTTP 的属性。</span><span class="sxs-lookup"><span data-stu-id="197d8-108">In most cases, the `WebRequest` class provides all the properties you need to make a request; however, if necessary, you can cast `WebRequest` objects created by the `WebRequest.Create` method to the `HttpWebRequest` type to access the HTTP-specific properties of the request.</span></span> <span data-ttu-id="197d8-109">同样，`HttpWebResponse` 对象可处理来自 HTTP 和 HTTPS 请求的响应。</span><span class="sxs-lookup"><span data-stu-id="197d8-109">Similarly, the `HttpWebResponse` object handles the responses from HTTP and HTTPS requests.</span></span> <span data-ttu-id="197d8-110">若要访问 `HttpWebResponse` 对象的特定于 HTTP 的属性，需要将 `WebResponse` 对象转换为 `HttpWebResponse` 类型。</span><span class="sxs-lookup"><span data-stu-id="197d8-110">To access the HTTP-specific properties of the `HttpWebResponse` object, you need to cast `WebResponse` objects to the `HttpWebResponse` type.</span></span>  
  
<span data-ttu-id="197d8-111">.NET Framework 还提供 <xref:System.Net.FileWebRequest> 和 <xref:System.Net.FileWebResponse> 类来处理使用“file:”URI 方案的资源请求。</span><span class="sxs-lookup"><span data-stu-id="197d8-111">.NET Framework also provides the <xref:System.Net.FileWebRequest> and <xref:System.Net.FileWebResponse> classes to handle requests for resources that use the "file:" URI scheme.</span></span> <span data-ttu-id="197d8-112">同样，提供的 <xref:System.Net.FtpWebRequest> 和 <xref:System.Net.FtpWebResponse> 类可处理使用“ftp:”方案的资源请求。</span><span class="sxs-lookup"><span data-stu-id="197d8-112">Likewise, the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes are provided to handle requests for resources that use the "ftp:" scheme.</span></span> <span data-ttu-id="197d8-113">如果请求的是使用上述任一方案的资源，则可使用 `WebRequest.Create` 方法获取用于发出请求的对象。</span><span class="sxs-lookup"><span data-stu-id="197d8-113">If your request is for a resource that uses any of these schemes, you can use the `WebRequest.Create` method to obtain an object with which to make your request.</span></span>  
  
<span data-ttu-id="197d8-114">要处理使用其他应用程序级协议的请求，请实现从 `WebRequest` 和 `WebResponse` 派生的协议特定的类。</span><span class="sxs-lookup"><span data-stu-id="197d8-114">To handle requests that use other application-level protocols, implement protocol-specific classes derived from `WebRequest` and `WebResponse`.</span></span> <span data-ttu-id="197d8-115">有关详细信息，请参阅[对可插入协议进行编程](programming-pluggable-protocols.md)。</span><span class="sxs-lookup"><span data-stu-id="197d8-115">For more information, see [Programming Pluggable Protocols](programming-pluggable-protocols.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="197d8-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="197d8-116">See also</span></span>

- [<span data-ttu-id="197d8-117">如何：使用 WebRequest 类请求数据</span><span class="sxs-lookup"><span data-stu-id="197d8-117">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="197d8-118">请求数据</span><span class="sxs-lookup"><span data-stu-id="197d8-118">Requesting Data</span></span>](requesting-data.md)

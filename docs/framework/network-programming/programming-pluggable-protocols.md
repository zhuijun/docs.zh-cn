---
title: 对可插入协议进行编程
description: 了解抽象的 WebRequest 和 WebResponse 类如何支持可插入协议，该协议允许应用程序在不指定协议的情况下获取数据。
ms.date: 03/30/2017
helpviewer_keywords:
- downloading Internet resources, pluggable protocols
- WebRequest class, pluggable protocols
- response to Internet request, pluggable protocols
- WebResponse class, pluggable protocols
- sending data, pluggable protocols
- network resources, pluggable protocols
- Internet, pluggable protocols
- programming pluggable protocols
- pluggable protocols, programming
- requesting data from Internet, pluggable protocols
- receiving data, pluggable protocols
- protocols, pluggable
ms.assetid: 66ef8456-7576-4e97-8956-959b216373db
ms.openlocfilehash: 510f616295abc13d93e0e0af5a37aca097d343e3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502192"
---
# <a name="programming-pluggable-protocols"></a><span data-ttu-id="81316-103">对可插入协议进行编程</span><span class="sxs-lookup"><span data-stu-id="81316-103">Programming Pluggable Protocols</span></span>
<span data-ttu-id="81316-104"><xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse> 抽象类为可插入协议提供了基础。</span><span class="sxs-lookup"><span data-stu-id="81316-104">The abstract <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide the base for pluggable protocols.</span></span> <span data-ttu-id="81316-105">通过从 <xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse> 派生协议特定的类，应用程序可以请求 Internet 资源中的数据并读取响应而无需指定所使用的协议。</span><span class="sxs-lookup"><span data-stu-id="81316-105">By deriving protocol-specific classes from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, an application can request data from an Internet resource and read the response without specifying the protocol being used.</span></span>  
  
 <span data-ttu-id="81316-106">在创建协议特定的 <xref:System.Net.WebRequest> 前，必须首先注册其 Create 方法。</span><span class="sxs-lookup"><span data-stu-id="81316-106">Before you can create a protocol-specific <xref:System.Net.WebRequest>, you must register its Create method.</span></span> <span data-ttu-id="81316-107">使用<xref:System.Net.WebRequest> 的静态 <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> 方法注册一个 <xref:System.Net.WebRequest> 子代来处理一组请求（包括对某一特定 Internet 方案的请求、对某个方案和服务器的请求或对某个方案、服务器和路径的请求）。</span><span class="sxs-lookup"><span data-stu-id="81316-107">Use the static <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> method of <xref:System.Net.WebRequest> to register a <xref:System.Net.WebRequest> descendant to handle a set of requests to a particular Internet scheme, to a scheme and server, or to a scheme, server, and path.</span></span>  
  
 <span data-ttu-id="81316-108">在大多数情况下，可以使用 <xref:System.Net.WebRequest> 类的方法和属性发送和接收数据。</span><span class="sxs-lookup"><span data-stu-id="81316-108">In most cases you will be able to send and receive data using the methods and properties of the <xref:System.Net.WebRequest> class.</span></span> <span data-ttu-id="81316-109">但是，如果需要访问协议特定的属性，则可以将 <xref:System.Net.WebRequest> 的类型转换成特定的派生类实例。</span><span class="sxs-lookup"><span data-stu-id="81316-109">However, if you need to access protocol-specific properties, you can typecast a <xref:System.Net.WebRequest> to a specific derived-class instance.</span></span>  
  
 <span data-ttu-id="81316-110">要利用可插入协议，<xref:System.Net.WebRequest> 子代必须提供一个默认的“请求并响应”事务，该事务不要求设置协议特定的属性。</span><span class="sxs-lookup"><span data-stu-id="81316-110">To take advantage of pluggable protocols, your <xref:System.Net.WebRequest> descendants must provide a default request-and-response transaction that does not require protocol-specific properties to be set.</span></span> <span data-ttu-id="81316-111">例如 <xref:System.Net.HttpWebRequest> 类实现了 HTTP 的 <xref:System.Net.WebRequest> 类，默认情况下提供 `GET` 请求并返回包含从 Web 服务器返回的流的 <xref:System.Net.HttpWebResponse>。</span><span class="sxs-lookup"><span data-stu-id="81316-111">For example, the <xref:System.Net.HttpWebRequest> class, which implements the <xref:System.Net.WebRequest> class for HTTP, provides a `GET` request by default and returns an <xref:System.Net.HttpWebResponse> that contains the stream returned from the Web server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81316-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="81316-112">See also</span></span>

- [<span data-ttu-id="81316-113">从 WebRequest 派生</span><span class="sxs-lookup"><span data-stu-id="81316-113">Deriving from WebRequest</span></span>](deriving-from-webrequest.md)
- [<span data-ttu-id="81316-114">从 WebResponse 派生</span><span class="sxs-lookup"><span data-stu-id="81316-114">Deriving from WebResponse</span></span>](deriving-from-webresponse.md)
- [<span data-ttu-id="81316-115">.NET Framework 中的网络编程</span><span class="sxs-lookup"><span data-stu-id="81316-115">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="81316-116">如何：转换 WebRequest 以访问协议特定属性</span><span class="sxs-lookup"><span data-stu-id="81316-116">How to: Typecast a WebRequest to Access Protocol Specific Properties</span></span>](how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)

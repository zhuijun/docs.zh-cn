---
title: 管理连接
description: 了解将 HTTP 用于数据资源的应用程序如何使用 .NET Framework ServicePoint 和 ServicePointManager 类管理连接。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Internet, connections
- HTTP, classes for connecting
- requesting data from Internet, connections
- sending data, connections
- receiving data, connections
- ServicePoint class, about ServicePoint class
- response to Internet request, connections
- connections [.NET Framework], classes
- network resources, connections
- downloading Internet resources, connections
- ServicePointManager class, about ServicePointManager class
ms.assetid: 9b3d3de7-189f-4f7d-81ae-9c29c441aaaa
ms.openlocfilehash: 124dff1b104e323b929d13f73cf17d740e747c32
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502283"
---
# <a name="managing-connections"></a><span data-ttu-id="892b6-103">管理连接</span><span class="sxs-lookup"><span data-stu-id="892b6-103">Managing Connections</span></span>
<span data-ttu-id="892b6-104">使用 HTTP 连接到数据资源的应用程序可使用 .NET Framework 的 <xref:System.Net.ServicePoint> 和 <xref:System.Net.ServicePointManager> 类管理与 Internet 的连接并有助于实现最优规模和最佳性能。</span><span class="sxs-lookup"><span data-stu-id="892b6-104">Applications that use HTTP to connect to data resources can use the .NET Framework's <xref:System.Net.ServicePoint> and <xref:System.Net.ServicePointManager> classes to manage connections to the Internet and to help them achieve optimum scale and performance.</span></span>  
  
 <span data-ttu-id="892b6-105">ServicePoint 类给应用程序提供了终结点，应用程序连接到终结点即可访问 Internet 资源。</span><span class="sxs-lookup"><span data-stu-id="892b6-105">The **ServicePoint** class provides an application with an endpoint to which the application can connect to access Internet resources.</span></span> <span data-ttu-id="892b6-106">每个 ServicePoint 都包含信息，该信息有助于通过共享连接之间的优化信息改进性能，优化与 Internet 服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="892b6-106">Each **ServicePoint** contains information that helps optimize connections with an Internet server by sharing optimization information between connections to improve performance.</span></span>  
  
 <span data-ttu-id="892b6-107">每个 ServicePoint 都由统一资源标识符 (URI) 标识，并根据方案标识符和 URI 的主机片段分类。</span><span class="sxs-lookup"><span data-stu-id="892b6-107">Each **ServicePoint** is identified by a Uniform Resource Identifier (URI) and is categorized according to the scheme identifier and host fragments of the URI.</span></span> <span data-ttu-id="892b6-108">例如，将由同一 ServicePoint 实例提供对 URI `http://www.contoso.com/index.htm` 和 `http://www.contoso.com/news.htm?date=today` 的请求，因为它们具有相同的方案标识符片段 (http) 和主机片段(`www.contoso.com`)。</span><span class="sxs-lookup"><span data-stu-id="892b6-108">For example, the same **ServicePoint** instance would provide requests to the URIs `http://www.contoso.com/index.htm` and `http://www.contoso.com/news.htm?date=today` since they have the same scheme identifier (http) and host fragments (`www.contoso.com`).</span></span> <span data-ttu-id="892b6-109">如果应用程序已具有与服务器 `www.contoso.com` 的持久连接，它使用该连接检索两个请求，避免创建两个连接。</span><span class="sxs-lookup"><span data-stu-id="892b6-109">If the application already has a persistent connection to the server `www.contoso.com`, it uses that connection to retrieve both requests, avoiding the need to create two connections.</span></span>  
  
 <span data-ttu-id="892b6-110">ServicePointManager 是管理 ServicePoint 实例的创建和析构的静态类。</span><span class="sxs-lookup"><span data-stu-id="892b6-110">**ServicePointManager** is a static class that manages the creation and destruction of **ServicePoint** instances.</span></span> <span data-ttu-id="892b6-111">如果应用程序请求一个不在现有  ServicePoint 实例集合里的 Internet 资源， ServicePointManager 将会创建 ServicePoint。</span><span class="sxs-lookup"><span data-stu-id="892b6-111">The **ServicePointManager** creates a **ServicePoint** when the application requests an Internet resource that is not in the collection of existing **ServicePoint** instances.</span></span> <span data-ttu-id="892b6-112">在 ServicePoint 实例超出最长空闲时间或现有数量超过应用程序的 ServicePoint 实例最大数量时，将销毁 ServicePoint 实例  。</span><span class="sxs-lookup"><span data-stu-id="892b6-112">**ServicePoint** instances are destroyed when they have exceeded their maximum idle time or when the number of existing **ServicePoint** instances exceeds the maximum number of **ServicePoint** instances for the application.</span></span> <span data-ttu-id="892b6-113">可通过设置 ServicePointManager 上的 <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> 和 <xref:System.Net.ServicePointManager.MaxServicePoints%2A> 属性，来控制默认空闲时间的最大值和 ServicePoint 实例的最大数量。</span><span class="sxs-lookup"><span data-stu-id="892b6-113">You can control both the default maximum idle time and the maximum number of **ServicePoint** instances by setting the <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> and <xref:System.Net.ServicePointManager.MaxServicePoints%2A> properties on the **ServicePointManager**.</span></span>  
  
 <span data-ttu-id="892b6-114">客户端和服务器之间的连接数可能会对应用程序吞吐量产生重大影响。</span><span class="sxs-lookup"><span data-stu-id="892b6-114">The number of connections between a client and server can have a dramatic impact on application throughput.</span></span> <span data-ttu-id="892b6-115">默认情况下，使用 <xref:System.Net.HttpWebRequest> 类的应用程序最多使用与给定服务器的两个持久连接，但是，可以基于每个应用程序设置最大连接数。</span><span class="sxs-lookup"><span data-stu-id="892b6-115">By default, an application using the <xref:System.Net.HttpWebRequest> class uses a maximum of two persistent connections to a given server, but you can set the maximum number of connections on a per-application basis.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="892b6-116">HTTP/1.1 规范将一个应用程序中的连接数限制为每个服务器两个连接。</span><span class="sxs-lookup"><span data-stu-id="892b6-116">The HTTP/1.1 specification limits the number of connections from an application to two connections per server.</span></span>  
  
 <span data-ttu-id="892b6-117">连接的最佳数目取决于应用程序运行的实际情况。</span><span class="sxs-lookup"><span data-stu-id="892b6-117">The optimum number of connections depends on the actual conditions in which the application runs.</span></span> <span data-ttu-id="892b6-118">增加应用程序的可用连接数可能不影响应用程序性能。</span><span class="sxs-lookup"><span data-stu-id="892b6-118">Increasing the number of connections available to the application may not affect application performance.</span></span> <span data-ttu-id="892b6-119">要确定更多连接的影响，请在改变连接数时运行性能测试。</span><span class="sxs-lookup"><span data-stu-id="892b6-119">To determine the impact of more connections, run performance tests while varying the number of connections.</span></span> <span data-ttu-id="892b6-120">在应用程序初始化时改变 ServicePointManager 类上的静态 <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> 属性，可以更改应用程序使用的连接数，如以下代码示例所示。</span><span class="sxs-lookup"><span data-stu-id="892b6-120">You can change the number of connections that an application uses by changing the static <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> property on the **ServicePointManager** class at application initialization, as shown in the following code sample.</span></span>  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 <span data-ttu-id="892b6-121">更改  ServicePointManager.DefaultConnectionLimit 属性不会影响之前初始化的 ServicePoint 实例。</span><span class="sxs-lookup"><span data-stu-id="892b6-121">Changing the **ServicePointManager.DefaultConnectionLimit** property does not affect previously initialized **ServicePoint** instances.</span></span> <span data-ttu-id="892b6-122">下面的代码演示如何将服务器 `http://www.contoso.com` 现有 ServicePoint 上的连接限制更改为存储在 `newLimit` 中的值。</span><span class="sxs-lookup"><span data-stu-id="892b6-122">The following code demonstrates changing the connection limit on an existing **ServicePoint** for the server `http://www.contoso.com` to the value stored in `newLimit`.</span></span>  
  
```csharp  
Uri uri = new Uri("http://www.contoso.com/");  
ServicePoint sp = ServicePointManager.FindServicePoint(uri);  
sp.ConnectionLimit = newLimit;  
```  
  
```vb  
Dim uri As New Uri("http://www.contoso.com/")  
Dim sp As ServicePoint = ServicePointManager.FindServicePoint(uri)  
sp.ConnectionLimit = newLimit  
```  
  
## <a name="see-also"></a><span data-ttu-id="892b6-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="892b6-123">See also</span></span>

- [<span data-ttu-id="892b6-124">连接分组</span><span class="sxs-lookup"><span data-stu-id="892b6-124">Connection Grouping</span></span>](connection-grouping.md)
- [<span data-ttu-id="892b6-125">使用应用程序协议</span><span class="sxs-lookup"><span data-stu-id="892b6-125">Using Application Protocols</span></span>](using-application-protocols.md)

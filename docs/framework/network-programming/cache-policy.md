---
title: 缓存策略
description: 了解缓存策略，即确定使用已请求资源的缓存副本是否可以满足请求的规则。
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- location-based cache policies
- cache [.NET Framework], policies
- request cache policies
- freshness of cached resources
- content cache policies
- expired content
ms.assetid: 1a7e04ec-7872-41c2-96c6-52566dcb412b
ms.openlocfilehash: d63d2b6bf8426968d2120647c8ecea2b7602825a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502660"
---
# <a name="cache-policy"></a><span data-ttu-id="50b9a-103">缓存策略</span><span class="sxs-lookup"><span data-stu-id="50b9a-103">Cache Policy</span></span>
<span data-ttu-id="50b9a-104">缓存策略定义规则，这些规则用于确定使用已请求资源的缓存副本是否可以满足请求。</span><span class="sxs-lookup"><span data-stu-id="50b9a-104">A cache policy defines rules that are used to determine whether a request can be satisfied using a cached copy of the requested resource.</span></span> <span data-ttu-id="50b9a-105">尽管应用程序为新鲜度指定客户端缓存要求，但有效的缓存策略是由客户端缓存要求、服务器的内容有效期限要求以及服务器的重新验证要求确定的。</span><span class="sxs-lookup"><span data-stu-id="50b9a-105">Applications specify client cache requirements for freshness, but the effective cache policy is determined by the client cache requirements, the server's content expiration requirements, and the server's revalidation requirements.</span></span> <span data-ttu-id="50b9a-106">客户端缓存策略和服务器要求的交互始终会造成最保守的缓存策略，有助于确保将最新鲜的内容返回给客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="50b9a-106">The interaction of client cache policy and server requirements always results in the most conservative cache policy, to help ensure that the freshest content is returned to the client application.</span></span>  
  
 <span data-ttu-id="50b9a-107">缓存策略是基于位置或基于时间的。</span><span class="sxs-lookup"><span data-stu-id="50b9a-107">Cache policies are either location-based or time-based.</span></span> <span data-ttu-id="50b9a-108">基于位置的缓存策略根据可从中获取已请求资源的位置定义缓存条目的新鲜度。</span><span class="sxs-lookup"><span data-stu-id="50b9a-108">A location-based cache policy defines the freshness of cached entries based on where the requested resource can be taken from.</span></span> <span data-ttu-id="50b9a-109">基于时间的缓存策略使用检索资源的时间、随资源返回的标头和当前时间来定义缓存条目的新鲜度。</span><span class="sxs-lookup"><span data-stu-id="50b9a-109">A time-based cache policy defines the freshness of cached entries using the time the resource was retrieved, headers returned with the resource, and the current time.</span></span> <span data-ttu-id="50b9a-110">大多数应用程序可以使用基于默认时间的缓存策略，这可在 [Internet 工程任务组 (IETF)](https://www.ietf.org/) 网站上实现 RFC 2616 中指定的缓存策略。</span><span class="sxs-lookup"><span data-stu-id="50b9a-110">Most applications can use the default time-based cache policy, which implements the caching policy specified in RFC 2616, available at [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website.</span></span>  
  
 <span data-ttu-id="50b9a-111">下表中所述的类用于指定缓存策略。</span><span class="sxs-lookup"><span data-stu-id="50b9a-111">The classes described in the following table are used to specify cache policies.</span></span>  
  
|<span data-ttu-id="50b9a-112">类名</span><span class="sxs-lookup"><span data-stu-id="50b9a-112">Class name</span></span>|<span data-ttu-id="50b9a-113">描述</span><span class="sxs-lookup"><span data-stu-id="50b9a-113">Description</span></span>|  
|----------------|-----------------|  
|<xref:System.Net.Cache.HttpRequestCachePolicy>|<span data-ttu-id="50b9a-114">表示使用 <xref:System.Net.HttpWebRequest> 对象请求的资源的基于位置和基于时间的缓存策略。</span><span class="sxs-lookup"><span data-stu-id="50b9a-114">Represents location-based and time-based cache policies for resources requested using <xref:System.Net.HttpWebRequest> objects.</span></span>|  
|<xref:System.Net.Cache.RequestCachePolicy>|<span data-ttu-id="50b9a-115">表示使用 <xref:System.Net.WebRequest> 对象请求的资源的基于位置的缓存策略或基于 <xref:System.Net.Cache.RequestCacheLevel.Default> 时间的缓存策略。</span><span class="sxs-lookup"><span data-stu-id="50b9a-115">Represents location-based cache policies or the <xref:System.Net.Cache.RequestCacheLevel.Default> time-based cache policy for resources requested using <xref:System.Net.WebRequest> objects.</span></span>|  
|<xref:System.Net.Cache.HttpCacheAgeControl>|<span data-ttu-id="50b9a-116">指定用于创建基于时间的 <xref:System.Net.Cache.HttpRequestCachePolicy> 对象的值。</span><span class="sxs-lookup"><span data-stu-id="50b9a-116">Specifies values used to create time-based <xref:System.Net.Cache.HttpRequestCachePolicy> objects.</span></span>|  
|<xref:System.Net.Cache.HttpRequestCacheLevel>|<span data-ttu-id="50b9a-117">指定用于创建基于位置和基于时间的 <xref:System.Net.Cache.HttpRequestCachePolicy> 对象的值。</span><span class="sxs-lookup"><span data-stu-id="50b9a-117">Specifies values used to create location-based and time-based <xref:System.Net.Cache.HttpRequestCachePolicy> objects.</span></span>|  
|<xref:System.Net.Cache.RequestCacheLevel>|<span data-ttu-id="50b9a-118">指定用于创建基于位置或基于 <xref:System.Net.Cache.RequestCacheLevel.Default> 时间的 <xref:System.Net.Cache.RequestCachePolicy> 对象的值。</span><span class="sxs-lookup"><span data-stu-id="50b9a-118">Specifies values used to create location-based or the <xref:System.Net.Cache.RequestCacheLevel.Default> time-based <xref:System.Net.Cache.RequestCachePolicy> objects.</span></span>|  
  
 <span data-ttu-id="50b9a-119">可以为应用程序发出的所有请求或为各个单独的请求定义一个缓存策略。</span><span class="sxs-lookup"><span data-stu-id="50b9a-119">You can define a cache policy for all requests made by your application or for individual requests.</span></span> <span data-ttu-id="50b9a-120">在同时指定应用程序级缓存策略和请求级缓存策略的情况下，会使用请求级策略。</span><span class="sxs-lookup"><span data-stu-id="50b9a-120">When you specify both an application-level cache policy and a request-level cache policy, the request-level policy is used.</span></span> <span data-ttu-id="50b9a-121">通过以编程方式或通过使用应用程序或计算机配置文件，以指定应用程序级缓存策略。</span><span class="sxs-lookup"><span data-stu-id="50b9a-121">You can specify an application-level cache policy programmatically or by using the application or machine configuration files.</span></span> <span data-ttu-id="50b9a-122">有关详细信息，请参阅 [\<requestCaching> 元素（网络设置）](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="50b9a-122">For more information, see [\<requestCaching> Element (Network Settings)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span></span>  
  
 <span data-ttu-id="50b9a-123">若要创建缓存策略，必须通过创建 <xref:System.Net.Cache.RequestCachePolicy> 或 <xref:System.Net.Cache.HttpRequestCachePolicy> 类的实例来创建策略对象。</span><span class="sxs-lookup"><span data-stu-id="50b9a-123">To create a cache policy, you must create a policy object by creating an instance of the <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> class.</span></span> <span data-ttu-id="50b9a-124">若要针对某个请求指定策略，请将此请求的 <xref:System.Net.WebRequest.CachePolicy%2A> 属性设置为策略对象。</span><span class="sxs-lookup"><span data-stu-id="50b9a-124">To specify the policy on a request, set the request's <xref:System.Net.WebRequest.CachePolicy%2A> property to the policy object.</span></span> <span data-ttu-id="50b9a-125">在以编程方式设置应用程序级策略时，请将 <xref:System.Net.HttpWebRequest.DefaultCachePolicy%2A> 属性设置为策略对象。</span><span class="sxs-lookup"><span data-stu-id="50b9a-125">When setting an application-level policy programmatically, set the <xref:System.Net.HttpWebRequest.DefaultCachePolicy%2A> property to the policy object.</span></span>  
  
 <span data-ttu-id="50b9a-126">有关演示如何创建和使用缓存策略的代码示例，请参阅[在网络应用程序中配置缓存](configuring-caching-in-network-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="50b9a-126">For code examples that demonstrate creating and using cache policies, see [Configuring Caching in Network Applications](configuring-caching-in-network-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50b9a-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="50b9a-127">See also</span></span>

- [<span data-ttu-id="50b9a-128">网络应用程序的缓存管理</span><span class="sxs-lookup"><span data-stu-id="50b9a-128">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="50b9a-129">基于位置的缓存策略</span><span class="sxs-lookup"><span data-stu-id="50b9a-129">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="50b9a-130">基于时间的缓存策略</span><span class="sxs-lookup"><span data-stu-id="50b9a-130">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="50b9a-131">在网络应用程序中配置缓存</span><span class="sxs-lookup"><span data-stu-id="50b9a-131">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)

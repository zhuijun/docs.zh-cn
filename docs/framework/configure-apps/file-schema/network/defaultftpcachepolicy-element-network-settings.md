---
title: <defaultFtpCachePolicy> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
ms.openlocfilehash: 9261a430642cb4d5ac4507835bd0fd3561bd8c02
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088432"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a><span data-ttu-id="76547-102">\<defaultFtpCachePolicy> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="76547-102">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="76547-103">介绍 FTP 缓存是否处于活动状态，并描述默认缓存策略。</span><span class="sxs-lookup"><span data-stu-id="76547-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultFtpCachePolicy>**

## <a name="syntax"></a><span data-ttu-id="76547-104">语法</span><span class="sxs-lookup"><span data-stu-id="76547-104">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76547-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="76547-105">Attributes and Elements</span></span>  
 <span data-ttu-id="76547-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="76547-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76547-107">特性</span><span class="sxs-lookup"><span data-stu-id="76547-107">Attributes</span></span>  
  
|<span data-ttu-id="76547-108">属性</span><span class="sxs-lookup"><span data-stu-id="76547-108">Attribute</span></span>|<span data-ttu-id="76547-109">说明</span><span class="sxs-lookup"><span data-stu-id="76547-109">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="76547-110">指定 FTP 缓存策略。</span><span class="sxs-lookup"><span data-stu-id="76547-110">Specifies the FTP caching policy.</span></span> <span data-ttu-id="76547-111">默认值为 `Default`。</span><span class="sxs-lookup"><span data-stu-id="76547-111">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="76547-112">policyLevel 特性</span><span class="sxs-lookup"><span data-stu-id="76547-112">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="76547-113">值</span><span class="sxs-lookup"><span data-stu-id="76547-113">Value</span></span>|<span data-ttu-id="76547-114">说明</span><span class="sxs-lookup"><span data-stu-id="76547-114">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="76547-115">如果资源是最新的，则返回缓存的资源，内容长度准确，并且存在过期、修改和内容长度属性。</span><span class="sxs-lookup"><span data-stu-id="76547-115">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="76547-116">从服务器返回资源。</span><span class="sxs-lookup"><span data-stu-id="76547-116">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="76547-117">如果内容长度存在并且与条目大小匹配，则返回缓存的资源。</span><span class="sxs-lookup"><span data-stu-id="76547-117">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="76547-118">如果提供了内容长度并与条目大小匹配，则返回缓存的资源;否则，将从服务器下载资源，并将其返回给调用方。</span><span class="sxs-lookup"><span data-stu-id="76547-118">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="76547-119">如果缓存资源的时间戳与服务器上资源的时间戳相同，则返回缓存的资源;否则，将从服务器下载资源，并将其存储在缓存中，并将其返回给调用方。</span><span class="sxs-lookup"><span data-stu-id="76547-119">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="76547-120">从服务器下载资源，将其存储在缓存中，并将资源返回给调用方。</span><span class="sxs-lookup"><span data-stu-id="76547-120">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="76547-121">如果缓存的资源存在，则将其删除。</span><span class="sxs-lookup"><span data-stu-id="76547-121">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="76547-122">从服务器下载资源，并将其返回给调用方。</span><span class="sxs-lookup"><span data-stu-id="76547-122">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="76547-123">如果时间戳与服务器上的资源的时间戳相同，则使用资源的缓存副本满足请求；否则从服务器下载资源，将资源展示给调用方，然后再存储在缓存中。</span><span class="sxs-lookup"><span data-stu-id="76547-123">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="76547-124">子元素</span><span class="sxs-lookup"><span data-stu-id="76547-124">Child Elements</span></span>  
 <span data-ttu-id="76547-125">无。</span><span class="sxs-lookup"><span data-stu-id="76547-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="76547-126">父元素</span><span class="sxs-lookup"><span data-stu-id="76547-126">Parent Elements</span></span>  
  
|<span data-ttu-id="76547-127">元素</span><span class="sxs-lookup"><span data-stu-id="76547-127">Element</span></span>|<span data-ttu-id="76547-128">描述</span><span class="sxs-lookup"><span data-stu-id="76547-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76547-129">requestCaching</span><span class="sxs-lookup"><span data-stu-id="76547-129">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="76547-130">控制网络请求的缓存机制。</span><span class="sxs-lookup"><span data-stu-id="76547-130">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76547-131">注解</span><span class="sxs-lookup"><span data-stu-id="76547-131">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="76547-132">示例</span><span class="sxs-lookup"><span data-stu-id="76547-132">Example</span></span>  
 <span data-ttu-id="76547-133">下面的示例演示如何指定的 FTP 缓存策略 `NoCacheNoStore` 。</span><span class="sxs-lookup"><span data-stu-id="76547-133">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultFtpCachePolicy  
        policyLevel="NoCacheNoStore">  
      </defaultFtpCachePolicy>  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="76547-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="76547-134">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="76547-135">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="76547-135">Network Settings Schema</span></span>](index.md)

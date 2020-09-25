---
title: <memoryCache> 元素（缓存设置）
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 14480682c5d221216df5da3844897855d1d92a0d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192420"
---
# <a name="memorycache-element-cache-settings"></a><span data-ttu-id="244a0-102">\<memoryCache> 元素（缓存设置）</span><span class="sxs-lookup"><span data-stu-id="244a0-102">\<memoryCache> Element (Cache Settings)</span></span>

<span data-ttu-id="244a0-103">定义一个用于配置基于 <xref:System.Runtime.Caching.MemoryCache> 类的缓存的元素。</span><span class="sxs-lookup"><span data-stu-id="244a0-103">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="244a0-104"><xref:System.Runtime.Caching.Configuration.MemoryCacheElement> 类定义可以用于配置缓存的 [memoryCache](memorycache-element-cache-settings.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="244a0-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> class defines a [memoryCache](memorycache-element-cache-settings.md) element that you can use to configure the cache.</span></span> <span data-ttu-id="244a0-105">可以在单个应用程序中使用 <xref:System.Runtime.Caching.MemoryCache> 类的多个实例。</span><span class="sxs-lookup"><span data-stu-id="244a0-105">Multiple instances of the <xref:System.Runtime.Caching.MemoryCache> class can be used in a single application.</span></span> <span data-ttu-id="244a0-106">配置文件中的每个 `memoryCache` 元素可以包含一个命名 <xref:System.Runtime.Caching.MemoryCache> 实例的设置。</span><span class="sxs-lookup"><span data-stu-id="244a0-106">Each `memoryCache` element in the configuration file can contain settings for a named <xref:System.Runtime.Caching.MemoryCache> instance.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<memoryCache>**  
  
## <a name="syntax"></a><span data-ttu-id="244a0-107">语法</span><span class="sxs-lookup"><span data-stu-id="244a0-107">Syntax</span></span>  
  
```xml  
<memoryCache>
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>
</memoryCache>  
```  
  
## <a name="type"></a><span data-ttu-id="244a0-108">类型</span><span class="sxs-lookup"><span data-stu-id="244a0-108">Type</span></span>  

 <span data-ttu-id="244a0-109"><xref:System.Runtime.Caching.MemoryCache> 类。</span><span class="sxs-lookup"><span data-stu-id="244a0-109"><xref:System.Runtime.Caching.MemoryCache> class.</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="244a0-110">特性和元素</span><span class="sxs-lookup"><span data-stu-id="244a0-110">Attributes and Elements</span></span>  

 <span data-ttu-id="244a0-111">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="244a0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="244a0-112">特性</span><span class="sxs-lookup"><span data-stu-id="244a0-112">Attributes</span></span>  
  
|<span data-ttu-id="244a0-113">属性</span><span class="sxs-lookup"><span data-stu-id="244a0-113">Attribute</span></span>|<span data-ttu-id="244a0-114">描述</span><span class="sxs-lookup"><span data-stu-id="244a0-114">Description</span></span>|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="244a0-115"><xref:System.Runtime.Caching.MemoryCache> 对象的实例可以增长到的最大内存大小（以兆字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="244a0-115">The maximum memory size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> object can grow to.</span></span> <span data-ttu-id="244a0-116">默认值为 0，这意味着默认情况下使用 <xref:System.Runtime.Caching.MemoryCache> 类的自动调整大小启发。</span><span class="sxs-lookup"><span data-stu-id="244a0-116">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="244a0-117">缓存配置的名称。</span><span class="sxs-lookup"><span data-stu-id="244a0-117">The name of the cache configuration.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="244a0-118">缓存可以使用的物理内存的百分比。</span><span class="sxs-lookup"><span data-stu-id="244a0-118">The percentage of physical memory that can be used by the cache.</span></span> <span data-ttu-id="244a0-119">默认值为 0，这意味着默认情况下使用 <xref:System.Runtime.Caching.MemoryCache> 类的自动调整大小启发。</span><span class="sxs-lookup"><span data-stu-id="244a0-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="244a0-120">一个时间间隔的值，在该时间间隔之后，缓存实现会将当前内存负载与为缓存实例设置的基于绝对值和百分比的内存限制进行比较。</span><span class="sxs-lookup"><span data-stu-id="244a0-120">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="244a0-121">该值以“HH:MM:SS”格式输入。</span><span class="sxs-lookup"><span data-stu-id="244a0-121">The value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="244a0-122">子元素</span><span class="sxs-lookup"><span data-stu-id="244a0-122">Child Elements</span></span>  
  
|<span data-ttu-id="244a0-123">元素</span><span class="sxs-lookup"><span data-stu-id="244a0-123">Element</span></span>|<span data-ttu-id="244a0-124">描述</span><span class="sxs-lookup"><span data-stu-id="244a0-124">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="244a0-125">包含 `namedCache` 实例的配置设置的集合。</span><span class="sxs-lookup"><span data-stu-id="244a0-125">Contains a collection of configuration settings for the `namedCache` instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="244a0-126">父元素</span><span class="sxs-lookup"><span data-stu-id="244a0-126">Parent Elements</span></span>  
  
|<span data-ttu-id="244a0-127">元素</span><span class="sxs-lookup"><span data-stu-id="244a0-127">Element</span></span>|<span data-ttu-id="244a0-128">描述</span><span class="sxs-lookup"><span data-stu-id="244a0-128">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="244a0-129">指定公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="244a0-129">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="244a0-130">包含使你可以在 .NET Framework 中内置的应用程序中实现输出缓存的类型。</span><span class="sxs-lookup"><span data-stu-id="244a0-130">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="244a0-131">备注</span><span class="sxs-lookup"><span data-stu-id="244a0-131">Remarks</span></span>  

 <span data-ttu-id="244a0-132"><xref:System.Runtime.Caching.MemoryCache> 类是抽象 <xref:System.Runtime.Caching.ObjectCache> 类的具体实现。</span><span class="sxs-lookup"><span data-stu-id="244a0-132">The <xref:System.Runtime.Caching.MemoryCache> class is a concrete implementation of the abstract <xref:System.Runtime.Caching.ObjectCache> class.</span></span> <span data-ttu-id="244a0-133"><xref:System.Runtime.Caching.MemoryCache> 类的实例可以随来自应用程序配置文件的配置信息一起提供。</span><span class="sxs-lookup"><span data-stu-id="244a0-133">Instances of the <xref:System.Runtime.Caching.MemoryCache> class can be supplied with configuration information from application configuration files.</span></span> <span data-ttu-id="244a0-134">[memoryCache](memorycache-element-cache-settings.md) 配置节包含 `namedCaches` 配置集合。</span><span class="sxs-lookup"><span data-stu-id="244a0-134">The [memoryCache](memorycache-element-cache-settings.md) configuration section contains a `namedCaches` configuration collection.</span></span>  
  
 <span data-ttu-id="244a0-135">基于内存的缓存对象进行初始化时，它首先尝试查找与传递给内存缓存构造函数的参数中的名称进行匹配的 `namedCaches` 项。</span><span class="sxs-lookup"><span data-stu-id="244a0-135">When a memory-based cache object is initialized, it first tries to find a `namedCaches` entry that matches the name in the parameter that is passed to the memory cache constructor.</span></span> <span data-ttu-id="244a0-136">如果找到 `namedCaches` 项，则从配置文件检索轮询和内存管理信息。</span><span class="sxs-lookup"><span data-stu-id="244a0-136">If a `namedCaches` entry is found, the polling and memory-management information are retrieved from the configuration file.</span></span>  
  
 <span data-ttu-id="244a0-137">初始化过程随后使用构造函数中配置信息的名称/值对的可选集合来确定是否重写了任何配置项。</span><span class="sxs-lookup"><span data-stu-id="244a0-137">The initialization process then determines whether any configuration entries were overridden, by using the optional collection of name/value pairs of configuration information in the constructor.</span></span> <span data-ttu-id="244a0-138">如果在名称/值对集合中传递以下值之一，则这些值会重写从配置文件获取的信息：</span><span class="sxs-lookup"><span data-stu-id="244a0-138">If you pass any one of the following values in the name/value pair collection, these values override information obtained from the configuration file:</span></span>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a><span data-ttu-id="244a0-139">示例</span><span class="sxs-lookup"><span data-stu-id="244a0-139">Example</span></span>  

 <span data-ttu-id="244a0-140">下面的示例演示如何 <xref:System.Runtime.Caching.MemoryCache> 通过将 `name` 属性设置为 "default"，将对象的名称设置为默认缓存对象名称。</span><span class="sxs-lookup"><span data-stu-id="244a0-140">The following example shows how to set the name of the <xref:System.Runtime.Caching.MemoryCache> object to the default cache object name by setting the `name` attribute to "Default".</span></span>  
  
 <span data-ttu-id="244a0-141">将 `cacheMemoryLimitMegabytes` 属性和 `physicalMemoryLimitPercentage` 属性设置为零。</span><span class="sxs-lookup"><span data-stu-id="244a0-141">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryLimitPercentage` attribute are set to zero.</span></span> <span data-ttu-id="244a0-142">将这些特性设置为零意味着默认情况下使用 <xref:System.Runtime.Caching.MemoryCache> 自动调整大小试探法。</span><span class="sxs-lookup"><span data-stu-id="244a0-142">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="244a0-143">每隔两分钟，缓存实现应对当前内存负载和基于百分比的绝对内存限制进行比较。</span><span class="sxs-lookup"><span data-stu-id="244a0-143">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
```xml  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"
               cacheMemoryLimitMegabytes="0"
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="244a0-144">请参阅</span><span class="sxs-lookup"><span data-stu-id="244a0-144">See also</span></span>

- <xref:System.Runtime.Caching.MemoryCache>
- [<span data-ttu-id="244a0-145">\<system.runtime.caching> 元素 (缓存设置) </span><span class="sxs-lookup"><span data-stu-id="244a0-145">\<system.runtime.caching> Element (Cache Settings)</span></span>](system-runtime-caching-element-cache-settings.md)
- [<span data-ttu-id="244a0-146">\<namedCaches> 元素 (缓存设置) </span><span class="sxs-lookup"><span data-stu-id="244a0-146">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)

---
title: <memoryCache> 元素（缓存设置）
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 94c21e0408b7616bf0c8a24267b72bfa7cc3aaa0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153979"
---
# <a name="memorycache-element-cache-settings"></a><span data-ttu-id="84bf9-102">\<memoryCache> 元素（缓存设置）</span><span class="sxs-lookup"><span data-stu-id="84bf9-102">\<memoryCache> Element (Cache Settings)</span></span>
<span data-ttu-id="84bf9-103">定义一个用于配置基于 <xref:System.Runtime.Caching.MemoryCache> 类的缓存的元素。</span><span class="sxs-lookup"><span data-stu-id="84bf9-103">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="84bf9-104"><xref:System.Runtime.Caching.Configuration.MemoryCacheElement> 类定义可以用于配置缓存的 [memoryCache](memorycache-element-cache-settings.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="84bf9-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> class defines a [memoryCache](memorycache-element-cache-settings.md) element that you can use to configure the cache.</span></span> <span data-ttu-id="84bf9-105">可以在单个应用程序中使用 <xref:System.Runtime.Caching.MemoryCache> 类的多个实例。</span><span class="sxs-lookup"><span data-stu-id="84bf9-105">Multiple instances of the <xref:System.Runtime.Caching.MemoryCache> class can be used in a single application.</span></span> <span data-ttu-id="84bf9-106">配置文件中的每个 `memoryCache` 元素可以包含一个命名 <xref:System.Runtime.Caching.MemoryCache> 实例的设置。</span><span class="sxs-lookup"><span data-stu-id="84bf9-106">Each `memoryCache` element in the configuration file can contain settings for a named <xref:System.Runtime.Caching.MemoryCache> instance.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<memoryCache>**  
  
## <a name="syntax"></a><span data-ttu-id="84bf9-107">语法</span><span class="sxs-lookup"><span data-stu-id="84bf9-107">Syntax</span></span>  
  
```xml  
<memoryCache>
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>
</memoryCache>  
```  
  
## <a name="type"></a><span data-ttu-id="84bf9-108">类型</span><span class="sxs-lookup"><span data-stu-id="84bf9-108">Type</span></span>  
 <span data-ttu-id="84bf9-109"><xref:System.Runtime.Caching.MemoryCache> 类。</span><span class="sxs-lookup"><span data-stu-id="84bf9-109"><xref:System.Runtime.Caching.MemoryCache> class.</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84bf9-110">特性和元素</span><span class="sxs-lookup"><span data-stu-id="84bf9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="84bf9-111">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="84bf9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84bf9-112">特性</span><span class="sxs-lookup"><span data-stu-id="84bf9-112">Attributes</span></span>  
  
|<span data-ttu-id="84bf9-113">属性</span><span class="sxs-lookup"><span data-stu-id="84bf9-113">Attribute</span></span>|<span data-ttu-id="84bf9-114">说明</span><span class="sxs-lookup"><span data-stu-id="84bf9-114">Description</span></span>|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="84bf9-115"><xref:System.Runtime.Caching.MemoryCache> 对象的实例可以增长到的最大内存大小（以兆字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="84bf9-115">The maximum memory size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> object can grow to.</span></span> <span data-ttu-id="84bf9-116">默认值为 0，这意味着默认情况下使用 <xref:System.Runtime.Caching.MemoryCache> 类的自动调整大小启发。</span><span class="sxs-lookup"><span data-stu-id="84bf9-116">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="84bf9-117">缓存配置的名称。</span><span class="sxs-lookup"><span data-stu-id="84bf9-117">The name of the cache configuration.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="84bf9-118">缓存可以使用的物理内存的百分比。</span><span class="sxs-lookup"><span data-stu-id="84bf9-118">The percentage of physical memory that can be used by the cache.</span></span> <span data-ttu-id="84bf9-119">默认值为 0，这意味着默认情况下使用 <xref:System.Runtime.Caching.MemoryCache> 类的自动调整大小启发。</span><span class="sxs-lookup"><span data-stu-id="84bf9-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="84bf9-120">一个时间间隔的值，在该时间间隔之后，缓存实现会将当前内存负载与为缓存实例设置的基于绝对值和百分比的内存限制进行比较。</span><span class="sxs-lookup"><span data-stu-id="84bf9-120">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="84bf9-121">该值以“HH:MM:SS”格式输入。</span><span class="sxs-lookup"><span data-stu-id="84bf9-121">The value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="84bf9-122">子元素</span><span class="sxs-lookup"><span data-stu-id="84bf9-122">Child Elements</span></span>  
  
|<span data-ttu-id="84bf9-123">元素</span><span class="sxs-lookup"><span data-stu-id="84bf9-123">Element</span></span>|<span data-ttu-id="84bf9-124">描述</span><span class="sxs-lookup"><span data-stu-id="84bf9-124">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="84bf9-125">包含 `namedCache` 实例的配置设置的集合。</span><span class="sxs-lookup"><span data-stu-id="84bf9-125">Contains a collection of configuration settings for the `namedCache` instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="84bf9-126">父元素</span><span class="sxs-lookup"><span data-stu-id="84bf9-126">Parent Elements</span></span>  
  
|<span data-ttu-id="84bf9-127">元素</span><span class="sxs-lookup"><span data-stu-id="84bf9-127">Element</span></span>|<span data-ttu-id="84bf9-128">描述</span><span class="sxs-lookup"><span data-stu-id="84bf9-128">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="84bf9-129">指定公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="84bf9-129">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="84bf9-130">包含使你可以在 .NET Framework 中内置的应用程序中实现输出缓存的类型。</span><span class="sxs-lookup"><span data-stu-id="84bf9-130">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84bf9-131">注解</span><span class="sxs-lookup"><span data-stu-id="84bf9-131">Remarks</span></span>  
 <span data-ttu-id="84bf9-132"><xref:System.Runtime.Caching.MemoryCache> 类是抽象 <xref:System.Runtime.Caching.ObjectCache> 类的具体实现。</span><span class="sxs-lookup"><span data-stu-id="84bf9-132">The <xref:System.Runtime.Caching.MemoryCache> class is a concrete implementation of the abstract <xref:System.Runtime.Caching.ObjectCache> class.</span></span> <span data-ttu-id="84bf9-133"><xref:System.Runtime.Caching.MemoryCache> 类的实例可以随来自应用程序配置文件的配置信息一起提供。</span><span class="sxs-lookup"><span data-stu-id="84bf9-133">Instances of the <xref:System.Runtime.Caching.MemoryCache> class can be supplied with configuration information from application configuration files.</span></span> <span data-ttu-id="84bf9-134">[memoryCache](memorycache-element-cache-settings.md) 配置节包含 `namedCaches` 配置集合。</span><span class="sxs-lookup"><span data-stu-id="84bf9-134">The [memoryCache](memorycache-element-cache-settings.md) configuration section contains a `namedCaches` configuration collection.</span></span>  
  
 <span data-ttu-id="84bf9-135">基于内存的缓存对象进行初始化时，它首先尝试查找与传递给内存缓存构造函数的参数中的名称进行匹配的 `namedCaches` 项。</span><span class="sxs-lookup"><span data-stu-id="84bf9-135">When a memory-based cache object is initialized, it first tries to find a `namedCaches` entry that matches the name in the parameter that is passed to the memory cache constructor.</span></span> <span data-ttu-id="84bf9-136">如果找到 `namedCaches` 项，则从配置文件检索轮询和内存管理信息。</span><span class="sxs-lookup"><span data-stu-id="84bf9-136">If a `namedCaches` entry is found, the polling and memory-management information are retrieved from the configuration file.</span></span>  
  
 <span data-ttu-id="84bf9-137">初始化过程随后使用构造函数中配置信息的名称/值对的可选集合来确定是否重写了任何配置项。</span><span class="sxs-lookup"><span data-stu-id="84bf9-137">The initialization process then determines whether any configuration entries were overridden, by using the optional collection of name/value pairs of configuration information in the constructor.</span></span> <span data-ttu-id="84bf9-138">如果在名称/值对集合中传递以下值之一，则这些值会重写从配置文件获取的信息：</span><span class="sxs-lookup"><span data-stu-id="84bf9-138">If you pass any one of the following values in the name/value pair collection, these values override information obtained from the configuration file:</span></span>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a><span data-ttu-id="84bf9-139">示例</span><span class="sxs-lookup"><span data-stu-id="84bf9-139">Example</span></span>  
 <span data-ttu-id="84bf9-140">下面的示例演示如何 <xref:System.Runtime.Caching.MemoryCache> 通过将 `name` 属性设置为 "default"，将对象的名称设置为默认缓存对象名称。</span><span class="sxs-lookup"><span data-stu-id="84bf9-140">The following example shows how to set the name of the <xref:System.Runtime.Caching.MemoryCache> object to the default cache object name by setting the `name` attribute to "Default".</span></span>  
  
 <span data-ttu-id="84bf9-141">将 `cacheMemoryLimitMegabytes` 属性和 `physicalMemoryLimitPercentage` 属性设置为零。</span><span class="sxs-lookup"><span data-stu-id="84bf9-141">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryLimitPercentage` attribute are set to zero.</span></span> <span data-ttu-id="84bf9-142">将这些特性设置为零意味着默认情况下使用 <xref:System.Runtime.Caching.MemoryCache> 自动调整大小试探法。</span><span class="sxs-lookup"><span data-stu-id="84bf9-142">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="84bf9-143">每隔两分钟，缓存实现应对当前内存负载和基于百分比的绝对内存限制进行比较。</span><span class="sxs-lookup"><span data-stu-id="84bf9-143">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="84bf9-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="84bf9-144">See also</span></span>

- <xref:System.Runtime.Caching.MemoryCache>
- [<span data-ttu-id="84bf9-145">\<system.runtime.caching>元素（缓存设置）</span><span class="sxs-lookup"><span data-stu-id="84bf9-145">\<system.runtime.caching> Element (Cache Settings)</span></span>](system-runtime-caching-element-cache-settings.md)
- [<span data-ttu-id="84bf9-146">\<namedCaches>元素（缓存设置）</span><span class="sxs-lookup"><span data-stu-id="84bf9-146">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)

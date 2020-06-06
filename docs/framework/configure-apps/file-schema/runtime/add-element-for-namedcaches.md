---
title: <namedCaches> 的 <add> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: c1345022b79df371ad9c89a39a0a8b625e26608c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154500"
---
# <a name="add-element-for-namedcaches"></a><span data-ttu-id="36e34-102">\<namedCaches> 的 \<add> 元素</span><span class="sxs-lookup"><span data-stu-id="36e34-102">\<add> Element for \<namedCaches></span></span>
<span data-ttu-id="36e34-103">向 `namedCache` 内存缓存的集合中添加项 `namedCaches` 。</span><span class="sxs-lookup"><span data-stu-id="36e34-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="36e34-104">语法</span><span class="sxs-lookup"><span data-stu-id="36e34-104">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="36e34-105">类型</span><span class="sxs-lookup"><span data-stu-id="36e34-105">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36e34-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="36e34-106">Attributes and Elements</span></span>  
 <span data-ttu-id="36e34-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="36e34-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36e34-108">特性</span><span class="sxs-lookup"><span data-stu-id="36e34-108">Attributes</span></span>  
  
|<span data-ttu-id="36e34-109">属性</span><span class="sxs-lookup"><span data-stu-id="36e34-109">Attribute</span></span>|<span data-ttu-id="36e34-110">说明</span><span class="sxs-lookup"><span data-stu-id="36e34-110">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="36e34-111">一个整数值，指定的实例可以增长到的最大允许大小（以 mb <xref:System.Runtime.Caching.MemoryCache> 为单位）。</span><span class="sxs-lookup"><span data-stu-id="36e34-111">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="36e34-112">默认值为0，这意味着 <xref:System.Runtime.Caching.MemoryCache> 默认情况下使用类的自动调整试探法。</span><span class="sxs-lookup"><span data-stu-id="36e34-112">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="36e34-113">缓存的名称。</span><span class="sxs-lookup"><span data-stu-id="36e34-113">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="36e34-114">一个介于0到100之间的整数值，用于指定缓存可使用的实际安装计算机内存的最大百分比。</span><span class="sxs-lookup"><span data-stu-id="36e34-114">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="36e34-115">默认值为0，这意味着 <xref:System.Runtime.Caching.MemoryCache> 默认情况下使用类的自动调整试探法。</span><span class="sxs-lookup"><span data-stu-id="36e34-115">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="36e34-116">一个时间间隔的值，在该时间间隔之后，缓存实现会将当前内存负载与为缓存实例设置的基于绝对值和百分比的内存限制进行比较。</span><span class="sxs-lookup"><span data-stu-id="36e34-116">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="36e34-117">此值以 "HH： MM： SS" 格式输入。</span><span class="sxs-lookup"><span data-stu-id="36e34-117">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="36e34-118">子元素</span><span class="sxs-lookup"><span data-stu-id="36e34-118">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="36e34-119">父元素</span><span class="sxs-lookup"><span data-stu-id="36e34-119">Parent Elements</span></span>  
  
|<span data-ttu-id="36e34-120">元素</span><span class="sxs-lookup"><span data-stu-id="36e34-120">Element</span></span>|<span data-ttu-id="36e34-121">描述</span><span class="sxs-lookup"><span data-stu-id="36e34-121">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="36e34-122">包含命名实例的配置设置的集合 <xref:System.Runtime.Caching.MemoryCache> 。</span><span class="sxs-lookup"><span data-stu-id="36e34-122">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36e34-123">注解</span><span class="sxs-lookup"><span data-stu-id="36e34-123">Remarks</span></span>  
 <span data-ttu-id="36e34-124">`add`元素向内存缓存的集合中添加项 `namedCaches` 。</span><span class="sxs-lookup"><span data-stu-id="36e34-124">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="36e34-125">您可以在使用元素之前使用[clear](clear-element-for-namedcaches.md)元素 `add` ，以确保集合中没有其他命名缓存。</span><span class="sxs-lookup"><span data-stu-id="36e34-125">You can use the [clear](clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="36e34-126">此元素可在 machine.config 文件和 web.config 文件中使用。</span><span class="sxs-lookup"><span data-stu-id="36e34-126">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36e34-127">示例</span><span class="sxs-lookup"><span data-stu-id="36e34-127">Example</span></span>  
 <span data-ttu-id="36e34-128">下面的示例演示如何为内存缓存的集合定义默认项的设置 `namedCache` `namedCaches` 。</span><span class="sxs-lookup"><span data-stu-id="36e34-128">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"
               cacheMemoryLimitMegabytes="0"
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="36e34-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="36e34-129">See also</span></span>

- [<span data-ttu-id="36e34-130">\<namedCaches>元素（缓存设置）</span><span class="sxs-lookup"><span data-stu-id="36e34-130">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)

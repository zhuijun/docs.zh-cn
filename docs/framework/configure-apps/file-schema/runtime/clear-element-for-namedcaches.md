---
title: <namedCaches> 的 <clear> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: bcc0e23f0c47ad3a98430e36da31d39612caa3c9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252759"
---
# <a name="clear-element-for-namedcaches"></a><span data-ttu-id="13191-102">\<namedCaches> 的 \<clear> 元素</span><span class="sxs-lookup"><span data-stu-id="13191-102">\<clear> Element for \<namedCaches></span></span>
<span data-ttu-id="13191-103">清除 `namedCache` 内存缓存的集合中的所有项 `namedCaches` 。</span><span class="sxs-lookup"><span data-stu-id="13191-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a><span data-ttu-id="13191-104">语法</span><span class="sxs-lookup"><span data-stu-id="13191-104">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="Default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="13191-105">类型</span><span class="sxs-lookup"><span data-stu-id="13191-105">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13191-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="13191-106">Attributes and Elements</span></span>  
 <span data-ttu-id="13191-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="13191-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13191-108">特性</span><span class="sxs-lookup"><span data-stu-id="13191-108">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="13191-109">子元素</span><span class="sxs-lookup"><span data-stu-id="13191-109">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="13191-110">父元素</span><span class="sxs-lookup"><span data-stu-id="13191-110">Parent Elements</span></span>  
  
|<span data-ttu-id="13191-111">元素</span><span class="sxs-lookup"><span data-stu-id="13191-111">Element</span></span>|<span data-ttu-id="13191-112">说明</span><span class="sxs-lookup"><span data-stu-id="13191-112">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="13191-113">包含命名实例的配置设置的集合 <xref:System.Runtime.Caching.MemoryCache> 。</span><span class="sxs-lookup"><span data-stu-id="13191-113">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13191-114">注解</span><span class="sxs-lookup"><span data-stu-id="13191-114">Remarks</span></span>  
 <span data-ttu-id="13191-115">`clear`元素清除 `namedCache` 内存缓存的命名缓存集合中的所有项。</span><span class="sxs-lookup"><span data-stu-id="13191-115">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="13191-116">在 `clear` 使用 `add` 元素添加新的命名缓存条目之前，可以使用元素，以便确定集合中没有其他命名缓存。</span><span class="sxs-lookup"><span data-stu-id="13191-116">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13191-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="13191-117">See also</span></span>

- [<span data-ttu-id="13191-118">\<namedCaches>元素（缓存设置）</span><span class="sxs-lookup"><span data-stu-id="13191-118">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)

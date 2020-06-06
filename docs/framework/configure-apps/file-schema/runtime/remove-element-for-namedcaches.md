---
title: <namedCaches> 的 <remove> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
ms.openlocfilehash: 991ad0eb9c04c27ded4d566115107ac7b47a71e1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252341"
---
# <a name="remove-element-for-namedcaches"></a><span data-ttu-id="6854e-102">\<namedCaches> 的 \<remove> 元素</span><span class="sxs-lookup"><span data-stu-id="6854e-102">\<remove> Element for \<namedCaches></span></span>
<span data-ttu-id="6854e-103">从内存缓存的 `namedCaches` 集合中删除一个命名的缓存条目。</span><span class="sxs-lookup"><span data-stu-id="6854e-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="6854e-104">语法</span><span class="sxs-lookup"><span data-stu-id="6854e-104">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="6854e-105">类型</span><span class="sxs-lookup"><span data-stu-id="6854e-105">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6854e-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="6854e-106">Attributes and Elements</span></span>  
 <span data-ttu-id="6854e-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6854e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6854e-108">特性</span><span class="sxs-lookup"><span data-stu-id="6854e-108">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="6854e-109">子元素</span><span class="sxs-lookup"><span data-stu-id="6854e-109">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="6854e-110">父元素</span><span class="sxs-lookup"><span data-stu-id="6854e-110">Parent Elements</span></span>  
  
|<span data-ttu-id="6854e-111">元素</span><span class="sxs-lookup"><span data-stu-id="6854e-111">Element</span></span>|<span data-ttu-id="6854e-112">说明</span><span class="sxs-lookup"><span data-stu-id="6854e-112">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="6854e-113">包含命名实例的配置设置的集合 <xref:System.Runtime.Caching.MemoryCache> 。</span><span class="sxs-lookup"><span data-stu-id="6854e-113">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6854e-114">注解</span><span class="sxs-lookup"><span data-stu-id="6854e-114">Remarks</span></span>  
 <span data-ttu-id="6854e-115">`remove`元素 `namedCache` 从内存缓存的命名缓存集合中删除一个条目。</span><span class="sxs-lookup"><span data-stu-id="6854e-115">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6854e-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6854e-116">See also</span></span>

- [<span data-ttu-id="6854e-117">\<namedCaches>元素（缓存设置）</span><span class="sxs-lookup"><span data-stu-id="6854e-117">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)

---
title: <namedCaches> 的 <remove> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
ms.openlocfilehash: c8ad5a0ce6d7a3059943b3962b9255385cea6e15
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183983"
---
# <a name="remove-element-for-namedcaches"></a><span data-ttu-id="fcd62-102">\<namedCaches> 的 \<remove> 元素</span><span class="sxs-lookup"><span data-stu-id="fcd62-102">\<remove> Element for \<namedCaches></span></span>

<span data-ttu-id="fcd62-103">从内存缓存的 `namedCaches` 集合中删除一个命名的缓存条目。</span><span class="sxs-lookup"><span data-stu-id="fcd62-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="fcd62-104">语法</span><span class="sxs-lookup"><span data-stu-id="fcd62-104">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="fcd62-105">类型</span><span class="sxs-lookup"><span data-stu-id="fcd62-105">Type</span></span>  

 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fcd62-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="fcd62-106">Attributes and Elements</span></span>  

 <span data-ttu-id="fcd62-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="fcd62-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fcd62-108">特性</span><span class="sxs-lookup"><span data-stu-id="fcd62-108">Attributes</span></span>  

 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="fcd62-109">子元素</span><span class="sxs-lookup"><span data-stu-id="fcd62-109">Child Elements</span></span>  

 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="fcd62-110">父元素</span><span class="sxs-lookup"><span data-stu-id="fcd62-110">Parent Elements</span></span>  
  
|<span data-ttu-id="fcd62-111">元素</span><span class="sxs-lookup"><span data-stu-id="fcd62-111">Element</span></span>|<span data-ttu-id="fcd62-112">描述</span><span class="sxs-lookup"><span data-stu-id="fcd62-112">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="fcd62-113">包含命名实例的配置设置的集合 <xref:System.Runtime.Caching.MemoryCache> 。</span><span class="sxs-lookup"><span data-stu-id="fcd62-113">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fcd62-114">备注</span><span class="sxs-lookup"><span data-stu-id="fcd62-114">Remarks</span></span>  

 <span data-ttu-id="fcd62-115">`remove`元素 `namedCache` 从内存缓存的命名缓存集合中删除一个条目。</span><span class="sxs-lookup"><span data-stu-id="fcd62-115">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcd62-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="fcd62-116">See also</span></span>

- [<span data-ttu-id="fcd62-117">\<namedCaches> 元素 (缓存设置) </span><span class="sxs-lookup"><span data-stu-id="fcd62-117">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)

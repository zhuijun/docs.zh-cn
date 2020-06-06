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
# <a name="clear-element-for-namedcaches"></a>\<namedCaches> 的 \<clear> 元素
清除 `namedCache` 内存缓存的集合中的所有项 `namedCaches` 。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a>语法  
  
```xml  
<namedCaches>  
    <clear name="Default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>类型  
 `Type`  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
 `None`  
  
### <a name="child-elements"></a>子元素  
 `None`  
  
### <a name="parent-elements"></a>父元素  
  
|元素|说明|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|包含命名实例的配置设置的集合 <xref:System.Runtime.Caching.MemoryCache> 。|  
  
## <a name="remarks"></a>注解  
 `clear`元素清除 `namedCache` 内存缓存的命名缓存集合中的所有项。 在 `clear` 使用 `add` 元素添加新的命名缓存条目之前，可以使用元素，以便确定集合中没有其他命名缓存。  
  
## <a name="see-also"></a>另请参阅

- [\<namedCaches>元素（缓存设置）](namedcaches-element-cache-settings.md)

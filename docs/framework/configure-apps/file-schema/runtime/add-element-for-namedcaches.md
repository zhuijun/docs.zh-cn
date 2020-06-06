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
# <a name="add-element-for-namedcaches"></a>\<namedCaches> 的 \<add> 元素
向 `namedCache` 内存缓存的集合中添加项 `namedCaches` 。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a>语法  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>类型  
 `None`  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|属性|说明|  
|-|-|  
|`CacheMemoryLimitMegabytes`|一个整数值，指定的实例可以增长到的最大允许大小（以 mb <xref:System.Runtime.Caching.MemoryCache> 为单位）。 默认值为0，这意味着 <xref:System.Runtime.Caching.MemoryCache> 默认情况下使用类的自动调整试探法。|  
|`Name`|缓存的名称。|  
|`PhysicalMemoryLimitPercentage`|一个介于0到100之间的整数值，用于指定缓存可使用的实际安装计算机内存的最大百分比。 默认值为0，这意味着 <xref:System.Runtime.Caching.MemoryCache> 默认情况下使用类的自动调整试探法。|  
|`PollingInterval`|一个时间间隔的值，在该时间间隔之后，缓存实现会将当前内存负载与为缓存实例设置的基于绝对值和百分比的内存限制进行比较。 此值以 "HH： MM： SS" 格式输入。|  
  
### <a name="child-elements"></a>子元素  
 `None`  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|包含命名实例的配置设置的集合 <xref:System.Runtime.Caching.MemoryCache> 。|  
  
## <a name="remarks"></a>注解  
 `add`元素向内存缓存的集合中添加项 `namedCaches` 。 您可以在使用元素之前使用[clear](clear-element-for-namedcaches.md)元素 `add` ，以确保集合中没有其他命名缓存。 此元素可在 machine.config 文件和 web.config 文件中使用。  
  
## <a name="example"></a>示例  
 下面的示例演示如何为内存缓存的集合定义默认项的设置 `namedCache` `namedCaches` 。  
  
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
  
## <a name="see-also"></a>另请参阅

- [\<namedCaches>元素（缓存设置）](namedcaches-element-cache-settings.md)

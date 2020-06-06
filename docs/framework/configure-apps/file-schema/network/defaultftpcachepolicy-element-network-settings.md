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
# <a name="defaultftpcachepolicy-element-network-settings"></a>\<defaultFtpCachePolicy> 元素（网络设置）
介绍 FTP 缓存是否处于活动状态，并描述默认缓存策略。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultFtpCachePolicy>**

## <a name="syntax"></a>语法  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|属性|说明|  
|---------------|-----------------|  
|`policyLevel`|指定 FTP 缓存策略。 默认值为 `Default`。|  
  
## <a name="policylevel-attribute"></a>policyLevel 特性  
  
|值|说明|  
|-----------|-----------------|  
|`Default`|如果资源是最新的，则返回缓存的资源，内容长度准确，并且存在过期、修改和内容长度属性。|  
|`BypassCache`|从服务器返回资源。|  
|`CacheOnly`|如果内容长度存在并且与条目大小匹配，则返回缓存的资源。|  
|`CacheIfAvailable`|如果提供了内容长度并与条目大小匹配，则返回缓存的资源;否则，将从服务器下载资源，并将其返回给调用方。|  
|`Revalidate`|如果缓存资源的时间戳与服务器上资源的时间戳相同，则返回缓存的资源;否则，将从服务器下载资源，并将其存储在缓存中，并将其返回给调用方。|  
|`Reload`|从服务器下载资源，将其存储在缓存中，并将资源返回给调用方。|  
|`NoCacheNoStore`|如果缓存的资源存在，则将其删除。 从服务器下载资源，并将其返回给调用方。|  
|`Revalidate`|如果时间戳与服务器上的资源的时间戳相同，则使用资源的缓存副本满足请求；否则从服务器下载资源，将资源展示给调用方，然后再存储在缓存中。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[requestCaching](requestcaching-element-network-settings.md)|控制网络请求的缓存机制。|  
  
## <a name="remarks"></a>注解  
  
## <a name="example"></a>示例  
 下面的示例演示如何指定的 FTP 缓存策略 `NoCacheNoStore` 。  
  
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
  
## <a name="see-also"></a>另请参阅

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [网络设置架构](index.md)

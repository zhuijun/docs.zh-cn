---
title: <net.pipe>
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: dd984b2ab89060451b1b2d02c324e803766908ce
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397714"
---
# \<net.pipe>
指定命名管道激活服务的配置设置，命名管道激活服务将管理命名管道连接的生存期，并处理通过命名管道到达的激活请求。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<net.pipe>**  
  
## <a name="syntax"></a>语法  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <net.pipe maxPendingAccepts="Integer"
              maxPendingConnections="Integer"
              receiveTimeout="TimeSpan">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18" />
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19" />
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-20" />
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only) -->
        <add securityIdentifier="S-1-5-32-568" />
      </allowAccounts>
    </net.pipe>
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a>类型  
 `Type`  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|属性|说明|  
|---------------|-----------------|  
|`maxPendingAccepts`|一个整数，指定共享服务侦听终结点上的最大未完成并发接受线程数。 默认值为 2。|  
|`maxPendingConnections`|一个整数，指定可等待调度的最大连接数。 默认值为 100。|  
|`receiveTimeout`|<xref:System.TimeSpan>，它将为读取组帧数据并执行来自基础连接的连接调度指定超时值。 默认值为“00:00:10”|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|一个配置元素的集合，这些元素包含一个 `securityIdentifier` 属性，用于为承载 WCF 服务并被授予对共享服务的连接访问权限的进程指定用户帐户。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|包含侦听器进程 SMSvcHost.exe 的配置设置。|  
  
## <a name="see-also"></a>另请参阅

- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>

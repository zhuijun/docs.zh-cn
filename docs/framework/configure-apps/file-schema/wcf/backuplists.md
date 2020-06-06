---
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 5f2bb030d13389e15cb44f1ddff3b8168b4f2140
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850266"
---
# \<backupLists>
表示一个配置节，用于定义一组用来处理错误的备份服务。 每个子元素都是一个备份列表，用于枚举当无法到达主终结点时路由服务将使用的一组终结点。 如果列表中的第一个终结点关闭，则路由服务会自动故障转移到列表中的下一个终结点。  这样，可以方便地提高应用程序的可靠性，而不必告诉客户端应用程序应如何处理复杂模式或所有服务的部署位置。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupLists>**  
  
## <a name="syntax"></a>语法  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
 无。  
  
### <a name="child-elements"></a>子元素  
  
|元素|说明|  
|-------------|-----------------|  
|[\<filter>](filter.md)|包含当无法访问主终结点时路由服务将使用的终结点的列表。 .|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|说明|  
|-------------|-----------------|  
|[\<routing>](routing.md)|表示用于定义一组路由筛选器的配置节，这些筛选器确定计算传入消息时使用的 Windows Communication Foundation （WCF）的类型，以及用于 <xref:System.ServiceModel.Dispatcher.MessageFilter> 定义在筛选器匹配时要将消息发送到的目标终结点的路由表。|  
  
## <a name="see-also"></a>另请参阅

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>

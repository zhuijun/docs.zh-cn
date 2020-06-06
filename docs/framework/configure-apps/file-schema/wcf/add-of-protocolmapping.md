---
title: <add> 的 <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: 6197d01665d49a7c97ac9e44251abf15faf80a8f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850376"
---
# <a name="add-of-protocolmapping"></a>\<add> 的 \<protocolMapping>
表示传输协议方案（例如，http、net.tcp、net.pipe 等）与 Windows Communication Foundation （WCF）绑定之间的默认协议映射。 在运行时创建默认终结点时，WCF 会查看已配置的映射，并决定要将哪个绑定用于特定的地址。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<protocolMapping>**](protocolmapping.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a>语法  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|元素|说明|  
|-------------|-----------------|  
|binding|一个字符串，指定在创建默认终结点时要用于终结点的绑定类型。|  
|bindingConfiguration|一个字符串，指定要引用的绑定配置节的名称。|  
|scheme|要用于默认终结点的传输协议方案。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|说明|  
|-------------|-----------------|  
|[\<protocolMapping>](protocolmapping.md)|表示用于定义传输协议方案（例如，http、net.tcp、net.pipe 等）与 Windows Communication Foundation （WCF）绑定之间的默认协议映射的配置节。|  
  
## <a name="example"></a>示例  
 下面的配置示例演示 machine.config 文件中的默认协议映射。 您可以通过修改 machine.config 文件在计算机级别重写此默认映射。 或者，如果您只希望在应用程序范围内重写此映射，则可以在应用程序配置文件中重写此节，并为单独的协议方案更改映射。  
  
```xml  
<protocolMapping>
  <add scheme="http"
       binding="basicHttpBinding" />
  <add scheme="net.tcp"
       binding="netTcpBinding" />
  <add scheme="net.pipe"
       binding="netNamedPipeBinding" />
  <add scheme="net.msmq"
       binding="netMsmqBinding" />
</protocolMapping>
```  
  
## <a name="see-also"></a>另请参阅

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>

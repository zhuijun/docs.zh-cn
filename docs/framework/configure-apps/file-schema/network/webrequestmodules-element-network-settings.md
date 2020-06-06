---
title: <webRequestModules> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
ms.openlocfilehash: 7f2805283f89e6165d336b3e593d34054e02115d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154538"
---
# <a name="webrequestmodules-element-network-settings"></a>\<webRequestModules> 元素（网络设置）
指定用于从网络主机请求信息的模块。  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules>  
  
## <a name="syntax"></a>语法  
  
```xml  
<webRequestModules>
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
 无。  
  
### <a name="child-elements"></a>子元素  
  
|**元素**|**描述**|  
|-----------------|---------------------|  
|[add](add-element-for-webrequestmodules-network-settings.md)|向应用程序添加自定义 Web 请求模块。|  
|[清除](clear-element-for-webrequestmodules-network-settings.md)|从应用程序中删除所有已注册的 Web 请求模块。|  
|[删除](remove-element-for-webrequestmodules-network-settings.md)|从应用程序中移除自定义 Web 请求模块。|  
  
### <a name="parent-elements"></a>父元素  
  
|**元素**|**描述**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|包含指定 .NET Framework 如何连接到网络的设置。|  
  
## <a name="remarks"></a>注解  
 此 `webRequestModules` 元素注册 <xref:System.Net.WebRequest> 类的子代，以处理向网络主机发出的信息请求。 Web 请求模块必须实现 <xref:System.Net.IWebRequestCreate> 接口。  
  
 .NET Framework 包含以、和开头的 Uri 的 Web 请求 `http://` 模块 `https://` `file://` 。 只能通过在配置文件中注册自定义模块来重写默认模块。  
  
## <a name="configuration-files"></a>配置文件  
 此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。  
  
## <a name="example"></a>示例  
 下面的示例将注册默认的 HTTP 模块。 应将版本和 PublicKeyToken 的值替换为指定模块的正确值。  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Net.WebRequest>
- <xref:System.Net.IWebRequestCreate>
- [网络设置架构](index.md)

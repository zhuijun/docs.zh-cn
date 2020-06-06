---
title: <sharedListeners> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sharedListeners
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners
helpviewer_keywords:
- <sharedListeners> element
- listeners
- shared listeners
- trace listeners, <sharedListeners> element
- sharedListeners element
ms.assetid: de200534-19dd-4156-86cf-c50521802c4c
ms.openlocfilehash: 69f15cc9583b397017ac30a0c567914495867c18
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153316"
---
# <a name="sharedlisteners-element"></a>\<sharedListeners> 元素
包含任何源或跟踪元素可以引用的侦听器。  默认情况下，这些侦听器不会接收任何跟踪，而且不能在运行时检索这些侦听器。 可以按名称将标识为共享侦听器的侦听器添加到源或跟踪。  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<sharedListeners>**  
  
## <a name="syntax"></a>语法  
  
```xml  
<sharedListeners>
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
 无。  
  
### <a name="child-elements"></a>子元素  
  
|元素|说明|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-trace.md)|将侦听器添加到 `sharedListeners` 集合中。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|说明|  
|-------------|-----------------|  
|`Configuration`|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
|`system.diagnostics`|为 ASP.NET 配置节指定根元素。|  
  
## <a name="remarks"></a>注解  
 将侦听器添加到共享侦听器集合并不会使其成为活动侦听器。 还必须将其添加到跟踪源或跟踪，方法是将其添加到跟踪 `Listeners` 元素的集合。 .NET Framework 中的侦听器类派生自 <xref:System.Diagnostics.TraceListener> 类。  
  
 此元素可在计算机配置文件（Machine.config）和应用程序配置文件中使用。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用 `<sharedListeners>` 元素将侦听器添加 `console` 到 `Listeners` <xref:System.Diagnostics.TraceSource> 和类的集合 <xref:System.Diagnostics.Trace> 。 控制台跟踪侦听器通过对或的调用将跟踪信息写入控制台 <xref:System.Diagnostics.TraceSource> <xref:System.Diagnostics.Trace> 。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sharedListeners>  
      <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"  
          initializeData="Warning" />  
      </add>  
    </sharedListeners>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"  >  
        <listeners>  
          <add name="console" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Verbose"/>  
    </switches>  
    <trace>  
      <listeners>  
        <add name="console" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Diagnostics.TraceListener>
- [跟踪和调试设置架构](index.md)
- [跟踪侦听器](../../../debug-trace-profile/trace-listeners.md)

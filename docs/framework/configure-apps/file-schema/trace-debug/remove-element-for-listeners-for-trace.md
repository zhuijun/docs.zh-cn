---
title: <remove>的元素 <listeners><trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
ms.openlocfilehash: f06973ec30d5061e4a200d6bf7e68adcf6302018
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088837"
---
# <a name="remove-element-for-listeners-for-trace"></a>\<remove>的元素 \<listeners>\<trace>
从**侦听器**集合中删除侦听器。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a>语法  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|属性|说明|  
|---------------|-----------------|  
|**name**|必需的特性。<br /><br /> 要从**侦听器**集合中删除的侦听器的名称。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
|`listeners`|指定用于收集、存储和路由消息的侦听器。 侦听器将跟踪输出定向到适当的目标。|  
|`system.diagnostics`|指定用于收集、存储和路由消息的跟踪侦听器以及对跟踪开关设置的级别。|  
|`trace`|配置 ASP.NET 跟踪服务。|  
  
## <a name="remarks"></a>注解  
  
> [!NOTE]
> <xref:System.Diagnostics.DefaultTraceListener>从集合中移除会 `Listeners` 改变 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 、 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType> 、 <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> 和方法的行为 <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> 。 `Assert` `Fail` 通常，调用或方法会导致显示消息框，但是，如果不 <xref:System.Diagnostics.DefaultTraceListener> 在集合中，则不会显示消息框 `Listeners` 。  
  
## <a name="example"></a>示例  
 下面的示例演示如何从跟踪**侦听器**集合中删除默认的跟踪侦听器。  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <remove name="Default" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [跟踪和调试设置架构](index.md)

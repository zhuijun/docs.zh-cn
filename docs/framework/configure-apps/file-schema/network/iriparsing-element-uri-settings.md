---
title: <iriParsing> 元素（Uri 设置）
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: fd617d1b4ac8e532c6f9aeaa01465e9866b059e9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "71698095"
---
# <a name="iriparsing-element-uri-settings"></a>\<iriParsing> 元素（Uri 设置）
指定是否对 <xref:System.Uri> 应用国际资源标识符 (IRI) 分析以及是否应该应用 IRI 分析规则。  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<iriParsing>**  
  
## <a name="syntax"></a>语法  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|**元素**|**描述**|  
|-----------------|---------------------|  
|`enabled`|指定是否启用 IRI 分析。 默认值为 `false`。|  
  
### <a name="child-elements"></a>子元素  
 无  
  
### <a name="parent-elements"></a>父元素  
  
|**元素**|**描述**|  
|-----------------|---------------------|  
|[uri](uri-element-uri-settings.md)|包含指定 .NET Framework 如何处理使用统一资源标识符（Uri）表示的 web 地址的设置。|  
  
## <a name="remarks"></a>注解  
 已 <xref:System.Uri> 在 .NET Framework 3.5 中扩展了现有的类。 3.0 SP1 和 2.0 SP1，提供对国际资源标识符（IRI）和国际化域名（IDN）的支持。 当前用户将看不到 .NET Framework 2.0 行为中的任何更改，除非它们专门启用 IRI 和 IDN 支持。 这确保了 NET Framework 以前版本的应用程序兼容性。  
  
 若要启用对 IRI 的支持，需要以下两项更改：  
  
1. 将以下行添加到 .NET Framework 2.0 目录下的 machine.config 文件中。  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. 指定是否应该应用 IRI 分析规则。 这可以在 machine.config 或应用配置文件中完成。  
  
 启用 IRI 分析（启用 Iriparsing> = `true` ）将根据 RFC 3987 中的最新 IRI 规则执行规范化和字符检查。 默认值为 `false` ，将根据 rfc 2396 和 rfc 3986 （针对 IPv6 文本）执行规范化和字符检查。  
  
### <a name="configuration-files"></a>配置文件  
 此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>说明  
 下面的示例演示类使用的配置， <xref:System.Uri> 以支持 IRI 分析和 IDN 名称。  
  
### <a name="code"></a>代码  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [网络设置架构](index.md)

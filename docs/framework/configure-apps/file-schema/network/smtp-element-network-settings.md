---
title: <smtp> 元素（网络设置）
description: "\" <smtp> 网络设置\" 元素在 .NET Framework 中配置发送电子邮件选项的传递格式、传递方法和发件人地址。"
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
ms.openlocfilehash: b30b82922a69ea660f4c4abfd808e89fa9945183
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504506"
---
# <a name="smtp-element-network-settings"></a>\<smtp> 元素（网络设置）
配置发送电子邮件的传递格式、传递方法和发件人地址。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<smtp>**
  
## <a name="syntax"></a>语法  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|属性|说明|  
|---------------|-----------------|  
|`deliveryFormat`|指定传出电子邮件的传递格式。 可接受的值为 SevenBit 和 International。|  
|`deliveryMethod`|指定电子邮件的传递方法。 可接受的值为 Network、PickupDirectoryFromIis 和 SpecifiedPickupDirectory。|  
|`from`|指定传出电子邮件的发件人地址。|  
  
### <a name="child-elements"></a>子元素  
  
|属性|说明|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|配置简单邮件传输协议（SMTP）服务器的本地目录。|  
|`network`|配置外部 SMTP 服务器的网络选项。|  
  
### <a name="parent-elements"></a>父元素  
  
|**元素**|**说明**|  
|-----------------|---------------------|  
|[\<mailSettings>元素（网络设置）](mailsettings-element-network-settings.md)|配置邮件发送选项。|  
  
## <a name="example"></a>示例  
 下面的示例指定了使用默认网络凭据发送电子邮件所需的适当 SMTP 参数。  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network" deliveryFormat="SevenBit"  from="ben@contoso.com">  
        <network  
          host="localhost"  
          port="25"  
          defaultCredentials="true"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [网络设置架构](index.md)

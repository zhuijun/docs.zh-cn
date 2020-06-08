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
# <a name="smtp-element-network-settings"></a><span data-ttu-id="adfd4-103">\<smtp> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="adfd4-103">\<smtp> Element (Network Settings)</span></span>
<span data-ttu-id="adfd4-104">配置发送电子邮件的传递格式、传递方法和发件人地址。</span><span class="sxs-lookup"><span data-stu-id="adfd4-104">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<smtp>**
  
## <a name="syntax"></a><span data-ttu-id="adfd4-105">语法</span><span class="sxs-lookup"><span data-stu-id="adfd4-105">Syntax</span></span>  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="adfd4-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="adfd4-106">Attributes and Elements</span></span>  
 <span data-ttu-id="adfd4-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="adfd4-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="adfd4-108">特性</span><span class="sxs-lookup"><span data-stu-id="adfd4-108">Attributes</span></span>  
  
|<span data-ttu-id="adfd4-109">属性</span><span class="sxs-lookup"><span data-stu-id="adfd4-109">Attribute</span></span>|<span data-ttu-id="adfd4-110">说明</span><span class="sxs-lookup"><span data-stu-id="adfd4-110">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="adfd4-111">指定传出电子邮件的传递格式。</span><span class="sxs-lookup"><span data-stu-id="adfd4-111">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="adfd4-112">可接受的值为 SevenBit 和 International。</span><span class="sxs-lookup"><span data-stu-id="adfd4-112">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="adfd4-113">指定电子邮件的传递方法。</span><span class="sxs-lookup"><span data-stu-id="adfd4-113">Specifies the delivery method for emails.</span></span> <span data-ttu-id="adfd4-114">可接受的值为 Network、PickupDirectoryFromIis 和 SpecifiedPickupDirectory。</span><span class="sxs-lookup"><span data-stu-id="adfd4-114">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="adfd4-115">指定传出电子邮件的发件人地址。</span><span class="sxs-lookup"><span data-stu-id="adfd4-115">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="adfd4-116">子元素</span><span class="sxs-lookup"><span data-stu-id="adfd4-116">Child Elements</span></span>  
  
|<span data-ttu-id="adfd4-117">属性</span><span class="sxs-lookup"><span data-stu-id="adfd4-117">Attribute</span></span>|<span data-ttu-id="adfd4-118">说明</span><span class="sxs-lookup"><span data-stu-id="adfd4-118">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="adfd4-119">配置简单邮件传输协议（SMTP）服务器的本地目录。</span><span class="sxs-lookup"><span data-stu-id="adfd4-119">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="adfd4-120">配置外部 SMTP 服务器的网络选项。</span><span class="sxs-lookup"><span data-stu-id="adfd4-120">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="adfd4-121">父元素</span><span class="sxs-lookup"><span data-stu-id="adfd4-121">Parent Elements</span></span>  
  
|<span data-ttu-id="adfd4-122">**元素**</span><span class="sxs-lookup"><span data-stu-id="adfd4-122">**Element**</span></span>|<span data-ttu-id="adfd4-123">**说明**</span><span class="sxs-lookup"><span data-stu-id="adfd4-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="adfd4-124">\<mailSettings>元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="adfd4-124">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="adfd4-125">配置邮件发送选项。</span><span class="sxs-lookup"><span data-stu-id="adfd4-125">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="adfd4-126">示例</span><span class="sxs-lookup"><span data-stu-id="adfd4-126">Example</span></span>  
 <span data-ttu-id="adfd4-127">下面的示例指定了使用默认网络凭据发送电子邮件所需的适当 SMTP 参数。</span><span class="sxs-lookup"><span data-stu-id="adfd4-127">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="adfd4-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="adfd4-128">See also</span></span>

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [<span data-ttu-id="adfd4-129">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="adfd4-129">Network Settings Schema</span></span>](index.md)

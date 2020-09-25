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
ms.openlocfilehash: 58f496b4a07f7d5531df897dd54bb6176111f1c4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178315"
---
# <a name="smtp-element-network-settings"></a><span data-ttu-id="28436-103">\<smtp> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="28436-103">\<smtp> Element (Network Settings)</span></span>

<span data-ttu-id="28436-104">配置发送电子邮件的传递格式、传递方法和发件人地址。</span><span class="sxs-lookup"><span data-stu-id="28436-104">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<smtp>**
  
## <a name="syntax"></a><span data-ttu-id="28436-105">语法</span><span class="sxs-lookup"><span data-stu-id="28436-105">Syntax</span></span>  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28436-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="28436-106">Attributes and Elements</span></span>  

 <span data-ttu-id="28436-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="28436-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28436-108">特性</span><span class="sxs-lookup"><span data-stu-id="28436-108">Attributes</span></span>  
  
|<span data-ttu-id="28436-109">属性</span><span class="sxs-lookup"><span data-stu-id="28436-109">Attribute</span></span>|<span data-ttu-id="28436-110">描述</span><span class="sxs-lookup"><span data-stu-id="28436-110">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="28436-111">指定传出电子邮件的传递格式。</span><span class="sxs-lookup"><span data-stu-id="28436-111">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="28436-112">可接受的值为 SevenBit 和 International。</span><span class="sxs-lookup"><span data-stu-id="28436-112">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="28436-113">指定电子邮件的传递方法。</span><span class="sxs-lookup"><span data-stu-id="28436-113">Specifies the delivery method for emails.</span></span> <span data-ttu-id="28436-114">可接受的值为 Network、PickupDirectoryFromIis 和 SpecifiedPickupDirectory。</span><span class="sxs-lookup"><span data-stu-id="28436-114">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="28436-115">指定传出电子邮件的发件人地址。</span><span class="sxs-lookup"><span data-stu-id="28436-115">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28436-116">子元素</span><span class="sxs-lookup"><span data-stu-id="28436-116">Child Elements</span></span>  
  
|<span data-ttu-id="28436-117">Attribute</span><span class="sxs-lookup"><span data-stu-id="28436-117">Attribute</span></span>|<span data-ttu-id="28436-118">描述</span><span class="sxs-lookup"><span data-stu-id="28436-118">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="28436-119"> (SMTP) 服务器配置简单邮件传输协议的本地目录。</span><span class="sxs-lookup"><span data-stu-id="28436-119">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="28436-120">配置外部 SMTP 服务器的网络选项。</span><span class="sxs-lookup"><span data-stu-id="28436-120">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="28436-121">父元素</span><span class="sxs-lookup"><span data-stu-id="28436-121">Parent Elements</span></span>  
  
|<span data-ttu-id="28436-122">**元素**</span><span class="sxs-lookup"><span data-stu-id="28436-122">**Element**</span></span>|<span data-ttu-id="28436-123">**说明**</span><span class="sxs-lookup"><span data-stu-id="28436-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="28436-124">\<mailSettings> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="28436-124">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="28436-125">配置邮件发送选项。</span><span class="sxs-lookup"><span data-stu-id="28436-125">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="28436-126">示例</span><span class="sxs-lookup"><span data-stu-id="28436-126">Example</span></span>  

 <span data-ttu-id="28436-127">下面的示例指定了使用默认网络凭据发送电子邮件所需的适当 SMTP 参数。</span><span class="sxs-lookup"><span data-stu-id="28436-127">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="28436-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="28436-128">See also</span></span>

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [<span data-ttu-id="28436-129">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="28436-129">Network Settings Schema</span></span>](index.md)

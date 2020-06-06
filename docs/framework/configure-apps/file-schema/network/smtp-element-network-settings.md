---
title: <smtp> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
ms.openlocfilehash: 625c3cb82a8659c742b540724e5cf31be65a705e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089099"
---
# <a name="smtp-element-network-settings"></a><span data-ttu-id="29304-102">\<smtp> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="29304-102">\<smtp> Element (Network Settings)</span></span>
<span data-ttu-id="29304-103">配置发送电子邮件的传递格式、传递方法和发件人地址。</span><span class="sxs-lookup"><span data-stu-id="29304-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<smtp>**
  
## <a name="syntax"></a><span data-ttu-id="29304-104">语法</span><span class="sxs-lookup"><span data-stu-id="29304-104">Syntax</span></span>  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29304-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="29304-105">Attributes and Elements</span></span>  
 <span data-ttu-id="29304-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="29304-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29304-107">特性</span><span class="sxs-lookup"><span data-stu-id="29304-107">Attributes</span></span>  
  
|<span data-ttu-id="29304-108">属性</span><span class="sxs-lookup"><span data-stu-id="29304-108">Attribute</span></span>|<span data-ttu-id="29304-109">说明</span><span class="sxs-lookup"><span data-stu-id="29304-109">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="29304-110">指定传出电子邮件的传递格式。</span><span class="sxs-lookup"><span data-stu-id="29304-110">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="29304-111">可接受的值为 SevenBit 和 International。</span><span class="sxs-lookup"><span data-stu-id="29304-111">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="29304-112">指定电子邮件的传递方法。</span><span class="sxs-lookup"><span data-stu-id="29304-112">Specifies the delivery method for emails.</span></span> <span data-ttu-id="29304-113">可接受的值为 Network、PickupDirectoryFromIis 和 SpecifiedPickupDirectory。</span><span class="sxs-lookup"><span data-stu-id="29304-113">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="29304-114">指定传出电子邮件的发件人地址。</span><span class="sxs-lookup"><span data-stu-id="29304-114">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29304-115">子元素</span><span class="sxs-lookup"><span data-stu-id="29304-115">Child Elements</span></span>  
  
|<span data-ttu-id="29304-116">属性</span><span class="sxs-lookup"><span data-stu-id="29304-116">Attribute</span></span>|<span data-ttu-id="29304-117">说明</span><span class="sxs-lookup"><span data-stu-id="29304-117">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="29304-118">配置简单邮件传输协议（SMTP）服务器的本地目录。</span><span class="sxs-lookup"><span data-stu-id="29304-118">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="29304-119">配置外部 SMTP 服务器的网络选项。</span><span class="sxs-lookup"><span data-stu-id="29304-119">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="29304-120">父元素</span><span class="sxs-lookup"><span data-stu-id="29304-120">Parent Elements</span></span>  
  
|<span data-ttu-id="29304-121">**元素**</span><span class="sxs-lookup"><span data-stu-id="29304-121">**Element**</span></span>|<span data-ttu-id="29304-122">**描述**</span><span class="sxs-lookup"><span data-stu-id="29304-122">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="29304-123">\<mailSettings>元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="29304-123">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="29304-124">配置邮件发送选项。</span><span class="sxs-lookup"><span data-stu-id="29304-124">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="29304-125">示例</span><span class="sxs-lookup"><span data-stu-id="29304-125">Example</span></span>  
 <span data-ttu-id="29304-126">下面的示例指定了使用默认网络凭据发送电子邮件所需的适当 SMTP 参数。</span><span class="sxs-lookup"><span data-stu-id="29304-126">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="29304-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="29304-127">See also</span></span>

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [<span data-ttu-id="29304-128">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="29304-128">Network Settings Schema</span></span>](index.md)

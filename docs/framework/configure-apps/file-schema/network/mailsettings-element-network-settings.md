---
title: <mailSettings> 元素（网络设置）
description: <mailSettings>网络设置元素在 .NET Framework 中配置邮件发送选项。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
ms.openlocfilehash: ce7b8564e4ee5ea73d42259612c077420d36645b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504558"
---
# <a name="mailsettings-element-network-settings"></a><span data-ttu-id="fdaf1-103">\<mailSettings> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="fdaf1-103">\<mailSettings> Element (Network Settings)</span></span>
<span data-ttu-id="fdaf1-104">配置邮件发送选项。</span><span class="sxs-lookup"><span data-stu-id="fdaf1-104">Configures mail sending options.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<mailSettings>**

## <a name="syntax"></a><span data-ttu-id="fdaf1-105">语法</span><span class="sxs-lookup"><span data-stu-id="fdaf1-105">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fdaf1-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="fdaf1-106">Attributes and Elements</span></span>  
 <span data-ttu-id="fdaf1-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="fdaf1-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fdaf1-108">特性</span><span class="sxs-lookup"><span data-stu-id="fdaf1-108">Attributes</span></span>  
 <span data-ttu-id="fdaf1-109">无。</span><span class="sxs-lookup"><span data-stu-id="fdaf1-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fdaf1-110">子元素</span><span class="sxs-lookup"><span data-stu-id="fdaf1-110">Child Elements</span></span>  
  
|<span data-ttu-id="fdaf1-111">属性</span><span class="sxs-lookup"><span data-stu-id="fdaf1-111">Attribute</span></span>|<span data-ttu-id="fdaf1-112">说明</span><span class="sxs-lookup"><span data-stu-id="fdaf1-112">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="fdaf1-113">\<smtp>元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="fdaf1-113">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="fdaf1-114">配置简单邮件传输协议选项。</span><span class="sxs-lookup"><span data-stu-id="fdaf1-114">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fdaf1-115">父元素</span><span class="sxs-lookup"><span data-stu-id="fdaf1-115">Parent Elements</span></span>  
  
|<span data-ttu-id="fdaf1-116">**元素**</span><span class="sxs-lookup"><span data-stu-id="fdaf1-116">**Element**</span></span>|<span data-ttu-id="fdaf1-117">**说明**</span><span class="sxs-lookup"><span data-stu-id="fdaf1-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="fdaf1-118">\<system.Net>元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="fdaf1-118">\<system.Net> Element (Network Settings)</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="fdaf1-119">包含指定 .NET Framework 如何连接到网络的设置。</span><span class="sxs-lookup"><span data-stu-id="fdaf1-119">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fdaf1-120">示例</span><span class="sxs-lookup"><span data-stu-id="fdaf1-120">Example</span></span>  
 <span data-ttu-id="fdaf1-121">下面的示例指定了使用默认网络凭据发送电子邮件所需的适当 SMTP 参数。</span><span class="sxs-lookup"><span data-stu-id="fdaf1-121">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network">  
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
  
## <a name="see-also"></a><span data-ttu-id="fdaf1-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fdaf1-122">See also</span></span>

- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="fdaf1-123">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="fdaf1-123">Network Settings Schema</span></span>](index.md)

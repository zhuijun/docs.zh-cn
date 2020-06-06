---
title: <mailSettings> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
ms.openlocfilehash: 4e8bf23ce39edadf80f019315c690b597b3d7361
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089236"
---
# <a name="mailsettings-element-network-settings"></a><span data-ttu-id="8e862-102">\<mailSettings> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="8e862-102">\<mailSettings> Element (Network Settings)</span></span>
<span data-ttu-id="8e862-103">配置邮件发送选项。</span><span class="sxs-lookup"><span data-stu-id="8e862-103">Configures mail sending options.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<mailSettings>**

## <a name="syntax"></a><span data-ttu-id="8e862-104">语法</span><span class="sxs-lookup"><span data-stu-id="8e862-104">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e862-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="8e862-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8e862-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="8e862-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e862-107">特性</span><span class="sxs-lookup"><span data-stu-id="8e862-107">Attributes</span></span>  
 <span data-ttu-id="8e862-108">无。</span><span class="sxs-lookup"><span data-stu-id="8e862-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8e862-109">子元素</span><span class="sxs-lookup"><span data-stu-id="8e862-109">Child Elements</span></span>  
  
|<span data-ttu-id="8e862-110">属性</span><span class="sxs-lookup"><span data-stu-id="8e862-110">Attribute</span></span>|<span data-ttu-id="8e862-111">说明</span><span class="sxs-lookup"><span data-stu-id="8e862-111">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="8e862-112">\<smtp>元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="8e862-112">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="8e862-113">配置简单邮件传输协议选项。</span><span class="sxs-lookup"><span data-stu-id="8e862-113">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8e862-114">父元素</span><span class="sxs-lookup"><span data-stu-id="8e862-114">Parent Elements</span></span>  
  
|<span data-ttu-id="8e862-115">**元素**</span><span class="sxs-lookup"><span data-stu-id="8e862-115">**Element**</span></span>|<span data-ttu-id="8e862-116">**描述**</span><span class="sxs-lookup"><span data-stu-id="8e862-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8e862-117">\<system.Net>元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="8e862-117">\<system.Net> Element (Network Settings)</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="8e862-118">包含指定 .NET Framework 如何连接到网络的设置。</span><span class="sxs-lookup"><span data-stu-id="8e862-118">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8e862-119">示例</span><span class="sxs-lookup"><span data-stu-id="8e862-119">Example</span></span>  
 <span data-ttu-id="8e862-120">下面的示例指定了使用默认网络凭据发送电子邮件所需的适当 SMTP 参数。</span><span class="sxs-lookup"><span data-stu-id="8e862-120">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8e862-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8e862-121">See also</span></span>

- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="8e862-122">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="8e862-122">Network Settings Schema</span></span>](index.md)

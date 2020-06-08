---
title: <specifiedPickupDirectory> 元素（网络设置）
description: <specifiedPickupDirectory>网络设置元素为 .NET Framework 中的 SMTP 服务器选项配置本地目录。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
ms.openlocfilehash: f0c4c1845e9542d0f3b836ff03f16bdf2979ebd8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504493"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="f3dc8-103">\<specifiedPickupDirectory> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="f3dc8-103">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="f3dc8-104">配置简单邮件传输协议（SMTP）服务器的本地目录。</span><span class="sxs-lookup"><span data-stu-id="f3dc8-104">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**  
  
## <a name="syntax"></a><span data-ttu-id="f3dc8-105">语法</span><span class="sxs-lookup"><span data-stu-id="f3dc8-105">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3dc8-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="f3dc8-106">Attributes and Elements</span></span>  
 <span data-ttu-id="f3dc8-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f3dc8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3dc8-108">特性</span><span class="sxs-lookup"><span data-stu-id="f3dc8-108">Attributes</span></span>  
  
|<span data-ttu-id="f3dc8-109">属性</span><span class="sxs-lookup"><span data-stu-id="f3dc8-109">Attribute</span></span>|<span data-ttu-id="f3dc8-110">说明</span><span class="sxs-lookup"><span data-stu-id="f3dc8-110">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="f3dc8-111">应用程序在其中保存电子邮件以供 SMTP 服务器稍后处理的目录。</span><span class="sxs-lookup"><span data-stu-id="f3dc8-111">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3dc8-112">子元素</span><span class="sxs-lookup"><span data-stu-id="f3dc8-112">Child Elements</span></span>  
 <span data-ttu-id="f3dc8-113">无。</span><span class="sxs-lookup"><span data-stu-id="f3dc8-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f3dc8-114">父元素</span><span class="sxs-lookup"><span data-stu-id="f3dc8-114">Parent Elements</span></span>  
  
|<span data-ttu-id="f3dc8-115">元素</span><span class="sxs-lookup"><span data-stu-id="f3dc8-115">Element</span></span>|<span data-ttu-id="f3dc8-116">描述</span><span class="sxs-lookup"><span data-stu-id="f3dc8-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3dc8-117">\<smtp>元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="f3dc8-117">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="f3dc8-118">配置简单邮件传输协议（SMTP）邮件发送选项。</span><span class="sxs-lookup"><span data-stu-id="f3dc8-118">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3dc8-119">注解</span><span class="sxs-lookup"><span data-stu-id="f3dc8-119">Remarks</span></span>  
 <span data-ttu-id="f3dc8-120">`specifiedPickupDirectory` 特性设置应用程序保存邮件以供 SMTP 服务器处理的目录。</span><span class="sxs-lookup"><span data-stu-id="f3dc8-120">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3dc8-121">示例</span><span class="sxs-lookup"><span data-stu-id="f3dc8-121">Example</span></span>  
 <span data-ttu-id="f3dc8-122">下面的示例将 c:\maildrop 指定为邮件分拣目录。</span><span class="sxs-lookup"><span data-stu-id="f3dc8-122">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="SpecifiedPickupDirectory">  
        <specifiedPickupDirectory  
          pickupDirectoryLocation="c:\maildrop"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f3dc8-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f3dc8-123">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="f3dc8-124">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="f3dc8-124">Network Settings Schema</span></span>](index.md)

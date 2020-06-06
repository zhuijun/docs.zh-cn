---
title: <specifiedPickupDirectory> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
ms.openlocfilehash: 4b0cbaf9a7bfe2a9b1610811f4201253d219a6b2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154603"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="980df-102">\<specifiedPickupDirectory> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="980df-102">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="980df-103">配置简单邮件传输协议（SMTP）服务器的本地目录。</span><span class="sxs-lookup"><span data-stu-id="980df-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**  
  
## <a name="syntax"></a><span data-ttu-id="980df-104">语法</span><span class="sxs-lookup"><span data-stu-id="980df-104">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="980df-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="980df-105">Attributes and Elements</span></span>  
 <span data-ttu-id="980df-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="980df-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="980df-107">特性</span><span class="sxs-lookup"><span data-stu-id="980df-107">Attributes</span></span>  
  
|<span data-ttu-id="980df-108">属性</span><span class="sxs-lookup"><span data-stu-id="980df-108">Attribute</span></span>|<span data-ttu-id="980df-109">说明</span><span class="sxs-lookup"><span data-stu-id="980df-109">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="980df-110">应用程序在其中保存电子邮件以供 SMTP 服务器稍后处理的目录。</span><span class="sxs-lookup"><span data-stu-id="980df-110">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="980df-111">子元素</span><span class="sxs-lookup"><span data-stu-id="980df-111">Child Elements</span></span>  
 <span data-ttu-id="980df-112">无。</span><span class="sxs-lookup"><span data-stu-id="980df-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="980df-113">父元素</span><span class="sxs-lookup"><span data-stu-id="980df-113">Parent Elements</span></span>  
  
|<span data-ttu-id="980df-114">元素</span><span class="sxs-lookup"><span data-stu-id="980df-114">Element</span></span>|<span data-ttu-id="980df-115">描述</span><span class="sxs-lookup"><span data-stu-id="980df-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="980df-116">\<smtp>元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="980df-116">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="980df-117">配置简单邮件传输协议（SMTP）邮件发送选项。</span><span class="sxs-lookup"><span data-stu-id="980df-117">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="980df-118">注解</span><span class="sxs-lookup"><span data-stu-id="980df-118">Remarks</span></span>  
 <span data-ttu-id="980df-119">`specifiedPickupDirectory` 特性设置应用程序保存邮件以供 SMTP 服务器处理的目录。</span><span class="sxs-lookup"><span data-stu-id="980df-119">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="980df-120">示例</span><span class="sxs-lookup"><span data-stu-id="980df-120">Example</span></span>  
 <span data-ttu-id="980df-121">下面的示例将 c:\maildrop 指定为邮件分拣目录。</span><span class="sxs-lookup"><span data-stu-id="980df-121">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="980df-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="980df-122">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="980df-123">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="980df-123">Network Settings Schema</span></span>](index.md)

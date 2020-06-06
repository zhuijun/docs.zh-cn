---
title: 网络设置架构
ms.date: 03/30/2017
helpviewer_keywords:
- elements [.NET Framework], network configuration elements
- sending data, network configuration elements
- receiving data, network configuration elements
- configuration settings [.NET Framework], networks
- Internet, network configuration elements
- network configuration elements
- network settings
- connections [.NET Framework], network configuration elements
- network resources, network configuration elements
ms.assetid: f1de5a0f-76c5-4833-819f-5222b8146340
ms.openlocfilehash: 5e3bd1b1734fc7fba50b72785531a8b001d6d741
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "71698155"
---
# <a name="network-settings-schema"></a><span data-ttu-id="60ba5-102">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="60ba5-102">Network Settings Schema</span></span>
<span data-ttu-id="60ba5-103">网络设置指定 .NET Framework 与 Internet 的连接方式。</span><span class="sxs-lookup"><span data-stu-id="60ba5-103">Network settings specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="60ba5-104">\<system.net>设置指定 .NET Framework 如何连接到网络。</span><span class="sxs-lookup"><span data-stu-id="60ba5-104">The \<system.net> settings specify how the .NET Framework connects to the network.</span></span> <span data-ttu-id="60ba5-105">下表描述了[ \<system.Net> 元素（网络设置）](system-net-element-network-settings.md)下每个子配置元素的功能。</span><span class="sxs-lookup"><span data-stu-id="60ba5-105">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="60ba5-106">元素</span><span class="sxs-lookup"><span data-stu-id="60ba5-106">Element</span></span>|<span data-ttu-id="60ba5-107">说明</span><span class="sxs-lookup"><span data-stu-id="60ba5-107">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60ba5-108">\<authenticationModules>元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="60ba5-108">\<authenticationModules> Element (Network Settings)</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="60ba5-109">指定用于验证 Internet 请求的模块。</span><span class="sxs-lookup"><span data-stu-id="60ba5-109">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="60ba5-110">\<connectionManagement>元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="60ba5-110">\<connectionManagement> Element (Network Settings)</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="60ba5-111">指定到 Internet 主机的最大连接数。</span><span class="sxs-lookup"><span data-stu-id="60ba5-111">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="60ba5-112">\<defaultProxy>元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="60ba5-112">\<defaultProxy> Element (Network Settings)</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="60ba5-113">指定用于路由到 Internet 的 HTTP 请求的代理服务器。</span><span class="sxs-lookup"><span data-stu-id="60ba5-113">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="60ba5-114">\<mailSettings>元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="60ba5-114">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="60ba5-115">包含邮件发送选项的设置。</span><span class="sxs-lookup"><span data-stu-id="60ba5-115">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="60ba5-116">\<requestCaching>元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="60ba5-116">\<requestCaching> Element (Network Settings)</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="60ba5-117">控制网络请求的缓存机制。</span><span class="sxs-lookup"><span data-stu-id="60ba5-117">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="60ba5-118">\<webRequestModules>元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="60ba5-118">\<webRequestModules> Element (Network Settings)</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="60ba5-119">指定用于从 Internet 主机请求信息的模块。</span><span class="sxs-lookup"><span data-stu-id="60ba5-119">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
<span data-ttu-id="60ba5-120">\<uri>设置指定 .NET Framework 如何处理使用统一资源标识符（uri）表示的 web 地址。</span><span class="sxs-lookup"><span data-stu-id="60ba5-120">The \<uri> settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="60ba5-121">下表描述了[ \<uri> 元素（Uri 设置）](uri-element-uri-settings.md)下每个子配置元素的功能。</span><span class="sxs-lookup"><span data-stu-id="60ba5-121">The following table describes the function of each child configuration element under the [\<uri> Element (Uri Settings)](uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="60ba5-122">元素</span><span class="sxs-lookup"><span data-stu-id="60ba5-122">Element</span></span>|<span data-ttu-id="60ba5-123">说明</span><span class="sxs-lookup"><span data-stu-id="60ba5-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60ba5-124">\<idn>元素（Uri 设置）</span><span class="sxs-lookup"><span data-stu-id="60ba5-124">\<idn> Element (Uri Settings)</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="60ba5-125">指定是否对域名应用国际化域名 (IDN) 分析。</span><span class="sxs-lookup"><span data-stu-id="60ba5-125">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="60ba5-126">\<iriParsing>元素（Uri 设置）</span><span class="sxs-lookup"><span data-stu-id="60ba5-126">\<iriParsing> Element (Uri Settings)</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="60ba5-127">指定是否对 <xref:System.Uri> 应用国际资源标识符 (IRI) 分析以及是否应该应用 IRI 分析规则。</span><span class="sxs-lookup"><span data-stu-id="60ba5-127">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="60ba5-128">\<schemeSettings>元素（Uri 设置）</span><span class="sxs-lookup"><span data-stu-id="60ba5-128">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="60ba5-129">指定如何分析特定方案的 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="60ba5-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="60ba5-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="60ba5-130">See also</span></span>

- [<span data-ttu-id="60ba5-131">配置 Internet 应用程序</span><span class="sxs-lookup"><span data-stu-id="60ba5-131">Configuring Internet Applications</span></span>](../../../network-programming/configuring-internet-applications.md)
- [<span data-ttu-id="60ba5-132">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="60ba5-132">Configuration File Schema</span></span>](../index.md)

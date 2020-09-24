---
title: 网络设置架构
description: 了解用于指定 .NET Framework 如何连接到 Internet 并处理 Uri 的网络设置的架构。
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
ms.openlocfilehash: 8071fcfcdb16b6e71d8d7af05a704d8842b3e963
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158911"
---
# <a name="network-settings-schema"></a><span data-ttu-id="4fe1d-103">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="4fe1d-103">Network Settings Schema</span></span>

<span data-ttu-id="4fe1d-104">网络设置指定 .NET Framework 与 Internet 的连接方式。</span><span class="sxs-lookup"><span data-stu-id="4fe1d-104">Network settings specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="4fe1d-105">\<system.net>设置指定 .NET Framework 如何连接到网络。</span><span class="sxs-lookup"><span data-stu-id="4fe1d-105">The \<system.net> settings specify how the .NET Framework connects to the network.</span></span> <span data-ttu-id="4fe1d-106">下表描述了[ \<system.Net> 元素 (网络设置) ](system-net-element-network-settings.md)下的每个子配置元素的功能。</span><span class="sxs-lookup"><span data-stu-id="4fe1d-106">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="4fe1d-107">元素</span><span class="sxs-lookup"><span data-stu-id="4fe1d-107">Element</span></span>|<span data-ttu-id="4fe1d-108">描述</span><span class="sxs-lookup"><span data-stu-id="4fe1d-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4fe1d-109">\<authenticationModules> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="4fe1d-109">\<authenticationModules> Element (Network Settings)</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="4fe1d-110">指定用于验证 Internet 请求的模块。</span><span class="sxs-lookup"><span data-stu-id="4fe1d-110">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="4fe1d-111">\<connectionManagement> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="4fe1d-111">\<connectionManagement> Element (Network Settings)</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="4fe1d-112">指定到 Internet 主机的最大连接数。</span><span class="sxs-lookup"><span data-stu-id="4fe1d-112">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="4fe1d-113">\<defaultProxy> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="4fe1d-113">\<defaultProxy> Element (Network Settings)</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="4fe1d-114">指定用于路由到 Internet 的 HTTP 请求的代理服务器。</span><span class="sxs-lookup"><span data-stu-id="4fe1d-114">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="4fe1d-115">\<mailSettings> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="4fe1d-115">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="4fe1d-116">包含邮件发送选项的设置。</span><span class="sxs-lookup"><span data-stu-id="4fe1d-116">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="4fe1d-117">\<requestCaching> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="4fe1d-117">\<requestCaching> Element (Network Settings)</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="4fe1d-118">控制网络请求的缓存机制。</span><span class="sxs-lookup"><span data-stu-id="4fe1d-118">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="4fe1d-119">\<webRequestModules> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="4fe1d-119">\<webRequestModules> Element (Network Settings)</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="4fe1d-120">指定用于从 Internet 主机请求信息的模块。</span><span class="sxs-lookup"><span data-stu-id="4fe1d-120">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
<span data-ttu-id="4fe1d-121">这些 \<uri> 设置指定 .NET Framework 如何处理使用统一资源标识符 (uri) 表示的 web 地址。</span><span class="sxs-lookup"><span data-stu-id="4fe1d-121">The \<uri> settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="4fe1d-122">下表描述了元素下的每个子配置元素的功能， [ \<uri> (Uri 设置) ](uri-element-uri-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="4fe1d-122">The following table describes the function of each child configuration element under the [\<uri> Element (Uri Settings)](uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="4fe1d-123">元素</span><span class="sxs-lookup"><span data-stu-id="4fe1d-123">Element</span></span>|<span data-ttu-id="4fe1d-124">描述</span><span class="sxs-lookup"><span data-stu-id="4fe1d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4fe1d-125">\<idn> 元素 (Uri 设置) </span><span class="sxs-lookup"><span data-stu-id="4fe1d-125">\<idn> Element (Uri Settings)</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="4fe1d-126">指定是否对域名应用国际化域名 (IDN) 分析。</span><span class="sxs-lookup"><span data-stu-id="4fe1d-126">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="4fe1d-127">\<iriParsing> 元素 (Uri 设置) </span><span class="sxs-lookup"><span data-stu-id="4fe1d-127">\<iriParsing> Element (Uri Settings)</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="4fe1d-128">指定是否对 <xref:System.Uri> 应用国际资源标识符 (IRI) 分析以及是否应该应用 IRI 分析规则。</span><span class="sxs-lookup"><span data-stu-id="4fe1d-128">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="4fe1d-129">\<schemeSettings> 元素 (Uri 设置) </span><span class="sxs-lookup"><span data-stu-id="4fe1d-129">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="4fe1d-130">指定如何分析特定方案的 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="4fe1d-130">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4fe1d-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="4fe1d-131">See also</span></span>

- [<span data-ttu-id="4fe1d-132">配置 Internet 应用程序</span><span class="sxs-lookup"><span data-stu-id="4fe1d-132">Configuring Internet Applications</span></span>](../../../network-programming/configuring-internet-applications.md)
- [<span data-ttu-id="4fe1d-133">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="4fe1d-133">Configuration File Schema</span></span>](../index.md)

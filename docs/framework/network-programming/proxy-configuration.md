---
title: 代理配置
description: 了解如何配置自适应和静态代理服务器。 代理配置控制代理服务器如何处理客户端对资源的请求。
ms.date: 06/18/2018
helpviewer_keywords:
- Networking
- adaptive proxies
- static proxies
- Network Resources
- Internet, proxy configuration
- proxies
- network, proxy configuration
- proxies, configuring
ms.assetid: 353c0a8b-4cee-44f6-8e65-60e286743df9
ms.openlocfilehash: 4d62f5736e9aa469be49d101e85851bc01b7c159
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141600"
---
# <a name="proxy-configuration"></a><span data-ttu-id="8acf8-104">代理配置</span><span class="sxs-lookup"><span data-stu-id="8acf8-104">Proxy Configuration</span></span>
<span data-ttu-id="8acf8-105">代理服务器处理客户端对资源的请求。</span><span class="sxs-lookup"><span data-stu-id="8acf8-105">A proxy server handles client requests for resources.</span></span> <span data-ttu-id="8acf8-106">代理可以从其缓存中返回已请求的资源，或将请求转发到资源驻留的服务器。</span><span class="sxs-lookup"><span data-stu-id="8acf8-106">A proxy can return a requested resource from its cache or forward the request to the server where the resource resides.</span></span> <span data-ttu-id="8acf8-107">代理可以通过减少发送到远程服务器的请求数量来提高网络性能。</span><span class="sxs-lookup"><span data-stu-id="8acf8-107">Proxies can improve network performance by reducing the number of requests sent to remote servers.</span></span> <span data-ttu-id="8acf8-108">代理还可以用于限制对资源的访问。</span><span class="sxs-lookup"><span data-stu-id="8acf8-108">Proxies can also be used to restrict access to resources.</span></span>  
  
## <a name="adaptive-proxies"></a><span data-ttu-id="8acf8-109">自适应代理</span><span class="sxs-lookup"><span data-stu-id="8acf8-109">Adaptive Proxies</span></span>  
 <span data-ttu-id="8acf8-110">在 .NET Framework 中，有两种代理：自适应和静态。</span><span class="sxs-lookup"><span data-stu-id="8acf8-110">In the .NET Framework, proxies come in two varieties: adaptive and static.</span></span> <span data-ttu-id="8acf8-111">自适应代理会在网络配置更改时调整它们的设置。</span><span class="sxs-lookup"><span data-stu-id="8acf8-111">Adaptive proxies adjust their settings when the network configuration changes.</span></span> <span data-ttu-id="8acf8-112">例如，如果便携式计算机用户启动拨号网络连接,自适应代理会识别此更改,发现并运行其新配置脚本，然后相应调整其设置。</span><span class="sxs-lookup"><span data-stu-id="8acf8-112">For example, if a laptop user starts a dialup network connection, an adaptive proxy would recognize this change, discover and run its new configuration script, and adjust its settings appropriately.</span></span>  
  
 <span data-ttu-id="8acf8-113">自适应代理是通过配置脚本配置的（请参阅[自动代理检测](automatic-proxy-detection.md)）。</span><span class="sxs-lookup"><span data-stu-id="8acf8-113">Adaptive proxies are configured by a configuration script (see [Automatic Proxy Detection](automatic-proxy-detection.md)).</span></span> <span data-ttu-id="8acf8-114">脚本针对每个协议生成一组应用程序协议和一个代理。</span><span class="sxs-lookup"><span data-stu-id="8acf8-114">The script generates a set of application protocols and a proxy for each protocol.</span></span>  
  
 <span data-ttu-id="8acf8-115">网络环境的变化可能要求系统使用一组新代理。</span><span class="sxs-lookup"><span data-stu-id="8acf8-115">Changes in the network environment may require that the system use a new set of proxies.</span></span> <span data-ttu-id="8acf8-116">如果网络连接不可用或新的网络连接已初始化，系统必须在新环境中发现相应的配置脚本源并运行新脚本。</span><span class="sxs-lookup"><span data-stu-id="8acf8-116">If a network connection goes down or a new network connection is initialized, the system must discover the appropriate source of the configuration script in the new environment and run the new script.</span></span>  
  
 <span data-ttu-id="8acf8-117">可以使用配置文件中的 [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) 元素的 `usesystemdefault` 属性。</span><span class="sxs-lookup"><span data-stu-id="8acf8-117">You can use the `usesystemdefault` attribute of the [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) element in your configuration file.</span></span> <span data-ttu-id="8acf8-118">`usesystemdefault` 属性控制是否应从用户的 Internet Explorer 代理设置读取静态代理设置（代理地址、跳过列表和跳过本地）。</span><span class="sxs-lookup"><span data-stu-id="8acf8-118">The `usesystemdefault` attribute controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="8acf8-119">如果此值设置为 `true`，那么将使用来自 Internet Explorer 的静态代理设置。</span><span class="sxs-lookup"><span data-stu-id="8acf8-119">If this value is set to `true`, the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="8acf8-120">如果此值设置为 `false` 或未设置，那么静态代理设置可在配置中指定并将替代 Internet Explorer 代理设置。</span><span class="sxs-lookup"><span data-stu-id="8acf8-120">If this value is `false` or not set, the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="8acf8-121">此外，此值必须设置为 `false` 或不设置，才能启用自适应代理。</span><span class="sxs-lookup"><span data-stu-id="8acf8-121">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>  
  
 <span data-ttu-id="8acf8-122">以下例子显示了典型的自适应代理配置。</span><span class="sxs-lookup"><span data-stu-id="8acf8-122">The following example shows a typical adaptive proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a><span data-ttu-id="8acf8-123">静态代理</span><span class="sxs-lookup"><span data-stu-id="8acf8-123">Static Proxies</span></span>  
 <span data-ttu-id="8acf8-124">静态代理通常由应用程序显示配置，或者当配置文件被应用程序或系统调用时配置。</span><span class="sxs-lookup"><span data-stu-id="8acf8-124">Static proxies are usually configured explicitly by an application, or when a configuration file is invoked by an application or the system.</span></span> <span data-ttu-id="8acf8-125">静态代理在拓扑结构更改不频繁的网络中很有用，比如连接到企业网络的台式计算机。</span><span class="sxs-lookup"><span data-stu-id="8acf8-125">Static proxies are useful in networks in which the topology changes infrequently, such as a desktop computer connected to a corporate network.</span></span>  
  
 <span data-ttu-id="8acf8-126">多个选项控制静态代理的运行方式。</span><span class="sxs-lookup"><span data-stu-id="8acf8-126">Several options control how a static proxy operates.</span></span> <span data-ttu-id="8acf8-127">可以指定以下各项：</span><span class="sxs-lookup"><span data-stu-id="8acf8-127">You can specify the following:</span></span>  
  
- <span data-ttu-id="8acf8-128">代理的地址。</span><span class="sxs-lookup"><span data-stu-id="8acf8-128">The address of the proxy.</span></span>  
  
- <span data-ttu-id="8acf8-129">是否应对本地地址不使用代理。</span><span class="sxs-lookup"><span data-stu-id="8acf8-129">Whether the proxy should be bypassed for local addresses.</span></span>  
  
- <span data-ttu-id="8acf8-130">是否应对一组地址不使用代理。</span><span class="sxs-lookup"><span data-stu-id="8acf8-130">Whether the proxy should be bypassed for a set of addresses.</span></span>  
  
 <span data-ttu-id="8acf8-131">下表显示了静态代理的配置选项。</span><span class="sxs-lookup"><span data-stu-id="8acf8-131">The following table shows the configuration options for a static proxy.</span></span>  
  
|<span data-ttu-id="8acf8-132">特性、属性或配置文件设置</span><span class="sxs-lookup"><span data-stu-id="8acf8-132">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="8acf8-133">描述</span><span class="sxs-lookup"><span data-stu-id="8acf8-133">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|<span data-ttu-id="8acf8-134">`proxyaddress` 或 <xref:System.Net.WebProxy.Address></span><span class="sxs-lookup"><span data-stu-id="8acf8-134">`proxyaddress` or <xref:System.Net.WebProxy.Address></span></span>|<span data-ttu-id="8acf8-135">要使用的代理地址。</span><span class="sxs-lookup"><span data-stu-id="8acf8-135">The address of the proxy to use.</span></span>|  
|<span data-ttu-id="8acf8-136">`bypassonlocal` 或 <xref:System.Net.WebProxy.BypassProxyOnLocal></span><span class="sxs-lookup"><span data-stu-id="8acf8-136">`bypassonlocal` or <xref:System.Net.WebProxy.BypassProxyOnLocal></span></span>|<span data-ttu-id="8acf8-137">控制是否对本地地址不使用代理。</span><span class="sxs-lookup"><span data-stu-id="8acf8-137">Controls whether the proxy is bypassed for local addresses.</span></span>|  
|<span data-ttu-id="8acf8-138">`bypasslist` 或 <xref:System.Net.WebProxy.BypassArrayList></span><span class="sxs-lookup"><span data-stu-id="8acf8-138">`bypasslist` or <xref:System.Net.WebProxy.BypassArrayList></span></span>|<span data-ttu-id="8acf8-139">用正则表达式描述不使用代理的一组地址。</span><span class="sxs-lookup"><span data-stu-id="8acf8-139">Describes, with regular expressions, a set of addresses that bypass the proxy.</span></span>|  
|`usesystemdefault`|<span data-ttu-id="8acf8-140">控制是否应从用户的 Internet Explorer 代理设置读取静态代理设置（代理地址、跳过列表和跳过本地）。</span><span class="sxs-lookup"><span data-stu-id="8acf8-140">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="8acf8-141">如果此值设置为 `true`，那么将使用来自 Internet Explorer 的静态代理设置。</span><span class="sxs-lookup"><span data-stu-id="8acf8-141">If this value is set to `true`, then the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="8acf8-142">在 .NET Framework 2.0 中，当这个值设置为 `true` 时，Internet Explorer 代理设置不会被配置文件中的其他代理设置替代。</span><span class="sxs-lookup"><span data-stu-id="8acf8-142">On .NET Framework 2.0 when this value is set to `true`, the Internet Explorer proxy settings are not overridden by other proxy settings in the configuration file.</span></span> <span data-ttu-id="8acf8-143">在 .NET Framework 1.1 中，Internet Explorer 代理设置可以被配置文件中的其他代理设置替代。</span><span class="sxs-lookup"><span data-stu-id="8acf8-143">On .NET Framework 1.1, the Internet Explorer proxy settings can be overridden by other proxy settings in the configuration file.</span></span><br /><br /> <span data-ttu-id="8acf8-144">如果此值设置为 `false` 或未设置，那么静态代理设置可在配置中指定并将替代 Internet Explorer 代理设置。</span><span class="sxs-lookup"><span data-stu-id="8acf8-144">If this value is `false` or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="8acf8-145">此外，此值必须设置为 `false` 或不设置，才能启用自适应代理。</span><span class="sxs-lookup"><span data-stu-id="8acf8-145">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="8acf8-146">以下示例显示了一个典型的静态代理配置。</span><span class="sxs-lookup"><span data-stu-id="8acf8-146">The following example shows a typical static proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
        <proxy  proxyaddress="http://proxy.contoso.com:3128"  
                bypassonlocal="True"  
        />  
        <bypasslist>  
            <add address="[a-z]+.blueyonderairlines.com$" />  
        </bypasslist>  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8acf8-147">请参阅</span><span class="sxs-lookup"><span data-stu-id="8acf8-147">See also</span></span>

- <xref:System.Net.WebProxy>
- <xref:System.Net.GlobalProxySelection>
- [<span data-ttu-id="8acf8-148">自动代理检测</span><span class="sxs-lookup"><span data-stu-id="8acf8-148">Automatic Proxy Detection</span></span>](automatic-proxy-detection.md)

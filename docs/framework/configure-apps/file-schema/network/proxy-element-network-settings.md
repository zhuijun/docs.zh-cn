---
title: <proxy> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
ms.openlocfilehash: 590ea747c2fa9e5e85e5e9d05f6fb80fe60251d3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154785"
---
# <a name="proxy-element-network-settings"></a><span data-ttu-id="94b31-102">\<proxy> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="94b31-102">\<proxy> Element (Network Settings)</span></span>
<span data-ttu-id="94b31-103">定义代理服务器。</span><span class="sxs-lookup"><span data-stu-id="94b31-103">Defines a proxy server.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**

## <a name="syntax"></a><span data-ttu-id="94b31-104">语法</span><span class="sxs-lookup"><span data-stu-id="94b31-104">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified"
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94b31-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="94b31-105">Attributes and Elements</span></span>  
 <span data-ttu-id="94b31-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="94b31-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94b31-107">特性</span><span class="sxs-lookup"><span data-stu-id="94b31-107">Attributes</span></span>  
  
|<span data-ttu-id="94b31-108">**特性**</span><span class="sxs-lookup"><span data-stu-id="94b31-108">**Attribute**</span></span>|<span data-ttu-id="94b31-109">**描述**</span><span class="sxs-lookup"><span data-stu-id="94b31-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="94b31-110">指定是否自动检测代理。</span><span class="sxs-lookup"><span data-stu-id="94b31-110">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="94b31-111">默认值为 `unspecified`。</span><span class="sxs-lookup"><span data-stu-id="94b31-111">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="94b31-112">指定对于本地资源是否跳过代理。</span><span class="sxs-lookup"><span data-stu-id="94b31-112">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="94b31-113">本地资源包括本地服务器（ `http://localhost` 、 `http://loopback` 或 `http://127.0.0.1` ）和没有句点（）的 URI `http://webserver` 。</span><span class="sxs-lookup"><span data-stu-id="94b31-113">Local resources include the local server (`http://localhost`, `http://loopback`, or `http://127.0.0.1`) and a URI without a period (`http://webserver`).</span></span> <span data-ttu-id="94b31-114">默认值为 `unspecified`。</span><span class="sxs-lookup"><span data-stu-id="94b31-114">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="94b31-115">指定要使用的代理 URI。</span><span class="sxs-lookup"><span data-stu-id="94b31-115">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="94b31-116">指定配置脚本的位置。</span><span class="sxs-lookup"><span data-stu-id="94b31-116">Specifies the location of the configuration script.</span></span> <span data-ttu-id="94b31-117">不要将 `bypassonlocal` 属性与此属性一起使用。</span><span class="sxs-lookup"><span data-stu-id="94b31-117">Do not use the `bypassonlocal` attribute with this attribute.</span></span> |  
|`usesystemdefault`|<span data-ttu-id="94b31-118">指定是否使用 Internet Explorer 代理设置。</span><span class="sxs-lookup"><span data-stu-id="94b31-118">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="94b31-119">如果设置为 `true` ，则后续特性将重写 Internet Explorer 代理设置。</span><span class="sxs-lookup"><span data-stu-id="94b31-119">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="94b31-120">默认值为 `unspecified`。</span><span class="sxs-lookup"><span data-stu-id="94b31-120">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="94b31-121">子元素</span><span class="sxs-lookup"><span data-stu-id="94b31-121">Child Elements</span></span>  
 <span data-ttu-id="94b31-122">无。</span><span class="sxs-lookup"><span data-stu-id="94b31-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="94b31-123">父元素</span><span class="sxs-lookup"><span data-stu-id="94b31-123">Parent Elements</span></span>  
  
|<span data-ttu-id="94b31-124">**元素**</span><span class="sxs-lookup"><span data-stu-id="94b31-124">**Element**</span></span>|<span data-ttu-id="94b31-125">**描述**</span><span class="sxs-lookup"><span data-stu-id="94b31-125">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="94b31-126">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="94b31-126">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="94b31-127">配置超文本传输协议 (HTTP) 代理服务器。</span><span class="sxs-lookup"><span data-stu-id="94b31-127">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="94b31-128">文本值</span><span class="sxs-lookup"><span data-stu-id="94b31-128">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94b31-129">注解</span><span class="sxs-lookup"><span data-stu-id="94b31-129">Remarks</span></span>  
 <span data-ttu-id="94b31-130">`proxy`元素为应用程序定义代理服务器。</span><span class="sxs-lookup"><span data-stu-id="94b31-130">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="94b31-131">如果配置文件中缺少此元素，则 .NET Framework 将使用 Internet Explorer 中的代理设置。</span><span class="sxs-lookup"><span data-stu-id="94b31-131">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="94b31-132">特性的值 `proxyaddress` 应为格式正确的统一资源标识符（URI）。</span><span class="sxs-lookup"><span data-stu-id="94b31-132">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="94b31-133">`scriptLocation`属性指自动检测代理配置脚本。</span><span class="sxs-lookup"><span data-stu-id="94b31-133">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="94b31-134">在 <xref:System.Net.WebProxy> Internet Explorer 中选择 "**使用自动配置脚本**" 选项后，类将尝试查找配置脚本（通常名为 Wpad）。</span><span class="sxs-lookup"><span data-stu-id="94b31-134">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span> <span data-ttu-id="94b31-135">如果 `bypassonlocal` 设置为任何值， `scriptLocation` 则将被忽略。</span><span class="sxs-lookup"><span data-stu-id="94b31-135">If `bypassonlocal` is set to any value, `scriptLocation` is ignored.</span></span>
  
 <span data-ttu-id="94b31-136">将 `usesystemdefault` .NET Framework 版本1.1 应用程序的属性迁移到版本2.0。</span><span class="sxs-lookup"><span data-stu-id="94b31-136">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="94b31-137">如果 `proxyaddress` 特性指定了无效的默认代理，则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="94b31-137">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="94b31-138">异常的 <xref:System.Exception.InnerException%2A> 属性应具有错误根本原因的详细信息。</span><span class="sxs-lookup"><span data-stu-id="94b31-138">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="94b31-139">配置文件</span><span class="sxs-lookup"><span data-stu-id="94b31-139">Configuration Files</span></span>  
 <span data-ttu-id="94b31-140">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="94b31-140">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="94b31-141">示例</span><span class="sxs-lookup"><span data-stu-id="94b31-141">Example</span></span>  
 <span data-ttu-id="94b31-142">以下示例使用 Internet Explorer 代理中的默认值，指定代理地址，并绕过代理进行本地访问。</span><span class="sxs-lookup"><span data-stu-id="94b31-142">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="94b31-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="94b31-143">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="94b31-144">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="94b31-144">Network Settings Schema</span></span>](index.md)

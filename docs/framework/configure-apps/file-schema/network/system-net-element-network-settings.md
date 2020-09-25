---
title: <system.Net> 元素（网络设置）
description: <system.Net> 网络设置元素包含用于指定 .NET Framework 如何连接到 .NET Framework 中的网络选项的设置。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
ms.openlocfilehash: 80d54df40c6798e146013b4f2d867386ae35169c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201715"
---
# <a name="systemnet-element-network-settings"></a><span data-ttu-id="e3fce-103">\<system.Net> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="e3fce-103">\<system.Net> Element (Network Settings)</span></span>

<span data-ttu-id="e3fce-104">包含指定 .NET Framework 如何连接到网络的设置。</span><span class="sxs-lookup"><span data-stu-id="e3fce-104">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.net>**  
  
## <a name="syntax"></a><span data-ttu-id="e3fce-105">语法</span><span class="sxs-lookup"><span data-stu-id="e3fce-105">Syntax</span></span>  
  
```xml  
<system.net>
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3fce-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e3fce-106">Attributes and Elements</span></span>  

 <span data-ttu-id="e3fce-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e3fce-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3fce-108">特性</span><span class="sxs-lookup"><span data-stu-id="e3fce-108">Attributes</span></span>  

 <span data-ttu-id="e3fce-109">无。</span><span class="sxs-lookup"><span data-stu-id="e3fce-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e3fce-110">子元素</span><span class="sxs-lookup"><span data-stu-id="e3fce-110">Child Elements</span></span>  
  
|<span data-ttu-id="e3fce-111">**元素**</span><span class="sxs-lookup"><span data-stu-id="e3fce-111">**Element**</span></span>|<span data-ttu-id="e3fce-112">**说明**</span><span class="sxs-lookup"><span data-stu-id="e3fce-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e3fce-113">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="e3fce-113">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="e3fce-114">指定用于对 Internet 请求进行身份验证的模块。</span><span class="sxs-lookup"><span data-stu-id="e3fce-114">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="e3fce-115">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="e3fce-115">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="e3fce-116">指定与 Internet 主机的最大连接数。</span><span class="sxs-lookup"><span data-stu-id="e3fce-116">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="e3fce-117">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="e3fce-117">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="e3fce-118">配置超文本传输协议 (HTTP) 代理服务器。</span><span class="sxs-lookup"><span data-stu-id="e3fce-118">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="e3fce-119">mailSettings</span><span class="sxs-lookup"><span data-stu-id="e3fce-119">mailSettings</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="e3fce-120"> (SMTP) 邮件发送选项配置简单邮件传输协议。</span><span class="sxs-lookup"><span data-stu-id="e3fce-120">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="e3fce-121">requestCaching</span><span class="sxs-lookup"><span data-stu-id="e3fce-121">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="e3fce-122">控制网络请求的缓存机制。</span><span class="sxs-lookup"><span data-stu-id="e3fce-122">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="e3fce-123">设置</span><span class="sxs-lookup"><span data-stu-id="e3fce-123">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="e3fce-124">为 <xref:System.Net> 和相关子命名空间中的类配置基本网络选项。</span><span class="sxs-lookup"><span data-stu-id="e3fce-124">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="e3fce-125">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="e3fce-125">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="e3fce-126">指定用于从 Internet 主机请求信息的模块。</span><span class="sxs-lookup"><span data-stu-id="e3fce-126">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e3fce-127">父元素</span><span class="sxs-lookup"><span data-stu-id="e3fce-127">Parent Elements</span></span>  
  
|<span data-ttu-id="e3fce-128">**元素**</span><span class="sxs-lookup"><span data-stu-id="e3fce-128">**Element**</span></span>|<span data-ttu-id="e3fce-129">**说明**</span><span class="sxs-lookup"><span data-stu-id="e3fce-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e3fce-130">configuration</span><span class="sxs-lookup"><span data-stu-id="e3fce-130">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="e3fce-131">包含所有命名空间的设置。</span><span class="sxs-lookup"><span data-stu-id="e3fce-131">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3fce-132">备注</span><span class="sxs-lookup"><span data-stu-id="e3fce-132">Remarks</span></span>  

 <span data-ttu-id="e3fce-133">[\<system.net>](system-net-element-network-settings.md)元素包含 <xref:System.Net> 和相关子命名空间中的类的设置。</span><span class="sxs-lookup"><span data-stu-id="e3fce-133">The [\<system.net>](system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="e3fce-134">设置配置身份验证模块、连接管理、邮件设置、代理服务器和 Internet 请求模块，用于接收来自 Internet 主机的信息。</span><span class="sxs-lookup"><span data-stu-id="e3fce-134">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3fce-135">示例</span><span class="sxs-lookup"><span data-stu-id="e3fce-135">Example</span></span>  

 <span data-ttu-id="e3fce-136">下面的示例演示了类使用的典型配置 <xref:System.Net> 。</span><span class="sxs-lookup"><span data-stu-id="e3fce-136">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient" />  
      <add type="System.Net.NegotiateClient" />  
      <add type="System.Net.KerberosClient" />  
      <add type="System.Net.NtlmClient" />  
      <add type="System.Net.BasicClient" />  
    </authenticationModules>  
    <connectionManagement>  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="https"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="file"  
           type="System.Net.FileWebRequestCreator"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e3fce-137">请参阅</span><span class="sxs-lookup"><span data-stu-id="e3fce-137">See also</span></span>

- [<span data-ttu-id="e3fce-138">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="e3fce-138">Network Settings Schema</span></span>](index.md)

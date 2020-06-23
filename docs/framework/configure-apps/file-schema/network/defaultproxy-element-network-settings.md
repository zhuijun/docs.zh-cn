---
title: <defaultProxy> 元素（网络设置）
description: <defaultProxy>网络设置元素在 .NET Framework 中配置超文本传输协议（HTTP）代理服务器。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
ms.openlocfilehash: 85004d49ce7605b050709a3019592ec696a7bada
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141626"
---
# <a name="defaultproxy-element-network-settings"></a><span data-ttu-id="ced27-103">\<defaultProxy> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="ced27-103">\<defaultProxy> Element (Network Settings)</span></span>
<span data-ttu-id="ced27-104">配置超文本传输协议 (HTTP) 代理服务器。</span><span class="sxs-lookup"><span data-stu-id="ced27-104">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultProxy>**  
  
## <a name="syntax"></a><span data-ttu-id="ced27-105">语法</span><span class="sxs-lookup"><span data-stu-id="ced27-105">Syntax</span></span>  
  
```xml  
<defaultProxy  
  enabled="True|False"  
  useDefaultCredentials="True|False">  
    <bypasslist>...</bypasslist>  
    <proxy>...</proxy>  
    <module>...</module>  
</defaultProxy>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ced27-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="ced27-106">Attributes and Elements</span></span>  
 <span data-ttu-id="ced27-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ced27-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ced27-108">特性</span><span class="sxs-lookup"><span data-stu-id="ced27-108">Attributes</span></span>  
  
|<span data-ttu-id="ced27-109">**元素**</span><span class="sxs-lookup"><span data-stu-id="ced27-109">**Element**</span></span>|<span data-ttu-id="ced27-110">**说明**</span><span class="sxs-lookup"><span data-stu-id="ced27-110">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="ced27-111">指定是否使用 Web 代理。</span><span class="sxs-lookup"><span data-stu-id="ced27-111">Specifies whether a web proxy is used.</span></span> <span data-ttu-id="ced27-112">默认值为 `True`。</span><span class="sxs-lookup"><span data-stu-id="ced27-112">The default value is `True`.</span></span>|  
|`useDefaultCredentials`|<span data-ttu-id="ced27-113">指定是否使用此主机的默认凭据来访问 Web 代理。</span><span class="sxs-lookup"><span data-stu-id="ced27-113">Specifies whether the default credentials for this host are used to access the web proxy.</span></span> <span data-ttu-id="ced27-114">默认值为 `False`。</span><span class="sxs-lookup"><span data-stu-id="ced27-114">The default value is `False`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ced27-115">子元素</span><span class="sxs-lookup"><span data-stu-id="ced27-115">Child Elements</span></span>  
  
|<span data-ttu-id="ced27-116">**元素**</span><span class="sxs-lookup"><span data-stu-id="ced27-116">**Element**</span></span>|<span data-ttu-id="ced27-117">**说明**</span><span class="sxs-lookup"><span data-stu-id="ced27-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ced27-118">bypasslist</span><span class="sxs-lookup"><span data-stu-id="ced27-118">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="ced27-119">提供一组描述不使用代理的地址的正则表达式。</span><span class="sxs-lookup"><span data-stu-id="ced27-119">Provides a set of regular expressions that describe addresses that do not use the proxy.</span></span>|  
|[<span data-ttu-id="ced27-120">模块</span><span class="sxs-lookup"><span data-stu-id="ced27-120">module</span></span>](module-element-network-settings.md)|<span data-ttu-id="ced27-121">向应用程序添加新的代理模块。</span><span class="sxs-lookup"><span data-stu-id="ced27-121">Adds a new proxy module to the application.</span></span>|  
|[<span data-ttu-id="ced27-122">代理</span><span class="sxs-lookup"><span data-stu-id="ced27-122">proxy</span></span>](proxy-element-network-settings.md)|<span data-ttu-id="ced27-123">定义代理服务器。</span><span class="sxs-lookup"><span data-stu-id="ced27-123">Defines a proxy server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ced27-124">父元素</span><span class="sxs-lookup"><span data-stu-id="ced27-124">Parent Elements</span></span>  
  
|<span data-ttu-id="ced27-125">**元素**</span><span class="sxs-lookup"><span data-stu-id="ced27-125">**Element**</span></span>|<span data-ttu-id="ced27-126">**说明**</span><span class="sxs-lookup"><span data-stu-id="ced27-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ced27-127">system.net</span><span class="sxs-lookup"><span data-stu-id="ced27-127">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="ced27-128">包含指定 .NET Framework 如何连接到网络的设置。</span><span class="sxs-lookup"><span data-stu-id="ced27-128">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ced27-129">备注</span><span class="sxs-lookup"><span data-stu-id="ced27-129">Remarks</span></span>  
 <span data-ttu-id="ced27-130">如果 defaultProxy 元素为空，则将沿用 Internet Explorer 中的代理设置。</span><span class="sxs-lookup"><span data-stu-id="ced27-130">If the defaultProxy element is empty, the proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="ced27-131">这种行为在 .NET Framework 1.1 版中有所不同。</span><span class="sxs-lookup"><span data-stu-id="ced27-131">This behavior is different from version 1.1 of the .NET Framework.</span></span>  
  
 <span data-ttu-id="ced27-132">如果[module](module-element-network-settings.md)元素指定非公共类型，该类型不是从 <xref:System.Net.IWebProxy> 类派生，则此对象的无参数构造函数中出现异常，或者在检索系统指定的默认代理时出现异常，则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="ced27-132">An exception is thrown if the [module](module-element-network-settings.md) element specifies a non-public type, the type is not deriving from the <xref:System.Net.IWebProxy> class, an exception from the parameterless constructor of this object occurred, or an exception occurred while retrieving the system-specified default proxy.</span></span> <span data-ttu-id="ced27-133">异常的 <xref:System.Exception.InnerException%2A> 属性应具有错误根本原因的详细信息。</span><span class="sxs-lookup"><span data-stu-id="ced27-133">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="ced27-134">配置文件</span><span class="sxs-lookup"><span data-stu-id="ced27-134">Configuration Files</span></span>  
 <span data-ttu-id="ced27-135">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="ced27-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ced27-136">示例</span><span class="sxs-lookup"><span data-stu-id="ced27-136">Example</span></span>  
 <span data-ttu-id="ced27-137">以下示例使用 Internet Explorer 代理中的默认值，指定代理地址，并绕过代理进行本地访问和 contoso.com。</span><span class="sxs-lookup"><span data-stu-id="ced27-137">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access and contoso.com.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="True"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="True"  
      />  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ced27-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ced27-138">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="ced27-139">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="ced27-139">Network Settings Schema</span></span>](index.md)

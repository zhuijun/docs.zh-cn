---
title: <ipv6> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/ipv6
- http://schemas.microsoft.com/.NetConfiguration/v2.0#ipv6
helpviewer_keywords:
- <ipv6> element
- ipv6 element
ms.assetid: 10b79aef-327b-4718-a892-e11f55e4d169
ms.openlocfilehash: c16949171d082bd02abb0a02db83c2e71c2f17df
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088138"
---
# <a name="ipv6-element-network-settings"></a><span data-ttu-id="e60ea-102">\<ipv6> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="e60ea-102">\<ipv6> Element (Network Settings)</span></span>
<span data-ttu-id="e60ea-103">启用来自类的过时成员的 Internet 协议版本6（IPv6）响应 <xref:System.Net.Dns> 。</span><span class="sxs-lookup"><span data-stu-id="e60ea-103">Enables Internet Protocol version 6 (IPv6) responses from obsolete members of the <xref:System.Net.Dns> class.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ipv6>**

## <a name="syntax"></a><span data-ttu-id="e60ea-104">语法</span><span class="sxs-lookup"><span data-stu-id="e60ea-104">Syntax</span></span>  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e60ea-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e60ea-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e60ea-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e60ea-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e60ea-107">特性</span><span class="sxs-lookup"><span data-stu-id="e60ea-107">Attributes</span></span>  
  
|<span data-ttu-id="e60ea-108">**特性**</span><span class="sxs-lookup"><span data-stu-id="e60ea-108">**Attribute**</span></span>|<span data-ttu-id="e60ea-109">**描述**</span><span class="sxs-lookup"><span data-stu-id="e60ea-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`enabled`|<span data-ttu-id="e60ea-110">指定类的成员是否 <xref:System.Net.Dns> 返回 Internet 协议版本6（IPv6）地址。</span><span class="sxs-lookup"><span data-stu-id="e60ea-110">Specifies whether members of the <xref:System.Net.Dns> class return Internet Protocol version 6 (IPv6) addresses.</span></span> <span data-ttu-id="e60ea-111">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="e60ea-111">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e60ea-112">子元素</span><span class="sxs-lookup"><span data-stu-id="e60ea-112">Child Elements</span></span>  
 <span data-ttu-id="e60ea-113">无。</span><span class="sxs-lookup"><span data-stu-id="e60ea-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e60ea-114">父元素</span><span class="sxs-lookup"><span data-stu-id="e60ea-114">Parent Elements</span></span>  
  
|<span data-ttu-id="e60ea-115">**元素**</span><span class="sxs-lookup"><span data-stu-id="e60ea-115">**Element**</span></span>|<span data-ttu-id="e60ea-116">**描述**</span><span class="sxs-lookup"><span data-stu-id="e60ea-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e60ea-117">设置</span><span class="sxs-lookup"><span data-stu-id="e60ea-117">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="e60ea-118">配置 <xref:System.Net> 命名空间的基本网络选项。</span><span class="sxs-lookup"><span data-stu-id="e60ea-118">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e60ea-119">注解</span><span class="sxs-lookup"><span data-stu-id="e60ea-119">Remarks</span></span>  
 <span data-ttu-id="e60ea-120">此设置为类的过时成员启用 IPv6 支持 <xref:System.Net.Dns> ： <xref:System.Net.Dns.BeginGetHostByName%2A> 、 <xref:System.Net.Dns.BeginResolve%2A> 、 <xref:System.Net.Dns.EndGetHostByName%2A> 、、、 <xref:System.Net.Dns.EndResolve%2A> <xref:System.Net.Dns.GetHostByAddress%2A> <xref:System.Net.Dns.GetHostByName%2A> 和 <xref:System.Net.Dns.Resolve%2A> 。</span><span class="sxs-lookup"><span data-stu-id="e60ea-120">This setting enables IPv6 support for the obsolete members of the <xref:System.Net.Dns> class: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, and <xref:System.Net.Dns.Resolve%2A>.</span></span> <span data-ttu-id="e60ea-121">对于命名空间的其他成员 <xref:System.Net?displayProperty=nameWithType> ，如果在操作系统中启用了 ipv6，则可能会返回 ipv6 地址。</span><span class="sxs-lookup"><span data-stu-id="e60ea-121">For other members of the <xref:System.Net?displayProperty=nameWithType> namespace, IPv6 addresses may be returned if IPv6 is enabled in the operating system.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e60ea-122">配置文件</span><span class="sxs-lookup"><span data-stu-id="e60ea-122">Configuration Files</span></span>  
 <span data-ttu-id="e60ea-123">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="e60ea-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e60ea-124">示例</span><span class="sxs-lookup"><span data-stu-id="e60ea-124">Example</span></span>  
 <span data-ttu-id="e60ea-125">下面的示例演示如何为类启用 IPv6 支持 <xref:System.Net.Dns> 。</span><span class="sxs-lookup"><span data-stu-id="e60ea-125">The following example shows how to enable IPv6 support for the <xref:System.Net.Dns> class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e60ea-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e60ea-126">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Dns?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e60ea-127">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="e60ea-127">Network Settings Schema</span></span>](index.md)

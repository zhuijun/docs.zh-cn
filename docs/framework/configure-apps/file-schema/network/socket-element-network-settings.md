---
title: <socket> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
ms.openlocfilehash: 0e2b369eccfbc658a790ef61a961315a88361669
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089091"
---
# <a name="socket-element-network-settings"></a><span data-ttu-id="13a1b-102">\<socket> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="13a1b-102">\<socket> Element (Network Settings)</span></span>
<span data-ttu-id="13a1b-103">指定套接字操作是否使用完成端口。</span><span class="sxs-lookup"><span data-stu-id="13a1b-103">Specifies whether socket operations use completion ports.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<socket>**

## <a name="syntax"></a><span data-ttu-id="13a1b-104">语法</span><span class="sxs-lookup"><span data-stu-id="13a1b-104">Syntax</span></span>  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13a1b-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="13a1b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="13a1b-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="13a1b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13a1b-107">特性</span><span class="sxs-lookup"><span data-stu-id="13a1b-107">Attributes</span></span>  
  
|<span data-ttu-id="13a1b-108">**特性**</span><span class="sxs-lookup"><span data-stu-id="13a1b-108">**Attribute**</span></span>|<span data-ttu-id="13a1b-109">**描述**</span><span class="sxs-lookup"><span data-stu-id="13a1b-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|<span data-ttu-id="13a1b-110">指示套接字是否应始终对接受方法调用使用完成端口。</span><span class="sxs-lookup"><span data-stu-id="13a1b-110">Indicates whether the socket should always use completion ports for Accept method calls.</span></span> <span data-ttu-id="13a1b-111">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="13a1b-111">The default value is `false`.</span></span>|  
|`alwaysUseCompletionPortsForConnect`|<span data-ttu-id="13a1b-112">指示套接字是否应始终对连接方法调用使用完成端口。</span><span class="sxs-lookup"><span data-stu-id="13a1b-112">Indicates whether the socket should always use completion ports for Connect method calls.</span></span> <span data-ttu-id="13a1b-113">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="13a1b-113">The default value is `false`.</span></span>|  
|`ipProtectionLevel`|<span data-ttu-id="13a1b-114">指定要用于 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> 套接字的默认。</span><span class="sxs-lookup"><span data-stu-id="13a1b-114">Specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="13a1b-115">默认值取决于 Windows 的版本。</span><span class="sxs-lookup"><span data-stu-id="13a1b-115">The default value depends on the version of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13a1b-116">子元素</span><span class="sxs-lookup"><span data-stu-id="13a1b-116">Child Elements</span></span>  
 <span data-ttu-id="13a1b-117">无。</span><span class="sxs-lookup"><span data-stu-id="13a1b-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="13a1b-118">父元素</span><span class="sxs-lookup"><span data-stu-id="13a1b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="13a1b-119">**元素**</span><span class="sxs-lookup"><span data-stu-id="13a1b-119">**Element**</span></span>|<span data-ttu-id="13a1b-120">**描述**</span><span class="sxs-lookup"><span data-stu-id="13a1b-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="13a1b-121">设置</span><span class="sxs-lookup"><span data-stu-id="13a1b-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="13a1b-122">配置 <xref:System.Net> 命名空间的基本网络选项。</span><span class="sxs-lookup"><span data-stu-id="13a1b-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13a1b-123">注解</span><span class="sxs-lookup"><span data-stu-id="13a1b-123">Remarks</span></span>  
 <span data-ttu-id="13a1b-124">`alwaysUseCompletionPortsForAccept` 和 `alwaysUseCompletionPortsForConnect` 特性用于指定 <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace 中的类在使用完全端口时的默认行为。</span><span class="sxs-lookup"><span data-stu-id="13a1b-124">The `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes are used to specify the default behavior regarding the use of completion ports by the classes in the <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span></span> <span data-ttu-id="13a1b-125">对于高性能服务器应用程序，建议使用完成端口。</span><span class="sxs-lookup"><span data-stu-id="13a1b-125">Completion ports are recommended for high performance server applications.</span></span>  
  
 <span data-ttu-id="13a1b-126">和特性的默认值 `alwaysUseCompletionPortsForAccept` `alwaysUseCompletionPortsForConnect` 为**false**。</span><span class="sxs-lookup"><span data-stu-id="13a1b-126">The default value for the `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes is **false**.</span></span>  
  
 <span data-ttu-id="13a1b-127"><xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A>可用于 `alwaysUseCompletionPortsForAccept` 从适用的配置文件中获取特性的当前值。</span><span class="sxs-lookup"><span data-stu-id="13a1b-127">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> can be used to get the current value of the `alwaysUseCompletionPortsForAccept` attribute from applicable configuration files.</span></span> <span data-ttu-id="13a1b-128"><xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A>可用于 `alwaysUseCompletionPortsForConnect` 从适用的配置文件中获取特性的当前值。</span><span class="sxs-lookup"><span data-stu-id="13a1b-128">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> can be used to get the current value of the `alwaysUseCompletionPortsForConnect` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="13a1b-129">`ipProtectionLevel`特性指定 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> 要用于套接字的默认。</span><span class="sxs-lookup"><span data-stu-id="13a1b-129">The `ipProtectionLevel` attribute specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="13a1b-130"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>属性允许将 IPv6 套接字的限制配置为指定的作用域，如具有相同的链接本地或站点本地前缀的地址。</span><span class="sxs-lookup"><span data-stu-id="13a1b-130">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property enables configuration of a restriction for an IPv6 socket to a specified scope, such as addresses with the same link local or site local prefix.</span></span> <span data-ttu-id="13a1b-131">此选项使应用程序可以对 IPv6 套接字设置访问限制。</span><span class="sxs-lookup"><span data-stu-id="13a1b-131">This option enables applications to place access restrictions on IPv6 sockets.</span></span> <span data-ttu-id="13a1b-132">通过应用此类限制，可让在专用局域网上运行的应用程序能够通过简单的方式很好地增强自身的安全性，以便防范外部攻击。</span><span class="sxs-lookup"><span data-stu-id="13a1b-132">Such restrictions enable an application running on a private LAN to simply and robustly harden itself against external attacks.</span></span> <span data-ttu-id="13a1b-133">此选项扩大或缩小侦听套接字的范围，在适当的时候启用从公共用户和私有用户进行的不受限制的访问，或根据需要限制对同一站点的访问。</span><span class="sxs-lookup"><span data-stu-id="13a1b-133">This option widens or narrows the scope of a listening socket, enabling unrestricted access from public and private users when appropriate, or restricting access only to the same site, as required.</span></span>  
  
 <span data-ttu-id="13a1b-134">此 `ipProtectionLevel` 属性设置只影响初始传入流量：</span><span class="sxs-lookup"><span data-stu-id="13a1b-134">This `ipProtectionLevel` attribute setting affects only initial incoming traffic:</span></span>  
  
- <span data-ttu-id="13a1b-135">在套接字上侦听传入连接的 TCP 服务器。</span><span class="sxs-lookup"><span data-stu-id="13a1b-135">A TCP server listening for incoming connections on a socket.</span></span>  
  
- <span data-ttu-id="13a1b-136">在套接字上接收数据包的 UDP 应用程序。</span><span class="sxs-lookup"><span data-stu-id="13a1b-136">A UDP application receiving a packet on a socket.</span></span>  
  
 <span data-ttu-id="13a1b-137">此配置设置不影响已建立的 TCP 连接（流量在两个方向上无限制），并且不影响发送 UDP 数据包的应用程序。</span><span class="sxs-lookup"><span data-stu-id="13a1b-137">This configuration setting does not affect already established TCP connections (traffic is unrestricted in both directions) and does not affect an application sending UDP packets.</span></span>  
  
 <span data-ttu-id="13a1b-138">属性设置的可能值与 `ipProtectionLevel` 枚举中指定的已定义保护级别相对应，如下所示 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> ：</span><span class="sxs-lookup"><span data-stu-id="13a1b-138">The possible values for the `ipProtectionLevel` attribute setting correspond with the defined protection levels specified in the <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> enumeration as follows:</span></span>  
  
|<span data-ttu-id="13a1b-139">**属性值**</span><span class="sxs-lookup"><span data-stu-id="13a1b-139">**Attribute Value**</span></span>|<span data-ttu-id="13a1b-140">**描述**</span><span class="sxs-lookup"><span data-stu-id="13a1b-140">**Description**</span></span>|  
|-|-|  
|<span data-ttu-id="13a1b-141">EdgeRestricted</span><span class="sxs-lookup"><span data-stu-id="13a1b-141">EdgeRestricted</span></span>|<span data-ttu-id="13a1b-142">IP 保护级别是“边缘受限的”。</span><span class="sxs-lookup"><span data-stu-id="13a1b-142">The IP protection level is edge restricted.</span></span> <span data-ttu-id="13a1b-143">此值应由设计为在 Internet 上运行的应用程序使用。</span><span class="sxs-lookup"><span data-stu-id="13a1b-143">This value would be used by applications designed to operate across the Internet.</span></span> <span data-ttu-id="13a1b-144">此设置不允许使用 Windows Teredo 实现的网络地址转换 (NAT) 遍历。</span><span class="sxs-lookup"><span data-stu-id="13a1b-144">This setting does not allow Network Address Translation (NAT) traversal using the Windows Teredo implementation.</span></span> <span data-ttu-id="13a1b-145">这些应用程序可能会绕过 IPv4 防火墙，因此，必须加强应用程序的安全性以防范针对开放端口的 Internet 攻击。</span><span class="sxs-lookup"><span data-stu-id="13a1b-145">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="13a1b-146">在 Windows Server 2003 和 Windows XP 中，针对套接字的 IP 保护级别的默认值是“边缘受限的”。</span><span class="sxs-lookup"><span data-stu-id="13a1b-146">On Windows Server 2003 and Windows XP, the default value for the IP Protection level on a socket is edge restricted.</span></span>|  
|<span data-ttu-id="13a1b-147">受限</span><span class="sxs-lookup"><span data-stu-id="13a1b-147">Restricted</span></span>|<span data-ttu-id="13a1b-148">IP 保护级别是“受限的”。</span><span class="sxs-lookup"><span data-stu-id="13a1b-148">The IP protection level is restricted.</span></span> <span data-ttu-id="13a1b-149">此值应由未实现 Internet 方案的 Intranet 应用程序使用。</span><span class="sxs-lookup"><span data-stu-id="13a1b-149">This value would be used by intranet applications that do not implement Internet scenarios.</span></span> <span data-ttu-id="13a1b-150">一般情况下，不会针对 Internet 样式的攻击来对这些应用程序进行测试或加强安全性。</span><span class="sxs-lookup"><span data-stu-id="13a1b-150">These applications are generally not tested or hardened against Internet-style attacks.</span></span> <span data-ttu-id="13a1b-151">此设置将限制仅接收链接本地的通信。</span><span class="sxs-lookup"><span data-stu-id="13a1b-151">This setting will limit the received traffic to link-local only.</span></span>|  
|<span data-ttu-id="13a1b-152">非受限</span><span class="sxs-lookup"><span data-stu-id="13a1b-152">Unrestricted</span></span>|<span data-ttu-id="13a1b-153">IP 保护级别是“不受限的”。</span><span class="sxs-lookup"><span data-stu-id="13a1b-153">The IP protection level is unrestricted.</span></span> <span data-ttu-id="13a1b-154">此值应由设计为在 Internet 上运行的应用程序使用，包括利用 Windows 中内置的 IPv6 NAT 遍历功能（例如，Teredo）的应用程序。</span><span class="sxs-lookup"><span data-stu-id="13a1b-154">This value would be used by applications designed to operate across the Internet, including applications taking advantage of IPv6 NAT traversal capabilities built into Windows (Teredo, for example).</span></span> <span data-ttu-id="13a1b-155">这些应用程序可能会绕过 IPv4 防火墙，因此，必须加强应用程序的安全性以防范针对开放端口的 Internet 攻击。</span><span class="sxs-lookup"><span data-stu-id="13a1b-155">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="13a1b-156">在 Windows Server 2008 R2 和 Windows Vista 中，针对套接字的 IP 保护级别的默认值是“不受限的”。</span><span class="sxs-lookup"><span data-stu-id="13a1b-156">On Windows Server 2008 R2 and Windows Vista, the default value for the IP Protection level on a socket is unrestricted.</span></span>|  
|<span data-ttu-id="13a1b-157">未指定</span><span class="sxs-lookup"><span data-stu-id="13a1b-157">Unspecified</span></span>|<span data-ttu-id="13a1b-158">IP 保护级别是“未指定的”。</span><span class="sxs-lookup"><span data-stu-id="13a1b-158">The IP protection level is unspecified.</span></span> <span data-ttu-id="13a1b-159">在 Windows 7 和 Windows Server 2008 R2 中，针对套接字的 IP 保护级别的默认值是“未指定的”。</span><span class="sxs-lookup"><span data-stu-id="13a1b-159">On Windows 7 and Windows Server 2008 R2, the default value for the IP Protection level on a socket is unspecified.</span></span>|  
  
 <span data-ttu-id="13a1b-160">`ipProtectionLevel`**未指定**该属性的默认值。</span><span class="sxs-lookup"><span data-stu-id="13a1b-160">The default value for the `ipProtectionLevel` attribute is **Unspecified**.</span></span>  
  
 <span data-ttu-id="13a1b-161"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>属性可用于 `ipProtectionLevel` 从适用的配置文件中获取特性的当前值。</span><span class="sxs-lookup"><span data-stu-id="13a1b-161">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property can be used to get the current value of the `ipProtectionLevel` attribute from applicable configuration files.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="13a1b-162">配置文件</span><span class="sxs-lookup"><span data-stu-id="13a1b-162">Configuration Files</span></span>  
 <span data-ttu-id="13a1b-163">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="13a1b-163">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="13a1b-164">示例</span><span class="sxs-lookup"><span data-stu-id="13a1b-164">Example</span></span>  
 <span data-ttu-id="13a1b-165">下面的示例演示如何指定应使用完成端口，并且默认值 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> 应为 "无限制"。</span><span class="sxs-lookup"><span data-stu-id="13a1b-165">The following example shows how to specify that completion ports should be used and that the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> should be unrestricted.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <socket  
        alwaysUseCompletionPortsForAccept="true"  
        alwaysUseCompletionPortsForConnect="true"  
        ipProtectionLevel="Unrestricted"  
       />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="13a1b-166">另请参阅</span><span class="sxs-lookup"><span data-stu-id="13a1b-166">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>
- [<span data-ttu-id="13a1b-167">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="13a1b-167">Network Settings Schema</span></span>](index.md)

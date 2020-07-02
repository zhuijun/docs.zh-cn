---
title: 启用和禁用 IPv6
description: 按照这些配置步骤使用 IPv6 协议，包括修改计算机的配置文件或应用程序的配置文件。
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
ms.openlocfilehash: 7729647b09df20a98d5d639a641cb0a31f557330
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502608"
---
# <a name="enabling-and-disabling-ipv6"></a><span data-ttu-id="f4662-103">启用和禁用 IPv6</span><span class="sxs-lookup"><span data-stu-id="f4662-103">Enabling and Disabling IPv6</span></span>
<span data-ttu-id="f4662-104">若要使用 IPv6 协议，请确保当前运行的操作系统版本支持 IPv6，并确保正确配置了操作系统和网络类。</span><span class="sxs-lookup"><span data-stu-id="f4662-104">To use the IPv6 protocol, ensure that you are running a version of the operating system that supports IPv6 and ensure that the operating system and the networking classes are configured properly.</span></span>  
  
## <a name="configuration-steps"></a><span data-ttu-id="f4662-105">配置步骤</span><span class="sxs-lookup"><span data-stu-id="f4662-105">Configuration Steps</span></span>  
 <span data-ttu-id="f4662-106">下表列出了各种配置</span><span class="sxs-lookup"><span data-stu-id="f4662-106">The following table lists various configurations</span></span>  
  
|<span data-ttu-id="f4662-107">支持 IPv6 的操作系统？</span><span class="sxs-lookup"><span data-stu-id="f4662-107">Operating system IPv6-enabled?</span></span>|<span data-ttu-id="f4662-108">支持 IPv6 的网络类？</span><span class="sxs-lookup"><span data-stu-id="f4662-108">Networking classes IPv6-enabled?</span></span>|<span data-ttu-id="f4662-109">描述</span><span class="sxs-lookup"><span data-stu-id="f4662-109">Description</span></span>|  
|-------------------------------------|---------------------------------------|-----------------|  
|<span data-ttu-id="f4662-110">否</span><span class="sxs-lookup"><span data-stu-id="f4662-110">No</span></span>|<span data-ttu-id="f4662-111">否</span><span class="sxs-lookup"><span data-stu-id="f4662-111">No</span></span>|<span data-ttu-id="f4662-112">可以分析 IPv6 地址。</span><span class="sxs-lookup"><span data-stu-id="f4662-112">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="f4662-113">否</span><span class="sxs-lookup"><span data-stu-id="f4662-113">No</span></span>|<span data-ttu-id="f4662-114">是</span><span class="sxs-lookup"><span data-stu-id="f4662-114">Yes</span></span>|<span data-ttu-id="f4662-115">可以分析 IPv6 地址。</span><span class="sxs-lookup"><span data-stu-id="f4662-115">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="f4662-116">是</span><span class="sxs-lookup"><span data-stu-id="f4662-116">Yes</span></span>|<span data-ttu-id="f4662-117">否</span><span class="sxs-lookup"><span data-stu-id="f4662-117">No</span></span>|<span data-ttu-id="f4662-118">使用未标记为过时的名称解析方法，可以分析并解析 IPv6 地址。</span><span class="sxs-lookup"><span data-stu-id="f4662-118">Can parse IPv6 addresses and resolve IPv6 addresses using name resolution methods not marked obsolete.</span></span>|  
|<span data-ttu-id="f4662-119">是</span><span class="sxs-lookup"><span data-stu-id="f4662-119">Yes</span></span>|<span data-ttu-id="f4662-120">是</span><span class="sxs-lookup"><span data-stu-id="f4662-120">Yes</span></span>|<span data-ttu-id="f4662-121">使用所有方法（包含标记为过时的方法），可以分析并解析 IPv6 地址。</span><span class="sxs-lookup"><span data-stu-id="f4662-121">Can parse and resolve IPv6 addresses using all methods including those marked obsolete.</span></span>|  
  
 <span data-ttu-id="f4662-122">请注意，要为 System.Net 命名空间中的所有类启用 IPv6 支持，必须修改计算机配置文件或应用程序的配置文件。</span><span class="sxs-lookup"><span data-stu-id="f4662-122">Be aware that to enable the IPv6 support for all classes in the System.Net namespace, you must modify the computer configuration file or the configuration file for the application.</span></span> <span data-ttu-id="f4662-123">应用程序的配置文件优先于计算机配置文件。</span><span class="sxs-lookup"><span data-stu-id="f4662-123">The configuration file for an application has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="f4662-124">有关如何修改计算机配置文件 machine.config 以启用 Ipv6 支持的示例，请参阅[如何：修改计算机配置文件以启用 Ipv6 支持](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md)。</span><span class="sxs-lookup"><span data-stu-id="f4662-124">For an example of how to modify the computer configuration file, *machine.config*, to enable Ipv6 support see, [How to: Modify the Computer Configuration File to Enable Ipv6 Support](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span> <span data-ttu-id="f4662-125">此外，请确保操作系统启用了 IPv6 支持。</span><span class="sxs-lookup"><span data-stu-id="f4662-125">Also, ensure that the IPv6 support is enabled for the operating system.</span></span>  
  
 <span data-ttu-id="f4662-126">.NET Framework 在配置文件中具有如下配置开关设置</span><span class="sxs-lookup"><span data-stu-id="f4662-126">The .NET Framework has a configuration switch set in a configuration file as follows</span></span>  
  
```xml  
<system.net>  
  ...  
  <settings>  
    ...  
    <ipv6 enabled="true"/>  
    ...  
  </settings>  
  ...  
</system.net>  
```  
  
 <span data-ttu-id="f4662-127">对于 .NET Framework 1.1 及更早版本，ipv6 enabled 配置开关的值指定 <xref:System.Net.Dns?displayProperty=nameWithType> 类的成员是否返回 IPv6 地址。</span><span class="sxs-lookup"><span data-stu-id="f4662-127">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="f4662-128">对于 .NET Framework 2.0 和更高版本，如果 Windows 支持 IPv6，则 <xref:System.Net.Dns?displayProperty=nameWithType> 类的成员（例如 <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> 方法）将返回含一个限制的 IPv6 地址。</span><span class="sxs-lookup"><span data-stu-id="f4662-128">For .NET Framework version 2.0 and later, if Windows supports IPv6, then members of the <xref:System.Net.Dns?displayProperty=nameWithType> class, (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="f4662-129">DNS <xref:System.Net.Dns?displayProperty=nameWithType> 的已过时成员（例如，<xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> 方法）将读取并识别配置文件中 ipv6 enabled 设置的值。</span><span class="sxs-lookup"><span data-stu-id="f4662-129">Obsolete members of the DNS <xref:System.Net.Dns?displayProperty=nameWithType> (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file for the ipv6 enabled setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4662-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="f4662-130">See also</span></span>

- [<span data-ttu-id="f4662-131">Internet 协议版本 6</span><span class="sxs-lookup"><span data-stu-id="f4662-131">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)
- [<span data-ttu-id="f4662-132">套接字</span><span class="sxs-lookup"><span data-stu-id="f4662-132">Sockets</span></span>](sockets.md)
- [<span data-ttu-id="f4662-133">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="f4662-133">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="f4662-134">\<ipv6> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="f4662-134">\<ipv6> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/ipv6-element-network-settings.md)

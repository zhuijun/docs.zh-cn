---
title: Internet 协议版本 6
description: 了解 IPv6 协议及其与 IPv4 的差异。 .NET Framework 应用程序支持 IPv6，但可能需要进行配置。
ms.date: 03/30/2017
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
ms.openlocfilehash: dd8b0b26e449fba7479d2678aff25ed49e721a90
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502387"
---
# <a name="internet-protocol-version-6"></a><span data-ttu-id="df691-104">Internet 协议版本 6</span><span class="sxs-lookup"><span data-stu-id="df691-104">Internet Protocol Version 6</span></span>
<span data-ttu-id="df691-105">Internet 协议版本 6 (IPv6) 是 Internet 的网络层的标准协议新套件。</span><span class="sxs-lookup"><span data-stu-id="df691-105">The Internet Protocol version 6 (IPv6) is a new suite of standard protocols for the network layer of the Internet.</span></span> <span data-ttu-id="df691-106">IPv6 旨在解决当前版本的 Internet 协议套件（称作 IPv4）存在的许多问题，包括地址消耗、安全性、自动配置和扩展性等问题。</span><span class="sxs-lookup"><span data-stu-id="df691-106">IPv6 is designed to solve many of the problems of the current version of the Internet Protocol suite (known as IPv4) with regard to address depletion, security, auto-configuration, extensibility, and so on.</span></span> <span data-ttu-id="df691-107">IPv6 扩展了 Internet 的功能以启用新型应用程序，包括对等和移动应用程序。</span><span class="sxs-lookup"><span data-stu-id="df691-107">IPv6 expands the capabilities of the Internet to enable new kinds of applications, including peer-to-peer and mobile applications.</span></span> <span data-ttu-id="df691-108">以下是当前 IPv4 协议的主要问题：</span><span class="sxs-lookup"><span data-stu-id="df691-108">The following are the main issues of the current IPv4 protocol:</span></span>  
  
- <span data-ttu-id="df691-109">地址空间快速消耗。</span><span class="sxs-lookup"><span data-stu-id="df691-109">Rapid depletion of the address space.</span></span>  
  
     <span data-ttu-id="df691-110">这导致使用网络地址转换器 (NAT) 将多个专用地址映射到一个公共 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="df691-110">This has led to the use of Network Address Translators (NATs) that map multiple private addresses to a single public IP address.</span></span> <span data-ttu-id="df691-111">此机制造成的主要问题是处理开销和端对端连接性的缺失。</span><span class="sxs-lookup"><span data-stu-id="df691-111">The main problems created by this mechanism are processing overhead and lack of end-to-end connectivity.</span></span>  
  
- <span data-ttu-id="df691-112">层次结构支持缺失。</span><span class="sxs-lookup"><span data-stu-id="df691-112">Lack of hierarchy support.</span></span>  
  
     <span data-ttu-id="df691-113">因其固有的预定义类组织，IPv4 缺乏真正的层次结构支持。</span><span class="sxs-lookup"><span data-stu-id="df691-113">Because of its inherent predefined class organization, IPv4 lacks true hierarchical support.</span></span> <span data-ttu-id="df691-114">无法通过真正地映射网络拓扑的方式构成 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="df691-114">It is impossible to structure the IP addresses in a way that truly maps the network topology.</span></span> <span data-ttu-id="df691-115">由于存在这种重大的设计缺陷，所以需要通过大型路由表将 IPv4 数据包传送至 Internet 上的任何位置。</span><span class="sxs-lookup"><span data-stu-id="df691-115">This crucial design flaw creates the need for large routing tables to deliver IPv4 packets to any location on the Internet.</span></span>  
  
- <span data-ttu-id="df691-116">复杂的网络配置。</span><span class="sxs-lookup"><span data-stu-id="df691-116">Complex network configuration.</span></span>  
  
     <span data-ttu-id="df691-117">对于 IPv4，地址必须以静态方式分配，或使用配置协议，如 DHCP。</span><span class="sxs-lookup"><span data-stu-id="df691-117">With IPv4, addresses must be assigned statically or using a configuration protocol such as DHCP.</span></span> <span data-ttu-id="df691-118">在理想情况下，主机不需要依靠 DHCP 基础结构的管理。</span><span class="sxs-lookup"><span data-stu-id="df691-118">In an ideal situation, hosts would not have to rely on the administration of a DHCP infrastructure.</span></span> <span data-ttu-id="df691-119">主机可基于其所在的网络段自行配置。</span><span class="sxs-lookup"><span data-stu-id="df691-119">Instead, they would be able to configure themselves based on the network segment in which they are located.</span></span>  
  
- <span data-ttu-id="df691-120">缺乏内置身份验证和保密性。</span><span class="sxs-lookup"><span data-stu-id="df691-120">Lack of built-in authentication and confidentiality.</span></span>  
  
     <span data-ttu-id="df691-121">IPv4 不需要针对提供交换数据的身份验证或加密的机制的支持。</span><span class="sxs-lookup"><span data-stu-id="df691-121">IPv4 does not require the support for any mechanism that provides authentication or encryption of the exchanged data.</span></span> <span data-ttu-id="df691-122">IPv6 在这一方面作出更改。</span><span class="sxs-lookup"><span data-stu-id="df691-122">This changes with IPv6.</span></span> <span data-ttu-id="df691-123">Internet 协议安全 (IPSec)是 IPv6 支持要求。</span><span class="sxs-lookup"><span data-stu-id="df691-123">Internet Protocol security (IPSec) is an IPv6 support requirement.</span></span>  
  
 <span data-ttu-id="df691-124">新协议套件必须满足以下基本需求：</span><span class="sxs-lookup"><span data-stu-id="df691-124">A new protocol suite must satisfy the following basic requirements:</span></span>  
  
- <span data-ttu-id="df691-125">低开销的大规模路由和寻址。</span><span class="sxs-lookup"><span data-stu-id="df691-125">Large-scale routing and addressing with low overhead.</span></span>  
  
- <span data-ttu-id="df691-126">针对各种连接情况进行自动配置。</span><span class="sxs-lookup"><span data-stu-id="df691-126">Auto-configuration for various connecting situations.</span></span>  
  
- <span data-ttu-id="df691-127">内置身份验证和保密性。</span><span class="sxs-lookup"><span data-stu-id="df691-127">Built-in authentication and confidentiality.</span></span>  
  
 <span data-ttu-id="df691-128">有关详细信息，请参阅 [IPv6 寻址](ipv6-addressing.md)、[IPv6 路由](ipv6-routing.md)、[IPv6 自动配置](ipv6-auto-configuration.md)、[启用和禁用 IPv6](enabling-and-disabling-ipv6.md) 以及[如何：修改计算机配置文件以启用 IPv6 支持](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md)。</span><span class="sxs-lookup"><span data-stu-id="df691-128">For more information, see [IPv6 Addressing](ipv6-addressing.md), [IPv6 Routing](ipv6-routing.md), [IPv6 Auto-Configuration](ipv6-auto-configuration.md), [Enabling and Disabling IPv6](enabling-and-disabling-ipv6.md), and [How to: Modify the Computer Configuration File to Enable IPv6 Support](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="df691-129">reference</span><span class="sxs-lookup"><span data-stu-id="df691-129">References</span></span>  
 <span data-ttu-id="df691-130">以下是可以在 [Internet 工程任务组 (IETF)](https://www.ietf.org/) 找到的精选 RFC 文档：</span><span class="sxs-lookup"><span data-stu-id="df691-130">The following are selected RFC documents that you can find at the [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website:</span></span>  
  
- <span data-ttu-id="df691-131">RFC 1287，面向未来的 Internet 体系结构。</span><span class="sxs-lookup"><span data-stu-id="df691-131">RFC 1287, Towards the Future Internet Architecture.</span></span>  
  
- <span data-ttu-id="df691-132">RFC 1454，下一 IP 版本的建议的比较。</span><span class="sxs-lookup"><span data-stu-id="df691-132">RFC 1454, Comparison of Proposals for Next Version of IP.</span></span>  
  
- <span data-ttu-id="df691-133">RFC 2373，IP 版本 6 寻址体系结构。</span><span class="sxs-lookup"><span data-stu-id="df691-133">RFC 2373, IP Version 6 Addressing Architecture.</span></span>  
  
- <span data-ttu-id="df691-134">RFC 2374，IPv6 可聚合全局单播地址格式。</span><span class="sxs-lookup"><span data-stu-id="df691-134">RFC 2374, An IPv6 Aggregatable Global Unicast Address Format.</span></span>  
  
 <span data-ttu-id="df691-135">还可以在 [IP 版本 6 (IPv6)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29) 中找到 IPv6 相关信息。</span><span class="sxs-lookup"><span data-stu-id="df691-135">You can also find IPv6-related information on the [IP Version 6 (IPv6)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df691-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="df691-136">See also</span></span>

- [<span data-ttu-id="df691-137">IPv6 套接字示例</span><span class="sxs-lookup"><span data-stu-id="df691-137">IPv6 Sockets Sample</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms180981%28v=vs.85%29)
- [<span data-ttu-id="df691-138">网络编程示例</span><span class="sxs-lookup"><span data-stu-id="df691-138">Network Programming Samples</span></span>](network-programming-samples.md)
- [<span data-ttu-id="df691-139">套接字</span><span class="sxs-lookup"><span data-stu-id="df691-139">Sockets</span></span>](sockets.md)

---
title: IPv6 寻址
description: 了解 Internet 协议版本 6 (IPv6) 地址，包括文本表示形式和地址类型。
ms.date: 03/30/2017
helpviewer_keywords:
- Internet Protocol version 6, addresses in
- Neighbor Discovery
- IPv6, enabling
- IPv6, mobility and
- Internet Protocol version 6, anycast addresses
- IPv6, Neighbor Discovery
- Internet Protocol version 6, auto-configuring
- Internet Protocol version 6, enabling
- IPv6, unicast addresses
- IPv6, auto-configuring
- Internet Protocol version 6, routing
- IPv6, RFC documents
- IPv6, routing
- Internet Protocol version 6, disabling
- Internet Protocol version 6, unicast addresses
- IPv6, multicast addresses
- Internet Protocol version 6, mobility and
- Internet Protocol version 6, RFC documents
- Internet Protocol version 6, Neighbor Discovery
- IPv6, anycast addresses
- Internet Protocol version 6, multicast addresses
- IPv6, addresses in
- IPv6, disabling
ms.assetid: 20a104ae-1649-4649-a005-531a5cf74c93
ms.openlocfilehash: fbf68cb5f40450c2f9ecf4900801ee55e326fcb4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502335"
---
# <a name="ipv6-addressing"></a><span data-ttu-id="f5c11-103">IPv6 寻址</span><span class="sxs-lookup"><span data-stu-id="f5c11-103">IPv6 Addressing</span></span>

<span data-ttu-id="f5c11-104">在 Internet 协议版本 6（IPv6）中，地址长度为 128 位。</span><span class="sxs-lookup"><span data-stu-id="f5c11-104">In the Internet Protocol version 6 (IPv6), addresses are 128 bits long.</span></span> <span data-ttu-id="f5c11-105">地址空间如此之大的一个原因是将可用地址细分为可以反映 Internet 拓扑的路由域的层次结构。</span><span class="sxs-lookup"><span data-stu-id="f5c11-105">One reason for such a large address space is to subdivide the available addresses into a hierarchy of routing domains that reflect the Internet's topology.</span></span> <span data-ttu-id="f5c11-106">另一个原因是映射将设备连接到网络的网络适配器（或接口）的地址。</span><span class="sxs-lookup"><span data-stu-id="f5c11-106">Another reason is to map the addresses of network adapters (or interfaces) that connect devices to the network.</span></span> <span data-ttu-id="f5c11-107">IPv6 有可以解析最低级别的地址（即网络接口级别的地址）的固有功能以及自动配置功能。</span><span class="sxs-lookup"><span data-stu-id="f5c11-107">IPv6 features an inherent capability to resolve addresses at their lowest level, which is at the network interface level, and also has auto-configuration capabilities.</span></span>

## <a name="text-representation"></a><span data-ttu-id="f5c11-108">文本表示形式</span><span class="sxs-lookup"><span data-stu-id="f5c11-108">Text Representation</span></span>

<span data-ttu-id="f5c11-109">以下是用于将 IPv6 地址表示为文本字符串的三种常规形式：</span><span class="sxs-lookup"><span data-stu-id="f5c11-109">The following are the three conventional forms used to represent the IPv6 addresses as text strings:</span></span>

- <span data-ttu-id="f5c11-110">冒号十六进制形式。</span><span class="sxs-lookup"><span data-stu-id="f5c11-110">**Colon-hexadecimal form**.</span></span> <span data-ttu-id="f5c11-111">这是首选形式 n:n:n:n:n:n:n:n。</span><span class="sxs-lookup"><span data-stu-id="f5c11-111">This is the preferred form n:n:n:n:n:n:n:n.</span></span> <span data-ttu-id="f5c11-112">每个 n 表示地址的 8 个 16 位元素之一的十六进制值。</span><span class="sxs-lookup"><span data-stu-id="f5c11-112">Each n represents the hexadecimal value of one of the eight 16-bit elements of the address.</span></span> <span data-ttu-id="f5c11-113">例如：`3FFE:FFFF:7654:FEDA:1245:BA98:3210:4562`。</span><span class="sxs-lookup"><span data-stu-id="f5c11-113">For example: `3FFE:FFFF:7654:FEDA:1245:BA98:3210:4562`.</span></span>

- <span data-ttu-id="f5c11-114">压缩形式。</span><span class="sxs-lookup"><span data-stu-id="f5c11-114">**Compressed form**.</span></span> <span data-ttu-id="f5c11-115">由于地址长度，有些地址通常包含一长串的零。</span><span class="sxs-lookup"><span data-stu-id="f5c11-115">Due to the address length, it is common to have addresses containing a long string of zeros.</span></span> <span data-ttu-id="f5c11-116">若要简化这些地址的编写，可使用压缩形式，其中 0 块的单个相邻的序列由双冒号 (::) 表示。</span><span class="sxs-lookup"><span data-stu-id="f5c11-116">To simplify writing these addresses, use the compressed form, in which a single contiguous sequence of 0 blocks are represented by a double-colon symbol (::).</span></span> <span data-ttu-id="f5c11-117">该符号在地址中只能出现一次。</span><span class="sxs-lookup"><span data-stu-id="f5c11-117">This symbol can appear only once in an address.</span></span> <span data-ttu-id="f5c11-118">例如，多播地址 `FFED:0:0:0:0:BA98:3210:4562` 的压缩形式是 `FFED::BA98:3210:4562`。</span><span class="sxs-lookup"><span data-stu-id="f5c11-118">For example, the multicast address `FFED:0:0:0:0:BA98:3210:4562` in compressed form is `FFED::BA98:3210:4562`.</span></span> <span data-ttu-id="f5c11-119">单播地址 `3FFE:FFFF:0:0:8:800:20C4:0` 的压缩形式是 `3FFE:FFFF::8:800:20C4:0`。</span><span class="sxs-lookup"><span data-stu-id="f5c11-119">The unicast address `3FFE:FFFF:0:0:8:800:20C4:0` in compressed form is `3FFE:FFFF::8:800:20C4:0`.</span></span> <span data-ttu-id="f5c11-120">环回地址 `0:0:0:0:0:0:0:1` 的压缩形式是 `::` 1。</span><span class="sxs-lookup"><span data-stu-id="f5c11-120">The loopback address `0:0:0:0:0:0:0:1` in compressed form is `::`1.</span></span> <span data-ttu-id="f5c11-121">未指定地址 `0:0:0:0:0:0:0:0` 的压缩形式是 `::`。</span><span class="sxs-lookup"><span data-stu-id="f5c11-121">The unspecified address `0:0:0:0:0:0:0:0` in compressed form is `::`.</span></span>

- <span data-ttu-id="f5c11-122">**混合形式**。</span><span class="sxs-lookup"><span data-stu-id="f5c11-122">**Mixed form**.</span></span> <span data-ttu-id="f5c11-123">此形式合并了 IPv4 和 IPv6 地址。</span><span class="sxs-lookup"><span data-stu-id="f5c11-123">This form combines IPv4 and IPv6 addresses.</span></span> <span data-ttu-id="f5c11-124">在这种情况下，地址格式为 n:n:n:n:n:n:d.d.d.d，其中每个 n 表示六个 IPv6 高序位 16 位地址元素的十六进制值，每个 d 表示一个 IPv4 地址的十进制值。</span><span class="sxs-lookup"><span data-stu-id="f5c11-124">In this case, the address format is n:n:n:n:n:n:d.d.d.d, where each n represents the hexadecimal values of the six IPv6 high-order 16-bit address elements, and each d represents the decimal value of an IPv4 address.</span></span>

## <a name="address-types"></a><span data-ttu-id="f5c11-125">地址类型</span><span class="sxs-lookup"><span data-stu-id="f5c11-125">Address Types</span></span>

<span data-ttu-id="f5c11-126">地址中的前导位定义了特定 IPv6 地址类型。</span><span class="sxs-lookup"><span data-stu-id="f5c11-126">The leading bits in the address define the specific IPv6 address type.</span></span> <span data-ttu-id="f5c11-127">包含这些前导位的可变长度字段称为格式前缀 (FP)。</span><span class="sxs-lookup"><span data-stu-id="f5c11-127">The variable-length field containing these leading bits is called a Format Prefix (FP).</span></span>

<span data-ttu-id="f5c11-128">IPv6 的单播地址分为两个部分。</span><span class="sxs-lookup"><span data-stu-id="f5c11-128">An IPv6 unicast address is divided into two parts.</span></span> <span data-ttu-id="f5c11-129">第一部分包含地址前缀，第二部分包含接口标识符。</span><span class="sxs-lookup"><span data-stu-id="f5c11-129">The first part contains the address prefix, and the second part contains the interface identifier.</span></span> <span data-ttu-id="f5c11-130">表示 IPv6 地址/前缀组合的简洁方法如下：ipv6-address/prefix-length。</span><span class="sxs-lookup"><span data-stu-id="f5c11-130">A concise way to express an IPv6 address/prefix combination is as follows: ipv6-address/prefix-length.</span></span>

<span data-ttu-id="f5c11-131">以下是具有 64 位前缀的地址示例。</span><span class="sxs-lookup"><span data-stu-id="f5c11-131">The following is an example of an address with a 64-bit prefix.</span></span>

<span data-ttu-id="f5c11-132">`3FFE:FFFF:0:CD30:0:0:0:0/64`。</span><span class="sxs-lookup"><span data-stu-id="f5c11-132">`3FFE:FFFF:0:CD30:0:0:0:0/64`.</span></span>

<span data-ttu-id="f5c11-133">本示例中的前缀是 `3FFE:FFFF:0:CD30`。</span><span class="sxs-lookup"><span data-stu-id="f5c11-133">The prefix in this example is `3FFE:FFFF:0:CD30`.</span></span> <span data-ttu-id="f5c11-134">此地址也可以采用压缩形式编写为 `3FFE:FFFF:0:CD30::/64`。</span><span class="sxs-lookup"><span data-stu-id="f5c11-134">The address can also be written in a compressed form, as `3FFE:FFFF:0:CD30::/64`.</span></span>

<span data-ttu-id="f5c11-135">IPv6 定义以下地址类型：</span><span class="sxs-lookup"><span data-stu-id="f5c11-135">IPv6 defines the following address types:</span></span>

- <span data-ttu-id="f5c11-136">单播地址。</span><span class="sxs-lookup"><span data-stu-id="f5c11-136">**Unicast address**.</span></span> <span data-ttu-id="f5c11-137">单个接口的标识符。</span><span class="sxs-lookup"><span data-stu-id="f5c11-137">An identifier for a single interface.</span></span> <span data-ttu-id="f5c11-138">发送到此地址的数据包将会发送到已标识接口。</span><span class="sxs-lookup"><span data-stu-id="f5c11-138">A packet sent to this address is delivered to the identified interface.</span></span> <span data-ttu-id="f5c11-139">可通过高序位八进制数的值，区分单播地址和多播地址。</span><span class="sxs-lookup"><span data-stu-id="f5c11-139">The unicast addresses are distinguished from the multicast addresses by the value of the high-order octet.</span></span> <span data-ttu-id="f5c11-140">多播地址的高序位八进制数具有 FF 的十六进制值。</span><span class="sxs-lookup"><span data-stu-id="f5c11-140">The multicast addresses' high-order octet has the hexadecimal value of FF.</span></span> <span data-ttu-id="f5c11-141">此八进制数的任何其他值标识单播地址。</span><span class="sxs-lookup"><span data-stu-id="f5c11-141">Any other value for this octet identifies a unicast address.</span></span> <span data-ttu-id="f5c11-142">以下是不同类型的单播地址：</span><span class="sxs-lookup"><span data-stu-id="f5c11-142">The following are different types of unicast addresses:</span></span>

  - <span data-ttu-id="f5c11-143">链接本地地址。</span><span class="sxs-lookup"><span data-stu-id="f5c11-143">**Link-local addresses**.</span></span> <span data-ttu-id="f5c11-144">这些地址用于单个链接，并且具有以下格式：FE80::InterfaceID。</span><span class="sxs-lookup"><span data-stu-id="f5c11-144">These addresses are used on a single link and have the following format: FE80::*InterfaceID*.</span></span> <span data-ttu-id="f5c11-145">链接本地地址用于链接的节点之间以实现自动地址配置、邻居发现，或者用于不存在路由器的情况。</span><span class="sxs-lookup"><span data-stu-id="f5c11-145">Link-local addresses are used between nodes on a link for auto-address configuration, neighbor discovery, or when no routers are present.</span></span> <span data-ttu-id="f5c11-146">链接本地地址主要用于启动时，以及系统尚未获取较大范围地址时。</span><span class="sxs-lookup"><span data-stu-id="f5c11-146">A link-local address is used primarily at startup and when the system has not yet acquired addresses of larger scope.</span></span>

  - <span data-ttu-id="f5c11-147">站点本地地址。</span><span class="sxs-lookup"><span data-stu-id="f5c11-147">**Site-local addresses**.</span></span> <span data-ttu-id="f5c11-148">这些地址用于单个站点，具有以下格式：FEC0::SubnetID:InterfaceID 。</span><span class="sxs-lookup"><span data-stu-id="f5c11-148">These addresses are used on a single site and have the following format: FEC0::*SubnetID*:*InterfaceID*.</span></span> <span data-ttu-id="f5c11-149">站点本地地址用于在站点内寻址，无需全局前缀。</span><span class="sxs-lookup"><span data-stu-id="f5c11-149">The site-local addresses are used for addressing inside a site without the need for a global prefix.</span></span>

  - <span data-ttu-id="f5c11-150">全局 IPv6 单播地址。</span><span class="sxs-lookup"><span data-stu-id="f5c11-150">**Global IPv6 unicast addresses**.</span></span> <span data-ttu-id="f5c11-151">这些地址可以在 Internet 上使用，并具有以下格式：010 (FP，3 位) TLA ID (13 位)预留(8 位) NLA ID (24 位) SLA ID (16 位) InterfaceID (64 位)</span><span class="sxs-lookup"><span data-stu-id="f5c11-151">These addresses can be used across the Internet and have the following format: 010(FP, 3 bits) TLA ID (13 bits) Reserved (8 bits) NLA ID (24 bits) SLA ID (16 bits) *InterfaceID* (64 bits).</span></span>

- <span data-ttu-id="f5c11-152">多播地址。</span><span class="sxs-lookup"><span data-stu-id="f5c11-152">**Multicast address**.</span></span> <span data-ttu-id="f5c11-153">一组接口（通常属于不同节点）的标识符。</span><span class="sxs-lookup"><span data-stu-id="f5c11-153">An identifier for a set of interfaces (typically belonging to different nodes).</span></span> <span data-ttu-id="f5c11-154">发送到此地址的数据包将发送到由该地址标识的所有接口。</span><span class="sxs-lookup"><span data-stu-id="f5c11-154">A packet sent to this address is delivered to all the interfaces identified by the address.</span></span> <span data-ttu-id="f5c11-155">多播地址类型取代了 IPv4 广播地址。</span><span class="sxs-lookup"><span data-stu-id="f5c11-155">The multicast address types supersede the IPv4 broadcast addresses.</span></span>

- <span data-ttu-id="f5c11-156">任播地址。</span><span class="sxs-lookup"><span data-stu-id="f5c11-156">**Anycast address**.</span></span> <span data-ttu-id="f5c11-157">一组接口（通常属于不同节点）的标识符。</span><span class="sxs-lookup"><span data-stu-id="f5c11-157">An identifier for a set of interfaces (typically belonging to different nodes).</span></span> <span data-ttu-id="f5c11-158">发送到此地址的数据包将发送到由该地址标识的仅一个接口。</span><span class="sxs-lookup"><span data-stu-id="f5c11-158">A packet sent to this address is delivered to only one interface identified by the address.</span></span> <span data-ttu-id="f5c11-159">这是路由指标标识的最近接口。</span><span class="sxs-lookup"><span data-stu-id="f5c11-159">This is the nearest interface as identified by routing metrics.</span></span> <span data-ttu-id="f5c11-160">任播地址取自单播地址空间，无法从语法上进行区分。</span><span class="sxs-lookup"><span data-stu-id="f5c11-160">Anycast addresses are taken from the unicast address space and are not syntactically distinguishable.</span></span> <span data-ttu-id="f5c11-161">寻址的接口根据其配置区分单播和任播地址。</span><span class="sxs-lookup"><span data-stu-id="f5c11-161">The addressed interface performs the distinction between unicast and anycast addresses as a function of its configuration.</span></span>

<span data-ttu-id="f5c11-162">通常，节点始终具有链接本地地址。</span><span class="sxs-lookup"><span data-stu-id="f5c11-162">In general, a node always has a link-local address.</span></span> <span data-ttu-id="f5c11-163">它可能具有站点本地地址和一个或多个全局地址。</span><span class="sxs-lookup"><span data-stu-id="f5c11-163">It might have a site-local address and one or more global addresses.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5c11-164">请参阅</span><span class="sxs-lookup"><span data-stu-id="f5c11-164">See also</span></span>

- [<span data-ttu-id="f5c11-165">Internet 协议版本 6</span><span class="sxs-lookup"><span data-stu-id="f5c11-165">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)
- [<span data-ttu-id="f5c11-166">套接字</span><span class="sxs-lookup"><span data-stu-id="f5c11-166">Sockets</span></span>](sockets.md)

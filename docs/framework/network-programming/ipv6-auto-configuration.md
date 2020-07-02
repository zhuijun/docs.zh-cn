---
title: IPv6 自动配置
description: 了解 IPv6 如何支持节点即插即用，其中节点加入 IPv6 网络并在无人工干预的情况下进行配置。
ms.date: 03/30/2017
ms.assetid: 581c1d21-1013-43a3-bf3e-2d9ead62b79c
ms.openlocfilehash: 9d65bc453478ac4679556e931b1758c18cfedcf3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502322"
---
# <a name="ipv6-auto-configuration"></a><span data-ttu-id="529a6-103">IPv6 自动配置</span><span class="sxs-lookup"><span data-stu-id="529a6-103">IPv6 Auto-Configuration</span></span>
<span data-ttu-id="529a6-104">IPv6 的一个重要目标是支持节点即插即用。</span><span class="sxs-lookup"><span data-stu-id="529a6-104">One important goal for IPv6 is to support node Plug and Play.</span></span> <span data-ttu-id="529a6-105">也就是说，可以将节点插入 IPv6 网络，让其自动进行配置，无需任何人为干预。</span><span class="sxs-lookup"><span data-stu-id="529a6-105">That is, it should be possible to plug a node into an IPv6 network and have it automatically configured without any human intervention.</span></span>  
  
## <a name="type-of-auto-configuration"></a><span data-ttu-id="529a6-106">自动配置类型</span><span class="sxs-lookup"><span data-stu-id="529a6-106">Type of Auto-Configuration</span></span>  
 <span data-ttu-id="529a6-107">IPv6 支持以下自动配置类型：</span><span class="sxs-lookup"><span data-stu-id="529a6-107">IPv6 supports the following types of auto-configuration:</span></span>  
  
- <span data-ttu-id="529a6-108">有状态自动配置。</span><span class="sxs-lookup"><span data-stu-id="529a6-108">**Stateful auto-configuration**.</span></span> <span data-ttu-id="529a6-109">这种类型的配置需要一定程度的人为干预，因其需要 IPv6 动态主机配置协议 (DHCPv6) 服务器来安装和管理节点。</span><span class="sxs-lookup"><span data-stu-id="529a6-109">This type of configuration requires a certain level of human intervention because it needs a Dynamic Host Configuration Protocol for IPv6 (DHCPv6) server for the installation and administration of the nodes.</span></span> <span data-ttu-id="529a6-110">DHCPv6 服务器保存向其提供配置信息的节点列表。</span><span class="sxs-lookup"><span data-stu-id="529a6-110">The DHCPv6 server keeps a list of nodes to which it supplies configuration information.</span></span> <span data-ttu-id="529a6-111">它还维护状态信息，这样服务器知道每个地址的使用时间，以及何时可用于重新分配。</span><span class="sxs-lookup"><span data-stu-id="529a6-111">It also maintains state information so the server knows how long each address is in use, and when it might be available for reassignment.</span></span>  
  
- <span data-ttu-id="529a6-112">无状态自动配置。</span><span class="sxs-lookup"><span data-stu-id="529a6-112">**Stateless auto-configuration**.</span></span> <span data-ttu-id="529a6-113">这种配置类型适用于小型组织和个人。</span><span class="sxs-lookup"><span data-stu-id="529a6-113">This type of configuration is suitable for small organizations and individuals.</span></span> <span data-ttu-id="529a6-114">这种情况下，每个主机通过接收的路由器播发的内容确定其地址。</span><span class="sxs-lookup"><span data-stu-id="529a6-114">In this case, each host determines its addresses from the contents of received router advertisements.</span></span> <span data-ttu-id="529a6-115">使用 IEEE EUI-64 标准来定义地址的网络 ID 部分，可以合理地假定链接上主机地址的唯一性。</span><span class="sxs-lookup"><span data-stu-id="529a6-115">Using the IEEE EUI-64 standard to define the network ID portion of the address, it is reasonable to assume the uniqueness of the host address on the link.</span></span>  
  
 <span data-ttu-id="529a6-116">无论如何确定地址，节点必须验证可能的地址对于本地链接是否唯一。</span><span class="sxs-lookup"><span data-stu-id="529a6-116">Regardless of how the address is determined, the node must verify that its potential address is unique to the local link.</span></span> <span data-ttu-id="529a6-117">通过向可能的地址发送邻居请求消息可完成此操作。</span><span class="sxs-lookup"><span data-stu-id="529a6-117">This is done by sending a neighbor solicitation message to the potential address.</span></span> <span data-ttu-id="529a6-118">如果节点收到任何响应，就知道该地址已在使用，并且必须确定其他地址。</span><span class="sxs-lookup"><span data-stu-id="529a6-118">If the node receives any response, it knows that the address is already in use and must determine another address.</span></span>  
  
## <a name="ipv6-mobility"></a><span data-ttu-id="529a6-119">IPv6 移动性</span><span class="sxs-lookup"><span data-stu-id="529a6-119">IPv6 Mobility</span></span>  
 <span data-ttu-id="529a6-120">移动设备的广泛应用催生了新的要求：设备必须能够随意改变 IPv6 Internet 上的位置，但是仍然保持现有连接。</span><span class="sxs-lookup"><span data-stu-id="529a6-120">The proliferation of mobile devices has introduced a new requirement: A device must be able to arbitrarily change locations on the IPv6 Internet and still maintain existing connections.</span></span> <span data-ttu-id="529a6-121">为实现此功能，向移动节点分配一个始终可以到达的主地址。</span><span class="sxs-lookup"><span data-stu-id="529a6-121">To provide this functionality, a mobile node is assigned a home address at which it can always be reached.</span></span> <span data-ttu-id="529a6-122">当移动节点在其中时，它连接到主链接并使用其主地址。</span><span class="sxs-lookup"><span data-stu-id="529a6-122">When the mobile node is at home, it connects to the home link and uses its home address.</span></span> <span data-ttu-id="529a6-123">当移动节点离开时，主代理（通常是路由器）在移动节点和其正与之通信的节点之间中继消息。</span><span class="sxs-lookup"><span data-stu-id="529a6-123">When the mobile node is away from home, a home agent, which is usually a router, relays messages between the mobile node and nodes with which it is communicating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="529a6-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="529a6-124">See also</span></span>

- [<span data-ttu-id="529a6-125">Internet 协议版本 6</span><span class="sxs-lookup"><span data-stu-id="529a6-125">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)
- [<span data-ttu-id="529a6-126">套接字</span><span class="sxs-lookup"><span data-stu-id="529a6-126">Sockets</span></span>](sockets.md)

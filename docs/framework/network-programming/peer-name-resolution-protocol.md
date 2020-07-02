---
title: 对等名称解析协议
description: 了解对等名称解析协议 (PNRP)，一种安全、可缩放的动态名称注册和名称解析协议。
ms.date: 03/30/2017
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
ms.openlocfilehash: 72eb63c2c90f398c515d77cd2b2d693237e533a5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502218"
---
# <a name="peer-name-resolution-protocol"></a><span data-ttu-id="528dd-103">对等名称解析协议</span><span class="sxs-lookup"><span data-stu-id="528dd-103">Peer Name Resolution Protocol</span></span>
<span data-ttu-id="528dd-104">在对等环境中，对等机使用特定的名称解析系统从名称或其他类型的标识符解析彼此的网络位置（地址、协议和端口）。</span><span class="sxs-lookup"><span data-stu-id="528dd-104">In peer-to-peer environments, peers use specific name resolution systems to resolve each other's network locations (addresses, protocols, and ports) from names or other types of identifiers.</span></span> <span data-ttu-id="528dd-105">过去，由于本质上的短暂性连接以及域名系统 (DNS) 内的其他缺陷，造成对等名称解析十分复杂。</span><span class="sxs-lookup"><span data-stu-id="528dd-105">In the past, peer name resolution has been complicated by the inherently transient connectivity as well as other shortcomings within the Domain Name System (DNS).</span></span>  
  
 <span data-ttu-id="528dd-106">Microsoft® Windows® 对等网络平台使用对等名称解析协议 (PNRP) 解决了这个问题，该协议是一个安全、可缩放的动态名称注册和名称解析协议，最早开发用于 Windows XP，然后在 Windows Vista™ 中得到升级。</span><span class="sxs-lookup"><span data-stu-id="528dd-106">The Microsoft® Windows® Peer-to-Peer Networking platform solves this problem with the Peer Name Resolution Protocol (PNRP), a secure, scalable, and dynamic name registration and name resolution protocol first developed for Windows XP and then upgraded in Windows Vista™.</span></span> <span data-ttu-id="528dd-107">PNRP 与传统的名称解析系统相比有很大不同，为应用程序开发者带来了振奋人心的全新可能。</span><span class="sxs-lookup"><span data-stu-id="528dd-107">PNRP works very differently from traditional name resolution systems, opening up exciting new possibilities for application developers.</span></span>  
  
 <span data-ttu-id="528dd-108">通过 PNRP，对等名称可以应用于计算机或者计算机上单独的应用程序和服务。</span><span class="sxs-lookup"><span data-stu-id="528dd-108">With PNRP, peer names can be applied to the machine, or individual applications or services on the machine.</span></span> <span data-ttu-id="528dd-109">对等名称解析包括地址、端口，以及可能的扩展有效负载。</span><span class="sxs-lookup"><span data-stu-id="528dd-109">A peer name resolution includes an address, port, and possibly an extended payload.</span></span> <span data-ttu-id="528dd-110">此系统的优势在于容错度、无瓶颈以及绝不返回过时地址的名称解析；这使得该协议成为定位移动用户的卓越解决方案。</span><span class="sxs-lookup"><span data-stu-id="528dd-110">Benefits of this system include fault tolerance, no bottlenecks, and name resolutions that will never return stale addresses; making the protocol an excellent solution for locating mobile users.</span></span>  
  
 <span data-ttu-id="528dd-111">在安全性方面，对等名称可以发布为安全的（受保护的）或不安全的（不受保护的）。</span><span class="sxs-lookup"><span data-stu-id="528dd-111">In terms of security, peer names can be published as secured (protected) or unsecured (unprotected).</span></span> <span data-ttu-id="528dd-112">PNRP 使用公钥加密保护安全对等名称免遭欺骗；计算机和服务都可使用 PNRP 命名。</span><span class="sxs-lookup"><span data-stu-id="528dd-112">PNRP uses public key cryptography to protect secure peer names against spoofing; both computers and services can be named with PNRP.</span></span>  
  
<span data-ttu-id="528dd-113">对等名称解析协议具备以下属性：</span><span class="sxs-lookup"><span data-stu-id="528dd-113">The Peer Name Resolution Protocol demonstrates the following properties:</span></span>  
  
- <span data-ttu-id="528dd-114">分布式的，且几乎完全无服务器的。</span><span class="sxs-lookup"><span data-stu-id="528dd-114">Distributed and almost entirely serverless.</span></span> <span data-ttu-id="528dd-115">只有在启动进程时才需要服务器。</span><span class="sxs-lookup"><span data-stu-id="528dd-115">Servers are only required for the bootstrapping process.</span></span>  
  
- <span data-ttu-id="528dd-116">安全的名称发布，无需第三方介入。</span><span class="sxs-lookup"><span data-stu-id="528dd-116">Secure name publication without the involvement of third parties.</span></span> <span data-ttu-id="528dd-117">和 DNS 名称发布不同，PNRP 名称发布是即时的，且没有财务成本。</span><span class="sxs-lookup"><span data-stu-id="528dd-117">Unlike DNS name publication, PNRP name publication is instantaneous and without financial cost.</span></span>  
  
- <span data-ttu-id="528dd-118">PNRP 实时更新，以便防止解析过时地址。</span><span class="sxs-lookup"><span data-stu-id="528dd-118">PNRP updates in real-time, which prevents the resolution of stale addresses.</span></span>  
  
- <span data-ttu-id="528dd-119">通过 PNRP 解析名称远不止适用于计算机，它还允许对服务进行名称解析。</span><span class="sxs-lookup"><span data-stu-id="528dd-119">The resolution of names via PNRP extends beyond computers by also allowing name resolution for services.</span></span>  
  
## <a name="the-systemnetpeertopeer-namespace"></a><span data-ttu-id="528dd-120">System.Net.PeerToPeer 命名空间</span><span class="sxs-lookup"><span data-stu-id="528dd-120">The System.Net.PeerToPeer namespace</span></span>  
  
- <span data-ttu-id="528dd-121">PNRP 功能由 .NET Framework 版本 3.5 内的 <xref:System.Net.PeerToPeer> 命名空间定义。</span><span class="sxs-lookup"><span data-stu-id="528dd-121">PNRP functionality is defined by the <xref:System.Net.PeerToPeer> namespace within the .NET Framework version 3.5.</span></span> <span data-ttu-id="528dd-122">它提供的类型集可以用于注册可用的 PNRP 服务并解析其对等名称。</span><span class="sxs-lookup"><span data-stu-id="528dd-122">It provides a set of types that can be used to register and resolve peer names with an available PNRP service.</span></span>  
  
- <span data-ttu-id="528dd-123">（可以使用 <xref:System.ServiceModel.PeerResolvers> 命名空间中提供的类型创建并实例化 PNRP 和自定义对等解析程序。）</span><span class="sxs-lookup"><span data-stu-id="528dd-123">(PNRP and custom peer resolvers can be created and instantiated using the types provided in the <xref:System.ServiceModel.PeerResolvers> namespace.)</span></span>  
  
- <span data-ttu-id="528dd-124">有如下基本类型可用于注册可用的 PNRP 服务并解析其名称：</span><span class="sxs-lookup"><span data-stu-id="528dd-124">The basic types used to register and resolve names with an available PNRP service are as follows:</span></span>  
  
- <span data-ttu-id="528dd-125"><xref:System.Net.PeerToPeer.Cloud>：定义描述可用 PNRP 云的信息，包括其范围。</span><span class="sxs-lookup"><span data-stu-id="528dd-125"><xref:System.Net.PeerToPeer.Cloud>: Defines the information describing an available PNRP cloud, including its scope.</span></span>  
  
- <span data-ttu-id="528dd-126"><xref:System.Net.PeerToPeer.PeerName>：定义可用于在云中注册并随后解析对等机的对等名称。</span><span class="sxs-lookup"><span data-stu-id="528dd-126"><xref:System.Net.PeerToPeer.PeerName>: Defines a peer name that can be used to register and subsequently resolve a peer within a cloud.</span></span>  
  
- <span data-ttu-id="528dd-127"><xref:System.Net.PeerToPeer.PeerNameRecord>：定义 PNRP 云中包含对等机注册信息在内的记录，其中包括可联系到该对等机的网络终结点。</span><span class="sxs-lookup"><span data-stu-id="528dd-127"><xref:System.Net.PeerToPeer.PeerNameRecord>: Defines the record in PNRP cloud that contains the registration information for a peer, which includes the network endpoints at which the peer can be contacted.</span></span>  
  
- <span data-ttu-id="528dd-128"><xref:System.Net.PeerToPeer.PeerNameRegistration>：定义对等名称的注册进程，包括开始和结束对等名称解析的方法。</span><span class="sxs-lookup"><span data-stu-id="528dd-128"><xref:System.Net.PeerToPeer.PeerNameRegistration>: Defines the registration process for a peer name, including methods to start and stop peer name registration.</span></span>  
  
- <span data-ttu-id="528dd-129"><xref:System.Net.PeerToPeer.PeerNameResolver>：定义将对等名称解析到其网络终结点的进程，包括解析的同步和异步方法。</span><span class="sxs-lookup"><span data-stu-id="528dd-129"><xref:System.Net.PeerToPeer.PeerNameResolver>: Defines the process for resolving a peer name to its network endpoint(s), including both synchronous and asynchronous methods for resolution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="528dd-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="528dd-130">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers>
- <xref:System.Net.PeerToPeer>
- [<span data-ttu-id="528dd-131">网络编程示例</span><span class="sxs-lookup"><span data-stu-id="528dd-131">Network Programming Samples</span></span>](network-programming-samples.md)

<!-- to-do: review sample links
- [PeerToPeer Technology Sample](https://go.microsoft.com/fwlink/?LinkID=179571)
-->

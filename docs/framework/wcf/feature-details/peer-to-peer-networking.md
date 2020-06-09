---
title: 对等网络
ms.date: 03/30/2017
ms.assetid: ad6cb67b-fd1c-4ca1-a767-b410da2e16ca
ms.openlocfilehash: 42bda754afa58354c087e587e500bebfe72169f4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600758"
---
# <a name="peer-to-peer-networking"></a><span data-ttu-id="db335-102">对等网络</span><span class="sxs-lookup"><span data-stu-id="db335-102">Peer-to-Peer Networking</span></span>
<span data-ttu-id="db335-103">对等通道是 Windows Communication Foundation （WCF）中的一种多方对等（P2P）通信技术。</span><span class="sxs-lookup"><span data-stu-id="db335-103">Peer Channel is a multiparty, peer-to-peer (P2P) communication technology in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="db335-104">它为应用程序开发人员提供了基于消息的、安全且可伸缩的 P2P 信道。</span><span class="sxs-lookup"><span data-stu-id="db335-104">It provides a secure and scalable message-based P2P communication channel for application developers.</span></span> <span data-ttu-id="db335-105">可从对等通道中获益的多方应用程序的一个常见示例是协作应用程序，例如聊天应用程序，其中一组人以对等方式（无需服务器）相互聊天。</span><span class="sxs-lookup"><span data-stu-id="db335-105">One common example of a multiparty application that can benefit from Peer Channel is a collaborative application, such as chat, where a group of people chat with one another in a peer-to-peer manner without servers.</span></span> <span data-ttu-id="db335-106">对等通道可为消费者和企业方案启用 P2P 协作、内容分发、负载平衡和分布式处理。</span><span class="sxs-lookup"><span data-stu-id="db335-106">Peer Channel enables P2P collaboration, content distribution, load balancing, and distributed processing for both consumer and enterprise scenarios.</span></span>  
  
 <span data-ttu-id="db335-107">默认情况下，在 Windows Vista 上启用对等通道，这与 WCF 完全相同。</span><span class="sxs-lookup"><span data-stu-id="db335-107">Peer Channel is enabled by default on Windows Vista, as is all of WCF.</span></span> <span data-ttu-id="db335-108">若要访问对等通道类，请在项目中添加对 System.ServiceModel.dll 的引用。</span><span class="sxs-lookup"><span data-stu-id="db335-108">To access Peer Channel classes, add references to System.ServiceModel.dll to your project.</span></span>  
  
 <span data-ttu-id="db335-109">以下各节包含有关对等网络以及使用对等通道类来创建启用对等的网络应用程序的信息。</span><span class="sxs-lookup"><span data-stu-id="db335-109">The following sections contain information about peer-to-peer networking and the use of Peer Channel classes to create peer-enabled network applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="db335-110">本节内容</span><span class="sxs-lookup"><span data-stu-id="db335-110">In This Section</span></span>  
 <span data-ttu-id="db335-111">[对等通道方案](peer-channel-scenarios.md)：介绍对等通道 api 支持的开发方案，如发布/订阅消息传递、协作、分布式处理和游戏。</span><span class="sxs-lookup"><span data-stu-id="db335-111">[Peer Channel Scenarios](peer-channel-scenarios.md):  Describes development scenarios supported by the Peer Channel APIs, such as publication/subscription messaging, collaboration, distributed processing, and gaming.</span></span>  
  
 <span data-ttu-id="db335-112">[对等通道概念](peer-channel-concepts.md)：介绍对等网格、对等节点、对等通道安全和对等解析程序。</span><span class="sxs-lookup"><span data-stu-id="db335-112">[Peer Channel Concepts](peer-channel-concepts.md):  Describes Peer Meshes, Peer Nodes, Peer Channel security, and Peer Resolvers.</span></span>  
  
 <span data-ttu-id="db335-113">[生成对等通道应用程序](building-a-peer-channel-application.md)：提供有关开发对等通道应用程序的指导。</span><span class="sxs-lookup"><span data-stu-id="db335-113">[Building a Peer Channel Application](building-a-peer-channel-application.md):  Provides guidance on developing Peer Channel applications.</span></span>  
  
## <a name="peer-channel-code-examples"></a><span data-ttu-id="db335-114">对等通道代码示例</span><span class="sxs-lookup"><span data-stu-id="db335-114">Peer Channel Code Examples</span></span>  
 <span data-ttu-id="db335-115">[对等通道自定义对等解析程序](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751466(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="db335-115">[Peer Channel Custom Peer Resolver](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751466(v=vs.90))</span></span>  
  
## <a name="peer-channel-team-blog"></a><span data-ttu-id="db335-116">对等通道团队博客</span><span class="sxs-lookup"><span data-stu-id="db335-116">Peer Channel Team blog</span></span>  
 [<span data-ttu-id="db335-117">对等通道团队博客</span><span class="sxs-lookup"><span data-stu-id="db335-117">Peer Channel Team Blog</span></span>](https://docs.microsoft.com/archive/blogs/peerchan/)

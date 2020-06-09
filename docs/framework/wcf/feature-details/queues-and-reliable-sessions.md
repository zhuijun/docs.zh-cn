---
title: 队列和可靠会话
ms.date: 03/30/2017
ms.assetid: 7e794d03-141c-45ed-b6b1-6c0e104c1464
ms.openlocfilehash: af45fd86f673d0cc296f6593d9d5709d3e2b616e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596742"
---
# <a name="queues-and-reliable-sessions"></a><span data-ttu-id="7951b-102">队列和可靠会话</span><span class="sxs-lookup"><span data-stu-id="7951b-102">Queues and Reliable Sessions</span></span>
<span data-ttu-id="7951b-103">队列和可靠会话是实现可靠消息传递的 Windows Communication Foundation （WCF）功能。</span><span class="sxs-lookup"><span data-stu-id="7951b-103">Queues and reliable sessions are the Windows Communication Foundation (WCF) features that implement reliable messaging.</span></span> <span data-ttu-id="7951b-104">本节中包含的主题讨论 WCF 可靠的消息传送功能。</span><span class="sxs-lookup"><span data-stu-id="7951b-104">The topics contained in this section discuss the WCF reliable messaging features.</span></span>  
  
 <span data-ttu-id="7951b-105">可靠消息传递是指可靠消息源（称为“源”）如何将消息可靠地传送到可靠的消息目标（称为“目标”）。</span><span class="sxs-lookup"><span data-stu-id="7951b-105">Reliable messaging is how a reliable messaging source (called the source) transfers messages reliably to a reliable messaging destination (called the destination).</span></span>  
  
 <span data-ttu-id="7951b-106">可靠消息传递具有以下几个关键方面：</span><span class="sxs-lookup"><span data-stu-id="7951b-106">Reliable messaging has the following key aspects:</span></span>  
  
- <span data-ttu-id="7951b-107">从源发送到目标的消息的传送保证，而不管消息传送或传输是否失败。</span><span class="sxs-lookup"><span data-stu-id="7951b-107">Transfer assurances for messages sent from a source to a destination regardless of message transfer failure or transport failures.</span></span>  
  
- <span data-ttu-id="7951b-108">源和目标相互分离，这为源和目标提供了独立的故障与恢复，即使源或目标不可用，也可以可靠地传送和传输消息。</span><span class="sxs-lookup"><span data-stu-id="7951b-108">Separation of the source and the destination from each other, which provides independent failure and recovery of the source and the destination as well as reliable transfer and delivery of messages even though the source or destination is unavailable.</span></span>  
  
 <span data-ttu-id="7951b-109">可靠消息传递经常伴随高延迟成本。</span><span class="sxs-lookup"><span data-stu-id="7951b-109">Reliable messaging frequently comes at the cost of high latency.</span></span> <span data-ttu-id="7951b-110">“延迟”是指消息从源到达目标所需要的时间。</span><span class="sxs-lookup"><span data-stu-id="7951b-110">Latency is the time it takes for the message to reach the destination from the source.</span></span> <span data-ttu-id="7951b-111">因此，WCF 提供以下类型的可靠消息传送：</span><span class="sxs-lookup"><span data-stu-id="7951b-111">WCF, therefore, provides the following types of reliable messaging:</span></span>  
  
- <span data-ttu-id="7951b-112">[可靠会话](reliable-sessions.md)，提供可靠的传输，而不会产生高延迟成本</span><span class="sxs-lookup"><span data-stu-id="7951b-112">[Reliable Sessions](reliable-sessions.md), which offer reliable transfer without the cost of high latency</span></span>  
  
- <span data-ttu-id="7951b-113">[WCF 中的队列](queues-in-wcf.md)，提供可靠的传输和源与目标之间的分离。</span><span class="sxs-lookup"><span data-stu-id="7951b-113">[Queues in WCF](queues-in-wcf.md), which offer both reliable transfers and separation between the source and the destination.</span></span>  
  
## <a name="reliable-sessions"></a><span data-ttu-id="7951b-114">可靠会话</span><span class="sxs-lookup"><span data-stu-id="7951b-114">Reliable Sessions</span></span>  
 <span data-ttu-id="7951b-115">可靠会话使用 WS-ReliableMessaging 协议提供源和目标之间的端到端可靠消息传送，而不管分隔消息（源和目标）终结点的中介的数量和类型如何。</span><span class="sxs-lookup"><span data-stu-id="7951b-115">Reliable sessions provide end-to-end reliable transfer of messages between a source and a destination using the WS-ReliableMessaging protocol regardless of the number or type of intermediaries that separate the messaging (source and destination) endpoints.</span></span> <span data-ttu-id="7951b-116">这包括不使用 SOAP 的任何传输中介（例如 HTTP 代理）或在终结点之间流动所必需的使用 SOAP 的中介（例如基于 SOAP 的路由器或网桥）。</span><span class="sxs-lookup"><span data-stu-id="7951b-116">This includes any transport intermediaries that do not use SOAP (for example, HTTP proxies) or intermediaries that use SOAP (for example, SOAP-based routers or bridges) that are required for messages to flow between the endpoints.</span></span> <span data-ttu-id="7951b-117">可靠会话使用内存中的传送窗口屏蔽 SOAP 消息级别的失败并在传输失败时重新建立连接。</span><span class="sxs-lookup"><span data-stu-id="7951b-117">Reliable sessions use an in-memory transfer window to mask SOAP message-level failures and re-establish connections in the case of transport failures.</span></span>  
  
 <span data-ttu-id="7951b-118">可靠会话提供低延迟可靠消息传送。</span><span class="sxs-lookup"><span data-stu-id="7951b-118">Reliable sessions provide low-latency reliable message transfers.</span></span> <span data-ttu-id="7951b-119">可靠会话通过任何代理或中介为 SOAP 消息提供的功能相当于 TCP 通过 IP 网桥为数据包提供的功能。</span><span class="sxs-lookup"><span data-stu-id="7951b-119">They provide for SOAP messages over any proxies or intermediaries, equivalent to what TCP provides for packets over IP bridges.</span></span> <span data-ttu-id="7951b-120">有关可靠会话的详细信息，请参阅[可靠会话](reliable-sessions.md)。</span><span class="sxs-lookup"><span data-stu-id="7951b-120">For more information about reliable sessions, see [Reliable Sessions](reliable-sessions.md).</span></span>  
  
## <a name="queues"></a><span data-ttu-id="7951b-121">队列</span><span class="sxs-lookup"><span data-stu-id="7951b-121">Queues</span></span>  
 <span data-ttu-id="7951b-122">WCF 中的队列以高延迟为代价提供可靠的消息传送和源与目标之间的分离。</span><span class="sxs-lookup"><span data-stu-id="7951b-122">Queues in WCF provide both reliable transfers of messages and separation between sources and destinations at the cost of high latency.</span></span> <span data-ttu-id="7951b-123">WCF 排队通信建立在消息队列（也称为 MSMQ）之上。</span><span class="sxs-lookup"><span data-stu-id="7951b-123">WCF queued communication is built on top of Message Queuing (also known as MSMQ).</span></span>  
  
 <span data-ttu-id="7951b-124">MSMQ 作为可选项随 Windows 提供，并作为 NT 服务运行。</span><span class="sxs-lookup"><span data-stu-id="7951b-124">MSMQ is shipped as an option with Windows that runs as an NT service.</span></span> <span data-ttu-id="7951b-125">它捕获代表源的传输队列中要传输的消息，并将消息传递到目标队列。</span><span class="sxs-lookup"><span data-stu-id="7951b-125">It captures messages for transmission in a transmission queue on behalf of the source and delivers it to a target queue.</span></span> <span data-ttu-id="7951b-126">目标队列代表目标接受消息，待以后目标请求消息时传递。</span><span class="sxs-lookup"><span data-stu-id="7951b-126">The target queue accepts messages on behalf of the destination for later delivery whenever the destination requests for messages.</span></span> <span data-ttu-id="7951b-127">MSMQ 队列管理器实现可靠的消息传输协议，以使消息不会在传输过程中丢失。</span><span class="sxs-lookup"><span data-stu-id="7951b-127">The MSMQ queue managers implement a reliable message-transfer protocol so that messages are not lost in transmission.</span></span> <span data-ttu-id="7951b-128">协议可以是本机的，也可以是基于 SOAP 的协议，例如 Soap 可靠消息传递协议 (SRMP)。</span><span class="sxs-lookup"><span data-stu-id="7951b-128">The protocol can be native or SOAP-based, such as Soap Reliable Messaging Protocol (SRMP).</span></span>  
  
 <span data-ttu-id="7951b-129">在队列之间与可靠消息传送相耦合的分离，使松耦合的应用程序能够可靠地通信。</span><span class="sxs-lookup"><span data-stu-id="7951b-129">The separation, coupled with reliable message transfers between queues, enables applications that are loosely coupled to communicate reliably.</span></span> <span data-ttu-id="7951b-130">与可靠会话不同，源和目标不必同时运行。</span><span class="sxs-lookup"><span data-stu-id="7951b-130">Unlike reliable sessions, the source and destination do not have to be running at the same time.</span></span> <span data-ttu-id="7951b-131">这暗示可以出现此类情况：当源产生消息的速率和目标使用消息的速率不匹配时，队列实际上用作一种负载平衡机制。</span><span class="sxs-lookup"><span data-stu-id="7951b-131">This implicitly enables scenarios where queues are, in effect, used as a load-leveling mechanism when there is a mismatch between the rate of message production by the source and the rate of the message consumption by the destination.</span></span> <span data-ttu-id="7951b-132">有关队列的详细信息，请参阅[WCF 中的队列](queues-in-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="7951b-132">For more information about queues, see [Queues in WCF](queues-in-wcf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7951b-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7951b-133">See also</span></span>

- [<span data-ttu-id="7951b-134">WCF 中的队列</span><span class="sxs-lookup"><span data-stu-id="7951b-134">Queues in WCF</span></span>](queues-in-wcf.md)
- [<span data-ttu-id="7951b-135">在 WCF 中排队</span><span class="sxs-lookup"><span data-stu-id="7951b-135">Queuing in WCF</span></span>](queuing-in-wcf.md)
- [<span data-ttu-id="7951b-136">可靠会话</span><span class="sxs-lookup"><span data-stu-id="7951b-136">Reliable Sessions</span></span>](reliable-sessions.md)
- [<span data-ttu-id="7951b-137">可靠会话概述</span><span class="sxs-lookup"><span data-stu-id="7951b-137">Reliable Sessions Overview</span></span>](reliable-sessions-overview.md)

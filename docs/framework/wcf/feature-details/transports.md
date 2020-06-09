---
title: Windows Communication Foundation 中的传输
ms.date: 03/30/2017
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
ms.openlocfilehash: 077d63d8038b245a68083611897c1e6c68971071
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598666"
---
# <a name="transports-in-windows-communication-foundation"></a><span data-ttu-id="db4bb-102">Windows Communication Foundation 中的传输</span><span class="sxs-lookup"><span data-stu-id="db4bb-102">Transports in Windows Communication Foundation</span></span>
<span data-ttu-id="db4bb-103">传输层是通道堆栈的最低层。</span><span class="sxs-lookup"><span data-stu-id="db4bb-103">The transport layer is at the lowest level of the channel stack.</span></span> <span data-ttu-id="db4bb-104">Windows Communication Foundation 中使用的主要传输有 HTTP、HTTPS、TCP 和命名管道。</span><span class="sxs-lookup"><span data-stu-id="db4bb-104">The main transports used in Windows Communication Foundation (WCF) are HTTP, HTTPS, TCP, and named pipes.</span></span> <span data-ttu-id="db4bb-105">本节中的主题讨论如何选择传输、配置传输和设置优化属性。</span><span class="sxs-lookup"><span data-stu-id="db4bb-105">The topics in this section discuss choosing among these transports, configuring the transport, and setting tuning properties.</span></span>  
  
 <span data-ttu-id="db4bb-106">WCF 包括其他传输。</span><span class="sxs-lookup"><span data-stu-id="db4bb-106">WCF includes additional transports.</span></span> <span data-ttu-id="db4bb-107">有关消息队列（也称为 MSMQ）传输的信息，请参阅[队列和可靠会话](queues-and-reliable-sessions.md)。</span><span class="sxs-lookup"><span data-stu-id="db4bb-107">For information about Message Queuing (also known as MSMQ) transport, see [Queues and Reliable Sessions](queues-and-reliable-sessions.md).</span></span> <span data-ttu-id="db4bb-108">有关对等传输的信息，请参阅对等[网络](peer-to-peer-networking.md)。</span><span class="sxs-lookup"><span data-stu-id="db4bb-108">For information about peer-to-peer transport, see [Peer-to-Peer Networking](peer-to-peer-networking.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="db4bb-109">本节内容</span><span class="sxs-lookup"><span data-stu-id="db4bb-109">In This Section</span></span>  
 [<span data-ttu-id="db4bb-110">选择传输方式</span><span class="sxs-lookup"><span data-stu-id="db4bb-110">Choosing a Transport</span></span>](choosing-a-transport.md)  
 <span data-ttu-id="db4bb-111">说明三种主要传输和选择其中一种传输时的注意事项。</span><span class="sxs-lookup"><span data-stu-id="db4bb-111">Describes the three main transports and considerations in selecting one.</span></span>  
  
 [<span data-ttu-id="db4bb-112">选择消息编码器</span><span class="sxs-lookup"><span data-stu-id="db4bb-112">Choosing a Message Encoder</span></span>](choosing-a-message-encoder.md)  
 <span data-ttu-id="db4bb-113">说明选择消息编码绑定元素时要考虑的因素。</span><span class="sxs-lookup"><span data-stu-id="db4bb-113">Describes factors to consider when choosing a message-encoding binding element.</span></span>  
  
 [<span data-ttu-id="db4bb-114">流消息传输</span><span class="sxs-lookup"><span data-stu-id="db4bb-114">Streaming Message Transfer</span></span>](streaming-message-transfer.md)  
 <span data-ttu-id="db4bb-115">说明如何配置传输层进行流式处理。</span><span class="sxs-lookup"><span data-stu-id="db4bb-115">Describes how to configure the transport layer to do streaming.</span></span>  
  
 [<span data-ttu-id="db4bb-116">配置 HTTP 和 HTTPS</span><span class="sxs-lookup"><span data-stu-id="db4bb-116">Configuring HTTP and HTTPS</span></span>](configuring-http-and-https.md)  
 <span data-ttu-id="db4bb-117">说明如何配置 HTTP 和 HTTPS 传输绑定元素。</span><span class="sxs-lookup"><span data-stu-id="db4bb-117">Describes how to configure the HTTP and HTTPS transport binding elements.</span></span>  
  
 [<span data-ttu-id="db4bb-118">如何：用受限预留替换 WCF URL 预留</span><span class="sxs-lookup"><span data-stu-id="db4bb-118">How to: Replace the WCF URL Reservation with a Restricted Reservation</span></span>](how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 <span data-ttu-id="db4bb-119">介绍如何使用 WCFURL 受限预订。</span><span class="sxs-lookup"><span data-stu-id="db4bb-119">Describes how to use WCFURL restricted reservations.</span></span>  
  
 [<span data-ttu-id="db4bb-120">传输配额</span><span class="sxs-lookup"><span data-stu-id="db4bb-120">Transport Quotas</span></span>](transport-quotas.md)  
 <span data-ttu-id="db4bb-121">说明设置传输层中可用配额时的注意事项。</span><span class="sxs-lookup"><span data-stu-id="db4bb-121">Describes considerations in setting the quotas available in the transport layer.</span></span>  
  
 [<span data-ttu-id="db4bb-122">使用 NAT 和防火墙</span><span class="sxs-lookup"><span data-stu-id="db4bb-122">Working with NATs and Firewalls</span></span>](working-with-nats-and-firewalls.md)  
 <span data-ttu-id="db4bb-123">说明在防火墙后发送或接收消息时或存在网络地址转换 (NAT) 时如何配置传输层。</span><span class="sxs-lookup"><span data-stu-id="db4bb-123">Describes how to configure the transport layer when messages are sent or received behind a firewall or when network address translation (NAT) is present.</span></span>  
  
 [<span data-ttu-id="db4bb-124">Net.TCP 端口共享</span><span class="sxs-lookup"><span data-stu-id="db4bb-124">Net.TCP Port Sharing</span></span>](net-tcp-port-sharing.md)  
 <span data-ttu-id="db4bb-125">介绍如何使用 WCF 的 Net.tcp 端口共享组件。</span><span class="sxs-lookup"><span data-stu-id="db4bb-125">Describes how to use the Net.TCP Port Sharing component of WCF.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="db4bb-126">参考</span><span class="sxs-lookup"><span data-stu-id="db4bb-126">Reference</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a><span data-ttu-id="db4bb-127">相关章节</span><span class="sxs-lookup"><span data-stu-id="db4bb-127">Related Sections</span></span>  
 [<span data-ttu-id="db4bb-128">绑定</span><span class="sxs-lookup"><span data-stu-id="db4bb-128">Bindings</span></span>](bindings.md)  
  
 [<span data-ttu-id="db4bb-129">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="db4bb-129">Extending Bindings</span></span>](../extending/extending-bindings.md)

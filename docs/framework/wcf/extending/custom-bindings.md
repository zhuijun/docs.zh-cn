---
title: 自定义绑定
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, endpoints
- Windows Communication Foundation, configuration
ms.assetid: 58532b6d-4eea-4a4f-854f-a1c8c842564d
ms.openlocfilehash: 062aba26227fedeea3e5f462ebf5d55cf0cba56c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539992"
---
# <a name="custom-bindings"></a><span data-ttu-id="c1333-102">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="c1333-102">Custom Bindings</span></span>

<span data-ttu-id="c1333-103">当系统提供的某个绑定不符合服务的需求时，可使用 <xref:System.ServiceModel.Channels.CustomBinding> 类。</span><span class="sxs-lookup"><span data-stu-id="c1333-103">You can use the <xref:System.ServiceModel.Channels.CustomBinding> class when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="c1333-104">所有绑定都是从绑定元素的有序集构造而来的。</span><span class="sxs-lookup"><span data-stu-id="c1333-104">All bindings are constructed from an ordered set of binding elements.</span></span> <span data-ttu-id="c1333-105">自定义绑定可以从一组系统提供的绑定元素生成，也可以包含用户定义的自定义绑定元素。</span><span class="sxs-lookup"><span data-stu-id="c1333-105">Custom bindings can be built from a set of system-provided binding elements or can include user-defined custom binding elements.</span></span> <span data-ttu-id="c1333-106">例如，可以使用自定义绑定元素在服务终结点使用新的传输或编码器。</span><span class="sxs-lookup"><span data-stu-id="c1333-106">You can use custom binding elements, for example, to enable the use of new transports or encoders at a service endpoint.</span></span> <span data-ttu-id="c1333-107">有关工作示例，请参阅 [自定义绑定示例](/previous-versions/dotnet/netframework-3.5/ms751479(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="c1333-107">For working examples, see [Custom Binding Samples](/previous-versions/dotnet/netframework-3.5/ms751479(v=vs.90)).</span></span> <span data-ttu-id="c1333-108">有关详细信息，请参阅 [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md)。</span><span class="sxs-lookup"><span data-stu-id="c1333-108">For more information, see [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>

## <a name="construction-of-a-custom-binding"></a><span data-ttu-id="c1333-109">自定义绑定的构造</span><span class="sxs-lookup"><span data-stu-id="c1333-109">Construction of a Custom Binding</span></span>

<span data-ttu-id="c1333-110">自定义绑定是使用 <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> 构造函数并通过“堆叠”在一起的绑定元素的集合构造的，这些元素的特定顺序如下：</span><span class="sxs-lookup"><span data-stu-id="c1333-110">A custom binding is constructed using the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> constructor from a collection of binding elements that are "stacked" in a specific order:</span></span>

- <span data-ttu-id="c1333-111">最顶层是一个允许流事务的可选 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> 类。</span><span class="sxs-lookup"><span data-stu-id="c1333-111">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> class that allows flowing transactions.</span></span>

- <span data-ttu-id="c1333-112">接下来是一个可选的 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> 类，它提供了 WS-ReliableMessaging 规范中定义的会话和排序机制。</span><span class="sxs-lookup"><span data-stu-id="c1333-112">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> class that provides a session and ordering mechanisms as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="c1333-113">会话可通过 SOAP 和传输中介。</span><span class="sxs-lookup"><span data-stu-id="c1333-113">A session can cross SOAP and transport intermediaries.</span></span>

- <span data-ttu-id="c1333-114">接下来是一个可选的 <xref:System.ServiceModel.Channels.SecurityBindingElement> 类，它提供了授权、身份验证、保护和机密性等安全功能。</span><span class="sxs-lookup"><span data-stu-id="c1333-114">Next is an optional <xref:System.ServiceModel.Channels.SecurityBindingElement> class that provides security features such as authorization, authentication, protection, and confidentiality.</span></span>

- <span data-ttu-id="c1333-115">接下来是一个可选的 <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> 类，它提供了通过本身不支持双工通信的传输协议（例如 HTTP）进行双向双工通信的功能。</span><span class="sxs-lookup"><span data-stu-id="c1333-115">Next is an optional <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> class that provides the ability to have two way duplex communication with a transport protocol that does not support duplex communication natively, such as HTTP.</span></span>

- <span data-ttu-id="c1333-116">接下来是一个可选的 <xref:System.ServiceModel.Channels.OneWayBindingElement> 类，它提供了单向通信。</span><span class="sxs-lookup"><span data-stu-id="c1333-116">Next is an optional <xref:System.ServiceModel.Channels.OneWayBindingElement>) class that provides one-way communication.</span></span>

- <span data-ttu-id="c1333-117">接下来是一个可选的流安全绑定元素，它可以是以下元素之一。</span><span class="sxs-lookup"><span data-stu-id="c1333-117">Next is an optional stream security binding element which can be one of the following.</span></span>

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- <span data-ttu-id="c1333-118">再接下来是一个必需的消息编码绑定元素。</span><span class="sxs-lookup"><span data-stu-id="c1333-118">Next is a required message encoding binding element.</span></span> <span data-ttu-id="c1333-119">可以使用自己的消息编码器或者以下三种消息编码绑定之一：</span><span class="sxs-lookup"><span data-stu-id="c1333-119">You can use your own message encoder or one of the three message encoding bindings:</span></span>

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

<span data-ttu-id="c1333-120">底层是一个必需的传输元素。</span><span class="sxs-lookup"><span data-stu-id="c1333-120">At the bottom is a required transport element.</span></span> <span data-ttu-id="c1333-121">你可以使用自己的传输，或者 Windows Communication Foundation (WCF) 提供的传输绑定元素之一：</span><span class="sxs-lookup"><span data-stu-id="c1333-121">You can use your own transport or one of the following transport binding elements Windows Communication Foundation (WCF) provides:</span></span>

- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>

<span data-ttu-id="c1333-122">下表总结了每层的选项。</span><span class="sxs-lookup"><span data-stu-id="c1333-122">The following table summarizes the options for each layer.</span></span>

|<span data-ttu-id="c1333-123">层</span><span class="sxs-lookup"><span data-stu-id="c1333-123">Layer</span></span>|<span data-ttu-id="c1333-124">选项</span><span class="sxs-lookup"><span data-stu-id="c1333-124">Options</span></span>|<span data-ttu-id="c1333-125">必选</span><span class="sxs-lookup"><span data-stu-id="c1333-125">Required</span></span>|
|-----------|-------------|--------------|
|<span data-ttu-id="c1333-126">事务</span><span class="sxs-lookup"><span data-stu-id="c1333-126">Transactions</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="c1333-127">否</span><span class="sxs-lookup"><span data-stu-id="c1333-127">No</span></span>|
|<span data-ttu-id="c1333-128">可靠性</span><span class="sxs-lookup"><span data-stu-id="c1333-128">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="c1333-129">否</span><span class="sxs-lookup"><span data-stu-id="c1333-129">No</span></span>|
|<span data-ttu-id="c1333-130">安全性</span><span class="sxs-lookup"><span data-stu-id="c1333-130">Security</span></span>|<xref:System.ServiceModel.Channels.SecurityBindingElement>|<span data-ttu-id="c1333-131">否</span><span class="sxs-lookup"><span data-stu-id="c1333-131">No</span></span>|
|<span data-ttu-id="c1333-132">编码</span><span class="sxs-lookup"><span data-stu-id="c1333-132">Encoding</span></span>|<span data-ttu-id="c1333-133">文本、二进制、消息传输优化机制 (MTOM)、自定义</span><span class="sxs-lookup"><span data-stu-id="c1333-133">Text, binary, Message Transmission Optimization Mechanism (MTOM), custom</span></span>|<span data-ttu-id="c1333-134">是</span><span class="sxs-lookup"><span data-stu-id="c1333-134">Yes</span></span>|
|<span data-ttu-id="c1333-135">Transport</span><span class="sxs-lookup"><span data-stu-id="c1333-135">Transport</span></span>|<span data-ttu-id="c1333-136">TCP、HTTP、HTTPS、命名管道（也称为 IPC）、对等 (P2P)、消息队列（也称为 MSMQ）、自定义</span><span class="sxs-lookup"><span data-stu-id="c1333-136">TCP, HTTP, HTTPS, named pipes (also known as IPC), Peer-to-Peer (P2P), Message Queuing (also known as MSMQ), Custom</span></span>|<span data-ttu-id="c1333-137">是</span><span class="sxs-lookup"><span data-stu-id="c1333-137">Yes</span></span>|

<span data-ttu-id="c1333-138">此外，可以定义自己的绑定元素，并将它们插在前面定义的任何层之间。</span><span class="sxs-lookup"><span data-stu-id="c1333-138">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1333-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="c1333-139">See also</span></span>

- [<span data-ttu-id="c1333-140">终结点创建概述</span><span class="sxs-lookup"><span data-stu-id="c1333-140">Endpoint Creation Overview</span></span>](../endpoint-creation-overview.md)
- [<span data-ttu-id="c1333-141">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="c1333-141">Using Bindings to Configure Services and Clients</span></span>](../using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="c1333-142">系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="c1333-142">System-Provided Bindings</span></span>](../system-provided-bindings.md)
- [<span data-ttu-id="c1333-143">如何：自定义系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="c1333-143">How to: Customize a System-Provided Binding</span></span>](how-to-customize-a-system-provided-binding.md)
- [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="c1333-144">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="c1333-144">Custom Binding</span></span>](../samples/custom-binding.md)

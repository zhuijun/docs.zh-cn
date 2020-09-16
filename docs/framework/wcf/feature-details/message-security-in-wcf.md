---
title: WCF 中的消息安全
description: 了解 TransportWithMessageCredential，它是一种使用传输和消息安全模式的组合的 WCF 消息安全类型。
ms.date: 03/30/2017
ms.assetid: a80efb59-591a-4a37-bb3c-8fffa6ca0b7d
ms.openlocfilehash: ea10a87a7c8f9e545c320af30c5cf9958317c2f7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551127"
---
# <a name="message-security-in-wcf"></a><span data-ttu-id="5a1c1-103">WCF 中的消息安全</span><span class="sxs-lookup"><span data-stu-id="5a1c1-103">Message Security in WCF</span></span>

<span data-ttu-id="5a1c1-104">Windows Communication Foundation (WCF) 提供了两个用于提供安全 (`Transport` 和 `Message`) 的主要模式，以及两个 () `TransportWithMessageCredential` 的。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-104">Windows Communication Foundation (WCF) has two major modes for providing security (`Transport` and `Message`) and a third mode (`TransportWithMessageCredential`) that combines the two.</span></span> <span data-ttu-id="5a1c1-105">本主题讨论消息安全和使用它的原因。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-105">This topic discusses message security and the reasons to use it.</span></span>

## <a name="what-is-message-security"></a><span data-ttu-id="5a1c1-106">何为消息安全？</span><span class="sxs-lookup"><span data-stu-id="5a1c1-106">What Is Message Security?</span></span>

<span data-ttu-id="5a1c1-107">消息安全使用 WS-Security 规范来保护消息。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-107">Message security uses the WS-Security specification to secure messages.</span></span> <span data-ttu-id="5a1c1-108">WS 安全规范描述 SOAP 消息传送的增强功能，以确保 SOAP 消息级别的机密性、完整性和身份验证 (而不是传输级别) 。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-108">The WS-Security specification describes enhancements to SOAP messaging to ensure confidentiality, integrity, and authentication at the SOAP message level (instead of the transport level).</span></span>

<span data-ttu-id="5a1c1-109">简言之，消息安全与传输安全的不同之处在于，前者将安全凭据和声明与每条消息以及任何消息保护（签名或加密）封装在一起。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-109">In brief, message security differs from transport security by encapsulating the security credentials and claims with every message along with any message protection (signing or encryption).</span></span> <span data-ttu-id="5a1c1-110">通过修改消息内容将安全直接应用于消息，受保护的消息可以在安全方面进行自包含。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-110">Applying the security directly to the message by modifying its content allows the secured message to be self-containing with respect to the security aspects.</span></span> <span data-ttu-id="5a1c1-111">这会使某些在使用传输安全时不可能的情况成为可能。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-111">This enables some scenarios that are not possible when transport security is used.</span></span>

## <a name="reasons-to-use-message-security"></a><span data-ttu-id="5a1c1-112">使用消息安全的原因</span><span class="sxs-lookup"><span data-stu-id="5a1c1-112">Reasons to Use Message Security</span></span>

<span data-ttu-id="5a1c1-113">在消息级安全中，所有安全信息均封装在消息中。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-113">In message-level security, all of the security information is encapsulated in the message.</span></span> <span data-ttu-id="5a1c1-114">使用消息级安全（而非传输级安全）保护消息具有以下优点：</span><span class="sxs-lookup"><span data-stu-id="5a1c1-114">Securing the message with message-level security instead of transport-level security has the following advantages:</span></span>

- <span data-ttu-id="5a1c1-115">端对端安全。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-115">End-to-end security.</span></span> <span data-ttu-id="5a1c1-116">传输安全（如安全套接字层 (SSL)）仅在通信是点对点时才保护消息。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-116">Transport security, such as Secure Sockets Layer (SSL) only secures messages when the communication is point-to-point.</span></span> <span data-ttu-id="5a1c1-117">如果消息在到达最终接收方之前要路由到一个或多个 SOAP 中介（如路由器），则一旦中介从网络上读取消息，消息本身将不会受到保护。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-117">If the message is routed to one or more SOAP intermediaries (for example a router) before reaching the ultimate receiver, the message itself is not protected once an intermediary reads it from the wire.</span></span> <span data-ttu-id="5a1c1-118">此外，客户端身份验证信息仅对第一个中介可用，而且必须以带外方式重新传输到最终接收方（如果需要）。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-118">Additionally, the client authentication information is available only to the first intermediary and must be re-transmitted to the ultimate receiver in out-of-band fashion, if necessary.</span></span> <span data-ttu-id="5a1c1-119">即使整个路由在单个跃点之间使用 SSL 安全也是如此。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-119">This applies even if the entire route uses SSL security between individual hops.</span></span> <span data-ttu-id="5a1c1-120">因为消息安全直接作用于消息并保护其中的 XML，所以无论消息在到达最终接收方之前涉及到多少个中介，总能保持安全。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-120">Because message security works directly with the message and secures the XML in it, the security stays with the message regardless of how many intermediaries are involved before it reaches the ultimate receiver.</span></span> <span data-ttu-id="5a1c1-121">这可以实现真正的端对端安全方案。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-121">This enables a true end-to-end security scenario.</span></span>

- <span data-ttu-id="5a1c1-122">增强的灵活性。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-122">Increased flexibility.</span></span> <span data-ttu-id="5a1c1-123">可以对消息的某些部分（而非整个消息）进行签名或加密。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-123">Parts of the message, instead of the entire message, can be signed or encrypted.</span></span> <span data-ttu-id="5a1c1-124">这表示中介可以查看消息中为它们提供的那些部分。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-124">This means that intermediaries can view the parts of the message that are intended for them.</span></span> <span data-ttu-id="5a1c1-125">如果发送方需要让消息中的部分信息对中介可见，但又希望确保消息不被篡改，则它可以只对消息进行签名而不加密。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-125">If the sender needs to make part of the information in the message visible to the intermediaries but wants to ensure that it is not tampered with, it can just sign it but leave it unencrypted.</span></span> <span data-ttu-id="5a1c1-126">由于签名属于消息，因而最终接收方可以验证消息中的信息是否按原样接收的。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-126">Since the signature is part of the message, the ultimate receiver can verify that the information in the message was received intact.</span></span> <span data-ttu-id="5a1c1-127">在某个方案中，可能有一个 SOAP 中介服务，该服务根据 Action 标头值路由消息。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-127">One scenario might have a SOAP intermediary service that routes message according the Action header value.</span></span> <span data-ttu-id="5a1c1-128">默认情况下，WCF 不对操作值进行加密，但如果使用消息安全，则对其进行签名。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-128">By default, WCF does not encrypt the Action value but signs it if message security is used.</span></span> <span data-ttu-id="5a1c1-129">因此，所有中介都可获得此信息，但没有一个能更改它。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-129">Therefore, this information is available to all intermediaries, but no one can change it.</span></span>

- <span data-ttu-id="5a1c1-130">对多个传输的支持。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-130">Support for multiple transports.</span></span> <span data-ttu-id="5a1c1-131">可以通过许多不同的传输（例如命名管道和 TCP）来发送受保护的消息，而不必依赖于安全协议。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-131">You can send secured messages over many different transports, such as named pipes and TCP, without having to rely on the protocol for security.</span></span> <span data-ttu-id="5a1c1-132">使用传输级安全时，所有安全信息的范围限定于单个特殊的传输连接，不能从消息内容本身获取这些信息。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-132">With transport-level security, all the security information is scoped to a single particular transport connection and is not available from the message content itself.</span></span> <span data-ttu-id="5a1c1-133">无论您使用什么传输来传送消息，消息安全都会让消息变得安全，并且安全上下文直接嵌入消息内。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-133">Message security makes the message secure regardless of what transport you use to transmit the message, and the security context is directly embedded inside the message.</span></span>

- <span data-ttu-id="5a1c1-134">对一组范围广泛的凭据和声明的支持。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-134">Support for a wide set of credentials and claims.</span></span> <span data-ttu-id="5a1c1-135">消息安全基于 WS-Security 规范，该规范提供能够在 SOAP 消息内传输任何类型声明的可扩展框架。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-135">The message security is based on the WS-Security specification, which provides an extensible framework capable of transmitting any type of claim inside the SOAP message.</span></span> <span data-ttu-id="5a1c1-136">与传输安全不同，您可以使用的这组身份验证机制或声明不受传输能力的限制。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-136">Unlike transport security, the set of authentication mechanisms, or claims, that you can use is not limited by the transport capabilities.</span></span> <span data-ttu-id="5a1c1-137">WCF 消息安全包括多种类型的身份验证和声明传输，可以根据需要进行扩展以支持其他类型。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-137">WCF message security includes multiple types of authentication and claim transmission and can be extended to support additional types as necessary.</span></span> <span data-ttu-id="5a1c1-138">例如，由于这些原因，如果没有消息安全，联合凭据方案不可能实现。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-138">For those reasons, for example, a federated credentials scenario is not possible without message security.</span></span> <span data-ttu-id="5a1c1-139">有关 WCF 支持的联合方案的详细信息，请参阅 [联合和颁发的令牌](federation-and-issued-tokens.md)。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-139">For more information about federation scenarios WCF supports, see [Federation and Issued Tokens](federation-and-issued-tokens.md).</span></span>

## <a name="how-message-and-transport-security-compare"></a><span data-ttu-id="5a1c1-140">消息安全与传输安全比较</span><span class="sxs-lookup"><span data-stu-id="5a1c1-140">How Message and Transport Security Compare</span></span>

### <a name="pros-and-cons-of-transport-level-security"></a><span data-ttu-id="5a1c1-141">传输级安全的优缺点</span><span class="sxs-lookup"><span data-stu-id="5a1c1-141">Pros and Cons of Transport-Level Security</span></span>

<span data-ttu-id="5a1c1-142">传输安全具有以下优点：</span><span class="sxs-lookup"><span data-stu-id="5a1c1-142">Transport security has the following advantages:</span></span>

- <span data-ttu-id="5a1c1-143">不要求通信双方理解 XML 级安全概念。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-143">Does not require that the communicating parties understand XML-level security concepts.</span></span> <span data-ttu-id="5a1c1-144">这可提高互操作性，例如，当将 HTTPS 用于保护通信时。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-144">This can improve the interoperability, for example, when HTTPS is used to secure the communication.</span></span>

- <span data-ttu-id="5a1c1-145">全面提高的性能。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-145">Generally improved performance.</span></span>

- <span data-ttu-id="5a1c1-146">提供了硬件加速器。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-146">Hardware accelerators are available.</span></span>

- <span data-ttu-id="5a1c1-147">可以使用流。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-147">Streaming is possible.</span></span>

 <span data-ttu-id="5a1c1-148">传输安全具有以下缺点：</span><span class="sxs-lookup"><span data-stu-id="5a1c1-148">Transport security has the following disadvantages:</span></span>

- <span data-ttu-id="5a1c1-149">仅支持跃点到跃点。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-149">Hop-to-hop only.</span></span>

- <span data-ttu-id="5a1c1-150">有限且不可扩展的凭据集。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-150">Limited and inextensible set of credentials.</span></span>

- <span data-ttu-id="5a1c1-151">依赖于传输。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-151">Transport-dependent.</span></span>

### <a name="disadvantages-of-message-level-security"></a><span data-ttu-id="5a1c1-152">消息级安全的缺点</span><span class="sxs-lookup"><span data-stu-id="5a1c1-152">Disadvantages of Message-Level Security</span></span>

<span data-ttu-id="5a1c1-153">消息安全具有以下缺点：</span><span class="sxs-lookup"><span data-stu-id="5a1c1-153">Message security has the following disadvantages:</span></span>

- <span data-ttu-id="5a1c1-154">性能</span><span class="sxs-lookup"><span data-stu-id="5a1c1-154">Performance</span></span>

- <span data-ttu-id="5a1c1-155">不能使用消息流。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-155">Cannot use message streaming.</span></span>

- <span data-ttu-id="5a1c1-156">要求实现 XML 级安全机制并支持 WS-Security 规范。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-156">Requires implementation of XML-level security mechanisms and support for WS-Security specification.</span></span> <span data-ttu-id="5a1c1-157">这可能影响互操作性。</span><span class="sxs-lookup"><span data-stu-id="5a1c1-157">This might affect the interoperability.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a1c1-158">请参阅</span><span class="sxs-lookup"><span data-stu-id="5a1c1-158">See also</span></span>

- [<span data-ttu-id="5a1c1-159">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="5a1c1-159">Securing Services and Clients</span></span>](securing-services-and-clients.md)
- [<span data-ttu-id="5a1c1-160">传输安全</span><span class="sxs-lookup"><span data-stu-id="5a1c1-160">Transport Security</span></span>](transport-security.md)
- [<span data-ttu-id="5a1c1-161">如何：使用传输安全和消息凭据</span><span class="sxs-lookup"><span data-stu-id="5a1c1-161">How to: Use Transport Security and Message Credentials</span></span>](how-to-use-transport-security-and-message-credentials.md)
- <span data-ttu-id="5a1c1-162">[Microsoft Patterns and Practices, Chapter 3: Implementing Transport and Message Layer Security（《Microsoft 模式与实践》第 3 章：实现传输和消息层安全性）](/previous-versions/msp-n-p/ff647370(v=pandp.10))</span><span class="sxs-lookup"><span data-stu-id="5a1c1-162">[Microsoft Patterns and Practices, Chapter 3: Implementing Transport and Message Layer Security](/previous-versions/msp-n-p/ff647370(v=pandp.10))</span></span>

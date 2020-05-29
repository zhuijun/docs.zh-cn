---
title: 可靠消息传送协议版本 1.0
ms.date: 03/30/2017
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
ms.openlocfilehash: 8d192afcffca52136d6d71de49770c5a5ad13895
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202306"
---
# <a name="reliable-messaging-protocol-version-10"></a><span data-ttu-id="f7c80-102">可靠消息传送协议版本 1.0</span><span class="sxs-lookup"><span data-stu-id="f7c80-102">Reliable Messaging Protocol version 1.0</span></span>

<span data-ttu-id="f7c80-103">本主题介绍了使用 HTTP 传输进行互操作所需的 WS-TRUST 2005 年2月（版本1.0）协议的 Windows Communication Foundation （WCF）实现细节。</span><span class="sxs-lookup"><span data-stu-id="f7c80-103">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-Reliable Messaging February 2005 (version 1.0) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="f7c80-104">WCF 遵循与本主题中所述的约束和说明相关的 WS 可靠消息传送规范。</span><span class="sxs-lookup"><span data-stu-id="f7c80-104">WCF follows the WS-Reliable Messaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="f7c80-105">请注意，ws-reliablemessaging 版本1.0 协议是从 WinFX 开始实现的。</span><span class="sxs-lookup"><span data-stu-id="f7c80-105">Note that the WS-ReliableMessaging version 1.0 protocol is implemented starting with the WinFX.</span></span>

<span data-ttu-id="f7c80-106">WS-可靠消息2月2005协议在 WCF 中由实现 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> 。</span><span class="sxs-lookup"><span data-stu-id="f7c80-106">The WS-Reliable Messaging February 2005 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>

<span data-ttu-id="f7c80-107">为方便起见，本主题使用以下角色：</span><span class="sxs-lookup"><span data-stu-id="f7c80-107">For convenience, the topic uses the following roles:</span></span>

- <span data-ttu-id="f7c80-108">发起方：启动 WS-Reliable Message 序列创建的客户端</span><span class="sxs-lookup"><span data-stu-id="f7c80-108">Initiator: the client that initiates WS-Reliable Message sequence creation</span></span>

- <span data-ttu-id="f7c80-109">响应方：接收发起方的请求的服务</span><span class="sxs-lookup"><span data-stu-id="f7c80-109">Responder: the service that receives the initiator's requests</span></span>

<span data-ttu-id="f7c80-110">本文档使用下表中的前缀和命名空间。</span><span class="sxs-lookup"><span data-stu-id="f7c80-110">This document uses the prefixes and namespaces in the following table.</span></span>

|<span data-ttu-id="f7c80-111">前缀</span><span class="sxs-lookup"><span data-stu-id="f7c80-111">Prefix</span></span>|<span data-ttu-id="f7c80-112">命名空间</span><span class="sxs-lookup"><span data-stu-id="f7c80-112">Namespace</span></span>|
|------------|---------------|
|<span data-ttu-id="f7c80-113">wsrm</span><span class="sxs-lookup"><span data-stu-id="f7c80-113">wsrm</span></span>|`http://schemas.xmlsoap.org/ws/2005/02/rm`|
|<span data-ttu-id="f7c80-114">netrm</span><span class="sxs-lookup"><span data-stu-id="f7c80-114">netrm</span></span>|`http://schemas.microsoft.com/ws/2006/05/rm`|
|<span data-ttu-id="f7c80-115">s</span><span class="sxs-lookup"><span data-stu-id="f7c80-115">s</span></span>|`http://www.w3.org/2003/05/soap-envelope`|
|<span data-ttu-id="f7c80-116">wsa</span><span class="sxs-lookup"><span data-stu-id="f7c80-116">wsa</span></span>|`http://schemas.xmlsoap.org/ws/2005/08/addressing`|
|<span data-ttu-id="f7c80-117">wsse</span><span class="sxs-lookup"><span data-stu-id="f7c80-117">wsse</span></span>|`http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd`|

## <a name="messaging"></a><span data-ttu-id="f7c80-118">消息传递</span><span class="sxs-lookup"><span data-stu-id="f7c80-118">Messaging</span></span>

### <a name="sequence-establishment-messages"></a><span data-ttu-id="f7c80-119">序列建立消息</span><span class="sxs-lookup"><span data-stu-id="f7c80-119">Sequence Establishment Messages</span></span>

<span data-ttu-id="f7c80-120">WCF 实现 `CreateSequence` 和 `CreateSequenceResponse` 消息以建立可靠的消息序列。</span><span class="sxs-lookup"><span data-stu-id="f7c80-120">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable message sequence.</span></span> <span data-ttu-id="f7c80-121">适用以下约束：</span><span class="sxs-lookup"><span data-stu-id="f7c80-121">The following constraints apply:</span></span>

- <span data-ttu-id="f7c80-122">B1101： WCF 发起方不会在消息中生成可选的 Expires 元素，也不会 `CreateSequence` 在 `CreateSequence` 消息包含元素的情况下，在 `Offer` `Expires` 元素中包含可选元素 `Offer` 。</span><span class="sxs-lookup"><span data-stu-id="f7c80-122">B1101: The WCF Initiator does not generate the optional Expires element in the `CreateSequence` message or, in the cases when the `CreateSequence` message contains an `Offer` element, the optional `Expires` element in the `Offer` element.</span></span>

- <span data-ttu-id="f7c80-123">B1102：访问消息时 `CreateSequence` ，WCF `Responder` 将发送和接收两个 `Expires` 元素（如果存在），但不使用它们的值。</span><span class="sxs-lookup"><span data-stu-id="f7c80-123">B1102: When accessing the `CreateSequence` message, the WCF`Responder` sends and receives both `Expires` elements if they exist, but does not use their values.</span></span>

<span data-ttu-id="f7c80-124">WS-Reliable Messaging 引入了 `Offer` 机制来建立两个形成会话的反向相关的序列。</span><span class="sxs-lookup"><span data-stu-id="f7c80-124">WS-Reliable Messaging introduces the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>

- <span data-ttu-id="f7c80-125">R1103：如果 `CreateSequence` 包含一个 `Offer` 元素，则可靠消息响应方要么必须接受序列并使用包含形成两个相关反向序列的 `CreateSequenceResponse` 元素的 `wsrm:Accept` 进行响应，要么必须拒绝 `CreateSequence` 请求。</span><span class="sxs-lookup"><span data-stu-id="f7c80-125">R1103: If `CreateSequence` contains an `Offer` element, the Reliable Messaging Responder must either accept the sequence and respond with `CreateSequenceResponse` that contains a `wsrm:Accept` element, forming two correlated converse sequences or reject the `CreateSequence` request.</span></span>

- <span data-ttu-id="f7c80-126">R1104：在反向序列上流动的 `SequenceAcknowledgement` 和应用程序消息必须发送到 `ReplyTo` 的 `CreateSequence` 终结点引用。</span><span class="sxs-lookup"><span data-stu-id="f7c80-126">R1104: `SequenceAcknowledgement` and application messages flowing on converse sequence must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>

- <span data-ttu-id="f7c80-127">R1105：`AcksTo` 中的 `ReplyTo` 和 `CreateSequence` 终结点引用必须具有与八进制识别匹配的地址值。</span><span class="sxs-lookup"><span data-stu-id="f7c80-127">R1105: `AcksTo` and `ReplyTo` endpoint references in the `CreateSequence` must have address values that match the octet-wise.</span></span>

  <span data-ttu-id="f7c80-128">在创建序列之前，WCF 响应程序验证和 epr 的 URI 部分 `AcksTo` `ReplyTo` 是否相同。</span><span class="sxs-lookup"><span data-stu-id="f7c80-128">The WCF Responder verifies that the URI portion of the `AcksTo` and `ReplyTo` EPRs are identical before creating a sequence.</span></span>

- <span data-ttu-id="f7c80-129">R1106：`AcksTo` 中的 `ReplyTo` 和 `CreateSequence` 终结点引用应具有相同的引用参数集。</span><span class="sxs-lookup"><span data-stu-id="f7c80-129">R1106: `AcksTo` and `ReplyTo` Endpoint References in the `CreateSequence` should have the same set of reference parameters.</span></span>

  <span data-ttu-id="f7c80-130">WCF 不强制执行，但假定的 [引用参数] `AcksTo` `ReplyTo` `CreateSequence` 相同，并使用 `ReplyTo` 确认和反向序列消息的终结点引用中的 [引用参数]。</span><span class="sxs-lookup"><span data-stu-id="f7c80-130">WCF does not enforce but assumes that [reference parameters] of `AcksTo` and `ReplyTo` on `CreateSequence` are identical and uses [reference parameters] from `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>

- <span data-ttu-id="f7c80-131">R1107：在使用 `Offer` 机制建立两个反向序列时，在反向序列上流动的 `SequenceAcknowledgement` 和应用程序消息必须发送到 `ReplyTo` 的 `CreateSequence` 终结点引用。</span><span class="sxs-lookup"><span data-stu-id="f7c80-131">R1107: When two converse sequences are established using the `Offer` mechanism, `SequenceAcknowledgement` and application messages flowing on converse sequences must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>

- <span data-ttu-id="f7c80-132">R1108：使用 Offer 机制建立两个反向序列时，`[address]` 的 `wsrm:AcksTo` 元素的 `wsrm:Accept` 终结点引用子元素的 `CreateSequenceResponse` 属性必须与 `CreateSequence` 的识别字节的目标 URI 相匹配。</span><span class="sxs-lookup"><span data-stu-id="f7c80-132">R1108: When two converse sequences are established using the Offer mechanism, the `[address]` property of the `wsrm:AcksTo` Endpoint Reference child element of the `wsrm:Accept` element of the `CreateSequenceResponse` must match byte-wise the destination URI of the `CreateSequence`.</span></span>

- <span data-ttu-id="f7c80-133">R1109：在使用 `Offer` 机制建立两个反向序列时，发起方发送的消息和响应方的消息确认必须发送到同一个终结点引用。</span><span class="sxs-lookup"><span data-stu-id="f7c80-133">R1109: When two converse sequences are established using the `Offer` mechanism, messages sent by initiator and acknowledgements to messages by responder must be sent to the same Endpoint Reference.</span></span>

  <span data-ttu-id="f7c80-134">WCF 使用 WS 可靠的消息传送在发起方和响应方之间建立可靠会话。</span><span class="sxs-lookup"><span data-stu-id="f7c80-134">WCF uses WS-Reliable Messaging to establish reliable sessions between the Initiator and Responder.</span></span> <span data-ttu-id="f7c80-135">WCF 的 WS 可靠消息传递实现为单向、请求-答复和全双工消息传递模式提供可靠的会话。</span><span class="sxs-lookup"><span data-stu-id="f7c80-135">WCF's WS-Reliable Messaging implementation provides reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="f7c80-136">上的 WS 可靠消息传送 `Offer` 机制 `CreateSequence` / `CreateSequenceResponse` 允许你建立两个相关的反向序列，并提供适用于所有消息终结点的会话协议。</span><span class="sxs-lookup"><span data-stu-id="f7c80-136">The WS-Reliable Messaging `Offer` mechanism on `CreateSequence`/`CreateSequenceResponse` lets you establish two correlated converse sequences, and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="f7c80-137">因为 WCF 为此类会话提供了安全保证，包括会话完整性的端到端保护，所以确保向同一方发送的消息到达同一目标是不切实际的。</span><span class="sxs-lookup"><span data-stu-id="f7c80-137">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure messages intended to the same party are arriving at the same destination.</span></span> <span data-ttu-id="f7c80-138">这也允许在应用程序消息上捎带序列确认消息。</span><span class="sxs-lookup"><span data-stu-id="f7c80-138">This also allows piggy-backing of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="f7c80-139">因此，约束 R1104、R1105 和 R1108 适用于 WCF。</span><span class="sxs-lookup"><span data-stu-id="f7c80-139">Therefore, constraints R1104, R1105, and R1108 apply to WCF.</span></span>

<span data-ttu-id="f7c80-140">`CreateSequence` 消息的一个示例。</span><span class="sxs-lookup"><span data-stu-id="f7c80-140">An example of a `CreateSequence` message.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <a:Action s:mustUnderstand="1">
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequence
    </a:Action>
    <a:ReplyTo>
      <a:Address>
         http://Business456.com/clientA
      </a:Address>
    </a:ReplyTo>
    <a:MessageID>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </a:MessageID>
    <a:To s:mustUnderstand="1">
      http://Business456.com/clientA
    </a:To>
  </s:Header>
  <s:Body>
    <wsrm:CreateSequence>
      <wsrm:AcksTo>
       <wsa:Address>
         http://Business456.com/clientA
       </wsa:Address>
     </wsrm:AcksTo>
     <wsrm:Offer>
      <wsrm:Identifier>
        urn:uuid:0afb8d36-bf26-4776-b8cf-8c91fddb5496
      </wsrm:Identifier>
     </wsrm:Offer>
   </wsrm:CreateSequence>
  </s:Body>
</s:Envelope>
```

 <span data-ttu-id="f7c80-141">`CreateSequenceResponse` 消息的一个示例。</span><span class="sxs-lookup"><span data-stu-id="f7c80-141">An example of a `CreateSequenceResponse` message.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <a:Action s:mustUnderstand="1">
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequenceResponse
    </a:Action>
    <a:RelatesTo>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </a:RelatesTo>
    <a:To s:mustUnderstand="1">
      http://Business456.com/clientA
    </a:To>
  </s:Header>
  <s:Body>
   <wsrm:CreateSequenceResponse>
    <Identifier>
     urn:uuid:eea0a36c-b38a-43e8-8c76-2fabe2d76386
    </Identifier>
    <Accept>
    <AcksTo>
      <a:Address>
        http://BusinessABC.com/serviceA
      </a:Address>
    </AcksTo>
    </Accept>
   </wsrm:CreateSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="sequence"></a><span data-ttu-id="f7c80-142">序列</span><span class="sxs-lookup"><span data-stu-id="f7c80-142">Sequence</span></span>

<span data-ttu-id="f7c80-143">以下是适用于序列的约束的列表：</span><span class="sxs-lookup"><span data-stu-id="f7c80-143">The following is a list of constraints that apply to sequences:</span></span>

- <span data-ttu-id="f7c80-144">B1201： WCF 生成并访问的序列号 `xs:long` 的最大非独占值9223372036854775807不超过最大值。</span><span class="sxs-lookup"><span data-stu-id="f7c80-144">B1201:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>

- <span data-ttu-id="f7c80-145">B1202： WCF 始终使用操作 URI 生成一个空的 expression-bodied 最后一条消息 `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` 。</span><span class="sxs-lookup"><span data-stu-id="f7c80-145">B1202:WCF always generates an empty-bodied last message with the action URI of `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span></span>

- <span data-ttu-id="f7c80-146">B1203： `LastMessage` 只要操作 URI 不为，WCF 就会接收并传递包含一个元素的序列标头的消息 `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` 。</span><span class="sxs-lookup"><span data-stu-id="f7c80-146">B1203: WCF receives and delivers a message with a Sequence header that contains a `LastMessage` element as long as the action URI is not `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span></span>

<span data-ttu-id="f7c80-147">Sequence 标头的一个示例。</span><span class="sxs-lookup"><span data-stu-id="f7c80-147">An example of a Sequence Header.</span></span>

```xml
<wsrm:Sequence>
  <wsrm:Identifier>
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
  </wsrm:Identifier>
  <wsrm:MessageNumber>
    10
  </wsrm:MessageNumber>
  <wsrm:LastMessage/>
 </wsrm:Sequence>
```

### <a name="ackrequested-header"></a><span data-ttu-id="f7c80-148">AckRequested 标头</span><span class="sxs-lookup"><span data-stu-id="f7c80-148">AckRequested Header</span></span>

<span data-ttu-id="f7c80-149">WCF 使用 `AckRequested` 标头作为 keep-alive 机制。</span><span class="sxs-lookup"><span data-stu-id="f7c80-149">WCF uses `AckRequested` Header as a keep-alive mechanism.</span></span> <span data-ttu-id="f7c80-150">WCF 不会生成可选的 `MessageNumber` 元素。</span><span class="sxs-lookup"><span data-stu-id="f7c80-150">WCF does not generate the optional `MessageNumber` element.</span></span> <span data-ttu-id="f7c80-151">接收到带有 `AckRequested` 包含元素的标头的消息时 `MessageNumber` ，WCF 将忽略该 `MessageNumber` 元素的值，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="f7c80-151">Upon receiving a message with an `AckRequested` header that contains the `MessageNumber` element, WCF ignores the `MessageNumber` element’s value, as shown in the following example.</span></span>

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
  </wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement-header"></a><span data-ttu-id="f7c80-152">SequenceAcknowledgement 标头</span><span class="sxs-lookup"><span data-stu-id="f7c80-152">SequenceAcknowledgement Header</span></span>

<span data-ttu-id="f7c80-153">WCF 对 WS-TRUST 消息中提供的序列确认使用非法携带机制。</span><span class="sxs-lookup"><span data-stu-id="f7c80-153">WCF uses piggy-back mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span>

- <span data-ttu-id="f7c80-154">R1401：使用 `Offer` 机制建立两个相反序列时，`SequenceAcknowledgement` 头可能包括在传输到预期接收方的任何应用程序消息中。</span><span class="sxs-lookup"><span data-stu-id="f7c80-154">R1401: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span>

- <span data-ttu-id="f7c80-155">B1402：在接收任何序列消息（例如，为了满足消息）之前，WCF 必须生成确认时 `AckRequested` ，wcf 将生成 `SequenceAcknowledgement` 包含范围0-0 的标头，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="f7c80-155">B1402: When WCF must generate an acknowledgement prior to receiving any sequence messages (for example, to satisfy an `AckRequested` message), WCF generates a `SequenceAcknowledgement` header that contains the range 0-0, as shown in the following example.</span></span>

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="0" Lower="0"/>
  </wsrm:SequenceAcknowledgement>
  ```

- <span data-ttu-id="f7c80-156">B1403： WCF 不生成 `SequenceAcknowledgement` 包含 `Nack` 元素但支持元素的标头 `Nack` 。</span><span class="sxs-lookup"><span data-stu-id="f7c80-156">B1403: WCF does not generate `SequenceAcknowledgement` headers that contain a `Nack` element but supports `Nack` elements.</span></span>

### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="f7c80-157">WS-ReliableMessaging 错误</span><span class="sxs-lookup"><span data-stu-id="f7c80-157">WS-ReliableMessaging Faults</span></span>

<span data-ttu-id="f7c80-158">下面列出了适用于 WS-TRUST 消息错误的 WCF 实现的约束：</span><span class="sxs-lookup"><span data-stu-id="f7c80-158">The following is a list of constraints that apply to the WCF implementation of WS-Reliable Messaging faults:</span></span>

- <span data-ttu-id="f7c80-159">B1501： WCF 不会生成 `MessageNumberRollover` 错误。</span><span class="sxs-lookup"><span data-stu-id="f7c80-159">B1501: WCF does not generate `MessageNumberRollover` faults.</span></span>

- <span data-ttu-id="f7c80-160">B1502： WCF 终结点可能生成 `CreateSequenceRefused` 错误，如规范中所述。</span><span class="sxs-lookup"><span data-stu-id="f7c80-160">B1502:WCF endpoint may generate `CreateSequenceRefused` faults as described in the specification.</span></span>

- <span data-ttu-id="f7c80-161">B1503：当服务终结点达到其连接限制并且无法处理新连接时，WCF 将生成附加的 `CreateSequenceRefused` 错误子代码， `netrm:ConnectionLimitReached` 如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="f7c80-161">B1503:When the service endpoint reaches its connection limit and cannot process new connections, WCF generates an additional `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>

  ```xml
  <s:Envelope>
    <s:Header>
      <wsa:Action>
        http://schemas.xmlsoap.org/ws/2005/08/addressing/fault
      </wsa:Action>
    </s:Header>
    <s:Body>
      <s:Fault>
        <s:Code>
          <s:Value>
            s:Receiver
          </s:Value>
          <s:Subcode>
            <s:Value>
              wsrm:CreateSequenceRefused
            </s:Value>
            <s:Subcode>
              <s:Value>
                netrm:ConnectionLimitReached
              </s:Value>
            </s:Subcode>
          </s:Subcode>
        </s:Code>
        <s:Reason>
          <s:Text xml:lang="en">
            [Reason]
          </s:Text>
        </s:Reason>
      </s:Fault>
    </s:Body>
  </s:Envelope>
  ```

### <a name="ws-addressing-faults"></a><span data-ttu-id="f7c80-162">WS-Addressing 错误</span><span class="sxs-lookup"><span data-stu-id="f7c80-162">WS-Addressing Faults</span></span>

<span data-ttu-id="f7c80-163">由于 WS 可靠消息传送使用 WS-ADDRESSING，WCF WS-TRUST 消息的实现可能会产生 WS-ADDRESSING 错误。</span><span class="sxs-lookup"><span data-stu-id="f7c80-163">Because WS-Reliable Messaging uses WS-Addressing, WCF WS-Reliable Messaging implementation may generate WS-Addressing faults.</span></span> <span data-ttu-id="f7c80-164">本部分介绍 WCF 在 WS-TRUST 消息层上显式生成的 WS 寻址错误：</span><span class="sxs-lookup"><span data-stu-id="f7c80-164">This section covers the WS-Addressing faults that WCF explicitly generates at the WS-Reliable Messaging layer:</span></span>

- <span data-ttu-id="f7c80-165">B1601：在以下条件之一成立时，WCF 将生成所需的错误消息寻址标头：</span><span class="sxs-lookup"><span data-stu-id="f7c80-165">B1601:WCF generates the fault Message Addressing Header Required when one of the following is true:</span></span>

  - <span data-ttu-id="f7c80-166">消息缺少 `Sequence` 标头和 `Action` 标头。</span><span class="sxs-lookup"><span data-stu-id="f7c80-166">A message is missing a `Sequence` header and an `Action` header.</span></span>

  - <span data-ttu-id="f7c80-167">`CreateSequence` 消息缺少 `MessageId` 标头。</span><span class="sxs-lookup"><span data-stu-id="f7c80-167">A `CreateSequence` message is missing a `MessageId` header.</span></span>

  - <span data-ttu-id="f7c80-168">`CreateSequence` 消息缺少 `ReplyTo` 标头。</span><span class="sxs-lookup"><span data-stu-id="f7c80-168">A `CreateSequence` message is missing a `ReplyTo` header.</span></span>

- <span data-ttu-id="f7c80-169">B1602： WCF 在答复缺少标头的消息时生成不支持的错误操作 `Sequence` ，并且具有不能 `Action` 在 ws-trust 消息规范中识别的标头。</span><span class="sxs-lookup"><span data-stu-id="f7c80-169">B1602:WCF generates the fault Action Not Supported in reply to a message that is missing a `Sequence` header and has an `Action` header that is not a recognized in the WS-Reliable Messaging specification.</span></span>

- <span data-ttu-id="f7c80-170">B1603： WCF 生成错误终结点不可用，以指示终结点不会根据 `CreateSequence` 消息的寻址标头的检查来处理序列。</span><span class="sxs-lookup"><span data-stu-id="f7c80-170">B1603:WCF generates the fault Endpoint Unavailable to indicate that the endpoint does not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>

## <a name="protocol-composition"></a><span data-ttu-id="f7c80-171">协议组合</span><span class="sxs-lookup"><span data-stu-id="f7c80-171">Protocol Composition</span></span>

### <a name="composition-with-ws-addressing"></a><span data-ttu-id="f7c80-172">与 WS-Addressing 组合</span><span class="sxs-lookup"><span data-stu-id="f7c80-172">Composition with WS-Addressing</span></span>

<span data-ttu-id="f7c80-173">WCF 支持两个版本的 WS-ADDRESSING： WS-ADDRESSING 2004/08 [WS-ADDRESSING] 和 W3C WS 寻址1.0 建议 [WS-ATOMICTRANSACTION] 和 [WS-ADDRESSING-SOAP]。</span><span class="sxs-lookup"><span data-stu-id="f7c80-173">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>

<span data-ttu-id="f7c80-174">尽管 WS-Reliable Messaging 规范只提及 WS-Addressing 2004/08，它并未限制要使用的 WS-Addressing 版本。</span><span class="sxs-lookup"><span data-stu-id="f7c80-174">While the WS-Reliable Messaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="f7c80-175">下面列出了适用于 WCF 的约束：</span><span class="sxs-lookup"><span data-stu-id="f7c80-175">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="f7c80-176">R2101：WS-Addressing 2004/08 和 WS-Addressing 1.0 都可以与 WS-Reliable Messaging 一起使用。</span><span class="sxs-lookup"><span data-stu-id="f7c80-176">R2101:Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>

- <span data-ttu-id="f7c80-177">R2102：必须在给定的 WS-TRUST 消息传递序列或使用机制关联的一对反向序列中使用一对 WS-ADDRESSING 的单版本 `wsrm:Offer` 。</span><span class="sxs-lookup"><span data-stu-id="f7c80-177">R2102:A single version of WS-Addressing must be used throughout a given WS-Reliable Messaging sequence or a pair of converse sequences correlated by using the `wsrm:Offer` mechanism.</span></span>

### <a name="composition-with-soap"></a><span data-ttu-id="f7c80-178">与 SOAP 组合</span><span class="sxs-lookup"><span data-stu-id="f7c80-178">Composition with SOAP</span></span>

<span data-ttu-id="f7c80-179">WCF 支持将 SOAP 1.1 和 SOAP 1.2 同时用于 WS-TRUST 消息。</span><span class="sxs-lookup"><span data-stu-id="f7c80-179">WCF supports use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>

### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="f7c80-180">与 WS-Security 和 WS-SecureConversation 组合</span><span class="sxs-lookup"><span data-stu-id="f7c80-180">Composition with WS-Security and WS-SecureConversation</span></span>

<span data-ttu-id="f7c80-181">WCF 通过使用安全传输（HTTPS）、使用 WS 安全机制和结合 WS 安全会话撰写，为 WS-MANAGEMENT 消息传递序列提供保护。</span><span class="sxs-lookup"><span data-stu-id="f7c80-181">WCF provides protection for WS-Reliable Messaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="f7c80-182">下面列出了适用于 WCF 的约束：</span><span class="sxs-lookup"><span data-stu-id="f7c80-182">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="f7c80-183">R2301：若要保护 WS-TRUST 消息序列的完整性，以及单个消息的完整性和保密性，WCF 需要使用 WS 安全对话。</span><span class="sxs-lookup"><span data-stu-id="f7c80-183">R2301:To protect the integrity of a WS-Reliable Messaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>

- <span data-ttu-id="f7c80-184">R2302：WS-Secure Conversation 会话必须在建立 WS-Reliable Messaging 序列之前建立。</span><span class="sxs-lookup"><span data-stu-id="f7c80-184">R2302:AWS-Secure Conversation session must be established prior to establishing WS-Reliable Messaging sequence(s).</span></span>

- <span data-ttu-id="f7c80-185">R2303：如果 WS-Reliable Messaging 序列生存期超过了 WS-Secure Conversation 会话的生存期，则通过使用 WS-Secure Conversation 建立的 `SecurityContextToken` 必须通过使用相应的 WS-Secure Conversation 续订绑定来进行续订。</span><span class="sxs-lookup"><span data-stu-id="f7c80-185">R2303: If the WS-Reliable Messaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>

- <span data-ttu-id="f7c80-186">B2304：WS-Reliable Messaging 序列或一对相关的反向序列总是绑定到单一的 WS-SecureConversation 会话。</span><span class="sxs-lookup"><span data-stu-id="f7c80-186">B2304:WS-Reliable Messaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>

  <span data-ttu-id="f7c80-187">WCF 源在 `wsse:SecurityTokenReference` 消息的元素可扩展性部分生成元素 `CreateSequence` 。</span><span class="sxs-lookup"><span data-stu-id="f7c80-187">The WCF source generates the `wsse:SecurityTokenReference` element in the element extensibility section of the `CreateSequence` message.</span></span>

- <span data-ttu-id="f7c80-188">R2305：使用 WS 安全会话撰写时， `CreateSequence` 消息必须包含 `wsse:SecurityTokenReference` 元素。</span><span class="sxs-lookup"><span data-stu-id="f7c80-188">R2305:When composed with WS-Secure Conversation, a `CreateSequence` message must contain the `wsse:SecurityTokenReference` element.</span></span>

## <a name="ws-reliable-messaging-ws-policy-assertion"></a><span data-ttu-id="f7c80-189">WS-Reliable Messaging WS-Policy 断言</span><span class="sxs-lookup"><span data-stu-id="f7c80-189">WS-Reliable Messaging WS-Policy Assertion</span></span>

<span data-ttu-id="f7c80-190">WCF 使用 WS 可靠的消息传递 WS 策略断言 `wsrm:RMAssertion` 来描述终结点功能。</span><span class="sxs-lookup"><span data-stu-id="f7c80-190">WCF uses WS-Reliable Messaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="f7c80-191">下面列出了适用于 WCF 的约束：</span><span class="sxs-lookup"><span data-stu-id="f7c80-191">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="f7c80-192">B3001： WCF `wsrm:RMAssertion` 将 WS 策略断言附加到 `wsdl:binding` 元素。</span><span class="sxs-lookup"><span data-stu-id="f7c80-192">B3001: WCF attaches `wsrm:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="f7c80-193">WCF 同时支持 `wsdl:binding` 和元素的附件 `wsdl:port` 。</span><span class="sxs-lookup"><span data-stu-id="f7c80-193">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>

- <span data-ttu-id="f7c80-194">B3002： WCF 支持 WS 可靠消息传递断言的以下可选属性，并在 WCF 上提供对这些属性的控制 `ReliableMessagingBindingElement` ：</span><span class="sxs-lookup"><span data-stu-id="f7c80-194">B3002: WCF supports the following optional properties of WS-Reliable Messaging assertion and provides control over them on the WCF`ReliableMessagingBindingElement`:</span></span>

  - `wsrm:InactivityTimeout`

  - `wsrm:AcknowledgementInterval`

  <span data-ttu-id="f7c80-195">下面是一个示例。</span><span class="sxs-lookup"><span data-stu-id="f7c80-195">The following is an example.</span></span>

  ```xml
  <wsrm:RMAssertion>
    <wsrm:InactivityTimeout Milliseconds="600000" />
    <wsrm:AcknowledgementInterval Milliseconds="200" />
  </wsrm:RMAssertion>
  ```

## <a name="flow-control-ws-reliable-messaging-extension"></a><span data-ttu-id="f7c80-196">流控制 WS-Reliable Messaging 扩展</span><span class="sxs-lookup"><span data-stu-id="f7c80-196">Flow Control WS-Reliable Messaging Extension</span></span>

<span data-ttu-id="f7c80-197">WCF 使用 WS 可靠的消息传递扩展性提供对序列消息流的可选更严格的控制。</span><span class="sxs-lookup"><span data-stu-id="f7c80-197">WCF uses WS-Reliable Messaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>

<span data-ttu-id="f7c80-198">通过将属性设置为，启用流控制 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> `true` 。</span><span class="sxs-lookup"><span data-stu-id="f7c80-198">Flow control is enabled by setting the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="f7c80-199">下面列出了适用于 WCF 的约束：</span><span class="sxs-lookup"><span data-stu-id="f7c80-199">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="f7c80-200">B4001：启用可靠消息流控制时，WCF 会 `netrm:BufferRemaining` 在标头的元素扩展性中生成元素 `SequenceAcknowledgement` 。</span><span class="sxs-lookup"><span data-stu-id="f7c80-200">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header.</span></span>

- <span data-ttu-id="f7c80-201">B4002：启用可靠消息流控制时，WCF 不需要 `netrm:BufferRemaining` 元素出现在 `SequenceAcknowledgement` 标头中，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="f7c80-201">B4002: When Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element to be present in `SequenceAcknowledgement` header, as shown in the following example.</span></span>

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>
      http://fabrikam123.com/abc
    </wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="1" Lower="1"/>
    <netrm:BufferRemaining>
      8
    </netrm:BufferRemaining>
  </wsrm:SequenceAcknowledgement>
  ```

- <span data-ttu-id="f7c80-202">B4003： WCF 使用 `netrm:BufferRemaining` 来指示可靠消息传送目标可以缓冲多少条新消息。</span><span class="sxs-lookup"><span data-stu-id="f7c80-202">B4003: WCF uses `netrm:BufferRemaining` to indicate how many new messages the Reliable Messaging Destination can buffer.</span></span>

- <span data-ttu-id="f7c80-203">B4004：当可靠消息目标应用程序无法快速接收消息时，WCF 可靠消息传递服务会限制传输的消息数。</span><span class="sxs-lookup"><span data-stu-id="f7c80-203">B4004:The WCF Reliable Messaging Service throttles the number of messages transmitted when the Reliable Messaging destination application cannot receive messages quickly.</span></span> <span data-ttu-id="f7c80-204">可靠消息传递目标将缓冲消息，而该元素的值将下降为 0。</span><span class="sxs-lookup"><span data-stu-id="f7c80-204">The Reliable Messaging destination buffers messages and the element’s value drops to 0.</span></span>

- <span data-ttu-id="f7c80-205">B4005： WCF 生成 `netrm:BufferRemaining` 0 到4096之间的整数值，并读取0到0之间的整数值 `xs:int` `maxInclusive` 214748364。</span><span class="sxs-lookup"><span data-stu-id="f7c80-205">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>

## <a name="message-exchange-patterns"></a><span data-ttu-id="f7c80-206">消息交换模式</span><span class="sxs-lookup"><span data-stu-id="f7c80-206">Message Exchange Patterns</span></span>

<span data-ttu-id="f7c80-207">本部分介绍在将 WS-TRUST 消息用于不同消息交换模式时，WCF 的行为。</span><span class="sxs-lookup"><span data-stu-id="f7c80-207">This section describes WCF's behavior when WS-Reliable Messaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="f7c80-208">对于每个消息交换模式，可以考虑下面的两个部署方案：</span><span class="sxs-lookup"><span data-stu-id="f7c80-208">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>

- <span data-ttu-id="f7c80-209">不可寻址发起方：发起方位于防火墙后面；响应方仅可以通过 HTTP 响应向发起方传递消息。</span><span class="sxs-lookup"><span data-stu-id="f7c80-209">Non-Addressable Initiator: Initiator is behind firewall; Responder can deliver messages to Initiator only on HTTP responses.</span></span>

- <span data-ttu-id="f7c80-210">可寻址的发起方：发起方和响应方都可以发送 HTTP 请求；换句话说，可以建立两个相反的 HTTP 连接。</span><span class="sxs-lookup"><span data-stu-id="f7c80-210">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>

### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="f7c80-211">单向、不可寻址的发起方</span><span class="sxs-lookup"><span data-stu-id="f7c80-211">One-way, Non-addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="f7c80-212">绑定</span><span class="sxs-lookup"><span data-stu-id="f7c80-212">Binding</span></span>

<span data-ttu-id="f7c80-213">WCF 通过一个 HTTP 通道使用一个序列来提供单向消息交换模式。</span><span class="sxs-lookup"><span data-stu-id="f7c80-213">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="f7c80-214">WCF 使用 HTTP 请求将所有消息从 RMS 传输到 RMD，并使用 HTTP 响应将所有消息从 RMD 传输到 RMS。</span><span class="sxs-lookup"><span data-stu-id="f7c80-214">WCF uses the HTTP requests to transmit all messages from the RMS to the RMD and the HTTP response to transmit all messages from the RMD to the RMS.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="f7c80-215">CreateSequence 交换</span><span class="sxs-lookup"><span data-stu-id="f7c80-215">CreateSequence Exchange</span></span>

<span data-ttu-id="f7c80-216">WCF 发起方将生成一 `CreateSequence` 条不含产品/服务的消息。</span><span class="sxs-lookup"><span data-stu-id="f7c80-216">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="f7c80-217">WCF 响应方确保在 `CreateSequence` 创建序列之前没有任何提议。</span><span class="sxs-lookup"><span data-stu-id="f7c80-217">The WCF Responder ensures the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="f7c80-218">WCF 响应方 `CreateSequence` 使用消息答复请求 `CreateSequenceResponse` 。</span><span class="sxs-lookup"><span data-stu-id="f7c80-218">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>

#### <a name="sequenceacknowledgement"></a><span data-ttu-id="f7c80-219">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="f7c80-219">SequenceAcknowledgement</span></span>

<span data-ttu-id="f7c80-220">WCF 发起方处理除 `CreateSequence` 消息和错误消息之外的所有消息的回复确认。</span><span class="sxs-lookup"><span data-stu-id="f7c80-220">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="f7c80-221">WCF 响应方始终在对序列和消息的响应中生成独立确认 `AckRequested` 。</span><span class="sxs-lookup"><span data-stu-id="f7c80-221">The WCF Responder always generates a stand-alone acknowledgement in the response to both sequence and `AckRequested` messages.</span></span>

#### <a name="terminatesequence-message"></a><span data-ttu-id="f7c80-222">TerminateSequence 消息</span><span class="sxs-lookup"><span data-stu-id="f7c80-222">TerminateSequence message</span></span>

<span data-ttu-id="f7c80-223">WCF 将视为单向 `TerminateSequence` 操作，这意味着 http 响应的正文和 http 202 状态代码为空。</span><span class="sxs-lookup"><span data-stu-id="f7c80-223">WCF treats `TerminateSequence` as a one-way operation, meaning the HTTP response has an empty body and HTTP 202 status code.</span></span>

### <a name="one-way-addressable-initiator"></a><span data-ttu-id="f7c80-224">单向、可寻址的发起方</span><span class="sxs-lookup"><span data-stu-id="f7c80-224">One Way, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="f7c80-225">绑定</span><span class="sxs-lookup"><span data-stu-id="f7c80-225">Binding</span></span>

<span data-ttu-id="f7c80-226">WCF 提供了一种单向消息交换模式，它在入站和出站 Http 通道上使用一个序列。</span><span class="sxs-lookup"><span data-stu-id="f7c80-226">WCF provides a one-way message exchange pattern using one sequence over an inbound and an outbound Http channel.</span></span> <span data-ttu-id="f7c80-227">WCF 使用 HTTP 请求传输所有消息。</span><span class="sxs-lookup"><span data-stu-id="f7c80-227">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="f7c80-228">所有 HTTP 响应的正文都为空，并且具有 HTTP 202 状态代码。</span><span class="sxs-lookup"><span data-stu-id="f7c80-228">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="f7c80-229">CreateSequence 交换</span><span class="sxs-lookup"><span data-stu-id="f7c80-229">CreateSequence Exchange</span></span>

<span data-ttu-id="f7c80-230">WCF 发起方将生成一 `CreateSequence` 条不含产品/服务的消息。</span><span class="sxs-lookup"><span data-stu-id="f7c80-230">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="f7c80-231">在创建序列之前，WCF 响应程序确保 `CreateSequence` 没有任何提议。</span><span class="sxs-lookup"><span data-stu-id="f7c80-231">The WCF Responder ensures that the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="f7c80-232">WCF 响应 `CreateSequenceResponse` 程序通过 `ReplyTo` 终结点引用发送的 HTTP 请求传输消息。</span><span class="sxs-lookup"><span data-stu-id="f7c80-232">The WCF Responder transmits the `CreateSequenceResponse` message on an HTTP request addressed with the `ReplyTo` endpoint reference.</span></span>

### <a name="duplex-addressable-initiator"></a><span data-ttu-id="f7c80-233">双工、可寻址的发起方</span><span class="sxs-lookup"><span data-stu-id="f7c80-233">Duplex, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="f7c80-234">绑定</span><span class="sxs-lookup"><span data-stu-id="f7c80-234">Binding</span></span>

<span data-ttu-id="f7c80-235">WCF 提供了一种完全异步的双向消息交换模式，它在入站和出站 HTTP 通道上使用两个序列。</span><span class="sxs-lookup"><span data-stu-id="f7c80-235">WCF provides a fully asynchronous two-way message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="f7c80-236">WCF 使用 HTTP 请求传输所有消息。</span><span class="sxs-lookup"><span data-stu-id="f7c80-236">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="f7c80-237">所有 HTTP 响应的正文都为空，并且具有 HTTP 202 状态代码。</span><span class="sxs-lookup"><span data-stu-id="f7c80-237">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="f7c80-238">CreateSequence 交换</span><span class="sxs-lookup"><span data-stu-id="f7c80-238">CreateSequence Exchange</span></span>

<span data-ttu-id="f7c80-239">WCF 发起方会生成一 `CreateSequence` 条包含产品/服务的消息。</span><span class="sxs-lookup"><span data-stu-id="f7c80-239">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="f7c80-240">WCF 响应方确保在 `CreateSequence` 创建序列之前具有提议。</span><span class="sxs-lookup"><span data-stu-id="f7c80-240">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="f7c80-241">WCF 将发送的 `CreateSequenceResponse` HTTP 请求发送到 `CreateSequence` 的 `ReplyTo` 终结点引用。</span><span class="sxs-lookup"><span data-stu-id="f7c80-241">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>

#### <a name="sequence-lifetime"></a><span data-ttu-id="f7c80-242">序列生存期</span><span class="sxs-lookup"><span data-stu-id="f7c80-242">Sequence Lifetime</span></span>

<span data-ttu-id="f7c80-243">WCF 将两个序列视为一个全双工会话。</span><span class="sxs-lookup"><span data-stu-id="f7c80-243">WCF treats the two sequences as one fully duplex session.</span></span>

<span data-ttu-id="f7c80-244">生成出错的错误时，WCF 要求远程终结点对这两个序列进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="f7c80-244">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="f7c80-245">读取出错一序列的错误时，WCF 会对这两个序列进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="f7c80-245">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>

<span data-ttu-id="f7c80-246">WCF 可以关闭其出站序列并继续处理其入站序列上的消息。</span><span class="sxs-lookup"><span data-stu-id="f7c80-246">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="f7c80-247">相反，WCF 可以处理入站序列的关闭，并继续按其出站序列发送消息。</span><span class="sxs-lookup"><span data-stu-id="f7c80-247">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>

### <a name="request-reply-non-addressable-initiator"></a><span data-ttu-id="f7c80-248">请求-答复、不可寻址的发起方</span><span class="sxs-lookup"><span data-stu-id="f7c80-248">Request-Reply, Non-Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="f7c80-249">绑定</span><span class="sxs-lookup"><span data-stu-id="f7c80-249">Binding</span></span>

<span data-ttu-id="f7c80-250">WCF 提供在一个 HTTP 通道上使用两个序列的单向和请求-答复消息交换模式。</span><span class="sxs-lookup"><span data-stu-id="f7c80-250">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="f7c80-251">WCF 使用 HTTP 请求来传输请求序列的消息，并使用 HTTP 响应传输答复序列的消息。</span><span class="sxs-lookup"><span data-stu-id="f7c80-251">WCF uses the HTTP requests to transmit the request sequence’s messages and uses the HTTP responses to transmit the reply sequence’s messages.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="f7c80-252">CreateSequence 交换</span><span class="sxs-lookup"><span data-stu-id="f7c80-252">CreateSequence Exchange</span></span>

<span data-ttu-id="f7c80-253">WCF 发起方会生成一 `CreateSequence` 条包含产品/服务的消息。</span><span class="sxs-lookup"><span data-stu-id="f7c80-253">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="f7c80-254">WCF 响应方确保在 `CreateSequence` 创建序列之前具有提议。</span><span class="sxs-lookup"><span data-stu-id="f7c80-254">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="f7c80-255">WCF 响应方 `CreateSequence` 使用消息答复请求 `CreateSequenceResponse` 。</span><span class="sxs-lookup"><span data-stu-id="f7c80-255">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="f7c80-256">单向消息</span><span class="sxs-lookup"><span data-stu-id="f7c80-256">One-way Message</span></span>

<span data-ttu-id="f7c80-257">若要成功完成单向消息交换协议，WCF 发起方会在 http 请求上传输请求序列消息，并 `SequenceAcknowledgement` 在 http 响应上接收独立的消息。</span><span class="sxs-lookup"><span data-stu-id="f7c80-257">To complete a one-way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="f7c80-258">`SequenceAcknowledgement` 必须确认已传输的消息。</span><span class="sxs-lookup"><span data-stu-id="f7c80-258">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>

<span data-ttu-id="f7c80-259">WCF 响应程序可以使用确认、错误或具有空正文和 HTTP 202 状态代码的响应来答复请求。</span><span class="sxs-lookup"><span data-stu-id="f7c80-259">The WCF Responder can reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>

#### <a name="two-way-messages"></a><span data-ttu-id="f7c80-260">双向消息</span><span class="sxs-lookup"><span data-stu-id="f7c80-260">Two Way Messages</span></span>

<span data-ttu-id="f7c80-261">若要成功完成双向消息交换协议，WCF 发起方会在 http 请求上传输请求序列消息，并在 HTTP 响应上接收答复序列消息。</span><span class="sxs-lookup"><span data-stu-id="f7c80-261">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="f7c80-262">响应必须包含一个确认已传输的请求序列消息的 `SequenceAcknowledgement`。</span><span class="sxs-lookup"><span data-stu-id="f7c80-262">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>

<span data-ttu-id="f7c80-263">WCF 响应程序可以使用应用程序答复、错误或正文为空的响应和 HTTP 202 状态代码来回复请求。</span><span class="sxs-lookup"><span data-stu-id="f7c80-263">The WCF Responder can reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>

<span data-ttu-id="f7c80-264">由于存在单向消息和应用程序答复的计时，因此请求序列消息的序列号与响应消息的序列号不相关联。</span><span class="sxs-lookup"><span data-stu-id="f7c80-264">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>

#### <a name="retrying-replies"></a><span data-ttu-id="f7c80-265">重试答复</span><span class="sxs-lookup"><span data-stu-id="f7c80-265">Retrying Replies</span></span>

<span data-ttu-id="f7c80-266">WCF 依赖 HTTP 请求-答复相关性进行双向消息交换协议关联。</span><span class="sxs-lookup"><span data-stu-id="f7c80-266">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="f7c80-267">因此，当确认请求序列消息时，WCF 发起方不会停止重试请求序列消息，而是在 HTTP 响应携带确认、用户消息或错误时停止。</span><span class="sxs-lookup"><span data-stu-id="f7c80-267">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries an acknowledgement, user message, or fault.</span></span> <span data-ttu-id="f7c80-268">WCF 响应方重试答复关联到的请求的 HTTP 请求阶段的答复。</span><span class="sxs-lookup"><span data-stu-id="f7c80-268">The WCF Responder retries replies on the HTTP request leg of the request to which the reply is correlated.</span></span>

#### <a name="lastmessage-exchange"></a><span data-ttu-id="f7c80-269">LastMessage 交换</span><span class="sxs-lookup"><span data-stu-id="f7c80-269">LastMessage Exchange</span></span>

<span data-ttu-id="f7c80-270">WCF 发起方在 HTTP 请求腿上生成并传输空的 expression-bodied 最后一条消息。</span><span class="sxs-lookup"><span data-stu-id="f7c80-270">The WCF Initiator generates and transmits an empty bodied last message on the HTTP request leg.</span></span> <span data-ttu-id="f7c80-271">WCF 需要一个响应，但忽略实际响应消息。</span><span class="sxs-lookup"><span data-stu-id="f7c80-271">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="f7c80-272">WCF 响应方答复请求序列的 expression-bodied 最后一条消息，该消息具有答复序列的 expression-bodied 最后一条消息。</span><span class="sxs-lookup"><span data-stu-id="f7c80-272">The WCF Responder replies to the request sequence’s empty-bodied last message with the reply sequence’s empty-bodied last message.</span></span>

<span data-ttu-id="f7c80-273">如果 WCF 响应程序收到操作 URI 不是的最后一条消息 `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` ，则 wcf 将使用最后一条消息进行答复。</span><span class="sxs-lookup"><span data-stu-id="f7c80-273">If the WCF Responder receives a last message in which the action URI is not `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`, WCF replies with a last message.</span></span> <span data-ttu-id="f7c80-274">在双向消息交换协议中，最后一条消息携带应用程序消息；在单向消息交换协议中，最后一条消息为空。</span><span class="sxs-lookup"><span data-stu-id="f7c80-274">In the case of a two-way message exchange protocol, the last message carries the application message; in the case of a one-way message exchange protocol, the last message is empty.</span></span>

<span data-ttu-id="f7c80-275">WCF 响应程序不需要确认答复序列的 expression-bodied 最后一条消息。</span><span class="sxs-lookup"><span data-stu-id="f7c80-275">The WCF Responder does not require an acknowledgement for the reply sequence’s empty-bodied last message.</span></span>

#### <a name="terminatesequence-exchange"></a><span data-ttu-id="f7c80-276">TerminateSequence 交换</span><span class="sxs-lookup"><span data-stu-id="f7c80-276">TerminateSequence Exchange</span></span>

<span data-ttu-id="f7c80-277">当所有请求都收到有效答复时，WCF 发起方会生成请求序列的消息并将其传输到 `TerminateSequence` HTTP 请求腿。</span><span class="sxs-lookup"><span data-stu-id="f7c80-277">When all requests have received a valid reply, the WCF Initiator generates and transmits the request sequence’s `TerminateSequence` message on the HTTP request leg.</span></span> <span data-ttu-id="f7c80-278">WCF 需要一个响应，但忽略实际响应消息。</span><span class="sxs-lookup"><span data-stu-id="f7c80-278">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="f7c80-279">WCF 响应方 `TerminateSequence` 用答复序列的消息答复请求序列的消息 `TerminateSequence` 。</span><span class="sxs-lookup"><span data-stu-id="f7c80-279">The WCF Responder replies to the request sequence’s `TerminateSequence` message with the reply sequence’s `TerminateSequence` message.</span></span>

<span data-ttu-id="f7c80-280">在正常的关闭序列中，两个 `TerminateSequence` 消息都携带一个完整范围的 `SequenceAcknowledgement`。</span><span class="sxs-lookup"><span data-stu-id="f7c80-280">In a normal shutdown sequence, both `TerminateSequence` messages carry a full range `SequenceAcknowledgement`.</span></span>

### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="f7c80-281">请求/答复、可寻址的发起方</span><span class="sxs-lookup"><span data-stu-id="f7c80-281">Request/Reply, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="f7c80-282">绑定</span><span class="sxs-lookup"><span data-stu-id="f7c80-282">Binding</span></span>

<span data-ttu-id="f7c80-283">WCF 在入站和出站 HTTP 通道上使用两个序列提供请求-答复消息交换模式。</span><span class="sxs-lookup"><span data-stu-id="f7c80-283">WCF provides a request-reply message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="f7c80-284">WCF 使用 HTTP 请求传输所有消息。</span><span class="sxs-lookup"><span data-stu-id="f7c80-284">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="f7c80-285">所有 HTTP 响应的正文都为空，并且具有 HTTP 202 状态代码。</span><span class="sxs-lookup"><span data-stu-id="f7c80-285">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="f7c80-286">CreateSequence 交换</span><span class="sxs-lookup"><span data-stu-id="f7c80-286">CreateSequence Exchange</span></span>

<span data-ttu-id="f7c80-287">WCF 发起方会生成一 `CreateSequence` 条包含产品/服务的消息。</span><span class="sxs-lookup"><span data-stu-id="f7c80-287">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="f7c80-288">WCF 响应方确保在 `CreateSequence` 创建序列之前具有提议。</span><span class="sxs-lookup"><span data-stu-id="f7c80-288">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="f7c80-289">WCF 将发送的 `CreateSequenceResponse` HTTP 请求发送到 `CreateSequence` 的 `ReplyTo` 终结点引用。</span><span class="sxs-lookup"><span data-stu-id="f7c80-289">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>

#### <a name="requestreply-correlation"></a><span data-ttu-id="f7c80-290">请求/答复关联</span><span class="sxs-lookup"><span data-stu-id="f7c80-290">Request/Reply Correlation</span></span>

<span data-ttu-id="f7c80-291">WCF 发起方确保所有应用程序请求消息都具有 `MessageId` 和 `ReplyTo` 终结点引用。</span><span class="sxs-lookup"><span data-stu-id="f7c80-291">The WCF Initiator ensures all application request messages bear a `MessageId` and a `ReplyTo` endpoint reference.</span></span> <span data-ttu-id="f7c80-292">WCF 发起方 `CreateSequence` `ReplyTo` 在每个应用程序请求消息上应用消息的终结点引用。</span><span class="sxs-lookup"><span data-stu-id="f7c80-292">The WCF Initiator applies the `CreateSequence` message’s `ReplyTo` endpoint reference on each application request message.</span></span> <span data-ttu-id="f7c80-293">WCF 响应程序要求传入请求消息具有 `MessageId` 和 `ReplyTo` 。</span><span class="sxs-lookup"><span data-stu-id="f7c80-293">The WCF Responder requires that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span> <span data-ttu-id="f7c80-294">WCF 响应程序确保终结点引用的 `CreateSequence` 和所有应用程序请求消息的 URI 相同。</span><span class="sxs-lookup"><span data-stu-id="f7c80-294">The WCF Responder ensures that the endpoint reference’s URI of both the `CreateSequence` and all application request messages are identical.</span></span>

---
title: 通道分块
ms.date: 03/30/2017
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
ms.openlocfilehash: 7a5e5292bcb37e83de21458716e34887a0557d91
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585540"
---
# <a name="chunking-channel"></a><span data-ttu-id="59da5-102">通道分块</span><span class="sxs-lookup"><span data-stu-id="59da5-102">Chunking Channel</span></span>

<span data-ttu-id="59da5-103">使用 Windows Communication Foundation （WCF）发送大消息时，通常需要限制用于缓冲这些消息的内存量。</span><span class="sxs-lookup"><span data-stu-id="59da5-103">When sending large messages using Windows Communication Foundation (WCF), it is often desirable to limit the amount of memory used to buffer those messages.</span></span> <span data-ttu-id="59da5-104">一种可能的解决方案是流处理消息正文（假定数据主要集中在正文中）。</span><span class="sxs-lookup"><span data-stu-id="59da5-104">One possible solution is to stream the message body (assuming the bulk of the data is in the body).</span></span> <span data-ttu-id="59da5-105">不过，有些协议要求对整个消息进行缓冲。</span><span class="sxs-lookup"><span data-stu-id="59da5-105">However some protocols require buffering of the entire message.</span></span> <span data-ttu-id="59da5-106">可靠消息和消息安全就是两个这样的示例。</span><span class="sxs-lookup"><span data-stu-id="59da5-106">Reliable messaging and security are two such examples.</span></span> <span data-ttu-id="59da5-107">另一个可能的解决方案是将大消息分割成称为消息块的小消息，一次发送一个消息块，并在接收端重建大消息。</span><span class="sxs-lookup"><span data-stu-id="59da5-107">Another possible solution is to divide up the large message into smaller messages called chunks, send those chunks one chunk at a time, and reconstitute the large message on the receiving side.</span></span> <span data-ttu-id="59da5-108">应用程序本身就能实现这种分块和取消分块，或者使用自定义通道来实现。</span><span class="sxs-lookup"><span data-stu-id="59da5-108">The application itself could do this chunking and de-chunking or it could use a custom channel to do it.</span></span> <span data-ttu-id="59da5-109">块区通道示例演示如何使用自定义协议或分层通道为任意大的消息进行分块和取消分块。</span><span class="sxs-lookup"><span data-stu-id="59da5-109">The chunking channel sample shows how a custom protocol or layered channel can be used to do chunking and de-chunking of arbitrarily large messages.</span></span>

<span data-ttu-id="59da5-110">应始终在构造了要发送的整个消息后才使用块区。</span><span class="sxs-lookup"><span data-stu-id="59da5-110">Chunking should always be employed only after the entire message to be sent has been constructed.</span></span> <span data-ttu-id="59da5-111">块区通道应始终在安全通道和可靠会话通道之下分层。</span><span class="sxs-lookup"><span data-stu-id="59da5-111">A chunking channel should always be layered below a security channel and a reliable session channel.</span></span>

> [!NOTE]
> <span data-ttu-id="59da5-112">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="59da5-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="59da5-113">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="59da5-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="59da5-114">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="59da5-114">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="59da5-115">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="59da5-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="59da5-116">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="59da5-116">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`

## <a name="chunking-channel-assumptions-and-limitations"></a><span data-ttu-id="59da5-117">块区通道的假设和限制</span><span class="sxs-lookup"><span data-stu-id="59da5-117">Chunking Channel Assumptions and Limitations</span></span>

### <a name="message-structure"></a><span data-ttu-id="59da5-118">消息结构</span><span class="sxs-lookup"><span data-stu-id="59da5-118">Message Structure</span></span>

<span data-ttu-id="59da5-119">块区通道假定要分块的消息具有下面的消息结构：</span><span class="sxs-lookup"><span data-stu-id="59da5-119">The chunking channel assumes the following message structure for messages to be chunked:</span></span>

```xml
<soap:Envelope>
  <!-- headers -->
  <soap:Body>
    <operationElement>
      <paramElement>data to be chunked</paramElement>
    </operationElement>
  </soap:Body>
</soap:Envelope>
```

<span data-ttu-id="59da5-120">在使用 ServiceModel 时，具有一个输入参数的协定操作会使其输入消息符合此消息形状。</span><span class="sxs-lookup"><span data-stu-id="59da5-120">When using the ServiceModel, contract operations that have 1 input parameter comply with this shape of message for their input message.</span></span> <span data-ttu-id="59da5-121">同样，具有一个输出参数或一个返回值的协定操作会使其输出消息符合此消息形状。</span><span class="sxs-lookup"><span data-stu-id="59da5-121">Similarly, contract operations that have 1 output parameter or return value comply with this shape of message for their output message.</span></span> <span data-ttu-id="59da5-122">下面是这种操作的示例：</span><span class="sxs-lookup"><span data-stu-id="59da5-122">The following are examples of such operations:</span></span>

```csharp
[ServiceContract]
interface ITestService
{
    [OperationContract]
    Stream EchoStream(Stream stream);

    [OperationContract]
    Stream DownloadStream();

    [OperationContract(IsOneWay = true)]
    void UploadStream(Stream stream);
}
```

### <a name="sessions"></a><span data-ttu-id="59da5-123">会话</span><span class="sxs-lookup"><span data-stu-id="59da5-123">Sessions</span></span>

<span data-ttu-id="59da5-124">块区通道要求消息以消息（消息块）的有序传递方式只传送一次。</span><span class="sxs-lookup"><span data-stu-id="59da5-124">The chunking channel requires messages to be delivered exactly once, in ordered delivery of messages (chunks).</span></span> <span data-ttu-id="59da5-125">这意味着基础通道堆栈必须是会话式的。</span><span class="sxs-lookup"><span data-stu-id="59da5-125">This means the underlying channel stack must be sessionful.</span></span> <span data-ttu-id="59da5-126">会话可以由传输提供（例如 TCP 传输），也可以由会话协议通道提供（例如 ReliableSession 通道）。</span><span class="sxs-lookup"><span data-stu-id="59da5-126">Sessions can be provided by the transport (for example, TCP transport) or by a sessionful protocol channel (for example, ReliableSession channel).</span></span>

### <a name="asynchronous-send-and-receive"></a><span data-ttu-id="59da5-127">异步发送和接收</span><span class="sxs-lookup"><span data-stu-id="59da5-127">Asynchronous Send and Receive</span></span>

<span data-ttu-id="59da5-128">此版本的块区通道示例中未实现异步发送和接收方法。</span><span class="sxs-lookup"><span data-stu-id="59da5-128">Asynchronous send and receive methods are not implemented in this version of the chunking channel sample.</span></span>

## <a name="chunking-protocol"></a><span data-ttu-id="59da5-129">块区协议</span><span class="sxs-lookup"><span data-stu-id="59da5-129">Chunking Protocol</span></span>

<span data-ttu-id="59da5-130">块区通道定义一个协议，该协议指示一系列消息块的开始点和结束点以及每个消息块的序列号。</span><span class="sxs-lookup"><span data-stu-id="59da5-130">The chunking channel defines a protocol that indicates the start and end of a series of chunks as well as the sequence number of each chunk.</span></span> <span data-ttu-id="59da5-131">下面三个示例消息演示开始消息、消息块消息和结束消息，并有说明每个消息主要特征的注释。</span><span class="sxs-lookup"><span data-stu-id="59da5-131">The following three example messages demonstrate the start, chunk and end messages with comments that describe the key aspects of each.</span></span>

### <a name="start-message"></a><span data-ttu-id="59da5-132">开始消息</span><span class="sxs-lookup"><span data-stu-id="59da5-132">Start Message</span></span>

```xml
<s:Envelope xmlns:a="http://www.w3.org/2005/08/addressing"
            xmlns:s="http://www.w3.org/2003/05/soap-envelope">
  <s:Header>
<!--Original message action is replaced with a chunking-specific action. -->
    <a:Action s:mustUnderstand="1">http://samples.microsoft.com/chunkingAction</a:Action>
<!--
Original message is assigned a unique id that is transmitted
in a MessageId header. Note that this is different from the WS-Addressing MessageId header.
-->
    <MessageId s:mustUnderstand="1" xmlns="http://samples.microsoft.com/chunking">
53f183ee-04aa-44a0-b8d3-e45224563109
</MessageId>
<!--
ChunkingStart header signals the start of a chunked message.
-->
    <ChunkingStart s:mustUnderstand="1" i:nil="true" xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://samples.microsoft.com/chunking" />
<!--
Original message action is transmitted in OriginalAction.
This is required to re-create the original message on the other side.
-->
    <OriginalAction xmlns="http://samples.microsoft.com/chunking">
http://tempuri.org/ITestService/EchoStream
    </OriginalAction>
   <!--
    All original message headers are included here.
   -->
  </s:Header>
  <s:Body>
<!--
Chunking assumes this structure of Body content:
<element>
  <childelement>large data to be chunked<childelement>
</element>
The start message contains just <element> and <childelement> without
the data to be chunked.
-->
    <EchoStream xmlns="http://tempuri.org/">
      <stream />
    </EchoStream>
  </s:Body>
</s:Envelope>
```

### <a name="chunk-message"></a><span data-ttu-id="59da5-133">消息块消息</span><span class="sxs-lookup"><span data-stu-id="59da5-133">Chunk Message</span></span>

```xml
<s:Envelope
  xmlns:a="http://www.w3.org/2005/08/addressing"
  xmlns:s="http://www.w3.org/2003/05/soap-envelope">
  <s:Header>
   <!--
    All chunking protocol messages have this action.
   -->
    <a:Action s:mustUnderstand="1">
      http://samples.microsoft.com/chunkingAction
    </a:Action>
<!--
Same as MessageId in the start message. The GUID indicates which original message this chunk belongs to.
-->
    <MessageId s:mustUnderstand="1"
               xmlns="http://samples.microsoft.com/chunking">
      53f183ee-04aa-44a0-b8d3-e45224563109
    </MessageId>
<!--
The sequence number of the chunk.
This number restarts at 1 with each new sequence of chunks.
-->
    <ChunkNumber s:mustUnderstand="1"
                 xmlns="http://samples.microsoft.com/chunking">
      1096
    </ChunkNumber>
  </s:Header>
  <s:Body>
<!--
The chunked data is wrapped in a chunk element.
The encoding of this data (and the entire message)
depends on the encoder used. The chunking channel does not mandate an encoding.
-->
    <chunk xmlns="http://samples.microsoft.com/chunking">
kfSr2QcBlkHTvQ==
    </chunk>
  </s:Body>
</s:Envelope>
```

### <a name="end-message"></a><span data-ttu-id="59da5-134">结束消息</span><span class="sxs-lookup"><span data-stu-id="59da5-134">End Message</span></span>

```xml
<s:Envelope xmlns:a="http://www.w3.org/2005/08/addressing"
            xmlns:s="http://www.w3.org/2003/05/soap-envelope">
  <s:Header>
    <a:Action s:mustUnderstand="1">
      http://samples.microsoft.com/chunkingAction
    </a:Action>
<!--
Same as MessageId in the start message. The GUID indicates which original message this chunk belongs to.
-->
    <MessageId s:mustUnderstand="1"
               xmlns="http://samples.microsoft.com/chunking">
      53f183ee-04aa-44a0-b8d3-e45224563109
    </MessageId>
<!--
ChunkingEnd header signals the end of a chunk sequence.
-->
    <ChunkingEnd s:mustUnderstand="1" i:nil="true"
                 xmlns:i="http://www.w3.org/2001/XMLSchema-instance"
                 xmlns="http://samples.microsoft.com/chunking" />
<!--
ChunkingEnd messages have a sequence number.
-->
    <ChunkNumber s:mustUnderstand="1"
                 xmlns="http://samples.microsoft.com/chunking">
      79
    </ChunkNumber>
  </s:Header>
  <s:Body>
<!--
The ChunkingEnd message has the same <element><childelement> structure
as the ChunkingStart message.
-->
    <EchoStream xmlns="http://tempuri.org/">
      <stream />
    </EchoStream>
  </s:Body>
</s:Envelope>
```

## <a name="chunking-channel-architecture"></a><span data-ttu-id="59da5-135">块区通道体系结构</span><span class="sxs-lookup"><span data-stu-id="59da5-135">Chunking Channel Architecture</span></span>

<span data-ttu-id="59da5-136">块区通道是一个在高级别遵循典型通道体系结构的 `IDuplexSessionChannel`。</span><span class="sxs-lookup"><span data-stu-id="59da5-136">The chunking channel is an `IDuplexSessionChannel` that, at a high level, follows the typical channel architecture.</span></span> <span data-ttu-id="59da5-137">有一个 `ChunkingBindingElement`，可用于生成 `ChunkingChannelFactory` 和 `ChunkingChannelListener`。</span><span class="sxs-lookup"><span data-stu-id="59da5-137">There is a `ChunkingBindingElement` that can build a `ChunkingChannelFactory` and a `ChunkingChannelListener`.</span></span> <span data-ttu-id="59da5-138">在请求时，`ChunkingChannelFactory` 可创建 `ChunkingChannel` 的实例。</span><span class="sxs-lookup"><span data-stu-id="59da5-138">The `ChunkingChannelFactory` creates instances of `ChunkingChannel` when it is asked to.</span></span> <span data-ttu-id="59da5-139">当接受新的内部通道时，`ChunkingChannelListener` 可创建 `ChunkingChannel` 的实例。</span><span class="sxs-lookup"><span data-stu-id="59da5-139">The `ChunkingChannelListener` creates instances of `ChunkingChannel` when a new inner channel is accepted.</span></span> <span data-ttu-id="59da5-140">`ChunkingChannel` 本身负责发送和接收消息。</span><span class="sxs-lookup"><span data-stu-id="59da5-140">The `ChunkingChannel` itself is responsible for sending and receiving messages.</span></span>

<span data-ttu-id="59da5-141">在下一个较低级别，`ChunkingChannel` 依赖于若干组件来实现块区协议。</span><span class="sxs-lookup"><span data-stu-id="59da5-141">At the next level down, `ChunkingChannel` relies on several components to implement the chunking protocol.</span></span> <span data-ttu-id="59da5-142">在发送端，通道使用一个名为 <xref:System.Xml.XmlDictionaryWriter> 的自定义 `ChunkingWriter`，它完成实际的分块。</span><span class="sxs-lookup"><span data-stu-id="59da5-142">On the send side, the channel uses a custom <xref:System.Xml.XmlDictionaryWriter> called `ChunkingWriter` that does the actual chunking.</span></span> <span data-ttu-id="59da5-143">`ChunkingWriter` 直接使用内部通道发送消息块。</span><span class="sxs-lookup"><span data-stu-id="59da5-143">`ChunkingWriter` uses the inner channel directly to send chunks.</span></span> <span data-ttu-id="59da5-144">使用自定义 `XmlDictionaryWriter` 可以在编写原始消息的大型正文的同时发送消息块。</span><span class="sxs-lookup"><span data-stu-id="59da5-144">Using a custom `XmlDictionaryWriter` allows us to send out chunks as the large body of the original message is being written.</span></span> <span data-ttu-id="59da5-145">这意味着不对整个原始消息进行缓冲。</span><span class="sxs-lookup"><span data-stu-id="59da5-145">This means we do not buffer the entire original message.</span></span>

![显示分块通道发送体系结构的关系图。](./media/chunking-channel/chunking-channel-send.gif)

<span data-ttu-id="59da5-147">在接收端，`ChunkingChannel` 从内部通道提取消息并将其传递到名为 <xref:System.Xml.XmlDictionaryReader> 的自定义 `ChunkingReader`，后者将从传入的消息块重组原始消息。</span><span class="sxs-lookup"><span data-stu-id="59da5-147">On the receive side, `ChunkingChannel` pulls messages from the inner channel and hands them to a custom <xref:System.Xml.XmlDictionaryReader> called `ChunkingReader`, which reconstitutes the original message from the incoming chunks.</span></span> <span data-ttu-id="59da5-148">`ChunkingChannel` 将此 `ChunkingReader` 包装到一个名为 `Message` 的自定义 `ChunkingMessage` 实现中并将此消息返回到上一层。</span><span class="sxs-lookup"><span data-stu-id="59da5-148">`ChunkingChannel` wraps this `ChunkingReader` in a custom `Message` implementation called `ChunkingMessage` and returns this message to the layer above.</span></span> <span data-ttu-id="59da5-149">通过 `ChunkingReader` 和 `ChunkingMessage` 的这一组合，可以在上一层读取原始消息正文时取消消息的分块，而不必缓冲整个原始消息正文。</span><span class="sxs-lookup"><span data-stu-id="59da5-149">This combination of `ChunkingReader` and `ChunkingMessage` allows us to de-chunk the original message body as it is being read by the layer above instead of having to buffer the entire original message body.</span></span> <span data-ttu-id="59da5-150">`ChunkingReader` 有一个队列可用来将传入的消息块缓冲为缓冲的消息块，缓冲的消息块最多可以达到可配置的最大缓冲消息块数量。</span><span class="sxs-lookup"><span data-stu-id="59da5-150">`ChunkingReader` has a queue where it buffers incoming chunks up to a maximum configurable number of buffered chunks.</span></span> <span data-ttu-id="59da5-151">当达到此最大限度时，读取器将等待上一层将消息从队列中排出（即仅从原始消息正文中读取）或等待直到达到最大接收超时值。</span><span class="sxs-lookup"><span data-stu-id="59da5-151">When this maximum limit is reached, the reader waits for messages to be drained from the queue by the layer above (that is, by just reading from the original message body) or until the maximum receive timeout is reached.</span></span>

![显示分块通道接收体系结构的关系图。](./media/chunking-channel/chunking-channel-receive.gif)

## <a name="chunking-programming-model"></a><span data-ttu-id="59da5-153">块区编程模型</span><span class="sxs-lookup"><span data-stu-id="59da5-153">Chunking Programming Model</span></span>

<span data-ttu-id="59da5-154">服务开发人员可以通过在协定中对操作应用 `ChunkingBehavior` 属性来指定哪些消息需要分块。</span><span class="sxs-lookup"><span data-stu-id="59da5-154">Service developers can specify which messages are to be chunked by applying the `ChunkingBehavior` attribute to operations within the contract.</span></span> <span data-ttu-id="59da5-155">该属性公开一个 `AppliesTo` 属性，允许开发人员指定是否对输入消息和/或输出消息应用分块。</span><span class="sxs-lookup"><span data-stu-id="59da5-155">The attribute exposes an `AppliesTo` property that allows the developer to specify whether chunking applies to the input message, the output message or both.</span></span> <span data-ttu-id="59da5-156">下面的示例演示 `ChunkingBehavior` 属性的用法：</span><span class="sxs-lookup"><span data-stu-id="59da5-156">The following example shows the usage of `ChunkingBehavior` attribute:</span></span>

```csharp
[ServiceContract]
interface ITestService
{
    [OperationContract]
    [ChunkingBehavior(ChunkingAppliesTo.Both)]
    Stream EchoStream(Stream stream);

    [OperationContract]
    [ChunkingBehavior(ChunkingAppliesTo.OutMessage)]
    Stream DownloadStream();

    [OperationContract(IsOneWay=true)]
    [ChunkingBehavior(ChunkingAppliesTo.InMessage)]
    void UploadStream(Stream stream);

}
```

<span data-ttu-id="59da5-157">`ChunkingBindingElement` 将在此编程模型中编译一个操作 URI 的列表，用于标识要分块的消息。</span><span class="sxs-lookup"><span data-stu-id="59da5-157">From this programming model, the `ChunkingBindingElement` compiles a list of action URIs that identify messages to be chunked.</span></span> <span data-ttu-id="59da5-158">每个传出消息的操作都将与此列表进行对比以确定该消息是应该进行分块还是直接发送。</span><span class="sxs-lookup"><span data-stu-id="59da5-158">The action of each outgoing message is compared against this list to determine if the message should be chunked or sent directly.</span></span>

## <a name="implementing-the-send-operation"></a><span data-ttu-id="59da5-159">实现 Send 操作</span><span class="sxs-lookup"><span data-stu-id="59da5-159">Implementing the Send Operation</span></span>

<span data-ttu-id="59da5-160">在高级别上，Send 操作首先检查传出消息是否必须分块，如果不是，则使用内部通道直接发送消息。</span><span class="sxs-lookup"><span data-stu-id="59da5-160">At a high level, the Send operation first checks whether the outgoing message must be chunked and, if not, sends the message directly using the inner channel.</span></span>

<span data-ttu-id="59da5-161">如果消息必须分块，则 Send 操作将创建一个新的 `ChunkingWriter` 并对传出消息调用 `WriteBodyContents`，同时向该消息传递此 `ChunkingWriter`。</span><span class="sxs-lookup"><span data-stu-id="59da5-161">If the message must be chunked, Send creates a new `ChunkingWriter` and calls `WriteBodyContents` on the outgoing message passing it this `ChunkingWriter`.</span></span> <span data-ttu-id="59da5-162">`ChunkingWriter` 然后进行消息分块（包括将原始消息头复制到开始消息块消息中）并使用内部通道发送消息块。</span><span class="sxs-lookup"><span data-stu-id="59da5-162">The `ChunkingWriter` then does the message chunking (including copying original message headers to the start chunk message) and sends chunks using the inner channel.</span></span>

<span data-ttu-id="59da5-163">值得注意的一些详细信息：</span><span class="sxs-lookup"><span data-stu-id="59da5-163">A few details worth noting:</span></span>

- <span data-ttu-id="59da5-164">Send 首先调用 `ThrowIfDisposedOrNotOpened` 以确保 `CommunicationState` 处于已打开状态。</span><span class="sxs-lookup"><span data-stu-id="59da5-164">Send first calls `ThrowIfDisposedOrNotOpened` to ensure the `CommunicationState` is opened.</span></span>

- <span data-ttu-id="59da5-165">发送是同步的，以便每个会话一次只发送一个消息。</span><span class="sxs-lookup"><span data-stu-id="59da5-165">Sending is synchronized so that only one message can be sent at a time for each session.</span></span> <span data-ttu-id="59da5-166">有一个名为 `ManualResetEvent` 的 `sendingDone`，在发送分块消息时将会重置。</span><span class="sxs-lookup"><span data-stu-id="59da5-166">There is a `ManualResetEvent` named `sendingDone` that is reset when a chunked message is being sent.</span></span> <span data-ttu-id="59da5-167">发送结束消息块消息后，将设置此事件。</span><span class="sxs-lookup"><span data-stu-id="59da5-167">Once the end chunk message is sent, this event is set.</span></span> <span data-ttu-id="59da5-168">Send 方法在尝试发送传出消息之前将等待设置此事件。</span><span class="sxs-lookup"><span data-stu-id="59da5-168">The Send method waits for this event to be set before it tries to send the outgoing message.</span></span>

- <span data-ttu-id="59da5-169">Send 将锁定 `CommunicationObject.ThisLock` 以防止在发送时更改同步状态。</span><span class="sxs-lookup"><span data-stu-id="59da5-169">Send locks the `CommunicationObject.ThisLock` to prevent synchronized state changes while sending.</span></span> <span data-ttu-id="59da5-170">有关 <xref:System.ServiceModel.Channels.CommunicationObject> 状态和状态机的更多信息，请参见 <xref:System.ServiceModel.Channels.CommunicationObject> 文档。</span><span class="sxs-lookup"><span data-stu-id="59da5-170">See the <xref:System.ServiceModel.Channels.CommunicationObject> documentation for more information about <xref:System.ServiceModel.Channels.CommunicationObject> states and state machine.</span></span>

- <span data-ttu-id="59da5-171">传递给 Send 的超时值用作整个发送操作（包括发送所有消息块）的超时值。</span><span class="sxs-lookup"><span data-stu-id="59da5-171">The timeout passed to Send is used as the timeout for the entire send operation which includes sending all of the chunks.</span></span>

- <span data-ttu-id="59da5-172">为避免对整个原始消息正文进行缓存，选择了自定义 <xref:System.Xml.XmlDictionaryWriter> 设计。</span><span class="sxs-lookup"><span data-stu-id="59da5-172">The custom <xref:System.Xml.XmlDictionaryWriter> design was chosen to avoid buffering the entire original message body.</span></span> <span data-ttu-id="59da5-173">如果要使用 <xref:System.Xml.XmlDictionaryReader> 对正文获取 `message.GetReaderAtBodyContents`，则将缓冲整个正文。</span><span class="sxs-lookup"><span data-stu-id="59da5-173">If we were to get an <xref:System.Xml.XmlDictionaryReader> on the body using `message.GetReaderAtBodyContents` the entire body would be buffered.</span></span> <span data-ttu-id="59da5-174">相反，我们有一个 <xref:System.Xml.XmlDictionaryWriter> 传递给的自定义 `message.WriteBodyContents` 。</span><span class="sxs-lookup"><span data-stu-id="59da5-174">Instead, we have a custom  <xref:System.Xml.XmlDictionaryWriter> that is passed to `message.WriteBodyContents`.</span></span> <span data-ttu-id="59da5-175">由于消息会在该编写器上调用 WriteBase64，因此编写器会将消息块包装成消息并使用内部通道发送消息。</span><span class="sxs-lookup"><span data-stu-id="59da5-175">As the message calls WriteBase64 on the writer, the writer packages up chunks into messages and sends them using the inner channel.</span></span> <span data-ttu-id="59da5-176">在发送信息块之前，WriteBase64 处于阻止状态。</span><span class="sxs-lookup"><span data-stu-id="59da5-176">WriteBase64 blocks until the chunk is sent.</span></span>

## <a name="implementing-the-receive-operation"></a><span data-ttu-id="59da5-177">实现 Receive 操作</span><span class="sxs-lookup"><span data-stu-id="59da5-177">Implementing the Receive Operation</span></span>

<span data-ttu-id="59da5-178">在高级别上，Receive 操作首先检查传入消息是否不为 `null` 以及其操作是否为 `ChunkingAction`。</span><span class="sxs-lookup"><span data-stu-id="59da5-178">At a high level, the Receive operation first checks that the incoming message is not `null` and that its action is the `ChunkingAction`.</span></span> <span data-ttu-id="59da5-179">如果传入消息不符合这两个条件，则会从 Receive 按原样返回该消息。</span><span class="sxs-lookup"><span data-stu-id="59da5-179">If it does not meet both criteria, the message is returned unchanged from Receive.</span></span> <span data-ttu-id="59da5-180">否则，Receive 将创建一个新的 `ChunkingReader` 和一个包装在其周围的新的 `ChunkingMessage`（通过调用 `GetNewChunkingMessage`）。</span><span class="sxs-lookup"><span data-stu-id="59da5-180">Otherwise, Receive creates a new `ChunkingReader` and a new `ChunkingMessage` wrapped around it (by calling `GetNewChunkingMessage`).</span></span> <span data-ttu-id="59da5-181">在返回该新 `ChunkingMessage` 之前，Receive 将使用线程池的线程来执行 `ReceiveChunkLoop`，它会循环调用 `innerChannel.Receive` 并将消息块发送到 `ChunkingReader`，直到收到结束消息块消息或达到接收超时值。</span><span class="sxs-lookup"><span data-stu-id="59da5-181">Before returning that new `ChunkingMessage`, Receive uses a threadpool thread to execute `ReceiveChunkLoop`, which calls `innerChannel.Receive` in a loop and hands off chunks to the `ChunkingReader` until the end chunk message is received or the receive timeout is hit.</span></span>

<span data-ttu-id="59da5-182">值得注意的一些详细信息：</span><span class="sxs-lookup"><span data-stu-id="59da5-182">A few details worth noting:</span></span>

- <span data-ttu-id="59da5-183">和 Send 一样，Receive 首先调用 `ThrowIfDisposedOrNotOepned` 以确保 `CommunicationState` 处于已打开状态。</span><span class="sxs-lookup"><span data-stu-id="59da5-183">Like Send, Receive first calls `ThrowIfDisposedOrNotOepned` to ensure the `CommunicationState` is Opened.</span></span>

- <span data-ttu-id="59da5-184">接收也是同步的，以便一次只能从会话接收一个消息。</span><span class="sxs-lookup"><span data-stu-id="59da5-184">Receive is also synchronized so that only one message can be received at a time from the session.</span></span> <span data-ttu-id="59da5-185">这一点特别重要，因为一旦接收了一个开始消息块消息，所有随后接收的消息都将是此新消息块序列中的消息块，直到接收到结束消息块消息为止。</span><span class="sxs-lookup"><span data-stu-id="59da5-185">This is especially important because once a start chunk message is received, all subsequent received messages are expected to be chunks within this new chunk sequence until an end chunk message is received.</span></span> <span data-ttu-id="59da5-186">在接收属于当前正在取消分块的消息的所有消息块之前，Receive 无法从内部通道提取消息。</span><span class="sxs-lookup"><span data-stu-id="59da5-186">Receive cannot pull messages from the inner channel until all chunks that belong to the message currently being de-chunked are received.</span></span> <span data-ttu-id="59da5-187">为了完成此操作，Receive 使用一个名为 `ManualResetEvent` 的 `currentMessageCompleted`，它是在接收到结束消息块消息时设置的，并在接收到新的开始消息块消息时重置。</span><span class="sxs-lookup"><span data-stu-id="59da5-187">To accomplish this, Receive uses a `ManualResetEvent` named `currentMessageCompleted`, which is set when the end chunk message is received and reset when a new start chunk message is received.</span></span>

- <span data-ttu-id="59da5-188">与 Send 不同，Receive 在接收时不阻止同步状态的转换。</span><span class="sxs-lookup"><span data-stu-id="59da5-188">Unlike Send, Receive does not prevent synchronized state transitions while receiving.</span></span> <span data-ttu-id="59da5-189">例如，可以在正在接收时调用 Close，并等待挂起的原始消息接收完成或达到指定的超时值。</span><span class="sxs-lookup"><span data-stu-id="59da5-189">For example, Close can be called while receiving and waits until the pending receive of the original message is completed or the specified timeout value is reached.</span></span>

- <span data-ttu-id="59da5-190">传递给 Receive 的超时值用作整个接收操作（包括接收所有消息块）的超时值。</span><span class="sxs-lookup"><span data-stu-id="59da5-190">The timeout passed to Receive is used as the timeout for the entire receive operation, which includes receiving all of the chunks.</span></span>

- <span data-ttu-id="59da5-191">如果使用消息的层在使用消息正文时的速率低于传入消息块消息的速率，则 `ChunkingReader` 会缓冲这些传入的消息块，直至达到由 `ChunkingBindingElement.MaxBufferedChunks` 指定的限制。</span><span class="sxs-lookup"><span data-stu-id="59da5-191">If the layer that consumes the message is consuming the message body at a rate lower than the rate of incoming chunk messages, the `ChunkingReader` buffers those incoming chunks up to the limit specified by `ChunkingBindingElement.MaxBufferedChunks`.</span></span> <span data-ttu-id="59da5-192">一旦达到该制，将不再从下一层拉取消息块，直到用完缓冲消息块或达到接收超时值。</span><span class="sxs-lookup"><span data-stu-id="59da5-192">Once that limit is reached, no more chunks are pulled from the lower layer until either a buffered chunk is consumed or the receive timeout is reached.</span></span>

## <a name="communicationobject-overrides"></a><span data-ttu-id="59da5-193">CommunicationObject 重写</span><span class="sxs-lookup"><span data-stu-id="59da5-193">CommunicationObject Overrides</span></span>

### <a name="onopen"></a><span data-ttu-id="59da5-194">OnOpen</span><span class="sxs-lookup"><span data-stu-id="59da5-194">OnOpen</span></span>

<span data-ttu-id="59da5-195">`OnOpen` 调用 `innerChannel.Open` 以打开内部通道。</span><span class="sxs-lookup"><span data-stu-id="59da5-195">`OnOpen` calls `innerChannel.Open` to open the inner channel.</span></span>

### <a name="onclose"></a><span data-ttu-id="59da5-196">OnClose</span><span class="sxs-lookup"><span data-stu-id="59da5-196">OnClose</span></span>

<span data-ttu-id="59da5-197">`OnClose` 首先将 `stopReceive` 设置为 `true` 以通知挂起的 `ReceiveChunkLoop` 停止。</span><span class="sxs-lookup"><span data-stu-id="59da5-197">`OnClose` first sets `stopReceive` to `true` to signal the pending `ReceiveChunkLoop` to stop.</span></span> <span data-ttu-id="59da5-198">然后，它会等待 `receiveStopped` <xref:System.Threading.ManualResetEvent> ，后者在停止时设置 `ReceiveChunkLoop` 。</span><span class="sxs-lookup"><span data-stu-id="59da5-198">It then waits for the `receiveStopped` <xref:System.Threading.ManualResetEvent>, which is set when `ReceiveChunkLoop` stops.</span></span> <span data-ttu-id="59da5-199">如果 `ReceiveChunkLoop` 在指定的超时之内停止，则 `OnClose` 将使用剩余超时调用 `innerChannel.Close`。</span><span class="sxs-lookup"><span data-stu-id="59da5-199">Assuming the `ReceiveChunkLoop` stops within the specified timeout, `OnClose` calls `innerChannel.Close` with the remaining timeout.</span></span>

### <a name="onabort"></a><span data-ttu-id="59da5-200">OnAbort</span><span class="sxs-lookup"><span data-stu-id="59da5-200">OnAbort</span></span>

<span data-ttu-id="59da5-201">`OnAbort` 调用 `innerChannel.Abort` 以中止内部通道。</span><span class="sxs-lookup"><span data-stu-id="59da5-201">`OnAbort` calls `innerChannel.Abort` to abort the inner channel.</span></span> <span data-ttu-id="59da5-202">如果有挂起的 `ReceiveChunkLoop`，则它会从挂起的 `innerChannel.Receive` 调用获取一个异常。</span><span class="sxs-lookup"><span data-stu-id="59da5-202">If there is a pending `ReceiveChunkLoop` it gets an exception from the pending `innerChannel.Receive` call.</span></span>

### <a name="onfaulted"></a><span data-ttu-id="59da5-203">OnFaulted</span><span class="sxs-lookup"><span data-stu-id="59da5-203">OnFaulted</span></span>

<span data-ttu-id="59da5-204">当通道出错时，`ChunkingChannel` 不需要特殊行为，因此不重写 `OnFaulted`。</span><span class="sxs-lookup"><span data-stu-id="59da5-204">The `ChunkingChannel` does not require special behavior when the channel is faulted so `OnFaulted` is not overridden.</span></span>

## <a name="implementing-channel-factory"></a><span data-ttu-id="59da5-205">实现通道工厂</span><span class="sxs-lookup"><span data-stu-id="59da5-205">Implementing Channel Factory</span></span>

<span data-ttu-id="59da5-206">`ChunkingChannelFactory` 负责创建 `ChunkingDuplexSessionChannel` 的实例和负责级联状态向内部通道工厂的转换。</span><span class="sxs-lookup"><span data-stu-id="59da5-206">The `ChunkingChannelFactory` is responsible for creating instances of `ChunkingDuplexSessionChannel` and for cascading state transitions to the inner channel factory.</span></span>

<span data-ttu-id="59da5-207">`OnCreateChannel` 使用内部通道工厂来创建 `IDuplexSessionChannel` 内部通道。</span><span class="sxs-lookup"><span data-stu-id="59da5-207">`OnCreateChannel` uses the inner channel factory to create an `IDuplexSessionChannel` inner channel.</span></span> <span data-ttu-id="59da5-208">然后创建新的 `ChunkingDuplexSessionChannel`，同时为其传递此内部通道以及要分块的消息操作的列表和在接收时要缓冲的消息块的最大数量。</span><span class="sxs-lookup"><span data-stu-id="59da5-208">It then creates a new `ChunkingDuplexSessionChannel` passing it this inner channel along with the list of message actions to be chunked and the maximum number of chunks to buffer upon receive.</span></span> <span data-ttu-id="59da5-209">要分块的消息操作的列表和在接收时要缓冲的消息块的最大数量是在构造函数中传递给 `ChunkingChannelFactory` 的两个参数。</span><span class="sxs-lookup"><span data-stu-id="59da5-209">The list of message actions to be chunked and the maximum number of chunks to buffer are two parameters passed to `ChunkingChannelFactory` in its constructor.</span></span> <span data-ttu-id="59da5-210">有关 `ChunkingBindingElement` 的一节说明了这些值的来源。</span><span class="sxs-lookup"><span data-stu-id="59da5-210">The section on `ChunkingBindingElement` describes where these values come from.</span></span>

<span data-ttu-id="59da5-211">`OnOpen`、`OnClose`、`OnAbort` 及其异步等效方法调用内部通道工厂上的相应状态转换方法。</span><span class="sxs-lookup"><span data-stu-id="59da5-211">The `OnOpen`, `OnClose`, `OnAbort` and their asynchronous equivalents call the corresponding state transition method on the inner channel factory.</span></span>

## <a name="implementing-channel-listener"></a><span data-ttu-id="59da5-212">实现通道侦听器</span><span class="sxs-lookup"><span data-stu-id="59da5-212">Implementing Channel Listener</span></span>

<span data-ttu-id="59da5-213">`ChunkingChannelListener` 是围绕内部通道侦听器的包装程序。</span><span class="sxs-lookup"><span data-stu-id="59da5-213">The `ChunkingChannelListener` is a wrapper around an inner channel listener.</span></span> <span data-ttu-id="59da5-214">除了将调用委托给该内部通道侦听器以外，其主要功能是在从内部通道侦听器接收的通道周围包装新的 `ChunkingDuplexSessionChannels`。</span><span class="sxs-lookup"><span data-stu-id="59da5-214">Its main function, besides delegate calls to that inner channel listener, is to wrap new `ChunkingDuplexSessionChannels` around channels accepted from the inner channel listener.</span></span> <span data-ttu-id="59da5-215">此操作在 `OnAcceptChannel` 和 `OnEndAcceptChannel` 中完成。</span><span class="sxs-lookup"><span data-stu-id="59da5-215">This is done in `OnAcceptChannel` and `OnEndAcceptChannel`.</span></span> <span data-ttu-id="59da5-216">将会向新创建的 `ChunkingDuplexSessionChannel` 传递该内部通道以及前述的其他参数。</span><span class="sxs-lookup"><span data-stu-id="59da5-216">The newly created `ChunkingDuplexSessionChannel` is passed the inner channel along with the other parameters previously described.</span></span>

## <a name="implementing-binding-element-and-binding"></a><span data-ttu-id="59da5-217">实现绑定元素和绑定</span><span class="sxs-lookup"><span data-stu-id="59da5-217">Implementing Binding Element and Binding</span></span>

<span data-ttu-id="59da5-218">`ChunkingBindingElement` 负责创建 `ChunkingChannelFactory` 和 `ChunkingChannelListener`。</span><span class="sxs-lookup"><span data-stu-id="59da5-218">`ChunkingBindingElement` is responsible for creating the `ChunkingChannelFactory` and `ChunkingChannelListener`.</span></span> <span data-ttu-id="59da5-219">`ChunkingBindingElement`检查和中的 T 是否 `CanBuildChannelFactory` \<T> `CanBuildChannelListener` \<T> 属于类型 `IDuplexSessionChannel` （块区通道支持的唯一通道）以及绑定中的其他绑定元素是否支持此通道类型。</span><span class="sxs-lookup"><span data-stu-id="59da5-219">The `ChunkingBindingElement` checks whether T in `CanBuildChannelFactory`\<T> and `CanBuildChannelListener`\<T> is of type `IDuplexSessionChannel` (the only channel supported by the chunking channel) and that the other binding elements in the binding support this channel type.</span></span>

<span data-ttu-id="59da5-220">`BuildChannelFactory`\<T>首先检查是否可以生成请求的通道类型，然后获取要分块的消息操作的列表。</span><span class="sxs-lookup"><span data-stu-id="59da5-220">`BuildChannelFactory`\<T> first checks that the requested channel type can be built and then gets a list of message actions to be chunked.</span></span> <span data-ttu-id="59da5-221">有关详细信息，请参阅以下部分。</span><span class="sxs-lookup"><span data-stu-id="59da5-221">For more information, see the following section.</span></span> <span data-ttu-id="59da5-222">然后它创建一个新的 `ChunkingChannelFactory`，同时为其传递内部通道工厂（从 `context.BuildInnerChannelFactory<IDuplexSessionChannel>` 返回）、消息操作列表和要缓冲的消息块的最大数量。</span><span class="sxs-lookup"><span data-stu-id="59da5-222">It then creates a new `ChunkingChannelFactory` passing it the inner channel factory (as returned from `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), the list of message actions, and the maximum number of chunks to buffer.</span></span> <span data-ttu-id="59da5-223">消息块的最大数量来自一个名为 `MaxBufferedChunks` 的属性，此属性由 `ChunkingBindingElement` 公开。</span><span class="sxs-lookup"><span data-stu-id="59da5-223">The maximum number of chunks comes from a property called `MaxBufferedChunks` exposed by the `ChunkingBindingElement`.</span></span>

<span data-ttu-id="59da5-224">`BuildChannelListener<T>` 有一个类似的实现，用于创建 `ChunkingChannelListener` 并为其传递内部通道侦听器。</span><span class="sxs-lookup"><span data-stu-id="59da5-224">`BuildChannelListener<T>` has a similar implementation for creating `ChunkingChannelListener` and passing it the inner channel listener.</span></span>

<span data-ttu-id="59da5-225">此示例中包括一个名为 `TcpChunkingBinding` 的示例绑定。</span><span class="sxs-lookup"><span data-stu-id="59da5-225">There is an example binding included in this sample named `TcpChunkingBinding`.</span></span> <span data-ttu-id="59da5-226">此绑定由两个绑定元素组成：`TcpTransportBindingElement` 和 `ChunkingBindingElement`。</span><span class="sxs-lookup"><span data-stu-id="59da5-226">This binding consists of two binding elements: `TcpTransportBindingElement` and `ChunkingBindingElement`.</span></span> <span data-ttu-id="59da5-227">除了公开 `MaxBufferedChunks` 属性以外，该绑定还设置几个 `TcpTransportBindingElement` 属性，如 `MaxReceivedMessageSize`（对于标头，将它设置为 `ChunkingUtils.ChunkSize` + 100KB 字节）。</span><span class="sxs-lookup"><span data-stu-id="59da5-227">In addition to exposing the `MaxBufferedChunks` property, the binding also sets some of the `TcpTransportBindingElement` properties such as `MaxReceivedMessageSize` (sets it to `ChunkingUtils.ChunkSize` + 100KB bytes for headers).</span></span>

<span data-ttu-id="59da5-228">`TcpChunkingBinding` 也实现 `IBindingRuntimePreferences` 并从 `ReceiveSynchronously` 方法返回 true，指示只实现同步的 Receive 调用。</span><span class="sxs-lookup"><span data-stu-id="59da5-228">`TcpChunkingBinding` also implements `IBindingRuntimePreferences` and returns true from the `ReceiveSynchronously` method indicating that only the synchronous Receive calls are implemented.</span></span>

### <a name="determining-which-messages-to-chunk"></a><span data-ttu-id="59da5-229">确定对哪些消息分块</span><span class="sxs-lookup"><span data-stu-id="59da5-229">Determining Which Messages To Chunk</span></span>

<span data-ttu-id="59da5-230">块区通道只对通过 `ChunkingBehavior` 属性标识的消息进行分块。</span><span class="sxs-lookup"><span data-stu-id="59da5-230">The chunking channel chunks only the messages identified through the `ChunkingBehavior` attribute.</span></span> <span data-ttu-id="59da5-231">`ChunkingBehavior` 类实现 `IOperationBehavior` 并通过调用 `AddBindingParameter` 方法来实现。</span><span class="sxs-lookup"><span data-stu-id="59da5-231">The `ChunkingBehavior` class implements `IOperationBehavior` and is implemented by calling the `AddBindingParameter` method.</span></span> <span data-ttu-id="59da5-232">在此方法中，`ChunkingBehavior` 将检查其 `AppliesTo` 属性（`InMessage` 和/或 `OutMessage`）的值以确定应该对哪些消息进行分块。</span><span class="sxs-lookup"><span data-stu-id="59da5-232">In this method, the `ChunkingBehavior` examines the value of its `AppliesTo` property (`InMessage`, `OutMessage` or both) to determine which messages should be chunked.</span></span> <span data-ttu-id="59da5-233">然后获取这些消息中每个消息的操作（从 `OperationDescription` 上的消息集合中获取），并将其添加到包含在 `ChunkingBindingParameter` 的实例内的字符串集合中。</span><span class="sxs-lookup"><span data-stu-id="59da5-233">It then gets the action of each of those messages (from the Messages collection on `OperationDescription`) and adds it to a string collection contained within an instance of `ChunkingBindingParameter`.</span></span> <span data-ttu-id="59da5-234">然后将此 `ChunkingBindingParameter` 添加到所提供的 `BindingParameterCollection` 中。</span><span class="sxs-lookup"><span data-stu-id="59da5-234">It then adds this `ChunkingBindingParameter` to the provided `BindingParameterCollection`.</span></span>

<span data-ttu-id="59da5-235">当绑定元素生成通道工厂或通道侦听器时，会在 `BindingParameterCollection` 内将此 `BindingContext` 传递给绑定中的每个绑定元素。</span><span class="sxs-lookup"><span data-stu-id="59da5-235">This `BindingParameterCollection` is passed inside the `BindingContext` to each binding element in the binding when that binding element builds the channel factory or the channel listener.</span></span> <span data-ttu-id="59da5-236">的 `ChunkingBindingElement` 实现 `BuildChannelFactory<T>` ，并 `BuildChannelListener<T>` `ChunkingBindingParameter` 将其从中提取出来 `BindingContext’` `BindingParameterCollection` 。</span><span class="sxs-lookup"><span data-stu-id="59da5-236">The `ChunkingBindingElement`'s implementation of `BuildChannelFactory<T>` and `BuildChannelListener<T>` pull this `ChunkingBindingParameter` out of the `BindingContext’`s `BindingParameterCollection`.</span></span> <span data-ttu-id="59da5-237">然后将包含在 `ChunkingBindingParameter` 内的操作集合传递给 `ChunkingChannelFactory` 或 `ChunkingChannelListener`，后者又将它传递给 `ChunkingDuplexSessionChannel`。</span><span class="sxs-lookup"><span data-stu-id="59da5-237">The collection of actions contained within the `ChunkingBindingParameter` is then passed to the `ChunkingChannelFactory` or `ChunkingChannelListener`, which in turn passes it to the `ChunkingDuplexSessionChannel`.</span></span>

## <a name="running-the-sample"></a><span data-ttu-id="59da5-238">运行示例</span><span class="sxs-lookup"><span data-stu-id="59da5-238">Running the Sample</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="59da5-239">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="59da5-239">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="59da5-240">使用以下命令安装 ASP.NET 4.0。</span><span class="sxs-lookup"><span data-stu-id="59da5-240">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="59da5-241">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="59da5-241">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="59da5-242">若要生成解决方案，请按照[生成 Windows Communication Foundation 示例](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="59da5-242">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="59da5-243">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="59da5-243">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

5. <span data-ttu-id="59da5-244">先运行 Service.exe，然后运行 Client.exe 并观察两个控制台窗口的输出。</span><span class="sxs-lookup"><span data-stu-id="59da5-244">Run Service.exe first, then run Client.exe and watch both console windows for output.</span></span>

<span data-ttu-id="59da5-245">运行此示例时，应生成下面的输出。</span><span class="sxs-lookup"><span data-stu-id="59da5-245">When running the sample, the following output is expected.</span></span>

<span data-ttu-id="59da5-246">Client：</span><span class="sxs-lookup"><span data-stu-id="59da5-246">Client:</span></span>

```console
Press enter when service is available

 > Sent chunk 1 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 2 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 3 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 4 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 5 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 6 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 7 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 8 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 9 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 10 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 1 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 2 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 3 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 4 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 5 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 6 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 7 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 8 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 9 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 10 of message 5b226ad5-c088-4988-b737-6a565e0563dd
```

<span data-ttu-id="59da5-247">服务器:</span><span class="sxs-lookup"><span data-stu-id="59da5-247">Server:</span></span>

```console
Service started, press enter to exit
 < Received chunk 1 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 2 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 3 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 4 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 5 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 6 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 7 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 8 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 9 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 10 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 1 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 2 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 3 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 4 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 5 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 6 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 7 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 8 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 9 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 10 of message 5b226ad5-c088-4988-b737-6a565e0563dd
```

---
title: 如何：启用流处理
description: 了解如何在 WCF 中启用流消息而不是默认的缓冲传输，这些传输消息必须在处理前完全接收。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6ca2cf4b-c7a1-49d8-a79b-843a90556ba4
ms.openlocfilehash: 538fd8634094aa6fbf097ddb94469d7bca749a63
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247021"
---
# <a name="how-to-enable-streaming"></a><span data-ttu-id="3577c-103">如何：启用流处理</span><span class="sxs-lookup"><span data-stu-id="3577c-103">How to: Enable Streaming</span></span>
<span data-ttu-id="3577c-104">Windows Communication Foundation （WCF）可以使用缓冲传输或流式传输发送消息。</span><span class="sxs-lookup"><span data-stu-id="3577c-104">Windows Communication Foundation (WCF) can send messages using either buffered or streamed transfers.</span></span> <span data-ttu-id="3577c-105">在默认的缓冲传输模式中，只有在一条消息全部传递完之后，接收方才能读取该消息。</span><span class="sxs-lookup"><span data-stu-id="3577c-105">In the default buffered-transfer mode, a message must be completely delivered before a receiver can read it.</span></span> <span data-ttu-id="3577c-106">在流传输模式中，不必等到消息全部传递完，接收方便可以开始处理该消息。</span><span class="sxs-lookup"><span data-stu-id="3577c-106">In streaming transfer mode, the receiver can begin to process the message before it is completely delivered.</span></span> <span data-ttu-id="3577c-107">当传递的信息很长且可以依次处理时，流模式非常有用。</span><span class="sxs-lookup"><span data-stu-id="3577c-107">The streaming mode is useful when the information that is passed is lengthy and can be processed serially.</span></span> <span data-ttu-id="3577c-108">当消息过长以致于无法全部缓冲时，流模式也非常有用。</span><span class="sxs-lookup"><span data-stu-id="3577c-108">Streaming mode is also useful when the message is too large to be entirely buffered.</span></span>  
  
 <span data-ttu-id="3577c-109">若要启用流处理，请适当地定义 `OperationContract` 并在传输级别上启用流处理。</span><span class="sxs-lookup"><span data-stu-id="3577c-109">To enable streaming, define the `OperationContract` appropriately and enable streaming at the transport level.</span></span>  
  
### <a name="to-stream-data"></a><span data-ttu-id="3577c-110">对数据进行流处理</span><span class="sxs-lookup"><span data-stu-id="3577c-110">To stream data</span></span>  
  
1. <span data-ttu-id="3577c-111">若要对数据进行流处理，服务的 `OperationContract` 必须满足两个要求：</span><span class="sxs-lookup"><span data-stu-id="3577c-111">To stream data, the `OperationContract` for the service must satisfy two requirements:</span></span>  
  
    1. <span data-ttu-id="3577c-112">保留要进行流处理的数据的参数必须是方法中的唯一参数。</span><span class="sxs-lookup"><span data-stu-id="3577c-112">The parameter that holds the data to be streamed must be the only parameter in the method.</span></span> <span data-ttu-id="3577c-113">例如，如果要对输入消息进行流处理，则该操作必须正好具有一个输入参数。</span><span class="sxs-lookup"><span data-stu-id="3577c-113">For example, if the input message is the one to be streamed, the operation must have exactly one input parameter.</span></span> <span data-ttu-id="3577c-114">同样，如果要对输出消息进行流处理，则该操作必须正好具有一个输出参数或一个返回值。</span><span class="sxs-lookup"><span data-stu-id="3577c-114">Similarly, if the output message is to be streamed, the operation must have either exactly one output parameter or a return value.</span></span>  
  
    2. <span data-ttu-id="3577c-115">参数和返回值的类型中至少有一个必须是 <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message> 或 <xref:System.Xml.Serialization.IXmlSerializable>。</span><span class="sxs-lookup"><span data-stu-id="3577c-115">At least one of the types of the parameter and return value must be either <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, or <xref:System.Xml.Serialization.IXmlSerializable>.</span></span>  
  
     <span data-ttu-id="3577c-116">下面是流处理数据的协定的示例。</span><span class="sxs-lookup"><span data-stu-id="3577c-116">The following is an example of a contract for streamed data.</span></span>  
  
     [!code-csharp[c_HowTo_EnableStreaming#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#1)]
     [!code-vb[c_HowTo_EnableStreaming#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#1)]  
  
     <span data-ttu-id="3577c-117">`GetStream` 操作接收一些缓冲输入数据作为经过缓冲的 `string`，并返回经过流处理的 `Stream`。</span><span class="sxs-lookup"><span data-stu-id="3577c-117">The `GetStream` operation receives some buffered input data as a `string`, which is buffered, and returns a `Stream`, which is streamed.</span></span> <span data-ttu-id="3577c-118">相反，`UploadStream` 接收一个经过流处理的 `Stream`，并返回一个经过缓冲的 `bool`。</span><span class="sxs-lookup"><span data-stu-id="3577c-118">Conversely `UploadStream` takes in a `Stream` (streamed) and returns a `bool` (buffered).</span></span> <span data-ttu-id="3577c-119">`EchoStream` 是输入消息和输出消息都经过流处理的操作的示例，它接收和返回 `Stream`。</span><span class="sxs-lookup"><span data-stu-id="3577c-119">`EchoStream` takes and returns `Stream` and is an example of an operation whose input and output messages are both streamed.</span></span> <span data-ttu-id="3577c-120">最后，`GetReversedStream` 将不接收输入，并返回一个 `Stream`（已经过流处理）。</span><span class="sxs-lookup"><span data-stu-id="3577c-120">Finally, `GetReversedStream` takes no inputs and returns a `Stream` (streamed).</span></span>  
  
2. <span data-ttu-id="3577c-121">必须在绑定上启用流处理。</span><span class="sxs-lookup"><span data-stu-id="3577c-121">Streaming must be enabled on the binding.</span></span> <span data-ttu-id="3577c-122">设置 `TransferMode` 属性，可以采用下面的值之一：</span><span class="sxs-lookup"><span data-stu-id="3577c-122">You set a `TransferMode` property, which can take one of the following values:</span></span>  
  
    1. <span data-ttu-id="3577c-123">`Buffered`,</span><span class="sxs-lookup"><span data-stu-id="3577c-123">`Buffered`,</span></span>  
  
    2. <span data-ttu-id="3577c-124">`Streamed`，此值在两个方向上启用流通信。</span><span class="sxs-lookup"><span data-stu-id="3577c-124">`Streamed`, which enables streaming communication in both directions.</span></span>  
  
    3. <span data-ttu-id="3577c-125">`StreamedRequest`，此值仅启用请求流处理。</span><span class="sxs-lookup"><span data-stu-id="3577c-125">`StreamedRequest`, which enables streaming the request only.</span></span>  
  
    4. <span data-ttu-id="3577c-126">`StreamedResponse`，此值仅启用响应流处理。</span><span class="sxs-lookup"><span data-stu-id="3577c-126">`StreamedResponse`, which enables streaming the response only.</span></span>  
  
     <span data-ttu-id="3577c-127">`BasicHttpBinding` 公开绑定上的 `TransferMode` 属性，与 `NetTcpBinding` 和 `NetNamedPipeBinding` 一样。</span><span class="sxs-lookup"><span data-stu-id="3577c-127">The `BasicHttpBinding` exposes the `TransferMode` property on the binding, as does `NetTcpBinding` and `NetNamedPipeBinding`.</span></span> <span data-ttu-id="3577c-128">还可以在传输绑定元素上设置 `TransferMode` 属性，并且在自定义绑定中使用。</span><span class="sxs-lookup"><span data-stu-id="3577c-128">The `TransferMode` property can also be set on the transport binding element and used in a custom binding.</span></span>  
  
     <span data-ttu-id="3577c-129">下面的示例演示如何通过代码和通过更改配置文件来设置 `TransferMode`。</span><span class="sxs-lookup"><span data-stu-id="3577c-129">The following samples show how to set `TransferMode` by code and by changing the configuration file.</span></span> <span data-ttu-id="3577c-130">两个示例都将 `maxReceivedMessageSize` 属性设置为 64 MB，这是可以接收的最大消息大小。</span><span class="sxs-lookup"><span data-stu-id="3577c-130">The samples also both set the `maxReceivedMessageSize` property to 64 MB, which places a cap on the maximum allowable size of messages on receive.</span></span> <span data-ttu-id="3577c-131">默认的 `maxReceivedMessageSize` 为 64 KB，对于流处理方案而言，此值通常太低。</span><span class="sxs-lookup"><span data-stu-id="3577c-131">The default `maxReceivedMessageSize` is 64 KB, which is usually too low for streaming scenarios.</span></span> <span data-ttu-id="3577c-132">根据应用程序期望接收的消息的最大大小适当地设置此配额设置。</span><span class="sxs-lookup"><span data-stu-id="3577c-132">Set this quota setting as appropriate depending on the maximum size of messages your application expects to receive.</span></span> <span data-ttu-id="3577c-133">还请注意，`maxBufferSize` 可控制缓冲的最大大小，应适当地进行设置。</span><span class="sxs-lookup"><span data-stu-id="3577c-133">Also note that `maxBufferSize` controls the maximum size that is buffered, and set it appropriately.</span></span>  
  
    1. <span data-ttu-id="3577c-134">下面示例中的配置段演示如何将 `TransferMode` 和自定义 HTTP 绑定上的 `basicHttpBinding` 属性设置为流处理。</span><span class="sxs-lookup"><span data-stu-id="3577c-134">The following configuration snippet from the sample shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding.</span></span>  
  
         [!code-xml[c_HowTo_EnableStreaming#103](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/common/app.config#103)]
  
    2. <span data-ttu-id="3577c-135">下面的代码段演示如何将 `TransferMode` 和自定义 HTTP 绑定上的 `basicHttpBinding` 属性设置为流处理。</span><span class="sxs-lookup"><span data-stu-id="3577c-135">The following code snippet shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding.</span></span>  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#2)]
         [!code-vb[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#2)]  
  
    3. <span data-ttu-id="3577c-136">下面的代码段演示如何将自定义 TCP 绑定上的 `TransferMode` 属性设置为流处理。</span><span class="sxs-lookup"><span data-stu-id="3577c-136">The following code snippet shows setting the `TransferMode` property to streaming on a custom TCP binding.</span></span>  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#3)]
         [!code-vb[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#3)]  
  
3. <span data-ttu-id="3577c-137">`GetStream`、`UploadStream` 和 `EchoStream` 操作都可以处理直接从文件发送数据或将接收的数据直接保存到文件的情况。</span><span class="sxs-lookup"><span data-stu-id="3577c-137">The operations `GetStream`, `UploadStream`, and `EchoStream` all deal with sending data directly from a file or saving received data directly to a file.</span></span> <span data-ttu-id="3577c-138">下面的代码适用于 `GetStream`。</span><span class="sxs-lookup"><span data-stu-id="3577c-138">The following code is for `GetStream`.</span></span>  
  
     [!code-csharp[c_HowTo_EnableStreaming#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#4)]
     [!code-vb[c_HowTo_EnableStreaming#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#4)]  
  
### <a name="writing-a-custom-stream"></a><span data-ttu-id="3577c-139">编写自定义流</span><span class="sxs-lookup"><span data-stu-id="3577c-139">Writing a custom stream</span></span>  
  
1. <span data-ttu-id="3577c-140">若要在发送或接收数据流的每个块区时对其进行特殊处理，可从 <xref:System.IO.Stream> 派生一个自定义流类。</span><span class="sxs-lookup"><span data-stu-id="3577c-140">To do special processing on each chunk of a data stream as it is being sent or received, derive a custom stream class from <xref:System.IO.Stream>.</span></span> <span data-ttu-id="3577c-141">与自定义流的示例一样，下面的代码包含 `GetReversedStream` 方法和 `ReverseStream` 类。</span><span class="sxs-lookup"><span data-stu-id="3577c-141">As an example of a custom stream, the following code contains a `GetReversedStream` method and a `ReverseStream` class-.</span></span>  
  
     <span data-ttu-id="3577c-142">`GetReversedStream` 创建并返回 `ReverseStream` 的新实例。</span><span class="sxs-lookup"><span data-stu-id="3577c-142">`GetReversedStream` creates and returns a new instance of `ReverseStream`.</span></span> <span data-ttu-id="3577c-143">当系统从 `ReverseStream` 对象中读取时，发生实际处理。</span><span class="sxs-lookup"><span data-stu-id="3577c-143">The actual processing happens as the system reads from the `ReverseStream` object.</span></span> <span data-ttu-id="3577c-144">`ReverseStream.Read` 方法从基础文件中读取字节块区，反转字节，然后返回反转的字节。</span><span class="sxs-lookup"><span data-stu-id="3577c-144">The `ReverseStream.Read` method reads a chunk of bytes from the underlying file, reverses them, then returns the reversed bytes.</span></span> <span data-ttu-id="3577c-145">此方法不会反转整个文件内容；一次只能反转一个字节块区。</span><span class="sxs-lookup"><span data-stu-id="3577c-145">This method does not reverse the entire file content; it reverses one chunk of bytes at a time.</span></span> <span data-ttu-id="3577c-146">本示例演示在从流中读取内容或将内容写入到流中时如何执行流处理。</span><span class="sxs-lookup"><span data-stu-id="3577c-146">This example shows how you can perform stream processing as the content is being read to or written from the stream.</span></span>  
  
     [!code-csharp[c_HowTo_EnableStreaming#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#2)]
     [!code-vb[c_HowTo_EnableStreaming#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="3577c-147">请参阅</span><span class="sxs-lookup"><span data-stu-id="3577c-147">See also</span></span>

- [<span data-ttu-id="3577c-148">大型数据和流</span><span class="sxs-lookup"><span data-stu-id="3577c-148">Large Data and Streaming</span></span>](large-data-and-streaming.md)
- [<span data-ttu-id="3577c-149">Stream</span><span class="sxs-lookup"><span data-stu-id="3577c-149">Stream</span></span>](../samples/stream.md)

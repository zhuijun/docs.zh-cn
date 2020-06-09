---
title: 流
ms.date: 03/30/2017
ms.assetid: 58a3db81-20ab-4627-bf31-39d30b70b4fe
ms.openlocfilehash: a482c27dfd0970b319a605a480b5f54689e42d48
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589833"
---
# <a name="stream"></a><span data-ttu-id="36a25-102">流</span><span class="sxs-lookup"><span data-stu-id="36a25-102">Stream</span></span>
<span data-ttu-id="36a25-103">流示例演示流传输模式通信的用法。</span><span class="sxs-lookup"><span data-stu-id="36a25-103">The Stream sample demonstrates the use of streaming transfer mode communication.</span></span> <span data-ttu-id="36a25-104">收发流的若干操作都由服务公开。</span><span class="sxs-lookup"><span data-stu-id="36a25-104">The service exposes several operations that send and receive streams.</span></span> <span data-ttu-id="36a25-105">此示例是自承载的。</span><span class="sxs-lookup"><span data-stu-id="36a25-105">This sample is self-hosted.</span></span> <span data-ttu-id="36a25-106">客户端和服务都是控制台程序。</span><span class="sxs-lookup"><span data-stu-id="36a25-106">Both the client and service are console programs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="36a25-107">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="36a25-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="36a25-108">Windows Communication Foundation （WCF）可在两种传输模式（缓冲或流式处理）中进行通信。</span><span class="sxs-lookup"><span data-stu-id="36a25-108">Windows Communication Foundation (WCF) can communicate in two transfer modes—buffered or streaming.</span></span> <span data-ttu-id="36a25-109">在默认的缓冲传输模式中，必须完整传递消息，接收方才能读取该消息。</span><span class="sxs-lookup"><span data-stu-id="36a25-109">In the default buffered transfer mode, a message must be completely delivered before a receiver can read it.</span></span> <span data-ttu-id="36a25-110">在流传输模式下，接收方可以在完整传递消息之前开始处理该消息。</span><span class="sxs-lookup"><span data-stu-id="36a25-110">In the streaming transfer mode, the receiver can begin to process the message before it is completely delivered.</span></span> <span data-ttu-id="36a25-111">当传递的信息很长且可以依次处理时，流模式非常有用。</span><span class="sxs-lookup"><span data-stu-id="36a25-111">The streaming mode is useful when the information that is passed is lengthy and can be processed serially.</span></span> <span data-ttu-id="36a25-112">当消息过长以致于无法全部缓冲时，流模式也非常有用。</span><span class="sxs-lookup"><span data-stu-id="36a25-112">Streaming mode is also useful when the message is too large to be entirely buffered.</span></span>  
  
## <a name="streaming-and-service-contracts"></a><span data-ttu-id="36a25-113">流处理和服务协定</span><span class="sxs-lookup"><span data-stu-id="36a25-113">Streaming and Service Contracts</span></span>  
 <span data-ttu-id="36a25-114">在设计服务协定时，可以考虑进行流处理。</span><span class="sxs-lookup"><span data-stu-id="36a25-114">Streaming is something to be considered when designing a service contract.</span></span> <span data-ttu-id="36a25-115">如果某个操作接收或返回大量数据，则应当考虑对该数据进行流处理，以免因对输入或输出消息进行缓冲而导致内存使用率过高。</span><span class="sxs-lookup"><span data-stu-id="36a25-115">If an operation receives or returns large amounts of data, you should consider streaming this data to avoid high memory utilization due to buffering of input or output messages.</span></span> <span data-ttu-id="36a25-116">若要对数据进行流处理，用来存放该数据的参数必须是消息中的唯一参数。</span><span class="sxs-lookup"><span data-stu-id="36a25-116">To stream data, the parameter that holds that data must be the only parameter in the message.</span></span> <span data-ttu-id="36a25-117">例如，如果要对输入消息进行流处理，则该操作必须正好具有一个输入参数。</span><span class="sxs-lookup"><span data-stu-id="36a25-117">For example, if the input message is the one to be streamed, the operation must have exactly one input parameter.</span></span> <span data-ttu-id="36a25-118">同样，如果要对输出消息进行流处理，则该操作必须正好具有一个输出参数或一个返回值。</span><span class="sxs-lookup"><span data-stu-id="36a25-118">Similarly, if the output message is to be streamed, the operation must have either exactly one output parameter or a return value.</span></span> <span data-ttu-id="36a25-119">在任一情况下，该参数或返回值类型必须是 `Stream`、`Message` 或 `IXmlSerializable`。</span><span class="sxs-lookup"><span data-stu-id="36a25-119">In either case, the parameter or return value type must be either `Stream`, `Message`, or `IXmlSerializable`.</span></span> <span data-ttu-id="36a25-120">下面是该流处理示例中使用的服务协定。</span><span class="sxs-lookup"><span data-stu-id="36a25-120">The following is the service contract used in this streaming sample.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IStreamingSample  
{  
    [OperationContract]  
    Stream GetStream(string data);  
    [OperationContract]  
    bool UploadStream(Stream stream);  
    [OperationContract]  
    Stream EchoStream(Stream stream);  
    [OperationContract]  
    Stream GetReversedStream();  
  
}  
```  
  
 <span data-ttu-id="36a25-121">`GetStream` 操作接收一些输入数据作为经过缓冲的字符串，并返回经过流处理的 `Stream`。</span><span class="sxs-lookup"><span data-stu-id="36a25-121">The `GetStream` operation receives some input data as a string, which is buffered, and returns a `Stream`, which is streamed.</span></span> <span data-ttu-id="36a25-122">相反，`UploadStream` 接收一个经过流处理的 `Stream`，并返回一个经过缓冲的 `bool`。</span><span class="sxs-lookup"><span data-stu-id="36a25-122">Conversely, `UploadStream` takes in a `Stream` (streamed) and returns a `bool` (buffered).</span></span> <span data-ttu-id="36a25-123">`EchoStream` 是输入消息和输出消息都经过流处理的操作的示例，它接收和返回 `Stream`。</span><span class="sxs-lookup"><span data-stu-id="36a25-123">`EchoStream` takes and returns `Stream` and is an example of an operation whose input and output messages are both streamed.</span></span> <span data-ttu-id="36a25-124">最后，`GetReversedStream` 将不接收输入，并返回一个 `Stream`（已经过流处理）。</span><span class="sxs-lookup"><span data-stu-id="36a25-124">Finally, `GetReversedStream` takes no inputs and returns a `Stream` (streamed).</span></span>  
  
## <a name="enabling-streamed-transfers"></a><span data-ttu-id="36a25-125">启用流传输</span><span class="sxs-lookup"><span data-stu-id="36a25-125">Enabling Streamed Transfers</span></span>  
 <span data-ttu-id="36a25-126">按照上面的说明定义操作协定将在编程模型级别提供流处理。</span><span class="sxs-lookup"><span data-stu-id="36a25-126">Defining operation contracts as previously described provides streaming at the programming model level.</span></span> <span data-ttu-id="36a25-127">如果仅限于此，则传输仍将缓冲整个消息内容。</span><span class="sxs-lookup"><span data-stu-id="36a25-127">If you stop there, the transport still buffers the entire message content.</span></span> <span data-ttu-id="36a25-128">若要启用传输流，请在传输的绑定元素上选择传输模式。</span><span class="sxs-lookup"><span data-stu-id="36a25-128">To enable transport streaming, select a transfer mode on the binding element of the transport.</span></span> <span data-ttu-id="36a25-129">该绑定元素具有一个 `TransferMode` 属性，该属性可以设置为 `Buffered`、`Streamed`、`StreamedRequest` 或 `StreamedResponse`。</span><span class="sxs-lookup"><span data-stu-id="36a25-129">The binding element has a `TransferMode` property that can be set to `Buffered`, `Streamed`, `StreamedRequest`, or `StreamedResponse`.</span></span> <span data-ttu-id="36a25-130">将传输模式设置为 `Streamed` 将在两个方向上启用流通信。</span><span class="sxs-lookup"><span data-stu-id="36a25-130">Setting the transfer mode to `Streamed` enables streaming communication in both directions.</span></span> <span data-ttu-id="36a25-131">将传输模式设置为 `StreamedRequest` 或 `StreamedResponse` 将分别只在请求或响应中启用流通信。</span><span class="sxs-lookup"><span data-stu-id="36a25-131">Setting the transfer mode to `StreamedRequest` or `StreamedResponse` enables streaming communication in only the request or response, respectively.</span></span>  
  
 <span data-ttu-id="36a25-132">`basicHttpBinding` 公开绑定上的 `TransferMode` 属性，这与 `NetTcpBinding` 和 `NetNamedPipeBinding` 一样。</span><span class="sxs-lookup"><span data-stu-id="36a25-132">The `basicHttpBinding` exposes the `TransferMode` property on the binding as does `NetTcpBinding` and `NetNamedPipeBinding`.</span></span> <span data-ttu-id="36a25-133">对于其他传输，必须创建一个自定义绑定以设置传输模式。</span><span class="sxs-lookup"><span data-stu-id="36a25-133">For other transports, you must create a custom binding to set the transfer mode.</span></span>  
  
 <span data-ttu-id="36a25-134">示例中的如下配置代码演示如何将 `TransferMode` 和自定义 HTTP 绑定上的 `basicHttpBinding` 属性设置为流处理：</span><span class="sxs-lookup"><span data-stu-id="36a25-134">The following configuration code from the sample shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding:</span></span>  
  
```xml  
<!-- An example basicHttpBinding using streaming. -->  
<basicHttpBinding>  
  <binding name="HttpStreaming" maxReceivedMessageSize="67108864"  
           transferMode="Streamed"/>  
</basicHttpBinding>  
<!-- An example customBinding using HTTP and streaming.-->  
<customBinding>  
  <binding name="Soap12">  
    <textMessageEncoding messageVersion="Soap12WSAddressing10" />  
    <httpTransport transferMode="Streamed"  
                   maxReceivedMessageSize="67108864"/>  
  </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="36a25-135">除了将 `transferMode` 设置为 `Streamed` 以外，上面的配置代码还将 `maxReceivedMessageSize` 设置为 64 MB。</span><span class="sxs-lookup"><span data-stu-id="36a25-135">In addition to setting the `transferMode` to `Streamed`, the previous configuration code sets the `maxReceivedMessageSize` to 64MB.</span></span> <span data-ttu-id="36a25-136">作为一个防范机制，`maxReceivedMessageSize` 为允许接收的最大消息设置了上限。</span><span class="sxs-lookup"><span data-stu-id="36a25-136">As a defense mechanism, `maxReceivedMessageSize` places a cap on the maximum allowable size of messages on receive.</span></span> <span data-ttu-id="36a25-137">默认的 `maxReceivedMessageSize` 为 64 KB，对于流处理方案而言，此值通常太低。</span><span class="sxs-lookup"><span data-stu-id="36a25-137">The default `maxReceivedMessageSize` is 64 KB, which is usually too low for streaming scenarios.</span></span>  
  
## <a name="processing-data-as-it-is-streamed"></a><span data-ttu-id="36a25-138">处理经过流处理的数据</span><span class="sxs-lookup"><span data-stu-id="36a25-138">Processing Data As It Is Streamed</span></span>  
 <span data-ttu-id="36a25-139">`GetStream`、`UploadStream` 和 `EchoStream` 操作都可以处理直接从文件发送数据或将接收的数据直接保存到文件的情况。</span><span class="sxs-lookup"><span data-stu-id="36a25-139">The operations `GetStream`, `UploadStream` and `EchoStream` all deal with sending data directly from a file or saving received data directly to a file.</span></span> <span data-ttu-id="36a25-140">但是，在某些情况下，需要发送或接收大量数据，并对正在发送或接收的数据块执行某种处理。</span><span class="sxs-lookup"><span data-stu-id="36a25-140">However in some cases, there is a requirement to send or receive large amounts of data and perform some processing on chunks of the data as it is being sent or received.</span></span> <span data-ttu-id="36a25-141">解决类似方案的一种方法是编写一个自定义流（一个派生自 <xref:System.IO.Stream> 的类）来处理读取或写入的数据。</span><span class="sxs-lookup"><span data-stu-id="36a25-141">One way to address such scenarios is to write a custom stream (a class that derives from <xref:System.IO.Stream>) that processes data as it is read or written.</span></span> <span data-ttu-id="36a25-142">`GetReversedStream` 操作和 `ReverseStream` 类就是类似方法的一个示例。</span><span class="sxs-lookup"><span data-stu-id="36a25-142">The `GetReversedStream` operation and `ReverseStream` class are an example of this.</span></span>  
  
 <span data-ttu-id="36a25-143">`GetReversedStream` 创建并返回 `ReverseStream` 的新实例。</span><span class="sxs-lookup"><span data-stu-id="36a25-143">`GetReversedStream` creates and returns a new instance of `ReverseStream`.</span></span> <span data-ttu-id="36a25-144">当系统从该 `ReverseStream` 对象中进行读取时，会发生实际的处理。</span><span class="sxs-lookup"><span data-stu-id="36a25-144">The actual processing happens as the system reads from that `ReverseStream` object.</span></span> <span data-ttu-id="36a25-145">`ReverseStream.Read` 实现从基础文件中读取字节块区，反转字节，然后返回经过反转的字节。</span><span class="sxs-lookup"><span data-stu-id="36a25-145">The `ReverseStream.Read` implementation reads a chunk of bytes from the underlying file, reverses them, then returns the reversed bytes.</span></span> <span data-ttu-id="36a25-146">这不会反转整个文件内容，而是一次仅反转一个字节块区。</span><span class="sxs-lookup"><span data-stu-id="36a25-146">This does not reverse the entire file content; it reverses one chunk of bytes at a time.</span></span> <span data-ttu-id="36a25-147">下面的示例演示在流中读取或写入内容时如何进行流处理。</span><span class="sxs-lookup"><span data-stu-id="36a25-147">This is an example to show how you can perform stream processing as the content is being read or written from and to the stream.</span></span>  
  
```csharp
class ReverseStream : Stream  
{  
  
    FileStream inStream;  
    internal ReverseStream(string filePath)  
    {  
        //Opens the file and places a StreamReader around it.  
        inStream = File.OpenRead(filePath);  
    }  
  
    // Other methods removed for brevity.  
  
    public override int Read(byte[] buffer, int offset, int count)  
    {  
        int countRead=inStream.Read(buffer, offset,count);  
        ReverseBuffer(buffer, offset, countRead);  
        return countRead;  
    }  
  
    public override void Close()  
    {  
        inStream.Close();  
        base.Close();  
    }  
    protected override void Dispose(bool disposing)  
    {  
        inStream.Dispose();  
        base.Dispose(disposing);  
    }  
    void ReverseBuffer(byte[] buffer, int offset, int count)  
    {  
        int i, j;  
        for (i = offset, j = offset + count - 1; i < j; i++, j--)  
        {  
            byte currenti = buffer[i];  
            buffer[i] = buffer[j];  
            buffer[j] = currenti;  
        }  
  
    }  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="36a25-148">运行示例</span><span class="sxs-lookup"><span data-stu-id="36a25-148">Running the Sample</span></span>  
 <span data-ttu-id="36a25-149">若要运行此示例，请首先按照本文档末尾的说明生成服务和客户端，</span><span class="sxs-lookup"><span data-stu-id="36a25-149">To run the sample, first build both the service and the client by following the directions at the end of this document.</span></span> <span data-ttu-id="36a25-150">然后在两个不同的控制台窗口中启动服务和客户端。</span><span class="sxs-lookup"><span data-stu-id="36a25-150">Then start the service and the client in two different console windows.</span></span> <span data-ttu-id="36a25-151">当客户端启动时，它会在服务就绪时等待您按 Enter。</span><span class="sxs-lookup"><span data-stu-id="36a25-151">When the client starts, it waits for you to press ENTER when the service is ready.</span></span> <span data-ttu-id="36a25-152">客户端随后会依次通过 HTTP 和 TCP 来调用 `GetStream()`、`UploadStream()` 和 `GetReversedStream()` 方法。</span><span class="sxs-lookup"><span data-stu-id="36a25-152">The client then calls the methods `GetStream()`, `UploadStream()` and `GetReversedStream()` first over HTTP and then over TCP.</span></span> <span data-ttu-id="36a25-153">下面是服务的示例输出，其后面是客户端的示例输出：</span><span class="sxs-lookup"><span data-stu-id="36a25-153">Here is an example output from the service followed by example output from the client:</span></span>  
  
 <span data-ttu-id="36a25-154">服务输出：</span><span class="sxs-lookup"><span data-stu-id="36a25-154">Service Output:</span></span>  
  
```console  
The streaming service is ready.  
Press <ENTER> to terminate service.  
  
Saving to file D:\...\uploadedfile  
......................  
File D:\...\uploadedfile saved  
Saving to file D:\...\uploadedfile  
...............  
File D:\...\uploadedfile saved  
```  
  
 <span data-ttu-id="36a25-155">客户端输出：</span><span class="sxs-lookup"><span data-stu-id="36a25-155">Client Output:</span></span>  
  
```console  
Press <ENTER> when service is ready  
------ Using HTTP ------
Calling GetStream()  
Saving to file D:\...\clientfile  
......................  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
Calling UploadStream()  
Calling GetReversedStream()  
Saving to file D:\...\clientfile  
......................  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
------ Using Custom HTTP ------  
Calling GetStream()  
Saving to file D:\...\clientfile  
...............  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
Calling UploadStream()  
Calling GetReversedStream()  
Saving to file D:\...\clientfile  
...............  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="36a25-156">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="36a25-156">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="36a25-157">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="36a25-157">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="36a25-158">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="36a25-158">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="36a25-159">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="36a25-159">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="36a25-160">如果使用 Svcutil.exe 为此示例重新生成配置，请确保在客户端配置中修改终结点名称以与客户端代码匹配。</span><span class="sxs-lookup"><span data-stu-id="36a25-160">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="36a25-161">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="36a25-161">The samples may already be installed on your machine.</span></span> <span data-ttu-id="36a25-162">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="36a25-162">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="36a25-163">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="36a25-163">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="36a25-164">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="36a25-164">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  

---
title: 自定义消息编码器：压缩编码器
ms.date: 03/30/2017
ms.assetid: 57450b6c-89fe-4b8a-8376-3d794857bfd7
ms.openlocfilehash: db20ec20579d6fcb0ec202920db0d7781b0676df
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600615"
---
# <a name="custom-message-encoder-compression-encoder"></a><span data-ttu-id="6c717-102">自定义消息编码器：压缩编码器</span><span class="sxs-lookup"><span data-stu-id="6c717-102">Custom Message Encoder: Compression Encoder</span></span>

<span data-ttu-id="6c717-103">此示例演示如何使用 Windows Communication Foundation （WCF）平台实现自定义编码器。</span><span class="sxs-lookup"><span data-stu-id="6c717-103">This sample demonstrates how to implement a custom encoder using the Windows Communication Foundation (WCF) platform.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6c717-104">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="6c717-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6c717-105">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="6c717-105">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="6c717-106">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="6c717-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6c717-107">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="6c717-107">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`

## <a name="sample-details"></a><span data-ttu-id="6c717-108">示例详细信息</span><span class="sxs-lookup"><span data-stu-id="6c717-108">Sample Details</span></span>

<span data-ttu-id="6c717-109">该示例由一个客户端控制台程序 (.exe)、一个自承载的服务控制台程序 (.exe) 和一个压缩消息编码器库 (.dll) 组成。</span><span class="sxs-lookup"><span data-stu-id="6c717-109">This sample consists of a client console program (.exe), a self-hosted service console program (.exe) and a compression message encoder library (.dll).</span></span> <span data-ttu-id="6c717-110">该服务实现定义“请求-答复”通信模式的协定。</span><span class="sxs-lookup"><span data-stu-id="6c717-110">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="6c717-111">该协定由 `ISampleServer` 接口定义，而该接口将公开基本字符串回显操作（`Echo` 和 `BigEcho`）。</span><span class="sxs-lookup"><span data-stu-id="6c717-111">The contract is defined by the `ISampleServer` interface, which exposes basic string echoing operations (`Echo` and `BigEcho`).</span></span> <span data-ttu-id="6c717-112">客户端向给定的操作发出同步请求，服务通过将该消息回送到客户端来进行回复。</span><span class="sxs-lookup"><span data-stu-id="6c717-112">The client makes synchronous requests to a given operation and the service replies by repeating the message back to the client.</span></span> <span data-ttu-id="6c717-113">客户端和服务活动显示在控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="6c717-113">Client and service activity is visible in the console windows.</span></span> <span data-ttu-id="6c717-114">提供该示例的目的在于演示如何编写自定义编码器并演示压缩消息对网络的影响。</span><span class="sxs-lookup"><span data-stu-id="6c717-114">The intent of this sample is to show how to write a custom encoder and demonstrate the impact of compression of a message on the wire.</span></span> <span data-ttu-id="6c717-115">可以为压缩消息编码器添加计算消息大小和/或处理时间的方法。</span><span class="sxs-lookup"><span data-stu-id="6c717-115">You can add instrumentation to the compression message encoder to calculate message size, processing time, or both.</span></span>

> [!NOTE]
> <span data-ttu-id="6c717-116">在 .NET Framework 4 中，如果服务器正在发送压缩响应（使用 GZip 或 Deflate 等算法创建），则会在 WCF 客户端上启用自动解压缩。</span><span class="sxs-lookup"><span data-stu-id="6c717-116">In the .NET Framework 4, automatic decompression has been enabled on a WCF client if the server is sending a compressed response (created with an algorithm such as GZip or Deflate).</span></span> <span data-ttu-id="6c717-117">如果服务是 Internet 信息服务 (IIS) 中的 Web 承载服务，则可以为该服务配置 IIS 以发送压缩响应。</span><span class="sxs-lookup"><span data-stu-id="6c717-117">If the service is Web-hosted in Internet Information Server (IIS), then IIS can be configured for the service to send a compressed response.</span></span> <span data-ttu-id="6c717-118">如果客户端和服务上都需要执行压缩和解压缩，或者如果该服务是自承载服务，则可以使用此示例。</span><span class="sxs-lookup"><span data-stu-id="6c717-118">This sample can be used if the requirement is to do compression and decompression on both the client and the service or if the service is self-hosted.</span></span>

<span data-ttu-id="6c717-119">此示例演示如何生成自定义消息编码器并将其集成到 WCF 应用程序中。</span><span class="sxs-lookup"><span data-stu-id="6c717-119">The sample demonstrates how to build and integrate a custom message encoder into a WCF application.</span></span> <span data-ttu-id="6c717-120">库 GZipEncoder.dll 是同时用客户端和服务部署的。</span><span class="sxs-lookup"><span data-stu-id="6c717-120">The library GZipEncoder.dll is deployed with both the client and the service.</span></span> <span data-ttu-id="6c717-121">该示例还演示对消息进行压缩所带来的影响。</span><span class="sxs-lookup"><span data-stu-id="6c717-121">This sample also demonstrates the impact of compressing messages.</span></span> <span data-ttu-id="6c717-122">GZipEncoder.dll 中的代码演示以下操作：</span><span class="sxs-lookup"><span data-stu-id="6c717-122">The code in GZipEncoder.dll demonstrates the following:</span></span>

- <span data-ttu-id="6c717-123">生成自定义编码器和编码器工厂。</span><span class="sxs-lookup"><span data-stu-id="6c717-123">Building a custom encoder and encoder factory.</span></span>

- <span data-ttu-id="6c717-124">为自定义编码器开发绑定元素。</span><span class="sxs-lookup"><span data-stu-id="6c717-124">Developing a binding element for a custom encoder.</span></span>

- <span data-ttu-id="6c717-125">使用自定义绑定配置集成自定义绑定元素。</span><span class="sxs-lookup"><span data-stu-id="6c717-125">Using the custom binding configuration for integrating custom binding elements.</span></span>

- <span data-ttu-id="6c717-126">开发自定义配置处理程序以允许对自定义绑定元素进行文件配置。</span><span class="sxs-lookup"><span data-stu-id="6c717-126">Developing a custom configuration handler to allow file configuration of a custom binding element.</span></span>

<span data-ttu-id="6c717-127">如上所述，在自定义编码器中实现了多个层。</span><span class="sxs-lookup"><span data-stu-id="6c717-127">As indicated previously, there are several layers that are implemented in a custom encoder.</span></span> <span data-ttu-id="6c717-128">为了更好地阐释各层之间的关系，下面列出了经过简化的服务启动事件顺序的列表：</span><span class="sxs-lookup"><span data-stu-id="6c717-128">To better illustrate the relationship between each of these layers, a simplified order of events for service start-up is in the following list:</span></span>

1. <span data-ttu-id="6c717-129">服务器启动。</span><span class="sxs-lookup"><span data-stu-id="6c717-129">The server starts.</span></span>

2. <span data-ttu-id="6c717-130">读取配置信息。</span><span class="sxs-lookup"><span data-stu-id="6c717-130">The configuration information is read.</span></span>

    1. <span data-ttu-id="6c717-131">服务配置对自定义配置处理程序进行注册。</span><span class="sxs-lookup"><span data-stu-id="6c717-131">The service configuration registers the custom configuration handler.</span></span>

    2. <span data-ttu-id="6c717-132">创建并打开服务主机。</span><span class="sxs-lookup"><span data-stu-id="6c717-132">The service host is created and opened.</span></span>

    3. <span data-ttu-id="6c717-133">自定义配置元素创建并返回自定义绑定元素。</span><span class="sxs-lookup"><span data-stu-id="6c717-133">The custom configuration element creates and returns the custom binding element.</span></span>

    4. <span data-ttu-id="6c717-134">自定义绑定元素创建并返回消息编码器工厂。</span><span class="sxs-lookup"><span data-stu-id="6c717-134">The custom binding element creates and returns a message encoder factory.</span></span>

3. <span data-ttu-id="6c717-135">接收消息。</span><span class="sxs-lookup"><span data-stu-id="6c717-135">A message is received.</span></span>

4. <span data-ttu-id="6c717-136">消息编码器工厂返回消息编码器以读入消息并写出响应。</span><span class="sxs-lookup"><span data-stu-id="6c717-136">The message encoder factory returns a message encoder for reading in the message and writing out the response.</span></span>

5. <span data-ttu-id="6c717-137">编码器层是作为类工厂实现的。</span><span class="sxs-lookup"><span data-stu-id="6c717-137">The encoder layer is implemented as a class factory.</span></span> <span data-ttu-id="6c717-138">对于自定义编码器，只有编码器类工厂才是必须公开的。</span><span class="sxs-lookup"><span data-stu-id="6c717-138">Only the encoder class factory must be publicly exposed for the custom encoder.</span></span> <span data-ttu-id="6c717-139">在创建 <xref:System.ServiceModel.ServiceHost> 或 <xref:System.ServiceModel.ChannelFactory%601> 对象时，绑定元素会返回工厂对象。</span><span class="sxs-lookup"><span data-stu-id="6c717-139">The factory object is returned by the binding element when the <xref:System.ServiceModel.ServiceHost> or <xref:System.ServiceModel.ChannelFactory%601> object is created.</span></span> <span data-ttu-id="6c717-140">消息编码器可以在缓冲模式或流模式下运行。</span><span class="sxs-lookup"><span data-stu-id="6c717-140">Message encoders can operate in a buffered or streaming mode.</span></span> <span data-ttu-id="6c717-141">此示例对缓冲模式和流模式均进行了演示。</span><span class="sxs-lookup"><span data-stu-id="6c717-141">This sample demonstrates both buffered mode and streaming mode.</span></span>

<span data-ttu-id="6c717-142">在每个模式下，`ReadMessage` 抽象类都随附了 `WriteMessage` 和 `MessageEncoder` 方法。</span><span class="sxs-lookup"><span data-stu-id="6c717-142">For each mode there is an accompanying `ReadMessage` and `WriteMessage` method on the abstract `MessageEncoder` class.</span></span> <span data-ttu-id="6c717-143">大部分编码工作都在这些方法中进行。</span><span class="sxs-lookup"><span data-stu-id="6c717-143">A majority of the encoding work takes place in these methods.</span></span> <span data-ttu-id="6c717-144">此示例包装现有的文本和二进制消息编码器。</span><span class="sxs-lookup"><span data-stu-id="6c717-144">The sample wraps the existing text and binary message encoders.</span></span> <span data-ttu-id="6c717-145">这允许该示例将对消息网络表示形式的读写操作委托给内部编码器，并允许压缩编码器对结果进行压缩或解压缩。</span><span class="sxs-lookup"><span data-stu-id="6c717-145">This allows the sample to delegate the reading and writing of the wire representation of messages to the inner encoder and allows the compression encoder to compress or decompress the results.</span></span> <span data-ttu-id="6c717-146">由于没有用于消息编码的管道，这是在 WCF 中使用多个编码器的唯一模型。</span><span class="sxs-lookup"><span data-stu-id="6c717-146">Because there is no pipeline for message encoding, this is the only model for using multiple encoders in WCF.</span></span> <span data-ttu-id="6c717-147">在对消息进行解压缩之后，所得到的消息将立即向上传递到堆栈，供通道堆栈进行处理。</span><span class="sxs-lookup"><span data-stu-id="6c717-147">Once the message has been decompressed, the resulting message is passed up the stack for the channel stack to handle.</span></span> <span data-ttu-id="6c717-148">在压缩过程中，所得到的压缩消息都直接写入所提供的流中。</span><span class="sxs-lookup"><span data-stu-id="6c717-148">During compression, the resulting compressed message is written directly to the stream provided.</span></span>

<span data-ttu-id="6c717-149">此示例使用帮助器方法（`CompressBuffer` 和 `DecompressBuffer`）执行从缓冲区到流的转换，以便使用 `GZipStream` 类。</span><span class="sxs-lookup"><span data-stu-id="6c717-149">This sample uses helper methods (`CompressBuffer` and `DecompressBuffer`) to perform conversion from buffers to streams to use the `GZipStream` class.</span></span>

<span data-ttu-id="6c717-150">经过缓冲处理的 `ReadMessage` 和 `WriteMessage` 类使用 `BufferManager` 类。</span><span class="sxs-lookup"><span data-stu-id="6c717-150">The buffered `ReadMessage` and `WriteMessage` classes make use of the `BufferManager` class.</span></span> <span data-ttu-id="6c717-151">编码器只能通过编码器工厂来访问。</span><span class="sxs-lookup"><span data-stu-id="6c717-151">The encoder is accessible only through the encoder factory.</span></span> <span data-ttu-id="6c717-152">`MessageEncoderFactory` 抽象类提供了一个名为 `Encoder` 的属性和一个名为 `CreateSessionEncoder` 的方法，前者用来访问当前的编码器，后者用来创建支持会话的编码器。</span><span class="sxs-lookup"><span data-stu-id="6c717-152">The abstract `MessageEncoderFactory` class provides a property named `Encoder` for accessing the current encoder and a method named `CreateSessionEncoder` for creating an encoder that supports sessions.</span></span> <span data-ttu-id="6c717-153">类似的编码器有序而可靠，可以用在通道支持会话的方案中。</span><span class="sxs-lookup"><span data-stu-id="6c717-153">Such an encoder can be used in the scenario where the channel supports sessions, is ordered and is reliable.</span></span> <span data-ttu-id="6c717-154">对于写入网络中的数据，此方案允许在每个会话中进行优化。</span><span class="sxs-lookup"><span data-stu-id="6c717-154">This scenario allows for optimization in each session of the data written to the wire.</span></span> <span data-ttu-id="6c717-155">如果这不是所需的，则基方法不应当重载。</span><span class="sxs-lookup"><span data-stu-id="6c717-155">If this is not desired, the base method should not be overloaded.</span></span> <span data-ttu-id="6c717-156">`Encoder` 属性提供了一种访问无会话编码器的机制，该属性的值由 `CreateSessionEncoder` 方法的默认实现返回。</span><span class="sxs-lookup"><span data-stu-id="6c717-156">The `Encoder` property provides a mechanism for accessing the session-less encoder and the default implementation of the `CreateSessionEncoder` method returns the value of the property.</span></span> <span data-ttu-id="6c717-157">由于此示例通过包装现有的编码器来提供压缩，因此 `MessageEncoderFactory` 实现接受一个表示内部编码器工厂的 `MessageEncoderFactory`。</span><span class="sxs-lookup"><span data-stu-id="6c717-157">Because the sample wraps an existing encoder to provide compression, the `MessageEncoderFactory` implementation accepts a `MessageEncoderFactory` that represents the inner encoder factory.</span></span>

<span data-ttu-id="6c717-158">定义编码器和编码器工厂后，可以将其与 WCF 客户端和服务一起使用。</span><span class="sxs-lookup"><span data-stu-id="6c717-158">Now that the encoder and encoder factory are defined, they can be used with a WCF client and service.</span></span> <span data-ttu-id="6c717-159">但是，必须将这些编码器添加到通道堆栈中。</span><span class="sxs-lookup"><span data-stu-id="6c717-159">However, these encoders must be added to the channel stack.</span></span> <span data-ttu-id="6c717-160">您可以从 <xref:System.ServiceModel.ServiceHost> 和 <xref:System.ServiceModel.ChannelFactory%601> 类派生类，并重写 `OnInitialize` 方法以手动添加该编码器工厂。</span><span class="sxs-lookup"><span data-stu-id="6c717-160">You can derive classes from the <xref:System.ServiceModel.ServiceHost> and <xref:System.ServiceModel.ChannelFactory%601> classes and override the `OnInitialize` methods to add this encoder factory manually.</span></span> <span data-ttu-id="6c717-161">还可以通过自定义绑定元素来公开编码器工厂。</span><span class="sxs-lookup"><span data-stu-id="6c717-161">You can also expose the encoder factory through a custom binding element.</span></span>

<span data-ttu-id="6c717-162">若要创建新的自定义绑定元素，请从 <xref:System.ServiceModel.Channels.BindingElement> 类派生一个类。</span><span class="sxs-lookup"><span data-stu-id="6c717-162">To create a new custom binding element, derive a class from the <xref:System.ServiceModel.Channels.BindingElement> class.</span></span> <span data-ttu-id="6c717-163">但是，存在多种类型的绑定元素。</span><span class="sxs-lookup"><span data-stu-id="6c717-163">There are, however, several types of binding elements.</span></span> <span data-ttu-id="6c717-164">为了确保自定义绑定元素被识别为消息编码绑定元素，还必须实现 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="6c717-164">To ensure that the custom binding element is recognized as a message encoding binding element, you also must implement the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.</span></span> <span data-ttu-id="6c717-165"><xref:System.ServiceModel.Channels.MessageEncodingBindingElement> 公开了一种用来新建消息编码器工厂的方法 (`CreateMessageEncoderFactory`)，实现该方法的目的在于返回匹配的消息编码器工厂的实例。</span><span class="sxs-lookup"><span data-stu-id="6c717-165">The <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> exposes a method for creating a new message encoder factory (`CreateMessageEncoderFactory`), which is implemented to return an instance of the matching message encoder factory.</span></span> <span data-ttu-id="6c717-166">另外，<xref:System.ServiceModel.Channels.MessageEncodingBindingElement> 还有一个指示寻址版本的属性。</span><span class="sxs-lookup"><span data-stu-id="6c717-166">Additionally, the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> has a property to indicate the addressing version.</span></span> <span data-ttu-id="6c717-167">由于此示例包装现有的编码器，因此示例实现还会包装现有的编码器绑定元素、将内部编码器绑定元素作为构造函数的参数并通过一个属性来公开它。</span><span class="sxs-lookup"><span data-stu-id="6c717-167">Because this sample wraps the existing encoders, the sample implementation also wraps the existing encoder binding elements and takes an inner encoder binding element as a parameter to the constructor and exposes it through a property.</span></span> <span data-ttu-id="6c717-168">下面的示例代码演示 `GZipMessageEncodingBindingElement` 类的实现。</span><span class="sxs-lookup"><span data-stu-id="6c717-168">The following sample code shows the implementation of the `GZipMessageEncodingBindingElement` class.</span></span>

```csharp
public sealed class GZipMessageEncodingBindingElement
                        : MessageEncodingBindingElement //BindingElement
                        , IPolicyExportExtension
{

    //We use an inner binding element to store information
    //required for the inner encoder.
    MessageEncodingBindingElement innerBindingElement;

        //By default, use the default text encoder as the inner encoder.
        public GZipMessageEncodingBindingElement()
            : this(new TextMessageEncodingBindingElement()) { }

    public GZipMessageEncodingBindingElement(MessageEncodingBindingElement messageEncoderBindingElement)
    {
        this.innerBindingElement = messageEncoderBindingElement;
    }

    public MessageEncodingBindingElement InnerMessageEncodingBindingElement
    {
        get { return innerBindingElement; }
        set { innerBindingElement = value; }
    }

    //Main entry point into the encoder binding element.
    // Called by WCF to get the factory that creates the
    //message encoder.
    public override MessageEncoderFactory CreateMessageEncoderFactory()
    {
        return new
GZipMessageEncoderFactory(innerBindingElement.CreateMessageEncoderFactory());
    }

    public override MessageVersion MessageVersion
    {
        get { return innerBindingElement.MessageVersion; }
        set { innerBindingElement.MessageVersion = value; }
    }

    public override BindingElement Clone()
    {
        return new
        GZipMessageEncodingBindingElement(this.innerBindingElement);
    }

    public override T GetProperty<T>(BindingContext context)
    {
        if (typeof(T) == typeof(XmlDictionaryReaderQuotas))
        {
            return innerBindingElement.GetProperty<T>(context);
        }
        else
        {
            return base.GetProperty<T>(context);
        }
    }

    public override IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)
    {
        if (context == null)
            throw new ArgumentNullException("context");

        context.BindingParameters.Add(this);
        return context.BuildInnerChannelFactory<TChannel>();
    }

    public override IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)
    {
        if (context == null)
            throw new ArgumentNullException("context");

        context.BindingParameters.Add(this);
        return context.BuildInnerChannelListener<TChannel>();
    }

    public override bool CanBuildChannelListener<TChannel>(BindingContext context)
    {
        if (context == null)
            throw new ArgumentNullException("context");

        context.BindingParameters.Add(this);
        return context.CanBuildInnerChannelListener<TChannel>();
    }

    void IPolicyExportExtension.ExportPolicy(MetadataExporter exporter, PolicyConversionContext policyContext)
    {
        if (policyContext == null)
        {
            throw new ArgumentNullException("policyContext");
        }
       XmlDocument document = new XmlDocument();
       policyContext.GetBindingAssertions().Add(document.CreateElement(
            GZipMessageEncodingPolicyConstants.GZipEncodingPrefix,
            GZipMessageEncodingPolicyConstants.GZipEncodingName,
            GZipMessageEncodingPolicyConstants.GZipEncodingNamespace));
    }
}
```

<span data-ttu-id="6c717-169">请注意，`GZipMessageEncodingBindingElement` 类实现 `IPolicyExportExtension` 接口，以使该绑定元素可以作为元数据中的策略导出，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="6c717-169">Note that `GZipMessageEncodingBindingElement` class implements the `IPolicyExportExtension` interface, so that this binding element can be exported as a policy in metadata, as shown in the following example.</span></span>

```xml
<wsp:Policy wsu:Id="BufferedHttpSampleServer_ISampleServer_policy">
    <wsp:ExactlyOne>
      <wsp:All>
        <gzip:text xmlns:gzip=
        "http://schemas.microsoft.com/ws/06/2004/mspolicy/netgzip1" />
       <wsaw:UsingAddressing />
     </wsp:All>
   </wsp:ExactlyOne>
</wsp:Policy>
```

<span data-ttu-id="6c717-170">`GZipMessageEncodingBindingElementImporter` 类实现 `IPolicyImportExtension` 接口，该类导入 `GZipMessageEncodingBindingElement` 的策略。</span><span class="sxs-lookup"><span data-stu-id="6c717-170">The `GZipMessageEncodingBindingElementImporter` class implements the `IPolicyImportExtension` interface, this class imports policy for `GZipMessageEncodingBindingElement`.</span></span> <span data-ttu-id="6c717-171">Svcutil.exe 工具可用于将策略导入到配置文件中以处理 `GZipMessageEncodingBindingElement`，应将下面的代码添加到 Svcutil.exe.config 中。</span><span class="sxs-lookup"><span data-stu-id="6c717-171">Svcutil.exe tool can be used to import policies to the configuration file, to handle `GZipMessageEncodingBindingElement`, the following should be added to Svcutil.exe.config.</span></span>

```xml
<configuration>
  <system.serviceModel>
    <extensions>
      <bindingElementExtensions>
        <add name="gzipMessageEncoding"
          type=
            "Microsoft.ServiceModel.Samples.GZipMessageEncodingElement, GZipEncoder, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
      </bindingElementExtensions>
    </extensions>
    <client>
      <metadata>
        <policyImporters>
          <remove type=
"System.ServiceModel.Channels.MessageEncodingBindingElementImporter, System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
          <extension type=
"Microsoft.ServiceModel.Samples.GZipMessageEncodingBindingElementImporter, GZipEncoder, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
        </policyImporters>
      </metadata>
    </client>
  </system.serviceModel>
</configuration>
```

<span data-ttu-id="6c717-172">现在压缩编码器具有一个匹配的绑定元素，可以通过编程方式将它挂钩到服务或客户端，方法是构造新的自定义绑定对象并向其中添加自定义绑定元素，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="6c717-172">Now that there is a matching binding element for the compression encoder, it can be programmatically hooked into the service or client by constructing a new custom binding object and adding the custom binding element to it, as shown in the following sample code.</span></span>

```csharp
ICollection<BindingElement> bindingElements = new List<BindingElement>();
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();
GZipMessageEncodingBindingElement compBindingElement = new GZipMessageEncodingBindingElement ();
bindingElements.Add(compBindingElement);
bindingElements.Add(httpBindingElement);
CustomBinding binding = new CustomBinding(bindingElements);
binding.Name = "SampleBinding";
binding.Namespace = "http://tempuri.org/bindings";
```

<span data-ttu-id="6c717-173">尽管对于大多数用户方案该操作已足够，但是，如果某个服务是由 Web 承载的，则支持文件配置是至关重要的。</span><span class="sxs-lookup"><span data-stu-id="6c717-173">While this may be sufficient for the majority of user scenarios, supporting a file configuration is critical if a service is to be Web-hosted.</span></span> <span data-ttu-id="6c717-174">若要支持由 Web 承载的方案，必须开发一个自定义配置处理程序，以便允许在文件中配置自定义绑定元素。</span><span class="sxs-lookup"><span data-stu-id="6c717-174">To support the Web-hosted scenario, you must develop a custom configuration handler to allow a custom binding element to be configurable in a file.</span></span>

<span data-ttu-id="6c717-175">您可以在配置系统的顶部为绑定元素生成一个配置处理程序。</span><span class="sxs-lookup"><span data-stu-id="6c717-175">You can build a configuration handler for the binding element on top of the configuration system.</span></span> <span data-ttu-id="6c717-176">绑定元素的配置处理程序必须从 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> 类派生。</span><span class="sxs-lookup"><span data-stu-id="6c717-176">The configuration handler for the binding element must derive from the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> class.</span></span> <span data-ttu-id="6c717-177"><xref:System.ServiceModel.Configuration.BindingElementExtensionElement.BindingElementType?displayProperty=nameWithType>通知配置系统要为此节创建的绑定元素的类型。</span><span class="sxs-lookup"><span data-stu-id="6c717-177">The <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.BindingElementType?displayProperty=nameWithType> informs the configuration system of the type of binding element to create for this section.</span></span> <span data-ttu-id="6c717-178">`BindingElement` 的所有可设置方面应当作为属性在 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> 派生类中公开。</span><span class="sxs-lookup"><span data-stu-id="6c717-178">All aspects of the `BindingElement` that can be set should be exposed as properties in the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> derived class.</span></span> <span data-ttu-id="6c717-179"><xref:System.Configuration.ConfigurationPropertyAttribute>如果缺少属性，则有助于将配置元素特性映射到属性和设置默认值。</span><span class="sxs-lookup"><span data-stu-id="6c717-179">The <xref:System.Configuration.ConfigurationPropertyAttribute> assists in mapping the configuration element attributes to the properties and setting default values if attributes are missing.</span></span> <span data-ttu-id="6c717-180">在配置中的值加载并应用到属性之后，将调用 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A?displayProperty=nameWithType> 方法，该方法将属性转换成绑定元素的具体实例。</span><span class="sxs-lookup"><span data-stu-id="6c717-180">After the values from configuration are loaded and applied to the properties, the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A?displayProperty=nameWithType> method is called, which converts the properties into a concrete instance of a binding element.</span></span> <span data-ttu-id="6c717-181"><xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A?displayProperty=nameWithType>方法用于将派生类的属性转换为 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> 要在新创建的绑定元素上设置的值。</span><span class="sxs-lookup"><span data-stu-id="6c717-181">The <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A?displayProperty=nameWithType> method is used to convert the properties on the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> derived class into the values to be set on the newly created binding element.</span></span>

<span data-ttu-id="6c717-182">下面的示例代码演示 `GZipMessageEncodingElement` 的实现。</span><span class="sxs-lookup"><span data-stu-id="6c717-182">The following sample code shows the implementation of the `GZipMessageEncodingElement`.</span></span>

```csharp
public class GZipMessageEncodingElement : BindingElementExtensionElement
{
    public GZipMessageEncodingElement()
    {
    }

//Called by the WCF to discover the type of binding element this
//config section enables
    public override Type BindingElementType
    {
        get { return typeof(GZipMessageEncodingBindingElement); }
    }

    //The only property we need to configure for our binding element is
    //the type of inner encoder to use. Here, we support text and
    //binary.
    [ConfigurationProperty("innerMessageEncoding",
                         DefaultValue = "textMessageEncoding")]
    public string InnerMessageEncoding
    {
        get { return (string)base["innerMessageEncoding"]; }
        set { base["innerMessageEncoding"] = value; }
    }

    //Called by the WCF to apply the configuration settings (the
    //property above) to the binding element
    public override void ApplyConfiguration(BindingElement bindingElement)
    {
        GZipMessageEncodingBindingElement binding =
                (GZipMessageEncodingBindingElement)bindingElement;
        PropertyInformationCollection propertyInfo =
                    this.ElementInformation.Properties;
        if (propertyInfo["innerMessageEncoding"].ValueOrigin !=
                                     PropertyValueOrigin.Default)
        {
            switch (this.InnerMessageEncoding)
            {
                case "textMessageEncoding":
                    binding.InnerMessageEncodingBindingElement =
                      new TextMessageEncodingBindingElement();
                    break;
                case "binaryMessageEncoding":
                    binding.InnerMessageEncodingBindingElement =
                         new BinaryMessageEncodingBindingElement();
                    break;
            }
        }
    }

    //Called by the WCF to create the binding element
    protected override BindingElement CreateBindingElement()
    {
        GZipMessageEncodingBindingElement bindingElement =
                new GZipMessageEncodingBindingElement();
        this.ApplyConfiguration(bindingElement);
        return bindingElement;
    }
}
```

<span data-ttu-id="6c717-183">此配置处理程序映射到服务或客户端的 App.config 或 Web.config 中的以下表示形式。</span><span class="sxs-lookup"><span data-stu-id="6c717-183">This configuration handler maps to the following representation in the App.config or Web.config for the service or client.</span></span>

```xml
<gzipMessageEncoding innerMessageEncoding="textMessageEncoding" />
```

<span data-ttu-id="6c717-184">若要使用此配置处理程序，必须在元素中注册它， [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) 如下面的示例配置中所示。</span><span class="sxs-lookup"><span data-stu-id="6c717-184">To use this configuration handler, it must be registered within the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, as shown in the following sample configuration.</span></span>

```xml
<extensions>
    <bindingElementExtensions>
       <add
           name="gzipMessageEncoding"
           type=
           "Microsoft.ServiceModel.Samples.GZipMessageEncodingElement,
           GZipEncoder, Version=1.0.0.0, Culture=neutral,
           PublicKeyToken=null" />
      </bindingElementExtensions>
</extensions>
```

<span data-ttu-id="6c717-185">在运行服务器时，操作请求和响应将显示在控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="6c717-185">When you run the server, the operation requests and responses are displayed in the console window.</span></span> <span data-ttu-id="6c717-186">在该窗口中按 Enter 可以关闭服务器。</span><span class="sxs-lookup"><span data-stu-id="6c717-186">Press ENTER in the window to shut down the server.</span></span>

```console
Press Enter key to Exit.

        Server Echo(string input) called:
        Client message: Simple hello

        Server BigEcho(string[] input) called:
        64 client messages
```

<span data-ttu-id="6c717-187">在运行客户端时，操作请求和响应将显示在控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="6c717-187">When you run the client, the operation requests and responses are displayed in the console window.</span></span> <span data-ttu-id="6c717-188">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="6c717-188">Press ENTER in the client window to shut down the client.</span></span>

```console
Calling Echo(string):
Server responds: Simple hello Simple hello

Calling BigEcho(string[]):
Server responds: Hello 0

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6c717-189">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="6c717-189">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="6c717-190">使用以下命令安装 ASP.NET 4.0：</span><span class="sxs-lookup"><span data-stu-id="6c717-190">Install ASP.NET 4.0 using the following command:</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="6c717-191">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="6c717-191">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="6c717-192">若要生成解决方案，请按照[生成 Windows Communication Foundation 示例](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="6c717-192">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="6c717-193">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="6c717-193">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6c717-194">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="6c717-194">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6c717-195">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="6c717-195">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="6c717-196">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="6c717-196">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6c717-197">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="6c717-197">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`

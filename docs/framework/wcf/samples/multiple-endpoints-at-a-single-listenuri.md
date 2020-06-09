---
title: 在单个 ListenUri 中承载多个终结点
ms.date: 03/30/2017
ms.assetid: 911ffad4-4d47-4430-b7c2-79192ce6bcbd
ms.openlocfilehash: 91220c6631db2f283b6571fbc32af2211feeaa35
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602487"
---
# <a name="multiple-endpoints-at-a-single-listenuri"></a><span data-ttu-id="755a3-102">在单个 ListenUri 中承载多个终结点</span><span class="sxs-lookup"><span data-stu-id="755a3-102">Multiple Endpoints at a Single ListenUri</span></span>
<span data-ttu-id="755a3-103">此示例演示了一个在单个 `ListenUri` 中承载多个终结点的服务。</span><span class="sxs-lookup"><span data-stu-id="755a3-103">This sample demonstrates a service that hosts multiple endpoints at a single `ListenUri`.</span></span> <span data-ttu-id="755a3-104">此示例基于实现计算器服务的[入门](getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="755a3-104">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="755a3-105">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="755a3-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="755a3-106">如[多终结点](multiple-endpoints.md)示例中所示，服务可以托管多个终结点，每个终结点具有不同的地址，并且可能也有不同的绑定。</span><span class="sxs-lookup"><span data-stu-id="755a3-106">As demonstrated in the [Multiple Endpoints](multiple-endpoints.md) sample, a service can host multiple endpoints, each with different addresses and possibly also different bindings.</span></span> <span data-ttu-id="755a3-107">此示例演示了可以在同一个地址承载多个终结点，</span><span class="sxs-lookup"><span data-stu-id="755a3-107">This sample shows that it is possible to host multiple endpoints at the same address.</span></span> <span data-ttu-id="755a3-108">还演示了服务终结点所具有的两种地址（`EndpointAddress` 和 `ListenUri`）之间的区别。</span><span class="sxs-lookup"><span data-stu-id="755a3-108">This sample also demonstrates the differences between the two kinds of addresses that a service endpoint has: `EndpointAddress` and `ListenUri`.</span></span>  
  
 <span data-ttu-id="755a3-109">`EndpointAddress` 是服务的逻辑地址，</span><span class="sxs-lookup"><span data-stu-id="755a3-109">The `EndpointAddress` is the logical address of a service.</span></span> <span data-ttu-id="755a3-110">它是 SOAP 消息所发送到的地址。</span><span class="sxs-lookup"><span data-stu-id="755a3-110">It is the address that SOAP messages are addressed to.</span></span> <span data-ttu-id="755a3-111">`ListenUri` 是服务的物理地址，</span><span class="sxs-lookup"><span data-stu-id="755a3-111">The `ListenUri` is the physical address of the service.</span></span> <span data-ttu-id="755a3-112">它具有服务终结点在当前计算机上实际侦听消息时使用的端口和地址信息。</span><span class="sxs-lookup"><span data-stu-id="755a3-112">It has the port and address information where the service endpoint actually listens for messages on the current machine.</span></span> <span data-ttu-id="755a3-113">在多数情况下，无需对这些地址进行区分；如果没有明确指定 `ListenUri`，则地址默认为终结点 `EndpointAddress` 的 URI。</span><span class="sxs-lookup"><span data-stu-id="755a3-113">In most cases, there is no need for these addresses to differ; when a `ListenUri` is not explicitly specified, it defaults to the URI of the `EndpointAddress` of the endpoint.</span></span> <span data-ttu-id="755a3-114">在少数情况下（例如，在配置路由器时），有必要区分这些地址，因为路由器可能会接受发送到大量服务的消息。</span><span class="sxs-lookup"><span data-stu-id="755a3-114">In a few cases, it is useful to distinguish them, such as when configuring a router, which might accept messages addressed to a number of different services.</span></span>  
  
## <a name="service"></a><span data-ttu-id="755a3-115">服务</span><span class="sxs-lookup"><span data-stu-id="755a3-115">Service</span></span>  
 <span data-ttu-id="755a3-116">此示例中的服务有两个协定：`ICalculator` 和 `IEcho`。</span><span class="sxs-lookup"><span data-stu-id="755a3-116">The service in this sample has two contracts, `ICalculator` and `IEcho`.</span></span> <span data-ttu-id="755a3-117">除了通常的 `IMetadataExchange` 终结点，还有三个应用程序终结点，如下面的代码中所示。</span><span class="sxs-lookup"><span data-stu-id="755a3-117">In addition to the customary `IMetadataExchange` endpoint, there are three application endpoints, as shown in the following code.</span></span>  
  
```xml  
<endpoint address="urn:Stuff"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.ICalculator"
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
<endpoint address="urn:Stuff"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IEcho"
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
<endpoint address="urn:OtherEcho"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IEcho"
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
```  
  
 <span data-ttu-id="755a3-118">所有这三个终结点都在同一个 `ListenUri` 中承载，而且使用相同的 `binding`（即，位于同一个 `ListenUri` 的终结点必须具有相同的绑定），这是由于它们共享一个通道堆栈，而且该通道堆栈在计算机中的该物理地址上侦听消息。</span><span class="sxs-lookup"><span data-stu-id="755a3-118">All three endpoints are hosted at the same `ListenUri` and use the same `binding` - endpoints at the same `ListenUri` must have the same binding, because they are sharing a single channel stack that listens for messages at that physical address on the machine.</span></span> <span data-ttu-id="755a3-119">每个终结点的 `address` 都是一个 URN；尽管地址通常表示物理位置，但实际上地址可以是任何种类的 URI，因为地址可用于匹配和筛选目的，如该示例中所示。</span><span class="sxs-lookup"><span data-stu-id="755a3-119">The `address` of each endpoint is a URN; though typically addresses represent physical locations, in fact the address can be any kind of URI, because the address is used for matching and filtering purposes as is demonstrated in this sample.</span></span>  
  
 <span data-ttu-id="755a3-120">由于所有三个终结点共享相同的 `ListenUri` ，因此当消息到达该处时，Windows Communication Foundation （WCF）必须确定消息的目标终结点。</span><span class="sxs-lookup"><span data-stu-id="755a3-120">Because all three endpoints share the same `ListenUri`, when a message arrives there, Windows Communication Foundation (WCF) must decide which endpoint the message is destined for.</span></span> <span data-ttu-id="755a3-121">每个终结点都有一个消息筛选器，该消息筛选器由地址筛选器和协定筛选器两部分组成。</span><span class="sxs-lookup"><span data-stu-id="755a3-121">Each endpoint has a message filter that is comprised of two parts: the address filter and the contract filter.</span></span> <span data-ttu-id="755a3-122">地址筛选器将 SOAP 消息的 `To` 与服务终结点的地址相匹配。</span><span class="sxs-lookup"><span data-stu-id="755a3-122">The address filter matches the `To` of the SOAP message to the address of the service endpoint.</span></span> <span data-ttu-id="755a3-123">例如，只有发送到 `To "Urn:OtherEcho"` 的消息才是该服务的第三个候选终结点。</span><span class="sxs-lookup"><span data-stu-id="755a3-123">For example, only messages addressed `To "Urn:OtherEcho"` are candidates for the third endpoint of this service.</span></span> <span data-ttu-id="755a3-124">协定筛选器与那些与特定协定的操作相关联的 Action 相匹配。</span><span class="sxs-lookup"><span data-stu-id="755a3-124">The contract filter matches the Actions associated with the operations of a particular contract.</span></span> <span data-ttu-id="755a3-125">例如，具有 `IEcho` 操作的消息。</span><span class="sxs-lookup"><span data-stu-id="755a3-125">For example, messages with the action of `IEcho`.</span></span> <span data-ttu-id="755a3-126">`Echo` 与该服务的第二个终结点和第三个终结点的协定筛选器均匹配，因为这两个终结点均承载 `IEcho` 协定。</span><span class="sxs-lookup"><span data-stu-id="755a3-126">`Echo` matches the contract filters of both the second and third endpoints of this service, because both of those endpoints host the `IEcho` contract.</span></span>  
  
 <span data-ttu-id="755a3-127">因此，有了地址筛选器和协定筛选器的这一组合，可以将到达该服务 `ListenUri` 的每条消息路由到正确的终结点。</span><span class="sxs-lookup"><span data-stu-id="755a3-127">Thus the combination of address filter and contract filter makes it possible to route each message that arrives at this service's `ListenUri` to the correct endpoint.</span></span> <span data-ttu-id="755a3-128">第三个终结点与其他两个终结点不同，因为它接受从其他终结点发送到另一个地址的消息。</span><span class="sxs-lookup"><span data-stu-id="755a3-128">The third endpoint is differentiated from the other two because it accepts messages sent to a different address from the other endpoints.</span></span> <span data-ttu-id="755a3-129">前两个终结点的区别在于它们的协定（传入消息的 Action）不同。</span><span class="sxs-lookup"><span data-stu-id="755a3-129">The first and second endpoints are differentiated from each other based on their contracts (the Action of the incoming message).</span></span>  
  
## <a name="client"></a><span data-ttu-id="755a3-130">客户端</span><span class="sxs-lookup"><span data-stu-id="755a3-130">Client</span></span>  
 <span data-ttu-id="755a3-131">正如服务器上的终结点有两个不同的地址一样，客户端终结点也有两个地址。</span><span class="sxs-lookup"><span data-stu-id="755a3-131">Just as endpoints on the server have two different addresses, client endpoints also have two addresses.</span></span> <span data-ttu-id="755a3-132">在服务器和客户端上，逻辑地址均称为 `EndpointAddress`。</span><span class="sxs-lookup"><span data-stu-id="755a3-132">On both server and client, the logical address is called the `EndpointAddress`.</span></span> <span data-ttu-id="755a3-133">但是，物理地址在服务器上称为 `ListenUri`，在客户端上称为 `Via`。</span><span class="sxs-lookup"><span data-stu-id="755a3-133">But whereas the physical address is called the `ListenUri` on the server, on the client, the physical address is called the `Via`.</span></span>  
  
 <span data-ttu-id="755a3-134">而在服务器上，这两个地址在默认情况下是相同的。</span><span class="sxs-lookup"><span data-stu-id="755a3-134">As on the server, by default, these two addresses are the same.</span></span> <span data-ttu-id="755a3-135">若要在客户端上指定一个不同于终结点地址的 `Via`，可以使用 `ClientViaBehavior`：</span><span class="sxs-lookup"><span data-stu-id="755a3-135">To specify a `Via` on the client that is different from the endpoint's address, `ClientViaBehavior` is used:</span></span>  
  
```csharp  
Uri via = new Uri("http://localhost/ServiceModelSamples/service.svc");  
CalculatorClient calcClient = new CalculatorClient();  
calcClient.ChannelFactory.Endpoint.Behaviors.Add(  
        new ClientViaBehavior(via));  
```  
  
 <span data-ttu-id="755a3-136">和平常一样，地址来自由 Svcutil.exe 生成的客户端配置文件。</span><span class="sxs-lookup"><span data-stu-id="755a3-136">As usual, the address comes from the client configuration file, which was generated by Svcutil.exe.</span></span> <span data-ttu-id="755a3-137">`Via`（与服务的 `ListenUri` 相对应）不出现在服务的元数据中，因此该信息必须在带外传递到客户端（就像服务的元数据地址一样）。</span><span class="sxs-lookup"><span data-stu-id="755a3-137">The `Via` (which corresponds to the `ListenUri` of the service) does not appear in the service's metadata and so this information must be communicated to the client out-of-band (just like the service's metadata address).</span></span>  
  
 <span data-ttu-id="755a3-138">此示例中的客户端将消息发送到每台服务器的三个应用程序终结点，以演示它可以与所有这三个终结点通信并能够对这些终结点进行区分，即使这些终结点具有相同的 `Via` 也是如此。</span><span class="sxs-lookup"><span data-stu-id="755a3-138">The client in this sample sends messages to each of the server's three application endpoints, to demonstrate that it can communicate with (and differentiate) all three endpoints, even though they all have the same `Via`.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="755a3-139">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="755a3-139">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="755a3-140">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="755a3-140">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="755a3-141">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="755a3-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="755a3-142">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="755a3-142">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="755a3-143">若要跨计算机运行，则必须将 Client.cs 文件中的 localhost 替换为服务计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="755a3-143">For cross-machine, you must replace localhost in the Client.cs file with the name of the service machine.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="755a3-144">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="755a3-144">The samples may already be installed on your machine.</span></span> <span data-ttu-id="755a3-145">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="755a3-145">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="755a3-146">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="755a3-146">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="755a3-147">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="755a3-147">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpointsSingleUri`  

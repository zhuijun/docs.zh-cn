---
title: 双工服务
description: 了解如何在 WCF 中创建双工服务协定，这允许两个终结点通过客户端创建的通道互相发送消息。
ms.date: 05/09/2018
dev_langs:
- csharp
- vb
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
ms.openlocfilehash: a43bb63a0ccf1a34b79dce755c19f7ed4cb6c16c
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247346"
---
# <a name="duplex-services"></a><span data-ttu-id="8c4a2-103">双工服务</span><span class="sxs-lookup"><span data-stu-id="8c4a2-103">Duplex Services</span></span>

<span data-ttu-id="8c4a2-104">双工服务协定是一种消息交换模式，其中双方终结点都可独立向对方发送消息。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-104">A duplex service contract is a message exchange pattern in which both endpoints can send messages to the other independently.</span></span> <span data-ttu-id="8c4a2-105">因此，双工服务可以将消息发送回客户端终结点，从而提供类似事件的行为。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-105">A duplex service, therefore, can send messages back to the client endpoint, providing event-like behavior.</span></span> <span data-ttu-id="8c4a2-106">当客户端连接到服务并为服务提供可用来将消息发送回客户端的通道时，就会发生双工通信。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-106">Duplex communication occurs when a client connects to a service and provides the service with a channel on which the service can send messages back to the client.</span></span> <span data-ttu-id="8c4a2-107">请注意，双工服务的类似事件的行为仅在会话中起作用。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-107">Note that the event-like behavior of duplex services only works within a session.</span></span>

<span data-ttu-id="8c4a2-108">若要创建双工协定，需要创建一对接口。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-108">To create a duplex contract you create a pair of interfaces.</span></span> <span data-ttu-id="8c4a2-109">第一个接口是描述客户端可调用的操作的服务协定接口。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-109">The first is the service contract interface that describes the operations that a client can invoke.</span></span> <span data-ttu-id="8c4a2-110">该服务协定必须在属性中指定一个*回调协定* <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-110">That service contract must specify a *callback contract* in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="8c4a2-111">回调协定是定义服务可在客户端终结点上调用的操作的接口。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-111">The callback contract is the interface that defines the operations that the service can call on the client endpoint.</span></span> <span data-ttu-id="8c4a2-112">虽然系统提供的双工绑定利用了会话，但是双工协定不需要会话。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-112">A duplex contract does not require a session, although the system-provided duplex bindings make use of them.</span></span>

<span data-ttu-id="8c4a2-113">下面是双工协定的示例。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-113">The following is an example of a duplex contract.</span></span>

[!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
[!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]

<span data-ttu-id="8c4a2-114">`CalculatorService` 类实现 `ICalculatorDuplex` 主接口。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-114">The `CalculatorService` class implements the primary `ICalculatorDuplex` interface.</span></span> <span data-ttu-id="8c4a2-115">服务使用 <xref:System.ServiceModel.InstanceContextMode.PerSession> 实例模式来维护每个会话的结果。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-115">The service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the result for each session.</span></span> <span data-ttu-id="8c4a2-116">名为 `Callback` 的私有属性访问指向客户端的回调通道。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-116">A private property named `Callback` accesses the callback channel to the client.</span></span> <span data-ttu-id="8c4a2-117">服务使用该回调通过回调接口将消息返送给客户端，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-117">The service uses the callback for sending messages back to the client through the callback interface, as shown in the following sample code.</span></span>

[!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
[!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]

<span data-ttu-id="8c4a2-118">客户端必须提供一个实现双工协定回调接口的类，以便从服务接收消息。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-118">The client must provide a class that implements the callback interface of the duplex contract, for receiving messages from the service.</span></span> <span data-ttu-id="8c4a2-119">下面的示例代码演示了一个实现 `CallbackHandler` 接口的 `ICalculatorDuplexCallback` 类。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-119">The following sample code shows a `CallbackHandler` class that implements the `ICalculatorDuplexCallback` interface.</span></span>

[!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
[!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]

<span data-ttu-id="8c4a2-120">为双工协定生成的 WCF 客户端需要在 <xref:System.ServiceModel.InstanceContext> 构造时提供一个类。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-120">The WCF client that is generated for a duplex contract requires a <xref:System.ServiceModel.InstanceContext> class to be provided upon construction.</span></span> <span data-ttu-id="8c4a2-121">此 <xref:System.ServiceModel.InstanceContext> 类用作实现回调接口并处理从服务发送回的消息的对象所在的位置。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-121">This <xref:System.ServiceModel.InstanceContext> class is used as the site for an object that implements the callback interface and handles messages that are sent back from the service.</span></span> <span data-ttu-id="8c4a2-122"><xref:System.ServiceModel.InstanceContext> 类是用 `CallbackHandler` 类的实例构造的。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-122">An <xref:System.ServiceModel.InstanceContext> class is constructed with an instance of the `CallbackHandler` class.</span></span> <span data-ttu-id="8c4a2-123">此对象处理通过回调接口从服务发送到客户端的消息。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-123">This object handles messages sent from the service to the client on the callback interface.</span></span>

[!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
[!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]

<span data-ttu-id="8c4a2-124">服务的配置必须设置为提供同时支持会话通信和双工通信的绑定。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-124">The configuration for the service must be set up to provide a binding that supports both session communication and duplex communication.</span></span> <span data-ttu-id="8c4a2-125">`wsDualHttpBinding` 元素支持会话通信，并通过提供双 HTTP 连接（一个连接对应于一个方向）来允许进行双工通信。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-125">The `wsDualHttpBinding` element supports session communication and allows duplex communication by providing dual HTTP connections, one for each direction.</span></span>

<span data-ttu-id="8c4a2-126">在客户端，必须配置一个服务器可用来连接客户端的地址，如下面的示例配置所示。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-126">On the client, you must configure an address that the server can use to connect to the client, as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="8c4a2-127">未能使用安全会话通过身份验证的非双工客户端通常会引发 <xref:System.ServiceModel.Security.MessageSecurityException>。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-127">Non-duplex clients that fail to authenticate using a secure conversation typically throw a <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span> <span data-ttu-id="8c4a2-128">但是，如果使用安全会话的双工客户端未能通过身份验证，客户端则收到 <xref:System.TimeoutException>。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-128">However, if a duplex client that uses a secure conversation fails to authenticate, the client receives a <xref:System.TimeoutException> instead.</span></span>

<span data-ttu-id="8c4a2-129">如果使用 `WSHttpBinding` 元素创建客户端/服务，并且不包含客户端回调终结点，您将收到以下错误。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-129">If you create a client/service using the `WSHttpBinding` element and you do not include the client callback endpoint, you will receive the following error.</span></span>

```console
HTTP could not register URL
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.
```

<span data-ttu-id="8c4a2-130">下面的示例代码演示如何以编程方式指定客户端终结点地址。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-130">The following sample code shows how to specify the client endpoint address programmatically.</span></span>

```csharp
WSDualHttpBinding binding = new WSDualHttpBinding();
EndpointAddress endptadr = new EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server");
binding.ClientBaseAddress = new Uri("http://localhost:8000/DuplexTestUsingCode/Client/");
```

```vb
Dim binding As New WSDualHttpBinding()
Dim endptadr As New EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server")
binding.ClientBaseAddress = New Uri("http://localhost:8000/DuplexTestUsingCode/Client/")
```

<span data-ttu-id="8c4a2-131">下面的示例代码演示了如何在配置中指定客户端终结点地址。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-131">The following sample code shows how to specify the client endpoint address in configuration.</span></span>

```xml
<client>
    <endpoint name ="ServerEndpoint"
          address="http://localhost:12000/DuplexTestUsingConfig/Server"
          bindingConfiguration="WSDualHttpBinding_IDuplexTest"
            binding="wsDualHttpBinding"
           contract="IDuplexTest" />
</client>
<bindings>
    <wsDualHttpBinding>
        <binding name="WSDualHttpBinding_IDuplexTest"
          clientBaseAddress="http://localhost:8000/myClient/" >
            <security mode="None"/>
         </binding>
    </wsDualHttpBinding>
</bindings>
```

> [!WARNING]
> <span data-ttu-id="8c4a2-132">当服务或客户端关闭其通道时，双工模型不会自动检测。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-132">The duplex model doesn't automatically detect when a service or client closes its channel.</span></span> <span data-ttu-id="8c4a2-133">因此，如果客户端意外终止，则默认情况下将不会通知该服务; 或者，如果服务意外终止，则将不会通知客户端。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-133">So if a client unexpectedly terminates, by default the service will not be notified, or if a service unexpectedly terminates, the client will not be notified.</span></span> <span data-ttu-id="8c4a2-134">如果你使用断开连接的服务，则 <xref:System.ServiceModel.CommunicationException> 会引发异常。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-134">If you use a service that is disconnected, the <xref:System.ServiceModel.CommunicationException> exception is raised.</span></span> <span data-ttu-id="8c4a2-135">客户端和服务可以实现自己的协议以相互通知对方（如果它们这么选择）。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-135">Clients and services can implement their own protocol to notify each other if they so choose.</span></span> <span data-ttu-id="8c4a2-136">有关错误处理的详细信息，请参阅[WCF 错误处理](../wcf-error-handling.md)。</span><span class="sxs-lookup"><span data-stu-id="8c4a2-136">For more information on error handling, see [WCF Error Handling](../wcf-error-handling.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8c4a2-137">请参阅</span><span class="sxs-lookup"><span data-stu-id="8c4a2-137">See also</span></span>

- [<span data-ttu-id="8c4a2-138">双工</span><span class="sxs-lookup"><span data-stu-id="8c4a2-138">Duplex</span></span>](../samples/duplex.md)
- [<span data-ttu-id="8c4a2-139">指定客户端运行时行为</span><span class="sxs-lookup"><span data-stu-id="8c4a2-139">Specifying Client Run-Time Behavior</span></span>](../specifying-client-run-time-behavior.md)
- [<span data-ttu-id="8c4a2-140">如何：创建通道工厂并用它创建和管理通道</span><span class="sxs-lookup"><span data-stu-id="8c4a2-140">How to: Create a Channel Factory and Use it to Create and Manage Channels</span></span>](how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)

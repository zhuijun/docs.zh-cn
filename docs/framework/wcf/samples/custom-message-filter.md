---
title: 自定义消息筛选器
ms.date: 03/30/2017
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
ms.openlocfilehash: 0e4da0f2283fd537afe3cacdddfb36c327cfd3b4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600039"
---
# <a name="custom-message-filter"></a><span data-ttu-id="c2b15-102">自定义消息筛选器</span><span class="sxs-lookup"><span data-stu-id="c2b15-102">Custom Message Filter</span></span>
<span data-ttu-id="c2b15-103">此示例演示如何替换 Windows Communication Foundation （WCF）用于将消息调度到终结点的消息筛选器。</span><span class="sxs-lookup"><span data-stu-id="c2b15-103">This sample demonstrates how to replace the message filters that Windows Communication Foundation (WCF) uses to dispatch messages to endpoints.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c2b15-104">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="c2b15-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c2b15-105">当通道上的第一个消息到达服务器时，服务器必须确定哪个（如果有）与该 URI 关联的终结点应该接收消息。</span><span class="sxs-lookup"><span data-stu-id="c2b15-105">When the first message on a channel arrives at the server, the server must determine which (if any) of the endpoints associated with that URI should receive the message.</span></span> <span data-ttu-id="c2b15-106">此过程受附加到 <xref:System.ServiceModel.Dispatcher.MessageFilter> 的 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> 对象控制。</span><span class="sxs-lookup"><span data-stu-id="c2b15-106">This process is controlled by the <xref:System.ServiceModel.Dispatcher.MessageFilter> objects attached to the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span></span>  
  
 <span data-ttu-id="c2b15-107">服务的每个终结点都有一个 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>。</span><span class="sxs-lookup"><span data-stu-id="c2b15-107">Each endpoint of a service has a single <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span></span> <span data-ttu-id="c2b15-108"><xref:System.ServiceModel.Dispatcher.EndpointDispatcher> 同时具有 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> 和 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>。</span><span class="sxs-lookup"><span data-stu-id="c2b15-108">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> has both an <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> and a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>.</span></span> <span data-ttu-id="c2b15-109">这两个筛选器的联合是用于该终结点的消息筛选器。</span><span class="sxs-lookup"><span data-stu-id="c2b15-109">The union of these two filters is the message filter used for that endpoint.</span></span>  
  
 <span data-ttu-id="c2b15-110">默认情况下，终结点的 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> 与发送到某个地址的任何消息匹配，该地址与服务终结点的 <xref:System.ServiceModel.EndpointAddress> 的匹配。</span><span class="sxs-lookup"><span data-stu-id="c2b15-110">By default, the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> for an endpoint matches any message that is addressed to an address that matches the service endpoint's <xref:System.ServiceModel.EndpointAddress>.</span></span> <span data-ttu-id="c2b15-111">默认情况下， <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> 终结点的会检查传入消息的操作，并将与服务终结点协定操作的操作之一对应的任何消息匹配 `IsInitiating` = `true` 。</span><span class="sxs-lookup"><span data-stu-id="c2b15-111">By default, the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> for an endpoint inspects the action of the incoming message and matches any message with an action that corresponds to one of the actions of the service endpoint contract's operations (only `IsInitiating`=`true` actions are considered).</span></span> <span data-ttu-id="c2b15-112">因此，默认情况下，仅当消息的 To 标头为终结点的 <xref:System.ServiceModel.EndpointAddress> 并且消息的动作与终结点操作的动作之一匹配时，终结点的筛选器才与此消息匹配。</span><span class="sxs-lookup"><span data-stu-id="c2b15-112">As a result, by default, the filter for an endpoint only matches if both the message's To header is the <xref:System.ServiceModel.EndpointAddress> of the endpoint and the message's action matches one of the endpoint operation's actions.</span></span>  
  
 <span data-ttu-id="c2b15-113">使用行为可以更改这些筛选器。</span><span class="sxs-lookup"><span data-stu-id="c2b15-113">These filters can be changed using a behavior.</span></span> <span data-ttu-id="c2b15-114">在本示例中，服务创建一个 <xref:System.ServiceModel.Description.IEndpointBehavior>，该行为替换 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> 上的 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> 和 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>：</span><span class="sxs-lookup"><span data-stu-id="c2b15-114">In the sample, the service creates an <xref:System.ServiceModel.Description.IEndpointBehavior> that replaces the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> and <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> on the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:</span></span>  
  
```csharp
class FilteringEndpointBehavior : IEndpointBehavior
{
    //...
}
```  
  
 <span data-ttu-id="c2b15-115">定义两个地址筛选器：</span><span class="sxs-lookup"><span data-stu-id="c2b15-115">Two address filters are defined:</span></span>  
  
```csharp
// Matches any message whose To address contains the letter 'e'  
class MatchEAddressFilter : MessageFilter { }
// Matches any message whose To address does not contain the letter 'e'  
class MatchNoEAddressFilter : MessageFilter { }  
```  
  
 <span data-ttu-id="c2b15-116">使 `FilteringEndpointBehavior` 变得可配置并允许两个不同变体。</span><span class="sxs-lookup"><span data-stu-id="c2b15-116">The `FilteringEndpointBehavior` is made configurable and allows for two different variations.</span></span>  
  
```csharp
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement { }
```  
  
 <span data-ttu-id="c2b15-117">变体 1 仅匹配包含“e”的地址（但具有任何操作），而变体 2 仅匹配不含“e”的地址：</span><span class="sxs-lookup"><span data-stu-id="c2b15-117">Variation 1 matches only addresses that contain an 'e' (but that have any Action) whereas Variation 2 matches only addresses that lack an 'e':</span></span>  
  
```csharp
if (Variation == 1)  
    return new FilteringEndpointBehavior(  
        new MatchEAddressFilter(), new MatchAllMessageFilter());  
else  
    return new FilteringEndpointBehavior(  
        new MatchNoEAddressFilter(), new MatchAllMessageFilter());  
```  
  
 <span data-ttu-id="c2b15-118">在配置文件中，服务注册新行为：</span><span class="sxs-lookup"><span data-stu-id="c2b15-118">In the configuration file, the service registers the new behavior:</span></span>  
  
```xml  
<extensions>  
    <behaviorExtensions>  
        <add name="filteringEndpointBehavior" type="Microsoft.ServiceModel.Samples.FilteringEndpointBehaviorExtension, service" />  
    </behaviorExtensions>  
</extensions>
```  
  
 <span data-ttu-id="c2b15-119">然后，服务为每个变体创建 `endpointBehavior` 配置：</span><span class="sxs-lookup"><span data-stu-id="c2b15-119">Then the service creates `endpointBehavior` configurations for each variation:</span></span>  
  
```xml  
<endpointBehaviors>  
    <behavior name="endpoint1">  
        <filteringEndpointBehavior variation="1" />  
    </behavior>  
    <behavior name="endpoint2">  
        <filteringEndpointBehavior variation="2" />  
    </behavior>  
</endpointBehaviors>  
```  
  
 <span data-ttu-id="c2b15-120">最后，服务的终结点引用 `behaviorConfigurations` 之一：</span><span class="sxs-lookup"><span data-stu-id="c2b15-120">Finally, the service's endpoint references one of the `behaviorConfigurations`:</span></span>  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"
        behaviorConfiguration="endpoint2" />  
```  
  
 <span data-ttu-id="c2b15-121">客户端应用程序的实现非常简单；它通过将该值作为到 `via` 的第二个 (<xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29>) 参数传入并在每个通道上发送单个消息，但分别使用不同的终结点地址，创建两个到达服务的 URI 的通道。</span><span class="sxs-lookup"><span data-stu-id="c2b15-121">The implementation of the client application is straightforward; it creates two channels to the service's URI (by passing in that value as the second (`via`) parameter to <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> and sends a single message on each channel, but it uses different endpoint addresses for each.</span></span> <span data-ttu-id="c2b15-122">因此，来自客户端的出站消息具有不同的 To 标记，服务器做出相应响应，如客户端的输出所示：</span><span class="sxs-lookup"><span data-stu-id="c2b15-122">As a result, the outbound messages from the client have different To designations, and the server responds accordingly, as demonstrated by the client's output:</span></span>  
  
```console  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 <span data-ttu-id="c2b15-123">切换服务器配置文件中的变体导致交换筛选器，客户端看到相反的行为（到 `urn:e` 的消息成功，而到 `urn:a` 的消息失败）。</span><span class="sxs-lookup"><span data-stu-id="c2b15-123">Switching the variation in the server's configuration file causes the filter to be swapped and the client sees the opposite behavior (the message to `urn:e` succeeds, whereas the message to `urn:a` fails).</span></span>  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="c2b15-124">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="c2b15-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c2b15-125">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="c2b15-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c2b15-126">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="c2b15-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c2b15-127">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="c2b15-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c2b15-128">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="c2b15-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c2b15-129">若要生成解决方案，请按照[生成 Windows Communication Foundation 示例](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="c2b15-129">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="c2b15-130">若要在单计算机配置中运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="c2b15-130">To run the sample in a single-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
3. <span data-ttu-id="c2b15-131">若要在跨计算机配置中运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作，并在 Client.cs 中更改以下行。</span><span class="sxs-lookup"><span data-stu-id="c2b15-131">To run the sample in a cross-machine configuration, follow the instructions at [Running the Windows Communication Foundation Samples](running-the-samples.md) and change the following line in Client.cs.</span></span>  
  
    ```csharp
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     <span data-ttu-id="c2b15-132">用服务器的名称替换 localhost。</span><span class="sxs-lookup"><span data-stu-id="c2b15-132">Replace localhost with the name of server.</span></span>  
  
    ```csharp
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  

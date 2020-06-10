---
title: 自定义绑定命令
ms.date: 03/30/2017
ms.assetid: 6e13bf96-5de0-4476-b646-5f150774418d
ms.openlocfilehash: f7ba5c21b35d556be2c8d0817c37d98ad7d7dfcb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594733"
---
# <a name="custom-binding-imperative"></a><span data-ttu-id="82392-102">自定义绑定命令</span><span class="sxs-lookup"><span data-stu-id="82392-102">Custom Binding Imperative</span></span>
<span data-ttu-id="82392-103">此示例演示如何在不使用配置文件或 Windows Communication Foundation （WCF）生成的客户端的情况下，编写命令性代码来定义和使用自定义绑定。</span><span class="sxs-lookup"><span data-stu-id="82392-103">The sample demonstrates how to write imperative code to define and use custom bindings without using a configuration file or a Windows Communication Foundation (WCF) generated client.</span></span> <span data-ttu-id="82392-104">本示例将 HTTP 传输提供的功能与可靠会话通道结合在一起，用于创建基于 HTTP 的可靠绑定。</span><span class="sxs-lookup"><span data-stu-id="82392-104">This sample combines the features provided by the HTTP transport and the reliable session channel to create a reliable HTTP-based binding.</span></span> <span data-ttu-id="82392-105">此示例基于实现计算器服务的[入门](getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="82392-105">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82392-106">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="82392-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="82392-107">在客户端和服务上，创建包含两个绑定元素（可靠会话和 HTTP）的自定义绑定：</span><span class="sxs-lookup"><span data-stu-id="82392-107">On both the client and the service, a custom binding is created that contains two binding elements (Reliable Session and HTTP):</span></span>  

```csharp
ReliableSessionBindingElement reliableSession = new ReliableSessionBindingElement();  
reliableSession.Ordered = true;  
  
HttpTransportBindingElement httpTransport = new HttpTransportBindingElement();  
httpTransport.AuthenticationScheme = System.Net.AuthenticationSchemes.Anonymous;  
httpTransport.HostNameComparisonMode = HostNameComparisonMode.StrongWildcard;  
  
CustomBinding binding = new CustomBinding(reliableSession, httpTransport);  
```
  
 <span data-ttu-id="82392-108">在服务上，通过将终结点添加到 ServiceHost 来使用绑定：</span><span class="sxs-lookup"><span data-stu-id="82392-108">On the service, the binding is used by adding an endpoint to the ServiceHost:</span></span>  

```csharp
serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, "");  
```

 <span data-ttu-id="82392-109">在客户端上，<xref:System.ServiceModel.ChannelFactory> 使用绑定来创建服务通道：</span><span class="sxs-lookup"><span data-stu-id="82392-109">On the client, the binding is used by a <xref:System.ServiceModel.ChannelFactory> to create a channel to the service:</span></span>  

```csharp
EndpointAddress address = new EndpointAddress("http://localhost:8000/servicemodelsamples/service");  
ChannelFactory<ICalculator> channelFactory = new ChannelFactory<ICalculator>(binding, address);  
ICalculator channel = channelFactory.CreateChannel();  
```

 <span data-ttu-id="82392-110">然后将此通道用于与服务进行交互：</span><span class="sxs-lookup"><span data-stu-id="82392-110">This channel is then used to interact with the service:</span></span>  

```csharp
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = channel.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```

 <span data-ttu-id="82392-111">运行示例时，操作请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="82392-111">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="82392-112">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="82392-112">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="82392-113">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="82392-113">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="82392-114">请确保已[为 Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="82392-114">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="82392-115">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="82392-115">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="82392-116">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="82392-116">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="82392-117">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="82392-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="82392-118">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="82392-118">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="82392-119">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="82392-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="82392-120">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="82392-120">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Custom\Imperative`  
  
## <a name="see-also"></a><span data-ttu-id="82392-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="82392-121">See also</span></span>

- [<span data-ttu-id="82392-122">自定义绑定示例</span><span class="sxs-lookup"><span data-stu-id="82392-122">Custom Binding Samples</span></span>](custom-binding.md)

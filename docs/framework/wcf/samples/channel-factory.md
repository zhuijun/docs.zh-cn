---
title: 通道工厂
ms.date: 03/30/2017
ms.assetid: 09b53aa1-b13c-476c-a461-e82fcacd2a8b
ms.openlocfilehash: 2aa44c4ef274fa548d490b0d8a648457a7b1e03b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600654"
---
# <a name="channel-factory"></a><span data-ttu-id="d034f-102">通道工厂</span><span class="sxs-lookup"><span data-stu-id="d034f-102">Channel Factory</span></span>

<span data-ttu-id="d034f-103">此示例演示客户端应用程序如何使用 <xref:System.ServiceModel.ChannelFactory> 类而不是生成的客户端创建通道。</span><span class="sxs-lookup"><span data-stu-id="d034f-103">This sample demonstrates how a client application can create a channel with the <xref:System.ServiceModel.ChannelFactory> class instead of a generated client.</span></span> <span data-ttu-id="d034f-104">此示例基于实现计算器服务的[入门](getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="d034f-104">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span>

> [!NOTE]
> <span data-ttu-id="d034f-105">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="d034f-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="d034f-106">此示例使用 <xref:System.ServiceModel.ChannelFactory%601> 类来创建到服务终结点的通道。</span><span class="sxs-lookup"><span data-stu-id="d034f-106">This sample uses the <xref:System.ServiceModel.ChannelFactory%601> class to create a channel to a service endpoint.</span></span> <span data-ttu-id="d034f-107">通常，若要创建到服务终结点的通道，可以使用 "Svcutil.exe"[元数据实用工具（）](../servicemodel-metadata-utility-tool-svcutil-exe.md)生成客户端类型，并创建生成的类型的实例。</span><span class="sxs-lookup"><span data-stu-id="d034f-107">Typically, to create a channel to a service endpoint you generate a client type with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) and create an instance of the generated type.</span></span> <span data-ttu-id="d034f-108">还可以通过使用 <xref:System.ServiceModel.ChannelFactory%601> 类创建通道，如该示例所示。</span><span class="sxs-lookup"><span data-stu-id="d034f-108">You can also create a channel by using the <xref:System.ServiceModel.ChannelFactory%601> class, as demonstrated in this sample.</span></span> <span data-ttu-id="d034f-109">下面的示例代码创建的服务与[入门](getting-started-sample.md)中的服务相同。</span><span class="sxs-lookup"><span data-stu-id="d034f-109">The service created by the following sample code is identical to the service in the [Getting Started](getting-started-sample.md).</span></span>

```csharp
EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");
WSHttpBinding binding = new WSHttpBinding();
ChannelFactory<ICalculator> factory = new
                    ChannelFactory<ICalculator>(binding, address);
ICalculator channel = factory.CreateChannel();
```

> [!IMPORTANT]
> <span data-ttu-id="d034f-110">如果你在跨计算机方案中运行该示例，则必须将前面代码中的“localhost”替换为运行服务的计算机的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="d034f-110">If you are running this sample in a cross-machine scenario, you must replace "localhost" in the preceding code with the fully-qualified name of the machine that is running the service.</span></span> <span data-ttu-id="d034f-111">此示例不使用配置来设置终结点地址，因此这必须通过代码完成。</span><span class="sxs-lookup"><span data-stu-id="d034f-111">This sample does not use configuration to set the endpoint address, so this must be done in code.</span></span>

<span data-ttu-id="d034f-112">一旦创建了通道，便可以像调用生成的客户端那样调用服务操作。</span><span class="sxs-lookup"><span data-stu-id="d034f-112">Once the channel is created, service operations can be invoked just as with a generated client.</span></span>

```csharp
// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = channel.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
```

<span data-ttu-id="d034f-113">若要关闭通道，必须将其强制转换为 <xref:System.ServiceModel.IClientChannel> 接口。</span><span class="sxs-lookup"><span data-stu-id="d034f-113">To close the channel, it must first be cast to an <xref:System.ServiceModel.IClientChannel> interface.</span></span> <span data-ttu-id="d034f-114">这是因为生成的通道是在使用 `ICalculator` 接口的客户端应用程序中声明的，该应用程序具有 `Add` 和 `Subtract` 等方法，但没有 `Close` 方法。</span><span class="sxs-lookup"><span data-stu-id="d034f-114">This is because the channel as generated is declared in the client application using the `ICalculator` interface, which has methods like `Add` and `Subtract` but not `Close`.</span></span> <span data-ttu-id="d034f-115">`Close` 方法在 <xref:System.ServiceModel.ICommunicationObject> 接口上产生。</span><span class="sxs-lookup"><span data-stu-id="d034f-115">The `Close` method originates on the <xref:System.ServiceModel.ICommunicationObject> interface.</span></span>

```csharp
// Close the channel.
 ((IClientChannel)client).Close();
```

<span data-ttu-id="d034f-116">运行示例时，操作请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="d034f-116">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="d034f-117">在客户端窗口中按 Enter 可以关闭客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="d034f-117">Press ENTER in the client window to shut down the client application.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d034f-118">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="d034f-118">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="d034f-119">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="d034f-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="d034f-120">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="d034f-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span> <span data-ttu-id="d034f-121">请注意，该示例不会启用元数据发布。</span><span class="sxs-lookup"><span data-stu-id="d034f-121">Note that this sample does not enable metadata publishing.</span></span> <span data-ttu-id="d034f-122">必须先对该示例启用元数据发布才能重新生成客户端类型。</span><span class="sxs-lookup"><span data-stu-id="d034f-122">You must first enable metadata publishing for this sample to regenerate the client type.</span></span>

3. <span data-ttu-id="d034f-123">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="d034f-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

### <a name="to-run-the-sample-cross-machine"></a><span data-ttu-id="d034f-124">跨计算机运行示例</span><span class="sxs-lookup"><span data-stu-id="d034f-124">To run the sample cross machine</span></span>

1. <span data-ttu-id="d034f-125">将下面代码中的“localhost”替换为运行服务的计算机的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="d034f-125">Replace "localhost" in the following code with the fully-qualified name of the machine that is running the service.</span></span>

    ```csharp
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");
    ```

> [!IMPORTANT]
> <span data-ttu-id="d034f-126">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="d034f-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d034f-127">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="d034f-127">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="d034f-128">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="d034f-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d034f-129">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="d034f-129">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`

---
title: 双工
ms.date: 03/30/2017
helpviewer_keywords:
- Duplex Service Contract
ms.assetid: bc5de6b6-1a63-42a3-919a-67d21bae24e0
ms.openlocfilehash: 77eab6a4975fc67c20558a53f399c7e709215587
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575194"
---
# <a name="duplex"></a><span data-ttu-id="14b12-102">双工</span><span class="sxs-lookup"><span data-stu-id="14b12-102">Duplex</span></span>

<span data-ttu-id="14b12-103">“双工”示例演示如何定义和实现双工协定。</span><span class="sxs-lookup"><span data-stu-id="14b12-103">The Duplex sample demonstrates how to define and implement a duplex contract.</span></span> <span data-ttu-id="14b12-104">当客户端与服务建立会话并为服务提供可用来将消息发送回客户端的通道时，就会发生双工通信。</span><span class="sxs-lookup"><span data-stu-id="14b12-104">Duplex communication occurs when a client establishes a session with a service and gives the service a channel on which the service can send messages back to the client.</span></span> <span data-ttu-id="14b12-105">此示例基于[入门](getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="14b12-105">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="14b12-106">双工协定以一对接口形式定义：一个从客户端到服务的主接口和一个从服务到客户端的回调接口。</span><span class="sxs-lookup"><span data-stu-id="14b12-106">A duplex contract is defined as a pair of interfaces—a primary interface from the client to the service and a callback interface from the service to the client.</span></span> <span data-ttu-id="14b12-107">在本示例中，`ICalculatorDuplex` 接口允许客户端执行数学运算，通过会话计算结果。</span><span class="sxs-lookup"><span data-stu-id="14b12-107">In this sample, the `ICalculatorDuplex` interface allows the client to perform math operations, calculating the result over a session.</span></span> <span data-ttu-id="14b12-108">服务在 `ICalculatorDuplexCallback` 接口上返回结果。</span><span class="sxs-lookup"><span data-stu-id="14b12-108">The service returns results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="14b12-109">双工协定需要会话，因为必须建立上下文才能将客户端和服务之间发送的一组消息关联在一起。</span><span class="sxs-lookup"><span data-stu-id="14b12-109">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between the client and the service.</span></span>

> [!NOTE]
> <span data-ttu-id="14b12-110">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="14b12-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="14b12-111">在此示例中，客户端是一个控制台应用程序 (.exe)，服务是由 Internet 信息服务 (IIS) 承载的。</span><span class="sxs-lookup"><span data-stu-id="14b12-111">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="14b12-112">双工协定定义如下：</span><span class="sxs-lookup"><span data-stu-id="14b12-112">The duplex contract is defined as follows:</span></span>

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required,
                 CallbackContract=typeof(ICalculatorDuplexCallback))]
public interface ICalculatorDuplex
{
    [OperationContract(IsOneWay = true)]
    void Clear();
    [OperationContract(IsOneWay = true)]
    void AddTo(double n);
    [OperationContract(IsOneWay = true)]
    void SubtractFrom(double n);
    [OperationContract(IsOneWay = true)]
    void MultiplyBy(double n);
    [OperationContract(IsOneWay = true)]
    void DivideBy(double n);
}

public interface ICalculatorDuplexCallback
{
    [OperationContract(IsOneWay = true)]
    void Result(double result);
    [OperationContract(IsOneWay = true)]
    void Equation(string eqn);
}
```

<span data-ttu-id="14b12-113">`CalculatorService` 类实现 `ICalculatorDuplex` 主接口。</span><span class="sxs-lookup"><span data-stu-id="14b12-113">The `CalculatorService` class implements the primary `ICalculatorDuplex` interface.</span></span> <span data-ttu-id="14b12-114">服务使用 <xref:System.ServiceModel.InstanceContextMode.PerSession> 实例模式来维护每个会话的结果。</span><span class="sxs-lookup"><span data-stu-id="14b12-114">The service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the result for each session.</span></span> <span data-ttu-id="14b12-115">名为 `Callback` 的私有属性用于访问指向客户端的回调通道。</span><span class="sxs-lookup"><span data-stu-id="14b12-115">A private property named `Callback` is used to access the callback channel to the client.</span></span> <span data-ttu-id="14b12-116">服务使用该回调通过回调接口将消息发送回客户端。</span><span class="sxs-lookup"><span data-stu-id="14b12-116">The service uses the callback for sending messages back to the client through the callback interface.</span></span>

```csharp
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]
public class CalculatorService : ICalculatorDuplex
{
    double result = 0.0D;
    string equation;

    public CalculatorService()
    {
        equation = result.ToString();
    }

    public void Clear()
    {
        Callback.Equation($"{equation} = {result}");
        equation = result.ToString();
    }

    public void AddTo(double n)
    {
        result += n;
        equation += $" + {n}";
        Callback.Result(result);
    }

    //...

    ICalculatorDuplexCallback Callback
    {
        get
        {
            return OperationContext.Current.GetCallbackChannel<ICalculatorDuplexCallback>();
        }
    }
}
```

<span data-ttu-id="14b12-117">客户端必须提供一个实现双工协定回调接口的类，以便从服务接收消息。</span><span class="sxs-lookup"><span data-stu-id="14b12-117">The client must provide a class that implements the callback interface of the duplex contract, for receiving messages from the service.</span></span> <span data-ttu-id="14b12-118">该示例中，定义 `CallbackHandler` 类以实现 `ICalculatorDuplexCallback` 接口。</span><span class="sxs-lookup"><span data-stu-id="14b12-118">In the sample, a `CallbackHandler` class is defined to implement the `ICalculatorDuplexCallback` interface.</span></span>

```csharp
public class CallbackHandler : ICalculatorDuplexCallback
{
   public void Result(double result)
   {
      Console.WriteLine("Result({0})", result);
   }

   public void Equation(string equation)
   {
      Console.WriteLine("Equation({0}", equation);
   }
}
```

<span data-ttu-id="14b12-119">针对双工协定生成的代理需要在构造时提供一个 <xref:System.ServiceModel.InstanceContext>。</span><span class="sxs-lookup"><span data-stu-id="14b12-119">The proxy that is generated for a duplex contract requires a <xref:System.ServiceModel.InstanceContext> to be provided upon construction.</span></span> <span data-ttu-id="14b12-120">此 <xref:System.ServiceModel.InstanceContext> 用作实现回调接口并处理从服务发送回的消息的对象所在的位置。</span><span class="sxs-lookup"><span data-stu-id="14b12-120">This <xref:System.ServiceModel.InstanceContext> is used as the site for an object that implements the callback interface and handles messages that are sent back from the service.</span></span> <span data-ttu-id="14b12-121"><xref:System.ServiceModel.InstanceContext> 是用 `CallbackHandler` 类的实例构造的。</span><span class="sxs-lookup"><span data-stu-id="14b12-121">An <xref:System.ServiceModel.InstanceContext> is constructed with an instance of the `CallbackHandler` class.</span></span> <span data-ttu-id="14b12-122">此对象处理通过回调接口从服务发送到客户端的消息。</span><span class="sxs-lookup"><span data-stu-id="14b12-122">This object handles messages sent from the service to the client on the callback interface.</span></span>

```csharp
// Construct InstanceContext to handle messages on callback interface.
InstanceContext instanceContext = new InstanceContext(new CallbackHandler());

// Create a client.
CalculatorDuplexClient client = new CalculatorDuplexClient(instanceContext);

Console.WriteLine("Press <ENTER> to terminate client once the output is displayed.");
Console.WriteLine();

// Call the AddTo service operation.
double value = 100.00D;
client.AddTo(value);

// Call the SubtractFrom service operation.
value = 50.00D;
client.SubtractFrom(value);

// Call the MultiplyBy service operation.
value = 17.65D;
client.MultiplyBy(value);

// Call the DivideBy service operation.
value = 2.00D;
client.DivideBy(value);

// Complete equation.
client.Clear();

Console.ReadLine();

//Closing the client gracefully closes the connection and cleans up resources.
client.Close();
```

<span data-ttu-id="14b12-123">已将配置修改为提供同时支持会话通信和双工通信的绑定。</span><span class="sxs-lookup"><span data-stu-id="14b12-123">The configuration has been modified to provide a binding that supports both session communication and duplex communication.</span></span> <span data-ttu-id="14b12-124">`wsDualHttpBinding` 支持会话通信，并通过提供双 HTTP 连接（一个连接对应于一个方向）来允许进行双工通信。</span><span class="sxs-lookup"><span data-stu-id="14b12-124">The `wsDualHttpBinding` supports session communication and allows duplex communication by providing dual HTTP connections, one for each direction.</span></span> <span data-ttu-id="14b12-125">在服务上，配置中的唯一区别是所用的绑定。</span><span class="sxs-lookup"><span data-stu-id="14b12-125">On the service, the only difference in configuration is the binding that is used.</span></span> <span data-ttu-id="14b12-126">在客户端上，必须配置一个服务器可用来连接客户端的地址，如下面的示例配置所示。</span><span class="sxs-lookup"><span data-stu-id="14b12-126">On the client, you must configure an address that the server can use to connect to the client as shown in the following sample configuration.</span></span>

```xml
<client>
  <endpoint name=""
            address="http://localhost/servicemodelsamples/service.svc"
            binding="wsDualHttpBinding"
            bindingConfiguration="DuplexBinding"
            contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />
</client>

<bindings>
  <!-- Configure a binding that support duplex communication. -->
  <wsDualHttpBinding>
    <binding name="DuplexBinding"
             clientBaseAddress="http://localhost:8000/myClient/">
    </binding>
  </wsDualHttpBinding>
</bindings>
```

<span data-ttu-id="14b12-127">当运行示例时，从服务发送的回调接口上，可以看到返回到客户端的消息。</span><span class="sxs-lookup"><span data-stu-id="14b12-127">When you run the sample, you see the messages that are returned to the client on the callback interface that is sent from the service.</span></span> <span data-ttu-id="14b12-128">显示每个中间结果，最后在所有操作完成时显示整个公式。</span><span class="sxs-lookup"><span data-stu-id="14b12-128">Each intermediate result is displayed, followed by the entire equation upon the completion of all operations.</span></span> <span data-ttu-id="14b12-129">按 Enter 可关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="14b12-129">Press ENTER to shut down the client.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="14b12-130">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="14b12-130">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="14b12-131">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="14b12-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="14b12-132">若要生成 c #、c + + 或 Visual Basic .NET 版本的解决方案，请按照[生成 Windows Communication Foundation 示例](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="14b12-132">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="14b12-133">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="14b12-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="14b12-134">在跨计算机配置中运行客户端时，请确保 `address` 使用相应计算机的名称，将元素的属性[ \<endpoint> \<client> ](../../configure-apps/file-schema/wcf/endpoint-of-client.md)中的 "localhost" 替换为该元素的元素的属性 `clientBaseAddress` ，如下 [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) [\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md) 所示：</span><span class="sxs-lookup"><span data-stu-id="14b12-134">When running the client in a cross-machine configuration, be sure to replace "localhost" in both the `address` attribute of the [\<endpoint> of \<client>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element and the `clientBaseAddress` attribute of the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element of the [\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md) element with the name of the appropriate machine, as shown in the following:</span></span>

    ```xml
    <client>
        <endpoint name = ""
        address="http://service_machine_name/servicemodelsamples/service.svc"
        ... />
    </client>
    ...
    <wsDualHttpBinding>
        <binding name="DuplexBinding" clientBaseAddress="http://client_machine_name:8000/myClient/">
        </binding>
    </wsDualHttpBinding>
    ```

> [!IMPORTANT]
> <span data-ttu-id="14b12-135">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="14b12-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="14b12-136">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="14b12-136">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="14b12-137">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="14b12-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="14b12-138">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="14b12-138">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Duplex`

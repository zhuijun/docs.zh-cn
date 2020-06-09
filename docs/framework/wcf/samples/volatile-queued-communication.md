---
title: 可变排队通信
ms.date: 03/30/2017
ms.assetid: 0d012f64-51c7-41d0-8e18-c756f658ee3d
ms.openlocfilehash: a9f7e8a96fd293c7f87cc19846a42a42f28de288
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602334"
---
# <a name="volatile-queued-communication"></a><span data-ttu-id="0260b-102">可变排队通信</span><span class="sxs-lookup"><span data-stu-id="0260b-102">Volatile Queued Communication</span></span>

<span data-ttu-id="0260b-103">此示例演示如何通过消息队列 (MSMQ) 传输来执行可变排队通信。</span><span class="sxs-lookup"><span data-stu-id="0260b-103">This sample demonstrates how to perform volatile queued communication over the Message Queuing (MSMQ) transport.</span></span> <span data-ttu-id="0260b-104">此示例使用 <xref:System.ServiceModel.NetMsmqBinding>。</span><span class="sxs-lookup"><span data-stu-id="0260b-104">This sample uses <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="0260b-105">此例中的服务是自承载控制台应用程序，通过它可以观察服务接收排队消息。</span><span class="sxs-lookup"><span data-stu-id="0260b-105">The service in this case is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

> [!NOTE]
> <span data-ttu-id="0260b-106">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="0260b-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="0260b-107">在排队通信中，客户端使用队列与服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="0260b-107">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="0260b-108">更确切地说，客户端向队列发送消息。</span><span class="sxs-lookup"><span data-stu-id="0260b-108">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="0260b-109">服务从队列接收消息。</span><span class="sxs-lookup"><span data-stu-id="0260b-109">The service receives messages from the queue.</span></span> <span data-ttu-id="0260b-110">因此不必同时运行服务和客户端便可使用队列进行通信。</span><span class="sxs-lookup"><span data-stu-id="0260b-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

<span data-ttu-id="0260b-111">发送没有保证的消息时，MSMQ 仅尽量传递消息，这不同于“一次性”保证。具有“一次性”保证时，MSMQ 可确保消息被送达，如果无法送达消息，则会向您发出通知。</span><span class="sxs-lookup"><span data-stu-id="0260b-111">When you send a message with no assurances, MSMQ only makes a best effort to deliver the message, unlike with Exactly Once assurances where MSMQ ensures that the message gets delivered or, if it cannot be delivered, lets you know that the message cannot be delivered.</span></span>

<span data-ttu-id="0260b-112">在某些情况下，当及时送达比丢失消息更重要时，您可能想要通过某个队列发送没有保证的可变消息。</span><span class="sxs-lookup"><span data-stu-id="0260b-112">In certain scenarios, you may want to send a volatile message with no assurances over a queue, when timely delivery is more important than losing messages.</span></span> <span data-ttu-id="0260b-113">队列管理器崩溃时可变消息不存在。</span><span class="sxs-lookup"><span data-stu-id="0260b-113">Volatile messages do not survive queue manager crashes.</span></span> <span data-ttu-id="0260b-114">因此，如果队列管理器崩溃，用于存储可变消息的非事务性队列可以存在，但消息本身则无法存在，因为消息未存储在磁盘中。</span><span class="sxs-lookup"><span data-stu-id="0260b-114">Therefore if the queue manager crashes, the non-transactional queue used to store volatile messages survives but the messages themselves do not because the messages are not stored on the disk.</span></span>

> [!NOTE]
> <span data-ttu-id="0260b-115">不能使用 MSMQ 在某个事务范围内发送没有保证的可变消息。</span><span class="sxs-lookup"><span data-stu-id="0260b-115">You cannot send volatile messages with no assurances within the scope of a transaction using MSMQ.</span></span> <span data-ttu-id="0260b-116">还必须创建非事务性队列以发送可变消息。</span><span class="sxs-lookup"><span data-stu-id="0260b-116">You also must create a non-transactional queue to send volatile messages.</span></span>

<span data-ttu-id="0260b-117">此示例中的服务协定是定义最适合与队列一起使用的单向服务的 `IStockTicker`。</span><span class="sxs-lookup"><span data-stu-id="0260b-117">The service contract in this sample is `IStockTicker` that defines one-way services that are best suited for use with queuing.</span></span>

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
public interface IStockTicker
{
    [OperationContract(IsOneWay = true)]
    void StockTick(string symbol, float price);
}
```

<span data-ttu-id="0260b-118">服务操作显示股票代号符号和价格，如下面的示例代码所示：</span><span class="sxs-lookup"><span data-stu-id="0260b-118">The service operation displays the stock ticker symbol and price, as shown in the following sample code:</span></span>

```csharp
public class StockTickerService : IStockTicker
{
    public void StockTick(string symbol, float price)
    {
        Console.WriteLine("Stock Tick {0}:{1} ", symbol, price);
     }
     …
}
```

<span data-ttu-id="0260b-119">服务是自承载服务。</span><span class="sxs-lookup"><span data-stu-id="0260b-119">The service is self hosted.</span></span> <span data-ttu-id="0260b-120">使用 MSMQ 传输时，必须提前创建所使用的队列。</span><span class="sxs-lookup"><span data-stu-id="0260b-120">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="0260b-121">可以手动或通过代码完成此操作。</span><span class="sxs-lookup"><span data-stu-id="0260b-121">This can be done manually or through code.</span></span> <span data-ttu-id="0260b-122">在此示例中，该服务包含代码，以检查队列是否存在并在必要时创建队列。</span><span class="sxs-lookup"><span data-stu-id="0260b-122">In this sample, the service contains code to check for the existence of the queue and create it if required.</span></span> <span data-ttu-id="0260b-123">从配置文件中读取队列名称。</span><span class="sxs-lookup"><span data-stu-id="0260b-123">The queue name is read from the configuration file.</span></span> <span data-ttu-id="0260b-124">基址[元数据实用工具（svcutil.exe）](../servicemodel-metadata-utility-tool-svcutil-exe.md)使用该基址来生成服务的代理。</span><span class="sxs-lookup"><span data-stu-id="0260b-124">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy for the service.</span></span>

```csharp
// Host the service within this EXE console application.
public static void Main()
{
    // Get MSMQ queue name from app settings in configuration.
    string queueName = ConfigurationManager.AppSettings["queueName"];

    // Create the transacted MSMQ queue if necessary.
    if (!MessageQueue.Exists(queueName))
        MessageQueue.Create(queueName);

    // Create a ServiceHost for the StockTickerService type.
    using (ServiceHost serviceHost = new ServiceHost(typeof(StockTickerService)))
    {
        // Open the ServiceHost to create listeners and start listening for messages.
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        // Close the ServiceHost to shutdown the service.
        serviceHost.Close();
    }
}
```

<span data-ttu-id="0260b-125">MSMQ 队列名是在配置文件的 appSettings 节中指定的。</span><span class="sxs-lookup"><span data-stu-id="0260b-125">The MSMQ queue name is specified in the appSettings section of the configuration file.</span></span> <span data-ttu-id="0260b-126">服务终结点是在配置文件的 system.serviceModel 节中定义的，它指定了 `netMsmqBinding` 绑定。</span><span class="sxs-lookup"><span data-stu-id="0260b-126">The endpoint for the service is defined in the system.serviceModel section of the configuration file and specifies the `netMsmqBinding` binding.</span></span>

> [!NOTE]
> <span data-ttu-id="0260b-127">队列名称对本地计算机使用圆点 (.)，并在使用 <xref:System.Messaging> 创建队列时在其路径中使用反斜杠分隔符。</span><span class="sxs-lookup"><span data-stu-id="0260b-127">The queue name uses a dot (.) for the local machine and backslash separators in its path when creating a queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="0260b-128">Windows Communication Foundation （WCF）终结点地址指定一个 net.pipe：方案，使用本地计算机的 "localhost"，并在其路径中使用正斜杠。</span><span class="sxs-lookup"><span data-stu-id="0260b-128">The Windows Communication Foundation (WCF) endpoint address specifies a net.msmq: scheme, uses "localhost" for the local machine and forward slashes in its path.</span></span>

<span data-ttu-id="0260b-129">消息的保证和持久性或可变性也在配置中指定。</span><span class="sxs-lookup"><span data-stu-id="0260b-129">The assurances and durability or volatility of messages are also specified in the configuration.</span></span>

```xml
<appSettings>
  <!-- use appSetting to configure MSMQ queue name -->
  <add key="queueName" value=".\private$\ServiceModelSamplesVolatile" />
</appSettings>

<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.StockTickerService"
             behaviorConfiguration="CalculatorServiceBehavior">
    ...
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesVolatile"
                binding="netMsmqBinding"
                bindingConfiguration="volatileBinding"
                contract="Microsoft.ServiceModel.Samples.IStockTicker" />
    ...
    </service>
  </services>

  <bindings>
    <netMsmqBinding>
      <binding name="volatileBinding"
             durable="false"
           exactlyOnce="false"/>
    </netMsmqBinding>
  </bindings>
  ...
</system.serviceModel>
```

<span data-ttu-id="0260b-130">由于该示例通过使用非事务性队列来发送排队消息，因此无法将经过事务处理的消息发送到队列。</span><span class="sxs-lookup"><span data-stu-id="0260b-130">Because the sample sends queued messages by using a non-transactional queue, transacted messages cannot be sent to the queue.</span></span>

```csharp
// Create a client.
Random r = new Random(137);

StockTickerClient client = new StockTickerClient();

float price = 43.23F;
for (int i = 0; i < 10; i++)
{
    float increment = 0.01f * (r.Next(10));
    client.StockTick("zzz" + i, price + increment);
}

//Closing the client gracefully cleans up resources.
client.Close();
```

<span data-ttu-id="0260b-131">运行示例时，客户端和服务活动将显示在服务和客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="0260b-131">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="0260b-132">您可以看到服务从客户端接收消息。</span><span class="sxs-lookup"><span data-stu-id="0260b-132">You can see the service receive messages from the client.</span></span> <span data-ttu-id="0260b-133">在每个控制台窗口中按 Enter 可以关闭服务和客户端。</span><span class="sxs-lookup"><span data-stu-id="0260b-133">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="0260b-134">请注意：由于正在使用队列，因此不必同时启动和运行客户端和服务。</span><span class="sxs-lookup"><span data-stu-id="0260b-134">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="0260b-135">可以先运行客户端，再将其关闭，然后启动服务，这样服务仍然会收到客户端的消息。</span><span class="sxs-lookup"><span data-stu-id="0260b-135">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Stock Tick zzz0:43.25
Stock Tick zzz1:43.23
Stock Tick zzz2:43.28
Stock Tick zzz3:43.3
Stock Tick zzz4:43.23
Stock Tick zzz5:43.25
Stock Tick zzz6:43.25
Stock Tick zzz7:43.24
Stock Tick zzz8:43.32
Stock Tick zzz9:43.3
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0260b-136">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="0260b-136">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="0260b-137">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="0260b-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="0260b-138">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="0260b-138">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="0260b-139">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="0260b-139">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

<span data-ttu-id="0260b-140">默认情况下使用 <xref:System.ServiceModel.NetMsmqBinding> 启用传输安全。</span><span class="sxs-lookup"><span data-stu-id="0260b-140">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="0260b-141">MSMQ 传输安全性有两个相关的属性， <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` 默认情况下，身份验证模式设置为 `Windows` ，保护级别设置为 `Sign` 。</span><span class="sxs-lookup"><span data-stu-id="0260b-141">There are two pertinent properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="0260b-142">为了使 MSMQ 提供身份验证和签名功能，MSMQ 必须是域的一部分，并且必须安装 MSMQ 的 Active Directory 集成选项。</span><span class="sxs-lookup"><span data-stu-id="0260b-142">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="0260b-143">如果在不满足这些条件的计算机上运行此示例，将会收到错误。</span><span class="sxs-lookup"><span data-stu-id="0260b-143">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="0260b-144">在加入到工作组或在没有 Active Directory 集成的计算机上运行示例</span><span class="sxs-lookup"><span data-stu-id="0260b-144">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>

1. <span data-ttu-id="0260b-145">如果计算机不是域成员或尚未安装 Active Directory 集成，请将身份验证模式和保护级别设置为 `None` 以关闭传输安全性，如下面的示例配置代码所示：</span><span class="sxs-lookup"><span data-stu-id="0260b-145">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration code:</span></span>

    ```xml
    <system.serviceModel>
        <services>
          <service name="Microsoft.ServiceModel.Samples.StockTickerService"
                   behaviorConfiguration="StockTickerServiceBehavior">
            <host>
              <baseAddresses>
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
              </baseAddresses>
            </host>

            <!-- Define NetMsmqEndpoint -->
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesVolatile"
                      binding="netMsmqBinding"
                      bindingConfiguration="volatileBinding"
                      contract="Microsoft.ServiceModel.Samples.IStockTicker" />
            <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
            <endpoint address="mex"
                      binding="mexHttpBinding"
                      contract="IMetadataExchange" />

          </service>
        </services>

        <bindings>
          <netMsmqBinding>
            <binding name="volatileBinding"
                  durable="false"
                  exactlyOnce="false">
              <security mode="None" />
            </binding>
          </netMsmqBinding>
        </bindings>

        <behaviors>
          <serviceBehaviors>
            <behavior name="StockTickerServiceBehavior">
              <serviceMetadata httpGetEnabled="True"/>
            </behavior>
          </serviceBehaviors>
        </behaviors>

      </system.serviceModel>
    ```

2. <span data-ttu-id="0260b-146">确保在运行示例前更改服务器和客户端上的配置。</span><span class="sxs-lookup"><span data-stu-id="0260b-146">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0260b-147">将 `security mode` 设置为 `None` 等效于将 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>、<xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> 和 `Message` 安全设置为 `None`。</span><span class="sxs-lookup"><span data-stu-id="0260b-147">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0260b-148">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="0260b-148">The samples may already be installed on your computer.</span></span> <span data-ttu-id="0260b-149">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="0260b-149">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="0260b-150">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="0260b-150">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0260b-151">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="0260b-151">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Volatile`

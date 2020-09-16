---
title: Windows Communication Foundation 到消息队列
ms.date: 03/30/2017
ms.assetid: 78d0d0c9-648e-4d4a-8f0a-14d9cafeead9
ms.openlocfilehash: a6e322936740f7d88d30b9a205ac937a807bedc1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552922"
---
# <a name="windows-communication-foundation-to-message-queuing"></a><span data-ttu-id="5a887-102">Windows Communication Foundation 到消息队列</span><span class="sxs-lookup"><span data-stu-id="5a887-102">Windows Communication Foundation to Message Queuing</span></span>

<span data-ttu-id="5a887-103">此示例演示了 Windows Communication Foundation (WCF) 应用程序如何将消息发送到消息队列 (MSMQ) 应用程序。</span><span class="sxs-lookup"><span data-stu-id="5a887-103">This sample demonstrates how a Windows Communication Foundation (WCF) application can send a message to a Message Queuing (MSMQ) application.</span></span> <span data-ttu-id="5a887-104">此服务是自承载控制台应用程序，通过它可以观察服务接收排队消息。</span><span class="sxs-lookup"><span data-stu-id="5a887-104">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span> <span data-ttu-id="5a887-105">服务和客户端不需要同时运行。</span><span class="sxs-lookup"><span data-stu-id="5a887-105">The service and client do not have to be running at the same time.</span></span>

 <span data-ttu-id="5a887-106">服务从队列接收消息并处理订单。</span><span class="sxs-lookup"><span data-stu-id="5a887-106">The service receives messages from the queue and processes orders.</span></span> <span data-ttu-id="5a887-107">服务创建一个事务性队列，并为收到的消息设置消息处理程序，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="5a887-107">The service creates a transactional queue and sets up a message received message handler, as shown in the following sample code.</span></span>

```csharp
static void Main(string[] args)
{
    if (!MessageQueue.Exists(
              ConfigurationManager.AppSettings["queueName"]))
       MessageQueue.Create(
           ConfigurationManager.AppSettings["queueName"], true);
        //Connect to the queue
        MessageQueue Queue = new
    MessageQueue(ConfigurationManager.AppSettings["queueName"]);
    Queue.ReceiveCompleted +=
                 new ReceiveCompletedEventHandler(ProcessOrder);
    Queue.BeginReceive();
    Console.WriteLine("Order Service is running");
    Console.ReadLine();
}
```

 <span data-ttu-id="5a887-108">当消息到达队列中时，将调用消息处理程序 `ProcessOrder`。</span><span class="sxs-lookup"><span data-stu-id="5a887-108">When a message is received in the queue, the message handler `ProcessOrder` is invoked.</span></span>

```csharp
public static void ProcessOrder(Object source,
    ReceiveCompletedEventArgs asyncResult)
{
    try
    {
        // Connect to the queue.
        MessageQueue Queue = (MessageQueue)source;
        // End the asynchronous receive operation.
        System.Messaging.Message msg =
                     Queue.EndReceive(asyncResult.AsyncResult);
        msg.Formatter = new System.Messaging.XmlMessageFormatter(
                                new Type[] { typeof(PurchaseOrder) });
        PurchaseOrder po = (PurchaseOrder) msg.Body;
        Random statusIndexer = new Random();
        po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];
        Console.WriteLine("Processing {0} ", po);
        Queue.BeginReceive();
    }
    catch (System.Exception ex)
    {
        Console.WriteLine(ex.Message);
    }

}
```

 <span data-ttu-id="5a887-109">服务从 MSMQ 消息正文中提取 `ProcessOrder` 并处理订单。</span><span class="sxs-lookup"><span data-stu-id="5a887-109">The service extracts the `ProcessOrder` from the MSMQ message body, and processes the order.</span></span>

 <span data-ttu-id="5a887-110">MSMQ 队列名称在配置文件的 appSettings 节中指定，如以下示例配置所示。</span><span class="sxs-lookup"><span data-stu-id="5a887-110">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

```xml
<appSettings>
    <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>
```

> [!NOTE]
> <span data-ttu-id="5a887-111">队列名称为本地计算机使用圆点 (.)，并在其路径中使用反斜杠分隔符。</span><span class="sxs-lookup"><span data-stu-id="5a887-111">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span>

 <span data-ttu-id="5a887-112">客户端创建采购订单并在事务的范围内提交该采购订单，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="5a887-112">The client creates a purchase order and submits the purchase order within the scope of a transaction, as shown in the following sample code.</span></span>

```csharp
// Create the purchase order
PurchaseOrder po = new PurchaseOrder();
// Fill in the details
...

OrderProcessorClient client = new OrderProcessorClient("OrderResponseEndpoint");

MsmqMessage<PurchaseOrder> ordermsg = new MsmqMessage<PurchaseOrder>(po);
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
{
    client.SubmitPurchaseOrder(ordermsg);
    scope.Complete();
}
Console.WriteLine("Order has been submitted:{0}", po);

//Closing the client gracefully closes the connection and cleans up resources
client.Close();
```

 <span data-ttu-id="5a887-113">客户端按顺序使用自定义客户端将 MSMQ 消息发送给队列。</span><span class="sxs-lookup"><span data-stu-id="5a887-113">The client uses a custom client in-order to send the MSMQ message to the queue.</span></span> <span data-ttu-id="5a887-114">由于接收和处理消息的应用程序是 MSMQ 应用程序，而不是 WCF 应用程序，因此两个应用程序之间没有隐式服务协定。</span><span class="sxs-lookup"><span data-stu-id="5a887-114">Because the application that receives and processes the message is an MSMQ application and not a WCF application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="5a887-115">所以在此方案中，我们不能使用 Svcutil.exe 工具创建代理。</span><span class="sxs-lookup"><span data-stu-id="5a887-115">So, we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>

 <span data-ttu-id="5a887-116">对于使用绑定发送消息的所有 WCF 应用程序而言，自定义客户端本质上都是相同的 `MsmqIntegration` 。</span><span class="sxs-lookup"><span data-stu-id="5a887-116">The custom client is essentially the same for all WCF applications that use the `MsmqIntegration` binding to send messages.</span></span> <span data-ttu-id="5a887-117">与其他客户端不同，它不包含一系列服务操作。</span><span class="sxs-lookup"><span data-stu-id="5a887-117">Unlike other clients, it does not include a range of service operations.</span></span> <span data-ttu-id="5a887-118">它只是一个提交消息操作。</span><span class="sxs-lookup"><span data-stu-id="5a887-118">It is a submit message operation only.</span></span>

```csharp
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}

public partial class OrderProcessorClient : System.ServiceModel.ClientBase<IOrderProcessor>, IOrderProcessor
{
    public OrderProcessorClient(){}

    public OrderProcessorClient(string configurationName)
        : base(configurationName)
    { }

    public OrderProcessorClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)
        : base(binding, address)
    { }

    public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)
    {
        base.Channel.SubmitPurchaseOrder(msg);
    }
}
```

 <span data-ttu-id="5a887-119">运行示例时，客户端和服务活动将显示在服务和客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="5a887-119">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="5a887-120">您可以看到服务从客户端接收消息。</span><span class="sxs-lookup"><span data-stu-id="5a887-120">You can see the service receive messages from the client.</span></span> <span data-ttu-id="5a887-121">在每个控制台窗口中按 Enter 可以关闭服务和客户端。</span><span class="sxs-lookup"><span data-stu-id="5a887-121">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="5a887-122">请注意：由于正在使用队列，因此不必同时启动和运行客户端和服务。</span><span class="sxs-lookup"><span data-stu-id="5a887-122">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="5a887-123">例如，可以先运行客户端，再将其关闭，然后启动服务，这样服务仍然会收到客户端的消息。</span><span class="sxs-lookup"><span data-stu-id="5a887-123">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>

> [!NOTE]
> <span data-ttu-id="5a887-124">此示例需要安装消息队列。</span><span class="sxs-lookup"><span data-stu-id="5a887-124">This sample requires the installation of Message Queuing.</span></span> <span data-ttu-id="5a887-125">请参阅 [消息队列](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))中的安装说明。</span><span class="sxs-lookup"><span data-stu-id="5a887-125">See the installation instructions in [Message Queuing](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85)).</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="5a887-126">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="5a887-126">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="5a887-127">确保已对 [Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="5a887-127">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="5a887-128">如果先运行服务，则它将检查以确保队列存在。</span><span class="sxs-lookup"><span data-stu-id="5a887-128">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="5a887-129">如果队列不存在，则服务将创建一个队列。</span><span class="sxs-lookup"><span data-stu-id="5a887-129">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="5a887-130">可以先运行服务以创建队列或通过 MSMQ 队列管理器创建一个队列。</span><span class="sxs-lookup"><span data-stu-id="5a887-130">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="5a887-131">执行下面的步骤来在 Windows 2008 中创建队列。</span><span class="sxs-lookup"><span data-stu-id="5a887-131">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="5a887-132">在 Visual Studio 2012 中打开服务器管理器。</span><span class="sxs-lookup"><span data-stu-id="5a887-132">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="5a887-133">展开 " **功能** " 选项卡。</span><span class="sxs-lookup"><span data-stu-id="5a887-133">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="5a887-134">右键单击 "**专用消息队列**"，然后选择 "**新建**  >  **专用队列**"。</span><span class="sxs-lookup"><span data-stu-id="5a887-134">Right-click **Private Message Queues**, and then select **New** > **Private Queue**.</span></span>

    4. <span data-ttu-id="5a887-135">选中 " **事务性** " 框。</span><span class="sxs-lookup"><span data-stu-id="5a887-135">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="5a887-136">输入 `ServiceModelSamplesTransacted` 作为新队列的名称。</span><span class="sxs-lookup"><span data-stu-id="5a887-136">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="5a887-137">若要生成 c # 或 Visual Basic 版解决方案，请按照 [生成 Windows Communication Foundation 示例](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="5a887-137">To build the C# or Visual Basic edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="5a887-138">若要在单计算机配置中运行示例，请按照 [运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="5a887-138">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

## <a name="run-the-sample-across-computers"></a><span data-ttu-id="5a887-139">跨计算机运行示例</span><span class="sxs-lookup"><span data-stu-id="5a887-139">Run the sample across computers</span></span>

1. <span data-ttu-id="5a887-140">将 \service\bin\ 文件夹（在语言特定文件夹内）中的服务程序文件复制到服务计算机上。</span><span class="sxs-lookup"><span data-stu-id="5a887-140">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2. <span data-ttu-id="5a887-141">将 \client\bin\ 文件夹（在语言特定文件夹内）中的客户端程序文件复制到客户端计算机上。</span><span class="sxs-lookup"><span data-stu-id="5a887-141">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3. <span data-ttu-id="5a887-142">在 Client.exe.config 文件中，更改客户端终结点地址以指定服务计算机名称，而不是使用“.”。</span><span class="sxs-lookup"><span data-stu-id="5a887-142">In the Client.exe.config file, change the client endpoint address to specify the service computer name instead of ".".</span></span>

4. <span data-ttu-id="5a887-143">在服务计算机上，在命令提示符下启动 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="5a887-143">On the service computer, launch Service.exe from a command prompt.</span></span>

5. <span data-ttu-id="5a887-144">在客户端计算机上，在命令提示符下启动 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="5a887-144">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5a887-145">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="5a887-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5a887-146">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="5a887-146">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="5a887-147">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a887-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5a887-148">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="5a887-148">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\WcfToMsmq`

## <a name="see-also"></a><span data-ttu-id="5a887-149">请参阅</span><span class="sxs-lookup"><span data-stu-id="5a887-149">See also</span></span>

- [<span data-ttu-id="5a887-150">如何：与 WCF 终结点和消息队列应用程序交换消息</span><span class="sxs-lookup"><span data-stu-id="5a887-150">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- <span data-ttu-id="5a887-151">[消息队列](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="5a887-151">[Message Queuing](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span></span>

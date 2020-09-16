---
title: 到 Windows Communication Foundation 的消息队列
ms.date: 03/30/2017
ms.assetid: 6d718eb0-9f61-4653-8a75-d2dac8fb3520
ms.openlocfilehash: 5132e0380aebd595e79429fab9df8a7fb94574a0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558688"
---
# <a name="message-queuing-to-windows-communication-foundation"></a><span data-ttu-id="1bdb8-102">到 Windows Communication Foundation 的消息队列</span><span class="sxs-lookup"><span data-stu-id="1bdb8-102">Message Queuing to Windows Communication Foundation</span></span>

<span data-ttu-id="1bdb8-103">此示例演示了消息队列 (MSMQ) 应用程序如何将 MSMQ 消息发送到 Windows Communication Foundation (WCF) 服务。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-103">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="1bdb8-104">此服务是自承载控制台应用程序，通过它可以观察服务接收排队消息。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-104">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

 <span data-ttu-id="1bdb8-105">服务协定是 `IOrderProcessor`，它定义了适合与队列一起使用的单向服务。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-105">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="1bdb8-106">MSMQ 消息没有 Action 标头，因此无法将不同的 MSMQ 消息自动映射到操作协定。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-106">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="1bdb8-107">所以只能有一个操作协定。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-107">Therefore, there can be only one operation contract.</span></span> <span data-ttu-id="1bdb8-108">如果希望为服务定义多个操作协定，则应用程序必须提供有关 MSMQ 消息中的哪个标头（例如，标签或 correlationID）可用于确定要调度的操作协定的信息。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-108">If you want to define more than one operation contract for the service, the application must provide information as to which header in the MSMQ message (for example, the label or correlationID) can be used to decide which operation contract to dispatch.</span></span>

 <span data-ttu-id="1bdb8-109">MSMQ 消息不包含有关哪些标头可映射到操作协定的不同参数的信息。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-109">The MSMQ message does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="1bdb8-110">该参数属于 <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) 类型，包含基础 MSMQ 消息。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-110">The parameter is of type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), which contains the underlying MSMQ message.</span></span> <span data-ttu-id="1bdb8-111"><xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) 类中的“T”类型代表序列化到 MSMQ 消息正文中的数据。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-111">The type "T" in the <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="1bdb8-112">在此示例中，`PurchaseOrder` 类型序列化到 MSMQ 消息正文中。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-112">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>

 <span data-ttu-id="1bdb8-113">下面的示例代码演示订单处理服务的服务协定。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-113">The following sample code shows the service contract of the order processing service.</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
[ServiceKnownType(typeof(PurchaseOrder))]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}
```

 <span data-ttu-id="1bdb8-114">服务是自承载服务。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-114">The service is self hosted.</span></span> <span data-ttu-id="1bdb8-115">使用 MSMQ 时，必须提前创建所使用的队列。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-115">When using MSMQ, the queue used must be created in advance.</span></span> <span data-ttu-id="1bdb8-116">可以手动或通过代码完成此操作。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-116">This can be done manually or through code.</span></span> <span data-ttu-id="1bdb8-117">在此示例中，该服务检查队列是否存在并在必要时创建队列。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-117">In this sample, the service checks for the existence of the queue and creates it if required.</span></span> <span data-ttu-id="1bdb8-118">从配置文件中读取队列名称。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-118">The queue name is read from the configuration file.</span></span>

```csharp
public static void Main()
{
    // Get the MSMQ queue name from the application settings in
    // configuration.
    string queueName = ConfigurationManager.AppSettings["queueName"];
    // Create the MSMQ queue if necessary.
    if (!MessageQueue.Exists(queueName))
        MessageQueue.Create(queueName, true);
    …
}
```

 <span data-ttu-id="1bdb8-119">该服务为 <xref:System.ServiceModel.ServiceHost> 创建和打开 `OrderProcessorService`，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-119">The service creates and opens a <xref:System.ServiceModel.ServiceHost> for the `OrderProcessorService`, as shown in the following sample code.</span></span>

```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))
{
    serviceHost.Open();
    Console.WriteLine("The service is ready.");
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
    serviceHost.Close();
}
```

 <span data-ttu-id="1bdb8-120">MSMQ 队列名称在配置文件的 appSettings 节中指定，如以下示例配置所示。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-120">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="1bdb8-121">队列名称为本地计算机使用圆点 (.)，并在其路径中使用反斜杠分隔符。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-121">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="1bdb8-122">WCF 终结点地址指定 msmq.formatname 方案，并为本地计算机使用 localhost。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-122">The WCF endpoint address specifies a msmq.formatname scheme, and uses localhost for the local computer.</span></span> <span data-ttu-id="1bdb8-123">用于每个 MSMQ 格式名寻址指南的队列地址遵从 msmq.formatname 方案。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-123">The address of the queue for each MSMQ Format Name addressing guidelines follows the msmq.formatname scheme.</span></span>

```xml
<appSettings>
    <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>
```

 <span data-ttu-id="1bdb8-124">该客户端应用程序是一个 MSMQ 应用程序，它使用 <xref:System.Messaging.MessageQueue.Send%2A> 方法向队列发送持久的事务性消息，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-124">The client application is an MSMQ application that uses the <xref:System.Messaging.MessageQueue.Send%2A> method to send a durable and transactional message to the queue, as shown in the following sample code.</span></span>

```csharp
//Connect to the queue.
MessageQueue orderQueue = new MessageQueue(ConfigurationManager.AppSettings["orderQueueName"]);

// Create the purchase order.
PurchaseOrder po = new PurchaseOrder();
po.CustomerId = "somecustomer.com";
po.PONumber = Guid.NewGuid().ToString();

PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();
lineItem1.ProductId = "Blue Widget";
lineItem1.Quantity = 54;
lineItem1.UnitCost = 29.99F;

PurchaseOrderLineItem lineItem2 = new PurchaseOrderLineItem();
lineItem2.ProductId = "Red Widget";
lineItem2.Quantity = 890;
lineItem2.UnitCost = 45.89F;

po.orderLineItems = new PurchaseOrderLineItem[2];
po.orderLineItems[0] = lineItem1;
po.orderLineItems[1] = lineItem2;

// Submit the purchase order.
Message msg = new Message();
msg.Body = po;
//Create a transaction scope.
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
{

    orderQueue.Send(msg, MessageQueueTransactionType.Automatic);
    // Complete the transaction.
    scope.Complete();

}
Console.WriteLine("Placed the order:{0}", po);
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

 <span data-ttu-id="1bdb8-125">运行示例时，客户端和服务活动将显示在服务和客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-125">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="1bdb8-126">您可以看到服务从客户端接收消息。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-126">You can see the service receive messages from the client.</span></span> <span data-ttu-id="1bdb8-127">在每个控制台窗口中按 Enter 可以关闭服务和客户端。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-127">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="1bdb8-128">请注意：由于正在使用队列，因此不必同时启动和运行客户端和服务。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-128">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="1bdb8-129">例如，可以先运行客户端，再将其关闭，然后启动服务，这样服务仍然会收到客户端的消息。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-129">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="1bdb8-130">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="1bdb8-130">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="1bdb8-131">确保已对 [Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="1bdb8-132">如果先运行服务，则它将检查以确保队列存在。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-132">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="1bdb8-133">如果队列不存在，则服务将创建一个队列。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-133">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="1bdb8-134">可以先运行服务以创建队列或通过 MSMQ 队列管理器创建一个队列。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-134">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="1bdb8-135">执行下面的步骤来在 Windows 2008 中创建队列。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-135">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="1bdb8-136">在 Visual Studio 2012 中打开服务器管理器。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-136">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="1bdb8-137">展开 " **功能** " 选项卡。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-137">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="1bdb8-138">右键单击 "**专用消息队列**"，然后选择 "**新建\*\*\*\*专用队列**"。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-138">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="1bdb8-139">选中 " **事务性** " 框。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-139">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="1bdb8-140">输入 `ServiceModelSamplesTransacted` 作为新队列的名称。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-140">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="1bdb8-141">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="1bdb8-142">若要在单计算机配置中运行示例，请按照 [运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-142">To run the sample in a single- computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

## <a name="run-the-sample-across-computers"></a><span data-ttu-id="1bdb8-143">跨计算机运行示例</span><span class="sxs-lookup"><span data-stu-id="1bdb8-143">Run the sample across computers</span></span>

1. <span data-ttu-id="1bdb8-144">将 \service\bin\ 文件夹（在语言特定文件夹内）中的服务程序文件复制到服务计算机上。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-144">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2. <span data-ttu-id="1bdb8-145">将 \client\bin\ 文件夹（在语言特定文件夹内）中的客户端程序文件复制到客户端计算机上。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-145">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3. <span data-ttu-id="1bdb8-146">在 Client.exe.config 文件中，更改 orderQueueName 以指定服务计算机名称，而不是使用“.”。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-146">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>

4. <span data-ttu-id="1bdb8-147">在服务计算机上，在命令提示符下启动 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-147">On the service computer, launch Service.exe from a command prompt.</span></span>

5. <span data-ttu-id="1bdb8-148">在客户端计算机上，在命令提示符下启动 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-148">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1bdb8-149">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="1bdb8-149">The samples may already be installed on your computer.</span></span> <span data-ttu-id="1bdb8-150">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="1bdb8-150">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="1bdb8-151">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bdb8-151">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1bdb8-152">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="1bdb8-152">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MsmqToWcf`

## <a name="see-also"></a><span data-ttu-id="1bdb8-153">请参阅</span><span class="sxs-lookup"><span data-stu-id="1bdb8-153">See also</span></span>

- [<span data-ttu-id="1bdb8-154">WCF 中的队列</span><span class="sxs-lookup"><span data-stu-id="1bdb8-154">Queues in WCF</span></span>](../feature-details/queues-in-wcf.md)
- [<span data-ttu-id="1bdb8-155">如何：与 WCF 终结点和消息队列应用程序交换消息</span><span class="sxs-lookup"><span data-stu-id="1bdb8-155">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- <span data-ttu-id="1bdb8-156">[消息队列](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="1bdb8-156">[Message Queuing](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span></span>

---
title: 消息相关性
ms.date: 03/30/2017
ms.assetid: 3f62babd-c991-421f-bcd8-391655c82a1f
ms.openlocfilehash: 84b10b507f9fdaa7c53cf937bb132c8cc0aac33f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591627"
---
# <a name="message-correlation"></a><span data-ttu-id="99108-102">消息相关性</span><span class="sxs-lookup"><span data-stu-id="99108-102">Message Correlation</span></span>

<span data-ttu-id="99108-103">此示例演示消息队列（MSMQ）应用程序如何将 MSMQ 消息发送到 Windows Communication Foundation （WCF）服务，以及如何在请求/响应方案中将消息与发送方和接收方应用程序相关联。</span><span class="sxs-lookup"><span data-stu-id="99108-103">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a Windows Communication Foundation (WCF) service and how messages can be correlated between sender and receiver applications in a request/response scenario.</span></span> <span data-ttu-id="99108-104">此示例使用 msmqIntegrationBinding 绑定。</span><span class="sxs-lookup"><span data-stu-id="99108-104">This sample uses the msmqIntegrationBinding binding.</span></span> <span data-ttu-id="99108-105">这种情况下的服务是自承载控制台应用程序，通过它可以观察接收排队消息的服务。</span><span class="sxs-lookup"><span data-stu-id="99108-105">The service in this case is a self-hosted console application to allow you to observe the service that receives queued messages.</span></span> <span data-ttu-id="99108-106">k</span><span class="sxs-lookup"><span data-stu-id="99108-106">k</span></span>

 <span data-ttu-id="99108-107">该服务处理接收的来自发送方的消息，并向发送方回发一个响应消息。</span><span class="sxs-lookup"><span data-stu-id="99108-107">The service processes the message received from the sender and sends a response message back to the sender.</span></span> <span data-ttu-id="99108-108">发送方将它收到的响应与其最初发送的请求关联。</span><span class="sxs-lookup"><span data-stu-id="99108-108">The sender correlates the response it received to the request it sent originally.</span></span> <span data-ttu-id="99108-109">可以使用消息的 `MessageID` 和 `CorrelationID` 属性将请求消息与响应消息关联。</span><span class="sxs-lookup"><span data-stu-id="99108-109">The `MessageID` and `CorrelationID` properties of the message are used to correlate the request and response messages.</span></span>

 <span data-ttu-id="99108-110">`IOrderProcessor` 服务协定定义了适合与队列一起使用的单向服务操作。</span><span class="sxs-lookup"><span data-stu-id="99108-110">The `IOrderProcessor` service contract defines a one-way service operation that is suitable for use with queuing.</span></span> <span data-ttu-id="99108-111">MSMQ 消息没有 Action 标头，因此无法将不同的 MSMQ 消息自动映射到操作协定。</span><span class="sxs-lookup"><span data-stu-id="99108-111">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="99108-112">因此，在这种情况下只有一个操作协定。</span><span class="sxs-lookup"><span data-stu-id="99108-112">Therefore, there can be only one operation contract in this case.</span></span> <span data-ttu-id="99108-113">如果您希望在服务中定义更多的操作协定，则应用程序必须提供相关信息，如 MSMQ 消息中的哪个标头（例如标签或 correlationID）可用于确定要调度的操作协定。</span><span class="sxs-lookup"><span data-stu-id="99108-113">If you want to define more operation contracts in the service, the application must provide information as to which header in the MSMQ message (for example, the label, or correlationID) can be used to decide which operation contract to dispatch.</span></span>

 <span data-ttu-id="99108-114">MSMQ 消息也不包含诸如哪些标头映射到操作协定的不同参数等信息。</span><span class="sxs-lookup"><span data-stu-id="99108-114">The MSMQ message also does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="99108-115">因此，在该操作协定中只有一个参数。</span><span class="sxs-lookup"><span data-stu-id="99108-115">Therefore, there can be only one parameter in the operation contract.</span></span> <span data-ttu-id="99108-116">参数的类型为 <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> ，包含基础 MSMQ 消息。</span><span class="sxs-lookup"><span data-stu-id="99108-116">The parameter is of type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, which contains the underlying MSMQ message.</span></span> <span data-ttu-id="99108-117">`MsmqMessage<T>` 类中的“T”类型表示序列化到 MSMQ 消息正文中的数据。</span><span class="sxs-lookup"><span data-stu-id="99108-117">The type "T" in the `MsmqMessage<T>` class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="99108-118">在此示例中，`PurchaseOrder` 类型序列化到 MSMQ 消息正文中。</span><span class="sxs-lookup"><span data-stu-id="99108-118">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
[ServiceKnownType(typeof(PurchaseOrder))]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}
```

 <span data-ttu-id="99108-119">服务操作处理采购订单，并在服务控制台窗口中显示采购订单的内容及其状态。</span><span class="sxs-lookup"><span data-stu-id="99108-119">The service operation processes the purchase order and displays the contents of the purchase order and its status in the service console window.</span></span> <span data-ttu-id="99108-120"><xref:System.ServiceModel.OperationBehaviorAttribute> 使用队列配置要在事务中登记的操作并在返回操作时标记事务已完成。</span><span class="sxs-lookup"><span data-stu-id="99108-120">The <xref:System.ServiceModel.OperationBehaviorAttribute> configures the operation to enlist in a transaction with the queue and to mark the transaction complete when the operation returns.</span></span> <span data-ttu-id="99108-121">`PurchaseOrder` 包含必须由服务处理的订单详细信息。</span><span class="sxs-lookup"><span data-stu-id="99108-121">The `PurchaseOrder` contains the order details that must be processed by the service.</span></span>

```csharp
// Service class that implements the service contract.
public class OrderProcessorService : IOrderProcessor
{
   [OperationBehavior(TransactionScopeRequired = true,
          TransactionAutoComplete = true)]
   public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> ordermsg)
   {
       PurchaseOrder po = (PurchaseOrder)ordermsg.Body;
       Random statusIndexer = new Random();
       po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];
       Console.WriteLine("Processing {0} ", po);
       //Send a response to the client that the order has been received
         and is pending fullfillment.
       SendResponse(ordermsg);
    }

    private void SendResponse(MsmqMessage<PurchaseOrder> ordermsg)
    {
        OrderResponseClient client = new OrderResponseClient("OrderResponseEndpoint");

        //Set the correlation ID such that the client can correlate the response to the order.
        MsmqMessage<PurchaseOrder> orderResponsemsg = new MsmqMessage<PurchaseOrder>(ordermsg.Body);
        orderResponsemsg.CorrelationId = ordermsg.Id;
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
        {
            client.SendOrderResponse(orderResponsemsg);
            scope.Complete();
        }

        client.Close();
    }
}
```

 <span data-ttu-id="99108-122">服务使用自定义客户端 `OrderResponseClient` 将 MSMQ 消息发送到队列。</span><span class="sxs-lookup"><span data-stu-id="99108-122">The service uses a custom client `OrderResponseClient` to send the MSMQ message to the queue.</span></span> <span data-ttu-id="99108-123">由于接收和处理消息的应用程序是 MSMQ 应用程序，而不是 WCF 应用程序，因此两个应用程序之间没有隐式服务协定。</span><span class="sxs-lookup"><span data-stu-id="99108-123">Because the application that receives and processes the message is an MSMQ application and not a WCF application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="99108-124">所以在此方案中，我们不能使用 Svcutil.exe 工具创建代理。</span><span class="sxs-lookup"><span data-stu-id="99108-124">So we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>

 <span data-ttu-id="99108-125">对于使用绑定发送消息的所有 WCF 应用程序而言，自定义代理本质上是相同的 `msmqIntegrationBinding` 。</span><span class="sxs-lookup"><span data-stu-id="99108-125">The custom proxy is essentially the same for all WCF applications that use the `msmqIntegrationBinding` binding to send messages.</span></span> <span data-ttu-id="99108-126">与其他代理不同，它不包含一系列服务操作。</span><span class="sxs-lookup"><span data-stu-id="99108-126">Unlike other proxies, it does not include a range of service operations.</span></span> <span data-ttu-id="99108-127">它只是一个提交消息操作。</span><span class="sxs-lookup"><span data-stu-id="99108-127">It is a submit message operation only.</span></span>

```csharp
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]
public interface IOrderResponse
{

    [System.ServiceModel.OperationContractAttribute(IsOneWay = true, Action = "*")]
    void SendOrderResponse(MsmqMessage<PurchaseOrder> msg);
}

public partial class OrderResponseClient : System.ServiceModel.ClientBase<IOrderResponse>, IOrderResponse
{

    public OrderResponseClient()
    { }

    public OrderResponseClient(string configurationName)
        : base(configurationName)
    { }

    public OrderResponseClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)
        : base(binding, address)
    { }

    public void SendOrderResponse(MsmqMessage<PurchaseOrder> msg)
    {
        base.Channel.SendOrderResponse(msg);
    }
}
```

 <span data-ttu-id="99108-128">服务是自承载服务。</span><span class="sxs-lookup"><span data-stu-id="99108-128">The service is self hosted.</span></span> <span data-ttu-id="99108-129">使用 MSMQ 集成传输时，必须提前创建所使用的队列。</span><span class="sxs-lookup"><span data-stu-id="99108-129">When using the MSMQ integration transport, the queue used must be created in advance.</span></span> <span data-ttu-id="99108-130">可以手动或通过代码完成此操作。</span><span class="sxs-lookup"><span data-stu-id="99108-130">This can be done manually or through code.</span></span> <span data-ttu-id="99108-131">在此示例中，服务包含 <xref:System.Messaging> 代码，以检查队列是否存在并在必要时创建队列。</span><span class="sxs-lookup"><span data-stu-id="99108-131">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and create it if necessary.</span></span> <span data-ttu-id="99108-132">从配置文件中读取队列名称。</span><span class="sxs-lookup"><span data-stu-id="99108-132">The queue name is read from the configuration file.</span></span>

```csharp
public static void Main()
{
       // Get the MSMQ queue name from application settings in configuration.
      string queueName =
                ConfigurationManager.AppSettings["orderQueueName"];
      // Create the transacted MSMQ queue if necessary.
      if (!MessageQueue.Exists(queueName))
                MessageQueue.Create(queueName, true);
     // Create a ServiceHost for the OrderProcessorService type.
     using (ServiceHost serviceHost = new
                   ServiceHost(typeof(OrderProcessorService)))
     {
            serviceHost.Open();
            // The service can now be accessed.
            Console.WriteLine("The service is ready.");
            Console.WriteLine("Press <ENTER> to terminate service.");
            Console.ReadLine();
            // Close the ServiceHost to shutdown the service.
            serviceHost.Close();
      }
}
```

 <span data-ttu-id="99108-133">订单请求发送至的 MSMQ 队列是在配置文件的 appSettings 节中指定的。</span><span class="sxs-lookup"><span data-stu-id="99108-133">The MSMQ queue to which the order requests are sent is specified in the appSettings section of the configuration file.</span></span> <span data-ttu-id="99108-134">客户端终结点和服务终结点是在配置文件的 system.serviceModel 节中定义的。</span><span class="sxs-lookup"><span data-stu-id="99108-134">The client and service endpoints are defined in the system.serviceModel section of the configuration file.</span></span> <span data-ttu-id="99108-135">二者均指定了 `msmqIntegrationbinding` 绑定。</span><span class="sxs-lookup"><span data-stu-id="99108-135">Both specify the `msmqIntegrationbinding` binding.</span></span>

```xml
<appSettings>
  <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>

<system.serviceModel>
  <client>
    <endpoint    name="OrderResponseEndpoint"
              address="msmq.formatname:DIRECT=OS:.\private$\OrderResponse"
              binding="msmqIntegrationBinding"
              bindingConfiguration="OrderProcessorBinding"
              contract="Microsoft.ServiceModel.Samples.IOrderResponse">
    </endpoint>
  </client>

  <services>
    <service
      name="Microsoft.ServiceModel.Samples.OrderProcessorService">
      <endpoint address="msmq.formatname:DIRECT=OS:.\private$\Orders"
                            binding="msmqIntegrationBinding"
                bindingConfiguration="OrderProcessorBinding"
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor">
      </endpoint>
    </service>
  </services>

  <bindings>
    <msmqIntegrationBinding>
      <binding name="OrderProcessorBinding" >
        <security mode="None" />
      </binding>
    </msmqIntegrationBinding>
  </bindings>

</system.serviceModel>
```

 <span data-ttu-id="99108-136">客户端应用程序使用 <xref:System.Messaging> 向队列发送持久的事务性消息。</span><span class="sxs-lookup"><span data-stu-id="99108-136">The client application uses <xref:System.Messaging> to send a durable and transactional message to the queue.</span></span> <span data-ttu-id="99108-137">消息的正文包含采购订单。</span><span class="sxs-lookup"><span data-stu-id="99108-137">The message's body contains the purchase order.</span></span>

```csharp
static void PlaceOrder()
{
    //Connect to the queue
    MessageQueue orderQueue =
            new MessageQueue(
                    ConfigurationManager.AppSettings["orderQueueName"])
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

    Message msg = new Message();
    msg.UseDeadLetterQueue = true;
    msg.Body = po;

    //Create a transaction scope.
    using (TransactionScope scope = new
     TransactionScope(TransactionScopeOption.Required))
    {
        // Submit the purchase order.
        orderQueue.Send(msg, MessageQueueTransactionType.Automatic);
        // Complete the transaction.
        scope.Complete();
    }
    //Save the messageID for order response correlation.
    orderMessageID = msg.Id;
    Console.WriteLine("Placed the order, waiting for response...");
}
```

 <span data-ttu-id="99108-138">从中接收订单响应的 MSMQ 队列是在配置文件的 appSettings 节中定义的，如下面的示例配置所示。</span><span class="sxs-lookup"><span data-stu-id="99108-138">The MSMQ queue from which the order responses are received is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="99108-139">队列名称为本地计算机使用圆点 (.)，并在其路径中使用反斜杠分隔符。</span><span class="sxs-lookup"><span data-stu-id="99108-139">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="99108-140">WCF 终结点地址指定 msmq.formatname 方案，并为本地计算机使用 "localhost"。</span><span class="sxs-lookup"><span data-stu-id="99108-140">The WCF endpoint address specifies a msmq.formatname scheme, and uses "localhost" for the local computer.</span></span> <span data-ttu-id="99108-141">根据 MSMQ 准则，格式正确的格式名称应遵循 URI 中的 msmq.formatname。</span><span class="sxs-lookup"><span data-stu-id="99108-141">A properly formed format name follows msmq.formatname in the URI according to MSMQ guidelines.</span></span>

```xml
<appSettings>
    <add key=" orderResponseQueueName" value=".\private$\Orders" />
</appSettings>
```

 <span data-ttu-id="99108-142">客户端应用程序保存发送到服务的订单请求消息的 `messageID`，并等待服务响应。</span><span class="sxs-lookup"><span data-stu-id="99108-142">The client application saves the `messageID` of the order request message that it sends to the service and waits for a response from the service.</span></span> <span data-ttu-id="99108-143">一旦响应到达队列，客户端使用消息的 `correlationID` 属性将该响应与客户端发送的订单消息关联，此属性包含客户端最初向服务发送的订单消息的 `messageID`。</span><span class="sxs-lookup"><span data-stu-id="99108-143">Once a response arrives in the queue the client correlates it with the order message it sent using the `correlationID` property of the message, which contains the `messageID` of the order message that the client sent to the service originally.</span></span>

```csharp
static void DisplayOrderStatus()
{
    MessageQueue orderResponseQueue = new
     MessageQueue(ConfigurationManager.AppSettings
                  ["orderResponseQueueName"]);
    //Create a transaction scope.
    bool responseReceived = false;
    orderResponseQueue.MessageReadPropertyFilter.CorrelationId = true;
    while (!responseReceived)
    {
       Message responseMsg;
       using (TransactionScope scope2 = new
         TransactionScope(TransactionScopeOption.Required))
       {
          //Receive the Order Response message.
          responseMsg =
              orderResponseQueue.Receive
                   (MessageQueueTransactionType.Automatic);
          scope2.Complete();
     }
     responseMsg.Formatter = new
     System.Messaging.XmlMessageFormatter(new Type[] {
         typeof(PurchaseOrder) });
     PurchaseOrder responsepo = (PurchaseOrder)responseMsg.Body;
    //Check if the response is for the order placed.
    if (orderMessageID == responseMsg.CorrelationId)
    {
       responseReceived = true;
       Console.WriteLine("Status of current Order: OrderID-{0},Order
            Status-{1}", responsepo.PONumber, responsepo.Status);
    }
    else
    {
       Console.WriteLine("Status of previous Order: OrderID-{0},Order
            Status-{1}", responsepo.PONumber, responsepo.Status);
    }
  }
}
```

 <span data-ttu-id="99108-144">运行示例时，客户端和服务活动将显示在服务和客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="99108-144">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="99108-145">可以看到服务接收来自客户端的消息，并向客户端回发响应。</span><span class="sxs-lookup"><span data-stu-id="99108-145">You can see the service receive messages from the client and sends a response back to the client.</span></span> <span data-ttu-id="99108-146">客户端会显示来自服务的响应。</span><span class="sxs-lookup"><span data-stu-id="99108-146">The client displays the response received from the service.</span></span> <span data-ttu-id="99108-147">在每个控制台窗口中按 Enter 可以关闭服务和客户端。</span><span class="sxs-lookup"><span data-stu-id="99108-147">Press ENTER in each console window to shut down the service and client.</span></span>

> [!NOTE]
> <span data-ttu-id="99108-148">此示例要求安装消息队列 (MSMQ)。</span><span class="sxs-lookup"><span data-stu-id="99108-148">This sample requires the installation of Message Queuing (MSMQ).</span></span> <span data-ttu-id="99108-149">请参阅“请参见”部分中的 MSMQ 安装说明。</span><span class="sxs-lookup"><span data-stu-id="99108-149">See the MSMQ installation instructions in the See Also section.</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="99108-150">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="99108-150">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="99108-151">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="99108-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="99108-152">如果先运行服务，则它将检查以确保队列存在。</span><span class="sxs-lookup"><span data-stu-id="99108-152">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="99108-153">如果队列不存在，则服务将创建一个队列。</span><span class="sxs-lookup"><span data-stu-id="99108-153">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="99108-154">可以先运行服务以创建队列或通过 MSMQ 队列管理器创建一个队列。</span><span class="sxs-lookup"><span data-stu-id="99108-154">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="99108-155">执行下面的步骤来在 Windows 2008 中创建队列。</span><span class="sxs-lookup"><span data-stu-id="99108-155">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="99108-156">在 Visual Studio 2012 中打开服务器管理器。</span><span class="sxs-lookup"><span data-stu-id="99108-156">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="99108-157">展开 "**功能**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="99108-157">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="99108-158">右键单击 "**专用消息队列**"，然后选择 "**新建\*\*\*\*专用队列**"。</span><span class="sxs-lookup"><span data-stu-id="99108-158">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="99108-159">选中 "**事务性**" 框。</span><span class="sxs-lookup"><span data-stu-id="99108-159">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="99108-160">输入 `ServiceModelSamplesTransacted` 作为新队列的名称。</span><span class="sxs-lookup"><span data-stu-id="99108-160">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="99108-161">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="99108-161">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="99108-162">若要在单计算机配置中运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="99108-162">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

## <a name="run-the-sample-across-computers"></a><span data-ttu-id="99108-163">跨计算机运行示例</span><span class="sxs-lookup"><span data-stu-id="99108-163">Run the sample across computers</span></span>

1. <span data-ttu-id="99108-164">将 \service\bin\ 文件夹（在语言特定文件夹内）中的服务程序文件复制到服务计算机上。</span><span class="sxs-lookup"><span data-stu-id="99108-164">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2. <span data-ttu-id="99108-165">将 \client\bin\ 文件夹（在语言特定文件夹内）中的客户端程序文件复制到客户端计算机上。</span><span class="sxs-lookup"><span data-stu-id="99108-165">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3. <span data-ttu-id="99108-166">在 Client.exe.config 文件中，更改 orderQueueName 以指定服务计算机名称，而不是使用“.”。</span><span class="sxs-lookup"><span data-stu-id="99108-166">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>

4. <span data-ttu-id="99108-167">在 Service.exe.config 文件中，更改客户端终结点地址以指定客户端计算机名称，而不是使用“.”。</span><span class="sxs-lookup"><span data-stu-id="99108-167">In the Service.exe.config file, change the client endpoint address to specify the client computer name instead of ".".</span></span>

5. <span data-ttu-id="99108-168">在服务计算机上，在命令提示符下启动 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="99108-168">On the service computer, launch Service.exe from a command prompt.</span></span>

6. <span data-ttu-id="99108-169">在客户端计算机上，在命令提示符下启动 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="99108-169">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="99108-170">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="99108-170">The samples may already be installed on your computer.</span></span> <span data-ttu-id="99108-171">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="99108-171">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="99108-172">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="99108-172">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="99108-173">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="99108-173">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MessageCorrelation`

## <a name="see-also"></a><span data-ttu-id="99108-174">另请参阅</span><span class="sxs-lookup"><span data-stu-id="99108-174">See also</span></span>

- [<span data-ttu-id="99108-175">在 WCF 中排队</span><span class="sxs-lookup"><span data-stu-id="99108-175">Queuing in WCF</span></span>](../feature-details/queuing-in-wcf.md)
- <span data-ttu-id="99108-176">[消息队列](https://docs.microsoft.com/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="99108-176">[Message Queuing](https://docs.microsoft.com/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span></span>

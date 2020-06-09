---
title: 死信队列
ms.date: 03/30/2017
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
ms.openlocfilehash: 8ea2ea530db8745c3802f9f39793ffd77ddd0008
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575285"
---
# <a name="dead-letter-queues"></a><span data-ttu-id="8d89b-102">死信队列</span><span class="sxs-lookup"><span data-stu-id="8d89b-102">Dead Letter Queues</span></span>
<span data-ttu-id="8d89b-103">本示例演示如何处理传递失败的消息。</span><span class="sxs-lookup"><span data-stu-id="8d89b-103">This sample demonstrates how to handle and process messages that have failed delivery.</span></span> <span data-ttu-id="8d89b-104">它基于[事务性 MSMQ 绑定](transacted-msmq-binding.md)示例。</span><span class="sxs-lookup"><span data-stu-id="8d89b-104">It is based on the [Transacted MSMQ Binding](transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="8d89b-105">本示例使用 `netMsmqBinding` 绑定。</span><span class="sxs-lookup"><span data-stu-id="8d89b-105">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="8d89b-106">此服务是自承载控制台应用程序，通过它可以观察服务接收排队消息。</span><span class="sxs-lookup"><span data-stu-id="8d89b-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

> [!NOTE]
> <span data-ttu-id="8d89b-107">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="8d89b-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!NOTE]
> <span data-ttu-id="8d89b-108">此示例演示仅适用于 Windows Vista 的每个应用程序死信队列。</span><span class="sxs-lookup"><span data-stu-id="8d89b-108">This sample demonstrates each application dead letter queue that is only available on Windows Vista.</span></span> <span data-ttu-id="8d89b-109">可以修改此示例以在 Windows Server 2003 和 Windows XP 上使用 MSMQ 3.0 的默认系统范围队列。</span><span class="sxs-lookup"><span data-stu-id="8d89b-109">The sample can be modified to use the default system-wide queues for MSMQ 3.0 on Windows Server 2003 and Windows XP.</span></span>

 <span data-ttu-id="8d89b-110">在排队通信中，客户端使用队列与服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="8d89b-110">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="8d89b-111">更确切地说，客户端向队列发送消息。</span><span class="sxs-lookup"><span data-stu-id="8d89b-111">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="8d89b-112">服务从队列接收消息。</span><span class="sxs-lookup"><span data-stu-id="8d89b-112">The service receives messages from the queue.</span></span> <span data-ttu-id="8d89b-113">因此不必同时运行服务和客户端便可使用队列进行通信。</span><span class="sxs-lookup"><span data-stu-id="8d89b-113">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

 <span data-ttu-id="8d89b-114">由于排队通信可能需要一定的休眠时间，因此可能需要在消息上关联生存期时间值，以确保消息超过该时间后不会发送到应用程序。</span><span class="sxs-lookup"><span data-stu-id="8d89b-114">Because queued communication can involve a certain amount of dormancy, you may want to associate a time-to-live value on the message to ensure that the message does not get delivered to the application if it has gone past the time.</span></span> <span data-ttu-id="8d89b-115">在某些情况下，还必须通知应用程序消息传递是否失败。</span><span class="sxs-lookup"><span data-stu-id="8d89b-115">There are also cases, where an application must be informed whether a message failed delivery.</span></span> <span data-ttu-id="8d89b-116">在所有这些情况下（如消息的生存期过期或消息传递失败），会将消息放入死信队列中。</span><span class="sxs-lookup"><span data-stu-id="8d89b-116">In all of these cases, such as when the time-to-live on the message has expired or the message failed delivery, the message is put in a dead letter queue.</span></span> <span data-ttu-id="8d89b-117">然后，执行发送任务的应用程序可以读取死信队列中的消息并采取纠正措施（从不执行任何操作到纠正传递失败的原因），并重新发送消息。</span><span class="sxs-lookup"><span data-stu-id="8d89b-117">The sending application can then read the messages in the dead-letter queue and take corrective actions that range from no action to correcting the reasons for failed delivery and resending the message.</span></span>

 <span data-ttu-id="8d89b-118">`NetMsmqBinding` 绑定中的死信队列用下面的属性表示：</span><span class="sxs-lookup"><span data-stu-id="8d89b-118">The dead-letter queue in the `NetMsmqBinding` binding is expressed in the following properties:</span></span>

- <span data-ttu-id="8d89b-119"><xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> 属性表示客户端需要的死信队列。</span><span class="sxs-lookup"><span data-stu-id="8d89b-119"><xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> property to express the kind of dead-letter queue required by the client.</span></span> <span data-ttu-id="8d89b-120">此枚举具有下列值：</span><span class="sxs-lookup"><span data-stu-id="8d89b-120">This enumeration has the following values:</span></span>

- <span data-ttu-id="8d89b-121">`None`：客户端不需要死信队列。</span><span class="sxs-lookup"><span data-stu-id="8d89b-121">`None`: No dead-letter queue is required by the client.</span></span>

- <span data-ttu-id="8d89b-122">`System`：系统死信队列用于存储死消息。</span><span class="sxs-lookup"><span data-stu-id="8d89b-122">`System`: The system dead-letter queue is used to store dead messages.</span></span> <span data-ttu-id="8d89b-123">系统死信队列由计算机上运行的所有应用程序共享。</span><span class="sxs-lookup"><span data-stu-id="8d89b-123">The system dead-letter queue is shared by all applications running on the computer.</span></span>

- <span data-ttu-id="8d89b-124">`Custom`：使用 <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> 属性指定的自定义死信队列用于存储死消息。</span><span class="sxs-lookup"><span data-stu-id="8d89b-124">`Custom`: A custom dead-letter queue specified using the <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> property is used to store dead messages.</span></span> <span data-ttu-id="8d89b-125">此功能仅适用于 Windows Vista。</span><span class="sxs-lookup"><span data-stu-id="8d89b-125">This feature is only available on Windows Vista.</span></span> <span data-ttu-id="8d89b-126">当应用程序必须使用自己的死信队列而不与同一计算机上运行的其他应用程序共享该死信队列时使用此功能。</span><span class="sxs-lookup"><span data-stu-id="8d89b-126">This is used when the application must use its own dead letter queue instead of sharing it with other applications running on the same computer.</span></span>

- <span data-ttu-id="8d89b-127"><xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> 属性表示要用作死信队列的特定队列。</span><span class="sxs-lookup"><span data-stu-id="8d89b-127"><xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> property to express the specific queue to use as a dead-letter queue.</span></span> <span data-ttu-id="8d89b-128">这仅适用于 Windows Vista。</span><span class="sxs-lookup"><span data-stu-id="8d89b-128">This is available only in Windows Vista.</span></span>

 <span data-ttu-id="8d89b-129">在本示例中，客户端在事务范围内将一批消息发送到服务并为这些消息的“生存期”指定任意低的值（约 2 秒钟）。</span><span class="sxs-lookup"><span data-stu-id="8d89b-129">In this sample, the client sends a batch of messages to the service from within the scope of a transaction and specifies an arbitrarily low value for "time-to-live" for these messages (about 2 seconds).</span></span> <span data-ttu-id="8d89b-130">客户端还指定一个自定义死信队列用于排队已过期的消息。</span><span class="sxs-lookup"><span data-stu-id="8d89b-130">The client also specifies a custom dead-letter queue to use to enqueue the messages that have expired.</span></span>

 <span data-ttu-id="8d89b-131">客户端应用程序可以读取死信队列中的消息，并重试发送消息或纠正导致原始消息放入死信队列的错误，然后发送消息。</span><span class="sxs-lookup"><span data-stu-id="8d89b-131">The client application can read the messages in the dead-letter queue and either retry sending the message or correct the error that caused the original message to be placed in the dead-letter queue and send the message.</span></span> <span data-ttu-id="8d89b-132">在本示例中，客户端显示一条错误消息。</span><span class="sxs-lookup"><span data-stu-id="8d89b-132">In the sample, the client displays an error message.</span></span>

 <span data-ttu-id="8d89b-133">服务协定为 `IOrderProcessor`，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="8d89b-133">The service contract is `IOrderProcessor`, as shown in the following sample code.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="8d89b-134">该示例中的服务代码是[事务性 MSMQ 绑定](transacted-msmq-binding.md)的。</span><span class="sxs-lookup"><span data-stu-id="8d89b-134">The service code in the sample is that of the [Transacted MSMQ Binding](transacted-msmq-binding.md).</span></span>

 <span data-ttu-id="8d89b-135">与服务的通信发生在事务范围内。</span><span class="sxs-lookup"><span data-stu-id="8d89b-135">Communication with the service takes place within the scope of a transaction.</span></span> <span data-ttu-id="8d89b-136">服务读取队列中的消息，执行操作，然后显示操作的结果。</span><span class="sxs-lookup"><span data-stu-id="8d89b-136">The service reads messages from the queue, performs the operation and then displays the results of the operation.</span></span> <span data-ttu-id="8d89b-137">应用程序还为死信消息创建死信队列。</span><span class="sxs-lookup"><span data-stu-id="8d89b-137">The application also creates a dead-letter queue for dead-letter messages.</span></span>

```csharp
//The service contract is defined in generatedClient.cs, generated from the service by the svcutil tool.

//Client implementation code.
class Client
{
    static void Main()
    {
        // Get MSMQ queue name from app settings in configuration
        string deadLetterQueueName = ConfigurationManager.AppSettings["deadLetterQueueName"];

        // Create the transacted MSMQ queue for storing dead message if necessary.
        if (!MessageQueue.Exists(deadLetterQueueName))
            MessageQueue.Create(deadLetterQueueName, true);

        // Create a proxy with given client endpoint configuration
        OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");

        // Create the purchase order
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

        //Create a transaction scope.
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
        {
            // Make a queued call to submit the purchase order
            client.SubmitPurchaseOrder(po);
            // Complete the transaction.
            scope.Complete();
        }

        client.Close();

        Console.WriteLine();
        Console.WriteLine("Press <ENTER> to terminate client.");
        Console.ReadLine();
    }
}
```

 <span data-ttu-id="8d89b-138">客户端的配置为消息到达服务指定一个短的持续时间。</span><span class="sxs-lookup"><span data-stu-id="8d89b-138">The client's configuration specifies a short duration for the message to reach the service.</span></span> <span data-ttu-id="8d89b-139">如果消息无法在指定的持续时间内传输，则该消息将会过期并将移动到死信队列中。</span><span class="sxs-lookup"><span data-stu-id="8d89b-139">If the message cannot be transmitted within the duration specified, the message expires and is moved to the dead-letter queue.</span></span>

> [!NOTE]
> <span data-ttu-id="8d89b-140">客户端可以在指定的时间内将消息传送到服务队列。</span><span class="sxs-lookup"><span data-stu-id="8d89b-140">It is possible for the client to deliver the message to the service queue within the specified time.</span></span> <span data-ttu-id="8d89b-141">为确可以在操作中看到死信服务，应在启动服务之前运行客户端。</span><span class="sxs-lookup"><span data-stu-id="8d89b-141">To ensure you see the dead-letter service in action, you should run the client before starting the service.</span></span> <span data-ttu-id="8d89b-142">消息将超时并被传送到死信服务。</span><span class="sxs-lookup"><span data-stu-id="8d89b-142">The message times out and is delivered to the dead-letter service.</span></span>

 <span data-ttu-id="8d89b-143">应用程序必须定义使用哪个队列作为其死信队列。</span><span class="sxs-lookup"><span data-stu-id="8d89b-143">The application must define which queue to use as its dead-letter queue.</span></span> <span data-ttu-id="8d89b-144">如果未指定队列，则使用默认系统范围事务性死信队列对死消息排队。</span><span class="sxs-lookup"><span data-stu-id="8d89b-144">If no queue is specified, the default system-wide transactional dead-letter queue is used to queue dead messages.</span></span> <span data-ttu-id="8d89b-145">在本示例中，客户端应用程序指定其自己的应用程序死信队列。</span><span class="sxs-lookup"><span data-stu-id="8d89b-145">In this example, the client application specifies its own application dead-letter queue.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <appSettings>
    <!-- use appSetting to configure MSMQ Dead Letter queue name -->
    <add key="deadLetterQueueName" value=".\private$\ServiceModelSamplesOrdersAppDLQ"/>
  </appSettings>

  <system.serviceModel>
    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint name="OrderProcessorEndpoint"
                address="net.msmq://localhost/private/ServiceModelSamplesDeadLetter"
                binding="netMsmqBinding"
                bindingConfiguration="PerAppDLQBinding"
                contract="IOrderProcessor" />
    </client>

    <bindings>
      <netMsmqBinding>
        <binding name="PerAppDLQBinding"
                 deadLetterQueue="Custom"
                 customDeadLetterQueue="net.msmq://localhost/private/ServiceModelSamplesOrdersAppDLQ"
                 timeToLive="00:00:02"/>
      </netMsmqBinding>
    </bindings>
  </system.serviceModel>

</configuration>
```

 <span data-ttu-id="8d89b-146">死信消息服务从死信队列中读取消息。</span><span class="sxs-lookup"><span data-stu-id="8d89b-146">The dead-letter message service reads messages from the dead-letter queue.</span></span> <span data-ttu-id="8d89b-147">死信消息服务实现 `IOrderProcessor` 协定。</span><span class="sxs-lookup"><span data-stu-id="8d89b-147">The dead-letter message service implements the `IOrderProcessor` contract.</span></span> <span data-ttu-id="8d89b-148">但其实现不处理订单。</span><span class="sxs-lookup"><span data-stu-id="8d89b-148">Its implementation however is not to process orders.</span></span> <span data-ttu-id="8d89b-149">死信消息服务是客户端服务，没有处理订单的功能。</span><span class="sxs-lookup"><span data-stu-id="8d89b-149">The dead-letter message service is a client service and does not have the facility to process orders.</span></span>

> [!NOTE]
> <span data-ttu-id="8d89b-150">死信队列是客户端队列，对于客户端队列管理器来说是本地队列。</span><span class="sxs-lookup"><span data-stu-id="8d89b-150">The dead-letter queue is a client queue and is local to the client queue manager.</span></span>

 <span data-ttu-id="8d89b-151">死信消息服务实现可检查消息传递失败的原因并采取纠正措施。</span><span class="sxs-lookup"><span data-stu-id="8d89b-151">The dead-letter message service implementation checks for the reason a message failed delivery and takes corrective measures.</span></span> <span data-ttu-id="8d89b-152">消息失败的原因在两个枚举 <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> 和 <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A> 中捕获。</span><span class="sxs-lookup"><span data-stu-id="8d89b-152">The reason for a message failure is captured in two enumerations, <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> and <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>.</span></span> <span data-ttu-id="8d89b-153">您可以从 <xref:System.ServiceModel.Channels.MsmqMessageProperty> 中检索 <xref:System.ServiceModel.OperationContext>，如下面的示例代码所示：</span><span class="sxs-lookup"><span data-stu-id="8d89b-153">You can retrieve the <xref:System.ServiceModel.Channels.MsmqMessageProperty> from the <xref:System.ServiceModel.OperationContext> as shown in the following sample code:</span></span>

```csharp
public void SubmitPurchaseOrder(PurchaseOrder po)
{
    Console.WriteLine("Submitting purchase order did not succeed ", po);
    MsmqMessageProperty mqProp =
                  OperationContext.Current.IncomingMessageProperties[
                  MsmqMessageProperty.Name] as MsmqMessageProperty;
    Console.WriteLine("Message Delivery Status: {0} ",
                                                mqProp.DeliveryStatus);
    Console.WriteLine("Message Delivery Failure: {0}",
                                               mqProp.DeliveryFailure);
    Console.WriteLine();
    …
}
```

 <span data-ttu-id="8d89b-154">死信队列中的消息是被发送到处理消息的服务的消息。</span><span class="sxs-lookup"><span data-stu-id="8d89b-154">Messages in the dead-letter queue are messages that are addressed to the service that is processing the message.</span></span> <span data-ttu-id="8d89b-155">因此，当死信消息服务从队列中读取消息时，Windows Communication Foundation （WCF）通道层将查找终结点中不匹配项，并且不会调度消息。</span><span class="sxs-lookup"><span data-stu-id="8d89b-155">Therefore, when the dead-letter message service reads messages from the queue, the Windows Communication Foundation (WCF) channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="8d89b-156">在这种情况下，会将消息发送到订单处理服务，但由死信消息服务接收。</span><span class="sxs-lookup"><span data-stu-id="8d89b-156">In this case, the message is addressed to the order processing service but is received by the dead-letter message service.</span></span> <span data-ttu-id="8d89b-157">若要接收发送到不同终结点的消息，请在 `ServiceBehavior` 中指定一个可匹配任何地址的地址筛选器。</span><span class="sxs-lookup"><span data-stu-id="8d89b-157">To receive a message that is addressed to a different endpoint, an address filter to match any address is specified in the `ServiceBehavior`.</span></span> <span data-ttu-id="8d89b-158">这是成功处理从死信队列中读取的消息所必需的。</span><span class="sxs-lookup"><span data-stu-id="8d89b-158">This is required to successfully process messages that are read from the dead-letter queue.</span></span>

 <span data-ttu-id="8d89b-159">在此示例中，如果失败的原因是消息超时，则死信消息服务将重新发送消息。出于所有其他原因，它会显示传递失败，如下面的示例代码所示：</span><span class="sxs-lookup"><span data-stu-id="8d89b-159">In this sample, the dead-letter message service resends the message if the reason for failure is that the message timed out. For all other reasons, it displays the delivery failure, as shown in the following sample code:</span></span>

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
[ServiceBehavior(InstanceContextMode=InstanceContextMode.Single, ConcurrencyMode=ConcurrencyMode.Single, AddressFilterMode=AddressFilterMode.Any)]
public class PurchaseOrderDLQService : IOrderProcessor
{
    OrderProcessorClient orderProcessorService;
    public PurchaseOrderDLQService()
    {
        orderProcessorService = new OrderProcessorClient("OrderProcessorEndpoint");
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Console.WriteLine("Submitting purchase order did not succeed ", po);
        MsmqMessageProperty mqProp = OperationContext.Current.IncomingMessageProperties[MsmqMessageProperty.Name] as MsmqMessageProperty;

        Console.WriteLine("Message Delivery Status: {0} ", mqProp.DeliveryStatus);
        Console.WriteLine("Message Delivery Failure: {0}", mqProp.DeliveryFailure);
        Console.WriteLine();

        // resend the message if timed out
        if (mqProp.DeliveryFailure == DeliveryFailure.ReachQueueTimeout ||
            mqProp.DeliveryFailure == DeliveryFailure.ReceiveTimeout)
        {
            // re-send
            Console.WriteLine("Purchase order Time To Live expired");
            Console.WriteLine("Trying to resend the message");

            // reuse the same transaction used to read the message from dlq to enqueue the message to app. queue
            orderProcessorService.SubmitPurchaseOrder(po);
            Console.WriteLine("Purchase order resent");
        }
    }

    // Host the service within this EXE console application.
    public static void Main()
    {
        // Create a ServiceHost for the PurchaseOrderDLQService type.
        using (ServiceHost serviceHost = new ServiceHost(typeof(PurchaseOrderDLQService)))
        {
            // Open the ServiceHostBase to create listeners and start listening for messages.
            serviceHost.Open();

            // The service can now be accessed.
            Console.WriteLine("The dead letter service is ready.");
            Console.WriteLine("Press <ENTER> to terminate service.");
            Console.WriteLine();
            Console.ReadLine();
        }
    }
}
```

 <span data-ttu-id="8d89b-160">下面的示例演示死信消息的配置：</span><span class="sxs-lookup"><span data-stu-id="8d89b-160">The following sample shows the configuration for a dead-letter message:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.PurchaseOrderDLQService">
        <!-- Define NetMsmqEndpoint in this case, DLQ end point to read messages-->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesOrdersAppDLQ"
                  binding="netMsmqBinding"
                  bindingConfiguration="DefaultBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
      </service>
    </services>

    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint name="OrderProcessorEndpoint"
                 address="net.msmq://localhost/private/ServiceModelSamplesDeadLetter"
                 binding="netMsmqBinding"
                 bindingConfiguration="SystemDLQBinding"
                 contract="IOrderProcessor" />
    </client>

    <bindings>
      <netMsmqBinding>
        <binding name="DefaultBinding" />
        <binding name="SystemDLQBinding"
                 deadLetterQueue="System"/>
      </netMsmqBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```

 <span data-ttu-id="8d89b-161">在运行示例的过程中，需要运行 3 个可执行文件以查看死信队列如何适用于每个应用程序：客户端、服务和死信服务（从每个应用程序的死信队列中读取消息并将消息重新发送到服务）。</span><span class="sxs-lookup"><span data-stu-id="8d89b-161">In running the sample, there are 3 executables to run to see how the dead-letter queue works for each application; the client, service and a dead-letter service that reads from the dead-letter queue for each application and resends the message to the service.</span></span> <span data-ttu-id="8d89b-162">所有这些应用程序都是控制台应用程序，均在控制台窗口中输出结果。</span><span class="sxs-lookup"><span data-stu-id="8d89b-162">All are console applications with output in console windows.</span></span>

> [!NOTE]
> <span data-ttu-id="8d89b-163">由于队列正在使用中，因此不必同时启动和运行客户端和服务。</span><span class="sxs-lookup"><span data-stu-id="8d89b-163">Because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="8d89b-164">可以先运行客户端，再将其关闭，然后启动服务，这样服务仍然会收到客户端的消息。</span><span class="sxs-lookup"><span data-stu-id="8d89b-164">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span> <span data-ttu-id="8d89b-165">您应该启动服务，然后关闭服务，以便创建队列。</span><span class="sxs-lookup"><span data-stu-id="8d89b-165">You should start the service and shut it down so that the queue can be created.</span></span>

 <span data-ttu-id="8d89b-166">在运行客户端时，客户端将显示消息：</span><span class="sxs-lookup"><span data-stu-id="8d89b-166">When running the client, the client displays the message:</span></span>

```console
Press <ENTER> to terminate client.
```

 <span data-ttu-id="8d89b-167">客户端尝试发送消息，但由于短的超时，消息过期并在每个应用程序的死信队列中排队。</span><span class="sxs-lookup"><span data-stu-id="8d89b-167">The client attempted to send the message but with a short timeout, the message expired and is now queued in the dead-letter queue for each application.</span></span>

 <span data-ttu-id="8d89b-168">然后运行死信服务，读取消息并显示错误代码，然后将消息重新发回服务。</span><span class="sxs-lookup"><span data-stu-id="8d89b-168">You then run the dead-letter service, which reads the message and displays the error code and resends the message back to the service.</span></span>

```console
The dead letter service is ready.
Press <ENTER> to terminate service.

Submitting purchase order did not succeed
Message Delivery Status: InDoubt
Message Delivery Failure: ReachQueueTimeout

Purchase order Time To Live expired
Trying to resend the message
Purchase order resent
```

 <span data-ttu-id="8d89b-169">服务启动，然后读取重新发送的消息并处理该消息。</span><span class="sxs-lookup"><span data-stu-id="8d89b-169">The service starts and then reads the resent message and processes it.</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 97897eff-f926-4057-a32b-af8fb11b9bf9
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8d89b-170">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="8d89b-170">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="8d89b-171">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="8d89b-171">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="8d89b-172">如果先运行服务，则它将检查以确保队列存在。</span><span class="sxs-lookup"><span data-stu-id="8d89b-172">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="8d89b-173">如果队列不存在，则服务将创建一个队列。</span><span class="sxs-lookup"><span data-stu-id="8d89b-173">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="8d89b-174">可以先运行服务以创建队列或通过 MSMQ 队列管理器创建一个队列。</span><span class="sxs-lookup"><span data-stu-id="8d89b-174">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="8d89b-175">执行下面的步骤来在 Windows 2008 中创建队列。</span><span class="sxs-lookup"><span data-stu-id="8d89b-175">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="8d89b-176">在 Visual Studio 2012 中打开服务器管理器。</span><span class="sxs-lookup"><span data-stu-id="8d89b-176">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="8d89b-177">展开 "**功能**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="8d89b-177">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="8d89b-178">右键单击 "**专用消息队列**"，然后选择 "**新建\*\*\*\*专用队列**"。</span><span class="sxs-lookup"><span data-stu-id="8d89b-178">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="8d89b-179">选中 "**事务性**" 框。</span><span class="sxs-lookup"><span data-stu-id="8d89b-179">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="8d89b-180">输入 `ServiceModelSamplesTransacted` 作为新队列的名称。</span><span class="sxs-lookup"><span data-stu-id="8d89b-180">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="8d89b-181">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="8d89b-181">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="8d89b-182">若要在单一计算机配置或跨计算机配置中运行示例，请相应地更改队列名称，用计算机的全名替换 localhost，并按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="8d89b-182">To run the sample in a single- or cross-computer configuration change queue names appropriately, replacing localhost with full name of the computer and follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="8d89b-183">在加入到工作组的计算机上运行此示例</span><span class="sxs-lookup"><span data-stu-id="8d89b-183">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="8d89b-184">如果计算机不是域成员，请将身份验证模式和保护级别设置为 `None` 以禁用传输安全性，如下面的示例配置所示：</span><span class="sxs-lookup"><span data-stu-id="8d89b-184">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     <span data-ttu-id="8d89b-185">确保通过设置终结点的 `bindingConfiguration` 属性将终结点与绑定关联。</span><span class="sxs-lookup"><span data-stu-id="8d89b-185">Ensure the endpoint is associated with the binding by setting the endpoint's `bindingConfiguration` attribute.</span></span>

2. <span data-ttu-id="8d89b-186">确保在运行示例前更改 DeadLetterService、服务器和客户端上的配置。</span><span class="sxs-lookup"><span data-stu-id="8d89b-186">Ensure that you change the configuration on the DeadLetterService, server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8d89b-187">将 `security mode` 设置为 `None` 等效于将 `MsmqAuthenticationMode`、`MsmqProtectionLevel` 和 `Message` 安全设置为 `None`。</span><span class="sxs-lookup"><span data-stu-id="8d89b-187">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel` and `Message` security to `None`.</span></span>

## <a name="comments"></a><span data-ttu-id="8d89b-188">注释</span><span class="sxs-lookup"><span data-stu-id="8d89b-188">Comments</span></span>
 <span data-ttu-id="8d89b-189">默认情况下对 `netMsmqBinding` 绑定传输启用了安全性。</span><span class="sxs-lookup"><span data-stu-id="8d89b-189">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="8d89b-190">`MsmqAuthenticationMode` 和 `MsmqProtectionLevel` 这两个属性共同确定了传输安全性的类型。</span><span class="sxs-lookup"><span data-stu-id="8d89b-190">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="8d89b-191">默认情况下，身份验证模式设置为 `Windows`，保护级别设置为 `Sign`。</span><span class="sxs-lookup"><span data-stu-id="8d89b-191">By default the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="8d89b-192">MSMQ 必须是域的成员才可以提供身份验证和签名功能。</span><span class="sxs-lookup"><span data-stu-id="8d89b-192">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="8d89b-193">如果在不是域成员的计算机上运行此示例，则会接收以下错误：“用户的内部消息队列证书不存在”。</span><span class="sxs-lookup"><span data-stu-id="8d89b-193">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8d89b-194">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="8d89b-194">The samples may already be installed on your computer.</span></span> <span data-ttu-id="8d89b-195">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="8d89b-195">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="8d89b-196">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="8d89b-196">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8d89b-197">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="8d89b-197">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  

---
title: MSMQ 4.0 中的病毒消息处理
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: 54e69d60aabb3793ef4a8d800dd0e6238c28f231
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602435"
---
# <a name="poison-message-handling-in-msmq-40"></a><span data-ttu-id="06aec-102">MSMQ 4.0 中的病毒消息处理</span><span class="sxs-lookup"><span data-stu-id="06aec-102">Poison Message Handling in MSMQ 4.0</span></span>
<span data-ttu-id="06aec-103">本示例演示如何在服务中执行病毒消息处理。</span><span class="sxs-lookup"><span data-stu-id="06aec-103">This sample demonstrates how to perform poison message handling in a service.</span></span> <span data-ttu-id="06aec-104">此示例基于已进行[事务处理的 MSMQ 绑定](transacted-msmq-binding.md)示例。</span><span class="sxs-lookup"><span data-stu-id="06aec-104">This sample is based on the [Transacted MSMQ Binding](transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="06aec-105">其中使用到了 `netMsmqBinding`。</span><span class="sxs-lookup"><span data-stu-id="06aec-105">This sample uses the `netMsmqBinding`.</span></span> <span data-ttu-id="06aec-106">此服务是自承载控制台应用程序，通过它可以观察服务接收排队消息。</span><span class="sxs-lookup"><span data-stu-id="06aec-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

 <span data-ttu-id="06aec-107">在排队通信中，客户端使用队列与服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="06aec-107">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="06aec-108">更确切地说，客户端向队列发送消息。</span><span class="sxs-lookup"><span data-stu-id="06aec-108">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="06aec-109">服务从队列接收消息。</span><span class="sxs-lookup"><span data-stu-id="06aec-109">The service receives messages from the queue.</span></span> <span data-ttu-id="06aec-110">因此不必同时运行服务和客户端便可使用队列进行通信。</span><span class="sxs-lookup"><span data-stu-id="06aec-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

 <span data-ttu-id="06aec-111">病毒消息是一类当服务读取消息时不能对消息进行处理，并因此终止从中读取消息的事务时从队列重复读取的消息。</span><span class="sxs-lookup"><span data-stu-id="06aec-111">A poison message is a message that is repeatedly read from a queue when the service reading the message cannot process the message and therefore terminates the transaction under which the message is read.</span></span> <span data-ttu-id="06aec-112">在这种情况下，将再次重试消息。</span><span class="sxs-lookup"><span data-stu-id="06aec-112">In such cases, the message is retried again.</span></span> <span data-ttu-id="06aec-113">如果消息出现问题，这种情况在理论上将永远继续下去。</span><span class="sxs-lookup"><span data-stu-id="06aec-113">This can theoretically go on forever if there is a problem with the message.</span></span> <span data-ttu-id="06aec-114">仅当使用事务从队列中读取并调用服务操作时，才会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="06aec-114">This can only occur when you use transactions to read from the queue and invoke the service operation.</span></span>

 <span data-ttu-id="06aec-115">根据 MSMQ 版本，NetMsmqBinding 支持对病毒消息进行有限检测和完全检测。</span><span class="sxs-lookup"><span data-stu-id="06aec-115">Based on the version of MSMQ, the NetMsmqBinding supports limited detection to full detection of poison messages.</span></span> <span data-ttu-id="06aec-116">在已经将消息检测为病毒后，可以通过多种方式对消息进行处理。</span><span class="sxs-lookup"><span data-stu-id="06aec-116">After the message has been detected as poisoned, then it can be handled in several ways.</span></span> <span data-ttu-id="06aec-117">同样，根据 MSMQ 版本，NetMsmqBinding 支持对病毒消息进行有限处理和完全处理。</span><span class="sxs-lookup"><span data-stu-id="06aec-117">Again, based on the version of MSMQ, the NetMsmqBinding supports limited handling to full handling of poison messages.</span></span>

 <span data-ttu-id="06aec-118">此示例演示了 windows Server 2003 和 Windows XP 平台上提供的有限病毒功能，以及 Windows Vista 上提供的完整病毒功能。</span><span class="sxs-lookup"><span data-stu-id="06aec-118">This sample illustrates the limited poison facilities provided on Windows Server 2003 and Windows XP platform and the full poison facilities provided on Windows Vista.</span></span> <span data-ttu-id="06aec-119">在这两个示例中，目标是将病毒消息从队列移出到另一个队列。</span><span class="sxs-lookup"><span data-stu-id="06aec-119">In both samples, the objective is to move the poison message out of the queue to another queue.</span></span> <span data-ttu-id="06aec-120">然后，可以通过病毒消息服务来处理该队列。</span><span class="sxs-lookup"><span data-stu-id="06aec-120">That queue can then be serviced by a poison message service.</span></span>

## <a name="msmq-v40-poison-handling-sample"></a><span data-ttu-id="06aec-121">MSMQ v4.0 病毒处理示例</span><span class="sxs-lookup"><span data-stu-id="06aec-121">MSMQ v4.0 Poison Handling Sample</span></span>
 <span data-ttu-id="06aec-122">在 Windows Vista 中，MSMQ 提供了一个可用于存储病毒消息的病毒子队列设备。</span><span class="sxs-lookup"><span data-stu-id="06aec-122">In Windows Vista, MSMQ provides a poison subqueue facility that can be used to store poison messages.</span></span> <span data-ttu-id="06aec-123">此示例演示使用 Windows Vista 处理病毒消息的最佳实践。</span><span class="sxs-lookup"><span data-stu-id="06aec-123">This sample demonstrates the best practice of dealing with poison messages using Windows Vista.</span></span>

 <span data-ttu-id="06aec-124">Windows Vista 中的病毒消息检测功能非常复杂。</span><span class="sxs-lookup"><span data-stu-id="06aec-124">The poison message detection in Windows Vista is sophisticated.</span></span> <span data-ttu-id="06aec-125">有 3 属性可帮助检测。</span><span class="sxs-lookup"><span data-stu-id="06aec-125">There are 3 properties that help with detection.</span></span> <span data-ttu-id="06aec-126"><xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> 是重新从队列中读取给定消息并将其调度到应用程序中以进行处理的次数。</span><span class="sxs-lookup"><span data-stu-id="06aec-126">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is number of times a given message is re-read from the queue and dispatched to the application for processing.</span></span> <span data-ttu-id="06aec-127">当由于某一消息无法调度到应用程序或应用程序在服务操作中回滚事务，该消息返回到队列中时，即会从队列中重新读取该消息。</span><span class="sxs-lookup"><span data-stu-id="06aec-127">A message is re-read from the queue when it is put back into the queue because the message cannot be dispatched to the application or the application rolls back the transaction in the service operation.</span></span> <span data-ttu-id="06aec-128"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> 是将消息移动到重试队列的次数。</span><span class="sxs-lookup"><span data-stu-id="06aec-128"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> is the number of times the message is moved to the retry queue.</span></span> <span data-ttu-id="06aec-129">当达到 <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> 时，即会将该消息移动到重试队列。</span><span class="sxs-lookup"><span data-stu-id="06aec-129">When <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reached, the message is moved to the retry queue.</span></span> <span data-ttu-id="06aec-130">属性 <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> 是将消息从重试队列移回到主队列之前的时间延迟。</span><span class="sxs-lookup"><span data-stu-id="06aec-130">The property <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> is the time delay after which the message is moved from the retry queue back to the main queue.</span></span> <span data-ttu-id="06aec-131"><xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> 重置为 0。</span><span class="sxs-lookup"><span data-stu-id="06aec-131">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reset to 0.</span></span> <span data-ttu-id="06aec-132">再次尝试消息。</span><span class="sxs-lookup"><span data-stu-id="06aec-132">The message is tried again.</span></span> <span data-ttu-id="06aec-133">如果读取消息的所有尝试都失败，则会将该消息标记为已中毒。</span><span class="sxs-lookup"><span data-stu-id="06aec-133">If all attempts to read the message have failed, then the message is marked as poisoned.</span></span>

 <span data-ttu-id="06aec-134">一旦将消息标记为已中毒，则将按照 <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> 枚举中的设置来处理该消息。</span><span class="sxs-lookup"><span data-stu-id="06aec-134">Once the message is marked as poisoned, the message is dealt with according to the settings in the <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> enumeration.</span></span> <span data-ttu-id="06aec-135">迭代可能的值：</span><span class="sxs-lookup"><span data-stu-id="06aec-135">To reiterate the possible values:</span></span>

- <span data-ttu-id="06aec-136">Fault（默认值）：将侦听器和服务主机视为出现故障。</span><span class="sxs-lookup"><span data-stu-id="06aec-136">Fault (default): To fault the listener and also the service host.</span></span>

- <span data-ttu-id="06aec-137">放置：将放置消息。</span><span class="sxs-lookup"><span data-stu-id="06aec-137">Drop: To drop the message.</span></span>

- <span data-ttu-id="06aec-138">Move：将消息移动到病毒消息子队列。</span><span class="sxs-lookup"><span data-stu-id="06aec-138">Move: To move the message to the poison message subqueue.</span></span> <span data-ttu-id="06aec-139">此值仅适用于 Windows Vista。</span><span class="sxs-lookup"><span data-stu-id="06aec-139">This value is available only on Windows Vista.</span></span>

- <span data-ttu-id="06aec-140">Reject：要通过将消息发送回发送方死信队列来拒绝消息。</span><span class="sxs-lookup"><span data-stu-id="06aec-140">Reject: To reject the message, sending the message back to the sender's dead-letter queue.</span></span> <span data-ttu-id="06aec-141">此值仅适用于 Windows Vista。</span><span class="sxs-lookup"><span data-stu-id="06aec-141">This value is available only on Windows Vista.</span></span>

 <span data-ttu-id="06aec-142">示例演示了如何使用 `Move` 处理病毒消息。</span><span class="sxs-lookup"><span data-stu-id="06aec-142">The sample demonstrates using the `Move` disposition for the poison message.</span></span> <span data-ttu-id="06aec-143">`Move`使消息移动到病毒子队列。</span><span class="sxs-lookup"><span data-stu-id="06aec-143">`Move` causes the message to move to the poison subqueue.</span></span>

 <span data-ttu-id="06aec-144">服务协定是 `IOrderProcessor`，它定义了适合与队列一起使用的单向服务。</span><span class="sxs-lookup"><span data-stu-id="06aec-144">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="06aec-145">该服务操作显示一条指示它正在处理订单的消息。</span><span class="sxs-lookup"><span data-stu-id="06aec-145">The service operation displays a message stating it is processing the order.</span></span> <span data-ttu-id="06aec-146">为了演示病毒消息功能， `SubmitPurchaseOrder` 服务操作将引发异常，以便在服务的随机调用中回滚事务。</span><span class="sxs-lookup"><span data-stu-id="06aec-146">To demonstrate the poison message functionality, the `SubmitPurchaseOrder` service operation throws an exception to roll back the transaction on a random invocation of the service.</span></span> <span data-ttu-id="06aec-147">这将导致消息被放回队列中。</span><span class="sxs-lookup"><span data-stu-id="06aec-147">This causes the message to be put back in the queue.</span></span> <span data-ttu-id="06aec-148">并最终将消息标记为病毒。</span><span class="sxs-lookup"><span data-stu-id="06aec-148">Eventually the message is marked as poison.</span></span> <span data-ttu-id="06aec-149">将该配置设置为将病毒消息移动到病毒子队列。</span><span class="sxs-lookup"><span data-stu-id="06aec-149">The configuration is set to move the poison message to the poison subqueue.</span></span>

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
public class OrderProcessorService : IOrderProcessor
{
    static Random r = new Random(137);

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {

        int randomNumber = r.Next(10);

        if (randomNumber % 2 == 0)
        {
            Orders.Add(po);
            Console.WriteLine("Processing {0} ", po);
        }
        else
        {
            Console.WriteLine("Aborting transaction, cannot process purchase order: " + po.PONumber);
            Console.WriteLine();
            throw new Exception("Cannot process purchase order: " + po.PONumber);
        }
    }

    public static void OnServiceFaulted(object sender, EventArgs e)
    {
        Console.WriteLine("Service Faulted");
    }

    // Host the service within this EXE console application.
    public static void Main()
    {
        // Get MSMQ queue name from app settings in configuration.
        string queueName = ConfigurationManager.AppSettings["queueName"];

        // Create the transacted MSMQ queue if necessary.
        if (!System.Messaging.MessageQueue.Exists(queueName))
            System.Messaging.MessageQueue.Create(queueName, true);

        // Get the base address that is used to listen for WS-MetaDataExchange requests.
        // This is useful to generate a proxy for the client.
        string baseAddress = ConfigurationManager.AppSettings["baseAddress"];

        // Create a ServiceHost for the OrderProcessorService type.
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService), new Uri(baseAddress));

        // Hook on to the service host faulted events.
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);

        // Open the ServiceHostBase to create listeners and start listening for messages.
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        if(serviceHost.State != CommunicationState.Faulted) {
            serviceHost.Close();
        }

    }
}
```

 <span data-ttu-id="06aec-150">服务配置包括下面的病毒消息属性：`receiveRetryCount`、`maxRetryCycles`、`retryCycleDelay` 和 `receiveErrorHandling`，如下面的配置文件所示。</span><span class="sxs-lookup"><span data-stu-id="06aec-150">The service configuration includes the following poison message properties: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, and `receiveErrorHandling` as shown in the following configuration file.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <appSettings>
    <!-- Use appSetting to configure MSMQ queue name. -->
    <add key="queueName" value=".\private$\ServiceModelSamplesPoison" />
    <add key="baseAddress" value="http://localhost:8000/orderProcessor/poisonSample"/>
  </appSettings>
  <system.serviceModel>
    <services>
      <service
              name="Microsoft.ServiceModel.Samples.OrderProcessorService">
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison"
                  binding="netMsmqBinding"
                  bindingConfiguration="PoisonBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
      </service>
    </services>

    <bindings>
      <netMsmqBinding>
        <binding name="PoisonBinding"
                 receiveRetryCount="0"
                 maxRetryCycles="1"
                 retryCycleDelay="00:00:05"
                 receiveErrorHandling="Move">
        </binding>
      </netMsmqBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```

## <a name="processing-messages-from-the-poison-message-queue"></a><span data-ttu-id="06aec-151">处理病毒消息队列中的消息</span><span class="sxs-lookup"><span data-stu-id="06aec-151">Processing messages from the poison message queue</span></span>
 <span data-ttu-id="06aec-152">病毒消息服务从最终病毒消息队列中读取消息并处理这些消息。</span><span class="sxs-lookup"><span data-stu-id="06aec-152">The poison message service reads messages from the final poison message queue and processes them.</span></span>

 <span data-ttu-id="06aec-153">病毒消息队列中的消息是指发送到正在处理消息的服务的消息，这可能不同于病毒消息服务终结点。</span><span class="sxs-lookup"><span data-stu-id="06aec-153">Messages in the poison message queue are messages that are addressed to the service that is processing the message, which could be different from the poison message service endpoint.</span></span> <span data-ttu-id="06aec-154">因此，当病毒消息服务从队列中读取消息时，WCF 通道层将查找终结点中不匹配项，并且不会调度消息。</span><span class="sxs-lookup"><span data-stu-id="06aec-154">Therefore, when the poison message service reads messages from the queue, the WCF channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="06aec-155">在这种情况下，消息将发送到订单处理服务，但将由病毒消息服务接收。</span><span class="sxs-lookup"><span data-stu-id="06aec-155">In this case, the message is addressed to the order processing service but is being received by the poison message service.</span></span> <span data-ttu-id="06aec-156">如果无论消息是否发送到不同的终结点都要继续接收消息，则我们必须添加 `ServiceBehavior` 来筛选地址，其中匹配标准是要匹配消息发送到的任何服务终结点。</span><span class="sxs-lookup"><span data-stu-id="06aec-156">To continue to receive the message even if the message is addressed to a different endpoint, we must add a `ServiceBehavior` to filter addresses where the match criterion is to match any service endpoint the message is addressed to.</span></span> <span data-ttu-id="06aec-157">这是成功处理从病毒消息队列中读取的消息所必需的。</span><span class="sxs-lookup"><span data-stu-id="06aec-157">This is required to successfully process messages that you read from the poison message queue.</span></span>

 <span data-ttu-id="06aec-158">病毒消息服务实现本身非常类似于服务实现。</span><span class="sxs-lookup"><span data-stu-id="06aec-158">The poison message service implementation itself is very similar to the service implementation.</span></span> <span data-ttu-id="06aec-159">它实现协定并处理订单。</span><span class="sxs-lookup"><span data-stu-id="06aec-159">It implements the contract and processes the orders.</span></span> <span data-ttu-id="06aec-160">代码示例如下所示。</span><span class="sxs-lookup"><span data-stu-id="06aec-160">The code example is as follows.</span></span>

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
[ServiceBehavior(AddressFilterMode=AddressFilterMode.Any)]
public class OrderProcessorService : IOrderProcessor
{
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Orders.Add(po);
        Console.WriteLine("Processing {0} ", po);
    }

    public static void OnServiceFaulted(object sender, EventArgs e)
    {
        Console.WriteLine("Service Faulted...exiting app");
        Environment.Exit(1);
    }

    // Host the service within this EXE console application.
    public static void Main()
    {

        // Create a ServiceHost for the OrderProcessorService type.
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService));

        // Hook on to the service host faulted events.
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);

        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The poison message service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        // Close the ServiceHostBase to shutdown the service.
        if(serviceHost.State != CommunicationState.Faulted)
        {
            serviceHost.Close();
        }
    }
```

 <span data-ttu-id="06aec-161">不同于从订单队列读取消息的订单处理服务，病毒消息服务从病毒子队列读取消息。</span><span class="sxs-lookup"><span data-stu-id="06aec-161">Unlike the order processing service that reads messages from the order queue, the poison message service reads messages from the poison subqueue.</span></span> <span data-ttu-id="06aec-162">病毒队列是主队列的子队列，名为 "有害"，由 MSMQ 自动生成。</span><span class="sxs-lookup"><span data-stu-id="06aec-162">The poison queue is a subqueue of the main queue, is named "poison" and is automatically generated by MSMQ.</span></span> <span data-ttu-id="06aec-163">若要访问它，请提供主队列名称，后跟一个 ";" 和子队列名称，在本例中为 "有害"，如下面的示例配置中所示。</span><span class="sxs-lookup"><span data-stu-id="06aec-163">To access it, provide the main queue name followed by a ";" and the subqueue name, in this case -"poison", as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="06aec-164">在 MSMQ 3.0 版的示例中，病毒队列名称不是子队列，而是将消息移动到的队列。</span><span class="sxs-lookup"><span data-stu-id="06aec-164">In the sample for MSMQ v3.0, the poison queue name is not a sub-queue, rather the queue that we moved the message to.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.OrderProcessorService">
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison;poison"
                  binding="netMsmqBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" >
        </endpoint>
      </service>
    </services>

  </system.serviceModel>
</configuration>
```

 <span data-ttu-id="06aec-165">当运行示例时，客户端、服务和病毒消息服务活动将显示在控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="06aec-165">When you run the sample, the client, service, and poison message service activities are displayed in console windows.</span></span> <span data-ttu-id="06aec-166">您可以看到服务从客户端接收消息。</span><span class="sxs-lookup"><span data-stu-id="06aec-166">You can see the service receive messages from the client.</span></span> <span data-ttu-id="06aec-167">在每个控制台窗口中按 Enter 可以关闭服务。</span><span class="sxs-lookup"><span data-stu-id="06aec-167">Press ENTER in each console window to shut down the services.</span></span>

 <span data-ttu-id="06aec-168">服务开始运行、处理订单并随机开始终止处理。</span><span class="sxs-lookup"><span data-stu-id="06aec-168">The service starts running, processing orders and at random starts to terminate processing.</span></span> <span data-ttu-id="06aec-169">如果消息指示服务已经处理完订单，则可以再次运行客户端来发送其他消息，直到您看到服务确实已经终止某条消息。</span><span class="sxs-lookup"><span data-stu-id="06aec-169">If the message indicates it has processed the order, you can run the client again to send another message until you see the service has actually terminated a message.</span></span> <span data-ttu-id="06aec-170">根据配置的病毒设置，在将消息移到最终病毒队列中之前将再次重试处理消息。</span><span class="sxs-lookup"><span data-stu-id="06aec-170">Based on the configured poison settings, the message is tried once for processing before moving it to the final poison queue.</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 0f063b71-93e0-42a1-aa3b-bca6c7a89546
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending

Processing Purchase Order: 5ef9a4fa-5a30-4175-b455-2fb1396095fa
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending

Aborting transaction, cannot process purchase order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89
```

 <span data-ttu-id="06aec-171">启动病毒消息服务以从病毒队列中读取病毒消息。</span><span class="sxs-lookup"><span data-stu-id="06aec-171">Start up the poison message service to read the poisoned message from the poison queue.</span></span> <span data-ttu-id="06aec-172">在本示例中，病毒消息服务读取消息并处理这些消息。</span><span class="sxs-lookup"><span data-stu-id="06aec-172">In this example, the poison message service reads the message and processes it.</span></span> <span data-ttu-id="06aec-173">您可以看到病毒消息服务读取已终止并已中毒的采购订单。</span><span class="sxs-lookup"><span data-stu-id="06aec-173">You could see that the purchase order that was terminated and poisoned is read by the poison message service.</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="06aec-174">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="06aec-174">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="06aec-175">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="06aec-175">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="06aec-176">如果先运行服务，则它将检查以确保队列存在。</span><span class="sxs-lookup"><span data-stu-id="06aec-176">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="06aec-177">如果队列不存在，则服务将创建一个队列。</span><span class="sxs-lookup"><span data-stu-id="06aec-177">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="06aec-178">可以先运行服务以创建队列或通过 MSMQ 队列管理器创建一个队列。</span><span class="sxs-lookup"><span data-stu-id="06aec-178">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="06aec-179">执行下面的步骤来在 Windows 2008 中创建队列。</span><span class="sxs-lookup"><span data-stu-id="06aec-179">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="06aec-180">在 Visual Studio 2012 中打开服务器管理器。</span><span class="sxs-lookup"><span data-stu-id="06aec-180">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="06aec-181">展开 "**功能**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="06aec-181">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="06aec-182">右键单击 "**专用消息队列**"，然后选择 "**新建\*\*\*\*专用队列**"。</span><span class="sxs-lookup"><span data-stu-id="06aec-182">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="06aec-183">选中 "**事务性**" 框。</span><span class="sxs-lookup"><span data-stu-id="06aec-183">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="06aec-184">输入 `ServiceModelSamplesTransacted` 作为新队列的名称。</span><span class="sxs-lookup"><span data-stu-id="06aec-184">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="06aec-185">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="06aec-185">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="06aec-186">若要以单一计算机配置或跨计算机配置来运行示例，请更改队列名称以反映实际主机名而不是 localhost，并按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="06aec-186">To run the sample in a single- or cross-computer configuration, change the queue names to reflect the actual hostname instead of localhost and follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

 <span data-ttu-id="06aec-187">默认情况下对 `netMsmqBinding` 绑定传输启用了安全性。</span><span class="sxs-lookup"><span data-stu-id="06aec-187">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="06aec-188">`MsmqAuthenticationMode` 和 `MsmqProtectionLevel` 这两个属性共同确定了传输安全性的类型。</span><span class="sxs-lookup"><span data-stu-id="06aec-188">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="06aec-189">默认情况下，身份验证模式设置为 `Windows`，保护级别设置为 `Sign`。</span><span class="sxs-lookup"><span data-stu-id="06aec-189">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="06aec-190">MSMQ 必须是域的成员才可以提供身份验证和签名功能。</span><span class="sxs-lookup"><span data-stu-id="06aec-190">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="06aec-191">如果在不是域成员的计算机上运行此示例，则会接收以下错误：“用户的内部消息队列证书不存在”。</span><span class="sxs-lookup"><span data-stu-id="06aec-191">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>

#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="06aec-192">在加入到工作组的计算机上运行此示例</span><span class="sxs-lookup"><span data-stu-id="06aec-192">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="06aec-193">如果计算机不是域成员，请将身份验证模式和保护级别设置为 `None` 以禁用传输安全性，如下面的示例配置所示：</span><span class="sxs-lookup"><span data-stu-id="06aec-193">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     <span data-ttu-id="06aec-194">确保通过设置终结点的 bindingConfiguration 属性将终结点与绑定关联。</span><span class="sxs-lookup"><span data-stu-id="06aec-194">Ensure the endpoint is associated with the binding by setting the endpoint's bindingConfiguration attribute.</span></span>

2. <span data-ttu-id="06aec-195">请确保在运行示例前更改 PoisonMessageServer、服务器和客户端上的配置。</span><span class="sxs-lookup"><span data-stu-id="06aec-195">Ensure that you change the configuration on the PoisonMessageServer, server, and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="06aec-196">将 `security mode` 设置为 `None` 等效于将 `MsmqAuthenticationMode`、`MsmqProtectionLevel` 和 `Message` 安全设置为 `None`。</span><span class="sxs-lookup"><span data-stu-id="06aec-196">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel`, and `Message` security to `None`.</span></span>  
  
3. <span data-ttu-id="06aec-197">若要使元数据交换正常工作，应当向 http 绑定注册一个 URL。</span><span class="sxs-lookup"><span data-stu-id="06aec-197">In order for Meta Data Exchange to work, we register a URL with http binding.</span></span> <span data-ttu-id="06aec-198">这要求服务在具有提升权限的命令窗口中运行。</span><span class="sxs-lookup"><span data-stu-id="06aec-198">This requires that the service run in an elevated command window.</span></span> <span data-ttu-id="06aec-199">否则，你将得到如下所示的异常： `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied` 。</span><span class="sxs-lookup"><span data-stu-id="06aec-199">Otherwise, you get an exception such as: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="06aec-200">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="06aec-200">The samples may already be installed on your computer.</span></span> <span data-ttu-id="06aec-201">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="06aec-201">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="06aec-202">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="06aec-202">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="06aec-203">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="06aec-203">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`

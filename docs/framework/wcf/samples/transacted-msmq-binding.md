---
title: 已经过事务处理的 MSMQ 绑定
ms.date: 03/30/2017
ms.assetid: 71f5cb8d-f1df-4e1e-b8a2-98e734a75c37
ms.openlocfilehash: fa53099caba144f321698f180fe18f7614a1fa64
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596560"
---
# <a name="transacted-msmq-binding"></a><span data-ttu-id="5dd09-102">已经过事务处理的 MSMQ 绑定</span><span class="sxs-lookup"><span data-stu-id="5dd09-102">Transacted MSMQ Binding</span></span>

<span data-ttu-id="5dd09-103">本示例演示如何使用消息队列 (MSMQ) 执行已经过事务处理的排队通信。</span><span class="sxs-lookup"><span data-stu-id="5dd09-103">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ).</span></span>

> [!NOTE]
> <span data-ttu-id="5dd09-104">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="5dd09-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="5dd09-105">在排队通信中，客户端使用队列与服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="5dd09-105">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="5dd09-106">更确切地说，客户端向队列发送消息。</span><span class="sxs-lookup"><span data-stu-id="5dd09-106">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="5dd09-107">服务从队列接收消息。</span><span class="sxs-lookup"><span data-stu-id="5dd09-107">The service receives messages from the queue.</span></span> <span data-ttu-id="5dd09-108">因此，不必同时运行服务和客户端便可使用队列进行通信。</span><span class="sxs-lookup"><span data-stu-id="5dd09-108">The service and client, therefore, do not have to be running at the same time to communicate using a queue.</span></span>

<span data-ttu-id="5dd09-109">当事务用于发送和接收消息时，实际上有两个单独的事务。</span><span class="sxs-lookup"><span data-stu-id="5dd09-109">When transactions are used to send and receive messages, there are actually two separate transactions.</span></span> <span data-ttu-id="5dd09-110">当客户端在事务范围内发送消息时，事务相对于客户端和客户端队列管理器来说是本地事务。</span><span class="sxs-lookup"><span data-stu-id="5dd09-110">When the client sends messages within the scope of a transaction, the transaction is local to the client and the client queue manager.</span></span> <span data-ttu-id="5dd09-111">当服务在事务范围内接收消息时，事务相对于服务和接收队列管理器来说是本地事务。</span><span class="sxs-lookup"><span data-stu-id="5dd09-111">When the service receives messages within the scope of the transaction, the transaction is local to the service and the receiving queue manager.</span></span> <span data-ttu-id="5dd09-112">请务必牢记，客户端和服务不会参与同一个事务；实际上，它们在对队列执行操作（如发送和接收）时使用的是不同的事务。</span><span class="sxs-lookup"><span data-stu-id="5dd09-112">It is very important to remember that the client and the service are not participating in the same transaction; rather, they are using different transactions when performing their operations (such as send and receive) with the queue.</span></span>

<span data-ttu-id="5dd09-113">在本示例中，客户端在事务范围内向服务发送一批消息。</span><span class="sxs-lookup"><span data-stu-id="5dd09-113">In this sample, the client sends a batch of messages to the service from within the scope of a transaction.</span></span> <span data-ttu-id="5dd09-114">然后，服务在服务定义的事务范围内接收发送到队列的消息。</span><span class="sxs-lookup"><span data-stu-id="5dd09-114">The messages sent to the queue are then received by the service within the transaction scope defined by the service.</span></span>

<span data-ttu-id="5dd09-115">服务协定为 `IOrderProcessor`，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="5dd09-115">The service contract is `IOrderProcessor`, as shown in the following sample code.</span></span> <span data-ttu-id="5dd09-116">此接口定义了适合与队列一起使用的单向服务。</span><span class="sxs-lookup"><span data-stu-id="5dd09-116">The interface defines a one-way service that is suitable for use with queues.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

<span data-ttu-id="5dd09-117">服务行为通过将 `TransactionScopeRequired` 设置为 `true` 来定义操作行为。</span><span class="sxs-lookup"><span data-stu-id="5dd09-117">The service behavior defines an operation behavior with `TransactionScopeRequired` set to `true`.</span></span> <span data-ttu-id="5dd09-118">这可确保此方法所访问的任何资源管理器都使用相同的事务范围从队列中检索消息。</span><span class="sxs-lookup"><span data-stu-id="5dd09-118">This ensures that the same transaction scope that is used to retrieve the message from the queue is used by any resource managers accessed by the method.</span></span> <span data-ttu-id="5dd09-119">它还确保在方法引发异常的情况下，将消息返回到队列。</span><span class="sxs-lookup"><span data-stu-id="5dd09-119">It also guarantees that if the method throws an exception, the message is returned to the queue.</span></span> <span data-ttu-id="5dd09-120">如果未设置操作行为，队列通道会创建一个从队列中读取消息的事务，并在调度前自动提交该事务，这样当操作失败时，消息将丢失。</span><span class="sxs-lookup"><span data-stu-id="5dd09-120">Without setting this operation behavior, a queued channel creates a transaction to read the message from the queue and commits it automatically before dispatch such that if the operation fails, the message is lost.</span></span> <span data-ttu-id="5dd09-121">对于服务操作而言，最常见的方案是在用于从队列中读取消息的事务中进行登记，如下面的代码中所示。</span><span class="sxs-lookup"><span data-stu-id="5dd09-121">The most common scenario is for service operations to enlist in the transaction that is used to read the message from the queue, as demonstrated in the following code.</span></span>

```csharp
 // This service class that implements the service contract.
 // This added code writes output to the console window.
 public class OrderProcessorService : IOrderProcessor
 {
     [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
     public void SubmitPurchaseOrder(PurchaseOrder po)
     {
         Orders.Add(po);
         Console.WriteLine("Processing {0} ", po);
     }
  …
}
```

<span data-ttu-id="5dd09-122">服务是自承载服务。</span><span class="sxs-lookup"><span data-stu-id="5dd09-122">The service is self hosted.</span></span> <span data-ttu-id="5dd09-123">使用 MSMQ 传输时，必须提前创建所使用的队列。</span><span class="sxs-lookup"><span data-stu-id="5dd09-123">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="5dd09-124">可以手动或通过代码完成此操作。</span><span class="sxs-lookup"><span data-stu-id="5dd09-124">This can be done manually or through code.</span></span> <span data-ttu-id="5dd09-125">在此示例中，该服务包含代码，以检查队列是否存在并在不存在时创建队列。</span><span class="sxs-lookup"><span data-stu-id="5dd09-125">In this sample, the service contains code to check for the existence of the queue and create the queue if it does not exist.</span></span> <span data-ttu-id="5dd09-126">从配置文件中读取队列名称。</span><span class="sxs-lookup"><span data-stu-id="5dd09-126">The queue name is read from the configuration file.</span></span> <span data-ttu-id="5dd09-127">基址[元数据实用工具（svcutil.exe）](../servicemodel-metadata-utility-tool-svcutil-exe.md)使用该基址来生成服务的代理。</span><span class="sxs-lookup"><span data-stu-id="5dd09-127">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>

```csharp
// Host the service within this EXE console application.
public static void Main()
{
    // Get the MSMQ queue name from appSettings in configuration.
    string queueName = ConfigurationManager.AppSettings["queueName"];

    // Create the transacted MSMQ queue if necessary.
    if (!MessageQueue.Exists(queueName))
        MessageQueue.Create(queueName, true);

    // Create a ServiceHost for the OrderProcessorService type.
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))
    {
        // Open the ServiceHost to create listeners and start listening for messages.
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        // Close the ServiceHost to shut down the service.
        serviceHost.Close();
    }
}
```

<span data-ttu-id="5dd09-128">MSMQ 队列名称在配置文件的 appSettings 节中指定，如以下示例配置所示。</span><span class="sxs-lookup"><span data-stu-id="5dd09-128">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

```xml
<appSettings>
    <add key="queueName" value=".\private$\ServiceModelSamplesTransacted" />
</appSettings>
```

> [!NOTE]
> <span data-ttu-id="5dd09-129">队列名称为本地计算机使用圆点 (.)，并在使用 <xref:System.Messaging> 创建队列时在其路径中使用反斜杠分隔符。</span><span class="sxs-lookup"><span data-stu-id="5dd09-129">The queue name uses a dot (.) for the local computer and backslash separators in its path when creating the queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="5dd09-130">Windows Communication Foundation （WCF）终结点使用带有 net.pipe 方案的队列地址，使用 "localhost" 来表示本地计算机，并在其路径中使用正斜杠。</span><span class="sxs-lookup"><span data-stu-id="5dd09-130">The Windows Communication Foundation (WCF) endpoint uses the queue address with net.msmq scheme, uses "localhost" to denote the local computer, and uses forward slashes in its path.</span></span>

<span data-ttu-id="5dd09-131">客户端创建事务范围。</span><span class="sxs-lookup"><span data-stu-id="5dd09-131">The client creates a transaction scope.</span></span> <span data-ttu-id="5dd09-132">与队列的通信发生在事务范围之内，从而可将该事务范围视为原子单元，其中所有消息均将发送到队列或者没有任何消息发送到队列。</span><span class="sxs-lookup"><span data-stu-id="5dd09-132">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages are sent to the queue or none of the messages are sent to the queue.</span></span> <span data-ttu-id="5dd09-133">通过在事务范围上调用 <xref:System.Transactions.TransactionScope.Complete%2A> 可以提交事务。</span><span class="sxs-lookup"><span data-stu-id="5dd09-133">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A> on the transaction scope.</span></span>

```csharp
// Create a client.
OrderProcessorClient client = new OrderProcessorClient();

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

// Create a transaction scope.
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
{
    // Make a queued call to submit the purchase order.
    client.SubmitPurchaseOrder(po);
    // Complete the transaction.
    scope.Complete();
}

// Closing the client gracefully closes the connection and cleans up resources.
client.Close();

Console.WriteLine();
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

<span data-ttu-id="5dd09-134">若要验证事务正在运行，请按照下面的示例代码注释事务范围来修改客户端，重新生成解决方案并运行客户端。</span><span class="sxs-lookup"><span data-stu-id="5dd09-134">To verify that transactions are working, modify the client by commenting the transaction scope as shown in the following sample code, rebuild the solution, and run the client.</span></span>

```csharp
//scope.Complete();
```

<span data-ttu-id="5dd09-135">因为事务没有完成，所以消息未发送到队列。</span><span class="sxs-lookup"><span data-stu-id="5dd09-135">Because the transaction is not completed, the messages are not sent to the queue.</span></span>

<span data-ttu-id="5dd09-136">运行示例时，客户端和服务活动将显示在服务和客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="5dd09-136">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="5dd09-137">您可以看到服务从客户端接收消息。</span><span class="sxs-lookup"><span data-stu-id="5dd09-137">You can see the service receive messages from the client.</span></span> <span data-ttu-id="5dd09-138">在每个控制台窗口中按 Enter 可以关闭服务和客户端。</span><span class="sxs-lookup"><span data-stu-id="5dd09-138">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="5dd09-139">请注意：由于正在使用队列，因此不必同时启动和运行客户端和服务。</span><span class="sxs-lookup"><span data-stu-id="5dd09-139">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="5dd09-140">可以先运行客户端，再将其关闭，然后启动服务，这样服务仍然会收到客户端的消息。</span><span class="sxs-lookup"><span data-stu-id="5dd09-140">You can run the client, shut it down, and then start up the service and it still receives the messages.</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 7b31ce51-ae7c-4def-9b8b-617e4288eafd
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5dd09-141">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="5dd09-141">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="5dd09-142">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="5dd09-142">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="5dd09-143">如果先运行服务，则它将检查以确保队列存在。</span><span class="sxs-lookup"><span data-stu-id="5dd09-143">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="5dd09-144">如果队列不存在，则服务将创建一个队列。</span><span class="sxs-lookup"><span data-stu-id="5dd09-144">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="5dd09-145">可以先运行服务以创建队列或通过 MSMQ 队列管理器创建一个队列。</span><span class="sxs-lookup"><span data-stu-id="5dd09-145">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="5dd09-146">执行下面的步骤来在 Windows 2008 中创建队列。</span><span class="sxs-lookup"><span data-stu-id="5dd09-146">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="5dd09-147">在 Visual Studio 2012 中打开服务器管理器。</span><span class="sxs-lookup"><span data-stu-id="5dd09-147">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="5dd09-148">展开 "**功能**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="5dd09-148">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="5dd09-149">右键单击 "**专用消息队列**"，然后选择 "**新建\*\*\*\*专用队列**"。</span><span class="sxs-lookup"><span data-stu-id="5dd09-149">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="5dd09-150">选中 "**事务性**" 框。</span><span class="sxs-lookup"><span data-stu-id="5dd09-150">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="5dd09-151">输入 `ServiceModelSamplesTransacted` 作为新队列的名称。</span><span class="sxs-lookup"><span data-stu-id="5dd09-151">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="5dd09-152">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="5dd09-152">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="5dd09-153">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="5dd09-153">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

<span data-ttu-id="5dd09-154">默认情况下使用 <xref:System.ServiceModel.NetMsmqBinding> 启用传输安全。</span><span class="sxs-lookup"><span data-stu-id="5dd09-154">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="5dd09-155">对于 MSMQ 传输安全存在两个相关属性：<xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> 和 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>。</span><span class="sxs-lookup"><span data-stu-id="5dd09-155">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>.</span></span> <span data-ttu-id="5dd09-156">默认情况下，身份验证模式设置为 `Windows`，保护级别设置为 `Sign`。</span><span class="sxs-lookup"><span data-stu-id="5dd09-156">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="5dd09-157">为了使 MSMQ 提供身份验证和签名功能，MSMQ 必须是域的一部分，并且必须安装 MSMQ 的 Active Directory 集成选项。</span><span class="sxs-lookup"><span data-stu-id="5dd09-157">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the Active Directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="5dd09-158">如果在未满足这些条件的计算机上运行此示例，将会收到错误。</span><span class="sxs-lookup"><span data-stu-id="5dd09-158">If you run this sample on a computer that does not satisfy these criteria, you receive an error.</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="5dd09-159">在加入到工作组或在没有 Active Directory 集成的计算机上运行示例</span><span class="sxs-lookup"><span data-stu-id="5dd09-159">To run the sample on a computer joined to a workgroup or without Active Directory integration</span></span>

1. <span data-ttu-id="5dd09-160">如果计算机不是域成员或尚未安装 Active Directory 集成，请将身份验证模式和保护级别设置为 `None` 以关闭传输安全性，如下面的示例配置代码所示。</span><span class="sxs-lookup"><span data-stu-id="5dd09-160">If your computer is not part of a domain or does not have Active Directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration code.</span></span>

    ```xml
    <system.serviceModel>
      <services>
        <service name="Microsoft.ServiceModel.Samples.OrderProcessorService"
                 behaviorConfiguration="OrderProcessorServiceBehavior">
          <host>
            <baseAddresses>
              <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
            </baseAddresses>
          </host>
          <!-- Define NetMsmqEndpoint. -->
          <endpoint
              address="net.msmq://localhost/private/ServiceModelSamplesTransacted"
              binding="netMsmqBinding"
              bindingConfiguration="Binding1"
           contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
          <!-- The mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex. -->
          <endpoint address="mex"
                    binding="mexHttpBinding"
                    contract="IMetadataExchange" />
        </service>
      </services>

      <bindings>
        <netMsmqBinding>
          <binding name="Binding1">
            <security mode="None" />
          </binding>
        </netMsmqBinding>
      </bindings>

        <behaviors>
          <serviceBehaviors>
            <behavior name="OrderProcessorServiceBehavior">
              <serviceMetadata httpGetEnabled="True"/>
            </behavior>
          </serviceBehaviors>
        </behaviors>

      </system.serviceModel>
    ```

2. <span data-ttu-id="5dd09-161">确保在运行示例前更改服务器和客户端上的配置。</span><span class="sxs-lookup"><span data-stu-id="5dd09-161">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="5dd09-162">将 `security mode` 设置为 `None` 等效于将 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>、<xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> 和 `Message` 安全设置为 `None`。</span><span class="sxs-lookup"><span data-stu-id="5dd09-162">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5dd09-163">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="5dd09-163">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5dd09-164">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="5dd09-164">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="5dd09-165">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="5dd09-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5dd09-166">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="5dd09-166">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Transacted`

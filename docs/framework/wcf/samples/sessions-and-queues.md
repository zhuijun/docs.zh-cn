---
title: 会话和队列
ms.date: 03/30/2017
ms.assetid: 47d7c5c2-1e6f-4619-8003-a0ff67dcfbd6
ms.openlocfilehash: 425135b533b898cbc75464f50ce8a5e8f6550755
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84584163"
---
# <a name="sessions-and-queues"></a><span data-ttu-id="bc858-102">会话和队列</span><span class="sxs-lookup"><span data-stu-id="bc858-102">Sessions and queues</span></span>

<span data-ttu-id="bc858-103">此示例演示如何通过消息队列 (MSMQ) 传输来发送和接收排队通信中的一组相关消息。</span><span class="sxs-lookup"><span data-stu-id="bc858-103">This sample demonstrates how to send and receive a set of related messages in queued communication over the Message Queuing (MSMQ) transport.</span></span> <span data-ttu-id="bc858-104">本示例使用 `netMsmqBinding` 绑定。</span><span class="sxs-lookup"><span data-stu-id="bc858-104">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="bc858-105">此服务是自承载控制台应用程序，通过它可以观察服务接收排队消息。</span><span class="sxs-lookup"><span data-stu-id="bc858-105">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bc858-106">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="bc858-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bc858-107">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="bc858-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bc858-108">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="bc858-108">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="bc858-109">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="bc858-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bc858-110">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="bc858-110">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Session`  
  
 <span data-ttu-id="bc858-111">在排队通信中，客户端使用队列与服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="bc858-111">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="bc858-112">更确切地说，客户端向队列发送消息。</span><span class="sxs-lookup"><span data-stu-id="bc858-112">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="bc858-113">服务从队列接收消息。</span><span class="sxs-lookup"><span data-stu-id="bc858-113">The service receives messages from the queue.</span></span> <span data-ttu-id="bc858-114">因此不必同时运行服务和客户端便可使用队列进行通信。</span><span class="sxs-lookup"><span data-stu-id="bc858-114">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="bc858-115">有时，客户端会发送在组中相关的一组消息。</span><span class="sxs-lookup"><span data-stu-id="bc858-115">Sometimes, a client sends a set of messages that are related to each other in a group.</span></span> <span data-ttu-id="bc858-116">如果必须同时或按指定顺序处理消息，则可以使用队列将这些消息分为一组，以便由单一的接收应用程序进行处理。</span><span class="sxs-lookup"><span data-stu-id="bc858-116">When messages must be processed together or in a specified order, a queue can be used to group them together, for processing by a single receiving application.</span></span> <span data-ttu-id="bc858-117">这对于一组服务器上有多个接收应用程序的情况尤其重要，并且有必要确保一组消息由同一个接收应用程序来处理。</span><span class="sxs-lookup"><span data-stu-id="bc858-117">This is particularly important when there are several receiving applications on a group of servers and it is necessary to ensure that a group of messages is processed by the same receiving application.</span></span> <span data-ttu-id="bc858-118">排队的会话是一种用于发送和接收必须同时处理的一组相关消息的机制。</span><span class="sxs-lookup"><span data-stu-id="bc858-118">Queued sessions are a mechanism used to send and receive a related set of messages that must get processed all at once.</span></span> <span data-ttu-id="bc858-119">排队的会话需要一个展示此模式的事务。</span><span class="sxs-lookup"><span data-stu-id="bc858-119">Queued sessions require a transaction to exhibit this pattern.</span></span>  
  
 <span data-ttu-id="bc858-120">在该示例中，客户端向服务发送多则消息，作为单一事务范围中的会话的一部分。</span><span class="sxs-lookup"><span data-stu-id="bc858-120">In the sample, the client sends a number of messages to the service as part of a session within the scope of a single transaction.</span></span>  
  
 <span data-ttu-id="bc858-121">服务协定是 `IOrderTaker`，它定义了适合与队列一起使用的单向服务。</span><span class="sxs-lookup"><span data-stu-id="bc858-121">The service contract is `IOrderTaker`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="bc858-122">在以下示例代码中显示的协定中使用的 <xref:System.ServiceModel.SessionMode> 表明消息是会话的一部分。</span><span class="sxs-lookup"><span data-stu-id="bc858-122">The <xref:System.ServiceModel.SessionMode> used in the contract shown in the following sample code indicates that the messages are part of the session.</span></span>  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required)]  
public interface IOrderTaker  
{  
    [OperationContract(IsOneWay = true)]  
    void OpenPurchaseOrder(string customerId);  
  
    [OperationContract(IsOneWay = true)]  
    void AddProductLineItem(string productId, int quantity);  
  
    [OperationContract(IsOneWay = true)]  
    void EndPurchaseOrder();  
}  
```

 <span data-ttu-id="bc858-123">该服务按如下方式定义服务操作：第一个操作在事务中登记，但不会自动完成事务。</span><span class="sxs-lookup"><span data-stu-id="bc858-123">The service defines service operations in such a way that the first operation enlists in a transaction but does not automatically complete the transaction.</span></span> <span data-ttu-id="bc858-124">后续操作也在同一个事务中登记，但也不自动完成事务。</span><span class="sxs-lookup"><span data-stu-id="bc858-124">Subsequent operations also enlist in the same transaction but do not automatically complete.</span></span> <span data-ttu-id="bc858-125">会话中的最后一个操作自动完成该事务。</span><span class="sxs-lookup"><span data-stu-id="bc858-125">The last operation in the session automatically completes the transaction.</span></span> <span data-ttu-id="bc858-126">因此，对服务协定中的若干个操作调用使用了同一个事务。</span><span class="sxs-lookup"><span data-stu-id="bc858-126">Thus, the same transaction is used for several operation invocations in the service contract.</span></span> <span data-ttu-id="bc858-127">如果其中任何一个操作引发异常，则事务将回滚，并且会话将返回到队列中。</span><span class="sxs-lookup"><span data-stu-id="bc858-127">If any of the operations throw an exception, then the transaction rolls back and the session is put back into the queue.</span></span> <span data-ttu-id="bc858-128">成功完成最后一个操作后，事务即已提交。</span><span class="sxs-lookup"><span data-stu-id="bc858-128">Upon successful completion of the last operation, the transaction is committed.</span></span> <span data-ttu-id="bc858-129">服务使用 `PerSession` 作为 <xref:System.ServiceModel.InstanceContextMode>，以便在服务的同一个实例上的会话中接收所有消息。</span><span class="sxs-lookup"><span data-stu-id="bc858-129">The service uses `PerSession` as the <xref:System.ServiceModel.InstanceContextMode> to receive all messages in a session on the same instance of the service.</span></span>  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class OrderTakerService : IOrderTaker  
{  
    PurchaseOrder po;  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                 TransactionAutoComplete = false)]  
    public void OpenPurchaseOrder(string customerId)  
    {  
        Console.WriteLine("Creating purchase order");  
        po = new PurchaseOrder(customerId);  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                  TransactionAutoComplete = false)]  
    public void AddProductLineItem(string productId, int quantity)  
    {  
        po.AddProductLineItem(productId, quantity);  
        Console.WriteLine("Product " + productId + " quantity " +
                            quantity + " added to purchase order");  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                  TransactionAutoComplete = true)]  
    public void EndPurchaseOrder()  
    {  
       Console.WriteLine("Purchase Order Completed");  
       Console.WriteLine();  
       Console.WriteLine(po.ToString());  
    }  
}  
```

 <span data-ttu-id="bc858-130">服务是自承载服务。</span><span class="sxs-lookup"><span data-stu-id="bc858-130">The service is self hosted.</span></span> <span data-ttu-id="bc858-131">使用 MSMQ 传输时，必须提前创建所使用的队列。</span><span class="sxs-lookup"><span data-stu-id="bc858-131">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="bc858-132">可以手动或通过代码完成此操作。</span><span class="sxs-lookup"><span data-stu-id="bc858-132">This can be done manually or through code.</span></span> <span data-ttu-id="bc858-133">在此示例中，服务包含 <xref:System.Messaging> 代码，以检查队列是否存在并在必要时创建队列。</span><span class="sxs-lookup"><span data-stu-id="bc858-133">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="bc858-134">使用 <xref:System.Configuration.ConfigurationManager.AppSettings%2A> 类从配置文件中读取队列名称。</span><span class="sxs-lookup"><span data-stu-id="bc858-134">The queue name is read from the configuration file using the <xref:System.Configuration.ConfigurationManager.AppSettings%2A> class.</span></span>  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the OrderTakerService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderTakerService)))  
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

 <span data-ttu-id="bc858-135">MSMQ 队列名称是在配置文件的 appSettings 节中指定的。</span><span class="sxs-lookup"><span data-stu-id="bc858-135">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="bc858-136">服务终结点是在配置文件的 system.serviceModel 节中定义的，它指定了 `netMsmqBinding` 绑定。</span><span class="sxs-lookup"><span data-stu-id="bc858-136">The endpoint for the service is defined in the system.serviceModel section of the configuration file and specifies the `netMsmqBinding` binding.</span></span>  
  
```xml  
<appSettings>  
  <!-- Use appSetting to configure MSMQ queue name. -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesSession" />  
</appSettings>  
  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.OrderTakerService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
      ...  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesSession"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderTaker" />  
      ...  
    </service>  
  </services>  
  ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="bc858-137">客户端创建事务范围。</span><span class="sxs-lookup"><span data-stu-id="bc858-137">The client creates a transaction scope.</span></span> <span data-ttu-id="bc858-138">会话中的所有消息都将发送到该事务范围中的队列，使其被视为一个原子单元，其中的所有消息都将成功或失败。</span><span class="sxs-lookup"><span data-stu-id="bc858-138">All messages in the session are sent to the queue within the transaction scope, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span> <span data-ttu-id="bc858-139">通过调用 <xref:System.Transactions.TransactionScope.Complete%2A> 提交事务。</span><span class="sxs-lookup"><span data-stu-id="bc858-139">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A>.</span></span>  

```csharp
//Create a transaction scope.  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    // Create a client with given client endpoint configuration.  
    OrderTakerClient client = new OrderTakerClient("OrderTakerEndpoint");  
    // Open a purchase order.  
    client.OpenPurchaseOrder("somecustomer.com");  
    Console.WriteLine("Purchase Order created");  
  
    // Add product line items.  
    Console.WriteLine("Adding 10 quantities of blue widget");  
    client.AddProductLineItem("Blue Widget", 10);  
  
    Console.WriteLine("Adding 23 quantities of red widget");  
    client.AddProductLineItem("Red Widget", 23);  
  
    // Close the purchase order.  
    Console.WriteLine("Closing the purchase order");  
    client.EndPurchaseOrder();  
  
    //Closing the client gracefully closes the connection and cleans up resources.  
    client.Close();
  
    // Complete the transaction.  
    scope.Complete();  
}  
```

> [!NOTE]
> <span data-ttu-id="bc858-140">只能对会话中的所有消息使用单一事务，并且必须在提交事务之前发送会话中的所有消息。</span><span class="sxs-lookup"><span data-stu-id="bc858-140">You can use only a single transaction for all messages in the session and all messages in the session must be sent before committing the transaction.</span></span> <span data-ttu-id="bc858-141">关闭客户端将关闭会话。</span><span class="sxs-lookup"><span data-stu-id="bc858-141">Closing the client closes the session.</span></span> <span data-ttu-id="bc858-142">因此，必须在完成事务之前关闭客户端，以便向队列发送会话中的所有消息。</span><span class="sxs-lookup"><span data-stu-id="bc858-142">Therefore, the client has to be closed before the transaction is completed to send all messages in the session to the queue.</span></span>  
  
 <span data-ttu-id="bc858-143">运行示例时，客户端和服务活动将显示在服务和客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="bc858-143">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="bc858-144">您可以看到服务从客户端接收消息。</span><span class="sxs-lookup"><span data-stu-id="bc858-144">You can see the service receive messages from the client.</span></span> <span data-ttu-id="bc858-145">在每个控制台窗口中按 Enter 可以关闭服务和客户端。</span><span class="sxs-lookup"><span data-stu-id="bc858-145">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="bc858-146">由于队列正在使用中，因此不必同时启动和运行客户端和服务。</span><span class="sxs-lookup"><span data-stu-id="bc858-146">Because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="bc858-147">可以先运行客户端，再将其关闭，然后启动服务，这样服务仍然会收到客户端的消息。</span><span class="sxs-lookup"><span data-stu-id="bc858-147">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span>  
  
 <span data-ttu-id="bc858-148">在客户端上。</span><span class="sxs-lookup"><span data-stu-id="bc858-148">On the client.</span></span>  
  
```console  
Purchase Order created  
Adding 10 quantities of blue widget  
Adding 23 quantities of red widget  
Closing the purchase order  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="bc858-149">在服务上。</span><span class="sxs-lookup"><span data-stu-id="bc858-149">On the service.</span></span>  
  
```console  
The service is ready.  
Press <ENTER> to terminate service.  
  
Creating purchase order  
Product Blue Widget quantity 10 added to purchase order  
Product Red Widget quantity 23 added to purchase order  
Purchase Order Completed  
  
Purchase Order: 7c86fef0-2306-4c51-80e6-bcabcc1a6e5e  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 10 of Blue Widget @unit price: $2985  
                Order LineItem: 23 of Red Widget @unit price: $156  
        Total cost of this order: $33438  
        Order status: Pending  
```  
  
### <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="bc858-150">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="bc858-150">Set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="bc858-151">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="bc858-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="bc858-152">若要生成 c #、c + + 或 Visual Basic .NET 版本的解决方案，请按照[生成 Windows Communication Foundation 示例](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="bc858-152">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="bc858-153">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="bc858-153">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
 <span data-ttu-id="bc858-154">默认情况下使用 <xref:System.ServiceModel.NetMsmqBinding> 启用传输安全。</span><span class="sxs-lookup"><span data-stu-id="bc858-154">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="bc858-155">MSMQ 传输安全有两个相关的属性， <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` 默认情况下，身份验证模式设置为， `Windows` 保护级别设置为 `Sign` 。</span><span class="sxs-lookup"><span data-stu-id="bc858-155">There are two relevant properties for MSMQ transport security namely, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="bc858-156">为了使 MSMQ 提供身份验证和签名功能，MSMQ 必须是域的一部分，并且必须安装 MSMQ 的 Active Directory 集成选项。</span><span class="sxs-lookup"><span data-stu-id="bc858-156">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="bc858-157">如果在未满足这些条件的计算机上运行此示例，将会收到错误。</span><span class="sxs-lookup"><span data-stu-id="bc858-157">If you run this sample on a computer that does not satisfy these criteria, you receive an error.</span></span>  
  
### <a name="run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="bc858-158">在加入工作组的计算机上运行示例</span><span class="sxs-lookup"><span data-stu-id="bc858-158">Run the sample on a computer joined to a workgroup</span></span>  
  
1. <span data-ttu-id="bc858-159">如果您的计算机不是域成员或尚未安装 Active Directory 集成，请将身份验证模式和保护级别设置为 `None` 以关闭传输安全性，如下面的示例配置所示。</span><span class="sxs-lookup"><span data-stu-id="bc858-159">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <services>  
        <service name="Microsoft.ServiceModel.Samples.OrderTakerService"  
                 behaviorConfiguration="OrderTakerServiceBehavior">  
          <host>  
            <baseAddresses>  
              <add baseAddress=  
             "http://localhost:8000/ServiceModelSamples/service"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint  
              address=  
            "net.msmq://localhost/private/ServiceModelSamplesSession"  
              binding="netMsmqBinding"  
              bindingConfiguration="Binding1"  
           contract="Microsoft.ServiceModel.Samples.IOrderTaker" />  
          <!-- The mex endpoint is exposed at-->
          <!--http://localhost:8000/ServiceModelSamples/service/mex. -->  
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
            <behavior name="OrderTakerServiceBehavior">  
              <serviceMetadata httpGetEnabled="True"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    ```  
  
2. <span data-ttu-id="bc858-160">确保在运行示例前更改服务器和客户端上的配置。</span><span class="sxs-lookup"><span data-stu-id="bc858-160">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="bc858-161">将安全模式设置为 `None` 等效于将 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>、<xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> 和 `Message` 安全设置为 `None`。</span><span class="sxs-lookup"><span data-stu-id="bc858-161">Setting security mode to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  

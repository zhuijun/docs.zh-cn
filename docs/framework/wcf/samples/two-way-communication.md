---
title: 双向通信
ms.date: 03/30/2017
ms.assetid: fb64192d-b3ea-4e02-9fb3-46a508d26c60
ms.openlocfilehash: 291380d656b0e22c7fdf1cb291c45d05359a95c8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591262"
---
# <a name="two-way-communication"></a><span data-ttu-id="f0c40-102">双向通信</span><span class="sxs-lookup"><span data-stu-id="f0c40-102">Two-Way Communication</span></span>
<span data-ttu-id="f0c40-103">本示例演示如何通过 MSMQ 执行事务处理双向排队通信。</span><span class="sxs-lookup"><span data-stu-id="f0c40-103">This sample demonstrates how to perform transacted two-way queued communication over MSMQ.</span></span> <span data-ttu-id="f0c40-104">本示例使用 `netMsmqBinding` 绑定。</span><span class="sxs-lookup"><span data-stu-id="f0c40-104">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="f0c40-105">在本例中，服务是一个自承载的控制台应用程序，通过它可以观察服务接收排队消息。</span><span class="sxs-lookup"><span data-stu-id="f0c40-105">In this case, the service is a self-hosted console application that allows you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f0c40-106">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="f0c40-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f0c40-107">此示例基于已进行[事务处理的 MSMQ 绑定](transacted-msmq-binding.md)。</span><span class="sxs-lookup"><span data-stu-id="f0c40-107">This sample is based on the [Transacted MSMQ Binding](transacted-msmq-binding.md).</span></span>  
  
 <span data-ttu-id="f0c40-108">在排队通信中，客户端使用队列与服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="f0c40-108">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="f0c40-109">客户端向队列发送消息，服务从队列接收消息。</span><span class="sxs-lookup"><span data-stu-id="f0c40-109">The client sends messages to a queue, and the service receives messages from the queue.</span></span> <span data-ttu-id="f0c40-110">因此不必同时运行服务和客户端便可使用队列进行通信。</span><span class="sxs-lookup"><span data-stu-id="f0c40-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="f0c40-111">本示例演示使用队列的双向通信。</span><span class="sxs-lookup"><span data-stu-id="f0c40-111">This sample demonstrates 2-way communication using queues.</span></span> <span data-ttu-id="f0c40-112">客户端从事务范围内向队列发送采购订单。</span><span class="sxs-lookup"><span data-stu-id="f0c40-112">The client sends purchase orders to the queue from within the scope of a transaction.</span></span> <span data-ttu-id="f0c40-113">服务接收订单、处理订单，然后在事务范围内使用队列中订单的状态回调客户端。</span><span class="sxs-lookup"><span data-stu-id="f0c40-113">The service receives the orders, processes the order and then calls back the client with the status of the order from the queue within the scope of a transaction.</span></span> <span data-ttu-id="f0c40-114">为了便于双向通信，客户端和服务都使用队列以便将采购订单和订单状态排入队列。</span><span class="sxs-lookup"><span data-stu-id="f0c40-114">To facilitate two-way communication the client and service both use queues to enqueue purchase orders and order status.</span></span>  
  
 <span data-ttu-id="f0c40-115">服务协定 `IOrderProcessor` 定义适合使用队列的单向服务操作。</span><span class="sxs-lookup"><span data-stu-id="f0c40-115">The service contract `IOrderProcessor` defines one-way service operations that suit the use of queuing.</span></span> <span data-ttu-id="f0c40-116">服务操作包括用于向其发送订单状态的答复终结点。</span><span class="sxs-lookup"><span data-stu-id="f0c40-116">The service operation includes the reply endpoint to use to send the order statuses to.</span></span> <span data-ttu-id="f0c40-117">答复终结点是用于将订单状态发回客户端的队列的 URI。</span><span class="sxs-lookup"><span data-stu-id="f0c40-117">The reply endpoint is the URI of the queue to send the order status back to the client.</span></span> <span data-ttu-id="f0c40-118">订单处理应用程序实现下面的协定。</span><span class="sxs-lookup"><span data-stu-id="f0c40-118">The order processing application implements this contract.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po, string
                                  reportOrderStatusTo);  
}
```
  
 <span data-ttu-id="f0c40-119">用于发送订单状态的答复协定由客户端指定。</span><span class="sxs-lookup"><span data-stu-id="f0c40-119">The reply contract to send order status is specified by the client.</span></span> <span data-ttu-id="f0c40-120">客户端实现订单状态协定。</span><span class="sxs-lookup"><span data-stu-id="f0c40-120">The client implements the order status contract.</span></span> <span data-ttu-id="f0c40-121">服务使用下面协定的生成的代理将订单状态发回客户端。</span><span class="sxs-lookup"><span data-stu-id="f0c40-121">The service uses the generated proxy of this contract to send order status back to the client.</span></span>  

```csharp
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```

 <span data-ttu-id="f0c40-122">服务操作处理提交的采购订单。</span><span class="sxs-lookup"><span data-stu-id="f0c40-122">The service operation processes the submitted purchase order.</span></span> <span data-ttu-id="f0c40-123">对服务操作应用 <xref:System.ServiceModel.OperationBehaviorAttribute> 以在用于从队列中接收消息的事务中指定自动登记，并指定在服务操作完成时事务自动完成。</span><span class="sxs-lookup"><span data-stu-id="f0c40-123">The <xref:System.ServiceModel.OperationBehaviorAttribute> is applied to the service operation to specify automatic enlistment in a transaction that is used to receive the message from the queue and automatic completion of transactions on completion of the service operation.</span></span> <span data-ttu-id="f0c40-124">`Orders` 类封装了订单处理功能。</span><span class="sxs-lookup"><span data-stu-id="f0c40-124">The `Orders` class encapsulates order processing functionality.</span></span> <span data-ttu-id="f0c40-125">在本例中，它将采购订单添加到字典。</span><span class="sxs-lookup"><span data-stu-id="f0c40-125">In this case, it adds the purchase order to a dictionary.</span></span> <span data-ttu-id="f0c40-126">`Orders` 类中的操作可以使用服务操作登记的事务。</span><span class="sxs-lookup"><span data-stu-id="f0c40-126">The transaction that the service operation enlisted in is available to the operations in the `Orders` class.</span></span>  
  
 <span data-ttu-id="f0c40-127">服务操作除了处理提交的采购订单之外，还向客户端答复有关订单状态的信息。</span><span class="sxs-lookup"><span data-stu-id="f0c40-127">The service operation, in addition to processing the submitted purchase order, replies back to the client on the status of the order.</span></span>  

```csharp
[OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
public void SubmitPurchaseOrder(PurchaseOrder po, string reportOrderStatusTo)  
{  
    Orders.Add(po);  
    Console.WriteLine("Processing {0} ", po);  
    Console.WriteLine("Sending back order status information");  
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding("ClientCallbackBinding");  
    OrderStatusClient client = new OrderStatusClient(msmqCallbackBinding, new EndpointAddress(reportOrderStatusTo));  
  
    // Please note that the same transaction that is used to dequeue the purchase order is used  
    // to send back order status.  
    using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
    {  
        client.OrderStatus(po.PONumber, po.Status);  
        scope.Complete();  
    }  
    //Close the client.  
    client.Close();  
}  
```

 <span data-ttu-id="f0c40-128">MSMQ 队列名称是在配置文件的 appSettings 节中指定的。</span><span class="sxs-lookup"><span data-stu-id="f0c40-128">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="f0c40-129">服务的终结点是在配置文件的 System.ServiceModel 节中定义的。</span><span class="sxs-lookup"><span data-stu-id="f0c40-129">The endpoint for the service is defined in the System.ServiceModel section of the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f0c40-130">MSMQ 队列名称和终结点地址使用略有不同的寻址约定。</span><span class="sxs-lookup"><span data-stu-id="f0c40-130">The MSMQ queue name and endpoint address use slightly different addressing conventions.</span></span> <span data-ttu-id="f0c40-131">MSMQ 队列名称为本地计算机使用圆点 (.)，并在其路径中使用反斜杠分隔符。</span><span class="sxs-lookup"><span data-stu-id="f0c40-131">The MSMQ queue name uses a dot (.) for the local machine and backslash separators in its path.</span></span> <span data-ttu-id="f0c40-132">Windows Communication Foundation （WCF）终结点地址指定一个 net.pipe：方案，使用本地计算机的 "localhost"，并在其路径中使用正斜杠。</span><span class="sxs-lookup"><span data-stu-id="f0c40-132">The Windows Communication Foundation (WCF) endpoint address specifies a net.msmq: scheme, uses "localhost" for the local machine, and uses forward slashes in its path.</span></span> <span data-ttu-id="f0c40-133">若要从在远程计算机上承载的队列读取数据，请将“.”和“localhost”替换为远程计算机名称。</span><span class="sxs-lookup"><span data-stu-id="f0c40-133">To read from a queue that is hosted on the remote machine, replace the "." and "localhost" to the remote machine name.</span></span>  
  
 <span data-ttu-id="f0c40-134">服务是自承载服务。</span><span class="sxs-lookup"><span data-stu-id="f0c40-134">The service is self hosted.</span></span> <span data-ttu-id="f0c40-135">使用 MSMQ 传输时，必须提前创建所使用的队列。</span><span class="sxs-lookup"><span data-stu-id="f0c40-135">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="f0c40-136">可以手动或通过代码完成此操作。</span><span class="sxs-lookup"><span data-stu-id="f0c40-136">This can be done manually or through code.</span></span> <span data-ttu-id="f0c40-137">在此示例中，该服务检查队列是否存在并在必要时创建队列。</span><span class="sxs-lookup"><span data-stu-id="f0c40-137">In this sample, the service checks for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="f0c40-138">从配置文件中读取队列名称。</span><span class="sxs-lookup"><span data-stu-id="f0c40-138">The queue name is read from the configuration file.</span></span> <span data-ttu-id="f0c40-139">基址[元数据实用工具（svcutil.exe）](../servicemodel-metadata-utility-tool-svcutil-exe.md)使用该基址来生成服务的代理。</span><span class="sxs-lookup"><span data-stu-id="f0c40-139">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from appSettings in configuration.  
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
    }  
}  
```

 <span data-ttu-id="f0c40-140">客户端创建事务。</span><span class="sxs-lookup"><span data-stu-id="f0c40-140">The client creates a transaction.</span></span> <span data-ttu-id="f0c40-141">与队列的通信在事务范围内进行，从而可以将事务范围视为所有消息在其中成功或失败的原子单元。</span><span class="sxs-lookup"><span data-stu-id="f0c40-141">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span>  

```csharp
// Create a ServiceHost for the OrderStatus service type.  
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderStatusService)))  
{  
  
    // Open the ServiceHostBase to create listeners and start listening for order status messages.  
    serviceHost.Open();  
  
    // Create the purchase order.  
    ...  
  
    // Create a client with given client endpoint configuration.  
    OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
    //Create a transaction scope.  
    using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
    {  
        string hostName = Dns.GetHostName();  
  
        // Make a queued call to submit the purchase order.  
        client.SubmitPurchaseOrder(po, "net.msmq://" + hostName + "/private/ServiceModelSamplesTwo-way/OrderStatus");  
  
        // Complete the transaction.  
        scope.Complete();  
    }  
  
    //Close down the client.  
    client.Close();  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
  
    // Close the ServiceHost to shutdown the service.  
    serviceHost.Close();  
}  
```

 <span data-ttu-id="f0c40-142">客户端代码实现 `IOrderStatus` 协定以便从服务接收订单状态。</span><span class="sxs-lookup"><span data-stu-id="f0c40-142">The client code implements the `IOrderStatus` contract to receive order status from the service.</span></span> <span data-ttu-id="f0c40-143">在本例中，它输出订单状态。</span><span class="sxs-lookup"><span data-stu-id="f0c40-143">In this case, it prints out the order status.</span></span>  

```csharp
[ServiceBehavior]  
public class OrderStatusService : IOrderStatus  
{  
    [OperationBehavior(TransactionAutoComplete = true,
                        TransactionScopeRequired = true)]  
    public void OrderStatus(string poNumber, string status)  
    {  
        Console.WriteLine("Status of order {0}:{1} ", poNumber ,
                                                           status);  
    }  
}  
```

 <span data-ttu-id="f0c40-144">订单状态队列在 `Main` 方法中创建。</span><span class="sxs-lookup"><span data-stu-id="f0c40-144">The order status queue is created in the `Main` method.</span></span> <span data-ttu-id="f0c40-145">客户端配置包括订单状态服务配置，以便承载订单状态服务，如下面的示例配置所示。</span><span class="sxs-lookup"><span data-stu-id="f0c40-145">The client configuration includes the order status service configuration to host the order status service, as shown in the following sample configuration.</span></span>  
  
```xml  
<appSettings>  
  <!-- Use appSetting to configure MSMQ queue name. -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderStatus" />  
</appSettings>  
  
<system.serviceModel>  
  
  <services>  
    <service
       name="Microsoft.ServiceModel.Samples.OrderStatusService">  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderStatus"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
    </service>  
  </services>  
  
  <client>  
    <!-- Define NetMsmqEndpoint -->  
    <endpoint name="OrderProcessorEndpoint"  
              address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"
              binding="netMsmqBinding"
              contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
  </client>  
  
</system.serviceModel>  
```  
  
 <span data-ttu-id="f0c40-146">运行示例时，客户端和服务活动将显示在服务和客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="f0c40-146">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="f0c40-147">您可以看到服务从客户端接收消息。</span><span class="sxs-lookup"><span data-stu-id="f0c40-147">You can see the service receive messages from the client.</span></span> <span data-ttu-id="f0c40-148">在每个控制台窗口中按 Enter 可以关闭服务和客户端。</span><span class="sxs-lookup"><span data-stu-id="f0c40-148">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="f0c40-149">服务显示采购订单信息并指示正在将订单状态发回订单状态队列。</span><span class="sxs-lookup"><span data-stu-id="f0c40-149">The service displays the purchase order information and indicates it is sending back the order status to the order status queue.</span></span>  
  
```console  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 124a1f69-3699-4b16-9bcc-43147a8756fc  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
  
Sending back order status information  
```  
  
 <span data-ttu-id="f0c40-150">客户端显示由服务发送的订单状态信息。</span><span class="sxs-lookup"><span data-stu-id="f0c40-150">The client displays the order status information sent by the service.</span></span>  
  
```console  
Press <ENTER> to terminate client.  
Status of order 124a1f69-3699-4b16-9bcc-43147a8756fc:Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f0c40-151">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="f0c40-151">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f0c40-152">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="f0c40-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="f0c40-153">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="f0c40-153">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="f0c40-154">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="f0c40-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f0c40-155">如果使用 Svcutil.exe 为该示例重新生成配置，请确保在客户端配置中修改终结点名称以与客户端代码匹配。</span><span class="sxs-lookup"><span data-stu-id="f0c40-155">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint names in the client configuration to match the client code.</span></span>  
  
 <span data-ttu-id="f0c40-156">默认情况下使用 <xref:System.ServiceModel.NetMsmqBinding> 启用传输安全。</span><span class="sxs-lookup"><span data-stu-id="f0c40-156">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="f0c40-157">MSMQ 传输安全性有两个相关的属性， <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` 默认情况下，身份验证模式设置为， `Windows` 保护级别设置为 `Sign` 。</span><span class="sxs-lookup"><span data-stu-id="f0c40-157">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="f0c40-158">为了使 MSMQ 提供身份验证和签名功能，MSMQ 必须是域的一部分，并且必须安装 MSMQ 的 Active Directory 集成选项。</span><span class="sxs-lookup"><span data-stu-id="f0c40-158">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="f0c40-159">如果在不满足这些条件的计算机上运行此示例，将会收到错误。</span><span class="sxs-lookup"><span data-stu-id="f0c40-159">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="f0c40-160">在加入到工作组或在没有 Active Directory 集成的计算机上运行示例</span><span class="sxs-lookup"><span data-stu-id="f0c40-160">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1. <span data-ttu-id="f0c40-161">如果计算机不是域成员或尚未安装 Active Directory 集成，请将身份验证模式和保护级别设置为 `None` 以关闭传输安全性，如下面的示例配置所示：</span><span class="sxs-lookup"><span data-stu-id="f0c40-161">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
    ```xml  
    <configuration>  
  
      <appSettings>  
        <!-- Use appSetting to configure MSMQ queue name. -->  
        <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderProcessor" />  
      </appSettings>  
  
      <system.serviceModel>  
        <services>  
          <service
              name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="TransactedBinding"
                      contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
          </service>  
        </services>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="TransactedBinding" >  
             <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
2. <span data-ttu-id="f0c40-162">关闭客户端配置的安全性将生成下面的内容：</span><span class="sxs-lookup"><span data-stu-id="f0c40-162">Turning off security for a client configuration generates the following:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <appSettings>  
        <!-- Use appSetting to configure MSMQ queue name. -->  
        <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderStatus" />  
      </appSettings>  
  
      <system.serviceModel>  
  
        <services>  
          <service
             name="Microsoft.ServiceModel.Samples.OrderStatusService">  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderStatus"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="TransactedBinding" contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
          </service>  
        </services>  
  
        <client>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint name="OrderProcessorEndpoint"  
                    address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"
                    binding="netMsmqBinding"
                    bindingConfiguration="TransactedBinding"  
                    contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
        </client>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="TransactedBinding" >  
             <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
3. <span data-ttu-id="f0c40-163">本示例中的服务在 `OrderProcessorService` 中创建一个绑定。</span><span class="sxs-lookup"><span data-stu-id="f0c40-163">The service for this sample creates a binding in the `OrderProcessorService`.</span></span> <span data-ttu-id="f0c40-164">实例化该绑定后添加一行代码以将安全模式设置为 `None`。</span><span class="sxs-lookup"><span data-stu-id="f0c40-164">Add a line of code after the binding is instantiated to set the security mode to `None`.</span></span>  
  
    ```csharp
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
    msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
    ```  
  
4. <span data-ttu-id="f0c40-165">确保在运行示例前更改服务器和客户端上的配置。</span><span class="sxs-lookup"><span data-stu-id="f0c40-165">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f0c40-166">将 `security mode` 设置为`None` 等效于将 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>、<xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> 或 `Message` 安全设置为 `None`。</span><span class="sxs-lookup"><span data-stu-id="f0c40-166">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> or `Message` security to `None`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f0c40-167">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="f0c40-167">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f0c40-168">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="f0c40-168">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f0c40-169">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="f0c40-169">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f0c40-170">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="f0c40-170">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Net\MSMQ\Two-Way`  

---
title: MSMQ 激活
ms.date: 03/30/2017
ms.assetid: e3834149-7b8c-4a54-806b-b4296720f31d
ms.openlocfilehash: 349eadb8f517993c343e81656204ad25e62ed931
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555232"
---
# <a name="msmq-activation"></a><span data-ttu-id="c7de3-102">MSMQ 激活</span><span class="sxs-lookup"><span data-stu-id="c7de3-102">MSMQ Activation</span></span>

<span data-ttu-id="c7de3-103">本示例演示如何在 Windows 进程激活服务 (WAS) 中承载从消息队列读取的应用程序。</span><span class="sxs-lookup"><span data-stu-id="c7de3-103">This sample demonstrates how to host applications in Windows Process Activation Service (WAS) that are read from a message queue.</span></span> <span data-ttu-id="c7de3-104">此示例使用 `netMsmqBinding` 和基于 [双向通信](two-way-communication.md) 示例。</span><span class="sxs-lookup"><span data-stu-id="c7de3-104">This sample uses the `netMsmqBinding` and is based on the [Two-Way Communication](two-way-communication.md) sample.</span></span> <span data-ttu-id="c7de3-105">本示例中的服务是一个 Web 承载的应用程序，而客户端是自承载的，并输出到控制台以观察提交的采购订单的状态。</span><span class="sxs-lookup"><span data-stu-id="c7de3-105">The service in this case is a Web-hosted application and the client is self-hosted and outputs to the console to observe the status of purchase orders submitted.</span></span>

> [!NOTE]
> <span data-ttu-id="c7de3-106">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="c7de3-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!NOTE]
> <span data-ttu-id="c7de3-107">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="c7de3-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c7de3-108">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="c7de3-108">Check for the following (default) directory before continuing.</span></span>
>
> <span data-ttu-id="c7de3-109">\<InstallDrive>： \ WF_WCF_Samples</span><span class="sxs-lookup"><span data-stu-id="c7de3-109">\<InstallDrive>:\WF_WCF_Samples</span></span>
>
> <span data-ttu-id="c7de3-110">如果此目录不存在，请跳到 [Windows Communication Foundation (WCF) ，并 Windows Workflow Foundation (的 WF) 示例](https://www.microsoft.com/download/details.aspx?id=21459) ，.NET Framework 4 下载所有 WCF 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="c7de3-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all WCF and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c7de3-111">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="c7de3-111">This sample is located in the following directory.</span></span>
>
> <span data-ttu-id="c7de3-112">\<InstallDrive>:\Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.</span><span class="sxs-lookup"><span data-stu-id="c7de3-112">\<InstallDrive>:\Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.</span></span>

<span data-ttu-id="c7de3-113">Windows 进程激活服务 (已) ，用于 Windows Server 2008 的新进程激活机制提供了类似 IIS 的功能，这些功能以前仅对使用非 HTTP 协议的应用程序可用的基于 HTTP 的应用程序可用。</span><span class="sxs-lookup"><span data-stu-id="c7de3-113">Windows Process Activation Service (WAS), the new process activation mechanism for Windows Server 2008, provides IIS-like features that were previously only available to HTTP-based applications to applications that use non-HTTP protocols.</span></span> <span data-ttu-id="c7de3-114">Windows Communication Foundation (WCF) 使用侦听器适配器接口传递通过 WCF 支持的非 HTTP 协议（如 TCP、命名管道和 MSMQ）接收的激活请求。</span><span class="sxs-lookup"><span data-stu-id="c7de3-114">Windows Communication Foundation (WCF) uses the Listener Adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by WCF, such as TCP, Named Pipes, and MSMQ.</span></span> <span data-ttu-id="c7de3-115">用于通过非 HTTP 协议接收请求的功能由 SMSvcHost.exe 中运行的托管 Windows 服务承载。</span><span class="sxs-lookup"><span data-stu-id="c7de3-115">The functionality for receiving requests over non-HTTP protocols is hosted by managed Windows services running in SMSvcHost.exe.</span></span>

<span data-ttu-id="c7de3-116">Net.Msmq Listener Adapter 服务 (NetMsmqActivator) 根据队列中的消息激活排队的应用程序。</span><span class="sxs-lookup"><span data-stu-id="c7de3-116">The Net.Msmq Listener Adapter service (NetMsmqActivator) activates queued applications based on messages in the queue.</span></span>

<span data-ttu-id="c7de3-117">客户端从事务范围内向服务发送采购订单。</span><span class="sxs-lookup"><span data-stu-id="c7de3-117">The client sends purchase orders to the service from within the scope of a transaction.</span></span> <span data-ttu-id="c7de3-118">服务在事务中接收订单并处理订单。</span><span class="sxs-lookup"><span data-stu-id="c7de3-118">The service receives the orders in a transaction and processes them.</span></span> <span data-ttu-id="c7de3-119">然后服务使用订单状态回调客户端。</span><span class="sxs-lookup"><span data-stu-id="c7de3-119">The service then calls back the client with the status of the order.</span></span> <span data-ttu-id="c7de3-120">为了便于双向通信，客户端和服务都使用队列以便将采购订单和订单状态排入队列。</span><span class="sxs-lookup"><span data-stu-id="c7de3-120">To facilitate two-way communication the client and service both use queues to enqueue purchase orders and order status.</span></span>

<span data-ttu-id="c7de3-121">服务协定 `IOrderProcessor` 定义使用队列的单向服务操作。</span><span class="sxs-lookup"><span data-stu-id="c7de3-121">The service contract `IOrderProcessor` defines the one-way service operations that work with queuing.</span></span> <span data-ttu-id="c7de3-122">服务操作使用答复终结点将订单状态发送到客户端。</span><span class="sxs-lookup"><span data-stu-id="c7de3-122">The service operation uses the reply endpoint to send order statuses to the client.</span></span> <span data-ttu-id="c7de3-123">答复终结点的地址是用于将订单状态发回客户端的队列的 URI。</span><span class="sxs-lookup"><span data-stu-id="c7de3-123">The reply endpoint's address is the URI of the queue used to send the order status back to the client.</span></span> <span data-ttu-id="c7de3-124">订单处理应用程序实现下面的协定。</span><span class="sxs-lookup"><span data-stu-id="c7de3-124">The order processing application implements this contract.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po,
                                           string reportOrderStatusTo);
}
```

<span data-ttu-id="c7de3-125">向其发送订单状态的答复协定由客户端指定。</span><span class="sxs-lookup"><span data-stu-id="c7de3-125">The reply contract to send order status to is specified by the client.</span></span> <span data-ttu-id="c7de3-126">客户端实现订单状态协定。</span><span class="sxs-lookup"><span data-stu-id="c7de3-126">The client implements the order status contract.</span></span> <span data-ttu-id="c7de3-127">服务使用下面协定的生成的客户端将订单状态发回客户端。</span><span class="sxs-lookup"><span data-stu-id="c7de3-127">The service uses the generated client of this contract to send order status back to the client.</span></span>

```csharp
[ServiceContract]
public interface IOrderStatus
{
    [OperationContract(IsOneWay = true)]
    void OrderStatus(string poNumber, string status);
}
```

<span data-ttu-id="c7de3-128">服务操作处理提交的采购订单。</span><span class="sxs-lookup"><span data-stu-id="c7de3-128">The service operation processes the submitted purchase order.</span></span> <span data-ttu-id="c7de3-129">对服务操作应用 <xref:System.ServiceModel.OperationBehaviorAttribute> 以在用于从队列中接收消息的事务中指定自动登记，并指定在服务操作完成时事务自动完成。</span><span class="sxs-lookup"><span data-stu-id="c7de3-129">The <xref:System.ServiceModel.OperationBehaviorAttribute> is applied to the service operation to specify automatic enlistment in the transaction that is used to receive the message from the queue and automatic completion of the transaction on completion of the service operation.</span></span> <span data-ttu-id="c7de3-130">`Orders` 类封装了订单处理功能。</span><span class="sxs-lookup"><span data-stu-id="c7de3-130">The `Orders` class encapsulates order processing functionality.</span></span> <span data-ttu-id="c7de3-131">在本例中，它将采购订单添加到字典。</span><span class="sxs-lookup"><span data-stu-id="c7de3-131">In this case, it adds the purchase order to a dictionary.</span></span> <span data-ttu-id="c7de3-132">`Orders` 类中的操作可以使用服务操作登记的事务。</span><span class="sxs-lookup"><span data-stu-id="c7de3-132">The transaction that the service operation enlisted in is available to the operations in the `Orders` class.</span></span>

<span data-ttu-id="c7de3-133">服务操作除了处理提交的采购订单之外，还向客户端答复有关订单状态的信息。</span><span class="sxs-lookup"><span data-stu-id="c7de3-133">The service operation, in addition to processing the submitted purchase order, replies back to the client about the status of the order.</span></span>

```csharp
public class OrderProcessorService : IOrderProcessor
{
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po, string reportOrderStatusTo)
    {
        Orders.Add(po);
        Console.WriteLine("Processing {0} ", po);
        Console.WriteLine("Sending back order status information");
        NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();
        msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;
        OrderStatusClient client = new OrderStatusClient(msmqCallbackBinding, new EndpointAddress(reportOrderStatusTo));
        // please note that the same transaction that is used to dequeue purchase order is used
        // to send back order status
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
        {
            client.OrderStatus(po.PONumber, po.Status);
            scope.Complete();
        }
    }
}
```

<span data-ttu-id="c7de3-134">要使用的客户端绑定是使用配置文件指定的。</span><span class="sxs-lookup"><span data-stu-id="c7de3-134">The client binding to use is specified using a configuration file.</span></span>

<span data-ttu-id="c7de3-135">MSMQ 队列名称是在配置文件的 appSettings 节中指定的。</span><span class="sxs-lookup"><span data-stu-id="c7de3-135">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="c7de3-136">服务的终结点是在配置文件的 System.serviceModel 节中定义的。</span><span class="sxs-lookup"><span data-stu-id="c7de3-136">The endpoint for the service is defined in the System.serviceModel section of the configuration file.</span></span>

> [!NOTE]
> <span data-ttu-id="c7de3-137">MSMQ 队列名称和终结点地址使用略有不同的寻址约定。</span><span class="sxs-lookup"><span data-stu-id="c7de3-137">The MSMQ queue name and endpoint address use slightly different addressing conventions.</span></span> <span data-ttu-id="c7de3-138">MSMQ 队列名称为本地计算机使用圆点 (.)，并在其路径中使用反斜杠分隔符。</span><span class="sxs-lookup"><span data-stu-id="c7de3-138">The MSMQ queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="c7de3-139">WCF 终结点地址指定一个 net.pipe：方案，使用本地计算机的 "localhost"，并在其路径中使用正斜杠。</span><span class="sxs-lookup"><span data-stu-id="c7de3-139">The WCF endpoint address specifies a net.msmq: scheme, uses "localhost" for the local computer, and uses forward slashes in its path.</span></span> <span data-ttu-id="c7de3-140">若要从在远程计算机上承载的队列读取数据，请将“.”和“localhost”替换为远程计算机名称。</span><span class="sxs-lookup"><span data-stu-id="c7de3-140">To read from a queue that is hosted on the remote computer, replace the "." and "localhost" to the remote computer name.</span></span>

<span data-ttu-id="c7de3-141">使用一个以类名作为名称的 .svc 文件来承载 WAS 中的服务代码。</span><span class="sxs-lookup"><span data-stu-id="c7de3-141">A .svc file with the name of the class is used to host the service code in WAS.</span></span>

<span data-ttu-id="c7de3-142">Service.svc 文件本身包含用于创建 `OrderProcessorService` 的指令。</span><span class="sxs-lookup"><span data-stu-id="c7de3-142">The Service.svc file itself contains a directive to create the `OrderProcessorService`.</span></span>

`<%@ServiceHost language="c#" Debug="true" Service="Microsoft.ServiceModel.Samples.OrderProcessorService"%>`

<span data-ttu-id="c7de3-143">Service.svc 文件还包含一个程序集指令以确保加载 System.Transactions.dll。</span><span class="sxs-lookup"><span data-stu-id="c7de3-143">The Service.svc file also contains an assembly directive to ensure that System.Transactions.dll is loaded.</span></span>

`<%@Assembly name="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"%>`

<span data-ttu-id="c7de3-144">客户端创建事务范围。</span><span class="sxs-lookup"><span data-stu-id="c7de3-144">The client creates a transaction scope.</span></span> <span data-ttu-id="c7de3-145">与服务的通信在事务范围内进行，从而可以将事务范围视为所有消息在其中成功或失败的原子单元。</span><span class="sxs-lookup"><span data-stu-id="c7de3-145">Communication with the service takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span> <span data-ttu-id="c7de3-146">通过在事务范围上调用 `Complete` 可以提交事务。</span><span class="sxs-lookup"><span data-stu-id="c7de3-146">The transaction is committed by calling `Complete` on the transaction scope.</span></span>

```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderStatusService)))
{
    // Open the ServiceHostBase to create listeners and start listening
    // for order status messages.
    serviceHost.Open();

    // Create a proxy with given client endpoint configuration
    OrderProcessorClient client = new OrderProcessorClient();

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
    using (TransactionScope scope = new
        TransactionScope(TransactionScopeOption.Required))
    {
        // Make a queued call to submit the purchase order
        client.SubmitPurchaseOrder(po,
       "net.msmq://localhost/private/ServiceModelSamplesOrder/OrderStatus");
        // Complete the transaction.
        scope.Complete();
    }

    //Closing the client gracefully closes the connection and cleans up
    //resources
    client.Close();

    Console.WriteLine();
    Console.WriteLine("Press <ENTER> to terminate client.");
    Console.ReadLine();

    // Close the ServiceHostBase to shutdown the service.
    serviceHost.Close();
    }
```

<span data-ttu-id="c7de3-147">客户端代码实现 `IOrderStatus` 协定以便从服务接收订单状态。</span><span class="sxs-lookup"><span data-stu-id="c7de3-147">The client code implements the `IOrderStatus` contract to receive order status from the service.</span></span> <span data-ttu-id="c7de3-148">在本例中，它输出订单状态。</span><span class="sxs-lookup"><span data-stu-id="c7de3-148">In this case, it prints out the order status.</span></span>

```csharp
[ServiceBehavior]
public class OrderStatusService : IOrderStatus
{
    [OperationBehavior(TransactionAutoComplete = true,
                        TransactionScopeRequired = true)]
    public void OrderStatus(string poNumber, string status)
    {
        Console.WriteLine("Status of order {0}:{1} ",
                                         poNumber , status);
    }
}
```

<span data-ttu-id="c7de3-149">订单状态队列在 `Main` 方法中创建。</span><span class="sxs-lookup"><span data-stu-id="c7de3-149">The order status queue is created in the `Main` method.</span></span> <span data-ttu-id="c7de3-150">客户端配置包括订单状态服务配置，以便承载订单状态服务，如下面的示例配置所示。</span><span class="sxs-lookup"><span data-stu-id="c7de3-150">The client configuration includes the order status service configuration to host the order status service, as shown in the following sample configuration.</span></span>

```xml
<appSettings>
    <!-- use appSetting to configure MSMQ queue name -->
    <add key="targetQueueName" value=".\private$\ServiceModelSamples/service.svc" />
    <add key="responseQueueName" value=".\private$\ServiceModelSamples/OrderStatus" />
  </appSettings>

<system.serviceModel>

    <services>
      <service
         name="Microsoft.ServiceModel.Samples.OrderStatusService">
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamples/OrderStatus"
                  binding="netMsmqBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderStatus" />
      </service>
    </services>

    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint name="OrderProcessorEndpoint"
                address="net.msmq://localhost/private/ServiceModelSamples/service.svc"
                binding="netMsmqBinding"
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
    </client>

  </system.serviceModel>
```

<span data-ttu-id="c7de3-151">运行示例时，客户端和服务活动将显示在服务器和客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="c7de3-151">When you run the sample, the client and service activities are displayed in both the server and client console windows.</span></span> <span data-ttu-id="c7de3-152">您可以看到服务器从客户端接收消息。</span><span class="sxs-lookup"><span data-stu-id="c7de3-152">You can see the server receive messages from the client.</span></span> <span data-ttu-id="c7de3-153">在每个控制台窗口中按 Enter 可以关闭服务器和客户端。</span><span class="sxs-lookup"><span data-stu-id="c7de3-153">Press ENTER in each console window to shut down the server and client.</span></span>

<span data-ttu-id="c7de3-154">客户端显示由服务器发送的订单状态信息：</span><span class="sxs-lookup"><span data-stu-id="c7de3-154">The client displays the order status information sent by the server:</span></span>

```console
Press <ENTER> to terminate client.
Status of order 70cf9d63-3dfa-4e69-81c2-23aa4478ebed :Pending
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c7de3-155">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="c7de3-155">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="c7de3-156">确保安装了 IIS 7.0，因为 WAS 激活所必需的。</span><span class="sxs-lookup"><span data-stu-id="c7de3-156">Ensure that IIS 7.0 is installed, as it is required for WAS activation.</span></span>

2. <span data-ttu-id="c7de3-157">确保已对 [Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="c7de3-157">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span> <span data-ttu-id="c7de3-158">此外，还必须安装 WCF 非 HTTP 激活组件：</span><span class="sxs-lookup"><span data-stu-id="c7de3-158">In addition, you must install the WCF non-HTTP activation components:</span></span>

    1. <span data-ttu-id="c7de3-159">从“开始”菜单中，选择“控制面板” 。</span><span class="sxs-lookup"><span data-stu-id="c7de3-159">From the **Start** menu, choose **Control Panel**.</span></span>

    2. <span data-ttu-id="c7de3-160">选择 " **程序和功能**"。</span><span class="sxs-lookup"><span data-stu-id="c7de3-160">Select **Programs and Features**.</span></span>

    3. <span data-ttu-id="c7de3-161">单击 **"打开或关闭 Windows 功能"**。</span><span class="sxs-lookup"><span data-stu-id="c7de3-161">Click **Turn Windows Features on or off**.</span></span>

    4. <span data-ttu-id="c7de3-162">在 " **功能摘要**" 下，单击 " **添加功能**"。</span><span class="sxs-lookup"><span data-stu-id="c7de3-162">Under **Features Summary**, click **Add Features**.</span></span>

    5. <span data-ttu-id="c7de3-163">展开 **Microsoft .NET Framework 3.0** 节点并检查 **Windows Communication Foundation 非 HTTP 激活** 功能。</span><span class="sxs-lookup"><span data-stu-id="c7de3-163">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>

3. <span data-ttu-id="c7de3-164">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="c7de3-164">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="c7de3-165">通过从命令窗口执行 client.exe 运行客户端。</span><span class="sxs-lookup"><span data-stu-id="c7de3-165">Run the client by executing client.exe from a command window.</span></span> <span data-ttu-id="c7de3-166">这将创建队列并向其发送消息。</span><span class="sxs-lookup"><span data-stu-id="c7de3-166">This creates the queue and sends a message to it.</span></span> <span data-ttu-id="c7de3-167">让客户端保持运行以观察服务读取消息的结果</span><span class="sxs-lookup"><span data-stu-id="c7de3-167">Leave the client running to see the result of the service reading the message</span></span>

5. <span data-ttu-id="c7de3-168">在默认情况下 MSMQ 激活服务将作为网络服务运行。</span><span class="sxs-lookup"><span data-stu-id="c7de3-168">The MSMQ activation service runs as Network Service by default.</span></span> <span data-ttu-id="c7de3-169">因此，用于激活应用程序的队列必须具有对网络服务的接收和查看权限。</span><span class="sxs-lookup"><span data-stu-id="c7de3-169">Therefore, the queue that is used to activate the application must have receive and peek permissions for Network Service.</span></span> <span data-ttu-id="c7de3-170">可以通过使用消息队列 MMC 来添加这些权限：</span><span class="sxs-lookup"><span data-stu-id="c7de3-170">This can be added by using the Message Queuing MMC:</span></span>

    1. <span data-ttu-id="c7de3-171">从 " **开始** " 菜单中，单击 " **运行**"，然后键入 `Compmgmt.msc` 并按 enter。</span><span class="sxs-lookup"><span data-stu-id="c7de3-171">From the **Start** menu, click **Run**, then type `Compmgmt.msc` and press ENTER.</span></span>

    2. <span data-ttu-id="c7de3-172">在 " **服务和应用程序**" 下，展开 " **消息队列**"。</span><span class="sxs-lookup"><span data-stu-id="c7de3-172">Under **Services and Applications**, expand **Message Queuing**.</span></span>

    3. <span data-ttu-id="c7de3-173">单击 " **专用队列**"。</span><span class="sxs-lookup"><span data-stu-id="c7de3-173">Click **Private Queues**.</span></span>

    4. <span data-ttu-id="c7de3-174">右键单击队列 (servicemodelsamples/node.js) 并选择 " **属性**"。</span><span class="sxs-lookup"><span data-stu-id="c7de3-174">Right-click the queue (servicemodelsamples/Service.svc) and choose **Properties**.</span></span>

    5. <span data-ttu-id="c7de3-175">在 " **安全** " 选项卡上，单击 " **添加** " 并向网络服务授予 "查看" 和 "接收" 权限。</span><span class="sxs-lookup"><span data-stu-id="c7de3-175">On the **Security** tab, click **Add** and give peek and receive permissions to Network Service.</span></span>

6. <span data-ttu-id="c7de3-176">将 Windows 进程激活服务 (WAS) 配置为支持 MSMQ 激活。</span><span class="sxs-lookup"><span data-stu-id="c7de3-176">Configure the Windows Process Activation Service (WAS) to support MSMQ activation.</span></span>

    <span data-ttu-id="c7de3-177">为方便起见，在位于示例目录中名为 AddMsmqSiteBinding.cmd 的批处理文件中实现以下步骤。</span><span class="sxs-lookup"><span data-stu-id="c7de3-177">As a convenience, the following steps are implemented in a batch file called AddMsmqSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="c7de3-178">若要支持 net.msmq 激活，必须首先将默认网站绑定到 net.msmq 协议。</span><span class="sxs-lookup"><span data-stu-id="c7de3-178">To support net.msmq activation, the default Web site must first be bound to the net.msmq protocol.</span></span> <span data-ttu-id="c7de3-179">可以通过使用随 IIS 7.0 管理工具集安装的 appcmd.exe 来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="c7de3-179">This can be done using appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="c7de3-180">在具有提升权限的（管理员）命令提示符处，运行下列命令。</span><span class="sxs-lookup"><span data-stu-id="c7de3-180">From an elevated (administrator) command prompt, run the following command.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        -+bindings.[protocol='net.msmq',bindingInformation='localhost']
        ```

        > [!NOTE]
        > <span data-ttu-id="c7de3-181">此命令是单行文本。</span><span class="sxs-lookup"><span data-stu-id="c7de3-181">This command is a single line of text.</span></span>

        <span data-ttu-id="c7de3-182">此命令可将 net.msmq 站点绑定添加到默认网站。</span><span class="sxs-lookup"><span data-stu-id="c7de3-182">This command adds a net.msmq site binding to the default Web site.</span></span>

    2. <span data-ttu-id="c7de3-183">尽管网站内的所有应用程序共享一个公共 net.msmq 绑定，但是每个应用程序可以单独启用 net.msmq 支持。</span><span class="sxs-lookup"><span data-stu-id="c7de3-183">Although all applications within a site share a common net.msmq binding, each application can enable net.msmq support individually.</span></span> <span data-ttu-id="c7de3-184">若要启用 /servicemodelsamples 应用程序的 net.msmq，请在具有提升权限的命令提示符处运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="c7de3-184">To enable net.msmq for the /servicemodelsamples application, run the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.msmq
        ```

        > [!NOTE]
        > <span data-ttu-id="c7de3-185">此命令是单行文本。</span><span class="sxs-lookup"><span data-stu-id="c7de3-185">This command is a single line of text.</span></span>

        <span data-ttu-id="c7de3-186">此命令允许使用和访问/servicemodelsamples 应用程序 `http://localhost/servicemodelsamples` `net.msmq://localhost/servicemodelsamples` 。</span><span class="sxs-lookup"><span data-stu-id="c7de3-186">This command enables the /servicemodelsamples application to be accessed using `http://localhost/servicemodelsamples` and `net.msmq://localhost/servicemodelsamples`.</span></span>

7. <span data-ttu-id="c7de3-187">如果您以前没有进行此操作，应确保启用 MSMQ 激活服务。</span><span class="sxs-lookup"><span data-stu-id="c7de3-187">If you have not done so previously, ensure that the MSMQ activation service is enabled.</span></span> <span data-ttu-id="c7de3-188">从 " **开始** " 菜单中，单击 " **运行**"，然后键入 `Services.msc` 。</span><span class="sxs-lookup"><span data-stu-id="c7de3-188">From the **Start** menu, click **Run**, and type `Services.msc`.</span></span> <span data-ttu-id="c7de3-189">在服务列表中搜索 **Net.tcp 侦听器适配器**。</span><span class="sxs-lookup"><span data-stu-id="c7de3-189">Search the list of services for the **Net.Msmq Listener Adapter**.</span></span> <span data-ttu-id="c7de3-190">右键单击并选择 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="c7de3-190">Right-click and select **Properties**.</span></span> <span data-ttu-id="c7de3-191">将 " **启动类型** " 设置为 " **自动**"，单击 " **应用** "，然后单击 " **开始** " 按钮。</span><span class="sxs-lookup"><span data-stu-id="c7de3-191">Set the **Startup Type** to **Automatic**, click **Apply** and click the **Start** button.</span></span> <span data-ttu-id="c7de3-192">此步骤只能在第一次使用 Net.Msmq Listener Adapter 服务之前操作一次。</span><span class="sxs-lookup"><span data-stu-id="c7de3-192">This step must only be done once prior to the first usage of the Net.Msmq Listener Adapter service.</span></span>

8. <span data-ttu-id="c7de3-193">若要以单机配置或跨计算机配置来运行示例，请按照 [运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="c7de3-193">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span> <span data-ttu-id="c7de3-194">此外，在客户端上更改用于提交采购订单的代码，使其在提交采购订单时在队列的 URI 中反映计算机名。</span><span class="sxs-lookup"><span data-stu-id="c7de3-194">Additionally, change the code on the client that submits the purchase order to reflect the computer name in the URI of the queue when submitting the purchase order.</span></span> <span data-ttu-id="c7de3-195">使用以下代码：</span><span class="sxs-lookup"><span data-stu-id="c7de3-195">Use the following code:</span></span>

    ```csharp
    client.SubmitPurchaseOrder(po, "net.msmq://localhost/private/ServiceModelSamples/OrderStatus");
    ```

9. <span data-ttu-id="c7de3-196">移除为此示例添加的 net.msmq 站点绑定。</span><span class="sxs-lookup"><span data-stu-id="c7de3-196">Remove the net.msmq site binding you added for this sample.</span></span>

    <span data-ttu-id="c7de3-197">为方便起见，在位于示例目录中名为 RemoveMsmqSiteBinding.cmd 的批处理文件中实现以下步骤：</span><span class="sxs-lookup"><span data-stu-id="c7de3-197">As a convenience, the following steps are implemented in a batch file called RemoveMsmqSiteBinding.cmd located in the sample directory:</span></span>

    1. <span data-ttu-id="c7de3-198">通过在具有提升权限的命令提示符处运行以下命令，从启用的协议列表中移除 net.msmq。</span><span class="sxs-lookup"><span data-stu-id="c7de3-198">Remove net.msmq from the list of enabled protocols by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="c7de3-199">此命令是单行文本。</span><span class="sxs-lookup"><span data-stu-id="c7de3-199">This command is a single line of text.</span></span>

    2. <span data-ttu-id="c7de3-200">通过在具有提升权限的命令提示符处运行以下命令移除 net.msmq 站点绑定。</span><span class="sxs-lookup"><span data-stu-id="c7de3-200">Remove the net.msmq site binding by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.msmq',bindingInformation='localhost']
        ```

        > [!NOTE]
        > <span data-ttu-id="c7de3-201">此命令是单行文本。</span><span class="sxs-lookup"><span data-stu-id="c7de3-201">This command is a single line of text.</span></span>

    > [!WARNING]
    > <span data-ttu-id="c7de3-202">运行该批处理文件会将 DefaultAppPool 重置为使用 .NET Framework 2.0 版运行。</span><span class="sxs-lookup"><span data-stu-id="c7de3-202">Running the batch file will reset the DefaultAppPool to run using .NET Framework version 2.0.</span></span>

<span data-ttu-id="c7de3-203">默认情况下对 `netMsmqBinding` 绑定传输启用了安全性。</span><span class="sxs-lookup"><span data-stu-id="c7de3-203">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="c7de3-204">`MsmqAuthenticationMode` 和 `MsmqProtectionLevel` 这两个属性共同确定了传输安全性的类型。</span><span class="sxs-lookup"><span data-stu-id="c7de3-204">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="c7de3-205">默认情况下，身份验证模式设置为 `Windows`，保护级别设置为 `Sign`。</span><span class="sxs-lookup"><span data-stu-id="c7de3-205">By default the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="c7de3-206">MSMQ 必须是域的成员才可以提供身份验证和签名功能。</span><span class="sxs-lookup"><span data-stu-id="c7de3-206">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="c7de3-207">如果在不是域成员的计算机上运行此示例，则会接收以下错误：“用户的内部消息队列证书不存在”。</span><span class="sxs-lookup"><span data-stu-id="c7de3-207">If you run this sample on a computer that is not part of a domain, the following error is received: "User's internal message queuing certificate does not exist".</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="c7de3-208">在加入到工作组的计算机上运行此示例</span><span class="sxs-lookup"><span data-stu-id="c7de3-208">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="c7de3-209">如果计算机不是域成员，请将身份验证模式和保护级别设置为 None 以禁用传输安全性，如下面的示例配置所示。</span><span class="sxs-lookup"><span data-stu-id="c7de3-209">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to none as shown in the following sample configuration.</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding configurationName="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

2. <span data-ttu-id="c7de3-210">在运行示例前更改服务和客户端上的配置。</span><span class="sxs-lookup"><span data-stu-id="c7de3-210">Change the configuration on both the server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c7de3-211">将 `security mode` 设置为 `None` 等效于将 `MsmqAuthenticationMode`、`MsmqProtectionLevel` 和 `Message` 安全设置为 `None`。</span><span class="sxs-lookup"><span data-stu-id="c7de3-211">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel` and `Message` security to `None`.</span></span>

3. <span data-ttu-id="c7de3-212">若要在加入到工作组的计算机上启用激活，必须使用特定用户帐户运行激活服务和辅助进程（两者使用的账户必须相同），并且队列必须具有该特定用户帐户的 ACL。</span><span class="sxs-lookup"><span data-stu-id="c7de3-212">To enable activation in a computer joined to a workgroup, both the activation service and the worker process must be run with a specific user account (must be same for both) and the queue must have ACLs for the specific user account.</span></span>

     <span data-ttu-id="c7de3-213">更改运行辅助进程所用的标识：</span><span class="sxs-lookup"><span data-stu-id="c7de3-213">To change the identity that the worker process runs under:</span></span>

    1. <span data-ttu-id="c7de3-214">运行 Inetmgr.exe。</span><span class="sxs-lookup"><span data-stu-id="c7de3-214">Run Inetmgr.exe.</span></span>

    2. <span data-ttu-id="c7de3-215">在 " **应用程序池**" 下，右键 \*\*单击 ") \*\* **DefaultAppPool** "，然后选择 " **设置应用程序池默认值 ...**" (。</span><span class="sxs-lookup"><span data-stu-id="c7de3-215">Under **Application Pools**, right-click the **AppPool** (typically **DefaultAppPool**) and choose **Set Application Pool Defaults…**.</span></span>

    3. <span data-ttu-id="c7de3-216">更改标识属性以使用特定用户帐户。</span><span class="sxs-lookup"><span data-stu-id="c7de3-216">Change the Identity properties to use the specific user account.</span></span>

     <span data-ttu-id="c7de3-217">更改运行激活服务所使用的标识：</span><span class="sxs-lookup"><span data-stu-id="c7de3-217">To change the identity that the Activation Service runs under:</span></span>

    1. <span data-ttu-id="c7de3-218">运行 Services.msc。</span><span class="sxs-lookup"><span data-stu-id="c7de3-218">Run Services.msc.</span></span>

    2. <span data-ttu-id="c7de3-219">右键单击 **Listener 适配器**，然后选择 " **属性**"。</span><span class="sxs-lookup"><span data-stu-id="c7de3-219">Right-click the **Net.MsmqListener Adapter**, and choose **Properties**.</span></span>

4. <span data-ttu-id="c7de3-220">更改 " **登录** " 选项卡中的帐户。</span><span class="sxs-lookup"><span data-stu-id="c7de3-220">Change the account in the **LogOn** tab.</span></span>

5. <span data-ttu-id="c7de3-221">在工作组中，服务还必须使用不受限制的令牌来运行。</span><span class="sxs-lookup"><span data-stu-id="c7de3-221">In workgroup, the service must also run using an unrestricted token.</span></span> <span data-ttu-id="c7de3-222">为此，请在命令窗口中运行下面的命令：</span><span class="sxs-lookup"><span data-stu-id="c7de3-222">To do this, run the following in a command window:</span></span>

    ```console
    sc sidtype netmsmqactivator unrestricted
    ```

## <a name="see-also"></a><span data-ttu-id="c7de3-223">请参阅</span><span class="sxs-lookup"><span data-stu-id="c7de3-223">See also</span></span>

- <span data-ttu-id="c7de3-224">[AppFabric 承载和持久性示例](/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="c7de3-224">[AppFabric Hosting and Persistence Samples](/previous-versions/appfabric/ff383418(v=azure.10))</span></span>

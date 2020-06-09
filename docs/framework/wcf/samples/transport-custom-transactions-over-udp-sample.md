---
title: 传输：UDP 示例上的自定义事务
ms.date: 03/30/2017
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
ms.openlocfilehash: ce1e6f0aedff46aaf58e22d8c23c37b03f8789dd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596534"
---
# <a name="transport-custom-transactions-over-udp-sample"></a><span data-ttu-id="5144d-102">传输：UDP 示例上的自定义事务</span><span class="sxs-lookup"><span data-stu-id="5144d-102">Transport: Custom Transactions over UDP Sample</span></span>
<span data-ttu-id="5144d-103">此示例基于 Windows Communication Foundation （WCF）[传输扩展性](transport-extensibility.md)中的[传输： UDP](transport-udp.md)示例。</span><span class="sxs-lookup"><span data-stu-id="5144d-103">This sample is based on the [Transport: UDP](transport-udp.md) sample in the Windows Communication Foundation (WCF)[Transport Extensibility](transport-extensibility.md).</span></span> <span data-ttu-id="5144d-104">它扩展 UDP 传输示例，以支持自定义事务流并演示 <xref:System.ServiceModel.Channels.TransactionMessageProperty> 属性的用法。</span><span class="sxs-lookup"><span data-stu-id="5144d-104">It extends the UDP Transport sample to support custom transaction flow and demonstrates the use of the <xref:System.ServiceModel.Channels.TransactionMessageProperty> property.</span></span>  
  
## <a name="code-changes-in-the-udp-transport-sample"></a><span data-ttu-id="5144d-105">UDP 传输示例中的代码更改</span><span class="sxs-lookup"><span data-stu-id="5144d-105">Code Changes in the UDP Transport Sample</span></span>  
 <span data-ttu-id="5144d-106">为了演示事务流，示例对 `ICalculatorContract` 的服务协定进行了更改，用于为 `CalculatorService.Add()` 设定一个事务范围。</span><span class="sxs-lookup"><span data-stu-id="5144d-106">To demonstrate transaction flow, the sample changes the service contract for `ICalculatorContract` to require a transaction scope for `CalculatorService.Add()`.</span></span> <span data-ttu-id="5144d-107">本示例还向 `System.Guid` 操作的协定另外添加了一个 `Add` 参数。</span><span class="sxs-lookup"><span data-stu-id="5144d-107">The sample also adds an extra `System.Guid` parameter to the contract of the `Add` operation.</span></span> <span data-ttu-id="5144d-108">此参数用于将客户端事务的标识符传递给服务。</span><span class="sxs-lookup"><span data-stu-id="5144d-108">This parameter is used to pass the identifier of the client transaction to the service.</span></span>  
  
```csharp  
class CalculatorService : IDatagramContract, ICalculatorContract  
{  
    [OperationBehavior(TransactionScopeRequired=true)]  
    public int Add(int x, int y, Guid clientTransactionId)  
    {  
        if(Transaction.Current.TransactionInformation.DistributedIdentifier == clientTransactionId)  
    {  
        Console.WriteLine("The client transaction has flowed to the service");  
    }  
    else  
    {  
     Console.WriteLine("The client transaction has NOT flowed to the service");  
    }  
  
    Console.WriteLine("   adding {0} + {1}", x, y);
    return (x + y);  
    }  
  
    [...]  
}  
```  
  
 <span data-ttu-id="5144d-109">[传输： udp](transport-udp.md)示例使用 udp 包在客户端和服务之间传递消息。</span><span class="sxs-lookup"><span data-stu-id="5144d-109">The [Transport: UDP](transport-udp.md) sample uses UDP packets to pass messages between a client and a service.</span></span> <span data-ttu-id="5144d-110">[传输：自定义传输示例](transport-custom-transactions-over-udp-sample.md)使用相同的机制传输消息，但当事务流动时，会将其插入 UDP 数据包以及编码的消息中。</span><span class="sxs-lookup"><span data-stu-id="5144d-110">The [Transport: Custom Transport Sample](transport-custom-transactions-over-udp-sample.md) uses the same mechanism to transport messages, but when a transaction is flowed, it is inserted into the UDP packet along with the encoded message.</span></span>  
  
```csharp  
byte[] txmsgBuffer = TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 <span data-ttu-id="5144d-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer` 是一个帮助器方法，包含用于将当前事务的传播程序令牌与消息实体合并，并将合并结果放入缓冲区中的新功能。</span><span class="sxs-lookup"><span data-stu-id="5144d-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer` is a helper method that contains new functionality to merge the propagation token for the current transaction with the message entity and place it into a buffer.</span></span>  
  
 <span data-ttu-id="5144d-112">对于自定义事务流传输，客户端实现必须知道哪些服务操作需要事务流，并将此信息传递给 WCF。</span><span class="sxs-lookup"><span data-stu-id="5144d-112">For custom transaction flow transport, the client implementation must know what service operations require transaction flow and to pass this information to WCF.</span></span> <span data-ttu-id="5144d-113">还应存在用于将用户事务传递到传输层的机制。</span><span class="sxs-lookup"><span data-stu-id="5144d-113">There should also be a mechanism for transmitting the user transaction to the transport layer.</span></span> <span data-ttu-id="5144d-114">此示例使用 "WCF 消息检查器" 获取此信息。</span><span class="sxs-lookup"><span data-stu-id="5144d-114">This sample uses "WCF message inspectors" to obtain this information.</span></span> <span data-ttu-id="5144d-115">此处实现的名为 `TransactionFlowInspector` 的客户端消息检查器执行下列任务：</span><span class="sxs-lookup"><span data-stu-id="5144d-115">The client message inspector implemented here, which is called `TransactionFlowInspector`, performs the following tasks:</span></span>  
  
- <span data-ttu-id="5144d-116">确定对于给定的消息操作，事务是否必须进行流处理（这发生在 `IsTxFlowRequiredForThisOperation()` 中）。</span><span class="sxs-lookup"><span data-stu-id="5144d-116">Determines whether a transaction must be flowed for a given message action (this takes place in `IsTxFlowRequiredForThisOperation()`).</span></span>  
  
- <span data-ttu-id="5144d-117">如果需要对事务进行流处理（这在 `TransactionFlowProperty` 中完成），则使用 `BeforeSendRequest()` 将当前环境事务附加到消息。</span><span class="sxs-lookup"><span data-stu-id="5144d-117">Attaches the current ambient transaction to the message using `TransactionFlowProperty`, if a transaction is required to be flowed (this is done in `BeforeSendRequest()`).</span></span>  
  
```csharp  
public class TransactionFlowInspector : IClientMessageInspector  
{  
   void IClientMessageInspector.AfterReceiveReply(ref           System.ServiceModel.Channels.Message reply, object correlationState)  
  {  
  }  
  
   public object BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
   {  
       // obtain the tx propagation token  
       byte[] propToken = null;
       if (Transaction.Current != null && IsTxFlowRequiredForThisOperation(request.Headers.Action))  
       {  
           try  
           {  
               propToken = TransactionInterop.GetTransmitterPropagationToken(Transaction.Current);  
           }  
           catch (TransactionException e)  
           {  
              throw new CommunicationException("TransactionInterop.GetTransmitterPropagationToken failed.", e);  
           }  
       }  
  
      // set the propToken on the message in a TransactionFlowProperty  
       TransactionFlowProperty.Set(propToken, request);  
  
       return null;
    }  
  }  
  
  static bool IsTxFlowRequiredForThisOperation(String action)  
 {  
       // In general, this should contain logic to identify which operations (actions)      require transaction flow.  
      [...]  
 }  
}  
```  
  
 <span data-ttu-id="5144d-118">使用自定义行为 `TransactionFlowInspector` 将 `TransactionFlowBehavior` 本身传递到框架。</span><span class="sxs-lookup"><span data-stu-id="5144d-118">The `TransactionFlowInspector` itself is passed to the framework using a custom behavior: the `TransactionFlowBehavior`.</span></span>  
  
```csharp  
public class TransactionFlowBehavior : IEndpointBehavior  
{  
       public void AddBindingParameters(ServiceEndpoint endpoint,            System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
      {  
      }  
  
       public void ApplyClientBehavior(ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.ClientRuntime clientRuntime)  
      {  
            TransactionFlowInspector inspector = new TransactionFlowInspector();  
            clientRuntime.MessageInspectors.Add(inspector);  
      }  
  
      public void ApplyDispatchBehavior(ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.EndpointDispatcher endpointDispatcher)  
     {  
     }  
  
      public void Validate(ServiceEndpoint endpoint)  
      {  
      }  
}  
```  
  
 <span data-ttu-id="5144d-119">根据前面的机制，用户代码在调用服务操作之前创建 `TransactionScope`。</span><span class="sxs-lookup"><span data-stu-id="5144d-119">With the preceding mechanism in place, the user code creates a `TransactionScope` before calling the service operation.</span></span> <span data-ttu-id="5144d-120">消息检查器确保将事务传递到传输，以防需要将事务流动到服务操作。</span><span class="sxs-lookup"><span data-stu-id="5144d-120">The message inspector ensures that the transaction is passed to the transport in case it is required to be flowed to the service operation.</span></span>  
  
```csharp  
CalculatorContractClient calculatorClient = new CalculatorContractClient("SampleProfileUdpBinding_ICalculatorContract");  
calculatorClient.Endpoint.Behaviors.Add(new TransactionFlowBehavior());
  
try  
{  
       for (int i = 0; i < 5; ++i)  
      {  
              // call the 'Add' service operation under a transaction scope  
             using (TransactionScope ts = new TransactionScope())  
             {  
        [...]  
        Console.WriteLine(calculatorClient.Add(i, i * 2));  
         }  
      }
       calculatorClient.Close();  
}  
catch (TimeoutException)  
{  
    calculatorClient.Abort();  
}  
catch (CommunicationException)  
{  
    calculatorClient.Abort();  
}  
catch (Exception)  
{  
    calculatorClient.Abort();  
    throw;  
}  
```  
  
 <span data-ttu-id="5144d-121">从客户端接收 UDP 数据包时，服务可对数据包进行反序列化，从而提取消息和可能存在的事务。</span><span class="sxs-lookup"><span data-stu-id="5144d-121">Upon receiving a UDP packet from the client, the service deserializes it to extract the message and possibly a transaction.</span></span>  
  
```csharp  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 <span data-ttu-id="5144d-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` 是用于反转 `TransactionMessageBuffer.WriteTransactionMessageBuffer()` 执行的序列化过程的帮助器方法。</span><span class="sxs-lookup"><span data-stu-id="5144d-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` is the helper method that reverses the serialization process performed by `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span></span>  
  
 <span data-ttu-id="5144d-123">如果事务已流入，它会通过 `TransactionMessageProperty` 追加到消息。</span><span class="sxs-lookup"><span data-stu-id="5144d-123">If a transaction was flowed in, it is appended to the message in the `TransactionMessageProperty`.</span></span>  
  
```csharp  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 <span data-ttu-id="5144d-124">这可以确保调度程序在调度时选择事务，并在调用由消息处理的服务操作时使用该事务。</span><span class="sxs-lookup"><span data-stu-id="5144d-124">This ensures that the dispatcher picks up the transaction at dispatch time and uses it when calling the service operation addressed by the message.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5144d-125">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="5144d-125">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5144d-126">若要生成解决方案，请按照[生成 Windows Communication Foundation 示例](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="5144d-126">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="5144d-127">当前示例的运行方式与[传输： UDP](transport-udp.md)示例类似。</span><span class="sxs-lookup"><span data-stu-id="5144d-127">The current sample should be run similarly to the [Transport: UDP](transport-udp.md) sample.</span></span> <span data-ttu-id="5144d-128">若要运行该示例，请使用 UdpTestService.exe 启动服务。</span><span class="sxs-lookup"><span data-stu-id="5144d-128">To run it, start the service with UdpTestService.exe.</span></span> <span data-ttu-id="5144d-129">如果运行的是 Windows Vista，则必须以提升的权限启动该服务。</span><span class="sxs-lookup"><span data-stu-id="5144d-129">If you are running Windows Vista, you must start the service with elevated privileges.</span></span> <span data-ttu-id="5144d-130">为此，请在文件资源管理器中右键单击 Udptestservice.exe，然后单击 "以**管理员身份运行**"。</span><span class="sxs-lookup"><span data-stu-id="5144d-130">To do so, right-click UdpTestService.exe in File Explorer and click **Run as administrator**.</span></span>  
  
3. <span data-ttu-id="5144d-131">将生成以下输出。</span><span class="sxs-lookup"><span data-stu-id="5144d-131">This produces the following output.</span></span>  
  
    ```console  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4. <span data-ttu-id="5144d-132">此时可以通过运行 UdpTestClient.exe 启动客户端。</span><span class="sxs-lookup"><span data-stu-id="5144d-132">At this time, you can start the client by running UdpTestClient.exe.</span></span> <span data-ttu-id="5144d-133">客户端生成的输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="5144d-133">The output produced by the client is as follows.</span></span>  
  
    ```console
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5. <span data-ttu-id="5144d-134">服务输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="5144d-134">The service output is as follows.</span></span>  
  
    ```console
    Hello, world!  
    Hello, world!  
    Hello, world!  
    Hello, world!  
    Hello, world!  
    The client transaction has flowed to the service  
       adding 0 + 0  
    The client transaction has flowed to the service  
       adding 1 + 2  
    The client transaction has flowed to the service  
       adding 2 + 4  
    The client transaction has flowed to the service  
       adding 3 + 6  
    The client transaction has flowed to the service  
       adding 4 + 8  
    ```  
  
6. <span data-ttu-id="5144d-135">如果服务应用程序可以将 `The client transaction has flowed to the service` 操作的 `clientTransactionId` 参数中的客户端发送的事务标识符与服务事务的标识符进行匹配，则服务应用程序会显示消息 `CalculatorService.Add()`。</span><span class="sxs-lookup"><span data-stu-id="5144d-135">The service application displays the message `The client transaction has flowed to the service` if it can match the transaction identifier sent by the client, in the `clientTransactionId` parameter of the `CalculatorService.Add()` operation, to the identifier of the service transaction.</span></span> <span data-ttu-id="5144d-136">仅当客户端事务已经流动到服务时才可以获得匹配。</span><span class="sxs-lookup"><span data-stu-id="5144d-136">A match is obtained only if the client transaction has flowed to the service.</span></span>  
  
7. <span data-ttu-id="5144d-137">若要对使用配置发布的终结点运行客户端应用程序，请在服务应用程序窗口中按 Enter，并再次运行测试客户端。</span><span class="sxs-lookup"><span data-stu-id="5144d-137">To run the client application against endpoints published using configuration, press ENTER on the service application window and then run the test client again.</span></span> <span data-ttu-id="5144d-138">您将在服务上看到如下输出。</span><span class="sxs-lookup"><span data-stu-id="5144d-138">You should see the following output on the service.</span></span>  
  
    ```console  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8. <span data-ttu-id="5144d-139">现在对服务运行客户端将产生与前面相似的输出。</span><span class="sxs-lookup"><span data-stu-id="5144d-139">Running the client against the service now produces similar output as before.</span></span>  
  
9. <span data-ttu-id="5144d-140">若要使用 Svcutil.exe 重新生成客户端代码和配置，请启动服务应用程序，然后从示例的根目录中运行下面的 Svcutil.exe 命令。</span><span class="sxs-lookup"><span data-stu-id="5144d-140">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe command from the root directory of the sample.</span></span>  
  
    ```console  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. <span data-ttu-id="5144d-141">注意，Svcutil.exe 不会为 `sampleProfileUdpBinding` 生成绑定扩展配置；必须手动添加它。</span><span class="sxs-lookup"><span data-stu-id="5144d-141">Note that Svcutil.exe does not generate the binding extension configuration for the `sampleProfileUdpBinding`; you must add it manually.</span></span>  
  
    ```xml  
    <configuration>  
        <system.serviceModel>
            …  
            <extensions>  
                <!-- This was added manually because svcutil.exe does not add this extension to the file -->  
                <bindingExtensions>  
                    <add name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
                </bindingExtensions>  
            </extensions>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
> [!IMPORTANT]
> <span data-ttu-id="5144d-142">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="5144d-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5144d-143">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="5144d-143">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5144d-144">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="5144d-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5144d-145">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="5144d-145">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a><span data-ttu-id="5144d-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5144d-146">See also</span></span>

- [<span data-ttu-id="5144d-147">传输：UDP</span><span class="sxs-lookup"><span data-stu-id="5144d-147">Transport: UDP</span></span>](transport-udp.md)

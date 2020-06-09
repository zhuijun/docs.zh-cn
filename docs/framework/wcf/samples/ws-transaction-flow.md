---
title: WS 事务流
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: 1fbde53289c147d8ea273b9c86e65cbb8e262b30
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596405"
---
# <a name="ws-transaction-flow"></a><span data-ttu-id="8452e-102">WS 事务流</span><span class="sxs-lookup"><span data-stu-id="8452e-102">WS Transaction Flow</span></span>
<span data-ttu-id="8452e-103">本示例演示客户端协调事务和使用 WS-Atomic 事务或 OleTransactions 协议的事务流的客户端和服务器选项的用法。</span><span class="sxs-lookup"><span data-stu-id="8452e-103">This sample demonstrates the use of a client-coordinated transaction and the client and server options for transaction flow using either the WS-Atomic Transaction or OleTransactions protocol.</span></span> <span data-ttu-id="8452e-104">此示例基于实现计算器服务的[入门](getting-started-sample.md)，但操作的作用是为了说明如何使用 `TransactionFlowAttribute` **TransactionFlowOption**枚举来确定启用了事务流的程度。</span><span class="sxs-lookup"><span data-stu-id="8452e-104">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service but the operations are attributed to demonstrate the use of the `TransactionFlowAttribute` with the **TransactionFlowOption** enumeration to determine to what degree transaction flow is enabled.</span></span> <span data-ttu-id="8452e-105">在流事务范围内，请求操作的日志将写入数据库并保存，直到客户端协调事务完成。如果客户端事务没有完成，则 Web 服务事务确保不提交对数据库的相应更新。</span><span class="sxs-lookup"><span data-stu-id="8452e-105">Within the scope of the flowed transaction, a log of the requested operations is written to a database and persists until the client coordinated transaction has completed - if the client transaction does not complete, the Web service transaction ensures that the appropriate updates to the database are not committed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8452e-106">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="8452e-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="8452e-107">初始化到服务的连接和事务后，客户端访问多个服务操作。</span><span class="sxs-lookup"><span data-stu-id="8452e-107">After initiating a connection to the service and a transaction, the client accesses several service operations.</span></span> <span data-ttu-id="8452e-108">用于服务的协定定义如下，每个操作演示 `TransactionFlowOption` 的一种不同的设置。</span><span class="sxs-lookup"><span data-stu-id="8452e-108">The contract for the service is defined as follows with each of the operations demonstrating a different setting for the `TransactionFlowOption`.</span></span>  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Add(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Allowed)]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.NotAllowed)]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);
}  
```

 <span data-ttu-id="8452e-109">这按处理操作的顺序定义这些操作：</span><span class="sxs-lookup"><span data-stu-id="8452e-109">This defines the operations in the order they are to be processed:</span></span>  
  
- <span data-ttu-id="8452e-110">`Add` 操作请求必须包括流事务。</span><span class="sxs-lookup"><span data-stu-id="8452e-110">An `Add` operation request must include a flowed transaction.</span></span>  
  
- <span data-ttu-id="8452e-111">`Subtract` 操作请求可能包括流事务。</span><span class="sxs-lookup"><span data-stu-id="8452e-111">A `Subtract` operation request may include a flowed transaction.</span></span>  
  
- <span data-ttu-id="8452e-112">由于显式 NotAllowed 设置，`Multiply` 操作请求不得包括流事务。</span><span class="sxs-lookup"><span data-stu-id="8452e-112">A `Multiply` operation request must not include a flowed transaction through the explicit NotAllowed setting.</span></span>  
  
- <span data-ttu-id="8452e-113">由于省略 `Divide` 属性，`TransactionFlow` 操作请求不得包括流事务。</span><span class="sxs-lookup"><span data-stu-id="8452e-113">A `Divide` operation request must not include a flowed transaction through the omission of a `TransactionFlow` attribute.</span></span>  
  
 <span data-ttu-id="8452e-114">若要启用事务流， [\<transactionFlow>](../../configure-apps/file-schema/wcf/transactionflow.md) 必须使用启用了属性的绑定，以及相应的操作属性。</span><span class="sxs-lookup"><span data-stu-id="8452e-114">To enable transaction flow, bindings with the [\<transactionFlow>](../../configure-apps/file-schema/wcf/transactionflow.md) property enabled must be used in addition to the appropriate operation attributes.</span></span> <span data-ttu-id="8452e-115">在本示例中，除了元数据交换终结点以外，服务的配置还公开 TCP 终结点和 HTTP 终结点。</span><span class="sxs-lookup"><span data-stu-id="8452e-115">In this sample, the service's configuration exposes a TCP endpoint and an HTTP endpoint in addition to a Metadata Exchange endpoint.</span></span> <span data-ttu-id="8452e-116">TCP 终结点和 HTTP 终结点使用以下绑定，两者都 [\<transactionFlow>](../../configure-apps/file-schema/wcf/transactionflow.md) 启用了属性。</span><span class="sxs-lookup"><span data-stu-id="8452e-116">The TCP endpoint and the HTTP endpoint use the following bindings, both of which have the [\<transactionFlow>](../../configure-apps/file-schema/wcf/transactionflow.md) property enabled.</span></span>  
  
```xml  
<bindings>  
  <netTcpBinding>  
    <binding name="transactionalOleTransactionsTcpBinding"  
             transactionFlow="true"  
             transactionProtocol="OleTransactions"/>  
  </netTcpBinding>  
  <wsHttpBinding>  
    <binding name="transactionalWsatHttpBinding"  
             transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
> [!NOTE]
> <span data-ttu-id="8452e-117">系统提供的 netTcpBinding 允许使用 transactionProtocol 的规范，而系统提供的 wsHttpBinding 仅使用互操作性更强的 WSAtomicTransactionOctober2004 协议。</span><span class="sxs-lookup"><span data-stu-id="8452e-117">The system-provided netTcpBinding allows specification of the transactionProtocol whereas the system-provided wsHttpBinding uses only the more interoperable WSAtomicTransactionOctober2004 protocol.</span></span> <span data-ttu-id="8452e-118">OleTransactions 协议仅可供 Windows Communication Foundation （WCF）客户端使用。</span><span class="sxs-lookup"><span data-stu-id="8452e-118">The OleTransactions protocol is only available for use by Windows Communication Foundation (WCF) clients.</span></span>  
  
 <span data-ttu-id="8452e-119">对于实现 `ICalculator` 接口的类，所有方法的 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 属性都设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="8452e-119">For the class that implements the `ICalculator` interface, all of the methods are attributed with <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property set to `true`.</span></span> <span data-ttu-id="8452e-120">此设置声明在方法内采取的所有操作都在事务范围内发生。</span><span class="sxs-lookup"><span data-stu-id="8452e-120">This setting declares that all actions taken within the method occur within the scope of a transaction.</span></span> <span data-ttu-id="8452e-121">在本例中，采取的操作包括记录到日志数据库。</span><span class="sxs-lookup"><span data-stu-id="8452e-121">In this case, the actions taken include recording to the log database.</span></span> <span data-ttu-id="8452e-122">如果操作请求包括流事务，则操作发生在传入事务的范围内或自动生成新事务范围。</span><span class="sxs-lookup"><span data-stu-id="8452e-122">If the operation request includes a flowed transaction then the actions occur within the scope of the incoming transaction or a new transaction scope is automatically generated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8452e-123"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 属性定义服务方法实现的本地行为，不定义客户端对事务进行流处理的能力或需求。</span><span class="sxs-lookup"><span data-stu-id="8452e-123">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property defines behavior local to the service method implementations and does not define the client's ability to or requirement for flowing a transaction.</span></span>  

```csharp
// Service class that implements the service contract.  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Add(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Adding {0} to {1}", n1, n2));  
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Subtract(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Subtracting {0} from {1}", n2, n1));  
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Multiply(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Multiplying {0} by {1}", n1, n2));  
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Divide(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Dividing {0} by {1}", n1, n2));  
        return n1 / n2;  
    }  
  
    // Logging method omitted for brevity  
}  
```

 <span data-ttu-id="8452e-124">在客户端，针对操作的服务的 `TransactionFlowOption` 设置反映在客户端 `ICalculator` 接口的生成的定义中。</span><span class="sxs-lookup"><span data-stu-id="8452e-124">On the client, the service's `TransactionFlowOption` settings on the operations are reflected in the client's generated definition of the `ICalculator` interface.</span></span> <span data-ttu-id="8452e-125">而且服务的 `transactionFlow` 属性设置也反映在客户端的应用程序配置中。</span><span class="sxs-lookup"><span data-stu-id="8452e-125">Also, the service's `transactionFlow` property settings are reflected in the client's application configuration.</span></span> <span data-ttu-id="8452e-126">通过选择适当的 `endpointConfigurationName`，客户端可以选择传输和协议。</span><span class="sxs-lookup"><span data-stu-id="8452e-126">The client can select the transport and protocol by selecting the appropriate `endpointConfigurationName`.</span></span>  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
> <span data-ttu-id="8452e-127">无论选择哪种协议或传输，观察到的本示例的行为都是相同的。</span><span class="sxs-lookup"><span data-stu-id="8452e-127">The observed behavior of this sample is the same no matter which protocol or transport is chosen.</span></span>  
  
 <span data-ttu-id="8452e-128">启动到服务的连接后，客户端在对服务操作的调用附近创建新的 `TransactionScope`。</span><span class="sxs-lookup"><span data-stu-id="8452e-128">Having initiated the connection to the service, the client creates a new `TransactionScope` around the calls to the service operations.</span></span>  

```csharp
// Start a transaction scope  
using (TransactionScope tx =  
            new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    Console.WriteLine("Starting transaction");  
  
    // Call the Add service operation  
    //  - generatedClient will flow the required active transaction  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client.Add(value1, value2);  
    Console.WriteLine("  Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation  
    //  - generatedClient will flow the allowed active transaction  
    value1 = 145.00D;  
    value2 = 76.54D;  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Start a transaction scope that suppresses the current transaction  
    using (TransactionScope txSuppress =  
                new TransactionScope(TransactionScopeOption.Suppress))  
    {  
        // Call the Subtract service operation  
        //  - the active transaction is suppressed from the generatedClient  
        //    and no transaction will flow  
        value1 = 21.05D;  
        value2 = 42.16D;  
        result = client.Subtract(value1, value2);  
        Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
        // Complete the suppressed scope  
        txSuppress.Complete();  
    }  
  
    // Call the Multiply service operation  
    // - generatedClient will not flow the active transaction  
    value1 = 9.00D;  
    value2 = 81.25D;  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("  Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    // - generatedClient will not flow the active transaction  
    value1 = 22.00D;  
    value2 = 7.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("  Divide({0},{1}) = {2}", value1, value2, result);  
  
    // Complete the transaction scope  
    Console.WriteLine("  Completing transaction");  
    tx.Complete();  
}  
  
Console.WriteLine("Transaction committed");  
```

 <span data-ttu-id="8452e-129">对操作的调用如下：</span><span class="sxs-lookup"><span data-stu-id="8452e-129">The calls to the operations are as follows:</span></span>  
  
- <span data-ttu-id="8452e-130">`Add` 请求将必需的事务流动到服务，服务的操作在客户端的事务范围内发生。</span><span class="sxs-lookup"><span data-stu-id="8452e-130">The `Add` request flows the required transaction to the service and the service's actions occur within the scope of the client's transaction.</span></span>  
  
- <span data-ttu-id="8452e-131">第一个 `Subtract` 请求也将允许的事务流动到服务，服务的操作再次在客户端的事务范围内发生。</span><span class="sxs-lookup"><span data-stu-id="8452e-131">The first `Subtract` request also flows the allowed transaction to the service and again the service's actions occur within the scope of the client's transaction.</span></span>  
  
- <span data-ttu-id="8452e-132">第二个 `Subtract` 请求在用 `TransactionScopeOption.Suppress` 选项声明的新事务范围内执行。</span><span class="sxs-lookup"><span data-stu-id="8452e-132">The second `Subtract` request is performed within a new transaction scope declared with the `TransactionScopeOption.Suppress` option.</span></span> <span data-ttu-id="8452e-133">这会禁止客户端的初始外层事务，请求不会将事务流动到服务。</span><span class="sxs-lookup"><span data-stu-id="8452e-133">This suppresses the client's initial outer transaction and the request does not flow a transaction to the service.</span></span> <span data-ttu-id="8452e-134">此方法允许客户端显式放弃和防止将事务流动到服务（不需要流动时）。</span><span class="sxs-lookup"><span data-stu-id="8452e-134">This approach allows a client to explicitly opt-out of and protect against flowing a transaction to a service when that is not required.</span></span> <span data-ttu-id="8452e-135">服务的操作发生在新的未连接的事务范围内。</span><span class="sxs-lookup"><span data-stu-id="8452e-135">The service's actions occur within the scope of a new and unconnected transaction.</span></span>  
  
- <span data-ttu-id="8452e-136">`Multiply` 请求不会将事务流动到服务，因为客户端的生成的 `ICalculator` 接口定义包括设置为 <xref:System.ServiceModel.TransactionFlowAttribute><xref:System.ServiceModel.TransactionFlowOption> 的 `NotAllowed`。</span><span class="sxs-lookup"><span data-stu-id="8452e-136">The `Multiply` request does not flow a transaction to the service because the client's generated definition of the `ICalculator` interface includes a <xref:System.ServiceModel.TransactionFlowAttribute> set to <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`.</span></span>  
  
- <span data-ttu-id="8452e-137">`Divide` 请求不会将事务流动到服务，因为客户端的 `ICalculator` 接口生成的定义再次没有包括 `TransactionFlowAttribute`。</span><span class="sxs-lookup"><span data-stu-id="8452e-137">The `Divide` request does not flow a transaction to the service because again the client's generated definition of the `ICalculator` interface does not include a `TransactionFlowAttribute`.</span></span> <span data-ttu-id="8452e-138">服务的操作再次发生在另一个新的未连接的事务范围内。</span><span class="sxs-lookup"><span data-stu-id="8452e-138">The service's actions again occur within the scope of another new and unconnected transaction.</span></span>  
  
 <span data-ttu-id="8452e-139">运行示例时，操作请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="8452e-139">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="8452e-140">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="8452e-140">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Starting transaction  
  Add(100,15.99) = 115.99  
  Subtract(145,76.54) = 68.46  
  Subtract(21.05,42.16) = -21.11  
  Multiply(9,81.25) = 731.25  
  Divide(22,7) = 3.14285714285714  
  Completing transaction  
Transaction committed  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="8452e-141">服务操作请求的日志记录显示在服务的控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="8452e-141">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="8452e-142">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="8452e-142">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 <span data-ttu-id="8452e-143">成功执行示例后，客户端的事务范围完成并提交在该范围内采取的所有操作。</span><span class="sxs-lookup"><span data-stu-id="8452e-143">After a successful execution, the client's transaction scope completes and all actions taken within that scope are committed.</span></span> <span data-ttu-id="8452e-144">特别是，上面提到的 5 个记录保留在服务的数据库中。</span><span class="sxs-lookup"><span data-stu-id="8452e-144">Specifically, the noted 5 records are persisted in the service's database.</span></span> <span data-ttu-id="8452e-145">其中的前 2 个记录已在客户端的事务范围内发生。</span><span class="sxs-lookup"><span data-stu-id="8452e-145">The first 2 of these have occurred within the scope of the client's transaction.</span></span>  
  
 <span data-ttu-id="8452e-146">如果在客户端的 `TransactionScope` 内的任意位置发生异常，则事务无法完成。</span><span class="sxs-lookup"><span data-stu-id="8452e-146">If an exception occurred anywhere within the client's `TransactionScope` then the transaction cannot complete.</span></span> <span data-ttu-id="8452e-147">这将导致在该范围内写入日志的记录不会被提交到数据库。</span><span class="sxs-lookup"><span data-stu-id="8452e-147">This causes the records logged within that scope to not be committed to the database.</span></span> <span data-ttu-id="8452e-148">注释掉完成外层 `TransactionScope` 的调用后重复运行该示例可以观察到此效果。</span><span class="sxs-lookup"><span data-stu-id="8452e-148">This effect can be observed by repeating the sample run after commenting out the call to complete the outer `TransactionScope`.</span></span> <span data-ttu-id="8452e-149">当如此运行时，只记录后 3 个操作（来自第二个 `Subtract`、`Multiply` 和 `Divide` 请求），因为客户端事务不流到这些操作。</span><span class="sxs-lookup"><span data-stu-id="8452e-149">On such a run, only the last 3 actions (from the second `Subtract`, the `Multiply` and the `Divide` requests) are logged because the client transaction did not flow to those.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8452e-150">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="8452e-150">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8452e-151">若要生成 c # 或 Visual Basic .NET 版本的解决方案，请按照[生成 Windows Communication Foundation 示例](building-the-samples.md)中的说明进行操作</span><span class="sxs-lookup"><span data-stu-id="8452e-151">To build the C# or Visual Basic .NET version of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md)</span></span>  
  
2. <span data-ttu-id="8452e-152">确保已安装 SQL Server Express Edition 或 SQL Server，并确保已在服务的应用程序配置文件中正确设置连接字符串。</span><span class="sxs-lookup"><span data-stu-id="8452e-152">Ensure that you have installed SQL Server Express Edition or SQL Server, and that the connection string has been correctly set in the service’s application configuration file.</span></span> <span data-ttu-id="8452e-153">若要在不使用数据库的情况下运行示例，请将服务的应用程序配置文件中的 `usingSql` 值设置为 `false`</span><span class="sxs-lookup"><span data-stu-id="8452e-153">To run the sample without using a database, set the `usingSql` value in the service’s application configuration file to `false`</span></span>  
  
3. <span data-ttu-id="8452e-154">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="8452e-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8452e-155">对于跨计算机配置，请按照下面的说明操作来启用分布式事务处理协调器，并使用 Windows SDK 中的 WsatConfig.exe 工具来启用 WCF 事务网络支持。</span><span class="sxs-lookup"><span data-stu-id="8452e-155">For cross-machine configuration, enable the Distributed Transaction Coordinator using the instructions below, and use the WsatConfig.exe tool from the Windows SDK to enable WCF Transactions network support.</span></span> <span data-ttu-id="8452e-156">有关设置 Wsatconfig.exe 的信息，请参阅[配置 WS 原子事务支持](../feature-details/configuring-ws-atomic-transaction-support.md)。</span><span class="sxs-lookup"><span data-stu-id="8452e-156">For information on setting up WsatConfig.exe, see [Configuring WS-Atomic Transaction Support](../feature-details/configuring-ws-atomic-transaction-support.md).</span></span>  
  
 <span data-ttu-id="8452e-157">无论是在同一台计算机上还是在不同的计算机上运行此示例，都必须配置 Microsoft 分布式事务处理协调器（MSDTC）以启用网络事务流，并使用 Wsatconfig.exe 工具启用 WCF 事务网络支持。</span><span class="sxs-lookup"><span data-stu-id="8452e-157">Whether you run the sample on the same computer or on different computers, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable WCF transactions network support.</span></span>  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a><span data-ttu-id="8452e-158">配置 Microsoft 分布式事务处理协调器 (MSDTC) 以支持运行示例</span><span class="sxs-lookup"><span data-stu-id="8452e-158">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample</span></span>  
  
1. <span data-ttu-id="8452e-159">在运行 Windows Server 2003 或 Windows XP 的服务计算机上，按以下说明配置 MSDTC 以允许传入网络事务。</span><span class="sxs-lookup"><span data-stu-id="8452e-159">On a service machine running Windows Server 2003 or Windows XP, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1. <span data-ttu-id="8452e-160">从 "**开始**" 菜单，导航到 **"控制面板**"，然后依次导航到 "**管理工具**" 和 "**组件服务**"。</span><span class="sxs-lookup"><span data-stu-id="8452e-160">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="8452e-161">展开 "**组件服务**"。</span><span class="sxs-lookup"><span data-stu-id="8452e-161">Expand **Component Services**.</span></span> <span data-ttu-id="8452e-162">打开 "**计算机**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="8452e-162">Open the **Computers** folder.</span></span>  
  
    3. <span data-ttu-id="8452e-163">右键单击**我的电脑**，然后选择 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="8452e-163">Right-click **My Computer** and select **Properties**.</span></span>  
  
    4. <span data-ttu-id="8452e-164">在 " **MSDTC** " 选项卡上，单击 "**安全配置**"。</span><span class="sxs-lookup"><span data-stu-id="8452e-164">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    5. <span data-ttu-id="8452e-165">检查 "**网络 DTC 访问**" 和 "**允许入站**"。</span><span class="sxs-lookup"><span data-stu-id="8452e-165">Check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    6. <span data-ttu-id="8452e-166">单击 **"确定**"，然后单击 **"是**" 以重新启动 MSDTC 服务。</span><span class="sxs-lookup"><span data-stu-id="8452e-166">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    7. <span data-ttu-id="8452e-167">单击“确定”  关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="8452e-167">Click **OK** to close the dialog box.</span></span>  
  
2. <span data-ttu-id="8452e-168">在运行 Windows Server 2008 或 Windows Vista 的服务计算机上，按以下说明配置 MSDTC 以允许传入网络事务。</span><span class="sxs-lookup"><span data-stu-id="8452e-168">On a service machine running Windows Server 2008 or Windows Vista, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1. <span data-ttu-id="8452e-169">从 "**开始**" 菜单，导航到 **"控制面板**"，然后依次导航到 "**管理工具**" 和 "**组件服务**"。</span><span class="sxs-lookup"><span data-stu-id="8452e-169">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="8452e-170">展开 "**组件服务**"。</span><span class="sxs-lookup"><span data-stu-id="8452e-170">Expand **Component Services**.</span></span> <span data-ttu-id="8452e-171">打开 "**计算机**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="8452e-171">Open the **Computers** folder.</span></span> <span data-ttu-id="8452e-172">选择**分布式事务处理协调器**。</span><span class="sxs-lookup"><span data-stu-id="8452e-172">Select **Distributed Transaction Coordinator**.</span></span>  
  
    3. <span data-ttu-id="8452e-173">右键单击 " **DTC 协调器**"，然后选择 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="8452e-173">Right-click **DTC Coordinator** and select **Properties**.</span></span>  
  
    4. <span data-ttu-id="8452e-174">在 "**安全**" 选项卡上，选中 "**网络 DTC 访问**" 和 "**允许入站**"。</span><span class="sxs-lookup"><span data-stu-id="8452e-174">On the **Security** tab, check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    5. <span data-ttu-id="8452e-175">单击 **"确定**"，然后单击 **"是**" 以重新启动 MSDTC 服务。</span><span class="sxs-lookup"><span data-stu-id="8452e-175">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6. <span data-ttu-id="8452e-176">单击“确定”  关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="8452e-176">Click **OK** to close the dialog box.</span></span>  
  
3. <span data-ttu-id="8452e-177">在客户端计算机上，配置 MSDTC 以允许传出网络事务：</span><span class="sxs-lookup"><span data-stu-id="8452e-177">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>  
  
    1. <span data-ttu-id="8452e-178">从 "**开始**" 菜单中，依次导航到 `Control Panel` "**管理工具**" 和 "**组件服务**"。</span><span class="sxs-lookup"><span data-stu-id="8452e-178">From the **Start** menu, navigate to `Control Panel`, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="8452e-179">右键单击**我的电脑**，然后选择 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="8452e-179">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3. <span data-ttu-id="8452e-180">在 " **MSDTC** " 选项卡上，单击 "**安全配置**"。</span><span class="sxs-lookup"><span data-stu-id="8452e-180">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4. <span data-ttu-id="8452e-181">检查 "**网络 DTC 访问**" 和 "**允许出站**"。</span><span class="sxs-lookup"><span data-stu-id="8452e-181">Check **Network DTC Access** and **Allow Outbound**.</span></span>  
  
    5. <span data-ttu-id="8452e-182">单击 **"确定**"，然后单击 **"是**" 以重新启动 MSDTC 服务。</span><span class="sxs-lookup"><span data-stu-id="8452e-182">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6. <span data-ttu-id="8452e-183">单击“确定”  关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="8452e-183">Click **OK** to close the dialog box.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8452e-184">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="8452e-184">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8452e-185">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="8452e-185">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="8452e-186">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="8452e-186">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8452e-187">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="8452e-187">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`

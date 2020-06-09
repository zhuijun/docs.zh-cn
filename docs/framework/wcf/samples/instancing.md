---
title: 实例化
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, instancing sample
- Instancing Sample [Windows Communication Foundation]
ms.assetid: c290fa54-f6ae-45a1-9186-d9504ebc6ee6
ms.openlocfilehash: 1cfaa0db5b81858b733343f17cae71e5815ef60b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596612"
---
# <a name="instancing"></a><span data-ttu-id="1422d-102">实例化</span><span class="sxs-lookup"><span data-stu-id="1422d-102">Instancing</span></span>
<span data-ttu-id="1422d-103">“实例化”示例演示实例化行为设置，此设置控制如何响应客户端请求来创建服务类的实例。</span><span class="sxs-lookup"><span data-stu-id="1422d-103">The Instancing sample demonstrates the instancing behavior setting, which controls how instances of a service class are created in response to client requests.</span></span> <span data-ttu-id="1422d-104">该示例基于实现服务协定的[入门](getting-started-sample.md) `ICalculator` 。</span><span class="sxs-lookup"><span data-stu-id="1422d-104">The sample is based on the [Getting Started](getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="1422d-105">本示例定义从 `ICalculatorInstance` 继承的新协定 `ICalculator`。</span><span class="sxs-lookup"><span data-stu-id="1422d-105">This sample defines a new contract, `ICalculatorInstance`, which inherits from `ICalculator`.</span></span> <span data-ttu-id="1422d-106">用 `ICalculatorInstance` 指定的协定提供了三个附加操作，用于检查服务实例的状态。</span><span class="sxs-lookup"><span data-stu-id="1422d-106">The contract specified by `ICalculatorInstance` provides three additional operations for inspecting the state of the service instance.</span></span> <span data-ttu-id="1422d-107">通过更改实例化设置，运行客户端时可以观察到行为中的更改。</span><span class="sxs-lookup"><span data-stu-id="1422d-107">By altering the instancing setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="1422d-108">在此示例中，客户端是一个控制台应用程序 (.exe)，服务是由 Internet 信息服务 (IIS) 承载的。</span><span class="sxs-lookup"><span data-stu-id="1422d-108">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1422d-109">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="1422d-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1422d-110">可以使用下列实例化模式：</span><span class="sxs-lookup"><span data-stu-id="1422d-110">The following instancing modes are available:</span></span>  
  
- <span data-ttu-id="1422d-111"><xref:System.ServiceModel.InstanceContextMode.PerCall>：为每个客户端请求创建一个新的服务实例。</span><span class="sxs-lookup"><span data-stu-id="1422d-111"><xref:System.ServiceModel.InstanceContextMode.PerCall>: A new service instance is created for each client request.</span></span>  
  
- <span data-ttu-id="1422d-112"><xref:System.ServiceModel.InstanceContextMode.PerSession>：为每个新的客户端会话创建一个新的实例，并在该会话的生存期内对其进行维护（这需要能够支持会话的绑定）。</span><span class="sxs-lookup"><span data-stu-id="1422d-112"><xref:System.ServiceModel.InstanceContextMode.PerSession>: A new instance is created for each new client session, and maintained for the lifetime of that session (requires a binding that supports session).</span></span>  
  
- <span data-ttu-id="1422d-113"><xref:System.ServiceModel.InstanceContextMode.Single>：服务类的单个实例处理应用程序生存期内的所有客户端请求。</span><span class="sxs-lookup"><span data-stu-id="1422d-113"><xref:System.ServiceModel.InstanceContextMode.Single>: A single instance of the service class handles all client requests for the lifetime of the application.</span></span>  
  
 <span data-ttu-id="1422d-114">服务类使用以下代码示例中显示的 `[ServiceBehavior(InstanceContextMode=<setting>)]` 属性来指定实例化行为。</span><span class="sxs-lookup"><span data-stu-id="1422d-114">The service class specifies instancing behavior with the `[ServiceBehavior(InstanceContextMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="1422d-115">通过更改注释掉的行，可以观察每个实例模式的行为。</span><span class="sxs-lookup"><span data-stu-id="1422d-115">By changing which lines are commented out, you can observe the behavior of each of the instance modes.</span></span> <span data-ttu-id="1422d-116">更改实例化模式之后要记着重新生成服务。</span><span class="sxs-lookup"><span data-stu-id="1422d-116">Remember to rebuild the service after changing the instancing mode.</span></span> <span data-ttu-id="1422d-117">没有要在客户端上指定的实例化相关设置。</span><span class="sxs-lookup"><span data-stu-id="1422d-117">There are no instancing-related settings to specify on the client.</span></span>  
  
```csharp
// Enable one of the following instance modes to compare instancing behaviors.  
 [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
  
// PerCall creates a new instance for each operation.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerCall)]  
  
// Singleton creates a single instance for application lifetime.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class CalculatorService : ICalculatorInstance  
{  
    static Object syncObject = new object();  
    static int instanceCount;  
    int instanceId;  
    int operationCount;  
  
    public CalculatorService()  
    {  
        lock (syncObject)  
        {  
            instanceCount++;  
            instanceId = instanceCount;  
        }  
    }  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 / n2;  
    }  
  
    public string GetInstanceContextMode()  
    {   // Return the InstanceContextMode of the service  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.InstanceContextMode.ToString();  
    }  
  
    public int GetInstanceId()  
    {   // Return the id for this instance  
        return instanceId;  
    }  
  
    public int GetOperationCount()  
    {   // Return the number of ICalculator operations performed
        // on this instance  
        lock (syncObject)  
        {  
            return operationCount;  
        }  
    }  
}  
  
static void Main()  
{  
    // Create a client.  
    CalculatorInstanceClient client = new CalculatorInstanceClient();  
    string instanceMode = client.GetInstanceContextMode();  
    Console.WriteLine("InstanceContextMode: {0}", instanceMode);  
    DoCalculations(client);  
  
    // Create a second client.  
    CalculatorInstanceClient client2 = new CalculatorInstanceClient();  
  
    DoCalculations(client2);  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
}  
```  
  
 <span data-ttu-id="1422d-118">运行示例时，操作请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="1422d-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="1422d-119">会显示运行服务时所使用的实例模式。</span><span class="sxs-lookup"><span data-stu-id="1422d-119">The instance mode the service is running under is displayed.</span></span> <span data-ttu-id="1422d-120">执行每个操作后，显示实例 ID 和操作计数以反映实例化模式的行为。</span><span class="sxs-lookup"><span data-stu-id="1422d-120">After each operation, the instance ID and operation count are displayed to reflect the behavior of the instancing mode.</span></span> <span data-ttu-id="1422d-121">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="1422d-121">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1422d-122">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="1422d-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1422d-123">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="1422d-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="1422d-124">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="1422d-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="1422d-125">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="1422d-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1422d-126">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="1422d-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1422d-127">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="1422d-127">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="1422d-128">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="1422d-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1422d-129">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="1422d-129">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Instancing`  

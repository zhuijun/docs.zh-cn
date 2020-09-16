---
title: 使用内联代码的 IIS 承载
ms.date: 03/30/2017
helpviewer_keywords:
- Web hosted service
- IIS Hosting Using Inline Code Sample [Windows Communication Foundation]
ms.assetid: 56fe3687-a34b-4661-8e30-b33770f413fa
ms.openlocfilehash: 41e19c318953d7e97eb5183c5a16a3780813f94c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558987"
---
# <a name="iis-hosting-using-inline-code"></a><span data-ttu-id="bc0d5-102">使用内联代码的 IIS 承载</span><span class="sxs-lookup"><span data-stu-id="bc0d5-102">IIS Hosting Using Inline Code</span></span>

<span data-ttu-id="bc0d5-103">此示例演示如何实现由 Internet 信息服务 (IIS) 承载的服务，该服务的服务代码以内联方式包含在一个 .svc 文件中，并且可以按需编译。</span><span class="sxs-lookup"><span data-stu-id="bc0d5-103">This sample demonstrates how to implement a service hosted by Internet Information Services (IIS), where the service code is contained in-line in a .svc file and is compiled on demand.</span></span> <span data-ttu-id="bc0d5-104">服务代码还可以直接在源代码文件（位于应用程序的 \App_Code 目录中）中实现，也可以编译为 \bin 中所部署的程序集。</span><span class="sxs-lookup"><span data-stu-id="bc0d5-104">Service code can also be implemented directly in source code files located in the application's \App_Code directory, or compiled into assembly deployed in \bin.</span></span> <span data-ttu-id="bc0d5-105">此示例不演示这些技术。</span><span class="sxs-lookup"><span data-stu-id="bc0d5-105">This sample does not demonstrate these techniques.</span></span>

> [!NOTE]
> <span data-ttu-id="bc0d5-106">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="bc0d5-106">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bc0d5-107">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="bc0d5-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="bc0d5-108">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="bc0d5-108">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="bc0d5-109">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc0d5-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bc0d5-110">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="bc0d5-110">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\InlineCode`

<span data-ttu-id="bc0d5-111">本示例演示一个典型的服务，该服务实现定义“请求-答复”通信模式的协定。</span><span class="sxs-lookup"><span data-stu-id="bc0d5-111">The sample demonstrates a typical service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="bc0d5-112">该服务由 IIS 承载，服务代码完全包含在 Service.svc 文件中。</span><span class="sxs-lookup"><span data-stu-id="bc0d5-112">The service is hosted in IIS and the service code is entirely contained in the Service.svc file.</span></span> <span data-ttu-id="bc0d5-113">该服务由主机激活，并由发送给它的第一条消息按需编译。</span><span class="sxs-lookup"><span data-stu-id="bc0d5-113">The service is host-activated and compiled on-demand by the first message sent to the service.</span></span> <span data-ttu-id="bc0d5-114">没有必要进行预先编译。</span><span class="sxs-lookup"><span data-stu-id="bc0d5-114">There is no pre-compilation necessary.</span></span> <span data-ttu-id="bc0d5-115">该服务实现一个 `ICalculator` 协定，下面的代码对该协定进行了定义：</span><span class="sxs-lookup"><span data-stu-id="bc0d5-115">The service implements an `ICalculator` contract as defined in the following code:</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
    public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

<span data-ttu-id="bc0d5-116">服务实现计算并返回相应的结果。</span><span class="sxs-lookup"><span data-stu-id="bc0d5-116">The service implementation calculates and returns the appropriate result.</span></span>

`<%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService" %>`

```csharp
// Service class that implements the service contract.
public class CalculatorService : ICalculator
{
    public double Add(double n1, double n2)
    {
        return n1 + n2;
    }
    public double Subtract(double n1, double n2)
    {
        return n1 - n2;
    }
    public double Multiply(double n1, double n2)
    {
        return n1 * n2;
    }
    public double Divide(double n1, double n2)
    {
        return n1 / n2;
    }
}
```

<span data-ttu-id="bc0d5-117">运行示例时，操作请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="bc0d5-117">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="bc0d5-118">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="bc0d5-118">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bc0d5-119">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="bc0d5-119">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="bc0d5-120">确保已对 [Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="bc0d5-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="bc0d5-121">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="bc0d5-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="bc0d5-122">构建解决方案后，运行 setup.bat 在 IIS 7.0 中设置 ServiceModelSamples 应用程序。</span><span class="sxs-lookup"><span data-stu-id="bc0d5-122">After the solution has been built, run setup.bat to set up the ServiceModelSamples Application in IIS 7.0.</span></span> <span data-ttu-id="bc0d5-123">现在，ServiceModelSamples 目录应显示为 IIS 7.0 应用程序。</span><span class="sxs-lookup"><span data-stu-id="bc0d5-123">The ServiceModelSamples directory should now appear as an IIS 7.0 Application.</span></span>

4. <span data-ttu-id="bc0d5-124">若要以单机配置或跨计算机配置来运行示例，请按照 [运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="bc0d5-124">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span> <span data-ttu-id="bc0d5-125">有关如何创建可调用此服务的客户端应用程序的示例，请参阅 [如何：创建客户端](../how-to-create-a-wcf-client.md)。</span><span class="sxs-lookup"><span data-stu-id="bc0d5-125">For an example on how to create a client application that can call this service, see [How to: Create a Client](../how-to-create-a-wcf-client.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bc0d5-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="bc0d5-126">See also</span></span>

- <span data-ttu-id="bc0d5-127">[AppFabric 承载和持久性示例](/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="bc0d5-127">[AppFabric Hosting and Persistence Samples](/previous-versions/appfabric/ff383418(v=azure.10))</span></span>

---
title: 限制
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, throttling sample
- Throttling Sample [Windows Communication Foundation]
ms.assetid: 40bb3582-8ae9-4410-96f0-6c515bfaf47c
ms.openlocfilehash: f007d153a04117df872ea2fcdc68af38c57b53b3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600862"
---
# <a name="throttling"></a><span data-ttu-id="f4e9a-102">限制</span><span class="sxs-lookup"><span data-stu-id="f4e9a-102">Throttling</span></span>
<span data-ttu-id="f4e9a-103">遏制示例演示如何使用遏制控制。</span><span class="sxs-lookup"><span data-stu-id="f4e9a-103">The Throttling sample demonstrates the use of throttling controls.</span></span> <span data-ttu-id="f4e9a-104">限制控件会对并发调用、实例或会话的数目施加限制以防止过度使用资源。</span><span class="sxs-lookup"><span data-stu-id="f4e9a-104">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span> <span data-ttu-id="f4e9a-105">您可以在服务配置文件设置中指定遏制行为。</span><span class="sxs-lookup"><span data-stu-id="f4e9a-105">Throttling behavior is specified in service configuration file settings.</span></span> <span data-ttu-id="f4e9a-106">此示例基于实现计算器服务的[入门](getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="f4e9a-106">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span>  
  
 <span data-ttu-id="f4e9a-107">在此示例中，客户端是一个控制台应用程序 (.exe)，服务是由 Internet 信息服务 (IIS) 承载的。</span><span class="sxs-lookup"><span data-stu-id="f4e9a-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f4e9a-108">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="f4e9a-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f4e9a-109">服务配置文件指定中的限制控件 [\<serviceThrottling>](../../configure-apps/file-schema/wcf/servicethrottling.md) ，如下面的示例配置中所示。</span><span class="sxs-lookup"><span data-stu-id="f4e9a-109">The service configuration file specifies throttling controls in a [\<serviceThrottling>](../../configure-apps/file-schema/wcf/servicethrottling.md), as shown in the following sample configuration.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceDebug includeExceptionDetailInFaults="False" />  
      <serviceMetadata httpGetEnabled="True"/>  
      <!-- Specify throttling behavior -->  
    <serviceThrottling maxConcurrentCalls="2"  
                       maxConcurrentInstances="10"/>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="f4e9a-110">按照配置要求，服务将最大并发调用数限制为 2，最大并发实例数限制为 10。</span><span class="sxs-lookup"><span data-stu-id="f4e9a-110">As configured, the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span>  
  
 <span data-ttu-id="f4e9a-111">为了演示遏制，我们对服务方法定义了休眠时间，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f4e9a-111">In order to demonstrate throttling we define a sleep time on the service methods as follows:</span></span>  
  
```csharp
public double Add(double n1, double n2)  
{  
    System.Threading.Thread.Sleep(2000);  
    return n1 + n2;  
}  
```  
  
 <span data-ttu-id="f4e9a-112">运行示例时，操作请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="f4e9a-112">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="f4e9a-113">并发执行 Add 和 Subtract 方法以及 Multiply 和 Divide 方法，条件是并发执行的方法不超过 2 个，并由此而表现出遏制。</span><span class="sxs-lookup"><span data-stu-id="f4e9a-113">The Add and Subtract methods are executed concurrently and the Multiply and Divide methods are executed concurrently proving that not more than 2 methods can be executed concurrently thus demonstrating throttling.</span></span>  
  
```console  
Press <ENTER> to terminate client.  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Add Result: 115.99  
Subtract Result: 68.46  
Multiply Result: 731.25  
Divide Result: 3.14285714285714  
  
Press any key to continue . . .  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f4e9a-114">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="f4e9a-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f4e9a-115">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="f4e9a-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="f4e9a-116">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="f4e9a-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="f4e9a-117">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="f4e9a-117">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f4e9a-118">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="f4e9a-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f4e9a-119">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="f4e9a-119">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f4e9a-120">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="f4e9a-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f4e9a-121">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="f4e9a-121">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Throttling`  

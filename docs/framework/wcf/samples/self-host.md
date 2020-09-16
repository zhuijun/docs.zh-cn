---
title: 自承载
ms.date: 03/30/2017
helpviewer_keywords:
- Self hosted service
- Self Host Sample [Windows Communication Foundation]
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
ms.openlocfilehash: 544ae8c0bc88d49c281810714225dbadecfd443b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558402"
---
# <a name="self-host"></a><span data-ttu-id="c2b40-102">自承载</span><span class="sxs-lookup"><span data-stu-id="c2b40-102">Self-Host</span></span>
<span data-ttu-id="c2b40-103">此示例演示如何在控制台应用程序中实现自承载服务。</span><span class="sxs-lookup"><span data-stu-id="c2b40-103">This sample demonstrates how to implement a self-hosted service in a console application.</span></span> <span data-ttu-id="c2b40-104">此示例基于 [入门](getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="c2b40-104">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="c2b40-105">服务配置文件已从 Web.config 重命名为 App.config，并修改为配置一个由主机使用的基址。</span><span class="sxs-lookup"><span data-stu-id="c2b40-105">The service configuration file has been renamed from Web.config to App.config and modified to configure a base address, which the host uses.</span></span> <span data-ttu-id="c2b40-106">服务源代码已修改为实现一个静态 `Main` 函数，该函数创建并打开一个提供已配置的基址的服务主机。</span><span class="sxs-lookup"><span data-stu-id="c2b40-106">The service source code has been modified to implement a static `Main` function that creates and opens a service host that provides the configured base address.</span></span> <span data-ttu-id="c2b40-107">服务实现已修改为将每个操作的输出写入控制台。</span><span class="sxs-lookup"><span data-stu-id="c2b40-107">The service implementation has been modified to write output to the console for each operation.</span></span> <span data-ttu-id="c2b40-108">客户端未经修改，只是配置了服务的正确终结点地址。</span><span class="sxs-lookup"><span data-stu-id="c2b40-108">The client has been unmodified, except for configuring the correct endpoint address of the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c2b40-109">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="c2b40-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c2b40-110">此示例实现一个静态主函数，以便为给定的 <xref:System.ServiceModel.ServiceHost> 类型创建一个 `CalculatorService`，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="c2b40-110">The sample implements a static main function to create a <xref:System.ServiceModel.ServiceHost> for the given `CalculatorService` type, as shown in the following sample code.</span></span>  
  
```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Create a ServiceHost for the CalculatorService type.  
    using (ServiceHost serviceHost =
           new ServiceHost(typeof(CalculatorService)))  
    {  
        // Open the ServiceHost to create listeners
        // and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
    }  
}  
```  
  
 <span data-ttu-id="c2b40-111">当服务承载在 Internet 信息服务 (IIS) 或 Windows 进程激活服务 (WAS) 中时，服务的基址由宿主环境提供。</span><span class="sxs-lookup"><span data-stu-id="c2b40-111">When a service is hosted in Internet Information Services (IIS) or Windows Process Activation Service (WAS), the base address of the service is provided by the hosting environment.</span></span> <span data-ttu-id="c2b40-112">在自承载情况下，您必须亲自指定基址。</span><span class="sxs-lookup"><span data-stu-id="c2b40-112">In the self-hosted case, you must specify the base address yourself.</span></span> <span data-ttu-id="c2b40-113">这是使用的元素、的子级、的子级、的子级实现的， `add` [\<baseAddresses>](../../configure-apps/file-schema/wcf/baseaddresses.md) [\<host>](../../configure-apps/file-schema/wcf/host.md) [\<service>](../../configure-apps/file-schema/wcf/service.md) 如下面的示例配置中所示。</span><span class="sxs-lookup"><span data-stu-id="c2b40-113">This is done using the `add` element, child of [\<baseAddresses>](../../configure-apps/file-schema/wcf/baseaddresses.md), child of [\<host>](../../configure-apps/file-schema/wcf/host.md), child of [\<service>](../../configure-apps/file-schema/wcf/service.md) as demonstrated in the following sample configuration.</span></span>  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
  ...  
</service>  
```  
  
 <span data-ttu-id="c2b40-114">运行示例时，操作请求和响应将显示在服务和客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="c2b40-114">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="c2b40-115">在每个控制台窗口中按 Enter 可以关闭服务和客户端。</span><span class="sxs-lookup"><span data-stu-id="c2b40-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c2b40-116">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="c2b40-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c2b40-117">确保已对 [Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="c2b40-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c2b40-118">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="c2b40-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="c2b40-119">若要以单机配置或跨计算机配置来运行示例，请按照 [运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="c2b40-119">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c2b40-120">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="c2b40-120">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c2b40-121">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="c2b40-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c2b40-122">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2b40-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c2b40-123">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="c2b40-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## <a name="see-also"></a><span data-ttu-id="c2b40-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="c2b40-124">See also</span></span>

- <span data-ttu-id="c2b40-125">[AppFabric 承载和持久性示例](/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="c2b40-125">[AppFabric Hosting and Persistence Samples](/previous-versions/appfabric/ff383418(v=azure.10))</span></span>

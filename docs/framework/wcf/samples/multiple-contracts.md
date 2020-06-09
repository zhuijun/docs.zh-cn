---
title: 多个协定
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: e8451c49395a1dad55c5afca419f47a8e856b61f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602500"
---
# <a name="multiple-contracts"></a><span data-ttu-id="5f0b7-102">多个协定</span><span class="sxs-lookup"><span data-stu-id="5f0b7-102">Multiple Contracts</span></span>
<span data-ttu-id="5f0b7-103">“多个协定”示例演示如何在一个服务上实现多个协定，以及如何配置终结点以便与实现的每个协定进行通信。</span><span class="sxs-lookup"><span data-stu-id="5f0b7-103">The Multiple Contracts sample demonstrates how to implement more than one contract on a service and how to configure endpoints for communicating with each of the implemented contracts.</span></span> <span data-ttu-id="5f0b7-104">此示例基于[入门](getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="5f0b7-104">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="5f0b7-105">该服务已进行修改以定义两个协定：`ICalculator` 协定和 `ICalculatorSession` 协定。</span><span class="sxs-lookup"><span data-stu-id="5f0b7-105">The service has been modified to define two contracts, the `ICalculator` contract and the `ICalculatorSession` contract.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5f0b7-106">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="5f0b7-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5f0b7-107">服务类同时实现了 `ICalculator` 和 `ICalculatorSession` 协定。</span><span class="sxs-lookup"><span data-stu-id="5f0b7-107">The service class implements both the `ICalculator` and `ICalculatorSession` contracts.</span></span> <span data-ttu-id="5f0b7-108">因为其中一个协定需要一个会话，所以该服务使用 <xref:System.ServiceModel.InstanceContextMode.PerSession> 实例模式在会话生存期内维护状态。</span><span class="sxs-lookup"><span data-stu-id="5f0b7-108">Because one of the contracts requires a session, the service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the state over the lifetime of the session.</span></span>  
  
 <span data-ttu-id="5f0b7-109">服务配置已进行修改，定义了两个终结点，以公开每个协定。</span><span class="sxs-lookup"><span data-stu-id="5f0b7-109">The service configuration has been modified to define two endpoints to expose each contract.</span></span> <span data-ttu-id="5f0b7-110">`ICalculator` 终结点是使用 `basicHttpBinding` 在基地址上公开的。</span><span class="sxs-lookup"><span data-stu-id="5f0b7-110">The `ICalculator` endpoint is exposed at the base address using a `basicHttpBinding`.</span></span> <span data-ttu-id="5f0b7-111">`ICalculatorSession` 终结点是使用 `wsHttpBinding`（其 `bindingConfiguration` 属性设置为 `BindingWithSession`）在基地址/会话上公开的，如下面的示例配置中所示。</span><span class="sxs-lookup"><span data-stu-id="5f0b7-111">The `ICalculatorSession` endpoint is exposed at the baseaddress/session using a `wsHttpBinding` with the `bindingConfiguration` attribute set to `BindingWithSession`, as shown in the following sample configuration.</span></span>  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <!-- ICalculator endpoint is exposed using BasicBinding at the base  
       address provided by host:   
       http://localhost/servicemodelsamples/service.svc  -->  
  <endpoint address=""  
            binding="basicHttpBinding"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  <!-- ICalculatorSession endpoint is exposed using BindingWithSession  
       at {baseaddress}/session:  
       http://localhost/servicemodelsamples/service.svc/session -->  
  <endpoint address="session"  
            binding="wsHttpBinding"  
            bindingConfiguration="BindingWithSession"
           contract="Microsoft.ServiceModel.Samples.ICalculatorSession" />  
  ...  
</service>  
```  
  
 <span data-ttu-id="5f0b7-112">生成的客户端代码现在包含同时适用于原始 `ICalculator` 协定和新 `ICalculatorSession` 协定的客户端类。</span><span class="sxs-lookup"><span data-stu-id="5f0b7-112">The generated client code now includes a client class for both the original `ICalculator` contract and the new `ICalculatorSession` contract.</span></span> <span data-ttu-id="5f0b7-113">客户端配置和代码已进行修改，可以与相应服务终结点上的每个协定进行通信。</span><span class="sxs-lookup"><span data-stu-id="5f0b7-113">The client configuration and code have been modified to communicate with each contract at the appropriate service endpoint.</span></span>  
  
 <span data-ttu-id="5f0b7-114">客户端是一个控制台窗口应用程序 (.exe)。</span><span class="sxs-lookup"><span data-stu-id="5f0b7-114">The client is a console windows application (.exe).</span></span> <span data-ttu-id="5f0b7-115">服务是由 Internet 信息服务 (IIS) 承载的。</span><span class="sxs-lookup"><span data-stu-id="5f0b7-115">The service is hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="5f0b7-116">客户端控制台窗口显示发送给每个终结点的操作，首先是基本终结点，然后是安全终结点。</span><span class="sxs-lookup"><span data-stu-id="5f0b7-116">The client console window displays the operations sent to each of the endpoints, first the basic endpoint, followed by the secure endpoint.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5f0b7-117">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="5f0b7-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5f0b7-118">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="5f0b7-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5f0b7-119">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="5f0b7-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="5f0b7-120">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="5f0b7-120">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5f0b7-121">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="5f0b7-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5f0b7-122">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="5f0b7-122">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5f0b7-123">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="5f0b7-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5f0b7-124">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="5f0b7-124">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  

---
title: NetNamedPipeBinding
ms.date: 03/30/2017
helpviewer_keywords:
- Net Profile Named Pipe
ms.assetid: e78e845f-c325-46e2-927d-81616f97f7d5
ms.openlocfilehash: b8a852345572e172d7c5400dca535bb8c098ec4f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84584189"
---
# <a name="netnamedpipebinding"></a><span data-ttu-id="2aaa1-102">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="2aaa1-102">NetNamedPipeBinding</span></span>
<span data-ttu-id="2aaa1-103">本示例演示在同一台计算机上提供跨进程通信的 `netNamedPipeBinding` 绑定。</span><span class="sxs-lookup"><span data-stu-id="2aaa1-103">This sample demonstrates the `netNamedPipeBinding` binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="2aaa1-104">命名管道不能跨计算机工作。</span><span class="sxs-lookup"><span data-stu-id="2aaa1-104">Named pipes do not work across machines.</span></span> <span data-ttu-id="2aaa1-105">此示例基于[入门](getting-started-sample.md)计算器服务。</span><span class="sxs-lookup"><span data-stu-id="2aaa1-105">This sample is based on The [Getting Started](getting-started-sample.md) calculator service.</span></span>  
  
 <span data-ttu-id="2aaa1-106">在本示例中，服务是自承载服务。</span><span class="sxs-lookup"><span data-stu-id="2aaa1-106">In this sample, the service is self-hosted.</span></span> <span data-ttu-id="2aaa1-107">客户端和服务都是控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="2aaa1-107">Both the client and the service are console applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2aaa1-108">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="2aaa1-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="2aaa1-109">绑定是在客户端和服务的配置文件中指定的。</span><span class="sxs-lookup"><span data-stu-id="2aaa1-109">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="2aaa1-110">绑定类型是在 `binding` 或 [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) [ \<endpoint> \<client> ](../../configure-apps/file-schema/wcf/endpoint-of-client.md)元素的属性中指定的，如下面的示例配置所示：</span><span class="sxs-lookup"><span data-stu-id="2aaa1-110">The binding type is specified in the `binding` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) or [\<endpoint> of \<client>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element, as shown in the following sample configuration:</span></span>  
  
```xml  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="2aaa1-111">前面的示例演示如何配置终结点以使用具有默认设置的 `netNamedPipeBinding` 绑定。</span><span class="sxs-lookup"><span data-stu-id="2aaa1-111">The previous sample shows how to configure an endpoint to use the `netNamedPipeBinding` binding with the default settings.</span></span> <span data-ttu-id="2aaa1-112">如果要配置 `netNamedPipeBinding` 绑定并更改它的一些设置，则必须定义绑定配置。</span><span class="sxs-lookup"><span data-stu-id="2aaa1-112">If you want to configure the `netNamedPipeBinding` binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="2aaa1-113">终结点必须使用 `bindingConfiguration` 属性按名称来引用绑定配置。</span><span class="sxs-lookup"><span data-stu-id="2aaa1-113">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span>  
  
```xml  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          bindingConfiguration="Binding1"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="2aaa1-114">在本示例中，绑定配置的名称为 `Binding1` 并具有以下定义：</span><span class="sxs-lookup"><span data-stu-id="2aaa1-114">In this sample, the binding configuration is named `Binding1` and has the following definition:</span></span>  
  
```xml  
<bindings>  
  <!--   
        Following is the expanded configuration section for a NetNamedPipeBinding.  
        Each property is configured with the default value.  
     -->  
  <netNamedPipeBinding>  
    <binding name="Binding1"
             closeTimeout="00:01:00"  
             openTimeout="00:01:00"
             receiveTimeout="00:10:00"
             sendTimeout="00:01:00"  
             transactionFlow="false"
             transferMode="Buffered"
             transactionProtocol="OleTransactions"  
             hostNameComparisonMode="StrongWildcard"
             maxBufferPoolSize="524288"  
             maxBufferSize="65536"
             maxConnections="10"
             maxReceivedMessageSize="65536">  
      <security mode="Transport">  
        <transport protectionLevel="EncryptAndSign" />  
      </security>  
    </binding>  
  </netNamedPipeBinding>  
</bindings>  
```  
  
 <span data-ttu-id="2aaa1-115">运行示例时，操作请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="2aaa1-115">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="2aaa1-116">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="2aaa1-116">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2aaa1-117">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="2aaa1-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2aaa1-118">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="2aaa1-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="2aaa1-119">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="2aaa1-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="2aaa1-120">若要在单个计算机配置中运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="2aaa1-120">To run the sample in a single machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2aaa1-121">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="2aaa1-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2aaa1-122">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="2aaa1-122">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="2aaa1-123">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="2aaa1-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2aaa1-124">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="2aaa1-124">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\NamedPipe`  

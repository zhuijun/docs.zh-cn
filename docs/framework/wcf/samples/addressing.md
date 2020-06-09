---
title: 寻址
ms.date: 03/30/2017
ms.assetid: d438e6f2-d0f3-43aa-b259-b51b5bda2e64
ms.openlocfilehash: 3221a12a21aebe20e0f6822554937623dc3fbb8d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575961"
---
# <a name="addressing"></a><span data-ttu-id="89dfd-102">寻址</span><span class="sxs-lookup"><span data-stu-id="89dfd-102">Addressing</span></span>
<span data-ttu-id="89dfd-103">“寻址”示例演示终结点地址的各个方面和功能。</span><span class="sxs-lookup"><span data-stu-id="89dfd-103">The Addressing sample demonstrates various aspects and features of endpoint addresses.</span></span> <span data-ttu-id="89dfd-104">该示例基于[入门](getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="89dfd-104">The sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="89dfd-105">在本示例中，服务是自承载的。</span><span class="sxs-lookup"><span data-stu-id="89dfd-105">In this sample the service is self-hosted.</span></span> <span data-ttu-id="89dfd-106">服务和客户端都是控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="89dfd-106">Both the service and the client are console applications.</span></span> <span data-ttu-id="89dfd-107">服务使用相对和绝对终结点地址的组合来定义多个终结点。</span><span class="sxs-lookup"><span data-stu-id="89dfd-107">The service defines multiple endpoints using a combination of relative and absolute endpoint addresses.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="89dfd-108">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="89dfd-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="89dfd-109">服务配置文件指定一个基址和四个终结点。</span><span class="sxs-lookup"><span data-stu-id="89dfd-109">The service configuration file specifies a base address and four endpoints.</span></span> <span data-ttu-id="89dfd-110">基址是在 service/host/baseAddresses 下使用 add 元素来指定的，如下面的示例配置所示。</span><span class="sxs-lookup"><span data-stu-id="89dfd-110">The base address is specified using the add element, under service/host/baseAddresses as demonstrated in the following sample configuration.</span></span>  
  
```xml  
<service name="Microsoft.ServiceModel.Samples.CalculatorService"  
         behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />  
    </baseAddresses>  
  </host>  
</service>  
```  
  
 <span data-ttu-id="89dfd-111">在以下示例配置中显示的第一个终结点定义指定一个相对地址，这意味着终结点地址是遵循 URI 构成规则的基址和相对地址的结合。</span><span class="sxs-lookup"><span data-stu-id="89dfd-111">The first endpoint definition shown in the following sample configuration specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of URI composition.</span></span>  
  
```xml
<!-- Empty relative address specified:   
     use the base address provided by the host. -->  
<!-- The endpoint address is  
     http://localhost:8000/ServiceModelSamples/service. -->  
<endpoint address=""  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="89dfd-112">在本例中，相对地址为空（“”），因此终结点地址与基址相同。</span><span class="sxs-lookup"><span data-stu-id="89dfd-112">In this case, the relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="89dfd-113">实际终结点地址为 `http://localhost:8000/servicemodelsamples/service` 。</span><span class="sxs-lookup"><span data-stu-id="89dfd-113">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service`.</span></span>
  
 <span data-ttu-id="89dfd-114">第二个终结点定义也指定一个相对地址，如下面的示例配置所示。</span><span class="sxs-lookup"><span data-stu-id="89dfd-114">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span>  
  
```xml  
<!-- The relative address specified: use the base address -->  
<!-- provided by the host + path. The endpoint address is -->  
<!-- http://localhost:8000/servicemodelsamples/service/test. -->  
<endpoint address="/test"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="89dfd-115">将相对地址“test”追加到基址。</span><span class="sxs-lookup"><span data-stu-id="89dfd-115">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="89dfd-116">实际终结点地址为 `http://localhost:8000/servicemodelsamples/service/test` 。</span><span class="sxs-lookup"><span data-stu-id="89dfd-116">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service/test`.</span></span>
  
 <span data-ttu-id="89dfd-117">第三个终结点定义指定一个绝对地址，如下面的示例配置所示。</span><span class="sxs-lookup"><span data-stu-id="89dfd-117">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="89dfd-118">基址在地址中不起作用。</span><span class="sxs-lookup"><span data-stu-id="89dfd-118">The base address plays no role in the address.</span></span> <span data-ttu-id="89dfd-119">实际终结点地址为 `http://localhost:8001/hello/servicemodelsamples` 。</span><span class="sxs-lookup"><span data-stu-id="89dfd-119">The actual endpoint address is `http://localhost:8001/hello/servicemodelsamples`.</span></span>
  
 <span data-ttu-id="89dfd-120">第四个终结点地址指定一个绝对地址和一个不同的传输协议 (TCP)。</span><span class="sxs-lookup"><span data-stu-id="89dfd-120">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="89dfd-121">基址在地址中不起作用。</span><span class="sxs-lookup"><span data-stu-id="89dfd-121">The base address plays no role in the address.</span></span> <span data-ttu-id="89dfd-122">实际终结点地址为 `net.tcp://localhost:9000/servicemodelsamples/service` 。</span><span class="sxs-lookup"><span data-stu-id="89dfd-122">The actual endpoint address is `net.tcp://localhost:9000/servicemodelsamples/service`.</span></span>
  
```xml  
<!-- The absolute address specified, different transport: -->  
<!-- use the specified address, and ignore the base address. -->  
<!-- The endpoint address is -->  
<!-- net.tcp://localhost:9000/servicemodelsamples/service. -->  
<endpoint address=  
          "net.tcp://localhost:9000/servicemodelsamples/service"  
          binding="netTcpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="89dfd-123">客户端只访问四个服务终结点之一，但是在客户端的配置文件中对所有四个终结点都进行了定义。</span><span class="sxs-lookup"><span data-stu-id="89dfd-123">The client accesses just one of the four service endpoints, but all four are defined in its configuration file.</span></span> <span data-ttu-id="89dfd-124">客户端创建 `CalculatorProxy` 对象时将选择一个终结点。</span><span class="sxs-lookup"><span data-stu-id="89dfd-124">The client selects an endpoint when it creates the `CalculatorProxy` object.</span></span> <span data-ttu-id="89dfd-125">通过更改从 `CalculatorEndpoint1` 到 `CalculatorEndpoint4` 中的配置名称，您可以使用每个终结点。</span><span class="sxs-lookup"><span data-stu-id="89dfd-125">By changing the configuration name from `CalculatorEndpoint1` through `CalculatorEndpoint4`, you can exercise each of the endpoints.</span></span>  
  
 <span data-ttu-id="89dfd-126">运行示例时，服务会枚举其每个终结点的地址、绑定名称和协定名称。</span><span class="sxs-lookup"><span data-stu-id="89dfd-126">When you run the sample, the service enumerates the address, binding name and contract name for each of its endpoints.</span></span> <span data-ttu-id="89dfd-127">从 ServiceHost 的角度来看，元数据交换 (MEX) 终结点只是另一个终结点，因此在列表中出现。</span><span class="sxs-lookup"><span data-stu-id="89dfd-127">The metadata exchange (MEX) endpoint is just another endpoint from the ServiceHost's perspective so it shows up in the list.</span></span>  
  
```console  
Service endpoints:  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service/test  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8001/hello/servicemodelsamples  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  net.tcp://localhost:9000/servicemodelsamples/service  
           binding:  NetTcpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service/mex  
           binding:  MetadataExchangeHttpBinding  
           contract: IMetadataExchange  
  
The service is ready.  
Press <ENTER> to terminate service.  
```  
  
 <span data-ttu-id="89dfd-128">运行客户端时，操作请求和响应将显示在服务和客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="89dfd-128">When you run the client, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="89dfd-129">在每个控制台窗口中按 Enter 可以关闭服务和客户端。</span><span class="sxs-lookup"><span data-stu-id="89dfd-129">Press ENTER in each console window to shut down the service and client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="89dfd-130">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="89dfd-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="89dfd-131">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="89dfd-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="89dfd-132">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="89dfd-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="89dfd-133">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="89dfd-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="89dfd-134">如果使用 Svcutil.exe 为此示例重新生成配置，请确保在客户端配置中修改终结点名称以与客户端代码匹配。</span><span class="sxs-lookup"><span data-stu-id="89dfd-134">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="89dfd-135">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="89dfd-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="89dfd-136">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="89dfd-136">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="89dfd-137">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="89dfd-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="89dfd-138">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="89dfd-138">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Addressing`  

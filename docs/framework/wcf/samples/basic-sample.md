---
title: 基本示例
ms.date: 03/30/2017
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
ms.openlocfilehash: db560ec7dea3912ecec8d84943cc9a01512d1f33
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575766"
---
# <a name="basic-sample"></a><span data-ttu-id="7a0e7-102">基本示例</span><span class="sxs-lookup"><span data-stu-id="7a0e7-102">Basic Sample</span></span>

<span data-ttu-id="7a0e7-103">此示例演示如何使服务可发现以及如何搜索和调用可发现服务。</span><span class="sxs-lookup"><span data-stu-id="7a0e7-103">This sample shows how to make a service discoverable and how to search for and call a discoverable service.</span></span> <span data-ttu-id="7a0e7-104">此示例由两个项目组成：服务项目和客户端项目。</span><span class="sxs-lookup"><span data-stu-id="7a0e7-104">This sample is composed of two projects: service and client.</span></span>

> [!NOTE]
> <span data-ttu-id="7a0e7-105">此示例在代码中实现发现。</span><span class="sxs-lookup"><span data-stu-id="7a0e7-105">This sample implements discovery in code.</span></span>  <span data-ttu-id="7a0e7-106">有关在配置中实现发现的示例，请参阅[配置](configuration-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="7a0e7-106">For a sample that implements discovery in configuration, see [Configuration](configuration-sample.md).</span></span>

## <a name="service"></a><span data-ttu-id="7a0e7-107">服务</span><span class="sxs-lookup"><span data-stu-id="7a0e7-107">Service</span></span>

<span data-ttu-id="7a0e7-108">这是一个简单计算器服务实现。</span><span class="sxs-lookup"><span data-stu-id="7a0e7-108">This is a simple calculator service implementation.</span></span> <span data-ttu-id="7a0e7-109">与发现相关的代码可以在 `Main` 中找到，其中向服务主机添加了一个 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>，并且添加了一个 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="7a0e7-109">The discovery related code can be found in `Main` where a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is added to the service host and a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is added as shown in the following code.</span></span>

```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new
      WSHttpBinding(), String.Empty);

    // Make the service discoverable over UDP multicast
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());

    serviceHost.Open();
    // ...
}
```

## <a name="client"></a><span data-ttu-id="7a0e7-110">客户端</span><span class="sxs-lookup"><span data-stu-id="7a0e7-110">Client</span></span>

<span data-ttu-id="7a0e7-111">客户端使用 <xref:System.ServiceModel.Discovery.DynamicEndpoint> 定位服务。</span><span class="sxs-lookup"><span data-stu-id="7a0e7-111">The client uses a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to locate the service.</span></span> <span data-ttu-id="7a0e7-112">标准终结点 <xref:System.ServiceModel.Discovery.DynamicEndpoint> 在打开客户端时解析服务的终结点。</span><span class="sxs-lookup"><span data-stu-id="7a0e7-112">The <xref:System.ServiceModel.Discovery.DynamicEndpoint>, a standard endpoint, resolves the endpoint of the service when the client is opened.</span></span> <span data-ttu-id="7a0e7-113">在本例中，<xref:System.ServiceModel.Discovery.DynamicEndpoint> 基于服务协定查找服务。</span><span class="sxs-lookup"><span data-stu-id="7a0e7-113">In this case, the <xref:System.ServiceModel.Discovery.DynamicEndpoint> looks for the service based on the service contract.</span></span> <span data-ttu-id="7a0e7-114">默认情况下，<xref:System.ServiceModel.Discovery.DynamicEndpoint> 对 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 进行搜索。</span><span class="sxs-lookup"><span data-stu-id="7a0e7-114">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> conducts the search over a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> by default.</span></span> <span data-ttu-id="7a0e7-115">定位到服务终结点后，客户端便通过指定绑定连接到服务。</span><span class="sxs-lookup"><span data-stu-id="7a0e7-115">Once it locates a service endpoint, the client connects to that service over the specified binding.</span></span>

```csharp
public static void Main()
{
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());
   // ...
}
```

<span data-ttu-id="7a0e7-116">客户端定义一个名为 `InvokeCalculatorService` 方法，该方法使用 <xref:System.ServiceModel.Discovery.DiscoveryClient> 类搜索服务。</span><span class="sxs-lookup"><span data-stu-id="7a0e7-116">The client defines a method called `InvokeCalculatorService` that uses the <xref:System.ServiceModel.Discovery.DiscoveryClient> class to search for services.</span></span> <span data-ttu-id="7a0e7-117"><xref:System.ServiceModel.Discovery.DynamicEndpoint> 继承自 <xref:System.ServiceModel.Description.ServiceEndpoint>，因此可以传递给 `InvokeCalculatorService` 方法。</span><span class="sxs-lookup"><span data-stu-id="7a0e7-117">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> inherits from <xref:System.ServiceModel.Description.ServiceEndpoint>, so it can be passed to the `InvokeCalculatorService` method.</span></span> <span data-ttu-id="7a0e7-118">本示例随后使用 <xref:System.ServiceModel.Discovery.DynamicEndpoint> 创建 `CalculatorServiceClient` 的实例并调用计算器服务的各个操作。</span><span class="sxs-lookup"><span data-stu-id="7a0e7-118">The example then uses the <xref:System.ServiceModel.Discovery.DynamicEndpoint> to create an instance of `CalculatorServiceClient` and calls the various operations of the calculator service.</span></span>

```csharp
static void InvokeCalculatorService(ServiceEndpoint serviceEndpoint)
{
   // Create a client
   CalculatorServiceClient client = new CalculatorServiceClient(serviceEndpoint);

   Console.WriteLine("Invoking CalculatorService");
   Console.WriteLine();

   double value1 = 100.00D;
   double value2 = 15.99D;

   // Call the Add service operation.
   double result = client.Add(value1, value2);
   Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

   // Call the Subtract service operation.
   result = client.Subtract(value1, value2);
   Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

   // Call the Multiply service operation.
   result = client.Multiply(value1, value2);
   Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

   // Call the Divide service operation.
   result = client.Divide(value1, value2);
   Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);
   Console.WriteLine();

   //Closing the client gracefully closes the connection and cleans up resources
   client.Close();
}
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="7a0e7-119">使用此示例</span><span class="sxs-lookup"><span data-stu-id="7a0e7-119">To use this sample</span></span>

1. <span data-ttu-id="7a0e7-120">此示例使用 HTTP 终结点，若要运行此示例，必须添加正确的 URL ACL。</span><span class="sxs-lookup"><span data-stu-id="7a0e7-120">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added.</span></span> <span data-ttu-id="7a0e7-121">有关详细信息，请参阅[配置 HTTP 和 HTTPS](../feature-details/configuring-http-and-https.md)。</span><span class="sxs-lookup"><span data-stu-id="7a0e7-121">For more information, see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="7a0e7-122">使用提升的特权执行下面的命令应添加相应的 ACL。</span><span class="sxs-lookup"><span data-stu-id="7a0e7-122">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="7a0e7-123">如果该命令无效，则可能需要使用你的域和用户名替换以下自变量。</span><span class="sxs-lookup"><span data-stu-id="7a0e7-123">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. <span data-ttu-id="7a0e7-124">使用 Visual Studio 2012，打开基本 .sln 并生成示例。</span><span class="sxs-lookup"><span data-stu-id="7a0e7-124">Using Visual Studio 2012, open the Basic.sln and build the sample.</span></span>

3. <span data-ttu-id="7a0e7-125">运行 service.exe 应用程序。</span><span class="sxs-lookup"><span data-stu-id="7a0e7-125">Run the service.exe application.</span></span>

4. <span data-ttu-id="7a0e7-126">服务启动后，运行 client.exe。</span><span class="sxs-lookup"><span data-stu-id="7a0e7-126">After the service has started, run the client.exe.</span></span>

5. <span data-ttu-id="7a0e7-127">观察客户端是否能够在不知道服务地址的情况下找到服务。</span><span class="sxs-lookup"><span data-stu-id="7a0e7-127">Observe that the client was able to find the service without knowing its address.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7a0e7-128">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="7a0e7-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7a0e7-129">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="7a0e7-129">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="7a0e7-130">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="7a0e7-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7a0e7-131">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="7a0e7-131">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`

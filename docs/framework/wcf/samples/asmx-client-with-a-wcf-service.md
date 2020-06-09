---
title: 带有 WCF 服务的 ASMX 客户端
ms.date: 03/30/2017
ms.assetid: 3ea381ee-ac7d-4d62-8c6c-12dc3650879f
ms.openlocfilehash: fd13d4907f1be09440387a36e14ecdc4926ba7e7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594772"
---
# <a name="asmx-client-with-a-wcf-service"></a><span data-ttu-id="7c957-102">带有 WCF 服务的 ASMX 客户端</span><span class="sxs-lookup"><span data-stu-id="7c957-102">ASMX Client with a WCF Service</span></span>

<span data-ttu-id="7c957-103">此示例演示如何使用 Windows Communication Foundation （WCF）创建服务，然后从非 WCF 客户端（如 .ASMX 客户端）访问该服务。</span><span class="sxs-lookup"><span data-stu-id="7c957-103">This sample demonstrates how to create a service using Windows Communication Foundation (WCF) and then access the service from a non-WCF client, such as an ASMX client.</span></span>

> [!NOTE]
> <span data-ttu-id="7c957-104">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="7c957-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="7c957-105">此示例由客户端控制台程序 (.exe) 和 Internet 信息服务 (IIS) 所承载的服务库 (.dll) 组成。</span><span class="sxs-lookup"><span data-stu-id="7c957-105">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="7c957-106">该服务实现定义“请求-答复”通信模式的协定。</span><span class="sxs-lookup"><span data-stu-id="7c957-106">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="7c957-107">该协定由 `ICalculator` 接口定义，此接口公开数学运算（`Add`、`Subtract`、`Multiply` 和 `Divide`）。</span><span class="sxs-lookup"><span data-stu-id="7c957-107">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="7c957-108">ASMX 客户端向某个数学运算发出同步请求，服务使用结果进行回复。</span><span class="sxs-lookup"><span data-stu-id="7c957-108">The ASMX client makes synchronous requests to a math operation and the service replies with the result.</span></span>

<span data-ttu-id="7c957-109">该服务实现一个 `ICalculator` 协定，下面的代码对该协定进行了定义。</span><span class="sxs-lookup"><span data-stu-id="7c957-109">The service implements an `ICalculator` contract as defined in the following code.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"), XmlSerializerFormat]
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

<span data-ttu-id="7c957-110"><xref:System.Runtime.Serialization.DataContractSerializer> 和 <xref:System.Xml.Serialization.XmlSerializer> 将 CLR 类型映射到 XML 表示形式。</span><span class="sxs-lookup"><span data-stu-id="7c957-110">The <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Xml.Serialization.XmlSerializer> map CLR types to an XML representation.</span></span> <span data-ttu-id="7c957-111"><xref:System.Runtime.Serialization.DataContractSerializer> 对某些 XML 表示形式的解释不同于 XmlSerializer。</span><span class="sxs-lookup"><span data-stu-id="7c957-111">The <xref:System.Runtime.Serialization.DataContractSerializer> interprets some XML representations differently than XmlSerializer.</span></span> <span data-ttu-id="7c957-112">当使用 XmlSerializer 时，非 WCF 代理生成器（如 Wsdl.exe）会生成一个更易于使用的接口。</span><span class="sxs-lookup"><span data-stu-id="7c957-112">Non-WCF proxy generators, such as Wsdl.exe, generate a more usable interface when the XmlSerializer is being used.</span></span> <span data-ttu-id="7c957-113"><xref:System.ServiceModel.XmlSerializerFormatAttribute>应用于 `ICalculator` 接口，以确保使用 XMLSERIALIZER 将 CLR 类型映射到 XML。</span><span class="sxs-lookup"><span data-stu-id="7c957-113">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> is applied to the `ICalculator` interface, to ensure that the XmlSerializer is used for mapping CLR types to XML.</span></span> <span data-ttu-id="7c957-114">服务实现计算并返回相应的结果。</span><span class="sxs-lookup"><span data-stu-id="7c957-114">The service implementation calculates and returns the appropriate result.</span></span>

<span data-ttu-id="7c957-115">服务公开单一终结点，以便与使用配置文件 (Web.config) 定义的服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="7c957-115">The service exposes a single endpoint for communicating with the service, defined using a configuration file (Web.config).</span></span> <span data-ttu-id="7c957-116">终结点由地址、绑定和协定组成。</span><span class="sxs-lookup"><span data-stu-id="7c957-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="7c957-117">服务在 Internet 信息服务 (IIS) 主机提供的基地址公开该终结点。</span><span class="sxs-lookup"><span data-stu-id="7c957-117">The service exposes the endpoint at the base address provided by the Internet Information Services (IIS) host.</span></span> <span data-ttu-id="7c957-118">`binding` 属性设置为 basicHttpBinding，它使用 SOAP 1.1（符合 WS-I BasicProfile 1.1）提供 HTTP 通信，如下面的示例配置所示。</span><span class="sxs-lookup"><span data-stu-id="7c957-118">The `binding` attribute is set to basicHttpBinding that provides HTTP communications using SOAP 1.1, which is compliant with WS-I BasicProfile 1.1 as shown in the following sample configuration.</span></span>

```xml
<services>
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc.  -->
    <endpoint address=""
              binding="basicHttpBinding"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />
  </service>
</services>
```

<span data-ttu-id="7c957-119">使用由 Web 服务描述语言（WSDL）实用程序（Wsdl.exe）生成的类型化代理来与 WCF 服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="7c957-119">The ASMX client communicates with the WCF service using a typed proxy that is generated by the Web Services Description Language (WSDL) utility (Wsdl.exe).</span></span> <span data-ttu-id="7c957-120">该类型化代理包含在 generatedClient.cs 文件中。</span><span class="sxs-lookup"><span data-stu-id="7c957-120">The typed proxy is contained in the file generatedClient.cs.</span></span> <span data-ttu-id="7c957-121">WSDL 实用工具为指定的服务检索元数据并生成一个类型化代理，供客户端用来进行通信。</span><span class="sxs-lookup"><span data-stu-id="7c957-121">The WSDL utility retrieves metadata for the specified service and generates a typed proxy for use by a client to communicate.</span></span> <span data-ttu-id="7c957-122">默认情况下，框架不公开任何元数据。</span><span class="sxs-lookup"><span data-stu-id="7c957-122">By default, the framework does not expose any metadata.</span></span> <span data-ttu-id="7c957-123">若要公开生成代理所需的元数据，必须添加 [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md) ，并将其 `httpGetEnabled` 属性设置为， `True` 如下面的配置所示。</span><span class="sxs-lookup"><span data-stu-id="7c957-123">To expose the metadata required to generate the proxy, you must add a [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md) and set its `httpGetEnabled` attribute to `True` as shown in the following configuration.</span></span>

```xml
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <!-- Setting httpGetEnabled to True on the serviceMetadata
           behavior exposes the service's wsdl at <base address>?wsdl :
           http://localhost/servicemodelsamples/service.svc?wsdl -->
      <serviceMetadata httpGetEnabled="True"/>
      <serviceDebug includeExceptionDetailInFaults="False" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```

<span data-ttu-id="7c957-124">在客户端目录中通过命令提示符运行以下命令可以生成该类型化代理。</span><span class="sxs-lookup"><span data-stu-id="7c957-124">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>

```console
wsdl /n:Microsoft.ServiceModel.Samples /o:generatedClient.cs /urlkey:CalculatorServiceAddress http://localhost/servicemodelsamples/service.svc?wsdl
```

<span data-ttu-id="7c957-125">通过使用生成的类型化代理，客户端可以通过配置相应的地址来访问给定的服务终结点。</span><span class="sxs-lookup"><span data-stu-id="7c957-125">By using the generated typed proxy, the client can access a given service endpoint by configuring the appropriate address.</span></span> <span data-ttu-id="7c957-126">客户端使用配置文件 (App.config) 指定要与其通信的终结点。</span><span class="sxs-lookup"><span data-stu-id="7c957-126">The client uses a configuration file (App.config) to specify the endpoint to communicate with.</span></span>

```xml
<appSettings>
  <add key="CalculatorServiceAddress"
       value="http://localhost/ServiceModelSamples/service.svc"/>
</appSettings>
```

<span data-ttu-id="7c957-127">客户端实现构造了类型化代理的一个实例，以开始与服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="7c957-127">The client implementation constructs an instance of the typed proxy to begin communicating with the service.</span></span>

```csharp
// Create a client to the CalculatorService.
using (CalculatorService client = new CalculatorService())
{
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

    // Call the Subtract service operation.
    value1 = 145.00D;
    value2 = 76.54D;
    result = client.Subtract(value1, value2);
    Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

    // Call the Multiply service operation.
    value1 = 9.00D;
    value2 = 81.25D;
    result = client.Multiply(value1, value2);
    Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

    // Call the Divide service operation.
    value1 = 22.00D;
    value2 = 7.00D;
    result = client.Divide(value1, value2);
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);

}

Console.WriteLine();
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

<span data-ttu-id="7c957-128">运行示例时，操作请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="7c957-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="7c957-129">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="7c957-129">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7c957-130">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="7c957-130">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="7c957-131">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="7c957-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="7c957-132">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="7c957-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="7c957-133">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="7c957-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!NOTE]
> <span data-ttu-id="7c957-134">有关传递和返回复杂数据类型的详细信息，请参阅： [Windows 窗体客户端中的数据绑定](data-binding-in-a-windows-forms-client.md)、 [Windows Presentation Foundation 客户端中的数据](data-binding-in-a-wpf-client.md)绑定，以及[ASP.NET 客户端中的数据绑定](data-binding-in-an-aspnet-client.md)</span><span class="sxs-lookup"><span data-stu-id="7c957-134">For more information about passing and returning complex data types see: [Data Binding in a Windows Forms Client](data-binding-in-a-windows-forms-client.md), [Data Binding in a Windows Presentation Foundation Client](data-binding-in-a-wpf-client.md), and [Data Binding in an ASP.NET Client](data-binding-in-an-aspnet-client.md)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7c957-135">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="7c957-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7c957-136">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="7c957-136">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="7c957-137">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="7c957-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7c957-138">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="7c957-138">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\ASMX`

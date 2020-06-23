---
title: 使用 WCF 客户端访问服务
description: 了解如何为 WCF 服务创建 WCF 客户端代理。 客户端应用程序使用客户端代理与服务进行通信。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], consuming services
ms.assetid: d780af9f-73c5-42db-9e52-077a5e4de7fe
ms.openlocfilehash: 25446a89a0b5657d32d77e2d0d57f58f36bed71b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245539"
---
# <a name="accessing-services-using-a-wcf-client"></a><span data-ttu-id="5005d-104">使用 WCF 客户端访问服务</span><span class="sxs-lookup"><span data-stu-id="5005d-104">Accessing Services Using a WCF Client</span></span>

<span data-ttu-id="5005d-105">创建服务后，下一步是创建 WCF 客户端代理。</span><span class="sxs-lookup"><span data-stu-id="5005d-105">After you create a service, the next step is to create a WCF client proxy.</span></span> <span data-ttu-id="5005d-106">客户端应用程序使用 WCF 客户端代理与服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="5005d-106">A client application uses the WCF client proxy to communicate with the service.</span></span> <span data-ttu-id="5005d-107">客户端应用程序通常会导入服务的元数据，以生成可用于调用服务的 WCF 客户端代码。</span><span class="sxs-lookup"><span data-stu-id="5005d-107">Client applications usually import a service's metadata to generate WCF client code that can be used to invoke the service.</span></span>

 <span data-ttu-id="5005d-108">创建 WCF 客户端的基本步骤如下所示：</span><span class="sxs-lookup"><span data-stu-id="5005d-108">The basic steps for creating a WCF client include the following:</span></span>

1. <span data-ttu-id="5005d-109">编译服务代码。</span><span class="sxs-lookup"><span data-stu-id="5005d-109">Compile the service code.</span></span>

2. <span data-ttu-id="5005d-110">生成 WCF 客户端代理。</span><span class="sxs-lookup"><span data-stu-id="5005d-110">Generate the WCF client proxy.</span></span>

3. <span data-ttu-id="5005d-111">实例化 WCF 客户端代理。</span><span class="sxs-lookup"><span data-stu-id="5005d-111">Instantiate the WCF client proxy.</span></span>

<span data-ttu-id="5005d-112">可以使用服务模型元数据实用工具（SvcUtil.exe）手动生成 WCF 客户端代理。有关详细信息[Svcutil.exe](servicemodel-metadata-utility-tool-svcutil-exe.md)，请参阅 ""</span><span class="sxs-lookup"><span data-stu-id="5005d-112">The WCF client proxy can be generated manually by using the Service Model Metadata Utility Tool (SvcUtil.exe) for more information see, [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="5005d-113">还可以使用**添加服务引用**功能在 Visual Studio 中生成 WCF 客户端代理。</span><span class="sxs-lookup"><span data-stu-id="5005d-113">The WCF client proxy can also be generated within Visual Studio using the **Add Service Reference**  feature.</span></span> <span data-ttu-id="5005d-114">若要使用上述两种方法中的一种生成 WCF 客户端代理，必须运行该服务。</span><span class="sxs-lookup"><span data-stu-id="5005d-114">To generate the WCF client proxy using either method the service must be running.</span></span> <span data-ttu-id="5005d-115">如果服务是自承载服务，则必须运行主机。</span><span class="sxs-lookup"><span data-stu-id="5005d-115">If the service is self-hosted you must run the host.</span></span> <span data-ttu-id="5005d-116">如果服务是在 IIS/WAS 中承载的，则无需执行任何其他操作。</span><span class="sxs-lookup"><span data-stu-id="5005d-116">If the service is hosted in IIS/WAS you do not need to do anything else.</span></span>

## <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="5005d-117">ServiceModel 元数据实用工具</span><span class="sxs-lookup"><span data-stu-id="5005d-117">ServiceModel Metadata Utility Tool</span></span>
 <span data-ttu-id="5005d-118">"行[元数据实用工具（Svcutil.exe）](servicemodel-metadata-utility-tool-svcutil-exe.md) " 是一个命令行工具，用于从元数据生成代码。</span><span class="sxs-lookup"><span data-stu-id="5005d-118">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) is a command-line tool for generating code from metadata.</span></span> <span data-ttu-id="5005d-119">下面是一个基本 Svcutil.exe 命令示例。</span><span class="sxs-lookup"><span data-stu-id="5005d-119">The following use is an example of a basic Svcutil.exe command.</span></span>

```console
Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
```

 <span data-ttu-id="5005d-120">另外，还可以使用 Svcutil.exe 来处理文件系统中的 Web 服务描述语言 (WSDL) 和 XML 架构定义语言 (XSD) 文件。</span><span class="sxs-lookup"><span data-stu-id="5005d-120">Alternatively, you can use Svcutil.exe with Web Services Description Language (WSDL) and XML Schema definition language (XSD) files on the file system.</span></span>

```console
Svcutil.exe <list of WSDL and XSD files on file system>
```

 <span data-ttu-id="5005d-121">结果是一个代码文件，其中包含客户端应用程序可用于调用服务的 WCF 客户端代码。</span><span class="sxs-lookup"><span data-stu-id="5005d-121">The result is a code file that contains WCF client code that the client application can use to invoke the service.</span></span>

 <span data-ttu-id="5005d-122">您还可以使用该工具生成配置文件。</span><span class="sxs-lookup"><span data-stu-id="5005d-122">You can also use the tool to generate configuration files.</span></span>

```console
Svcutil.exe <file1 [,file2]>
```

 <span data-ttu-id="5005d-123">如果仅提供了一个文件名，则该文件名是输出文件的名称。</span><span class="sxs-lookup"><span data-stu-id="5005d-123">If only one file name is given, that is the name of the output file.</span></span> <span data-ttu-id="5005d-124">如果提供了两个文件名，则第一个文件是输入配置文件，其内容将与生成的配置合并，然后写出到第二个文件中。</span><span class="sxs-lookup"><span data-stu-id="5005d-124">If two file names are given, then the first file is an input configuration file whose contents are merged with the generated configuration and written out into the second file.</span></span> <span data-ttu-id="5005d-125">有关配置的详细信息，请参阅[配置服务的绑定](configuring-bindings-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="5005d-125">For more information about configuration, see [Configuring Bindings for Services](configuring-bindings-for-wcf-services.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5005d-126">与任何未受保护的网络请求一样，未受保护的元数据请求也会带来一定的风险：如果您不能确定您正在与其进行通信的终结点身份属实，那么您检索的信息有可能是来自于恶意服务的元数据。</span><span class="sxs-lookup"><span data-stu-id="5005d-126">Unsecured metadata requests pose certain risks in the same way that any unsecured network request does: If you are not certain that the endpoint you are communicating with is who it says it is, the information you retrieve might be metadata from a malicious service.</span></span>

## <a name="add-service-reference-in-visual-studio"></a><span data-ttu-id="5005d-127">Visual Studio 中的“添加服务引用”功能</span><span class="sxs-lookup"><span data-stu-id="5005d-127">Add Service Reference in Visual Studio</span></span>

 <span data-ttu-id="5005d-128">在运行服务的情况下，右键单击将包含 WCF 客户端代理的项目，然后选择 "**添加**  >  **服务引用**"。</span><span class="sxs-lookup"><span data-stu-id="5005d-128">With the service running, right click the project that will contain the WCF client proxy and select **Add** > **Service Reference**.</span></span> <span data-ttu-id="5005d-129">在 "**添加服务引用" 对话框**中，键入要调用的服务的 URL，然后单击 "**开始**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="5005d-129">In the **Add Service Reference Dialog**, type in the URL to the service you want to call and click the **Go** button.</span></span> <span data-ttu-id="5005d-130">该对话框将显示在您指定的地址上提供的服务列表。</span><span class="sxs-lookup"><span data-stu-id="5005d-130">The dialog will display a list of services available at the address you specify.</span></span> <span data-ttu-id="5005d-131">双击服务以查看可用的协定和操作，为生成的代码指定命名空间，然后单击 **"确定"** 按钮。</span><span class="sxs-lookup"><span data-stu-id="5005d-131">Double click the service to see the contracts and operations available, specify a namespace for the generated code, and click the **OK** button.</span></span>

## <a name="example"></a><span data-ttu-id="5005d-132">示例</span><span class="sxs-lookup"><span data-stu-id="5005d-132">Example</span></span>
 <span data-ttu-id="5005d-133">下面的代码示例演示为服务创建的一个服务协定。</span><span class="sxs-lookup"><span data-stu-id="5005d-133">The following code example shows a service contract created for a service.</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    // Other methods are not shown here.
}
```

```vb
' Define a service contract.
<ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
Public Interface ICalculator
    <OperationContract()>  _
    Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
    ' Other methods are not shown here.
End Interface
```

 <span data-ttu-id="5005d-134">在 Visual Studio 中的元数据实用工具工具和**添加服务引用**生成以下 WCF 客户端类。</span><span class="sxs-lookup"><span data-stu-id="5005d-134">The ServiceModel Metadata utility tool and **Add Service Reference** in Visual Studio generates the following WCF client class.</span></span> <span data-ttu-id="5005d-135">该类从 <xref:System.ServiceModel.ClientBase%601> 泛型类继承，并实现 `ICalculator` 接口。</span><span class="sxs-lookup"><span data-stu-id="5005d-135">The class inherits from the generic <xref:System.ServiceModel.ClientBase%601> class and implements the `ICalculator` interface.</span></span> <span data-ttu-id="5005d-136">该工具还生成 `ICalculator` 接口（此处未演示）。</span><span class="sxs-lookup"><span data-stu-id="5005d-136">The tool also generates the `ICalculator` interface (not shown here).</span></span>

```csharp
public partial class CalculatorClient : System.ServiceModel.ClientBase<ICalculator>, ICalculator
{
    public CalculatorClient()
    {}

    public CalculatorClient(string endpointConfigurationName) :
            base(endpointConfigurationName)
    {}

    public CalculatorClient(string endpointConfigurationName, string remoteAddress) :
            base(endpointConfigurationName, remoteAddress)
    {}

    public CalculatorClient(string endpointConfigurationName,
        System.ServiceModel.EndpointAddress remoteAddress) :
            base(endpointConfigurationName, remoteAddress)
    {}

    public CalculatorClient(System.ServiceModel.Channels.Binding binding,
        System.ServiceModel.EndpointAddress remoteAddress) :
            base(binding, remoteAddress)
    {}

    public double Add(double n1, double n2)
    {
        return base.Channel.Add(n1, n2);
    }
}
```

```vb
Partial Public Class CalculatorClient
    Inherits System.ServiceModel.ClientBase(Of ICalculator)
    Implements ICalculator

    Public Sub New()
        MyBase.New
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String)
        MyBase.New(endpointConfigurationName)
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String, ByVal remoteAddress As String)
        MyBase.New(endpointConfigurationName, remoteAddress)
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String,
        ByVal remoteAddress As System.ServiceModel.EndpointAddress)
        MyBase.New(endpointConfigurationName, remoteAddress)
    End Sub

    Public Sub New(ByVal binding As System.ServiceModel.Channels.Binding,
        ByVal remoteAddress As System.ServiceModel.EndpointAddress)
        MyBase.New(binding, remoteAddress)
    End Sub

    Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        Implements ICalculator.Add
        Return MyBase.Channel.Add(n1, n2)
    End Function
End Class
```

## <a name="using-the-wcf-client"></a><span data-ttu-id="5005d-137">使用 WCF 客户端</span><span class="sxs-lookup"><span data-stu-id="5005d-137">Using the WCF Client</span></span>
 <span data-ttu-id="5005d-138">若要使用 WCF 客户端，请创建 WCF 客户端的实例，然后调用其方法，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="5005d-138">To use the WCF client, create an instance of the WCF client, and then call its methods, as shown in the following code.</span></span>

```csharp
// Create a client object with the given client endpoint configuration.
CalculatorClient calcClient = new CalculatorClient("CalculatorEndpoint"));
// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = calcClient.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
```

```vb
' Create a client object with the given client endpoint configuration.
Dim calcClient As CalculatorClient = _
New CalculatorClient("CalculatorEndpoint")

' Call the Add service operation.
Dim value1 As Double = 100.00D
Dim value2 As Double = 15.99D
Dim result As Double = calcClient.Add(value1, value2)
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)
```

## <a name="debugging-exceptions-thrown-by-a-client"></a><span data-ttu-id="5005d-139">调试客户端引发的异常</span><span class="sxs-lookup"><span data-stu-id="5005d-139">Debugging Exceptions Thrown by a Client</span></span>

<span data-ttu-id="5005d-140">WCF 客户端引发的许多异常由服务上的异常引起。</span><span class="sxs-lookup"><span data-stu-id="5005d-140">Many exceptions thrown by a WCF client are caused by an exception on the service.</span></span> <span data-ttu-id="5005d-141">这些功能的示例包括：</span><span class="sxs-lookup"><span data-stu-id="5005d-141">Some examples of this are:</span></span>

- <span data-ttu-id="5005d-142"><xref:System.Net.Sockets.SocketException>: 现有连接被远程主机强行关闭。</span><span class="sxs-lookup"><span data-stu-id="5005d-142"><xref:System.Net.Sockets.SocketException>: An existing connection was forcibly closed by the remote host.</span></span>

- <span data-ttu-id="5005d-143"><xref:System.ServiceModel.CommunicationException>: 基础连接意外关闭。</span><span class="sxs-lookup"><span data-stu-id="5005d-143"><xref:System.ServiceModel.CommunicationException>: The underlying connection was closed unexpectedly.</span></span>

- <span data-ttu-id="5005d-144"><xref:System.ServiceModel.CommunicationObjectAbortedException>: 套接字连接已中止。</span><span class="sxs-lookup"><span data-stu-id="5005d-144"><xref:System.ServiceModel.CommunicationObjectAbortedException>: The socket connection was aborted.</span></span> <span data-ttu-id="5005d-145">这可能是由于处理消息时出错或远程主机超过接收超时或者潜在的网络资源问题导致的。</span><span class="sxs-lookup"><span data-stu-id="5005d-145">This could be caused by an error processing your message, a receive time-out being exceeded by the remote host, or an underlying network resource issue.</span></span>

<span data-ttu-id="5005d-146">当发生这些类型的异常时，解决问题的最佳方式是在服务端启用跟踪并确定服务端发生了何种异常。</span><span class="sxs-lookup"><span data-stu-id="5005d-146">When these types of exceptions occur, the best way to solve the problem is to turn on tracing on the service side and determine what exception occurred there.</span></span> <span data-ttu-id="5005d-147">有关跟踪的详细信息，请参阅[跟踪](./diagnostics/tracing/index.md)和[使用跟踪对应用程序进行故障排除](./diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)。</span><span class="sxs-lookup"><span data-stu-id="5005d-147">For more information about tracing, see [Tracing](./diagnostics/tracing/index.md) and [Using Tracing to Troubleshoot Your Application](./diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5005d-148">请参阅</span><span class="sxs-lookup"><span data-stu-id="5005d-148">See also</span></span>

- [<span data-ttu-id="5005d-149">如何：创建客户端</span><span class="sxs-lookup"><span data-stu-id="5005d-149">How to: Create a Client</span></span>](how-to-create-a-wcf-client.md)
- [<span data-ttu-id="5005d-150">如何：使用双工协定访问服务</span><span class="sxs-lookup"><span data-stu-id="5005d-150">How to: Access Services with a Duplex Contract</span></span>](./feature-details/how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="5005d-151">如何：以异步方式调用服务操作</span><span class="sxs-lookup"><span data-stu-id="5005d-151">How to: Call Service Operations Asynchronously</span></span>](./feature-details/how-to-call-wcf-service-operations-asynchronously.md)
- [<span data-ttu-id="5005d-152">如何：使用单向和请求-答复协定访问服务</span><span class="sxs-lookup"><span data-stu-id="5005d-152">How to: Access Services with One-Way and Request-Reply Contracts</span></span>](./feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [<span data-ttu-id="5005d-153">如何：访问 WSE 3.0 服务</span><span class="sxs-lookup"><span data-stu-id="5005d-153">How to: Access a WSE 3.0 Service</span></span>](./feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [<span data-ttu-id="5005d-154">了解生成的客户端代码</span><span class="sxs-lookup"><span data-stu-id="5005d-154">Understanding Generated Client Code</span></span>](./feature-details/understanding-generated-client-code.md)
- [<span data-ttu-id="5005d-155">如何：使用 XmlSerializer 改善 WCF 客户端应用程序的启动时间</span><span class="sxs-lookup"><span data-stu-id="5005d-155">How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer</span></span>](./feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
- [<span data-ttu-id="5005d-156">指定客户端运行时行为</span><span class="sxs-lookup"><span data-stu-id="5005d-156">Specifying Client Run-Time Behavior</span></span>](specifying-client-run-time-behavior.md)
- [<span data-ttu-id="5005d-157">配置客户端行为</span><span class="sxs-lookup"><span data-stu-id="5005d-157">Configuring Client Behaviors</span></span>](configuring-client-behaviors.md)

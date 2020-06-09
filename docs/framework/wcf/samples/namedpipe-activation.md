---
title: NamedPipe 激活
ms.date: 03/30/2017
ms.assetid: f3c0437d-006c-442e-bfb0-6b29216e4e29
ms.openlocfilehash: 8d9a10b94c52514db611144352653b911d109056
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602461"
---
# <a name="namedpipe-activation"></a><span data-ttu-id="19731-102">NamedPipe 激活</span><span class="sxs-lookup"><span data-stu-id="19731-102">NamedPipe Activation</span></span>

<span data-ttu-id="19731-103">本示例演示如何承载使用 Windows 进程激活服务 (WAS) 的服务以激活通过命名管道进行通信的服务。</span><span class="sxs-lookup"><span data-stu-id="19731-103">This sample demonstrates hosting a service that uses Windows Process Activation Service (WAS) to activate a service that communicates over names pipes.</span></span> <span data-ttu-id="19731-104">此示例基于[入门](getting-started-sample.md)，并要求运行 Windows Vista。</span><span class="sxs-lookup"><span data-stu-id="19731-104">This sample is based on the [Getting Started](getting-started-sample.md) and requires Windows Vista to run.</span></span>

> [!NOTE]
> <span data-ttu-id="19731-105">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="19731-105">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="19731-106">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="19731-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="19731-107">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="19731-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="19731-108">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="19731-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="19731-109">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="19731-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\NamedPipeActivation`

## <a name="sample-details"></a><span data-ttu-id="19731-110">示例详细信息</span><span class="sxs-lookup"><span data-stu-id="19731-110">Sample Details</span></span>

<span data-ttu-id="19731-111">本示例由客户端控制台程序 (.exe) 和由 Windows 进程激活服务 (WAS) 激活的辅助进程中承载的服务库 (.dll) 组成。</span><span class="sxs-lookup"><span data-stu-id="19731-111">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by the Windows Process Activation Services (WAS).</span></span> <span data-ttu-id="19731-112">客户端活动显示在控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="19731-112">Client activity is visible in the console window.</span></span>

<span data-ttu-id="19731-113">该服务实现定义“请求-答复”通信模式的协定。</span><span class="sxs-lookup"><span data-stu-id="19731-113">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="19731-114">该协定由 `ICalculator` 接口定义，该接口公开数学运算（加、减、乘和除），如下面的示例代码所示：</span><span class="sxs-lookup"><span data-stu-id="19731-114">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code.</span></span>

```csharp
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

<span data-ttu-id="19731-115">客户端向给定的数学运算发出同步请求，服务实现进行计算并返回相应的结果。</span><span class="sxs-lookup"><span data-stu-id="19731-115">The client makes synchronous requests to a given math operation and the service implementation calculates and returns the appropriate result.</span></span>

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

<span data-ttu-id="19731-116">示例使用经过修改的无安全性的 `netNamedPipeBinding` 绑定。</span><span class="sxs-lookup"><span data-stu-id="19731-116">The sample uses a modified `netNamedPipeBinding` binding with no security.</span></span> <span data-ttu-id="19731-117">绑定是在客户端和服务的配置文件中指定的。</span><span class="sxs-lookup"><span data-stu-id="19731-117">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="19731-118">服务的绑定类型是在终结点元素的 `binding` 属性中指定的，如下面的示例配置所示。</span><span class="sxs-lookup"><span data-stu-id="19731-118">The binding type for the service is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>

<span data-ttu-id="19731-119">如果你想使用安全的命名管道绑定，请将服务器的安全模式更改为所需的安全设置，并在客户端上重新运行 svcutil.exe 以获取更新的客户端配置文件。</span><span class="sxs-lookup"><span data-stu-id="19731-119">If you want use a secured named pipe binding, change the server's security mode to the desired security setting and run svcutil.exe again on the client to obtain an updated client configuration file.</span></span>

```xml
<system.serviceModel>
        <services>
            <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">

        <!-- This endpoint is exposed at the base address provided by host: net.pipe://localhost/servicemodelsamples/service.svc  -->
        <endpoint address=""
                  binding="netNamedPipeBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at net.pipe://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexNamedPipeBinding"
                  contract="IMetadataExchange" />
      </service>
        </services>
        <bindings>
            <netNamedPipeBinding>
                <binding name="Binding1" >
                    <security mode = "None">
                    </security>
                </binding >
            </netNamedPipeBinding>
        </bindings>

    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>
```

<span data-ttu-id="19731-120">客户端的终结点信息按下面的示例代码所示进行配置。</span><span class="sxs-lookup"><span data-stu-id="19731-120">The client’s endpoint information is configured as shown in the following sample code.</span></span>

```xml
<system.serviceModel>

    <client>
      <endpoint name=""
                          address="net.pipe://localhost/servicemodelsamples/service.svc"
                          binding="netNamedPipeBinding"
                          bindingConfiguration="Binding1"
                          contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </client>

    <bindings>

      <!--  Following is the expanded configuration section for a NetNamedPipeBinding.
            Each property is configured with the default value. -->

      <netNamedPipeBinding>
        <binding name="Binding1"
                         maxBufferSize="65536"
                         maxConnections="10">
          <security mode = "None">
          </security>
        </binding >

      </netNamedPipeBinding>
    </bindings>

  </system.serviceModel>
```

<span data-ttu-id="19731-121">运行示例时，操作请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="19731-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="19731-122">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="19731-122">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="19731-123">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="19731-123">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="19731-124">确保已安装 IIS 7.0。</span><span class="sxs-lookup"><span data-stu-id="19731-124">Ensure that IIS 7.0 is installed.</span></span> <span data-ttu-id="19731-125">激活 WAS 需要 IIS 7.0。</span><span class="sxs-lookup"><span data-stu-id="19731-125">IIS 7.0 is required for WAS activation.</span></span>

2. <span data-ttu-id="19731-126">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="19731-126">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

    <span data-ttu-id="19731-127">此外，还必须安装 WCF 非 HTTP 激活组件：</span><span class="sxs-lookup"><span data-stu-id="19731-127">In addition, you must install the WCF non-HTTP activation components:</span></span>

    1. <span data-ttu-id="19731-128">从“开始”菜单中，选择“控制面板” 。</span><span class="sxs-lookup"><span data-stu-id="19731-128">From the **Start** menu, choose **Control Panel**.</span></span>

    2. <span data-ttu-id="19731-129">选择 "**程序和功能**"。</span><span class="sxs-lookup"><span data-stu-id="19731-129">Select **Programs and Features**.</span></span>

    3. <span data-ttu-id="19731-130">单击 **"打开或关闭 Windows 组件"**。</span><span class="sxs-lookup"><span data-stu-id="19731-130">Click **Turn Windows Components on or Off**.</span></span>

    4. <span data-ttu-id="19731-131">展开**Microsoft .NET Framework 3.0**节点并检查**Windows Communication Foundation 非 HTTP 激活**功能。</span><span class="sxs-lookup"><span data-stu-id="19731-131">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>

3. <span data-ttu-id="19731-132">将 Windows 进程激活服务 (WAS) 配置为支持命名管道激活。</span><span class="sxs-lookup"><span data-stu-id="19731-132">Configure the Windows Process Activation Service (WAS) to support named pipe activation.</span></span>

    <span data-ttu-id="19731-133">为方便起见，在位于示例目录中名为 AddNetPipeSiteBinding.cmd 的批处理文件中实现以下两个步骤。</span><span class="sxs-lookup"><span data-stu-id="19731-133">As a convenience, the following two steps are implemented in a batch file called AddNetPipeSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="19731-134">若要支持 net.pipe 激活，必须首先将默认的网站绑定到 net.pipe 协议。</span><span class="sxs-lookup"><span data-stu-id="19731-134">To support net.pipe activation, the default Web site must first be bound to the net.pipe protocol.</span></span> <span data-ttu-id="19731-135">可以通过使用随 IIS 7.0 管理工具集安装的 appcmd.exe 来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="19731-135">This can be done using appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="19731-136">在具有提升权限的（管理员）命令提示符处，运行下列命令。</span><span class="sxs-lookup"><span data-stu-id="19731-136">From an elevated (administrator) command prompt, run the following command.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        -+bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > <span data-ttu-id="19731-137">此命令是单行文本。</span><span class="sxs-lookup"><span data-stu-id="19731-137">This command is a single line of text.</span></span>

        <span data-ttu-id="19731-138">此命令可将 net.pipe 网站绑定添加到默认网站。</span><span class="sxs-lookup"><span data-stu-id="19731-138">This command adds a net.pipe site binding to the default Web site.</span></span>

    2. <span data-ttu-id="19731-139">尽管网站内的所有应用程序共享一个公共 net.pipe 绑定，但是每个应用程序可以单独启用 net.pipe 支持。</span><span class="sxs-lookup"><span data-stu-id="19731-139">Although all applications within a site share a common net.pipe binding, each application can enable net.pipe support individually.</span></span> <span data-ttu-id="19731-140">若要启用 /servicemodelsamples 应用程序的 net.pipe，请在具有提升权限的命令提示符处运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="19731-140">To enable net.pipe for the /servicemodelsamples application, run the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.pipe
        ```

        > [!NOTE]
        > <span data-ttu-id="19731-141">此命令是单行文本。</span><span class="sxs-lookup"><span data-stu-id="19731-141">This command is a single line of text.</span></span>

        <span data-ttu-id="19731-142">此命令允许使用和访问/servicemodelsamples 应用程序 `http://localhost/servicemodelsamples` `net.tcp://localhost/servicemodelsamples` 。</span><span class="sxs-lookup"><span data-stu-id="19731-142">This command enables the /servicemodelsamples application to be accessed using both `http://localhost/servicemodelsamples` and `net.tcp://localhost/servicemodelsamples`.</span></span>

4. <span data-ttu-id="19731-143">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="19731-143">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

5. <span data-ttu-id="19731-144">移除为此示例添加的 net.pipe 网站绑定。</span><span class="sxs-lookup"><span data-stu-id="19731-144">Remove the net.pipe site binding you added for this sample.</span></span>

    <span data-ttu-id="19731-145">为方便起见，在位于示例目录中名为 RemoveNetPipeSiteBinding.cmd 的批处理文件中实现以下两个步骤：</span><span class="sxs-lookup"><span data-stu-id="19731-145">As a convenience, the following two steps are implemented in a batch file called RemoveNetPipeSiteBinding.cmd located in the sample directory:</span></span>

    1. <span data-ttu-id="19731-146">通过在具有提升权限的命令提示符处运行以下命令，从启用的协议列表中移除 net.tcp。</span><span class="sxs-lookup"><span data-stu-id="19731-146">Remove net.tcp from the list of enabled protocols by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="19731-147">必须以单行文本的形式输入此命令。</span><span class="sxs-lookup"><span data-stu-id="19731-147">This command must be entered as a single line of text.</span></span>

    2. <span data-ttu-id="19731-148">通过在具有提升权限的命令提示符处运行以下命令移除 net.tcp 站点绑定。</span><span class="sxs-lookup"><span data-stu-id="19731-148">Remove the net.tcp site binding by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > <span data-ttu-id="19731-149">必须以单行文本的形式键入此命令。</span><span class="sxs-lookup"><span data-stu-id="19731-149">This command must be typed in as a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="19731-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="19731-150">See also</span></span>

- <span data-ttu-id="19731-151">[AppFabric 承载和持久性示例](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="19731-151">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>

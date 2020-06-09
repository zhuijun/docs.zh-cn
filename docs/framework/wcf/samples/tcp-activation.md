---
title: TCP 激活
ms.date: 03/30/2017
ms.assetid: bf8c215c-0228-4f4f-85c2-e33794ec09a7
ms.openlocfilehash: 0fa737adbdc7acc51511557877799c89849149bc
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598653"
---
# <a name="tcp-activation"></a><span data-ttu-id="9a42b-102">TCP 激活</span><span class="sxs-lookup"><span data-stu-id="9a42b-102">TCP Activation</span></span>

<span data-ttu-id="9a42b-103">本示例演示承载一个服务，该服务使用 Windows 进程激活服务 (WAS) 的服务来激活通过 net.tcp 协议通信的服务。</span><span class="sxs-lookup"><span data-stu-id="9a42b-103">This sample demonstrates hosting a service that uses Windows Process Activation Services (WAS) to activate a service that communicates over the net.tcp protocol.</span></span> <span data-ttu-id="9a42b-104">此示例基于[入门](getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="9a42b-104">This sample is based on the [Getting Started](getting-started-sample.md).</span></span>

> [!NOTE]
> <span data-ttu-id="9a42b-105">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="9a42b-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9a42b-106">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="9a42b-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9a42b-107">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="9a42b-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="9a42b-108">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="9a42b-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9a42b-109">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="9a42b-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\TCPActivation`

<span data-ttu-id="9a42b-110">本示例由客户端控制台程序 (.exe) 和用 WAS 激活的工作进程中承载的服务库 (.dll) 组成。</span><span class="sxs-lookup"><span data-stu-id="9a42b-110">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by WAS.</span></span> <span data-ttu-id="9a42b-111">客户端活动显示在控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="9a42b-111">Client activity is visible in the console window.</span></span>

<span data-ttu-id="9a42b-112">该服务实现定义“请求-答复”通信模式的协定。</span><span class="sxs-lookup"><span data-stu-id="9a42b-112">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="9a42b-113">该协定由 `ICalculator` 接口定义，该接口公开数学运算（加、减、乘和除），如下面的示例代码所示：</span><span class="sxs-lookup"><span data-stu-id="9a42b-113">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code:</span></span>

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

<span data-ttu-id="9a42b-114">服务实现计算并返回适当的结果：</span><span class="sxs-lookup"><span data-stu-id="9a42b-114">The service implementation calculates and returns the appropriate result:</span></span>

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

<span data-ttu-id="9a42b-115">本示例使用 net.tcp 绑定的变体，该绑定启用 TCP 端口共享并关闭安全。</span><span class="sxs-lookup"><span data-stu-id="9a42b-115">The sample uses a variant of the net.tcp binding with TCP port sharing enabled and security turned off.</span></span> <span data-ttu-id="9a42b-116">如果您想使用安全的 TCP 绑定，请将服务器的安全模式更改为所需的设置，并在客户端上重新运行 Svcutil.exe 以生成更新客户端配置文件。</span><span class="sxs-lookup"><span data-stu-id="9a42b-116">If you want to use a secured TCP binding, change the server's security mode to the desired setting and re-run Svcutil.exe on the client to generate an update client configuration file.</span></span>

<span data-ttu-id="9a42b-117">下面的示例显示服务的配置：</span><span class="sxs-lookup"><span data-stu-id="9a42b-117">The following sample shows the configuration for the service:</span></span>

```xml
<system.serviceModel>

    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: net.tcp://localhost/servicemodelsamples/service.svc  -->
        <endpoint binding="netTcpBinding" bindingConfiguration="PortSharingBinding"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at net.tcp://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexTcpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <bindings>
      <netTcpBinding>
        <binding name="PortSharingBinding" portSharingEnabled="true">
          <security mode="None" />
        </binding>
      </netTcpBinding>
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

<span data-ttu-id="9a42b-118">客户端的终结点按如下所示的示例代码进行配置：</span><span class="sxs-lookup"><span data-stu-id="9a42b-118">The client's endpoint is configured as shown in the following sample code:</span></span>

```xml
<system.serviceModel>
    <bindings>
        <netTcpBinding>
          <binding name="NetTcpBinding_ICalculator">
            <security mode="None"/>
          </binding>
        </netTcpBinding>
    </bindings>
    <client>
        <endpoint address="net.tcp://localhost/servicemodelsamples/service.svc"
            binding="netTcpBinding" bindingConfiguration="NetTcpBinding_ICalculator"
            contract="Microsoft.ServiceModel.Samples.ICalculator" name="NetTcpBinding_ICalculator" />
    </client>
</system.serviceModel>
```

<span data-ttu-id="9a42b-119">运行示例时，操作请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="9a42b-119">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="9a42b-120">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="9a42b-120">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9a42b-121">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="9a42b-121">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="9a42b-122">确保已安装 IIS 7.0。</span><span class="sxs-lookup"><span data-stu-id="9a42b-122">Ensure that IIS 7.0 is installed.</span></span> <span data-ttu-id="9a42b-123">激活 WAS 需要 IIS 7.0。</span><span class="sxs-lookup"><span data-stu-id="9a42b-123">IIS 7.0 is required for WAS activation.</span></span>

2. <span data-ttu-id="9a42b-124">请确保已[为 Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="9a42b-124">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

    <span data-ttu-id="9a42b-125">此外，还必须安装 WCF 非 HTTP 激活组件：</span><span class="sxs-lookup"><span data-stu-id="9a42b-125">In addition, you must install the WCF non-HTTP activation components:</span></span>

    1. <span data-ttu-id="9a42b-126">从“开始”菜单中，选择“控制面板” 。</span><span class="sxs-lookup"><span data-stu-id="9a42b-126">From the **Start** menu, choose **Control Panel**.</span></span>

    2. <span data-ttu-id="9a42b-127">选择 "**程序和功能**"。</span><span class="sxs-lookup"><span data-stu-id="9a42b-127">Select **Programs and Features**.</span></span>

    3. <span data-ttu-id="9a42b-128">单击 **"打开或关闭 Windows 组件"**。</span><span class="sxs-lookup"><span data-stu-id="9a42b-128">Click **Turn Windows Components on or Off**.</span></span>

    4. <span data-ttu-id="9a42b-129">展开**Microsoft .NET Framework 3.0**节点并检查**Windows Communication Foundation 非 HTTP 激活**功能。</span><span class="sxs-lookup"><span data-stu-id="9a42b-129">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>

3. <span data-ttu-id="9a42b-130">配置 WAS 以支持 TCP 激活。</span><span class="sxs-lookup"><span data-stu-id="9a42b-130">Configure WAS to support TCP activation.</span></span>

    <span data-ttu-id="9a42b-131">为方便起见，在位于示例目录中名为 AddNetTcpSiteBinding.cmd 的批处理文件中实现以下两个步骤。</span><span class="sxs-lookup"><span data-stu-id="9a42b-131">As a convenience, the following two steps are implemented in a batch file called AddNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="9a42b-132">若要支持 net.tcp 激活，必须首先将默认的网站绑定到一个 net.tcp 端口。</span><span class="sxs-lookup"><span data-stu-id="9a42b-132">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="9a42b-133">可以使用随 Internet 信息服务 7.0 (IIS) 管理工具集一起安装的 Appcmd.exe 来完成此操作。</span><span class="sxs-lookup"><span data-stu-id="9a42b-133">This can be done using Appcmd.exe, which is installed with the Internet Information Services 7.0 (IIS) management toolset.</span></span> <span data-ttu-id="9a42b-134">在管理员级别命令提示符处，运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="9a42b-134">From an administrator-level command prompt, run the following command:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!TIP]
        > <span data-ttu-id="9a42b-135">此命令是单行文本。</span><span class="sxs-lookup"><span data-stu-id="9a42b-135">This command is a single line of text.</span></span> <span data-ttu-id="9a42b-136">此命令将 net.tcp 网站绑定添加到以任何主机名侦听 TCP 端口 808 的默认网站。</span><span class="sxs-lookup"><span data-stu-id="9a42b-136">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any hostname.</span></span>

    2. <span data-ttu-id="9a42b-137">尽管网站内的所有应用程序共享一个公共 net.tcp 绑定，但是每个应用程序可以单独启用 net.tcp 支持。</span><span class="sxs-lookup"><span data-stu-id="9a42b-137">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="9a42b-138">若要启用 /servicemodelsamples 应用程序的 net.tcp，请在管理员级别命令提示符处运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="9a42b-138">To enable net.tcp for the /servicemodelsamples application, run the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.tcp
        ```

        > [!NOTE]
        > <span data-ttu-id="9a42b-139">此命令是单行文本。</span><span class="sxs-lookup"><span data-stu-id="9a42b-139">This command is a single line of text.</span></span> <span data-ttu-id="9a42b-140">此命令允许使用和访问/servicemodelsamples 应用程序 `http://localhost/servicemodelsamples` `net.tcp://localhost/servicemodelsamples` 。</span><span class="sxs-lookup"><span data-stu-id="9a42b-140">This command enables the /servicemodelsamples application to be accessed using both `http://localhost/servicemodelsamples` and `net.tcp://localhost/servicemodelsamples`.</span></span>

4. <span data-ttu-id="9a42b-141">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="9a42b-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

5. <span data-ttu-id="9a42b-142">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="9a42b-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

    <span data-ttu-id="9a42b-143">移除为此示例添加的 net.tcp 网站绑定。</span><span class="sxs-lookup"><span data-stu-id="9a42b-143">Remove the net.tcp site binding you added for this sample.</span></span>

    <span data-ttu-id="9a42b-144">为方便起见，在位于示例目录中名为 RemoveNetTcpSiteBinding.cmd 的批处理文件中实现以下两个步骤。</span><span class="sxs-lookup"><span data-stu-id="9a42b-144">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="9a42b-145">通过在管理员级别命令提示符处运行以下命令，可从启用的协议列表移除 net.tcp：</span><span class="sxs-lookup"><span data-stu-id="9a42b-145">Remove net.tcp from the list of enabled protocols by running the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="9a42b-146">必须以单行文本的形式输入此命令。</span><span class="sxs-lookup"><span data-stu-id="9a42b-146">This command must be entered as a single line of text.</span></span>

    2. <span data-ttu-id="9a42b-147">通过在管理员级别命令提示符处运行以下命令，可移除 net.tcp 站点绑定：</span><span class="sxs-lookup"><span data-stu-id="9a42b-147">Remove the net.tcp site binding by running the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > <span data-ttu-id="9a42b-148">必须以单行文本的形式键入此命令。</span><span class="sxs-lookup"><span data-stu-id="9a42b-148">This command must be typed in as a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="9a42b-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9a42b-149">See also</span></span>

- <span data-ttu-id="9a42b-150">[AppFabric 承载和持久性示例](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="9a42b-150">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>

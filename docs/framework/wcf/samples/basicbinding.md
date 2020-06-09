---
title: BasicBinding
ms.date: 03/30/2017
ms.assetid: 86fbeb87-4d89-4b61-9577-867e0ac12945
ms.openlocfilehash: 84bfe78aa9e82b9600c48e0a32514f669fcc7d77
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575649"
---
# <a name="basicbinding"></a><span data-ttu-id="126a4-102">BasicBinding</span><span class="sxs-lookup"><span data-stu-id="126a4-102">BasicBinding</span></span>

<span data-ttu-id="126a4-103">此示例演示如何使用 `basicHttpBinding` 来提供 HTTP 通信以及与第一代和第二代 Web 服务的最大互操作性。</span><span class="sxs-lookup"><span data-stu-id="126a4-103">This sample demonstrates the use of `basicHttpBinding` that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span>

> [!NOTE]
> <span data-ttu-id="126a4-104">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="126a4-104">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="126a4-105">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="126a4-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="126a4-106">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="126a4-106">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="126a4-107">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="126a4-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="126a4-108">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="126a4-108">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\Http`

## <a name="sample-details"></a><span data-ttu-id="126a4-109">示例详细信息</span><span class="sxs-lookup"><span data-stu-id="126a4-109">Sample Details</span></span>

<span data-ttu-id="126a4-110">此示例基于实现计算器服务的[入门](getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="126a4-110">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span>

<span data-ttu-id="126a4-111">若要将基本绑定与默认行为一起使用，只需要使用绑定节的名称。</span><span class="sxs-lookup"><span data-stu-id="126a4-111">To use the basic binding with default behavior, only the binding section name is required.</span></span> <span data-ttu-id="126a4-112">如果要配置基本绑定并更改它的某些设置，则必须定义一个绑定配置。</span><span class="sxs-lookup"><span data-stu-id="126a4-112">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="126a4-113">终结点必须通过使用 <> 元素的属性按名称引用绑定配置 `bindingConfiguration` `endpoint` ，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="126a4-113">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the <`endpoint`> element, as shown in the following sample code.</span></span>

```xml
<services>
    <service
        type="Microsoft.ServiceModel.Samples.CalculatorService"
        behaviorConfiguration="CalculatorServiceBehavior">
       <endpoint address=""
             binding="basicHttpBinding"
             bindingConfiguration="Binding1"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
</services>
```

<span data-ttu-id="126a4-114">在此示例中，定义了绑定配置并将其命名为 `"Binding1"`，如下面的代码示例所示。</span><span class="sxs-lookup"><span data-stu-id="126a4-114">In this sample, the binding configuration is named `"Binding1"` and is defined as shown in the following code example.</span></span>

```xml
<bindings>
   <basicHttpBinding>
      <binding name="Binding1"
               hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Text"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true" >
         <security mode="None" />
      </binding>
   </basicHttpBinding>
</bindings>
```

<span data-ttu-id="126a4-115">绑定元素提供用来设置如下内容的属性：主机名比较模式、最大消息大小、代理选项、超时、消息编码和其他选项。</span><span class="sxs-lookup"><span data-stu-id="126a4-115">The binding element provides attributes for setting the host name comparison mode, maximum message size, proxy options, timeouts, message encoding, and other options.</span></span>

<span data-ttu-id="126a4-116">运行示例时，操作请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="126a4-116">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="126a4-117">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="126a4-117">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="126a4-118">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="126a4-118">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="126a4-119">使用以下命令安装 ASP.NET 4.0。</span><span class="sxs-lookup"><span data-stu-id="126a4-119">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="126a4-120">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="126a4-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="126a4-121">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="126a4-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="126a4-122">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="126a4-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

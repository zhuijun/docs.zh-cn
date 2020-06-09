---
title: 使用传输安全的 BasicBinding
ms.date: 03/30/2017
ms.assetid: f49b1de6-0254-4362-8ef2-fccd8ff9688b
ms.openlocfilehash: 822a7dcb20c6559a70ba77719b6e7a62633bb31c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575662"
---
# <a name="basicbinding-with-transport-security"></a><span data-ttu-id="ab75c-102">使用传输安全的 BasicBinding</span><span class="sxs-lookup"><span data-stu-id="ab75c-102">BasicBinding with Transport Security</span></span>

<span data-ttu-id="ab75c-103">本示例演示对基本绑定使用 SSL 传输安全。</span><span class="sxs-lookup"><span data-stu-id="ab75c-103">This sample demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="ab75c-104">此示例基于实现计算器服务的[入门](getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="ab75c-104">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ab75c-105">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="ab75c-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ab75c-106">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="ab75c-106">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="ab75c-107">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="ab75c-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ab75c-108">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="ab75c-108">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\TransportSecurity`

## <a name="sample-details"></a><span data-ttu-id="ab75c-109">示例详细信息</span><span class="sxs-lookup"><span data-stu-id="ab75c-109">Sample Details</span></span>

<span data-ttu-id="ab75c-110">默认情况下，基本绑定支持 HTTP 通信。</span><span class="sxs-lookup"><span data-stu-id="ab75c-110">By default, the basic binding supports HTTP communication.</span></span> <span data-ttu-id="ab75c-111">本示例演示如何为基本绑定启用传输安全。</span><span class="sxs-lookup"><span data-stu-id="ab75c-111">The sample shows how to enable transport security for the basic binding.</span></span> <span data-ttu-id="ab75c-112">在运行此示例之前，必须通过使用 Web 服务器证书向导来创建证书并分配此证书。</span><span class="sxs-lookup"><span data-stu-id="ab75c-112">Before you run the sample, you must create a certificate and assign it by using the Web Server Certificate Wizard.</span></span>

> [!NOTE]
> <span data-ttu-id="ab75c-113">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="ab75c-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="ab75c-114">示例中的程序代码与[入门](getting-started-sample.md)服务的程序代码相同。</span><span class="sxs-lookup"><span data-stu-id="ab75c-114">The program code in the sample is identical to that of the [Getting Started](getting-started-sample.md) service.</span></span> <span data-ttu-id="ab75c-115">配置文件设置中的终结点定义和绑定定义已进行修改，可以启用安全通信，如下面的示例配置所示。</span><span class="sxs-lookup"><span data-stu-id="ab75c-115">The endpoint definition and binding definition in the configuration file settings are modified to enable secure communication, as shown in the following sample configuration.</span></span>

```xml
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
   </services>
  <bindings>
    <basicHttpBinding>
      <!-- Configure basicHttpBinding with Transport security -->
      <!-- mode and clientCredentialType set to None. -->
      <binding name="Binding1">
        <security mode="Transport">
          <transport clientCredentialType="None"/>
        </security>
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```

<span data-ttu-id="ab75c-116">由于本示例中使用的证书是用 Makecert 创建的测试证书，因此，当你尝试在浏览器中访问 HTTPS：地址（例如）时，将出现安全 `https://localhost/servicemodelsamples/service.svc` 警报。</span><span class="sxs-lookup"><span data-stu-id="ab75c-116">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an HTTPS: address in your browser, such as `https://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="ab75c-117">若要允许 Windows Communication Foundation （WCF）客户端使用测试证书，则会向客户端添加一些额外的代码以禁止显示安全警报。</span><span class="sxs-lookup"><span data-stu-id="ab75c-117">To allow the Windows Communication Foundation (WCF) client to work with a test certificate, some additional code is added to the client to suppress the security alert.</span></span> <span data-ttu-id="ab75c-118">使用真正的证书时不需要此代码和附带的类。</span><span class="sxs-lookup"><span data-stu-id="ab75c-118">This code, and the accompanying class, is not necessary when using real certificates.</span></span>

```csharp
// This code is required only for test certificates such as those
// created by Makecert.exe.
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");
```

<span data-ttu-id="ab75c-119">运行示例时，操作请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="ab75c-119">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ab75c-120">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="ab75c-120">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ab75c-121">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="ab75c-121">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="ab75c-122">使用以下命令安装 ASP.NET 4.0：</span><span class="sxs-lookup"><span data-stu-id="ab75c-122">Install ASP.NET 4.0 using the following command:</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="ab75c-123">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="ab75c-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="ab75c-124">确保已执行[Internet Information Services （IIS）服务器证书安装说明](iis-server-certificate-installation-instructions.md)。</span><span class="sxs-lookup"><span data-stu-id="ab75c-124">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](iis-server-certificate-installation-instructions.md).</span></span>

4. <span data-ttu-id="ab75c-125">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="ab75c-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

5. <span data-ttu-id="ab75c-126">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="ab75c-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

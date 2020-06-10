---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: a78eac52095d3f647efdacc9104a75e46651f389
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596366"
---
# <a name="wshttpbinding"></a><span data-ttu-id="e4e15-102">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="e4e15-102">WSHttpBinding</span></span>
<span data-ttu-id="e4e15-103">此示例演示如何使用 Windows Communication Foundation （WCF）实现典型的服务和典型的客户端。</span><span class="sxs-lookup"><span data-stu-id="e4e15-103">This sample demonstrates how to implement a typical service and a typical client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="e4e15-104">此示例由客户端控制台程序 (client.exe) 和 Internet 信息服务 (IIS) 所承载的服务库组成。</span><span class="sxs-lookup"><span data-stu-id="e4e15-104">This sample consists of a client console program (client.exe) and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="e4e15-105">该服务实现定义“请求-答复”通信模式的协定。</span><span class="sxs-lookup"><span data-stu-id="e4e15-105">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="e4e15-106">该协定由 `ICalculator` 接口定义，此接口公开数学运算（加、减、乘和除）。</span><span class="sxs-lookup"><span data-stu-id="e4e15-106">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="e4e15-107">客户端向给定的数学运算发出同步请求，服务使用结果进行回复。</span><span class="sxs-lookup"><span data-stu-id="e4e15-107">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="e4e15-108">客户端活动显示在控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="e4e15-108">Client activity is visible in the console window.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e4e15-109">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="e4e15-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e4e15-110">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="e4e15-110">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="e4e15-111">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="e4e15-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e4e15-112">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="e4e15-112">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
> <span data-ttu-id="e4e15-113">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="e4e15-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e4e15-114">此示例使用公开 `ICalculator` 协定 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="e4e15-114">This sample exposes the `ICalculator` contract using the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="e4e15-115">此绑定的配置已在 Web.config 文件中展开。</span><span class="sxs-lookup"><span data-stu-id="e4e15-115">The configuration of this binding has been expanded in the Web.config file.</span></span>  
  
```xml
<bindings>  
  <wsHttpBinding>  
    <!--The following is the expanded configuration section for a-->  
    <!--WSHttpBinding. Each property is configured with the default-->
    <!--value. See the ReliableSession, TransactionFlow, -->  
    <!--TransportSecurity, and MessageSecurity samples in the WS -->  
    <!--directory to learn how to configure these features. -->  
    <binding name="Binding1"  
              bypassProxyOnLocal="false"
              transactionFlow="false"
              hostNameComparisonMode="StrongWildcard"  
              maxBufferPoolSize="524288"
              maxReceivedMessageSize="65536"  
              messageEncoding="Text"
              textEncoding="utf-8"
              useDefaultWebProxy="true"  
              allowCookies="false">  
      <reliableSession ordered="true"
                       inactivityTimeout="00:10:00"  
                       enabled="false" />  
      <security mode="Message">  
        <message clientCredentialType="Windows"
                 negotiateServiceCredential="true"  
                 algorithmSuite="Default"
                 establishSecurityContext="true" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="e4e15-116">在基 `binding` 元素上，通过 `maxReceivedMessageSize` 值可以配置传入消息的最大大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="e4e15-116">On the base `binding` element, the `maxReceivedMessageSize` value lets you configure the maximum size of an incoming message (in bytes).</span></span> <span data-ttu-id="e4e15-117">通过 `hostNameComparisonMode` 值，可以配置向服务多路分解消息时是否考虑主机名。</span><span class="sxs-lookup"><span data-stu-id="e4e15-117">The `hostNameComparisonMode` value lets you configure whether the hostname is considered when de-multiplexing messages to the service.</span></span> <span data-ttu-id="e4e15-118">通过 `messageEncoding` 值可以配置是对消息使用文本还是 MTOM 编码。</span><span class="sxs-lookup"><span data-stu-id="e4e15-118">The `messageEncoding` value lets you configure whether to use Text or MTOM encoding for messages.</span></span> <span data-ttu-id="e4e15-119">通过 `textEncoding` 值可以为消息配置字符编码。</span><span class="sxs-lookup"><span data-stu-id="e4e15-119">The `textEncoding` value lets you configure the character encoding for messages.</span></span> <span data-ttu-id="e4e15-120">通过 `bypassProxyOnLocal` 值可以配置是否对本地通信使用 HTTP 协议。</span><span class="sxs-lookup"><span data-stu-id="e4e15-120">The `bypassProxyOnLocal` value lets you configure whether to use an HTTP proxy for local communication.</span></span> <span data-ttu-id="e4e15-121">通过 `transactionFlow` 值可以配置是否对当前事务进行流处理（如果为事务流配置了操作）。</span><span class="sxs-lookup"><span data-stu-id="e4e15-121">The `transactionFlow` value configures whether the current transaction is flowed (if an operation is configured for transaction flow).</span></span>  
  
 <span data-ttu-id="e4e15-122">在 [\<reliableSession>](../../configure-apps/file-schema/wcf/reliablesession.md) 元素上，启用的布尔值配置是否启用可靠会话。</span><span class="sxs-lookup"><span data-stu-id="e4e15-122">On the [\<reliableSession>](../../configure-apps/file-schema/wcf/reliablesession.md) element, the enabled Boolean value configures whether reliable sessions are enabled.</span></span> <span data-ttu-id="e4e15-123">`ordered` 值配置是否保留消息顺序。</span><span class="sxs-lookup"><span data-stu-id="e4e15-123">The `ordered` value configures whether message ordering is preserved.</span></span> <span data-ttu-id="e4e15-124">`inactivityTimeout` 值配置会话在出错之前可以闲置的时间。</span><span class="sxs-lookup"><span data-stu-id="e4e15-124">The `inactivityTimeout` value configures how long a session can be idle before being faulted.</span></span>  
  
 <span data-ttu-id="e4e15-125">在上 [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) ， `mode` 值配置应该使用的安全模式。</span><span class="sxs-lookup"><span data-stu-id="e4e15-125">On the [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md), the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="e4e15-126">在此示例中，将使用消息安全性，这就是在 [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) 中指定的原因 [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="e4e15-126">In this sample, messages security is being used, which is why the [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) is specified inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="e4e15-127">运行示例时，操作请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="e4e15-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e4e15-128">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="e4e15-128">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e4e15-129">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="e4e15-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e4e15-130">使用以下命令安装 ASP.NET 4.0。</span><span class="sxs-lookup"><span data-stu-id="e4e15-130">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="e4e15-131">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="e4e15-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="e4e15-132">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="e4e15-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="e4e15-133">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="e4e15-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  

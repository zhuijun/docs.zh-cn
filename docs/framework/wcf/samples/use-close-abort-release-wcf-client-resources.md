---
title: 使用“关闭”和“中止”发布 WCF 客户端资源
description: 当网络出现故障时，Dispose 会失败并引发异常。 这可能会导致意外的行为。 相反，请使用 Close 和 Abort 在网络发生故障时释放客户端资源。
ms.date: 11/12/2018
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
ms.openlocfilehash: b338b760f461d7b773f43dd1f5e6dbce98f9e15a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599914"
---
# <a name="close-and-abort-release-resources-safely-when-network-connections-have-dropped"></a><span data-ttu-id="adaf6-105">网络连接中断时，安全关闭和中止发布资源</span><span class="sxs-lookup"><span data-stu-id="adaf6-105">Close and Abort release resources safely when network connections have dropped</span></span>

<span data-ttu-id="adaf6-106">此示例演示如何使用 `Close` 和 `Abort` 方法在使用类型化客户端时清理资源。</span><span class="sxs-lookup"><span data-stu-id="adaf6-106">This sample demonstrates using the `Close` and `Abort` methods to clean up resources when using a typed client.</span></span> <span data-ttu-id="adaf6-107">`using`当网络连接不稳定时，语句将导致异常。</span><span class="sxs-lookup"><span data-stu-id="adaf6-107">The `using` statement causes exceptions when the network connection is not robust.</span></span> <span data-ttu-id="adaf6-108">此示例基于实现计算器服务的[入门](getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="adaf6-108">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="adaf6-109">在此示例中，客户端是一个控制台应用程序 (.exe)，服务是由 Internet 信息服务 (IIS) 承载的。</span><span class="sxs-lookup"><span data-stu-id="adaf6-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>

> [!NOTE]
> <span data-ttu-id="adaf6-110">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="adaf6-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="adaf6-111">本示例演示对类型化客户端使用 C# 的“using”语句时发生的两个常见问题以及发生异常后用于正确清除的代码。</span><span class="sxs-lookup"><span data-stu-id="adaf6-111">This sample shows two of the common problems that occur when using the C# "using" statement with typed clients, as well as code that correctly cleans up after exceptions.</span></span>

<span data-ttu-id="adaf6-112">C# 的“using”语句会导致调用 `Dispose`()。</span><span class="sxs-lookup"><span data-stu-id="adaf6-112">The C# "using" statement results in a call to `Dispose`().</span></span> <span data-ttu-id="adaf6-113">它等效于 `Close`()，当发生网络错误时可能会引发异常。</span><span class="sxs-lookup"><span data-stu-id="adaf6-113">This is the same as `Close`(), which may throw exceptions when a network error occurs.</span></span> <span data-ttu-id="adaf6-114">由于对 `Dispose`() 的调用是在“using”块的右大括号处隐式发生的，因此导致异常的根源往往会被编写代码和阅读代码的人所忽略。</span><span class="sxs-lookup"><span data-stu-id="adaf6-114">Because the call to `Dispose`() happens implicitly at the closing brace of the "using" block, this source of exceptions is likely to go unnoticed both by people writing the code and reading the code.</span></span> <span data-ttu-id="adaf6-115">这是应用程序错误的潜在根源。</span><span class="sxs-lookup"><span data-stu-id="adaf6-115">This represents a potential source of application errors.</span></span>

<span data-ttu-id="adaf6-116">`DemonstrateProblemUsingCanThrow` 方法中演示的第一个问题是，右大括号引发异常，不执行右大括号后面的代码：</span><span class="sxs-lookup"><span data-stu-id="adaf6-116">The first problem, illustrated in the `DemonstrateProblemUsingCanThrow` method, is that the closing brace throws an exception and the code after the closing brace does not execute:</span></span>

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
} // <-- this line might throw
Console.WriteLine("Hope this code wasn't important, because it might not happen.");
```

<span data-ttu-id="adaf6-117">即使 using 块中的内容不会引发异常或可以捕获 using 块中的所有异常，`Console.WriteLine` 也不会发生，因为右大括号处的隐式 `Dispose`() 调用可能会引发异常。</span><span class="sxs-lookup"><span data-stu-id="adaf6-117">Even if nothing inside the using block throws an exception or all exceptions inside the using block are caught, the `Console.WriteLine` might not happen because the implicit `Dispose`() call at the closing brace might throw an exception.</span></span>

<span data-ttu-id="adaf6-118">`DemonstrateProblemUsingCanThrowAndMask` 方法中演示的第二个问题是右大括号引发异常的另一种隐含情况：</span><span class="sxs-lookup"><span data-stu-id="adaf6-118">The second problem, illustrated in the `DemonstrateProblemUsingCanThrowAndMask` method, is another implication of the closing brace throwing an exception:</span></span>

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
    throw new ApplicationException("Hope this exception was not important, because "+
                                   "it might be masked by the Close exception.");
} // <-- this line might throw an exception.
```

<span data-ttu-id="adaf6-119">因为 `Dispose`() 发生在“finally”块内，因此在 `ApplicationException`() 失败的情况下，`Dispose` 不会发生在 using 块外。</span><span class="sxs-lookup"><span data-stu-id="adaf6-119">Because the `Dispose`() occurs inside a "finally" block, the `ApplicationException` is never seen outside the using block if the `Dispose`() fails.</span></span> <span data-ttu-id="adaf6-120">如果外面的代码必须要知道 `ApplicationException` 发生的时间，则“using”构造可能会因为屏蔽此异常而导致问题。</span><span class="sxs-lookup"><span data-stu-id="adaf6-120">If the code outside must know about when the `ApplicationException` occurs, the "using" construct may cause problems by masking this exception.</span></span>

<span data-ttu-id="adaf6-121">最后，示例演示 `DemonstrateCleanupWithExceptions` 中发生异常时如何正确清除异常。</span><span class="sxs-lookup"><span data-stu-id="adaf6-121">Finally, the sample demonstrates how to clean up correctly when exceptions occur in `DemonstrateCleanupWithExceptions`.</span></span> <span data-ttu-id="adaf6-122">本示例使用 try/catch 块报告错误并调用 `Abort`。</span><span class="sxs-lookup"><span data-stu-id="adaf6-122">This uses a try/catch block to report errors and call `Abort`.</span></span> <span data-ttu-id="adaf6-123">有关从客户端调用捕获异常的详细信息，请参阅[预期异常](expected-exceptions.md)示例。</span><span class="sxs-lookup"><span data-stu-id="adaf6-123">See the [Expected Exceptions](expected-exceptions.md) sample for more details about catching exceptions from client calls.</span></span>

```csharp
try
{
    ...
    client.Close();
}
catch (CommunicationException e)
{
    ...
    client.Abort();
}
catch (TimeoutException e)
{
    ...
    client.Abort();
}
catch (Exception e)
{
    ...
    client.Abort();
    throw;
}
```

> [!NOTE]
> <span data-ttu-id="adaf6-124">using 语句和 ServiceHost：许多自承载的应用程序主要用于承载服务，并且 ServiceHost.Close 很少引发异常，因此这样的应用程序可以安全地一起使用 using 语句和 ServiceHost。</span><span class="sxs-lookup"><span data-stu-id="adaf6-124">The using statement and ServiceHost: Many self-hosting applications do little more than host a service, and ServiceHost.Close rarely throws an exception, so such applications can safely use the using statement with ServiceHost.</span></span> <span data-ttu-id="adaf6-125">但请注意，ServiceHost.Close 可能引发 `CommunicationException`，因此，如果关闭 ServiceHost 以后应用程序继续执行，则应避免使用 using 语句并遵循前面提供的模式。</span><span class="sxs-lookup"><span data-stu-id="adaf6-125">However, be aware that ServiceHost.Close can throw a `CommunicationException`, so if your application continues after closing the ServiceHost, you should avoid the using statement and follow the pattern previously given.</span></span>

<span data-ttu-id="adaf6-126">运行示例时，在客户端控制台窗口中显示操作响应和异常。</span><span class="sxs-lookup"><span data-stu-id="adaf6-126">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>

<span data-ttu-id="adaf6-127">客户端进程运行三个方案，每个方案都会尝试调用 `Divide`。</span><span class="sxs-lookup"><span data-stu-id="adaf6-127">The client process runs three scenarios, each of which attempts to call `Divide`.</span></span> <span data-ttu-id="adaf6-128">第一个方案演示由于 `Dispose`() 中发生异常而跳过代码。</span><span class="sxs-lookup"><span data-stu-id="adaf6-128">The first scenario demonstrates code being skipped because of an exception from `Dispose`().</span></span> <span data-ttu-id="adaf6-129">第二个方案演示由于 `Dispose`() 中发生异常而屏蔽重要异常。</span><span class="sxs-lookup"><span data-stu-id="adaf6-129">The second scenario demonstrates an important exception being masked because of an exception from `Dispose`().</span></span> <span data-ttu-id="adaf6-130">第三个方案演示如何正确清除。</span><span class="sxs-lookup"><span data-stu-id="adaf6-130">The third scenario demonstrates correct clean up.</span></span>

<span data-ttu-id="adaf6-131">客户端进程的预期输出为：</span><span class="sxs-lookup"><span data-stu-id="adaf6-131">The expected output from the client process is:</span></span>

```console
=
= Demonstrating problem:  closing brace of using statement can throw.
=
Got System.ServiceModel.CommunicationException from Divide.
Got System.ServiceModel.Security.MessageSecurityException
=
= Demonstrating problem:  closing brace of using statement can mask other Exceptions.
=
Got System.ServiceModel.CommunicationException from Divide.
Got System.ServiceModel.Security.MessageSecurityException
=
= Demonstrating cleanup with Exceptions.
=
Calling client.Add(0.0, 0.0);
        client.Add(0.0, 0.0); returned 0
Calling client.Divide(0.0, 0.0);
Got System.ServiceModel.CommunicationException from Divide.

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="adaf6-132">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="adaf6-132">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="adaf6-133">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="adaf6-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="adaf6-134">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="adaf6-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="adaf6-135">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="adaf6-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="adaf6-136">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="adaf6-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="adaf6-137">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="adaf6-137">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="adaf6-138">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="adaf6-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="adaf6-139">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="adaf6-139">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`

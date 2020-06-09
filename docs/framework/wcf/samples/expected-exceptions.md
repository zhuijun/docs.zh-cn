---
title: 预期异常
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: d8e3c024eb69fe22ec27f3e3697bc4fc7b4ee121
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600524"
---
# <a name="expected-exceptions"></a><span data-ttu-id="e3a5c-102">预期异常</span><span class="sxs-lookup"><span data-stu-id="e3a5c-102">Expected Exceptions</span></span>
<span data-ttu-id="e3a5c-103">此示例演示如何在使用类型化客户端时捕获预期异常。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-103">This sample demonstrates how to catch expected exceptions when using a typed client.</span></span> <span data-ttu-id="e3a5c-104">此示例基于实现计算器服务的[入门](getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-104">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="e3a5c-105">在此示例中，客户端是一个控制台应用程序 (.exe)，服务是由 Internet 信息服务 (IIS) 承载的。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-105">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e3a5c-106">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e3a5c-107">此示例演示如何捕获和处理正确的程序所必须处理的两个预期异常类型：`TimeoutException` 和 `CommunicationException`。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-107">This sample demonstrates catching and handling the two expected exception types that correct programs must handle: `TimeoutException` and `CommunicationException`.</span></span>  
  
 <span data-ttu-id="e3a5c-108">Windows Communication Foundation （WCF）客户端上的通信方法引发的异常可能是预期的，也可能是意外的。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-108">Exceptions that are thrown from communication methods on a Windows Communication Foundation (WCF) client are either expected or unexpected.</span></span> <span data-ttu-id="e3a5c-109">意外异常包括灾难性故障（如 `OutOfMemoryException`）和编程错误（如 `ArgumentNullException` 或 `InvalidOperationException`）。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-109">Unexpected exceptions include catastrophic failures like `OutOfMemoryException` and programming errors like `ArgumentNullException` or `InvalidOperationException`.</span></span> <span data-ttu-id="e3a5c-110">通常不会有任何有用的方法来处理意外错误，因此，通常不应在调用 WCF 客户端通信方法时捕获它们。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-110">Typically there is no useful way to handle unexpected errors, so typically you should not catch them when calling a WCF client communication method.</span></span>  
  
 <span data-ttu-id="e3a5c-111">WCF 客户端上通信方法的预期异常包括 `TimeoutException` 、 `CommunicationException` 和的任何派生类 `CommunicationException` 。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-111">Expected exceptions from communication methods on a WCF client include `TimeoutException`, `CommunicationException`, and any derived class of `CommunicationException`.</span></span> <span data-ttu-id="e3a5c-112">这表示在通信过程中出现的问题，可通过中止 WCF 客户端并报告通信故障来安全地处理这些问题。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-112">These indicate a problem during communication that can be safely handled by aborting the WCF client and reporting a communication failure.</span></span> <span data-ttu-id="e3a5c-113">因为外部因素可能导致任何应用程序中出现这些错误，所以正确的应用程序必须捕获这些异常并在发生异常时进行恢复。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-113">Because external factors can cause these errors in any application, correct applications must catch these exceptions and recover when they occur.</span></span>  
  
 <span data-ttu-id="e3a5c-114">客户端可以引发 `CommunicationException` 的几个派生类。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-114">There are several derived classes of `CommunicationException` that a client can throw.</span></span> <span data-ttu-id="e3a5c-115">在某些情况下，应用程序也会捕获其中的某些类以执行特殊的处理，而让其他类作为 `CommunicationException` 进行处理。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-115">In some cases, applications also catch some of these to do special handling, but let the others be handled as a `CommunicationException`.</span></span> <span data-ttu-id="e3a5c-116">这可以通过先捕获比较具体的异常类型，然后在稍后的 catch 子句中捕获 `CommunicationException` 来完成。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-116">This can be accomplished by catching the more specific exception type first and then catching `CommunicationException` in a later catch-clause.</span></span>  
  
 <span data-ttu-id="e3a5c-117">调用客户端通信方法的代码必须捕获 `TimeoutException` 和 `CommunicationException`。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-117">Code that calls a client communication method must catch the `TimeoutException` and `CommunicationException`.</span></span> <span data-ttu-id="e3a5c-118">处理此类错误的一种方法是中止客户端并报告通信故障。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-118">One way to handle such errors is to abort the client and report the communication failure.</span></span>  
  
```csharp
try  
{  
    ...  
    double result = client.Add(value1, value2);  
    ...  
    client.Close();  
}  
catch (TimeoutException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
catch (CommunicationException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="e3a5c-119">如果发生预期异常，客户端或许可以继续使用，或许无法继续使用。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-119">If an expected exception occurs, the client may or may not be usable afterwards.</span></span> <span data-ttu-id="e3a5c-120">若要确定客户端是否仍然可以使用，请检查 `State` 属性是否为 `CommunicationState`.Opened。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-120">To determine if the client is still usable, check that the `State` property is `CommunicationState`.Opened.</span></span> <span data-ttu-id="e3a5c-121">如果此属性仍然处于打开状态，则客户端仍然可以使用。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-121">If it is still opened, then it is still usable.</span></span> <span data-ttu-id="e3a5c-122">否则，则应中止客户端并释放对其的所有引用。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-122">Otherwise you should abort the client and release all references to it.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="e3a5c-123">您可能注意到具有会话的客户端在出现异常后常常不能再使用，而没有会话的客户端在出现异常后常常可以继续使用。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-123">You may observe that clients that have a session are often no longer usable after an exception, and clients that do not have a session are often still usable after an exception.</span></span> <span data-ttu-id="e3a5c-124">但是，这些情况都是不能保证的，因此如果您希望在出现异常后继续使用客户端，您的应用程序应检查 `State` 属性以验证客户端是否仍然处于打开状态。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-124">However, neither of these is guaranteed, so if you want to try to continue using the client after an exception your application should check the `State` property to verify the client is still opened.</span></span>  
  
 <span data-ttu-id="e3a5c-125">运行示例时，在客户端控制台窗口中显示操作响应和异常。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-125">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="e3a5c-126">客户端进程运行两个方案，每个方案都尝试先调用 `Add`，再调用 `Divide`。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-126">The client process runs two scenarios, each of which attempts to call `Add` followed by `Divide`.</span></span> <span data-ttu-id="e3a5c-127">第一个方案通过在调用 `Divide` 之前中止客户端来模拟网络问题。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-127">The first scenario simulates a network issue by aborting the client before making the call to `Divide`.</span></span> <span data-ttu-id="e3a5c-128">第二个方案通过将超时设置为太短的时间而使方法无法完成，从而导致超时情况的发生。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-128">The second scenario causes a timeout condition by setting the timeout too short for the method to complete.</span></span> <span data-ttu-id="e3a5c-129">客户端进程的预期输出为：</span><span class="sxs-lookup"><span data-stu-id="e3a5c-129">The expected output from the client process is:</span></span>  
  
```output
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e3a5c-130">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="e3a5c-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e3a5c-131">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e3a5c-132">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="e3a5c-133">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e3a5c-134">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e3a5c-135">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="e3a5c-135">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="e3a5c-136">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="e3a5c-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e3a5c-137">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="e3a5c-137">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  

---
title: 默认服务行为
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
ms.openlocfilehash: 4da3deff69930dba7249e0651f820b448b837862
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592445"
---
# <a name="default-service-behavior"></a><span data-ttu-id="b01c6-102">默认服务行为</span><span class="sxs-lookup"><span data-stu-id="b01c6-102">Default Service Behavior</span></span>
<span data-ttu-id="b01c6-103">此示例演示如何配置服务行为设置。</span><span class="sxs-lookup"><span data-stu-id="b01c6-103">This sample demonstrates how service behavior settings can be configured.</span></span> <span data-ttu-id="b01c6-104">该示例基于实现服务协定的[入门](getting-started-sample.md) `ICalculator` 。</span><span class="sxs-lookup"><span data-stu-id="b01c6-104">The sample is based on the [Getting Started](getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="b01c6-105">此示例使用 <xref:System.ServiceModel.ServiceBehaviorAttribute> 和 <xref:System.ServiceModel.OperationBehaviorAttribute> 属性来显式定义服务行为和操作行为。</span><span class="sxs-lookup"><span data-stu-id="b01c6-105">This sample explicitly defines service behaviors and operation behaviors using the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes.</span></span> <span data-ttu-id="b01c6-106">你可以在配置文件中配置行为，也可以通过代码强制配置行为（如此示例所示）。</span><span class="sxs-lookup"><span data-stu-id="b01c6-106">You can configure behaviors in configuration files or imperatively in code (as this sample demonstrates).</span></span>  
  
 <span data-ttu-id="b01c6-107">在此示例中，客户端是一个控制台应用程序 (.exe)，服务是由 Internet 信息服务 (IIS) 承载的。</span><span class="sxs-lookup"><span data-stu-id="b01c6-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b01c6-108">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="b01c6-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b01c6-109">服务类使用 <xref:System.ServiceModel.ServiceBehaviorAttribute> 和 <xref:System.ServiceModel.OperationBehaviorAttribute> 来指定行为，如下面的代码示例所示。</span><span class="sxs-lookup"><span data-stu-id="b01c6-109">The service class specifies behaviors with the <xref:System.ServiceModel.ServiceBehaviorAttribute> and the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following code sample.</span></span> <span data-ttu-id="b01c6-110">指定的所有值均为默认值。</span><span class="sxs-lookup"><span data-stu-id="b01c6-110">All values specified are the defaults.</span></span>  
  
```csharp
[ServiceBehavior(  
    AutomaticSessionShutdown=true,  
    ConcurrencyMode=ConcurrencyMode.Single,  
    InstanceContextMode=InstanceContextMode.PerSession,  
    IncludeExceptionDetailInFaults=false,  
    UseSynchronizationContext=true,  
    ValidateMustUnderstand=true)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(  
        TransactionAutoComplete=true,  
        TransactionScopeRequired=false,  
        Impersonation=ImpersonationOption.NotAllowed)]  
    public double Add(double n1, double n2)  
    {  
        System.Threading.Thread.Sleep(1600);  
        return n1 + n2;  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="b01c6-111">服务行为是使用 <xref:System.ServiceModel.ServiceBehaviorAttribute> 属性指定的。</span><span class="sxs-lookup"><span data-stu-id="b01c6-111">Service behaviors are specified with the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span> <span data-ttu-id="b01c6-112">下表描述了其中的一些行为。</span><span class="sxs-lookup"><span data-stu-id="b01c6-112">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="b01c6-113">服务行为</span><span class="sxs-lookup"><span data-stu-id="b01c6-113">Service behavior</span></span>|<span data-ttu-id="b01c6-114">描述</span><span class="sxs-lookup"><span data-stu-id="b01c6-114">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|<span data-ttu-id="b01c6-115">在客户端的请求下自动关闭会话。</span><span class="sxs-lookup"><span data-stu-id="b01c6-115">Automatically shuts down a session at the client's request.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|<span data-ttu-id="b01c6-116">指定每个服务实例的并发模式。</span><span class="sxs-lookup"><span data-stu-id="b01c6-116">Specifies the concurrency mode for each service instance.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|<span data-ttu-id="b01c6-117">指定实例上下文模式。</span><span class="sxs-lookup"><span data-stu-id="b01c6-117">Specifies the instance context mode.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|<span data-ttu-id="b01c6-118">确定是否使用所提供的同步上下文（如果已设置该上下文）。</span><span class="sxs-lookup"><span data-stu-id="b01c6-118">Determines whether to use the provided synchronization context, if one is set.</span></span> <span data-ttu-id="b01c6-119">在希望控制是否在 Windows 窗体应用程序中使用 `WindowsFormsSynchronizationContext` 时使用该上下文。</span><span class="sxs-lookup"><span data-stu-id="b01c6-119">Use this when you want to control whether to use a `WindowsFormsSynchronizationContext` in Windows Forms applications.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|<span data-ttu-id="b01c6-120">确定是否要将常规未处理执行异常转换为 `Fault<string>` 并将其作为错误消息发送。</span><span class="sxs-lookup"><span data-stu-id="b01c6-120">Determines whether general unhandled execution exceptions are to be converted into a `Fault<string>` and sent as a fault message.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|<span data-ttu-id="b01c6-121">指定事务的隔离级别。</span><span class="sxs-lookup"><span data-stu-id="b01c6-121">Specifies the isolation level for transactions.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|<span data-ttu-id="b01c6-122">确定意外消息头是否会导致错误。</span><span class="sxs-lookup"><span data-stu-id="b01c6-122">Determines whether unexpected message headers cause an error condition.</span></span>|  
  
 <span data-ttu-id="b01c6-123">操作行为是使用 <xref:System.ServiceModel.OperationBehaviorAttribute> 属性指定的。</span><span class="sxs-lookup"><span data-stu-id="b01c6-123">Operation behaviors are specified by using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="b01c6-124">下表描述了其中的一些行为。</span><span class="sxs-lookup"><span data-stu-id="b01c6-124">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="b01c6-125">操作行为</span><span class="sxs-lookup"><span data-stu-id="b01c6-125">Operation Behavior</span></span>|<span data-ttu-id="b01c6-126">描述</span><span class="sxs-lookup"><span data-stu-id="b01c6-126">Description</span></span>|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|<span data-ttu-id="b01c6-127">确定服务操作的完成是否提交当前事务。</span><span class="sxs-lookup"><span data-stu-id="b01c6-127">Determines whether service operation completion commits the current transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|<span data-ttu-id="b01c6-128">确定服务操作是否在客户端流动的事务中登记。</span><span class="sxs-lookup"><span data-stu-id="b01c6-128">Determines whether the service operation enlists in a client-flowed transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|<span data-ttu-id="b01c6-129">确定服务操作是否模拟调用方的标识。</span><span class="sxs-lookup"><span data-stu-id="b01c6-129">Determines whether the service operation impersonates the caller's identity.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|<span data-ttu-id="b01c6-130">确定是否在服务操作调用的开头或结尾处回收服务实例。</span><span class="sxs-lookup"><span data-stu-id="b01c6-130">Determines whether service instances are recycled at the start or end of the service operation call.</span></span>|  
  
 <span data-ttu-id="b01c6-131">运行示例时，操作请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="b01c6-131">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="b01c6-132">调用之间的延迟是在服务操作中对 `System.Threading.Thread.Sleep()` 进行调用的结果。</span><span class="sxs-lookup"><span data-stu-id="b01c6-132">The delay between the calls is the result of the calls to `System.Threading.Thread.Sleep()` made in the service operations.</span></span> <span data-ttu-id="b01c6-133">其余的行为示例更详细地说明这些行为。</span><span class="sxs-lookup"><span data-stu-id="b01c6-133">The rest of the behavior samples explain these behaviors in more detail.</span></span> <span data-ttu-id="b01c6-134">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="b01c6-134">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b01c6-135">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="b01c6-135">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b01c6-136">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="b01c6-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b01c6-137">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="b01c6-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b01c6-138">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="b01c6-138">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b01c6-139">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="b01c6-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b01c6-140">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="b01c6-140">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b01c6-141">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="b01c6-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b01c6-142">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="b01c6-142">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  

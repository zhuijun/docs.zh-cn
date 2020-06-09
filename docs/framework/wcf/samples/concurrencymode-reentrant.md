---
title: 可重入的 ConcurrencyMode
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: 67e719afd40b52f37c777cf9791291a16878592f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600083"
---
# <a name="concurrencymode-reentrant"></a><span data-ttu-id="a735f-102">可重入的 ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="a735f-102">ConcurrencyMode Reentrant</span></span>
<span data-ttu-id="a735f-103">本示例演示对服务实现使用 ConcurrencyMode.Reentrant 的必要性和含义。</span><span class="sxs-lookup"><span data-stu-id="a735f-103">This sample demonstrates the necessity and implications of using ConcurrencyMode.Reentrant on a service implementation.</span></span> <span data-ttu-id="a735f-104">ConcurrencyMode.Reentrant 暗示服务（或回调）只在给定时间处理一个消息（类似于 `ConcurencyMode.Single`）。</span><span class="sxs-lookup"><span data-stu-id="a735f-104">ConcurrencyMode.Reentrant implies that the service (or callback) processes only one message at a given time (analogous to `ConcurencyMode.Single`).</span></span> <span data-ttu-id="a735f-105">为了确保线程安全，Windows Communication Foundation （WCF）会锁定 `InstanceContext` 处理消息，以便不能处理其他消息。</span><span class="sxs-lookup"><span data-stu-id="a735f-105">To ensure thread safety, Windows Communication Foundation (WCF) locks the `InstanceContext` processing a message so that no other messages can be processed.</span></span> <span data-ttu-id="a735f-106">在处于可重入模式的情况下，`InstanceContext` 将仅在服务进行传出调用之前解除锁定，从而允许后续调用（可按示例中的演示重入），并在下次进入服务时被锁定。</span><span class="sxs-lookup"><span data-stu-id="a735f-106">In case of Reentrant mode, the `InstanceContext` is unlocked just before the service makes an outgoing call thereby allowing the subsequent call, (which can be reentrant as demonstrated in the sample) to get the lock next time it comes in to the service.</span></span> <span data-ttu-id="a735f-107">为了演示此行为，示例演示了客户端和服务如何使用双工协定相互发送消息。</span><span class="sxs-lookup"><span data-stu-id="a735f-107">To demonstrate the behavior, the sample shows how a client and service can send messages between each other using a duplex contract.</span></span>  
  
 <span data-ttu-id="a735f-108">定义的协定是双工协定，其 `Ping` 方法由服务实现，其回调方法 `Pong` 由客户端实现。</span><span class="sxs-lookup"><span data-stu-id="a735f-108">The contract defined is a duplex contract with the `Ping` method being implemented by the service and the callback method `Pong` being implemented by the client.</span></span> <span data-ttu-id="a735f-109">客户端用滴答计数调用服务的 `Ping` 方法，从而启动调用。</span><span class="sxs-lookup"><span data-stu-id="a735f-109">A client invokes the server's `Ping` method with a tick count thereby initiating the call.</span></span> <span data-ttu-id="a735f-110">服务检查滴答计数是否等于 0，然后调用回调 `Pong` 方法，同时递减滴答计数。</span><span class="sxs-lookup"><span data-stu-id="a735f-110">The service checks whether the tick count is not equal to 0 and then invokes the callbacks `Pong` method while decrementing the tick count.</span></span> <span data-ttu-id="a735f-111">以上过程通过示例中的以下代码完成。</span><span class="sxs-lookup"><span data-stu-id="a735f-111">This is done by the following code in the sample.</span></span>  
  
```csharp
public void Ping(int ticks)  
{  
     Console.WriteLine("Ping: Ticks = " + ticks);  
     //Keep pinging back and forth till Ticks reaches 0.  
     if (ticks != 0)  
     {  
         OperationContext.Current.GetCallbackChannel<IPingPongCallback>().Pong((ticks - 1));  
     }  
}  
```  
  
 回调的 `Pong` 实现与 `Ping` 实现具有相同的逻辑。 也就是说，该实现检查滴答计数是否不为零，然后对回调通道（在本例中为用于发送原始 `Ping` 消息的通道）调用 `Ping` 方法，并使滴答计数减 1。 当滴答计数达到 0 时，该方法返回，从而将所有回复解包回启动该调用的客户端进行的第一个调用。 <span data-ttu-id="a735f-115">回调实现中显示了此过程。</span><span class="sxs-lookup"><span data-stu-id="a735f-115">This is shown in the callback implementation.</span></span>  
  
```csharp
public void Pong(int ticks)  
{  
    Console.WriteLine("Pong: Ticks = " + ticks);  
    if (ticks != 0)  
    {  
        //Retrieve the Callback  Channel (in this case the Channel which was used to send the  
        //original message) and make an outgoing call until ticks reaches 0.  
        IPingPong channel = OperationContext.Current.GetCallbackChannel<IPingPong>();  
        channel.Ping((ticks - 1));  
    }  
}  
```  
  
 `Ping` 和 `Pong` 方法都是请求/答复，这意味着对 `Ping` 的调用返回前，对 `CallbackChannel<T>.Pong()` 的第一个调用不会返回。 在客户端上，在由 `Pong` 方法进行的下一个 `Ping` 调用返回前，该方法不会返回。 <span data-ttu-id="a735f-118">由于回调和服务在答复挂起请求之前，必须进行传出请求/答复调用，因此这两个实现必须使用 ConcurrencyMode.Reentrant 行为进行标记。</span><span class="sxs-lookup"><span data-stu-id="a735f-118">Because both the callback and the service must make outgoing request/reply calls before they can reply for the pending request, both the implementations must be marked with the ConcurrencyMode.Reentrant behavior.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a735f-119">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="a735f-119">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a735f-120">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="a735f-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a735f-121">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="a735f-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a735f-122">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="a735f-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="a735f-123">演示</span><span class="sxs-lookup"><span data-stu-id="a735f-123">Demonstrates</span></span>  
 <span data-ttu-id="a735f-124">若要运行示例，请生成客户端和服务器项目。</span><span class="sxs-lookup"><span data-stu-id="a735f-124">To run the sample, build the client and server projects.</span></span> <span data-ttu-id="a735f-125">然后打开两个命令窗口，并将目录更改为 \<sample> \CS\Service\bin\debug 和 \<sample> \CS\Client\bin\debug 目录。</span><span class="sxs-lookup"><span data-stu-id="a735f-125">Then open two command windows and change the directories to the \<sample>\CS\Service\bin\debug and \<sample>\CS\Client\bin\debug directories.</span></span> <span data-ttu-id="a735f-126">然后，键入 `service.exe` ，然后调用该客户端，并将其初始值作为输入参数传递。</span><span class="sxs-lookup"><span data-stu-id="a735f-126">Then start the service by typing `service.exe` and then invoke the Client.exe with the initial value of ticks passed as an input argument.</span></span> <span data-ttu-id="a735f-127">显示了 10 次滴答的示例输出。</span><span class="sxs-lookup"><span data-stu-id="a735f-127">A sample output for 10 ticks is shown.</span></span>  
  
```console  
Prompt>Service.exe  
ServiceHost Started. Press Enter to terminate service.  
Ping: Ticks = 10  
Ping: Ticks = 8  
Ping: Ticks = 6  
Ping: Ticks = 4  
Ping: Ticks = 2  
Ping: Ticks = 0  
  
Prompt>Client.exe 10  
Pong: Ticks = 9  
Pong: Ticks = 7  
Pong: Ticks = 5  
Pong: Ticks = 3  
Pong: Ticks = 1  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="a735f-128">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="a735f-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a735f-129">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="a735f-129">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a735f-130">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="a735f-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a735f-131">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="a735f-131">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  

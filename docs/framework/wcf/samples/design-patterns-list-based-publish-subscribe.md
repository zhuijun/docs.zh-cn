---
title: 设计模式：基于列表的发布-订阅
ms.date: 03/30/2017
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
ms.openlocfilehash: 5aaea5b0def544f8b3e963d71e269592b9b40784
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592341"
---
# <a name="design-patterns-list-based-publish-subscribe"></a><span data-ttu-id="ebf57-102">设计模式：基于列表的发布-订阅</span><span class="sxs-lookup"><span data-stu-id="ebf57-102">Design Patterns: List-Based Publish-Subscribe</span></span>
<span data-ttu-id="ebf57-103">此示例演示了作为 Windows Communication Foundation （WCF）程序实现的基于列表的发布-订阅模式。</span><span class="sxs-lookup"><span data-stu-id="ebf57-103">This sample illustrates the List-based Publish-Subscribe pattern implemented as a Windows Communication Foundation (WCF) program.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ebf57-104">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="ebf57-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ebf57-105">基于列表的发布-订阅设计模式在 Microsoft 模式 & 实践发布、[集成模式](https://docs.microsoft.com/previous-versions/msp-n-p/ff647309(v=pandp.10))中进行了介绍。</span><span class="sxs-lookup"><span data-stu-id="ebf57-105">The List-based Publish-Subscribe design pattern is described in the Microsoft Patterns & Practices publication, [Integration Patterns](https://docs.microsoft.com/previous-versions/msp-n-p/ff647309(v=pandp.10)).</span></span> <span data-ttu-id="ebf57-106">发布-订阅模式可以向已经订阅某一信息主题的接收者群体传递信息。</span><span class="sxs-lookup"><span data-stu-id="ebf57-106">The Publish-Subscribe pattern passes information to a collection of recipients who have subscribed to an information topic.</span></span> <span data-ttu-id="ebf57-107">基于列表的发布-订阅可维护一份订户列表。</span><span class="sxs-lookup"><span data-stu-id="ebf57-107">List-based publish-subscribe maintains a list of subscribers.</span></span> <span data-ttu-id="ebf57-108">如果有要共享的信息，则会向列表上的每个订户发送一份副本。</span><span class="sxs-lookup"><span data-stu-id="ebf57-108">When there is information to share, a copy is sent to each subscriber on the list.</span></span> <span data-ttu-id="ebf57-109">本示例演示基于列表的动态发布-订阅模式，在此模式下客户端可以根据需要随时订阅或取消订阅。</span><span class="sxs-lookup"><span data-stu-id="ebf57-109">This sample demonstrates a dynamic list-based publish-subscribe pattern, where clients can subscribe or unsubscribe as often as required.</span></span>  
  
 <span data-ttu-id="ebf57-110">基于列表的发布-订阅示例由客户端、服务和数据源程序组成。</span><span class="sxs-lookup"><span data-stu-id="ebf57-110">The List-based Publish-Subscribe sample consists of a client, a service, and a data source program.</span></span> <span data-ttu-id="ebf57-111">可以有多个客户端和多个数据源程序同时运行。</span><span class="sxs-lookup"><span data-stu-id="ebf57-111">There can be more than one client and more than one data source program running.</span></span> <span data-ttu-id="ebf57-112">客户端订阅服务、接收通知，然后取消订阅。</span><span class="sxs-lookup"><span data-stu-id="ebf57-112">Clients subscribe to the service, receive notifications, and unsubscribe.</span></span> <span data-ttu-id="ebf57-113">数据源程序向服务发送将与所有当前订户共享的信息。</span><span class="sxs-lookup"><span data-stu-id="ebf57-113">Data source programs send information to the service to be shared with all current subscribers.</span></span>  
  
 <span data-ttu-id="ebf57-114">在本示例中，客户端和数据源是控制台程序（.exe 文件），而服务是 Internet 信息服务 (IIS) 所承载的库 (.dll)。</span><span class="sxs-lookup"><span data-stu-id="ebf57-114">In this sample, the client and data source are console programs (.exe files) and the service is a library (.dll) hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="ebf57-115">客户端和数据源活动在桌面上可见。</span><span class="sxs-lookup"><span data-stu-id="ebf57-115">Client and data source activity are visible on the desktop.</span></span>  
  
 <span data-ttu-id="ebf57-116">服务使用双工通信。</span><span class="sxs-lookup"><span data-stu-id="ebf57-116">The service uses duplex communication.</span></span> <span data-ttu-id="ebf57-117">`ISampleContract` 服务协定与 `ISampleClientCallback` 回调协定成对出现。</span><span class="sxs-lookup"><span data-stu-id="ebf57-117">The `ISampleContract` service contract is paired up with an `ISampleClientCallback` callback contract.</span></span> <span data-ttu-id="ebf57-118">服务实现 Subscribe 和 Unsubscribe 服务操作，客户端使用这些操作加入或离开订户列表。</span><span class="sxs-lookup"><span data-stu-id="ebf57-118">The service implements Subscribe and Unsubscribe service operations, which clients use to join or leave the list of subscribers.</span></span> <span data-ttu-id="ebf57-119">服务还实现 `PublishPriceChange` 服务操作，数据源程序调用该操作来向服务提供新信息。</span><span class="sxs-lookup"><span data-stu-id="ebf57-119">The service also implements the `PublishPriceChange` service operation, which the data source program calls to provide the service with new information.</span></span> <span data-ttu-id="ebf57-120">客户端程序实现 `PriceChange` 服务操作，服务调用该操作向所有订户通知价格更改。</span><span class="sxs-lookup"><span data-stu-id="ebf57-120">The client program implements the `PriceChange` service operation, which the service calls to notify all subscribers of a price change.</span></span>  
  
```csharp  
// Create a service contract and define the service operations.  
// NOTE: The service operations must be declared explicitly.  
[ServiceContract(SessionMode=SessionMode.Required,  
      CallbackContract=typeof(ISampleClientContract))]  
public interface ISampleContract  
{  
    [OperationContract(IsOneWay = false, IsInitiating=true)]  
    void Subscribe();  
    [OperationContract(IsOneWay = false, IsTerminating=true)]  
    void Unsubscribe();  
    [OperationContract(IsOneWay = true)]  
    void PublishPriceChange(string item, double price,
                                     double change);  
}  
  
public interface ISampleClientContract  
{  
    [OperationContract(IsOneWay = true)]  
    void PriceChange(string item, double price, double change);  
}  
```  
  
 <span data-ttu-id="ebf57-121">服务使用 .NET Framework 事件作为向所有订户通知新信息的机制。</span><span class="sxs-lookup"><span data-stu-id="ebf57-121">The service uses a .NET Framework event as the mechanism to inform all subscribers about new information.</span></span> <span data-ttu-id="ebf57-122">如果客户端通过调用 Subscribe 加入服务，服务将提供一个事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="ebf57-122">When a client joins the service by calling Subscribe, it provides an event handler.</span></span> <span data-ttu-id="ebf57-123">如果客户端离开，服务将取消其事件处理程序对事件的订阅。</span><span class="sxs-lookup"><span data-stu-id="ebf57-123">When a client leaves, it unsubscribes its event handler from the event.</span></span> <span data-ttu-id="ebf57-124">当数据源调用服务以报告价格变化时，服务将引发事件。</span><span class="sxs-lookup"><span data-stu-id="ebf57-124">When a data source calls the service to report a price change, the service raises the event.</span></span> <span data-ttu-id="ebf57-125">这将调用服务的每个实例（订阅服务的每个客户端一个实例），并导致其事件处理程序执行。</span><span class="sxs-lookup"><span data-stu-id="ebf57-125">This calls each instance of the service, one for each client that has subscribed, and causes their event handlers to execute.</span></span> <span data-ttu-id="ebf57-126">每个事件处理程序都通过其回调函数向其客户端传递信息。</span><span class="sxs-lookup"><span data-stu-id="ebf57-126">Each event handler passes the information to its client through its callback function.</span></span>  
  
```csharp
public class PriceChangeEventArgs : EventArgs  
    {  
        public string Item;  
        public double Price;  
        public double Change;  
    }  
  
    // The Service implementation implements your service contract.  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    public class SampleService : ISampleContract  
    {  
        public static event PriceChangeEventHandler PriceChangeEvent;  
        public delegate void PriceChangeEventHandler(object sender, PriceChangeEventArgs e);  
  
        ISampleClientContract callback = null;  
  
        PriceChangeEventHandler priceChangeHandler = null;  
  
        //Clients call this service operation to subscribe.  
        //A price change event handler is registered for this client instance.  
  
        public void Subscribe()  
        {  
            callback = OperationContext.Current.GetCallbackChannel<ISampleClientContract>();  
            priceChangeHandler = new PriceChangeEventHandler(PriceChangeHandler);  
            PriceChangeEvent += priceChangeHandler;  
        }  
  
        //Clients call this service operation to unsubscribe.  
        //The previous price change event handler is unregistered.  
  
        public void Unsubscribe()  
        {  
            PriceChangeEvent -= priceChangeHandler;  
        }  
  
        //Information source clients call this service operation to report a price change.  
        //A price change event is raised. The price change event handlers for each subscriber will execute.  
  
        public void PublishPriceChange(string item, double price, double change)  
        {  
            PriceChangeEventArgs e = new PriceChangeEventArgs();  
            e.Item = item;  
            e.Price = price;  
            e.Change = change;  
            PriceChangeEvent(this, e);  
        }  
  
        //This event handler runs when a PriceChange event is raised.  
        //The client's PriceChange service operation is invoked to provide notification about the price change.  
  
        public void PriceChangeHandler(object sender, PriceChangeEventArgs e)  
        {  
            callback.PriceChange(e.Item, e.Price, e.Change);  
        }  
  
    }  
```  
  
 <span data-ttu-id="ebf57-127">运行示例时，将启动多个客户端。</span><span class="sxs-lookup"><span data-stu-id="ebf57-127">When you run the sample, launch several clients.</span></span> <span data-ttu-id="ebf57-128">这些客户端都将订阅服务。</span><span class="sxs-lookup"><span data-stu-id="ebf57-128">The clients subscribe to the service.</span></span> <span data-ttu-id="ebf57-129">然后运行数据源程序，它将信息发送到服务。</span><span class="sxs-lookup"><span data-stu-id="ebf57-129">Then run the data source program, which sends information to the service.</span></span> <span data-ttu-id="ebf57-130">服务将信息传递给所有订户。</span><span class="sxs-lookup"><span data-stu-id="ebf57-130">The service passes on the information to all subscribers.</span></span> <span data-ttu-id="ebf57-131">您可以在每个客户端控制台上查看活动并确认已收到信息。</span><span class="sxs-lookup"><span data-stu-id="ebf57-131">You can see activity on each client console confirming that the information has been received.</span></span> <span data-ttu-id="ebf57-132">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="ebf57-132">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="ebf57-133">设置和生成示例</span><span class="sxs-lookup"><span data-stu-id="ebf57-133">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="ebf57-134">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="ebf57-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ebf57-135">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="ebf57-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="ebf57-136">在同一计算机上运行示例</span><span class="sxs-lookup"><span data-stu-id="ebf57-136">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="ebf57-137">通过输入以下地址来测试是否可以使用浏览器访问服务： `http://localhost/servicemodelsamples/service.svc` 。</span><span class="sxs-lookup"><span data-stu-id="ebf57-137">Test that you can access the service using a browser by entering the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="ebf57-138">在响应中应显示确认页。</span><span class="sxs-lookup"><span data-stu-id="ebf57-138">A confirmation page should be displayed in response.</span></span>  
  
2. <span data-ttu-id="ebf57-139">\\从 \client\bin 的特定于语言的文件夹中运行客户端。</span><span class="sxs-lookup"><span data-stu-id="ebf57-139">Run Client.exe from \client\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="ebf57-140">客户端活动将显示在客户端控制台窗口上。</span><span class="sxs-lookup"><span data-stu-id="ebf57-140">Client activity is displayed on the client console window.</span></span> <span data-ttu-id="ebf57-141">启动多个客户端。</span><span class="sxs-lookup"><span data-stu-id="ebf57-141">Launch several clients.</span></span>  
  
3. <span data-ttu-id="ebf57-142">\\从 \datasource\bin 的特定于语言的文件夹中运行 Datasource。</span><span class="sxs-lookup"><span data-stu-id="ebf57-142">Run Datasource.exe from \datasource\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="ebf57-143">数据源活动将显示在控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="ebf57-143">Data source activity is displayed on the console window.</span></span> <span data-ttu-id="ebf57-144">数据源向服务发送信息后，信息应传递到每个客户端。</span><span class="sxs-lookup"><span data-stu-id="ebf57-144">Once the data source sends information to the service, it should be passed on to each client.</span></span>  
  
4. <span data-ttu-id="ebf57-145">如果客户端、数据源和服务程序无法通信，请参阅[WCF 示例的故障排除提示](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="ebf57-145">If the client, data source, and service programs are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="ebf57-146">跨计算机运行示例</span><span class="sxs-lookup"><span data-stu-id="ebf57-146">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="ebf57-147">安装服务计算机：</span><span class="sxs-lookup"><span data-stu-id="ebf57-147">Set up the service machine:</span></span>  
  
    1. <span data-ttu-id="ebf57-148">在服务计算机上创建一个名为 ServiceModelSamples 的虚拟目录。</span><span class="sxs-lookup"><span data-stu-id="ebf57-148">On the service machine, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="ebf57-149">[Windows Communication Foundation 示例的一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)中的批处理文件 setupvroot.bat 可用于创建磁盘目录和虚拟目录。</span><span class="sxs-lookup"><span data-stu-id="ebf57-149">The batch file Setupvroot.bat from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md) can be used to create the disk directory and virtual directory.</span></span>  
  
    2. <span data-ttu-id="ebf57-150">从 %SystemDrive%\Inetpub\wwwroot\servicemodelsamples 中将服务程序文件复制到服务计算机上的 ServiceModelSamples 虚拟目录中。</span><span class="sxs-lookup"><span data-stu-id="ebf57-150">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service machine.</span></span> <span data-ttu-id="ebf57-151">确保在 \bin 目录中包括这些文件。</span><span class="sxs-lookup"><span data-stu-id="ebf57-151">Be sure to include the files in the \bin directory.</span></span>  
  
    3. <span data-ttu-id="ebf57-152">测试是否可使用浏览器从客户端计算机访问服务。</span><span class="sxs-lookup"><span data-stu-id="ebf57-152">Test that you can access the service from the client machine using a browser.</span></span>  
  
2. <span data-ttu-id="ebf57-153">安装客户端计算机：</span><span class="sxs-lookup"><span data-stu-id="ebf57-153">Set up the client machines:</span></span>  
  
    1. <span data-ttu-id="ebf57-154">将 \client\bin\ 文件夹（在语言特定文件夹内）中的客户端程序文件复制到客户端计算机上。</span><span class="sxs-lookup"><span data-stu-id="ebf57-154">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machines.</span></span>  
  
    2. <span data-ttu-id="ebf57-155">在每个客户端配置文件中，更改终结点定义的地址值以与服务的新地址相匹配。</span><span class="sxs-lookup"><span data-stu-id="ebf57-155">In each client configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="ebf57-156">在地址中将任何对“localhost”的引用替换为一个完全限定的域名。</span><span class="sxs-lookup"><span data-stu-id="ebf57-156">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
3. <span data-ttu-id="ebf57-157">安装数据源计算机：</span><span class="sxs-lookup"><span data-stu-id="ebf57-157">Set up the data source machine:</span></span>  
  
    1. <span data-ttu-id="ebf57-158">将 \datasource\bin\ 文件夹（在语言特定文件夹内）中的数据源程序文件复制到数据源计算机上。</span><span class="sxs-lookup"><span data-stu-id="ebf57-158">Copy the data source program files from the \datasource\bin\ folder, under the language-specific folder, to the data source machine.</span></span>  
  
    2. <span data-ttu-id="ebf57-159">在数据源配置文件中，更改终结点定义的地址值以与服务的新地址相匹配。</span><span class="sxs-lookup"><span data-stu-id="ebf57-159">In the data source configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="ebf57-160">在地址中将任何对“localhost”的引用替换为一个完全限定的域名。</span><span class="sxs-lookup"><span data-stu-id="ebf57-160">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
4. <span data-ttu-id="ebf57-161">在客户端计算机上的命令提示符下启动 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="ebf57-161">On the client machines, launch Client.exe from a command prompt.</span></span>  
  
5. <span data-ttu-id="ebf57-162">在数据源计算机上的命令提示符下启动 Datasource.exe。</span><span class="sxs-lookup"><span data-stu-id="ebf57-162">On the data source machine, launch Datasource.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ebf57-163">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="ebf57-163">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ebf57-164">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="ebf57-164">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ebf57-165">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="ebf57-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ebf57-166">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="ebf57-166">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  

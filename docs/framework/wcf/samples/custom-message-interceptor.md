---
title: 自定义消息拦截器
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: b9a517d0f8ada3680d49cd5ab0b13fa9e4d85402
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600057"
---
# <a name="custom-message-interceptor"></a><span data-ttu-id="02092-102">自定义消息拦截器</span><span class="sxs-lookup"><span data-stu-id="02092-102">Custom Message Interceptor</span></span>
<span data-ttu-id="02092-103">此示例演示通道扩展模型的使用。</span><span class="sxs-lookup"><span data-stu-id="02092-103">This sample demonstrates the use of the channel extensibility model.</span></span> <span data-ttu-id="02092-104">特别是，演示如何实现可创建通道工厂和通道侦听器的自定义绑定元素，以便在运行时堆栈的特定点截获所有传入和传出消息。</span><span class="sxs-lookup"><span data-stu-id="02092-104">In particular, it shows how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span> <span data-ttu-id="02092-105">此示例还包括一个客户端和一个服务器，用于演示这些自定义工厂的使用。</span><span class="sxs-lookup"><span data-stu-id="02092-105">The sample also includes a client and server that demonstrate the use of these custom factories.</span></span>  
  
 <span data-ttu-id="02092-106">在此示例中，客户端和服务都是控制台程序 (.exe)。</span><span class="sxs-lookup"><span data-stu-id="02092-106">In this sample, both the client and the service are console programs (.exe).</span></span> <span data-ttu-id="02092-107">客户端和服务都使用一个通用库 (.dll)，其中包含自定义绑定元素及其关联的运行库对象。</span><span class="sxs-lookup"><span data-stu-id="02092-107">The client and service both make use of a common library (.dll) that contains the custom binding element and its associated run-time objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="02092-108">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="02092-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="02092-109">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="02092-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="02092-110">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="02092-110">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="02092-111">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="02092-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="02092-112">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="02092-112">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 <span data-ttu-id="02092-113">该示例介绍了使用通道框架和以下 WCF 最佳方案在 Windows Communication Foundation （WCF）中创建自定义分层通道的建议过程。</span><span class="sxs-lookup"><span data-stu-id="02092-113">The sample describes the recommended procedure for creating a custom layered channel in Windows Communication Foundation (WCF), by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="02092-114">创建自定义分层通道的步骤如下所示：</span><span class="sxs-lookup"><span data-stu-id="02092-114">The steps to create a custom layered channel are as follows:</span></span>  
  
1. <span data-ttu-id="02092-115">确定您的通道工厂和通道侦听器将要支持哪些通道形状。</span><span class="sxs-lookup"><span data-stu-id="02092-115">Decide which of the channel shapes your channel factory and channel listener will support.</span></span>  
  
2. <span data-ttu-id="02092-116">创建支持您的通道形状的通道工厂和通道侦听器。</span><span class="sxs-lookup"><span data-stu-id="02092-116">Create a channel factory and a channel listener that support your channel shapes.</span></span>  
  
3. <span data-ttu-id="02092-117">添加一个绑定元素，用于将自定义分层通道添加到通道堆栈中。</span><span class="sxs-lookup"><span data-stu-id="02092-117">Add a binding element that adds the custom layered channel to a channel stack.</span></span>  
  
4. <span data-ttu-id="02092-118">添加一个绑定元素扩展部分，以便将新的绑定元素公开到配置系统。</span><span class="sxs-lookup"><span data-stu-id="02092-118">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
## <a name="channel-shapes"></a><span data-ttu-id="02092-119">通道形状</span><span class="sxs-lookup"><span data-stu-id="02092-119">Channel Shapes</span></span>  
 <span data-ttu-id="02092-120">编写自定义分层通道的第一步是确定该通道需要哪些形状。</span><span class="sxs-lookup"><span data-stu-id="02092-120">The first step in writing a custom layered channel is to decide which shapes are required for the channel.</span></span> <span data-ttu-id="02092-121">对于我们的消息拦截器，支持我们下面的层所支持的任何形状（例如，如果我们下面的层可以生成 <xref:System.ServiceModel.Channels.IOutputChannel> 和 <xref:System.ServiceModel.Channels.IDuplexSessionChannel>，则我们也公开 <xref:System.ServiceModel.Channels.IOutputChannel> 和 <xref:System.ServiceModel.Channels.IDuplexSessionChannel>）。</span><span class="sxs-lookup"><span data-stu-id="02092-121">For our message inspector, we support any shape that the layer below us supports (for example, if the layer below us can build <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, then we also expose <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span></span>  
  
## <a name="channel-factory-and-listener-factory"></a><span data-ttu-id="02092-122">通道工厂和侦听器工厂</span><span class="sxs-lookup"><span data-stu-id="02092-122">Channel Factory and Listener Factory</span></span>  
 <span data-ttu-id="02092-123">编写自定义分层通道的下一步是为客户端通道创建 <xref:System.ServiceModel.Channels.IChannelFactory> 的实现，并为服务通道创建 <xref:System.ServiceModel.Channels.IChannelListener> 的实现。</span><span class="sxs-lookup"><span data-stu-id="02092-123">The next step in writing a custom layered channel is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span>  
  
 <span data-ttu-id="02092-124">这些类采用内部工厂和侦听器，并将除 `OnCreateChannel` 和 `OnAcceptChannel` 之外的所有调用委托给内部工厂和侦听器。</span><span class="sxs-lookup"><span data-stu-id="02092-124">These classes take an inner factory and listener, and delegate all but the `OnCreateChannel` and `OnAcceptChannel` calls to the inner factory and listener.</span></span>  
  
```csharp
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{
    //...
}

class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{
    //...
}  
```  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="02092-125">添加绑定元素</span><span class="sxs-lookup"><span data-stu-id="02092-125">Adding a Binding Element</span></span>  
 <span data-ttu-id="02092-126">此示例定义了一个自定义绑定元素：`InterceptingBindingElement`。</span><span class="sxs-lookup"><span data-stu-id="02092-126">The sample defines a custom binding element: `InterceptingBindingElement`.</span></span> <span data-ttu-id="02092-127">`InterceptingBindingElement`采用 `ChannelMessageInterceptor` 作为输入，并使用它 `ChannelMessageInterceptor` 来处理通过它的消息。</span><span class="sxs-lookup"><span data-stu-id="02092-127">`InterceptingBindingElement` takes a `ChannelMessageInterceptor` as an input, and uses this `ChannelMessageInterceptor` to manipulate messages that pass through it.</span></span> <span data-ttu-id="02092-128">这是唯一必须公开的类。</span><span class="sxs-lookup"><span data-stu-id="02092-128">This is the only class that must be public.</span></span> <span data-ttu-id="02092-129">工厂、侦听器和通道都可以是公共运行库接口的内部实现。</span><span class="sxs-lookup"><span data-stu-id="02092-129">The factory, listener, and channels can all be internal implementations of the public run-time interfaces.</span></span>  
  
```csharp
public class InterceptingBindingElement : BindingElement
{
}
```  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="02092-130">添加配置支持</span><span class="sxs-lookup"><span data-stu-id="02092-130">Adding Configuration Support</span></span>  
 <span data-ttu-id="02092-131">为了与绑定配置集成，库定义了一个配置节处理程序作为绑定元素扩展部分。</span><span class="sxs-lookup"><span data-stu-id="02092-131">To integrate with binding configuration, the library defines a configuration section handler as a binding element extension section.</span></span> <span data-ttu-id="02092-132">客户端和服务器配置文件必须向配置系统注册该绑定元素扩展。</span><span class="sxs-lookup"><span data-stu-id="02092-132">The client and server configuration files must register the binding element extension with the configuration system.</span></span> <span data-ttu-id="02092-133">希望将其绑定元素公开给配置系统的实现程序可以从此类派生。</span><span class="sxs-lookup"><span data-stu-id="02092-133">Implementers that want to expose their binding element to the configuration system can derive from this class.</span></span>  
  
```csharp
public abstract class InterceptingElement : BindingElementExtensionElement
{
    //...
}
```  
  
## <a name="adding-policy"></a><span data-ttu-id="02092-134">添加策略</span><span class="sxs-lookup"><span data-stu-id="02092-134">Adding Policy</span></span>  
 <span data-ttu-id="02092-135">为了与我们的策略系统集成，`InterceptingBindingElement` 实现了 IPolicyExportExtension，以表明我们应参与生成策略。</span><span class="sxs-lookup"><span data-stu-id="02092-135">To integrate with our policy system, `InterceptingBindingElement` implements IPolicyExportExtension to signal that we should participate in generating policy.</span></span> <span data-ttu-id="02092-136">若要支持在生成的客户端导入策略，用户可以注册 `InterceptingBindingElementImporter` 的派生类并重写 `CreateMessageInterceptor`()，以生成启用策略的 `ChannelMessageInterceptor` 类。</span><span class="sxs-lookup"><span data-stu-id="02092-136">To support importing policy on a generated client, the user can register a derived class of `InterceptingBindingElementImporter` and override `CreateMessageInterceptor`() to generate their policy-enabled `ChannelMessageInterceptor` class.</span></span>  
  
## <a name="example-droppable-message-inspector"></a><span data-ttu-id="02092-137">示例：可丢弃的消息拦截器</span><span class="sxs-lookup"><span data-stu-id="02092-137">Example: Droppable Message Inspector</span></span>  
 <span data-ttu-id="02092-138">此示例中包括了丢弃消息的 `ChannelMessageInspector` 的示例实现。</span><span class="sxs-lookup"><span data-stu-id="02092-138">Included in the sample is an example implementation of `ChannelMessageInspector` which drops messages.</span></span>  
  
```csharp
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 <span data-ttu-id="02092-139">您可以按如下方式从配置中访问该示例：</span><span class="sxs-lookup"><span data-stu-id="02092-139">You can access it from configuration as follows:</span></span>  
  
```xml  
<configuration>  
    ...  
    <system.serviceModel>  
        ...  
        <extensions>  
            <bindingElementExtensions>  
                <add name="droppingInterceptor"
                   type=  
          "Microsoft.ServiceModel.Samples.DroppingServerElement, library"/>  
            </bindingElementExtensions>  
        </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="02092-140">客户端和服务器都使用这个新创建的配置部分，将自定义工厂插入其运行库通道堆栈的最低层（在传输层之上）。</span><span class="sxs-lookup"><span data-stu-id="02092-140">The client and server both use this newly created configuration section to insert the custom factories into the lowest-level of their run-time channel stacks (above the transport level).</span></span>  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="02092-141">客户端使用 `MessageInterceptor` 库在编号为偶数的消息中添加一个自定义头。</span><span class="sxs-lookup"><span data-stu-id="02092-141">The client uses the `MessageInterceptor` library to add a custom header to even numbered messages.</span></span> <span data-ttu-id="02092-142">另一方面，服务则使用 `MessageInterceptor` 库丢弃所有没有这个特殊头的消息。</span><span class="sxs-lookup"><span data-stu-id="02092-142">The service on the other hand uses `MessageInterceptor` library to drop any messages that do not have this special header.</span></span>  
  
 <span data-ttu-id="02092-143">运行服务后再运行客户端，您应该可以看到以下客户端输出。</span><span class="sxs-lookup"><span data-stu-id="02092-143">You should see the following client output after running the service and then the client.</span></span>  
  
```console  
Reporting the next 10 wind speed  
100 kph  
Server dropped a message.  
90 kph  
80 kph  
Server dropped a message.  
70 kph  
60 kph  
Server dropped a message.  
50 kph  
40 kph  
Server dropped a message.  
30 kph  
20 kph  
Server dropped a message.  
10 kph  
Press ENTER to shut down client  
```  
  
 <span data-ttu-id="02092-144">客户端向服务报告了 10 个不同的风速，但只用这个特殊的头标记了其中 5 个。</span><span class="sxs-lookup"><span data-stu-id="02092-144">The client reports 10 different wind speeds to the service, but only tags half of them with the special header.</span></span>  
  
 <span data-ttu-id="02092-145">在服务上，您应看到以下输出：</span><span class="sxs-lookup"><span data-stu-id="02092-145">On the service, you should see the following output:</span></span>  
  
```console  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="02092-146">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="02092-146">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="02092-147">使用以下命令安装 ASP.NET 4.0。</span><span class="sxs-lookup"><span data-stu-id="02092-147">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="02092-148">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="02092-148">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="02092-149">若要生成解决方案，请按照[生成 Windows Communication Foundation 示例](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="02092-149">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="02092-150">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="02092-150">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="02092-151">先运行 Service.exe，然后运行 Client.exe 并观察两个控制台窗口的输出。</span><span class="sxs-lookup"><span data-stu-id="02092-151">Run Service.exe first then run Client.exe and watch both console windows for output.</span></span>  

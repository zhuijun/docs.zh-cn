---
title: Net.TCP 端口共享示例
ms.date: 03/30/2017
ms.assetid: 03da5959-0574-4e91-8a53-05854b6c55dc
ms.openlocfilehash: 6c196380951d0da912cd937e3ebc38a03f80489c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84584305"
---
# <a name="nettcp-port-sharing-sample"></a><span data-ttu-id="49b55-102">Net.TCP 端口共享示例</span><span class="sxs-lookup"><span data-stu-id="49b55-102">Net.TCP Port Sharing Sample</span></span>
<span data-ttu-id="49b55-103">TCP/IP 协议使用一个称为端口的 16 位数字来区分与在同一台计算机上运行的多个网络应用程序的连接。</span><span class="sxs-lookup"><span data-stu-id="49b55-103">The TCP/IP protocol uses a 16-bit number, called a port, to differentiate connections to multiple network applications running on the same machine.</span></span> <span data-ttu-id="49b55-104">如果某个应用程序正在侦听一个端口，则此端口的所有 TCP 通信将转至该应用程序。</span><span class="sxs-lookup"><span data-stu-id="49b55-104">If an application is listening on a port, then all TCP traffic for that port goes to that application.</span></span> <span data-ttu-id="49b55-105">其他应用程序无法同时侦听此端口。</span><span class="sxs-lookup"><span data-stu-id="49b55-105">Other applications cannot listen on that port at the same time.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="49b55-106">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="49b55-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="49b55-107">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="49b55-107">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="49b55-108">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="49b55-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="49b55-109">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="49b55-109">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\PortSharing`  
  
 <span data-ttu-id="49b55-110">许多协议具有所使用的标准或默认端口号。</span><span class="sxs-lookup"><span data-stu-id="49b55-110">Many protocols have a standard or default port number that they use.</span></span> <span data-ttu-id="49b55-111">例如，HTTP 协议通常使用 TCP 端口 80。</span><span class="sxs-lookup"><span data-stu-id="49b55-111">For example, the HTTP protocol typically uses TCP port 80.</span></span> <span data-ttu-id="49b55-112">Internet 信息服务 (IIS) 具有一个侦听器，可在多个 HTTP 应用程序之间共享一个端口。</span><span class="sxs-lookup"><span data-stu-id="49b55-112">Internet Information Services (IIS) has a listener to share a port between multiple HTTP applications.</span></span> <span data-ttu-id="49b55-113">IIS 直接侦听此端口，并基于消息流内的信息将消息转发到适当的应用程序。</span><span class="sxs-lookup"><span data-stu-id="49b55-113">IIS listens on the port directly and forwards messages to the appropriate application based on information inside the message stream.</span></span> <span data-ttu-id="49b55-114">这就允许多个 HTTP 应用程序使用相同的端口号，而不必竞相保留此端口来接收消息。</span><span class="sxs-lookup"><span data-stu-id="49b55-114">This allows multiple HTTP applications to use the same port number without having to compete to reserve the port for receiving messages.</span></span>  
  
 <span data-ttu-id="49b55-115">Wcf-nettcp 端口共享是一种 Windows Communication Foundation （WCF）功能，与此类似，它允许多个网络应用程序共享一个端口。</span><span class="sxs-lookup"><span data-stu-id="49b55-115">NetTcp Port Sharing is a Windows Communication Foundation (WCF)feature that similarly allows multiple network applications to share a single port.</span></span> <span data-ttu-id="49b55-116">NetTcp Port Sharing Service 接受使用 net.tcp 协议的连接，并基于消息的目标地址来转发消息。</span><span class="sxs-lookup"><span data-stu-id="49b55-116">The NetTcp Port Sharing Service accepts connections using the net.tcp protocol and forwards messages based on their destination address.</span></span>  
  
 <span data-ttu-id="49b55-117">默认情况下不会启用 NetTcp Port Sharing Service。</span><span class="sxs-lookup"><span data-stu-id="49b55-117">The NetTcp Port Sharing Service is not enabled by default.</span></span> <span data-ttu-id="49b55-118">运行该示例之前，必须手动启用此服务。</span><span class="sxs-lookup"><span data-stu-id="49b55-118">Before running this sample, you must manually enable the service.</span></span> <span data-ttu-id="49b55-119">有关详细信息，请参阅[如何：启用 Net.tcp 端口共享服务](../feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)。</span><span class="sxs-lookup"><span data-stu-id="49b55-119">For more information, see [How to: Enable the Net.TCP Port Sharing Service](../feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).</span></span> <span data-ttu-id="49b55-120">如果禁用了此服务，则在启动服务器应用程序时将引发异常。</span><span class="sxs-lookup"><span data-stu-id="49b55-120">If the service is disabled, an exception is thrown when the server application is started.</span></span>  
  
```console
Unhandled Exception: System.ServiceModel.CommunicationException: The TransportManager failed to listen on the supplied URI using the NetTcpPortSharing service: failed to start the service because it is disabled. An administrator can enable it by running 'sc.exe config NetTcpPortSharing start= demand'.. ---> System.InvalidOperationException: Cannot start service NetTcpPortSharing on computer '.'. ---> System.ComponentModel.Win32Exception: The service cannot be started, either because it is disabled or because it has no enabled devices associated with it  
```  
  
 <span data-ttu-id="49b55-121">在服务器上启用端口共享的方法是设置 <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> 绑定或 <xref:System.ServiceModel.NetTcpBinding> 绑定元素的 <xref:System.ServiceModel.Channels.TcpTransportBindingElement> 属性。</span><span class="sxs-lookup"><span data-stu-id="49b55-121">Port sharing is enabled on the server by setting the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property of the <xref:System.ServiceModel.NetTcpBinding> binding or the <xref:System.ServiceModel.Channels.TcpTransportBindingElement> binding element.</span></span> <span data-ttu-id="49b55-122">客户端不必知道是如何配置端口共享以便在服务器上使用的。</span><span class="sxs-lookup"><span data-stu-id="49b55-122">The client does not have to know how port sharing has been configured to use it on the server.</span></span>  
  
## <a name="enabling-port-sharing"></a><span data-ttu-id="49b55-123">启用端口共享</span><span class="sxs-lookup"><span data-stu-id="49b55-123">Enabling Port Sharing</span></span>  
 <span data-ttu-id="49b55-124">下面的代码演示如何在服务器上启用端口共享。</span><span class="sxs-lookup"><span data-stu-id="49b55-124">The following code demonstrates enabling port sharing on the server.</span></span> <span data-ttu-id="49b55-125">它在具有随机 URI 路径的固定端口上启动 `ICalculator` 服务的一个实例。</span><span class="sxs-lookup"><span data-stu-id="49b55-125">It starts an instance of the `ICalculator` service on a fixed port with a random URI path.</span></span> <span data-ttu-id="49b55-126">即使两个服务可以共享同一端口，但它们的整体终结点地址仍必须是唯一的，以便 NetTcp Port Sharing Service 可以将消息路由到正确的应用程序。</span><span class="sxs-lookup"><span data-stu-id="49b55-126">Even though two services can share the same port, their overall endpoint addresses still must be unique so that the NetTcp Port Sharing Service can route messages to the correct application.</span></span>  

```csharp
// Configure a binding with TCP port sharing enabled  
NetTcpBinding binding = new NetTcpBinding();  
binding.PortSharingEnabled = true;  
  
// Start a service on a fixed TCP port  
ServiceHost host = new ServiceHost(typeof(CalculatorService));  
ushort salt = (ushort)new Random().Next();  
string address = $"net.tcp://localhost:9000/calculator/{salt}";
host.AddServiceEndpoint(typeof(ICalculator), binding, address);  
host.Open();  
```

 <span data-ttu-id="49b55-127">启用端口共享后，可以多次运行此服务，而不会引起端口号冲突。</span><span class="sxs-lookup"><span data-stu-id="49b55-127">With port sharing enabled, you can run the service multiple times without having a conflict over the port number.</span></span> <span data-ttu-id="49b55-128">如果更改代码以禁用端口共享，则启动服务的两个副本将导致第二个副本失败，并出现 <xref:System.ServiceModel.AddressAlreadyInUseException>。</span><span class="sxs-lookup"><span data-stu-id="49b55-128">If you change the code to disable port sharing, starting up two copies of the service results in the second failing with an <xref:System.ServiceModel.AddressAlreadyInUseException>.</span></span>  
  
```console  
Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000.  Make sure that you are not trying to use this endpoint multiple times in your application and that there are no other applications listening on this endpoint. ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="49b55-129">运行示例</span><span class="sxs-lookup"><span data-stu-id="49b55-129">Running the Sample</span></span>  
 <span data-ttu-id="49b55-130">可以使用测试客户端来检查消息是否正确路由到共享端口的服务。</span><span class="sxs-lookup"><span data-stu-id="49b55-130">You can use the test client to check that messages are correctly routed to services sharing the port.</span></span>  

```csharp
class client  
{  
   static void Main(string[] args)  
   {  
      Console.Write("Enter the service number to test: ");  
      ushort salt = ushort.Parse(Console.ReadLine());  
      string address = $"net.tcp://localhost:9000/calculator/{salt}";
      ChannelFactory<ICalculator> factory = new ChannelFactory<ICalculator>(new NetTcpBinding());  
      ICalculator proxy = factory.CreateChannel(new EndpointAddress(address));  
  
      // Call the Add service operation.  
      double value1 = 100.00D;  
      double value2 = 15.99D;  
      double result = proxy.Add(value1, value2);  
      Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Subtract service operation.  
      value1 = 145.00D;  
      value2 = 76.54D;  
      result = proxy.Subtract(value1, value2);  
      Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Multiply service operation.  
      value1 = 9.00D;  
      value2 = 81.25D;  
      result = proxy.Multiply(value1, value2);  
      Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Divide service operation.  
      value1 = 22.00D;  
      value2 = 7.00D;  
      result = proxy.Divide(value1, value2);  
      Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
      Console.WriteLine();  
      Console.WriteLine("Press <ENTER> to terminate client.");  
      Console.ReadLine();  
  
      factory.Close();  
   }  
}  
```

 <span data-ttu-id="49b55-131">服务的每个实例将输出其唯一的编号和地址。</span><span class="sxs-lookup"><span data-stu-id="49b55-131">Each instance of the service prints out its unique number and address.</span></span> <span data-ttu-id="49b55-132">例如，运行 service.exe 时可能会看到以下文本。</span><span class="sxs-lookup"><span data-stu-id="49b55-132">For instance, you may see the following text when you run service.exe.</span></span>  
  
```console  
Service #4381 listening on net.tcp://localhost:9000/calculator/4381.  
Press <ENTER> to terminate service.  
```  
  
 <span data-ttu-id="49b55-133">在此输入运行 client.exe 时看到的服务编号。</span><span class="sxs-lookup"><span data-stu-id="49b55-133">Enter the service number you see here when you run client.exe.</span></span>  
  
```console  
Enter the service number to test: 4381  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="49b55-134">可以通过更改客户端使用的所生成的地址，使用跨计算机配置来运行此示例。</span><span class="sxs-lookup"><span data-stu-id="49b55-134">This sample can be run in a cross-machine configuration by changing the generated address that the client uses.</span></span> <span data-ttu-id="49b55-135">在 Client.cs 中，更改终结点的地址格式字符串以与服务的新地址相匹配。</span><span class="sxs-lookup"><span data-stu-id="49b55-135">In the Client.cs, change the endpoint address format string to match the new address of your service.</span></span> <span data-ttu-id="49b55-136">将对“localhost”的所有引用替换为服务器计算机的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="49b55-136">Replace any references to "localhost" with the IP address of the server machine.</span></span> <span data-ttu-id="49b55-137">进行此更改之后，必须重新编译该示例。</span><span class="sxs-lookup"><span data-stu-id="49b55-137">You must recompile the sample after making this change.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="49b55-138">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="49b55-138">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="49b55-139">使用以下命令安装 ASP.NET 4.0。</span><span class="sxs-lookup"><span data-stu-id="49b55-139">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="49b55-140">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="49b55-140">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="49b55-141">按照前面的简介部分中的说明启用 NetTcp Port Sharing Service。</span><span class="sxs-lookup"><span data-stu-id="49b55-141">Enable the NetTcp Port Sharing Service as previously described in the introduction section.</span></span>  
  
4. <span data-ttu-id="49b55-142">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="49b55-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
5. <span data-ttu-id="49b55-143">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="49b55-143">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span> <span data-ttu-id="49b55-144">前面的“运行示例”部分中包含有关运行该示例的特定详细信息。</span><span class="sxs-lookup"><span data-stu-id="49b55-144">Specific details for running this sample are included previously in the Running the Sample section.</span></span>  

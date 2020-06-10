---
title: 如何：创建通过 WebSocket 进行通信的 WCF 服务
ms.date: 03/30/2017
ms.assetid: bafbbd89-eab8-4e9a-b4c3-b7b0178e12d8
ms.openlocfilehash: 5aade8e3fb2049521ed06f5f1a148be2e4636e36
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597106"
---
# <a name="how-to-create-a-wcf-service-that-communicates-over-websockets"></a><span data-ttu-id="79978-102">如何：创建通过 WebSocket 进行通信的 WCF 服务</span><span class="sxs-lookup"><span data-stu-id="79978-102">How to: Create a WCF Service that Communicates over WebSockets</span></span>
<span data-ttu-id="79978-103">WCF 服务和客户端可以使用 <xref:System.ServiceModel.NetHttpBinding> 绑定通过 WebSocket 进行通信。</span><span class="sxs-lookup"><span data-stu-id="79978-103">WCF services and clients can use the <xref:System.ServiceModel.NetHttpBinding> binding to communicate over WebSockets.</span></span>  <span data-ttu-id="79978-104">当 <xref:System.ServiceModel.NetHttpBinding> 确定服务协定定义回调协定时，将使用 WebSocket。</span><span class="sxs-lookup"><span data-stu-id="79978-104">WebSockets will be used when the <xref:System.ServiceModel.NetHttpBinding> determines the service contract defines a callback contract.</span></span> <span data-ttu-id="79978-105">本主题描述如何实现使用 <xref:System.ServiceModel.NetHttpBinding> 通过 WebSocket 进行通信的 WCF 服务和客户端。</span><span class="sxs-lookup"><span data-stu-id="79978-105">This topic describes how to implement a WCF service and client that uses the <xref:System.ServiceModel.NetHttpBinding> to communicate over WebSockets.</span></span>  
  
### <a name="define-the-service"></a><span data-ttu-id="79978-106">定义服务</span><span class="sxs-lookup"><span data-stu-id="79978-106">Define the Service</span></span>  
  
1. <span data-ttu-id="79978-107">定义回调协定</span><span class="sxs-lookup"><span data-stu-id="79978-107">Define a callback contract</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IStockQuoteCallback  
        {  
            [OperationContract(IsOneWay = true)]  
            Task SendQuote(string code, double value);  
        }  
    ```  
  
     <span data-ttu-id="79978-108">本协定将由客户端应用程序实现，以允许服务将消息发送回客户端。</span><span class="sxs-lookup"><span data-stu-id="79978-108">This contract will be implemented by the client application to allow the service to send messages back to the client.</span></span>  
  
2. <span data-ttu-id="79978-109">定义服务协定并指定 `IStockQuoteCallback` 接口作为回调协定。</span><span class="sxs-lookup"><span data-stu-id="79978-109">Define the service contract and specify the `IStockQuoteCallback` interface as the callback contract.</span></span>  
  
    ```csharp  
    [ServiceContract(CallbackContract = typeof(IStockQuoteCallback))]  
        public interface IStockQuoteService  
        {  
            [OperationContract(IsOneWay = true)]  
            Task StartSendingQuotes();  
        }  
    ```  
  
3. <span data-ttu-id="79978-110">实现服务协定。</span><span class="sxs-lookup"><span data-stu-id="79978-110">Implement the service contract.</span></span>  
  
    ```csharp
    public class StockQuoteService : IStockQuoteService  
    {  
        public async Task StartSendingQuotes()  
        {  
            var callback = OperationContext.Current.GetCallbackChannel<IStockQuoteCallback>();  
            var random = new Random();  
            double price = 29.00;  

            while (((IChannel)callback).State == CommunicationState.Opened)  
            {  
                await callback.SendQuote("MSFT", price);  
                price += random.NextDouble();  
                await Task.Delay(1000);  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="79978-111">服务操作 `StartSendingQuotes` 将实现为异步调用。</span><span class="sxs-lookup"><span data-stu-id="79978-111">The service operation `StartSendingQuotes` is implemented as an asynchronous call.</span></span> <span data-ttu-id="79978-112">我们使用 `OperationContext` 检索回调通道；如果通道是打开的，则对回调通道进行异步调用。</span><span class="sxs-lookup"><span data-stu-id="79978-112">We retrieve the callback channel using the `OperationContext` and if the channel is open, we make an async call on the callback channel.</span></span>  
  
4. <span data-ttu-id="79978-113">配置服务</span><span class="sxs-lookup"><span data-stu-id="79978-113">Configure the service</span></span>  
  
    ```xml  
    <configuration>  
        <appSettings>  
          <add key="aspnet:UseTaskFriendlySynchronizationContext" value="true" />
        </appSettings>  
        <system.web>  
          <compilation debug="true" targetFramework="4.5" />
        </system.web>  
        <system.serviceModel>  
            <protocolMapping>  
              <add scheme="http" binding="netHttpBinding"/>  
              <add scheme="https" binding="netHttpsBinding"/>  
            </protocolMapping>  
            <behaviors>  
                <serviceBehaviors>  
                    <behavior name="">  
                        <serviceMetadata httpGetEnabled="true" httpsGetEnabled="true" />  
                        <serviceDebug includeExceptionDetailInFaults="false" />  
                    </behavior>  
                </serviceBehaviors>  
            </behaviors>  
            <serviceHostingEnvironment aspNetCompatibilityEnabled="true"  
                multipleSiteBindingsEnabled="true" />  
        </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="79978-114">服务的配置文件依赖于 WCF 的默认终结点。</span><span class="sxs-lookup"><span data-stu-id="79978-114">The service’s configuration file relies on WCF’s default endpoints.</span></span> <span data-ttu-id="79978-115">使用 `<protocolMapping>` 部分来指定应将 `NetHttpBinding` 用于所创建的默认终结点。</span><span class="sxs-lookup"><span data-stu-id="79978-115">The `<protocolMapping>` section is used to specify that the `NetHttpBinding` should be used for the default endpoints created.</span></span>  
  
### <a name="define-the-client"></a><span data-ttu-id="79978-116">定义客户端</span><span class="sxs-lookup"><span data-stu-id="79978-116">Define the Client</span></span>  
  
1. <span data-ttu-id="79978-117">实现回调协定。</span><span class="sxs-lookup"><span data-stu-id="79978-117">Implement the callback contract.</span></span>  
  
    ```csharp  
    private class CallbackHandler : StockQuoteServiceReference.IStockQuoteServiceCallback  
            {  
                public async Task SendQuoteAsync(string code, double value)  
                {  
                    Console.WriteLine("{0}: {1:f2}", code, value);  
                }  
            }  
    ```  
  
     <span data-ttu-id="79978-118">回调协定操作将作为异步方法实现。</span><span class="sxs-lookup"><span data-stu-id="79978-118">The callback contract operation is implemented as an asynchronous method.</span></span>  
  
    1. <span data-ttu-id="79978-119">实现客户端代码。</span><span class="sxs-lookup"><span data-stu-id="79978-119">Implement the client code.</span></span>  
  
        ```csharp  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                var context = new InstanceContext(new CallbackHandler());  
                var client = new StockQuoteServiceReference.StockQuoteServiceClient(context);  
                client.StartSendingQuotes();
                Console.ReadLine();  
            }  
  
            private class CallbackHandler : StockQuoteServiceReference.IStockQuoteServiceCallback  
            {  
                public async Task SendQuoteAsync(string code, double value)  
                {  
                    Console.WriteLine("{0}: {1:f2}", code, value);  
                }  
            }  
        }  
        ```  
  
         <span data-ttu-id="79978-120">为清楚起见，此处重复使用了 CallbackHandler。</span><span class="sxs-lookup"><span data-stu-id="79978-120">The CallbackHandler is repeated here for clarity.</span></span> <span data-ttu-id="79978-121">客户端应用程序创建新的 InstanceContext，并指定回调接口的实现。</span><span class="sxs-lookup"><span data-stu-id="79978-121">The client application creates a new InstanceContext and specifies the implementation of the callback interface.</span></span> <span data-ttu-id="79978-122">下一步，它创建将引用发送到新创建的 InstanceContext 的代理类实例。</span><span class="sxs-lookup"><span data-stu-id="79978-122">Next it creates an instance of the proxy class sending a reference to the newly created InstanceContext.</span></span> <span data-ttu-id="79978-123">当客户端调用服务时，该服务将使用指定的回调协定调用客户端。</span><span class="sxs-lookup"><span data-stu-id="79978-123">When the client calls the service, the service will call the client using the callback contract specified.</span></span>  
  
    2. <span data-ttu-id="79978-124">配置客户端</span><span class="sxs-lookup"><span data-stu-id="79978-124">Configure the client</span></span>  
  
        ```xml  
        <?xml version="1.0" encoding="utf-8" ?>  
        <configuration>  
            <startup>
                <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />  
            </startup>  
            <system.serviceModel>  
                <bindings>  
                    <netHttpBinding>  
                        <binding name="NetHttpBinding_IStockQuoteService">  
                            <webSocketSettings transportUsage="Always" />  
                        </binding>  
                    </netHttpBinding>  
                </bindings>  
                <client>  
                    <endpoint address="ws://localhost/NetHttpSampleServer/StockQuoteService.svc"  
                        binding="netHttpBinding" bindingConfiguration="NetHttpBinding_IStockQuoteService"  
                        contract="StockQuoteServiceReference.IStockQuoteService" name="NetHttpBinding_IStockQuoteService" />  
                </client>  
            </system.serviceModel>  
        </configuration>  
        ```  
  
         <span data-ttu-id="79978-125">在客户端配置中无需执行任何特殊内容，只需通过 `NetHttpBinding` 指定客户端终结点。</span><span class="sxs-lookup"><span data-stu-id="79978-125">There is nothing special you need to do in the client configuration, just specify the client side endpoint using the `NetHttpBinding`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79978-126">示例</span><span class="sxs-lookup"><span data-stu-id="79978-126">Example</span></span>  
 <span data-ttu-id="79978-127">下面是本主题中使用的完整代码。</span><span class="sxs-lookup"><span data-stu-id="79978-127">The following is the complete code used in this topic.</span></span>  
  
```csharp  
// IStockQuoteService.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
using System.Threading.Tasks;  
  
namespace Server  
{  
    [ServiceContract(CallbackContract = typeof(IStockQuoteCallback))]  
    public interface IStockQuoteService  
    {  
        [OperationContract(IsOneWay = true)]  
        Task StartSendingQuotes();  
    }  
  
    [ServiceContract]  
    public interface IStockQuoteCallback  
    {  
        [OperationContract(IsOneWay = true)]  
        Task SendQuote(string code, double value);  
    }  
}  
```  
  
```csharp
// StockQuoteService.svc.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
using System.Text;  
using System.Threading.Tasks;  
  
namespace Server  
{  
    public class StockQuoteService : IStockQuoteService  
    {  
        public async Task StartSendingQuotes()  
        {  
            var callback = OperationContext.Current.GetCallbackChannel<IStockQuoteCallback>();  
            var random = new Random();  
            double price = 29.00;  
  
            while (((IChannel)callback).State == CommunicationState.Opened)  
            {  
                await callback.SendQuote("MSFT", price);  
                price += random.NextDouble();  
                await Task.Delay(1000);  
            }  
        }  
    }  
}  
```  
  
```xml  
<?xml version="1.0"?>  
  
<!--  
  For more information on how to configure your ASP.NET application, please visit  
  https://go.microsoft.com/fwlink/?LinkId=169433  
  -->  
  
<configuration>  
    <appSettings>  
      <add key="aspnet:UseTaskFriendlySynchronizationContext" value="true" />
    </appSettings>  
    <system.web>  
      <compilation debug="true" targetFramework="4.5" />
    </system.web>  
    <system.serviceModel>  
        <protocolMapping>  
          <add scheme="http" binding="netHttpBinding"/>  
          <add scheme="https" binding="netHttpsBinding"/>  
        </protocolMapping>  
        <behaviors>  
            <serviceBehaviors>  
                <behavior name="">  
                    <serviceMetadata httpGetEnabled="true" httpsGetEnabled="true" />  
                    <serviceDebug includeExceptionDetailInFaults="false" />  
                </behavior>  
            </serviceBehaviors>  
        </behaviors>  
        <serviceHostingEnvironment aspNetCompatibilityEnabled="true"  
            multipleSiteBindingsEnabled="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
```
<!-- StockQuoteService.svc -->  
<%@ ServiceHost Language="C#" Debug="true" Service="Server.StockQuoteService" CodeBehind="StockQuoteService.svc.cs" %>  
```  
  
```csharp  
// Client.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.ServiceModel;  
using System.Text;  
using System.Threading.Tasks;  
  
namespace Client  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            var context = new InstanceContext(new CallbackHandler());  
            var client = new StockQuoteServiceReference.StockQuoteServiceClient(context);  
            client.StartSendingQuotes();
            Console.ReadLine();  
        }  
  
        private class CallbackHandler : StockQuoteServiceReference.IStockQuoteServiceCallback  
        {  
            public async Task SendQuoteAsync(string code, double value)  
            {  
                Console.WriteLine("{0}: {1:f2}", code, value);  
            }  
        }  
    }  
}  
```  
  
```xml  
<!--App.config -->  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <startup>
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />  
    </startup>  
    <system.serviceModel>  
        <bindings>  
            <netHttpBinding>  
                <binding name="NetHttpBinding_IStockQuoteService">  
                    <webSocketSettings transportUsage="Always" />  
                </binding>  
            </netHttpBinding>  
        </bindings>  
        <client>  
            <endpoint address="ws://localhost/NetHttpSampleServer/StockQuoteService.svc"  
                binding="netHttpBinding" bindingConfiguration="NetHttpBinding_IStockQuoteService"  
                contract="StockQuoteServiceReference.IStockQuoteService" name="NetHttpBinding_IStockQuoteService" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="79978-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="79978-128">See also</span></span>

- [<span data-ttu-id="79978-129">同步和异步操作</span><span class="sxs-lookup"><span data-stu-id="79978-129">Synchronous and Asynchronous Operations</span></span>](../synchronous-and-asynchronous-operations.md)
- [<span data-ttu-id="79978-130">使用 NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="79978-130">Using the NetHttpBinding</span></span>](using-the-nethttpbinding.md)

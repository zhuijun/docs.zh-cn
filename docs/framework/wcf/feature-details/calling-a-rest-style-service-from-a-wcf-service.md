---
title: 从 WCF 服务调用 REST 样式服务
description: 了解如何通过创建一个范围并从该范围调用 REST 样式的服务，使 WCF 服务通过 REST 样式的服务使用正确的上下文。
ms.date: 03/30/2017
ms.assetid: 77df81d8-7f53-4daf-8d2d-bf7996e94d5a
ms.openlocfilehash: 15f468923cf55feb85e7aeca1a2cc5e38050d665
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245292"
---
# <a name="calling-a-rest-style-service-from-a-wcf-service"></a><span data-ttu-id="79dd0-103">从 WCF 服务调用 REST 样式服务</span><span class="sxs-lookup"><span data-stu-id="79dd0-103">Calling a REST-style service from a WCF service</span></span>

<span data-ttu-id="79dd0-104">当从常规（基于 SOAP）的 WCF 服务调用 REST 样式服务时，服务方法的操作上下文（包含有关传入请求的信息）将重写应由传出请求使用的上下文。</span><span class="sxs-lookup"><span data-stu-id="79dd0-104">When calling a REST-style service from a regular (SOAP-based) WCF service, the operation context on the service method (which contains information about the incoming request) overrides the context which should be used by the outgoing request.</span></span> <span data-ttu-id="79dd0-105">这会导致 HTTP GET 请求更改为 HTTP POST 请求。</span><span class="sxs-lookup"><span data-stu-id="79dd0-105">This causes HTTP GET requests to change to HTTP POST requests.</span></span> <span data-ttu-id="79dd0-106">要强制 WCF 服务使用正确的上下文来调用 REST 样式服务，请创建一个新的 <xref:System.ServiceModel.OperationContextScope>，并从操作上下文作用域内调用 REST 样式服务。</span><span class="sxs-lookup"><span data-stu-id="79dd0-106">To force the WCF service to use the right context for calling the REST-style service, create a new <xref:System.ServiceModel.OperationContextScope> and call the REST-style service from inside the operation context scope.</span></span> <span data-ttu-id="79dd0-107">本主题将介绍如何创建一个用于说明此方法的简单示例。</span><span class="sxs-lookup"><span data-stu-id="79dd0-107">This topic will describe how to create a simple sample that illustrates this technique.</span></span>

## <a name="define-the-rest-style-service-contract"></a><span data-ttu-id="79dd0-108">定义 REST 样式服务协定</span><span class="sxs-lookup"><span data-stu-id="79dd0-108">Define the REST-style service contract</span></span>

<span data-ttu-id="79dd0-109">定义简单的 REST 样式服务协定：</span><span class="sxs-lookup"><span data-stu-id="79dd0-109">Define a simple  REST-style service contract:</span></span>

```csharp
[ServiceContract]
public interface IRestInterface
{
    [OperationContract, WebGet]
    int Add(int x, int y);

    [OperationContract, WebGet]
    string Echo(string input);
}
```

## <a name="implement-the-rest-style-service-contract"></a><span data-ttu-id="79dd0-110">实现 REST 样式服务协定</span><span class="sxs-lookup"><span data-stu-id="79dd0-110">Implement the REST-style service contract</span></span>

<span data-ttu-id="79dd0-111">实现 REST 样式服务协定：</span><span class="sxs-lookup"><span data-stu-id="79dd0-111">Implement the REST-style service contract:</span></span>

```csharp
public class RestService : IRestInterface
{
    public int Add(int x, int y)
    {
        return x + y;
    }

    public string Echo(string input)
    {
        return input;
    }
}
```

## <a name="define-the-wcf-service-contract"></a><span data-ttu-id="79dd0-112">定义 WCF 服务协定</span><span class="sxs-lookup"><span data-stu-id="79dd0-112">Define the WCF service contract</span></span>

<span data-ttu-id="79dd0-113">定义将用于调用 REST 样式服务的 WCF 服务协定：</span><span class="sxs-lookup"><span data-stu-id="79dd0-113">Define a WCF service contract  that will be used to call the REST-style service:</span></span>

```csharp
[ServiceContract]
public interface INormalInterface
{
    [OperationContract]
    int CallAdd(int x, int y);

    [OperationContract]
    string CallEcho(string input);
}
```

## <a name="implement-the-wcf-service-contract"></a><span data-ttu-id="79dd0-114">实现 WCF 服务协定</span><span class="sxs-lookup"><span data-stu-id="79dd0-114">Implement the WCF service contract</span></span>

<span data-ttu-id="79dd0-115">实现 WCF 服务协定：</span><span class="sxs-lookup"><span data-stu-id="79dd0-115">Implement the WCF service contract:</span></span>

```csharp
public class NormalService : INormalInterface
{
    static MyRestClient client = new MyRestClient(RestServiceBaseAddress);
    public int CallAdd(int x, int y)
    {
        return client.Add(x, y);
    }

    public string CallEcho(string input)
    {
        return client.Echo(input);
    }
}
```

## <a name="create-the-client-proxy-for-the-rest-style-service"></a><span data-ttu-id="79dd0-116">为 REST 样式服务创建客户端代理</span><span class="sxs-lookup"><span data-stu-id="79dd0-116">Create the client proxy for the REST-style service</span></span>

<span data-ttu-id="79dd0-117">使用 <xref:System.ServiceModel.ClientBase%601> 来实现客户端代理。</span><span class="sxs-lookup"><span data-stu-id="79dd0-117">Using <xref:System.ServiceModel.ClientBase%601> to implement the client proxy.</span></span> <span data-ttu-id="79dd0-118">对于每个调用的方法，创建一个新的 <xref:System.ServiceModel.OperationContextScope>，并使用它来调用此操作。</span><span class="sxs-lookup"><span data-stu-id="79dd0-118">For each method called, a new <xref:System.ServiceModel.OperationContextScope> is created and used to call the operation.</span></span>

```csharp
public class MyRestClient : ClientBase<IRestInterface>, IRestInterface
{
    public MyRestClient(string address)
        : base(new WebHttpBinding(), new EndpointAddress(address))
    {
        this.Endpoint.Behaviors.Add(new WebHttpBehavior());
    }

    public int Add(int x, int y)
    {
        using (new OperationContextScope(this.InnerChannel))
        {
            return base.Channel.Add(x, y);
        }
    }

    public string Echo(string input)
    {
        using (new OperationContextScope(this.InnerChannel))
        {
            return base.Channel.Echo(input);
        }
    }
}
```

## <a name="host-and-call-the-services"></a><span data-ttu-id="79dd0-119">承载和调用服务</span><span class="sxs-lookup"><span data-stu-id="79dd0-119">Host and call the services</span></span>

<span data-ttu-id="79dd0-120">在控制台应用程序中承载这两项服务，并添加所需的终结点和行为。</span><span class="sxs-lookup"><span data-stu-id="79dd0-120">Host both services in a console app, adding the needed endpoints and behaviors.</span></span> <span data-ttu-id="79dd0-121">然后，调用常规 WCF 服务：</span><span class="sxs-lookup"><span data-stu-id="79dd0-121">And then call the regular WCF service:</span></span>

```csharp
public static void Main()
{
    ServiceHost restHost = new ServiceHost(typeof(RestService), new Uri(RestServiceBaseAddress));
    restHost.AddServiceEndpoint(typeof(IRestInterface), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());
    restHost.Open();

    ServiceHost normalHost = new ServiceHost(typeof(NormalService), new Uri(NormalServiceBaseAddress));
    normalHost.AddServiceEndpoint(typeof(INormalInterface), new BasicHttpBinding(), "");
    normalHost.Open();

    Console.WriteLine("Hosts opened");

    ChannelFactory<INormalInterface> factory = new ChannelFactory<INormalInterface>(new BasicHttpBinding(), new EndpointAddress(NormalServiceBaseAddress));
    INormalInterface proxy = factory.CreateChannel();

    Console.WriteLine(proxy.CallAdd(123, 456));
    Console.WriteLine(proxy.CallEcho("Hello world"));
}
```

## <a name="complete-code-listing"></a><span data-ttu-id="79dd0-122">完成代码清单</span><span class="sxs-lookup"><span data-stu-id="79dd0-122">Complete code listing</span></span>

<span data-ttu-id="79dd0-123">下面列出了本主题中实现的示例：</span><span class="sxs-lookup"><span data-stu-id="79dd0-123">The following is a complete listing of the sample implemented in this topic:</span></span>

```csharp
public class CallingRESTSample
{
    static readonly string RestServiceBaseAddress = "http://" + Environment.MachineName + ":8008/Service";
    static readonly string NormalServiceBaseAddress = "http://" + Environment.MachineName + ":8000/Service";

    [ServiceContract]
    public interface IRestInterface
    {
        [OperationContract, WebGet]
        int Add(int x, int y);
        [OperationContract, WebGet]
        string Echo(string input);
    }

    [ServiceContract]
    public interface INormalInterface
    {
        [OperationContract]
        int CallAdd(int x, int y);
        [OperationContract]
        string CallEcho(string input);
    }

    public class RestService : IRestInterface
    {
        public int Add(int x, int y)
        {
            return x + y;
        }

        public string Echo(string input)
        {
            return input;
        }
    }

    public class MyRestClient : ClientBase<IRestInterface>, IRestInterface
    {
        public MyRestClient(string address)
            : base(new WebHttpBinding(), new EndpointAddress(address))
        {
            this.Endpoint.Behaviors.Add(new WebHttpBehavior());
        }

        public int Add(int x, int y)
        {
            using (new OperationContextScope(this.InnerChannel))
            {
                return base.Channel.Add(x, y);
            }
        }

        public string Echo(string input)
        {
            using (new OperationContextScope(this.InnerChannel))
            {
                return base.Channel.Echo(input);
            }
        }
    }

    public class NormalService : INormalInterface
    {
        static MyRestClient client = new MyRestClient(RestServiceBaseAddress);
        public int CallAdd(int x, int y)
        {
            return client.Add(x, y);
        }

        public string CallEcho(string input)
        {
            return client.Echo(input);
        }
    }

    public static void Main()
    {
        ServiceHost restHost = new ServiceHost(typeof(RestService), new Uri(RestServiceBaseAddress));
        restHost.AddServiceEndpoint(typeof(IRestInterface), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());
        restHost.Open();

        ServiceHost normalHost = new ServiceHost(typeof(NormalService), new Uri(NormalServiceBaseAddress));
        normalHost.AddServiceEndpoint(typeof(INormalInterface), new BasicHttpBinding(), "");
        normalHost.Open();

        Console.WriteLine("Hosts opened");

        ChannelFactory<INormalInterface> factory = new ChannelFactory<INormalInterface>(new BasicHttpBinding(), new EndpointAddress(NormalServiceBaseAddress));
        INormalInterface proxy = factory.CreateChannel();

        Console.WriteLine(proxy.CallAdd(123, 456));
        Console.WriteLine(proxy.CallEcho("Hello world"));
    }
}
```

## <a name="see-also"></a><span data-ttu-id="79dd0-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="79dd0-124">See also</span></span>

- [<span data-ttu-id="79dd0-125">如何：创建基本 WCF Web HTTP 服务</span><span class="sxs-lookup"><span data-stu-id="79dd0-125">How to: Create a Basic WCF Web HTTP Service</span></span>](how-to-create-a-basic-wcf-web-http-service.md)
- [<span data-ttu-id="79dd0-126">WCF Web HTTP 编程对象模型</span><span class="sxs-lookup"><span data-stu-id="79dd0-126">WCF Web HTTP Programming Object Model</span></span>](wcf-web-http-programming-object-model.md)

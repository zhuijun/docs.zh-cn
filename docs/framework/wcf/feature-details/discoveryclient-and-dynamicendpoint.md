---
title: DiscoveryClient 和 DynamicEndpoint
ms.date: 03/30/2017
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
ms.openlocfilehash: 6144a3fb528e64fd55fa125b6254d415ec3e8b26
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599160"
---
# <a name="discoveryclient-and-dynamicendpoint"></a><span data-ttu-id="68781-102">DiscoveryClient 和 DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="68781-102">DiscoveryClient and DynamicEndpoint</span></span>
<span data-ttu-id="68781-103"><xref:System.ServiceModel.Discovery.DiscoveryClient> 和 <xref:System.ServiceModel.Discovery.DynamicEndpoint> 是客户端上用来搜索服务的两个类。</span><span class="sxs-lookup"><span data-stu-id="68781-103"><xref:System.ServiceModel.Discovery.DiscoveryClient> and <xref:System.ServiceModel.Discovery.DynamicEndpoint> are two classes used on the client side to search for services.</span></span> <span data-ttu-id="68781-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> 为您提供与一组特定条件相匹配的服务列表，并允许您连接到这些服务。</span><span class="sxs-lookup"><span data-stu-id="68781-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> provides you with a list of services that match a specific set of criteria and allows you to connect to the services.</span></span> <span data-ttu-id="68781-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint> 执行相同的操作，另外会自动连接到所发现的服务之一。</span><span class="sxs-lookup"><span data-stu-id="68781-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint> performs the same operation and in addition, automatically connects to one of the services that was found.</span></span> <span data-ttu-id="68781-106">可以将任何终结点转换为 <xref:System.ServiceModel.Discovery.DynamicEndpoint>，也可以在配置中添加搜索条件，这样，如果您需要在解决方案中执行发现操作，但不希望修改客户端逻辑，则 <xref:System.ServiceModel.Discovery.DynamicEndpoint> 会非常有用 – 此时您只需修改终结点。</span><span class="sxs-lookup"><span data-stu-id="68781-106">Any endpoint can be made into a <xref:System.ServiceModel.Discovery.DynamicEndpoint>, the search criteria can also be added in configuration, thus <xref:System.ServiceModel.Discovery.DynamicEndpoint> is useful when you need discovery in your solution but do not want to modify the client logic – you only need to modify the endpoints.</span></span> <span data-ttu-id="68781-107">另一方面，<xref:System.ServiceModel.Discovery.DiscoveryClient> 可用于对您的搜索操作获得更精细的控制。</span><span class="sxs-lookup"><span data-stu-id="68781-107"><xref:System.ServiceModel.Discovery.DiscoveryClient> on the other hand can be used to gain finer control over your search operation.</span></span> <span data-ttu-id="68781-108">下面对每个类的用途和优势加以详细说明。</span><span class="sxs-lookup"><span data-stu-id="68781-108">The uses and benefits of each are elaborated below.</span></span>  
  
## <a name="discoveryclient"></a><span data-ttu-id="68781-109">DiscoveryClient</span><span class="sxs-lookup"><span data-stu-id="68781-109">DiscoveryClient</span></span>  
 <span data-ttu-id="68781-110"><xref:System.ServiceModel.Discovery.DiscoveryClient> 定义同步和异步 Find 方法以及 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> 和 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> 事件。</span><span class="sxs-lookup"><span data-stu-id="68781-110">The <xref:System.ServiceModel.Discovery.DiscoveryClient> defines synchronous and asynchronous Find methods, <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events.</span></span>  <span data-ttu-id="68781-111">它还定义了同步和异步 Resolve 方法以及 <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> 事件。</span><span class="sxs-lookup"><span data-stu-id="68781-111">It also defines synchronous and asynchronous Resolve methods and a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> event.</span></span> <span data-ttu-id="68781-112">使用 <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> 或 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> 方法可以搜索服务。</span><span class="sxs-lookup"><span data-stu-id="68781-112">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> or <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> methods to search for services.</span></span> <span data-ttu-id="68781-113">这两个方法都接受 <xref:System.ServiceModel.Discovery.FindCriteria> 实例，该实例可用于指定协定类型名称、作用域、最大请求结果数和作用域匹配规则。</span><span class="sxs-lookup"><span data-stu-id="68781-113">Both of these methods take a <xref:System.ServiceModel.Discovery.FindCriteria> instance that allows you to specify contract type names, scopes, maximum number of results requested, and scope matching rules.</span></span> <span data-ttu-id="68781-114">调用 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> 方法时，可以使用 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> 和 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> 事件。</span><span class="sxs-lookup"><span data-stu-id="68781-114">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events can be used when calling the <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> method.</span></span> <span data-ttu-id="68781-115">只要 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> 从服务中收到响应，就会激发 <xref:System.ServiceModel.Discovery.DiscoveryClient>。</span><span class="sxs-lookup"><span data-stu-id="68781-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> is fired whenever the <xref:System.ServiceModel.Discovery.DiscoveryClient> receives a response from a service.</span></span> <span data-ttu-id="68781-116">可使用该事件来显示指示查找操作进度的进度栏。</span><span class="sxs-lookup"><span data-stu-id="68781-116">It can be used to display a progress bar showing the progress of the find operation.</span></span> <span data-ttu-id="68781-117">它还可用来在接收到查找响应时对这些响应进行操作。</span><span class="sxs-lookup"><span data-stu-id="68781-117">It can also be used to act on find responses as they are received.</span></span> <span data-ttu-id="68781-118">查找操作完成时激发 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> 事件。</span><span class="sxs-lookup"><span data-stu-id="68781-118">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> event is fired when the find operation completes.</span></span> <span data-ttu-id="68781-119">如果已接收到最大响应数或 <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> 已结束，则可能发生此情况。</span><span class="sxs-lookup"><span data-stu-id="68781-119">This may happen because the maximum number of responses has been received or if the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> has elapsed.</span></span> <span data-ttu-id="68781-120">查找操作完成时，将在 <xref:System.ServiceModel.Discovery.FindResponse> 实例中返回结果。</span><span class="sxs-lookup"><span data-stu-id="68781-120">When the find operation completes the results are returned in a <xref:System.ServiceModel.Discovery.FindResponse> instance.</span></span> <span data-ttu-id="68781-121"><xref:System.ServiceModel.Discovery.FindResponse> 包含 <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> 的集合，该集合包含地址、协定类型名称、扩展、侦听 URI 和匹配的服务的作用域。</span><span class="sxs-lookup"><span data-stu-id="68781-121">The <xref:System.ServiceModel.Discovery.FindResponse> contains a collection of <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> which contains the addresses, contract type names, extensions, listen URIs, and scopes of the matching services.</span></span> <span data-ttu-id="68781-122">然后，您可以使用这些信息连接到匹配的服务并调用其中一个服务。</span><span class="sxs-lookup"><span data-stu-id="68781-122">You can then use this information to connect to and call one of the matching services.</span></span> <span data-ttu-id="68781-123">下面的示例演示了如何调用 DiscoveryClient （s）方法，并使用返回的元数据来调用找到的服务的。</span><span class="sxs-lookup"><span data-stu-id="68781-123">The following example shows how to call the System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) method and use the returned metadata to call the found service.</span></span> <span data-ttu-id="68781-124">使用的好处 <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> 是，你可以缓存找到的终结点列表并稍后使用这些终结点。</span><span class="sxs-lookup"><span data-stu-id="68781-124">A benefit of using <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> is that you can cache the list of endpoints you’ve found and use them at a later time.</span></span> <span data-ttu-id="68781-125">通过此缓存，您可以构建自定义逻辑来处理各种失败情况。</span><span class="sxs-lookup"><span data-stu-id="68781-125">With this cache, you can build custom logic to handle various failure conditions.</span></span>  
  
```csharp
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
FindCriteria criteria = new FindCriteria(typeof(ICalculatorService));  
FindResponse fr = dc.Find(criteria);  
  
if (fr.Endpoints.Count > 0)  
{  
   EndpointAddress ep = fr.Endpoints[0].Address;  
   CalculatorServiceClient client = new CalculatorServiceClient();  
  
    // Connect to the discovered service endpoint  
   client.Endpoint.Address = endpointAddress;  
   Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
   double value1 = 100.00D;  
   double value2 = 15.99D;  
  
   // Call the Add service operation.  
   double result = client.Add(value1, value2);  
   Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
}  
else  
   Console.WriteLine("No matching endpoints found");  
```  
  
 <span data-ttu-id="68781-126">下面的示例演示如何采用异步方式执行查找操作。</span><span class="sxs-lookup"><span data-stu-id="68781-126">The following example shows how to perform a find operation asynchronously.</span></span>  
  
```csharp
static void FindServiceAsync()  
{  
   DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());
   dc.FindCompleted += new EventHandler<FindCompletedEventArgs>( discoveryClient_FindCompleted);  
   dc.FindProgressChanged += new EventHandler<FindProgressChangedEventArgs>(discoveryClient_FindProgressChanged);  
   dc.FindAsync(new FindCriteria(typeof(ICalculatorService)));
}
static void discoveryClient_FindProgressChanged(object sender, FindProgressChangedEventArgs e)  
{  
   Console.WriteLine("Found service at: " + e.EndpointDiscoveryMetadata.Address  
}
  
static void discoveryClient_FindCompleted(object sender, FindCompletedEventArgs e)  
{
      if (e.Result.Endpoints.Count > 0)  
            {  
                EndpointAddress ep = e.Result.Endpoints[0].Address;  
                CalculatorServiceClient client = new CalculatorServiceClient();  
  
                // Connect to the discovered service endpoint  
                client.Endpoint.Address = ep;  
                Console.WriteLine("Invoking CalculatorService at {0}", ep);  
  
                double value1 = 100.00D;  
                double value2 = 15.99D;  
  
                double result = client.Add(value1, value2);  
                Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
            }  
            else  
                Console.WriteLine("No matching endpoints found");  
  
        }  
```
  
 <span data-ttu-id="68781-127">使用 <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> 和 <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> 方法可以查找基于其终结点地址的服务。</span><span class="sxs-lookup"><span data-stu-id="68781-127">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> and <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> methods to locate a service based on its endpoint address.</span></span> <span data-ttu-id="68781-128">如果终结点地址不是网络可寻址地址，则此操作非常有用。</span><span class="sxs-lookup"><span data-stu-id="68781-128">This is useful when the endpoint address is not network addressable.</span></span> <span data-ttu-id="68781-129">Resolve 方法接受 <xref:System.ServiceModel.Discovery.ResolveCriteria> 的实例，该实例可用于指定要解析的服务终结点地址、解析操作的最大持续时间和一组扩展。</span><span class="sxs-lookup"><span data-stu-id="68781-129">The Resolve methods take an instance of <xref:System.ServiceModel.Discovery.ResolveCriteria> which allows you to specify the endpoint address of the service you are resolving, the maximum duration of the resolve operation, and a set of extensions.</span></span> <span data-ttu-id="68781-130">下面的示例演示如何使用 <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> 方法来解析服务。</span><span class="sxs-lookup"><span data-stu-id="68781-130">The following example shows how to use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> method to resolve a service.</span></span>  
  
```csharp  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a><span data-ttu-id="68781-131">DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="68781-131">DynamicEndpoint</span></span>  
 <span data-ttu-id="68781-132"><xref:System.ServiceModel.Discovery.DynamicEndpoint>是一个标准终结点（有关详细信息，请参阅[标准终结点](standard-endpoints.md)），它执行发现并自动选择匹配的服务。</span><span class="sxs-lookup"><span data-stu-id="68781-132"><xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint (For more information, see [Standard Endpoints](standard-endpoints.md)) which performs discovery and automatically selects a matching service.</span></span> <span data-ttu-id="68781-133">只需要创建一个传入要搜索的协定和要使用的绑定的 <xref:System.ServiceModel.Discovery.DynamicEndpoint>，然后将 <xref:System.ServiceModel.Discovery.DynamicEndpoint> 实例传递给 WCF 客户端。</span><span class="sxs-lookup"><span data-stu-id="68781-133">Just create a <xref:System.ServiceModel.Discovery.DynamicEndpoint> passing in the contract to search for and the binding to use and pass the <xref:System.ServiceModel.Discovery.DynamicEndpoint> instance to the WCF client.</span></span> <span data-ttu-id="68781-134">下面的示例演示如何创建并使用 <xref:System.ServiceModel.Discovery.DynamicEndpoint> 来调用计算器服务。</span><span class="sxs-lookup"><span data-stu-id="68781-134">The following example shows how to create and use a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to call the calculator service.</span></span> <span data-ttu-id="68781-135">每次打开客户端时都会执行发现操作。</span><span class="sxs-lookup"><span data-stu-id="68781-135">The discovery is performed every time the client is opened.</span></span> <span data-ttu-id="68781-136"><xref:System.ServiceModel.Discovery.DynamicEndpoint>通过将 `kind ="dynamicEndpoint"` 属性添加到终结点配置元素，还可以将配置中定义的任何终结点转换为。</span><span class="sxs-lookup"><span data-stu-id="68781-136">Any endpoint defined in configuration can also be turned into a <xref:System.ServiceModel.Discovery.DynamicEndpoint> by adding the `kind ="dynamicEndpoint"` attribute to the endpoint configuration element.</span></span>  
  
```csharp  
DynamicEndpoint dynamicEndpoint = new DynamicEndpoint(ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
CalculatorServiceClient client = new CalculatorServiceClient(dynamicEndpoint);  
  
Console.WriteLine("Invoking CalculatorService");  
Console.WriteLine();  
  
double value1 = 100.00D;  
double value2 = 15.99D;  
  
double result = client.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
## <a name="see-also"></a><span data-ttu-id="68781-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="68781-137">See also</span></span>

- [<span data-ttu-id="68781-138">通过范围进行发现</span><span class="sxs-lookup"><span data-stu-id="68781-138">Discovery with Scopes</span></span>](../samples/discovery-with-scopes-sample.md)
- [<span data-ttu-id="68781-139">基本</span><span class="sxs-lookup"><span data-stu-id="68781-139">Basic</span></span>](../samples/basic-sample.md)

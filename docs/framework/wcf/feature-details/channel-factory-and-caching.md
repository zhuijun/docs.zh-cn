---
title: 通道工厂和缓存
ms.date: 03/30/2017
ms.assetid: 954f030e-091c-4c0e-a7a2-10f9a6b1f529
ms.openlocfilehash: 5b8348a98b484ca08e3dbeba141dc49825c8c071
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587360"
---
# <a name="channel-factory-and-caching"></a><span data-ttu-id="ee4e1-102">通道工厂和缓存</span><span class="sxs-lookup"><span data-stu-id="ee4e1-102">Channel Factory and Caching</span></span>

<span data-ttu-id="ee4e1-103">WCF 客户端应用程序使用 <xref:System.ServiceModel.ChannelFactory%601> 类来创建 WCF 服务的通信通道。</span><span class="sxs-lookup"><span data-stu-id="ee4e1-103">WCF client applications use the <xref:System.ServiceModel.ChannelFactory%601> class to create a communication channel with a WCF service.</span></span>  <span data-ttu-id="ee4e1-104">创建 <xref:System.ServiceModel.ChannelFactory%601> 实例会带来一定的开销，因为这涉及以下操作：</span><span class="sxs-lookup"><span data-stu-id="ee4e1-104">Creating <xref:System.ServiceModel.ChannelFactory%601> instances incurs some overhead because it involves the following operations:</span></span>

- <span data-ttu-id="ee4e1-105">构造 <xref:System.ServiceModel.Description.ContractDescription> 树</span><span class="sxs-lookup"><span data-stu-id="ee4e1-105">Constructing the <xref:System.ServiceModel.Description.ContractDescription> tree</span></span>

- <span data-ttu-id="ee4e1-106">反映所有所需的 CLR 类型</span><span class="sxs-lookup"><span data-stu-id="ee4e1-106">Reflecting all of the required CLR types</span></span>

- <span data-ttu-id="ee4e1-107">构造通道堆栈</span><span class="sxs-lookup"><span data-stu-id="ee4e1-107">Constructing the channel stack</span></span>

- <span data-ttu-id="ee4e1-108">资源的释放</span><span class="sxs-lookup"><span data-stu-id="ee4e1-108">Disposing of resources</span></span>

<span data-ttu-id="ee4e1-109">为了尽量减少这种开销，WCF 可以缓存使用 WCF 客户端代理时的通道工厂。</span><span class="sxs-lookup"><span data-stu-id="ee4e1-109">To help minimize this overhead, WCF can cache channel factories when you are using a WCF client proxy.</span></span>

> [!TIP]
> <span data-ttu-id="ee4e1-110">当直接使用 <xref:System.ServiceModel.ChannelFactory%601> 类时，您可以直接控制通道工厂创建。</span><span class="sxs-lookup"><span data-stu-id="ee4e1-110">You have direct control over channel factory creation when you use the <xref:System.ServiceModel.ChannelFactory%601> class directly.</span></span>

<span data-ttu-id="ee4e1-111">用[Svcutil.exe 元数据实用工具（）](../servicemodel-metadata-utility-tool-svcutil-exe.md)生成的 WCF 客户端代理派生自 <xref:System.ServiceModel.ClientBase%601> 。</span><span class="sxs-lookup"><span data-stu-id="ee4e1-111">WCF client proxies generated with [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) are derived from <xref:System.ServiceModel.ClientBase%601>.</span></span> <span data-ttu-id="ee4e1-112"><xref:System.ServiceModel.ClientBase%601> 定义一个静态 <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> 属性，该属性定义通道工厂缓存行为。</span><span class="sxs-lookup"><span data-stu-id="ee4e1-112"><xref:System.ServiceModel.ClientBase%601> defines a static <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property that defines channel factory caching behavior.</span></span> <span data-ttu-id="ee4e1-113">为特定类型设定缓存设置。</span><span class="sxs-lookup"><span data-stu-id="ee4e1-113">Cache settings are made for a specific type.</span></span> <span data-ttu-id="ee4e1-114">例如，将设置 `ClientBase<ITest>.CacheSettings` 为下面定义的值之一将仅影响类型为的代理/ClientBase `ITest` 。</span><span class="sxs-lookup"><span data-stu-id="ee4e1-114">For example, setting  `ClientBase<ITest>.CacheSettings` to one of the values defined below will affect only those proxy/ClientBase of type `ITest`.</span></span> <span data-ttu-id="ee4e1-115">特定 <xref:System.ServiceModel.ClientBase%601> 的缓存设置在创建第一个代理/ClientBase 实例后就不可改变。</span><span class="sxs-lookup"><span data-stu-id="ee4e1-115">The cache setting for a particular <xref:System.ServiceModel.ClientBase%601> is immutable as soon as the first proxy/ClientBase instance is created.</span></span>

## <a name="specifying-caching-behavior"></a><span data-ttu-id="ee4e1-116">指定缓存行为</span><span class="sxs-lookup"><span data-stu-id="ee4e1-116">Specifying Caching Behavior</span></span>

<span data-ttu-id="ee4e1-117">缓存行为通过将 <xref:System.ServiceModel.ClientBase%601.CacheSetting> 属性设置为下列值之一指定。</span><span class="sxs-lookup"><span data-stu-id="ee4e1-117">Caching behavior is specified by setting the <xref:System.ServiceModel.ClientBase%601.CacheSetting> property to one of the following values.</span></span>

|<span data-ttu-id="ee4e1-118">缓存设置值</span><span class="sxs-lookup"><span data-stu-id="ee4e1-118">Cache Setting Value</span></span>|<span data-ttu-id="ee4e1-119">描述</span><span class="sxs-lookup"><span data-stu-id="ee4e1-119">Description</span></span>|
|-------------------------|-----------------|
|<xref:System.ServiceModel.CacheSetting.AlwaysOn>|<span data-ttu-id="ee4e1-120">应用程序域内的 <xref:System.ServiceModel.ClientBase%601> 的所有实例都可以参与缓存。</span><span class="sxs-lookup"><span data-stu-id="ee4e1-120">All instances of <xref:System.ServiceModel.ClientBase%601> within the app-domain can participate in caching.</span></span> <span data-ttu-id="ee4e1-121">开发人员已经确定对缓存没有不利的安全性影响。</span><span class="sxs-lookup"><span data-stu-id="ee4e1-121">The developer has determined that there are no adverse security implications to caching.</span></span> <span data-ttu-id="ee4e1-122">即使访问了上的 "安全敏感" 属性，缓存也不会关闭 <xref:System.ServiceModel.ClientBase%601> 。</span><span class="sxs-lookup"><span data-stu-id="ee4e1-122">Caching will not be turned off even if "security-sensitive" properties on <xref:System.ServiceModel.ClientBase%601> are accessed.</span></span> <span data-ttu-id="ee4e1-123">的 "安全敏感" 属性 <xref:System.ServiceModel.ClientBase%601> 是 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> 、 <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> 和 <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A> 。</span><span class="sxs-lookup"><span data-stu-id="ee4e1-123">The "security-sensitive" properties of <xref:System.ServiceModel.ClientBase%601> are <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>, <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> and <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A>.</span></span>|
|<xref:System.ServiceModel.CacheSetting.Default>|<span data-ttu-id="ee4e1-124">只有从在配置文件中定义的终结点创建的 <xref:System.ServiceModel.ClientBase%601> 的实例才参与应用程序域内的缓存。</span><span class="sxs-lookup"><span data-stu-id="ee4e1-124">Only instances of <xref:System.ServiceModel.ClientBase%601> created from endpoints defined in configuration files participate in caching within the app-domain.</span></span> <span data-ttu-id="ee4e1-125">以编程方式在应用程序域内创建的 <xref:System.ServiceModel.ClientBase%601> 的任何实例都将不参与缓存。</span><span class="sxs-lookup"><span data-stu-id="ee4e1-125">Any instances of <xref:System.ServiceModel.ClientBase%601> created programmatically within that app-domain will not participate in caching.</span></span> <span data-ttu-id="ee4e1-126">此外， <xref:System.ServiceModel.ClientBase%601> 只要访问了其任何 "安全敏感" 属性，就会对实例禁用缓存。</span><span class="sxs-lookup"><span data-stu-id="ee4e1-126">Also, caching will be disabled for an instance of <xref:System.ServiceModel.ClientBase%601> once any of its "security-sensitive" properties is accessed.</span></span>|
|<xref:System.ServiceModel.CacheSetting.AlwaysOff>|<span data-ttu-id="ee4e1-127">在相关应用程序域内，已对特定类型的 <xref:System.ServiceModel.ClientBase%601> 的所有实例关闭缓存。</span><span class="sxs-lookup"><span data-stu-id="ee4e1-127">Caching is turned off for all instances of <xref:System.ServiceModel.ClientBase%601> of a particular type within the app-domain in question.</span></span>|

<span data-ttu-id="ee4e1-128">下面的代码段演示如何使用 <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="ee4e1-128">The following code snippets illustrate how to use the <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property.</span></span>

```csharp
class Program
{
   static void Main(string[] args)
   {
      ClientBase<ITest>.CacheSettings = CacheSettings.AlwaysOn;
      foreach (string msg in messages)
      {
         using (TestClient proxy = new TestClient (new BasicHttpBinding(), new EndpointAddress(address)))
         {
            // ...
            proxy.Test(msg);
            // ...
         }
      }
   }
}
// Generated by SvcUtil.exe
public partial class TestClient : System.ServiceModel.ClientBase, ITest { }
```

<span data-ttu-id="ee4e1-129">在上述代码中，`TestClient` 的所有实例都将使用相同的通道工厂。</span><span class="sxs-lookup"><span data-stu-id="ee4e1-129">In the above code, all instances of `TestClient` will use the same channel factory.</span></span>

```csharp
class Program
{
   static void Main(string[] args)
   {
      ClientBase.CacheSettings = CacheSettings.Default;
      int i = 1;
      foreach (string msg in messages)
      {
         using (TestClient proxy = new TestClient ("MyEndpoint", new EndpointAddress(address)))
         {
            if (i == 4)
            {
               ServiceEndpoint endpoint = proxy.Endpoint;
               ... // use endpoint in some way
            }
            proxy.Test(msg);
         }
         i++;
   }
}

// Generated by SvcUtil.exe
public partial class TestClient : System.ServiceModel.ClientBase, ITest {}
```

<span data-ttu-id="ee4e1-130">在上述示例中，`TestClient` 的所有实例都将使用相同的通道工厂，实例 #4 除外。</span><span class="sxs-lookup"><span data-stu-id="ee4e1-130">In the example above, all instances of `TestClient` would use the same channel factory except instance #4.</span></span> <span data-ttu-id="ee4e1-131">实例 # 4 将使用专门供其使用而创建的通道工厂。</span><span class="sxs-lookup"><span data-stu-id="ee4e1-131">Instance #4 would use a channel factory that is created specifically for its use.</span></span> <span data-ttu-id="ee4e1-132">此设置适用于此类方案：特定终结点需要的安全设置不同于属于相同通道工厂类型（在此情况下为 `ITest`）的其他终结点。</span><span class="sxs-lookup"><span data-stu-id="ee4e1-132">This setting would work for scenarios where a particular endpoint needs different security settings from the other endpoints of the same channel factory type (in this case `ITest`).</span></span>

```csharp
class Program
{
   static void Main(string[] args)
   {
      ClientBase.CacheSettings = CacheSettings.AlwaysOff;
      foreach (string msg in messages)
      {
         using (TestClient proxy = new TestClient ("MyEndpoint", new EndpointAddress(address)))
         {
            proxy.Test(msg);
         }
      }
   }
}

// Generated by SvcUtil.exe
public partial class TestClient : System.ServiceModel.ClientBase, ITest {}
```

<span data-ttu-id="ee4e1-133">在上面的示例中，`TestClient` 的所有实例将使用不同的通道工厂。</span><span class="sxs-lookup"><span data-stu-id="ee4e1-133">In the example above, all instances of `TestClient` would use different channel factories.</span></span> <span data-ttu-id="ee4e1-134">当每个终结点具有不同的安全需求并且对缓存没有意义时，这非常有用。</span><span class="sxs-lookup"><span data-stu-id="ee4e1-134">This is useful when each endpoint has different security requirements and it makes no sense to cache.</span></span>

## <a name="see-also"></a><span data-ttu-id="ee4e1-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ee4e1-135">See also</span></span>

- <xref:System.ServiceModel.ClientBase%601>
- [<span data-ttu-id="ee4e1-136">生成客户端</span><span class="sxs-lookup"><span data-stu-id="ee4e1-136">Building Clients</span></span>](../building-clients.md)
- [<span data-ttu-id="ee4e1-137">客户端</span><span class="sxs-lookup"><span data-stu-id="ee4e1-137">Clients</span></span>](clients.md)
- [<span data-ttu-id="ee4e1-138">使用 WCF 客户端访问服务</span><span class="sxs-lookup"><span data-stu-id="ee4e1-138">Accessing Services Using a WCF Client</span></span>](../accessing-services-using-a-wcf-client.md)
- [<span data-ttu-id="ee4e1-139">如何：使用 ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="ee4e1-139">How to: Use the ChannelFactory</span></span>](how-to-use-the-channelfactory.md)

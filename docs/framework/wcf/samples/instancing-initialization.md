---
title: 实例化初始化
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: 06a8dfe571b652ded236df3097b37861c03a858d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596651"
---
# <a name="instancing-initialization"></a><span data-ttu-id="7c734-102">实例化初始化</span><span class="sxs-lookup"><span data-stu-id="7c734-102">Instancing Initialization</span></span>
<span data-ttu-id="7c734-103">此示例通过定义接口扩展了[池](pooling.md)采样， `IObjectControl` 该接口通过激活和停用来自定义对象的初始化。</span><span class="sxs-lookup"><span data-stu-id="7c734-103">This sample extends the [Pooling](pooling.md) sample by defining an interface, `IObjectControl`, which customizes the initialization of an object by activating and deactivating it.</span></span> <span data-ttu-id="7c734-104">客户端调用向池中返回对象以及不向池中返回对象的方法。</span><span class="sxs-lookup"><span data-stu-id="7c734-104">The client invokes methods that return the object to the pool and that do not return the object to the pool.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7c734-105">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="7c734-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="extensibility-points"></a><span data-ttu-id="7c734-106">扩展点</span><span class="sxs-lookup"><span data-stu-id="7c734-106">Extensibility Points</span></span>  
 <span data-ttu-id="7c734-107">创建 Windows Communication Foundation （WCF）扩展的第一步是确定要使用的扩展点。</span><span class="sxs-lookup"><span data-stu-id="7c734-107">The first step in creating a Windows Communication Foundation (WCF) extension is to decide the extensibility point to use.</span></span> <span data-ttu-id="7c734-108">在 WCF 中，术语 " *EndpointDispatcher* " 指的是一个运行时组件，该组件负责将传入消息转换成用户服务上的方法调用，并将该方法的返回值转换为传出消息。</span><span class="sxs-lookup"><span data-stu-id="7c734-108">In WCF, the term *EndpointDispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="7c734-109">WCF 服务为每个终结点创建 EndpointDispatcher。</span><span class="sxs-lookup"><span data-stu-id="7c734-109">A WCF service creates an EndpointDispatcher for each endpoint.</span></span>  
  
 <span data-ttu-id="7c734-110">EndpointDispatcher 使用 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> 类提供终结点范围（适用于服务收到或发送的所有消息）的扩展。</span><span class="sxs-lookup"><span data-stu-id="7c734-110">The EndpointDispatcher offers endpoint scope (for all messages received or sent by the service) extensibility using the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> class.</span></span> <span data-ttu-id="7c734-111">通过此类可以自定义控制 EndpointDispatcher 行为的各种属性。</span><span class="sxs-lookup"><span data-stu-id="7c734-111">This class allows you to customize various properties that control the behavior of the EndpointDispatcher.</span></span> <span data-ttu-id="7c734-112">本示例重点介绍 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> 属性，该属性指向提供服务类实例的对象。</span><span class="sxs-lookup"><span data-stu-id="7c734-112">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="iinstanceprovider"></a><span data-ttu-id="7c734-113">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="7c734-113">IInstanceProvider</span></span>  
 <span data-ttu-id="7c734-114">在 WCF 中，EndpointDispatcher 通过使用实现接口的实例提供程序来创建服务类的实例 <xref:System.ServiceModel.Dispatcher.IInstanceProvider> 。</span><span class="sxs-lookup"><span data-stu-id="7c734-114">In WCF, the EndpointDispatcher creates instances of a service class by using an instance provider that implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="7c734-115">此接口只有两个方法：</span><span class="sxs-lookup"><span data-stu-id="7c734-115">This interface has only two methods:</span></span>  
  
- <span data-ttu-id="7c734-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>：当消息到达时，Dispatcher 调用 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> 方法，以创建服务类的实例来处理该消息。</span><span class="sxs-lookup"><span data-stu-id="7c734-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: When a message arrives, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="7c734-117">调用此方法的频率由 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 属性决定。</span><span class="sxs-lookup"><span data-stu-id="7c734-117">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="7c734-118">例如，如果 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 属性设置为 <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>，则创建服务类的一个新实例来处理到达的每个消息，因此每当有消息到达时，都会调用 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>。</span><span class="sxs-lookup"><span data-stu-id="7c734-118">For example if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="7c734-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>：当服务实例处理完消息后，EndpointDispatcher 将调用 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="7c734-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: When the service instance finishes processing the message, the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method.</span></span> <span data-ttu-id="7c734-120">与 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> 方法中一样，调用此方法的频率由 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 属性决定。</span><span class="sxs-lookup"><span data-stu-id="7c734-120">As in the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="7c734-121">对象池</span><span class="sxs-lookup"><span data-stu-id="7c734-121">The Object Pool</span></span>  
 <span data-ttu-id="7c734-122">`ObjectPoolInstanceProvider` 类包含对象池的实现。</span><span class="sxs-lookup"><span data-stu-id="7c734-122">The `ObjectPoolInstanceProvider` class contains the implementation for the object pool.</span></span> <span data-ttu-id="7c734-123">此类实现 <xref:System.ServiceModel.Dispatcher.IInstanceProvider> 接口，以便与服务模型层进行交互。</span><span class="sxs-lookup"><span data-stu-id="7c734-123">This class implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface to interact with the service model layer.</span></span> <span data-ttu-id="7c734-124">当 EndpointDispatcher 调用 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> 方法时，自定义实现将在内存中的池内寻找现有对象，而不是创建新的实例。</span><span class="sxs-lookup"><span data-stu-id="7c734-124">When the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="7c734-125">如果找到一个对象，则返回该对象。</span><span class="sxs-lookup"><span data-stu-id="7c734-125">If one is available, it is returned.</span></span> <span data-ttu-id="7c734-126">否则，`ObjectPoolInstanceProvider` 则检查 `ActiveObjectsCount` 属性（从池中返回的对象数）是否已达到最大池大小。</span><span class="sxs-lookup"><span data-stu-id="7c734-126">Otherwise, `ObjectPoolInstanceProvider` checks whether the `ActiveObjectsCount` property (number of objects returned from the pool) has reached the maximum pool size.</span></span> <span data-ttu-id="7c734-127">如果没有达到最大池大小，则创建一个新实例并将其返回调用方，而 `ActiveObjectsCount` 则相应地增加。</span><span class="sxs-lookup"><span data-stu-id="7c734-127">If not, a new instance is created and returned to the caller and `ActiveObjectsCount` is subsequently incremented.</span></span> <span data-ttu-id="7c734-128">否则，对象创建请求将排队，等待配置的时间段。</span><span class="sxs-lookup"><span data-stu-id="7c734-128">Otherwise an object creation request is queued for a configured period of time.</span></span> <span data-ttu-id="7c734-129">下面的示例代码演示了 `GetObjectFromThePool` 的实现。</span><span class="sxs-lookup"><span data-stu-id="7c734-129">The implementation for `GetObjectFromThePool` is shown in the following sample code.</span></span>  
  
```csharp
private object GetObjectFromThePool()  
{  
    bool didNotTimeout =
       availableCount.WaitOne(creationTimeout, true);  
    if(didNotTimeout)  
    {  
         object obj = null;  
         lock (poolLock)  
        {  
             if (pool.Count != 0)  
             {  
                   obj = pool.Pop();  
                   activeObjectsCount++;  
             }  
             else if (pool.Count == 0)  
             {  
                   if (activeObjectsCount < maxPoolSize)  
                   {  
                        obj = CreateNewPoolObject();  
                        activeObjectsCount++;  
  
                        #if (DEBUG)  
                        WritePoolMessage(  
                             ResourceHelper.GetString("MsgNewObject"));  
                       #endif  
                   }
            }  
           idleTimer.Stop();  
      }  
     // Call the Activate method if possible.  
    if (obj is IObjectControl)  
   {  
         ((IObjectControl)obj).Activate();  
   }  
   return obj;  
}  
throw new TimeoutException(  
ResourceHelper.GetString("ExObjectCreationTimeout"));  
}  
```  
  
 <span data-ttu-id="7c734-130">自定义 `ReleaseInstance` 实现将已释放的实例重新添加回池中并减少 `ActiveObjectsCount` 值。</span><span class="sxs-lookup"><span data-stu-id="7c734-130">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="7c734-131">EndpointDispatcher 可以从不同的线程调用这些方法，因此需要同步访问 `ObjectPoolInstanceProvider` 类中的类级别成员。</span><span class="sxs-lookup"><span data-stu-id="7c734-131">The EndpointDispatcher can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolInstanceProvider` class is required.</span></span>  
  
```csharp
public void ReleaseInstance(InstanceContext instanceContext, object instance)  
{  
    lock (poolLock)  
    {  
        // Check whether the object can be pooled.
        // Call the Deactivate method if possible.  
        if (instance is IObjectControl)  
        {  
            IObjectControl objectControl = (IObjectControl)instance;  
            objectControl.Deactivate();  
  
            if (objectControl.CanBePooled)  
            {  
                pool.Push(instance);  
  
                #if(DEBUG)  
                WritePoolMessage(  
                    ResourceHelper.GetString("MsgObjectPooled"));  
                #endif
            }  
            else  
            {  
                #if(DEBUG)  
                WritePoolMessage(  
                    ResourceHelper.GetString("MsgObjectWasNotPooled"));  
                #endif  
            }  
        }  
        else  
        {  
            pool.Push(instance);  
  
            #if(DEBUG)  
            WritePoolMessage(  
                ResourceHelper.GetString("MsgObjectPooled"));  
            #endif
        }  
  
        activeObjectsCount--;  
  
        if (activeObjectsCount == 0)  
        {  
            idleTimer.Start();
        }  
    }  
  
    availableCount.Release(1);  
}  
```  
  
 <span data-ttu-id="7c734-132">`ReleaseInstance`方法提供了*清理初始化*功能。</span><span class="sxs-lookup"><span data-stu-id="7c734-132">The `ReleaseInstance` method provides a *clean up initialization* feature.</span></span> <span data-ttu-id="7c734-133">通常，该池为其生存期保持最少数量的对象。</span><span class="sxs-lookup"><span data-stu-id="7c734-133">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="7c734-134">但是，可能有过度使用的时期，此时需要在池中创建更多对象以达到配置中指定的最大限制。</span><span class="sxs-lookup"><span data-stu-id="7c734-134">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="7c734-135">最终，当池变得不是很活跃时，那些多余的对象可能会变成额外的开销。</span><span class="sxs-lookup"><span data-stu-id="7c734-135">Eventually when the pool becomes less active those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="7c734-136">因此，当 `activeObjectsCount` 达到 0 时，会启动一个空闲计时器，该计时器将触发并执行清除循环。</span><span class="sxs-lookup"><span data-stu-id="7c734-136">Therefore when the `activeObjectsCount` reaches zero an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
```csharp  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();
}  
```  
  
 <span data-ttu-id="7c734-137">使用以下行为对 ServiceModel 层扩展进行挂钩：</span><span class="sxs-lookup"><span data-stu-id="7c734-137">ServiceModel layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="7c734-138">服务行为：这些行为允许自定义整个服务运行时。</span><span class="sxs-lookup"><span data-stu-id="7c734-138">Service Behaviors: These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="7c734-139">终结点行为：这些行为允许自定义特定的服务终结点，包括 EndpointDispatcher。</span><span class="sxs-lookup"><span data-stu-id="7c734-139">Endpoint Behaviors: These allow for the customization of a particular service endpoint, including the EndpointDispatcher.</span></span>  
  
- <span data-ttu-id="7c734-140">协定行为：这些行为允许在客户端或服务上分别自定义 <xref:System.ServiceModel.Dispatcher.ClientRuntime> 或 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> 类。</span><span class="sxs-lookup"><span data-stu-id="7c734-140">Contract Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientRuntime> or <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client or the service respectively.</span></span>  
  
- <span data-ttu-id="7c734-141">操作行为：这些行为允许在客户端或服务上分别自定义 <xref:System.ServiceModel.Dispatcher.ClientOperation> 或 <xref:System.ServiceModel.Dispatcher.DispatchOperation> 类。</span><span class="sxs-lookup"><span data-stu-id="7c734-141">Operation Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientOperation> or <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes on the client or the service respectively.</span></span>  
  
 <span data-ttu-id="7c734-142">为了实现对象池扩展，可以创建终结点行为或服务行为。</span><span class="sxs-lookup"><span data-stu-id="7c734-142">For the purpose of an object pooling extension, either an endpoint behavior or a service behavior can be created.</span></span> <span data-ttu-id="7c734-143">在此示例中，我们使用了服务行为，它使服务的每个终结点都具有对象池能力。</span><span class="sxs-lookup"><span data-stu-id="7c734-143">In this example, we use a service behavior, which applies object pooling ability to every endpoint of the service.</span></span> <span data-ttu-id="7c734-144">服务行为是通过实现 <xref:System.ServiceModel.Description.IServiceBehavior> 接口创建的。</span><span class="sxs-lookup"><span data-stu-id="7c734-144">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="7c734-145">可以通过多种方式让 ServiceModel 注意到自定义行为：</span><span class="sxs-lookup"><span data-stu-id="7c734-145">There are several ways to make the ServiceModel aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="7c734-146">使用自定义属性。</span><span class="sxs-lookup"><span data-stu-id="7c734-146">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="7c734-147">强制将它添加到服务说明的行为集合中。</span><span class="sxs-lookup"><span data-stu-id="7c734-147">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="7c734-148">扩展配置文件。</span><span class="sxs-lookup"><span data-stu-id="7c734-148">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="7c734-149">本示例使用自定义属性。</span><span class="sxs-lookup"><span data-stu-id="7c734-149">This sample uses a custom attribute.</span></span> <span data-ttu-id="7c734-150">构造 <xref:System.ServiceModel.ServiceHost> 后，它检查服务类型定义中使用的属性并将可用行为添加到服务说明的行为集合中。</span><span class="sxs-lookup"><span data-stu-id="7c734-150">When the <xref:System.ServiceModel.ServiceHost> is constructed, it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="7c734-151"><xref:System.ServiceModel.Description.IServiceBehavior>接口有三种方法： <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> `,` 和 <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> 。</span><span class="sxs-lookup"><span data-stu-id="7c734-151">The <xref:System.ServiceModel.Description.IServiceBehavior> interface has three methods: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>`,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>`,` and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="7c734-152">初始化时，WCF 将调用这些方法 <xref:System.ServiceModel.ServiceHost> 。</span><span class="sxs-lookup"><span data-stu-id="7c734-152">These methods are called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="7c734-153">首先调用 <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType>；它允许检查服务的一致性。</span><span class="sxs-lookup"><span data-stu-id="7c734-153"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> is called first; it allows the service to be inspected for inconsistencies.</span></span> <span data-ttu-id="7c734-154">然后调用 <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType>；只有非常高级的方案才需要此方法。</span><span class="sxs-lookup"><span data-stu-id="7c734-154"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> is called next; this method is only required in very advanced scenarios.</span></span> <span data-ttu-id="7c734-155">最后调用 <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>，它负责配置运行时。</span><span class="sxs-lookup"><span data-stu-id="7c734-155"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> is called last and is responsible for configuring the runtime.</span></span> <span data-ttu-id="7c734-156">下面的参数传递给 <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>：</span><span class="sxs-lookup"><span data-stu-id="7c734-156">The following parameters are passed into <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:</span></span>  
  
- <span data-ttu-id="7c734-157">`Description`：此参数提供整个服务的服务说明。</span><span class="sxs-lookup"><span data-stu-id="7c734-157">`Description`: This parameter provides the service description for the entire service.</span></span> <span data-ttu-id="7c734-158">它可用于检查有关服务的终结点、协定、绑定和其他关联数据的说明数据。</span><span class="sxs-lookup"><span data-stu-id="7c734-158">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data associated with the service.</span></span>  
  
- <span data-ttu-id="7c734-159">`ServiceHostBase`：此参数提供当前正在初始化的 <xref:System.ServiceModel.ServiceHostBase>。</span><span class="sxs-lookup"><span data-stu-id="7c734-159">`ServiceHostBase`: This parameter provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="7c734-160">在自定义 <xref:System.ServiceModel.Description.IServiceBehavior> 实现中，会实例化 `ObjectPoolInstanceProvider` 的一个新实例，并将其分配给附加到 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> 的每个 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> 的 <xref:System.ServiceModel.ServiceHostBase> 属性。</span><span class="sxs-lookup"><span data-stu-id="7c734-160">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation, a new instance of `ObjectPoolInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> that is attached to the <xref:System.ServiceModel.ServiceHostBase>.</span></span>  
  
```csharp
public void ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
{  
    if (enabled)  
    {  
        // Create an instance of the ObjectPoolInstanceProvider.  
        instanceProvider = new ObjectPoolInstanceProvider(description.ServiceType,  
        maxPoolSize, minPoolSize, creationTimeout);  
  
        // Assign our instance provider to Dispatch behavior in each
        // endpoint.  
        foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)  
        {  
             ChannelDispatcher cd = cdb as ChannelDispatcher;  
             if (cd != null)  
             {  
                 foreach (EndpointDispatcher ed in cd.Endpoints)  
                 {  
                        ed.DispatchRuntime.InstanceProvider = instanceProvider;  
                 }  
             }  
         }  
     }  
}
```  
  
 <span data-ttu-id="7c734-161">除了 <xref:System.ServiceModel.Description.IServiceBehavior> 实现外，`ObjectPoolingAttribute` 类有多个可以使用属性自变量自定义对象池的成员。</span><span class="sxs-lookup"><span data-stu-id="7c734-161">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the `ObjectPoolingAttribute` class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="7c734-162">这些成员包括 `MaxSize`、`MinSize`、`Enabled` 和 `CreationTimeout`，用于匹配 .NET 企业服务提供的对象池功能集。</span><span class="sxs-lookup"><span data-stu-id="7c734-162">These members include `MaxSize`, `MinSize`, `Enabled` and `CreationTimeout`, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="7c734-163">现在可以通过使用新创建的自定义特性对服务实现进行批注，将对象池行为添加到 WCF 服务 `ObjectPooling` 。</span><span class="sxs-lookup"><span data-stu-id="7c734-163">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```csharp  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a><span data-ttu-id="7c734-164">挂钩激活和停用</span><span class="sxs-lookup"><span data-stu-id="7c734-164">Hooking Activation and Deactivation</span></span>  
 <span data-ttu-id="7c734-165">对象池的主要目的是通过代价相对较高的创建和初始化来优化生存期较短的对象。</span><span class="sxs-lookup"><span data-stu-id="7c734-165">The primary objective of object pooling is to optimize short-lived objects with relatively expensive creation and initialization.</span></span> <span data-ttu-id="7c734-166">因此，如果使用得当，它可以显著提高应用程序的性能。</span><span class="sxs-lookup"><span data-stu-id="7c734-166">Therefore it can give a dramatic performance boost to an application if properly used.</span></span> <span data-ttu-id="7c734-167">因为对象是从池中返回的，所以只调用构造函数一次。</span><span class="sxs-lookup"><span data-stu-id="7c734-167">Because the object is returned from the pool, the constructor is called only once.</span></span> <span data-ttu-id="7c734-168">但是，有些应用程序需要某种级别的控制，以便初始化和清除单一上下文中使用的资源。</span><span class="sxs-lookup"><span data-stu-id="7c734-168">However, some applications require some level of control so that they can initialize and clean-up the resources used during a single context.</span></span> <span data-ttu-id="7c734-169">例如，用于一组计算的某个对象可以在处理下一个计算之前重置其私有字段。</span><span class="sxs-lookup"><span data-stu-id="7c734-169">For example, an object being used for a set of calculations can reset its private fields before processing the next calculation.</span></span> <span data-ttu-id="7c734-170">企业服务通过允许对象开发人员重写 `Activate` 基类中的 `Deactivate` 和 <xref:System.EnterpriseServices.ServicedComponent> 方法，实现了这种上下文特定的初始化。</span><span class="sxs-lookup"><span data-stu-id="7c734-170">Enterprise Services enabled this kind of context-specific initialization by letting the object developer override `Activate` and `Deactivate` methods from the <xref:System.EnterpriseServices.ServicedComponent> base class.</span></span>  
  
 <span data-ttu-id="7c734-171">对象池就在从池中返回对象之前调用 `Activate` 方法。</span><span class="sxs-lookup"><span data-stu-id="7c734-171">The object pool calls the `Activate` method just before returning the object from the pool.</span></span> <span data-ttu-id="7c734-172">当对象重新返回到池中后，将调用 `Deactivate`。</span><span class="sxs-lookup"><span data-stu-id="7c734-172">`Deactivate` is called when the object returns back to the pool.</span></span> <span data-ttu-id="7c734-173"><xref:System.EnterpriseServices.ServicedComponent> 基类还有一个称为 `boolean` 的 `CanBePooled` 属性，它可用于通知池是否可以对对象进一步进行池处理。</span><span class="sxs-lookup"><span data-stu-id="7c734-173">The <xref:System.EnterpriseServices.ServicedComponent> base class also has a `boolean` property called `CanBePooled`, which can be used to notify the pool whether the object can be pooled further.</span></span>  
  
 <span data-ttu-id="7c734-174">为了模拟此功能，此示例声明了一个具有上述成员的公共接口 (`IObjectControl`)。</span><span class="sxs-lookup"><span data-stu-id="7c734-174">To mimic this functionality, the sample declares a public interface (`IObjectControl`) that has the aforementioned members.</span></span> <span data-ttu-id="7c734-175">此接口然后由用来提供上下文特定初始化的服务类来实现。</span><span class="sxs-lookup"><span data-stu-id="7c734-175">This interface is then implemented by service classes intended to provide context specific initialization.</span></span> <span data-ttu-id="7c734-176">必须修改 <xref:System.ServiceModel.Dispatcher.IInstanceProvider> 实现才能满足这些要求。</span><span class="sxs-lookup"><span data-stu-id="7c734-176">The <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation must be modified to meet these requirements.</span></span> <span data-ttu-id="7c734-177">现在，每次通过调用方法获取对象时 `GetInstance` ，必须检查该对象是否实现 `IObjectControl.` （如果它存在），必须 `Activate` 相应地调用方法。</span><span class="sxs-lookup"><span data-stu-id="7c734-177">Now, each time you get an object by calling the `GetInstance` method, you must check whether the object implements `IObjectControl.` If it does, you must call the `Activate` method appropriately.</span></span>  
  
```csharp  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 <span data-ttu-id="7c734-178">将对象返回池中时，需要在将对象添加回池之前检查 `CanBePooled` 属性。</span><span class="sxs-lookup"><span data-stu-id="7c734-178">When returning an object to the pool, a check is required for the `CanBePooled` property before adding the object back to the pool.</span></span>  
  
```csharp  
if (instance is IObjectControl)  
{  
    IObjectControl objectControl = (IObjectControl)instance;  
    objectControl.Deactivate();  
    if (objectControl.CanBePooled)  
    {  
       pool.Push(instance);  
    }  
}  
```  
  
 <span data-ttu-id="7c734-179">因为服务开发人员可以决定对象是否可以进行池处理，所以池中的对象计数在给定时间可以低于最小大小。</span><span class="sxs-lookup"><span data-stu-id="7c734-179">Because the service developer can decide whether an object can be pooled, the object count in the pool at a given time can go below the minimum size.</span></span> <span data-ttu-id="7c734-180">因此，您必须检查对象计数是否低于最小水平，并在清除过程中执行必要的初始化。</span><span class="sxs-lookup"><span data-stu-id="7c734-180">Therefore you must check whether the object count has gone below the minimum level and perform the necessary initialization in the clean-up procedure.</span></span>  
  
```csharp  
// Remove the surplus objects.  
if (pool.Count > minPoolSize)  
{  
  // Clean the surplus objects.  
}
else if (pool.Count < minPoolSize)  
{  
  // Reinitialize the missing objects.  
  while(pool.Count != minPoolSize)  
  {  
    pool.Push(CreateNewPoolObject());  
  }  
}  
```  
  
 <span data-ttu-id="7c734-181">运行示例时，操作请求和响应将显示在服务和客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="7c734-181">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="7c734-182">在每个控制台窗口中按 Enter 可以关闭服务和客户端。</span><span class="sxs-lookup"><span data-stu-id="7c734-182">Press Enter in each console window to shut down the service and client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7c734-183">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="7c734-183">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7c734-184">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="7c734-184">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="7c734-185">若要生成解决方案，请按照[生成 Windows Communication Foundation 示例](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="7c734-185">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="7c734-186">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="7c734-186">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7c734-187">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="7c734-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7c734-188">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="7c734-188">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="7c734-189">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="7c734-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7c734-190">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="7c734-190">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  

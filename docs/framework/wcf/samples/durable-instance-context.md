---
title: 持久性实例上下文
ms.date: 03/30/2017
ms.assetid: 97bc2994-5a2c-47c7-927a-c4cd273153df
ms.openlocfilehash: 567ca62d48e80993328548b11f8b59c4fcd355fe
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600589"
---
# <a name="durable-instance-context"></a><span data-ttu-id="7f757-102">持久性实例上下文</span><span class="sxs-lookup"><span data-stu-id="7f757-102">Durable Instance Context</span></span>

<span data-ttu-id="7f757-103">此示例演示如何自定义 Windows Communication Foundation （WCF）运行时以启用持久实例上下文。</span><span class="sxs-lookup"><span data-stu-id="7f757-103">This sample demonstrates how to customize the Windows Communication Foundation (WCF) runtime to enable durable instance contexts.</span></span> <span data-ttu-id="7f757-104">它使用 SQL Server 2005 作为其后备存储（在本例中为 SQL Server 2005 Express）。</span><span class="sxs-lookup"><span data-stu-id="7f757-104">It uses SQL Server 2005 as its backing store (SQL Server 2005 Express in this case).</span></span> <span data-ttu-id="7f757-105">但是，它还提供了一种访问自定义存储机制的方法。</span><span class="sxs-lookup"><span data-stu-id="7f757-105">However, it also provides a way to access custom storage mechanisms.</span></span>

> [!NOTE]
> <span data-ttu-id="7f757-106">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="7f757-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="7f757-107">此示例涉及同时扩展 WCF 的通道层和服务模型层。</span><span class="sxs-lookup"><span data-stu-id="7f757-107">This sample involves extending both the channel layer and the service model layer of the WCF.</span></span> <span data-ttu-id="7f757-108">因此，有必要先了解基础概念再阅读实现细节。</span><span class="sxs-lookup"><span data-stu-id="7f757-108">Therefore it is necessary to understand the underlying concepts before going into the implementation details.</span></span>

<span data-ttu-id="7f757-109">持久性实例上下文在实际方案中相当常见。</span><span class="sxs-lookup"><span data-stu-id="7f757-109">Durable instance contexts can be found in the real world scenarios quite often.</span></span> <span data-ttu-id="7f757-110">例如，购物车应用程序能够暂停一半购物，并在另一天继续。</span><span class="sxs-lookup"><span data-stu-id="7f757-110">A shopping cart application, for example, has the ability to pause shopping halfway through and continue it on another day.</span></span> <span data-ttu-id="7f757-111">因此，当我们改天访问购物车应用程序时，我们的原始上下文将得以还原。</span><span class="sxs-lookup"><span data-stu-id="7f757-111">So that when we visit the shopping cart the next day, our original context is restored.</span></span> <span data-ttu-id="7f757-112">一定要注意的是，当我们断开连接时，购物车应用程序（在服务器上）不保持购物车实例，</span><span class="sxs-lookup"><span data-stu-id="7f757-112">It is important to note that the shopping cart application (on the server) does not maintain the shopping cart instance while we are disconnected.</span></span> <span data-ttu-id="7f757-113">而是将其状态保持在持久性存储介质中，并使用它为还原后的上下文构造新实例。</span><span class="sxs-lookup"><span data-stu-id="7f757-113">Instead, it persists its state into a durable storage media and uses it when constructing a new instance for the restored context.</span></span> <span data-ttu-id="7f757-114">因此，可为同一个上下文服务的服务实例与上一个实例不同（即，这两个实例的内存地址不同）。</span><span class="sxs-lookup"><span data-stu-id="7f757-114">Therefore the service instance that may service for the same context is not the same as the previous instance (that is, it does not have the same memory address).</span></span>

<span data-ttu-id="7f757-115">持久性实例上下文是由在客户端和服务之间交换上下文 ID 的小型协议来实现的。</span><span class="sxs-lookup"><span data-stu-id="7f757-115">Durable instance context is made possible by a small protocol that exchanges a context ID between the client and service.</span></span> <span data-ttu-id="7f757-116">这个上下文 ID 是在客户端上创建的，然后传输到服务。</span><span class="sxs-lookup"><span data-stu-id="7f757-116">This context ID is created on the client and transmitted to the service.</span></span> <span data-ttu-id="7f757-117">在创建了服务实例之后，服务运行库将尝试加载所保持的状态，该状态与持久性存储（默认为 SQL Server 2005 数据库）中的这个上下文 ID 相对应。</span><span class="sxs-lookup"><span data-stu-id="7f757-117">When the service instance is created, the service runtime tries to load the persisted state that corresponds to this context ID from a persistent storage (by default it is a SQL Server 2005 database).</span></span> <span data-ttu-id="7f757-118">如果没有可用状态，则新实例将具有其默认状态。</span><span class="sxs-lookup"><span data-stu-id="7f757-118">If no state is available, the new instance has its default state.</span></span> <span data-ttu-id="7f757-119">服务实现功能使用自定义属性来标记用于更改服务实现状态的操作，以便该运行库可以在调用这些操作之后保存服务实例。</span><span class="sxs-lookup"><span data-stu-id="7f757-119">The service implementation uses a custom attribute to mark operations that change the state of the service implementation so that the runtime can save the service instance after invoking them.</span></span>

<span data-ttu-id="7f757-120">根据上面的说明，可以通过方便地区分以下两个步骤来实现目标：</span><span class="sxs-lookup"><span data-stu-id="7f757-120">By the previous description, two steps can easily be distinguished to achieve the goal:</span></span>

1. <span data-ttu-id="7f757-121">更改在网络上传递的消息，使其包含上下文 ID。</span><span class="sxs-lookup"><span data-stu-id="7f757-121">Change the message that goes on the wire to carry the context ID.</span></span>

2. <span data-ttu-id="7f757-122">更改服务的本地行为，以便实现自定义实例化逻辑。</span><span class="sxs-lookup"><span data-stu-id="7f757-122">Change the service local behavior to implement custom instancing logic.</span></span>

<span data-ttu-id="7f757-123">由于列表中的第一个会影响网络上的消息，因此应将其作为自定义通道实现，并挂钩到通道层。</span><span class="sxs-lookup"><span data-stu-id="7f757-123">Because the first one in the list affects the messages on the wire, it should be implemented as a custom channel and be hooked up to the channel layer.</span></span> <span data-ttu-id="7f757-124">第二项会影响服务的本地行为，因此可以通过扩展几个服务扩展点来实现。</span><span class="sxs-lookup"><span data-stu-id="7f757-124">The latter only affects the service local behavior and therefore can be implemented by extending several service extensibility points.</span></span> <span data-ttu-id="7f757-125">随后的几节将分别讨论其中的每个扩展。</span><span class="sxs-lookup"><span data-stu-id="7f757-125">In the next few sections, each of these extensions are discussed.</span></span>

## <a name="durable-instancecontext-channel"></a><span data-ttu-id="7f757-126">持久性 InstanceContext 通道</span><span class="sxs-lookup"><span data-stu-id="7f757-126">Durable InstanceContext Channel</span></span>

<span data-ttu-id="7f757-127">要查看的第一项就是通道层扩展。</span><span class="sxs-lookup"><span data-stu-id="7f757-127">The first thing to look at is a channel layer extension.</span></span> <span data-ttu-id="7f757-128">编写自定义通道时的第一步就是确定通道的通信结构。</span><span class="sxs-lookup"><span data-stu-id="7f757-128">The first step in writing a custom channel is to decide the communication structure of the channel.</span></span> <span data-ttu-id="7f757-129">由于引入了新的网络协议，通道应与通道堆栈中的几乎所有其他通道一起工作。</span><span class="sxs-lookup"><span data-stu-id="7f757-129">As a new wire protocol is being introduced, the channel should work with almost any other channel in the channel stack.</span></span> <span data-ttu-id="7f757-130">因此它应当支持所有的消息交换模式。</span><span class="sxs-lookup"><span data-stu-id="7f757-130">Therefore it should support all the message exchange patterns.</span></span> <span data-ttu-id="7f757-131">但是，无论通道的通信结构如何，其核心功能都是相同的。</span><span class="sxs-lookup"><span data-stu-id="7f757-131">However, the core functionality of the channel is the same regardless of its communication structure.</span></span> <span data-ttu-id="7f757-132">更具体地说，在客户端上，它应当将上下文 ID 写入消息中；在服务中，它应当从消息中读取这个上下文 ID 并将其传递到较高层。</span><span class="sxs-lookup"><span data-stu-id="7f757-132">More specifically, from the client it should write the context ID to the messages and from the service it should read this context ID from the messages and pass it to the upper levels.</span></span> <span data-ttu-id="7f757-133">因此，创建了一个 `DurableInstanceContextChannelBase` 类，该类充当所有持久性实例上下文通道实现的抽象基类。</span><span class="sxs-lookup"><span data-stu-id="7f757-133">Because of that, a `DurableInstanceContextChannelBase` class is created that acts as the abstract base class for all durable instance context channel implementations.</span></span> <span data-ttu-id="7f757-134">该类中包含常见的状态机管理功能，以及两个用来将上下文信息应用于消息并从消息中读取上下文信息的受保护成员。</span><span class="sxs-lookup"><span data-stu-id="7f757-134">This class contains the common state machine management functions and two protected members to apply and read the context information to and from messages.</span></span>

```csharp
class DurableInstanceContextChannelBase
{
  //…
  protected void ApplyContext(Message message)
  {
    //…
  }
  protected string ReadContextId(Message message)
  {
    //…
  }
}
```

<span data-ttu-id="7f757-135">这两种方法使用所实现的 `IContextManager` 将上下文 ID 写入消息中或从消息中读取上下文 ID。</span><span class="sxs-lookup"><span data-stu-id="7f757-135">These two methods make use of `IContextManager` implementations to write and read the context ID to or from the message.</span></span> <span data-ttu-id="7f757-136">（ `IContextManager` 是用于为所有上下文管理器定义协定的自定义接口。）通道可以在自定义 SOAP 标头或 HTTP cookie 标头中包含上下文 ID。</span><span class="sxs-lookup"><span data-stu-id="7f757-136">(`IContextManager` is a custom interface used to define the contract for all context managers.) The channel can either include the context ID in a custom SOAP header or in an HTTP cookie header.</span></span> <span data-ttu-id="7f757-137">每个上下文管理器实现都继承自 `ContextManagerBase` 类，该类包含所有上下文管理器的常用功能。</span><span class="sxs-lookup"><span data-stu-id="7f757-137">Each context manager implementation inherits from the `ContextManagerBase` class that contains the common functionality for all context managers.</span></span> <span data-ttu-id="7f757-138">使用该类中的 `GetContextId` 方法，可以客户端中产生上下文 ID。</span><span class="sxs-lookup"><span data-stu-id="7f757-138">The `GetContextId` method in this class is used to originate the context ID from the client.</span></span> <span data-ttu-id="7f757-139">首次产生某个上下文 ID 时，此方法会将该上下文 ID 保存到一个文本文件中，该文件的名称是由远程终结点地址构造的（典型 URI 中的无效文件名字符会替换为 @ 字符）。</span><span class="sxs-lookup"><span data-stu-id="7f757-139">When a context ID is originated for the first time, this method saves it into a text file whose name is constructed by the remote endpoint address (the invalid file name characters in the typical URIs are replaced with @ characters).</span></span>

<span data-ttu-id="7f757-140">以后，当需要针对同一个远程终结点使用该上下文 ID 时，此方法会检查是否存在相应的文件。</span><span class="sxs-lookup"><span data-stu-id="7f757-140">Later when the context ID is required for the same remote endpoint, it checks whether an appropriate file exists.</span></span> <span data-ttu-id="7f757-141">如果存在的话，此方法会读取并返回该上下文 ID。</span><span class="sxs-lookup"><span data-stu-id="7f757-141">If it does, it reads the context ID and returns.</span></span> <span data-ttu-id="7f757-142">否则，此方法会返回一个新生成的上下文 ID 并将其保存到文件中。</span><span class="sxs-lookup"><span data-stu-id="7f757-142">Otherwise it returns a newly generated context ID and saves it to a file.</span></span> <span data-ttu-id="7f757-143">使用默认配置时，这些文件放置在一个名为 ContextStore 的目录中，该目录位于当前用户的 temp 目录中。</span><span class="sxs-lookup"><span data-stu-id="7f757-143">With the default configuration, these files are placed in a directory called ContextStore, which resides in the current user's temp directory.</span></span> <span data-ttu-id="7f757-144">不过，可以使用绑定元素来配置此位置。</span><span class="sxs-lookup"><span data-stu-id="7f757-144">However this location is configurable using the binding element.</span></span>

<span data-ttu-id="7f757-145">用来传输上下文 ID 的机制是可配置的。</span><span class="sxs-lookup"><span data-stu-id="7f757-145">The mechanism used to transport the context ID is configurable.</span></span> <span data-ttu-id="7f757-146">它可以写入 HTTP Cookie 头中，也可以写入自定义 SOAP 头中。</span><span class="sxs-lookup"><span data-stu-id="7f757-146">It could be either written to the HTTP cookie header or to a custom SOAP header.</span></span> <span data-ttu-id="7f757-147">自定义 SOAP 头方法允许将该协议与非 HTTP 协议（例如，TCP 或命名管道）一起使用。</span><span class="sxs-lookup"><span data-stu-id="7f757-147">The custom SOAP header approach makes it possible to use this protocol with non-HTTP protocols (for example, TCP or Named Pipes).</span></span> <span data-ttu-id="7f757-148">这两个选项由两个类（即 `MessageHeaderContextManager` 和 `HttpCookieContextManager`）来实现。</span><span class="sxs-lookup"><span data-stu-id="7f757-148">There are two classes, namely `MessageHeaderContextManager` and `HttpCookieContextManager`, which implement these two options.</span></span>

<span data-ttu-id="7f757-149">这两个类都将上下文 ID 写入相应的消息中。</span><span class="sxs-lookup"><span data-stu-id="7f757-149">Both of them write the context ID to the message appropriately.</span></span> <span data-ttu-id="7f757-150">例如，`MessageHeaderContextManager` 类中的 `WriteContext` 方法将上下文 ID 写入 SOAP 头中。</span><span class="sxs-lookup"><span data-stu-id="7f757-150">For example, the `MessageHeaderContextManager` class writes it to a SOAP header in the `WriteContext` method.</span></span>

```csharp
public override void WriteContext(Message message)
{
  string contextId = this.GetContextId();

  MessageHeader contextHeader =
    MessageHeader.CreateHeader(DurableInstanceContextUtility.HeaderName,
      DurableInstanceContextUtility.HeaderNamespace,
      contextId,
      true);

  message.Headers.Add(contextHeader);
}
```

<span data-ttu-id="7f757-151">`ApplyContext` 类中的 `ReadContextId` 和 `DurableInstanceContextChannelBase` 方法分别都调用 `IContextManager.ReadContext` 和 `IContextManager.WriteContext`。</span><span class="sxs-lookup"><span data-stu-id="7f757-151">Both the `ApplyContext` and `ReadContextId` methods in the `DurableInstanceContextChannelBase` class invoke the `IContextManager.ReadContext` and `IContextManager.WriteContext`, respectively.</span></span> <span data-ttu-id="7f757-152">但是，这些上下文管理器不是由 `DurableInstanceContextChannelBase` 类直接创建的，</span><span class="sxs-lookup"><span data-stu-id="7f757-152">However, these context managers are not directly created by the `DurableInstanceContextChannelBase` class.</span></span> <span data-ttu-id="7f757-153">而是使用 `ContextManagerFactory` 类创建的。</span><span class="sxs-lookup"><span data-stu-id="7f757-153">Instead it uses the `ContextManagerFactory` class to do that job.</span></span>

```csharp
IContextManager contextManager =
                ContextManagerFactory.CreateContextManager(contextType,
                this.contextStoreLocation,
                this.endpointAddress);
```

<span data-ttu-id="7f757-154">`ApplyContext` 方法由发送通道调用。</span><span class="sxs-lookup"><span data-stu-id="7f757-154">The `ApplyContext` method is invoked by the sending channels.</span></span> <span data-ttu-id="7f757-155">它将上下文 ID 插入传出消息中。</span><span class="sxs-lookup"><span data-stu-id="7f757-155">It injects the context ID to the outgoing messages.</span></span> <span data-ttu-id="7f757-156">`ReadContextId` 方法由接收通道调用。</span><span class="sxs-lookup"><span data-stu-id="7f757-156">The `ReadContextId` method is invoked by the receiving channels.</span></span> <span data-ttu-id="7f757-157">此方法可确保上下文 ID 在传入消息中可用，并将上下文 ID 添加到 `Properties` 类的 `Message` 集合中。</span><span class="sxs-lookup"><span data-stu-id="7f757-157">This method ensures that the context ID is available in the incoming messages and adds it to the `Properties` collection of the `Message` class.</span></span> <span data-ttu-id="7f757-158">此方法还在无法读取上下文 ID 时引发 `CommunicationException`，从而导致通道中止。</span><span class="sxs-lookup"><span data-stu-id="7f757-158">It also throws a `CommunicationException` in case of a failure to read the context ID and thus causes the channel to be aborted.</span></span>

```csharp
message.Properties.Add(DurableInstanceContextUtility.ContextIdProperty, contextId);
```

<span data-ttu-id="7f757-159">在继续操作之前，一定要先了解 `Properties` 类的 `Message` 集合的用法。</span><span class="sxs-lookup"><span data-stu-id="7f757-159">Before proceeding, it is important to understand the usage of the `Properties` collection in the `Message` class.</span></span> <span data-ttu-id="7f757-160">通常，在将数据从较低的通道层传递到较高层时，将使用这个 `Properties` 集合。</span><span class="sxs-lookup"><span data-stu-id="7f757-160">Typically, this `Properties` collection is used when passing data from lower to the upper levels from the channel layer.</span></span> <span data-ttu-id="7f757-161">这样，无论协议细节如何，都可以按照一致的方式向较高层提供所需的数据。</span><span class="sxs-lookup"><span data-stu-id="7f757-161">This way the desired data can be provided to the upper levels in a consistent manner regardless of the protocol details.</span></span> <span data-ttu-id="7f757-162">换句话说，通道层可以作为 SOAP 标头或 HTTP cookie 标头来发送和接收上下文 ID。</span><span class="sxs-lookup"><span data-stu-id="7f757-162">In other words, the channel layer can send and receive the context ID either as a SOAP header or an HTTP cookie header.</span></span> <span data-ttu-id="7f757-163">但是，较高层没有必要知道这些细节，因为通道层会使 `Properties` 集合中提供这些信息。</span><span class="sxs-lookup"><span data-stu-id="7f757-163">But it is not necessary for the upper levels to know about these details because the channel layer makes this information available in the `Properties` collection.</span></span>

<span data-ttu-id="7f757-164">现在，`DurableInstanceContextChannelBase` 类已经就绪，必须实现全部十个必要的接口（IOutputChannel、IInputChannel、IOutputSessionChannel、IInputSessionChannel、IRequestChannel、IReplyChannel、IRequestSessionChannel、IReplySessionChannel、IDuplexChannel 和 IDuplexSessionChannel）。</span><span class="sxs-lookup"><span data-stu-id="7f757-164">Now with the `DurableInstanceContextChannelBase` class in place all ten of the necessary interfaces (IOutputChannel, IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, IDuplexChannel, IDuplexSessionChannel) must be implemented.</span></span> <span data-ttu-id="7f757-165">它们类似于每个可用的消息交换模式（数据报、单工、双工和它们的会话变体）。</span><span class="sxs-lookup"><span data-stu-id="7f757-165">They resemble every available message exchange pattern (datagram, simplex, duplex, and their sessionful variants).</span></span> <span data-ttu-id="7f757-166">其中每个实现都继承前面描述的基类，并 `ApplyContext` `ReadContextId` 相应地调用和。</span><span class="sxs-lookup"><span data-stu-id="7f757-166">Each of these implementations inherits the base class previously described and calls `ApplyContext` and `ReadContextId` appropriately.</span></span> <span data-ttu-id="7f757-167">例如，用来实现 IOutputChannel 接口的 `DurableInstanceContextOutputChannel` 从发送消息的每种方法中调用 `ApplyContext` 方法。</span><span class="sxs-lookup"><span data-stu-id="7f757-167">For example, `DurableInstanceContextOutputChannel` - which implements the IOutputChannel interface - calls the `ApplyContext` method from each method that sends the messages.</span></span>

```csharp
public void Send(Message message, TimeSpan timeout)
{
    // Apply the context information before sending the message.
    this.ApplyContext(message);
    //…
}
```

<span data-ttu-id="7f757-168">另一方面， `DurableInstanceContextInputChannel` 实现 `IInputChannel` 接口的是 `ReadContextId` 在每个方法中调用方法，后者接收消息。</span><span class="sxs-lookup"><span data-stu-id="7f757-168">On the other hand, `DurableInstanceContextInputChannel` - which implements the `IInputChannel` interface - calls the `ReadContextId` method in each method, which receives the messages.</span></span>

```csharp
public Message Receive(TimeSpan timeout)
{
    //…
      ReadContextId(message);
      return message;
}
```

<span data-ttu-id="7f757-169">除此之外，这些通道实现还将方法调用委托给通道堆栈中位于其下方的通道。</span><span class="sxs-lookup"><span data-stu-id="7f757-169">Apart from this, these channel implementations delegate the method invocations to the channel below them in the channel stack.</span></span> <span data-ttu-id="7f757-170">但是，会话变量有一个基本逻辑来确保上下文 ID 仅随导致创建会话的第一条消息发送和读取。</span><span class="sxs-lookup"><span data-stu-id="7f757-170">However, sessionful variants have a basic logic to make sure that the context ID is sent and is read only for the first message that causes the session to be created.</span></span>

```csharp
if (isFirstMessage)
{
//…
    this.ApplyContext(message);
    isFirstMessage = false;
}
```

<span data-ttu-id="7f757-171">然后， `DurableInstanceContextBindingElement` 类和类会相应地将这些通道实现添加到 WCF 信道运行时 `DurableInstanceContextBindingElementSection` 。</span><span class="sxs-lookup"><span data-stu-id="7f757-171">These channel implementations are then added to the WCF channel runtime by the `DurableInstanceContextBindingElement` class and `DurableInstanceContextBindingElementSection` class appropriately.</span></span> <span data-ttu-id="7f757-172">有关绑定元素和绑定元素部分的详细信息，请参阅[HttpCookieSession](httpcookiesession.md)信道示例文档。</span><span class="sxs-lookup"><span data-stu-id="7f757-172">See the [HttpCookieSession](httpcookiesession.md) channel sample documentation for more details about binding elements and binding element sections.</span></span>

## <a name="service-model-layer-extensions"></a><span data-ttu-id="7f757-173">服务模型层扩展</span><span class="sxs-lookup"><span data-stu-id="7f757-173">Service Model Layer Extensions</span></span>

<span data-ttu-id="7f757-174">既然上下文 ID 已经穿过了通道层，可以实现服务行为来自定义实例化了。</span><span class="sxs-lookup"><span data-stu-id="7f757-174">Now that the context ID has traveled through the channel layer, the service behavior can be implemented to customize the instantiation.</span></span> <span data-ttu-id="7f757-175">在该实例中，存储管理器用来从持久性存储中加载状态或将状态保存到持久性存储中。</span><span class="sxs-lookup"><span data-stu-id="7f757-175">In this sample, a storage manager is used to load and save state from or to the persistent store.</span></span> <span data-ttu-id="7f757-176">如上所述，该实例提供一个将 SQL Server 2005 用作其后备存储的存储管理器。</span><span class="sxs-lookup"><span data-stu-id="7f757-176">As explained previously, this sample provides a storage manager that uses SQL Server 2005 as its backing store.</span></span> <span data-ttu-id="7f757-177">但是，还可以向该扩展中添加自定义存储机制。</span><span class="sxs-lookup"><span data-stu-id="7f757-177">However, it is also possible to add custom storage mechanisms to this extension.</span></span> <span data-ttu-id="7f757-178">为此，需要声明一个必须由所有的存储管理器实现的公共接口。</span><span class="sxs-lookup"><span data-stu-id="7f757-178">To do that a public interface is declared, which must be implemented by all storage managers.</span></span>

```csharp
public interface IStorageManager
{
    object GetInstance(string contextId, Type type);
    void SaveInstance(string contextId, object state);
}
```

<span data-ttu-id="7f757-179">`SqlServerStorageManager` 类包含默认的 `IStorageManager` 实现。</span><span class="sxs-lookup"><span data-stu-id="7f757-179">The `SqlServerStorageManager` class contains the default `IStorageManager` implementation.</span></span> <span data-ttu-id="7f757-180">在其 `SaveInstance` 方法中，将使用 XmlSerializer 序列化给定对象并将其保存到 SQL Server 数据库中。</span><span class="sxs-lookup"><span data-stu-id="7f757-180">In its `SaveInstance` method, the given object is serialized using the XmlSerializer and is saved to the SQL Server database.</span></span>

```csharp
XmlSerializer serializer = new XmlSerializer(state.GetType());
string data;

using (StringWriter writer = new StringWriter(CultureInfo.InvariantCulture))
{
    serializer.Serialize(writer, state);
    data = writer.ToString();
}

using (SqlConnection connection = new SqlConnection(GetConnectionString()))
{
    connection.Open();

    string update = @"UPDATE Instances SET Instance = @instance WHERE ContextId = @contextId";

    using (SqlCommand command = new SqlCommand(update, connection))
    {
        command.Parameters.Add("@instance", SqlDbType.VarChar, 2147483647).Value = data;
        command.Parameters.Add("@contextId", SqlDbType.VarChar, 256).Value = contextId;

        int rows = command.ExecuteNonQuery();

        if (rows == 0)
        {
            string insert = @"INSERT INTO Instances(ContextId, Instance) VALUES(@contextId, @instance)";
            command.CommandText = insert;
            command.ExecuteNonQuery();
        }
    }
}
```

<span data-ttu-id="7f757-181">在 `GetInstance` 方法中，读取给定上下文 ID 的序列化数据，并将其构造的对象返回给调用方。</span><span class="sxs-lookup"><span data-stu-id="7f757-181">In the `GetInstance` method, the serialized data is read for a given context ID and the object constructed from it is returned to the caller.</span></span>

```csharp
object data;
using (SqlConnection connection = new SqlConnection(GetConnectionString()))
{
    connection.Open();

    string select = "SELECT Instance FROM Instances WHERE ContextId = @contextId";
    using (SqlCommand command = new SqlCommand(select, connection))
    {
        command.Parameters.Add("@contextId", SqlDbType.VarChar, 256).Value = contextId;
        data = command.ExecuteScalar();
    }
}

if (data != null)
{
    XmlSerializer serializer = new XmlSerializer(type);
    using (StringReader reader = new StringReader((string)data))
    {
        object instance = serializer.Deserialize(reader);
        return instance;
    }
}
```

<span data-ttu-id="7f757-182">这些存储管理器的用户不应当直接实例化它们，</span><span class="sxs-lookup"><span data-stu-id="7f757-182">Users of these storage managers are not supposed to instantiate them directly.</span></span> <span data-ttu-id="7f757-183">而是应当使用 `StorageManagerFactory` 类，该类从存储管理器的创建细节提取数据。</span><span class="sxs-lookup"><span data-stu-id="7f757-183">They use the `StorageManagerFactory` class, which abstracts from the storage manager creation details.</span></span> <span data-ttu-id="7f757-184">该类有一个静态成员（即 `GetStorageManager`），该成员创建一个具有给定存储管理器类型的实例。</span><span class="sxs-lookup"><span data-stu-id="7f757-184">This class has one static member, `GetStorageManager`, which creates an instance of a given storage manager type.</span></span> <span data-ttu-id="7f757-185">如果类型参数是 `null`，此方法会创建默认 `SqlServerStorageManager` 类的一个实例并返回它。</span><span class="sxs-lookup"><span data-stu-id="7f757-185">If the type parameter is `null`, this method creates an instance of the default `SqlServerStorageManager` class and returns it.</span></span> <span data-ttu-id="7f757-186">此方法还对给定类型进行验证，确保该类型能够实现 `IStorageManager` 接口。</span><span class="sxs-lookup"><span data-stu-id="7f757-186">It also validates the given type to make sure that it implements the `IStorageManager` interface.</span></span>

```csharp
public static IStorageManager GetStorageManager(Type storageManagerType)
{
IStorageManager storageManager = null;

if (storageManagerType == null)
{
    return new SqlServerStorageManager();
}
else
{
    object obj = Activator.CreateInstance(storageManagerType);

    // Throw if the specified storage manager type does not
    // implement IStorageManager.
    if (obj is IStorageManager)
    {
        storageManager = (IStorageManager)obj;
    }
    else
    {
        throw new InvalidOperationException(
                  ResourceHelper.GetString("ExInvalidStorageManager"));
    }

    return storageManager;
}
}
```

<span data-ttu-id="7f757-187">我们已经实现了要在持久性存储中读写实例的必要基础结构，</span><span class="sxs-lookup"><span data-stu-id="7f757-187">The necessary infrastructure to read and write instances from the persistent storage is implemented.</span></span> <span data-ttu-id="7f757-188">现在必须采取必要的步骤来更改服务行为。</span><span class="sxs-lookup"><span data-stu-id="7f757-188">Now the necessary steps to change the service behavior have to be taken.</span></span>

<span data-ttu-id="7f757-189">作为此过程的第一步，我们必须保存已通过通道层到达当前 InstanceContext 的上下文 ID。</span><span class="sxs-lookup"><span data-stu-id="7f757-189">As the first step of this process we have to save the context ID, which came through the channel layer to the current InstanceContext.</span></span> <span data-ttu-id="7f757-190">InstanceContext 是一个运行时组件，它充当 WCF 调度程序和服务实例之间的链接。</span><span class="sxs-lookup"><span data-stu-id="7f757-190">InstanceContext is a runtime component that acts as the link between the WCF dispatcher and the service instance.</span></span> <span data-ttu-id="7f757-191">可用来向服务实例提供其他状态和行为。</span><span class="sxs-lookup"><span data-stu-id="7f757-191">It can be used to provide additional state and behavior to the service instance.</span></span> <span data-ttu-id="7f757-192">这是必不可少的，因为在会话通信中，上下文 ID 仅随第一条消息发送。</span><span class="sxs-lookup"><span data-stu-id="7f757-192">This is essential because in sessionful communication the context ID is sent only with the first message.</span></span>

<span data-ttu-id="7f757-193">WCF 允许通过使用其可扩展对象模式添加新的状态和行为来扩展其 InstanceContext 运行时组件。</span><span class="sxs-lookup"><span data-stu-id="7f757-193">WCF allows extending its InstanceContext runtime component by adding a new state and behavior using its extensible object pattern.</span></span> <span data-ttu-id="7f757-194">在 WCF 中使用可扩展对象模式，以使用新功能扩展现有的运行时类，或者向对象中添加新的状态功能。</span><span class="sxs-lookup"><span data-stu-id="7f757-194">The extensible object pattern is used in WCF to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="7f757-195">可扩展对象模式中有三个接口-IExtensibleObject \<T> 、IExtension \<T> 和 IExtensionCollection \<T> ：</span><span class="sxs-lookup"><span data-stu-id="7f757-195">There are three interfaces in the extensible object pattern - IExtensibleObject\<T>, IExtension\<T>, and IExtensionCollection\<T>:</span></span>

- <span data-ttu-id="7f757-196">IExtensibleObject \<T> 接口由允许自定义其功能的扩展的对象实现。</span><span class="sxs-lookup"><span data-stu-id="7f757-196">The IExtensibleObject\<T> interface is implemented by objects that allow extensions that customize their functionality.</span></span>

- <span data-ttu-id="7f757-197">IExtension \<T> 接口是由类型为 T 的类的扩展的对象实现的。</span><span class="sxs-lookup"><span data-stu-id="7f757-197">The IExtension\<T> interface is implemented by objects that are extensions of classes of type T.</span></span>

- <span data-ttu-id="7f757-198">IExtensionCollection \<T> 接口是 iextension 的集合，可用于按其类型检索 iextension。</span><span class="sxs-lookup"><span data-stu-id="7f757-198">The IExtensionCollection\<T> interface is a collection of IExtensions that allows for retrieving IExtensions by their type.</span></span>

<span data-ttu-id="7f757-199">因此，应当创建一个 InstanceContextExtension 类，该类实现 IExtension 接口并定义保存上下文 ID 所必需的状态。</span><span class="sxs-lookup"><span data-stu-id="7f757-199">Therefore an InstanceContextExtension class should be created that implements the IExtension interface and defines the required state to save the context ID.</span></span> <span data-ttu-id="7f757-200">此类还提供用来存放正使用的存储管理器的状态。</span><span class="sxs-lookup"><span data-stu-id="7f757-200">This class also provides the state to hold the storage manager being used.</span></span> <span data-ttu-id="7f757-201">在保存了新状态之后，就无法对其进行修改。</span><span class="sxs-lookup"><span data-stu-id="7f757-201">Once the new state is saved, it should not be possible to modify it.</span></span> <span data-ttu-id="7f757-202">因此，状态是在构造实例时提供并保存到实例中的，之后，只能使用只读属性来进行访问。</span><span class="sxs-lookup"><span data-stu-id="7f757-202">Therefore the state is provided and saved to the instance at the time it is being constructed and then only accessible using read-only properties.</span></span>

```csharp
// Constructor
public DurableInstanceContextExtension(string contextId,
            IStorageManager storageManager)
{
    this.contextId = contextId;
    this.storageManager = storageManager;
}

// Read only properties
public string ContextId
{
    get { return this.contextId; }
}

public IStorageManager StorageManager
{
    get { return this.storageManager; }
}
```

<span data-ttu-id="7f757-203">InstanceContextInitializer 类实现 IInstanceContextInitializer 接口，并将实例上下文扩展添加到所构造的 InstanceContext 的 Extensions 集合中。</span><span class="sxs-lookup"><span data-stu-id="7f757-203">The InstanceContextInitializer class implements the IInstanceContextInitializer interface and adds the instance context extension to the Extensions collection of the InstanceContext being constructed.</span></span>

```csharp
public void Initialize(InstanceContext instanceContext, Message message)
{
    string contextId =
  (string)message.Properties[DurableInstanceContextUtility.ContextIdProperty];

    DurableInstanceContextExtension extension =
                new DurableInstanceContextExtension(contextId,
                     storageManager);
    instanceContext.Extensions.Add(extension);
}
```

<span data-ttu-id="7f757-204">如上所述，上下文 ID 读取自 `Properties` 类的 `Message` 集合并传递到扩展类的构造函数。</span><span class="sxs-lookup"><span data-stu-id="7f757-204">As described earlier the context ID is read from the `Properties` collection of the `Message` class and passed to the constructor of the extension class.</span></span> <span data-ttu-id="7f757-205">这演示了如何以一致的方式在层之间交换信息。</span><span class="sxs-lookup"><span data-stu-id="7f757-205">This demonstrates how information can be exchanged between the layers in a consistent manner.</span></span>

<span data-ttu-id="7f757-206">下一个重要步骤是重写服务实例的创建过程。</span><span class="sxs-lookup"><span data-stu-id="7f757-206">The next important step is overriding the service instance creation process.</span></span> <span data-ttu-id="7f757-207">WCF 允许实现自定义实例化行为，并使用 IInstanceProvider 接口将它们挂钩到运行时。</span><span class="sxs-lookup"><span data-stu-id="7f757-207">WCF allows implementing custom instantiation behaviors and hooking them up to the runtime using the IInstanceProvider interface.</span></span> <span data-ttu-id="7f757-208">这可以通过实现新的 `InstanceProvider` 类来完成。</span><span class="sxs-lookup"><span data-stu-id="7f757-208">The new `InstanceProvider` class is implemented to do that job.</span></span> <span data-ttu-id="7f757-209">构造函数中接受实例提供程序所需的服务类型。</span><span class="sxs-lookup"><span data-stu-id="7f757-209">The service type expected from the instance provider is accepted in the constructor.</span></span> <span data-ttu-id="7f757-210">以后，可以使用此服务类型来创建新实例。</span><span class="sxs-lookup"><span data-stu-id="7f757-210">Later this is used to create new instances.</span></span> <span data-ttu-id="7f757-211">在 `GetInstance` 实现中，创建一个存储管理器实例以查找持久化实例。</span><span class="sxs-lookup"><span data-stu-id="7f757-211">In the `GetInstance` implementation, an instance of a storage manager is created looking for a persisted instance.</span></span> <span data-ttu-id="7f757-212">如果它返回 `null` ，则会实例化服务类型的新实例并将其返回给调用方。</span><span class="sxs-lookup"><span data-stu-id="7f757-212">If it returns `null`, then a new instance of the service type is instantiated and returned to the caller.</span></span>

```csharp
public object GetInstance(InstanceContext instanceContext, Message message)
{
    object instance = null;

    DurableInstanceContextExtension extension =
    instanceContext.Extensions.Find<DurableInstanceContextExtension>();

    string contextId = extension.ContextId;
    IStorageManager storageManager = extension.StorageManager;

    instance = storageManager.GetInstance(contextId, serviceType);

    instance ??= Activator.CreateInstance(serviceType);
    return instance;
}
```

<span data-ttu-id="7f757-213">下一个重要步骤是将 `InstanceContextExtension` 、 `InstanceContextInitializer` 和 `InstanceProvider` 类安装到服务模型运行时中。</span><span class="sxs-lookup"><span data-stu-id="7f757-213">The next important step is to install the `InstanceContextExtension`, `InstanceContextInitializer`, and `InstanceProvider` classes into the service model runtime.</span></span> <span data-ttu-id="7f757-214">自定义属性可用来标记服务实现类以安装该行为。</span><span class="sxs-lookup"><span data-stu-id="7f757-214">A custom attribute could be used to mark the service implementation classes to install the behavior.</span></span> <span data-ttu-id="7f757-215">`DurableInstanceContextAttribute` 包含对该属性的实现，它实现了用来扩展整个服务运行库的 `IServiceBehavior` 接口。</span><span class="sxs-lookup"><span data-stu-id="7f757-215">The `DurableInstanceContextAttribute` contains the implementation for this attribute and it implements the `IServiceBehavior` interface to extend the entire service runtime.</span></span>

<span data-ttu-id="7f757-216">此类有一个接受要使用的存储管理器类型的属性。</span><span class="sxs-lookup"><span data-stu-id="7f757-216">This class has a property that accepts the type of the storage manager to be used.</span></span> <span data-ttu-id="7f757-217">通过这种方式，实现使用户能够将自己的 `IStorageManager` 实现指定为此特性的参数。</span><span class="sxs-lookup"><span data-stu-id="7f757-217">In this way, the implementation enables the users to specify their own `IStorageManager` implementation as parameter of this attribute.</span></span>

<span data-ttu-id="7f757-218">在 `ApplyDispatchBehavior` 实现中， `InstanceContextMode` `ServiceBehavior` 正在验证当前属性的。</span><span class="sxs-lookup"><span data-stu-id="7f757-218">In the `ApplyDispatchBehavior` implementation, the `InstanceContextMode` of the current `ServiceBehavior` attribute is being verified.</span></span> <span data-ttu-id="7f757-219">如果此属性设置为 Singleton，则将无法启用持久性实例化，而且将引发 `InvalidOperationException` 以通知主机。</span><span class="sxs-lookup"><span data-stu-id="7f757-219">If this property is set to Singleton, enabling durable instancing is not possible and an `InvalidOperationException` is thrown to notify the host.</span></span>

```csharp
ServiceBehaviorAttribute serviceBehavior =
    serviceDescription.Behaviors.Find<ServiceBehaviorAttribute>();

if (serviceBehavior != null &&
     serviceBehavior.InstanceContextMode == InstanceContextMode.Single)
{
    throw new InvalidOperationException(
       ResourceHelper.GetString("ExSingletonInstancingNotSupported"));
}
```

<span data-ttu-id="7f757-220">在此之后，会创建存储管理器的实例、实例上下文初始值设定项和实例提供程序，并将它们安装在为每个终结点创建的 `DispatchRuntime` 中。</span><span class="sxs-lookup"><span data-stu-id="7f757-220">After this the instances of the storage manager, instance context initializer, and the instance provider are created and installed in the `DispatchRuntime` created for every endpoint.</span></span>

```csharp
IStorageManager storageManager =
    StorageManagerFactory.GetStorageManager(storageManagerType);

InstanceContextInitializer contextInitializer =
    new InstanceContextInitializer(storageManager);

InstanceProvider instanceProvider =
    new InstanceProvider(description.ServiceType);

foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)
{
    ChannelDispatcher cd = cdb as ChannelDispatcher;

    if (cd != null)
    {
        foreach (EndpointDispatcher ed in cd.Endpoints)
        {
            ed.DispatchRuntime.InstanceContextInitializers.Add(contextInitializer);
            ed.DispatchRuntime.InstanceProvider = instanceProvider;
        }
    }
}
```

<span data-ttu-id="7f757-221">总之，到目前为止，此示例已经生成了一个针对自定义上下文 ID 交换启用了自定义网络协议的通道，而且还覆盖了默认实例化行为，以便从持久性存储中加载实例。</span><span class="sxs-lookup"><span data-stu-id="7f757-221">In summary so far, this sample has produced a channel that enabled the custom wire protocol for custom context ID exchange and it also overwrites the default instancing behavior to load the instances from the persistent storage.</span></span>

<span data-ttu-id="7f757-222">剩下的就是通过某种方法来将服务实例保存到持久性存储中。</span><span class="sxs-lookup"><span data-stu-id="7f757-222">What is left is a way to save the service instance to the persistent storage.</span></span> <span data-ttu-id="7f757-223">如上所述，已经有一个必需的功能来将状态保存在 `IStorageManager` 实现中。</span><span class="sxs-lookup"><span data-stu-id="7f757-223">As discussed previously, there is already the required functionality to save the state in an `IStorageManager` implementation.</span></span> <span data-ttu-id="7f757-224">现在，我们必须将此集成到 WCF 运行时。</span><span class="sxs-lookup"><span data-stu-id="7f757-224">We now must integrate this with the WCF runtime.</span></span> <span data-ttu-id="7f757-225">需要另一个适用于服务实现类中的方法的属性。</span><span class="sxs-lookup"><span data-stu-id="7f757-225">Another attribute is required that is applicable to the methods in the service implementation class.</span></span> <span data-ttu-id="7f757-226">此属性假设应用于对服务实例的状态进行更改的方法。</span><span class="sxs-lookup"><span data-stu-id="7f757-226">This attribute is supposed to be applied to the methods that change the state of the service instance.</span></span>

<span data-ttu-id="7f757-227">`SaveStateAttribute` 类实现了此功能。</span><span class="sxs-lookup"><span data-stu-id="7f757-227">The `SaveStateAttribute` class implements this functionality.</span></span> <span data-ttu-id="7f757-228">它还实现 `IOperationBehavior` 类以修改每个操作的 WCF 运行时。</span><span class="sxs-lookup"><span data-stu-id="7f757-228">It also implements `IOperationBehavior` class to modify the WCF runtime for each operation.</span></span> <span data-ttu-id="7f757-229">使用此特性标记方法时，WCF 运行时将调用方法， `ApplyBehavior` 同时构造适当的 `DispatchOperation` 。</span><span class="sxs-lookup"><span data-stu-id="7f757-229">When a method is marked with this attribute, the WCF runtime invokes the `ApplyBehavior` method while the appropriate `DispatchOperation` is being constructed.</span></span> <span data-ttu-id="7f757-230">此方法实现中有一个代码行：</span><span class="sxs-lookup"><span data-stu-id="7f757-230">There is a single line of code in this method implementation:</span></span>

```csharp
dispatch.Invoker = new OperationInvoker(dispatch.Invoker);
```

<span data-ttu-id="7f757-231">此指令会创建 `OperationInvoker` 类型的一个实例并将它分配给正构造的 `Invoker` 的 `DispatchOperation` 属性。</span><span class="sxs-lookup"><span data-stu-id="7f757-231">This instruction creates an instance of `OperationInvoker` type and assigns it to the `Invoker` property of the `DispatchOperation` being constructed.</span></span> <span data-ttu-id="7f757-232">`OperationInvoker` 类是一个包装，它面向为 `DispatchOperation` 创建的默认操作调用程序。</span><span class="sxs-lookup"><span data-stu-id="7f757-232">The `OperationInvoker` class is a wrapper for the default operation invoker created for the `DispatchOperation`.</span></span> <span data-ttu-id="7f757-233">此类实现 `IOperationInvoker` 接口。</span><span class="sxs-lookup"><span data-stu-id="7f757-233">This class implements the `IOperationInvoker` interface.</span></span> <span data-ttu-id="7f757-234">在 `Invoke` 方法实现中，实际方法调用被委托给内部操作调用程序。</span><span class="sxs-lookup"><span data-stu-id="7f757-234">In the `Invoke` method implementation, the actual method invocation is delegated to the inner operation invoker.</span></span> <span data-ttu-id="7f757-235">但是，在返回结果之前，会使用 `InstanceContext` 中的存储管理器来保存服务实例。</span><span class="sxs-lookup"><span data-stu-id="7f757-235">However, before returning the results the storage manager in the `InstanceContext` is used to save the service instance.</span></span>

```csharp
object result = innerOperationInvoker.Invoke(instance,
    inputs, out outputs);

// Save the instance using the storage manager saved in the
// current InstanceContext.
InstanceContextExtension extension =
    OperationContext.Current.InstanceContext.Extensions.Find<InstanceContextExtension>();

extension.StorageManager.SaveInstance(extension.ContextId, instance);
return result;
```

## <a name="using-the-extension"></a><span data-ttu-id="7f757-236">使用扩展</span><span class="sxs-lookup"><span data-stu-id="7f757-236">Using the Extension</span></span>

<span data-ttu-id="7f757-237">通道层和服务模型层扩展都已完成，它们现在可以在 WCF 应用程序中使用。</span><span class="sxs-lookup"><span data-stu-id="7f757-237">Both the channel layer and service model layer extensions are done and they can now be used in WCF applications.</span></span> <span data-ttu-id="7f757-238">服务必须使用自定义绑定将通道添加到通道堆栈中，然后使用相应的特性标记服务实现类。</span><span class="sxs-lookup"><span data-stu-id="7f757-238">Services must add the channel into the channel stack using a custom binding and then mark the service implementation classes with the appropriate attributes.</span></span>

```csharp
[DurableInstanceContext]
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]
public class ShoppingCart : IShoppingCart
{
//…
     [SaveState]
     public int AddItem(string item)
     {
         //…
     }
//…
 }
```

<span data-ttu-id="7f757-239">客户端应用程序必须使用自定义绑定将 DurableInstanceContextChannel 添加到通道堆栈中。</span><span class="sxs-lookup"><span data-stu-id="7f757-239">Client applications must add the DurableInstanceContextChannel into the channel stack using a custom binding.</span></span> <span data-ttu-id="7f757-240">若要以声明方式在配置文件中配置通道，必须将绑定元素节添加到绑定元素扩展集合中。</span><span class="sxs-lookup"><span data-stu-id="7f757-240">To configure the channel declaratively in the configuration file, the binding element section has to be added to the binding element extensions collection.</span></span>

```xml
<system.serviceModel>
 <extensions>
   <bindingElementExtensions>
     <add name="durableInstanceContext"
type="Microsoft.ServiceModel.Samples.DurableInstanceContextBindingElementSection, DurableInstanceContextExtension, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>
   </bindingElementExtensions>
 </extensions>
</system.serviceModel>
```

<span data-ttu-id="7f757-241">现在，可以像其他标准绑定元素那样，将该绑定元素用于自定义绑定：</span><span class="sxs-lookup"><span data-stu-id="7f757-241">Now the binding element can be used with a custom binding just like other standard binding elements:</span></span>

```xml
<bindings>
 <customBinding>
   <binding name="TextOverHttp">
     <durableInstanceContext contextType="HttpCookie"/>
     <reliableSession />
     <textMessageEncoding />
     <httpTransport />
   </binding>
 </customBinding>
</bindings>
```

## <a name="conclusion"></a><span data-ttu-id="7f757-242">结论</span><span class="sxs-lookup"><span data-stu-id="7f757-242">Conclusion</span></span>

<span data-ttu-id="7f757-243">此示例演示了如何创建自定义协议通道以及如何通过自定义服务行为来启用该通道。</span><span class="sxs-lookup"><span data-stu-id="7f757-243">This sample showed how to create a custom protocol channel and how to customize the service behavior to enable it.</span></span>

<span data-ttu-id="7f757-244">用户可以使用配置节来指定 `IStorageManager` 实现，从而进一步改进扩展。</span><span class="sxs-lookup"><span data-stu-id="7f757-244">The extension can be further improved by letting users specify the `IStorageManager` implementation using a configuration section.</span></span> <span data-ttu-id="7f757-245">这会允许在不重新编译服务代码的情况下修改后备存储。</span><span class="sxs-lookup"><span data-stu-id="7f757-245">This makes it possible to modify the backing store without recompiling the service code.</span></span>

<span data-ttu-id="7f757-246">而且，您可以尝试实现一个用来封装实例状态的类（例如，`StateBag`）。</span><span class="sxs-lookup"><span data-stu-id="7f757-246">Furthermore you could try to implement a class (for example, `StateBag`), which encapsulates the state of the instance.</span></span> <span data-ttu-id="7f757-247">无论何时状态发生变化，该类都负责保持状态。</span><span class="sxs-lookup"><span data-stu-id="7f757-247">That class is responsible for persisting the state whenever it changes.</span></span> <span data-ttu-id="7f757-248">这样，就可以避免使用 `SaveState` 属性，并能够更准确地执行保持工作（例如，可以在状态实际发生变化时保持状态，而不是在每次调用具有 `SaveState` 属性的方法时保存状态）。</span><span class="sxs-lookup"><span data-stu-id="7f757-248">This way you can avoid using the `SaveState` attribute and perform the persisting work more accurately (for example, you could persist the state when the state is actually changed rather than saving it each time when a method with the `SaveState` attribute is called).</span></span>

<span data-ttu-id="7f757-249">运行示例时，会显示下面的输出。</span><span class="sxs-lookup"><span data-stu-id="7f757-249">When you run the sample, the following output is displayed.</span></span> <span data-ttu-id="7f757-250">客户端会向其购物车中添加两项，之后将从服务中获取其购物车中各项的列表。</span><span class="sxs-lookup"><span data-stu-id="7f757-250">The client adds two items to its shopping cart and then gets the list of items in its shopping cart from the service.</span></span> <span data-ttu-id="7f757-251">在每个控制台窗口中按 Enter 可以关闭服务和客户端。</span><span class="sxs-lookup"><span data-stu-id="7f757-251">Press ENTER in each console window to shut down the service and client.</span></span>

```console
Enter the name of the product: apples
Enter the name of the product: bananas

Shopping cart currently contains the following items.
apples
bananas
Press ENTER to shut down client
```

> [!NOTE]
> <span data-ttu-id="7f757-252">重新生成服务会覆盖数据库文件。</span><span class="sxs-lookup"><span data-stu-id="7f757-252">Rebuilding the service overwrites the database file.</span></span> <span data-ttu-id="7f757-253">如果要使状态在多个示例运行之间得以保持，请确保在不同的运行之间不重新生成示例。</span><span class="sxs-lookup"><span data-stu-id="7f757-253">To observe state preserved across multiple runs of the sample, be sure not to rebuild the sample between runs.</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7f757-254">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="7f757-254">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="7f757-255">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="7f757-255">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="7f757-256">若要生成解决方案，请按照[生成 Windows Communication Foundation 示例](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="7f757-256">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="7f757-257">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="7f757-257">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!NOTE]
> <span data-ttu-id="7f757-258">必须运行 SQL Server 2005 或 SQL Express 2005 才能运行此示例。</span><span class="sxs-lookup"><span data-stu-id="7f757-258">You must be running SQL Server 2005 or SQL Express 2005 to run this sample.</span></span> <span data-ttu-id="7f757-259">如果您运行的是 SQL Server 2005，则必须修改服务连接字符串的配置。</span><span class="sxs-lookup"><span data-stu-id="7f757-259">If you are running SQL Server 2005, you must modify the configuration of the service's connection string.</span></span> <span data-ttu-id="7f757-260">在跨计算机运行时，只需要在服务器计算机上安装 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="7f757-260">When running cross-machine, SQL Server is only required on the server machine.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7f757-261">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="7f757-261">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7f757-262">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="7f757-262">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="7f757-263">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="7f757-263">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7f757-264">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="7f757-264">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Durable`

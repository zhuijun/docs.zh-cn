---
title: 传输：UDP
ms.date: 03/30/2017
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
ms.openlocfilehash: dcf2d9896ab7c95101e224521174b54c88ca3fc2
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558991"
---
# <a name="transport-udp"></a><span data-ttu-id="2be61-102">传输：UDP</span><span class="sxs-lookup"><span data-stu-id="2be61-102">Transport: UDP</span></span>
<span data-ttu-id="2be61-103">UDP 传输示例演示如何将 UDP 单播和多播作为自定义 Windows Communication Foundation (WCF) 传输实现。</span><span class="sxs-lookup"><span data-stu-id="2be61-103">The UDP Transport sample demonstrates how to implement UDP unicast and multicast as a custom Windows Communication Foundation (WCF) transport.</span></span> <span data-ttu-id="2be61-104">该示例介绍了使用通道框架和以下 WCF 最佳做法在 WCF 中创建自定义传输的建议过程。</span><span class="sxs-lookup"><span data-stu-id="2be61-104">The sample describes the recommended procedure for creating a custom transport in WCF, by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="2be61-105">创建自定义传输的步骤如下：</span><span class="sxs-lookup"><span data-stu-id="2be61-105">The steps to create a custom transport are as follows:</span></span>  
  
1. <span data-ttu-id="2be61-106">确定你的 ChannelFactory 和 IReplyChannel) 哪些通道 [消息交换模式](#MessageExchangePatterns) (IOutputChannel、IInputChannel、IDuplexChannel、IRequestChannel 或 ChannelListener。</span><span class="sxs-lookup"><span data-stu-id="2be61-106">Decide which of the channel [Message Exchange Patterns](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel, or IReplyChannel) your ChannelFactory and ChannelListener will support.</span></span> <span data-ttu-id="2be61-107">然后确定是否要支持这些接口的会话变体。</span><span class="sxs-lookup"><span data-stu-id="2be61-107">Then decide whether you will support the sessionful variations of these interfaces.</span></span>  
  
2. <span data-ttu-id="2be61-108">创建支持您的消息交换模式的通道工厂和侦听器。</span><span class="sxs-lookup"><span data-stu-id="2be61-108">Create a channel factory and listener that support your Message Exchange Pattern.</span></span>  
  
3. <span data-ttu-id="2be61-109">请确保将特定于网络的任何异常正常化为 <xref:System.ServiceModel.CommunicationException> 的相应派生类。</span><span class="sxs-lookup"><span data-stu-id="2be61-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
4. <span data-ttu-id="2be61-110">添加一个 [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) 元素，该元素将自定义传输添加到通道堆栈。</span><span class="sxs-lookup"><span data-stu-id="2be61-110">Add a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="2be61-111">有关详细信息，请参阅 [添加绑定元素](#AddingABindingElement)。</span><span class="sxs-lookup"><span data-stu-id="2be61-111">For more information, see [Adding a Binding Element](#AddingABindingElement).</span></span>  
  
5. <span data-ttu-id="2be61-112">添加一个绑定元素扩展部分，以便将新的绑定元素公开到配置系统。</span><span class="sxs-lookup"><span data-stu-id="2be61-112">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
6. <span data-ttu-id="2be61-113">添加元数据扩展以将各种功能传递给其他终结点。</span><span class="sxs-lookup"><span data-stu-id="2be61-113">Add metadata extensions to communicate capabilities to other endpoints.</span></span>  
  
7. <span data-ttu-id="2be61-114">添加一个绑定，该绑定根据定义完善的配置文件来预配置绑定元素堆栈。</span><span class="sxs-lookup"><span data-stu-id="2be61-114">Add a binding that pre-configures a stack of binding elements according to a well-defined profile.</span></span> <span data-ttu-id="2be61-115">有关详细信息，请参阅 [添加标准绑定](#AddingAStandardBinding)。</span><span class="sxs-lookup"><span data-stu-id="2be61-115">For more information, see [Adding a Standard Binding](#AddingAStandardBinding).</span></span>  
  
8. <span data-ttu-id="2be61-116">添加一个绑定部分和绑定配置元素，以便将该绑定公开到配置系统。</span><span class="sxs-lookup"><span data-stu-id="2be61-116">Add a binding section and binding configuration element to expose the binding to the configuration system.</span></span> <span data-ttu-id="2be61-117">有关详细信息，请参阅 [添加配置支持](#AddingConfigurationSupport)。</span><span class="sxs-lookup"><span data-stu-id="2be61-117">For more information, see [Adding Configuration Support](#AddingConfigurationSupport).</span></span>  
  
<a name="MessageExchangePatterns"></a>
## <a name="message-exchange-patterns"></a><span data-ttu-id="2be61-118">消息交换模式</span><span class="sxs-lookup"><span data-stu-id="2be61-118">Message Exchange Patterns</span></span>  
 <span data-ttu-id="2be61-119">编写自定义传输的第一步是决定该传输需要哪些消息交换模式 (MEP)。</span><span class="sxs-lookup"><span data-stu-id="2be61-119">The first step in writing a custom transport is to decide which Message Exchange Patterns (MEPs) are required for the transport.</span></span> <span data-ttu-id="2be61-120">有三种 MEP 可供选择：</span><span class="sxs-lookup"><span data-stu-id="2be61-120">There are three MEPs to choose from:</span></span>  
  
- <span data-ttu-id="2be61-121">数据报 (IInputChannel/IOutputChannel)</span><span class="sxs-lookup"><span data-stu-id="2be61-121">Datagram (IInputChannel/IOutputChannel)</span></span>  
  
     <span data-ttu-id="2be61-122">当使用数据报 MEP 时，客户端使用“启动后不管”交换形式发送消息。</span><span class="sxs-lookup"><span data-stu-id="2be61-122">When using a datagram MEP, a client sends a message using a "fire and forget" exchange.</span></span> <span data-ttu-id="2be61-123">“发后不理”交换形式是一种要求带外确认成功传递的交换形式。</span><span class="sxs-lookup"><span data-stu-id="2be61-123">A fire and forget exchange is one that requires out-of-band confirmation of successful delivery.</span></span> <span data-ttu-id="2be61-124">消息在传输过程中可能会丢失，而永远不能到达服务。</span><span class="sxs-lookup"><span data-stu-id="2be61-124">The message might be lost in transit and never reach the service.</span></span> <span data-ttu-id="2be61-125">如果在客户端成功完成发送操作，这并不保证远程终结点已经收到消息。</span><span class="sxs-lookup"><span data-stu-id="2be61-125">If the send operation completes successfully at the client end, it does not guarantee that the remote endpoint has received the message.</span></span> <span data-ttu-id="2be61-126">数据报是消息传递的基本构造块，因为您可以在它上面构建自己的协议，包括可靠的协议和安全的协议。</span><span class="sxs-lookup"><span data-stu-id="2be61-126">The datagram is a fundamental building block for messaging, as you can build your own protocols on top of it—including reliable protocols and secure protocols.</span></span> <span data-ttu-id="2be61-127">客户端数据报通道实现 <xref:System.ServiceModel.Channels.IOutputChannel> 接口，而服务数据报通道实现 <xref:System.ServiceModel.Channels.IInputChannel> 接口。</span><span class="sxs-lookup"><span data-stu-id="2be61-127">Client datagram channels implement the <xref:System.ServiceModel.Channels.IOutputChannel> interface and service datagram channels implement the <xref:System.ServiceModel.Channels.IInputChannel> interface.</span></span>  
  
- <span data-ttu-id="2be61-128">请求/响应 (IRequestChannel/IReplyChannel)</span><span class="sxs-lookup"><span data-stu-id="2be61-128">Request-Response (IRequestChannel/IReplyChannel)</span></span>  
  
     <span data-ttu-id="2be61-129">在此 MEP 中，将发送一个消息并接收一个答复。</span><span class="sxs-lookup"><span data-stu-id="2be61-129">In this MEP, a message is sent, and a reply is received.</span></span> <span data-ttu-id="2be61-130">此模式由请求-响应对组成。</span><span class="sxs-lookup"><span data-stu-id="2be61-130">The pattern consists of request-response pairs.</span></span> <span data-ttu-id="2be61-131">请求-响应调用的示例有远程过程调用 (RPC) 和浏览器 GET。</span><span class="sxs-lookup"><span data-stu-id="2be61-131">Examples of request-response calls are remote procedure calls (RPC) and browser GETs.</span></span> <span data-ttu-id="2be61-132">此模式也称为半双工。</span><span class="sxs-lookup"><span data-stu-id="2be61-132">This pattern is also known as Half-Duplex.</span></span> <span data-ttu-id="2be61-133">在此 MEP 中，客户端通道实现 <xref:System.ServiceModel.Channels.IRequestChannel>，而服务通道实现 <xref:System.ServiceModel.Channels.IReplyChannel>。</span><span class="sxs-lookup"><span data-stu-id="2be61-133">In this MEP, client channels implement <xref:System.ServiceModel.Channels.IRequestChannel> and service channels implement <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span>  
  
- <span data-ttu-id="2be61-134">双工 (IDuplexChannel)</span><span class="sxs-lookup"><span data-stu-id="2be61-134">Duplex (IDuplexChannel)</span></span>  
  
     <span data-ttu-id="2be61-135">通过双工 MEP，客户端可以发送任意数目的消息，并以任意顺序接收消息。</span><span class="sxs-lookup"><span data-stu-id="2be61-135">The duplex MEP allows an arbitrary number of messages to be sent by a client and received in any order.</span></span> <span data-ttu-id="2be61-136">双工 MEP 就像电话通话，所说的每一个字都是一条消息。</span><span class="sxs-lookup"><span data-stu-id="2be61-136">The duplex MEP is like a phone conversation, where each word being spoken is a message.</span></span> <span data-ttu-id="2be61-137">由于在这种 MEP 中两端都可发送和接收，因此，由客户端和服务通道实现的接口为 <xref:System.ServiceModel.Channels.IDuplexChannel>。</span><span class="sxs-lookup"><span data-stu-id="2be61-137">Because both sides can send and receive in this MEP, the interface implemented by the client and service channels is <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
 <span data-ttu-id="2be61-138">每个 MEP 还可以支持会话。</span><span class="sxs-lookup"><span data-stu-id="2be61-138">Each of these MEPs can also support sessions.</span></span> <span data-ttu-id="2be61-139">具有会话功能的通道所提供的额外功能是它能够关联在一个通道上发送和接收的所有消息。</span><span class="sxs-lookup"><span data-stu-id="2be61-139">The added functionality provided by a session-aware channel is that it correlates all messages sent and received on a channel.</span></span> <span data-ttu-id="2be61-140">请求-响应模式是一种由两个消息组成的独立会话，因为请求和响应是相关的。</span><span class="sxs-lookup"><span data-stu-id="2be61-140">The Request-Response pattern is a stand-alone two-message session, as the request and reply are correlated.</span></span> <span data-ttu-id="2be61-141">与此形成对照的是，支持会话的请求-响应模式意味着该通道上的所有请求-响应对都是相关的。</span><span class="sxs-lookup"><span data-stu-id="2be61-141">In contrast, the Request-Response pattern that supports sessions implies that all request/response pairs on that channel are correlated with each other.</span></span> <span data-ttu-id="2be61-142">这样总共提供了六个 MEP 供您选择：数据报、请求-响应、双工、具有会话的数据报、具有会话的请求-响应以及具有会话的双工。</span><span class="sxs-lookup"><span data-stu-id="2be61-142">This gives you a total of six MEPs—Datagram, Request-Response, Duplex, Datagram with sessions, Request-Response with sessions, and Duplex with sessions—to choose from.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2be61-143">对于 UDP 传输，所支持的唯一 MEP 是数据报，因为 UDP 的性质是一个“启动后不管”协议。</span><span class="sxs-lookup"><span data-stu-id="2be61-143">For the UDP transport, the only MEP that is supported is Datagram, because UDP is inherently a "fire and forget" protocol.</span></span>  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a><span data-ttu-id="2be61-144">ICommunicationObject 和 WCF 对象生存期</span><span class="sxs-lookup"><span data-stu-id="2be61-144">The ICommunicationObject and the WCF object lifecycle</span></span>  
 <span data-ttu-id="2be61-145">WCF 具有一个通用状态计算机，用于管理用于通信的对象（如、和）的生命周期 <xref:System.ServiceModel.Channels.IChannel> <xref:System.ServiceModel.Channels.IChannelFactory> <xref:System.ServiceModel.Channels.IChannelListener> 。</span><span class="sxs-lookup"><span data-stu-id="2be61-145">WCF has a common state machine that is used for managing the lifecycle of objects like <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, and <xref:System.ServiceModel.Channels.IChannelListener> that are used for communication.</span></span> <span data-ttu-id="2be61-146">这些通信对象可以处于五种状态。</span><span class="sxs-lookup"><span data-stu-id="2be61-146">There are five states in which these communication objects can exist.</span></span> <span data-ttu-id="2be61-147">这些状态通过 <xref:System.ServiceModel.CommunicationState> 枚举来表示，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2be61-147">These states are represented by the <xref:System.ServiceModel.CommunicationState> enumeration, and are as follows:</span></span>  
  
- <span data-ttu-id="2be61-148">已创建：这是 <xref:System.ServiceModel.ICommunicationObject> 在首次实例化后的状态。</span><span class="sxs-lookup"><span data-stu-id="2be61-148">Created: This is the state of a <xref:System.ServiceModel.ICommunicationObject> when it is first instantiated.</span></span> <span data-ttu-id="2be61-149">在此状态中不会发生输入/输出 (I/O)。</span><span class="sxs-lookup"><span data-stu-id="2be61-149">No input/output (I/O) occurs in this state.</span></span>  
  
- <span data-ttu-id="2be61-150">正在打开：当调用 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 时，对象即转换到此状态。</span><span class="sxs-lookup"><span data-stu-id="2be61-150">Opening: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="2be61-151">此时，属性被设置为不可变属性，并且可以开始输入/输出。</span><span class="sxs-lookup"><span data-stu-id="2be61-151">At this point properties are made immutable, and input/output can begin.</span></span> <span data-ttu-id="2be61-152">此转换只有从“已创建”状态转换才有效。</span><span class="sxs-lookup"><span data-stu-id="2be61-152">This transition is valid only from the Created state.</span></span>  
  
- <span data-ttu-id="2be61-153">已打开：当打开进程完成后，对象即转换到此状态。</span><span class="sxs-lookup"><span data-stu-id="2be61-153">Opened: Objects transition to this state when the open process completes.</span></span> <span data-ttu-id="2be61-154">此转换只有从“正在打开”状态转换才有效。</span><span class="sxs-lookup"><span data-stu-id="2be61-154">This transition is valid only from the Opening state.</span></span> <span data-ttu-id="2be61-155">此时，对象完全可用于传送。</span><span class="sxs-lookup"><span data-stu-id="2be61-155">At this point, the object is fully usable for transfer.</span></span>  
  
- <span data-ttu-id="2be61-156">正在关闭：当调用 <xref:System.ServiceModel.ICommunicationObject.Close%2A> 以完成正常关闭时，对象即转换到此状态。</span><span class="sxs-lookup"><span data-stu-id="2be61-156">Closing: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Close%2A> is called for a graceful shutdown.</span></span> <span data-ttu-id="2be61-157">此转换只有从“已打开”状态转换才有效。</span><span class="sxs-lookup"><span data-stu-id="2be61-157">This transition is valid only from the Opened state.</span></span>  
  
- <span data-ttu-id="2be61-158">已关闭：在“已关闭”状态下，对象无法再使用。</span><span class="sxs-lookup"><span data-stu-id="2be61-158">Closed: In the Closed state objects are no longer usable.</span></span> <span data-ttu-id="2be61-159">一般情况下，仍然可以访问大多数配置以进行检查，但不能进行通信。</span><span class="sxs-lookup"><span data-stu-id="2be61-159">In general, most configuration is still accessible for inspection, but no communication can occur.</span></span> <span data-ttu-id="2be61-160">此状态相当于被释放。</span><span class="sxs-lookup"><span data-stu-id="2be61-160">This state is equivalent to being disposed.</span></span>  
  
- <span data-ttu-id="2be61-161">出错：在“出错”状态下，可以访问对象以进行检查，但对象无法再使用。</span><span class="sxs-lookup"><span data-stu-id="2be61-161">Faulted: In the Faulted state, objects are accessible to inspection but no longer usable.</span></span> <span data-ttu-id="2be61-162">当发生不可恢复的错误时，对象即转换到此状态。</span><span class="sxs-lookup"><span data-stu-id="2be61-162">When a non-recoverable error occurs, the object transitions into this state.</span></span> <span data-ttu-id="2be61-163">此状态的唯一有效转换为 `Closed` 状态。</span><span class="sxs-lookup"><span data-stu-id="2be61-163">The only valid transition from this state is into the `Closed` state.</span></span>  
  
 <span data-ttu-id="2be61-164">每次状态转换都会触发事件。</span><span class="sxs-lookup"><span data-stu-id="2be61-164">There are events that fire for each state transition.</span></span> <span data-ttu-id="2be61-165">可以随时调用 <xref:System.ServiceModel.ICommunicationObject.Abort%2A> 方法，它将导致对象立即从当前状态转换到“已关闭”状态。</span><span class="sxs-lookup"><span data-stu-id="2be61-165">The <xref:System.ServiceModel.ICommunicationObject.Abort%2A> method can be called at any time, and causes the object to transition immediately from its current state into the Closed state.</span></span> <span data-ttu-id="2be61-166">调用 <xref:System.ServiceModel.ICommunicationObject.Abort%2A> 将终止任何未完成的工作。</span><span class="sxs-lookup"><span data-stu-id="2be61-166">Calling <xref:System.ServiceModel.ICommunicationObject.Abort%2A> terminates any unfinished work.</span></span>  
  
<a name="ChannelAndChannelListener"></a>
## <a name="channel-factory-and-channel-listener"></a><span data-ttu-id="2be61-167">通道工厂和通道侦听器</span><span class="sxs-lookup"><span data-stu-id="2be61-167">Channel Factory and Channel Listener</span></span>  
 <span data-ttu-id="2be61-168">编写自定义传输的下一步是为客户端通道创建 <xref:System.ServiceModel.Channels.IChannelFactory> 的实现，并为服务通道创建 <xref:System.ServiceModel.Channels.IChannelListener> 的实现。</span><span class="sxs-lookup"><span data-stu-id="2be61-168">The next step in writing a custom transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span> <span data-ttu-id="2be61-169">通道层使用工厂模式构建通道。</span><span class="sxs-lookup"><span data-stu-id="2be61-169">The channel layer uses a factory pattern for constructing channels.</span></span> <span data-ttu-id="2be61-170">WCF 为此过程提供基类帮助程序。</span><span class="sxs-lookup"><span data-stu-id="2be61-170">WCF provides base class helpers for this process.</span></span>  
  
- <span data-ttu-id="2be61-171"><xref:System.ServiceModel.Channels.CommunicationObject> 类实现 <xref:System.ServiceModel.ICommunicationObject> 并强制执行前面步骤 2 中所述的状态机。</span><span class="sxs-lookup"><span data-stu-id="2be61-171">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine previously described in Step 2.</span></span>

- <span data-ttu-id="2be61-172"><xref:System.ServiceModel.Channels.ChannelManagerBase> 类实现 <xref:System.ServiceModel.Channels.CommunicationObject> 并为 <xref:System.ServiceModel.Channels.ChannelFactoryBase> 和 <xref:System.ServiceModel.Channels.ChannelListenerBase> 提供统一的基类。</span><span class="sxs-lookup"><span data-stu-id="2be61-172">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase> and <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span></span> <span data-ttu-id="2be61-173"><xref:System.ServiceModel.Channels.ChannelManagerBase> 类与 <xref:System.ServiceModel.Channels.ChannelBase>（用来实现 <xref:System.ServiceModel.Channels.IChannel> 的基类）结合使用。</span><span class="sxs-lookup"><span data-stu-id="2be61-173">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>  
  
- <span data-ttu-id="2be61-174"><xref:System.ServiceModel.Channels.ChannelFactoryBase>类实现 <xref:System.ServiceModel.Channels.ChannelManagerBase> 和 <xref:System.ServiceModel.Channels.IChannelFactory> ，并将重载合并 `CreateChannel` 到一个 `OnCreateChannel` 抽象方法中。</span><span class="sxs-lookup"><span data-stu-id="2be61-174">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>  
  
- <span data-ttu-id="2be61-175"><xref:System.ServiceModel.Channels.ChannelListenerBase> 类实现 <xref:System.ServiceModel.Channels.IChannelListener>。</span><span class="sxs-lookup"><span data-stu-id="2be61-175">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="2be61-176">它负责执行基本状态管理。</span><span class="sxs-lookup"><span data-stu-id="2be61-176">It takes care of basic state management.</span></span>  
  
 <span data-ttu-id="2be61-177">在此示例中，工厂实现包含在 UdpChannelFactory.cs 中，侦听器实现包含在 UdpChannelListener.cs 中。</span><span class="sxs-lookup"><span data-stu-id="2be61-177">In this sample, the factory implementation is contained in UdpChannelFactory.cs and the listener implementation is contained in UdpChannelListener.cs.</span></span> <span data-ttu-id="2be61-178"><xref:System.ServiceModel.Channels.IChannel> 实现位于 UdpOutputChannel.cs 和 UdpInputChannel.cs 中。</span><span class="sxs-lookup"><span data-stu-id="2be61-178">The <xref:System.ServiceModel.Channels.IChannel> implementations are in UdpOutputChannel.cs and UdpInputChannel.cs.</span></span>  
  
### <a name="the-udp-channel-factory"></a><span data-ttu-id="2be61-179">UDP 通道工厂</span><span class="sxs-lookup"><span data-stu-id="2be61-179">The UDP Channel Factory</span></span>  
 <span data-ttu-id="2be61-180">`UdpChannelFactory` 派生自 <xref:System.ServiceModel.Channels.ChannelFactoryBase>。</span><span class="sxs-lookup"><span data-stu-id="2be61-180">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="2be61-181">该示例重写 <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> 以提供对消息编码器的消息版本的访问。</span><span class="sxs-lookup"><span data-stu-id="2be61-181">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="2be61-182">此示例还重写了 <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A>，因此我们可以在状态机转换时拆开 <xref:System.ServiceModel.Channels.BufferManager> 的实例。</span><span class="sxs-lookup"><span data-stu-id="2be61-182">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> so that we can tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="2be61-183">UDP 输出通道</span><span class="sxs-lookup"><span data-stu-id="2be61-183">The UDP Output Channel</span></span>  
 <span data-ttu-id="2be61-184">`UdpOutputChannel` 实现 <xref:System.ServiceModel.Channels.IOutputChannel>。</span><span class="sxs-lookup"><span data-stu-id="2be61-184">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="2be61-185">构造函数对自变量进行验证，并基于传入的 <xref:System.Net.EndPoint> 来构造目标 <xref:System.ServiceModel.EndpointAddress> 对象。</span><span class="sxs-lookup"><span data-stu-id="2be61-185">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 <span data-ttu-id="2be61-186">通道可以正常关闭或非正常关闭。</span><span class="sxs-lookup"><span data-stu-id="2be61-186">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="2be61-187">如果通道正常关闭，则套接字也将关闭，并调用基类 `OnClose` 方法。</span><span class="sxs-lookup"><span data-stu-id="2be61-187">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="2be61-188">如果引发异常，则基础结构将调用 `Abort` 以确保清理该通道。</span><span class="sxs-lookup"><span data-stu-id="2be61-188">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp
this.socket.Close(0);  
```  
  
 <span data-ttu-id="2be61-189">然后，实现 `Send()` 和 `BeginSend()` / `EndSend()` 。</span><span class="sxs-lookup"><span data-stu-id="2be61-189">We then implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="2be61-190">这将分解为两个主要部分。</span><span class="sxs-lookup"><span data-stu-id="2be61-190">This breaks down into two main sections.</span></span> <span data-ttu-id="2be61-191">首先，将消息序列化为字节数组。</span><span class="sxs-lookup"><span data-stu-id="2be61-191">First we serialize the message into a byte array.</span></span>  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="2be61-192">然后，在网络上发送生成的数据。</span><span class="sxs-lookup"><span data-stu-id="2be61-192">Then we send the resulting data on the wire.</span></span>  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a><span data-ttu-id="2be61-193">UdpChannelListener</span><span class="sxs-lookup"><span data-stu-id="2be61-193">The UdpChannelListener</span></span>  
 <span data-ttu-id="2be61-194">`UdpChannelListener`示例实现的派生自 <xref:System.ServiceModel.Channels.ChannelListenerBase> 类。</span><span class="sxs-lookup"><span data-stu-id="2be61-194">The `UdpChannelListener` that the sample implements derives from the <xref:System.ServiceModel.Channels.ChannelListenerBase> class.</span></span> <span data-ttu-id="2be61-195">它使用单个 UDP 套接字来接收数据报。</span><span class="sxs-lookup"><span data-stu-id="2be61-195">It uses a single UDP socket to receive datagrams.</span></span> <span data-ttu-id="2be61-196">`OnOpen` 方法使用该 UDP 套接字以异步循环形式接收数据。</span><span class="sxs-lookup"><span data-stu-id="2be61-196">The `OnOpen` method receives data using the UDP socket in an asynchronous loop.</span></span> <span data-ttu-id="2be61-197">收到的数据随后将借助于消息编码系统转换为消息。</span><span class="sxs-lookup"><span data-stu-id="2be61-197">The data are then converted into messages using the Message Encoding Framework.</span></span>  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 <span data-ttu-id="2be61-198">由于可以用同一个数据报通道来表示来自多个源的消息，因此 `UdpChannelListener` 是一个单一实例侦听器。</span><span class="sxs-lookup"><span data-stu-id="2be61-198">Because the same datagram channel represents messages that arrive from a number of sources, the `UdpChannelListener` is a singleton listener.</span></span> <span data-ttu-id="2be61-199">一次最多有一个 <xref:System.ServiceModel.Channels.IChannel> 与此侦听器关联的活动。</span><span class="sxs-lookup"><span data-stu-id="2be61-199">There is, at most, one active <xref:System.ServiceModel.Channels.IChannel> associated with this listener at a time.</span></span> <span data-ttu-id="2be61-200">只有当随后释放了由 `AcceptChannel` 方法返回的通道时，该示例才生成另一个通道。</span><span class="sxs-lookup"><span data-stu-id="2be61-200">The sample generates another one only if a channel that is returned by the `AcceptChannel` method is subsequently disposed.</span></span> <span data-ttu-id="2be61-201">收到的消息将排入这个单一实例通道的队列中。</span><span class="sxs-lookup"><span data-stu-id="2be61-201">When a message is received, it is enqueued into this singleton channel.</span></span>  
  
#### <a name="udpinputchannel"></a><span data-ttu-id="2be61-202">UdpInputChannel</span><span class="sxs-lookup"><span data-stu-id="2be61-202">UdpInputChannel</span></span>  
 <span data-ttu-id="2be61-203">`UdpInputChannel` 类实现 `IInputChannel`。</span><span class="sxs-lookup"><span data-stu-id="2be61-203">The `UdpInputChannel` class implements `IInputChannel`.</span></span> <span data-ttu-id="2be61-204">该类包括一个传入消息队列，该队列由 `UdpChannelListener` 的套接字来填充。</span><span class="sxs-lookup"><span data-stu-id="2be61-204">It consists of a queue of incoming messages that is populated by the `UdpChannelListener`'s socket.</span></span> <span data-ttu-id="2be61-205">这些消息可以由 `IInputChannel.Receive` 方法取消排队。</span><span class="sxs-lookup"><span data-stu-id="2be61-205">These messages are dequeued by the `IInputChannel.Receive` method.</span></span>  
  
<a name="AddingABindingElement"></a>
## <a name="adding-a-binding-element"></a><span data-ttu-id="2be61-206">添加绑定元素</span><span class="sxs-lookup"><span data-stu-id="2be61-206">Adding a Binding Element</span></span>  
 <span data-ttu-id="2be61-207">现在已经生成了工厂和通道，必须通过绑定将它们公开给 ServiceModel 运行库。</span><span class="sxs-lookup"><span data-stu-id="2be61-207">Now that the factories and channels are built, we must expose them to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="2be61-208">绑定是指绑定元素的集合，该集合表示与服务地址相关联的通信堆栈。</span><span class="sxs-lookup"><span data-stu-id="2be61-208">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="2be61-209">堆栈中的每个元素都由 [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) 元素表示。</span><span class="sxs-lookup"><span data-stu-id="2be61-209">Each element in the stack is represented by a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
 <span data-ttu-id="2be61-210">在下面的示例中，绑定元素为 `UdpTransportBindingElement`，它派生自 <xref:System.ServiceModel.Channels.TransportBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="2be61-210">In the sample, the binding element is `UdpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="2be61-211">它重写以下方法以生成与我们的绑定相关联的工厂。</span><span class="sxs-lookup"><span data-stu-id="2be61-211">It overrides the following methods to build the factories associated with our binding.</span></span>  
  
```csharp
public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
{  
    return (IChannelFactory<TChannel>)(object)new UdpChannelFactory(this, context);  
}  
  
public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
{  
    return (IChannelListener<TChannel>)(object)new UdpChannelListener(this, context);  
}  
```  
  
 <span data-ttu-id="2be61-212">它还包含用于克隆 `BindingElement` 并返回我们自己的方案 (soap.udp) 的成员。</span><span class="sxs-lookup"><span data-stu-id="2be61-212">It also contains members for cloning the `BindingElement` and returning our scheme (soap.udp).</span></span>  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a><span data-ttu-id="2be61-213">为传输绑定元素添加元数据支持</span><span class="sxs-lookup"><span data-stu-id="2be61-213">Adding Metadata Support for a Transport Binding Element</span></span>  
 <span data-ttu-id="2be61-214">若要将我们的传输集成到元数据系统中，我们必须支持策略的导入和导出。</span><span class="sxs-lookup"><span data-stu-id="2be61-214">To integrate our transport into the metadata system, we must support both the import and export of policy.</span></span> <span data-ttu-id="2be61-215">这样，我们便可以通过 " [ ( # A0) ](../servicemodel-metadata-utility-tool-svcutil-exe.md)使用</span><span class="sxs-lookup"><span data-stu-id="2be61-215">This allows us to generate clients of our binding through the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="2be61-216">添加 WSDL 支持</span><span class="sxs-lookup"><span data-stu-id="2be61-216">Adding WSDL Support</span></span>  
 <span data-ttu-id="2be61-217">绑定中的传输绑定元素负责导出和导入元数据中的寻址信息。</span><span class="sxs-lookup"><span data-stu-id="2be61-217">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="2be61-218">当使用 SOAP 绑定时，传输绑定元素还应在元数据中导出正确的传输 URI。</span><span class="sxs-lookup"><span data-stu-id="2be61-218">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="2be61-219">WSDL 导出</span><span class="sxs-lookup"><span data-stu-id="2be61-219">WSDL Export</span></span>  
 <span data-ttu-id="2be61-220">若要导出寻址信息，`UdpTransportBindingElement` 需要实现 `IWsdlExportExtension` 接口。</span><span class="sxs-lookup"><span data-stu-id="2be61-220">To export addressing information the `UdpTransportBindingElement` implements the `IWsdlExportExtension` interface.</span></span> <span data-ttu-id="2be61-221">`ExportEndpoint` 方法将正确的寻址信息添加到 WSDL 端口中。</span><span class="sxs-lookup"><span data-stu-id="2be61-221">The `ExportEndpoint` method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="2be61-222">当终结点使用 SOAP 绑定时，`UdpTransportBindingElement` 方法的 `ExportEndpoint` 实现也会导出传输 URI。</span><span class="sxs-lookup"><span data-stu-id="2be61-222">The `UdpTransportBindingElement` implementation of the `ExportEndpoint` method also exports a transport URI when the endpoint uses a SOAP binding.</span></span>  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="2be61-223">WSDL 导入</span><span class="sxs-lookup"><span data-stu-id="2be61-223">WSDL Import</span></span>  
 <span data-ttu-id="2be61-224">若要扩展 WSDL 导入系统以处理导入地址，必须将以下配置添加到 Svcutil.exe 的配置文件中，如 Svcutil.exe.config 文件所示。</span><span class="sxs-lookup"><span data-stu-id="2be61-224">To extend the WSDL import system to handle importing the addresses, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="2be61-225">当运行 Svcutil.exe 时，有两个选项可用来获取 Svcutil.exe 以加载 WSDL 导入扩展：</span><span class="sxs-lookup"><span data-stu-id="2be61-225">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1. <span data-ttu-id="2be61-226">使用/SvcutilConfig 将 Svcutil.exe 点指向配置文件： \<file> 。</span><span class="sxs-lookup"><span data-stu-id="2be61-226">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="2be61-227">将配置节添加到与 Svcutil.exe 处于同一目录的 Svcutil.exe.config 中。</span><span class="sxs-lookup"><span data-stu-id="2be61-227">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="2be61-228">`UdpBindingElementImporter` 类型实现 `IWsdlImportExtension` 接口。</span><span class="sxs-lookup"><span data-stu-id="2be61-228">The `UdpBindingElementImporter` type implements the `IWsdlImportExtension` interface.</span></span> <span data-ttu-id="2be61-229">`ImportEndpoint` 方法从 WSDL 端口中导入地址。</span><span class="sxs-lookup"><span data-stu-id="2be61-229">The `ImportEndpoint` method imports the address from the WSDL port.</span></span>  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="2be61-230">添加策略支持</span><span class="sxs-lookup"><span data-stu-id="2be61-230">Adding Policy Support</span></span>  
 <span data-ttu-id="2be61-231">自定义绑定元素可以在 WSDL 绑定中为服务终结点导出策略断言以表示该绑定元素的功能。</span><span class="sxs-lookup"><span data-stu-id="2be61-231">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="2be61-232">策略导出</span><span class="sxs-lookup"><span data-stu-id="2be61-232">Policy Export</span></span>  
 <span data-ttu-id="2be61-233">`UdpTransportBindingElement`实现 `IPolicyExportExtension` 以添加对导出策略的支持的类型。</span><span class="sxs-lookup"><span data-stu-id="2be61-233">The `UdpTransportBindingElement` type implements `IPolicyExportExtension` to add support for exporting policy.</span></span> <span data-ttu-id="2be61-234">因此，`System.ServiceModel.MetadataExporter` 在为任何包含它的绑定而生成策略时都包含 `UdpTransportBindingElement`。</span><span class="sxs-lookup"><span data-stu-id="2be61-234">As a result, `System.ServiceModel.MetadataExporter` includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="2be61-235">在 `IPolicyExportExtension.ExportPolicy` 中，如果我们在多播模式下，则添加 UDP 的断言和另一个断言。</span><span class="sxs-lookup"><span data-stu-id="2be61-235">In `IPolicyExportExtension.ExportPolicy`, we add an assertion for UDP and another assertion if we are in multicast mode.</span></span> <span data-ttu-id="2be61-236">这是因为，多路广播模式影响通信堆栈的构造方式，因此必须在两端之间进行协调。</span><span class="sxs-lookup"><span data-stu-id="2be61-236">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
```csharp
ICollection<XmlElement> bindingAssertions = context.GetBindingAssertions();  
XmlDocument xmlDocument = new XmlDocument();  
bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.TransportAssertion, UdpPolicyStrings.UdpNamespace));  
if (Multicast)  
{  
    bindingAssertions.Add(xmlDocument.CreateElement(
        UdpPolicyStrings.Prefix,
        UdpPolicyStrings.MulticastAssertion,
        UdpPolicyStrings.UdpNamespace));  
}  
```  
  
 <span data-ttu-id="2be61-237">因为自定义传输绑定元素负责处理寻址，所以 `IPolicyExportExtension` 上的 `UdpTransportBindingElement` 实现还必须处理导出相应的 WS-Addressing 策略断言以指示正在使用的 WS-Addressing 的版本。</span><span class="sxs-lookup"><span data-stu-id="2be61-237">Because custom transport binding elements are responsible for handling addressing, the `IPolicyExportExtension` implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="2be61-238">策略导入</span><span class="sxs-lookup"><span data-stu-id="2be61-238">Policy Import</span></span>  
 <span data-ttu-id="2be61-239">若要扩展策略导入系统，必须将以下配置添加到 Svcutil.exe 的配置文件中，如 Svcutil.exe.config 文件所示。</span><span class="sxs-lookup"><span data-stu-id="2be61-239">To extend the Policy Import system, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="2be61-240">然后从已注册的类 (`IPolicyImporterExtension`) 中实现 `UdpBindingElementImporter`。</span><span class="sxs-lookup"><span data-stu-id="2be61-240">Then we implement `IPolicyImporterExtension` from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="2be61-241">在 `ImportPolicy()` 中，浏览命名空间中的断言，处理用于生成传输的断言，并检查它是否为多播。</span><span class="sxs-lookup"><span data-stu-id="2be61-241">In `ImportPolicy()`, we look through the assertions in our namespace, and process the ones for generating the transport and check whether it is multicast.</span></span> <span data-ttu-id="2be61-242">还必须从绑定断言列表中移除已经处理的断言。</span><span class="sxs-lookup"><span data-stu-id="2be61-242">We also must remove the assertions we handle from the list of binding assertions.</span></span> <span data-ttu-id="2be61-243">同样，当运行 Svcutil.exe 时，有两个用于集成的选项：</span><span class="sxs-lookup"><span data-stu-id="2be61-243">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1. <span data-ttu-id="2be61-244">使用/SvcutilConfig 将 Svcutil.exe 点指向配置文件： \<file> 。</span><span class="sxs-lookup"><span data-stu-id="2be61-244">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="2be61-245">将配置节添加到与 Svcutil.exe 处于同一目录的 Svcutil.exe.config 中。</span><span class="sxs-lookup"><span data-stu-id="2be61-245">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
<a name="AddingAStandardBinding"></a>
## <a name="adding-a-standard-binding"></a><span data-ttu-id="2be61-246">添加标准绑定</span><span class="sxs-lookup"><span data-stu-id="2be61-246">Adding a Standard Binding</span></span>  
 <span data-ttu-id="2be61-247">绑定元素可以按照以下两种方式使用：</span><span class="sxs-lookup"><span data-stu-id="2be61-247">Our binding element can be used in the following two ways:</span></span>  
  
- <span data-ttu-id="2be61-248">通过自定义绑定：自定义绑定允许用户根据任意一组绑定元素创建自己的绑定。</span><span class="sxs-lookup"><span data-stu-id="2be61-248">Through a custom binding: A custom binding allows the user to create their own binding based on an arbitrary set of binding elements.</span></span>  
  
- <span data-ttu-id="2be61-249">通过使用系统提供的、包含我们的绑定元素的绑定。</span><span class="sxs-lookup"><span data-stu-id="2be61-249">By using a system-provided binding that includes our binding element.</span></span> <span data-ttu-id="2be61-250">WCF 提供了许多这些系统定义的绑定，如 `BasicHttpBinding` 、 `NetTcpBinding` 和 `WsHttpBinding` 。</span><span class="sxs-lookup"><span data-stu-id="2be61-250">WCF provides a number of these system-defined bindings, such as `BasicHttpBinding`, `NetTcpBinding`, and `WsHttpBinding`.</span></span> <span data-ttu-id="2be61-251">这些绑定中的每个绑定与一个准确定义的配置文件相关联。</span><span class="sxs-lookup"><span data-stu-id="2be61-251">Each of these bindings is associated with a well-defined profile.</span></span>  
  
 <span data-ttu-id="2be61-252">此示例在从 `SampleProfileUdpBinding` 派生的 <xref:System.ServiceModel.Channels.Binding> 中实现配置文件绑定。</span><span class="sxs-lookup"><span data-stu-id="2be61-252">The sample implements profile binding in `SampleProfileUdpBinding`, which derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="2be61-253">`SampleProfileUdpBinding` 中最多包含四个绑定元素：`UdpTransportBindingElement`、`TextMessageEncodingBindingElement CompositeDuplexBindingElement` 和 `ReliableSessionBindingElement`。</span><span class="sxs-lookup"><span data-stu-id="2be61-253">The `SampleProfileUdpBinding` contains up to four binding elements within it: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, and `ReliableSessionBindingElement`.</span></span>  
  
```csharp
public override BindingElementCollection CreateBindingElements()  
{
    BindingElementCollection bindingElements = new BindingElementCollection();  
    if (ReliableSessionEnabled)  
    {  
        bindingElements.Add(session);  
        bindingElements.Add(compositeDuplex);  
    }  
    bindingElements.Add(encoding);  
    bindingElements.Add(transport);  
    return bindingElements.Clone();  
}  
```  
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="2be61-254">添加自定义标准绑定导入程序</span><span class="sxs-lookup"><span data-stu-id="2be61-254">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="2be61-255">Svcutil.exe 和 `WsdlImporter` 类型默认情况下识别并导入系统定义的绑定。</span><span class="sxs-lookup"><span data-stu-id="2be61-255">Svcutil.exe and the `WsdlImporter` type, by default, recognizes and imports system-defined bindings.</span></span> <span data-ttu-id="2be61-256">否则，绑定将作为 `CustomBinding` 实例而导入。</span><span class="sxs-lookup"><span data-stu-id="2be61-256">Otherwise, the binding gets imported as a `CustomBinding` instance.</span></span> <span data-ttu-id="2be61-257">若要启用 Svcutil.exe 和 `WsdlImporter` 以导入 `SampleProfileUdpBinding`，`UdpBindingElementImporter` 还需充当自定义标准绑定导入程序。</span><span class="sxs-lookup"><span data-stu-id="2be61-257">To enable Svcutil.exe and the `WsdlImporter` to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="2be61-258">自定义标准绑定导入程序在 `ImportEndpoint` 接口上实现 `IWsdlImportExtension` 方法，以检查从元数据中导入的 `CustomBinding` 实例，了解它是否由特定的标准绑定生成。</span><span class="sxs-lookup"><span data-stu-id="2be61-258">A custom standard binding importer implements the `ImportEndpoint` method on the `IWsdlImportExtension` interface to examine the `CustomBinding` instance imported from metadata to see whether it could have been generated by a specific standard binding.</span></span>  
  
```csharp
if (context.Endpoint.Binding is CustomBinding)  
{  
    Binding binding;  
    if (transportBindingElement is UdpTransportBindingElement)  
    {  
        //if TryCreate is true, the CustomBinding will be replace by a SampleProfileUdpBinding in the  
        //generated config file for better typed generation.  
        if (SampleProfileUdpBinding.TryCreate(bindingElements, out binding))  
        {  
            binding.Name = context.Endpoint.Binding.Name;  
            binding.Namespace = context.Endpoint.Binding.Namespace;  
            context.Endpoint.Binding = binding;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="2be61-259">通常，实现自定义标准绑定导入程序包括检查导入的绑定元素的属性以验证是否仅更改了标准绑定可以设置的属性，而所有其他属性都是各自的默认值。</span><span class="sxs-lookup"><span data-stu-id="2be61-259">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="2be61-260">用于实现标准绑定导入程序的基本策略是创建标准绑定的实例，将绑定元素中的属性传播到标准绑定支持的标准绑定实例中，然后将标准绑定中的绑定元素与导入的绑定元素进行比较。</span><span class="sxs-lookup"><span data-stu-id="2be61-260">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>  
  
<a name="AddingConfigurationSupport"></a>
## <a name="adding-configuration-support"></a><span data-ttu-id="2be61-261">添加配置支持</span><span class="sxs-lookup"><span data-stu-id="2be61-261">Adding Configuration Support</span></span>  
 <span data-ttu-id="2be61-262">若要通过配置公开传输，必须实现两个配置节。</span><span class="sxs-lookup"><span data-stu-id="2be61-262">To expose our transport through configuration, we must implement two configuration sections.</span></span> <span data-ttu-id="2be61-263">第一个是 `BindingElementExtensionElement` 的 `UdpTransportBindingElement`。</span><span class="sxs-lookup"><span data-stu-id="2be61-263">The first is a `BindingElementExtensionElement` for `UdpTransportBindingElement`.</span></span> <span data-ttu-id="2be61-264">这样使 `CustomBinding` 实现可以引用绑定元素。</span><span class="sxs-lookup"><span data-stu-id="2be61-264">This is so that `CustomBinding` implementations can reference our binding element.</span></span> <span data-ttu-id="2be61-265">第二个是 `Configuration` 的 `SampleProfileUdpBinding`。</span><span class="sxs-lookup"><span data-stu-id="2be61-265">The second is a `Configuration` for our `SampleProfileUdpBinding`.</span></span>  
  
### <a name="binding-element-extension-element"></a><span data-ttu-id="2be61-266">绑定元素扩展元素</span><span class="sxs-lookup"><span data-stu-id="2be61-266">Binding Element Extension Element</span></span>  
 <span data-ttu-id="2be61-267">`UdpTransportElement` 节是一个 `BindingElementExtensionElement`，它向配置系统公开 `UdpTransportBindingElement`。</span><span class="sxs-lookup"><span data-stu-id="2be61-267">The section `UdpTransportElement` is a `BindingElementExtensionElement` that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="2be61-268">通过一些基本重写，我们定义了配置节名称、绑定元素的类型以及如何创建绑定元素。</span><span class="sxs-lookup"><span data-stu-id="2be61-268">With a few basic overrides, we define our configuration section name, the type of our binding element and how to create our binding element.</span></span> <span data-ttu-id="2be61-269">然后，我们可以注册配置文件中的扩展节，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="2be61-269">We can then register our extension section in a configuration file as shown in the following code.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
        <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport" />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="2be61-270">可以从自定义绑定来引用该扩展以将 UDP 用作传输协议。</span><span class="sxs-lookup"><span data-stu-id="2be61-270">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <customBinding>  
       <binding configurationName="UdpCustomBinding">  
         <udpTransport/>  
       </binding>  
      </customBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="binding-section"></a><span data-ttu-id="2be61-271">绑定节</span><span class="sxs-lookup"><span data-stu-id="2be61-271">Binding Section</span></span>  
 <span data-ttu-id="2be61-272">`SampleProfileUdpBindingCollectionElement` 节是一个 `StandardBindingCollectionElement`，它向配置系统公开 `SampleProfileUdpBinding`。</span><span class="sxs-lookup"><span data-stu-id="2be61-272">The section `SampleProfileUdpBindingCollectionElement` is a `StandardBindingCollectionElement` that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="2be61-273">批量实现委派给从 `SampleProfileUdpBindingConfigurationElement` 派生的 `StandardBindingElement`。</span><span class="sxs-lookup"><span data-stu-id="2be61-273">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from `StandardBindingElement`.</span></span> <span data-ttu-id="2be61-274">`SampleProfileUdpBindingConfigurationElement`具有与的属性相对应的属性 `SampleProfileUdpBinding` ，以及要从绑定中映射的函数 `ConfigurationElement` 。</span><span class="sxs-lookup"><span data-stu-id="2be61-274">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="2be61-275">最后，在 `OnApplyConfiguration` 中重写 `SampleProfileUdpBinding` 方法，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="2be61-275">Finally, override the `OnApplyConfiguration` method in our `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
```csharp
protected override void OnApplyConfiguration(string configurationName)  
{  
    if (binding == null)
        throw new ArgumentNullException("binding");

    if (binding.GetType() != typeof(SampleProfileUdpBinding))
    {
        throw new ArgumentException(string.Format(CultureInfo.CurrentCulture,
            "Invalid type for binding. Expected type: {0}. Type passed in: {1}.",
            typeof(SampleProfileUdpBinding).AssemblyQualifiedName,
            binding.GetType().AssemblyQualifiedName));
    }
    SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;

    udpBinding.OrderedSession = this.OrderedSession;
    udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;
    udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;
    if (this.ClientBaseAddress != null)
        udpBinding.ClientBaseAddress = ClientBaseAddress;
}
```  
  
 <span data-ttu-id="2be61-276">为了向配置系统注册此处理程序，我们将下面一节添加到相关的配置文件中。</span><span class="sxs-lookup"><span data-stu-id="2be61-276">To register this handler with the configuration system, we add the following section to the relevant configuration file.</span></span>  
  
```xml
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
        <sectionGroup name="bindings">  
          <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
        </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 <span data-ttu-id="2be61-277">然后即可从 serviceModel 配置节引用它。</span><span class="sxs-lookup"><span data-stu-id="2be61-277">It can then be referenced from the serviceModel configuration section.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint configurationName="calculator"  
                address="soap.udp://localhost:8001/"
                bindingConfiguration="CalculatorServer"  
                binding="sampleProfileUdpBinding"
                contract= "Microsoft.ServiceModel.Samples.ICalculatorContract">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="the-udp-test-service-and-client"></a><span data-ttu-id="2be61-278">UDP 测试服务和客户端</span><span class="sxs-lookup"><span data-stu-id="2be61-278">The UDP Test Service and Client</span></span>  
 <span data-ttu-id="2be61-279">用于使用此示例传输的测试代码位于 UdpTestService 和 UdpTestClient 目录中。</span><span class="sxs-lookup"><span data-stu-id="2be61-279">Test code for using this sample transport is available in the UdpTestService and UdpTestClient directories.</span></span> <span data-ttu-id="2be61-280">服务代码包含两个测试 - 一个测试从代码中设置绑定和终结点，另一个测试通过配置完成这些操作。</span><span class="sxs-lookup"><span data-stu-id="2be61-280">The service code consists of two tests—one test sets up bindings and endpoints from code and the other does it through configuration.</span></span> <span data-ttu-id="2be61-281">这两个测试都使用两个终结点。</span><span class="sxs-lookup"><span data-stu-id="2be61-281">Both tests use two endpoints.</span></span> <span data-ttu-id="2be61-282">一个终结点使用 `SampleUdpProfileBinding` [\<reliableSession>](/previous-versions/ms731375(v=vs.90)) 设置为的 `true` 。</span><span class="sxs-lookup"><span data-stu-id="2be61-282">One endpoint uses the `SampleUdpProfileBinding` with [\<reliableSession>](/previous-versions/ms731375(v=vs.90)) set to `true`.</span></span> <span data-ttu-id="2be61-283">另一个终结点使用具有 `UdpTransportBindingElement` 的自定义绑定。</span><span class="sxs-lookup"><span data-stu-id="2be61-283">The other endpoint uses a custom binding with `UdpTransportBindingElement`.</span></span> <span data-ttu-id="2be61-284">这等效于在 `SampleUdpProfileBinding` 设置为的情况下使用 [\<reliableSession>](/previous-versions/ms731375(v=vs.90)) `false` 。</span><span class="sxs-lookup"><span data-stu-id="2be61-284">This is equivalent to using `SampleUdpProfileBinding` with [\<reliableSession>](/previous-versions/ms731375(v=vs.90)) set to `false`.</span></span> <span data-ttu-id="2be61-285">这两个测试都创建一个服务，为每个绑定添加一个终结点，打开该服务，然后等待用户按 Enter 后再关闭该服务。</span><span class="sxs-lookup"><span data-stu-id="2be61-285">Both tests create a service, add an endpoint for each binding, open the service and then wait for the user to hit ENTER before closing the service.</span></span>  
  
 <span data-ttu-id="2be61-286">当您启动服务测试应用程序时，应看到如下输出。</span><span class="sxs-lookup"><span data-stu-id="2be61-286">When you start the service test application you should see the following output.</span></span>  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 <span data-ttu-id="2be61-287">然后你可以根据发布的终结点运行测试客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="2be61-287">You can then run the test client application against the published endpoints.</span></span> <span data-ttu-id="2be61-288">客户端测试应用程序为每个终结点创建一个客户端，并向每个终结点发送五条消息。</span><span class="sxs-lookup"><span data-stu-id="2be61-288">The client test application creates a client for each endpoint and sends five messages to each endpoint.</span></span> <span data-ttu-id="2be61-289">下面是客户端输出。</span><span class="sxs-lookup"><span data-stu-id="2be61-289">The following output is on the client.</span></span>  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 <span data-ttu-id="2be61-290">下面是服务的完整输出。</span><span class="sxs-lookup"><span data-stu-id="2be61-290">The following is the full output on the service.</span></span>  
  
```console
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
   adding 0 + 0  
   adding 1 + 2  
   adding 2 + 4  
   adding 3 + 6  
   adding 4 + 8  
```  
  
 <span data-ttu-id="2be61-291">若要根据使用配置发布的终结点运行客户端应用程序，请在服务中按 Enter，然后再次运行测试客户端。</span><span class="sxs-lookup"><span data-stu-id="2be61-291">To run the client application against endpoints published using configuration, hit ENTER on the service and then run the test client again.</span></span> <span data-ttu-id="2be61-292">您将在服务上看到如下输出。</span><span class="sxs-lookup"><span data-stu-id="2be61-292">You should see the following output on the service.</span></span>  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 <span data-ttu-id="2be61-293">重新运行客户端产生的结果与前面的结果相同。</span><span class="sxs-lookup"><span data-stu-id="2be61-293">Running the client again yields the same as the preceding results.</span></span>  
  
 <span data-ttu-id="2be61-294">若要使用 Svcutil.exe 重新生成客户端代码和配置，请启动服务应用程序，然后从示例的根目录中运行以下 Svcutil.exe。</span><span class="sxs-lookup"><span data-stu-id="2be61-294">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe from the root directory of the sample.</span></span>  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 <span data-ttu-id="2be61-295">请注意，Svcutil.exe 不会为 `SampleProfileUdpBinding` 生成绑定扩展配置；所以您必须手动添加它。</span><span class="sxs-lookup"><span data-stu-id="2be61-295">Note that Svcutil.exe does not generate the binding extension configuration for the `SampleProfileUdpBinding`, so you must add it manually.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>
    <extensions>  
      <!-- This was added manually because svcutil.exe does not add this extension to the file -->  
      <bindingExtensions>  
        <add name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
      </bindingExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2be61-296">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="2be61-296">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2be61-297">若要生成解决方案，请按照 [生成 Windows Communication Foundation 示例](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="2be61-297">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="2be61-298">若要以单机配置或跨计算机配置来运行示例，请按照 [运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="2be61-298">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
3. <span data-ttu-id="2be61-299">请参阅前面的“UDP 测试服务和客户端”一节。</span><span class="sxs-lookup"><span data-stu-id="2be61-299">Refer to the preceding "The UDP Test Service and Client" section.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2be61-300">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="2be61-300">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2be61-301">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="2be61-301">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="2be61-302">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2be61-302">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2be61-303">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="2be61-303">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`

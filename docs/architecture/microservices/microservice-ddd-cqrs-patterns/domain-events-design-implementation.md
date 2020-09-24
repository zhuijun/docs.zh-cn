---
title: 域事件。 设计和实现
description: 适用于容器化 .NET 应用程序的 .NET 微服务体系结构 | 深入了解域事件（在聚合之间建立通信的一个关键概念）。
ms.date: 10/08/2018
ms.openlocfilehash: e786af9b5cd005573dcc9d08a3ccd19f25f13813
ms.sourcegitcommit: a8730298170b8d96b4272e0c3dfc9819c606947b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90738770"
---
# <a name="domain-events-design-and-implementation"></a><span data-ttu-id="a8f73-104">域事件：设计和实现</span><span class="sxs-lookup"><span data-stu-id="a8f73-104">Domain events: design and implementation</span></span>

<span data-ttu-id="a8f73-105">使用域事件显式实现域中的更改的副作用。</span><span class="sxs-lookup"><span data-stu-id="a8f73-105">Use domain events to explicitly implement side effects of changes within your domain.</span></span> <span data-ttu-id="a8f73-106">如果使用 DDD 术语表述，即使用域事件跨多个聚合显式实现副作用。</span><span class="sxs-lookup"><span data-stu-id="a8f73-106">In other words, and using DDD terminology, use domain events to explicitly implement side effects across multiple aggregates.</span></span> <span data-ttu-id="a8f73-107">（可选）为了提高可伸缩性并减小对数据库锁定的影响，可在相同域的聚合之间使用最终一致性。</span><span class="sxs-lookup"><span data-stu-id="a8f73-107">Optionally, for better scalability and less impact in database locks, use eventual consistency between aggregates within the same domain.</span></span>

## <a name="what-is-a-domain-event"></a><span data-ttu-id="a8f73-108">什么是域事件？</span><span class="sxs-lookup"><span data-stu-id="a8f73-108">What is a domain event?</span></span>

<span data-ttu-id="a8f73-109">事件是过去发生的事。</span><span class="sxs-lookup"><span data-stu-id="a8f73-109">An event is something that has happened in the past.</span></span> <span data-ttu-id="a8f73-110">域事件是在域中发生的事，你希望同一个域（进程）的其他部分了解它。</span><span class="sxs-lookup"><span data-stu-id="a8f73-110">A domain event is, something that happened in the domain that you want other parts of the same domain (in-process) to be aware of.</span></span> <span data-ttu-id="a8f73-111">通知部分通常以某种方式对事件作出反应。</span><span class="sxs-lookup"><span data-stu-id="a8f73-111">The notified parts usually react somehow to the events.</span></span>

<span data-ttu-id="a8f73-112">域事件的一个重要优势是可以显式表示副作用。</span><span class="sxs-lookup"><span data-stu-id="a8f73-112">An important benefit of domain events is that side effects can be expressed explicitly.</span></span>

<span data-ttu-id="a8f73-113">例如，如果只使用实体框架，并且必须对某个事件作出反应，则可能会对需要向触发事件的内容关闭的任何内容进行编码。</span><span class="sxs-lookup"><span data-stu-id="a8f73-113">For example, if you're just using Entity Framework and there has to be a reaction to some event, you would probably code whatever you need close to what triggers the event.</span></span> <span data-ttu-id="a8f73-114">因此规则会隐式地关联到代码，需要查看代码才有希望认识到在其中实现了规则。</span><span class="sxs-lookup"><span data-stu-id="a8f73-114">So the rule gets coupled, implicitly, to the code, and you have to look into the code to, hopefully, realize the rule is implemented there.</span></span>

<span data-ttu-id="a8f73-115">另一方面，使用域事件会使概念明确，因为会涉及到 `DomainEvent` 以及至少一个 `DomainEventHandler`。</span><span class="sxs-lookup"><span data-stu-id="a8f73-115">On the other hand, using domain events makes the concept explicit, because there is a `DomainEvent` and at least one `DomainEventHandler` involved.</span></span>

<span data-ttu-id="a8f73-116">例如在 eShopOnContainers 应用程序中，当创建订单时，用户会成为买家，因此 `OrderStartedDomainEvent` 会被引发并在 `ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler` 中进行处理，这样基础概念便十分明显。</span><span class="sxs-lookup"><span data-stu-id="a8f73-116">For example, in the eShopOnContainers application, when an order is created, the user becomes a buyer, so an `OrderStartedDomainEvent` is raised and handled in the `ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler`, so the underlying concept is evident.</span></span>

<span data-ttu-id="a8f73-117">简言之，域事件可帮助根据域专家提供的通用语言显式表示域规则。</span><span class="sxs-lookup"><span data-stu-id="a8f73-117">In short, domain events help you to express, explicitly, the domain rules, based in the ubiquitous language provided by the domain experts.</span></span> <span data-ttu-id="a8f73-118">通过域事件还可更好地在相同域中的类之间分离关注点。</span><span class="sxs-lookup"><span data-stu-id="a8f73-118">Domain events also enable a better separation of concerns among classes within the same domain.</span></span>

<span data-ttu-id="a8f73-119">请务必确保与域事件相关的所有操作都成功完成，或是都未成功完成，正如数据库事务一样。</span><span class="sxs-lookup"><span data-stu-id="a8f73-119">It's important to ensure that, just like a database transaction, either all the operations related to a domain event finish successfully or none of them do.</span></span>

<span data-ttu-id="a8f73-120">域事件类似于消息样式事件，但有一个重要的区别。</span><span class="sxs-lookup"><span data-stu-id="a8f73-120">Domain events are similar to messaging-style events, with one important difference.</span></span> <span data-ttu-id="a8f73-121">对于真正的消息传送、消息队列、消息中转站或使用 AMQP 的服务总线，消息始终异步发送，并跨进程和计算机传达。</span><span class="sxs-lookup"><span data-stu-id="a8f73-121">With real messaging, message queuing, message brokers, or a service bus using AMQP, a message is always sent asynchronously and communicated across processes and machines.</span></span> <span data-ttu-id="a8f73-122">这对于集成多个绑定上下文、微服务或不同应用程序很有用。</span><span class="sxs-lookup"><span data-stu-id="a8f73-122">This is useful for integrating multiple Bounded Contexts, microservices, or even different applications.</span></span> <span data-ttu-id="a8f73-123">但是，对于域事件，需要从当前运行的域操作引发事件，但需要在相同的域中发生副作用。</span><span class="sxs-lookup"><span data-stu-id="a8f73-123">However, with domain events, you want to raise an event from the domain operation you are currently running, but you want any side effects to occur within the same domain.</span></span>

<span data-ttu-id="a8f73-124">域事件和副作用（过后触发的操作，由事件处理程序管理）应几乎立即发生，通常在进程内或在相同的域中。</span><span class="sxs-lookup"><span data-stu-id="a8f73-124">The domain events and their side effects (the actions triggered afterwards that are managed by event handlers) should occur almost immediately, usually in-process, and within the same domain.</span></span> <span data-ttu-id="a8f73-125">因此，域事件可以是同步或异步。</span><span class="sxs-lookup"><span data-stu-id="a8f73-125">Thus, domain events could be synchronous or asynchronous.</span></span> <span data-ttu-id="a8f73-126">但是集成事件应始终是异步。</span><span class="sxs-lookup"><span data-stu-id="a8f73-126">Integration events, however, should always be asynchronous.</span></span>

## <a name="domain-events-versus-integration-events"></a><span data-ttu-id="a8f73-127">域事件和集成事件</span><span class="sxs-lookup"><span data-stu-id="a8f73-127">Domain events versus integration events</span></span>

<span data-ttu-id="a8f73-128">从语义上看，域事件和集成事件是相同的：都是对已发生事件的通知。</span><span class="sxs-lookup"><span data-stu-id="a8f73-128">Semantically, domain and integration events are the same thing: notifications about something that just happened.</span></span> <span data-ttu-id="a8f73-129">但是，它们的实现必须不同。</span><span class="sxs-lookup"><span data-stu-id="a8f73-129">However, their implementation must be different.</span></span> <span data-ttu-id="a8f73-130">域事件是推送到域事件调度程序的消息，可基于 IoC 容器或任何其他方法作为内存中转存进程实现。</span><span class="sxs-lookup"><span data-stu-id="a8f73-130">Domain events are just messages pushed to a domain event dispatcher, which could be implemented as an in-memory mediator based on an IoC container or any other method.</span></span>

<span data-ttu-id="a8f73-131">但是，集成事件的目的是将已提交事务和更新传播到其他子系统，无论它们是其他微服务、绑定上下文，还是外部应用程序。</span><span class="sxs-lookup"><span data-stu-id="a8f73-131">On the other hand, the purpose of integration events is to propagate committed transactions and updates to additional subsystems, whether they are other microservices, Bounded Contexts or even external applications.</span></span> <span data-ttu-id="a8f73-132">因此，它们应仅在成功保存实体时发生，否则便会如同整个操作从未发生一样。</span><span class="sxs-lookup"><span data-stu-id="a8f73-132">Hence, they should occur only if the entity is successfully persisted, otherwise it's as if the entire operation never happened.</span></span>

<span data-ttu-id="a8f73-133">如前所述，集成事件必须基于多个微服务（其他绑定上下文）或外部系统/应用程序之间的异步通信。</span><span class="sxs-lookup"><span data-stu-id="a8f73-133">As mentioned before, integration events must be based on asynchronous communication between multiple microservices (other Bounded Contexts) or even external systems/applications.</span></span>

<span data-ttu-id="a8f73-134">因此，事件总线接口需要一些基础结构来实现远程服务之间的进程间和分布式通信。</span><span class="sxs-lookup"><span data-stu-id="a8f73-134">Thus, the event bus interface needs some infrastructure that allows inter-process and distributed communication between potentially remote services.</span></span> <span data-ttu-id="a8f73-135">可以基于商用服务总线、队列、作为邮箱的共享数据库或任何其他分布式和基于推送的消息传送系统。</span><span class="sxs-lookup"><span data-stu-id="a8f73-135">It can be based on a commercial service bus, queues, a shared database used as a mailbox, or any other distributed and ideally push based messaging system.</span></span>

## <a name="domain-events-as-a-preferred-way-to-trigger-side-effects-across-multiple-aggregates-within-the-same-domain"></a><span data-ttu-id="a8f73-136">域事件是在相同域中跨多个聚合触发副作用的首选方式</span><span class="sxs-lookup"><span data-stu-id="a8f73-136">Domain events as a preferred way to trigger side effects across multiple aggregates within the same domain</span></span>

<span data-ttu-id="a8f73-137">如果执行与一个聚合实例相关的命令需要其他域规则运行一个或多个其他聚合，应将这些副作用设计和实现为由域事件触发。</span><span class="sxs-lookup"><span data-stu-id="a8f73-137">If executing a command related to one aggregate instance requires additional domain rules to be run on one or more additional aggregates, you should design and implement those side effects to be triggered by domain events.</span></span> <span data-ttu-id="a8f73-138">如图 7-14 所示，这是一个最重要的用例之一，应将域事件用于在相同域模型中跨多个聚合传播状态更改。</span><span class="sxs-lookup"><span data-stu-id="a8f73-138">As shown in Figure 7-14, and as one of the most important use cases, a domain event should be used to propagate state changes across multiple aggregates within the same domain model.</span></span>

![向买家聚合显示域事件控制的关系图。](./media/domain-events-design-implementation/domain-model-ordering-microservice.png)

<span data-ttu-id="a8f73-140">**图 7-14**。</span><span class="sxs-lookup"><span data-stu-id="a8f73-140">**Figure 7-14**.</span></span> <span data-ttu-id="a8f73-141">域事件在相同域的多个聚合之间强制执行一致性</span><span class="sxs-lookup"><span data-stu-id="a8f73-141">Domain events to enforce consistency between multiple aggregates within the same domain</span></span>

<span data-ttu-id="a8f73-142">图 7-14 显示了域事件如何实现聚合之间的一致性。</span><span class="sxs-lookup"><span data-stu-id="a8f73-142">Figure 7-14 shows how consistency between aggregates is achieved by domain events.</span></span> <span data-ttu-id="a8f73-143">当用户发起订单时，订单聚合将发送 `OrderStarted` 域事件。</span><span class="sxs-lookup"><span data-stu-id="a8f73-143">When the user initiates an order, the Order Aggregate sends an `OrderStarted` domain event.</span></span> <span data-ttu-id="a8f73-144">OrderStarted 域事件基于标识微服务中的原始用户信息（包含 CreateOrder 命令中提供的信息），由买方聚合处理，以在订购微服务时创建买家对象。</span><span class="sxs-lookup"><span data-stu-id="a8f73-144">The OrderStarted domain event is handled by the Buyer Aggregate to create a Buyer object in the ordering microservice, based on the original user info from the identity microservice (with information provided in the CreateOrder command).</span></span>

<span data-ttu-id="a8f73-145">或者，可以使聚合根订阅由聚合（子实体）成员引发的事件。</span><span class="sxs-lookup"><span data-stu-id="a8f73-145">Alternately, you can have the aggregate root subscribed for events raised by members of its aggregates (child entities).</span></span> <span data-ttu-id="a8f73-146">例如，每个 OrderItem 子实体可以在项目价格高于特定金额，或产品项目金额过高时，引发事件。</span><span class="sxs-lookup"><span data-stu-id="a8f73-146">For instance, each OrderItem child entity can raise an event when the item price is higher than a specific amount, or when the product item amount is too high.</span></span> <span data-ttu-id="a8f73-147">然后，聚合根可以接收这些事件，并执行全局计算或聚合。</span><span class="sxs-lookup"><span data-stu-id="a8f73-147">The aggregate root can then receive those events and perform a global calculation or aggregation.</span></span>

<span data-ttu-id="a8f73-148">请注意，此基于事件的通信不会直接在聚合中实现，需要实现域事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="a8f73-148">It is important to understand that this event-based communication is not implemented directly within the aggregates; you need to implement domain event handlers.</span></span>

<span data-ttu-id="a8f73-149">处理域事件是一个应用程序问题。</span><span class="sxs-lookup"><span data-stu-id="a8f73-149">Handling the domain events is an application concern.</span></span> <span data-ttu-id="a8f73-150">域模型层应只关注域逻辑（域专家可理解的内容），而不应关注应用程序基础结构（如处理程序）和使用存储库的副作用持久性操作。</span><span class="sxs-lookup"><span data-stu-id="a8f73-150">The domain model layer should only focus on the domain logic—things that a domain expert would understand, not application infrastructure like handlers and side-effect persistence actions using repositories.</span></span> <span data-ttu-id="a8f73-151">因此，应用程序层级别是在引发域事件时应执行域事件处理程序触发操作的位置。</span><span class="sxs-lookup"><span data-stu-id="a8f73-151">Therefore, the application layer level is where you should have domain event handlers triggering actions when a domain event is raised.</span></span>

<span data-ttu-id="a8f73-152">域事件还可用于触发任意数量的应用程序操作，并且更重要的是，必须可在将来通过分离方式增加此数目。</span><span class="sxs-lookup"><span data-stu-id="a8f73-152">Domain events can also be used to trigger any number of application actions, and what is more important, must be open to increase that number in the future in a decoupled way.</span></span> <span data-ttu-id="a8f73-153">例如，发起订单时，可能需要发布域事件以将信息传播到其他聚合，或引发通知等应用程序操作。</span><span class="sxs-lookup"><span data-stu-id="a8f73-153">For instance, when the order is started, you might want to publish a domain event to propagate that info to other aggregates or even to raise application actions like notifications.</span></span>

<span data-ttu-id="a8f73-154">关键在于域事件发生时要执行的操作的可变数量。</span><span class="sxs-lookup"><span data-stu-id="a8f73-154">The key point is the open number of actions to be executed when a domain event occurs.</span></span> <span data-ttu-id="a8f73-155">最终，域中的操作和规则以及应用程序会发展。</span><span class="sxs-lookup"><span data-stu-id="a8f73-155">Eventually, the actions and rules in the domain and application will grow.</span></span> <span data-ttu-id="a8f73-156">事件发生时的复杂性或副作用操作的数量将增加，但如果代码被“固定”（即使用 `new` 创建特定对象），每当需要添加新操作时，还需要更改正在工作和经过测试的代码。</span><span class="sxs-lookup"><span data-stu-id="a8f73-156">The complexity or number of side-effect actions when something happens will grow, but if your code were coupled with "glue" (that is, creating specific objects with `new`), then every time you needed to add a new action you would also need to change working and tested code.</span></span>

<span data-ttu-id="a8f73-157">此更改可能会导致新 bug，而且此方法还会违背 [SOLID](https://en.wikipedia.org/wiki/SOLID) 的[开/闭原则](https://en.wikipedia.org/wiki/Open/closed_principle)。</span><span class="sxs-lookup"><span data-stu-id="a8f73-157">This change could result in new bugs and this approach also goes against the [Open/Closed principle](https://en.wikipedia.org/wiki/Open/closed_principle) from [SOLID](https://en.wikipedia.org/wiki/SOLID).</span></span> <span data-ttu-id="a8f73-158">不仅如此，协调操作的原始类将不断增加，这违背了[单一功能原则 (SRP)](https://en.wikipedia.org/wiki/Single_responsibility_principle)。</span><span class="sxs-lookup"><span data-stu-id="a8f73-158">Not only that, the original class that was orchestrating the operations would grow and grow, which goes against the [Single Responsibility Principle (SRP)](https://en.wikipedia.org/wiki/Single_responsibility_principle).</span></span>

<span data-ttu-id="a8f73-159">但是，如果使用域事件，可以通过使用以下方法分离功能来创建细化和分离的实现：</span><span class="sxs-lookup"><span data-stu-id="a8f73-159">On the other hand, if you use domain events, you can create a fine-grained and decoupled implementation by segregating responsibilities using this approach:</span></span>

1. <span data-ttu-id="a8f73-160">发送命令（例如，CreateOrder）。</span><span class="sxs-lookup"><span data-stu-id="a8f73-160">Send a command (for example, CreateOrder).</span></span>
2. <span data-ttu-id="a8f73-161">在命令处理程序中接收命令。</span><span class="sxs-lookup"><span data-stu-id="a8f73-161">Receive the command in a command handler.</span></span>
   - <span data-ttu-id="a8f73-162">执行单个聚合的事务。</span><span class="sxs-lookup"><span data-stu-id="a8f73-162">Execute a single aggregate's transaction.</span></span>
   - <span data-ttu-id="a8f73-163">（可选）引发副作用的域事件（例如 OrderStartedDomainEvent）。</span><span class="sxs-lookup"><span data-stu-id="a8f73-163">(Optional) Raise domain events for side effects (for example, OrderStartedDomainEvent).</span></span>
3. <span data-ttu-id="a8f73-164">处理域事件（在当前进程中），这些域事件会在多个聚合或应用程序操作中执行可变数量的副作用。</span><span class="sxs-lookup"><span data-stu-id="a8f73-164">Handle domain events (within the current process) that will execute an open number of side effects in multiple aggregates or application actions.</span></span> <span data-ttu-id="a8f73-165">例如：</span><span class="sxs-lookup"><span data-stu-id="a8f73-165">For example:</span></span>
   - <span data-ttu-id="a8f73-166">验证或创建购买者和付款方式。</span><span class="sxs-lookup"><span data-stu-id="a8f73-166">Verify or create buyer and payment method.</span></span>
   - <span data-ttu-id="a8f73-167">创建相关集成事件并将其发送到事件总线，以在微服务中传播状态，或触发外部操作，例如将电子邮件发送给购买者。</span><span class="sxs-lookup"><span data-stu-id="a8f73-167">Create and send a related integration event to the event bus to propagate states across microservices or trigger external actions like sending an email to the buyer.</span></span>
   - <span data-ttu-id="a8f73-168">处理其他副作用。</span><span class="sxs-lookup"><span data-stu-id="a8f73-168">Handle other side effects.</span></span>

<span data-ttu-id="a8f73-169">如图 7-15 所示，从同一域事件，可以处理与域中的其他聚合相关的多个操作，或处理需要在与集成事件和事件总线相关的微服务中执行的其他应用程序操作。</span><span class="sxs-lookup"><span data-stu-id="a8f73-169">As shown in Figure 7-15, starting from the same domain event, you can handle multiple actions related to other aggregates in the domain or additional application actions you need to perform across microservices connecting with integration events and the event bus.</span></span>

![显示域事件将数据传递到几个事件处理程序的关系图。](./media/domain-events-design-implementation/aggregate-domain-event-handlers.png)

<span data-ttu-id="a8f73-171">**图 7-15**。</span><span class="sxs-lookup"><span data-stu-id="a8f73-171">**Figure 7-15**.</span></span> <span data-ttu-id="a8f73-172">处理每个域的多个操作</span><span class="sxs-lookup"><span data-stu-id="a8f73-172">Handling multiple actions per domain</span></span>

<span data-ttu-id="a8f73-173">同一个域事件在应用层中可以有多个处理程序，一个处理程序可以解决聚合之间的一致性，另一个处理程序可以发布集成事件，以便其他微服务可以对它执行操作。</span><span class="sxs-lookup"><span data-stu-id="a8f73-173">There can be several handlers for the same domain event in the Application Layer, one handler can solve consistency between aggregates and another handler can publish an integration event, so other microservices can do something with it.</span></span> <span data-ttu-id="a8f73-174">事件处理程序通常在应用程序层中，因为会将存储库或应用程序 API 等基础结构对象用于微服务行为。</span><span class="sxs-lookup"><span data-stu-id="a8f73-174">The event handlers are typically in the application layer, because you will use infrastructure objects like repositories or an application API for the microservice's behavior.</span></span> <span data-ttu-id="a8f73-175">在此意义上，事件处理程序类似于命令处理程序，因此两者都在应用程序层中。</span><span class="sxs-lookup"><span data-stu-id="a8f73-175">In that sense, event handlers are similar to command handlers, so both are part of the application layer.</span></span> <span data-ttu-id="a8f73-176">两者的重要区别是命令应只处理一次。</span><span class="sxs-lookup"><span data-stu-id="a8f73-176">The important difference is that a command should be processed only once.</span></span> <span data-ttu-id="a8f73-177">域事件可处理零或 n 次，因为它可被多个接收方或事件处理程序接收，针对每个处理程序具有不同用途  。</span><span class="sxs-lookup"><span data-stu-id="a8f73-177">A domain event could be processed zero or *n* times, because it can be received by multiple receivers or event handlers with a different purpose for each handler.</span></span>

<span data-ttu-id="a8f73-178">借助每个域事件的可变数量的处理程序，可添加所需数量的域规则，而不会影响当前代码。</span><span class="sxs-lookup"><span data-stu-id="a8f73-178">Having an open number of handlers per domain event allows you to add as many domain rules as needed, without affecting  current code.</span></span> <span data-ttu-id="a8f73-179">例如，可以轻松地添加一些（或者甚至是一个）事件处理程序来实现以下业务规则：</span><span class="sxs-lookup"><span data-stu-id="a8f73-179">For instance, implementing the following business rule might be as easy as adding a few event handlers (or even just one):</span></span>

> <span data-ttu-id="a8f73-180">如果客户在商店购买的总金额（跨任意数量订单）超过 6,000 美元，则为每个新订单提供 10% 的折扣，并通过电子邮件告知客户将来订单的折扣。</span><span class="sxs-lookup"><span data-stu-id="a8f73-180">When the total amount purchased by a customer in the store, across any number of orders, exceeds $6,000, apply a 10% off discount to every new order and notify the customer with an email about that discount for future orders.</span></span>

## <a name="implement-domain-events"></a><span data-ttu-id="a8f73-181">实现域事件</span><span class="sxs-lookup"><span data-stu-id="a8f73-181">Implement domain events</span></span>

<span data-ttu-id="a8f73-182">在 C# 中，域事件只是数据保留结构或类（如 DTO），包含与域中发生的事件相关的所有信息，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="a8f73-182">In C#, a domain event is simply a data-holding structure or class, like a DTO, with all the information related to what just happened in the domain, as shown in the following example:</span></span>

```csharp
public class OrderStartedDomainEvent : INotification
{
    public string UserId { get; }
    public int CardTypeId { get; }
    public string CardNumber { get; }
    public string CardSecurityNumber { get; }
    public string CardHolderName { get; }
    public DateTime CardExpiration { get; }
    public Order Order { get; }

    public OrderStartedDomainEvent(Order order,
                                   int cardTypeId, string cardNumber,
                                   string cardSecurityNumber, string cardHolderName,
                                   DateTime cardExpiration)
    {
        Order = order;
        CardTypeId = cardTypeId;
        CardNumber = cardNumber;
        CardSecurityNumber = cardSecurityNumber;
        CardHolderName = cardHolderName;
        CardExpiration = cardExpiration;
    }
}
```

<span data-ttu-id="a8f73-183">这实质上是一个包含与 OrderStarted 事件相关的所有数据的类。</span><span class="sxs-lookup"><span data-stu-id="a8f73-183">This is essentially a class that holds all the data related to the OrderStarted event.</span></span>

<span data-ttu-id="a8f73-184">关于域的通用语言，由于事件在过去发生的，事件的类名称应使用过去时态谓词表示，如 OrderStartedDomainEvent 或 OrderShippedDomainEvent。</span><span class="sxs-lookup"><span data-stu-id="a8f73-184">In terms of the ubiquitous language of the domain, since an event is something that happened in the past, the class name of the event should be represented as a past-tense verb, like OrderStartedDomainEvent or OrderShippedDomainEvent.</span></span> <span data-ttu-id="a8f73-185">这是域事件在 eShopOnContainers 的订购微服务中的实现方式。</span><span class="sxs-lookup"><span data-stu-id="a8f73-185">That's how the domain event is implemented in the ordering microservice in eShopOnContainers.</span></span>

<span data-ttu-id="a8f73-186">如前文所述，事件的一个重要特性是：由于事件是在过去发生的，所以不应发生更改。</span><span class="sxs-lookup"><span data-stu-id="a8f73-186">As noted earlier, an important characteristic of events is that since an event is something that happened in the past, it should not change.</span></span> <span data-ttu-id="a8f73-187">因此，它必须是一个不可变的类。</span><span class="sxs-lookup"><span data-stu-id="a8f73-187">Therefore, it must be an immutable class.</span></span> <span data-ttu-id="a8f73-188">可以从上一个代码中看到，属性是只读的。</span><span class="sxs-lookup"><span data-stu-id="a8f73-188">You can see in the previous code that the properties are read-only.</span></span> <span data-ttu-id="a8f73-189">无法更新对象，只能在创建它时设置值。</span><span class="sxs-lookup"><span data-stu-id="a8f73-189">There's no way to update the object, you can only set values when you create it.</span></span>

<span data-ttu-id="a8f73-190">这里必须重点强调的是，如果域事件要使用需要序列化和反序列化事件对象的队列进行异步处理，则属性必须是“专用集”而不是只读，以便反序列化程序能够在出队列时分配值。</span><span class="sxs-lookup"><span data-stu-id="a8f73-190">It's important to highlight here that if domain events were to be handled asynchronously, using a queue that required serializing and deserializing the event objects, the properties would have to be "private set" instead of read-only, so the deserializer would be able to assign the values upon dequeuing.</span></span> <span data-ttu-id="a8f73-191">这不是订购微服务中的问题，因为域事件发布/订阅是使用 MediatR 同步实现的。</span><span class="sxs-lookup"><span data-stu-id="a8f73-191">This is not an issue in the Ordering microservice, as the domain event pub/sub is implemented synchronously using MediatR.</span></span>

### <a name="raise-domain-events"></a><span data-ttu-id="a8f73-192">引发域事件</span><span class="sxs-lookup"><span data-stu-id="a8f73-192">Raise domain events</span></span>

<span data-ttu-id="a8f73-193">下一个问题是如何引发域事件，使其到达相关的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="a8f73-193">The next question is how to raise a domain event so it reaches its related event handlers.</span></span> <span data-ttu-id="a8f73-194">可使用多个方法。</span><span class="sxs-lookup"><span data-stu-id="a8f73-194">You can use multiple approaches.</span></span>

<span data-ttu-id="a8f73-195">Udi Dahan 最初建议（例如在 [Domain Events – Take 2](https://udidahan.com/2008/08/25/domain-events-take-2/)（域事件 – Take 2）等一系列文章中）将静态类用于管理和引发事件。</span><span class="sxs-lookup"><span data-stu-id="a8f73-195">Udi Dahan originally proposed (for example, in several related posts, such as [Domain Events – Take 2](https://udidahan.com/2008/08/25/domain-events-take-2/)) using a static class for managing and raising the events.</span></span> <span data-ttu-id="a8f73-196">这可能包括名为 DomainEvents 的静态类，该类会在调用时，使用 `DomainEvents.Raise(Event myEvent)` 等语法立即引发域事件。</span><span class="sxs-lookup"><span data-stu-id="a8f73-196">This might include a static class named DomainEvents that would raise domain events immediately when it is called, using syntax like `DomainEvents.Raise(Event myEvent)`.</span></span> <span data-ttu-id="a8f73-197">Jimmy Bogard 写了过一篇博客文章（[强化你的域：域事件](https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/)），其中建议了类似的方法。</span><span class="sxs-lookup"><span data-stu-id="a8f73-197">Jimmy Bogard wrote a blog post ([Strengthening your domain: Domain Events](https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/)) that recommends a similar approach.</span></span>

<span data-ttu-id="a8f73-198">但是，如果域事件类是静态的，它也会立即调度给处理程序。</span><span class="sxs-lookup"><span data-stu-id="a8f73-198">However, when the domain events class is static, it also dispatches to handlers immediately.</span></span> <span data-ttu-id="a8f73-199">这使得测试和调试更加困难，因为会在引发事件后立即执行具有副作用逻辑的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="a8f73-199">This makes testing and debugging more difficult, because the event handlers with side-effects logic are executed immediately after the event is raised.</span></span> <span data-ttu-id="a8f73-200">测试和调试时，你只希望专注于当前聚合类发生的事件；不希望突然重定向到其他事件处理程序，处理与其他聚合或应用程序逻辑相关的副作用。</span><span class="sxs-lookup"><span data-stu-id="a8f73-200">When you are testing and debugging, you just want to focus on what is happening in the current aggregate classes; you do not want to suddenly be redirected to other event handlers for side effects related to other aggregates or application logic.</span></span> <span data-ttu-id="a8f73-201">因此，其他方法应运而生，下一节将进行介绍。</span><span class="sxs-lookup"><span data-stu-id="a8f73-201">This is why other approaches have evolved, as explained in the next section.</span></span>

#### <a name="the-deferred-approach-to-raise-and-dispatch-events"></a><span data-ttu-id="a8f73-202">用于引发和调度事件的延迟方法</span><span class="sxs-lookup"><span data-stu-id="a8f73-202">The deferred approach to raise and dispatch events</span></span>

<span data-ttu-id="a8f73-203">一个更好的方法是将域事件添加到集合，然后在提交事务之前或之后立即调度这些域事件（正如 EF 中的 SaveChanges），而不是立即调度到域事件处理程序    。</span><span class="sxs-lookup"><span data-stu-id="a8f73-203">Instead of dispatching to a domain event handler immediately, a better approach is to add the domain events to a collection and then to dispatch those domain events *right before* or *right* *after* committing the transaction (as with SaveChanges in EF).</span></span> <span data-ttu-id="a8f73-204">（Jimmy Bogard 的文章 [A better domain events pattern](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)（一个更好的域事件模式）中介绍了此方法。）</span><span class="sxs-lookup"><span data-stu-id="a8f73-204">(This approach was described by Jimmy Bogard in this post [A better domain events pattern](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/).)</span></span>

<span data-ttu-id="a8f73-205">确定要在提交事务之前还是之后立即发送域事件非常重要，因为这决定了是将副作用添加到相同事务，还是不同事务中。</span><span class="sxs-lookup"><span data-stu-id="a8f73-205">Deciding if you send the domain events right before or right after committing the transaction is important, since it determines whether you will include the side effects as part of the same transaction or in different transactions.</span></span> <span data-ttu-id="a8f73-206">如果是将副作用添加到不同事务，需要处理跨多个聚合的最终一致性。</span><span class="sxs-lookup"><span data-stu-id="a8f73-206">In the latter case, you need to deal with eventual consistency across multiple aggregates.</span></span> <span data-ttu-id="a8f73-207">下一节中将对此主题进行讨论。</span><span class="sxs-lookup"><span data-stu-id="a8f73-207">This topic is discussed in the next section.</span></span>

<span data-ttu-id="a8f73-208">eShopOnContainers 使用延迟方法。</span><span class="sxs-lookup"><span data-stu-id="a8f73-208">The deferred approach is what eShopOnContainers uses.</span></span> <span data-ttu-id="a8f73-209">首先，将实体中发生的事件添加到每个实体的集合或事件列表。</span><span class="sxs-lookup"><span data-stu-id="a8f73-209">First, you add the events happening in your entities into a collection or list of events per entity.</span></span> <span data-ttu-id="a8f73-210">此列表应属于实体对象（或最好属于基本实体类），如以下实体基类示例所示：</span><span class="sxs-lookup"><span data-stu-id="a8f73-210">That list should be part of the entity object, or even better, part of your base entity class, as shown in the following example of the Entity base class:</span></span>

```csharp
public abstract class Entity
{
     //...
     private List<INotification> _domainEvents;
     public List<INotification> DomainEvents => _domainEvents;

     public void AddDomainEvent(INotification eventItem)
     {
         _domainEvents = _domainEvents ?? new List<INotification>();
         _domainEvents.Add(eventItem);
     }

     public void RemoveDomainEvent(INotification eventItem)
     {
         _domainEvents?.Remove(eventItem);
     }
     //... Additional code
}
```

<span data-ttu-id="a8f73-211">要引发事件时，只需将其在聚合根实体的方法处添加到代码中的事件集合。</span><span class="sxs-lookup"><span data-stu-id="a8f73-211">When you want to raise an event, you just add it to the event collection from code at any method of the aggregate-root entity.</span></span>

<span data-ttu-id="a8f73-212">以下代码（属于 [eShopOnContainers 的订单聚合根](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs)）演示如下示例：</span><span class="sxs-lookup"><span data-stu-id="a8f73-212">The following code, part of the [Order aggregate-root at eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs), shows an example:</span></span>

```csharp
var orderStartedDomainEvent = new OrderStartedDomainEvent(this, //Order object
                                                          cardTypeId, cardNumber,
                                                          cardSecurityNumber,
                                                          cardHolderName,
                                                          cardExpiration);
this.AddDomainEvent(orderStartedDomainEvent);
```

<span data-ttu-id="a8f73-213">请注意 AddDomainEvent 方法的唯一功能是将事件添加到列表。</span><span class="sxs-lookup"><span data-stu-id="a8f73-213">Notice that the only thing that the AddDomainEvent method is doing is adding an event to the list.</span></span> <span data-ttu-id="a8f73-214">尚未调度任何事件，尚未调用任何事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="a8f73-214">No event is dispatched yet, and no event handler is invoked yet.</span></span>

<span data-ttu-id="a8f73-215">你需要在稍后将事务提交到数据库时调度事件。</span><span class="sxs-lookup"><span data-stu-id="a8f73-215">You actually want to dispatch the events later on, when you commit the transaction to the database.</span></span> <span data-ttu-id="a8f73-216">如果使用 Entity Framework Core，意味着在 EF DbContext 的 SaveChanges 方法中，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="a8f73-216">If you are using Entity Framework Core, that means in the SaveChanges method of your EF DbContext, as in the following code:</span></span>

```csharp
// EF Core DbContext
public class OrderingContext : DbContext, IUnitOfWork
{
    // ...
    public async Task<bool> SaveEntitiesAsync(CancellationToken cancellationToken = default(CancellationToken))
    {
        // Dispatch Domain Events collection.
        // Choices:
        // A) Right BEFORE committing data (EF SaveChanges) into the DB. This makes
        // a single transaction including side effects from the domain event
        // handlers that are using the same DbContext with Scope lifetime
        // B) Right AFTER committing data (EF SaveChanges) into the DB. This makes
        // multiple transactions. You will need to handle eventual consistency and
        // compensatory actions in case of failures.
        await _mediator.DispatchDomainEventsAsync(this);

        // After this line runs, all the changes (from the Command Handler and Domain
        // event handlers) performed through the DbContext will be committed
        var result = await base.SaveChangesAsync();
    }
}
```

<span data-ttu-id="a8f73-217">使用此代码可将实体事件调度到相应的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="a8f73-217">With this code, you dispatch the entity events to their respective event handlers.</span></span>

<span data-ttu-id="a8f73-218">总体结果是将域事件引用（简单添加到内存中列表）从调度到事件处理程序中分离。</span><span class="sxs-lookup"><span data-stu-id="a8f73-218">The overall result is that you have decoupled the raising of a domain event (a simple add into a list in memory) from dispatching it to an event handler.</span></span> <span data-ttu-id="a8f73-219">此外，可同步或异步调度事件，具体取决于你使用的调度程序。</span><span class="sxs-lookup"><span data-stu-id="a8f73-219">In addition, depending on what kind of dispatcher you are using, you could dispatch the events synchronously or asynchronously.</span></span>

<span data-ttu-id="a8f73-220">请注意事务边界在此时发挥巨大作用。</span><span class="sxs-lookup"><span data-stu-id="a8f73-220">Be aware that transactional boundaries come into significant play here.</span></span> <span data-ttu-id="a8f73-221">如果工作单元和事务可跨多个聚合（如使用 EF Core 和关系数据库时），这可正常运行。</span><span class="sxs-lookup"><span data-stu-id="a8f73-221">If your unit of work and transaction can span more than one aggregate (as when using EF Core and a relational database), this can work well.</span></span> <span data-ttu-id="a8f73-222">但是，如果事务不能跨聚合（例如使用 Azure CosmosDB 等 NoSQL 数据库时），必须执行额外步骤以实现一致性。</span><span class="sxs-lookup"><span data-stu-id="a8f73-222">But if the transaction cannot span aggregates, such as when you are using a NoSQL database like Azure CosmosDB, you have to implement additional steps to achieve consistency.</span></span> <span data-ttu-id="a8f73-223">这是持久性无感知不通用的另一个原因，它取决于你使用的存储系统。</span><span class="sxs-lookup"><span data-stu-id="a8f73-223">This is another reason why persistence ignorance is not universal; it depends on the storage system you use.</span></span>

### <a name="single-transaction-across-aggregates-versus-eventual-consistency-across-aggregates"></a><span data-ttu-id="a8f73-224">跨聚合的单个事务与跨聚合的最终一致性</span><span class="sxs-lookup"><span data-stu-id="a8f73-224">Single transaction across aggregates versus eventual consistency across aggregates</span></span>

<span data-ttu-id="a8f73-225">是跨聚合执行单个事务，还是依赖跨聚合的最终一致性，这一点存在争议。</span><span class="sxs-lookup"><span data-stu-id="a8f73-225">The question of whether to perform a single transaction across aggregates versus relying on eventual consistency across those aggregates is a controversial one.</span></span> <span data-ttu-id="a8f73-226">Eric Evans 和 Vaughn Vernon 等许多作者提倡遵循一个事务 = 一个聚合的规则，因此支持跨聚合的最终一致性。</span><span class="sxs-lookup"><span data-stu-id="a8f73-226">Many DDD authors like Eric Evans and Vaughn Vernon advocate the rule that one transaction = one aggregate and therefore argue for eventual consistency across aggregates.</span></span> <span data-ttu-id="a8f73-227">例如，Eric Evans 在他的著作《Domain-Driven Design》（域驱动的设计）中表示  ：</span><span class="sxs-lookup"><span data-stu-id="a8f73-227">For example, in his book *Domain-Driven Design*, Eric Evans says this:</span></span>

> <span data-ttu-id="a8f73-228">跨聚合的任何规则都不会始终保持最新状态。</span><span class="sxs-lookup"><span data-stu-id="a8f73-228">Any rule that spans Aggregates will not be expected to be up-to-date at all times.</span></span> <span data-ttu-id="a8f73-229">通过事件处理、批处理或其他更新机制，其他依赖项可在特定时间内解析。</span><span class="sxs-lookup"><span data-stu-id="a8f73-229">Through event processing, batch processing, or other update mechanisms, other dependencies can be resolved within some specific time.</span></span> <span data-ttu-id="a8f73-230">（第 128 页）</span><span class="sxs-lookup"><span data-stu-id="a8f73-230">(page 128)</span></span>

<span data-ttu-id="a8f73-231">Vaughn Vernon 在 [Effective Aggregate Design.第 II 部分：让聚合共同工作](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)：</span><span class="sxs-lookup"><span data-stu-id="a8f73-231">Vaughn Vernon says the following in [Effective Aggregate Design. Part II: Making Aggregates Work Together](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf):</span></span>

> <span data-ttu-id="a8f73-232">因此，如果在一个聚合实例上执行命令需要在一个或多个聚合上执行其他业务规则，则使用最终一致性。\[...\]有一个实用方法可在 DDD 模型中支持最终一致性。</span><span class="sxs-lookup"><span data-stu-id="a8f73-232">Thus, if executing a command on one aggregate instance requires that additional business rules execute on one or more aggregates, use eventual consistency \[...\] There is a practical way to support eventual consistency in a DDD model.</span></span> <span data-ttu-id="a8f73-233">聚合方法发布及时交付到一个或多个异步订阅服务器的域事件。</span><span class="sxs-lookup"><span data-stu-id="a8f73-233">An aggregate method publishes a domain event that is in time delivered to one or more asynchronous subscribers.</span></span>

<span data-ttu-id="a8f73-234">此观点基于接受细化事务，而不是跨多个聚合或实体的事务。</span><span class="sxs-lookup"><span data-stu-id="a8f73-234">This rationale is based on embracing fine-grained transactions instead of transactions spanning many aggregates or entities.</span></span> <span data-ttu-id="a8f73-235">原理是在第二种情况下，具有高可伸缩性要求的大规模应用程序的数据库锁定的数量巨大。</span><span class="sxs-lookup"><span data-stu-id="a8f73-235">The idea is that in the second case, the number of database locks will be substantial in large-scale applications with high scalability needs.</span></span> <span data-ttu-id="a8f73-236">接受高可伸缩性应用程序不需要多个聚合间的即时事务一致性的事实，有助于接受最终一致性的概念。</span><span class="sxs-lookup"><span data-stu-id="a8f73-236">Embracing the fact that highly scalable applications need not have instant transactional consistency between multiple aggregates helps with accepting the concept of eventual consistency.</span></span> <span data-ttu-id="a8f73-237">业务通常不需要原子更改，而且确定特定操作是否需要原子事务始终是域专家的职责。</span><span class="sxs-lookup"><span data-stu-id="a8f73-237">Atomic changes are often not needed by the business, and it is in any case the responsibility of the domain experts to say whether particular operations need atomic transactions or not.</span></span> <span data-ttu-id="a8f73-238">如果操作始终需要多个聚合间的原子事务，应考虑聚合是否应该更大，或是否未正确设计。</span><span class="sxs-lookup"><span data-stu-id="a8f73-238">If an operation always needs an atomic transaction between multiple aggregates, you might ask whether your aggregate should be larger or was not correctly designed.</span></span>

<span data-ttu-id="a8f73-239">但 Jimmy Bogard 等其他开发者和架构师赞成在多个聚合中跨越单个事务 - 但仅当这些额外聚合与相同原始命令的副作用相关时。</span><span class="sxs-lookup"><span data-stu-id="a8f73-239">However, other developers and architects like Jimmy Bogard are okay with spanning a single transaction across several aggregates—but only when those additional aggregates are related to side effects for the same original command.</span></span> <span data-ttu-id="a8f73-240">例如，在 [A better domain events pattern](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)（更好的域事件模式）中，Bogard 表示：</span><span class="sxs-lookup"><span data-stu-id="a8f73-240">For instance, in [A better domain events pattern](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/), Bogard says this:</span></span>

> <span data-ttu-id="a8f73-241">通常情况下，我希望域事件的副作用发生在相同的逻辑事务中，但不一定是在引发域事件的同一作用域 \[...\]在提交事务前，将事件调度到相应的处理程序。</span><span class="sxs-lookup"><span data-stu-id="a8f73-241">Typically, I want the side effects of a domain event to occur within the same logical transaction, but not necessarily in the same scope of raising the domain event \[...\] Just before we commit our transaction, we dispatch our events to their respective handlers.</span></span>

<span data-ttu-id="a8f73-242">如果在提交原始事务前调度域事件，这是因为希望在相同事务中添加这些事件的副作用  。</span><span class="sxs-lookup"><span data-stu-id="a8f73-242">If you dispatch the domain events right *before* committing the original transaction, it is because you want the side effects of those events to be included in the same transaction.</span></span> <span data-ttu-id="a8f73-243">例如，如果 EF DbContext SaveChanges 方法失败，事务会回退所有更改，包括由相关域事件处理程序实现的副作用操作。</span><span class="sxs-lookup"><span data-stu-id="a8f73-243">For example, if the EF DbContext SaveChanges method fails, the transaction will roll back all changes, including the result of any side effect operations implemented by the related domain event handlers.</span></span> <span data-ttu-id="a8f73-244">这是因为默认情况下 DbContext 生存范围定义为“已设置范围”。</span><span class="sxs-lookup"><span data-stu-id="a8f73-244">This is because the DbContext life scope is by default defined as "scoped."</span></span> <span data-ttu-id="a8f73-245">因此，DbContext 对象跨多个在相同范围或对象图中实例化的存储库对象共享。</span><span class="sxs-lookup"><span data-stu-id="a8f73-245">Therefore, the DbContext object is shared across multiple repository objects being instantiated within the same scope or object graph.</span></span> <span data-ttu-id="a8f73-246">在开发 Web API 或 MVC 应用时，这与 HttpRequest 范围一致。</span><span class="sxs-lookup"><span data-stu-id="a8f73-246">This coincides with the HttpRequest scope when developing Web API or MVC apps.</span></span>

<span data-ttu-id="a8f73-247">实际上，这两种方法（单个原子事务和最终一致性）都是正确的。</span><span class="sxs-lookup"><span data-stu-id="a8f73-247">Actually, both approaches (single atomic transaction and eventual consistency) can be right.</span></span> <span data-ttu-id="a8f73-248">实际上取决于你的域或业务要求，以及域专家的建议。</span><span class="sxs-lookup"><span data-stu-id="a8f73-248">It really depends on your domain or business requirements and what the domain experts tell you.</span></span> <span data-ttu-id="a8f73-249">它还取决于所需的服务可缩放性（事务越细化，对数据库锁定的影响越小）。</span><span class="sxs-lookup"><span data-stu-id="a8f73-249">It also depends on how scalable you need the service to be (more granular transactions have less impact with regard to database locks).</span></span> <span data-ttu-id="a8f73-250">它取决于你愿意在代码上进行的投资，由于最终一致性需要更复杂的代码以检测聚合中可能的不一致，且需要实现补偿操作。</span><span class="sxs-lookup"><span data-stu-id="a8f73-250">And it depends on how much investment you are willing to make in your code, since eventual consistency requires more complex code in order to detect possible inconsistencies across aggregates and the need to implement compensatory actions.</span></span> <span data-ttu-id="a8f73-251">请考虑以下情况：如果将更改提交到原始聚合，并且之后当调度事件时如果发生问题，事件处理程序无法提交副作用，则聚合之间将产生不一致。</span><span class="sxs-lookup"><span data-stu-id="a8f73-251">Consider that if you commit changes to the original aggregate and afterwards, when the events are being dispatched, if there is an issue and the event handlers cannot commit their side effects, you will have inconsistencies between aggregates.</span></span>

<span data-ttu-id="a8f73-252">若要执行补偿操作，可将域事件存储在其他数据库表格，使其属于原始事务。</span><span class="sxs-lookup"><span data-stu-id="a8f73-252">A way to allow compensatory actions would be to store the domain events in additional database tables so they can be part of the original transaction.</span></span> <span data-ttu-id="a8f73-253">然后，可通过批处理比较事件列表和聚合的当前状态，从而检测不一致并运行补偿操作。</span><span class="sxs-lookup"><span data-stu-id="a8f73-253">Afterwards, you could have a batch process that detects inconsistencies and runs compensatory actions by comparing the list of events with the current state of the aggregates.</span></span> <span data-ttu-id="a8f73-254">补偿操作属于复杂主题，需要你进行深度分析，包括与业务用户和域专家进行讨论。</span><span class="sxs-lookup"><span data-stu-id="a8f73-254">The compensatory actions are part of a complex topic that will require deep analysis from your side, which includes discussing it with the business user and domain experts.</span></span>

<span data-ttu-id="a8f73-255">在任何情况下，你可以选择所需的方法。</span><span class="sxs-lookup"><span data-stu-id="a8f73-255">In any case, you can choose the approach you need.</span></span> <span data-ttu-id="a8f73-256">但初始延迟方法（在提交前引发事件，从而使用单个事务）是使用 EF Core 和关系数据库时最简单的方法。</span><span class="sxs-lookup"><span data-stu-id="a8f73-256">But the initial deferred approach—raising the events before committing, so you use a single transaction—is the simplest approach when using EF Core and a relational database.</span></span> <span data-ttu-id="a8f73-257">该方法易于实现且在许多业务情景中有效。</span><span class="sxs-lookup"><span data-stu-id="a8f73-257">It is easier to implement and valid in many business cases.</span></span> <span data-ttu-id="a8f73-258">这也是 eShopOnContainers 的订购微服务中使用的方法。</span><span class="sxs-lookup"><span data-stu-id="a8f73-258">It is also the approach used in the ordering microservice in eShopOnContainers.</span></span>

<span data-ttu-id="a8f73-259">但如何将这些事件调度到相应的事件处理程序？</span><span class="sxs-lookup"><span data-stu-id="a8f73-259">But how do you actually dispatch those events to their respective event handlers?</span></span> <span data-ttu-id="a8f73-260">在上一个示例中看到的 `_mediator` 对象是什么？</span><span class="sxs-lookup"><span data-stu-id="a8f73-260">What's the `_mediator` object you see in the previous example?</span></span> <span data-ttu-id="a8f73-261">它与用于在事件与其事件处理程序之间映射的技术和项目有关。</span><span class="sxs-lookup"><span data-stu-id="a8f73-261">It has to do with the techniques and artifacts you use to map between events and their event handlers.</span></span>

### <a name="the-domain-event-dispatcher-mapping-from-events-to-event-handlers"></a><span data-ttu-id="a8f73-262">域事件调度程序：从事件映射到事件处理程序</span><span class="sxs-lookup"><span data-stu-id="a8f73-262">The domain event dispatcher: mapping from events to event handlers</span></span>

<span data-ttu-id="a8f73-263">可调度或发布事件后，需要用于发布事件的某种项目，以便每个相关处理程序可获取它，并基于该事件处理副作用。</span><span class="sxs-lookup"><span data-stu-id="a8f73-263">Once you're able to dispatch or publish the events, you need some kind of artifact that will publish the event, so that every related handler can get it and process side effects based on that event.</span></span>

<span data-ttu-id="a8f73-264">一种方法是使用真正的消息传送系统或事件总线，可能基于服务总线，而不是内存中事件。</span><span class="sxs-lookup"><span data-stu-id="a8f73-264">One approach is a real messaging system or even an event bus, possibly based on a service bus as opposed to in-memory events.</span></span> <span data-ttu-id="a8f73-265">但是，对于第一种情况，真正的消息传送可能对于处理域事件来说用力过猛，因为你只需要处理相同进程（即相同域和应用程序层）中的事件。</span><span class="sxs-lookup"><span data-stu-id="a8f73-265">However, for the first case, real messaging would be overkill for processing domain events, since you just need to process those events within the same process (that is, within the same domain and application layer).</span></span>

<span data-ttu-id="a8f73-266">将事件映射到多个事件处理程序的另一种方法是使用 IoC 容器中的类型注册，以便动态推断是否调度事件。</span><span class="sxs-lookup"><span data-stu-id="a8f73-266">Another way to map events to multiple event handlers is by using types registration in an IoC container so you can dynamically infer where to dispatch the events.</span></span> <span data-ttu-id="a8f73-267">换而言之，需要知道什么事件处理程序需要获得特定事件。</span><span class="sxs-lookup"><span data-stu-id="a8f73-267">In other words, you need to know what event handlers need to get a specific event.</span></span> <span data-ttu-id="a8f73-268">图 7-16 显示此方法的简化方法。</span><span class="sxs-lookup"><span data-stu-id="a8f73-268">Figure 7-16 shows a simplified approach for this approach.</span></span>

![显示域事件调度程序向相应处理程序发送事件的关系图。](./media/domain-events-design-implementation/domain-event-dispatcher.png)

<span data-ttu-id="a8f73-270">**图 7-16**。</span><span class="sxs-lookup"><span data-stu-id="a8f73-270">**Figure 7-16**.</span></span> <span data-ttu-id="a8f73-271">使用 IoC 的域事件调度程序</span><span class="sxs-lookup"><span data-stu-id="a8f73-271">Domain event dispatcher using IoC</span></span>

<span data-ttu-id="a8f73-272">可以构建所有联结和项目，自行实现此方法。</span><span class="sxs-lookup"><span data-stu-id="a8f73-272">You can build all the plumbing and artifacts to implement that approach by yourself.</span></span> <span data-ttu-id="a8f73-273">但是还可使用 [MediatR](https://github.com/jbogard/MediatR)（它实际上使用 IoC 容器）等可用库。</span><span class="sxs-lookup"><span data-stu-id="a8f73-273">However, you can also use available libraries like [MediatR](https://github.com/jbogard/MediatR) that uses your IoC container under the covers.</span></span> <span data-ttu-id="a8f73-274">因此，可以直接使用预定义的接口和转存进程对象的发布/调度方法。</span><span class="sxs-lookup"><span data-stu-id="a8f73-274">You can therefore directly use the predefined interfaces and the mediator object's publish/dispatch methods.</span></span>

<span data-ttu-id="a8f73-275">在代码中，首先需要在 IoC 容器中注册事件处理程序类型，如 [eShopOnContainers 订购服务](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/MediatorModule.cs)处的以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="a8f73-275">In code, you first need to register the event handler types in your IoC container, as shown in the following example at [eShopOnContainers Ordering microservice](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/MediatorModule.cs):</span></span>

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        // Other registrations ...
        // Register the DomainEventHandler classes (they implement IAsyncNotificationHandler<>)
        // in assembly holding the Domain Events
        builder.RegisterAssemblyTypes(typeof(ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler)
                                       .GetTypeInfo().Assembly)
                                         .AsClosedTypesOf(typeof(IAsyncNotificationHandler<>));
        // Other registrations ...
    }
}
```

<span data-ttu-id="a8f73-276">代码首先通过查找保留处理程序（使用 typeof(ValidateOrAddBuyerAggregateWhenXxxx)，但你可能已经选择任何其他事件处理程序来查找此程序集）的程序集，识别包含域事件处理程序的程序集。</span><span class="sxs-lookup"><span data-stu-id="a8f73-276">The code first identifies the assembly that contains the domain event handlers by locating the assembly that holds any of the handlers (using typeof(ValidateOrAddBuyerAggregateWhenXxxx), but you could have chosen any other event handler to locate the assembly).</span></span> <span data-ttu-id="a8f73-277">由于所有事件处理程序实现 IAsyncNotificationHandler 接口，代码仅搜索这些类型并注册所有事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="a8f73-277">Since all the event handlers implement the IAsyncNotificationHandler interface, the code then just searches for those types and registers all the event handlers.</span></span>

### <a name="how-to-subscribe-to-domain-events"></a><span data-ttu-id="a8f73-278">如何订阅域事件</span><span class="sxs-lookup"><span data-stu-id="a8f73-278">How to subscribe to domain events</span></span>

<span data-ttu-id="a8f73-279">使用 MediatR 时，每个事件处理程序必须使用 INotificationHandler 接口的通用参数上提供的事件类型，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="a8f73-279">When you use MediatR, each event handler must use an event type that is provided on the generic parameter of the INotificationHandler interface, as you can see in the following code:</span></span>

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
  : IAsyncNotificationHandler<OrderStartedDomainEvent>
```

<span data-ttu-id="a8f73-280">基于事件和事件处理程序之间的关系（可将其视为订阅），MediatR 项目可发现每个事件的所有事件处理程序并触发每个事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="a8f73-280">Based on the relationship between event and event handler, which can be considered the subscription, the MediatR artifact can discover all the event handlers for each event and trigger each one of those event handlers.</span></span>

### <a name="how-to-handle-domain-events"></a><span data-ttu-id="a8f73-281">如何处理域事件</span><span class="sxs-lookup"><span data-stu-id="a8f73-281">How to handle domain events</span></span>

<span data-ttu-id="a8f73-282">最后，事件处理程序通常实现使用基础结构存储库的应用程序层，以获取所需其他聚合并执行副作用域逻辑。</span><span class="sxs-lookup"><span data-stu-id="a8f73-282">Finally, the event handler usually implements application layer code that uses infrastructure repositories to obtain the required additional aggregates and to execute side-effect domain logic.</span></span> <span data-ttu-id="a8f73-283">以下[ eShopOnContainers 中的域事件处理程序代码](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/DomainEventHandlers/OrderStartedEvent/ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler.cs)演示实现示例。</span><span class="sxs-lookup"><span data-stu-id="a8f73-283">The following [domain event handler code at eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/DomainEventHandlers/OrderStartedEvent/ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler.cs), shows an implementation example.</span></span>

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
                   : INotificationHandler<OrderStartedDomainEvent>
{
    private readonly ILoggerFactory _logger;
    private readonly IBuyerRepository<Buyer> _buyerRepository;
    private readonly IIdentityService _identityService;

    public ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler(
        ILoggerFactory logger,
        IBuyerRepository<Buyer> buyerRepository,
        IIdentityService identityService)
    {
        // ...Parameter validations...
    }

    public async Task Handle(OrderStartedDomainEvent orderStartedEvent)
    {
        var cardTypeId = (orderStartedEvent.CardTypeId != 0) ? orderStartedEvent.CardTypeId : 1;
        var userGuid = _identityService.GetUserIdentity();
        var buyer = await _buyerRepository.FindAsync(userGuid);
        bool buyerOriginallyExisted = (buyer == null) ? false : true;

        if (!buyerOriginallyExisted)
        {
            buyer = new Buyer(userGuid);
        }

        buyer.VerifyOrAddPaymentMethod(cardTypeId,
                                       $"Payment Method on {DateTime.UtcNow}",
                                       orderStartedEvent.CardNumber,
                                       orderStartedEvent.CardSecurityNumber,
                                       orderStartedEvent.CardHolderName,
                                       orderStartedEvent.CardExpiration,
                                       orderStartedEvent.Order.Id);

        var buyerUpdated = buyerOriginallyExisted ? _buyerRepository.Update(buyer)
                                                                      : _buyerRepository.Add(buyer);

        await _buyerRepository.UnitOfWork
                .SaveEntitiesAsync();

        // Logging code using buyerUpdated info, etc.
    }
}
```

<span data-ttu-id="a8f73-284">前面的域事件处理程序代码被视为应用程序层代码，因为其使用基础结构存储库，如有关基础结构持久化层的下一节所述。</span><span class="sxs-lookup"><span data-stu-id="a8f73-284">The previous domain event handler code is considered application layer code because it uses infrastructure repositories, as explained in the next section on the infrastructure-persistence layer.</span></span> <span data-ttu-id="a8f73-285">事件处理程序还可以使用其他基础结构组件。</span><span class="sxs-lookup"><span data-stu-id="a8f73-285">Event handlers could also use other infrastructure components.</span></span>

#### <a name="domain-events-can-generate-integration-events-to-be-published-outside-of-the-microservice-boundaries"></a><span data-ttu-id="a8f73-286">域事件可以生成要在微服务边界之外发布的集成事件</span><span class="sxs-lookup"><span data-stu-id="a8f73-286">Domain events can generate integration events to be published outside of the microservice boundaries</span></span>

<span data-ttu-id="a8f73-287">最后，请注意，有时需要跨多个微服务传播事件。</span><span class="sxs-lookup"><span data-stu-id="a8f73-287">Finally, it's important to mention that you might sometimes want to propagate events across multiple microservices.</span></span> <span data-ttu-id="a8f73-288">该传播是集成事件，可通过特定域事件处理程序的事件总线发布它。</span><span class="sxs-lookup"><span data-stu-id="a8f73-288">That propagation is an integration event, and it could be published through an event bus from any specific domain event handler.</span></span>

## <a name="conclusions-on-domain-events"></a><span data-ttu-id="a8f73-289">域事件的结论</span><span class="sxs-lookup"><span data-stu-id="a8f73-289">Conclusions on domain events</span></span>

<span data-ttu-id="a8f73-290">如前文所述，使用域事件显式实现域中的更改的副作用。</span><span class="sxs-lookup"><span data-stu-id="a8f73-290">As stated, use domain events to explicitly implement side effects of changes within your domain.</span></span> <span data-ttu-id="a8f73-291">若要使用 DDD 术语表述，则是使用域事件跨一个或多个聚合显式实现副作用。</span><span class="sxs-lookup"><span data-stu-id="a8f73-291">To use DDD terminology, use domain events to explicitly implement side effects across one or multiple aggregates.</span></span> <span data-ttu-id="a8f73-292">此外，为了提高可伸缩性并减小对数据库锁定的影响，可在相同域的聚合之间使用最终一致性。</span><span class="sxs-lookup"><span data-stu-id="a8f73-292">Additionally, and for better scalability and less impact on database locks, use eventual consistency between aggregates within the same domain.</span></span>

<span data-ttu-id="a8f73-293">参考应用使用 [MediatR](https://github.com/jbogard/MediatR) 在单个事务中跨聚合同步传播域事件。</span><span class="sxs-lookup"><span data-stu-id="a8f73-293">The reference app uses [MediatR](https://github.com/jbogard/MediatR) to propagate domain events synchronously across aggregates, within a single transaction.</span></span> <span data-ttu-id="a8f73-294">但是，也可使用 [RabbitMQ](https://www.rabbitmq.com/) 或 [Azure 服务总线](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)等一些 AMQP 实现来异步传播域事件，从而运用最终一致性，但如上所述，必须考虑到失败时要执行补偿操作的需求。</span><span class="sxs-lookup"><span data-stu-id="a8f73-294">However, you could also use some AMQP implementation like [RabbitMQ](https://www.rabbitmq.com/) or [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview) to propagate domain events asynchronously, using eventual consistency but, as mentioned above, you have to consider the need for compensatory actions in case of failures.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="a8f73-295">其他资源</span><span class="sxs-lookup"><span data-stu-id="a8f73-295">Additional resources</span></span>

- <span data-ttu-id="a8f73-296">**Greg Young.What is a Domain Event?** （什么是域事件？）</span><span class="sxs-lookup"><span data-stu-id="a8f73-296">**Greg Young. What is a Domain Event?**</span></span> \
  <https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf#page=25>

- <span data-ttu-id="a8f73-297">**Jan Stenberg。Domain Events and Eventual Consistency** （域事件和最终一致性） </span><span class="sxs-lookup"><span data-stu-id="a8f73-297">**Jan Stenberg. Domain Events and Eventual Consistency** </span></span>\
  <https://www.infoq.com/news/2015/09/domain-events-consistency>

- <span data-ttu-id="a8f73-298">**Jimmy Bogard。A better domain events pattern** （更好的域事件模式） </span><span class="sxs-lookup"><span data-stu-id="a8f73-298">**Jimmy Bogard. A better domain events pattern** </span></span>\
  <https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/>

- <span data-ttu-id="a8f73-299">**Vaughn Vernon。有效聚合设计，第 II 部分：让聚合共同工作** </span><span class="sxs-lookup"><span data-stu-id="a8f73-299">**Vaughn Vernon. Effective Aggregate Design Part II: Making Aggregates Work Together** </span></span>\
  [https://dddcommunity.org/wp-content/uploads/files/pdf\_articles/Vernon\_2011\_2.pdf](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)

- <span data-ttu-id="a8f73-300">**Jimmy Bogard。强化域：域事件** </span><span class="sxs-lookup"><span data-stu-id="a8f73-300">**Jimmy Bogard. Strengthening your domain: Domain Events** </span></span>\
  <https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/>

- <span data-ttu-id="a8f73-301">**Tony Truong。Domain Events Pattern Example** （域事件模式示例） </span><span class="sxs-lookup"><span data-stu-id="a8f73-301">**Tony Truong. Domain Events Pattern Example** </span></span>\
  <https://www.tonytruong.net/domain-events-pattern-example/>

- <span data-ttu-id="a8f73-302">**Udi Dahan.How to create fully encapsulated Domain Models** （如何创建完全封装的域模型） </span><span class="sxs-lookup"><span data-stu-id="a8f73-302">**Udi Dahan. How to create fully encapsulated Domain Models** </span></span>\
  <https://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/>

- <span data-ttu-id="a8f73-303">**Udi Dahan.Domain Events – Take 2** （域事件 – 搞定两个问题） </span><span class="sxs-lookup"><span data-stu-id="a8f73-303">**Udi Dahan. Domain Events – Take 2** </span></span>\
  <https://udidahan.com/2008/08/25/domain-events-take-2/>

- <span data-ttu-id="a8f73-304">**Udi Dahan.Domain Events – Salvation** （域事件 – 救助） </span><span class="sxs-lookup"><span data-stu-id="a8f73-304">**Udi Dahan. Domain Events – Salvation** </span></span>\
  <https://udidahan.com/2009/06/14/domain-events-salvation/>

- <span data-ttu-id="a8f73-305">**Jan Kronquist。Don't publish Domain Events, return them!** （不要发布域事件，返回它们！）</span><span class="sxs-lookup"><span data-stu-id="a8f73-305">**Jan Kronquist. Don't publish Domain Events, return them!**</span></span> \
  <https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/>

- <span data-ttu-id="a8f73-306">**Cesar de la Torre。Domain Events vs.Integration Events in DDD and microservices architectures** （DDD 和微服务体系结构中的域事件和集成事件） </span><span class="sxs-lookup"><span data-stu-id="a8f73-306">**Cesar de la Torre. Domain Events vs. Integration Events in DDD and microservices architectures** </span></span>\
  <https://devblogs.microsoft.com/cesardelatorre/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/>

>[!div class="step-by-step"]
><span data-ttu-id="a8f73-307">[上一页](client-side-validation.md)
>[下一页](infrastructure-persistence-layer-design.md)</span><span class="sxs-lookup"><span data-stu-id="a8f73-307">[Previous](client-side-validation.md)
[Next](infrastructure-persistence-layer-design.md)</span></span>

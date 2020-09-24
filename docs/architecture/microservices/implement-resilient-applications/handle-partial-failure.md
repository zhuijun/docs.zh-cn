---
title: 处理部分失败错误
description: 了解如何妥善处理部分失败错误。 微服务可能无法完全正常运行，但仍可以执行一些有用的工作。
ms.date: 10/16/2018
ms.openlocfilehash: 3345fffe3a38b8336d71ebb9c88e76d3315fd2e2
ms.sourcegitcommit: a8730298170b8d96b4272e0c3dfc9819c606947b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90738757"
---
# <a name="handle-partial-failure"></a><span data-ttu-id="e45af-104">处理部分失败错误</span><span class="sxs-lookup"><span data-stu-id="e45af-104">Handle partial failure</span></span>

<span data-ttu-id="e45af-105">在基于微服务的应用程序这类分布式系统中，经常会出现部分失败错误。</span><span class="sxs-lookup"><span data-stu-id="e45af-105">In distributed systems like microservices-based applications, there's an ever-present risk of partial failure.</span></span> <span data-ttu-id="e45af-106">例如，单个微服务/容器可能会失败，也可能无法在短时间响应，或者单个 VM 或服务器会出现故障。</span><span class="sxs-lookup"><span data-stu-id="e45af-106">For instance, a single microservice/container can fail or might not be available to respond for a short time, or a single VM or server can crash.</span></span> <span data-ttu-id="e45af-107">由于客户端和服务是彼此独立的流程，因此服务可能无法及时响应客户端的请求。</span><span class="sxs-lookup"><span data-stu-id="e45af-107">Since clients and services are separate processes, a service might not be able to respond in a timely way to a client's request.</span></span> <span data-ttu-id="e45af-108">服务可能过载并且对请求的响应速度过慢，或者只是由于网络问题在短时间内无法访问。</span><span class="sxs-lookup"><span data-stu-id="e45af-108">The service might be overloaded and responding very slowly to requests or might simply not be accessible for a short time because of network issues.</span></span>

<span data-ttu-id="e45af-109">例如，请查看 eShopOnContainers 示例应用程序的订单详细信息页。</span><span class="sxs-lookup"><span data-stu-id="e45af-109">For example, consider the Order details page from the eShopOnContainers sample application.</span></span> <span data-ttu-id="e45af-110">如果订购微服务在用户尝试提交订单时没有响应，则客户端进程（MVC Web 应用程序）的错误实现（例如，如果客户端代码使用同步 RPC 而没有出现超时）将会无限期地阻止线程等待回应。</span><span class="sxs-lookup"><span data-stu-id="e45af-110">If the ordering microservice is unresponsive when the user tries to submit an order, a bad implementation of the client process (the MVC web application)—for example, if the client code were to use synchronous RPCs with no timeout—would block threads indefinitely waiting for a response.</span></span> <span data-ttu-id="e45af-111">每个无响应的等待除了会造成不良用户体验之外，还会消耗或阻止线程，然而线程在高度可缩放应用程序中极有价值。</span><span class="sxs-lookup"><span data-stu-id="e45af-111">Besides creating a bad user experience, every unresponsive wait consumes or blocks a thread, and threads are extremely valuable in highly scalable applications.</span></span> <span data-ttu-id="e45af-112">如果受阻止的线程数量众多，应用程序的运行时最终会耗尽所有线程。</span><span class="sxs-lookup"><span data-stu-id="e45af-112">If there are many blocked threads, eventually the application's runtime can run out of threads.</span></span> <span data-ttu-id="e45af-113">在这种情况下，应用程序会出现全局无响应，而不只是部分无响应，如图 8-1 中所示。</span><span class="sxs-lookup"><span data-stu-id="e45af-113">In that case, the application can become globally unresponsive instead of just partially unresponsive, as shown in Figure 8-1.</span></span>

![显示部分失败的关系图。](./media/handle-partial-failure/partial-failures-diagram.png)

<span data-ttu-id="e45af-115">**图 8-1**。</span><span class="sxs-lookup"><span data-stu-id="e45af-115">**Figure 8-1**.</span></span> <span data-ttu-id="e45af-116">因依赖性影响服务线程可用性而出现的部分失败错误</span><span class="sxs-lookup"><span data-stu-id="e45af-116">Partial failures because of dependencies that impact service thread availability</span></span>

<span data-ttu-id="e45af-117">在基于微服务的大型应用程序中，任何部分失败错误都可能被放大，尤其是在大多数内部微服务交互都基于同步 HTTP 调用的情况下（这种情况被视为反模式）。</span><span class="sxs-lookup"><span data-stu-id="e45af-117">In a large microservices-based application, any partial failure can be amplified, especially if most of the internal microservices interaction is based on synchronous HTTP calls (which is considered an anti-pattern).</span></span> <span data-ttu-id="e45af-118">想想一个每天接收上百万传入调用的系统。</span><span class="sxs-lookup"><span data-stu-id="e45af-118">Think about a system that receives millions of incoming calls per day.</span></span> <span data-ttu-id="e45af-119">如果系统采用基于同步 HTTP 调用长链的不当设计，那么这些传入调用可能会再产生数百万对数十个内部微服务的传出调用（假设比例为 1:4）作为同步依赖项。</span><span class="sxs-lookup"><span data-stu-id="e45af-119">If your system has a bad design that's based on long chains of synchronous HTTP calls, these incoming calls might result in many more millions of outgoing calls (let's suppose a ratio of 1:4) to dozens of internal microservices as synchronous dependencies.</span></span> <span data-ttu-id="e45af-120">图 8-2 中显示了这种情况，尤其是依赖项 \#3，它启动链，调用依赖项 #4，该依赖项又调用 #5。</span><span class="sxs-lookup"><span data-stu-id="e45af-120">This situation is shown in Figure 8-2, especially dependency \#3, that starts a chain, calling dependency #4, which then calls #5.</span></span>

![显示多个分布式依赖项的关系图。](./media/handle-partial-failure/multiple-distributed-dependencies.png)

<span data-ttu-id="e45af-122">**图 8-2**。</span><span class="sxs-lookup"><span data-stu-id="e45af-122">**Figure 8-2**.</span></span> <span data-ttu-id="e45af-123">采用 HTTP 请求长链的不当设计所产生的影响</span><span class="sxs-lookup"><span data-stu-id="e45af-123">The impact of having an incorrect design featuring long chains of HTTP requests</span></span>

<span data-ttu-id="e45af-124">即使每个依赖项本身都具有卓越的可用性，在分布式和基于云的系统中也一定会出现间歇性故障。</span><span class="sxs-lookup"><span data-stu-id="e45af-124">Intermittent failure is guaranteed in a distributed and cloud-based system, even if every dependency itself has excellent availability.</span></span> <span data-ttu-id="e45af-125">这是需要考虑的事实。</span><span class="sxs-lookup"><span data-stu-id="e45af-125">It's a fact you need to consider.</span></span>

<span data-ttu-id="e45af-126">如果不设计和实现能保证容错的技术，那么即使是很短的故障时间也会被放大。</span><span class="sxs-lookup"><span data-stu-id="e45af-126">If you do not design and implement techniques to ensure fault tolerance, even small downtimes can be amplified.</span></span> <span data-ttu-id="e45af-127">例如，50 个依赖项，每个具有 99.99% 的可用性，因为这种连锁效应，每个月会产生几个小时的故障时间。</span><span class="sxs-lookup"><span data-stu-id="e45af-127">As an example, 50 dependencies each with 99.99% of availability would result in several hours of downtime each month because of this ripple effect.</span></span> <span data-ttu-id="e45af-128">如果微服务依赖项在处理大量请求时出现失败错误，那么该失败错误可能会迅速蔓延到每个服务中的所有可用请求线程，然后导致整个应用程序出现故障。</span><span class="sxs-lookup"><span data-stu-id="e45af-128">When a microservice dependency fails while handling a high volume of requests, that failure can quickly saturate all available request threads in each service and crash the whole application.</span></span>

![显示微服务中放大的部分失败的关系图。](./media/handle-partial-failure/partial-failure-amplified-microservices.png)

<span data-ttu-id="e45af-130">**图 8-3**。</span><span class="sxs-lookup"><span data-stu-id="e45af-130">**Figure 8-3**.</span></span> <span data-ttu-id="e45af-131">由微服务使用同步 HTTP 调用长链放大的部分失败错误</span><span class="sxs-lookup"><span data-stu-id="e45af-131">Partial failure amplified by microservices with long chains of synchronous HTTP calls</span></span>

<span data-ttu-id="e45af-132">为最大程度地减少此问题，在此指南的[异步微服务集成强制实现微服务自治性](../architect-microservice-container-applications/communication-in-microservice-architecture.md#asynchronous-microservice-integration-enforces-microservices-autonomy)部分中，建议在内部微服务间使用异步通信。</span><span class="sxs-lookup"><span data-stu-id="e45af-132">To minimize this problem, in the section [Asynchronous microservice integration enforce microservice's autonomy](../architect-microservice-container-applications/communication-in-microservice-architecture.md#asynchronous-microservice-integration-enforces-microservices-autonomy), this guide encourages you to use asynchronous communication across the internal microservices.</span></span>

<span data-ttu-id="e45af-133">此外，必须要设计可处理部分失败错误的微服务和客户端应用程序 - 即构建复原微服务和客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="e45af-133">In addition, it's essential that you design your microservices and client applications to handle partial failures—that is, to build resilient microservices and client applications.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e45af-134">[上一页](index.md)
>[下一页](partial-failure-strategies.md)</span><span class="sxs-lookup"><span data-stu-id="e45af-134">[Previous](index.md)
[Next](partial-failure-strategies.md)</span></span>

---
title: 生成适用于云的可复原服务。 在云中处理暂时性故障
description: 通过 Azure 云和 Windows 容器现代化现有 .NET 应用程序 | 生成适用于云的可复原服务。 在云中处理暂时性故障
ms.date: 04/30/2018
ms.openlocfilehash: 8e9f1eda71e4b98a56cbfc1c7a4ff34e67bee3f4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172152"
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a><span data-ttu-id="23962-105">生成适用于云的可复原服务：在云中处理暂时性故障</span><span class="sxs-lookup"><span data-stu-id="23962-105">Build resilient services ready for the cloud: Embrace transient failures in the cloud</span></span>

<span data-ttu-id="23962-106">恢复能力是指从故障中恢复并继续工作的能力。</span><span class="sxs-lookup"><span data-stu-id="23962-106">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="23962-107">复原能力并不是指避免故障，而是接受会发生故障这一事实，然后以能够避免停机或数据丢失的方式对故障做出响应。</span><span class="sxs-lookup"><span data-stu-id="23962-107">Resiliency is not about avoiding failures, but accepting the fact that failures will occur, and then responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="23962-108">恢复的目标是使应用程序在发生故障后回到完全正常运行的状态。</span><span class="sxs-lookup"><span data-stu-id="23962-108">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="23962-109">当你的应用程序至少实现了基于软件的复原能力模型（而不是基于硬件的模型）时，你的应用程序即处于云就绪状态。</span><span class="sxs-lookup"><span data-stu-id="23962-109">Your application is ready for the cloud when, at a minimum, it implements a software-based model of resiliency, rather than a hardware-based model.</span></span> <span data-ttu-id="23962-110">你的云应用程序必须接受将会出现的部分故障。</span><span class="sxs-lookup"><span data-stu-id="23962-110">Your cloud application must embrace the partial failures that will certainly occur.</span></span> <span data-ttu-id="23962-111">设计或部分重构你的应用程序，以实现预期部分故障的复原能力。</span><span class="sxs-lookup"><span data-stu-id="23962-111">Design or partially refactor your application to achieve resiliency with expected partial failures.</span></span> <span data-ttu-id="23962-112">应将其设计为能够处理部分故障，如短暂的网络中断或者云中的节点或 VM 故障。</span><span class="sxs-lookup"><span data-stu-id="23962-112">It should be designed to cope with partial failures, like transient network outages and nodes, or VMs crashing in the cloud.</span></span> <span data-ttu-id="23962-113">甚至将容器移动到业务流程协调程序群集内的另一个节点，也可能导致应用程序出现间歇性的功能短缺故障。</span><span class="sxs-lookup"><span data-stu-id="23962-113">Even containers being moved to a different node within an orchestrator cluster can cause intermittent short failures within the application.</span></span>

## <a name="handling-partial-failure"></a><span data-ttu-id="23962-114">处理部分失败错误</span><span class="sxs-lookup"><span data-stu-id="23962-114">Handling partial failure</span></span>

<span data-ttu-id="23962-115">在基于云的应用程序中，存在部分故障的现有风险。</span><span class="sxs-lookup"><span data-stu-id="23962-115">In a cloud-based application, there's an ever-present risk of partial failure.</span></span> <span data-ttu-id="23962-116">例如，单个网站实例或容器可能出现故障，或者它可能短时间不可用或没有响应。</span><span class="sxs-lookup"><span data-stu-id="23962-116">For instance, a single website instance or a container might fail, or it might be unavailable or unresponsive for a short time.</span></span> <span data-ttu-id="23962-117">或者，单个 VM 或服务器可能会出现故障。</span><span class="sxs-lookup"><span data-stu-id="23962-117">Or, a single VM or server might crash.</span></span>

<span data-ttu-id="23962-118">由于客户端和服务是彼此独立的流程，因此服务可能无法及时响应客户端的请求。</span><span class="sxs-lookup"><span data-stu-id="23962-118">Because clients and services are separate processes, a service might not be able to respond in a timely manner to a client's request.</span></span> <span data-ttu-id="23962-119">服务可能过载并且对请求的响应速度慢，或者由于网络问题在短时间内无法访问。</span><span class="sxs-lookup"><span data-stu-id="23962-119">The service might be overloaded and respond slowly to requests, or it might not be accessible for a short time because of network issues.</span></span>

<span data-ttu-id="23962-120">例如，假设有一个在 Azure SQL 数据库中访问数据库的整体式 .NET 应用程序。</span><span class="sxs-lookup"><span data-stu-id="23962-120">For example, consider a monolithic .NET application that accesses a database in Azure SQL Database.</span></span> <span data-ttu-id="23962-121">如果 Azure SQL 数据库或任何其他第三方服务短时间内没有响应（Azure SQL 数据库可能移动到另一个节点或服务器，在几秒钟内无响应），则当用户尝试执行任何操作时，应用程序可能会出现故障并同时显示异常。</span><span class="sxs-lookup"><span data-stu-id="23962-121">If the Azure SQL database or any other third-party service is unresponsive for a brief time (an Azure SQL database might be moved to a different node or server, and be unresponsive for a few seconds), when the user tries to do any action, the application might crash and show an exception at the same moment.</span></span>

<span data-ttu-id="23962-122">使用 HTTP 服务的应用可能会出现类似的情况。</span><span class="sxs-lookup"><span data-stu-id="23962-122">A similar scenario might occur in an app that consumes HTTP services.</span></span> <span data-ttu-id="23962-123">在出现短暂的暂时性故障时，网络或服务本身可能无法在云中使用。</span><span class="sxs-lookup"><span data-stu-id="23962-123">The network or the service itself might not be available in the cloud during a short, transient failure.</span></span>

<span data-ttu-id="23962-124">如图 4-9 中所示的可复原应用程序应该实现“以指数回退方式重试”之类的技术，使应用程序有机会处理资源的暂时性故障。</span><span class="sxs-lookup"><span data-stu-id="23962-124">A resilient application like the one shown in Figure 4-9 should implement techniques like "retries with exponential backoff" to give the application an opportunity to handle transient failures in resources.</span></span> <span data-ttu-id="23962-125">你还应在应用程序中使用“断路器”。</span><span class="sxs-lookup"><span data-stu-id="23962-125">You also should use "circuit breakers" in your applications.</span></span> <span data-ttu-id="23962-126">当实际上是长期故障时，断路器会阻止该应用程序尝试访问该资源。</span><span class="sxs-lookup"><span data-stu-id="23962-126">A circuit breaker stops an application from trying to access a resource when it's actually a long-term failure.</span></span> <span data-ttu-id="23962-127">通过使用断路器，应用程序可避免造成自身的拒绝服务。</span><span class="sxs-lookup"><span data-stu-id="23962-127">By using a circuit breaker, the application avoids provoking a denial of service to itself.</span></span>

![通过以指数回退方式重试处理的部分故障的关系图。](./media/retry-partial-failures.png)

<span data-ttu-id="23962-129">**图 4-9.** 。</span><span class="sxs-lookup"><span data-stu-id="23962-129">**Figure 4-9.**</span></span> <span data-ttu-id="23962-130">通过以指数回退方式重试处理的部分故障</span><span class="sxs-lookup"><span data-stu-id="23962-130">Partial failures handled by retries with exponential backoff</span></span>

<span data-ttu-id="23962-131">可以在 HTTP 资源和数据库资源中使用这些技术。</span><span class="sxs-lookup"><span data-stu-id="23962-131">You can use these techniques both in HTTP resources and in database resources.</span></span> <span data-ttu-id="23962-132">在图 4-9 中，应用程序基于 3 层体系结构，因此，你需要在服务级别 (HTTP) 和数据级别 (TCP) 上使用这些方法。</span><span class="sxs-lookup"><span data-stu-id="23962-132">In Figure 4-9, the application is based on a 3-tier architecture, so you need these techniques at the services level (HTTP) and at the data tier level (TCP).</span></span> <span data-ttu-id="23962-133">在除数据库之外仅使用单个应用层（无其他服务或微服务）的整体式应用程序中，处理数据库连接级别的暂时性故障可能就足够了。</span><span class="sxs-lookup"><span data-stu-id="23962-133">In a monolithic application that uses only a single app tier in addition to the database (no additional services or microservices), handling transient failures at the database connection level might be enough.</span></span> <span data-ttu-id="23962-134">在这种情况下，只需要数据库连接的特定配置。</span><span class="sxs-lookup"><span data-stu-id="23962-134">In that scenario, just a particular configuration of the database connection is required.</span></span>

<span data-ttu-id="23962-135">实现访问数据库的可复原通信时，根据所使用的 .NET 版本，过程可能非常直接（例如[带有实体框架 6 或更高版本](/ef/ef6/fundamentals/connection-resiliency/retry-logic)。</span><span class="sxs-lookup"><span data-stu-id="23962-135">When implementing resilient communications that access the database, depending on the version of .NET you are using, it can be straightforward (for example, [with Entity Framework 6 or later](/ef/ef6/fundamentals/connection-resiliency/retry-logic).</span></span> <span data-ttu-id="23962-136">只需配置数据库连接即可）。</span><span class="sxs-lookup"><span data-stu-id="23962-136">It's just a matter of configuring the database connection).</span></span> <span data-ttu-id="23962-137">或者，你可能需要使用其他库，如[暂时性故障处理应用程序块](/previous-versions/msp-n-p/hh680934(v=pandp.50))（适用于早期版本的 .NET），甚至实现你自己的库。</span><span class="sxs-lookup"><span data-stu-id="23962-137">Or, you might need to use additional libraries like the [Transient Fault Handling Application Block](/previous-versions/msp-n-p/hh680934(v=pandp.50)) (for earlier versions of .NET), or even implement your own library.</span></span>

<span data-ttu-id="23962-138">实现 HTTP 重试和断路器时，适用于 .NET 的建议使用 [Polly](https://github.com/App-vNext/Polly) 库，此库面向 .NET Framework 4.0、.NET Framework 4.5 和 .NET Standard 1.1，其中包括 .NET Core 支持。</span><span class="sxs-lookup"><span data-stu-id="23962-138">When implementing HTTP retries and circuit breakers, the recommendation for .NET is to use the [Polly](https://github.com/App-vNext/Polly) library, which targets .NET Framework 4.0, .NET Framework 4.5, and .NET Standard 1.1, which includes .NET Core support.</span></span>

<span data-ttu-id="23962-139">若要了解如何实现用于处理云中部分故障的策略，请参阅以下参考。</span><span class="sxs-lookup"><span data-stu-id="23962-139">To learn how to implement strategies for handling partial failures in the cloud, see the following references.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="23962-140">其他资源</span><span class="sxs-lookup"><span data-stu-id="23962-140">Additional resources</span></span>

- <span data-ttu-id="23962-141">**实现可复原通信以处理部分故障**</span><span class="sxs-lookup"><span data-stu-id="23962-141">**Implementing resilient communication to handle partial failure**</span></span>

    [https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/partial-failure-strategies](../../microservices/implement-resilient-applications/partial-failure-strategies.md)

- <span data-ttu-id="23962-142">**实体框架连接复原能力和重试逻辑（版本 6 及更高版本）**</span><span class="sxs-lookup"><span data-stu-id="23962-142">**Entity Framework connection resiliency and retry logic (version 6 and later)**</span></span>

    [https://docs.microsoft.com/ef/ef6/fundamentals/connection-resiliency/retry-logic](/ef/ef6/fundamentals/connection-resiliency/retry-logic)

- <span data-ttu-id="23962-143">**暂时性故障处理应用程序块**</span><span class="sxs-lookup"><span data-stu-id="23962-143">**The Transient Fault Handling Application Block**</span></span>

- <https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)>

- <span data-ttu-id="23962-144">**用于复原 HTTP 通信的 Polly 库**</span><span class="sxs-lookup"><span data-stu-id="23962-144">**Polly library for resilient HTTP communication**</span></span>

    <https://github.com/App-vNext/Polly>

>[!div class="step-by-step"]
><span data-ttu-id="23962-145">[上一页](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
>[下一页](modernize-your-apps-with-monitoring-and-telemetry.md)</span><span class="sxs-lookup"><span data-stu-id="23962-145">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](modernize-your-apps-with-monitoring-and-telemetry.md)</span></span>

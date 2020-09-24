---
title: 云本机通信模式
description: 了解云本机应用程序中的重要服务通信问题
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 5ce789924e828865f7bdf717b081b9112203293a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91160913"
---
# <a name="cloud-native-communication-patterns"></a><span data-ttu-id="e36f2-103">云本机通信模式</span><span class="sxs-lookup"><span data-stu-id="e36f2-103">Cloud-native communication patterns</span></span>

<span data-ttu-id="e36f2-104">构造云本机系统时，通信成为一项重大设计决策。</span><span class="sxs-lookup"><span data-stu-id="e36f2-104">When constructing a cloud-native system, communication becomes a significant design decision.</span></span> <span data-ttu-id="e36f2-105">前端客户端应用程序如何与后端微服务通信？</span><span class="sxs-lookup"><span data-stu-id="e36f2-105">How does a front-end client application communicate with a back-end microservice?</span></span> <span data-ttu-id="e36f2-106">后端微服务如何相互通信？</span><span class="sxs-lookup"><span data-stu-id="e36f2-106">How do back-end microservices communicate with each other?</span></span> <span data-ttu-id="e36f2-107">在云本机应用程序中实现通信时，应考虑哪些原则、模式和最佳做法？</span><span class="sxs-lookup"><span data-stu-id="e36f2-107">What are the principles, patterns, and best practices to consider when implementing communication in cloud-native applications?</span></span>

## <a name="communication-considerations"></a><span data-ttu-id="e36f2-108">通信注意事项</span><span class="sxs-lookup"><span data-stu-id="e36f2-108">Communication considerations</span></span>

<span data-ttu-id="e36f2-109">在单一应用程序中，通信非常简单。</span><span class="sxs-lookup"><span data-stu-id="e36f2-109">In a monolithic application, communication is straightforward.</span></span> <span data-ttu-id="e36f2-110">代码模块在同一可执行空间中一起执行 (在服务器上处理) 。</span><span class="sxs-lookup"><span data-stu-id="e36f2-110">The code modules execute together in the same executable space (process) on a server.</span></span> <span data-ttu-id="e36f2-111">这种方法可以提高性能，因为所有内容都在共享内存中同时运行，但会导致难以维护、发展和缩放的代码紧密耦合。</span><span class="sxs-lookup"><span data-stu-id="e36f2-111">This approach can have performance advantages as everything runs together in shared memory, but results in tightly coupled code that becomes difficult to maintain, evolve, and scale.</span></span>

<span data-ttu-id="e36f2-112">云本机系统实现了基于微服务的体系结构，其中包含许多小型的独立微服务。</span><span class="sxs-lookup"><span data-stu-id="e36f2-112">Cloud-native systems implement a microservice-based architecture with many small, independent microservices.</span></span> <span data-ttu-id="e36f2-113">每个微服务在单独的进程中执行，通常在部署到 *群集*的容器中运行。</span><span class="sxs-lookup"><span data-stu-id="e36f2-113">Each microservice executes in a separate process and typically runs inside a container that is deployed to a *cluster*.</span></span>

<span data-ttu-id="e36f2-114">群集将一组虚拟机组合在一起，形成高度可用的环境。</span><span class="sxs-lookup"><span data-stu-id="e36f2-114">A cluster groups a pool of virtual machines together to form a highly available environment.</span></span> <span data-ttu-id="e36f2-115">它们是使用业务流程工具进行管理的，该工具负责部署和管理容器化的微服务。</span><span class="sxs-lookup"><span data-stu-id="e36f2-115">They're managed with an orchestration tool, which is responsible for deploying and managing the containerized microservices.</span></span> <span data-ttu-id="e36f2-116">图4-1 显示了使用完全托管的[Azure Kubernetes 服务](/azure/aks/intro-kubernetes)部署到 azure 云中的[Kubernetes](https://kubernetes.io)群集。</span><span class="sxs-lookup"><span data-stu-id="e36f2-116">Figure 4-1 shows a [Kubernetes](https://kubernetes.io) cluster deployed into the Azure cloud with the fully managed [Azure Kubernetes Services](/azure/aks/intro-kubernetes).</span></span>

![Azure 中的 Kubernetes 群集](./media/kubernetes-cluster-in-azure.png)

<span data-ttu-id="e36f2-118">**图 4-1**。</span><span class="sxs-lookup"><span data-stu-id="e36f2-118">**Figure 4-1**.</span></span> <span data-ttu-id="e36f2-119">Azure 中的 Kubernetes 群集</span><span class="sxs-lookup"><span data-stu-id="e36f2-119">A Kubernetes cluster in Azure</span></span>

<span data-ttu-id="e36f2-120">在群集中，微服务通过 Api 和消息技术相互通信。</span><span class="sxs-lookup"><span data-stu-id="e36f2-120">Across the cluster, microservices communicate with each other through APIs and messaging technologies.</span></span>

<span data-ttu-id="e36f2-121">尽管它们提供了许多好处，但微服务没有免费的午餐。</span><span class="sxs-lookup"><span data-stu-id="e36f2-121">While they provide many benefits, microservices are no free lunch.</span></span> <span data-ttu-id="e36f2-122">组件之间的本地进程内方法调用现在被替换为网络调用。</span><span class="sxs-lookup"><span data-stu-id="e36f2-122">Local in-process method calls between components are now replaced with network calls.</span></span> <span data-ttu-id="e36f2-123">每个微服务都必须通过网络协议进行通信，这会增加系统的复杂性：</span><span class="sxs-lookup"><span data-stu-id="e36f2-123">Each microservice must communicate over a network protocol, which adds complexity to your system:</span></span>

- <span data-ttu-id="e36f2-124">网络拥塞、延迟和暂时性故障都是一个经常性的问题。</span><span class="sxs-lookup"><span data-stu-id="e36f2-124">Network congestion, latency, and transient faults are a constant concern.</span></span>

- <span data-ttu-id="e36f2-125">复原 (也就是说，重试失败的请求) 至关重要。</span><span class="sxs-lookup"><span data-stu-id="e36f2-125">Resiliency (that is, retrying failed requests) is essential.</span></span>

- <span data-ttu-id="e36f2-126">某些调用必须是 [幂等](https://www.restapitutorial.com/lessons/idempotency.html) 的，以便保持一致的状态。</span><span class="sxs-lookup"><span data-stu-id="e36f2-126">Some calls must be [idempotent](https://www.restapitutorial.com/lessons/idempotency.html) as to keep consistent state.</span></span>

- <span data-ttu-id="e36f2-127">每个微服务都必须对调用进行身份验证和授权。</span><span class="sxs-lookup"><span data-stu-id="e36f2-127">Each microservice must authenticate and authorize calls.</span></span>

- <span data-ttu-id="e36f2-128">必须对每个消息进行序列化，然后进行反序列化，这可能会消耗大量资源。</span><span class="sxs-lookup"><span data-stu-id="e36f2-128">Each message must be serialized and then deserialized - which can be expensive.</span></span>

- <span data-ttu-id="e36f2-129">消息加密/解密十分重要。</span><span class="sxs-lookup"><span data-stu-id="e36f2-129">Message encryption/decryption becomes important.</span></span>

<span data-ttu-id="e36f2-130">适用于 [容器化 .Net 应用程序的微服务的体系结构](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)可从 Microsoft 免费获取，为微服务应用程序提供了更深入的通信模式。</span><span class="sxs-lookup"><span data-stu-id="e36f2-130">The book [.NET Microservices: Architecture for Containerized .NET Applications](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook), available for free from Microsoft, provides an in-depth coverage of communication patterns for microservice applications.</span></span> <span data-ttu-id="e36f2-131">在本章中，我们提供了这些模式以及 Azure 云中提供的实现选项的高级概述。</span><span class="sxs-lookup"><span data-stu-id="e36f2-131">In this chapter, we provide a high-level overview of these patterns along with implementation options available in the Azure cloud.</span></span>

<span data-ttu-id="e36f2-132">在本章中，我们将首先解决前端应用程序和后端微服务之间的通信。</span><span class="sxs-lookup"><span data-stu-id="e36f2-132">In this chapter, we'll first address communication between front-end applications and back-end microservices.</span></span> <span data-ttu-id="e36f2-133">接下来，我们将探讨后端微服务相互通信。</span><span class="sxs-lookup"><span data-stu-id="e36f2-133">We'll then look at back-end microservices communicate with each other.</span></span> <span data-ttu-id="e36f2-134">我们将探索 gRPC 的通信技术。</span><span class="sxs-lookup"><span data-stu-id="e36f2-134">We'll explore the up and gRPC communication technology.</span></span> <span data-ttu-id="e36f2-135">最后，我们将使用服务网格技术来了解新的创新性通信模式。</span><span class="sxs-lookup"><span data-stu-id="e36f2-135">Finally, we'll look new innovative communication patterns using service mesh technology.</span></span> <span data-ttu-id="e36f2-136">我们还将了解 Azure 云如何提供不同种类的 *后备服务* 来支持云本机通信。</span><span class="sxs-lookup"><span data-stu-id="e36f2-136">We'll also see how the Azure cloud provides different kinds of *backing services* to support cloud-native communication.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e36f2-137">[上一页](other-deployment-options.md)
>[下一页](front-end-communication.md)</span><span class="sxs-lookup"><span data-stu-id="e36f2-137">[Previous](other-deployment-options.md)
[Next](front-end-communication.md)</span></span>

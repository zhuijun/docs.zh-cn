---
title: 可复原通信
description: 构建适用于 Azure 的云本机 .NET 应用 |弹性通信
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 18b26223634efc5c05f680d0cbb7c8cbc2490a59
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166035"
---
# <a name="resilient-communications"></a><span data-ttu-id="c2c9f-103">弹性通信</span><span class="sxs-lookup"><span data-stu-id="c2c9f-103">Resilient communications</span></span>

<span data-ttu-id="c2c9f-104">本书介绍了基于微服务的体系结构方法。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-104">Throughout this book, we've embraced a microservice-based architectural approach.</span></span> <span data-ttu-id="c2c9f-105">虽然这种体系结构提供了重要的优势，但却带来了许多挑战：</span><span class="sxs-lookup"><span data-stu-id="c2c9f-105">While such an architecture provides important benefits, it presents many challenges:</span></span>

- <span data-ttu-id="c2c9f-106">*进程外网络通信。*</span><span class="sxs-lookup"><span data-stu-id="c2c9f-106">*Out-of-process network communication.*</span></span> <span data-ttu-id="c2c9f-107">每个微服务都通过网络协议进行通信，该协议引入了网络拥塞、延迟和暂时性故障。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-107">Each microservice communicates over a network protocol that introduces network congestion, latency, and transient faults.</span></span>

- <span data-ttu-id="c2c9f-108">*服务发现。*</span><span class="sxs-lookup"><span data-stu-id="c2c9f-108">*Service discovery.*</span></span> <span data-ttu-id="c2c9f-109">当跨计算机群集使用其自己的 IP 地址和端口运行时，微服务如何发现并相互通信？</span><span class="sxs-lookup"><span data-stu-id="c2c9f-109">How do microservices discover and communicate with each other when running across a cluster of machines with their own IP addresses and ports?</span></span>

- <span data-ttu-id="c2c9f-110">*复原.*</span><span class="sxs-lookup"><span data-stu-id="c2c9f-110">*Resiliency.*</span></span> <span data-ttu-id="c2c9f-111">如何管理短暂的故障并使系统保持稳定？</span><span class="sxs-lookup"><span data-stu-id="c2c9f-111">How do you manage short-lived failures and keep the system stable?</span></span>

- <span data-ttu-id="c2c9f-112">*负载均衡。*</span><span class="sxs-lookup"><span data-stu-id="c2c9f-112">*Load balancing.*</span></span> <span data-ttu-id="c2c9f-113">如何在多个微服务实例之间分布入站流量？</span><span class="sxs-lookup"><span data-stu-id="c2c9f-113">How does inbound traffic get distributed across multiple instances of a microservice?</span></span>

- <span data-ttu-id="c2c9f-114">*安全性。*</span><span class="sxs-lookup"><span data-stu-id="c2c9f-114">*Security.*</span></span> <span data-ttu-id="c2c9f-115">安全问题（例如传输级加密和证书管理）如何强制实施？</span><span class="sxs-lookup"><span data-stu-id="c2c9f-115">How are security concerns such as transport-level encryption and certificate management enforced?</span></span>

- <span data-ttu-id="c2c9f-116">*分布式监视。*</span><span class="sxs-lookup"><span data-stu-id="c2c9f-116">*Distributed Monitoring.*</span></span> <span data-ttu-id="c2c9f-117">-你如何关联和捕获跨多个使用微服务的单个请求的可跟踪性和监视？</span><span class="sxs-lookup"><span data-stu-id="c2c9f-117">- How do you correlate and capture traceability and monitoring for a single request across multiple consuming microservices?</span></span>

<span data-ttu-id="c2c9f-118">你可以使用不同的库和框架解决这些问题，但实现可能成本高昂、复杂且耗时。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-118">You can address these concerns with different libraries and frameworks, but the implementation can be expensive, complex, and time-consuming.</span></span> <span data-ttu-id="c2c9f-119">最终，还会提供与业务逻辑耦合的基础结构问题。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-119">You also end up with infrastructure concerns coupled to business logic.</span></span>

## <a name="service-mesh"></a><span data-ttu-id="c2c9f-120">服务网格</span><span class="sxs-lookup"><span data-stu-id="c2c9f-120">Service mesh</span></span>

<span data-ttu-id="c2c9f-121">一种更好的方法是以 *服务网格*为依据的技术。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-121">A better approach is an evolving technology entitled *Service Mesh*.</span></span> <span data-ttu-id="c2c9f-122">[服务网格](https://www.nginx.com/blog/what-is-a-service-mesh/)是一种可配置的基础结构层，其中内置了用于处理服务通信的功能以及上述其他难题。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-122">A [service mesh](https://www.nginx.com/blog/what-is-a-service-mesh/) is a configurable infrastructure layer with built-in capabilities to handle service communication and the other challenges mentioned above.</span></span> <span data-ttu-id="c2c9f-123">它通过将这些问题移到服务代理中来分离这些问题。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-123">It decouples these concerns by moving them into a service proxy.</span></span> <span data-ttu-id="c2c9f-124">代理部署到一个单独的进程中 (称为 [挎斗](/azure/architecture/patterns/sidecar)) ，以提供与业务代码的隔离。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-124">The proxy is deployed into a separate process (called a [sidecar](/azure/architecture/patterns/sidecar)) to provide isolation from business code.</span></span> <span data-ttu-id="c2c9f-125">但是，挎斗链接到服务-它是用它创建的并共享其生命周期。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-125">However, the sidecar is linked to the service - it's created with it and shares its lifecycle.</span></span> <span data-ttu-id="c2c9f-126">图6-7 显示了这种情况。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-126">Figure 6-7 shows this scenario.</span></span>

![使用侧面汽车的服务网格](./media/service-mesh-with-side-car.png)

<span data-ttu-id="c2c9f-128">图 6-7  。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-128">**Figure 6-7**.</span></span> <span data-ttu-id="c2c9f-129">使用侧面汽车的服务网格</span><span class="sxs-lookup"><span data-stu-id="c2c9f-129">Service mesh with a side car</span></span>

<span data-ttu-id="c2c9f-130">在上图中，请注意代理如何截获和管理微服务与群集之间的通信。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-130">In the previous figure, note how the proxy intercepts and manages communication among the microservices and the cluster.</span></span>

<span data-ttu-id="c2c9f-131">服务网格以逻辑方式拆分为两个不同的组件： [数据平面](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc) 和 [控制平面](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc)。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-131">A service mesh is logically split into two disparate components: A [data plane](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc) and [control plane](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc).</span></span> <span data-ttu-id="c2c9f-132">图6-8 显示了这些组件及其责任。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-132">Figure 6-8 shows these components and their responsibilities.</span></span>

![服务网格控制和数据平面](./media/istio-control-and-data-plane.png)

<span data-ttu-id="c2c9f-134">**图6-8。**</span><span class="sxs-lookup"><span data-stu-id="c2c9f-134">**Figure 6-8.**</span></span> <span data-ttu-id="c2c9f-135">服务网格控制和数据平面</span><span class="sxs-lookup"><span data-stu-id="c2c9f-135">Service mesh control and data plane</span></span>

<span data-ttu-id="c2c9f-136">一旦配置后，服务网格就会非常有效。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-136">Once configured, a service mesh is highly functional.</span></span> <span data-ttu-id="c2c9f-137">它可以从服务发现终结点中检索相应的实例池。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-137">It can retrieve a corresponding pool of instances from a service discovery endpoint.</span></span> <span data-ttu-id="c2c9f-138">然后，网格可以将请求发送到特定的实例，记录结果的延迟和响应类型。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-138">The mesh can then send a request to a specific instance, recording the latency and response type of the result.</span></span> <span data-ttu-id="c2c9f-139">网格可以根据许多因素选择最有可能返回快速响应的实例，包括其观察到的最近请求的延迟。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-139">A mesh can choose the instance most likely to return a fast response based on many factors, including its observed latency for recent requests.</span></span>

<span data-ttu-id="c2c9f-140">如果实例无响应或失败，网格将在另一个实例上重试该请求。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-140">If an instance is unresponsive or fails, the mesh will retry the request on another instance.</span></span> <span data-ttu-id="c2c9f-141">如果它返回错误，则网格将从负载平衡池中逐出实例，并在修复后重述该实例。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-141">If it returns errors, a mesh will evict the instance from the load-balancing pool and restate it after it heals.</span></span> <span data-ttu-id="c2c9f-142">如果请求超时，网格可能会失败，然后重试该请求。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-142">If a request times out, a mesh can fail and then retry the request.</span></span> <span data-ttu-id="c2c9f-143">网格将捕获度量值并将其分发到集中式指标系统。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-143">A mesh captures and emits metrics and distributed tracing to a centralized metrics system.</span></span>

## <a name="istio-and-envoy"></a><span data-ttu-id="c2c9f-144">Istio 和 Envoy</span><span class="sxs-lookup"><span data-stu-id="c2c9f-144">Istio and Envoy</span></span>

<span data-ttu-id="c2c9f-145">虽然目前存在一些服务网格选项，但在撰写本文时， [Istio](https://istio.io/docs/concepts/what-is-istio/) 是最受欢迎的。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-145">While a few service mesh options currently exist, [Istio](https://istio.io/docs/concepts/what-is-istio/) is the most popular at the time of this writing.</span></span> <span data-ttu-id="c2c9f-146">Istio 是 IBM、Google 和 Lyft 的联合冒险。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-146">Istio is a joint venture from IBM, Google, and Lyft.</span></span> <span data-ttu-id="c2c9f-147">这是一个开源产品，可集成到新的或现有的分布式应用程序。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-147">It's an open-source offering that can be integrated into a new or existing distributed application.</span></span> <span data-ttu-id="c2c9f-148">该技术提供了一个一致且完整的解决方案来保护、连接和监视微服务。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-148">The technology provides a consistent and complete solution to secure, connect, and monitor microservices.</span></span> <span data-ttu-id="c2c9f-149">其功能包括：</span><span class="sxs-lookup"><span data-stu-id="c2c9f-149">Its features include:</span></span>

- <span data-ttu-id="c2c9f-150">使用基于标识的强身份验证和授权在群集中保护服务间通信。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-150">Secure service-to-service communication in a cluster with strong identity-based authentication and authorization.</span></span>
- <span data-ttu-id="c2c9f-151">自动负载均衡，适用于 HTTP、 [gRPC](https://grpc.io/)、WEBSOCKET 和 TCP 流量。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-151">Automatic load balancing for HTTP, [gRPC](https://grpc.io/), WebSocket, and TCP traffic.</span></span>
- <span data-ttu-id="c2c9f-152">通过丰富的路由规则、重试、故障转移和故障注入对流量行为进行精细控制。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-152">Fine-grained control of traffic behavior with rich routing rules, retries, failovers, and fault injection.</span></span>
- <span data-ttu-id="c2c9f-153">支持访问控制、速率限制和配额的可插入策略层和配置 API。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-153">A pluggable policy layer and configuration API supporting access controls, rate limits, and quotas.</span></span>
- <span data-ttu-id="c2c9f-154">针对群集中的所有流量（包括流入和出口）的自动指标、日志和跟踪。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-154">Automatic metrics, logs, and traces for all traffic within a cluster, including cluster ingress and egress.</span></span>

<span data-ttu-id="c2c9f-155">Istio 实现的关键组件是一种名为 [Envoy 代理](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy)的代理服务。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-155">A key component for an Istio implementation is a proxy service entitled the [Envoy proxy](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy).</span></span> <span data-ttu-id="c2c9f-156">它与每个服务一起运行，并为以下功能提供平台无关的基础：</span><span class="sxs-lookup"><span data-stu-id="c2c9f-156">It runs alongside each service and provides a platform-agnostic foundation for the following features:</span></span>

- <span data-ttu-id="c2c9f-157">动态服务发现。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-157">Dynamic service discovery.</span></span>
- <span data-ttu-id="c2c9f-158">负载均衡。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-158">Load balancing.</span></span>
- <span data-ttu-id="c2c9f-159">TLS 终止。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-159">TLS termination.</span></span>
- <span data-ttu-id="c2c9f-160">HTTP 和 gRPC 代理。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-160">HTTP and gRPC proxies.</span></span>
- <span data-ttu-id="c2c9f-161">断路器复原。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-161">Circuit breaker resiliency.</span></span>
- <span data-ttu-id="c2c9f-162">运行状况检查。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-162">Health checks.</span></span>
- <span data-ttu-id="c2c9f-163">[用不](https://martinfowler.com/bliki/CanaryRelease.html)到的部署滚动更新。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-163">Rolling updates with [canary](https://martinfowler.com/bliki/CanaryRelease.html) deployments.</span></span>

<span data-ttu-id="c2c9f-164">如前文所述，Envoy 作为挎斗部署到群集中的每个微服务。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-164">As previously discussed, Envoy is deployed as a sidecar to each microservice in the cluster.</span></span>

## <a name="integration-with-azure-kubernetes-services"></a><span data-ttu-id="c2c9f-165">与 Azure Kubernetes 服务集成</span><span class="sxs-lookup"><span data-stu-id="c2c9f-165">Integration with Azure Kubernetes Services</span></span>

<span data-ttu-id="c2c9f-166">Azure 云支持 Istio，并在 Azure Kubernetes 服务中提供对该服务的直接支持。</span><span class="sxs-lookup"><span data-stu-id="c2c9f-166">The Azure cloud embraces Istio and provides direct support for it within Azure Kubernetes Services.</span></span> <span data-ttu-id="c2c9f-167">以下链接可帮助你入门：</span><span class="sxs-lookup"><span data-stu-id="c2c9f-167">The following links can help you get started:</span></span>

- [<span data-ttu-id="c2c9f-168">在 AKS 中安装 Istio</span><span class="sxs-lookup"><span data-stu-id="c2c9f-168">Installing Istio in AKS</span></span>](/azure/aks/istio-install)
- [<span data-ttu-id="c2c9f-169">使用 AKS 和 Istio</span><span class="sxs-lookup"><span data-stu-id="c2c9f-169">Using AKS and Istio</span></span>](/azure/aks/istio-scenario-routing)

### <a name="references"></a><span data-ttu-id="c2c9f-170">参考</span><span class="sxs-lookup"><span data-stu-id="c2c9f-170">References</span></span>

- [<span data-ttu-id="c2c9f-171">Polly</span><span class="sxs-lookup"><span data-stu-id="c2c9f-171">Polly</span></span>](http://www.thepollyproject.org/)

- [<span data-ttu-id="c2c9f-172">重试模式</span><span class="sxs-lookup"><span data-stu-id="c2c9f-172">Retry pattern</span></span>](/azure/architecture/patterns/retry)

- [<span data-ttu-id="c2c9f-173">断路器模式</span><span class="sxs-lookup"><span data-stu-id="c2c9f-173">Circuit Breaker pattern</span></span>](/azure/architecture/patterns/circuit-breaker)

- [<span data-ttu-id="c2c9f-174">Azure 白皮书中的复原能力</span><span class="sxs-lookup"><span data-stu-id="c2c9f-174">Resilience in Azure whitepaper</span></span>](https://azure.microsoft.com/mediahandler/files/resourcefiles/resilience-in-azure-whitepaper/Resilience%20in%20Azure.pdf)

- [<span data-ttu-id="c2c9f-175">网络延迟</span><span class="sxs-lookup"><span data-stu-id="c2c9f-175">network latency</span></span>](https://www.techopedia.com/definition/8553/network-latency)

- [<span data-ttu-id="c2c9f-176">冗余</span><span class="sxs-lookup"><span data-stu-id="c2c9f-176">Redundancy</span></span>](/azure/architecture/guide/design-principles/redundancy)

- [<span data-ttu-id="c2c9f-177">异地复制</span><span class="sxs-lookup"><span data-stu-id="c2c9f-177">geo-replication</span></span>](/azure/sql-database/sql-database-active-geo-replication)

- [<span data-ttu-id="c2c9f-178">Azure 流量管理器</span><span class="sxs-lookup"><span data-stu-id="c2c9f-178">Azure Traffic Manager</span></span>](/azure/traffic-manager/traffic-manager-overview)

- [<span data-ttu-id="c2c9f-179">自动缩放指南</span><span class="sxs-lookup"><span data-stu-id="c2c9f-179">Autoscaling guidance</span></span>](/azure/architecture/best-practices/auto-scaling)

- [<span data-ttu-id="c2c9f-180">Istio</span><span class="sxs-lookup"><span data-stu-id="c2c9f-180">Istio</span></span>](https://istio.io/docs/concepts/what-is-istio/)

- [<span data-ttu-id="c2c9f-181">Envoy 代理</span><span class="sxs-lookup"><span data-stu-id="c2c9f-181">Envoy proxy</span></span>](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy)

>[!div class="step-by-step"]
><span data-ttu-id="c2c9f-182">[上一页](infrastructure-resiliency-azure.md)
>[下一页](monitoring-health.md)</span><span class="sxs-lookup"><span data-stu-id="c2c9f-182">[Previous](infrastructure-resiliency-azure.md)
[Next](monitoring-health.md)</span></span>

---
title: 云本机复原能力
description: 构建适用于 Azure 的云本机 .NET 应用 |云本机复原
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 5c4fb261515c151fd666cc33cbb020447716c814
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163552"
---
# <a name="cloud-native-resiliency"></a><span data-ttu-id="71b37-103">云本机复原能力</span><span class="sxs-lookup"><span data-stu-id="71b37-103">Cloud-native resiliency</span></span>

<span data-ttu-id="71b37-104">复原能力是指系统能够应对故障，并仍能正常工作。</span><span class="sxs-lookup"><span data-stu-id="71b37-104">Resiliency is the ability of your system to react to failure and still remain functional.</span></span> <span data-ttu-id="71b37-105">这并不是为了避免故障，而是接受故障，并构建云本机服务来响应它。</span><span class="sxs-lookup"><span data-stu-id="71b37-105">It's not about avoiding failure, but accepting failure and constructing your cloud-native services to respond to it.</span></span> <span data-ttu-id="71b37-106">你需要尽快返回到完全正常运行的状态。</span><span class="sxs-lookup"><span data-stu-id="71b37-106">You want to return to a fully functioning state quickly as possible.</span></span>

<span data-ttu-id="71b37-107">与传统的单一应用程序不同，在一个进程中，所有内容都一起运行，云本机系统采用分布式体系结构，如图6-1 所示：</span><span class="sxs-lookup"><span data-stu-id="71b37-107">Unlike traditional monolithic applications, where everything runs together in a single process, cloud-native systems embrace a distributed architecture as shown in Figure 6-1:</span></span>

![分布式云-本机环境](./media/distributed-cloud-native-environment.png)

<span data-ttu-id="71b37-109">**图 6-1**。</span><span class="sxs-lookup"><span data-stu-id="71b37-109">**Figure 6-1.**</span></span> <span data-ttu-id="71b37-110">分布式云-本机环境</span><span class="sxs-lookup"><span data-stu-id="71b37-110">Distributed cloud-native environment</span></span>

<span data-ttu-id="71b37-111">在上图中，每个微服务和基于云的 [支持服务](https://12factor.net/backing-services) 在单独的进程中执行，跨服务器基础结构，通过基于网络的调用进行通信。</span><span class="sxs-lookup"><span data-stu-id="71b37-111">In the previous figure, each microservice and cloud-based [backing service](https://12factor.net/backing-services) execute in a separate process, across server infrastructure, communicating via network-based calls.</span></span>

<span data-ttu-id="71b37-112">在此环境中操作，服务必须对许多不同的难题保密：</span><span class="sxs-lookup"><span data-stu-id="71b37-112">Operating in this environment, a service must be sensitive to many different challenges:</span></span>

- <span data-ttu-id="71b37-113">意外的网络延迟-服务请求到达接收方和背面的时间。</span><span class="sxs-lookup"><span data-stu-id="71b37-113">Unexpected network latency - the time for a service request to travel to the receiver and back.</span></span>

- <span data-ttu-id="71b37-114">[暂时性故障](/azure/architecture/best-practices/transient-faults) -生存期较短的网络连接错误。</span><span class="sxs-lookup"><span data-stu-id="71b37-114">[Transient faults](/azure/architecture/best-practices/transient-faults) - short-lived network connectivity errors.</span></span>

- <span data-ttu-id="71b37-115">由长时间运行的同步操作所阻塞。</span><span class="sxs-lookup"><span data-stu-id="71b37-115">Blockage by a long-running synchronous operation.</span></span>

- <span data-ttu-id="71b37-116">已崩溃并且正在重新启动或移动的主机进程。</span><span class="sxs-lookup"><span data-stu-id="71b37-116">A host process that has crashed and is being restarted or moved.</span></span>

- <span data-ttu-id="71b37-117">一段时间后无法响应的重载微服务。</span><span class="sxs-lookup"><span data-stu-id="71b37-117">An overloaded microservice that can't respond for a short time.</span></span>

- <span data-ttu-id="71b37-118">正在进行的 orchestrator 操作，例如滚动升级或将服务从一个节点移到另一个节点。</span><span class="sxs-lookup"><span data-stu-id="71b37-118">An in-flight orchestrator operation such as a rolling upgrade or moving a service from one node to another.</span></span>

- <span data-ttu-id="71b37-119">硬件故障。</span><span class="sxs-lookup"><span data-stu-id="71b37-119">Hardware failures.</span></span>

<span data-ttu-id="71b37-120">云平台可以检测并缓解其中许多基础结构问题。</span><span class="sxs-lookup"><span data-stu-id="71b37-120">Cloud platforms can detect and mitigate many of these infrastructure issues.</span></span> <span data-ttu-id="71b37-121">它可以重启、横向扩展，甚至可将你的服务重新分发到另一个节点。</span><span class="sxs-lookup"><span data-stu-id="71b37-121">It may restart, scale out, and even redistribute your service to a different node.</span></span>  <span data-ttu-id="71b37-122">但是，若要充分利用此内置保护，你必须将你的服务设计为对其做出反应并在此动态环境中发展。</span><span class="sxs-lookup"><span data-stu-id="71b37-122">However, to take full advantage of this built-in protection, you must design your services to react to it and thrive in this dynamic environment.</span></span>

<span data-ttu-id="71b37-123">在以下部分中，我们将探讨你的服务和托管云资源可利用的防御性技术，以最大程度地减少停机时间和中断时间。</span><span class="sxs-lookup"><span data-stu-id="71b37-123">In the following sections, we'll explore defensive techniques that your service and managed cloud resources can leverage to minimize downtime and disruption.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="71b37-124">[上一页](elastic-search-in-azure.md)
>[下一页](application-resiliency-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="71b37-124">[Previous](elastic-search-in-azure.md)
[Next](application-resiliency-patterns.md)</span></span>

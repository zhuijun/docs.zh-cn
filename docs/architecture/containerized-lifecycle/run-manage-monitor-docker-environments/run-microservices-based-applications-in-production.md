---
title: 在生产环境中运行基于微服务的组合应用程序
description: 了解在生产中运行基于容器的应用程序的关键组件
ms.date: 08/06/2020
ms.openlocfilehash: a045804e2e40dcf401a697d3e58b13f05ca61b94
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915045"
---
# <a name="run-composed-and-microservices-based-applications-in-production-environments"></a><span data-ttu-id="6e5bc-103">在生产环境中运行基于微服务的组合应用程序</span><span class="sxs-lookup"><span data-stu-id="6e5bc-103">Run composed and microservices-based applications in production environments</span></span>

<span data-ttu-id="6e5bc-104">由多个微服务组成的应用程序确实需要部署到业务流程协调程序群集中，才能简化部署的复杂性并使其从 IT 角度来看是可行的。</span><span class="sxs-lookup"><span data-stu-id="6e5bc-104">Applications composed by multiple microservices do need to be deployed into orchestrator clusters in order to simplify the complexity of deployment and make it viable from an IT point of view.</span></span> <span data-ttu-id="6e5bc-105">如果没有业务流程协调程序群集，很难部署和横向扩展复杂的微服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="6e5bc-105">Without an orchestrator cluster, it would be difficult to deploy and scale out a complex microservices application.</span></span>

## <a name="introduction-to-orchestrators-schedulers-and-container-clusters"></a><span data-ttu-id="6e5bc-106">业务流程协调程序、计划程序以及容器群集的简介</span><span class="sxs-lookup"><span data-stu-id="6e5bc-106">Introduction to orchestrators, schedulers, and container clusters</span></span>

<span data-ttu-id="6e5bc-107">本电子书的前面部分介绍了群集和计划程序（作为软件体系结构和开发讨论的一部分）   。</span><span class="sxs-lookup"><span data-stu-id="6e5bc-107">Earlier in this e-book, *clusters* and *schedulers* were introduced as part of the discussion on software architecture and development.</span></span> <span data-ttu-id="6e5bc-108">Kubernetes 和 Service Fabric 都是 Docker 群集的示例。</span><span class="sxs-lookup"><span data-stu-id="6e5bc-108">Kubernetes and Service Fabric are examples of Docker clusters.</span></span> <span data-ttu-id="6e5bc-109">这两个业务流程协调程序都可以作为 Microsoft Azure Kubernetes Service 提供的基础结构的一部分运行。</span><span class="sxs-lookup"><span data-stu-id="6e5bc-109">Both of these orchestrators can run as a part of the infrastructure provided by Microsoft Azure Kubernetes Service.</span></span>

<span data-ttu-id="6e5bc-110">应用程序跨多个主机系统横向扩展时，管理每个主机系统和抽离基础平台的复杂性的能力就变得有吸引力了。</span><span class="sxs-lookup"><span data-stu-id="6e5bc-110">When applications are scaled-out across multiple host systems, the ability to manage each host system and abstract away the complexity of the underlying platform becomes attractive.</span></span> <span data-ttu-id="6e5bc-111">这正是业务流程协调程序和计划程序所提供的内容。</span><span class="sxs-lookup"><span data-stu-id="6e5bc-111">That's precisely what orchestrators and schedulers provide.</span></span> <span data-ttu-id="6e5bc-112">接下来简要了解这两者：</span><span class="sxs-lookup"><span data-stu-id="6e5bc-112">Let's take a brief look at them here:</span></span>

- <span data-ttu-id="6e5bc-113">**计划程序**。</span><span class="sxs-lookup"><span data-stu-id="6e5bc-113">**Schedulers**.</span></span><span data-ttu-id="6e5bc-114"> “计划”是指管理员可以将服务文件加载到主机系统，让主机系统确定如何运行特定容器。</span><span class="sxs-lookup"><span data-stu-id="6e5bc-114"> "Scheduling" refers to the ability for an administrator to load a service file onto a host system that establishes how to run a specific container.</span></span> <span data-ttu-id="6e5bc-115">在 Docker 群集中启动容器通常称为计划。</span><span class="sxs-lookup"><span data-stu-id="6e5bc-115">Launching containers in a Docker cluster tends to be known as scheduling.</span></span> <span data-ttu-id="6e5bc-116">虽然计划是指加载服务定义的特定行为，但从更常规的意义上讲，计划程序负责挂接到主机的 init 系统以管理任何所需容量的服务。</span><span class="sxs-lookup"><span data-stu-id="6e5bc-116">Although scheduling refers to the specific act of loading the service definition, in a more general sense, schedulers are responsible for hooking into a host's init system to manage services in whatever capacity needed.</span></span>

   <span data-ttu-id="6e5bc-117">群集计划程序有多个目的：有效使用群集资源、使用用户提供的放置约束、快速计划应用程序以使其不处于挂起状态、具有一定程度的“公平性”、能够承受错误以及始终可用。</span><span class="sxs-lookup"><span data-stu-id="6e5bc-117">A cluster scheduler has multiple goals: using the cluster's resources efficiently, working with user-supplied placement constraints, scheduling applications rapidly to not leave them in a pending state, having a degree of "fairness," being robust to errors, and always be available.</span></span>

- <span data-ttu-id="6e5bc-118">**业务流程协调程序**。</span><span class="sxs-lookup"><span data-stu-id="6e5bc-118">**Orchestrators**.</span></span><span data-ttu-id="6e5bc-119"> 平台将生命周期管理功能扩展到部署在主机群集上的复杂的多容器工作负载。</span><span class="sxs-lookup"><span data-stu-id="6e5bc-119"> Platforms extend life-cycle management capabilities to complex, multi-container workloads deployed on a cluster of hosts.</span></span> <span data-ttu-id="6e5bc-120">通过抽象主机基础结构，业务流程工具为用户提供了一种方法，可以将整个群集视为单个部署目标。</span><span class="sxs-lookup"><span data-stu-id="6e5bc-120">By abstracting the host infrastructure, orchestration tools give users a way to treat the entire cluster as a single deployment target.</span></span>

   <span data-ttu-id="6e5bc-121">业务流程的过程涉及工具和平台，可以从每个容器的初始放置或部署自动执行应用程序管理的所有方面；根据主机的运行状况或性能，将容器迁移到不同的主机；版本控制和滚动更新以及支持扩展和故障转移的运行状况监视功能等。</span><span class="sxs-lookup"><span data-stu-id="6e5bc-121">The process of orchestration involves tooling and a platform that can automate all aspects of application management from initial placement or deployment per container; moving containers to different hosts depending on its host's health or performance; versioning and rolling updates and health monitoring functions that support scaling and failover; and many more.</span></span>

   <span data-ttu-id="6e5bc-122">业务流程是一个泛指的术语，指容器计划、群集管理和可能的其他主机预配。</span><span class="sxs-lookup"><span data-stu-id="6e5bc-122">Orchestration is a broad term that refers to container scheduling, cluster management, and possibly the provisioning of additional hosts.</span></span>

<span data-ttu-id="6e5bc-123">业务流程协调程序和计划程序提供的功能很难从头开发和创建，因此通常使用供应商提供的业务流程解决方案。</span><span class="sxs-lookup"><span data-stu-id="6e5bc-123">The capabilities provided by orchestrators and schedulers are complex to develop and create from scratch, therefore you usually would want to use orchestration solutions offered by vendors.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6e5bc-124">[上一页](index.md)
>[下一页](manage-production-docker-environments.md)</span><span class="sxs-lookup"><span data-stu-id="6e5bc-124">[Previous](index.md)
[Next](manage-production-docker-environments.md)</span></span>

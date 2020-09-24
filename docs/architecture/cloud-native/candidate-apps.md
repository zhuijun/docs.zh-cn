---
title: 云本机的候选应用
description: 了解哪些类型的应用程序受益于云本机方法
author: robvet
ms.date: 05/14/2020
ms.openlocfilehash: 8f00633a575dad12b0bc1d5adb83acac03db0659
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91160939"
---
# <a name="candidate-apps-for-cloud-native"></a><span data-ttu-id="8af0e-103">云本机的候选应用</span><span class="sxs-lookup"><span data-stu-id="8af0e-103">Candidate apps for cloud native</span></span>

<span data-ttu-id="8af0e-104">查看公文包中的应用。</span><span class="sxs-lookup"><span data-stu-id="8af0e-104">Look at the apps in your portfolio.</span></span> <span data-ttu-id="8af0e-105">有多少用户有资格使用云本机体系结构？</span><span class="sxs-lookup"><span data-stu-id="8af0e-105">How many of them qualify for a cloud-native architecture?</span></span> <span data-ttu-id="8af0e-106">它们全部？</span><span class="sxs-lookup"><span data-stu-id="8af0e-106">All of them?</span></span> <span data-ttu-id="8af0e-107">也许有些吗？</span><span class="sxs-lookup"><span data-stu-id="8af0e-107">Perhaps some?</span></span>

<span data-ttu-id="8af0e-108">应用成本/收益分析后，就很有可能不支持巨大价格标记，这是云本机所必需的。</span><span class="sxs-lookup"><span data-stu-id="8af0e-108">Applying a cost/benefit analysis, there's a good chance that most wouldn't support the hefty price tag required to be cloud native.</span></span> <span data-ttu-id="8af0e-109">云本机的成本远远超出了应用程序的商业价值。</span><span class="sxs-lookup"><span data-stu-id="8af0e-109">The cost of being cloud native would far exceed the business value of the application.</span></span>

<span data-ttu-id="8af0e-110">什么类型的应用程序可能是云本机的候选项？</span><span class="sxs-lookup"><span data-stu-id="8af0e-110">What type of application might be a candidate for cloud native?</span></span>

- <span data-ttu-id="8af0e-111">需要不断发展业务能力/功能的战略企业系统</span><span class="sxs-lookup"><span data-stu-id="8af0e-111">Strategic enterprise system that need to constantly evolve business capabilities/features</span></span>

- <span data-ttu-id="8af0e-112">需要高发布速度的应用程序，具有高置信度</span><span class="sxs-lookup"><span data-stu-id="8af0e-112">An application that requires a high release velocity - with high confidence</span></span>

- <span data-ttu-id="8af0e-113">一种系统，其中的各个功能必须在不完全重新部署整个系统的情况 *下* 发布</span><span class="sxs-lookup"><span data-stu-id="8af0e-113">A system with where individual features must release *without* a full redeployment of the entire system</span></span>

- <span data-ttu-id="8af0e-114">团队开发的应用程序，具有不同技术领域的专业知识</span><span class="sxs-lookup"><span data-stu-id="8af0e-114">An application developed by teams with expertise in different technology stacks</span></span>

- <span data-ttu-id="8af0e-115">具有必须独立缩放的组件的应用程序</span><span class="sxs-lookup"><span data-stu-id="8af0e-115">An application with components that must scale independently</span></span>

<span data-ttu-id="8af0e-116">然后有一些旧系统。</span><span class="sxs-lookup"><span data-stu-id="8af0e-116">Then there are legacy systems.</span></span> <span data-ttu-id="8af0e-117">尽管我们都喜欢构建新的应用程序，但我们经常负责现代化对企业至关重要的旧工作负荷。</span><span class="sxs-lookup"><span data-stu-id="8af0e-117">While we'd all like to build new applications, we're often responsible for modernizing legacy workloads that are critical to the business.</span></span> <span data-ttu-id="8af0e-118">随着时间的推移，旧应用程序可以分解为微服务，并最终将 "replatformed" 分解为云本机体系结构。</span><span class="sxs-lookup"><span data-stu-id="8af0e-118">Over time, a legacy application could be decomposed into microservices, containerized, and ultimately "replatformed" into a cloud-native architecture.</span></span>

### <a name="modernizing-legacy-apps"></a><span data-ttu-id="8af0e-119">现代化旧版应用</span><span class="sxs-lookup"><span data-stu-id="8af0e-119">Modernizing legacy apps</span></span>

<span data-ttu-id="8af0e-120">免费的 Microsoft 电子书 [通过 Azure 云和 Windows 容器实现现有 .net 应用程序的现代化，](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) 为将本地工作负荷迁移到云中提供了指导。</span><span class="sxs-lookup"><span data-stu-id="8af0e-120">The free Microsoft e-book [Modernize existing .NET applications with Azure cloud and Windows Containers](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) provides guidance for migrating on-premises workloads into cloud.</span></span> <span data-ttu-id="8af0e-121">图1-10 显示，没有适用于现代化旧版应用程序的单个大小合适的策略。</span><span class="sxs-lookup"><span data-stu-id="8af0e-121">Figure 1-10 shows that there isn't a single, one-size-fits-all strategy for modernizing legacy applications.</span></span>

![迁移旧工作负荷的策略](./media/strategies-for-migrating-legacy-workloads.png)

<span data-ttu-id="8af0e-123">**图 1-10**。</span><span class="sxs-lookup"><span data-stu-id="8af0e-123">**Figure 1-10**.</span></span> <span data-ttu-id="8af0e-124">迁移旧工作负荷的策略</span><span class="sxs-lookup"><span data-stu-id="8af0e-124">Strategies for migrating legacy workloads</span></span>

<span data-ttu-id="8af0e-125">不关键的单一应用在很大程度上得益于快速迁移 ([云基础结构](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md) 的) 迁移。</span><span class="sxs-lookup"><span data-stu-id="8af0e-125">Monolithic apps that are non-critical largely benefit from a quick lift-and-shift ([Cloud Infrastructure-Ready](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md)) migration.</span></span> <span data-ttu-id="8af0e-126">此处，本地工作负荷重新承载基于云的 VM，无需更改。</span><span class="sxs-lookup"><span data-stu-id="8af0e-126">Here, the on-premises workload is rehosted to a cloud-based VM, without changes.</span></span> <span data-ttu-id="8af0e-127">此方法使用 [IaaS (基础结构即服务) 模型](https://azure.microsoft.com/overview/what-is-iaas/)。</span><span class="sxs-lookup"><span data-stu-id="8af0e-127">This approach uses the [IaaS (Infrastructure as a Service) model](https://azure.microsoft.com/overview/what-is-iaas/).</span></span> <span data-ttu-id="8af0e-128">Azure 包含多个工具，如 [Azure Migrate](https://azure.microsoft.com/services/azure-migrate/)、 [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/)和 [Azure 数据库迁移服务](https://azure.microsoft.com/campaigns/database-migration/) ，使此类移动更容易。</span><span class="sxs-lookup"><span data-stu-id="8af0e-128">Azure includes several tools such as [Azure Migrate](https://azure.microsoft.com/services/azure-migrate/), [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/), and [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/) to make such a move easier.</span></span> <span data-ttu-id="8af0e-129">尽管此策略可能会节省成本，但这种应用程序通常不会构建为解锁和利用云计算的好处。</span><span class="sxs-lookup"><span data-stu-id="8af0e-129">While this strategy can yield some cost savings, such applications typically weren't architected to unlock and leverage the benefits of cloud computing.</span></span>

<span data-ttu-id="8af0e-130">对业务至关重要的单一应用程序通常会受益于改进的 (*云优化*) 迁移。</span><span class="sxs-lookup"><span data-stu-id="8af0e-130">Monolithic apps that are critical to the business oftentimes benefit from an enhanced lift-and-shift (*Cloud Optimized*) migration.</span></span> <span data-ttu-id="8af0e-131">此方法包括启用关键云服务的部署优化，无需更改应用程序的核心体系结构。</span><span class="sxs-lookup"><span data-stu-id="8af0e-131">This approach includes deployment optimizations that enable key cloud services - without changing the core architecture of the application.</span></span> <span data-ttu-id="8af0e-132">例如，你可能会 [容器化](/virtualization/windowscontainers/about/) 该应用程序并将其部署到容器 orchestrator，如 [Azure Kubernetes Services](https://azure.microsoft.com/services/kubernetes-service/)，如本书稍后部分所述。</span><span class="sxs-lookup"><span data-stu-id="8af0e-132">For example, you might [containerize](/virtualization/windowscontainers/about/) the application and deploy it to a container orchestrator, like [Azure Kubernetes Services](https://azure.microsoft.com/services/kubernetes-service/), discussed later in this book.</span></span> <span data-ttu-id="8af0e-133">一旦进入云中，应用程序就可以使用其他云服务，例如数据库、消息队列、监视和分布式缓存。</span><span class="sxs-lookup"><span data-stu-id="8af0e-133">Once in the cloud, the application could consume other cloud services such as databases, message queues, monitoring, and distributed caching.</span></span>

<span data-ttu-id="8af0e-134">最后，执行战略性企业功能的单一应用程序可能最大程度地受益于 *云本机* 方法（本书的主题）。</span><span class="sxs-lookup"><span data-stu-id="8af0e-134">Finally, monolithic apps that perform strategic enterprise functions might best benefit from a *Cloud-Native* approach, the subject of this book.</span></span> <span data-ttu-id="8af0e-135">此方法可提供灵活性和速度。</span><span class="sxs-lookup"><span data-stu-id="8af0e-135">This approach provides agility and velocity.</span></span> <span data-ttu-id="8af0e-136">但这种情况下，它需要 replatforming、重新架构和重写代码。</span><span class="sxs-lookup"><span data-stu-id="8af0e-136">But, it comes at a cost of replatforming, rearchitecting, and rewriting code.</span></span>

<span data-ttu-id="8af0e-137">如果你和你的团队相信云本机方法合适，则可以 behooves 你的组织制定决策。</span><span class="sxs-lookup"><span data-stu-id="8af0e-137">If you and your team believe a cloud-native approach is appropriate, it behooves you to rationalize the decision with your organization.</span></span> <span data-ttu-id="8af0e-138">云本机方法将解决什么问题？</span><span class="sxs-lookup"><span data-stu-id="8af0e-138">What exactly is the business problem that a cloud-native approach will solve?</span></span> <span data-ttu-id="8af0e-139">它如何与业务需求保持一致？</span><span class="sxs-lookup"><span data-stu-id="8af0e-139">How would it align with business needs?</span></span>

- <span data-ttu-id="8af0e-140">更自信地快速发布功能？</span><span class="sxs-lookup"><span data-stu-id="8af0e-140">Rapid releases of features with increased confidence?</span></span>

- <span data-ttu-id="8af0e-141">精细的可伸缩性-更有效地使用资源？</span><span class="sxs-lookup"><span data-stu-id="8af0e-141">Fine-grained scalability - more efficient usage of resources?</span></span>

- <span data-ttu-id="8af0e-142">提高了系统复原能力？</span><span class="sxs-lookup"><span data-stu-id="8af0e-142">Improved system resiliency?</span></span>

- <span data-ttu-id="8af0e-143">提高了系统性能？</span><span class="sxs-lookup"><span data-stu-id="8af0e-143">Improved system performance?</span></span>

- <span data-ttu-id="8af0e-144">更深入地了解操作？</span><span class="sxs-lookup"><span data-stu-id="8af0e-144">More visibility into operations?</span></span>

- <span data-ttu-id="8af0e-145">融合开发平台和数据存储以获得适用于该作业的最佳工具？</span><span class="sxs-lookup"><span data-stu-id="8af0e-145">Blend development platforms and data stores to arrive at the best tool for the job?</span></span>

- <span data-ttu-id="8af0e-146">未来的应用程序投资证明？</span><span class="sxs-lookup"><span data-stu-id="8af0e-146">Future-proof application investment?</span></span>

<span data-ttu-id="8af0e-147">适当的迁移策略取决于组织的优先级和目标系统。</span><span class="sxs-lookup"><span data-stu-id="8af0e-147">The right migration strategy depends on organizational priorities and the systems you're targeting.</span></span> <span data-ttu-id="8af0e-148">对于许多人来说，对单一应用程序进行云优化或将粗粒度服务添加到 N 层应用程序可能更具成本效益。</span><span class="sxs-lookup"><span data-stu-id="8af0e-148">For many, it may be more cost effective to cloud-optimize a monolithic application or add coarse-grained services to an N-Tier app.</span></span> <span data-ttu-id="8af0e-149">在这些情况下，你仍可以充分利用 cloud PaaS 功能，如 Azure App Service 提供的功能。</span><span class="sxs-lookup"><span data-stu-id="8af0e-149">In these cases, you can still make full use of cloud PaaS capabilities like the ones offered by Azure App Service.</span></span>

## <a name="summary"></a><span data-ttu-id="8af0e-150">总结</span><span class="sxs-lookup"><span data-stu-id="8af0e-150">Summary</span></span>

<span data-ttu-id="8af0e-151">本章介绍了云本机计算。</span><span class="sxs-lookup"><span data-stu-id="8af0e-151">In this chapter, we introduced cloud-native computing.</span></span> <span data-ttu-id="8af0e-152">我们提供了一个定义，同时提供了驱动云本机应用程序的关键功能。</span><span class="sxs-lookup"><span data-stu-id="8af0e-152">We provided a definition along with the key capabilities that drive a cloud-native application.</span></span> <span data-ttu-id="8af0e-153">我们探讨了可证明这种投资和工作量的应用程序类型。</span><span class="sxs-lookup"><span data-stu-id="8af0e-153">We looked at the types of applications that might justify this investment and effort.</span></span>

<span data-ttu-id="8af0e-154">随着简介，我们现在深入了解云本机。</span><span class="sxs-lookup"><span data-stu-id="8af0e-154">With the introduction behind, we now dive into a much more detailed look at cloud native.</span></span>

### <a name="references"></a><span data-ttu-id="8af0e-155">参考</span><span class="sxs-lookup"><span data-stu-id="8af0e-155">References</span></span>

- [<span data-ttu-id="8af0e-156">云本机计算基础</span><span class="sxs-lookup"><span data-stu-id="8af0e-156">Cloud Native Computing Foundation</span></span>](https://www.cncf.io/)

- [<span data-ttu-id="8af0e-157">.NET 微服务：容器化 .NET 应用程序的体系结构</span><span class="sxs-lookup"><span data-stu-id="8af0e-157">.NET Microservices: Architecture for Containerized .NET applications</span></span>](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [<span data-ttu-id="8af0e-158">利用 Azure 云和 Windows 容器实现现有 .NET 应用程序的现代化</span><span class="sxs-lookup"><span data-stu-id="8af0e-158">Modernize existing .NET applications with Azure cloud and Windows Containers</span></span>](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)

- [<span data-ttu-id="8af0e-159">云本机模式（按 Cornelia Davis）</span><span class="sxs-lookup"><span data-stu-id="8af0e-159">Cloud Native Patterns by Cornelia Davis</span></span>](https://www.manning.com/books/cloud-native-patterns)

- [<span data-ttu-id="8af0e-160">超过十二个因素的应用程序</span><span class="sxs-lookup"><span data-stu-id="8af0e-160">Beyond the Twelve-Factor Application</span></span>](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)

- [<span data-ttu-id="8af0e-161">什么是基础结构即代码</span><span class="sxs-lookup"><span data-stu-id="8af0e-161">What is Infrastructure as Code</span></span>](/azure/devops/learn/what-is-infrastructure-as-code)

- [<span data-ttu-id="8af0e-162">Uber 工程的微部署：自信地部署</span><span class="sxs-lookup"><span data-stu-id="8af0e-162">Uber Engineering's Micro Deploy: Deploying Daily with Confidence</span></span>](https://eng.uber.com/micro-deploy/)

- [<span data-ttu-id="8af0e-163">Netflix 如何部署代码</span><span class="sxs-lookup"><span data-stu-id="8af0e-163">How Netflix Deploys Code</span></span>](https://www.infoq.com/news/2013/06/netflix/)

- [<span data-ttu-id="8af0e-164">缩放 WeChat 微服务的重载控制</span><span class="sxs-lookup"><span data-stu-id="8af0e-164">Overload Control for Scaling WeChat Microservices</span></span>](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf)

>[!div class="step-by-step"]
><span data-ttu-id="8af0e-165">[上一页](definition.md)
>[下一页](introduce-eshoponcontainers-reference-app.md)</span><span class="sxs-lookup"><span data-stu-id="8af0e-165">[Previous](definition.md)
[Next](introduce-eshoponcontainers-reference-app.md)</span></span>

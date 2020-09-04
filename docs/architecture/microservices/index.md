---
title: .NET 微服务。 适用于容器化 .NET 应用程序的体系结构
description: 适用于容器化 .NET 应用程序的 .NET 微服务体系结构 | 微服务可是模块化且可独立部署的服务。 （适用于 Linux 和 Windows）的 Docker 容器可将服务及其依赖项绑定到单个单元，使该单元在一个独立的环境中运行，因而可简化部署和测试。
ms.date: 09/02/2020
ms.openlocfilehash: aea5012fee102f388827d146043e69592e14f22b
ms.sourcegitcommit: b78018c850590dfc0348301e1748b779c28604cc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "89379130"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="facc2-105">.NET 微服务：适用于容器化 .NET 应用程序的体系结构</span><span class="sxs-lookup"><span data-stu-id="facc2-105">.NET Microservices: Architecture for Containerized .NET Applications</span></span>

![封面](./media/cover-small.png)

<span data-ttu-id="facc2-107">**版本 v3.1.2** - 已更新到 ASP.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="facc2-107">**EDITION v3.1.2** - Updated to ASP.NET Core 3.1</span></span>

<span data-ttu-id="facc2-108">本指南介绍如何使用容器开发基于微服务的应用程序并对其进行管理。</span><span class="sxs-lookup"><span data-stu-id="facc2-108">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="facc2-109">本指南探讨使用 .NET Core 和 Docker 容器的体系结构设计和实现方法。</span><span class="sxs-lookup"><span data-stu-id="facc2-109">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span>

<span data-ttu-id="facc2-110">为了更加轻松地开始使用，本指南重点介绍一个容器化和基于微服务的参考应用程序（用户可获取该应用程序）。</span><span class="sxs-lookup"><span data-stu-id="facc2-110">To make it easier to get started, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="facc2-111">可通过 [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub 存储库获取该参考应用程序。</span><span class="sxs-lookup"><span data-stu-id="facc2-111">The reference application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

## <a name="action-links"></a><span data-ttu-id="facc2-112">操作链接</span><span class="sxs-lookup"><span data-stu-id="facc2-112">Action links</span></span>

- <span data-ttu-id="facc2-113">此电子书还提供 PDF 格式（仅限英文）[下载](https://aka.ms/microservicesebook)</span><span class="sxs-lookup"><span data-stu-id="facc2-113">This e-book is also available in a PDF format (English version only) [Download](https://aka.ms/microservicesebook)</span></span>

- <span data-ttu-id="facc2-114">克隆参考应用程序 [GitHub 上的 eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) 或为其创建分支</span><span class="sxs-lookup"><span data-stu-id="facc2-114">Clone/Fork the reference application [eShopOnContainers on GitHub](https://github.com/dotnet-architecture/eShopOnContainers)</span></span>

- <span data-ttu-id="facc2-115">观看[第 9 频道上的介绍视频](https://aka.ms/microservices-video)</span><span class="sxs-lookup"><span data-stu-id="facc2-115">Watch the [introductory video on Channel 9](https://aka.ms/microservices-video)</span></span>

- <span data-ttu-id="facc2-116">立即了解[微服务体系结构](https://aka.ms/MicroservicesArchitecture)</span><span class="sxs-lookup"><span data-stu-id="facc2-116">Get to know the [Microservices Architecture](https://aka.ms/MicroservicesArchitecture) right away</span></span>

## <a name="introduction"></a><span data-ttu-id="facc2-117">介绍</span><span class="sxs-lookup"><span data-stu-id="facc2-117">Introduction</span></span>

<span data-ttu-id="facc2-118">企业通过使用容器，日益实现成本节约、解决部署问题并改进 DevOps 和生产操作。</span><span class="sxs-lookup"><span data-stu-id="facc2-118">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="facc2-119">通过创建 Azure Kubernetes 服务、Azure Service Fabric 等产品，同时与 Docker、Mesosphere 和 Kubernetes 等行业领先者合作，Microsoft 一直在推出适用于 Windows 和 Linux 的容器创新。</span><span class="sxs-lookup"><span data-stu-id="facc2-119">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Kubernetes Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="facc2-120">这些产品提供容器解决方案，可帮助公司以云的速度和规模生成并部署应用程序，而无需考虑其选用的平台或工具。</span><span class="sxs-lookup"><span data-stu-id="facc2-120">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="facc2-121">Docker 正在逐渐成为容器行业的事实标准，受到 Windows 和 Linux 生态系统领域最重要供应商的支持。</span><span class="sxs-lookup"><span data-stu-id="facc2-121">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="facc2-122">（Microsoft 是支持 Docker 的主要云供应商之一。）将来，Docker 可能会在云端或本地的任何数据中心普及。</span><span class="sxs-lookup"><span data-stu-id="facc2-122">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="facc2-123">此外，[microservices](https://martinfowler.com/articles/microservices.html)（微服务）体系结构兴起，成为分布式任务关键型应用程序的重要方法。</span><span class="sxs-lookup"><span data-stu-id="facc2-123">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="facc2-124">在基于微服务的体系结构中，应用程序在可独立开发、测试、部署和版本控制的一系列服务上生成。</span><span class="sxs-lookup"><span data-stu-id="facc2-124">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="facc2-125">关于本指南</span><span class="sxs-lookup"><span data-stu-id="facc2-125">About this guide</span></span>

<span data-ttu-id="facc2-126">本指南介绍如何使用容器开发基于微服务的应用程序并对其进行管理。</span><span class="sxs-lookup"><span data-stu-id="facc2-126">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="facc2-127">本指南探讨使用 .NET Core 和 Docker 容器的体系结构设计和实现方法。</span><span class="sxs-lookup"><span data-stu-id="facc2-127">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> <span data-ttu-id="facc2-128">为了更加轻松地开始使用容器和微服务，本指南重点介绍一个容器化和基于微服务的参考应用程序（用户可获取该应用程序）。</span><span class="sxs-lookup"><span data-stu-id="facc2-128">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="facc2-129">可通过 [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub 存储库获取该示例应用程序。</span><span class="sxs-lookup"><span data-stu-id="facc2-129">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="facc2-130">本指南主要在开发环境级别提供基础开发和体系结构指导，重点介绍以下两种技术：Docker 和 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="facc2-130">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET Core.</span></span> <span data-ttu-id="facc2-131">我们的目标是为用户在应用程序设计时提供指导，使用户无需将重点放在其生产环境的基础结构（云端或本地）上。</span><span class="sxs-lookup"><span data-stu-id="facc2-131">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="facc2-132">用户可在创建生产就绪的应用程序时，稍后制定有关基础结构的决策。</span><span class="sxs-lookup"><span data-stu-id="facc2-132">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="facc2-133">因此，本指南不区分基础结构，更侧重于考虑开发环境。</span><span class="sxs-lookup"><span data-stu-id="facc2-133">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="facc2-134">学习本指南后，接下来将了解 Microsoft Azure 上的生产就绪微服务。</span><span class="sxs-lookup"><span data-stu-id="facc2-134">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="version"></a><span data-ttu-id="facc2-135">Version</span><span class="sxs-lookup"><span data-stu-id="facc2-135">Version</span></span>

<span data-ttu-id="facc2-136">本指南已进行了修订，涵盖 .NET Core 3.1  版本以及与 .NET Core 3.1 同期的同一“批”技术（即 Azure 和其他第三方技术）的许多其他更新。</span><span class="sxs-lookup"><span data-stu-id="facc2-136">This guide has been revised to cover **.NET Core 3.1** version along with many additional updates related to the same “wave” of technologies (that is, Azure and additional third-party technologies) coinciding in time with the .NET Core 3.1 release.</span></span> <span data-ttu-id="facc2-137">这就是书本版本也更新到 3.1 的原因  。</span><span class="sxs-lookup"><span data-stu-id="facc2-137">That’s why the book version has also been updated to version **3.1**.</span></span>

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="facc2-138">本指南未涵盖的内容</span><span class="sxs-lookup"><span data-stu-id="facc2-138">What this guide does not cover</span></span>

<span data-ttu-id="facc2-139">本指南未涵盖应用程序生命周期、DevOps、CI/CD 管道或团队协作。</span><span class="sxs-lookup"><span data-stu-id="facc2-139">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="facc2-140">补充指南 [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook)（使用 Microsoft 平台和工具的容器化 Docker 应用程序的生命周期）重点介绍该主题。</span><span class="sxs-lookup"><span data-stu-id="facc2-140">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="facc2-141">此外，当前指南不提供实现 Azure 基础结构的详细信息，例如有关特定业务流程的信息。</span><span class="sxs-lookup"><span data-stu-id="facc2-141">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="facc2-142">其他资源</span><span class="sxs-lookup"><span data-stu-id="facc2-142">Additional resources</span></span>

- <span data-ttu-id="facc2-143">《使用 Microsoft 平台和工具的容器化 Docker 应用程序生命周期》  （可下载电子书）</span><span class="sxs-lookup"><span data-stu-id="facc2-143">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book)</span></span>  
    <https://aka.ms/dockerlifecycleebook>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="facc2-144">本指南的目标读者</span><span class="sxs-lookup"><span data-stu-id="facc2-144">Who should use this guide</span></span>

<span data-ttu-id="facc2-145">本指南的目标读者是不熟悉以下内容的开发人员和解决方案架构师：基于 Docker 的应用程序开发和基于微服务的架构。</span><span class="sxs-lookup"><span data-stu-id="facc2-145">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="facc2-146">若要了解如何使用 Microsoft 开发技术（特别是 .NET Core）和 Docker 容器架构、设计和实现概念验证应用程序，本指南是理想之选。</span><span class="sxs-lookup"><span data-stu-id="facc2-146">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET Core) and with Docker containers.</span></span>

<span data-ttu-id="facc2-147">如果企业架构师等技术决策制定者想要在综合了解体系结构和技术的基础上，作出有关新式和现代分布式应用程序应选择的方法的决策，则本指南也非常有用。</span><span class="sxs-lookup"><span data-stu-id="facc2-147">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="facc2-148">如何使用本指南</span><span class="sxs-lookup"><span data-stu-id="facc2-148">How to use this guide</span></span>

<span data-ttu-id="facc2-149">本指南的第一部分介绍 Docker 容器，探讨用作开发框架时如何在 .NET Core 和 .NET Framework 之间选择，并提供有关微服务的概述。</span><span class="sxs-lookup"><span data-stu-id="facc2-149">The first part of this guide introduces Docker containers, discusses how to choose between .NET Core and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="facc2-150">此内容适合希望大概了解而不关注代码实现细节的架构师和技术决策制定者。</span><span class="sxs-lookup"><span data-stu-id="facc2-150">This content is for architects and technical decision makers who want an overview but don't need to focus on code implementation details.</span></span>

<span data-ttu-id="facc2-151">本指南的第二部分从[基于 Docker 的应用程序的开发过程](./docker-application-development-process/index.md)一节开始。</span><span class="sxs-lookup"><span data-stu-id="facc2-151">The second part of the guide starts with the [Development process for Docker based applications](./docker-application-development-process/index.md) section.</span></span> <span data-ttu-id="facc2-152">重点介绍使用 .NET Core 和 Docker 实现应用程序的开发和微服务模式。</span><span class="sxs-lookup"><span data-stu-id="facc2-152">It focuses on the development and microservice patterns for implementing applications using .NET Core and Docker.</span></span> <span data-ttu-id="facc2-153">对于要重点了解代码以及模式和实现详细信息的开发人员和架构师，此部分最有吸引力。</span><span class="sxs-lookup"><span data-stu-id="facc2-153">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="facc2-154">相关微服务和基于容器的参考应用程序：eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="facc2-154">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="facc2-155">eShopOnContainers 应用程序是用于 .NET Core 和旨在使用 Docker 容器部署的微服务的开源参考应用。</span><span class="sxs-lookup"><span data-stu-id="facc2-155">The eShopOnContainers application is an open-source reference app for .NET Core and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="facc2-156">该应用程序包含多个子系统，包括多个网上商店 UI 前端（一个 Web MVC 应用、一个 Web SPA 和一个本机移动应用）。</span><span class="sxs-lookup"><span data-stu-id="facc2-156">The application consists of multiple subsystems, including several e-store UI front-ends (a Web MVC app, a Web SPA, and a native mobile app).</span></span> <span data-ttu-id="facc2-157">还包括用于所有所需服务器端操作的后端微服务和容器。</span><span class="sxs-lookup"><span data-stu-id="facc2-157">It also includes the back-end microservices and containers for all required server-side operations.</span></span>

<span data-ttu-id="facc2-158">应用程序的用途是展示体系结构模式。</span><span class="sxs-lookup"><span data-stu-id="facc2-158">The purpose of the application is to showcase architectural patterns.</span></span> <span data-ttu-id="facc2-159">**它不是可直接用于生产的模板**，无法启动实际应用程序。</span><span class="sxs-lookup"><span data-stu-id="facc2-159">**IT IS NOT A PRODUCTION-READY TEMPLATE** to start real-world applications.</span></span> <span data-ttu-id="facc2-160">事实上，应用程序处于永久 beta 状态，因为它还用来在出现有趣的新技术时对其进行测试。</span><span class="sxs-lookup"><span data-stu-id="facc2-160">In fact, the application is in a permanent beta state, as it's also used to test new potentially interesting technologies as they show up.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="facc2-161">向我们发送反馈！</span><span class="sxs-lookup"><span data-stu-id="facc2-161">Send us your feedback!</span></span>

<span data-ttu-id="facc2-162">本指南旨在帮助用户了解 .NET 中容器化应用程序和微服务的体系结构。</span><span class="sxs-lookup"><span data-stu-id="facc2-162">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="facc2-163">本指南和相关的参考应用程序会不断更新，欢迎你提供宝贵意见！</span><span class="sxs-lookup"><span data-stu-id="facc2-163">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="facc2-164">如有关于本指南的改进建议，请在 <https://aka.ms/ebookfeedback> 提交反馈。</span><span class="sxs-lookup"><span data-stu-id="facc2-164">If you have comments about how this guide can be improved, submit feedback at <https://aka.ms/ebookfeedback>.</span></span>

## <a name="credits"></a><span data-ttu-id="facc2-165">信用</span><span class="sxs-lookup"><span data-stu-id="facc2-165">Credits</span></span>

<span data-ttu-id="facc2-166">合著者：</span><span class="sxs-lookup"><span data-stu-id="facc2-166">Co-Authors:</span></span>

> <span data-ttu-id="facc2-167">**Cesar de la Torre**，Microsoft Corp .NET 产品团队的高级项目经理。</span><span class="sxs-lookup"><span data-stu-id="facc2-167">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="facc2-168">**Bill Wagner**，Microsoft Corp C+E 高级内容开发人员。</span><span class="sxs-lookup"><span data-stu-id="facc2-168">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="facc2-169">**Mike Rousos**，Microsoft DevDiv CAT 团队的主要软件工程师</span><span class="sxs-lookup"><span data-stu-id="facc2-169">**Mike Rousos**, Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="facc2-170">编辑：</span><span class="sxs-lookup"><span data-stu-id="facc2-170">Editors:</span></span>

> <span data-ttu-id="facc2-171">**Mike Pope**</span><span class="sxs-lookup"><span data-stu-id="facc2-171">**Mike Pope**</span></span>
>
> <span data-ttu-id="facc2-172">**Steve Hoag**</span><span class="sxs-lookup"><span data-stu-id="facc2-172">**Steve Hoag**</span></span>

<span data-ttu-id="facc2-173">参与者和审阅者：</span><span class="sxs-lookup"><span data-stu-id="facc2-173">Participants and reviewers:</span></span>

> <span data-ttu-id="facc2-174">**Jeffrey Ritcher**，Microsoft Azure 团队的合作伙伴软件工程师</span><span class="sxs-lookup"><span data-stu-id="facc2-174">**Jeffrey Richter**, Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="facc2-175">**Jimmy Bogard**，Headspring 的首席架构师</span><span class="sxs-lookup"><span data-stu-id="facc2-175">**Jimmy Bogard**, Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="facc2-176">**Udi Dahan**，Particular Software 的创始人兼 CEO</span><span class="sxs-lookup"><span data-stu-id="facc2-176">**Udi Dahan**, Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="facc2-177">**Jimmy Nilsson**，Factor10 的共同创始人兼 CEO</span><span class="sxs-lookup"><span data-stu-id="facc2-177">**Jimmy Nilsson**, Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="facc2-178">**Glenn Condron**，ASP.NET 团队的高级项目经理</span><span class="sxs-lookup"><span data-stu-id="facc2-178">**Glenn Condron**, Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="facc2-179">**Mark Fussell**，Microsoft Azure Service Fabric 团队的主要项目经理主管</span><span class="sxs-lookup"><span data-stu-id="facc2-179">**Mark Fussell**, Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="facc2-180">**Diego Vega**，Microsoft 实体框架团队的项目经理主管</span><span class="sxs-lookup"><span data-stu-id="facc2-180">**Diego Vega**, PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="facc2-181">**Barry Dorrans**，高级安全项目经理</span><span class="sxs-lookup"><span data-stu-id="facc2-181">**Barry Dorrans**, Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="facc2-182">**Rowan Miller**，Microsoft 高级项目经理</span><span class="sxs-lookup"><span data-stu-id="facc2-182">**Rowan Miller**, Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="facc2-183">**Ankit Asthana**，Microsoft .NET 团队的主要项目经理</span><span class="sxs-lookup"><span data-stu-id="facc2-183">**Ankit Asthana**, Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="facc2-184">**Scott Hunter**，Microsoft .NET 团队的合作伙伴总监项目经理</span><span class="sxs-lookup"><span data-stu-id="facc2-184">**Scott Hunter**, Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="facc2-185">Microsoft .NET 团队高级项目经理 Nish Anil </span><span class="sxs-lookup"><span data-stu-id="facc2-185">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="facc2-186">**Dylan Reisenberger**，Polly的架构师兼开发主管</span><span class="sxs-lookup"><span data-stu-id="facc2-186">**Dylan Reisenberger**, Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="facc2-187">**Steve "ardalis" Smith** - 软件设计师及培训师 - [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="facc2-187">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>
>
> <span data-ttu-id="facc2-188">**Ian Cooper**，Brighter 的编码架构师</span><span class="sxs-lookup"><span data-stu-id="facc2-188">**Ian Cooper**, Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="facc2-189">**Unai Zorrilla**，Plain Concepts 的架构师兼开发主管</span><span class="sxs-lookup"><span data-stu-id="facc2-189">**Unai Zorrilla**, Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="facc2-190">**Eduard Tomas**，Plain Concepts 的开发主管</span><span class="sxs-lookup"><span data-stu-id="facc2-190">**Eduard Tomas**, Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="facc2-191">**Ramon Tomas**，Plain Concepts 的开发者</span><span class="sxs-lookup"><span data-stu-id="facc2-191">**Ramon Tomas**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="facc2-192">**David Sanz**，Plain Concepts 的开发者</span><span class="sxs-lookup"><span data-stu-id="facc2-192">**David Sanz**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="facc2-193">**Javier Valero**，Grupo Solutio 的首席运营官</span><span class="sxs-lookup"><span data-stu-id="facc2-193">**Javier Valero**, Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="facc2-194">**Pierre Millet**，Microsoft 高级顾问</span><span class="sxs-lookup"><span data-stu-id="facc2-194">**Pierre Millet**, Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="facc2-195">**Michael Friis**，Docker Inc 的产品经理</span><span class="sxs-lookup"><span data-stu-id="facc2-195">**Michael Friis**, Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="facc2-196">**Charles Lowell**，Microsoft VS CAT 团队的软件工程师</span><span class="sxs-lookup"><span data-stu-id="facc2-196">**Charles Lowell**, Software Engineer, VS CAT team, Microsoft</span></span>
>
> <span data-ttu-id="facc2-197">**Miguel Veloso**，Plain Concepts 的软件开发工程师</span><span class="sxs-lookup"><span data-stu-id="facc2-197">**Miguel Veloso**, Software Development Engineer at Plain Concepts</span></span>
>
> <span data-ttu-id="facc2-198">Sumit Ghosh，Neudesic 的首席顾问</span><span class="sxs-lookup"><span data-stu-id="facc2-198">**Sumit Ghosh**, Principal Consultant at Neudesic</span></span>

## <a name="copyright"></a><span data-ttu-id="facc2-199">Copyright</span><span class="sxs-lookup"><span data-stu-id="facc2-199">Copyright</span></span>

<span data-ttu-id="facc2-200">发布者</span><span class="sxs-lookup"><span data-stu-id="facc2-200">PUBLISHED BY</span></span>

<span data-ttu-id="facc2-201">Microsoft 开发人员部门、.NET 和 Visual Studio 产品团队</span><span class="sxs-lookup"><span data-stu-id="facc2-201">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="facc2-202">Microsoft Corporation 的一个部门</span><span class="sxs-lookup"><span data-stu-id="facc2-202">A division of Microsoft Corporation</span></span>

<span data-ttu-id="facc2-203">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="facc2-203">One Microsoft Way</span></span>

<span data-ttu-id="facc2-204">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="facc2-204">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="facc2-205">版权所有 © 2020 Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="facc2-205">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="facc2-206">保留所有权利。</span><span class="sxs-lookup"><span data-stu-id="facc2-206">All rights reserved.</span></span> <span data-ttu-id="facc2-207">未经发布者书面许可，不得以任何形式或任何方式复制或传播本书中的任何内容。</span><span class="sxs-lookup"><span data-stu-id="facc2-207">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="facc2-208">本书“按原样”提供，表达作者的观点和看法。</span><span class="sxs-lookup"><span data-stu-id="facc2-208">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="facc2-209">本书中表达的观点、看法和信息（包括 URL 和其他 Internet 网站引用）如有更改，恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="facc2-209">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="facc2-210">本书中提及的一些示例仅用于说明，纯属虚构。</span><span class="sxs-lookup"><span data-stu-id="facc2-210">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="facc2-211">不存在任何实际关联或联系，请勿妄加推断。</span><span class="sxs-lookup"><span data-stu-id="facc2-211">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="facc2-212">Microsoft 和 <https://www.microsoft.com> 上“商标”网页列出的商标是 Microsoft 集团公司的商标。</span><span class="sxs-lookup"><span data-stu-id="facc2-212">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="facc2-213">Mac 和 macOS 是 Apple Inc. 的商标</span><span class="sxs-lookup"><span data-stu-id="facc2-213">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="facc2-214">Docker 的鲸鱼徽标是 Docker Inc. 的注册商标经许可方可使用。</span><span class="sxs-lookup"><span data-stu-id="facc2-214">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="facc2-215">所有其他标记和徽标均为其各自所有者的财产。</span><span class="sxs-lookup"><span data-stu-id="facc2-215">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="facc2-216">下一页</span><span class="sxs-lookup"><span data-stu-id="facc2-216">Next</span></span>](container-docker-introduction/index.md)

---
title: 构建方法 - 无服务器应用
description: 介绍如何构建方法来生成基于云的企业应用程序（从 N 层体系结构到无服务器）。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 0ab84d1f3425c1fda787756b73fd8315fe6d4231
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171970"
---
# <a name="architecture-approaches"></a><span data-ttu-id="90c0b-103">体系结构方法</span><span class="sxs-lookup"><span data-stu-id="90c0b-103">Architecture approaches</span></span>

<span data-ttu-id="90c0b-104">了解构建企业应用程序的现有方法有助于澄清无服务器所扮演的角色。</span><span class="sxs-lookup"><span data-stu-id="90c0b-104">Understanding existing approaches to architecting enterprise apps helps clarify the role played by serverless.</span></span> <span data-ttu-id="90c0b-105">许多方法和模式在许多软件开发过程中都进行了发展，它们都具有自己的优点和缺点。</span><span class="sxs-lookup"><span data-stu-id="90c0b-105">There are many approaches and patterns that evolved over decades of software development, and all have their own pros and cons.</span></span> <span data-ttu-id="90c0b-106">在许多情况下，终极解决方案可能不涉及确定单一方法，但可能会集成多种方法。</span><span class="sxs-lookup"><span data-stu-id="90c0b-106">In many cases, the ultimate solution may not involve deciding on a single approach but may integrate several approaches.</span></span> <span data-ttu-id="90c0b-107">迁移方案通常涉及通过混合方法从一种体系结构方法切换到另一种方法。</span><span class="sxs-lookup"><span data-stu-id="90c0b-107">Migration scenarios often involve shifting from one architecture approach to another through a hybrid approach.</span></span>

<span data-ttu-id="90c0b-108">本章概述了企业应用程序的逻辑体系结构和物理体系结构模式。</span><span class="sxs-lookup"><span data-stu-id="90c0b-108">This chapter provides an overview of both logical and physical architecture patterns for enterprise applications.</span></span>

## <a name="architecture-patterns"></a><span data-ttu-id="90c0b-109">体系结构模式</span><span class="sxs-lookup"><span data-stu-id="90c0b-109">Architecture patterns</span></span>

<span data-ttu-id="90c0b-110">现代业务应用程序遵循各种体系结构模式。</span><span class="sxs-lookup"><span data-stu-id="90c0b-110">Modern business applications follow a variety of architecture patterns.</span></span> <span data-ttu-id="90c0b-111">本部分提供对常见模式的调查。</span><span class="sxs-lookup"><span data-stu-id="90c0b-111">This section represents a survey of common patterns.</span></span> <span data-ttu-id="90c0b-112">此处列出的模式并不一定是所有最佳做法，但阐释了不同的方法。</span><span class="sxs-lookup"><span data-stu-id="90c0b-112">The patterns listed here aren't necessarily all best practices, but illustrate different approaches.</span></span>

<span data-ttu-id="90c0b-113">有关详细信息，请参阅 [Azure 应用程序体系结构指南](/azure/architecture/guide/)。</span><span class="sxs-lookup"><span data-stu-id="90c0b-113">For more information, see [Azure application architecture guide](/azure/architecture/guide/).</span></span>

## <a name="monoliths"></a><span data-ttu-id="90c0b-114">整体模式</span><span class="sxs-lookup"><span data-stu-id="90c0b-114">Monoliths</span></span>

<span data-ttu-id="90c0b-115">许多业务应用程序都遵循整体模式。</span><span class="sxs-lookup"><span data-stu-id="90c0b-115">Many business applications follow a monolith pattern.</span></span> <span data-ttu-id="90c0b-116">旧应用程序通常实现为整体模式。</span><span class="sxs-lookup"><span data-stu-id="90c0b-116">Legacy applications are often implemented as monoliths.</span></span> <span data-ttu-id="90c0b-117">在整体模式下，所有应用程序问题都包含在一个部署中。</span><span class="sxs-lookup"><span data-stu-id="90c0b-117">In the monolith pattern, all application concerns are contained in a single deployment.</span></span> <span data-ttu-id="90c0b-118">从用户界面到数据库调用的所有内容都包含在相同的代码库中。</span><span class="sxs-lookup"><span data-stu-id="90c0b-118">Everything from user interface to database calls is included in the same codebase.</span></span>

![整体体系结构](./media/monolith-architecture.png)

<span data-ttu-id="90c0b-120">整体方法有以下几个优点。</span><span class="sxs-lookup"><span data-stu-id="90c0b-120">There are several advantages to the monolith approach.</span></span> <span data-ttu-id="90c0b-121">它通常可以轻松地下拉一个基本代码并开始工作。</span><span class="sxs-lookup"><span data-stu-id="90c0b-121">It's often easy to pull down a single code base and start working.</span></span> <span data-ttu-id="90c0b-122">加速时间可能更少，并且创建测试环境就像提供一个新副本一样简单。</span><span class="sxs-lookup"><span data-stu-id="90c0b-122">Ramp up time may be less, and creating test environments is as simple as providing a new copy.</span></span> <span data-ttu-id="90c0b-123">整体模式可设计为包括多个组件和应用程序。</span><span class="sxs-lookup"><span data-stu-id="90c0b-123">The monolith may be designed to include multiple components and applications.</span></span>

<span data-ttu-id="90c0b-124">遗憾的是，整体模式往往会大规模分解。</span><span class="sxs-lookup"><span data-stu-id="90c0b-124">Unfortunately, the monolith pattern tends to break down at scale.</span></span> <span data-ttu-id="90c0b-125">整体方法的主要缺点包括：</span><span class="sxs-lookup"><span data-stu-id="90c0b-125">Major disadvantages of the monolith approach include:</span></span>

- <span data-ttu-id="90c0b-126">很难在同一基本代码中并行运行。</span><span class="sxs-lookup"><span data-stu-id="90c0b-126">Difficult to work in parallel in the same code base.</span></span>
- <span data-ttu-id="90c0b-127">任何更改（不管是多么简单）都需要部署整个应用程序的新版本。</span><span class="sxs-lookup"><span data-stu-id="90c0b-127">Any change, no matter how trivial, requires deploying a new version of the entire application.</span></span>
- <span data-ttu-id="90c0b-128">重构可能会影响整个应用程序。</span><span class="sxs-lookup"><span data-stu-id="90c0b-128">Refactoring potentially impacts the entire application.</span></span>
- <span data-ttu-id="90c0b-129">通常，唯一的缩放解决方案是创建整体模式的多个资源密集型副本。</span><span class="sxs-lookup"><span data-stu-id="90c0b-129">Often the only solution to scale is to create multiple, resource-intensive copies of the monolith.</span></span>
- <span data-ttu-id="90c0b-130">在获取系统扩展或其他系统时，集成可能会很困难。</span><span class="sxs-lookup"><span data-stu-id="90c0b-130">As systems expand or other systems are acquired, integration can be difficult.</span></span>
- <span data-ttu-id="90c0b-131">由于需要配置整个整体模式，因此可能很难测试。</span><span class="sxs-lookup"><span data-stu-id="90c0b-131">It may be difficult to test due to the need to configure the entire monolith.</span></span>
- <span data-ttu-id="90c0b-132">代码重用很有挑战性，而其他应用程序最终拥有自己的代码副本。</span><span class="sxs-lookup"><span data-stu-id="90c0b-132">Code reuse is challenging and often other apps end up having their own copies of code.</span></span>

<span data-ttu-id="90c0b-133">许多企业都将云视为迁移整体应用程序、同时将其重构为更多可用模式的机会。</span><span class="sxs-lookup"><span data-stu-id="90c0b-133">Many businesses look to the cloud as an opportunity to migrate monolith applications and at the same time refactor them to more usable patterns.</span></span> <span data-ttu-id="90c0b-134">通常，分解各个应用程序和组件以允许单独维护、部署和缩放。</span><span class="sxs-lookup"><span data-stu-id="90c0b-134">It's common to break out the individual applications and components to allow them to be maintained, deployed, and scaled separately.</span></span>

## <a name="n-layer-applications"></a><span data-ttu-id="90c0b-135">N 层应用程序</span><span class="sxs-lookup"><span data-stu-id="90c0b-135">N-Layer applications</span></span>

<span data-ttu-id="90c0b-136">N 层应用程序将应用程序逻辑分区到特定的层。</span><span class="sxs-lookup"><span data-stu-id="90c0b-136">N-layer application partition application logic into specific layers.</span></span> <span data-ttu-id="90c0b-137">最常见层包括：</span><span class="sxs-lookup"><span data-stu-id="90c0b-137">The most common layers include:</span></span>

- <span data-ttu-id="90c0b-138">用户界面</span><span class="sxs-lookup"><span data-stu-id="90c0b-138">User interface</span></span>
- <span data-ttu-id="90c0b-139">业务逻辑</span><span class="sxs-lookup"><span data-stu-id="90c0b-139">Business logic</span></span>
- <span data-ttu-id="90c0b-140">数据访问</span><span class="sxs-lookup"><span data-stu-id="90c0b-140">Data access</span></span>

<span data-ttu-id="90c0b-141">其他层可能包括中间件、批处理和 API。</span><span class="sxs-lookup"><span data-stu-id="90c0b-141">Other layers may include middleware, batch processing, and API.</span></span> <span data-ttu-id="90c0b-142">请注意，层是合乎逻辑的。</span><span class="sxs-lookup"><span data-stu-id="90c0b-142">It's important to note the layers are logical.</span></span> <span data-ttu-id="90c0b-143">尽管它们是隔离开发的，但它们可能都部署到相同的目标平台。</span><span class="sxs-lookup"><span data-stu-id="90c0b-143">Although they're developed in isolation, they may all be deployed to the same target platform.</span></span>

![N 层体系结构](./media/n-layer-architecture.png)

<span data-ttu-id="90c0b-145">N 层方法有以下几个优点，包括：</span><span class="sxs-lookup"><span data-stu-id="90c0b-145">There are several advantages to the N-Layer approach, including:</span></span>

- <span data-ttu-id="90c0b-146">重构与层隔离。</span><span class="sxs-lookup"><span data-stu-id="90c0b-146">Refactoring is isolated to a layer.</span></span>
- <span data-ttu-id="90c0b-147">团队可以独立生成、测试、部署和维护单独的层。</span><span class="sxs-lookup"><span data-stu-id="90c0b-147">Teams can independently build, test, deploy, and maintain separate layers.</span></span>
- <span data-ttu-id="90c0b-148">层可以换出，例如，数据层可以访问多个数据库，而无需对 UI 层进行更改。</span><span class="sxs-lookup"><span data-stu-id="90c0b-148">Layers can be swapped out, for example the data layer may access multiple databases without requiring changes to the UI layer.</span></span>

<span data-ttu-id="90c0b-149">无服务器可用于实现一个或多个层。</span><span class="sxs-lookup"><span data-stu-id="90c0b-149">Serverless may be used to implement one or more layers.</span></span>

## <a name="microservices"></a><span data-ttu-id="90c0b-150">微服务</span><span class="sxs-lookup"><span data-stu-id="90c0b-150">Microservices</span></span>

<span data-ttu-id="90c0b-151">**[微服务](/azure/architecture/guide/architecture-styles/microservices)** 体系结构包含的常见特征包括：</span><span class="sxs-lookup"><span data-stu-id="90c0b-151">**[Microservices](/azure/architecture/guide/architecture-styles/microservices)** architectures contain common characteristics that include:</span></span>

- <span data-ttu-id="90c0b-152">应用程序由多个小型服务组成。</span><span class="sxs-lookup"><span data-stu-id="90c0b-152">Applications are composed of several small services.</span></span>
- <span data-ttu-id="90c0b-153">每个服务都在自己的进程中运行。</span><span class="sxs-lookup"><span data-stu-id="90c0b-153">Each service runs in its own process.</span></span>
- <span data-ttu-id="90c0b-154">服务围绕业务领域进行调整。</span><span class="sxs-lookup"><span data-stu-id="90c0b-154">Services are aligned around business domains.</span></span>
- <span data-ttu-id="90c0b-155">服务通过轻型 API 通信，通常使用 HTTP 作为传输。</span><span class="sxs-lookup"><span data-stu-id="90c0b-155">Services communicate over lightweight APIs, typically using HTTP as the transport.</span></span>
- <span data-ttu-id="90c0b-156">服务可独立部署和升级。</span><span class="sxs-lookup"><span data-stu-id="90c0b-156">Services can be deployed and upgraded independently.</span></span>
- <span data-ttu-id="90c0b-157">服务不依赖于单个数据存储区。</span><span class="sxs-lookup"><span data-stu-id="90c0b-157">Services aren't dependent on a single data store.</span></span>
- <span data-ttu-id="90c0b-158">系统设计时考虑到了故障，即使某些服务发生故障，应用程序仍可能运行。</span><span class="sxs-lookup"><span data-stu-id="90c0b-158">The system is designed with failure in mind, and the app may still run even when certain services fail.</span></span>

<span data-ttu-id="90c0b-159">微服务不必与其他体系结构方法互相排斥。</span><span class="sxs-lookup"><span data-stu-id="90c0b-159">Microservices don't have to be mutually exclusive to other architecture approaches.</span></span> <span data-ttu-id="90c0b-160">例如，N 层体系结构可以使用微服务作为中间层。</span><span class="sxs-lookup"><span data-stu-id="90c0b-160">For example, an N-Tier architecture may use microservices for the middle tier.</span></span> <span data-ttu-id="90c0b-161">还可以通过多种方式从 IIS 主机上的虚拟目录到容器实现微服务。</span><span class="sxs-lookup"><span data-stu-id="90c0b-161">It's also possible to implement microservices in a variety of ways, from virtual directories on IIS hosts to containers.</span></span> <span data-ttu-id="90c0b-162">微服务的特征使它们特别适用于无服务器实现。</span><span class="sxs-lookup"><span data-stu-id="90c0b-162">The characteristics of microservices make them especially ideal for serverless implementations.</span></span>

![微服务体系结构](./media/microservices-architecture.png)

<span data-ttu-id="90c0b-164">微服务体系结构的优点包括：</span><span class="sxs-lookup"><span data-stu-id="90c0b-164">The pros of microservices architectures include:</span></span>

- <span data-ttu-id="90c0b-165">重构通常与单个服务隔离。</span><span class="sxs-lookup"><span data-stu-id="90c0b-165">Refactoring is often isolated to a single service.</span></span>
- <span data-ttu-id="90c0b-166">服务可以彼此独立地升级。</span><span class="sxs-lookup"><span data-stu-id="90c0b-166">Services can be upgraded independently of each other.</span></span>
- <span data-ttu-id="90c0b-167">可针对单个服务的需求优化复原能力和弹性。</span><span class="sxs-lookup"><span data-stu-id="90c0b-167">Resiliency and elasticity can be tuned to the demands of individual services.</span></span>
- <span data-ttu-id="90c0b-168">开发可以跨不同的团队和平台并行发生。</span><span class="sxs-lookup"><span data-stu-id="90c0b-168">Development can happen in parallel across disparate teams and platforms.</span></span>
- <span data-ttu-id="90c0b-169">为隔离服务编写综合测试更加轻松。</span><span class="sxs-lookup"><span data-stu-id="90c0b-169">It's easier to write comprehensive tests for isolated services.</span></span>

<span data-ttu-id="90c0b-170">微服务带来了自己的挑战，包括：</span><span class="sxs-lookup"><span data-stu-id="90c0b-170">Microservices come with their own challenges, including:</span></span>

- <span data-ttu-id="90c0b-171">确定哪些服务可用，以及如何调用它们。</span><span class="sxs-lookup"><span data-stu-id="90c0b-171">Determining what services are available and how to call them.</span></span>
- <span data-ttu-id="90c0b-172">管理服务的生命周期。</span><span class="sxs-lookup"><span data-stu-id="90c0b-172">Managing the lifecycle of services.</span></span>
- <span data-ttu-id="90c0b-173">了解服务在整个应用程序中的配合方式。</span><span class="sxs-lookup"><span data-stu-id="90c0b-173">Understanding how services fit together in the overall application.</span></span>
- <span data-ttu-id="90c0b-174">跨不同服务进行完全系统调用测试。</span><span class="sxs-lookup"><span data-stu-id="90c0b-174">Full system testing of calls made across disparate services.</span></span>

<span data-ttu-id="90c0b-175">最终推出解决方案以解决所有这些挑战，包括利用稍后讨论的无服务器的好处。</span><span class="sxs-lookup"><span data-stu-id="90c0b-175">Ultimately there are solutions to address all of these challenges, including tapping into the benefits of serverless that are discussed later.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="90c0b-176">[上一页](index.md)
>[下一页](architecture-deployment-approaches.md)</span><span class="sxs-lookup"><span data-stu-id="90c0b-176">[Previous](index.md)
[Next](architecture-deployment-approaches.md)</span></span>

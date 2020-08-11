---
title: 使用 Microsoft 工具的 Docker 应用程序 DevOps 工作流
description: 通过 Microsoft 工具和 Microsoft 平台及工具 DevOps 工作流实现容器化的 Docker 应用程序生命周期
ms.date: 08/06/2020
ms.openlocfilehash: 30c5066fa90d8792d8eef8f760dc63c00ce32130
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915201"
---
# <a name="docker-application-devops-workflow-with-microsoft-tools"></a><span data-ttu-id="a95d2-103">使用 Microsoft 工具的 Docker 应用程序 DevOps 工作流</span><span class="sxs-lookup"><span data-stu-id="a95d2-103">Docker application DevOps workflow with Microsoft tools</span></span>

<span data-ttu-id="a95d2-104">*Microsoft Visual Studio、Azure DevOps Services、Team Foundation Server 和 Azure Monitor 实现了一个面向开发和 IT 操作的综合生态系统，它向你的团队提供工具来管理项目并快速构建、测试和部署容器化应用程序。*</span><span class="sxs-lookup"><span data-stu-id="a95d2-104">*Microsoft Visual Studio, Azure DevOps Services, Team Foundation Server, and Azure Monitor provide a comprehensive ecosystem for development and IT operations that give your team the tools to manage projects and rapidly build, test, and deploy containerized applications.*</span></span>

<span data-ttu-id="a95d2-105">借助云端的 Visual Studio 和 Azure DevOps Services，还有本地的 Team Foundation Server，开发团队可高效地构建、测试和发布面向 Windows 或 Linux 的容器化应用程序。</span><span class="sxs-lookup"><span data-stu-id="a95d2-105">With Visual Studio and Azure DevOps Services in the cloud, along with Team Foundation Server on-premises, development teams can productively build, test, and release containerized applications that target either Windows or Linux.</span></span>

<span data-ttu-id="a95d2-106">Microsoft 工具可通过全局生成和持续集成 (CI)，还有通过 Azure DevOps Services 进行的测试，来针对容器化应用程序的特定实现（Docker、.NET Core 或与其他平台的任何组合）实现管道自动化，从而持续部署 (CD) 到 Docker 环境（开发、过渡、生产），并通过 Azure Monitor 将有关服务的分析信息传递给开发团队。</span><span class="sxs-lookup"><span data-stu-id="a95d2-106">Microsoft tools can automate the pipeline for specific implementations of containerized applications—Docker, .NET Core, or any combination with other platforms—from global builds and Continuous Integration (CI) and tests with Azure DevOps Services or Team Foundation Server, to Continuous Deployment (CD) to Docker environments (Development, Staging, Production), and to transmit analytics information about the services to the development team through Azure Monitor.</span></span> <span data-ttu-id="a95d2-107">每个代码提交都能启动生成 (CI) 过程并自动将服务部署到特定的容器化环境 (CD)。</span><span class="sxs-lookup"><span data-stu-id="a95d2-107">Every code commit can initiate a build (CI) and automatically deploy the services to specific containerized environments (CD).</span></span>

<span data-ttu-id="a95d2-108">开发者和测试者可以使用 Microsoft Azure 中的模板快速轻松地配置生产环境，如基于 Docker 的开发和测试环境。</span><span class="sxs-lookup"><span data-stu-id="a95d2-108">Developers and testers can easily and quickly provision production-like development and test environments based on Docker by using templates in Microsoft Azure.</span></span>

<span data-ttu-id="a95d2-109">容器化应用程序开发的复杂度根据业务复杂度和可伸缩性需要逐步增加。</span><span class="sxs-lookup"><span data-stu-id="a95d2-109">The complexity of containerized application development increases steadily depending on the business complexity and scalability needs.</span></span> <span data-ttu-id="a95d2-110">这种复杂性的一个很好的例子就是基于微服务体系结构的应用程序。</span><span class="sxs-lookup"><span data-stu-id="a95d2-110">A good example of this complexity are applications based on microservices architectures.</span></span> <span data-ttu-id="a95d2-111">要在此类环境中成功操作，你的项目必须自动处理整个生命周期 - 不仅是生成和部署，还必须收集遥测数据并管理版本。</span><span class="sxs-lookup"><span data-stu-id="a95d2-111">To succeed in such an environment, your project must automate the entire life cycle—not only the build and deployment, but it also must manage versions along with the collection of telemetry.</span></span> <span data-ttu-id="a95d2-112">Azure DevOps Service 和 Azure 提供了以下功能：</span><span class="sxs-lookup"><span data-stu-id="a95d2-112">Azure DevOps Services and Azure offer the following capabilities:</span></span>

- <span data-ttu-id="a95d2-113">Azure DevOps Services/Team Foundation Server 源代码管理（基于 Git 或 Team Foundation 版本控制）、敏捷规划（支持 Agile、Scrum 和 CMMI）、CI、发布管理，以及适合敏捷团队的其他工具。</span><span class="sxs-lookup"><span data-stu-id="a95d2-113">Azure DevOps Services/Team Foundation Server source code management (based on Git or Team Foundation Version Control), Agile planning (Agile, Scrum, and CMMI are supported), CI, release management, and other tools for Agile teams.</span></span>

- <span data-ttu-id="a95d2-114">Azure DevOps Services 和 Team Foundation Server 带有一个强大且在不断扩充的生态系统，它包含第一方和第三方扩展，可用于轻松构造面向微服务的 CI、生成、测试、交付和发布管理管道。</span><span class="sxs-lookup"><span data-stu-id="a95d2-114">Azure DevOps Services and Team Foundation Server include a powerful and growing ecosystem of first and third-party extensions with which you easily can construct a CI, build, test, delivery, and release management pipeline for microservices.</span></span>

- <span data-ttu-id="a95d2-115">在 Azure DevOps Services 中作为生成管道的一部分运行自动测试。</span><span class="sxs-lookup"><span data-stu-id="a95d2-115">Run automated tests as part of your build pipeline in Azure DevOps Services.</span></span>

- <span data-ttu-id="a95d2-116">Azure DevOps Services 可通过交付到多个环境改善 DevOps 生命周期，这不仅是针对生产环境，还针对 A/B 试验和[金丝雀版本](https://martinfowler.com/bliki/CanaryRelease.html)等测试。</span><span class="sxs-lookup"><span data-stu-id="a95d2-116">Azure DevOps Services can tighten the DevOps life cycle with delivery to multiple environments, not just for production environments, but also for testing, including A/B experimentation, [canary releases](https://martinfowler.com/bliki/CanaryRelease.html), and so on.</span></span>

- <span data-ttu-id="a95d2-117">组织可使用 Azure Resource Manager 和熟悉的工具，通过 Azure 容器注册表中存储的专用映像和 Azure 组件（数据、PaaS 等）的任何依赖项轻松地预配 Docker 容器。</span><span class="sxs-lookup"><span data-stu-id="a95d2-117">Organizations easily can provision Docker containers from private images stored in Azure Container Registry along with any dependency on Azure components (Data, PaaS, etc.) using Azure Resource Manager templates with tools they're already comfortable with.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a95d2-118">[上一页](../design-develop-containerized-apps/build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
>[下一页](docker-application-outer-loop-devops-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="a95d2-118">[Previous](../design-develop-containerized-apps/build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
[Next](docker-application-outer-loop-devops-workflow.md)</span></span>

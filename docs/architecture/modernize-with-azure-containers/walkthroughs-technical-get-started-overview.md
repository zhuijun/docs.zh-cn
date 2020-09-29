---
title: 演练和技术入门概述
description: 通过 Azure 云和 Windows 容器现代化现有 .NET 应用程序 | 演练和技术入门概述
ms.date: 04/28/2018
ms.openlocfilehash: 98d33b13d2b28bfe1c35894df45e525cff0520c1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172139"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="2813b-103">演练和技术入门概述</span><span class="sxs-lookup"><span data-stu-id="2813b-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="2813b-104">为了限制此电子书的大小，GitHub 存储库中提供了其他技术文档和完整演练。</span><span class="sxs-lookup"><span data-stu-id="2813b-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="2813b-105">本章中所述的联机演练系列介绍了基于 Windows 容器和部署到 Azure 的多个环境的分步设置。</span><span class="sxs-lookup"><span data-stu-id="2813b-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="2813b-106">以下部分介绍每个演练的具体内容、目标和高级构想，并提供所涉及任务的关系图。</span><span class="sxs-lookup"><span data-stu-id="2813b-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="2813b-107">可以在 <https://github.com/dotnet-architecture/eShopModernizing/wiki> 的 eShopModernizing 应用 GitHub 存储库 wiki 中获取演练本身  。</span><span class="sxs-lookup"><span data-stu-id="2813b-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at <https://github.com/dotnet-architecture/eShopModernizing/wiki>.</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="2813b-108">技术演练列表</span><span class="sxs-lookup"><span data-stu-id="2813b-108">Technical walkthrough list</span></span>

<span data-ttu-id="2813b-109">以下入门演练提供示例应用（可以使用容器进行直接迁移，然后使用 Azure 中的多个部署选项进行移动）的一致且全面的技术指南。</span><span class="sxs-lookup"><span data-stu-id="2813b-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="2813b-110">以下每个演练都使用新的示例 eShopLegacy 和 eShopModernizing 应用，这些应用可从 <https://github.com/dotnet-architecture/eShopModernizing> 的 GitHub 中获得。</span><span class="sxs-lookup"><span data-stu-id="2813b-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at <https://github.com/dotnet-architecture/eShopModernizing>.</span></span>

- <span data-ttu-id="2813b-111">**eShop 旧版应用（要现代化的基准应用）的教程**</span><span class="sxs-lookup"><span data-stu-id="2813b-111">**Tour of eShop legacy apps (baseline apps to modernize)**</span></span>

- <span data-ttu-id="2813b-112">**使用 Windows 容器容器化现有 ASP.NET Web 应用（WebForms 和 MVC）**</span><span class="sxs-lookup"><span data-stu-id="2813b-112">**Containerize your existing ASP.NET web apps (WebForms & MVC) with Windows Containers**</span></span>

- <span data-ttu-id="2813b-113">**使用 Windows 容器容器化现有 WCF 服务（N 层应用）**</span><span class="sxs-lookup"><span data-stu-id="2813b-113">**Containerize your existing WCF services (N-Tier apps) with Windows Containers**</span></span>

- <span data-ttu-id="2813b-114">**将基于 Windows 容器的应用部署到 Azure VM**</span><span class="sxs-lookup"><span data-stu-id="2813b-114">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="2813b-115">**将基于 Windows 容器的应用部署到 Azure 容器服务中的 Kubernetes**</span><span class="sxs-lookup"><span data-stu-id="2813b-115">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="2813b-116">演练 1：eShop 旧版应用的教程</span><span class="sxs-lookup"><span data-stu-id="2813b-116">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="2813b-117">技术演练可用性</span><span class="sxs-lookup"><span data-stu-id="2813b-117">Technical walkthrough availability</span></span>

<span data-ttu-id="2813b-118">eShopModernizing GitHub 存储库 wiki 中提供了完整的技术演练：</span><span class="sxs-lookup"><span data-stu-id="2813b-118">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="2813b-119">eShopModernizing wiki 演练</span><span class="sxs-lookup"><span data-stu-id="2813b-119">eShopModernizing wiki walkthroughs</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a><span data-ttu-id="2813b-120">概述</span><span class="sxs-lookup"><span data-stu-id="2813b-120">Overview</span></span>

<span data-ttu-id="2813b-121">在本演练中，可以浏览三个示例旧版应用程序的初始实现。</span><span class="sxs-lookup"><span data-stu-id="2813b-121">In this walkthrough, you can explore the initial implementation of three sample legacy applications.</span></span> <span data-ttu-id="2813b-122">前两个示例 Web 应用具有整体式体系结构，并且是使用经典 ASP.NET 创建的。</span><span class="sxs-lookup"><span data-stu-id="2813b-122">The first two sample web apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="2813b-123">第一个应用程序基于 ASP.NET 4.x MVC；第二个应用程序基于 ASP.NET 4.x Web Forms。</span><span class="sxs-lookup"><span data-stu-id="2813b-123">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span>
<span data-ttu-id="2813b-124">第三个应用是由客户端 WinForms 应用和服务器端 [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) 服务组成的 3 层应用。</span><span class="sxs-lookup"><span data-stu-id="2813b-124">The third app is a 3-Tier app composed by a client WinForms app and a server-side [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span></span>

<span data-ttu-id="2813b-125">[eShopModernizing GitHub 存储库](https://github.com/dotnet-architecture/eShopModernizing)中提供了所有这些应用程序。</span><span class="sxs-lookup"><span data-stu-id="2813b-125">All these applications are available at the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

### <a name="goals"></a><span data-ttu-id="2813b-126">目标</span><span class="sxs-lookup"><span data-stu-id="2813b-126">Goals</span></span>

<span data-ttu-id="2813b-127">本演练的主要目的只是熟悉这些应用及其代码和配置。</span><span class="sxs-lookup"><span data-stu-id="2813b-127">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="2813b-128">可以配置应用，使其生成并使用模拟数据（而无需使用 SQL 数据库）进行测试。</span><span class="sxs-lookup"><span data-stu-id="2813b-128">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="2813b-129">此可选配置以分离的方式基于依赖项注入。</span><span class="sxs-lookup"><span data-stu-id="2813b-129">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario-1-aspnet-web-apps"></a><span data-ttu-id="2813b-130">应用场景 1：ASP.NET Web 应用</span><span class="sxs-lookup"><span data-stu-id="2813b-130">Scenario 1: ASP.NET Web apps</span></span>

<span data-ttu-id="2813b-131">下图显示了原始旧版 ASP.NET Web 应用程序的简单方案。</span><span class="sxs-lookup"><span data-stu-id="2813b-131">The figure below shows the simple scenario of the original legacy ASP.NET web applications.</span></span>

![原始旧版 ASP.NET Web 应用程序的简单体系结构方案](./media/image5-1.png)

<span data-ttu-id="2813b-133">从业务域角度来看，这两个应用提供相同的目录管理功能。</span><span class="sxs-lookup"><span data-stu-id="2813b-133">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="2813b-134">eShop 企业团队的成员将使用该应用查看和编辑产品目录。</span><span class="sxs-lookup"><span data-stu-id="2813b-134">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span>

<span data-ttu-id="2813b-135">下图显示了初始应用屏幕截图。</span><span class="sxs-lookup"><span data-stu-id="2813b-135">The next figure shows the initial app screenshots.</span></span>

![ASP.NET MVC 和 ASP.NET Web Forms 应用程序（现有/旧技术）](./media/image5-2.png)

<span data-ttu-id="2813b-137">ASP.NET 4.x 或早期版本中的依赖项（对于 MVC 或 Web Forms）意味着这些应用程序不会在 .NET Core 上运行，除非使用 ASP.NET Core MVC 来完全重写代码。</span><span class="sxs-lookup"><span data-stu-id="2813b-137">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won't run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span>

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a><span data-ttu-id="2813b-138">应用场景 2：WCF 服务和 WinForms 客户端应用（3 层应用）</span><span class="sxs-lookup"><span data-stu-id="2813b-138">Scenario 2: WCF service and WinForms client app (3-Tier app)</span></span>

<span data-ttu-id="2813b-139">下图显示了原始 3 层旧版应用程序的简单方案。</span><span class="sxs-lookup"><span data-stu-id="2813b-139">The figure below shows the simple scenario of the original 3-Tier legacy application.</span></span>

![具有 WCF 服务和 WinForms 客户端应用的原始旧版 3 层应用的简单体系结构方案](./media/image5-1.5.png)

### <a name="benefits"></a><span data-ttu-id="2813b-141">优点</span><span class="sxs-lookup"><span data-stu-id="2813b-141">Benefits</span></span>

<span data-ttu-id="2813b-142">此演练的优点非常简单：只是熟悉代码和初始应用。</span><span class="sxs-lookup"><span data-stu-id="2813b-142">The benefits of this walkthrough are simple: Just get familiar with the code and initial apps.</span></span>

### <a name="next-steps"></a><span data-ttu-id="2813b-143">后续步骤</span><span class="sxs-lookup"><span data-stu-id="2813b-143">Next steps</span></span>

<span data-ttu-id="2813b-144">在 GitHub wiki 上更深入了解此内容：</span><span class="sxs-lookup"><span data-stu-id="2813b-144">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="2813b-145">有关基准 ASP.NET MVC 和 Web Forms“旧版”应用的教程</span><span class="sxs-lookup"><span data-stu-id="2813b-145">Tour on the baseline ASP.NET MVC and Web Forms "legacy" apps</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [<span data-ttu-id="2813b-146">有关基准 WCF 服务和 WinForms（3 层）“旧版”应用的教程</span><span class="sxs-lookup"><span data-stu-id="2813b-146">Tour on the baseline WCF service and WinForms (3-Tier) "legacy" app</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="2813b-147">演练 2：使用 Windows 容器容器化现有 .NET 应用程序</span><span class="sxs-lookup"><span data-stu-id="2813b-147">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="overview"></a><span data-ttu-id="2813b-148">概述</span><span class="sxs-lookup"><span data-stu-id="2813b-148">Overview</span></span>

<span data-ttu-id="2813b-149">使用 Windows 容器改进现有 .NET 应用程序（例如，基于 MVC、Web Forms 或 WCF 的应用程序）到生产、开发和测试环境的部署。</span><span class="sxs-lookup"><span data-stu-id="2813b-149">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="2813b-150">目标</span><span class="sxs-lookup"><span data-stu-id="2813b-150">Goals</span></span>

<span data-ttu-id="2813b-151">本演练的目的是演示用于容器化现有 .NET Framework 应用程序的多个选项。</span><span class="sxs-lookup"><span data-stu-id="2813b-151">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="2813b-152">你可以：</span><span class="sxs-lookup"><span data-stu-id="2813b-152">You can:</span></span>

- <span data-ttu-id="2813b-153">使用 [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker)（Visual Studio 2017 或更高版本）容器化应用程序。</span><span class="sxs-lookup"><span data-stu-id="2813b-153">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="2813b-154">通过手动添加 [Dockerfile](https://docs.docker.com/engine/reference/builder/)，然后使用 [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/) 来容器化应用程序。</span><span class="sxs-lookup"><span data-stu-id="2813b-154">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="2813b-155">使用 [Img2Docker](https://github.com/docker/communitytools-image2docker-win) 工具（Docker 的开源工具）容器化应用程序。</span><span class="sxs-lookup"><span data-stu-id="2813b-155">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="2813b-156">本演练重点介绍 Visual Studio 2017 Tools for Docker 方法，但另外两种方法与使用 Dockerfile 非常相似。</span><span class="sxs-lookup"><span data-stu-id="2813b-156">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario-1-containerized-aspnet-web-apps"></a><span data-ttu-id="2813b-157">应用场景 1：容器化 ASP.NET Web 应用</span><span class="sxs-lookup"><span data-stu-id="2813b-157">Scenario 1: Containerized ASP.NET web apps</span></span>

<span data-ttu-id="2813b-158">下图显示了容器化 eShop 旧版 Web 应用应用程序的方案。</span><span class="sxs-lookup"><span data-stu-id="2813b-158">Figure below shows the scenario for containerized eShop legacy web apps applications.</span></span>

![开发环境中的容器化 ASP.NET 应用程序的简化体系结构关系图](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a><span data-ttu-id="2813b-160">应用场景 2：容器化 WCF 服务</span><span class="sxs-lookup"><span data-stu-id="2813b-160">Scenario 2: Containerized WCF service</span></span>

<span data-ttu-id="2813b-161">下图显示了具有容器化 WCF 服务的 3 层应用的方案。</span><span class="sxs-lookup"><span data-stu-id="2813b-161">Figure below shows the scenario for a 3-Tier app with a containerized WCF service.</span></span>

![开发环境中的容器化 WCF 服务的简化体系结构关系图](./media/image5-3.5.png)

### <a name="benefits"></a><span data-ttu-id="2813b-163">优点</span><span class="sxs-lookup"><span data-stu-id="2813b-163">Benefits</span></span>

<span data-ttu-id="2813b-164">在容器中运行整体式应用程序有优点。</span><span class="sxs-lookup"><span data-stu-id="2813b-164">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="2813b-165">首先，创建应用程序的映像。</span><span class="sxs-lookup"><span data-stu-id="2813b-165">First, you create an image for the application.</span></span> <span data-ttu-id="2813b-166">自此，每个部署会在相同的环境中运行。</span><span class="sxs-lookup"><span data-stu-id="2813b-166">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="2813b-167">每个容器会使用相同的操作系统版本，安装相同版本的依赖项，使用同一个 .NET Framework 版本，并通过同一个流程生成。</span><span class="sxs-lookup"><span data-stu-id="2813b-167">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="2813b-168">基本上，使用 Docker 映像控制应用程序的依赖项。</span><span class="sxs-lookup"><span data-stu-id="2813b-168">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="2813b-169">部署容器时，依赖项随应用程序移动。</span><span class="sxs-lookup"><span data-stu-id="2813b-169">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="2813b-170">另一个优点是，开发人员可以在 Windows 容器提供的一致环境中运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="2813b-170">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="2813b-171">仅某些版本中出现的问题会立即被发现，而不会出现在过渡或生产环境中。</span><span class="sxs-lookup"><span data-stu-id="2813b-171">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="2813b-172">应用程序在容器中运行后，开发团队的成员使用的开发环境之间的差异将不那么重要。</span><span class="sxs-lookup"><span data-stu-id="2813b-172">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="2813b-173">容器化应用程序还具有较为平缓的的横向扩展曲线。</span><span class="sxs-lookup"><span data-stu-id="2813b-173">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="2813b-174">使用容器化应用，VM 或物理计算机可以拥有更多应用程序和服务实例（与每台计算机的常规应用程序部署相比）。</span><span class="sxs-lookup"><span data-stu-id="2813b-174">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="2813b-175">这将转换为更高的密度和更少的所需资源，尤其是在使用业务流程协调程序（如 Kubernetes）时。</span><span class="sxs-lookup"><span data-stu-id="2813b-175">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes.</span></span>

<span data-ttu-id="2813b-176">在理想情况下，容器化不需要对应用程序代码 (C\#) 进行任何更改。</span><span class="sxs-lookup"><span data-stu-id="2813b-176">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="2813b-177">在大多数情况下，只需要 Docker 部署元数据文件（Dockerfile 和 Docker Compose 文件）。</span><span class="sxs-lookup"><span data-stu-id="2813b-177">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="2813b-178">后续步骤</span><span class="sxs-lookup"><span data-stu-id="2813b-178">Next steps</span></span>

<span data-ttu-id="2813b-179">在 GitHub wiki 上更深入了解此内容：</span><span class="sxs-lookup"><span data-stu-id="2813b-179">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="2813b-180">如何使用 Windows 容器和 Docker 容器化 .NET Framework Web 应用</span><span class="sxs-lookup"><span data-stu-id="2813b-180">How to containerize the .NET Framework web apps with Windows Containers and Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [<span data-ttu-id="2813b-181">向 WCF 服务添加 Docker 支持</span><span class="sxs-lookup"><span data-stu-id="2813b-181">Adding Docker Support to a WCF service</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="2813b-182">演练 3：将基于 Windows 容器的应用部署到 Azure VM</span><span class="sxs-lookup"><span data-stu-id="2813b-182">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="2813b-183">技术演练可用性</span><span class="sxs-lookup"><span data-stu-id="2813b-183">Technical walkthrough availability</span></span>

<span data-ttu-id="2813b-184">eShopModernizing GitHub 存储库 wiki 中提供了完整的技术演练：<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="2813b-184">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span></span>

### <a name="overview"></a><span data-ttu-id="2813b-185">概述</span><span class="sxs-lookup"><span data-stu-id="2813b-185">Overview</span></span>

<span data-ttu-id="2813b-186">通过在 Azure 中部署到 Windows Server 2016 虚拟机 (VM) 上的 Docker 主机，可以快速设置开发/测试/过渡环境。</span><span class="sxs-lookup"><span data-stu-id="2813b-186">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="2813b-187">还可以为你提供一个公共场所，供测试人员或业务用户验证应用。</span><span class="sxs-lookup"><span data-stu-id="2813b-187">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="2813b-188">VM 还可以是有效的基础结构即服务 (IaaS) 生产环境。</span><span class="sxs-lookup"><span data-stu-id="2813b-188">VMs also can be valid Infrastructure as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="2813b-189">目标</span><span class="sxs-lookup"><span data-stu-id="2813b-189">Goals</span></span>

<span data-ttu-id="2813b-190">本演练的目的是介绍将 Windows 容器部署到基于 Windows Server 2016 或更高版本的 Azure VM 的多个替代方案。</span><span class="sxs-lookup"><span data-stu-id="2813b-190">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="2813b-191">方案</span><span class="sxs-lookup"><span data-stu-id="2813b-191">Scenarios</span></span>

<span data-ttu-id="2813b-192">本演练介绍了多个方案。</span><span class="sxs-lookup"><span data-stu-id="2813b-192">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="2813b-193">方案 A：通过 Docker 引擎连接从开发电脑部署到 Azure VM</span><span class="sxs-lookup"><span data-stu-id="2813b-193">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![通过 Docker 引擎连接从开发电脑部署到 Azure VM](./media/image5-4.png)

<span data-ttu-id="2813b-195">**图 5-4**。</span><span class="sxs-lookup"><span data-stu-id="2813b-195">**Figure 5-4.**</span></span> <span data-ttu-id="2813b-196">通过 Docker 引擎连接从开发电脑部署到 Azure VM</span><span class="sxs-lookup"><span data-stu-id="2813b-196">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="2813b-197">情况 B：通过 Docker 注册表部署到 Azure VM</span><span class="sxs-lookup"><span data-stu-id="2813b-197">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![通过 Docker 注册表部署到 Azure VM](./media/image5-5.png)

<span data-ttu-id="2813b-199">**图 5-5**。</span><span class="sxs-lookup"><span data-stu-id="2813b-199">**Figure 5-5.**</span></span> <span data-ttu-id="2813b-200">通过 Docker 注册表部署到 Azure VM</span><span class="sxs-lookup"><span data-stu-id="2813b-200">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="2813b-201">方案 C：从 Azure DevOps Services 中的 CI/CD 管道部署到 Azure VM</span><span class="sxs-lookup"><span data-stu-id="2813b-201">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

![从 Azure DevOps Services 中的 CI/CD 管道部署到 Azure VM](./media/image5-6.png)

<span data-ttu-id="2813b-203">**如 5-6**。</span><span class="sxs-lookup"><span data-stu-id="2813b-203">**Figure 5-6.**</span></span> <span data-ttu-id="2813b-204">从 Azure DevOps Services 中的 CI/CD 管道部署到 Azure VM</span><span class="sxs-lookup"><span data-stu-id="2813b-204">Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="2813b-205">适用于 Windows 容器的 Azure VM</span><span class="sxs-lookup"><span data-stu-id="2813b-205">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="2813b-206">适用于 Windows 容器的 Azure VM 是基于安装了 Docker 引擎的 Windows Server 2016、Windows 10 或更高版本的 VM。</span><span class="sxs-lookup"><span data-stu-id="2813b-206">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="2813b-207">在大多数情况下，在 Azure VM 中使用 Windows Server 2016。</span><span class="sxs-lookup"><span data-stu-id="2813b-207">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="2813b-208">Azure 当前提供名为“包含容器的 Windows Server 2016”的 VM  。</span><span class="sxs-lookup"><span data-stu-id="2813b-208">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="2813b-209">通过 Windows Server Core 或 Windows Nano Server，可以使用此 VM 尝试新的 Windows Server 容器功能。</span><span class="sxs-lookup"><span data-stu-id="2813b-209">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="2813b-210">安装容器操作系统映像后，VM 即可用于 Docker。</span><span class="sxs-lookup"><span data-stu-id="2813b-210">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="2813b-211">优点</span><span class="sxs-lookup"><span data-stu-id="2813b-211">Benefits</span></span>

<span data-ttu-id="2813b-212">尽管可以将 Windows 容器部署到本地 Windows Server 2016 VM，但在部署到 Azure 时，可以使用随时可用的 Windows Server 容器 VM 来更轻松地入门。</span><span class="sxs-lookup"><span data-stu-id="2813b-212">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="2813b-213">还可以获取可供测试人员访问的常用联机位置，并通过 Azure 虚拟机规模集进行自动缩放。</span><span class="sxs-lookup"><span data-stu-id="2813b-213">You also get a common online location that's accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="2813b-214">后续步骤</span><span class="sxs-lookup"><span data-stu-id="2813b-214">Next steps</span></span>

<span data-ttu-id="2813b-215">在 GitHub wiki 上更深入了解此内容：</span><span class="sxs-lookup"><span data-stu-id="2813b-215">Explore this content more in-depth on the GitHub wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a><span data-ttu-id="2813b-216">演练 4：将基于 Windows 容器的应用部署到 Azure 容器实例 (ACI)</span><span class="sxs-lookup"><span data-stu-id="2813b-216">Walkthrough 4: Deploy your Windows Containers-based apps to Azure Container Instances (ACI)</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="2813b-217">技术演练可用性</span><span class="sxs-lookup"><span data-stu-id="2813b-217">Technical walkthrough availability</span></span>

<span data-ttu-id="2813b-218">eShopModernizing GitHub 存储库 wiki 中提供了完整的技术演练：</span><span class="sxs-lookup"><span data-stu-id="2813b-218">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="2813b-219">[将应用部署到 ACI（Azure 容器实例）](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span><span class="sxs-lookup"><span data-stu-id="2813b-219">[Deploying the Apps to ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span></span>

### <a name="overview"></a><span data-ttu-id="2813b-220">概述</span><span class="sxs-lookup"><span data-stu-id="2813b-220">Overview</span></span>

<span data-ttu-id="2813b-221">[Azure 容器实例 (ACI)](/azure/container-instances/) 是创建容器开发/测试/过渡环境（可在其中部署容器的单个实例）的最快方式。</span><span class="sxs-lookup"><span data-stu-id="2813b-221">[Azure Container Instances (ACI)](/azure/container-instances/) is the quickest way to have a Containers dev/test/staging environment where you can deploy single instances of containers.</span></span>

### <a name="goals"></a><span data-ttu-id="2813b-222">目标</span><span class="sxs-lookup"><span data-stu-id="2813b-222">Goals</span></span>

<span data-ttu-id="2813b-223">本演练演示了将 Windows 容器部署到 Azure 容器实例 (ACI) 以及将 eShopModernizing 应用部署到 ACI 的主要方案。</span><span class="sxs-lookup"><span data-stu-id="2813b-223">This walkthrough shows you the main scenarios when deploying Windows Containers to Azure Container Instances (ACI) and how you can deploy eShopModernizing Apps into ACI.</span></span>

### <a name="scenarios"></a><span data-ttu-id="2813b-224">方案</span><span class="sxs-lookup"><span data-stu-id="2813b-224">Scenarios</span></span>

<span data-ttu-id="2813b-225">将 eShopModernizing 应用部署到 ACI 中可能会发生变化，例如仅部署一个应用或部署所有应用（MVC 应用、WebForms 应用或 WCF 服务）。</span><span class="sxs-lookup"><span data-stu-id="2813b-225">There can be variations about deploying the eShopModernizing apps into ACI such as deploying just one or all of the apps (MVC app, WebForms app or WCF service).</span></span> <span data-ttu-id="2813b-226">在以下方案中，你可以看到 ASP.NET MVC 应用和 SQL Server 容器，它们都作为容器部署到 ACI（Azure 容器实例）中。</span><span class="sxs-lookup"><span data-stu-id="2813b-226">In the following scenario shown below you can see the ASP.NET MVC app plus the SQL Server container both of them deployed as containers into ACI (Azure Container Instances).</span></span>

![从开发环境部署到 ACI](./media/image5-3.5.6.png)

### <a name="benefits"></a><span data-ttu-id="2813b-228">优点</span><span class="sxs-lookup"><span data-stu-id="2813b-228">Benefits</span></span>

<span data-ttu-id="2813b-229">使用 Azure 容器实例，可以在 Azure 中轻松创建和管理 Docker 容器，无需预配虚拟机或采用更高级别的服务。</span><span class="sxs-lookup"><span data-stu-id="2813b-229">Azure Container Instances makes it easy to create and manage Docker containers in Azure, without having to provision virtual machines or adopt a higher-level service.</span></span> <span data-ttu-id="2813b-230">使用 ACI，可以在 Azure 中直接部署 Windows 容器，并在几秒钟内使用完全限定的域名 (FQDN) 向 Internet 公开该容器（前提是 Docker 注册表（例如 Docker Hub 或 Azure 容器注册表）中已准备好 Windows 容器映像）。</span><span class="sxs-lookup"><span data-stu-id="2813b-230">With ACI, you can directly deploy a Windows container in Azure and expose it to the internet with a fully qualified domain name (FQDN) in a matter of seconds (Provided that you have the Windows Container image ready in a Docker registry like Docker Hub or Azure Container Registry).</span></span>

### <a name="considerations"></a><span data-ttu-id="2813b-231">注意事项</span><span class="sxs-lookup"><span data-stu-id="2813b-231">Considerations</span></span>

<span data-ttu-id="2813b-232">将包含完全 .NET Framework/ASP.NET 或 SQL Server 的 Windows 容器部署到 Azure 容器实例 (ACI) 的速度不如部署到常规 Docker 主机（例如，包含 Windows 容器的 Windows Server 2016）的速度快，因为每次都必须下载 Docker 映像（从 Docker 注册表中拉取），并且 SQL 容器映像 (15.1 GB) 和 ASP.NET 容器映像 (13.9 GB) 的大小非常大，但它比维护你自己的 Docker 主机（包含 Azure 中的 Windows 容器 VM 的永久在线 Windows Server 2016）更便宜，更不用说整个业务流程协调程序（例如 Azure Kubernetes 服务 (AKS)），而这也是生产部署的一个不错选择。</span><span class="sxs-lookup"><span data-stu-id="2813b-232">Deploying Windows Containers with either full .NET Framework / ASP.NET or SQL Server into Azure Container Instances (ACI) is not quite as fast as deploying to a regular Docker Host (like a Windows Server 2016 with Windows Containers) because the Docker image has to be downloaded (pulled from the Docker registry) every time and the sizes of the SQL container image (15.1 GB) and the ASP.NET container image (13.9 GB) are significantly large, however it is much cheaper than maintaining your own docker host (permanently on-line Windows Server 2016 with Windows Containers VM in Azure) not to mention a whole orchestrator like Kubernetes in Azure (AKS) which is, on the other hand, a great choice for production deployments.</span></span>

<span data-ttu-id="2813b-233">主要结论是，使用 Azure 容器实例是适用于开发/测试方案和 CI/CD 管道的最终选择。</span><span class="sxs-lookup"><span data-stu-id="2813b-233">As main conclusion, using Azure Container Instances is a very compelling option for Dev/Test scenarios and for CI/CD pipelines.</span></span>

### <a name="next-steps"></a><span data-ttu-id="2813b-234">后续步骤</span><span class="sxs-lookup"><span data-stu-id="2813b-234">Next steps</span></span>

<span data-ttu-id="2813b-235">在 GitHub wiki 上更深入了解此内容：</span><span class="sxs-lookup"><span data-stu-id="2813b-235">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="2813b-236">演练 5：将基于 Windows 容器的应用部署到 Azure 容器服务中的 Kubernetes</span><span class="sxs-lookup"><span data-stu-id="2813b-236">Walkthrough 5: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="2813b-237">技术演练可用性</span><span class="sxs-lookup"><span data-stu-id="2813b-237">Technical walkthrough availability</span></span>

<span data-ttu-id="2813b-238">eShopModernizing GitHub 存储库 wiki 中提供了完整的技术演练：</span><span class="sxs-lookup"><span data-stu-id="2813b-238">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a><span data-ttu-id="2813b-239">概述</span><span class="sxs-lookup"><span data-stu-id="2813b-239">Overview</span></span>

<span data-ttu-id="2813b-240">基于 Windows 容器的应用程序很快需要使用平台，使其与 IaaS VM 离得更远。</span><span class="sxs-lookup"><span data-stu-id="2813b-240">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="2813b-241">这是为了轻松实现高可伸缩性和更好的自动可伸缩性，并显著改进自动化部署和版本控制。</span><span class="sxs-lookup"><span data-stu-id="2813b-241">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="2813b-242">可以使用 [Azure 容器服务](https://azure.microsoft.com/services/container-service/)中提供的业务流程协调程序 [Kubernetes](https://kubernetes.io/) 来实现这些目标。</span><span class="sxs-lookup"><span data-stu-id="2813b-242">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="2813b-243">目标</span><span class="sxs-lookup"><span data-stu-id="2813b-243">Goals</span></span>

<span data-ttu-id="2813b-244">本演练的目的是了解如何将基于 Windows 容器的应用程序部署到 Azure 容器服务中的 Kubernetes（也称为 K8s  ）。</span><span class="sxs-lookup"><span data-stu-id="2813b-244">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="2813b-245">从头开始部署到 Kubernetes 的过程分为两个步骤：</span><span class="sxs-lookup"><span data-stu-id="2813b-245">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1. <span data-ttu-id="2813b-246">将 Kubernetes 群集部署到 Azure 容器服务。</span><span class="sxs-lookup"><span data-stu-id="2813b-246">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2. <span data-ttu-id="2813b-247">将应用程序和相关资源部署到 Kubernetes 群集。</span><span class="sxs-lookup"><span data-stu-id="2813b-247">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="2813b-248">方案</span><span class="sxs-lookup"><span data-stu-id="2813b-248">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="2813b-249">方案 A：从开发环境直接部署到 Kubernetes 群集</span><span class="sxs-lookup"><span data-stu-id="2813b-249">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![从开发环境直接部署到 Kubernetes 群集](./media/image5-7.png)

<span data-ttu-id="2813b-251">**图 5-7**。</span><span class="sxs-lookup"><span data-stu-id="2813b-251">**Figure 5-7.**</span></span> <span data-ttu-id="2813b-252">从开发环境直接部署到 Kubernetes 群集</span><span class="sxs-lookup"><span data-stu-id="2813b-252">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="2813b-253">情况 B：从 Azure DevOps Services 中的 CI/CD 管道部署到 Kubernetes 群集</span><span class="sxs-lookup"><span data-stu-id="2813b-253">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

![从 Azure DevOps Services 中的 CI/CD 管道部署到 Kubernetes 群集](./media/image5-8.png)

<span data-ttu-id="2813b-255">**图 5-8**。</span><span class="sxs-lookup"><span data-stu-id="2813b-255">**Figure 5-8.**</span></span> <span data-ttu-id="2813b-256">从 Azure DevOps Services 中的 CI/CD 管道部署到 Kubernetes 群集</span><span class="sxs-lookup"><span data-stu-id="2813b-256">Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="benefits"></a><span data-ttu-id="2813b-257">优点</span><span class="sxs-lookup"><span data-stu-id="2813b-257">Benefits</span></span>

<span data-ttu-id="2813b-258">部署到 Kubernetes 中的群集有许多优点。</span><span class="sxs-lookup"><span data-stu-id="2813b-258">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="2813b-259">最大的优点是，可以获得一个生产就绪环境，在该环境中，你可以根据要使用的容器实例数（现有节点中的内部可伸缩性）以及群集中的节点数或 VM 数（群集的全局可伸缩性）来扩展应用程序。</span><span class="sxs-lookup"><span data-stu-id="2813b-259">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="2813b-260">Azure 容器服务优化了专门针对 Azure 的常用开源工具和技术。</span><span class="sxs-lookup"><span data-stu-id="2813b-260">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="2813b-261">可以获得一个开放的解决方案，该解决方案为容器和应用程序配置提供可移植性。</span><span class="sxs-lookup"><span data-stu-id="2813b-261">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="2813b-262">用户选择主机的大小和数量以及业务流程协调程序工具，然后容器服务可处理其他操作。</span><span class="sxs-lookup"><span data-stu-id="2813b-262">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="2813b-263">使用 Kubernetes，开发人员可以在考虑物理计算机和虚拟机时取得进展，规划支持以下功能的以容器为中心的基础结构等等：</span><span class="sxs-lookup"><span data-stu-id="2813b-263">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="2813b-264">基于多个容器的应用程序</span><span class="sxs-lookup"><span data-stu-id="2813b-264">Applications based on multiple containers</span></span>

- <span data-ttu-id="2813b-265">复制容器实例和水平自动缩放</span><span class="sxs-lookup"><span data-stu-id="2813b-265">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="2813b-266">命名和发现（例如，内部 DNS）</span><span class="sxs-lookup"><span data-stu-id="2813b-266">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="2813b-267">均衡负载</span><span class="sxs-lookup"><span data-stu-id="2813b-267">Balancing loads</span></span>

- <span data-ttu-id="2813b-268">滚动更新</span><span class="sxs-lookup"><span data-stu-id="2813b-268">Rolling updates</span></span>

- <span data-ttu-id="2813b-269">分布机密</span><span class="sxs-lookup"><span data-stu-id="2813b-269">Distributing secrets</span></span>

- <span data-ttu-id="2813b-270">应用程序运行状况检查</span><span class="sxs-lookup"><span data-stu-id="2813b-270">Application health checks</span></span>

### <a name="next-steps"></a><span data-ttu-id="2813b-271">后续步骤</span><span class="sxs-lookup"><span data-stu-id="2813b-271">Next steps</span></span>

<span data-ttu-id="2813b-272">在 GitHub wiki 上更深入了解此内容：<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="2813b-272">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span></span>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a><span data-ttu-id="2813b-273">演练 6：将基于 Windows 容器的应用部署到用于容器的 Azure 应用服务</span><span class="sxs-lookup"><span data-stu-id="2813b-273">Walkthrough 6: Deploy your Windows Containers-based apps to Azure App Service for Containers</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="2813b-274">技术演练可用性</span><span class="sxs-lookup"><span data-stu-id="2813b-274">Technical walkthrough availability</span></span>

<span data-ttu-id="2813b-275">eShopModernizing GitHub 存储库 wiki 中提供了完整的技术演练：</span><span class="sxs-lookup"><span data-stu-id="2813b-275">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a><span data-ttu-id="2813b-276">概述</span><span class="sxs-lookup"><span data-stu-id="2813b-276">Overview</span></span>

<span data-ttu-id="2813b-277">可以轻松地将使用 Windows 容器的简单容器化应用程序部署到用于容器的 Azure 应用服务。</span><span class="sxs-lookup"><span data-stu-id="2813b-277">A simple containerized application using Windows Containers can easily be deployed to Azure App Service for Containers.</span></span> <span data-ttu-id="2813b-278">对于大多数基于 Windows 容器的应用程序，建议采用此方法。</span><span class="sxs-lookup"><span data-stu-id="2813b-278">This is the recommended approach for most Windows Container-based applications.</span></span>

### <a name="goals"></a><span data-ttu-id="2813b-279">目标</span><span class="sxs-lookup"><span data-stu-id="2813b-279">Goals</span></span>

<span data-ttu-id="2813b-280">本演练的目的是了解如何将基于 Windows 容器的应用程序部署到注册表（Docker Hub 或 Azure 容器注册表）中用于容器的 Azure 应用服务。</span><span class="sxs-lookup"><span data-stu-id="2813b-280">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Azure App Service for Containers from a registry (Docker Hub or Azure Container Registry).</span></span>

### <a name="scenario"></a><span data-ttu-id="2813b-281">方案</span><span class="sxs-lookup"><span data-stu-id="2813b-281">Scenario</span></span>

![将基于 Windows 容器的应用部署到用于容器的 Azure 应用服务](./media/image5-11.png)

### <a name="benefits"></a><span data-ttu-id="2813b-283">优点</span><span class="sxs-lookup"><span data-stu-id="2813b-283">Benefits</span></span>

<span data-ttu-id="2813b-284">部署到用于容器的 Azure 应用服务提供的容器优点与 Azure 应用服务的 PaaS 优点配对。</span><span class="sxs-lookup"><span data-stu-id="2813b-284">Deploying to Azure App Service for Containers offers the benefits of containers paired with the PaaS benefits of Azure App Service.</span></span> <span data-ttu-id="2813b-285">应用服务可以轻松地在垂直和水平方向上缩放，并且可以配置为自动缩放以满足不断变化的需求。</span><span class="sxs-lookup"><span data-stu-id="2813b-285">The app service can easily be scaled both vertically and horizontally, and can be configured to autoscale to meet changing demands.</span></span> <span data-ttu-id="2813b-286">可以在零停机的情况下执行更新，也可以轻松地配置注册表中的持续部署。</span><span class="sxs-lookup"><span data-stu-id="2813b-286">Updates can be performed with zero downtime and configuration of continuous deployment from a registry is easily configured as well.</span></span>

### <a name="next-steps"></a><span data-ttu-id="2813b-287">后续步骤</span><span class="sxs-lookup"><span data-stu-id="2813b-287">Next steps</span></span>

<span data-ttu-id="2813b-288">在 GitHub wiki 上更深入了解此内容：<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span><span class="sxs-lookup"><span data-stu-id="2813b-288">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="2813b-289">[上一页](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
> [下一页](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="2813b-289">[Previous](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span> <!-- Next Chapter -->

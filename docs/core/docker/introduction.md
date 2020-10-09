---
title: Docker 简介
description: 本文简要概述 .NET Core 应用程序上下文中的 Docker。
ms.date: 03/20/2019
ms.custom: mvc
ms.openlocfilehash: 16ad49c39d588aac8f8a7a918eb4d799f37823ac
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654817"
---
# <a name="introduction-to-net-and-docker"></a><span data-ttu-id="76755-103">.NET 和 Docker 简介</span><span class="sxs-lookup"><span data-stu-id="76755-103">Introduction to .NET and Docker</span></span>

<span data-ttu-id="76755-104">.NET Core 可以在 Docker 容器中轻松运行。</span><span class="sxs-lookup"><span data-stu-id="76755-104">.NET Core can easily run in a Docker container.</span></span> <span data-ttu-id="76755-105">容器提供一种轻量级方法，用于将应用程序与主机系统的其他组件分隔，以便仅共享内核，并使用提供给应用程序的资源。</span><span class="sxs-lookup"><span data-stu-id="76755-105">Containers provide a lightweight way to isolate your application from the rest of the host system, sharing just the kernel, and using resources given to your application.</span></span> <span data-ttu-id="76755-106">如果你不熟悉 Docker，强烈建议通读 Docker 的[概述文档](https://docs.docker.com/engine/docker-overview/)。</span><span class="sxs-lookup"><span data-stu-id="76755-106">If you're unfamiliar with Docker, it's highly recommended that you read through Docker's [overview documentation](https://docs.docker.com/engine/docker-overview/).</span></span>

<span data-ttu-id="76755-107">若要详细了解如何安装 Docker，请参阅 [Docker 桌面：社区版](https://www.docker.com/products/docker-desktop)的下载页面。</span><span class="sxs-lookup"><span data-stu-id="76755-107">For more information about how to install Docker, see the download page for [Docker Desktop: Community Edition](https://www.docker.com/products/docker-desktop).</span></span>

## <a name="docker-basics"></a><span data-ttu-id="76755-108">Docker 基础知识</span><span class="sxs-lookup"><span data-stu-id="76755-108">Docker basics</span></span>

<span data-ttu-id="76755-109">首先来熟悉几个概念。</span><span class="sxs-lookup"><span data-stu-id="76755-109">There are a few concepts you should be familiar with.</span></span> <span data-ttu-id="76755-110">Docker 客户端具有可用于管理映像和容器的 CLI。</span><span class="sxs-lookup"><span data-stu-id="76755-110">The Docker client has a CLI that you can use to manage images and containers.</span></span> <span data-ttu-id="76755-111">如前文所述，应花时间通读 [Docker 概述](https://docs.docker.com/engine/docker-overview/)文档。</span><span class="sxs-lookup"><span data-stu-id="76755-111">As previously stated, you should take the time to read through the [Docker overview](https://docs.docker.com/engine/docker-overview/) documentation.</span></span>

### <a name="images"></a><span data-ttu-id="76755-112">映像</span><span class="sxs-lookup"><span data-stu-id="76755-112">Images</span></span>

<span data-ttu-id="76755-113">映像是构成容器基础的文件系统更改的有序集合。</span><span class="sxs-lookup"><span data-stu-id="76755-113">An image is an ordered collection of filesystem changes that form the basis of a container.</span></span> <span data-ttu-id="76755-114">映像不具有状态，并且是只读的。</span><span class="sxs-lookup"><span data-stu-id="76755-114">The image doesn't have a state and is read-only.</span></span> <span data-ttu-id="76755-115">大多情况下，一个映像以另一个映像为基础，但具有一些自定义设置。</span><span class="sxs-lookup"><span data-stu-id="76755-115">Much the time an image is based on another image, but with some customization.</span></span> <span data-ttu-id="76755-116">例如，为应用程序创建新映像时，可将其基于已包含 .NET Core 运行时的现有映像。</span><span class="sxs-lookup"><span data-stu-id="76755-116">For example, when you create an new image for your application, you would base it on an existing image that already contains the .NET Core runtime.</span></span>

<span data-ttu-id="76755-117">由于容器是从映像创建的，因此，映像具有一组在容器启动时运行的运行参数（例如启动可执行文件）。</span><span class="sxs-lookup"><span data-stu-id="76755-117">Because containers are created from images, images have a set of run parameters (such as a starting executable) that run when the container starts.</span></span>

### <a name="containers"></a><span data-ttu-id="76755-118">容器</span><span class="sxs-lookup"><span data-stu-id="76755-118">Containers</span></span>

<span data-ttu-id="76755-119">容器是映像的可运行实例。</span><span class="sxs-lookup"><span data-stu-id="76755-119">A container is a runnable instance of an image.</span></span> <span data-ttu-id="76755-120">生成映像时，部署应用程序和依赖项。</span><span class="sxs-lookup"><span data-stu-id="76755-120">As you build your image, you deploy your application and dependencies.</span></span> <span data-ttu-id="76755-121">然后可以实例化多个容器，且每个容器相互独立。</span><span class="sxs-lookup"><span data-stu-id="76755-121">Then, multiple containers can be instantiated, each isolated from one another.</span></span> <span data-ttu-id="76755-122">每个容器实例具有其自己的文件系统、内存和网络接口。</span><span class="sxs-lookup"><span data-stu-id="76755-122">Each container instance has its own filesystem, memory, and network interface.</span></span>

### <a name="registries"></a><span data-ttu-id="76755-123">注册表</span><span class="sxs-lookup"><span data-stu-id="76755-123">Registries</span></span>

<span data-ttu-id="76755-124">容器注册表是映像存储库的集合。</span><span class="sxs-lookup"><span data-stu-id="76755-124">Container registries are a collection of image repositories.</span></span> <span data-ttu-id="76755-125">映像可以基于注册表映像。</span><span class="sxs-lookup"><span data-stu-id="76755-125">You can base your images on a registry image.</span></span> <span data-ttu-id="76755-126">可以直接从注册表中的映像创建容器。</span><span class="sxs-lookup"><span data-stu-id="76755-126">You can create containers directly from an image in a registry.</span></span> <span data-ttu-id="76755-127">[Docker 容器、映像和注册表之间的关系](../../architecture/microservices/container-docker-introduction/docker-containers-images-registries.md)是[构建和生成容器化应用程序或微服务](../../architecture/microservices/architect-microservice-container-applications/index.md)时的一个重要概念。</span><span class="sxs-lookup"><span data-stu-id="76755-127">The [relationship between Docker containers, images, and registries](../../architecture/microservices/container-docker-introduction/docker-containers-images-registries.md) is an important concept when [architecting and building containerized applications or microservices](../../architecture/microservices/architect-microservice-container-applications/index.md).</span></span> <span data-ttu-id="76755-128">此方法大大缩短了开发和部署之间的时间。</span><span class="sxs-lookup"><span data-stu-id="76755-128">This approach greatly shortens the time between development and deployment.</span></span>

<span data-ttu-id="76755-129">Docker 具有一个托管在 [Docker 中心](https://hub.docker.com/)的公共注册表，可供用户使用。</span><span class="sxs-lookup"><span data-stu-id="76755-129">Docker has a public registry hosted at the [Docker Hub](https://hub.docker.com/) that you can use.</span></span> <span data-ttu-id="76755-130">[.NET Core 相关映像](https://hub.docker.com/_/microsoft-dotnet-core/)均在 Docker 中心列出。</span><span class="sxs-lookup"><span data-stu-id="76755-130">[.NET Core related images](https://hub.docker.com/_/microsoft-dotnet-core/) are listed at the Docker Hub.</span></span>

<span data-ttu-id="76755-131">[Microsoft 容器注册表 (MCR)](/azure/container-registry) 是 Microsoft 提供的容器映像的官方来源。</span><span class="sxs-lookup"><span data-stu-id="76755-131">The [Microsoft Container Registry (MCR)](/azure/container-registry) is the official source of Microsoft-provided container images.</span></span> <span data-ttu-id="76755-132">MCR 构建在 Azure CDN 之上，可提供用于全局复制的映像。</span><span class="sxs-lookup"><span data-stu-id="76755-132">The MCR is built on Azure CDN to provide globally-replicated images.</span></span> <span data-ttu-id="76755-133">但是，MCR 没有面向公众的网站，了解有关 Microsoft 提供的容器映像的主要方法是通过 [Microsoft Docker 中心页面](https://hub.docker.com/_/microsoft-dotnet-core/)。</span><span class="sxs-lookup"><span data-stu-id="76755-133">However, the MCR does not have a public-facing website and the primary way to learn about Microsoft-provided container images is through the [Microsoft Docker Hub pages](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span>

### <a name="dockerfile"></a><span data-ttu-id="76755-134">Dockerfile</span><span class="sxs-lookup"><span data-stu-id="76755-134">Dockerfile</span></span>

<span data-ttu-id="76755-135">Dockerfile\*\*\*\* 是定义可创建映像的一组指令的文件。</span><span class="sxs-lookup"><span data-stu-id="76755-135">A **Dockerfile** is a file that defines a set of instructions that creates an image.</span></span> <span data-ttu-id="76755-136">Dockerfile\*\*\*\* 中的每个指令创建映像中的一个层。</span><span class="sxs-lookup"><span data-stu-id="76755-136">Each instruction in the **Dockerfile** creates a layer in the image.</span></span> <span data-ttu-id="76755-137">大多数情况下，在重新生成映像时，只会重新生成已发生更改的层。</span><span class="sxs-lookup"><span data-stu-id="76755-137">For the most part, when you rebuild the image, only the layers that have changed are rebuilt.</span></span> <span data-ttu-id="76755-138">可以将 Dockerfile\*\*\*\* 分发给其他人，便于他们采用你创建映像的方式重新创建一个新映像。</span><span class="sxs-lookup"><span data-stu-id="76755-138">The **Dockerfile** can be distributed to others and allows them to recreate a new image in the same manner you created it.</span></span> <span data-ttu-id="76755-139">尽管可以分发有关如何创建映像的指令\*\*，但分发映像的主要方式是将其发布到注册表。</span><span class="sxs-lookup"><span data-stu-id="76755-139">While this allows you to distribute the *instructions* on how to create the image, the main way to distribute your image is to publish it to a registry.</span></span>

## <a name="net-core-images"></a><span data-ttu-id="76755-140">.NET Core 映像</span><span class="sxs-lookup"><span data-stu-id="76755-140">.NET Core images</span></span>

<span data-ttu-id="76755-141">官方 .NET Core Docker 映像发布到 Microsoft 容器注册表 (MCR)，用户可以在 [Microsoft.NET Core Docker 中心存储库](https://hub.docker.com/_/microsoft-dotnet-core/)中找到这些映像。</span><span class="sxs-lookup"><span data-stu-id="76755-141">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="76755-142">每个存储库包含 .NET（SDK 或运行时）和可以使用的操作系统的不同组合的映像。</span><span class="sxs-lookup"><span data-stu-id="76755-142">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="76755-143">Microsoft 提供适合特定场景的映像。</span><span class="sxs-lookup"><span data-stu-id="76755-143">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="76755-144">例如，[ASP.NET Core 存储库](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/)提供针对在生产环境中运行 ASP.NET Core 应用生成的映像。</span><span class="sxs-lookup"><span data-stu-id="76755-144">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

## <a name="azure-services"></a><span data-ttu-id="76755-145">Azure 服务</span><span class="sxs-lookup"><span data-stu-id="76755-145">Azure services</span></span>

<span data-ttu-id="76755-146">各种 Azure 服务都支持容器。</span><span class="sxs-lookup"><span data-stu-id="76755-146">Various Azure services support containers.</span></span> <span data-ttu-id="76755-147">为应用程序创建 Docker 映像并将其部署到以下服务之一：</span><span class="sxs-lookup"><span data-stu-id="76755-147">You create a Docker image for your application and deploy it to one of the following services:</span></span>

- <span data-ttu-id="76755-148">[Azure Kubernetes 服务 (AKS)](https://azure.microsoft.com/services/kubernetes-service/)</span><span class="sxs-lookup"><span data-stu-id="76755-148">[Azure Kubernetes Service (AKS)](https://azure.microsoft.com/services/kubernetes-service/)</span></span>\
<span data-ttu-id="76755-149">使用 kubernetes 缩放和编排 Linux 容器。</span><span class="sxs-lookup"><span data-stu-id="76755-149">Scale and orchestrate Linux containers using Kubernetes.</span></span>

- <span data-ttu-id="76755-150">[Azure 应用服务](https://azure.microsoft.com/services/app-service/containers/)</span><span class="sxs-lookup"><span data-stu-id="76755-150">[Azure App Service](https://azure.microsoft.com/services/app-service/containers/)</span></span>\
<span data-ttu-id="76755-151">在 PaaS 环境中使用 Linux 容器部署 Web 应用或 API。</span><span class="sxs-lookup"><span data-stu-id="76755-151">Deploy web apps or APIs using Linux containers in a PaaS environment.</span></span>

- <span data-ttu-id="76755-152">[Azure 容器实例](https://azure.microsoft.com/services/container-instances/)</span><span class="sxs-lookup"><span data-stu-id="76755-152">[Azure Container Instances](https://azure.microsoft.com/services/container-instances/)</span></span>\
<span data-ttu-id="76755-153">将容器托管在云中，而不使用任何高级管理服务。</span><span class="sxs-lookup"><span data-stu-id="76755-153">Host your container in the cloud without any higher-level management services.</span></span>

- <span data-ttu-id="76755-154">[Azure Batch](https://azure.microsoft.com/services/batch/)</span><span class="sxs-lookup"><span data-stu-id="76755-154">[Azure Batch](https://azure.microsoft.com/services/batch/)</span></span>\
<span data-ttu-id="76755-155">使用容器运行重复的计算作业。</span><span class="sxs-lookup"><span data-stu-id="76755-155">Run repetitive compute jobs using containers.</span></span>

- <span data-ttu-id="76755-156">[Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)</span><span class="sxs-lookup"><span data-stu-id="76755-156">[Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)</span></span>\
<span data-ttu-id="76755-157">使用 Windows Server 容器直接迁移 .NET 应用程序并将其现代化为微服务。</span><span class="sxs-lookup"><span data-stu-id="76755-157">Lift, shift, and modernize .NET applications to microservices using Windows Server containers.</span></span>

- <span data-ttu-id="76755-158">[Azure 容器注册表](https://azure.microsoft.com/services/container-registry/)</span><span class="sxs-lookup"><span data-stu-id="76755-158">[Azure Container Registry](https://azure.microsoft.com/services/container-registry/)</span></span>\
<span data-ttu-id="76755-159">在所有类型的 Azure 部署中存储和管理容器映像。</span><span class="sxs-lookup"><span data-stu-id="76755-159">Store and manage container images across all types of Azure deployments.</span></span>

## <a name="next-steps"></a><span data-ttu-id="76755-160">后续步骤</span><span class="sxs-lookup"><span data-stu-id="76755-160">Next steps</span></span>

- [<span data-ttu-id="76755-161">了解如何容器化 .NET Core 应用。</span><span class="sxs-lookup"><span data-stu-id="76755-161">Learn how to containerize a .NET Core application.</span></span>](build-container.md)
- [<span data-ttu-id="76755-162">了解如何容器化 ASP.NET Core 应用程序。</span><span class="sxs-lookup"><span data-stu-id="76755-162">Learn how to containerize an ASP.NET Core application.</span></span>](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [<span data-ttu-id="76755-163">试学“ASP.NET Core 微服务”教程。</span><span class="sxs-lookup"><span data-stu-id="76755-163">Try the Learn ASP.NET Core Microservice tutorial.</span></span>](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [<span data-ttu-id="76755-164">了解 Visual Studio 中的容器工具</span><span class="sxs-lookup"><span data-stu-id="76755-164">Learn about Container Tools in Visual Studio</span></span>](/visualstudio/containers/overview)

---
title: 其他容器部署选项
description: 使用 Azure 的其他容器部署选项
ms.date: 05/13/2020
ms.openlocfilehash: 2eac822b74af636e0ab0ed24b58eb7139526f4a2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163617"
---
# <a name="other-container-deployment-options"></a><span data-ttu-id="fd762-103">其他容器部署选项</span><span class="sxs-lookup"><span data-stu-id="fd762-103">Other container deployment options</span></span>

<span data-ttu-id="fd762-104">除了 Azure Kubernetes Service (AKS) 以外，还可以将容器部署到容器和 Azure 容器实例的 Azure App Service。</span><span class="sxs-lookup"><span data-stu-id="fd762-104">Aside from Azure Kubernetes Service (AKS), you can also deploy containers to Azure App Service for Containers and Azure Container Instances.</span></span>

## <a name="when-does-it-make-sense-to-deploy-to-app-service-for-containers"></a><span data-ttu-id="fd762-105">部署到容器的应用服务有何意义？</span><span class="sxs-lookup"><span data-stu-id="fd762-105">When does it make sense to deploy to App Service for Containers?</span></span>

<span data-ttu-id="fd762-106">不需要业务流程的简单生产应用程序非常适合用于容器 Azure App Service。</span><span class="sxs-lookup"><span data-stu-id="fd762-106">Simple production applications that don't require orchestration are well suited to Azure App Service for Containers.</span></span>

## <a name="how-to-deploy-to-app-service-for-containers"></a><span data-ttu-id="fd762-107">如何部署到容器的应用服务</span><span class="sxs-lookup"><span data-stu-id="fd762-107">How to deploy to App Service for Containers</span></span>

<span data-ttu-id="fd762-108">若要部署到 [容器 Azure App Service](https://azure.microsoft.com/services/app-service/containers/)，需要一个 Azure 容器注册表 (ACR) 实例和凭据来访问它。</span><span class="sxs-lookup"><span data-stu-id="fd762-108">To deploy to [Azure App Service for Containers](https://azure.microsoft.com/services/app-service/containers/), you'll need an Azure Container Registry (ACR) instance and credentials to access it.</span></span> <span data-ttu-id="fd762-109">将容器映像推送到 ACR 存储库，以便将其提取到 Azure App Service 中。</span><span class="sxs-lookup"><span data-stu-id="fd762-109">Push your container image to the ACR repository so it can pulled into your Azure App Service.</span></span> <span data-ttu-id="fd762-110">完成后，可以将应用程序配置为连续部署。</span><span class="sxs-lookup"><span data-stu-id="fd762-110">Once complete, you can configure the app for Continuous Deployment.</span></span> <span data-ttu-id="fd762-111">这样做会在图像更改为 ACR 时自动部署更新。</span><span class="sxs-lookup"><span data-stu-id="fd762-111">Doing so will automatically deploy updates whenever the image changes in ACR.</span></span>

## <a name="when-does-it-make-sense-to-deploy-to-azure-container-instances"></a><span data-ttu-id="fd762-112">部署到 Azure 容器实例时有何意义？</span><span class="sxs-lookup"><span data-stu-id="fd762-112">When does it make sense to deploy to Azure Container Instances?</span></span>

<span data-ttu-id="fd762-113">[Azure 容器实例 (ACI) ](https://azure.microsoft.com/services/container-instances/) 使你能够在托管的无服务器云环境中运行 Docker 容器，而无需设置虚拟机或群集。</span><span class="sxs-lookup"><span data-stu-id="fd762-113">[Azure Container Instances (ACI)](https://azure.microsoft.com/services/container-instances/) enables you to run Docker containers in a managed, serverless cloud environment, without having to set up virtual machines or clusters.</span></span> <span data-ttu-id="fd762-114">这是一个很好的解决方案，适用于可在隔离容器中运行的短时间运行的工作负荷。</span><span class="sxs-lookup"><span data-stu-id="fd762-114">It's a great solution for short-running workloads that can run in an isolated container.</span></span> <span data-ttu-id="fd762-115">请考虑将 ACI 用于简单服务、测试方案、任务自动化和生成作业。</span><span class="sxs-lookup"><span data-stu-id="fd762-115">Consider ACI for simple services, testing scenarios, task automation, and build jobs.</span></span> <span data-ttu-id="fd762-116">ACI 向上旋转容器实例，执行任务，然后将其向下旋转。</span><span class="sxs-lookup"><span data-stu-id="fd762-116">ACI spins-up a container instance, performs the task, and then spins it down.</span></span>

## <a name="how-to-deploy-an-app-to-azure-container-instances"></a><span data-ttu-id="fd762-117">如何将应用部署到 Azure 容器实例</span><span class="sxs-lookup"><span data-stu-id="fd762-117">How to deploy an app to Azure Container Instances</span></span>

<span data-ttu-id="fd762-118">若要部署到 [ (ACI) 的 Azure 容器实例 ](/azure/container-instances/)，需要一个 Azure 容器注册表 (ACR) 和用于访问该实例的凭据。</span><span class="sxs-lookup"><span data-stu-id="fd762-118">To deploy to [Azure Container Instances (ACI)](/azure/container-instances/), you need an Azure Container Registry (ACR) and credentials for accessing it.</span></span> <span data-ttu-id="fd762-119">将容器映像推送到存储库后，可将其拉入 ACI。</span><span class="sxs-lookup"><span data-stu-id="fd762-119">Once you push your container image to the repository, it's available to pull into ACI.</span></span> <span data-ttu-id="fd762-120">可以使用 Azure 门户或命令行界面来处理 ACI。</span><span class="sxs-lookup"><span data-stu-id="fd762-120">You can work with ACI using the Azure portal or command-line interface.</span></span> <span data-ttu-id="fd762-121">ACR 提供与 ACI 的紧密集成。</span><span class="sxs-lookup"><span data-stu-id="fd762-121">ACR provides tight integration with ACI.</span></span> <span data-ttu-id="fd762-122">图3-14 显示了如何将单个容器映像推送到 ACR。</span><span class="sxs-lookup"><span data-stu-id="fd762-122">Figure 3-14 shows how to push an individual container image to ACR.</span></span>

![Azure 容器注册表运行实例](./media/acr-runinstance-contextmenu.png)

<span data-ttu-id="fd762-124">**图 3-14**。</span><span class="sxs-lookup"><span data-stu-id="fd762-124">**Figure 3-14**.</span></span> <span data-ttu-id="fd762-125">Azure 容器注册表运行实例</span><span class="sxs-lookup"><span data-stu-id="fd762-125">Azure Container Registry Run Instance</span></span>

<span data-ttu-id="fd762-126">可以快速完成在 ACI 中创建实例的操作。</span><span class="sxs-lookup"><span data-stu-id="fd762-126">Creating an instance in ACI can be done quickly.</span></span> <span data-ttu-id="fd762-127">指定映像注册表、Azure 资源组信息、要分配的内存量以及要侦听的端口。</span><span class="sxs-lookup"><span data-stu-id="fd762-127">Specify the image registry, Azure resource group information, the amount of memory to allocate, and the port on which to listen.</span></span> <span data-ttu-id="fd762-128">本 [快速入门演示如何使用 Azure 门户将容器实例部署到 ACI](/azure/container-instances/container-instances-quickstart-portal)。</span><span class="sxs-lookup"><span data-stu-id="fd762-128">This [quickstart shows how to deploy a container instance to ACI using the Azure portal](/azure/container-instances/container-instances-quickstart-portal).</span></span>

<span data-ttu-id="fd762-129">部署完成后，查找新部署的容器的 IP 地址，并通过指定的端口与它进行通信。</span><span class="sxs-lookup"><span data-stu-id="fd762-129">Once the deployment completes, find the newly deployed container's IP address and communicate with it over the port you specified.</span></span>

<span data-ttu-id="fd762-130">Azure 容器实例提供了在 Azure 中运行简单容器工作负荷的最快方法。</span><span class="sxs-lookup"><span data-stu-id="fd762-130">Azure Container Instances offers the fastest way to run simple container workloads in Azure.</span></span> <span data-ttu-id="fd762-131">不需要配置应用服务、orchestrator 或虚拟机。</span><span class="sxs-lookup"><span data-stu-id="fd762-131">You don't need to configure an app service, orchestrator, or virtual machine.</span></span> <span data-ttu-id="fd762-132">对于需要完整容器业务流程的方案、服务发现、自动缩放或协调升级，我们建议 Azure Kubernetes Service (AKS) 。</span><span class="sxs-lookup"><span data-stu-id="fd762-132">For scenarios where you require full container orchestration, service discovery, automatic scaling, or coordinated upgrades, we recommend Azure Kubernetes Service (AKS).</span></span>

## <a name="references"></a><span data-ttu-id="fd762-133">参考</span><span class="sxs-lookup"><span data-stu-id="fd762-133">References</span></span>

- [<span data-ttu-id="fd762-134">什么是 Kubernetes？</span><span class="sxs-lookup"><span data-stu-id="fd762-134">What is Kubernetes?</span></span>](https://blog.newrelic.com/engineering/what-is-kubernetes/)
- [<span data-ttu-id="fd762-135">通过 Minikube 安装 Kubernetes</span><span class="sxs-lookup"><span data-stu-id="fd762-135">Installing Kubernetes with Minikube</span></span>](https://kubernetes.io/docs/setup/learning-environment/minikube/)
- [<span data-ttu-id="fd762-136">MiniKube vs Docker Desktop</span><span class="sxs-lookup"><span data-stu-id="fd762-136">MiniKube vs Docker Desktop</span></span>](https://medium.com/containers-101/local-kubernetes-for-windows-minikube-vs-docker-desktop-25a1c6d3b766)
- [<span data-ttu-id="fd762-137">Visual Studio Tools for Docker</span><span class="sxs-lookup"><span data-stu-id="fd762-137">Visual Studio Tools for Docker</span></span>](/dotnet/standard/containerized-lifecycle-architecture/design-develop-containerized-apps/visual-studio-tools-for-docker)
- [<span data-ttu-id="fd762-138">了解无服务器冷启动</span><span class="sxs-lookup"><span data-stu-id="fd762-138">Understanding serverless cold start</span></span>](https://azure.microsoft.com/blog/understanding-serverless-cold-start/)
- [<span data-ttu-id="fd762-139">准备好 Azure Functions 实例</span><span class="sxs-lookup"><span data-stu-id="fd762-139">Pre-warmed Azure Functions instances</span></span>](/azure/azure-functions/functions-premium-plan#pre-warmed-instances)
- [<span data-ttu-id="fd762-140">在 Linux 上使用自定义映像创建函数</span><span class="sxs-lookup"><span data-stu-id="fd762-140">Create a function on Linux using a custom image</span></span>](/azure/azure-functions/functions-create-function-linux-custom-image)
- [<span data-ttu-id="fd762-141">在 Docker 容器中运行 Azure Functions</span><span class="sxs-lookup"><span data-stu-id="fd762-141">Run Azure Functions in a Docker Container</span></span>](https://markheath.net/post/azure-functions-docker)
- [<span data-ttu-id="fd762-142">在 Linux 上使用自定义映像创建函数</span><span class="sxs-lookup"><span data-stu-id="fd762-142">Create a function on Linux using a custom image</span></span>](/azure/azure-functions/functions-create-function-linux-custom-image)
- [<span data-ttu-id="fd762-143">Azure Functions 与 Kubernetes 事件驱动的自动缩放</span><span class="sxs-lookup"><span data-stu-id="fd762-143">Azure Functions with Kubernetes Event Driven Autoscaling</span></span>](/azure/azure-functions/functions-kubernetes-keda)
- [<span data-ttu-id="fd762-144">未的版本</span><span class="sxs-lookup"><span data-stu-id="fd762-144">Canary Release</span></span>](https://martinfowler.com/bliki/CanaryRelease.html)
- [<span data-ttu-id="fd762-145">Azure Dev Spaces 与 VS Code</span><span class="sxs-lookup"><span data-stu-id="fd762-145">Azure Dev Spaces with VS Code</span></span>](/azure/dev-spaces/quickstart-netcore)
- [<span data-ttu-id="fd762-146">与 Visual Studio Azure Dev Spaces</span><span class="sxs-lookup"><span data-stu-id="fd762-146">Azure Dev Spaces with Visual Studio</span></span>](/azure/dev-spaces/quickstart-netcore-visualstudio)
- [<span data-ttu-id="fd762-147">AKS 多节点池</span><span class="sxs-lookup"><span data-stu-id="fd762-147">AKS Multiple Node Pools</span></span>](/azure/aks/use-multiple-node-pools)
- [<span data-ttu-id="fd762-148">AKS 群集自动缩放程序</span><span class="sxs-lookup"><span data-stu-id="fd762-148">AKS Cluster Autoscaler</span></span>](/azure/aks/cluster-autoscaler)
- [<span data-ttu-id="fd762-149">教程：在 AKS 中缩放应用程序</span><span class="sxs-lookup"><span data-stu-id="fd762-149">Tutorial: Scale applications in AKS</span></span>](/azure/aks/tutorial-kubernetes-scale)
- [<span data-ttu-id="fd762-150">Azure Functions 的缩放和托管</span><span class="sxs-lookup"><span data-stu-id="fd762-150">Azure Functions scale and hosting</span></span>](/azure/azure-functions/functions-scale)
- [<span data-ttu-id="fd762-151">Azure 容器实例文档</span><span class="sxs-lookup"><span data-stu-id="fd762-151">Azure Container Instances Docs</span></span>](/azure/container-instances/)
- [<span data-ttu-id="fd762-152">从 ACR 部署容器实例</span><span class="sxs-lookup"><span data-stu-id="fd762-152">Deploy Container Instance from ACR</span></span>](/azure/container-instances/container-instances-using-azure-container-registry#deploy-with-azure-portal)

>[!div class="step-by-step"]
><span data-ttu-id="fd762-153">[上一页](scale-containers-serverless.md)
>[下一页](communication-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="fd762-153">[Previous](scale-containers-serverless.md)
[Next](communication-patterns.md)</span></span>

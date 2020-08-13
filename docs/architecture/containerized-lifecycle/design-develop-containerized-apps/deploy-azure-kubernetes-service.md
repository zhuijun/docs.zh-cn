---
title: 协调安排微服务和多容器应用程序，实现高可伸缩性和高可用性
description: 了解如何使用 Azure Kubernetes 服务部署应用。
ms.date: 08/06/2020
ms.openlocfilehash: b4deb9906e0fece7fb611b6988df576e8b07fe46
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916119"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a><span data-ttu-id="3f048-103">部署到 Azure Kubernetes 服务 (AKS)</span><span class="sxs-lookup"><span data-stu-id="3f048-103">Deploy to Azure Kubernetes Service (AKS)</span></span>

<span data-ttu-id="3f048-104">你可以使用安装了 Azure 命令行接口 (Azure CLI) 的首选客户端操作系统（Windows、macOS 或 Linux）与 AKS 进行交互。</span><span class="sxs-lookup"><span data-stu-id="3f048-104">You can interact with AKS using your preferred client operating system (Windows, macOS, or Linux) with Azure command-line interface(Azure CLI) installed.</span></span> <span data-ttu-id="3f048-105">有关更多详细信息，请参阅 [Azure CLI 文档](https://docs.microsoft.com/cli/azure/?view=azure-cli-latest)和[安装指南](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)，以了解可用的环境。</span><span class="sxs-lookup"><span data-stu-id="3f048-105">For more details, refer [Azure CLI documentation](https://docs.microsoft.com/cli/azure/?view=azure-cli-latest) and [Installation guide](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) for the available environments.</span></span>

## <a name="create-the-aks-environment-in-azure"></a><span data-ttu-id="3f048-106">在 Azure 中创建 AKS 环境</span><span class="sxs-lookup"><span data-stu-id="3f048-106">Create the AKS environment in Azure</span></span>

<span data-ttu-id="3f048-107">有多种方法可创建 AKS 环境。</span><span class="sxs-lookup"><span data-stu-id="3f048-107">There are several ways to create the AKS Environment.</span></span> <span data-ttu-id="3f048-108">可以使用 Azure-CLI 命令或使用 Azure 门户来完成此操作。</span><span class="sxs-lookup"><span data-stu-id="3f048-108">It can be done by using Azure CLI commands or by using the Azure portal.</span></span>

<span data-ttu-id="3f048-109">此处是有关使用 Azure-CLI 创建群集和通过 Azure 门户查看结果的一些示例。</span><span class="sxs-lookup"><span data-stu-id="3f048-109">Here you can explore some examples using the Azure CLI to create the cluster and the Azure portal to review the results.</span></span> <span data-ttu-id="3f048-110">还需要在开发计算机中安装 Kubectl 和 Docker。</span><span class="sxs-lookup"><span data-stu-id="3f048-110">You also need to have Kubectl and Docker in your development machine.</span></span>

## <a name="create-the-aks-cluster"></a><span data-ttu-id="3f048-111">创建 AKS 群集</span><span class="sxs-lookup"><span data-stu-id="3f048-111">Create the AKS cluster</span></span>

<span data-ttu-id="3f048-112">使用以下命令创建 AKS 群集（资源组必须存在）：</span><span class="sxs-lookup"><span data-stu-id="3f048-112">Create the AKS cluster using this command (the resource group must exist):</span></span>

```console
az aks create --resource-group explore-docker-aks-rg --name explore-docker-aks --node-vm-size Standard_B2s --node-count 1 --generate-ssh-keys --location westeurope
```

> [!NOTE]
> <span data-ttu-id="3f048-113">`--node-vm-size` 和 `--node-count` 参数值适用于样本/开发应用程序。</span><span class="sxs-lookup"><span data-stu-id="3f048-113">The `--node-vm-size` and `--node-count` parameter values are good enough for a sample/dev application.</span></span>

<span data-ttu-id="3f048-114">创建完作业后，你可以看到：</span><span class="sxs-lookup"><span data-stu-id="3f048-114">After the creation job finishes, you can see:</span></span>

- <span data-ttu-id="3f048-115">在初始资源组中创建的 AKS 群集</span><span class="sxs-lookup"><span data-stu-id="3f048-115">The AKS cluster created in the initial resource group</span></span>
- <span data-ttu-id="3f048-116">一个新的相关资源组，其中包含与 AKS 群集相关的资源，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="3f048-116">A new, related resource group, containing the resources related to the AKS cluster, as show in the following images.</span></span>

<span data-ttu-id="3f048-117">带有 AKS 群集的初始资源组：</span><span class="sxs-lookup"><span data-stu-id="3f048-117">The initial resource group, with the AKS cluster:</span></span>

![AKS 资源组的浏览器视图。](media/deploy-azure-kubernetes-service/aks-cluster-view.png)

<span data-ttu-id="3f048-119">**图 4-17**。</span><span class="sxs-lookup"><span data-stu-id="3f048-119">**Figure 4-17**.</span></span> <span data-ttu-id="3f048-120">Azure 的 AKS 资源组视图。</span><span class="sxs-lookup"><span data-stu-id="3f048-120">AKS Resource Group view from Azure.</span></span>

<span data-ttu-id="3f048-121">AKS 群集资源组：</span><span class="sxs-lookup"><span data-stu-id="3f048-121">The AKS cluster resource group:</span></span>

![Azure AKS 资源组的浏览器视图。](media/deploy-azure-kubernetes-service/aks-resource-group-view.png)

<span data-ttu-id="3f048-123">**图 4-18**.</span><span class="sxs-lookup"><span data-stu-id="3f048-123">**Figure 4-18**.</span></span> <span data-ttu-id="3f048-124">Azure 的 AKS 视图。</span><span class="sxs-lookup"><span data-stu-id="3f048-124">AKS view from Azure.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3f048-125">通常无需修改 AKS 群集资源组中的资源。</span><span class="sxs-lookup"><span data-stu-id="3f048-125">In general, you shouldn't need to modify the resources in the AKS cluster resource group.</span></span> <span data-ttu-id="3f048-126">例如，删除 AKS 群集时，资源组随之删除。</span><span class="sxs-lookup"><span data-stu-id="3f048-126">For example, the resource group is deleted when you delete the AKS cluster.</span></span>

<span data-ttu-id="3f048-127">还可以查看使用 `Azure CLI` 和 `Kubectl` 创建的节点。</span><span class="sxs-lookup"><span data-stu-id="3f048-127">You can also view the node created using `Azure CLI` and `Kubectl`.</span></span>

<span data-ttu-id="3f048-128">首先，获取凭据：</span><span class="sxs-lookup"><span data-stu-id="3f048-128">First, getting the credentials:</span></span>

```console
az aks get-credentials --resource-group explore-docker-aks-rg --name explore-docker-aks
```

![来自上述命令的控制台输出：将“explore-docker-aks”合并为 /home/miguel/.kube/config 中的当前上下文。](media/deploy-azure-kubernetes-service/get-credentials-command-result.png)

<span data-ttu-id="3f048-130">**图 4-19**.</span><span class="sxs-lookup"><span data-stu-id="3f048-130">**Figure 4-19**.</span></span> <span data-ttu-id="3f048-131">`aks get-credentials` 命令结果。</span><span class="sxs-lookup"><span data-stu-id="3f048-131">`aks get-credentials` command result.</span></span>

<span data-ttu-id="3f048-132">然后，从 Kubectl 获取节点：</span><span class="sxs-lookup"><span data-stu-id="3f048-132">And then, getting nodes from Kubectl:</span></span>

```console
kubectl get nodes
```

![来自上述命令的控制台输出：包括状态、时限（运行时间）和版本的节点列表](media/deploy-azure-kubernetes-service/kubectl-get-nodes-command-result.png)

<span data-ttu-id="3f048-134">图 4-20\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3f048-134">**Figure 4-20**.</span></span> <span data-ttu-id="3f048-135">`kubectl get nodes` 命令结果。</span><span class="sxs-lookup"><span data-stu-id="3f048-135">`kubectl get nodes` command result.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="3f048-136">[上一页](orchestrate-high-scalability-availability.md)
> [下一页](docker-apps-development-environment.md)</span><span class="sxs-lookup"><span data-stu-id="3f048-136">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-development-environment.md)</span></span>

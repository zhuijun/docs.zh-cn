---
title: 缩放容器和无服务器应用程序
description: 利用 Azure Kubernetes 服务缩放云本机应用程序以满足用户需求。
ms.date: 05/13/2020
ms.openlocfilehash: edf56ba50ba391e06e588d682918cd473a2cf374
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165974"
---
# <a name="scaling-containers-and-serverless-applications"></a><span data-ttu-id="cb7fd-103">缩放容器和无服务器应用程序</span><span class="sxs-lookup"><span data-stu-id="cb7fd-103">Scaling containers and serverless applications</span></span>

<span data-ttu-id="cb7fd-104">缩放应用程序的方法有两种：向上或向外缩放。前者是指将容量添加到单个资源，而后者则是指添加更多的资源来增加容量。</span><span class="sxs-lookup"><span data-stu-id="cb7fd-104">There are two ways to scale an application: up or out. The former refers to adding capacity to a single resource, while the latter refers to adding more resources to increase capacity.</span></span>

## <a name="the-simple-solution-scaling-up"></a><span data-ttu-id="cb7fd-105">简单的解决方案：向上缩放</span><span class="sxs-lookup"><span data-stu-id="cb7fd-105">The simple solution: scaling up</span></span>

<span data-ttu-id="cb7fd-106">升级具有增加的 CPU、内存、磁盘 i/o 速度和网络 i/o 速度的现有主机服务器称为 " *向上缩放*"。</span><span class="sxs-lookup"><span data-stu-id="cb7fd-106">Upgrading an existing host server with increased CPU, memory, disk I/O speed, and network I/O speed is known as *scaling up*.</span></span> <span data-ttu-id="cb7fd-107">扩展云本机应用程序涉及从云供应商处选择更强大的资源。</span><span class="sxs-lookup"><span data-stu-id="cb7fd-107">Scaling up a cloud-native application involves choosing more capable resources from the cloud vendor.</span></span> <span data-ttu-id="cb7fd-108">例如，你可以在 Kubernetes 群集中使用具有更大 Vm 的新节点池。</span><span class="sxs-lookup"><span data-stu-id="cb7fd-108">For example, you can a new node pool with larger VMs in your Kubernetes cluster.</span></span> <span data-ttu-id="cb7fd-109">然后，将容器化服务迁移到新池。</span><span class="sxs-lookup"><span data-stu-id="cb7fd-109">Then, migrate your containerized services to the new pool.</span></span>

<span data-ttu-id="cb7fd-110">无服务器应用通过从专用应用服务计划中选择 [高级函数计划](/azure/azure-functions/functions-scale) 或高级实例大小进行扩展。</span><span class="sxs-lookup"><span data-stu-id="cb7fd-110">Serverless apps scale up by choosing the [premium Functions plan](/azure/azure-functions/functions-scale) or premium instance sizes from a dedicated app service plan.</span></span>

## <a name="scaling-out-cloud-native-apps"></a><span data-ttu-id="cb7fd-111">向外扩展云本机应用</span><span class="sxs-lookup"><span data-stu-id="cb7fd-111">Scaling out cloud-native apps</span></span>

<span data-ttu-id="cb7fd-112">云本机应用程序通常会经历较大的需求波动，并需要一段时间的通知。</span><span class="sxs-lookup"><span data-stu-id="cb7fd-112">Cloud-native applications often experience large fluctuations in demand and require scale on a moment's notice.</span></span> <span data-ttu-id="cb7fd-113">它们倾向于横向扩展。通过向现有群集添加 (称为节点) 或应用程序实例的其他计算机，横向扩展。</span><span class="sxs-lookup"><span data-stu-id="cb7fd-113">They favor scaling out. Scaling out is done horizontally by adding additional machines (called nodes) or application instances to an existing cluster.</span></span> <span data-ttu-id="cb7fd-114">在 Kubernetes 中，可以通过调整应用的配置设置来进行手动缩放 (例如， [缩放节点池](/azure/aks/use-multiple-node-pools#scale-a-node-pool-manually)) 或通过自动缩放。</span><span class="sxs-lookup"><span data-stu-id="cb7fd-114">In Kubernetes, you can scale manually by adjusting configuration settings for the app (for example, [scaling a node pool](/azure/aks/use-multiple-node-pools#scale-a-node-pool-manually)), or through autoscaling.</span></span>

<span data-ttu-id="cb7fd-115">AKS 群集可通过以下两种方式之一进行自动缩放：</span><span class="sxs-lookup"><span data-stu-id="cb7fd-115">AKS clusters can autoscale in one of two ways:</span></span>

<span data-ttu-id="cb7fd-116">首先， [横向 Pod 自动缩放程序](/azure/aks/tutorial-kubernetes-scale#autoscale-pods) 监视资源需求，并自动缩放 Pod 副本以满足此要求。</span><span class="sxs-lookup"><span data-stu-id="cb7fd-116">First, the [Horizontal Pod Autoscaler](/azure/aks/tutorial-kubernetes-scale#autoscale-pods) monitors resource demand and automatically scales your POD replicas to meet it.</span></span> <span data-ttu-id="cb7fd-117">当流量增加时，会自动预配其他副本以扩展你的服务。</span><span class="sxs-lookup"><span data-stu-id="cb7fd-117">When traffic increases, additional replicas are automatically provisioned to scale out your services.</span></span> <span data-ttu-id="cb7fd-118">同样，当需求减少时，它们将被删除以进行扩展。</span><span class="sxs-lookup"><span data-stu-id="cb7fd-118">Likewise, when demand decreases, they're removed to scale-in your services.</span></span> <span data-ttu-id="cb7fd-119">定义要缩放的指标，例如 CPU 使用率。</span><span class="sxs-lookup"><span data-stu-id="cb7fd-119">You define the metric on which to scale, for example, CPU usage.</span></span> <span data-ttu-id="cb7fd-120">你还可以指定要运行的最小和最大副本数。</span><span class="sxs-lookup"><span data-stu-id="cb7fd-120">You can also specify the minimum and maximum number of replicas to run.</span></span> <span data-ttu-id="cb7fd-121">AKS 监视该度量值并相应地进行缩放。</span><span class="sxs-lookup"><span data-stu-id="cb7fd-121">AKS monitors that metric and scales accordingly.</span></span>

<span data-ttu-id="cb7fd-122">接下来， [AKS Cluster 自动缩放程序](/azure/aks/cluster-autoscaler) 功能使你能够跨 Kubernetes 群集自动缩放计算节点，以满足需求。</span><span class="sxs-lookup"><span data-stu-id="cb7fd-122">Next, the [AKS Cluster Autoscaler](/azure/aks/cluster-autoscaler) feature enables you to automatically scale compute nodes across a Kubernetes cluster to meet demand.</span></span> <span data-ttu-id="cb7fd-123">通过此功能，可以在需要的多个计算容量时，自动将新 Vm 添加到基础 Azure 虚拟机规模集。</span><span class="sxs-lookup"><span data-stu-id="cb7fd-123">With it, you can automatically add new VMs to the underlying Azure Virtual Machine Scale Set whenever more compute capacity of is required.</span></span> <span data-ttu-id="cb7fd-124">它还会在不再需要节点时将其删除。</span><span class="sxs-lookup"><span data-stu-id="cb7fd-124">It also removes nodes when no longer required.</span></span>

<span data-ttu-id="cb7fd-125">图3-13 显示了这两个缩放服务之间的关系。</span><span class="sxs-lookup"><span data-stu-id="cb7fd-125">Figure 3-13 shows the relationship between these two scaling services.</span></span>

![向外扩展应用服务计划。](./media/aks-cluster-autoscaler.png)

<span data-ttu-id="cb7fd-127">**图 3-13**。</span><span class="sxs-lookup"><span data-stu-id="cb7fd-127">**Figure 3-13**.</span></span> <span data-ttu-id="cb7fd-128">向外扩展应用服务计划。</span><span class="sxs-lookup"><span data-stu-id="cb7fd-128">Scaling out an App Service plan.</span></span>

<span data-ttu-id="cb7fd-129">同时，两者都确保容器实例和计算节点获得最佳数量，以支持波动需求。</span><span class="sxs-lookup"><span data-stu-id="cb7fd-129">Working together, both ensure an optimal number of container instances and compute nodes to support fluctuating demand.</span></span> <span data-ttu-id="cb7fd-130">横向 pod 自动缩放程序优化所需的 pod 数。</span><span class="sxs-lookup"><span data-stu-id="cb7fd-130">The horizontal pod autoscaler optimizes the number of pods required.</span></span> <span data-ttu-id="cb7fd-131">群集自动缩放程序优化所需的节点数。</span><span class="sxs-lookup"><span data-stu-id="cb7fd-131">The cluster autoscaler optimizes the number of nodes required.</span></span>

### <a name="scaling-azure-functions"></a><span data-ttu-id="cb7fd-132">缩放 Azure Functions</span><span class="sxs-lookup"><span data-stu-id="cb7fd-132">Scaling Azure Functions</span></span>

<span data-ttu-id="cb7fd-133">Azure Functions 根据需要自动横向扩展。</span><span class="sxs-lookup"><span data-stu-id="cb7fd-133">Azure Functions automatically scale out upon demand.</span></span> <span data-ttu-id="cb7fd-134">服务器资源是基于触发事件的数量动态分配和删除的。</span><span class="sxs-lookup"><span data-stu-id="cb7fd-134">Server resources are dynamically allocated and removed based on the number of triggered events.</span></span> <span data-ttu-id="cb7fd-135">只需为运行函数时使用的计算资源付费。</span><span class="sxs-lookup"><span data-stu-id="cb7fd-135">You're only charged for compute resources consumed when your functions run.</span></span> <span data-ttu-id="cb7fd-136">计费基于执行次数、执行时间和使用的内存。</span><span class="sxs-lookup"><span data-stu-id="cb7fd-136">Billing is based upon the number of executions, execution time, and memory used.</span></span>

<span data-ttu-id="cb7fd-137">尽管默认消耗计划为大多数应用提供经济实惠的可缩放解决方案，但 "高级" 选项允许开发人员灵活应对自定义 Azure Functions 要求。</span><span class="sxs-lookup"><span data-stu-id="cb7fd-137">While the default consumption plan provides an economical and scalable solution for most apps, the premium option allows developers flexibility for custom Azure Functions requirements.</span></span> <span data-ttu-id="cb7fd-138">升级到高级计划可对实例大小、准备好实例进行控制， (避免冷启动延迟) 和专用 Vm。</span><span class="sxs-lookup"><span data-stu-id="cb7fd-138">Upgrading to the premium plan provides control over instance sizes, pre-warmed instances (to avoid cold start delays), and dedicated VMs.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="cb7fd-139">[上一页](deploy-containers-azure.md)
>[下一页](other-deployment-options.md)</span><span class="sxs-lookup"><span data-stu-id="cb7fd-139">[Previous](deploy-containers-azure.md)
[Next](other-deployment-options.md)</span></span>

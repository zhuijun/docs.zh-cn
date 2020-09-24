---
title: 在 Azure Kubernetes 服务中进行监视
description: 在 Azure Kubernetes 服务中进行监视
ms.date: 05/13/2020
ms.openlocfilehash: 3900f169b9be4f807e72392da38a1224d6ce28e3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163695"
---
# <a name="monitoring-in-azure-kubernetes-services"></a><span data-ttu-id="9edc1-103">在 Azure Kubernetes 服务中进行监视</span><span class="sxs-lookup"><span data-stu-id="9edc1-103">Monitoring in Azure Kubernetes Services</span></span>

<span data-ttu-id="9edc1-104">Kubernetes 中的内置日志记录为基元。</span><span class="sxs-lookup"><span data-stu-id="9edc1-104">The built-in logging in Kubernetes is primitive.</span></span> <span data-ttu-id="9edc1-105">但是，有一些极佳的选项可让你从 Kubernetes 中取出日志，并将其放在正确分析的位置。</span><span class="sxs-lookup"><span data-stu-id="9edc1-105">However, there are some great options for getting the logs out of Kubernetes and into a place where they can be properly analyzed.</span></span> <span data-ttu-id="9edc1-106">如果需要监视 AKS 群集，为 Kubernetes 配置弹性堆栈是一种很好的解决方案。</span><span class="sxs-lookup"><span data-stu-id="9edc1-106">If you need to monitor your AKS clusters, configuring Elastic Stack for Kubernetes is a great solution.</span></span>

## <a name="azure-monitor-for-containers"></a><span data-ttu-id="9edc1-107">用于容器的 Azure Monitor</span><span class="sxs-lookup"><span data-stu-id="9edc1-107">Azure Monitor for Containers</span></span>

<span data-ttu-id="9edc1-108">[容器 Azure Monitor](/azure/azure-monitor/insights/container-insights-overview) 不仅支持从 Kubernetes 使用日志，还支持从其他业务流程引擎（例如 DC/OS、Docker Swarm 和 Red Hat OpenShift）使用日志。</span><span class="sxs-lookup"><span data-stu-id="9edc1-108">[Azure Monitor for Containers](/azure/azure-monitor/insights/container-insights-overview) supports consuming logs from not just Kubernetes but also from other orchestration engines such as DC/OS, Docker Swarm, and Red Hat OpenShift.</span></span>

<span data-ttu-id="9edc1-109">![使用不同容器中的日志 ](./media/containers-diagram.png)
 **图 7-10**。</span><span class="sxs-lookup"><span data-stu-id="9edc1-109">![Consuming logs from various containers](./media/containers-diagram.png)
**Figure 7-10**.</span></span> <span data-ttu-id="9edc1-110">使用不同容器中的日志</span><span class="sxs-lookup"><span data-stu-id="9edc1-110">Consuming logs from various containers</span></span>

<span data-ttu-id="9edc1-111">[Prometheus](https://prometheus.io/) 是一个流行的开源指标监视解决方案。</span><span class="sxs-lookup"><span data-stu-id="9edc1-111">[Prometheus](https://prometheus.io/) is a popular open source metric monitoring solution.</span></span> <span data-ttu-id="9edc1-112">它属于云本机计算基础。</span><span class="sxs-lookup"><span data-stu-id="9edc1-112">It is part of the Cloud Native Compute Foundation.</span></span> <span data-ttu-id="9edc1-113">通常，使用 Prometheus 需要使用其自己的存储管理 Prometheus 服务器。</span><span class="sxs-lookup"><span data-stu-id="9edc1-113">Typically, using Prometheus requires managing a Prometheus server with its own store.</span></span> <span data-ttu-id="9edc1-114">但是， [为容器 Azure Monitor 提供与 Prometheus 指标端点的直接集成](/azure/azure-monitor/insights/container-insights-prometheus-integration)，因此不需要单独的服务器。</span><span class="sxs-lookup"><span data-stu-id="9edc1-114">However, [Azure Monitor for Containers provides direct integration with Prometheus metrics endpoints](/azure/azure-monitor/insights/container-insights-prometheus-integration), so a separate server is not required.</span></span>

<span data-ttu-id="9edc1-115">日志和指标信息不只是从群集中运行的容器中收集，而是由群集本身进行收集。</span><span class="sxs-lookup"><span data-stu-id="9edc1-115">Log and metric information is gathered not just from the containers running in the cluster but also from the cluster hosts themselves.</span></span> <span data-ttu-id="9edc1-116">它允许将日志信息与这两者进行关联，这使得跟踪错误变得更加容易。</span><span class="sxs-lookup"><span data-stu-id="9edc1-116">It allows correlating log information from the two making it much easier to track down an error.</span></span>

<span data-ttu-id="9edc1-117">安装日志收集器不同于 [Windows](/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes) 和 [Linux](/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes) 群集。</span><span class="sxs-lookup"><span data-stu-id="9edc1-117">Installing the log collectors differs on [Windows](/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes) and [Linux](/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes) clusters.</span></span> <span data-ttu-id="9edc1-118">但在这两种情况下，日志集合都作为 Kubernetes [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/)实现，这意味着日志收集器将作为容器在每个节点上运行。</span><span class="sxs-lookup"><span data-stu-id="9edc1-118">But in both cases the log collection is implemented as a Kubernetes [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/), meaning that the log collector is run as a container on each of the nodes.</span></span>

<span data-ttu-id="9edc1-119">无论哪个协调器或操作系统运行 Azure Monitor 守护程序，日志信息都将转发到与用户熟悉的 Azure Monitor 工具。</span><span class="sxs-lookup"><span data-stu-id="9edc1-119">No matter which orchestrator or operating system is running the Azure Monitor daemon, the log information is forwarded to the same Azure Monitor tools with which users are familiar.</span></span> <span data-ttu-id="9edc1-120">这可确保在混合不同的日志源（如混合 Kubernetes/Azure Functions 环境）的环境中获得并行体验。</span><span class="sxs-lookup"><span data-stu-id="9edc1-120">This ensures a parallel experience in environments that mix different log sources such as a hybrid Kubernetes/Azure Functions environment.</span></span>

<span data-ttu-id="9edc1-121">![显示多个正在运行的容器中的日志记录和指标信息的示例仪表板。 ](./media/containers-dashboard.png)
**图 7-11**。</span><span class="sxs-lookup"><span data-stu-id="9edc1-121">![A sample dashboard showing logging and metric information from a number of running containers.](./media/containers-dashboard.png)
**Figure 7-11**.</span></span> <span data-ttu-id="9edc1-122">显示多个正在运行的容器中的日志记录和指标信息的示例仪表板。</span><span class="sxs-lookup"><span data-stu-id="9edc1-122">A sample dashboard showing logging and metric information from a number of running containers.</span></span>

## <a name="logfinalize"></a><span data-ttu-id="9edc1-123">Log. Finalize ( # A1</span><span class="sxs-lookup"><span data-stu-id="9edc1-123">Log.Finalize()</span></span>

<span data-ttu-id="9edc1-124">日志记录是在大规模部署任何应用程序时最忽略但最重要的部分之一。</span><span class="sxs-lookup"><span data-stu-id="9edc1-124">Logging is one of the most overlooked and yet most important parts of deploying any application at scale.</span></span> <span data-ttu-id="9edc1-125">随着应用程序的大小和复杂程度的增加，调试它们的难度也很大。</span><span class="sxs-lookup"><span data-stu-id="9edc1-125">As the size and complexity of applications increase, then so does the difficulty of debugging them.</span></span> <span data-ttu-id="9edc1-126">可用的高质量日志使调试变得更加简单，并将其从 "几乎不可能" 领域移到 "令人愉快的体验"。</span><span class="sxs-lookup"><span data-stu-id="9edc1-126">Having top quality logs available makes debugging much easier and moves it from the realm of "nearly impossible" to "a pleasant experience".</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9edc1-127">[上一页](logging-with-elastic-stack.md)
>[下一页](azure-monitor.md)</span><span class="sxs-lookup"><span data-stu-id="9edc1-127">[Previous](logging-with-elastic-stack.md)
[Next](azure-monitor.md)</span></span>

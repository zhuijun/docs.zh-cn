---
title: 通过监视和遥测对应用进行现代化
description: 通过 Azure 云和 Windows 容器现代化现有 .NET 应用程序 | 通过监视和遥测现代化应用
ms.date: 04/30/2018
ms.openlocfilehash: a6094435eece661d99904876ac49b3ca85ec45a7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171996"
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a><span data-ttu-id="70831-103">通过监视和遥测对应用进行现代化</span><span class="sxs-lookup"><span data-stu-id="70831-103">Modernize your apps with monitoring and telemetry</span></span>

<span data-ttu-id="70831-104">在生产环境中运行应用程序时，请务必了解应用程序的执行情况。</span><span class="sxs-lookup"><span data-stu-id="70831-104">When you run an application in production, it's critical that you have insights about how your application is performing.</span></span> <span data-ttu-id="70831-105">它是否在高级别下执行？</span><span class="sxs-lookup"><span data-stu-id="70831-105">Is it performing at a high level?</span></span> <span data-ttu-id="70831-106">用户是否遇到了错误，或是应用程序是否稳定和可靠？</span><span class="sxs-lookup"><span data-stu-id="70831-106">Are users getting errors, or is the application stable and reliable?</span></span> <span data-ttu-id="70831-107">你需要丰富的性能监视、功能强大的警报和仪表板，帮助确保应用程序可用且行为符合预期。</span><span class="sxs-lookup"><span data-stu-id="70831-107">You need rich performance monitoring, powerful alerting, and dashboards to help ensure that your application is available and performing as expected.</span></span> <span data-ttu-id="70831-108">还需要能够快速查看是否存在问题，确定受影响的客户数量，并执行根本原因分析来查找并解决问题。</span><span class="sxs-lookup"><span data-stu-id="70831-108">You also need to be able to see quickly if there's a problem, determine how many customers are affected, and perform a root-cause analysis to find and fix the issue.</span></span>

## <a name="monitor-your-application-with-application-insights"></a><span data-ttu-id="70831-109">使用 Application Insights 监视应用程序</span><span class="sxs-lookup"><span data-stu-id="70831-109">Monitor your application with Application Insights</span></span>

<span data-ttu-id="70831-110">Application Insights 是面向在多个平台上工作的 Web开发人员的可扩展应用程序性能管理 (APM) 服务。</span><span class="sxs-lookup"><span data-stu-id="70831-110">Application Insights is an extensible Application Performance Management (APM) service for web developers who work on multiple platforms.</span></span> <span data-ttu-id="70831-111">使用它可以监视实时 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="70831-111">Use it to monitor your live web application.</span></span> <span data-ttu-id="70831-112">Application Insights 可以自动检测性能异常。</span><span class="sxs-lookup"><span data-stu-id="70831-112">Application Insights automatically detects performance anomalies.</span></span> <span data-ttu-id="70831-113">其中包含强大的分析工具来帮助诊断问题，帮助你了解用户在应用中实际执行了哪些操作。</span><span class="sxs-lookup"><span data-stu-id="70831-113">It includes powerful analytics tools to help you diagnose issues, and to help you understand what users actually do with your app.</span></span> <span data-ttu-id="70831-114">Application Insights 旨在帮助持续提高性能与可用性。</span><span class="sxs-lookup"><span data-stu-id="70831-114">Application Insights is designed to help you continuously improve performance and usability.</span></span> <span data-ttu-id="70831-115">它适用于各种平台（包括 .NET、Node.js 和 J2EE）中的应用，不管这些应用是托管在本地还是云中。</span><span class="sxs-lookup"><span data-stu-id="70831-115">It works for apps on a wide variety of platforms, including .NET, Node.js, and J2EE, whether hosted on-premises or in the cloud.</span></span> <span data-ttu-id="70831-116">Application Insights 与 DevOps 进程集成，并且具有与不同开发工具的连接点。</span><span class="sxs-lookup"><span data-stu-id="70831-116">Application Insights integrates with your DevOps processes, and has connection points to a variety of development tools.</span></span>

<span data-ttu-id="70831-117">图 4-10 显示的示例说明了 Application Insights 如何监视应用程序以及它如何将这些见解呈现给仪表板。</span><span class="sxs-lookup"><span data-stu-id="70831-117">Figure 4-10 shows an example of how Application Insights monitors your application and how it surfaces those insights to a dashboard.</span></span>

![Application Insights 监视仪表板的屏幕截图。](./media/modernize-your-apps-with-monitoring-and-telemetry/application-insights-monitoring-dashboard.png)

<span data-ttu-id="70831-119">**图 4-10.**</span><span class="sxs-lookup"><span data-stu-id="70831-119">**Figure 4-10.**</span></span> <span data-ttu-id="70831-120">Application Insights 监视仪表板</span><span class="sxs-lookup"><span data-stu-id="70831-120">Application Insights monitoring dashboard</span></span>

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a><span data-ttu-id="70831-121">利用 Log Analytics 及其容器监视解决方案监视 Docker 基础结构</span><span class="sxs-lookup"><span data-stu-id="70831-121">Monitor your Docker infrastructure with Log Analytics and its Container Monitoring solution</span></span>

<span data-ttu-id="70831-122">[Azure Log Analytics](/azure/log-analytics/log-analytics-overview) 是 [Microsoft Azure 总体监视解决方案](/azure/monitoring-and-diagnostics/monitoring-overview)的一部分。</span><span class="sxs-lookup"><span data-stu-id="70831-122">[Azure Log Analytics](/azure/log-analytics/log-analytics-overview) is part of the [Microsoft Azure overall monitoring solution](/azure/monitoring-and-diagnostics/monitoring-overview).</span></span> <span data-ttu-id="70831-123">它也是 [Operations Management Suite (OMS)](/azure/operations-management-suite/operations-management-suite-overview) 中的服务。</span><span class="sxs-lookup"><span data-stu-id="70831-123">It's also a service in [Operations Management Suite (OMS)](/azure/operations-management-suite/operations-management-suite-overview).</span></span> <span data-ttu-id="70831-124">Log Analytics 可监视云和本地环境（OMS 适用于本地），使其保持较高的可用性和性能。</span><span class="sxs-lookup"><span data-stu-id="70831-124">Log Analytics monitors cloud and on-premises environments (OMS for on-premises) to help maintain availability and performance.</span></span> <span data-ttu-id="70831-125">它可以收集云和本地环境中的资源生成的数据以及其他监视工具的数据，针对多个源提供分析。</span><span class="sxs-lookup"><span data-stu-id="70831-125">It collects data generated by resources in your cloud and on-premises environments and from other monitoring tools to provide analysis across multiple sources.</span></span>

<span data-ttu-id="70831-126">与 Azure 基础结构日志相关，Log Analytics 作为 Azure 服务，从其他 Azure 服务（通过 [Azure Monitor](/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)）、Azure VM、Docker 容器以及本地或其他云基础结构引入日志和指标数据。</span><span class="sxs-lookup"><span data-stu-id="70831-126">In relation to Azure infrastructure logs, Log Analytics, as an Azure service, ingests log and metric data from other Azure services (via [Azure Monitor](/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)), Azure VMs, Docker containers, and on-premises or other cloud infrastructures.</span></span> <span data-ttu-id="70831-127">Log Analytics 在此数据的基础上提供灵活的日志搜索和现成的分析。</span><span class="sxs-lookup"><span data-stu-id="70831-127">Log Analytics offers flexible log search and out-of-the box analytics on top of this data.</span></span> <span data-ttu-id="70831-128">它提供丰富的工具以用于跨多个源分析数据，允许针对所有日志运行复杂的查询，并可以根据指定的条件主动发出警报。</span><span class="sxs-lookup"><span data-stu-id="70831-128">It provides rich tools that you can use to analyze data across sources, it allows complex queries across all logs, and it can proactively alert based on specified conditions.</span></span> <span data-ttu-id="70831-129">甚至可将自定义数据收集到它的中心 Log Analytics 存储库，你可在其中查询和可视化这些数据。</span><span class="sxs-lookup"><span data-stu-id="70831-129">You can even collect custom data in the central Log Analytics repository, where you can query and visualize it.</span></span> <span data-ttu-id="70831-130">还可以利用 Log Analytics 的内置解决方案，立即获取基础结构安全性与功能的见解。</span><span class="sxs-lookup"><span data-stu-id="70831-130">You can also take advantage of the Log Analytics built-in solutions to immediately gain insights into the security and functionality of your infrastructure.</span></span>

<span data-ttu-id="70831-131">可以通过在任意浏览器中运行的 OMS 门户或 Azure 门户访问 Log Analytics。在这些门户中，可以访问配置设置和多个工具来分析和处理收集的数据。</span><span class="sxs-lookup"><span data-stu-id="70831-131">You can access Log Analytics through the OMS portal or the Azure portal, which run in any browser, and provide you with access to configuration settings and multiple tools to analyze and act on collected data.</span></span>

<span data-ttu-id="70831-132">Log Analytics 中的[容器监视解决方案](/azure/log-analytics/log-analytics-containers)可帮助用户在单个位置查看和管理 Docker 和 Windows 容器主机。</span><span class="sxs-lookup"><span data-stu-id="70831-132">The [Container Monitoring solution](/azure/log-analytics/log-analytics-containers) in Log Analytics helps you view and manage your Docker and Windows Container hosts in a single location.</span></span> <span data-ttu-id="70831-133">解决方案显示哪些容器正在运行，它们正在运行哪些容器映像以及正在运行容器的位置。</span><span class="sxs-lookup"><span data-stu-id="70831-133">The solution shows which containers are running, what container image they're running, and where containers are running.</span></span> <span data-ttu-id="70831-134">可以查看详细审核信息，其中包括了与容器一起使用的命令。</span><span class="sxs-lookup"><span data-stu-id="70831-134">You can view detailed audit information, including commands that are being used with containers.</span></span> <span data-ttu-id="70831-135">用户还可以通过查看和搜索集中式日志来排查容器问题，而无需远程查看 Docker 或 Windows 主机。</span><span class="sxs-lookup"><span data-stu-id="70831-135">You can also troubleshoot containers by viewing and searching centralized logs, without needing to remotely view Docker or Windows hosts.</span></span> <span data-ttu-id="70831-136">可以在主机上找到可能具有干扰性并且占用过多资源的容器。</span><span class="sxs-lookup"><span data-stu-id="70831-136">You can find containers that might be noisy and consuming excess resources on a host.</span></span> <span data-ttu-id="70831-137">此外，还可以查看容器的集中式 CPU、内存、存储器、网络使用情况和性能信息。</span><span class="sxs-lookup"><span data-stu-id="70831-137">Additionally, you can view centralized CPU, memory, storage, and network usage, and performance information, for containers.</span></span> <span data-ttu-id="70831-138">在运行 Windows 的计算机上，可以集中比较 Windows Server、Hyper-V 和 Docker 容器中的日志。</span><span class="sxs-lookup"><span data-stu-id="70831-138">On computers running Windows, you can centralize and compare logs from Windows Server, Hyper-V, and Docker containers.</span></span> <span data-ttu-id="70831-139">解决方案支持以下容器 Orchestrator：</span><span class="sxs-lookup"><span data-stu-id="70831-139">The solution supports the following container orchestrators:</span></span>

- <span data-ttu-id="70831-140">Docker Swarm</span><span class="sxs-lookup"><span data-stu-id="70831-140">Docker Swarm</span></span>

- <span data-ttu-id="70831-141">DC/OS</span><span class="sxs-lookup"><span data-stu-id="70831-141">DC/OS</span></span>

- <span data-ttu-id="70831-142">Kubernetes</span><span class="sxs-lookup"><span data-stu-id="70831-142">Kubernetes</span></span>

- <span data-ttu-id="70831-143">Red Hat OpenShift</span><span class="sxs-lookup"><span data-stu-id="70831-143">Red Hat OpenShift</span></span>

<span data-ttu-id="70831-144">图 4-11 显示了各种容器主机、代理和 OMS 之间的关系。</span><span class="sxs-lookup"><span data-stu-id="70831-144">Figure 4-11 shows the relationships between various container hosts and agents and OMS.</span></span>

![Log Analytics 容器监视解决方案的屏幕截图。](./media/modernize-your-apps-with-monitoring-and-telemetry/log-analytics-container-monitoring-solution.png)

<span data-ttu-id="70831-146">**图 4-11.**</span><span class="sxs-lookup"><span data-stu-id="70831-146">**Figure 4-11.**</span></span> <span data-ttu-id="70831-147">Log Analytics 容器监视解决方案</span><span class="sxs-lookup"><span data-stu-id="70831-147">Log Analytics Container Monitoring solution</span></span>

<span data-ttu-id="70831-148">你可以将 Log Analytics 容器监视解决方案用于：</span><span class="sxs-lookup"><span data-stu-id="70831-148">You can use the Log Analytics Container Monitoring solution to:</span></span>

- <span data-ttu-id="70831-149">查看单个位置中有关所有容器主机的信息。</span><span class="sxs-lookup"><span data-stu-id="70831-149">See information about all container hosts in a single location.</span></span>

- <span data-ttu-id="70831-150">了解正在运行的容器、正在运行的映像以及它们的运行位置。</span><span class="sxs-lookup"><span data-stu-id="70831-150">Know which containers are running, what image they're running, and where they're running.</span></span>

- <span data-ttu-id="70831-151">查看容器上操作的审核线索。</span><span class="sxs-lookup"><span data-stu-id="70831-151">See an audit trail for actions on containers.</span></span>

- <span data-ttu-id="70831-152">通过查看和搜索集中式日志进行故障排除，而无需远程登录到 Docker 主机。</span><span class="sxs-lookup"><span data-stu-id="70831-152">Troubleshoot by viewing and searching centralized logs without remote login to the Docker hosts.</span></span>

- <span data-ttu-id="70831-153">在主机上找到可能是“具有干扰性的邻域”并且占用过多资源的容器。</span><span class="sxs-lookup"><span data-stu-id="70831-153">Find containers that might be "noisy neighbors," and be consuming excess resources on a host.</span></span>

- <span data-ttu-id="70831-154">查看容器的集中式 CPU、内存、存储器、网络使用情况和性能信息。</span><span class="sxs-lookup"><span data-stu-id="70831-154">View centralized CPU, memory, storage, and network usage, and performance information, for containers.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="70831-155">其他资源</span><span class="sxs-lookup"><span data-stu-id="70831-155">Additional resources</span></span>

- <span data-ttu-id="70831-156">**Microsoft Azure 中的监视概述**</span><span class="sxs-lookup"><span data-stu-id="70831-156">**Overview of monitoring in Microsoft Azure**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="70831-157">**什么是 Application Insights？**</span><span class="sxs-lookup"><span data-stu-id="70831-157">**What is Application Insights?**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- <span data-ttu-id="70831-158">**什么是 Log Analytics？**</span><span class="sxs-lookup"><span data-stu-id="70831-158">**What is Log Analytics?**</span></span>

<https://docs.microsoft.com/azure/log-analytics/log-analytics-overview>

- <span data-ttu-id="70831-159">**Azure Monitor 中的容器监视解决方案**</span><span class="sxs-lookup"><span data-stu-id="70831-159">**Container Monitoring solution in Azure Monitor**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/insights/containers>

- <span data-ttu-id="70831-160">**Azure Monitor 概述**</span><span class="sxs-lookup"><span data-stu-id="70831-160">**Overview of Azure Monitor**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="70831-161">**什么是 Operations Management Suite (OMS)？**</span><span class="sxs-lookup"><span data-stu-id="70831-161">**What is Operations Management Suite (OMS)?**</span></span>

<https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview>

>[!div class="step-by-step"]
><span data-ttu-id="70831-162">[上一页](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
>[下一页](life-cycle-ci-cd-pipelines-devops-tools.md)</span><span class="sxs-lookup"><span data-stu-id="70831-162">[Previous](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
[Next](life-cycle-ci-cd-pipelines-devops-tools.md)</span></span>

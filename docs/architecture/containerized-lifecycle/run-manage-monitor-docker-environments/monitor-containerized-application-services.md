---
title: 监视容器化应用程序服务
description: 了解监控容器体系结构的一些关键方面
ms.date: 02/15/2019
ms.openlocfilehash: e41df53ad94784436442c3cf7defed3fab510455
ms.sourcegitcommit: e7748001b1cee80ced691d8a76ca814c0b02dd9b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86374437"
---
# <a name="monitor-containerized-application-services"></a><span data-ttu-id="7927a-103">监视容器化应用程序服务</span><span class="sxs-lookup"><span data-stu-id="7927a-103">Monitor containerized application services</span></span>

<span data-ttu-id="7927a-104">对于分成多个容器和微服务的应用程序来说，关键是要有一种方法来监视和分析整个应用程序的行为。</span><span class="sxs-lookup"><span data-stu-id="7927a-104">It's critical for applications split into multiple containers and microservices to have a way to monitor and analyze the behavior of the whole application.</span></span>

## <a name="azure-monitor"></a><span data-ttu-id="7927a-105">Azure Monitor</span><span class="sxs-lookup"><span data-stu-id="7927a-105">Azure Monitor</span></span>

<span data-ttu-id="7927a-106">[Azure Monitor](https://azure.microsoft.com/services/monitor/) 是一种可扩展的分析服务，可监视实时 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="7927a-106">[Azure Monitor](https://azure.microsoft.com/services/monitor/) is an extensible analytics service that monitors your live application.</span></span> <span data-ttu-id="7927a-107">它可以帮助检测和诊断性能问题，并了解用户实际使用应用的情况。</span><span class="sxs-lookup"><span data-stu-id="7927a-107">It helps you to detect and diagnose performance issues and to understand what users actually do with your app.</span></span> <span data-ttu-id="7927a-108">它专为开发人员设计，旨在帮助你不断提高服务或应用程序的性能和可用性。</span><span class="sxs-lookup"><span data-stu-id="7927a-108">It's designed for developers, with the intent of helping you to continuously improve the performance and usability of your services or applications.</span></span> <span data-ttu-id="7927a-109">Azure Monitor 可与各种平台上的 Web/服务和独立应用程序配合使用，如 .NET、Java、Node.js 以及本地或云端托管的许多其他平台。</span><span class="sxs-lookup"><span data-stu-id="7927a-109">Azure Monitor works with both web/services and standalone apps on a wide variety of platforms like .NET, Java, Node.js and many other platforms, hosted on-premises or in the cloud.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="7927a-110">其他资源</span><span class="sxs-lookup"><span data-stu-id="7927a-110">Additional resources</span></span>

- <span data-ttu-id="7927a-111">**Azure Monitor 概述** </span><span class="sxs-lookup"><span data-stu-id="7927a-111">**Overview of Azure Monitor** </span></span>\
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="7927a-112">**什么是 Application Insights？**</span><span class="sxs-lookup"><span data-stu-id="7927a-112">**What is Application Insights?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- <span data-ttu-id="7927a-113">**什么是 Azure Monitor 指标？**</span><span class="sxs-lookup"><span data-stu-id="7927a-113">**What is Azure Monitor Metrics?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- <span data-ttu-id="7927a-114">**Azure Monitor 中的容器监视解决方案** </span><span class="sxs-lookup"><span data-stu-id="7927a-114">**Container Monitoring solution in Azure Monitor** </span></span>\
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a><span data-ttu-id="7927a-115">安全性和备份服务</span><span class="sxs-lookup"><span data-stu-id="7927a-115">Security and backup services</span></span>

<span data-ttu-id="7927a-116">为了确保应用程序和基础设施处于最佳状态以支持业务需求，必须处理许多细节方面的支持工作，而在微服务领域，情况变得更加复杂，因此需要一种在需要采取行动时既有高级视图又有详细视图的方法。</span><span class="sxs-lookup"><span data-stu-id="7927a-116">There are many support chores with lots of details that you have to handle to ensure your applications and infrastructure are in top notch condition to support business needs, and the situation becomes more complicated in the microservices realm, so you need a way to have both high-level and detailed views when you need to take action.</span></span>

<span data-ttu-id="7927a-117">Azure 具有管理和提供云和本地资源的四个关键方面的统一视图的工具：</span><span class="sxs-lookup"><span data-stu-id="7927a-117">Azure has the tools to manage and provide a unified view of four critical aspects of both your cloud and on-premises resources:</span></span>

- <span data-ttu-id="7927a-118">**安全性**。</span><span class="sxs-lookup"><span data-stu-id="7927a-118">**Security**.</span></span> <span data-ttu-id="7927a-119">使用 [Azure 安全中心](https://azure.microsoft.com/services/security-center/)。</span><span class="sxs-lookup"><span data-stu-id="7927a-119">With [Azure Security Center](https://azure.microsoft.com/services/security-center/).</span></span>
  - <span data-ttu-id="7927a-120">全面了解并控制虚拟机、应用和工作负载的安全性。</span><span class="sxs-lookup"><span data-stu-id="7927a-120">Get full visibility and control over the security of your virtual machines, apps, and workloads.</span></span>
  - <span data-ttu-id="7927a-121">集中管理安全策略并集成现有流程和工具。</span><span class="sxs-lookup"><span data-stu-id="7927a-121">Centralize the management of your security policies and integrate existing processes and tools.</span></span>
  - <span data-ttu-id="7927a-122">使用高级分析检测真实威胁。</span><span class="sxs-lookup"><span data-stu-id="7927a-122">Detect real threats with advanced analytics.</span></span>

- <span data-ttu-id="7927a-123">**备份**。</span><span class="sxs-lookup"><span data-stu-id="7927a-123">**Backup**.</span></span> <span data-ttu-id="7927a-124">使用 [Azure 备份](https://azure.microsoft.com/services/backup/)。</span><span class="sxs-lookup"><span data-stu-id="7927a-124">With [Azure Backup](https://azure.microsoft.com/services/backup/).</span></span>
  - <span data-ttu-id="7927a-125">避免成本高昂的业务中断，满足符合性目标，并保护数据免受勒索软件和人为错误的影响。</span><span class="sxs-lookup"><span data-stu-id="7927a-125">Avoid costly business disruptions, meet compliance goals, and protect your data against ransomware and human errors.</span></span>
  - <span data-ttu-id="7927a-126">保持备份数据在传输和静止时加密。</span><span class="sxs-lookup"><span data-stu-id="7927a-126">Keep your backup data encrypted in transit and at rest.</span></span>
  - <span data-ttu-id="7927a-127">确保基于多因素身份验证的访问，以防止未经授权的使用。</span><span class="sxs-lookup"><span data-stu-id="7927a-127">Ensure access based on multifactor authentication to prevent unauthorized use.</span></span>

- <span data-ttu-id="7927a-128">**本地资源**。</span><span class="sxs-lookup"><span data-stu-id="7927a-128">**On-premises resources**.</span></span> <span data-ttu-id="7927a-129">使用[混合云解决方案](https://azure.microsoft.com/solutions/hybrid-cloud-app/)。</span><span class="sxs-lookup"><span data-stu-id="7927a-129">With [hybrid cloud solutions](https://azure.microsoft.com/solutions/hybrid-cloud-app/).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7927a-130">[上一页](manage-production-docker-environments.md)
>[下一页](../key-takeaways/index.md)</span><span class="sxs-lookup"><span data-stu-id="7927a-130">[Previous](manage-production-docker-environments.md)
[Next](../key-takeaways/index.md)</span></span>

---
title: Azure Monitor
description: 使用 Azure Monitor 来了解系统的运行情况。
ms.date: 07/05/2020
ms.openlocfilehash: 65e17740dba49c3ac3f6e13462897b5342da6710
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91160965"
---
# <a name="azure-monitor"></a><span data-ttu-id="0749e-103">Azure Monitor</span><span class="sxs-lookup"><span data-stu-id="0749e-103">Azure Monitor</span></span>

<span data-ttu-id="0749e-104">除了 Azure 中所发现的云应用程序监视解决方案外，任何其他云提供程序都不会获得太多的成熟。</span><span class="sxs-lookup"><span data-stu-id="0749e-104">No other cloud provider has as mature of a cloud application monitoring solution than that found in Azure.</span></span> <span data-ttu-id="0749e-105">Azure Monitor 是一组用于提供系统状态的工具集合的名称。</span><span class="sxs-lookup"><span data-stu-id="0749e-105">Azure Monitor is an umbrella name for a collection of tools designed to provide visibility into the state of your system.</span></span> <span data-ttu-id="0749e-106">它可帮助你了解云本机服务的执行方式，并主动识别影响它们的问题。</span><span class="sxs-lookup"><span data-stu-id="0749e-106">It helps you understand how your cloud-native services are performing and proactively identifies issues affecting them.</span></span> <span data-ttu-id="0749e-107">图7-12 显示了 Azure Monitor 的高级别视图。</span><span class="sxs-lookup"><span data-stu-id="0749e-107">Figure 7-12 presents a high level of view of Azure Monitor.</span></span>

<span data-ttu-id="0749e-108">![Azure Monitor 的概要视图。 ](./media/azure-monitor.png)
**图 7-12**。</span><span class="sxs-lookup"><span data-stu-id="0749e-108">![High-level view of Azure Monitor.](./media/azure-monitor.png)
**Figure 7-12**.</span></span> <span data-ttu-id="0749e-109">Azure Monitor 的概要视图。</span><span class="sxs-lookup"><span data-stu-id="0749e-109">High-level view of Azure Monitor.</span></span>

## <a name="gathering-logs-and-metrics"></a><span data-ttu-id="0749e-110">收集日志和指标</span><span class="sxs-lookup"><span data-stu-id="0749e-110">Gathering logs and metrics</span></span>

<span data-ttu-id="0749e-111">任何监视解决方案中的第一步是收集尽可能多的数据。</span><span class="sxs-lookup"><span data-stu-id="0749e-111">The first step in any monitoring solution is to gather as much data as possible.</span></span> <span data-ttu-id="0749e-112">收集的数据越多，见解越深入。</span><span class="sxs-lookup"><span data-stu-id="0749e-112">The more data gathered, the deeper the insights.</span></span> <span data-ttu-id="0749e-113">检测系统在传统上非常困难。</span><span class="sxs-lookup"><span data-stu-id="0749e-113">Instrumenting systems has traditionally been difficult.</span></span> <span data-ttu-id="0749e-114">简单网络管理协议 (SNMP) 是用于收集计算机级别信息的黄金标准协议，但它需要大量的知识和配置。</span><span class="sxs-lookup"><span data-stu-id="0749e-114">Simple Network Management Protocol (SNMP) was the gold standard protocol for collecting machine level information, but it required a great deal of knowledge and configuration.</span></span> <span data-ttu-id="0749e-115">幸运的是，很多这样的硬性工作已经消除，因为最常见的指标是 Azure Monitor 自动收集的。</span><span class="sxs-lookup"><span data-stu-id="0749e-115">Fortunately, much of this hard work has been eliminated as the most common metrics are gathered automatically by Azure Monitor.</span></span>

<span data-ttu-id="0749e-116">应用程序级指标和事件无法自动检测，因为它们特定于要部署的应用程序。</span><span class="sxs-lookup"><span data-stu-id="0749e-116">Application level metrics and events aren't possible to instrument automatically because they're specific to the application being deployed.</span></span> <span data-ttu-id="0749e-117">为了收集这些指标，有可直接报告此类信息的 [sdk 和 api](/azure/azure-monitor/app/api-custom-events-metrics) ，例如当客户注册或完成订单。</span><span class="sxs-lookup"><span data-stu-id="0749e-117">In order to gather these metrics, there are [SDKs and APIs available](/azure/azure-monitor/app/api-custom-events-metrics) to directly report such information, such as when a customer signs up or completes an order.</span></span> <span data-ttu-id="0749e-118">还可以通过 Application Insights 捕获异常并将其报告回 Azure Monitor。</span><span class="sxs-lookup"><span data-stu-id="0749e-118">Exceptions can also be captured and reported back into Azure Monitor via Application Insights.</span></span> <span data-ttu-id="0749e-119">Sdk 支持在云本机应用程序（包括中转、Python、JavaScript 和 .NET 语言）中找到的大多数语言。</span><span class="sxs-lookup"><span data-stu-id="0749e-119">The SDKs support most every language found in Cloud Native Applications including Go, Python, JavaScript, and the .NET languages.</span></span>

<span data-ttu-id="0749e-120">收集有关应用程序状态信息的最终目标是确保最终用户具有良好的体验。</span><span class="sxs-lookup"><span data-stu-id="0749e-120">The ultimate goal of gathering information about the state of your application is to ensure that your end users have a good experience.</span></span> <span data-ttu-id="0749e-121">判断用户是否遇到了问题，而不是在进行 [外部 web 测试](/azure/azure-monitor/app/monitor-web-app-availability)的情况？</span><span class="sxs-lookup"><span data-stu-id="0749e-121">What better way to tell if users are experiencing issues than doing [outside-in web tests](/azure/azure-monitor/app/monitor-web-app-availability)?</span></span> <span data-ttu-id="0749e-122">这些测试非常简单，只需从世界各地的位置 ping 你的网站，或使代理登录到站点并模拟用户操作。</span><span class="sxs-lookup"><span data-stu-id="0749e-122">These tests can be as simple as pinging your website from locations around the world or as involved as having agents log into the site and simulate user actions.</span></span>

## <a name="reporting-data"></a><span data-ttu-id="0749e-123">报告数据</span><span class="sxs-lookup"><span data-stu-id="0749e-123">Reporting data</span></span>

<span data-ttu-id="0749e-124">收集数据后，可以对数据进行操作、汇总并将其绘制到图表中，这样用户就可以立即查看出现问题的时间。</span><span class="sxs-lookup"><span data-stu-id="0749e-124">Once the data is gathered, it can be manipulated, summarized, and plotted into charts, which allow users to instantly see when there are problems.</span></span> <span data-ttu-id="0749e-125">可以将这些图表收集到仪表板或工作簿中，这是一个多页面报表，旨在告诉您有关系统的某个方面。</span><span class="sxs-lookup"><span data-stu-id="0749e-125">These charts can be gathered into dashboards or into Workbooks, a multi-page report designed to tell a story about some aspect of the system.</span></span>

<span data-ttu-id="0749e-126">无需一些人工智能或机器学习即可完成新式应用程序。</span><span class="sxs-lookup"><span data-stu-id="0749e-126">No modern application would be complete without some artificial intelligence or machine learning.</span></span> <span data-ttu-id="0749e-127">为此， [可以将数据传递](https://www.youtube.com/watch?v=Cuza-I1g9tw) 到 Azure 中的各种机器学习工具，以便您可以提取其他隐藏的趋势和信息。</span><span class="sxs-lookup"><span data-stu-id="0749e-127">To this end, data [can be passed](https://www.youtube.com/watch?v=Cuza-I1g9tw) to the various machine learning tools in Azure to allow you to extract trends and information that would otherwise be hidden.</span></span>

<span data-ttu-id="0749e-128">Application Insights 提供了一种 (功能强大的类似 SQL 的) 查询语言（称为 *Kusto* ），它可以查询记录、汇总记录，甚至绘制图表。</span><span class="sxs-lookup"><span data-stu-id="0749e-128">Application Insights provides a powerful (SQL-like) query language called *Kusto* that can query records, summarize them, and even plot charts.</span></span> <span data-ttu-id="0749e-129">例如，以下查询将查找2007年11月的所有记录，按州分组，并将前10个为饼图。</span><span class="sxs-lookup"><span data-stu-id="0749e-129">For example, the following query will locate all records for the month of November 2007, group them by state, and plot the top 10 as a pie chart.</span></span>

```kusto
StormEvents
| where StartTime >= datetime(2007-11-01) and StartTime < datetime(2007-12-01)
| summarize count() by State
| top 10 by count_
| render piechart
```

<span data-ttu-id="0749e-130">图7-13 显示了此 Application Insights 查询的结果。</span><span class="sxs-lookup"><span data-stu-id="0749e-130">Figure 7-13 shows the results of this Application Insights Query.</span></span>

<span data-ttu-id="0749e-131">![Application Insights 查询结果 ](./media/application_insights_example.png)
 **图 7-13**。</span><span class="sxs-lookup"><span data-stu-id="0749e-131">![Application Insights query results](./media/application_insights_example.png)
**Figure 7-13**.</span></span> <span data-ttu-id="0749e-132">Application Insights 查询结果。</span><span class="sxs-lookup"><span data-stu-id="0749e-132">Application Insights query results.</span></span>

<span data-ttu-id="0749e-133">[使用 Kusto](https://dataexplorer.azure.com/clusters/help/databases/Samples)查询有一个板块。</span><span class="sxs-lookup"><span data-stu-id="0749e-133">There is a [playground for experimenting with Kusto](https://dataexplorer.azure.com/clusters/help/databases/Samples) queries.</span></span> <span data-ttu-id="0749e-134">读取 [示例查询](/azure/kusto/query/samples) 也可以指导。</span><span class="sxs-lookup"><span data-stu-id="0749e-134">Reading [sample queries](/azure/kusto/query/samples) can also be instructive.</span></span>

## <a name="dashboards"></a><span data-ttu-id="0749e-135">仪表板</span><span class="sxs-lookup"><span data-stu-id="0749e-135">Dashboards</span></span>

<span data-ttu-id="0749e-136">有多种不同的仪表板技术可用于从 Azure Monitor 显示信息。</span><span class="sxs-lookup"><span data-stu-id="0749e-136">There are several different dashboard technologies that may be used to surface the information from Azure Monitor.</span></span> <span data-ttu-id="0749e-137">最简单的情况是，只需在 Application Insights 中运行查询，然后将 [数据绘制到图表](/azure/azure-monitor/learn/tutorial-app-dashboards)中。</span><span class="sxs-lookup"><span data-stu-id="0749e-137">Perhaps the simplest is to just run queries in Application Insights and [plot the data into a chart](/azure/azure-monitor/learn/tutorial-app-dashboards).</span></span>

<span data-ttu-id="0749e-138">![在 Azure 主仪表板 ](./media/azure_dashboard.png)
 **图 7-14**中嵌入 Application Insights 图表的示例。</span><span class="sxs-lookup"><span data-stu-id="0749e-138">![An example of Application Insights charts embedded in the main Azure Dashboard](./media/azure_dashboard.png)
**Figure 7-14**.</span></span> <span data-ttu-id="0749e-139">在 Azure 主仪表板中嵌入 Application Insights 图表的示例。</span><span class="sxs-lookup"><span data-stu-id="0749e-139">An example of Application Insights charts embedded in the main Azure Dashboard.</span></span>

<span data-ttu-id="0749e-140">然后，可以通过使用 "仪表板" 功能，将这些图表嵌入到 Azure 门户中。</span><span class="sxs-lookup"><span data-stu-id="0749e-140">These charts can then be embedded in the Azure portal proper through use of the dashboard feature.</span></span> <span data-ttu-id="0749e-141">对于具有更严格要求的用户（例如，能够向下钻取多个数据层），可以 [Power BI](https://powerbi.microsoft.com/)Azure Monitor 数据。</span><span class="sxs-lookup"><span data-stu-id="0749e-141">For users with more exacting requirements, such as being able to drill down into several tiers of data, Azure Monitor data is available to [Power BI](https://powerbi.microsoft.com/).</span></span> <span data-ttu-id="0749e-142">Power BI 是行业领先的企业级商业智能工具，可从多个不同的数据源聚合数据。</span><span class="sxs-lookup"><span data-stu-id="0749e-142">Power BI is an industry-leading, enterprise class, business intelligence tool that can aggregate data from many different data sources.</span></span>

![Power BI 仪表板的示例](./media/powerbidashboard.png)

<span data-ttu-id="0749e-144">**图 7-15**。</span><span class="sxs-lookup"><span data-stu-id="0749e-144">**Figure 7-15**.</span></span> <span data-ttu-id="0749e-145">Power BI 仪表板的示例。</span><span class="sxs-lookup"><span data-stu-id="0749e-145">An example Power BI dashboard.</span></span>

## <a name="alerts"></a><span data-ttu-id="0749e-146">警报</span><span class="sxs-lookup"><span data-stu-id="0749e-146">Alerts</span></span>

<span data-ttu-id="0749e-147">有时，数据仪表板不足。</span><span class="sxs-lookup"><span data-stu-id="0749e-147">Sometimes, having data dashboards is insufficient.</span></span> <span data-ttu-id="0749e-148">如果没有人唤醒监视仪表板，则在解决问题之前，甚至会检测到问题。</span><span class="sxs-lookup"><span data-stu-id="0749e-148">If nobody is awake to watch the dashboards, then it can still be many hours before a problem is addressed, or even detected.</span></span> <span data-ttu-id="0749e-149">为此，Azure Monitor 还提供了一个顶部凹槽 [警报解决方案](/azure/azure-monitor/platform/alerts-overview)。</span><span class="sxs-lookup"><span data-stu-id="0749e-149">To this end, Azure Monitor also provides a top notch [alerting solution](/azure/azure-monitor/platform/alerts-overview).</span></span> <span data-ttu-id="0749e-150">可以通过各种条件触发警报，包括：</span><span class="sxs-lookup"><span data-stu-id="0749e-150">Alerts can be triggered by a wide range of conditions including:</span></span>

- <span data-ttu-id="0749e-151">指标值</span><span class="sxs-lookup"><span data-stu-id="0749e-151">Metric values</span></span>
- <span data-ttu-id="0749e-152">日志搜索查询</span><span class="sxs-lookup"><span data-stu-id="0749e-152">Log search queries</span></span>
- <span data-ttu-id="0749e-153">活动日志事件</span><span class="sxs-lookup"><span data-stu-id="0749e-153">Activity Log events</span></span>
- <span data-ttu-id="0749e-154">基础 Azure 平台的运行状况</span><span class="sxs-lookup"><span data-stu-id="0749e-154">Health of the underlying Azure platform</span></span>
- <span data-ttu-id="0749e-155">网址可用性测试</span><span class="sxs-lookup"><span data-stu-id="0749e-155">Tests for web site availability</span></span>

<span data-ttu-id="0749e-156">触发警报时，警报可执行各种任务。</span><span class="sxs-lookup"><span data-stu-id="0749e-156">When triggered, the alerts can perform a wide variety of tasks.</span></span> <span data-ttu-id="0749e-157">在简单端，警报可能只是向个人发送电子邮件通知或发送到个人的短信。</span><span class="sxs-lookup"><span data-stu-id="0749e-157">On the simple side, the alerts may just send an e-mail notification to a mailing list or a text message to an individual.</span></span> <span data-ttu-id="0749e-158">更多涉及的警报可能会在工具（如 PagerDuty）中触发工作流，该工具可感知特定应用程序的调用者。</span><span class="sxs-lookup"><span data-stu-id="0749e-158">More involved alerts might trigger a workflow in a tool such as PagerDuty, which is aware of who is on call for a particular application.</span></span> <span data-ttu-id="0749e-159">警报可以触发 [Microsoft Flow](https://flow.microsoft.com/) 的操作，以接近无限制工作流的方式。</span><span class="sxs-lookup"><span data-stu-id="0749e-159">Alerts can trigger actions in [Microsoft Flow](https://flow.microsoft.com/) unlocking near limitless possibilities for workflows.</span></span>

<span data-ttu-id="0749e-160">当发现警报的常见原因时，可以使用警报的常见原因和解决方法的步骤来增强警报。</span><span class="sxs-lookup"><span data-stu-id="0749e-160">As common causes of alerts are identified, the alerts can be enhanced with details about the common causes of the alerts and the steps to take to resolve them.</span></span> <span data-ttu-id="0749e-161">高度成熟的云本机应用程序部署可以选择启动自愈任务，这些任务可执行一些操作，例如从规模集中删除失败节点或触发自动缩放活动。</span><span class="sxs-lookup"><span data-stu-id="0749e-161">Highly mature cloud-native application deployments may opt to kick off self-healing tasks, which perform actions such as removing failing nodes from a scale set or triggering an autoscaling activity.</span></span> <span data-ttu-id="0749e-162">最终，可能不再需要唤醒2AM 上的待命人员来解决实时站点问题，因为系统将能够自行调整以进行补偿或至少 limp，直到在某个时间早上进入工作为止。</span><span class="sxs-lookup"><span data-stu-id="0749e-162">Eventually it may no longer be necessary to wake up on-call personnel at 2AM to resolve a live-site issue as the system will be able to adjust itself to compensate or at least limp along until somebody arrives at work the next morning.</span></span>

<span data-ttu-id="0749e-163">Azure Monitor 会自动利用机器学习来了解部署的应用程序的正常运行参数。</span><span class="sxs-lookup"><span data-stu-id="0749e-163">Azure Monitor automatically leverages machine learning to understand the normal operating parameters of deployed applications.</span></span> <span data-ttu-id="0749e-164">这使它能够检测到其正常参数外操作的服务。</span><span class="sxs-lookup"><span data-stu-id="0749e-164">This enables it to detect services that are operating outside of their normal parameters.</span></span> <span data-ttu-id="0749e-165">例如，站点上典型的工作日流量可能是每分钟10000请求。</span><span class="sxs-lookup"><span data-stu-id="0749e-165">For instance, the typical weekday traffic on the site might be 10,000 requests per minute.</span></span> <span data-ttu-id="0749e-166">然后，在给定的一周突然，每分钟遇到的请求数非常罕见的20000请求。</span><span class="sxs-lookup"><span data-stu-id="0749e-166">And then, on a given week, suddenly the number of requests hits a highly unusual 20,000 requests per minute.</span></span> <span data-ttu-id="0749e-167">[智能检测](/azure/azure-monitor/app/proactive-diagnostics) 会注意到与标准的偏差，并触发警报。</span><span class="sxs-lookup"><span data-stu-id="0749e-167">[Smart Detection](/azure/azure-monitor/app/proactive-diagnostics) will notice this deviation from the norm and trigger an alert.</span></span> <span data-ttu-id="0749e-168">同时，趋势分析非常智能，可避免在预计流量负载时触发误报。</span><span class="sxs-lookup"><span data-stu-id="0749e-168">At the same time, the trend analysis is smart enough to avoid firing false positives when the traffic load is expected.</span></span>

## <a name="references"></a><span data-ttu-id="0749e-169">参考</span><span class="sxs-lookup"><span data-stu-id="0749e-169">References</span></span>

- [<span data-ttu-id="0749e-170">Azure Monitor</span><span class="sxs-lookup"><span data-stu-id="0749e-170">Azure Monitor</span></span>](/azure/azure-monitor/overview)

>[!div class="step-by-step"]
><span data-ttu-id="0749e-171">[上一页](monitoring-azure-kubernetes.md)
>[下一页](identity.md)</span><span class="sxs-lookup"><span data-stu-id="0749e-171">[Previous](monitoring-azure-kubernetes.md)
[Next](identity.md)</span></span>

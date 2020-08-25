---
title: 使用弹性堆栈进行日志记录
description: 使用弹性堆栈、Logstash 和 Kibana 进行日志记录
ms.date: 05/13/2020
ms.openlocfilehash: 32d9d0dae175d8d45d48b56d17f133b4cc432363
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811166"
---
# <a name="logging-with-elastic-stack"></a><span data-ttu-id="cdd43-103">使用弹性堆栈进行日志记录</span><span class="sxs-lookup"><span data-stu-id="cdd43-103">Logging with Elastic Stack</span></span>

<span data-ttu-id="cdd43-104">有很多非常好的集中式日志记录工具，从免费的开源工具到成本较高的选项，这些工具的成本会有所不同。</span><span class="sxs-lookup"><span data-stu-id="cdd43-104">There are many good centralized logging tools and they vary in cost from being free, open-source tools, to more expensive options.</span></span> <span data-ttu-id="cdd43-105">在许多情况下，免费的工具与付费的产品/服务非常好。</span><span class="sxs-lookup"><span data-stu-id="cdd43-105">In many cases, the free tools are as good as or better than the paid offerings.</span></span> <span data-ttu-id="cdd43-106">一个此类工具是三个开源组件的组合：弹性搜索、Logstash 和 Kibana。</span><span class="sxs-lookup"><span data-stu-id="cdd43-106">One such tool is a combination of three open-source components: Elastic search, Logstash, and Kibana.</span></span>

<span data-ttu-id="cdd43-107">这些工具共同称为弹性堆栈或 ELK 堆栈。</span><span class="sxs-lookup"><span data-stu-id="cdd43-107">Collectively these tools are known as the Elastic Stack or ELK stack.</span></span>

## <a name="elastic-stack"></a><span data-ttu-id="cdd43-108">弹性堆栈</span><span class="sxs-lookup"><span data-stu-id="cdd43-108">Elastic Stack</span></span>

<span data-ttu-id="cdd43-109">弹性堆栈是一个功能强大的选项，可用于从 Kubernetes 群集中收集信息。</span><span class="sxs-lookup"><span data-stu-id="cdd43-109">The Elastic Stack is a powerful option for gathering information from a Kubernetes cluster.</span></span> <span data-ttu-id="cdd43-110">Kubernetes 支持将日志发送到 Elasticsearch 终结点，而在 [大多数情况](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/)下，你只需设置环境变量，如图7-5 所示：</span><span class="sxs-lookup"><span data-stu-id="cdd43-110">Kubernetes supports sending logs to an Elasticsearch endpoint, and for the [most part](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/), all you need to get started is to set the environment variables as shown in Figure 7-5:</span></span>

```kubernetes
KUBE_LOGGING_DESTINATION=elasticsearch
KUBE_ENABLE_NODE_LOGGING=true
```

<span data-ttu-id="cdd43-111">**图 7-5**。</span><span class="sxs-lookup"><span data-stu-id="cdd43-111">**Figure 7-5**.</span></span> <span data-ttu-id="cdd43-112">Kubernetes 的配置变量</span><span class="sxs-lookup"><span data-stu-id="cdd43-112">Configuration variables for Kubernetes</span></span>

<span data-ttu-id="cdd43-113">这会在群集上安装 Elasticsearch，并将所有群集日志发送到该群集。</span><span class="sxs-lookup"><span data-stu-id="cdd43-113">This will install Elasticsearch on the cluster and target sending all the cluster logs to it.</span></span>

<span data-ttu-id="cdd43-114">![Kibana 仪表板的一个示例，显示针对 Kubernetes ](./media/kibana-dashboard.png)
 **图 7-6**中的日志引入的查询结果。</span><span class="sxs-lookup"><span data-stu-id="cdd43-114">![An example of a Kibana dashboard showing the results of a query against logs ingested from Kubernetes](./media/kibana-dashboard.png)
**Figure 7-6**.</span></span> <span data-ttu-id="cdd43-115">Kibana 仪表板的一个示例，显示针对引入 from Kubernetes 中的日志查询的结果</span><span class="sxs-lookup"><span data-stu-id="cdd43-115">An example of a Kibana dashboard showing the results of a query against logs that are ingested from Kubernetes</span></span>

## <a name="what-are-the-advantages-of-elastic-stack"></a><span data-ttu-id="cdd43-116">弹性堆栈的优点是什么？</span><span class="sxs-lookup"><span data-stu-id="cdd43-116">What are the advantages of Elastic Stack?</span></span>

<span data-ttu-id="cdd43-117">弹性堆栈以低成本、可缩放且可缩放的云形式提供集中式日志记录。</span><span class="sxs-lookup"><span data-stu-id="cdd43-117">Elastic Stack provides centralized logging in a low-cost, scalable, cloud-friendly manner.</span></span> <span data-ttu-id="cdd43-118">它的用户界面可简化数据分析，使你可以从数据中发现见解，而无需使用笨接口。</span><span class="sxs-lookup"><span data-stu-id="cdd43-118">Its user interface streamlines data analysis so you can spend your time gleaning insights from your data instead of fighting with a clunky interface.</span></span> <span data-ttu-id="cdd43-119">它支持各种输入，因此，当你的分布式应用程序跨越更多和不同类型的服务时，你可以继续将日志和指标数据馈送到系统中。</span><span class="sxs-lookup"><span data-stu-id="cdd43-119">It supports a wide variety of inputs so as your distributed application spans more and different kinds of services, you can expect to continue to be able to feed log and metric data into the system.</span></span> <span data-ttu-id="cdd43-120">弹性堆栈还支持快速搜索（甚至跨大型数据集），这样，即使大型应用程序也可以记录详细数据，并且仍能以高性能的方式对其进行查看。</span><span class="sxs-lookup"><span data-stu-id="cdd43-120">The Elastic Stack also supports fast searches even across large data sets, making it possible even for large applications to log detailed data and still be able to have visibility into it in a performant fashion.</span></span>

## <a name="logstash"></a><span data-ttu-id="cdd43-121">Logstash</span><span class="sxs-lookup"><span data-stu-id="cdd43-121">Logstash</span></span>

<span data-ttu-id="cdd43-122">第一个组件为 [Logstash](https://www.elastic.co/products/logstash)。</span><span class="sxs-lookup"><span data-stu-id="cdd43-122">The first component is [Logstash](https://www.elastic.co/products/logstash).</span></span> <span data-ttu-id="cdd43-123">此工具用于从大量不同的源收集日志信息。</span><span class="sxs-lookup"><span data-stu-id="cdd43-123">This tool is used to gather log information from a large variety of different sources.</span></span> <span data-ttu-id="cdd43-124">例如，Logstash 可以从磁盘读取日志，还可以从日志记录库（如 [Serilog](https://serilog.net/)）接收消息。</span><span class="sxs-lookup"><span data-stu-id="cdd43-124">For instance, Logstash can read logs from disk and also receive messages from logging libraries like [Serilog](https://serilog.net/).</span></span> <span data-ttu-id="cdd43-125">Logstash 可以在日志到达时对其执行一些基本筛选和扩展。</span><span class="sxs-lookup"><span data-stu-id="cdd43-125">Logstash can do some basic filtering and expansion on the logs as they arrive.</span></span> <span data-ttu-id="cdd43-126">例如，如果日志包含 IP 地址，则可以将 Logstash 配置为执行地理查找，并获取该邮件的国家/地区或甚至是源城市。</span><span class="sxs-lookup"><span data-stu-id="cdd43-126">For instance, if your logs contain IP addresses then Logstash may be configured to do a geographical lookup and obtain a country or even city of origin for that message.</span></span>

<span data-ttu-id="cdd43-127">Serilog 是用于 .NET 语言的日志记录库，用于实现参数化日志记录。</span><span class="sxs-lookup"><span data-stu-id="cdd43-127">Serilog is a logging library for .NET languages, which allows for parameterized logging.</span></span> <span data-ttu-id="cdd43-128">参数不会生成嵌入字段的文本日志消息，而是将参数保持独立。</span><span class="sxs-lookup"><span data-stu-id="cdd43-128">Instead of generating a textual log message that embeds fields, parameters are kept separate.</span></span> <span data-ttu-id="cdd43-129">这允许更智能的筛选和搜索。</span><span class="sxs-lookup"><span data-stu-id="cdd43-129">This allows for more intelligent filtering and searching.</span></span> <span data-ttu-id="cdd43-130">图7-7 显示了用于写入 Logstash 的示例 Serilog 配置。</span><span class="sxs-lookup"><span data-stu-id="cdd43-130">A sample Serilog configuration for writing to Logstash appears in Figure 7-7.</span></span>

```csharp
var log = new LoggerConfiguration()
         .WriteTo.Http("http://localhost:8080")
         .CreateLogger();
```

<span data-ttu-id="cdd43-131">**图 7-7**。</span><span class="sxs-lookup"><span data-stu-id="cdd43-131">**Figure 7-7**.</span></span> <span data-ttu-id="cdd43-132">用于将日志信息直接写入 logstash over HTTP 的 Serilog config</span><span class="sxs-lookup"><span data-stu-id="cdd43-132">Serilog config for writing log information directly to logstash over HTTP</span></span>

<span data-ttu-id="cdd43-133">Logstash 将使用如图7-8 中所示的配置。</span><span class="sxs-lookup"><span data-stu-id="cdd43-133">Logstash would use a configuration like the one shown in Figure 7-8.</span></span>

```
input {
    http {
        #default host 0.0.0.0:8080
        codec => json
    }
}

output {
    elasticsearch {
        hosts => "elasticsearch:9200"
        index=>"sales-%{+xxxx.ww}"
    }
}
```

<span data-ttu-id="cdd43-134">**图 7-8**。</span><span class="sxs-lookup"><span data-stu-id="cdd43-134">**Figure 7-8**.</span></span> <span data-ttu-id="cdd43-135">使用 Serilog 中的日志的 Logstash 配置</span><span class="sxs-lookup"><span data-stu-id="cdd43-135">A Logstash configuration for consuming logs from Serilog</span></span>

<span data-ttu-id="cdd43-136">对于不需要进行大量的日志操作的情况，有一种替代方法 Logstash 称为 [节拍](https://www.elastic.co/products/beats)。</span><span class="sxs-lookup"><span data-stu-id="cdd43-136">For scenarios where extensive log manipulation isn't needed there's an alternative to Logstash known as [Beats](https://www.elastic.co/products/beats).</span></span> <span data-ttu-id="cdd43-137">节拍是一系列工具，可以将各种数据从日志收集到网络数据和正常运行时间信息。</span><span class="sxs-lookup"><span data-stu-id="cdd43-137">Beats is a family of tools that can gather a wide variety of data from logs to network data and uptime information.</span></span> <span data-ttu-id="cdd43-138">许多应用程序将同时使用 Logstash 和节拍。</span><span class="sxs-lookup"><span data-stu-id="cdd43-138">Many applications will use both Logstash and Beats.</span></span>

<span data-ttu-id="cdd43-139">Logstash 收集了日志后，需要将其放在某个位置。</span><span class="sxs-lookup"><span data-stu-id="cdd43-139">Once the logs have been gathered by Logstash, it needs somewhere to put them.</span></span> <span data-ttu-id="cdd43-140">尽管 Logstash 支持多个不同的输出，但其中一个比较激动人心的输出是弹性搜索。</span><span class="sxs-lookup"><span data-stu-id="cdd43-140">While Logstash supports many different outputs, one of the more exciting ones is Elastic search.</span></span>

## <a name="elastic-search"></a><span data-ttu-id="cdd43-141">弹性搜索</span><span class="sxs-lookup"><span data-stu-id="cdd43-141">Elastic search</span></span>

<span data-ttu-id="cdd43-142">弹性搜索是一个功能强大的搜索引擎，可以在日志到达时对其进行索引。</span><span class="sxs-lookup"><span data-stu-id="cdd43-142">Elastic search is a powerful search engine that can index logs as they arrive.</span></span> <span data-ttu-id="cdd43-143">它对日志快速运行查询。</span><span class="sxs-lookup"><span data-stu-id="cdd43-143">It makes running queries against the logs quick.</span></span> <span data-ttu-id="cdd43-144">弹性搜索可以处理大量日志，在极大情况下，可以在多个节点之间横向扩展。</span><span class="sxs-lookup"><span data-stu-id="cdd43-144">Elastic search can handle huge quantities of logs and, in extreme cases, can be scaled out across many nodes.</span></span>

<span data-ttu-id="cdd43-145">精心设计为包含参数或通过 Logstash 处理将参数拆分为包含参数的日志消息可以直接查询，因为 Elasticsearch 会保留此信息。</span><span class="sxs-lookup"><span data-stu-id="cdd43-145">Log messages that have been crafted to contain parameters or that have had parameters split from them through Logstash processing, can be queried directly as Elasticsearch preserves this information.</span></span>

<span data-ttu-id="cdd43-146">`jill@example.com`在图7-9 中将会搜索访问的前10页的查询。</span><span class="sxs-lookup"><span data-stu-id="cdd43-146">A query that searches for the top 10 pages visited by `jill@example.com`, appears in Figure 7-9.</span></span>

```json
"query": {
    "match": {
      "user": "jill@example.com"
    }
  },
  "aggregations": {
    "top_10_pages": {
      "terms": {
        "field": "page",
        "size": 10
      }
    }
  }
```

<span data-ttu-id="cdd43-147">**图 7-9**。</span><span class="sxs-lookup"><span data-stu-id="cdd43-147">**Figure 7-9**.</span></span> <span data-ttu-id="cdd43-148">用于查找用户访问的前10页的 Elasticsearch 查询</span><span class="sxs-lookup"><span data-stu-id="cdd43-148">An Elasticsearch query for finding top 10 pages visited by a user</span></span>

## <a name="visualizing-information-with-kibana-web-dashboards"></a><span data-ttu-id="cdd43-149">通过 Kibana web 仪表板可视化信息</span><span class="sxs-lookup"><span data-stu-id="cdd43-149">Visualizing information with Kibana web dashboards</span></span>

<span data-ttu-id="cdd43-150">堆栈的最终组件为 Kibana。</span><span class="sxs-lookup"><span data-stu-id="cdd43-150">The final component of the stack is Kibana.</span></span> <span data-ttu-id="cdd43-151">此工具用于在 web 仪表板中提供交互式可视化对象。</span><span class="sxs-lookup"><span data-stu-id="cdd43-151">This tool is used to provide interactive visualizations in a web dashboard.</span></span> <span data-ttu-id="cdd43-152">即使是非技术用户，也可以进行精心设计的仪表板。</span><span class="sxs-lookup"><span data-stu-id="cdd43-152">Dashboards may be crafted even by users who are non-technical.</span></span> <span data-ttu-id="cdd43-153">驻留在 Elasticsearch 索引中的大部分数据都可以包含在 Kibana 仪表板中。</span><span class="sxs-lookup"><span data-stu-id="cdd43-153">Most data that is resident in the Elasticsearch index, can be included in the Kibana dashboards.</span></span> <span data-ttu-id="cdd43-154">单个用户的仪表板可能不同，Kibana 通过允许用户特定的仪表板启用此自定义。</span><span class="sxs-lookup"><span data-stu-id="cdd43-154">Individual users may have different dashboard desires and Kibana enables this customization through allowing user-specific dashboards.</span></span>

## <a name="installing-elastic-stack-on-azure"></a><span data-ttu-id="cdd43-155">在 Azure 上安装弹性堆栈</span><span class="sxs-lookup"><span data-stu-id="cdd43-155">Installing Elastic Stack on Azure</span></span>

<span data-ttu-id="cdd43-156">可以通过多种方式在 Azure 上安装弹性堆栈。</span><span class="sxs-lookup"><span data-stu-id="cdd43-156">The Elastic stack can be installed on Azure in a number of ways.</span></span> <span data-ttu-id="cdd43-157">与往常一样，可以 [预配虚拟机并直接在其上安装弹性堆栈](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch)。</span><span class="sxs-lookup"><span data-stu-id="cdd43-157">As always, it's possible to [provision virtual machines and install Elastic Stack on them directly](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch).</span></span> <span data-ttu-id="cdd43-158">此选项由一些经验丰富的用户首选，因为它提供了最高的可定制性。</span><span class="sxs-lookup"><span data-stu-id="cdd43-158">This option is preferred by some experienced users as it offers the highest degree of customizability.</span></span> <span data-ttu-id="cdd43-159">在基础结构上部署为服务会带来巨大的管理开销，迫使那些采用该路径的用户获得与基础结构相关的所有任务的所有权（例如，保护计算机并随时保持修补程序的最新）。</span><span class="sxs-lookup"><span data-stu-id="cdd43-159">Deploying on infrastructure as a service introduces significant management overhead forcing those who take that path to take ownership of all the tasks associated with infrastructure as a service such as securing the machines and keeping up-to-date with patches.</span></span>

<span data-ttu-id="cdd43-160">开销较少的选项是使用已在其上配置弹性堆栈的众多 Docker 容器之一。</span><span class="sxs-lookup"><span data-stu-id="cdd43-160">An option with less overhead is to make use of one of the many Docker containers on which the Elastic Stack has already been configured.</span></span> <span data-ttu-id="cdd43-161">这些容器可以放入现有的 Kubernetes 群集，并与应用程序代码一起运行。</span><span class="sxs-lookup"><span data-stu-id="cdd43-161">These containers can be dropped into an existing Kubernetes cluster and run alongside application code.</span></span> <span data-ttu-id="cdd43-162">[Sebp/elk](https://elk-docker.readthedocs.io/)容器是一种记录完善且经过测试的弹性堆栈容器。</span><span class="sxs-lookup"><span data-stu-id="cdd43-162">The [sebp/elk](https://elk-docker.readthedocs.io/) container is a well-documented and tested Elastic Stack container.</span></span>

<span data-ttu-id="cdd43-163">另一种方法是 [最近发布的 ELK 产品/服务](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/)。</span><span class="sxs-lookup"><span data-stu-id="cdd43-163">Another option is a [recently announced ELK-as-a-service offering](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/).</span></span>

## <a name="references"></a><span data-ttu-id="cdd43-164">引用</span><span class="sxs-lookup"><span data-stu-id="cdd43-164">References</span></span>

- [<span data-ttu-id="cdd43-165">在 Azure 上安装弹性堆栈</span><span class="sxs-lookup"><span data-stu-id="cdd43-165">Install Elastic Stack on Azure</span></span>](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch)

>[!div class="step-by-step"]
><span data-ttu-id="cdd43-166">[上一页](observability-patterns.md)
>[下一页](monitoring-azure-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="cdd43-166">[Previous](observability-patterns.md)
[Next](monitoring-azure-kubernetes.md)</span></span>

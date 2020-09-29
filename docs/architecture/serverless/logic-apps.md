---
title: Azure 逻辑应用 - 无服务器应用
description: 使用 Azure 逻辑应用可以生成可缩放的自动化工作流，以便跨云服务和本地系统集成应用和数据。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 11fdf5b5f176eb0d66eee6dde7638d3eae1e1f55
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171840"
---
# <a name="azure-logic-apps"></a><span data-ttu-id="02d6b-103">Azure 逻辑应用</span><span class="sxs-lookup"><span data-stu-id="02d6b-103">Azure Logic Apps</span></span>

<span data-ttu-id="02d6b-104">[Azure 逻辑应用](/azure/logic-apps)提供无服务器引擎来生成自动化工作流，以便在云服务和本地系统之间集成应用和数据。</span><span class="sxs-lookup"><span data-stu-id="02d6b-104">[Azure Logic Apps](/azure/logic-apps) provides a serverless engine to build automated workflows to integrate apps and data between cloud services and on-premises systems.</span></span> <span data-ttu-id="02d6b-105">使用可视化设计器生成工作流。</span><span class="sxs-lookup"><span data-stu-id="02d6b-105">You build workflows using a visual designer.</span></span> <span data-ttu-id="02d6b-106">可以基于事件或计时器触发工作流，并利用连接器来集成应用程序和促进企业到企业 (B2B) 通信。</span><span class="sxs-lookup"><span data-stu-id="02d6b-106">You can trigger workflows based on events or timers and leverage connectors to integration applications and facilitate business-to-business (B2B) communication.</span></span> <span data-ttu-id="02d6b-107">逻辑应用与 Azure Functions 无缝集成。</span><span class="sxs-lookup"><span data-stu-id="02d6b-107">Logic Apps integrates seamlessly with Azure Functions.</span></span>

![Azure 逻辑应用徽标](./media/logic-apps-logo.png)

<span data-ttu-id="02d6b-109">逻辑应用不仅可以将云服务（如 Functions）与云资源（如队列和数据库）连接。</span><span class="sxs-lookup"><span data-stu-id="02d6b-109">Logic Apps can do more than just connect your cloud services (like functions) with cloud resources (like queues and databases).</span></span> <span data-ttu-id="02d6b-110">还可以通过本地网关协调本地工作流。</span><span class="sxs-lookup"><span data-stu-id="02d6b-110">You can also orchestrate on-premises workflows with the on-premises gateway.</span></span> <span data-ttu-id="02d6b-111">例如，可以使用逻辑应用触发本地 SQL 存储过程，以便响应工作流中基于云的事件或条件逻辑。</span><span class="sxs-lookup"><span data-stu-id="02d6b-111">For example, you can use the Logic App to trigger an on-premises SQL stored procedure in response to a cloud-based event or conditional logic in your workflow.</span></span> <span data-ttu-id="02d6b-112">详细了解[使用 Azure 本地数据网关连接到本地数据源](/azure/analysis-services/analysis-services-gateway)。</span><span class="sxs-lookup"><span data-stu-id="02d6b-112">Learn more about [Connecting to on-premises data sources with Azure On-premises Data Gateway](/azure/analysis-services/analysis-services-gateway).</span></span>

![逻辑应用体系结构](./media/logic-apps-architecture.png)

<span data-ttu-id="02d6b-114">与 Azure Functions 一样，可以使用触发器启动逻辑应用工作流。</span><span class="sxs-lookup"><span data-stu-id="02d6b-114">Like Azure Functions, you kick off Logic App workflows with a trigger.</span></span> <span data-ttu-id="02d6b-115">有很多触发器可供选择。</span><span class="sxs-lookup"><span data-stu-id="02d6b-115">There are many triggers for you to choose from.</span></span> <span data-ttu-id="02d6b-116">以下截图仅显示数百个可用触发器中较常用的几个触发器。</span><span class="sxs-lookup"><span data-stu-id="02d6b-116">The following capture shows just a few of the more popular ones out of hundreds that are available.</span></span>

![逻辑应用触发器](./media/logic-app-triggers.png)

<span data-ttu-id="02d6b-118">触发应用后，可以使用可视化设计器来构建步骤、循环、条件和操作。</span><span class="sxs-lookup"><span data-stu-id="02d6b-118">Once the app is triggered, you can use the visual designer to build out steps, loops, conditions, and actions.</span></span> <span data-ttu-id="02d6b-119">可以在后续步骤中使用上一步中引入的任何数据。</span><span class="sxs-lookup"><span data-stu-id="02d6b-119">Any data ingested in a previous step is available for you to use in subsequent steps.</span></span> <span data-ttu-id="02d6b-120">以下工作流从 CosmosDB 数据库加载 URL。</span><span class="sxs-lookup"><span data-stu-id="02d6b-120">The following workflow loads URLs from a CosmosDB database.</span></span> <span data-ttu-id="02d6b-121">将查找具有主机 `t.co` 的 URL，然后在 Twitter 上搜索它们。</span><span class="sxs-lookup"><span data-stu-id="02d6b-121">It finds the ones with a host of `t.co` then searches for them on Twitter.</span></span> <span data-ttu-id="02d6b-122">如果找到相应的推文，将通过调用函数来更新具有相关推文的文档。</span><span class="sxs-lookup"><span data-stu-id="02d6b-122">If it finds corresponding tweets, it updates the documents with the related tweets by calling a function.</span></span>

![逻辑应用工作流](./media/logic-app-workflow.png)

<span data-ttu-id="02d6b-124">逻辑应用仪表板显示运行工作流的历史记录，以及每次运行是否已成功完成。</span><span class="sxs-lookup"><span data-stu-id="02d6b-124">The Logic Apps dashboard shows the history of running your workflows and whether each run completed successfully or not.</span></span> <span data-ttu-id="02d6b-125">可以导航到任何给定运行，并检查每个步骤使用的数据以进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="02d6b-125">You can navigate into any given run and inspect the data used by each step for troubleshooting.</span></span> <span data-ttu-id="02d6b-126">逻辑应用还提供了可编辑且非常适合于复杂企业工作流的现有模板。</span><span class="sxs-lookup"><span data-stu-id="02d6b-126">Logic Apps also provides existing templates you can edit and are well suited for complex enterprise workflows.</span></span>

<span data-ttu-id="02d6b-127">若要了解详细信息，请参阅 [Azure 逻辑应用](/azure/logic-apps)。</span><span class="sxs-lookup"><span data-stu-id="02d6b-127">To learn more, see [Azure Logic Apps](/azure/logic-apps).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="02d6b-128">[上一页](application-insights.md)
>[下一页](event-grid.md)</span><span class="sxs-lookup"><span data-stu-id="02d6b-128">[Previous](application-insights.md)
[Next](event-grid.md)</span></span>

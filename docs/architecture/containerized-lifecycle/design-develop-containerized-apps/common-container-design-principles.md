---
title: 常见容器设计原则
description: 了解良好容器设计的基本原则，即容器应只承载一个进程。
ms.date: 08/06/2020
ms.openlocfilehash: 7dcf4b4af3385a2a500c5bc16a889b56fa2c25d5
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916000"
---
# <a name="common-container-design-principles"></a><span data-ttu-id="9abec-103">常见容器设计原则</span><span class="sxs-lookup"><span data-stu-id="9abec-103">Common container design principles</span></span>

<span data-ttu-id="9abec-104">在进入开发过程之前，有几个关于如何使用容器的基本概念值得一提。</span><span class="sxs-lookup"><span data-stu-id="9abec-104">Ahead of getting into the development process there are a few basic concepts worth mentioning with regard to how you use containers.</span></span>

## <a name="container-equals-a-process"></a><span data-ttu-id="9abec-105">容器等于进程</span><span class="sxs-lookup"><span data-stu-id="9abec-105">Container equals a process</span></span>

<span data-ttu-id="9abec-106">在容器模型中，容器表示单个进程。</span><span class="sxs-lookup"><span data-stu-id="9abec-106">In the container model, a container represents a single process.</span></span> <span data-ttu-id="9abec-107">通过将容器定义为进程边界，可以开始创建用于缩放或批处理进程的基元。</span><span class="sxs-lookup"><span data-stu-id="9abec-107">By defining a container as a process boundary, you begin to create the primitives used to scale, or batch-off, processes.</span></span> <span data-ttu-id="9abec-108">运行 Docker 容器时，将看到 [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#entrypoint) 定义。</span><span class="sxs-lookup"><span data-stu-id="9abec-108">When you run a Docker container, you'll see an [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#entrypoint) definition.</span></span> <span data-ttu-id="9abec-109">这定义了容器的进程和生命周期。</span><span class="sxs-lookup"><span data-stu-id="9abec-109">This defines the process and the lifetime of the container.</span></span> <span data-ttu-id="9abec-110">该进程完成，则容器的生命周期结束。</span><span class="sxs-lookup"><span data-stu-id="9abec-110">When the process completes, the container life-cycle ends.</span></span> <span data-ttu-id="9abec-111">有长时间运行的进程（如 Web 服务器）和存留较短的进程（如批处理作业），其可能已实现为 Microsoft Azure [WebJobs](https://azure.microsoft.com/documentation/articles/websites-webjobs-resources/)。</span><span class="sxs-lookup"><span data-stu-id="9abec-111">There are long-running processes, such as web servers, and short-lived processes, such as batch jobs, which might have been implemented as Microsoft Azure [WebJobs](https://azure.microsoft.com/documentation/articles/websites-webjobs-resources/).</span></span> <span data-ttu-id="9abec-112">如果进程失败，则容器结束，Orchestrator 接管。</span><span class="sxs-lookup"><span data-stu-id="9abec-112">If the process fails, the container ends, and the orchestrator takes over.</span></span> <span data-ttu-id="9abec-113">如果业务流程协调程序已指示为使五个实例保持运行，而其中一个实例失败，则业务流程协调程序会创建另一个容器，来替换失败的进程。</span><span class="sxs-lookup"><span data-stu-id="9abec-113">If the orchestrator was instructed to keep five instances running and one fails, the orchestrator will create another container to replace the failed process.</span></span> <span data-ttu-id="9abec-114">在批处理作业中，使用参数启动该进程。</span><span class="sxs-lookup"><span data-stu-id="9abec-114">In a batch job, the process is started with parameters.</span></span> <span data-ttu-id="9abec-115">进程完成，则工作完成。</span><span class="sxs-lookup"><span data-stu-id="9abec-115">When the process completes, the work is complete.</span></span>

<span data-ttu-id="9abec-116">某些情况下，可能需要在单个容器中运行多个进程。</span><span class="sxs-lookup"><span data-stu-id="9abec-116">You might find a scenario in which you want multiple processes running in a single container.</span></span> <span data-ttu-id="9abec-117">在任何体系结构文档中，没有“绝不可能”或“总是如此”的情况。</span><span class="sxs-lookup"><span data-stu-id="9abec-117">In any architecture document, there's never a "never," nor is there always an "always."</span></span> <span data-ttu-id="9abec-118">对于需要多个进程的方案，常见的模式是使用 [Supervisor](http://supervisord.org/)。</span><span class="sxs-lookup"><span data-stu-id="9abec-118">For scenarios requiring multiple processes, a common pattern is to use [Supervisor](http://supervisord.org/).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9abec-119">[上一页](design-docker-applications.md)
>[下一页](monolithic-applications.md)</span><span class="sxs-lookup"><span data-stu-id="9abec-119">[Previous](design-docker-applications.md)
[Next](monolithic-applications.md)</span></span>

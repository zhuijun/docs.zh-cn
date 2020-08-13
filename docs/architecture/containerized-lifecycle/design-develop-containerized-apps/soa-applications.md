---
title: SOA 应用程序
description: 请记住，容器也可以是 SOA 应用程序的有用部署选项。
ms.date: 08/06/2020
ms.openlocfilehash: 5cc616eaf3be31ae704320df6ec54deed9529989
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915258"
---
# <a name="service-oriented-applications"></a><span data-ttu-id="8c13c-103">面向服务的应用程序</span><span class="sxs-lookup"><span data-stu-id="8c13c-103">Service-oriented applications</span></span>

<span data-ttu-id="8c13c-104">面向服务的体系结构 (SOA) 是一个使用过度的术语，不同的人对它的理解不尽相同。</span><span class="sxs-lookup"><span data-stu-id="8c13c-104">Service-Oriented Architecture (SOA) was an overused term that meant many different things to different people.</span></span> <span data-ttu-id="8c13c-105">但相同的理解是，SOA 意味着通过将应用程序的体系结构分解为多个服务（通常为 HTTP 服务），将其分为不同类型（例如子系统，或者在其他情况下分类为层），从而来划分应用程序的结构。</span><span class="sxs-lookup"><span data-stu-id="8c13c-105">But as a common denominator, SOA means that you structure the architecture of your application by decomposing it into several services (most commonly as HTTP services) that can be classified in different types like subsystems or, in other cases, as tiers.</span></span>

<span data-ttu-id="8c13c-106">现在，你可以将这些服务部署为 Docker 容器，从而解决与部署相关的问题，因为所有依赖项都包含在容器映像中。</span><span class="sxs-lookup"><span data-stu-id="8c13c-106">Today, you can deploy those services as Docker containers, which solve deployment-related issues because all of the dependencies are included in the container image.</span></span> <span data-ttu-id="8c13c-107">但是，当你需要扩展 SOA 时，如果基于单个实例进行部署，则可能会遇到难题。</span><span class="sxs-lookup"><span data-stu-id="8c13c-107">However, when you need to scale out SOAs, you might encounter challenges if you're deploying based on single instances.</span></span> <span data-ttu-id="8c13c-108">可以使用 Docker 群集软件或业务流程协调程序来处理此难题。</span><span class="sxs-lookup"><span data-stu-id="8c13c-108">This challenge can be handled using Docker clustering software or an orchestrator.</span></span> <span data-ttu-id="8c13c-109">在下一部分，你将探索微服务方法，更详细地了解业务流程协调程序。</span><span class="sxs-lookup"><span data-stu-id="8c13c-109">You'll get to look at orchestrators in greater detail in the next section, when you explore microservices approaches.</span></span>

<span data-ttu-id="8c13c-110">对于传统的面向服务的体系结构和更高级的微服务体系结构，Docker 容器都是有用的（但不是必需的）。</span><span class="sxs-lookup"><span data-stu-id="8c13c-110">Docker containers are useful (but not required) for both traditional service-oriented architectures and the more advanced microservices architectures.</span></span>

<span data-ttu-id="8c13c-111">归根结底，容器群集解决方案对于传统的 SOA 体系结构和更高级的微服务体系结构都很有用，其中每个微服务都拥有其数据模型。</span><span class="sxs-lookup"><span data-stu-id="8c13c-111">At the end of the day, the container clustering solutions are useful for both a traditional SOA architecture and for a more advanced microservices architecture in which each microservice owns its data model.</span></span> <span data-ttu-id="8c13c-112">由于有多个数据库，还可以横向扩展数据层，而不必使用 SOA 服务共享的单一数据库。</span><span class="sxs-lookup"><span data-stu-id="8c13c-112">And thanks to multiple databases, you can also scale out the data tier instead of working with monolithic databases shared by the SOA services.</span></span> <span data-ttu-id="8c13c-113">但是，关于拆分数据的讨论纯粹是关于架构和设计。</span><span class="sxs-lookup"><span data-stu-id="8c13c-113">However, the discussion about splitting the data is purely about architecture and design.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8c13c-114">[上一页](state-and-data-in-docker-applications.md)
>[下一页](orchestrate-high-scalability-availability.md)</span><span class="sxs-lookup"><span data-stu-id="8c13c-114">[Previous](state-and-data-in-docker-applications.md)
[Next](orchestrate-high-scalability-availability.md)</span></span>

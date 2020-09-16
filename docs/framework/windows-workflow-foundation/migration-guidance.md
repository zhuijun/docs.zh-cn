---
title: 迁移指南
ms.date: 03/30/2017
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
ms.openlocfilehash: 16f725dcb5d6f6e5d06771b7836fa187be005910
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559195"
---
# <a name="migration-guidance"></a><span data-ttu-id="bdfe8-102">迁移指南</span><span class="sxs-lookup"><span data-stu-id="bdfe8-102">Migration Guidance</span></span>

<span data-ttu-id="bdfe8-103">在 .NET Framework 4 中，Microsoft 发布了 Windows Workflow Foundation (WF) 的第二个主要版本。</span><span class="sxs-lookup"><span data-stu-id="bdfe8-103">In the .NET Framework 4, Microsoft is releasing the second major version of Windows Workflow Foundation (WF).</span></span> [!INCLUDE[wf1](../../../includes/wf1-md.md)] <span data-ttu-id="bdfe8-104">在 WinFX 中发布 (这包括了 System.web 中的类型。 \* 名称现在称为 WF3) 并在 .NET Framework 3.5 中得到增强。</span><span class="sxs-lookup"><span data-stu-id="bdfe8-104">was released in WinFX (this included the types in the System.Workflow.\* namespaces; now referred to as WF3) and enhanced in .NET Framework 3.5.</span></span> <span data-ttu-id="bdfe8-105">WF3 也是 .NET Framework 4 的一部分，但它存在于新的工作流技术 (系统中的类型。 \* 名称称为 WF4) 。</span><span class="sxs-lookup"><span data-stu-id="bdfe8-105">WF3 is also part of the .NET Framework 4, but it exists there alongside new workflow technology (the types in the System.Activities.\* namespaces; referred to as WF4).</span></span> <span data-ttu-id="bdfe8-106">考虑何时采用 WF4 时，重要的是首先要认识到您来控制时间安排。</span><span class="sxs-lookup"><span data-stu-id="bdfe8-106">When considering when to adopt WF4, it is important to first recognize that you control the timing.</span></span>  
  
- <span data-ttu-id="bdfe8-107">WF3 是 .NET Framework 4 的完全受支持的部分。</span><span class="sxs-lookup"><span data-stu-id="bdfe8-107">WF3 is a fully supported part of the .NET Framework 4.</span></span>  
  
- <span data-ttu-id="bdfe8-108">WF3 应用程序无需修改即可在 .NET Framework 4 上运行，并继续完全受支持。</span><span class="sxs-lookup"><span data-stu-id="bdfe8-108">WF3 applications run on the .NET Framework 4 without modification and continue to be fully supported.</span></span>  
  
- <span data-ttu-id="bdfe8-109">可以创建新的 WF3 应用程序，并可在 Visual Studio 2012 中编辑现有应用程序并完全支持这些应用程序。</span><span class="sxs-lookup"><span data-stu-id="bdfe8-109">New WF3 applications can be created and your existing applications can be edited in Visual Studio 2012 and are fully supported.</span></span>  
  
 <span data-ttu-id="bdfe8-110">因此，决定采用 .NET Framework 4 的决定与迁移到 WF4 (的决策是分离的。 \* 从 WF3 (\*) 。) 。</span><span class="sxs-lookup"><span data-stu-id="bdfe8-110">Thus, the decision to adopt the .NET Framework 4 is decoupled from your decision to move to WF4 (System.Activities.\*) from WF3 (System.Workflow.\*).</span></span> <span data-ttu-id="bdfe8-111">本主题提供 WF 迁移指南的相关链接，涵盖了使用 WF3 和 WF4 的相关信息。</span><span class="sxs-lookup"><span data-stu-id="bdfe8-111">This topic provides links to WF migration guidance that provides information about working with WF3 and WF4.</span></span>  
  
## <a name="wf-migration-white-papers-and-cookbooks"></a><span data-ttu-id="bdfe8-112">WF 迁移白皮书和指南</span><span class="sxs-lookup"><span data-stu-id="bdfe8-112">WF migration white papers and cookbooks</span></span>

 <span data-ttu-id="bdfe8-113">[WF 迁移概述](/previous-versions/appfabric/ff383417(v=azure.10))主题提供了 WF3 和 WF4 之间的关系以及迁移策略的全面概述。</span><span class="sxs-lookup"><span data-stu-id="bdfe8-113">The [WF Migration Overview](/previous-versions/appfabric/ff383417(v=azure.10)) topic provides a broad overview of the relationship between WF3 and WF4 and migration strategies.</span></span> <span data-ttu-id="bdfe8-114">关联的主题深入探讨特定主题。</span><span class="sxs-lookup"><span data-stu-id="bdfe8-114">Companion topics drill into specific topics.</span></span>  
  
 <span data-ttu-id="bdfe8-115">[WF Migration Overview（WF 迁移概述）](/previous-versions/appfabric/ff383417(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="bdfe8-115">[WF Migration Overview](/previous-versions/appfabric/ff383417(v=azure.10))</span></span>  
 <span data-ttu-id="bdfe8-116">描述 WF3 与 WF4 之间的关系，以及作为 .NET 4 中工作流技术的用户或潜在用户所拥有的选择。</span><span class="sxs-lookup"><span data-stu-id="bdfe8-116">Describes the relationship between WF3 and WF4, and the choices you have as a user or a potential user of workflow technology in .NET 4.</span></span>  
  
 <span data-ttu-id="bdfe8-117">[WF Migration: Best Practices for WF3 Development（WF 迁移：WF3 开发的最佳做法）](/previous-versions/appfabric/ff383417(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="bdfe8-117">[WF Migration: Best Practices for WF3 Development](/previous-versions/appfabric/ff383417(v=azure.10))</span></span>  
 <span data-ttu-id="bdfe8-118">讨论如何设计 WF3 项目以便可以更轻松地迁移至 WF4。</span><span class="sxs-lookup"><span data-stu-id="bdfe8-118">Discusses how to design WF3 artifacts so they can be more easily migrated to WF4.</span></span>  
  
 <span data-ttu-id="bdfe8-119">[WF Guidance: Rules（WF 指南：规则）](/previous-versions/appfabric/ff383417(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="bdfe8-119">[WF Guidance: Rules](/previous-versions/appfabric/ff383417(v=azure.10))</span></span>  
 <span data-ttu-id="bdfe8-120">介绍如何将规则相关投资引入 .NET Framework 4 解决方案。</span><span class="sxs-lookup"><span data-stu-id="bdfe8-120">Discusses how to bring rules-related investments forward into .NET Framework 4 solutions.</span></span>  
  
 <span data-ttu-id="bdfe8-121">[WF 指南：状态机](/previous-versions/appfabric/ff383417(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="bdfe8-121">[WF Guidance: State Machine](/previous-versions/appfabric/ff383417(v=azure.10))</span></span>  
 <span data-ttu-id="bdfe8-122">讨论在缺乏状态机活动下的 WF4 控制流建模。</span><span class="sxs-lookup"><span data-stu-id="bdfe8-122">Discusses WF4 control flow modeling in the absence of a State-Machine activity.</span></span>  
  
 <span data-ttu-id="bdfe8-123">请注意，本指南仅适用于面向 .NET Framework 4 的工作流项目。</span><span class="sxs-lookup"><span data-stu-id="bdfe8-123">Note that this guidance only applies to workflow projects that target .NET Framework 4.</span></span> <span data-ttu-id="bdfe8-124">状态机工作流在 .NET 4.0.1 中是通过发布 Platform Update 1 加入的，是 .NET Framework 4.5 的组成部分。</span><span class="sxs-lookup"><span data-stu-id="bdfe8-124">State Machine workflows were added in .NET 4.0.1 with the release of Platform Update 1, and were included as part of .NET Framework 4.5.</span></span> <span data-ttu-id="bdfe8-125">有关 .NET 4.0.1 中的状态机工作流的详细信息-4.0.3 和 .NET Framework 4.5，请参阅 [Update 4.0.1 for Microsoft .NET Framework 4 功能](/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100)) 和 [状态机工作流](state-machine-workflows.md)。</span><span class="sxs-lookup"><span data-stu-id="bdfe8-125">For more information about state machine workflows in .NET 4.0.1 - 4.0.3 and .NET Framework 4.5, see [Update 4.0.1 for Microsoft .NET Framework 4 Features](/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100)) and [State Machine Workflows](state-machine-workflows.md).</span></span>  
  
 <span data-ttu-id="bdfe8-126">[WF Migration Cookbook: Custom Activities（WF 迁移实用手册：自定义活动）](/previous-versions/appfabric/ff383417(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="bdfe8-126">[WF Migration Cookbook: Custom Activities](/previous-versions/appfabric/ff383417(v=azure.10))</span></span>  
 <span data-ttu-id="bdfe8-127">提供用于在 WF4 上重新设计 WF3 自定义活动的示例和说明。</span><span class="sxs-lookup"><span data-stu-id="bdfe8-127">Provides examples and instructions for redesigning WF3 custom activities on WF4.</span></span>  
  
 <span data-ttu-id="bdfe8-128">[WF Migration Cookbook: Advanced Custom Activities（WF 迁移实用手册：高级自定义活动）](/previous-versions/appfabric/ff383417(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="bdfe8-128">[WF Migration Cookbook: Advanced Custom Activities](/previous-versions/appfabric/ff383417(v=azure.10))</span></span>  
 <span data-ttu-id="bdfe8-129">提供将使用 WF3 队列和对子活动进行排程的高级 WF3 自定义活动重新设计为 WF4 自定义活动的指南。</span><span class="sxs-lookup"><span data-stu-id="bdfe8-129">Provides guidance for redesigning advanced WF3 custom activities that use WF3 queues and schedule child activities as WF4 custom activities.</span></span>  
  
 <span data-ttu-id="bdfe8-130">[WF Migration Cookbook: Workflows（WF 迁移实用手册：工作流）](/previous-versions/appfabric/ff383417(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="bdfe8-130">[WF Migration Cookbook: Workflows](/previous-versions/appfabric/ff383417(v=azure.10))</span></span>  
 <span data-ttu-id="bdfe8-131">提供用于在 WF4 上重新设计 WF3 工作流的示例和说明。</span><span class="sxs-lookup"><span data-stu-id="bdfe8-131">Provides examples and instructions for redesigning WF3 workflows on WF4.</span></span>  
  
 <span data-ttu-id="bdfe8-132">[WF Migration Cookbook: Workflow Hosting（WF 迁移实用手册：工作流承载）](/previous-versions/appfabric/ff383417(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="bdfe8-132">[WF Migration Cookbook: Workflow Hosting](/previous-versions/appfabric/ff383417(v=azure.10))</span></span>  
 <span data-ttu-id="bdfe8-133">提供将 WF3 承载代码重新设计为 WF4 承载代码的指南。</span><span class="sxs-lookup"><span data-stu-id="bdfe8-133">Provides guidance for redesigning WF3 hosting code as WF4 hosting code.</span></span> <span data-ttu-id="bdfe8-134">目标是介绍 WF3 和 WF4 在工作流承载上的关键差异。</span><span class="sxs-lookup"><span data-stu-id="bdfe8-134">The goal is to cover the key differences in workflow hosting between WF3 and WF4.</span></span>  
  
 <span data-ttu-id="bdfe8-135">[WF Migration Cookbook: Workflow（WF 迁移实用手册：工作流跟踪）](/previous-versions/appfabric/ff383417(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="bdfe8-135">[WF Migration Cookbook: Workflow Tracking](/previous-versions/appfabric/ff383417(v=azure.10))</span></span>  
 <span data-ttu-id="bdfe8-136">提供用等价 WF4 跟踪代码和配置来重新设计 WF3 跟踪代码和配置的指南。</span><span class="sxs-lookup"><span data-stu-id="bdfe8-136">Provides guidance for redesigning WF3 tracking code and configuration using equivalent WF4 tracking code and configuration.</span></span>  
  
 <span data-ttu-id="bdfe8-137">[WF Guidance: Workflow Services（WF 指南：工作流服务）](/previous-versions/appfabric/ff383417(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="bdfe8-137">[WF Guidance: Workflow Services](/previous-versions/appfabric/ff383417(v=azure.10))</span></span>  
 <span data-ttu-id="bdfe8-138">提供面向示例的分步说明，针对现成活动的一般方案，将在 WF3 中创建、实现 Windows Communication Foundation (WCF) Web 服务（通常称为工作流服务）的工作流重新设计为使用 WF4。</span><span class="sxs-lookup"><span data-stu-id="bdfe8-138">Provides example-oriented step-by-step instructions for redesigning workflows that implement Windows Communication Foundation (WCF) web services (commonly referred to as workflow services) created in WF3 to use WF4, for common scenarios for out-of-box activities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdfe8-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="bdfe8-139">See also</span></span>

- <xref:System.Activities.Statements.Interop>

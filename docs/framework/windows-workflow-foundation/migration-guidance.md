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
# <a name="migration-guidance"></a>迁移指南

在 .NET Framework 4 中，Microsoft 发布了 Windows Workflow Foundation (WF) 的第二个主要版本。 [!INCLUDE[wf1](../../../includes/wf1-md.md)] 在 WinFX 中发布 (这包括了 System.web 中的类型。 \* 名称现在称为 WF3) 并在 .NET Framework 3.5 中得到增强。 WF3 也是 .NET Framework 4 的一部分，但它存在于新的工作流技术 (系统中的类型。 \* 名称称为 WF4) 。 考虑何时采用 WF4 时，重要的是首先要认识到您来控制时间安排。  
  
- WF3 是 .NET Framework 4 的完全受支持的部分。  
  
- WF3 应用程序无需修改即可在 .NET Framework 4 上运行，并继续完全受支持。  
  
- 可以创建新的 WF3 应用程序，并可在 Visual Studio 2012 中编辑现有应用程序并完全支持这些应用程序。  
  
 因此，决定采用 .NET Framework 4 的决定与迁移到 WF4 (的决策是分离的。 \* 从 WF3 (\*) 。) 。 本主题提供 WF 迁移指南的相关链接，涵盖了使用 WF3 和 WF4 的相关信息。  
  
## <a name="wf-migration-white-papers-and-cookbooks"></a>WF 迁移白皮书和指南

 [WF 迁移概述](/previous-versions/appfabric/ff383417(v=azure.10))主题提供了 WF3 和 WF4 之间的关系以及迁移策略的全面概述。 关联的主题深入探讨特定主题。  
  
 [WF Migration Overview（WF 迁移概述）](/previous-versions/appfabric/ff383417(v=azure.10))  
 描述 WF3 与 WF4 之间的关系，以及作为 .NET 4 中工作流技术的用户或潜在用户所拥有的选择。  
  
 [WF Migration: Best Practices for WF3 Development（WF 迁移：WF3 开发的最佳做法）](/previous-versions/appfabric/ff383417(v=azure.10))  
 讨论如何设计 WF3 项目以便可以更轻松地迁移至 WF4。  
  
 [WF Guidance: Rules（WF 指南：规则）](/previous-versions/appfabric/ff383417(v=azure.10))  
 介绍如何将规则相关投资引入 .NET Framework 4 解决方案。  
  
 [WF 指南：状态机](/previous-versions/appfabric/ff383417(v=azure.10))  
 讨论在缺乏状态机活动下的 WF4 控制流建模。  
  
 请注意，本指南仅适用于面向 .NET Framework 4 的工作流项目。 状态机工作流在 .NET 4.0.1 中是通过发布 Platform Update 1 加入的，是 .NET Framework 4.5 的组成部分。 有关 .NET 4.0.1 中的状态机工作流的详细信息-4.0.3 和 .NET Framework 4.5，请参阅 [Update 4.0.1 for Microsoft .NET Framework 4 功能](/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100)) 和 [状态机工作流](state-machine-workflows.md)。  
  
 [WF Migration Cookbook: Custom Activities（WF 迁移实用手册：自定义活动）](/previous-versions/appfabric/ff383417(v=azure.10))  
 提供用于在 WF4 上重新设计 WF3 自定义活动的示例和说明。  
  
 [WF Migration Cookbook: Advanced Custom Activities（WF 迁移实用手册：高级自定义活动）](/previous-versions/appfabric/ff383417(v=azure.10))  
 提供将使用 WF3 队列和对子活动进行排程的高级 WF3 自定义活动重新设计为 WF4 自定义活动的指南。  
  
 [WF Migration Cookbook: Workflows（WF 迁移实用手册：工作流）](/previous-versions/appfabric/ff383417(v=azure.10))  
 提供用于在 WF4 上重新设计 WF3 工作流的示例和说明。  
  
 [WF Migration Cookbook: Workflow Hosting（WF 迁移实用手册：工作流承载）](/previous-versions/appfabric/ff383417(v=azure.10))  
 提供将 WF3 承载代码重新设计为 WF4 承载代码的指南。 目标是介绍 WF3 和 WF4 在工作流承载上的关键差异。  
  
 [WF Migration Cookbook: Workflow（WF 迁移实用手册：工作流跟踪）](/previous-versions/appfabric/ff383417(v=azure.10))  
 提供用等价 WF4 跟踪代码和配置来重新设计 WF3 跟踪代码和配置的指南。  
  
 [WF Guidance: Workflow Services（WF 指南：工作流服务）](/previous-versions/appfabric/ff383417(v=azure.10))  
 提供面向示例的分步说明，针对现成活动的一般方案，将在 WF3 中创建、实现 Windows Communication Foundation (WCF) Web 服务（通常称为工作流服务）的工作流重新设计为使用 WF4。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Activities.Statements.Interop>

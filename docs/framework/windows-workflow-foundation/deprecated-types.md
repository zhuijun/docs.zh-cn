---
title: Windows Workflow Foundation 中弃用的类型
ms.date: 03/30/2017
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
ms.openlocfilehash: b0ec30d2778333537e781e6681927f7048b630ea
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543779"
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a>Windows Workflow Foundation 中弃用的类型
在 .NET 4 中，工作流团队在 <xref:System.Activities> 命名空间中发布了一个全新的工作流引擎。 随着 .NET 4.5 Beta 的发布，我们将 "WF 3"、和命名空间中的大多数类型标记 <xref:System.Workflow.Activities> <xref:System.Workflow.ComponentModel>  <xref:System.Workflow.Runtime> 为过时。  
  
## <a name="obsolete-namespaces-and-tools"></a>过时的命名空间和工具  
 以下程序集具有将被弃用的一个或多个公共类型：  
  
- System.Workflow.Activities.dll  
  
- System.Workflow.ComponentModel.dll  
  
- System.Workflow.Runtime.dll  
  
- System.WorkflowServices.dll  
  
- Microsoft.Workflow.DebugController.dll  
  
- Microsoft.Workflow.Compiler.exe  
  
- Wfc.exe  
  
 因此，使用已弃用的 WF 3 API 的客户将会遇到生成警告，其中包含如下消息：  
  
 **警告 BC40000： X 已过时： WF 3 类型已弃用。请改用 WF 4。** 我们将在将来的版本中从 .NET Framework 移除这些类型，但我们尚未确定有关时间范围（不在 4.5 中移除）。 借助于当前这个步骤，我们可以将我们的方向传达给客户，使他们能够有充裕的时间转移到新的 WF4 模型。 当然，我们将继续支持 [Microsoft 支持部门生命周期策略](/lifecycle/)下的这些 WF 3 类型。 现有的 WF3 应用程序在 .NET 4.5 上运行时不会出现问题，并且 Visual Studio 2012 将支持新的和现有的基于 WF3 的解决方案。  
  
 <xref:System.Workflow.Activities.Rules> 命名空间中与规则相关的类型（在 WF 4.5 中没有替代选项）尚不会被弃用。  
  
 如果客户想要将其应用程序迁移到 WF 4，则会在 [工作流4迁移指南](migration-guidance.md)中找到帮助。

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
# <a name="deprecated-types-in-windows-workflow-foundation"></a><span data-ttu-id="9e131-102">Windows Workflow Foundation 中弃用的类型</span><span class="sxs-lookup"><span data-stu-id="9e131-102">Deprecated types in Windows Workflow Foundation</span></span>
<span data-ttu-id="9e131-103">在 .NET 4 中，工作流团队在 <xref:System.Activities> 命名空间中发布了一个全新的工作流引擎。</span><span class="sxs-lookup"><span data-stu-id="9e131-103">In .NET 4 the Workflow Team released an all new Workflow engine in the <xref:System.Activities> namespace.</span></span> <span data-ttu-id="9e131-104">随着 .NET 4.5 Beta 的发布，我们将 "WF 3"、和命名空间中的大多数类型标记 <xref:System.Workflow.Activities> <xref:System.Workflow.ComponentModel>  <xref:System.Workflow.Runtime> 为过时。</span><span class="sxs-lookup"><span data-stu-id="9e131-104">With the release of .NET 4.5 Beta we are marking most of the types in the "WF 3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, and  <xref:System.Workflow.Runtime> namespaces as obsolete.</span></span>  
  
## <a name="obsolete-namespaces-and-tools"></a><span data-ttu-id="9e131-105">过时的命名空间和工具</span><span class="sxs-lookup"><span data-stu-id="9e131-105">Obsolete namespaces and tools</span></span>  
 <span data-ttu-id="9e131-106">以下程序集具有将被弃用的一个或多个公共类型：</span><span class="sxs-lookup"><span data-stu-id="9e131-106">The following assemblies have one or more public types that will be deprecated:</span></span>  
  
- <span data-ttu-id="9e131-107">System.Workflow.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="9e131-107">System.Workflow.Activities.dll</span></span>  
  
- <span data-ttu-id="9e131-108">System.Workflow.ComponentModel.dll</span><span class="sxs-lookup"><span data-stu-id="9e131-108">System.Workflow.ComponentModel.dll</span></span>  
  
- <span data-ttu-id="9e131-109">System.Workflow.Runtime.dll</span><span class="sxs-lookup"><span data-stu-id="9e131-109">System.Workflow.Runtime.dll</span></span>  
  
- <span data-ttu-id="9e131-110">System.WorkflowServices.dll</span><span class="sxs-lookup"><span data-stu-id="9e131-110">System.WorkflowServices.dll</span></span>  
  
- <span data-ttu-id="9e131-111">Microsoft.Workflow.DebugController.dll</span><span class="sxs-lookup"><span data-stu-id="9e131-111">Microsoft.Workflow.DebugController.dll</span></span>  
  
- <span data-ttu-id="9e131-112">Microsoft.Workflow.Compiler.exe</span><span class="sxs-lookup"><span data-stu-id="9e131-112">Microsoft.Workflow.Compiler.exe</span></span>  
  
- <span data-ttu-id="9e131-113">Wfc.exe</span><span class="sxs-lookup"><span data-stu-id="9e131-113">Wfc.exe</span></span>  
  
 <span data-ttu-id="9e131-114">因此，使用已弃用的 WF 3 API 的客户将会遇到生成警告，其中包含如下消息：</span><span class="sxs-lookup"><span data-stu-id="9e131-114">As a result, customers who are using the deprecated WF 3 APIs will encounter build warnings with a message similar to the following:</span></span>  
  
 <span data-ttu-id="9e131-115">**警告 BC40000： X 已过时： WF 3 类型已弃用。请改用 WF 4。**</span><span class="sxs-lookup"><span data-stu-id="9e131-115">**Warning BC40000: X is obsolete: WF 3 types are deprecated. Please use WF 4 instead.**</span></span> <span data-ttu-id="9e131-116">我们将在将来的版本中从 .NET Framework 移除这些类型，但我们尚未确定有关时间范围（不在 4.5 中移除）。</span><span class="sxs-lookup"><span data-stu-id="9e131-116">We will remove the types from the .NET Framework in a future release, but we have not yet determined that timeframe (not in 4.5).</span></span> <span data-ttu-id="9e131-117">借助于当前这个步骤，我们可以将我们的方向传达给客户，使他们能够有充裕的时间转移到新的 WF4 模型。</span><span class="sxs-lookup"><span data-stu-id="9e131-117">This current step allows us to communicate our direction to our customers and allow them plenty of time to move to the new WF4 model.</span></span> <span data-ttu-id="9e131-118">当然，我们将继续支持 [Microsoft 支持部门生命周期策略](/lifecycle/)下的这些 WF 3 类型。</span><span class="sxs-lookup"><span data-stu-id="9e131-118">We will, of course, continue to support these WF 3 types under the [Microsoft Support Lifecycle Policy](/lifecycle/).</span></span> <span data-ttu-id="9e131-119">现有的 WF3 应用程序在 .NET 4.5 上运行时不会出现问题，并且 Visual Studio 2012 将支持新的和现有的基于 WF3 的解决方案。</span><span class="sxs-lookup"><span data-stu-id="9e131-119">Existing WF3 applications will run without issue on .NET 4.5, and Visual Studio 2012 will support new and existing WF3-based solutions.</span></span>  
  
 <span data-ttu-id="9e131-120"><xref:System.Workflow.Activities.Rules> 命名空间中与规则相关的类型（在 WF 4.5 中没有替代选项）尚不会被弃用。</span><span class="sxs-lookup"><span data-stu-id="9e131-120">Rules related types in the <xref:System.Workflow.Activities.Rules> namespace, which do not have a replacement in WF 4.5, have not been deprecated.</span></span>  
  
 <span data-ttu-id="9e131-121">如果客户想要将其应用程序迁移到 WF 4，则会在 [工作流4迁移指南](migration-guidance.md)中找到帮助。</span><span class="sxs-lookup"><span data-stu-id="9e131-121">Customers who want to migrate their applications to WF 4 will find help in the [Workflow 4 Migration Guidance](migration-guidance.md).</span></span>

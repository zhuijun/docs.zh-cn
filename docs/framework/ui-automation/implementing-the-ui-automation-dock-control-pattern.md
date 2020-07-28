---
title: 实现 UI 自动化 Dock 控件模式
description: 了解如何实现 UI 自动化 dock 控件模式。 使用 DockPattern 控件模式公开控件的停靠属性。 实现 IDockProvider。
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, dock
- dock control pattern
- UI Automation, dock control pattern
ms.assetid: ea3d2212-7c8e-4dd7-bf08-73141ca2d4fb
ms.openlocfilehash: 8080d78c7bded3cb884f92948eb1259cda5544dc
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165902"
---
# <a name="implementing-the-ui-automation-dock-control-pattern"></a><span data-ttu-id="10a80-105">实现 UI 自动化 Dock 控件模式</span><span class="sxs-lookup"><span data-stu-id="10a80-105">Implementing the UI Automation Dock Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="10a80-106">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="10a80-106">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="10a80-107">有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="10a80-107">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="10a80-108">本主题介绍实现 <xref:System.Windows.Automation.Provider.IDockProvider>的准则和约定，包括有关属性的信息。</span><span class="sxs-lookup"><span data-stu-id="10a80-108">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IDockProvider>, including information about properties.</span></span> <span data-ttu-id="10a80-109">本主题的结尾列出了指向其他参考资料的链接。</span><span class="sxs-lookup"><span data-stu-id="10a80-109">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="10a80-110"><xref:System.Windows.Automation.DockPattern> 控件模式用于公开停靠容器内控件的停靠属性。</span><span class="sxs-lookup"><span data-stu-id="10a80-110">The <xref:System.Windows.Automation.DockPattern> control pattern is used to expose the dock properties of a control within a docking container.</span></span> <span data-ttu-id="10a80-111">停靠容器是一个可让你水平或垂直地在彼此之间相对排列子元素的控件。</span><span class="sxs-lookup"><span data-stu-id="10a80-111">A docking container is a control that allows you to arrange child elements horizontally and vertically, relative to each other.</span></span> <span data-ttu-id="10a80-112">有关实现此控件模式的控件示例，请参阅 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="10a80-112">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
 <span data-ttu-id="10a80-113">![具有两个停靠子级的停靠容器。](./media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")</span><span class="sxs-lookup"><span data-stu-id="10a80-113">![Docking container with two docked children.](./media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")</span></span>  
<span data-ttu-id="10a80-114">Visual Studio 中的停靠示例，其中“类视图”窗口为 DockPosition.Right，“错误列表”窗口为 DockPosition.Bottom</span><span class="sxs-lookup"><span data-stu-id="10a80-114">Docking Example from Visual Studio Where "Class View" Window Is DockPosition.Right and "Error List" Window Is DockPosition.Bottom</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="10a80-115">实现准则和约定</span><span class="sxs-lookup"><span data-stu-id="10a80-115">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="10a80-116">在实现 Dock 控件模式时，请注意以下准则和约定：</span><span class="sxs-lookup"><span data-stu-id="10a80-116">When implementing the Dock control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="10a80-117"><xref:System.Windows.Automation.Provider.IDockProvider> 不公开停靠容器的任何属性，或者停靠在停靠容器内当前控件旁边的控件的任何属性。</span><span class="sxs-lookup"><span data-stu-id="10a80-117"><xref:System.Windows.Automation.Provider.IDockProvider> does not expose any properties of the docking container or any properties of controls that are docked adjacent to the current control within the docking container.</span></span>  
  
- <span data-ttu-id="10a80-118">控件根据其当前的 z 顺序彼此相对停靠；控件的 z 顺序位置越高，则其距停靠容器的指定边缘就越远。</span><span class="sxs-lookup"><span data-stu-id="10a80-118">Controls are docked relative to each other based on their current z-order; the higher their z-order placement, the farther they are placed from the specified edge of the docking container.</span></span>  
  
- <span data-ttu-id="10a80-119">如果调整了停靠容器的大小，则容器内的停靠控件将沿着最初的停靠边缘重新定位。</span><span class="sxs-lookup"><span data-stu-id="10a80-119">If the docking container is resized, any docked controls within the container will be repositioned flush to the same edge to which they were originally docked.</span></span> <span data-ttu-id="10a80-120">停靠的控件也将调整大小，以根据其 <xref:System.Windows.Automation.DockPosition>的停靠行为来填充容器内的任何空间。</span><span class="sxs-lookup"><span data-stu-id="10a80-120">The docked controls will also resize to fill any space within the container according to the docking behavior of their <xref:System.Windows.Automation.DockPosition>.</span></span> <span data-ttu-id="10a80-121">例如，如果指定了 <xref:System.Windows.Automation.DockPosition.Top> ，则控件的左边和右边将会扩展以填充任何可用空间。</span><span class="sxs-lookup"><span data-stu-id="10a80-121">For example, if <xref:System.Windows.Automation.DockPosition.Top> is specified, the left and right sides of the control will expand to fill any available space.</span></span> <span data-ttu-id="10a80-122">如果指定了 <xref:System.Windows.Automation.DockPosition.Fill> ，则控件的所有四个边都将扩展以填充任何可用空间。</span><span class="sxs-lookup"><span data-stu-id="10a80-122">If <xref:System.Windows.Automation.DockPosition.Fill> is specified, all four sides of the control will expand to fill any available space.</span></span>  
  
- <span data-ttu-id="10a80-123">在具有多个监视器的系统上，控件应该停靠在当前监视器的左侧或右侧。</span><span class="sxs-lookup"><span data-stu-id="10a80-123">On a multi-monitor system, controls should dock to the left or right side of the current monitor.</span></span> <span data-ttu-id="10a80-124">如果这不可能，则控件应该停靠在最左侧监视器的左侧或最右侧监视器的右侧。</span><span class="sxs-lookup"><span data-stu-id="10a80-124">If that is not possible, they should dock to the left side of the leftmost monitor or the right side of the rightmost monitor.</span></span>  
  
<a name="Required_Members_for_IDockProvider"></a>
## <a name="required-members-for-idockprovider"></a><span data-ttu-id="10a80-125">IDockProvider 必需的成员</span><span class="sxs-lookup"><span data-stu-id="10a80-125">Required Members for IDockProvider</span></span>  
 <span data-ttu-id="10a80-126">实现 IDockProvider 接口需要以下属性和方法。</span><span class="sxs-lookup"><span data-stu-id="10a80-126">The following properties and methods are required for implementing the IDockProvider interface.</span></span>  
  
|<span data-ttu-id="10a80-127">必需的成员</span><span class="sxs-lookup"><span data-stu-id="10a80-127">Required members</span></span>|<span data-ttu-id="10a80-128">成员类型</span><span class="sxs-lookup"><span data-stu-id="10a80-128">Member type</span></span>|<span data-ttu-id="10a80-129">说明</span><span class="sxs-lookup"><span data-stu-id="10a80-129">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IDockProvider.DockPosition%2A>|<span data-ttu-id="10a80-130">Property</span><span class="sxs-lookup"><span data-stu-id="10a80-130">Property</span></span>|<span data-ttu-id="10a80-131">无</span><span class="sxs-lookup"><span data-stu-id="10a80-131">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A>|<span data-ttu-id="10a80-132">方法</span><span class="sxs-lookup"><span data-stu-id="10a80-132">Method</span></span>|<span data-ttu-id="10a80-133">无</span><span class="sxs-lookup"><span data-stu-id="10a80-133">None</span></span>|  
  
 <span data-ttu-id="10a80-134">没有与此控件模式关联的事件。</span><span class="sxs-lookup"><span data-stu-id="10a80-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="10a80-135">例外</span><span class="sxs-lookup"><span data-stu-id="10a80-135">Exceptions</span></span>  
 <span data-ttu-id="10a80-136">提供程序必须引发以下异常。</span><span class="sxs-lookup"><span data-stu-id="10a80-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="10a80-137">例外类型</span><span class="sxs-lookup"><span data-stu-id="10a80-137">Exception type</span></span>|<span data-ttu-id="10a80-138">条件</span><span class="sxs-lookup"><span data-stu-id="10a80-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A><br /><br /> <span data-ttu-id="10a80-139">-当控件无法执行请求的停靠样式时。</span><span class="sxs-lookup"><span data-stu-id="10a80-139">-   When a control is not able to execute the requested dock style.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="10a80-140">请参阅</span><span class="sxs-lookup"><span data-stu-id="10a80-140">See also</span></span>

- [<span data-ttu-id="10a80-141">UI 自动化控件模式概述</span><span class="sxs-lookup"><span data-stu-id="10a80-141">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="10a80-142">在 UI 自动化提供程序中支持控件模式</span><span class="sxs-lookup"><span data-stu-id="10a80-142">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="10a80-143">客户端的 UI 自动化控件模式</span><span class="sxs-lookup"><span data-stu-id="10a80-143">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="10a80-144">UI 自动化树概述</span><span class="sxs-lookup"><span data-stu-id="10a80-144">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="10a80-145">在 UI 自动化中使用缓存</span><span class="sxs-lookup"><span data-stu-id="10a80-145">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)

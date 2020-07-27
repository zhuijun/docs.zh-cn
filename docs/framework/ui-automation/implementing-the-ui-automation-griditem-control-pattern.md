---
title: 实现 UI 自动化 GridItem 控件模式
description: 了解在 UI 自动化中为网格项实现 GridItemPattern 控件模式的准则和约定。 请参阅 IGridItemProvider 的必需成员。
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: e0a0c616f3f0cf9bc091e4fbb496d71ab8550bd3
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165826"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a><span data-ttu-id="d055e-104">实现 UI 自动化 GridItem 控件模式</span><span class="sxs-lookup"><span data-stu-id="d055e-104">Implementing the UI Automation GridItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="d055e-105">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="d055e-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="d055e-106">有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="d055e-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="d055e-107">本主题介绍实现 <xref:System.Windows.Automation.Provider.IGridItemProvider>的准则和约定，包括有关属性的信息。</span><span class="sxs-lookup"><span data-stu-id="d055e-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span></span> <span data-ttu-id="d055e-108">本概述的结尾列出了指向其他参考资料的链接。</span><span class="sxs-lookup"><span data-stu-id="d055e-108">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="d055e-109"><xref:System.Windows.Automation.GridItemPattern> 控件模式用于支持实现 <xref:System.Windows.Automation.Provider.IGridProvider> 的容器的各个子控件。</span><span class="sxs-lookup"><span data-stu-id="d055e-109">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span> <span data-ttu-id="d055e-110">有关实现此控件模式的控件示例，请参阅 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="d055e-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="d055e-111">实现准则和约定</span><span class="sxs-lookup"><span data-stu-id="d055e-111">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="d055e-112">在实现 <xref:System.Windows.Automation.Provider.IGridProvider> 时，请注意以下准则和约定：</span><span class="sxs-lookup"><span data-stu-id="d055e-112">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="d055e-113">网格坐标从零开始，左上角单元格坐标为 (0, 0)。</span><span class="sxs-lookup"><span data-stu-id="d055e-113">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="d055e-114">合并的单元格将根据 UI 自动化提供程序定义的其基本定位单元格来报告其 <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> 和 <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="d055e-114">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span></span> <span data-ttu-id="d055e-115">通常，它将是最左上方的行或列。</span><span class="sxs-lookup"><span data-stu-id="d055e-115">Typically, it will be the topmost and leftmost row or column.</span></span>  
  
- <span data-ttu-id="d055e-116"><xref:System.Windows.Automation.Provider.IGridItemProvider> 不对网格进行实时操作，如合并或拆分单元格。</span><span class="sxs-lookup"><span data-stu-id="d055e-116"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span></span>  
  
- <span data-ttu-id="d055e-117">通常，可以使用键盘遍历实现 <xref:System.Windows.Automation.Provider.IGridItemProvider> 的控件（即 UI 自动化客户端可以移动到相邻的控件）。</span><span class="sxs-lookup"><span data-stu-id="d055e-117">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span></span>  
  
<a name="Required_Members_for_IGridItemProvider"></a>
## <a name="required-members-for-igriditemprovider"></a><span data-ttu-id="d055e-118">IGridItemProvider 必需的成员</span><span class="sxs-lookup"><span data-stu-id="d055e-118">Required Members for IGridItemProvider</span></span>  
 <span data-ttu-id="d055e-119">实现 <xref:System.Windows.Automation.Provider.IGridItemProvider>需要以下属性和方法。</span><span class="sxs-lookup"><span data-stu-id="d055e-119">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span>  
  
|<span data-ttu-id="d055e-120">必需的成员</span><span class="sxs-lookup"><span data-stu-id="d055e-120">Required members</span></span>|<span data-ttu-id="d055e-121">成员类型</span><span class="sxs-lookup"><span data-stu-id="d055e-121">Member type</span></span>|<span data-ttu-id="d055e-122">说明</span><span class="sxs-lookup"><span data-stu-id="d055e-122">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|<span data-ttu-id="d055e-123">属性</span><span class="sxs-lookup"><span data-stu-id="d055e-123">Property</span></span>|<span data-ttu-id="d055e-124">无</span><span class="sxs-lookup"><span data-stu-id="d055e-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|<span data-ttu-id="d055e-125">属性</span><span class="sxs-lookup"><span data-stu-id="d055e-125">Property</span></span>|<span data-ttu-id="d055e-126">无</span><span class="sxs-lookup"><span data-stu-id="d055e-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|<span data-ttu-id="d055e-127">属性</span><span class="sxs-lookup"><span data-stu-id="d055e-127">Property</span></span>|<span data-ttu-id="d055e-128">无</span><span class="sxs-lookup"><span data-stu-id="d055e-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|<span data-ttu-id="d055e-129">属性</span><span class="sxs-lookup"><span data-stu-id="d055e-129">Property</span></span>|<span data-ttu-id="d055e-130">无</span><span class="sxs-lookup"><span data-stu-id="d055e-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|<span data-ttu-id="d055e-131">属性</span><span class="sxs-lookup"><span data-stu-id="d055e-131">Property</span></span>|<span data-ttu-id="d055e-132">无</span><span class="sxs-lookup"><span data-stu-id="d055e-132">None</span></span>|  
  
 <span data-ttu-id="d055e-133">没有与此控件模式关联的方法或事件。</span><span class="sxs-lookup"><span data-stu-id="d055e-133">This control pattern has no associated methods or events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="d055e-134">例外</span><span class="sxs-lookup"><span data-stu-id="d055e-134">Exceptions</span></span>  
 <span data-ttu-id="d055e-135">没有与此控件模式关联的异常。</span><span class="sxs-lookup"><span data-stu-id="d055e-135">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d055e-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d055e-136">See also</span></span>

- [<span data-ttu-id="d055e-137">UI 自动化控件模式概述</span><span class="sxs-lookup"><span data-stu-id="d055e-137">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="d055e-138">在 UI 自动化提供程序中支持控件模式</span><span class="sxs-lookup"><span data-stu-id="d055e-138">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="d055e-139">客户端的 UI 自动化控件模式</span><span class="sxs-lookup"><span data-stu-id="d055e-139">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="d055e-140">实现 UI 自动化 Grid 控件模式</span><span class="sxs-lookup"><span data-stu-id="d055e-140">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="d055e-141">UI 自动化树概述</span><span class="sxs-lookup"><span data-stu-id="d055e-141">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="d055e-142">在 UI 自动化中使用缓存</span><span class="sxs-lookup"><span data-stu-id="d055e-142">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)

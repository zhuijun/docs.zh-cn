---
title: 实现 UI 自动化 TableItem 控件模式
description: 在 UI 自动化中查看实现 TableItem 控件模式的准则和约定。 了解 ITableItemProvider 接口的必需成员。
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: 3d6d31fe0e041fbba147df14d290a775188755f2
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163520"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a><span data-ttu-id="9b562-104">实现 UI 自动化 TableItem 控件模式</span><span class="sxs-lookup"><span data-stu-id="9b562-104">Implementing the UI Automation TableItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="9b562-105">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="9b562-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="9b562-106">有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="9b562-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="9b562-107">本主题介绍了实现 <xref:System.Windows.Automation.Provider.ITableItemProvider>的准则和约定，包括有关事件和属性的信息。</span><span class="sxs-lookup"><span data-stu-id="9b562-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableItemProvider>, including information about events and properties.</span></span> <span data-ttu-id="9b562-108">本概述的结尾列出了指向其他参考资料的链接。</span><span class="sxs-lookup"><span data-stu-id="9b562-108">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="9b562-109"><xref:System.Windows.Automation.TableItemPattern> 控件模式用于支持实现 <xref:System.Windows.Automation.Provider.ITableProvider> 的容器的子控件。</span><span class="sxs-lookup"><span data-stu-id="9b562-109">The <xref:System.Windows.Automation.TableItemPattern> control pattern is used to support child controls of containers that implement <xref:System.Windows.Automation.Provider.ITableProvider>.</span></span> <span data-ttu-id="9b562-110">对个别单元格功能的访问是由 <xref:System.Windows.Automation.Provider.IGridItemProvider> 必需的并发实现提供的。</span><span class="sxs-lookup"><span data-stu-id="9b562-110">Access to individual cell functionality is provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span> <span data-ttu-id="9b562-111">此控件模式类似于 <xref:System.Windows.Automation.Provider.IGridItemProvider>，不同之处在于任何实现 <xref:System.Windows.Automation.Provider.ITableItemProvider> 的控件都必须以编程方式公开各个单元格与其行和列信息之间的关系。</span><span class="sxs-lookup"><span data-stu-id="9b562-111">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridItemProvider> with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableItemProvider> must programmatically expose the relationship between the individual cell and its row and column information.</span></span> <span data-ttu-id="9b562-112">有关实现此控件模式的控件示例，请参阅 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="9b562-112">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="9b562-113">实现准则和约定</span><span class="sxs-lookup"><span data-stu-id="9b562-113">Implementation Guidelines and Conventions</span></span>  
  
- <span data-ttu-id="9b562-114">有关相关的网格项功能，请参阅[实现 UI 自动化 GridItem 控件模式](implementing-the-ui-automation-griditem-control-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="9b562-114">For related grid item functionality, see [Implementing the UI Automation GridItem Control Pattern](implementing-the-ui-automation-griditem-control-pattern.md).</span></span>  
  
<a name="Required_Members_for_ITableItemProvider"></a>
## <a name="required-members-for-itableitemprovider"></a><span data-ttu-id="9b562-115">ITableItemProvider 必需的成员</span><span class="sxs-lookup"><span data-stu-id="9b562-115">Required Members for ITableItemProvider</span></span>  
  
|<span data-ttu-id="9b562-116">必需的成员</span><span class="sxs-lookup"><span data-stu-id="9b562-116">Required member</span></span>|<span data-ttu-id="9b562-117">成员类型</span><span class="sxs-lookup"><span data-stu-id="9b562-117">Member type</span></span>|<span data-ttu-id="9b562-118">说明</span><span class="sxs-lookup"><span data-stu-id="9b562-118">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|<span data-ttu-id="9b562-119">方法</span><span class="sxs-lookup"><span data-stu-id="9b562-119">Method</span></span>|<span data-ttu-id="9b562-120">无</span><span class="sxs-lookup"><span data-stu-id="9b562-120">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|<span data-ttu-id="9b562-121">方法</span><span class="sxs-lookup"><span data-stu-id="9b562-121">Method</span></span>|<span data-ttu-id="9b562-122">无</span><span class="sxs-lookup"><span data-stu-id="9b562-122">None</span></span>|  
  
 <span data-ttu-id="9b562-123">没有与此控件模式关联的属性或事件。</span><span class="sxs-lookup"><span data-stu-id="9b562-123">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="9b562-124">例外</span><span class="sxs-lookup"><span data-stu-id="9b562-124">Exceptions</span></span>  
 <span data-ttu-id="9b562-125">没有与此控件模式关联的异常。</span><span class="sxs-lookup"><span data-stu-id="9b562-125">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b562-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9b562-126">See also</span></span>

- [<span data-ttu-id="9b562-127">UI 自动化控件模式概述</span><span class="sxs-lookup"><span data-stu-id="9b562-127">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="9b562-128">在 UI 自动化提供程序中支持控件模式</span><span class="sxs-lookup"><span data-stu-id="9b562-128">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="9b562-129">客户端的 UI 自动化控件模式</span><span class="sxs-lookup"><span data-stu-id="9b562-129">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="9b562-130">实现 UI 自动化 Table 控件模式</span><span class="sxs-lookup"><span data-stu-id="9b562-130">Implementing the UI Automation Table Control Pattern</span></span>](implementing-the-ui-automation-table-control-pattern.md)
- [<span data-ttu-id="9b562-131">实现 UI 自动化 GridItem 控件模式</span><span class="sxs-lookup"><span data-stu-id="9b562-131">Implementing the UI Automation GridItem Control Pattern</span></span>](implementing-the-ui-automation-griditem-control-pattern.md)
- [<span data-ttu-id="9b562-132">UI 自动化树概述</span><span class="sxs-lookup"><span data-stu-id="9b562-132">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="9b562-133">在 UI 自动化中使用缓存</span><span class="sxs-lookup"><span data-stu-id="9b562-133">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)

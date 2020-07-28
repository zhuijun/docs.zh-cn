---
title: 实现 UI 自动化 Table 控件模式
description: 在 UI 自动化中查看实现 Table 控件模式的准则和约定。 了解 ITableProvider 接口的必需成员。
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
ms.openlocfilehash: e88ddee04ba887daf1929d855526cd0d062f78d5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168240"
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a><span data-ttu-id="25971-104">实现 UI 自动化 Table 控件模式</span><span class="sxs-lookup"><span data-stu-id="25971-104">Implementing the UI Automation Table Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="25971-105">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="25971-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="25971-106">有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="25971-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="25971-107">本主题介绍实现 <xref:System.Windows.Automation.Provider.ITableProvider>的准则和约定，包括有关属性、方法和事件的信息。</span><span class="sxs-lookup"><span data-stu-id="25971-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="25971-108">本概述的结尾列出了指向其他参考资料的链接。</span><span class="sxs-lookup"><span data-stu-id="25971-108">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="25971-109"><xref:System.Windows.Automation.TablePattern> 控件模式用于支持作为子元素集合的容器的控件。</span><span class="sxs-lookup"><span data-stu-id="25971-109">The <xref:System.Windows.Automation.TablePattern> control pattern is used to support controls that act as containers for a collection of child elements.</span></span> <span data-ttu-id="25971-110">此元素的子元素必须实现 <xref:System.Windows.Automation.Provider.ITableItemProvider> ，并且在可以按行和列进行遍历的二维逻辑坐标系统中进行组织。</span><span class="sxs-lookup"><span data-stu-id="25971-110">The children of this element must implement <xref:System.Windows.Automation.Provider.ITableItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column.</span></span> <span data-ttu-id="25971-111">此控件模式类似于 <xref:System.Windows.Automation.Provider.IGridProvider>，区别在于任何实现 <xref:System.Windows.Automation.Provider.ITableProvider> 的控件都还必须公开每个子元素的列和/或行标头关系。</span><span class="sxs-lookup"><span data-stu-id="25971-111">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridProvider>, with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableProvider> must also expose a column and/or row header relationship for each child element.</span></span> <span data-ttu-id="25971-112">有关实现此控件模式的控件示例，请参阅 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="25971-112">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="25971-113">实现准则和约定</span><span class="sxs-lookup"><span data-stu-id="25971-113">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="25971-114">在实现 Table 控件模式时，请注意以下准则和约定：</span><span class="sxs-lookup"><span data-stu-id="25971-114">When implementing the Table control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="25971-115">对个别单元格的内容的访问是通过二维逻辑坐标系统或由所需的 <xref:System.Windows.Automation.Provider.IGridProvider> 的并发实现提供的数组来实现。</span><span class="sxs-lookup"><span data-stu-id="25971-115">Access to the content of individual cells is through a two-dimensional logical coordinate system or array provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span>  
  
- <span data-ttu-id="25971-116">列或行标头可包含在表对象中或可以为与表对象相关联的单独标头对象。</span><span class="sxs-lookup"><span data-stu-id="25971-116">A column or row header can be contained within a table object or be a separate header object that is associated with a table object.</span></span>  
  
- <span data-ttu-id="25971-117">列和行标头可能包含主标头以及任何支持的标头。</span><span class="sxs-lookup"><span data-stu-id="25971-117">Column and row headers may include both a primary header as well as any supporting headers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="25971-118">在 Microsoft Excel 电子表格中，此概念在用户定义了 "First name" 列的情况下变得明显。</span><span class="sxs-lookup"><span data-stu-id="25971-118">This concept becomes evident in a Microsoft Excel spreadsheet where a user has defined a "First name" column.</span></span> <span data-ttu-id="25971-119">此列现在有两个标头 — 用户定义的“名字”标头和应用程序分配的该列的字母数字名称。</span><span class="sxs-lookup"><span data-stu-id="25971-119">This column now has two headers—the "First name" header defined by the user and the alphanumeric designation for that column assigned by the application.</span></span>  
  
- <span data-ttu-id="25971-120">有关相关网格功能，请参阅[实现 UI 自动化网格控件模式](implementing-the-ui-automation-grid-control-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="25971-120">See [Implementing the UI Automation Grid Control Pattern](implementing-the-ui-automation-grid-control-pattern.md) for related grid functionality.</span></span>  
  
 <span data-ttu-id="25971-121">![具有复杂标题项的表。](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span><span class="sxs-lookup"><span data-stu-id="25971-121">![Table with complex header items.](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span></span>  
<span data-ttu-id="25971-122">具有复杂列标头的表示例</span><span class="sxs-lookup"><span data-stu-id="25971-122">Example of a Table with Complex Column Headers</span></span>  
  
 <span data-ttu-id="25971-123">![具有不明确的 RowOrColumnMajor 属性的表。](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span><span class="sxs-lookup"><span data-stu-id="25971-123">![Table with ambiguous RowOrColumnMajor property.](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span></span>  
<span data-ttu-id="25971-124">具有不明确的 RowOrColumnMajor 属性的表示例。</span><span class="sxs-lookup"><span data-stu-id="25971-124">Example of a Table with Ambiguous RowOrColumnMajor Property</span></span>  
  
<a name="Required_Members_for_ITableProvider"></a>
## <a name="required-members-for-itableprovider"></a><span data-ttu-id="25971-125">ITableProvider 必需的成员</span><span class="sxs-lookup"><span data-stu-id="25971-125">Required Members for ITableProvider</span></span>  
 <span data-ttu-id="25971-126">ITableProvider 接口需要以下属性和方法。</span><span class="sxs-lookup"><span data-stu-id="25971-126">The following properties and methods are required for the ITableProvider interface.</span></span>  
  
|<span data-ttu-id="25971-127">必需的成员</span><span class="sxs-lookup"><span data-stu-id="25971-127">Required members</span></span>|<span data-ttu-id="25971-128">成员类型</span><span class="sxs-lookup"><span data-stu-id="25971-128">Member type</span></span>|<span data-ttu-id="25971-129">说明</span><span class="sxs-lookup"><span data-stu-id="25971-129">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|<span data-ttu-id="25971-130">Property</span><span class="sxs-lookup"><span data-stu-id="25971-130">Property</span></span>|<span data-ttu-id="25971-131">无</span><span class="sxs-lookup"><span data-stu-id="25971-131">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|<span data-ttu-id="25971-132">方法</span><span class="sxs-lookup"><span data-stu-id="25971-132">Method</span></span>|<span data-ttu-id="25971-133">无</span><span class="sxs-lookup"><span data-stu-id="25971-133">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|<span data-ttu-id="25971-134">方法</span><span class="sxs-lookup"><span data-stu-id="25971-134">Method</span></span>|<span data-ttu-id="25971-135">无</span><span class="sxs-lookup"><span data-stu-id="25971-135">None</span></span>|  
  
 <span data-ttu-id="25971-136">没有与此控件模式关联的事件。</span><span class="sxs-lookup"><span data-stu-id="25971-136">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="25971-137">例外</span><span class="sxs-lookup"><span data-stu-id="25971-137">Exceptions</span></span>  
 <span data-ttu-id="25971-138">没有与此控件模式关联的异常。</span><span class="sxs-lookup"><span data-stu-id="25971-138">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25971-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="25971-139">See also</span></span>

- [<span data-ttu-id="25971-140">UI 自动化控件模式概述</span><span class="sxs-lookup"><span data-stu-id="25971-140">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="25971-141">在 UI 自动化提供程序中支持控件模式</span><span class="sxs-lookup"><span data-stu-id="25971-141">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="25971-142">客户端的 UI 自动化控件模式</span><span class="sxs-lookup"><span data-stu-id="25971-142">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="25971-143">实现 UI 自动化 TableItem 控件模式</span><span class="sxs-lookup"><span data-stu-id="25971-143">Implementing the UI Automation TableItem Control Pattern</span></span>](implementing-the-ui-automation-tableitem-control-pattern.md)
- [<span data-ttu-id="25971-144">实现 UI 自动化 Grid 控件模式</span><span class="sxs-lookup"><span data-stu-id="25971-144">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="25971-145">UI 自动化树概述</span><span class="sxs-lookup"><span data-stu-id="25971-145">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="25971-146">在 UI 自动化中使用缓存</span><span class="sxs-lookup"><span data-stu-id="25971-146">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)

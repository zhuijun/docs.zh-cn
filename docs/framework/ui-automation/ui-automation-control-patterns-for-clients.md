---
title: 客户端的 UI 自动化控件模式
description: 阅读有关 UI 自动化客户端的控件模式的概述。 使用控件模式来访问有关用户界面（UI）的信息。
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control patterns for clients
- control patterns, UI Automation clients
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
ms.openlocfilehash: f2def328228a30ace6d0edc0661d6e79f237d6f4
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163868"
---
# <a name="ui-automation-control-patterns-for-clients"></a><span data-ttu-id="bb26e-104">客户端的 UI 自动化控件模式</span><span class="sxs-lookup"><span data-stu-id="bb26e-104">UI Automation Control Patterns for Clients</span></span>
> [!NOTE]
> <span data-ttu-id="bb26e-105">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="bb26e-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="bb26e-106">有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="bb26e-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="bb26e-107">此概述介绍 UI 自动化客户端的控件模式。</span><span class="sxs-lookup"><span data-stu-id="bb26e-107">This overview introduces control patterns for UI Automation clients.</span></span> <span data-ttu-id="bb26e-108">它包括有关 UI 自动化客户端如何使用控件模式访问 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]相关信息的信息。</span><span class="sxs-lookup"><span data-stu-id="bb26e-108">It includes information on how a UI Automation client can use control patterns to access information about the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="bb26e-109">控件模式提供了一种方法，用于独立于控件类型或控件的外观对控件的功能进行分类和公开。</span><span class="sxs-lookup"><span data-stu-id="bb26e-109">Control patterns provide a way to categorize and expose a control's functionality independent of the control type or the appearance of the control.</span></span> <span data-ttu-id="bb26e-110">UI 自动化客户端可以检查 <xref:System.Windows.Automation.AutomationElement> 以确定哪些控件模式受支持并确保控件的行为。</span><span class="sxs-lookup"><span data-stu-id="bb26e-110">UI Automation clients can examine an <xref:System.Windows.Automation.AutomationElement> to determine which control patterns are supported and be assured of the behavior of the control.</span></span>  
  
 <span data-ttu-id="bb26e-111">有关控件模式的完整列表，请参阅 [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="bb26e-111">For a complete list of control patterns, see [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md).</span></span>  
  
<a name="uiautomation_getting_control_patterns"></a>
## <a name="getting-control-patterns"></a><span data-ttu-id="bb26e-112">获取控件模式</span><span class="sxs-lookup"><span data-stu-id="bb26e-112">Getting Control Patterns</span></span>  
 <span data-ttu-id="bb26e-113">客户端通过调用 <xref:System.Windows.Automation.AutomationElement> 或 <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> 从 <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>检索控件模式。</span><span class="sxs-lookup"><span data-stu-id="bb26e-113">Clients retrieve a control pattern from an <xref:System.Windows.Automation.AutomationElement> by calling either <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> or <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="bb26e-114">客户端可以使用 <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> 方法或单个 `IsPatternAvailable` 属性（例如 <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>）来确定一个模式或一组模式是否在 <xref:System.Windows.Automation.AutomationElement>上受支持。</span><span class="sxs-lookup"><span data-stu-id="bb26e-114">Clients can use the <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> method or an individual `IsPatternAvailable` property (for example, <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>) to determine if a pattern or group of patterns is supported on the <xref:System.Windows.Automation.AutomationElement>.</span></span> <span data-ttu-id="bb26e-115">但是，尝试获取控件模式并针对 `null` 引用进行测试比检查支持的属性并检索控件模式更高效，因为这样进行的跨进程调用更少。</span><span class="sxs-lookup"><span data-stu-id="bb26e-115">However, it is more efficient to attempt to get the control pattern and test for a `null` reference than to check the supported properties and retrieve the control pattern since it results in fewer cross-process calls.</span></span>  
  
 <span data-ttu-id="bb26e-116">以下示例演示如何从 <xref:System.Windows.Automation.TextPattern> 获取 <xref:System.Windows.Automation.AutomationElement>控件模式。</span><span class="sxs-lookup"><span data-stu-id="bb26e-116">The following example demonstrates how to get a <xref:System.Windows.Automation.TextPattern> control pattern from an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>
## <a name="retrieving-properties-on-control-patterns"></a><span data-ttu-id="bb26e-117">检索控件模式上的属性</span><span class="sxs-lookup"><span data-stu-id="bb26e-117">Retrieving Properties on Control Patterns</span></span>  
 <span data-ttu-id="bb26e-118">客户端可以通过调用 <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> 或 <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> 并将返回的对象强制转换为适当类型，来检索控件模式上的属性值。</span><span class="sxs-lookup"><span data-stu-id="bb26e-118">Clients can retrieve the property values on control patterns by calling either <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> or <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> and casting the object returned to an appropriate type.</span></span> <span data-ttu-id="bb26e-119">有关属性的详细信息 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ，请参阅[客户端的 UI 自动化属性](ui-automation-properties-for-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="bb26e-119">For more information on [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] properties, see [UI Automation Properties for Clients](ui-automation-properties-for-clients.md).</span></span>  
  
 <span data-ttu-id="bb26e-120">除了 `GetPropertyValue` 方法之外，还可以通过公共语言运行时（CLR）访问器检索属性值以访问 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 模式上的属性。</span><span class="sxs-lookup"><span data-stu-id="bb26e-120">In addition to the `GetPropertyValue` methods, property values can be retrieved through the common language runtime (CLR) accessors to access the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] properties on a pattern.</span></span>  
  
<a name="uiautomation_with_variable_patterns"></a>
## <a name="controls-with-variable-patterns"></a><span data-ttu-id="bb26e-121">具有可变模式的控件</span><span class="sxs-lookup"><span data-stu-id="bb26e-121">Controls with Variable Patterns</span></span>  
 <span data-ttu-id="bb26e-122">某些控件类型支持不同的模式，具体取决于它们的状态或使用控件的方式。</span><span class="sxs-lookup"><span data-stu-id="bb26e-122">Some control types support different patterns depending on their state or the manner in which the control is being used.</span></span> <span data-ttu-id="bb26e-123">可以具有可变模式的控件示例包括列表视图（缩略图、磁贴、图标、列表、详细信息）、Microsoft Excel 图表（饼图、折线图、条形图、带有公式的单元值）、Microsoft Word 的文档区域（正常、Web 版式、大纲、打印布局、打印预览）和 Microsoft Windows Media Player 外观。</span><span class="sxs-lookup"><span data-stu-id="bb26e-123">Examples of controls that can have variable patterns are list views (thumbnails, tiles, icons, list, details), Microsoft Excel Charts (Pie, Line, Bar, Cell Value with a formula), Microsoft Word's document area (Normal, Web Layout, Outline, Print Layout, Print Preview), and Microsoft Windows Media Player skins.</span></span>  
  
 <span data-ttu-id="bb26e-124">实现自定义控件类型的控件可以具有表示其功能所需的任何控件模式集。</span><span class="sxs-lookup"><span data-stu-id="bb26e-124">Controls implementing custom control types can have any set of control patterns that are needed to represent their functionality.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb26e-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="bb26e-125">See also</span></span>

- [<span data-ttu-id="bb26e-126">UI 自动化控件模式</span><span class="sxs-lookup"><span data-stu-id="bb26e-126">UI Automation Control Patterns</span></span>](ui-automation-control-patterns.md)
- [<span data-ttu-id="bb26e-127">UI 自动化文本模式</span><span class="sxs-lookup"><span data-stu-id="bb26e-127">UI Automation Text Pattern</span></span>](ui-automation-text-pattern.md)
- [<span data-ttu-id="bb26e-128">使用 UI 自动化调用控件</span><span class="sxs-lookup"><span data-stu-id="bb26e-128">Invoke a Control Using UI Automation</span></span>](invoke-a-control-using-ui-automation.md)
- [<span data-ttu-id="bb26e-129">使用 UI 自动化获取复选框的切换状态</span><span class="sxs-lookup"><span data-stu-id="bb26e-129">Get the Toggle State of a Check Box Using UI Automation</span></span>](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [<span data-ttu-id="bb26e-130">UI 自动化客户端的控件模式映射</span><span class="sxs-lookup"><span data-stu-id="bb26e-130">Control Pattern Mapping for UI Automation Clients</span></span>](control-pattern-mapping-for-ui-automation-clients.md)
- [<span data-ttu-id="bb26e-131">TextPattern 插入文本示例</span><span class="sxs-lookup"><span data-stu-id="bb26e-131">TextPattern Insert Text Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [<span data-ttu-id="bb26e-132">TextPattern 搜索和选择示例</span><span class="sxs-lookup"><span data-stu-id="bb26e-132">TextPattern Search and Selection Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FindText)
- [<span data-ttu-id="bb26e-133">InvokePattern、ExpandCollapsePattern 和 TogglePattern 示例</span><span class="sxs-lookup"><span data-stu-id="bb26e-133">InvokePattern, ExpandCollapsePattern, and TogglePattern Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)

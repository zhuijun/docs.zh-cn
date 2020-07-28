---
title: 实现 UI 自动化 ExpandCollapse 控件模式
description: 了解 UI 自动化中 ExpandCollapse 控件模式的实现准则和约定。 知道如何实现 Iexpandcollapseprovider 必需。
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, ExpandCollapse control pattern
- ExpandCollapse control pattern
- control patterns, ExpandCollapse
ms.assetid: 1dbabb8c-0d68-47c1-a35e-1c01cb01af26
ms.openlocfilehash: 525b57816071ba2d879036676201a0506d1a29db
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165858"
---
# <a name="implementing-the-ui-automation-expandcollapse-control-pattern"></a><span data-ttu-id="c2987-104">实现 UI 自动化 ExpandCollapse 控件模式</span><span class="sxs-lookup"><span data-stu-id="c2987-104">Implementing the UI Automation ExpandCollapse Control Pattern</span></span>

> [!NOTE]
> <span data-ttu-id="c2987-105">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="c2987-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="c2987-106">有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="c2987-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>

<span data-ttu-id="c2987-107">本主题介绍实现 <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>的准则和约定，包括有关属性、方法和事件的信息。</span><span class="sxs-lookup"><span data-stu-id="c2987-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="c2987-108">本概述的结尾列出了指向其他参考资料的链接。</span><span class="sxs-lookup"><span data-stu-id="c2987-108">Links to additional references are listed at the end of the overview.</span></span>

<span data-ttu-id="c2987-109"><xref:System.Windows.Automation.ExpandCollapsePattern> 控件模式用于支持以可视化方式展开来显示更多内容或者以可视化方式折叠来隐藏相关内容的控件。</span><span class="sxs-lookup"><span data-stu-id="c2987-109">The <xref:System.Windows.Automation.ExpandCollapsePattern> control pattern is used to support controls that visually expand to display more content and collapse to hide content.</span></span> <span data-ttu-id="c2987-110">有关实现此控件模式的控件示例，请参阅 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="c2987-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>

<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="c2987-111">实现准则和约定</span><span class="sxs-lookup"><span data-stu-id="c2987-111">Implementation Guidelines and Conventions</span></span>

<span data-ttu-id="c2987-112">在实现 ExpandCollapse 控件模式时，请注意以下准则和约定：</span><span class="sxs-lookup"><span data-stu-id="c2987-112">When implementing the ExpandCollapse control pattern, note the following guidelines and conventions:</span></span>

- <span data-ttu-id="c2987-113">聚合控件（通过一些子对象生成，这些子对象提供具有展开/折叠功能的 UI）必须支持 <xref:System.Windows.Automation.ExpandCollapsePattern> 控件模式，而它们的子元素不必支持。</span><span class="sxs-lookup"><span data-stu-id="c2987-113">Aggregate controls—built with child objects that provide the UI with expand/collapse functionality—must support the <xref:System.Windows.Automation.ExpandCollapsePattern> control pattern whereas their child elements do not.</span></span> <span data-ttu-id="c2987-114">例如，组合框控件是由列表框、按钮和编辑控件组合而成的，但它是唯一一个必须支持 <xref:System.Windows.Automation.ExpandCollapsePattern>的父组合框。</span><span class="sxs-lookup"><span data-stu-id="c2987-114">For example, a combo box control is built with a combination of list box, button, and edit controls, but it is only the parent combo box that must support the <xref:System.Windows.Automation.ExpandCollapsePattern>.</span></span>

  > [!NOTE]
  > <span data-ttu-id="c2987-115">菜单控件是一个例外，它是对各个 MenuItem 对象的聚合。</span><span class="sxs-lookup"><span data-stu-id="c2987-115">An exception is the menu control, which is an aggregate of individual MenuItem objects.</span></span> <span data-ttu-id="c2987-116">MenuItem 对象可以支持 <xref:System.Windows.Automation.ExpandCollapsePattern> 控件模式，但是父 Menu 控件无法支持。</span><span class="sxs-lookup"><span data-stu-id="c2987-116">The MenuItem objects can support the <xref:System.Windows.Automation.ExpandCollapsePattern> control pattern, but the parent Menu control cannot.</span></span> <span data-ttu-id="c2987-117">Tree 和 Tree Item 控件也存在类似的例外。</span><span class="sxs-lookup"><span data-stu-id="c2987-117">A similar exception applies to the Tree and Tree Item controls.</span></span>

- <span data-ttu-id="c2987-118">将某个控件的 <xref:System.Windows.Automation.ExpandCollapseState> 设置为 <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>后，该控件的所有 <xref:System.Windows.Automation.ExpandCollapsePattern> 功能当前都处于非活动状态，通过该控件模式可以获取的唯一信息就是 <xref:System.Windows.Automation.ExpandCollapseState>。</span><span class="sxs-lookup"><span data-stu-id="c2987-118">When the <xref:System.Windows.Automation.ExpandCollapseState> of a control is set to <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>, any <xref:System.Windows.Automation.ExpandCollapsePattern> functionality is currently inactive for the control and the only information that can be obtained using this control pattern is the <xref:System.Windows.Automation.ExpandCollapseState>.</span></span> <span data-ttu-id="c2987-119">如果以后添加任何子对象，则 <xref:System.Windows.Automation.ExpandCollapseState> 会发生更改，同时 <xref:System.Windows.Automation.ExpandCollapsePattern> 功能将被激活。</span><span class="sxs-lookup"><span data-stu-id="c2987-119">If any child objects are subsequently added, the <xref:System.Windows.Automation.ExpandCollapseState> changes and <xref:System.Windows.Automation.ExpandCollapsePattern> functionality is activated.</span></span>

- <span data-ttu-id="c2987-120"><xref:System.Windows.Automation.ExpandCollapseState> 仅表示直接子对象的可见性，而不表示所有后代对象的可见性。</span><span class="sxs-lookup"><span data-stu-id="c2987-120"><xref:System.Windows.Automation.ExpandCollapseState> refers to the visibility of immediate child objects only; it does not refer to the visibility of all descendant objects.</span></span>

- <span data-ttu-id="c2987-121">展开和折叠功能是特定于控件的。</span><span class="sxs-lookup"><span data-stu-id="c2987-121">Expand and Collapse functionality is control-specific.</span></span> <span data-ttu-id="c2987-122">下面是该行为的示例。</span><span class="sxs-lookup"><span data-stu-id="c2987-122">The following are examples of this behavior.</span></span>

  - <span data-ttu-id="c2987-123">Office Personal Menu 可以是具有三种状态（<xref:System.Windows.Automation.ExpandCollapseState.Expanded>、 <xref:System.Windows.Automation.ExpandCollapseState.Collapsed> 和 <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>）的 MenuItem，该 MenuItem 中的控件指定在调用 <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> 或 <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> 时要采用的状态。</span><span class="sxs-lookup"><span data-stu-id="c2987-123">The Office Personal Menu can be a tri-state MenuItem (<xref:System.Windows.Automation.ExpandCollapseState.Expanded>, <xref:System.Windows.Automation.ExpandCollapseState.Collapsed> and <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>) where the control specifies the state to adopt when an <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> or <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> is called.</span></span>

  - <span data-ttu-id="c2987-124">对 TreeItem 调用 <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> 可能会显示所有后代，也可能仅显示直接子级。</span><span class="sxs-lookup"><span data-stu-id="c2987-124">Calling <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> on a TreeItem may display all descendants or only immediate children.</span></span>

  - <span data-ttu-id="c2987-125">如果对某个控件调用 <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> 或 <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> 以保持该控件的后代的状态，则应当发送可见性更改事件，而不是状态更改事件。如果折叠父控件无法保持该控件的后代的状态，则该控件可能会销毁所有不再可见的后代并引发一个销毁事件，也可能会更改每个后代的 <xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A> 并引发一个可见性更改事件。</span><span class="sxs-lookup"><span data-stu-id="c2987-125">If calling <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> or <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> on a control maintains the state of its descendants, a visibility change event should be sent, not a state change event If the parent control does not maintain the state of its descendants when collapsed, the control may destroy all the descendants that are no longer visible and raise a destroyed event; or it may change the <xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A> for each descendant and raise a visibility change event.</span></span>

- <span data-ttu-id="c2987-126">为保证导航操作，最好让对象保留在具有相应可见性状态的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 树中，而不管其父级的 <xref:System.Windows.Automation.ExpandCollapseState>如何。</span><span class="sxs-lookup"><span data-stu-id="c2987-126">To guarantee navigation, it is desirable for an object to be in the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree (with appropriate visibility state) regardless of its parents <xref:System.Windows.Automation.ExpandCollapseState>.</span></span> <span data-ttu-id="c2987-127">如果后代是按需生成的，那么，仅当它们在首次显示之后或者可见时，才能出现在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 树中。</span><span class="sxs-lookup"><span data-stu-id="c2987-127">If descendants are generated on demand, they may only appear in the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree after being displayed for the first time or only while they are visible.</span></span>

<a name="Required_Members_for_the_IValueProvider_Interface"></a>

## <a name="required-members-for-iexpandcollapseprovider"></a><span data-ttu-id="c2987-128">IExpandCollapseProvider 必需的成员</span><span class="sxs-lookup"><span data-stu-id="c2987-128">Required Members for IExpandCollapseProvider</span></span>

<span data-ttu-id="c2987-129">实现 <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>需要以下属性和方法。</span><span class="sxs-lookup"><span data-stu-id="c2987-129">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>.</span></span>

|<span data-ttu-id="c2987-130">必需的成员</span><span class="sxs-lookup"><span data-stu-id="c2987-130">Required members</span></span>|<span data-ttu-id="c2987-131">成员类型</span><span class="sxs-lookup"><span data-stu-id="c2987-131">Member type</span></span>|<span data-ttu-id="c2987-132">说明</span><span class="sxs-lookup"><span data-stu-id="c2987-132">Notes</span></span>|
|----------------------|-----------------|-----------|
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A>|<span data-ttu-id="c2987-133">Property</span><span class="sxs-lookup"><span data-stu-id="c2987-133">Property</span></span>|<span data-ttu-id="c2987-134">无</span><span class="sxs-lookup"><span data-stu-id="c2987-134">None</span></span>|
|<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A>|<span data-ttu-id="c2987-135">方法</span><span class="sxs-lookup"><span data-stu-id="c2987-135">Method</span></span>|<span data-ttu-id="c2987-136">无</span><span class="sxs-lookup"><span data-stu-id="c2987-136">None</span></span>|
|<xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A>|<span data-ttu-id="c2987-137">方法</span><span class="sxs-lookup"><span data-stu-id="c2987-137">Method</span></span>|<span data-ttu-id="c2987-138">无</span><span class="sxs-lookup"><span data-stu-id="c2987-138">None</span></span>|
|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|<span data-ttu-id="c2987-139">事件</span><span class="sxs-lookup"><span data-stu-id="c2987-139">Event</span></span>|<span data-ttu-id="c2987-140">此控件没有关联的事件；请使用此泛型委托。</span><span class="sxs-lookup"><span data-stu-id="c2987-140">This control has no associated events; use this generic delegate.</span></span>|

<a name="Exceptions"></a>

## <a name="exceptions"></a><span data-ttu-id="c2987-141">例外</span><span class="sxs-lookup"><span data-stu-id="c2987-141">Exceptions</span></span>

<span data-ttu-id="c2987-142">提供程序必须引发以下异常。</span><span class="sxs-lookup"><span data-stu-id="c2987-142">Providers must throw the following exceptions.</span></span>

|<span data-ttu-id="c2987-143">例外类型</span><span class="sxs-lookup"><span data-stu-id="c2987-143">Exception type</span></span>|<span data-ttu-id="c2987-144">条件</span><span class="sxs-lookup"><span data-stu-id="c2987-144">Condition</span></span>|
|--------------------|---------------|
|<xref:System.InvalidOperationException>|<span data-ttu-id="c2987-145">当 <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> 或 <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> 时，将调用 <xref:System.Windows.Automation.ExpandCollapseState> = <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>。</span><span class="sxs-lookup"><span data-stu-id="c2987-145">Either <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> or <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> is called when the <xref:System.Windows.Automation.ExpandCollapseState> = <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>.</span></span>|

## <a name="see-also"></a><span data-ttu-id="c2987-146">请参阅</span><span class="sxs-lookup"><span data-stu-id="c2987-146">See also</span></span>

- [<span data-ttu-id="c2987-147">UI 自动化控件模式概述</span><span class="sxs-lookup"><span data-stu-id="c2987-147">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="c2987-148">在 UI 自动化提供程序中支持控件模式</span><span class="sxs-lookup"><span data-stu-id="c2987-148">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="c2987-149">客户端的 UI 自动化控件模式</span><span class="sxs-lookup"><span data-stu-id="c2987-149">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="c2987-150">使用 TreeWalker 在 UI 自动化元素之间导航</span><span class="sxs-lookup"><span data-stu-id="c2987-150">Navigate Among UI Automation Elements with TreeWalker</span></span>](navigate-among-ui-automation-elements-with-treewalker.md)
- [<span data-ttu-id="c2987-151">UI 自动化树概述</span><span class="sxs-lookup"><span data-stu-id="c2987-151">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="c2987-152">在 UI 自动化中使用缓存</span><span class="sxs-lookup"><span data-stu-id="c2987-152">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)

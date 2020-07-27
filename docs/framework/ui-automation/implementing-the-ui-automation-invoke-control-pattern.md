---
title: 实现 UI 自动化 Invoke 控件模式
description: 阅读准则和约定，以实现 UI 自动化中的 Invoke 控件模式。 请参阅 Iinvokeprovider 必需接口的必需成员。
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Invoke control pattern
- control patterns, Invoke
- Invoke control pattern
ms.assetid: e5b1e239-49f8-468e-bfec-1fba02ec9ac4
ms.openlocfilehash: b464b3ab5cd2b0789798f8b865b946c5eae017eb
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166171"
---
# <a name="implementing-the-ui-automation-invoke-control-pattern"></a><span data-ttu-id="f87f2-104">实现 UI 自动化 Invoke 控件模式</span><span class="sxs-lookup"><span data-stu-id="f87f2-104">Implementing the UI Automation Invoke Control Pattern</span></span>

> [!NOTE]
> <span data-ttu-id="f87f2-105">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="f87f2-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="f87f2-106">有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="f87f2-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>

<span data-ttu-id="f87f2-107">本主题介绍了实现 <xref:System.Windows.Automation.Provider.IInvokeProvider>的准则和约定，包括有关事件和属性的信息。</span><span class="sxs-lookup"><span data-stu-id="f87f2-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IInvokeProvider>, including information about events and properties.</span></span> <span data-ttu-id="f87f2-108">本主题的结尾列出了指向其他参考资料的链接。</span><span class="sxs-lookup"><span data-stu-id="f87f2-108">Links to additional references are listed at the end of the topic.</span></span>

<span data-ttu-id="f87f2-109"><xref:System.Windows.Automation.InvokePattern> 控件模式用于支持激活时不维护状态而是启动或执行单个明确操作的控件。</span><span class="sxs-lookup"><span data-stu-id="f87f2-109">The <xref:System.Windows.Automation.InvokePattern> control pattern is used to support controls that do not maintain state when activated but rather initiate or perform a single, unambiguous action.</span></span> <span data-ttu-id="f87f2-110">维护状态的控件（如复选框和单选按钮）则是必须分别实现 <xref:System.Windows.Automation.Provider.IToggleProvider> 和 <xref:System.Windows.Automation.Provider.ISelectionItemProvider> 。</span><span class="sxs-lookup"><span data-stu-id="f87f2-110">Controls that do maintain state, such as check boxes and radio buttons, must instead implement <xref:System.Windows.Automation.Provider.IToggleProvider> and <xref:System.Windows.Automation.Provider.ISelectionItemProvider> respectively.</span></span> <span data-ttu-id="f87f2-111">有关实现此 Invoke 控件模式的控件的示例，请参阅 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="f87f2-111">For examples of controls that implement the Invoke control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>

<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="f87f2-112">实现准则和约定</span><span class="sxs-lookup"><span data-stu-id="f87f2-112">Implementation Guidelines and Conventions</span></span>

<span data-ttu-id="f87f2-113">在实现 Invoke 控件模式时，请注意以下准则和约定：</span><span class="sxs-lookup"><span data-stu-id="f87f2-113">When implementing the Invoke control pattern, note the following guidelines and conventions:</span></span>

- <span data-ttu-id="f87f2-114">如果不通过另一个控件模式提供程序公开同一行为，则控件实现 <xref:System.Windows.Automation.Provider.IInvokeProvider> 。</span><span class="sxs-lookup"><span data-stu-id="f87f2-114">Controls implement <xref:System.Windows.Automation.Provider.IInvokeProvider> if the same behavior is not exposed through another control pattern provider.</span></span> <span data-ttu-id="f87f2-115">例如，如果控件上的 <xref:System.Windows.Automation.InvokePattern.Invoke%2A> 方法与 <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> 方法或 <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> 方法执行同一操作，则控件不应实现 <xref:System.Windows.Automation.Provider.IInvokeProvider>。</span><span class="sxs-lookup"><span data-stu-id="f87f2-115">For example, if the <xref:System.Windows.Automation.InvokePattern.Invoke%2A> method on a control performs the same action as the <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> or <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> method, the control should not implement <xref:System.Windows.Automation.Provider.IInvokeProvider>.</span></span>

- <span data-ttu-id="f87f2-116">通常通过单击或双击或按 ENTER、预定义的键盘快捷键或某种备用的击键组合来调用控件。</span><span class="sxs-lookup"><span data-stu-id="f87f2-116">Invoking a control is generally performed by clicking or double-clicking or pressing ENTER, a predefined keyboard shortcut, or some alternate combination of keystrokes.</span></span>

- <span data-ttu-id="f87f2-117">在已被激活的控件上引发<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent> （作为对执行关联操作的控件的响应）。</span><span class="sxs-lookup"><span data-stu-id="f87f2-117"><xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent> is raised on a control that has been activated (as a response to a control carrying out its associated action).</span></span> <span data-ttu-id="f87f2-118">如果可能，应在控件完成操作后引发事件且在不阻止的情况下返回事件。</span><span class="sxs-lookup"><span data-stu-id="f87f2-118">If possible, the event should be raised after the control has completed the action and returned without blocking.</span></span> <span data-ttu-id="f87f2-119">在以下情况中，应在服务 Invoke 请求之前引发调用的事件：</span><span class="sxs-lookup"><span data-stu-id="f87f2-119">The Invoked event should be raised before servicing the Invoke request in the following scenarios:</span></span>

  - <span data-ttu-id="f87f2-120">不可能等至操作完成，或这一做法不实际。</span><span class="sxs-lookup"><span data-stu-id="f87f2-120">It is not possible or practical to wait until the action is complete.</span></span>

  - <span data-ttu-id="f87f2-121">该操作需要用户交互。</span><span class="sxs-lookup"><span data-stu-id="f87f2-121">The action requires user interaction.</span></span>

  - <span data-ttu-id="f87f2-122">该操作很耗时并且会导致调用的客户端花费大量的时间进行阻止。</span><span class="sxs-lookup"><span data-stu-id="f87f2-122">The action is time-consuming and will cause the calling client to block for a significant amount of time.</span></span>

- <span data-ttu-id="f87f2-123">如果调用该控件会产生巨大的负面影响，应通过 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A> 属性公开这些副作用。</span><span class="sxs-lookup"><span data-stu-id="f87f2-123">If invoking the control has significant side-effects, those side-effects should be exposed through the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A> property.</span></span> <span data-ttu-id="f87f2-124">例如，即使 <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> 不与所选内容相关联， <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> 也可能会导致另一个控件变为处于选定状态。</span><span class="sxs-lookup"><span data-stu-id="f87f2-124">For example, even though <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> is not associated with selection, <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> may cause another control to become selected.</span></span>

- <span data-ttu-id="f87f2-125">悬停（或鼠标悬停）效果通常不会构成调用的事件。</span><span class="sxs-lookup"><span data-stu-id="f87f2-125">Hover (or mouse-over) effects generally do not constitute an Invoked event.</span></span> <span data-ttu-id="f87f2-126">但是，执行基于悬停状态的操作（而不是导致视觉效果）的控件应支持 <xref:System.Windows.Automation.InvokePattern> 控件模式。</span><span class="sxs-lookup"><span data-stu-id="f87f2-126">However, controls that perform an action (as opposed to cause a visual effect) based on the hover state should support the <xref:System.Windows.Automation.InvokePattern> control pattern.</span></span>

> [!NOTE]
> <span data-ttu-id="f87f2-127">如果该控件仅可作为与鼠标相关的副作用的结果被调用，则此实现被视为可访问性问题。</span><span class="sxs-lookup"><span data-stu-id="f87f2-127">This implementation is considered an accessibility issue if the control can be invoked only as a result of a mouse-related side effect.</span></span>

- <span data-ttu-id="f87f2-128">调用一个控件不同于选择一个项。</span><span class="sxs-lookup"><span data-stu-id="f87f2-128">Invoking a control is different from selecting an item.</span></span> <span data-ttu-id="f87f2-129">但是，具体取决于控件，调用控件可能导致项被选为副作用。</span><span class="sxs-lookup"><span data-stu-id="f87f2-129">However, depending on the control, invoking it may cause the item to become selected as a side-effect.</span></span> <span data-ttu-id="f87f2-130">例如，调用 "我的文档" 文件夹中的 Microsoft Word 文档列表项将选择该项并打开该文档。</span><span class="sxs-lookup"><span data-stu-id="f87f2-130">For example, invoking a Microsoft Word document list item in the My Documents folder both selects the item and opens the document.</span></span>

- <span data-ttu-id="f87f2-131">元素被调用时将立即从 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 树中消失。</span><span class="sxs-lookup"><span data-stu-id="f87f2-131">An element can disappear from the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree immediately upon being invoked.</span></span> <span data-ttu-id="f87f2-132">从由事件回调提供的元素请求信息可能失败。</span><span class="sxs-lookup"><span data-stu-id="f87f2-132">Requesting information from the element provided by the event callback may fail as a result.</span></span> <span data-ttu-id="f87f2-133">建议的解决方法是预取缓存的信息。</span><span class="sxs-lookup"><span data-stu-id="f87f2-133">Pre-fetching cached information is the recommended workaround.</span></span>

- <span data-ttu-id="f87f2-134">控件可实现多个控件模式。</span><span class="sxs-lookup"><span data-stu-id="f87f2-134">Controls can implement multiple control patterns.</span></span> <span data-ttu-id="f87f2-135">例如，Microsoft Excel 工具栏上的 "填充颜色" 控件同时实现 <xref:System.Windows.Automation.InvokePattern> 和 <xref:System.Windows.Automation.ExpandCollapsePattern> 控件模式。</span><span class="sxs-lookup"><span data-stu-id="f87f2-135">For example, the Fill Color control on the Microsoft Excel toolbar implements both the <xref:System.Windows.Automation.InvokePattern> and the <xref:System.Windows.Automation.ExpandCollapsePattern> control patterns.</span></span> <span data-ttu-id="f87f2-136"><xref:System.Windows.Automation.ExpandCollapsePattern> 公开菜单，而 <xref:System.Windows.Automation.InvokePattern> 用所选颜色填充活动选择项。</span><span class="sxs-lookup"><span data-stu-id="f87f2-136"><xref:System.Windows.Automation.ExpandCollapsePattern> exposes the menu and the <xref:System.Windows.Automation.InvokePattern> fills the active selection with the chosen color.</span></span>

<a name="Required_Members_for_the_IValueProvider_Interface"></a>

## <a name="required-members-for-iinvokeprovider"></a><span data-ttu-id="f87f2-137">IInvokeProvider 必需的成员</span><span class="sxs-lookup"><span data-stu-id="f87f2-137">Required Members for IInvokeProvider</span></span>

<span data-ttu-id="f87f2-138">实现 <xref:System.Windows.Automation.Provider.IInvokeProvider>需要以下属性和方法。</span><span class="sxs-lookup"><span data-stu-id="f87f2-138">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IInvokeProvider>.</span></span>

|<span data-ttu-id="f87f2-139">必需的成员</span><span class="sxs-lookup"><span data-stu-id="f87f2-139">Required members</span></span>|<span data-ttu-id="f87f2-140">成员类型</span><span class="sxs-lookup"><span data-stu-id="f87f2-140">Member type</span></span>|<span data-ttu-id="f87f2-141">说明</span><span class="sxs-lookup"><span data-stu-id="f87f2-141">Notes</span></span>|
|----------------------|-----------------|-----------|
|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A>|<span data-ttu-id="f87f2-142">method</span><span class="sxs-lookup"><span data-stu-id="f87f2-142">method</span></span>|<span data-ttu-id="f87f2-143"><xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> 是一个异步调用且必须立即返回而不阻塞。</span><span class="sxs-lookup"><span data-stu-id="f87f2-143"><xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> is an asynchronous call and must return immediately without blocking.</span></span><br /><br /> <span data-ttu-id="f87f2-144">此行为对于被调用时直接或间接启动模式对话框的控件而言尤其重要。</span><span class="sxs-lookup"><span data-stu-id="f87f2-144">This behavior is particularly critical for controls that, directly or indirectly, launch a modal dialog when invoked.</span></span> <span data-ttu-id="f87f2-145">引发该事件的任何 UI 自动化客户端将保持被阻止的状态，直到模式对话框关闭为止。</span><span class="sxs-lookup"><span data-stu-id="f87f2-145">Any UI Automation client that instigated the event will remain blocked until the modal dialog is closed.</span></span>|

<a name="Exceptions"></a>

## <a name="exceptions"></a><span data-ttu-id="f87f2-146">例外</span><span class="sxs-lookup"><span data-stu-id="f87f2-146">Exceptions</span></span>

<span data-ttu-id="f87f2-147">提供程序必须引发以下异常。</span><span class="sxs-lookup"><span data-stu-id="f87f2-147">Providers must throw the following exceptions.</span></span>

|<span data-ttu-id="f87f2-148">异常类型</span><span class="sxs-lookup"><span data-stu-id="f87f2-148">Exception Type</span></span>|<span data-ttu-id="f87f2-149">条件</span><span class="sxs-lookup"><span data-stu-id="f87f2-149">Condition</span></span>|
|--------------------|---------------|
|<xref:System.Windows.Automation.ElementNotEnabledException>|<span data-ttu-id="f87f2-150">如果未启用该控件。</span><span class="sxs-lookup"><span data-stu-id="f87f2-150">If the control is not enabled.</span></span>|

## <a name="see-also"></a><span data-ttu-id="f87f2-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f87f2-151">See also</span></span>

- [<span data-ttu-id="f87f2-152">UI 自动化控件模式概述</span><span class="sxs-lookup"><span data-stu-id="f87f2-152">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="f87f2-153">在 UI 自动化提供程序中支持控件模式</span><span class="sxs-lookup"><span data-stu-id="f87f2-153">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="f87f2-154">客户端的 UI 自动化控件模式</span><span class="sxs-lookup"><span data-stu-id="f87f2-154">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="f87f2-155">使用 UI 自动化调用控件</span><span class="sxs-lookup"><span data-stu-id="f87f2-155">Invoke a Control Using UI Automation</span></span>](invoke-a-control-using-ui-automation.md)
- [<span data-ttu-id="f87f2-156">UI 自动化树概述</span><span class="sxs-lookup"><span data-stu-id="f87f2-156">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="f87f2-157">在 UI 自动化中使用缓存</span><span class="sxs-lookup"><span data-stu-id="f87f2-157">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)

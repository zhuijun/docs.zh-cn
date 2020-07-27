---
title: 实现 UI 自动化 Window 控件模式
description: 查看准则和约定，以在 UI 自动化中实现 Window 控件模式。 了解 IWindowProvider 接口的必需成员。
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
ms.openlocfilehash: e1d7429f86896947a10b73965caa7d771f54490b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168187"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a><span data-ttu-id="a6991-104">实现 UI 自动化 Window 控件模式</span><span class="sxs-lookup"><span data-stu-id="a6991-104">Implementing the UI Automation Window Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="a6991-105">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="a6991-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a6991-106">有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="a6991-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="a6991-107">本主题介绍实现 <xref:System.Windows.Automation.Provider.IWindowProvider>的准则和约定，包括有关 <xref:System.Windows.Automation.WindowPattern> 属性、方法和事件的信息。</span><span class="sxs-lookup"><span data-stu-id="a6991-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IWindowProvider>, including information about <xref:System.Windows.Automation.WindowPattern> properties, methods, and events.</span></span> <span data-ttu-id="a6991-108">本主题的结尾列出了指向其他参考资料的链接。</span><span class="sxs-lookup"><span data-stu-id="a6991-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="a6991-109"><xref:System.Windows.Automation.WindowPattern>控件模式用于支持在传统图形用户界面（GUI）中提供基于窗口的基本功能的控件。</span><span class="sxs-lookup"><span data-stu-id="a6991-109">The <xref:System.Windows.Automation.WindowPattern> control pattern is used to support controls that provide fundamental window-based functionality within a traditional graphical user interface (GUI).</span></span> <span data-ttu-id="a6991-110">必须实现此控件模式的控件示例包括顶级应用程序窗口、多文档界面（MDI）子窗口、大小可调的拆分窗格控件、模式对话框和气球状帮助窗口。</span><span class="sxs-lookup"><span data-stu-id="a6991-110">Examples of controls that must implement this control pattern include top-level application windows, multiple-document interface (MDI) child windows, resizable split pane controls, modal dialogs and balloon help windows.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="a6991-111">实现准则和约定</span><span class="sxs-lookup"><span data-stu-id="a6991-111">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="a6991-112">在实现 Window 控件模式时，请注意以下准则和约定：</span><span class="sxs-lookup"><span data-stu-id="a6991-112">When implementing the Window control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="a6991-113">为了能够使用 UI 自动化同时修改窗口大小和屏幕位置，除了 <xref:System.Windows.Automation.Provider.ITransformProvider> 外，控件还必须实现 <xref:System.Windows.Automation.Provider.IWindowProvider>。</span><span class="sxs-lookup"><span data-stu-id="a6991-113">To support the ability to modify both window size and screen position using UI Automation, a control must implement <xref:System.Windows.Automation.Provider.ITransformProvider> in addition to <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
- <span data-ttu-id="a6991-114">包含标题栏和标题栏元素（使控件能够移动、调整大小、最大化、最小化或关闭）的控件通常需要实现 <xref:System.Windows.Automation.Provider.IWindowProvider>。</span><span class="sxs-lookup"><span data-stu-id="a6991-114">Controls that contain title bars and title bar elements that enable the control to be moved, resized, maximized, minimized, or closed are typically required to implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
- <span data-ttu-id="a6991-115">诸如工具提示弹出窗口以及组合框或下拉菜单之类的控件通常不实现 <xref:System.Windows.Automation.Provider.IWindowProvider>。</span><span class="sxs-lookup"><span data-stu-id="a6991-115">Controls such as tooltip pop-ups and combo box or menu drop-downs do not typically implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
- <span data-ttu-id="a6991-116">气球状帮助窗口和基本工具提示弹出窗口的区别在于是否提供了像窗口一样的“关闭”按钮。</span><span class="sxs-lookup"><span data-stu-id="a6991-116">Balloon help windows are differentiated from basic tooltip pop-ups by the provision of a window-like Close button.</span></span>  
  
- <span data-ttu-id="a6991-117">IWindowProvider 不支持全屏模式，因为它是特定于应用程序的功能，而不是典型的窗口行为。</span><span class="sxs-lookup"><span data-stu-id="a6991-117">Full-screen mode is not supported by IWindowProvider as it is feature-specific to an application and is not typical window behavior.</span></span>  
  
<a name="Required_Members_for_IWindowProvider"></a>
## <a name="required-members-for-iwindowprovider"></a><span data-ttu-id="a6991-118">IWindowProvider 必需的成员</span><span class="sxs-lookup"><span data-stu-id="a6991-118">Required Members for IWindowProvider</span></span>  
 <span data-ttu-id="a6991-119">IWindowProvider 接口需要以下属性、方法和事件。</span><span class="sxs-lookup"><span data-stu-id="a6991-119">The following properties, methods, and events are required for the IWindowProvider interface.</span></span>  
  
|<span data-ttu-id="a6991-120">必需的成员</span><span class="sxs-lookup"><span data-stu-id="a6991-120">Required member</span></span>|<span data-ttu-id="a6991-121">成员类型</span><span class="sxs-lookup"><span data-stu-id="a6991-121">Member type</span></span>|<span data-ttu-id="a6991-122">说明</span><span class="sxs-lookup"><span data-stu-id="a6991-122">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|<span data-ttu-id="a6991-123">属性</span><span class="sxs-lookup"><span data-stu-id="a6991-123">Property</span></span>|<span data-ttu-id="a6991-124">无</span><span class="sxs-lookup"><span data-stu-id="a6991-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|<span data-ttu-id="a6991-125">属性</span><span class="sxs-lookup"><span data-stu-id="a6991-125">Property</span></span>|<span data-ttu-id="a6991-126">无</span><span class="sxs-lookup"><span data-stu-id="a6991-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|<span data-ttu-id="a6991-127">属性</span><span class="sxs-lookup"><span data-stu-id="a6991-127">Property</span></span>|<span data-ttu-id="a6991-128">无</span><span class="sxs-lookup"><span data-stu-id="a6991-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|<span data-ttu-id="a6991-129">属性</span><span class="sxs-lookup"><span data-stu-id="a6991-129">Property</span></span>|<span data-ttu-id="a6991-130">无</span><span class="sxs-lookup"><span data-stu-id="a6991-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|<span data-ttu-id="a6991-131">属性</span><span class="sxs-lookup"><span data-stu-id="a6991-131">Property</span></span>|<span data-ttu-id="a6991-132">无</span><span class="sxs-lookup"><span data-stu-id="a6991-132">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|<span data-ttu-id="a6991-133">属性</span><span class="sxs-lookup"><span data-stu-id="a6991-133">Property</span></span>|<span data-ttu-id="a6991-134">无</span><span class="sxs-lookup"><span data-stu-id="a6991-134">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|<span data-ttu-id="a6991-135">方法</span><span class="sxs-lookup"><span data-stu-id="a6991-135">Method</span></span>|<span data-ttu-id="a6991-136">无</span><span class="sxs-lookup"><span data-stu-id="a6991-136">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|<span data-ttu-id="a6991-137">方法</span><span class="sxs-lookup"><span data-stu-id="a6991-137">Method</span></span>|<span data-ttu-id="a6991-138">无</span><span class="sxs-lookup"><span data-stu-id="a6991-138">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|<span data-ttu-id="a6991-139">方法</span><span class="sxs-lookup"><span data-stu-id="a6991-139">Method</span></span>|<span data-ttu-id="a6991-140">无</span><span class="sxs-lookup"><span data-stu-id="a6991-140">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|<span data-ttu-id="a6991-141">事件</span><span class="sxs-lookup"><span data-stu-id="a6991-141">Event</span></span>|<span data-ttu-id="a6991-142">无</span><span class="sxs-lookup"><span data-stu-id="a6991-142">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|<span data-ttu-id="a6991-143">事件</span><span class="sxs-lookup"><span data-stu-id="a6991-143">Event</span></span>|<span data-ttu-id="a6991-144">无</span><span class="sxs-lookup"><span data-stu-id="a6991-144">None</span></span>|  
|<xref:System.Windows.Automation.WindowInteractionState>|<span data-ttu-id="a6991-145">事件</span><span class="sxs-lookup"><span data-stu-id="a6991-145">Event</span></span>|<span data-ttu-id="a6991-146">不保证为 <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span><span class="sxs-lookup"><span data-stu-id="a6991-146">Is not guaranteed to be <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span></span>|  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="a6991-147">例外</span><span class="sxs-lookup"><span data-stu-id="a6991-147">Exceptions</span></span>  
 <span data-ttu-id="a6991-148">提供程序必须引发以下异常。</span><span class="sxs-lookup"><span data-stu-id="a6991-148">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="a6991-149">例外类型</span><span class="sxs-lookup"><span data-stu-id="a6991-149">Exception type</span></span>|<span data-ttu-id="a6991-150">条件</span><span class="sxs-lookup"><span data-stu-id="a6991-150">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> <span data-ttu-id="a6991-151">-控件不支持请求的行为时。</span><span class="sxs-lookup"><span data-stu-id="a6991-151">-   When a control does not support a requested behavior.</span></span>|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> <span data-ttu-id="a6991-152">-当参数不是有效的数字时。</span><span class="sxs-lookup"><span data-stu-id="a6991-152">-   When the parameter is not a valid number.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6991-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a6991-153">See also</span></span>

- [<span data-ttu-id="a6991-154">UI 自动化控件模式概述</span><span class="sxs-lookup"><span data-stu-id="a6991-154">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="a6991-155">在 UI 自动化提供程序中支持控件模式</span><span class="sxs-lookup"><span data-stu-id="a6991-155">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="a6991-156">客户端的 UI 自动化控件模式</span><span class="sxs-lookup"><span data-stu-id="a6991-156">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="a6991-157">UI 自动化树概述</span><span class="sxs-lookup"><span data-stu-id="a6991-157">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="a6991-158">在 UI 自动化中使用缓存</span><span class="sxs-lookup"><span data-stu-id="a6991-158">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)

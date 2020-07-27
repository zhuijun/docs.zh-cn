---
title: UI 自动化对标准控件的支持
description: 获取有关对 Windows Presentation Foundation （WPF）、Win32 和 Windows 窗体开发的应用程序中的标准控件的 UI 自动化支持的信息。
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 17916a6978008439e91caae00d8b6f26045f9018
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166123"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="d6456-103">UI 自动化对标准控件的支持</span><span class="sxs-lookup"><span data-stu-id="d6456-103">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="d6456-104">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="d6456-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="d6456-105">有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="d6456-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="d6456-106">本主题包含有关为 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 、Win32 和 Windows 窗体框架开发的应用程序中标准控件的支持的信息。</span><span class="sxs-lookup"><span data-stu-id="d6456-106">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32, and Windows Forms frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="d6456-107">Windows Presentation Foundation 控件</span><span class="sxs-lookup"><span data-stu-id="d6456-107">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="d6456-108">为用户交互提供信息或支持的所有 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 控件元素均具有对 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的完整本机支持。</span><span class="sxs-lookup"><span data-stu-id="d6456-108">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="d6456-109">面板等其他元素对 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]不可见。</span><span class="sxs-lookup"><span data-stu-id="d6456-109">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>
## <a name="win32-controls"></a><span data-ttu-id="d6456-110">Win32 控件</span><span class="sxs-lookup"><span data-stu-id="d6456-110">Win32 Controls</span></span>  
 <span data-ttu-id="d6456-111">大多数 Win32 控件都 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 通过 UIAutomationClientsideProviders.dll 中的客户端提供程序公开。</span><span class="sxs-lookup"><span data-stu-id="d6456-111">Most Win32 controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="d6456-112">此程序集将自动注册，以用于 UI 自动化客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="d6456-112">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="d6456-113">仅为*ComCtrl32.dll*版本6中的控件提供完全支持。</span><span class="sxs-lookup"><span data-stu-id="d6456-113">Full support is provided only for controls from version 6 of *ComCtrl32.dll*.</span></span>  
  
 <span data-ttu-id="d6456-114">支持以下控件。</span><span class="sxs-lookup"><span data-stu-id="d6456-114">The following controls are supported.</span></span>  
  
|<span data-ttu-id="d6456-115">类名</span><span class="sxs-lookup"><span data-stu-id="d6456-115">Class name</span></span>|<span data-ttu-id="d6456-116">控件类型</span><span class="sxs-lookup"><span data-stu-id="d6456-116">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="d6456-117">Button</span><span class="sxs-lookup"><span data-stu-id="d6456-117">Button</span></span>|<span data-ttu-id="d6456-118">Button</span><span class="sxs-lookup"><span data-stu-id="d6456-118">Button</span></span>|  
|<span data-ttu-id="d6456-119">Button</span><span class="sxs-lookup"><span data-stu-id="d6456-119">Button</span></span>|<span data-ttu-id="d6456-120">RadioButton</span><span class="sxs-lookup"><span data-stu-id="d6456-120">RadioButton</span></span>|  
|<span data-ttu-id="d6456-121">Button</span><span class="sxs-lookup"><span data-stu-id="d6456-121">Button</span></span>|<span data-ttu-id="d6456-122">Group</span><span class="sxs-lookup"><span data-stu-id="d6456-122">Group</span></span>|  
|<span data-ttu-id="d6456-123">Button</span><span class="sxs-lookup"><span data-stu-id="d6456-123">Button</span></span>|<span data-ttu-id="d6456-124">CheckBox</span><span class="sxs-lookup"><span data-stu-id="d6456-124">CheckBox</span></span>|  
|<span data-ttu-id="d6456-125">Button</span><span class="sxs-lookup"><span data-stu-id="d6456-125">Button</span></span>|<span data-ttu-id="d6456-126">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="d6456-126">Hyperlink</span></span>|  
|<span data-ttu-id="d6456-127">Button</span><span class="sxs-lookup"><span data-stu-id="d6456-127">Button</span></span>|<span data-ttu-id="d6456-128">SplitButton</span><span class="sxs-lookup"><span data-stu-id="d6456-128">SplitButton</span></span>|  
|<span data-ttu-id="d6456-129">Button</span><span class="sxs-lookup"><span data-stu-id="d6456-129">Button</span></span>|<span data-ttu-id="d6456-130">CheckBox</span><span class="sxs-lookup"><span data-stu-id="d6456-130">CheckBox</span></span>|  
|<span data-ttu-id="d6456-131">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="d6456-131">ComboBoxEx32</span></span>|<span data-ttu-id="d6456-132">组合框</span><span class="sxs-lookup"><span data-stu-id="d6456-132">ComboBox</span></span>|  
|<span data-ttu-id="d6456-133">组合框</span><span class="sxs-lookup"><span data-stu-id="d6456-133">ComboBox</span></span>|<span data-ttu-id="d6456-134">组合框</span><span class="sxs-lookup"><span data-stu-id="d6456-134">ComboBox</span></span>|  
|<span data-ttu-id="d6456-135">编辑</span><span class="sxs-lookup"><span data-stu-id="d6456-135">Edit</span></span>|<span data-ttu-id="d6456-136">文档</span><span class="sxs-lookup"><span data-stu-id="d6456-136">Document</span></span>|  
|<span data-ttu-id="d6456-137">编辑</span><span class="sxs-lookup"><span data-stu-id="d6456-137">Edit</span></span>|<span data-ttu-id="d6456-138">编辑</span><span class="sxs-lookup"><span data-stu-id="d6456-138">Edit</span></span>|  
|<span data-ttu-id="d6456-139">SysLink</span><span class="sxs-lookup"><span data-stu-id="d6456-139">SysLink</span></span>|<span data-ttu-id="d6456-140">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="d6456-140">Hyperlink</span></span>|  
|<span data-ttu-id="d6456-141">静态</span><span class="sxs-lookup"><span data-stu-id="d6456-141">Static</span></span>|<span data-ttu-id="d6456-142">文本</span><span class="sxs-lookup"><span data-stu-id="d6456-142">Text</span></span>|  
|<span data-ttu-id="d6456-143">静态</span><span class="sxs-lookup"><span data-stu-id="d6456-143">Static</span></span>|<span data-ttu-id="d6456-144">映像</span><span class="sxs-lookup"><span data-stu-id="d6456-144">Image</span></span>|  
|<span data-ttu-id="d6456-145">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="d6456-145">SysIPAddress32</span></span>|<span data-ttu-id="d6456-146">自定义</span><span class="sxs-lookup"><span data-stu-id="d6456-146">Custom</span></span>|  
|<span data-ttu-id="d6456-147">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="d6456-147">SysHeader32</span></span>|<span data-ttu-id="d6456-148">Header/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="d6456-148">Header/HeaderItem</span></span>|  
|<span data-ttu-id="d6456-149">SysListView32</span><span class="sxs-lookup"><span data-stu-id="d6456-149">SysListView32</span></span>|<span data-ttu-id="d6456-150">DataGrid</span><span class="sxs-lookup"><span data-stu-id="d6456-150">DataGrid</span></span>|  
|<span data-ttu-id="d6456-151">SysListView32</span><span class="sxs-lookup"><span data-stu-id="d6456-151">SysListView32</span></span>|<span data-ttu-id="d6456-152">列出</span><span class="sxs-lookup"><span data-stu-id="d6456-152">List</span></span>|  
|<span data-ttu-id="d6456-153">ListBox</span><span class="sxs-lookup"><span data-stu-id="d6456-153">ListBox</span></span>|<span data-ttu-id="d6456-154">列出</span><span class="sxs-lookup"><span data-stu-id="d6456-154">List</span></span>|  
|<span data-ttu-id="d6456-155">ListBox</span><span class="sxs-lookup"><span data-stu-id="d6456-155">ListBox</span></span>|<span data-ttu-id="d6456-156">ListItem</span><span class="sxs-lookup"><span data-stu-id="d6456-156">ListItem</span></span>|  
|<span data-ttu-id="d6456-157">#32768</span><span class="sxs-lookup"><span data-stu-id="d6456-157">#32768</span></span>|<span data-ttu-id="d6456-158">菜单</span><span class="sxs-lookup"><span data-stu-id="d6456-158">Menu</span></span>|  
|<span data-ttu-id="d6456-159">#32768</span><span class="sxs-lookup"><span data-stu-id="d6456-159">#32768</span></span>|<span data-ttu-id="d6456-160">MenuItem</span><span class="sxs-lookup"><span data-stu-id="d6456-160">MenuItem</span></span>|  
|<span data-ttu-id="d6456-161">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="d6456-161">msctls_progress32</span></span>|<span data-ttu-id="d6456-162">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="d6456-162">ProgressBar</span></span>|  
|<span data-ttu-id="d6456-163">RichEdit</span><span class="sxs-lookup"><span data-stu-id="d6456-163">RichEdit</span></span>|<span data-ttu-id="d6456-164">Document。</span><span class="sxs-lookup"><span data-stu-id="d6456-164">Document.</span></span> <span data-ttu-id="d6456-165">查看注释。</span><span class="sxs-lookup"><span data-stu-id="d6456-165">See note.</span></span>|  
|<span data-ttu-id="d6456-166">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="d6456-166">RichEdit20A</span></span>|<span data-ttu-id="d6456-167">文档</span><span class="sxs-lookup"><span data-stu-id="d6456-167">Document</span></span>|  
|<span data-ttu-id="d6456-168">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="d6456-168">RichEdit20W</span></span>|<span data-ttu-id="d6456-169">文档</span><span class="sxs-lookup"><span data-stu-id="d6456-169">Document</span></span>|  
|<span data-ttu-id="d6456-170">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="d6456-170">RichEdit50W</span></span>|<span data-ttu-id="d6456-171">文档</span><span class="sxs-lookup"><span data-stu-id="d6456-171">Document</span></span>|  
|<span data-ttu-id="d6456-172">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="d6456-172">ScrollBar</span></span>|<span data-ttu-id="d6456-173">滑块</span><span class="sxs-lookup"><span data-stu-id="d6456-173">Slider</span></span>|  
|<span data-ttu-id="d6456-174">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="d6456-174">msctls_trackbar32</span></span>|<span data-ttu-id="d6456-175">滑块</span><span class="sxs-lookup"><span data-stu-id="d6456-175">Slider</span></span>|  
|<span data-ttu-id="d6456-176">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="d6456-176">msctls_updown32</span></span>|<span data-ttu-id="d6456-177">Spinner</span><span class="sxs-lookup"><span data-stu-id="d6456-177">Spinner</span></span>|  
|<span data-ttu-id="d6456-178">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="d6456-178">msctls_statusbar32</span></span>|<span data-ttu-id="d6456-179">StatusBar</span><span class="sxs-lookup"><span data-stu-id="d6456-179">StatusBar</span></span>|  
|<span data-ttu-id="d6456-180">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="d6456-180">SysTabControl32</span></span>|<span data-ttu-id="d6456-181">选项卡</span><span class="sxs-lookup"><span data-stu-id="d6456-181">Tab</span></span>|  
|<span data-ttu-id="d6456-182">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="d6456-182">SysTabControl32</span></span>|<span data-ttu-id="d6456-183">TabItem</span><span class="sxs-lookup"><span data-stu-id="d6456-183">TabItem</span></span>|  
|<span data-ttu-id="d6456-184">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="d6456-184">ToolbarWindow32</span></span>|<span data-ttu-id="d6456-185">ToolBar</span><span class="sxs-lookup"><span data-stu-id="d6456-185">ToolBar</span></span>|  
|<span data-ttu-id="d6456-186">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="d6456-186">ToolbarWindow32</span></span>|<span data-ttu-id="d6456-187">MenuItem</span><span class="sxs-lookup"><span data-stu-id="d6456-187">MenuItem</span></span>|  
|<span data-ttu-id="d6456-188">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="d6456-188">ToolbarWindow32</span></span>|<span data-ttu-id="d6456-189">Button</span><span class="sxs-lookup"><span data-stu-id="d6456-189">Button</span></span>|  
|<span data-ttu-id="d6456-190">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="d6456-190">ToolbarWindow32</span></span>|<span data-ttu-id="d6456-191">CheckBox</span><span class="sxs-lookup"><span data-stu-id="d6456-191">CheckBox</span></span>|  
|<span data-ttu-id="d6456-192">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="d6456-192">ToolbarWindow32</span></span>|<span data-ttu-id="d6456-193">RadioButton</span><span class="sxs-lookup"><span data-stu-id="d6456-193">RadioButton</span></span>|  
|<span data-ttu-id="d6456-194">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="d6456-194">ToolbarWindow32</span></span>|<span data-ttu-id="d6456-195">Separator</span><span class="sxs-lookup"><span data-stu-id="d6456-195">Separator</span></span>|  
|<span data-ttu-id="d6456-196">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="d6456-196">tooltips_class32</span></span>|<span data-ttu-id="d6456-197">ToolTip</span><span class="sxs-lookup"><span data-stu-id="d6456-197">ToolTip</span></span>|  
|<span data-ttu-id="d6456-198">#32774</span><span class="sxs-lookup"><span data-stu-id="d6456-198">#32774</span></span>|<span data-ttu-id="d6456-199">ToolTip</span><span class="sxs-lookup"><span data-stu-id="d6456-199">ToolTip</span></span>|  
|<span data-ttu-id="d6456-200">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="d6456-200">ReBarWindow32</span></span>|<span data-ttu-id="d6456-201">工具栏</span><span class="sxs-lookup"><span data-stu-id="d6456-201">Toolbar</span></span>|  
|<span data-ttu-id="d6456-202">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="d6456-202">SysTreeView32</span></span>|<span data-ttu-id="d6456-203">树</span><span class="sxs-lookup"><span data-stu-id="d6456-203">Tree</span></span>|  
|<span data-ttu-id="d6456-204">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="d6456-204">SysTreeView32</span></span>|<span data-ttu-id="d6456-205">TreeItem</span><span class="sxs-lookup"><span data-stu-id="d6456-205">TreeItem</span></span>|  
  
 <span data-ttu-id="d6456-206">**注意**只有 Windows Vista 附带的版本支持 RichEdit 控件（在3.1 版及更高版本 RichEd20.dll 中，并且 MsftEdit.dll 版本4.1 及更高版本）。</span><span class="sxs-lookup"><span data-stu-id="d6456-206">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="d6456-207">不支持以下控件。</span><span class="sxs-lookup"><span data-stu-id="d6456-207">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="d6456-208">类名</span><span class="sxs-lookup"><span data-stu-id="d6456-208">Class name</span></span>|<span data-ttu-id="d6456-209">控件类型</span><span class="sxs-lookup"><span data-stu-id="d6456-209">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="d6456-210">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="d6456-210">SysAnimate32</span></span>|<span data-ttu-id="d6456-211">映像</span><span class="sxs-lookup"><span data-stu-id="d6456-211">Image</span></span>|  
|<span data-ttu-id="d6456-212">SysPager</span><span class="sxs-lookup"><span data-stu-id="d6456-212">SysPager</span></span>|<span data-ttu-id="d6456-213">Spinner</span><span class="sxs-lookup"><span data-stu-id="d6456-213">Spinner</span></span>|  
|<span data-ttu-id="d6456-214">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="d6456-214">SysDateTimePick32</span></span>|<span data-ttu-id="d6456-215">自定义</span><span class="sxs-lookup"><span data-stu-id="d6456-215">Custom</span></span>|  
|<span data-ttu-id="d6456-216">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="d6456-216">SysMonthCal32</span></span>|<span data-ttu-id="d6456-217">日历</span><span class="sxs-lookup"><span data-stu-id="d6456-217">Calendar</span></span>|  
|<span data-ttu-id="d6456-218">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="d6456-218">MS_WINNOTE</span></span>|<span data-ttu-id="d6456-219">工具提示</span><span class="sxs-lookup"><span data-stu-id="d6456-219">Tooltip</span></span>|  
|<span data-ttu-id="d6456-220">VBBubble</span><span class="sxs-lookup"><span data-stu-id="d6456-220">VBBubble</span></span>|<span data-ttu-id="d6456-221">工具提示</span><span class="sxs-lookup"><span data-stu-id="d6456-221">Tooltip</span></span>|  
|<span data-ttu-id="d6456-222">ScrollBar（在用作独立控件时）</span><span class="sxs-lookup"><span data-stu-id="d6456-222">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="d6456-223">滑块</span><span class="sxs-lookup"><span data-stu-id="d6456-223">Slider</span></span>|  
|<span data-ttu-id="d6456-224">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="d6456-224">SuperGrid</span></span>|<span data-ttu-id="d6456-225">自定义</span><span class="sxs-lookup"><span data-stu-id="d6456-225">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>
## <a name="windows-forms-controls"></a><span data-ttu-id="d6456-226">Windows 窗体控件</span><span class="sxs-lookup"><span data-stu-id="d6456-226">Windows Forms Controls</span></span>  
 <span data-ttu-id="d6456-227">[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]通过 UIAutomationClientsideProviders.dll 中的客户端提供程序向 Windows 窗体控件公开。</span><span class="sxs-lookup"><span data-stu-id="d6456-227">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="d6456-228">此程序集将自动注册，以用于 UI 自动化客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="d6456-228">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="d6456-229">通常，支持作为 Win32 公共控件的托管包装器 Windows 窗体控件 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d6456-229">Typically, Windows Forms controls that are managed wrappers for Win32 common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="d6456-230">支持以下控件。</span><span class="sxs-lookup"><span data-stu-id="d6456-230">The following controls are supported.</span></span>  
  
|<span data-ttu-id="d6456-231">类名</span><span class="sxs-lookup"><span data-stu-id="d6456-231">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="d6456-232">Button</span><span class="sxs-lookup"><span data-stu-id="d6456-232">Button</span></span>|  
|<span data-ttu-id="d6456-233">CheckBox</span><span class="sxs-lookup"><span data-stu-id="d6456-233">CheckBox</span></span>|  
|<span data-ttu-id="d6456-234">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="d6456-234">CheckedListBox</span></span>|  
|<span data-ttu-id="d6456-235">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="d6456-235">ColorDialog</span></span>|  
|<span data-ttu-id="d6456-236">组合框</span><span class="sxs-lookup"><span data-stu-id="d6456-236">ComboBox</span></span>|  
|<span data-ttu-id="d6456-237">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="d6456-237">FolderBrowser</span></span>|  
|<span data-ttu-id="d6456-238">FontDialog</span><span class="sxs-lookup"><span data-stu-id="d6456-238">FontDialog</span></span>|  
|<span data-ttu-id="d6456-239">GroupBox</span><span class="sxs-lookup"><span data-stu-id="d6456-239">GroupBox</span></span>|  
|<span data-ttu-id="d6456-240">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="d6456-240">HscrollBar</span></span>|  
|<span data-ttu-id="d6456-241">ImageList</span><span class="sxs-lookup"><span data-stu-id="d6456-241">ImageList</span></span>|  
|<span data-ttu-id="d6456-242">Label</span><span class="sxs-lookup"><span data-stu-id="d6456-242">Label</span></span>|  
|<span data-ttu-id="d6456-243">ListBox</span><span class="sxs-lookup"><span data-stu-id="d6456-243">ListBox</span></span>|  
|<span data-ttu-id="d6456-244">ListView</span><span class="sxs-lookup"><span data-stu-id="d6456-244">ListView</span></span>|  
|<span data-ttu-id="d6456-245">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="d6456-245">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="d6456-246">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="d6456-246">MonthCalendar</span></span>|  
|<span data-ttu-id="d6456-247">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="d6456-247">NotifyIcon</span></span>|  
|<span data-ttu-id="d6456-248">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="d6456-248">OpenFileDialog</span></span>|  
|<span data-ttu-id="d6456-249">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="d6456-249">PageSetupDialog</span></span>|  
|<span data-ttu-id="d6456-250">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="d6456-250">PrintDialog</span></span>|  
|<span data-ttu-id="d6456-251">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="d6456-251">ProgressBar</span></span>|  
|<span data-ttu-id="d6456-252">RadioButton</span><span class="sxs-lookup"><span data-stu-id="d6456-252">RadioButton</span></span>|  
|<span data-ttu-id="d6456-253">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="d6456-253">RichTextBox</span></span>|  
|<span data-ttu-id="d6456-254">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="d6456-254">SaveFileDialog</span></span>|  
|<span data-ttu-id="d6456-255">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="d6456-255">ScrollableControl</span></span>|  
|<span data-ttu-id="d6456-256">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="d6456-256">SoundPlayer</span></span>|  
|<span data-ttu-id="d6456-257">StatusBar</span><span class="sxs-lookup"><span data-stu-id="d6456-257">StatusBar</span></span>|  
|<span data-ttu-id="d6456-258">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="d6456-258">TabControl/TabPage</span></span>|  
|<span data-ttu-id="d6456-259">TextBox</span><span class="sxs-lookup"><span data-stu-id="d6456-259">TextBox</span></span>|  
|<span data-ttu-id="d6456-260">Timer</span><span class="sxs-lookup"><span data-stu-id="d6456-260">Timer</span></span>|  
|<span data-ttu-id="d6456-261">工具栏</span><span class="sxs-lookup"><span data-stu-id="d6456-261">Toolbar</span></span>|  
|<span data-ttu-id="d6456-262">ToolTip</span><span class="sxs-lookup"><span data-stu-id="d6456-262">ToolTip</span></span>|  
|<span data-ttu-id="d6456-263">TrackBar</span><span class="sxs-lookup"><span data-stu-id="d6456-263">TrackBar</span></span>|  
|<span data-ttu-id="d6456-264">TreeView</span><span class="sxs-lookup"><span data-stu-id="d6456-264">TreeView</span></span>|  
|<span data-ttu-id="d6456-265">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="d6456-265">VscrollBar</span></span>|  
|<span data-ttu-id="d6456-266">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="d6456-266">WebBrowser</span></span>|  
  
 <span data-ttu-id="d6456-267">以下控件 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 仅通过其对 Microsoft Active Accessibility 的支持公开。</span><span class="sxs-lookup"><span data-stu-id="d6456-267">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="d6456-268">某些功能可能不可用。</span><span class="sxs-lookup"><span data-stu-id="d6456-268">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="d6456-269">控件名称</span><span class="sxs-lookup"><span data-stu-id="d6456-269">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="d6456-270">BindingSource</span><span class="sxs-lookup"><span data-stu-id="d6456-270">BindingSource</span></span>|  
|<span data-ttu-id="d6456-271">DataGrid</span><span class="sxs-lookup"><span data-stu-id="d6456-271">DataGrid</span></span>|  
|<span data-ttu-id="d6456-272">DataGridView</span><span class="sxs-lookup"><span data-stu-id="d6456-272">DataGridView</span></span>|  
|<span data-ttu-id="d6456-273">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="d6456-273">DataNavigator</span></span>|  
|<span data-ttu-id="d6456-274">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="d6456-274">DomainUpDown</span></span>|  
|<span data-ttu-id="d6456-275">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="d6456-275">ErrorProvider</span></span>|  
|<span data-ttu-id="d6456-276">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="d6456-276">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="d6456-277">窗体</span><span class="sxs-lookup"><span data-stu-id="d6456-277">Form</span></span>|  
|<span data-ttu-id="d6456-278">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="d6456-278">LinkLabel</span></span>|  
|<span data-ttu-id="d6456-279">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="d6456-279">HelpProvider</span></span>|  
|<span data-ttu-id="d6456-280">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="d6456-280">MaskedTextBox</span></span>|  
|<span data-ttu-id="d6456-281">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="d6456-281">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="d6456-282">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="d6456-282">NumericUpDown</span></span>|  
|<span data-ttu-id="d6456-283">Panel</span><span class="sxs-lookup"><span data-stu-id="d6456-283">Panel</span></span>|  
|<span data-ttu-id="d6456-284">PictureBox</span><span class="sxs-lookup"><span data-stu-id="d6456-284">PictureBox</span></span>|  
|<span data-ttu-id="d6456-285">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="d6456-285">PrintDocument</span></span>|  
|<span data-ttu-id="d6456-286">PrintPreview-Control</span><span class="sxs-lookup"><span data-stu-id="d6456-286">PrintPreview-Control</span></span>|  
|<span data-ttu-id="d6456-287">PrintPreview-Dialog</span><span class="sxs-lookup"><span data-stu-id="d6456-287">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="d6456-288">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="d6456-288">PropertyGrid</span></span>|  
|<span data-ttu-id="d6456-289">用户控件</span><span class="sxs-lookup"><span data-stu-id="d6456-289">UserControl</span></span>|  
|<span data-ttu-id="d6456-290">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="d6456-290">ToolStrip</span></span>|  
|<span data-ttu-id="d6456-291">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="d6456-291">TableLayoutPanel</span></span>|  
|<span data-ttu-id="d6456-292">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="d6456-292">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="d6456-293">Splitter</span><span class="sxs-lookup"><span data-stu-id="d6456-293">Splitter</span></span>|  
|<span data-ttu-id="d6456-294">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="d6456-294">RaftingContainer</span></span>|  
|<span data-ttu-id="d6456-295">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="d6456-295">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d6456-296">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d6456-296">See also</span></span>

- [<span data-ttu-id="d6456-297">UI 自动化控件类型</span><span class="sxs-lookup"><span data-stu-id="d6456-297">UI Automation Control Types</span></span>](ui-automation-control-types.md)

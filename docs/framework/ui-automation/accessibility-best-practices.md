---
title: 辅助功能最佳方案
description: 了解 .NET 中的辅助功能最佳实践。 探索编程访问、用户设置、可视化 UI 设计、导航和无模接口。
ms.date: 03/30/2017
helpviewer_keywords:
- best practices for accessibility
- accessibility, best practices for
ms.assetid: e6d5cd98-21a3-4b01-999c-fb953556d0e6
ms.openlocfilehash: 2980881bbcd34ca82f6cca7723cf976e0890f463
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557081"
---
# <a name="accessibility-best-practices"></a><span data-ttu-id="9864b-104">辅助功能最佳做法</span><span class="sxs-lookup"><span data-stu-id="9864b-104">Accessibility best practices</span></span>

> [!NOTE]
> <span data-ttu-id="9864b-105">本文适用于想要使用命名空间中定义的托管 UI 自动化类的 .NET Framework 开发人员 <xref:System.Windows.Automation> 。</span><span class="sxs-lookup"><span data-stu-id="9864b-105">This article is intended for .NET Framework developers who want to use the managed UI Automation classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="9864b-106">有关 UI 自动化的最新信息，请参阅[Windows 自动化 API： Ui 自动化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="9864b-106">For the latest information about UI Automation, see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="9864b-107">在控件或应用程序中实现以下最佳做法将提高使用辅助技术设备的用户的可访问性。</span><span class="sxs-lookup"><span data-stu-id="9864b-107">Implementing the following best practices in controls or applications will improve their accessibility for people who use assistive technology devices.</span></span> <span data-ttu-id="9864b-108">其中许多最佳实践侧重于 (UI) 设计的良好用户界面。</span><span class="sxs-lookup"><span data-stu-id="9864b-108">Many of these best practices focus on good user interface (UI) design.</span></span> <span data-ttu-id="9864b-109">每个最佳做法都包含 Windows Presentation Foundation (WPF) 控件或应用程序的实现信息。</span><span class="sxs-lookup"><span data-stu-id="9864b-109">Each best practice includes implementation information for Windows Presentation Foundation (WPF) controls or applications.</span></span> <span data-ttu-id="9864b-110">在许多情况下，满足这些最佳做法的工作已包含在 WPF 控件中。</span><span class="sxs-lookup"><span data-stu-id="9864b-110">In many cases, the work to meet these best practices is already included in WPF controls.</span></span>  
  
<a name="Programmatic_Access"></a>
## <a name="programmatic-access"></a><span data-ttu-id="9864b-111">以编程方式访问</span><span class="sxs-lookup"><span data-stu-id="9864b-111">Programmatic Access</span></span>  
 <span data-ttu-id="9864b-112">编程访问涉及确保所有 UI 元素都已标记、公开了属性值并引发了相应的事件。</span><span class="sxs-lookup"><span data-stu-id="9864b-112">Programmatic access involves ensuring that all UI elements are labeled, property values are exposed, and appropriate events are raised.</span></span> <span data-ttu-id="9864b-113">对于标准 WPF 控件，其中的大部分工作已通过完成 <xref:System.Windows.Automation.Peers.AutomationPeer> 。</span><span class="sxs-lookup"><span data-stu-id="9864b-113">For standard WPF controls, most of this work is already done through <xref:System.Windows.Automation.Peers.AutomationPeer>.</span></span> <span data-ttu-id="9864b-114">自定义控件需要额外操作以确保正确实现编程访问。</span><span class="sxs-lookup"><span data-stu-id="9864b-114">Custom controls require additional work to ensure that programmatic access is correctly implemented.</span></span>  
  
<a name="Enable_Programmatic_Access_to_all_UI_Elements_and_Text"></a>
### <a name="enable-programmatic-access-to-all-ui-elements-and-text"></a><span data-ttu-id="9864b-115">对所有 UI 元素和文本启用编程访问</span><span class="sxs-lookup"><span data-stu-id="9864b-115">Enable Programmatic Access to all UI Elements and Text</span></span>  
 <span data-ttu-id="9864b-116">用户界面 (UI) 元素应启用编程访问。</span><span class="sxs-lookup"><span data-stu-id="9864b-116">User interface (UI) elements should enable programmatic access.</span></span> <span data-ttu-id="9864b-117">如果 UI 是标准 WPF 控件，则控件中包含对编程访问的支持。</span><span class="sxs-lookup"><span data-stu-id="9864b-117">If the UI is a standard WPF control, support for programmatic access is included in the control.</span></span> <span data-ttu-id="9864b-118">如果此控件是自定义控件（已是公共控件或“控件”的子类别），则必须检查可能需要修改的区域的 <xref:System.Windows.Automation.Peers.AutomationPeer> 实现。</span><span class="sxs-lookup"><span data-stu-id="9864b-118">If the control is a custom control – a control that has been subclassed from a common control or a control that has been subclassed from Control – then you must check the <xref:System.Windows.Automation.Peers.AutomationPeer> implementation for areas that may need modification.</span></span>  
  
 <span data-ttu-id="9864b-119">遵循此最佳做法，辅助技术供应商可以标识和操作产品 UI 的元素。</span><span class="sxs-lookup"><span data-stu-id="9864b-119">Following this best practice allows assistive technology vendors to identify and manipulate elements of your product's UI.</span></span>  
  
<a name="Place_Names__Titles_and_Descriptions_on_UI_Objects_"></a>
### <a name="place-names-titles-and-descriptions-on-ui-objects-frames-and-pages"></a><span data-ttu-id="9864b-120">在 UI 对象、帧和页面上添加名称、标题和说明</span><span class="sxs-lookup"><span data-stu-id="9864b-120">Place Names, Titles, and Descriptions on UI Objects, Frames, and Pages</span></span>  
 <span data-ttu-id="9864b-121">辅助技术（尤其是屏幕阅读器）使用标题来了解导航方案中的帧、对象或页面的位置。</span><span class="sxs-lookup"><span data-stu-id="9864b-121">Assistive technologies, especially screen readers, use the title to understand the location of the frame, object, or page in the navigation scheme.</span></span> <span data-ttu-id="9864b-122">因此，标题必须是描述性的。</span><span class="sxs-lookup"><span data-stu-id="9864b-122">Therefore, the title must be descriptive.</span></span> <span data-ttu-id="9864b-123">例如，如果用户已深入导航到某个特定区域，“Microsoft 网页”的网页标题毫无用处。</span><span class="sxs-lookup"><span data-stu-id="9864b-123">For example, a Web page title of "Microsoft Web Page" is useless if the user has navigated deeply into some particular area.</span></span> <span data-ttu-id="9864b-124">描述性标题对于有视力障碍且依赖屏幕阅读器的用户至关重要。</span><span class="sxs-lookup"><span data-stu-id="9864b-124">A descriptive title is critical for users who are blind and depend on screen readers.</span></span> <span data-ttu-id="9864b-125">同样，对于 WPF 控件， <xref:System.Windows.Automation.AutomationProperties.NameProperty> 和对于 <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> 辅助技术设备十分重要。</span><span class="sxs-lookup"><span data-stu-id="9864b-125">Similarly, for WPF controls, <xref:System.Windows.Automation.AutomationProperties.NameProperty> and <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> are important for assistive technology devices.</span></span>  
  
 <span data-ttu-id="9864b-126">遵循此最佳做法，辅助技术可以在示例控件和应用程序中识别和操作 UI。</span><span class="sxs-lookup"><span data-stu-id="9864b-126">Following this best practice allows assistive technologies to identify and manipulate UI in sample controls and applications.</span></span>  
  
<a name="Ensure_Programmatic_Events_are_Triggered_by_all_UI"></a>
### <a name="ensure-programmatic-events-are-triggered-by-all-ui-activities"></a><span data-ttu-id="9864b-127">确保编程事件可以由所有 UI 活动触发</span><span class="sxs-lookup"><span data-stu-id="9864b-127">Ensure Programmatic Events Are Triggered by All UI Activities</span></span>  
 <span data-ttu-id="9864b-128">遵循此最佳做法，辅助技术可以侦听 UI 中的更改并通知用户这些更改。</span><span class="sxs-lookup"><span data-stu-id="9864b-128">Following this best practice allows assistive technologies to listen for changes in the UI and notify the user about these changes.</span></span>  
  
<a name="User_Settings"></a>
## <a name="user-settings"></a><span data-ttu-id="9864b-129">用户设置</span><span class="sxs-lookup"><span data-stu-id="9864b-129">User Settings</span></span>  
 <span data-ttu-id="9864b-130">本节中的最佳做法可确保控件或应用程序不重写用户设置。</span><span class="sxs-lookup"><span data-stu-id="9864b-130">The best practice in this section ensures that controls or applications do not override user settings.</span></span>  
  
<a name="Respect_all_System_Wide_Settings_and_do_not_Interfere"></a>
### <a name="respect-all-system-wide-settings-and-do-not-interfere-with-accessibility-functions"></a><span data-ttu-id="9864b-131">请遵守所有系统范围内设置，同时请勿干扰辅助功能函数</span><span class="sxs-lookup"><span data-stu-id="9864b-131">Respect All System-Wide Settings and Do Not Interfere with Accessibility Functions</span></span>  
 <span data-ttu-id="9864b-132">用户可以使用“控制面板”设置一些系统范围内标志；而其他标志可通过编程方式进行设置。</span><span class="sxs-lookup"><span data-stu-id="9864b-132">Users can use the Control Panel to set some system-wide flags; other flags can be set programmatically.</span></span> <span data-ttu-id="9864b-133">控件或应用程序不应更改这些设置。</span><span class="sxs-lookup"><span data-stu-id="9864b-133">These settings should not be changed by controls or applications.</span></span> <span data-ttu-id="9864b-134">此外，应用程序必须支持其主机操作系统的辅助功能设置。</span><span class="sxs-lookup"><span data-stu-id="9864b-134">Also, applications must support the accessibility settings of their host operating system.</span></span>  
  
 <span data-ttu-id="9864b-135">遵循此最佳做法，用户可设置辅助功能设置并了解应用程序将不会更改这些设置。</span><span class="sxs-lookup"><span data-stu-id="9864b-135">Following this best practice allows users to set accessibility settings and know that those settings will not be changed by applications.</span></span>  
  
<a name="Visual_UI_Design"></a>
## <a name="visual-ui-design"></a><span data-ttu-id="9864b-136">可视 UI 设计</span><span class="sxs-lookup"><span data-stu-id="9864b-136">Visual UI Design</span></span>  
 <span data-ttu-id="9864b-137">本节中的最佳做法可确保控件或应用程序有效地使用颜色和图像，并可供辅助技术使用。</span><span class="sxs-lookup"><span data-stu-id="9864b-137">Best Practices in this section ensure that controls or applications use color and images effectively and are able to be used by Assistive technologies.</span></span>  
  
<a name="Don_t_Hard_Code_Colors"></a>
### <a name="dont-hard-code-colors"></a><span data-ttu-id="9864b-138">请勿进行硬编码颜色</span><span class="sxs-lookup"><span data-stu-id="9864b-138">Don't Hard-Code Colors</span></span>  
 <span data-ttu-id="9864b-139">色盲、视力较差，或者使用黑白屏幕的用户可能无法使用带有硬编码颜色的应用程序。</span><span class="sxs-lookup"><span data-stu-id="9864b-139">People who are color blind, have low vision, or are using a black and white screen might not be able to use applications with hard-coded colors.</span></span>  
  
 <span data-ttu-id="9864b-140">遵循此最佳做法，用户可根据各自需求调整颜色组合。</span><span class="sxs-lookup"><span data-stu-id="9864b-140">Following this best practice allows users to adjust color combinations based on individual needs.</span></span>  
  
<a name="Support_High_Contrast_and_all_System_Display_Attributes"></a>
### <a name="support-high-contrast-and-all-system-display-attributes"></a><span data-ttu-id="9864b-141">支持高对比度和所有系统显示特性</span><span class="sxs-lookup"><span data-stu-id="9864b-141">Support High Contrast and all System Display Attributes</span></span>  
 <span data-ttu-id="9864b-142">应用程序不应中断或禁用用户选定的系统范围内对比度设置、颜色选择或其他系统范围内显示设置和特性。</span><span class="sxs-lookup"><span data-stu-id="9864b-142">Applications should not disrupt or disable user-selected, system-wide contrast settings, color selections, or other system-wide display settings and attributes.</span></span> <span data-ttu-id="9864b-143">用户采用的系统范围内设置可增强应用程序的辅助功能，因此应用程序不应禁用或忽略它。</span><span class="sxs-lookup"><span data-stu-id="9864b-143">System-wide settings adopted by a user enhance the accessibility of applications, so they should not be disabled or disregarded by applications.</span></span> <span data-ttu-id="9864b-144">应在前景色背景色组合中正确运用颜色，以确保提供适当的对比度。</span><span class="sxs-lookup"><span data-stu-id="9864b-144">Color should be used in their correct foreground-on-background combination to provide proper contrast.</span></span> <span data-ttu-id="9864b-145">不要混合使用不相关的颜色，也不要反转颜色。</span><span class="sxs-lookup"><span data-stu-id="9864b-145">Don't mix unrelated colors, and don't reverse colors.</span></span>  
  
 <span data-ttu-id="9864b-146">很多用户需要特定的高对比度组合，例如黑色背景中的白色文本。</span><span class="sxs-lookup"><span data-stu-id="9864b-146">Many users require specific high-contrast combinations, such as white text on a black background.</span></span> <span data-ttu-id="9864b-147">绘制这些对比色（如白色背景上的黑色文本）会导致背景渗入前景，使一些用户阅读困难。</span><span class="sxs-lookup"><span data-stu-id="9864b-147">Drawing these reversed, as black text on a white background causes the background to bleed over the foreground and can make reading difficult for some users.</span></span>  
  
<a name="Ensure_all_UI_Correctly_Scales_by_any_DPI_Setting"></a>
### <a name="ensure-all-ui-correctly-scales-by-any-dpi-setting"></a><span data-ttu-id="9864b-148">确保任何 DPI 设置可以正确缩放所有 UI</span><span class="sxs-lookup"><span data-stu-id="9864b-148">Ensure All UI Correctly Scales by Any DPI Setting</span></span>  
 <span data-ttu-id="9864b-149">确保所有 UI 可以按英寸的任何点进行正确缩放 (dpi) 设置。</span><span class="sxs-lookup"><span data-stu-id="9864b-149">Ensure that all UI can correctly scale by any dots per inch (dpi) setting.</span></span> <span data-ttu-id="9864b-150">此外，请确保 UI 元素适合 1024 x 768 屏幕，每英寸120点 (dpi) 。</span><span class="sxs-lookup"><span data-stu-id="9864b-150">Also, ensure that UI elements fit in a screen of 1024 x 768 with 120 dots per inch (dpi).</span></span>  
  
<a name="Navigation"></a>
## <a name="navigation"></a><span data-ttu-id="9864b-151">导航</span><span class="sxs-lookup"><span data-stu-id="9864b-151">Navigation</span></span>  
 <span data-ttu-id="9864b-152">本节中的最佳做法可确保解决控件和应用程序的导航问题。</span><span class="sxs-lookup"><span data-stu-id="9864b-152">Best Practices in this section ensure that navigation has been addressed for controls and applications.</span></span>  
  
<a name="Provide_Keyboard_Interface_for_all_UI_Elements"></a>
### <a name="provide-keyboard-interface-for-all-ui-elements"></a><span data-ttu-id="9864b-153">为所有 UI 元素提供键盘界面</span><span class="sxs-lookup"><span data-stu-id="9864b-153">Provide Keyboard Interface for All UI Elements</span></span>  
 <span data-ttu-id="9864b-154">制表位停止，特别是在仔细规划时，为用户授予另一种导航 UI 的方法。</span><span class="sxs-lookup"><span data-stu-id="9864b-154">Tab stops, especially when carefully planned, give users another way to navigate the UI.</span></span>  
  
 <span data-ttu-id="9864b-155">应用程序应提供以下键盘界面：</span><span class="sxs-lookup"><span data-stu-id="9864b-155">Applications should provide the following keyboard interfaces:</span></span>  
  
- <span data-ttu-id="9864b-156">用户可与之交互的所有控件的制表位，例如按钮、链接或列表框</span><span class="sxs-lookup"><span data-stu-id="9864b-156">tab stops for all controls that the user can interact with, such as buttons, links, or list boxes</span></span>  
  
- <span data-ttu-id="9864b-157">逻辑 Tab 键顺序</span><span class="sxs-lookup"><span data-stu-id="9864b-157">logical tab order</span></span>  
  
<a name="Show_the_Keyboard_Focus"></a>
### <a name="show-the-keyboard-focus"></a><span data-ttu-id="9864b-158">显示键盘焦点</span><span class="sxs-lookup"><span data-stu-id="9864b-158">Show the Keyboard Focus</span></span>  
 <span data-ttu-id="9864b-159">用户需要知道哪个对象具有键盘焦点，以便可以预测击键效果。</span><span class="sxs-lookup"><span data-stu-id="9864b-159">Users need to know which object has the keyboard focus so that they can anticipate the effect of their keystrokes.</span></span> <span data-ttu-id="9864b-160">若要突出显示键盘焦点，请使用颜色、字体或图形（如矩形）或放大倍数。</span><span class="sxs-lookup"><span data-stu-id="9864b-160">To highlight the keyboard focus, use colors, fonts, or graphics such as rectangles or magnification.</span></span> <span data-ttu-id="9864b-161">若要呼叫时突出显示键盘焦点，请更改音量、音调或音质。</span><span class="sxs-lookup"><span data-stu-id="9864b-161">To audibly highlight the keyboard focus, change the volume, pitch, or tonal quality.</span></span>  
  
 <span data-ttu-id="9864b-162">为避免混淆，应用程序应隐藏所有可视焦点指示器并调暗位于非活动窗口（或窗格）中的选择内容。</span><span class="sxs-lookup"><span data-stu-id="9864b-162">To avoid confusion, applications should hide all visual focus indicators and dim selections that are located in inactive windows (or panes).</span></span>  
  
 <span data-ttu-id="9864b-163">应用程序使用键盘焦点执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="9864b-163">Applications should do the following with keyboard focus:</span></span>  
  
- <span data-ttu-id="9864b-164">始终应有一个项具有键盘焦点</span><span class="sxs-lookup"><span data-stu-id="9864b-164">one item should always have keyboard focus</span></span>  
  
- <span data-ttu-id="9864b-165">键盘焦点应该为可见和明显</span><span class="sxs-lookup"><span data-stu-id="9864b-165">keyboard focus should be visible and obvious</span></span>  
  
- <span data-ttu-id="9864b-166">选择和/或带有焦点的项应以可视化方式突出显示</span><span class="sxs-lookup"><span data-stu-id="9864b-166">selections and/or focused items should be visually highlighted</span></span>  
  
<a name="Support_Navigation_Standards_and_Powerful_Navigation"></a>
### <a name="support-navigation-standards-and-powerful-navigation-schemes"></a><span data-ttu-id="9864b-167">支持导航标准和功能强大的导航方案</span><span class="sxs-lookup"><span data-stu-id="9864b-167">Support Navigation Standards and Powerful Navigation Schemes</span></span>  
 <span data-ttu-id="9864b-168">键盘导航的不同方面为用户提供了用于浏览 UI 的不同方式。</span><span class="sxs-lookup"><span data-stu-id="9864b-168">Different aspects of keyboard navigation provide different ways for users to navigate the UI.</span></span>  
  
 <span data-ttu-id="9864b-169">应用程序应提供以下键盘界面：</span><span class="sxs-lookup"><span data-stu-id="9864b-169">Applications should provide the following keyboard interfaces:</span></span>  
  
- <span data-ttu-id="9864b-170">所有命令、菜单和控件的快捷键和带下划线的访问键</span><span class="sxs-lookup"><span data-stu-id="9864b-170">shortcut keys and underlined access keys for all commands, menus, and controls</span></span>  
  
- <span data-ttu-id="9864b-171">重要链接的键盘快捷键</span><span class="sxs-lookup"><span data-stu-id="9864b-171">keyboard shortcuts to important links</span></span>  
  
- <span data-ttu-id="9864b-172">所有菜单项都具有一个访问键；所有按钮都有加速键，所有命令都具有一个加速键。</span><span class="sxs-lookup"><span data-stu-id="9864b-172">all menu items have an access key; all buttons have accelerator keys, all commands have an accelerator key.</span></span>  
  
<a name="Do_not_let_Mouse_Location_Interfere_with_Keyboard"></a>
### <a name="do-not-let-mouse-location-interfere-with-keyboard-navigation"></a><span data-ttu-id="9864b-173">不要让鼠标位置干扰键盘导航</span><span class="sxs-lookup"><span data-stu-id="9864b-173">Do Not Let Mouse Location Interfere with Keyboard Navigation</span></span>  
 <span data-ttu-id="9864b-174">鼠标位置不应干扰键盘导航。</span><span class="sxs-lookup"><span data-stu-id="9864b-174">Mouse location should not interfere with keyboard navigation.</span></span> <span data-ttu-id="9864b-175">例如，如果鼠标定位在某个位置并且用户使用键盘导航，则不应发生鼠标单击，除非用户启动。</span><span class="sxs-lookup"><span data-stu-id="9864b-175">For example, if the mouse is positioned some place and the user is navigating with the keyboard, a mouse click should not happen unless initiated by the user.</span></span>  
  
<a name="Multimodal_Interface"></a>
## <a name="multimodal-interface"></a><span data-ttu-id="9864b-176">多模式界面</span><span class="sxs-lookup"><span data-stu-id="9864b-176">Multimodal Interface</span></span>  
 <span data-ttu-id="9864b-177">本节中的最佳做法可确保应用程序 UI 包含视觉对象元素的替代项。</span><span class="sxs-lookup"><span data-stu-id="9864b-177">Best Practices in this section ensure that application UI includes alternatives for visual elements.</span></span>  
  
<a name="Provide_User_Selectable_Equivalents_for_Non_Text"></a>
### <a name="provide-user-selectable-equivalents-for-non-text-elements"></a><span data-ttu-id="9864b-178">提供非文本元素的用户可选等效项</span><span class="sxs-lookup"><span data-stu-id="9864b-178">Provide User-Selectable Equivalents for Non-Text Elements</span></span>  
 <span data-ttu-id="9864b-179">对于每个非文本元素，都会提供文本、脚本或音频说明（如 alt 文本、标题或可视反馈）的用户可选等效项。</span><span class="sxs-lookup"><span data-stu-id="9864b-179">For each non-text element, provide a user-selectable equivalent for text, transcripts, or audio descriptions, such as alt text, captions, or visual feedback.</span></span>  
  
 <span data-ttu-id="9864b-180">非文本元素涵盖各种 UI 元素，包括图像、图像映射区域、动画、小程序、框架、脚本、图形按钮、声音、独立的音频文件和视频。</span><span class="sxs-lookup"><span data-stu-id="9864b-180">Non-text elements cover a wide range of UI elements including: images, image map regions, animations, applets, frames, scripts, graphical buttons, sounds, stand-alone audio files, and video.</span></span> <span data-ttu-id="9864b-181">当非文本元素包含用户需要访问的可视信息、语音或一般音频信息时，这些元素很重要，以便了解 UI 的内容。</span><span class="sxs-lookup"><span data-stu-id="9864b-181">Non-text elements are important when they contain visual information, speech, or general audio information that the user needs access to in order to understand the content of the UI.</span></span>  
  
<a name="Use_Color_but_also_Provide_Alternatives_to_Color"></a>
### <a name="use-color-but-also-provide-alternatives-to-color"></a><span data-ttu-id="9864b-182">使用颜色，且同时提供颜色的替换项</span><span class="sxs-lookup"><span data-stu-id="9864b-182">Use Color but Also Provide Alternatives to Color</span></span>  
 <span data-ttu-id="9864b-183">使用颜色来增强、强调或重申通过其他方式显示的信息，但请勿仅使用颜色传达信息。</span><span class="sxs-lookup"><span data-stu-id="9864b-183">Use color to enhance, emphasize, or reiterate information shown by other means, but do not communicate information by using color alone.</span></span> <span data-ttu-id="9864b-184">色盲或者使用单色显示的用户需要颜色的替换项。</span><span class="sxs-lookup"><span data-stu-id="9864b-184">Users who are color blind or have a monochrome display need alternatives to color.</span></span>  
  
<a name="Use_Standard_Input_APIs_with_Devices_Independent"></a>
### <a name="use-standard-input-apis-with-device-independent-calls"></a><span data-ttu-id="9864b-185">通过独立于设备的调用使用标准输入 API</span><span class="sxs-lookup"><span data-stu-id="9864b-185">Use Standard Input APIs with Device-Independent Calls</span></span>  
 <span data-ttu-id="9864b-186">独立于设备的调用确保键盘和鼠标的功能相等，同时为辅助技术提供有关 UI 的所需信息。</span><span class="sxs-lookup"><span data-stu-id="9864b-186">Device-independent calls ensure keyboard and mouse feature equality, while providing assistive technology with needed information about the UI.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9864b-187">请参阅</span><span class="sxs-lookup"><span data-stu-id="9864b-187">See also</span></span>

- <xref:System.Windows.Automation.Peers>
- <span data-ttu-id="9864b-188">[带有主题和 UI 自动化支持示例的 NumericUpDown 自定义控件](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771573(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="9864b-188">[NumericUpDown Custom Control with Theme and UI Automation Support Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771573(v=vs.90))</span></span>
- [<span data-ttu-id="9864b-189">键盘用户界面设计的准则</span><span class="sxs-lookup"><span data-stu-id="9864b-189">Guidelines for Keyboard User Interface Design</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/dnacc/guidelines-for-keyboard-user-interface-design)

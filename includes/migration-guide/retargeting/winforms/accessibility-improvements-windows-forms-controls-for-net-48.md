---
ms.openlocfilehash: e528a41748d9353c96d443f68e15e7a98ee7f4ae
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617789"
---
### <a name="accessibility-improvements-in-windows-forms-controls-for-net-48"></a><span data-ttu-id="fb6c6-101">适用于 .NET 4.8 的 Windows 窗体控件中的辅助功能改进</span><span class="sxs-lookup"><span data-stu-id="fb6c6-101">Accessibility improvements in Windows Forms controls for .NET 4.8</span></span>

#### <a name="details"></a><span data-ttu-id="fb6c6-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="fb6c6-102">Details</span></span>

<span data-ttu-id="fb6c6-103">Windows 窗体框架持续改进其与辅助功能技术的协作方式，以更好地支持 Windows 窗体客户。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-103">The Windows Forms Framework is continuing to improve how it works with accessibility technologies to better support Windows Forms customers.</span></span> <span data-ttu-id="fb6c6-104">其中包括以下更改：</span><span class="sxs-lookup"><span data-stu-id="fb6c6-104">These include the following changes:</span></span>

- <span data-ttu-id="fb6c6-105">改进高对比度模式的显示效果。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-105">Changes to improve display during High Contrast mode.</span></span>
- <span data-ttu-id="fb6c6-106">对讲述人交互的更改。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-106">Changes to interaction with Narrator.</span></span>
- <span data-ttu-id="fb6c6-107">辅助功能层次结构中的更改（通过 UI 自动化树改进导航）。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-107">Changes in the Accessible hierarchy (improving navigation through the UI Automation tree).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="fb6c6-108">建议</span><span class="sxs-lookup"><span data-stu-id="fb6c6-108">Suggestion</span></span>

<span data-ttu-id="fb6c6-109">**如何选择加入或选择退出这些更改** 为使应用程序从这些更改中获益，它必须在 .NET Framework 4.8 上运行。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-109">**How to opt in or out of these changes** In order for the application to benefit from these changes, it must run on the .NET Framework 4.8.</span></span> <span data-ttu-id="fb6c6-110">应用程序可通过以下任一方式选择加入这些更改：</span><span class="sxs-lookup"><span data-stu-id="fb6c6-110">The application can opt in into these changes in either of the following ways:</span></span>

- <span data-ttu-id="fb6c6-111">重新编译为面向 .NET Framework 4.8。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-111">It is recompiled to target the .NET Framework 4.8.</span></span> <span data-ttu-id="fb6c6-112">对于面向 .NET Framework 4.8 的 Windows 窗体应用程序，这些辅助功能更改将默认启用。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-112">These accessibility changes are enabled by default on Windows Forms applications that target the .NET Framework 4.8.</span></span>
- <span data-ttu-id="fb6c6-113">它面向 .NET Framework 4.7.2 或更低版本，通过向应用配置文件的 `<runtime>` 部分添加以下 [AppContext 开关](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element)并将其设置为 `false`，可选择弃用旧版辅助功能行为，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-113">It targets the .NET Framework 4.7.2 or earlier version and opts out of the legacy accessibility behaviors by adding the following [AppContext switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the `<runtime>` section of the app config file and setting it to `false`, as the following example shows.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
  </startup>
  <runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
  </runtime>
</configuration>
```

<span data-ttu-id="fb6c6-114">请注意，要选择加入 .NET Framework 4.8 中添加的辅助功能，还必须选择加入 .NET Framework 4.7.1 及 4.7.2 的辅助功能。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-114">Note that to opt in to the accessibility features added in .NET Framework 4.8, you must also opt in to accessibility features of .NET Framework 4.7.1 and 4.7.2 as well.</span></span> <span data-ttu-id="fb6c6-115">面向 .NET Framework 4.8 且希望保留旧版辅助功能行为的应用程序可以通过将此 AppContext 开关显式设置为 `true` 来选择加入使用旧版辅助功能。启用键盘 ToolTip 调用支持需要将 `Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false` 行添加到 AppContextSwitchOverrides 值：</span><span class="sxs-lookup"><span data-stu-id="fb6c6-115">Applications that target the .NET Framework 4.8 and want to preserve the legacy accessibility behavior can opt in to the use of legacy accessibility features by explicitly setting this AppContext switch to `true`.Enabling the keyboard ToolTip invocation support requires adding the `Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false` line to the AppContextSwitchOverrides value:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false" />
```

<span data-ttu-id="fb6c6-116">请注意，启用此功能需要选择加入上述 .NET Framework 4.7.1 到 4.8 的辅助功能。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-116">Note that enabling this feature requires opting in to the aforementioned accessibility features of .NET Framework 4.7.1 - 4.8.</span></span> <span data-ttu-id="fb6c6-117">此外，如果未选择加入任何辅助功能，但选择加入了工具提示显示功能，则首次访问这些功能时将引发运行时 <xref:System.NotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-117">Also, if any of the accessibility features are not opted in but the tooltip display feature is opted in, a runtime <xref:System.NotSupportedException> will be thrown on the first access to these features.</span></span> <span data-ttu-id="fb6c6-118">异常消息表明键盘工具提示需要启用第 3 级辅助功能改进。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-118">The exception message indicates that keyboard ToolTips require accessibility improvements of level 3 to be enabled.</span></span>

<span data-ttu-id="fb6c6-119">**在高对比度主题中使用 OS 定义的颜色**</span><span class="sxs-lookup"><span data-stu-id="fb6c6-119">**Use of OS-defined colors in High Contrast themes**</span></span>

- <span data-ttu-id="fb6c6-120">改进了高对比度主题。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-120">Improved high-contrast themes.</span></span>

<span data-ttu-id="fb6c6-121">**改进了讲述人支持**</span><span class="sxs-lookup"><span data-stu-id="fb6c6-121">**Improved Narrator support**</span></span>

- <span data-ttu-id="fb6c6-122">在说出 <xref:System.Windows.Forms.DataGridViewCell> 的辅助功能名称时，讲述人现在会说出 <xref:System.Windows.Forms.DataGridViewColumn> 的排序方向。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-122">Narrator now announces the sort direction of the <xref:System.Windows.Forms.DataGridViewColumn> when announcing an accessible name of a <xref:System.Windows.Forms.DataGridViewCell>.</span></span>

<span data-ttu-id="fb6c6-123">**改进了 CheckedListBox 辅助功能支持**</span><span class="sxs-lookup"><span data-stu-id="fb6c6-123">**Improved CheckedListBox Accessibility support**</span></span>

- <span data-ttu-id="fb6c6-124">改进了 <xref:System.Windows.Forms.CheckedListBox> 控件的讲述人支持。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-124">Improved Narrator support for the <xref:System.Windows.Forms.CheckedListBox> control.</span></span> <span data-ttu-id="fb6c6-125">使用键盘导航到 <xref:System.Windows.Forms.CheckedListBox> 控件时，讲述人会聚焦 <xref:System.Windows.Forms.CheckedListBox> 项并说出该项。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-125">When navigating to the <xref:System.Windows.Forms.CheckedListBox> control using the keyboard, Narrator focuses the <xref:System.Windows.Forms.CheckedListBox> item and announces it.</span></span>
- <span data-ttu-id="fb6c6-126">控件变得聚焦时，空的 CheckedListBox 控件现包含为第一个虚拟项绘制的焦点矩形。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-126">An empty CheckedListBox control now has a focus rectangle drawn for a virtual first item when the control becomes focused.</span></span>

<span data-ttu-id="fb6c6-127">**改进了 ComboBox 辅助功能支持**</span><span class="sxs-lookup"><span data-stu-id="fb6c6-127">**Improved ComboBox Accessibility support**</span></span>

- <span data-ttu-id="fb6c6-128">为 <xref:System.Windows.Forms.ComboBox> 控件启用了 UI 自动化支持，并且可以使用 UI 自动化通知和其他 UI 自动化功能。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-128">Enabled UI Automation support for the <xref:System.Windows.Forms.ComboBox> control, with the ability to use UI Automation notifications and other UI Automation features.</span></span>
<span data-ttu-id="fb6c6-129">**改进了 DataGridView 辅助功能支持**</span><span class="sxs-lookup"><span data-stu-id="fb6c6-129">**Improved DataGridView Accessibility support**</span></span>

- <span data-ttu-id="fb6c6-130">为 <xref:System.Windows.Forms.DataGridView> 控件启用了 UI 自动化支持，并且可以使用 UI 自动化通知和其他 UI 自动化功能。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-130">Enabled UI Automation support for <xref:System.Windows.Forms.DataGridView> control with ability to use UI Automation notifications and other UI Automation features.</span></span>
- <span data-ttu-id="fb6c6-131">对应于 <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl> 或 <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl> 的 UI 自动化元素现在是相应编辑单元的子元素。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-131">The UI Automation element which corresponds to the <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl> or <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl> is now a child of corresponding editing cell.</span></span>

<span data-ttu-id="fb6c6-132">**改进了 LinkLabel 辅助功能支持**</span><span class="sxs-lookup"><span data-stu-id="fb6c6-132">**Improved LinkLabel Accessibility support**</span></span>

- <span data-ttu-id="fb6c6-133">改进了 <xref:System.Windows.Forms.LinkLabel> 控件辅助功能：如果禁用了对应的 <xref:System.Windows.Forms.LinkLabel> 控件，讲述人会指示链接的禁用状态。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-133">Improved <xref:System.Windows.Forms.LinkLabel> control accessibility: Narrator announces the disabled state for the link if the corresponding <xref:System.Windows.Forms.LinkLabel> control is disabled.</span></span>

<span data-ttu-id="fb6c6-134">**改进了 ProgressBar 辅助功能支持**</span><span class="sxs-lookup"><span data-stu-id="fb6c6-134">**Improved ProgressBar Accessibility support**</span></span>

- <span data-ttu-id="fb6c6-135">为 <xref:System.Windows.Forms.ProgressBar> 控件启用了 UI 自动化支持，并且可以使用 UI 自动化通知和其他 UI 自动化功能。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-135">Enabled UI Automation support for the <xref:System.Windows.Forms.ProgressBar> control with the ability to use UI Automation notifications and other UI Automation features.</span></span> <span data-ttu-id="fb6c6-136">开发人员现可使用 UI 自动化通知，讲述人可以通过这些通知来指示进度。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-136">Developers are now able to use UI Automation notifications which Narrator can announce to indicate progress.</span></span>
<span data-ttu-id="fb6c6-137">有关 UI 自动化事件概述（包括 UI 自动化通知事件）的概述，请参阅 [UI 自动化事件概述](https://docs.microsoft.com/windows/desktop/WinAuto/uiauto-eventsoverview)。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-137">For an overview of UI automation events overview, including UI automation notification events, see the [UI Automation Events Overview](https://docs.microsoft.com/windows/desktop/WinAuto/uiauto-eventsoverview).</span></span>

<span data-ttu-id="fb6c6-138">**改进了 PropertyGrid 辅助功能支持**</span><span class="sxs-lookup"><span data-stu-id="fb6c6-138">**Improved PropertyGrid Accessibility support**</span></span>

- <span data-ttu-id="fb6c6-139">为 <xref:System.Windows.Forms.PropertyGrid> 控件启用了 UI 自动化支持，并且可以使用 UI 自动化通知和其他 UI 自动化功能。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-139">Enabled UI Automation support for the <xref:System.Windows.Forms.PropertyGrid> control, with the ability to use UI Automation notifications and other UI Automation features.</span></span>
- <span data-ttu-id="fb6c6-140">与当前编辑的属性对应的 UI 自动化元素现在是对应属性项 UI 自动化元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-140">The UI Automation element which corresponds to the currently edited property is now a child of the corresponding property item UI Automation element.</span></span>
- <span data-ttu-id="fb6c6-141">如果父 <xref:System.Windows.Forms.PropertyGrid> 控件设置为类别视图，则 UI 自动化属性项元素现在是对应类别元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-141">The UI Automation property item element is now a child of the corresponding category element if the parent <xref:System.Windows.Forms.PropertyGrid> control is set to category view.</span></span>

<span data-ttu-id="fb6c6-142">**改进了 ToolStrip 支持**</span><span class="sxs-lookup"><span data-stu-id="fb6c6-142">**Improved ToolStrip support**</span></span>

- <span data-ttu-id="fb6c6-143">为 <xref:System.Windows.Forms.ToolStrip> 控件启用了 UI 自动化支持，并且可以使用 UI 自动化通知和其他 UI 自动化功能。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-143">Enabled UI Automation support for the <xref:System.Windows.Forms.ToolStrip> control, with the ability to use UI Automation notifications and other UI Automation features.</span></span>
- <span data-ttu-id="fb6c6-144">改进了对 <xref:System.Windows.Forms.ToolStrip> 项的导航。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-144">Improved navigation through <xref:System.Windows.Forms.ToolStrip> items.</span></span>
- <span data-ttu-id="fb6c6-145">在项模式下，讲述人焦点不会消失，也不会转到隐藏项。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-145">In items mode, Narrator focus does not disappear and does not go to hidden items.</span></span>

<span data-ttu-id="fb6c6-146">**改进了视觉提示**</span><span class="sxs-lookup"><span data-stu-id="fb6c6-146">**Improved Visual cues**</span></span>

- <span data-ttu-id="fb6c6-147">空的 <xref:System.Windows.Forms.CheckedListBox> 控件现在在接收焦点时显示焦点指示器。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-147">An empty <xref:System.Windows.Forms.CheckedListBox> control now displays a focus indicator when it receives focus.</span></span>
<span data-ttu-id="fb6c6-148">注意：在运行时为控件启用了 UI 自动化支持，但设计时未使用该支持。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-148">Note: UI automation support is enabled for controls in runtime but is not used in design time.</span></span> <span data-ttu-id="fb6c6-149">有关 UI 自动化的概述，请参阅 [UI 自动化概述](https://docs.microsoft.com/dotnet/framework/ui-automation/ui-automation-overview)。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-149">For an overview of UI automation, see the [UI Automation Overview](https://docs.microsoft.com/dotnet/framework/ui-automation/ui-automation-overview).</span></span>

<span data-ttu-id="fb6c6-150">**通过键盘调用控件的工具提示**</span><span class="sxs-lookup"><span data-stu-id="fb6c6-150">**Invoking controls' ToolTips with a keyboard**</span></span>

- <span data-ttu-id="fb6c6-151">现可通过使用键盘聚焦控件来调用控件工具提示。</span><span class="sxs-lookup"><span data-stu-id="fb6c6-151">Control tooltip can now be invoked by focusing the control with keyboard.</span></span> <span data-ttu-id="fb6c6-152">应用程序必须显式启用此功能（请参阅 **&quot;如何选择加入或退出这些更改&quot;** 部分）</span><span class="sxs-lookup"><span data-stu-id="fb6c6-152">This feature needs to be enabled explicitly for the application (see section **&quot;How to opt in or out of these changes&quot;**)</span></span>

| <span data-ttu-id="fb6c6-153">“属性”</span><span class="sxs-lookup"><span data-stu-id="fb6c6-153">Name</span></span>    | <span data-ttu-id="fb6c6-154">“值”</span><span class="sxs-lookup"><span data-stu-id="fb6c6-154">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fb6c6-155">范围</span><span class="sxs-lookup"><span data-stu-id="fb6c6-155">Scope</span></span>   | <span data-ttu-id="fb6c6-156">主要</span><span class="sxs-lookup"><span data-stu-id="fb6c6-156">Major</span></span>       |
| <span data-ttu-id="fb6c6-157">Version</span><span class="sxs-lookup"><span data-stu-id="fb6c6-157">Version</span></span> | <span data-ttu-id="fb6c6-158">4.8</span><span class="sxs-lookup"><span data-stu-id="fb6c6-158">4.8</span></span>         |
| <span data-ttu-id="fb6c6-159">类型</span><span class="sxs-lookup"><span data-stu-id="fb6c6-159">Type</span></span>    | <span data-ttu-id="fb6c6-160">重定目标</span><span class="sxs-lookup"><span data-stu-id="fb6c6-160">Retargeting</span></span> |

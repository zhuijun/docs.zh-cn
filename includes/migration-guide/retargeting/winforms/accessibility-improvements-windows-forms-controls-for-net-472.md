---
ms.openlocfilehash: cc3c2c2be179842f87be8892d057a6c4138086cb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614398"
---
### <a name="accessibility-improvements-in-windows-forms-controls-for-net-472"></a><span data-ttu-id="1d454-101">适用于 .NET 4.7.2 的 Windows 窗体控件中的辅助功能改进</span><span class="sxs-lookup"><span data-stu-id="1d454-101">Accessibility improvements in Windows Forms controls for .NET 4.7.2</span></span>

#### <a name="details"></a><span data-ttu-id="1d454-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="1d454-102">Details</span></span>

<span data-ttu-id="1d454-103">Windows 窗体框架正在改进其辅助功能技术的工作方式，以更好地支持 Windows 窗体客户。</span><span class="sxs-lookup"><span data-stu-id="1d454-103">Windows Forms Framework is improving how it works with accessibility technologies to better support Windows Forms customers.</span></span> <span data-ttu-id="1d454-104">其中包括以下更改：</span><span class="sxs-lookup"><span data-stu-id="1d454-104">These include the following changes:</span></span>

- <span data-ttu-id="1d454-105">改进高对比度模式的显示效果。</span><span class="sxs-lookup"><span data-stu-id="1d454-105">Changes to improve display during High Contrast mode.</span></span>
- <span data-ttu-id="1d454-106">用于改进 DataGridView 和 MenuStrip 控件中的键盘导航的更改。</span><span class="sxs-lookup"><span data-stu-id="1d454-106">Changes to improve the keyboard navigation in the DataGridView and MenuStrip controls.</span></span>
- <span data-ttu-id="1d454-107">对讲述人交互的更改。</span><span class="sxs-lookup"><span data-stu-id="1d454-107">Changes to interaction with Narrator.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1d454-108">建议</span><span class="sxs-lookup"><span data-stu-id="1d454-108">Suggestion</span></span>

<span data-ttu-id="1d454-109">**如何选择启用或选择弃用这些更改** 为使应用程序从这些更改获益，它必须在 .NET Framework 4.7.2 或更高版本上运行。</span><span class="sxs-lookup"><span data-stu-id="1d454-109">**How to opt in or out of these changes** In order for the application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later.</span></span> <span data-ttu-id="1d454-110">此应用程序可通过以下任何一种方式从这些更改中获益：</span><span class="sxs-lookup"><span data-stu-id="1d454-110">The application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="1d454-111">重新编译为面向 .NET Framework 4.7.2。</span><span class="sxs-lookup"><span data-stu-id="1d454-111">It is recompiled to target the .NET Framework 4.7.2.</span></span> <span data-ttu-id="1d454-112">对于面向 .NET Framework 4.7.2 或更高版本的 Windows 窗体 应用程序，这些辅助功能更改将默认启用。</span><span class="sxs-lookup"><span data-stu-id="1d454-112">These accessibility changes are enabled by default on Windows Forms applications that target the .NET Framework 4.7.2 or later.</span></span>
- <span data-ttu-id="1d454-113">它面向 .NET Framework 4.7.1 或更早版本，通过向 app config 文件的 `<runtime>` 部分添加以下 [AppContext 开关](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element)并将其设置为 `false`，可选择弃用旧版辅助功能行为，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="1d454-113">It targets the .NET Framework 4.7.1 or earlier version and opts out of the legacy accessibility behaviors by adding the following [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the `<runtime>` section of the app config file and setting it to `false`, as the following example shows.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
  </startup>
  <runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
  </runtime>
</configuration>
```

<span data-ttu-id="1d454-114">请注意，要选择启用 .NET Framework 4.7.2 中添加的辅助功能，还必须选择启用 .NET Framework 4.7.1 的辅助功能。</span><span class="sxs-lookup"><span data-stu-id="1d454-114">Note that to opt in to the accessibility features added in .NET Framework 4.7.2, you must also opt in to accessibility features of .NET Framework 4.7.1 as well.</span></span> <span data-ttu-id="1d454-115">面向 .NET Framework 4.7.2 或更高版本并希望保留旧版辅助功能行为的应用程序，可通过将此 AppContext 开关显式设置为 `true` 来选择启用旧版辅助功能。</span><span class="sxs-lookup"><span data-stu-id="1d454-115">Applications that target the .NET Framework 4.7.2 or later and want to preserve the legacy accessibility behavior can opt in to the use of legacy accessibility features by explicitly setting this AppContext switch to `true`.</span></span>

<span data-ttu-id="1d454-116">**在高对比度主题中使用 OS 定义的颜色**</span><span class="sxs-lookup"><span data-stu-id="1d454-116">**Use of OS-defined colors in High Contrast themes**</span></span>

- <span data-ttu-id="1d454-117"><xref:System.Windows.Forms.ToolStripDropDownButton> 的下拉菜单现在在高对比度主题中使用 OS 定义的颜色。</span><span class="sxs-lookup"><span data-stu-id="1d454-117">The drop down arrow of the <xref:System.Windows.Forms.ToolStripDropDownButton> now uses OS-defined colors in High Contrast theme.</span></span>
- <span data-ttu-id="1d454-118">现在，在高对比度主题中选中将 <xref:System.Windows.Forms.Button>、<xref:System.Windows.Forms.RadioButton> 和 <xref:System.Windows.Forms.CheckBox> 控件的 <xref:System.Windows.Forms.ButtonBase.FlatStyle> 设置为 <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> 或 <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType> 时，它们会使用 OS 定义的颜色。</span><span class="sxs-lookup"><span data-stu-id="1d454-118"><xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with <xref:System.Windows.Forms.ButtonBase.FlatStyle> set to <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> or <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType> now use OS-defined colors in High Contrast theme when selected.</span></span> <span data-ttu-id="1d454-119">以前，文本和背景颜色对比度低，难以阅读。</span><span class="sxs-lookup"><span data-stu-id="1d454-119">Previously, text and background colors were not contrasting and were hard to read.</span></span>
- <span data-ttu-id="1d454-120">包含在 <xref:System.Windows.Forms.GroupBox>（其 <xref:System.Windows.Forms.Control.Enabled> 属性设置为 `false`）中的控件现在将在高对比度主题中使用 OS 定义的颜色。</span><span class="sxs-lookup"><span data-stu-id="1d454-120">Controls contained within a <xref:System.Windows.Forms.GroupBox> that has its <xref:System.Windows.Forms.Control.Enabled> property set to `false` will now use OS-defined colors in High Contrast theme.</span></span>
- <span data-ttu-id="1d454-121">在高对比度模式下，<xref:System.Windows.Forms.ToolStripButton>、<xref:System.Windows.Forms.ToolStripComboBox> 和 <xref:System.Windows.Forms.ToolStripDropDownButton> 控件的亮度对比度提高。</span><span class="sxs-lookup"><span data-stu-id="1d454-121">The <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, and <xref:System.Windows.Forms.ToolStripDropDownButton> controls have an increased luminosity contrast ratio in High Contrast Mode.</span></span>
- <span data-ttu-id="1d454-122">对于 <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor?displayProperty=nameWithType> 属性，<xref:System.Windows.Forms.DataGridViewLinkCell> 将默认使用高对比模式下 OS 定义的颜色。</span><span class="sxs-lookup"><span data-stu-id="1d454-122"><xref:System.Windows.Forms.DataGridViewLinkCell> will by default use OS-defined colors in High Contrast mode for the <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor?displayProperty=nameWithType> property.</span></span>
<span data-ttu-id="1d454-123">注意：Windows 10 已更改部分高对比度系统颜色的值。</span><span class="sxs-lookup"><span data-stu-id="1d454-123">NOTE: Windows 10 has changed values for some high contrast system colors.</span></span> <span data-ttu-id="1d454-124">Windows 窗体框架基于 Win32 框架。</span><span class="sxs-lookup"><span data-stu-id="1d454-124">Windows Forms Framework is based on the Win32 framework.</span></span> <span data-ttu-id="1d454-125">为获得最佳体验，请运行最新版本的 Windows，并通过在测试应用程序中添加 app.manifest 文件选择使用最新的 OS 更改，同时取消注释以下代码：</span><span class="sxs-lookup"><span data-stu-id="1d454-125">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-commenting the following code:</span></span>

```xml
<!-- Windows 10 -->
<supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
```

<span data-ttu-id="1d454-126">**改进了讲述人支持**</span><span class="sxs-lookup"><span data-stu-id="1d454-126">**Improved Narrator support**</span></span>

- <span data-ttu-id="1d454-127">现在，讲述人将在公布 <xref:System.Windows.Forms.ToolStripMenuItem> 的文本时公布 <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> 属性的值。</span><span class="sxs-lookup"><span data-stu-id="1d454-127">Narrator now announces the value of the <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> property when announcing the text of a <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>
- <span data-ttu-id="1d454-128">当 <xref:System.Windows.Forms.ToolStripMenuItem> 的 <xref:System.Windows.Forms.Control.Enabled> 属性设置为 `false` 时，讲述人现在会有所指示。</span><span class="sxs-lookup"><span data-stu-id="1d454-128">Narrator now indicates when a <xref:System.Windows.Forms.ToolStripMenuItem> has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>
- <span data-ttu-id="1d454-129">当 <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> 属性设置为 `true` 时，讲述人现在会针对复选框的状态给出反馈。</span><span class="sxs-lookup"><span data-stu-id="1d454-129">Narrator now gives feedback on the state of a check box when the <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> property is set to `true`.</span></span>
- <span data-ttu-id="1d454-130">讲述人扫描模式焦点顺序现在与 ClickOnce 下载对话框窗口中控件的视觉顺序一致。</span><span class="sxs-lookup"><span data-stu-id="1d454-130">Narrator Scan Mode focus order is now consistent with the visual order of the controls on the ClickOnce download dialog window.</span></span>

<span data-ttu-id="1d454-131">**改进了 DataGridView 辅助功能支持**</span><span class="sxs-lookup"><span data-stu-id="1d454-131">**Improved DataGridView Accessibility support**</span></span>

- <span data-ttu-id="1d454-132"><xref:System.Windows.Forms.DataGridView> 中的行现在可使用键盘进行排序。</span><span class="sxs-lookup"><span data-stu-id="1d454-132">Rows in a <xref:System.Windows.Forms.DataGridView> can now be sorted using the keyboard.</span></span> <span data-ttu-id="1d454-133">现在用户可使用 F3 键按当前列排序。</span><span class="sxs-lookup"><span data-stu-id="1d454-133">Now a user can use the F3 key in order to sort by the current column.</span></span>
- <span data-ttu-id="1d454-134">若 <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> 设置为 <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>，当用户按 Tab 键遍历当前行中的单元格时，列标题将更改颜色来指示当前列。</span><span class="sxs-lookup"><span data-stu-id="1d454-134">When the <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> is set to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, the column header will change color to indicate the current column as the user tabs through the cells in the current row.</span></span>
- <span data-ttu-id="1d454-135"><xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Parent?displayProperty=nameWithType> 属性现在返回正确的父控件。</span><span class="sxs-lookup"><span data-stu-id="1d454-135">The <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Parent?displayProperty=nameWithType> property now returns the correct parent control.</span></span>

<span data-ttu-id="1d454-136">**改进了视觉提示**</span><span class="sxs-lookup"><span data-stu-id="1d454-136">**Improved Visual cues**</span></span>

- <span data-ttu-id="1d454-137">具有空 <xref:System.Windows.Forms.ButtonBase.Text> 属性的 <xref:System.Windows.Forms.RadioButton> 和 <xref:System.Windows.Forms.CheckBox> 控件现在将在接收到焦点时显示焦点指示器。</span><span class="sxs-lookup"><span data-stu-id="1d454-137">The <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with an empty <xref:System.Windows.Forms.ButtonBase.Text> property will now display a focus indicator when they receive focus.</span></span>

<span data-ttu-id="1d454-138">**改进了属性网格支持**</span><span class="sxs-lookup"><span data-stu-id="1d454-138">**Improved Property Grid Support**</span></span>

- <span data-ttu-id="1d454-139">现在，仅在 PropertyGrid 元素启用时，<xref:System.Windows.Forms.PropertyGrid> 控件子元素才会为 <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> 属性返回 `true`。</span><span class="sxs-lookup"><span data-stu-id="1d454-139">The <xref:System.Windows.Forms.PropertyGrid> control child elements now return a `true` for the  <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> property only when a PropertyGrid element is enabled.</span></span>
- <span data-ttu-id="1d454-140">现在，仅在用户可更改 PropertyGrid 元素时，<xref:System.Windows.Forms.PropertyGrid> 控件子元素才会为 <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> 属性返回 `false`。</span><span class="sxs-lookup"><span data-stu-id="1d454-140">The <xref:System.Windows.Forms.PropertyGrid> control child elements now return a `false` for the <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> property only when a PropertyGrid element can be changed by the user.</span></span>
<span data-ttu-id="1d454-141">有关 UI 自动化的概述，请参阅 [UI 自动化概述](https://docs.microsoft.com/dotnet/framework/ui-automation/ui-automation-overview)。</span><span class="sxs-lookup"><span data-stu-id="1d454-141">For an overview of UI automation, see the [UI Automation Overview](https://docs.microsoft.com/dotnet/framework/ui-automation/ui-automation-overview).</span></span></p><span data-ttu-id="1d454-142">**改进了的键盘导航**</span><span class="sxs-lookup"><span data-stu-id="1d454-142">**Improved keyboard navigation**</span></span>

- <span data-ttu-id="1d454-143"><xref:System.Windows.Forms.ToolStripButton> 包含在将 <xref:System.Windows.Forms.ToolStripPanel.TabStop> 属性设置为 `true` 的 <xref:System.Windows.Forms.ToolStripPanel> 中时，现在允许聚焦。</span><span class="sxs-lookup"><span data-stu-id="1d454-143"><xref:System.Windows.Forms.ToolStripButton> now allows focus when contained within a <xref:System.Windows.Forms.ToolStripPanel> that has the <xref:System.Windows.Forms.ToolStripPanel.TabStop> property set to `true`.</span></span>

| <span data-ttu-id="1d454-144">“属性”</span><span class="sxs-lookup"><span data-stu-id="1d454-144">Name</span></span>    | <span data-ttu-id="1d454-145">“值”</span><span class="sxs-lookup"><span data-stu-id="1d454-145">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1d454-146">范围</span><span class="sxs-lookup"><span data-stu-id="1d454-146">Scope</span></span>   | <span data-ttu-id="1d454-147">主要</span><span class="sxs-lookup"><span data-stu-id="1d454-147">Major</span></span>       |
| <span data-ttu-id="1d454-148">Version</span><span class="sxs-lookup"><span data-stu-id="1d454-148">Version</span></span> | <span data-ttu-id="1d454-149">4.7.2</span><span class="sxs-lookup"><span data-stu-id="1d454-149">4.7.2</span></span>       |
| <span data-ttu-id="1d454-150">类型</span><span class="sxs-lookup"><span data-stu-id="1d454-150">Type</span></span>    | <span data-ttu-id="1d454-151">重定目标</span><span class="sxs-lookup"><span data-stu-id="1d454-151">Retargeting</span></span> |

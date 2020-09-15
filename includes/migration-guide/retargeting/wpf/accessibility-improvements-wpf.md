---
ms.openlocfilehash: 895d09e4ec39bd4a92ed1f4910da80474334d99b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497253"
---
### <a name="accessibility-improvements-in-wpf"></a><span data-ttu-id="4e9d4-101">WPF 中辅助功能的改进</span><span class="sxs-lookup"><span data-stu-id="4e9d4-101">Accessibility improvements in WPF</span></span>

#### <a name="details"></a><span data-ttu-id="4e9d4-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="4e9d4-102">Details</span></span>

<span data-ttu-id="4e9d4-103">**高对比度改进**</span><span class="sxs-lookup"><span data-stu-id="4e9d4-103">**High Contrast improvements**</span></span>

- <span data-ttu-id="4e9d4-104"><xref:System.Windows.Controls.Expander> 控件的焦点现在可见。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-104">The focus for the <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="4e9d4-105">在先前版本的 .NET Framework 中，并非如此。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-105">In previous versions of .NET Framework, it was not.</span></span>
- <span data-ttu-id="4e9d4-106"><xref:System.Windows.Controls.CheckBox> 和 <xref:System.Windows.Controls.RadioButton> 控件中的文本在选中时，比之前的 .NET Framework 版本更易查看。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-106">The text in <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls when they are selected is now easier to see than in previous .NET Framework versions.</span></span>
- <span data-ttu-id="4e9d4-107">现在已禁用的 <xref:System.Windows.Controls.ComboBox> 的边框颜色与已禁用的文本颜色相同。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-107">The border of a disabled <xref:System.Windows.Controls.ComboBox> is now the same color as the disabled text.</span></span> <span data-ttu-id="4e9d4-108">在先前版本的 .NET Framework 中，并非如此。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-108">In previous versions of .NET Framework, it was not.</span></span>
- <span data-ttu-id="4e9d4-109">禁用和聚焦的按钮现在使用正确的主题颜色。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-109">Disabled and focused buttons now use the correct theme color.</span></span> <span data-ttu-id="4e9d4-110">在先前版本的 .NET Framework 中，并未如此。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-110">In previous versions of .NET Framework, they did not.</span></span>
- <span data-ttu-id="4e9d4-111">当 <xref:System.Windows.Controls.ComboBox> 控件的样式设置为 <xref:System.Windows.Controls.ToolBar.ComboBoxStyleKey?displayProperty=nameWithType> 时，下拉按钮现在可见。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-111">The dropdown button is now visible when a <xref:System.Windows.Controls.ComboBox> control's style is set to <xref:System.Windows.Controls.ToolBar.ComboBoxStyleKey?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4e9d4-112">在先前版本的 .NET Framework 中，并非如此。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-112">In previous versions of .NET Framework, it was not.</span></span>
- <span data-ttu-id="4e9d4-113"><xref:System.Windows.Controls.DataGrid> 控件中的排序指示器箭头现在可使用主题颜色。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-113">The sort indicator arrow in a <xref:System.Windows.Controls.DataGrid> control now uses theme colors.</span></span> <span data-ttu-id="4e9d4-114">在先前版本的 .NET Framework 中，并非如此。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-114">In previous versions of .NET Framework, it did not.</span></span>
- <span data-ttu-id="4e9d4-115">默认超链接样式更改为在鼠标悬停时显示正确的主题颜色。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-115">The default hyperlink style now changes to the correct theme color on mouse over.</span></span> <span data-ttu-id="4e9d4-116">在先前版本的 .NET Framework 中，并非如此。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-116">In previous versions of .NET Framework, it did not.</span></span>
- <span data-ttu-id="4e9d4-117">单选按钮上的键盘焦点现在可见。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-117">The Keyboard focus on radio buttons is now visible.</span></span> <span data-ttu-id="4e9d4-118">在先前版本的 .NET Framework 中，并非如此。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-118">In previous versions of .NET Framework, it was not.</span></span>
- <span data-ttu-id="4e9d4-119">现在 <xref:System.Windows.Controls.DataGrid> 控件的复选框列对键盘焦点反馈使用预期的颜色。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-119">The <xref:System.Windows.Controls.DataGrid> control's checkbox column now uses the expected colors for keyboard focus feedback.</span></span> <span data-ttu-id="4e9d4-120">在先前版本的 .NET Framework 中，并非如此。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-120">In previous versions of .NET Framework, it did not.</span></span>
- <span data-ttu-id="4e9d4-121">现在，键盘焦点视觉对象在 <xref:System.Windows.Controls.ComboBox> 和 <xref:System.Windows.Controls.ListBox> 控件上可见。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-121">the Keyboard focus visuals are now visible on <xref:System.Windows.Controls.ComboBox> and <xref:System.Windows.Controls.ListBox> controls.</span></span> <span data-ttu-id="4e9d4-122">在先前版本的 .NET Framework 中，并非如此。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-122">In previous versions of .NET Framework, it was not.</span></span>

<span data-ttu-id="4e9d4-123">**屏幕阅读器交互改进**</span><span class="sxs-lookup"><span data-stu-id="4e9d4-123">**Screen reader interaction improvements**</span></span>

- <span data-ttu-id="4e9d4-124">屏幕阅读器现在正确地将 <xref:System.Windows.Controls.Expander> 控件称为组（展开/折叠）。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-124"><xref:System.Windows.Controls.Expander> controls are now correctly announced as groups (expand/collapse) by screen readers.</span></span>
- <span data-ttu-id="4e9d4-125">屏幕阅读器现在正确地将 <xref:System.Windows.Controls.DataGridCell> 控件称为数据网格单元格（已本地化）。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-125"><xref:System.Windows.Controls.DataGridCell> controls are now correctly announced as data grid cell (localized) by screen readers.</span></span>
- <span data-ttu-id="4e9d4-126">屏幕阅读器现在将宣布可编辑的 <xref:System.Windows.Controls.ComboBox> 的名称。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-126">Screen readers will now announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>
- <span data-ttu-id="4e9d4-127">屏幕阅读器不再将 <xref:System.Windows.Controls.PasswordBox> 控件读作“视图中没有任何项”。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-127"><xref:System.Windows.Controls.PasswordBox> controls are no longer announced as "no item in view" by screen readers.</span></span>

<span data-ttu-id="4e9d4-128">**LiveRegion 支持**</span><span class="sxs-lookup"><span data-stu-id="4e9d4-128">**LiveRegion support**</span></span>

<span data-ttu-id="4e9d4-129">屏幕阅读器（例如讲述人）可帮助用户理解应用程序的用户界面 (UI)，这通常是通过描述当前具有焦点的 UI 元素来实现的。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-129">Screen readers, such as Narrator, help people understand the user interface (UI) of an application, usually by describing the UI element that currently has focus.</span></span> <span data-ttu-id="4e9d4-130">但是，如果 UI 元素更改了屏幕中某些地方，并且不具有焦点，则用户可能不会收到通知，并且错过重要信息。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-130">However, if a UI element changes somewhere in the screen and it does not have the focus, the user may not be informed and miss important information.</span></span> <span data-ttu-id="4e9d4-131">LiveRegions 旨在解决此问题。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-131">LiveRegions are meant to solve this problem.</span></span> <span data-ttu-id="4e9d4-132">开发人员可使用它们来通知屏幕阅读器或任何其他 [UI 自动化](~/docs/framework/ui-automation/ui-automation-overview.md)客户端 UI 元素有重要更改。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-132">A developer can use them to inform the screen reader or any other [UI Automation](~/docs/framework/ui-automation/ui-automation-overview.md) client that an important change has been made to a UI element.</span></span> <span data-ttu-id="4e9d4-133">然后，屏幕阅读器可确定向用户通知此更改的方式和时间。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-133">The screen reader can then decide how and when to inform the user of this change.</span></span> <span data-ttu-id="4e9d4-134">LiveSetting 属性还让屏幕阅读器知道了向用户通知 UI 更改的重要性。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-134">The LiveSetting property also lets the screen reader know how important it is to inform the user of the change made to the UI.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4e9d4-135">建议</span><span class="sxs-lookup"><span data-stu-id="4e9d4-135">Suggestion</span></span>

<span data-ttu-id="4e9d4-136">**如何选择启用或弃用这些更改**</span><span class="sxs-lookup"><span data-stu-id="4e9d4-136">**How to opt in or out of these changes**</span></span>

<span data-ttu-id="4e9d4-137">为了使应用程序从这些更改中获益，它必须在 .NET Framework 4.7.1 或更高版本上运行。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-137">In order for the application to benefit from these changes, it must run on .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="4e9d4-138">此应用程序可通过以下任何一种方式从这些更改中获益：</span><span class="sxs-lookup"><span data-stu-id="4e9d4-138">The application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="4e9d4-139">面向 .NET Framework 4.7.1。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-139">Target .NET Framework 4.7.1.</span></span> <span data-ttu-id="4e9d4-140">此为推荐方法。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-140">This is the recommended approach.</span></span> <span data-ttu-id="4e9d4-141">对于面向 .NET Framework 4.7.1 或更高版本的 WPF 应用程序，这些辅助功能默认启用。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-141">These accessibility changes are enabled by default on WPF applications that target .NET Framework 4.7.1 or later.</span></span>
- <span data-ttu-id="4e9d4-142">通过向应用配置文件的 `<runtime>` 部分添加以下 [AppContext 开关](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)并将其设置为 `false`，可选择弃用旧版辅助功能行为，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-142">It opts out of the legacy accessibility behaviors by adding the following [AppContext Switch](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) in the `<runtime>` section of the app config file and setting it to `false`, as the following example shows.</span></span>

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
    </startup>
    <runtime>
      <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false'  -->
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
    </runtime>
  </configuration>
  ```

<span data-ttu-id="4e9d4-143">如果应用程序面向 .NET Framework 4.7.1 或更高版本并希望保留旧版辅助功能行为，则它们可通过将此 AppContext 开关显式设置为 `true` 来选择启用旧版辅助功能。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-143">Applications that target .NET Framework 4.7.1 or later and want to preserve the legacy accessibility behavior can opt in to the use of legacy accessibility features by explicitly setting this AppContext switch to `true`.</span></span>
<span data-ttu-id="4e9d4-144">有关 UI 自动化的概述，请参阅 [UI 自动化概述](~/docs/framework/ui-automation/ui-automation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4e9d4-144">For an overview of UI automation, see [UI Automation Overview](~/docs/framework/ui-automation/ui-automation-overview.md).</span></span>

| <span data-ttu-id="4e9d4-145">名称</span><span class="sxs-lookup"><span data-stu-id="4e9d4-145">Name</span></span>    | <span data-ttu-id="4e9d4-146">值</span><span class="sxs-lookup"><span data-stu-id="4e9d4-146">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4e9d4-147">范围</span><span class="sxs-lookup"><span data-stu-id="4e9d4-147">Scope</span></span>   | <span data-ttu-id="4e9d4-148">主要</span><span class="sxs-lookup"><span data-stu-id="4e9d4-148">Major</span></span>       |
| <span data-ttu-id="4e9d4-149">Version</span><span class="sxs-lookup"><span data-stu-id="4e9d4-149">Version</span></span> | <span data-ttu-id="4e9d4-150">4.7.1</span><span class="sxs-lookup"><span data-stu-id="4e9d4-150">4.7.1</span></span>       |
| <span data-ttu-id="4e9d4-151">类型</span><span class="sxs-lookup"><span data-stu-id="4e9d4-151">Type</span></span>    | <span data-ttu-id="4e9d4-152">重定目标</span><span class="sxs-lookup"><span data-stu-id="4e9d4-152">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="4e9d4-153">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="4e9d4-153">Affected APIs</span></span>

- <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting(System.Windows.DependencyObject,System.Windows.Automation.AutomationLiveSetting)?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting(System.Windows.DependencyObject)?displayProperty=nameWithType>
- <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore?displayProperty=nameWithType>

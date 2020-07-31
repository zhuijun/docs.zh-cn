---
title: .NET Framework 中辅助功能的新增功能
description: 请参阅从 .NET Framework 4.7.1 开始的 .NET 辅助功能的新增功能。 利用辅助功能，应用可以为辅助技术用户提供正确的体验。
ms.custom: updateeachrelease
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
ms.openlocfilehash: 593591ca340cc130a3a6d1daa015a849b8eca0f8
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925834"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="69585-104">.NET Framework 中辅助功能的新增功能</span><span class="sxs-lookup"><span data-stu-id="69585-104">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="69585-105">.NET Framework 旨在让用户更轻松地使用应用程序。</span><span class="sxs-lookup"><span data-stu-id="69585-105">The .NET Framework aims at making applications more accessible for your users.</span></span> <span data-ttu-id="69585-106">辅助功能使应用程序能够为辅助技术用户提供最佳体验。</span><span class="sxs-lookup"><span data-stu-id="69585-106">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="69585-107">从 .NET Framework 4.7.1 开始，.NET Framework 包括大量辅助功能改进，使开发人员能够创建易于访问的应用程序。</span><span class="sxs-lookup"><span data-stu-id="69585-107">Starting with .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span>

## <a name="accessibility-switches"></a><span data-ttu-id="69585-108">辅助功能开关</span><span class="sxs-lookup"><span data-stu-id="69585-108">Accessibility switches</span></span>

<span data-ttu-id="69585-109">如果应用面向 .NET Framework 4.7 或更低版本，但是在 .NET Framework 4.7.1 或更高版本上运行，可以将应用配置为选择使用辅助功能。</span><span class="sxs-lookup"><span data-stu-id="69585-109">You can configure your app to opt into accessibility features if it targets .NET Framework 4.7 or an earlier version but is running on .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="69585-110">如果应用面向 .NET Framework 4.7.1 或更高版本，还可以将应用配置为使用旧版功能（且不使用辅助功能）。</span><span class="sxs-lookup"><span data-stu-id="69585-110">You can also configure your app to use legacy features (and not take advantage of accessibility features) if it targets .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="69585-111">包括辅助功能的每个 .NET Framework 版本都有一个特定于版本的辅助开关，请将它添加到应用程序配置文件 [`<runtime>`](../configure-apps/file-schema/runtime/index.md) 部分中的 [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="69585-111">Each version of the .NET Framework that includes accessibility features has a version-specific accessibility switch, which you add to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> <span data-ttu-id="69585-112">以下是受支持的开关：</span><span class="sxs-lookup"><span data-stu-id="69585-112">The following are the supported switches:</span></span>

|<span data-ttu-id="69585-113">Version</span><span class="sxs-lookup"><span data-stu-id="69585-113">Version</span></span>|<span data-ttu-id="69585-114">开关</span><span class="sxs-lookup"><span data-stu-id="69585-114">Switch</span></span>|
|---|---|
|<span data-ttu-id="69585-115">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="69585-115">.NET Framework 4.7.1</span></span>|<span data-ttu-id="69585-116">"Switch.UseLegacyAccessibilityFeatures"</span><span class="sxs-lookup"><span data-stu-id="69585-116">"Switch.UseLegacyAccessibilityFeatures"</span></span>|
|<span data-ttu-id="69585-117">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="69585-117">.NET Framework 4.7.2</span></span>|<span data-ttu-id="69585-118">"Switch.UseLegacyAccessibilityFeatures.2"</span><span class="sxs-lookup"><span data-stu-id="69585-118">"Switch.UseLegacyAccessibilityFeatures.2"</span></span>|
|<span data-ttu-id="69585-119">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="69585-119">.NET Framework 4.8</span></span>|<span data-ttu-id="69585-120">"Switch.UseLegacyAccessibilityFeatures.3"</span><span class="sxs-lookup"><span data-stu-id="69585-120">"Switch.UseLegacyAccessibilityFeatures.3"</span></span>|

### <a name="taking-advantage-of-accessibility-enhancements"></a><span data-ttu-id="69585-121">利用辅助功能改进</span><span class="sxs-lookup"><span data-stu-id="69585-121">Taking advantage of accessibility enhancements</span></span>

<span data-ttu-id="69585-122">对于面向 .NET Framework 4.7.1 或更高版本的应用程序，新的辅助功能默认情况下处于启用状态。</span><span class="sxs-lookup"><span data-stu-id="69585-122">The new accessibility features are enabled by default for applications that target .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="69585-123">此外，对于面向 .NET Framework 早期版本，但在 .NET Framework 4.7.1 或更高版本上运行的应用程序，可通过将开关添加到应用程序配置文件 [`<runtime>`](../configure-apps/file-schema/runtime/index.md) 部分中的 [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 元素并将其值设为 `false` 来选择弃用旧辅助功能行为（因而利用辅助功能改进）。</span><span class="sxs-lookup"><span data-stu-id="69585-123">In addition, applications that target an earlier version of the .NET Framework but are running on .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby take advantage of accessibility improvements) by adding switches to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `false`.</span></span> <span data-ttu-id="69585-124">以下代码演示如何选择使用 .NET Framework 4.7.1 中引入的辅助功能改进：</span><span class="sxs-lookup"><span data-stu-id="69585-124">The following shows how to opt in to accessibility enhancements introduced in .NET Framework 4.7.1:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="69585-125">如果选择使用更高的 .NET Framework 版本中的辅助功能，还必须显式选择使用更低 .NET Framework 版本的功能。</span><span class="sxs-lookup"><span data-stu-id="69585-125">If you choose to opt in to accessibility features in a later version of the .NET Framework, you must also explicitly opt in to the features from earlier versions of the .NET Framework.</span></span> <span data-ttu-id="69585-126">通过配置应用以利用 .NET Framework 4.7.1 和 4.7.2 中的辅助功能改进需要以下 [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 元素：</span><span class="sxs-lookup"><span data-stu-id="69585-126">Configuring your app to take advantage of accessibility improvements in both .NET Framework 4.7.1 and 4.7.2 requires the following [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

<span data-ttu-id="69585-127">通过配置应用以利用 .NET Framework 4.7.1、4.7.2 和 4.8 中的辅助功能改进需要以下 [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 元素：</span><span class="sxs-lookup"><span data-stu-id="69585-127">Configuring your app to take advantage of accessibility improvements in .NET Framework 4.7.1, 4.7.2, and 4.8 requires the following [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a><span data-ttu-id="69585-128">还原旧行为</span><span class="sxs-lookup"><span data-stu-id="69585-128">Restoring legacy behavior</span></span>

<span data-ttu-id="69585-129">对于面向 .NET Framework 4.7.1 或更高版本的应用程序，可通过将开关添加到应用程序配置文件 [`<runtime>`](../configure-apps/file-schema/runtime/index.md) 部分中的 [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 元素并将其值设为 `true` 来禁用辅助功能。</span><span class="sxs-lookup"><span data-stu-id="69585-129">Applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding switches to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `true`.</span></span> <span data-ttu-id="69585-130">例如，以下配置选择弃用 .NET Framework 4.7.2 中引入的辅助功能：</span><span class="sxs-lookup"><span data-stu-id="69585-130">For example, the following configuration opts out of accessibility features introduced in .NET Framework 4.7.2:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-net-framework-48"></a><span data-ttu-id="69585-131">.NET Framework 4.8 中辅助功能的新增功能</span><span class="sxs-lookup"><span data-stu-id="69585-131">What's new in accessibility in .NET Framework 4.8</span></span>

<span data-ttu-id="69585-132">.NET Framework 4.8 在以下几个领域包含新增辅助功能：</span><span class="sxs-lookup"><span data-stu-id="69585-132">.NET Framework 4.8 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="69585-133">Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="69585-133">Windows Forms</span></span>](#winforms48)

- [<span data-ttu-id="69585-134">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="69585-134">Windows Presentation Foundation (WPF)</span></span>](#wpf48)

- [<span data-ttu-id="69585-135">Windows Workflow Foundation (WF) 工作流设计器</span><span class="sxs-lookup"><span data-stu-id="69585-135">Windows Workflow Foundation (WF) workflow designer</span></span>](#wf48)

<a name="winforms48"></a>

### <a name="windows-forms"></a><span data-ttu-id="69585-136">Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="69585-136">Windows Forms</span></span>

<span data-ttu-id="69585-137">在 .NET Framework 4.8 中，Windows 窗体将对 LiveRegions 和通知事件的支持添加到多个常用控件中。</span><span class="sxs-lookup"><span data-stu-id="69585-137">In .NET Framework 4.8, Windows Forms adds support for LiveRegions and Notification Events to many commonly used controls.</span></span> <span data-ttu-id="69585-138">它还会在用户使用键盘导航到控件时添加工具提示支持。</span><span class="sxs-lookup"><span data-stu-id="69585-138">It also adds support for ToolTips when a user navigates to a control by using the keyboard.</span></span>

<span data-ttu-id="69585-139">**标签和 StatusStrips 中的 UIA LiveRegions 支持**</span><span class="sxs-lookup"><span data-stu-id="69585-139">**UIA LiveRegions Support in Labels and StatusStrips**</span></span>

<span data-ttu-id="69585-140">UIA LiveRegions 允许应用程序开发人员将用户工作位置之外的某个控件中的文本更改通知给屏幕阅读器。</span><span class="sxs-lookup"><span data-stu-id="69585-140">UIA LiveRegions allow application developers to notify screen readers of a text change in a control that is located apart from the location where the user is working.</span></span> <span data-ttu-id="69585-141">例如，对于显示连接状态的 <xref:System.Windows.Forms.StatusStrip> 控件，这很有用。</span><span class="sxs-lookup"><span data-stu-id="69585-141">This is useful, for example, for a <xref:System.Windows.Forms.StatusStrip> control that shows a connection status.</span></span> <span data-ttu-id="69585-142">如果连接断开且状态发生更改，开发人员可能会希望将此情况通知给屏幕阅读器。</span><span class="sxs-lookup"><span data-stu-id="69585-142">If the connection is dropped and the status changes, the developer might want to notify the screen reader.</span></span>

<span data-ttu-id="69585-143">从 .NET Framework 4.8 开始，Windows 窗体同时为 <xref:System.Windows.Forms.Label> 和 <xref:System.Windows.Forms.StatusStrip> 控件实现 UIA LiveRegions。</span><span class="sxs-lookup"><span data-stu-id="69585-143">Starting with .NET Framework 4.8, Windows Forms implements UIA LiveRegions for both the <xref:System.Windows.Forms.Label> and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="69585-144">例如，以下代码在名为 `label1` 的 <xref:System.Windows.Forms.Label> 控件中使用 LiveRegion：</span><span class="sxs-lookup"><span data-stu-id="69585-144">For example, the following code uses the LiveRegion in a <xref:System.Windows.Forms.Label> control named `label1`:</span></span>

```csharp
public Form1()
{
   InitializeComponent();
   label1.AutomationLiveSetting = AutomationLiveSetting.Polite;
}

…
Label1.Text = “Ready!”;
```

<span data-ttu-id="69585-145">无论用户在何处与应用程序交互，讲述人都会宣布“准备就绪”。</span><span class="sxs-lookup"><span data-stu-id="69585-145">Narrator announces “Ready” regardless of where the user is interacting with the application.</span></span>

<span data-ttu-id="69585-146">还可以将 <xref:System.Windows.Forms.UserControl> 实现为 LiveRegion：</span><span class="sxs-lookup"><span data-stu-id="69585-146">You can also implement your <xref:System.Windows.Forms.UserControl> as a LiveRegion:</span></span>

```csharp
using System;
using System.Windows.Forms;
using System.Windows.Forms.Automation;

namespace WindowsFormsApplication
{
   public partial class UserControl1 : UserControl, IAutomationLiveRegion
   {
      public UserControl1()
      {
         InitializeComponent();
      }

      public AutomationLiveSetting AutomationLiveSetting { get; set; }
      private AutomationLiveSetting IAutomationLiveRegion.GetLiveSetting()
      {
         return this.AutomationLiveSetting;
      }

      protected override void OnTextChanged(EventArgs e)
      {
         base.OnTextChanged(e);
         AutomationNotifications.UiaRaiseLiveRegionChangedEvent(this.AccessibilityObject);
      }
   }
}
```

<span data-ttu-id="69585-147">**UIA 通知事件**</span><span class="sxs-lookup"><span data-stu-id="69585-147">**UIA notification events**</span></span>

<span data-ttu-id="69585-148">Windows 10 Fall Creators Update 中引入的 UIA 通知事件允许应用程序引发 UIA 事件，这使得讲述人仅根据你为事件提供的文本来进行宣读，而无需在 UI 中使用相应的控件。</span><span class="sxs-lookup"><span data-stu-id="69585-148">The UIA Notification event, introduced in Windows 10 Fall Creators Update, allows your app to raise a UIA event, which leads to Narrator simply making an announcement based on text you supply with the event, without the need to have a corresponding control in the UI.</span></span> <span data-ttu-id="69585-149">在某些情况下，这是一种能够显着改善应用辅助功能的简单方法。</span><span class="sxs-lookup"><span data-stu-id="69585-149">In some scenarios, this is a straightforward way to dramatically improve the accessibility of your app.</span></span> <span data-ttu-id="69585-150">也可以用于通知可能需要很长时间的某些进程的进度。</span><span class="sxs-lookup"><span data-stu-id="69585-150">In can also be useful to notify of the progress of some process that may take a long time.</span></span> <span data-ttu-id="69585-151">有关 UIA 通知事件的详细信息，请参阅[桌面应用程序是否可以利用新的 UI 通知事件？](https://docs.microsoft.com/archive/blogs/winuiautomation/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need)。</span><span class="sxs-lookup"><span data-stu-id="69585-151">For more information about UIA Notification Events, see [Can your desktop app leverage the new UI Notification event?](https://docs.microsoft.com/archive/blogs/winuiautomation/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need).</span></span>

<span data-ttu-id="69585-152">下面的示例会引发[通知事件](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A)：</span><span class="sxs-lookup"><span data-stu-id="69585-152">The following example raises the [Notification event](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A):</span></span>

```csharp
MethodInfo raiseMethod = typeof(AccessibleObject).GetMethod("RaiseAutomationNotification");
if (raiseMethod != null) {
   raiseMethod.Invoke(progressBar1.AccessibilityObject, new object[3] {/*Other*/ 4, /*All*/ 2, "The progress is 50%." });
}
```

<span data-ttu-id="69585-153">**键盘访问工具提示**</span><span class="sxs-lookup"><span data-stu-id="69585-153">**ToolTips on keyboard access**</span></span>

<span data-ttu-id="69585-154">在面向 .NET Framework 4.7.2 及更早版本的应用程序中，只能通过将鼠标指针移到控件上，才能触发控件[工具提示](xref:System.Windows.Forms.ToolTip)。</span><span class="sxs-lookup"><span data-stu-id="69585-154">In applications that target .NET Framework 4.7.2 and earlier versions, a control [tooltip](xref:System.Windows.Forms.ToolTip) can only be triggered to pop up by moving a mouse pointer into the control.</span></span> <span data-ttu-id="69585-155">从 .NET Framework 4.8 开始，键盘用户可以通过使用 Tab 键或箭头键（具有或不具有修饰键）来聚焦控件，从而触发控件的工具提示。</span><span class="sxs-lookup"><span data-stu-id="69585-155">Starting with .NET Framework 4.8, a keyboard user can trigger a control’s tooltip by focusing the control using a Tab key or arrow keys with or without modifier keys.</span></span> <span data-ttu-id="69585-156">要实现这一特定的辅助功能优化效果，需要额外的 [AppContext 开关](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)：</span><span class="sxs-lookup"><span data-stu-id="69585-156">This particular accessibility enhancement requires an additional [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1"/>
   </startup>
   <runtime>
      <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false  -->
      <!-- Please note that disabling Switch.UseLegacyAccessibilityFeatures, Switch.UseLegacyAccessibilityFeatures.2 and Switch.UseLegacyAccessibilityFeatures.3 is required to disable Switch.System.Windows.Forms.UseLegacyToolTipDisplay -->
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false"/>
   </runtime>
</configuration>
```

<span data-ttu-id="69585-157">下图显示用户使用键盘选中按钮时的工具提示。</span><span class="sxs-lookup"><span data-stu-id="69585-157">The following figure shows the tooltip when the user has selected a button with the keyboard.</span></span>

![用户使用键盘导航到按钮时工具提示的屏幕截图。](./media/whats-new-in-accessibility/select-tooltip-with-keyboard.png)

<a name="wpf48"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="69585-159">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="69585-159">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="69585-160">从 .NET Framework 4.8 开始，WPF 包括大量辅助功能改进。</span><span class="sxs-lookup"><span data-stu-id="69585-160">Starting with .NET Framework 4.8, WPF includes a number of accessibility improvements.</span></span>

<span data-ttu-id="69585-161">**屏幕讲述人不再宣读可见性为“折叠”或“隐藏”的元素**</span><span class="sxs-lookup"><span data-stu-id="69585-161">**Screen narrators no longer announce elements with Collapsed or Hidden visibility**</span></span>

<span data-ttu-id="69585-162">可见性为“折叠”或“隐藏”的元素不再被屏幕讲述人宣读。</span><span class="sxs-lookup"><span data-stu-id="69585-162">Elements with collapsed or hidden visibility are no longer announced by screen reader.</span></span> <span data-ttu-id="69585-163">如果向用户宣读包含可见性为 <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> 或 <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> 的元素的用户界面，屏幕阅读器可能会错误呈现这些界面。</span><span class="sxs-lookup"><span data-stu-id="69585-163">User interfaces that contain elements with a Visibility of <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> or <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> can be misrepresented by screen readers if they are announced to the user.</span></span> <span data-ttu-id="69585-164">从 .NET Framework 4.8 开始，WPF 不再在 UIAutomation 树的控制视图中包含折叠或隐藏的元素，屏幕阅读器无法再宣读这些元素。</span><span class="sxs-lookup"><span data-stu-id="69585-164">Starting with .NET Framework 4.8, WPF no longer includes collapsed or hidden elements in the Control View of the UIAutomation tree, so the screen readers can no longer announce these elements.</span></span>

<span data-ttu-id="69585-165">**与非基于修饰器的文本选择配合使用的 SelectionTextBrush 属性**</span><span class="sxs-lookup"><span data-stu-id="69585-165">**SelectionTextBrush property for use with non-Adorner based text selection**</span></span>

<span data-ttu-id="69585-166">在 .NET Framework 4.7.2 中，WPF 添加了无需使用修饰器层即可绘制 <xref:System.Windows.Controls.TextBox> 和 <xref:System.Windows.Controls.PasswordBox> 文本选择的功能。</span><span class="sxs-lookup"><span data-stu-id="69585-166">In the .NET Framework 4.7.2, WPF added the ability to draw <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.PasswordBox> text selection without using the Adorner layer.</span></span> <span data-ttu-id="69585-167">此方案中所选文本的前景色由 <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType> 决定。</span><span class="sxs-lookup"><span data-stu-id="69585-167">The foreground color of the selected text in this scenario was dictated by <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="69585-168">.NET Framework 4.8 添加了一个新属性 `SelectionTextBrush`，允许开发人员在使用非基于修饰器的文本选择时为所选文本选择特定画笔。</span><span class="sxs-lookup"><span data-stu-id="69585-168">.NET Framework 4.8 adds a new property, `SelectionTextBrush`, that allows developers to select the specific brush for the selected text when using non-Adorner based text selection.</span></span> <span data-ttu-id="69585-169">此属性仅适用于 <xref:System.Windows.Controls.Primitives.TextBoxBase> 派生的控件和启用了非基于修饰器的文本选择功能的 WPF 应用程序中的 <xref:System.Windows.Controls.PasswordBox> 控件。</span><span class="sxs-lookup"><span data-stu-id="69585-169">This property works only on <xref:System.Windows.Controls.Primitives.TextBoxBase>-derived controls and the <xref:System.Windows.Controls.PasswordBox> control in WPF applications with non-Adorner-based text selection enabled.</span></span> <span data-ttu-id="69585-170">该属性不适用于 <xref:System.Windows.Controls.RichTextBox> 控件。</span><span class="sxs-lookup"><span data-stu-id="69585-170">It does not work on the <xref:System.Windows.Controls.RichTextBox> control.</span></span> <span data-ttu-id="69585-171">如果未启用非基于修饰器的文本选择功能，则忽略此属性。</span><span class="sxs-lookup"><span data-stu-id="69585-171">If non-Adorner-based text selection is not enabled, this property is ignored.</span></span>

<span data-ttu-id="69585-172">要使用此属性，只需将其添加到 XAML 代码，并使用适当的画笔或绑定。</span><span class="sxs-lookup"><span data-stu-id="69585-172">To use this property, simply add it to your XAML code and use the appropriate brush or binding.</span></span> <span data-ttu-id="69585-173">生成的文本选择如下所示：</span><span class="sxs-lookup"><span data-stu-id="69585-173">The resulting text selection looks like this:</span></span>

![运行中应用的屏幕截图，其中选中了“Hello World”文字。](./media/whats-new-in-accessibility/selectiontextbrush-property.png)

<span data-ttu-id="69585-175">可以结合使用 `SelectionBrush` 和 `SelectionTextBrush` 属性来生成你认为合适的任何背景色和前景色组合。</span><span class="sxs-lookup"><span data-stu-id="69585-175">You can combine the use of the `SelectionBrush` and `SelectionTextBrush` properties to generate any background and foreground color combination that you deem appropriate.</span></span>

<span data-ttu-id="69585-176">**对 UIAutomation ControllerFor 属性的支持**</span><span class="sxs-lookup"><span data-stu-id="69585-176">**Support for the UIAutomation ControllerFor property**</span></span>

<span data-ttu-id="69585-177">UIAutomation 的 `ControllerFor` 属性返回一系列由支持该属性的自动化元素操纵的自动化元素。</span><span class="sxs-lookup"><span data-stu-id="69585-177">UIAutomation’s `ControllerFor` property returns an array of automation elements that are manipulated by the automation element that supports this property.</span></span> <span data-ttu-id="69585-178">此属性通常用于自动建议辅助功能。</span><span class="sxs-lookup"><span data-stu-id="69585-178">This property is commonly used for Auto-suggest accessibility.</span></span> <span data-ttu-id="69585-179">应在自动化元素会影响应用程序 UI 或桌面的一个或多个段时使用 `ControllerFor`。</span><span class="sxs-lookup"><span data-stu-id="69585-179">`ControllerFor` is used when an automation element affects one or more segments of the application UI or the desktop.</span></span> <span data-ttu-id="69585-180">否则，很难将控制操作的影响与 UI 元素关联。</span><span class="sxs-lookup"><span data-stu-id="69585-180">Otherwise, it is hard to associate the impact of the control operation with UI elements.</span></span> <span data-ttu-id="69585-181">此功能增加了控件为 `ControllerFor` 属性提供值的功能。</span><span class="sxs-lookup"><span data-stu-id="69585-181">This feature adds the ability for controls to provide a value for the `ControllerFor` property.</span></span>

<span data-ttu-id="69585-182">.NET framework 4.8 添加了新的虚拟方法 <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="69585-182">.NET Framework 4.8 adds a new virtual method, <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>.</span></span> <span data-ttu-id="69585-183">要为 `ControllerFor` 属性提供值，只需替代此方法并为此 <xref:System.Windows.Automation.Peers.AutomationPeer> 操作的控件返回 `List<AutomationPeer>`：</span><span class="sxs-lookup"><span data-stu-id="69585-183">To provide a value for the `ControllerFor` property, simply override this method and return a `List<AutomationPeer>` for the controls being manipulated by this <xref:System.Windows.Automation.Peers.AutomationPeer>:</span></span>

```csharp
public class AutoSuggestTextBox: TextBox
{
   protected override AutomationPeer OnCreateAutomationPeer()
   {
      return new AutoSuggestTextBoxAutomationPeer(this);
   }

   public ListBox SuggestionListBox;
}

internal class AutoSuggestTextBoxAutomationPeer : TextBoxAutomationPeer
{
   public AutoSuggestTextBoxAutomationPeer(AutoSuggestTextBox owner) : base(owner)
   {
   }

   protected override List<AutomationPeer> GetControlledPeersCore()
   {
      List<AutomationPeer> controlledPeers = new List<AutomationPeer>();
      AutoSuggestTextBox owner = Owner as AutoSuggestTextBox;
      controlledPeers.Add(UIElementAutomationPeer.CreatePeerForElement(owner.SuggestionListBox));
      return controlledPeers;
   }
}
```

<span data-ttu-id="69585-184">**键盘访问工具提示**</span><span class="sxs-lookup"><span data-stu-id="69585-184">**Tooltips on keyboard access**</span></span>

<span data-ttu-id="69585-185">在 .NET Framework 4.7.2 和更早版本中，仅当用户将鼠标光标悬停在控件上时，系统才会显示工具提示。</span><span class="sxs-lookup"><span data-stu-id="69585-185">In .NET Framework 4.7.2 and earlier versions, tooltips display only when the user hovers the mouse cursor over a control.</span></span> <span data-ttu-id="69585-186">在 .NET Framework 4.8 中，工具提示还会在键盘聚焦时显示，也可以通过键盘快捷方式显示。</span><span class="sxs-lookup"><span data-stu-id="69585-186">In .NET Framework 4.8, tooltips also display on keyboard focus, as well as via a keyboard shortcut.</span></span>

<span data-ttu-id="69585-187">要启用此功能，应用程序需要面向 .NET Framework 4.8，或使用 `Switch.UseLegacyAccessibilityFeatures.3` 和 `Switch.UseLegacyToolTipDisplay` [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 开关来选择加入。</span><span class="sxs-lookup"><span data-stu-id="69585-187">To enable this feature, an application needs to target .NET Framework 4.8 or opt-in by using the `Switch.UseLegacyAccessibilityFeatures.3` and `Switch.UseLegacyToolTipDisplay` [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switches.</span></span> <span data-ttu-id="69585-188">下面是一个示例应用程序配置文件：</span><span class="sxs-lookup"><span data-stu-id="69585-188">The following is a sample application configuration file:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />
   </startup>
   <runtime>
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.UseLegacyToolTipDisplay=false" />
   </runtime>
</configuration>
```

<span data-ttu-id="69585-189">启用后，一旦控件接收到键盘焦点，包含工具提示的所有控件都会显示工具提示。</span><span class="sxs-lookup"><span data-stu-id="69585-189">Once enabled, all controls that contain a tooltip display it once the control receives keyboard focus.</span></span> <span data-ttu-id="69585-190">随时间推移或当键盘焦点发生变化时，可关闭工具提示。</span><span class="sxs-lookup"><span data-stu-id="69585-190">The tooltip can be dismissed over time or when the keyboard focus changes.</span></span> <span data-ttu-id="69585-191">用户还可以通过使用新的键盘快捷键 Ctrl+Shift+F10 手动关闭工具提示。</span><span class="sxs-lookup"><span data-stu-id="69585-191">Users can also dismiss the tooltip manually by using a new keyboard shortcut, Ctrl + Shift + F10.</span></span> <span data-ttu-id="69585-192">关闭工具提示后，可以使用相同的键盘快捷键再次显示。</span><span class="sxs-lookup"><span data-stu-id="69585-192">Once the tooltip has been dismissed it can be displayed again by using the same keyboard shortcut.</span></span>

> [!NOTE]
> <span data-ttu-id="69585-193"><xref:System.Windows.Controls.Ribbon.Ribbon> 控件上的[功能区工具提示](xref:System.Windows.Controls.Ribbon.RibbonToolTip)不在键盘聚焦时显示；它们仅通过键盘快捷键显示。</span><span class="sxs-lookup"><span data-stu-id="69585-193">[Ribbon tooltips](xref:System.Windows.Controls.Ribbon.RibbonToolTip) on <xref:System.Windows.Controls.Ribbon.Ribbon> controls won’t show on keyboard focus; they only show via the keyboard shortcut.</span></span>

<span data-ttu-id="69585-194">**添加了对 SizeOfSet 和 PositionInSet UIAutomation 属性的支持**</span><span class="sxs-lookup"><span data-stu-id="69585-194">**Added Support for SizeOfSet and PositionInSet UIAutomation properties**</span></span>

<span data-ttu-id="69585-195">Windows 10 引入了两个新的 UIAutomation 属性（`SizeOfSet` 和 `PositionInSet`），应用程序用其描述集合中的项数。</span><span class="sxs-lookup"><span data-stu-id="69585-195">Windows 10 introduced two new UIAutomation properties, `SizeOfSet` and `PositionInSet`, which are used by applications to describe the count of items in a set.</span></span> <span data-ttu-id="69585-196">然后，UIAutomation 客户端应用程序（如屏幕阅读器）可以向某个应用程序查询这些属性，并宣布应用程序 UI 的准确表示形式。</span><span class="sxs-lookup"><span data-stu-id="69585-196">UIAutomation client applications such as screen readers can then query an application for these properties and announce an accurate representation of the application’s UI.</span></span>

<span data-ttu-id="69585-197">从 .NET Framework 4.8 开始，WPF 向 WPF 应用程序中的 UIAutomation 公开这两个属性。</span><span class="sxs-lookup"><span data-stu-id="69585-197">Starting with .NET Framework 4.8, WPF  exposes these two properties to UIAutomation in WPF applications.</span></span> <span data-ttu-id="69585-198">这可以通过以下两种方式实现：</span><span class="sxs-lookup"><span data-stu-id="69585-198">This can be accomplished in two ways:</span></span>

- <span data-ttu-id="69585-199">通过使用依赖项属性。</span><span class="sxs-lookup"><span data-stu-id="69585-199">By using dependency properties.</span></span>

  <span data-ttu-id="69585-200">WPF 添加了两个新的依赖项属性：<xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> 和 <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="69585-200">WPF adds two new dependency properties, <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>.</span></span> <span data-ttu-id="69585-201">开发人员可以使用 XAML 来设置它们的值：</span><span class="sxs-lookup"><span data-stu-id="69585-201">A developer can use XAML to set their values:</span></span>

  ```xaml
  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="1">Button 1</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="2">Button 2</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="3">Button 3</Button>
  ```

- <span data-ttu-id="69585-202">通过替代 AutomationPeer 虚拟方法。</span><span class="sxs-lookup"><span data-stu-id="69585-202">By overriding AutomationPeer virtual methods.</span></span>

  <span data-ttu-id="69585-203"><xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> 和 <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> 虚拟方法已添加到 AutomationPeer 类中。</span><span class="sxs-lookup"><span data-stu-id="69585-203">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> and <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> virtual methods been added to the AutomationPeer class.</span></span> <span data-ttu-id="69585-204">开发人员可以通过替代这些方法为 `SizeOfSet` 和 `PositionInSet` 提供值，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="69585-204">A developer can provide values for `SizeOfSet` and `PositionInSet` by overriding these methods, as shown in the following example:</span></span>

  ```csharp
  public class MyButtonAutomationPeer : ButtonAutomationPeer
  {
    protected override int GetSizeOfSetCore()
    {
        // Call into your own logic to provide a value for SizeOfSet
        return CalculateSizeOfSet();
    }

    protected override int GetPositionInSetCore()
    {
        // Call into your own logic to provide a value for PositionInSet
        return CalculatePositionInSet();
    }
  }
  ```

<span data-ttu-id="69585-205">此外，开发人员无需执行其他操作，<xref:System.Windows.Controls.ItemsControl> 实例中的项会自动为这些属性提供值。</span><span class="sxs-lookup"><span data-stu-id="69585-205">In addition, items in <xref:System.Windows.Controls.ItemsControl> instances provide a value for these properties automatically without additional action from the developer.</span></span> <span data-ttu-id="69585-206">如果将 <xref:System.Windows.Controls.ItemsControl> 归组，则组的集合表示为一个集，并且每个组计为一个单独的集，该组内的每个项提供其在该组内的位置以及该组的大小。</span><span class="sxs-lookup"><span data-stu-id="69585-206">If an <xref:System.Windows.Controls.ItemsControl> is grouped, the collection of groups is represented as a set, and each group is counted as a separate set, with each item inside that group providing its position inside that group as well as the size of the group.</span></span> <span data-ttu-id="69585-207">虚拟化不会影响自动值。</span><span class="sxs-lookup"><span data-stu-id="69585-207">Automatic values are not affected by virtualization.</span></span> <span data-ttu-id="69585-208">即使没有实现某个项，它仍然会计入集的总大小，并影响其在同级项集中的位置。</span><span class="sxs-lookup"><span data-stu-id="69585-208">Even if an item is not realized, it is still counted toward the total size of the set and affects the position in the set of its sibling items.</span></span>

<span data-ttu-id="69585-209">仅当应用程序面向 .NET Framework 4.8 时，才会提供自动值。</span><span class="sxs-lookup"><span data-stu-id="69585-209">Automatic values are only provided if the application targets .NET Framework 4.8.</span></span> <span data-ttu-id="69585-210">对于面向 .NET Framework 早期版本的应用程序，可以设置 `Switch.UseLegacyAccessibilityFeatures.3` [AppContext 开关](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)，如以下 App.config 文件中所示：</span><span class="sxs-lookup"><span data-stu-id="69585-210">For applications that target an earlier version of the .NET Framework, you can set the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), as shown in the following App.config file:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />
   </startup>
   <runtime>
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
   </runtime>
</configuration>
```

<a name="wf48"></a>

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="69585-211">Windows Workflow Foundation (WF) 工作流设计器</span><span class="sxs-lookup"><span data-stu-id="69585-211">Windows Workflow Foundation (WF) workflow designer</span></span>

<span data-ttu-id="69585-212">.NET Framework 4.8 中的工作流设计器包含以下更改：</span><span class="sxs-lookup"><span data-stu-id="69585-212">The workflow designer includes the following changes in .NET Framework 4.8:</span></span>

- <span data-ttu-id="69585-213">使用讲述人的用户将体验到 FlowSwitch 事例标签的改进。</span><span class="sxs-lookup"><span data-stu-id="69585-213">Users using Narrator will see improvements in FlowSwitch case labels.</span></span>

- <span data-ttu-id="69585-214">使用讲述人的用户将体验到按钮描述的改进。</span><span class="sxs-lookup"><span data-stu-id="69585-214">Users using Narrator will see improvements in button descriptions.</span></span>

- <span data-ttu-id="69585-215">选择高对比度主题的用户将看到工作流设计器及其控件可见性方面的改进，例如元素间的对比度效果更好和用于焦点元素的更明显的选择框。</span><span class="sxs-lookup"><span data-stu-id="69585-215">Users who choose High Contrast themes will see improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

<span data-ttu-id="69585-216">如果应用程序面向 .NET Framework 4.7.2 或更早版本，则可以通过在应用程序配置文件中将 `Switch.UseLegacyAccessibilityFeatures.3` [AppContext 开关](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)设置为 `false` 来选择这些更改。</span><span class="sxs-lookup"><span data-stu-id="69585-216">If your application targets .NET Framework 4.7.2 or an earlier version, you can opt into these changes by setting the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to `false` in your application configuration file.</span></span> <span data-ttu-id="69585-217">有关详细信息，请参阅本文中的[利用辅助功能改进](#taking-advantage-of-accessibility-enhancements)部分。</span><span class="sxs-lookup"><span data-stu-id="69585-217">For more information, see the [Taking advantage of accessibility enhancements](#taking-advantage-of-accessibility-enhancements) section in this article.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-472"></a><span data-ttu-id="69585-218">.NET Framework 4.7.2 中辅助功能的新增功能</span><span class="sxs-lookup"><span data-stu-id="69585-218">What's new in accessibility in .NET Framework 4.7.2</span></span>

<span data-ttu-id="69585-219">.NET Framework 4.7.2 在以下几个领域包含新增辅助功能：</span><span class="sxs-lookup"><span data-stu-id="69585-219">.NET Framework 4.7.2 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="69585-220">Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="69585-220">Windows Forms</span></span>](#winforms472)

- [<span data-ttu-id="69585-221">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="69585-221">Windows Presentation Foundation (WPF)</span></span>](#wpf472)

<a name="winforms472"></a>

### <a name="windows-forms"></a><span data-ttu-id="69585-222">Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="69585-222">Windows Forms</span></span>

<span data-ttu-id="69585-223">**高对比度主题中的 OS 定义的颜色**</span><span class="sxs-lookup"><span data-stu-id="69585-223">**OS-defined colors in High Contrast themes**</span></span>

<span data-ttu-id="69585-224">自 .NET Framework 4.7.2 起，Windows 窗体使用高对比度主题中的操作系统定义的颜色。</span><span class="sxs-lookup"><span data-stu-id="69585-224">Starting with .NET Framework 4.7.2, Windows Forms uses colors defined by the operating system in High Contrast themes.</span></span> <span data-ttu-id="69585-225">这会影响以下控件：</span><span class="sxs-lookup"><span data-stu-id="69585-225">This affects the following controls:</span></span>

- <span data-ttu-id="69585-226"><xref:System.Windows.Forms.ToolStripDropDownButton> 控件的下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="69585-226">The drop-down arrow of the <xref:System.Windows.Forms.ToolStripDropDownButton> control.</span></span>

- <span data-ttu-id="69585-227"><xref:System.Windows.Forms.ButtonBase.FlatStyle> 设为 <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> 或 <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType> 的 <xref:System.Windows.Forms.Button>、<xref:System.Windows.Forms.RadioButton> 和 <xref:System.Windows.Forms.CheckBox> 控件。</span><span class="sxs-lookup"><span data-stu-id="69585-227">The <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with <xref:System.Windows.Forms.ButtonBase.FlatStyle> set to <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> or <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span></span> <span data-ttu-id="69585-228">以前，所选文本和背景颜色对比度低，难以阅读。</span><span class="sxs-lookup"><span data-stu-id="69585-228">Previously, selected text and background colors were not contrasting and were hard to read.</span></span>

- <span data-ttu-id="69585-229"><xref:System.Windows.Forms.Control.Enabled> 属性设为 `false` 的 <xref:System.Windows.Forms.GroupBox> 中所包含的控件。</span><span class="sxs-lookup"><span data-stu-id="69585-229">Controls contained within a <xref:System.Windows.Forms.GroupBox> that has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="69585-230">在高对比度模式下，<xref:System.Windows.Forms.ToolStripButton>、<xref:System.Windows.Forms.ToolStripComboBox> 和 <xref:System.Windows.Forms.ToolStripDropDownButton> 控件的亮度对比度提高。</span><span class="sxs-lookup"><span data-stu-id="69585-230">The <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, and <xref:System.Windows.Forms.ToolStripDropDownButton> controls, which have an increased luminosity contrast ratio in High Contrast Mode.</span></span>

- <span data-ttu-id="69585-231"><xref:System.Windows.Forms.DataGridViewLinkCell> 的 <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> 属性。</span><span class="sxs-lookup"><span data-stu-id="69585-231">The <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> property of the <xref:System.Windows.Forms.DataGridViewLinkCell>.</span></span>

<span data-ttu-id="69585-232">**讲述人改进**</span><span class="sxs-lookup"><span data-stu-id="69585-232">**Narrator improvements**</span></span>

<span data-ttu-id="69585-233">自 .NET Framework 4.7.2 起，讲述人支持在以下几个方面改进：</span><span class="sxs-lookup"><span data-stu-id="69585-233">Starting with .NET Framework 4.7.2, Narrator support is enhanced as follows:</span></span>

- <span data-ttu-id="69585-234">它在公布 <xref:System.Windows.Forms.ToolStripMenuItem> 的文本时会公布 <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> 属性的值。</span><span class="sxs-lookup"><span data-stu-id="69585-234">It announces the value of the <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> property when announcing the text of a <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>

- <span data-ttu-id="69585-235">当 <xref:System.Windows.Forms.ToolStripMenuItem> 的 <xref:System.Windows.Forms.Control.Enabled> 属性设置为 `false` 时，它会有所指示。</span><span class="sxs-lookup"><span data-stu-id="69585-235">It indicates when a <xref:System.Windows.Forms.ToolStripMenuItem> has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="69585-236">当 <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> 属性设置为 `true` 时，它会针对复选框的状态给出反馈。</span><span class="sxs-lookup"><span data-stu-id="69585-236">It gives feedback on the state of a check box when the <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> property is set to `true`.</span></span>

- <span data-ttu-id="69585-237">讲述人扫描模式焦点顺序与 ClickOnce 下载对话框窗口中控件的视觉顺序一致。</span><span class="sxs-lookup"><span data-stu-id="69585-237">Narrator's Scan Mode focus order is consistent with the visual order of the controls on the ClickOnce download dialog window.</span></span>

<span data-ttu-id="69585-238">**DataGridView 改进**</span><span class="sxs-lookup"><span data-stu-id="69585-238">**DataGridView improvements**</span></span>

<span data-ttu-id="69585-239">自 .NET Framework 4.7.2 起，<xref:System.Windows.Forms.DataGridView> 控件引入了以下辅助功能改进：</span><span class="sxs-lookup"><span data-stu-id="69585-239">Starting with .NET Framework 4.7.2, the <xref:System.Windows.Forms.DataGridView> control has introduced the following accessibility improvements:</span></span>

- <span data-ttu-id="69585-240">可以使用键盘对行进行排序。</span><span class="sxs-lookup"><span data-stu-id="69585-240">Rows can be sorted using the keyboard.</span></span> <span data-ttu-id="69585-241">用户可使用 F3 按当前列排序。</span><span class="sxs-lookup"><span data-stu-id="69585-241">A user can use the F3 key in order to sort by the current column.</span></span>

- <span data-ttu-id="69585-242">若 <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> 设置为 <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>，当用户按 Tab 键遍历当前行中的单元格时，列标题将更改颜色来指示当前列。</span><span class="sxs-lookup"><span data-stu-id="69585-242">When the <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> is set to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, the column header changes color to indicate the current column as the user tabs through the cells in the current row.</span></span>

- <span data-ttu-id="69585-243"><xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> 的 <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> 属性返回正确的父控件。</span><span class="sxs-lookup"><span data-stu-id="69585-243">The <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> property of a  <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> returns the correct parent control.</span></span>

<span data-ttu-id="69585-244">**改进了视觉提示**</span><span class="sxs-lookup"><span data-stu-id="69585-244">**Improved visual cues**</span></span>

- <span data-ttu-id="69585-245">具有空 <xref:System.Windows.Forms.ButtonBase.Text> 属性的 <xref:System.Windows.Forms.RadioButton> 和 <xref:System.Windows.Forms.CheckBox> 控件在接收到焦点时会显示焦点指示器。</span><span class="sxs-lookup"><span data-stu-id="69585-245">The <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with an empty <xref:System.Windows.Forms.ButtonBase.Text> property  display a focus indicator when they receive the focus.</span></span>

<span data-ttu-id="69585-246">**改进了属性网格支持**</span><span class="sxs-lookup"><span data-stu-id="69585-246">**Improved Property Grid Support**</span></span>

- <span data-ttu-id="69585-247">现在，仅在 PropertyGrid 元素启用时，<xref:System.Windows.Forms.PropertyGrid> 控件子元素才会为 <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> 属性返回 `true`。</span><span class="sxs-lookup"><span data-stu-id="69585-247">The <xref:System.Windows.Forms.PropertyGrid> control child elements now return a `true` for the  <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> property only when a PropertyGrid element is enabled.</span></span>

- <span data-ttu-id="69585-248">仅在用户可更改 PropertyGrid 元素时，<xref:System.Windows.Forms.PropertyGrid> 控件子元素才会为 <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> 属性返回 `false`。</span><span class="sxs-lookup"><span data-stu-id="69585-248">The <xref:System.Windows.Forms.PropertyGrid> control child elements return a `false` for the <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> property only when a PropertyGrid element can be changed by the user.</span></span>

<span data-ttu-id="69585-249">**改进了的键盘导航**</span><span class="sxs-lookup"><span data-stu-id="69585-249">**Improved keyboard navigation**</span></span>

- <span data-ttu-id="69585-250"><xref:System.Windows.Forms.ToolStripButton> 控件允许在焦点包含在 <xref:System.Windows.Forms.ToolStripPanel>（其 <xref:System.Windows.Forms.ToolStripPanel.TabStop> 属性设置为 `true`）中时进行聚焦</span><span class="sxs-lookup"><span data-stu-id="69585-250">The <xref:System.Windows.Forms.ToolStripButton> control allows focus when contained within a <xref:System.Windows.Forms.ToolStripPanel> that has the <xref:System.Windows.Forms.ToolStripPanel.TabStop> property set to `true`</span></span>

<a name="wpf472"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="69585-251">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="69585-251">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="69585-252">**对复选框和单选按钮控件的更改**</span><span class="sxs-lookup"><span data-stu-id="69585-252">**Changes to the CheckBox and RadioButton controls**</span></span>

<span data-ttu-id="69585-253">在 .NET Framework 4.7.1 和更低版本中，WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> 和 <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> 控件不一致且在经典和高对比度主题中具有不正确的焦点视觉对象。</span><span class="sxs-lookup"><span data-stu-id="69585-253">In .NET Framework 4.7.1 and earlier versions, the WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> and <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> controls have inconsistent and, in Classic and High Contrast themes, incorrect focus visuals.</span></span>  <span data-ttu-id="69585-254">控件没有内容集时会出现这些问题。</span><span class="sxs-lookup"><span data-stu-id="69585-254">These issues occur in cases where the controls do not have any content set.</span></span>  <span data-ttu-id="69585-255">这会使得主题间的转换变得混乱且难以看到焦点视觉对象。</span><span class="sxs-lookup"><span data-stu-id="69585-255">This can make the transition between themes confusing and the focus visual hard to see.</span></span>

<span data-ttu-id="69585-256">现在，在 .NET Framework 4.7.2 中，主题间的这些视觉对象更加一致，并且在经典和高对比度主题中更轻松可见。</span><span class="sxs-lookup"><span data-stu-id="69585-256">In .NET Framework 4.7.2, these visuals are now more consistent across themes and more easily visible in Classic and High Contrast themes.</span></span>

<span data-ttu-id="69585-257">**在 WPF 应用程序中托管的 WinForms 控件**</span><span class="sxs-lookup"><span data-stu-id="69585-257">**WinForms controls hosted in a WPF application**</span></span>

<span data-ttu-id="69585-258">对于 .NET Framework 4.7.1 和更低版本中的 WPF 应用程序托管的 WinForms 控件，如果该层中的第一个或最后一个控件是 WPF <xref:System.Windows.Forms.Integration.ElementHost> 控件，那么用户不能按 Tab 退出 WinForms 层。</span><span class="sxs-lookup"><span data-stu-id="69585-258">For WinForms control hosted in a WPF application in .NET Framework 4.7.1 and earlier versions, users couldn't tab out of the WinForms layer if the first or last control in that layer is the WPF <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span> <span data-ttu-id="69585-259">现在，在 .NET Framework 4.7.2 中，用户能够按 Tab 退出 WinForms 层。</span><span class="sxs-lookup"><span data-stu-id="69585-259">In .NET Framework 4.7.2, users are now able to tab out of the WinForms layer.</span></span>

<span data-ttu-id="69585-260">但是，依赖于永不转义 WinForms 层的焦点的自动化应用程序不再会按预期工作。</span><span class="sxs-lookup"><span data-stu-id="69585-260">However, automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-471"></a><span data-ttu-id="69585-261">.NET Framework 4.7.1 中辅助功能的新增功能</span><span class="sxs-lookup"><span data-stu-id="69585-261">What's new in accessibility in .NET Framework 4.7.1</span></span>

<span data-ttu-id="69585-262">.NET Framework 4.7.1 在以下几个领域包含新增辅助功能：</span><span class="sxs-lookup"><span data-stu-id="69585-262">.NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="69585-263">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="69585-263">Windows Presentation Foundation (WPF)</span></span>](#wpf471)

- [<span data-ttu-id="69585-264">Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="69585-264">Windows Forms</span></span>](#winforms471)

- [<span data-ttu-id="69585-265">ASP.NET Web 控件</span><span class="sxs-lookup"><span data-stu-id="69585-265">ASP.NET web controls</span></span>](#aspnet471)

- [<span data-ttu-id="69585-266">.NET SDK 工具</span><span class="sxs-lookup"><span data-stu-id="69585-266">.NET SDK Tools</span></span>](#tools471)

- [<span data-ttu-id="69585-267">Windows Workflow Foundation (WF) 工作流设计器</span><span class="sxs-lookup"><span data-stu-id="69585-267">Windows Workflow Foundation (WF) Workflow Designer</span></span>](#wf471)

<a name="wpf471"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="69585-268">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="69585-268">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="69585-269">**屏幕阅读器改进**</span><span class="sxs-lookup"><span data-stu-id="69585-269">**Screen reader improvements**</span></span>

<span data-ttu-id="69585-270">如果启用了辅助功能改进，.NET Framework 4.7.1 包括以下可影响屏幕阅读器的增强功能：</span><span class="sxs-lookup"><span data-stu-id="69585-270">If accessibility improvements are enabled, .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="69585-271">在 .NET Framework 4.7 及更低版本中，<xref:System.Windows.Controls.Expander> 控件由屏幕阅读器宣称为按钮。</span><span class="sxs-lookup"><span data-stu-id="69585-271">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="69585-272">从 .NET Framework 4.7.1 开始，它们被正确地称为可展开/可折叠组。</span><span class="sxs-lookup"><span data-stu-id="69585-272">Starting with .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="69585-273">在 .NET Framework 4.7 及更低版本中，<xref:System.Windows.Controls.DataGridCell> 控件由屏幕阅读器宣称为“自定义”。</span><span class="sxs-lookup"><span data-stu-id="69585-273">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="69585-274">从 .NET Framework 4.7.1 开始，它们被正确地称为数据网格单元格（已本地化）。</span><span class="sxs-lookup"><span data-stu-id="69585-274">Starting with .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>

- <span data-ttu-id="69585-275">从 .NET Framework 4.7.1 开始，屏幕阅读器宣布可编辑 <xref:System.Windows.Controls.ComboBox> 的名称。</span><span class="sxs-lookup"><span data-stu-id="69585-275">Starting with .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="69585-276">在 .NET Framework 4.7 及更低版本中，<xref:System.Windows.Controls.PasswordBox> 控件被宣称为“视图中没有任何项”或有其他错误行为。</span><span class="sxs-lookup"><span data-stu-id="69585-276">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="69585-277">此问题已在 .NET Framework 4.7.1 及更高版本中解决。</span><span class="sxs-lookup"><span data-stu-id="69585-277">This issue is fixed starting with .NET Framework 4.7.1.</span></span>

<span data-ttu-id="69585-278">**UIAutomation LiveRegion 支持**</span><span class="sxs-lookup"><span data-stu-id="69585-278">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="69585-279">屏幕阅读器（如讲述人）可帮助用户阅读应用程序的 UI 内容，通常通过具有焦点的 UI 内容的文本到语音转换输出实现。</span><span class="sxs-lookup"><span data-stu-id="69585-279">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="69585-280">但是，如果 UI 元素更改，并且不具有焦点，则用户可能不会收到通知，并且可能会错过重要信息。</span><span class="sxs-lookup"><span data-stu-id="69585-280">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="69585-281">活动区域旨在解决此问题。</span><span class="sxs-lookup"><span data-stu-id="69585-281">Live regions aim at solving this problem.</span></span> <span data-ttu-id="69585-282">开发人员可使用它们来通知屏幕阅读器或任何其他 UIAutomation 客户端 UI 元素有重要更改。</span><span class="sxs-lookup"><span data-stu-id="69585-282">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="69585-283">然后，屏幕阅读器可确定向用户通知此更改的方式和时间。</span><span class="sxs-lookup"><span data-stu-id="69585-283">The screen reader can then decide how and when to inform the user of this change.</span></span>

<span data-ttu-id="69585-284">为了支持活动区域，向 WPF 添加了以下 API：</span><span class="sxs-lookup"><span data-stu-id="69585-284">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="69585-285"><xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> 和 <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> 字段，用于标识 LiveSetting 属性和 LiveRegionChanged 事件。</span><span class="sxs-lookup"><span data-stu-id="69585-285">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="69585-286">可通过使用 XAML 来进行设置。</span><span class="sxs-lookup"><span data-stu-id="69585-286">They can be set by using XAML.</span></span>

- <span data-ttu-id="69585-287">AutomationProperties.LiveSetting 附加属性，用于向屏幕阅读器通知 UI 更改对用户的重要性。</span><span class="sxs-lookup"><span data-stu-id="69585-287">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="69585-288"><xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> 属性，用于标识 AutomationProperties.LiveSetting 附加属性。</span><span class="sxs-lookup"><span data-stu-id="69585-288">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>

- <span data-ttu-id="69585-289"><xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> 方法，可替代该方法以提供 LiveSetting 值。</span><span class="sxs-lookup"><span data-stu-id="69585-289">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="69585-290"><xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> 和 <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> 方法，用于获取和设置 LiveSetting 值。</span><span class="sxs-lookup"><span data-stu-id="69585-290">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>

- <span data-ttu-id="69585-291"><xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> 枚举，用于定义以下可能的 LiveSetting 值：</span><span class="sxs-lookup"><span data-stu-id="69585-291">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

  - <span data-ttu-id="69585-292"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="69585-292"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="69585-293">如果活动区域的内容已更改，则该元素不会发送通知。</span><span class="sxs-lookup"><span data-stu-id="69585-293">The element does not send notifications if the content of the live region has changed.</span></span>
  - <span data-ttu-id="69585-294"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="69585-294"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="69585-295">如果活动区域的内容已更改，则该元素将发送非中断通知。</span><span class="sxs-lookup"><span data-stu-id="69585-295">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>

  - <span data-ttu-id="69585-296"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="69585-296"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="69585-297">如果活动区域的内容已更改，则该元素将发送中断通知。</span><span class="sxs-lookup"><span data-stu-id="69585-297">The element sends interruptive notifications if the content of the live region has changed.</span></span>

<span data-ttu-id="69585-298">可通过对相关元素设置 AutomationProperties.LiveSetting 属性来创建 LiveRegion，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="69585-298">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="69585-299">活动区域中的数据发生更改，并且需要通知屏幕阅读器时，可显式引发事件，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="69585-299">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```

```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="69585-300">**高对比度**</span><span class="sxs-lookup"><span data-stu-id="69585-300">**High contrast**</span></span>

<span data-ttu-id="69585-301">从 .NET Framework 4.7.1 开始，对多种 WPF 控件进行了高对比度改进。</span><span class="sxs-lookup"><span data-stu-id="69585-301">Starting with .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="69585-302">可在设置 <xref:System.Windows.SystemParameters.HighContrast%2A> 主题后看到这些改进。</span><span class="sxs-lookup"><span data-stu-id="69585-302">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="69585-303">这些方法包括：</span><span class="sxs-lookup"><span data-stu-id="69585-303">These include:</span></span>

- <span data-ttu-id="69585-304"><xref:System.Windows.Controls.Expander> 控件</span><span class="sxs-lookup"><span data-stu-id="69585-304"><xref:System.Windows.Controls.Expander> control</span></span>

  <span data-ttu-id="69585-305"><xref:System.Windows.Controls.Expander> 控件的焦点视觉对象现在可见。</span><span class="sxs-lookup"><span data-stu-id="69585-305">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="69585-306"><xref:System.Windows.Controls.ComboBox>、<xref:System.Windows.Controls.ListBox> 和 <xref:System.Windows.Controls.RadioButton> 控件的键盘视觉对象也可见。</span><span class="sxs-lookup"><span data-stu-id="69585-306">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="69585-307">例如：</span><span class="sxs-lookup"><span data-stu-id="69585-307">For example:</span></span>

  <span data-ttu-id="69585-308">在此之前:</span><span class="sxs-lookup"><span data-stu-id="69585-308">Before:</span></span>

  ![此屏幕截图中显示了一个有焦点的组合框控件，其中没有焦点视觉对象。](./media/whats-new-in-accessibility/expander-control-before.png)

  <span data-ttu-id="69585-310">之后：</span><span class="sxs-lookup"><span data-stu-id="69585-310">After:</span></span>

  ![此屏幕截图中显示了一个有焦点的组合框控件，其中控件文本周围显示了虚线。](./media/whats-new-in-accessibility/expander-control-after.png)

- <span data-ttu-id="69585-312"><xref:System.Windows.Controls.CheckBox> 和 <xref:System.Windows.Controls.RadioButton> 控件</span><span class="sxs-lookup"><span data-stu-id="69585-312"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>

  <span data-ttu-id="69585-313">在高对比度主题下选中时，<xref:System.Windows.Controls.CheckBox> 和 <xref:System.Windows.Controls.RadioButton> 控件中的文本更易于查看。</span><span class="sxs-lookup"><span data-stu-id="69585-313">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="69585-314">例如：</span><span class="sxs-lookup"><span data-stu-id="69585-314">For example:</span></span>

  <span data-ttu-id="69585-315">在此之前:</span><span class="sxs-lookup"><span data-stu-id="69585-315">Before:</span></span>

  ![此屏幕截图中显示了单选按钮和复选按钮，在高对比度主题下文本可见性差。](./media/whats-new-in-accessibility/high-contrast-radio-button-before.png)

  <span data-ttu-id="69585-317">之后：</span><span class="sxs-lookup"><span data-stu-id="69585-317">After:</span></span>

  ![高对比度主题上文本可见性高的单选和复选按钮的屏幕截图。](./media/whats-new-in-accessibility/high-contrast-radio-button-after.png)

- <span data-ttu-id="69585-319"><xref:System.Windows.Controls.ComboBox> 控件</span><span class="sxs-lookup"><span data-stu-id="69585-319"><xref:System.Windows.Controls.ComboBox> control</span></span>

  <span data-ttu-id="69585-320">从 .NET Framework 4.7.1 开始，已禁用的 <xref:System.Windows.Controls.ComboBox> 控件的边框与禁用的文本颜色相同。</span><span class="sxs-lookup"><span data-stu-id="69585-320">Starting with .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="69585-321">例如：</span><span class="sxs-lookup"><span data-stu-id="69585-321">For example:</span></span>

  <span data-ttu-id="69585-322">在此之前:</span><span class="sxs-lookup"><span data-stu-id="69585-322">Before:</span></span>

  ![此屏幕截图中显示了一个已禁用的组合框，其边框和空间文本具有不同的颜色。](./media/whats-new-in-accessibility/combo-disabled-before.png)

  <span data-ttu-id="69585-324">之后：</span><span class="sxs-lookup"><span data-stu-id="69585-324">After:</span></span>

  ![此屏幕截图中显示了一个已禁用的组合框，其边框和空间文本具有相同的颜色。](./media/whats-new-in-accessibility/combo-disabled-after.png)

  <span data-ttu-id="69585-326">此外，已禁用的按钮和具有焦点的按钮使用正确的主题颜色。</span><span class="sxs-lookup"><span data-stu-id="69585-326">In addition, disabled and focused buttons use the correct theme color.</span></span>

  <span data-ttu-id="69585-327">在此之前:</span><span class="sxs-lookup"><span data-stu-id="69585-327">Before:</span></span>

  ![此屏幕截图中显示了一个黑色按钮，按钮上有灰色文字“将焦点放到此处”。](./media/whats-new-in-accessibility/button-theme-colors-before.png)

  <span data-ttu-id="69585-329">之后：</span><span class="sxs-lookup"><span data-stu-id="69585-329">After:</span></span>

  ![带有黑色文本的蓝色按钮屏幕截图，文本显示“Focus Me”。](./media/whats-new-in-accessibility/button-theme-colors-after.png)

  <span data-ttu-id="69585-331">最后，在 .NET Framework 4.7 及更低版本中，将 <xref:System.Windows.Controls.ComboBox> 控件的样式设置为 `Toolbar.ComboBoxStyleKey` 会导致下拉箭头不可见。</span><span class="sxs-lookup"><span data-stu-id="69585-331">Finally, in .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="69585-332">此问题已在 .NET Framework 4.7.1 及更高版本中解决。</span><span class="sxs-lookup"><span data-stu-id="69585-332">This issue is fixed starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="69585-333">例如：</span><span class="sxs-lookup"><span data-stu-id="69585-333">For example:</span></span>

  <span data-ttu-id="69585-334">在此之前:</span><span class="sxs-lookup"><span data-stu-id="69585-334">Before:</span></span>

  ![此屏幕截图中显示了一个组合框控件，其中有一个不可见下拉箭头。](./media/whats-new-in-accessibility/combo-box-style-key-before.png)

  <span data-ttu-id="69585-336">之后：</span><span class="sxs-lookup"><span data-stu-id="69585-336">After:</span></span>

  ![显示下拉箭头的组合框控件的屏幕截图。](./media/whats-new-in-accessibility/combo-box-style-key-after.png)

- <span data-ttu-id="69585-338"><xref:System.Windows.Controls.DataGrid> 控件</span><span class="sxs-lookup"><span data-stu-id="69585-338"><xref:System.Windows.Controls.DataGrid> control</span></span>

  <span data-ttu-id="69585-339">从 .NET Framework 4.7.1 开始，<xref:System.Windows.Controls.DataGrid> 控件中的排序指示符箭头现在使用正确的主题颜色。</span><span class="sxs-lookup"><span data-stu-id="69585-339">Starting with .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="69585-340">例如：</span><span class="sxs-lookup"><span data-stu-id="69585-340">For example:</span></span>

  <span data-ttu-id="69585-341">在此之前:</span><span class="sxs-lookup"><span data-stu-id="69585-341">Before:</span></span>

  ![改进前的排序指示符箭头的屏幕截图。](./media/whats-new-in-accessibility/sort-indicator-before.png)

  <span data-ttu-id="69585-343">之后：</span><span class="sxs-lookup"><span data-stu-id="69585-343">After:</span></span>

  ![改进后的排序指示符箭头的屏幕截图。](./media/whats-new-in-accessibility/sort-indicator-after.png)

  <span data-ttu-id="69585-345">此外，在 .NET Framework 4.7 及更低版本中，在高对比度模式下，默认链接样式在鼠标悬停在其上时更改为不正确的颜色。</span><span class="sxs-lookup"><span data-stu-id="69585-345">In addition, in .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="69585-346">此问题已在 .NET Framework 4.7.1 及更高版本中解决。</span><span class="sxs-lookup"><span data-stu-id="69585-346">This is resolved starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="69585-347">同样，从 .NET Framework 4.7.1 开始，<xref:System.Windows.Controls.DataGrid> 复选框列对键盘焦点反馈使用预期的颜色。</span><span class="sxs-lookup"><span data-stu-id="69585-347">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with .NET Framework 4.7.1.</span></span>

  <span data-ttu-id="69585-348">在此之前:</span><span class="sxs-lookup"><span data-stu-id="69585-348">Before:</span></span>

  ![显示“点击此处！”的链接屏幕截图](./media/whats-new-in-accessibility/default-link-style-before.png)

  <span data-ttu-id="69585-351">之后：</span><span class="sxs-lookup"><span data-stu-id="69585-351">After:</span></span>

  ![显示“点击此处！”的链接屏幕截图](./media/whats-new-in-accessibility/default-link-style-after.png)

<span data-ttu-id="69585-354">有关 .NET Framework 4.7.1 中 WPF 辅助功能改进的详细信息，请参阅 [WPF 辅助功能改进](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf)。</span><span class="sxs-lookup"><span data-stu-id="69585-354">For more information on WPF accessibility improvements in .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

<a name="winforms471"></a>

### <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="69585-355">Windows 窗体辅助功能改进</span><span class="sxs-lookup"><span data-stu-id="69585-355">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="69585-356">在 .NET Framework 4.7.1 中，Windows 窗体 (WinForms) 包括以下几个方面的辅助功能改进。</span><span class="sxs-lookup"><span data-stu-id="69585-356">In .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="69585-357">**改进了高对比度模式下的显示**</span><span class="sxs-lookup"><span data-stu-id="69585-357">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="69585-358">从 .NET Framework 4.7.1 开始，多种 WinForms 控件改进了高对比度模式下在操作系统中的呈现方式。</span><span class="sxs-lookup"><span data-stu-id="69585-358">Starting with .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="69585-359">Windows 10 更改了一些高对比度系统颜色的值，而 Windows 窗体基于 Windows 10 Win32 框架。</span><span class="sxs-lookup"><span data-stu-id="69585-359">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="69585-360">为获得最佳体验，请运行最新版本的 Windows，并通过在测试应用程序中添加 app.manifest 文件选择使用最新的 OS 更改，同时取消注释 Windows 10 支持的 OS 行，最终结果如下所示：</span><span class="sxs-lookup"><span data-stu-id="69585-360">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!-- Windows 10 -->
<supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
```

<span data-ttu-id="69585-361">高对比度更改的一些示例包括：</span><span class="sxs-lookup"><span data-stu-id="69585-361">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="69585-362"><xref:System.Windows.Forms.MenuStrip> 项中的复选标记更易于查看。</span><span class="sxs-lookup"><span data-stu-id="69585-362">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="69585-363">选中后，禁用的 <xref:System.Windows.Forms.MenuStrip> 项更易于查看。</span><span class="sxs-lookup"><span data-stu-id="69585-363">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="69585-364">所选 <xref:System.Windows.Forms.Button> 控件中的文本与选中颜色形成鲜明对比。</span><span class="sxs-lookup"><span data-stu-id="69585-364">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="69585-365">禁用的文本更易于阅读。</span><span class="sxs-lookup"><span data-stu-id="69585-365">Disabled text is easier to read.</span></span> <span data-ttu-id="69585-366">例如：</span><span class="sxs-lookup"><span data-stu-id="69585-366">For example:</span></span>

  <span data-ttu-id="69585-367">在此之前:</span><span class="sxs-lookup"><span data-stu-id="69585-367">Before:</span></span>

  ![一个应用的屏幕截图，该应用在高对比度模式下运行着不同的控件，而尚未改进可访问性。](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-before.png)

  <span data-ttu-id="69585-369">之后：</span><span class="sxs-lookup"><span data-stu-id="69585-369">After:</span></span>

  ![应用程序的屏幕截图，在辅助功能改进之后，该应用程序使用在高对比度模式下运行的不同控件。](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-after.png)

- <span data-ttu-id="69585-371">“线程异常”对话框中的高对比度改进。</span><span class="sxs-lookup"><span data-stu-id="69585-371">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="69585-372">**改进了讲述人支持**</span><span class="sxs-lookup"><span data-stu-id="69585-372">**Improved Narrator support**</span></span>

<span data-ttu-id="69585-373">.NET Framework 4.7.1 中的 Windows 窗体对讲述人进行了以下辅助功改进：</span><span class="sxs-lookup"><span data-stu-id="69585-373">Windows Forms in .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="69585-374">讲述人以及其他 UI 自动化工具可访问 <xref:System.Windows.Forms.MonthCalendar> 控件。</span><span class="sxs-lookup"><span data-stu-id="69585-374">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="69585-375">当某个项的选中状态更改时，<xref:System.Windows.Forms.CheckedListBox> 控件会通知讲述人，因此用户可获知更改了列表项的值。</span><span class="sxs-lookup"><span data-stu-id="69585-375">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>

- <span data-ttu-id="69585-376"><xref:System.Windows.Forms.DataGridViewCell> 控件向讲述人报告正确的只读状态。</span><span class="sxs-lookup"><span data-stu-id="69585-376">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>

- <span data-ttu-id="69585-377">讲述人现在可以阅读已禁用的 <xref:System.Windows.Forms.ToolStripMenuItem> 文本，而以前它会跳过禁用的菜单项。</span><span class="sxs-lookup"><span data-stu-id="69585-377">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="69585-378">**增强了对 UIAutomation 辅助功能模式的支持**</span><span class="sxs-lookup"><span data-stu-id="69585-378">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="69585-379">从 .NET Framework 4.7.1 开始，辅助功能技术工具的开发人员可以利用常见的 API 辅助功能模式和多个 WinForms 控件的属性。</span><span class="sxs-lookup"><span data-stu-id="69585-379">Starting with .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="69585-380">这些辅助功能改进包括：</span><span class="sxs-lookup"><span data-stu-id="69585-380">These accessibility improvements include:</span></span>

- <span data-ttu-id="69585-381"><xref:System.Windows.Forms.ComboBox> 和 <xref:System.Windows.Forms.ToolStripSplitButton> 现在支持[展开/折叠模式](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="69585-381">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="69585-382"><xref:System.Windows.Forms.DataGridViewCheckBoxCell> 现在支持[切换模式](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="69585-382">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>

- <span data-ttu-id="69585-383"><xref:System.Windows.Forms.ToolStripItem> 控件支持 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> 属性和[展开/折叠模式](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="69585-383">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="69585-384"><xref:System.Windows.Forms.NumericUpDown> 和 <xref:System.Windows.Forms.DomainUpDown> 控件支持 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> 属性。</span><span class="sxs-lookup"><span data-stu-id="69585-384">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span></span>

<span data-ttu-id="69585-385">**改进了属性浏览器体验**</span><span class="sxs-lookup"><span data-stu-id="69585-385">**Improved property browser experience**</span></span>

<span data-ttu-id="69585-386">从 .NET Framework 4.7.1 开始，Windows 窗体包括以下改进：</span><span class="sxs-lookup"><span data-stu-id="69585-386">Starting with .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="69585-387">更好地通过各种下拉选择窗口使用键盘导航。</span><span class="sxs-lookup"><span data-stu-id="69585-387">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="69585-388">减少不必要的制表位。</span><span class="sxs-lookup"><span data-stu-id="69585-388">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="69585-389">更好地报告控件类型。</span><span class="sxs-lookup"><span data-stu-id="69585-389">Better reporting of control types.</span></span>
- <span data-ttu-id="69585-390">改进了讲述人行为。</span><span class="sxs-lookup"><span data-stu-id="69585-390">Improved narrator behavior.</span></span>

<a name="aspnet471"></a>

### <a name="aspnet-web-controls"></a><span data-ttu-id="69585-391">ASP.NET Web 控件</span><span class="sxs-lookup"><span data-stu-id="69585-391">ASP.NET web controls</span></span>

<span data-ttu-id="69585-392">自 .NET Framework 4.7.1 和 Visual Studio 2017 版本 15.3 起，ASP.NET 改进了 ASP.NET Web 控件与 Visual Studio 中的辅助功能技术配合使用的方式。</span><span class="sxs-lookup"><span data-stu-id="69585-392">Starting with .NET Framework 4.7.1 and Visual Studio 2017 version 15.3, ASP.NET improves how ASP.NET web controls work with accessibility technology in Visual Studio.</span></span> <span data-ttu-id="69585-393">包括以下更改：</span><span class="sxs-lookup"><span data-stu-id="69585-393">Changes include the following:</span></span>

- <span data-ttu-id="69585-394">在以下控件中实现缺失 UI 的辅助功能模式：例如“详细信息视图”向导中的“添加字段”对话框或“ListView”向导的“配置 ListView”对话框   。</span><span class="sxs-lookup"><span data-stu-id="69585-394">Changes to implement missing UI accessibility patterns in controls, like the **Add Field** dialog in the **Details View** wizard, or the **Configure ListView** dialog of the **ListView** wizard.</span></span>

- <span data-ttu-id="69585-395">改善在高对比度模式下（如“数据页导航字段编辑器”）的显示。</span><span class="sxs-lookup"><span data-stu-id="69585-395">Changes to improve the display in High Contrast mode, like the **Data Pager Fields Editor**.</span></span>

- <span data-ttu-id="69585-396">改善以下控件的键盘导航体验：例如 DataPager 控件的“编辑页导航字段”向导中的“字段”对话框、“配置 ObjectContext”对话框或“配置数据源”向导的“配置数据选择”对话框    。</span><span class="sxs-lookup"><span data-stu-id="69585-396">Changes to improve the keyboard navigation experiences for controls, like the **Fields** dialog in the **Edit Pager Fields** wizard of the DataPager control, the **Configure ObjectContext** dialog, or the **Configure Data Selection** dialog of the **Configure Data Source** wizard.</span></span>

<a name="tools471"></a>

### <a name="net-sdk-tools"></a><span data-ttu-id="69585-397">.NET SDK 工具</span><span class="sxs-lookup"><span data-stu-id="69585-397">.NET SDK Tools</span></span>

<span data-ttu-id="69585-398">[配置编辑器工具 (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) 和[服务跟踪查看器工具 (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) 通过修复各种辅助功能问题得到改进。</span><span class="sxs-lookup"><span data-stu-id="69585-398">The [Configuration Editor Tool (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) and [Service Trace Viewer Tool (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="69585-399">其中大多数都是一些小问题，如未定义名称或未正确实现某些 UI 自动化模式。</span><span class="sxs-lookup"><span data-stu-id="69585-399">Most of these were small issues, like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="69585-400">虽然许多用户不会意识到这些小问题的重要性，但使用屏幕阅读器等辅助技术的客户会发现这些 SDK 工具更易于访问。</span><span class="sxs-lookup"><span data-stu-id="69585-400">While many users won’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span>

<span data-ttu-id="69585-401">这些改进更改了某些旧行为，例如键盘焦点顺序。</span><span class="sxs-lookup"><span data-stu-id="69585-401">These enhancements change some previous behaviors, such as keyboard focus order.</span></span>

<a name="wf471"></a>

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="69585-402">Windows Workflow Foundation (WF) 工作流设计器</span><span class="sxs-lookup"><span data-stu-id="69585-402">Windows Workflow Foundation (WF) Workflow Designer</span></span>

<span data-ttu-id="69585-403">工作流设计器中的辅助功能更改包括：</span><span class="sxs-lookup"><span data-stu-id="69585-403">Accessibility changes in the Workflow Designer include the following:</span></span>

- <span data-ttu-id="69585-404">某些控件中 Tab 键顺序更改为从左到右以及从上到下：</span><span class="sxs-lookup"><span data-stu-id="69585-404">The tab order changes to left to right and top to bottom in some controls:</span></span>

  - <span data-ttu-id="69585-405">设置 <xref:System.ServiceModel.Activities.InitializeCorrelation> 活动相关数据的初始化相关窗口。</span><span class="sxs-lookup"><span data-stu-id="69585-405">The initialize correlation window for setting correlation data for the <xref:System.ServiceModel.Activities.InitializeCorrelation> activity.</span></span>

  - <span data-ttu-id="69585-406"><xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.SendReply> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 活动的内容定义窗口。</span><span class="sxs-lookup"><span data-stu-id="69585-406">The content definition window for the <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply> activities.</span></span>

- <span data-ttu-id="69585-407">通过键盘可以使用更多功能：</span><span class="sxs-lookup"><span data-stu-id="69585-407">More functions are available via the keyboard:</span></span>

  - <span data-ttu-id="69585-408">编辑活动的属性时，属性组在第一次聚焦时可以通过键盘折叠。</span><span class="sxs-lookup"><span data-stu-id="69585-408">When editing the properties of an activity, property groups can be collapsed by keyboard the first time they are focused.</span></span>

  - <span data-ttu-id="69585-409">警告图标可以通过键盘访问。</span><span class="sxs-lookup"><span data-stu-id="69585-409">Warning icons are accessible by keyboard.</span></span>

  - <span data-ttu-id="69585-410">“属性”窗口的“更多属性”按钮可以通过键盘访问 。</span><span class="sxs-lookup"><span data-stu-id="69585-410">The **More Properties** button in the **Properties** window is accessible by keyboard.</span></span>

  - <span data-ttu-id="69585-411">键盘用户可以访问工作流设计器“参数”和“变量”窗格的标题项 。</span><span class="sxs-lookup"><span data-stu-id="69585-411">Keyboard users can access the header items in the **Arguments** and **Variables** panes of the Workflow Designer.</span></span>

- <span data-ttu-id="69585-412">提升了聚焦项的可见性，例如当：</span><span class="sxs-lookup"><span data-stu-id="69585-412">Improved visibility of items with focus, such as when:</span></span>

  - <span data-ttu-id="69585-413">将行添加到工作流设计器和活动设计器使用的数据网格。</span><span class="sxs-lookup"><span data-stu-id="69585-413">Adding rows to data grids used by the Workflow Designer and activity designers.</span></span>

  - <span data-ttu-id="69585-414">在 <xref:System.ServiceModel.Activities.ReceiveReply> 和 <xref:System.ServiceModel.Activities.SendReply> 活动中按 Tab 键切换字段。</span><span class="sxs-lookup"><span data-stu-id="69585-414">Tabbing through fields in the <xref:System.ServiceModel.Activities.ReceiveReply> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>

  - <span data-ttu-id="69585-415">设置变量或自变量的默认值</span><span class="sxs-lookup"><span data-stu-id="69585-415">Setting default values for variables or arguments</span></span>

- <span data-ttu-id="69585-416">屏幕读取器现在可以正确识别：</span><span class="sxs-lookup"><span data-stu-id="69585-416">Screen readers can now correctly recognize:</span></span>

  - <span data-ttu-id="69585-417">工作流设计器中设置的断点。</span><span class="sxs-lookup"><span data-stu-id="69585-417">Breakpoints set in the workflow designer.</span></span>

  - <span data-ttu-id="69585-418"><xref:System.Activities.Statements.FlowSwitch%601>、<xref:System.Activities.Statements.FlowDecision> 和 <xref:System.ServiceModel.Activities.CorrelationScope> 活动。</span><span class="sxs-lookup"><span data-stu-id="69585-418">The <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, and <xref:System.ServiceModel.Activities.CorrelationScope> activities.</span></span>
  - <span data-ttu-id="69585-419"><xref:System.ServiceModel.Activities.Receive> 活动的内容。</span><span class="sxs-lookup"><span data-stu-id="69585-419">The contents of the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>

  - <span data-ttu-id="69585-420"><xref:System.Activities.Statements.InvokeMethod> 活动的目标类型。</span><span class="sxs-lookup"><span data-stu-id="69585-420">The Target Type for the <xref:System.Activities.Statements.InvokeMethod> activity.</span></span>

  - <span data-ttu-id="69585-421"><xref:System.Activities.Statements.TryCatch> 活动中的“异常”组合框和“最终”部分。</span><span class="sxs-lookup"><span data-stu-id="69585-421">The Exception combo box and the Finally section in the <xref:System.Activities.Statements.TryCatch> activity.</span></span>

  - <span data-ttu-id="69585-422">消息传递活动（<xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.SendReply> 和 <xref:System.ServiceModel.Activities.ReceiveReply>）中的“消息类型”组合框、“添加相关初始化表达式”窗口中的拆分器、“内容定义”窗口和“CorrelatesOn 定义”窗口。</span><span class="sxs-lookup"><span data-stu-id="69585-422">The Message Type combo box, the splitter in the Add Correlation Initializers window, the Content Definition window, and the CorrelatesOn Definition window in the messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>

  - <span data-ttu-id="69585-423">状态机转换和转换目标。</span><span class="sxs-lookup"><span data-stu-id="69585-423">State machine transitions and transitions destinations.</span></span>

  - <span data-ttu-id="69585-424"><xref:System.Activities.Statements.FlowDecision> 活动上的注释和连接器。</span><span class="sxs-lookup"><span data-stu-id="69585-424">Annotations and connectors on <xref:System.Activities.Statements.FlowDecision> activities.</span></span>

  - <span data-ttu-id="69585-425">活动的上下文（右键单击）菜单。</span><span class="sxs-lookup"><span data-stu-id="69585-425">The context (right-click) menus for activities.</span></span>

  - <span data-ttu-id="69585-426">属性值编辑器、“清除搜索”按钮、“按类别”和“按字母顺序”排序按钮以及属性网格中的“表达式编辑器”对话框。</span><span class="sxs-lookup"><span data-stu-id="69585-426">The property value editors, the Clear Search button, the By Category and Alphabetical sort buttons, and the Expression Editor dialog in the properties grid.</span></span>

  - <span data-ttu-id="69585-427">工作流设计器中的缩放百分比。</span><span class="sxs-lookup"><span data-stu-id="69585-427">The zoom percentage in the Workflow Designer.</span></span>

  - <span data-ttu-id="69585-428"><xref:System.Activities.Statements.Parallel> 和 <xref:System.Activities.Statements.Pick> 活动中的分隔符。</span><span class="sxs-lookup"><span data-stu-id="69585-428">The separator in <xref:System.Activities.Statements.Parallel> and <xref:System.Activities.Statements.Pick> activities.</span></span>

  - <span data-ttu-id="69585-429"><xref:System.Activities.Statements.InvokeDelegate> 活动。</span><span class="sxs-lookup"><span data-stu-id="69585-429">The <xref:System.Activities.Statements.InvokeDelegate> activity.</span></span>

  - <span data-ttu-id="69585-430">字典活动（`Microsoft.Activities.AddToDictionary<TKey,TValue>`、`Microsoft.Activities.RemoveFromDictionary<TKey,TValue>` 等）的“选择类型”窗口。</span><span class="sxs-lookup"><span data-stu-id="69585-430">The Select Types window for dictionary activities (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`, etc.).</span></span>

  - <span data-ttu-id="69585-431">“浏览和选择 .NET 类型”窗口。</span><span class="sxs-lookup"><span data-stu-id="69585-431">The Browse and Select .NET Type window.</span></span>

  - <span data-ttu-id="69585-432">工作流设计器中的痕迹导航。</span><span class="sxs-lookup"><span data-stu-id="69585-432">Breadcrumbs in the Workflow Designer.</span></span>

- <span data-ttu-id="69585-433">选择高对比度主题的用户将看到工作流设计器及其控件可见性的许多改进，例如元素间更好的对比度和焦点元素更明显的选择框。</span><span class="sxs-lookup"><span data-stu-id="69585-433">Users who choose High Contrast themes will see many improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="69585-434">请参阅</span><span class="sxs-lookup"><span data-stu-id="69585-434">See also</span></span>

- [<span data-ttu-id="69585-435">.NET Framework 的新增功能</span><span class="sxs-lookup"><span data-stu-id="69585-435">What's new in the .NET Framework</span></span>](index.md)

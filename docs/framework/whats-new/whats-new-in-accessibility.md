---
title: .NET Framework 中辅助功能的新增功能
ms.custom: updateeachrelease
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
ms.openlocfilehash: 4243599f44749e7b38ebe78ca88b8ec2a9390650
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249716"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="1c603-102">.NET Framework 中辅助功能的新增功能</span><span class="sxs-lookup"><span data-stu-id="1c603-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="1c603-103">.NET Framework 旨在让用户更轻松地使用应用程序。</span><span class="sxs-lookup"><span data-stu-id="1c603-103">The .NET Framework aims at making applications more accessible for your users.</span></span> <span data-ttu-id="1c603-104">辅助功能使应用程序能够为辅助技术用户提供最佳体验。</span><span class="sxs-lookup"><span data-stu-id="1c603-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="1c603-105">从 .NET Framework 4.7.1 开始，.NET Framework 包括大量辅助功能改进，使开发人员能够创建易于访问的应用程序。</span><span class="sxs-lookup"><span data-stu-id="1c603-105">Starting with .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span>

## <a name="accessibility-switches"></a><span data-ttu-id="1c603-106">辅助功能开关</span><span class="sxs-lookup"><span data-stu-id="1c603-106">Accessibility switches</span></span>

<span data-ttu-id="1c603-107">如果应用面向 .NET Framework 4.7 或更低版本，但是在 .NET Framework 4.7.1 或更高版本上运行，可以将应用配置为选择使用辅助功能。</span><span class="sxs-lookup"><span data-stu-id="1c603-107">You can configure your app to opt into accessibility features if it targets .NET Framework 4.7 or an earlier version but is running on .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="1c603-108">如果应用面向 .NET Framework 4.7.1 或更高版本，还可以将应用配置为使用旧版功能（且不使用辅助功能）。</span><span class="sxs-lookup"><span data-stu-id="1c603-108">You can also configure your app to use legacy features (and not take advantage of accessibility features) if it targets .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="1c603-109">包括辅助功能的每个 .NET Framework 版本都有一个特定于版本的辅助开关，请将它添加到应用程序配置文件 [`<runtime>`](../configure-apps/file-schema/runtime/index.md) 部分中的 [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="1c603-109">Each version of the .NET Framework that includes accessibility features has a version-specific accessibility switch, which you add to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> <span data-ttu-id="1c603-110">以下是受支持的开关：</span><span class="sxs-lookup"><span data-stu-id="1c603-110">The following are the supported switches:</span></span>

|<span data-ttu-id="1c603-111">Version</span><span class="sxs-lookup"><span data-stu-id="1c603-111">Version</span></span>|<span data-ttu-id="1c603-112">开关</span><span class="sxs-lookup"><span data-stu-id="1c603-112">Switch</span></span>|
|---|---|
|<span data-ttu-id="1c603-113">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="1c603-113">.NET Framework 4.7.1</span></span>|<span data-ttu-id="1c603-114">"Switch.UseLegacyAccessibilityFeatures"</span><span class="sxs-lookup"><span data-stu-id="1c603-114">"Switch.UseLegacyAccessibilityFeatures"</span></span>|
|<span data-ttu-id="1c603-115">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="1c603-115">.NET Framework 4.7.2</span></span>|<span data-ttu-id="1c603-116">"Switch.UseLegacyAccessibilityFeatures.2"</span><span class="sxs-lookup"><span data-stu-id="1c603-116">"Switch.UseLegacyAccessibilityFeatures.2"</span></span>|
|<span data-ttu-id="1c603-117">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="1c603-117">.NET Framework 4.8</span></span>|<span data-ttu-id="1c603-118">"Switch.UseLegacyAccessibilityFeatures.3"</span><span class="sxs-lookup"><span data-stu-id="1c603-118">"Switch.UseLegacyAccessibilityFeatures.3"</span></span>|

### <a name="taking-advantage-of-accessibility-enhancements"></a><span data-ttu-id="1c603-119">利用辅助功能改进</span><span class="sxs-lookup"><span data-stu-id="1c603-119">Taking advantage of accessibility enhancements</span></span>

<span data-ttu-id="1c603-120">对于面向 .NET Framework 4.7.1 或更高版本的应用程序，新的辅助功能默认情况下处于启用状态。</span><span class="sxs-lookup"><span data-stu-id="1c603-120">The new accessibility features are enabled by default for applications that target .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="1c603-121">此外，对于面向 .NET Framework 早期版本，但在 .NET Framework 4.7.1 或更高版本上运行的应用程序，可通过将开关添加到应用程序配置文件 [`<runtime>`](../configure-apps/file-schema/runtime/index.md) 部分中的 [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 元素并将其值设为 `false` 来选择弃用旧辅助功能行为（因而利用辅助功能改进）。</span><span class="sxs-lookup"><span data-stu-id="1c603-121">In addition, applications that target an earlier version of the .NET Framework but are running on .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby take advantage of accessibility improvements) by adding switches to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `false`.</span></span> <span data-ttu-id="1c603-122">以下代码演示如何选择使用 .NET Framework 4.7.1 中引入的辅助功能改进：</span><span class="sxs-lookup"><span data-stu-id="1c603-122">The following shows how to opt in to accessibility enhancements introduced in .NET Framework 4.7.1:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="1c603-123">如果选择使用更高的 .NET Framework 版本中的辅助功能，还必须显式选择使用更低 .NET Framework 版本的功能。</span><span class="sxs-lookup"><span data-stu-id="1c603-123">If you choose to opt in to accessibility features in a later version of the .NET Framework, you must also explicitly opt in to the features from earlier versions of the .NET Framework.</span></span> <span data-ttu-id="1c603-124">通过配置应用以利用 .NET Framework 4.7.1 和 4.7.2 中的辅助功能改进需要以下 [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 元素：</span><span class="sxs-lookup"><span data-stu-id="1c603-124">Configuring your app to take advantage of accessibility improvements in both .NET Framework 4.7.1 and 4.7.2 requires the following [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

<span data-ttu-id="1c603-125">通过配置应用以利用 .NET Framework 4.7.1、4.7.2 和 4.8 中的辅助功能改进需要以下 [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 元素：</span><span class="sxs-lookup"><span data-stu-id="1c603-125">Configuring your app to take advantage of accessibility improvements in .NET Framework 4.7.1, 4.7.2, and 4.8 requires the following [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a><span data-ttu-id="1c603-126">还原旧行为</span><span class="sxs-lookup"><span data-stu-id="1c603-126">Restoring legacy behavior</span></span>

<span data-ttu-id="1c603-127">对于面向 .NET Framework 4.7.1 或更高版本的应用程序，可通过将开关添加到应用程序配置文件 [`<runtime>`](../configure-apps/file-schema/runtime/index.md) 部分中的 [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 元素并将其值设为 `true` 来禁用辅助功能。</span><span class="sxs-lookup"><span data-stu-id="1c603-127">Applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding switches to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `true`.</span></span> <span data-ttu-id="1c603-128">例如，以下配置选择弃用 .NET Framework 4.7.2 中引入的辅助功能：</span><span class="sxs-lookup"><span data-stu-id="1c603-128">For example, the following configuration opts out of accessibility features introduced in .NET Framework 4.7.2:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-net-framework-48"></a><span data-ttu-id="1c603-129">.NET Framework 4.8 中辅助功能的新增功能</span><span class="sxs-lookup"><span data-stu-id="1c603-129">What's new in accessibility in .NET Framework 4.8</span></span>

<span data-ttu-id="1c603-130">.NET Framework 4.8 在以下几个领域包含新增辅助功能：</span><span class="sxs-lookup"><span data-stu-id="1c603-130">.NET Framework 4.8 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="1c603-131">Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="1c603-131">Windows Forms</span></span>](#winforms48)

- [<span data-ttu-id="1c603-132">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="1c603-132">Windows Presentation Foundation (WPF)</span></span>](#wpf48)

- [<span data-ttu-id="1c603-133">Windows Workflow Foundation (WF) 工作流设计器</span><span class="sxs-lookup"><span data-stu-id="1c603-133">Windows Workflow Foundation (WF) workflow designer</span></span>](#wf48)

<a name="winforms48" />

### <a name="windows-forms"></a><span data-ttu-id="1c603-134">Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="1c603-134">Windows Forms</span></span>

<span data-ttu-id="1c603-135">在 .NET Framework 4.8 中，Windows 窗体将对 LiveRegions 和通知事件的支持添加到多个常用控件中。</span><span class="sxs-lookup"><span data-stu-id="1c603-135">In .NET Framework 4.8, Windows Forms adds support for LiveRegions and Notification Events to many commonly used controls.</span></span> <span data-ttu-id="1c603-136">它还会在用户使用键盘导航到控件时添加工具提示支持。</span><span class="sxs-lookup"><span data-stu-id="1c603-136">It also adds support for ToolTips when a user navigates to a control by using the keyboard.</span></span>

<span data-ttu-id="1c603-137">**标签和 StatusStrips 中的 UIA LiveRegions 支持**</span><span class="sxs-lookup"><span data-stu-id="1c603-137">**UIA LiveRegions Support in Labels and StatusStrips**</span></span>

<span data-ttu-id="1c603-138">UIA LiveRegions 允许应用程序开发人员将用户工作位置之外的某个控件中的文本更改通知给屏幕阅读器。</span><span class="sxs-lookup"><span data-stu-id="1c603-138">UIA LiveRegions allow application developers to notify screen readers of a text change in a control that is located apart from the location where the user is working.</span></span> <span data-ttu-id="1c603-139">例如，对于显示连接状态的 <xref:System.Windows.Forms.StatusStrip> 控件，这很有用。</span><span class="sxs-lookup"><span data-stu-id="1c603-139">This is useful, for example, for a <xref:System.Windows.Forms.StatusStrip> control that shows a connection status.</span></span> <span data-ttu-id="1c603-140">如果连接断开且状态发生更改，开发人员可能会希望将此情况通知给屏幕阅读器。</span><span class="sxs-lookup"><span data-stu-id="1c603-140">If the connection is dropped and the status changes, the developer might want to notify the screen reader.</span></span>

<span data-ttu-id="1c603-141">从 .NET Framework 4.8 开始，Windows 窗体同时为 <xref:System.Windows.Forms.Label> 和 <xref:System.Windows.Forms.StatusStrip> 控件实现 UIA LiveRegions。</span><span class="sxs-lookup"><span data-stu-id="1c603-141">Starting with .NET Framework 4.8, Windows Forms implements UIA LiveRegions for both the <xref:System.Windows.Forms.Label> and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="1c603-142">例如，以下代码在名为 `label1` 的 <xref:System.Windows.Forms.Label> 控件中使用 LiveRegion：</span><span class="sxs-lookup"><span data-stu-id="1c603-142">For example, the following code uses the LiveRegion in a <xref:System.Windows.Forms.Label> control named `label1`:</span></span>

```csharp
public Form1()
{
   InitializeComponent();
   label1.AutomationLiveSetting = AutomationLiveSetting.Polite;
}

…
Label1.Text = “Ready!”;
```

<span data-ttu-id="1c603-143">无论用户在何处与应用程序交互，讲述人都会宣布“准备就绪”。</span><span class="sxs-lookup"><span data-stu-id="1c603-143">Narrator announces “Ready” regardless of where the user is interacting with the application.</span></span>

<span data-ttu-id="1c603-144">还可以将 <xref:System.Windows.Forms.UserControl> 实现为 LiveRegion：</span><span class="sxs-lookup"><span data-stu-id="1c603-144">You can also implement your <xref:System.Windows.Forms.UserControl> as a LiveRegion:</span></span>

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

<span data-ttu-id="1c603-145">**UIA 通知事件**</span><span class="sxs-lookup"><span data-stu-id="1c603-145">**UIA notification events**</span></span>

<span data-ttu-id="1c603-146">Windows 10 Fall Creators Update 中引入的 UIA 通知事件允许应用程序引发 UIA 事件，这使得讲述人仅根据你为事件提供的文本来进行宣读，而无需在 UI 中使用相应的控件。</span><span class="sxs-lookup"><span data-stu-id="1c603-146">The UIA Notification event, introduced in Windows 10 Fall Creators Update, allows your app to raise a UIA event, which leads to Narrator simply making an announcement based on text you supply with the event, without the need to have a corresponding control in the UI.</span></span> <span data-ttu-id="1c603-147">在某些情况下，这是一种能够显着改善应用辅助功能的简单方法。</span><span class="sxs-lookup"><span data-stu-id="1c603-147">In some scenarios, this is a straightforward way to dramatically improve the accessibility of your app.</span></span> <span data-ttu-id="1c603-148">也可以用于通知可能需要很长时间的某些进程的进度。</span><span class="sxs-lookup"><span data-stu-id="1c603-148">In can also be useful to notify of the progress of some process that may take a long time.</span></span> <span data-ttu-id="1c603-149">有关 UIA 通知事件的详细信息，请参阅[桌面应用程序是否可以利用新的 UI 通知事件？](https://docs.microsoft.com/archive/blogs/winuiautomation/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need)。</span><span class="sxs-lookup"><span data-stu-id="1c603-149">For more information about UIA Notification Events, see [Can your desktop app leverage the new UI Notification event?](https://docs.microsoft.com/archive/blogs/winuiautomation/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need).</span></span>

<span data-ttu-id="1c603-150">下面的示例会引发[通知事件](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A)：</span><span class="sxs-lookup"><span data-stu-id="1c603-150">The following example raises the [Notification event](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A):</span></span>

```csharp
MethodInfo raiseMethod = typeof(AccessibleObject).GetMethod("RaiseAutomationNotification");
if (raiseMethod != null) {
   raiseMethod.Invoke(progressBar1.AccessibilityObject, new object[3] {/*Other*/ 4, /*All*/ 2, "The progress is 50%." });
}
```

<span data-ttu-id="1c603-151">**键盘访问工具提示**</span><span class="sxs-lookup"><span data-stu-id="1c603-151">**ToolTips on keyboard access**</span></span>

<span data-ttu-id="1c603-152">在面向 .NET Framework 4.7.2 及更早版本的应用程序中，只能通过将鼠标指针移到控件上，才能触发控件[工具提示](xref:System.Windows.Forms.ToolTip)。</span><span class="sxs-lookup"><span data-stu-id="1c603-152">In applications that target .NET Framework 4.7.2 and earlier versions, a control [tooltip](xref:System.Windows.Forms.ToolTip) can only be triggered to pop up by moving a mouse pointer into the control.</span></span> <span data-ttu-id="1c603-153">从 .NET Framework 4.8 开始，键盘用户可以通过使用 Tab 键或箭头键（具有或不具有修饰键）来聚焦控件，从而触发控件的工具提示。</span><span class="sxs-lookup"><span data-stu-id="1c603-153">Starting with .NET Framework 4.8, a keyboard user can trigger a control’s tooltip by focusing the control using a Tab key or arrow keys with or without modifier keys.</span></span> <span data-ttu-id="1c603-154">要实现这一特定的辅助功能优化效果，需要额外的 [AppContext 开关](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)：</span><span class="sxs-lookup"><span data-stu-id="1c603-154">This particular accessibility enhancement requires an additional [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):</span></span>

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

<span data-ttu-id="1c603-155">下图显示用户使用键盘选中按钮时的工具提示。</span><span class="sxs-lookup"><span data-stu-id="1c603-155">The following figure shows the tooltip when the user has selected a button with the keyboard.</span></span>

![用户使用键盘导航到按钮时工具提示的屏幕截图。](./media/whats-new-in-accessibility/select-tooltip-with-keyboard.png)

<a name="wpf48" />

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="1c603-157">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="1c603-157">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="1c603-158">从 .NET Framework 4.8 开始，WPF 包括大量辅助功能改进。</span><span class="sxs-lookup"><span data-stu-id="1c603-158">Starting with .NET Framework 4.8, WPF includes a number of accessibility improvements.</span></span>

<span data-ttu-id="1c603-159">**屏幕讲述人不再宣读可见性为“折叠”或“隐藏”的元素**</span><span class="sxs-lookup"><span data-stu-id="1c603-159">**Screen narrators no longer announce elements with Collapsed or Hidden visibility**</span></span>

<span data-ttu-id="1c603-160">可见性为“折叠”或“隐藏”的元素不再被屏幕讲述人宣读。</span><span class="sxs-lookup"><span data-stu-id="1c603-160">Elements with collapsed or hidden visibility are no longer announced by screen reader.</span></span> <span data-ttu-id="1c603-161">如果向用户宣读包含可见性为 <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> 或 <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> 的元素的用户界面，屏幕阅读器可能会错误呈现这些界面。</span><span class="sxs-lookup"><span data-stu-id="1c603-161">User interfaces that contain elements with a Visibility of <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> or <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> can be misrepresented by screen readers if they are announced to the user.</span></span> <span data-ttu-id="1c603-162">从 .NET Framework 4.8 开始，WPF 不再在 UIAutomation 树的控制视图中包含折叠或隐藏的元素，屏幕阅读器无法再宣读这些元素。</span><span class="sxs-lookup"><span data-stu-id="1c603-162">Starting with .NET Framework 4.8, WPF no longer includes collapsed or hidden elements in the Control View of the UIAutomation tree, so the screen readers can no longer announce these elements.</span></span>

<span data-ttu-id="1c603-163">**与非基于修饰器的文本选择配合使用的 SelectionTextBrush 属性**</span><span class="sxs-lookup"><span data-stu-id="1c603-163">**SelectionTextBrush property for use with non-Adorner based text selection**</span></span>

<span data-ttu-id="1c603-164">在 .NET Framework 4.7.2 中，WPF 添加了无需使用修饰器层即可绘制 <xref:System.Windows.Controls.TextBox> 和 <xref:System.Windows.Controls.PasswordBox> 文本选择的功能。</span><span class="sxs-lookup"><span data-stu-id="1c603-164">In the .NET Framework 4.7.2, WPF added the ability to draw <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.PasswordBox> text selection without using the Adorner layer.</span></span> <span data-ttu-id="1c603-165">此方案中所选文本的前景色由 <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType> 决定。</span><span class="sxs-lookup"><span data-stu-id="1c603-165">The foreground color of the selected text in this scenario was dictated by <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="1c603-166">.NET Framework 4.8 添加了一个新属性 `SelectionTextBrush`，允许开发人员在使用非基于修饰器的文本选择时为所选文本选择特定画笔。</span><span class="sxs-lookup"><span data-stu-id="1c603-166">.NET Framework 4.8 adds a new property, `SelectionTextBrush`, that allows developers to select the specific brush for the selected text when using non-Adorner based text selection.</span></span> <span data-ttu-id="1c603-167">此属性仅适用于 <xref:System.Windows.Controls.Primitives.TextBoxBase> 派生的控件和启用了非基于修饰器的文本选择功能的 WPF 应用程序中的 <xref:System.Windows.Controls.PasswordBox> 控件。</span><span class="sxs-lookup"><span data-stu-id="1c603-167">This property works only on <xref:System.Windows.Controls.Primitives.TextBoxBase>-derived controls and the <xref:System.Windows.Controls.PasswordBox> control in WPF applications with non-Adorner-based text selection enabled.</span></span> <span data-ttu-id="1c603-168">该属性不适用于 <xref:System.Windows.Controls.RichTextBox> 控件。</span><span class="sxs-lookup"><span data-stu-id="1c603-168">It does not work on the <xref:System.Windows.Controls.RichTextBox> control.</span></span> <span data-ttu-id="1c603-169">如果未启用非基于修饰器的文本选择功能，则忽略此属性。</span><span class="sxs-lookup"><span data-stu-id="1c603-169">If non-Adorner-based text selection is not enabled, this property is ignored.</span></span>

<span data-ttu-id="1c603-170">要使用此属性，只需将其添加到 XAML 代码，并使用适当的画笔或绑定。</span><span class="sxs-lookup"><span data-stu-id="1c603-170">To use this property, simply add it to your XAML code and use the appropriate brush or binding.</span></span> <span data-ttu-id="1c603-171">生成的文本选择如下所示：</span><span class="sxs-lookup"><span data-stu-id="1c603-171">The resulting text selection looks like this:</span></span>

![运行中应用的屏幕截图，其中选中了“Hello World”文字。](./media/whats-new-in-accessibility/selectiontextbrush-property.png)

<span data-ttu-id="1c603-173">可以结合使用 `SelectionBrush` 和 `SelectionTextBrush` 属性来生成你认为合适的任何背景色和前景色组合。</span><span class="sxs-lookup"><span data-stu-id="1c603-173">You can combine the use of the `SelectionBrush` and `SelectionTextBrush` properties to generate any background and foreground color combination that you deem appropriate.</span></span>

<span data-ttu-id="1c603-174">**对 UIAutomation ControllerFor 属性的支持**</span><span class="sxs-lookup"><span data-stu-id="1c603-174">**Support for the UIAutomation ControllerFor property**</span></span>

<span data-ttu-id="1c603-175">UIAutomation 的 `ControllerFor` 属性返回一系列由支持该属性的自动化元素操纵的自动化元素。</span><span class="sxs-lookup"><span data-stu-id="1c603-175">UIAutomation’s `ControllerFor` property returns an array of automation elements that are manipulated by the automation element that supports this property.</span></span> <span data-ttu-id="1c603-176">此属性通常用于自动建议辅助功能。</span><span class="sxs-lookup"><span data-stu-id="1c603-176">This property is commonly used for Auto-suggest accessibility.</span></span> <span data-ttu-id="1c603-177">应在自动化元素会影响应用程序 UI 或桌面的一个或多个段时使用 `ControllerFor`。</span><span class="sxs-lookup"><span data-stu-id="1c603-177">`ControllerFor` is used when an automation element affects one or more segments of the application UI or the desktop.</span></span> <span data-ttu-id="1c603-178">否则，很难将控制操作的影响与 UI 元素关联。</span><span class="sxs-lookup"><span data-stu-id="1c603-178">Otherwise, it is hard to associate the impact of the control operation with UI elements.</span></span> <span data-ttu-id="1c603-179">此功能增加了控件为 `ControllerFor` 属性提供值的功能。</span><span class="sxs-lookup"><span data-stu-id="1c603-179">This feature adds the ability for controls to provide a value for the `ControllerFor` property.</span></span>

<span data-ttu-id="1c603-180">.NET framework 4.8 添加了新的虚拟方法 <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="1c603-180">.NET Framework 4.8 adds a new virtual method, <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1c603-181">要为 `ControllerFor` 属性提供值，只需替代此方法并为此 <xref:System.Windows.Automation.Peers.AutomationPeer> 操作的控件返回 `List<AutomationPeer>`：</span><span class="sxs-lookup"><span data-stu-id="1c603-181">To provide a value for the `ControllerFor` property, simply override this method and return a `List<AutomationPeer>` for the controls being manipulated by this <xref:System.Windows.Automation.Peers.AutomationPeer>:</span></span>

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

<span data-ttu-id="1c603-182">**键盘访问工具提示**</span><span class="sxs-lookup"><span data-stu-id="1c603-182">**Tooltips on keyboard access**</span></span>

<span data-ttu-id="1c603-183">在 .NET Framework 4.7.2 和更早版本中，仅当用户将鼠标光标悬停在控件上时，系统才会显示工具提示。</span><span class="sxs-lookup"><span data-stu-id="1c603-183">In .NET Framework 4.7.2 and earlier versions, tooltips display only when the user hovers the mouse cursor over a control.</span></span> <span data-ttu-id="1c603-184">在 .NET Framework 4.8 中，工具提示还会在键盘聚焦时显示，也可以通过键盘快捷方式显示。</span><span class="sxs-lookup"><span data-stu-id="1c603-184">In .NET Framework 4.8, tooltips also display on keyboard focus, as well as via a keyboard shortcut.</span></span>

<span data-ttu-id="1c603-185">要启用此功能，应用程序需要面向 .NET Framework 4.8，或使用 `Switch.UseLegacyAccessibilityFeatures.3` 和 `Switch.UseLegacyToolTipDisplay` [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 开关来选择加入。</span><span class="sxs-lookup"><span data-stu-id="1c603-185">To enable this feature, an application needs to target .NET Framework 4.8 or opt-in by using the `Switch.UseLegacyAccessibilityFeatures.3` and `Switch.UseLegacyToolTipDisplay` [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switches.</span></span> <span data-ttu-id="1c603-186">下面是一个示例应用程序配置文件：</span><span class="sxs-lookup"><span data-stu-id="1c603-186">The following is a sample application configuration file:</span></span>

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

<span data-ttu-id="1c603-187">启用后，一旦控件接收到键盘焦点，包含工具提示的所有控件都会显示工具提示。</span><span class="sxs-lookup"><span data-stu-id="1c603-187">Once enabled, all controls that contain a tooltip display it once the control receives keyboard focus.</span></span> <span data-ttu-id="1c603-188">随时间推移或当键盘焦点发生变化时，可关闭工具提示。</span><span class="sxs-lookup"><span data-stu-id="1c603-188">The tooltip can be dismissed over time or when the keyboard focus changes.</span></span> <span data-ttu-id="1c603-189">用户还可以通过使用新的键盘快捷键 Ctrl+Shift+F10 手动关闭工具提示。</span><span class="sxs-lookup"><span data-stu-id="1c603-189">Users can also dismiss the tooltip manually by using a new keyboard shortcut, Ctrl + Shift + F10.</span></span> <span data-ttu-id="1c603-190">关闭工具提示后，可以使用相同的键盘快捷键再次显示。</span><span class="sxs-lookup"><span data-stu-id="1c603-190">Once the tooltip has been dismissed it can be displayed again by using the same keyboard shortcut.</span></span>

> [!NOTE]
> <span data-ttu-id="1c603-191"><xref:System.Windows.Controls.Ribbon.Ribbon> 控件上的[功能区工具提示](xref:System.Windows.Controls.Ribbon.RibbonToolTip)不在键盘聚焦时显示；它们仅通过键盘快捷键显示。</span><span class="sxs-lookup"><span data-stu-id="1c603-191">[Ribbon tooltips](xref:System.Windows.Controls.Ribbon.RibbonToolTip) on <xref:System.Windows.Controls.Ribbon.Ribbon> controls won’t show on keyboard focus; they only show via the keyboard shortcut.</span></span>

<span data-ttu-id="1c603-192">**添加了对 SizeOfSet 和 PositionInSet UIAutomation 属性的支持**</span><span class="sxs-lookup"><span data-stu-id="1c603-192">**Added Support for SizeOfSet and PositionInSet UIAutomation properties**</span></span>

<span data-ttu-id="1c603-193">Windows 10 引入了两个新的 UIAutomation 属性（`SizeOfSet` 和 `PositionInSet`），应用程序用其描述集合中的项数。</span><span class="sxs-lookup"><span data-stu-id="1c603-193">Windows 10 introduced two new UIAutomation properties, `SizeOfSet` and `PositionInSet`, which are used by applications to describe the count of items in a set.</span></span> <span data-ttu-id="1c603-194">然后，UIAutomation 客户端应用程序（如屏幕阅读器）可以向某个应用程序查询这些属性，并宣布应用程序 UI 的准确表示形式。</span><span class="sxs-lookup"><span data-stu-id="1c603-194">UIAutomation client applications such as screen readers can then query an application for these properties and announce an accurate representation of the application’s UI.</span></span>

<span data-ttu-id="1c603-195">从 .NET Framework 4.8 开始，WPF 向 WPF 应用程序中的 UIAutomation 公开这两个属性。</span><span class="sxs-lookup"><span data-stu-id="1c603-195">Starting with .NET Framework 4.8, WPF  exposes these two properties to UIAutomation in WPF applications.</span></span> <span data-ttu-id="1c603-196">这可以通过以下两种方式实现：</span><span class="sxs-lookup"><span data-stu-id="1c603-196">This can be accomplished in two ways:</span></span>

- <span data-ttu-id="1c603-197">通过使用依赖项属性。</span><span class="sxs-lookup"><span data-stu-id="1c603-197">By using dependency properties.</span></span>

  <span data-ttu-id="1c603-198">WPF 添加了两个新的依赖项属性：<xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> 和 <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="1c603-198">WPF adds two new dependency properties, <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1c603-199">开发人员可以使用 XAML 来设置它们的值：</span><span class="sxs-lookup"><span data-stu-id="1c603-199">A developer can use XAML to set their values:</span></span>

  ```xaml
  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="1">Button 1</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="2">Button 2</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="3">Button 3</Button>
  ```

- <span data-ttu-id="1c603-200">通过替代 AutomationPeer 虚拟方法。</span><span class="sxs-lookup"><span data-stu-id="1c603-200">By overriding AutomationPeer virtual methods.</span></span>

  <span data-ttu-id="1c603-201"><xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> 和 <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> 虚拟方法已添加到 AutomationPeer 类中。</span><span class="sxs-lookup"><span data-stu-id="1c603-201">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> and <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> virtual methods been added to the AutomationPeer class.</span></span> <span data-ttu-id="1c603-202">开发人员可以通过替代这些方法为 `SizeOfSet` 和 `PositionInSet` 提供值，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="1c603-202">A developer can provide values for `SizeOfSet` and `PositionInSet` by overriding these methods, as shown in the following example:</span></span>

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

<span data-ttu-id="1c603-203">此外，开发人员无需执行其他操作，<xref:System.Windows.Controls.ItemsControl> 实例中的项会自动为这些属性提供值。</span><span class="sxs-lookup"><span data-stu-id="1c603-203">In addition, items in <xref:System.Windows.Controls.ItemsControl> instances provide a value for these properties automatically without additional action from the developer.</span></span> <span data-ttu-id="1c603-204">如果将 <xref:System.Windows.Controls.ItemsControl> 归组，则组的集合表示为一个集，并且每个组计为一个单独的集，该组内的每个项提供其在该组内的位置以及该组的大小。</span><span class="sxs-lookup"><span data-stu-id="1c603-204">If an <xref:System.Windows.Controls.ItemsControl> is grouped, the collection of groups is represented as a set, and each group is counted as a separate set, with each item inside that group providing its position inside that group as well as the size of the group.</span></span> <span data-ttu-id="1c603-205">虚拟化不会影响自动值。</span><span class="sxs-lookup"><span data-stu-id="1c603-205">Automatic values are not affected by virtualization.</span></span> <span data-ttu-id="1c603-206">即使没有实现某个项，它仍然会计入集的总大小，并影响其在同级项集中的位置。</span><span class="sxs-lookup"><span data-stu-id="1c603-206">Even if an item is not realized, it is still counted toward the total size of the set and affects the position in the set of its sibling items.</span></span>

<span data-ttu-id="1c603-207">仅当应用程序面向 .NET Framework 4.8 时，才会提供自动值。</span><span class="sxs-lookup"><span data-stu-id="1c603-207">Automatic values are only provided if the application targets .NET Framework 4.8.</span></span> <span data-ttu-id="1c603-208">对于面向 .NET Framework 早期版本的应用程序，可以设置 `Switch.UseLegacyAccessibilityFeatures.3` [AppContext 开关](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)，如以下 App.config 文件中所示：</span><span class="sxs-lookup"><span data-stu-id="1c603-208">For applications that target an earlier version of the .NET Framework, you can set the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), as shown in the following App.config file:</span></span>

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

<a name="wf48" />

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="1c603-209">Windows Workflow Foundation (WF) 工作流设计器</span><span class="sxs-lookup"><span data-stu-id="1c603-209">Windows Workflow Foundation (WF) workflow designer</span></span>

<span data-ttu-id="1c603-210">.NET Framework 4.8 中的工作流设计器包含以下更改：</span><span class="sxs-lookup"><span data-stu-id="1c603-210">The workflow designer includes the following changes in .NET Framework 4.8:</span></span>

- <span data-ttu-id="1c603-211">使用讲述人的用户将体验到 FlowSwitch 事例标签的改进。</span><span class="sxs-lookup"><span data-stu-id="1c603-211">Users using Narrator will see improvements in FlowSwitch case labels.</span></span>

- <span data-ttu-id="1c603-212">使用讲述人的用户将体验到按钮描述的改进。</span><span class="sxs-lookup"><span data-stu-id="1c603-212">Users using Narrator will see improvements in button descriptions.</span></span>

- <span data-ttu-id="1c603-213">选择高对比度主题的用户将看到工作流设计器及其控件可见性方面的改进，例如元素间的对比度效果更好和用于焦点元素的更明显的选择框。</span><span class="sxs-lookup"><span data-stu-id="1c603-213">Users who choose High Contrast themes will see improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

<span data-ttu-id="1c603-214">如果应用程序面向 .NET Framework 4.7.2 或更早版本，则可以通过在应用程序配置文件中将 `Switch.UseLegacyAccessibilityFeatures.3` [AppContext 开关](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)设置为 `false` 来选择这些更改。</span><span class="sxs-lookup"><span data-stu-id="1c603-214">If your application targets .NET Framework 4.7.2 or an earlier version, you can opt into these changes by setting the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to `false` in your application configuration file.</span></span> <span data-ttu-id="1c603-215">有关详细信息，请参阅本文中的[利用辅助功能改进](#taking-advantage-of-accessibility-enhancements)部分。</span><span class="sxs-lookup"><span data-stu-id="1c603-215">For more information, see the [Taking advantage of accessibility enhancements](#taking-advantage-of-accessibility-enhancements) section in this article.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-472"></a><span data-ttu-id="1c603-216">.NET Framework 4.7.2 中辅助功能的新增功能</span><span class="sxs-lookup"><span data-stu-id="1c603-216">What's new in accessibility in .NET Framework 4.7.2</span></span>

<span data-ttu-id="1c603-217">.NET Framework 4.7.2 在以下几个领域包含新增辅助功能：</span><span class="sxs-lookup"><span data-stu-id="1c603-217">.NET Framework 4.7.2 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="1c603-218">Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="1c603-218">Windows Forms</span></span>](#winforms472)

- [<span data-ttu-id="1c603-219">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="1c603-219">Windows Presentation Foundation (WPF)</span></span>](#wpf472)

<a name="winforms472"></a>

### <a name="windows-forms"></a><span data-ttu-id="1c603-220">Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="1c603-220">Windows Forms</span></span>

<span data-ttu-id="1c603-221">**高对比度主题中的 OS 定义的颜色**</span><span class="sxs-lookup"><span data-stu-id="1c603-221">**OS-defined colors in High Contrast themes**</span></span>

<span data-ttu-id="1c603-222">自 .NET Framework 4.7.2 起，Windows 窗体使用高对比度主题中的操作系统定义的颜色。</span><span class="sxs-lookup"><span data-stu-id="1c603-222">Starting with .NET Framework 4.7.2, Windows Forms uses colors defined by the operating system in High Contrast themes.</span></span> <span data-ttu-id="1c603-223">这会影响以下控件：</span><span class="sxs-lookup"><span data-stu-id="1c603-223">This affects the following controls:</span></span>

- <span data-ttu-id="1c603-224"><xref:System.Windows.Forms.ToolStripDropDownButton> 控件的下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="1c603-224">The drop-down arrow of the <xref:System.Windows.Forms.ToolStripDropDownButton> control.</span></span>

- <span data-ttu-id="1c603-225"><xref:System.Windows.Forms.ButtonBase.FlatStyle> 设为 <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> 或 <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType> 的 <xref:System.Windows.Forms.Button>、<xref:System.Windows.Forms.RadioButton> 和 <xref:System.Windows.Forms.CheckBox> 控件。</span><span class="sxs-lookup"><span data-stu-id="1c603-225">The <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with <xref:System.Windows.Forms.ButtonBase.FlatStyle> set to <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> or <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1c603-226">以前，所选文本和背景颜色对比度低，难以阅读。</span><span class="sxs-lookup"><span data-stu-id="1c603-226">Previously, selected text and background colors were not contrasting and were hard to read.</span></span>

- <span data-ttu-id="1c603-227"><xref:System.Windows.Forms.Control.Enabled> 属性设为 `false` 的 <xref:System.Windows.Forms.GroupBox> 中所包含的控件。</span><span class="sxs-lookup"><span data-stu-id="1c603-227">Controls contained within a <xref:System.Windows.Forms.GroupBox> that has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="1c603-228">在高对比度模式下，<xref:System.Windows.Forms.ToolStripButton>、<xref:System.Windows.Forms.ToolStripComboBox> 和 <xref:System.Windows.Forms.ToolStripDropDownButton> 控件的亮度对比度提高。</span><span class="sxs-lookup"><span data-stu-id="1c603-228">The <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, and <xref:System.Windows.Forms.ToolStripDropDownButton> controls, which have an increased luminosity contrast ratio in High Contrast Mode.</span></span>

- <span data-ttu-id="1c603-229"><xref:System.Windows.Forms.DataGridViewLinkCell> 的 <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> 属性。</span><span class="sxs-lookup"><span data-stu-id="1c603-229">The <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> property of the <xref:System.Windows.Forms.DataGridViewLinkCell>.</span></span>

<span data-ttu-id="1c603-230">**讲述人改进**</span><span class="sxs-lookup"><span data-stu-id="1c603-230">**Narrator improvements**</span></span>

<span data-ttu-id="1c603-231">自 .NET Framework 4.7.2 起，讲述人支持在以下几个方面改进：</span><span class="sxs-lookup"><span data-stu-id="1c603-231">Starting with .NET Framework 4.7.2, Narrator support is enhanced as follows:</span></span>

- <span data-ttu-id="1c603-232">它在公布 <xref:System.Windows.Forms.ToolStripMenuItem> 的文本时会公布 <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> 属性的值。</span><span class="sxs-lookup"><span data-stu-id="1c603-232">It announces the value of the <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> property when announcing the text of a <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>

- <span data-ttu-id="1c603-233">当 <xref:System.Windows.Forms.ToolStripMenuItem> 的 <xref:System.Windows.Forms.Control.Enabled> 属性设置为 `false` 时，它会有所指示。</span><span class="sxs-lookup"><span data-stu-id="1c603-233">It indicates when a <xref:System.Windows.Forms.ToolStripMenuItem> has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="1c603-234">当 <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> 属性设置为 `true` 时，它会针对复选框的状态给出反馈。</span><span class="sxs-lookup"><span data-stu-id="1c603-234">It gives feedback on the state of a check box when the <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> property is set to `true`.</span></span>

- <span data-ttu-id="1c603-235">讲述人扫描模式焦点顺序与 ClickOnce 下载对话框窗口中控件的视觉顺序一致。</span><span class="sxs-lookup"><span data-stu-id="1c603-235">Narrator's Scan Mode focus order is consistent with the visual order of the controls on the ClickOnce download dialog window.</span></span>

<span data-ttu-id="1c603-236">**DataGridView 改进**</span><span class="sxs-lookup"><span data-stu-id="1c603-236">**DataGridView improvements**</span></span>

<span data-ttu-id="1c603-237">自 .NET Framework 4.7.2 起，<xref:System.Windows.Forms.DataGridView> 控件引入了以下辅助功能改进：</span><span class="sxs-lookup"><span data-stu-id="1c603-237">Starting with .NET Framework 4.7.2, the <xref:System.Windows.Forms.DataGridView> control has introduced the following accessibility improvements:</span></span>

- <span data-ttu-id="1c603-238">可以使用键盘对行进行排序。</span><span class="sxs-lookup"><span data-stu-id="1c603-238">Rows can be sorted using the keyboard.</span></span> <span data-ttu-id="1c603-239">用户可使用 F3 按当前列排序。</span><span class="sxs-lookup"><span data-stu-id="1c603-239">A user can use the F3 key in order to sort by the current column.</span></span>

- <span data-ttu-id="1c603-240">若 <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> 设置为 <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>，当用户按 Tab 键遍历当前行中的单元格时，列标题将更改颜色来指示当前列。</span><span class="sxs-lookup"><span data-stu-id="1c603-240">When the <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> is set to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, the column header changes color to indicate the current column as the user tabs through the cells in the current row.</span></span>

- <span data-ttu-id="1c603-241"><xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> 的 <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> 属性返回正确的父控件。</span><span class="sxs-lookup"><span data-stu-id="1c603-241">The <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> property of a  <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> returns the correct parent control.</span></span>

<span data-ttu-id="1c603-242">**改进了视觉提示**</span><span class="sxs-lookup"><span data-stu-id="1c603-242">**Improved visual cues**</span></span>

- <span data-ttu-id="1c603-243">具有空 <xref:System.Windows.Forms.ButtonBase.Text> 属性的 <xref:System.Windows.Forms.RadioButton> 和 <xref:System.Windows.Forms.CheckBox> 控件在接收到焦点时会显示焦点指示器。</span><span class="sxs-lookup"><span data-stu-id="1c603-243">The <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with an empty <xref:System.Windows.Forms.ButtonBase.Text> property  display a focus indicator when they receive the focus.</span></span>

<span data-ttu-id="1c603-244">**改进了属性网格支持**</span><span class="sxs-lookup"><span data-stu-id="1c603-244">**Improved Property Grid Support**</span></span>

- <span data-ttu-id="1c603-245">现在，仅在 PropertyGrid 元素启用时，<xref:System.Windows.Forms.PropertyGrid> 控件子元素才会为 <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> 属性返回 `true`。</span><span class="sxs-lookup"><span data-stu-id="1c603-245">The <xref:System.Windows.Forms.PropertyGrid> control child elements now return a `true` for the  <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> property only when a PropertyGrid element is enabled.</span></span>

- <span data-ttu-id="1c603-246">仅在用户可更改 PropertyGrid 元素时，<xref:System.Windows.Forms.PropertyGrid> 控件子元素才会为 <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> 属性返回 `false`。</span><span class="sxs-lookup"><span data-stu-id="1c603-246">The <xref:System.Windows.Forms.PropertyGrid> control child elements return a `false` for the <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> property only when a PropertyGrid element can be changed by the user.</span></span>

<span data-ttu-id="1c603-247">**改进了的键盘导航**</span><span class="sxs-lookup"><span data-stu-id="1c603-247">**Improved keyboard navigation**</span></span>

- <span data-ttu-id="1c603-248"><xref:System.Windows.Forms.ToolStripButton> 控件允许在焦点包含在 <xref:System.Windows.Forms.ToolStripPanel>（其 <xref:System.Windows.Forms.ToolStripPanel.TabStop> 属性设置为 `true`）中时进行聚焦</span><span class="sxs-lookup"><span data-stu-id="1c603-248">The <xref:System.Windows.Forms.ToolStripButton> control allows focus when contained within a <xref:System.Windows.Forms.ToolStripPanel> that has the <xref:System.Windows.Forms.ToolStripPanel.TabStop> property set to `true`</span></span>

<a name="wpf472"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="1c603-249">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="1c603-249">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="1c603-250">**对复选框和单选按钮控件的更改**</span><span class="sxs-lookup"><span data-stu-id="1c603-250">**Changes to the CheckBox and RadioButton controls**</span></span>

<span data-ttu-id="1c603-251">在 .NET Framework 4.7.1 和更低版本中，WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> 和 <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> 控件不一致且在经典和高对比度主题中具有不正确的焦点视觉对象。</span><span class="sxs-lookup"><span data-stu-id="1c603-251">In .NET Framework 4.7.1 and earlier versions, the WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> and <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> controls have inconsistent and, in Classic and High Contrast themes, incorrect focus visuals.</span></span>  <span data-ttu-id="1c603-252">控件没有内容集时会出现这些问题。</span><span class="sxs-lookup"><span data-stu-id="1c603-252">These issues occur in cases where the controls do not have any content set.</span></span>  <span data-ttu-id="1c603-253">这会使得主题间的转换变得混乱且难以看到焦点视觉对象。</span><span class="sxs-lookup"><span data-stu-id="1c603-253">This can make the transition between themes confusing and the focus visual hard to see.</span></span>

<span data-ttu-id="1c603-254">现在，在 .NET Framework 4.7.2 中，主题间的这些视觉对象更加一致，并且在经典和高对比度主题中更轻松可见。</span><span class="sxs-lookup"><span data-stu-id="1c603-254">In .NET Framework 4.7.2, these visuals are now more consistent across themes and more easily visible in Classic and High Contrast themes.</span></span>

<span data-ttu-id="1c603-255">**在 WPF 应用程序中托管的 WinForms 控件**</span><span class="sxs-lookup"><span data-stu-id="1c603-255">**WinForms controls hosted in a WPF application**</span></span>

<span data-ttu-id="1c603-256">对于 .NET Framework 4.7.1 和更低版本中的 WPF 应用程序托管的 WinForms 控件，如果该层中的第一个或最后一个控件是 WPF <xref:System.Windows.Forms.Integration.ElementHost> 控件，那么用户不能按 Tab 退出 WinForms 层。</span><span class="sxs-lookup"><span data-stu-id="1c603-256">For WinForms control hosted in a WPF application in .NET Framework 4.7.1 and earlier versions, users couldn't tab out of the WinForms layer if the first or last control in that layer is the WPF <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span> <span data-ttu-id="1c603-257">现在，在 .NET Framework 4.7.2 中，用户能够按 Tab 退出 WinForms 层。</span><span class="sxs-lookup"><span data-stu-id="1c603-257">In .NET Framework 4.7.2, users are now able to tab out of the WinForms layer.</span></span>

<span data-ttu-id="1c603-258">但是，依赖于永不转义 WinForms 层的焦点的自动化应用程序不再会按预期工作。</span><span class="sxs-lookup"><span data-stu-id="1c603-258">However, automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-471"></a><span data-ttu-id="1c603-259">.NET Framework 4.7.1 中辅助功能的新增功能</span><span class="sxs-lookup"><span data-stu-id="1c603-259">What's new in accessibility in .NET Framework 4.7.1</span></span>

<span data-ttu-id="1c603-260">.NET Framework 4.7.1 在以下几个领域包含新增辅助功能：</span><span class="sxs-lookup"><span data-stu-id="1c603-260">.NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="1c603-261">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="1c603-261">Windows Presentation Foundation (WPF)</span></span>](#wpf471)

- [<span data-ttu-id="1c603-262">Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="1c603-262">Windows Forms</span></span>](#winforms471)

- [<span data-ttu-id="1c603-263">ASP.NET Web 控件</span><span class="sxs-lookup"><span data-stu-id="1c603-263">ASP.NET web controls</span></span>](#aspnet471)

- [<span data-ttu-id="1c603-264">.NET SDK 工具</span><span class="sxs-lookup"><span data-stu-id="1c603-264">.NET SDK Tools</span></span>](#tools471)

- [<span data-ttu-id="1c603-265">Windows Workflow Foundation (WF) 工作流设计器</span><span class="sxs-lookup"><span data-stu-id="1c603-265">Windows Workflow Foundation (WF) Workflow Designer</span></span>](#wf471)

<a name="wpf471"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="1c603-266">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="1c603-266">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="1c603-267">**屏幕阅读器改进**</span><span class="sxs-lookup"><span data-stu-id="1c603-267">**Screen reader improvements**</span></span>

<span data-ttu-id="1c603-268">如果启用了辅助功能改进，.NET Framework 4.7.1 包括以下可影响屏幕阅读器的增强功能：</span><span class="sxs-lookup"><span data-stu-id="1c603-268">If accessibility improvements are enabled, .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="1c603-269">在 .NET Framework 4.7 及更低版本中，<xref:System.Windows.Controls.Expander> 控件由屏幕阅读器宣称为按钮。</span><span class="sxs-lookup"><span data-stu-id="1c603-269">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="1c603-270">从 .NET Framework 4.7.1 开始，它们被正确地称为可展开/可折叠组。</span><span class="sxs-lookup"><span data-stu-id="1c603-270">Starting with .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="1c603-271">在 .NET Framework 4.7 及更低版本中，<xref:System.Windows.Controls.DataGridCell> 控件由屏幕阅读器宣称为“自定义”。</span><span class="sxs-lookup"><span data-stu-id="1c603-271">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="1c603-272">从 .NET Framework 4.7.1 开始，它们被正确地称为数据网格单元格（已本地化）。</span><span class="sxs-lookup"><span data-stu-id="1c603-272">Starting with .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>

- <span data-ttu-id="1c603-273">从 .NET Framework 4.7.1 开始，屏幕阅读器宣布可编辑 <xref:System.Windows.Controls.ComboBox> 的名称。</span><span class="sxs-lookup"><span data-stu-id="1c603-273">Starting with .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="1c603-274">在 .NET Framework 4.7 及更低版本中，<xref:System.Windows.Controls.PasswordBox> 控件被宣称为“视图中没有任何项”或有其他错误行为。</span><span class="sxs-lookup"><span data-stu-id="1c603-274">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="1c603-275">此问题已在 .NET Framework 4.7.1 及更高版本中解决。</span><span class="sxs-lookup"><span data-stu-id="1c603-275">This issue is fixed starting with .NET Framework 4.7.1.</span></span>

<span data-ttu-id="1c603-276">**UIAutomation LiveRegion 支持**</span><span class="sxs-lookup"><span data-stu-id="1c603-276">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="1c603-277">屏幕阅读器（如讲述人）可帮助用户阅读应用程序的 UI 内容，通常通过具有焦点的 UI 内容的文本到语音转换输出实现。</span><span class="sxs-lookup"><span data-stu-id="1c603-277">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="1c603-278">但是，如果 UI 元素更改，并且不具有焦点，则用户可能不会收到通知，并且可能会错过重要信息。</span><span class="sxs-lookup"><span data-stu-id="1c603-278">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="1c603-279">活动区域旨在解决此问题。</span><span class="sxs-lookup"><span data-stu-id="1c603-279">Live regions aim at solving this problem.</span></span> <span data-ttu-id="1c603-280">开发人员可使用它们来通知屏幕阅读器或任何其他 UIAutomation 客户端 UI 元素有重要更改。</span><span class="sxs-lookup"><span data-stu-id="1c603-280">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="1c603-281">然后，屏幕阅读器可确定向用户通知此更改的方式和时间。</span><span class="sxs-lookup"><span data-stu-id="1c603-281">The screen reader can then decide how and when to inform the user of this change.</span></span>

<span data-ttu-id="1c603-282">为了支持活动区域，向 WPF 添加了以下 API：</span><span class="sxs-lookup"><span data-stu-id="1c603-282">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="1c603-283"><xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> 和 <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> 字段，用于标识 LiveSetting 属性和 LiveRegionChanged 事件。</span><span class="sxs-lookup"><span data-stu-id="1c603-283">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="1c603-284">可通过使用 XAML 来进行设置。</span><span class="sxs-lookup"><span data-stu-id="1c603-284">They can be set by using XAML.</span></span>

- <span data-ttu-id="1c603-285">AutomationProperties.LiveSetting 附加属性，用于向屏幕阅读器通知 UI 更改对用户的重要性。</span><span class="sxs-lookup"><span data-stu-id="1c603-285">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="1c603-286"><xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> 属性，用于标识 AutomationProperties.LiveSetting 附加属性。</span><span class="sxs-lookup"><span data-stu-id="1c603-286">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>

- <span data-ttu-id="1c603-287"><xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> 方法，可替代该方法以提供 LiveSetting 值。</span><span class="sxs-lookup"><span data-stu-id="1c603-287">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="1c603-288"><xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> 和 <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> 方法，用于获取和设置 LiveSetting 值。</span><span class="sxs-lookup"><span data-stu-id="1c603-288">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>

- <span data-ttu-id="1c603-289"><xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> 枚举，用于定义以下可能的 LiveSetting 值：</span><span class="sxs-lookup"><span data-stu-id="1c603-289">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

  - <span data-ttu-id="1c603-290"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="1c603-290"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1c603-291">如果活动区域的内容已更改，则该元素不会发送通知。</span><span class="sxs-lookup"><span data-stu-id="1c603-291">The element does not send notifications if the content of the live region has changed.</span></span>
  - <span data-ttu-id="1c603-292"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="1c603-292"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1c603-293">如果活动区域的内容已更改，则该元素将发送非中断通知。</span><span class="sxs-lookup"><span data-stu-id="1c603-293">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>

  - <span data-ttu-id="1c603-294"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="1c603-294"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1c603-295">如果活动区域的内容已更改，则该元素将发送中断通知。</span><span class="sxs-lookup"><span data-stu-id="1c603-295">The element sends interruptive notifications if the content of the live region has changed.</span></span>

<span data-ttu-id="1c603-296">可通过对相关元素设置 AutomationProperties.LiveSetting 属性来创建 LiveRegion，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="1c603-296">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="1c603-297">活动区域中的数据发生更改，并且需要通知屏幕阅读器时，可显式引发事件，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="1c603-297">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```

```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="1c603-298">**高对比度**</span><span class="sxs-lookup"><span data-stu-id="1c603-298">**High contrast**</span></span>

<span data-ttu-id="1c603-299">从 .NET Framework 4.7.1 开始，对多种 WPF 控件进行了高对比度改进。</span><span class="sxs-lookup"><span data-stu-id="1c603-299">Starting with .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="1c603-300">可在设置 <xref:System.Windows.SystemParameters.HighContrast%2A> 主题后看到这些改进。</span><span class="sxs-lookup"><span data-stu-id="1c603-300">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="1c603-301">这些方法包括：</span><span class="sxs-lookup"><span data-stu-id="1c603-301">These include:</span></span>

- <span data-ttu-id="1c603-302"><xref:System.Windows.Controls.Expander> 控件</span><span class="sxs-lookup"><span data-stu-id="1c603-302"><xref:System.Windows.Controls.Expander> control</span></span>

  <span data-ttu-id="1c603-303"><xref:System.Windows.Controls.Expander> 控件的焦点视觉对象现在可见。</span><span class="sxs-lookup"><span data-stu-id="1c603-303">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="1c603-304"><xref:System.Windows.Controls.ComboBox>、<xref:System.Windows.Controls.ListBox> 和 <xref:System.Windows.Controls.RadioButton> 控件的键盘视觉对象也可见。</span><span class="sxs-lookup"><span data-stu-id="1c603-304">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="1c603-305">例如：</span><span class="sxs-lookup"><span data-stu-id="1c603-305">For example:</span></span>

  <span data-ttu-id="1c603-306">在此之前:</span><span class="sxs-lookup"><span data-stu-id="1c603-306">Before:</span></span>

  ![此屏幕截图中显示了一个有焦点的组合框控件，其中没有焦点视觉对象。](./media/whats-new-in-accessibility/expander-control-before.png)

  <span data-ttu-id="1c603-308">之后：</span><span class="sxs-lookup"><span data-stu-id="1c603-308">After:</span></span>

  ![此屏幕截图中显示了一个有焦点的组合框控件，其中控件文本周围显示了虚线。](./media/whats-new-in-accessibility/expander-control-after.png)

- <span data-ttu-id="1c603-310"><xref:System.Windows.Controls.CheckBox> 和 <xref:System.Windows.Controls.RadioButton> 控件</span><span class="sxs-lookup"><span data-stu-id="1c603-310"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>

  <span data-ttu-id="1c603-311">在高对比度主题下选中时，<xref:System.Windows.Controls.CheckBox> 和 <xref:System.Windows.Controls.RadioButton> 控件中的文本更易于查看。</span><span class="sxs-lookup"><span data-stu-id="1c603-311">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="1c603-312">例如：</span><span class="sxs-lookup"><span data-stu-id="1c603-312">For example:</span></span>

  <span data-ttu-id="1c603-313">在此之前:</span><span class="sxs-lookup"><span data-stu-id="1c603-313">Before:</span></span>

  ![此屏幕截图中显示了单选按钮和复选按钮，在高对比度主题下文本可见性差。](./media/whats-new-in-accessibility/high-contrast-radio-button-before.png)

  <span data-ttu-id="1c603-315">之后：</span><span class="sxs-lookup"><span data-stu-id="1c603-315">After:</span></span>

  ![高对比度主题上文本可见性高的单选和复选按钮的屏幕截图。](./media/whats-new-in-accessibility/high-contrast-radio-button-after.png)

- <span data-ttu-id="1c603-317"><xref:System.Windows.Controls.ComboBox> 控件</span><span class="sxs-lookup"><span data-stu-id="1c603-317"><xref:System.Windows.Controls.ComboBox> control</span></span>

  <span data-ttu-id="1c603-318">从 .NET Framework 4.7.1 开始，已禁用的 <xref:System.Windows.Controls.ComboBox> 控件的边框与禁用的文本颜色相同。</span><span class="sxs-lookup"><span data-stu-id="1c603-318">Starting with .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="1c603-319">例如：</span><span class="sxs-lookup"><span data-stu-id="1c603-319">For example:</span></span>

  <span data-ttu-id="1c603-320">在此之前:</span><span class="sxs-lookup"><span data-stu-id="1c603-320">Before:</span></span>

  ![此屏幕截图中显示了一个已禁用的组合框，其边框和空间文本具有不同的颜色。](./media/whats-new-in-accessibility/combo-disabled-before.png)

  <span data-ttu-id="1c603-322">之后：</span><span class="sxs-lookup"><span data-stu-id="1c603-322">After:</span></span>

  ![此屏幕截图中显示了一个已禁用的组合框，其边框和空间文本具有相同的颜色。](./media/whats-new-in-accessibility/combo-disabled-after.png)

  <span data-ttu-id="1c603-324">此外，已禁用的按钮和具有焦点的按钮使用正确的主题颜色。</span><span class="sxs-lookup"><span data-stu-id="1c603-324">In addition, disabled and focused buttons use the correct theme color.</span></span>

  <span data-ttu-id="1c603-325">在此之前:</span><span class="sxs-lookup"><span data-stu-id="1c603-325">Before:</span></span>

  ![此屏幕截图中显示了一个黑色按钮，按钮上有灰色文字“将焦点放到此处”。](./media/whats-new-in-accessibility/button-theme-colors-before.png)

  <span data-ttu-id="1c603-327">之后：</span><span class="sxs-lookup"><span data-stu-id="1c603-327">After:</span></span>

  ![带有黑色文本的蓝色按钮屏幕截图，文本显示“Focus Me”。](./media/whats-new-in-accessibility/button-theme-colors-after.png)

  <span data-ttu-id="1c603-329">最后，在 .NET Framework 4.7 及更低版本中，将 <xref:System.Windows.Controls.ComboBox> 控件的样式设置为 `Toolbar.ComboBoxStyleKey` 会导致下拉箭头不可见。</span><span class="sxs-lookup"><span data-stu-id="1c603-329">Finally, in .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="1c603-330">此问题已在 .NET Framework 4.7.1 及更高版本中解决。</span><span class="sxs-lookup"><span data-stu-id="1c603-330">This issue is fixed starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="1c603-331">例如：</span><span class="sxs-lookup"><span data-stu-id="1c603-331">For example:</span></span>

  <span data-ttu-id="1c603-332">在此之前:</span><span class="sxs-lookup"><span data-stu-id="1c603-332">Before:</span></span>

  ![此屏幕截图中显示了一个组合框控件，其中有一个不可见下拉箭头。](./media/whats-new-in-accessibility/combo-box-style-key-before.png)

  <span data-ttu-id="1c603-334">之后：</span><span class="sxs-lookup"><span data-stu-id="1c603-334">After:</span></span>

  ![显示下拉箭头的组合框控件的屏幕截图。](./media/whats-new-in-accessibility/combo-box-style-key-after.png)

- <span data-ttu-id="1c603-336"><xref:System.Windows.Controls.DataGrid> 控件</span><span class="sxs-lookup"><span data-stu-id="1c603-336"><xref:System.Windows.Controls.DataGrid> control</span></span>

  <span data-ttu-id="1c603-337">从 .NET Framework 4.7.1 开始，<xref:System.Windows.Controls.DataGrid> 控件中的排序指示符箭头现在使用正确的主题颜色。</span><span class="sxs-lookup"><span data-stu-id="1c603-337">Starting with .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="1c603-338">例如：</span><span class="sxs-lookup"><span data-stu-id="1c603-338">For example:</span></span>

  <span data-ttu-id="1c603-339">在此之前:</span><span class="sxs-lookup"><span data-stu-id="1c603-339">Before:</span></span>

  ![改进前的排序指示符箭头的屏幕截图。](./media/whats-new-in-accessibility/sort-indicator-before.png)

  <span data-ttu-id="1c603-341">之后：</span><span class="sxs-lookup"><span data-stu-id="1c603-341">After:</span></span>

  ![改进后的排序指示符箭头的屏幕截图。](./media/whats-new-in-accessibility/sort-indicator-after.png)

  <span data-ttu-id="1c603-343">此外，在 .NET Framework 4.7 及更低版本中，在高对比度模式下，默认链接样式在鼠标悬停在其上时更改为不正确的颜色。</span><span class="sxs-lookup"><span data-stu-id="1c603-343">In addition, in .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="1c603-344">此问题已在 .NET Framework 4.7.1 及更高版本中解决。</span><span class="sxs-lookup"><span data-stu-id="1c603-344">This is resolved starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="1c603-345">同样，从 .NET Framework 4.7.1 开始，<xref:System.Windows.Controls.DataGrid> 复选框列对键盘焦点反馈使用预期的颜色。</span><span class="sxs-lookup"><span data-stu-id="1c603-345">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with .NET Framework 4.7.1.</span></span>

  <span data-ttu-id="1c603-346">在此之前:</span><span class="sxs-lookup"><span data-stu-id="1c603-346">Before:</span></span>

  ![显示“点击此处！”的链接屏幕截图](./media/whats-new-in-accessibility/default-link-style-before.png)

  <span data-ttu-id="1c603-349">之后：</span><span class="sxs-lookup"><span data-stu-id="1c603-349">After:</span></span>

  ![显示“点击此处！”的链接屏幕截图](./media/whats-new-in-accessibility/default-link-style-after.png)

<span data-ttu-id="1c603-352">有关 .NET Framework 4.7.1 中 WPF 辅助功能改进的详细信息，请参阅 [WPF 辅助功能改进](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf)。</span><span class="sxs-lookup"><span data-stu-id="1c603-352">For more information on WPF accessibility improvements in .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

<a name="winforms471"></a>

### <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="1c603-353">Windows 窗体辅助功能改进</span><span class="sxs-lookup"><span data-stu-id="1c603-353">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="1c603-354">在 .NET Framework 4.7.1 中，Windows 窗体 (WinForms) 包括以下几个方面的辅助功能改进。</span><span class="sxs-lookup"><span data-stu-id="1c603-354">In .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="1c603-355">**改进了高对比度模式下的显示**</span><span class="sxs-lookup"><span data-stu-id="1c603-355">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="1c603-356">从 .NET Framework 4.7.1 开始，多种 WinForms 控件改进了高对比度模式下在操作系统中的呈现方式。</span><span class="sxs-lookup"><span data-stu-id="1c603-356">Starting with .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="1c603-357">Windows 10 更改了一些高对比度系统颜色的值，而 Windows 窗体基于 Windows 10 Win32 框架。</span><span class="sxs-lookup"><span data-stu-id="1c603-357">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="1c603-358">为获得最佳体验，请运行最新版本的 Windows，并通过在测试应用程序中添加 app.manifest 文件选择使用最新的 OS 更改，同时取消注释 Windows 10 支持的 OS 行，最终结果如下所示：</span><span class="sxs-lookup"><span data-stu-id="1c603-358">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!-- Windows 10 -->
<supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
```

<span data-ttu-id="1c603-359">高对比度更改的一些示例包括：</span><span class="sxs-lookup"><span data-stu-id="1c603-359">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="1c603-360"><xref:System.Windows.Forms.MenuStrip> 项中的复选标记更易于查看。</span><span class="sxs-lookup"><span data-stu-id="1c603-360">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="1c603-361">选中后，禁用的 <xref:System.Windows.Forms.MenuStrip> 项更易于查看。</span><span class="sxs-lookup"><span data-stu-id="1c603-361">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="1c603-362">所选 <xref:System.Windows.Forms.Button> 控件中的文本与选中颜色形成鲜明对比。</span><span class="sxs-lookup"><span data-stu-id="1c603-362">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="1c603-363">禁用的文本更易于阅读。</span><span class="sxs-lookup"><span data-stu-id="1c603-363">Disabled text is easier to read.</span></span> <span data-ttu-id="1c603-364">例如：</span><span class="sxs-lookup"><span data-stu-id="1c603-364">For example:</span></span>

  <span data-ttu-id="1c603-365">在此之前:</span><span class="sxs-lookup"><span data-stu-id="1c603-365">Before:</span></span>

  ![一个应用的屏幕截图，该应用在高对比度模式下运行着不同的控件，而尚未改进可访问性。](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-before.png)

  <span data-ttu-id="1c603-367">之后：</span><span class="sxs-lookup"><span data-stu-id="1c603-367">After:</span></span>

  ![应用程序的屏幕截图，在辅助功能改进之后，该应用程序使用在高对比度模式下运行的不同控件。](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-after.png)

- <span data-ttu-id="1c603-369">“线程异常”对话框中的高对比度改进。</span><span class="sxs-lookup"><span data-stu-id="1c603-369">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="1c603-370">**改进了讲述人支持**</span><span class="sxs-lookup"><span data-stu-id="1c603-370">**Improved Narrator support**</span></span>

<span data-ttu-id="1c603-371">.NET Framework 4.7.1 中的 Windows 窗体对讲述人进行了以下辅助功改进：</span><span class="sxs-lookup"><span data-stu-id="1c603-371">Windows Forms in .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="1c603-372">讲述人以及其他 UI 自动化工具可访问 <xref:System.Windows.Forms.MonthCalendar> 控件。</span><span class="sxs-lookup"><span data-stu-id="1c603-372">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="1c603-373">当某个项的选中状态更改时，<xref:System.Windows.Forms.CheckedListBox> 控件会通知讲述人，因此用户可获知更改了列表项的值。</span><span class="sxs-lookup"><span data-stu-id="1c603-373">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>

- <span data-ttu-id="1c603-374"><xref:System.Windows.Forms.DataGridViewCell> 控件向讲述人报告正确的只读状态。</span><span class="sxs-lookup"><span data-stu-id="1c603-374">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>

- <span data-ttu-id="1c603-375">讲述人现在可以阅读已禁用的 <xref:System.Windows.Forms.ToolStripMenuItem> 文本，而以前它会跳过禁用的菜单项。</span><span class="sxs-lookup"><span data-stu-id="1c603-375">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="1c603-376">**增强了对 UIAutomation 辅助功能模式的支持**</span><span class="sxs-lookup"><span data-stu-id="1c603-376">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="1c603-377">从 .NET Framework 4.7.1 开始，辅助功能技术工具的开发人员可以利用常见的 API 辅助功能模式和多个 WinForms 控件的属性。</span><span class="sxs-lookup"><span data-stu-id="1c603-377">Starting with .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="1c603-378">这些辅助功能改进包括：</span><span class="sxs-lookup"><span data-stu-id="1c603-378">These accessibility improvements include:</span></span>

- <span data-ttu-id="1c603-379"><xref:System.Windows.Forms.ComboBox> 和 <xref:System.Windows.Forms.ToolStripSplitButton> 现在支持[展开/折叠模式](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="1c603-379">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="1c603-380"><xref:System.Windows.Forms.DataGridViewCheckBoxCell> 现在支持[切换模式](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="1c603-380">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>

- <span data-ttu-id="1c603-381"><xref:System.Windows.Forms.ToolStripItem> 控件支持 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> 属性和[展开/折叠模式](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="1c603-381">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="1c603-382"><xref:System.Windows.Forms.NumericUpDown> 和 <xref:System.Windows.Forms.DomainUpDown> 控件支持 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> 属性。</span><span class="sxs-lookup"><span data-stu-id="1c603-382">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span></span>

<span data-ttu-id="1c603-383">**改进了属性浏览器体验**</span><span class="sxs-lookup"><span data-stu-id="1c603-383">**Improved property browser experience**</span></span>

<span data-ttu-id="1c603-384">从 .NET Framework 4.7.1 开始，Windows 窗体包括以下改进：</span><span class="sxs-lookup"><span data-stu-id="1c603-384">Starting with .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="1c603-385">更好地通过各种下拉选择窗口使用键盘导航。</span><span class="sxs-lookup"><span data-stu-id="1c603-385">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="1c603-386">减少不必要的制表位。</span><span class="sxs-lookup"><span data-stu-id="1c603-386">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="1c603-387">更好地报告控件类型。</span><span class="sxs-lookup"><span data-stu-id="1c603-387">Better reporting of control types.</span></span>
- <span data-ttu-id="1c603-388">改进了讲述人行为。</span><span class="sxs-lookup"><span data-stu-id="1c603-388">Improved narrator behavior.</span></span>

<a name="aspnet471"></a>

### <a name="aspnet-web-controls"></a><span data-ttu-id="1c603-389">ASP.NET Web 控件</span><span class="sxs-lookup"><span data-stu-id="1c603-389">ASP.NET web controls</span></span>

<span data-ttu-id="1c603-390">自 .NET Framework 4.7.1 和 Visual Studio 2017 版本 15.3 起，ASP.NET 改进了 ASP.NET Web 控件与 Visual Studio 中的辅助功能技术配合使用的方式。</span><span class="sxs-lookup"><span data-stu-id="1c603-390">Starting with .NET Framework 4.7.1 and Visual Studio 2017 version 15.3, ASP.NET improves how ASP.NET web controls work with accessibility technology in Visual Studio.</span></span> <span data-ttu-id="1c603-391">包括以下更改：</span><span class="sxs-lookup"><span data-stu-id="1c603-391">Changes include the following:</span></span>

- <span data-ttu-id="1c603-392">在以下控件中实现缺失 UI 的辅助功能模式：例如“详细信息视图”向导中的“添加字段”对话框或“ListView”向导的“配置 ListView”对话框   。</span><span class="sxs-lookup"><span data-stu-id="1c603-392">Changes to implement missing UI accessibility patterns in controls, like the **Add Field** dialog in the **Details View** wizard, or the **Configure ListView** dialog of the **ListView** wizard.</span></span>

- <span data-ttu-id="1c603-393">改善在高对比度模式下（如“数据页导航字段编辑器”）的显示。</span><span class="sxs-lookup"><span data-stu-id="1c603-393">Changes to improve the display in High Contrast mode, like the **Data Pager Fields Editor**.</span></span>

- <span data-ttu-id="1c603-394">改善以下控件的键盘导航体验：例如 DataPager 控件的“编辑页导航字段”向导中的“字段”对话框、“配置 ObjectContext”对话框或“配置数据源”向导的“配置数据选择”对话框    。</span><span class="sxs-lookup"><span data-stu-id="1c603-394">Changes to improve the keyboard navigation experiences for controls, like the **Fields** dialog in the **Edit Pager Fields** wizard of the DataPager control, the **Configure ObjectContext** dialog, or the **Configure Data Selection** dialog of the **Configure Data Source** wizard.</span></span>

<a name="tools471"></a>

### <a name="net-sdk-tools"></a><span data-ttu-id="1c603-395">.NET SDK 工具</span><span class="sxs-lookup"><span data-stu-id="1c603-395">.NET SDK Tools</span></span>

<span data-ttu-id="1c603-396">[配置编辑器工具 (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) 和[服务跟踪查看器工具 (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) 通过修复各种辅助功能问题得到改进。</span><span class="sxs-lookup"><span data-stu-id="1c603-396">The [Configuration Editor Tool (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) and [Service Trace Viewer Tool (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="1c603-397">其中大多数都是一些小问题，如未定义名称或未正确实现某些 UI 自动化模式。</span><span class="sxs-lookup"><span data-stu-id="1c603-397">Most of these were small issues, like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="1c603-398">虽然许多用户不会意识到这些小问题的重要性，但使用屏幕阅读器等辅助技术的客户会发现这些 SDK 工具更易于访问。</span><span class="sxs-lookup"><span data-stu-id="1c603-398">While many users won’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span>

<span data-ttu-id="1c603-399">这些改进更改了某些旧行为，例如键盘焦点顺序。</span><span class="sxs-lookup"><span data-stu-id="1c603-399">These enhancements change some previous behaviors, such as keyboard focus order.</span></span>

<a name="wf471"></a>

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="1c603-400">Windows Workflow Foundation (WF) 工作流设计器</span><span class="sxs-lookup"><span data-stu-id="1c603-400">Windows Workflow Foundation (WF) Workflow Designer</span></span>

<span data-ttu-id="1c603-401">工作流设计器中的辅助功能更改包括：</span><span class="sxs-lookup"><span data-stu-id="1c603-401">Accessibility changes in the Workflow Designer include the following:</span></span>

- <span data-ttu-id="1c603-402">某些控件中 Tab 键顺序更改为从左到右以及从上到下：</span><span class="sxs-lookup"><span data-stu-id="1c603-402">The tab order changes to left to right and top to bottom in some controls:</span></span>

  - <span data-ttu-id="1c603-403">设置 <xref:System.ServiceModel.Activities.InitializeCorrelation> 活动相关数据的初始化相关窗口。</span><span class="sxs-lookup"><span data-stu-id="1c603-403">The initialize correlation window for setting correlation data for the <xref:System.ServiceModel.Activities.InitializeCorrelation> activity.</span></span>

  - <span data-ttu-id="1c603-404"><xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.SendReply> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 活动的内容定义窗口。</span><span class="sxs-lookup"><span data-stu-id="1c603-404">The content definition window for the <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply> activities.</span></span>

- <span data-ttu-id="1c603-405">通过键盘可以使用更多功能：</span><span class="sxs-lookup"><span data-stu-id="1c603-405">More functions are available via the keyboard:</span></span>

  - <span data-ttu-id="1c603-406">编辑活动的属性时，属性组在第一次聚焦时可以通过键盘折叠。</span><span class="sxs-lookup"><span data-stu-id="1c603-406">When editing the properties of an activity, property groups can be collapsed by keyboard the first time they are focused.</span></span>

  - <span data-ttu-id="1c603-407">警告图标可以通过键盘访问。</span><span class="sxs-lookup"><span data-stu-id="1c603-407">Warning icons are accessible by keyboard.</span></span>

  - <span data-ttu-id="1c603-408">“属性”窗口的“更多属性”按钮可以通过键盘访问 。</span><span class="sxs-lookup"><span data-stu-id="1c603-408">The **More Properties** button in the **Properties** window is accessible by keyboard.</span></span>

  - <span data-ttu-id="1c603-409">键盘用户可以访问工作流设计器“参数”和“变量”窗格的标题项 。</span><span class="sxs-lookup"><span data-stu-id="1c603-409">Keyboard users can access the header items in the **Arguments** and **Variables** panes of the Workflow Designer.</span></span>

- <span data-ttu-id="1c603-410">提升了聚焦项的可见性，例如当：</span><span class="sxs-lookup"><span data-stu-id="1c603-410">Improved visibility of items with focus, such as when:</span></span>

  - <span data-ttu-id="1c603-411">将行添加到工作流设计器和活动设计器使用的数据网格。</span><span class="sxs-lookup"><span data-stu-id="1c603-411">Adding rows to data grids used by the Workflow Designer and activity designers.</span></span>

  - <span data-ttu-id="1c603-412">在 <xref:System.ServiceModel.Activities.ReceiveReply> 和 <xref:System.ServiceModel.Activities.SendReply> 活动中按 Tab 键切换字段。</span><span class="sxs-lookup"><span data-stu-id="1c603-412">Tabbing through fields in the <xref:System.ServiceModel.Activities.ReceiveReply> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>

  - <span data-ttu-id="1c603-413">设置变量或自变量的默认值</span><span class="sxs-lookup"><span data-stu-id="1c603-413">Setting default values for variables or arguments</span></span>

- <span data-ttu-id="1c603-414">屏幕读取器现在可以正确识别：</span><span class="sxs-lookup"><span data-stu-id="1c603-414">Screen readers can now correctly recognize:</span></span>

  - <span data-ttu-id="1c603-415">工作流设计器中设置的断点。</span><span class="sxs-lookup"><span data-stu-id="1c603-415">Breakpoints set in the workflow designer.</span></span>

  - <span data-ttu-id="1c603-416"><xref:System.Activities.Statements.FlowSwitch%601>、<xref:System.Activities.Statements.FlowDecision> 和 <xref:System.ServiceModel.Activities.CorrelationScope> 活动。</span><span class="sxs-lookup"><span data-stu-id="1c603-416">The <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, and <xref:System.ServiceModel.Activities.CorrelationScope> activities.</span></span>
  - <span data-ttu-id="1c603-417"><xref:System.ServiceModel.Activities.Receive> 活动的内容。</span><span class="sxs-lookup"><span data-stu-id="1c603-417">The contents of the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>

  - <span data-ttu-id="1c603-418"><xref:System.Activities.Statements.InvokeMethod> 活动的目标类型。</span><span class="sxs-lookup"><span data-stu-id="1c603-418">The Target Type for the <xref:System.Activities.Statements.InvokeMethod> activity.</span></span>

  - <span data-ttu-id="1c603-419"><xref:System.Activities.Statements.TryCatch> 活动中的“异常”组合框和“最终”部分。</span><span class="sxs-lookup"><span data-stu-id="1c603-419">The Exception combo box and the Finally section in the <xref:System.Activities.Statements.TryCatch> activity.</span></span>

  - <span data-ttu-id="1c603-420">消息传递活动（<xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.SendReply> 和 <xref:System.ServiceModel.Activities.ReceiveReply>）中的“消息类型”组合框、“添加相关初始化表达式”窗口中的拆分器、“内容定义”窗口和“CorrelatesOn 定义”窗口。</span><span class="sxs-lookup"><span data-stu-id="1c603-420">The Message Type combo box, the splitter in the Add Correlation Initializers window, the Content Definition window, and the CorrelatesOn Definition window in the messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>

  - <span data-ttu-id="1c603-421">状态机转换和转换目标。</span><span class="sxs-lookup"><span data-stu-id="1c603-421">State machine transitions and transitions destinations.</span></span>

  - <span data-ttu-id="1c603-422"><xref:System.Activities.Statements.FlowDecision> 活动上的注释和连接器。</span><span class="sxs-lookup"><span data-stu-id="1c603-422">Annotations and connectors on <xref:System.Activities.Statements.FlowDecision> activities.</span></span>

  - <span data-ttu-id="1c603-423">活动的上下文（右键单击）菜单。</span><span class="sxs-lookup"><span data-stu-id="1c603-423">The context (right-click) menus for activities.</span></span>

  - <span data-ttu-id="1c603-424">属性值编辑器、“清除搜索”按钮、“按类别”和“按字母顺序”排序按钮以及属性网格中的“表达式编辑器”对话框。</span><span class="sxs-lookup"><span data-stu-id="1c603-424">The property value editors, the Clear Search button, the By Category and Alphabetical sort buttons, and the Expression Editor dialog in the properties grid.</span></span>

  - <span data-ttu-id="1c603-425">工作流设计器中的缩放百分比。</span><span class="sxs-lookup"><span data-stu-id="1c603-425">The zoom percentage in the Workflow Designer.</span></span>

  - <span data-ttu-id="1c603-426"><xref:System.Activities.Statements.Parallel> 和 <xref:System.Activities.Statements.Pick> 活动中的分隔符。</span><span class="sxs-lookup"><span data-stu-id="1c603-426">The separator in <xref:System.Activities.Statements.Parallel> and <xref:System.Activities.Statements.Pick> activities.</span></span>

  - <span data-ttu-id="1c603-427"><xref:System.Activities.Statements.InvokeDelegate> 活动。</span><span class="sxs-lookup"><span data-stu-id="1c603-427">The <xref:System.Activities.Statements.InvokeDelegate> activity.</span></span>

  - <span data-ttu-id="1c603-428">字典活动（`Microsoft.Activities.AddToDictionary<TKey,TValue>`、`Microsoft.Activities.RemoveFromDictionary<TKey,TValue>` 等）的“选择类型”窗口。</span><span class="sxs-lookup"><span data-stu-id="1c603-428">The Select Types window for dictionary activities (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`, etc.).</span></span>

  - <span data-ttu-id="1c603-429">“浏览和选择 .NET 类型”窗口。</span><span class="sxs-lookup"><span data-stu-id="1c603-429">The Browse and Select .NET Type window.</span></span>

  - <span data-ttu-id="1c603-430">工作流设计器中的痕迹导航。</span><span class="sxs-lookup"><span data-stu-id="1c603-430">Breadcrumbs in the Workflow Designer.</span></span>

- <span data-ttu-id="1c603-431">选择高对比度主题的用户将看到工作流设计器及其控件可见性的许多改进，例如元素间更好的对比度和焦点元素更明显的选择框。</span><span class="sxs-lookup"><span data-stu-id="1c603-431">Users who choose High Contrast themes will see many improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c603-432">请参阅</span><span class="sxs-lookup"><span data-stu-id="1c603-432">See also</span></span>

- [<span data-ttu-id="1c603-433">.NET Framework 的新增功能</span><span class="sxs-lookup"><span data-stu-id="1c603-433">What's new in the .NET Framework</span></span>](index.md)

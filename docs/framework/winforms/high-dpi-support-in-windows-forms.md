---
title: 高 DPI 支持
description: 了解 Windows 窗体中常见的高 DPI 和动态 DPI 方案的支持。 还了解如何配置 Windows 窗体应用程序以实现高 DPI 支持。
ms.date: 05/16/2017
helpviewer_keywords:
- High DPI in Windows Forms
- Dynamic rescaling in Windows Forms
- Windows Forms layout
- Windows Forms dynamic resizing
ms.assetid: 075ea4c3-900c-4f8a-9dd2-13ea6804346b
ms.openlocfilehash: a9e0766307095da447c772de5a3065c18b7b7154
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325655"
---
# <a name="high-dpi-support-in-windows-forms"></a>Windows 窗体中的高 DPI 支持

从 .NET Framework 4.7 开始，Windows 窗体包括常见高 DPI 和动态 DPI 方案的增强功能。 其中包括:

- 对许多 Windows 窗体控件（如控件和控件）的缩放和布局进行了改进 <xref:System.Windows.Forms.MonthCalendar> <xref:System.Windows.Forms.CheckedListBox> 。

- 单步缩放。  在 .NET Framework 4.6 及更早版本中，缩放是通过多个走刀执行的，这会导致某些控件的缩放比例超出了必需。

- 支持动态 DPI 方案，在此方案中，用户在启动 Windows 窗体应用程序后更改了 DPI 或缩放系数。

从 .NET Framework 4.7 开始 .NET Framework 版本中，增强的高 DPI 支持是一项可选功能。 您必须将应用程序配置为利用它。

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a>配置 Windows 窗体应用以实现高 DPI 支持

支持高 DPI 感知的新 Windows 窗体功能仅在面向 .NET Framework 4.7 的应用程序中提供，并且在从 Windows 10 创意者更新开始的 Windows 操作系统上运行。

此外，若要在 Windows 窗体应用程序中配置高 DPI 支持，必须执行以下操作：

- 声明与 Windows 10 的兼容性。

  为此，请将以下内容添加到清单文件中：

  ```xml
  <compatibility xmlns="urn:schemas-microsoft-com:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- 启用*app.config*文件中的每监视器 DPI 感知。

  Windows 窗体引入了一个新 [`<System.Windows.Forms.ApplicationConfigurationSection>`](../configure-apps/file-schema/winforms/index.md) 元素，用于支持从 .NET Framework 4.7 开始添加的新功能和自定义项。 若要利用支持高 DPI 的新功能，请将以下项添加到应用程序配置文件中。

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>
  ```

  > [!IMPORTANT]
  > 在以前版本的 .NET Framework 中，你使用了清单来添加高 DPI 支持。 不再建议使用此方法，因为它会替代在 app.config 文件上定义的设置。

- 调用静态 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> 方法。

  这应该是应用程序入口点中的第一个方法调用。 例如：

  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a>退出单个高 DPI 功能

将 `DpiAwareness` 值设置为可 `PerMonitorV2` 从 .NET Framework 4.7 开始 .NET Framework 版本支持所有高 DPI 感知功能。 通常，这适用于大多数 Windows 窗体应用程序。 但是，你可能想要选择不提供一个或多个单独的功能。 执行此操作的最重要的原因是您的现有应用程序代码已经处理了该功能。  例如，如果你的应用程序处理自动缩放，则你可能想要禁用自动调整大小功能，如下所示：

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

有关各个键及其值的列表，请参阅[Windows 窗体添加配置元素](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)。

## <a name="new-dpi-change-events"></a>新的 DPI 更改事件

从 .NET Framework 4.7 开始，三个新事件允许以编程方式处理动态 DPI 更改：

- <xref:System.Windows.Forms.Control.DpiChangedAfterParent>，在控件的父控件或窗体的 DPI 更改事件发生后以编程方式更改控件的 DPI 设置时，将激发此事件。
- <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>，在其父控件或窗体的 DPI 更改事件发生之前以编程方式更改控件的 DPI 设置时，将激发此事件。
- <xref:System.Windows.Forms.Form.DpiChanged>，在当前显示窗体的显示设备上的 DPI 设置更改时激发。

## <a name="new-helper-methods-and-properties"></a>新的帮助器方法和属性

.NET Framework 4.7 还添加了一些新的帮助器方法和属性，这些方法和属性提供了有关 DPI 缩放的信息，并允许您执行 DPI 缩放。 其中包括:

- <xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>，它将值从逻辑与设备像素转换。

- <xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>，它将位图图像缩放为设备的逻辑 DPI。

- <xref:System.Windows.Forms.Control.DeviceDpi%2A>，它返回当前设备的 DPI。

## <a name="versioning-considerations"></a>版本控制注意事项

除了在 .NET Framework 4.7 和 Windows 10 创意者更新上运行以外，应用程序还可以在与高 DPI 改进不兼容的环境中运行。 在这种情况下，需要为应用程序开发回退。 你可以执行此操作来执行[自定义绘图](./controls/user-drawn-controls.md)来处理缩放。

为此，还需要确定运行应用的操作系统。 可以用如下代码来实现：

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

请注意，如果 Windows 10 未在应用程序清单中列出为受支持的操作系统，则你的应用程序不会成功检测到它。

你还可以查看生成应用程序所针对的 .NET Framework 的版本：

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a>另请参阅

- [Windows 窗体添加配置元素](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)
- [调整 Windows 窗体的大小和比例](adjusting-the-size-and-scale-of-windows-forms.md)
